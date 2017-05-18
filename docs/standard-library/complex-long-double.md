---
title: complex&lt;long double&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::complex<long double>
- complex<long double>
- std.complex<long double>
dev_langs:
- C++
helpviewer_keywords:
- complex<long double> function
ms.assetid: 37591991-b385-46e9-b727-d534dbc10432
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 75e4e8bc79cb972c19e200a4d8fc1340535cd297
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="complexltlong-doublegt"></a>complex&lt;long double&gt;
Describe un objeto que almacena un par ordenado de objetos, ambos de tipo `long double`, donde el primero representa la parte real de un número complejo y el segundo representa la parte imaginaria.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <>
class complex<long double> {
public:
    constexpr complex(
    long double _RealVal = 0,
    long double _ImagVal = 0);

complex(
    constexpr complex<long double>& complexNum);
// rest same as template class complex
};
```  
  
#### <a name="parameters"></a>Parámetros  
 `_RealVal`  
 Valor de tipo **long double** de la parte real del número complejo que se está construyendo.  
  
 `_ImagVal`  
 Valor de tipo `long double` de la parte imaginaria del número complejo que se está construyendo.  
  
 `complexNum`  
 Número complejo de tipo **double** o **float** cuyas partes reales e imaginarias se usan para inicializar un número complejo de tipo `long double` que se está construyendo.  
  
## <a name="return-value"></a>Valor devuelto  
 Número complejo de tipo `long double`.  
  
## <a name="remarks"></a>Comentarios  
 La especialización explícita de la clase de plantilla compleja en una clase compleja de tipo `long double` solo se distingue de la clase de plantilla en los constructores que define. Se permite que la conversión de `long double` a **float** sea implícita, pero la conversión de **double** a `long double` debe ser **explícita**. El uso de la conversión **explícita** descarta el inicio con la conversión de tipos mediante sintaxis de asignación.  
  
 Para obtener más información sobre la clase de plantilla `complex`, vea [complex (Clase)](../standard-library/complex-class.md). Para obtener una lista de los miembros de la clase de plantilla `complex`, vea .  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// complex_comp_ld.cpp  
// compile with: /EHsc  
#include <complex>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   double pi = 3.14159265359;  
  
   // The first constructor specifies real & imaginary parts  
   complex <long double> c1 ( 4.0 , 5.0 );  
   cout << "Specifying initial real & imaginary parts,\n"  
        << " as type float gives c1 = " << c1 << endl;  
  
   // The second constructor initializes values of the real &  
   // imaginary parts using those of complex number of type float  
   complex <float> c2float ( 1.0 , 3.0 );  
   complex <long double> c2longdouble ( c2float );  
   cout << "Implicit conversion from type float to type long double,"  
        << "\n gives c2longdouble = " << c2longdouble << endl;  
  
   // The third constructor initializes values of the real &  
   // imaginary parts using those of a complex number  
   // of type double  
   complex <double> c3double ( 3.0 , 4.0 );  
   complex <long double> c3longdouble ( c3double );  
   cout << "Implicit conversion from type long double to type float,"  
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
\* Output:   
Specifying initial real & imaginary parts,  
 as type float gives c1 = (4,5)  
Implicit conversion from type float to type long double,  
 gives c2longdouble = (1,3)  
Implicit conversion from type long double to type float,  
 gives c3longdouble = (3,4)  
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 5  
Argument of c3 is recovered from c3 using:  
 arg ( c3 ) = 0.927295 radians, which is 53.1301 degrees.  
*\  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado**: \<complex>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [complex (Clase)](../standard-library/complex-class.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)




