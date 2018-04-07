---
title: Trivial, diseño estándar y POD, tipos literales | Documentos de Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
caps.latest.revision: 13
manager: ghogen
ms.openlocfilehash: e977449c1c31b0b3f83c04b9b52a1a0bacb37f31
ms.sourcegitcommit: d9ee6f777974d031570f4260c9581ea2c81ad875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2018
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>Trivial, diseño estándar y POD, tipos literales

El término *diseño* hace referencia a cómo se organizan los miembros de un objeto de clase, struct o union en la memoria. En algunos casos, el diseño está bien definido por la especificación del lenguaje. Pero cuando una clase o struct contiene determinadas características del lenguaje C++, como clases base virtuales, funciones virtuales, los miembros con control de acceso diferente, el compilador es libre para elegir un diseño. Ese diseño puede variar dependiendo de qué optimizaciones se realizan y en muchos casos, objeto no puedan ocupar incluso un área contigua de memoria. Por ejemplo, si una clase tiene funciones virtuales, todas las instancias de esa clase pueden compartir una tabla única función virtual. Estos tipos son muy útiles, por supuesto, pero también tienen limitaciones. Puesto que está definido el diseño no se pueden pasar a los programas escritos en otros lenguajes, como C, ya que pueden no contiguas copiarse o no confiable con funciones de bajo nivel rápido como `memcopy` o serializar a través de una red.

 Para habilitar metaprograms razonar sobre la idoneidad de un determinado tipo de operaciones que dependen de un diseño de memoria específica, así como los programas de C++ y los compiladores, C ++ 14 introdujo tres categorías de simples clases y structs: *trivial*, *diseño estándar*, y *POD* o Plain Old Data. La biblioteca estándar tiene las plantillas de función `is_trivial<T>`, `is_standard_layout<T>` y `is_pod<T>` que determinan si un tipo determinado pertenece a una categoría determinada.

## <a name="trivial-types"></a>Tipos triviales

 Cuando una clase o struct de C++ ha proporcionado por el compilador o explícitamente su valor predeterminado de las funciones miembro especiales, es un tipo trivial. Ocupa un área de memoria contigua. Puede tener miembros con especificadores de acceso diferentes. En C++, el compilador es libre de elegir cómo ordenar a miembros en esta situación. Por lo tanto, puede memcopy dichos objetos pero confiable no se puede utilizar desde un programa de C. Un tipo trivial T puede copiarse en una matriz de char o char sin signo y copiado correctamente en una variable de T. Tenga en cuenta que debido a los requisitos de alineación, podría haber bytes de relleno entre los miembros de tipo.

 Los tipos triviales tienen un constructor predeterminado trivial, constructor de copias trivial, operador de asignación de copias trivial y un destructor trivial. En cada caso, *trivial* significa que el operador/constructor/destructor no es proporcionado por el usuario y pertenece a una clase que tiene

- ninguna función virtual o las clases base virtuales

- ninguna clase base con un correspondiente no trivial constructor/operador/destructor

- ningún miembro de datos del tipo de clase con un correspondiente no trivial constructor/operador/destructor

Los ejemplos siguientes muestran los tipos triviales. En Trivial2, la presencia de la `Trivial2(int a, int b)` constructor requiere que proporcione un constructor predeterminado. Para que el tipo que se consideran triviales, debe explícitamente que un constructor predeterminado.

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

 Cuando una clase o struct no contiene determinadas características del lenguaje C++, como funciones virtuales que no se encuentran en el lenguaje C, y todos los miembros tienen el mismo control de acceso, es un tipo de diseño estándar. Es capaz de memcopy y lo suficientemente definido por el diseño que puede ser utilizado por los programas de C. Tipos de diseño estándar pueden tener funciones miembro especiales definidas por el usuario. Además, los tipos de diseño estándar tienen estas características:

- ninguna función virtual o clases base virtuales

- todos los miembros de datos no estáticos tienen el mismo control de acceso

- todos los miembros no estáticos de tipo de clase son diseño estándar

- las clases base son diseño estándar

- no tiene ninguna clase base del mismo tipo como el primer miembro de datos no estáticos.

- cumple alguna de estas condiciones:

  - ningún miembro de datos no estáticos de la clase más derivada y no más de una clase base con miembros de datos no estáticos, o

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

 Los dos últimos requisitos quizás se pueden ilustrar mejor con código. En el ejemplo siguiente, aunque Base es diseño estándar, `Derived` no es un diseño estándar porque ambos TI (la clase más derivada) y `Base` tener miembros de datos no estáticos:

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

 Derivada también sería diseño estándar si `Base` tenía los miembros de datos y `Derived` tenía sólo las funciones de miembro.

## <a name="pod-types"></a>Tipos POD

 Cuando una clase o struct es trivial y diseño estándar, es un tipo POD (Plain Old Data). El diseño de memoria de los tipos POD, por tanto, es contiguo y cada miembro tiene una dirección más alta que el miembro que se declaró antes de que, para que la copia de byte a byte y la E/S binario pueden realizarse en estos tipos.  Tipos escalares como int también son tipos POD. Tipos POD que son clases pueden tener solo los tipos POD como miembros de datos no estáticos.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra las diferencias entre el diseño estándar trivial, y los tipos POD:

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