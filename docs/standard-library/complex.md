---
title: '&lt;complex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <complex>
- std::<complex>
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
ms.openlocfilehash: afcdb1246d9c02f83dbc8708326d10e802ad2779
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525872"
---
# <a name="ltcomplexgt"></a>&lt;complex&gt;

Define la clase de plantilla contenedor `complex` y sus plantillas auxiliares.

## <a name="syntax"></a>Sintaxis

```cpp
#include <complex>
```

## <a name="remarks"></a>Comentarios

Un número complejo es un par ordenado de números reales. En términos puramente geométricos, el plano complejo es el plano real y bidimensional. Las cualidades especiales del plano complejo que lo diferencian del plano real se deben a que tiene una estructura algebraica adicional. Esta estructura algebraica tiene dos operaciones fundamentales:

- Adición, definida como (*un*, *b*) + (*c*, *d.*) = (*un* + *c* , *b* + *d.*)

- Multiplicación definida como (*un*, *b*) \* (*c*, *d.*) = (*ac*  -  *bd*, *ad* + *bc*)

El conjunto de números complejos con las operaciones de suma compleja y multiplicación compleja son un campo en el sentido algebraico estándar:

- Las operaciones de suma y multiplicación son conmutativas y asociativas, y la multiplicación se distribuye sobre la suma exactamente como lo hace con la suma y multiplicación reales en el campo de los números reales.

- El número complejo (0, 0) es la identidad aditiva y (1, 0) es la identidad multiplicativa.

- El inverso aditivo de un número complejo (*un*, *b*) es (-*un*, -*b*) y el inverso multiplicativo de todos estos números complejos excepto (0, 0) es

   (*un*/ (*un*<sup>2</sup> + *b*<sup>2</sup>), -*b*/ (*un*<sup>2</sup> + *b*<sup>2</sup>))

Mediante la representación de un número complejo *z* = (*una*, *b*) en el formulario *z* = *una*  +  *bi*, donde *i*<sup>2</sup> = -1, las reglas para el álgebra del conjunto de números reales se puede aplicar al conjunto de números complejos y a sus componentes. Por ejemplo:

   (1 + 2*i*) \* (2 + 3*i*) = 1 \* (2 + 3*i*) + 2*i* \* (2 + 3*i*) = (2 + 3*i*) + (4*i* + 6*i*<sup>2</sup>) = (2-6) + (3 + 4)*i* = -4 + 7*i*

El sistema de números complejos es un campo, pero no es un campo ordenado. No hay ningún orden de los números complejos, como sucede con el campo de números reales y sus subconjuntos, por lo que las desigualdades no se puede aplicar a números complejos tal como están para números reales.

Existen tres formas comunes de representar un número complejo *z*:

- Cartesiana: *z* = *un* + *bi*

- Polar: *z* = *r* (cos *p* + *i* sen *p*)

- Exponencial: *z* = *r* \* *e*<sup>*ip*</sup>

Los términos usados en estas representaciones estándar de un número complejo se conocen como se indica a continuación:

- El componente cartesiano real o la parte real *a*.

- El componente cartesiano imaginario o la parte imaginaria *b*.

- El módulo o valor absoluto de un número complejo *r*.

- El ángulo de fase o argumento *p* en radianes.

A menos que se especifique lo contrario, las funciones que pueden devolver varios valores se deben devolver un valor principal de sus argumentos mayor que - π y menor que o igual a + π mantenerlos solo con valores. Todos los ángulos deben expresarse en radianes, donde hay 2π radianes (360 grados) en un círculo.

### <a name="functions"></a>Funciones

|Función|Descripción|
|-|-|
|[abs](../standard-library/complex-functions.md#abs)|Calcula el módulo de un número complejo.|
|[arg](../standard-library/complex-functions.md#arg)|Extrae el argumento de un número complejo.|
|[conj](../standard-library/complex-functions.md#conj)|Devuelve el conjugado complejo de un número complejo.|
|[cos](../standard-library/complex-functions.md#cos)|Devuelve el coseno de un número complejo.|
|[cosh](../standard-library/complex-functions.md#cosh)|Devuelve el coseno hiperbólico de un número complejo.|
|[exp](../standard-library/complex-functions.md#exp)|Devuelve la función exponencial de un número complejo.|
|[imag](../standard-library/complex-functions.md#imag)|Extrae el componente imaginario de un número complejo.|
|[log](../standard-library/complex-functions.md#log)|Devuelve el logaritmo natural de un número complejo.|
|[log10](../standard-library/complex-functions.md#log10)|Devuelve el logaritmo de base 10 de un número complejo.|
|[norm](../standard-library/complex-functions.md#norm)|Extrae la norma de un número complejo.|
|[polar](../standard-library/complex-functions.md#polar)|Devuelve el número complejo, que corresponde a un módulo y argumento especificados, en formato cartesiano.|
|[pow](../standard-library/complex-functions.md#pow)|Evalúa el número complejo obtenido al elevar una base que es un número complejo a la potencia de otro número complejo.|
|[real](../standard-library/complex-functions.md#real)|Extrae el componente real de un número complejo|
|[sin](../standard-library/complex-functions.md#sin)|Devuelve el seno de un número complejo.|
|[sinh](../standard-library/complex-functions.md#sinh)|Devuelve el seno hiperbólico de un número complejo.|
|[sqrt](../standard-library/complex-functions.md#sqrt)|Devuelve la raíz cuadrada de un número complejo.|
|[tan](../standard-library/complex-functions.md#tan)|Devuelve la tangente de un número complejo.|
|[tanh](../standard-library/complex-functions.md#tanh)|Devuelve la tangente hiperbólica de un número complejo.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator!=](../standard-library/complex-operators.md#op_neq)|Prueba la igualdad entre dos números complejos, uno de los cuales o ambos pueden pertenecer al subconjunto del tipo para las partes reales e imaginarias.|
|[operator*](../standard-library/complex-operators.md#op_star)|Multiplica dos números complejos, donde uno de ellos o los dos pueden pertenecer al subconjunto del tipo para las partes reales e imaginarias.|
|[operator+](../standard-library/complex-operators.md#op_add)|Suma dos números complejos, donde uno de ellos o los dos pueden pertenecer al subconjunto del tipo para las partes reales e imaginarias.|
|[operator-](../standard-library/complex-operators.md#operator-)|Resta dos números complejos, donde uno de ellos o los dos pueden pertenecer al subconjunto del tipo para las partes reales e imaginarias.|
|[operator/](../standard-library/complex-operators.md#op_div)|Divide dos números complejos, donde uno de ellos o los dos pueden pertenecer al subconjunto del tipo para las partes reales e imaginarias.|
|[operator<\<](../standard-library/complex-operators.md#op_lt_lt)|Función de plantilla que inserta un número complejo en el flujo de salida.|
|[operator==](../standard-library/complex-operators.md#op_eq_eq)|Prueba la igualdad entre dos números complejos, uno de los cuales o ambos pueden pertenecer al subconjunto del tipo para las partes reales e imaginarias.|
|[operator>>](../standard-library/complex-operators.md#op_gt_gt)|Función de plantilla que extrae un valor complejo del flujo de salida.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[complex\<double>](../standard-library/complex-double.md)|La clase de plantilla especializada de forma explícita describe un objeto que almacena un par ordenado de objetos, ambos de tipo **doble**, donde el primero representa la parte real de un número complejo y el segundo representa la parte imaginaria.|
|[complex\<float>](../standard-library/complex-float.md)|La clase de plantilla especializada de forma explícita describe un objeto que almacena un par ordenado de objetos, ambos de tipo **float**, donde el primero representa la parte real de un número complejo y el segundo representa la parte imaginaria.|
|[complex\<long double>](../standard-library/complex-long-double.md)|La clase de plantilla especializada de forma explícita describe un objeto que almacena un par ordenado de objetos, ambos de tipo **long double**, donde el primero representa la parte real de un número complejo y el segundo representa la parte imaginaria.|
|[complex](../standard-library/complex-class.md)|Clase de plantilla que describe un objeto que se usa para representar el sistema de números complejos y realizar operaciones aritméticas complejas.|

### <a name="literals"></a>Literales

El encabezado \<complex> define los [literales definidos por el usuario](../cpp/user-defined-literals-cpp.md) siguientes, que crean un número complejo con la parte real igual a cero y la parte imaginaria igual al valor del parámetro de entrada.

|||
|-|-|
|`constexpr complex<long double> operator""il(long double d)`<br /><br /> `constexpr complex<long double> operator""il(unsigned long long d)`|Devuelve: `complex<long double>{0.0L, static_cast<long double>(d)}`|
|`constexpr complex<double> operator""i(long double d)`<br /><br /> `constexpr complex<double> operator""i(unsigned long long d)`|Devuelve: `complex<double>{0.0, static_cast<double>(d)}`.|
|`constexpr complex<float> operator""if(long double d)`<br /><br /> `constexpr complex<float> operator""if(unsigned long long d)`|Devuelve: `complex<float>{0.0f, static_cast<float>(d)}`.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
