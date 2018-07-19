---
title: Instrucciones para desarrolladores de C++ para los canales del lado de ejecución especulativa | Microsoft Docs
ms.custom: ''
ms.date: 07/10/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
- Spectre
- CVE-2017-5753
- Speculative Execution
author: mamillmsft
ms.author: mikeblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c355924ce1f264ce63e02f5fda948a62675e675
ms.sourcegitcommit: 894b3b3a91fcd8894b582747b03135c0be450c1f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38102470"
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>Instrucciones para desarrolladores de C++ para los canales del lado de ejecución especulativa

En este artículo contiene instrucciones para desarrolladores ayudar a identificar y mitigar las vulnerabilidades de hardware de canal de lado de ejecución especulativa en software de C++. Estas vulnerabilidades pueden revelar información confidencial a través de límites de confianza y pueden afectar al software que se ejecuta en procesadores que admiten la ejecución especulativa, fuera de secuencia de instrucciones. Esta clase de vulnerabilidades fue el primero se describe en enero de 2018 y obtener información general adicional y pueden encontrar instrucciones en [aviso de seguridad de Microsoft](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002).

Las instrucciones proporcionadas en este artículo está relacionado con las clases de vulnerabilidades representadas por:

1. CVE-2017-5753, también conocido como variante 1. Esta clase de vulnerabilidad de hardware está relacionado con los canales de lado que pueden surgir debido a la ejecución especulativa que se produce como resultado una predicción de bifurcación condicional. El compilador de Visual C++ en Visual Studio 2017 (empezando por la versión 15.5.5) incluye compatibilidad con la `/Qspectre` relacionados con CVE-2017-5753 conmutador que proporciona una mitigación de tiempo de compilación para un conjunto limitado de modelos de codificación potencialmente vulnerables. La documentación de la [/qspectre](https://docs.microsoft.com/en-us/cpp/build/reference/qspectre) marca proporciona más información sobre sus efectos y uso. 

2. CVE-2018-3639, también conocido como [especulativa Store omisión (SSB)](https://aka.ms/sescsrdssb). Esta clase de vulnerabilidad de hardware está relacionado con los canales de lado que pueden surgir debido a la ejecución especulativa de una carga por delante de un almacén dependiente como resultado de una predicción de acceso de memoria.

Encontrará una introducción accesible sobre vulnerabilidades de canal lateral de ejecución especulativa en la presentación titulada [el caso de Spectre y Meltdown](https://www.youtube.com/watch?v=_4O0zMW-Zu4) por uno de los equipos de investigación que detectan estos problemas.

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>¿Cuáles son las vulnerabilidades de hardware de canal de lado de ejecución especulativa?

Las CPU actuales ofrecen niveles superiores de rendimiento haciendo uso de la ejecución especulativa y de desorden de instrucciones. Por ejemplo, esto se logra con frecuencia al predecir el destino de ramas (condicionales e indirectas) que permite que la CPU empezar a anticipa ejecutando instrucciones en el destino de bifurcación previstos, lo que evita una pausa hasta que el destino de bifurcación real puede resolver. En caso de que la CPU más tarde descubre que se ha producido una predicción, todo el estado de la máquina que se calculó anticipa se descartan. Esto garantiza que no hay ningún efecto arquitectónicamente visible de la especulación mispredicted.

Aunque la ejecución especulativa no afecta el estado de visibilidad de su arquitectura, puede dejar residuos en estado no arquitectónicos, como las memorias caché distintos que se usan por la CPU. Resulta que estos seguimientos residuales de ejecución especulativa que puede dar lugar a vulnerabilidades de canal lateral. Para comprender mejor esto, considere el siguiente fragmento de código que proporciona un ejemplo de CVE-2017-5753 (omisión de comprobación de límites):

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

En este ejemplo, `ReadByte` es proporcionar un búfer, un tamaño de búfer y un índice en ese búfer. El parámetro de índice, según lo especificado por `untrusted_index`, proporcionado por una menor contexto con privilegios, como un proceso sin derechos administrativos. Si `untrusted_index` es menor que `buffer_size`, a continuación, se lee el carácter que ocupa ese índice de `buffer` y se utiliza para el índice en una región compartida de memoria que hace referencia `shared_buffer`. 

Desde una perspectiva arquitectónica, esta secuencia de código es perfectamente segura tal como se garantiza que `untrusted_index` siempre será menor que `buffer_size`. Sin embargo, en la presencia de ejecución especulativa, es posible que la CPU se errores de predicción de la rama condicional y ejecutará el cuerpo de if instrucción incluso cuando `untrusted_index` es mayor o igual que `buffer_size`. Por consiguiente, la CPU anticipa puede leer un byte más allá de los límites de `buffer` (que puede ser un secreto) y, a continuación, se podría usar ese valor de byte para calcular la dirección de una carga posterior a través de `shared_buffer`. 

Mientras que la CPU finalmente detectará esta predicción, pueden quedar residuales efectos secundarios en la memoria caché de CPU que ofrecen información sobre el valor de bytes que se leyó fuera de los límites de `buffer`. Estos efectos pueden ser detectados por una menor contexto privilegiado que se ejecuta en el sistema por sondeo rapidez cada caché línea `shared_buffer` se tiene acceso. Los pasos que se pueden realizar para lograr esto son:

1. **Invocar `ReadByte` varias veces con `untrusted_index` que se va a menos de `buffer_size`** . El contexto de ataque puede hacer que el contexto de la víctima invocar `ReadByte` (por ejemplo, a través de RPC), que es la predicción de ramas capacitado para no ser tomada como `untrusted_index` es menor que `buffer_size`.

2. **Vaciar todas las líneas de caché en `shared_buffer`** . El contexto del atacante debe vaciar todas las líneas de caché en la región de memoria que hace referencia compartida `shared_buffer`. Dado que la región de memoria se comparte, esto es sencillo y puede realizarse mediante las funciones intrínsecas, como `_mm_clflush`.

3. **Invocar `ReadByte` con `untrusted_index` es mayor que `buffer_size`** . El contexto ataca provoca que el contexto de la víctima invocar `ReadByte` tal que predice incorrectamente que no se realizará la rama. Esta hace que el procesador para ejecutar anticipa el cuerpo de if bloque con `untrusted_index` es mayor que `buffer_size`, por tanto, provocando una lectura fuera de límites de `buffer`. Por lo tanto, `shared_buffer` está indizada con un valor potencialmente confidencial que se leyó fuera de los límites, lo cual provoca la línea de caché correspondiente que va a cargar la CPU.

4. **Leer cada línea de caché en `shared_buffer` para ver lo que se tiene acceso a más rápidamente**. El contexto del atacante puede leer cada línea de caché en `shared_buffer` y detectar la línea de caché que se carga mucho más rápido que los demás. Se trata de la línea de caché que es probable que se han incorporado el paso 3. Dado que hay una relación 1:1 entre la línea de valor y la memoria caché de bytes en este ejemplo, esto permite que el atacante puede deducir el valor real del byte que se leyó fuera de los límites.

Los pasos anteriores proporcionan un ejemplo del uso de una técnica conocida como VACIADO + RECARGA junto con el aprovechamiento de una instancia de CVE-2017-5753.

## <a name="what-software-scenarios-can-be-impacted"></a>¿Qué escenarios de software pueden verse afectados?

Desarrollo de software seguro mediante un proceso como el [Security Development Lifecycle](https://www.microsoft.com/en-us/sdl/) (SDL) normalmente requiere que los desarrolladores a identificar los límites de confianza que existen en su aplicación. Existe un límite de confianza en lugares donde una aplicación puede interactuar con los datos proporcionados por un contexto de menor confianza, por ejemplo, otro proceso en el sistema o un proceso en modo usuario sin derechos administrativos en el caso de un controlador de dispositivo de modo kernel. La nueva clase de vulnerabilidades relacionadas con canales de lado de la ejecución especulativa es relevante para muchos de los límites de confianza en los modelos de seguridad de software existente que aislar código y los datos en un dispositivo. 

En la tabla siguiente proporciona un resumen de los modelos de seguridad de software donde los desarrolladores que deba preocuparse acerca de estas vulnerabilidades que se producen:

|Límite de confianza|Descripción|
|----------------|----------------|
|Límites de máquina virtual|Las aplicaciones que aislar las cargas de trabajo en máquinas virtuales independientes que reciben datos de confianza desde otra máquina virtual pueden estar en peligro.| 
|Límite del núcleo|Un controlador de dispositivo de modo kernel que recibe los datos de confianza de un proceso en modo usuario no administrativo puede estar en peligro.| 
|Límite de proceso|Una aplicación que recibe los datos de confianza de otro proceso que se ejecuta en el sistema local, como a través de una llamada a procedimiento remoto (RPC), memoria compartida u otras comunicaciones entre procesos (IPC) mecanismos pueden estar en peligro.|
|Límite de enclave|Una aplicación que se ejecuta dentro de un enclave seguro (por ejemplo, Intel SGX) que recibe datos de confianza desde fuera el enclave puede estar en peligro.|
|Límites de los lenguajes|Una aplicación que interpreta o Just In Time (JIT) compila y ejecuta el código no seguro que se escriben un lenguaje de nivel superior puede estar en peligro.|

Aplicaciones que tienen la superficie expuesta a ataques a cualquiera de los anteriores límites deben revisar el código en la superficie de ataque para identificar y mitigar los posibles casos de vulnerabilidades de canal lateral de ejecución especulativa de confianza. Debe tenerse en cuenta que los límites de confianza expuestos a las superficies de ataque remoto, como los protocolos de red remota, que no han demostrado poner en riesgo a vulnerabilidades de canal lateral de ejecución especulativa.

## <a name="potentially-vulnerable-coding-patterns"></a>Potencialmente vulnerables patrones de codificación

Pueden surgir vulnerabilidades de canal lateral de ejecución especulativa como consecuencia de varios patrones de codificación. En esta sección se describe los patrones de codificación potencialmente vulnerables y proporciona ejemplos para cada uno, pero debería reconocer que pueden existir variaciones en estos temas. Por lo tanto, se aconseja a los desarrolladores para aprovechar estos patrones como ejemplos y no como una lista exhaustiva de todos los modelos de codificación potencialmente vulnerables. Las mismas clases de vulnerabilidades de seguridad de memoria que pueden existir en el software hoy en día pueden existir a lo largo de especulativa y rutas de acceso fuera de orden de ejecución, incluyendo pero sin limitarse a saturaciones del búfer, fuera de los límites de matriz accesos, uso de memoria no inicializada, tipo confusión y así sucesivamente. También se pueden aplicar los mismos tipos primitivos que los atacantes pueden utilizar para aprovechar las vulnerabilidades de seguridad de memoria a lo largo de las rutas de acceso de arquitectura a especulativas rutas de acceso.

En general, predicción de ejecución especulativa lado canales rama relacionados a condicional puede presentar cuando una expresión condicional opera en datos que se pueden controlar o influidos por un contexto de menor confianza. Por ejemplo, esto puede incluir las expresiones condicionales usadas en `if`, `for`, `while`, `switch`, o las instrucciones ternarias. Para cada una de estas instrucciones, el compilador puede generar una rama condicional que la CPU, a continuación, puede predecir el destino de bifurcación para en tiempo de ejecución.

Para cada ejemplo, se inserta un comentario con la frase "Barrera de especulación" donde un desarrollador podría suponer una barrera como mitigación. Esto se explica con más detalle en la sección en las mitigaciones.

## <a name="speculative-out-of-bounds-load"></a>Especulativa fuera de los límites de carga

Esta categoría de patrones de codificación implica una predicción de rama condicional que conduce a un especulativa fuera de los límites acceso a la memoria.

### <a name="array-out-of-bounds-load-feeding-a-load"></a>Matriz fuera de los límites de carga proporcionando una carga

Este patrón de codificación es el patrón de codificación vulnerable descrito originalmente para CVE-2017-5753 (omisión de comprobación de límites). La sección de fondo de este artículo explica este patrón en detalle.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        // SPECULATION BARRIER
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

De forma similar, una matriz fuera de los límites puede producirse carga junto con un bucle que supera su terminación condición debido a una predicción. En este ejemplo, la bifurcación condicional asociado con el `x < buffer_size` puede errores de predicción y anticipa ejecutar el cuerpo de expresión la `for` bucle cuando `x` es mayor o igual que `buffer_size`, por lo tanto lo que provocará un especulativa fuera de los límites de carga.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadBytes(unsigned char *buffer, unsigned int buffer_size) {
    for (unsigned int x = 0; x < buffer_size; x++) {
        // SPECULATION BARRIER
        unsigned char value = buffer[x];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>Matriz fuera de los límites de carga alimentar una bifurcación

Este patrón de codificación implica el caso donde una predicción de bifurcación condicional puede dar lugar a un fuera de los límites acceso a una matriz de punteros de función, lo que, a continuación, lleva a una rama en el destino indirecta de direcciones que se leyó fuera de los límites. El siguiente fragmento de código proporciona un ejemplo que se muestra cómo hacerlo. 

En este ejemplo, se proporciona un identificador de mensaje que no se confía para DispatchMessage a través de la `untrusted_message_id` parámetro. Si `untrusted_message_id` es menor que `MAX_MESSAGE_ID`, a continuación, se usa para indexar una matriz de punteros de función y la rama para el destino de bifurcación correspondiente. Este código es seguro su arquitectura, pero si la CPU errores de predicción de la rama condicional, podría causar `DispatchTable` indexando `untrusted_message_id` cuando su valor es mayor o igual que `MAX_MESSAGE_ID`, provocando así un acceso fuera de los límites. Esto podría dar lugar a ejecución especulativa desde una dirección de destino de rama que se deriva más allá de los límites de la matriz que podría provocar la divulgación de información según el código que se ejecuta anticipa.

```cpp
#define MAX_MESSAGE_ID 16

typedef void (*MESSAGE_ROUTINE)(unsigned char *buffer, unsigned int buffer_size);

const MESSAGE_ROUTINE DispatchTable[MAX_MESSAGE_ID];

void DispatchMessage(unsigned int untrusted_message_id, unsigned char *buffer, unsigned int buffer_size) {
    if (untrusted_message_id < MAX_MESSAGE_ID) {
        // SPECULATION BARRIER
        DispatchTable[untrusted_message_id](buffer, buffer_size);
    }
}
```

Como con el caso de una matriz fuera de los límites de carga alimentar carga otro, esta condición también puede surgir junto con un bucle que supera su condición de finalización debido a una predicción.

### <a name="array-out-of-bounds-store-feeding-an-indirect-branch"></a>Fuera de los límites de matriz almacenar alimentar una bifurcación

Mientras que el ejemplo anterior se mostró cómo un especulativa fuera de los límites carga puede influir en un destino de bifurcación indirecta, también es posible que un almacén fuera de los límites para modificar un destino de bifurcación, como un puntero de función o una dirección de retorno. Esto puede provocar la ejecución especulativa desde una dirección especificada por el atacante.

En este ejemplo, un índice de confianza se pasa a través de la `untrusted_index` parámetro. Si `untrusted_index` es menor que el número de elementos de la `pointers` matriz (256 elementos) y, a continuación, el valor de puntero proporcionado en `ptr` se escribe en el `pointers` matriz. Este código es seguro su arquitectura, pero si la CPU errores de predicción de la rama condicional, podría causar `ptr` anticipa que se escribe más allá de los límites de la pila asignado `pointers` matriz. Esto podría provocar daños especulativo de la dirección de devolución para `WriteSlot`. Si un atacante puede controlar el valor de `ptr`, es posible puedan provocar la ejecución especulativa de arbitrario de direcciones cuando `WriteSlot` devuelve a lo largo de la ruta de acceso especulativa.

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
}
```

De forma similar, si una variable local de puntero de función denominada `func` asignados en la pila, a continuación, es posible modificar anticipa la dirección que `func` hace referencia a cuando se produce la predicción de bifurcación condicional. Esto podría provocar la ejecución especulativa desde una dirección arbitraria cuando el puntero de función se llama a través.

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    void (*func)() = &callback;
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
    func();
}
```

Debe tenerse en cuenta que en ambos ejemplos implican la modificación especulativa de punteros de rama indirecta asignada a la pila. Es posible que también se puede producir especulativa modificación para incluso memoria de sólo lectura en algunas CPU, memoria asignados por montón y variables globales. Memoria asignada a la pila, el compilador de Visual C++ ya realiza los pasos para que sea más difícil de modificar anticipa destinos asignada a la pila de bifurcación indirecta, como reordenando las variables locales de forma que los búferes se colocan junto a una cookie de seguridad como parte de la [/GS](https://docs.microsoft.com/en-us/cpp/build/reference/gs-buffer-security-check) característica de seguridad del compilador.

## <a name="speculative-type-confusion"></a>Confusión de tipo especulativa

Esta categoría se ocupa de patrones que pueden dar lugar a una confusión especulativa de tipo de codificación. Esto se produce cuando se tiene acceso a memoria con un tipo incorrecto a lo largo de una ruta de acceso que no es arquitectura durante la ejecución especulativa. Predicción de bifurcación condicional y omisión de la tienda especulativa pueden provocar confusión de un tipo especulativa. 

Para la omisión de la tienda especulativas, esto puede ocurrir en escenarios donde un compilador vuelve a usar una ubicación de la pila para las variables de varios tipos. Esto es porque el almacén de arquitectura de una variable de tipo `A` puede omitirse, lo que permite la carga de tipo `A` anticipa ejecutar antes de que se asigna a la variable. Si la variable anteriormente almacenada es de un tipo diferente, esto puede crear las condiciones de una confusión especulativa de tipo.

Para la predicción de bifurcación condicional, se usará el siguiente fragmento de código para describir diferentes condiciones confusión especulativa tipo puede dar lugar a.

```cpp
enum TypeName {
    Type1,
    Type2
};

class CBaseType {
public:
    CBaseType(TypeName type) : type(type) {}
    TypeName type;
};

class CType1 : public CBaseType {
public:
    CType1() : CBaseType(Type1) {}
    char field1[256];
    unsigned char field2;
};

class CType2 : public CBaseType {
public:
    CType2() : CBaseType(Type2) {}
    void (*dispatch_routine)();
    unsigned char field2;
};

// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ProcessType(CBaseType *obj)
{
    if (obj->type == Type1) {
        // SPECULATION BARRIER
        CType1 *obj1 = static_cast<CType1 *>(obj);

        unsigned char value = obj1->field2;

        return shared_buffer[value * 4096];
    }
    else if (obj->type == Type2) {
        // SPECULATION BARRIER
        CType2 *obj2 = static_cast<CType2 *>(obj);

        obj2->dispatch_routine();

        return obj2->field2;
    }
}
```

### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>Confusión de tipo especulativa dan lugar a un fuera de los límites de carga

Este patrón de codificación implica el caso donde puede dar lugar a una confusión especulativa de tipo en un fuera de los límites o acceso confundido por el tipo de campo donde el valor cargado fuentes de distribución de una dirección de carga posteriores. Esto es similar al patrón de codificación fuera de los límites de matriz, pero se manifiesta a través de una alternativa a la secuencia de codificación, como se indicó anteriormente. En este ejemplo, podría provocar que el contexto de la víctima para ejecutar un contexto ataca `ProcessType` varias veces con un objeto de tipo `CType1` (`type` es igual al campo `Type1`). Esto tendrá el efecto del entrenamiento de la rama condicional para la primera `if` instrucción no predecir tomada. El contexto de ataque, a continuación, puede provocar el contexto de la víctima para ejecutar `ProcessType` con un objeto de tipo `CType2`. Esto puede provocar confusión de un tipo especulativa si el condicional de bifurcación para el primer `if` instrucción errores de predicción y ejecuta el cuerpo de la `if` instrucción, la conversión, por tanto, un objeto de tipo `CType2` a `CType1`. Puesto que `CType2` es menor que `CType1`, el acceso a la memoria para `CType1::field2` resultado en un especulativa fuera de los límites cargará de datos que pueden ser secretas. Este valor se utiliza en una carga de `shared_buffer` que puede crear efectos observables, igual que con la matriz fuera de los límites en el ejemplo se describe anteriormente.

### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>Confusión de tipo especulativa dan lugar a una rama indirecta

Este patrón de codificación implica el caso donde una confusión especulativa tipo puede dar lugar a una rama indirecta no segura durante la ejecución especulativa. En este ejemplo, podría provocar que el contexto de la víctima para ejecutar un contexto ataca `ProcessType` varias veces con un objeto de tipo `CType2` (`type` es igual al campo `Type2`). Esto tendrá el efecto del entrenamiento de la rama condicional para la primera `if` instrucción que se debe realizar y el `else if` instrucción que no se debe realizar. El contexto de ataque, a continuación, puede provocar el contexto de la víctima para ejecutar `ProcessType` con un objeto de tipo `CType1`. Esto puede provocar confusión de un tipo especulativa si el condicional de bifurcación para el primer `if` predice la instrucción realizadas y el `else if` instrucción predice no tomada, ejecutar, por tanto, el cuerpo de la `else if` y la conversión de un objeto de tipo `CType1` a `CType2`. Puesto que la `CType2::dispatch_routine` campo se superpone con el `char` matriz `CType1::field1`, esto podría resultar en una rama especulativa indirecta a un destino de bifurcación no deseados. Si el contexto de ataque puede controlar los valores de byte en el `CType1::field1` matriz, pueden ser capaces de controlar la dirección de destino de bifurcación.

## <a name="speculative-uninitialized-use"></a>Uso sin inicializar especulativa

Esta categoría de patrones de codificación implica escenarios donde puede obtener acceso a memoria no inicializada y usarlo para alimentar una carga posterior o rama indirecta ejecución especulativa. Para que estos modelos de codificación que se pueda usar, debe ser capaz de controlar o influyen significativamente en el contenido de la memoria que se usa sin inicializar el contexto que se está usando en un atacante.

### <a name="speculative-uninitialized-use-leading-to-an-out-of-bounds-load"></a>Uso sin inicializar especulativa dan lugar a un fuera de los límites de carga

Puede provocar un uso sin inicializar especulativo un fuera de los límites de carga con un valor controlada por el atacante. En el ejemplo siguiente, el valor de `index` se asigna `trusted_index` en todas las rutas de arquitectura y `trusted_index` se supone que es menor o igual a `buffer_size`. Sin embargo, según el código generado por el compilador, es posible que se puede producir una omisión de la tienda especulativas que permite la carga de `buffer[index]` y expresiones dependientes ejecutará antes de la asignación a `index`. Si esto ocurre, un valor no inicializado para `index` se usará como el desplazamiento de `buffer` que podría permitir que un atacante leer la información confidencial fuera de los límites y se transmiten a través de un canal de lado a través de la carga dependiente de `shared_buffer` .

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

void InitializeIndex(unsigned int trusted_index, unsigned int *index) {
    *index = trusted_index;
}

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int trusted_index) {
    unsigned int index;

    InitializeIndex(trusted_index, &index); // not inlined

    // SPECULATION BARRIER
    unsigned char value = buffer[index];
    return shared_buffer[value * 4096];
}
```

### <a name="speculative-uninitialized-use-leading-to-an-indirect-branch"></a>Uso sin inicializar especulativa dan lugar a una rama indirecta

Un uso sin inicializar especulativo puede provocar una rama indirecta donde el destino de bifurcación está controlado por un atacante. En el ejemplo siguiente, `routine` está asignado tanto `DefaultMessageRoutine1` o `DefaultMessageRoutine` dependiendo del valor de `mode`. En la ruta de acceso de arquitectura, esto dará como resultado `routine` siempre que se está inicializando por delante de la rama indirecta. Sin embargo, dependiendo del código generado por el compilador, una omisión especulativa store se puede producir que permite la rama indirecta a través de `routine` ejecutará anticipa por delante de la asignación a `routine`. Si esto ocurre, un atacante puede ser capaz de ejecutar especulativo desde una dirección arbitraria, suponiendo que el atacante puede influir en o controlar el valor inicializado de `routine`.

```cpp
#define MAX_MESSAGE_ID 16

typedef void (*MESSAGE_ROUTINE)(unsigned char *buffer, unsigned int buffer_size);

const MESSAGE_ROUTINE DispatchTable[MAX_MESSAGE_ID];
extern unsigned int mode;

void InitializeRoutine(MESSAGE_ROUTINE *routine) {
    if (mode == 1) {
        *routine = &DefaultMessageRoutine1;
    }
    else {
        *routine = &DefaultMessageRoutine;
    }
}

void DispatchMessage(unsigned int untrusted_message_id, unsigned char *buffer, unsigned int buffer_size) {
    MESSAGE_ROUTINE routine;

    InitializeRoutine(&routine); // not inlined

    // SPECULATION BARRIER
    routine(buffer, buffer_size);
}
```

## <a name="mitigation-options"></a>Opciones de mitigación

Al realizar cambios en el código fuente se pueden mitigar vulnerabilidades de canal lateral de ejecución especulativa. Estos cambios pueden implicar mitigar instancias específicas de una vulnerabilidad, por ejemplo, agregando un *barrera de especulación*, o al realizar cambios en el diseño de una aplicación para que información confidencial inaccesible para especulativa ejecución.

### <a name="speculation-barrier-via-manual-instrumentation"></a>Barrera de especulación a través de la instrumentación manual

Un *barrera de especulación* se pueden insertar manualmente por un desarrollador para evitar la ejecución especulativa de continuar a lo largo de una ruta de acceso que no es arquitectura. Por ejemplo, un desarrollador puede insertar una barrera de especulación antes de un patrón de codificación peligroso en el cuerpo de un bloque condicional, ya sea al principio del bloque (después de la rama condicional) o antes de la primera carga constituye un problema. Esto evitará que una predicción de bifurcación condicional, ejecutar el código peligroso en una ruta de acceso que no es arquitectura serializando la ejecución. La secuencia de barrera de especulación difiere por arquitectura de hardware, como se describe en la tabla siguiente:

|Arquitectura|Barrera de especulación intrínseco para CVE-2017-5753|Barrera de especulación intrínseco para CVE-2018-3639|
|----------------|----------------|----------------|
|x86/x64|_mm_lfence()|_mm_lfence()|
|ARM|actualmente, no disponible|__dsb(0)|
|ARM64|actualmente, no disponible|__dsb(0)|

Por ejemplo, el modelo de código siguiente se puede mitigar mediante el uso de la `_mm_lfence` intrínsecos, como se muestra a continuación.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        _mm_lfence();
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>Barrera de especulación a través de la instrumentación en tiempo de compilador

El compilador de Visual C++ en Visual Studio 2017 (empezando por la versión 15.5.5) incluye compatibilidad con la `/Qspectre` relacionados con CVE-2017-5753 conmutador que inserta automáticamente una barrera de especulación para un conjunto limitado de modelos de codificación potencialmente vulnerables. La documentación de la [/qspectre](https://docs.microsoft.com/en-us/cpp/build/reference/qspectre) marca proporciona más información sobre sus efectos y uso. Es importante tener en cuenta que esta marca no cubre todos los modelos de codificación potencialmente vulnerables y por lo tanto los desarrolladores no deben confiar en ella como una solución completa para esta clase de vulnerabilidades.

### <a name="masking-array-indices"></a>Los índices de matriz de enmascaramiento

En casos donde un especulativa fuera de los límites de carga se puede producir, el índice de matriz puede ser limitado fuertemente en la ruta de acceso no arquitectónicas y de arquitectura mediante la adición de lógica para enlazar explícitamente el índice de matriz. Por ejemplo, si una matriz se puede asignar a un tamaño que se alinea a la potencia de dos, puede introducir una máscara simple. Esto se muestra en el ejemplo siguiente, donde se supone que `buffer_size` se alinea a la potencia de dos. Esto garantiza que `untrusted_index` es siempre menor que `buffer_size`, aunque se produzca una predicción de bifurcación condicional y `untrusted_index` se ha pasado con un valor mayor o igual que `buffer_size`.

Debe tenerse en cuenta que el enmascaramiento de índice que se realiza aquí podrían experimentar almacén especulativa omisión según el código generado por el compilador.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        untrusted_index &= (buffer_size - 1);
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="removing-sensitive-information-from-memory"></a>Quitar información confidencial de la memoria

Otra técnica que puede utilizarse para mitigar vulnerabilidades de canal lateral de ejecución especulativa es quitar información confidencial de la memoria. Los desarrolladores de software pueden buscar oportunidades para refactorizar su aplicación que información confidencial no sea accesible durante la ejecución especulativa. Esto puede realizarse mediante la refactorización del diseño de una aplicación para aislar la información confidencial en procesos independientes. Por ejemplo, una aplicación de explorador web puede intentar aislar los datos asociados con cada origen de web en procesos independientes, lo que evita un proceso que se puede tener acceso a datos entre orígenes a través de la ejecución especulativa.

## <a name="see-also"></a>Vea también

[Instrucciones para mitigar las vulnerabilidades de canal lateral de ejecución especulativa](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)

[Mitigar vulnerabilidades de hardware de canal de lado de ejecución especulativa](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)