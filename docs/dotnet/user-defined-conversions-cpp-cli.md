---
title: "Conversiones definidas por el usuario (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "conversiones definidas por el usuario [C++]"
ms.assetid: 8010fd59-2775-4e9a-a6ed-58055032d66f
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conversiones definidas por el usuario (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En esta sección se describen las conversiones definidas por el usuario \(UDC\) cuando uno de los tipos de conversión es una referencia o una instancia de un tipo de valor o un tipo de referencia.  
  
## Conversiones implícitas y explícitas  
 Una conversión definida por el usuario puede ser implícita o explícita.  Una CDU debe ser implícita si la conversión no se produce una pérdida de información.  Si no una CDU explícita debe definirse.  
  
 El constructor nativo de una clase se puede utilizar para convertir la referencia o un tipo de valor a una clase nativa.  
  
 Para obtener más información sobre conversiones, vea [Conversión boxing](../windows/boxing-cpp-component-extensions.md) y [Conversiones estándar](../cpp/standard-conversions.md).  
  
```  
// mcpp_User_Defined_Conversions.cpp  
// compile with: /clr  
#include "stdio.h"  
ref class R;  
class N;  
  
value class V {  
   static operator V(R^) {  
      return V();  
   }  
};  
  
ref class R {  
public:  
   static operator N(R^);  
   static operator V(R^) {  
      System::Console::WriteLine("in R::operator N");  
      return V();  
   }  
};  
  
class N {  
public:  
   N(R^) {  
      printf("in N::N\n");  
   }  
};  
  
R::operator N(R^) {  
   System::Console::WriteLine("in R::operator N");  
   return N(nullptr);  
}  
  
int main() {  
   // Direct initialization:  
   R ^r2;  
   N n2(r2);   // direct initialization, calls constructor  
   static_cast<N>(r2);   // also direct initialization  
  
   R ^r3;  
   // ambiguous V::operator V(R^) and R::operator V(R^)  
   // static_cast<V>(r3);     
}  
```  
  
 **Resultados**  
  
  **en N::N**  
**en N::N**   
## Convertido\-De Operators  
 Convertido\- de operators crea un objeto de clase en la que definen el operador de un objeto de algún otro tipo.  
  
 C\+\+ estándar no admite a convertido\-de operators; C\+\+ estándar utiliza constructores con este fin.  Sin embargo, al utilizar los tipos de CLR, Visual C\+\+ proporciona compatibilidad sintáctico para calling convertido\- de operators.  
  
 Para interoperar correctamente con otros lenguajes conformes a CLS, conviene ajustar a cada constructor singular definida por el usuario para una clase determinada con un convertido\- de correspondiente operator.  
  
 Convertido\-de operators:  
  
-   Se definirá como funciones estáticas.  
  
-   Puede ser implícitamente \(para las conversiones para seguir la precisión como cortocircuito\-a\- int\) o explícito, cuando puede producirse una pérdida de precisión.  
  
-   Devolverá un objeto de la clase contenedora.  
  
-   Tendrá “de tipo como el único tipo de parámetro.  
  
 El ejemplo siguiente se muestra un implícito y explícito “convertido\- de”, operador definido por el usuario de \(UDC\) de conversión.  
  
```  
// clr_udc_convert_from.cpp  
// compile with: /clr  
value struct MyDouble {  
   double d;  
  
   MyDouble(int i) {  
      d = static_cast<double>(i);  
      System::Console::WriteLine("in constructor");  
   }  
  
   // Wrap the constructor with a convert-from operator.  
   // implicit UDC because conversion cannot lose precision  
   static operator MyDouble (int i) {  
      System::Console::WriteLine("in operator");  
      // call the constructor  
      MyDouble d(i);  
      return d;  
   }  
  
   // an explicit user-defined conversion operator  
   static explicit operator signed short int (MyDouble) {  
      return 1;  
   }  
};  
  
int main() {  
   int i = 10;  
   MyDouble md = i;  
   System::Console::WriteLine(md.d);  
  
   // using explicit user-defined conversion operator requires a cast    
   unsigned short int j = static_cast<unsigned short int>(md);  
   System::Console::WriteLine(j);  
}  
```  
  
 **Resultados**  
  
  **en el operador**  
**en constructor**  
**10**  
**1**   
## Convertido\- operadores  
 Convertido\- operadores convierte un objeto de clase en la que se define el operador a otro objeto.  El ejemplo siguiente se muestra un implícitamente, convertido\- a, operador de conversión definida por el usuario:  
  
```  
// clr_udc_convert_to.cpp  
// compile with: /clr  
using namespace System;  
value struct MyInt {  
   Int32 i;  
  
   // convert MyInt to String^  
   static operator String^ ( MyInt val ) {  
      return val.i.ToString();  
   }  
  
   MyInt(int _i) : i(_i) {}  
};  
  
int main() {  
   MyInt mi(10);  
   String ^s = mi;  
   Console::WriteLine(s);  
}  
```  
  
 **Resultados**  
  
  **10** Un objeto definido por el usuario explícito convertido\- a operador de conversión es adecuado para las conversiones que potencialmente pierden datos de alguna manera.  Para invocar un explícito convertido\- a operador, una conversión debe utilizarse.  
  
```  
// clr_udc_convert_to_2.cpp  
// compile with: /clr  
value struct MyDouble {  
   double d;  
   // convert MyDouble to Int32  
   static explicit operator System::Int32 ( MyDouble val ) {  
      return (int)val.d;  
   }  
};  
  
int main() {  
   MyDouble d;  
   d.d = 10.3;  
   System::Console::WriteLine(d.d);  
   int i = 0;  
   i = static_cast<int>(d);  
   System::Console::WriteLine(i);  
}  
```  
  
 **Resultados**  
  
  **10.3**  
**10**   
## Para convertir clases genéricas  
 Puede convertir una clase genérica a t.  
  
```  
// clr_udc_generics.cpp  
// compile with: /clr  
generic<class T>   
public value struct V {  
   T mem;  
   static operator T(V v) {  
      return v.mem;  
   }  
  
   void f(T t) {  
      mem = t;  
   }  
};  
  
int main() {  
   V<int> v;  
   v.f(42);  
   int i = v;  
   i += v;  
   System::Console::WriteLine(i == (42 * 2) );  
}  
```  
  
 **Resultados**  
  
  **True** Un constructor que convierte toma un tipo y lo utiliza para crear un objeto.  Se llama a un constructor que desarrolla con la inicialización directa sólo; las conversiones no invocarán convertir constructores.  De forma predeterminada, cuando se convierten a constructores es explícito para tipos CLR.  
  
```  
// clr_udc_converting_constructors.cpp  
// compile with: /clr  
public ref struct R {  
   int m;  
   char c;  
  
   R(int i) : m(i) { }  
   R(char j) : c(j) { }  
};  
  
public value struct V {  
   R^ ptr;  
   int m;  
  
   V(R^ r) : ptr(r) { }  
   V(int i) : m(i) { }  
};  
  
int main() {   
   R^ r = gcnew R(5);  
  
   System::Console::WriteLine( V(5).m);  
   System::Console::WriteLine( V(r).ptr);  
}  
```  
  
 **Resultados**  
  
  **5**  
**R** En este ejemplo de código, una función de conversión estática implícita hace lo mismo que un constructor explícito de conversión.  
  
```  
public value struct V {  
   int m;  
   V(int i) : m(i) {}  
   static operator V(int i) {  
      V v(i*100);  
      return v;  
   }  
};  
  
public ref struct R {  
   int m;  
   R(int i) : m(i) {}  
   static operator R^(int i) {  
      return gcnew R(i*100);  
   }  
};  
  
int main() {  
   V v(13);   // explicit  
   R^ r = gcnew R(12);   // explicit  
  
   System::Console::WriteLine(v.m);  
   System::Console::WriteLine(r->m);  
  
   // explicit ctor can't be called here: not ambiguous  
   v = 5;  
   r = 20;  
  
   System::Console::WriteLine(v.m);  
   System::Console::WriteLine(r->m);  
}  
```  
  
 **Resultados**  
  
  **13**  
**12**  
**500**  
**2000**   
## Vea también  
 [Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md)