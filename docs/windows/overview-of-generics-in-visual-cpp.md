---
title: Información general sobre genéricos en C / c++ / CLI
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
ms.openlocfilehash: 1105025ebebdfcbce723505747f6677674c04334
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655174"
---
# <a name="overview-of-generics-in-ccli"></a>Información general sobre genéricos en C / c++ / CLI

Los genéricos son tipos parametrizados compatibles con common language runtime. Un tipo parametrizado es un tipo que se define con un parámetro de tipo desconocido que se especifica cuando se usa el tipo genérico.

## <a name="why-generics"></a>¿Por qué los genéricos?

C++ admite plantillas y ambas plantillas y genéricos admiten tipos parametrizados para crear clases de colección con tipo. Sin embargo, las plantillas proporcionan la parametrización de tiempo de compilación. No se puede hacer referencia a un ensamblado que contiene una definición de plantilla y crear nuevas especializaciones de la plantilla. Una vez compilada, una plantilla especializada es similar de cualquier otra clase o método. En cambio, los genéricos se emiten en MSIL como un tipo parametrizado conocido por el tiempo de ejecución sea un tipo parametrizado; el código de origen que hace referencia a un ensamblado que contiene un tipo genérico puede crear especializaciones de tipo genérico. Para obtener más información sobre la comparación de plantillas estándares de C++ y tipos genéricos, vea [genéricos y plantillas (C++ / c++ / CLI)](../windows/generics-and-templates-visual-cpp.md).

## <a name="generic-functions-and-types"></a>Tipos y funciones genéricas

Tipos de clase, siempre sean tipos administrados, pueden ser genéricos. Un ejemplo de esto podría ser un `List` clase. El tipo de un objeto en la lista sería el parámetro de tipo. Si necesitara un `List` clase para muchos tipos diferentes de objetos, antes de los genéricos que se ha usado un `List` que toma `System::Object` como el tipo de elemento. Pero eso permitiría a cualquier objeto (incluidos los objetos del tipo incorrecto) que se usará en la lista. Esta lista se llamaría una clase de colección sin tipo. En el mejor, puede comprobar el tipo en tiempo de ejecución y produce una excepción. O bien, es posible que ha usado una plantilla, que se podría perder su calidad genérico compilada una vez en un ensamblado. Los consumidores del ensamblado no podrían crear sus propios especializaciones de la plantilla. Los genéricos permiten crear clases de colección con tipo, por ejemplo `List<int>` (léase como "Lista de int") y `List<double>` ("lista de doble") no que generaría un error en tiempo de compilación si intentó incluir un tipo que la colección se ha diseñado para Aceptar en el objeto colección. Además, estos tipos siguen siendo genéricos después de que se compilan.

Una descripción de la sintaxis de las clases genéricas puede encontrarse en [clases genéricas (C++ / c++ / CLI)](../windows/generic-classes-cpp-cli.md). Un nuevo espacio de nombres, <xref:System.Collections.Generic>, incluye un conjunto de tipos de colección con parámetros incluidos <xref:System.Collections.Generic.Dictionary%602>, <xref:System.Collections.Generic.List%601> y <xref:System.Collections.Generic.LinkedList%601>.

Tanto instancia y las funciones miembro de clase estática, delegados y funciones globales también pueden ser genéricas. Funciones genéricas pueden ser necesarias si los parámetros de la función son de un tipo desconocido, o si la propia función debe trabajar con tipos genéricos. En muchos casos donde `System::Object` puede haberse usado en el pasado como parámetro para un tipo de objeto desconocido, un parámetro de tipo genérico puede utilizarse en su lugar, lo que permite más código de seguridad de tipos. Cualquier intento de pasar un tipo que la función no se diseñó para se marcaría como un error en tiempo de compilación. Mediante `System::Object` como un parámetro de función, el paso involuntario de un objeto que la función no se ha diseñado para tratar con no detectaría y tendría que convertir el tipo de objeto desconocido a un tipo específico en el cuerpo de función y de la cuenta para el posibilidad de una excepción InvalidCastException. Con un genérico, el código intenta pasar un objeto a la función provocará un conflicto de tipos por lo que se garantiza que el cuerpo de la función del tipo correcto.

Las mismas ventajas se aplican a las clases de colección basadas en tipos genéricos. Clases de colección en el pasado se usaría `System::Object` para almacenar elementos en una colección. Inserción de objetos de un tipo que la colección no se diseñó para no se ha marcado en tiempo de compilación y a menudo ni siquiera cuando se insertaron los objetos. Normalmente, un objeto podría convertirse en algún otro tipo cuando se tiene acceso a en la colección. Solo cuando la conversión no se pudo sería el tipo inesperado detectado. Los genéricos se resuelve este problema en tiempo de compilación mediante la detección de cualquier código que inserta un tipo que no coincide con (o se convierten implícitamente) el parámetro de tipo de la colección genérica.

Para obtener una descripción de la sintaxis, vea [funciones genéricas (C++ / c++ / CLI)](../windows/generic-functions-cpp-cli.md).

## <a name="terminology-used-with-generics"></a>Terminología que se usa con los genéricos

### <a name="type-parameters"></a>Parámetros de tipo

Una declaración genérica contiene uno o más tipos desconocidos, conocidos como *parámetros de tipo*. Parámetros de tipo se asigna un nombre que representa el tipo dentro del cuerpo de la declaración genérica. El parámetro de tipo se utiliza como un tipo dentro del cuerpo de la declaración genérica. La declaración genérica para `List<T>` contiene el parámetro de tipo T.

### <a name="type-arguments"></a>Argumentos de tipo

El *argumento de tipo* es el tipo real utilizado en lugar del parámetro de tipo cuando está especializado en el tipo genérico para un tipo específico o tipos. Por ejemplo, **int** es el argumento de tipo en `List<int>`. Tipos de valor y tipos de identificador son los únicos tipos que se permiten en como un argumento de tipo genérico.

### <a name="constructed-type"></a>Tipo construido

Un tipo construido a partir de un tipo genérico se conoce como un *tipo construido*. Un tipo completamente especificado, como `List<T>` es un *tipo construido abierto*; un tipo completamente especificado, como `List<double>,` es un *tipo construido cerrado* o *especializado de tipo* . Tipos construidos abiertos pueden usarse en la definición de otros métodos ni tipos genéricos y no puede especificar totalmente hasta que la envolvente genérico es en sí mismo especificado. Por ejemplo, este es un uso de un tipo construido abierto como una clase base para un tipo genérico:

```cpp
// generics_overview.cpp
// compile with: /clr /c
generic <typename T>

ref class List {};

generic <typename T>

ref class Queue : public List<T> {};
```

### <a name="constraint"></a>Restricción

Una restricción es una restricción de los tipos que se puede usar como un parámetro de tipo. Por ejemplo, una clase genérica especificada podría aceptar solo las clases que heredan de una clase especificada o implementar una interfaz especificada. Para obtener más información, consulte [restricciones en parámetros de tipo genérico (C++ / c++ / CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="reference-types-and-value-types"></a>Tipos de referencia y tipos de valor

Controla los tipos y tipos de valor pueden usarse como argumentos de tipo. En la definición genérica, en el que se puede usar el tipo, la sintaxis es la de los tipos de referencia. Por ejemplo, el `->` operador se usa para tener acceso a los miembros del tipo del parámetro de tipo si el tipo usado al final es un tipo de referencia o un tipo de valor o no. Cuando se usa un tipo de valor como argumento de tipo, el tiempo de ejecución genera el código que usa los tipos de valor directamente, sin conversión boxing de los tipos de valor.

Cuando se usa un tipo de referencia como un argumento de tipo genérico, use la sintaxis de identificador. Cuando se usa un tipo de valor como un argumento de tipo genérico, use el nombre del tipo directamente.

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

Parámetros de tipo en una clase genérica se tratan como otros identificadores. Sin embargo, dado que no se conoce el tipo, hay restricciones sobre su uso. Por ejemplo, no puede usar los miembros y métodos de la clase de parámetro de tipo a menos que se conoce el parámetro de tipo para admitir a estos miembros. Es decir, para tener acceso a un miembro a través del parámetro de tipo, debe agregar el tipo que contiene al miembro de la lista de restricciones del parámetro de tipo.

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

Estas restricciones se aplican a los operadores también. No puede usar un parámetro de tipo genérico sin restricciones el `==` y `!=` operadores para comparar dos instancias del parámetro de tipo, en caso de que el tipo no admite estos operadores. Estas comprobaciones son necesarias para los genéricos, pero no para las plantillas, porque se pueden especializar genéricos en tiempo de ejecución con cualquier clase que satisface las restricciones, cuando es demasiado tarde para comprobar el uso de miembros no válidos.

Una instancia predeterminada del parámetro de tipo puede crearse mediante el `()` operador. Por ejemplo:

`T t = T();`

donde `T` es un parámetro de tipo en una definición de clase o método genérico, inicializa la variable a su valor predeterminado. Si `T` es una clase ref es un puntero nulo; si `T` es una clase de valor, el objeto se inicializa en cero. Esto se denomina un *predeterminado inicializador*.

## <a name="see-also"></a>Vea también

[Genéricos](../windows/generics-cpp-component-extensions.md)