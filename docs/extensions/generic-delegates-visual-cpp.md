---
title: Delegados genéricos (C++/CLI)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- generic delegates
- delegates, generic [C++]
ms.assetid: 09d430b2-1aef-4fbc-87f9-9d7b8185d798
ms.openlocfilehash: 4c579d0c0ab39a2ddcadfd116bdfed8ba9da2863
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182037"
---
# <a name="generic-delegates-ccli"></a>Delegados genéricos (C++/CLI)

Puede usar parámetros de tipo genérico con delegados. Para obtener más información sobre delegados, consulte [delegate (C++/CLI y C++/CX)](delegate-cpp-component-extensions.md).

## <a name="syntax"></a>Sintaxis

```cpp
[attributes]
generic < [class | typename] type-parameter-identifiers>
[type-parameter-constraints-clauses]
[accessibility-modifiers] delegate result-type identifier
([formal-parameters]);
```

### <a name="parameters"></a>Parámetros

*attributes*<br/>
(Opcional) Información declarativa adicional. Para más información sobre atributos y clases de atributos, consulte Atributos.

*type-parameter-identifier(s)*<br/>
Lista de identificadores separados por comas para los parámetros de tipo.

*type-parameter-constraints-clauses*<br/>
Toma la forma especificada en el artículo sobre [las restricciones en parámetros de tipo genérico (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md).

*accessibility-modifiers*<br/>
(Opcional) Modificadores de accesibilidad (por ejemplo, **public** y **private**).

*result-type*<br/>
Tipo de valor devuelto del delegado.

*identifier*<br/>
Nombre del delegado.

*formal-parameters*<br/>
(Opcional) Lista de parámetros del delegado.

## <a name="example"></a>Ejemplo

Los parámetros de tipo delegado se especifican en el punto en el que se crea un objeto delegado. Tanto el delegado como el método asociado a él deben tener la misma firma. A continuación se ofrece un ejemplo de una declaración de delegado genérico.

```cpp
// generics_generic_delegate1.cpp
// compile with: /clr /c
generic <class ItemType>
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);
```

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra que:

- No puede usar el mismo objeto delegado con tipos construidos diferentes. Cree objetos delegados distintos para tipos diferentes.

- Un delegado genérico puede asociarse a un método genérico.

- Al llamarse a un método genérico sin especificar argumentos de tipo, el compilador intenta realizar inferencia de los argumentos de tipo para la llamada.

```cpp
// generics_generic_delegate2.cpp
// compile with: /clr
generic <class ItemType>
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);

generic <class ItemType>
ref struct MyGenClass {
   ItemType MyMethod(ItemType i, ItemType % j) {
      return ItemType();
   }
};

ref struct MyClass {
   generic <class ItemType>
   static ItemType MyStaticMethod(ItemType i, ItemType % j) {
      return ItemType();
   }
};

int main() {
   MyGenClass<int> ^ myObj1 = gcnew MyGenClass<int>();
   MyGenClass<double> ^ myObj2 = gcnew MyGenClass<double>();
   GenDelegate<int>^ myDelegate1 =
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);

   GenDelegate<double>^ myDelegate2 =
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);

   GenDelegate<int>^ myDelegate =
      gcnew GenDelegate<int>(&MyClass::MyStaticMethod<int>);
}
```

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se declara un delegado genérico `GenDelegate<ItemType>` y, a continuación, se crea una instancia de este asociándolo al método `MyMethod` que usa el parámetro de tipo `ItemType`. Se crean e invocan dos instancias del delegado (una entera y una doble).

```cpp
// generics_generic_delegate.cpp
// compile with: /clr
using namespace System;

// declare generic delegate
generic <typename ItemType>
delegate ItemType GenDelegate (ItemType p1, ItemType% p2);

// Declare a generic class:
generic <typename ItemType>
ref class MyGenClass {
public:
   ItemType MyMethod(ItemType p1, ItemType% p2) {
      p2 = p1;
      return p1;
    }
};

int main() {
   int i = 0, j = 0;
   double m = 0.0, n = 0.0;

   MyGenClass<int>^ myObj1 = gcnew MyGenClass<int>();
   MyGenClass<double>^ myObj2 = gcnew MyGenClass<double>();

   // Instantiate a delegate using int.
   GenDelegate<int>^ MyDelegate1 =
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);

   // Invoke the integer delegate using MyMethod.
   i = MyDelegate1(123, j);

   Console::WriteLine(
      "Invoking the integer delegate: i = {0}, j = {1}", i, j);

   // Instantiate a delegate using double.
   GenDelegate<double>^ MyDelegate2 =
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);

   // Invoke the integer delegate using MyMethod.
   m = MyDelegate2(0.123, n);

   Console::WriteLine(
      "Invoking the double delegate: m = {0}, n = {1}", m, n);
}
```

```Output
Invoking the integer delegate: i = 123, j = 123
Invoking the double delegate: m = 0.123, n = 0.123
```

## <a name="see-also"></a>Consulte también

[Genéricos](generics-cpp-component-extensions.md)
