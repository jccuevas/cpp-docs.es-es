---
title: declaración using
ms.date: 11/04/2016
helpviewer_keywords:
- using declaration
- declarations [C++], using-declaration
- namespaces [C++], unqualified names in
- using keyword [C++]
ms.assetid: 4184e2b1-3adc-408e-b5f3-0b3f8b554723
ms.openlocfilehash: d762ea36e83d2384b7bb50c2914f6a634c134d15
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187848"
---
# <a name="using-declaration"></a>declaración using

La declaración **using** introduce un nombre en la región declarativa en la que aparece la declaración using.

## <a name="syntax"></a>Sintaxis

```
using [typename] nested-name-specifier unqualified-id ;
using declarator-list ;
```

### <a name="parameters"></a>Parámetros

*Nested-Name-Specifier* Secuencia de nombres de espacio de nombres, clase o enumeración y operadores de resolución de ámbito (::), terminada por un operador de resolución de ámbito. Se puede usar un solo operador de resolución de ámbito para introducir un nombre del espacio de nombres global. La palabra clave **TypeName** es opcional y se puede usar para resolver nombres dependientes cuando se introducen en una plantilla de clase de una clase base.

*inqualified-ID* Una expresión de ID. incompleta, que puede ser un identificador, un nombre de operador sobrecargado, un nombre de función de conversión o un operador literal definido por el usuario, un nombre de destructor de clase o un nombre de plantilla y una lista de argumentos.

*lista de declaradores* Lista separada por comas de [**TypeName**] *declaradores* de nombre-de- *especificador Nested-Name-Specifier* , seguido opcionalmente por puntos suspensivos.

## <a name="remarks"></a>Observaciones

Una declaración Using introduce un nombre no completo como sinónimo de una entidad declarada en otro lugar. Permite usar un nombre único de un espacio de nombres específico sin la calificación explícita en la región de declaración en la que aparece. Esto contrasta con la [directiva using](../cpp/namespaces-cpp.md#using_directives), que permite usar *todos* los nombres de un espacio de nombres sin calificación. La palabra clave **using** también se utiliza para los [alias de tipo](../cpp/aliases-and-typedefs-cpp.md).

## <a name="example"></a>Ejemplo

Se puede utilizar una declaración using en una definición de clase.

```cpp
// using_declaration1.cpp
#include <stdio.h>
class B {
public:
   void f(char) {
      printf_s("In B::f()\n");
   }

   void g(char) {
      printf_s("In B::g()\n");
   }
};

class D : B {
public:
   using B::f;    // B::f(char) is now visible as D::f(char)
   using B::g;    // B::g(char) is now visible as D::g(char)
   void f(int) {
      printf_s("In D::f()\n");
      f('c');     // Invokes B::f(char) instead of recursing
   }

   void g(int) {
      printf_s("In D::g()\n");
      g('c');     // Invokes B::g(char) instead of recursing
   }
};

int main() {
   D myD;
   myD.f(1);
   myD.g('a');
}
```

```Output
In D::f()
In B::f()
In B::g()
```

## <a name="example"></a>Ejemplo

Cuando se utiliza para declarar un miembro, una declaración using debe hacer referencia a un miembro de una clase base.

```cpp
// using_declaration2.cpp
#include <stdio.h>

class B {
public:
   void f(char) {
      printf_s("In B::f()\n");
   }

   void g(char) {
      printf_s("In B::g()\n");
   }
};

class C {
public:
   int g();
};

class D2 : public B {
public:
   using B::f;   // ok: B is a base of D2
   // using C::g;   // error: C isn't a base of D2
};

int main() {
   D2 MyD2;
   MyD2.f('a');
}
```

```Output
In B::f()
```

## <a name="example"></a>Ejemplo

Se puede hacer referencia a los miembros declarados mediante una declaración Using mediante la calificación explícita. El prefijo `::` hace referencia al espacio de nombres global.

```cpp
// using_declaration3.cpp
#include <stdio.h>

void f() {
   printf_s("In f\n");
}

namespace A {
   void g() {
      printf_s("In A::g\n");
   }
}

namespace X {
   using ::f;   // global f is also visible as X::f
   using A::g;   // A's g is now visible as X::g
}

void h() {
   printf_s("In h\n");
   X::f();   // calls ::f
   X::g();   // calls A::g
}

int main() {
   h();
}
```

```Output
In h
In f
In A::g
```

## <a name="example"></a>Ejemplo

Cuando se crea una declaración using, el sinónimo creado por la declaración solo hace referencia a las definiciones que son válidas en el lugar de la declaración using. Las definiciones que se agregan a un espacio de nombres después de la declaración using no son sinónimos válidos.

Un nombre definido por una declaración **using** es un alias para su nombre original. No afecta al tipo, la vinculación u otros atributos de la declaración original.

```cpp
// post_declaration_namespace_additions.cpp
// compile with: /c
namespace A {
   void f(int) {}
}

using A::f;   // f is a synonym for A::f(int) only

namespace A {
   void f(char) {}
}

void f() {
   f('a');   // refers to A::f(int), even though A::f(char) exists
}

void b() {
   using A::f;   // refers to A::f(int) AND A::f(char)
   f('a');   // calls A::f(char);
}
```

## <a name="example"></a>Ejemplo

En cuanto a las funciones de espacios de nombres, si se proporciona un conjunto de declaraciones locales y declaraciones using para un único nombre en una región declarativa, todas ellas deben hacer referencia a la misma entidad o todas ellas deben hacer referencia a funciones.

```cpp
// functions_in_namespaces1.cpp
// C2874 expected
namespace B {
    int i;
    void f(int);
    void f(double);
}

void g() {
    int i;
    using B::i;   // error: i declared twice
    void f(char);
    using B::f;   // ok: each f is a function
}
```

En el ejemplo anterior, la instrucción `using B::i` hace que se declare un segundo `int i` en la función `g()`. La instrucción `using B::f` no entra en conflicto con la función `f(char)` porque los nombres de función introducidos por `B::f` tienen distintos tipos de parámetro.

## <a name="example"></a>Ejemplo

Una declaración de función local no puede tener el mismo nombre y tipo que una función introducida mediante una declaración using. Por ejemplo:

```cpp
// functions_in_namespaces2.cpp
// C2668 expected
namespace B {
    void f(int);
    void f(double);
}

namespace C {
    void f(int);
    void f(double);
    void f(char);
}

void h() {
    using B::f;          // introduces B::f(int) and B::f(double)
    using C::f;          // C::f(int), C::f(double), and C::f(char)
    f('h');              // calls C::f(char)
    f(1);                // C2668 ambiguous: B::f(int) or C::f(int)?
    void f(int);         // C2883 conflicts with B::f(int) and C::f(int)
}
```

## <a name="example"></a>Ejemplo

Con respecto a la herencia, cuando una declaración using introduce un nombre de una clase base en el ámbito de una clase derivada, las funciones miembro de la clase derivada invalidan las funciones de miembro virtual que tienen los mismos nombres y tipos de argumento en la clase base.

```cpp
// using_declaration_inheritance1.cpp
#include <stdio.h>
struct B {
   virtual void f(int) {
      printf_s("In B::f(int)\n");
   }

   virtual void f(char) {
      printf_s("In B::f(char)\n");
   }

   void g(int) {
      printf_s("In B::g\n");
   }

   void h(int);
};

struct D : B {
   using B::f;
   void f(int) {   // ok: D::f(int) overrides B::f(int)
      printf_s("In D::f(int)\n");
   }

   using B::g;
   void g(char) {   // ok: there is no B::g(char)
      printf_s("In D::g(char)\n");
   }

   using B::h;
   void h(int) {}   // Note: D::h(int) hides non-virtual B::h(int)
};

void f(D* pd) {
   pd->f(1);     // calls D::f(int)
   pd->f('a');   // calls B::f(char)
   pd->g(1);     // calls B::g(int)
   pd->g('a');   // calls D::g(char)
}

int main() {
   D * myd = new D();
   f(myd);
}
```

```Output
In D::f(int)
In B::f(char)
In B::g
In D::g(char)
```

## <a name="example"></a>Ejemplo

Todas las instancias de un nombre mencionado en una declaración using deben ser accesibles. En concreto, si una clase derivada utiliza una declaración using para tener acceso a un miembro de una clase base, el nombre de miembro debe ser accesible. Si el nombre es el de una función miembro sobrecargada, todas las funciones enumeradas deben ser accesibles.

Para obtener más información sobre la accesibilidad de los miembros, vea [member-access control](../cpp/member-access-control-cpp.md).

```cpp
// using_declaration_inheritance2.cpp
// C2876 expected
class A {
private:
   void f(char);
public:
   void f(int);
protected:
   void g();
};

class B : public A {
   using A::f;   // C2876: A::f(char) is inaccessible
public:
   using A::g;   // B::g is a public synonym for A::g
};
```

## <a name="see-also"></a>Consulte también

[Espacios de nombres](../cpp/namespaces-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
