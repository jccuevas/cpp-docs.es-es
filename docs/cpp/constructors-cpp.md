---
title: Constructores (C++)
ms.date: 12/27/2019
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
ms.openlocfilehash: 985c63c5c937f9e85b6898cdbcc61f347688b96d
ms.sourcegitcommit: 00f50ff242031d6069aa63c81bc013e432cae0cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/30/2019
ms.locfileid: "75546398"
---
# <a name="constructors-c"></a>Constructores (C++)

Para personalizar cómo se inicializan los miembros de clase o para invocar funciones cuando se crea un objeto de la clase, defina un *constructor*. Un constructor tiene el mismo nombre que la clase y no devuelve ningún valor. Puede definir tantos constructores sobrecargados como sean necesarios para personalizar la inicialización de varias maneras. Normalmente, los constructores tienen accesibilidad pública para que el código fuera de la definición de clase o de la jerarquía de herencia pueda crear objetos de la clase. Pero también puede declarar un constructor como **Protected** o **Private**.

Opcionalmente, los constructores pueden tomar una lista de miembros init. Se trata de una manera más eficaz de inicializar miembros de clase que asignar valores en el cuerpo del constructor. En el ejemplo siguiente se muestra una clase `Box` con tres constructores sobrecargados. Las dos últimas listas de inicialización de miembros de uso:

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

Cuando se declara una instancia de una clase, el compilador elige el constructor que se va a invocar en función de las reglas de resolución de sobrecarga:

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

- Los constructores se pueden declarar como **inline**, [Explicit](#explicit_constructors), **Friend** o [constexpr](#constexpr_constructors).
- Un constructor puede inicializar un objeto declarado como **const**, **volatile** o **const volatile**. El objeto se convierte en **const** una vez completado el constructor.
- Para definir un constructor en un archivo de implementación, asígnele un nombre completo como con cualquier otra función miembro: `Box::Box(){...}`.

## <a name="member_init_list"></a>Listas de inicializadores de miembro

Un constructor puede tener opcionalmente una lista de inicializadores de miembro, que inicializa los miembros de clase antes de la ejecución del cuerpo del constructor. (Tenga en cuenta que una lista de inicializadores de miembro no es lo mismo que una *lista de inicializadores* de tipo [std:: initializer_list\<t >](../standard-library/initializer-list-class.md)).

El uso de una lista de inicializadores de miembro es preferible a la asignación de valores en el cuerpo del constructor porque inicializa directamente el miembro. En el ejemplo siguiente se muestra que la lista de inicializadores de miembro consta de todas las expresiones de **identificador (argumento)** detrás del signo de dos puntos:

```cpp
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

El identificador debe hacer referencia a un miembro de clase. se inicializa con el valor del argumento. El argumento puede ser uno de los parámetros de constructor, una llamada de función o un [> de\<t:: initializer_list](../standard-library/initializer-list-class.md).

los miembros **const** y los miembros de tipo de referencia se deben inicializar en la lista de inicializadores de miembro.

Las llamadas a los constructores de clase base con parámetros deben realizarse en la lista de inicializadores para asegurarse de que la clase base se inicializa completamente antes de la ejecución del constructor derivado.

## <a name="default_constructors"></a>Constructores predeterminados

Normalmente, los *constructores predeterminados* no tienen parámetros, pero pueden tener parámetros con valores predeterminados.

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

Los constructores predeterminados son una de las [funciones miembro especiales](special-member-functions.md). Si no se declara ningún constructor en una clase, el compilador proporciona un constructor predeterminado **alineado** implícito.

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

Si confía en un constructor predeterminado implícito, asegúrese de inicializar los miembros en la definición de clase, tal como se muestra en el ejemplo anterior. Sin esos inicializadores, los miembros se desinicializarían y la llamada de volumen () generaría un valor de elementos no utilizados. En general, se recomienda inicializar los miembros de esta manera incluso cuando no se confía en un constructor predeterminado implícito.

Puede evitar que el compilador genere un constructor predeterminado implícito si lo define como [eliminado](#explicitly_defaulted_and_deleted_constructors):

```cpp
    // Default constructor
    Box() = delete;
```

Un constructor predeterminado generado por el compilador se definirá como eliminado si alguno de los miembros de clase no es constructor predeterminado. Por ejemplo, todos los miembros del tipo de clase y sus miembros de tipo de clase deben tener un constructor y destructores predeterminados a los que se pueda tener acceso. Todos los miembros de datos de tipo de referencia, así como los miembros **const** deben tener un inicializador de miembro predeterminado.

Cuando se llama a un constructor predeterminado generado por el compilador e intenta utilizar paréntesis, se emite una advertencia:

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

Este es un ejemplo del problema de Most Vexing Parse. Dado que la expresión del ejemplo se puede interpretar como la declaración de una función o como la invocación de un constructor predeterminado, y dado que los analizadores de C++ prefieren las declaraciones sobre otras cosas, la expresión se trata como una declaración de función. Para obtener más información, vea [la mayoría de Vexing Parse](https://en.wikipedia.org/wiki/Most_vexing_parse).

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

Sin embargo, puede usar un conjunto de listas de inicializadores para inicializar una matriz de objetos de cuadro:

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

Para obtener más información, vea [inicializadores](initializers.md).

## <a name="copy_and_move_constructors"></a>Constructores de copias

Un *constructor de copias* Inicializa un objeto mediante la copia de los valores de miembro de un objeto del mismo tipo. Si los miembros de clase son tipos simples, como valores escalares, el constructor de copias generado por el compilador es suficiente y no es necesario definir los suyos propios. Si la clase requiere una inicialización más compleja, debe implementar un constructor de copias personalizado. Por ejemplo, si un miembro de clase es un puntero, debe definir un constructor de copias para asignar una nueva memoria y copiar los valores del objeto señalado en el otro. El constructor de copias generado por el compilador simplemente copia el puntero, de modo que el nuevo puntero siga señalando a la ubicación de la memoria del otro.

Un constructor de copias puede tener una de estas firmas:

```cpp
    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

Al definir un constructor de copias, también debe definir un operador de asignación de copia (=). Para obtener más información, vea constructores de [asignación](assignment.md) y de [copia y operadores de asignación de copia](copy-constructors-and-copy-assignment-operators-cpp.md).

Puede evitar que se copie el objeto definiendo el constructor de copias como eliminado:

```cpp
    Box (const Box& other) = delete;
```

Al intentar copiar el objeto se produce el error *C2280: intentando hacer referencia a una función eliminada*.

## <a name="move_constructors"></a>Constructores de movimiento

Un *constructor de movimiento* es una función miembro especial que mueve la propiedad de los datos de un objeto existente a una nueva variable sin copiar los datos originales. Toma una referencia rvalue como primer parámetro y los parámetros adicionales deben tener valores predeterminados. Los constructores de movimiento pueden aumentar significativamente la eficacia del programa al pasar objetos de gran tamaño.

```cpp
Box(Box&& other);
```

El compilador elige un constructor de movimiento en determinadas situaciones en las que el objeto se inicializa con otro objeto del mismo tipo que está a punto de ser destruido y ya no necesita sus recursos. En el ejemplo siguiente se muestra un caso cuando se selecciona un constructor de movimiento mediante la resolución de sobrecarga. En el constructor que llama a `get_Box()`, el valor devuelto es un *xValue* (valor que expira). No se asigna a ninguna variable y, por lo tanto, está fuera del ámbito. Para proporcionar motivación a este ejemplo, vamos a dar a Box un vector grande de cadenas que represente su contenido. En lugar de copiar el vector y sus cadenas, el constructor de movimiento "lo robará del valor de expiración" box "para que el vector pertenezca ahora al nuevo objeto. La llamada a `std::move` es todo lo necesario, ya que las clases `vector` y `string` implementan sus propios constructores de movimiento.

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
    void Get_Contents()
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
    b2.Get_Contents(); // Prove that we have all the values

    char ch;
    cin >> ch; // keep window open
    return 0;
}
```

Si una clase no define un constructor de movimiento, el compilador genera uno implícito si no hay ningún constructor de copias declarado por el usuario, operador de asignación de copia, operador de asignación de movimiento o destructor. Si no se define ningún constructor de movimiento explícito o implícito, las operaciones que, de otro modo, usarían un constructor de movimiento, utilizarán en su lugar el constructor de copias. Si una clase declara un constructor de movimiento o un operador de asignación de movimiento, el constructor de copias declarado implícitamente se define como eliminado.

Un constructor de movimiento declarado implícitamente se define como Deleted si alguno de los miembros que son tipos de clase carece de un destructor o el compilador no puede determinar qué constructor se debe usar para la operación de movimiento.

Para obtener más información sobre cómo escribir un constructor de movimiento no trivial, vea [constructores de movimiento y operadores de asignaciónC++de movimiento ()](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

## <a name="explicitly_defaulted_and_deleted_constructors"></a>Constructores explícitamente predeterminados y eliminados

Puede establecer explícitamente constructores de copia *predeterminados* , constructores predeterminados, constructores de movimiento, operadores de asignación de copia, operadores de asignación de movimiento y destructores. Puede *eliminar* explícitamente todas las funciones miembro especiales.

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

Para obtener más información, vea [funciones predeterminadas y eliminadas explícitamente](../cpp/explicitly-defaulted-and-deleted-functions.md).

## <a name="constexpr_constructors"></a>constructores constexpr

Un constructor se puede declarar como [constexpr](constexpr-cpp.md) si

- se declara como valor predeterminado o bien satisface todas las condiciones de [las funciones constexpr](constexpr-cpp.md#constexpr_functions) en general.
- la clase no tiene clases base virtuales;
- cada uno de los parámetros es un [tipo literal](trivial-standard-layout-and-pod-types.md#literal_types);
- el cuerpo no es un bloque try de función;
- se inicializan todos los miembros de datos no estáticos y los subobjetos de clase base;
- Si la clase es (a) una Unión que tiene miembros variantes, o (b) tiene uniones anónimas, solo se inicializa uno de los miembros de la Unión;
- todos los miembros de datos no estáticos del tipo de clase y todos los subobjetos de clase base tienen un constructor constexpr

## <a name="init_list_constructors"></a>Constructores de la lista de inicializadores

Si un constructor toma un valor [STD:: initializer_list\<t\>](../standard-library/initializer-list-class.md) como su parámetro y cualquier otro parámetro tiene argumentos predeterminados, ese constructor se seleccionará en la resolución de sobrecarga cuando se cree una instancia de la clase a través de la inicialización directa. Puede utilizar la initializer_list para inicializar cualquier miembro que pueda aceptarla. Por ejemplo, supongamos que la clase Box (mostrada anteriormente) tiene un miembro `std::vector<string>` `m_contents`. Puede proporcionar un constructor similar al siguiente:

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

Y, a continuación, crear objetos de cuadro como este:

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit_constructors"></a>Constructores explícitos

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

Estas conversiones pueden ser útiles en algunos casos, pero lo más habitual es que provoquen errores sutiles, pero graves, en el código. Como norma general, debe utilizar la palabra clave **Explicit** en un constructor (y los operadores definidos por el usuario) para evitar este tipo de conversión implícita de tipos:

```cpp
explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

Cuando el constructor es explícito, esta línea provoca un error del compilador: `ShippingOrder so(42, 10.8);`.  Para obtener más información, vea [conversiones de tipos definidos por el usuario](../cpp/user-defined-type-conversions-cpp.md).

## <a name="order_of_construction"></a>Orden de construcción

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

Un constructor de clase derivada siempre llama a un constructor de clase base, por lo que se pueden usar clases base completamente construidas antes de realizar cualquier trabajo adicional. Se llama a los constructores de clase base en orden de derivación; por ejemplo, si `ClassA` se deriva de `ClassB`, que se deriva de `ClassC`, primero se llama al constructor `ClassC`, después el constructor `ClassB` y, por último, el constructor `ClassA`.

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

## <a name="extended_aggregate"></a>Constructores derivados e inicialización de agregados extendidos

Si el constructor de una clase base no es público, pero accesible para una clase derivada, en el modo **/STD: c++ 17** en Visual Studio 2017 y versiones posteriores, no se pueden usar llaves vacías para inicializar un objeto del tipo derivado.

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

En el ejemplo siguiente se muestra el comportamiento de C++ 17 en Visual Studio 2017 y versiones posteriores en el modo **/STD: c++ 17** :

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

### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>Constructores para las clases que tienen herencia múltiple

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

## <a name="delegating_constructors"></a>Delegar constructores

Un *constructor de delegación* llama a un constructor diferente en la misma clase para realizar parte del trabajo de inicialización. Esto resulta útil si tiene varios constructores que todos tienen para realizar un trabajo similar. Puede escribir la lógica principal en un constructor e invocarla desde otras personas. En el siguiente ejemplo trivial, Box (int) delega su cuadro de trabajo a (int, int, int):

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

El objeto creado por los constructores se inicializa totalmente en cuanto finaliza cualquiera de los constructores. Para obtener más información, vea [delegar constructores](../cpp/delegating-constructors.md).

## <a name="inheriting_constructors"></a>Heredar constructores (C++ 11)

Una clase derivada puede heredar los constructores de una clase base directa mediante una declaración **using** , tal como se muestra en el ejemplo siguiente:

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

**Visual Studio 2017 y versiones posteriores**: la instrucción **using** en el modo **/STD: c++ 17** pone en el ámbito todos los constructores de la clase base, excepto aquellos que tienen una firma idéntica a los constructores de la clase derivada. En general, es mejor usar constructores que heredan cuando la clase derivada no declara ningún constructor o miembro de datos nuevo. Vea también [mejoras en la versión 15,7 de Visual Studio 2017](https://docs.microsoft.com/cpp/overview/cpp-conformance-improvements?view=vs-2017#improvements_157).

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

## <a name="constructors_in_composite_classes"></a>Constructores y clases compuestas

Las clases que contienen miembros de tipo de clase se conocen como *clases compuestas*. Cuando se crea un miembro de tipo de clase compuesta, se llama al constructor antes que al propio constructor de la clase. Si una clase contenida carece de un constructor predeterminado, debe utilizar una lista de inicializaciones en el constructor de la clase compuesta. En el ejemplo anterior de `StorageBox`, si cambia el tipo de la variable miembro `m_label` a una nueva clase `Label`, debe llamar al constructor de la clase base e inicializar la variable `m_label` en el constructor `StorageBox`:

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
- [Constructores de movimiento y operadores de asignación de movimiento](move-constructors-and-move-assignment-operators-cpp.md)
- [Delegar constructores](delegating-constructors.md)

## <a name="see-also"></a>Vea también

[Clases y Structs](classes-and-structs-cpp.md)
