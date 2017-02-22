---
title: "Comportamiento no est&#225;ndar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "compatibilidad y conformidad, comportamiento no estándar"
  - "específico de Microsoft, comportamiento del compilador"
  - "comportamiento no estándar, conformidad y compatibilidad"
ms.assetid: a57dea27-dc79-4f64-8a83-017e84841773
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Comportamiento no est&#225;ndar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En las próximas secciones se muestran algunos de los lugares en los que la implementación de Visual C\+\+ de C\+\+ no cumple con el estándar de C\+\+.  Los números de sección que se indican a continuación se refieren a los números de sección del estándar de C\+\+ 11 \(ISO\/IEC 14882:2011\(E\)\).  
  
 La lista de límites del compilador que difieren de los definidos en el estándar de C\+\+ se proporciona en [Límites del compilador](../cpp/compiler-limits.md).  
  
## Tipos de valor devueltos de covariante  
 Las clases base virtuales no se admiten como tipos devueltos de covariante cuando la función virtual tiene un número variable de argumentos.  Esto no cumple con el párrafo 7 de la sección 10.3 de la especificación ISO de C\+\+.  El ejemplo siguiente no se compila y se produce el error del compilador [C2688](../error-messages/compiler-errors-2/compiler-error-c2688.md)  
  
```cpp  
// CovariantReturn.cpp  
class A   
{  
   virtual A* f(int c, ...);   // remove ...  
};  
  
class B : virtual A  
{  
   B* f(int c, ...);   // C2688 remove ...  
};  
```  
  
## Enlazar nombres no dependientes en plantillas  
 En estos momentos, el compilador de Visual C\+\+ no admite nombres no dependientes al analizar una plantilla inicialmente.  Esto no cumple con la sección 14.6.3 de la especificación ISO de C\+\+.  Esto puede hacer que se vean las sobrecargas declaradas después de la plantilla \(pero antes de que se creen instancias de la plantilla\).  
  
```cpp  
#include <iostream>  
using namespace std;  
  
namespace N {  
   void f(int) { cout << "f(int)" << endl;}  
}  
  
template <class T> void g(T) {  
    N::f('a');   // calls f(char), should call f(int)  
}  
  
namespace N {  
    void f(char) { cout << "f(char)" << endl;}  
}  
  
int main() {  
    g('c');  
}  
// Output: f(char)  
  
```  
  
## Especificadores de excepciones de funciones  
 Los especificadores de excepciones de funciones distintos de `throw()` se analizan pero no se usan.  Esto no cumple con la sección 15.4 de la especificación ISO de C\+\+.  Por ejemplo:  
  
```cpp  
void f() throw(int); // parsed but not used  
void g() throw();    // parsed and used  
```  
  
 Para obtener más información sobre las especificaciones de excepciones, vea [Especificaciones de excepciones](../cpp/exception-specifications-throw-cpp.md).  
  
## char\_traits::eof\(\)  
 El estándar de C\+\+ indica que [char\_traits::eof](../Topic/char_traits::eof.md) no debe corresponder a un valor `char_type` válido.  El compilador de Visual C\+\+ exige esta restricción para el tipo `char`, pero no para el tipo `wchar_t`.  Esto no cumple con el requisito indicado en la tabla 62 de la sección 12.1.1 de la especificación ISO de C\+\+.  En el ejemplo siguiente se muestra esto.  
  
```cpp  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    char_traits<char>::int_type int2 = char_traits<char>::eof();  
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;  
  
    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();  
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;  
}  
```  
  
## Ubicación de almacenamiento de objetos  
 El estándar de C\+\+ \(sección 1.8, párrafo 6\) requiere que los objetos de C\+\+ completos tengan ubicaciones de almacenamiento únicas.  Sin embargo, con Visual C\+\+ hay casos en los que tipos sin miembros de datos compartirán una ubicación de almacenamiento con otros tipos mientras dure el objeto.