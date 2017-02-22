---
title: "discrete_distribution (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "random/std::tr1::discrete_distribution"
  - "std::tr1::discrete_distribution"
  - "tr1.discrete_distribution"
  - "std.tr1.discrete_distribution"
  - "discrete_distribution"
  - "tr1::discrete_distribution"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "discrete_distribution (clase)"
ms.assetid: 8c8ba8f8-c06f-4f07-b354-f53950142fcf
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# discrete_distribution (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera una distribución de enteros discreta que tenga intervalos de ancho uniforme con probabilidad uniforme en cada intervalo.  
  
## Sintaxis  
  
```  
template<class IntType = int> class discrete_distribution { public:     // types     typedef IntType result_type;     struct param_type;     // constructor and reset functions     discrete_distribution();     template<class InputIterator>     discrete_distribution(InputIterator firstW, InputIterator lastW);     discrete_distribution(initializer_list<double> weightlist);     template<class UnaryOperation>     discrete_distribution(size_t count, double xmin, double xmax, UnaryOperation funcweight);     explicit discrete_distribution(const param_type& parm);     void reset();     // generating functions     template<class URNG>     result_type operator()(URNG& gen);     template<class URNG>     result_type operator()(URNG& gen, const param_type& parm);     // property functions     vector<double> probabilities() const;     param_type param() const;     void param(const param_type& parm);     result_type min() const;     result_type max() const; };  
```  
  
#### Parámetros  
 `IntType`  
 Un tipo de resultado de entero, el valor predeterminado es `int`.  Para obtener más información sobre los tipos posibles, vea [\<random\>](../standard-library/random.md).  
  
## Comentarios  
 Esta distribución de muestreo tiene intervalos de ancho uniforme con probabilidad uniforme en cada intervalo.  Para obtener información sobre otras distribuciones de muestreo, vea [piecewise\_linear\_distribution \(Clase\)](../standard-library/piecewise-linear-distribution-class.md) y [piecewise\_constant\_distribution \(Clase\)](../standard-library/piecewise-constant-distribution-class.md).  
  
 La tabla siguiente incluye vínculos a artículos sobre miembros individuales:  
  
|||  
|-|-|  
|[discrete\_distribution::discrete\_distribution](../Topic/discrete_distribution::discrete_distribution.md)|`discrete_distribution::param`|  
|`discrete_distribution::operator()`|[discrete\_distribution::param\_type](../Topic/discrete_distribution::param_type.md)|  
  
 La función de propiedad `vector<double> probabilities()` devuelve las probabilidades individuales de cada entero generado.  
  
 Para obtener más información sobre las clases de distribución y sus miembros, vea [\<random\>](../standard-library/random.md).  
  
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
  
    discrete_distribution<> distr({ 1, 2, 3, 4, 5 });  
  
    cout << endl;  
    cout << "min() == " << distr.min() << endl;  
    cout << "max() == " << distr.max() << endl;  
    cout << "probabilities (value: probability):" << endl;  
    vector<double> p = distr.probabilities();  
    int counter = 0;  
    for (const auto& n : p) {  
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
        cout << setw(5) << elem.first << ' ' << string(elem.second, ':') << endl;  
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
  **Utilice CTRL\-Z para omitir la entrada de datos y ejecutarlo con los valores predeterminados.  Introduzca un valor entero para el recuento de muestra: 100**  
**mín\(\) \=\= 0**  
**máx\(\) \=\= 4**  
**probabilidades \(valor: probabilidad\):**  
 **0:   0.0666666667**  
 **1:   0.1333333333**  
 **2:   0.2000000000**  
 **3:   0.2666666667**  
 **4:   0.3333333333**  
**Distribución para 100 muestras:**  
 **0 :::::**  
 **1 ::::::::::::::**  
 **2 :::::::::::::::::**  
 **3 ::::::::::::::::::::::::::::::**  
 **4 ::::::::::::::::::::::::::::::::::**    
## Requisitos  
 **Encabezado:** \<random\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<random\>](../standard-library/random.md)