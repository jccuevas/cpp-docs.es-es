---
title: Trivial, diseño estándar, POD y tipos literales | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.topic: language-reference
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9bb4a84b42cadeb2e076548a220725f1e867fe9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099724"
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>Trivial, diseño estándar, POD y tipos de literales

El término *diseño* hace referencia a cómo se organizan los miembros de un objeto de clase, struct o union en la memoria. En algunos casos, el diseño está bien definido por la especificación del lenguaje. Pero cuando una clase o struct contiene ciertas características del lenguaje C++, como clases base virtuales, funciones virtuales, los miembros con control de acceso diferente, el compilador es libre de elegir un diseño. Ese diseño puede variar dependiendo de qué optimizaciones se realizan y en muchos casos, objeto no puede ocupar incluso un área contigua de memoria. Por ejemplo, si una clase tiene funciones virtuales, todas las instancias de esa clase pueden compartir una tabla de función virtual único. Estos tipos son muy útiles, por supuesto, pero también tienen limitaciones. Porque no está definido el diseño no se pueden pasar a los programas escritos en otros lenguajes, como C, ya que pueden no contiguas copiarse o no confiable con funciones de bajo nivel rápido como `memcopy` o serializar a través de una red.

Para habilitar los compiladores, así como los programas de C++ y metaprograms razonar sobre la idoneidad de un tipo dado para las operaciones que dependen de un diseño de memoria específica, C ++ 14 presentó tres categorías de clases simple y estructuras: *trivial*, *diseño estándar*, y *POD* o datos antiguos. La biblioteca estándar tiene las plantillas de función `is_trivial<T>`, `is_standard_layout<T>` y `is_pod<T>` que determinan si un tipo determinado pertenece a una categoría determinada.

## <a name="trivial-types"></a>Tipos triviales

Cuando una clase o struct de C++ ha proporcionado por el compilador o explícitamente su valor predeterminado, las funciones miembro especiales es un tipo trivial. Ocupa un área de memoria contiguas. Puede tener miembros con los especificadores de acceso diferentes. En C++, el compilador es libre de elegir cómo ordenar a miembros en esta situación. Por lo tanto, puede memcopy dichos objetos pero confiable no puede consumir desde un programa C. Un tipo trivial T puede copiar en una matriz de char o char sin signo y copiado en una variable T. Tenga en cuenta que debido a los requisitos de alineación, podría haber bytes de relleno entre los miembros de tipo.

Los tipos triviales tienen un constructor predeterminado trivial, constructor de copias trivial, operador de asignación de copia trivial y un destructor trivial. En cada caso, *trivial* significa que el operador/constructor/destructor no está proporcionado por el usuario y pertenece a una clase que tiene

- No hay funciones virtuales o las clases base virtuales

- ninguna clase base con un correspondiente no trivial constructor o operador/destructor

- ningún miembro de datos de tipo de clase con un correspondiente no trivial constructor o operador/destructor

Los ejemplos siguientes muestran los tipos triviales. En Trivial2, la presencia de la `Trivial2(int a, int b)` constructor requiere que proporcione un constructor predeterminado. Para que el tipo se consideran triviales, debe explícitamente ese constructor predeterminado.

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

Cuando una clase o estructura no tiene ciertas características del lenguaje C++, como funciones virtuales que no se encuentran en el lenguaje C, y todos los miembros tienen el mismo control de acceso, es un tipo de diseño estándar. Es capaz de memcopy y suficientemente definido por el diseño que pueden utilizarse los programas de C. Tipos de diseño estándar pueden tener funciones miembro especiales definidas por el usuario. Además, los tipos de diseño estándar tienen estas características:

- No hay funciones virtuales o las clases base virtuales

- todos los miembros de datos no estáticos tienen el mismo control de acceso

- todos los miembros no estáticos del tipo de clase son diseño estándar

- clases base son diseño estándar

- no tiene ninguna clase base del mismo tipo como el primer miembro de datos no estáticos.

- cumple alguna de estas condiciones:

  - ningún miembro de datos no estáticos en la clase más derivada y no más de una clase base con miembros de datos no estáticos, o

  - no tiene ninguna clase base con miembros de datos no estáticos

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

Quizás se pueden ilustrar mejor los dos últimos requisitos con el código. En el ejemplo siguiente, aunque Base es diseño estándar, `Derived` no es un diseño estándar porque ambas (la clase más derivada) de TI y `Base` tener miembros de datos no estáticos:

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

En este ejemplo `Derived` es diseño estándar porque `Base` no tiene ningún miembro de datos no estáticos:

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

Derivado también sería diseño estándar si `Base` tenía los miembros de datos y `Derived` tenía solo las funciones de miembro.

## <a name="pod-types"></a>Tipos POD

Cuando una clase o struct es trivial y diseño estándar, es un tipo POD (Plain Old Data). El diseño de memoria de los tipos POD, por tanto, es contiguo y cada miembro tiene una dirección más alta que el miembro que se declaró antes de que, por lo que copia el byte a byte y la E/S binaria pueden realizarse en estos tipos.  Tipos escalares, como int también son tipos POD. Tipos POD que son clases pueden tener solo los tipos POD como miembros de datos no estáticos.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra las diferencias entre el diseño estándar trivial, y tipos POD:

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

## <a name="literal_types"></a> Tipos literales

Un tipo literal es aquel cuyo diseño se puede determinar en tiempo de compilación. Estos son los tipos literales:

- void
- tipos escalares
- referencias
- Matrices de void, tipos escalares o referencias.
- Una clase que tiene un destructor trivial y uno o varios constructores constexpr que no son constructores de movimiento ni de copias. Además, todos sus miembros de datos no estáticos y sus clases base deben ser tipos literales y no volátiles.

## <a name="see-also"></a>Vea también

[Conceptos básicos](../cpp/basic-concepts-cpp.md)