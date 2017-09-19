---
title: piecewise_linear_distribution (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- piecewise_linear_distribution
- random/std::piecewise_linear_distribution
- random/std::piecewise_linear_distribution::reset
- random/std::piecewise_linear_distribution::intervals
- random/std::piecewise_linear_distribution::densities
- random/std::piecewise_linear_distribution::param
- random/std::piecewise_linear_distribution::min
- random/std::piecewise_linear_distribution::max
- random/std::piecewise_linear_distribution::operator()
- random/std::piecewise_linear_distribution::param_type
- random/std::piecewise_linear_distribution::param_type::intervals
- random/std::piecewise_linear_distribution::param_type::densities
- random/std::piecewise_linear_distribution::param_type::operator==
- random/std::piecewise_linear_distribution::param_type::operator!=
- random/std::piecewise_linear_distribution::param_type
dev_langs:
- C++
helpviewer_keywords:
- piecewise_linear_distribution class
ms.assetid: cd141152-7163-4754-8f98-c6d6500005e0
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: 4c98be8541c04dd9819fd459fad4cfdf25951a0c
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="piecewiselineardistribution-class"></a>piecewise_linear_distribution (Clase)
Genera una distribución lineal a trozos que tenga intervalos de ancho variable con probabilidad variable linealmente en cada intervalo.  
  
## <a name="syntax"></a>Sintaxis  
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
   template <class InputIteratorI, class InputIteratorW>  
   piecewise_linear_distribution(
      InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);
   template <class UnaryOperation>  
   piecewise_linear_distribution(
      initializer_list<result_type> intervals, UnaryOperation weightfunc);
   template <class UnaryOperation>  
   piecewise_linear_distribution(
      size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   explicit piecewise_linear_distribution(const param_type& parm);
   void reset();

   // generating functions  
   template <class URNG>  
   result_type operator()(URNG& gen);
   template <class URNG>  
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
#### <a name="parameters"></a>Parámetros  
 `RealType`  
 El tipo de resultado de punto flotante, el valor predeterminado es `double`. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).  
  
## <a name="remarks"></a>Comentarios  
 Esta distribución de muestreo tiene intervalos de ancho variable con probabilidad variable linealmente en cada intervalo. Para obtener más información sobre otras distribuciones de muestreo, vea [piecewise_linear_distribution](../standard-library/piecewise-constant-distribution-class.md) y [discrete_distribution](../standard-library/discrete-distribution-class.md).  
  
 La tabla siguiente incluye vínculos a artículos sobre miembros individuales:  
  
||||  
|-|-|-|  
|[piecewise_linear_distribution](#piecewise_linear_distribution)|`piecewise_linear_distribution::intervals`|`piecewise_linear_distribution::param`|  
|`piecewise_linear_distribution::operator()`|`piecewise_linear_distribution::densities`|[param_type](#param_type)|  
  
La función de propiedad `intervals()` devuelve un `vector<result_type>` con el conjunto de intervalos almacenados de la distribución.  
  
La función de la propiedad `densities()` devuelve un `vector<result_type>` con las densidades almacenadas para cada conjunto de intervalos, que se calculan según los pesos proporcionados en los parámetros del constructor.  
  
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
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for the sample count: 100
min() == 0
max() == 15
intervals (index: interval):
          0:   0.0000000000          
          1:   1.0000000000          
          2:   6.0000000000          
          3:  15.0000000000
densities (index: density):
          0:   0.0645161290
          1:   0.3225806452
          2:   0.3225806452
          3:   0.6451612903
Distribution for 100 samples:
    0-1 :::::::::::::::::::::
    1-2 ::::::
    2-3 :::
    3-4 :::::::
    4-5 ::::::
    5-6 ::::::
    6-7 :::::
    7-8 ::::::::::
    8-9 ::::::::::
    9-10 ::::::
   10-11 ::::
   11-12 :::
   12-13 :::
   13-14 :::::
   14-15 :::::  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<random>  
  
 **Espacio de nombres:** std  
  
##  <a name="piecewise_linear_distribution"></a> piecewise_linear_distribution::piecewise_linear_distribution  
 Construye la distribución.  
  
```  
 
// default constructor  
piecewise_linear_distribution();

 
// constructs using a range of intervals, [firstI, lastI), with  
// matching weights starting at firstW  
template <class InputIteratorI, class InputIteratorW>  
piecewise_linear_distribution(InputIteratorI firstI, InputIteratorI lastI, InputIteratorW firstW);

 
// constructs using an initializer list for range of intervals,  
// with weights generated by function weightfunc  
template <class UnaryOperation>  
piecewise_linear_distribution(initializer_list<RealType>  
intervals, UnaryOperation weightfunc);

 
// constructs using an initializer list for range of count intervals,  
// distributed uniformly over [xmin,xmax] with weights generated by function weightfunc  
template <class UnaryOperation>  
piecewise_linear_distribution(size_t count, RealType xmin, RealType xmax, UnaryOperation weightfunc);

 
// constructs from an existing param_type structure  
explicit piecewise_linear_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>Parámetros  
*firstI*  
Un iterador de entrada del primer elemento del intervalo de distribución.  
  
*lastI*  
Un iterador de entrada del último elemento del intervalo de distribución.  
  
*firstW*  
Un iterador de entrada del primer elemento del intervalo de pesos.  
  
*intervals*  
[initializer_list](../cpp/initializers.md) con los intervalos de la distribución.  
  
*count*  
Número de elementos del intervalo de distribución.  
  
*xmin*  
Valor mínimo del intervalo de distribución.  
  
*xmax*  
Valor máximo del intervalo de distribución. Debe ser mayor que *xmin*.  
  
*weightfunc*  
Objeto que representa la función de probabilidad de la distribución. Tanto el parámetro como el valor devuelto debe poder convertirse a `double`.  
  
*parm*  
La estructura de parámetros utilizada para construir la distribución.  
  
### <a name="remarks"></a>Comentarios  
El constructor predeterminado establece los parámetros almacenados, como que hay un intervalo, 0 a 1, con una densidad de probabilidad de 1.  
  
El constructor del intervalo de iterador  
  
```  
template <class InputIteratorI, class InputIteratorW>  
piecewise_linear_distribution(
    InputIteratorI firstI, 
    InputIteratorI lastI,  
    InputIteratorW firstW);
```  
  
construye un objeto de distribución con intervalos de iteradores sobre la secuencia [ `firstI`, `lastI`) y una secuencia de peso coincidente que empiece en `firstW`.  
  
El constructor de lista de inicializador  
  
```  
template <class UnaryOperation>  
piecewise_linear_distribution(
    initializer_list<result_type> intervals,   
    UnaryOperation weightfunc);
```  
  
construye un objeto de distribución con intervalos desde la lista de inicializador `intervals` y pesos generados desde la función `weightfunc`.  
  
El constructor definido como  
  
```  
template <class UnaryOperation>  
piecewise_linear_distribution(
    size_t count, 
    result_type xmin, 
    result_type xmax,  
    UnaryOperation weightfunc);
```  
  
construye un objeto de distribución con `count` intervalos distribuidos uniformemente en [`xmin,xmax`], asignando a cada intervalo pesos según la función `weightfunc`, y `weightfunc` debe aceptar un parámetro y tener un valor devuelto que puedan convertirse en `double`. **Condición previa:**`xmin < xmax`.  
  
El constructor definido como  
```  
explicit piecewise_linear_distribution(const param_type& parm);
```  
crea un objeto de distribución usando `parm` como la estructura de parámetros almacenados.  
  
##  <a name="param_type"></a> piecewise_linear_distribution::param_type  
Almacena todos los parámetros de la distribución.  
  
```  
struct param_type {  
   typedef piecewise_linear_distribution<result_type> distribution_type;  
   param_type();
   template <class IterI, class IterW>  
   param_type(
      IterI firstI, IterI lastI, IterW firstW);
   template <class UnaryOperation>  
   param_type(
      size_t count, result_type xmin, result_type xmax, UnaryOperation weightfunc);
   std::vector<result_type> densities() const;
   std::vector<result_type> intervals() const;
     
   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  

### <a name="parameters"></a>Parámetros  
Vea los parámetros del constructor para [piecewise_linear_distribution](#piecewise_linear_distribution).  
  
### <a name="remarks"></a>Comentarios  
 **Condición previa:** `xmin < xmax`  
  
Esta estructura se puede pasar al constructor de clases de la distribución en el momento de creación de instancias, a la función miembro `param()` para definir los parámetros almacenados de una distribución existente y a `operator()` para usarse en lugar de los parámetros almacenados.  
  
## <a name="see-also"></a>Vea también  
 [\<random>](../standard-library/random.md)




