---
title: Información general sobre las convenciones ABI ARM64
ms.date: 03/27/2019
ms.openlocfilehash: 4c0f89f97529d4cd70e1449c90b131d25d30f9ee
ms.sourcegitcommit: ac5c04b347e817eeece6e2c98e60236fc0e307a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/29/2019
ms.locfileid: "58639451"
---
# <a name="overview-of-arm64-abi-conventions"></a>Información general sobre las convenciones ABI ARM64

La interfaz binaria de aplicación básica (ABI) de Windows cuando se compila y se ejecutan en procesadores ARM en modo de 64 bits (ARMv8 o arquitecturas más adelante), en su mayor parte, sigue la norma EABI de AArch64 de ARM. Este artículo resalta algunas de las suposiciones de clave y los cambios de las documentadas en la EABI. Para obtener información acerca de la ABI de 32 bits, consulte [las convenciones ABI de información general de ARM](overview-of-arm-abi-conventions.md). Para obtener más información acerca de la norma EABI de ARM, consulte [interfaz binaria de aplicación (ABI) de la arquitectura ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html) (vínculo externo).

## <a name="definitions"></a>Definiciones

Con la introducción de la compatibilidad con 64 bits, ARM ha definido varios términos:

- **AArch32** : arquitectura (ISA) definido por ARM, incluida la ejecución de modo de control de posición de conjunto de la instrucción de 32 bits heredada.
- **AArch64** : arquitectura (ISA) definido por ARM de conjunto de la nueva instrucción de 64 bits.
- **ARMv7** : la especificación de "generación comienzan el 7 de" hardware ARM, lo que solo incluye compatibilidad con AArch32. Esta versión del hardware ARM es la primera versión de Windows para ARM admitida.
- **ARMv8** : la especificación de "generación 8" hardware ARM, lo que incluye compatibilidad con AArch32 y AArch64.

Windows también utilizan estos términos:

- **ARM** : hace referencia a la arquitectura ARM de 32 bits (AArch32), que a veces se denomina WoA (Windows en ARM).
- **ARM32** : igual que ARM, anterior; se utiliza en este documento para mayor claridad.
- **ARM64** : hace referencia a la arquitectura ARM de 64 bits (AArch64). No hay nada como WoA64.

Por último, cuando se hace referencia a tipos de datos, las siguientes definiciones de ARM se hace referencia:

- **Short Vector** : un tipo de datos se puede representar directamente en SIMD, un vector de bytes de 8 o 16 bytes correspondientes a los elementos. Se está alineado a su tamaño, en bytes de 8 o 16 bytes, donde cada elemento puede ser 1, 2, 4 u 8 bytes.
- **(Punto flotante homogéneo agregado) HFA** : un tipo de datos con los miembros de punto flotante idénticos de 2 a 4, ser flotantes o duplica.
- **HVA (Short vectorial homogéneo agregado)** : un tipo de datos con los miembros idénticos de Vector corto de 2 a 4.

## <a name="base-requirements"></a>Requisitos básicos

La versión ARM64 de Windows se presupone que se está ejecutando en un ARMv8 o arquitectura posterior en todo momento. Ambos punto flotante y soporte técnico de NEÓN se supone que la presente en el hardware.

La especificación de ARMv8 permite la compatibilidad completa de aplicaciones AArch32. Sin embargo, no está prevista la compatibilidad con las aplicaciones de ARM32 existentes en la versión ARM64 de Windows. (Es decir, hay no hay planes para WOW64). Esta compatibilidad está sujeto a la reevaluación de en el futuro, pero es la suposición de trabajo actual.

La especificación de ARMv8 describe crypto opcional nueva y códigos auxiliares CRC para AArch32 y AArch64. Compatibilidad con ellos está actualmente opcional pero recomendado. Aplicaciones para sacar provecho de estos códigos de operación, deben convertirlo en tiempo de ejecución comprueba su existencia.

## <a name="endianness"></a>Modos endian

Como con el ARM32 versión de Windows en Windows ARM64 se ejecuta en modo little-endian. Cambiar modos endian es difícil de lograr sin compatibilidad con el modo kernel en AArch64, por lo que es más fácil de aplicar.

## <a name="alignment"></a>Alineación

Que se ejecutan en ARM64 de Windows permite que el hardware de CPU para controlar de forma transparente los accesos desalineados. En una mejora con respecto a AArch32, esta compatibilidad ahora también funciona para todos los accesos de entero (incluidos los accesos de múltiples palabras) y para accesos de punto flotante.

Sin embargo, los accesos a la memoria caché (dispositivo) sigue siempre se deben alinear. Si el código posiblemente podría leer o escribir datos mal alineados de la memoria caché, debe asegurarse alinear todos los accesos.

## <a name="integer-registers"></a>Registros de enteros

La arquitectura AArch64 admite 32 registros de enteros:

| Registro | ¿Volátil? | Rol |
| - | - | - |
| x0 | Volátil | Parámetro/cero registrar 1, el registro de resultados |
| x1-x7 | Volátil | Register/cero el parámetro 2-8 |
| x8-x15 | Volátil | Registros |
| x16-x17 | Volátil | Registros de llamada de procedimiento dentro de un borrador |
| x18 | No volátil | Registro de la plataforma: en modo kernel, señala KPCR del procesador actual; en modo de usuario, señala TEB |
| x19-x28 | No volátil | Registros |
| x29/fp | No volátil | Puntero de marco |
| x30/lr | No volátil | Registra el vínculo |

Puede tener acceso a cada registro como un valor de 64 bits (a través de x0-x30) o como un valor de 32 bits (a través de w0-w30). las operaciones de 32 bits cero-extensión sus resultados hasta 64 bits.

Consulte el parámetro pasar la sección para obtener más información sobre el uso de los registros de parámetro.

A diferencia de AArch32, el contador de programas (PC) y el puntero de pila (SP) no están indizadas registros. Está limitados en cómo puede tener acceso. También tenga en cuenta que no hay ningún x31 registrar. Que se utiliza la codificación para fines especiales.

El puntero de marco (x29) es necesario para la compatibilidad con recorridos de pila rápidos usando ETW y otros servicios. Debe apuntar a la anterior {x29, x 30} par en la pila.

## <a name="floating-pointsimd-registers"></a>Registros de punto flotante/SIMD

La arquitectura AArch64 también admite 32 registros de punto flotante/SIMD, resumidos a continuación:

| Registro | ¿Volátil? | Rol |
| - | - | - |
| v0 | Volátil | Parámetro/cero registrar 1, el registro de resultados |
| v1-v7 | Volátil | Parámetro/cero registra 2-8 |
| v8-v15 | No volátil | Cero registra (solo 64 bits inferiores son volátiles) |
| v16-v31 | Volátil | Registros |

Puede tener acceso a cada registro como un valor de 128 bits (mediante v0 v31 o q0 q31). Podrá acceder a él como un valor de 64 bits (a través de d0-d31), como un valor de 32 bits (a través de s0-s31), como un valor de 16 bits (a través de h0-h31) o como un valor de 8 bits (a través de b0-b31). Accesos inferior a 128 bits tener acceso solo a los bits inferiores del registro de 128 bits. Deje intacto el resto de bits a menos que se especifique lo contrario. (AArch64 es diferente de AArch32, donde se empaquetan los registros más pequeños encima de los registros de mayor tamaño).

El registro de control de punto flotante (FPCR) tiene ciertos requisitos de los distintos campos de bits dentro de él:

| Bits | Significado | ¿Volátil? | Rol |
| - | - | - | - |
| 26 | AHP | No volátil | Control de Media precisión alternativo. |
| 25 | DN | No volátil | Control de modo de NaN predeterminado. |
| 24 | FZ | No volátil | Control del modo de vaciado de cero. |
| 23-22 | RMode | No volátil | Control del modo de redondeo. |
| 15,12-8 | IDE/IXE/etc | No volátil | Excepción interceptar habilitar bits, siempre debe ser 0. |

## <a name="system-registers"></a>Registros del sistema

Al igual que AArch32, la especificación de AArch64 proporciona tres registros "Id. de subproceso" controlado por el sistema:

| Registro | Rol |
| - | - |
| TPIDR_EL0 | Reservado. |
| TPIDRRO_EL0 | Contiene el número de CPU de procesador actual. |
| TPIDR_EL1 | Apunta a la estructura de KPCR de procesador actual. |

## <a name="floating-point-exceptions"></a>Excepciones de punto flotante

Soporte técnico para las excepciones de punto flotante de IEEE es opcional en los sistemas de AArch64. Para las variantes de procesador que tienen excepciones de punto flotante de hardware, el kernel de Windows detecta automáticamente las excepciones y las deshabilita implícitamente en el registro FPCR. Esta captura garantiza un comportamiento normalizado a través de las variantes de procesador. En caso contrario, el código desarrollado en una plataforma sin compatibilidad con la excepción posible propio teniendo excepciones inesperadas cuando se ejecuta en una plataforma compatible con.

## <a name="parameter-passing"></a>Paso de parámetros

Para las funciones no variádicas, la ABI de Windows sigue las reglas especificadas por ARM para pasar parámetros. Estas reglas son un extracto directamente desde el estándar llame al procedimiento de la arquitectura de AArch64:

### <a name="stage-a--initialization"></a>Fase A: inicialización

Esta fase se realiza exactamente una vez, antes de que comience el procesamiento de los argumentos.

1. El número siguiente de registro de uso general (NGRN) se establece en cero.

1. El siguiente SIMD y el número de registro de punto flotante (NSRN) se establece en cero.

1. La siguiente dirección de argumento apilado (NSAA) se establece en el valor de puntero de pila actual (SP).

### <a name="stage-b--pre-padding-and-extension-of-arguments"></a>Fase B: relleno previo y extensión de argumentos

Para cada argumento de la lista, se aplica la primera regla coincidente en la lista siguiente. Si no se usa ninguna coincidencia de regla, el argumento sin modificar.

1. Si el tipo de argumento es un tipo compuesto cuyo tamaño no se puede determinar estáticamente por el llamador y destinatario de la llamada, el argumento se copia en memoria y el argumento se reemplaza por un puntero a la copia. (No hay ningún tipo de este tipo en C o C++, pero existen en otros idiomas o en las extensiones de lenguaje).

1. Si el tipo de argumento es un HFA o un HVA y, después, se usa el argumento sin modificar.

1. Si el tipo de argumento es un tipo compuesto mayores de 16 bytes, a continuación, el argumento se copia a la memoria asignada por el llamador y el argumento se reemplaza por un puntero a la copia.

1. Si el tipo de argumento es un tipo compuesto, el tamaño del argumento se redondea al múltiplo más cercano de 8 bytes.

### <a name="stage-c--assignment-of-arguments-to-registers-and-stack"></a>Fase C: asignación de argumentos a registros y la pila

Para cada argumento de la lista, las reglas siguientes se aplican a su vez, hasta que se ha asignado el argumento. Cuando un argumento se asigna a un registro, los bits no utilizados en el registro han sin especificar valor. Si un argumento se asigna a un espacio de pila, los bytes de relleno no utilizados han sin especificar valor.

1. Si el argumento es una mitad-, único, doble o punto flotante de precisión de cuatro o tipo de Vector corto y el NSRN es menor que 8, el argumento se asigna a los bits menos significativos del registro v\[NSRN]. El NSRN se incrementa en uno. Ahora se ha asignado el argumento.

1. Si el argumento es un HFA o un HVA y hay suficiente SIMD sin asignar y registros de punto flotante (NSRN + número de miembros superior a 8), el argumento se asigna a SIMD y registros de punto flotante, un registro por cada miembro del HFA o HVA. El NSRN se incrementa en el número de registros empleado. Ahora se ha asignado el argumento.

1. Si el argumento es un HFA o un HVA, a continuación, el NSRN está establecido en 8 y el tamaño del argumento se redondea al múltiplo más cercano de 8 bytes.

1. Si el argumento es un HFA, un HVA, un tipo de Vector corto o de punto flotante de precisión de cuatro, entonces la NSAA se redondea hasta el mayor de 8 o la alineación Natural del tipo del argumento.

1. Si el argumento es un tipo de punto flotante de precisión mitad o simple, a continuación, el tamaño del argumento se establece en 8 bytes. El efecto es como si tuviera el argumento se han copiado para los bits menos significativos de un registro de 64 bits, y los bits restantes se rellenan con valores no especificados.

1. Si el argumento es un HFA, un HVA, mitad-, Single-, Double- o punto flotante de precisión de cuatro o tipo de Vector corto y luego el argumento se copia en memoria en la NSAA ajustada. La NSAA se incrementará en función del tamaño del argumento. Ahora se ha asignado el argumento.

1. Si el argumento es un entero o un tipo de puntero, el tamaño del argumento es menor o igual a 8 bytes y el NGRN es menor que 8, el argumento se copia en los bits menos significativos de x\[NGRN]. El NGRN se incrementa en uno. Ahora se ha asignado el argumento.

1. Si el argumento tiene una alineación de 16, el NGRN se redondea al siguiente número par.

1. Si el argumento es un tipo entero, el tamaño del argumento es igual a 16 y la NGRN es inferior a 7, el argumento se copia a x\[NGRN] y x\[NGRN + 1]. x\[NGRN] debe contener el inferior direccionado doble palabra de la representación de memoria del argumento. El NGRN se incrementa en dos. Ahora se ha asignado el argumento.

1. Si el argumento es un tipo compuesto y el tamaño en palabras dobles del argumento es no más de 8 menos NGRN, el argumento se copia en los registros de uso general consecutivos, empezando por x\[NGRN]. El argumento se pasa como si se hubieran cargado en los registros desde una dirección alineada de palabra doble, con una secuencia de instrucciones de LDR que carga registros consecutivos de la memoria adecuada. El contenido de todas las partes no utilizadas de los registros no se especifica este estándar. El NGRN se incrementa en el número de registros empleado. Ahora se ha asignado el argumento.

1. El NGRN está establecido en 8.

1. La NSAA se redondea hasta el mayor de 8 o la alineación Natural del tipo del argumento.

1. Si el argumento es un tipo compuesto, el argumento se copia en la memoria en la NSAA ajustada. La NSAA se incrementará en función del tamaño del argumento. Ahora se ha asignado el argumento.

1. Si el tamaño del argumento es menor que 8 bytes, a continuación, el tamaño del argumento se establece en 8 bytes. El efecto es como si el argumento se copia a los bits menos significativos de un registro de 64 bits, y los bits restantes se rellenaron con los valores no especificados.

1. El argumento se copia en memoria en la NSAA ajustada. La NSAA se incrementará en función del tamaño del argumento. Ahora se ha asignado el argumento.

### <a name="addendum-variadic-functions"></a>Anexo: Funciones Variádicas

Las funciones que toman un número variable de argumentos se controlan de forma diferente a anterior, como sigue:

1. Todos los compuestos se tratan igual; ningún tratamiento especial de HFAs o HVAs.

1. No se usan para SIMD y los registros de punto flotante.

De hecho, es el mismo que las reglas siguientes C.12–C.15 asignar argumentos a una pila imaginaria, donde se cargan los primeros 64 bytes de la pila en x0 x7 y cualquier otro argumento de pila se coloca normalmente.

## <a name="return-values"></a>Valores devueltos

Se devuelven los valores enteros en x0.

Valores de punto flotante se devuelven en s0, d0/v0 según corresponda.

Tipos devueltos por el valor se tratan de forma diferente dependiendo de si tienen algunas propiedades. Tipos que tienen todas estas propiedades,

- son *agregado* C ++ 14 estándar definición, es decir, tienen ningún constructor proporcionado por el usuario, ningún miembro de datos no estático privado o protegido, ninguna clase base y no hay funciones virtuales, y
- tienen un operador de asignación de copia trivial, y
- tienen un destructor trivial,

Use el siguiente estilo devuelto:

- Tipos de menor o igual a 8 bytes se devuelven en x0.
- Tipos de menor o igual que 16 bytes se devuelven en x0 y x1 con x0 que contiene los 8 bytes de orden inferior.
- Para los tipos mayores de 16 bytes, el llamador reservará un bloque de memoria de tamaño suficiente y la alineación para contener el resultado. La dirección del bloque de memoria debe pasarse como un argumento adicional a la función de x8. El destinatario puede modificar el bloque de memoria de resultados en cualquier momento durante la ejecución de la subrutina. El destinatario no es necesario conservar el valor almacenado en x8.

Todos los demás tipos usan esta convención:

- El llamador reservará de un bloque de memoria de tamaño suficiente y la alineación para contener el resultado. La dirección del bloque de memoria debe pasarse como un argumento adicional a la función de x0 o x1 si $ se pasa en x0. El destinatario puede modificar el bloque de memoria de resultados en cualquier momento durante la ejecución de la subrutina. El destinatario devuelve la dirección del bloque de memoria en x0.

## <a name="stack"></a>Pila

Las siguientes ABI RAS mediante ARM, la pila debe permanecer 16 bytes alineados en todo momento. AArch64 contiene una característica de hardware que genera errores de alineación de pila cada vez que el SP no es la alineación de 16 bytes y se realiza una carga de SP relativa o store. Windows se ejecuta con esta característica está habilitada en todo momento.

Las funciones que asignan 4k o más valorados de pila deben asegurarse de que cada página antes de la página final se toca en orden. Esta acción garantiza que ningún código pueda "saltarse" las páginas de protección que Windows usa para expandir la pila. Normalmente, el toque se realiza mediante el `__chkstk` auxiliar, que tiene una convención de llamada personalizada que pasa la asignación de pila total dividida por 16 en x15.

## <a name="red-zone"></a>Zona roja

El área de 16 bytes inmediatamente debajo el puntero de pila actual está reservada para su uso por el análisis y dinámica de escenarios de aplicación de revisiones. Esta área permite que el código generado con cuidado para insertarse que almacena dos registros en [sp, #-16] usa temporalmente con fines arbitrarios. El kernel de Windows garantiza que los 16 bytes no se sobrescriben si se toma una excepción o interrupción, en el modo de usuario y kernel.

## <a name="kernel-stack"></a>Pila de kernel

La pila de modo kernel predeterminada en Windows es seis páginas (24k). Preste atención adicional a las funciones con búferes de pila de gran tamaño en modo kernel. Una interrupción inoportuno podría estar en contacto con poco espacio en cabeza y crear una comprobación de errores de pánico de pila.

## <a name="stack-walking"></a>El recorrido de pila

Código dentro de Windows se compila con punteros de marco habilitados ([/Oy-](reference/oy-frame-pointer-omission.md)) para habilitar el recorrido de pila rápidos. Por lo general, x29 (fp) apunta al siguiente vínculo de la cadena, que es un {fp, lr} par, que indica el puntero al fotograma anterior en la pila y la dirección de retorno. Se recomienda establecer código de terceros para habilitar los punteros de marcos, para permitir la generación de perfiles mejorada y seguimiento.

## <a name="exception-unwinding"></a>Desenredado en excepciones

Desenredo durante el control de excepciones es asistido mediante el uso de códigos de desenredado. Los códigos de desenredado son una secuencia de bytes almacenados en la sección .xdata de la aplicación ejecutable. Describen la operación del prólogo y epílogo de forma abstracta, tal que los efectos del prólogo de una función se pueden deshacer como preparación para la copia de seguridad hasta el marco de pila del llamador. Para obtener más información sobre los códigos de desenredado, consulte [ARM64 excepciones](arm64-exception-handling.md).

La EABI de ARM también especifica un modelo de desenredado en excepciones que usa códigos de desenredado. Sin embargo, la especificación tal como se presenta es insuficiente para el desenredado en Windows, donde se deben controlar casos donde el equipo está en medio de un prólogo de función y el epílogo.

Debe describirse con tablas de función dinámica a través de código que se genera dinámicamente `RtlAddFunctionTable` y funciones asociadas, por lo que el código generado podrá participar en el control de excepciones.

## <a name="cycle-counter"></a>Contador de ciclos

Todas las CPU de ARMv8 son necesarios para admitir un contador de ciclos registrar un registro de 64 bits que configura Windows para que sean legibles en cualquier nivel de la excepción, incluido el modo de usuario. Se puede acceder a través de la PMCCNTR_EL0 especial registrar, utilizando el código de operación MSR en código de ensamblado, o el `_ReadStatusReg` intrínsecas en el código de C o C++.

El contador de ciclos aquí es un contador de ciclos auténtico, no un reloj de pared. La frecuencia de recuento varía según la frecuencia del procesador. Si cree que debe conocer la frecuencia del ciclo de contador, no debería usar el contador de ciclos. En su lugar, desea medir el tiempo de reloj, en los que debe usar `QueryPerformanceCounter`.

## <a name="see-also"></a>Vea también

[Problemas comunes de migración de ARM en Visual C++](common-visual-cpp-arm-migration-issues.md)<br/>
[Control de excepciones ARM64](arm64-exception-handling.md)
