---
title: Interfaces genéricas (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- generic interfaces
- interfaces, generic [C++}
ms.assetid: f3da788a-ba83-4db7-9dcf-9b95a8fb9d1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2065b96875f2c441b24eb69f8ca51b06fe5717f0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444500"
---
# <a name="generic-interfaces-visual-c"></a>Interfaces genéricas (Visual C++)

Las restricciones que se aplican a parámetros de tipo en las clases son los mismos que los que se aplican a parámetros de tipo en interfaces (consulte [clases genéricas (C++ / c++ / CLI)](../windows/generic-classes-cpp-cli.md)).

Las reglas que controlan la sobrecarga de funciones son las mismas para las funciones dentro de las clases genéricas o interfaces genéricas.

Implementaciones de miembros de interfaz explícita trabajar con tipos de interfaz construida en la misma manera que con los tipos de interfaz simple (vea los ejemplos siguientes).

Para obtener más información sobre las interfaces, vea [clase de interfaz](../windows/interface-class-cpp-component-extensions.md).

## <a name="syntax"></a>Sintaxis

```cpp
[attributes] generic <class-key type-parameter-identifier[, ...]>
[type-parameter-constraints-clauses][accesibility-modifiers] interface class identifier [: base-list] {   interface-body} [declarators] ;
```

## <a name="remarks"></a>Comentarios

*Atributos*<br/>
(Opcional) Información declarativa adicional. Para obtener más información sobre los atributos y clases de atributos, vea **atributos**.

*clave de clase*<br/>
**clase** o **typename**

*tipo de-parámetro-identificadores*<br/>
Lista separada por comas de identificadores.

*tipo de parámetro restricciones cláusulas*<br/>
Toma la forma especificada en [restricciones en parámetros de tipo genérico (C++ / c++ / CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)

*modificadores de accesibilidad*<br/>
(Opcional) Modificadores de accesibilidad (por ejemplo, **public, private**).

*identifier*<br/>
El nombre de la interfaz.

*base-list*<br/>
(Opcional) Una lista que contiene una o varias interfaces base explícitas separadas por comas.

*cuerpo de la interfaz*<br/>
Declaraciones de los miembros de interfaz.

*declaradores*<br/>
(Opcional) Declaraciones de variables en función de este tipo.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo declarar y crear una instancia de una interfaz genérica. En el ejemplo, la interfaz genérica `IList<ItemType>` se declara. A continuación, se implementa mediante dos clases genéricas, `List1<ItemType>` y `List2<ItemType>`, con diferentes implementaciones.

```cpp
// generic_interface.cpp
// compile with: /clr
using namespace System;

// An exception to be thrown by the List when
// attempting to access elements beyond the
// end of the list.
ref class ElementNotFoundException : Exception {};

// A generic List interface
generic <typename ItemType>
public interface class IList {
   ItemType MoveFirst();
   bool Add(ItemType item);
   bool AtEnd();
   ItemType Current();
   void MoveNext();
};

// A linked list implementation of IList
generic <typename ItemType>
public ref class List1 : public IList<ItemType> {
   ref class Node {
      ItemType m_item;

   public:
      ItemType get_Item() { return m_item; };
      void set_Item(ItemType value) { m_item = value; };

      Node^ next;

      Node(ItemType item) {
         m_item = item;
         next = nullptr;
      }
   };

   Node^ first;
   Node^ last;
   Node^ current;

   public:
   List1() {
      first = nullptr;
      last = first;
      current = first;
   }

   virtual ItemType MoveFirst() {
      current = first;
      if (first != nullptr)  
        return first->get_Item();
      else
         return ItemType();
   }

   virtual bool Add(ItemType item) {
      if (last != nullptr) {
         last->next = gcnew Node(item);
         last = last->next;
      }
      else {
         first = gcnew Node(item);
         last = first;
         current = first;
      }
      return true;
   }

   virtual bool AtEnd() {
      if (current == nullptr )  
        return true;
      else
        return false;
   }

   virtual ItemType Current() {
       if (current != nullptr)  
         return current->get_Item();
       else
         throw gcnew ElementNotFoundException();
   }

   virtual void MoveNext() {
      if (current != nullptr)  
       current = current->next;
      else
        throw gcnew ElementNotFoundException();
   }
};

// An array implementation of IList
generic <typename ItemType>
ref class List2 : public IList<ItemType> {
   array<ItemType>^ item_array;
   int count;
   int current;

   public:

   List2() {
      // not yet possible to declare an
      // array of a generic type parameter
      item_array = gcnew array<ItemType>(256);
      count = current = 0;
   }

   virtual ItemType MoveFirst() {
      current = 0;
      return item_array[0];
   }

   virtual bool Add(ItemType item) {
      if (count < 256)  
         item_array[count++] = item;
      else
        return false;
      return true;
   }

   virtual bool AtEnd() {
      if (current >= count)  
        return true;
      else
        return false;
   }

   virtual ItemType Current() {
      if (current < count)  
        return item_array[current];
      else
        throw gcnew ElementNotFoundException();
   }

   virtual void MoveNext() {
      if (current < count)  
         ++current;
      else
         throw gcnew ElementNotFoundException();
   }
};

// Add elements to the list and display them.
generic <typename ItemType>
void AddStringsAndDisplay(IList<ItemType>^ list, ItemType item1, ItemType item2) {
   list->Add(item1);
   list->Add(item2);
   for (list->MoveFirst(); ! list->AtEnd(); list->MoveNext())  
   Console::WriteLine(list->Current());
}

int main() {
   // Instantiate both types of list.

   List1<String^>^ list1 = gcnew List1<String^>();
   List2<String^>^ list2 = gcnew List2<String^>();

   // Use the linked list implementation of IList.
   AddStringsAndDisplay<String^>(list1, "Linked List", "List1");

   // Use the array implementation of the IList.
   AddStringsAndDisplay<String^>(list2, "Array List", "List2");
}
```

```Output
Linked List
List1
Array List
List2
```

## <a name="example"></a>Ejemplo

En este ejemplo declara una interfaz genérica, `IMyGenIface`y dos interfaces no genéricas, `IMySpecializedInt` y `ImySpecializedString`, que se especializan `IMyGenIface`. Las dos interfaces especializadas, a continuación, se implementan mediante dos clases, `MyIntClass` y `MyStringClass`. El ejemplo muestra cómo especializar interfaces genéricas, crear instancias de interfaces no genéricas y y llamar a los miembros implementados explícitamente en las interfaces.

```cpp
// generic_interface2.cpp
// compile with: /clr
// Specializing and implementing generic interfaces.
using namespace System;

generic <class ItemType>
public interface class IMyGenIface {
   void Initialize(ItemType f);
};

public interface class IMySpecializedInt: public IMyGenIface<int> {
   void Display();
};

public interface class IMySpecializedString: public IMyGenIface<String^> {
   void Display();
};

public ref class MyIntClass: public IMySpecializedInt {
   int myField;

public:
   virtual void Initialize(int f) {
      myField = f;
   }

   virtual void Display() {
      Console::WriteLine("The integer field contains: {0}", myField);
   } 
};

public ref struct MyStringClass: IMySpecializedString { 
   String^ myField;

public:
   virtual void Initialize(String^ f) {
      myField = f;
    }

   virtual void Display() {
      Console::WriteLine("The String field contains: {0}", myField);
   }
};

int main() {
   // Instantiate the generic interface.
   IMyGenIface<int>^ myIntObj = gcnew MyIntClass();

   // Instantiate the specialized interface "IMySpecializedInt."
   IMySpecializedInt^ mySpIntObj = (IMySpecializedInt^) myIntObj;

   // Instantiate the generic interface.
   IMyGenIface<String^>^ myStringObj = gcnew MyStringClass();

   // Instantiate the specialized interface "IMySpecializedString."
   IMySpecializedString^ mySpStringObj =
            (IMySpecializedString^) myStringObj;

   // Call the explicitly implemented interface members.
   myIntObj->Initialize(1234);
   mySpIntObj->Display();

   myStringObj->Initialize("My string");
   mySpStringObj->Display();
}
```

```Output
The integer field contains: 1234
The String field contains: My string
```

## <a name="see-also"></a>Vea también

[Genéricos](../windows/generics-cpp-component-extensions.md)