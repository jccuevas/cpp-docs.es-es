---
title: "geometric_distribution (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.geometric_distribution"
  - "random/std::tr1::geometric_distribution"
  - "tr1::geometric_distribution"
  - "tr1.geometric_distribution"
  - "geometric_distribution"
  - "std::tr1::geometric_distribution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "geometric_distribution (clase)"
  - "geometric_distribution (clase) [TR1]"
ms.assetid: 38f933af-3b49-492e-9d26-b6b272a60013
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# geometric_distribution (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera una distribución geométrica.  
  
## Sintaxis  
  
```  
template<class IntType = int> class geometric_distribution { public:     // types     typedef IntType result_type;     struct param_type;     // constructors and reset functions     explicit geometric_distribution(double p = 0.5);     explicit geometric_distribution(const param_type& parm);     void reset();     // generating functions     template<class URNG>     result_type operator()(URNG& gen);     template<class URNG>     result_type operator()(URNG& gen, const param_type& parm);     // property functions     double p() const;     param_type param() const;     void param(const param_type& parm);     result_type min() const;     result_type max() const; };  
```  
  
#### Parámetros  
 `IntType`  
 Tipo de resultado de entero, su valor predeterminado es `int`.  Para conocer los posibles tipos, vea [\<random\>](../standard-library/random.md).  
  
## Comentarios  
 La clase de plantilla describe una distribución que genera valores de un tipo integral especificado por el usuario con la distribución geométrica.  En la siguiente tabla encontrará vínculos que llevan a artículos sobre miembros individuales.  
  
||||  
|-|-|-|  
|[geometric\_distribution::geometric\_distribution](../Topic/geometric_distribution::geometric_distribution.md)|`geometric_distribution::p`|`geometric_distribution::param`|  
|`geometric_distribution::operator()`||[geometric\_distribution::param\_type](../Topic/geometric_distribution::param_type.md)|  
  
 La función de propiedad `p()` devuelve el valor de parámetro de distribución `p` almacenado.  
  
 Para más información sobre las clases de distribución y sus correspondientes miembros, vea [\<random\>](../standard-library/random.md).  
  
 Para ver información detallada sobre la distribución chi cuadrado, consulte el artículo de Wolfram MathWorld sobre la [distribución geométrica](http://go.microsoft.com/fwlink/?LinkId=400529).  
  
## Ejemplo  
  
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
  
## Salida  
 Primera prueba:  
  
  **Use CTRL\+Z para omitir la entrada de datos y ejecutar con los valores predeterminados.  Escriba un valor de punto flotante para el parámetro de distribución “p”:**  
**Escriba un valor entero para el recuento de muestras: 100**  
**min\(\) \=\= 0**  
**max\(\) \=\= 2147483647**  
**p\(\) \=\= 0.5000000000**  
**Distribución de 100 muestras:**  
 **0 ::::::::::::::::::::::::::::::::::::::::::::::::::::**  
 **1 ::::::::::::::::::::::::**  
 **2 ::::::::::::::**  
 **3 :::::**  
 **4 ::**  
 **5 ::**  
 **6 :**  Segunda prueba:  
  
  **Use CTRL\+Z para omitir la entrada de datos y ejecutar con los valores predeterminados.  Escriba un valor de punto flotante para el parámetro de distribución “p”: .1**  
**Escriba un valor entero para el recuento de muestras: 100**  
**min\(\) \=\= 0**  
**max\(\) \=\= 2147483647**  
**p\(\) \=\= 0.1000000000**  
**Distribución de 100 muestras:**  
 **0 :::::::::**  
 **1 :::::::::::**  
 **2 :::::::**  
 **3 ::::::::**  
 **4 ::::::::**  
 **5 ::::::**  
 **6 :::::**  
 **7 ::::::**  
 **8 :::::**  
 **9 ::::**  
 **10 ::::**  
 **11 ::**  
 **12 :**  
 **13 :**  
 **14 :::**  
 **15 ::::**  
 **16 :::**  
 **17 :**  
 **18 :**  
 **19 :**  
 **20 ::**  
 **21 :**  
 **22 :**  
 **23 :**  
 **28 ::**  
 **33 :**  
 **35 :**  
 **40 :**    
## Requisitos  
 **Encabezado:** \<random\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<random\>](../standard-library/random.md)