---
title: hash_map (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::hash_map
- cliext::hash_map::begin
- cliext::hash_map::bucket_count
- cliext::hash_map::clear
- cliext::hash_map::const_iterator
- cliext::hash_map::const_reference
- cliext::hash_map::const_reverse_iterator
- cliext::hash_map::count
- cliext::hash_map::difference_type
- cliext::hash_map::empty
- cliext::hash_map::end
- cliext::hash_map::equal_range
- cliext::hash_map::erase
- cliext::hash_map::find
- cliext::hash_map::generic_container
- cliext::hash_map::generic_iterator
- cliext::hash_map::generic_reverse_iterator
- cliext::hash_map::generic_value
- cliext::hash_map::hash_delegate
- cliext::hash_map::hash_map
- cliext::hash_map::hasher
- cliext::hash_map::insert
- cliext::hash_map::iterator
- cliext::hash_map::key_comp
- cliext::hash_map::key_compare
- cliext::hash_map::key_type
- cliext::hash_map::load_factor
- cliext::hash_map::lower_bound
- cliext::hash_map::make_value
- cliext::hash_map::mapped_type
- cliext::hash_map::max_load_factor
- cliext::hash_map::operator=
- cliext::hash_map::operator
- cliext::hash_map::rbegin
- cliext::hash_map::reference
- cliext::hash_map::rehash
- cliext::hash_map::rend
- cliext::hash_map::reverse_iterator
- cliext::hash_map::size
- cliext::hash_map::size_type
- cliext::hash_map::swap
- cliext::hash_map::to_array
- cliext::hash_map::upper_bound
- cliext::hash_map::value_comp
- cliext::hash_map::value_compare
- cliext::hash_map::value_type
helpviewer_keywords:
- <cliext/hash_map> header [STL/CLR]
- <hash_map> header [STL/CLR]
- hash_map class [STL/CLR]
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
- hash_map member [STL/CLR]
- hasher member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- load_factor member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- mapped_type member [STL/CLR]
- max_load_factor member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
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
ms.assetid: c3cfc69b-04c6-42ae-a30e-0eda953fe883
ms.openlocfilehash: d87444fe5a62bac30d62cd7e44dfba7934083ef4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208746"
---
# <a name="hash_map-stlclr"></a>hash_map (STL/CLR)

La clase de plantilla describe un objeto que controla una secuencia de elementos de longitud variable que tiene acceso bidireccional. Use el `hash_map` de contenedor para administrar una secuencia de elementos como una tabla hash, cada entrada de tabla que almacena una lista de nodos vinculada bidireccional y cada nodo que almacena un elemento. Un elemento se compone de una clave, para ordenar la secuencia y un valor asignado, que va junto a la conducción.

En la descripción siguiente, `GValue` es igual que:

`Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`

donde:

`GKey` es igual que `Key` a menos que la segunda sea un tipo de referencia, en cuyo caso se `Key^`

`GMapped` es igual que `Mapped` a menos que la segunda sea un tipo de referencia, en cuyo caso se `Mapped^`

## <a name="syntax"></a>Sintaxis

```cpp
template<typename Key,
    typename Mapped>
    ref class hash_map
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        System::Collections::Generic::IDictionary<Gkey, GMapped>,
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>Parámetros

*Clave*<br/>
Tipo del componente clave de un elemento en la secuencia controlada.

*Les*<br/>
Tipo del componente adicional de un elemento en la secuencia controlada.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<cliext (/hash_map >

**Espacio de nombres:** cliext (

## <a name="declarations"></a>Declaraciones

|Definición de tipo|Descripción|
|---------------------|-----------------|
|[hash_map::const_iterator (STL/CLR)](#const_iterator)|El tipo de un iterador constante para la secuencia controlada.|
|[hash_map::const_reference (STL/CLR)](#const_reference)|El tipo de una referencia constante a un elemento.|
|[hash_map::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|El tipo de un iterador invertido constante para la secuencia controlada.|
|[hash_map::difference_type (STL/CLR)](#difference_type)|El tipo de una distancia (posiblemente firmada) entre dos elementos.|
|[hash_map::generic_container (STL/CLR)](#generic_container)|Tipo de la interfaz genérica para el contenedor.|
|[hash_map::generic_iterator (STL/CLR)](#generic_iterator)|El tipo de un iterador para la interfaz genérica del contenedor.|
|[hash_map::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|El tipo de un iterador inverso para la interfaz genérica del contenedor.|
|[hash_map::generic_value (STL/CLR)](#generic_value)|Tipo de un elemento de la interfaz genérica para el contenedor.|
|[hash_map::hasher (STL/CLR)](#hasher)|Delegado de hash para una clave.|
|[hash_map::iterator (STL/CLR)](#iterator)|El tipo de un iterador para la secuencia controlada.|
|[hash_map::key_compare (STL/CLR)](#key_compare)|Delegado de ordenación para dos claves.|
|[hash_map::key_type (STL/CLR)](#key_type)|El tipo de una clave de ordenación.|
|[hash_map::mapped_type (STL/CLR)](#mapped_type)|Tipo del valor asignado asociado a cada clave.|
|[hash_map::reference (STL/CLR)](#reference)|El tipo de una referencia a un elemento.|
|[hash_map::reverse_iterator (STL/CLR)](#reverse_iterator)|El tipo de un iterador invertido para la secuencia controlada.|
|[hash_map::size_type (STL/CLR)](#size_type)|El tipo de una distancia (no negativa) entre dos elementos.|
|[hash_map::value_compare (STL/CLR)](#value_compare)|Delegado de ordenación para dos valores de elemento.|
|[hash_map::value_type (STL/CLR)](#value_type)|El tipo de un elemento.|

|Función miembro|Descripción|
|---------------------|-----------------|
|[hash_map::begin (STL/CLR)](#begin)|Designa el principio de la secuencia controlada.|
|[hash_map::bucket_count (STL/CLR)](#bucket_count)|Cuenta el número de depósitos.|
|[hash_map::clear (STL/CLR)](#clear)|Quita todos los elementos.|
|[hash_map::count (STL/CLR)](#count)|Cuenta los elementos que coinciden con una clave especificada.|
|[hash_map::empty (STL/CLR)](#empty)|Comprueba si no hay ningún elemento presente.|
|[hash_map::end (STL/CLR)](#end)|Designa el final de la secuencia controlada.|
|[hash_map::equal_range (STL/CLR)](#equal_range)|Busca el intervalo que coincide con una clave especificada.|
|[hash_map::erase (STL/CLR)](#erase)|Quita los elementos de las posiciones especificadas.|
|[hash_map::find (STL/CLR)](#find)|Busca un elemento que coincide con una clave especificada.|
|[hash_map::hash_delegate (STL/CLR)](#hash_delegate)|Copia el delegado hash para una clave.|
|[hash_map::hash_map (STL/CLR)](#hash_map)|Construye un objeto contenedor.|
|[hash_map::insert (STL/CLR)](#insert)|Agrega elementos.|
|[hash_map::key_comp (STL/CLR)](#key_comp)|Copia el delegado de ordenación de dos claves.|
|[hash_map::load_factor (STL/CLR)](#load_factor)|Cuenta los elementos promedio por depósito.|
|[hash_map::lower_bound (STL/CLR)](#lower_bound)|Busca el principio del intervalo que coincide con una clave especificada.|
|[hash_map::make_value (STL/CLR)](#make_value)|Construye un objeto de valor.|
|[hash_map::max_load_factor (STL/CLR)](#max_load_factor)|Obtiene o establece los elementos máximos por depósito.|
|[hash_map::rbegin (STL/CLR)](#rbegin)|Designa el principio de la secuencia controlada inversa.|
|[hash_map::rehash (STL/CLR)](#rehash)|Recompila la tabla hash.|
|[hash_map::rend (STL/CLR)](#rend)|Designa el final de la secuencia controlada inversa.|
|[hash_map::size (STL/CLR)](#size)|Cuenta el número de elementos.|
|[hash_map::swap (STL/CLR)](#swap)|Intercambia el contenido de dos contenedores.|
|[hash_map::to_array (STL/CLR)](#to_array)|Copia la secuencia controlada en una nueva matriz.|
|[hash_map::upper_bound (STL/CLR)](#upper_bound)|Busca el final del intervalo que coincide con una clave especificada.|
|[hash_map::value_comp (STL/CLR)](#value_comp)|Copia el delegado de ordenación para dos valores de elemento.|

|Operator|Descripción|
|--------------|-----------------|
|[hash_map::operator= (STL/CLR)](#op_as)|Reemplaza la secuencia controlada.|
|[hash_map::operator(STL/CLR)](#op)|Asigna una clave a su valor asignado asociado.|

## <a name="interfaces"></a>Interfaces

|Interfaz|Descripción|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplicar un objeto.|
|<xref:System.Collections.IEnumerable>|Secuencia a través de elementos.|
|<xref:System.Collections.ICollection>|Mantiene el grupo de elementos.|
|<xref:System.Collections.Generic.IEnumerable%601>|Secuencia a través de elementos con tipo.|
|<xref:System.Collections.Generic.ICollection%601>|Mantiene el grupo de elementos con tipo.|
|<xref:System.Collections.Generic.IDictionary%602>|Mantener el grupo de {Key, Value} pares.|
|IHash < clave, valor >|Mantenga el contenedor genérico.|

## <a name="remarks"></a>Observaciones

El objeto asigna y libera almacenamiento para la secuencia que controla como nodos individuales en una lista vinculada bidireccional. Para agilizar el acceso, el objeto también mantiene una matriz de longitud variable de punteros en la lista (la tabla hash), administrando eficazmente toda la lista como una secuencia de sublistas o depósitos. Inserta elementos en un depósito que mantiene ordenado modificando los vínculos entre los nodos, nunca copiando el contenido de un nodo en otro. Esto significa que puede insertar y quitar elementos libremente sin molestar a los elementos restantes.

El objeto ordena cada depósito que controla llamando a un objeto delegado almacenado de tipo [hash_set:: key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md). Puede especificar el objeto delegado almacenado al construir el hash_set; Si no especifica ningún objeto delegado, el valor predeterminado es el `operator<=(key_type, key_type)`de comparación.

Tiene acceso al objeto delegado almacenado llamando a la función miembro [hash_set:: key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)`()`. Dicho objeto delegado debe definir una ordenación equivalente entre las claves de tipo [hash_set:: key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md). Esto significa que, para dos claves `X` y `Y`:

`key_comp()(X, Y)` devuelve el mismo resultado booleano en cada llamada.

Si `key_comp()(X, Y) && key_comp()(Y, X)` es true, se dice que `X` y `Y` tienen una ordenación equivalente.

Cualquier regla de ordenación que se comporta como `operator<=(key_type, key_type)`, `operator>=(key_type, key_type)` o `operator==(key_type, key_type)` define el orden eqivalent.

Tenga en cuenta que el contenedor solo garantiza que los elementos cuyas claves tienen una ordenación equivalente (y el hash al mismo valor entero) son adyacentes dentro de un depósito. A diferencia de la clase de plantilla [hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md), un objeto de clase de plantilla `hash_map` garantiza que las claves para todos los elementos son únicas. (Dos claves no tienen una ordenación equivalente).

El objeto determina qué depósito debe contener una clave de ordenación determinada llamando a un objeto delegado almacenado de tipo [hash_set:: Hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md). Puede tener acceso a este objeto almacenado llamando a la función miembro [hash_set:: hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md)`()` para obtener un valor entero que dependa del valor de clave. Puede especificar el objeto delegado almacenado al construir el hash_set; Si no especifica ningún objeto delegado, el valor predeterminado es la función `System::Object::hash_value(key_type)`. Esto significa que, para cualquier clave `X` y `Y`:

`hash_delegate()(X)` devuelve el mismo resultado entero en cada llamada.

Si `X` y `Y` tienen una ordenación equivalente, `hash_delegate()(X)` debe devolver el mismo resultado entero que `hash_delegate()(Y)`.

Cada elemento contiene una clave independiente y un valor asignado. La secuencia se representa de forma que permite la búsqueda, inserción y eliminación de un elemento arbitrario con varias operaciones que son independientes del número de elementos de la secuencia (tiempo constante), al menos en el mejor de los casos. Además, la inserción de un elemento no invalida ningún iterador y al quitar un elemento solo se invalidan los iteradores que apuntan al elemento quitado.

Sin embargo, si los valores con hash no se distribuyen uniformemente, se puede degenerar una tabla hash. En el extremo--para una función hash que siempre devuelve el mismo valor, la búsqueda, la inserción y la eliminación son proporcionales al número de elementos de la secuencia (tiempo lineal). El contenedor está orientado a elegir una función hash razonable, el tamaño medio del depósito y el tamaño de la tabla hash (número total de cubos), pero puede invalidar cualquiera de estas opciones o todas ellas. Consulte, por ejemplo, las funciones [hash_set:: max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md) y [hash_set:: rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md).

Un hash_map admite iteradores bidireccionales, lo que significa que puede ir a los elementos adyacentes dado un iterador que designa un elemento en la secuencia controlada. Un nodo principal especial corresponde al iterador devuelto por [hash_map:: end (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)`()`. Puede reducir este iterador para llegar al último elemento de la secuencia controlada, si está presente. Puede incrementar un iterador hash_map para llegar al nodo principal y, a continuación, se comparará como igual a `end()`. Pero no se puede desreferenciar el iterador devuelto por `end()`.

Tenga en cuenta que no puede hacer referencia a un elemento de hash_map directamente a su posición numérica, que requiere un iterador de acceso aleatorio.

Un iterador hash_map almacena un identificador para su nodo de hash_map asociado, que a su vez almacena un identificador en su contenedor asociado. Solo se pueden usar iteradores con sus objetos de contenedor asociados. Un iterador hash_map sigue siendo válido, siempre y cuando su nodo de hash_map asociado esté asociado a algunos hash_map. Además, un iterador válido es dereferenceable--se puede usar para obtener acceso al valor del elemento que designa, y siempre que no sea igual que `end()`.

Al borrar o quitar un elemento, se llama al destructor para su valor almacenado. Al destruir el contenedor, se borran todos los elementos. Por lo tanto, un contenedor cuyo tipo de elemento es una clase Ref garantiza que ningún elemento durar más el contenedor. Sin embargo, tenga en cuenta que un contenedor de controladores *no destruye sus* elementos.

## <a name="members"></a>Members

## <a name="hash_mapbegin-stlclr"></a><a name="begin"></a>hash_map:: Begin (STL/CLR)

Designa el principio de la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator begin();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador bidireccional que designa el primer elemento de la secuencia controlada o más allá del final de una secuencia vacía. Se usa para obtener un iterador que designe el principio de la secuencia controlada, indicado por `current`, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_begin.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items
    Myhash_map::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = [{0} {1}]",
        it->first, it->second);
    ++it;
    System::Console::WriteLine("*++begin() = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*begin() = [a 1]
*++begin() = [b 2]
```

## <a name="hash_mapbucket_count-stlclr"></a><a name="bucket_count"></a>hash_map:: bucket_count (STL/CLR)

Cuenta el número de depósitos.

### <a name="syntax"></a>Sintaxis

```cpp
int bucket_count();
```

### <a name="remarks"></a>Observaciones

Las funciones miembro devuelven el número actual de depósitos. Se utiliza para determinar el tamaño de la tabla hash.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_bucket_count.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1 = gcnew Myhash_map;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
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
[a 1] [b 2] [c 3]
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

## <a name="hash_mapclear-stlclr"></a><a name="clear"></a>hash_map:: CLEAR (STL/CLR)

Quita todos los elementos.

### <a name="syntax"></a>Sintaxis

```cpp
void clear();
```

### <a name="remarks"></a>Observaciones

La función miembro llama eficazmente a [hash_map:: Erase (STL/CLR)](../dotnet/hash-map-erase-stl-clr.md)`(` [hash_map:: Begin (STL/clr)](../dotnet/hash-map-begin-stl-clr.md)`(),` [HASH_MAP:: end (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)`())`. Se utiliza para asegurarse de que la secuencia controlada está vacía.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_clear.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));

    // display contents " [a 1] [b 2]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
size() = 0
[a 1] [b 2]
size() = 0
```

## <a name="hash_mapconst_iterator-stlclr"></a><a name="const_iterator"></a>hash_map:: const_iterator (STL/CLR)

El tipo de un iterador constante para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de tipo sin especificar `T2` que puede actuar como iterador bidireccional constante para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_const_iterator.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Myhash_map::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("[{0} {1}] ", cit->first, cit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="hash_mapconst_reference-stlclr"></a><a name="const_reference"></a>hash_map:: const_reference (STL/CLR)

El tipo de una referencia constante a un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Observaciones

El tipo describe una referencia constante a un elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_const_reference.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Myhash_map::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Myhash_map::const_reference cref = *cit;
        System::Console::Write("[{0} {1}] ", cref->first, cref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="hash_mapconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>hash_map:: const_reverse_iterator (STL/CLR)

Tipo de un iterador inverso constante para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de tipo sin especificar `T4` que puede actuar como un iterador inverso constante para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Myhash_map::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("[{0} {1}] ", crit->first, crit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="hash_mapcount-stlclr"></a><a name="count"></a>hash_map:: Count (STL/CLR)

Busca el número de elementos que coinciden con una clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
size_type count(key_type key);
```

#### <a name="parameters"></a>Parámetros

*key*<br/>
Valor de clave que se va a buscar.

### <a name="remarks"></a>Observaciones

La función miembro devuelve el número de elementos de la secuencia controlada que tienen una ordenación equivalente con la *clave*. Se usa para determinar el número de elementos que están actualmente en la secuencia controlada que coinciden con una clave especificada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_count.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
count(L'A') = 0
count(L'b') = 1
count(L'C') = 0
```

## <a name="hash_mapdifference_type-stlclr"></a><a name="difference_type"></a>hash_map::d ifference_type (STL/CLR)

Tipos de una distancia con signo entre dos elementos.

### <a name="syntax"></a>Sintaxis

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Observaciones

El tipo describe un recuento de elementos posiblemente negativos.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_difference_type.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Myhash_map::difference_type diff = 0;
    for (Myhash_map::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Myhash_map::iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
end()-begin() = 3
begin()-end() = -3
```

## <a name="hash_mapempty-stlclr"></a><a name="empty"></a>hash_map:: Empty (STL/CLR)

Comprueba si no hay ningún elemento presente.

### <a name="syntax"></a>Sintaxis

```cpp
bool empty();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve true para una secuencia controlada vacía. Es equivalente a [hash_map:: Size (STL/CLR)](../dotnet/hash-map-size-stl-clr.md)`() == 0`. Se utiliza para comprobar si la hash_map está vacía.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_empty.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
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
[a 1] [b 2] [c 3]
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="hash_mapend-stlclr"></a><a name="end"></a>hash_map:: end (STL/CLR)

Designa el final de la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator end();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador bidireccional que apunta justo después del final de la secuencia controlada. Se usa para obtener un iterador que designe el final de la secuencia controlada. su estado no cambia si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_end.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect last two items
    Myhash_map::iterator it = c1.end();
    --it;
    --it;
    System::Console::WriteLine("*-- --end() = [{0} {1}]",
        it->first, it->second);
    ++it;
    System::Console::WriteLine("*--end() = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*-- --end() = [b 2]
*--end() = [c 3]
```

## <a name="hash_mapequal_range-stlclr"></a><a name="equal_range"></a>hash_map:: equal_range (STL/CLR)

Busca el intervalo que coincide con una clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>Parámetros

*key*<br/>
Valor de clave que se va a buscar.

### <a name="remarks"></a>Observaciones

La función miembro devuelve un par de iteradores `cliext::pair<iterator, iterator>(lower_bound(key), upper_bound(key))`. Se usa para determinar el intervalo de elementos que se encuentran actualmente en la secuencia controlada que coinciden con una clave especificada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_equal_range.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
typedef Myhash_map::pair_iter_iter Pairii;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // display results of failed search
    Pairii pair1 = c1.equal_range(L'x');
    System::Console::WriteLine("equal_range(L'x') empty = {0}",
        pair1.first == pair1.second);

    // display results of successful search
    pair1 = c1.equal_range(L'b');
    for (; pair1.first != pair1.second; ++pair1.first)
        System::Console::Write("[{0} {1}] ",
            pair1.first->first, pair1.first->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
equal_range(L'x') empty = True
[b 2]
```

## <a name="hash_maperase-stlclr"></a><a name="erase"></a>hash_map:: Erase (STL/CLR)

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
Valor de clave que se va a borrar.

*last*<br/>
Final del intervalo que se va a borrar.

*where*<br/>
Elemento que se va a borrar.

### <a name="remarks"></a>Observaciones

La primera función miembro quita el elemento de la secuencia controlada a la que apunta Where, y devuelve un iterador que designa el primer elemento que permanece más allá del elemento *que*se ha quitado o [hash_map:: end (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)`()` si no existe ese elemento. Se utiliza para quitar un solo elemento.

La segunda función miembro quita los elementos de la secuencia controlada en el intervalo [`first`, `last`) y devuelve un iterador que designa el primer elemento que permanece más allá de los elementos quitados, o `end()` si no existe ese elemento. Se usa para quitar cero o más elementos contiguos.

La tercera función miembro quita cualquier elemento de la secuencia controlada cuya clave tenga una ordenación equivalente a *key*y devuelve un recuento del número de elementos que se han quitado. Se usa para quitar y contar todos los elementos que coinciden con una clave especificada.

Cada eliminación de elementos tarda un tiempo proporcional al logaritmo del número de elementos de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_erase.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    cliext::hash_map<wchar_t, int> c1;
    c1.insert(cliext::hash_map<wchar_t, int>::make_value(L'a', 1));
    c1.insert(cliext::hash_map<wchar_t, int>::make_value(L'b', 2));
    c1.insert(cliext::hash_map<wchar_t, int>::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (cliext::hash_map<wchar_t, int>::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // erase an element and reinspect
    cliext::hash_map<wchar_t, int>::iterator it =
        c1.erase(c1.begin());
    System::Console::WriteLine("erase(begin()) = [{0} {1}]",
        it->first, it->second);

    // add elements and display " b c d e"
    c1.insert(cliext::hash_map<wchar_t, int>::make_value(L'd', 4));
    c1.insert(cliext::hash_map<wchar_t, int>::make_value(L'e', 5));
    for each (cliext::hash_map<wchar_t, int>::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // erase all but end
    it = c1.end();
    it = c1.erase(c1.begin(), --it);
    System::Console::WriteLine("erase(begin(), end()-1) = [{0} {1}]",
        it->first, it->second);
    System::Console::WriteLine("size() = {0}", c1.size());

    // erase end
    System::Console::WriteLine("erase(L'x') = {0}", c1.erase(L'x'));
    System::Console::WriteLine("erase(L'e') = {0}", c1.erase(L'e'));
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
erase(begin()) = [b 2]
[b 2] [c 3] [d 4] [e 5]
erase(begin(), end()-1) = [e 5]
size() = 1
erase(L'x') = 0
erase(L'e') = 1
```

## <a name="hash_mapfind-stlclr"></a><a name="find"></a>hash_map:: Find (STL/CLR)

Busca un elemento que coincide con una clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Parámetros

*key*<br/>
Valor de clave que se va a buscar.

### <a name="remarks"></a>Observaciones

Si al menos un elemento de la secuencia controlada tiene una ordenación equivalente con la *clave*, la función miembro devuelve un iterador que designa uno de esos elementos. en caso contrario, devuelve [hash_map:: end (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)`()`. Se usa para buscar un elemento que se encuentra actualmente en la secuencia controlada que coincide con una clave especificada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_find.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("find {0} = {1}",
        L'A', c1.find(L'A') != c1.end());

    Myhash_map::iterator it = c1.find(L'b');
    System::Console::WriteLine("find {0} = [{1} {2}]",
        L'b', it->first, it->second);

    System::Console::WriteLine("find {0} = {1}",
        L'C', c1.find(L'C') != c1.end());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
find A = False
find b = [b 2]
find C = False
```

## <a name="hash_mapgeneric_container-stlclr"></a><a name="generic_container"></a>hash_map:: generic_container (STL/CLR)

Tipo de la interfaz genérica para el contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Microsoft::VisualC::StlClr::
    IHash<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>Observaciones

El tipo describe la interfaz genérica para esta clase de contenedor de plantillas.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_generic_container.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_map::generic_container^ gc1 = %c1;
    for each (Myhash_map::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(Myhash_map::make_value(L'd', 4));
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify original and display generic
    c1.insert(Myhash_map::make_value(L'e', 5));
    for each (Myhash_map::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3] [d 4]
[a 1] [b 2] [c 3] [d 4] [e 5]
```

## <a name="hash_mapgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>hash_map:: generic_iterator (STL/CLR)

Tipo de un iterador que se va a usar con la interfaz genérica del contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un iterador genérico que se puede usar con la interfaz genérica para esta clase de contenedor de plantillas.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_generic_iterator.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_map::generic_container^ gc1 = %c1;
    for each (Myhash_map::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_map::generic_iterator gcit = gc1->begin();
    Myhash_map::generic_value gcval = *gcit;
    System::Console::Write("[{0} {1}] ", gcval->first, gcval->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1]
```

## <a name="hash_mapgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>hash_map:: generic_reverse_iterator (STL/CLR)

Tipo de un iterador inverso que se va a usar con la interfaz genérica del contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value>
    generic_reverse_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un iterador inverso genérico que se puede usar con la interfaz genérica para esta clase de contenedor de plantillas.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_map::generic_container^ gc1 = %c1;
    for each (Myhash_map::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_map::generic_reverse_iterator gcit = gc1->rbegin();
    Myhash_map::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[c 3]
```

## <a name="hash_mapgeneric_value-stlclr"></a><a name="generic_value"></a>hash_map:: generic_value (STL/CLR)

Tipo de un elemento que se va a usar con la interfaz genérica del contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de tipo `GValue` que describe el valor del elemento almacenado que se va a usar con la interfaz genérica para esta clase de contenedor de plantillas.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_generic_value.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_map::generic_container^ gc1 = %c1;
    for each (Myhash_map::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_map::generic_iterator gcit = gc1->begin();
    Myhash_map::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1]
```

## <a name="hash_maphash_delegate-stlclr"></a><a name="hash_delegate"></a>hash_map:: hash_delegate (STL/CLR)

Busca un elemento que coincide con una clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
hasher^ hash_delegate();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve el delegado que se usa para convertir un valor de clave en un entero. Se usa para aplicar un algoritmo hash a una clave.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_hash_delegate.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    Myhash_map::hasher^ myhash = c1.hash_delegate();

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 1616896120
hash(L'b') = 570892832
```

## <a name="hash_maphash_map-stlclr"></a><a name="hash_map"></a>hash_map:: hash_map (STL/CLR)

Construye un objeto contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
hash_map();
explicit hash_map(key_compare^ pred);
hash_map(key_compare^ pred, hasher^ hashfn);
hash_map(hash_map<Key, Mapped>% right);
hash_map(hash_map<Key, Mapped>^ right);
template<typename InIter>
    hash_maphash_map(InIter first, InIter last);
template<typename InIter>
    hash_map(InIter first, InIter last,
        key_compare^ pred);
template<typename InIter>
    hash_map(InIter first, InIter last,
        key_compare^ pred, hasher^ hashfn);
hash_map(System::Collections::Generic::IEnumerable<GValue>^ right);
hash_map(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
hash_map(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred, hasher^ hashfn);
```

#### <a name="parameters"></a>Parámetros

*first*<br/>
Principio del intervalo que se va a insertar.

*hashfn*<br/>
Función hash para asignar claves a cubos.

*last*<br/>
Final del intervalo que se va a insertar.

*pronostica*<br/>
Predicado de ordenación para la secuencia controlada.

*right*<br/>
Objeto o intervalo que se va a insertar.

### <a name="remarks"></a>Observaciones

El constructor:

`hash_map();`

Inicializa la secuencia controlada sin elementos, con el predicado de ordenación predeterminado `key_compare()`y con la función hash predeterminada. Se usa para especificar una secuencia controlada inicial vacía, con el predicado de ordenación y la función hash predeterminados.

El constructor:

`explicit hash_map(key_compare^ pred);`

Inicializa la secuencia controlada sin elementos, con el predicado de ordenación *Pred*y con la función hash predeterminada. Se usa para especificar una secuencia controlada inicial vacía, con el predicado de ordenación especificado y la función hash predeterminada.

El constructor:

`hash_map(key_compare^ pred, hasher^ hashfn);`

Inicializa la secuencia controlada sin elementos, con el predicado de ordenación *Pred*y con la función hash *hashfn*. Se usa para especificar una secuencia controlada inicial vacía, con el predicado de ordenación y la función hash especificados.

El constructor:

`hash_map(hash_map<Key, Mapped>% right);`

Inicializa la secuencia controlada con la secuencia [`right.begin()`, `right.end()`), con el predicado de ordenación predeterminado y con la función hash predeterminada. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de hash_map *derecha*, con el predicado de ordenación y la función hash predeterminados.

El constructor:

`hash_map(hash_map<Key, Mapped>^ right);`

Inicializa la secuencia controlada con la secuencia [`right->begin()`, `right->end()`), con el predicado de ordenación predeterminado y con la función hash predeterminada. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de hash_map *derecha*, con el predicado de ordenación y la función hash predeterminados.

El constructor:

`template<typename InIter> hash_map(InIter first, InIter last);`

Inicializa la secuencia controlada con la secuencia [`first`, `last`), con el predicado de ordenación predeterminado y con la función hash predeterminada. Se usa para convertir la secuencia controlada en una copia de otra secuencia, con el predicado de ordenación y la función hash predeterminados.

El constructor:

`template<typename InIter> hash_map(InIter first, InIter last, key_compare^ pred);`

Inicializa la secuencia controlada con la secuencia [`first`, `last`), con el predicado de ordenación *Pred*y con la función hash predeterminada. Se usa para convertir la secuencia controlada en una copia de otra secuencia, con el predicado de ordenación especificado y la función hash predeterminada.

El constructor:

`template<typename InIter> hash_map(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`

Inicializa la secuencia controlada con la secuencia [`first`, `last`), con el predicado de ordenación *Pred*y con la función hash *hashfn*. Se usa para convertir la secuencia controlada en una copia de otra secuencia, con el predicado de ordenación y la función hash especificados.

El constructor:

`hash_map(System::Collections::Generic::IEnumerable<Key>^ right);`

Inicializa la secuencia controlada con la secuencia designada por el *derecho*del enumerador, con el predicado de ordenación predeterminado y con la función hash predeterminada. Se usa para convertir la secuencia controlada en una copia de otra secuencia descrita por un enumerador, con el predicado de ordenación y la función hash predeterminados.

El constructor:

`hash_map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

Inicializa la secuencia controlada con la secuencia designada por el *derecho*del enumerador, con el predicado de ordenación *Pred*y con la función hash predeterminada. Se usa para convertir la secuencia controlada en una copia de otra secuencia descrita por un enumerador, con el predicado de ordenación y la función hash predeterminados especificados.

El constructor:

`hash_map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`

Inicializa la secuencia controlada con la secuencia designada por el *derecho*del enumerador, con el predicado de ordenación *Pred*y con la función hash *hashfn*. Se usa para convertir la secuencia controlada en una copia de otra secuencia descrita por un enumerador, con el predicado de ordenación y la función hash especificados.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_construct.cpp
// compile with: /clr
#include <cliext/hash_map>

int myfun(wchar_t key)
    { // hash a key
    return (key ^ 0xdeadbeef);
    }

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
// construct an empty container
    Myhash_map c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an ordering rule
    Myhash_map c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (Myhash_map::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an ordering rule and hash function
    Myhash_map c2h(cliext::greater_equal<wchar_t>(),
        gcnew Myhash_map::hasher(&myfun));
    System::Console::WriteLine("size() = {0}", c2h.size());

    c2h.insert(c1.begin(), c1.end());
    for each (Myhash_map::value_type elem in c2h)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct with an iterator range
    Myhash_map c3(c1.begin(), c1.end());
    for each (Myhash_map::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Myhash_map c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (Myhash_map::value_type elem in c4)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule and hash function
    Myhash_map c4h(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>(),
        gcnew Myhash_map::hasher(&myfun));
    for each (Myhash_map::value_type elem in c4h)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct with an enumeration
    Myhash_map c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Myhash_map::value_type>^)%c3);
    for each (Myhash_map::value_type elem in c5)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Myhash_map c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Myhash_map::value_type>^)%c3,
                cliext::greater_equal<wchar_t>());
    for each (Myhash_map::value_type elem in c6)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule and hash function
    Myhash_map c6h(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Myhash_map::value_type>^)%c3,
                cliext::greater_equal<wchar_t>(),
                gcnew Myhash_map::hasher(&myfun));
    for each (Myhash_map::value_type elem in c6h)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct by copying another container
    Myhash_map c7(c4);
    for each (Myhash_map::value_type elem in c7)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct by copying a container handle
    Myhash_map c8(%c3);
    for each (Myhash_map::value_type elem in c8)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
[a 1] [b 2] [c 3]
size() = 0
[a 1] [b 2] [c 3]
size() = 0
[c 3] [b 2] [a 1]

[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[c 3] [b 2] [a 1]

[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[c 3] [b 2] [a 1]

[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
```

## <a name="hash_maphasher-stlclr"></a><a name="hasher"></a>hash_map:: Hasher (STL/CLR)

Delegado de hash para una clave.

### <a name="syntax"></a>Sintaxis

```cpp
Microsoft::VisualC::StlClr::UnaryDelegate<GKey, int>
    hasher;
```

### <a name="remarks"></a>Observaciones

El tipo describe un delegado que convierte un valor de clave en un entero.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_hasher.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    Myhash_map::hasher^ myhash = c1.hash_delegate();

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 1616896120
hash(L'b') = 570892832
```

## <a name="hash_mapinsert-stlclr"></a><a name="insert"></a>hash_map:: Insert (STL/CLR)

Agrega elementos.

### <a name="syntax"></a>Sintaxis

```cpp
cliext::pair<iterator, bool> insert(value_type val);
iterator insert(iterator where, value_type val);
template<typename InIter>
    void insert(InIter first, InIter last);
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);
```

#### <a name="parameters"></a>Parámetros

*first*<br/>
Principio del intervalo que se va a insertar.

*last*<br/>
Final del intervalo que se va a insertar.

*right*<br/>
Enumeración que se va a insertar.

*val*<br/>
Valor de clave que se va a insertar.

*where*<br/>
Donde en el contenedor se va a insertar (solo sugerencia).

### <a name="remarks"></a>Observaciones

Cada una de las funciones miembro inserta una secuencia especificada por los operandos restantes.

La primera función miembro intenta insertar un elemento con el valor `val`y devuelve un par de valores `X`. Si `X.second` es true, `X.first` designa el elemento recién insertado; de lo contrario `X.first` designa un elemento con una ordenación equivalente que ya existe y no se inserta ningún elemento nuevo. Se usa para insertar un solo elemento.

La segunda función miembro inserta un elemento con el valor *Val*, usando *Where* como una sugerencia (para mejorar el rendimiento) y devuelve un iterador que designa el elemento recién insertado. Se usa para insertar un elemento único que puede ser adyacente a un elemento conocido.

La tercera función miembro inserta la secuencia [`first`, `last`). Se usa para insertar cero o más elementos copiados de otra secuencia.

La cuarta función miembro inserta la secuencia designada por la *derecha*. Se usa para insertar una secuencia descrita por un enumerador.

Cada inserción de elementos tarda un tiempo proporcional al logaritmo del número de elementos de la secuencia controlada. No obstante, la inserción se puede realizar en tiempo constante amortizado, dada una sugerencia que designa un elemento adyacente al punto de inserción.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_insert.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
typedef Myhash_map::pair_iter_bool Pairib;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value, unique and duplicate
    Pairib pair1 =
        c1.insert(Myhash_map::make_value(L'x', 24));
    System::Console::WriteLine("insert([L'x' 24]) = [{0} {1}] {2}",
        pair1.first->first, pair1.first->second, pair1.second);

    pair1 = c1.insert(Myhash_map::make_value(L'b', 2));
    System::Console::WriteLine("insert([L'b' 2]) = [{0} {1}] {2}",
        pair1.first->first, pair1.first->second, pair1.second);

    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value with hint
    Myhash_map::iterator it =
        c1.insert(c1.begin(), Myhash_map::make_value(L'y', 25));
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",
        it->first, it->second);
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an iterator range
    Myhash_map c2;
    it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (Myhash_map::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an enumeration
    Myhash_map c3;
    c3.insert(   // NOTE: cast is not needed
        (System::Collections::Generic::
            IEnumerable<Myhash_map::value_type>^)%c1);
    for each (Myhash_map::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
insert([L'x' 24]) = [x 24] True
insert([L'b' 2]) = [b 2] False
[a 1] [b 2] [c 3] [x 24]
insert(begin(), [L'y' 25]) = [y 25]
[a 1] [b 2] [c 3] [x 24] [y 25]
[a 1] [b 2] [c 3] [x 24]
[a 1] [b 2] [c 3] [x 24] [y 25]
```

## <a name="hash_mapiterator-stlclr"></a><a name="iterator"></a>hash_map:: iterator (STL/CLR)

El tipo de un iterador para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de tipo sin especificar `T1` que puede actuar como un iterador bidireccional para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_iterator.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Myhash_map::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("[{0} {1}] ", it->first, it->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="hash_mapkey_comp-stlclr"></a><a name="key_comp"></a>hash_map:: key_comp (STL/CLR)

Copia el delegado de ordenación de dos claves.

### <a name="syntax"></a>Sintaxis

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve el delegado de ordenación que se usa para ordenar la secuencia controlada. Se usa para comparar dos claves.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_key_comp.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    Myhash_map::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_map c2 = cliext::greater<wchar_t>();
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

## <a name="hash_mapkey_compare-stlclr"></a><a name="key_compare"></a>hash_map:: key_compare (STL/CLR)

Delegado de ordenación para dos claves.

### <a name="syntax"></a>Sintaxis

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>
    key_compare;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del delegado que determina el orden de sus argumentos clave.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_key_compare.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    Myhash_map::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_map c2 = cliext::greater<wchar_t>();
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

## <a name="hash_mapkey_type-stlclr"></a><a name="key_type"></a>hash_map:: key_type (STL/CLR)

El tipo de una clave de ordenación.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de la *clave*de parámetro de plantilla.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_key_type.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using key_type
    for (Myhash_map::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Myhash_map::key_type val = it->first;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="hash_mapload_factor-stlclr"></a><a name="load_factor"></a>hash_map:: load_factor (STL/CLR)

Cuenta los elementos promedio por depósito.

### <a name="syntax"></a>Sintaxis

```cpp
float load_factor();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve `(float)`[hash_map:: Size (STL/CLR)](../dotnet/hash-map-size-stl-clr.md)`() /` [hash_map:: bucket_count (STL/CLR)](../dotnet/hash-map-bucket-count-stl-clr.md)`()`. Se usa para determinar el tamaño promedio del depósito.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_load_factor.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1 = gcnew Myhash_map;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
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
[a 1] [b 2] [c 3]
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

## <a name="hash_maplower_bound-stlclr"></a><a name="lower_bound"></a>hash_map:: lower_bound (STL/CLR)

Busca el principio del intervalo que coincide con una clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Parámetros

*key*<br/>
Valor de clave que se va a buscar.

### <a name="remarks"></a>Observaciones

La función miembro determina el primer elemento `X` en la secuencia controlada que aplica un algoritmo hash al mismo depósito como *clave* y tiene una ordenación equivalente a la *clave*. Si no existe ningún elemento de este tipo, devuelve [hash_map:: end (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)`()`; en caso contrario, devuelve un iterador que designa `X`. Se usa para buscar el principio de una secuencia de elementos que se encuentran actualmente en la secuencia controlada que coinciden con una clave especificada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_lower_bound.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",
        c1.lower_bound(L'x') == c1.end());

    Myhash_map::iterator it = c1.lower_bound(L'a');
    System::Console::WriteLine("*lower_bound(L'a') = [{0} {1}]",
        it->first, it->second);
    it = c1.lower_bound(L'b');
    System::Console::WriteLine("*lower_bound(L'b') = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
lower_bound(L'x')==end() = True
*lower_bound(L'a') = [a 1]
*lower_bound(L'b') = [b 2]
```

## <a name="hash_mapmake_value-stlclr"></a><a name="make_value"></a>hash_map:: make_value (STL/CLR)

Construye un objeto de valor.

### <a name="syntax"></a>Sintaxis

```cpp
static value_type make_value(key_type key, mapped_type mapped);
```

#### <a name="parameters"></a>Parámetros

*key*<br/>
Valor de clave que se va a usar.

*les*<br/>
Valor asignado que se va a buscar.

### <a name="remarks"></a>Observaciones

La función miembro devuelve un `value_type` objeto cuya clave es *clave* y cuyo valor asignado está *asignado*. Se usa para crear un objeto adecuado para su uso con otras funciones miembro.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_make_value.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="hash_mapmapped_type-stlclr"></a><a name="mapped_type"></a>hash_map:: mapped_type (STL/CLR)

El tipo de un valor asignado asociado a cada clave.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Mapped mapped_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla `Mapped`.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_mapped_type.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using mapped_type
    for (Myhash_map::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in mapped_type object
        Myhash_map::mapped_type val = it->second;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
1 2 3
```

## <a name="hash_mapmax_load_factor-stlclr"></a><a name="max_load_factor"></a>hash_map:: max_load_factor (STL/CLR)

Obtiene o establece los elementos máximos por depósito.

### <a name="syntax"></a>Sintaxis

```cpp
float max_load_factor();
void max_load_factor(float new_factor);
```

#### <a name="parameters"></a>Parámetros

*new_factor*<br/>
Nuevo factor de carga máximo para almacenar.

### <a name="remarks"></a>Observaciones

La primera función miembro devuelve el factor de carga máximo almacenado actual. Se usa para determinar el tamaño promedio de cubo máximo.

La segunda función miembro reemplaza el factor de carga máximo del almacén por *new_factor*. No se produce ningún rehash automático hasta una inserción posterior.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_max_load_factor.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1 = gcnew Myhash_map;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
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
[a 1] [b 2] [c 3]
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

## <a name="hash_mapoperator-stlclr"></a><a name="op_as"></a>hash_map:: Operator = (STL/CLR)

Reemplaza la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
hash_map<Key, Mapped>% operator=(hash_map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Contenedor que se va a copiar.

### <a name="remarks"></a>Observaciones

El operador miembro copia *directamente* en el objeto y, a continuación, devuelve `*this`. Se usa para reemplazar la secuencia controlada por una copia de la secuencia controlada a la *derecha*.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_operator_as.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Myhash_map c2;
    c2 = c1;
// display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
```

## <a name="hash_mapoperatorstlclr"></a><a name="op"></a>hash_map:: Operator (STL/CLR)

Asigna una clave a su valor asignado asociado.

### <a name="syntax"></a>Sintaxis

```cpp
mapped_type operator[](key_type key);
```

#### <a name="parameters"></a>Parámetros

*key*<br/>
Valor de clave que se va a buscar.

### <a name="remarks"></a>Observaciones

Las funciones miembro intentan encontrar un elemento con una ordenación equivalente a la *clave*. Si encuentra uno, devuelve el valor asignado asociado; de lo contrario, inserta `value_type(key, mapped_type())` y devuelve el valor asignado (predeterminado) asociado. Se usa para buscar un valor asignado según su clave asociada o para asegurarse de que existe una entrada para la clave si no se encuentra ninguna.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_operator_sub.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("c1[{0}] = {1}",
        L'A', c1[L'A']);
    System::Console::WriteLine("c1[{0}] = {1}",
        L'b', c1[L'b']);

    // redisplay altered contents
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // alter mapped values and redisplay
    c1[L'A'] = 10;
    c1[L'c'] = 13;
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
c1[A] = 0
c1[b] = 2
[a 1] [A 0] [b 2] [c 3]
[a 1] [A 10] [b 2] [c 13]
```

## <a name="hash_maprbegin-stlclr"></a><a name="rbegin"></a>hash_map:: rbegin (STL/CLR)

Designa el principio de la secuencia controlada inversa.

### <a name="syntax"></a>Sintaxis

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador inverso que designa el último elemento de la secuencia controlada o justo después del principio de una secuencia vacía. Por lo tanto, designa el parámetro `beginning` de la secuencia inversa. Se usa para obtener un iterador que designe el principio de la secuencia controlada mostrada en orden inverso, indicado por `current`, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_rbegin.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Myhash_map::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = [{0} {1}]",
        rit->first, rit->second);
    ++rit;
    System::Console::WriteLine("*++rbegin() = [{0} {1}]",
        rit->first, rit->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*rbegin() = [c 3]
*++rbegin() = [b 2]
```

## <a name="hash_mapreference-stlclr"></a><a name="reference"></a>hash_map:: Reference (STL/CLR)

El tipo de una referencia a un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Observaciones

El tipo describe una referencia a un elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_reference.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Myhash_map::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Myhash_map::reference ref = *it;
        System::Console::Write("[{0} {1}] ", ref->first, ref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="hash_maprehash-stlclr"></a><a name="rehash"></a>hash_map:: rehash (STL/CLR)

Recompila la tabla hash.

### <a name="syntax"></a>Sintaxis

```cpp
void rehash();
```

### <a name="remarks"></a>Observaciones

La función miembro vuelve a generar la tabla hash, asegurándose de que [hash_map:: load_factor (STL/CLR)](../dotnet/hash-map-load-factor-stl-clr.md)`() <=` [hash_map:: max_load_factor (STL/CLR)](../dotnet/hash-map-max-load-factor-stl-clr.md). De lo contrario, la tabla hash solo aumenta de tamaño según sea necesario después de una inserción. (Nunca se reduce de tamaño automáticamente). Se usa para ajustar el tamaño de la tabla hash.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_rehash.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1 = gcnew Myhash_map;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
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
[a 1] [b 2] [c 3]
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

## <a name="hash_maprend-stlclr"></a><a name="rend"></a>hash_map:: Rend (STL/CLR)

Designa el final de la secuencia controlada inversa.

### <a name="syntax"></a>Sintaxis

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador inverso que apunta inmediatamente después del principio de la secuencia controlada. Por lo tanto, designa el parámetro `end` de la secuencia inversa. Se usa para obtener un iterador que designe el final de la secuencia controlada mostrada en orden inverso, indicado por `current`, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_rend.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Myhash_map::reverse_iterator rit = c1.rend();
    --rit;
    --rit;
    System::Console::WriteLine("*-- --rend() = [{0} {1}]",
        rit->first, rit->second);
    ++rit;
    System::Console::WriteLine("*--rend() = [{0} {1}]",
        rit->first, rit->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*-- --rend() = [b 2]
*--rend() = [a 1]
```

## <a name="hash_mapreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>hash_map:: reverse_iterator (STL/CLR)

El tipo de un iterador invertido para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de tipo sin especificar `T3` que puede actuar como iterador inverso para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Myhash_map::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("[{0} {1}] ", rit->first, rit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="hash_mapsize-stlclr"></a><a name="size"></a>hash_map:: Size (STL/CLR)

Cuenta el número de elementos.

### <a name="syntax"></a>Sintaxis

```cpp
size_type size();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve la longitud de la secuencia controlada. Se utiliza para determinar el número de elementos que hay actualmente en la secuencia controlada. Si todo lo que le interesa es si la secuencia tiene un tamaño distinto de cero, vea [hash_map:: Empty (STL/CLR)](../dotnet/hash-map-empty-stl-clr.md)`()`.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_size.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.insert(Myhash_map::make_value(L'd', 4));
    c1.insert(Myhash_map::make_value(L'e', 5));
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="hash_mapsize_type-stlclr"></a><a name="size_type"></a>hash_map:: size_type (STL/CLR)

El tipo de una distancia con signo entre dos elementos.

### <a name="syntax"></a>Sintaxis

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Observaciones

El tipo describe un recuento de elementos no negativos.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_size_type.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Myhash_map::size_type diff = 0;
    for (Myhash_map::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
end()-begin() = 3
```

## <a name="hash_mapswap-stlclr"></a><a name="swap"></a>hash_map:: swap (STL/CLR)

Intercambia el contenido de dos contenedores.

### <a name="syntax"></a>Sintaxis

```cpp
void swap(hash_map<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Contenedor con el que se va a intercambiar el contenido.

### <a name="remarks"></a>Observaciones

La función miembro intercambia las secuencias controladas entre `this` y *right*. Lo hace en tiempo constante y no inicia ninguna excepción. Se usa como una forma rápida de intercambiar el contenido de dos contenedores.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_swap.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Myhash_map c2;
    c2.insert(Myhash_map::make_value(L'd', 4));
    c2.insert(Myhash_map::make_value(L'e', 5));
    c2.insert(Myhash_map::make_value(L'f', 6));
    for each (Myhash_map::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    for each (Myhash_map::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[d 4] [e 5] [f 6]
[d 4] [e 5] [f 6]
[a 1] [b 2] [c 3]
```

## <a name="hash_mapto_array-stlclr"></a><a name="to_array"></a>hash_map:: to_array (STL/CLR)

Copia la secuencia controlada en una nueva matriz.

### <a name="syntax"></a>Sintaxis

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve una matriz que contiene la secuencia controlada. Se utiliza para obtener una copia de la secuencia controlada en forma de matriz.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_to_array.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // copy the container and modify it
    cli::array<Myhash_map::value_type>^ a1 = c1.to_array();

    c1.insert(Myhash_map::make_value(L'd', 4));
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (Myhash_map::value_type elem in a1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3] [d 4]
[a 1] [b 2] [c 3]
```

## <a name="hash_mapupper_bound-stlclr"></a><a name="upper_bound"></a>hash_map:: upper_bound (STL/CLR)

Busca el final del intervalo que coincide con una clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Parámetros

*key*<br/>
Valor de clave que se va a buscar.

### <a name="remarks"></a>Observaciones

La función miembro determina el último elemento `X` en la secuencia controlada que aplica un algoritmo hash al mismo depósito como *clave* y tiene una ordenación equivalente a la *clave*. Si no existe ningún elemento de este tipo, o si `X` es el último elemento de la secuencia controlada, devuelve [hash_map:: end (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)`()`; en caso contrario, devuelve un iterador que designa el primer elemento más allá de `X`. Se usa para buscar el final de una secuencia de elementos que se encuentran actualmente en la secuencia controlada que coinciden con una clave especificada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_upper_bound.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Myhash_map::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",
        c1.upper_bound(L'x') == c1.end());

    Myhash_map::iterator it = c1.upper_bound(L'a');
    System::Console::WriteLine("*upper_bound(L'a') = [{0} {1}]",
        it->first, it->second);
    it = c1.upper_bound(L'b');
    System::Console::WriteLine("*upper_bound(L'b') = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
upper_bound(L'x')==end() = True
*upper_bound(L'a') = [b 2]
*upper_bound(L'b') = [c 3]
```

## <a name="hash_mapvalue_comp-stlclr"></a><a name="value_comp"></a>hash_map:: value_comp (STL/CLR)

Copia el delegado de ordenación para dos valores de elemento.

### <a name="syntax"></a>Sintaxis

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve el delegado de ordenación que se usa para ordenar la secuencia controlada. Se usa para comparar dos valores de elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_value_comp.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    Myhash_map::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Myhash_map::make_value(L'a', 1),
            Myhash_map::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Myhash_map::make_value(L'a', 1),
            Myhash_map::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Myhash_map::make_value(L'b', 2),
            Myhash_map::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = True
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="hash_mapvalue_compare-stlclr"></a><a name="value_compare"></a>hash_map:: value_compare (STL/CLR)

Delegado de ordenación para dos valores de elemento.

### <a name="syntax"></a>Sintaxis

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>
    value_compare;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del delegado que determina el orden de sus argumentos de valor.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_value_compare.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    Myhash_map::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Myhash_map::make_value(L'a', 1),
            Myhash_map::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Myhash_map::make_value(L'a', 1),
            Myhash_map::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Myhash_map::make_value(L'b', 2),
            Myhash_map::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = True
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="hash_mapvalue_type-stlclr"></a><a name="value_type"></a>hash_map:: value_type (STL/CLR)

El tipo de un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de `generic_value`.

### <a name="example"></a>Ejemplo

```cpp
// cliext_hash_map_value_type.cpp
// compile with: /clr
#include <cliext/hash_map>

typedef cliext::hash_map<wchar_t, int> Myhash_map;
int main()
    {
    Myhash_map c1;
    c1.insert(Myhash_map::make_value(L'a', 1));
    c1.insert(Myhash_map::make_value(L'b', 2));
    c1.insert(Myhash_map::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using value_type
    for (Myhash_map::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Myhash_map::value_type val = *it;
        System::Console::Write("[{0} {1}] ", val->first, val->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```
