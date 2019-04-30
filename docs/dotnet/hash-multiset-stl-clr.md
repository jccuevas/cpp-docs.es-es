---
title: hash_multiset (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::hash_multiset
- cliext::hash_multiset::begin
- cliext::hash_multiset::bucket_count
- cliext::hash_multiset::clear
- cliext::hash_multiset::const_iterator
- cliext::hash_multiset::const_reference
- cliext::hash_multiset::const_reverse_iterator
- cliext::hash_multiset::count
- cliext::hash_multiset::difference_type
- cliext::hash_multiset::empty
- cliext::hash_multiset::end
- cliext::hash_multiset::equal_range
- cliext::hash_multiset::erase
- cliext::hash_multiset::find
- cliext::hash_multiset::generic_container
- cliext::hash_multiset::generic_iterator
- cliext::hash_multiset::generic_reverse_iterator
- cliext::hash_multiset::generic_value
- cliext::hash_multiset::hash_delegate
- cliext::hash_multiset::hash_multiset
- cliext::hash_multiset::hasher
- cliext::hash_multiset::insert
- cliext::hash_multiset::iterator
- cliext::hash_multiset::key_comp
- cliext::hash_multiset::key_compare
- cliext::hash_multiset::key_type
- cliext::hash_multiset::load_factor
- cliext::hash_multiset::lower_bound
- cliext::hash_multiset::make_value
- cliext::hash_multiset::max_load_factor
- cliext::hash_multiset::operator=
- cliext::hash_multiset::rbegin
- cliext::hash_multiset::reference
- cliext::hash_multiset::rehash
- cliext::hash_multiset::rend
- cliext::hash_multiset::reverse_iterator
- cliext::hash_multiset::size
- cliext::hash_multiset::size_type
- cliext::hash_multiset::swap
- cliext::hash_multiset::to_array
- cliext::hash_multiset::upper_bound
- cliext::hash_multiset::value_comp
- cliext::hash_multiset::value_compare
- cliext::hash_multiset::value_type
helpviewer_keywords:
- <cliext/hash_set> header [STL/CLR]
- hash_multiset class [STL/CLR]
- <hash_set> header [STL/CLR]
- begin member [STL/CLR]
- bucket_count member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- count member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- equal_range member [STL/CLR]
- erase member [STL/CLR]
- find member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- hash_delegate member [STL/CLR]
- hash_multiset member [STL/CLR]
- hasher member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- load_factor member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- max_load_factor member [STL/CLR]
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rehash member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 8462bd21-6829-4dd3-ac81-c42d6fdf92f0
ms.openlocfilehash: 8d8e7ab9bcbaf9ea8ce95558c53d5936473f9c8f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222980"
---
# <a name="hashmultiset-stlclr"></a>hash_multiset (STL/CLR)

La clase de plantilla describe un objeto que controla una secuencia de elementos de longitud variable que tiene acceso bidireccional. Usar el contenedor `hash_multiset` para administrar una secuencia de elementos como una tabla hash, cada entrada de la tabla almacenar un bidireccional vinculado lista de nodos y cada nodo almacenar un elemento. El valor de cada elemento se utiliza como clave, para ordenar la secuencia.

En la descripción siguiente, `GValue` es el mismo que `GKey`, que es igual a su vez *clave* a menos que este último es un tipo de referencia, en cuyo caso es `Key^`.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename Key>
    ref class hash_multiset
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>Parámetros

*Key*<br/>
El tipo del componente clave de un elemento de la secuencia controlada.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<cliext/hash_set >

**Namespace:** cliext

## <a name="declarations"></a>Declaraciones

|Definición de tipo|Descripción|
|---------------------|-----------------|
|[hash_multiset::const_iterator (STL/CLR)](#const_iterator)|El tipo de un iterador constante para la secuencia controlada.|
|[hash_multiset::const_reference (STL/CLR)](#const_reference)|El tipo de una referencia constante a un elemento.|
|[hash_multiset::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|El tipo de un iterador invertido constante para la secuencia controlada.|
|[hash_multiset::difference_type (STL/CLR)](#difference_type)|El tipo de una distancia entre dos elementos (posiblemente con signo).|
|[hash_multiset::generic_container (STL/CLR)](#generic_container)|El tipo de la interfaz genérica para el contenedor.|
|[hash_multiset::generic_iterator (STL/CLR)](#generic_iterator)|El tipo de iterador para la interfaz genérica para el contenedor.|
|[hash_multiset::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|El tipo de un iterador inverso de la interfaz genérica para el contenedor.|
|[hash_multiset::generic_value (STL/CLR)](#generic_value)|El tipo de un elemento de la interfaz genérica para el contenedor.|
|[hash_multiset::hasher (STL/CLR)](#hasher)|El delegado de hash para una clave.|
|[hash_multiset::iterator (STL/CLR)](#iterator)|El tipo de un iterador para la secuencia controlada.|
|[hash_multiset::key_compare (STL/CLR)](#key_compare)|Delegado de ordenación para dos claves.|
|[hash_multiset::key_type (STL/CLR)](#key_type)|El tipo de una clave de ordenación.|
|[hash_multiset::reference (STL/CLR)](#reference)|El tipo de una referencia a un elemento.|
|[hash_multiset::reverse_iterator (STL/CLR)](#reverse_iterator)|El tipo de un iterador invertido para la secuencia controlada.|
|[hash_multiset::size_type (STL/CLR)](#size_type)|El tipo de una distancia (no negativo) entre dos elementos.|
|[hash_multiset::value_compare (STL/CLR)](#value_compare)|Delegado de ordenación para dos valores de elemento.|
|[hash_multiset::value_type (STL/CLR)](#value_type)|El tipo de un elemento.|

|Función miembro|Descripción|
|---------------------|-----------------|
|[hash_multiset::begin (STL/CLR)](#begin)|Designa el principio de la secuencia controlada.|
|[hash_multiset::bucket_count (STL/CLR)](#bucket_count)|Cuenta el número de depósitos.|
|[hash_multiset::clear (STL/CLR)](#clear)|Quita todos los elementos.|
|[hash_multiset::count (STL/CLR)](#count)|Recuentos de elementos que coinciden con una clave especificada.|
|[hash_multiset::empty (STL/CLR)](#empty)|Comprueba si no hay ningún elemento presente.|
|[hash_multiset::end (STL/CLR)](#end)|Designa el final de la secuencia controlada.|
|[hash_multiset::equal_range (STL/CLR)](#equal_range)|Busca el intervalo que coincide con una clave especificada.|
|[hash_multiset::erase (STL/CLR)](#erase)|Quita los elementos de las posiciones especificadas.|
|[hash_multiset::find (STL/CLR)](#find)|Busca un elemento que coincide con una clave especificada.|
|[hash_multiset::hash_delegate (STL/CLR)](#hash_delegate)|Copia al delegado de hash para una clave.|
|[hash_multiset::hash_multiset (STL/CLR)](#hash_multiset)|Construye un objeto contenedor.|
|[hash_multiset::insert (STL/CLR)](#insert)|Agrega elementos.|
|[hash_multiset::key_comp (STL/CLR)](#key_comp)|Copia al delegado de ordenación de dos claves.|
|[hash_multiset::load_factor (STL/CLR)](#load_factor)|Cuenta los elementos promedio por depósito.|
|[hash_multiset::lower_bound (STL/CLR)](#lower_bound)|Busca el principio del intervalo que coincide con una clave especificada.|
|[hash_multiset::make_value (STL/CLR)](#make_value)|Construye un objeto de valor.|
|[hash_multiset::max_load_factor (STL/CLR)](#max_load_factor)|Obtiene o establece los elementos máximos por depósito.|
|[hash_multiset::rbegin (STL/CLR)](#rbegin)|Designa el principio de la secuencia controlada inversa.|
|[hash_multiset::rehash (STL/CLR)](#rehash)|Recompila la tabla hash.|
|[hash_multiset::rend (STL/CLR)](#rend)|Designa el final de la secuencia controlada inversa.|
|[hash_multiset::size (STL/CLR)](#size)|Cuenta el número de elementos.|
|[hash_multiset::swap (STL/CLR)](#swap)|Intercambia el contenido de dos contenedores.|
|[hash_multiset::to_array (STL/CLR)](#to_array)|Copia la secuencia controlada a una nueva matriz.|
|[hash_multiset::upper_bound (STL/CLR)](#upper_bound)|Busca el final del intervalo que coincide con una clave especificada.|
|[hash_multiset::value_comp (STL/CLR)](#value_comp)|Copia al delegado de ordenación de dos valores de elemento.|

|Operador|Descripción|
|--------------|-----------------|
|[hash_multiset::operator= (STL/CLR)](#op)|Reemplaza la secuencia controlada.|

## <a name="interfaces"></a>Interfaces

|Interfaz|Descripción|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplicar un objeto.|
|<xref:System.Collections.IEnumerable>|Secuencia a través de los elementos.|
|<xref:System.Collections.ICollection>|Mantener el grupo de elementos.|
|<xref:System.Collections.Generic.IEnumerable%601>|Secuencia a través de los elementos con tipo.|
|<xref:System.Collections.Generic.ICollection%601>|Mantener el grupo de elementos con tipo.|
|IHash\<clave, valor >|Mantener contenedor genérico.|

## <a name="remarks"></a>Comentarios

El objeto asigna y libera almacenamiento para la secuencia que controla como nodos individuales en una lista vinculada bidireccional. Para acelerar el acceso, el objeto también mantiene una matriz de longitud variable de punteros en la lista (la tabla hash), administrar de forma eficaz la lista completa como una secuencia de sublistas, o cubos. Inserta elementos en un cubo que mantiene ordenada por la modificación de los vínculos entre los nodos nunca copiando el contenido de un nodo a otro. Esto significa que puede insertar y quitar elementos libremente sin perturbar elementos restantes.

El objeto ordena cada depósito controla mediante una llamada a un objeto delegado almacenado de tipo [hash_set:: key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md). Puede especificar el objeto de delegado almacenado cuando se construye el objeto hash_set; Si se especifica ningún objeto de delegado, el valor predeterminado es la comparación `operator<=(key_type, key_type)`.

Tiene acceso al objeto de delegado almacenado mediante una llamada a la función miembro [hash_set:: key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)`()`. Este tipo de objeto de delegado debe definir una ordenación equivalente entre las claves de tipo [hash_set:: KEY_TYPE (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md). Esto significa que, en las dos claves `X` y `Y`:

`key_comp()(X, Y)` Devuelve el valor booleano mismo resultado en cada llamada.

Si `key_comp()(X, Y) && key_comp()(Y, X)` es true, a continuación, `X` y `Y` se dice que tienen una ordenación equivalente.

Cualquier regla de ordenación que se comporta como `operator<=(key_type, key_type)`, `operator>=(key_type, key_type)` o `operator==(key_type, key_type)` define eqivalent orden.

Tenga en cuenta que el contenedor solo garantiza que los elementos cuyas claves tienen una ordenación equivalente (y qué hash en el mismo valor entero) son adyacentes dentro de un depósito. A diferencia de la clase de plantilla [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md), un objeto de clase de plantilla `hash_multiset` no requiere que las claves para todos los elementos sean únicas. (Dos o más teclas pueden tener una ordenación equivalente).

El objeto determina qué cubo debe contener una clave de ordenación especificada mediante una llamada a un objeto delegado almacenado de tipo [hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md). Acceder a este objeto almacenado llamando a la función miembro [hash_set::hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md) `()` para obtener un valor entero que depende del valor de clave. Puede especificar el objeto de delegado almacenado cuando se construye el objeto hash_set; Si se especifica ningún objeto de delegado, el valor predeterminado es la función `System::Object::hash_value(key_type)`. Esto significa que para cualquier clave `X` y `Y`:

`hash_delegate()(X)` Devuelve el mismo resultado entero en cada llamada.

Si `X` y `Y` tienen una ordenación equivalente, a continuación, `hash_delegate()(X)` debe devolver el mismo resultado entero como `hash_delegate()(Y)`.

Cada elemento actúa como una clave y un valor. La secuencia se representa de forma que permita la búsqueda, inserción y eliminación de un elemento arbitrario con un número de operaciones que es independiente del número de elementos de la secuencia (tiempo constante): al menos en el mejor de los casos. Además, la inserción de un elemento no invalida ningún iterador y al quitar un elemento solo se invalidan los iteradores que apuntan al elemento quitado.

Si los valores hash no se distribuyen uniformemente, sin embargo, puede degenerar una tabla hash. En casos extremos, para una función hash que siempre devuelve el mismo valor, búsqueda, inserción y eliminación son proporcionales al número de elementos de la secuencia (tiempo lineal). El contenedor protegida elegir una función hash razonable, el tamaño de depósito promedio y tamaño de la tabla hash (número total de depósitos), pero puede invalidar cualquiera o todas estas opciones. Consulte, por ejemplo, las funciones [hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md) y [hash_set::rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md).

Un objeto hash_multiset es compatible con los iteradores bidireccionales, lo que significa que puede ejecutar paso a paso para los elementos adyacentes que proporciona un iterador que designa un elemento de la secuencia controlada. Un nodo principal especial que se corresponde con el iterador devuelto por [hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`. Puede reducir este iterador para alcanzar el último elemento de la secuencia controlada, si está presente. Puede incrementar un iterador hash_multiset para alcanzar el nodo principal y, a continuación, comparará igual a `end()`. Pero no se puede desreferenciar el iterador devuelto por `end()`.

Tenga en cuenta que no puede hacer referencia a un elemento del objeto hash_multiset directamente dado su posición numérica--que requiera un iterador de acceso aleatorio.

Un iterador hash_multiset almacena un identificador a su nodo asociado hash_multiset, que a su vez almacena un identificador de su contenedor asociado. Puede usar iteradores sólo con sus objetos de contenedor asociado. Un iterador hash_multiset sigue siendo válido siempre y cuando su nodo asociado hash_multiset está asociado a algún objeto hash_multiset. Además, un iterador válido es dereferenceable, puede usar para tener acceso o modificar el valor del elemento designa--siempre y cuando no es igual a `end()`.

Borrar o quitar un elemento llama al destructor para su valor almacenado. Destruir el contenedor, borra todos los elementos. Por lo tanto, un contenedor cuyo tipo de elemento es una clase ref garantiza que ningún elemento durar más que el contenedor. Sin embargo, tenga en cuenta que un contenedor de controladores no *no* destruir sus elementos.

## <a name="members"></a>Miembros

## <a name="begin"></a> hash_multiset::begin (STL/CLR)

Designa el principio de la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator begin();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve un iterador bidireccional que designa el primer elemento de la secuencia controlada o justo después del final de una secuencia vacía. Se usa para obtener un iterador que designa el `current` principio de la secuencia controlada, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_begin.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Myhash_multiset::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);
    return (0);
    }
```

```Output
a b c
*begin() = a
*++begin() = b
```

## <a name="bucket_count"></a> hash_multiset::bucket_count (STL/CLR)

Cuenta el número de depósitos.

### <a name="syntax"></a>Sintaxis

```cpp
int bucket_count();
```

### <a name="remarks"></a>Comentarios

Las funciones miembro devuelve el número actual de depósitos. Se usa para determinar el tamaño de la tabla hash.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_bucket_count.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="clear"></a> hash_multiset::clear (STL/CLR)

Quita todos los elementos.

### <a name="syntax"></a>Sintaxis

```cpp
void clear();
```

### <a name="remarks"></a>Comentarios

La función miembro llama eficazmente a [hash_multiset:: Erase (STL/CLR)](../dotnet/hash-multiset-erase-stl-clr.md) `(` [hash_multiset:: begin (STL/CLR)](../dotnet/hash-multiset-begin-stl-clr.md) `(),` [hash_multiset:: end (STL/CLR) ](../dotnet/hash-multiset-end-stl-clr.md)`())`. Usarlo para asegurarse de que está vacía la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_clear.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    // add elements and clear again
    c1.insert(L'a');
    c1.insert(L'b');

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 0
a b
size() = 0
```

## <a name="const_iterator"></a> hash_multiset::const_iterator (STL/CLR)

El tipo de un iterador constante para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto de tipo sin especificar `T2` que puede actuar como un iterador constante bidireccional para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_const_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Myhash_multiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reference"></a> hash_multiset::const_reference (STL/CLR)

El tipo de una referencia constante a un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Comentarios

El tipo describe una referencia constante a un elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_const_reference.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Myhash_multiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Myhash_multiset::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reverse_iterator"></a> hash_multiset::const_reverse_iterator (STL/CLR)

El tipo de un iterador inverso constante de la secuencia controlada...

### <a name="syntax"></a>Sintaxis

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto de tipo sin especificar `T4` que puede actuar como un iterador inverso constante de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Myhash_multiset::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="count"></a> hash_multiset::count (STL/CLR)

Busca el número de elementos que coinciden con una clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
size_type count(key_type key);
```

#### <a name="parameters"></a>Parámetros

*key*<br/>
Valor de clave que se va a buscar.

### <a name="remarks"></a>Comentarios

La función miembro devuelve el número de elementos de la secuencia controlada que tienen una ordenación equivalente con *clave*. Se usa para determinar el número de elementos actualmente en la secuencia controlada que coinciden con una clave especificada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_count.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));
    return (0);
    }
```

```Output
a b c
count(L'A') = 0
count(L'b') = 1
count(L'C') = 0
```

## <a name="difference_type"></a> hash_multiset::difference_type (STL/CLR)

Los tipos de una distancia con signo entre dos elementos.

### <a name="syntax"></a>Sintaxis

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Comentarios

El tipo describe un recuento de elemento posiblemente negativo.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_difference_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Myhash_multiset::difference_type diff = 0;
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Myhash_multiset::iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
begin()-end() = -3
```

## <a name="empty"></a> hash_multiset::empty (STL/CLR)

Comprueba si no hay ningún elemento presente.

### <a name="syntax"></a>Sintaxis

```cpp
bool empty();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve true para una secuencia controlada vacía. Equivale a [hash_multiset:: Size (STL/CLR)](../dotnet/hash-multiset-size-stl-clr.md)`() == 0`. Usa para comprobar si el objeto hash_multiset está vacío.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_empty.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());
    return (0);
    }
```

```Output
a b c
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="end"></a> hash_multiset::end (STL/CLR)

Designa el final de la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator end();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve un iterador bidireccional que apunta justo después del final de la secuencia controlada. Se usa para obtener un iterador que designa el final de la secuencia controlada; su estado se no cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_end.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    Myhash_multiset::iterator it = c1.end();
    --it;
    System::Console::WriteLine("*-- --end() = {0}", *--it);
    System::Console::WriteLine("*--end() = {0}", *++it);
    return (0);
    }
```

```Output
a b c
*-- --end() = b
*--end() = c
```

## <a name="equal_range"></a> hash_multiset::equal_range (STL/CLR)

Busca el intervalo que coincide con una clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>Parámetros

*key*<br/>
Valor de clave que se va a buscar.

### <a name="remarks"></a>Comentarios

La función miembro devuelve un par de iteradores `cliext::pair<iterator, iterator>(` [hash_multiset:: lower_bound (STL/CLR)](../dotnet/hash-multiset-lower-bound-stl-clr.md) `(key),` [hash_multiset:: upper_bound (STL/CLR)](../dotnet/hash-multiset-upper-bound-stl-clr.md)`(key))`. Se usa para determinar el intervalo de elementos actualmente en la secuencia controlada que coinciden con una clave especificada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_equal_range.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
typedef Myhash_multiset::pair_iter_iter Pairii;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display results of failed search
    Pairii pair1 = c1.equal_range(L'x');
    System::Console::WriteLine("equal_range(L'x') empty = {0}",
        pair1.first == pair1.second);

    // display results of successful search
    pair1 = c1.equal_range(L'b');
    for (; pair1.first != pair1.second; ++pair1.first)
        System::Console::Write("{0} ", *pair1.first);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
equal_range(L'x') empty = True
b
```

## <a name="erase"></a> hash_multiset::erase (STL/CLR)

Quita los elementos de las posiciones especificadas.

### <a name="syntax"></a>Sintaxis

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
bool erase(key_type key)
```

#### <a name="parameters"></a>Parámetros

*first*<br/>
Principio del intervalo que se va a borrar.

*key*<br/>
Valor de clave para borrar.

*last*<br/>
Fin del intervalo que se va a borrar.

*where*<br/>
Elemento que se va a borrar.

### <a name="remarks"></a>Comentarios

La primera función miembro quita el elemento de la secuencia controlada señalada por *donde*y devuelve un iterador que designa el primer elemento que permanece más allá del elemento quitado, o [hash_multiset:: end () STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md) `()` si no existe ese elemento. Usa para quitar un elemento único.

La segunda función miembro quita los elementos de la secuencia controlada en el intervalo [`first`, `last`) y devuelve un iterador que designa el primer elemento que permanece más allá de los elementos quitados, o `end()` si ningún elemento existe... Usa para quitar cero o más elementos contiguos.

La tercera función miembro quita cualquier elemento de la secuencia controlada cuyo criterio de ordenación es equivalente a *clave*y devuelve un recuento del número de elementos quitados. Usa para quitar y contar todos los elementos que coinciden con una clave especificada.

Eliminación de cada elemento tarda tiempo proporcional al logaritmo del número de elementos de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_erase.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase an element and reinspect
    System::Console::WriteLine("erase(begin()) = {0}",
        *c1.erase(c1.begin()));

    // add elements and display " b c d e"
    c1.insert(L'd');
    c1.insert(L'e');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase all but end
    Myhash_multiset::iterator it = c1.end();
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",
        *c1.erase(c1.begin(), --it));
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
erase(begin()) = b
b c d e
erase(begin(), end()-1) = e
size() = 1
```

## <a name="find"></a> hash_multiset::find (STL/CLR)

Busca un elemento que coincide con una clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Parámetros

*key*<br/>
Valor de clave que se va a buscar.

### <a name="remarks"></a>Comentarios

Si al menos un elemento de la secuencia controlada tiene una ordenación equivalente con *clave*, la función miembro devuelve un iterador que designa uno de esos elementos; de lo contrario, devuelve [hash_multiset:: end (STL/CLR) ](../dotnet/hash-multiset-end-stl-clr.md)`()`. Usa para buscar un elemento actualmente en la secuencia controlada que coincide con una clave especificada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_find.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("find {0} = {1}",
        L'A', c1.find(L'A') != c1.end());
    System::Console::WriteLine("find {0} = {1}",
        L'b', *c1.find(L'b'));
    System::Console::WriteLine("find {0} = {1}",
        L'C', c1.find(L'C') != c1.end());
    return (0);
    }
```

```Output
a b c
find A = False
find b = b
find C = False
```

## <a name="generic_container"></a> hash_multiset::generic_container (STL/CLR)

El tipo de la interfaz genérica para el contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Microsoft::VisualC::StlClr::
    IHash<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>Comentarios

El tipo describe la interfaz genérica para esta clase de contenedor de plantilla.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_generic_container.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.insert(L'e');
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a b c d
a b c d e
```

## <a name="generic_iterator"></a> hash_multiset::generic_iterator (STL/CLR)

El tipo de iterador para su uso con la interfaz genérica para el contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe un iterador genérico que puede usarse con la interfaz genérica para esta clase de contenedor de plantilla.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_generic_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_multiset::generic_iterator gcit = gc1->begin();
    Myhash_multiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="generic_reverse_iterator"></a> hash_multiset::generic_reverse_iterator (STL/CLR)

El tipo de un iterador inverso para su uso con la interfaz genérica para el contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value>
    generic_reverse_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe un iterador inverso genérico que puede usarse con la interfaz genérica para esta clase de contenedor de plantilla.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_multiset::generic_reverse_iterator gcit = gc1->rbegin();
    Myhash_multiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
c
```

## <a name="generic_value"></a> hash_multiset::generic_value (STL/CLR)

El tipo de un elemento para su uso con la interfaz genérica para el contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto de tipo `GValue` que describe el valor del elemento almacenados para su uso con la interfaz genérica para esta clase de contenedor de plantilla.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_generic_value.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_multiset::generic_iterator gcit = gc1->begin();
    Myhash_multiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="hash_delegate"></a> hash_multiset::hash_delegate (STL/CLR)

Busca un elemento que coincide con una clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
hasher^ hash_delegate();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve al delegado que se usa para convertir un valor de clave en un entero. Se usa para una clave de hash.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_hash_delegate.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::hasher^ myhash = c1.hash_delegate();

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 1616896120
hash(L'b') = 570892832
```

## <a name="hash_multiset"></a> hash_multiset::hash_multiset (STL/CLR)

Construye un objeto contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
hash_multiset();
explicit hash_multiset(key_compare^ pred);
hash_multiset(key_compare^ pred, hasher^ hashfn);
hash_multiset(hash_multiset<Key>% right);
hash_multiset(hash_multiset<Key>^ right);
template<typename InIter>
    hash_multiset(InIter first, InIter last);
template<typename InIter>
    hash_multiset(InIter first, InIter last,
        key_compare^ pred);
template<typename InIter>
    hash_multiset(InIter first, InIter last,
        key_compare^ pred, hasher^ hashfn);
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right);
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred, hasher^ hashfn);
```

#### <a name="parameters"></a>Parámetros

*first*<br/>
Principio del intervalo que se va a insertar.

*hashfn*<br/>
Función para las claves de asignación a los depósitos de hash.

*last*<br/>
Fin del intervalo que se va a insertar.

*pred*<br/>
Orden de predicado de la secuencia controlada.

*right*<br/>
Objeto o intervalo que se va a insertar.

### <a name="remarks"></a>Comentarios

El constructor:

`hash_multiset();`

Inicializa la secuencia controlada sin elementos, con el valor predeterminado ordenación predicado `key_compare()`y con la función hash predeterminada. Se usa para especificar una secuencia controlada inicial vacía, con el valor predeterminado ordenación en función de predicado y hash.

El constructor:

`explicit hash_multiset(key_compare^ pred);`

Inicializa la secuencia controlada con ningún elemento con el predicado de ordenación *pred*y con la función hash predeterminada. Se usa para especificar una secuencia controlada inicial vacía, con el predicado de ordenación especificado y la función hash predeterminada.

El constructor:

`hash_multiset(key_compare^ pred, hasher^ hashfn);`

Inicializa la secuencia controlada con ningún elemento con el predicado de ordenación *pred*y con la función hash *hashfn*. Se usa para especificar una secuencia controlada inicial vacía, con la función de predicado y hash de ordenación especificada.

El constructor:

`hash_multiset(hash_multiset<Key>% right);`

Inicializa la secuencia controlada por la secuencia [`right.begin()`, `right.end()`), con el predicado del orden de predeterminado y con la función hash predeterminada. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto hash_multiset *derecho*, con el predicado de ordenación predeterminada y la función hash.

El constructor:

`hash_multiset(hash_multiset<Key>^ right);`

Inicializa la secuencia controlada por la secuencia [`right->begin()`, `right->end()`), con el predicado del orden de predeterminado y con la función hash predeterminada. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto hash_multiset *derecho*, con el predicado de ordenación predeterminada y la función hash.

El constructor:

`template<typename InIter> hash_multiset(InIter first, InIter last);`

Inicializa la secuencia controlada por la secuencia [`first`, `last`), con el predicado del orden de predeterminado y con la función hash predeterminada. Usarlo para realizar una copia de otra secuencia de la secuencia controlada con el valor predeterminado ordenación en función de predicado y hash.

El constructor:

`template<typename InIter> hash_multiset(InIter first, InIter last, key_compare^ pred);`

Inicializa la secuencia controlada por la secuencia [`first`, `last`), con el predicado de ordenación *pred*y con la función hash predeterminada. Usa para realizar una copia de otra secuencia, con el predicado de ordenación especificado y la función hash predeterminada de la secuencia controlada.

El constructor:

`template<typename InIter> hash_multiset(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`

Inicializa la secuencia controlada por la secuencia [`first`, `last`), con el predicado de ordenación *pred*y con la función hash *hashfn*. Usa para realizar una copia de otra secuencia, con la función de predicado y hash de ordenación especificada de la secuencia controlada.

El constructor:

`hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right);`

Inicializa la secuencia controlada con la secuencia designada por el enumerador *derecho*, con el predicado del orden de predeterminado y con la función hash predeterminada. Usa para realizar una copia de otra secuencia que se describe mediante un enumerador, con el valor predeterminado ordenación en función de predicado y hash de la secuencia controlada.

El constructor:

`hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

Inicializa la secuencia controlada con la secuencia designada por el enumerador *derecho*, con el predicado de ordenación *pred*y con la función hash predeterminada. Usa para realizar una copia de otra secuencia descrita por un enumerador con la ordenación predeterminada y el predicado hash función especificada de la secuencia controlada.

El constructor:

`hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`

Inicializa la secuencia controlada con la secuencia designada por el enumerador *derecho*, con el predicado de ordenación *pred*y con la función hash *hashfn*. Usa para realizar una copia de otra secuencia descrita por un enumerador con la función de predicado y hash de ordenación especificado de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_construct.cpp
// compile with: /clr
#include <cliext/hash_set>

int myfun(wchar_t key)
    { // hash a key
    return (key ^ 0xdeadbeef);
    }

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
// construct an empty container
    Myhash_multiset c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule
    Myhash_multiset c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule and hash function
    Myhash_multiset c2h(cliext::greater_equal<wchar_t>(),
        gcnew Myhash_multiset::hasher(&myfun));
    System::Console::WriteLine("size() = {0}", c2h.size());

    c2h.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct with an iterator range
    Myhash_multiset c3(c1.begin(), c1.end());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Myhash_multiset c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule and hash function
    Myhash_multiset c4h(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>(),
        gcnew Myhash_multiset::hasher(&myfun));
    for each (wchar_t elem in c4h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct with an enumeration
    Myhash_multiset c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Myhash_multiset c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c6)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule and hash function
    Myhash_multiset c6h(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>(),
                gcnew Myhash_multiset::hasher(&myfun));
    for each (wchar_t elem in c6h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct from a generic container
    Myhash_multiset c7(c4);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Myhash_multiset c8(%c3);
    for each (wchar_t elem in c8)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
a b c
size() = 0
a b c
size() = 0
c b a

a b c
a b c
c b a

a b c
a b c
c b a

a b c
a b c
```

## <a name="hasher"></a> hash_multiset::hasher (STL/CLR)

El delegado de hash para una clave.

### <a name="syntax"></a>Sintaxis

```cpp
Microsoft::VisualC::StlClr::UnaryDelegate<GKey, int>
    hasher;
```

### <a name="remarks"></a>Comentarios

El tipo describe a un delegado que convierte un valor de clave en un entero.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_hasher.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::hasher^ myhash = c1.hash_delegate();

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 1616896120
hash(L'b') = 570892832
```

## <a name="insert"></a> hash_multiset::insert (STL/CLR)

Agrega elementos.

### <a name="syntax"></a>Sintaxis

```cpp
iterator insert(value_type val);
iterator insert(iterator where, value_type val);
template<typename InIter>
    void insert(InIter first, InIter last);
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);
```

#### <a name="parameters"></a>Parámetros

*first*<br/>
Principio del intervalo que se va a insertar.

*last*<br/>
Fin del intervalo que se va a insertar.

*right*<br/>
Enumeración que se va a insertar.

*val*<br/>
Valor de clave se va a insertar.

*where*<br/>
Lugar en el contenedor que se va a insertar (sugerencia solo).

### <a name="remarks"></a>Comentarios

Cada una de las funciones miembro inserta una secuencia especificada por los operandos restantes.

La primera función miembro inserta un elemento con el valor *val*y devuelve un iterador que designa el elemento recién insertado. Usarlo para insertar un elemento único.

La segunda función miembro inserta un elemento con el valor *val*con *donde* como una sugerencia (para mejorar el rendimiento) y devuelve un iterador que designa el elemento recién insertado. Usarlo para insertar un elemento único que podría ser adyacente a un elemento que conoce.

La tercera función miembro inserta la secuencia [`first`, `last`). Usa para insertar cero o más de los elementos copiados desde la otra secuencia.

La cuarta función miembro inserta la secuencia designada por el *derecho*. Usa para insertar una secuencia descrita por un enumerador.

Inserción de cada elemento tarda tiempo proporcional al logaritmo del número de elementos de la secuencia controlada. Inserción puede producirse en tiempo constante amortizado, sin embargo, dada una sugerencia que designa un elemento adyacente al punto de inserción.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_insert.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value, unique and duplicate
    System::Console::WriteLine("insert(L'x') = {0}",
        *c1.insert(L'x'));

    System::Console::WriteLine("insert(L'b') = {0}",
        *c1.insert(L'b'));

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value with hint
    System::Console::WriteLine("insert(begin(), L'y') = {0}",
        *c1.insert(c1.begin(), L'y'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an iterator range
    Myhash_multiset c2;
    Myhash_multiset::iterator it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an enumeration
    Myhash_multiset c3;
    c3.insert(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
insert(L'x') = x
insert(L'b') = b
a b b c x
insert(begin(), L'y') = y
a b b c x y
a b b c x
a b b c x y
```

## <a name="iterator"></a> hash_multiset::iterator (STL/CLR)

El tipo de un iterador para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto de tipo sin especificar `T1` que puede actuar como un iterador bidireccional para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Myhash_multiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="key_comp"></a> hash_multiset::key_comp (STL/CLR)

Copia al delegado de ordenación de dos claves.

### <a name="syntax"></a>Sintaxis

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve al delegado de ordenación utilizado para ordenar la secuencia controlada. Usa para comparar dos claves.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_key_comp.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_multiset c2 = cliext::greater<wchar_t>();
    kcomp = c2.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="key_compare"></a> hash_multiset::key_compare (STL/CLR)

Delegado de ordenación para dos claves.

### <a name="syntax"></a>Sintaxis

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>
    key_compare;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo para el delegado que determina el orden de sus argumentos de la claves.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_key_compare.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_multiset c2 = cliext::greater<wchar_t>();
    kcomp = c2.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="key_type"></a> hash_multiset::key_type (STL/CLR)

El tipo de una clave de ordenación.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla *clave*.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_key_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using key_type
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Myhash_multiset::key_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="load_factor"></a> hash_multiset::load_factor (STL/CLR)

Cuenta los elementos promedio por depósito.

### <a name="syntax"></a>Sintaxis

```cpp
float load_factor();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve `(float)` [hash_multiset:: Size (STL/CLR)](../dotnet/hash-multiset-size-stl-clr.md) `() /` [hash_multiset::bucket_count (STL/CLR)](../dotnet/hash-multiset-bucket-count-stl-clr.md)`()`. Se usa para determinar el tamaño de depósito promedio.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_load_factor.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="lower_bound"></a> hash_multiset::lower_bound (STL/CLR)

Busca el principio del intervalo que coincide con una clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Parámetros

*key*<br/>
Valor de clave que se va a buscar.

### <a name="remarks"></a>Comentarios

La función miembro determina el primer elemento `X` en la secuencia controlada que aplica un algoritmo hash al mismo depósito que *clave* y tiene una ordenación equivalente a *clave*. Si no existe ese elemento, devuelve [hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`; en caso contrario, devuelve un iterador que designa `X`. Usa para buscar el principio de una secuencia de elementos actualmente en la secuencia controlada que coinciden con una clave especificada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_lower_bound.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",
        c1.lower_bound(L'x') == c1.end());

    System::Console::WriteLine("*lower_bound(L'a') = {0}",
        *c1.lower_bound(L'a'));
    System::Console::WriteLine("*lower_bound(L'b') = {0}",
        *c1.lower_bound(L'b'));
    return (0);
    }
```

```Output
a b c
lower_bound(L'x')==end() = True
*lower_bound(L'a') = a
*lower_bound(L'b') = b
```

## <a name="make_value"></a> hash_multiset::make_value (STL/CLR)

Construye un objeto de valor.

### <a name="syntax"></a>Sintaxis

```cpp
static value_type make_value(key_type key);
```

#### <a name="parameters"></a>Parámetros

*key*<br/>
Valor de clave para usar.

### <a name="remarks"></a>Comentarios

La función miembro devuelve un `value_type` objeto cuya clave es *clave*. Usarlo para crear un objeto adecuado para su uso con otras funciones de miembro.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_make_value.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(Myhash_multiset::make_value(L'a'));
    c1.insert(Myhash_multiset::make_value(L'b'));
    c1.insert(Myhash_multiset::make_value(L'c'));

    // display contents " a b c"
    for each (Myhash_multiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="max_load_factor"></a> hash_multiset::max_load_factor (STL/CLR)

Obtiene o establece los elementos máximos por depósito.

### <a name="syntax"></a>Sintaxis

```cpp
float max_load_factor();
void max_load_factor(float new_factor);
```

#### <a name="parameters"></a>Parámetros

*new_factor*<br/>
Nuevo máximo cargar factor que hay que almacenar.

### <a name="remarks"></a>Comentarios

La primera función miembro devuelve el factor de carga máxima almacenado actual. Se usa para determinar el tamaño máximo de depósito promedio.

La segunda función miembro reemplaza el factor de carga máxima de la tienda con *new_factor*. Ningún recombinando automática se produce hasta que una inserción posteriores.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_max_load_factor.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="op"></a> hash_multiset::operator= (STL/CLR)

Reemplaza la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
hash_multiset<Key>% operator=(hash_multiset<Key>% right);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Contenedor que se va a copiar.

### <a name="remarks"></a>Comentarios

Las copias de operador miembro *derecho* al objeto, a continuación, devuelve `*this`. Se usa para reemplazar la secuencia controlada por una copia de la secuencia controlada en *derecho*.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_operator_as.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (Myhash_multiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Myhash_multiset c2;
    c2 = c1;
// display contents " a b c"
    for each (Myhash_multiset::value_type elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="rbegin"></a> hash_multiset::rbegin (STL/CLR)

Designa el principio de la secuencia controlada inversa.

### <a name="syntax"></a>Sintaxis

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve un iterador inverso que designa el último elemento de la secuencia controlada o inmediatamente después del principio de una secuencia vacía. Por tanto, designa el `beginning` de la secuencia inversa. Se usa para obtener un iterador que designa el `current` principio de la secuencia controlada mostrada en orden inverso, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_rbegin.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Myhash_multiset::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = {0}", *rit);
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);
    return (0);
    }
```

```Output
a b c
*rbegin() = c
*++rbegin() = b
```

## <a name="reference"></a> hash_multiset::reference (STL/CLR)

El tipo de una referencia a un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Comentarios

El tipo describe una referencia a un elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_reference.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Myhash_multiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Myhash_multiset::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="rehash"></a> hash_multiset::rehash (STL/CLR)

Recompila la tabla hash.

### <a name="syntax"></a>Sintaxis

```cpp
void rehash();
```

### <a name="remarks"></a>Comentarios

La función miembro se vuelve a generar la tabla hash, lo que garantiza que [hash_multiset::load_factor (STL/CLR)](../dotnet/hash-multiset-load-factor-stl-clr.md) `() <=` [hash_multiset::max_load_factor (STL/CLR)](../dotnet/hash-multiset-max-load-factor-stl-clr.md). En caso contrario, la tabla hash aumenta de tamaño según sea necesario después de una inserción. (Nunca disminuye de tamaño automáticamente.) Usa para ajustar el tamaño de la tabla hash.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_rehash.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="rend"></a> hash_multiset::rend (STL/CLR)

Designa el final de la secuencia controlada inversa.

### <a name="syntax"></a>Sintaxis

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve un iterador inverso que apunta inmediatamente después del principio de la secuencia controlada. Por tanto, designa el `end` de la secuencia inversa. Se usa para obtener un iterador que designa el `current` final de la secuencia controlada mostrada en orden inverso, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_rend.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Myhash_multiset::reverse_iterator rit = c1.rend();
    --rit;
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);
    System::Console::WriteLine("*--rend() = {0}", *++rit);
    return (0);
    }
```

```Output
a b c
*-- --rend() = b
*--rend() = a
```

## <a name="reverse_iterator"></a> hash_multiset::reverse_iterator (STL/CLR)

El tipo de un iterador invertido para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe un objeto de tipo sin especificar `T3` que puede actuar como un iterador inverso de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Myhash_multiset::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="size"></a> hash_multiset::size (STL/CLR)

Cuenta el número de elementos.

### <a name="syntax"></a>Sintaxis

```cpp
size_type size();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve la longitud de la secuencia controlada. Se usa para determinar el número de elementos actualmente en la secuencia controlada. Si lo único que interesa es si la secuencia tiene un tamaño distinto de cero, vea [hash_multiset:: Empty (STL/CLR)](../dotnet/hash-multiset-empty-stl-clr.md)`()`.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_size.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.insert(L'a');
    c1.insert(L'b');
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 3 starting with 3
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="size_type"></a> hash_multiset::size_type (STL/CLR)

El tipo de una distancia con signo entre dos elementos.

### <a name="syntax"></a>Sintaxis

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Comentarios

El tipo describe un recuento de elemento no negativo.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_size_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Myhash_multiset::size_type diff = 0;
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="swap"></a> hash_multiset::swap (STL/CLR)

Intercambia el contenido de dos contenedores.

### <a name="syntax"></a>Sintaxis

```cpp
void swap(hash_multiset<Key>% right);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Contenedor con el que se va a intercambiar el contenido.

### <a name="remarks"></a>Comentarios

La función miembro intercambia las secuencias controladas entre `this` y *derecho*. Lo hace en tiempo constante y no inicia ninguna excepción. Úselo como una forma rápida para intercambiar el contenido de dos contenedores.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_swap.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Myhash_multiset c2;
    c2.insert(L'd');
    c2.insert(L'e');
    c2.insert(L'f');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
d e f
d e f
a b c
```

## <a name="to_array"></a> hash_multiset::to_array (STL/CLR)

Copia la secuencia controlada a una nueva matriz.

### <a name="syntax"></a>Sintaxis

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve una matriz que contiene la secuencia controlada. Se usa para obtener una copia de la secuencia controlada en forma de matriz.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_to_array.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.insert(L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c d
a b c
```

## <a name="upper_bound"></a> hash_multiset::upper_bound (STL/CLR)

Busca el final del intervalo que coincide con una clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Parámetros

*key*<br/>
Valor de clave que se va a buscar.

### <a name="remarks"></a>Comentarios

La función miembro determina el último elemento `X` en la secuencia controlada que aplica un algoritmo hash al mismo depósito que *clave* y tiene una ordenación equivalente a *clave*. Si no existe ese elemento, o si `X` es el último elemento de la secuencia controlada, se devuelve [hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`; en caso contrario, devuelve un iterador que designa el primer elemento más allá `X`. Utiliza para localizar el final de una secuencia de elementos actualmente en la secuencia controlada que coinciden con una clave especificada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_upper_bound.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",
        c1.upper_bound(L'x') == c1.end());

    System::Console::WriteLine("*upper_bound(L'a') = {0}",
        *c1.upper_bound(L'a'));
    System::Console::WriteLine("*upper_bound(L'b') = {0}",
        *c1.upper_bound(L'b'));
    return (0);
    }
```

```Output
a b c
upper_bound(L'x')==end() = True
*upper_bound(L'a') = b
*upper_bound(L'b') = c
```

## <a name="value_comp"></a> hash_multiset::value_comp (STL/CLR)

Copia al delegado de ordenación de dos valores de elemento.

### <a name="syntax"></a>Sintaxis

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve al delegado de ordenación utilizado para ordenar la secuencia controlada. Usa para comparar dos valores de elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_value_comp.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="value_compare"></a> hash_multiset::value_compare (STL/CLR)

Delegado de ordenación para dos valores de elemento.

### <a name="syntax"></a>Sintaxis

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>
    value_compare;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo para el delegado que determina el orden de sus argumentos de valor.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_value_compare.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="value_type"></a> hash_multiset::value_type (STL/CLR)

El tipo de un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de `generic_value`.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_multiset_value_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using value_type
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Myhash_multiset::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```