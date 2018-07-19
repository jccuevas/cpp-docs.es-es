---
title: Clase map | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- map/std::map
- map/std::map::allocator_type
- map/std::map::const_iterator
- map/std::map::const_pointer
- map/std::map::const_reference
- map/std::map::const_reverse_iterator
- map/std::map::difference_type
- map/std::map::iterator
- map/std::map::key_compare
- map/std::map::key_type
- map/std::map::mapped_type
- map/std::map::pointer
- map/std::map::reference
- map/std::map::reverse_iterator
- map/std::map::size_type
- map/std::map::value_type
- map/std::map::at
- map/std::map::begin
- map/std::map::cbegin
- map/std::map::cend
- map/std::map::clear
- map/std::map::count
- map/std::map::crbegin
- map/std::map::crend
- map/std::map::emplace
- map/std::map::emplace_hint
- map/std::map::empty
- map/std::map::end
- map/std::map::equal_range
- map/std::map::erase
- map/std::map::find
- map/std::map::get_allocator
- map/std::map::insert
- map/std::map::key_comp
- map/std::map::lower_bound
- map/std::map::max_size
- map/std::map::rbegin
- map/std::map::rend
- map/std::map::size
- map/std::map::swap
- map/std::map::upper_bound
- map/std::map::value_comp
dev_langs:
- C++
helpviewer_keywords:
- std::map [C++]
- std::map [C++], allocator_type
- std::map [C++], const_iterator
- std::map [C++], const_pointer
- std::map [C++], const_reference
- std::map [C++], const_reverse_iterator
- std::map [C++], difference_type
- std::map [C++], iterator
- std::map [C++], key_compare
- std::map [C++], key_type
- std::map [C++], mapped_type
- std::map [C++], pointer
- std::map [C++], reference
- std::map [C++], reverse_iterator
- std::map [C++], size_type
- std::map [C++], value_type
- std::map [C++], at
- std::map [C++], begin
- std::map [C++], cbegin
- std::map [C++], cend
- std::map [C++], clear
- std::map [C++], count
- std::map [C++], crbegin
- std::map [C++], crend
- std::map [C++], emplace
- std::map [C++], emplace_hint
- std::map [C++], empty
- std::map [C++], end
- std::map [C++], equal_range
- std::map [C++], erase
- std::map [C++], find
- std::map [C++], get_allocator
- std::map [C++], insert
- std::map [C++], key_comp
- std::map [C++], lower_bound
- std::map [C++], max_size
- std::map [C++], rbegin
- std::map [C++], rend
- std::map [C++], size
- std::map [C++], swap
- std::map [C++], upper_bound
- std::map [C++], value_comp
ms.assetid: 7876f4c9-ebb4-4878-af1e-09364c43af0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40b84e3daac5a1e5574c09e656d39dc774b57031
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027750"
---
# <a name="map-class"></a>map (Clase)

Se utiliza para el almacenamiento y la recuperación de datos de una colección en la que cada elemento es un par que tiene un valor de datos y una clave de ordenación. El valor de la clave es único y se utiliza para ordenar los datos automáticamente.

El valor de un elemento de una asignación se puede cambiar directamente. El valor de clave es una constante y no se puede cambiar. En su lugar, se deben eliminar los valores de clave asociados a los antiguos elementos y se deben insertar nuevos valores de clave para los elementos nuevos.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Key,
    class Type,
    class Traits = less<Key>,
    class Allocator=allocator<pair <const Key, Type>>>
class map;
```

### <a name="parameters"></a>Parámetros

*Clave* escriba los datos de clave que se almacenará en el mapa.

*Tipo* el elemento tipo de datos que se almacenará en el mapa.

*Rasgos* el tipo que proporciona un objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el mapa. Este argumento es opcional y el predicado binario `less<Key>` es el valor predeterminado.

En C++14 puede habilitar la búsqueda heterogénea especificando el predicado std::less<> que no tiene ningún parámetro de tipo. Para obtener más información, vea [Búsqueda heterogénea en los contenedores asociativos](../standard-library/stl-containers.md#sequence_containers).

*Asignador* el tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria de la asignación. Este argumento es opcional y el valor predeterminado es `allocator<pair<const Key, Type> >`.

## <a name="remarks"></a>Comentarios

La clase map de la biblioteca estándar de C++ es:

- Un contenedor de tamaño variable que recupera eficazmente valores de elementos según los valores de clave asociados.

- Reversible, porque proporciona iteradores bidireccionales para tener acceso a sus elementos.

- Ordenada, porque sus elementos se ordenan por valores de clave según una función de comparación especificada.

- Única, ya que cada uno de sus elementos debe tener una clave única.

- Un contenedor asociativo de pares, ya que los valores de datos de sus elementos son distintos de sus valores de clave.

- Una clase de plantilla, porque la funcionalidad que proporciona es genérica e independiente del tipo de elemento o de clave. Los tipos de datos usados para los elementos y las claves se especifican como parámetros en la plantilla de clase junto con la función de comparación y el asignador.

El iterador proporcionado por la clase map es un iterador bidireccional, pero las funciones miembro de clase [insert](#insert) y [map](#map) tienen versiones que toman como parámetros de plantilla un iterador de entrada más débil, cuyos requisitos de funcionalidad son menores que los garantizados por la clase de iteradores bidireccionales. Los distintos conceptos de iterador están relacionados por los refinamientos de su funcionalidad. Cada concepto de iterador tiene su propio conjunto de requisitos y los algoritmos que funcionan con él deben estar limitados por esos requisitos. Un iterador de entrada se puede desreferenciar para hacer referencia a algún objeto e incrementar al iterador siguiente de la secuencia.

Se recomienda elegir el tipo de contenedor según la clase de búsqueda e inserción que necesite la aplicación. Los contenedores asociativos están optimizados para las operaciones de búsqueda, inserción y eliminación. Las funciones miembro que admiten estas operaciones explícitamente las realizan en una tiempo de caso peor que es proporcional al logaritmo del número de elementos del contenedor. La inserción de elementos no invalida ningún iterador y al quitar elementos solo se invalidan los iteradores que habían apuntado específicamente a los elementos quitados.

Se recomienda que el mapa sea el contenedor asociativo preferido si la aplicación satisface las condiciones que asocian valores a claves. Un modelo para este tipo de estructura es una lista ordenada de palabras clave que aparecen de forma única y que tienen asociados valores de cadena que proporcionan definiciones. Si una palabra tiene más de una definición correcta, de modo que la clave no es única, el contenedor más adecuado sería un multimap. Si solo se va a almacenar la lista de palabras, el contenedor adecuado sería un conjunto. Si se permiten varias apariciones de las palabras, lo mejor sería usar un multiset.

La asignación ordena los elementos que controla mediante una llamada a un objeto de función almacenado de tipo [key_compare](#key_compare). Este objeto almacenado es una función de comparación a la que se tiene acceso mediante una llamada al método [key_comp](#key_comp). En general, se comparan dos elementos especificados para determinar si uno es menor que otro o si son equivalentes. Cuando se comparan todos los elementos, se crea una secuencia ordenada de elementos no equivalentes.

> [!NOTE]
> La función de comparación es un predicado binario que induce una ordenación parcial estricta en el sentido matemático estándar. Un f predicado binario es un objeto de función que tiene dos objetos de argumento x y y y un valor devuelto de **true** o **false**. Una ordenación impuesta en un conjunto es una ordenación si el predicado binario es Irreflexivo, antisimétrico y transitivo, y si la equivalencia es transitiva, donde dos objetos débil estricta x e y se definen para ser equivalentes cuando tanto f y f(y,x) son **false** . Si la condición más fuerte de igualdad entre las claves reemplaza la de equivalencia, la ordenación se convierte en total (en el sentido de que todos los elementos se ordenan entre sí) y las claves coincidentes serán indiscernibles unas de otras.
>
> En C++14 puede habilitar la búsqueda heterogénea especificando el predicado `std::less<>` o `std::greater<>`, que no tienen ningún parámetro de tipo. Para obtener más información, vea [Búsqueda heterogénea en los contenedores asociativos](../standard-library/stl-containers.md#sequence_containers).

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[map](#map)|Crea una lista de un tamaño concreto o con elementos de un valor concreto o con un `allocator` específico o como copia de algún otro mapa.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[allocator_type](#allocator_type)|Definición de tipos para la clase `allocator` del objeto map.|
|[const_iterator](#const_iterator)|Definición de tipos para un iterador bidireccional que puede leer un **const** elemento del mapa.|
|[const_pointer](#const_pointer)|Una definición de tipo para un puntero a un **const** elemento de un mapa.|
|[const_reference](#const_reference)|Una definición de tipo para una referencia a un **const** elemento almacenado en un mapa para leer y realizar **const** operaciones.|
|[const_reverse_iterator](#const_reverse_iterator)|Tipo que proporciona un iterador bidireccional que puede leer cualquier elemento **const** de la asignación.|
|[difference_type](#difference_type)|Definición de tipos enteros con signo para el número de elementos de un mapa en un intervalo entre los elementos a los que apuntan los iteradores.|
|[iterator](#iterator)|Definición de tipos para un iterador bidireccional que puede leer o modificar cualquier elemento de un mapa.|
|[key_compare](#key_compare)|Definición de tipos para un objeto de función que puede comparar dos claves de ordenación para determinar el orden relativo de dos elementos del mapa.|
|[key_type](#key_type)|Definición de tipos para la clave de ordenación almacenada en cada elemento del mapa.|
|[mapped_type](#mapped_type)|Definición de tipos para los datos almacenados en cada elemento de un mapa.|
|[pointer](#pointer)|Una definición de tipo para un puntero a un **const** elemento de un mapa.|
|[reference](#reference)|Definición de tipos para una referencia a un elemento almacenado en un mapa.|
|[reverse_iterator](#reverse_iterator)|Definición de tipos para un iterador bidireccional que puede leer o modificar un elemento de un mapa invertido.|
|[size_type](#size_type)|Definición de tipos enteros sin signo para el número de elementos de un mapa|
|[value_type](#value_type)|Definición de tipos para el tipo de objeto almacenado como elemento en un mapa.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[at](#at)|Busca un elemento con un valor de clave especificado.|
|[begin](#begin)|Devuelve un iterador que apunta al primer elemento del mapa.|
|[cbegin](#cbegin)|Devuelve un iterador constante que apunta al primer elemento del mapa.|
|[cend](#cend)|Devuelve un iterador constante más allá del final.|
|[clear](#clear)|Borra todos los elementos de un mapa.|
|[count](#count)|Devuelve el número de elementos de un mapa cuya clave coincide con la clave especificada en un parámetro.|
|[crbegin](#crbegin)|Devuelve un iterador constante que apunta al primer elemento de un mapa invertido.|
|[crend](#crend)|Devuelve un iterador constante que apunta a la ubicación posterior al último elemento de un mapa invertido.|
|[emplace](#emplace)|Inserta en el mapa un elemento construido en contexto.|
|[emplace_hint](#emplace_hint)|Inserta en el mapa un elemento construido en contexto, con una sugerencia de colocación.|
|[empty](#empty)|Devuelve **true** si un mapa está vacío.|
|[end](#end)|Devuelve el iterador más allá del final.|
|[equal_range](#equal_range)|Devuelve un par de iteradores. El primer iterador del par apunta al primer elemento de un `map` cuya clave es mayor que una clave especificada. El segundo iterador del par apunta al primer elemento del `map` cuya clave es igual o mayor que la clave especificada.|
|[erase](#erase)|Quita un elemento o un intervalo de elementos de un mapa de las posiciones especificadas.|
|[find](#find)|Devuelve un iterador que apunta a la ubicación de un elemento en un mapa que tiene una clave igual que una clave especificada.|
|[get_allocator](#get_allocator)|Devuelve una copia del objeto `allocator` utilizado para construir el mapa.|
|[insert](#insert)|Inserta un elemento o un intervalo de elementos en el mapa en una posición especificada.|
|[key_comp](#key_comp)|Devuelve una copia del objeto de comparación utilizado para ordenar las claves en un mapa.|
|[lower_bound](#lower_bound)|Devuelve un iterador al primer elemento de un mapa cuyo valor de clave es igual o mayor que el de una clave especificada.|
|[max_size](#max_size)|Devuelve la longitud máxima del mapa.|
|[rbegin](#rbegin)|Devuelve un iterador que apunta al primer elemento de un mapa invertido.|
|[rend](#rend)|Devuelve un iterador que apunta a la ubicación posterior al último elemento de un mapa invertido.|
|[size](#size)|Devuelve el número de elementos del mapa.|
|[swap](#swap)|Intercambia los elementos de dos mapas.|
|[upper_bound](#upper_bound)|Devuelve un iterador al primer elemento de un mapa cuyo valor de clave es mayor que el de una clave especificada.|
|[value_comp](#value_comp)|Recupera una copia del objeto de comparación que se utiliza para ordenar valores de elementos de un mapa.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator&#91;&#93;](#op_at)|Inserta un elemento en un mapa con un valor de clave especificado.|
|[operator=](#op_eq)|Reemplaza los elementos de un mapa con una copia de otro mapa.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<map>

**Espacio de nombres:** std

## <a name="allocator_type"></a>  map::allocator_type

Tipo que representa la clase de asignador para el objeto de asignación.

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>Ejemplo

Vea en el ejemplo de [get_allocator](#get_allocator) cómo se usa `allocator_type`.

## <a name="at"></a>  map::at

Busca un elemento con un valor de clave especificado.

```cpp
Type& at(const Key& key);

const Type& at(const Key& key) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|Parámetro|Descripción|
|*key*|Valor de clave que se va a buscar.|

### <a name="return-value"></a>Valor devuelto

Una referencia al valor de datos del elemento encontrado.

### <a name="remarks"></a>Comentarios

Si no se encuentra el valor de clave de argumento, la función genera un objeto de clase [out_of_range](../standard-library/out-of-range-class.md).

### <a name="example"></a>Ejemplo

```cpp
// map_at.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

typedef std::map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// find and show elements
    std::cout << "c1.at('a') == " << c1.at('a') << std::endl;
    std::cout << "c1.at('b') == " << c1.at('b') << std::endl;
    std::cout << "c1.at('c') == " << c1.at('c') << std::endl;

    return (0);
    }
```

## <a name="begin"></a>  map::begin

Devuelve un iterador que direcciona el primer elemento del asignación.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional que direcciona el primer elemento de la asignación o a la ubicación siguiente a una asignación vacía.

### <a name="example"></a>Ejemplo

```cpp
// map_begin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: const_iterator m1_cIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 0, 0 ) );
   m1.insert ( Int_Pair ( 1, 1 ) );
   m1.insert ( Int_Pair ( 2, 4 ) );

   m1_cIter = m1.begin ( );
   cout << "The first element of m1 is " << m1_cIter -> first << endl;

   m1_Iter = m1.begin ( );
   m1.erase ( m1_Iter );

   // The following 2 lines would err because the iterator is const
   // m1_cIter = m1.begin ( );
   // m1.erase ( m1_cIter );

   m1_cIter = m1.begin( );
   cout << "The first element of m1 is now " << m1_cIter -> first << endl;
}
```

```Output
The first element of m1 is 0
The first element of m1 is now 1
```

## <a name="cbegin"></a>  map::cbegin

Devuelve un **const** iterador que direcciona la ubicación situada más allá del último elemento de un intervalo.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Un **const** iterador bidireccional que direcciona el primer elemento del intervalo, o la ubicación situada más allá del final de un intervalo vacío (para un intervalo vacío, `cbegin() == cend()`).

### <a name="remarks"></a>Comentarios

Con el valor devuelto de `cbegin`, los elementos del intervalo no se pueden modificar.

Se puede usar esta función miembro en lugar de la función miembro `begin()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, considere la posibilidad de `Container` sea modificable (no - **const**) contenedor de cualquier naturaleza que admite `begin()` y `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  map::cend

Devuelve un **const** iterador que direcciona la ubicación situada más allá del último elemento de un intervalo.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valor devuelto

Un **const** iterador de acceso bidireccional que apunta justo después del final del intervalo.

### <a name="remarks"></a>Comentarios

`cend` se usa para probar si un iterador ha sobrepasado el final de su intervalo.

Se puede usar esta función miembro en lugar de la función miembro `end()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, considere la posibilidad de `Container` sea modificable (no - **const**) contenedor de cualquier naturaleza que admite `end()` y `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

El valor devuelto por `cend` no se debe desreferenciar.

## <a name="clear"></a>  map::clear

Borra todos los elementos de un mapa.

```cpp
void clear();
```

### <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo debe usarse la función miembro map::clear.

```cpp
// map_clear.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 4));

    i = m1.size();
    cout << "The size of the map is initially "
         << i << "." << endl;

    m1.clear();
    i = m1.size();
    cout << "The size of the map after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the map is initially 2.
The size of the map after clearing is 0.
```

## <a name="const_iterator"></a>  map::const_iterator

Tipo que proporciona un iterador bidireccional que puede leer un elemento **const** de la asignación.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Comentarios

Un tipo `const_iterator` no se puede utilizar para modificar el valor de un elemento.

El `const_iterator` definido mediante la asignación apunta a elementos que son objetos de [value_type](#value_type), que son de tipo `pair`\< **constKey**, **Type**>, cuyo primer miembro es la clave para el elemento y cuyo segundo miembro es la referencia asignada que el elemento conserva.

Para desreferenciar un `const_iterator` `cIter` que apunta a un elemento en un mapa, use el `->` operador.

Para tener acceso al valor de clave del elemento, use `cIter` -> **first**, que es equivalente a (\* `cIter`). **first**.

Para tener acceso al valor de la referencia asignada del elemento, use `cIter` -> **second**, que es equivalente a (\* `cIter`). **second**.

### <a name="example"></a>Ejemplo

Vea en el ejemplo de [begin](#begin) cómo se usa `const_iterator`.

## <a name="const_pointer"></a>  map::const_pointer

Tipo que proporciona un puntero a un elemento **const** de una asignación.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Comentarios

Un tipo `const_pointer` no se puede utilizar para modificar el valor de un elemento.

En la mayoría de los casos, se debe usar [iterator](#iterator) para obtener acceso a los elementos de un objeto de asignación.

## <a name="const_reference"></a>  map::const_reference

Tipo que proporciona una referencia a un elemento **const** almacenado en una asignación para leer operaciones **const** y realizarlas.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Ejemplo

```cpp
// map_const_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the map is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the map is 1.
The data value of first element in the map is 10.
```

## <a name="const_reverse_iterator"></a>  map::const_reverse_iterator

Tipo que proporciona un iterador bidireccional que puede leer cualquier elemento **const** de la asignación.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Comentarios

Un tipo `const_reverse_iterator` no puede modificar el valor de un elemento. Se usa para iterar en la asignación en orden inverso.

El `const_reverse_iterator` definido por el mapa apunta a elementos que son objetos de [value_type](#value_type), que es de tipo `pair<const Key, Type>`, cuyo primer miembro es la clave para el elemento y cuyo segundo miembro es la referencia asignada que el elemento.

Para desreferenciar un `const_reverse_iterator crIter` que apunta a un elemento en un mapa, use el `->` operador.

Para obtener acceso al valor de la clave para el elemento, utilice `crIter`  ->  **primera**, que es equivalente a (\* `crIter`). **primera**.

Para obtener acceso al valor de la referencia asignada del elemento, utilice `crIter`  ->  **segundo**, que es equivalente a (\* `crIter`). **primera**.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [rend](#rend) para obtener un ejemplo de cómo declarar y usar `const_reverse_iterator`.

## <a name="count"></a>  map::count

Devuelve el número de elementos de una asignación cuya clave coincide con una clave especificada por un parámetro.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Parámetros

*clave* el valor de clave de los elementos que deben coincidir el mapa.

### <a name="return-value"></a>Valor devuelto

1 si el objeto map contiene un elemento cuyo criterio de ordenación coincide con el criterio del parámetro; 0 si el objeto map no contiene ningún elemento con el mismo criterio.

### <a name="remarks"></a>Comentarios

La función miembro devuelve el número de elementos *x* del intervalo

[ `lower_bound` (_ *Key* ), `upper_bound` (\_ *Key* ) )

que es 0 o 1 en el caso de map, que es un contenedor asociativo único.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el uso de la función miembro map::count.

```cpp
// map_count.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 1));
    m1.insert(Int_Pair(1, 4));
    m1.insert(Int_Pair(2, 1));

    // Keys must be unique in map, so duplicates are ignored
    i = m1.count(1);
    cout << "The number of elements in m1 with a sort key of 1 is: "
         << i << "." << endl;

    i = m1.count(2);
    cout << "The number of elements in m1 with a sort key of 2 is: "
         << i << "." << endl;

    i = m1.count(3);
    cout << "The number of elements in m1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in m1 with a sort key of 1 is: 1.
The number of elements in m1 with a sort key of 2 is: 1.
The number of elements in m1 with a sort key of 3 is: 0.
```

## <a name="crbegin"></a>  map::crbegin

Devuelve un iterador const que direcciona el primer elemento de un mapa invertido.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional inverso const que direcciona el primer elemento de un objeto [map](../standard-library/map-class.md) invertido o que direcciona lo que fue el último elemento de un objeto `map` sin invertir.

### <a name="remarks"></a>Comentarios

`crbegin` se usa con un `map` invertido igual que [begin](#begin) se usa con un `map`.

Con el valor devuelto de `crbegin`, el objeto `map` no se puede modificar.

`crbegin` puede usarse para iterar un objeto `map` hacia atrás.

### <a name="example"></a>Ejemplo

```cpp
// map_crbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crbegin( );
   cout << "The first element of the reversed map m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed map m1 is 3.
```

## <a name="crend"></a>  map::crend

Devuelve un iterador const que direcciona la ubicación que sigue al último elemento de un mapa invertido.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional inverso const que direcciona la ubicación siguiente al último elemento de un objeto [map](../standard-library/map-class.md) invertido (la ubicación que precedió al primer elemento del objeto `map` sin invertir).

### <a name="remarks"></a>Comentarios

`crend` se usa con un mapa invertido igual que [end](#end) se usa con un `map`.

Con el valor devuelto de `crend`, el objeto `map` no se puede modificar.

Se puede utilizar `crend` para comprobar si un iterador inverso llegó al final de su `map`.

El valor devuelto por `crend` no se debe desreferenciar.

### <a name="example"></a>Ejemplo

```cpp
// map_crend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crend( );
   m1_crIter--;
   cout << "The last element of the reversed map m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed map m1 is 1.
```

## <a name="difference_type"></a>  map::difference_type

Tipo entero con signo que se puede usar para representar el número de elementos de un mapa en un intervalo de elementos a los que apuntan los iteradores.

```cpp
typedef allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Comentarios

El `difference_type` es el tipo devuelto al restar o incrementar los iteradores del contenedor. `difference_type` se suele usar para representar el número de elementos que hay en el intervalo *[ first,  last)* entre los iteradores `first` y `last`. Incluye el elemento al que apunta `first` y el intervalo de elementos que abarca hasta el elemento al que apunta `last` sin incluirlo.

Tenga en cuenta que, aunque `difference_type` está disponible para todos los iteradores que cumplen los requisitos de un iterador de entrada, incluida la clase de iteradores bidireccionales admitida por los contenedores reversibles como set, solo los iteradores de acceso aleatorio proporcionados por un contenedor de acceso aleatorio, como vector, admiten la resta entre iteradores.

### <a name="example"></a>Ejemplo

```cpp
// map_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <map>
#include <algorithm>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );
   m1.insert ( Int_Pair ( 2, 30 ) );

   map <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;
   m1_bIter = m1.begin( );
   m1_eIter = m1.end( );

   // Count the number of elements in a map
   map <int, int>::difference_type  df_count = 1;
   m1_Iter = m1.begin( );
   while ( m1_Iter != m1_eIter)
   {
      df_count++;
      m1_Iter++;
   }

   cout << "The number of elements in the map m1 is: "
        << df_count << "." << endl;
}
```

```Output
The number of elements in the map m1 is: 4.
```

## <a name="emplace"></a>  map::emplace

Inserta un elemento construido en contexto (no se realiza ninguna operación de copia o de movimiento) en un mapa.

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
    Args&&... args);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|Parámetro|Descripción|
|*args*|Argumentos reenviados para construir un elemento que se va a insertar en el mapa, a menos que ya contenga un elemento cuyo valor esté ordenado de forma equivalente.|

### <a name="return-value"></a>Valor devuelto

Un [par](../standard-library/pair-structure.md) cuyo **bool** componente es true si se realizó una inserción y false si el mapa ya contenía un elemento de valor equivalente en la ordenación. El componente de iterador del par de valor devuelto apunta al elemento recién insertado si el **bool** componente es true, o al elemento existente si la **bool** componente es false.

Para tener acceso al componente de iterador de `pair` `pr`, utilice `pr.first`; para desreferenciarlo, utilice `*pr.first`. Para tener acceso a la **bool** componente, use `pr.second`. Para obtener un ejemplo, vea el código de ejemplo que se muestra más adelante en este artículo.

### <a name="remarks"></a>Comentarios

Esta función no invalida ningún iterador ni ninguna referencia.

Durante el emplazamiento, si se produce una excepción, el estado del contenedor no se modifica.

El [value_type](#value_type) de un elemento es un par, de modo que el valor de un elemento será un par ordenado en el que el primer componente es igual que el valor de clave y el segundo componente es igual que el valor de datos del elemento.

### <a name="example"></a>Ejemplo

```cpp
// map_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: ";

    for (const auto& p : m) {
        cout << "(" << p.first << ", " << p.second << ") ";
    }

    cout << endl;
}

int main()
{
    map<int, string> m1;

    auto ret = m1.emplace(10, "ten");

    if (!ret.second){
        auto pr = *ret.first;
        cout << "Emplace failed, element with key 10 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
        cout << "map not modified" << endl;
    }
    else{
        cout << "map modified, now contains ";
        print(m1);
    }
    cout << endl;

    ret = m1.emplace(10, "one zero");

    if (!ret.second){
        auto pr = *ret.first;
        cout << "Emplace failed, element with key 10 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
    }
    else{
        cout << "map modified, now contains ";
        print(m1);
    }
    cout << endl;
}

```

## <a name="emplace_hint"></a>  map::emplace_hint

Inserta un elemento construido en contexto (no se realiza ninguna operación de copia o de movimiento), con una sugerencia de colocación.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|Parámetro|Descripción|
|*args*|Argumentos reenviados para construir un elemento que se va a insertar en el mapa a menos que el mapa ya contenga ese elemento o, más en general, a menos que ya contenga un elemento cuya clave esté ordenada de manera equivalente.|
|*where*|Lugar donde se va a iniciar la búsqueda del punto de inserción correcto. (Si ese punto precede inmediatamente a *donde*, inserción se puede realizar en tiempo constante amortizado en lugar de tiempo logarítmico.)|

### <a name="return-value"></a>Valor devuelto

Iterador al elemento recién insertado.

Si se produjo un error en la inserción porque el elemento ya existe, devuelve un iterador al elemento existente con su clave.

### <a name="remarks"></a>Comentarios

Esta función no invalida ningún iterador ni ninguna referencia.

Durante el emplazamiento, si se produce una excepción, el estado del contenedor no se modifica.

El [value_type](#value_type) de un elemento es un par, de modo que el valor de un elemento será un par ordenado en el que el primer componente es igual que el valor de clave y el segundo componente es igual que el valor de datos del elemento.

### <a name="example"></a>Ejemplo

```cpp
// map_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: " << endl;

    for (const auto& p : m) {
        cout << "(" << p.first <<  "," << p.second << ") ";
    }

    cout << endl;
}

int main()
{
    map<string, string> m1;

    // Emplace some test data
    m1.emplace("Anna", "Accounting");
    m1.emplace("Bob", "Accounting");
    m1.emplace("Carmine", "Engineering");

    cout << "map starting data: ";
    print(m1);
    cout << endl;

    // Emplace with hint
    // m1.end() should be the "next" element after this emplacement
    m1.emplace_hint(m1.end(), "Doug", "Engineering");

    cout << "map modified, now contains ";
    print(m1);
    cout << endl;
}

```

## <a name="empty"></a>  map::empty

Comprueba si un mapa está vacío.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si el mapa está vacío; **False** si el mapa no lo está.

### <a name="example"></a>Ejemplo

```cpp
// map_empty.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2;

   typedef pair <int, int> Int_Pair;
   m1.insert ( Int_Pair ( 1, 1 ) );

   if ( m1.empty( ) )
      cout << "The map m1 is empty." << endl;
   else
      cout << "The map m1 is not empty." << endl;

   if ( m2.empty( ) )
      cout << "The map m2 is empty." << endl;
   else
      cout << "The map m2 is not empty." << endl;
}
```

```Output
The map m1 is not empty.
The map m2 is empty.
```

## <a name="end"></a>  map::end

Devuelve el iterador más allá del final.

```cpp
const_iterator end() const;


iterator end();
```

### <a name="return-value"></a>Valor devuelto

El iterador siguiente al final. Si el mapa está vacío, `map::end() == map::begin()`.

### <a name="remarks"></a>Comentarios

`end` se usa para comprobar si un iterador ha sobrepasado el final de su mapa.

El valor devuelto por `end` no se debe desreferenciar.

Para obtener un ejemplo de código, vea [map::find](#find).

## <a name="equal_range"></a>  map::equal_range

Devuelve un par de iteradores que representan el [lower_bound](#lower_bound) de la clave y el [upper_bound](#upper_bound) de la clave.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Parámetros

*clave* el valor de clave de argumento que se comparará con la clave de ordenación de un elemento del mapa que se está buscando.

### <a name="return-value"></a>Valor devuelto

Para tener acceso al primer iterador de un par `pr` devuelto por la función miembro, use `pr`. **first** y para desreferenciar el iterador de límite inferior, use \*( `pr`. **first**). Para tener acceso al segundo iterador de un par `pr` devuelto por la función miembro, use `pr`. **second** y para desreferenciar el iterador de límite superior, use \*( `pr`. **second**).

### <a name="example"></a>Ejemplo

```cpp
// map_equal_range.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef map <int, int, less<int> > IntMap;
   IntMap m1;
   map <int, int> :: const_iterator m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMap::const_iterator, IntMap::const_iterator> p1, p2;
   p1 = m1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the map m1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the map m1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   m1_RcIter = m1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << m1_RcIter -> second << "," << endl
        << " matching the 2nd element of the pair"
        << " returned by equal_range( 2 )." << endl;

   p2 = m1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == m1.end( ) ) && ( p2.second == m1.end( ) ) )
      cout << "The map m1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of map m1 with a key >= 40 is: "
           << p2.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the map m1 is: 20.
The upper bound of the element with a key of 2 in the map m1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
 matching the 2nd element of the pair returned by equal_range( 2 ).
The map m1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>  map::erase

Quita un elemento o un intervalo de elementos de una asignación de las posiciones especificadas o quita los elementos que coinciden con una clave especificada.

```cpp
iterator erase(
    const_iterator Where);


iterator erase(
    const_iterator First,
    const_iterator Last);


size_type erase(
    const key_type& Key);
```

### <a name="parameters"></a>Parámetros

*Donde* posición del elemento que se va a quitar.

*Primera* posición del primer elemento que se va a quitar.

*Último* posición inmediatamente siguiente al último elemento que se va a quitar.

*Clave* el valor de clave de los elementos que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Para las dos primeras funciones miembro, iterador bidireccional que designa el primer elemento que permanece más allá de los elementos quitados, o un elemento que es el final de la asignación si no existe ese elemento.

Para la tercera función miembro, devuelve el número de elementos que se han quitado de la asignación.

### <a name="example"></a>Ejemplo

```cpp
// map_erase.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>
#include <iterator> // next() and prev() helper functions
#include <utility>  // make_pair()

using namespace std;

using mymap = map<int, string>;

void printmap(const mymap& m) {
    for (const auto& elem : m) {
        cout << " [" << elem.first << ", " << elem.second << "]";
    }
    cout << endl << "size() == " << m.size() << endl << endl;
}

int main()
{
    mymap m1;

    // Fill in some data to test with, one at a time
    m1.insert(make_pair(1, "A"));
    m1.insert(make_pair(2, "B"));
    m1.insert(make_pair(3, "C"));
    m1.insert(make_pair(4, "D"));
    m1.insert(make_pair(5, "E"));

    cout << "Starting data of map m1 is:" << endl;
    printmap(m1);
    // The 1st member function removes an element at a given position
    m1.erase(next(m1.begin()));
    cout << "After the 2nd element is deleted, the map m1 is:" << endl;
    printmap(m1);

    // Fill in some data to test with, one at a time, using an intializer list
    mymap m2
    {
        { 10, "Bob" },
        { 11, "Rob" },
        { 12, "Robert" },
        { 13, "Bert" },
        { 14, "Bobby" }
    };

    cout << "Starting data of map m2 is:" << endl;
    printmap(m2);
    // The 2nd member function removes elements
    // in the range [First, Last)
    m2.erase(next(m2.begin()), prev(m2.end()));
    cout << "After the middle elements are deleted, the map m2 is:" << endl;
    printmap(m2);

    mymap m3;

    // Fill in some data to test with, one at a time, using emplace
    m3.emplace(1, "red");
    m3.emplace(2, "yellow");
    m3.emplace(3, "blue");
    m3.emplace(4, "green");
    m3.emplace(5, "orange");
    m3.emplace(6, "purple");
    m3.emplace(7, "pink");

    cout << "Starting data of map m3 is:" << endl;
    printmap(m3);
    // The 3rd member function removes elements with a given Key
    mymap::size_type count = m3.erase(2);
    // The 3rd member function also returns the number of elements removed
    cout << "The number of elements removed from m3 is: " << count << "." << endl;
    cout << "After the element with a key of 2 is deleted, the map m3 is:" << endl;
    printmap(m3);
}

```

## <a name="find"></a>  map::find

Devuelve un iterador que hace referencia a la ubicación de un elemento de un mapa que tiene una clave equivalente a una clave especificada.

```cpp
iterator find(const Key& key);


const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Parámetros

*clave* el valor de clave que debe coincidir con el criterio de ordenación de un elemento del mapa que se está buscando.

### <a name="return-value"></a>Valor devuelto

Iterador que hace referencia a la ubicación de un elemento con una clave especificada, o la ubicación siguiente al último elemento del mapa (`map::end()`) si no se encuentra ninguna coincidencia con la clave.

### <a name="remarks"></a>Comentarios

La función miembro devuelve un iterador que hace referencia a un elemento del mapa cuyo criterio de ordenación es equivalente a la clave de argumento de un predicado binario que induce a una ordenación basada en una relación de comparabilidad de menor que.

Si el valor devuelto de `find` se asigna a `const_iterator`, el objeto de mapa no puede modificarse. Si el valor devuelto de `find` se asigna a un `iterator`, se puede modificar el objeto de mapa

### <a name="example"></a>Ejemplo

```cpp
// compile with: /EHsc /W4 /MTd
#include <map>
#include <iostream>
#include <vector>
#include <string>
#include <utility>  // make_pair()

using namespace std;

template <typename A, typename B> void print_elem(const pair<A, B>& p) {
    cout << "(" << p.first << ", " << p.second << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

template <typename C, class T> void findit(const C& c, T val) {
    cout << "Trying find() on value " << val << endl;
    auto result = c.find(val);
    if (result != c.end()) {
        cout << "Element found: "; print_elem(*result); cout << endl;
    } else {
        cout << "Element not found." << endl;
    }
}

int main()
{
    map<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });
    cout << "The starting map m1 is (key, value):" << endl;
    print_collection(m1);

    vector<pair<int, string>> v;
    v.push_back(make_pair(43, "Tc"));
    v.push_back(make_pair(41, "Nb"));
    v.push_back(make_pair(46, "Pd"));
    v.push_back(make_pair(42, "Mo"));
    v.push_back(make_pair(44, "Ru"));
    v.push_back(make_pair(44, "Ru")); // attempt a duplicate

    cout << "Inserting the following vector data into m1:" << endl;
    print_collection(v);

    m1.insert(v.begin(), v.end());

    cout << "The modified map m1 is (key, value):" << endl;
    print_collection(m1);
    cout << endl;
    findit(m1, 45);
    findit(m1, 6);
}

```

## <a name="get_allocator"></a>  map::get_allocator

Devuelve una copia del objeto de asignador usado para construir el mapa.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valor devuelto

Asignador usado por el mapa.

### <a name="remarks"></a>Comentarios

Los asignadores de la clase map especifican la forma en que la clase administra el almacenamiento. Los asignadores predeterminados proporcionados con las clases contenedoras de la biblioteca estándar de C++ son suficientes para la mayoría de las necesidades de programación. La escritura y el uso de sus propias clases de asignador son temas avanzados de C++.

### <a name="example"></a>Ejemplo

```cpp
// map_get_allocator.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int>::allocator_type m1_Alloc;
   map <int, int>::allocator_type m2_Alloc;
   map <int, double>::allocator_type m3_Alloc;
   map <int, int>::allocator_type m4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   map <int, int> m1;
   map <int, int, allocator<int> > m2;
   map <int, double, allocator<double> > m3;

   m1_Alloc = m1.get_allocator( );
   m2_Alloc = m2.get_allocator( );
   m3_Alloc = m3.get_allocator( );

   cout << "The number of integers that can be allocated\n"
        << "before free memory is exhausted: "
        << m2.max_size( ) << ".\n" << endl;

   cout << "The number of doubles that can be allocated\n"
        << "before free memory is exhausted: "
        << m3.max_size( ) <<  ".\n" << endl;

   // The following line creates a map m4
   // with the allocator of map m1.
   map <int, int> m4( less<int>( ), m1_Alloc );

   m4_Alloc = m4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated with the other
   if( m1_Alloc == m4_Alloc )
   {
      cout << "The allocators are interchangeable." << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable." << endl;
   }
}
```

## <a name="insert"></a>  map::insert

Inserta un elemento o un intervalo de elementos en una asignación.

```cpp
// (1) single element
pair<iterator, bool> insert(
    const value_type& Val);


// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(
    ValTy&& Val);


// (3) single element with hint
iterator insert(
    const_iterator Where,
    const value_type& Val);


// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);


// (5) range
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);


// (6) initializer list
void insert(
    initializer_list<value_type>
IList);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|Parámetro|Descripción|
|*Val*|Valor de un elemento que se va a insertar en la asignación a menos que ya contenga un elemento cuya clave se ordena de forma equivalente.|
|*Where*|Lugar donde se va a iniciar la búsqueda del punto de inserción correcto. (Si ese punto precede inmediatamente a *donde*, inserción se puede realizar en tiempo constante amortizado en lugar de tiempo logarítmico.)|
|*ValTy*|Parámetro de plantilla que especifica el tipo de argumento que se puede usar la asignación para construir un elemento de [value_type](#value_type)y realiza *Val* como argumento.|
|*Primero*|Posición del primer elemento que se va a copiar.|
|*Último*|Posición situada más allá del último elemento que se va a copiar.|
|*InputIterator*|Argumento de la función de plantilla que cumple los requisitos de un [iterador de entrada](../standard-library/input-iterator-tag-struct.md) que apunta a elementos de un tipo que se puede usar para crear objetos [value_type](#value_type).|
|*IList*|El elemento [initializer_list](../standard-library/initializer-list.md) del que se van a copiar los elementos.|

### <a name="return-value"></a>Valor devuelto

Las funciones miembro de un único elemento, (1) y (2), devuelven un [par](../standard-library/pair-structure.md) cuyo **bool** componente es true si se realizó una inserción y false si el mapa ya contenía un elemento cuya clave tenía un valor equivalente en la ordenación. El componente de iterador del par de valor devuelto apunta al elemento recién insertado si el **bool** componente es true, o al elemento existente si la **bool** componente es false.

Las funciones miembro de un solo elemento con sugerencia, (3) y (4), devuelven un iterador que apunta a la posición donde se insertó el nuevo elemento en la asignación o, si ya existe un elemento con una clave equivalente, al elemento existente.

### <a name="remarks"></a>Comentarios

Esta función no invalida ningún iterador, puntero o referencia.

Durante la inserción de un solo elemento, si se produce una excepción, no se modifica el estado del contenedor. Durante la inserción de varios elementos, si se produce una excepción, el contenedor se deja en un estado sin especificar pero válido.

Para tener acceso al componente de iterador de un `pair` `pr` devuelto por la función miembro de un único elemento, utilice `pr.first`; para desreferenciar el iterador dentro del par devuelto, utilice `*pr.first`, especificando un elemento. Para tener acceso a la **bool** componente, use `pr.second`. Para obtener un ejemplo, vea el código de ejemplo que se muestra más adelante en este artículo.

El objeto [value_type](#value_type) de un contenedor es un typedef que pertenece al contenedor y, para map, `map<K, V>::value_type` es `pair<const K, V>`. El valor de un elemento es un par ordenado en el que el primer componente es igual al valor de clave y el segundo componente es igual al valor de datos del elemento.

La función miembro de intervalo (5) inserta la secuencia de valores de elemento en una asignación que corresponde a cada elemento direccionado por un iterador en el intervalo `[First, Last)`; por lo tanto, `Last` no se inserta. La función miembro de contenedor `end()` hace referencia a la posición situada justo después del último elemento del contenedor; por ejemplo, la instrucción `m.insert(v.begin(), v.end());` intenta insertar todos los elementos de `v` en `m`. Solo se insertan los elementos que tienen valores únicos en el intervalo; se omiten los duplicados. Para observar qué elementos se rechazan, utilice las versiones de un solo elemento de `insert`.

La función miembro de lista de inicializadores (6) usa [initializer_list](../standard-library/initializer-list.md) para copiar los elementos al mapa.

Para la inserción de un elemento construido en contexto (es decir, no se realiza ninguna operación de copia o movimiento), vea [map::emplace](#emplace) y [map::emplace_hint](#emplace_hint).

### <a name="example"></a>Ejemplo

```cpp
// map_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>
#include <vector>
#include <utility>  // make_pair()

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: ";

    for (const auto& p : m) {
        cout << "(" << p.first << ", " << p.second << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    map<int, int> m1;
    // call insert(const value_type&) version
    m1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    m1.insert(make_pair(2, 20));

    cout << "The original key and mapped values of m1 are:" << endl;
    print(m1);

    // intentionally attempt a duplicate, single element
    auto ret = m1.insert(make_pair(1, 111));
    if (!ret.second){
        auto pr = *ret.first;
        cout << "Insert failed, element with key value 1 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
    }
    else{
        cout << "The modified key and mapped values of m1 are:" << endl;
        print(m1);
    }
    cout << endl;

    // single element, with hint
    m1.insert(m1.end(), make_pair(3, 30));
    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);
    cout << endl;

    // The templatized version inserting a jumbled range
    map<int, int> m2;
    vector<pair<int, int>> v;
    v.push_back(make_pair(43, 294));
    v.push_back(make_pair(41, 262));
    v.push_back(make_pair(45, 330));
    v.push_back(make_pair(42, 277));
    v.push_back(make_pair(44, 311));

    cout << "Inserting the following vector data into m2:" << endl;
    print(v);

    m2.insert(v.begin(), v.end());

    cout << "The modified key and mapped values of m2 are:" << endl;
    print(m2);
    cout << endl;

    // The templatized versions move-constructing elements
    map<int, string>  m3;
    pair<int, string> ip1(475, "blue"), ip2(510, "green");

    // single element
    m3.insert(move(ip1));
    cout << "After the first move insertion, m3 contains:" << endl;
    print(m3);

    // single element with hint
    m3.insert(m3.end(), move(ip2));
    cout << "After the second move insertion, m3 contains:" << endl;
    print(m3);
    cout << endl;

    map<int, int> m4;
    // Insert the elements from an initializer_list
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });
    cout << "After initializer_list insertion, m4 contains:" << endl;
    print(m4);
    cout << endl;
}

```

## <a name="iterator"></a>  map::iterator

Tipo que proporciona un iterador bidireccional que puede leer o modificar cualquier elemento de un mapa.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Comentarios

El `iterator` definido por los puntos de mapa a los elementos que son objetos de [value_type](#value_type), que es de tipo `pair`*\<***constKey**, **Tipo***>*, cuyo primer miembro es la clave para el elemento y cuyo segundo miembro es el dato de referencia asignada mantenido por el elemento.

Para desreferenciar un **iterador** `Iter` que apunta a un elemento en un mapa, use el `->` operador.

Para tener acceso al valor de clave del elemento, use `Iter` -> **first**, que es equivalente a (\* `Iter`). **first**. Para tener acceso al valor de la referencia asignada del elemento, use `Iter` -> **second**, que es equivalente a (\* `Iter`). **second**.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [comenzar](#begin) para obtener un ejemplo de cómo declarar y usar `iterator`.

## <a name="key_comp"></a>  map::key_comp

Recupera una copia del objeto de comparación usado para ordenar claves de un mapa.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto de función que un mapa usa para ordenar sus elementos.

### <a name="remarks"></a>Comentarios

El objeto almacenado define la función miembro

**bool operator**( **constKey&**`left`, **const Key&**`right`);

que devuelve **True** si `left` precede y no es igual a `right` en el criterio de ordenación.

### <a name="example"></a>Ejemplo

```cpp
// map_key_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   map <int, int, less<int> > m1;
   map <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of m1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of m1."
           << endl;
   }

   map <int, int, greater<int> > m2;
   map <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of m2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of m2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of m1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of m2.
```

## <a name="key_compare"></a>  map::key_compare

Tipo que proporciona un objeto de función que puede comparar dos criterios de ordenación para determinar el orden relativo de dos elementos del mapa.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Comentarios

`key_compare` es un sinónimo del parámetro de plantilla *rasgos*.

Para obtener más información sobre *rasgos* vea el [map (clase)](../standard-library/map-class.md) tema.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [key_comp](#key_comp) para obtener un ejemplo de cómo declarar y usar `key_compare`.

## <a name="key_type"></a>  map::key_type

Tipo que describe la clave de ordenación almacenada en cada elemento del mapa.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Comentarios

`key_type` es un sinónimo del parámetro de plantilla *clave*.

Para obtener más información sobre *clave*, vea la sección Comentarios de la [map (clase)](../standard-library/map-class.md) tema.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [value_type](#value_type) para obtener un ejemplo de cómo declarar y usar `key_type`.

## <a name="lower_bound"></a>  map::lower_bound

Devuelve un iterador al primer elemento de un mapa cuyo valor de clave es igual o mayor que el de una clave especificada.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Parámetros

*clave* el valor de clave de argumento que se comparará con la clave de ordenación de un elemento del mapa que se está buscando.

### <a name="return-value"></a>Valor devuelto

Un `iterator` o `const_iterator` que se dirige la ubicación de un elemento en un mapa que tiene una clave que es igual o mayor que la clave de argumento o que direcciona la ubicación siguiente al último elemento del mapa si no coinciden con se encuentra para la clave.

Si el valor devuelto de `lower_bound` se asigna a `const_iterator`, el objeto de mapa no puede modificarse. Si el valor devuelto de `lower_bound` se asigna a un `iterator`, se puede modificar el objeto de mapa.

### <a name="example"></a>Ejemplo

```cpp
// map_lower_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.lower_bound( 2 );
   cout << "The first element of map m1 with a key of 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for this key, end( ) is returned
   m1_RcIter = m1. lower_bound ( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The map m1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of map m1 with a key of 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the map can be found
   // using a dereferenced iterator addressing the location
   m1_AcIter = m1.end( );
   m1_AcIter--;
   m1_RcIter = m1. lower_bound ( m1_AcIter -> first );
   cout << "The element of m1 with a key matching "
        << "that of the last element is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The first element of map m1 with a key of 2 is: 20.
The map m1 doesn't have an element with a key of 4.
The element of m1 with a key matching that of the last element is: 30.
```

## <a name="map"></a>  map::map

Construye un mapa que está vacío o que es una copia de todo o de parte de otro mapa.

```cpp
map();

explicit map(
    const Traits& Comp);

map(
    const Traits& Comp,
    const Allocator& Al);

map(
    const map& Right);

map(
    map&& Right);

map(
    initializer_list<value_type> IList);

map(
    initializer_list<value_type> IList,
    const Traits& Comp);

map(
    initializer_list<value_type> IList,
    const Traits& Comp,
    const Allocator& Allocator);

template <class InputIterator>
map(
 InputIterator First,
    InputIterator Last);

template <class InputIterator>
map(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
map(
 InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|Parámetro|Descripción|
|*Al*|Clase de asignador de almacenamiento que se va a utilizar para este mapa, que toma `Allocator` como valor predeterminado.|
|*Comp.*|Función de comparación de tipo `const Traits` que se utiliza para ordenar los elementos del mapa, que de forma predeterminada es `hash_compare`.|
|*Derecha*|Asignación de la que el conjunto construido va a ser una copia.|
|*Primero*|Posición del primer elemento en el intervalo de elementos que se va a copiar.|
|*Último*|Posición del primer elemento más allá del intervalo de elementos que se va a copiar.|
|*IList*|initializer_list de la que se van a copiar los elementos.|

### <a name="remarks"></a>Comentarios

Todos los constructores almacenan un tipo de objeto de asignador que administra el almacenamiento en memoria del mapa y que se puede devolver más adelante mediante una llamada a [get_allocator](#get_allocator). El parámetro de asignador se suele omitir en las declaraciones de clase y las macros de preprocesamiento que se utilizan para sustituir asignadores alternativos.

Todos los constructores inicializan sus mapas.

Todos los constructores almacenan un objeto de función de tipo Traits que se usa para establecer un orden entre las claves del mapa y que se puede devolver más adelante mediante una llamada a [key_comp](#key_comp).

Los tres primeros constructores especifican un mapa inicial vacío, el segundo especifica el tipo de función de comparación (*Comp*) que se usará para establecer explícitamente el orden de los elementos y el tercero especifica el tipo de asignador ( *Al*) que se usará. La palabra clave **explícita** suprime ciertas clases de conversión automática de tipos.

El cuarto constructor especifica una copia del mapa *derecha*.

El quinto constructor especifica una copia del mapa moviendo *derecha*.

Los constructores sexto, séptimo y octavos utilizan una initializer_list de la que se van a copiar los miembros.

Los tres constructores siguientes copian el intervalo `[First, Last)` de un mapa especificando de forma cada vez más explícita el tipo de función de comparación de clase `Traits` y el asignador.

### <a name="example"></a>Ejemplo

```cpp
// map_map.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    typedef pair <int, int> Int_Pair;
    map <int, int>::iterator m1_Iter, m3_Iter, m4_Iter, m5_Iter, m6_Iter, m7_Iter;
    map <int, int, less<int> >::iterator m2_Iter;

    // Create an empty map m0 of key type integer
    map <int, int> m0;

    // Create an empty map m1 with the key comparison
    // function of less than, then insert 4 elements
    map <int, int, less<int> > m1;
    m1.insert(Int_Pair(1, 10));
    m1.insert(Int_Pair(2, 20));
    m1.insert(Int_Pair(3, 30));
    m1.insert(Int_Pair(4, 40));

    // Create an empty map m2 with the key comparison
    // function of geater than, then insert 2 elements
    map <int, int, less<int> > m2;
    m2.insert(Int_Pair(1, 10));
    m2.insert(Int_Pair(2, 20));

    // Create a map m3 with the
    // allocator of map m1
    map <int, int>::allocator_type m1_Alloc;
    m1_Alloc = m1.get_allocator();
    map <int, int> m3(less<int>(), m1_Alloc);
    m3.insert(Int_Pair(3, 30));

    // Create a copy, map m4, of map m1
    map <int, int> m4(m1);

    // Create a map m5 by copying the range m1[ first,  last)
    map <int, int>::const_iterator m1_bcIter, m1_ecIter;
    m1_bcIter = m1.begin();
    m1_ecIter = m1.begin();
    m1_ecIter++;
    m1_ecIter++;
    map <int, int> m5(m1_bcIter, m1_ecIter);

    // Create a map m6 by copying the range m4[ first,  last)
    // and with the allocator of map m2
    map <int, int>::allocator_type m2_Alloc;
    m2_Alloc = m2.get_allocator();
    map <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);

    cout << "m1 =";
    for (auto i : m1)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m2 =";
    for(auto i : m2)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m3 =";
    for (auto i : m3)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m4 =";
    for (auto i : m4)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m5 =";
    for (auto i : m5)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m6 =";
    for (auto i : m6)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m7 by moving m5
    cout << "m7 =";
    map<int, int> m7(move(m5));
    for (auto i : m7)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m8 by copying in an initializer_list
    map<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };
    cout << "m8: = ";
    for (auto i : m8)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m9 with an initializer_list and a comparator
    map<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());
    cout << "m9: = ";
    for (auto i : m9)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m10 with an initializer_list, a comparator, and an allocator
    map<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());
    cout << "m10: = ";
    for (auto i : m10)
        cout << i.first << " " << i.second << ", ";
    cout << endl;
}

```

## <a name="mapped_type"></a>  map::mapped_type

Tipo que representa los datos almacenados en un mapa.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Comentarios

El tipo `mapped_type` es un sinónimo de la clase *tipo* parámetro de plantilla.

Para obtener más información sobre *tipo* vea el [map (clase)](../standard-library/map-class.md) tema.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [value_type](#value_type) para obtener un ejemplo de cómo declarar y usar `mapped_type`.

## <a name="max_size"></a>  map::max_size

Devuelve la longitud máxima del mapa.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud máxima posible del mapa.

### <a name="example"></a>Ejemplo

```cpp
// map_max_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: size_type i;

   i = m1.max_size( );
   cout << "The maximum possible length "
        << "of the map is " << i << "."
        << endl << "(Magnitude is machine specific.)";
}
```

## <a name="op_at"></a>  map::operator[]

Inserta un elemento en un mapa con un valor de clave especificado.

```cpp
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|Parámetro|Descripción|
|*key*|El valor de clave del elemento que se tiene que insertar.|

### <a name="return-value"></a>Valor devuelto

Referencia al valor de datos del elemento insertado.

### <a name="remarks"></a>Comentarios

Si el valor de clave de argumento no se encuentra, se inserta junto con el valor predeterminado del tipo de datos.

`operator[]` puede utilizarse para insertar elementos en un mapa `m` mediante `m[ key] = DataValue;` donde `DataValue` es el valor de la `mapped_type` del elemento con un valor de clave de *clave*.

Cuando se emplea `operator[]` para insertar elementos, la referencia devuelta no indica si una inserción cambia un elemento ya existente o crea uno nuevo. Se pueden usar las funciones miembro [find](#find) e [insert](#insert) para determinar si ya existe un elemento con una clave especificada antes de una inserción.

### <a name="example"></a>Ejemplo

```cpp
// map_op_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   map <int, int> m1;
   map <int, int> :: iterator pIter;

   // Insert a data value of 10 with a key of 1
   // into a map using the operator[] member function
   m1[ 1 ] = 10;

   // Compare other ways to insert objects into a map
   m1.insert ( map <int, int> :: value_type ( 2, 20 ) );
   m1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // If the key already exists, operator[]
   // changes the value of the datum in the element
   m1[ 2 ] = 40;

   // operator[] will also insert the value of the data
   // type's default constructor if the value is unspecified
   m1[5];

   cout  << "The keys of the mapped elements are now:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are now:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

// insert by moving key
    map<string, int> c2;
    string str("abc");
    cout << "c2[move(str)] == " << c2[move(str)] << endl;
    cout << "c2["abc"] == " << c2["abc"] << endl;

    return (0);
}
```

```Output
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 30.
The keys of the mapped elements are now: 1 2 3 5.
The values of the mapped elements are now: 10 40 30 0.
c2[move(str)] == 0
c2["abc"] == 1
```

## <a name="op_eq"></a>  map::operator=

Reemplaza los elementos de un mapa con una copia de otro mapa.

```cpp
map& operator=(const map& right);

map& operator=(map&& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|Parámetro|Descripción|
|*right*|Objeto [map](../standard-library/map-class.md) que se copia a `map`.|

### <a name="remarks"></a>Comentarios

Después de borrar todos los elementos existentes en un `map`, `operator=` copia o mueve el contenido de *derecho* en el mapa.

### <a name="example"></a>Ejemplo

```cpp
// map_operator_as.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
   {
   using namespace std;
   map<int, int> v1, v2, v3;
   map<int, int>::iterator iter;

   v1.insert(pair<int, int>(1, 10));

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;
   }
```

## <a name="pointer"></a>  map::pointer

Tipo que proporciona un puntero a un elemento de un mapa.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Comentarios

Un tipo `pointer` puede usarse para modificar el valor de un elemento.

En la mayoría de los casos, se debe usar [iterator](#iterator) para obtener acceso a los elementos de un objeto de asignación.

## <a name="rbegin"></a>  map::rbegin

Devuelve un iterador que direcciona el primer elemento de un mapa invertido.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional inverso que direcciona el primer elemento de un mapa invertido o que direcciona lo que fue el último elemento de un mapa sin invertir.

### <a name="remarks"></a>Comentarios

`rbegin` se usa con un mapa invertido igual que [begin](#begin) se usa con un mapa.

Si el valor devuelto de `rbegin` se asigna a `const_reverse_iterator`, el objeto de mapa no puede modificarse. Si el valor devuelto de `rbegin` se asigna a `reverse_iterator`, el objeto de mapa puede modificarse.

`rbegin` puede usarse para iterar un mapa hacia atrás.

### <a name="example"></a>Ejemplo

```cpp
// map_rbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: reverse_iterator m1_rIter;
   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rbegin( );
   cout << "The first element of the reversed map m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a map in a forward order
   cout << "The map is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a map in a reverse order
   cout << "The reversed map is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A map element can be erased by dereferencing to its key
   m1_rIter = m1.rbegin( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed map is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed map m1 is 3.
The map is: 1 2 3 .
The reversed map is: 3 2 1 .
After the erasure, the first element in the reversed map is 2.
```

## <a name="reference"></a>  map::reference

Tipo que proporciona una referencia a un elemento almacenado en un mapa.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Ejemplo

```cpp
// map_reference.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the map is "
        << Ref2 << "." << endl;

   //The non-const_reference can be used to modify the
   //data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the map is 1.
The data value of first element in the map is 10.
The modified data value of first element is 15.
```

## <a name="rend"></a>  map::rend

Devuelve un iterador que direcciona la ubicación que sigue al último elemento de un mapa invertido.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional inverso que direcciona la ubicación siguiente al último elemento de un mapa invertido (la ubicación que precedió al primer elemento del mapa sin invertir).

### <a name="remarks"></a>Comentarios

`rend` se usa con un mapa invertido igual que [end](#end) se usa con un mapa.

Si el valor devuelto de `rend` se asigna a `const_reverse_iterator`, el objeto de mapa no puede modificarse. Si el valor devuelto de `rend` se asigna a `reverse_iterator`, el objeto de mapa puede modificarse.

Se puede usar `rend` para comprobar si un iterador inverso llegó al final de su mapa.

El valor devuelto por `rend` no se debe desreferenciar.

### <a name="example"></a>Ejemplo

```cpp
// map_rend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: reverse_iterator m1_rIter;
   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "The last element of the reversed map m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a map in a forward order
   cout << "The map is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a map in a reverse order
   cout << "The reversed map is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A map element can be erased by dereferencing to its key
   m1_rIter = --m1.rend( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed map is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed map m1 is 1.
The map is: 1 2 3 .
The reversed map is: 3 2 1 .
After the erasure, the last element in the reversed map is 2.
```

## <a name="reverse_iterator"></a>  map::reverse_iterator

Tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento de un mapa invertido.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Comentarios

Un tipo `reverse_iterator` no puede modificar el valor de un elemento. Se usa para iterar en la asignación en orden inverso.

El `reverse_iterator` definido por los puntos de mapa a los elementos que son objetos de [value_type](#value_type), que es de tipo `pair`*\<***constKey**, **Tipo***>*, cuyo primer miembro es la clave para el elemento y cuyo segundo miembro es el dato de referencia asignada mantenido por el elemento.

Para desreferenciar un `reverse_iterator` `rIter` que apunta a un elemento en un mapa, use el `->` operador.

Para tener acceso al valor de clave del elemento, use `rIter` -> **first**, que es equivalente a (\* `rIter`). **first**. Para tener acceso al valor de la referencia asignada del elemento, use `rIter` -> **second**, que es equivalente a (\* `rIter`). **first**.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [rbegin](#rbegin) para obtener un ejemplo de cómo declarar y usar `reverse_iterator`.

## <a name="size"></a>  map::size

Devuelve el número de elementos del mapa.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valor devuelto

Longitud actual del mapa.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el uso de la función miembro map::size.

```cpp
// map_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1, m2;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    i = m1.size();
    cout << "The map length is " << i << "." << endl;

    m1.insert(Int_Pair(2, 4));
    i = m1.size();
    cout << "The map length is now " << i << "." << endl;
}
```

```Output
The map length is 1.
The map length is now 2.
```

## <a name="size_type"></a>  map::size_type

Tipo entero sin signo que puede representar el número de elementos de un mapa.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [size](#size) para obtener un ejemplo de cómo declarar y usar `size_type`.

## <a name="swap"></a>  map::swap

Intercambia los elementos de dos mapas.

```cpp
void swap(
    map<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*derecha* mapa de argumentos que proporciona los elementos que se intercambie con el mapa de destino.

### <a name="remarks"></a>Comentarios

La función miembro no invalida ninguna referencia, puntero o iterador que designan los elementos de los dos mapas cuyos elementos se intercambian.

### <a name="example"></a>Ejemplo

```cpp
// map_swap.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3;
   map <int, int>::iterator m1_Iter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m2.insert ( Int_Pair ( 10, 100 ) );
   m2.insert ( Int_Pair ( 20, 200 ) );
   m3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   //m2 is said to be the argument map; m1 the target map
   m1.swap( m2 );

   cout << "After swapping with m2, map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( m1, m3 );

   cout << "After swapping with m3, map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original map m1 is: 10 20 30.
After swapping with m2, map m1 is: 100 200.
After swapping with m3, map m1 is: 300.
```

## <a name="upper_bound"></a>  map::upper_bound

Devuelve un iterador al primer elemento de un mapa cuyo valor de clave es mayor que el de una clave especificada.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Parámetros

*clave* el valor de clave de argumento que se comparará con el valor de clave de ordenación de un elemento del mapa que se está buscando.

### <a name="return-value"></a>Valor devuelto

Un `iterator` o `const_iterator` que se dirige la ubicación de un elemento en un mapa que tiene una clave que es mayor que la clave de argumento o que direcciona la ubicación siguiente al último elemento del mapa si no coinciden con se encuentra para la clave.

Si el valor devuelto se asigna a `const_iterator`, el objeto de mapa no puede modificarse. Si el valor devuelto se asigna a un `iterator`, se puede modificar el objeto de mapa.

### <a name="example"></a>Ejemplo

```cpp
// map_upper_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.upper_bound( 2 );
   cout << "The first element of map m1 with a key "
        << "greater than 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end is returned
   m1_RcIter = m1. upper_bound ( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The map m1 doesn't have an element "
           << "with a key greater than 4." << endl;
   else
      cout << "The element of map m1 with a key > 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the map can be found
   // using a dereferenced iterator addressing the location
   m1_AcIter = m1.begin( );
   m1_RcIter = m1. upper_bound ( m1_AcIter -> first );
   cout << "The 1st element of m1 with a key greater than\n"
        << "that of the initial element of m1 is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The first element of map m1 with a key greater than 2 is: 30.
The map m1 doesn't have an element with a key greater than 4.
The 1st element of m1 with a key greater than
that of the initial element of m1 is: 20.
```

## <a name="value_comp"></a>  map::value_comp

La función miembro devuelve un objeto de función que determina el orden de los elementos de un mapa mediante la comparación de sus valores de clave.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto de función de comparación que un mapa usa para ordenar sus elementos.

### <a name="remarks"></a>Comentarios

Para un mapa *m*, si dos elementos *e*1( *k*1, *d*1) y *e*2( *k*2, `d`2) son objetos de tipo `value_type`, donde *k*1 y *k*2 son sus claves de tipo `key_type`, y `d`1 y `d`2 son sus datos de tipo `mapped_type`, entonces *m.*`value_comp`( *e*1, *e*2) es equivalente a *m.*`key_comp`*(k*1, *k*2). Un objeto almacenado define la función miembro

**BOOL (operador)**( **value_type &**`left`, **value_type &**`right`);

que devuelve **True** si el valor de clave de `left` precede y no es igual al valor de clave de `right` en el criterio de ordenación.

### <a name="example"></a>Ejemplo

```cpp
// map_value_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   map <int, int, less<int> > m1;
   map <int, int, less<int> >::value_compare vc1 = m1.value_comp( );
   pair< map<int,int>::iterator, bool > pr1, pr2;

   pr1= m1.insert ( map <int, int> :: value_type ( 1, 10 ) );
   pr2= m1.insert ( map <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *pr1.first, *pr2.first ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does not precede the element ( 2,5 )."
           << endl;
   }

   if(vc1( *pr2.first, *pr1.first ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does not precede the element ( 1,10 )."
           << endl;
   }
}
```

```Output
The element ( 1,10 ) precedes the element ( 2,5 ).
The element ( 2,5 ) does not precede the element ( 1,10 ).
```

## <a name="value_type"></a>  map::value_type

Tipo de objeto almacenado como elemento en un mapa.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="example"></a>Ejemplo

```cpp
// map_value_type.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   map <int, int> m1;
   map <int, int> :: key_type key1;
   map <int, int> :: mapped_type mapped1;
   map <int, int> :: value_type value1;
   map <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   m1.insert ( map <int, int> :: value_type ( 1, 10 ) );

   // Compare other ways to insert objects into a map
   m1.insert ( cInt2Int ( 2, 20 ) );
   m1[ 3 ] = 30;

   // Initializing key1 and mapped1
   key1 = ( m1.begin( ) -> first );
   mapped1 = ( m1.begin( ) -> second );

   cout << "The key of first element in the map is "
        << key1 << "." << endl;

   cout << "The data value of first element in the map is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type is not assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

## <a name="see-also"></a>Vea también

[\<Map > miembros](http://msdn.microsoft.com/7e8f0bc2-6034-40f6-9d14-76d4cef86308)<br/>
[Contenedores](../cpp/containers-modern-cpp.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
