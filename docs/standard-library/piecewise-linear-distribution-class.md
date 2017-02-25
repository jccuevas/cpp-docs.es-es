---
title: "piecewise_linear_distribution (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::tr1::piecewise_linear_distribution"
  - "tr1.piecewise_linear_distribution"
  - "piecewise_linear_distribution"
  - "std.tr1.piecewise_linear_distribution"
  - "random/std::tr1::piecewise_linear_distribution"
  - "tr1::piecewise_linear_distribution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "piecewise_linear_distribution (clase)"
ms.assetid: cd141152-7163-4754-8f98-c6d6500005e0
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# piecewise_linear_distribution (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera una distribución lineal a trozos que tenga intervalos de ancho variable con probabilidad variable linealmente en cada intervalo.  
  
## Sintaxis  
  
```  
template<class RealType = double>  
class piecewise_linear_distribution  
{  
public:  
    // types  
    typedef RealType result_type;  
    struct param_type;  
    // constructor and reset functions  
    piecewise_linear_distribution();  
    template<class InputIteratorI, class InputIteratorW>  
    piecewise_linear_distribution(InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);  
    template<class UnaryOperation>  
    piecewise_linear_distribution(initializer_list<RealType> intervals, UnaryOperation weightfunc);  
    template<class UnaryOperation>  
    piecewise_linear_distribution(size_t count, RealType xmin, RealType xmax, UnaryOperation weightfunc);  
    explicit piecewise_linear_distribution(const param_type& parm);  
    void reset();  
    // generating functions  
    template<class URNG>  
    result_type operator()(URNG& gen);  
    template<class URNG>  
    result_type operator()(URNG& gen, const param_type& parm);  
    // property functions  
    vector<result_type> intervals() const;  
    vector<result_type> densities() const;  
    param_type param() const;  
    void param(const param_type& parm);  
    result_type min() const;  
    result_type max() const;  
};  
```  
  
#### Parámetros  
 `RealType`  
 El tipo de resultado de punto flotante, el valor predeterminado es `double`. Para los tipos posibles, consulte [\<random\>](../standard-library/random.md).  
  
## Comentarios  
 Esta distribución de muestreo tiene intervalos de ancho variable con probabilidad variable linealmente en cada intervalo. Para obtener más información sobre otras distribuciones de muestreo, vea [piecewise\_constant\_distribution](../standard-library/piecewise-constant-distribution-class.md) y [discrete\_distribution](../standard-library/discrete-distribution-class.md).  
  
 La tabla siguiente incluye vínculos a artículos sobre miembros individuales:  
  
||||  
|-|-|-|  
|[piecewise\_linear\_distribution::piecewise\_linear\_distribution](../Topic/piecewise_linear_distribution::piecewise_linear_distribution.md)|`piecewise_linear_distribution::intervals`|`piecewise_linear_distribution::param`|  
|`piecewise_linear_distribution::operator()`|`piecewise_linear_distribution::densities`|[piecewise\_linear\_distribution::param\_type](../Topic/piecewise_linear_distribution::param_type.md)|  
  
 La función de propiedad `intervals()` devuelve un `vector<RealType>` con el conjunto de intervalos almacenados de la distribución.  
  
 La función de la propiedad `densities()` devuelve un `vector<RealType>` con las densidades almacenadas para cada conjunto de intervalos, que se calculan según los pesos proporcionados en los parámetros del constructor.  
  
 Para obtener más información acerca de las clases de distribución y sus miembros, consulte [\<random\>](../standard-library/random.md).  
  
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
    vector<double> weights{ 1, 5, 5, 10 };  
  
    piecewise_linear_distribution<double> distr(intervals.begin(), intervals.end(), weights.begin());  
  
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
        cout << setw(5) << elem.first << '-' << elem.first + 1 << ' ' << string(elem.second, ':') << endl;  
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
  
```Output  
Utilice CTRL-Z para omitir la entrada de datos y ejecutarlo con valores predeterminados. Escriba un valor entero para el recuento de muestras: 100min() == 0max() == 15intervals (índice: intervalo): 0: 0,0000000000 1: 1.0000000000 2: 6.0000000000 3: 15.0000000000densities (índice: densidad): 0: 0.0645161290 1: 0.3225806452 2: 0.3225806452 3: 0.6451612903Distribution para 100 muestras: 0-1::: 1 y 2::: 2-3::: 3 y 4::: 4-5::: 5 y 6::: 6-7::: 7-8::: 8-9::: 9-10::: 10-11: 11-12::: 12 y 13::: 13 y 14::: 14 y 15:::  
```  
  
## Requisitos  
 **Encabezado:** \<random\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<random\>](../standard-library/random.md)