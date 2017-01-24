---
title: "C&#243;mo: Definir y utilizar delegados (C++/CLI) | Microsoft Docs"
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
  - "delegados"
ms.assetid: 1cdf3420-89c1-47c0-b796-aa984020e0f8
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Definir y utilizar delegados (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se muestra cómo definir y utilizar los delegados de [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)].  
  
 Aunque .NET Framework proporciona varios delegados, quizás tenga que a veces definir nuevos delegados.  
  
 El ejemplo de código siguiente se define un delegado denominado `MyCallback`.  La función de código \- de control de eventos que se llama cuando es este nuevo delegado desencadenar\- debe tener un tipo de valor devuelto de `void` y tomar una referencia de <xref:System.String> .  
  
 La función principal utiliza un método estático definido por `SomeClass` para crear instancias del delegado de `MyCallback` .  El delegado haga otro método de llamar a esta función, como muestra enviando la cadena “single” el objeto delegado.  Se vincula juntos y después ejecuta el Siguiente, instancias adicionales de `MyCallback` por una llamada al objeto delegado.  
  
```  
// use_delegate.cpp  
// compile with: /clr  
using namespace System;  
  
ref class SomeClass  
{  
public:  
   static void Func(String^ str)  
   {  
      Console::WriteLine("static SomeClass::Func - {0}", str);  
   }  
};  
  
ref class OtherClass  
{  
public:  
   OtherClass( Int32 n )   
   {  
      num = n;  
   }  
  
   void Method(String^ str)   
   {  
      Console::WriteLine("OtherClass::Method - {0}, num = {1}",   
         str, num);  
   }  
  
   Int32 num;  
};  
  
delegate void MyCallback(String^ str);  
  
int main( )   
{  
   MyCallback^ callback = gcnew MyCallback(SomeClass::Func);     
   callback("single");   
  
   callback += gcnew MyCallback(SomeClass::Func);     
  
   OtherClass^ f = gcnew OtherClass(99);  
   callback += gcnew MyCallback(f, &OtherClass::Method);  
  
   f = gcnew OtherClass(100);  
   callback += gcnew MyCallback(f, &OtherClass::Method);  
  
   callback("chained");  
  
   return 0;  
}  
```  
  
 **Resultados**  
  
  **SomeClass::Func estático \- single**  
**SomeClass::Func estático \- encadenado**  
**SomeClass::Func estático \- encadenado**  
**OtherClass::Method \- encadenado, \= 99 numéricos**  
**OtherClass::Method \- encadenado, \= 100 numéricos** El ejemplo de código siguiente se muestra cómo asociar un delegado con un miembro de una clase de valor.  
  
```  
// mcppv2_del_mem_value_class.cpp  
// compile with: /clr  
using namespace System;  
public delegate void MyDel();  
  
value class A {  
public:  
   void func1() {  
      Console::WriteLine("test");  
   }  
};  
  
int main() {  
   A a;  
   A^ ah = a;  
   MyDel^ f = gcnew MyDel(a, &A::func1);   // implicit box of a  
   f();  
   MyDel^ f2 = gcnew MyDel(ah, &A::func1);  
   f2();  
}  
```  
  
 **Resultados**  
  
  **prueba**  
**prueba**   
## Cómo crear delegados  
 Puede utilizar el operador de “`-`” para quitar un delegado componente de un delegado compuesto.  
  
```  
// mcppv2_compose_delegates.cpp  
// compile with: /clr  
using namespace System;  
  
delegate void MyDelegate(String ^ s);  
  
ref class MyClass {  
public:  
   static void Hello(String ^ s) {  
      Console::WriteLine("Hello, {0}!", s);  
   }  
  
   static void Goodbye(String ^ s) {  
      Console::WriteLine("  Goodbye, {0}!", s);  
   }  
};  
  
int main() {  
  
   MyDelegate ^ a = gcnew MyDelegate(MyClass::Hello);  
   MyDelegate ^ b = gcnew MyDelegate(MyClass::Goodbye);  
   MyDelegate ^ c = a + b;  
   MyDelegate ^ d = c - a;  
  
   Console::WriteLine("Invoking delegate a:");  
   a("A");  
   Console::WriteLine("Invoking delegate b:");  
   b("B");  
   Console::WriteLine("Invoking delegate c:");  
   c("C");  
   Console::WriteLine("Invoking delegate d:");  
   d("D");  
}  
```  
  
 **Resultados**  
  
  **Invocar el delegado a:**  
**¡Hola, A\!**  
**Invocar b delegado:**  
 **¡Adiós, b\!**  
**Invocar c delegado:**  
**¡Hola, C\!**  
 **¡Adiós, C\!**  
**Invocar d delegado:**  
 **¡Adiós, d\!**   
## Pase un delegate^ a una función nativa que espera recibir un puntero a función  
 De un componente administrado puede llamar a una función nativa con parámetros de puntero a función donde la función nativa a continuación puede llamar a la función miembro de delegado del componente administrado.  
  
 Este ejemplo crea el archivo .dll que exporta la función nativa:  
  
```  
// delegate_to_native_function.cpp  
// compile with: /LD  
#include < windows.h >  
extern "C" {  
   __declspec(dllexport)  
   void nativeFunction(void (CALLBACK *mgdFunc)(const char* str)) {  
      mgdFunc("Call to Managed Function");  
   }  
}  
```  
  
 El ejemplo siguiente utiliza el archivo .dll y pasa un identificador delegado a la función nativa que espera un puntero a función.  
  
```  
// delegate_to_native_function_2.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
delegate void Del(String ^s);  
public ref class A {  
public:  
   void delMember(String ^s) {  
      Console::WriteLine(s);  
   }  
};  
  
[DllImportAttribute("delegate_to_native_function", CharSet=CharSet::Ansi)]  
extern "C" void nativeFunction(Del ^d);  
  
int main() {  
   A ^a = gcnew A;  
   Del ^d = gcnew Del(a, &A::delMember);  
   nativeFunction(d);   // Call to native function  
}  
```  
  
 **Resultados**  
  
  **Llamada a la función administrada**   
## Para asociar delegados con funciones no administradas  
 Para asociar un delegado a una función nativa, debe ajustar la función nativa en un tipo administrado y declarar la función que se invoque con `PInvoke`.  
  
```  
// mcppv2_del_to_umnangd_func.cpp  
// compile with: /clr  
#pragma unmanaged  
extern "C" void printf(const char*, ...);  
class A {  
public:  
   static void func(char* s) {  
      printf(s);  
   }  
};  
  
#pragma managed  
public delegate void func(char*);   
  
ref class B {  
   A* ap;  
  
public:  
   B(A* ap):ap(ap) {}  
   void func(char* s) {  
      ap->func(s);   
   }  
};  
  
int main() {  
   A* a = new A;  
   B^ b = gcnew B(a);  
   func^ f = gcnew func(b, &B::func);  
   f("hello");  
   delete a;  
}  
```  
  
 **Resultados**  
  
  **hello**   
## Para utilizar delegados independientes  
 Puede utilizar un delegado independiente para pasar una instancia del tipo cuya función desea llamar cuando se llama al delegado.  
  
 Los delegados independientes son especialmente útiles si desea recorrer en iteración los objetos en un colección\- por utilizar [for each, in](../dotnet/for-each-in.md) palabra clave\- y llamar a una función miembro en cada instancia.  
  
 Aquí es cómo declarar, crear instancias, y llamar el límite y delegados independientes:  
  
|Acción|Delegados de límite|Delegados independientes|  
|------------|-------------------------|------------------------------|  
|Declare|La firma del delegado debe coincidir con la de la función que desea llamar a través del delegado.|El primer parámetro de la firma del delegado es el tipo de `this` para el objeto que desea llamar.<br /><br /> Después del primer parámetro, la firma del delegado debe coincidir con la de la función que desea llamar a través del delegado.|  
|Instantiate|Al crear instancias de un delegado enlazado, puede especificar una función de instancia, o una función global o estática del miembro.<br /><br /> Para especificar una función de instancia, el primer parámetro es una instancia del tipo cuyo miembro la función que desea llamar y el segundo parámetro es la dirección de la función que desea llamar.<br /><br /> Si desea llamar una función global o miembro static, simplemente pase el nombre de una función global o de la función miembro estática.|Al crear instancias de un delegado independiente, simplemente pase la dirección de la función que desea llamar.|  
|Call|Cuando se llama a un delegado enlazado, simplemente pase los parámetros requeridos por la firma de delegado.|Igual que un delegado enlazado, pero recuerdan que el primer parámetro debe ser una instancia del objeto que contiene la función que desea llamar.|  
  
 Este ejemplo muestra cómo declarar, crear instancias, y llamar a delegados independientes:  
  
```  
// unbound_delegates.cpp  
// compile with: /clr  
ref struct A {  
   A(){}  
   A(int i) : m_i(i) {}  
   void Print(int i) { System::Console::WriteLine(m_i + i);}  
  
private:  
   int m_i;  
};  
  
value struct V {  
   void Print() { System::Console::WriteLine(m_i);}  
   int m_i;  
};  
  
delegate void Delegate1(A^, int i);  
delegate void Delegate2(A%, int i);  
  
delegate void Delegate3(interior_ptr<V>);  
delegate void Delegate4(V%);  
  
delegate void Delegate5(int i);  
delegate void Delegate6();  
  
int main() {  
   A^ a1 = gcnew A(1);  
   A% a2 = *gcnew A(2);  
  
   Delegate1 ^ Unbound_Delegate1 = gcnew Delegate1(&A::Print);  
   // delegate takes a handle  
   Unbound_Delegate1(a1, 1);  
   Unbound_Delegate1(%a2, 1);  
  
   Delegate2 ^ Unbound_Delegate2 = gcnew Delegate2(&A::Print);  
   // delegate takes a tracking reference (must deference the handle)  
   Unbound_Delegate2(*a1, 1);  
   Unbound_Delegate2(a2, 1);  
  
   // instantiate a bound delegate to an instance member function  
   Delegate5 ^ Bound_Del = gcnew Delegate5(a1, &A::Print);  
   Bound_Del(1);  
  
   // instantiate value types  
   V v1 = {7};  
   V v2 = {8};  
  
   Delegate3 ^ Unbound_Delegate3 = gcnew Delegate3(&V::Print);  
   Unbound_Delegate3(&v1);  
   Unbound_Delegate3(&v2);  
  
   Delegate4 ^ Unbound_Delegate4 = gcnew Delegate4(&V::Print);  
   Unbound_Delegate4(v1);  
   Unbound_Delegate4(v2);  
  
   Delegate6 ^ Bound_Delegate3 = gcnew Delegate6(v1, &V::Print);  
   Bound_Delegate3();  
}  
```  
  
 **Resultados**  
  
  **2**  
**3**  
**2**  
**3**  
**2**  
**7**  
**8**  
**7**  
**8**  
**7** El ejemplo siguiente se muestra cómo utilizar delegados independientes y las palabras clave de [for each, in](../dotnet/for-each-in.md) para recorrer de objetos en una colección y llamar a una función miembro en cada instancia.  
  
```  
// unbound_delegates_2.cpp  
// compile with: /clr  
using namespace System;  
  
ref class RefClass {  
   String^ _Str;  
  
public:  
   RefClass( String^ str ) : _Str( str ) {}  
   void Print() { Console::Write( _Str ); }  
};  
  
delegate void PrintDelegate( RefClass^ );  
  
int main() {  
   PrintDelegate^ d = gcnew PrintDelegate( &RefClass::Print );  
  
   array< RefClass^ >^ a = gcnew array<RefClass^>( 10 );  
  
   for ( int i = 0; i < a->Length; ++i )  
      a[i] = gcnew RefClass( i.ToString() );  
  
   for each ( RefClass^ R in a )  
      d( R );  
  
   Console::WriteLine();  
}  
```  
  
 Este ejemplo crea un delegado sin enlazar a las funciones del descriptor de acceso de una propiedad:  
  
```  
// unbound_delegates_3.cpp  
// compile with: /clr  
ref struct B {  
   property int P1 {  
      int get() { return m_i; }  
      void set(int i) { m_i = i; }  
   }  
  
private:  
   int m_i;  
};  
  
delegate void DelBSet(B^, int);  
delegate int DelBGet(B^);  
  
int main() {  
   B^ b = gcnew B;  
  
   DelBSet^ delBSet = gcnew DelBSet(&B::P1::set);  
   delBSet(b, 11);  
  
   DelBGet^ delBGet = gcnew DelBGet(&B::P1::get);     
   System::Console::WriteLine(delBGet(b));  
}  
```  
  
 **Resultados**  
  
  **11** El ejemplo siguiente se muestra cómo invocar un delegado de multidifusión, donde se ha enlazado una instancia y una instancia está sin enlazar.  
  
```  
// unbound_delegates_4.cpp  
// compile with: /clr  
ref class R {  
public:  
   R(int i) : m_i(i) {}  
  
   void f(R ^ r) {  
      System::Console::WriteLine("in f(R ^ r)");  
   }  
  
   void f() {  
      System::Console::WriteLine("in f()");  
   }  
  
private:  
   int m_i;  
};  
  
delegate void Del(R ^);  
  
int main() {  
   R ^r1 = gcnew R(11);  
   R ^r2 = gcnew R(12);  
  
   Del^ d = gcnew Del(r1, &R::f);  
   d += gcnew Del(&R::f);  
   d(r2);  
};  
```  
  
 **Resultados**  
  
  **en f \(^ de r r\)**  
**en f\(\)** El ejemplo siguiente muestra cómo crear y llamar a un delegado genérico independiente.  
  
```  
// unbound_delegates_5.cpp  
// compile with: /clr  
ref struct R {  
   R(int i) : m_i(i) {}  
  
   int f(R ^) { return 999; }  
   int f() { return m_i + 5; }  
  
   int m_i;  
};  
  
value struct V {  
   int f(V%) { return 999; }  
   int f() { return m_i + 5; }   
  
   int m_i;  
};  
  
generic <typename T>  
delegate int Del(T t);  
  
generic <typename T>  
delegate int DelV(T% t);  
  
int main() {     
   R^ hr = gcnew R(7);  
   System::Console::WriteLine((gcnew Del<R^>(&R::f))(hr));  
  
   V v;  
   v.m_i = 9;  
   System::Console::WriteLine((gcnew DelV<V >(&V::f))(v) );  
}  
```  
  
 **Resultados**  
  
  **12**  
**14**   
## Vea también  
 [delegado](../windows/delegate-cpp-component-extensions.md)