---
title: binomial_distribution (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::binomial_distribution
- random/std::binomial_distribution::reset
- random/std::binomial_distribution::p
- random/std::binomial_distribution::t
- random/std::binomial_distribution::param
- random/std::binomial_distribution::min
- random/std::binomial_distribution::max
- random/std::binomial_distribution::operator()
- random/std::binomial_distribution::param_type
- random/std::binomial_distribution::param_type::p
- random/std::binomial_distribution::param_type::t
- random/std::binomial_distribution::param_type::operator==
- random/std::binomial_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- std::binomial_distribution [C++]
- std::binomial_distribution [C++], reset
- std::binomial_distribution [C++], p
- std::binomial_distribution [C++], t
- std::binomial_distribution [C++], param
- std::binomial_distribution [C++], min
- std::binomial_distribution [C++], max
- std::binomial_distribution [C++], param_type
- std::binomial_distribution [C++], param_type
ms.assetid: b7c8a26a-da8c-45a5-a3a8-208f7a3609ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f46e2d7f6fd7337965d0b5dcf5b5cfe8d7a53688
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846316"
---
# <a name="binomialdistribution-class"></a>binomial_distribution (Clase)

Genera una distribución binomial.

## <a name="syntax"></a>Sintaxis

```cpp
template<class IntType = int>
class binomial_distribution
   {
public:
   // types
   typedef IntType result_type;
   struct param_type;

   // constructors and reset functions
   explicit binomial_distribution(result_type t = 1, double p = 0.5);
   explicit binomial_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type t() const;
   double p() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parámetros

*IntType* el tipo de resultado entero, valor predeterminado es `int`. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).

*URNG* El motor de generador de números aleatorios uniformes. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Comentarios

La clase de plantilla describe una distribución que produce valores de un tipo de entero especificado por el usuario o de tipo `int` si no se proporciona ninguno, distribuido según la distribución binomial. La tabla siguiente incluye vínculos a artículos sobre miembros individuales.

||||
|-|-|-|
|[binomial_distribution](#binomial_distribution)|`binomial_distribution::t`|`binomial_distribution::param`|
|`binomial_distribution::operator()`|`binomial_distribution::p`|[param_type](#param_type)|

Los miembros de propiedad `t()` y `p()` devuelven los valores para los parámetros de distribución almacenados actualmente `t` y `p`, respectivamente.

El miembro de propiedad `param()` establece o devuelve el paquete de parámetros de distribución almacenado `param_type`.

Las funciones miembro `min()` y `max()` devuelven el resultado posible más pequeño y el resultado posible más grande, respectivamente.

La función miembro `reset()` descarta cualquier valor almacenado en caché, de modo que la siguiente llamada a `operator()` no depende de ningún valor obtenido del motor antes de la llamada.

Las funciones miembro `operator()` devuelven el siguiente valor generado basado en el motor URNG, desde el paquete de parámetros actual o desde el paquete de parámetros especificado.

Para obtener más información sobre las clases de distribución y sus miembros, vea [\<random>](../standard-library/random.md).

Para obtener información más detallada sobre la función de probabilidad discreta de distribución binomial, vea el artículo de Wolfram MathWorld sobre la [distribución binomial](http://go.microsoft.com/fwlink/p/?linkid=398469).

## <a name="example"></a>Ejemplo

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const int t, const double p, const int& s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::binomial_distribution<> distr(t, p);

    std::cout << std::endl;
    std::cout << "p == " << distr.p() << std::endl;
    std::cout << "t == " << distr.t() << std::endl;

    // generate the distribution as a histogram
    std::map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Histogram for " << s << " samples:" << std::endl;
    for (const auto& elem : histogram) {
        std::cout << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    int    t_dist = 1;
    double p_dist = 0.5;
    int    samples = 100;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter an integer value for t distribution (where 0 <= t): ";
    std::cin >> t_dist;
    std::cout << "Enter a double value for p distribution (where 0.0 <= p <= 1.0): ";
    std::cin >> p_dist;
    std::cout << "Enter an integer value for a sample count: ";
    std::cin >> samples;

    test(t_dist, p_dist, samples);
}
```

Primera ejecución:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for t distribution (where 0 <= t): 22
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .25
Enter an integer value for a sample count: 100

p == 0.25
t == 22
Histogram for 100 samples:
    1 :
    2 ::
    3 :::::::::::::
    4 ::::::::::::::
    5 :::::::::::::::::::::::::
    6 ::::::::::::::::::
    7 :::::::::::::
    8 ::::::
    9 ::::::
    11 :
    12 :
```

Segunda ejecución:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for t distribution (where 0 <= t): 22
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .5
Enter an integer value for a sample count: 100

p == 0.5
t == 22
Histogram for 100 samples:
    6 :
    7 ::
    8 :::::::::
    9 ::::::::::
    10 ::::::::::::::::
    11 :::::::::::::::::::
    12 :::::::::::
    13 :::::::::::::
    14 :::::::::::::::
    15 ::
    16 ::
```

Tercera ejecución:

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for t distribution (where 0 <= t): 22
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .75
Enter an integer value for a sample count: 100

p == 0.75
t == 22
Histogram for 100 samples:
    13 ::::
    14 :::::::::::
    15 :::::::::::::::
    16 :::::::::::::::::::::
    17 ::::::::::::::
    18 :::::::::::::::::
    19 :::::::::::
    20 ::::::
    21 :
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<random>

**Espacio de nombres:** std

## <a name="binomial_distribution"></a>  binomial_distribution::binomial_distribution

Construye la distribución.

```cpp
explicit binomial_distribution(result_type t = 1, double p = 0.5);
explicit binomial_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parámetros

*t* el `t` parámetro de distribución.

*p* el `p` parámetro de distribución.

*parm* el `param_type` estructura utilizada para construir la distribución.

### <a name="remarks"></a>Comentarios

**Condición previa:** `0 ≤ t` y `0.0 ≤ p ≤ 1.0`

El primer constructor crea un objeto cuyo valor `p` almacenado contiene el valor *p* y cuyo valor `t` almacenado contiene el valor *t*.

El segundo constructor crea un objeto cuyos parámetros almacenados se inicializan desde *parm*. Los parámetros actuales de una distribución existente se pueden obtener y definir llamando a la función miembro `param()`.

## <a name="param_type"></a>  binomial_distribution::param_type

Almacena todos los parámetros de la distribución.

```cpp
struct param_type {
   typedef binomial_distribution<result_type> distribution_type;
   param_type(result_type t = 1, double p = 0.5);
   result_type t() const;
   double p() const;
   .....
   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parámetros

*t* el `t` parámetro de distribución.

*p* el `p` parámetro de distribución.

*derecho* la `param_type` objeto que se va a comparar con esta.

### <a name="remarks"></a>Comentarios

**Condición previa:** `0 ≤ t` y `0.0 ≤ p ≤ 1.0`

Esta estructura se puede pasar al constructor de clases de la distribución en el momento de creación de instancias, a la función miembro `param()` para definir los parámetros almacenados de una distribución existente y a `operator()` para usarse en lugar de los parámetros almacenados.

## <a name="see-also"></a>Vea también

[\<random>](../standard-library/random.md)<br/>
