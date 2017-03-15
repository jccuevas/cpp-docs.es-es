---
title: "C&#243;mo: Usar safe_cast en C++/CLI | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "safe_cast (palabra clave) [C++], convertir a tipos básicos"
ms.assetid: 0fbc87d8-ecdf-4cd5-81f4-0d8cc18e2aff
caps.latest.revision: 18
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Usar safe_cast en C++/CLI
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se muestra cómo utilizar safe\_cast en aplicaciones de [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)] .  Para obtener información sobre safe\_cast en [!INCLUDE[cppwrt_short](../build/reference/includes/cppwrt_short_md.md)], vea [safe\_cast](../windows/safe-cast-cpp-component-extensions.md).  
  
## Convertir hacia arriba  
 Una conversión es una conversión de un tipo derivado en una de sus clases base.  Esta conversión es seguro y no requiere una notación de conversión explícita.  El ejemplo siguiente se muestra cómo realizar una hacia arriba, con `safe_cast` y sin él.  
  
```  
// safe_upcast.cpp  
// compile with: /clr  
using namespace System;  
interface class A {  
   void Test();  
};  
  
ref struct B : public A {  
   virtual void Test() {  
      Console::WriteLine("in B::Test");  
   }  
  
   void Test2() {  
      Console::WriteLine("in B::Test2");  
   }  
};  
  
ref struct C : public B {  
   virtual void Test() override {  
      Console::WriteLine("in C::Test");  
   };  
};  
  
int main() {  
   C ^ c = gcnew C;  
  
   // implicit upcast  
   B ^ b = c;  
   b->Test();  
   b->Test2();  
  
   // upcast with safe_cast  
   b = nullptr;  
   b = safe_cast<B^>(c);  
   b->Test();  
   b->Test2();  
}  
```  
  
  **en C::Test**  
**en B::Test2**  
**en C::Test**  
**en B::Test2**   
## Convertir hacia abajo  
 Una conversión en tipos inferiores es una conversión de una clase base a una clase que se deriva de la clase base.  Una conversión en tipos inferiores es seguro solo si el objeto que se resuelve en tiempo de ejecución aborda realmente un objeto de clase derivada.  A diferencia de `static_cast`, `safe_cast` realiza una comprobación dinámica y produce <xref:System.InvalidCastException> si la conversión.  
  
```  
// safe_downcast.cpp  
// compile with: /clr  
using namespace System;  
  
interface class A { void Test(); };  
  
ref struct B : public A {  
   virtual void Test() {   
      Console::WriteLine("in B::Test()");  
   }  
  
   void Test2() {   
      Console::WriteLine("in B::Test2()");  
   }  
};  
  
ref struct C : public B {  
   virtual void Test() override {   
      Console::WriteLine("in C::Test()");  
   }  
};  
  
interface class I {};  
  
value struct V : public I {};  
  
int main() {  
   A^ a = gcnew C();  
   a->Test();  
   B^ b = safe_cast<B^>(a);  
   b->Test();  
   b->Test2();  
  
   V v;   
   I^ i = v;   // i boxes V  
   V^ refv = safe_cast<V^>(i);   
  
   Object^ o = gcnew B;  
   A^ a2= safe_cast<A^>(o);  
}  
```  
  
  **en C::Test\(\)**  
**en C::Test\(\)**  
**en B::Test2\(\)**   
## safe\_cast con conversiones definidas por el usuario  
 El ejemplo siguiente muestra cómo puede utilizar `safe_cast` para invocar conversiones definidas por el usuario.  
  
```  
// safe_cast_udc.cpp  
// compile with: /clr  
using namespace System;  
value struct V;  
  
ref struct R {  
   int x;  
   R() {  
      x = 1;  
   }  
  
   R(int argx) {  
      x = argx;  
   }  
  
   static operator R::V^(R^ r);  
};  
  
value struct V {  
   int x;  
   static operator R^(V& v) {  
      Console::WriteLine("in operator R^(V& v)");  
      R^ r = gcnew R();  
      r->x = v.x;    
      return r;  
   }  
  
   V(int argx) {  
      x = argx;  
   }  
};  
  
   R::operator V^(R^ r) {  
      Console::WriteLine("in operator V^(R^ r)");  
      return gcnew V(r->x);  
   }  
  
int main() {  
   bool fReturnVal = false;  
   V v(2);  
   R^ r = safe_cast<R^>(v);   // should invoke UDC  
   V^ v2 = safe_cast<V^>(r);   // should invoke UDC  
}  
```  
  
  **en el operador R^ \(V& v**  
**en el operador V^ \(R^ r\)**   
## operaciones safe\_cast y boxing  
 **Conversión boxing**  
  
 La conversión boxing se define como conversión compilador\- inline, definido por el usuario.  Por consiguiente, puede utilizar `safe_cast` el cuadro un valor en el montón CLR.  
  
 El ejemplo siguiente se muestra la conversión boxing con tipos de valor simples y definido por el usuario.  Cuadros de `safe_cast` una variable de tipo de valor que está en el montón nativo para que se pueda asignar a una variable en la pila basura\- obtenida.  
  
```  
// safe_cast_boxing.cpp  
// compile with: /clr  
using namespace System;  
  
interface struct I {};  
  
value struct V : public I {   
   int m_x;  
  
   V(int i) : m_x(i) {}  
};  
  
int main() {  
   // box a value type  
   V v(100);  
   I^ i = safe_cast<I^>(v);  
  
   int x = 100;  
   V^ refv = safe_cast<V^>(v);  
   int^ refi = safe_cast<int^>(x);  
}  
```  
  
 El ejemplo siguiente se muestra que la conversión tiene prioridad sobre una conversión definida por el usuario en una operación de `safe_cast` .  
  
```  
// safe_cast_boxing_2.cpp  
// compile with: /clr  
static bool fRetval = true;  
  
interface struct I {};  
value struct V : public I {  
   int x;  
  
   V(int argx) {  
      x = argx;  
   }  
  
   static operator I^(V v) {  
      fRetval = false;  
      I^ pi = v;  
      return pi;  
   }  
};  
  
ref struct R {  
   R() {}  
   R(V^ pv) {}  
};  
  
int main() {  
   V v(10);  
   I^ pv = safe_cast<I^>(v);   // boxing will occur, not UDC "operator I^"  
}  
```  
  
 **Conversión unboxing**  
  
 Unboxing se define como conversión compilador\- inline, definido por el usuario.  Por consiguiente, puede utilizar `safe_cast` para unbox un valor en el montón CLR.  
  
 Unboxing es una conversión definida por el usuario, pero a diferencia de conversión boxing, unboxing debe ser explícito\- que, se debería realizar por `static_cast`, conversión de estilo C, o `safe_cast`; unboxing no se puede realizar de forma implícita.  
  
```  
// safe_cast_unboxing.cpp  
// compile with: /clr  
int main() {  
   System::Object ^ o = 42;  
   int x = safe_cast<int>(o);  
}  
```  
  
 El ejemplo siguiente muestra unboxing con tipos de valor y tipos primitivos.  
  
```  
// safe_cast_unboxing_2.cpp  
// compile with: /clr  
using namespace System;  
  
interface struct I {};  
  
value struct VI : public I {};  
  
void test1() {  
   Object^ o = 5;  
   int x = safe_cast<Int32>(o);  
}  
  
value struct V {  
   int x;  
   String^ s;  
};  
  
void test2() {  
   V localv;  
   Object^ o = localv;  
   V unboxv = safe_cast<V>(o);  
}  
  
void test3() {  
   V localv;  
   V^ o2 = localv;  
   V unboxv2 = safe_cast<V>(o2);  
}  
  
void test4() {  
   I^ refi = VI();  
   VI vi  = safe_cast<VI>(refi);  
}  
  
int main() {  
   test1();  
   test2();  
   test3();  
   test4();  
}  
```  
  
## safe\_cast y tipos genéricos  
 El ejemplo siguiente muestra cómo puede utilizar `safe_cast` para realizar una conversión en tipos inferiores con un tipo genérico.  
  
```  
// safe_cast_generic_types.cpp  
// compile with: /clr  
interface struct I {};  
  
generic<class T> where T:I  
ref struct Base {  
   T t;  
   void test1() {}  
};  
  
generic<class T> where T:I  
ref struct Derived:public Base <T> {};  
  
ref struct R:public I {};  
  
typedef Base<R^> GBase_R;  
typedef Derived<R^> GDerived_R;  
  
int main() {  
   GBase_R^ br = gcnew GDerived_R();  
   GDerived_R^ dr = safe_cast<GDerived_R^>(br);  
}  
```  
  
## Vea también  
 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)