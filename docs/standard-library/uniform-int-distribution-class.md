---
title: uniform_int_distribution (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::uniform_int_distribution
- random/std::uniform_int_distribution::reset
- random/std::uniform_int_distribution::a
- random/std::uniform_int_distribution::b
- random/std::uniform_int_distribution::param
- random/std::uniform_int_distribution::min
- random/std::uniform_int_distribution::max
- random/std::uniform_int_distribution::operator()
- random/std::uniform_int_distribution::param_type
- random/std::uniform_int_distribution::param_type::a
- random/std::uniform_int_distribution::param_type::b
- random/std::uniform_int_distribution::param_type::operator==
- random/std::uniform_int_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- std::uniform_int_distribution [C++]
- std::uniform_int_distribution [C++], reset
- std::uniform_int_distribution [C++], a
- std::uniform_int_distribution [C++], b
- std::uniform_int_distribution [C++], param
- std::uniform_int_distribution [C++], min
- std::uniform_int_distribution [C++], max
- std::uniform_int_distribution [C++], param_type
- std::uniform_int_distribution [C++], param_type
ms.assetid: a1867dcd-3bd9-4787-afe3-4b62692c1d04
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d982aee3f5542e8bfcff1da96ce3e70775ead5fe
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961583"
---
# <a name="uniformintdistribution-class"></a>uniform_int_distribution (Clase)

Genera una distribución de enteros uniforme (cada valor es igual de probable) en un intervalo de salida que es inclusivo-inclusivo.

## <a name="syntax"></a>Sintaxis

```cpp
template<class IntType = int>
   class uniform_int_distribution {
public:
   // types
   typedef IntType result_type;
   struct param_type;

   // constructors and reset functions
   explicit uniform_int_distribution(
      result_type a = 0, result_type b = numeric_limits<result_type>::max());
   explicit uniform_int_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
      result_type operator()(URNG& gen);
   template <class URNG>
      result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type a() const;
   result_type b() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
};
```

### <a name="parameters"></a>Parámetros

*IntType* el tipo de resultado entero, el valor predeterminado es **int**. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Comentarios

La clase de plantilla describe una distribución inclusiva-inclusiva que produce valores de un tipo entero especificado por el usuario con una distribución, de modo que todos los valores son igual de probables. La tabla siguiente incluye vínculos a artículos sobre miembros individuales.

||||
|-|-|-|
|[uniform_int_distribution](#uniform_int_distribution)|`uniform_int_distribution::a`|`uniform_int_distribution::param`|
|`uniform_int_distribution::operator()`|`uniform_int_distribution::b`|[param_type](#param_type)|

El miembro de propiedad `a()` devuelve el límite mínimo de la distribución almacenado actualmente, mientras que `b()` devuelve el límite máximo almacenado actualmente. En esta clase de distribución, estos valores máximo y mínimo son los mismos que los que devuelven las funciones de propiedad comunes `min()` y `max()`.

El miembro de propiedad `param()` establece o devuelve el paquete de parámetros de distribución almacenado `param_type`.

Las funciones miembro `min()` y `max()` devuelven el resultado posible más pequeño y el resultado posible más grande, respectivamente.

La función miembro `reset()` descarta cualquier valor almacenado en caché, de modo que la siguiente llamada a `operator()` no depende de ningún valor obtenido del motor antes de la llamada.

Las funciones miembro `operator()` devuelven el siguiente valor generado basado en el motor URNG, desde el paquete de parámetros actual o desde el paquete de parámetros especificado.

Para obtener más información sobre las clases de distribución y sus miembros, vea [\<random>](../standard-library/random.md).

## <a name="example"></a>Ejemplo

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const int a, const int b, const int s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::uniform_int_distribution<> distr(a, b);

    std::cout << "lower bound == " << distr.a() << std::endl;
    std::cout << "upper bound == " << distr.b() << std::endl;

    // generate the distribution as a histogram
    std::map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Distribution for " << s << " samples:" << std::endl;
    for (const auto& elem : histogram) {
        std::cout << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    int a_dist = 1;
    int b_dist = 10;

    int samples = 100;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter an integer value for the lower bound of the distribution: ";
    std::cin >> a_dist;
    std::cout << "Enter an integer value for the upper bound of the distribution: ";
    std::cin >> b_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(a_dist, b_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for the lower bound of the distribution: 0
Enter an integer value for the upper bound of the distribution: 12
Enter an integer value for the sample count: 200
lower bound == 0
upper bound == 12
Distribution for 200 samples:
    0 :::::::::::::::
    1 :::::::::::::::::::::
    2 ::::::::::::::::::
    3 :::::::::::::::
    4 :::::::
    5 :::::::::::::::::::::
    6 :::::::::::::
    7 ::::::::::
    8 :::::::::::::::
    9 :::::::::::::
   10 ::::::::::::::::::::::
   11 :::::::::::::
   12 :::::::::::::::::
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<random>

**Espacio de nombres:** std

## <a name="uniform_int_distribution"></a>  uniform_int_distribution::uniform_int_distribution

Construye la distribución.

```cpp
explicit uniform_int_distribution(
   result_type a = 0, result_type b = std::numeric_limits<result_type>::max());
explicit uniform_int_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parámetros

*a*  
Límite inferior para los valores aleatorios (incluido).

*b*  
Límite superior para los valores aleatorios (incluido).

*parm*  
La estructura `param_type` usada para construir la distribución.

### <a name="remarks"></a>Comentarios

**Condición previa:** `a ≤ b`

El primer constructor crea un objeto cuyo almacenado *un* valor contiene el valor *un* y cuyo almacenado *b* valor contiene el valor *b*.

El segundo constructor crea un objeto cuyos parámetros almacenados se inicializan desde *parm*. Los parámetros actuales de una distribución existente se pueden obtener y definir llamando a la función miembro `param()`.

## <a name="param_type"></a>  uniform_int_distribution::param_type

Almacena los parámetros de la distribución.

```cpp
struct param_type {
   typedef uniform_int_distribution<result_type> distribution_type;
   param_type(
      result_type a = 0, result_type b = std::numeric_limits<result_type>::max());
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parámetros

*a*  
Límite inferior para los valores aleatorios (incluido).

*b*  
Límite superior para los valores aleatorios (incluido).

*right*  
El objeto `param_type` que se va a comparar con este.

### <a name="remarks"></a>Comentarios

**Condición previa:** `a ≤ b`

Esta estructura se puede pasar al constructor de clases de la distribución en el momento de creación de instancias, a la función miembro `param()` para definir los parámetros almacenados de una distribución existente y a `operator()` para usarse en lugar de los parámetros almacenados.

## <a name="see-also"></a>Vea también

[\<random>](../standard-library/random.md)<br/>
