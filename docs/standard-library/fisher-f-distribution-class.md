---
title: fisher_f_distribution (Clase)
ms.date: 11/04/2016
f1_keywords:
- random/std::fisher_f_distribution
- random/std::fisher_f_distribution::reset
- random/std::fisher_f_distribution::m
- random/std::fisher_f_distribution::n
- random/std::fisher_f_distribution::param
- random/std::fisher_f_distribution::min
- random/std::fisher_f_distribution::max
- random/std::fisher_f_distribution::operator()
- random/std::fisher_f_distribution::param_type
- random/std::fisher_f_distribution::param_type::m
- random/std::fisher_f_distribution::param_type::n
- random/std::fisher_f_distribution::param_type::operator==
- random/std::fisher_f_distribution::param_type::operator!=
helpviewer_keywords:
- std::fisher_f_distribution [C++]
- std::fisher_f_distribution [C++], reset
- std::fisher_f_distribution [C++], m
- std::fisher_f_distribution [C++], n
- std::fisher_f_distribution [C++], param
- std::fisher_f_distribution [C++], min
- std::fisher_f_distribution [C++], max
- std::fisher_f_distribution [C++], param_type
- std::fisher_f_distribution [C++], param_type
ms.assetid: 9513b6ce-3309-4be1-829b-f504bca35bbf
ms.openlocfilehash: 2c6a976f3874d563f5bba600b9894ae0103625b0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319593"
---
# <a name="fisher_f_distribution-class"></a>fisher_f_distribution (Clase)

Genera una distribución F de Fisher.

## <a name="syntax"></a>Sintaxis

```cpp
template<class RealType = double>
class fisher_f_distribution
   {
public:
   // types
   typedef RealType result_type;
   struct param_type;  // constructor and reset functions
   explicit fisher_f_distribution(result_type m = 1.0, result_type n = 1.0);
   explicit fisher_f_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   result_type m() const;
   result_type n() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parámetros

*RealType*\
El tipo de resultado de punto flotante, por defecto **es double**. Para ver los tipos posibles, consulte [ \<>aleatorias ](../standard-library/random.md).

*Urng*\
El motor generador de números aleatorios uniforme. Para ver los tipos posibles, consulte [ \<>aleatorias ](../standard-library/random.md).

## <a name="remarks"></a>Observaciones

La plantilla de clase describe una distribución que produce valores de un tipo de punto flotante especificado por el usuario, o escriba **double** si no se proporciona ninguno, distribuido según la distribución F de Fisher. La tabla siguiente incluye vínculos a artículos sobre miembros individuales.

||||
|-|-|-|
|[fisher_f_distribution](#fisher_f_distribution)|`fisher_f_distribution::m`|`fisher_f_distribution::param`|
|`fisher_f_distribution::operator()`|`fisher_f_distribution::n`|[param_type](#param_type)|

Las funciones de propiedad `m()` y `n()` devuelven los valores para los parámetros de distribución almacenados `m` y `n`, respectivamente.

El miembro de propiedad `param()` establece o devuelve el paquete de parámetros de distribución almacenado `param_type`.

Las funciones miembro `min()` y `max()` devuelven el resultado posible más pequeño y el resultado posible más grande, respectivamente.

La función miembro `reset()` descarta cualquier valor almacenado en caché, de modo que la siguiente llamada a `operator()` no depende de ningún valor obtenido del motor antes de la llamada.

Las funciones miembro `operator()` devuelven el siguiente valor generado basado en el motor URNG, desde el paquete de parámetros actual o desde el paquete de parámetros especificado.

Para obtener más información acerca de las clases de distribución y sus miembros, vea [ \<>aleatorias ](../standard-library/random.md).

Para obtener más información sobre la distribución F, vea el artículo de Wolfram MathWorld sobre la [distribución F](https://go.microsoft.com/fwlink/p/?linkid=400899).

## <a name="example"></a>Ejemplo

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

void test(const double m, const double n, const int s) {

    // uncomment to use a non-deterministic seed
    //    std::random_device rd;
    //    std::mt19937 gen(rd());
    std::mt19937 gen(1701);

    std::fisher_f_distribution<> distr(m, n);

    std::cout << std::endl;
    std::cout << "min() == " << distr.min() << std::endl;
    std::cout << "max() == " << distr.max() << std::endl;
    std::cout << "m() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.m() << std::endl;
    std::cout << "n() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.n() << std::endl;

    // generate the distribution as a histogram
    std::map<double, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    std::cout << "Distribution for " << s << " samples:" << std::endl;
    int counter = 0;
    for (const auto& elem : histogram) {
        std::cout << std::fixed << std::setw(11) << ++counter << ": "
            << std::setw(14) << std::setprecision(10) << elem.first << std::endl;
    }
    std::cout << std::endl;
}

int main()
{
    double m_dist = 1;
    double n_dist = 1;
    int samples = 10;

    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;
    std::cout << "Enter a floating point value for the \'m\' distribution parameter (must be greater than zero): ";
    std::cin >> m_dist;
    std::cout << "Enter a floating point value for the \'n\' distribution parameter (must be greater than zero): ";
    std::cin >> n_dist;
    std::cout << "Enter an integer value for the sample count: ";
    std::cin >> samples;

    test(m_dist, n_dist, samples);
}
```

## <a name="output"></a>Output

Primera ejecución:

```Output
Enter a floating point value for the 'm' distribution parameter (must be greater than zero): 1
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == 0
max() == 1.79769e+308
m() == 1.0000000000
n() == 1.0000000000
Distribution for 10 samples:
    1: 0.0204569549
    2: 0.0221376644
    3: 0.0297234962
    4: 0.1600937252
    5: 0.2775342196
    6: 0.3950701700
    7: 0.8363200295
    8: 0.9512500702
    9: 2.7844815974
    10: 3.4320929653
```

Segunda ejecución:

```Output
Enter a floating point value for the 'm' distribution parameter (must be greater than zero): 1
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): .1
Enter an integer value for the sample count: 10

min() == 0
max() == 1.79769e+308
m() == 1.0000000000
n() == 0.1000000000
Distribution for 10 samples:
    1: 0.0977725649
    2: 0.5304122767
    3: 4.9468518084
    4: 25.1012074939
    5: 48.8082121613
    6: 401.8075539377
    7: 8199.5947873699
    8: 226492.6855335717
    9: 2782062.6639740225
    10: 20829747131.7185860000
```

Tercera ejecución:

```Output
Enter a floating point value for the 'm' distribution parameter (must be greater than zero): .1
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1
Enter an integer value for the sample count: 10

min() == 0
max() == 1.79769e+308
m() == 0.1000000000
n() == 1.0000000000
Distribution for 10 samples:
    1: 0.0000000000
    2: 0.0000000000
    3: 0.0000000000
    4: 0.0000000000
    5: 0.0000000033
    6: 0.0000073975
    7: 0.0000703800
    8: 0.0280427735
    9: 0.2660239949
    10: 3.4363333954
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<random>

**Espacio de nombres:** std

## <a name="fisher_f_distributionfisher_f_distribution"></a><a name="fisher_f_distribution"></a>fisher_f_distribution::fisher_f_distribution

Construye la distribución.

```cpp
explicit fisher_f_distribution(result_type m = 1.0, result_type n = 1.0);
explicit fisher_f_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parámetros

*M*\
El parámetro de distribución `m`.

*N*\
El parámetro de distribución `n`.

*Parmesana*\
La estructura `param_type` usada para construir la distribución.

### <a name="remarks"></a>Observaciones

**Condición previa:** `0.0 < m` y `0.0 < n`

El primer constructor crea un objeto cuyo valor `m` almacenado contiene el valor *m* y cuyo valor `n` almacenado contiene el valor *n*.

El segundo constructor crea un objeto cuyos parámetros almacenados se inicializan desde *parm*. Los parámetros actuales de una distribución existente se pueden obtener y definir llamando a la función miembro `param()`.

## <a name="fisher_f_distributionparam_type"></a><a name="param_type"></a>fisher_f_distribution::param_type

Almacena los parámetros de la distribución.

```cpp
struct param_type {
   typedef fisher_f_distribution<result_type> distribution_type;
   param_type(result_type m = 1.0, result_type n = 1.0);
   result_type m() const;
   result_type n() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parámetros

*M*\
El parámetro de distribución `m`.

*N*\
El parámetro de distribución `n`.

*Correcto*\
El objeto `param_type` que se va a comparar con este.

### <a name="remarks"></a>Observaciones

**Condición previa:** `0.0 < m` y `0.0 < n`

Esta estructura se puede pasar al constructor de clases de la distribución en el momento de creación de instancias, a la función miembro `param()` para definir los parámetros almacenados de una distribución existente y a `operator()` para usarse en lugar de los parámetros almacenados.

## <a name="see-also"></a>Consulte también

[\<>al azar](../standard-library/random.md)
