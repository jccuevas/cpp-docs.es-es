---
title: Inicialización de llaves para clases, estructuras y uniones
description: Utilice la inicialización de llaves con cualquier clase, estructura o unión C++
ms.date: 11/19/2019
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
ms.openlocfilehash: 4628ffe8935fc32e86468c631d5d9e9622d63d2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374076"
---
# <a name="brace-initialization"></a>Inicialización de llaves

No siempre es necesario definir un constructor para una clase, especialmente si son relativamente sencillas. Los usuarios pueden inicializar objetos de una clase o struct usando la inicialización uniforme, tal y como se muestra en el siguiente ejemplo:

```cpp
// no_constructor.cpp
// Compile with: cl /EHsc no_constructor.cpp
#include <time.h>

// No constructor
struct TempData
{
    int StationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

// Has a constructor
struct TempData2
{
    TempData2(double minimum, double maximum, double cur, int id, time_t t) :
       stationId{id}, timeSet{t}, current{cur}, maxTemp{maximum}, minTemp{minimum} {}
    int stationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

int main()
{
    time_t time_to_set;

    // Member initialization (in order of declaration):
    TempData td{ 45978, time(&time_to_set), 28.9, 37.0, 16.7 };

    // Default initialization = {0,0,0,0,0}
    TempData td_default{};

    // Uninitialized = if used, emits warning C4700 uninitialized local variable
    TempData td_noInit;

    // Member declaration (in order of ctor parameters)
    TempData2 td2{ 16.7, 37.0, 28.9, 45978, time(&time_to_set) };

    return 0;
}
```

Tenga en cuenta que cuando una clase o estructura no tiene ningún constructor, proporcione los elementos de lista en el orden en que se declaran los miembros en la clase. Si la clase tiene un constructor, proporcione los elementos en el orden de los parámetros. Si un tipo tiene un constructor predeterminado, ya esté declarado de forma implícita o de forma explícita, puede utilizar la inicialización de llave predeterminada (con las llaves vacías). Por ejemplo, la siguiente clase puede inicializarse mediante la inicialización de llave predeterminada y la no predeterminada:

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
    class_d d5{ "string", 'c', 2.0 }; // compiler error
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

Puede utilizar la inicialización de llaves en cualquier lugar donde normalmente haría la inicialización, por ejemplo, como un parámetro de función o un valor devuelto, o con la **nueva** palabra clave:

```cpp
class_d* cf = new class_d{4.5};
kr->add_d({ 4.5 });
return { 4.5 };
```

En el modo **/std:c++17,** las reglas para la inicialización de llaves vacías son ligeramente más restrictivas. Consulte [Constructores derivados e inicialización de agregado extendido.](constructors-cpp.md#extended_aggregate)

## <a name="initializer_list-constructors"></a>constructores initializer_list

El [initializer_list Class](../standard-library/initializer-list-class.md) representa una lista de objetos de un tipo especificado que se pueden usar en un constructor y en otros contextos. Puede construir initializer_list mediante la inicialización de llave:

```cpp
initializer_list<int> int_list{5, 6, 7};
```

> [!IMPORTANT]
> Para utilizar esta clase, debe incluir el [ \<encabezado initializer_list>.](../standard-library/initializer-list.md)

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
regex rgx{ 'x', 'y', 'z' };
```

## <a name="see-also"></a>Consulte también

[Clases y structs](../cpp/classes-and-structs-cpp.md)<br/>
[Constructores](../cpp/constructors-cpp.md)
