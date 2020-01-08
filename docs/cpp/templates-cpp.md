---
title: Plantillas (C++)
ms.date: 12/27/2019
f1_keywords:
- template_cpp
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
ms.openlocfilehash: 36ada3cc3b933e99e9b29b3b58463f6bc526fc7d
ms.sourcegitcommit: 00f50ff242031d6069aa63c81bc013e432cae0cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/30/2019
ms.locfileid: "75546411"
---
# <a name="templates-c"></a>Plantillas (C++)

Las plantillas son la base para la programación C++genérica en. Como lenguaje fuertemente tipado, C++ requiere que todas las variables tengan un tipo específico, declarado explícitamente por el programador o deducido por el compilador. Sin embargo, muchas estructuras de datos y algoritmos tienen el mismo aspecto, independientemente del tipo en el que estén trabajando. Las plantillas le permiten definir las operaciones de una clase o función y permitir que el usuario especifique en qué tipos concretos deben funcionar esas operaciones.

## <a name="defining-and-using-templates"></a>Definir y usar plantillas

Una plantilla es una construcción que genera un tipo o una función ordinarios en tiempo de compilación basándose en los argumentos que el usuario proporciona para los parámetros de plantilla. Por ejemplo, puede definir una plantilla de función similar a la siguiente:

```cpp
template <typename T>
T minimum(const T& lhs, const T& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

En el código anterior se describe una plantilla para una función genérica con un solo parámetro de tipo *T*, cuyo valor devuelto y los parámetros de llamada (LHS y RHS) son todo este tipo. Puede asignar el nombre que desee a un parámetro de tipo, pero por Convención se usa con más frecuencia las mayúsculas y minúsculas. *T* es un parámetro de plantilla; la palabra clave **TypeName** indica que este parámetro es un marcador de posición para un tipo. Cuando se llama a la función, el compilador reemplazará cada instancia de `T` por el argumento de tipo concreto especificado por el usuario o deducido por el compilador. El proceso en el que el compilador genera una clase o función a partir de una plantilla se denomina *creación de instancias de plantilla*. `minimum<int>` es una creación de instancias de la plantilla `minimum<T>`.

En cualquier otro lugar, un usuario puede declarar una instancia de la plantilla especializada en int. suponga que get_a () y get_b () son funciones que devuelven un valor int:

```cpp
int a = get_a();
int b = get_b();
int i = minimum<int>(a, b);
```

Sin embargo, dado que se trata de una plantilla de función y el compilador puede deducir el tipo de `T` a partir de los argumentos *a* y *b*, puede llamarlo como una función normal:

```cpp
int i = minimum(a, b);
```

Cuando el compilador encuentra la última instrucción, genera una nueva función en la que todas las apariciones de *T* de la plantilla se reemplazan por **int**:

```cpp
int minimum(const int& lhs, const int& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

Las reglas para el modo en que el compilador realiza la deducción de tipos en las plantillas de función se basan en las reglas de las funciones ordinarias. Para obtener más información, consulte la [resolución de sobrecarga de llamadas de plantilla de función](../cpp/overload-resolution-of-function-template-calls.md).

## <a id="type_parameters"></a>Parámetros de tipo

En la plantilla `minimum` anterior, tenga en cuenta que el parámetro de tipo *t* no se califica de ningún modo hasta que se use en los parámetros de llamada de función, donde se agregan los calificadores const y Reference.

No hay ningún límite práctico para el número de parámetros de tipo. Separe varios parámetros por comas:

```cpp
template <typename T, typename U, typename V> class Foo{};
```

La **clase** keyword es equivalente a **TypeName** en este contexto. Puede expresar el ejemplo anterior como:

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

Cualquier tipo integrado o definido por el usuario se puede usar como un argumento de tipo. Por ejemplo, puede usar [STD:: Vector](../standard-library/vector-class.md) en la biblioteca estándar para almacenar variables de tipo **int**, **Double**, [STD:: String](../standard-library/basic-string-class.md), `MyClass`, **const** `MyClass`*, `MyClass&`, etc. La restricción principal cuando se usan plantillas es que un argumento de tipo debe admitir las operaciones que se aplican a los parámetros de tipo. Por ejemplo, si llamamos a `minimum` mediante `MyClass` como en este ejemplo:

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

Se generará un error del compilador porque `MyClass` no proporciona una sobrecarga para el operador **<** .

No es necesario que los argumentos de tipo de ninguna plantilla determinada pertenezcan a la misma jerarquía de objetos, aunque se puede definir una plantilla que aplique este tipo de restricción. Puede combinar técnicas orientadas a objetos con plantillas; por ejemplo, puede almacenar un * derivado en un vector\<base\*>.    Tenga en cuenta que los argumentos deben ser punteros

```cpp
vector<MyClass*> vec;
   MyDerived d(3, L"back again", time(0));
   vec.push_back(&d);

   // or more realistically:
   vector<shared_ptr<MyClass>> vec2;
   vec2.push_back(make_shared<MyDerived>());
```

Los requisitos básicos que `std::vector` y otros contenedores de la biblioteca estándar imponen los elementos de `T` es que `T` ser de copia, asignable y copiable.

## <a name="non-type-parameters"></a>Parámetros sin tipo

A diferencia de los tipos genéricos en otros C# lenguajes como C++ y Java, las plantillas admiten *parámetros sin tipo*, también denominados parámetros de valor. Por ejemplo, puede proporcionar un valor entero constante para especificar la longitud de una matriz, como en este ejemplo, que es similar a la clase [STD:: Array](../standard-library/array-class-stl.md) de la biblioteca estándar:

```cpp
template<typename T, size_t L>
class MyArray
{
    T arr[L];
public:
    MyArray() { ... }
};
```

Observe la sintaxis de la declaración de plantilla. El valor `size_t` se pasa como argumento de plantilla en tiempo de compilación y debe ser **const** o una expresión **constexpr** . Se usa del siguiente modo:

```cpp
MyArray<MyClass*, 10> arr;
```

Otros tipos de valores, incluidos los punteros y las referencias, se pueden pasar como parámetros que no son de tipo. Por ejemplo, puede pasar un puntero a una función o a un objeto de función para personalizar alguna operación dentro del código de la plantilla.

### <a name="type-deduction-for-non-type-template-parameters"></a>Deducción de tipos para parámetros de plantilla sin tipo

En Visual Studio 2017 y versiones posteriores, en el modo **/STD: c++ 17** , el compilador deduce el tipo de un argumento de plantilla sin tipo que se declara con **auto**:

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

## <a id="template_parameters"></a>Plantillas como parámetros de plantilla

Una plantilla puede ser un parámetro de plantilla. En este ejemplo, MyClass2 tiene dos parámetros de plantilla: un parámetro TypeName *T* y un parámetro de plantilla *ARR*:

```cpp
template<typename T, template<typename U, int I> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
    U u; //Error. U not in scope
};
```

Dado que el propio parámetro *ARR* no tiene cuerpo, no se necesitan sus nombres de parámetro. De hecho, es un error hacer referencia a los nombres de los parámetros de clase o TypeName de *ARR*desde dentro del cuerpo de `MyClass2`. Por esta razón, se pueden omitir los nombres de parámetro de tipo de *ARR*, tal como se muestra en este ejemplo:

```cpp
template<typename T, template<typename, int> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
};
```

## <a name="default-template-arguments"></a>Argumentos de plantilla predeterminados

Las plantillas de clase y función pueden tener argumentos predeterminados. Cuando una plantilla tiene un argumento predeterminado, puede dejarla sin especificar cuando la utiliza. Por ejemplo, la plantilla STD:: Vector tiene un argumento predeterminado para el asignador:

```cpp
template <class T, class Allocator = allocator<T>> class vector;
```

En la mayoría de los casos, la clase predeterminada STD:: allocator es aceptable, por lo que se usa un vector similar al siguiente:

```cpp
vector<int> myInts;
```

Pero si es necesario, puede especificar un asignador personalizado como el siguiente:

```cpp
vector<int, MyAllocator> ints;
```

Para varios argumentos de plantilla, todos los argumentos después del primer argumento predeterminado deben tener argumentos predeterminados.

Cuando se usa una plantilla cuyos parámetros están configurados de forma predeterminada, use corchetes angulares vacíos:

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

En algunos casos, no es posible o deseable que una plantilla defina exactamente el mismo código para cualquier tipo. Por ejemplo, puede que desee definir una ruta de acceso de código para que se ejecute solo si el argumento de tipo es un puntero, o un STD:: wstring, o un tipo derivado de una clase base determinada.  En tales casos, puede definir una *especialización* de la plantilla para ese tipo en particular. Cuando un usuario crea una instancia de la plantilla con ese tipo, el compilador usa la especialización para generar la clase y para todos los demás tipos, el compilador elige la plantilla más general. Las especializaciones en las que se especializan todos los parámetros son *especializaciones completas*. Si solo algunos de los parámetros están especializados, se denomina *especialización parcial*.

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

Una plantilla puede tener cualquier número de especializaciones siempre que cada parámetro de tipo especializado sea único. Solo las plantillas de clase pueden estar parcialmente especializadas. Todas las especializaciones completas y parciales de una plantilla se deben declarar en el mismo espacio de nombres que la plantilla original.

Para obtener más información, vea [especialización de plantilla](../cpp/template-specialization-cpp.md).