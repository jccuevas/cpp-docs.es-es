---
title: "complex&lt;double&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.complex<double>"
  - "complex<double>"
  - "std::complex<double>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "función complejo < double >"
ms.assetid: 0d0b9d2a-9b9b-410b-82a0-86b6df127e47
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# complex&lt;double&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que almacena un par ordenado de objetos, ambos de tipo **double***,* donde el primero representa la parte real de un número complejo y el segundo representa la parte imaginaria.  
  
## Sintaxis  
  
```  
template<>  
   class complex<double> {  
public:  
   constexpr complex(  
      double _RealVal = 0,   
      double _ImagVal = 0  
   );  
  
   constexpr complex(  
      const complex<double>& _ComplexNum  
   );  
   constexpr explicit complex(  
      const complex<long double>& _ComplexNum  
   );  
   // rest same as template class complex  
};  
```  
  
#### Parámetros  
 `_RealVal`  
 Valor de tipo **double** de la parte real del número complejo que se está construyendo.  
  
 `_ImagVal`  
 Valor de tipo **double** de la parte imaginaria del número complejo que se está construyendo.  
  
 `_ComplexNum`  
 Número complejo de tipo **float** o de tipo `long double` cuyas partes reales e imaginarias se usan para inicializar el número complejo de tipo **double** que se está construyendo.  
  
## Valor devuelto  
 Número complejo de tipo **double**.  
  
## Comentarios  
 La especialización explícita de la clase de plantilla compleja en una clase compleja de tipo **double** solo se distingue de la clase de plantilla en los constructores que define. Se permite que la conversión de **float** a **double** sea implícita, pero la conversión de `long double` a **double** debe ser **explícita**. El uso de la conversión **explícita** descarta el inicio con la conversión de tipos mediante sintaxis de asignación.  
  
 Para obtener más información sobre la clase de plantilla `complex`, consulte [complex \(Clase\)](../standard-library/complex-class.md). Para obtener una lista de los miembros de la clase de plantilla `complex`, vea .  
  
## Ejemplo  
  
```  
// complex_comp_dbl.cpp  
// compile with: /EHsc  
#include <complex>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   double pi = 3.14159265359;  
  
   // The first constructor specifies real & imaginary parts  
   complex <double> c1 ( 4.0 , 5.0 );  
   cout << "Specifying initial real & imaginary parts,\n"  
        << " as type double gives c1 = " << c1 << endl;  
  
   // The second constructor initializes values of the real &  
   // imaginary parts using those of complex number of type float  
   complex <float> c2float ( 4.0 , 5.0 );  
   complex <double> c2double ( c2float );  
   cout << "Implicit conversion from type float to type double,"  
        << "\n gives c2double = " << c2double << endl;  
  
   // The third constructor initializes values of the real &  
   // imaginary parts using those of a complex number  
   // of type long double  
   complex <long double> c3longdouble ( 4.0 , 5.0 );  
   complex <double> c3double ( c3longdouble );  
   cout << "Explicit conversion from type float to type double,"  
        << "\n gives c3longdouble = " << c3longdouble << endl;  
  
   // The modulus and argument of a complex number can be recovered  
   double absc3 = abs ( c3longdouble );  
   double argc3 = arg ( c3longdouble );  
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "  
        << absc3 << endl;  
   cout << "Argument of c3 is recovered from c3 using:\n arg ( c3 ) = "  
        << argc3 << " radians, which is " << argc3 * 180 / pi  
        << " degrees." << endl;  
}  
```  
  
 **Especificar partes imaginarias & real iniciales, como tipo doble proporciona c1 \= \(4,5\) conversión implícita de tipo float a tipo double, c2double ofrece \= \(4,5\) conversión explícita de tipo float a tipo double, da c3longdouble \= \(4,5\) el módulo de c3 se recupera utilizando c3: abs \(c3\) \= 6.40312 argumento de c3 se recupera utilizando c3: arg \(c3\) \= 0.896055 radianes, que es 51.3402 grados.**   
## Requisitos  
 **Encabezado:** \<complex\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [complex \(Clase\)](../standard-library/complex-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)