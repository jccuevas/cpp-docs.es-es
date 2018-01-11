---
title: chi_squared_distribution (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- random/std::chi_squared_distribution
- random/std::chi_squared_distribution::reset
- random/std::chi_squared_distribution::n
- random/std::chi_squared_distribution::param
- random/std::chi_squared_distribution::min
- random/std::chi_squared_distribution::max
- random/std::chi_squared_distribution::operator()
- random/std::chi_squared_distribution::param_type
- random/std::chi_squared_distribution::param_type::n
- random/std::chi_squared_distribution::param_type::operator==
- random/std::chi_squared_distribution::param_type::operator!=
dev_langs: C++
helpviewer_keywords:
- std::chi_squared_distribution [C++]
- std::chi_squared_distribution [C++], reset
- std::chi_squared_distribution [C++], n
- std::chi_squared_distribution [C++], param
- std::chi_squared_distribution [C++], min
- std::chi_squared_distribution [C++], max
- std::chi_squared_distribution [C++], param_type
- std::chi_squared_distribution [C++], param_type
ms.assetid: 9b603fbe-cafd-4a92-b8c5-a434d60b8122
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3d5ca4de3cd7192fa4847bf6090a02b156458340
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="chisquareddistribution-class"></a>chi_squared_distribution (Clase)
Genera una distribución chi cuadrado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class RealType = double>  
class chi_squared_distribution {
public:    
    // types 
    typedef RealType result_type;    
    struct param_type;  

    // constructor and reset functions 
    explicit chi_squared_distribution(RealType n = 1);
    explicit chi_squared_distribution(const param_type& parm);
    void reset();  

    // generating functions 
    template <class URNG>  
    result_type operator()(URNG& gen);
    template <class URNG>
    result_type operator()(URNG& gen, const param_type& parm);
    
    // property functions 
    RealType n() const;
    param_type param() const;
    void param(const param_type& parm);
    result_type min() const;
    result_type max() const;
};
```  
#### <a name="parameters"></a>Parámetros  
*RealType*  
Un tipo de resultado de punto flotante, el valor predeterminado es `double`. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).  
  
*URNG* El motor de generador de números aleatorios uniformes. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).  
  
## <a name="remarks"></a>Comentarios  
La clase de plantilla describe una distribución que genera valores de un tipo de punto flotante especificado por el usuario (o de tipo `double` si no se especifica ninguno) distribuidos según la distribución chi cuadrado. La tabla siguiente incluye vínculos a artículos sobre miembros individuales.  
  
||||  
|-|-|-|  
|[chi_squared_distribution)](../standard-library/chi-squared-distribution-class.md)|`chi_squared_distribution::n`|`chi_squared_distribution::param`|  
|`chi_squared_distribution::operator()`||[param_type](#param_type)|  
  
La función de propiedad `n()` devuelve el valor del parámetro de distribución almacenado `n`.  
  
El miembro de propiedad `param()` establece o devuelve el paquete de parámetros de distribución almacenado `param_type`.  

Las funciones miembro `min()` y `max()` devuelven el resultado posible más pequeño y el resultado posible más grande, respectivamente.  
  
La función miembro `reset()` descarta cualquier valor almacenado en caché, de modo que la siguiente llamada a `operator()` no depende de ningún valor obtenido del motor antes de la llamada.  
  
Las funciones miembro `operator()` devuelven el siguiente valor generado basado en el motor URNG, desde el paquete de parámetros actual o desde el paquete de parámetros especificado.
  
Para obtener más información sobre las clases de distribución y sus miembros, vea [\<random>](../standard-library/random.md).  
  
Para obtener información detallada sobre la distribución chi cuadrado, vea el artículo de Wolfram MathWorld sobre la [distribución chi cuadrado](http://go.microsoft.com/fwlink/p/?linkid=400528).  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const double n, const int s) {  
  
    // uncomment to use a non-deterministic generator  
    //    std::random_device gen;  
    std::mt19937 gen(1701);  
  
    std::chi_squared_distribution<> distr(n);  
  
    std::cout << std::endl;  
    std::cout << "min() == " << distr.min() << std::endl;  
    std::cout << "max() == " << distr.max() << std::endl;  
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
    double n_dist = 0.5;  
    int samples = 10;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter a floating point value for the \'n\' distribution parameter (must be greater than zero): ";  
    std::cin >> n_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(n_dist, samples);  
}  
```  
  
Primera ejecución:  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): .5  
Enter an integer value for the sample count: 10  
 
min() == 4.94066e-324  
max() == 1.79769e+308  
n() == 0.5000000000  
Distribution for 10 samples:  
    1: 0.0007625595  
    2: 0.0016895062  
    3: 0.0058683478  
    4: 0.0189647765  
    5: 0.0556619371  
    6: 0.1448191353  
    7: 0.1448245325  
    8: 0.1903494379  
    9: 0.9267525768  
    10: 1.5429743723  
```  
  
Segunda ejecución:  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): .3333  
Enter an integer value for the sample count: 10  
 
min() == 4.94066e-324  
max() == 1.79769e+308  
n() == 0.3333000000  
Distribution for 10 samples:  
    1: 0.0000148725  
    2: 0.0000490528  
    3: 0.0003175988  
    4: 0.0018454535  
    5: 0.0092808795  
    6: 0.0389540735  
    7: 0.0389562514  
    8: 0.0587028468  
    9: 0.6183666639  
    10: 1.3552086624  
```  
  
Tercera ejecución:  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1000  
Enter an integer value for the sample count: 10  
 
min() == 4.94066e-324  
max() == 1.79769e+308  
n() == 1000.0000000000  
Distribution for 10 samples:  
    1: 958.5284624473  
    2: 958.7882787809  
    3: 963.0667684792  
    4: 987.9638091514  
    5: 1016.2433493745  
    6: 1021.9337111110  
    7: 1021.9723046240  
    8: 1035.7622110505  
    9: 1043.8725156645  
    10: 1054.7051509381  
```  
  
## <a name="requirements"></a>Requisitos  
**Encabezado:** \<random>  
  
**Espacio de nombres:** std  
  
##  <a name="chi_squared_distribution"></a>  chi_squared_distribution::chi_squared_distribution  
Construye la distribución.  
  
```  
explicit chi_squared_distribution(result_type n = 1.0);  
explicit chi_squared_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>Parámetros  
*n*  
El parámetro de distribución `n`.  
  
*parm*  
 La estructura de parámetros utilizada para construir la distribución.  
  
### <a name="remarks"></a>Comentarios  
**Condición previa:** `0.0 < n`  
  
El primer constructor crea un objeto cuyo almacenado `n` valor contiene el valor  *n* .  
  
El segundo constructor crea un objeto cuyos parámetros almacenados se inicializan desde *parm*. Los parámetros actuales de una distribución existente se pueden obtener y definir llamando a la función miembro `param()`.  
  
##  <a name="param_type"></a>  chi_squared_distribution::param_type  
Almacena los parámetros de la distribución.  
  
```cpp    
struct param_type {  
   typedef chi_squared_distribution<result_type> distribution_type;  
   param_type(result_type n = 1.0);
   result_type n() const;
   
   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  

### <a name="parameters"></a>Parámetros  
*n*  
El parámetro de distribución `n`.  
  
*right*  
El objeto `param_type` que se va a comparar con este.  
  
### <a name="remarks"></a>Comentarios  
**Condición previa:** `0.0 < n`  
  
Esta estructura se puede pasar al constructor de clases de la distribución en el momento de creación de instancias, a la función miembro `param()` para definir los parámetros almacenados de una distribución existente y a `operator()` para usarse en lugar de los parámetros almacenados.  
  
## <a name="see-also"></a>Vea también  
 [\<random>](../standard-library/random.md)



