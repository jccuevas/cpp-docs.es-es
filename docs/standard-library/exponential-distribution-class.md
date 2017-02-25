---
title: "exponential_distribution (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::tr1::exponential_distribution"
  - "exponential_distribution"
  - "tr1::exponential_distribution"
  - "tr1.exponential_distribution"
  - "random/std::tr1::exponential_distribution"
  - "std.tr1.exponential_distribution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "exponential_distribution (clase)"
  - "exponential_distribution (clase) [TR1]"
ms.assetid: d54f3126-a09b-45f9-a30b-0d94d03bcdc9
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# exponential_distribution (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera una distribución exponencial.  
  
## Sintaxis  
  
```  
template<class RealType = double> class exponential_distribution { public:     // types     typedef RealType result_type;     struct param_type;     // constructors and reset functions     explicit exponential_distribution(RealType lambda = 1.0);     explicit exponential_distribution(const param_type& parm);     void reset();     // generating functions     template<class URNG>     result_type operator()(URNG& gen);     template<class URNG>     result_type operator()(URNG& gen, const param_type& parm);     // property functions     RealType lambda() const;     param_type param() const;     void param(const param_type& parm);     result_type min() const;     result_type max() const; };  
```  
  
#### Parámetros  
 `RealType`  
 Un tipo de resultado de punto flotante, el valor predeterminado es `double`.  Para obtener más información sobre los tipos posibles, vea [\<random\>](../standard-library/random.md).  
  
## Comentarios  
 La clase de plantilla describe una distribución que produce valores de un tipo de entero especificado por el usuario o de tipo `double` si no se proporciona ninguno, distribuido según la distribución exponencial.  La tabla siguiente incluye vínculos a artículos sobre miembros individuales.  
  
||||  
|-|-|-|  
|[exponential\_distribution::exponential\_distribution](../Topic/exponential_distribution::exponential_distribution.md)|`exponential_distribution::lambda`|`exponential_distribution::param`|  
|`exponential_distribution::operator()`||[exponential\_distribution::param\_type](../Topic/exponential_distribution::param_type.md)|  
  
 La función de propiedad `lambda()` devuelve el valor del parámetro de distribución almacenado `lambda`.  
  
 Para obtener más información sobre las clases de distribución y sus miembros, vea [\<random\>](../standard-library/random.md).  
  
 Para más detalles sobre la distribución exponencial, vea el artículo de Wolfram MathWorld sobre la [distribución exponencial](http://go.microsoft.com/fwlink/?LinkId=401098).  
  
## Ejemplo  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const double l, const int s) {  
  
    // uncomment to use a non-deterministic generator  
    //    std::random_device gen;  
    std::mt19937 gen(1701);  
  
    std::exponential_distribution<> distr(l);  
  
    std::cout << std::endl;  
    std::cout << "min() == " << distr.min() << std::endl;  
    std::cout << "max() == " << distr.max() << std::endl;  
    std::cout << "lambda() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.lambda() << std::endl;  
  
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
    double l_dist = 0.5;  
    int samples = 10;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter a floating point value for the 'lambda' distribution parameter (must be greater than zero): ";  
    std::cin >> l_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(l_dist, samples);  
}  
  
```  
  
## Salida  
  
```  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'lambda' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
  
min() == 0  
max() == 1.79769e+308  
lambda() == 1.0000000000  
Distribution for 10 samples:  
          1:   0.0936880533  
          2:   0.1225944894  
          3:   0.6443593183  
          4:   0.6551171649  
          5:   0.7313457551  
          6:   0.7313557977  
          7:   0.7590097389  
          8:   1.4466885214  
          9:   1.6434088411  
         10:   2.1201210996  
```  
  
## Requisitos  
 **Encabezado:** \<random\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<random\>](../standard-library/random.md)