---
title: Problemas comunes de migración de ARM en Visual C++
ms.date: 05/06/2019
ms.assetid: 0f4c434e-0679-4331-ba0a-cc15dd435a46
ms.openlocfilehash: 2c29b4ffa5344b309622314970ce52c47a0ebd05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328798"
---
# <a name="common-visual-c-arm-migration-issues"></a>Problemas comunes de migración de ARM en Visual C++

Al usar el compilador de Microsoft C++ (MSVC), el mismo código fuente de C++ puede producir resultados diferentes en la arquitectura ARM con respecto a las arquitecturas x86 o x64.

## <a name="sources-of-migration-issues"></a>Fuentes de problemas de migración

Muchos de los problemas que pueden surgir al migrar código de las arquitecturas x86 o x64 a la arquitectura ARM están relacionados con las construcciones de código fuente que pueden invocar un comportamiento no definido, definido por la implementación o no especificado.

Un *comportamiento no definido* es aquel que el estándar de C++ no define y que se debe a una operación que no tiene ningún resultado razonable, como convertir un valor de punto flotante en un entero sin signo, o desplazar un valor un número de posiciones negativo o que supera el número de bits en su tipo promovido.

Un *comportamiento definido por la implementación* es aquel que el estándar de C++ requiere que el proveedor del compilador defina y documente. Un programa puede basarse de forma segura en el comportamiento definido por la implementación, aunque es posible que no sea portable. Entre los ejemplos de comportamiento definido por la implementación se incluyen los tamaños de los tipos de datos integrados y sus requisitos de alineación. Una operación que podría verse afectada por el comportamiento definido por la implementación es el acceso a la lista de argumentos de variable.

Un *comportamiento no especificado* es aquel que el estándar de C++ deja intencionadamente como no determinista. Aunque el comportamiento se considera no determinista, las invocaciones particulares de un comportamiento no especificado se determinan mediante la implementación del compilador. Aun así, no es necesario que un proveedor del compilador determine de antemano el resultado o garantice un comportamiento coherente entre invocaciones comparables y no hay ningún requisito relativo a la documentación. Un ejemplo de comportamiento sin especificar es el orden en el que se evalúan las subexpresiones, que incluyen argumentos para una llamada de función.

Otros problemas de migración se pueden atribuir a diferencias de hardware entre las arquitecturas ARM y x86 o x64 que interactúan con el estándar de C++ de forma diferente. Por ejemplo, el modelo de memoria fuerte de la arquitectura x86 y x64 proporciona a las variables calificadas para `volatile` algunas propiedades adicionales que se usaban para facilitar ciertos tipos de comunicación entre subprocesos en el pasado. Aun así, el modelo de memoria débil de la arquitectura ARM no es compatible con este uso, que el estándar de C++ no requiere.

> [!IMPORTANT]
> Aunque `volatile` obtiene algunas propiedades que se pueden usar para implementar formas limitadas de comunicación entre subprocesos en x86 y x64, estas propiedades adicionales no son suficientes para implementar la comunicación entre subprocesos en general. El estándar de C++ recomienda que la comunicación se implemente mediante primitivas de sincronización apropiadas.

Dado que las distintas plataformas pueden expresar estos tipos de comportamiento de forma diferente, el traslado de software entre plataformas puede resultar difícil y ser propenso a errores si depende del comportamiento de una plataforma específica. Aunque se pueden observar muchos de estos tipos de comportamiento y podrían parecer estables, confiar en ellos es, como mínimo, no portable. Además, en el caso de los comportamientos sin definir o no especificados, también es un error. Ni siquiera se recomienda basarse en el comportamiento que se menciona en este documento, que podría cambiar en el futuro en compiladores o implementaciones de CPU.

## <a name="example-migration-issues"></a>Ejemplos de problemas de migración

En el resto de este documento se describe la manera en que el comportamiento diferente de estos elementos del lenguaje de C++ puede generar resultados distintos en diversas plataformas.

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>Conversión de punto flotante a entero sin signo

En la arquitectura ARM, la conversión de un valor de punto flotante a un entero de 32 bits se satura al valor más próximo que el entero puede representar si el valor de punto flotante está fuera del intervalo que el entero puede representar. En las arquitecturas x86 y x64, la conversión se ajusta si el entero es sin signo, o si se establece en -2147483648 en caso de que sea un entero con signo. Ninguna de estas arquitecturas admite directamente la conversión de valores de punto flotante a tipos enteros más pequeños. En su lugar, las conversiones se realizan a 32 bits y los resultados se truncan a un tamaño menor.

En la arquitectura ARM, la combinación de saturación y truncamiento significa que la conversión a tipos sin signo satura correctamente los tipos sin signo más pequeños cuando se satura un entero de 32 bits, pero se genera un resultado truncado para los valores mayores de lo que el tipo más pequeño puede representar, pero demasiado pequeños para saturar el entero de 32 bits completo. La conversión también se satura correctamente para los enteros con signo de 32 bits, pero el truncamiento de los enteros con signo saturados genera -1 para los valores con saturación positiva y 0 para los valores con saturación negativa. La conversión a un entero con signo más pequeño genera un resultado truncado imprevisible.

Para las arquitecturas x86 y x64, la combinación del comportamiento de ajuste para las conversiones de enteros sin signo y la valoración explícita de las conversiones de enteros con signo en caso de desbordamiento, junto con el truncamiento, hacen que los resultados de la mayoría de los desplazamientos sean imprevisibles si son demasiado grandes.

Estas plataformas también difieren en la manera en que controlan la conversión de NaN ("no es un número") a tipos enteros. En ARM, NaN convierte a 0x00000000; en x86 y x64, convierte a 0x80000000.

Solo es posible basarse en la conversión de punto flotante si se sabe que el valor se encuentra dentro del intervalo del tipo de entero al que se está convirtiendo.

### <a name="shift-operator---behavior"></a>Comportamiento del operador de desplazamiento (\<\< >>)

En la arquitectura ARM, se puede desplazar un valor a la izquierda o a la derecha hasta 255 bits antes de que el patrón empiece a repetirse. En las arquitecturas x86 y x64, el patrón se repite en cada múltiplo de 32, a menos que el origen del patrón sea una variable de 64 bits. En ese caso, el patrón se repite en cada múltiplo de 64 en x64 y en cada múltiplo de 256 en x86, donde se emplea una implementación de software. Por ejemplo, en el caso de una variable de 32 bits que tiene un valor de 1 desplazado a la izquierda 32 posiciones, el resultado es 0 en ARM, 1 en x86 y también 1 en x64. En cambio, si el origen del valor es una variable de 64 bits, el resultado en las tres plataformas es 4294967296 y el valor no se "ajustará" hasta que se desplace 64 posiciones en x64, o 256 posiciones en ARM y x86.

Dado que el resultado de una operación de desplazamiento que supera el número de bits del tipo de origen es indefinido, no es necesario que el compilador tenga un comportamiento coherente en todas las situaciones. Por ejemplo, si los dos operandos de un desplazamiento se conocen en tiempo de compilación, el compilador podría optimizar el programa mediante una rutina interna para calcular previamente el resultado del desplazamiento y sustituir el resultado, en lugar de la operación de desplazamiento. Si la cantidad de desplazamiento es demasiado grande o negativa, el resultado de la rutina interna podría diferir del resultado de la misma expresión de desplazamiento que ejecuta la CPU.

### <a name="variable-arguments-varargs-behavior"></a>Comportamiento de los argumentos de variable (varargs)

En la arquitectura de ARM, los parámetros de la lista de argumentos de variable que se pasan en la pila están sujetos a alineación. Por ejemplo, un parámetro de 64 bits está alineado en un límite de 64 bits. En x86 y x64, los argumentos que se pasan en la pila no están sujetos a alineación y se empaquetan sólidamente. Esta diferencia puede dar lugar a que una función variádica como `printf` lea las direcciones de memoria que estaban diseñadas como relleno en ARM si el diseño esperado de la lista de argumentos de variable no coincide exactamente, aunque podría funcionar para un subconjunto de valores en las arquitecturas x86 o x64. Considere este ejemplo:

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will "parse" the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

En este caso, el error se puede corregir si se garantiza que se usa la especificación de formato correcta para que se tenga en cuenta la alineación del argumento. Este código es correcto:

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>Orden de evaluación de argumentos

Dado que los procesadores de ARM, x86 y x64 son tan diferentes, pueden presentar requisitos distintos para las implementaciones del compilador y también diversas oportunidades para las optimizaciones. Debido a esto, y unido a otros factores, como la configuración de optimización y de la convención de llamada, un compilador puede evaluar los argumentos de función en un orden diferente en las distintas arquitecturas o cuando se cambian los otros factores. Esto puede hacer que el comportamiento de una aplicación que se basa en un determinado orden de evaluación cambie de forma inesperada.

Este tipo de error puede producirse si los argumentos de una función tienen efectos secundarios que afectan a otros argumentos de la función en la misma llamada. Normalmente, este tipo de dependencia es fácil de evitar, pero a veces puede quedar oculta por dependencias difíciles de discernir o por la sobrecarga de operador. Considere este ejemplo de código:

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

Aparece bien definido, pero si `->` y `*` son operadores sobrecargados, el código se convierte en algo similar a esto:

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

Además, si hay una dependencia entre `operator->(memory_handle)` y `operator*(p)`, el código podría basarse en un determinado orden de evaluación, aunque en el código original parezca que no hay ninguna dependencia posible.

### <a name="volatile-keyword-default-behavior"></a>Comportamiento predeterminado de la palabra clave volatile

El compilador MSVC admite dos interpretaciones diferentes del calificador de almacenamiento `volatile`, que se pueden especificar mediante modificadores del compilador. El modificador [/volatile:ms](reference/volatile-volatile-keyword-interpretation.md) selecciona la semántica volátil extendida de Microsoft que garantiza una ordenación fuerte, como es el caso tradicional de x86 y x64, debido al modelo de memoria fuerte de estas arquitecturas. El modificador [/volatile:iso](reference/volatile-volatile-keyword-interpretation.md) selecciona la semántica volátil estándar de C++ estricta, que no garantiza una ordenación fuerte.

En la arquitectura ARM, el valor predeterminado es **/volatile:iso**, debido a que los procesadores ARM tienen un modelo de memoria ordenada débil y a que el software ARM no acostumbra a basarse en la semántica extendida de **/volatile:ms** y no suele tener que interactuar con el software que sí lo hace. Aun así, a veces sigue siendo conveniente o incluso necesario compilar un programa ARM para usar la semántica extendida. Por ejemplo, puede que portar un programa para usar la semántica de C++ ISO sea demasiado costoso, o que el software de controlador tenga que adherirse a la semántica tradicional para funcionar correctamente. En estos casos, puede usar el modificador **/volatile:ms**, pero para volver a crear la semántica volátil tradicional en destinos ARM, el compilador debe insertar barreras de memoria alrededor de cada lectura o escritura de una variable `volatile` para aplicar una ordenación fuerte, lo que puede tener un impacto negativo en el rendimiento.

En las arquitecturas x86 y x64, el valor predeterminado es **/volatile:ms**, puesto que gran parte del software que ya se ha creado para estas arquitecturas mediante MSVC se basa en él. Al compilar programas x86 y x64, puede especificar el modificador **/volatile:iso** para ayudar a evitar la dependencia innecesaria de la semántica volátil tradicional y promover la portabilidad.

## <a name="see-also"></a>Vea también

[Configuración de Visual C++ para procesadores ARM](configuring-programs-for-arm-processors-visual-cpp.md)
