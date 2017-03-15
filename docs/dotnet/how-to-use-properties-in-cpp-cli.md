---
title: "C&#243;mo: Usar propiedades en C++/CLI | Microsoft Docs"
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
  - "propiedades [C++], simples"
  - "propiedades simples"
ms.assetid: f5d82547-e214-4f05-9e1b-ddb6d0dc5e4c
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Usar propiedades en C++/CLI
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se muestra cómo utilizar propiedades en C\+\+\/CLI.  
  
## Propiedades básicas  
 Para propiedad\- esos básicos que simplemente asignación y recupera información privada que miembro\- no tiene que definir explícitamente el obtener y el descriptor de acceso conjunto funciona porque el compilador automáticamente la proporciona cuando se especifica solo el tipo de datos de la propiedad.  Este código muestra una propiedad básica:  
  
```  
// SimpleProperties.cpp  
// compile with: /clr  
using namespace System;  
  
ref class C {  
public:  
   property int Size;  
};  
  
int main() {  
   C^ c = gcnew C;  
   c->Size = 111;  
   Console::WriteLine("c->Size = {0}", c->Size);  
}  
```  
  
 **Resultados**  
  
  **C tamaño\>\= 111**   
## Propiedades estáticas  
 Este ejemplo de código se muestra cómo declarar y utilizar una propiedad estática.  Una propiedad estática puede tener acceso a los miembros estáticos de la clase.  
  
```  
// mcppv2_property_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref class StaticProperties {  
   static int MyInt;  
   static int MyInt2;  
  
public:  
   static property int Static_Data_Member_Property;  
  
   static property int Static_Block_Property {  
      int get() {  
         return MyInt;  
      }  
  
      void set(int value) {  
         MyInt = value;  
      }        
   }  
};  
  
int main() {  
   StaticProperties::Static_Data_Member_Property = 96;  
   Console::WriteLine(StaticProperties::Static_Data_Member_Property);  
  
   StaticProperties::Static_Block_Property = 47;  
   Console::WriteLine(StaticProperties::Static_Block_Property);  
}  
```  
  
 **Resultados**  
  
  **96**  
**47**   
## Propiedades indizadas  
 Una propiedad indizada expone normalmente una estructura de datos que se usa un operador suscrito.  
  
 Si utiliza una propiedad indizada predeterminada, puede tener acceso a la estructura de datos simplemente haciendo referencia al nombre de clase, pero si utiliza una propiedad indizada definido por el usuario, debe especificar el nombre de propiedad para tener acceso a la estructura de datos.  
  
 Para obtener información sobre cómo tener acceso a un indizador predeterminado utilizando el puntero de `this` , vea [Semántica del puntero this en los tipos de valor y de referencia](../misc/semantics-of-the-this-pointer-in-value-and-reference-types.md).  
  
 Para obtener información sobre cómo consumir un indizador escrita en C\#, vea [Cómo: Consumir un indizador de C\#](../dotnet/how-to-consume-a-csharp-indexer-cpp-cli.md).  
  
 Este ejemplo de código se muestra cómo utilizar propiedades indizadas predeterminadas y definido por el usuario:  
  
```  
// mcppv2_property_2.cpp  
// compile with: /clr  
using namespace System;  
public ref class C {  
   array<int>^ MyArr;  
  
public:  
   C() {  
      MyArr = gcnew array<int>(5);  
   }  
  
   // default indexer  
   property int default[int] {  
      int get(int index) {  
         return MyArr[index];  
      }  
      void set(int index, int value) {  
         MyArr[index] = value;  
      }  
   }  
  
   // user-defined indexer  
   property int indexer1[int] {  
      int get(int index) {  
         return MyArr[index];  
      }  
      void set(int index, int value) {  
         MyArr[index] = value;  
      }  
   }  
};  
  
int main() {  
   C ^ MyC = gcnew C();  
  
   // use the default indexer  
   Console::Write("[ ");  
   for (int i = 0 ; i < 5 ; i++) {  
      MyC[i] = i;  
      Console::Write("{0} ", MyC[i]);  
   }  
  
   Console::WriteLine("]");  
  
   // use the user-defined indexer  
   Console::Write("[ ");  
   for (int i = 0 ; i < 5 ; i++) {  
      MyC->indexer1[i] = i * 2;  
      Console::Write("{0} ", MyC->indexer1[i]);  
   }  
  
   Console::WriteLine("]");  
}  
```  
  
 **Resultados**  
  
  **\[ 0 1 2 3 4 \]**  
**\[ 0 2 4 6 8 \]** El ejemplo siguiente se muestra cómo llamar al indizador predeterminado utilizando el puntero de `this` .  
  
```  
// call_default_indexer_through_this_pointer.cpp  
// compile with: /clr /c  
value class Position {  
public:  
   Position(int x, int y) : position(gcnew array<int, 2>(100, 100)) {  
      this->default[x, y] = 1;  
   }  
  
   property int default[int, int] {  
      int get(int x, int y) {  
         return position[x, y];  
      }  
  
      void set(int x, int y, int value) {}  
   }  
  
private:  
   array<int, 2> ^ position;  
};  
```  
  
 Este ejemplo muestra cómo utilizar <xref:System.Reflection.DefaultMemberAttribute> para especificar el indizador predeterminado:  
  
```  
// specify_default_indexer.cpp  
// compile with: /LD /clr  
using namespace System;  
[Reflection::DefaultMember("XXX")]  
public ref struct Squares {  
   property Double XXX[Double] {  
      Double get(Double data) {  
         return data*data;  
      }  
   }  
};  
```  
  
 El ejemplo siguiente utiliza los metadatos que se crea en el ejemplo anterior.  
  
```  
// consume_default_indexer.cpp  
// compile with: /clr  
#using "specify_default_indexer.dll"  
int main() {  
   Squares ^ square = gcnew Squares();  
   System::Console::WriteLine("{0}", square[3]);  
}  
```  
  
 **Resultados**  
  
 **9**   
## Propiedades virtuales  
 Este ejemplo de código se muestra cómo declarar y utilizar propiedades virtuales:  
  
```  
// mcppv2_property_4.cpp  
// compile with: /clr  
using namespace System;  
interface struct IEFace {  
public:  
   property int VirtualProperty1;  
   property int VirtualProperty2 {  
      int get();  
      void set(int i);  
   }  
};  
  
// implement virtual events  
ref class PropImpl : public IEFace {  
   int MyInt;  
public:  
   virtual property int VirtualProperty1;  
  
   virtual property int VirtualProperty2 {  
      int get() {  
         return MyInt;  
      }  
      void set(int i) {  
         MyInt = i;  
      }  
   }  
};  
  
int main() {  
   PropImpl ^ MyPI = gcnew PropImpl();  
   MyPI->VirtualProperty1 = 93;  
   Console::WriteLine(MyPI->VirtualProperty1);  
  
   MyPI->VirtualProperty2 = 43;  
   Console::WriteLine(MyPI->VirtualProperty2);  
}  
```  
  
 **Resultados**  
  
  **93**  
**43**   
## Propiedades abstractas y selladas  
 Aunque se especifican las palabras clave de [abstractas](../windows/abstract-cpp-component-extensions.md) y de [sellado](../windows/sealed-cpp-component-extensions.md) como válido en la especificación de ECMA C\+\+\/CLI, para el compilador de Visual C\+\+, no puede especificarlos en propiedades triviales, ni en la declaración de propiedad de una propiedad no trivial.  
  
 Para declarar una propiedad sealed o abstracta, debe definir una propiedad no trivial y especificar la palabra clave de `abstract` o de `sealed` en el descriptor de acceso get y set funciona.  
  
```  
// properties_abstract_sealed.cpp  
// compile with: /clr  
ref struct A {  
protected:  
   int m_i;  
  
public:  
   A() { m_i = 87; }  
  
   // define abstract property  
   property int Prop_1 {  
      virtual int get() abstract;  
      virtual void set(int i) abstract;  
   }  
};  
  
ref struct B : A {  
private:  
   int m_i;  
  
public:  
   B() { m_i = 86; }  
  
   // implement abstract property  
   property int Prop_1 {  
      virtual int get() override { return m_i; }  
      virtual void set(int i) override { m_i = i; }  
   }  
};  
  
ref struct C {  
private:  
   int m_i;  
  
public:  
   C() { m_i = 87; }  
  
   // define sealed property  
   property int Prop_2 {  
      virtual int get() sealed { return m_i; }  
      virtual void set(int i) sealed { m_i = i; };  
   }  
};  
  
int main() {  
   B b1;  
   // call implementation of abstract property  
   System::Console::WriteLine(b1.Prop_1);  
  
   C c1;  
   // call sealed property  
   System::Console::WriteLine(c1.Prop_2);  
}  
```  
  
 **Resultados**  
  
  **86**  
**87**   
## Propiedades multidimensionales  
 Puede utilizar las propiedades multidimensionales para definir los métodos de descriptor de acceso de la propiedad que toman un número no estándar de parámetros.  
  
```  
// mcppv2_property_5.cpp  
// compile with: /clr  
ref class X {  
   double d;  
public:  
   X() : d(0) {}  
   property double MultiDimProp[int, int, int] {  
      double get(int, int, int) {  
         return d;  
      }  
      void set(int i, int j, int k, double l) {  
         // do something with those ints  
         d = l;  
      }  
   }  
  
   property double MultiDimProp2[int] {  
      double get(int) {  
         return d;  
      }  
      void set(int i, double l) {  
         // do something with those ints  
         d = l;  
      }  
   }  
  
};  
  
int main() {  
   X ^ MyX = gcnew X();  
   MyX->MultiDimProp[0,0,0] = 1.1;  
   System::Console::WriteLine(MyX->MultiDimProp[0, 0, 0]);  
}  
```  
  
 **Resultados**  
  
  **1.1**   
## Sobrecargar descriptores de acceso de propiedad  
 El ejemplo siguiente se muestra cómo sobrecargar propiedades indizadas.  
  
```  
// mcppv2_property_6.cpp  
// compile with: /clr  
ref class X {  
   double d;  
public:  
   X() : d(0.0) {}  
   property double MyProp[int] {  
      double get(int i) {  
         return d;  
      }  
  
      double get(System::String ^ i) {  
         return 2*d;  
      }  
  
      void set(int i, double l) {  
         d = i * l;  
      }  
   }   // end MyProp definition  
};  
  
int main() {  
   X ^ MyX = gcnew X();  
   MyX->MyProp[2] = 1.7;  
   System::Console::WriteLine(MyX->MyProp[1]);  
   System::Console::WriteLine(MyX->MyProp["test"]);  
}  
```  
  
 **Resultados**  
  
  **3.4**  
**6.8**   
## Vea también  
 [propiedad](../windows/property-cpp-component-extensions.md)