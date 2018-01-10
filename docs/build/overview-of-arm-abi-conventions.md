---
title: "Información general sobre las convenciones ABI de ARM | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 23f4ae8c-3148-4657-8c47-e933a9f387de
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 073fe113c1915913d06a63c7feabcb7808896188
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-arm-abi-conventions"></a>Información general de las convenciones ABI de ARM
La interfaz binaria de aplicaciones (ABI) para código compilado para Windows en procesadores de ARM se basa en la norma EABI de ARM. En este artículo se desgranan las principales diferencias entre Windows en ARM y la norma. Para obtener más información acerca de la norma EABI de ARM, vea [interfaz binaria de aplicaciones (ABI) de la arquitectura ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html).  
  
## <a name="base-requirements"></a>Requisitos básicos  
 Se da por hecho que Windows en ARM se ejecuta en todo momento en una arquitectura ARMv7. El hardware debe disponer de compatibilidad con punto flotante con el formato de VFPv3-D32 o posterior. El VFP debe admitir puntos flotantes de precisión sencilla y precisión doble en el hardware. Windows en tiempo de ejecución no admite la emulación de puntos flotantes para permitir la ejecución en un hardware distinto de VFP.  
  
 El hardware también debe contar con compatibilidad con Extensiones SIMD avanzadas (NEON), lo que engloba operaciones tanto de entero como de punto flotante. No se proporciona compatibilidad en tiempo de ejecución para la emulación.  
  
 La compatibilidad con la división de enteros (UDIV/SDIV) es enormemente recomendable, si bien no es obligatoria. Las plataformas que carezcan de compatibilidad con la división de enteros podrían sufrir una pérdida de rendimiento, dado que estas operaciones se deben interceptar y, muy probablemente, revisar.  
  
## <a name="endianness"></a>Modos endian  
 Windows en ARM se ejecuta en modo little-endian. Tanto el compilador de Visual C++ como Windows en tiempo de ejecución esperan que haya datos little-endian en todo momento. La instrucción SETEND de la arquitectura de conjunto de instrucciones de ARM (ISA) permite incluso que el código de modo de usuario cambie el modo endian actual, pero esto no es aconsejable porque es peligroso para una aplicación. Si se generara una excepción en modo big-endian, el comportamiento sería imprevisible y podría provocar un error de la aplicación en modo de usuario o una comprobación de errores en modo kernel.  
  
## <a name="alignment"></a>Alineación  
 Aunque Windows permite que el hardware de ARM administre de forma transparente los accesos de entero mal alineados, en algunas situaciones todavía podrían producirse errores de alineación. Siga estas reglas de alineación:  
  
-   No es necesario que las cargas y almacenes de enteros con tamaño de media palabra (16 bits) y de palabra completa (32 bits) estén alineados. El hardware se encarga de administrarlos de forma eficaz y transparente.  
  
-   Las cargas y almacenes de puntos flotantes sí deben estar alineados. El kernel administra las cargas y almacenes sin alinear con transparencia, pero esto conlleva una sobrecarga considerable.  
  
-   Las operaciones de carga o almacenamiento doble (LDRD/STRD) y múltiple (LDM/STM) deben estar alineadas. El kernel administra la mayor parte de ellas con transparencia, pero esto conlleva una sobrecarga considerable.  
  
-   Todos los accesos a memoria no almacenados en caché deben estar alineados, incluso los accesos de entero. Los accesos no alineados pueden provocar errores de alineación.  
  
## <a name="instruction-set"></a>Conjunto de instrucciones  
 El conjunto de instrucciones para Windows en ARM está limitado estrictamente a Thumb-2. Se espera que todo el código que se ejecute en esta plataforma se inicie y permanezca siempre en modo Thumb. Un intento de cambiar al conjunto de instrucciones de ARM heredado podría realizarse correctamente, pero, de suceder, se podrían generar excepciones o interrupciones que desemboquen en un error de la aplicación en modo de usuario o en una comprobación de errores en modo kernel.  
  
 Un efecto secundario de este requisito es que todos los punteros de código deben tener el conjunto de bits de orden inferior. Esto se debe a que, cuando se cargan y bifurcan mediante BLX o BX, el procesador seguirá en modo Thumb, de modo que no tratará de ejecutar el código de destino como instrucciones de ARM de 32 bits.  
  
### <a name="it-instructions"></a>Instrucciones IT  
 No se pueden usar instrucciones IT en código Thumb-2, salvo en los siguientes casos concretos:  
  
-   La instrucción IT solo se puede usar para modificar una instrucción de destino.  
  
-   La instrucción de destino debe ser una instrucción de 16 bits.  
  
-   La instrucción de destino debe ser una de las siguientes:  
  
    |Códigos de operación de 16 bits|Clase|Restricciones|  
    |---------------------|-----------|------------------|  
    |MOV, MVN|Mover|Rm != PC, Rd != PC|  
    |LDR, LDR[S]B, LDR[S]H|Cargar desde memoria|Pero no formatos de literal LDR|  
    |STR, STRB, STRH|Almacenar en memoria||  
    |ADD, ADC, RSB, SBC, SUB|Sumar o restar|Pero no los formatos ADD/SUB SP, SP, imm7<br /><br /> Rm != PC, Rdn != PC, Rdm != PC|  
    |CMP, CMN|Comparar|Rm != PC, Rn != PC|  
    |MUL|Multiplicar||  
    |ASR, LSL, LSR, ROR|Desplazamiento bit a bit||  
    |AND, BIC, EOR, ORR, TST|Aritmética bit a bit||  
    |BX|Bifurcación que registrar|Rm != PC|  
  
 Aunque las CPU ARMv7 actuales no pueden informar del uso de formatos de instrucción no permitidos, está previsto que sí lo hagan en las próximas versiones. Si estos formatos se detectan, cualquier programa que los use podría finalizar con una excepción de instrucción no definida.  
  
### <a name="sdivudiv-instructions"></a>Instrucciones SDIV/UDIV  
 El uso de instrucciones de división de entero SDIV y UDIV es totalmente apto, incluso en plataformas que carezcan de hardware nativo para administrarlas. La sobrecarga por división SDIV o UDIV en un procesador Cortex-A9 es de 80 ciclos aproximadamente, además del tiempo de división extra de 20-250 ciclos, según las entradas.  
  
## <a name="integer-registers"></a>Registros de enteros  
 El procesador de ARM admite 16 registros de enteros:  
  
|Registro|¿Volátil?|Rol|  
|--------------|---------------|----------|  
|r0|Volátil|Parámetro, resultado, registro residual 1|  
|r1|Volátil|Parámetro, resultado, registro residual 2|  
|r2|Volátil|Parámetro, registro residual 3|  
|r3|Volátil|Parámetro, registro residual 4|  
|r4|No volátil||  
|r5|No volátil||  
|r6|No volátil||  
|r7|No volátil||  
|r8|No volátil||  
|r9|No volátil||  
|r10|No volátil||  
|r11|No volátil|Puntero de marco|  
|r12|Volátil|Registro residual de llamada dentro del procedimiento|  
|r13 (SP)|No volátil|Puntero de pila|  
|r14 (LR)|No volátil|Registro de vínculo|  
|r15 (PC)|No volátil|Contador de programas|  
  
 Para obtener detalles sobre el uso de los registros de parámetro y valor devuelto, vea la sección Paso de parámetros de este artículo.  
  
 Windows usa r11 para el recorrido rápido del marco de pila. Para más información, vea la sección Recorrido de la pila. Debido a este requisito, r11 debe apuntar siempre al vínculo superior de la cadena. No use r11 con fines generales, ya que el código no generará los recorridos de pila adecuados durante el análisis.  
  
## <a name="vfp-registers"></a>Registros de VFP  
 Windows admite únicamente variantes de ARM que tengan compatibilidad con coprocesadores VFPv3-D32. Esto quiere decir que siempre hay registros de punto flotante en los que poder basarse para pasar parámetros y, asimismo, que el conjunto completo de 32 registros estará siempre disponible para usarse. En esta tabla se resumen los registros de VFP y su uso:  
  
|Sencillos|Dobles|Cuádruples|¿Volátil?|Rol|  
|-------------|-------------|-----------|---------------|----------|  
|s0-s3|d0-d1|q0|Volátil|Parámetros, resultado, registro residual|  
|s4-s7|d2-d3|q1|Volátil|Parámetros, registro residual|  
|s8-s11|d4-d5|q2|Volátil|Parámetros, registro residual|  
|s12-s15|d6-d7|q3|Volátil|Parámetros, registro residual|  
|s16-s19|d8-d9|q4|No volátil||  
|s20-s23|d10-d11|q5|No volátil||  
|s24-s27|d12-d13|q6|No volátil||  
|s28-s31|d14-d15|q7|No volátil||  
||d16-d31|q8-q15|Volátil||  
  
 En la siguiente tabla se reflejan los campos de bits de estado de punto flotante y registro de control (FPSCR):  
  
|Bits|Significado|¿Volátil?|Rol|  
|----------|-------------|---------------|----------|  
|31-28|NZCV|Volátil|Marcas de estado|  
|27|QC|Volátil|Saturación acumulativa|  
|26|AHP|No volátil|Control de media precisión alternativo|  
|25|DN|No volátil|Control de modo de NaN predeterminado|  
|24|FZ|No volátil|Control de modo de volcado a cero|  
|23-22|RMode|No volátil|Control de modo de redondeo|  
|21-20|Intervalo|No volátil|Intervalo de vector, debe ser siempre 0|  
|18-16|Len|No volátil|Longitud del vector, debe ser siempre 0|  
|15, 12-8|IDE, IXE, etc.|No volátil|Bits de activación de intercepción de excepciones, debe ser siempre 0|  
|7, 4-0|IDC, IXC, etc.|Volátil|Marcas de excepción acumulativa|  
  
## <a name="floating-point-exceptions"></a>Excepciones de punto flotante  
 La mayoría del hardware de ARM no admite excepciones de punto flotante de IEEE. En las variantes de procesador que tengan excepciones de punto flotante de hardware, el kernel de Windows almacena las excepciones en caché de manera silenciosa y las deshabilita implícitamente en el registro FPSCR. De este modo, se garantiza un comportamiento normalizado en todas las variantes de procesador. Si no, el código desarrollado en una plataforma que no admite excepciones podría recibir excepciones inesperadas al ejecutarse en una plataforma con compatibilidad con excepciones.  
  
## <a name="parameter-passing"></a>Paso de parámetros  
 En las funciones no variádicas, la ABI de Windows en ARM sigue las reglas de ARM para el paso de parámetros (lo que engloba las extensiones VFP y SIMD avanzadas). Estas reglas siguen la [estándar de llamadas de procedimiento de la arquitectura ARM](http://infocenter.arm.com/help/topic/com.arm.doc.ihi0042c/IHI0042C_aapcs.pdf), consolidada con las extensiones VFP. De forma predeterminada, se pasan en los registros los primeros cuatro argumentos de entero y hasta ocho argumentos de punto flotante o de vector; los argumentos adicionales se pasan en la pila. Se usa el siguiente procedimiento para asignar argumentos a los registros o a la pila:  
  
### <a name="stage-ainitialization"></a>Fase A: inicialización  
 La inicialización se lleva a cabo exactamente una vez, antes de que comience el procesamiento de argumentos:  
  
1.  El siguiente número de registro principal (NCRN) se establece en r0.  
  
2.  Los registros de VFP se marcan como sin asignar.  
  
3.  La siguiente dirección de argumento apilado (NSAA) se establece en el SP actual.  
  
4.  Si se llama a una función que devuelve un resultado en la memoria, la dirección de ese resultado se sitúa en r0 y el NCRN se establece en r1.  
  
### <a name="stage-bpre-padding-and-extension-of-arguments"></a>Fase B: relleno previo y extensión de argumentos  
 En cada argumento de la lista se aplica la primera regla que coincida de la siguiente lista:  
  
1.  Si el argumento es un tipo compuesto cuyo tamaño no pueden averiguar estáticamente ni el llamador ni el destinatario de la llamada, el argumento se copia en la memoria y se reemplaza por un puntero en dicha copia.  
  
2.  Si el argumento es un byte o media palabra de 16 bits, se completa con ceros o con signos hasta llegar a una palabra completa de 32 bits y se trata como un argumento de 4 bytes.  
  
3.  Si el argumento es un tipo compuesto, su tamaño se redondea al múltiplo más próximo de 4.  
  
### <a name="stage-cassignment-of-arguments-to-registers-and-stack"></a>Fase C: asignación de argumentos a registros y la pila  
 En cada uno de los argumentos de la lista se aplican las siguientes reglas cada vez, hasta que los argumentos se hayan asignado:  
  
1.  Si el argumento es de tipo VFP y existen suficientes registros de VFP sin asignar consecutivos del tipo adecuado, dicho argumento se asigna a la secuencia con el número más bajo de esos registros.  
  
2.  Si el argumento es de tipo VFP, todos los demás registros sin asignar se marcan como no disponibles. La NSAA se ajusta hacia arriba hasta estar alineada correctamente para el tipo de argumento, y el argumento se copia en la pila, en la NSAA ajustada. Una vez hecho esto, la NSAA se incrementará en función del tamaño del argumento.  
  
3.  Si el argumento requiere una alineación de 8 bytes, el NCRN se redondea al siguiente número de registro par más alto.  
  
4.  Si el tamaño del argumento en palabras de 32 bits no es mayor que r4 menos NCRN, el argumento se copia en los registros principales, empezando por el NCRN, de manera que los bits menos significativos ocupan los registros con los números más bajos. El NCRN se incrementará en función del número de registros empleado.  
  
5.  Si el NCRN es menor que r4 y la NSAA equivale al SP, el argumento se divide entre los registros principales y la pila. La primera parte del argumento se copia en los registros principales, empezando por el NCRN, hasta llegar a r3 (inclusive). El resto del argumento se copia en la pila, empezando por la NSAA. El NCRN se establece en r4 y la NSAA se incrementa según el tamaño del argumento menos la cantidad pasada en los registros.  
  
6.  Si el argumento requiere una alineación de 8 bytes, la NSAA se redondea a la siguiente dirección alineada de 8 bytes.  
  
7.  El argumento se copia en la memoria, en la NSAA. La NSAA se incrementará en función del tamaño del argumento.  
  
 Los registros de VFP no se usan en las funciones variádicas, y las reglas 1 y 2 de la fase C se omiten. Esto significa que una función variádica puede comenzar por una inserción opcional {r0-r3} para anteponer los argumentos de registro a cualquier otro argumento adicional que el llamador haya pasado y, luego, acceder a la lista de argumentos completa directamente desde la pila.  
  
 Los valores de tipo de entero se devuelven en r0 (esto se extiende opcionalmente a r1 en el caso de los valores devueltos de 64 bits). Los valores de tipo SIMD o punto flotante VFP/NEON se devuelven en s0, d0 o q0, según corresponda.  
  
## <a name="stack"></a>Pila  
 La pila debe tener una alineación de 4 bytes en todo momento, y de 8 bytes en cualquier límite de función. Esto es necesario para dar cabida al uso frecuente de operaciones de interbloqueo en las variables de pila de 64 bits. La EABI de ARM indica que la pila tiene una alineación de 8 bytes en cualquier interfaz pública. Por motivos de coherencia, la ABI de Windows en ARM trata a cualquier límite de función como una interfaz pública.  
  
 Las funciones que deban usar un puntero de marco (por ejemplo, aquellas funciones que llaman a `alloca` o que modifican el puntero de la pila dinámicamente) deben establecer el puntero de marco en r11 en el prólogo de la función, y dejarlo tal cual hasta el epílogo. Las funciones que no requieran un puntero de marco deben realizar todas las actualizaciones de pila en el prólogo y dejar el puntero de pila tal cual hasta el epílogo.  
  
 Las funciones que asignan 4 KB o más en la pila deben garantizar que todas las páginas previas a la página final se tocan en orden. Con esto se consigue que ningún código pueda “saltarse” las páginas de protección que Windows usa para expandir la pila. De esto se suele encargar la función auxiliar `__chkstk`, a la que se pasa la asignación de pila total en bytes dividida entre 4 en r4 y que, luego, devuelve la asignación de pila final en bytes de nuevo en r4.  
  
### <a name="red-zone"></a>Zona roja  
 El área de 8 bytes inmediatamente debajo del puntero de pila actual está reservada para tareas de análisis y revisión dinámica. Esto permite que se pueda insertar código generado con cuidado, donde se almacenan 2 registros en [sp, #-8], que usa temporalmente con fines arbitrarios. El kernel de Windows garantiza que esos 8 bytes no se van a sobrescribir si se produce una excepción o interrupción, ya sea en el modo de usuario o kernel.  
  
### <a name="kernel-stack"></a>Pila de kernel  
 La pila en modo kernel predeterminada en Windows consta de tres páginas (12 KB). Procure no crear funciones que tienen búferes de pila de gran tamaño en el modo kernel. Podría tener lugar una interrupción con muy poca capacidad de aumento de la pila y provocar una comprobación de errores de pánico de la pila.  
  
## <a name="cc-specifics"></a>Conceptos específicos de C/C++  
 Las enumeraciones son tipos de enteros de 32 bits, salvo que al menos un valor de la enumeración requiera almacenamiento de palabras dobles de 64 bits. En tal caso, la enumeración se promueve a tipo de entero de 64 bits.  
  
 `wchar_t` se define como equivalente a `unsigned short` para mantener la compatibilidad con otras plataformas.  
  
## <a name="stack-walking"></a>Recorrido de la pila  
 Código de Windows se compila con punteros de marco habilitados ([/Oy (omisión de puntero de marco)](../build/reference/oy-frame-pointer-omission.md)) para habilitar el recorrido de pila rápidos. Por lo general, el registro r11 apunta al siguiente vínculo de la cadena, que es un par {r11, lr} que especifica el puntero al marco anterior en la pila, así como la dirección de devolución. Le recomendamos que su código tenga habilitados también los punteros de marco, ya que así mejorarán los perfiles y seguimientos.  
  
## <a name="exception-unwinding"></a>Desenredado en excepciones  
 El desenredado de la pila durante el control de excepciones es posible mediante el uso de códigos de desenredado. Los códigos de desenredado son una secuencia de bytes almacenada en la sección .xdata de la imagen ejecutable. Describen la operación del código de prólogo y epílogo de la función de forma abstracta, ya que así los efectos del prólogo de una función se pueden deshacer como preparación para desenredar en el marco de pila del llamador.  
  
 La EABI de ARM especifica un modelo de desenredado en excepciones en el que se usan códigos de desenredado. Sin embargo, esta especificación no basta para el desenredado en Windows, donde se deben controlar casos en los que el procesador se encuentra en medio del prólogo y el epílogo de una función. Para obtener más información acerca de las ventanas de datos de la excepción de ARM y desenredo de, consulte [control de excepciones de ARM](../build/arm-exception-handling.md).  
  
 Es recomendable que el código generado dinámicamente se describa por medio de tablas de funciones dinámicas especificadas en llamadas a `RtlAddFunctionTable` y funciones asociadas, ya que así el código generado podrá participar en el tratamiento de excepciones.  
  
## <a name="cycle-counter"></a>Contador de ciclos  
 Para poder usar un contador de ciclos, se necesitan procesadores de ARM en los que se ejecute Windows, si bien el uso directo del contador podría provocar problemas. Para que esto no suceda, Windows en ARM usa un código de operación sin definir con el que solicita un valor de contador de ciclos de 64 bits normalizado. Desde C o C++, use la función intrínseca `__rdpmccntr64` para emitir el código de operación adecuado; desde el ensamblado, use la instrucción `__rdpmccntr64`. La lectura del contador de ciclos conlleva alrededor de 60 ciclos en un Cortex-A9.  
  
 El contador es un contador de ciclos auténtico, no un reloj; por lo tanto, la frecuencia de recuento varía según la frecuencia del procesador. Si quiere medir el tiempo de reloj transcurrido, use `QueryPerformanceCounter`.  
  
## <a name="see-also"></a>Vea también  
 [Problemas comunes de migración de ARM de Visual C++](../build/common-visual-cpp-arm-migration-issues.md)   
 [Control de excepciones de ARM](../build/arm-exception-handling.md)