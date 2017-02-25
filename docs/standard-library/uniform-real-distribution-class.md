---
title: "uniform_real_distribution (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tr1::uniform_real_distribution"
  - "std::tr1::uniform_real_distribution"
  - "random/std::tr1::uniform_real_distribution"
  - "uniform_real_distribution"
  - "std.tr1.uniform_real_distribution"
  - "tr1.uniform_real_distribution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "uniform_real_distribution (clase)"
ms.assetid: 5cf906fd-0319-4984-b21b-98425cd7532d
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# uniform_real_distribution (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera una distribución de punto flotante uniforme \(todos los valores son probables en la misma medida\) dentro de un rango de salida inclusivo\-exclusivo.  
  
## Sintaxis  
  
```  
template<class RealType = double> class uniform_real_distribution { public:     // types     typedef RealType result_type;     struct param_type;     // constructors and reset functions     explicit uniform_real_distribution(RealType a = 0.0, RealType b = 1.0);     explicit uniform_real_distribution(const param_type& parm);     void reset();     // generating functions     template<class URNG>     result_type operator()(URNG& gen);     template<class URNG>     result_type operator()(URNG& gen, const param_type& parm);     // property functions     result_type a() const;     result_type b() const;     param_type param() const;     void param(const param_type& parm);     result_type min() const;     result_type max() const; };  
```  
  
#### Parámetros  
 `RealType`  
 Tipo de resultado de punto flotante, su valor predeterminado es `double`.  Para conocer los posibles tipos, vea [\<random\>](../standard-library/random.md).  
  
## Comentarios  
 La clase de plantilla describe una distribución inclusiva\-exclusiva que genera valores de un tipo de punto flotante integral especificado por el usuario con una distribución, de modo que cada valor es probable en igual medida.  En la siguiente tabla encontrará vínculos que llevan a artículos sobre miembros individuales.  
  
||||  
|-|-|-|  
|[uniform\_real\_distribution::uniform\_real\_distribution](../Topic/uniform_real_distribution::uniform_real_distribution.md)|`uniform_real_distribution::a`|`uniform_real_distribution::param`|  
|`uniform_real_distribution::operator()`|`uniform_real_distribution::b`|[uniform\_real\_distribution::param\_type](../Topic/uniform_real_distribution::param_type.md)|  
  
 El miembro de propiedad `a()` devuelve el límite mínimo almacenado actualmente de la distribución, mientras que `b()` devuelve el límite máximo.  En esta clase de distribución, estos valores máximo y mínimo son los mismos que los que devuelven las funciones de propiedad comunes `min()` y `max()` descritas en el tema [\<random\>](../standard-library/random.md).  
  
 Para más información sobre las clases de distribución y sus correspondientes miembros, vea [\<random\>](../standard-library/random.md).  
  
## Ejemplo  
  
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
  
## Salida  
  **Use CTRL\+Z para omitir la entrada de datos y ejecutar con los valores predeterminados.  Escriba un valor de punto flotante para el límite inferior de la distribución: .5**  
**Escriba un valor de punto flotante para el límite superior de la distribución: 1**  
**Escriba un valor entero para el recuento de muestras: 20**  
**límite inferior \=\= 0.5**  
**límite superior \=\= 1**  
**Distribución de 20 muestras:**  
 **1: 0.5144304741**  
 **2: 0.6003997192**  
 **3: 0.6060792968**  
 **4: 0.6270416650**  
 **5: 0.6295091197**  
 **6: 0.6437749373**  
 **7: 0.6513740058**  
 **8: 0.7062379346**  
 **9: 0.7117609406**  
 **10: 0.7206888566**  
 **11: 0.7423223702**  
 **12: 0.7826033033**  
 **13: 0.8112872958**  
 **14: 0.8440467608**  
 **15: 0.8461254641**  
 **16: 0.8598305065**  
 **17: 0.8640874069**  
 **18: 0.8770968361**  
 **19: 0.9397858282**  
 **20: 0.9804645012**    
## Requisitos  
 **Encabezado:** \<random\>  
  
 **Espacio de nombres:**  std  
  
## Vea también  
 [\<random\>](../standard-library/random.md)