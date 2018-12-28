---
title: x64 control de excepciones
ms.date: 12/17/2018
helpviewer_keywords:
- C++ exception handling, x64
- exception handling, x64
ms.assetid: 41fecd2d-3717-4643-b21c-65dcd2f18c93
ms.openlocfilehash: 33206dfb885239839c3a64436b6b540fc7d4e6e5
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627545"
---
# <a name="x64-exception-handling"></a>x64 control de excepciones

Información general del control estructurado de excepciones y control de excepciones de C++ y comportamiento en el x64 de convenciones de código. Para obtener información general sobre el control de excepciones, vea [control de excepciones en Visual C++](../cpp/exception-handling-in-visual-cpp.md).

## <a name="unwind-data-for-exception-handling-debugger-support"></a>Datos de control de excepciones, compatibilidad con el depurador de desenredo

Varias estructuras de datos son necesarias para el control de excepciones y compatibilidad con la depuración.

### <a name="struct-runtimefunction"></a>RUNTIME_FUNCTION (Estructura)

Control de excepciones basado en tabla requiere una entrada de tabla para todas las funciones que asignan el espacio de pila o llamar a otra función (por ejemplo, las funciones de hoja). Entradas de la tabla de función tienen el formato:

|||
|-|-|
|ULONG|Dirección de inicio de la función|
|ULONG|Dirección final de la función|
|ULONG|Dirección de la información de desenredo|

La estructura RUNTIME_FUNCTION debe ser DWORD alineada en memoria. Todas las direcciones son relativas a imágenes, es decir, son desplazamientos de 32 bits de la dirección inicial de la imagen que contiene la entrada de la tabla de función. Estas entradas se ordenan y se colocan en la sección .pdata de una imagen PE32 +. Para funciones generadas dinámicamente [compiladores JIT], el tiempo de ejecución para admitir estas funciones debe usar RtlInstallFunctionTableCallback o RtlAddFunctionTable para proporcionar esta información para el sistema operativo. Si no lo hace se producirá en poco confiables control de excepciones y depuración de procesos.

### <a name="struct-unwindinfo"></a>UNWIND_INFO (Estructura)

La estructura de información de datos de desenredado se usa para registrar los efectos de una función en el puntero de pila y donde se guardan los registros no volátiles en la pila:

|||
|-|-|
|UBYTE: 3|Versión|
|UBYTE: 5|Marcas|
|UBYTE|Tamaño de prólogo|
|UBYTE|Recuento de códigos de desenredado|
|UBYTE: 4|Registro de marco|
|UBYTE: 4|Desplazamiento de trama del registro (escalada)|
|USHORT \* n|Matriz de códigos de desenredado|
|variable|Puede ser de formulario (1) o (2), a continuación|

(1) controlador de excepciones

|||
|-|-|
|ULONG|Dirección del controlador de excepciones|
|variable|Datos del controlador específicos del lenguaje (opcional)|

(2) encadenados de información de desenredo

|||
|-|-|
|ULONG|Dirección de inicio de la función|
|ULONG|Dirección final de la función|
|ULONG|Dirección de la información de desenredo|

La estructura UNWIND_INFO debe ser DWORD alineada en memoria. Esto es lo que significa cada campo:

- **Versión**

   Número de versión de los datos de desenredo, actualmente 1.

- **marcas**

   Tres marcadores definidos actualmente:

   |Marcar|Descripción|
   |-|-|
   |`UNW_FLAG_EHANDLER`| La función tiene un controlador de excepciones que debe llamarse al buscar las funciones que necesiten examinar las excepciones.|
   |`UNW_FLAG_UHANDLER`| La función tiene un controlador de terminación que se debe llamar cuando se desenrede una excepción.|
   |`UNW_FLAG_CHAININFO`| Esta estructura no es la principal para el procedimiento de información de desenredo. En su lugar, la información de desenredo encadenada entrada es el contenido de una entrada RUNTIME_FUNCTION anterior. Para obtener información, consulte [Chained información de desenredo](#chained-unwind-info-structures). Si se establece esta marca, los indicadores UNW_FLAG_EHANDLER y UNW_FLAG_UHANDLER deben borrarse. Además, los campos de asignación de registro y de pila se ha corregido de marco deben tener los mismos valores como se muestra en el servidor principal de información de desenredo.|

- **Tamaño de prólogo**

   Longitud del prólogo de función en bytes.

- **Recuento de códigos de desenredado**

   El número de ranuras de la matriz de códigos de desenredado. Algunos códigos de desenredado, por ejemplo, UWOP_SAVE_NONVOL, requieren más de una ranura de la matriz.

- **Registro de marco**

   Si es distinto de cero, a continuación, la función utiliza un puntero de marco (FP), y este campo es el número del registro no volátil usa como el puntero de marco, con la misma codificación para el campo de información de la operación de nodos UNWIND_CODE.

- **Desplazamiento (escala) del registro del marco**

   Si el campo de registro de marco es distinto de cero, este campo es el desplazamiento de escalado desde RSP que se aplica a FP registrar cuando se haya establecido. En el registro de FP real se establece en RSP + 16 \* este número, permitiendo desplazamientos de 0 a 240. Este desplazamiento permite que señala el registro de FP en el centro de la asignación de pila local para marcos de pila dinámicos, lo que permite una mejor densidad del código a través de instrucciones más breves (más instrucciones pueden usar el formulario de desplazamiento de 8 bits con signo).

- **Matriz de códigos de desenredado**

   Una matriz de elementos que se explica el efecto del prólogo en los registros no volátiles y RSP. Consulte la sección sobre UNWIND_CODE para los significados de los elementos individuales. Para la alineación, esta matriz siempre tiene un número par de entradas y la última entrada es potencialmente sin usar. En ese caso, la matriz es uno más tiempo del indicado por el recuento de campo de códigos de desenredado.

- **Dirección del controlador de excepciones**

   Un puntero de imagen relativa a la función de la excepción específica del lenguaje o controlador de finalización, si marca UNW_FLAG_CHAININFO está desactivada y se ha establecido uno de los indicadores UNW_FLAG_EHANDLER o UNW_FLAG_UHANDLER.

- **Datos del controlador específicos del lenguaje**

   Datos del controlador de excepción específica del lenguaje de la función. El formato de estos datos se no se especifica y totalmente determinado por el controlador de excepción específico en uso.

- **Encadenadas de información de desenredo**

   Si se establece la marca UNW_FLAG_CHAININFO la estructura UNWIND_INFO finaliza con tres UWORD.  Estos UWORD representan la información de RUNTIME_FUNCTION para la función de desenredo encadenada.

### <a name="struct-unwindcode"></a>UNWIND_CODE (Estructura)

La matriz de códigos de desenredado se usa para registrar la secuencia de operaciones en el prólogo que afectan a los registros no volátiles y RSP. Cada elemento de código tiene este formato:

|||
|-|-|
|UBYTE|Desplazamiento en el prólogo|
|UBYTE: 4|Código de operación de desenredo|
|UBYTE: 4|Información de la operación|

La matriz está ordenada por orden descendente de desplazamiento en el prólogo.

#### <a name="offset-in-prolog"></a>Desplazamiento en el prólogo

Desplazamiento desde el principio del prólogo del final de la instrucción que realiza esta operación, más 1 (es decir, el desplazamiento del inicio de la instrucción siguiente).

#### <a name="unwind-operation-code"></a>Código de operación de desenredo

Nota: Ciertos códigos de operación requieren un desplazamiento sin signo en un valor en el marco de pila locales. Este desplazamiento es desde el principio, es decir, la dirección de la asignación fija de la pila más baja. Si el campo Frame Register de UNWIND_INFO es cero, este desplazamiento es from RSP. Si el campo Registrar fotograma es distinto de cero, se trata el desplazamiento desde donde se encontraba RSP se estableció el registro de FP. Esto significa que el registro de FP menos el desplazamiento del registro FP (16 \* desplazamiento del registro del marco de texto escalado en UNWIND_INFO). Si se usa un registro de FP, a continuación, cualquier código de desenredado teniendo un desplazamiento solo debe usarse después de que el registro de FP se establece en el prólogo.

Para todos los códigos de operación excepto `UWOP_SAVE_XMM128` y `UWOP_SAVE_XMM128_FAR`, el desplazamiento es siempre un múltiplo de 8, porque toda la pila se almacenan los valores de interés en límites de 8 bytes (la propia pila siempre está alineada de 16 bytes). Para los códigos de operación que toman un desplazamiento corto (menos de 512 KB), el USHORT final en los nodos de este código contiene el desplazamiento dividido por 8. Para los códigos de operación que toman un desplazamiento largo (512 KB < = desplazamiento < 4GB), los dos nodos USHORT finales de este código mantenga el desplazamiento (en formato little-endian).

Para los códigos de operación `UWOP_SAVE_XMM128` y `UWOP_SAVE_XMM128_FAR`, el desplazamiento es siempre un múltiplo de 16, ya que todas las operaciones de registros de XMM de 128 bits se deben producir en la memoria alineada de 16 bytes. Por lo tanto, se utiliza un factor de escala de 16 para `UWOP_SAVE_XMM128`, permitiendo desplazamientos de menos de 1 millón.

El código de operación de desenredo es uno de estos valores:

- `UWOP_PUSH_NONVOL` (0) 1 nodo

  Inserte un registro entero no volátil, disminuyendo RSP en 8. La información de la operación es el número del registro. Debido a las restricciones en los epílogos, `UWOP_PUSH_NONVOL` códigos de desenredado deben aparecer primeros en el prólogo y correspondientemente, los últimos en la matriz de códigos de desenredado. Esta ordenación relativa se aplica a todos los demás códigos de desenredado excepto `UWOP_PUSH_MACHFRAME`.

- `UWOP_ALLOC_LARGE` (1) 2 o 3 nodos

  Asignar un área de gran tamaño en la pila. Hay dos formas. Si la información de la operación es igual a 0, a continuación, el tamaño de la asignación dividido por 8 se registra en la próxima franja, lo que permite una asignación de hasta 512 K - 8. Si la información de la operación es igual a 1, el tamaño de la asignación sin escala se registra en las dos ranuras en formato little-endian, permitiendo asignaciones hasta 4GB - 8.

- `UWOP_ALLOC_SMALL` (2) 1 nodo

  Asignar un área pequeña en la pila. El tamaño de la asignación es el campo de información de la operación \* 8 + 8, permitiendo asignaciones de 8 a 128 bytes.

  El código de desenredo para una asignación de pila siempre debe usar la codificación más corta posible:

  |**Tamaño de asignación**|**Código de desenredado**|
  |-|-|
  |8 a 128 bytes|`UWOP_ALLOC_SMALL`|
  |136 a 512 KB - 8 bytes|`UWOP_ALLOC_LARGE`, información de la operación = 0|
  |512 KB y 4G - 8 bytes|`UWOP_ALLOC_LARGE`, información de la operación = 1|

- `UWOP_SET_FPREG` (3) 1 nodo

  Establecer el registro de puntero de marco configurando el registro con cierto desplazamiento del RSP actual. El desplazamiento es igual del campo (escalado) desplazamiento Frame Register de UNWIND_INFO \* 16, permitiendo desplazamientos de 0 a 240. El uso de un desplazamiento permite establecer un puntero de marco que apunta a la mitad de la asignación fija de la pila, ayudando a la densidad del código, ya que permite más accesos para usar formatos de instrucción cortos. El campo de información de la operación está reservado y no debe usarse.

- `UWOP_SAVE_NONVOL` (4) 2 nodos

  Guardar un registro entero no volátil en la pila utilizando MOV en lugar de una INSERCIÓN. Este código se utiliza principalmente para *reducción*, donde se guarda un registro permanente a la pila en una posición que se había asignada previamente. La información de la operación es el número del registro. El desplazamiento de la pila de escala por 8 se registra en los próximos desenredar la ranura de código de operación, como se describe en la nota anterior.

- `UWOP_SAVE_NONVOL_FAR` (5) 3 nodos

  Guardar un registro entero no volátil en la pila con un desplazamiento largo, utilizando MOV en lugar de una INSERCIÓN. Este código se utiliza principalmente para *reducción*, donde se guarda un registro permanente a la pila en una posición que se había asignada previamente. La información de la operación es el número del registro. El desplazamiento de la pila sin escala se registra en los próximos dos desenredo ranuras de código de operación, como se describe en la nota anterior.

- `UWOP_SAVE_XMM128` (8) 2 nodos

  Guarde todos los 128 bits de un registro XMM no variable en la pila. La información de la operación es el número del registro. El desplazamiento de la pila de escala por 16 se registra en la próxima franja.

- `UWOP_SAVE_XMM128_FAR` (9) 3 nodos

  Guarde todos los 128 bits de un registro XMM no variable en la pila con un desplazamiento largo. La información de la operación es el número del registro. El desplazamiento de la pila sin escala se registra en las siguientes dos ranuras.

- `UWOP_PUSH_MACHFRAME` (10) 1 nodo

  Insertar un marco del equipo.  Esto se usa para registrar el efecto de una interrupción de hardware o la excepción. Hay dos formas. Si la información de la operación es igual a 0, uno de estos marcos se ha insertado en la pila:

  |||
  |-|-|
  |RSP + 32|SS|
  |RSP + 24|RSP anterior|
  |RSP + 16|EFLAGS|
  |RSP + 8|CS|
  |RSP|COPIAR DESDE CD|

  Si la información de la operación es igual a 1, a continuación, uno de estos marcos se ha insertado:

  |||
  |-|-|
  |RSP + 40|SS|
  |RSP + 32|RSP anterior|
  |RSP + 24|EFLAGS|
  |RSP + 16|CS|
  |RSP + 8|COPIAR DESDE CD|
  |RSP|Código de error|

  Este código de desenredado siempre aparece en un prólogo ficticio, lo que realmente nunca se ejecuta, pero en su lugar aparece antes del punto de entrada real de una rutina de interrupción y sólo existe para proporcionar un lugar para simular la inserción de un marco del equipo. `UWOP_PUSH_MACHFRAME` registra la simulación, lo que indica que el equipo ha hecho conceptualmente esta operación:

  1. POP RIP remite desde la parte superior de la pila en *Temp*
  
  1. Insertar SS

  1. Insertar RSP anterior

  1. Insertar EFLAGS

  1. Insertar CS

  1. Insertar *Temp*

  1. Insertar código de Error (si la información de la operación es igual a 1)

  Simulated `UWOP_PUSH_MACHFRAME` reduce operación RSP en 40 (información de la operación es igual a 0) o 48 (información de la operación es igual a 1).

#### <a name="operation-info"></a>Información de la operación

El significado de los bits de información de la operación depende del código de operación. Para codificar un registro de uso general (entero), esta asignación se utiliza:

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
|8 a 15|R8 a R15|

### <a name="chained-unwind-info-structures"></a>Encadenar las estructuras de información de desenredo

Si se establece la marca UNW_FLAG_CHAININFO, a continuación, una estructura de información de desenredo es un secundario y el campo de dirección de excepción-controlador/encadenadas-info compartido contiene la información de desenredo principal. Este código de ejemplo recupera el elemento principal de desenredo información, suponiendo que `unwindInfo` es la estructura que tiene el UNW_FLAG_CHAININFO marcador establecido.

```cpp
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

Información encadenada es útil en dos situaciones. En primer lugar, se puede usar para los segmentos de código no contiguos. Mediante el uso de información encadenada, puede reducir el tamaño de la información de desenredo necesaria, porque no tiene que duplicar la matriz de códigos de desenredado de la información de desenredo principal.

También puede usar información encadenada para agrupar registros volátiles. El compilador puede retrasar guardar algunos registros variables hasta que está fuera del prólogo de función de entrada. Puede registrar esto haciendo que la información de desenredo principal para la parte de la función delante del código agrupado y, a continuación, configurar información encadenada con un tamaño distinto de cero de prólogo, donde los códigos de desenredado de la información encadenada reflejan guardado los registros no volátiles. En ese caso, los códigos de desenredado son todas las instancias de UWOP_SAVE_NONVOL. No se admite una agrupación que guarda los registros no volátiles, mediante una INSERCIÓN o modifica el registro RSP mediante el uso de una asignación fija adicional de la pila.

Un elemento UNWIND_INFO con UNW_FLAG_CHAININFO conjunto puede contener una entrada RUNTIME_FUNCTION cuyo elemento UNWIND_INFO también tenga UNW_FLAG_CHAININFO establecido, a veces denominado *reducción varios*. Finalmente, la información de desenredo encadenada punteros llegan a un elemento UNWIND_INFO con UNW_FLAG_CHAININFO desactivada; Este es el elemento UNWIND_INFO principal, que señala al punto de entrada del procedimiento real.

## <a name="unwind-procedure"></a>Procedimiento para desenredar

La matriz de códigos de desenredado se ordena en orden descendente. Cuando se produce una excepción, se almacena el contexto completo por el sistema operativo en un registro de contexto. A continuación, se invoca la lógica de envío de excepción, que ejecuta repetidamente estos pasos para encontrar un controlador de excepciones:

1. Utilice el RIP actual almacenado en el registro de contexto para buscar una entrada de tabla RUNTIME_FUNCTION que describe la función actual (o parte de la función de entradas UNWIND_INFO encadenadas).

1. Si se encuentra ninguna entrada de tabla de función, a continuación, se encuentra en una función de hoja y RSP ocupa directamente el puntero devuelto. El puntero de devolución en [RSP] se almacena en el contexto actualizado, el RSP simulado se incrementa en 8 y se repite el paso 1.

1. Si se encuentra una entrada de la tabla de función, RIP puede estar en tres regiones: a) en un epílogo, (b) en el prólogo o (c) en el código que puede quedar oculto por un controlador de excepciones.

   - Distingue un) si el RIP es dentro de un epílogo, a continuación, control está abandonando la función, no puede haber ningún controlador de excepciones asociado a esta excepción para esta función y los efectos del epílogo deben continuar para calcular el contexto de la función de llamador. Se examina determinar si el valor de RIP es dentro de un epílogo, la secuencia de código de RIP en. Si ese flujo de código puede coincidir con la parte final de un epílogo legítimo, entonces está en un epílogo y se simula la parte restante del epílogo, con el registro de contexto actualizado como cada instrucción se procesa. Una vez hecho esto, se repite el paso 1.

   - Caso b) si el valor de RIP está en el prólogo, control no ha había entrado en la función, no puede haber ningún controlador de excepciones asociado a esta excepción para esta función y los efectos del prólogo se deben deshacer para calcular el contexto de la función de llamador. El valor de RIP está en el prólogo si la distancia desde el principio de la función a RIP es menor o igual que el tamaño del prólogo codificado en la información de desenredo. Los efectos del prólogo se desenreda mediante exploración hacia delante a través de la matriz de códigos de desenredo para la primera entrada con un desplazamiento menor o igual que el desplazamiento de RIP desde el principio de la función y, después, deshaciendo el efecto de todos los elementos restantes de la matriz de códigos de desenredado. A continuación, se repite el paso 1.

   - Caso c) si el RIP no está dentro de un prólogo o epílogo y la función tiene un controlador de excepciones (UNW_FLAG_EHANDLER está establecido), a continuación, se llama al controlador específico del lenguaje. El controlador examina sus datos y llamadas a funciones filtro según corresponda. Puede devolver el controlador específico del idioma que se ha controlado la excepción o que es la búsqueda debe continuar. También puede iniciar una operación de desenredo directamente.

1. Si el controlador específico del lenguaje devuelve un estado controlado, entonces se puede continuar la ejecución mediante el registro de contexto original.

1. Si no hay ningún controlador específico del lenguaje o el controlador devuelve un estado de "continuar la búsqueda", el registro de contexto debe ser desenredar en el estado del llamador. Esto se logra mediante el procesamiento de todos los elementos de matriz de código de desenredado, deshaciendo el efecto de cada uno. A continuación, se repite el paso 1.

Cuando se encadena desenredo info está relacionado, se siguen estos pasos básicos. La única diferencia es, mientras que recorrer la matriz de códigos de desenredo para desenredar los efectos del prólogo, una vez que se alcanza el final de la matriz, está vinculado a la información de desenredo principal y se recorre la matriz de códigos de desenredado completa que se encuentran allí. Esta vinculación continúa hasta que llegan a una información de desenredo sin el indicador UNW_CHAINED_INFO y, a continuación, termina de recorrer su matriz de códigos de desenredado.

El conjunto más pequeño de datos de desenredo es de 8 bytes. Esto representaría una función que sólo asignó 128 bytes de pila o menos y, posiblemente, se había guarda un registro no volátil. Esto también es el tamaño de un encadenadas desenredo de la estructura de información para un prólogo de longitud cero sin códigos de desenredado.

## <a name="language-specific-handler"></a>Controlador específico del lenguaje

La dirección relativa del controlador específico del lenguaje está presente en UNWIND_INFO cada vez que se establecen marcas UNW_FLAG_EHANDLER o UNW_FLAG_UHANDLER. Como se describe en la sección anterior, el controlador específico del lenguaje se llama como parte de la búsqueda de un controlador de excepciones o como parte de una operación de desenredo. Tiene este prototipo:

```cpp
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**ExceptionRecord** proporciona un puntero a un registro de excepciones, que tiene la definición de Win64 estándar.

**EstablisherFrame** es la dirección de la base de la asignación fija de la pila para esta función.

**ContextRecord** puntos en el contexto de excepción en el momento en que se ha producido la excepción (en el caso del controlador de excepciones) o actual de "desenredo" contexto (en el caso del controlador de terminación).

**DispatcherContext** apunta al contexto del distribuidor para esta función. Tenga esta definición:

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

**ControlPc** es el valor de RIP dentro de esta función. Este valor es una dirección de la excepción o la dirección en la que deja la función establecedora control. Se usa el RIP para determinar si control está dentro de algún tipo de construcción protegido dentro de esta función, por ejemplo, un `__try` bloquear para `__try` / `__except` o `__try` / `__finally`.

**ImageBase** es la imagen base (dirección de carga) del módulo que contiene esta función, para agregarse a los desplazamientos de 32 bits utilizados en la entrada de la función y la información de desenredo para grabar direcciones relativas.

**FunctionEntry** proporciona un puntero a la RUNTIME_FUNCTION que contiene la función de entrada de función y desenredado direcciones relativas de base de la imagen de información para esta función.

**EstablisherFrame** es la dirección de la base de la asignación fija de la pila para esta función.

**TargetIp** suministra una dirección de instrucción opcional que especifica la dirección de continuación de desenredo. Esta dirección se omite si **EstablisherFrame** no se especifica.

**ContextRecord** apunta al contexto de la excepción, para su uso por el código de envío/desenredo de excepción del sistema.

**LanguageHandler** apunta a la rutina del controlador de lenguaje específico del idioma que se llama.

**HandlerData** apunta a los datos del controlador específicos del lenguaje para esta función.

## <a name="unwind-helpers-for-masm"></a>Las aplicaciones auxiliares de MASM de desenredado

Para poder escribir rutinas de ensamblado adecuado, hay un conjunto de pseudoperaciones que puede utilizarse para crear .pdata y .xdata en paralelo con las instrucciones de ensamblado real. Hay también un conjunto de macros que proporcionan un uso simplificado de las operaciones de pseudo para sus usos más comunes.

### <a name="raw-pseudo-operations"></a>Pseudoperaciones sin formato

|Operación de pseudo|Descripción|
|-|-|
|MARCO PROC \[:*ehandler*]|Causas MASM para generar una función de tabla de entrada en .pdata e información de desenredo en .xdata para estructurado de una función comportamiento de control de excepciones de desenredado.  Si *ehandler* está presente, este procedimiento se escribe en .xdata como el controlador específico del lenguaje.<br /><br /> Cuando se usa el atributo de marco, debe ir seguido por una. Directiva ENDPROLOG.  Si la función es una función de hoja (como se define en [tipos de función](../build/stack-usage.md#function-types)) no es necesario, como son el resto de estas pseudoperaciones el atributo de marco.|
|. PUSHREG *registrar*|Genera una entrada de código de desenredado UWOP_PUSH_NONVOL para el número de registro especificado mediante el desplazamiento actual en el prólogo.<br /><br /> Solo debe usarse con registros de enteros no volátil.  Inserciones de los registros volátiles, utilice una. ALLOCSTACK 8 en su lugar|
|. SETFRAME *registrar*, *desplazamiento*|Rellenos en el marco de registrar el campo y el desplazamiento en la información de desenredo mediante el registro especificado y el desplazamiento. El desplazamiento debe ser un múltiplo de 16 y menor o igual a 240. Esta directiva también genera una entrada de código de desenredo UWOP_SET_FPREG para el registro especificado mediante el desplazamiento actual del prólogo.|
|. ALLOCSTACK *tamaño*|Genera una entrada UWOP_ALLOC_SMALL o UWOP_ALLOC_LARGE con el tamaño especificado para el desplazamiento actual en el prólogo.<br /><br /> El *tamaño* operando debe ser un múltiplo de 8.|
|. SAVEREG *registrar*, *desplazamiento*|Genera un UWOP_SAVE_NONVOL o una entrada de código de desenredado UWOP_SAVE_NONVOL_FAR para el registro especificado y el desplazamiento mediante el desplazamiento actual del prólogo. MASM elige la codificación más eficaz.<br /><br /> *desplazamiento* debe ser positivo y un múltiplo de 8. *desplazamiento* es relativa a la base del marco del procedimiento, que se encuentra normalmente en RSP, o bien, si usa un puntero de marco, el puntero de marco sin escala.|
|. Savexmm128 *registrar*, *desplazamiento*|Genera un UWOP_SAVE_XMM128 o una entrada de código de desenredado UWOP_SAVE_XMM128_FAR para el registro XMM especificado y el desplazamiento mediante el desplazamiento actual del prólogo. MASM elige la codificación más eficaz.<br /><br /> *desplazamiento* debe ser positivo y un múltiplo de 16.  *desplazamiento* es relativa a la base del marco del procedimiento, que se encuentra normalmente en RSP, o bien, si usa un puntero de marco, el puntero de marco sin escala.|
|. PUSHFRAME \[ *código*]|Genera una entrada de código de desenredado UWOP_PUSH_MACHFRAME. Si el elemento opcional *código* se especifica, la entrada de código de desenredado se proporciona un modificador de 1. En caso contrario, el modificador es 0.|
|.ENDPROLOG|Señala el final de las declaraciones del prólogo.  Se debe producir en los primeros 255 bytes de la función.|

Este es un ejemplo de prólogo de función con el uso adecuado de la mayoría de los códigos de operación:

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
; if we didn’t have a frame pointer, this would be illegal
; if we didn’t make this modification,
; there would be no need for a frame pointer

    sub rsp, 060h

; we can unwind from the next AV because of the frame pointer

    mov rax, 0
    mov rax, [rax] ; AV!

; restore the registers that weren’t saved with a push
; this isn’t part of the official epilog, as described in section 2.5

    movdqa xmm7, [rbp]
    mov rsi, [rbp+018h]
    mov rdi, [rbp-010h]

; Here’s the official epilog

    lea rsp, [rbp-020h]
    pop rbp
    ret
sample ENDP
```

### <a name="masm-macros"></a>Macros de MASM

Con el fin de simplificar el uso de la [pseudoperaciones sin formato](#raw-pseudo-operations), hay un conjunto de macros, definidas en ksamd64.inc, que puede usarse para crear un procedimiento típico prólogos y epílogos.

|Macro|Descripción|
|-|-|
|alloc_stack(n)|Asigna un marco de pila de n bytes (mediante `sub rsp, n`) y emite adecuado (.allocstack n) de la información de desenredo|
|save_reg *reg*, *loc*|Guarda un registro no volátil *reg* en la pila en RSP desplazamiento *loc*y emite información de desenredo adecuado. (reg .savereg, loc)|
|push_reg *reg*|Inserta un registro permanente *reg* en la pila y emite información de desenredo adecuado. (.pushreg registro)|
|rex_push_reg *reg*|Guardar un registro permanente de la pila mediante una inserción de 2 bytes y emite información (.pushreg registro) se debe usar si la inserción es la primera instrucción en la función para asegurarse de que la función es "n" patchable de desenredo adecuado.|
|save_xmm128 *reg*, *loc*|Guarda un registro XMM no volátil *reg* en la pila en RSP desplazamiento *loc*y emite la correspondiente información de desenredo (reg. savexmm128, loc)|
|set_frame *reg*, *desplazamiento*|Establece el registro de marco *reg* sea RSP + *desplazamiento* (mediante un `mov`, o un `lea`) y emite la correspondiente información de desenredo (reg. set_frame, desplazamiento)|
|push_eflags|Inserta eflags con un `pushfq` instrucciones y emite adecuado (. alloc_stack 8) de la información de desenredo|

Este es un ejemplo de prólogo de función con el uso correcto de las macros:

```MASM
SkFrame struct
    Fill    dq ?; fill to 8 mod 16
    SavedRdi dq ?; saved register RDI
    SavedRsi dq ?; saved register RSI
SkFrame ends

sampleFrame struct
    Filldq?; fill to 8 mod 16
    SavedRdidq?; Saved Register RDI
    SavedRsi  dq?; Saved Register RSI
sampleFrame ends

sample2 PROC FRAME
    alloc_stack(sizeof sampleFrame)
    save_reg rdi, sampleFrame.SavedRdi
    save_reg rsi, sampleFrame.SavedRsi
    .end_prolog

; function body

    mov rsi, sampleFrame.SavedRsi[rsp]
    mov rdi, sampleFrame.SavedRdi[rsp]

; Here’s the official epilog

    add rsp, (sizeof sampleFrame)
    ret
sample2 ENDP
```

## <a name="unwind-data-definitions-in-c"></a>Datos definiciones de desenredo en C

Esta es una descripción de los datos de desenredo en C:

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

[x64 convenciones de software](../build/x64-software-conventions.md)