---
title: Guía del desarrollador de C++ para los canales de lado de ejecución especulativa | Documentos de Microsoft
ms.custom: ''
ms.date: 05/21/2018
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
ms.openlocfilehash: 515e2223e67d86da12488d9880a1a0a258fc4bdf
ms.sourcegitcommit: 4b2c3b0c720aef42bce7e1e5566723b0fec5ec7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>Guía del desarrollador de C++ para los canales de lado de ejecución especulativa

Este artículo contiene instrucciones para los desarrolladores que le ayudará a identificar y mitigar vulnerabilidades de hardware de canal de lado de ejecución especulativa en software de C++. Estas vulnerabilidades pueden revelar información confidencial a través de límites de confianza y pueden afectar al software que se ejecuta en procesadores que admiten la ejecución de instrucciones especulativa, fuera de servicio. Esta clase de vulnerabilidades debía primero se describe en enero de 2018 y obtener información general adicional y encontrará instrucciones en [aviso de seguridad de Microsoft](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002).

Las instrucciones proporcionadas en este artículo está relacionada con las clases de vulnerabilidades representadas por:

1. CVE-2017-5753, también conocido como variante de Spectre 1. Esta clase de vulnerabilidad de hardware está relacionado con los canales de lado que pueden surgir debido a la ejecución especulativa que se produce como resultado de una predicción de bifurcación condicional. El compilador de Visual C++ en Visual Studio de 2017 (a partir de la versión 15.5.5) incluye compatibilidad con la `/Qspectre` conmutador, que proporciona una reducción del tiempo de compilación para un conjunto limitado de modelos de codificación potencialmente vulnerables relacionados con CVE-2017-5753. La documentación de la [/Qspectre](https://docs.microsoft.com/en-us/cpp/build/reference/qspectre) marca proporciona más información sobre sus efectos y uso.

2. CVE-2018-3639, también conocida como [omisión especulativa de almacén (SSB)](https://aka.ms/sescsrdssb). Esta clase de vulnerabilidad de hardware está relacionado con los canales de lado que pueden surgir debido a la ejecución especulativa de una carga por delante de un almacén dependiente como resultado de una predicción de acceso de la memoria.

Encontrará una introducción a las vulnerabilidades de canal de lado de ejecución especulativa accesible en la presentación titulada [el caso de Spectre y colapso](https://www.youtube.com/watch?v=_4O0zMW-Zu4) mediante uno de los equipos de investigación que detectan estos problemas.

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>¿Cuáles son las vulnerabilidades del hardware de canal del lado de ejecución especulativa?

Las CPU actuales ofrecen niveles superiores de rendimiento realizando usan intensivamente la ejecución especulativa y fuera de secuencia de instrucciones. Por ejemplo, esto se suele llevar a cabo predecir el destino de bifurcaciones (condicionales e indirectas) que permite que la CPU empezar a forma especulativa ejecutando instrucciones en el destino de bifurcación previstos, lo que evita una pausa hasta que el destino de bifurcación real resolver. En caso de que la CPU más adelante detecta que se ha producido una predicción, se descarta todo el estado de la máquina que se calcula de forma especulativa. Esto no garantiza que no habrá ningún efecto visible su arquitectura de la especulación mispredicted.

Mientras ejecución especulativa no afecta a la arquitectura visibles en el estado, que puede dejar restos en estado no arquitectónico, como las memorias caché distintos que se usan por la CPU. Es estos seguimientos residuales de ejecución especulativa que puede dar lugar a vulnerabilidades de canal de lado. Para comprender mejor esto, considere el siguiente fragmento de código que proporciona un ejemplo de CVE-2017-5753 (omisión de comprobación de límites):

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

En este ejemplo, `ReadByte` es proporciona un búfer, un tamaño de búfer y un índice en dicho búfer. El parámetro de índice, tal y como especifica `untrusted_index`, proporciona una menor contexto privilegiado, por ejemplo, un proceso sin derechos administrativos. Si `untrusted_index` es menor que `buffer_size`, a continuación, se lee el carácter que ocupa ese índice de `buffer` y se utiliza para el índice en una región compartida de memoria que hace referencia a `shared_buffer`. 

Desde una perspectiva arquitectónica, esta secuencia de código es perfectamente segura tal y como se garantiza que `untrusted_index` siempre será menor que `buffer_size`. Sin embargo, en presencia de ejecución especulativa, es posible que la CPU se mispredict la bifurcación condicional y ejecuta el cuerpo del if instrucción incluso cuando `untrusted_index` es mayor o igual que `buffer_size`. Por consiguiente, la CPU forma especulativa puede leer un byte más allá de los límites de `buffer` (que puede ser un secreto) y, a continuación, utilizar ese valor de bytes para calcular la dirección de una carga posterior a través de `shared_buffer`. 

Mientras que la CPU finalmente detectará esta predicción, puede quedar residuales efectos secundarios en la memoria caché de CPU que revelan información sobre el valor de bytes que se ha leído fuera de los límites de `buffer`. Estos efectos secundarios se pueden detectar mediante una menor contexto privilegiado que se ejecuta en el sistema por sondeo rapidez cada caché línea `shared_buffer` se tiene acceso. Los pasos que se pueden realizar para lograr esto son:

1. **Invocar `ReadByte` varias veces con `untrusted_index` que se va a menos de `buffer_size`** . Puede hacer que el contexto de la víctima invocar el contexto ataca `ReadByte` (por ejemplo, a través de RPC), que es el elemento de predicción de bifurcación entrenado que no toma como `untrusted_index` es menor que `buffer_size`.

2. **Vaciar todas las líneas de caché en `shared_buffer`** . El contexto ataca debe vaciar todas las líneas de caché en la región compartida de memoria que hace referencia a `shared_buffer`. Dado que se comparte la región de memoria, esto es sencillo y se puede realizar con intrínsecos como `_mm_clflush`.

3. **Invocar `ReadByte` con `untrusted_index` es mayor que `buffer_size`** . El contexto de ataque hace que el contexto de la víctima invocar `ReadByte` que predice incorrectamente que no se realizará la bifurcación. Esto hace que el procesador de forma especulativa ejecuta el cuerpo del if bloque con `untrusted_index` es mayor que `buffer_size`, por lo tanto provocando una lectura fuera de los límites de `buffer`. Por lo tanto, `shared_buffer` está indizado mediante un valor potencialmente secreto que se ha leído fuera de límites, lo que produce la línea de caché respectivas sean cargados por la CPU.

4. **Leer cada línea de caché en `shared_buffer` para ver lo que se tiene acceso a más rápidamente**. El contexto del atacante puede leer cada línea de caché en `shared_buffer` y detectar la línea de caché que carga significativamente más rápido que las demás. Se trata de la línea de caché que es probable que se introdujeron el paso 3. Puesto que hay una relación de 1:1 entre la línea de caché y de valor de bytes en este ejemplo, esto permite que el atacante deducir el valor real del byte leído fuera de límites.

Los pasos anteriores proporcionan un ejemplo del uso de una técnica conocida como VACIADO + RECARGA junto con aprovecharse de una instancia de CVE-2017-5753.

## <a name="what-software-scenarios-can-be-impacted"></a>¿Qué escenarios de software se pueden ver afectados?

Desarrollo de software seguro mediante un proceso como el [ciclo de vida de desarrollo de seguridad](https://www.microsoft.com/en-us/sdl/) (SDL) normalmente requiere que los desarrolladores identificar los límites de confianza que existen en su aplicación. Existe un límite de confianza en lugares donde una aplicación puede interactuar con los datos proporcionados por un contexto de menor confianza, por ejemplo, otro proceso en el sistema o un proceso en modo usuario sin derechos administrativos en el caso de un controlador de dispositivo de modo kernel. La nueva clase de vulnerabilidades relacionadas con los canales de lado de ejecución especulativa es relevante para muchos de los límites de confianza en los modelos de seguridad de software que aislar código y los datos en un dispositivo. 

En la tabla siguiente proporciona un resumen de los modelos de seguridad de software que puede ser necesario que los desarrolladores que tener en cuenta acerca de estas vulnerabilidades que se producen:

|Límite de confianza|Descripción|
|----------------|----------------|
|Límite de máquina virtual|Las aplicaciones que aislar las cargas de trabajo en máquinas virtuales independientes que reciben datos no es de confianza desde otra máquina virtual pueden estar en peligro.| 
|Límite de kernel|Un controlador de dispositivo de modo kernel que recibe datos de confianza de un proceso en modo usuario no administrativo puede estar en peligro.| 
|Límite de proceso|Una aplicación que recibe datos de confianza de otro proceso que se ejecuta en el sistema local, como a través de una llamada a procedimiento remoto (RPC), memoria compartida u otra comunicación entre procesos (IPC) mecanismos pueden estar en peligro.|
|Límite de enclave|Una aplicación que se ejecuta dentro de un enclave seguro (por ejemplo, Intel SGX) que recibe los datos no es de confianza desde fuera al enclave puede estar en peligro.|
|Límite de lenguaje|Una aplicación que se interpreta o Just (JIT) compila y ejecuta el código no seguro que se escriben un lenguaje de nivel superior puede estar en peligro.|

Aplicaciones que tienen una superficie expuesta a ataques expuesto a cualquiera de los pasos anteriores límites deben revisar el código en la superficie de ataque para identificar y mitigar los posibles casos de vulnerabilidades de canal de lado de ejecución especulativa de confianza. Debe tenerse en cuenta que los límites de confianza que se expone a las superficies de ataque remoto, como los protocolos de red remota, que no han demostrado ser expuestos a las vulnerabilidades de canal de lado de ejecución especulativa.

## <a name="potentially-vulnerable-coding-patterns"></a>Modelos de codificación potencialmente vulnerables

Pueden surgir vulnerabilidades de canal de lado de ejecución especulativa como consecuencia de varios modelos de codificación. Esta sección describe los modelos de codificación potencialmente vulnerables y proporciona ejemplos para cada uno, pero debe reconocer que pueden existir variaciones en estos temas. Por lo tanto, se recomienda a los desarrolladores realizar estos patrones como ejemplos y no como una lista exhaustiva de todos los modelos de codificación potencialmente vulnerables.

En general, predicción de bifurcación relacionadas con condicional de ejecución especulativa lado canales puede presentar cuando una expresión condicional funciona en los datos que pueden ser controlados o influidos por un contexto de menor confianza. Por ejemplo, esto puede incluir expresiones condicionales que se usan en `if`, `for`, `while`, `switch`, o instrucciones ternarias. Para cada una de estas instrucciones, el compilador puede generar una bifurcación condicional que la CPU, puede predecir el destino de bifurcación de en tiempo de ejecución.

Para cada ejemplo, se inserta un comentario con la frase "Especulación de barrera" donde un desarrollador puede introducir una barrera como mitigación. Esto se explica con más detalle en la sección en mitigaciones.

## <a name="speculative-out-of-bounds-load"></a>Especulativa fuera de los límites de carga

Esta categoría de patrones de codificación implica una predicción de bifurcación condicional que conduce a un especulativa fuera de límites acceso a la memoria.

### <a name="array-out-of-bounds-load-feeding-a-load"></a>Incorpore una carga de la carga de matriz fuera de límites

Este modelo de codificación es el patrón de codificación vulnerable descrito originalmente para CVE-2017-5753 (omisión de comprobación de límites). La sección de fondo de este artículo explica este patrón en detalle.

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

De forma similar, una matriz fuera de límites puede producirse carga junto con un bucle que supera su terminación condición debido a una predicción. En este ejemplo, la bifurcación condicional asociado con el `x < buffer_size` expresión puede mispredict y forma especulativa ejecuta el cuerpo de la `for` bucle cuando `x` es mayor o igual que `buffer_size`, lo que da lugar a un especulativa cargar fuera de límites.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadBytes(unsigned char *buffer, unsigned int buffer_size) {
    for (unsigned int x = 0; x < buffer_size; x++) {
        // SPECULATION BARRIER
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>Incorpore una bifurcación indirecta de carga de matriz fuera de límites

Este modelo de codificación implica el caso donde puede provocar una predicción de bifurcación condicional una fuera de límites acceso a una matriz de punteros de función, lo que, a continuación, lleva a una bifurcación indirecta para el destino de direcciones que se leyó fuera de límites. El fragmento de código siguiente proporciona un ejemplo que muestra cómo hacerlo. 

En este ejemplo, se proporciona un identificador de mensaje no es de confianza para DispatchMessage a través de la `untrusted_message_id` parámetro. Si `untrusted_message_id` es menor que `MAX_MESSAGE_ID`, a continuación, se utiliza para indizar en una matriz de punteros a función y crear una bifurcación en el destino de bifurcación correspondiente. Este código es seguro para la ejecución de su arquitectura, pero si la CPU mispredicts la bifurcación condicional, podría producir en `DispatchTable` está indizando `untrusted_message_id` cuando su valor es mayor o igual que `MAX_MESSAGE_ID`, provocando así un acceso fuera de límites. Esto podría resultar en ejecución especulativa desde una dirección de destino de bifurcación que se deriva más allá de los límites de la matriz que podría provocar la divulgación de información según el código que se ejecuta de forma especulativa.

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

Como en el caso de una matriz fuera de los límites de carga incorpore carga otro, esta condición también puede surgir junto con un bucle que supera su condición terminación debido a una predicción.

## <a name="speculative-type-confusion"></a>Confusiones especulativa tipo

Esta categoría se ocupa de patrones que pueden dar lugar a un confusiones especulativa de tipo de codificación. Esto se produce cuando se tiene acceso a memoria con un tipo incorrecto a lo largo de una ruta de acceso no arquitectura durante la ejecución especulativa. Predicción de bifurcación condicional y omisión de almacén especulativa potencialmente puede provocar un confusiones especulativa de tipo. 

De omisión de almacén especulativa, esto puede ocurrir en escenarios donde un compilador reutiliza una ubicación de la pila para las variables de varios tipos. Esto es porque el almacén de la arquitectura de una variable de tipo `A` puede omitirse, lo que permite la carga de tipo `A` forma especulativa ejecutar antes de que se asigna a la variable. Si la variable anteriormente almacenada es de un tipo diferente, esto puede crear las condiciones para una confusiones especulativa de tipo.

Para la predicción de bifurcación condicional, el siguiente fragmento de código se usará para describir diversas condiciones que confusiones especulativa tipo pueden dar lugar a.

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

### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>Confusiones especulativa tipo dan lugar a una carga fuera de límites

Este modelo de codificación implica el caso donde un confusiones especulativa tipo pueden dar lugar a un fuera de límites o acceso ¿no entiende el tipo de campo donde el valor cargado fuentes de distribución de una dirección de carga posteriores. Esto es similar al modelo de codificación fuera de los límites de matriz, pero se manifiesta a través de una alternativa a la secuencia de codificación, como se indicó anteriormente. En este ejemplo, el contexto de un atacante podría provocar que el contexto de la víctima ejecutar `ProcessType` varias veces con un objeto de tipo `CType1` (`type` es igual al campo `Type1`). Esto tendrá el efecto de entrenamiento de la bifurcación condicional para la primera `if` instrucción no predecir tomada. El contexto de ataque, a continuación, puede hacer el contexto de la víctima ejecutar `ProcessType` con un objeto del tipo `CType2`. Esto puede producir un confusiones especulativa tipo si la directiva de bifurcación para el primer `if` instrucción mispredicts y ejecuta el cuerpo de la `if` instrucción, lo que convertir un objeto del tipo `CType2` a `CType1`. Puesto que `CType2` es menor que `CType1`, el acceso a la memoria para `CType1::field2` resultado en un especulativa fuera de límites cargará de datos que pueden ser secretos. Este valor, a continuación, se utiliza en una carga de `shared_buffer` que puede crear efectos secundarios observables, al igual que con la matriz fuera de límites en el ejemplo se se ha descrito anteriormente.

### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>Confusiones especulativa tipo dan lugar a una bifurcación indirecta

Este modelo de codificación implica el caso de que pueden producir un confusiones especulativa de tipo en una bifurcación indirecta no segura durante la ejecución especulativa. En este ejemplo, el contexto de un atacante podría provocar que el contexto de la víctima ejecutar `ProcessType` varias veces con un objeto de tipo `CType2` (`type` es igual al campo `Type2`). Esto tendrá el efecto de entrenamiento de la bifurcación condicional para la primera `if` instrucción que se debe tener cuidado y `else if` instrucción que no se debe realizar. El contexto de ataque, a continuación, puede hacer el contexto de la víctima ejecutar `ProcessType` con un objeto del tipo `CType1`. Esto puede producir un confusiones especulativa tipo si la directiva de bifurcación para el primer `if` instrucción predice realizada y `else if` instrucción predice no tomada, ejecutar, por tanto, el cuerpo de la `else if` y convertir un objeto del tipo `CType1` a `CType2`. Puesto que la `CType2::dispatch_routine` campo se superpone a la `char` matriz `CType1::field1`, esto podría resultar en una bifurcación especulativa indirecta a un destino de bifurcación no deseadas. Si el contexto ataca puede controlar los valores de byte en el `CType1::field1` matriz, pueden ser capaces de controlar la dirección de destino de bifurcación.

## <a name="speculative-uninitialized-use"></a>Uso sin inicializar especulativa

Esta categoría de patrones de codificación implica escenarios donde puede obtener acceso a memoria sin inicializar y usarla para introducir una carga posterior o rama indirecta ejecución especulativa. Para que estos modelos de codificación que se puede aprovechar, un atacante debe ser capaz de controlar o pueda influir en el contenido de la memoria que se usa sin que se va a inicializar el contexto que se está usando en.

### <a name="speculative-uninitialized-use-leading-to-an-out-of-bounds-load"></a>Uso sin inicializar especulativa dan lugar a una carga fuera de límites

Un uso sin inicializar especulativo puede dañar un fuera de los límites de carga con un valor controlada por el atacante. En el ejemplo siguiente, el valor de `index` se asigna `trusted_index` en todas las rutas de arquitectura y `trusted_index` se supone que es menor o igual que `buffer_size`. Sin embargo, dependiendo del código generado por el compilador, es posible que se puede producir una omisión de almacén especulativa que permite la carga de `buffer[index]` y expresiones dependientes para ejecutar antes de la asignación a `index`. Si esto ocurre, un valor sin inicializar para `index` se usará como el desplazamiento `buffer` que podría permitir que un atacante leer información confidencial fuera de límites y se transmiten a través de un canal de lado a través de la carga dependiente de `shared_buffer` .

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

### <a name="speculative-uninitialized-use-leading-to-an-indirect-branch"></a>Uso sin inicializar especulativa dan lugar a una bifurcación indirecta

Un uso sin inicializar especulativo puede generar una bifurcación indirecta donde el destino de bifurcación es controlado por un atacante. En el ejemplo siguiente, `routine` se les asigna `DefaultMessageRoutine1` o `DefaultMessageRoutine` dependiendo del valor de `mode`. En la ruta de la arquitectura, el resultado será `routine` siempre está inicializando por delante de la bifurcación indirecta. Sin embargo, según el código generado por el compilador, una omisión especulativa almacén se puede producir que permite la bifurcación indirecta a través de `routine` que se ejecute de forma especulativa por delante de la asignación a `routine`. Si esto ocurre, un atacante puede ejecutar de forma especulativa desde una dirección arbitraria, suponiendo que el atacante puede influir en o controlar el valor sin inicializar de `routine`.

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

Si se realizan cambios en código fuente se pueden mitigar vulnerabilidades de canal de lado de ejecución especulativa. Estos cambios pueden implicar mitigar instancias específicas de una vulnerabilidad, por ejemplo, mediante la adición de un *barrera especulación*, o mediante la realización de cambios en el diseño de una aplicación para que la información confidencial no estén accesibles para especulativa ejecución.

### <a name="speculation-barrier-via-manual-instrumentation"></a>Barrera especulación a través de la instrumentación manual

A *barrera especulación* se puede insertar manualmente por un desarrollador para impedir la ejecución especulativa de continuar a lo largo de una ruta de acceso no arquitectónicas. Por ejemplo, un desarrollador puede insertar una barrera de especulación antes de un modelo de codificación peligroso en el cuerpo de un bloque condicional, ya sea al principio del bloque (después de la bifurcación condicional) o antes de la primera carga de preocupación. Esto evitará que una predicción de bifurcación condicional de ejecutarse el código peligroso en una ruta de acceso no arquitectura serializando la ejecución. La secuencia de barrera especulación difiere por la arquitectura de hardware como se describe en la tabla siguiente:

|Arquitectura|Barrera especulación intrínseco para CVE-2017-5753|Barrera especulación intrínseco para CVE-2018-3639|
|----------------|----------------|----------------|
|x86/x64|_mm_lfence()|_mm_lfence()|
|ARM|actualmente, no disponible|__dsb(0)|
|ARM64|actualmente, no disponible|__dsb(0)|

Por ejemplo, el modelo de código siguiente se puede mitigar mediante el uso de la `_mm_lfence` intrínseco tal y como se muestra a continuación.

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

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>Barrera especulación a través de la instrumentación de tiempo de compilación

El compilador de Visual C++ en Visual Studio de 2017 (a partir de la versión 15.5.5) incluye compatibilidad con la `/Qspectre` conmutador que inserta automáticamente una barrera de especulación para un conjunto limitado de modelos de codificación potencialmente vulnerables relacionados con CVE-2017-5753. La documentación de la [/Qspectre](https://docs.microsoft.com/en-us/cpp/build/reference/qspectre) marca proporciona más información sobre sus efectos y uso. Es importante tener en cuenta que esta marca no cubre todos los modelos de codificación potencialmente vulnerables y por lo tanto a los desarrolladores no deben confiar en él como mitigación completa para esta clase de vulnerabilidades.

## <a name="masking-array-indices"></a>Índices de matriz de enmascaramiento

En casos donde un especulativa fuera de los límites de carga se puede producir, el índice de matriz puede ser limitado fuertemente en la ruta de acceso no arquitectónicos y arquitectura agregando lógica para enlazar explícitamente el índice de matriz. Por ejemplo, si una matriz se puede asignar a un tamaño que se alinea a la potencia de dos, puede introducir una máscara simple. Esto se ilustra en el ejemplo siguiente, donde se supone que `buffer_size` se alinea a la potencia de dos. Esto garantiza que `untrusted_index` es siempre menor que `buffer_size`, aunque se produzca una predicción de bifurcación condicional y `untrusted_index` se pasa con un valor mayor o igual que `buffer_size`.

Debe tenerse en cuenta que el enmascaramiento de índice que se realizan en este caso podrían experimentar omisión de almacén especulativa según el código generado por el compilador.

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

## <a name="removing-sensitive-information-from-memory"></a>Quitar información confidencial de la memoria

Otra técnica que puede utilizarse para mitigar vulnerabilidades de canal de lado de ejecución especulativa es quitar información confidencial de la memoria. Los desarrolladores de software pueden buscar oportunidades para refactorizar la aplicación que información confidencial no sea accesible durante la ejecución especulativa. Esto puede realizarse mediante la refactorización el diseño de una aplicación para aislar la información confidencial en procesos independientes. Por ejemplo, una aplicación de explorador web puede intentar aislar los datos asociados a cada origen de web en procesos independientes, lo que impide que un proceso al tener acceso a datos entre orígenes a través de la ejecución especulativa.

## <a name="see-also"></a>Vea también

[Instrucciones para mitigar las vulnerabilidades del lado de canal de ejecución especulativa](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)
[mitigación de vulnerabilidades de hardware de canal de lado de ejecución especulativa](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)