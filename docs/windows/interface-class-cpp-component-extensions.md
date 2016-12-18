---
title: "interface class (Extensiones de componentes de C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "interface_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interface y class (palabras clave)"
  - "interface y struct (palabras clave)"
ms.assetid: 3ccea701-f50b-4da7-ad6b-f0ee1203e2b9
caps.latest.revision: 30
caps.handback.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# interface class (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Declara una interfaz.  Para obtener información sobre interfaces nativas, vea [\_\_interfaz](../cpp/interface.md).  
  
## Todos los runtimes  
 **Sintaxis**  
  
```  
  
        interface_access interface class  name :  inherit_access base_interface {};  
interface_access interface struct name :  inherit_access base_interface {};  
```  
  
 **Parámetros**  
  
 *interface\_access*  
 La accesibilidad de una interfaz fuera del ensamblado.  Los valores posibles son **public** y `private`.  `private` es el valor predeterminado.  Las interfaces anidados no pueden tener un especificador de *interface\_access* .  
  
 *name*  
 Nombre de la interfaz.  
  
 *inherit\_access*  
 Accesibilidad de *base\_interface*.  La única accesibilidad permitida para una interfaz base es `public` \(valor predeterminado\).  
  
 *base\_interface* \(opcional\)  
 Una interfaz base para la interfaz *name*.  
  
 **Comentarios**  
  
 **interface struct** es equivalente a **interface class**.  
  
 Una interfaz puede contener las declaraciones de las funciones, los eventos, y las propiedades.  Todos los miembros de la interfaz tienen accesibilidad pública.  Una interfaz también puede contener miembros de datos, las funciones, los eventos, las propiedades y estáticos, y estos miembros estáticos se deben definir en la interfaz.  
  
 Una interfaz define cómo una clase puede implementar.  Una interfaz no es una clase y las clases pueden implementar solamente interfaces.  Cuando una clase define una función declarada en una interfaz, se implementa, no se reemplaza la función.  Por consiguiente, la búsqueda de nombre no incluye miembros de interfaz.  
  
 Una clase o struct que derive de una interfaz debe implementar todos los miembros de la interfaz.  Al implementar *nombre* de la interfaz también debe implementar las interfaces en la lista de `base_interface` .  
  
 Para obtener más información, vea:  
  
-   [Constructor estático de la interfaz](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)  
  
-   [Interfaces genéricas \(Visual C\+\+\)](../Topic/Generic%20Interfaces%20\(Visual%20C++\).md)  
  
 Para obtener información sobre otros tipos CLR, vea [Clases y Structs](../windows/classes-and-structs-cpp-component-extensions.md).  
  
 Puede detectar en tiempo de compilación si un tipo es una interfaz con `__is_interface_class(``type``)`.  Para obtener más información, vea [Compatibilidad de compilador para type traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 En el entorno de desarrollo, puede obtener Ayuda de F1 para estas palabras clave resaltando la palabra clave, \(`interface class`, por ejemplo\) y presionando F1.  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 **Comentarios**  
  
 \(No hay notas para esta característica de lenguaje que solo se apliquen a Windows en tiempo de ejecución\).  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **Comentarios**  
  
 \(No hay notas para esta característica de lenguaje que solo se apliquen a Common Language Runtime\).  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
### Ejemplos  
 **Ejemplo**  
  
 El ejemplo de código siguiente muestra cómo una interfaz puede definir el comportamiento de una función de reloj.  
  
```  
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
  
 **Resultados**  
  
  **en Function\_3**  
 **en Función\_2**  
 **en Función\_1**  
 **8**  
 **OnClick: 7, 3,14159**  
 **en Función\_1** **Ejemplo**  
  
 El ejemplo de código siguiente muestra dos maneras de implementar funciones con la misma firma declarada en varias interfaces y donde esas interfaces son utilizadas por una clase.  
  
```  
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
  
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)