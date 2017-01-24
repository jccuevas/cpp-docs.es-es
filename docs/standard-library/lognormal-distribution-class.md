---
title: "lognormal_distribution (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.lognormal_distribution"
  - "tr1.lognormal_distribution"
  - "tr1::lognormal_distribution"
  - "std::tr1::lognormal_distribution"
  - "lognormal_distribution"
  - "random/std::tr1::lognormal_distribution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lognormal_distribution (clase)"
ms.assetid: f2d6a431-6c3a-4370-b12e-4adb4ddf6cc4
caps.latest.revision: 15
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# lognormal_distribution (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera una distribución log\-normal.  
  
## Sintaxis  
  
```  
template<class RealType = double> class lognormal_distribution { public:     // types     typedef RealType result_type;     struct param_type;     // constructor and reset functions     explicit lognormal_distribution(RealType m = 0.0, RealType s = 1.0);     explicit lognormal_distribution(const param_type& parm);     void reset();     // generating functions     template<class URNG>     result_type operator()(URNG& gen);     template<class URNG>     result_type operator()(URNG& gen, const param_type& parm);     // property functions     RealType m() const;     RealType s() const;     param_type param() const;     void param(const param_type& parm);     result_type min() const;     result_type max() const; };  
```  
  
#### Parámetros  
 `RealType`  
 Un tipo de resultado de punto flotante, el valor predeterminado es `double`.  Para obtener más información sobre los tipos posibles, vea [\<random\>](../standard-library/random.md).  
  
## Comentarios  
 La clase de plantilla describe una distribución que produce valores de un tipo de entero especificado por el usuario o de tipo `double` si no se proporciona ninguno, distribuido según la distribución log\-normal.  La tabla siguiente incluye vínculos a artículos sobre miembros individuales.  
  
||||  
|-|-|-|  
|[lognormal\_distribution::lognormal\_distribution](../Topic/lognormal_distribution::lognormal_distribution.md)|`lognormal_distribution::m`|`lognormal_distribution::param`|  
|`lognormal_distribution::operator()`|`lognormal_distribution::s`|[lognormal\_distribution::param\_type](../Topic/lognormal_distribution::param_type.md)|  
  
 Las funciones de propiedad `m()` y `s()` devuelven los valores para los parámetros de distribución almacenados `m` y `s`, respectivamente.  
  
 Para obtener más información sobre las clases de distribución y sus miembros, vea [\<random\>](../standard-library/random.md).  
  
 Para más detalles sobre la distribución log\-normal, vea el artículo de Wolfram MathWorld sobre la [distribución log\-normal](http://go.microsoft.com/fwlink/?LinkId=400917).  
  
## Ejemplo  
  
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
  
## Salida  
  
```  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'm' distribution parameter: 0  
Enter a floating point value for the 's' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
  
min() == -1.79769e+308  
max() == 1.79769e+308  
m() == 0.0000000000  
s() == 1.0000000000  
Distribution for 10 samples:  
          1:   0.3862809339  
          2:   0.4128865601  
          3:   0.4490576787  
          4:   0.4862035428  
          5:   0.5930607126  
          6:   0.8190778771  
          7:   0.8902379317  
          8:   2.8332911667  
          9:   5.1359445565  
         10:   5.4406507912  
```  
  
## Requisitos  
 **Encabezado:** \<random\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<random\>](../standard-library/random.md)