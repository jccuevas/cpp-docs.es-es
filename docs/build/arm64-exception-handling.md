---
title: Control de excepciones de ARM64
description: Describe las convenciones y los datos de control de excepciones que usa Windows en ARM64.
ms.date: 11/19/2018
ms.openlocfilehash: 2304c04c5e9be31299e30bb48771f7c9777d1cd5
ms.sourcegitcommit: b9aaaebe6e7dc5a18fe26f73cc7cf5fce09262c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504480"
---
# <a name="arm64-exception-handling"></a>Control de excepciones de ARM64

Windows en ARM64 emplea el mismo mecanismo de control de excepciones estructurado tanto en las excepciones generadas por hardware asincrónicas como en las excepciones generadas por software sincrónicas. Los controladores de excepciones específicos de lenguaje se basan en el control de excepciones estructurado de Windows por medio de funciones del asistente de lenguaje. En este documento se describe el control de excepciones en Windows en ARM64, así como los asistentes de lenguaje que usa el código generado mediante el ensamblador ARM de Microsoft y el compilador de MSVC.

## <a name="goals-and-motivation"></a>Objetivos y motivación

Las convenciones de datos de desenredado de excepciones y esta descripción están previstas para lo siguiente:

1. Proporcionar una descripción suficiente para permitir el desenredado sin sondeos de código en todos los casos.

   - Analizar el código requiere que el código esté paginado. Esto evita el desenredado en algunas circunstancias en las que es útil (seguimiento, muestreo y depuración).

   - Analizar el código es complejo. El compilador debe tener cuidado de generar solo instrucciones que el responsable del desenredado pueda descodificar.

   - Si el desenredado no se puede describir completamente mediante el uso de códigos de desenredado, en algunos casos se deberá revertir a la descodificación de instrucciones. Esto aumenta la complejidad general e, idealmente, debería evitarse.

1. Admitir el desenredado en el prólogo y el epílogo medios.

   - El desenredado se utiliza en Windows para más funciones que el control de excepciones. Es fundamental que el código se pueda desenredar con precisión incluso cuando se encuentra en medio de una secuencia de código de prólogo o epílogo.

1. Ocupar una cantidad mínima de espacio.

   - Los códigos de desenredado no deben agregarse para aumentar considerablemente el tamaño binario.

   - Dado que es probable que los códigos de desenredado estén bloqueados en memoria, una superficie pequeña garantiza una sobrecarga mínima para cada binario cargado.

## <a name="assumptions"></a>Suposiciones

Estas suposiciones se realizan en la descripción del control de excepciones:

1. Los prólogos y epílogos tienden a reflejarse entre sí. Al aprovechar esta característica común, se puede reducir considerablemente el tamaño de los metadatos necesarios para describir el desenredado. En el cuerpo de una función, no importa si las operaciones del prólogo se deshacen o si las operaciones del epílogo se llevan a cabo de forma avanzada. Ambas deberían generar idénticos resultados.

1. En general, las funciones tienden a ser relativamente pequeñas. Varias optimizaciones de espacio dependen de este hecho para lograr el empaquetado de los datos más eficaz.

1. No hay código de condición en los epílogos.

1. Registro de puntero de marco dedicado: si el SP se guarda en otro registro (x29) en el prólogo, ese registro permanece intacto a lo largo de la función. Eso significa que el SP original se puede recuperar en cualquier momento.

1. A menos que el SP se guarde en otro registro, cualquier manipulación del puntero de pila se produce estrictamente dentro del prólogo y el epílogo.

1. El diseño del marco de pila se organiza tal como se describe en la sección siguiente.

## <a name="arm64-stack-frame-layout"></a>Diseño del marco de pila de ARM64

![diseño del marco de pila](media/arm64-exception-handling-stack-frame.png "diseño del marco de pila")

En el caso de las funciones encadenadas con marcos, el par FP y LR se puede guardar en cualquier posición del área variable local, en función de las consideraciones sobre la optimización. El objetivo es maximizar el número de variables locales a las que se puede acceder mediante una sola instrucción basada en el puntero de marco (X29) o el puntero de pila (SP). Sin embargo, en el caso de las funciones de `alloca`, se debe encadenar y X29 debe apuntar a la parte inferior de la pila. Para permitir una mejor cobertura de modo de direccionamiento de pares de registros, las áreas de almacenamiento de registros no volátiles se colocan en la parte superior de la pila de área local. Estos son algunos ejemplos que ilustran algunas de las secuencias de prólogo más eficaces. Con el fin de mejorar la claridad y la ubicación de la memoria caché, el orden en que se almacenan los registros guardados por el destinatario en todos los registros canónicos es "en aumento". El elemento `#framesz` siguiente representa el tamaño de la pila completa (excepto el área alloca). `#localsz` y `#outsz` denotan el tamaño del área local (incluida el área de almacenamiento del par \<x29, lr>) y el tamaño del parámetro de salida, respectivamente.

1. Encadenadas, #localsz \<= 512

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

1. Encadenadas, #localsz > 512

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

   Se tiene acceso a todas las variables locales en función de SP. \<x29,lr> puntos al marco anterior. En el caso del tamaño de marco \<= 512, el "sub sp,..." se puede optimizar si el área guardada regs se desplaza a la parte inferior de la pila. El inconveniente es que no es coherente con otros diseños anteriores y los regs guardados forman parte del rango para el modo de direccionamiento de desplazamiento anterior y posterior al índice, y pair-regs.

1. Funciones que no son de hoja no encadenadas (LR se guarda en el área guardada Int)

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]         // ...
        stp    x23,lr,[sp,#32]          // save last Int reg and lr
        stp    d8,d9,[sp,#48]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,#64]         // ...
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   O con registros Int guardados de número par,

    ```asm
        stp    x19,x20,[sp,#-80]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    x21,x22,[sp,#16]         // ...
        str    lr,[sp,#32]              // save lr
        stp    d8,d9,[sp,#40]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,#56]         // ...
        sub    sp,sp,#(framesz-80)      // allocate the remaining local area
    ```

   Solo se guarda x19:

    ```asm
        sub    sp,sp,#16                // reg save area allocation*
        stp    x19,lr,[sp]              // save x19, lr
        sub    sp,sp,#(framesz-16)      // allocate the remaining local area
    ```

   \* La asignación del área de almacenamiento reg no se pliega en el STP porque un STP reg-lr preindexado no se puede representar con los códigos de desenredado.

   Se tiene acceso a todas las variables locales en función de SP. \<x29> puntos al marco anterior.

1. Encadenadas, #framesz \<= 512, #outsz = 0

    ```asm
        stp    x29,lr,[sp,#-framesz]!       // pre-indexed, save <x29,lr>
        mov    x29,sp                       // x29 points to bottom of stack
        stp    x19,x20,[sp,#(framesz-32)]   // save INT pair
        stp    d8,d9,[sp,#(framesz-16)]     // save FP pair
    ```

   En comparación con el primer ejemplo de prólogo anterior, la ventaja es que todas las instrucciones para guardar registros están listas para ejecutarse después de una sola instrucción de asignación de la pila. Esto significa que no hay ninguna anti-dependencia en el SP que evite el paralelismo de nivel de instrucciones.

1. Encadenadas, tamaño de marco > 512 (opcional para funciones sin alloca)

    ```asm
        stp    x29,lr,[sp,#-80]!            // pre-indexed, save <x29,lr>
        stp    x19,x20,[sp,#16]             // save in INT regs
        stp    x21,x22,[sp,#32]             // ...
        stp    d8,d9,[sp,#48]               // save in FP regs
        stp    d10,d11,[sp,#64]
        mov    x29,sp                       // x29 points to top of local area
        sub    sp,sp,#(framesz-80)          // allocate the remaining local area
    ```

   Para fines de optimización, X29 se puede colocar en cualquier posición en el área local a fin de proporcionar una mejor cobertura para el modo de direccionamiento de desplazamiento anterior y posterior al índice, y "reg-pair". Se puede acceder a los punteros de marco de las variables locales siguientes en función del SP.

1. Encadenadas, tamaño de marco > 4 KB, con o sin alloca(),

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

## <a name="arm64-exception-handling-information"></a>Información de control de excepciones de ARM64

### <a name="pdata-records"></a>Registros .pdata

Los registros .pdata consisten en una matriz ordenada de elementos de longitud fija que describen cada función de manipulación de la pila en un binario PE. La frase "manipulación de pila" es importante: funciones de hoja que no requieren ningún almacenamiento local y no necesitan guardar o restaurar registros no volátiles, no requieren un registro .pdata. Estos registros deben omitirse explícitamente para ahorrar espacio. Un desenredado de una de estas funciones puede obtener la dirección de retorno directamente desde LR para avanzar al autor de la llamada.

Cada registro .pdata para ARM64 tiene una longitud de 8 bytes. El formato general de cada registro coloca la dirección virtual relativa de 32 bits del inicio de la función en la primera palabra, seguida de una segunda palabra que contiene el puntero de un bloque .xdata de longitud variable o una palabra empaquetada que describe una secuencia de desenredado de función canónica.

![diseño del registro .pdata](media/arm64-exception-handling-pdata-record.png "diseño del registro .pdata")

Los campos son los siguientes:

- **Function Start RVA** (RVA de inicio de la función) es la RVA de 32 bits del inicio de la función.

- **Flag** (Marca) es un campo de 2 bits que indica cómo interpretar los 30 bits restantes de la segunda palabra .pdata. Si **Flag** (Marca) es 0, el resto de los bits forma una **Exception Information RVA** (RVA de información de la excepción), con los dos bits inferiores implícitamente en 0. Si **Flag** (Marca) no es cero, el resto de los bits forma una estructura de **Packed Unwind Data** (Datos de desenredado empaquetados).

- **Exception Information RVA** (RVA de información de la excepción) es la dirección de la estructura de información de excepción de longitud variable, que se almacena en la sección .xdata. Estos datos deben tener una alineación de 4 bytes.

- **Packed Unwind Data** (Datos de desenredado empaquetados) es una descripción comprimida de las operaciones necesarias para desenredar desde una función, siempre y cuando el formato sea canónico. En este caso, no se necesita un registro .xdata.

### <a name="xdata-records"></a>Registros .xdata

Cuando el formato de desenredado empaquetado no basta para describir el desenredado de una función, se debe crear un registro .xdata de longitud variable. La dirección de este registro se almacena en la segunda palabra del registro .pdata. El formato de .xdata es un conjunto de palabras empaquetado y de longitud variable:

![diseño del registro .xdata](media/arm64-exception-handling-xdata-record.png "diseño del registro .xdata")

Estos datos se dividen en cuatro secciones:

1. Un encabezado de 1 o 2 palabras que indica el tamaño general de la estructura y proporciona datos de función fundamentales. La segunda palabra solo está presente si los campos **Epilog Count** (Recuento de epílogos) y **Code Words** (Palabras de código) están establecidos en 0. El encabezado tiene estos campos de bits:

   a. **Function Length** (Longitud de la función) es un campo de 18 bits. Indica la longitud total de la función en bytes, dividida entre 4. Si una función supera los 1 MB, se deberán usar varios registros .pdata y .xdata para describirla. Para obtener más información, vea la sección [Funciones de gran tamaño](#large-functions).

   b. **Vers** es un campo de 2 bits. Describe la versión de los .xdata restantes. Actualmente, solo se define la versión 0, por lo que no se permiten valores de 1 a 3.

   c. **X** es un campo de 1 bit. Indica la presencia (1) o ausencia (0) de datos de excepción.

   d. **E** es un campo de 1 bit. Indica que la información que describe un único epílogo está empaquetada en el encabezado (1) en lugar de requerir más palabras de ámbito posteriormente (0).

   e. **Epilog Count** (Recuento de epílogos) es un campo de 5 bits que tiene dos significados, en función del estado del bit **E**:

      1. Si **E** es 0, especifica el recuento del número total de ámbitos de epílogos descritos en la sección 2. Si hay más de 31 ámbitos en la función, el campo **Code Words** (Palabras de código) se debe establecer en 0 para indicar que se necesita una palabra de extensión.

      2. Si **E** es 1, este campo especifica el índice del primer código de desenredado que describe el único epílogo.

   f. **Code Words** (Palabras de código) es un campo de 5 bits que especifica el número de palabras de 32 bits necesario para contener todos los códigos de desenredado en la sección 3. Si se necesitan más de 31 palabras (es decir, si hay más de 124 bytes de código de desenredado), este campo se debe establecer en 0 para indicar que se necesita una palabra de extensión.

   g. **Extended Epilog Count** (Recuento de epílogos ampliados) y **Extended Code Words** (Palabras de código ampliadas) son campos de 16 y 8 bits, respectivamente. Proporcionan más espacio para poder codificar un número inusualmente grande de epílogos o de palabras de código de desenredado. La palabra de extensión que contiene estos campos solo está presente si los campos **Epilog Count** (Recuento de epílogos) y  **Code Words** (Palabras de código) de la primera palabra del encabezado son 0.

1. Si **Epilog Count** (Recuento de epílogos) no es cero, una lista de información sobre los ámbitos de epílogo, empaquetada a una palabra, viene después del encabezado y del encabezado ampliado opcional. Se almacenan en orden de aumento de desplazamiento inicial. Cada ámbito contiene los siguientes bits:

   a. **Epilog Start Offset** (Desplazamiento inicial del epílogo) es un campo de 18 bits que tiene el desplazamiento del epílogo en bytes, dividido entre 4, con respecto al inicio de la función.

   b. **Res** es un campo de 4 bits reservado para futuras expansiones. Su valor debe ser 0.

   c. **Epilog Start Index** (Índice inicial del epílogo) es un campo de 10 bits, 2 bits más que **Extended Code Words** (Palabras de código ampliadas). Indica el índice de bytes del primer código de desenredado que describe este epílogo.

1. Tras la lista de ámbitos del epílogo viene una matriz de bytes que contiene códigos de desenredado, que se detallan en profundidad en una sección posterior. Esta matriz se rellena al final del límite de palabra completa más cercano. Los códigos de desenredado se escriben en esta matriz. Comienzan con el más cercano al cuerpo de la función y se desplazan hacia los bordes de esta. Los bytes de cada código de desenredado se almacenan en orden big-endian, de modo que se pueden capturar directamente, empezando primero por el byte más significativo, que identifica la operación y la longitud del resto del código.

1. Por último, después de los bytes del código de desenredado, si el bit **X** del encabezado se ha establecido en 1, aparece la información del controlador de excepciones. Consta de una única **Exception Handler RVA** (RVA del controlador de excepciones) que proporciona la dirección del propio controlador de excepciones. Va seguido inmediatamente de una cantidad de datos de longitud variable que requiere el controlador de excepciones.

El registro .xdata está diseñado de forma que se pueden capturar los primeros 8 bytes y usarlos para calcular el tamaño completo del registro, menos la longitud de los datos de excepción de tamaño variable que le siguen. En el fragmento de código siguiente se calcula el tamaño del registro:

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

Aunque el prólogo y cada epílogo tienen su propio índice en los códigos de desenredado, comparten la tabla. Es completamente posible (y no es del todo inusual) que puedan compartir todos los mismos códigos. (Para obtener más información, vea el Ejemplo 2 en la sección [Ejemplos](#examples)). Los escritores de compiladores deben optimizar en este caso concreto, dado que el índice más grande que se puede especificar es 255, lo cual limita el número total de códigos de desenredado posibles de una función en particular.

### <a name="unwind-codes"></a>Códigos de desenredado

La matriz de códigos de desenredado es un conjunto de secuencias que describen exactamente cómo deshacer los efectos del prólogo, almacenado en el mismo orden en el que las operaciones se deben deshacer. Los códigos de desenredado se pueden considerar como un conjunto pequeño de instrucciones, codificado como una cadena de bytes. Una vez completada la ejecución, la dirección de devolución a la función de llamada se encuentra en el registro de LR. Y todos los registros no volátiles se restauran a sus valores en el momento en el que se ha llamado a la función.

Si existiera la certeza de que solo pueden producirse excepciones dentro de un cuerpo de función, y nunca en un prólogo o en un epílogo, solo sería necesaria una única secuencia. Sin embargo, el modelo de desenredado de Windows requiere que el código se pueda desenredar desde un prólogo o epílogo parcialmente ejecutado. A fin de cumplir este requisito, los códigos de desenredado se han diseñado meticulosamente de forma que tienen una asignación sin ambigüedad de 1:1 para cada código de operación relevante en el prólogo y el epílogo. Este diseño tiene varias implicaciones:

1. Mediante el recuento del número de códigos de desenredado, es posible calcular la longitud del prólogo y el epílogo.

1. Mediante el recuento del número de instrucciones pasado el inicio de un ámbito de epílogo, es posible omitir el número equivalente de códigos de desenredado. Después, podemos ejecutar el resto de una secuencia para completar el desenredado parcialmente ejecutado que realiza el epílogo.

1. Mediante el recuento del número de instrucciones antes del final del prólogo, es posible omitir el número equivalente de códigos de desenredado. Después, podemos ejecutar el resto de la secuencia para deshacer solo las partes del prólogo que hayan finalizado su ejecución.

Los códigos de desenredado se codifican según la tabla siguiente. Todos los códigos de desenredado son de byte único o doble, excepto el que asigna una pila grande. En total hay 21 códigos de desenredado. Cada código de desenredado asigna exactamente una instrucción en el prólogo o epílogo para permitir el desenredado de los prólogos y epílogos parcialmente ejecutados.

|Código de desenredado|Bits e interpretación|
|-|-|
|`alloc_s`|000xxxxx: asignar una pila pequeña de tamaño \< 512 (2^5 * 16).|
|`save_r19r20_x`|    001zzzzz: guardar un par \<x19,x20> en `[sp-#Z*8]!`, desplazamiento preindexado >= -248. |
|`save_fplr`|        01zzzzzz: guardar un par \<x29,lr> en `[sp+#Z*8]`, desplazamiento \<= 504. |
|`save_fplr_x`|        10zzzzzz: guardar un par \<x29,lr> en `[sp-(#Z+1)*8]!`, desplazamiento preindexado >= -512. |
|`alloc_m`|        11000xxx'xxxxxxxx: asignar una pila grande de tamaño \< 16 KB (2^11 * 16). |
|`save_regp`|        110010xx'xxzzzzzz: guardar un par x(19+#X) en `[sp+#Z*8]`, desplazamiento \<= 504. |
|`save_regp_x`|        110011xx'xxzzzzzz: guardar un par x(19+#X) en `[sp-(#Z+1)*8]!`, desplazamiento preindexado >= -512. |
|`save_reg`|        110100xx'xxzzzzzz: guardar un registro x(19+#X) en `[sp+#Z*8]`, desplazamiento \<= 504. |
|`save_reg_x`|        1101010x'xxxzzzzz: guardar un registro x(19+#X) en `[sp-(#Z+1)*8]!`, desplazamiento preindexado >= -256. |
|`save_lrpair`|         1101011x'xxzzzzzz: guardar un par \<x(19+2*#X),lr> en `[sp+#Z*8]`, desplazamiento \<= 504. |
|`save_fregp`|        1101100x'xxzzzzzz: guardar un par d(8+#X) en `[sp+#Z*8]`, desplazamiento \<= 504. |
|`save_fregp_x`|        1101101x'xxzzzzzz: guardar un registro d(8+#X), en `[sp-(#Z+1)*8]!`, desplazamiento preindexado >= -512. |
|`save_freg`|        1101110x'xxzzzzzz: guardar un registro d(8+#X) en `[sp+#Z*8]`, desplazamiento \<= 504. |
|`save_freg_x`|        11011110'xxxzzzzz: guardar un registro d(8+#X) en `[sp-(#Z+1)*8]!`, desplazamiento preindexado >= -256. |
|`alloc_l`|         11100000'xxxxxxxx'xxxxxxxx'xxxxxxxx: asignar una pila grande de tamaño \< 256 MB (2^24 *16). |
|`set_fp`|        11100001: configurar x29: con: `mov x29,sp`. |
|`add_fp`|        11100010'xxxxxxxx: configurar x29 con: `add x29,sp,#x*8`. |
|`nop`|            11100011: no se requiere ninguna operación de desenredado. |
|`end`|            11100100: final del código de desenredado. Implica ret en el epílogo. |
|`end_c`|        11100101: final del código de desenredado en el ámbito encadenado actual. |
|`save_next`|        11100110: guardar el siguiente par de registros Int o FP no volátiles. |
|`arithmetic(add)`|    11100111'000zxxxx: sumar cookie reg(z) a lr (0=x28, 1=sp); `add lr, lr, reg(z)` |
|`arithmetic(sub)`|    11100111'001zxxxx: restar cookie reg(z) de lr (0=x28, 1=sp); `sub lr, lr, reg(z)` |
|`arithmetic(eor)`|    11100111'010zxxxx: eor lr con cookie reg(z) (0=x28, 1=sp); `eor lr, lr, reg(z)` |
|`arithmetic(rol)`|    11100111'0110xxxx: rol simulado de LR con el registro de cookies (x28); xip0 = neg x28; `ror lr, xip0` |
|`arithmetic(ror)`|    11100111'100zxxxx: ror lr con cookie reg(z) (0=x28, 1=sp); `ror lr, lr, reg(z)` |
| |            11100111: xxxz----: ---- reservado |
| |              11101xxx: reservado para los casos de pila personalizados siguientes generados solo para las rutinas ASM |
| |              11101000: pila personalizada para MSFT_OP_TRAP_FRAME |
| |              11101001: pila personalizada para MSFT_OP_MACHINE_FRAME |
| |              11101010: pila personalizada para MSFT_OP_CONTEXT |
| |              11101100: Pila personalizada para MSFT_OP_CLEAR_UNWOUND_TO_CALL |
| |              1111xxxx: reservado |

En las instrucciones en las que hay valores grandes que ocupan múltiples bytes, los bits más relevantes son los que están almacenados en primer lugar. Este diseño permite encontrar el tamaño total, en bytes, del código de desenredado con solo buscar el primer byte del código. Dado que cada código de desenredado se asigna exactamente a una instrucción en un prólogo o epílogo, se puede calcular el tamaño del prólogo o epílogo. Se puede recorrer desde el principio de la secuencia hasta el final y usar una tabla de búsqueda, o un dispositivo similar, para averiguar la longitud del código de operación correspondiente.

No se permite el direccionamiento de desplazamiento posterior al índice en un prólogo. Todos los rangos de desplazamiento (#Z) coinciden con la codificación del direccionamiento de STP/STR excepto `save_r19r20_x`, en el que 248 es suficiente para todas las áreas de almacenamiento (10 registros Int + 8 registros FP + 8 registros de entrada).

`save_next` debe seguir un par de registros volátiles de tipo guardar para Int o FP: `save_regp`, `save_regp_x`, `save_fregp`, `save_fregp_x`, `save_r19r20_x` u otro `save_next`. Guarda el par de registros siguiente en la ranura siguiente de 16 bytes en orden "creciente". Un elemento `save_next` hace referencia al primer par de registros FP cuando sigue el elemento `save-next` que denota el último par de registros Int.

Dado que el tamaño de las instrucciones de devolución y salto normales es el mismo, no es necesario un código de desenredado de `end` independiente para escenarios de llamada de cola.

`end_c` está diseñado para administrar fragmentos de función no contiguos con fines de optimización. Un elemento `end_c` que indica el final de los códigos de desenredado en el ámbito actual debe ir seguido de otra serie de código de desenredado finalizada con un elemento `end` real. Los códigos de desenredado entre `end_c` y `end` representan las operaciones de prólogo en la región primaria (prólogo "fantasma").  En la sección siguiente se describen más detalles y ejemplos.

### <a name="packed-unwind-data"></a>Datos de desenredado empaquetados

Se pueden usar datos de desenredado empaquetados en las funciones cuyos prólogos y epílogos sigan el formato canónico descrito a continuación. Elimina por completo la necesidad de un registro .xdata y reduce notablemente el costo necesario para proporcionar datos de desenredado. Los prólogos y epílogos canónicos están diseñados para satisfacer los requisitos comunes de una función sencilla: Uno que no requiere un controlador de excepciones y que realiza las operaciones de configuración y desmontaje en un orden estándar.

El formato de un registro .pdata con datos de desenredado empaquetados tiene el aspecto siguiente:

![registro .pdata con datos de desenredado empaquetados](media/arm64-exception-handling-packed-unwind-data.png "registro .pdata con datos de desenredado empaquetados")

Los campos son los siguientes:

- **Function Start RVA** (RVA de inicio de la función) es la RVA de 32 bits del inicio de la función.
- **Flag** (Marca) es un campo de 2 bits tal como se ha descrito anteriormente, con los significados siguientes:
  - 00 = no se usan datos de desenredado empaquetados; el resto de los bits apuntan a un registro .xdata.
  - 01 = se usan datos de desenredado empaquetados con un solo prólogo y epílogo al principio y al final del ámbito.
  - 10 = se usan datos de desenredado empaquetados para el código sin ningún prólogo ni epílogo. Útil para describir segmentos de funciones independientes.
  - 11 = reservado.
- **Function Length** (Longitud de la función) es un campo de 11 bits que proporciona la longitud de toda la función, en bytes, dividida entre 4. Si la función supera los 8 KB, se deberá usar en su lugar un registro .xdata completo.
- **Frame Size** (Tamaño de marco) es un campo de 9 bits que indica el número de bytes de la pila asignado para esta función, dividido entre 16. Las funciones que asignan más de 8-16 KB de la pila deben usar un registro .xdata completo. Incluye el área de variables locales, el área de parámetros de salida, el área de Int y FP guardados por el destinatario y el área de parámetros de inicio, pero excluye el área de asignación dinámica.
- **CR** es una marca de 2 bits que indica si la función incluye instrucciones adicionales para configurar una cadena de marcos y un vínculo de retorno.
  - 00 = función no encadenada, el par \<X29,lr> no se guarda en la pila.
  - 01 = función no encadenada, \<lr> se guarda en la pila.
  - 10 = reservado.
  - 11 = función encadenada, se usa una instrucción de par de carga o almacenamiento en el prólogo o epílogo \<X29,lr>.
- **H** es una marca de 1 bit que indica si la función aloja los registros de parámetros de entero (x0-x7) almacenándolos en el inicio de la función. (0 = no aloja registros, 1 = aloja registros).
- **RegI** es un campo de 4 bits que indica el número de registros INT no volátiles (x19-x28) guardados en la ubicación de pila canónica.
- **RegF** es un campo de 3 bits que indica el número de registros FP no volátiles (d8-d15) guardados en la ubicación de pila canónica. (RegF = 0: no se guarda ningún registro FP; RegF>0: se guardan los registros RegF+1 FP). Los datos de desenredado empaquetados no se pueden usar para una función que solo guarde un registro FP.

Los prólogos canónicos que se encuentran en las categorías 1, 2 (sin área de parámetros de salida), 3 y 4 en la sección anterior se pueden representar con el formato de desenredado empaquetado.  Los epílogos de las funciones canónicas siguen un formato similar, salvo que **H** no tiene ningún efecto, se omite la instrucción `set_fp` y el orden de los pasos y las instrucciones de cada paso se invierten en el epílogo. El algoritmo para .xdata empaquetados sigue estos pasos, que se detallan en la tabla siguiente:

Paso 0: Calcular previamente el tamaño de cada área.

Paso 1: Guardar registros Int guardados por el destinatario.

Paso 2: Este paso es específico para el tipo 4 en las primeras secciones. LR se guarda al final del área Int.

Paso 3: Guardar registros FP guardados por el destinatario.

Paso 4: Guardar argumentos de entrada en el área de parámetros de inicio.

Paso 5: Asignar la pila restante, incluidos el área local, el par \<x29,lr> y el área de parámetros de salida. 5a corresponde al tipo canónico 1. 5b y 5c son para el tipo canónico 2. 5d y 5e son para los tipos 3 y 4.

Núm. de paso|Valores de marca|Núm. de instrucciones|Código de operación|Código de desenredado
-|-|-|-|-
0|||`#intsz = RegI * 8;`<br/>`if (CR==01) #intsz += 8; // lr`<br/>`#fpsz = RegF * 8;`<br/>`if(RegF) #fpsz += 8;`<br/>`#savsz=((#intsz+#fpsz+8*8*H)+0xf)&~0xf)`<br/>`#locsz = #famsz - #savsz`|
1|0 < **RegI** <= 10|RegI / 2 + **RegI** % 2|`stp x19,x20,[sp,#savsz]!`<br/>`stp x21,x22,[sp,#16]`<br/>`...`|`save_regp_x`<br/>`save_regp`<br/>`...`
2|**CR**==01*|1|`str lr,[sp,#(intsz-8)]`\*|`save_reg`
3|0 < **RegF** <=7|(RegF + 1) / 2 +<br/>(RegF + 1) % 2)|`stp d8,d9,[sp,#intsz]`\*\*<br/>`stp d10,d11,[sp,#(intsz+16)]`<br/>`...`<br/>`str d(8+RegF),[sp,#(intsz+fpsz-8)]`|`save_fregp`<br/>`...`<br/>`save_freg`
4|**H** == 1|4|`stp x0,x1,[sp,#(intsz+fpsz)]`<br/>`stp x2,x3,[sp,#(intsz+fpsz+16)]`<br/>`stp x4,x5,[sp,#(intsz+fpsz+32)]`<br/>`stp x6,x7,[sp,#(intsz+fpsz+48)]`|`nop`<br/>`nop`<br/>`nop`<br/>`nop`
5a|**CR** == 11 && #locsz<br/> <= 512|2|`stp x29,lr,[sp,#-locsz]!`<br/>`mov x29,sp`\*\*\*|`save_fplr_x`<br/>`set_fp`
5b|**CR** == 11 &&<br/>512 < #locsz <= 4080|3|`sub sp,sp,#locsz`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5c|**CR** == 11 && #locsz > 4080|4|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`<br/>`stp x29,lr,[sp,0]`<br/>`add x29,sp,0`|`alloc_m`<br/>`alloc_s`/`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5d|(**CR** == 00 \|\| **CR**==01) &&<br/>#locsz <= 4080|1|`sub sp,sp,#locsz`|`alloc_s`/`alloc_m`
5e|(**CR** == 00 \|\| **CR**==01) &&<br/>#locsz > 4080|2|`sub sp,sp,4080`<br/>`sub sp,sp,#(locsz-4080)`|`alloc_m`<br/>`alloc_s`/`alloc_m`

\* Si **CR** == 01 y **RegI** es un número impar, el paso 2 y el último elemento save_rep del paso 1 se combinan en un elemento save_regp.

\*\* Si **RegI** == **CR** == 0 y **RegF** ! = 0, el primer STP del punto flotante realiza el predecremento.

\*\*\* No existe ninguna instrucción correspondiente a `mov x29,sp` en el epílogo. No se pueden usar datos de desenredado empaquetados si una función requiere la restauración de SP desde x29.

### <a name="unwinding-partial-prologs-and-epilogs"></a>Desenredado de prólogos y epílogos parciales

La situación de desenredado más habitual tiene lugar cuando se produce una excepción o una llamada en el cuerpo de la función, que no tiene nada que ver con el prólogo y ninguno de los epílogos. En esta situación, el desenredado es sencillo: el responsable del desenredado simplemente comienza a ejecutar los códigos de la matriz de desenredado, empezando en el índice 0 y continuando hasta que se detecta un código de operación de finalización.

Es más difícil desenredar correctamente en caso de que se produzca una excepción o una interrupción mientras se ejecuta un prólogo o un epílogo. En estas situaciones, el marco de pila solo se construye parcialmente. El problema es determinar exactamente lo que se ha hecho, para deshacerlo correctamente.

Por ejemplo, tome esta secuencia de prólogo y epílogo:

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

Junto a cada código de operación se encuentra el código de desenredado adecuado que describe esta operación. Se puede ver cómo la serie de códigos de desenredado del prólogo es una imagen exacta reflejada de los códigos de desenredado del epílogo, sin contar su instrucción final. Esto es una situación habitual y constituye el motivo por el cual siempre asumimos que los códigos de desenredado del prólogo se almacenan en orden inverso al orden de ejecución del prólogo.

Por lo tanto, para el prólogo y el epílogo, nos quedamos con un conjunto habitual de códigos de desenredado:

`set_fp`, `save_regp 0,240`, `save_fregp,0,224`, `save_fplr_x_256`, `end`

El caso de epílogo es sencillo, ya que está en orden estándar. A partir del desplazamiento 0 en el epílogo (que comienza en el desplazamiento 0x100 en la función), esperamos ejecutar la secuencia de desenredado completa, ya que aún no se ha realizado ninguna limpieza. Si ya hemos avanzado una instrucción (en el desplazamiento 2 del epílogo), podemos desenredar correctamente omitiendo el primer código de desenredado. Se puede generalizar esta situación y suponer una asignación de 1:1 entre códigos de operación y códigos de desenredado. Después, para iniciar el desenredado de la instrucción *n* en el epílogo, deberíamos omitir los primeros *n* códigos de desenredado y comenzar a ejecutar desde allí.

Resulta que funciona una lógica similar para el prólogo, salvo que en orden inverso. Si comenzamos a desenredar desde el desplazamiento 0 en el prólogo, queremos que no se ejecute nada. Si desenredamos desde el desplazamiento 2, que es una avanzar una instrucción, querremos empezar a ejecutar la secuencia de desenredado un código de desenredado del final. (Recuerde que los códigos se almacenan en orden inverso). De nuevo aquí podemos generalizar: si empezamos a desenredar desde la instrucción n en el prólogo, deberíamos empezar a ejecutar n códigos de desenredado desde el final de la lista de códigos.

No siempre ocurre que coincidan exactamente los códigos del prólogo y el epílogo. Este es el motivo por el que es posible que la matriz de desenredado deba contener varias secuencias de códigos. Use la lógica siguiente para determinar el desplazamiento por el que empezar a procesar códigos:

1. Si desenreda desde el cuerpo de la función, empiece a ejecutar códigos de desenredado en el índice 0 y continúe hasta llegar a un código de operación de "finalización".

1. Si se desenreda desde un epílogo, utilice el índice de inicio específico de dicho epílogo, suministrado con el ámbito del epílogo como un punto de inicio. Calcule el número de bytes del PC en cuestión desde el inicio del epílogo. Después avance por los códigos de desenredado, omitiendo los códigos de desenredado hasta haber pasado por todas las instrucciones que ya se han ejecutado. Luego ejecute a partir de ese punto.

1. Si el desenredado se encuentra en el prólogo, use el índice 0 como punto de partida. Calcule la longitud del código del prólogo desde la secuencia y, después, calcule el número de bytes del PC en cuestión desde el final del prólogo. Después avance por los códigos de desenredado, omitiendo los códigos de desenredado hasta haber pasado por todas las instrucciones que todavía no se hayan ejecutado. Luego ejecute a partir de ese punto.

Estas reglas significan que los códigos de desenredado del prólogo siempre deben ser los primeros en la matriz. También son los códigos que se usan para desenredar en el caso general de desenredado desde el cuerpo. Las secuencias de código específicas de los epílogos deben ir inmediatamente después.

### <a name="function-fragments"></a>Fragmentos de función

Para fines de optimización de código y otros motivos, puede ser preferible dividir una función en fragmentos separados (también denominados regiones). Cuando se divide, cada fragmento resultante de la función necesita tener su propio registro .pdata independiente (y, probablemente, también uno .xdata).

Para cada fragmento secundario independiente que tenga su propio prólogo, se espera que no se realice ningún ajuste de la pila en su prólogo. Todo el espacio de la pila necesario para una región secundaria lo debe asignar previamente su región primaria (o región del host). Esto hace que la manipulación de puntero de pila tenga lugar estrictamente en el prólogo original de la función.

Un caso típico de fragmentos de función es la "separación de código", donde ese compilador puede quitar una región de código de su función de host. Hay tres casos inusuales que podría provocar la separación de código.

#### <a name="example"></a>Ejemplo

- (región 1: inicio)

    ```asm
        stp     x29,lr,[sp,#-256]!      // save_fplr_x  256 (pre-indexed store)
        stp     x19,x20,[sp,#240]       // save_regp 0, 240
        mov     x29,sp                  // set_fp
        ...
    ```

- (región 1: final)

- (región 3: inicio)

    ```asm
        ...
    ```

- (región 3: final)

- (región 2: inicio)

    ```asm
        ...
        mov     sp,x29                  // set_fp
        ldp     x19,x20,[sp,#240]       // save_regp 0, 240
        ldp     x29,lr,[sp],#256        // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (región 2: final)

1. Solo prólogo (región 1: todos los epílogos se encuentran en regiones independientes):

   Solo se debe describir el prólogo. No se puede representar en el formato .pdata compacto. En el caso completo de .xdata, se puede representar estableciendo el valor Epilog Count (Recuento de epílogos) = 0. Vea la región 1 en el ejemplo anterior.

   Códigos de desenredado: `set_fp`, `save_regp 0,240`, `save_fplr_x_256` y `end`.

1. Solo epílogos (región 2: el prólogo está en la región del host):

   Se supone que, al saltar el control a esta región, se han ejecutado todos los códigos del prólogo. El desenredado parcial puede producirse en los epílogos de la misma manera que en una función normal. Este tipo de región no se puede representar mediante el formato .pdata compacto. En el registro .xdata completo, se puede codificar con un prólogo "fantasma", entre corchetes mediante un par de código de desenredado `end_c` y `end`.  El elemento `end_c` inicial indica que el tamaño del prólogo es cero. El campo Epilog Start Index (Índice inicial del epílogo) de los puntos de epílogo únicos apunta a `set_fp`.

   Códigos de desenredado para la región 2: `end_c`, `set_fp`, `save_regp 0,240`, `save_fplr_x_256` y `end`.

1. Ningún registro ni epílogo (región 3: los prólogos y todos los epílogos están en otros fragmentos):

   El formato .pdata compacto se puede aplicar a través de configurar el campo Flag (Marca) = 10. Con el registro .xdata completo, Epilog Count (Recuento de epílogos) = 1. El código de desenredado es el mismo que el código de la región 2 anterior, pero el campo Epilog Start Index (Índice inicial del epílogo) también apunta a `end_c`. El desenredado parcial nunca se producirá en esta región de código.

Otro caso más complicado de fragmentos de función es "ajuste de reducción". Es posible que el compilador opte por retrasar el almacenamiento de algunos registros guardados por el destinatario hasta que estén fuera del prólogo de entrada de la función.

- (región 1: inicio)

    ```asm
        stp     x29,lr,[sp,#-256]!      // save_fplr_x  256 (pre-indexed store)
        stp     x19,x20,[sp,#240]       // save_regp 0, 240
        mov     x29,sp                  // set_fp
        ...
    ```

- (región 2: inicio)

    ```asm
        stp     x21,x22,[sp,#224]       // save_regp 2, 224
        ...
        ldp     x21,x22,[sp,#224]       // save_regp 2, 224
    ```

- (región 2: final)

    ```asm
        ...
        mov     sp,x29                  // set_fp
        ldp     x19,x20,[sp,#240]       // save_regp 0, 240
        ldp     x29,lr,[sp],#256        // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (región 1: final)

En el prólogo de la región 1, el espacio de pila está preasignado. Se puede ver que la región 2 tendrá el mismo código de desenredado incluso si se quita de su función de host.

Región 1: `set_fp`, `save_regp 0,240`, `save_fplr_x_256` y `end` con el campo Epilog Start Index (Índice inicial del epílogo) que apunta a `set_fp`, como de costumbre.

Región 2: `save_regp 2, 224`, `end_c`, `set_fp`, `save_regp 0,240`, `save_fplr_x_256` y `end`. El campo Epilog Start Index (Índice inicial del epílogo) apunta al primer código de desenredado `save_regp 2, 224`.

### <a name="large-functions"></a>Funciones de gran tamaño

Los fragmentos se pueden usar para describir funciones con un tamaño superior al límite de 1 MB que imponen los campos de bits en el encabezado de .xdata. Para describir una función muy grande como esta, debe dividirse en fragmentos menores que 1 MB. Cada fragmento se debe ajustar de forma que no divida un epílogo en varias partes.

Solo el primer fragmento de la función contendrá un prólogo; todos los demás están marcados como carentes de prólogo. Según cuál sea el número de epílogos presentes, cada fragmento puede contener cero o más epílogos. Recuerde que cada ámbito de epílogo en un fragmento especifica su desplazamiento de inicio con respecto al inicio del fragmento, no al inicio de la función.

Si un fragmento no tiene ni prólogo ni epílogo, seguirá necesitando su propio registro .pdata (y, probablemente, también un registro .xdata) para describir cómo llevar a cabo el desenredado desde el cuerpo de la función.

## <a name="examples"></a>Ejemplos

### <a name="example-1-frame-chained-compact-form"></a>Ejemplo 1: encadenada con marco y formato compacto.

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

### <a name="example-2-frame-chained-full-form-with-mirror-prolog--epilog"></a>Ejemplo 2: encadenada con marco y formato completo con un prólogo y epílogo reflejado.

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

El campo Epilog Start Index (Índice inicial del epílogo) [0] apunta a la misma secuencia del código de desenredado del prólogo.

### <a name="example-3-variadic-unchained-function"></a>Ejemplo 3: función variádica no encadenada

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

El campo Epilog Start Index (Índice inicial del epílogo) [4] apunta al centro del código de desenredado del prólogo (reutiliza parcialmente la matriz de desenredado).

## <a name="see-also"></a>Vea también

[Información general sobre las convenciones ABI de ARM64](arm64-windows-abi-conventions.md)<br/>
[Control de excepciones de ARM](arm-exception-handling.md)
