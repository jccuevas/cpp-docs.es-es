---
title: Introducción a los genéricos en C++/CLI
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], about generics
- default initializers [C++]
- type parameters [C++]
- constructed types
- type arguments [C++]
- constructed types, open [C++]
- open constructed types [C++]
- constructed types, closed [C++]
ms.assetid: 21f10637-0fce-4916-b925-6c86a126d3aa
ms.openlocfilehash: 38d33faec3610495e8cc5e97db2e81bd74be8b8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515670"
---
# <a name="overview-of-generics-in-ccli"></a>Introducción a los genéricos en C++/CLI

Los genéricos son tipos parametrizados compatibles con Common Language Runtime. Un tipo parametrizado es un tipo que se define con un parámetro de tipo desconocido que se especifica cuando se usa el tipo genérico.

## <a name="why-generics"></a>¿Por qué usar genéricos?

C++ admite plantillas y tanto estas como los genéricos admiten tipos parametrizados para crear clases de colección con tipo. Sin embargo, las plantillas proporcionan parametrización en tiempo de compilación. No se puede hacer referencia a un ensamblado que contenga una definición de plantilla y crear especializaciones de la plantilla. Una vez compilada, una plantilla especializada se parece a cualquier otra clase o método. En cambio, los genéricos se emiten en MSIL como un tipo parametrizado que se sabe que lo es en tiempo de ejecución; el código de origen que hace referencia a un ensamblado que contiene un tipo genérico puede crear especializaciones del tipo genérico. Para más información sobre la comparación de plantillas y genéricos de C++ estándar, consulte [Genéricos y plantillas (C++/CLI)](generics-and-templates-visual-cpp.md).

## <a name="generic-functions-and-types"></a>Funciones y tipos genéricos

Los tipos de clase, mientras sean tipos administrados, pueden ser genéricos. Un ejemplo de esto podría ser una clase `List`. El tipo de un objeto de la lista sería el parámetro de tipo. Si necesitara una clase `List` para muchos tipos diferentes de objetos, en lugar de genéricos podría haber usado un objeto `List` que toma `System::Object` como el tipo de elemento. Pero eso permitiría el uso de cualquier objeto de la lista (incluidos los objetos del tipo incorrecto). A una lista así se la conocería como clase de colección sin tipo. En el mejor de los casos, podría comprobar el tipo en tiempo de ejecución y producir una excepción. O bien, podría haber usado una plantilla, que perdería su calidad genérica una vez compilada en un ensamblado. Los consumidores del ensamblado no podrían crear sus propias especializaciones de la plantilla. Los genéricos permiten crear clases de colección con tipo, por ejemplo `List<int>` (se lee como "List of int") y `List<double>` ("List of double") que generarían un error en tiempo de compilación si intentara colocar un tipo en la colección con tipo que, por diseño, la colección no puede aceptar. Además, estos tipos siguen siendo genéricos una vez compilados.

Una descripción de la sintaxis de las clases genéricas puede encontrarse en [Clases genéricas (C++/CLI)](generic-classes-cpp-cli.md). Un nuevo espacio de nombres, <xref:System.Collections.Generic>, incluye un conjunto de tipos de colección parametrizados, como <xref:System.Collections.Generic.Dictionary%602>, <xref:System.Collections.Generic.List%601> y <xref:System.Collections.Generic.LinkedList%601>.

Las funciones miembro de clase estática e instancia y las funciones delegadas y globales también pueden ser genéricas. Las funciones genéricas pueden ser necesarias si los parámetros de la función son de un tipo desconocido, o si la propia función debe funcionar con tipos genéricos. En muchos casos donde `System::Object` se puede haber usado en el pasado como parámetro para un tipo de objeto desconocido, se puede usar en su lugar un parámetro de tipo genérico, lo que permite más código de seguridad de tipos. Cualquier intento de pasar un tipo para el que no se ha diseñado la función se marcaría como error en tiempo de compilación. Al usar `System::Object` como parámetro de función, no se detectaría el paso involuntario de un objeto para el que la función no está diseñada y tendría que convertir el tipo de objeto desconocido a un tipo específico en el cuerpo de función, además de considerar la posibilidad de una excepción InvalidCastException. Con un genérico, si el código intenta pasar un objeto a la función se produciría un conflicto de tipos para garantizar que el cuerpo de la función tenga el tipo correcto.

Las mismas ventajas se aplican a las clases de colección basadas en genéricos. En el pasado, las clases de colección usaban `System::Object` para almacenar elementos de una colección. La inserción de objetos de un tipo para el que la colección no estaba diseñada no se marcaba en tiempo de compilación y, con frecuencia, ni siquiera cuando se insertaban los objetos. Normalmente, un objeto se convertía en algún otro tipo cuando se accedía a él en la colección. Solo si la conversión producía error, se detectaba el tipo inesperado. Los genéricos resuelven este problema en tiempo de compilación al detectar cualquier código que inserta un tipo que no coincide con (o se convierten implícitamente en) el parámetro de tipo de la colección genérica.

Para ver una descripción de la sintaxis, consulte [Funciones genéricas (C++/CLI)](generic-functions-cpp-cli.md).

## <a name="terminology-used-with-generics"></a>Terminología usada con los genéricos

### <a name="type-parameters"></a>Parámetros de tipo

Una declaración genérica contiene uno o varios tipos desconocidos conocidos como *parámetros de tipo*. A los parámetros de tipo se les asigna un nombre que representa el tipo dentro del cuerpo de la declaración genérica. El parámetro de tipo se utiliza como tipo dentro del cuerpo de la declaración genérica. La declaración genérica de `List<T>` contiene el parámetro de tipo T.

### <a name="type-arguments"></a>Argumentos de tipo

El *argumento de tipo* es el tipo real utilizado en lugar del parámetro de tipo cuando el genérico se especializa para uno o varios tipos específicos. Por ejemplo, **int** es el argumento de tipo en `List<int>`. Los tipos de valor y los tipos de manipulador son los únicos tipos que se permiten como argumento de tipo genérico.

### <a name="constructed-type"></a>Tipo construido

Un tipo construido a partir de un tipo genérico se conoce como *tipo construido*. Un tipo no especificado completamente, como `List<T>` es un *tipo construido abierto*; un tipo completamente especificado, como `List<double>,` es un *tipo construido cerrado* o un *tipo especializado*. Los tipos construidos abiertos pueden usarse en la definición de otros métodos o tipos genéricos y no se pueden especificar completamente hasta que no se especifica el propio genérico envolvente. Por ejemplo, este es un uso de un tipo construido abierto como clase base para un genérico:

```cpp
// generics_overview.cpp
// compile with: /clr /c
generic <typename T>

ref class List {};

generic <typename T>

ref class Queue : public List<T> {};
```

### <a name="constraint"></a>Restricción

Una restricción es una limitación sobre los tipos que se pueden usar como parámetro de tipo. Por ejemplo, una clase genérica dada podría aceptar solo las clases que se heredan de una clase especificada, o implementar una interfaz especificada. Para más información, consulte [Restricciones de parámetros de tipo genérico](constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="reference-types-and-value-types"></a>Tipos de referencia y tipos de valor

Los tipos de manipuladores y los tipos de valor se pueden usar como argumentos de tipo. En la definición de genéricos, en la que se puede usar cualquier tipo, la sintaxis es la de los tipos de referencia. Por ejemplo, el operador `->` se usa para acceder a los miembros del tipo del parámetro de tipo si el tipo finalmente usado es un tipo de referencia o un tipo de valor. Cuando se usa un tipo de valor como argumento de tipo, se genera código en tiempo de ejecución que usa los tipos de valor directamente, sin aplicarles la conversión boxing.

Cuando se use un tipo de referencia como argumento de tipo genérico, utilice la sintaxis del manipulador. Cuando se use un tipo de valor como argumento de tipo genérico, utilice el nombre del tipo directamente.

```cpp
// generics_overview_2.cpp
// compile with: /clr
generic <typename T>

ref class GenericType {};
ref class ReferenceType {};

value struct ValueType {};

int main() {
    GenericType<ReferenceType^> x;
    GenericType<ValueType> y;
}
```

## <a name="type-parameters"></a>Parámetros de tipo

Los parámetros de tipo de una clase genérica se tratan como otros identificadores. Sin embargo, como no se conoce el tipo, hay restricciones sobre su uso. Por ejemplo, no puede usar miembros y métodos de la clase de parámetro de tipo a menos que se sepa que el parámetro de tipo admite estos miembros. Es decir, para acceder a un miembro mediante el parámetro de tipo, debe agregar el tipo que contiene el miembro a la lista de restricciones del parámetro de tipo.

```cpp
// generics_overview_3.cpp
// compile with: /clr
interface class I {
   void f1();
   void f2();
};

ref struct R : public I {
   virtual void f1() {}
   virtual void f2() {}
   virtual void f3() {}
};

generic <typename T>
where T : I
void f(T t) {
   t->f1();
   t->f2();
   safe_cast<R^>(t)->f3();
}

int main() {
   f(gcnew R());
}
```

Estas restricciones se aplican también a los operadores. Un parámetro de tipo genérico sin restricciones no puede usar los operadores `==` y `!=` para comparar dos instancias del parámetro de tipo, en caso de que el tipo no admita estos operadores. Estas comprobaciones son necesarias para los genéricos, pero no para las plantillas, porque los genéricos se pueden especializar en tiempo de ejecución con cualquier clase que satisfaga las restricciones, cuando es demasiado tarde para comprobar el uso de miembros no válidos.

Una instancia predeterminada del parámetro de tipo puede crearse mediante el operador `()`. Por ejemplo:

`T t = T();`

donde `T` es un parámetro de tipo en una definición de clase o método genéricos, inicializa la variable a su valor predeterminado. Si `T` es una clase de referencia, será un puntero nulo; si `T` es una clase de valor, el objeto se inicializa en cero. Esto se conoce como *inicializador predeterminado*.

## <a name="see-also"></a>Vea también

[Genéricos](generics-cpp-component-extensions.md)