---
title: Constructores (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: ece3414dbc7f4d362fa7dcc6f060e408b50e54e6
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="constructors-c"></a>Constructores (C++)
Un constructor es una especie de función miembro que inicializa una instancia de su clase. Un constructor tiene el mismo nombre que la clase y no devuelve ningún valor. Los constructores pueden tener un número indeterminado de parámetros y, a su vez, una clase puede tener un número indeterminado de constructores sobrecargados. Los constructores pueden tener cualquier tipo de accesibilidad, ya sea pública, protegida o privada. Si no define ningún constructor, el compilador generará un constructor predeterminado que no toma ningún parámetro; puede invalidar este comportamiento declarando un constructor predeterminado como eliminado.  
  
## <a name="in-this-topic"></a>En este tema  
  
-   [Orden de construcción](#order_of_construction)  
  
-   [Listas de miembros](#member_lists)  
  
-   [Constructores explícitos](#explicit_constructors)  
  
-   [Constructores predeterminados.](#default_constructors)  
  
-   [Copie y constructores de movimiento](#copy_and_move_constructors)  
  
-   [Constructores explícitamente establecidos como predeterminados y eliminados](#explicitly_defaulted_and_deleted_constructors)  
  
-   [Constructores de clases derivadas](#constructors_in_derived_classes)  
  
-   [Funciones virtuales en constructores](#virtual_functions_in_constructors)  
  
-   [Clases de constructores y compuestas](#constructors_in_composite_classes)  
  
-   [Delegación de constructores](#delegating_constructors)  
  
-   [Constructores que heredan (C ++ 11)](#inheriting_constructors)  
  
-   [Reglas para la declaración de constructores](#rules_for_declaring_constructors)  
  
-   [Invocar constructores explícitamente](#explicitly_invoking_constructors)  
  
##  <a name="order_of_construction"></a>Orden de construcción  
 Un constructor realiza su trabajo en este orden:  
  
1.  Llama a los constructores miembros y de clase base en el orden en que se declararon.  
  
2.  Si la clase se deriva de clases base virtuales, inicializa los punteros base virtuales del objeto.  
  
3.  Si la clase tiene o hereda funciones virtuales, inicializa los punteros de funciones virtuales del objeto. Los punteros de funciones virtuales apuntan a la tabla de funciones virtuales de la clase para permitir el enlace correcto de las llamadas de funciones virtuales al código.  
  
4.  Ejecuta cualquier código en el cuerpo de su función.  
  
 En el ejemplo siguiente se muestra el orden en el que los constructores miembros y de clase base se llaman en el constructor para una clase derivada. Primero, se llama al constructor base, después los miembros de la clase base se inicializan en el orden en que aparecen en la declaración de clase y después se llama al constructor derivado.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class Contained1 {  
public:  
    Contained1() {  
        cout << "Contained1 constructor." << endl;  
    }  
};  
  
class Contained2 {  
public:  
    Contained2() {  
        cout << "Contained2 constructor." << endl;  
    }  
};  
  
class Contained3 {  
public:  
    Contained3() {  
        cout << "Contained3 constructor." << endl;  
    }  
};  
  
class BaseContainer {  
public:  
    BaseContainer() {  
        cout << "BaseContainer constructor." << endl;  
    }  
private:  
    Contained1 c1;  
    Contained2 c2;  
};  
  
class DerivedContainer : public BaseContainer {  
public:  
    DerivedContainer() : BaseContainer() {  
        cout << "DerivedContainer constructor." << endl;  
    }  
private:  
    Contained3 c3;  
};  
  
int main() {  
    DerivedContainer dc;  
    int x = 3;  
}  
  
```  
  
 Este es el resultado:  
  
```  
Contained1 constructor.  
Contained2 constructor.  
BaseContainer constructor.  
Contained3 constructor.  
DerivedContainer constructor.  
```  
  
 Si un constructor inicia una excepción, el orden de destrucción es el inverso al orden de la construcción:  
  
1.  El código del cuerpo de la función de constructor se desenredará.  
  
2.  Los objetos miembro y de la clase base se destruirán en el orden inverso de la declaración.  
  
3.  Si el constructor no delega, se destruirán todos los miembros y objetos de clase base totalmente implementados. Sin embargo, dado que el objeto en sí no está totalmente implementado, el destructor no se ejecutará.  
  
##  <a name="member_lists"></a>Listas de miembros  
 Use una lista de inicializadores de miembro{b> <b}para inicializar miembros de clase desde argumentos de constructor. Este método usa *inicialización directa*, que es más eficaz que el uso de operadores de asignación dentro del cuerpo del constructor.  
  
```cpp  
class Box {  
public:  
    Box(int width, int length, int height)   
        : m_width(width), m_length(length), m_height(height) // member init list  
    {}  
    int Volume() {return m_width * m_length * m_height; }  
private:  
    int m_width;  
    int m_length;  
    int m_height;  
  
};  
  
```  
  
 Cree un objeto Box:  
  
```  
Box b(42, 21, 12);  
cout << "The volume is " << b.Volume();  
```  
  
##  <a name="explicit_constructors"></a>Constructores explícitos  
 Si una clase tiene un constructor con un solo parámetro, o si todos los parámetros excepto uno tienen un valor predeterminado, el tipo de parámetro se puede convertir implícitamente en el tipo de clase. Por ejemplo, si la clase `Box` tiene un constructor como este:  
  
```  
Box(int size): m_width(size), m_length(size), m_height(size){}  
```  
  
 Se puede inicializar un objeto Box como este:  
  
```  
Box b = 42;  
```  
  
 O pasar un valor int a una función que toma un objeto Box:  
  
```  
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
  
 Estas conversiones pueden ser útiles en algunos casos, pero lo más habitual es que provoquen errores sutiles, pero graves, en el código. Como regla general, es conveniente usar la palabra clave `explicit` en un constructor (y operadores definidos por el usuario) para evitar este tipo de conversión de tipos implícita:  
  
```  
  
explicit Box(int size): m_width(size), m_length(size), m_height(size){}  
```  
  
 Cuando el constructor es explícito, esta línea provoca un error del compilador: `ShippingOrder so(42, 10.8);`.  Para obtener más información, consulte [conversiones de tipos definidos por el usuario](../cpp/user-defined-type-conversions-cpp.md).  
  
##  <a name="default_constructors"></a>Constructores predeterminados.  
 *Constructores predeterminados* no tienen parámetros, sino que siguen reglas ligeramente distintas:  
  
 Constructores predeterminados son uno de los *funciones miembro especiales*; si se declara ningún constructor en una clase, el compilador proporciona un constructor predeterminado:  
  
```cpp  
class Box {  
    Box(int width, int length, int height)   
        : m_width(width), m_length(length), m_height(height){}  
};  
  
int main(){  
  
    Box box1{}; // call compiler-generated default ctor  
    Box box2;   // call compiler-generated default ctor  
}  
```  
  
 Cuando llama a un constructor predeterminado e intenta utilizar paréntesis, se devuelve una advertencia:  
  
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
    Box(int width, int length, int height)   
        : m_width(width), m_length(length), m_height(height){}  
};  
private:  
    int m_width;  
    int m_length;  
    int m_height;  
  
};  
  
int main(){  
  
    Box box1(1, 2, 3);  
    Box box2{ 2, 3, 4 };  
    Box box4;     // compiler error C2512: no appropriate default constructor available  
}  
  
```  
  
 Si una clase no tiene ningún constructor predeterminado, una matriz de objetos de esa clase no se puede crear únicamente mediante una sintaxis de corchetes. Por ejemplo, dado el bloque de código anterior, no se puede declarar una matriz de marcos como esta:  
  
```cpp  
Box boxes[3];    // compiler error C2512: no appropriate default constructor available  
  
```  
  
 Sin embargo, puede utilizar un conjunto de listas de inicializadores para inicializar una matriz de marcos:  
  
```cpp  
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };  
```  
  
##  <a name="copy_and_move_constructors"></a>Copie y constructores de movimiento  
 A *constructor de copias* es una función miembro especial que toma como entrada una referencia a un objeto del mismo tipo y realiza una copia del mismo. Para obtener más información, consulte [constructores de copias y operadores de asignación de copia (C++)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md). A *constructor de movimiento* también es una función miembro especial que desplaza la posesión de los datos de un objeto existente a una nueva variable sin copiar los datos originales. Para obtener más información, consulte [constructores de movimiento y operadores de asignación de movimiento (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md).  
  
##  <a name="explicitly_defaulted_and_deleted_constructors"></a>Constructores explícitamente establecidos como predeterminados y eliminados  
 Se puede convertir explícitamente *predeterminado* constructores de copias, constructores predeterminados, constructores de movimiento, operadores de asignación de copiar, mover los operadores de asignación y destructores. Se puede convertir explícitamente *eliminar* todas las funciones miembro especiales. Para obtener más información, consulte [explícitamente como valores predeterminados y eliminar funciones](../cpp/explicitly-defaulted-and-deleted-functions.md).  
  
##  <a name="constructors_in_derived_classes"></a>Constructores de clases derivadas  
 Un constructor de clase derivada siempre llama a un constructor de clase base, por lo que se pueden usar clases base completamente construidas antes de realizar cualquier trabajo adicional. Los constructores de clase base se llaman en orden de derivación: por ejemplo, si ClassA se deriva de ClassB, que se deriva de ClassC, se llama primero al constructor de ClassC, después al constructor de ClassB y, por último, al constructor de ClassA.  
  
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
  
### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>Constructores de clases que tienen herencia múltiple  
 Si una clase se deriva de varias clases base, los constructores de clase base se invocan en el orden en que se muestran en la declaración de la clase derivada:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class BaseClass1 {  
public:  
    BaseClass1() {  
        cout << "BaseClass1 constructor." << endl;  
    }  
};  
class BaseClass2 {  
public:  
    BaseClass2() {  
        cout << "BaseClass2 constructor." << endl;  
    }  
};  
class BaseClass3{  
public:  
    BaseClass3() {  
        cout << "BaseClass3 constructor." << endl;  
    }  
};  
class DerivedClass : public BaseClass1, public BaseClass2, public BaseClass3  {  
public:  
    DerivedClass() {  
        cout << "DerivedClass constructor." << endl;  
    }  
};  
  
int main() {  
    DerivedClass dc;  
}  
  
```  
  
 Debería esperar los siguientes resultados:  
  
```  
BaseClass1 constructor.  
BaseClass2 constructor.  
BaseClass3 constructor.  
DerivedClass constructor.  
```  
  
##  <a name="virtual_functions_in_constructors"></a>Funciones virtuales en constructores  
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
  
```  
BaseClass print_it  
Derived Class print_it  
```  
  
##  <a name="constructors_in_composite_classes"></a>Clases de constructores y compuestas  
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
  
##  <a name="delegating_constructors"></a>Delegación de constructores  
 A *constructor que delega* llama a un constructor diferente en la misma clase para realizar algunas de las tareas de inicialización. En el ejemplo siguiente, la clase derivada tiene tres constructores: el segundo constructor delega en el primero, y el tercero delega en el segundo:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class ConstructorDestructor {  
public:  
    ConstructorDestructor() {  
        cout << "ConstructorDestructor default constructor." << endl;  
    }  
    ConstructorDestructor(int int1) {  
        cout << "ConstructorDestructor constructor with 1 int." << endl;  
    }  
    ConstructorDestructor(int int1, int int2) : ConstructorDestructor(int1) {  
        cout << "ConstructorDestructor constructor with 2 ints." << endl;  
  
        throw exception();  
    }  
    ConstructorDestructor(int int1, int int2, int int3) : ConstructorDestructor(int1, int2) {  
        cout << "ConstructorDestructor constructor with 3 ints." << endl;  
    }  
    ~ConstructorDestructor() {  
        cout << "ConstructorDestructor destructor." << endl;  
    }  
};  
  
int main() {  
    ConstructorDestructor dc(1, 2, 3);  
}  
  
```  
  
 Este es el resultado:  
  
```  
ConstructorDestructor constructor with 1 int.  
ConstructorDestructor constructor with 2 ints.  
ConstructorDestructor constructor with 3 ints.  
```  
  
 El objeto creado por los constructores se inicializa totalmente en cuanto finaliza cualquiera de los constructores. `DerivedContainer(int int1)` es correcto, pero `DerivedContainer(int int1, int int2)` produce un error y se llama al destructor.  
  
```cpp  
class ConstructorDestructor {  
public:  
    ConstructorDestructor() {  
        cout << "ConstructorDestructor default constructor." << endl;  
    }  
    ConstructorDestructor(int int1) {  
        cout << "ConstructorDestructor constructor with 1 int." << endl;  
    }  
    ConstructorDestructor(int int1, int int2) : ConstructorDestructor(int1) {  
        cout << "ConstructorDestructor constructor with 2 ints." << endl;  
        throw exception();  
    }  
    ConstructorDestructor(int int1, int int2, int int3) : ConstructorDestructor(int1, int2) {  
        cout << "ConstructorDestructor constructor with 3 ints." << endl;  
    }  
  
    ~ConstructorDestructor() {  
        cout << "ConstructorDestructor destructor." << endl;  
    }  
};  
  
int main() {  
  
    try {  
        ConstructorDestructor cd{ 1, 2, 3 };  
    }  
    catch (const exception& ex){  
    }  
}  
  
```  
  
 Resultado:  
  
```  
ConstructorDestructor constructor with 1 int.  
ConstructorDestructor constructor with 2 ints.  
ConstructorDestructor destructor.  
```  
  
 Para obtener más información, consulte [inicialización uniforme y constructores de delegación](../cpp/uniform-initialization-and-delegating-constructors.md).  
  
##  <a name="inheriting_constructors"></a>Constructores que heredan (C ++ 11)  
 Una clase derivada puede heredar los constructores de una clase base directa, para lo cual utiliza una declaración using, como se muestra en el ejemplo siguiente:  
  
```  
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
  
int main(int argc, char argv[])  
{  
    cout << "Derived d1(5) calls: ";   
    Derived d1(5);  
    cout << "Derived d1('c') calls: ";  
    Derived d2('c');  
    cout << "Derived d3 = d2 calls: " ;  
    Derived d3 = d2;  
    cout << "Derived d4 calls: ";  
    Derived d4;   
  
    // Keep console open in debug mode:  
    cout << endl << "Press Enter to exit.";  
    char in[1];  
    cin.getline(in, 1);  
    return 0;  
}  
  
/* Output:  
Derived d1(5) calls: Base(int)  
Derived d1('c') calls: Base(char)  
Derived d3 = d2 calls: Base(Base&)  
Derived d4 calls: Base()  
  
Press Enter to exit.  
  
```  
  
 La instrucción using incluye en el ámbito a todos los constructores de la clase base, excepto los que tienen una firma idéntica a los constructores de la clase derivada. En general, es mejor usar constructores que heredan cuando la clase derivada no declara ningún constructor o miembro de datos nuevo.  
  
 Una plantilla de clase puede heredar todos los constructores de un argumento de tipo si dicho tipo especifica una clase base:  
  
```  
template< typename T >  
class Derived : T {  
    using T::T;   // declare the constructors from T  
    // ...  
};  
  
```  
  
 Una clase derivada no puede heredar de varias clases base si esas clases base tienen constructores con una firma idéntica.  
  
##  <a name="rules_for_declaring_constructors"></a>Reglas para la declaración de constructores  
 Un constructor tiene el mismo nombre que su clase. Se puede declarar cualquier número de constructores, de acuerdo con las reglas de las funciones sobrecargadas.  
  
 La `argument-declaration-list` puede estar vacía.  
  
 C++ define dos tipos especiales de constructores, constructores predeterminados y de copias, que se describen en la siguiente tabla.  
  
### <a name="default-and-copy-constructors"></a>Constructores predeterminados y de copias  
  
|Clase de construcción|Argumentos|Finalidad|  
|--------------------------|---------------|-------------|  
|Constructor predeterminado|Se puede llamar sin argumentos|Crear un objeto predeterminado del tipo de clase|  
|Constructor de copias|Puede aceptar un solo argumento de referencia al mismo tipo de clase|Copiar objetos del tipo de clase|  
  
 Los constructores predeterminados se pueden llamar sin argumentos. Sin embargo, puede declarar un constructor predeterminado con una lista de argumentos, siempre que todos los argumentos tengan valores predeterminados. De igual forma, los constructores de copias deben aceptar un único argumento de referencia al mismo tipo de clase. Se pueden proporcionar más argumentos, siempre que todos los demás argumentos tengan valores predeterminados.  
  
 Si no proporciona ningún constructor, el compilador intenta generar un constructor predeterminado. Si no proporciona un constructor de copias, el compilador intenta generar uno. Estos constructores generados por el compilador se consideran funciones miembro públicas. Si especifica un constructor de copias con un primer argumento que es un objeto y no una referencia se genera un error.  
  
 Un constructor predeterminado generado por el compilador configura el objeto (inicializa las vftables y vbtables, tal como se ha descrito anteriormente) y llama a los constructores predeterminados de las clases base y miembros, pero no realiza ninguna otra acción. Los constructores miembro y de clase base solo se llaman si existen, están accesibles y no son ambiguos.  
  
 Un constructor generado por el compilador configura un nuevo objeto y realiza una copia miembro a miembro del contenido del objeto que se va a copiar. Si existen constructores miembro o de clase base, se llaman; de lo contrario, se realiza una copia bit a bit.  
  
 Si todas las clases base y miembro de una clase `type` tienen constructores de copias que aceptan un **const** argumento, el constructor de copias generado por el compilador acepta un único argumento de tipo **const** `type` **&**. En caso contrario, el constructor de copias generado por el compilador acepta un único argumento de tipo `type` ** & **.  
  
 Puede utilizar un constructor para inicializar una **const** o `volatile` objeto, pero el constructor en sí no se pueden declarar como **const** o `volatile`. La clase de almacenamiento válida solo para un constructor es **en línea**; el uso de cualquier otro modificador de clase de almacenamiento, incluido el `__declspec` (palabra clave), con un constructor produce un error del compilador.  
  
 La convención de llamada stdcall se usa en funciones miembro estáticas y funciones globales declaradas con el **__stdcall** palabra clave que no usan una lista de argumentos de variable. Cuando se usa el **__stdcall** palabra clave en una función miembro no estática, por ejemplo, un constructor, el compilador usa la convención de llamada thiscall. "  
  
 Las clases derivadas no heredan los constructores de clases base. Cuando se crea un objeto de tipo de clase derivada, se construye empezando por los componentes de la clase base; a continuación, se pasa a los componentes de la clase derivada. El compilador utiliza el constructor de cada clase base cuando se inicializa esa parte del objeto completo (excepto en casos de derivación virtual.  
  
##  <a name="explicitly_invoking_constructors"></a>Invocar constructores explícitamente  
 Se puede llamar a los constructores explícitamente en un programa para crear objetos de un tipo determinado. Por ejemplo, para crear dos objetos `Point` que describen los extremos de una línea, se puede escribir el código siguiente:  
  
```  
DrawLine( Point( 13, 22 ), Point( 87, 91 ) );  
```  
  
 Se crean dos objetos de tipo `Point`, se pasan a la función `DrawLine` y se destruyen al final de la expresión (la llamada a función).  
  
 Otro contexto en el que se llama explícitamente a un constructor está en una inicialización:  
  
```  
Point pt = Point( 7, 11 );  
```  
  
 Un objeto de tipo `Point` se crea y se inicializa con el constructor que acepta dos argumentos de tipo `int`.  
  
 Los objetos creados mediante una llamada explícita a los constructores, como en los dos ejemplos anteriores, no tienen nombre y tienen la duración de la expresión en la que se crearon. Esto se explica con más detalle en [objetos temporales](../cpp/temporary-objects.md).  
  
 Normalmente es seguro llamar a la función miembro dentro de un constructor porque el objeto se ha configurado completamente (las tablas virtuales se han inicializado, etc.) antes de la ejecución de la primera línea de código de usuario. Sin embargo, puede que no sea seguro que una función miembro llame a una función miembro virtual de una clase base abstracta durante la construcción o destrucción.  
  
 Los constructores pueden llamar a funciones virtuales. Cuando se llama a funciones virtuales, la función invocada es la función definida para la clase propia del constructor (o heredada de sus bases). En el ejemplo siguiente se muestra lo que ocurre cuando se llama a una función virtual desde dentro de un constructor:  
  
```  
// specl_calling_virtual_functions.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class Base  
{  
public:  
    Base();             // Default constructor.  
    virtual void f();   // Virtual member function.  
};  
  
Base::Base()  
{  
    cout << "Constructing Base sub-object\n";  
    f();                // Call virtual member function  
}                       //  from inside constructor.  
  
void Base::f()  
{  
    cout << "Called Base::f()\n";  
}  
  
class Derived : public Base  
{  
public:  
    Derived();          // Default constructor.  
    void f();           // Implementation of virtual  
};                      //  function f for this class.  
  
Derived::Derived()  
{  
    cout << "Constructing Derived object\n";  
}  
  
void Derived::f()  
{  
    cout << "Called Derived::f()\n";  
}  
  
int main()  
{  
    Derived d;  
}  
```  
  
 Cuando se ejecuta el programa anterior, la declaración `Derived d` produce la siguiente secuencia de eventos:  
  
1.  Se llama al constructor para la clase `Derived` (`Derived::Derived`).  
  
2.  Antes de escribir el cuerpo del constructor de la clase `Derived`, se llama al constructor de la clase `Base` (`Base::Base`).  
  
 `Base::Base` llama a la función `f`, que es una función virtual. Normalmente se llamaría a `Derived::f`, porque el objeto `d` es de tipo `Derived`. Dado que la función `Base::Base` es un constructor, el objeto no es todavía de tipo `Derived` y se llama a `Base::f`.  
  

