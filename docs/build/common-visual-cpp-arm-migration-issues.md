---
title: Problemas comunes de migración de ARM en Visual C++
ms.date: 05/06/2019
ms.assetid: 0f4c434e-0679-4331-ba0a-cc15dd435a46
ms.openlocfilehash: 2c29b4ffa5344b309622314970ce52c47a0ebd05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328798"
---
# <a name="common-visual-c-arm-migration-issues"></a>Problemas comunes de migración de ARM en Visual C++

Cuando se usa el compilador de Microsoft C++ (MSVC), el mismo código fuente De C++ puede producir resultados diferentes en la arquitectura ARM que en las arquitecturas x86 o x64.

## <a name="sources-of-migration-issues"></a>Fuentes de problemas migratorios

Muchos problemas que puede encontrar al migrar código de las arquitecturas x86 o x64 a la arquitectura ARM están relacionados con construcciones de código fuente que pueden invocar un comportamiento indefinido, definido por la implementación o no especificado.

*El comportamiento indefinido* es un comportamiento que el estándar C++ no define, y que se debe a una operación que no tiene ningún resultado razonable: por ejemplo, convertir un valor de punto flotante en un entero sin signo o cambiar un valor por un número de posiciones que es negativo o supera el número de bits en su tipo promocionado.

*El comportamiento definido por* la implementación es un comportamiento que el estándar C++ requiere que el proveedor del compilador defina y documente. Un programa puede confiar de forma segura en el comportamiento definido por la implementación, aunque hacerlo podría no ser portátil. Entre los ejemplos de comportamiento definido por la implementación se incluyen los tamaños de los tipos de datos integrados y sus requisitos de alineación. Un ejemplo de una operación que podría verse afectada por el comportamiento definido por la implementación es tener acceso a la lista de argumentos de variables.

*El comportamiento no especificado* es el comportamiento que el estándar C++ deja intencionalmente no determinista. Aunque el comportamiento se considera no determinista, la implementación del compilador determina determinadas invocaciones de comportamiento no especificado. Sin embargo, no hay ningún requisito para que un proveedor del compilador predetermine el resultado o garantice un comportamiento coherente entre invocaciones comparables y no hay ningún requisito para la documentación. Un ejemplo de comportamiento no especificado es el orden en que se evalúan las subexpresiones, que incluyen argumentos para una llamada de función.

Otros problemas de migración se pueden atribuir a diferencias de hardware entre arquitecturas ARM y x86 o x64 que interactúan con el estándar C++ de forma diferente. Por ejemplo, el modelo de memoria fuerte de la `volatile`arquitectura x86 y x64 proporciona a las variables calificadas algunas propiedades adicionales que se han utilizado para facilitar ciertos tipos de comunicación entre subprocesos en el pasado. Pero el modelo de memoria débil de la arquitectura ARM no admite este uso, ni el estándar C++ lo requiere.

> [!IMPORTANT]
> Aunque `volatile` obtiene algunas propiedades que se pueden usar para implementar formas limitadas de comunicación entre subprocesos en x86 y x64, estas propiedades adicionales no son suficientes para implementar la comunicación entre subprocesos en general. El estándar C++ recomienda que dicha comunicación se implemente utilizando primitivas de sincronización adecuadas en su lugar.

Debido a que diferentes plataformas pueden expresar estos tipos de comportamiento de manera diferente, la portabilidad de software entre plataformas puede ser difícil y propensa a errores si depende del comportamiento de una plataforma específica. Aunque muchos de estos tipos de comportamiento se pueden observar y pueden parecer estables, confiar en ellos es al menos no portátil, y en los casos de comportamiento indefinido o no especificado, también es un error. Incluso el comportamiento que se cita en este documento no se debe confiar en y podría cambiar en futuros compiladores o implementaciones de CPU.

## <a name="example-migration-issues"></a>Ejemplo de problemas de migración

El resto de este documento describe cómo el comportamiento diferente de estos elementos del lenguaje C++ puede producir diversos resultados en diversas plataformas.

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>Conversión de punto flotante a entero sin signo

En la arquitectura ARM, la conversión de un valor de punto flotante a un entero de 32 bits se satura al valor más cercano que el entero puede representar si el valor de punto flotante está fuera del intervalo que puede representar el entero. En las arquitecturas x86 y x64, la conversión se ajusta si el entero no está firmado o se establece en -2147483648 si el entero está firmado. Ninguna de estas arquitecturas admite directamente la conversión de valores de punto flotante a tipos enteros más pequeños; en su lugar, las conversiones se realizan a 32 bits y los resultados se truncan a un tamaño menor.

Para la arquitectura ARM, la combinación de saturación y truncamiento significa que la conversión a tipos sin signo satura correctamente los tipos sin signo más pequeños cuando satura un entero de 32 bits, pero produce un resultado truncado para los valores que son mayores que el tipo más pequeño puede representar pero demasiado pequeño para saturar el entero completo de 32 bits. La conversión también se satura correctamente para los enteros con signo de 32 bits, pero el truncamiento de enteros saturados y con signo da como resultado -1 para los valores saturados positivamente y 0 para los valores saturados negativamente. La conversión a un entero con signo más pequeño produce un resultado truncado que es impredecible.

Para las arquitecturas x86 y x64, la combinación de comportamiento envolvente para conversiones de enteros sin signo y valoración explícita para conversiones de enteros con signo en el desbordamiento, junto con el truncamiento, hacen que los resultados de la mayoría de los turnos sean impredecibles si son demasiado grandes.

Estas plataformas también difieren en cómo manejan la conversión de NaN (Not-a-Number) a tipos enteros. En ARM, NaN convierte a 0x00000000; en x86 y x64, se convierte a 0x80000000.

La conversión de punto flotante solo se puede confiar en si sabe que el valor está dentro del intervalo del tipo entero al que se está convirtiendo.

### <a name="shift-operator---behavior"></a>Comportamiento del\< \< operador de cambio ( >>)

En la arquitectura ARM, un valor se puede desplazar a la izquierda o a la derecha hasta 255 bits antes de que el patrón comience a repetirse. En las arquitecturas x86 y x64, el patrón se repite en cada múltiplo de 32 a menos que el origen del patrón sea una variable de 64 bits; en ese caso, el patrón se repite en cada múltiplo de 64 en x64, y cada múltiplo de 256 en x86, donde se emplea una implementación de software. Por ejemplo, para una variable de 32 bits que tiene un valor de 1 desplazado a la izquierda por 32 posiciones, en ARM el resultado es 0, en x86 el resultado es 1, y en x64 el resultado también es 1. Sin embargo, si el origen del valor es una variable de 64 bits, el resultado en las tres plataformas es 4294967296, y el valor no se "envuelve" hasta que se desplaza 64 posiciones en x64, o 256 posiciones en ARM y x86.

Dado que el resultado de una operación de desplazamiento que supera el número de bits en el tipo de origen es indefinido, no es necesario que el compilador tenga un comportamiento coherente en todas las situaciones. Por ejemplo, si ambos operandos de un desplazamiento se conocen en tiempo de compilación, el compilador puede optimizar el programa mediante una rutina interna para calcular previamente el resultado del desplazamiento y, a continuación, sustituir el resultado en lugar de la operación de desplazamiento. Si la cantidad de desplazamiento es demasiado grande o negativa, el resultado de la rutina interna podría ser diferente del resultado de la misma expresión de desplazamiento que ejecuta la CPU.

### <a name="variable-arguments-varargs-behavior"></a>Comportamiento de los argumentos variables (varargs)

En la arquitectura ARM, los parámetros de la lista de argumentos de variableques que se pasan en la pila están sujetos a alineación. Por ejemplo, un parámetro de 64 bits se alinea en un límite de 64 bits. En x86 y x64, los argumentos que se pasan en la pila no están sujetos a alineación y empaquetan firmemente. Esta diferencia puede provocar que `printf` una función variádica como leer direcciones de memoria que se diseñaron como relleno en ARM si el diseño esperado de la lista de argumentos de variables no coincide exactamente, aunque podría funcionar para un subconjunto de algunos valores en las arquitecturas x86 o x64. En este ejemplo:

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will "parse" the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

En este caso, el error se puede corregir asegurándose de que se utiliza la especificación de formato correcta para que se tenga en cuenta la alineación del argumento. Este código es correcto:

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>Orden de evaluación de argumentos

Dado que los procesadores ARM, x86 y x64 son tan diferentes, pueden presentar diferentes requisitos a las implementaciones del compilador y también diferentes oportunidades para optimizaciones. Debido a esto, junto con otros factores como la configuración de convención de llamada y optimización, un compilador podría evaluar argumentos de función en un orden diferente en arquitecturas diferentes o cuando se cambian los otros factores. Esto puede hacer que el comportamiento de una aplicación que se basa en un orden de evaluación específico cambie inesperadamente.

Este tipo de error puede producirse cuando los argumentos de una función tienen efectos secundarios que afectan a otros argumentos a la función en la misma llamada. Normalmente, este tipo de dependencia es fácil de evitar, pero a veces puede ocultarse por dependencias que son difíciles de discernir o por sobrecarga del operador. Considere este ejemplo de código:

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

Esto parece bien definido, `->` `*` pero si y son operadores sobrecargados, a continuación, este código se traduce a algo que se asemeja a esto:

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

Y si hay una `operator->(memory_handle)` dependencia `operator*(p)`entre y , el código podría depender de un orden de evaluación específico, aunque el código original parezca que no hay ninguna dependencia posible.

### <a name="volatile-keyword-default-behavior"></a>comportamiento predeterminado de palabra clave volátil

El compilador MSVC admite dos `volatile` interpretaciones diferentes del calificador de almacenamiento que puede especificar mediante modificadores del compilador. El modificador [/volatile:ms](reference/volatile-volatile-keyword-interpretation.md) selecciona la semántica volátil extendida de Microsoft que garantiza un orden seguro, como ha sido el caso tradicional para x86 y x64 debido al modelo de memoria fuerte en esas arquitecturas. El modificador [/volatile:iso](reference/volatile-volatile-keyword-interpretation.md) selecciona la estricta semántica volátil estándar C++ que no garantiza un orden fuerte.

En la arquitectura ARM, el valor predeterminado es **/volatile:iso** porque los procesadores ARM tienen un modelo de memoria débilmente ordenado y porque el software ARM no tiene un legado de confiar en la semántica extendida de **/volatile:ms** y normalmente no tiene que interactuar con el software que sí lo tiene. Sin embargo, a veces es conveniente o incluso necesario compilar un programa ARM para usar la semántica extendida. Por ejemplo, puede ser demasiado costoso portar un programa para utilizar la semántica ISO C++, o el software del controlador podría tener que adherirse a la semántica tradicional para funcionar correctamente. En estos casos, puede utilizar el modificador **/volatile:ms;** sin embargo, para volver a crear la semántica volátil tradicional en los destinos `volatile` ARM, el compilador debe insertar barreras de memoria alrededor de cada lectura o escritura de una variable para aplicar un orden seguro, lo que puede tener un impacto negativo en el rendimiento.

En las arquitecturas x86 y x64, el valor predeterminado es **/volatile:ms** porque gran parte del software que ya se ha creado para estas arquitecturas mediante MSVC se basa en ellas. Al compilar programas x86 y x64, puede especificar el modificador **/volatile:iso** para ayudar a evitar la dependencia innecesaria de la semántica volátil tradicional y para promover la portabilidad.

## <a name="see-also"></a>Consulte también

[Configuración de Visual C++ para procesadores ARM](configuring-programs-for-arm-processors-visual-cpp.md)
