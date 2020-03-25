---
title: Restricciones de parámetros de tipo genérico (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- where
helpviewer_keywords:
- where keyword [C++]
- constraints, C++
ms.assetid: eb828cc9-684f-48a3-a898-b327700c0a63
ms.openlocfilehash: be5af8f6b2edaa8f93fef7ae06b2175b54b25396
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172483"
---
# <a name="constraints-on-generic-type-parameters-ccli"></a>Restricciones de parámetros de tipo genérico (C++/CLI)

En las declaraciones de método o tipo genérico, puede calificar un parámetro de tipo con restricciones. Una restricción es un requisito que deben satisfacer los tipos usados como argumentos de tipo. Por ejemplo, una restricción podría ser que el argumento de tipo debe implementar una determinada interfaz o heredar de una clase específica.

Las restricciones son opcionales; no especificar una restricción sobre un parámetro es equivalente a restringir ese parámetro a <xref:System.Object>.

## <a name="syntax"></a>Sintaxis

```cpp
where type-parameter: constraint list
```

### <a name="parameters"></a>Parámetros

*type-parameter*<br/>
Uno de los parámetros de tipo, que se va a restringir.

*constraint list*<br/>
*constraint list* es una lista separada por comas de especificaciones de restricción. La lista puede incluir interfaces que se van a implementar por el parámetro de tipo.

La lista puede incluir también una clase. Para que el argumento de tipo satisfaga una restricción de clase base, debe ser de la misma clase que la restricción o derivarse de ella.

También puede especificar **gcnew()** para indicar que el argumento de tipo debe tener un constructor público sin parámetros; o **ref class** para indicar que el argumento de tipo debe ser un tipo de referencia, incluido cualquier tipo de clase, interfaz, delegado o matriz; o **value class** para indicar que el tipo de argumento debe ser un tipo de valor. Se puede especificar cualquier tipo de valor excepto \<T>.

También puede especificar un parámetro genérico como restricción. El argumento de tipo proporcionado para el tipo que se va a restringir debe ser o derivarse del tipo de la restricción. Esto se conoce como restricción de tipo "naked".

## <a name="remarks"></a>Observaciones

La cláusula de restricción consta de **where** seguido de un tipo de parámetro, dos puntos ( **:** ) y la restricción, que especifica la naturaleza de la restricción sobre el tipo de parámetro. **where** es una palabra clave contextual; para más información, consulte [Palabras clave contextuales](context-sensitive-keywords-cpp-component-extensions.md). Separe varias cláusulas **where** con un espacio.

Se aplican restricciones a parámetros de tipo para imponer limitaciones sobre los tipos que se pueden usar como argumentos con un tipo o método genérico.

Las restricciones de clase e interfaz especifican que los tipos de argumento deben ser o heredar de una clase especificada o implementar una interfaz especificada.

La aplicación de restricciones a un tipo o método genérico permite que el código de ese tipo o método aproveche las ventajas de las características conocidas de los tipos restringidos. Por ejemplo, se puede declarar una clase genérica como que el tipo de parámetro implementa la interfaz `IComparable<T>`:

```cpp
// generics_constraints_1.cpp
// compile with: /c /clr
using namespace System;
generic <typename T>
where T : IComparable<T>
ref class List {};
```

Esta restricción requiere que un argumento de tipo usado para `T` implemente `IComparable<T>` en tiempo de compilación. También permite la llamada a métodos de interfaz, como `CompareTo`. Para llamar a métodos de interfaz, no hace falta ninguna conversión sobre una instancia del parámetro de tipo.

Los métodos estáticos de la clase del argumento de tipo no se pueden llamar mediante el parámetro de tipo, sino solo mediante el tipo con nombre real.

Una restricción no puede ser un tipo de valor, sino tipos integrados como **int** o **double**. Puesto que los tipos de valor no pueden tener clases derivadas, solo una clase podría satisfacer la restricción. En ese caso, el genérico se puede reescribir con el parámetro de tipo reemplazado por el tipo de valor específico.

En ocasiones, las restricciones son necesarias ya que el compilador no permitirá el uso de métodos u otras características de un tipo desconocido a menos que las restricciones impliquen que el tipo desconocido admite los métodos o interfaces.

Se pueden especificar varias restricciones para el mismo parámetro de tipo en una lista separada por comas

```cpp
// generics_constraints_2.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;
generic <typename T>
where T : List<T>, IComparable<T>
ref class List {};
```

Con varios parámetros de tipo, use una cláusula **where** para cada uno. Por ejemplo:

```cpp
// generics_constraints_3.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;

generic <typename K, typename V>
   where K: IComparable<K>
   where V: IComparable<K>
ref class Dictionary {};
```

En resumen, para usar restricciones en el código, siga las reglas siguientes:

- Si aparecen varias restricciones, estas pueden mostrarse en cualquier orden.

- Las restricciones también pueden ser tipos de clase, como clases base abstractas. Sin embargo, las restricciones no pueden ser tipos de valor o clases selladas.

- Las restricciones no pueden ser por sí solas parámetros de tipo, pero pueden estar relacionadas con ellos en un tipo construido abierto. Por ejemplo:

    ```cpp
    // generics_constraints_4.cpp
    // compile with: /c /clr
    generic <typename T>
    ref class G1 {};

    generic <typename Type1, typename Type2>
    where Type1 : G1<Type2>   // OK, G1 takes one type parameter
    ref class G2{};
    ```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar restricciones para llamar a métodos de instancia en parámetros de tipo.

```cpp
// generics_constraints_5.cpp
// compile with: /clr
using namespace System;

interface class IAge {
   int Age();
};

ref class MyClass {
public:
   generic <class ItemType> where ItemType : IAge
   bool isSenior(ItemType item) {
      // Because of the constraint,
      // the Age method can be called on ItemType.
      if (item->Age() >= 65)
         return true;
      else
         return false;
   }
};

ref class Senior : IAge {
public:
   virtual int Age() {
      return 70;
   }
};

ref class Adult: IAge {
public:
   virtual int Age() {
      return 30;
   }
};

int main() {
   MyClass^ ageGuess = gcnew MyClass();
   Adult^ parent = gcnew Adult();
   Senior^ grandfather = gcnew Senior();

   if (ageGuess->isSenior<Adult^>(parent))
      Console::WriteLine("\"parent\" is a senior");
   else
      Console::WriteLine("\"parent\" is not a senior");

   if (ageGuess->isSenior<Senior^>(grandfather))
      Console::WriteLine("\"grandfather\" is a senior");
   else
      Console::WriteLine("\"grandfather\" is not a senior");
}
```

```Output
"parent" is not a senior
"grandfather" is a senior
```

## <a name="example"></a>Ejemplo

Cuando se usa un parámetro de tipo genérico como restricción, esto se conoce como restricción de tipo "naked". Las restricciones de tipo "naked" son útiles cuando una función miembro con su propio parámetro de tipo tiene que restringir ese parámetro al parámetro de tipo del tipo contenedor.

En el ejemplo siguiente, `T` es una restricción de tipo "naked" en el contexto del método `Add`.

Las restricciones de tipo "naked" también se pueden utilizar en definiciones de clase genéricas. La utilidad de las restricciones de tipo "naked" con clases genéricas es limitada, ya que el compilador no puede dar por supuesto nada sobre la restricción de tipo "naked", excepto que se deriva de <xref:System.Object>. Use restricciones de tipo "naked" sobre clases genéricas en situaciones en las que quiera aplicar una relación de herencia entre dos parámetros de tipo.

```cpp
// generics_constraints_6.cpp
// compile with: /clr /c
generic <class T>
ref struct List {
   generic <class U>
   where U : T
   void Add(List<U> items)  {}
};

generic <class A, class B, class C>
where A : C
ref struct SampleClass {};
```

## <a name="see-also"></a>Consulte también

[Genéricos](generics-cpp-component-extensions.md)
