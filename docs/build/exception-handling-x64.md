---
title: Control de excepciones x64
ms.date: 10/14/2019
helpviewer_keywords:
- C++ exception handling, x64
- exception handling, x64
ms.assetid: 41fecd2d-3717-4643-b21c-65dcd2f18c93
ms.openlocfilehash: eff4f1a22512b597b5479dbcaabcc9d5fc93c940
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303206"
---
# <a name="x64-exception-handling"></a>Control de excepciones x64

Información general sobre el control estructurado de C++ excepciones y las convenciones de codificación y el comportamiento del control de excepciones en x64. Para obtener información general sobre el control de excepciones, vea [control C++de excepciones en Visual ](../cpp/exception-handling-in-visual-cpp.md).

## <a name="unwind-data-for-exception-handling-debugger-support"></a>Desenredar datos para el control de excepciones, compatibilidad del depurador

Se necesitan varias estructuras de datos para el control de excepciones y la compatibilidad con la depuración.

### <a name="struct-runtime_function"></a>RUNTIME_FUNCTION (Estructura)

El control de excepciones basado en tablas requiere una entrada de tabla para todas las funciones que asignan espacio de pila o llaman a otra función (por ejemplo, funciones no hoja). Las entradas de la tabla de funciones tienen el formato:

|||
|-|-|
|ULONG|Dirección de inicio de función|
|ULONG|Dirección final de la función|
|ULONG|Dirección de información de desenredo|

La estructura de RUNTIME_FUNCTION debe estar alineada en DWORD en la memoria. Todas las direcciones son relativas a la imagen, es decir, son desplazamientos de 32 bits de la dirección inicial de la imagen que contiene la entrada de la tabla de funciones. Estas entradas se ordenan y se colocan en la sección. pdata de una imagen de PE32 +. En el caso de las funciones generadas dinámicamente [compiladores JIT], el tiempo de ejecución para admitir estas funciones debe usar RtlInstallFunctionTableCallback o RtlAddFunctionTable para proporcionar esta información al sistema operativo. Si no lo hace, se producirá un control de excepciones y depuración de procesos no confiables.

### <a name="struct-unwind_info"></a>UNWIND_INFO (Estructura)

La estructura de información de datos de desenredo se utiliza para registrar los efectos que una función tiene en el puntero de pila y donde los registros no volátiles se guardan en la pila:

|||
|-|-|
|UBYTE: 3|Versión|
|UBYTE: 5|Marcas|
|UBYTE|Tamaño del prólogo|
|UBYTE|Recuento de códigos de desenredado|
|UBYTE: 4|Registro de marco|
|UBYTE: 4|Desplazamiento de registro de marco (escalado)|
|USHORT \* n|Matriz de códigos de desenredado|
|variable|Puede tener el formato (1) o (2) por debajo|

(1) controlador de excepciones

|||
|-|-|
|ULONG|Dirección del controlador de excepciones|
|variable|Datos de controlador específicos del lenguaje (opcional)|

(2) información de desenredo encadenada

|||
|-|-|
|ULONG|Dirección de inicio de función|
|ULONG|Dirección final de la función|
|ULONG|Dirección de información de desenredo|

La estructura de UNWIND_INFO debe estar alineada en DWORD en la memoria. Esto es lo que significa cada campo:

- **Versión**

   Número de versión de los datos de desenredado, actualmente 1.

- **Marcas**

   Actualmente hay tres marcas definidas:

   |Marcar|Descripción|
   |-|-|
   |`UNW_FLAG_EHANDLER`| La función tiene un controlador de excepciones que debe llamarse al buscar funciones que necesitan examinar excepciones.|
   |`UNW_FLAG_UHANDLER`| La función tiene un controlador de terminación que debe llamarse al desenredar una excepción.|
   |`UNW_FLAG_CHAININFO`| Esta estructura de información de desenredo no es la principal para el procedimiento. En su lugar, la entrada de información de desenredo encadenada es el contenido de una entrada de RUNTIME_FUNCTION anterior. Para obtener más información, consulte [estructuras de información de desenredo encadenadas](#chained-unwind-info-structures). Si se establece esta marca, se deben borrar las marcas UNW_FLAG_EHANDLER y UNW_FLAG_UHANDLER. Además, el registro de marco y los campos de asignación de pila fija deben tener los mismos valores que en la información de desenredo principal.|

- **Tamaño del prólogo**

   Longitud del prólogo de la función en bytes.

- **Recuento de códigos de desenredado**

   Número de ranuras de la matriz de códigos de desenredado. Algunos códigos de desenredado, por ejemplo UWOP_SAVE_NONVOL, requieren más de una ranura en la matriz.

- **Registro de marco**

   Si es distinto de cero, la función usa un puntero de marco (FP) y este campo es el número del registro no volátil que se usa como puntero de marco, usando la misma codificación para el campo de información de la operación de UNWIND_CODE nodos.

- **Desplazamiento de registro de marco (escalado)**

   Si el campo de registro del marco es distinto de cero, este campo es el desplazamiento a escala de RSP que se aplica al registro de FP cuando se establece. El registro de FP real se establece en RSP + 16 \* este número, lo que permite desplazamientos desde 0 hasta 240. Este desplazamiento permite señalar el registro de FP en el medio de la asignación de la pila local para los marcos de pila dinámicos, lo que permite una mayor densidad de código a través de instrucciones más cortas. (Es decir, más instrucciones pueden utilizar el formato de desplazamiento con signo de 8 bits).

- **Matriz de códigos de desenredado**

   Matriz de elementos que explica el efecto del prólogo en los registros no volátiles y RSP. Vea la sección sobre UNWIND_CODE de los significados de elementos individuales. A efectos de alineación, esta matriz siempre tiene un número par de entradas y la entrada final puede no usarse. En ese caso, la matriz es una longitud superior a la indicada por el campo recuento de códigos de desenredado.

- **Dirección del controlador de excepciones**

   Un puntero relativo a la imagen para la excepción o controlador de terminación específico del idioma de la función, si Flag UNW_FLAG_CHAININFO está claro y se ha establecido una de las marcas UNW_FLAG_EHANDLER o UNW_FLAG_UHANDLER.

- **Datos de controlador específicos del lenguaje**

   Los datos del controlador de excepciones específico del idioma de la función. El formato de estos datos no está especificado y está determinado por el controlador de excepciones específico en uso.

- **Información de desenredo encadenada**

   Si se establece Flag UNW_FLAG_CHAININFO, la estructura de UNWIND_INFO finaliza con tres UWORDs.  Estos UWORDs representan la información RUNTIME_FUNCTION para la función del desenredado encadenado.

### <a name="struct-unwind_code"></a>UNWIND_CODE (Estructura)

La matriz de códigos de desenredado se utiliza para registrar la secuencia de operaciones en el prólogo que afectan a los registros no volátiles y a RSP. Cada elemento de código tiene este formato:

|||
|-|-|
|UBYTE|Desplazamiento en el prólogo|
|UBYTE: 4|Código de operación de desenredado|
|UBYTE: 4|Información de la operación|

La matriz se ordena por orden descendente de desplazamiento en el prólogo.

#### <a name="offset-in-prolog"></a>Desplazamiento en el prólogo

Desplazamiento (desde el principio del prólogo) del final de la instrucción que realiza esta operación, más 1 (es decir, el desplazamiento del inicio de la instrucción siguiente).

#### <a name="unwind-operation-code"></a>Código de operación de desenredado

Nota: algunos códigos de operación requieren un desplazamiento sin signo a un valor en el marco de pila local. Este desplazamiento es desde el principio, es decir, la dirección más baja de la asignación de pila fija. Si el campo de registro de marco del UNWIND_INFO es cero, este desplazamiento es de RSP. Si el campo de registro del marco es distinto de cero, este desplazamiento es desde donde se encontró RSP cuando se estableció el registro de FP. Es igual al registro de FP menos el desplazamiento de registro de FP (16 \* el desplazamiento de registro del marco escalado en el UNWIND_INFO). Si se usa un registro FP, el código de desenredado que toma un desplazamiento solo debe usarse después de establecer el registro FP en el prólogo.

En todos los códigos de tiempo excepto `UWOP_SAVE_XMM128` y `UWOP_SAVE_XMM128_FAR`, el desplazamiento es siempre un múltiplo de 8, ya que todos los valores de pila de interés se almacenan en límites de 8 bytes (la pila es siempre de 16 bytes alineada). En el caso de los códigos de operación que toman un desplazamiento corto (menos de 512 k), el USHORT final de los nodos de este código contiene el desplazamiento dividido entre 8. En el caso de los códigos de operación que toman un desplazamiento largo (512K < = offset < 4 GB), los dos nodos de USHORT finales de este código contienen el desplazamiento (en formato Little-endian).

En el caso de los códigos de operación `UWOP_SAVE_XMM128` y `UWOP_SAVE_XMM128_FAR`, el desplazamiento es siempre un múltiplo de 16, ya que todas las operaciones de XMM de 128 bits deben realizarse en una memoria alineada de 16 bytes. Por lo tanto, se usa un factor de escala de 16 para `UWOP_SAVE_XMM128`, lo que permite desplazamientos de menos de 1 millón.

El código de operación de desenredo es uno de estos valores:

- `UWOP_PUSH_NONVOL` (0) 1 nodo

  Inserte un registro entero no volátil y disminuya RSP en 8. La información de la operación es el número del registro. Debido a las restricciones en los registros, los códigos de desenredado de `UWOP_PUSH_NONVOL` deben aparecer en primer lugar en el prólogo y, en consecuencia, en el último lugar de la matriz de códigos de desenredado. Esta ordenación relativa se aplica a todos los demás códigos de desenredado excepto `UWOP_PUSH_MACHFRAME`.

- `UWOP_ALLOC_LARGE` (1) 2 o 3 nodos

  Asignar un área de gran tamaño en la pila. Hay dos formas. Si la información de la operación es igual a 0, el tamaño de la asignación dividido entre 8 se registra en la siguiente ranura, lo que permite una asignación de hasta 512 k. Si la información de la operación es igual a 1, el tamaño sin escala de la asignación se registra en las dos ranuras siguientes en formato Little-endian, lo que permite asignaciones hasta 4GB-8.

- `UWOP_ALLOC_SMALL` (2) 1 nodo

  Asignar un área de pequeño tamaño en la pila. El tamaño de la asignación es el campo de información de la operación \* 8 + 8, lo que permite asignaciones entre 8 y 128 bytes.

  El código de desenredado de una asignación de pila siempre debe usar la codificación más corta posible:

  |**Tamaño de asignación**|**Código de desenredado**|
  |-|-|
  |de 8 a 128 bytes|`UWOP_ALLOC_SMALL`|
  |de 136 a 512 KB-8 bytes|`UWOP_ALLOC_LARGE`, información de la operación = 0|
  |512 k a 4G-8 bytes|`UWOP_ALLOC_LARGE`, información de la operación = 1|

- `UWOP_SET_FPREG` (3) 1 nodo

  Establezca el registro de puntero de marco estableciendo el registro en algún desplazamiento del RSP actual. El desplazamiento es igual al campo de desplazamiento del registro de marco (escalado) en el UNWIND_INFO \* 16, lo que permite desplazamientos de 0 a 240. El uso de un desplazamiento permite establecer un puntero de marco que apunta a la mitad de la asignación de pila fija, lo que ayuda a la densidad del código al permitir que más accesos usen formatos cortos de instrucción. El campo información de la operación está reservado y no debe usarse.

- `UWOP_SAVE_NONVOL` (4) 2 nodos

  Guarde un registro entero no volátil en la pila utilizando una tabla MOV en lugar de una inserciones. Este código se usa principalmente para el *ajuste de reducción*, donde un registro no volátil se guarda en la pila en una posición que se asignó previamente. La información de la operación es el número del registro. El desplazamiento de la pila escalado por 8 se registra en la siguiente ranura de código de operación de desenredado, tal y como se describe en la nota anterior.

- `UWOP_SAVE_NONVOL_FAR` (5) 3 nodos

  Guarde un registro de entero no volátil en la pila con un desplazamiento largo mediante una tabla MOV en lugar de una inserciones. Este código se usa principalmente para el *ajuste de reducción*, donde un registro no volátil se guarda en la pila en una posición que se asignó previamente. La información de la operación es el número del registro. El desplazamiento de la pila sin escala se registra en las dos ranuras de código de operación de desenredado siguientes, como se describe en la nota anterior.

- `UWOP_SAVE_XMM128` (8) 2 nodos

  Guarde todos los 128 bits de un registro XMM no volátil en la pila. La información de la operación es el número del registro. El desplazamiento de la pila escalado por 16 se registra en la siguiente ranura.

- `UWOP_SAVE_XMM128_FAR` (9) 3 nodos

  Guarde todos los 128 bits de un registro XMM no volátil en la pila con un desplazamiento largo. La información de la operación es el número del registro. El desplazamiento de la pila sin escala se registra en las dos ranuras siguientes.

- `UWOP_PUSH_MACHFRAME` (10) 1 nodo

  Inserte un marco de máquina.  Este código de desenredado se usa para registrar el efecto de una interrupción o excepción de hardware. Hay dos formas. Si la información de la operación es igual a 0, se inserta uno de estos marcos en la pila:

  |||
  |-|-|
  |RSP+32|SS|
  |RSP + 24|RSP anterior|
  |RSP + 16|EFLAGS|
  |RSP + 8|CS|
  |RSP|RASGA|

  Si la información de la operación es igual a 1, se ha insertado uno de estos marcos:

  |||
  |-|-|
  |RSP + 40|SS|
  |RSP+32|RSP anterior|
  |RSP + 24|EFLAGS|
  |RSP + 16|CS|
  |RSP + 8|RASGA|
  |RSP|Código de error|

  Este código de desenredado aparece siempre en un prólogo ficticio, que nunca se ejecuta realmente, sino que aparece antes del punto de entrada real de una rutina de interrupción y solo existe para proporcionar un lugar para simular la inserción de un marco de máquina. `UWOP_PUSH_MACHFRAME` registra la simulación, que indica que la máquina ha realizado conceptualmente esta operación:

  1. Extraer dirección de retorno RIP de la parte superior de la pila en *temp*
  
  1. Presionar SS

  1. Enviar RSP anterior

  1. EFLAGS de extracción

  1. CS de extracción

  1. Presione *temp*

  1. Código de error de la operación de envío (si la información operativa es igual a 1)

  La operación `UWOP_PUSH_MACHFRAME` simulada disminuye RSP en 40 (la información de operación es igual a 0) o 48 (la información de operación es igual a 1).

#### <a name="operation-info"></a>Información de la operación

El significado de los bits de información de la operación depende del código de la operación. Para codificar un registro de uso general (entero), se usa esta asignación:

|||
|-|-|
|0|RAX|
|1|RCX|
|2|RDX|
|3|RBX|
|4|RSP|
|5|RBP|
|6|RSI|
|7|RDI|
|de 8 a 15|R8 a R15|

### <a name="chained-unwind-info-structures"></a>Estructuras encadenadas de información de desenredo

Si se establece la marca de UNW_FLAG_CHAININFO, una estructura de información de desenredo es una secundaria y el campo de dirección del controlador de excepciones compartido/encadenado contiene la información de desenredo principal. Este código de ejemplo recupera la información de desenredo principal, suponiendo que `unwindInfo` sea la estructura que tiene establecida la marca UNW_FLAG_CHAININFO.

```cpp
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

La información encadenada es útil en dos situaciones. En primer lugar, se puede usar para segmentos de código no contiguos. Mediante el uso de información encadenada, puede reducir el tamaño de la información de desenredo necesaria, ya que no tiene que duplicar la matriz de códigos de desenredado de la información de desenredo principal.

También puede usar la información encadenada para agrupar el guardado de registros volátiles. El compilador puede retrasar el almacenamiento de algunos registros volátiles hasta que esté fuera del prólogo de entrada de función. Puede grabarlos con información de desenredo principal para la parte de la función antes del código agrupado y, a continuación, configurar la información encadenada con un tamaño distinto de cero de prólogo, donde los códigos de desenredado de la información encadenada reflejan el guardado de los registros no volátiles. En ese caso, los códigos de desenredado son todas las instancias de UWOP_SAVE_NONVOL. No se admite una agrupación que guarde registros no volátiles mediante una inserciones o modifique el registro RSP mediante una asignación de pila fija adicional.

Un elemento UNWIND_INFO que tiene UNW_FLAG_CHAININFO conjunto puede contener una entrada RUNTIME_FUNCTION cuyo elemento UNWIND_INFO también tiene UNW_FLAG_CHAININFO establecido, a veces denominado *varios ajustes de reducción*. Finalmente, los punteros de información de desenredo encadenados llegan a un UNWIND_INFO elemento que UNW_FLAG_CHAININFO desactivado. Este elemento es el elemento de UNWIND_INFO principal, que señala al punto de entrada del procedimiento real.

## <a name="unwind-procedure"></a>Procedimiento para desenredar

La matriz de códigos de desenredado se ordena en orden descendente. Cuando se produce una excepción, el sistema operativo almacena el contexto completo en un registro de contexto. A continuación, se invoca la lógica de envío de excepciones, que ejecuta repetidamente estos pasos para encontrar un controlador de excepciones:

1. Use el RIP actual almacenado en el registro de contexto para buscar una entrada de la tabla RUNTIME_FUNCTION que describa la función actual (o la parte de la función, para entradas de UNWIND_INFO encadenadas).

1. Si no se encuentra ninguna entrada de la tabla de funciones, está en una función de hoja y RSP direcciona directamente el puntero devuelto. El puntero devuelto en [RSP] se almacena en el contexto actualizado, el RSP simulado se incrementa en 8 y el paso 1 se repite.

1. Si se encuentra una entrada de tabla de función, RIP puede encontrarse dentro de tres regiones: a) en un epílogo, b) en el prólogo o en c) en el código que puede estar incluido en un controlador de excepciones.

   - Case a) si el RIP está dentro de un epílogo, el control deja la función, no puede haber ningún controlador de excepciones asociado a esta excepción para esta función y los efectos del epílogo deben continuar para calcular el contexto de la función de llamador. Para determinar si el RIP está dentro de un epílogo, se examina la secuencia de código de RIP en adelante. Si esa secuencia de código puede coincidir con la parte final de un epílogo legítimo, se encuentra en un epílogo y se simula la parte restante del epílogo, con el registro de contexto actualizado cuando se procesa cada instrucción. Tras este procesamiento, el paso 1 se repite.

   - Caso b) si el RIP se encuentra dentro del prólogo, el control no ha entrado en la función, no puede haber ningún controlador de excepciones asociado a esta excepción para esta función, y los efectos del prólogo deben deshacerse para calcular el contexto de la función de llamador. El RIP está dentro del prólogo si la distancia desde el inicio de la función a la RIP es menor o igual que el tamaño del prólogo codificado en la información de desenredo. Los efectos del prólogo se desenrollan recorriendo la matriz de códigos de desenredado de la primera entrada con un desplazamiento menor o igual que el desplazamiento del RIP desde el inicio de la función y, a continuación, deshaciendo el efecto de todos los elementos restantes en la matriz de códigos de desenredado. A continuación, se repite el paso 1.

   - Caso c) si el RIP no está dentro de un prólogo o epílogo y la función tiene un controlador de excepciones (se establece UNW_FLAG_EHANDLER), se llama al controlador específico del lenguaje. El controlador examina sus datos y llama a las funciones de filtro según corresponda. El controlador específico del lenguaje puede devolver que se controló la excepción o que se va a continuar la búsqueda. También puede iniciar un desenredado directamente.

1. Si el controlador específico del lenguaje devuelve un Estado controlado, la ejecución continúa utilizando el registro de contexto original.

1. Si no hay ningún controlador específico del lenguaje o el controlador devuelve un estado "Continue Search", el registro de contexto debe desenredarse en el estado del llamador. Se realiza procesando todos los elementos de la matriz de códigos de desenredado, deshaciendo el efecto de cada uno. A continuación, se repite el paso 1.

Cuando interviene información de desenredo encadenada, se siguen siguiendo estos pasos básicos. La única diferencia es que, al recorrer la matriz de códigos de desenredado para desenredar los efectos de un prólogo, una vez que se alcanza el final de la matriz, se vincula a la información de desenredado principal y se examina toda la matriz de códigos de desenredado. Esta vinculación continúa hasta que llega a una información de desenredo sin la marca de UNW_CHAINED_INFO y, a continuación, finaliza el recorrido de la matriz de códigos de desenredado.

El conjunto más pequeño de datos de desenredo es de 8 bytes. Esto representaría una función que solo asignaba 128 bytes de la pila o menos y, posiblemente, guardó un registro no volátil. También es el tamaño de una estructura de información de desenredo encadenada para un prólogo de longitud cero sin códigos de desenredado.

## <a name="language-specific-handler"></a>Controlador específico del lenguaje

La dirección relativa del controlador específico del lenguaje está presente en el UNWIND_INFO cada vez que se establecen marcas UNW_FLAG_EHANDLER o UNW_FLAG_UHANDLER. Tal y como se describe en la sección anterior, se llama al controlador específico del lenguaje como parte de la búsqueda de un controlador de excepciones o como parte de un desenredado. Tiene este prototipo:

```cpp
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**ExceptionRecord** proporciona un puntero a un registro de excepción, que tiene la definición estándar de Win64.

**EstablisherFrame** es la dirección de la base de la asignación de pila fija para esta función.

**ContextRecord** apunta al contexto de la excepción en el momento en que se generó la excepción (en el caso del controlador de excepciones) o el contexto de "desenredo" actual (en el caso del controlador de terminación).

**DispatcherContext** apunta al contexto del distribuidor para esta función. Tiene esta definición:

```cpp
typedef struct _DISPATCHER_CONTEXT {
    ULONG64 ControlPc;
    ULONG64 ImageBase;
    PRUNTIME_FUNCTION FunctionEntry;
    ULONG64 EstablisherFrame;
    ULONG64 TargetIp;
    PCONTEXT ContextRecord;
    PEXCEPTION_ROUTINE LanguageHandler;
    PVOID HandlerData;
} DISPATCHER_CONTEXT, *PDISPATCHER_CONTEXT;
```

**ControlPc** es el valor de RIP dentro de esta función. Este valor es una dirección de excepción o la dirección en la que el control dejó la función de establecimiento. RIP se usa para determinar si el control se encuentra dentro de una construcción protegida dentro de esta función, por ejemplo, un bloque de `__try` para `__try`/`__except` o `__try`/`__finally`.

**Imagebase** es la base de la imagen (dirección de carga) del módulo que contiene esta función, que se va a agregar a los desplazamientos de 32 bits usados en la entrada de la función y a la información de desenredo para registrar las direcciones relativas.

**FunctionEntry** proporciona un puntero a la entrada de función RUNTIME_FUNCTION que contiene las direcciones relativas de la función y la información de desenredo de la base de datos para esta función.

**EstablisherFrame** es la dirección de la base de la asignación de pila fija para esta función.

**TargetIp** Proporciona una dirección de instrucción opcional que especifica la dirección de continuación del desenredado. Esta dirección se omite si no se especifica **EstablisherFrame** .

**ContextRecord** apunta al contexto de la excepción, para su uso por parte del código de envío o desenredo de excepciones del sistema.

**LanguageHandler** apunta a la rutina del controlador de lenguaje específico del lenguaje que se está llamando.

**HandlerData** apunta a los datos del controlador específicos del lenguaje para esta función.

## <a name="unwind-helpers-for-masm"></a>Aplicaciones auxiliares de desenredo para MASM

Para escribir rutinas de ensamblado adecuadas, hay un conjunto de operaciones que se pueden usar en paralelo con las instrucciones de ensamblado reales para crear los. pdata y. xdata adecuados. Además, hay un conjunto de macros que proporcionan un uso simplificado de las pseudo operaciones para sus usos más comunes.

### <a name="raw-pseudo-operations"></a>Pseudo operaciones sin procesar

|Pseudo operación|Descripción|
|-|-|
|\[de marco de proceso:*ehandler*]|Hace que MASM genere una entrada de tabla de función en. pdata e información de desenredado en. xdata para el comportamiento de desenredado de las excepciones estructuradas de una función.  Si *ehandler* está presente, este procedimiento se especifica en. xdata como el controlador específico del lenguaje.<br /><br /> Cuando se usa el atributo de marco, debe ir seguido de un. Directiva ENDPROLOG.  Si la función es una función de hoja (tal y como se define en los [tipos de función](../build/stack-usage.md#function-types)), el atributo de marco no es necesario, como es el resto de estas pseudo operaciones.|
|. *Registro* de PUSHREG|Genera una entrada de código de desenredado de UWOP_PUSH_NONVOL para el número de registro especificado utilizando el desplazamiento actual en el prólogo.<br /><br /> Úselo solo con registros de enteros no volátiles.  En el caso de inserciones de registros volátiles, utilice. ALLOCSTACK 8, en su lugar|
|. *Registro*de SETFRAME, *desplazamiento*|Rellena el campo de registro de marco y el desplazamiento en la información de desenredado con el registro y el desplazamiento especificados. El desplazamiento debe ser un múltiplo de 16 y menor o igual que 240. Esta Directiva también genera una entrada de código de desenredado de UWOP_SET_FPREG para el registro especificado mediante el desplazamiento de prólogo actual.|
|. *Tamaño* de ALLOCSTACK|Genera un UWOP_ALLOC_SMALL o un UWOP_ALLOC_LARGE con el tamaño especificado para el desplazamiento actual en el prólogo.<br /><br /> El operando de *tamaño* debe ser un múltiplo de 8.|
|. *Registro*de SAVEREG, *desplazamiento*|Genera una entrada de código de desenredado de UWOP_SAVE_NONVOL o UWOP_SAVE_NONVOL_FAR para el registro y el desplazamiento especificados utilizando el desplazamiento de prólogo actual. MASM elige la codificación más eficaz.<br /><br /> el *desplazamiento* debe ser positivo y un múltiplo de 8. el *desplazamiento* es relativo a la base del marco del procedimiento, que suele estar en RSP, o bien, si se usa un puntero de marco, el puntero de marco sin escala.|
|. *Registro*de SAVEXMM128, *desplazamiento*|Genera una entrada de código de desenredado de UWOP_SAVE_XMM128 o UWOP_SAVE_XMM128_FAR para el registro de XMM y el desplazamiento especificados utilizando el desplazamiento de prólogo actual. MASM elige la codificación más eficaz.<br /><br /> el *desplazamiento* debe ser positivo y un múltiplo de 16.  el *desplazamiento* es relativo a la base del marco del procedimiento, que suele estar en RSP, o bien, si se usa un puntero de marco, el puntero de marco sin escala.|
|. PUSHFRAME *código*de \[]|Genera una entrada de código de desenredado de UWOP_PUSH_MACHFRAME. Si se especifica el *código* opcional, se asigna a la entrada de código de desenredado el modificador 1. De lo contrario, el modificador es 0.|
|.ENDPROLOG|Señala el final de las declaraciones de prólogo.  Debe aparecer en los primeros 255 bytes de la función.|

Este es un ejemplo de prólogo de función con uso correcto de la mayoría de los códigos de código:

```MASM
sample PROC FRAME
    db      048h; emit a REX prefix, to enable hot-patching
    push rbp
    .pushreg rbp
    sub rsp, 040h
    .allocstack 040h
    lea rbp, [rsp+020h]
    .setframe rbp, 020h
    movdqa [rbp], xmm7
    .savexmm128 xmm7, 020h ;the offset is from the base of the frame
                           ;not the scaled offset of the frame
    mov [rbp+018h], rsi
    .savereg rsi, 038h
    mov [rsp+010h], rdi
    .savereg rdi, 010h ; you can still use RSP as the base of the frame
                       ; or any other register you choose
    .endprolog

; you can modify the stack pointer outside of the prologue (similar to alloca)
; because we have a frame pointer.
; if we didn't have a frame pointer, this would be illegal
; if we didn't make this modification,
; there would be no need for a frame pointer

    sub rsp, 060h

; we can unwind from the next AV because of the frame pointer

    mov rax, 0
    mov rax, [rax] ; AV!

; restore the registers that weren't saved with a push
; this isn't part of the official epilog, as described in section 2.5

    movdqa xmm7, [rbp]
    mov rsi, [rbp+018h]
    mov rdi, [rbp-010h]

; Here's the official epilog

    lea rsp, [rbp+020h] ; deallocate both fixed and dynamic portions of the frame
    pop rbp
    ret
sample ENDP
```

Para más información sobre el ejemplo de epílogo, consulte el [código de epílogo](prolog-and-epilog.md#epilog-code) en [prólogo y epílogo x64](prolog-and-epilog.md).

### <a name="masm-macros"></a>Macros de MASM

Con el fin de simplificar el uso de las [pseudo operaciones sin procesar](#raw-pseudo-operations), hay un conjunto de macros, definido en ksamd64. Inc, que se puede usar para crear prólogos de procedimiento típicos y epílogos.

|Macro|Descripción|
|-|-|
|alloc_stack(n)|Asigna un marco de pila de n bytes (mediante `sub rsp, n`) y emite la información de desenredo adecuada (. allocstack n)|
|save_reg *reg*, *Loc*|Guarda un registro *de registro no* volátil en la pila en la *Ubicación*de desplazamiento de RSP y emite la información de desenredo adecuada. (. savereg reg, LOC)|
|push_reg *reg*|Envía un registro *reg* no volátil en la pila y emite la información de desenredo adecuada. (. pushreg reg)|
|rex_push_reg *reg*|Guarda un registro no volátil en la pila utilizando una inserciones de 2 bytes y emite la información de desenredo adecuada (. pushreg reg).  Use esta macro si la instrucción de incorporación de cambios es la primera instrucción de la función, para asegurarse de que la función se pueda revisar en caliente.|
|save_xmm128 *reg*, *Loc*|Guarda un *reg* de registro de XMM no volátil en la pila en la *Ubicación*de desplazamiento de RSP y emite la información de desenredo adecuada (. savexmm128 reg, LOC).|
|set_frame *reg*, *offset*|Establece que el *reg* del registro del marco sea el *desplazamiento* de RSP + (mediante un `mov`o un `lea`) y emite la información de desenredo adecuada (. set_frame reg, desplazamiento).|
|push_eflags|Envía el EFLAGS con una instrucción `pushfq` y emite la información de desenredo adecuada (. alloc_stack 8)|

Este es un ejemplo de prólogo de función con el uso adecuado de las macros:

```MASM
sampleFrame struct
    Fill     dq ?; fill to 8 mod 16
    SavedRdi dq ?; Saved Register RDI
    SavedRsi dq ?; Saved Register RSI
sampleFrame ends

sample2 PROC FRAME
    alloc_stack(sizeof sampleFrame)
    save_reg rdi, sampleFrame.SavedRdi
    save_reg rsi, sampleFrame.SavedRsi
    .end_prolog

; function body

    mov rsi, sampleFrame.SavedRsi[rsp]
    mov rdi, sampleFrame.SavedRdi[rsp]

; Here's the official epilog

    add rsp, (sizeof sampleFrame)
    ret
sample2 ENDP
```

## <a name="unwind-data-definitions-in-c"></a>Definiciones de datos de desenredo en C

A continuación se muestra una descripción de C de los datos de desenredado:

```C
typedef enum _UNWIND_OP_CODES {
    UWOP_PUSH_NONVOL = 0, /* info == register number */
    UWOP_ALLOC_LARGE,     /* no info, alloc size in next 2 slots */
    UWOP_ALLOC_SMALL,     /* info == size of allocation / 8 - 1 */
    UWOP_SET_FPREG,       /* no info, FP = RSP + UNWIND_INFO.FPRegOffset*16 */
    UWOP_SAVE_NONVOL,     /* info == register number, offset in next slot */
    UWOP_SAVE_NONVOL_FAR, /* info == register number, offset in next 2 slots */
    UWOP_SAVE_XMM128 = 8, /* info == XMM reg number, offset in next slot */
    UWOP_SAVE_XMM128_FAR, /* info == XMM reg number, offset in next 2 slots */
    UWOP_PUSH_MACHFRAME   /* info == 0: no error-code, 1: error-code */
} UNWIND_CODE_OPS;

typedef union _UNWIND_CODE {
    struct {
        UBYTE CodeOffset;
        UBYTE UnwindOp : 4;
        UBYTE OpInfo   : 4;
    };
    USHORT FrameOffset;
} UNWIND_CODE, *PUNWIND_CODE;

#define UNW_FLAG_EHANDLER  0x01
#define UNW_FLAG_UHANDLER  0x02
#define UNW_FLAG_CHAININFO 0x04

typedef struct _UNWIND_INFO {
    UBYTE Version       : 3;
    UBYTE Flags         : 5;
    UBYTE SizeOfProlog;
    UBYTE CountOfCodes;
    UBYTE FrameRegister : 4;
    UBYTE FrameOffset   : 4;
    UNWIND_CODE UnwindCode[1];
/*  UNWIND_CODE MoreUnwindCode[((CountOfCodes + 1) & ~1) - 1];
*   union {
*       OPTIONAL ULONG ExceptionHandler;
*       OPTIONAL ULONG FunctionEntry;
*   };
*   OPTIONAL ULONG ExceptionData[]; */
} UNWIND_INFO, *PUNWIND_INFO;

typedef struct _RUNTIME_FUNCTION {
    ULONG BeginAddress;
    ULONG EndAddress;
    ULONG UnwindData;
} RUNTIME_FUNCTION, *PRUNTIME_FUNCTION;

#define GetUnwindCodeEntry(info, index) \
    ((info)->UnwindCode[index])

#define GetLanguageSpecificDataPtr(info) \
    ((PVOID)&GetUnwindCodeEntry((info),((info)->CountOfCodes + 1) & ~1))

#define GetExceptionHandler(base, info) \
    ((PEXCEPTION_HANDLER)((base) + *(PULONG)GetLanguageSpecificDataPtr(info)))

#define GetChainedFunctionEntry(base, info) \
    ((PRUNTIME_FUNCTION)((base) + *(PULONG)GetLanguageSpecificDataPtr(info)))

#define GetExceptionDataPtr(info) \
    ((PVOID)((PULONG)GetLanguageSpecificData(info) + 1)
```

## <a name="see-also"></a>Vea también

[Convenciones de software x64](../build/x64-software-conventions.md)
