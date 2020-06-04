---
title: Clases genéricas (C++/CLI)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- classes [C++], generic
- generic classes [C++], about generic classes
- data types [C++], generic
- generic classes
- generics [C++], declaring generic classes
ms.assetid: 0beb99e1-1ec4-4fee-9836-ce9657d67a3a
ms.openlocfilehash: 78f4bf3abb98aab5e626e8ada538a22bdbca2912
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172365"
---
# <a name="generic-classes-ccli"></a>Clases genéricas (C++/CLI)

Una clase genérica se declara mediante el formato siguiente:

## <a name="syntax"></a>Sintaxis

```cpp
[attributes]
generic <class-key type-parameter-identifier(s)>
[constraint-clauses]
[accessibility-modifiers] ref class identifier  [modifiers]
[: base-list]
{
class-body
} [declarators] [;]
```

## <a name="remarks"></a>Observaciones

En la sintaxis anterior, se utilizan los términos siguientes:

*attributes*<br/>
(Opcional) Información declarativa adicional. Para más información sobre atributos y clases de atributos, consulte Atributos.

*class-key*<br/>
**class** o **typename**

*type-parameter-identifier(s)* , lista separada por comas de identificadores que especifican los nombres de los parámetros de tipo.

*constraint-clauses*<br/>
Lista (no separada por comas) de cláusulas **where** que especifican las restricciones de los parámetros de tipo. Adopta la forma:

> **donde** *type-parameter-Identifier* **:** *Constraint-List*  **...**

*constraint-list*<br/>
*clase o interfaz*[`,` *...* ]

*accessibility-modifiers*<br/>
Modificadores de accesibilidad de la clase genérica. En Windows Runtime, el único modificador permitido es **private**. En Common Language Runtime, los modificadores permitidos son **private** y **public**.

*identifier*<br/>
El nombre de la clase genérica, cualquier identificador de C++ válido.

*modifiers*<br/>
(Opcional) Los modificadores permitidos son **sealed** y **abstract**.

*base-list*<br/>
Una lista que contiene la clase base y las interfaces implementadas, separadas por comas.

*class-body*<br/>
El cuerpo de la clase, que contiene campos, funciones miembro, etc.

*declarators*<br/>
Declaraciones de cualquier variable de este tipo. Por ejemplo: `^`*identifier*[`,` ...]

Puede declarar clases genéricas, como estas (observe que la palabra clave **class** puede usarse en lugar de **typename**). En este ejemplo, `ItemType`, `KeyType` y `ValueType` son tipos desconocidos que se especifican en el punto donde el tipo. `HashTable<int, int>` es un tipo construido del tipo genérico `HashTable<KeyType, ValueType>`. Un número de diferentes tipos construidos puede construirse a partir de un único tipo genérico. Los tipos construidos creados a partir de clases genéricas se tratan como cualquier otro tipo de clase de referencia.

```cpp
// generic_classes_1.cpp
// compile with: /clr
using namespace System;
generic <typename ItemType>
ref struct Stack {
   // ItemType may be used as a type here
   void Add(ItemType item) {}
};

generic <typename KeyType, typename ValueType>
ref class HashTable {};

// The keyword class may be used instead of typename:
generic <class ListItem>
ref class List {};

int main() {
   HashTable<int, Decimal>^ g1 = gcnew HashTable<int, Decimal>();
}
```

Tanto los tipos de valor (ya sean integrados, como **int** o **doble**, o definidos por el usuario) como los tipos de referencia pueden usarse como argumento de tipo genérico. Aparte de esto, la sintaxis dentro de la definición genérica es la misma. Sintácticamente, el tipo desconocido se trata como si fuera un tipo de referencia. Sin embargo, se puede determinar eso en tiempo de ejecución si el tipo utilizado es un tipo de valor y sustituir el código generado adecuado para el acceso directo a los miembros. A los tipos de valor utilizados como argumentos de tipo genérico no se les ha aplicado la conversión boxing y, por lo tanto, no sufren la disminución del rendimiento asociada con ella. La sintaxis utilizada dentro del cuerpo del genérico debe ser `T^` y `->` en lugar de `.`. Cualquier uso de [ref new, gcnew](ref-new-gcnew-cpp-component-extensions.md) con el parámetro de tipo se interpretará de forma adecuada en tiempo de ejecución como la simple creación de un tipo de valor si el tipo de argumento es un tipo de valor.

También puede declarar una clase genérica con [Restricciones de parámetros de tipo genérico (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md) en los tipos que se pueden usar con el parámetro de tipo. En el ejemplo siguiente, cualquier tipo usado con `ItemType` debe implementar la interfaz `IItem`. Al intentar usar **int**, por ejemplo, que no implementa `IItem`, se produciría un error en tiempo de compilación porque el argumento de tipo no satisface la restricción.

```cpp
// generic_classes_2.cpp
// compile with: /clr /c
interface class IItem {};
generic <class ItemType>
where ItemType : IItem
ref class Stack {};
```

Las clases genéricas del mismo espacio de nombres no se pueden sobrecargar con solo cambiar el número o los tipos de parámetros de tipo. Sin embargo, esto es posible si cada clase reside en un espacio de nombres diferente. Por ejemplo, considere las siguientes dos clases, `MyClass` y `MyClass<ItemType>`, en los espacios de nombres `A` y `B`. Las dos clases se pueden sobrecargar en un tercer espacio de nombres C:

```cpp
// generic_classes_3.cpp
// compile with: /clr /c
namespace A {
   ref class MyClass {};
}

namespace B {
   generic <typename ItemType>
   ref class MyClass2 { };
}

namespace C {
   using namespace A;
   using namespace B;

   ref class Test {
      static void F() {
         MyClass^ m1 = gcnew MyClass();   // OK
         MyClass2<int>^ m2 = gcnew MyClass2<int>();   // OK
      }
   };
}
```

La clase base y las interfaces base no pueden ser parámetros de tipo. Sin embargo, la clase base puede incluir el parámetro de tipo como argumento, como en el caso siguiente:

```cpp
// generic_classes_4.cpp
// compile with: /clr /c
generic <typename ItemType>
interface class IInterface {};

generic <typename ItemType>
ref class MyClass : IInterface<ItemType> {};
```

Los constructores y destructores se ejecutan una vez para cada instancia de objeto (como de costumbre); los constructores estáticos se ejecutan una vez para cada tipo construido.

## <a name="fields-in-generic-classes"></a>Campos en clases genéricas

En esta sección se muestra el uso de campos de instancia y estáticos en clases genéricas.

### <a name="instance-variables"></a>Variables de instancia

Las variables de instancia de una clase genérica pueden tener inicializadores de tipo y variable que incluyan parámetros de tipo de la clase envolvente.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, se crean tres instancias diferentes de la clase genérica, MyClass\<ItemType>, mediante los tipos de argumentos adecuados (**int**, **double** y **string**).

```cpp
// generics_instance_fields1.cpp
// compile with: /clr
// Instance fields on generic classes
using namespace System;

generic <typename ItemType>
ref class MyClass {
// Field of the type ItemType:
public :
   ItemType field1;
   // Constructor using a parameter of the type ItemType:
   MyClass(ItemType p) {
   field1 = p;
   }
};

int main() {
   // Instantiate an instance with an integer field:
   MyClass<int>^ myObj1 = gcnew MyClass<int>(123);
   Console::WriteLine("Integer field = {0}", myObj1->field1);

   // Instantiate an instance with a double field:
   MyClass<double>^ myObj2 = gcnew MyClass<double>(1.23);
   Console::WriteLine("Double field = {0}", myObj2->field1);

   // Instantiate an instance with a String field:
   MyClass<String^>^ myObj3 = gcnew MyClass<String^>("ABC");
   Console::WriteLine("String field = {0}", myObj3->field1);
   }
```

```Output
Integer field = 123
Double field = 1.23
String field = ABC
```

## <a name="static-variables"></a>Variables estáticas

En la creación de un nuevo tipo genérico, se crean nuevas instancias de cualquier variable estática y se ejecuta cualquier constructor estático para ese tipo.

Las variables estáticas pueden usar cualquier parámetro de tipo de la clase envolvente.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar campos estáticos y un constructor estático dentro de una clase genérica.

```cpp
// generics_static2.cpp
// compile with: /clr
using namespace System;

interface class ILog {
   void Write(String^ s);
};

ref class DateTimeLog : ILog {
public:
   virtual void Write(String^ s) {
      Console::WriteLine( "{0}\t{1}", DateTime::Now, s);
   }
};

ref class PlainLog : ILog {
public:
   virtual void Write(String^ s) { Console::WriteLine(s); }
};

generic <typename LogType>
where LogType : ILog
ref class G {
   static LogType s_log;

public:
   G(){}
   void SetLog(LogType log) { s_log = log; }
   void F() { s_log->Write("Test1"); }
   static G() { Console::WriteLine("Static constructor called."); }
};

int main() {
   G<PlainLog^>^ g1 = gcnew G<PlainLog^>();
   g1->SetLog(gcnew PlainLog());
   g1->F();

   G<DateTimeLog^>^ g2 = gcnew G<DateTimeLog^>();
   g2->SetLog(gcnew DateTimeLog());

   // prints date
   // g2->F();
}
```

```Output
Static constructor called.
Static constructor called.
Static constructor called.
Test1
```

## <a name="methods-in-generic-classes"></a>Métodos en clases genéricas

Los métodos en clases genéricas pueden ser genéricos por sí solos; los métodos no genéricos se parametrizarán implícitamente mediante el parámetro de tipo de clase.

Las siguientes reglas especiales se aplican a métodos de clases genéricas:

- Los métodos en clases genéricas pueden usar parámetros de tipo como parámetros, tipos de valor devuelto o variables locales.

- Los métodos en clases genéricas pueden usar tipos construidos abiertos o cerrados como parámetros, tipos de valor devuelto o variables locales.

### <a name="non-generic-methods-in-generic-classes"></a>Métodos no genéricos en clases genéricas

Los métodos en clases genéricas que no tienen ningún parámetro de tipo adicional normalmente se conocen como no genéricos, aunque se parametrizan implícitamente mediante la clase genérica envolvente.

La signatura de un método no genérico puede incluir uno o más parámetros de tipo de la clase envolvente, ya sea directamente o en un tipo construido abierto. Por ejemplo:

`void MyMethod(MyClass<ItemType> x) {}`

El cuerpo de estos métodos también puede usar estos parámetros de tipo.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se declara un método no genérico, `ProtectData`, dentro de una clase genérica, `MyClass<ItemType>`. El método usa el parámetro de tipo de clase `ItemType` en su signatura en un tipo construido abierto.

```cpp
// generics_non_generic_methods1.cpp
// compile with: /clr
// Non-generic methods within a generic class.
using namespace System;

generic <typename ItemType>
ref class MyClass {
public:
   String^ name;
   ItemType data;

   MyClass(ItemType x) {
      data = x;
   }

   // Non-generic method using the type parameter:
   virtual void ProtectData(MyClass<ItemType>^ x) {
      data = x->data;
   }
};

// ItemType defined as String^
ref class MyMainClass: MyClass<String^> {
public:
   // Passing "123.00" to the constructor:
   MyMainClass(): MyClass<String^>("123.00") {
      name = "Jeff Smith";
   }

   virtual void ProtectData(MyClass<String^>^ x) override {
      x->data = String::Format("${0}**", x->data);
   }

   static void Main() {
      MyMainClass^ x1 = gcnew MyMainClass();

      x1->ProtectData(x1);
      Console::WriteLine("Name: {0}", x1->name);
      Console::WriteLine("Amount: {0}", x1->data);
   }
};

int main() {
   MyMainClass::Main();
}
```

```Output
Name: Jeff Smith
Amount: $123.00**
```

## <a name="generic-methods-in-generic-classes"></a>Métodos genéricos en clases genéricas

Puede declarar métodos genéricos en clases genéricas y no genéricas. Por ejemplo:

## <a name="example"></a>Ejemplo

```cpp
// generics_method2.cpp
// compile with: /clr /c
generic <typename Type1>
ref class G {
public:
   // Generic method having a type parameter
   // from the class, Type1, and its own type
   // parameter, Type2
   generic <typename Type2>
   void Method1(Type1 t1, Type2 t2) { F(t1, t2); }

   // Non-generic method:
   // Can use the class type param, Type1, but not Type2.
   void Method2(Type1 t1) { F(t1, t1); }

   void F(Object^ o1, Object^ o2) {}
};
```

El método no genérico sigue siendo genérico en el sentido de que se parametriza mediante el parámetro de tipo de la clase, pero no tiene ningún parámetro de tipo adicional.

Todos los tipos de métodos en clases genéricas pueden ser genéricos, incluidos los métodos estáticos, de instancia y virtuales.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra la declaración y el uso de métodos genéricos dentro de clases genéricas:

```cpp
// generics_generic_method2.cpp
// compile with: /clr
using namespace System;
generic <class ItemType>
ref class MyClass {
public:
   // Declare a generic method member.
   generic <class Type1>
   String^ MyMethod(ItemType item, Type1 t) {
      return String::Concat(item->ToString(), t->ToString());
   }
};

int main() {
   // Create instances using different types.
   MyClass<int>^ myObj1 = gcnew MyClass<int>();
   MyClass<String^>^ myObj2 = gcnew MyClass<String^>();
   MyClass<String^>^ myObj3 = gcnew MyClass<String^>();

   // Calling MyMethod using two integers.
   Console::WriteLine("MyMethod returned: {0}",
            myObj1->MyMethod<int>(1, 2));

   // Calling MyMethod using an integer and a string.
   Console::WriteLine("MyMethod returned: {0}",
            myObj2->MyMethod<int>("Hello #", 1));

   // Calling MyMethod using two strings.
   Console::WriteLine("MyMethod returned: {0}",
       myObj3->MyMethod<String^>("Hello ", "World!"));

   // generic methods can be called without specifying type arguments
   myObj1->MyMethod<int>(1, 2);
   myObj2->MyMethod<int>("Hello #", 1);
   myObj3->MyMethod<String^>("Hello ", "World!");
}
```

```Output
MyMethod returned: 12
MyMethod returned: Hello #1
MyMethod returned: Hello World!
```

## <a name="using-nested-types-in-generic-classes"></a>Uso de tipos anidados en clases genéricas

Al igual que sucede con las clases normales, puede declarar otros tipos dentro de una clase genérica. La declaración de clase anidada se parametriza implícitamente mediante los parámetros de tipo de la declaración de clase externa. Por lo tanto, se define una clase anidada distinta para cada tipo externo construido. Por ejemplo, en la declaración:

```cpp
// generic_classes_5.cpp
// compile with: /clr /c
generic <typename ItemType>
ref struct Outer {
   ref class Inner {};
};
```

El tipo `Outer<int>::Inner` no es igual que el tipo `Outer<double>::Inner`.

Al igual que sucede con los métodos genéricos en clases genéricas, se pueden definir parámetros de tipo adicionales para el tipo anidado. Si usa los mismos nombres de parámetros de tipo en la clase interna y externa, el parámetro de tipo interno ocultará el parámetro de tipo externo.

```cpp
// generic_classes_6.cpp
// compile with: /clr /c
generic <typename ItemType>
ref class Outer {
   ItemType outer_item;   // refers to outer ItemType

   generic <typename ItemType>
   ref class Inner {
      ItemType inner_item;   // refers to Inner ItemType
   };
};
```

Dado que no hay ninguna manera de hacer referencia al parámetro de tipo externo, en esta situación el compilador generará una advertencia.

Cuando se nombran tipos genéricos anidados construidos, el parámetro de tipo del tipo externo no se incluye en la lista de parámetros de tipo del tipo interno, aunque el tipo interno se parametrice implícitamente mediante el parámetro de tipo del tipo externo. En el caso anterior, un nombre de un tipo construido sería `Outer<int>::Inner<string>`.

En el ejemplo siguiente se muestra la creación y lectura de una lista vinculada mediante tipos anidados en clases genéricas.

## <a name="example"></a>Ejemplo

```cpp
// generics_linked_list.cpp
// compile with: /clr
using namespace System;
generic <class ItemType>
ref class LinkedList {
// The node class:
public:
   ref class Node {
   // The link field:
   public:
      Node^ next;
      // The data field:
      ItemType item;
   } ^first, ^current;
};

ref class ListBuilder {
public:
   void BuildIt(LinkedList<double>^ list) {
      /* Build the list */
      double m[5] = {0.1, 0.2, 0.3, 0.4, 0.5};
      Console::WriteLine("Building the list:");

      for (int n=0; n<=4; n++) {
         // Create a new node:
         list->current = gcnew LinkedList<double>::Node();

         // Assign a value to the data field:
         list->current->item = m[n];

         // Set the link field "next" to be the same as
         // the "first" field:
         list->current->next = list->first;

         // Redirect "first" to the new node:
         list->first = list->current;

         // Display node's data as it builds:
         Console::WriteLine(list->current->item);
      }
   }

   void ReadIt(LinkedList<double>^ list) {
      // Read the list
      // Make "first" the "current" link field:
      list->current = list->first;
      Console::WriteLine("Reading nodes:");

      // Read nodes until current == null:
      while (list->current != nullptr) {
         // Display the node's data field:
         Console::WriteLine(list->current->item);

         // Move to the next node:
         list->current = list->current->next;
      }
   }
};

int main() {
   // Create a list:
   LinkedList<double>^ aList = gcnew LinkedList<double>();

   // Initialize first node:
   aList->first = nullptr;

   // Instantiate the class, build, and read the list:
   ListBuilder^ myListBuilder = gcnew ListBuilder();
   myListBuilder->BuildIt(aList);
   myListBuilder->ReadIt(aList);
}
```

```Output
Building the list:
0.1
0.2
0.3
0.4
0.5
Reading nodes:
0.5
0.4
0.3
0.2
0.1
```

## <a name="properties-events-indexers-and-operators-in-generic-classes"></a>Propiedades, eventos, indizadores y operadores en clases genéricas

- Las propiedades, los eventos, los indizadores y los operadores pueden usar los parámetros de tipo de la clase genérica envolvente como valores devueltos, parámetros o variables locales, como cuando `ItemType` es un parámetro de tipo de una clase:

    ```cpp
    public ItemType MyProperty {}
    ```

- Las propiedades, los eventos, los indizadores y los operadores no se pueden parametrizar por sí solos.

## <a name="example"></a>Ejemplo

En este ejemplo se muestran declaraciones de una propiedad de instancia dentro de una clase genérica.

```cpp
// generics_generic_properties1.cpp
// compile with: /clr
using namespace System;

generic <typename ItemType>
ref class MyClass {
private:
   property ItemType myField;

public:
   property ItemType MyProperty {
      ItemType get() {
         return myField;
      }
      void set(ItemType value) {
         myField = value;
      }
   }
};

int main() {
   MyClass<String^>^ c = gcnew MyClass<String^>();
   MyClass<int>^ c1 = gcnew MyClass<int>();

   c->MyProperty = "John";
   c1->MyProperty = 234;

   Console::Write("{0}, {1}", c->MyProperty, c1->MyProperty);
}
```

```Output
John, 234
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra una clase genérica con un evento.

```cpp
// generics_generic_with_event.cpp
// compile with: /clr
// Declare a generic class with an event and
// invoke events.
using namespace System;

// declare delegates
generic <typename ItemType>
delegate void ClickEventHandler(ItemType);

// generic class that defines events
generic <typename ItemType>
ref class EventSource {
public:
   // declare the event OnClick
   event ClickEventHandler<ItemType>^ OnClick;
   void FireEvents(ItemType item) {
      // raises events
      OnClick(item);
   }
};

// generic class that defines methods that will called when
// event occurs
generic <typename ItemType>
ref class EventReceiver {
public:
   void OnMyClick(ItemType item) {
   Console::WriteLine("OnClick: {0}", item);
   }
};

int main() {
   EventSource<String^>^ MyEventSourceString =
                   gcnew EventSource<String^>();
   EventSource<int>^ MyEventSourceInt = gcnew EventSource<int>();
   EventReceiver<String^>^ MyEventReceiverString =
                   gcnew EventReceiver<String^>();
   EventReceiver<int>^ MyEventReceiverInt = gcnew EventReceiver<int>();

   // hook handler to event
   MyEventSourceString->OnClick += gcnew ClickEventHandler<String^>(
       MyEventReceiverString, &EventReceiver<String^>::OnMyClick);
   MyEventSourceInt->OnClick += gcnew ClickEventHandler<int>(
             MyEventReceiverInt, &EventReceiver<int>::OnMyClick);

   // invoke events
   MyEventSourceString->FireEvents("Hello");
   MyEventSourceInt->FireEvents(112);

   // unhook handler to event
   MyEventSourceString->OnClick -= gcnew ClickEventHandler<String^>(
        MyEventReceiverString, &EventReceiver<String^>::OnMyClick);
   MyEventSourceInt->OnClick -= gcnew ClickEventHandler<int>(
        MyEventReceiverInt, &EventReceiver<int>::OnMyClick);
}
```

## <a name="generic-structs"></a>Structs genéricos

Las reglas para declarar y usar structs genéricos son las mismas que para las clases genéricas, salvo por las diferencias observadas en la referencia de lenguaje de Visual C++.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se declara un struct genérico, `MyGenStruct`, con un campo, `myField` y se asignan valores de tipos diferentes (**int**, **double**, `String^`) a este campo.

```cpp
// generics_generic_struct1.cpp
// compile with: /clr
using namespace System;

generic <typename ItemType>
ref struct MyGenStruct {
public:
   ItemType myField;

   ItemType AssignValue(ItemType item) {
      myField = item;
      return myField;
   }
};

int main() {
   int myInt = 123;
   MyGenStruct<int>^ myIntObj = gcnew MyGenStruct<int>();
   myIntObj->AssignValue(myInt);
   Console::WriteLine("The field is assigned the integer value: {0}",
            myIntObj->myField);

   double myDouble = 0.123;
   MyGenStruct<double>^ myDoubleObj = gcnew MyGenStruct<double>();
   myDoubleObj->AssignValue(myDouble);
   Console::WriteLine("The field is assigned the double value: {0}",
            myDoubleObj->myField);

   String^ myString = "Hello Generics!";
   MyGenStruct<String^>^ myStringObj = gcnew MyGenStruct<String^>();
   myStringObj->AssignValue(myString);
   Console::WriteLine("The field is assigned the string: {0}",
            myStringObj->myField);
}
```

```Output
The field is assigned the integer value: 123
The field is assigned the double value: 0.123
The field is assigned the string: Hello Generics!
```

## <a name="see-also"></a>Consulte también

[Genéricos](generics-cpp-component-extensions.md)
