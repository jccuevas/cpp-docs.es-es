---
title: Compatibilidad con cálculos matemáticos complejos de C | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.complex
dev_langs:
- C++
helpviewer_keywords:
- complex numbers, math routines
- math routines
- complex numbers
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 661e1367ea64713cf7a143f276cd195d54fecf85
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392083"
---
# <a name="c-complex-math-support"></a>Compatibilidad con cálculos matemáticos complejos de C

La biblioteca en tiempo de ejecución de Microsoft C (CRT) ofrece muchas funciones de biblioteca de cálculos matemáticos complejos, incluidas las necesarias según ISO C99. El compilador no admite directamente las palabras clave **complex** ni **_Complex**, de modo que la implementación de Microsoft usa tipos de estructuras para representar los números complejos.

Estas funciones se implementan para equilibrar el rendimiento con exactitud. Dado que es posible que producir el resultado redondeado correctamente sea excesivamente costoso, estas funciones están diseñadas para generar con eficacia una buena aproximación al resultado redondeado correctamente. En la mayoría de los casos, el resultado producido se encuentra dentro de +/-1 ulp del resultado redondeado correctamente, aunque puede haber casos en los que la falta de precisión sea mayor.

Las rutinas de cálculos matemáticos complejos dependen de las funciones de la biblioteca de punto flotante para su implementación. Dichas funciones presentan implementaciones distintas según la arquitectura de CPU. Por ejemplo, puede que el CRT x86 de 32 bits tenga una implementación distinta que el CRT x64 de 64 bits. Además, algunas de las funciones pueden tener varias implementaciones para una determinada arquitectura de CPU. La implementación más eficaz se selecciona dinámicamente en tiempo de ejecución en función de los conjuntos de instrucciones compatibles con la CPU. Por ejemplo, en el CRT x86 de 32 bits, algunas funciones tienen una implementación x87 y una implementación SSE2. Cuando se ejecuta en una CPU que admite SSE2, se usa la implementación SSE2 más rápida. Cuando se ejecuta en una CPU que no admite SSE2, se usa la implementación x87 más lenta. Dado que es posible que diferentes implementaciones de las funciones de la biblioteca matemática usen distintas instrucciones de CPU y distintos algoritmos para generar sus resultados, puede que las funciones generen diferentes resultados en las CPU. En la mayoría de los casos, los resultados se encuentran dentro de +/-1 ulp del resultado redondeado correctamente, pero los resultados reales pueden variar de una CPU a otra.

## <a name="types-used-in-complex-math"></a>Tipos que se utilizan en cálculos matemáticos complejos

La implementación de Microsoft del encabezado complex.h define dichos tipos como equivalentes de los tipos complejos nativos del estándar C99:

|Tipo estándar|Tipo de Microsoft|
|-|-|
|**float complex** o **float _Complex**|**_FComplex**|
|**double complex** o **double _Complex**|**_DComplex**|
|**long double complex** o **long double _Complex**|**_LComplex**|

El encabezado math.h define un tipo independiente, **struct _complex**, que se usa para la función [_cabs](../c-runtime-library/reference/cabs.md). Las funciones de cálculos matemáticos complejos equivalentes ([cabs, cabsf, cabsl](../c-runtime-library/reference/cabs-cabsf-cabsl.md)) no usan el tipo **struct _complex**.

## <a name="complex-constants-and-macros"></a>Constantes y macros complejas

**I** se define como el tipo complejo de **float** **_FComplex** inicializado por `{ 0.0f, 1.0f }`.

## <a name="trigonometric-functions"></a>Funciones trigonométricas

|Función|Description|
|-|-|
|[cacos, cacosf, cacosl](../c-runtime-library/reference/cacos-cacosf-cacosl.md)|Permite calcular el arcocoseno complejo de un número complejo.|
|[casin, casinf, casinl](../c-runtime-library/reference/casin-casinf-casinl.md)|Permite calcular el arcoseno complejo de un número complejo.|
|[catan, catanf, catanl](../c-runtime-library/reference/catan-catanf-catanl.md)|Permite calcular la arcotangente compleja de un número complejo.|
|[ccos, ccosf, ccosl](../c-runtime-library/reference/ccos-ccosf-ccosl.md)|Permite calcular el coseno complejo de un número complejo.|
|[csin, csinf, csinl](../c-runtime-library/reference/csin-csinf-csinl.md)|Permite calcular el seno complejo de un número complejo.|
|[ctan, ctanf, ctanl](../c-runtime-library/reference/ctan-ctanf-ctanl.md)|Permite calcular la tangente compleja de un número complejo.|

## <a name="hyperbolic-functions"></a>Funciones hiperbólicas

|Función|Description|
|-|-|
|[cacosh, cacoshf, cacoshl](../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)|Permite calcular el arcocoseno hiperbólico complejo de un número complejo.|
|[casinh, casinhf, casinhl](../c-runtime-library/reference/casinh-casinhf-casinhl.md)|Permite calcular el arcoseno hiperbólico complejo de un número complejo.|
|[catanh, catanhf, catanhl](../c-runtime-library/reference/catanh-catanhf-catanhl.md)|Permite calcular la arcotangente hiperbólica compleja de un número complejo.|
|[ccosh, ccoshf, ccoshl](../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)|Permite calcular el coseno hiperbólico complejo de un número complejo.|
|[csinh, csinhf, csinhl](../c-runtime-library/reference/csinh-csinhf-csinhl.md)|Permite calcular el seno hiperbólico complejo de un número complejo.|
|[ctanh, ctanhf, ctanhl](../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)|Permite calcular la tangente hiperbólica compleja de un número complejo.|

## <a name="exponential-and-logarithmic-functions"></a>Funciones exponenciales y logarítmicas

|Función|Description|
|-|-|
|[cexp, cexpf, cexpl](../c-runtime-library/reference/cexp-cexpf-cexpl.md)|Permite calcular el valor exponencial complejo de base *e* de un número complejo.|
|[clog, clogf, clogl](../c-runtime-library/reference/clog-clogf-clogl.md)|Permite calcular el logaritmo natural complejo de base *e* de un número complejo.|
|[clog10, clog10f, clog10l](../c-runtime-library/reference/clog10-clog10f-clog10l.md)|Permite calcular el logaritmo complejo de base 10 de un número complejo.|

## <a name="power-and-absolute-value-functions"></a>Funciones de potencias y valores absolutos

|Función|Description|
|-|-|
|[cabs, cabsf, cabsl](../c-runtime-library/reference/cabs-cabsf-cabsl.md)|Permite calcular el valor complejo absoluto (también denominado "norma vectorial", "módulo" o "magnitud") de un número complejo.|
|[cpow, cpowf, cpowl](../c-runtime-library/reference/cpow-cpowf-cpowl.md)|Permite calcular la función de potencia compleja x<sup>y</sup>.|
|[csqrt, csqrtf, csqrtl](../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)|Permite calcular la raíz cuadrada compleja de un número complejo.|

## <a name="manipulation-functions"></a>Funciones de manipulación

|Función|Description|
|-|-|
|[_Cbuild, _FCbuild, _LCbuild](../c-runtime-library/reference/cbuild-fcbuild-lcbuild.md)|Permite construir un número complejo a partir de elementos reales e imaginarios.|
|[carg, cargf, cargl](../c-runtime-library/reference/carg-cargf-cargl.md)|Permite calcular el argumento (también denominado "ángulo de fase") de un número complejo.|
|[cimag, cimagf, cimagl](../c-runtime-library/reference/cimag-cimagf-cimagl.md)|Permite calcular el elemento imaginario de un número complejo.|
|[conj, conjf, conjl](../c-runtime-library/reference/conj-conjf-conjl.md)|Permite calcular el conjugado complejo de un número complejo.|
|[cproj, cprojf, cprojl](../c-runtime-library/reference/cproj-cprojf-cprojl.md)|Permite calcular la proyección de un número complejo en la esfera de Riemann.|
|[creal, crealf, creall](../c-runtime-library/reference/creal-crealf-creall.md)|Permite calcular el elemento real de un número complejo.|
|[norm, normf, norml](../c-runtime-library/reference/norm-normf-norml1.md)|Permite calcular la magnitud cuadrada de un número complejo.|

## <a name="operation-functions"></a>Funciones de operación

Dado que los números complejos no son un tipo nativo del compilador de Microsoft, los operadores aritméticos estándar no se definen en los tipos complejos. Para mayor comodidad, estas funciones de la biblioteca de cálculos matemáticos complejos se proporcionan para permitir una manipulación limitada de los números complejos del código de usuario:

|Función|Description|
|-|-|
|[_Cmulcc, _FCmulcc, _LCmulcc](../c-runtime-library/reference/cmulcc-fcmulcc-lcmulcc.md)|Permite multiplicar dos números complejos.|
|[_Cmulcr, _FCmulcr, _LCmulcr](../c-runtime-library/reference/cmulcr-fcmulcr-lcmulcr.md)|Permite multiplicar un número complejo y un número de punto flotante.|

## <a name="see-also"></a>Vea también

[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>
