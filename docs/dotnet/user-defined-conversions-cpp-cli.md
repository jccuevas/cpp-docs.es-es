---
title: Conversiones definidas por el usuario (C++ / CLI) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user-defined conversions [C++]
ms.assetid: 8010fd59-2775-4e9a-a6ed-58055032d66f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 721f7135814db0421165fed74e124a7a8fe58e99
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="user-defined-conversions-ccli"></a>Conversiones definidas por el usuario (C++/CLI)
Esta sección describen las conversiones definidas por el usuario (UDC) cuando uno de los tipos en la conversión es una instancia de un tipo de referencia o tipo de valor o referencia.  
  
## <a name="implicit-and-explicit-conversions"></a>Conversiones implícitas y explícitas  
 Una conversión definida por el usuario puede ser implícita o explícita.  Una conversión CDU debe ser implícita si la conversión no da como resultado una pérdida de información. En caso contrario, debe definirse un UDC explícita.  
  
 Constructor de una clase nativa se puede utilizar para convertir a un tipo de valor o referencia a una clase nativa.  
  
 Para obtener más información acerca de las conversiones, vea [conversión Boxing](../windows/boxing-cpp-component-extensions.md) y [conversiones estándar](../cpp/standard-conversions.md).  
  
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
  
 **Salida**  
  
```Output  
in N::N  
in N::N  
```  
  
## <a name="convert-from-operators"></a>Operadores de Convertir desde  
 Operadores de convertir desde crean un objeto de la clase en el que está definido el operador de un objeto de alguna otra clase.  
  
 Estándar de C++ no admite operadores de conversión; estándar de C++ utiliza constructores para este propósito. Sin embargo, al utilizar tipos CLR, Visual C++ proporcionan compatibilidad sintáctica para llamar a los operadores de conversión.  
  
 Para interoperar correctamente con otros lenguajes conformes a CLS, puede que desee ajustar cada constructor unario definido por el usuario para una clase dada con un operador de conversión correspondiente.  
  
 Operadores de conversión:  
  
-   Deben definirse como funciones estáticas.  
  
-   Puede ser implícita (para las conversiones que no pierden precisión como short a int) o explícita, cuando se puede producir una pérdida de precisión.  
  
-   Deben devolver un objeto de la clase contenedora.  
  
-   Debe tener el tipo "de" como el tipo de parámetro único.  
  
 El ejemplo siguiente muestra un implícita y explícita "convertir desde", el operador de conversión definida por el usuario (UDC).  
  
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
  
 **Salida**  
  
```Output  
in operator  
in constructor  
10  
1  
```  
  
## <a name="convert-to-operators"></a>Convertir a operadores  
 Operadores de conversión para convierten un objeto de la clase en el que está definido el operador a otro objeto. El ejemplo siguiente muestra un implícita, convertir en, el operador de conversión definida por el usuario:  
  
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
  
 **Salida**  
  
```Output  
10  
```  
  
 Un operador de conversión explícita definida por el usuario de convertir en es adecuado para las conversiones que podría perdieron datos de alguna manera. Para invocar un operador de conversión explícita, se debe usar una conversión.  
  
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
  
 **Salida**  
  
```Output  
10.3  
10  
```  
  
## <a name="to-convert-generic-classes"></a>Para convertir clases genéricas  
 Puede convertir una clase genérica a T.  
  
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
  
 **Salida**  
  
```Output  
True  
```  
  
 Un constructor que convierte toma un tipo y usa para crear un objeto.  Se llama a un constructor que convierte con inicialización directa solo; conversiones de tipos no invocará constructores de conversión. De forma predeterminada, constructores de conversión son explícitos para los tipos CLR.  
  
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
  
 **Salida**  
  
```Output  
5  
R  
```  
  
 En este ejemplo de código, una función de conversión estática implícita hace lo mismo que un constructor de conversión explícita.  
  
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
  
 **Salida**  
  
```Output  
13  
12  
500  
2000  
```  
  
## <a name="see-also"></a>Vea también  
 [Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md)