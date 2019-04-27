---
title: Constructores (C++)
ms.date: 04/06/2018
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
ms.openlocfilehash: a45cee1abd9351a8fef56769706fe8944a7965b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154742"
---
# <a name="constructors-c"></a>Constructores (C++)

Para personalizar cómo se inicializan los miembros de clase, o para invocar funciones cuando se crea un objeto de la clase, defina un *constructor*. Un constructor tiene el mismo nombre que la clase y no devuelve ningún valor. Puede definir tantos constructores sobrecargados según sea necesario para personalizar la inicialización de varias maneras. Normalmente, los constructores tienen accesibilidad pública para que el código fuera de la jerarquía de herencia o de definición de clase puede crear objetos de la clase. Pero también se puede declarar un constructor como **protegido** o **privada**.

Constructores, opcionalmente, pueden tomar a un miembro de la lista de init. Se trata de una forma más eficaz para inicializar a los miembros de clase que la asignación de valores en el cuerpo del constructor. El ejemplo siguiente muestra una clase `Box` con tres constructores sobrecargados. Las dos últimas usan listas de miembros de init:

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

Cuando se declara una instancia de una clase, el compilador elige qué constructor invocar según las reglas de resolución de sobrecarga:

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

- Los constructores se pueden declarar como **inline**, [explícita](#explicit_constructors), **friend** o [constexpr](#constexpr_constructors).
- Un constructor puede inicializar un objeto que se ha declarado como **const**, **volátil** o **const volatile**. El objeto se convierte en **const** una vez completado el constructor.
- Para definir un constructor en un archivo de implementación, asígnele un nombre completo al igual que con cualquier otra función miembro: `Box::Box(){...}`.

## <a name="member_init_list"></a> Listas de inicializadores de miembro

Un constructor puede tener opcionalmente una lista de inicializadores de miembro, que inicializa a los miembros de clase antes de la ejecución del cuerpo del constructor. (Tenga en cuenta que una lista de inicializadores de miembro no es lo mismo que un *lista de inicializadores* typu [std:: initializer_list\<T >](../standard-library/initializer-list-class.md).)

Es preferible usar una lista de inicializadores de miembro a través de la asignación de valores en el cuerpo del constructor porque inicializa al miembro directamente. En el ejemplo siguiente se muestra el inicializador de miembro de lista se compone de todos los **identifier(argument)** expresiones después de los dos puntos:

```cpp
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

El identificador debe hacer referencia a un miembro de clase; se inicializa con el valor del argumento. El argumento puede ser uno de los parámetros del constructor, una llamada de función o un [std:: initializer_list\<T >](../standard-library/initializer-list-class.md).

**Const** deben inicializarse miembros y los miembros del tipo de referencia en la lista de inicializadores de miembro.

En la lista de inicializadores, se deberían realizar llamadas a los constructores de clase base con parámetros para asegurarse de que la clase base está completamente inicializada antes de la ejecución del constructor derivada.

## <a name="default_constructors"></a> Constructores predeterminados

*Constructores predeterminados* suelen no tener ningún parámetro, pero pueden tener parámetros con valores predeterminados.

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

Los constructores predeterminados son uno de los [funciones miembro especiales](special-member-functions.md). Si no se declara ningún constructor en una clase, el compilador proporciona un modo implícito **inline** constructor predeterminado.

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

Si confía en un constructor predeterminado implícito, asegúrese de inicializar a los miembros de la definición de clase, como se muestra en el ejemplo anterior. Sin esos inicializadores, sería sin inicializar los miembros y la llamada Volume() generaría un valor de elementos no utilizados. En general, es aconsejable inicializar a miembros de este modo, incluso cuando no depender de un constructor predeterminado implícito.

Puede evitar que el compilador genere un constructor predeterminado implícito si se define como [eliminado](#explicitly_defaulted_and_deleted_constructors):

```cpp
    // Default constructor
    Box() = delete;
```

Un constructor predeterminado generado por el compilador se definirá como elimina si ningún miembro de clase no puede construir de forma predeterminada. Por ejemplo, todos los miembros de tipo de clase y sus miembros de tipo de clase, deben tener un constructor predeterminado y los destructores que son accesibles. Escribe todos los miembros de datos de referencia, así como **const** los miembros deben tener un inicializador de miembro predeterminado.

Al llamar a un constructor predeterminado generado por el compilador y pruebe a utilizar paréntesis, se emitirá una advertencia:

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

Este es un ejemplo del problema de Most Vexing Parse. Dado que la expresión del ejemplo se puede interpretar como la declaración de una función o como la invocación de un constructor predeterminado, y dado que los analizadores de C++ prefieren las declaraciones sobre otras cosas, la expresión se trata como una declaración de función. Para obtener más información, consulte [Most Vexing Parse](http://en.wikipedia.org/wiki/Most_vexing_parse).

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

Sin embargo, puede usar un conjunto de listas de inicializadores para inicializar una matriz de objetos incluidos:

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

Para obtener más información, consulte [inicializadores](initializers.md).

## <a name="copy_and_move_constructors"></a> Constructores de copias

Un *constructor de copias* Inicializa un objeto mediante la copia de los valores de miembro de un objeto del mismo tipo. Si los miembros de clase son todos los tipos simples como valores escalares, el constructor de copias generado por el compilador es suficiente y no necesita definir su propio. Si la clase requiere inicialización más compleja, deberá implementar un constructor de copia personalizado. Por ejemplo, si un miembro de clase es un puntero, a continuación, deberá definir un constructor de copias para asignar la memoria nueva y copie los valores de la otra apunta al objeto. El constructor de copias generado por el compilador simplemente copia el puntero, por lo que sigue el nuevo puntero señala a la otra ubicación de memoria.

Un constructor de copias puede tener una de estas firmas:

```cpp
    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

Al definir un constructor de copias, también debe definir un operador de asignación de copia (=). Para obtener más información, consulte [asignación](assignment.md) y [copie constructores y operadores de asignación](copy-constructors-and-copy-assignment-operators-cpp.md).

Puede impedir que el objeto que se copia al definir el constructor de copias como eliminado:

```cpp
    Box (const Box& other) = delete;
```

Al intentar copiar el objeto produce el error *C2280: intentando hacer referencia a una función eliminada*.

## <a name="move_constructors"></a> Constructores de movimiento

Un *constructor de movimiento* es una función miembro especial que desplaza la posesión de los datos de un objeto existente a una nueva variable sin copiar los datos originales. Toma una referencia rvalue como su primer parámetro y cualquier parámetro adicional debe tener valores predeterminados. Constructores de movimiento pueden aumentar considerablemente la eficacia del programa al pasar alrededor de los objetos grandes. Un constructor de movimiento toma una referencia rvalue como su primer parámetro. Cualquier otro parámetro debe tener valores predeterminados.

```cpp
Box(Box&& other);
```

El compilador elige un constructor de movimiento en determinadas situaciones donde se está inicializando el objeto mediante otro objeto del mismo tipo que se va a destruir y ya no lo necesite los recursos. El ejemplo siguiente muestra un caso cuando se selecciona un constructor de movimiento por la resolución de sobrecarga. La variable *cuadro* devuelto por get_Box() es un *xvalue* (valor que va a expirar) que se va a dejar fuera del ámbito. Para proporcionar la motivación para este ejemplo, elegiremos el cuadro de un vector de cadenas que representan su contenido grande. En lugar de copiar el vector y sus cadenas, el constructor de movimiento "roba", desde el valor que va a expirar "cuadro" para que el vector ahora pertenece al nuevo objeto. La llamada a `std::move` es todo lo necesario porque ambos `vector` y `string` clases implementan sus propios constructores de movimiento.

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

Si una clase no define un constructor de movimiento, el compilador genera uno implícito si no hay ningún constructor declarado por el usuario copia, operador de asignación de copia, el operador de asignación de movimiento o un destructor. Si no se define ningún constructor de movimiento explícita o implícita, las operaciones que usaría un constructor de movimiento utilizan el constructor de copia en su lugar. Si una clase declara un constructor de movimiento o un operador de asignación de movimiento, se define el constructor de copias declarado implícitamente como eliminado.

Un constructor de movimiento declarada de forma implícita se definan como eliminadas si los miembros que son tipos de clase no tienen un destructor o el compilador no puede determinar qué constructor que se usará para la operación de traslado.

Para obtener más información sobre cómo escribir un constructor de movimiento triviales, consulte [constructores de movimiento y operadores de asignación de movimiento (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).

## <a name="explicitly_defaulted_and_deleted_constructors"></a> Constructores explícitamente establecidos como valor predeterminados y eliminados

Se puede convertir explícitamente *predeterminada* constructores de copias, constructores predeterminados, constructores de movimiento, operadores de asignación de copiar, mover los operadores de asignación y destructores. Se puede convertir explícitamente *eliminar* todas las funciones miembro especiales.

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

Para obtener más información, consulte [explícitamente como valores predeterminados y eliminar funciones](../cpp/explicitly-defaulted-and-deleted-functions.md).

## <a name="constexpr_constructors"></a> constructores constexpr

Un constructor puede declararse como [constexpr](constexpr-cpp.md) si

- es declaradas como su valor predeterminado, o bien satisface todas las condiciones para [funciones constexpr](constexpr-cpp.md#constexpr_functions) en general;
- la clase no tiene ninguna clase base virtual;
- cada uno de los parámetros es un [tipo literal](trivial-standard-layout-and-pod-types.md#literal_types);
- el cuerpo no es un bloque try función;
- todos los miembros de datos no estáticos y los subobjetos de clase base se inicializan;
- Si la clase es (a) una unión tener miembros variantes o (b) tiene las uniones anónimas, sólo uno de los miembros de la unión se ha inicializado;
- cada miembro de datos no estáticos del tipo de clase y todos los subobjetos de clase base tienen un constructor constexpr

## <a name="init_list_constructors"></a> Constructores de la lista de inicializadores

Si un constructor que toma un [std:: initializer_list\<T\> ](../standard-library/initializer-list-class.md) como su parámetro y cualquier otro parámetro tener argumentos predeterminados, se seleccionará ese constructor en la resolución de sobrecarga cuando la clase es crea una instancia a través de la inicialización directa. Puede usar initializer_list para inicializar a un miembro que puede aceptarlo. Por ejemplo, suponga que la clase de cuadro (mostrada anteriormente) tiene un `std::vector<string>` miembro `m_contents`. Puede proporcionar un constructor como este:

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

Y, a continuación, cree un cuadro de objetos similar al siguiente:

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit_constructors"></a> Constructores explícitos

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

Estas conversiones pueden ser útiles en algunos casos, pero lo más habitual es que provoquen errores sutiles, pero graves, en el código. Como norma general, debe usar el **explícita** palabra clave en un constructor (y los operadores definidos por el usuario) para evitar este tipo de conversión de tipos implícita:

```cpp
explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

Cuando el constructor es explícito, esta línea provoca un error del compilador: `ShippingOrder so(42, 10.8);`.  Para obtener más información, consulte [conversiones de tipos definidos por el usuario](../cpp/user-defined-type-conversions-cpp.md).

## <a name="order_of_construction"></a> Orden de construcción

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

Un constructor de clase derivada siempre llama a un constructor de clase base, por lo que se pueden usar clases base completamente construidas antes de realizar cualquier trabajo adicional. Los constructores de clase base se llaman en orden de derivación: por ejemplo, si `ClassA` se deriva de `ClassB`, que se deriva `ClassC`, el `ClassC` se llama al constructor en primer lugar, el `ClassB` constructor, el `ClassA` constructor.

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

### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>Constructores de clases que tienen herencia múltiple

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

## <a name="virtual_functions_in_constructors"></a> Funciones virtuales en constructores

Se recomienda tener cuidado al llamar a funciones virtuales en constructores. Dado que el constructor de clase base se invoca siempre antes del constructor de clase derivada, la función a la que llama en el constructor base es la versión de la clase base, no la versión de la clase derivada. En el ejemplo siguiente, crear una `DerivedClass` hace que la implementación de `BaseClass` de `print_it()` se ejecute antes de que el constructor de `DerivedClass` haga que la implementación de `DerivedClass` de `print_it()` se ejecute:

```cpp
#include <iostream>
using namespace std;

class BaseClass{
public:
    BaseClass(){
        print_it();
    }
    virtual void print_it() {
        cout << "BaseClass print_it" << endl;
    }
};

class DerivedClass : public BaseClass {
public:
    DerivedClass() {
        print_it();
    }
    virtual void print_it(){
        cout << "Derived Class print_it" << endl;
    }
};

int main() {

    DerivedClass dc;
}
```

Este es el resultado:

```Output
BaseClass print_it
Derived Class print_it
```

## <a name="delegating_constructors"></a> Delegación de constructores

Un *constructor que delega* llama a un constructor diferente en la misma clase para realizar algunas de las tareas de inicialización. Esto es útil cuando tiene varios constructores que todos tienen que realizar un trabajo similar. Puede escribir la lógica principal en un constructor e invocarlo desde otros usuarios. En el siguiente ejemplo trivial, Box(int) delega su trabajo en Box(int,int,int):

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

El objeto creado por los constructores se inicializa totalmente en cuanto finaliza cualquiera de los constructores. Para obtener más información, consulte [inicialización uniforme y constructores de delegación](../cpp/uniform-initialization-and-delegating-constructors.md).

## <a name="inheriting_constructors"></a> Constructores que heredan (C ++ 11)

Una clase derivada puede heredar los constructores de una clase base directa mediante el uso de un **mediante** declaración como se muestra en el ejemplo siguiente:

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

**Visual Studio 2017 versión 15.7 y posteriores:** El **mediante** instrucción **/std: c ++ 17** modo pone en el ámbito de todos los constructores de la clase base excepto los que tienen una firma idéntica a los constructores de la clase derivada. En general, es mejor usar constructores que heredan cuando la clase derivada no declara ningún constructor o miembro de datos nuevo. Vea también [mejoras en Visual Studio 2017 versión 15.7](../overview/cpp-conformance-improvements.md#improvements_157).

Una plantilla de clase puede heredar todos los constructores de un argumento de tipo si dicho tipo especifica una clase base:

```cpp
template< typename T >
class Derived : T {
    using T::T;   // declare the constructors from T
    // ...
};
```

Una clase derivada no puede heredar de varias clases base si esas clases base tienen constructores con una firma idéntica.

## <a name="constructors_in_composite_classes"></a> Los constructores y clases compuestas

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
