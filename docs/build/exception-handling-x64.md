---
title: Control de excepciones x64
ms.date: 10/14/2019
helpviewer_keywords:
- C++ exception handling, x64
- exception handling, x64
ms.assetid: 41fecd2d-3717-4643-b21c-65dcd2f18c93
ms.openlocfilehash: eff4f1a22512b597b5479dbcaabcc9d5fc93c940
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303206"
---
# <a name="x64-exception-handling"></a>Control de excepciones x64

Información general sobre el control estructurado de excepciones y las convenciones de codificación y el comportamiento del control de excepciones de C++ en x64. Para obtener información general sobre el control de excepciones, vea [Control de excepciones en Visual C++](../cpp/exception-handling-in-visual-cpp.md).

## <a name="unwind-data-for-exception-handling-debugger-support"></a>Datos de desenredado para la compatibilidad con el control de excepciones y el depurador

Se necesitan varias estructuras de datos para el control de excepciones y la compatibilidad con la depuración.

### <a name="struct-runtime_function"></a>RUNTIME_FUNCTION (Estructura)

El control de excepciones basado en tablas requiere una entrada de tabla para todas las funciones que asignan espacio de pila o llaman a otra función (por ejemplo, funciones no hoja). Las entradas de la tabla de funciones tienen el formato:

|||
|-|-|
|ULONG|Dirección de inicio de la función|
|ULONG|Dirección final de la función|
|ULONG|Dirección de información de desenredado|

La estructura RUNTIME_FUNCTION debe estar alineada en DWORD en la memoria. Todas las direcciones son relativas a la imagen, es decir, son desplazamientos de 32 bits con respecto a la dirección inicial de la imagen que contiene la entrada de la tabla de funciones. Estas entradas se ordenan y se colocan en la sección .pdata de una imagen de PE32+. En el caso de las funciones generadas dinámicamente [compiladores JIT], el tiempo de ejecución para admitir estas funciones debe usar RtlInstallFunctionTableCallback o RtlAddFunctionTable para proporcionar esta información al sistema operativo. Si no lo hace, el control de excepciones y la depuración de procesos no serán confiables.

### <a name="struct-unwind_info"></a>UNWIND_INFO (Estructura)

La estructura de información de datos de desenredado se usa para registrar los efectos de una función en el puntero de pila y dónde se guardan los registros no volátiles en la pila:

|||
|-|-|
|UBYTE: 3|Versión|
|UBYTE: 5|Marcas|
|UBYTE|Tamaño del prólogo|
|UBYTE|Recuento de códigos de desenredado|
|UBYTE: 4|Registro de marco|
|UBYTE: 4|Desplazamiento de registro de marco (a escala)|
|USHORT \* n|Matriz de códigos de desenredado|
|variable|Puede tener el formato (1) o (2) siguiente|

(1) Controlador de excepciones

|||
|-|-|
|ULONG|Dirección del controlador de excepciones|
|variable|Datos del controlador específicos del idioma (opcional)|

(2) Información de desenredado encadenada

|||
|-|-|
|ULONG|Dirección de inicio de la función|
|ULONG|Dirección final de la función|
|ULONG|Dirección de información de desenredado|

La estructura UNWIND_INFO debe estar alineada en DWORD en la memoria. Este es el significado de cada fila:

- **Versión**

   Número de versión de los datos de desenredado, actualmente 1.

- **Marcas**

   Actualmente hay tres marcas definidas:

   |Marcar|Descripción|
   |-|-|
   |`UNW_FLAG_EHANDLER`| La función tiene un controlador de excepciones que se debe llamar al buscar funciones que necesitan examinar excepciones.|
   |`UNW_FLAG_UHANDLER`| La función tiene un controlador de finalización que se debe llamar al desenredar una excepción.|
   |`UNW_FLAG_CHAININFO`| Esta estructura de información de desenredado no es la principal para el procedimiento. En su lugar, la entrada de información de desenredado encadenada es el contenido de una entrada RUNTIME_FUNCTION anterior. Para obtener información, vea [Estructuras encadenadas de información de desenredado](#chained-unwind-info-structures). Si se establece esta marca, se deben borrar las marcas UNW_FLAG_EHANDLER y UNW_FLAG_UHANDLER. Además, el registro de marco y los campos de asignación de pila fija deben tener los mismos valores que en la información de desenredado principal.|

- **Tamaño del prólogo**

   Longitud del prólogo de la función en bytes.

- **Recuento de códigos de desenredado**

   Número de ranuras de la matriz de códigos de desenredado. Algunos códigos de desenredado, por ejemplo UWOP_SAVE_NONVOL, requieren más de una ranura en la matriz.

- **Registro de marco**

   Si es distinto de cero, la función usa un puntero de marco (FP) y este campo es el número del registro no volátil que se usa como puntero de marco, con la misma codificación para el campo de información de la operación de los nodos UNWIND_CODE.

- **Desplazamiento de registro de marco (a escala)**

   Si el campo de registro del marco es distinto de cero, este campo es el desplazamiento a escala con respecto a RSP que se aplica al registro de FP cuando se establece. El registro de FP real se establece en RSP + 16 \* este número, lo que permite desplazamientos desde 0 hasta 240. Este desplazamiento permite señalar el registro de FP en el centro de la asignación de la pila local para los marcos de pila dinámicos, lo que permite una mayor densidad de código mediante instrucciones más cortas. (Es decir, más instrucciones pueden usar el formato de desplazamiento con signo de 8 bits).

- **Matriz de códigos de desenredado**

   Matriz de elementos que explica el efecto del prólogo en los registros no volátiles y RSP. Vea la sección sobre UNWIND_CODE para obtener los significados de elementos individuales. Con fines de alineación, esta matriz siempre tiene un número par de entradas y la entrada final puede no usarse. En ese caso, la matriz es una longitud superior a la indicada por el campo de recuento de códigos de desenredado.

- **Dirección del controlador de excepciones**

   Un puntero relativo a la imagen para la excepción o controlador de finalización específico del idioma de la función, si se desactiva la marca UNW_FLAG_CHAININFO y se ha establecido UNW_FLAG_EHANDLER o UNW_FLAG_UHANDLER.

- **Datos del controlador específico del lenguaje**

   Los datos del controlador de excepciones específico del lenguaje de la función. El formato de estos datos no está especificado y se determina en su totalidad por el controlador de excepciones específico en uso.

- **Información de desenredado encadenada**

   Si se establece la marca UNW_FLAG_CHAININFO, la estructura UNWIND_INFO finaliza con tres elementos UWORD.  Estos elementos UWORD representan la información de RUNTIME_FUNCTION para la función del desenredado encadenado.

### <a name="struct-unwind_code"></a>UNWIND_CODE (Estructura)

La matriz de códigos de desenredado se usa para registrar la secuencia de operaciones en el prólogo que afectan a los registros no volátiles y a RSP. Cada elemento de código tiene este formato:

|||
|-|-|
|UBYTE|Desplazamiento en el prólogo|
|UBYTE: 4|Código de operación de desenredado|
|UBYTE: 4|Información de la operación|

La matriz se ordena por orden descendente de desplazamiento en el prólogo.

#### <a name="offset-in-prolog"></a>Desplazamiento en el prólogo

Desplazamiento (con respecto al principio del prólogo) del final de la instrucción que realiza esta operación, más 1 (es decir, el desplazamiento del inicio de la instrucción siguiente).

#### <a name="unwind-operation-code"></a>Código de operación de desenredado

Nota: Algunos códigos de operación requieren un desplazamiento sin signo a un valor en el marco de pila local. Este desplazamiento se realiza con respecto al principio, es decir, la dirección más baja de la asignación de pila fija. Si el campo de registro de marco de UNWIND_INFO es cero, este desplazamiento es desde RSP. Si el campo de registro del marco es distinto de cero, este desplazamiento se realiza con respecto a la ubicación de RSP cuando se haya establecido el registro de FP. Es igual al registro de FP menos el desplazamiento de registro de FP (16 \* el desplazamiento de registro del marco a escala en UNWIND_INFO). Si se usa un registro de FP, el código de desenredado que toma un desplazamiento solo se debe utilizar después de establecer el registro de FP en el prólogo.

En todos los códigos de operación excepto `UWOP_SAVE_XMM128` y `UWOP_SAVE_XMM128_FAR`, el desplazamiento es siempre un múltiplo de 8, ya que todos los valores de pila de interés se almacenan en límites de 8 bytes (la propia pila siempre tiene una alineación de 16 bytes). En el caso de los códigos de operación que toman un desplazamiento corto (menos de 512K), el valor USHORT final de los nodos de este código contiene el desplazamiento dividido entre 8. En el caso de los códigos de operación que toman un desplazamiento largo (512K <= desplazamiento < 4GB), los dos nodos USHORT finales de este código contienen el desplazamiento (en formato little endian).

En el caso de los códigos de operación `UWOP_SAVE_XMM128` y `UWOP_SAVE_XMM128_FAR`, el desplazamiento es siempre un múltiplo de 16, ya que todas las operaciones de XMM de 128 bits se deben realizar en una memoria alineada de 16 bytes. Por tanto, se usa un factor de escala de 16 para `UWOP_SAVE_XMM128`, lo que permite desplazamientos de menos de 1 millón.

El código de operación de desenredado es uno de estos valores:

- `UWOP_PUSH_NONVOL` (0) 1 nodo

  Inserte un registro entero no volátil y disminuya RSP en 8. La información de la operación es el número del registro. Debido a las restricciones en los epílogos, los códigos de desenredado de `UWOP_PUSH_NONVOL` deben aparecer en primer lugar en el prólogo y, en consecuencia, en el último lugar de la matriz de códigos de desenredado. Esta ordenación relativa se aplica a todos los demás códigos de desenredado excepto `UWOP_PUSH_MACHFRAME`.

- `UWOP_ALLOC_LARGE` (1) 2 o 3 nodos

  Asigne un área de gran tamaño en la pila. Hay dos formas. Si la información de la operación es igual a 0, el tamaño de la asignación dividido entre 8 se registra en la siguiente ranura, lo que permite una asignación de hasta 512K - 8. Si la información de la operación es igual a 1, el tamaño sin escala de la asignación se registra en las dos ranuras siguientes en formato little endian, lo que permite asignaciones de hasta 4GB - 8.

- `UWOP_ALLOC_SMALL` (2) 1 nodo

  Asigne un área de pequeño tamaño en la pila. El tamaño de la asignación es el campo de información de la operación \* 8 + 8, lo que permite asignaciones de entre 8 y 128 bytes.

  El código de desenredado de una asignación de pila siempre debe usar la codificación más corta posible:

  |**Tamaño de la asignación**|**Código de desenredado**|
  |-|-|
  |De 8 a 128 bytes|`UWOP_ALLOC_SMALL`|
  |De 136 a 512K-8 bytes|`UWOP_ALLOC_LARGE`, información de la operación = 0|
  |De 512K a 4G-8 bytes|`UWOP_ALLOC_LARGE`, información de la operación = 1|

- `UWOP_SET_FPREG` (3) 1 nodo

  Para configurar el registro de puntero de marco, establezca el registro en algún desplazamiento del RSP actual. El desplazamiento es igual al campo de desplazamiento del registro de marco (con escala) en UNWIND_INFO \* 16, lo que permite desplazamientos de 0 a 240. El uso de un desplazamiento permite establecer un puntero de marco que apunta al centro de la asignación de pila fija, lo que ayuda a la densidad del código al permitir que más accesos usen formatos cortos de instrucción. El campo de información de la operación está reservado y no se debe usar.

- `UWOP_SAVE_NONVOL` (4) 2 nodos

  Guarde un registro entero no volátil en la pila mediante MOV en lugar de PUSH. Este código se usa principalmente para la *reducción hasta ajustar*, donde un registro no volátil se guarda en la pila en una posición asignada previamente. La información de la operación es el número del registro. El desplazamiento de la pila a escala por 8 se registra en la siguiente ranura de código de operación de desenredado, como se describe en la nota anterior.

- `UWOP_SAVE_NONVOL_FAR` (5) 3 nodos

  Guarde un registro entero no volátil en la pila con un desplazamiento largo mediante MOV en lugar de PUSH. Este código se usa principalmente para la *reducción hasta ajustar*, donde un registro no volátil se guarda en la pila en una posición asignada previamente. La información de la operación es el número del registro. El desplazamiento de la pila sin escala se registra en las dos ranuras de código de operación de desenredado siguientes, como se describe en la nota anterior.

- `UWOP_SAVE_XMM128` (8) 2 nodos

  Guarde todos los 128 bits de un registro XMM no volátil en la pila. La información de la operación es el número del registro. El desplazamiento de la pila con escala de 16 se registra en la ranura siguiente.

- `UWOP_SAVE_XMM128_FAR` (9) 3 nodos

  Guarde todos los 128 bits de un registro XMM no volátil en la pila con un desplazamiento largo. La información de la operación es el número del registro. El desplazamiento de la pila sin escala se registra en las dos ranuras siguientes.

- `UWOP_PUSH_MACHFRAME` (10) 1 nodo

  Inserte un marco de máquina.  Este código de desenredado se usa para registrar el efecto de una interrupción o excepción de hardware. Hay dos formas. Si la información de la operación es igual a 0, uno de estos marcos se inserta en la pila:

  |||
  |-|-|
  |RSP+32|SS|
  |RSP+24|RSP anterior|
  |RSP+16|EFLAGS|
  |RSP+8|CS|
  |RSP|RIP|

  Si la información de la operación es igual a 1, uno de estos marcos se ha insertado:

  |||
  |-|-|
  |RSP+40|SS|
  |RSP+32|RSP anterior|
  |RSP+24|EFLAGS|
  |RSP+16|CS|
  |RSP+8|RIP|
  |RSP|Código de error|

  Este código de desenredado aparece siempre en un prólogo ficticio, que en realidad no se ejecuta nunca, sino que aparece antes del punto de entrada real de una rutina de interrupción y solo existe para proporcionar un lugar a fin de simular la inserción de un marco de equipo. `UWOP_PUSH_MACHFRAME` registra la simulación, que indica que el equipo ha realizado conceptualmente esta operación:

  1. Extracción de la dirección de retorno RIP de la parte superior de la pila en *Temp*
  
  1. Inserción de SS

  1. Inserción del RSP anterior

  1. Inserción de EFLAGS

  1. Inserción de CS

  1. Inserción de *Temp*

  1. Inserción de código de error (si la información de operación es igual a 1)

  La operación `UWOP_PUSH_MACHFRAME` simulada disminuye RSP en 40 (la información de operación es igual a 0) o 48 (la información de operación es igual a 1).

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
|8 a 15|R8 a R15|

### <a name="chained-unwind-info-structures"></a>Estructuras de información de desenredado encadenada

Si se establece la marca UNW_FLAG_CHAININFO, una estructura de información de desenredado es secundaria y el campo de dirección de la información encadenada o el controlador de excepciones compartido contiene la información de desenredado principal. Este código de ejemplo recupera la información de desenredado principal, siempre que `unwindInfo` sea la estructura que tiene establecida la marca UNW_FLAG_CHAININFO.

```cpp
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

La información encadenada es útil en dos situaciones. En primer lugar, se puede usar para segmentos de código no contiguos. Mediante el uso de información encadenada, puede reducir el tamaño de la información de desenredado necesaria, ya que no es necesario duplicar la matriz de códigos de desenredado de la información de desenredado principal.

También puede usar la información encadenada para agrupar el almacenamiento de registros volátiles. Es posible que el compilador retrase el almacenamiento de algunos registros volátiles hasta que esté fuera del prólogo de entrada de la función. Puede grabarlos si coloca la información de desenredado principal para la parte de la función antes del código agrupado y, después, configura la información encadenada con un tamaño de prólogo distinto de cero, donde los códigos de desenredado de la información encadenada reflejen el almacenamiento de los registros no volátiles. En ese caso, todos los códigos de desenredado son instancias de UWOP_SAVE_NONVOL. No se admite una agrupación que guarde registros no volátiles mediante PUSH o que modifique el registro RSP mediante una asignación de pila fija adicional.

Un elemento UNWIND_INFO en el que se establezca UNW_FLAG_CHAININFO puede contener una entrada RUNTIME_FUNCTION cuyo elemento UNWIND_INFO también tenga UNW_FLAG_CHAININFO establecido, lo que en ocasiones se denomina *reducción hasta ajustar múltiple*. En última instancia, los punteros de información de desenredado encadenada llegan a un elemento UNWIND_INFO con UNW_FLAG_CHAININFO desactivado. Este es el elemento UNWIND_INFO principal, que señala al punto de entrada del procedimiento real.

## <a name="unwind-procedure"></a>Procedimiento de desenredado

La matriz de códigos de desenredado se ordena en orden descendente. Cuando se produce una excepción, el sistema operativo almacena el contexto completo en un registro de contexto. Después, se invoca la lógica de envío de excepciones, que ejecuta repetidamente estos pasos para encontrar un controlador de excepciones:

1. Use el valor RIP actual almacenado en el registro de contexto para buscar una entrada de la tabla RUNTIME_FUNCTION que describa la función actual (o la parte de la función, para las entradas UNWIND_INFO encadenadas).

1. Si no se encuentra ninguna entrada de la tabla de funciones, está en una función de hoja y RSP direcciona directamente el puntero devuelto. El puntero devuelto en [RSP] se almacena en el contexto actualizado, el RSP simulado se incrementa en 8 y se repite el paso 1.

1. Si se encuentra una entrada de tabla de función, RIP puede encontrarse dentro de tres regiones: a) en un epílogo, b) en el prólogo o c) en código que puede estar incluido en un controlador de excepciones.

   - Caso a) Si RIP está dentro de un epílogo, el control sale de la función, no puede haber ningún controlador de excepciones asociado a esta excepción para esta función y los efectos del epílogo deben continuar para calcular el contexto de la función que realiza la llamada. Para determinar si RIP está dentro de un epílogo, se examina la secuencia de código desde RIP en adelante. Si esa secuencia de código puede coincidir con la parte final de un epílogo legítimo, entonces se encuentra en un epílogo y se simula la parte restante del epílogo, con la actualización del registro de contexto al procesar cada instrucción. Tras este procesamiento, se repite el paso 1.

   - Caso b) Si RIP está dentro del prólogo, el control no ha entrado en la función, no puede haber ningún controlador de excepciones asociado a esta excepción para esta función y los efectos del prólogo se deben deshacer para calcular el contexto de la función que realiza la llamada. RIP está dentro del prólogo si la distancia desde el inicio de la función a RIP es menor o igual que el tamaño del prólogo codificado en la información de desenredado. Para desenredar los efectos del prólogo se examina la matriz de códigos de desenredado en busca de la primera entrada con un desplazamiento menor o igual que el desplazamiento de RIP desde el inicio de la función y, después, se deshace el efecto de todos los elementos restantes en la matriz de códigos de desenredado. Después se repite el paso 1.

   - Caso c) Si RIP no está dentro de un prólogo o un epílogo, y la función tiene un controlador de excepciones (se establece UNW_FLAG_EHANDLER), se llama al controlador específico del lenguaje. El controlador examina sus datos y llama a las funciones de filtro según corresponda. El controlador específico del lenguaje puede devolver que la excepción se ha controlado o que se va a continuar la búsqueda. También puede iniciar un desenredado directamente.

1. Si el controlador específico del lenguaje devuelve un estado controlado, la ejecución continúa con el registro de contexto original.

1. Si no hay ningún controlador específico del lenguaje o el controlador devuelve un estado de "continuar búsqueda", el registro de contexto se debe desenredar en el estado del autor de la llamada. Para ello, se procesan todos los elementos de la matriz de códigos de desenredado y se deshace el efecto de cada uno. Después se repite el paso 1.

Cuando interviene información de desenredado encadenada, todavía se siguen estos pasos básicos. La única diferencia es que, al recorrer la matriz de códigos de desenredado para desenredar los efectos de un prólogo, una vez que se alcanza el final de la matriz, se vincula a la información de desenredado principal y se examina toda la matriz de códigos de desenredado. Esta vinculación continúa hasta que se llega a información de desenredado sin la marca UNW_CHAINED_INFO y, después, finaliza el recorrido por la matriz de códigos de desenredado.

El conjunto más pequeño de datos de desenredado es de 8 bytes. Esto representaría una función que solo ha asignado 128 bytes de la pila o menos y, posiblemente, ha guardado un registro no volátil. También es el tamaño de una estructura de información de desenredado encadenada para un prólogo de longitud cero sin códigos de desenredado.

## <a name="language-specific-handler"></a>Controlador específico del lenguaje

La dirección relativa del controlador específico del lenguaje está presente en UNWIND_INFO cada vez que se establecen las marcas UNW_FLAG_EHANDLER o UNW_FLAG_UHANDLER. Como se ha descrito en la sección anterior, se llama al controlador específico del lenguaje como parte de la búsqueda de un controlador de excepciones o como parte de un desenredado. Tiene este prototipo:

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

**ContextRecord** apunta al contexto de la excepción en el momento de generar la excepción (en el caso del controlador de excepciones), o bien al contexto de "desenredado" actual (en el caso del controlador de finalización).

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

**ControlPc** es el valor de RIP dentro de esta función. Este valor es una dirección de excepción o la dirección en la que el control ha abandonado la función de establecimiento. Se usa RIP para determinar si el control se encuentra dentro de una construcción protegida dentro de esta función, por ejemplo, un bloque `__try` para `__try`/`__except` o `__try`/`__finally`.

**ImageBase** es la base de imagen (la dirección de carga) del módulo que contiene esta función, que se va a agregar a los desplazamientos de 32 bits que se usan en la entrada de la función y a la información de desenredado para registrar las direcciones relativas.

**FunctionEntry** proporciona un puntero a la entrada de la función RUNTIME_FUNCTION que contiene las direcciones relativas de la función y la base de imagen de la información de desenredado para esta función.

**EstablisherFrame** es la dirección de la base de la asignación de pila fija para esta función.

**TargetIp** proporciona una dirección de instrucción opcional que especifica la dirección de continuación del desenredado. Esta dirección se omite si no se especifica **EstablisherFrame**.

**ContextRecord** apunta al contexto de la excepción, para su uso por parte del código de desenredado o envío de excepciones del sistema.

**LanguageHandler** apunta a la rutina del controlador de lenguaje específico del lenguaje al que se llama.

**HandlerData** apunta a los datos del controlador específico del lenguaje para esta función.

## <a name="unwind-helpers-for-masm"></a>Asistentes de desenredado para MASM

Para escribir rutinas de ensamblado adecuadas, hay un conjunto de pseudo-operaciones que se pueden usar en paralelo con las instrucciones de ensamblado reales para crear los .pdata y .xdata adecuados. Además, hay un conjunto de macros que proporcionan un uso simplificado de las pseudo-operaciones para sus usos más comunes.

### <a name="raw-pseudo-operations"></a>Pseudo-operaciones sin procesar

|Pseudo-operación|Descripción|
|-|-|
|PROC FRAME \[:*ehandler*]|Hace que MASM genere una entrada de tabla de función en .pdata e información de desenredado en .xdata para el comportamiento de desenredado de excepciones estructuradas de una función.  Si *ehandler* está presente, este procedimiento se especifica en .xdata como el controlador específico del lenguaje.<br /><br /> Cuando se usa el atributo FRAME, debe ir seguido de una directiva .ENDPROLOG.  Si la función es una función de hoja (tal y como se define en [Tipos de función](../build/stack-usage.md#function-types)), el atributo FRAME no es necesario, como el resto de estas pseudo-operaciones.|
|.PUSHREG *registro*|Genera una entrada de código de desenredado UWOP_PUSH_NONVOL para el número de registro especificado mediante el desplazamiento actual en el prólogo.<br /><br /> Úselo solo con registros de enteros no volátiles.  En el caso de inserciones de registros volátiles, use .ALLOCSTACK 8, en su lugar|
|.SETFRAME *registro*, *desplazamiento*|Rellena el campo de registro de marco y el desplazamiento en la información de desenredado con el registro y el desplazamiento especificados. El desplazamiento debe ser un múltiplo de 16 y menor o igual que 240. Esta directiva también genera una entrada de código de desenredado UWOP_SET_FPREG para el registro especificado mediante el desplazamiento de prólogo actual.|
|.ALLOCSTACK *tamaño*|Genera una entrada UWOP_ALLOC_SMALL o UWOP_ALLOC_LARGE con el tamaño especificado para el desplazamiento actual en el prólogo.<br /><br /> El operando *tamaño* debe ser un múltiplo de 8.|
|.SAVEREG *registro*, *desplazamiento*|Genera una entrada de código de desenredado UWOP_SAVE_NONVOL o UWOP_SAVE_NONVOL_FAR para el registro y el desplazamiento especificados mediante el desplazamiento de prólogo actual. MASM elige la codificación más eficaz.<br /><br /> *desplazamiento* debe ser positivo y un múltiplo de 8. *desplazamiento* es relativo a la base del marco del procedimiento, que suele estar en RSP, o bien, si se usa un puntero de marco, el puntero de marco sin escala.|
|.SAVEXMM128 *registro*, *desplazamiento*|Genera una entrada de código de desenredado UWOP_SAVE_XMM128 o UWOP_SAVE_XMM128_FAR para el registro XMM y el desplazamiento especificados mediante el desplazamiento de prólogo actual. MASM elige la codificación más eficaz.<br /><br /> *desplazamiento* debe ser positivo y un múltiplo de 16.  *desplazamiento* es relativo a la base del marco del procedimiento, que suele estar en RSP, o bien, si se usa un puntero de marco, el puntero de marco sin escala.|
|.PUSHFRAME \[*código*]|Genera una entrada de código de desenredado UWOP_PUSH_MACHFRAME. Si se especifica el valor *código* opcional, la entrada de código de desenredado recibe el modificador 1. De lo contrario, el modificador es 0.|
|.ENDPROLOG|Señala el final de las declaraciones de prólogo.  Debe aparecer en los primeros 255 bytes de la función.|

Este es un ejemplo de prólogo de función con el uso correcto de la mayoría de los códigos de operación:

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

Para obtener más información sobre el ejemplo de epílogo, vea [Código de epílogo](prolog-and-epilog.md#epilog-code) en [Prólogo y epílogo de x64](prolog-and-epilog.md).

### <a name="masm-macros"></a>Macros de MASM

Con el fin de simplificar el uso de las [pseudo-operaciones sin procesar](#raw-pseudo-operations), se puede utilizar un conjunto de macros (definido en ksamd64.inc) para crear prólogos y epílogos de procedimiento típicos.

|Macro|Descripción|
|-|-|
|alloc_stack(n)|Asigna un marco de pila de n bytes (mediante `sub rsp, n`) y emite la información de desenredado adecuada (.allocstack n)|
|save_reg *reg*, *loc*|Guarda un registro no volátil *reg* en la pila en el desplazamiento de RSP *loc* y emite la información de desenredado adecuada. (.savereg reg, loc)|
|push_reg *reg*|Inserta un registro no volátil *reg* en la pila y emite la información de desenredado adecuada. (.pushreg reg)|
|rex_push_reg *reg*|Guarda un registro no volátil en la pila mediante una inserción de 2 bytes y emite la información de desenredado adecuada (.pushreg reg).  Use esta macro si la instrucción de inserción es la primera de la función, para asegurarse de que a la función se le pueda aplicar una revisión activa.|
|save_xmm128 *reg*, *loc*|Guarda un registro de XMM no volátil *reg* en la pila en el desplazamiento de RSP *loc* y emite la información de desenredado adecuada (.savexmm128 reg, loc).|
|set_frame *reg*, *desplazamiento*|Establece el registro de marco *reg* para que sea RSP + *desplazamiento* (mediante `mov`o `lea`), y emite la información de desenredado adecuada (.set_frame reg, desplazamiento)|
|push_eflags|Inserta eflags con una instrucción `pushfq` y emite la información de desenredado adecuada (.alloc_stack 8)|

Este es un ejemplo de prólogo de función con el uso correcto de las macros:

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

## <a name="unwind-data-definitions-in-c"></a>Definiciones de datos de desenredado en C

A continuación se muestra una descripción para C de los datos de desenredado:

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
