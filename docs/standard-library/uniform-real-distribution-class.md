---
title: uniform_real_distribution (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- uniform_real_distribution
- std::uniform_real_distribution
- random/std::uniform_real_distribution
- std::uniform_real_distribution::reset
- random/std::uniform_real_distribution::reset
- std::uniform_real_distribution::a
- random/std::uniform_real_distribution::a
- std::uniform_real_distribution::b
- random/std::uniform_real_distribution::b
- std::uniform_real_distribution::param
- random/std::uniform_real_distribution::param
- std::uniform_real_distribution::min
- random/std::uniform_real_distribution::min
- std::uniform_real_distribution::max
- random/std::uniform_real_distribution::max
- std::uniform_real_distribution::operator()
- random/std::uniform_real_distribution::operator()
- std::uniform_real_distribution::param_type
- random/std::uniform_real_distribution::param_type
- std::uniform_real_distribution::param_type::a
- random/std::uniform_real_distribution::param_type::a
- std::uniform_real_distribution::param_type::b
- random/std::uniform_real_distribution::param_type::b
- std::uniform_real_distribution::param_type::operator==
- random/std::uniform_real_distribution::param_type::operator==
- std::uniform_real_distribution::param_type::operator!=
- random/std::uniform_real_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- uniform_real_distribution class
ms.assetid: 5cf906fd-0319-4984-b21b-98425cd7532d
caps.latest.revision: 18
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
translationtype: Machine Translation
ms.sourcegitcommit: 491992306060125ab91d64560113f7f8a3b740b1
ms.openlocfilehash: a7de3cf77ff7a70b13f57a1f06e015aa806c2a11
ms.lasthandoff: 02/24/2017

---
# <a name="uniformrealdistribution-class"></a>uniform_real_distribution (Clase)
Genera una distribución de punto flotante uniforme (todos los valores son probables en la misma medida) dentro de un rango de salida inclusivo-exclusivo.  
  
## <a name="syntax"></a>Sintaxis  
```  
template<class RealType = double>
   class uniform_real_distribution {
public:
   // types 
   typedef RealType result_type;
   struct param_type;

   // constructors and reset functions 
   explicit uniform_real_distribution(
      result_type a = 0.0, result_type b = 1.0);
   explicit uniform_real_distribution(const param_type& parm);
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
  
## <a name="remarks"></a>Comentarios  
La clase de plantilla describe una distribución inclusiva-exclusiva que genera valores de un tipo de punto flotante integral especificado por el usuario con una distribución, de modo que cada valor es probable en igual medida. La tabla siguiente incluye vínculos a artículos sobre miembros individuales.  
  
||||  
|-|-|-|  
|[uniform_real_distribution::uniform_real_distribution](#uniform_real_distribution__uniform_real_distribution)|`uniform_real_distribution::a`|`uniform_real_distribution::param`|  
|`uniform_real_distribution::operator()`|`uniform_real_distribution::b`|[uniform_real_distribution::param_type](#uniform_real_distribution__param_type)|  
  
El miembro de propiedad `a()` devuelve el límite mínimo de la distribución almacenado actualmente, mientras que `b()` devuelve el límite máximo almacenado actualmente. Para esta clase de distribución, estos valores mínimo y máximo son los mismos que los devueltos por las funciones de propiedad común `min()` y `max()` descritas en el tema [\<random>](../standard-library/random.md).  
  
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
  
void test(const double a, const double b, const int s) {  
  
    // uncomment to use a non-deterministic seed  
    //    std::random_device rd;  
    //    std::mt19937 gen(rd());  
    std::mt19937 gen(1729);  
  
    std::uniform_real_distribution<> distr(a,b);  
  
    std::cout << "lower bound == " << distr.a() << std::endl;  
    std::cout << "upper bound == " << distr.b() << std::endl;  
  
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
            << std::setprecision(10) << elem.first << std::endl;  
    }  
    std::cout << std::endl;  
}  
  
int main()  
{  
    double a_dist = 1.0;  
    double b_dist = 1.5;  
  
    int samples = 10;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter a floating point value for the lower bound of the distribution: ";  
    std::cin >> a_dist;  
    std::cout << "Enter a floating point value for the upper bound of the distribution: ";  
    std::cin >> b_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(a_dist, b_dist, samples);  
}  
  
```  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.
Enter a floating point value for the lower bound of the distribution: 0
Enter a floating point value for the upper bound of the distribution: 1
Enter an integer value for the sample count: 10
lower bound == 0
upper bound == 1
Distribution for 10 samples:
          1: 0.0288609485
          2: 0.2007994386
          3: 0.3027480117
          4: 0.4124758695
          5: 0.4413777133
          6: 0.4846447405
          7: 0.6225745916
          8: 0.6880935217
          9: 0.7541936723
         10: 0.8795716566
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<random>  
  
 **Espacio de nombres:** std  
  
##  <a name="a-nameuniformrealdistributionuniformrealdistributiona--uniformrealdistributionuniformrealdistribution"></a><a name="uniform_real_distribution__uniform_real_distribution"></a>  uniform_real_distribution::uniform_real_distribution  
Construye la distribución.  
  
```  
explicit uniform_real_distribution(result_type a = 0.0, result_type b = 1.0);
explicit uniform_real_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>Parámetros  
*a*  
Límite inferior para los valores aleatorios (incluido).  
  
*b*  
Límite superior para los valores aleatorios (excluido).  
  
*parm*  
La estructura `param_type` usada para construir la distribución.  
  
### <a name="remarks"></a>Comentarios  
 **Condición previa:** `a < b`  
  
El primer constructor crea un objeto cuyo valor `a` almacenado contiene el valor *a* y cuyo valor `b` almacenado contiene el valor *b*.  
  
El segundo constructor crea un objeto cuyos parámetros almacenados se inicializan desde *parm*. Los parámetros actuales de una distribución existente se pueden obtener y definir llamando a la función miembro `param()`.  
  
##  <a name="a-nameuniformrealdistributionparamtypea--uniformrealdistributionparamtype"></a><a name="uniform_real_distribution__param_type"></a>  uniform_real_distribution::param_type  
 Almacena todos los parámetros de la distribución.  
  
```  
struct param_type {  
   typedef uniform_real_distribution<result_type> distribution_type;  
   param_type(result_type a = 0.0, result_type b = 1.0);
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
Límite superior para los valores aleatorios (excluido).  
  
*right*  
El objeto `param_type` que se va a comparar con este.  
  
### <a name="remarks"></a>Comentarios  
 **Condición previa:** `a < b`  
  
Esta estructura se puede pasar al constructor de clases de la distribución en el momento de creación de instancias, a la función miembro `param()` para definir los parámetros almacenados de una distribución existente y a `operator()` para usarse en lugar de los parámetros almacenados.  
  
## <a name="see-also"></a>Vea también  
 [\<random>](../standard-library/random.md)




