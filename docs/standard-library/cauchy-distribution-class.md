---
title: cauchy_distribution (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- random/std::cauchy_distribution
- random/std::cauchy_distribution::reset
- random/std::cauchy_distribution::a
- random/std::cauchy_distribution::b
- random/std::cauchy_distribution::param
- random/std::cauchy_distribution::min
- random/std::cauchy_distribution::max
- random/std::cauchy_distribution::operator()
- random/std::cauchy_distribution::param_type
- random/std::cauchy_distribution::param_type::a
- random/std::cauchy_distribution::param_type::b
- random/std::cauchy_distribution::param_type::operator==
- random/std::cauchy_distribution::param_type::operator!=
dev_langs: C++
helpviewer_keywords:
- std::cauchy_distribution [C++]
- std::cauchy_distribution [C++], reset
- std::cauchy_distribution [C++], a
- std::cauchy_distribution [C++], b
- std::cauchy_distribution [C++], param
- std::cauchy_distribution [C++], min
- std::cauchy_distribution [C++], max
- std::cauchy_distribution [C++], param_type
- std::cauchy_distribution [C++], param_type
ms.assetid: 21522351-f2f1-46d9-97f0-d358c932356c
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 53ecdd04ebb24c6380e61f8bc5536d24df4dc21b
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="cauchydistribution-class"></a>cauchy_distribution (Clase)
Genera una distribución de Cauchy.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class RealType = double>  
class cauchy_distribution {  
public:  
   // types 
   typedef RealType result_type;  
   struct param_type;  
   
   // constructor and reset functions  
   explicit cauchy_distribution(result_type a = 0.0, result_type b = 1.0);
   explicit cauchy_distribution(const param_type& parm);
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
*RealType*  
Un tipo de resultado de punto flotante, el valor predeterminado es `double`. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).  
  
*URNG* El motor de generador de números aleatorios uniformes. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).  

## <a name="remarks"></a>Comentarios  
La clase de plantilla describe una distribución que genera valores de un tipo de punto flotante especificado por el usuario (o de tipo `double` si no se especifica ninguno) distribuidos según la distribución de Cauchy. La tabla siguiente incluye vínculos a artículos sobre miembros individuales.  
  
||||  
|-|-|-|  
|[cauchy_distribution](#cauchy_distribution)|`cauchy_distribution::a`|`cauchy_distribution::param`|  
|`cauchy_distribution::operator()`|`cauchy_distribution::b`|[param_type](#param_type)|  
  
Las funciones de propiedad `a()` y `b()` devuelven los valores respectivos para los parámetros de distribución almacenados `a` y `b`.  
  
El miembro de propiedad `param()` establece o devuelve el paquete de parámetros de distribución almacenado `param_type`.  

Las funciones miembro `min()` y `max()` devuelven el resultado posible más pequeño y el resultado posible más grande, respectivamente.  
  
La función miembro `reset()` descarta cualquier valor almacenado en caché, de modo que la siguiente llamada a `operator()` no depende de ningún valor obtenido del motor antes de la llamada.  
  
Las funciones miembro `operator()` devuelven el siguiente valor generado basado en el motor URNG, desde el paquete de parámetros actual o desde el paquete de parámetros especificado.
  
Para obtener más información sobre las clases de distribución y sus miembros, vea [\<random>](../standard-library/random.md).  
  
Para obtener información detallada sobre la distribución de Cauchy, vea el artículo de Wolfram MathWorld sobre la [distribución de Cauchy](http://go.microsoft.com/fwlink/p/?linkid=400523).  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const double a, const double b, const int s) {  
  
    // uncomment to use a non-deterministic generator  
    //    std::random_device gen;  
  
    std::mt19937 gen(1701);  
  
    std::cauchy_distribution<> distr(a, b);  
  
    std::cout << std::endl;  
    std::cout << "min() == " << distr.min() << std::endl;  
    std::cout << "max() == " << distr.max() << std::endl;  
    std::cout << "a() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.a() << std::endl;  
    std::cout << "b() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.b() << std::endl;  
  
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
    double a_dist = 0.0;  
    double b_dist = 1;  
  
    int samples = 10;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter a floating point value for the 'a' distribution parameter: ";  
    std::cin >> a_dist;  
    std::cout << "Enter a floating point value for the 'b' distribution parameter (must be greater than zero): ";  
    std::cin >> b_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(a_dist, b_dist, samples);  
}  
```  
  
Primera ejecución:  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'a' distribution parameter: 0  
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
 
min() == -1.79769e+308  
max() == 1.79769e+308  
a() == 0.0000000000  
b() == 1.0000000000  
Distribution for 10 samples:  
    1: -3.4650392984  
    2: -2.6369564174  
    3: -0.0786978867  
    4: -0.0609632093  
    5: 0.0589387400  
    6: 0.0589539764  
    7: 0.1004592006  
    8: 1.0965724260  
    9: 1.4389408122  
    10: 2.5253154706  
```  
  
Segunda ejecución:  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'a' distribution parameter: 0  
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 10  
Enter an integer value for the sample count: 10  
 
min() == -1.79769e+308  
max() == 1.79769e+308  
a() == 0.0000000000  
b() == 10.0000000000  
Distribution for 10 samples:  
    1: -34.6503929840  
    2: -26.3695641736  
    3: -0.7869788674  
    4: -0.6096320926  
    5: 0.5893873999  
    6: 0.5895397637  
    7: 1.0045920062  
    8: 10.9657242597  
    9: 14.3894081218  
    10: 25.2531547063  
```  
  
Tercera ejecución:  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'a' distribution parameter: 10  
Enter a floating point value for the 'b' distribution parameter (must be greater than zero): 10  
Enter an integer value for the sample count: 10  
 
min() == -1.79769e+308  
max() == 1.79769e+308  
a() == 10.0000000000  
b() == 10.0000000000  
Distribution for 10 samples:  
    1: -24.6503929840  
    2: -16.3695641736  
    3: 9.2130211326  
    4: 9.3903679074  
    5: 10.5893873999  
    6: 10.5895397637  
    7: 11.0045920062  
    8: 20.9657242597  
    9: 24.3894081218  
    10: 35.2531547063  
```  
  
## <a name="requirements"></a>Requisitos  
**Encabezado:** \<random>  
  
**Espacio de nombres:** std  
  
##  <a name="cauchy_distribution"></a>  cauchy_distribution::cauchy_distribution  
Construye la distribución.  
  
```  
explicit cauchy_distribution(result_type a = 0.0, result_type b = 1.0);
explicit cauchy_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>Parámetros  
*a*  
El parámetro de distribución `a`.  
  
*b*  
El parámetro de distribución `b`.  
  
*parm*  
La estructura `param_type` usada para construir la distribución.  
  
### <a name="remarks"></a>Comentarios  
**Condición previa:** `0.0 < b`  
  
El primer constructor crea un objeto cuyo valor `a` almacenado contiene el valor *a* y cuyo valor `b` almacenado contiene el valor *b*.  
  
El segundo constructor crea un objeto cuyos parámetros almacenados se inicializan desde *parm*. Los parámetros actuales de una distribución existente se pueden obtener y definir llamando a la función miembro `param()`.  
  
##  <a name="param_type"></a>  cauchy_distribution::param_type  
Almacena todos los parámetros de la distribución.  
  
```cpp    
struct param_type {  
   typedef cauchy_distribution<result_type> distribution_type;  
   param_type(result_type a = 0.0, result_type b = 1.0);
   result_type a() const;
   result_type b() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  
  
### <a name="parameters"></a>Parámetros  
*a*  
El parámetro de distribución `a`.  
  
*b*  
El parámetro de distribución `b`.  
  
*right*  
El objeto `param_type` que se va a comparar con este.  
  
### <a name="remarks"></a>Comentarios  
**Condición previa:** `0.0 < b`  
  
Esta estructura se puede pasar al constructor de clases de la distribución en el momento de creación de instancias, a la función miembro `param()` para definir los parámetros almacenados de una distribución existente y a `operator()` para usarse en lugar de los parámetros almacenados.  
  
## <a name="see-also"></a>Vea también  
[\<random>](../standard-library/random.md)



