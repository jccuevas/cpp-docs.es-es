---
title: '&lt;complex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <complex>
- std::<complex>
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
ms.openlocfilehash: 071e9369cdd0469d8ddc1c6649a3801732d8e23f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688217"
---
# <a name="ltcomplexgt"></a>&lt;complex&gt;

Define la plantilla de clase contenedora `complex` y sus plantillas auxiliares.

## <a name="requirements"></a>Requisitos

**Encabezado**: \<complex>

**Espacio de nombres:** std

## <a name="remarks"></a>Comentarios

Un número complejo es un par ordenado de números reales. En términos puramente geométricos, el plano complejo es el plano real y bidimensional. Las cualidades especiales del plano complejo que lo diferencian del plano real se deben a que tiene una estructura algebraica adicional. Esta estructura algebraica tiene dos operaciones fundamentales:

- Suma definida como (*a*, *b*) + (*c*, *d*) = (*a*  + *c*, *b*  + *d*)

- Multiplicación definida como (*a*, *b*) \* (*c*, *d*) = (*AC*  - *BD*, *ad*  + *BC*)

El conjunto de números complejos con las operaciones de suma compleja y multiplicación compleja son un campo en el sentido algebraico estándar:

- Las operaciones de suma y multiplicación son conmutativas y asociativas, y la multiplicación se distribuye sobre la suma exactamente como lo hace con la suma y multiplicación reales en el campo de los números reales.

- El número complejo (0,0) es la identidad aditiva y (1,0) es la identidad multiplicativa.

- El inverso aditivo de un número complejo (*a*, *b*) es (-*a*,-*b*) y el inverso multiplicativo de todos estos números complejos excepto (0, 0) es

   (*a/* (*a*<sup>2</sup>  + *b*<sup>2</sup>),-*b*/(*a*<sup>2</sup>  + *b*<sup>2</sup>))

Al representar un número complejo *z* = (*a*, *b*) con la forma *z*  = *una*  + *BI*, donde *i*<sup>2</sup> =-1, se pueden aplicar las reglas para el álgebra del conjunto de números reales al conjunto de complejos números y a sus componentes. Por ejemplo:

   (1 + 2*i*) \* (2 + 3*i*) = 1 \* (2 + 3*i*) + 2*i* \* (2 + 3*i*) = (2 + 3*i*) + (4*i* + 6*i*<sup>2</sup>) = (2-6) + (3 + 4)*i* =-4 + 7*i*

El sistema de números complejos es un campo, pero no es un campo ordenado. No hay ningún orden de los números complejos como el campo de los números reales y sus subconjuntos, por lo que no se pueden aplicar desigualdades a los números complejos como si fueran números reales.

Existen tres formas comunes de representar un número complejo *z*:

- Cartesiano: *z*  = *una*  + *BI*

- Polar: *z*  = *r* (cos *p*  + *i* *f*)

- Exponencial: *z*  = *r* \* *e*<sup>*IP*</sup>

Los términos usados en estas representaciones estándar de un número complejo se conocen como se indica a continuación:

- El componente cartesiano real o la parte real *a*.

- El componente cartesiano imaginario o la parte imaginaria *b*.

- El módulo o valor absoluto de un número complejo *r*.

- El argumento o el ángulo de fase *p* en radianes.

A menos que se especifique lo contrario, las funciones que pueden devolver varios valores deben devolver un valor de entidad de seguridad para sus argumentos mayores que-π y menor o igual que + π para mantenerlos con un solo valor. Todos los ángulos deben expresarse en radianes, donde hay 2π radianes (360 grados) en un círculo.

## <a name="members"></a>Miembros

### <a name="functions"></a>Funciones

|||
|-|-|
|[abs](../standard-library/complex-functions.md#abs)|Calcula el módulo de un número complejo.|
|[acos](../standard-library/complex-functions.md#acos)||
|[acosh](../standard-library/complex-functions.md#acosh)||
|[arg](../standard-library/complex-functions.md#arg)|Extrae el argumento de un número complejo.|
|[asin](../standard-library/complex-functions.md#asin)||
|[asinh](../standard-library/complex-functions.md#asinh)||
|[atan](../standard-library/complex-functions.md#atan)||
|[atanh](../standard-library/complex-functions.md#atanh)||
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
|[proj](../standard-library/complex-functions.md#proj)||
|[real](../standard-library/complex-functions.md#real)|Extrae el componente real de un número complejo|
|[sin](../standard-library/complex-functions.md#sin)|Devuelve el seno de un número complejo.|
|[sinh](../standard-library/complex-functions.md#sinh)|Devuelve el seno hiperbólico de un número complejo.|
|[sqrt](../standard-library/complex-functions.md#sqrt)|Devuelve la raíz cuadrada de un número complejo.|
|[tan](../standard-library/complex-functions.md#tan)|Devuelve la tangente de un número complejo.|
|[tanh](../standard-library/complex-functions.md#tanh)|Devuelve la tangente hiperbólica de un número complejo.|

### <a name="operators"></a>Operadores

|||
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

|||
|-|-|
|[complex\<double>](../standard-library/complex-double.md)|La plantilla de clase especializada explícitamente describe un objeto que almacena un par ordenado de objetos, ambos de tipo **Double**, donde el primero representa la parte real de un número complejo y el segundo representa la parte imaginaria.|
|[complex\<float>](../standard-library/complex-float.md)|La plantilla de clase especializada explícitamente describe un objeto que almacena un par ordenado de objetos, ambos de tipo **float**, donde el primero representa la parte real de un número complejo y el segundo representa la parte imaginaria.|
|[complex\<long double>](../standard-library/complex-long-double.md)|La plantilla de clase especializada explícitamente describe un objeto que almacena un par ordenado de objetos, ambos de tipo **Long Double**, donde el primero representa la parte real de un número complejo y el segundo representa la parte imaginaria.|
|[complex](../standard-library/complex-class.md)|La plantilla de clase describe un objeto que se usa para representar el sistema de números complejos y realizar operaciones aritméticas complejas.|

### <a name="literals"></a>Literales

El encabezado \<complex> define los [literales definidos por el usuario](../cpp/user-defined-literals-cpp.md) siguientes, que crean un número complejo con la parte real igual a cero y la parte imaginaria igual al valor del parámetro de entrada.

|||
|-|-|
|`constexpr complex<long double> operator""il(long double d)`<br />`constexpr complex<long double> operator""il(unsigned long long d)`|Devuelve: `complex<long double>{0.0L, static_cast<long double>(d)}`|
|`constexpr complex<double> operator""i(long double d)`<br />`constexpr complex<double> operator""i(unsigned long long d)`|Devuelve: `complex<double>{0.0, static_cast<double>(d)}`.|
|`constexpr complex<float> operator""if(long double d)`<br />`constexpr complex<float> operator""if(unsigned long long d)`|Devuelve: `complex<float>{0.0f, static_cast<float>(d)}`.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
