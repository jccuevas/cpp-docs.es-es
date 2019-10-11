---
title: Control de excepciones de ARM64
ms.date: 11/19/2018
ms.openlocfilehash: b4f9a5d6f86f8b88ef42525e6a9bb1b4071585ce
ms.sourcegitcommit: a9f1a1ba078c2b8c66c3d285accad8e57dc4539a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/08/2019
ms.locfileid: "72037738"
---
# <a name="arm64-exception-handling"></a>Control de excepciones de ARM64

Windows en ARM64 usa el mismo mecanismo de control de excepciones estructurado para las excepciones asincrónicas generadas por hardware y las excepciones generadas por software sincrónicas. Los controladores de excepciones específicos de lenguaje se basan en el control de excepciones estructurado de Windows por medio de funciones del asistente de lenguaje. En este documento se describe el control de excepciones en Windows en ARM64 y las aplicaciones auxiliares de lenguaje que usa el código generado por el ensamblador de ARM de Microsoft y el compilador de MSVC.

## <a name="goals-and-motivation"></a>Metas y motivación

Las convenciones de datos de desenredo de excepciones y esta descripción están pensadas para:

1. Proporcione una descripción suficiente para permitir el desenredo sin sondeos de código en todos los casos.

   - El análisis del código requiere que el código esté paginado en. Esto evita el desenredo en algunas circunstancias en las que es útil (seguimiento, muestreo y depuración).

   - Analizar el código es complejo. el compilador debe tener cuidado de generar solo instrucciones que el desenredo sea capaz de descodificar.

   - Si no se puede describir completamente el desenredado mediante el uso de códigos de desenredado, en algunos casos debe revertir a la descodificación de instrucciones. Esto aumenta la complejidad general y, idealmente, se evitaría.

1. Admitir el desenredado en el prólogo intermedio y el epílogo medio.

   - El desenredado se utiliza en Windows para más que el control de excepciones, por lo que es fundamental poder realizar un desenredado preciso incluso en medio de una secuencia de código de prólogo o epílogo.

1. Ocupe una cantidad mínima de espacio.

   - Los códigos de desenredado no deben agregarse para aumentar significativamente el tamaño binario.

   - Dado que es probable que los códigos de desenredado estén bloqueados en memoria, una pequeña superficie garantiza una sobrecarga mínima para cada binario cargado.

## <a name="assumptions"></a>Suposiciones

Estas son las suposiciones realizadas en la descripción del control de excepciones:

1. Los registros y los trabajos de registro tienden a reflejarse en otro. Al aprovechar este rasgo común, se puede reducir considerablemente el tamaño de los metadatos necesarios para describir el desenredado. En el cuerpo de la función, no importa si se deshacen las operaciones del prólogo o si las operaciones del epílogo se realizan de manera anticipada. Ambas deberían generar idénticos resultados.

1. Las funciones tienden a que todo sea relativamente pequeño. Varias optimizaciones del espacio dependen de esto para lograr el empaquetado más eficaz de los datos.

1. No hay código condicional en los registros.

1. Registro de puntero de marco dedicado: Si el SP se guarda en otro registro (X29) en el prólogo, ese registro permanece intacto a lo largo de la función, de modo que el SP original se puede recuperar en cualquier momento.

1. A menos que el SP se guarde en otro registro, toda la manipulación del puntero de pila se produce estrictamente dentro del prólogo y epílogo.

1. El diseño del marco de pila se organiza como se describe en la sección siguiente.

## <a name="arm64-stack-frame-layout"></a>ARM64 diseño del marco de pila

(media/arm64-exception-handling-stack-frame.png "diseño del marco de pila") de diseño del marco de ![pila]

En el caso de las funciones encadenadas con fotogramas, los pares FP y LR se pueden guardar en cualquier posición del área variable local en función de las consideraciones de optimización. El objetivo es maximizar el número de variables locales a las que se puede tener acceso mediante una sola instrucción basada en el puntero de marco (X29) o en el puntero de pila (SP). Sin embargo, para las funciones `alloca`, debe encadenarse y X29 debe apuntar a la parte inferior de la pila. Para permitir una mejor cobertura de modo de asignación de pares de registros, las áreas de guardado de registros no volátiles se colocan en la parte superior de la pila de área local. Estos son algunos ejemplos que ilustran algunas de las secuencias de prólogo más eficaces. Con el fin de mejorar la claridad y la ubicación de la memoria caché, el orden en que se almacenan los registros guardados por el destinatario en todos los registros canónicos está en el orden "en aumento". `#framesz` a continuación representa el tamaño de la pila completa (sin incluir el área alloca). `#localsz` y `#outsz` denotan el tamaño de área local (incluido el área de almacenamiento de los \<x29, LR > par) y el tamaño del parámetro saliente, respectivamente.

1. Encadenado, #localsz \< = 512

    ```asm
        stp    x19,x20,[sp,#-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,#16]            // save in FP regs (optional)
        stp    x0,x1,[sp,#32]            // home params (optional)
        stp    x2,x3,[sp,#48]
        stp    x4,x5,[sp,#64]
        stp    x6,x7,[sp,#72]
        stp    x29,lr,[sp,#-localsz]!   // save <x29,lr> at bottom of local area
        mov    x29,sp                   // x29 points to bottom of local
        sub    sp,sp,#outsz             // (optional for #outsz != 0)
    ```

1. Encadenado, #localsz > 512

    ```asm
        stp    x19,x20,[sp,#-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,#16]            // save in FP regs (optional)
        stp    x0,x1,[sp,#32]            // home params (optional)
        stp    x2,x3,[sp,#48]
        stp    x4,x5,[sp,#64]
        stp    x6,x7,[sp,#72]
        sub    sp,sp,#(localsz+outsz)   // allocate remaining frame
        stp    x29,lr,[sp,#outsz]       // save <x29,lr> at bottom of local area
        add    x29,sp,#outsz            // setup x29 points to bottom of local area
    ```

1. Funciones de hoja no encadenadas (LR sin guardar)

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]
        str    x23,[sp,#32]
        stp    d8,d9,[sp,#40]           // save FP regs (optional)
        stp    d10,d11,[sp,#56]
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   Se tiene acceso a todas las variables locales basándose en SP. \<x29, LR > apunta al fotograma anterior. Para el tamaño de marco \< = 512, el "sub SP,..." se puede optimizar si el área guardada regs se mueve a la parte inferior de la pila. El inconveniente de eso es que no es coherente con otros diseños anteriores y que los regs guardados forman parte del intervalo de pares-regs y del modo de direccionamiento de desplazamiento previo y posterior al índice.

1. Funciones no encadenadas no hoja (LR se guarda en el área guardada en int)

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]         // ...
        stp    x23,lr,[sp,#32]          // save last Int reg and lr
        stp    d8,d9,[sp,#48]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,#64]         // ...
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   O, con un número par guardado de registros int,

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]         // ...
        str    lr,[sp,#32]              // save lr
        stp    d8,d9,[sp,#40]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,#56]         // ...
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   Solo x19 guardado:

    ```asm
        sub    sp,sp,#16                // reg save area allocation*
        stp    x19,lr,[sp]              // save x19, lr
        sub    sp,sp,#(framesz-16)      // allocate the remaining local area
    ```

   \* la asignación del área de guardado del registro no se dobla en el STP porque un STP reg-LR con preíndice no se puede representar con los códigos de desenredado.

   Se tiene acceso a todas las variables locales basándose en SP. \<x29 > apunta al fotograma anterior.

1. Encadenado, #framesz \< = 512, #outsz = 0

    ```asm
        stp    x29,lr,[sp,#-framesz]!       // pre-indexed, save <x29,lr>
        mov    x29,sp                       // x29 points to bottom of stack
        stp    x19,x20,[sp,#(framesz-32)]   // save INT pair
        stp    d8,d9,[sp,#(framesz-16)]     // save FP pair
    ```

   En comparación con #1 prólogo anterior, la ventaja es que todas las instrucciones para guardar el registro están listas para ejecutarse justo después de la única instrucción de asignación de la pila. Por lo tanto, no hay ninguna dependencia en SP que impida el paralelismo de nivel de instrucción.

1. Encadenado, tamaño de marco > 512 (opcional para funciones sin alloca)

    ```asm
        stp    x29,lr,[sp,#-80]!            // pre-indexed, save <x29,lr>
        stp    x19,x20,[sp,#16]             // save in INT regs
        stp    x21,x22,[sp,#32]             // ...
        stp    d8,d9,[sp,#48]               // save in FP regs
        stp    d10,d11,[sp,#64]
        mov    x29,sp                       // x29 points to top of local area
        sub    sp,sp,#(framesz-80)          // allocate the remaining local area
    ```

   Para fines de optimización, X29 se puede colocar en cualquier posición en el área local para proporcionar una mejor cobertura para el modo de direccionamiento del desplazamiento anterior y/post-indexed. Se puede tener acceso a las variables locales por debajo de los punteros de marco según el SP.

1. Encadenado, tamaño de marco > 4K, con o sin alloca (),

    ```asm
        stp    x29,lr,[sp,#-80]!            // pre-indexed, save <x29,lr>
        stp    x19,x20,[sp,#16]             // save in INT regs
        stp    x21,x22,[sp,#32]             // ...
        stp    d8,d9,[sp,#48]               // save in FP regs
        stp    d10,d11,[sp,#64]
        mov    x29,sp                       // x29 points to top of local area
        mov    x15,#(framesz/16)
        bl     __chkstk
        sub    sp,sp,x15,lsl#4              // allocate remaining frame
                                            // end of prolog
        ...
        sub    sp,sp,#alloca                // more alloca() in body
        ...
                                            // beginning of epilog
        mov    sp,x29                       // sp points to top of local area
        ldp    d10,d11,[sp,#64]
        ...
        ldp    x29,lr,[sp],#80              // post-indexed, reload <x29,lr>
    ```

## <a name="arm64-exception-handling-information"></a>ARM64 información de control de excepciones

### <a name="pdata-records"></a>registros. pdata

Los registros. pdata son una matriz ordenada de elementos de longitud fija que describen cada función de manipulación de pila en un binario de PE. Nota detenidamente la frase "manipulación de pila": las funciones de hoja que no requieren almacenamiento local y que no necesitan guardar o restaurar registros no volátiles no requieren un registro. pdata; se deben omitir explícitamente para ahorrar espacio. Un desenredado de una de estas funciones puede simplemente obtener la dirección de retorno de LR para pasar al llamador.

Cada registro. pdata para ARM64 tiene una longitud de 8 bytes. El formato general de cada registro coloca la RVA de 32 bits de la función Start en la primera palabra, seguida de un segundo con que contiene un puntero a un bloque de longitud variable. xdata o una palabra empaquetada que describe una secuencia de desenredado de funciones canónicas.

diseño del ![registro. pdata](media/arm64-exception-handling-pdata-record.png ".")

Los campos son los siguientes:

- La **función de inicio RVA** es la rva de 32 bits del inicio de la función.

- La **marca** es un campo de 2 bits que indica cómo interpretar los 30 bits restantes de la segunda palabra. pdata. Si la **marca** es 0, los bits restantes forman una **RVA de información de excepción** (con los dos bits inferiores implícitamente 0). Si el **marcador** es distinto de cero, los bits restantes forman una estructura de **datos de desenredo empaquetada** .

- La **información de excepción RVA** es la dirección de la estructura de información de excepciones de longitud variable, que se almacena en la sección. xdata. Estos datos deben tener una alineación de 4 bytes.

- Los **datos de desenredado empaquetados** son una descripción comprimida de las operaciones necesarias para desenredar de una función, suponiendo una forma canónica. En este caso, no se necesita un registro .xdata.

### <a name="xdata-records"></a>registros. xdata

Cuando el formato de desenredado empaquetado no basta para describir el desenredado de una función, se debe crear un registro .xdata de longitud variable. La dirección de este registro se almacena en la segunda palabra del registro .pdata. El formato de. xdata es un conjunto de palabras de longitud variable empaquetada:

diseño del ![registro. xdata](media/arm64-exception-handling-xdata-record.png ". diseño del registro XData")

Estos datos se dividen en cuatro secciones:

1. Un encabezado de 1 o 2 palabras que describe el tamaño total de la estructura y proporciona datos de funciones clave. La segunda palabra solo está presente si los campos **número de epílogo** y **palabras de código** están establecidos en 0. Estos son los campos de bits del encabezado:

   a. La longitud de la **función** es un campo de 18 bits que indica la longitud total de la función en bytes, dividida entre 4. Si una función es mayor que 1M, se deben usar varios registros pdata y Xdata para describir la función. Vea la sección [funciones grandes](#large-functions) para obtener más detalles.

   b. **Versa** es un campo de 2 bits que describe la versión de XData restante. En el que se redactó este documento, solo se define la versión 0 y, por lo tanto, no se permiten los valores 1-3.

   c. **X** es un campo de 1 bit que indica la presencia (1) o la ausencia (0) de los datos de la excepción.

   d. **E** es un campo de bits que indica que la información que describe un solo epílogo se empaqueta en el encabezado (1) en lugar de requerir más palabras de ámbito más adelante (0).

   e. El **número de epílogos** es un campo de 5 bits que tiene dos significados, dependiendo del estado de **E** bit:

      1. Si **E** se establece en 0: especifica el recuento del número total de ámbitos de epílogo descritos en la sección 2. Si existen más de 31 ámbitos en la función, el campo **palabras de código** debe establecerse en 0 para indicar que se requiere una palabra de extensión.

      2. Si **E** está establecido en 1, este campo especifica el índice del primer código de desenredado que describe el epílogo solo.

   f. **Palabras de código** es un campo de 5 bits que especifica el número de palabras de 32 bits necesarias para contener todos los códigos de desenredado de la sección 3. Si se requieren más de 31 palabras (es decir, más de 124 bytes de código de desenredado), este campo debe establecerse en 0 para indicar que se necesita una palabra de extensión.

   g. El **número de epílogos extendidos** y las **palabras de código extendido** son campos de 16 y 8 bits, respectivamente, que proporcionan más espacio para codificar un número inusualmente grande de registros o un número inusualmente grande de palabras de código de desenredado. La palabra de extensión que contiene estos campos solo está presente si los campos **número de epílogo** y **palabras de código** de la primera palabra del encabezado están establecidos en 0.

1. Después del encabezado y del encabezado extendido opcional descrito anteriormente, si el **recuento de epílogo** no es cero, es una lista de información sobre los ámbitos de epílogo, empaquetada una en una palabra y almacenada en orden de desplazamiento inicial de aumento. Cada ámbito contiene los bits siguientes:

   a. El **desplazamiento de inicio de epílogo** es un campo de 18 bits que describe el desplazamiento en bytes, dividido entre 4, del epílogo con respecto al inicio de la función.

   b. **Res** es un campo de 4 bits que se reserva para una futura expansión. Su valor debe ser 0.

   c. El **Índice de inicio de epílogo** es un campo de 10 bits (2 más bits que las palabras de **código extendido**) que indica el índice de bytes del primer código de desenredado que describe este epílogo.

1. Una vez que la lista de ámbitos de epílogo incluye una matriz de bytes que contienen códigos de desenredado, se describe detalladamente en una sección posterior. Esta matriz se rellena al final del límite de palabra completa más cercano. Los códigos de desenredado se escriben en esta matriz, empezando por el más cercano al cuerpo de la función, desplazándose hacia los bordes de la función. Los bytes de cada código de desenredado se almacenan en orden big-endian, de modo que se pueden capturar directamente, empezando por el byte más significativo en primer lugar, que identifica la operación y la longitud del resto del código.

1. Por último, después de los bytes de código de desenredado, si el bit **X** del encabezado se estableció en 1, incluye la información del controlador de excepciones. Se compone de una única **RVA del controlador de excepciones** que proporciona la dirección del propio controlador de excepciones, seguido inmediatamente de una cantidad de datos de longitud variable requerida por el controlador de excepciones.

El registro. xdata anterior está diseñado de forma que es posible capturar los primeros 8 bytes y de que calcula el tamaño completo del registro (menos la longitud de los datos de excepción de tamaño variable que se indican a continuación). El siguiente fragmento de código calcula el tamaño del registro:

```cpp
ULONG ComputeXdataSize(PULONG *Xdata)
{
    ULONG EpilogScopes;
    ULONG Size;
    ULONG UnwindWords;

    if ((Xdata[0] >> 27) != 0) {
        Size = 4;
        EpilogScopes = (Xdata[0] >> 22) & 0x1f;
        UnwindWords = (Xdata[0] >> 27) & 0x0f;
    } else {
        Size = 8;
        EpilogScopes = Xdata[1] & 0xffff;
        UnwindWords = (Xdata[1] >> 16) & 0xff;
    }

    Size += 4 * EpilogScopes;
    Size += 4 * UnwindWords;
    if (Xdata[0] & (1 << 20)) {
        Size += 4;        // exception handler RVA
    }
    return Size;
}
```

Se debe tener en cuenta que, aunque el prólogo y cada epílogo tienen su propio índice en los códigos de desenredado, la tabla se comparte entre ellos y es completamente posible (y no es totalmente infrecuente) que todos pueden compartir los mismos códigos (vea el ejemplo 2 en la sección de ejemplos Bel permitir). Los escritores de compiladores deben optimizar en este caso, en concreto porque el índice más grande que se puede especificar es 255, lo que limita el número total de códigos de desenredado para una función determinada.

### <a name="unwind-codes"></a>Códigos de desenredado

La matriz de códigos de desenredado es un grupo de secuencias que describen exactamente cómo deshacer los efectos del prólogo, en el orden en que se deben deshacer las operaciones. Los códigos de desenredado se pueden considerar como un conjunto de instrucciones mini, codificado como una cadena de bytes. Una vez completada la ejecución, la dirección de devolución a la función de llamada se encuentra en el registro de LR y todos los registros no volátiles se restauran a sus valores en el momento en que se llamó a la función.

Si se garantiza que las excepciones solo se producen dentro del cuerpo de una función (y nunca con un prólogo o un epílogo), solo sería necesaria una única secuencia. Sin embargo, el modelo de desenredado de Windows requiere que se pueda desenredar dentro de un prólogo o epílogo parcialmente ejecutado. Para dar cabida a este requisito, los códigos de desenredado se han diseñado cuidadosamente de modo que se asignen de forma inequívoca 1:1 a cada código de operación pertinente del prólogo y epílogo. Esto implica lo siguiente:

1. Al contar el número de códigos de desenredado, es posible calcular la longitud del prólogo y el epílogo.

1. Al contar el número de instrucciones más allá del inicio de un ámbito de epílogo, es posible omitir el número equivalente de códigos de desenredado y ejecutar el resto de una secuencia para completar el desenredado parcialmente ejecutado que el epílogo estaba realizando.

1. Al contar el número de instrucciones antes del final del prólogo, es posible omitir el número equivalente de códigos de desenredado y ejecutar el resto de la secuencia para deshacer solo las partes del prólogo que hayan finalizado su ejecución.

Los códigos de desenredado se codifican según la tabla siguiente. Todos los códigos de desenredado son un byte único o doble, excepto el que asigna una pila grande. Por completo, hay 21 código de desenredado. Cada código de desenredado asigna exactamente una instrucción en el prólogo/epílogo para permitir el desenredado de los registros y epílogos parcialmente ejecutados.

|Código de desenredado|Bits e interpretación|
|-|-|
|`alloc_s`|000xxxxx: asigna una pila pequeña con el tamaño \< 512 (2 ^ 5 * 16).|
|`save_r19r20_x`|    001zzzzz: Save \<x19, x20 > Pair at [SP-#Z * 8]!, desplazamiento previamente indexado > =-248 |
|`save_fplr`|        01zzzzzz: Save \<x29, LR > par en [SP + #Z * 8], offset \< = 504. |
|`save_fplr_x`|        10zzzzzz: Save \<x29, LR > Pair at [SP-(#Z + 1) * 8]!, desplazamiento preindexado > =-512 |
|`alloc_m`|        11000xxx'xxxxxxxx: asigne una pila grande con el tamaño \< 16k (2 ^ 11 * 16). |
|`save_regp`|        110010xx'xxzzzzzz: Save x (19 + #X) Pair at [SP + #Z * 8], offset \< = 504 |
|`save_regp_x`|        110011xx'xxzzzzzz: Save Pair x (19 + #X) at [SP-(#Z + 1) * 8]!, desplazamiento previamente indexado > =-512 |
|`save_reg`|        110100xx'xxzzzzzz: Save reg x (19 + #X) at [SP + #Z * 8], offset \< = 504 |
|`save_reg_x`|        1101010x'xxxzzzzz: Ahorre reg x (19 + #X) en [SP-(#Z + 1) * 8]!, desplazamiento previamente indexado > =-256 |
|`save_lrpair`|         1101011x'xxzzzzzz: Save Pair \<x (19 + 2 *#X), lr > en [SP + #Z*8], offset \< = 504 |
|`save_fregp`|        1101100x'xxzzzzzz: Save Pair d (8 + #X) at [SP + #Z * 8], offset \< = 504 |
|`save_fregp_x`|        1101101x'xxzzzzzz: Save Pair d (8 + #X), at [SP-(#Z + 1) * 8]!, desplazamiento previamente indexado > =-512 |
|`save_freg`|        1101110x'xxzzzzzz: Save reg d (8 + #X) en [SP + #Z * 8], offset \< = 504 |
|`save_freg_x`|        11011110 ' xxxzzzzz: Save reg d (8 + #X) at [SP-(#Z + 1) * 8]!, desplazamiento previamente indexado > =-256 |
|`alloc_l`|         11100000 ' xxxxxxxx'xxxxxxxx'xxxxxxxx: asignar una pila grande con el tamaño \< 256M (2 ^ 24 * 16) |
|`set_fp`|        11100001: configurar X29: con: MOV X29, SP |
|`add_fp`|        11100010 ' xxxxxxxx: configure X29 con: Add X29, SP, #x * 8 |
|`nop`|            11100011: no se requiere ninguna operación de desenredado. |
|`end`|            11100100: fin del código de desenredado. Implica RET en Epílogo. |
|`end_c`|        11100101: fin del código de desenredado en el ámbito actual encadenado. |
|`save_next`|        11100110: Guarde el siguiente par de registros int o FP no volátiles. |
|`arithmetic(add)`|    11100111 ' 000zxxxx: Add cookie reg (z) to LR (0 = x28, 1 = SP); Agregar LR, LR, REG (z) |
|`arithmetic(sub)`|    11100111 ' 001zxxxx: sub cookie reg (z) from LR (0 = x28, 1 = SP); Sub LR, LR, REG (z) |
|`arithmetic(eor)`|    11100111 ' 010zxxxx: EOR LR con cookie reg (z) (0 = x28, 1 = SP); EOR LR, LR, REG (z) |
|`arithmetic(rol)`|    11100111 ' 0110xxxx: rol de la simulación de LR con el registro de cookies (x28); xip0 = NEG x28; ROR LR, xip0 |
|`arithmetic(ror)`|    11100111 ' 100zxxxx: RoR LR con cookie reg (z) (0 = x28, 1 = SP); ROR LR, LR, REG (z) |
| |            11100111: Xxxz----:----reservado |
| |              11101xxx: reservado para los casos de pila personalizados que se muestran a continuación solo se genera para las rutinas ASM |
| |              11101000: Pila personalizada para MSFT_OP_TRAP_FRAME |
| |              11101001: Pila personalizada para MSFT_OP_MACHINE_FRAME |
| |              11101010: Pila personalizada para MSFT_OP_CONTEXT |
| |              11101100: Pila personalizada para MSFT_OP_CLEAR_UNWOUND_TO_CALL |
| |              1111xxxx: reservado |

En las instrucciones con valores grandes que abarcan varios bytes, se almacenan primero los bits más significativos. Los códigos de desenredado anteriores están diseñados de forma que, con solo buscar el primer byte del código, es posible conocer el tamaño total en bytes del código de desenredado. Dado que cada código de desenredado se asigna exactamente a una instrucción de prólogo/epílogo, para calcular el tamaño del prólogo o epílogo, todo lo que se debe hacer es recorrer el inicio de la secuencia hasta el final, utilizando una tabla de búsqueda o un dispositivo similar para determinar cuánto tiempo el Cor el código de operación de respuesta es.

Tenga en cuenta que no se permite el direccionamiento posterior del desplazamiento indizado en el prólogo. Todos los intervalos de desplazamiento (#Z) coinciden con la codificación del direccionamiento de STP/STR, excepto `save_r19r20_x`, en el que 248 es suficiente para todas las áreas de almacenamiento (10 registros int + 8 registros FP + 8 registros de entrada).

`save_next` debe seguir a un par de registro volatile de tipo int o FP: `save_regp`, @no__t 2, `save_fregp`, `save_fregp_x`, `save_r19r20_x` u otro `save_next`. Guarda el siguiente par de registros en la siguiente ranura de 16 bytes en el orden "en aumento". `save-next` después de un `save_next` que denota el último par de registro int hace referencia al primer par de registro de FP.

Dado que el tamaño de las instrucciones de devolución y salto normales es el mismo, no es necesario un código de desenredado `end` separado para escenarios de llamada de cola.

`end_c` está diseñado para controlar los fragmentos de función no contiguos con fines de optimización. Un `end_c` que indica que el final de los códigos de desenredado en el ámbito actual debe ir seguido de otra serie de código de desenredado finalizada con un @no__t real-1. Los códigos de desenredado entre `end_c` y `end` representan las operaciones de prólogo en la región primaria (prólogo "fantasma").  En la sección siguiente se describen más detalles y ejemplos.

### <a name="packed-unwind-data"></a>Datos de desenredo empaquetados

En el caso de las funciones cuyos registros y archivos de registro siguen el formato canónico descrito a continuación, se pueden usar datos de desenredado empaquetados, lo que elimina la necesidad de un registro. xdata por completo y reduce significativamente el costo de proporcionar datos de desenredado. Los registros y los errores canónicos están diseñados para satisfacer los requisitos comunes de una función simple que no requiere un controlador de excepciones y que realiza las operaciones de instalación y desmontaje en un orden estándar.

El formato de un registro. pdata con datos de desenredado empaquetados tiene el siguiente aspecto:

![registro. pdata con registro de datos de desenredado](media/arm64-exception-handling-packed-unwind-data.png ". pdata empaquetado con datos de desenredado empaquetados")

Los campos son los siguientes:

- La **función de inicio RVA** es la rva de 32 bits del inicio de la función.
- La **marca** es un campo de 2 bits como se describió anteriormente, con los significados siguientes:
  - 00 = no se usan datos de desenredado empaquetados; los bits restantes apuntan a un registro. xdata
  - 01 = datos de desenredado empaquetados usados como se describe a continuación con un prólogo y un epílogo únicos al principio y al final del ámbito
  - 10 = datos de desenredado empaquetados usados como se describe a continuación para el código sin prólogo y epílogo; Esto resulta útil para describir segmentos de funciones independientes.
  - 11 = reservado;
- La longitud de la **función** es un campo de 11 bits que proporciona la longitud de la función completa en bytes, dividida entre 4. Si la función es mayor que 8 k, se debe usar en su lugar un registro. xdata completo.
- El **tamaño del marco** es un campo de 9 bits que indica el número de bytes de la pila que se asigna a esta función, dividido por 16. Las funciones que asignan más de (8k-16) bytes de stack deben usar un registro. xdata completo. Esto incluye el área de variables locales, el área de parámetros de salida, el área de int y FP guardados por el destinatario y el área de parámetros de inicio, pero excluye el área de asignación dinámica.
- **CR** es una marca de 2 bits que indica si la función incluye instrucciones adicionales para configurar una cadena de Marcos y devolver el vínculo:
  - 00 = función no encadenada, \<x29, el par de > LR no se guarda en la pila.
  - 01 = función encadenada, @no__t 0lr > se guarda en la pila
  - 10 = reservado;
  - 11 = función encadenada, se usa una instrucción de par de carga/almacenamiento en el prólogo/epílogo \<x29, LR >
- **H** es una marca de 1 bit que indica si la función aloja los registros de parámetros de entero (x0-7) almacenándolos en el inicio de la función. (0 = no se registra, 1 = casas registros).
- **RegI** es un campo de 4 bits que indica el número de registros int no volátiles (x19-x28) guardados en la ubicación de pila canónica.
- **RegF** es un campo de 3 bits que indica el número de registros FP no volátiles (D8-D15) guardados en la ubicación de pila canónica. (RegF = 0: no se guarda ningún registro FP; RegF > 0: Se guardan los registros RegF + 1 FP). Los datos de desenredado empaquetados no se pueden usar para una función que solo guarde un registro FP.

Los proregistros canónicos que se encuentran en las categorías 1, 2 (sin área de parámetros de salida), 3 y 4 en la sección anterior se pueden representar con el formato de desenredado empaquetado.  Los registros de las funciones canónicas siguen una forma muy similar, salvo que **H** no tiene ningún efecto, se omite la instrucción `set_fp` y el orden de los pasos, así como las instrucciones de cada paso, se invierten en Epílogo. El algoritmo para XData empaquetado sigue estos pasos, que se detallan en la tabla siguiente:

Paso 0: Realice el cálculo previo del tamaño de cada área.

Paso 1: Guardar registros guardados por el destinatario.

Paso 2: Este paso es específico para el tipo 4 en las primeras secciones. LR se guarda al final del área int.

Paso 3: Guardar registros guardados de la llamada de FP.

Paso 4: Guardar argumentos de entrada en el área de parámetros de inicio.

Paso 5: Asigne la pila restante, incluidos el área local, \<x29, el par de > LR y el área de parámetros de salida. 5A corresponde al tipo canónico 1. 5B y 5C son para el tipo canónico 2. 5D y 5e son tanto para el tipo 3 como para el tipo 4.

Pasar #|Valores de marca|n.º de instrucciones|Código de operación|Código de desenredado
-|-|-|-|-
0|||`#intsz = RegI * 8;`<br/>`if (CR==01) #intsz += 8; // lr`<br/>`#fpsz = RegF * 8;`<br/>`if(RegF) #fpsz += 8;`<br/>`#savsz=((#intsz+#fpsz+8*8*H)+0xf)&~0xf)`<br/>`#locsz = #famsz - #savsz`|
1|0 < **RegI** < = 10|RegI/2 + **RegI** % 2|`stp x19,x20,[sp,#savsz]!`<br/>`stp x21,x22,[sp,#16]`<br/>`...`|`save_regp_x`<br/>`save_regp`<br/>`...`
2|**CR**= = 01 *|1|`str lr,[sp,#(intsz-8)]`\*|`save_reg`
3|0 < **RegF** < = 7|(RegF + 1)/2 +<br/>(RegF + 1)% 2)|`stp d8,d9,[sp,#intsz]`\*\*<br/>`stp d10,d11,[sp,#(intsz+16)]`<br/>`...`<br/>`str d(8+RegF),[sp,#(intsz+fpsz-8)]`|`save_fregp`<br/>`...`<br/>`save_freg`
4|**H** == 1|4|`stp x0,x1,[sp,#(intsz+fpsz)]`<br/>`stp x2,x3,[sp,#(intsz+fpsz+16)]`<br/>`stp x4,x5,[sp,#(intsz+fpsz+32)]`<br/>`stp x6,x7,[sp,#(intsz+fpsz+48)]`|`nop`<br/>`nop`<br/>`nop`<br/>`nop`
5a|**CR** = = 11 & & #locsz<br/> <= 512|2|`stp x29,lr,[sp,#-locsz]!`<br/>`mov x29,sp`\*\*\*|`save_fplr_x`<br/>`set_fp`
5b|**CR** = = 11 & &<br/>512 < #locsz <= 4080|3|`sub sp,sp,#locsz`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5c|**CR** = = 11 & & #locsz > 4080|4|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`alloc_s`/`alloc_m`<br/>`save_fplr`<br/>`set_fp`
15D|(**CR** = = 00 \| @ NO__T-2 **CR**= = 01) & &<br/>#locsz < = 4080|1|`sub sp,sp,#locsz`|`alloc_s`/`alloc_m`
5e|(**CR** = = 00 \| @ NO__T-2 **CR**= = 01) & &<br/>#locsz > 4080|2|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`|`alloc_m`<br/>`alloc_s`/`alloc_m`

\* si **CR** = = 01 y **RegI** es un número impar, el paso 2 y el último save_rep del paso 1 se combinan en un save_regp.

\* @ no__t-1 si **RegI** == **CR** = = 0 y **RegF** ! = 0, el primer STP del punto flotante realiza el predecremento.

\* @ no__t-1 @ no__t-2 ninguna instrucción correspondiente a `mov x29,sp` está presente en el epílogo. No se pueden usar datos de desenredado empaquetados si una función requiere la restauración de SP desde X29.

### <a name="unwinding-partial-prologs-and-epilogs"></a>Desenredado de los archivos de registro y de los registros parciales

La situación de desenredo más común es aquella en la que se produjo la excepción o la llamada en el cuerpo de la función, fuera del prólogo y de todos los registros. En esta situación, el desenredado es sencillo: el desenredo simplemente comienza a ejecutar los códigos de la matriz de desenredado, empezando en el índice 0 y continuando hasta que se detecta un código de operación final.

Es más difícil desenredar correctamente en caso de que se produzca una excepción o una interrupción mientras se ejecuta un prólogo o un epílogo. En estas situaciones, el marco de pila solo se construye parcialmente y el truco es determinar exactamente lo que se ha hecho para deshacerlo correctamente.

Por ejemplo, realice esta secuencia de prólogo y epílogo:

```asm
0000:    stp    x29,lr,[sp,#-256]!          // save_fplr_x  256 (pre-indexed store)
0004:    stp    d8,d9,[sp,#224]             // save_fregp 0, 224
0008:    stp    x19,x20,[sp,#240]           // save_regp 0, 240
000c:    mov    x29,sp                      // set_fp
         ...
0100:    mov    sp,x29                      // set_fp
0104:    ldp    x19,x20,[sp,#240]           // save_regp 0, 240
0108:    ldp    d8,d9,[sp,224]              // save_fregp 0, 224
010c:    ldp    x29,lr,[sp],#256            // save_fplr_x  256 (post-indexed load)
0110:    ret    lr                          // end
```

Junto a cada código de operación se encuentra el código de desenredado adecuado que describe esta operación. Lo primero que hay que tener en cuenta es que la serie de códigos de desenredado del prólogo es una imagen reflejada exacta de los códigos de desenredado para el epílogo (sin contar la instrucción final del epílogo). Se trata de una situación común y, por este motivo, siempre se supone que los códigos de desenredado del prólogo se almacenan en orden inverso al orden de ejecución del prólogo.

Por lo tanto, para el prólogo y el epílogo, se deja un conjunto común de códigos de desenredado:

`set_fp`, `save_regp 0,240`, `save_fregp,0,224`, `save_fplr_x_256`, `end`

A partir del caso de epílogo (más sencillo como está en orden normal), en el desplazamiento 0 dentro del epílogo (que comienza en el desplazamiento 0x100 en la función), se esperaría ejecutar la secuencia de desenredado completa, ya que aún no se ha realizado ninguna limpieza. Si nos encontramos en una instrucción en (en el desplazamiento 2 del epílogo), podemos desenredar correctamente omitiendo el primer código de desenredado. Al generalizar esta situación, suponiendo una asignación 1:1 entre códigos de error y desenredado, podemos indicar que si estamos desenredando de la instrucción n en el epílogo, deberíamos omitir los primeros n códigos de desenredado y comenzar a ejecutar desde allí.

Resulta que funciona una lógica similar para el prólogo, excepto en orden inverso. Si estamos desenredando del desplazamiento 0 en el prólogo, deberíamos que no ejecute nada. Si desenredamos del desplazamiento 2, que es una instrucción de, deseamos empezar a ejecutar la secuencia de desenredado un código de desenredado desde el final (Recuerde que los códigos se almacenan en orden inverso). Y aquí también podremos generalizar que si estamos desenredando de la instrucción n en el prólogo, debemos empezar a ejecutar n códigos de desenredado desde el final de la lista de códigos.

Ahora no siempre es el caso de que los códigos de prólogo y epílogo coincidan exactamente. Por esta razón, la matriz de desenredado puede necesitar contener varias secuencias de códigos. Para determinar el desplazamiento por el que comienza el procesamiento de códigos, utilice la siguiente lógica:

1. Si desea desenredar desde dentro del cuerpo de la función, simplemente comience a ejecutar códigos de desenredado en el índice 0 y continúe hasta llegar a un código de operación de "fin".

1. Si el desenredado se encuentra dentro de un epílogo, use el índice de inicio específico del epílogo proporcionado con el ámbito del epílogo como punto de partida. Calcule el número de bytes que el equipo en cuestión proviene del inicio del epílogo. A continuación, avance a través de los códigos de desenredado, omitiendo los códigos de desenredado hasta que se tengan en cuenta todas las instrucciones que ya se han ejecutado. A continuación, ejecute a partir de ese punto.

1. Si el desenredado se encuentra dentro del prólogo, use el índice 0 como punto de partida. Calcule la longitud del código de prólogo a partir de la secuencia y, a continuación, calcule el número de bytes del equipo en cuestión desde el final del prólogo. A continuación, avance por los códigos de desenredado, omitiendo los códigos de desenredado hasta que se tengan en cuenta todas las instrucciones no ejecutadas todavía. A continuación, ejecute a partir de ese punto.

Como resultado de estas reglas, los códigos de desenredado del prólogo deben ser siempre el primero de la matriz, y también son los códigos usados para desenredar en el caso general de desenredado desde dentro del cuerpo. Las secuencias de código específicas de epílogo deben seguir inmediatamente después de.

### <a name="function-fragments"></a>Fragmentos de función

Para fines de optimización de código y otras razones, puede ser preferible dividir una función en fragmentos separados (también denominados regiones). Cuando esto se hace, cada fragmento de función resultante requiere su propio registro. pdata (y posiblemente. xdata) independiente.

En el caso del fragmento secundario separado que tiene su propio prólogo, se espera que no se realice ningún ajuste de la pila en su prólogo. Todo el espacio de pila requerido por las regiones secundarias debe estar asignado previamente por su región primaria (o como región del host). Esto mantiene la manipulación del puntero de pila estrictamente en el prólogo original de la función.

Un caso típico de fragmentos de función es "separación de código" con ese compilador puede desasociar una región de código de su función de host. Hay tres casos inusuales que pueden ser resultado de la separación de código.

#### <a name="example"></a>Ejemplo:

- (región 1: Begin)

    ```asm
        stp     x29,lr,[sp,#-256]!      // save_fplr_x  256 (pre-indexed store)
        stp     x19,x20,[sp,#240]       // save_regp 0, 240
        mov     x29,sp                  // set_fp
        ...
    ```

- (región 1: fin)
- (región 3: Begin)

    ```asm
        ...
    ```

- (región 3: fin)
- (región 2: Begin)

    ```asm
    ...
        mov     sp,x29                  // set_fp
        ldp     x19,x20,[sp,#240]       // save_regp 0, 240
        ldp     x29,lr,[sp],#256        // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (región 2: fin)

1. Solo prólogo (región 1: todos los registros se encuentran en regiones independientes):

   Solo debe describirse el prólogo. No se puede representar con el formato compacto. pdata. En el caso de Full. xdata, esto se puede representar estableciendo el número de epílogo = 0. Vea la región 1 en el ejemplo anterior.

   Códigos de desenredado: `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`.

1. Solo registros (región 2: el prólogo está en la región del host)

   Se supone que, al saltar a esta región el control de tiempo, se han ejecutado todos los códigos de prólogo. El desenredo parcial puede producirse en los registros de la misma manera que en una función normal. Este tipo de región no se puede representar mediante Compact. pdata. En el registro XData completo, se puede codificar con un prólogo "fantasma", entre corchetes por un par de código de desenredo `end_c` y `end`.  El @no__t inicial-0 indica que el tamaño del prólogo es cero. El índice de inicio del epílogo de la única señal apunta a `set_fp`.

   Código de desenredo para la región 2: `end_c`, `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`.

1. Ningún registro o EPI(región 3: los proregistros y todos los archivos de registro están en otros fragmentos):

   El formato Compact. pdata se puede aplicar a través de la marca de configuración = 10. Con el registro Full. xdata, el número de epílogos es 1. El código de desenredado es el mismo que el de la región 2 anterior, pero el índice de inicio de epílogo también señala a `end_c`. El desenredo parcial nunca se producirá en esta región de código.

Otro caso más complicado de fragmentos de función es "ajuste de reducción" con ese compilador puede optar por retrasar el guardado de algunos registros guardados por el destinatario hasta fuera del prólogo de entrada de función.

- (región 1: Begin)

    ```asm
        stp     x29,lr,[sp,#-256]!      // save_fplr_x  256 (pre-indexed store)
        stp     x19,x20,[sp,#240]       // save_regp 0, 240
        mov     x29,sp                  // set_fp
        ...
    ```

- (región 2: Begin)

    ```asm
        stp     x21,x22,[sp,#224]       // save_regp 2, 224
        ...
        ldp     x21,x22,[sp,#224]       // save_regp 2, 224
    ```

- (región 2: fin)

    ```asm
        ...
        mov     sp,x29                  // set_fp
        ldp     x19,x20,[sp,#240]       // save_regp 0, 240
        ldp     x29,lr,[sp],#256        // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (región 1: fin)

En el prólogo de la región 1, el espacio de pila está preasignado. Tenga en cuenta que la región 2 tendrá el mismo código de desenredado incluso si se sale de su función de host.

Región 1: `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end` con el índice de inicio de epílogo apunta a `set_fp` como de costumbre.

Región 2: `save_regp 2, 224`, `end_c`, @no__t 2, `save_regp 0,240`, `save_fplr_x_256`, `end`. El índice de inicio de epílogo apunta al primer código de desenredado `save_regp 2, 224`.

### <a name="large-functions"></a>Funciones grandes

Los fragmentos se pueden aprovechar para describir funciones mayores que el límite de 1M impuesto por los campos de bits del encabezado. xdata. Para describir una función muy grande de este tipo, simplemente debe dividirse en fragmentos inferiores a 1 millón. Cada fragmento debe ajustarse para que no divida un epílogo en varias partes.

Solo el primer fragmento de la función contendrá un prólogo; todos los demás fragmentos se marcan como sin prólogo. En función del número de archivos de registro presentes, cada fragmento puede contener cero o más registros. Tenga en cuenta que cada ámbito de epílogo de un fragmento especifica su desplazamiento inicial en relación al inicio del fragmento, no al inicio de la función.

Si un fragmento no tiene ningún prólogo y sin epílogo, todavía requiere su propio registro. pdata (y posiblemente. xdata) para describir cómo desenredar desde dentro del cuerpo de la función.

## <a name="examples"></a>Ejemplos

### <a name="example-1-frame-chained-compact-form"></a>Ejemplo 1: Con cadena y forma compacta

```asm
|Foo|     PROC
|$LN19|
    str     x19,[sp,#-0x10]!        // save_reg_x
    sub     sp,sp,#0x810            // alloc_m
    stp     fp,lr,[sp]              // save_fplr
    mov     fp,sp                   // set_fp
                                    //  end of prolog
    ...

|$pdata$Foo|
    DCD     imagerel     |$LN19|
    DCD     0x416101ed
    ;Flags[SingleProEpi] functionLength[492] RegF[0] RegI[1] H[0] frameChainReturn[Chained] frameSize[2080]
```

### <a name="example-2-frame-chained-full-form-with-mirror-prolog--epilog"></a>Ejemplo 2: De forma completa y encadenada con un prólogo & epílogo

```asm
|Bar|     PROC
|$LN19|
    stp     x19,x20,[sp,#-0x10]!    // save_regp_x
    stp     fp,lr,[sp,#-0x90]!      // save_fplr_x
    mov     fp,sp                   // set_fp
                                    // end of prolog
    ...
                                    // begin of epilog, a mirror sequence of Prolog
    mov     sp,fp
    ldp     fp,lr,[sp],#0x90
    ldp     x19,x20,[sp],#0x10
    ret     lr

|$pdata$Bar|
    DCD     imagerel     |$LN19|
    DCD     imagerel     |$unwind$cse2|
|$unwind$Bar|
    DCD     0x1040003d
    DCD     0x1000038
    DCD     0xe42291e1
    DCD     0xe42291e1
    ;Code Words[2], Epilog Count[1], E[0], X[0], Function Length[6660]
    ;Epilog Start Index[0], Epilog Start Offset[56]
    ;set_fp
    ;save_fplr_x
    ;save_r19r20_x
    ;end
```

Tenga en cuenta que el índice de EpilogStart [0] apunta a la misma secuencia de código de desenredado de prólogo.

### <a name="example-3-variadic-unchained-function"></a>Ejemplo 3: Variádicas función no encadenada

```asm
|Delegate| PROC
|$LN4|
    sub     sp,sp,#0x50
    stp     x19,lr,[sp]
    stp     x0,x1,[sp,#0x10]        // save incoming register to home area
    stp     x2,x3,[sp,#0x20]        // ...
    stp     x4,x5,[sp,#0x30]
    stp     x6,x7,[sp,#0x40]        // end of prolog
    ...
    ldp     x19,lr,[sp]             // beginning of epilog
    add     sp,sp,#0x50
    ret     lr

    AREA    |.pdata|, PDATA
|$pdata$Delegate|
    DCD     imagerel |$LN4|
    DCD     imagerel |$unwind$Delegate|

    AREA    |.xdata|, DATA
|$unwind$Delegate|
    DCD     0x18400012
    DCD     0x200000f
    DCD     0xe3e3e3e3
    DCD     0xe40500d6
    DCD     0xe40500d6
    ;Code Words[3], Epilog Count[1], E[0], X[0], Function Length[18]
    ;Epilog Start Index[4], Epilog Start Offset[15]
    ;nop        // nop for saving in home area
    ;nop        // ditto
    ;nop        // ditto
    ;nop        // ditto
    ;save_lrpair
    ;alloc_s
    ;end
```

Nota: El índice de EpilogStart [4] apunta al centro del código de desenredado del prólogo (reutiliza parcialmente la matriz de desenredado).

## <a name="see-also"></a>Vea también

[Información general de las convenciones de ABI de ARM64](arm64-windows-abi-conventions.md)<br/>
[Control de excepciones de ARM](arm-exception-handling.md)
