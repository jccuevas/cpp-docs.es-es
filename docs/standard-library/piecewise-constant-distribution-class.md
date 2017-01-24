---
title: "piecewise_constant_distribution (Clase) | Microsoft Docs"
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
  - "std.tr1.piecewise_constant_distribution"
  - "tr1.piecewise_constant_distribution"
  - "tr1::piecewise_constant_distribution"
  - "std::tr1::piecewise_constant_distribution"
  - "random/std::tr1::piecewise_constant_distribution"
  - "piecewise_constant_distribution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "piecewise_constant_distribution (clase)"
ms.assetid: 2c9a21fa-623e-4d63-b827-3f1556b6dedb
caps.latest.revision: 23
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# piecewise_constant_distribution (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera una distribución constante a trozos que tiene intervalos de diversos anchos con probabilidad uniforme en cada intervalo.  
  
## Sintaxis  
  
```  
template<class RealType = double> class piecewise_constant_distribution { public:     // types     typedef RealType result_type;     struct param_type;     // constructor and reset functions     piecewise_constant_distribution();     template<class InputIteratorI, class InputIteratorW>     piecewise_constant_distribution(InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);     template<class UnaryOperation>     piecewise_constant_distribution(initializer_list<RealType> intervals, UnaryOperation weightfunc);     template<class UnaryOperation>     piecewise_constant_distribution(size_t count, RealType xmin, RealType xmax, UnaryOperation weightfunc);     explicit piecewise_constant_distribution(const param_type& parm);     void reset();     // generating functions     template<class URNG>     result_type operator()(URNG& gen);     template<class URNG>     result_type operator()(URNG& gen, const param_type& parm);     // property functions     vector<result_type> intervals() const;     vector<result_type> densities() const;     param_type param() const;     void param(const param_type& parm);     result_type min() const;     result_type max() const; };  
```  
  
#### Parámetros  
 `RealType`  
 Tipo de resultado de punto flotante, su valor predeterminado es `double`.  Para conocer los posibles tipos, vea [\<random\>](../standard-library/random.md).  
  
## Comentarios  
 Esta distribución de muestreo tiene intervalos de diversos anchos con probabilidad uniforme en cada intervalo.  Para más información sobre las distribuciones de muestreo, consulte [piecewise\_linear\_distribution \(Clase\)](../standard-library/piecewise-linear-distribution-class.md) y [discrete\_distribution](../standard-library/discrete-distribution-class.md).  
  
 En la siguiente tabla encontrará vínculos que llevan a artículos sobre miembros individuales:  
  
||||  
|-|-|-|  
|[piecewise\_constant\_distribution::piecewise\_constant\_distribution](../Topic/piecewise_constant_distribution::piecewise_constant_distribution.md)|`piecewise_constant_distribution::intervals`|`piecewise_constant_distribution::param`|  
|`piecewise_constant_distribution::operator()`|`piecewise_constant_distribution::densities`|[piecewise\_constant\_distribution::param\_type](../Topic/piecewise_constant_distribution::param_type.md)|  
  
 La función de propiedad `intervals()` devuelve un `vector<RealType>` con un conjunto de intervalos almacenados de la distribución.  
  
 La función de propiedad `densities()` devuelve un `vector<RealType>` con las densidades almacenadas de cada conjunto de intervalos, que ser calculan según los pesos reflejados en los parámetros del constructor.  
  
 Para más información sobre las clases de distribución y sus correspondientes miembros, vea [\<random\>](../standard-library/random.md).  
  
## Ejemplo  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
using namespace std;  
  
void test(const int s) {  
  
    // uncomment to use a non-deterministic generator  
    // random_device rd;  
    // mt19937 gen(rd());  
    mt19937 gen(1701);  
  
    // Three intervals, non-uniform: 0 to 1, 1 to 6, and 6 to 15  
    vector<double> intervals{ 0, 1, 6, 15 };  
    // weights determine the densities used by the distribution  
    vector<double> weights{ 1, 5, 10 };  
  
    piecewise_constant_distribution<double> distr(intervals.begin(), intervals.end(), weights.begin());  
  
    cout << endl;  
    cout << "min() == " << distr.min() << endl;  
    cout << "max() == " << distr.max() << endl;  
    cout << "intervals (index: interval):" << endl;  
    vector<double> i = distr.intervals();  
    int counter = 0;  
    for (const auto& n : i) {  
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;  
        ++counter;  
    }  
    cout << endl;  
    cout << "densities (index: density):" << endl;  
    vector<double> d = distr.densities();  
    counter = 0;  
    for (const auto& n : d) {  
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;  
        ++counter;  
    }  
    cout << endl;  
  
    // generate the distribution as a histogram  
    map<int, int> histogram;  
    for (int i = 0; i < s; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    cout << "Distribution for " << s << " samples:" << endl;  
    for (const auto& elem : histogram) {  
        cout << setw(5) << elem.first << '-' << elem.first+1 << ' ' << string(elem.second, ':') << endl;  
    }  
    cout << endl;  
}  
  
int main()  
{  
    int samples = 100;  
  
    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;  
    cout << "Enter an integer value for the sample count: ";  
    cin >> samples;  
  
    test(samples);  
}  
  
```  
  
## Salida  
  **Use CTRL\+Z para omitir la entrada de datos y ejecutar con los valores predeterminados.  Escriba un valor entero para el recuento de muestras: 100**  
**min\(\) \=\= 0**  
**max\(\) \=\= 15**  
**intervals \(index: interval\):**  
 **0:   0.0000000000**  
 **1:   1.0000000000**  
 **2:   6.0000000000**  
 **3:  15.0000000000**  
**densities \(index: density\):**  
 **0:   0.0625000000**  
 **1:   0.0625000000**  
 **2:   0.0694444444**  
**Distribución de 100 muestras:**  
 **0\-1 :::::::**  
 **1\-2 ::::::**  
 **2\-3 :::::**  
 **3\-4 ::::::**  
 **4\-5 :::::::**  
 **5\-6 ::::::**  
 **6\-7 :::**  
 **7\-8 ::::::::::**  
 **8\-9 ::::::**  
 **9\-10 ::::::::::::**  
 **10\-11 :::::**  
 **11\-12 ::::::**  
 **12\-13 :::::::::**  
 **13\-14 ::::**  
 **14\-15 ::::::::**    
## Requisitos  
 **Encabezado:** \<random\>  
  
 **Espacio de nombres:**  std  
  
## Vea también  
 [\<random\>](../standard-library/random.md)   
 [piecewise\_linear\_distribution](../standard-library/piecewise-linear-distribution-class.md)