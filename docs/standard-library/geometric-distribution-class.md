---
title: geometric_distribution (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- random/std::geometric_distribution
- random/std::geometric_distribution::reset
- random/std::geometric_distribution::p
- random/std::geometric_distribution::param
- random/std::geometric_distribution::min
- random/std::geometric_distribution::max
- random/std::geometric_distribution::operator()
- random/std::geometric_distribution::param_type
- random/std::geometric_distribution::param_type::p
- random/std::geometric_distribution::param_type::operator==
- random/std::geometric_distribution::param_type::operator!=
- random/std::geometric_distribution::param_type
dev_langs:
- C++
helpviewer_keywords:
- std::geometric_distribution [C++]
- std::geometric_distribution [C++], reset
- std::geometric_distribution [C++], p
- std::geometric_distribution [C++], param
- std::geometric_distribution [C++], min
- std::geometric_distribution [C++], max
- std::geometric_distribution [C++], param_type
- std::geometric_distribution [C++], param_type
ms.assetid: 38f933af-3b49-492e-9d26-b6b272a60013
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 21665d4ef570f7451e3c1f9739eafaf067659541
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="geometricdistribution-class"></a>geometric_distribution (Clase)
Genera una distribución geométrica.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class IntType = int>
class geometric_distribution {
public:    
    // types 
    typedef IntType result_type; 
    struct param_type;   
    
    // constructors and reset functions 
    explicit geometric_distribution(double p = 0.5);
    explicit geometric_distribution(const param_type& parm);
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
#### <a name="parameters"></a>Parámetros  
*IntType*  
Un tipo de resultado de entero, el valor predeterminado es `int`. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).  
  
*URNG* El motor de generador de números aleatorios uniformes. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).  
  
## <a name="remarks"></a>Comentarios  
La clase de plantilla describe una distribución que genera valores de un tipo integral especificado por el usuario con la distribución geométrica. La tabla siguiente incluye vínculos a artículos sobre miembros individuales.  
  
||||  
|-|-|-|  
|[geometric_distribution)](#geometric_distribution)|`geometric_distribution::p`|`geometric_distribution::param`|  
|`geometric_distribution::operator()`||[param_type](#param_type)|  
  
La función de propiedad `p()` devuelve el valor de parámetro de distribución `p` almacenado.  
  
El miembro de propiedad `param()` establece o devuelve el paquete de parámetros de distribución almacenado `param_type`.  

Las funciones miembro `min()` y `max()` devuelven el resultado posible más pequeño y el resultado posible más grande, respectivamente.  
  
La función miembro `reset()` descarta cualquier valor almacenado en caché, de modo que la siguiente llamada a `operator()` no depende de ningún valor obtenido del motor antes de la llamada.  
  
Las funciones miembro `operator()` devuelven el siguiente valor generado basado en el motor URNG, desde el paquete de parámetros actual o desde el paquete de parámetros especificado.
  
Para obtener más información sobre las clases de distribución y sus miembros, vea [\<random>](../standard-library/random.md).  
  
Para obtener información detallada sobre la distribución chi cuadrado, vea el artículo de Wolfram MathWorld sobre la [distribución geométrica](http://go.microsoft.com/fwlink/LinkId=400529).  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const double p, const int s) {  
  
    // uncomment to use a non-deterministic generator  
    //    std::random_device gen;  
    std::mt19937 gen(1701);  
  
    std::geometric_distribution<> distr(p);  
  
    std::cout << std::endl;  
    std::cout << "min() == " << distr.min() << std::endl;  
    std::cout << "max() == " << distr.max() << std::endl;  
    std::cout << "p() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.p() << std::endl;  
  
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
    double p_dist = 0.5;  
  
    int samples = 100;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter a floating point value for the \'p\' distribution parameter: ";  
    std::cin >> p_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(p_dist, samples);  
}  
```  
  
Primera prueba:  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'p' distribution parameter: .5
Enter an integer value for the sample count: 100

min() == 0
max() == 2147483647
p() == 0.5000000000
Distribution for 100 samples:
    0 :::::::::::::::::::::::::::::::::::::::::::::::::::::
    1 ::::::::::::::::::::::::::
    2 ::::::::::::
    3 ::::::
    4 ::
    5 :
```  
  
Segunda prueba:  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the 'p' distribution parameter: .1
Enter an integer value for the sample count: 100

min() == 0
max() == 2147483647
p() == 0.1000000000
Distribution for 100 samples:
    0 :::::::::
    1 :::::::::::
    2 ::::::::::
    3 :::::::
    4 :::::
    5 ::::::::
    6 :::
    7 ::::::
    8 :::::::
    9 :::::
   10 :::
   11 :::
   12 ::
   13 :
   14 :::
   15 ::
   16 :::
   17 :::
   20 :::::
   21 :
   29 :
   32 :
   35 :
```  
  
## <a name="requirements"></a>Requisitos  
**Encabezado:** \<random>  
  
**Espacio de nombres:** std  
  
##  <a name="geometric_distribution"></a>  geometric_distribution::geometric_distribution  
Construye la distribución.  
  
```  
explicit geometric_distribution(double p = 0.5);
explicit geometric_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>Parámetros  
*p*  
El parámetro de distribución `p`.  
  
*parm*  
La estructura de parámetros utilizada para construir la distribución.  
  
### <a name="remarks"></a>Comentarios  
**Condición previa:** `0.0 < p && p < 1.0`  
  
El primer constructor crea un objeto cuyo valor `p` almacenado contiene el valor *p*.  
  
El segundo constructor crea un objeto cuyos parámetros almacenados se inicializan desde *parm*. Los parámetros actuales de una distribución existente se pueden obtener y definir llamando a la función miembro `param()`.  
  
##  <a name="param_type"></a>  geometric_distribution::param_type  
Almacena los parámetros de la distribución.  
  
```  
struct param_type {  
   typedef geometric_distribution<result_type> distribution_type;  
   param_type(double p = 0.5);
   double p() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  
  
### <a name="parameters"></a>Parámetros  
*p*  
El parámetro de distribución `p`.  
  
*right*  
La instancia `param_type` que comparar con esta.  
  
### <a name="remarks"></a>Comentarios  
**Condición previa:** `0.0 < p && p < 1.0`  
  
Esta estructura se puede pasar al constructor de clases de la distribución en el momento de creación de instancias, a la función miembro `param()` para definir los parámetros almacenados de una distribución existente y a `operator()` para usarse en lugar de los parámetros almacenados.  
  
## <a name="see-also"></a>Vea también  
[\<random>](../standard-library/random.md)



