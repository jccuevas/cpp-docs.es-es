---
title: Información general sobre las convenciones ABI de ARM64
ms.date: 03/27/2019
ms.openlocfilehash: 3a3df475b8f814fcecaf2e67a0a62c7267a0de30
ms.sourcegitcommit: e805200eaef4fe7a65a00051bbd305273af94fe7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2019
ms.locfileid: "74163222"
---
# <a name="overview-of-arm64-abi-conventions"></a>Información general sobre las convenciones ABI de ARM64

La interfaz binaria de aplicación (ABI) básica para Windows cuando se compila y se ejecuta en procesadores ARM en el modo de 64 bits (ARMv8 o en arquitecturas posteriores), en la mayoría de los casos, sigue AArch64 EABI estándar de ARM. En este artículo se resaltan algunas de las suposiciones clave y los cambios que se documentan en el EABI. Para obtener información sobre la ABI de 32 bits, consulte [información general de las convenciones de la ABI de ARM](overview-of-arm-abi-conventions.md). Para obtener más información sobre la EABI de ARM estándar, consulte [la interfaz binaria de aplicación (ABI) de la arquitectura ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html) (vínculo externo).

## <a name="definitions"></a>Definiciones

Con la introducción de la compatibilidad con 64 bits, ARM ha definido varios términos:

- **AArch32** : la arquitectura de conjunto de instrucciones de 32 bits (ISA) heredada definida por ARM, incluida la ejecución en modo Thumb.
- **AArch64** : la nueva arquitectura de conjunto de instrucciones (ISA) de 64 bits definida por ARM.
- **ARMv7** : la especificación del hardware ARM de "séptima generación", que solo incluye compatibilidad con AArch32. Esta versión del hardware de ARM es la primera versión de Windows para ARM compatible.
- **ARMv8** : la especificación del hardware ARM de "octava generación", que incluye compatibilidad con AArch32 y AArch64.

Windows también usa estos términos:

- **ARM** : hace referencia a la arquitectura arm de 32 bits (AArch32), que a veces se conoce como WoA (Windows en ARM).
- **ARM32** : igual que ARM, arriba; se usa en este documento para mayor claridad.
- **ARM64** : hace referencia a la arquitectura ARM de 64 bits (AArch64). No hay nada en WoA64.

Por último, cuando se hace referencia a los tipos de datos, se hace referencia a las siguientes definiciones de ARM:

- **Short-vector** : un tipo de datos que se represente directamente en SIMD, un vector de 8 bytes o un valor de 16 bytes de elementos. Está alineado con su tamaño, 8 bytes o 16 bytes, donde cada elemento puede ser 1, 2, 4 u 8 bytes.
- **HFA (agregado de punto flotante homogéneo)** : tipo de datos con 2 a 4 miembros de punto flotante idénticos, float o Double.
- **HVA (agregado de vector corto homogéneo)** : tipo de datos con 2 a 4 miembros de vectores cortos idénticos.

## <a name="base-requirements"></a>Requisitos básicos

En todo momento, la versión ARM64 de Windows presupone que se ejecuta en una arquitectura ARMv8 o posterior. Se supone que la compatibilidad de punto flotante y de neón está presente en el hardware.

La especificación ARMv8 describe los códigos de la aplicación auxiliar de cifrado de CRC y Crypto opcional para AArch32 y AArch64. Actualmente, la compatibilidad con ellos es opcional, pero se recomienda. Para sacar partido de estos códigos de ejecución, las aplicaciones primero deben realizar comprobaciones en tiempo de ejecución en busca de su existencia.

## <a name="endianness"></a>Modos endian

Al igual que con la versión ARM32 de Windows, en ARM64 Windows se ejecuta en modo Little-Endian. Cambiar modos endian es difícil de lograr sin la compatibilidad con el modo kernel en AArch64, por lo que es más fácil de aplicar.

## <a name="alignment"></a>Alineación

Windows que se ejecuta en ARM64 permite que el hardware de CPU controle los accesos desalineados de forma transparente. En una mejora de AArch32, esta compatibilidad ahora también funciona con todos los accesos enteros (incluidos los accesos de varias palabras) y para los accesos de punto flotante.

Sin embargo, el acceso a la memoria no almacenada en caché (dispositivo) todavía debe estar alineado. Si el código podría leer o escribir datos desalineados de la memoria no almacenada en caché, debe asegurarse de alinear todos los accesos.

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
| > = 64 | 16 |

## <a name="integer-registers"></a>Registros de enteros

La arquitectura AArch64 admite registros enteros de 32:

| Registro | ¿Volátil? | Rol |
| - | - | - |
| x0 | Volátil | Parámetro/registro de borrado 1, registro de resultados |
| x1-7 | Volátil | Parámetro/registro temporal 2-8 |
| x8-x15 | Volátil | Registros de borrado |
| x16-X17 | Volátil | Registros temporales de llamada de procedimiento interno |
| x18 | No volátil | Registro de plataforma: en modo kernel, apunta a KPCR para el procesador actual; en modo de usuario, apunta a TEB |
| x19-x28 | No volátil | Registros de borrado |
| X29/FP | No volátil | Puntero de marco |
| x30/LR | No volátil | Registros de vínculos |

Se puede tener acceso a cada registro como un valor completo de 64 bits (a través de x0-x30) o como un valor de 32 bits (a través de W0 (-W30). las operaciones de 32 bits extienden a cero sus resultados hasta 64 bits.

Consulte la sección paso de parámetros para obtener información detallada sobre el uso de los registros de parámetros.

A diferencia de AArch32, el contador de programas (PC) y el puntero de pila (SP) no son registros indexados. Están limitadas en cómo se puede acceder a ellos. Tenga en cuenta también que no hay ningún registro x31. Esa codificación se usa para fines especiales.

El puntero de marco (X29) es necesario por compatibilidad con el recorrido de pila rápido usado por ETW y otros servicios. Debe apuntar al par {X29, x30} anterior en la pila.

## <a name="floating-pointsimd-registers"></a>Registros de punto flotante/SIMD

La arquitectura AArch64 también admite registros de punto flotante/SIMD 32, que se resumen a continuación:

| Registro | ¿Volátil? | Rol |
| - | - | - |
| V0 | Volátil | Parámetro/registro de borrado 1, registro de resultados |
| v1-V7 | Volátil | Registros de parámetros/grietas de 2-8 |
| V8-V15 | No volátil | Registros de borrado (solo los bits 64 bajos son no volátiles) |
| v16-v31 | Volátil | Registros de borrado |

Se puede tener acceso a cada registro como un valor completo de 128 bits (a través de V0-v31 o q0-q31). Se puede tener acceso a él como un valor de 64 bits (a través de d0-D31), como un valor de 32 bits (a través de S0-S31), como un valor de 16 bits (a través de H0-H31) o como un valor de 8 bits (a través de B0-B31). El acceso a menos de 128 bits solo tiene acceso a los bits inferiores del registro completo de 128 bits. Dejan los bits restantes sin tocar a menos que se especifique lo contrario. (AArch64 es diferente de AArch32, donde los registros más pequeños se empaquetaron encima de los registros mayores).

El registro de control de punto flotante (FPCR) tiene ciertos requisitos en los distintos campos de bits que contiene:

| Bits | Significado | ¿Volátil? | Rol |
| - | - | - | - |
| 26 | AHP | No volátil | Control de media precisión alternativo. |
| 25 | DN | No volátil | Control de modo NaN predeterminado. |
| 24 | FZ | No volátil | Control de modo de vaciado a cero. |
| 23-22 | RMode | No volátil | Control de modo de redondeo. |
| 15, 12-8 | IDE/IXE/etc. | No volátil | La captura de excepciones habilita los bits, siempre debe ser 0. |

## <a name="system-registers"></a>Registros del sistema

Al igual que AArch32, la especificación AArch64 proporciona tres registros "ID. de subproceso" controlado por el sistema:

| Registro | Rol |
| - | - |
| TPIDR_EL0 | Reservado. |
| TPIDRRO_EL0 | Contiene el número de CPU del procesador actual. |
| TPIDR_EL1 | Apunta a la estructura KPCR para el procesador actual. |

## <a name="floating-point-exceptions"></a>Excepciones de punto flotante

La compatibilidad con las excepciones de punto flotante de IEEE es opcional en los sistemas AArch64. En el caso de las variantes de procesador que tienen excepciones de punto flotante de hardware, el kernel de Windows detecta las excepciones de forma silenciosa y las deshabilita de forma implícita en el registro FPCR. Esta captura garantiza un comportamiento normalizado entre variantes de procesador. De lo contrario, el código desarrollado en una plataforma sin compatibilidad con las excepciones puede ser que se produzcan excepciones inesperadas cuando se ejecute en una plataforma compatible con.

## <a name="parameter-passing"></a>Paso de parámetros

En el caso de las funciones que no son variádicas, la ABI de Windows sigue las reglas especificadas por ARM para el paso de parámetros. Estas reglas se extoman directamente del estándar de llamada de procedimiento para la arquitectura de AArch64:

### <a name="stage-a--initialization"></a>Fase A: inicialización

Esta fase se realiza exactamente una vez, antes de que empiece el procesamiento de los argumentos.

1. El siguiente número de registro de uso general (NGRN) se establece en cero.

1. El siguiente número de registro SIMD y de punto flotante (NSRN) se establece en cero.

1. La siguiente dirección de argumento apilado (NSAA) se establece en el valor del puntero de pila actual (SP).

### <a name="stage-b--pre-padding-and-extension-of-arguments"></a>Fase B: relleno previo y extensión de argumentos

Para cada argumento de la lista, se aplica la primera regla coincidente de la lista siguiente. Si no coincide ninguna regla, se utiliza el argumento sin modificar.

1. Si el tipo de argumento es un tipo compuesto cuyo tamaño no se puede determinar de forma estática por el llamador y el destinatario, el argumento se copia en la memoria y el argumento se reemplaza por un puntero a la copia. (No hay ningún tipo de estos tipos enC++ C/pero existen en otros lenguajes o en extensiones de lenguaje).

1. Si el tipo de argumento es HFA o HVA, el argumento se usa sin modificar.

1. Si el tipo de argumento es un tipo compuesto mayor de 16 bytes, el argumento se copia en la memoria asignada por el llamador y el argumento se reemplaza por un puntero a la copia.

1. Si el tipo de argumento es un tipo compuesto, el tamaño del argumento se redondea al múltiplo más cercano de 8 bytes.

### <a name="stage-c--assignment-of-arguments-to-registers-and-stack"></a>Fase C: asignación de argumentos a registros y pila

Para cada argumento de la lista, se aplican las siguientes reglas a su vez hasta que se haya asignado el argumento. Cuando se asigna un argumento a un registro, los bits sin usar del registro tienen un valor sin especificar. Si se asigna un argumento a una ranura de pila, los bytes de relleno no utilizados tienen un valor sin especificar.

1. Si el argumento es un tipo de vector de punto flotante, de doble o de precisión cuádruple o de doble precisión y el valor de NSRN es menor que 8, el argumento se asigna a los bits menos significativos del registro v\[NSRN]. El NSRN se incrementa en uno. Ahora se ha asignado el argumento.

1. Si el argumento es un HFA o un HVA y hay suficientes registros SIMD sin asignar y de punto flotante (NSRN + número de miembros ≤ 8), el argumento se asigna a los registros SIMD y de punto flotante, un registro por miembro de HFA o HVA. El valor de NSRN se incrementa según el número de registros utilizados. Ahora se ha asignado el argumento.

1. Si el argumento es un HFA o un HVA, el valor de NSRN se establece en 8 y el tamaño del argumento se redondea al múltiplo más cercano de 8 bytes.

1. Si el argumento es un HFA, un HVA, un punto flotante de precisión cuádruple o un tipo de vector corto, el NSAA se redondea al mayor de 8 o la alineación natural del tipo del argumento.

1. Si el argumento es un tipo de punto flotante de precisión sencilla o media, el tamaño del argumento se establece en 8 bytes. El efecto es como si el argumento se hubiera copiado en los bits menos significativos de un registro de 64 bits y los bits restantes rellenados con valores no especificados.

1. Si el argumento es un tipo de punto flotante de HFA, un valor de HVA, un tipo de vector de punto flotante de doble o de precisión cuádruple o de precisión cuádruple, el argumento se copia en la memoria en el NSAA ajustado. La NSAA se incrementará en función del tamaño del argumento. Ahora se ha asignado el argumento.

1. Si el argumento es un tipo entero o de puntero, el tamaño del argumento es menor o igual que 8 bytes y el valor de NGRN es menor que 8, el argumento se copia en los bits menos significativos en x\[NGRN]. El NGRN se incrementa en uno. Ahora se ha asignado el argumento.

1. Si el argumento tiene una alineación de 16, el NGRN se redondea al siguiente número par.

1. Si el argumento es un tipo entero, el tamaño del argumento es igual a 16 y el valor de NGRN es inferior a 7, el argumento se copia en x\[NGRN] y x\[NGRN + 1]. x\[NGRN] debe contener la doble palabra con dirección inferior de la representación de memoria del argumento. El NGRN se incrementa en dos. Ahora se ha asignado el argumento.

1. Si el argumento es un tipo compuesto y el tamaño en dos palabras dobles del argumento no es superior a 8 menos NGRN, el argumento se copia en registros de uso general consecutivos, empezando por x\[NGRN]. El argumento se pasa como si se hubiera cargado en los registros desde una dirección de doble palabra alineada, con una secuencia adecuada de instrucciones de LDR que cargan registros consecutivos de la memoria. Este estándar no especifica el contenido de las partes no utilizadas de los registros. El valor de NGRN se incrementa según el número de registros utilizados. Ahora se ha asignado el argumento.

1. El valor de NGRN se establece en 8.

1. El NSAA se redondea al mayor de 8 o la alineación natural del tipo del argumento.

1. Si el argumento es un tipo compuesto, el argumento se copia en la memoria en el NSAA ajustado. La NSAA se incrementará en función del tamaño del argumento. Ahora se ha asignado el argumento.

1. Si el tamaño del argumento es inferior a 8 bytes, el tamaño del argumento se establece en 8 bytes. El efecto es como si el argumento se copiase en los bits menos significativos de un registro de 64 bits y los bits restantes se rellenaron con valores no especificados.

1. El argumento se copia en la memoria en el NSAA ajustado. La NSAA se incrementará en función del tamaño del argumento. Ahora se ha asignado el argumento.

### <a name="addendum-variadic-functions"></a>Anexo: funciones de Variádicas

Las funciones que toman un número variable de argumentos se administran de forma distinta a como se indica a continuación:

1. Todos los compuestos se tratan igual que. sin tratamiento especial de HFAs o HVAs.

1. No se usan los registros SIMD y de punto flotante.

De hecho, es lo mismo que la siguiente regla C. 12 – C. 15 para asignar argumentos a una pila imaginaria, donde los primeros 64 bytes de la pila se cargan en x0-7, y los argumentos de pila restantes se colocan normalmente.

## <a name="return-values"></a>Valores devueltos

Los valores enteros se devuelven en x0.

Los valores de punto flotante se devuelven en S0, d0 o V0, según corresponda.

Los valores HFA y HVA se devuelven en S0-S3, d0-D3 o V0-V3, según corresponda.

Los tipos devueltos por valor se administran de forma diferente en función de si tienen determinadas propiedades. Tipos que tienen todas estas propiedades,

- se *agregan* mediante la definición estándar de c++ 14, es decir, no tienen ningún constructor proporcionado por el usuario, ningún miembro de datos no estático privado o protegido, ninguna clase base y ninguna función virtual.
- tienen un operador de asignación de copia trivial y
- tienen un destructor trivial,

Use el siguiente estilo de devolución:

- Los tipos menores o iguales a 8 bytes se devuelven en x0.
- Los tipos menores y iguales que 16 bytes se devuelven en x0 y x1, donde x0 contiene los 8 bytes de orden inferior.
- En el caso de tipos mayores de 16 bytes, el autor de la llamada reservará un bloque de memoria de tamaño y alineación suficientes para contener el resultado. La dirección del bloque de memoria se pasará como argumento adicional a la función en x8. El destinatario puede modificar el bloque de memoria de resultados en cualquier momento durante la ejecución de la subrutina. No es necesario que el destinatario de la llamada conserve el valor almacenado en x8.

Todos los demás tipos usan esta Convención:

- El autor de la llamada reservará un bloque de memoria de tamaño y alineación suficientes para contener el resultado. La dirección del bloque de memoria se pasará como argumento adicional a la función en x0, o x1 si $this se pasa en x0. El destinatario puede modificar el bloque de memoria de resultados en cualquier momento durante la ejecución de la subrutina. El destinatario devuelve la dirección del bloque de memoria en x0.

## <a name="stack"></a>Pila

Después de la ABI presentada por ARM, la pila debe permanecer alineada en todo momento de 16 bytes. AArch64 contiene una característica de hardware que genera errores de alineación de pila cuando el SP no tiene una alineación de 16 bytes y se realiza una carga o un almacén relativos a SP. Windows se ejecuta con esta característica habilitada en todo momento.

Las funciones que asignan 4k o más de una pila deben asegurarse de que todas las páginas anteriores a la página final se tocan en orden. Esta acción garantiza que ningún código pueda "pasar por encima" las páginas de protección que Windows usa para expandir la pila. Normalmente, la aplicación auxiliar de `__chkstk` realiza el toque, que tiene una Convención de llamada personalizada que pasa la asignación de pila total dividida entre 16 en x15.

## <a name="red-zone"></a>Zona roja

El área de 16 bytes inmediatamente debajo del puntero de pila actual se reserva para su uso en escenarios de análisis y de revisión dinámica. Esta área permite insertar el código generado cuidadosamente, que almacena dos registros en [SP, #-16] y los utiliza de forma temporal para propósitos arbitrarios. El kernel de Windows garantiza que esos 16 bytes no se sobrescriben si se realiza una excepción o una interrupción, en modo de usuario y de kernel.

## <a name="kernel-stack"></a>Pila de kernel

La pila de modo kernel predeterminada en Windows es de seis páginas (24K). Preste atención adicional a las funciones con búferes de pila de gran tamaño en modo kernel. Una interrupción con un tiempo incorrecto podría entrar en un poco de espacio y crear una comprobación de errores de pánico de la pila.

## <a name="stack-walking"></a>Recorrido de la pila

El código dentro de Windows se compila con punteros de Marcos habilitados ([/Oy-](reference/oy-frame-pointer-omission.md)) para permitir un recorrido rápido de la pila. Por lo general, X29 (FP) apunta al siguiente vínculo de la cadena, que es un par {FP, LR}, que indica el puntero al fotograma anterior en la pila y la dirección de devolución. También se recomienda que el código de terceros habilite los punteros de marco para permitir la generación de perfiles y el seguimiento mejorados.

## <a name="exception-unwinding"></a>Desenredo de excepciones

El desenredado durante el control de excepciones está asistido por el uso de códigos de desenredado. Los códigos de desenredado son una secuencia de bytes almacenada en la sección. xdata del archivo ejecutable. Describen el funcionamiento del prólogo y epílogo de forma abstracta, de modo que los efectos del prólogo de una función se pueden deshacer como preparación para la copia de seguridad en el marco de pila del llamador. Para obtener más información sobre los códigos de desenredado, vea [control de excepciones ARM64](arm64-exception-handling.md).

ARM EABI también especifica un modelo de desenredado de excepciones que usa códigos de desenredado. Sin embargo, la especificación tal como se presenta es insuficiente para desenredar en Windows, que debe controlar los casos en los que el equipo se encuentra en medio de una función prólogo o epílogo.

El código generado dinámicamente se debe describir con las tablas de funciones dinámicas a través de `RtlAddFunctionTable` y las funciones asociadas, de modo que el código generado pueda participar en el control de excepciones.

## <a name="cycle-counter"></a>Contador de ciclo

Todas las CPU de ARMv8 son necesarias para admitir un registro de contador de ciclo, un registro de 64 bits que Windows configura para ser legible en cualquier nivel de excepción, incluido el modo de usuario. Se puede tener acceso a ella a través del registro especial de PMCCNTR_EL0, mediante el código de operación MSR en el código del ensambladoC++ o el `_ReadStatusReg` intrínseco en C/Code.

El contador de ciclo aquí es un contador de ciclo verdadero, no un reloj de pared. La frecuencia de recuento dependerá de la frecuencia del procesador. Si cree que debe conocer la frecuencia del contador del ciclo, no debe usar el contador de ciclo. En su lugar, se desea medir el tiempo de reloj, para el que se debe usar `QueryPerformanceCounter`.

## <a name="see-also"></a>Vea también

[Problemas comunes de migración de ARM en Visual C++](common-visual-cpp-arm-migration-issues.md)<br/>
[Control de excepciones ARM64](arm64-exception-handling.md)
