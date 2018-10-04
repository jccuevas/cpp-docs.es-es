---
title: unordered_map (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- unordered_map/std::unordered_map
- unordered_map/std::unordered_map::allocator_type
- unordered_map/std::unordered_map::const_iterator
- unordered_map/std::unordered_map::const_local_iterator
- unordered_map/std::unordered_map::const_pointer
- unordered_map/std::unordered_map::const_reference
- unordered_map/std::unordered_map::difference_type
- unordered_map/std::unordered_map::hasher
- unordered_map/std::unordered_map::iterator
- unordered_map/std::unordered_map::key_equal
- unordered_map/std::unordered_map::key_type
- unordered_map/std::unordered_map::local_iterator
- unordered_map/std::unordered_map::mapped_type
- unordered_map/std::unordered_map::pointer
- unordered_map/std::unordered_map::reference
- unordered_map/std::unordered_map::size_type
- unordered_map/std::unordered_map::value_type
- unordered_map/std::unordered_map::at
- unordered_map/std::unordered_map::begin
- unordered_map/std::unordered_map::bucket
- unordered_map/std::unordered_map::bucket_count
- unordered_map/std::unordered_map::bucket_size
- unordered_map/std::unordered_map::cbegin
- unordered_map/std::unordered_map::cend
- unordered_map/std::unordered_map::clear
- unordered_map/std::unordered_map::count
- unordered_map/std::unordered_map::emplace
- unordered_map/std::unordered_map::emplace_hint
- unordered_map/std::unordered_map::empty
- unordered_map/std::unordered_map::end
- unordered_map/std::unordered_map::equal_range
- unordered_map/std::unordered_map::erase
- unordered_map/std::unordered_map::find
- unordered_map/std::unordered_map::get_allocator
- unordered_map/std::unordered_map::hash
- unordered_map/std::unordered_map::insert
- unordered_map/std::unordered_map::key_eq
- unordered_map/std::unordered_map::load_factor
- unordered_map/std::unordered_map::max_bucket_count
- unordered_map/std::unordered_map::max_load_factor
- unordered_map/std::unordered_map::max_size
- unordered_map/std::unordered_map::rehash
- unordered_map/std::unordered_map::size
- unordered_map/std::unordered_map::swap
- unordered_map/std::unordered_map::unordered_map
- unordered_map/std::unordered_map::hash_function
dev_langs:
- C++
helpviewer_keywords:
- std::unordered_map
- std::unordered_map::allocator_type
- std::unordered_map::const_iterator
- std::unordered_map::const_local_iterator
- std::unordered_map::const_pointer
- std::unordered_map::const_reference
- std::unordered_map::difference_type
- std::unordered_map::hasher
- std::unordered_map::iterator
- std::unordered_map::key_equal
- std::unordered_map::key_type
- std::unordered_map::local_iterator
- std::unordered_map::mapped_type
- std::unordered_map::pointer
- std::unordered_map::reference
- std::unordered_map::size_type
- std::unordered_map::value_type
- std::unordered_map::at
- std::unordered_map::begin
- std::unordered_map::bucket
- std::unordered_map::bucket_count
- std::unordered_map::bucket_size
- std::unordered_map::cbegin
- std::unordered_map::cend
- std::unordered_map::clear
- std::unordered_map::count
- std::unordered_map::emplace
- std::unordered_map::emplace_hint
- std::unordered_map::empty
- std::unordered_map::end
- std::unordered_map::equal_range
- std::unordered_map::erase
- std::unordered_map::find
- std::unordered_map::get_allocator
- std::unordered_map::hash
- std::unordered_map::insert
- std::unordered_map::key_eq
- std::unordered_map::load_factor
- std::unordered_map::max_bucket_count
- std::unordered_map::max_load_factor
- std::unordered_map::max_size
- std::unordered_map::rehash
- std::unordered_map::size
- std::unordered_map::swap
- std::unordered_map::unordered_map
- std::unordered_map::allocator_type
- std::unordered_map::const_iterator
- std::unordered_map::const_local_iterator
- std::unordered_map::const_pointer
- std::unordered_map::const_reference
- std::unordered_map::difference_type
- std::unordered_map::hasher
- std::unordered_map::iterator
- std::unordered_map::key_equal
- std::unordered_map::key_type
- std::unordered_map::local_iterator
- std::unordered_map::mapped_type
- std::unordered_map::pointer
- std::unordered_map::reference
- std::unordered_map::size_type
- std::unordered_map::value_type
- std::unordered_map::at
- std::unordered_map::begin
- std::unordered_map::bucket
- std::unordered_map::bucket_count
- std::unordered_map::bucket_size
- std::unordered_map::cbegin
- std::unordered_map::cend
- std::unordered_map::clear
- std::unordered_map::count
- std::unordered_map::emplace
- std::unordered_map::emplace_hint
- std::unordered_map::empty
- std::unordered_map::end
- std::unordered_map::equal_range
- std::unordered_map::erase
- std::unordered_map::find
- std::unordered_map::get_allocator
- std::unordered_map::hash_function
- std::unordered_map::insert
- std::unordered_map::key_eq
- std::unordered_map::load_factor
- std::unordered_map::max_bucket_count
- std::unordered_map::max_load_factor
- std::unordered_map::max_size
- std::unordered_map::rehash
- std::unordered_map::size
- std::unordered_map::swap
ms.assetid: 7cf7cfa1-16e7-461c-a9b2-3b8d8ec24e0d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3d5fb638851398f39aad94675e1f4b0a59618dd2
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235677"
---
# <a name="unorderedmap-class"></a>unordered_map (Clase)

La clase de plantilla describe un objeto que controla una secuencia de longitud variable de elementos de tipo `std::pair<const Key, Ty>`. La secuencia está ordenada débilmente por una función hash, que divide la secuencia en un conjunto ordenado subsecuencias denominadas depósitos. Dentro de cada depósito una función de comparación determina si algún par de elementos tiene una ordenación equivalente. Cada elemento almacena dos objetos, una clave de ordenación y un valor. La secuencia se representan de tal forma que permite la búsqueda, inserción y eliminación de un elemento arbitrario con una serie de operaciones que pueden ser independientes del número de elementos de la secuencia (tiempo constante), al menos cuando todos los depósitos tienen una longitud aproximadamente igual. En el peor de los casos, cuando todos los elementos están en un depósito, el número de operaciones es proporcional al número de elementos de la secuencia (tiempo lineal). Además, la inserción de un elemento no invalida ningún iterador y al quitar un elemento solo se invalidan los iteradores que apuntan al elemento quitado.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Key,
    class Ty,
    class Hash = std::hash<Key>,
    class Pred = std::equal_to<Key>,
    class Alloc = std::allocator<std::pair<const Key, Ty>>>
class unordered_map;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Key*|El tipo de clave.|
|*Ty*|El tipo asignado.|
|*hash*|El tipo de objeto de la función hash.|
|*Pred*|El tipo de objeto de función de comparación de igualdad.|
|*Alloc*|Clase de asignador.|

## <a name="members"></a>Miembros

|Definición de tipo|Descripción|
|-|-|
|[allocator_type](#allocator_type)|El tipo de un asignador para administrar el almacenamiento.|
|[const_iterator](#const_iterator)|El tipo de un iterador constante para la secuencia controlada.|
|[const_local_iterator](#const_local_iterator)|El tipo de un iterador de depósito constante para la secuencia controlada.|
|[const_pointer](#const_pointer)|El tipo de un puntero constante a un elemento.|
|[const_reference](#const_reference)|El tipo de una referencia constante a un elemento.|
|[difference_type](#difference_type)|El tipo de una distancia con signo entre dos elementos.|
|[hasher](#hasher)|El tipo de la función hash.|
|[iterator](#iterator)|El tipo de un iterador para la secuencia controlada.|
|[key_equal](#key_equal)|El tipo de la función de comparación.|
|[key_type](#key_type)|El tipo de una clave de ordenación.|
|[local_iterator](#local_iterator)|El tipo de un iterador de depósito para la secuencia controlada.|
|[mapped_type](#mapped_type)|El tipo de un valor asignado asociado a cada clave.|
|[pointer](#pointer)|El tipo de un puntero a un elemento.|
|[reference](#reference)|El tipo de una referencia a un elemento.|
|[size_type](#size_type)|El tipo de una distancia sin signo entre dos elementos.|
|[value_type](#value_type)|El tipo de un elemento.|

|Función miembro|Descripción|
|-|-|
|[at](#at)|Busca un elemento con la clave especificada.|
|[begin](#begin)|Designa el principio de la secuencia controlada.|
|[depósito](#bucket)|Obtiene el número de depósito para un valor de clave.|
|[bucket_count](#bucket_count)|Obtiene el número de depósitos.|
|[bucket_size](#bucket_size)|Obtiene el tamaño de un depósito.|
|[cbegin](#cbegin)|Designa el principio de la secuencia controlada.|
|[cend](#cend)|Designa el final de la secuencia controlada.|
|[clear](#clear)|Quita todos los elementos.|
|[count](#count)|Busca el número de elementos que coinciden con una clave especificada.|
|[emplace](#emplace)|Agrega un elemento construido en contexto.|
|[emplace_hint](#emplace_hint)|Agrega un elemento construido en contexto, con sugerencia.|
|[empty](#empty)|Comprueba si no hay ningún elemento presente.|
|[end](#end)|Designa el final de la secuencia controlada.|
|[equal_range](#equal_range)|Busca el intervalo que coincide con una clave especificada.|
|[erase](#erase)|Quita los elementos de las posiciones especificadas.|
|[find](#find)|Busca un elemento que coincide con una clave especificada.|
|[get_allocator](#get_allocator)|Obtiene el objeto de asignador almacenado.|
|[hash_function](#hash)|Obtiene el objeto de función hash almacenado.|
|[insert](#insert)|Agrega elementos.|
|[key_eq](#key_eq)|Obtiene el objeto de función de comparación almacenado.|
|[load_factor](#load_factor)|Cuenta los elementos promedio por depósito.|
|[max_bucket_count](#max_bucket_count)|Obtiene el número máximo de depósitos.|
|[max_load_factor](#max_load_factor)|Obtiene o establece los elementos máximos por depósito.|
|[max_size](#max_size)|Obtiene el tamaño máximo de la secuencia controlada.|
|[rehash)](#rehash)|Recompila la tabla hash.|
|[size](#size)|Cuenta el número de elementos.|
|[swap](#swap)|Intercambia el contenido de dos contenedores.|
|[unordered_map](#unordered_map)|Construye un objeto contenedor.|

|Operador|Descripción|
|-|-|
|[unordered_map::operator[]](#op_at)|Busca o inserta un elemento con la clave especificada.|
|[unordered_map::operator=](#op_eq)|Copia una tabla hash.|

## <a name="remarks"></a>Comentarios

El objeto ordena la secuencia que controla llamando a dos objetos almacenados, un objeto de función de comparación de tipo [unordered_map::key_equal](#key_equal) y un objeto de función hash de tipo [unordered_map::hasher](#hasher). Se tiene acceso al primer objeto almacenado llamando a la función miembro [unordered_map::key_eq](#key_eq)`()` y se tiene acceso al segundo objeto almacenado llamando a la función miembro [unordered_map::hash_function](#hash)`()` Concretamente, para todos los valores `X` e `Y` de tipo `Key`, la llamada a `key_eq()(X, Y)` solo devuelve true si los dos valores de argumento tienen una ordenación equivalente; la llamada a `hash_function()(keyval)` produce una distribución de valores de tipo `size_t`. A diferencia de la clase de plantilla [unordered_multimap](../standard-library/unordered-multimap-class.md), un objeto de clase de plantilla `unordered_map` garantiza que `key_eq()(X, Y)` es siempre false para cualquiera de los dos elementos de la secuencia controlada. (Las claves son únicas).

El objeto también almacena un factor de carga máxima, que especifica el número promedio deseado máximo de elementos por depósito. Si la inserción de un elemento hace que [unordered_map::load_factor](#load_factor)`()` supere el factor de carga máxima, el contenedor aumenta el número de depósitos y recompila la tabla hash según sea necesario.

El orden real de los elementos de la secuencia controlada depende de la función hash, la función de comparación, el orden de inserción, el factor de carga máxima y el número actual de depósitos. En general no se puede predecir el orden de los elementos de la secuencia controlada. Sin embargo, siempre se puede asegurar que cualquier subconjunto de elementos que tengan una ordenación equivalente son adyacentes en la secuencia controlada.

El objeto asigna y libera almacenamiento para la secuencia que controla a través de un objeto asignador almacenado de tipo [unordered_map::allocator_type](#allocator_type). Ese objeto de asignador debe tener la misma interfaz externa que un objeto de clase de plantilla `allocator`. Tenga en cuenta que el objeto de asignador almacenado no se copia cuando se asigna el objeto contenedor.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<unordered_map>

**Espacio de nombres:** std

## <a name="allocator_type"></a>  unordered_map::allocator_type

El tipo de un asignador para administrar el almacenamiento.

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `Alloc`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_allocator_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Mymap c1;

    Mymap::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}

```

```Output
al == std::allocator() is true
```

## <a name="at"></a>  unordered_map::at

Busca un elemento en un unordered_map con un valor de clave especificado.

```cpp
Ty& at(const Key& key);
const Ty& at(const Key& key) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*key*|Valor de clave que se va a buscar.|

### <a name="return-value"></a>Valor devuelto

Una referencia al valor de datos del elemento encontrado.

### <a name="remarks"></a>Comentarios

Si no se encuentra el valor de clave de argumento, la función genera un objeto de clase `out_of_range`.

### <a name="example"></a>Ejemplo

```cpp
// unordered_map_at.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
typedef std::unordered_map<char, int> Mymap;
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

## <a name="begin"></a>  unordered_map::begin

Designa el principio de la secuencia controlada o un depósito.

```cpp
iterator begin();
const_iterator begin() const;
local_iterator begin(size_type nbucket);
const_local_iterator begin(size_type nbucket) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*nbucket*|Número de depósito.|

### <a name="remarks"></a>Comentarios

Las dos primeras funciones miembro devuelven un iterador hacia delante que apunta al primer elemento de la secuencia (o más allá del final de una secuencia vacía). Las dos últimas funciones miembro devuelven un iterador hacia delante que apunta al primer elemento del depósito *nbucket* (o justo después del final de un depósito vacío).

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_begin.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

#typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect first two items " [c 3] [b 2]"
    Mymap::iterator it2 = c1.begin();
    std::cout << " [" << it2->first << ", " << it2->second << "]";
    ++it2;
    std::cout << " [" << it2->first << ", " << it2->second << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
[c, 3] [b, 2]
[a, 1]
```

## <a name="bucket"></a>  unordered_map::bucket

Obtiene el número de depósito para un valor de clave.

```cpp
size_type bucket(const Key& keyval) const;
```

### <a name="parameters"></a>Parámetros

*keyVal*<br/>
Valor de clave que se va a asignar.

### <a name="remarks"></a>Comentarios

La función miembro devuelve el número de depósito que corresponde actualmente al valor de clave *keyval*.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_bucket.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display buckets for keys
    Mymap::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="bucket_count"></a>  unordered_map::bucket_count

Obtiene el número de depósitos.

```cpp
size_type bucket_count() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve el número actual de depósitos.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_bucket_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    // rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
}

```

```Output
[c, 3][b, 2][a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1

```

## <a name="bucket_size"></a>  unordered_map::bucket_size

Obtiene el tamaño de un depósito.

```cpp
size_type bucket_size(size_type nbucket) const;
```

### <a name="parameters"></a>Parámetros

*nbucket*<br/>
Número de depósito.

### <a name="remarks"></a>Comentarios

Las funciones miembro devuelven el tamaño del número de depósito *nbucket*.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_bucket_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display buckets for keys
    Mymap::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
        << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="cbegin"></a>  unordered_map::cbegin

Devuelve un **const** iterador que direcciona el primer elemento del intervalo.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Un **const** hacia delante que apunta al primer elemento del intervalo o la ubicación situada más allá del final de un intervalo vacío (para un intervalo vacío, `cbegin() == cend()`).

### <a name="remarks"></a>Comentarios

Con el valor devuelto de `cbegin`, los elementos del intervalo no se pueden modificar.

Se puede usar esta función miembro en lugar de la función miembro `begin()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, considere la posibilidad de `Container` sea modificable (no - **const**) contenedor de cualquier naturaleza que admite `begin()` y `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  unordered_map::cend

Devuelve un **const** iterador que direcciona la ubicación situada más allá del último elemento de un intervalo.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valor devuelto

Un **const** hacia delante que apunta justo después del final del intervalo.

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

## <a name="clear"></a>  unordered_map::clear

Quita todos los elementos.

```cpp
void clear();
```

### <a name="remarks"></a>Comentarios

La función miembro llama a [unordered_map::erase](#erase)`(` [unordered_map::begin](#begin)`(),` [unordered_map::end](#end)`())`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_clear.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

    // display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}

```

```Output
[c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="const_iterator"></a>  unordered_map::const_iterator

El tipo de un iterador constante para la secuencia controlada.

```cpp
typedef T1 const_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto que puede actuar como un iterador de avance constante de la secuencia controlada. Aquí se describe como sinónimo del tipo definido por implementación `T1`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_const_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}

```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="const_local_iterator"></a>  unordered_map::const_local_iterator

El tipo de un iterador de depósito constante para la secuencia controlada.

```cpp
typedef T5 const_local_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto que puede actuar como iterador constante hacia delante para un depósito. Aquí se describe como sinónimo del tipo definido por implementación `T5`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_const_local_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Mymap::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
}

```

```Output
[c, 3] [b, 2] [a, 1]
[a, 1]
```

## <a name="const_pointer"></a>  unordered_map::const_pointer

El tipo de un puntero constante a un elemento.

```cpp
typedef Alloc::const_pointer const_pointer;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto que puede actuar como puntero constante a un elemento de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_const_pointer.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
    {
        Mymap::const_pointer p = &*it;
        std::cout << " [" << p->first << ", " << p->second << "]";
    }
    std::cout << std::endl;

    return (0);
}

```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="const_reference"></a>  unordered_map::const_reference

El tipo de una referencia constante a un elemento.

```cpp
typedef Alloc::const_reference const_reference;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto que puede actuar como referencia constante a un elemento de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_const_reference.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
    {
        Mymap::const_reference ref = *it;
        std::cout << " [" << ref.first << ", " << ref.second << "]";
    }
    std::cout << std::endl;

    return (0);
}

```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="count"></a>  unordered_map::count

Busca el número de elementos que coinciden con una clave especificada.

```cpp
size_type count(const Key& keyval) const;
```

### <a name="parameters"></a>Parámetros

*keyVal*<br/>
Valor de clave que se va a buscar.

### <a name="remarks"></a>Comentarios

La función miembro devuelve el número de elementos incluidos en el rango delimitado por [unordered_map::equal_range](#equal_range)`(keyval)`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "count('A') == " << c1.count('A') << std::endl;
    std::cout << "count('b') == " << c1.count('b') << std::endl;
    std::cout << "count('C') == " << c1.count('C') << std::endl;

    return (0);
}

```

```Output
[c, 3] [b, 2] [a, 1]
count('A') == 0
count('b') == 1
count('C') == 0
```

## <a name="difference_type"></a>  unordered_map::difference_type

El tipo de una distancia con signo entre dos elementos.

```cpp
typedef T3 difference_type;
```

### <a name="remarks"></a>Comentarios

El tipo de entero con signo describe un objeto que puede representar la diferencia entre las direcciones de dos elementos cualesquiera de la secuencia controlada. Aquí se describe como sinónimo del tipo definido por implementación `T3`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_difference_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // compute positive difference
    Mymap::difference_type diff = 0;
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        ++diff;
    std::cout << "end()-begin() == " << diff << std::endl;

    // compute negative difference
    diff = 0;
    for (Mymap::const_iterator it = c1.end();
        it != c1.begin(); --it)
        --diff;
    std::cout << "begin()-end() == " << diff << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
end()-begin() == 3
begin()-end() == -3
```

## <a name="emplace"></a>  unordered_map::emplace

Inserta un elemento construido en contexto (no se realiza ninguna operación de copia o de movimiento) en un unordered_map.

```cpp
template <class... Args>
pair<iterator, bool>  emplace( Args&&... args);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*args*|Argumentos reenviados para construir un elemento que se va a insertar en el unordered_map, a menos que ya contenga un elemento cuyo valor esté ordenado de forma equivalente.|

### <a name="return-value"></a>Valor devuelto

Un `pair` cuyo **bool** componente devuelve true si se realizó una inserción y false si el `unordered_map` ya contenía un elemento cuya clave tenía un valor equivalente en la ordenación y cuyo componente de iterador devuelve la dirección donde se insertó un nuevo elemento o donde ya se encontraba el elemento.

Para tener acceso al componente de iterador de un par `pr` devuelto por esta función miembro, utilice `pr.first` y, para desreferenciarlo, utilice `*(pr.first)`. Para tener acceso a la **bool** componente de un par `pr` devuelto por esta función miembro, utilice `pr.second`.

### <a name="remarks"></a>Comentarios

Esta función no invalida ningún iterador ni ninguna referencia.

Durante la inserción, si se produce una excepción pero no ocurre en la función hash del contenedor, el contenedor no se modifica. Si la excepción se produce en la función hash, el resultado es indefinido.

Para obtener un ejemplo de código, vea [map::emplace](../standard-library/map-class.md#emplace).

## <a name="emplace_hint"></a>  unordered_map::emplace_hint

Inserta un elemento construido en contexto (no se realiza ninguna operación de copia o de movimiento), con una sugerencia de colocación.

```cpp
template <class... Args>
iterator emplace_hint(const_iterator where, Args&&... args);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*args*|Argumentos reenviados para construir un elemento que se va a insertar en el unordered_map a menos que el unordered_map ya contenga ese elemento o, más en general, a menos que ya contenga un elemento cuya clave esté ordenada de manera equivalente.|
|*where*|Sugerencia con respecto al lugar donde se va a empezar a buscar el punto correcto de inserción.|

### <a name="return-value"></a>Valor devuelto

Iterador al elemento recién insertado.

Si se produjo un error en la inserción porque el elemento ya existe, devuelve un iterador al elemento existente.

### <a name="remarks"></a>Comentarios

Esta función no invalida ninguna referencia.

Durante la inserción, si se produce una excepción pero no ocurre en la función hash del contenedor, el contenedor no se modifica. Si la excepción se produce en la función hash, el resultado es indefinido.

El [value_type](../standard-library/map-class.md#value_type) de un elemento es un par, de modo que el valor de un elemento será un par ordenado en el que el primer componente es igual que el valor de clave y el segundo componente es igual que el valor de datos del elemento.

Para obtener un ejemplo de código, vea [map::emplace_hint](../standard-library/map-class.md#emplace_hint).

## <a name="empty"></a>  unordered_map::empty

Comprueba si no hay ningún elemento presente.

```cpp
bool empty() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve true para una secuencia controlada vacía.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_empty.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

    // display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
[c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="end"></a>  unordered_map::end

Designa el final de la secuencia controlada.

```cpp
iterator end();
const_iterator end() const;
local_iterator end(size_type nbucket);
const_local_iterator end(size_type nbucket) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*nbucket*|Número de depósito.|

### <a name="remarks"></a>Comentarios

Las dos primeras funciones miembro devuelven un iterador hacia delante que apunta inmediatamente después del final de la secuencia. Las dos últimas funciones miembro devuelven un iterador hacia delante que apunta justo después del final del depósito *nbucket*.

## <a name="equal_range"></a>  unordered_map::equal_range

Busca el intervalo que coincide con una clave especificada.

```cpp
std::pair<iterator, iterator>  equal_range(const Key& keyval);
std::pair<const_iterator, const_iterator>  equal_range(const Key& keyval) const;
```

### <a name="parameters"></a>Parámetros

*keyVal*<br/>
Valor de clave que se va a buscar.

### <a name="remarks"></a>Comentarios

La función miembro devuelve un par de iteradores `X` que `[X.first, X.second)` delimita únicamente los elementos de la secuencia controlada que tienen una ordenación equivalente con *keyval*. Si no hay elementos de este tipo, los dos iteradores son `end()`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_equal_range.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // display results of failed search
    std::pair<Mymap::iterator, Mymap::iterator> pair1 =
        c1.equal_range('x');
    std::cout << "equal_range('x'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << pair1.first->first
        << ", " << pair1.first->second << "]";
    std::cout << std::endl;

    // display results of successful search
    pair1 = c1.equal_range('b');
    std::cout << "equal_range('b'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << pair1.first->first
        << ", " << pair1.first->second << "]";
    std::cout << std::endl;

    return (0);
}

```

```Output
[c, 3] [b, 2] [a, 1]
equal_range('x'):
equal_range('b'): [b, 2]
```

## <a name="erase"></a>  unordered_map::erase

Quita un elemento o un intervalo de elementos de un unordered_map de las posiciones especificadas o quita los elementos que coinciden con una clave especificada.

```cpp
iterator erase(const_iterator Where);
iterator erase(const_iterator First, const_iterator Last);
size_type erase(const key_type& Key);
```

### <a name="parameters"></a>Parámetros

*Where*<br/>
Posición del elemento que se va a quitar.

*Primero*<br/>
Posición del primer elemento que se va a quitar.

*Último*<br/>
Posición situada más allá del último elemento que se va a quitar.

*Key*<br/>
Valor de clave de los elementos que se van a quitar.

### <a name="return-value"></a>Valor devuelto

Para las dos primeras funciones miembro, iterador bidireccional que designa el primer elemento que permanece más allá de los elementos quitados, o un elemento que es el final de la asignación si no existe ese elemento.

Para la tercera función miembro, devuelve el número de elementos que se han quitado de unordered_map.

### <a name="remarks"></a>Comentarios

Para obtener un ejemplo de código, vea [map::erase](../standard-library/map-class.md#erase).

## <a name="find"></a>  unordered_map::find

Busca un elemento que coincide con una clave especificada.

```cpp
const_iterator find(const Key& keyval) const;
```

### <a name="parameters"></a>Parámetros

*keyVal*<br/>
Valor de clave que se va a buscar.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [unordered_map::equal_range](#equal_range)`(keyval).first`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_find.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // try to find and fail
    std::cout << "find('A') == "
        << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;

    // try to find and succeed
    Mymap::iterator it = c1.find('b');
    std::cout << "find('b') == "
        << std::boolalpha << (it != c1.end())
        << ": [" << it->first << ", " << it->second << "]" << std::endl;

    return (0);
}

```

```Output
[c, 3] [b, 2] [a, 1]
find('A') == false
find('b') == true: [b, 2]
```

## <a name="get_allocator"></a>  unordered_map::get_allocator

Obtiene el objeto de asignador almacenado.

```cpp
Alloc get_allocator() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve el objeto de asignador almacenado.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_get_allocator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Mymap c1;

    Mymap::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
        << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}

```

```Output
al == std::allocator() is true
```

## <a name="hash"></a>  unordered_map::hash_function

Obtiene el objeto de función hash almacenado.

```cpp
Hash hash_function() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve el objeto de función hash almacenado.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_hash_function.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    Mymap::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}

```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="hasher"></a>  unordered_map::hasher

El tipo de la función hash.

```cpp
typedef Hash hasher;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `Hash`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_hasher.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    Mymap::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}

```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="insert"></a>  unordered_map::insert

Inserta un elemento o un intervalo de elementos en un unordered_map.

```cpp
// (1) single element
pair<iterator, bool> insert(    const value_type& Val);


// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(    ValTy&& Val);


// (3) single element with hint
iterator insert(    const_iterator Where,
    const value_type& Val);


// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(    const_iterator Where,
    ValTy&& Val);


// (5) range
template <class InputIterator>
void insert(InputIterator First,
    InputIterator Last);


// (6) initializer list
void insert(initializer_list<value_type>
IList);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Val*|Valor de un elemento que se va a insertar en el unordered_map a menos que ya contenga un elemento cuya clave se ordena de forma equivalente.|
|*Where*|Lugar donde se va a iniciar la búsqueda del punto de inserción correcto.|
|*ValTy*|Parámetro de plantilla que especifica el tipo de argumento que unordered_map puede utilizar para construir un elemento de [value_type](../standard-library/map-class.md#value_type)y realiza *Val* como argumento.|
|*Primero*|Posición del primer elemento que se va a copiar.|
|*Último*|Posición situada más allá del último elemento que se va a copiar.|
|*InputIterator*|Argumento de la función de plantilla que cumple los requisitos de un [iterador de entrada](../standard-library/input-iterator-tag-struct.md) que apunta a elementos de un tipo que se puede usar para crear objetos [value_type](../standard-library/map-class.md#value_type).|
|*IList*|El elemento [initializer_list](../standard-library/initializer-list.md) del que se van a copiar los elementos.|

### <a name="return-value"></a>Valor devuelto

Las funciones miembro de un único elemento, (1) y (2), devuelven un [par](../standard-library/pair-structure.md) cuyo **bool** componente es true si se realizó una inserción y false si el unordered_map ya contenía un elemento cuya clave tenía un valor equivalente en la ordenación. El componente de iterador del par de valor devuelto apunta al elemento recién insertado si el **bool** componente es true, o al elemento existente si la **bool** componente es false.

Las funciones miembro de un solo elemento con sugerencia, (3) y (4), devuelven un iterador que apunta a la posición donde se insertó el nuevo elemento en el unordered_map o, si ya existe un elemento con una clave equivalente, al elemento existente.

### <a name="remarks"></a>Comentarios

Esta función no invalida ningún iterador, puntero o referencia.

Durante la inserción de un solo elemento, si se produce una excepción pero no se realiza en la función hash del contenedor, no se modifica el estado del contenedor. Si la excepción se produce en la función hash, el resultado es indefinido. Durante la inserción de varios elementos, si se produce una excepción, el contenedor se deja en un estado sin especificar pero válido.

Para tener acceso al componente de iterador de un `pair` `pr` devuelto por la función miembro de un único elemento, utilice `pr.first`; para desreferenciar el iterador dentro del par devuelto, utilice `*pr.first`, especificando un elemento. Para tener acceso a la **bool** componente, use `pr.second`. Para obtener un ejemplo, vea el código de ejemplo que se muestra más adelante en este artículo.

El objeto [value_type](../standard-library/map-class.md#value_type) de un contenedor es un typedef que pertenece al contenedor y, para map, `map<K, V>::value_type` es `pair<const K, V>`. El valor de un elemento es un par ordenado en el que el primer componente es igual al valor de clave y el segundo componente es igual al valor de datos del elemento.

La función miembro de intervalo (5) inserta la secuencia de valores de elemento en un unordered_map que corresponde a cada elemento direccionado por un iterador en el intervalo `[First, Last)`; por lo tanto, `Last` no se inserta. La función miembro de contenedor `end()` hace referencia a la posición situada justo después del último elemento del contenedor; por ejemplo, la instrucción `m.insert(v.begin(), v.end());` intenta insertar todos los elementos de `v` en `m`. Solo se insertan los elementos que tienen valores únicos en el intervalo; se omiten los duplicados. Para observar qué elementos se rechazan, utilice las versiones de un solo elemento de `insert`.

La función miembro de lista de inicializadores (6) usa una [initializer_list](../standard-library/initializer-list.md) para copiar elementos en el unordered_map.

Para la inserción de un elemento construido en contexto (es decir, no se realiza ninguna operación de copia o movimiento), vea [unordered_map::emplace](#emplace) y [unordered_map::emplace_hint](#emplace_hint).

Para obtener un ejemplo de código, vea [map::insert](../standard-library/map-class.md#insert).

## <a name="iterator"></a>  unordered_map::iterator

El tipo de un iterador para la secuencia controlada.

```cpp
typedef T0 iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto que puede actuar como un iterador de avance de la secuencia controlada. Aquí se describe como sinónimo del tipo definido por implementación `T0`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="key_eq"></a>  unordered_map::key_eq

Obtiene el objeto de función de comparación almacenado.

```cpp
Pred key_eq() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve el objeto de función de comparación almacenado.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_key_eq.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    Mymap::key_equal cmpfn = c1.key_eq();
    std::cout << "cmpfn('a', 'a') == "
        << std::boolalpha << cmpfn('a', 'a') << std::endl;
    std::cout << "cmpfn('a', 'b') == "
        << std::boolalpha << cmpfn('a', 'b') << std::endl;

    return (0);
    }

```

```Output
cmpfn('a', 'a') == true
cmpfn('a', 'b') == false
```

## <a name="key_equal"></a>  unordered_map::key_equal

El tipo de la función de comparación.

```cpp
typedef Pred key_equal;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `Pred`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_key_equal.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    Mymap::key_equal cmpfn = c1.key_eq();
    std::cout << "cmpfn('a', 'a') == "
        << std::boolalpha << cmpfn('a', 'a') << std::endl;
    std::cout << "cmpfn('a', 'b') == "
        << std::boolalpha << cmpfn('a', 'b') << std::endl;

    return (0);
    }

```

```Output
cmpfn('a', 'a') == true
cmpfn('a', 'b') == false
```

## <a name="key_type"></a>  unordered_map::key_type

El tipo de una clave de ordenación.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `Key`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_key_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="load_factor"></a>  unordered_map::load_factor

Cuenta los elementos promedio por depósito.

```cpp
float load_factor() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve `(float)`[unordered_map::size](#size)`() / (float)`[unordered_map::bucket_count](#bucket_count)`()`, el promedio de elementos por depósito.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_load_factor.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1

```

## <a name="local_iterator"></a>  unordered_map::local_iterator

Tipo de un iterador de depósito.

```cpp
typedef T4 local_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto que puede actuar como iterador hacia delante para un depósito. Aquí se describe como sinónimo del tipo definido por implementación `T4`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_local_iterator.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect bucket containing 'a'
    Mymap::local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << lit->first << ", " << lit->second << "]";

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
[a, 1]
```

## <a name="mapped_type"></a>  unordered_map::mapped_type

El tipo de un valor asignado asociado a cada clave.

```cpp
typedef Ty mapped_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `Ty`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_mapped_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="max_bucket_count"></a>  unordered_map::max_bucket_count

Obtiene el número máximo de depósitos.

```cpp
size_type max_bucket_count() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve el número máximo de depósitos que se admiten actualmente.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_max_bucket_count.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1

```

## <a name="max_load_factor"></a>  unordered_map::max_load_factor

Obtiene o establece los elementos máximos por depósito.

```cpp
float max_load_factor() const;


void max_load_factor(float factor);
```

### <a name="parameters"></a>Parámetros

*factor*<br/>
El nuevo factor de carga máxima.

### <a name="remarks"></a>Comentarios

La primera función miembro devuelve el factor de carga máxima almacenado. La segunda función miembro reemplaza el factor de carga máxima almacenado con *factor*.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_max_load_factor.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_bucket_count() == "
        << c1.max_bucket_count() << std::endl;
    std::cout << "max_load_factor() == "
        << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_bucket_count() == 8
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_bucket_count() == 128
max_load_factor() == 0.1

```

## <a name="max_size"></a>  unordered_map::max_size

Obtiene el tamaño máximo de la secuencia controlada.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve la longitud de la secuencia más larga que puede controlar el objeto.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_max_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    std::cout << "max_size() == " << c1.max_size() << std::endl;

    return (0);
    }

```

```Output
max_size() == 536870911
```

## <a name="op_at"></a>  unordered_map::operator[]

Busca o inserta un elemento con la clave especificada.

```cpp
Ty& operator[](const Key& keyval);

Ty& operator[](Key&& keyval);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*keyVal*|Valor de clave que se va a buscar o insertar.|

### <a name="return-value"></a>Valor devuelto

Referencia al valor de datos del elemento insertado.

### <a name="remarks"></a>Comentarios

Si el valor de clave de argumento no se encuentra, se inserta junto con el valor predeterminado del tipo de datos.

Se puede usar `operator[]` para insertar elementos en un mapa *m* mediante *m*[_ *Key*] = `DataValue`; donde `DataValue` es el valor del `mapped_type` del elemento con un valor de clave de \_ *Key*.

Cuando se emplea `operator[]` para insertar elementos, la referencia devuelta no indica si una inserción cambia un elemento ya existente o crea uno nuevo. Se pueden usar las funciones miembro [find](../standard-library/map-class.md#find) e [insert](../standard-library/map-class.md#insert) para determinar si ya existe un elemento con una clave especificada antes de una inserción.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_operator_sub.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>
#include <string>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// try to find and fail
    std::cout << "c1['A'] == " << c1['A'] << std::endl;

// try to find and succeed
    std::cout << "c1['a'] == " << c1['a'] << std::endl;

// redisplay contents
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// insert by moving key
    std::unordered_map<string, int> c2;
    std::string str("abc");
    std::cout << "c2[std::move(str)] == " << c2[std::move(str)] << std::endl;
    std::cout << "c2["abc"] == " << c2["abc"] << std::endl;

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
c1['A'] == 0
c1['a'] == 1
[c, 3] [b, 2] [A, 0] [a, 1]
c2[move(str)] == 0
c2["abc"] == 1
```

### <a name="remarks"></a>Comentarios

La función miembro determina el iterador `where` como el valor devuelto de [unordered_map::insert](#insert)`(` [unordered_map::value_type](#value_type)`(keyval, Ty())`. (Inserta un elemento con la clave especificada si no existe tal elemento). A continuación devuelve una referencia a `(*where).second`.

## <a name="op_eq"></a>  unordered_map::operator=

Reemplaza los elementos de este unordered_map mediante los elementos de otro unordered_map.

```cpp
unordered_map& operator=(const unordered_map& right);

unordered_map& operator=(unordered_map&& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*right*|El unordered_map desde el que la función de operador asigna el contenido.|

### <a name="remarks"></a>Comentarios

La primera versión copia todos los elementos de *derecho* a este unordered_map.

La segunda versión mueve todos los elementos de *derecho* a este unordered_map.

Se descarta cualquier elemento que esté en este unordered_map antes de que `operator`= se ejecute.

### <a name="example"></a>Ejemplo

```cpp
// unordered_map_operator_as.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

int main( )
   {
   using namespace std;
   unordered_map<int, int> v1, v2, v3;
   unordered_map<int, int>::iterator iter;

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

## <a name="pointer"></a>  unordered_map::pointer

El tipo de un puntero a un elemento.

```cpp
typedef Alloc::pointer pointer;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto que puede actuar como puntero a un elemento de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_pointer.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Mymap::pointer p = &*it;
        std::cout << " [" << p->first << ", " << p->second << "]";
        }
    std::cout << std::endl;

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="reference"></a>  unordered_map::reference

El tipo de una referencia a un elemento.

```cpp
typedef Alloc::reference reference;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto que puede actuar como referencia a un elemento de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_reference.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::iterator it = c1.begin();
        it != c1.end(); ++it)
        {
        Mymap::reference ref = *it;
        std::cout << " [" << ref.first << ", " << ref.second << "]";
        }
    std::cout << std::endl;

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
```

## <a name="rehash"></a>  unordered_map::rehash

Recompila la tabla hash.

```cpp
void rehash(size_type nbuckets);
```

### <a name="parameters"></a>Parámetros

*nbuckets*<br/>
Número solicitado de depósitos.

### <a name="remarks"></a>Comentarios

La función miembro modifica el número de depósitos para que sea al menos *nbuckets* y recompila la tabla hash según sea necesario.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_rehash.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// inspect current parameters
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// change max_load_factor and redisplay
    c1.max_load_factor(0.10f);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;
    std::cout << std::endl;

// rehash and redisplay
    c1.rehash(100);
    std::cout << "bucket_count() == " << c1.bucket_count() << std::endl;
    std::cout << "load_factor() == " << c1.load_factor() << std::endl;
    std::cout << "max_load_factor() == " << c1.max_load_factor() << std::endl;

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
bucket_count() == 8
load_factor() == 0.375
max_load_factor() == 4

bucket_count() == 8
load_factor() == 0.375
max_load_factor() == 0.1

bucket_count() == 128
load_factor() == 0.0234375
max_load_factor() == 0.1
```

## <a name="size"></a>  unordered_map::size

Cuenta el número de elementos.

```cpp
size_type size() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_size.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

// clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert(Mymap::value_type('d', 4));
    c1.insert(Mymap::value_type('e', 5));

// display contents " [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
size == 0
empty() == true

[e, 5] [d, 4]
size == 2
empty() == false
```

## <a name="size_type"></a>  unordered_map::size_type

El tipo de una distancia sin signo entre dos elementos.

```cpp
typedef T2 size_type;
```

### <a name="remarks"></a>Comentarios

El tipo de entero sin signo describe un objeto que puede representar la longitud de cualquier secuencia controlada. Aquí se describe como sinónimo del tipo definido por implementación `T2`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_size_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::size_type sz = c1.size();

    std::cout << "size == " << sz << std::endl;

    return (0);
    }

```

```Output
size == 0
```

## <a name="swap"></a>  unordered_map::swap

Intercambia el contenido de dos contenedores.

```cpp
void swap(unordered_map& right);
```

### <a name="parameters"></a>Parámetros

*right*<br/>
El contenedor con el que se intercambia.

### <a name="remarks"></a>Comentarios

La función miembro intercambia las secuencias controladas entre `*this` y *derecho*. Si [unordered_map::get_allocator](#get_allocator)`() == right.get_allocator()`, lo hace en tiempo constante, inicia una excepción solo como resultado de copiar el objeto de rasgos almacenado de tipo `Tr` y no invalida referencias, punteros o iteradores que designan elementos en las dos secuencias controladas. De lo contrario, realiza varias asignaciones de elementos y llamadas de constructor proporcionales al número de elementos de ambas secuencias controladas.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_swap.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    Mymap c2;

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    c1.swap(c2);

// display contents " [f 6] [e 5] [d 4]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    swap(c1, c2);

// display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
    }

```

```Output
[c, 3] [b, 2] [a, 1]
[f, 6] [e, 5] [d, 4]
[c, 3] [b, 2] [a, 1]
```

## <a name="unordered_map"></a>  unordered_map::unordered_map

Construye un objeto contenedor.

```cpp
unordered_map(const unordered_map& Right);

explicit unordered_map(
    size_type Bucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Allocator());

unordered_map(unordered_map&& Right);
unordered_map(initializer_list<Type> IList);
unordered_map(initializer_list<Type> IList, size_type Bucket_count);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash,
    KeyEqual& equal);

unordered_map(
    initializer_list<Type> IList,
    size_type Bucket_count,
    const Hash& Hash,
    KeyEqual& Equal
    const Allocator& Al);

template <class InIt>
unordered_map(
    InputIterator First,
    InputIterator Last,
    size_type Bucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Alloc());
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|*Al*|Objeto de asignador que se va a almacenar.|
|*Comp.*|Objeto de función de comparación que se va a almacenar.|
|*hash*|Objeto de función hash que se va a almacenar.|
|*Bucket_count*|Número mínimo de depósitos.|
|*Derecha*|Contenedor que se va a copiar.|
|*Primero*||
|*Último*||
|*IList*|initializer_list que contiene los elementos que se van a copiar.|

### <a name="remarks"></a>Comentarios

El primer constructor especifica una copia de la secuencia controlada por `right`. El segundo constructor especifica una secuencia controlada vacía. El tercer constructor inserta la secuencia de valores de elemento `[first, last)`. El cuarto constructor especifica una copia de la secuencia moviendo `right`.

Todos los constructores también inicializan varios valores almacenados. Constructor de copias, los valores se obtienen de *derecha*. De lo contrario:

el número mínimo de depósitos es el argumento *Bucket_count*, si está presente; en caso contrario, es un valor predeterminado descrito aquí como el valor definido por la implementación `N0`.

El objeto de función hash es el argumento *Hash*, si está presente; de lo contrario es `Hash()`.

El objeto de función de comparación es el argumento *Comp*, si está presente; de lo contrario es `Pred()`.

El objeto de asignador es el argumento *Al*, si está presente; de lo contrario, es `Alloc()`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_construct.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>
#include <initializer_list>

using namespace std;

using Mymap = unordered_map<char, int>;

int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c2(8,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >());

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    // display contents " [f 6] [e 5] [d 4]"
    for (const auto& c : c2) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c3(c1.begin(),
        c1.end(),
        8,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >());

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c3) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    Mymap c4(move(c3));

    // display contents " [c 3] [b 2] [a 1]"
    for (const auto& c : c4) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
    cout << endl;

    // Construct with an initializer_list
    unordered_map<int, char> c5({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } });
    for (const auto& c : c5) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size
    unordered_map<int, char> c6({ { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } }, 4);
    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
    cout << endl;

    // Initializer_list plus size and hash
    unordered_map<int, char, hash<char>> c7(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size, hash, and key_equal
    unordered_map<int, char, hash<char>, equal_to<char>> c8(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>(),
        equal_to<char>()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;

    // Initializer_list plus size, hash, key_equal, and allocator
    unordered_map<int, char, hash<char>, equal_to<char>> c9(
        { { 5, 'g' }, { 6, 'h' }, { 7, 'i' }, { 8, 'j' } },
        4,
        hash<char>(),
        equal_to<char>(),
        allocator<pair<const char, int> >()
    );

    for (const auto& c : c1) {
        cout << " [" << c.first << ", " << c.second << "]";
    }
    cout << endl;
}
```

```Output
[a, 1] [b, 2] [c, 3]
[d, 4] [e, 5] [f, 6]
[a, 1] [b, 2] [c, 3]
[a, 1] [b, 2] [c, 3]

[5, g] [6, h] [7, i] [8, j]
[a, 1] [b, 2] [c, 3]

[a, 1] [b, 2] [c, 3]
[a, 1] [b, 2] [c, 3]
[a, 1] [b, 2] [c, 3]
```

## <a name="value_type"></a>  unordered_map::value_type

El tipo de un elemento.

```cpp
typedef std::pair<const Key, Ty> value_type;
```

### <a name="remarks"></a>Comentarios

El tipo describe un elemento de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_map__unordered_map_value_type.cpp
// compile with: /EHsc
#include <unordered_map>
#include <iostream>

typedef std::unordered_map<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    // add a value and reinspect
    Mymap::key_type key = 'd';
    Mymap::mapped_type mapped = 4;
    Mymap::value_type val = Mymap::value_type(key, mapped);
    c1.insert(val);

    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}

```

```Output
[c, 3] [b, 2] [a, 1]
[d, 4] [c, 3] [b, 2] [a, 1]
```

## <a name="see-also"></a>Vea también

[<unordered_map>](../standard-library/unordered-map.md)<br/>
[Contenedores](../cpp/containers-modern-cpp.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
