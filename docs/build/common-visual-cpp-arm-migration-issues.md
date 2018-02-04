---
title: "Problemas comunes de migración de ARM de Visual C++ | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 0f4c434e-0679-4331-ba0a-cc15dd435a46
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bcc34d472fb6db02eb902001ad5aac77dea5baf0
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="common-visual-c-arm-migration-issues"></a>Problemas comunes de migración de ARM en Visual C++

Cuando se usa Microsoft Visual C++ (MSVC), el mismo código fuente de C++ puede generar resultados diferentes en la arquitectura ARM en arquitecturas x86 o x x64.

## <a name="sources-of-migration-issues"></a>Orígenes de problemas de migración

Muchos problemas que pueden surgir al migrar el código de las arquitecturas x86 o x x64 a la arquitectura ARM están relacionados con construcciones de código fuente que podrían invocar comportamiento indefinido, definido por la implementación o no especificado.

*Un comportamiento indefinido* es el comportamiento que no define el estándar de C++ y que está causado por una operación que no tiene ningún resultado razonable: por ejemplo, convertir un valor de punto flotante en un entero sin signo, o cuando se desplaza un valor por un número de posiciones que es negativo o supera el número de bits de su tipo promovido.

*Comportamiento definido por la implementación* es el comportamiento que el estándar de C++ requiere que el proveedor de compilador definir y documentar. Un programa puede confiar en comportamiento definido por la implementación, aunque al hacerlo lo que podría no ser portátil. Ejemplos de comportamiento definido por la implementación incluyen los tamaños de tipos de datos integrados y los requisitos de alineación. Un ejemplo de una operación que podría verse afectada por comportamiento definido por la implementación tiene acceso a la lista de argumentos de variable.

*No se especifica comportamiento* es el comportamiento que el estándar de C++ deja intencionadamente no determinista. Aunque el comportamiento se considera no determinista, invocaciones determinadas de un comportamiento no especificado vienen determinadas por la implementación del compilador. Sin embargo, no hay ningún requisito para un proveedor de un compilador determinar por adelantado el resultado o garantizar un comportamiento coherente entre invocaciones comparables y no es necesario para la documentación. Un ejemplo de un comportamiento no especificado es el orden en que se evalúan subexpresiones, que contiene los argumentos para una llamada de función.

Otros problemas de migración pueden deberse a las diferencias de hardware entre ARM y las arquitecturas x86 o x x64 que interactúan con el estándar de C++ de forma diferente. Por ejemplo, se proporciona el modelo de memoria seguro de la arquitectura x86 y x64 `volatile`-calificado variables algunas propiedades adicionales que se usaron para facilitar ciertos tipos de comunicación entre subproceso en el pasado. Pero el modelo de memoria débil de la arquitectura ARM no admite este uso ni el estándar de C++ requiere.

> [!IMPORTANT]
>  Aunque `volatile` mejoras de algunas propiedades que pueden usarse para implementar formas limitadas de la comunicación entre subprocesos en x86 y x64, estas propiedades adicionales no son suficientes para implementar entre subprocesos comunicación en general. El estándar de C++, se recomienda que dicha comunicación se implementa utilizando primitivas de sincronización apropiada en su lugar.

Dado que diferentes plataformas podrían expresar este tipo de comportamiento diferente, trasladar software entre plataformas puede ser difícil y error propensas a si depende del comportamiento de una plataforma específica. Aunque muchos de estos tipos de comportamiento pueden observarse y pueden aparecer estables, depender de ellas es al menos no portable y en los casos de comportamiento sin definir o sin especificar, también es un error. Incluso el comportamiento que citados en este documento no debe confiar en y podría cambiar en futuras implementaciones de CPU o los compiladores.

## <a name="example-migration-issues"></a>Problemas de migración de ejemplo

El resto de este documento describe cómo el comportamiento de estos elementos del lenguaje C++ puede producir resultados diferentes en distintas plataformas.

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>Conversión de punto flotante a entero sin signo

En la arquitectura ARM, conversión de un valor de punto flotante en un entero de 32 bits se satura al valor más cercano que puede representar el entero si el valor de punto flotante está fuera del intervalo que puede representar el entero. En las arquitecturas x86 y x64, la conversión se ajusta alrededor de si el entero no está firmado o está establecido en -2147483648 si el entero está firmado. Ninguna de estas arquitecturas admite directamente la conversión de valores de punto flotante a tipos enteros más pequeños; en su lugar, se realizan las conversiones a 32 bits, y los resultados se truncan a un tamaño más pequeño.

Para la arquitectura ARM, la combinación de saturación y truncamiento significa que la conversión de tipos sin signo satura tipos sin signo más pequeños correctamente cuando se satura un entero de 32 bits, pero genera un resultado truncado para valores mayores que el tipo más pequeño puede representar pero demasiado pequeño para no saturar el entero de 32 bits. Conversión también se satura correctamente para los enteros con signo de 32 bits, pero da como resultado el truncamiento de enteros saturados, firmados en -1 para los valores de forma positiva saturado y 0 para los valores saturado negativamente. Conversión a un entero con signo más pequeño genera un resultado truncado que es imprevisible.

Para las arquitecturas x86 y x64, la combinación de comportamiento circular para las conversiones de enteros sin signo y valoración explícita para las conversiones de entero con signo si se produce desbordamiento, junto con el truncamiento, hacer que los resultados para la mayoría de desplazamientos imprevisibles si son demasiado grande.

Estas plataformas también difieren en cómo controlan la conversión de NaN (Not a Number) a tipos enteros. En ARM, NaN se convierte en 0 x 00000000; en x86 y x64, convierte en 0 x 80000000.

Conversión de punto flotante se puede confiar sólo en si sabe que el valor está dentro del intervalo del tipo de entero que se va a convertir a.

### <a name="shift-operator---behavior"></a>Operador de desplazamiento (\< \< >>) comportamiento

En la arquitectura ARM, un valor puede se desplazado a la izquierda o la derecha hasta 255 bits antes de que el patrón comience a repetir. En las arquitecturas x86 y x64, el patrón se repite en cada múltiplo de 32 a menos que el origen del patrón es una variable de 64 bits; en ese caso, el patrón se repite en cada múltiplo de 64 x 64 y cada múltiplo de 256 en x86, donde se emplea una implementación de software. Por ejemplo, para una variable de 32 bits que tiene un valor de 1 desplazado 32 posiciones a la izquierda, en ARM, el resultado es 0, en x86 el resultado es 1 y, en x64, el resultado también es 1. Sin embargo, si el origen del valor es una variable de 64 bits, a continuación, el resultado en las tres plataformas 4294967296, y el valor no "ajustarse" hasta que han desplazado a 64 posiciones en x64 o 256 posiciones en ARM y x86.

Dado que el resultado de una operación de desplazamiento que supera el número de bits en el tipo de origen no está definido, el compilador no tiene que tener un comportamiento coherente en todas las situaciones. Por ejemplo, si ambos operandos de un desplazamiento se conocen en tiempo de compilación, el compilador puede optimizar el programa mediante una rutina interna para calcular previamente el resultado de la tecla MAYÚS y, a continuación, sustituyendo el resultado en lugar de la operación de desplazamiento. Si la cantidad de desplazamiento es demasiado grande o negativo, el resultado de la rutina interna puede ser diferente que el resultado de la misma expresión de desplazamiento ejecutado por la CPU.

### <a name="variable-arguments-varargs-behavior"></a>Comportamiento de argumentos variables (varargs)

En la arquitectura ARM, parámetros de la lista de argumentos variables que se pasan en la pila están sujetos a alineación. Por ejemplo, un parámetro de 64 bits está alineado en un límite de 64 bits. En x86 y x64, los argumentos que se pasan en la pila no estén sujetos a la alineación y el módulo de estrechamente. Esta diferencia puede provocar una función variádica como `printf` para leer las direcciones de memoria que inicialmente se diseñó como relleno en ARM si el diseño esperado de la lista de argumentos de variable no coincide exactamente, aunque es posible que funcione para un subconjunto de algunos valores en el x86 o x64 arquitecturas. Considere este ejemplo:

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will “parse” the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

En este caso, se puede corregir el error, asegúrese de que se usa la especificación de formato correcto para que se considera la alineación del argumento. Este código es correcto:

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>Orden de evaluación del argumento

Dado que ARM, x 86 y x64 procesadores son tan diferentes, pueden presentar distintos requisitos para las implementaciones del compilador y también distintas formas de realizar las optimizaciones. Por este motivo, junto con otros factores como la convención de llamada y la optimización de configuración, un compilador puede evaluar argumentos de función en un orden diferente en distintas arquitecturas o cuando se cambian los otros factores. Esto puede hacer que el comportamiento de una aplicación que se basa en un orden de evaluación concreto para cambiar de forma inesperada.

Este tipo de error puede producirse cuando argumentos a una función tienen efectos secundarios que afectan a otros argumentos a la función en la misma llamada. Normalmente este tipo de dependencia es fácil evitar, pero a veces puede verse oscurecida por las dependencias que son difíciles de discernir o por la sobrecarga de operadores. Tenga en cuenta este ejemplo de código:

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

Esto parece bien definida, pero si `->` y `*` son operadores sobrecargados, este código se traduce a algo similar a esto:

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

Y si no hay una dependencia entre `operator->(memory_handle)` y `operator*(p)`, el código podría basarse en un orden de evaluación concreta, aunque el código original aspecto no haya ninguna dependencia posibles.

### <a name="volatile-keyword-default-behavior"></a>comportamiento predeterminado de palabra clave volatile

El compilador MSVC admite dos diferentes interpretaciones de los `volatile` calificador de almacenamiento que puede especificar mediante el uso de modificadores del compilador. El [/volatile:ms](../build/reference/volatile-volatile-keyword-interpretation.md) conmutador selecciona el extendidas semántica volátil que garantiza la solicitud segura, tal y como se ha caso tradicional para x86 y x64 debido al modelo de memoria seguros de dichas arquitecturas de Microsoft. El [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) conmutador selecciona el C++ estándar volátil semántica estricta que no garantiza el orden seguro.

En la arquitectura ARM, el valor predeterminado es **/volatile:iso** puesto procesadores ARM tienen un débilmente ordenado el modelo de memoria, y el software ARM no tener heredado de basarse en la semántica extendida de **/volatile:ms**  y normalmente no tiene para comunicarse con el software que realiza. Sin embargo, resulta conveniente todavía a veces o incluso necesarios para compilar un programa ARM para usar la semántica extendida. Por ejemplo, puede ser demasiado costosa trasladar un programa para utilizar la semántica de ISO C++, o podría tener software de controlador cumplir con la semántica tradicional para funcionar correctamente. En estos casos, puede usar el **/volatile:ms** conmutador; sin embargo, para volver a crear la semántica tradicional volátil en destinos ARM, el compilador debe insertar barreras de memoria alrededor de cada lectura o escritura de un `volatile` variable para aplicar ordenación seguro, que puede tener un impacto negativo en el rendimiento.

En las arquitecturas x86 y x64, el valor predeterminado es **/volatile:ms** porque gran parte del software que ya se ha creado para estas arquitecturas utilizando MSVC se basa en ellos. Al compilar programas de x86 y x64, puede especificar el **/volatile:iso** conmutador para ayudar a evitar la dependencia innecesario de la semántica tradicional volátil y promover la portabilidad.

## <a name="see-also"></a>Vea también

[Configuración de Visual C++ para procesadores ARM](../build/configuring-programs-for-arm-processors-visual-cpp.md)  
