---
title: Funciones genéricas (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- functions [C++], generic
- generic methods
- generics [C++], functions
- methods [C++], generic
- generic functions
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
ms.openlocfilehash: a4a1702c8b9902f5265a8a5f92316d7c82751609
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516380"
---
# <a name="generic-functions-ccli"></a>Funciones genéricas (C++/CLI)

Una función genérica es una función que se declara con parámetros de tipo. Cuando se invoca, se usan tipos reales en lugar de los parámetros de tipo.

## <a name="all-platforms"></a>Todas las plataformas

### <a name="remarks"></a>Comentarios

Esta característica no se aplica a todas las plataformas.

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

### <a name="remarks"></a>Comentarios

Esta característica no se admite en Windows Runtime.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Una función genérica es una función que se declara con parámetros de tipo. Cuando se invoca, se usan tipos reales en lugar de los parámetros de tipo.

### <a name="syntax"></a>Sintaxis

```cpp
[attributes] [modifiers]
return-type identifier<type-parameter identifier(s)>
[type-parameter-constraints clauses]

([formal-parameters])
{function-body}
```

### <a name="parameters"></a>Parámetros

*Atributos*<br/>
(Opcional) Información declarativa adicional. Para más información sobre atributos y clases de atributos, consulte Atributos.

*modifiers*<br/>
(Opcional) Un modificador de la función, por ejemplo, estático.  **virtual** no se permite porque los métodos virtuales no pueden ser genéricos.

*return-type*<br/>
Tipo devuelto por el método. Si el tipo de valor devuelto es nulo, no se requiere ningún valor devuelto.

*identifier*<br/>
Nombre de la función.

*type-parameter identifier(s)*<br/>
Lista separada por comas de identificadores.

*formal-parameters*<br/>
(Opcional) Lista de parámetros.

*type-parameter-constraints-clauses*<br/>
Especifica restricciones sobre los tipos que se pueden usar como argumentos de tipo, y adopta la forma especificada en [Restricciones de parámetros de tipo genérico (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md).

*function-body*<br/>
El cuerpo del método, que puede hacer referencia a los identificadores de parámetro de tipo.

### <a name="remarks"></a>Comentarios

Las funciones genéricas son funciones declaradas con un parámetro de tipo genérico. Pueden ser métodos de una clase o un struct, o funciones independientes. Una sola declaración genérica declara implícitamente una familia de funciones que solo difieren en la sustitución de un tipo real diferente por el parámetro de tipo genérico.

Un constructor de clases o structs no se puede declarar con parámetros de tipo genérico.

Cuando se invoca, el parámetro de tipo genérico se reemplaza por un tipo real. El tipo real puede especificarse explícitamente entre corchetes angulares mediante una sintaxis similar a la de la llamada de función de plantilla. Si se invoca sin los parámetros de tipo, el compilador intentará deducir el tipo real de los parámetros proporcionados en la llamada de función. Si el argumento de tipo deseado no se puede deducir de los parámetros usados, el compilador notificará un error.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

En ejemplo de código siguiente se muestra una función genérica.

```cpp
// generics_generic_function_1.cpp
// compile with: /clr
generic <typename ItemType>
void G(int i) {}

ref struct A {
   generic <typename ItemType>
   void G(ItemType) {}

   generic <typename ItemType>
   static void H(int i) {}
};

int main() {
   A myObject;

   // generic function call
   myObject.G<int>(10);

   // generic function call with type parameters deduced
   myObject.G(10);

   // static generic function call
   A::H<int>(10);

   // global generic function call
   G<int>(10);
}
```

Las funciones genéricas se pueden sobrecargar según su signatura o aridad, el número de parámetros de tipo en una función. Además, las funciones genéricas se pueden sobrecargar con funciones no genéricas del mismo nombre, siempre y cuando las funciones se diferencien en algunos parámetros de tipo. Por ejemplo, se pueden sobrecargar las siguientes funciones:

```cpp
// generics_generic_function_2.cpp
// compile with: /clr /c
ref struct MyClass {
   void MyMythod(int i) {}

   generic <class T>
   void MyMythod(int i) {}

   generic <class T, class V>
   void MyMythod(int i) {}
};
```

En el ejemplo siguiente se usa una función genérica para hallar el primer elemento de una matriz. Declara `MyClass`, que hereda de la clase base `MyBaseClass`. `MyClass` contiene una función genérica, `MyFunction`, que llama a otra función genérica, `MyBaseClassFunction`, dentro de la clase base. En `main`, la función genérica, `MyFunction`, se invoca con argumentos de tipo diferentes.

```cpp
// generics_generic_function_3.cpp
// compile with: /clr
using namespace System;

ref class MyBaseClass {
protected:
   generic <class ItemType>
   ItemType MyBaseClassFunction(ItemType item) {
      return item;
   }
};

ref class MyClass: public MyBaseClass {
public:
   generic <class ItemType>
   ItemType MyFunction(ItemType item) {
      return MyBaseClass::MyBaseClassFunction<ItemType>(item);
   }
};

int main() {
   MyClass^ myObj = gcnew MyClass();

   // Call MyFunction using an int.
   Console::WriteLine("My function returned an int: {0}",
                           myObj->MyFunction<int>(2003));

   // Call MyFunction using a string.
   Console::WriteLine("My function returned a string: {0}",
   myObj->MyFunction<String^>("Hello generic functions!"));
}
```

```Output
My function returned an int: 2003
My function returned a string: Hello generic functions!
```

## <a name="see-also"></a>Vea también

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)<br/>
[Genéricos](generics-cpp-component-extensions.md)
