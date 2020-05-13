---
title: Constructores (C++)
ms.date: 12/27/2019
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
ms.openlocfilehash: 4640bcf5f21bbe018a8744a6c5206bdd09509c98
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749648"
---
# <a name="constructors-c"></a>Constructores (C++)

Para personalizar cómo se inicializan los miembros de clase o para invocar funciones cuando se crea un objeto de la clase, defina un *constructor.* Un constructor tiene el mismo nombre que la clase y no devuelve ningún valor. Puede definir tantos constructores sobrecargados como sea necesario para personalizar la inicialización de varias maneras. Normalmente, los constructores tienen accesibilidad pública para que el código fuera de la definición de clase o jerarquía de herencia pueda crear objetos de la clase. Pero también puede declarar un constructor como **protegido** o **privado.**

Los constructores pueden, opcionalmente, tomar una lista de datos de miembros. Esta es una manera más eficaz de inicializar los miembros de clase que asignar valores en el cuerpo del constructor. En el ejemplo `Box` siguiente se muestra una clase con tres constructores sobrecargados. Las dos últimas listas de usuarios de miembros:

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initialize a Box with equal dimensions (i.e. a cube)
    explicit Box(int i) : m_width(i), m_length(i), m_height(i) // member init list
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}

    int Volume() { return m_width * m_length * m_height; }

private:
    // Will have value of 0 when default constructor is called.
    // If we didn't zero-init here, default constructor would
    // leave them uninitialized with garbage values.
    int m_width{ 0 };
    int m_length{ 0 };
    int m_height{ 0 };
};
```

Cuando se declara una instancia de una clase, el compilador elige qué constructor invocar en función de las reglas de resolución de sobrecarga:

```cpp
int main()
{
    Box b; // Calls Box()

    // Using uniform initialization (preferred):
    Box b2 {5}; // Calls Box(int)
    Box b3 {5, 8, 12}; // Calls Box(int, int, int)

    // Using function-style notation:
    Box b4(2, 4, 6); // Calls Box(int, int, int)
}
```

- Los constructores pueden declararse como **inline ,** [explicit](#explicit_constructors), **friend** o [constexpr](#constexpr_constructors).
- Un constructor puede inicializar un objeto que se ha declarado como **const**, **volatile** o **const volatile**. El objeto se convierte en **const** una vez completado el constructor.
- Para definir un constructor en un archivo de implementación, asíbóunse como con cualquier otra función miembro: `Box::Box(){...}`.

## <a name="member-initializer-lists"></a><a name="member_init_list"></a>Listas de inicializadores de miembros

Un constructor puede tener opcionalmente una lista de inicializadores de miembro, que inicializa los miembros de clase antes de la ejecución del cuerpo del constructor. (Tenga en cuenta que una lista de inicializadores de miembro no es lo mismo que una lista de *inicializadores* de tipo [std::initializer_list\<T>](../standard-library/initializer-list-class.md).)

Se prefiere usar una lista de inicializadores de miembro en lugar de asignar valores en el cuerpo del constructor porque inicializa directamente el miembro. En el ejemplo siguiente se muestra que la lista de inicializadores de miembro consta de todas las expresiones **identifier(argument)** después de los dos puntos:

```cpp
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

El identificador debe hacer referencia a un miembro de clase; se inicializa con el valor del argumento. El argumento puede ser uno de los parámetros del constructor, una llamada de función o un [>t\<std::initializer_list ](../standard-library/initializer-list-class.md).

**Const miembros** y miembros de tipo de referencia deben inicializarse en la lista de inicializadores de miembro.

Las llamadas a constructores de clase base parametrizadas deben realizarse en la lista de inicializadores para asegurarse de que la clase base se inicializa completamente antes de la ejecución del constructor derivado.

## <a name="default-constructors"></a><a name="default_constructors"></a>Constructores predeterminados

*Los constructores predeterminados* normalmente no tienen parámetros, pero pueden tener parámetros con valores predeterminados.

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

Los constructores predeterminados son una de las [funciones miembro especiales.](special-member-functions.md) Si no se declara ningún constructor en una clase, el compilador proporciona un constructor predeterminado **en línea** implícito.

```cpp
#include <iostream>
using namespace std;

class Box {
public:
    int Volume() {return m_width * m_height * m_length;}
private:
    int m_width { 0 };
    int m_height { 0 };
    int m_length { 0 };
};

int main() {
    Box box1; // Invoke compiler-generated constructor
    cout << "box1.Volume: " << box1.Volume() << endl; // Outputs 0
}
```

Si confía en un constructor predeterminado implícito, asegúrese de inicializar los miembros en la definición de clase, como se muestra en el ejemplo anterior. Sin esos inicializadores, los miembros no se inicializarían y la llamada Volume() produciría un valor de elemento sóno. En general, es recomendable inicializar los miembros de esta manera, incluso cuando no se basa en un constructor predeterminado implícito.

Puede evitar que el compilador genere un constructor predeterminado implícito definiéndolo como [eliminado:](#explicitly_defaulted_and_deleted_constructors)

```cpp
    // Default constructor
    Box() = delete;
```

Un constructor predeterminado generado por el compilador se definirá como eliminado si los miembros de clase no son constructibles de forma predeterminada. Por ejemplo, todos los miembros de tipo de clase y sus miembros de tipo de clase deben tener un constructor y destructores predeterminados que sean accesibles. Todos los miembros de datos de tipo de referencia, así como los **miembros const** deben tener un inicializador de miembro predeterminado.

Cuando se llama a un constructor predeterminado generado por el compilador e intenta usar paréntesis, se emite una advertencia:

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

Este es un ejemplo del problema de Most Vexing Parse. Dado que la expresión del ejemplo se puede interpretar como la declaración de una función o como la invocación de un constructor predeterminado, y dado que los analizadores de C++ prefieren las declaraciones sobre otras cosas, la expresión se trata como una declaración de función. Para obtener más información, consulte [Análisis más molesto](https://en.wikipedia.org/wiki/Most_vexing_parse).

Si se declaran constructores no predeterminados, el compilador no proporcionará un constructor predeterminado:

```cpp
class Box {
public:
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height){}
private:
    int m_width;
    int m_length;
    int m_height;

};

int main(){

    Box box1(1, 2, 3);
    Box box2{ 2, 3, 4 };
    Box box3; // C2512: no appropriate default constructor available
}
```

Si una clase no tiene ningún constructor predeterminado, una matriz de objetos de esa clase no se puede crear únicamente mediante una sintaxis de corchetes. Por ejemplo, dado el bloque de código anterior, no se puede declarar una matriz de marcos como esta:

```cpp
Box boxes[3]; // C2512: no appropriate default constructor available
```

Sin embargo, puede utilizar un conjunto de listas de inicializadores para inicializar una matriz de box objetos:

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

Para obtener más información, consulte [Inicializadores](initializers.md).

## <a name="copy-constructors"></a><a name="copy_and_move_constructors"></a>Constructores de copias

Un constructor de *copia* inicializa un objeto copiando los valores de miembro de un objeto del mismo tipo. Si los miembros de la clase son todos tipos simples, como valores escalares, el constructor de copias generado por el compilador es suficiente y no es necesario definir los suyos propios. Si la clase requiere una inicialización más compleja, debe implementar un constructor de copia personalizado. Por ejemplo, si un miembro de clase es un puntero, debe definir un constructor de copia para asignar nueva memoria y copiar los valores del objeto señalado del otro. El constructor de copia generado por el compilador simplemente copia el puntero, de modo que el nuevo puntero sigue apuntando a la ubicación de memoria del otro.

Un constructor de copias puede tener una de estas firmas:

```cpp
    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

Cuando se define un constructor de copias, también se debe definir un operador de asignación de copia (-). Para obtener más información, vea [Constructores de asignación](assignment.md) y [copia y operadores](copy-constructors-and-copy-assignment-operators-cpp.md)de asignación de copia .

Puede evitar que el objeto se copie definiendo el constructor de copias como eliminado:

```cpp
    Box (const Box& other) = delete;
```

Al intentar copiar el objeto se produce el error *C2280: intentar hacer referencia a una función eliminada*.

## <a name="move-constructors"></a><a name="move_constructors"></a>Mover constructores

Un *constructor de movimiento* es una función miembro especial que mueve la propiedad de los datos de un objeto existente a una nueva variable sin copiar los datos originales. Toma una referencia rvalue como su primer parámetro y cualquier parámetro adicional debe tener valores predeterminados. Los constructores de movimiento pueden aumentar significativamente la eficiencia del programa al pasar alrededor de objetos grandes.

```cpp
Box(Box&& other);
```

El compilador elige un constructor de movimiento en determinadas situaciones en las que el objeto se inicializa con otro objeto del mismo tipo que está a punto de ser destruido y ya no necesita sus recursos. En el ejemplo siguiente se muestra un caso cuando se selecciona un constructor de movimiento por resolución de sobrecarga. En el constructor `get_Box()`que llama a , el valor devuelto es un *valor x* (valor de eXpiring). No se asigna a ninguna variable y, por lo tanto, está a punto de salir del ámbito. Para proporcionar motivación para este ejemplo, vamos a dar a Box un vector grande de cadenas que representan su contenido. En lugar de copiar el vector y sus cadenas, el constructor de movimiento lo "roba" del valor que expira "box" para que el vector ahora pertenezca al nuevo objeto. La llamada `std::move` a es todo lo `vector` `string` que se necesita porque ambas y las clases implementan sus propios constructores de movimiento.

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
using namespace std;

class Box {
public:
    Box() { std::cout << "default" << std::endl; }
    Box(int width, int height, int length)
       : m_width(width), m_height(height), m_length(length)
    {
        std::cout << "int,int,int" << std::endl;
    }
    Box(Box& other)
       : m_width(other.m_width), m_height(other.m_height), m_length(other.m_length)
    {
        std::cout << "copy" << std::endl;
    }
    Box(Box&& other) : m_width(other.m_width), m_height(other.m_height), m_length(other.m_length)
    {
        m_contents = std::move(other.m_contents);
        std::cout << "move" << std::endl;
    }
    int Volume() { return m_width * m_height * m_length; }
    void Add_Item(string item) { m_contents.push_back(item); }
    void Print_Contents()
    {
        for (const auto& item : m_contents)
        {
            cout << item << " ";
        }
    }
private:
    int m_width{ 0 };
    int m_height{ 0 };
    int m_length{ 0 };
    vector<string> m_contents;
};

Box get_Box()
{
    Box b(5, 10, 18); // "int,int,int"
    b.Add_Item("Toupee");
    b.Add_Item("Megaphone");
    b.Add_Item("Suit");

    return b;
}

int main()
{
    Box b; // "default"
    Box b1(b); // "copy"
    Box b2(get_Box()); // "move"
    cout << "b2 contents: ";
    b2.Print_Contents(); // Prove that we have all the values

    char ch;
    cin >> ch; // keep window open
    return 0;
}
```

Si una clase no define un constructor de movimiento, el compilador genera uno implícito si no hay ningún constructor de copia declarado por el usuario, operador de asignación de copia, operador de asignación de movimiento o destructor. Si no se define ningún constructor de movimiento explícito o implícito, las operaciones que de otro modo usarían un constructor de movimiento usan el constructor de copia en su lugar. Si una clase declara un constructor de movimiento o un operador de asignación de movimiento, el constructor de copia declarado implícitamente se define como eliminado.

Un constructor de movimiento declarado implícitamente se define como eliminado si los miembros que son tipos de clase carecen de un destructor o el compilador no puede determinar qué constructor usar para la operación de movimiento.

Para obtener más información acerca de cómo escribir un constructor de movimiento no trivial, vea [Mover constructores y mover operadores de asignación (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

## <a name="explicitly-defaulted-and-deleted-constructors"></a><a name="explicitly_defaulted_and_deleted_constructors"></a>Constructores explícitamente predeterminados y eliminados

Puede establecer explícitamente constructores de copia *predeterminados,* constructores predeterminados, constructores de movimiento, operadores de asignación de copia, operadores de asignación de movimiento y destructores. Puede *eliminar* explícitamente todas las funciones miembro especiales.

```cpp
class Box
{
public:
    Box2() = delete;
    Box2(const Box2& other) = default;
    Box2& operator=(const Box2& other) = default;
    Box2(Box2&& other) = default;
    Box2& operator=(Box2&& other) = default;
    //...
};
```

Para obtener más información, consulte [Funciones eliminadas y predeterminadas explícitamente.](../cpp/explicitly-defaulted-and-deleted-functions.md)

## <a name="constexpr-constructors"></a><a name="constexpr_constructors"></a>constructores constexpr

Un constructor puede ser declarado como [constexpr](constexpr-cpp.md) si

- se declara como predeterminado o, de lo contrario, cumple todas las condiciones para las [funciones constexpr](constexpr-cpp.md#constexpr_functions) en general;
- la clase no tiene clases base virtuales;
- cada uno de los parámetros es un [tipo literal;](trivial-standard-layout-and-pod-types.md#literal_types)
- el cuerpo no es una función try-block;
- se inicializan todos los miembros de datos no estáticos y los subobjetos de clase base;
- si la clase es (a) una unión que tiene miembros de variante, o (b) tiene uniones anónimas, solo se inicializa uno de los miembros del sindicato;
- cada miembro de datos no estáticos de tipo de clase, y todos los subobjetos de clase base tienen un constructor constexpr

## <a name="initializer-list-constructors"></a><a name="init_list_constructors"></a>Constructores de lista de inicializadores

Si un constructor toma un [std::initializer_list\<T\> ](../standard-library/initializer-list-class.md) como parámetro y cualquier otro parámetro tiene argumentos predeterminados, ese constructor se seleccionará en resolución de sobrecarga cuando se cree una instancia de la clase a través de la inicialización directa. Puede usar el initializer_list para inicializar cualquier miembro que pueda aceptarlo. Por ejemplo, supongamos que la clase `std::vector<string>` `m_contents`Box (mostrada anteriormente) tiene un miembro. Puede proporcionar un constructor como este:

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

Y luego crea objetos Box como este:

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit-constructors"></a><a name="explicit_constructors"></a>Constructores explícitos

Si una clase tiene un constructor con un solo parámetro, o si todos los parámetros excepto uno tienen un valor predeterminado, el tipo de parámetro se puede convertir implícitamente en el tipo de clase. Por ejemplo, si la clase `Box` tiene un constructor como este:

```cpp
Box(int size): m_width(size), m_length(size), m_height(size){}
```

Se puede inicializar un objeto Box como este:

```cpp
Box b = 42;
```

O pasar un valor int a una función que toma un objeto Box:

```cpp
class ShippingOrder
{
public:
    ShippingOrder(Box b, double postage) : m_box(b), m_postage(postage){}

private:
    Box m_box;
    double m_postage;
}
//elsewhere...
    ShippingOrder so(42, 10.8);
```

Estas conversiones pueden ser útiles en algunos casos, pero lo más habitual es que provoquen errores sutiles, pero graves, en el código. Como regla general, debe usar la palabra clave **explicit** en un constructor (y operadores definidos por el usuario) para evitar este tipo de conversión de tipos implícita:

```cpp
explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

Cuando el constructor es explícito, esta línea provoca un error del compilador: `ShippingOrder so(42, 10.8);`.  Para obtener más información, consulte [Conversiones](../cpp/user-defined-type-conversions-cpp.md)de tipos definidas por el usuario .

## <a name="order-of-construction"></a><a name="order_of_construction"></a>Orden de construcción

Un constructor realiza su trabajo en este orden:

1. Llama a los constructores miembros y de clase base en el orden en que se declararon.

1. Si la clase se deriva de clases base virtuales, inicializa los punteros base virtuales del objeto.

1. Si la clase tiene o hereda funciones virtuales, inicializa los punteros de funciones virtuales del objeto. Los punteros de funciones virtuales apuntan a la tabla de funciones virtuales de la clase para permitir el enlace correcto de las llamadas de funciones virtuales al código.

1. Ejecuta cualquier código en el cuerpo de su función.

En el ejemplo siguiente se muestra el orden en el que los constructores miembros y de clase base se llaman en el constructor para una clase derivada. Primero, se llama al constructor base, después los miembros de la clase base se inicializan en el orden en que aparecen en la declaración de clase y después se llama al constructor derivado.

```cpp
#include <iostream>

using namespace std;

class Contained1 {
public:
    Contained1() { cout << "Contained1 ctor\n"; }
};

class Contained2 {
public:
    Contained2() { cout << "Contained2 ctor\n"; }
};

class Contained3 {
public:
    Contained3() { cout << "Contained3 ctor\n"; }
};

class BaseContainer {
public:
    BaseContainer() { cout << "BaseContainer ctor\n"; }
private:
    Contained1 c1;
    Contained2 c2;
};

class DerivedContainer : public BaseContainer {
public:
    DerivedContainer() : BaseContainer() { cout << "DerivedContainer ctor\n"; }
private:
    Contained3 c3;
};

int main() {
    DerivedContainer dc;
}
```

Este es el resultado:

```Output
Contained1 ctor
Contained2 ctor
BaseContainer ctor
Contained3 ctor
DerivedContainer ctor
```

Un constructor de clase derivada siempre llama a un constructor de clase base, por lo que se pueden usar clases base completamente construidas antes de realizar cualquier trabajo adicional. Los constructores de clase base se llaman en `ClassA` orden de `ClassB`derivación, por `ClassC`ejemplo, `ClassC` si se deriva `ClassB` de , `ClassA` que se deriva de , el constructor se llama primero, a continuación, el constructor y, a continuación, el constructor.

Si una clase base no tiene un constructor predeterminado, debe proporcionar los parámetros de constructor de clase base en el constructor de clase derivada:

```cpp
class Box {
public:
    Box(int width, int length, int height){
       m_width = width;
       m_length = length;
       m_height = height;
    }

private:
    int m_width;
    int m_length;
    int m_height;
};

class StorageBox : public Box {
public:
    StorageBox(int width, int length, int height, const string label&) : Box(width, length, height){
        m_label = label;
    }
private:
    string m_label;
};

int main(){

    const string aLabel = "aLabel";
    StorageBox sb(1, 2, 3, aLabel);
}
```

Si un constructor inicia una excepción, el orden de destrucción es el inverso al orden de la construcción:

1. El código del cuerpo de la función de constructor se desenredará.

1. Los objetos miembro y de la clase base se destruirán en el orden inverso de la declaración.

1. Si el constructor no delega, se destruirán todos los miembros y objetos de clase base totalmente implementados. Sin embargo, dado que el objeto en sí no está totalmente implementado, el destructor no se ejecutará.

## <a name="derived-constructors-and-extended-aggregate-initialization"></a><a name="extended_aggregate"></a>Constructores derivados e inicialización agregada extendida

Si el constructor de una clase base no es público, pero accesible para una clase derivada, en el modo **/std:c++17** en Visual Studio 2017 y versiones posteriores no puede usar llaves vacías para inicializar un objeto del tipo derivado.

En el ejemplo siguiente se muestra el comportamiento correspondiente de C++14:

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {};

Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // OK in C++14: Calls Derived::Derived()
               // which can call Base ctor.
```

En C ++ 17, `Derived` ahora se considera un tipo de agregado. Eso significa que la inicialización de `Base` mediante el constructor privado predeterminado se produce directamente como parte de la regla de inicialización de agregados extendida. Anteriormente, el constructor privado `Base` se llamaba a través del constructor `Derived` y se realizaba correctamente debido a la declaración friend.

En el ejemplo siguiente se muestra el comportamiento de C++17 en Visual Studio 2017 y versiones posteriores en modo **/std:c++17:**

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {
    Derived() {} // add user-defined constructor
                 // to call with {} initialization
};

Derived d1; // OK. No aggregate init involved.

Derived d2 {}; // error C2248: 'Base::Base': cannot access
               // private member declared in class 'Base'
```

### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>Constructores para clases que tienen herencia múltiple

Si una clase se deriva de varias clases base, los constructores de clase base se invocan en el orden en que se muestran en la declaración de la clase derivada:

```cpp
#include <iostream>
using namespace std;

class BaseClass1 {
public:
    BaseClass1() { cout << "BaseClass1 ctor\n"; }
};
class BaseClass2 {
public:
    BaseClass2() { cout << "BaseClass2 ctor\n"; }
};
class BaseClass3 {
public:
    BaseClass3() { cout << "BaseClass3 ctor\n"; }
};
class DerivedClass : public BaseClass1,
                     public BaseClass2,
                     public BaseClass3
                     {
public:
    DerivedClass() { cout << "DerivedClass ctor\n"; }
};

int main() {
    DerivedClass dc;
}
```

Debería esperar los siguientes resultados:

```Output
BaseClass1 ctor
BaseClass2 ctor
BaseClass3 ctor
DerivedClass ctor
```

## <a name="delegating-constructors"></a><a name="delegating_constructors"></a>Delegar constructores

Un constructor de *delegación* llama a un constructor diferente en la misma clase para realizar parte del trabajo de inicialización. Esto es útil cuando tiene varios constructores que todos tienen que realizar un trabajo similar. Puede escribir la lógica principal en un constructor e invocarla desde otros. En el siguiente ejemplo trivial, Box(int) delega su trabajo en Box(int,int,int):

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initialize a Box with equal dimensions (i.e. a cube)
    Box(int i) :  Box(i, i, i);  // delegating constructor
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
    //... rest of class as before
};
```

El objeto creado por los constructores se inicializa totalmente en cuanto finaliza cualquiera de los constructores. Para obtener más información, consulte [Delegar constructores](../cpp/delegating-constructors.md).

## <a name="inheriting-constructors-c11"></a><a name="inheriting_constructors"></a>Constructores heredados (C++11)

Una clase derivada puede heredar los constructores de una clase base directa mediante una declaración **using** como se muestra en el ejemplo siguiente:

```cpp
#include <iostream>
using namespace std;

class Base
{
public:
    Base() { cout << "Base()" << endl; }
    Base(const Base& other) { cout << "Base(Base&)" << endl; }
    explicit Base(int i) : num(i) { cout << "Base(int)" << endl; }
    explicit Base(char c) : letter(c) { cout << "Base(char)" << endl; }

private:
    int num;
    char letter;
};

class Derived : Base
{
public:
    // Inherit all constructors from Base
    using Base::Base;

private:
    // Can't initialize newMember from Base constructors.
    int newMember{ 0 };
};

int main()
{
    cout << "Derived d1(5) calls: ";
    Derived d1(5);
    cout << "Derived d1('c') calls: ";
    Derived d2('c');
    cout << "Derived d3 = d2 calls: " ;
    Derived d3 = d2;
    cout << "Derived d4 calls: ";
    Derived d4;
}

/* Output:
Derived d1(5) calls: Base(int)
Derived d1('c') calls: Base(char)
Derived d3 = d2 calls: Base(Base&)
Derived d4 calls: Base()*/
```

::: moniker range=">=vs-2017"

**Visual Studio 2017 y versiones posteriores:** la instrucción **using** en el modo **/std:c++17** incluye el ámbito de todos los constructores de la clase base excepto los que tienen una firma idéntica a los constructores de la clase derivada. En general, es mejor usar constructores que heredan cuando la clase derivada no declara ningún constructor o miembro de datos nuevo. Consulte también [Mejoras en Visual Studio 2017 versión 15.7](https://docs.microsoft.com/cpp/overview/cpp-conformance-improvements?view=vs-2017#improvements_157).

::: moniker-end

Una plantilla de clase puede heredar todos los constructores de un argumento de tipo si dicho tipo especifica una clase base:

```cpp
template< typename T >
class Derived : T {
    using T::T;   // declare the constructors from T
    // ...
};
```

Una clase derivada no puede heredar de varias clases base si esas clases base tienen constructores con una firma idéntica.

## <a name="constructors-and-composite-classes"></a><a name="constructors_in_composite_classes"></a>Constructores y clases compuestas

Las clases que contienen miembros de tipo de clase se conocen como *clases compuestas.* Cuando se crea un miembro de tipo de clase compuesta, se llama al constructor antes que al propio constructor de la clase. Si una clase contenida carece de un constructor predeterminado, debe utilizar una lista de inicializaciones en el constructor de la clase compuesta. En el ejemplo anterior de `StorageBox`, si cambia el tipo de la variable miembro `m_label` a una nueva clase `Label`, debe llamar al constructor de la clase base e inicializar la variable `m_label` en el constructor `StorageBox`:

```cpp
class Label {
public:
    Label(const string& name, const string& address) { m_name = name; m_address = address; }
    string m_name;
    string m_address;
};

class StorageBox : public Box {
public:
    StorageBox(int width, int length, int height, Label label)
        : Box(width, length, height), m_label(label){}
private:
    Label m_label;
};

int main(){
// passing a named Label
    Label label1{ "some_name", "some_address" };
    StorageBox sb1(1, 2, 3, label1);

    // passing a temporary label
    StorageBox sb2(3, 4, 5, Label{ "another name", "another address" });

    // passing a temporary label as an initializer list
    StorageBox sb3(1, 2, 3, {"myname", "myaddress"});
}
```

## <a name="in-this-section"></a>En esta sección

- [Constructores de copia y operadores de asignación de copia](copy-constructors-and-copy-assignment-operators-cpp.md)
- [Mover constructores y mover operadores de asignación](move-constructors-and-move-assignment-operators-cpp.md)
- [Delegar constructores](delegating-constructors.md)

## <a name="see-also"></a>Vea también

[Clases y estructuras](classes-and-structs-cpp.md)
