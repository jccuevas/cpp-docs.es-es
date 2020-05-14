---
title: Información general sobre las convenciones ABI de ARM64
ms.date: 03/27/2019
ms.openlocfilehash: 07d58bbd64795235ad63a7b26b6f18fcffdcd1d2
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303269"
---
# <a name="overview-of-arm64-abi-conventions"></a>Información general sobre las convenciones ABI de ARM64

La interfaz binaria de aplicación (ABI) básica para Windows cuando se compila y se ejecuta en procesadores ARM en el modo de 64 bits (ARMv8 o arquitecturas posteriores), en la mayoría de los casos, sigue el estándar AArch64 EABI de ARM. En este artículo se resaltan algunas de las suposiciones clave y los cambios que se documentan en la EABI. Para obtener información sobre la ABI de 32 bits, Vea [Información general de las convenciones ABI de ARM](overview-of-arm-abi-conventions.md). Para obtener más información sobre la EABI de ARM estándar, vea [Interfaz binaria de aplicaciones (ABI) para la arquitectura ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html) (vínculo externo).

## <a name="definitions"></a>Definiciones

Con la introducción de la compatibilidad con la programación de 64 bits, ARM ha definido varios términos:

- **AArch32**: arquitectura de conjunto de instrucciones (ISA) de 32 bits heredada que define ARM, incluida la ejecución en modo Thumb.
- **AArch64**: arquitectura de conjunto de instrucciones (ISA) nueva de 64 bits que define ARM.
- **ARMv7**: especificación del hardware ARM de "séptima generación", que solo incluye compatibilidad con AArch32. Esta versión del hardware de ARM es la primera versión de Windows para ARM compatible.
- **ARMv8**: especificación del hardware de ARM de "octava generación", que incluye compatibilidad con AArch32 y AArch64.

Windows también usa estos términos:

- **ARM**: hace referencia a la arquitectura ARM de 32 bits (AArch32), que a veces se conoce como WoA (Windows en ARM).
- **ARM32**: igual que el término ARM; se usa en este documento para mayor claridad.
- **ARM64**: hace referencia a la arquitectura ARM de 64 bits (AArch64). No existe nada como WoA64.

Por último, cuando se hace referencia a los tipos de datos, se mencionan las definiciones siguientes de ARM:

- **Vector corto**: un tipo de datos que se representa directamente en SIMD, un vector de 8 bytes o un valor de 16 bytes de elementos. Está alineado con su tamaño, 8 bytes o 16 bytes, donde cada elemento puede ser 1, 2, 4 u 8 bytes.
- **HFA (agregado de punto flotante homogéneo)** : un tipo de datos que incluye de 2 a 4 miembros de puntos flotantes idénticos, ya sean flotantes o dobles.
- **HVA (agregado de vector corto homogéneos)** : un tipo de datos que incluye de 2 a 4 miembros de vectores cortos idénticos.

## <a name="base-requirements"></a>Requisitos básicos

La versión ARM64 de Windows presupone que se ejecuta en una arquitectura ARMv8, o posterior, en todo momento. Se supone que la compatibilidad con el punto flotante y NEON está presente en el hardware.

La especificación ARMv8 describe los códigos de operación nuevos y opcionales del asistente de criptografía y de CRC para AArch32 y AArch64. Actualmente, la compatibilidad con estos es opcional, pero recomendable. A fin de sacar partido de estos códigos de operación, en primer lugar las aplicaciones deben realizar comprobaciones en tiempo de ejecución para probar su existencia.

## <a name="endianness"></a>Modos endian

Al igual que con la versión ARM32 de Windows, en ARM64 Windows se ejecuta en modo little-endian. Cambiar modos endian es difícil de lograr sin la compatibilidad con el modo kernel en AArch64, por lo que es más fácil de aplicar.

## <a name="alignment"></a>Alineación

Cuando Windows se ejecuta en ARM64, permite que el hardware de la CPU controle los accesos desalineados de forma transparente. En una mejora de AArch32, esta compatibilidad ahora también funciona para todos los accesos de enteros (incluidos los accesos de varias palabras) y para los accesos de punto flotante.

Sin embargo, los accesos a la memoria no almacenada en caché (dispositivo) todavía deben estar alineados. Si es posible que el código pueda leer o escribir datos desalineados de la memoria no almacenada en caché, debe asegurarse de alinear todos los accesos.

Alineación de diseño predeterminada para variables locales:

| Tamaño en bytes | Alineación en bytes |
| - | - |
| 1 | 1 |
| 2 | 2 |
| 3, 4 | 4 |
| > 4 | 8 |

Alineación de diseño predeterminada para las variables globales y estáticas:

| Tamaño en bytes | Alineación en bytes |
| - | - |
| 1 | 1 |
| 2 - 7 | 4 |
| 8 - 63 | 8 |
| >= 64 | 16 |

## <a name="integer-registers"></a>Registros de enteros

La arquitectura AArch64 admite registros enteros de 32:

| Registro | ¿Volátil? | Rol |
| - | - | - |
| x0 | Volátil | Parámetro/registro residual 1, registro de resultados |
| x1-x7 | Volátil | Parámetro/registro residual 2-8 |
| x8-x15 | Volátil | Registros residuales |
| x16-x17 | Volátil | Registros residuales de llamada dentro del procedimiento |
| x18 | No volátil | Registro de plataforma: en modo kernel, apunta a KPCR para el procesador actual; en modo de usuario, apunta a TEB |
| x19-x28 | No volátil | Registros residuales |
| x29/fp | No volátil | Puntero de marco |
| x30/lr | No volátil | Vinculación de registros |

Se puede acceder a cada registro como un valor completo de 64 bits (a través de x0-x30) o como un valor de 32 bits (a través de w0-w30). Las operaciones de 32 bits extienden a cero sus resultados hasta 64 bits.

Vea la sección Paso de parámetros para obtener información detallada sobre el uso de los registros de parámetros.

A diferencia de AArch32, el contador de programas (PC) y el puntero de pila (SP) no son registros indexados. Están limitados en cómo se puede acceder a ellos. Tenga en cuenta también que no hay ningún registro x31. Esa codificación se usa para fines especiales.

El puntero de marco (x29) es necesario para la compatibilidad con el recorrido rápido de la pila que usan ETW y otros servicios. Debe apuntar al par anterior {x29, x30} en la pila.

## <a name="floating-pointsimd-registers"></a>Registros de punto flotante/SIMD

La arquitectura AArch64 también admite registros de punto flotante/SIMD de 32, que se resumen a continuación:

| Registro | ¿Volátil? | Rol |
| - | - | - |
| v0 | Volátil | Parámetro/registro residual 1, registro de resultados |
| v1-v7 | Volátil | Parámetro/registro residual 2-8 |
| v8-v15 | No volátil | Registros residuales (solo los 64 bits inferiores son no volátiles) |
| v16-v31 | Volátil | Registros residuales |

Se puede acceder a cada registro como un valor completo de 128 bits (a través de v0-v31 o q0-q31). Se puede acceder a él como un valor de 64 bits (a través de d0-d31), como un valor de 32 bits (a través de s0-s31), como un valor de 16 bits (a través de hH0-h31) o como un valor de 8 bits (a través de b0-b31). Los accesos menores de 128 bits solo tienen acceso a los bits inferiores del registro completo de 128 bits. Los bits restantes se dejan sin tocar a menos que se especifique lo contrario. (AArch64 es diferente de AArch32, donde los registros más pequeños se han empaquetado encima de los registros más grandes).

El registro de control de punto flotante (FPCR) tiene ciertos requisitos en los distintos campos de bits que contiene:

| Bits | Significado | ¿Volátil? | Rol |
| - | - | - | - |
| 26 | AHP | No volátil | Control de media precisión alternativo. |
| 25 | DN | No volátil | Control de modo de NaN predeterminado. |
| 24 | FZ | No volátil | Control de modo de vaciado a cero. |
| 23-22 | RMode | No volátil | Control de modo de redondeo. |
| 15,12-8 | IDE/IXE/etc | No volátil | Bits de activación de captura de excepciones, debe ser siempre 0. |

## <a name="system-registers"></a>Registros del sistema

Al igual que AArch32, la especificación AArch64 proporciona tres registros "Id. de subproceso" controlados por el sistema:

| Registro | Rol |
| - | - |
| TPIDR_EL0 | Reservado. |
| TPIDRRO_EL0 | Contiene el número de CPU del procesador actual. |
| TPIDR_EL1 | Apunta a la estructura KPCR para el procesador actual. |

## <a name="floating-point-exceptions"></a>Excepciones de punto flotante

La compatibilidad con las excepciones de punto flotante de IEEE es opcional en los sistemas AArch64. En el caso de las variantes de procesador que tengan excepciones de punto flotante de hardware, el kernel de Windows almacena las excepciones en caché de manera silenciosa y las deshabilita implícitamente en el registro FPCR. Esta captura garantiza un comportamiento normalizado en todas las variantes de procesador. De lo contrario, el código desarrollado en una plataforma sin compatibilidad con las excepciones puede producir excepciones inesperadas cuando se ejecute en una plataforma con compatibilidad.

## <a name="parameter-passing"></a>Paso de parámetros

En el caso de las funciones que no son variádicas, la ABI de Windows sigue las reglas que especifica ARM para el paso de parámetros. Estas reglas se extraen directamente del estándar de llamada de procedimiento para la arquitectura AArch64:

### <a name="stage-a--initialization"></a>Fase A: Inicialización

Esta fase se realiza exactamente una vez, antes de que empiece el procesamiento de los argumentos.

1. El siguiente número de registro de uso general (NGRN) se establece en cero.

1. El siguiente número de registro de SIMD y de punto flotante (NSRN) se establece en cero.

1. La siguiente dirección de argumento apilado (NSAA) se establece en el valor actual del puntero de pila (SP).

### <a name="stage-b--pre-padding-and-extension-of-arguments"></a>Fase B: Relleno previo y extensión de argumentos

En cada argumento de la lista se aplica la primera regla que coincida de la lista siguiente. Si no coincide ninguna regla, se utiliza el argumento sin modificar.

1. Si el tipo de argumento es uno compuesto cuyo tamaño no pueden averiguar estáticamente ni el autor ni el destinatario de la llamada, el argumento se copia en la memoria y se reemplaza por un puntero en dicha copia. (No hay ninguno de estos tipos en C/C++, pero sí existen en otros lenguajes o en extensiones de lenguaje).

1. Si el tipo de argumento es HFA o HVA, el argumento se usa sin modificar.

1. Si el tipo de argumento es uno compuesto mayor de 16 bytes, el argumento se copia en la memoria que asigna el autor de la llamada y se reemplaza por un puntero en dicha copia.

1. Si el tipo de argumento es uno compuesto, su tamaño se redondea al alza al múltiplo más próximo de 8 bytes.

### <a name="stage-c--assignment-of-arguments-to-registers-and-stack"></a>Fase C: Asignación de argumentos a registros y la pila

En cada uno de los argumentos de la lista, se aplican las reglas siguientes por turno hasta que los argumentos se hayan asignado. Cuando se asigna un argumento a un registro, los bits sin usar del registro tienen un valor sin especificar. Si se asigna un argumento a una ranura de pila, los bytes de relleno sin usar tienen un valor sin especificar.

1. Si el argumento es un tipo de punto flotante de precisión media, sencilla, doble o cuádruple, o de vector corto, y el valor del NSRN es menor que 8, el argumento se asigna a los bits menos significativos del registro v\[NSRN]. El NSRN se incrementa en uno. Ahora se ha asignado el argumento.

1. Si el argumento es un HFA o un HVA y hay suficientes registros SIMD y de punto flotante sin asignar (NSRN + número de miembros ≤ 8), el argumento se asigna a los registros SIMD y de punto flotante, un registro por miembro de HFA o HVA. El NSRN se incrementará en función del número de registros empleado. Ahora se ha asignado el argumento.

1. Si el argumento es un HFA o un HVA, el NSRN se establece en 8 y su tamaño se redondea al alza al múltiplo más próximo de 8 bytes.

1. Si el argumento es un HFA, un HVA, un tipo de punto flotante de precisión cuádruple o de vector corto, la NSAA se redondea a 8 o a la alineación natural del tipo del argumento, el que sea mayor.

1. Si el argumento es un tipo de punto flotante de precisión media o sencilla, el tamaño del argumento se establece en 8 bytes. El efecto es como si el argumento se hubiera copiado en los bits menos significativos de un registro de 64 bits y los bits restantes se hubieran rellenado con valores sin especificar.

1. Si el argumento es un HFA, un HVA, un tipo de punto flotante de precisión media, sencilla, doble o cuádruple, o de vector corto, el argumento se copia en la memoria en la NSAA ajustada. La NSAA se incrementará en función del tamaño del argumento. Ahora se ha asignado el argumento.

1. Si el argumento es un tipo integral o de puntero, el tamaño del argumento es menor o igual que 8 bytes y el valor de NGRN es menor que 8, el argumento se copia en los bits menos significativos en x\[NGRN]. El NSRN se incrementa en uno. Ahora se ha asignado el argumento.

1. Si el argumento tiene una alineación de 16, el NGRN se redondea al siguiente número par.

1. Si el argumento es un tipo entero, el tamaño del argumento es igual a 16 y el valor de NGRN es menor que 7, el argumento se copia en x\[NGRN] y x\[NGRN+1]. x\[NGRN] debe contener la palabra doble más baja a la que haga referencia de la representación de memoria del argumento. El NSRN se incrementa en dos. Ahora se ha asignado el argumento.

1. Si el argumento es un tipo compuesto y el tamaño en palabras dobles del argumento no es superior a 8 menos NGRN, el argumento se copia en registros de uso general consecutivos, empezando por x\[NGRN]. El argumento se pasa como si se hubiera cargado en los registros desde una dirección de doble palabra alineada, con una secuencia adecuada de instrucciones de LDR que cargan registros consecutivos de la memoria. Este estándar no especifica el contenido de las partes sin usar de los registros. El NGRN se incrementará en función del número de registros empleado. Ahora se ha asignado el argumento.

1. El valor de NGRN se establece en 8.

1. La NSAA se redondea a 8 o a la alineación natural del tipo del argumento, el que sea mayor.

1. Si el argumento es un tipo compuesto, el argumento se copia en la memoria, en la NSAA ajustada. La NSAA se incrementará en función del tamaño del argumento. Ahora se ha asignado el argumento.

1. Si el tamaño del argumento es inferior a 8 bytes, se establece en 8 bytes. El efecto es como si el argumento se hubiera copiado en los bits menos significativos de un registro de 64 bits y los restantes se hubieran rellenado con valores sin especificar.

1. El argumento se copia en la memoria, en la NSAA ajustada. La NSAA se incrementará en función del tamaño del argumento. Ahora se ha asignado el argumento.

### <a name="addendum-variadic-functions"></a>Anexo: funciones variádicas

Las funciones que toman un número variable de argumentos se administran de forma distinta a como se indica anteriormente, del modo siguiente:

1. Todos los compuestos se tratan igual, sin tratamiento especial de HFA o HVA.

1. No se usan los registros SIMD y de punto flotante.

De hecho, es lo mismo que las reglas siguientes C.12–C.15 para asignar argumentos a una pila imaginaria, donde los primeros 64 bytes de la pila se cargan en x0-x7, y los argumentos de pila restantes se colocan normalmente.

## <a name="return-values"></a>Valores devueltos

Los valores enteros se devuelven en x0.

Los valores de punto flotante se devuelven en s0, d0 o v0, según corresponda.

Los valores HFA y HVA se devuelven en s0-s3, d0-d3 o v0-v3, según corresponda.

Los tipos devueltos por valor se administran de forma diferente en función de si tienen determinadas propiedades. Los tipos que tienen todas estas propiedades:

- son *agregados* por una definición de estándar de C++14, es decir, no tienen ningún constructor proporcionado por el usuario, ningún miembro de datos no estático privado o protegido, ninguna clase base ni ninguna función virtual,
- tienen un operador de asignación de copia trivial y
- tienen un destructor trivial,

usan el estilo de devolución siguiente:

- Los tipos menores o iguales que 8 bytes se devuelven en x0.
- Los tipos menores o iguales que 16 bytes se devuelven en x0 y x1, donde x0 contiene los 8 bytes de orden inferior.
- En el caso de tipos mayores de 16 bytes, el autor de la llamada reservará un bloque de memoria de tamaño y alineación suficientes para contener el resultado. La dirección del bloque de memoria se pasará como argumento adicional a la función en x8. El destinatario puede modificar el bloque de memoria de resultados en cualquier momento durante la ejecución de la subrutina. No es necesario que el destinatario conserve el valor almacenado en x8.

El resto de los tipos usan esta convención:

- El autor de la llamada reservará un bloque de memoria de tamaño y alineación suficientes para contener el resultado. La dirección del bloque de memoria se pasará como argumento adicional a la función en x0, o x1 si la variable $this se pasa en x0. El destinatario puede modificar el bloque de memoria de resultados en cualquier momento durante la ejecución de la subrutina. El destinatario devuelve la dirección del bloque de memoria en x0.

## <a name="stack"></a>Pila

Después de la ABI que propone ARM, la pila debe permanecer con una alineación de 16 bytes en todo momento. AArch64 contiene una característica de hardware que genera errores de alineación de pila cuando el SP no tiene una alineación de 16 bytes y se realiza una carga o un almacén relativos a SP. Windows se ejecuta con esta característica habilitada en todo momento.

Las funciones que asignan 4 KB o más en la pila deben garantizar que todas las páginas previas a la página final se tocan en orden. Con esta acción se consigue que ningún código pueda “saltarse” las páginas de restricción que Windows usa para expandir la pila. Normalmente, el asistente de `__chkstk` realiza el toque, que tiene una convención de llamada personalizada que pasa la asignación de pila total dividida entre 16 en x15.

## <a name="red-zone"></a>Zona roja

El área de 16 bytes inmediatamente debajo del puntero de pila actual está reservada para escenarios de análisis y revisión dinámica. Esto permite que se pueda insertar con cuidado código generado donde se almacenan dos registros en [sp, #-16] y que se usen temporalmente con fines arbitrarios. El kernel de Windows garantiza que esos 16 bytes no se van a sobrescribir si se produce una excepción o interrupción, ya sea en el modo de usuario o kernel.

## <a name="kernel-stack"></a>Pila de kernel

La pila predeterminada en modo kernel en Windows consta de seis páginas (24 KB). Preste mucha atención a las funciones con búferes de pila de gran tamaño en modo kernel. Podría producirse una interrupción inoportuna con poca capacidad y provocar una comprobación de errores de pánico de la pila.

## <a name="stack-walking"></a>Recorrido de la pila

El código de Windows se compila con los punteros de marco habilitados ([/Oy-](reference/oy-frame-pointer-omission.md)) para permitir el recorrido rápido de la pila. Por lo general, el registro x29 (fp) apunta al vínculo siguiente de la cadena, que es un par {fp, lr} que indica el puntero al marco anterior en la pila, así como la dirección de devolución. También se recomienda que el código de terceros habilite los punteros de marco para permitir la generación de perfiles y el seguimiento mejorados.

## <a name="exception-unwinding"></a>Desenredado en excepciones

El desenredado durante el control de excepciones está respaldado por el uso de códigos de desenredado. Los códigos de desenredado son una secuencia de bytes almacenada en la sección .xdata del ejecutable. Describen la operación del prólogo y epílogo de forma abstracta, de manera que los efectos del prólogo de una función se pueden deshacer como preparación para realizar la copia de seguridad en el marco de pila del autor de la llamada. Para obtener más información sobre los códigos de desenredado, vea [Control de excepciones de ARM64](arm64-exception-handling.md).

La EABI de ARM también especifica un modelo de desenredado en excepciones en el que se usan códigos de desenredado. Sin embargo, la especificación tal y como se presenta no basta para el desenredado en Windows, donde se deben controlar casos en los que el PC se encuentra en medio del prólogo o el epílogo de una función.

El código generado dinámicamente se debe describir con tablas de funciones dinámicas a través de `RtlAddFunctionTable` y de funciones asociadas, ya que así el código generado podrá participar en el tratamiento de excepciones.

## <a name="cycle-counter"></a>Contador de ciclos

Todas las CPU de ARMv8 son necesarias para admitir un registro de contador de ciclo, un registro de 64 bits que Windows configura para que sea legible en cualquier nivel de excepción, incluido el modo de usuario. Se puede acceder a través del registro especial de PMCCNTR_EL0, mediante el código de operación MSR en el código del ensamblado o con el código de C/C++ intrínseco en `_ReadStatusReg`.

El contador de ciclo aquí es un contador de ciclo verdadero, no un reloj. La frecuencia del contador dependerá de la frecuencia del procesador. Si cree que debe conocer la frecuencia del contador del ciclo, no lo debería usar. En su lugar, querrá medir el tiempo de reloj, para lo cual debería usar `QueryPerformanceCounter`.

## <a name="see-also"></a>Vea también

[Problemas comunes de migración de ARM en Visual C++](common-visual-cpp-arm-migration-issues.md)<br/>
[Control de excepciones de ARM64](arm64-exception-handling.md)
