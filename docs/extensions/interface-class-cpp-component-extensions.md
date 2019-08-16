---
title: Clase interface  (C++/CLI y C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- interface_CPP
helpviewer_keywords:
- interface class keyword
- interface struct keyword
ms.assetid: 3ccea701-f50b-4da7-ad6b-f0ee1203e2b9
ms.openlocfilehash: 60e8965e3ef2538554d8c664b35bd0849bd5e69e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515710"
---
# <a name="interface-class--ccli-and-ccx"></a>Clase interface  (C++/CLI y C++/CX)

Declara una interfaz.  Para información sobre las interfaces nativas, consulte [__interface](../cpp/interface.md).

## <a name="all-runtimes"></a>Todos los runtimes

### <a name="syntax"></a>Sintaxis

```cpp
interface_access
interface class
name :  inherit_accessbase_interface{};interface_accessinterface structname :  inherit_accessbase_interface{};
```

### <a name="parameters"></a>Parámetros

*interface_access*<br/>
La accesibilidad de una interfaz fuera del ensamblado.  Los valores posibles son **public** y **private**.  **private** es el valor predeterminado. Las interfaces anidadas no pueden tener un especificador *interface_access*.

*name*<br/>
Nombre de la interfaz.

*inherit_access*<br/>
La accesibilidad de *base_interface*.  La única accesibilidad permitida para una interfaz base es **public** (la predeterminada).

*base_interface*<br/>
(Opcional) Una interfaz base para la interfaz *name*.

### <a name="remarks"></a>Comentarios

**interface struct** es equivalente a **interface class**.

Una interfaz puede contener declaraciones de funciones, propiedades y eventos.  Todos los miembros de interfaz tienen accesibilidad pública. Una interfaz puede contener también miembros de datos estáticos, funciones y propiedades y estos miembros estáticos deben definirse en la interfaz.

Una interfaz define cómo se puede implementar una clase. Una interfaz no es una clase y las clases solo pueden implementar interfaces. Cuando una clase define una función declarada en una interfaz, la función se implementa, no se invalida. Por lo tanto, la búsqueda de nombres no incluye los miembros de interfaz.

Una clase o un struct que se deriven de una interfaz deben implementar todos los miembros de la interfaz. Al implementar la interfaz *name*, también debe implementar las interfaces de la lista `base_interface`.

Para obtener más información, consulte:

- [Constructor estático de interfaz](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)

- [Interfaces genéricas (C++/CLI)](generic-interfaces-visual-cpp.md)

Para información sobre otros tipos CLR, consulte [Clases y structs](classes-and-structs-cpp-component-extensions.md).

Puede detectar en tiempo de compilación si un tipo es una interfaz con `__is_interface_class(type)`. Para más información, consulte [Compatibilidad del compilador con rasgos de tipo](compiler-support-for-type-traits-cpp-component-extensions.md).

En el entorno de desarrollo, puede obtener ayuda (F1) sobre estas palabras clave si resalta la palabra clave, (`interface class`, por ejemplo) y presiona F1.

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

### <a name="remarks"></a>Comentarios

(No hay notas para esta característica de lenguaje que solo se apliquen a Windows Runtime).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Comentarios

(No hay notas para esta característica de lenguaje que solo se apliquen a Common Language Runtime).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

En el ejemplo de código siguiente se muestra cómo una interfaz puede definir el comportamiento de una función de reloj.

```cpp
// mcppv2_interface_class.cpp
// compile with: /clr
using namespace System;

public delegate void ClickEventHandler(int, double);

// define interface with nested interface
public interface class Interface_A {
   void Function_1();

   interface class Interface_Nested_A {
      void Function_2();
   };
};

// interface with a base interface
public interface class Interface_B : Interface_A {
   property int Property_Block;
   event ClickEventHandler^ OnClick;
   static void Function_3() { Console::WriteLine("in Function_3"); }
};

// implement nested interface
public ref class MyClass : public Interface_A::Interface_Nested_A {
public:
   virtual void Function_2() { Console::WriteLine("in Function_2"); }
};

// implement interface and base interface
public ref class MyClass2 : public Interface_B {
private:
   int MyInt;

public:
   // implement non-static function
   virtual void Function_1() { Console::WriteLine("in Function_1"); }

   // implement property
   property int Property_Block {
      virtual int get() { return MyInt; }
      virtual void set(int value) { MyInt = value; }
   }
   // implement event
   virtual event ClickEventHandler^ OnClick;

   void FireEvents() {
      OnClick(7, 3.14159);
   }
};

// class that defines method called when event occurs
ref class EventReceiver {
public:
   void OnMyClick(int i, double d) {
      Console::WriteLine("OnClick: {0}, {1}", i, d);
   }
};

int main() {
   // call static function in an interface
   Interface_B::Function_3();

   // instantiate class that implements nested interface
   MyClass ^ x = gcnew MyClass;
   x->Function_2();

   // instantiate class that implements interface with base interface
   MyClass2 ^ y = gcnew MyClass2;
   y->Function_1();
   y->Property_Block = 8;
   Console::WriteLine(y->Property_Block);

   EventReceiver^ MyEventReceiver = gcnew EventReceiver();

   // hook handler to event
   y->OnClick += gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);

   // invoke events
   y->FireEvents();

   // unhook handler to event
   y->OnClick -= gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);

   // call implemented function via interface handle
   Interface_A^ hi = gcnew MyClass2();
   hi->Function_1();
}
```

```Output
in Function_3

in Function_2

in Function_1

8

OnClick: 7, 3.14159

in Function_1
```

En el ejemplo de código siguiente se muestran dos maneras de implementar funciones con la misma signatura declarada en varias interfaces y dónde la clase usa esas interfaces.

```cpp
// mcppv2_interface_class_2.cpp
// compile with: /clr /c
interface class I {
   void Test();
   void Test2();
};

interface class J : I {
   void Test();
   void Test2();
};

ref struct R : I, J {
   // satisfies the requirement to implement Test in both interfaces
   virtual void Test() {}

   // implement both interface functions with explicit overrides
   virtual void A() = I::Test2 {}
   virtual void B() = J::Test2 {}
};
```

## <a name="see-also"></a>Vea también

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)