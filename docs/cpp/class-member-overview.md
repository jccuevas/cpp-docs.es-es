---
title: Información general sobre miembros de clase
ms.date: 11/04/2016
helpviewer_keywords:
- members [C++], types of class members
- members [C++]
- class members [C++], types of
- class members
ms.assetid: 8802cfa9-705d-4f37-acde-245d6838010c
ms.openlocfilehash: 8edfadefdacf94685952d31f2eaf83e8593eaef8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637923"
---
# <a name="class-member-overview"></a>Información general sobre miembros de clase

Una clase o struct está compuesta por sus miembros. Las funciones miembro son las encargadas de realizar el trabajo de la clase a la que pertenecen. El estado que mantienen se almacena en sus miembros de datos. Inicialización de los miembros se realiza mediante constructores y el trabajo de limpieza tales como la liberación de memoria y de los recursos se realiza mediante los destructores. En C++11 y versiones posteriores, los miembros de datos pueden (y normalmente deberían) inicializarse en el punto en el que se declaran.

## <a name="kinds-of-class-members"></a>Tipos de miembros de clase

La lista completa de categorías de miembros es la siguiente:

- [Funciones miembro especiales](special-member-functions.md).

- [Información general de las funciones miembro](overview-of-member-functions.md).

- [Los miembros de datos](static-members-cpp.md) tipos definidos por incluidos tipos integrados y otro usuario.

- Operadores

- [Declaraciones de clase anidada](nested-class-declarations.md) y.)

- [Uniones](unions.md)

- [Enumeraciones](../cpp/enumerations-cpp.md).

- [Campos de bits](../cpp/cpp-bit-fields.md).

- [Amigos](../cpp/friend-cpp.md).

- [Alias y definiciones de tipo](../cpp/aliases-and-typedefs-cpp.md).

    > [!NOTE]
    >  Se incluyen Friends en la lista anterior porque están contenidos en la declaración de clase. Sin embargo, no son miembros de clase verdaderos, porque no están en el ámbito de la clase.

## <a name="example-class-declaration"></a>Ejemplo de declaración de clase

En el siguiente ejemplo se muestra una declaración de clase sencilla:

```cpp
// TestRun.h

class TestRun
{
    // Start member list.

    //The class interface accessible to all callers.
public:
    // Use compiler-generated default constructor:
    TestRun() = default;
    // Don't generate a copy constructor:
    TestRun(const TestRun&) = delete;
    TestRun(std::string name);
    void DoSomething();
    int Calculate(int a, double d);
    virtual ~TestRun();
    enum class State { Active, Suspended };

    // Accessible to this class and derived classes only.
protected:
    virtual void Initialize();
    virtual void Suspend();
    State GetState();

    // Accessible to this class only.
private:
    // Default brace-initialization of instance members:
    State _state{ State::Suspended };
    std::string _testName{ "" };
    int _index{ 0 };

    // Non-const static member:
    static int _instances;
    // End member list.
};

// Define and initialize static member.
int TestRun::_instances{ 0 };
```

## <a name="member-accessibility"></a>Accesibilidad de miembros

Los miembros de una clase se declaran en la lista de miembros. La lista de miembros de una clase se puede dividir en cualquier número de **privada**, **protegido** y **pública** secciones mediante palabras clave conocidas como especificadores de acceso.  Dos puntos **:** debe seguir el especificador de acceso.  Estas secciones no necesitan ser contiguas, es decir, cualquiera de estas palabras clave puede aparecer varias veces en la lista de miembros.  La palabra clave designa el acceso de todos los miembros hacia arriba hasta el especificador de acceso siguiente o la llave de cierre. Para obtener más información, consulte [Control de acceso de miembro (C++)](../cpp/member-access-control-cpp.md).

## <a name="static-members"></a>Miembros estáticos

Un miembro de datos se puede declarar como static, lo que significa que todos los objetos de la clase tienen acceso a la misma copia del mismo. Una función miembro puede declararse como static, en cuyo caso solo puede acceder a los miembros de datos estáticos de la clase (y no tiene ningún *esto* puntero). Para obtener más información, consulte [miembros de datos estáticos](../cpp/static-members-cpp.md).

## <a name="special-member-functions"></a>Funciones miembro especiales

Las funciones miembro especiales son funciones que el compilador proporciona automáticamente si no las especifica en el código fuente.

1. Constructor predeterminado

1. Constructor de copias

1. **(C ++ 11)**  Constructor de movimiento

1. Operador de asignación de copia

1. **(C ++ 11)**  Operador de asignación de movimiento

1. Destructor

Para obtener más información, consulte [funciones miembro especiales](../cpp/special-member-functions.md).

## <a name="memberwise-initialization"></a>Inicialización miembro a miembro

En C++11 y versiones posteriores, los declaradores de miembros no estáticos pueden contener inicializadores.

```cpp
class CanInit
{
public:
    long num {7};       // OK in C++11
    int k = 9;          // OK in C++11
    static int i = 9; // Error: must be defined and initialized
                      // outside of class declaration.

    // initializes num to 7 and k to 9
    CanInit(){}

    // overwrites original initialized value of num:
    CanInit(int val) : num(val) {}
};
int main()
{
}
```

Si un miembro recibe un valor en un constructor, ese valor sobrescribe el valor con el que se inicializó el miembro en el punto de declaración.

Solo hay una copia compartida de los miembros de datos estáticos para todos los objetos de un tipo de clase determinado. Los miembros de datos estáticos se deben definir y se pueden inicializar en el ámbito de archivo. (Para obtener más información acerca de los miembros de datos estáticos, vea [miembros de datos estáticos](../cpp/static-members-cpp.md).) En el ejemplo siguiente se muestra cómo se realizan estas inicializaciones:

```cpp
// class_members2.cpp
class CanInit2
{
public:
    CanInit2() {} // Initializes num to 7 when new objects of type
                 //  CanInit are created.
    long     num {7};
    static int i;
    static int j;
};

// At file scope:

// i is defined at file scope and initialized to 15.
// The initializer is evaluated in the scope of CanInit.
int CanInit2::i = 15;

// The right side of the initializer is in the scope
// of the object being initialized
int CanInit2::j = i;
```

> [!NOTE]
>  El nombre de clase, `CanInit2`, debe preceder a `i` para especificar que el `i` definido es un miembro de la clase `CanInit2`.

## <a name="see-also"></a>Vea también

[Clases y structs](../cpp/classes-and-structs-cpp.md)