---
title: Error del compilador C2280
ms.date: 04/25/2017
f1_keywords:
- C2280
helpviewer_keywords:
- C2280
ms.assetid: e6c5b1fb-2b9b-4554-8ff9-775eeb37161b
ms.openlocfilehash: e1ec032878fefdc1992605df5ee1aa13c673d4cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388909"
---
# <a name="compiler-error-c2280"></a>Error del compilador C2280

'*declaración*': intentando hacer referencia a una función eliminada

El compilador detectó un intento para hacer referencia a un `deleted` función. Este error puede deberse a una llamada a una función miembro que se ha marcado explícitamente como `= deleted` en el código fuente. Este error también puede deberse a una llamada a una función miembro especial implícito de una estructura o clase que se declara automáticamente y se marca como `deleted` por el compilador. Para obtener más información acerca de cuándo el compilador genera automáticamente `default` o `deleted` funciones miembro especiales, consulte [funciones miembro especiales](../../cpp/special-member-functions.md).

## <a name="example-explicitly-deleted-functions"></a>Ejemplo: Funciones eliminadas explícitamente

Una llamada a un explícitamente `deleted` función provoca este error. Una forma explícita `deleted` función miembro implica que la clase o estructura se ha diseñado específicamente para impedir su uso, por lo tanto, para corregir este problema, debe cambiar el código para evitar esta situación.

```cpp
// C2280_explicit.cpp
// compile with: cl /c /W4 C2280_explicit.cpp
struct A {
    A();
    A(int) = delete;
};

struct B {
    A a1;
    A a2 = A(3); // C2280, calls deleted A::A(int)
    // To fix, remove the call to A(int)
};

void f() {
    B b;    // calls implicit B::B(void)
}
```

## <a name="example-uninitialized-data-members"></a>Ejemplo: Miembros de datos sin inicializar

Un miembro de datos de tipo de referencia sin inicializar o `const` miembro de datos hace que el compilador declara implícitamente un `deleted` constructor predeterminado. Para corregir este problema, inicialice al miembro de datos cuando se declara.

```cpp
// C2280_uninit.cpp
// compile with: cl /c C2280_uninit.cpp
struct A {
    const int i; // uninitialized const-qualified data
    // members or reference type data members cause
    // the implicit default constructor to be deleted.
    // To fix, initialize the value in the declaration:
    // const int i = 42;
} a;    // C2280
```

## <a name="example-reference-and-const-data-members"></a>Ejemplo: Referencia y los miembros de datos const

Un `const` o miembro de datos de referencia tipo hace que el compilador declarar un `deleted` operador de asignación de copia. Una vez inicializado, estos miembros no pueden asignarse a, por lo que una simple copia o movimiento no puede funcionar. Para corregir este problema, se recomienda que cambiar la lógica para quitar las operaciones de asignación que producen el error.

```cpp
// C2280_ref.cpp
// compile with: cl /c C2280_ref.cpp
extern int k;
struct A {
    A();
    int& ri = k; // a const or reference data member causes
    // implicit copy assignment operator to be deleted.
};

void f() {
    A a1, a2;
    // To fix, consider removing this assignment.
    a2 = a1;    // C2280
}
```

## <a name="example-movable-deletes-implicit-copy"></a>Ejemplo: Copia implícita eliminaciones movible

Si una clase declara un constructor de movimiento o un operador de asignación de movimiento, pero no declara explícitamente un constructor de copias, el compilador implícitamente declara un constructor de copias y que se define como `deleted`. De forma similar, si una clase declara un constructor de movimiento o un operador de asignación de movimiento, pero no declara explícitamente un operador de asignación de copia, el compilador implícitamente declara un operador de asignación de copia y lo define como `deleted`. Para corregir este problema, debe declarar explícitamente estos miembros.

Cuando aparezca el error C2280 en conexión con un `unique_ptr`, es casi seguro porque está intentando invocar su constructor de copias, que es un `deleted` función. Por diseño, un `unique_ptr` no puede copiarse. Utilice un constructor de movimiento para transferir la propiedad en su lugar.

```cpp
// C2280_move.cpp
// compile with: cl /c C2280_move.cpp
class base
{
public:
    base();
    ~base();
    base(base&&);
    // Move constructor causes copy constructor to be
    // implicitly declared as deleted. To fix this
    // issue, you can explicitly declare a copy constructor:
    // base(base&);
    // If you want the compiler default version, do this:
    // base(base&) = default;
};

void copy(base *p)
{
    base b{*p};  // C2280
}
```

## <a name="example-variant-and-volatile-members"></a>Ejemplo: Miembros de variantes y volatile

Las versiones del compilador antes de Visual Studio 2015 Update 2 estaban constructores y destructores para las uniones anónimas predeterminados generados y no conformes. Estas ahora se declaran implícitamente como `deleted`. Esas versiones también permitían la definición implícita no cumple las especificaciones de `default` copiar y mover los constructores y `default` copiar y mover los operadores de asignación en las clases y estructuras que tienen `volatile` variables de miembro. El compilador ahora considera tener constructores no triviales y operadores de asignación y no genera `default` implementaciones. Cuando esta clase es un miembro de una unión o una unión anónima dentro de una clase, los constructores de copia y movimiento y operadores de asignación de copia y movimiento de la unión o clase se definen implícitamente como `deleted`. Para corregir este problema, debe declarar explícitamente las funciones miembro especiales necesarios.

```cpp
// C2280_variant.cpp
// compile with: cl /c C2280_variant.cpp
struct A {
    A() = default;
    A(const A&);
};

struct B {
    union {
        A a;
        int i;
    };
    // To fix this issue, declare the required
    // special member functions:
    // B();
    // B(const B& b);
};

int main() {
    B b1;
    B b2(b1);  // C2280
}
```

## <a name="example-indirect-base-members-deleted"></a>Ejemplo: Miembros base indirectos eliminados

Versiones del compilador antes de Visual Studio 2015 Update 2 eran no conforme y permiten una clase derivada para llamar a funciones de derivadas indirectamente miembro especial `private virtual` clases base. El compilador ahora emite el error del compilador C2280 cuando se realiza una llamada de este tipo.

En este ejemplo, la clase `top` deriva indirectamente de privada virtual `base`. En el código que cumplen las especificaciones, esto hace que los miembros de `base` inaccesible para `top`; un objeto de tipo `top` no se predeterminada construir o destruir. Para corregir este problema en el código que confiar en el comportamiento del compilador anterior, cambie la clase intermedia para usar `protected virtual` derivación o cambiar la `top` clase utiliza la derivación directa:

```cpp
// C2280_indirect.cpp
// compile with: cl /c C2280_indirect.cpp
class base
{
protected:
    base();
    ~base();
};

class middle : private virtual base {};
// Possible fix: Replace line above with:
// class middle : protected virtual base {};
class top : public virtual middle {};    // C4594, C4624
// Another possible fix: use direct derivation:
// class top : public virtual middle, private virtual base {};

void destroy(top *p)
{
    delete p;  // C2280
}
```
