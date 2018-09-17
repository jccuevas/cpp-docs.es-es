---
title: Problemas comunes de migración de ARM de Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0f4c434e-0679-4331-ba0a-cc15dd435a46
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0e42cd14c5707f728f5577a77b2dd613c5ef2a0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709623"
---
# <a name="common-visual-c-arm-migration-issues"></a>Problemas comunes de migración de ARM en Visual C++

Cuando se usa Microsoft Visual C++ (MSVC), el mismo código fuente de C++ puede producir resultados diferentes en la arquitectura ARM superior que en las arquitecturas x86 o x64.

## <a name="sources-of-migration-issues"></a>Orígenes de problemas de migración

Muchos problemas que pueden surgir al migrar código desde las arquitecturas x86 o x64 a la arquitectura ARM están relacionados con las construcciones de código fuente que pueden invocar un comportamiento indefinido, definido por la implementación o no especificado.

*Un comportamiento indefinido* es el comportamiento que no define el estándar de C++ y que se debe a una operación que no tiene ningún resultado razonable: por ejemplo, convertir un valor de punto flotante a entero sin signo, o cuando se desplaza un valor por un número de posiciones que es negativo o supera el número de bits en su tipo promovido.

*Comportamiento definido por la implementación* es el comportamiento que el estándar de C++ requiere que el proveedor del compilador definir y documentar. Un programa puede confiar en el comportamiento definido por la implementación, aunque si lo hace, podría no ser portátil. Ejemplos de comportamiento definido por la implementación incluyen los tamaños de tipos de datos integrados y los requisitos de alineación. Un ejemplo de una operación que podría verse afectado por el comportamiento definido por la implementación tiene acceso a la lista de argumentos de variable.

*No se especifica el comportamiento* es el comportamiento que el estándar de C++ deja intencionadamente no determinista. Aunque el comportamiento se considera no determinista, invocaciones particulares de un comportamiento no especificado se determinan mediante la implementación del compilador. Sin embargo, hay ningún requisito para un proveedor de compilador determinar por adelantado el resultado o garantizar un comportamiento coherente entre las invocaciones comparables, y no hay ningún requisito para la documentación. Un ejemplo de un comportamiento no especificado es el orden en que se evalúan las subexpresiones, que incluyen argumentos de una llamada de función.

Otros problemas de migración se pueden atribuir a las diferencias de hardware entre ARM y arquitecturas x86 o x64 que interactúan con el estándar de C++ de forma diferente. Por ejemplo, se proporciona el modelo de memoria seguro de la arquitectura x86 y x64 `volatile`-calificado variables algunas propiedades adicionales que se usaron para facilitar ciertos tipos de comunicación entre subprocesos en el pasado. Pero el modelo de memoria débil de la arquitectura ARM no admite este uso ni lo el estándar de C++ requiere.

> [!IMPORTANT]
>  Aunque `volatile` ganancias algunas propiedades que pueden utilizarse para implementar formas limitadas de comunicación entre subprocesos en x86 y x64, estas propiedades adicionales no son suficientes para implementar entre subprocesos comunicación en general. El estándar de C++, se recomienda que dicha comunicación se implementa mediante el uso de primitivas de sincronización adecuado en su lugar.

Porque distintas plataformas podrían expresar estos tipos de comportamiento de manera diferente, la migración de software entre plataformas puede resultar difícil y propenso a errores si depende del comportamiento de una plataforma específica. Aunque muchos de estos tipos de comportamiento pueden observarse y pueden aparecer estables, confiar en ellos es al menos no portátil y en el caso de un comportamiento indefinido o no especificado, también es un error. Incluso el comportamiento que se mencionan en este documento no debe confiar en y podría cambiar en futuras implementaciones de CPU o los compiladores.

## <a name="example-migration-issues"></a>Problemas de migración de ejemplo

El resto de este documento describe cómo el comportamiento diferente de estos elementos del lenguaje C++ puede generar resultados diferentes en distintas plataformas.

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>Conversión de punto flotante a entero sin signo

En la arquitectura ARM, conversión de un valor de punto flotante en un entero de 32 bits se satura al valor más cercano que puede representar el entero si el valor de punto flotante está fuera del intervalo que puede representar el entero. En las arquitecturas x86 y x64, la conversión se ajusta a si el entero es sin signo o si está firmado el entero se establece en -2147483648. Ninguna de estas arquitecturas admite directamente la conversión de valores de punto flotante a tipos enteros más pequeños; en su lugar, se realizan las conversiones a 32 bits, y los resultados se truncan a un tamaño menor.

Para la arquitectura ARM, la combinación de saturación y truncamiento significa que la conversión a tipos sin signo correctamente satura tipos sin signo más pequeños cuando se satura un entero de 32 bits, pero genera un resultado truncado para valores mayores que el pueden representar tipos más pequeños, pero demasiado pequeño para saturar el entero de 32 bits. Conversión también se satura correctamente para los enteros con signo de 32 bits, pero da como resultado un truncamiento de enteros con signo, saturados en -1 para los valores de forma positiva saturado y 0 para valores saturado negativamente. Conversión a un entero con signo más pequeño produzca un resultado truncado es imprevisible.

Para las arquitecturas x86 y x64, la combinación de comportamiento circulares para las conversiones de entero sin signo y valoración explícita para las conversiones de entero con signo en caso de desbordamiento, junto con el truncamiento, hacer que los resultados de la mayoría de turnos impredecibles si están demasiado grande.

Estas plataformas también difieren en cómo controlan la conversión de NaN (Not a Number) en tipos enteros. En ARM, NaN se convierte en 0 x 00000000; x86 y x64, lo convierte en 0 x 80000000.

Conversión de punto flotante solo se puede confiar en si sabe que el valor está dentro del intervalo del que se va a convertir a tipo entero.

### <a name="shift-operator---behavior"></a>Operador de desplazamiento (\< \< >>) comportamiento

En la arquitectura ARM, un valor se puede cambiar izquierda o derecha hasta 255 bits antes de que comience el patrón que se repita. En las arquitecturas x86 y x64, el patrón se repite en cada múltiplo de 32 a menos que el origen del patrón es una variable de 64 bits; en ese caso, el patrón se repite en cada múltiplo de 64 x 64 y cada múltiplo de 256 en x86, donde se emplea una implementación de software. Por ejemplo, para una variable de 32 bits que tiene un valor de 1 desplazado a 32 posiciones a la izquierda, en ARM, el resultado es 0, en x86 el resultado es 1, y en x64 el resultado también es 1. Sin embargo, si el origen del valor es una variable de 64 bits, a continuación, el resultado en las tres plataformas 4294967296, y el valor no "ajustarse" hasta que se ha desplazado a 64 posiciones en x64 o 256 posiciones en ARM y x86.

Dado que el resultado de una operación de desplazamiento que supera el número de bits del tipo de origen no está definido, el compilador no debe tener un comportamiento coherente en todas las situaciones. Por ejemplo, si ambos operandos de un desplazamiento se conocen en tiempo de compilación, el compilador puede optimizar el programa mediante una rutina interna para calcular previamente el resultado de la tecla MAYÚS y, a continuación, sustituyendo el resultado en lugar de la operación de desplazamiento. Si la cantidad de desplazamiento es demasiado grande o negativo, el resultado de la rutina interno puede ser diferente que el resultado de la misma expresión de desplazamiento ejecutado por la CPU.

### <a name="variable-arguments-varargs-behavior"></a>Comportamiento de argumentos de variable (varargs)

En la arquitectura ARM, parámetros de la lista de argumentos de variable que se pasan en la pila están sujetos a alineación. Por ejemplo, un parámetro de 64 bits se alinea en un límite de 64 bits. En x86 y x64, argumentos que se pasan en la pila no están sujetos a la alineación y el módulo estrechamente. Esta diferencia puede provocar una función variádica como `printf` para leer las direcciones de memoria que se esperaba como relleno en ARM si el diseño de la lista de argumentos de variable esperado no coincide exactamente, aunque es posible que funcione para un subconjunto de algunos valores en el x86 o x64 arquitecturas. Considere este ejemplo:

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will “parse” the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

En este caso, el error puede corregirse asegurándose de que se usa la especificación de formato correcto para que se considera la alineación del argumento. Este código es correcto:

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>Orden de evaluación del argumento

Dado que ARM, x 86 y x64 son tan diferentes procesadores, presentan diferentes requisitos para las implementaciones del compilador y también distintas formas de realizar las optimizaciones. Por este motivo, junto con otros factores como la configuración de convención de llamada y optimización, un compilador puede evaluar los argumentos de función en un orden diferente en distintas arquitecturas o cuando se cambian los otros factores. Esto puede causar el comportamiento de una aplicación que se basa en un orden de evaluación concreto para cambiar de forma inesperada.

Este tipo de error puede producirse cuando los argumentos a una función tienen efectos secundarios que afectan a otros argumentos para la función en la misma llamada. Normalmente, es fácil evitar este tipo de dependencia, pero a veces se puede oscurecida por las dependencias que son difíciles de distinguir, o mediante la sobrecarga de operadores. Tenga en cuenta este ejemplo de código:

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

Esto parece bien definido, pero si `->` y `*` son los operadores sobrecargados, a continuación, este código se traduce a algo similar a esto:

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

Y si hay una dependencia entre `operator->(memory_handle)` y `operator*(p)`, el código podría depender de un orden de evaluación concreto, aunque el código original es similar a no hay ninguna dependencia posibles.

### <a name="volatile-keyword-default-behavior"></a>comportamiento predeterminado de palabra clave volatile

El compilador de MSVC admite dos diferentes interpretaciones de las `volatile` calificador de almacenamiento que se puede especificar mediante el uso de modificadores de compilador. El [/volatile: MS](../build/reference/volatile-volatile-keyword-interpretation.md) conmutador selecciona extendida semántica volátil que garantice la ordenación fuerte, tal como ha sido el caso tradicional para x86 y x64 debido al modelo de memoria seguro en esas arquitecturas de Microsoft. El [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) conmutador selecciona el C++ estándar volátil semántica estricta que no garantice la ordenación seguro.

En la arquitectura ARM, el valor predeterminado es **/volatile: ISO** dado procesadores ARM tienen un débilmente ordenan el modelo de memoria, así como software ARM no presenta un legado de depender de la semántica de extendido  **/volatile: MS** y normalmente no tiene para interactuar con el software que realiza. Sin embargo, resulta todavía a veces es conveniente o incluso necesario para compilar un programa ARM para usar la semántica extendida. Por ejemplo, puede ser demasiado costosa portar un programa que se utilizan la semántica de ISO C++, o podría tener software de controlador que se adhiere a la semántica tradicional para funcionar correctamente. En estos casos, puede usar el **/volatile: MS** conmutador; sin embargo, para volver a crear la semántica volátil tradicionales en los destinos ARM, el compilador debe insertar las barreras de memoria en torno a cada lectura o escritura de un `volatile` variable para aplicar ordenación seguro, que puede tener un impacto negativo en el rendimiento.

En las arquitecturas x86 y x64, el valor predeterminado es **/volatile: MS** porque gran parte del software que ya se ha creado para estas arquitecturas mediante el uso de MSVC se basa en ellos. Al compilar programas x86 y x64, puede especificar el **/volatile: ISO** conmutador para ayudar a evitar la dependencia innecesaria de la semántica volátil tradicional y promover la portabilidad.

## <a name="see-also"></a>Vea también

[Configuración de Visual C++ para procesadores ARM](../build/configuring-programs-for-arm-processors-visual-cpp.md)
