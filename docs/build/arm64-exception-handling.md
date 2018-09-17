---
title: Control de excepciones ARM64 | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7dfcf1839048f3c110bbca6754d1549161b63301
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716570"
---
# <a name="arm64-exception-handling"></a>Control de excepciones ARM64

Windows en ARM64 usa el mismo mecanismo de excepciones generadas por el hardware de asincrónicas y sincrónicas excepciones generadas por el software de control de excepciones estructurado. Los controladores de excepciones específicos de lenguaje se basan en el control de excepciones estructurado de Windows por medio de funciones auxiliares de lenguaje. Este documento describe el control de excepciones en Windows en ARM64 y las aplicaciones auxiliares de lenguaje utilizadas por el código generado por el ensamblador de ARM Microsoft y el compilador de Visual C++.

## <a name="goals-and-motivation"></a>Los objetivos y motivación

Las convenciones de datos de desenredo de excepciones y esta descripción, están diseñados para:

1. Proporcione suficiente descripción para permitir el desenredado sin código de sondeo en todos los casos.

   - Analizar el código requiere que el código de la paginación. Esto evita que el desenredado en algunas circunstancias donde resulta útil (seguimiento, de muestreo, la depuración).

   - Analizar el código es complejo; el compilador debe tener cuidado para generar solo instrucciones, que es capaz de descodificar el responsable del desenredado.

   - Si no se describe detalladamente mediante el uso de códigos de desenredado puede desenredar, a continuación, en algunos casos debe revertir a descodificar de la instrucción. Esto aumenta la complejidad general y lo ideal es que podría evitarse.

2. Soporte técnico de desenredado en medio del prólogo y epílogo intermedio.

   - Desenredo se usa en Windows durante más de control de excepciones, por lo que es fundamental que podremos realizar una lista precisa de desenredo incluso cuando en el medio de una secuencia de código de prólogo o epílogo.

3. Tardar una cantidad mínima de espacio.

   - No deben agregar los códigos de desenredado para aumentar significativamente el tamaño del archivo binario.

   - Puesto que los códigos de desenredado están probable que se puede bloquear en memoria, una pequeña superficie garantiza una sobrecarga mínima para cada archivo binario cargado.

## <a name="assumptions"></a>Suposiciones

Estos son los supuestos realizados en la descripción de control de excepciones:

1. Los prólogos y epílogos tienden a reflejarse cualquier otro. Al sacar partido de esta rasgo común, puede reducirse considerablemente el tamaño de los metadatos necesarios para describir el desenredado. Dentro del cuerpo de la función, no importa si las operaciones del prólogo se deshacen o las operaciones del epílogo se realizan de forma directa. Ambas deberían generar idénticos resultados.

2. Las funciones en todo el tienden a ser relativamente pequeñas. Varias optimizaciones para espacio dependen de esto con el fin de lograr el empaquetado más eficaz de datos.

3. No hay ningún código condicional de epílogos.

4. Dedicado de registro de puntero de marco: si el sp se guarde en otro registro (r29) en el prólogo, que registre permanece intacta en toda la función, para que el sp original podrá recuperarse en cualquier momento.

5. A menos que el sp se guarde en otro registro, toda la manipulación de puntero de pila ocurre estrictamente dentro del prólogo y epílogo.

6. El diseño del marco de pila está organizado como se describe en la sección siguiente.

## <a name="arm64-stack-frame-layout"></a>Diseño del marco de pila ARM64

![diseño del marco de pila](../build/media/arm64-exception-handling-stack-frame.png "diseño del marco de pila")

Para las funciones de marco encadenada, el par de fp y lr se puede guardar en cualquier posición de la variable local area dependiendo de las consideraciones de optimización. El objetivo es maximizar el número de variables locales que se puede tener acceso mediante una única instrucción en función de puntero de marco (r29) o de puntero de pila (sp). Sin embargo para `alloca` funciones, debe estar encadenada y r29 debe apuntar a la parte inferior de la pila. Para permitir una mejor cobertura de registro par direccionamiento-modo de, no volátil registrar aave áreas se colocan en la parte superior de la pila del área Local. Estos son ejemplos que ilustran varias de las secuencias de prólogo más eficaces. Para mayor claridad mejor emplazamiento en caché, el orden de almacenar los registros guardados y en todos los prólogos canónicos es en orden "creciente de". `#framesz` a continuación representa el tamaño de pila completa (excepto el área de alloca). `#localsz` y `#outsz` indican el tamaño de área local (incluida la operación de Guardar área para el \<r29, lr > par) y el tamaño del parámetro de salida, respectivamente.

1. Encadenar #localsz < = 512

    ```asm
        stp    r19,r20,[sp,-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,16]            // save in FP regs (optional)
        stp    r0,r1,[sp,32]            // home params (optional)
        stp    r2,r3,[sp, 48]
        stp    r4,r5,[sp,64]
        stp    r6,r7,[sp,72]
        stp    r29, lr, [sp, -#localsz]!    // save <r29,lr> at bottom of local area
        mov    r29,sp                   // r29 points to bottom of local
        sub    sp, #outsz               // (optional for #outsz != 0)
    ```

2. Encadenar #localsz > 512

    ```asm
        stp    r19,r20,[sp,-96]!        // pre-indexed, save in 1st FP/INT pair
        stp    d8,d9,[sp,16]            // save in FP regs (optional)
        stp    r0,r1,[sp,32]            // home params (optional)
        stp    r2,r3,[sp, 48]
        stp    r4,r5,[sp,64]
        stp    r6,r7,[sp,72]
        sub    sp,#localsz+#outsz       // allocate remaining frame
        stp    r29, lr, [sp, #outsz]    // save <r29,lr> at bottom of local area
        add    r29,sp, #outsz           // setup r29 points to bottom of local area
    ```

3. , Las funciones de hoja (lr sin guardar)

    ```asm
        stp    r19,r20,[sp, -72]!       // pre-indexed, save in 1st FP/INT reg-pair
        stp    r21,r22,[sp, 16]
        str    r23 [sp,32]
        stp    d8,d9,[sp,40]            // save FP regs (optional)
        stp    d10,d11,[sp,56]
        sub    sp,#framesz-72           // allocate the remaining local area
    ```

   Se tiene acceso a todas las variables locales en función de SP. \<R29, lr > señala al fotograma anterior. Para el tamaño del marco de < = 512, el "sub sp,..." puede optimizarse si el área de guardado de los registros se mueve a la parte inferior de la pila. La desventaja de es que no es coherente con otros diseños anteriores, y los registros guardados formen parte del intervalo para los registros el par y el modo de direccionamiento desplazamiento previo y posteriores al indizado.

4. Funciones, no de hoja (lr se guarda en el área de Int guardado)

    ```asm
        stp    r19,r20,[sp,-80]!        // pre-indexed, save in 1st FP/INT reg-pair
        stp    r21,r22,[sp,16]          // ...
        stp    r23, lr,[sp, 32]         // save last Int reg and lr
        stp    d8,d9,[sp, 48]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,64]          // ...
        sub    sp,#framesz-80           // allocate the remaining local area
    ```

   O bien, con un número par de los registros de Int, guardados

    ```asm
        stp    r19,r20,[sp,-72]!        // pre-indexed, save in 1st FP/INT reg-pair
        stp    r21,r22,[sp,16]          // ...
        str    lr,[sp, 32]              // save lr
        stp    d8,d9,[sp, 40]           // save FP reg-pair (optional)
        stp    d10,d11,[sp,56]          // ...
        sub    sp,#framesz-72           // allocate the remaining local area
    ```

   Solo r19 guardado:

    ```asm
        sub    sp, sp, #16              // reg save area allocation*
        stp    r19,lr,[sp,0]            // save r19, lr
        sub    sp,#framesz-16           // allocate the remaining local area
    ```

   \* El registro de la asignación del área de almacenamiento no se dobla en el stp porque no se puede representar un stp reg-lr indizada previamente con los códigos de desenredado.

   Se tiene acceso a todas las variables locales en función de SP. \<R29 > señala al fotograma anterior.

5. Encadenar #framesz < = 512, #outsz = 0

    ```asm
        stp    r29, lr, [sp, -#framesz]!    // pre-indexed, save <r29,lr>
        mov    r29,sp                       // r29 points to bottom of stack
        stp    r19,r20,[sp, #framesz -32]   // save INT pair
        stp    d8,d9,[sp, #framesz -16]     // save FP pair
    ```

   En comparación con el prólogo #1 anterior, la ventaja es que todos los registros guardar instrucciones está listo para ejecutarse justo después de la pila solo una instrucción de asignación. Por lo tanto, no hay ninguna dependencia contra de sp que impide el paralelismo de nivel.

6. Encadenadas, el tamaño de trama > 512 (opcional para las funciones sin alloca)

    ```asm
        stp    r29, lr, [sp, -80]!          // pre-indexed, save <r29,lr>
        stp    r19,r20,[sp,16]              // save in INT regs
        stp    r21,r22,[sp,32]              // ...
        stp    d8,d9,[sp,48]                // save in FP regs
        stp    d10,d11,[sp,64]
        mov    r29,sp                       // r29 points to top of local area
        sub    sp,#framesz-80               // allocate the remaining local area
    ```

   Con fines de optimización, r29 puede colocarse en cualquier posición de área local para proporcionar una mejor cobertura "reg par" y pre/post-la indexed desplazamiento de modo de direccionamiento. Pueden tener acceso a variables locales por debajo de los punteros de marco basado en SP.

7. Encadenadas, el tamaño de trama > 4K, con o sin alloca(),

    ```asm
        stp    r29, lr, [sp, -80]!          // pre-indexed, save <r29,lr>
        stp    r19,r20,[sp,16]              // save in INT regs
        stp    r21,r22,[sp,32]              // ...
        stp    d8,d9,[sp,48]                // save in FP regs
        stp    d10,d11,[sp,64]
        mov    r29,sp                       // r29 points to top of local area
        mov    r8, #framesz/16
        bl     chkstk
        sub    sp, r8*16                    // allocate remaining frame
                                            // end of prolog
        ...
        sp = alloca                         // more alloca() in body
        ...
                                            // beginning of epilog
        mov    sp,r29                       // sp points to top of local area
        ldp    d10,d11, [sp,64],
        ...
        ldp    r29, lr, [sp], -80           // post-indexed, reload <r29,lr>
    ```

## <a name="arm64-exception-handling-information"></a>Información de control de excepciones ARM64

### <a name="pdata-records"></a>registros .pdata

Los registros .pdata son una matriz ordenada de elementos de longitud fija que describen cada función de manipulación de pila en un binario PE. Tenga en cuenta cuidadosamente la frase "manipulación de la pila": las funciones de hoja que no requieren un almacenamiento local y que no es necesario guardar ni restaurar registros no volátiles no requieren un registro .pdata; estos se deben omitir explícitamente para ahorrar espacio. Un desenredo de una de estas funciones simplemente puede obtener la dirección de devolución de LR para subir al llamador.

Cada registro .pdata para ARM64 tiene 8 bytes de longitud. El formato general de los cada lugares registros la RVA de 32 bits de la función de inicio en la primera palabra, seguida de un segundo con la que contiene un puntero a un bloque .xdata de longitud variable, o una palabra empaquetada que describe una secuencia de desenredado de función canónica.

![diseño de registro .pdata](../build/media/arm64-exception-handling-pdata-record.png "composición de registro .pdata")

Los campos son los siguientes:

- **Función iniciar RVA** es la RVA de 32 bits del inicio de la función.

- **Marca** es un campo de 2 bits que indica cómo interpretar los 30 bits restantes de la segunda palabra .pdata. Si **marca** es 0, a continuación, el resto de bits forma un **RVA de información de excepción** (con los dos bits inferiores implícitamente en 0). Si **marca** es distinto de cero, a continuación, el resto de bits forma un **datos de desenredado empaquetado** estructura.

- **RVA de información de excepción** es la dirección de la estructura de información de excepción de longitud variable almacenada en la sección .xdata. Estos datos deben tener una alineación de 4 bytes.

- **Empaqueta los datos de desenredo** es una descripción comprimida de las operaciones necesarias para desenredar desde una función, suponiendo que la forma canónica. En este caso, no se necesita un registro .xdata.

### <a name="xdata-records"></a>registros .xdata

Cuando el formato de desenredado empaquetado no basta para describir el desenredado de una función, se debe crear un registro .xdata de longitud variable. La dirección de este registro se almacena en la segunda palabra del registro .pdata. El formato de .xdata es un conjunto de longitud variable empaquetado de palabras:

![diseño de registro .xdata](../build/media/arm64-exception-handling-xdata-record.png "composición de registro .xdata")

Estos datos se dividen en cuatro secciones:

1. Un encabezado de 1 o 2 palabras que describe el tamaño total de la estructura y proporcionar datos de la función clave. La segunda palabra solo está presente si tanto el **epílogo recuento** y **código palabras** campos se establecen en 0. Estos son los campos de bits en el encabezado:

   a. **Función longitud** es un campo de 18 bits que indica la longitud total de la función en bytes dividida entre 4. Si una función es mayor que 1 millón, varios registros de pdata y xdata deben utilizarse para describir la función. Consulte la [funciones grandes](#large-functions) sección para obtener más detalles.

   b. **Vers** es un campo de 2 bits que describe la versión de los xdata restantes. Cuando se redactó este documento, sólo la versión 0 está definida y, por tanto, no se permiten valores de 1 a 3.

   c. **X** es un campo de 1 bit que indica la presencia (1) o ausencia (0) de datos de excepción.

   d. **E** es un campo de bits indica que la información que describe un único epílogo está empaquetado en el encabezado (1) en lugar de requerir ámbito adicional palabras posteriores (0).

   e. **Recuento de epílogo** es un campo de 5 bits que tiene dos significados posibles, dependiendo del estado de **E** bits:

      1. Si **E** se establece en 0: especifica el recuento del número total de ámbitos de excepción que se describe en la sección 2. Si existen más de 31 ámbitos en la función, el **código palabras** campo debe establecerse en 0 para indicar que se necesita una palabra de extensión.

      2. Si **E** está establecido en 1, a continuación, este campo especifica el índice del primer código de desenredado que describe el uno y solo epílogo.

   f. **Código palabras** es un campo de 5 bits que especifica el número de palabras de 32 bits necesarios para contener todos los códigos de desenredado en la sección 4. Si se requieren más de 31 palabras (es decir, más de 124 desenredar bytes de código), a continuación, este campo debe establecerse en 0 para indicar que se necesita una palabra de extensión.

   g. **Cuenta de epílogo extendida** y **extendidos código palabras** son campos de 16 bits y 8 bits, respectivamente, que proporcionan más espacio para codificar un número inusualmente grande de epílogos o un número inusualmente grande de palabras de código de desenredado. La palabra de extensión que contiene estos campos solo está presente si tanto el **epílogo recuento** y **código palabras** campos en la primera palabra del encabezado se establecen en 0.

2. Después de los datos de excepción, si **epílogo recuento** no es cero, es una lista de información sobre los ámbitos de epílogo, uno empaquetado en una palabra y se almacenan en orden creciente de desplazamiento inicial. Cada ámbito contiene los bits siguientes:

   a. **Desplazamiento de inicio del epílogo** es un campo de 18 bits que describe el desplazamiento en bytes dividida entre 4 del epílogo en relación con el inicio de la función

   b. **Res** es un campo de 4 bits reservado para una futura expansión. Su valor debe ser 0.

   c. **Índice inicial de epílogo** es de 10 bits (más de 2 bits que **extendidos código palabras**) desenredo de campo que indica el índice de bytes del primer código que describe este epílogo.

3. Después de la lista de ámbitos de epílogo viene una matriz de bytes que contiene códigos de desenredado, se describe en detalle en una sección posterior. Esta matriz se rellena al final del límite de palabra completa más cercano. Los bytes se almacenan en orden little-endian, por lo que se pueden recuperar directamente en modo little-endian.

4. Por último, después los bytes de código de desenredado (y si el **X** bit en el encabezado se establece en 1) incluye la información del controlador de excepción. Esto se compone de una sola **RVA del controlador de excepción** proporcionando la dirección del controlador de excepciones, seguida inmediatamente de una cantidad de longitud variable de datos requeridos por el controlador de excepciones.

El registro .xdata anterior está diseñado para que es posible capturar los primeros 8 bytes y desde el calcular el tamaño completo del registro (menos la longitud de los datos de tamaño variable que sigue). El fragmento de código siguiente calcula el tamaño del registro:

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

Se debe tener en cuenta que aunque el tipo de prólogo y cada epílogo tiene su propio índice en los códigos de desenredado, la tabla se comparte entre ellos y es totalmente posible (y no por completo poco frecuente) que puede todos comparten los mismos códigos (vea el ejemplo 2 en el apéndice A, a continuación). Los autores de compiladores deberían optimizar para este caso, en particular porque el índice más grande que se puede especificar es de 255, lo que limita el número total de códigos de desenredado para una función determinada.

### <a name="unwind-codes"></a>Códigos de desenredado

La matriz de códigos de desenredado es el grupo de secuencias que describen exactamente cómo deshacer los efectos del prólogo, en el orden en que las operaciones de tienen que deshacerse. Los códigos de desenredado pueden considerarse como un mini conjunto de instrucciones codificado como una cadena de bytes. Cuando haya finalizado la ejecución, la dirección de retorno a la función que realiza la llamada está en el registro de lr, y todos los registros no volátiles se restauran en sus valores en el momento en que se llamó la función.

Si se garantiza que las excepciones solo se producen dentro de un cuerpo de función (y nunca con un prólogo o cualquier epílogo), solo una única secuencia sería necesaria. Sin embargo, el modelo de desenredado en Windows requiere que se pueda desenredar desde un parcialmente ejecutado prólogo o epílogo. Con el fin de satisfacer este requisito, los códigos de desenredado se han cuidadosamente diseñados, que se asignan inequívocamente 1:1 para cada código de operación relevante en el prólogo y epílogo. Esto implica lo siguiente:

1. Contando el número de códigos de desenredado, es posible calcular la longitud del prólogo y epílogo.

2. Contando el número de instrucciones tras el inicio de un ámbito de epílogo, es posible omitir el número equivalente de códigos de desenredado y ejecutar el resto de una secuencia para completar parcialmente ejecutado que estaba realizando el epílogo de desenredo.

3. Contando el número de instrucciones antes del final del prólogo, es posible omitir el número equivalente de códigos de desenredado y ejecutar el resto de la secuencia para deshacer solo aquellas partes del prólogo cuya ejecución está completa.

Los códigos de desenredado están codificados según la tabla siguiente. Todos los códigos de desenredado son un byte único o doble, excepto el que se asigna una pila enorme. Totalmente hay código de desenredado 21. Cada desenredo de código se asigna exactamente una instrucción en el prólogo y epílogo con el fin de permitir el desenredado de parcialmente ejecutados prólogos y epílogos.

Código de desenredado|Bits y la interpretación
|-|-|
`alloc_s`|000xxxxx: asignar la pila pequeña con tamaño < 512 (2 ^ 5 * 16).
`save_r19r20_x`|    001zzzzz: Guardar \<r19, r 20 > par en [sp-#Z * 8]!, desplazamiento previamente indizada > =-248
`save_fplr`|        01zzzzzz: Guardar \<r29, lr > emparejar en [sp + #Z * 8], desplazamiento < = 504.
`save_fplr_x`|        10zzzzzz: Guardar \<r29, lr > emparejar en [sp-(#Z + 1) * 8]!, desplazamiento previamente indizada > = -512
`alloc_m`|        11000xxx\|xxxxxxxx: asignar la pila de gran tamaño con tamaño < 16 k (2 ^ 11 * 16).
`save_regp`|        110010xx\|xxzzzzzz: guardar r(19+#X) par en [sp + #Z * 8], desplazamiento < = 504
`save_regp_x`|        110011xx\|xxzzzzzz: guardar r(19+#X) par en [sp-(#Z + 1) * 8]!, desplazamiento previamente indizada > = -512
`save_reg`|        110100xx\|xxzzzzzz: guardar r(19+#X) reg en [sp + #Z * 8], desplazamiento < = 504
`save_reg_x`|        x 1101010\|xxxzzzzz: guardar r(19+#X) reg en [sp-(#Z + 1) * 8]!, desplazamiento previamente indizada > =-256.
`save_lrpair`|         x 1101011\|xxzzzzzz: guardar par \<r19 + 2 *#X, lr > en [sp + #Z*8], desplazamiento < = 504
`save_fregp`|        x 1101100\|xxzzzzzz: guardar d(8+#X) par en [sp + #Z * 8], desplazamiento < = 504
`save_fregp_x`|        x 1101101\|xxzzzzzz: guardar d(8+#X) par, en [sp-(#Z + 1) * 8]!, desplazamiento previamente indizada > = -512
`save_freg`|        x 1101110\|xxzzzzzz: guardar d(8+#X) reg en [sp + #Z * 8], desplazamiento < = 504
`save_freg_x`|        11011110\|xxxzzzzz: guardar d(8+#X) reg en [sp-(#Z + 1) * 8]!, desplazamiento previamente indizada > =-256.
`alloc_l`|         11100000\|xxxxxxxx\|xxxxxxxx\|xxxxxxxx: asignar la pila de gran tamaño con tamaño < 256 M (2 ^ 24 * 16)
`set_fp`|        11100001: configurar r29: con: r29 mov, sp
`add_fp`|        11100010\|xxxxxxxx: configurar r29 con: agregar r29, sp, #x * 8
`nop`|            11100011: no hay desenredado se requiere la operación.
`end`|            11100100: final del código de desenredado. Implica ret en epílogo.
`end_c`|        11100101: final del código de desenredado en el actual ámbito encadenada.
`save_next`|        11100110: guardar siguiente Int no volátil o FP registrar par.
`arithmetic(add)`|    11100111\| 000zxxxx: agregar cookie reg(z) a lr (0 = x28, 1 = sp); agregar lr, lr, reg(z)
`arithmetic(sub)`|    11100111\| 001zxxxx: sub reg(z) cookie de lr (0 = x28, 1 = sp); sub lr, lr, reg(z)
`arithmetic(eor)`|    11100111\| 010zxxxx: eor lr con cookie reg(z) (0 = x28, 1 = sp); eor lr, lr, reg(z)
`arithmetic(rol)`|    11100111\| 0110xxxx: rol simulado de lr con cookie reg (x28); xip0 = neg x28; ror lr, xip0
`arithmetic(ror)`|    11100111\| 100zxxxx: ror lr con cookie reg(z) (0 = x28, 1 = sp); ror lr, lr, reg(z)
||            11100111: xxxz---:---reservado
||              11101xxx: reservado para casos de pila personalizados siguientes solo se genera para las rutinas de asm
||              11101001: pila personalizado para MSFT_OP_TRAP_FRAME
||              11101010: pila personalizado para MSFT_OP_MACHINE_FRAME
||              11101011: pila personalizado para MSFT_OP_CONTEXT
||              1111xxxx: reservado

En instrucciones con los valores grandes que ocupan múltiples bytes, los bits más significativos se almacenan en primer lugar. Los códigos de desenredado anteriores están diseñados para que simplemente buscando el primer byte del código, es posible conocer el tamaño total en bytes del código de desenredado. Dado que todos los códigos de desenredado se asignan exactamente a una instrucción de prólogo y epílogo, para calcular el tamaño del prólogo o epílogo, todo lo que debe hacerse es guiarlo desde el principio de la secuencia hasta el final, uso de una tabla de búsqueda o un dispositivo similar para determinar cuánto tiempo el cor es el código de operación responde.

Tenga en cuenta que indizados posteriores al direccionamiento de desplazamiento no se permite en el prólogo. Todos los intervalos de desplazamiento (#Z) coincide con la codificación de direccionamiento STP/STR excepto `save_r19r20_x` en qué 248 es suficiente para todas las áreas (10 registros Int + 8 registros FP + 8 registros de entrada) de guardar.

`save_next` debe seguir un proceso de guardar para Int o volatile FP registrar par: `save_regp`, `save_regp_x`, `save_fregp`, `save_fregp_x`, `save_r19r20_x`, u otro `save_next`. Guarda el siguiente par de registro en la próxima franja de 16 bytes en orden "crecimiento". `save-next` Siga un `save_next` que denota el último par de registro de Int hace referencia al primer par de registro FP.

Dado que el tamaño habituales de devolver y saltar las instrucciones son los mismos, no hay ninguna necesidad de un separados `end` código para escenarios de llamada de cola de desenredado.

`end_c` está diseñado para controlar los fragmentos de función no contiguo con fines de optimización. Un `end_c` que indica el final de los códigos de desenredado en el ámbito actual debe ir seguida de la otra serie de código de desenredado finalizada con un número real `end`. Los códigos de desenredado entre `end_c` y `end` representan las operaciones del prólogo en región primaria (prólogo "fantasma").  En la siguiente sección se describen más detalles y ejemplos.

### <a name="packed-unwind-data"></a>Empaquetan datos de desenredo

Para desenredar funciones empaquetadas cuyo seguimiento de los prólogos y epílogos la forma canónica se describe a continuación, se pueden usar los datos, eliminando la necesidad de un registro .xdata por completo y reduce considerablemente el costo de proporcionar datos de desenredo. El canónicos prólogos y epílogos están diseñados para satisfacer los requisitos comunes de una función simple que no requiere un controlador de excepciones y que lleva a cabo sus operaciones de instalación y desmontaje de forma estándar.

El formato de un registro .pdata con empaquetado desenredar datos este aspecto:

![datos de desenredo de registro .pdata con empaquetado](../build/media/arm64-exception-handling-packed-unwind-data.png "registro .pdata con empaquetado de datos de desenredo")

Los campos son los siguientes:

- **Función iniciar RVA** es la RVA de 32 bits del inicio de la función.
- **Marca** es un campo de 2 bits como se describió anteriormente, con los significados siguientes:
  - 00 = empaquetada desenredar datos no utilizados; Seleccione un registro .xdata, bits restantes a continuación
  - 01 = empaquetada utilizados como se describe a continuación con solo prólogo y epílogo al principio y al final del ámbito de datos de desenredo
  - 10 = empaquetada desenredar datos que se usan como se describe a continuación para código sin prólogo y epílogo; Esto es útil para describir los segmentos separados por función.
  - 11 = reservados;
- **Función longitud** es un campo de 11 bits que proporciona la longitud de toda la función en bytes dividida entre 4. Si la función es mayor que 8 KB, un registro .xdata completo debe usarse en su lugar.
- **Tamaño de la trama** es un campo de 9 bits que indica el número de bytes de la pila asignado a esta función, dividida por 16. Las funciones que asignan mayor de bytes (8k-16) de la pila deben usar un registro .xdata completo. Esto incluye el área de variable local, área de parámetros, el área de Int y FP guardados y y el área de parámetros de inicio de salida, pero sin incluir el área de asignación dinámica.
- **CR** es una marca de 2 bits que indica si la función incluye funciones extra para configurar una cadena de marcos y un vínculo devuelto:
  - 00 = función, \<r29, lr > par no se guarda en la pila.
  - 01 = función, \<lr > se guarda en la pila
  - 10 = reservados;
  - 11 = función encadenada, se usa una instrucción de par de almacén o carga en el prólogo y epílogo \<r29, lr >
- **H** es una marca de 1 bit que indica si la función alberga el parámetro entero registra (r0-r7) almacenándolas del principio de la función. (0 = no alberga registros, 1 = alberga registros).
- **Regis** es un campo de 4 bits que indica el número de registros INT no volátiles (r19-r28) guardado en la ubicación de la pila canónico.
- **RegF** es un campo de 3 bits que indica el número de registros FP no volátiles (d8-d15) guardado en la ubicación de la pila canónico. (0 no = FP se guarda el registro, m > 0: m + 1 registros FP se guardan). Para la función Guardar solo uno, el registro de FP empaquetado de desenredo no se puede aplicar los datos.

Los prólogos canónicos que pertenecen a categorías 1, 2 (sin área de parámetros de salida), 3 y 4 en la sección anterior pueden representarse mediante el formato de desenredado empaquetado.  Los epílogos para las funciones canónicas siguen un formato muy similar, excepción **H** no tiene ningún efecto, el `set_fp` instrucción se omite y se invierte el orden de los pasos, así como instrucciones en cada paso en el epílogo. El algoritmo de empaquetado xdata sigue estos pasos, que se detallan en la tabla siguiente:

Paso 0: Realizar el cálculo previo del tamaño de cada área.

Paso 1: Guardar los registros guardados y Int.

Paso 2: Este paso es específica de tipo 4 en las primeras secciones. LR se guardó al final del área de Int.

Paso 3: Guardar los registros guardados y FP.

Paso 4: Guarde los argumentos de entrada en el área de parámetros de inicio.

Paso 5: Asignar la pila restante, incluido un área local, \<r29, lr > par y el área de parámetros de salida. 5a corresponde al tipo canónico 1. 5b y 5c son para el tipo canónico 2. 5D y 5e son ambos tipos 3 y escriba 4.

Paso #|Valores de marca|número de instrucciones|Código de operación|Código de desenredado
-|-|-|-|-
0|||`#intsz = RegI * 8;`<br/>`if (CR==01) #intsz += 8; // lr`<br/>`#fpsz = RegF * 8;`<br/>`if(RegF) #fpsz += 8;`<br/>`#savsz=((#intsz+#fpsz+8*H)+0xf)&~0xf)`<br/>`#locsz = #famsz - #savsz`|
1|0 < **regis** < = 10|Regis / 2 + **regis** % 2|`stp r19,r20,[sp,#savsz]!`<br/>`stp r21,r22,[sp,16]`<br/>`...`|`save_regp_x`<br/>`save_regp`<br/>`...`
2|**CR**== 01 *|1|`str lr,[sp, #intsz-8]`\*|`save_reg`
3|0 < **RegF** < = 7|(RegF + 1) / 2 +<br/>(RegF + 1) % 2).|`stp d8,d9,[sp, #intsz]`\*\*<br/>`stp d10,d11,[sp, #intsz+16]`<br/>`...`<br/>`str d(8+RegF),[sp, #intsz+#fpsz-8]`|`save_fregp`<br/>`...`<br/>`save_freg`
4|**H** == 1|4|`stp r0,r1,[sp, #intsz+#fpsz]`<br/>`stp r2,r3,[sp, #intsz+#fpsz+16]`<br/>`stp r4,r5,[sp, #intsz+#fpsz+32]`<br/>`stp r6,r7,[sp, #intsz+#fpsz+48]`|`nop`<br/>`nop`<br/>`nop`<br/>`nop`
5a|**CR** == 11 & & #locsz<br/> < = 512|2|`stp r29,lr,[sp,-#locsz]!`<br/>`mov r29,sp`\*\*\*|`save_fplr_x`<br/>`set_fp`
5b|**CR** == 11 &AMP; &AMP;<br/>512 < #locsz < = 4088|3|`sub sp,sp, #locsz`<br/>`stp r29,lr,[sp,0]`<br/>`add r29, sp, 0`|`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5C|**CR** == 11 & & #locsz > 4088|4|`sub sp,sp,4088`<br/>`sub sp,sp, (#locsz-4088)`<br/>`stp r29,lr,[sp,0]`<br/>`add r29, sp, 0`|`alloc_m`<br/>`alloc_s`/`alloc_m`<br/>`save_fplr`<br/>`set_fp`
5D|(**CR** == 00 \| \| **CR**== 01) &AMP; &AMP;<br/>#locsz < = 4088|1|`sub sp,sp, #locsz`|`alloc_s`/`alloc_m`
5e|(**CR** == 00 \| \| **CR**== 01) &AMP; &AMP;<br/>#locsz > 4088|2|`sub sp,sp,4088`<br/>`sub sp,sp, (#locsz-4088)`|`alloc_m`<br/>`alloc_s`/`alloc_m`

\*: If **CR** == 01 y **regis** es un número impar, paso 2 y última save_rep en el paso 1 se combinan en un save_regp.

\*\* Si **regis** == **CR** == 0, y **RegF** ! = 0, el primer stp para el punto flotante no la predecremento.

\*\*\* Ninguna instrucción correspondiente a `mov r29, sp` está presente en el epílogo. Si una función requiere la restauración de sp desde r29, a continuación, no podemos utilizar empaquetan datos de desenredo.

### <a name="unwinding-partial-prologs-and-epilogs"></a>Epílogos y desenredado de prólogos parciales

La situación de desenredado más habitual es uno donde se produjo la excepción o la llamada en el cuerpo de la función fuera del prólogo y todos los epílogos. En esta situación, el desenredo es sencillo: el responsable del desenredado simplemente empieza a ejecutarse los códigos de la matriz de desenredado, empezando en el índice 0 y continuando hasta que se detecte un código de operación de finalización.

Es más difícil de desenredado correctamente en el caso donde se produce una excepción o interrupción mientras se ejecuta un prólogo o epílogo. En estas situaciones, el marco de pila solo parcialmente se construye y el truco consiste en determinar exactamente qué se ha realizado para poder deshacerlo correctamente.

Por ejemplo, siga esta secuencia de prólogo y epílogo:

```asm
0000:    stp    r29, lr, [sp, -256]!        // save_fplr_x  256 (pre-indexed store)
0004:    stp    d8,d9,[sp,224]              // save_fregp 0, 224
0008:    stp    r19,r20,[sp,240]            // save_regp 0, 240
000c:    mov    r29,sp                      // set_fp
         ...
0100:    mov    sp,r29                      // set_fp
0104:    ldp    r19,r20,[sp,240]            // save_regp 0, 240
0108:    ldp    d8,d9,[sp,224]              // save_fregp 0, 224
010c:    ldp    r29, lr, [sp, -256]!        // save_fplr_x  256 (post-indexed load)
0110:    ret     lr                         // end
```

Junto a cada código de operación es el código de desenredado pertinente que describe esta operación. Lo primero que tener en cuenta es que la serie de códigos de desenredado del prólogo es una imagen de espejo idéntica de los códigos de desenredado de epílogo (sin contar la instrucción final del epílogo). Esta es una situación común y, por este motivo, el desenredo de códigos para el prólogo siempre se asume que se almacenan en orden inverso del orden de ejecución del prólogo.

Por lo tanto, para el prólogo y epílogo, seguimos teniendo un conjunto común de códigos de desenredado:

`set_fp`, `save_regp 0,240`, `save_fregp,0,224`, `save_fplr_x_256`, `end`

Comenzando por el caso de epílogo (mucho más sencillo porque está en orden normal), en el desplazamiento 0 en el epílogo (que comienza en el desplazamiento 0 x 100 en la función), se esperaría ejecutar la secuencia de desenredado completa, tal y como no se ha realizado aún ninguna limpieza. Si nos vemos una instrucción en (en desplazamiento 2 en el epílogo), nos podemos desenredado correctamente omitiendo el primer código de desenredado. Generalizar esta situación, suponiendo una asignación 1:1 entre los códigos de operación y códigos de desenredado, nos podemos indicar que, si nos estamos desenredamos desde n instrucción en el epílogo, nos debemos omitir los primeros códigos de desenredado n y comenzar a ejecutar desde allí.

Resulta que una lógica similar funciona para el tipo de prólogo, excepto en orden inverso. Si nos estamos desenreda desde el desplazamiento 0 en el prólogo, querríamos ejecutar nada. Si se desenreda del desplazamiento de 2, que es una instrucción y, después, queremos empezar a ejecutar el código de desenredado una secuencia de desenredado del final (Recuerde que los códigos se almacenan en orden inverso). Y aquí también se puede generalizar que si nos estamos desenredamos desde n instrucción en el prólogo, podremos empezar a ejecutar códigos de desenredado n desde el final de la lista de códigos.

Ahora, no siempre es el caso de que los códigos de prólogo y epílogo coinciden exactamente. Por este motivo, la matriz de desenredado que deba contener varias secuencias de códigos. Para determinar el desplazamiento de dónde empezar a procesar códigos, utilice la siguiente lógica:

1. Si desenreda desde el cuerpo de la función, simplemente se empiezan a ejecutar códigos de desenredado en el índice 0 y continúe hasta dar con un código de operación "end".

2. Si desenreda desde un epílogo, utilice el índice de inicio de epílogo específico proporcionado con el ámbito de epílogo como punto de partida. Calcule cuántos bytes del PC en cuestión es desde el inicio del epílogo. A continuación, avance hacia delante a través de los códigos de desenredado, omitiendo los códigos de desenredado hasta que todas las instrucciones ejecutadas ya se tienen en cuenta. A continuación, ejecute empezando en ese momento.

3. Si desenreda desde el prólogo, utilice el índice 0 como punto de partida. Calcular la longitud del código de prólogo de la secuencia y, a continuación, calcula el número de bytes del PC en cuestión está en el extremo del prólogo. A continuación, avance hacia delante a través de los códigos de desenredado, omitiendo los códigos de desenredado hasta que se tienen en cuenta todas las instrucciones todavía ejecuta para. A continuación, ejecute empezando en ese momento.

Como resultado de estas reglas, los códigos de desenredado del prólogo siempre deben ser el primer elemento de la matriz, y también son los códigos de desenredado en general el caso de desenredado desde dentro del cuerpo. Las secuencias de código específico de epílogo deben seguir inmediatamente después.

### <a name="function-fragments"></a>Fragmentos de función

Para fines de optimización de código y otras razones, puede ser preferible para dividir una función en fragmentos separados (también denominadas regiones). Cuando esto sucede, cada fragmento de la función resultante requiere su propio registro .pdata (y posiblemente XData) registro.

Para separados fragmento secundaria que tiene su propio prólogo, se espera que no se realiza ningún ajuste de pila en el prólogo. Todo espacio requerido por la base de datos secundaria de la pila regiones se deben asignar previamente por su región primaria (o región llamado host). Esto mantiene la manipulación de puntero de pila estrictamente en el prólogo original de la función.

Un caso típico de fragmentos de función es "separación de código" con la que el compilador puede mover una región de código fuera de su función de host. Existen tres casos inusuales que podrían ser dan como resultados mediante la separación de código.

#### <a name="example"></a>Ejemplo:

- (la región 1: iniciar)

    ```asm
        stp     r29, lr, [sp, -256]!    // save_fplr_x  256 (pre-indexed store)
        stp     r19,r20,[sp,240]        // save_regp 0, 240
        mov     r29,sp                  // set_fp
        ...
    ```

- (la región 1: final)
- (3 de la región: empezar)

    ```asm
        ...
    ```

- (3 de la región: final)
- (la región 2: empezar)

    ```asm
    ...
        mov     sp,r29                  // set_fp
        ldp     r19,r20,[sp,240]        // save_regp 0, 240
        ldp     r29, lr, [sp, -256]!    // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (la región 2: final)

1. Solo prólogo (zona 1: todos los epílogos están en regiones separadas):

   Solo el prólogo debe describirse. Esto no puede representarse mediante el formato de .pdata compacto. En el caso de .xdata completo, esto puede representarse mediante el establecimiento de epílogo recuento = 0. Vea la región 1 en el ejemplo anterior.

   Códigos de desenredado: `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`.

2. Solo epílogos (zona 2: prólogo se encuentra en la región de host)

   Se supone que el control de tiempo que saltar en esta región, se han ejecutado todos los códigos de prólogo. Desenredo parcial puede producirse en epílogos la misma forma que una función normal. Este tipo de región no puede representarse mediante .pdata compacto. En el registro de xdata completa, puede estar codificado con un "fantasma" prólogo, enmarcado por un `end_c` y `end` par de código de desenredado.  El interlineado `end_c` indica el tamaño del prólogo es cero. Epílogo el índice inicial de los puntos de único epílogo a `set_fp`.

   Código de región 2 de desenredado: `end_c`, `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`.

3. Sin prólogos ni epílogos (región de 3: los prólogos y epílogos todas están en otros fragmentos):

   Formato de .pdata compacto puede aplicarse a través de indicador = 10. Con un registro .xdata completo, el recuento de epílogo = 1. Desenredo código es el mismo que para la región 2 anterior, pero el índice de inicio de epílogo también apunta a `end_c`. No se producirán desenredo parcial en esta región de código.

Otro caso más complicado de fragmentos de función es "reducir el ajuste" con la que el compilador puede optar por guardar algunos registros guardados por destinatarios hasta que se encuentra fuera del prólogo de función de entrada de retraso.

- (la región 1: iniciar)

    ```asm
        stp     r29, lr, [sp, -256]!    // save_fplr_x  256 (pre-indexed store)
        stp     r19,r20,[sp,240]        // save_regp 0, 240
        mov     r29,sp                  // set_fp
        ...
    ```

- (la región 2: empezar)

    ```asm
        stp     r21,r22,[sp,224]        // save_regp 2, 224
        ...
        ldp     r21,r22,[sp,224]        // save_regp 2, 224
    ```

- (la región 2: final)

    ```asm
        ...
        mov     sp,r29                  // set_fp
        ldp     r19,r20,[sp,240]        // save_regp 0, 240
        ldp     r29, lr, [sp, -256]!    // save_fplr_x  256 (post-indexed load)
        ret     lr                      // end
    ```

- (la región 1: final)

En el prólogo de la región 1, el espacio de pila está preasignado. Tenga en cuenta que esa región 2 tendrán el mismo código de desenredado incluso se mueve fuera de su función de host.

1 región: `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end` con el índice de inicio de epílogo señala a `set_fp` como de costumbre.

Zona 2: `save_regp 2, 224`, `end_c`, `set_fp`, `save_regp 0,240`, `save_fplr_x_256`, `end`. Índice inicial de epílogo señala para código de desenredado primero `save_regp 2, 224`.

### <a name="large-functions"></a>Funciones grandes

Fragmentos se pueden aprovechar para describir funciones con un tamaño superior al límite de 1 millón impuesto por los campos de bits en el encabezado de xdata. Para describir una función muy grande como esta, simplemente debe dividirse en fragmentos más pequeños de 1 000 000. Cada fragmento se debe ajustar para que no divida un epílogo en varias partes.

Solo el primer fragmento de la función va a contener un prólogo; todos los demás están marcados como si tuviera ningún prólogo. Dependiendo del número de epílogos está presente, cada fragmento puede contener cero o más epílogos. Tenga en cuenta que cada ámbito de epílogo en un fragmento especifica su desplazamiento inicial en relación con el inicio del fragmento, no al inicio de la función.

Si un fragmento no tiene ningún tipo de prólogo y ningún epílogo, todavía requiere su propio registro .pdata (y posiblemente XData) registro, para describir cómo desenredar desde dentro del cuerpo de la función.

## <a name="examples"></a>Ejemplos

### <a name="example-1-frame-chained-compact-form"></a>Ejemplo 1: Encadenados de marco, compact-formulario

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

### <a name="example-2-frame-chained-full-form-with-mirror-prolog--epilog"></a>Ejemplo 2: Encadenados de marco, formato completo con reflejo prólogo y epílogo

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

Tenga en cuenta que EpilogStart índice [0] señala a la misma secuencia de código de desenredado del prólogo.

### <a name="example-3-variadic-unchained-function"></a>Ejemplo 3: Variádica (función)

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

Nota: EpilogStart índice [4] apunta a la mitad del código de desenredado del prólogo (parcialmente reutilización desenredo de la matriz).

## <a name="see-also"></a>Vea también

[Información general sobre las convenciones ABI ARM64](arm64-windows-abi-conventions.md)<br/>
[Control de excepciones de ARM](../build/arm-exception-handling.md)
