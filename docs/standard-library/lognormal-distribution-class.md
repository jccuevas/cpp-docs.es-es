---
title: Clase lognormal_distribution | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- lognormal_distribution
- random/std::lognormal_distribution
- random/std::lognormal_distribution::reset
- random/std::lognormal_distribution::m
- random/std::lognormal_distribution::s
- random/std::lognormal_distribution::param
- random/std::lognormal_distribution::min
- random/std::lognormal_distribution::max
- random/std::lognormal_distribution::operator()
- random/std::lognormal_distribution::param_type
- random/std::lognormal_distribution::param_type::m
- random/std::lognormal_distribution::param_type::s
- random/std::lognormal_distribution::param_type::operator==
- random/std::lognormal_distribution::param_type::operator!=
- random/std::lognormal_distribution::param_type
dev_langs:
- C++
helpviewer_keywords:
- lognormal_distribution class
ms.assetid: f2d6a431-6c3a-4370-b12e-4adb4ddf6cc4
caps.latest.revision: 15
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 3c5d969e7250987471f88579d30e36d7838a9ed1
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="lognormaldistribution-class"></a>lognormal_distribution (Clase)
Genera una distribución log-normal.  
  
## <a name="syntax"></a>Sintaxis  
```  
template <class RealType = double>  
class lognormal_distribution  
   {  
public:  
   // types  
   typedef RealType result_type;  
   struct param_type;  
   // constructor and reset functions  
   explicit lognormal_distribution(result_type m = 0.0, result_type s = 1.0);
   explicit lognormal_distribution(const param_type& parm);
   void reset();
   // generating functions  
   template <class URNG>  
   result_type operator()(URNG& gen);
   template <class URNG>  
   result_type operator()(URNG& gen, const param_type& parm);
   // property functions  
   result_type m() const;
   result_type s() const;
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
La clase de plantilla describe una distribución que produce valores de un tipo de entero especificado por el usuario o de tipo `double` si no se proporciona ninguno, distribuido según la distribución log-normal. La tabla siguiente incluye vínculos a artículos sobre miembros individuales.  
  
||||  
|-|-|-|  
|[lognormal_distribution](#lognormal_distribution)|`lognormal_distribution::m`|`lognormal_distribution::param`|  
|`lognormal_distribution::operator()`|`lognormal_distribution::s`|[param_type](#param_type)|  
  
Las funciones de propiedad `m()` y `s()` devuelven los valores para los parámetros de distribución almacenados *m* y *s*, respectivamente.  
  
El miembro de propiedad `param()` establece o devuelve el paquete de parámetros de distribución almacenado `param_type`.  

Las funciones miembro `min()` y `max()` devuelven el resultado posible más pequeño y el resultado posible más grande, respectivamente.  
  
La función miembro `reset()` descarta cualquier valor almacenado en caché, de modo que la siguiente llamada a `operator()` no depende de ningún valor obtenido del motor antes de la llamada.  
  
Las funciones miembro `operator()` devuelven el siguiente valor generado basado en el motor URNG, desde el paquete de parámetros actual o desde el paquete de parámetros especificado.
  
Para obtener más información sobre las clases de distribución y sus miembros, vea [\<random>](../standard-library/random.md).  
  
Para obtener más información sobre la distribución LogNormal, vea el artículo de Wolfram MathWorld sobre la [distribución LogNormal](http://go.microsoft.com/fwlink/LinkId=400917).  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
using namespace std;  
  
void test(const double m, const double s, const int samples) {  
  
    // uncomment to use a non-deterministic seed  
    //    random_device gen;  
    //    mt19937 gen(rd());  
    mt19937 gen(1701);  
  
    lognormal_distribution<> distr(m, s);  
  
    cout << endl;  
    cout << "min() == " << distr.min() << endl;  
    cout << "max() == " << distr.max() << endl;  
    cout << "m() == " << fixed << setw(11) << setprecision(10) << distr.m() << endl;  
    cout << "s() == " << fixed << setw(11) << setprecision(10) << distr.s() << endl;  
  
    // generate the distribution as a histogram  
    map<double, int> histogram;  
    for (int i = 0; i < samples; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    cout << "Distribution for " << samples << " samples:" << endl;  
    int counter = 0;  
    for (const auto& elem : histogram) {  
        cout << fixed << setw(11) << ++counter << ": "  
            << setw(14) << setprecision(10) << elem.first << endl;  
    }  
    cout << endl;  
}  
  
int main()  
{  
    double m_dist = 1;  
    double s_dist = 1;  
    int samples = 10;  
  
    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;  
    cout << "Enter a floating point value for the 'm' distribution parameter: ";  
    cin >> m_dist;  
    cout << "Enter a floating point value for the 's' distribution parameter (must be greater than zero): ";  
    cin >> s_dist;  
    cout << "Enter an integer value for the sample count: ";  
    cin >> samples;  
  
    test(m_dist, s_dist, samples);  
}  
```  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'm' distribution parameter: 0  
Enter a floating point value for the 's' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
 
min() == -1.79769e+308  
max() == 1.79769e+308  
m() == 0.0000000000  
s() == 1.0000000000  
Distribution for 10 samples:  
    1: 0.3862809339  
    2: 0.4128865601  
    3: 0.4490576787  
    4: 0.4862035428  
    5: 0.5930607126  
    6: 0.8190778771  
    7: 0.8902379317  
    8: 2.8332911667  
    9: 5.1359445565  
    10: 5.4406507912  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<random>  
  
 **Espacio de nombres:** std  
  
##  <a name="lognormal_distribution"></a>  lognormal_distribution::lognormal_distribution  
 Construye la distribución.  
  
```  
explicit lognormal_distribution(RealType m = 0.0, RealType s = 1.0);
explicit lognormal_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>Parámetros  
*m*  
El parámetro de distribución `m`.  
  
*s*  
El parámetro de distribución `s`.  
  
*parm*  
La estructura `param_type` usada para construir la distribución.  
  
### <a name="remarks"></a>Comentarios  
**Condición previa:** `0.0 < s`  
  
El primer constructor crea un objeto cuyo valor `m` almacenado contiene el valor *m* y cuyo valor `s` almacenado contiene el valor *s*.  
  
El segundo constructor crea un objeto cuyos parámetros almacenados se inicializan desde *parm*. Los parámetros actuales de una distribución existente se pueden obtener y definir llamando a la función miembro `param()`.  
  
##  <a name="param_type"></a>  lognormal_distribution::param_type  
Almacena los parámetros de la distribución.  
  
```  
struct param_type {  
   typedef lognormal_distribution<result_type> distribution_type;  
   param_type(result_type m = 0.0, result_type s = 1.0);
   result_type m() const;
   result_type s() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
};  
```    
### <a name="parameters"></a>Parámetros  
*m*  
El parámetro de distribución `m`.  
  
*s*  
El parámetro de distribución `s`.  
  
*right*  
La estructura `param_type` que se usa para comparar.  
  
### <a name="remarks"></a>Comentarios  
**Condición previa:** `0.0 < s`  
  
Esta estructura se puede pasar al constructor de clases de la distribución en el momento de creación de instancias, a la función miembro `param()` para definir los parámetros almacenados de una distribución existente y a `operator()` para usarse en lugar de los parámetros almacenados.  
  
## <a name="see-also"></a>Vea también  
[\<random>](../standard-library/random.md)


