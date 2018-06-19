---
title: unordered_set (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- unordered_set/std::unordered_set
- unordered_set/std::unordered_set::allocator_type
- unordered_set/std::unordered_set::const_iterator
- unordered_set/std::unordered_set::const_local_iterator
- unordered_set/std::unordered_set::const_pointer
- unordered_set/std::unordered_set::const_reference
- unordered_set/std::unordered_set::difference_type
- unordered_set/std::unordered_set::hasher
- unordered_set/std::unordered_set::iterator
- unordered_set/std::unordered_set::key_equal
- unordered_set/std::unordered_set::key_type
- unordered_set/std::unordered_set::local_iterator
- unordered_set/std::unordered_set::pointer
- unordered_set/std::unordered_set::reference
- unordered_set/std::unordered_set::size_type
- unordered_set/std::unordered_set::value_type
- unordered_set/std::unordered_set::begin
- unordered_set/std::unordered_set::bucket
- unordered_set/std::unordered_set::bucket_count
- unordered_set/std::unordered_set::bucket_size
- unordered_set/std::unordered_set::cbegin
- unordered_set/std::unordered_set::cend
- unordered_set/std::unordered_set::clear
- unordered_set/std::unordered_set::count
- unordered_set/std::unordered_set::emplace
- unordered_set/std::unordered_set::emplace_hint
- unordered_set/std::unordered_set::empty
- unordered_set/std::unordered_set::end
- unordered_set/std::unordered_set::equal_range
- unordered_set/std::unordered_set::erase
- unordered_set/std::unordered_set::find
- unordered_set/std::unordered_set::get_allocator
- unordered_set/std::unordered_set::hash
- unordered_set/std::unordered_set::insert
- unordered_set/std::unordered_set::key_eq
- unordered_set/std::unordered_set::load_factor
- unordered_set/std::unordered_set::max_bucket_count
- unordered_set/std::unordered_set::max_load_factor
- unordered_set/std::unordered_set::max_size
- unordered_set/std::unordered_set::rehash
- unordered_set/std::unordered_set::size
- unordered_set/std::unordered_set::swap
- unordered_set/std::unordered_set::unordered_set
- unordered_set/std::unordered_set::operator=
- unordered_set/std::unordered_set::hash_function
dev_langs:
- C++
helpviewer_keywords:
- std::unordered_set
- std::unordered_set::allocator_type
- std::unordered_set::const_iterator
- std::unordered_set::const_local_iterator
- std::unordered_set::const_pointer
- std::unordered_set::const_reference
- std::unordered_set::difference_type
- std::unordered_set::hasher
- std::unordered_set::iterator
- std::unordered_set::key_equal
- std::unordered_set::key_type
- std::unordered_set::local_iterator
- std::unordered_set::pointer
- std::unordered_set::reference
- std::unordered_set::size_type
- std::unordered_set::value_type
- std::unordered_set::begin
- std::unordered_set::bucket
- std::unordered_set::bucket_count
- std::unordered_set::bucket_size
- std::unordered_set::cbegin
- std::unordered_set::cend
- std::unordered_set::clear
- std::unordered_set::count
- std::unordered_set::emplace
- std::unordered_set::emplace_hint
- std::unordered_set::empty
- std::unordered_set::end
- std::unordered_set::equal_range
- std::unordered_set::erase
- std::unordered_set::find
- std::unordered_set::get_allocator
- std::unordered_set::hash
- std::unordered_set::insert
- std::unordered_set::key_eq
- std::unordered_set::load_factor
- std::unordered_set::max_bucket_count
- std::unordered_set::max_load_factor
- std::unordered_set::max_size
- std::unordered_set::rehash
- std::unordered_set::size
- std::unordered_set::swap
- std::unordered_set::unordered_set
- std::unordered_set::operator=
- std::unordered_set::allocator_type
- std::unordered_set::const_iterator
- std::unordered_set::const_local_iterator
- std::unordered_set::const_pointer
- std::unordered_set::const_reference
- std::unordered_set::difference_type
- std::unordered_set::hasher
- std::unordered_set::iterator
- std::unordered_set::key_equal
- std::unordered_set::key_type
- std::unordered_set::local_iterator
- std::unordered_set::pointer
- std::unordered_set::reference
- std::unordered_set::size_type
- std::unordered_set::value_type
- std::unordered_set::begin
- std::unordered_set::bucket
- std::unordered_set::bucket_count
- std::unordered_set::bucket_size
- std::unordered_set::cbegin
- std::unordered_set::cend
- std::unordered_set::clear
- std::unordered_set::count
- std::unordered_set::emplace
- std::unordered_set::emplace_hint
- std::unordered_set::empty
- std::unordered_set::end
- std::unordered_set::equal_range
- std::unordered_set::erase
- std::unordered_set::find
- std::unordered_set::get_allocator
- std::unordered_set::hash_function
- std::unordered_set::insert
- std::unordered_set::key_eq
- std::unordered_set::load_factor
- std::unordered_set::max_bucket_count
- std::unordered_set::max_load_factor
- std::unordered_set::max_size
- std::unordered_set::rehash
- std::unordered_set::size
- std::unordered_set::swap
ms.assetid: ac08084e-05a7-48c0-9ae4-d40c529922dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e31c0eb559f36b1921660a900a6ade0ba095b6f8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862892"
---
# <a name="unorderedset-class"></a>unordered_set (Clase)

La clase de plantilla describe un objeto que controla una secuencia de longitud variable de elementos de tipo `const Key`. La secuencia está ordenada débilmente por una función hash, que divide la secuencia en un conjunto ordenado subsecuencias denominadas depósitos. Dentro de cada depósito una función de comparación determina si algún par de elementos tiene una ordenación equivalente. Cada elemento actúa como clave de ordenación y como valor. La secuencia se representan de tal forma que permite la búsqueda, inserción y eliminación de un elemento arbitrario con una serie de operaciones que pueden ser independientes del número de elementos de la secuencia (tiempo constante), al menos cuando todos los depósitos tienen una longitud aproximadamente igual. En el peor de los casos, cuando todos los elementos están en un depósito, el número de operaciones es proporcional al número de elementos de la secuencia (tiempo lineal). Además, la inserción de un elemento no invalida ningún iterador y al quitar un elemento solo se invalidan los iteradores que apuntan al elemento quitado.

## <a name="syntax"></a>Sintaxis

```cpp
template <
   class Key,
   class Hash = std::hash<Key>,
   class Pred = std::equal_to<Key>,
   class Alloc = std::allocator<Key>>
class unordered_set;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|`Key`|El tipo de clave.|
|`Hash`|El tipo de objeto de la función hash.|
|`Pred`|El tipo de objeto de función de comparación de igualdad.|
|`Alloc`|Clase de asignador.|

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
|[pointer](#pointer)|El tipo de un puntero a un elemento.|
|[reference](#reference)|El tipo de una referencia a un elemento.|
|[size_type](#size_type)|El tipo de una distancia sin signo entre dos elementos.|
|[value_type](#value_type)|El tipo de un elemento.|

|Función miembro|Descripción|
|-|-|
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
|[unordered_set](#unordered_set)|Construye un objeto contenedor.|

|Operadores|Descripción|
|-|-|
|[unordered_set::operator=](#op_eq)|Copia una tabla hash.|

## <a name="remarks"></a>Comentarios

El objeto ordena la secuencia que controla llamando a dos objetos almacenados, un objeto de función de comparación de tipo [unordered_set::key_equal](#key_equal) y un objeto de función hash de tipo [unordered_set::hasher](#hasher). Se tiene acceso al primer objeto almacenado llamando a la función miembro [unordered_set::key_eq](#key_eq)`()` y se tiene acceso al segundo objeto almacenado llamando a la función miembro [unordered_set::hash_function](#hash)`()`. Concretamente, para todos los valores `X` e `Y` de tipo `Key`, la llamada a `key_eq()(X, Y)` solo devuelve true si los dos valores de argumento tienen una ordenación equivalente; la llamada a `hash_function()(keyval)` produce una distribución de valores de tipo `size_t`. A diferencia de la clase de plantilla[unordered_multiset (clase)](../standard-library/unordered-multiset-class.md), un objeto de clase de plantilla `unordered_set` garantiza que `key_eq()(X, Y)` siempre es false para dos elementos cualesquiera de la secuencia controlada. (Las claves son únicas).

El objeto también almacena un factor de carga máxima, que especifica el número promedio deseado máximo de elementos por depósito. Si la inserción de un elemento hace que [unordered_set::load_factor](#load_factor)`()` supere el factor de carga máxima, el contenedor aumenta el número de depósitos y recompila la tabla hash según sea necesario.

El orden real de los elementos de la secuencia controlada depende de la función hash, la función de comparación, el orden de inserción, el factor de carga máxima y el número actual de depósitos. En general no se puede predecir el orden de los elementos de la secuencia controlada. Sin embargo, siempre se puede asegurar que cualquier subconjunto de elementos que tengan una ordenación equivalente son adyacentes en la secuencia controlada.

El objeto asigna y libera almacenamiento para la secuencia que controla a través de un objeto asignador almacenado de tipo [unordered_set::allocator_type](#allocator_type). Ese objeto de asignador debe tener la misma interfaz externa que un objeto de clase de plantilla `allocator`. Tenga en cuenta que el objeto de asignador almacenado no se copia cuando se asigna el objeto contenedor.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<unordered_set>

**Espacio de nombres:** std

## <a name="allocator_type"></a>  unordered_set::allocator_type

El tipo de un asignador para administrar el almacenamiento.

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `Alloc`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_allocator_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Myset c1;

    Myset::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
    << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="begin"></a>  unordered_set::begin

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
|`nbucket`|Número de depósito.|

### <a name="remarks"></a>Comentarios

Las dos primeras funciones miembro devuelven un iterador hacia delante que apunta al primer elemento de la secuencia (o más allá del final de una secuencia vacía). Las dos últimas funciones miembro devuelven un iterador hacia delante que apunta al primer elemento del depósito `nbucket` (o más allá del final de un depósito vacío).

### <a name="example"></a>Ejemplo

```cpp
// unordered_set_begin.cpp
// compile using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_set>
#include <iostream>

using namespace std;

typedef unordered_set<char> MySet;

int main()
{
    MySet c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents using range-based for
    for (auto it : c1) {
    cout << " [" << it << "]";
    }

    cout << endl;

    // display contents using explicit for
    for (MySet::const_iterator it = c1.begin(); it != c1.end(); ++it) {
        cout << " [" << *it << "]";
    }

    cout << std::endl;

    // display first two items
    MySet::iterator it2 = c1.begin();
    cout << " [" << *it2 << "]";
    ++it2;
    cout << " [" << *it2 << "]";
    cout << endl;

    // display bucket containing 'a'
    MySet::const_local_iterator lit = c1.begin(c1.bucket('a'));
    cout << " [" << *lit << "]";

    return (0);
}
```

```Output
 [a] [b] [c]
 [a] [b] [c]
 [a] [b]
 [a]
```

## <a name="bucket"></a>  unordered_set::bucket

Obtiene el número de depósito para un valor de clave.

```cpp
size_type bucket(const Key& keyval) const;
```

### <a name="parameters"></a>Parámetros

`keyval` Valor de clave que se va a asignar.

### <a name="remarks"></a>Comentarios

La función miembro devuelve el número de depósito que corresponde actualmente al valor de clave `keyval`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_bucket.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // display buckets for keys
    Myset::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
    << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="bucket_count"></a>  unordered_set::bucket_count

Obtiene el número de depósitos.

```cpp
size_type bucket_count() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve el número actual de depósitos.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_bucket_count.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
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
 [c] [b] [a]
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

## <a name="bucket_size"></a>  unordered_set::bucket_size

Obtiene el tamaño de un depósito.

```cpp
size_type bucket_size(size_type nbucket) const;
```

### <a name="parameters"></a>Parámetros

`nbucket` El número de depósito.

### <a name="remarks"></a>Comentarios

Las funciones miembro devuelven el tamaño del número de depósito `nbucket`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_bucket_size.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // display buckets for keys
    Myset::size_type bs = c1.bucket('a');
    std::cout << "bucket('a') == " << bs << std::endl;
    std::cout << "bucket_size(" << bs << ") == " << c1.bucket_size(bs)
    << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
bucket('a') == 7
bucket_size(7) == 1
```

## <a name="cbegin"></a>  unordered_set::cbegin

Devuelve un iterador `const` que direcciona el primer elemento del intervalo.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador `const` de acceso hacia delante que apunta al primer elemento del intervalo o la ubicación situada más allá del final de un intervalo vacío (para un intervalo vacío, `cbegin() == cend()`).

### <a name="remarks"></a>Comentarios

Con el valor devuelto de `cbegin`, los elementos del intervalo no se pueden modificar.

Se puede usar esta función miembro en lugar de la función miembro `begin()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, se considera que `Container` es un contenedor modificable (distinto de `const`) de cualquier naturaleza que admite `begin()` y `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 isContainer<T>::iterator
auto i2 = Container.cbegin();

// i2 isContainer<T>::const_iterator
```

## <a name="cend"></a>  unordered_set::cend

Devuelve un iterador `const` que direcciona la ubicación situada más allá del último elemento de un intervalo.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador `const` de acceso hacia delante que apunta justo después del final del intervalo.

### <a name="remarks"></a>Comentarios

`cend` se usa para probar si un iterador ha sobrepasado el final de su intervalo.

Se puede usar esta función miembro en lugar de la función miembro `end()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, se considera que `Container` es un contenedor modificable (distinto de `const`) de cualquier naturaleza que admite `end()` y `cend()`.

```cpp
auto i1 = Container.end();
// i1 isContainer<T>::iterator
auto i2 = Container.cend();

// i2 isContainer<T>::const_iterator
```

El valor devuelto por `cend` no se debe desreferenciar.

## <a name="clear"></a>  unordered_set::clear

Quita todos los elementos.

```cpp
void clear();
```

### <a name="remarks"></a>Comentarios

La función miembro llama a [unordered_set::erase](#erase)`(` [unordered_set::begin](#begin)`(),` [unordered_set::end](#end)`())`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_clear.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents " [e] [d]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
size == 0
empty() == true
 [e] [d]
size == 2
empty() == false
```

## <a name="const_iterator"></a>  unordered_set::const_iterator

El tipo de un iterador constante para la secuencia controlada.

```cpp
typedef T1 const_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto que puede actuar como un iterador de avance constante de la secuencia controlada. Aquí se describe como sinónimo del tipo definido por implementación `T1`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_const_iterator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
    std::cout << " [" << *it << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
```

## <a name="const_local_iterator"></a>  unordered_set::const_local_iterator

El tipo de un iterador de depósito constante para la secuencia controlada.

```cpp
typedef T5 const_local_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto que puede actuar como iterador constante hacia delante para un depósito. Aquí se describe como sinónimo del tipo definido por implementación `T5`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_const_local_iterator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::const_local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << *lit << "]";

    return (0);
}
```

```Output
 [c] [b] [a]
 [a]
```

## <a name="const_pointer"></a>  unordered_set::const_pointer

El tipo de un puntero constante a un elemento.

```cpp
typedef Alloc::const_pointer const_pointer;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto que puede actuar como puntero constante a un elemento de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_const_pointer.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::const_pointer p = &*it;
        std::cout << " [" << *p << "]";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
```

## <a name="const_reference"></a>  unordered_set::const_reference

El tipo de una referencia constante a un elemento.

```cpp
typedef Alloc::const_reference const_reference;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto que puede actuar como referencia constante a un elemento de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_const_reference.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::const_reference ref = *it;
        std::cout << " [" << ref << "]";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
```

## <a name="count"></a>  unordered_set::count

Busca el número de elementos que coinciden con una clave especificada.

```cpp
size_type count(const Key& keyval) const;
```

### <a name="parameters"></a>Parámetros

`keyval` Valor de clave que se buscará.

### <a name="remarks"></a>Comentarios

La función miembro devuelve el número de elementos incluidos en el rango delimitado por [unordered_set::equal_range](#equal_range)`(keyval)`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_count.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    std::cout << "count('A') == " << c1.count('A') << std::endl;
    std::cout << "count('b') == " << c1.count('b') << std::endl;
    std::cout << "count('C') == " << c1.count('C') << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
count('A') == 0
count('b') == 1
count('C') == 0
```

## <a name="difference_type"></a>  unordered_set::difference_type

El tipo de una distancia con signo entre dos elementos.

```cpp
typedef T3 difference_type;
```

### <a name="remarks"></a>Comentarios

El tipo de entero con signo describe un objeto que puede representar la diferencia entre las direcciones de dos elementos cualesquiera de la secuencia controlada. Aquí se describe como sinónimo del tipo definido por implementación `T3`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_difference_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // compute positive difference
    Myset::difference_type diff = 0;
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    std::cout << "end()-begin() == " << diff << std::endl;

    // compute negative difference
    diff = 0;
    for (Myset::const_iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    std::cout << "begin()-end() == " << diff << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
end()-begin() == 3
begin()-end() == -3
```

## <a name="emplace"></a>  unordered_set::emplace

Inserta un elemento construido en contexto (no se realiza ninguna operación de copia o de movimiento).

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
Args&&... args);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|`args`|Argumentos reenviados para construir un elemento que se va a insertar en el unordered_set, a menos que ya contenga un elemento cuyo valor esté ordenado de forma equivalente.|

### <a name="return-value"></a>Valor devuelto

`pair` cuyo componente `bool` devuelve true si se realizó una inserción y false si el `unordered_set` ya contenía un elemento cuya clave tenía un valor equivalente en la ordenación, y cuyo componente de iterador devuelve la dirección donde se ha insertado un nuevo elemento o donde ya estaba el elemento.

Para tener acceso al componente de iterador de un par `pr` devuelto por esta función miembro, utilice `pr.first` y, para desreferenciarlo, utilice `*(pr.first)`. Para tener acceso al componente `bool` de un par `pr` devuelto por esta función miembro, utilice `pr.second`.

### <a name="remarks"></a>Comentarios

Esta función no invalida ningún iterador ni ninguna referencia.

Durante la inserción, si se produce una excepción pero no ocurre en la función hash del contenedor, el contenedor no se modifica. Si la excepción se produce en la función hash, el resultado es indefinido.

Para obtener un ejemplo de código, vea [set::emplace](../standard-library/set-class.md#emplace).

## <a name="emplace_hint"></a>  unordered_set::emplace_hint

Inserta un elemento construido en contexto (no se realiza ninguna operación de copia o de movimiento), con una sugerencia de colocación.

```cpp
template <class... Args>
iterator emplace_hint(
const_iteratorwhere,
Args&&... args);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|`args`|Argumentos reenviados para construir un elemento que se va a insertar en el unordered_set a menos que el unordered_set ya contenga ese elemento o, más en general, a menos que ya contenga un elemento cuya clave esté ordenada de manera equivalente.|
|`where`|Sugerencia con respecto al lugar donde se va a empezar a buscar el punto correcto de inserción.|

### <a name="return-value"></a>Valor devuelto

Iterador al elemento recién insertado.

Si se produjo un error en la inserción porque el elemento ya existe, devuelve un iterador al elemento existente.

### <a name="remarks"></a>Comentarios

Esta función no invalida ningún iterador ni ninguna referencia.

Durante la inserción, si se produce una excepción pero no ocurre en la función hash del contenedor, el contenedor no se modifica. Si la excepción se produce en la función hash, el resultado es indefinido.

Para obtener un ejemplo de código, vea [set::emplace_hint](../standard-library/set-class.md#emplace_hint).

## <a name="empty"></a>  unordered_set::empty

Comprueba si no hay ningún elemento presente.

```cpp
bool empty() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve true para una secuencia controlada vacía.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_empty.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents " [e] [d]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
size == 0
empty() == true
 [e] [d]
size == 2
empty() == false
```

## <a name="end"></a>  unordered_set::end

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
|`nbucket`|Número de depósito.|

### <a name="remarks"></a>Comentarios

Las dos primeras funciones miembro devuelven un iterador hacia delante que apunta inmediatamente después del final de la secuencia. Las dos últimas funciones miembro devuelven un iterador hacia delante que apunta inmediatamente después del final del depósito `nbucket`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_end.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // inspect last two items " [a] [b]"
    Myset::iterator it2 = c1.end();
    --it2;
    std::cout << " [" << *it2 << "]";
    --it2;
    std::cout << " [" << *it2 << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::const_local_iterator lit = c1.end(c1.bucket('a'));
    --lit;
    std::cout << " [" << *lit << "]";

    return (0);
}
```

```Output
 [c] [b] [a]
 [a] [b]
 [a]
```

## <a name="equal_range"></a>  unordered_set::equal_range

Busca el intervalo que coincide con una clave especificada.

```cpp
std::pair<iterator, iterator>
equal_range(const Key& keyval);

std::pair<const_iterator, const_iterator>
equal_range(const Key& keyval) const;
```

### <a name="parameters"></a>Parámetros

`keyval` Valor de clave que se buscará.

### <a name="remarks"></a>Comentarios

La función miembro devuelve un par de iteradores `X` que`[X.first, X.second)` delimita únicamente los elementos de la secuencia controlada que tienen una ordenación equivalente con `keyval`. Si no hay elementos de este tipo, los dos iteradores son `end()`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_equal_range.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // display results of failed search
    std::pair<Myset::iterator, Myset::iterator> pair1 =
    c1.equal_range('x');
    std::cout << "equal_range('x'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << *pair1.first << "]";
    std::cout << std::endl;

    // display results of successful search
    pair1 = c1.equal_range('b');
    std::cout << "equal_range('b'):";
    for (; pair1.first != pair1.second; ++pair1.first)
        std::cout << " [" << *pair1.first << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
equal_range('x'):
equal_range('b'): [b]
```

## <a name="erase"></a>  unordered_set::erase

Quita un elemento o un intervalo de elementos de un unordered_set de las posiciones especificadas o quita los elementos que coinciden con una clave especificada.

```cpp
iterator erase(const_iterator Where);

iterator erase(const_iterator First, const_iterator Last);

size_type erase(const key_type& Key);
```

### <a name="parameters"></a>Parámetros

`Where` Posición del elemento que se va a quitar.

`First` Posición del primer elemento va a quitar.

`Last` Posición situada más allá del último elemento que se va a quitar.

`Key` El valor de clave de los elementos que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Para las dos primeras funciones miembro, iterador bidireccional que designa el primer elemento que permanece más allá de los elementos quitados, o un elemento que es el final de unordered_set si no existe ese elemento.

Para la tercera función miembro, devuelve el número de elementos que se han quitado de unordered_set.

### <a name="remarks"></a>Comentarios

Para obtener un ejemplo de código, vea [set::erase](../standard-library/set-class.md#erase).

## <a name="find"></a>  unordered_set::find

Busca un elemento que coincide con una clave especificada.

```cpp
const_iterator find(const Key& keyval) const;
```

### <a name="parameters"></a>Parámetros

`keyval` Valor de clave que se buscará.

### <a name="remarks"></a>Comentarios

La función miembro devuelve [unordered_set::equal_range](#equal_range)`(keyval).first`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_find.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // try to find and fail
    std::cout << "find('A') == "
    << std::boolalpha << (c1.find('A') != c1.end()) << std::endl;

    // try to find and succeed
    Myset::iterator it = c1.find('b');
    std::cout << "find('b') == "
    << std::boolalpha << (it != c1.end())
    << ": [" << *it << "]" << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
find('A') == false
find('b') == true: [b]
```

## <a name="get_allocator"></a>  unordered_set::get_allocator

Obtiene el objeto de asignador almacenado.

```cpp
Alloc get_allocator() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve el objeto de asignador almacenado.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_get_allocator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
typedef std::allocator<std::pair<const char, int> > Myalloc;
int main()
{
    Myset c1;

    Myset::allocator_type al = c1.get_allocator();
    std::cout << "al == std::allocator() is "
    << std::boolalpha << (al == Myalloc()) << std::endl;

    return (0);
}
```

```Output
al == std::allocator() is true
```

## <a name="hash"></a>  unordered_set::hash_function

Obtiene el objeto de función hash almacenado.

```cpp
Hash hash_function() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve el objeto de función hash almacenado.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_hash_function.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="hasher"></a>  unordered_set::hasher

El tipo de la función hash.

```cpp
typedef Hash hasher;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `Hash`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_hasher.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::hasher hfn = c1.hash_function();
    std::cout << "hfn('a') == " << hfn('a') << std::endl;
    std::cout << "hfn('b') == " << hfn('b') << std::endl;

    return (0);
}
```

```Output
hfn('a') == 1630279
hfn('b') == 1647086
```

## <a name="insert"></a>  unordered_set::insert

Inserta un elemento o un intervalo de elementos en un unordered_set.

```cpp
// (1) single element
pair<iterator, bool> insert(const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool> insert(ValTy&& Val);

// (3) single element with hint
iterator insert(const_iterator Where, const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(const_iterator Where, ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(InputIterator First, InputIterator Last);

// (6) initializer list
void insert(initializer_list<value_type> IList);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|`Val`|Valor de un elemento que se va a insertar en el unordered_set a menos que ya contenga un elemento cuya clave se ordena de forma equivalente.|
|`Where`|Lugar donde se va a iniciar la búsqueda del punto de inserción correcto.|
|`ValTy`|Parámetro de plantilla que especifica el tipo de argumento que el unordered_set puede utilizar para construir un elemento de[value_type](../standard-library/map-class.md#value_type)y el reenvío directo `Val` como un argumento.|
|`First`|Posición del primer elemento que se va a copiar.|
|`Last`|Posición situada más allá del último elemento que se va a copiar.|
|`InputIterator`|Argumento de la función de plantilla que cumple los requisitos de un [iterador de entrada](../standard-library/input-iterator-tag-struct.md) que apunta a elementos de un tipo que se puede usar para crear objetos [value_type](../standard-library/map-class.md#value_type).|
|`IList`|La [initializer_list](../standard-library/initializer-list.md) de la que se van a copiar los elementos.|

### <a name="return-value"></a>Valor devuelto

Las funciones miembro de un único elemento, (1) y (2), devuelven un[par](../standard-library/pair-structure.md) cuyo `bool` componente es true si se realizó una inserción y false si el unordered_set ya contenía un elemento cuya clave tenía un valor equivalente en el ordenación. El componente de iterador del par de valor devuelto apunta al elemento recién insertado si el componente `bool` es true, o al elemento existente si el componente `bool` es false.

Las funciones miembro de un solo elemento con sugerencia, (3) y (4), devuelven un iterador que apunta a la posición donde se insertó el nuevo elemento en el unordered_set o, si ya existe un elemento con una clave equivalente, al elemento existente.

### <a name="remarks"></a>Comentarios

Esta función no invalida ningún iterador, puntero o referencia.

Durante la inserción de un solo elemento, si se produce una excepción pero no se realiza en la función hash del contenedor, no se modifica el estado del contenedor. Si la excepción se produce en la función hash, el resultado es indefinido. Durante la inserción de varios elementos, si se produce una excepción, el contenedor se deja en un estado sin especificar pero válido.

Para tener acceso al componente de iterador de un `pair` `pr` devuelto por las funciones miembro de un único elemento, use `pr.first`; para desreferenciar el iterador dentro del par devuelto, utilice`*pr.first`, lo que le proporciona un elemento. Para tener acceso al componente `bool`, utilice `pr.second`. Para obtener un ejemplo, vea el código de ejemplo que se muestra más adelante en este artículo.

El[value_type](../standard-library/map-class.md#value_type) de un contenedor es un typedef que pertenece al contenedor y, para un conjunto, `unordered_set<V>::value_type` es de tipo `const V`.

La función miembro de intervalo (5) inserta la secuencia de valores de elemento en un unordered_set que corresponde a cada elemento direccionado por un iterador en el intervalo `[First, Last)`; por lo tanto, `Last` no se inserta. La función miembro de contenedor `end()` hace referencia a la posición situada justo después del último elemento del contenedor; por ejemplo, la instrucción `s.insert(v.begin(), v.end());` intenta insertar todos los elementos de `v` en `s`. Solo se insertan los elementos que tienen valores únicos en el intervalo; se omiten los duplicados. Para observar qué elementos se rechazan, utilice las versiones de un solo elemento de `insert`.

La función miembro de lista de inicializadores (6) usa una [initializer_list](../standard-library/initializer-list.md) para copiar elementos en el unordered_set.

Para la inserción de un elemento construido en contexto, es decir, se realiza ninguna operación de copia o movimiento: vea[set::emplace](../standard-library/set-class.md#emplace) y[set::emplace_hint](../standard-library/set-class.md#emplace_hint).

Para obtener un ejemplo de código, vea [set::insert](../standard-library/set-class.md#insert).

## <a name="iterator"></a>  unordered_set::iterator

Un tipo que proporciona un [iterador hacia delante](../standard-library/forward-iterator-tag-struct.md) constante que puede leer elementos en un unordered_set.

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [begin](../standard-library/set-class.md#begin) para obtener un ejemplo de cómo declarar y usar un **iterador**.

## <a name="key_eq"></a>  unordered_set::key_eq

Obtiene el objeto de función de comparación almacenado.

```cpp
Pred key_eq() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve el objeto de función de comparación almacenado.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_key_eq.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::key_equal cmpfn = c1.key_eq();
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

## <a name="key_equal"></a>  unordered_set::key_equal

El tipo de la función de comparación.

```cpp
typedef Pred key_equal;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `Pred`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_key_equal.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    Myset::key_equal cmpfn = c1.key_eq();
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

## <a name="key_type"></a>  unordered_set::key_type

El tipo de una clave de ordenación.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `Key`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_key_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // add a value and reinspect
    Myset::key_type key = 'd';
    Myset::value_type val = key;
    c1.insert(val);

    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
 [d] [c] [b] [a]
```

## <a name="load_factor"></a>  unordered_set::load_factor

Cuenta los elementos promedio por depósito.

```cpp
float load_factor() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve `(float)`[unordered_set::size](#size)`() / (float)`[unordered_set::bucket_count](#bucket_count)`()`, el promedio de elementos por depósito.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_load_factor.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
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
 [c] [b] [a]
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

## <a name="local_iterator"></a>  unordered_set::local_iterator

Tipo de un iterador de depósito.

```cpp
typedef T4 local_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto que puede actuar como iterador hacia delante para un depósito. Aquí se describe como sinónimo del tipo definido por implementación `T4`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_local_iterator.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // inspect bucket containing 'a'
    Myset::local_iterator lit = c1.begin(c1.bucket('a'));
    std::cout << " [" << *lit << "]";

    return (0);
}
```

```Output
 [c] [b] [a]
 [a]
```

## <a name="max_bucket_count"></a>  unordered_set::max_bucket_count

Obtiene el número máximo de depósitos.

```cpp
size_type max_bucket_count() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve el número máximo de depósitos que se admiten actualmente.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_max_bucket_count.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
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
 [c] [b] [a]
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

## <a name="max_load_factor"></a>  unordered_set::max_load_factor

Obtiene o establece los elementos máximos por depósito.

```cpp
float max_load_factor() const;

void max_load_factor(float factor);
```

### <a name="parameters"></a>Parámetros

`factor` El nuevo factor de carga máxima.

### <a name="remarks"></a>Comentarios

La primera función miembro devuelve el factor de carga máxima almacenado. La segunda función miembro reemplaza el factor de carga máxima almacenado con `factor`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_max_load_factor.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
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
 [c] [b] [a]
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

## <a name="max_size"></a>  unordered_set::max_size

Obtiene el tamaño máximo de la secuencia controlada.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve la longitud de la secuencia más larga que puede controlar el objeto.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_max_size.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    std::cout << "max_size() == " << c1.max_size() << std::endl;

    return (0);
}
```

```Output
max_size() == 4294967295
```

## <a name="op_eq"></a>  unordered_set::operator=

Copia una tabla hash.

```cpp
unordered_set& operator=(const unordered_set& right);

unordered_set& operator=(unordered_set&& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|`right`|El[unordered_set](../standard-library/unordered-set-class.md) que se va a copiar en el `unordered_set`.|

### <a name="remarks"></a>Comentarios

Después de borrar todos los elementos existentes en un `unordered_set`, `operator=` copia o mueve el contenido de `right` a `unordered_set`.

### <a name="example"></a>Ejemplo

```cpp
// unordered_set_operator_as.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

int main( )
{
    using namespace std;
    unordered_set<int> v1, v2, v3;
    unordered_set<int>::iterator iter;

    v1.insert(10);

    cout << "v1 = " ;
    for (iter = v1.begin(); iter != v1.end(); iter++)
        cout << *iter << " ";
    cout << endl;

    v2 = v1;
    cout << "v2 = ";
    for (iter = v2.begin(); iter != v2.end(); iter++)
        cout << *iter << " ";
    cout << endl;

    // move v1 into v2
    v2.clear();
    v2 = move(v1);
    cout << "v2 = ";
    for (iter = v2.begin(); iter != v2.end(); iter++)
        cout << *iter << " ";
    cout << endl;
}
```

## <a name="pointer"></a>  unordered_set::pointer

El tipo de un puntero a un elemento.

```cpp
typedef Alloc::pointer pointer;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto que puede actuar como puntero a un elemento de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_pointer.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::key_type key = *it;
        Myset::pointer p = &key;
        std::cout << " [" << *p << "]";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
```

## <a name="reference"></a>  unordered_set::reference

El tipo de una referencia a un elemento.

```cpp
typedef Alloc::reference reference;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto que puede actuar como referencia a un elemento de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_reference.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)
    {
        Myset::key_type key = *it;
        Myset::reference ref = key;
        std::cout << " [" << ref << "]";
    }
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
```

## <a name="rehash"></a>  unordered_set::rehash

Recompila la tabla hash.

```cpp
void rehash(size_type nbuckets);
```

### <a name="parameters"></a>Parámetros

`nbuckets` El número solicitado de depósitos.

### <a name="remarks"></a>Comentarios

La función miembro modifica el número de depósitos para que sea al menos `nbuckets` y vuelve a generar la tabla hash según sea necesario.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_rehash.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
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
 [c] [b] [a]
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

## <a name="size"></a>  unordered_set::size

Cuenta el número de elementos.

```cpp
size_type size() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_size.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // clear the container and reinspect
    c1.clear();
    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;
    std::cout << std::endl;

    c1.insert('d');
    c1.insert('e');

    // display contents " [e] [d]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    std::cout << "size == " << c1.size() << std::endl;
    std::cout << "empty() == " << std::boolalpha << c1.empty() << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
size == 0
empty() == true

[e] [d]
size == 2
empty() == false
```

## <a name="size_type"></a>  unordered_set::size_type

El tipo de una distancia sin signo entre dos elementos.

```cpp
typedef T2 size_type;
```

### <a name="remarks"></a>Comentarios

El tipo de entero sin signo describe un objeto que puede representar la longitud de cualquier secuencia controlada. Aquí se describe como sinónimo del tipo definido por implementación `T2`.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_size_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;
    Myset::size_type sz = c1.size();

    std::cout << "size == " << sz << std::endl;

    return (0);
}
```

```Output
size == 0
```

## <a name="swap"></a>  unordered_set::swap

Intercambia el contenido de dos contenedores.

```cpp
void swap(unordered_set& right);
```

### <a name="parameters"></a>Parámetros

`right` El contenedor que se va a intercambiar con.

### <a name="remarks"></a>Comentarios

La función miembro intercambia las secuencias controladas entre `*this` y `right`. Si [unordered_set::get_allocator](#get_allocator)`() == right.get_allocator()`, lo hace en tiempo constante, produce una excepción solo como resultado de copiar el objeto de rasgos almacenado de tipo `Tr`, y no invalida ninguna referencia, punteros, o iteradores que designan elementos en las dos secuencias controladas. De lo contrario, realiza varias asignaciones de elementos y llamadas de constructor proporcionales al número de elementos de ambas secuencias controladas.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_swap.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    Myset c2;

    c2.insert('d');
    c2.insert('e');
    c2.insert('f');

    c1.swap(c2);

    // display contents " [f] [e] [d]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    swap(c1, c2);

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
 [f] [e] [d]
 [c] [b] [a]
```

## <a name="unordered_set"></a>  unordered_set::unordered_set

Construye un objeto contenedor.

```cpp
unordered_set(const unordered_set& Right);

explicit unordered_set(
    size_typebucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Alloc());

unordered_set(unordered_set&& Right);

unordered_set(initializer_list<Type> IList);

unordered_set(initializer_list<Type> IList, size_typebucket_count);

unordered_set(
    initializer_list<Type> IList,
    size_typebucket_count,
    const Hash& Hash);

unordered_set(
    initializer_list<Type> IList,
    size_typebucket_count,
    const Hash& Hash,
    const Comp& Comp);

unordered_set(
    initializer_list<Type> IList,
    size_typebucket_count,
    const Hash& Hash,
    const Comp& Comp,
    const Allocator& Al);

template <class InputIterator>
unordered_set(
    InputIteratorfirst,
    InputIteratorlast,
    size_typebucket_count = N0,
    const Hash& Hash = Hash(),
    const Comp& Comp = Comp(),
    const Allocator& Al = Alloc());
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|-|-|
|`InputIterator`|Tipo de iterador.|
|`Al`|Objeto de asignador que se va a almacenar.|
|`Comp`|Objeto de función de comparación que se va a almacenar.|
|`Hash`|Objeto de función hash que se va a almacenar.|
|`bucket_count`|Número mínimo de depósitos.|
|`Right`|Contenedor que se va a copiar.|
|`IList`|initializer_list que contiene los elementos que se van a copiar.|

### <a name="remarks"></a>Comentarios

El primer constructor especifica una copia de la secuencia controlada por `Right`. El segundo constructor especifica una secuencia controlada vacía. El tercer constructor especifica una copia de la secuencia moviendo `Right` Los constructores cuarto a octavo utilizan una initializer_list para especificar los elementos que se van a copiar. El noveno constructor inserta la secuencia de valores de elemento `[first, last)`.

Todos los constructores también inicializan varios valores almacenados. Para el constructor de copias, los valores se obtienen de `Right`. De lo contrario:

El número mínimo de depósitos es el argumento `bucket_count`, si está presente; de lo contrario, es un valor predeterminado descrito aquí como el valor `N0` definido por la implementación.

El objeto de función hash es el argumento `Hash`, si está presente; de lo contrario, es `Hash()`.

El objeto de función de comparación es el argumento `Comp`, si está presente; de lo contrario, es `Comp()`.

El objeto de asignador es el argumento `Al`, si está presente; de lo contrario, es `Alloc()`.

## <a name="value_type"></a>  unordered_set::value_type

El tipo de un elemento.

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>Comentarios

El tipo describe un elemento de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// std__unordered_set__unordered_set_value_type.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    // add a value and reinspect
    Myset::key_type key = 'd';
    Myset::value_type val = key;
    c1.insert(val);

    for (Myset::const_iterator it = c1.begin(); it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
 [c] [b] [a]
 [d] [c] [b] [a]
```

## <a name="see-also"></a>Vea también

[<unordered_set>](../standard-library/unordered-set.md)<br/>
[Contenedores](../cpp/containers-modern-cpp.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
