---
title: bernoulli_distribution (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::bernoulli_distribution
- random/std::bernoulli_distribution::reset
- random/std::bernoulli_distribution::p
- random/std::bernoulli_distribution::param
- random/std::bernoulli_distribution::min
- random/std::bernoulli_distribution::max
- random/std::bernoulli_distribution::operator()
- random/std::bernoulli_distribution::param_type
- random/std::bernoulli_distribution::param_type::p
- random/std::bernoulli_distribution::param_type::operator==
- random/std::bernoulli_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- std::bernoulli_distribution [C++]
- std::bernoulli_distribution [C++], reset
- std::bernoulli_distribution [C++], p
- std::bernoulli_distribution [C++], param
- std::bernoulli_distribution [C++], min
- std::bernoulli_distribution [C++], max
- std::bernoulli_distribution [C++], param_type
- std::bernoulli_distribution [C++], param_type
ms.assetid: 586bcde1-95ca-411a-bf17-4aaf19482f34
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5fd2bfdfc2a55dc1723fb72ab8de64a46c3c612f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846082"
---
# <a name="bernoullidistribution-class"></a>bernoulli_distribution (Clase)

Genera una distribución de Bernoulli.

## <a name="syntax"></a>Sintaxis

```cpp
class bernoulli_distribution
   {
public:
   // types
   typedef bool result_type;
   struct param_type;

   // constructors and reset functions
   explicit bernoulli_distribution(double p = 0.5);
   explicit bernoulli_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   double p() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parámetros

*URNG* El motor de generador de números aleatorios uniformes. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Comentarios

Esta clase describe una distribución que genera valores de tipo `bool`, distribuidos según la función de probabilidad discreta de distribución de Bernoulli. La tabla siguiente incluye vínculos a artículos sobre miembros individuales.

||||
|-|-|-|
|[bernoulli_distribution](#bernoulli_distribution)|`bernoulli_distribution::p`|`bernoulli_distribution::param`|
|`bernoulli_distribution::operator()`||[param_type](#param_type)|

El miembro de propiedad `p()` devuelve el valor de parámetro de distribución `p` almacenado actualmente.

El miembro de propiedad `param()` establece o devuelve el paquete de parámetros de distribución almacenado `param_type`.

Las funciones miembro `min()` y `max()` devuelven el resultado posible más pequeño y el resultado posible más grande, respectivamente.

La función miembro `reset()` descarta cualquier valor almacenado en caché, de modo que la siguiente llamada a `operator()` no depende de ningún valor obtenido del motor antes de la llamada.

Las funciones miembro `operator()` devuelven el siguiente valor generado basado en el motor URNG, desde el paquete de parámetros actual o desde el paquete de parámetros especificado.

Para obtener más información sobre las clases de distribución y sus miembros, vea [\<random>](../standard-library/random.md).

Para obtener más información sobre la función de probabilidad discreta de distribución de Bernoulli, vea el artículo de Wolfram MathWorld sobre la [distribución de Bernoulli](http://go.microsoft.com/fwlink/p/?linkid=398467).

## <a name="example"></a>Ejemplo

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double p, const int s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1729);

    std::bernoulli_distribution distr(p);

    std::cout << "p == " << distr.p() << std::endl;

    // generate the distribution as a histogram
    std::map<bool, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Histogram for " << s << " samples:" << std::endl;
    for (const auto& elem : histogram) {
        std::cout << std::boolalpha << std::setw(5) << elem.first << ' ' << std::string(elem.second, ':') << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double p_dist = 0.5;
    int samples = 100;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a double value for p distribution (where 0.0 <= p <= 1.0): ";
    std::cin >> p_dist;
    std::cout << "Enter an integer value for a sample count: ";
    std::cin >> samples;

    test(p_dist, samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter a double value for p distribution (where 0.0 <= p <= 1.0): .45
Enter an integer value for a sample count: 100
p == 0.45
Histogram for 100 samples:
false :::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
 true :::::::::::::::::::::::::::::::::::::::::
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<random>

**Espacio de nombres:** std

## <a name="bernoulli_distribution"></a>  bernoulli_distribution::bernoulli_distribution

Construye la distribución.

```cpp
explicit bernoulli_distribution(double p = 0.5);
explicit bernoulli_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parámetros

*p* almacenado `p` parámetro de distribución.

*parm* el `param_type` estructura utilizada para construir la distribución.

### <a name="remarks"></a>Comentarios

**Condición previa:** `0.0 ≤ p ≤ 1.0`

El primer constructor crea un objeto cuyo valor `p` almacenado contiene el valor *p*.

El segundo constructor crea un objeto cuyos parámetros almacenados se inicializan desde *parm*. Los parámetros actuales de una distribución existente se pueden obtener y definir llamando a la función miembro `param()`.

## <a name="param_type"></a>  bernoulli_distribution::param_type

Contiene los parámetros de la distribución.

struct param_type {typedef bernoulli_distribution distribution_type; param_type (doble p = 0,5); doble p() const;

   bool operator==(const param_type& right) const; bool operator!=(const param_type& right) const; };

### <a name="parameters"></a>Parámetros

*p* almacenado `p` parámetro de distribución.

### <a name="remarks"></a>Comentarios

**Condición previa:** `0.0 ≤ p ≤ 1.0`

Esta estructura se puede pasar al constructor de clases de la distribución en el momento de creación de instancias, a la función miembro `param()` para definir los parámetros almacenados de una distribución existente y a `operator()` para usarse en lugar de los parámetros almacenados.

## <a name="see-also"></a>Vea también

[\<random>](../standard-library/random.md)<br/>
