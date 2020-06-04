---
title: Control de acceso a miembros (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- access control [C++]
- member access [C++]
- member-access control [C++]
ms.assetid: 2d596bca-56ad-4277-94e1-ce3db45fa14a
ms.openlocfilehash: e8f62e82ebb7fcc18be5ac7d203df0fb46c9b635
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369860"
---
# <a name="member-access-control-c"></a>Control de acceso a miembros (C++)

Los controles de acceso permiten separar la interfaz [pública](../cpp/public-cpp.md) de una clase de los detalles de implementación [privada](../cpp/private-cpp.md) y los miembros [protegidos](../cpp/protected-cpp.md) que solo se usan en las clases derivadas. El especificador de acceso se aplica a todos los miembros declarados después de él hasta que se encuentra el especificador de acceso siguiente.

```cpp
class Point
{
public:
    Point( int, int ) // Declare public constructor.;
    Point();// Declare public default constructor.
    int &x( int ); // Declare public accessor.
    int &y( int ); // Declare public accessor.

private:                 // Declare private state variables.
    int _x;
    int _y;

protected:      // Declare protected function for derived classes only.
    Point ToWindowCoords();
};
```

El acceso predeterminado es **privado** en una clase y **public** en una estructura o unión. Los especificadores de acceso de una clase se pueden usar cualquier número de veces en cualquier orden. La asignación de almacenamiento para objetos de tipos de clase depende de la implementación, pero se garantiza que a los miembros se les asignen direcciones de memoria sucesivamente superiores entre los especificadores de acceso.

## <a name="member-access-control"></a>Control de acceso a miembros

|Tipo de Acceso|Significado|
|--------------------|-------------|
|[Privado](../cpp/private-cpp.md)|Los miembros de clase declarados como **privados** solo pueden ser utilizados por funciones miembro y amigos (clases o funciones) de la clase.|
|[protected](../cpp/protected-cpp.md)|Los miembros de clase declarados como **protegidos** pueden ser utilizados por funciones miembro y amigos (clases o funciones) de la clase. Además, las clases derivadas de la clase también pueden usarlos.|
|[público](../cpp/public-cpp.md)|Los miembros de clase declarados como **públicos** pueden ser utilizados por cualquier función.|

El control de acceso impiden usar objetos de manera diferente a la que están destinados. Esta protección se pierde cuando se realizan conversiones de tipos explícitas.

> [!NOTE]
> El control de acceso también es aplicable a todos los nombres: funciones miembro, datos de miembro, clases anidadas y enumeradores.

## <a name="access-control-in-derived-classes"></a>Control de acceso en clases derivadas

Dos factores controlan los miembros de una clase base que están accesibles en una clase derivada; estos mismos factores controlan el acceso a los miembros heredados en la clase derivada:

- Si la clase derivada declara la clase base mediante el especificador de acceso **público.**

- Que el acceso al miembro esté en la clase base.

En la tabla siguiente se muestra la interacción entre estos factores y cómo se determina el acceso a miembros de clase base.

### <a name="member-access-in-base-class"></a>Acceso a miembros de clase base

|private|protected|Público|
|-------------|---------------|------------|
|Siempre inaccesible independientemente del acceso de derivación|Privado en la clase derivada si se utiliza la derivación privada|Privado en la clase derivada si se utiliza la derivación privada|
||Protegido en la clase derivada si se utiliza la derivación protegida|Protegido en la clase derivada si se utiliza la derivación protegida|
||Protegido en la clase derivada si se utiliza la derivación pública|Público en la clase derivada si se utiliza la derivación pública|

Esto se ilustra en el ejemplo siguiente:

```cpp
// access_specifiers_for_base_classes.cpp
class BaseClass
{
public:
    int PublicFunc(); // Declare a public member.
protected:
    int ProtectedFunc(); // Declare a protected member.
private:
    int PrivateFunc(); // Declare a private member.
};

// Declare two classes derived from BaseClass.
class DerivedClass1 : public BaseClass
{
    void foo()
    {
        PublicFunc();
        ProtectedFunc();
        PrivateFunc(); // function is inaccessible
    }
};

class DerivedClass2 : private BaseClass
{
    void foo()
    {
        PublicFunc();
        ProtectedFunc();
        PrivateFunc(); // function is inaccessible
    }
};

int main()
{
    DerivedClass1 derived_class1;
    DerivedClass2 derived_class2;
    derived_class1.PublicFunc();
    derived_class2.PublicFunc(); // function is inaccessible
}
```

En `DerivedClass1`, la función miembro `PublicFunc` es un miembro público y `ProtectedFunc` es un miembro protegido porque `BaseClass` es una clase base pública. `PrivateFunc` es privado para `BaseClass`, y es inaccesible en cualquiera de sus clases derivadas.

En `DerivedClass2`, las funciones `PublicFunc` y `ProtectedFunc` se consideran miembros privados porque `BaseClass` es una clase base privada. De nuevo, `PrivateFunc` es privado para `BaseClass`, y es inaccesible en cualquiera de sus clases derivadas.

Puede declarar una clase derivada sin un especificador de acceso de clase base. En tal caso, la derivación se considera privada si la declaración de clase derivada utiliza la palabra clave **class.** La derivación se considera pública si la declaración de clase derivada utiliza la palabra clave **struct.** Por ejemplo, el código siguiente:

```cpp
class Derived : Base
...
```

equivale a:

```cpp
class Derived : private Base
...
```

De igual forma, el código siguiente:

```cpp
struct Derived : Base
...
```

equivale a:

```cpp
struct Derived : public Base
...
```

Tenga en cuenta que los miembros declarados como que tienen acceso privado no son accesibles para funciones o clases derivadas a menos que esas funciones o clases se declaren mediante la declaración **friend** en la clase base.

Un tipo **de unión** no puede tener una clase base.

> [!NOTE]
> Al especificar una clase base privada, es recomendable utilizar explícitamente la palabra clave **private** para que los usuarios de la clase derivada comprendan el acceso de miembro.

## <a name="access-control-and-static-members"></a>Control de acceso y miembros estáticos

Cuando se especifica una clase base como **privada,** solo afecta a los miembros no estáticos. Los miembros estáticos públicos siguen siendo accesibles en las clases derivadas. Sin embargo, el acceso a los miembros de la clase base mediante el uso de punteros, referencias u objetos puede requerir una conversión en la que se aplica de nuevo el control de acceso de tiempo. Considere el ejemplo siguiente:

```cpp
// access_control.cpp
class Base
{
public:
    int Print();             // Nonstatic member.
    static int CountOf();    // Static member.
};

// Derived1 declares Base as a private base class.
class Derived1 : private Base
{
};
// Derived2 declares Derived1 as a public base class.
class Derived2 : public Derived1
{
    int ShowCount();    // Nonstatic member.
};
// Define ShowCount function for Derived2.
int Derived2::ShowCount()
{
   // Call static member function CountOf explicitly.
    int cCount = Base::CountOf();     // OK.

   // Call static member function CountOf using pointer.
    cCount = this->CountOf();  // C2247. Conversion of
                               //  Derived2 * to Base * not
                               //  permitted.
    return cCount;
}
```

En el código anterior, el control de acceso prohíbe la conversión de un puntero a `Derived2` en un puntero a `Base`. El puntero **this** es `Derived2 *`implícitamente de tipo . Para seleccionar `CountOf` la función, **debe** convertirse al tipo `Base *`. Este tipo de conversión no está permitido porque `Base` es una clase base indirecta privada a `Derived2`. La conversión a un tipo de clase base privada solo es aceptable para punteros a clases derivadas inmediatas. Por lo tanto, los punteros de tipo `Derived1 *` pueden convertirse al tipo `Base *`.

Observe que la llamada explícita a la función `CountOf`, sin utilizar un puntero, una referencia o un objeto para seleccionarla, no implica ninguna conversión. Por lo tanto, se permite la llamada.

Los miembros y objetos friend de una clase derivada, `T`, pueden convertir un puntero a `T` en un puntero a una clase base directa privada de `T`.

## <a name="access-to-virtual-functions"></a>Acceso a funciones virtuales

El control de acceso aplicado a las funciones [virtuales](../cpp/virtual-cpp.md) viene determinado por el tipo utilizado para realizar la llamada de función. El reemplazo de las declaraciones de la función no afecta al control de acceso para un tipo determinado. Por ejemplo:

```cpp
// access_to_virtual_functions.cpp
class VFuncBase
{
public:
    virtual int GetState() { return _state; }
protected:
    int _state;
};

class VFuncDerived : public VFuncBase
{
private:
    int GetState() { return _state; }
};

int main()
{
   VFuncDerived vfd;             // Object of derived type.
   VFuncBase *pvfb = &vfd;       // Pointer to base type.
   VFuncDerived *pvfd = &vfd;    // Pointer to derived type.
   int State;

   State = pvfb->GetState();     // GetState is public.
   State = pvfd->GetState();     // C2248 error expected; GetState is private;
}
```

En el ejemplo anterior, al llamar a la función virtual `GetState` mediante un puntero al tipo `VFuncBase`, se llama a `VFuncDerived::GetState`, y `GetState` se trata como public. Sin embargo, la llamada a `GetState` mediante un puntero al tipo `VFuncDerived` se considera una infracción del control de acceso, porque `GetState` se declara private en la clase `VFuncDerived`.

> [!CAUTION]
> La función virtual `GetState` se puede llamar mediante un puntero a la clase base `VFuncBase`. Esto no significa que la función llamada sea la versión de la clase base de esa función.

## <a name="access-control-with-multiple-inheritance"></a>Control de acceso con herencia múltiple

En los entramados de herencia múltiple con clases base virtuales, se puede acceder a un nombre determinado a través de más de una ruta. Dado que se puede aplicar un control de acceso diferente en estas rutas de acceso diferentes, el compilador elige la ruta de acceso que proporciona el mejor acceso. Consulte la siguiente figura.

![Acceso mediante rutas de acceso de un gráfico de herencia](../cpp/media/vc38v91.gif "Acceso mediante rutas de acceso de un gráfico de herencia") <br/>
Acceso mediante rutas de acceso de un gráfico de herencia

En la ilustración, se accede a un nombre declarado en la clase `VBase` siempre a través de la clase `RightPath`. La ruta de acceso derecha es más accesible porque `RightPath` declara `VBase` como clase base pública, mientras que `LeftPath` declara `VBase` como private.

## <a name="see-also"></a>Consulte también

[Referencia del idioma C++](../cpp/cpp-language-reference.md)
