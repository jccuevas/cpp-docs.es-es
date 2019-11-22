---
title: Problemas comunes de migración de ARM en Visual C++
ms.date: 05/06/2019
ms.assetid: 0f4c434e-0679-4331-ba0a-cc15dd435a46
ms.openlocfilehash: 518b8872b301a8fcfc0f154cb3d5d0299efb0975
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303229"
---
# <a name="common-visual-c-arm-migration-issues"></a>Problemas comunes de migración de ARM en Visual C++

Al usar el compilador de Microsoft C++ (MSVC) C++ , el mismo código fuente puede producir resultados diferentes en la arquitectura ARM que en las arquitecturas x86 o x64.

## <a name="sources-of-migration-issues"></a>Orígenes de problemas de migración

Muchos problemas que pueden surgir al migrar código de las arquitecturas x86 o x64 a la arquitectura ARM están relacionados con las construcciones de código fuente que pueden invocar un comportamiento no definido, definido por la implementación o no especificado.

El *comportamiento no definido* es el comportamiento C++ que no define el estándar y que se debe a una operación que no tiene ningún resultado razonable: por ejemplo, al convertir un valor de punto flotante en un entero sin signo o al desplazar un valor por un número de posiciones que es negativo o supera el número de bits de su tipo promocionado.

El comportamiento *definido por la implementación* es el C++ comportamiento que requiere el proveedor del compilador para definir y documentar. Un programa puede basarse de forma segura en el comportamiento definido por la implementación, aunque es posible que no sea portátil. Entre los ejemplos de comportamiento definido por la implementación se incluyen los tamaños de los tipos de datos integrados y sus requisitos de alineación. Un ejemplo de una operación que podría verse afectada por el comportamiento definido por la implementación es el acceso a la lista de argumentos variables.

Un *comportamiento no especificado* es el comportamiento C++ que el estándar deja intencionadamente no determinista. Aunque el comportamiento se considera no determinista, las invocaciones particulares de un comportamiento no especificado se determinan mediante la implementación del compilador. Sin embargo, no hay ningún requisito para que un proveedor del compilador determine el resultado o garantice un comportamiento coherente entre las invocaciones comparables y no hay ningún requisito para la documentación. Un ejemplo de comportamiento sin especificar es el orden en el que se evalúan las subexpresiones, que incluyen argumentos para una llamada de función.

Otros problemas de migración se pueden atribuir a diferencias de hardware entre las arquitecturas ARM y x86 o x64 C++ que interactúan con el estándar de forma diferente. Por ejemplo, el modelo de memoria fuerte de la arquitectura x86 y x64 proporciona a las variables calificadas en `volatile`algunas propiedades adicionales que se han usado para facilitar determinados tipos de comunicación entre subprocesos en el pasado. Sin embargo, el modelo de memoria débil de la arquitectura ARM no es compatible con C++ este uso, ni lo requiere el estándar.

> [!IMPORTANT]
>  Aunque `volatile` obtiene algunas propiedades que se pueden usar para implementar formas limitadas de comunicación entre subprocesos en x86 y x64, estas propiedades adicionales no son suficientes para implementar la comunicación entre subprocesos en general. El C++ estándar recomienda que, en su lugar, se implemente la comunicación mediante primitivas de sincronización apropiadas.

Dado que distintas plataformas pueden expresar de forma diferente estos tipos de comportamiento, el traslado de software entre plataformas puede resultar difícil y propenso a errores si depende del comportamiento de una plataforma específica. Aunque muchos de estos tipos de comportamiento se pueden observar y podrían parecer estables, confiar en ellos es al menos no portable y, en los casos de comportamiento sin definir o no especificado, también es un error. Incluso el comportamiento que se menciona en este documento no debe basarse en y podría cambiar en compiladores futuros o implementaciones de CPU.

## <a name="example-migration-issues"></a>Ejemplo de problemas de migración

En el resto de este documento se describe cómo el comportamiento diferente C++ de estos elementos de lenguaje puede generar resultados diferentes en distintas plataformas.

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>Conversión de punto flotante a entero sin signo

En la arquitectura ARM, la conversión de un valor de punto flotante en un entero de 32 bits se satura al valor más próximo que el entero puede representar si el valor de punto flotante está fuera del intervalo que el entero puede representar. En las arquitecturas x86 y x64, la conversión se ajusta si el entero está sin signo o se establece en-2147483648 si el entero está firmado. Ninguna de estas arquitecturas admite directamente la conversión de valores de punto flotante en tipos enteros más pequeños; en su lugar, las conversiones se realizan en 32 bits y los resultados se truncan a un tamaño menor.

En la arquitectura ARM, la combinación de saturación y truncamiento significa que la conversión a tipos sin signo satura correctamente los tipos sin signo más pequeños cuando satura un entero de 32 bits, pero genera un resultado truncado para los valores que son mayores que el valor de un tipo más pequeño puede representar pero demasiado pequeño para saturar el entero de 32 bits completo. La conversión también se satura correctamente para los enteros con signo de 32 bits, pero el truncamiento de los enteros con signo saturados es-1 para los valores de saturación positiva y 0 para los valores saturados negativamente. La conversión a un entero con signo más pequeño genera un resultado truncado que es imprevisible.

En el caso de las arquitecturas x86 y x64, la combinación de comportamiento de ajuste para las conversiones de enteros sin signo y la valoración explícita de las conversiones de enteros con signo en desbordamiento, junto con truncamiento, hacen que los resultados de la mayoría de los cambios sean imprevisibles si son demasiado grande.

Estas plataformas también difieren en cómo controlan la conversión de NaN (no un número) a tipos enteros. En ARM, NaN convierte en 0x00000000; en x86 y x64, se convierte en 0x80000000.

Solo se puede confiar en la conversión de punto flotante si sabe que el valor está dentro del intervalo del tipo de entero al que se está convirtiendo.

### <a name="shift-operator---behavior"></a>Comportamiento del operador de desplazamiento (\<\< > >)

En la arquitectura ARM, un valor se puede desplazar a la izquierda o a la derecha hasta 255 bits antes de que el patrón empiece a repetirse. En las arquitecturas x86 y x64, el patrón se repite en cada múltiplo de 32 a menos que el origen del patrón sea una variable de 64 bits; en ese caso, el patrón se repite en cada múltiplo de 64 en x64 y cada múltiplo de 256 en x86, donde se emplea una implementación de software. Por ejemplo, en el caso de una variable de 32 bits que tiene un valor de 1 desplazado a la izquierda en posiciones 32, en ARM el resultado es 0, en x86 el resultado es 1 y, en x64, el resultado también es 1. Sin embargo, si el origen del valor es una variable de 64 bits, el resultado en las tres plataformas es 4294967296 y el valor no se "ajustará" hasta que se desplacen 64 posiciones en x64 o 256 en ARM y x86.

Dado que el resultado de una operación de desplazamiento que supera el número de bits en el tipo de origen es indefinido, no es necesario que el compilador tenga un comportamiento coherente en todas las situaciones. Por ejemplo, si los dos operandos de un turno se conocen en tiempo de compilación, el compilador puede optimizar el programa mediante una rutina interna para calcular previamente el resultado del cambio y sustituir el resultado en lugar de la operación de desplazamiento. Si la cantidad de desplazamiento es demasiado grande o negativo, el resultado de la rutina interna podría ser diferente del resultado de la misma expresión de desplazamiento que la que ejecuta la CPU.

### <a name="variable-arguments-varargs-behavior"></a>Comportamiento de los argumentos de variable (varargs)

En la arquitectura de ARM, los parámetros de la lista de argumentos de variable que se pasan en la pila están sujetos a alineación. Por ejemplo, un parámetro de 64 bits está alineado en un límite de 64 bits. En x86 y x64, los argumentos que se pasan en la pila no están sujetos a la alineación y al módulo. Esta diferencia puede dar lugar a que una función variádicas como `printf` Lea las direcciones de memoria que se pretendían como relleno en ARM si el diseño esperado de la lista de argumentos variables no coincide exactamente, aunque podría funcionar para un subconjunto de algunos valores en las arquitecturas x86 o x64. Considere este ejemplo:

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will "parse" the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

En este caso, el error se puede corregir asegurándose de que se usa la especificación de formato correcta para que se considere la alineación del argumento. Este código es correcto:

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>Orden de evaluación de argumentos

Dado que los procesadores ARM, x86 y x64 son tan diferentes, pueden presentar requisitos diferentes para las implementaciones del compilador y también diferentes oportunidades para las optimizaciones. Debido a esto, junto con otros factores, como la configuración de la Convención de llamada y la optimización, un compilador puede evaluar los argumentos de la función en un orden diferente en las distintas arquitecturas o cuando se cambian los otros factores. Esto puede hacer que el comportamiento de una aplicación que se basa en un determinado orden de evaluación cambie de forma inesperada.

Este tipo de error puede producirse si los argumentos de una función tienen efectos secundarios que afectan a otros argumentos a la función en la misma llamada. Normalmente, este tipo de dependencia es fácil de evitar, pero a veces puede verse oscurecida por dependencias difíciles de discernir o por la sobrecarga de operadores. Considere este ejemplo de código:

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

Esto aparece bien definido, pero si `->` y `*` son operadores sobrecargados, este código se convierte en algo similar a esto:

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

Y si hay una dependencia entre `operator->(memory_handle)` y `operator*(p)`, el código podría basarse en un determinado orden de evaluación, aunque el código original parezca que no hay ninguna dependencia posible.

### <a name="volatile-keyword-default-behavior"></a>comportamiento predeterminado de la palabra clave volatile

El compilador MSVC admite dos interpretaciones diferentes del calificador de almacenamiento `volatile` que puede especificar mediante modificadores de compilador. El modificador [/volatile: MS](reference/volatile-volatile-keyword-interpretation.md) selecciona la semántica volátil extendida de Microsoft que garantiza una ordenación sólida, como es el caso tradicional para x86 y x64 debido al sólido modelo de memoria en esas arquitecturas. El modificador [/volatile: ISO](reference/volatile-volatile-keyword-interpretation.md) selecciona la C++ semántica volátil estándar estricta que no garantiza una ordenación sólida.

En la arquitectura ARM, el valor predeterminado es **/volatile: ISO** porque los procesadores ARM tienen un modelo de memoria de ordenación débil, y dado que el software ARM no tiene una herencia heredada de la semántica extendida de **/volatile: MS** y no suele tener que interactuar con el software que lo hace. Sin embargo, a veces sigue siendo conveniente o incluso necesario compilar un programa ARM para usar la semántica extendida. Por ejemplo, puede que el traslado de un programa sea demasiado costoso para usar la semántica C++ ISO, o que el software de controlador tenga que adherirse a la semántica tradicional para que funcione correctamente. En estos casos, puede usar el modificador **/volatile: MS** ; sin embargo, para volver a crear la semántica volátil tradicional en destinos ARM, el compilador debe insertar barreras de memoria alrededor de cada lectura o escritura de una variable `volatile` para aplicar una ordenación segura, lo que puede tener un impacto negativo en el rendimiento.

En las arquitecturas x86 y x64, el valor predeterminado es **/volatile: MS** porque gran parte del software que ya se ha creado para estas arquitecturas mediante MSVC se basa en ellos. Al compilar programas x86 y x64, puede especificar el modificador **/volatile: ISO** para evitar una dependencia innecesaria de la semántica volátil tradicional y para promover la portabilidad.

## <a name="see-also"></a>Vea también

[Configuración de Visual C++ para procesadores ARM](configuring-programs-for-arm-processors-visual-cpp.md)
