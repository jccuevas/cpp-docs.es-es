---
title: Plantillas (C++)
ms.date: 12/27/2019
f1_keywords:
- template_cpp
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
ms.openlocfilehash: e47f00c7e387974c7d1756cf3ee3865f892e6951
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032348"
---
# <a name="templates-c"></a>Plantillas (C++)

Las plantillas son la base para la programación genérica en C++. Como lenguaje fuertemente tipado, C++ requiere que todas las variables tengan un tipo específico, ya sea declarado explícitamente por el programador o deducido por el compilador. Sin embargo, muchas estructuras de datos y algoritmos tienen el mismo aspecto sin importar en qué tipo estén operando. Las plantillas permiten definir las operaciones de una clase o función y permiten al usuario especificar en qué tipos concretos deben trabajar esas operaciones.

## <a name="defining-and-using-templates"></a>Definición y uso de plantillas

Una plantilla es una construcción que genera un tipo o función normal en tiempo de compilación en función de los argumentos que el usuario proporciona para los parámetros de plantilla. Por ejemplo, puede definir una plantilla de función como esta:

```cpp
template <typename T>
T minimum(const T& lhs, const T& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

El código anterior describe una plantilla para una función genérica con un parámetro de tipo único *T*, cuyo valor devuelto y parámetros de llamada (lhs y rhs) son todos de este tipo. Puede asignar un nombre a un parámetro de tipo lo que desee, pero por convención se utilizan más comúnmente letras mayúsculas. *T* es un parámetro de plantilla; la palabra clave **typename** indica que este parámetro es un marcador de posición para un tipo. Cuando se llama a la función, `T` el compilador reemplazará cada instancia del argumento de tipo concreto especificado por el usuario o deducido por el compilador. El proceso en el que el compilador genera una clase o función a partir de una plantilla se conoce como creación de instancias de *plantilla;* `minimum<int>` es una creación de `minimum<T>`instancias de la plantilla.

En otros lugares, un usuario puede declarar una instancia de la plantilla especializada para int. Supongamos que get_a() y get_b() son funciones que devuelven un int:

```cpp
int a = get_a();
int b = get_b();
int i = minimum<int>(a, b);
```

Sin embargo, dado que se trata de `T` una plantilla de función y el compilador puede deducir el tipo de de los argumentos *a* y *b*, puede llamarlo como una función normal:

```cpp
int i = minimum(a, b);
```

Cuando el compilador encuentra la última instrucción, genera una nueva función en la que cada aparición de *T* en la plantilla se reemplaza por **int**:

```cpp
int minimum(const int& lhs, const int& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

Las reglas de cómo el compilador realiza la deducción de tipos en plantillas de función se basan en las reglas para las funciones normales. Para obtener más información, consulte [Resolución de sobrecarga de llamadas](../cpp/overload-resolution-of-function-template-calls.md)a plantillas de función .

## <a name="type-parameters"></a><a id="type_parameters"></a>Parámetros de tipo

En `minimum` la plantilla anterior, tenga en cuenta que el parámetro de tipo *T* no está calificado de ninguna manera hasta que se utiliza en los parámetros de llamada de función, donde se agregan los calificadores const y reference.

No hay un límite práctico para el número de parámetros de tipo. Separe varios parámetros por comas:

```cpp
template <typename T, typename U, typename V> class Foo{};
```

La **clase** de palabra clave es equivalente a **typename** en este contexto. Puede expresar el ejemplo anterior como:

```cpp
template <class T, class U, class V> class Foo{};
```

Puede usar el operador de puntos suspensivos (...) para definir una plantilla que toma un número arbitrario de cero o más parámetros de tipo:

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
```

Cualquier tipo integrado o definido por el usuario se puede utilizar como argumento de tipo. Por ejemplo, puede utilizar [std::vector](../standard-library/vector-class.md) en la biblioteca estándar para almacenar variables de tipo `MyClass` **int**, **double**, [std::string](../standard-library/basic-string-class.md), **const** `MyClass`*, `MyClass&`, etc. La restricción principal cuando se usan plantillas es que un argumento de tipo debe admitir las operaciones que se aplican a los parámetros de tipo. Por ejemplo, si `minimum` `MyClass` llamamos a using como en este ejemplo:

```cpp
class MyClass
{
public:
    int num;
    std::wstring description;
};

int main()
{
    MyClass mc1 {1, L"hello"};
    MyClass mc2 {2, L"goodbye"};
    auto result = minimum(mc1, mc2); // Error! C2678
}
```

Se generará un error `MyClass` del compilador porque no **<** proporciona una sobrecarga para el operador.

No hay ningún requisito inherente de que los argumentos de tipo para cualquier plantilla determinada pertenezcan a la misma jerarquía de objetos, aunque puede definir una plantilla que aplique dicha restricción. Puede combinar técnicas orientadas a objetos con plantillas; por ejemplo, puede almacenar un Derived* en un vector\<Base\*>.    Tenga en cuenta que los argumentos deben ser punteros

```cpp
vector<MyClass*> vec;
   MyDerived d(3, L"back again", time(0));
   vec.push_back(&d);

   // or more realistically:
   vector<shared_ptr<MyClass>> vec2;
   vec2.push_back(make_shared<MyDerived>());
```

Los requisitos `std::vector` básicos que y otros `T` contenedores de biblioteca estándar imponen a los elementos son que `T` son asignables por copia y reconstruibles por copia.

## <a name="non-type-parameters"></a>Parámetros que no son de tipo

A diferencia de los tipos genéricos en otros lenguajes, como C- y Java, las plantillas C++ admiten *parámetros que no*son de tipo, también denominados parámetros de valor. Por ejemplo, puede proporcionar un valor entero constante para especificar la longitud de una matriz, como con este ejemplo que es similar a la clase [std::array](../standard-library/array-class-stl.md) en la biblioteca estándar:

```cpp
template<typename T, size_t L>
class MyArray
{
    T arr[L];
public:
    MyArray() { ... }
};
```

Observe la sintaxis en la declaración de plantilla. El `size_t` valor se pasa como un argumento de plantilla en tiempo de compilación y debe ser **const** o una expresión **constexpr.** Lo usas así:

```cpp
MyArray<MyClass*, 10> arr;
```

Otros tipos de valores, incluidos punteros y referencias, se pueden pasar como parámetros que no son de tipo. Por ejemplo, puede pasar un puntero a una función o un objeto de función para personalizar alguna operación dentro del código de plantilla.

### <a name="type-deduction-for-non-type-template-parameters"></a>Deducción de tipos para parámetros de plantilla que no son de tipo

En Visual Studio 2017 y versiones posteriores, en el modo **/std:c++17,** el compilador deduce el tipo de un argumento de plantilla que no es de tipo que se declara con **auto:**

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

## <a name="templates-as-template-parameters"></a><a id="template_parameters"></a>Plantillas como parámetros de plantilla

Una plantilla puede ser un parámetro de plantilla. En este ejemplo, MyClass2 tiene dos parámetros de plantilla: un parámetro de nombre de tipo *T* y un parámetro de plantilla *Arr:*

```cpp
template<typename T, template<typename U, int I> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
    U u; //Error. U not in scope
};
```

Dado que el propio parámetro *Arr* no tiene ningún cuerpo, sus nombres de parámetro no son necesarios. De hecho, es un error hacer referencia a los nombres de parámetro `MyClass2`de clase o nombre de tipo de *Arr*desde el cuerpo de . Por esta razón, los nombres de parámetro de tipo *de Arr*se pueden omitir, como se muestra en este ejemplo:

```cpp
template<typename T, template<typename, int> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
};
```

## <a name="default-template-arguments"></a>Argumentos de plantilla predeterminados

Las plantillas de clase y función pueden tener argumentos predeterminados. Cuando una plantilla tiene un argumento predeterminado, puede dejarla sin especificar cuando la utilice. Por ejemplo, la plantilla std::vector tiene un argumento predeterminado para el asignador:

```cpp
template <class T, class Allocator = allocator<T>> class vector;
```

En la mayoría de los casos, la clase std::allocator predeterminada es aceptable, por lo que se utiliza un vector como este:

```cpp
vector<int> myInts;
```

Pero si es necesario, puede especificar un asignador personalizado como este:

```cpp
vector<int, MyAllocator> ints;
```

Para varios argumentos de plantilla, todos los argumentos después del primer argumento predeterminado deben tener argumentos predeterminados.

Cuando utilice una plantilla cuyos parámetros estén predeterminados, utilice corchetes angulares vacíos:

```cpp
template<typename A = int, typename B = double>
class Bar
{
    //...
};
...
int main()
{
    Bar<> bar; // use all default type arguments
}
```

## <a name="template-specialization"></a>Especialización de plantilla

En algunos casos, no es posible ni deseable que una plantilla defina exactamente el mismo código para cualquier tipo. Por ejemplo, es posible que desee definir una ruta de acceso de código que se ejecutará solo si el argumento type es un puntero, o un std::wstring, o un tipo derivado de una clase base determinada.  En tales casos, puede definir una *especialización* de la plantilla para ese tipo en particular. Cuando un usuario crea una instancia de la plantilla con ese tipo, el compilador usa la especialización para generar la clase y, para todos los demás tipos, el compilador elige la plantilla más general. Las especializaciones en las que todos los parámetros están especializados son *especializaciones completas.* Si sólo algunos de los parámetros están especializados, se denomina *especialización parcial.*

```cpp
template <typename K, typename V>
class MyMap{/*...*/};

// partial specialization for string keys
template<typename V>
class MyMap<string, V> {/*...*/};
...
MyMap<int, MyClass> classes; // uses original template
MyMap<string, MyClass> classes2; // uses the partial specialization
```

Una plantilla puede tener cualquier número de especializaciones siempre que cada parámetro de tipo especializado sea único. Solo las plantillas de clase pueden estar parcialmente especializadas. Todas las especializaciones completas y parciales de una plantilla deben declararse en el mismo espacio de nombres que la plantilla original.

Para obtener más información, consulte [Especialización de plantillas](../cpp/template-specialization-cpp.md).
