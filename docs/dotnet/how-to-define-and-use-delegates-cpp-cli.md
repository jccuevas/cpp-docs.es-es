---
title: Procedimiento Definir y utilizar delegados (C++ / c++ / CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- delegates
ms.assetid: 1cdf3420-89c1-47c0-b796-aa984020e0f8
ms.openlocfilehash: bcbf5bf978da5b6c13dd131e7a19975381bd97a5
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58771316"
---
# <a name="how-to-define-and-use-delegates-ccli"></a>Procedimiento Definir y utilizar delegados (C++ / c++ / CLI)

Este artículo muestra cómo definir y consumir delegados en C / c++ / CLI.

Aunque .NET Framework proporciona un número de delegados, en ocasiones, es posible que deba definir a nuevos delegados.

El ejemplo de código siguiente define un delegado que se denomina `MyCallback`. El código de control de eventos, la función que se llama cuando se desencadena este delegado nuevo, debe tener un tipo de valor devuelto de `void` y tomar un <xref:System.String> referencia.

La función principal usa un método estático que se define mediante `SomeClass` para crear instancias de la `MyCallback` delegar. El delegado, a continuación, se convierte en un método alternativo para llamar a esta función, como se muestra mediante el envío de la cadena "única" para el objeto de delegado. A continuación, más instancias de `MyCallback` están vinculados entre sí y, a continuación, se ejecuta mediante una llamada al objeto de delegado.

```cpp
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

```Output
static SomeClass::Func - single
static SomeClass::Func - chained
static SomeClass::Func - chained
OtherClass::Method - chained, num = 99
OtherClass::Method - chained, num = 100
```

El ejemplo de código siguiente muestra cómo asociar a un delegado a un miembro de una clase de valor.

```cpp
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

```Output
test
test
```

## <a name="how-to-compose-delegates"></a>Cómo crear delegados

Puede usar el "`-`" operador para quitar un delegado de componente de un delegado compuesto.

```cpp
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

**Salida**

```Output
Invoking delegate a:
Hello, A!
Invoking delegate b:
  Goodbye, B!
Invoking delegate c:
Hello, C!
  Goodbye, C!
Invoking delegate d:
  Goodbye, D!
```

## <a name="pass-a-delegate-to-a-native-function-that-expects-a-function-pointer"></a>Pasar un delegado ^ a una función nativa que espera un puntero de función

Desde un componente administrado puede llamar a una función nativa con la función de los parámetros de puntero donde la función nativa, a continuación, puede llamar a la función miembro de delegado del componente administrado.

Este ejemplo crea el archivo .dll que exporta la función nativa:

```cpp
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

El ejemplo siguiente utiliza el archivo .dll y pasa un delegado de controlador a la función nativa que espera un puntero de función.

```cpp
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

**Salida**

```Output
Call to Managed Function
```

## <a name="to-associate-delegates-with-unmanaged-functions"></a>Para asociar delegados a funciones no administradas

Para asociar un delegado a una función nativa, debe ajustar la función nativa en un tipo administrado y declarar la función que se invocará a través de `PInvoke`.

```cpp
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

**Salida**

```Output
hello
```

## <a name="to-use-unbound-delegates"></a>Utilizar delegados sin enlazar

Puede usar a un delegado sin enlazar para pasar una instancia del tipo cuya función que desea llamar cuando se llama al delegado.

Delegados sin enlazar son especialmente útiles si desea recorrer en iteración los objetos de una colección, utilizando [para cada uno, en](../dotnet/for-each-in.md) palabras clave y llamar a una función miembro en cada instancia.

Aquí le mostramos cómo declarar, crear instancias y llamada dependientes e independientes de los delegados:

|Acción|Enlazar delegados|Delegados sin enlazar|
|------------|---------------------|-----------------------|
|Declarar|La firma del delegado debe coincidir con la firma de la función que desea llamar a través del delegado.|El primer parámetro de la firma del delegado es el tipo de `this` para el objeto que desea llamar.<br /><br /> Después del primer parámetro, la firma del delegado debe coincidir con la firma de la función que desea llamar a través del delegado.|
|Crear una instancia de|Cuando crea una instancia de un delegado enlazado, puede especificar una función de instancia o una función miembro estática o global.<br /><br /> Para especificar una función de instancia, el primer parámetro es una instancia del tipo cuya función miembro que desea llamar y el segundo parámetro es la dirección de la función que desea llamar.<br /><br /> Si desea llamar a una función miembro estática o global, simplemente pase el nombre de una función global o el nombre de la función miembro estática.|Cuando crea una instancia de un delegado sin enlazar, simplemente pase la dirección de la función que desea llamar.|
|Llamar a|Cuando se llama a un delegado enlazado, simplemente pase los parámetros requeridos por la firma del delegado.|Igual que un límite delegar, pero recuerde que el primer parámetro debe ser una instancia del objeto que contiene la función que desea llamar.|

Este ejemplo muestra cómo declarar, crear instancias y llamar a delegados sin enlazar:

```cpp
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

**Salida**

```Output
2
3
2
3
2
7
8
7
8
7
```

El ejemplo siguiente muestra cómo usar delegados sin enlazar y [para cada uno, en](../dotnet/for-each-in.md) palabras clave para recorrer en iteración los objetos de una colección y llamar a una función miembro en cada instancia.

```cpp
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

Este ejemplo crea a un delegado sin enlazar a las funciones de descriptor de acceso de una propiedad:

```cpp
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

**Salida**

```Output
11
```

El ejemplo siguiente muestra cómo invocar a un delegado de multidifusión, donde se enlaza a una instancia y una instancia es independiente.

```cpp
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

**Salida**

```Output
in f(R ^ r)
in f()
```

El ejemplo siguiente muestra cómo crear y llamar a un delegado genérico sin enlazar.

```cpp
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

**Salida**

```Output
12
14
```

## <a name="see-also"></a>Vea también

[delegate (Extensiones de componentes de C++)](../extensions/delegate-cpp-component-extensions.md)
