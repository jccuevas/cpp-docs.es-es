---
title: "complex&lt;float&gt; | Microsoft Docs"
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
  - "std::complex<float>"
  - "std.complex<float>"
  - "complex<float>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "complex<float> (función)"
ms.assetid: 1178eb1e-39bd-4017-89cd-aea95f813939
caps.latest.revision: 23
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# complex&lt;float&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que almacena un par ordenado de objetos, ambos de tipo **float***,* donde el primero representa la parte real de un número complejo y el segundo la parte imaginaria.  
  
## Sintaxis  
  
```  
template<>  
   class complex<float> {  
public:  
   constexpr complex(  
      float _RealVal = 0,   
      float _ImagVal = 0  
   );  
  
   constexpr complex(  
      const complex<float>& _ComplexNum  
   );  
   constexpr complex(  
      const complex<double>& _ComplexNum  
   );  
   constexpr complex(  
      const complex<long double>& _ComplexNum  
   );  
   // rest same as template class complex  
};  
```  
  
#### Parámetros  
 `_RealVal`  
 Valor de tipo **float** de la parte real del número complejo que se está construyendo.  
  
 `_ImagVal`  
 Valor de tipo **float** de la parte imaginaria del número complejo que se está construyendo.  
  
 `_ComplexNum`  
 Número complejo de tipo **double** o de tipo `long double` cuyas partes reales e imaginarias se usan para inicializar el número complejo de tipo **float** que se está construyendo.  
  
## Valor devuelto  
 Número complejo de tipo **float**.  
  
## Comentarios  
 La especialización explícita de la clase de plantilla compleja en una clase compleja de tipo **float** solo se distingue de la clase de plantilla en los constructores que define.  Se permite que la conversión de **float** a **double** sea implícita, pero la conversión menos segura de **float** a `long double` debe ser **explícita**.  El uso de la conversión **explícita** descarta el inicio con la conversión de tipos mediante sintaxis de asignación.  
  
 Para obtener más información sobre la clase de plantilla `complex`, consulte [complex \(Clase\)](../standard-library/complex-class.md).  Para obtener una lista de los miembros de la clase de plantilla `complex`, vea .  
  
## Ejemplo  
  
```  
// complex_comp_flt.cpp  
// compile with: /EHsc  
#include <complex>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   double pi = 3.14159265359;  
  
   // The first constructor specifies real & imaginary parts  
   complex <float> c1 ( 4.0 , 5.0 );  
   cout << "Specifying initial real & imaginary parts,\n"  
        << " as type float gives c1 = " << c1 << endl;  
  
   // The second constructor initializes values of the real &  
   // imaginary parts using those of complex number of type double  
   complex <double> c2double ( 1.0 , 3.0 );  
   complex <float> c2float ( c2double );  
   cout << "Implicit conversion from type double to type float,"  
        << "\n gives c2float = " << c2float << endl;  
  
   // The third constructor initializes values of the real &  
   // imaginary parts using those of a complex number  
   // of type long double  
   complex <long double> c3longdouble ( 3.0 , 4.0 );  
   complex <float> c3float ( c3longdouble );  
   cout << "Explicit conversion from type long double to type float,"  
        << "\n gives c3float = " << c3float << endl;  
  
   // The modulus and argument of a complex number can be recovered  
   double absc3 = abs ( c3float);  
   double argc3 = arg ( c3float);  
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "  
        << absc3 << endl;  
   cout << "Argument of c3 is recovered from c3 using:\n arg ( c3 ) = "  
        << argc3 << " radians, which is " << argc3 * 180 / pi  
        << " degrees." << endl;  
}  
```  
  
  **Specifying initial real & imaginary parts,**  
 **as type float gives c1 \= \(4,5\)**  
**Implicit conversion from type double to type float,**  
 **gives c2float \= \(1,3\)**  
**Explicit conversion from type long double to type float,**  
 **gives c3float \= \(3,4\)**  
**The modulus of c3 is recovered from c3 using: abs \( c3 \) \= 5**  
**Argument of c3 is recovered from c3 using:**  
 **arg \( c3 \) \= 0.927295 radians, which is 53.1301 degrees.**   
## Requisitos  
 **Encabezado:** \<complex\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [complex \(Clase\)](../standard-library/complex-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)