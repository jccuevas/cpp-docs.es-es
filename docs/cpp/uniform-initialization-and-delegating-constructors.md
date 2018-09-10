---
title: Uniforme de inicialización y constructores de delegación | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: aa4daa64-eaec-4a3c-ade4-d9325e31e9d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f985d206a342611dfccb4f05347b0ecc9e9521b0
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314665"
---
# <a name="uniform-initialization-and-delegating-constructors"></a>Inicialización uniforme y constructores de delegación
En C++ moderno, puede usar *la inicialización de llave* para cualquier tipo, sin el signo igual. Además, se puede utilizar la delegación de constructores para simplificar el código cuando hay varios constructores que realizan un trabajo similar.

## <a name="brace-initialization"></a>Inicialización de llave
La inicialización de llave se puede utilizar para cualquier clase, struct o unión. Si un tipo tiene un constructor predeterminado, ya esté declarado de forma implícita o de forma explícita, puede utilizar la inicialización de llave predeterminada (con las llaves vacías). Por ejemplo, la siguiente clase puede inicializarse mediante la inicialización de llave predeterminada y la no predeterminada:

```cpp
#include <string>
using namespace std;

class class_a {
public:
    class_a() {}
    class_a(string str) : m_string{ str } {}
    class_a(string str, double dbl) : m_string{ str }, m_double{ dbl } {}
double m_double;
string m_string;
};

int main()
{
    class_a c1{};
    class_a c1_1;

    class_a c2{ "ww" };
    class_a c2_1("xx");

    // order of parameters is the same as the constructor
    class_a c3{ "yy", 4.4 };
    class_a c3_1("zz", 5.5);
}
```

Si una clase tiene constructores no predeterminados, el orden en que los miembros de clase aparecen en el inicializador de llave es aquel en que aparecen los parámetros correspondientes en el constructor, no el orden en que se declaran los miembros (como ocurre con `class_a` en el ejemplo anterior). De lo contrario, si el tipo no tiene ningún constructor declarado, el orden en que los miembros aparecen en el inicializador de llave es el mismo que el orden en que se declararon; en este caso, puede inicializar tantos miembros públicos como desee, pero no puede omitir ningún miembro. En el ejemplo siguiente se muestra el orden que se utiliza en la inicialización de llave cuando no hay un constructor declarado:

```cpp
class class_d {
public:
    float m_float;
    string m_string;
    wchar_t m_char;
};

int main()
{
    class_d d1{};
    class_d d1{ 4.5 };
    class_d d2{ 4.5, "string" };
    class_d d3{ 4.5, "string", 'c' };

    class_d d4{ "string", 'c' }; // compiler error
    class_d d5("string", 'c', 2.0 }; // compiler error
}
```

Si el constructor predeterminado se declara explícitamente pero se marca como eliminado, no se puede utilizar la inicialización de llave predeterminada:

```cpp
class class_f {
public:
    class_f() = delete;
    class_f(string x): m_string { x } {}
    string m_string;
};
int main()
{
    class_f cf{ "hello" };
    class_f cf1{}; // compiler error C2280: attempting to reference a deleted function
}
```

Puede usar la inicialización de llave en cualquier parte se suele realizar la inicialización, por ejemplo, como un parámetro de función o un valor devuelto, o con el **nuevo** palabra clave:

```cpp
class_d* cf = new class_d{4.5};
kr->add_d({ 4.5 });
return { 4.5 };
```

## <a name="initializerlist-constructors"></a>Constructores initializer_list
El [initializer_list (clase)](../standard-library/initializer-list-class.md) representa una lista de objetos de un tipo especificado que se puede usar en un constructor y en otros contextos. Puede construir initializer_list mediante la inicialización de llave:

```cpp
initializer_list<int> int_list{5, 6, 7};
```

> [!IMPORTANT]
>  Para usar esta clase, se debe incluir el [ \<initializer_list >](../standard-library/initializer-list.md) encabezado.

`initializer_list` puede copiarse. En este caso, los miembros de la nueva lista son referencias a los miembros de la lista original:

```cpp
initializer_list<int> ilist1{ 5, 6, 7 };
initializer_list<int> ilist2( ilist1 );
if (ilist1.begin() == ilist2.begin())
    cout << "yes" << endl; // expect "yes"
```

Las clases contenedoras de la biblioteca estándar y `string`, `wstring` y `regex`, tienen constructores `initializer_list`. En los ejemplos siguientes se muestra cómo realizar la inicialización de llave con estos constructores:

```cpp
vector<int> v1{ 9, 10, 11 };
map<int, string> m1{ {1, "a"}, {2, "b"} };
string s{ 'a', 'b', 'c' };
regex rgx{'x', 'y', 'z'};
```

## <a name="delegating-constructors"></a>Constructores que delegan
Muchas clases tienen varios constructores que realizan acciones similares, por ejemplo, validan parámetros:

```cpp
class class_c {
public:
    int max;
    int min;
    int middle;

    class_c() {}
    class_c(int my_max) {
        max = my_max > 0 ? my_max : 10;
    }
    class_c(int my_max, int my_min) {
        max = my_max > 0 ? my_max : 10;
        min = my_min > 0 && my_min < max ? my_min : 1;
    }
    class_c(int my_max, int my_min, int my_middle) {
        max = my_max > 0 ? my_max : 10;
        min = my_min > 0 && my_min < max ? my_min : 1;
        middle = my_middle < max && my_middle > min ? my_middle : 5;
    }
};
```

Puede reducir el código repetitivo si agrega una función que realice toda la validación, pero el código de `class_c` sería más fácil de entender y mantener si un constructor pudiera delegar alguna parte del trabajo en otro. Para agregar la delegación de constructores, utilice la sintaxis `constructor (. . .) : constructor (. . .)`:

```cpp
class class_c {
public:
    int max;
    int min;
    int middle;

    class_c(int my_max) {
        max = my_max > 0 ? my_max : 10;
    }
    class_c(int my_max, int my_min) : class_c(my_max) {
        min = my_min > 0 && my_min < max ? my_min : 1;
    }
    class_c(int my_max, int my_min, int my_middle) : class_c (my_max, my_min){
        middle = my_middle < max && my_middle > min ? my_middle : 5;
}
};
int main() {

    class_c c1{ 1, 3, 2 };
}
```

A medida que recorra paso a paso el ejemplo anterior, observe que el constructor `class_c(int, int, int)` llama primero al constructor `class_c(int, int)`, que a su vez llama a `class_c(int)`. Cada uno de los constructores realiza solo el trabajo que no realizan los otros constructores.

El primer constructor al que se llama inicializa el objeto para que todos sus miembros se inicialicen en ese momento. No se puede realizar la inicialización de miembro en un constructor que delega en otro constructor, tal como se muestra aquí:

```cpp
class class_a {
public:
    class_a() {}
    // member initialization here, no delegate
    class_a(string str) : m_string{ str } {}

    //can’t do member initialization here
    // error C3511: a call to a delegating constructor shall be the only member-initializer
    class_a(string str, double dbl) : class_a(str) , m_double{ dbl } {}

    // only member assignment
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }
    double m_double{ 1.0 };
    string m_string;
};
```

En el ejemplo siguiente se muestra el uso de los inicializadores de miembro de datos no estático. Observe que, si un constructor inicializa también un miembro de datos determinado, el inicializador de miembro se invalida:

```cpp
class class_a {
public:
    class_a() {}
    class_a(string str) : m_string{ str } {}
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }
    double m_double{ 1.0 };
    string m_string{ m_double < 10.0 ? "alpha" : "beta" };
};

int main() {
    class_a a{ "hello", 2.0 };  //expect a.m_double == 2.0, a.m_string == "hello"
    int y = 4;
}
```

La sintaxis de delegación de constructores no impide la creación accidental de recursividad de constructores (el Constructor1 llama al Constructor2, que llama al Constructor1) y no se genera ningún error hasta que se produzca un desbordamiento de pila. Es responsabilidad del programador evitar los ciclos.

```cpp
class class_f{
public:
    int max;
    int min;

    // don't do this
    class_f() : class_f(6, 3){ }
    class_f(int my_max, int my_min) : class_f() { }
};
```