---
title: Tipos triviales, de diseño estándar, POD y literales
ms.date: 04/05/2018
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
ms.openlocfilehash: 2745302b3ebd7927e9d839e4661e884a2bd91042
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865796"
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>Tipos triviales, de diseño estándar, POD y literales

El término *diseño* hace referencia a cómo se organizan en la memoria los miembros de un objeto de tipo de unión, estructura o clase. En algunos casos, el diseño está bien definido por la especificación del lenguaje. Pero cuando una clase o estructura contienen determinadas características de lenguaje C++ como clases base virtuales, funciones virtuales o miembros con distintos controles de acceso, el compilador es libre de elegir un diseño. Ese diseño puede variar dependiendo de las optimizaciones que se realizan y puede que, en muchos casos, el objeto ni siquiera ocupe un área contigua de memoria. Por ejemplo, si una clase tiene funciones virtuales, es posible que todas las instancias de esa clase compartan una única tabla de funciones virtuales. Estos tipos resultan muy útiles, pero también tienen limitaciones. Debido a que el diseño no está definido, no se pueden pasar a programas escritos en otros lenguajes, como C, y debido a que pueden no ser contiguos, no se pueden copiar con confianza con funciones rápidas de bajo nivel, como `memcopy`, ni serializarse a través de una red.

Para permitir a los compiladores, así como a los metaprogramas y programas de C++, razonar sobre la idoneidad de un tipo dado para las operaciones que dependen de un diseño de memoria específica, C++14 presentó tres categorías de clases y estructuras simples: *trivial*, *diseño estándar* y *POD* (Plain Old Data). La biblioteca estándar tiene las plantillas de función `is_trivial<T>`, `is_standard_layout<T>` y `is_pod<T>` que determinan si un tipo determinado pertenece a una categoría determinada.

## <a name="trivial-types"></a>Tipos triviales

Cuando una clase o estructura de C++ tiene funciones miembro especiales proporcionadas por el compilador o establecidas explícitamente como valor predeterminado, se trata de un tipo trivial. Ocupa un área de memoria contigua. Puede tener miembros con distintos especificadores de acceso. En C++, el compilador es libre de elegir cómo ordenar los miembros en esta situación. Por lo tanto, puede usar la función memcopy en dichos objetos pero no consumirlos con confianza desde un programa de C. Un tipo T trivial puede copiarse en una matriz de tipos char o unsigned char y copiarse de nuevo de forma segura en una variable T. Tenga en cuenta que, debido a los requisitos de alineación, podría haber bytes de relleno entre miembros del tipo.

Los tipos triviales tienen un constructor predeterminado trivial, un constructor de copia trivial, un operador de asignación de copia trivial y un destructor trivial. En cada caso, *trivial* significa que el operador, constructor o destructor no están proporcionados por el usuario y pertenecen a una clase que

- no tiene funciones virtuales ni clases base virtuales,

- ni tiene clases base con un constructor, operador o destructor de tipo no trivial correspondiente

- ni miembros de datos del tipo de clase con un constructor, operador o destructor de tipo no trivial correspondiente

En los siguientes ejemplos se muestran tipos triviales. En Trivial2, la presencia del constructor `Trivial2(int a, int b)` requiere que se proporcione un constructor predeterminado. Para que el tipo se considere trivial, debe establecerse explícitamente ese constructor como predeterminado.

```cpp
struct Trivial
{
      int i;
private:
   int j;
   };

struct Trivial2
{
   int i;
   Trivial2(int a, int b) : i(a), j(b) {}
   Trivial2() = default;
   private:
   int j;   // Different access control
};
```

## <a name="standard-layout-types"></a>Tipos de diseño estándar

Cuando una clase o estructura contienen determinadas características del lenguaje C++, como funciones virtuales que no se encuentran en el lenguaje C, y todos los miembros tienen el mismo control de acceso, se trata de un tipo de diseño estándar. Es capaz de usar la función memcopy y el diseño está lo suficientemente definido como para que los programas de C puedan consumirlo. Los tipos de diseño estándar pueden tener funciones miembro especiales definidas por el usuario. Además, los tipos de diseño estándar tienen estas características:

- no tienen funciones virtuales ni clases base virtuales

- todos los miembros de datos no estáticos tienen el mismo control de acceso

- todos los miembros no estáticos del tipo de clase son de diseño estándar

- las clases base son de diseño estándar

- no tienen clases base del mismo tipo como primer miembro de datos no estáticos.

- cumplen alguna de estas condiciones:

  - no tienen ningún miembro de datos no estáticos en la clase más derivada y no tienen más de una clase base con miembros de datos no estáticos, o

  - no tienen clases base con miembros de datos no estáticos

El código siguiente muestra un ejemplo de un tipo de diseño estándar:

```cpp
struct SL
{
   // All members have same access:
   int i;
   int j;
   SL(int a, int b) : i(a), j(b) {} // User-defined constructor OK
};
```

Quizás se pueden ilustrar mejor los dos últimos requisitos con el código. En el ejemplo siguiente, aunque Base es un diseño estándar, `Derived` no es un diseño estándar porque tanto él (la clase más derivada) como `Base` tienen miembros de datos no estáticos:

```cpp
struct Base
{
   int i;
   int j;
};

// std::is_standard_layout<<Derived> == false!
struct Derived : public Base
{
   int x;
   int y;
};
```

En este ejemplo, `Derived` es un diseño estándar porque `Base` no tiene ningún miembro de datos no estáticos:

```cpp
struct Base
{
   void Foo() {}
};

// std::is_standard_layout<<Derived> == true
struct Derived : public Base
{
   int x;
   int y;
};
```

La clase derivada también sería un diseño estándar si `Base` tuviera los miembros de datos y `Derived` solo tuviera funciones miembro.

## <a name="pod-types"></a>Tipos POD

Cuando una clase o estructura es tanto trivial como de diseño estándar, se trata de un tipo POD (Plain Old Data). El diseño de memoria de los tipos POD, por tanto, es contiguo y cada miembro tiene una dirección más alta que el miembro que se declaró antes, por lo que en estos tipos se pueden realizar copias byte a byte y E/S binaria.  Los tipos escalares, como int, también son tipos POD. Los tipos POD que son clases pueden tener solo los tipos POD como miembros de datos no estáticos.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran las diferencias entre los tipos trivial, de diseño estándar y POD:

```cpp
#include <type_traits>
#include <iostream>

using namespace std;

struct B
{
protected:
   virtual void Foo() {}
};

// Neither trivial nor standard-layout
struct A : B
{
      int a;
   int b;
   void Foo() override {} // Virtual function
};

// Trivial but not standard-layout
struct C
   {
      int a;
private:
   int b;   // Different access control
};

// Standard-layout but not trivial
struct D
{
   int a;
   int b;
   D() {} //User-defined constructor
};

struct POD
{
   int a;
   int b;
};

int main()
{
   cout << boolalpha;
   cout << "A is trivial is " << is_trivial<A>() << endl; // false
   cout << "A is standard-layout is " << is_standard_layout<A>() << endl;  // false

   cout << "C is trivial is " << is_trivial<C>() << endl; // true
   cout << "C is standard-layout is " << is_standard_layout<C>() << endl;  // false

   cout << "D is trivial is " << is_trivial<D>() << endl;  // false
   cout << "D is standard-layout is " << is_standard_layout<D>() << endl; // true

   cout << "POD is trivial is " << is_trivial<POD>() << endl; // true
   cout << "POD is standard-layout is " << is_standard_layout<POD>() << endl; // true

   return 0;
}
```

## <a name="literal_types"></a>Tipos literales

Un tipo literal es aquel cuyo diseño se puede determinar en tiempo de compilación. Estos son los tipos literales:

- void
- tipos escalares
- referencias
- Matrices de void, tipos escalares o referencias.
- Una clase que tiene un destructor trivial y uno o varios constructores constexpr que no son constructores de movimiento ni de copias. Además, todos sus miembros de datos no estáticos y sus clases base deben ser tipos literales y no volátiles.

## <a name="see-also"></a>Vea también

[Conceptos básicos](../cpp/basic-concepts-cpp.md)