---
title: multimap (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::multimap
- cliext::multimap::begin
- cliext::multimap::clear
- cliext::multimap::const_iterator
- cliext::multimap::const_reference
- cliext::multimap::const_reverse_iterator
- cliext::multimap::count
- cliext::multimap::difference_type
- cliext::multimap::empty
- cliext::multimap::end
- cliext::multimap::equal_range
- cliext::multimap::erase
- cliext::multimap::find
- cliext::multimap::generic_container
- cliext::multimap::generic_iterator
- cliext::multimap::generic_reverse_iterator
- cliext::multimap::generic_value
- cliext::multimap::insert
- cliext::multimap::iterator
- cliext::multimap::key_comp
- cliext::multimap::key_compare
- cliext::multimap::key_type
- cliext::multimap::lower_bound
- cliext::multimap::make_value
- cliext::multimap::mapped_type
- cliext::multimap::multimap
- cliext::multimap::operator=
- cliext::multimap::rbegin
- cliext::multimap::reference
- cliext::multimap::rend
- cliext::multimap::reverse_iterator
- cliext::multimap::size
- cliext::multimap::size_type
- cliext::multimap::swap
- cliext::multimap::to_array
- cliext::multimap::upper_bound
- cliext::multimap::value_comp
- cliext::multimap::value_compare
- cliext::multimap::value_type
- cliext::mutlimap::operator!=
- cliext::mutlimap::operator<
- cliext::mutlimap::operator<=
- cliext::mutlimap::operator==
- cliext::mutlimap::operator>
- cliext::mutlimap::operator>=
helpviewer_keywords:
- <map> header [STL/CLR]
- <cliext/map> header [STL/CLR]
- multimap class [STL/CLR]
- begin member [STL/CLR]
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
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- mapped_type member [STL/CLR]
- multimap member [STL/CLR]
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
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
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
ms.assetid: 3dfe329d-a078-462a-b050-7999ce6110ad
ms.openlocfilehash: 5175aba55a61cb54bbb5b941bb9b78f06a1b4b25
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208532"
---
# <a name="multimap-stlclr"></a>multimap (STL/CLR)

La clase de plantilla describe un objeto que controla una secuencia de elementos de longitud variable que tiene acceso bidireccional. El contenedor `multimap` se utiliza para administrar una secuencia de elementos como un árbol ordenado (casi) equilibrado de nodos, cada uno de los cuales almacena un elemento. Un elemento se compone de una clave, para ordenar la secuencia y un valor asignado, que va junto a la conducción.

En la descripción siguiente, `GValue` es igual que:

`Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`

donde:

`GKey` es igual que la *clave* a menos que la última sea un tipo de referencia, en cuyo caso se `Key^`

`GMapped` es igual que el *asignado* a menos que el último sea un tipo de referencia, en cuyo caso se `Mapped^`

## <a name="syntax"></a>Sintaxis

```cpp
template<typename Key,
    typename Mapped>
    ref class multimap
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>Parámetros

*Clave*<br/>
Tipo del componente clave de un elemento en la secuencia controlada.

*Les*<br/>
Tipo del componente adicional de un elemento en la secuencia controlada.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<cliext (/Map >

**Espacio de nombres:** cliext (

## <a name="declarations"></a>Declaraciones

|Definición de tipo|Descripción|
|---------------------|-----------------|
|[multimap::const_iterator (STL/CLR)](#const_iterator)|El tipo de un iterador constante para la secuencia controlada.|
|[multimap::const_reference (STL/CLR)](#const_reference)|El tipo de una referencia constante a un elemento.|
|[multimap::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|El tipo de un iterador invertido constante para la secuencia controlada.|
|[multimap::difference_type (STL/CLR)](#difference_type)|El tipo de una distancia (posiblemente firmada) entre dos elementos.|
|[multimap::generic_container (STL/CLR)](#generic_container)|Tipo de la interfaz genérica para el contenedor.|
|[multimap::generic_iterator (STL/CLR)](#generic_iterator)|El tipo de un iterador para la interfaz genérica del contenedor.|
|[multimap::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|El tipo de un iterador inverso para la interfaz genérica del contenedor.|
|[multimap::generic_value (STL/CLR)](#generic_value)|Tipo de un elemento de la interfaz genérica para el contenedor.|
|[multimap::iterator (STL/CLR)](#iterator)|El tipo de un iterador para la secuencia controlada.|
|[multimap::key_compare (STL/CLR)](#key_compare)|Delegado de ordenación para dos claves.|
|[multimap::key_type (STL/CLR)](#key_type)|El tipo de una clave de ordenación.|
|[multimap::mapped_type (STL/CLR)](#mapped_type)|Tipo del valor asignado asociado a cada clave.|
|[multimap::reference (STL/CLR)](#reference)|El tipo de una referencia a un elemento.|
|[multimap::reverse_iterator (STL/CLR)](#reverse_iterator)|El tipo de un iterador invertido para la secuencia controlada.|
|[multimap::size_type (STL/CLR)](#size_type)|El tipo de una distancia (no negativa) entre dos elementos.|
|[multimap::value_compare (STL/CLR)](#value_compare)|Delegado de ordenación para dos valores de elemento.|
|[multimap::value_type (STL/CLR)](#value_type)|El tipo de un elemento.|

|Función miembro|Descripción|
|---------------------|-----------------|
|[multimap::begin (STL/CLR)](#begin)|Designa el principio de la secuencia controlada.|
|[multimap::clear (STL/CLR)](#clear)|Quita todos los elementos.|
|[multimap::count (STL/CLR)](#count)|Cuenta los elementos que coinciden con una clave especificada.|
|[multimap::empty (STL/CLR)](#empty)|Comprueba si no hay ningún elemento presente.|
|[multimap::end (STL/CLR)](#end)|Designa el final de la secuencia controlada.|
|[multimap::equal_range (STL/CLR)](#equal_range)|Busca el intervalo que coincide con una clave especificada.|
|[multimap::erase (STL/CLR)](#erase)|Quita los elementos de las posiciones especificadas.|
|[multimap::find (STL/CLR)](#find)|Busca un elemento que coincide con una clave especificada.|
|[multimap::insert (STL/CLR)](#insert)|Agrega elementos.|
|[multimap::key_comp (STL/CLR)](#key_comp)|Copia el delegado de ordenación de dos claves.|
|[multimap::lower_bound (STL/CLR)](#lower_bound)|Busca el principio del intervalo que coincide con una clave especificada.|
|[multimap::make_value (STL/CLR)](#make_value)|Construye un objeto de valor.|
|[multimap::multimap (STL/CLR)](#multimap)|Construye un objeto contenedor.|
|[multimap::rbegin (STL/CLR)](#rbegin)|Designa el principio de la secuencia controlada inversa.|
|[multimap::rend (STL/CLR)](#rend)|Designa el final de la secuencia controlada inversa.|
|[multimap::size (STL/CLR)](#size)|Cuenta el número de elementos.|
|[multimap::swap (STL/CLR)](#swap)|Intercambia el contenido de dos contenedores.|
|[multimap::to_array (STL/CLR)](#to_array)|Copia la secuencia controlada en una nueva matriz.|
|[multimap::upper_bound (STL/CLR)](#upper_bound)|Busca el final del intervalo que coincide con una clave especificada.|
|[multimap::value_comp (STL/CLR)](#value_comp)|Copia el delegado de ordenación para dos valores de elemento.|

|Operator|Descripción|
|--------------|-----------------|
|[multimap::operator= (STL/CLR)](#op_as)|Reemplaza la secuencia controlada.|
|[operator!= (multimap) (STL/CLR)](#op_neq)|Determina si un objeto `multimap` no es igual a otro objeto `multimap`.|
|[operator< (multimap) (STL/CLR)](#op_lt)|Determina si un objeto `multimap` es menor que otro objeto `multimap`.|
|[operator<= (multimap) (STL/CLR)](#op_lteq)|Determina si un objeto `multimap` es menor o igual que otro objeto `multimap`.|
|[operator== (multimap) (STL/CLR)](#op_eq)|Determina si un objeto `multimap` es igual a otro objeto `multimap`.|
|[operator> (multimap) (STL/CLR)](#op_gt)|Determina si un objeto `multimap` es mayor que otro objeto `multimap`.|
|[operator>= (multimap) (STL/CLR)](#op_gteq)|Determina si un objeto `multimap` es mayor o igual que otro objeto `multimap`.|

## <a name="interfaces"></a>Interfaces

|Interfaz|Descripción|
|---------------|-----------------|
|<xref:System.ICloneable>|Duplicar un objeto.|
|<xref:System.Collections.IEnumerable>|Secuencia a través de elementos.|
|<xref:System.Collections.ICollection>|Mantiene el grupo de elementos.|
|<xref:System.Collections.Generic.IEnumerable%601>|Secuencia a través de elementos con tipo.|
|<xref:System.Collections.Generic.ICollection%601>|Mantiene el grupo de elementos con tipo.|
|ITree\<clave, valor >|Mantenga el contenedor genérico.|

## <a name="remarks"></a>Observaciones

El objeto asigna y libera almacenamiento para la secuencia que controla como nodos individuales. Inserta elementos en un árbol equilibrado (casi) que mantiene ordenado modificando los vínculos entre los nodos, nunca copiando el contenido de un nodo en otro. Esto significa que puede insertar y quitar elementos libremente sin molestar a los elementos restantes.

El objeto ordena la secuencia que controla llamando a un objeto delegado almacenado de tipo [Multimap:: key_compare (STL/CLR)](../dotnet/multimap-key-compare-stl-clr.md). Puede especificar el objeto delegado almacenado al construir el Multimap; Si no especifica ningún objeto delegado, el valor predeterminado es el `operator<(key_type, key_type)`de comparación. Puede tener acceso a este objeto almacenado llamando a la función miembro [Multimap:: key_comp (STL/CLR)](../dotnet/multimap-key-comp-stl-clr.md)`()`.

Dicho objeto delegado debe imponer una ordenación débil estricta en las claves de tipo [Multimap:: key_type (STL/CLR)](../dotnet/multimap-key-type-stl-clr.md). Esto significa que, para dos claves `X` y `Y`:

`key_comp()(X, Y)` devuelve el mismo resultado booleano en cada llamada.

Si `key_comp()(X, Y)` es true, `key_comp()(Y, X)` debe ser false.

Si `key_comp()(X, Y)` es true, se dice que `X` se ordena antes que `Y`.

Si `!key_comp()(X, Y) && !key_comp()(Y, X)` es true, se dice que `X` y `Y` tienen una ordenación equivalente.

Para cualquier elemento `X` que preceda a `Y` en la secuencia controlada, `key_comp()(Y, X)` es false. (Para el objeto de delegado predeterminado, las claves nunca disminuyen en el valor). A diferencia de la asignación de clases de plantilla [(STL/CLR)](../dotnet/map-stl-clr.md), un objeto de la clase de plantilla `multimap` no requiere que las claves para todos los elementos sean únicas. (Dos o más claves pueden tener una ordenación equivalente).

Cada elemento contiene una clave independiente y un valor asignado. La secuencia se representa de forma que permite la búsqueda, inserción y eliminación de un elemento arbitrario con un número de operaciones proporcional al logaritmo del número de elementos de la secuencia (tiempo logarítmico). Además, la inserción de un elemento no invalida ningún iterador y al quitar un elemento solo se invalidan los iteradores que apuntan al elemento quitado.

Un Multimap admite iteradores bidireccionales, lo que significa que puede ir a los elementos adyacentes dado un iterador que designa un elemento en la secuencia controlada. Un nodo principal especial corresponde al iterador devuelto por [Multimap:: end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)`()`. Puede reducir este iterador para llegar al último elemento de la secuencia controlada, si está presente. Puede incrementar un iterador Multimap para llegar al nodo principal y, a continuación, se comparará igual que `end()`. Pero no se puede desreferenciar el iterador devuelto por `end()`.

Tenga en cuenta que no puede hacer referencia a un elemento Multimap directamente a partir de su posición numérica, que requiere un iterador de acceso aleatorio.

Un iterador Multimap almacena un identificador en su nodo Multimap asociado, que a su vez almacena un identificador en su contenedor asociado. Solo se pueden usar iteradores con sus objetos de contenedor asociados. Un iterador Multimap sigue siendo válido, siempre y cuando su nodo Multimap asociado esté asociado a algún Multimap. Además, un iterador válido es dereferenceable--se puede usar para obtener acceso al valor del elemento que designa, y siempre que no sea igual que `end()`.

Al borrar o quitar un elemento, se llama al destructor para su valor almacenado. Al destruir el contenedor, se borran todos los elementos. Por lo tanto, un contenedor cuyo tipo de elemento es una clase Ref garantiza que ningún elemento durar más el contenedor. Sin embargo, tenga en cuenta que un contenedor de controladores *no destruye sus* elementos.

## <a name="members"></a>Members

## <a name="multimapbegin-stlclr"></a><a name="begin"></a>Multimap:: Begin (STL/CLR)

Designa el principio de la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator begin();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador bidireccional que designa el primer elemento de la secuencia controlada o más allá del final de una secuencia vacía. Se usa para obtener un iterador que designe el principio de la secuencia controlada, indicado por `current`, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_begin.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items
    Mymultimap::iterator it = c1.begin();
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

## <a name="multimapclear-stlclr"></a><a name="clear"></a>Multimap:: CLEAR (STL/CLR)

Quita todos los elementos.

### <a name="syntax"></a>Sintaxis

```cpp
void clear();
```

### <a name="remarks"></a>Observaciones

La función miembro llama eficazmente a [Multimap:: Erase (STL/CLR)](../dotnet/multimap-erase-stl-clr.md)`(` [Multimap:: Begin (STL/CLR)](../dotnet/multimap-begin-stl-clr.md)`(),` [MULTIMAP:: end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)`())`. Se utiliza para asegurarse de que la secuencia controlada está vacía.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_clear.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));

    // display contents " [a 1] [b 2]"
    for each (Mymultimap::value_type elem in c1)
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

## <a name="multimapconst_iterator-stlclr"></a><a name="const_iterator"></a>Multimap:: const_iterator (STL/CLR)

El tipo de un iterador constante para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de tipo sin especificar `T2` que puede actuar como iterador bidireccional constante para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_const_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymultimap::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("[{0} {1}] ", cit->first, cit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="multimapconst_reference-stlclr"></a><a name="const_reference"></a>Multimap:: const_reference (STL/CLR)

El tipo de una referencia constante a un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Observaciones

El tipo describe una referencia constante a un elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_const_reference.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymultimap::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Mymultimap::const_reference cref = *cit;
        System::Console::Write("[{0} {1}] ", cref->first, cref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="multimapconst_reverse_iterator-stlclr"></a><a name="const_reverse_iterator"></a>Multimap:: const_reverse_iterator (STL/CLR)

El tipo de un iterador invertido constante para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de tipo sin especificar `T4` que puede actuar como un iterador inverso constante para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Mymultimap::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("[{0} {1}] ", crit->first, crit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="multimapcount-stlclr"></a><a name="count"></a>Multimap:: Count (STL/CLR)

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
// cliext_multimap_count.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
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

## <a name="multimapdifference_type-stlclr"></a><a name="difference_type"></a>Multimap::d ifference_type (STL/CLR)

Tipos de una distancia con signo entre dos elementos.

### <a name="syntax"></a>Sintaxis

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Observaciones

El tipo describe un recuento de elementos posiblemente negativos.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_difference_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Mymultimap::difference_type diff = 0;
    for (Mymultimap::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Mymultimap::iterator it = c1.end(); it != c1.begin(); --it)
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

## <a name="multimapempty-stlclr"></a><a name="empty"></a>Multimap:: Empty (STL/CLR)

Comprueba si no hay ningún elemento presente.

### <a name="syntax"></a>Sintaxis

```cpp
bool empty();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve true para una secuencia controlada vacía. Es equivalente a [Multimap:: Size (STL/CLR)](../dotnet/multimap-size-stl-clr.md)`() == 0`. Se utiliza para comprobar si el Multimap está vacío.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_empty.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
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

## <a name="multimapend-stlclr"></a><a name="end"></a>Multimap:: end (STL/CLR)

Designa el final de la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator end();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador bidireccional que apunta justo después del final de la secuencia controlada. Se usa para obtener un iterador que designe el final de la secuencia controlada. su estado no cambia si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_end.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect last two items
    Mymultimap::iterator it = c1.end();
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

## <a name="multimapequal_range-stlclr"></a><a name="equal_range"></a>Multimap:: equal_range (STL/CLR)

Busca el intervalo que coincide con una clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
pair_iter_iter equal_range(key_type _Keyval);
```

#### <a name="parameters"></a>Parámetros

*_Keyval*<br/>
Valor de clave que se va a buscar.

### <a name="remarks"></a>Observaciones

El método devuelve un par de iteradores `-` [Multimap:: lower_bound (STL/CLR)](../dotnet/multimap-lower-bound-stl-clr.md)`(_Keyval),` [multimap:: upper_bound (STL/CLR)](../dotnet/multimap-upper-bound-stl-clr.md)`(_Keyval)`. Se usa para determinar el intervalo de elementos que se encuentran actualmente en la secuencia controlada que coinciden con una clave especificada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_equal_range.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
typedef Mymultimap::pair_iter_iter Pairii;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
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

## <a name="multimaperase-stlclr"></a><a name="erase"></a>Multimap:: Erase (STL/CLR)

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

La primera función miembro quita el elemento de la secuencia controlada a la *que apunta Where*, y devuelve un iterador que designa el primer elemento que permanece más allá del elemento quitado, o [Multimap:: end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)`()` si no existe ese elemento. Se utiliza para quitar un solo elemento.

La segunda función miembro quita los elementos de la secuencia controlada en el intervalo [`first`, `last`) y devuelve un iterador que designa el primer elemento que permanece más allá de los elementos quitados, o `end()` si no existe ese elemento. Se usa para quitar cero o más elementos contiguos.

La tercera función miembro quita cualquier elemento de la secuencia controlada cuya clave tenga una ordenación equivalente a *key*y devuelve un recuento del número de elementos que se han quitado. Se usa para quitar y contar todos los elementos que coinciden con una clave especificada.

Cada eliminación de elementos tarda un tiempo proporcional al logaritmo del número de elementos de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_erase.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    cliext::multimap<wchar_t, int> c1;
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'a', 1));
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'b', 2));
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (cliext::multimap<wchar_t, int>::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // erase an element and reinspect
    cliext::multimap<wchar_t, int>::iterator it =
        c1.erase(c1.begin());
    System::Console::WriteLine("erase(begin()) = [{0} {1}]",
        it->first, it->second);

    // add elements and display " b c d e"
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'd', 4));
    c1.insert(cliext::multimap<wchar_t, int>::make_value(L'e', 5));
    for each (cliext::multimap<wchar_t, int>::value_type elem in c1)
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

## <a name="multimapfind-stlclr"></a><a name="find"></a>Multimap:: Find (STL/CLR)

Busca un elemento que coincide con una clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>Parámetros

*key*<br/>
Valor de clave que se va a buscar.

### <a name="remarks"></a>Observaciones

Si al menos un elemento de la secuencia controlada tiene una ordenación equivalente con la *clave*, la función miembro devuelve un iterador que designa uno de esos elementos. de lo contrario, devuelve [Multimap:: end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)`()`. Se usa para buscar un elemento que se encuentra actualmente en la secuencia controlada que coincide con una clave especificada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_find.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("find {0} = {1}",
        L'A', c1.find(L'A') != c1.end());

    Mymultimap::iterator it = c1.find(L'b');
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

## <a name="multimapgeneric_container-stlclr"></a><a name="generic_container"></a>Multimap:: generic_container (STL/CLR)

Tipo de la interfaz genérica para el contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Microsoft::VisualC::StlClr::
    ITree<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>Observaciones

El tipo describe la interfaz genérica para esta clase de contenedor de plantillas.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_generic_container.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymultimap::generic_container^ gc1 = %c1;
    for each (Mymultimap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(Mymultimap::make_value(L'd', 4));
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify original and display generic
    c1.insert(Mymultimap::make_value(L'e', 5));
    for each (Mymultimap::value_type elem in gc1)
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

## <a name="multimapgeneric_iterator-stlclr"></a><a name="generic_iterator"></a>Multimap:: generic_iterator (STL/CLR)

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
// cliext_multimap_generic_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymultimap::generic_container^ gc1 = %c1;
    for each (Mymultimap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymultimap::generic_iterator gcit = gc1->begin();
    Mymultimap::generic_value gcval = *gcit;
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

## <a name="multimapgeneric_reverse_iterator-stlclr"></a><a name="generic_reverse_iterator"></a>Multimap:: generic_reverse_iterator (STL/CLR)

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
// cliext_multimap_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymultimap::generic_container^ gc1 = %c1;
    for each (Mymultimap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymultimap::generic_reverse_iterator gcit = gc1->rbegin();
    Mymultimap::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[c 3]
```

## <a name="multimapgeneric_value-stlclr"></a><a name="generic_value"></a>Multimap:: generic_value (STL/CLR)

Tipo de un elemento que se va a usar con la interfaz genérica del contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de tipo `GValue` que describe el valor del elemento almacenado que se va a usar con la interfaz genérica para esta clase de contenedor de plantillas.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_generic_value.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymultimap::generic_container^ gc1 = %c1;
    for each (Mymultimap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymultimap::generic_iterator gcit = gc1->begin();
    Mymultimap::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1]
```

## <a name="multimapinsert-stlclr"></a><a name="insert"></a>Multimap:: Insert (STL/CLR)

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
Final del intervalo que se va a insertar.

*right*<br/>
Enumeración que se va a insertar.

*val*<br/>
Valor de clave que se va a insertar.

*where*<br/>
Donde en el contenedor se va a insertar (solo sugerencia).

### <a name="remarks"></a>Observaciones

Cada una de las funciones miembro inserta una secuencia especificada por los operandos restantes.

La primera función miembro inserta un elemento con el valor *Val*y devuelve un iterador que designa el elemento recién insertado. Se usa para insertar un solo elemento.

La segunda función miembro inserta un elemento con el valor *Val*, usando *Where* como una sugerencia (para mejorar el rendimiento) y devuelve un iterador que designa el elemento recién insertado. Se usa para insertar un elemento único que puede ser adyacente a un elemento conocido.

La tercera función miembro inserta la secuencia [`first`, `last`). Se usa para insertar cero o más elementos copiados de otra secuencia.

La cuarta función miembro inserta la secuencia designada por la *derecha*. Se usa para insertar una secuencia descrita por un enumerador.

Cada inserción de elementos tarda un tiempo proporcional al logaritmo del número de elementos de la secuencia controlada. No obstante, la inserción se puede realizar en tiempo constante amortizado, dada una sugerencia que designa un elemento adyacente al punto de inserción.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_insert.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value, unique and duplicate
    Mymultimap::iterator it =
        c1.insert(Mymultimap::make_value(L'x', 24));
    System::Console::WriteLine("insert([L'x' 24]) = [{0} {1}]",
        it->first, it->second);

    it = c1.insert(Mymultimap::make_value(L'b', 2));
    System::Console::WriteLine("insert([L'b' 2]) = [{0} {1}]",
        it->first, it->second);

    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value with hint
    it = c1.insert(c1.begin(), Mymultimap::make_value(L'y', 25));
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",
        it->first, it->second);
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an iterator range
    Mymultimap c2;
    it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an enumeration
    Mymultimap c3;
    c3.insert(   // NOTE: cast is not needed
        (System::Collections::Generic::
            IEnumerable<Mymultimap::value_type>^)%c1);
    for each (Mymultimap::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
insert([L'x' 24]) = [x 24]
insert([L'b' 2]) = [b 2]
[a 1] [b 2] [b 2] [c 3] [x 24]
insert(begin(), [L'y' 25]) = [y 25]
[a 1] [b 2] [b 2] [c 3] [x 24] [y 25]
[a 1] [b 2] [b 2] [c 3] [x 24]
[a 1] [b 2] [b 2] [c 3] [x 24] [y 25]
```

## <a name="multimapiterator-stlclr"></a><a name="iterator"></a>Multimap:: iterator (STL/CLR)

El tipo de un iterador para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de tipo sin especificar `T1` que puede actuar como un iterador bidireccional para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymultimap::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("[{0} {1}] ", it->first, it->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="multimapkey_comp-stlclr"></a><a name="key_comp"></a>Multimap:: key_comp (STL/CLR)

Copia el delegado de ordenación de dos claves.

### <a name="syntax"></a>Sintaxis

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve el delegado de ordenación que se usa para ordenar la secuencia controlada. Se usa para comparar dos claves.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_key_comp.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    Mymultimap::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymultimap c2 = cliext::greater<wchar_t>();
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
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="multimapkey_compare-stlclr"></a><a name="key_compare"></a>Multimap:: key_compare (STL/CLR)

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
// cliext_multimap_key_compare.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    Mymultimap::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymultimap c2 = cliext::greater<wchar_t>();
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
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="multimapkey_type-stlclr"></a><a name="key_type"></a>Multimap:: key_type (STL/CLR)

El tipo de una clave de ordenación.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de la *clave*de parámetro de plantilla.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_key_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using key_type
    for (Mymultimap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Mymultimap::key_type val = it->first;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="multimaplower_bound-stlclr"></a><a name="lower_bound"></a>Multimap:: lower_bound (STL/CLR)

Busca el principio del intervalo que coincide con una clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>Parámetros

*key*<br/>
Valor de clave que se va a buscar.

### <a name="remarks"></a>Observaciones

La función miembro determina el primer elemento `X` en la secuencia controlada que tiene una ordenación equivalente a la *clave*. Si no existe ningún elemento de este tipo, devuelve [Multimap:: end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)`()`; en caso contrario, devuelve un iterador que designa `X`. Se usa para buscar el principio de una secuencia de elementos que se encuentran actualmente en la secuencia controlada que coinciden con una clave especificada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_lower_bound.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",
        c1.lower_bound(L'x') == c1.end());

    Mymultimap::iterator it = c1.lower_bound(L'a');
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

## <a name="multimapmake_value-stlclr"></a><a name="make_value"></a>Multimap:: make_value (STL/CLR)

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
// cliext_multimap_make_value.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="multimapmapped_type-stlclr"></a><a name="mapped_type"></a>Multimap:: mapped_type (STL/CLR)

El tipo de un valor asignado asociado a cada clave.

### <a name="syntax"></a>Sintaxis

```cpp
typedef Mapped mapped_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla *asignado*.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_mapped_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using mapped_type
    for (Mymultimap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in mapped_type object
        Mymultimap::mapped_type val = it->second;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
1 2 3
```

## <a name="multimapmultimap-stlclr"></a><a name="multimap"></a>Multimap:: Multimap (STL/CLR)

Construye un objeto contenedor.

### <a name="syntax"></a>Sintaxis

```cpp
multimap();
explicit multimap(key_compare^ pred);
multimap(multimap<Key, Mapped>% right);
multimap(multimap<Key, Mapped>^ right);
template<typename InIter>
    multimapmultimap(InIter first, InIter last);
template<typename InIter>
    multimap(InIter first, InIter last,
        key_compare^ pred);
multimap(System::Collections::Generic::IEnumerable<GValue>^ right);
multimap(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
```

#### <a name="parameters"></a>Parámetros

*first*<br/>
Principio del intervalo que se va a insertar.

*last*<br/>
Final del intervalo que se va a insertar.

*pronostica*<br/>
Predicado de ordenación para la secuencia controlada.

*right*<br/>
Objeto o intervalo que se va a insertar.

### <a name="remarks"></a>Observaciones

El constructor:

`multimap();`

Inicializa la secuencia controlada sin elementos, con el predicado de ordenación predeterminado `key_compare()`. Se usa para especificar una secuencia controlada inicial vacía, con el predicado de ordenación predeterminado.

El constructor:

`explicit multimap(key_compare^ pred);`

Inicializa la secuencia controlada sin elementos, con el predicado de ordenación *Pred*. Se usa para especificar una secuencia controlada inicial vacía, con el predicado de ordenación especificado.

El constructor:

`multimap(multimap<Key, Mapped>% right);`

Inicializa la secuencia controlada con la secuencia [`right.begin()`, `right.end()`), con el predicado de ordenación predeterminado. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto Multimap a la *derecha*, con el predicado de ordenación predeterminado.

El constructor:

`multimap(multimap<Key, Mapped>^ right);`

Inicializa la secuencia controlada con la secuencia [`right->begin()`, `right->end()`), con el predicado de ordenación predeterminado. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto Multimap a la *derecha*, con el predicado de ordenación predeterminado.

El constructor:

`template<typename InIter> multimap(InIter first, InIter last);`

Inicializa la secuencia controlada con la secuencia [`first`, `last`), con el predicado de ordenación predeterminado. Se usa para convertir la secuencia controlada en una copia de otra secuencia, con el predicado de ordenación predeterminado.

El constructor:

`template<typename InIter> multimap(InIter first, InIter last, key_compare^ pred);`

Inicializa la secuencia controlada con la secuencia [`first`, `last`), con el predicado de ordenación *Pred*. Se usa para convertir la secuencia controlada en una copia de otra secuencia, con el predicado de ordenación especificado.

El constructor:

`multimap(System::Collections::Generic::IEnumerable<Key>^ right);`

Inicializa la secuencia controlada con la secuencia designada por el *derecho*del enumerador, con el predicado de ordenación predeterminado. Se usa para convertir la secuencia controlada en una copia de otra secuencia descrita por un enumerador, con el predicado de ordenación predeterminado.

El constructor:

`multimap(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

Inicializa la secuencia controlada con la secuencia designada por el *derecho*del enumerador, con el predicado de ordenación *Pred*. Se usa para convertir la secuencia controlada en una copia de otra secuencia descrita por un enumerador, con el predicado de ordenación especificado.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_construct.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
// construct an empty container
    Mymultimap c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mymultimap c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range
    Mymultimap c3(c1.begin(), c1.end());
    for each (Mymultimap::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mymultimap c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (Mymultimap::value_type elem in c4)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration
    Mymultimap c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Mymultimap::value_type>^)%c3);
    for each (Mymultimap::value_type elem in c5)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Mymultimap c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Mymultimap::value_type>^)%c3,
                cliext::greater_equal<wchar_t>());
    for each (Mymultimap::value_type elem in c6)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct by copying another container
    Mymultimap c7(c4);
    for each (Mymultimap::value_type elem in c7)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct by copying a container handle
    Mymultimap c8(%c3);
    for each (Mymultimap::value_type elem in c8)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
[a 1] [b 2] [c 3]
size() = 0
[c 3] [b 2] [a 1]
[a 1] [b 2] [c 3]
[c 3] [b 2] [a 1]
[a 1] [b 2] [c 3]
[c 3] [b 2] [a 1]
[c 3] [b 2] [a 1]
[a 1] [b 2] [c 3]
```

## <a name="multimapoperator-stlclr"></a><a name="op_as"></a>Multimap:: Operator = (STL/CLR)

Reemplaza la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
multimap<Key, Mapped>% operator=(multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Contenedor que se va a copiar.

### <a name="remarks"></a>Observaciones

El operador miembro copia *directamente* en el objeto y, a continuación, devuelve `*this`. Se usa para reemplazar la secuencia controlada por una copia de la secuencia controlada a la *derecha*.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_operator_as.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2 = c1;
// display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
```

## <a name="multimaprbegin-stlclr"></a><a name="rbegin"></a>Multimap:: rbegin (STL/CLR)

Designa el principio de la secuencia controlada inversa.

### <a name="syntax"></a>Sintaxis

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador inverso que designa el último elemento de la secuencia controlada o justo después del principio de una secuencia vacía. Por lo tanto, designa el parámetro `beginning` de la secuencia inversa. Se usa para obtener un iterador que designe el principio de la secuencia controlada mostrada en orden inverso, indicado por `current`, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_rbegin.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymultimap::reverse_iterator rit = c1.rbegin();
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

## <a name="multimapreference-stlclr"></a><a name="reference"></a>Multimap:: Reference (STL/CLR)

El tipo de una referencia a un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Observaciones

El tipo describe una referencia a un elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_reference.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymultimap::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Mymultimap::reference ref = *it;
        System::Console::Write("[{0} {1}] ", ref->first, ref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="multimaprend-stlclr"></a><a name="rend"></a>Multimap:: Rend (STL/CLR)

Designa el final de la secuencia controlada inversa.

### <a name="syntax"></a>Sintaxis

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un iterador inverso que apunta inmediatamente después del principio de la secuencia controlada. Por lo tanto, designa el parámetro `end` de la secuencia inversa. Se usa para obtener un iterador que designe el final de la secuencia controlada mostrada en orden inverso, indicado por `current`, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_rend.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymultimap::reverse_iterator rit = c1.rend();
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

## <a name="multimapreverse_iterator-stlclr"></a><a name="reverse_iterator"></a>Multimap:: reverse_iterator (STL/CLR)

El tipo de un iterador invertido para la secuencia controlada.

### <a name="syntax"></a>Sintaxis

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe un objeto de tipo sin especificar `T3` que puede actuar como iterador inverso para la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Mymultimap::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("[{0} {1}] ", rit->first, rit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="multimapsize-stlclr"></a><a name="size"></a>Multimap:: Size (STL/CLR)

Cuenta el número de elementos.

### <a name="syntax"></a>Sintaxis

```cpp
size_type size();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve la longitud de la secuencia controlada. Se utiliza para determinar el número de elementos que hay actualmente en la secuencia controlada. Si todo lo que le interesa es si la secuencia tiene un tamaño distinto de cero, vea [Multimap:: Empty (STL/CLR)](../dotnet/multimap-empty-stl-clr.md)`()`.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_size.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.insert(Mymultimap::make_value(L'd', 4));
    c1.insert(Mymultimap::make_value(L'e', 5));
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="multimapsize_type-stlclr"></a><a name="size_type"></a>Multimap:: size_type (STL/CLR)

El tipo de una distancia con signo entre dos elementos.

### <a name="syntax"></a>Sintaxis

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Observaciones

El tipo describe un recuento de elementos no negativos.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_size_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Mymultimap::size_type diff = 0;
    for (Mymultimap::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
end()-begin() = 3
```

## <a name="multimapswap-stlclr"></a><a name="swap"></a>Multimap:: swap (STL/CLR)

Intercambia el contenido de dos contenedores.

### <a name="syntax"></a>Sintaxis

```cpp
void swap(multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parámetros

*right*<br/>
Contenedor con el que se va a intercambiar el contenido.

### <a name="remarks"></a>Observaciones

La función miembro intercambia las secuencias controladas entre `this` y *right*. Lo hace en tiempo constante y no inicia ninguna excepción. Se usa como una forma rápida de intercambiar el contenido de dos contenedores.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_swap.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'd', 4));
    c2.insert(Mymultimap::make_value(L'e', 5));
    c2.insert(Mymultimap::make_value(L'f', 6));
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    for each (Mymultimap::value_type elem in c2)
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

## <a name="multimapto_array-stlclr"></a><a name="to_array"></a>Multimap:: to_array (STL/CLR)

Copia la secuencia controlada en una nueva matriz.

### <a name="syntax"></a>Sintaxis

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve una matriz que contiene la secuencia controlada. Se utiliza para obtener una copia de la secuencia controlada en forma de matriz.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_to_array.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // copy the container and modify it
    cli::array<Mymultimap::value_type>^ a1 = c1.to_array();

    c1.insert(Mymultimap::make_value(L'd', 4));
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (Mymultimap::value_type elem in a1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3] [d 4]
[a 1] [b 2] [c 3]
```

## <a name="multimapupper_bound-stlclr"></a><a name="upper_bound"></a>Multimap:: upper_bound (STL/CLR)

Busca el final del intervalo que coincide con una clave especificada.

### <a name="syntax"></a>Sintaxis

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>Parámetros

*key*<br/>
Valor de clave que se va a buscar.

### <a name="remarks"></a>Observaciones

La función miembro determina el último elemento `X` en la secuencia controlada que tiene una ordenación equivalente a la *clave*. Si no existe ningún elemento de este tipo, o si `X` es el último elemento de la secuencia controlada, devuelve [Multimap:: end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)`()`; en caso contrario, devuelve un iterador que designa el primer elemento más allá de `X`. Se usa para buscar el final de una secuencia de elementos que se encuentran actualmente en la secuencia controlada que coinciden con una clave especificada.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_upper_bound.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",
        c1.upper_bound(L'x') == c1.end());

    Mymultimap::iterator it = c1.upper_bound(L'a');
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

## <a name="multimapvalue_comp-stlclr"></a><a name="value_comp"></a>Multimap:: value_comp (STL/CLR)

Copia el delegado de ordenación para dos valores de elemento.

### <a name="syntax"></a>Sintaxis

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve el delegado de ordenación que se usa para ordenar la secuencia controlada. Se usa para comparar dos valores de elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_value_comp.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    Mymultimap::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Mymultimap::make_value(L'a', 1),
            Mymultimap::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Mymultimap::make_value(L'a', 1),
            Mymultimap::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Mymultimap::make_value(L'b', 2),
            Mymultimap::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = False
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="multimapvalue_compare-stlclr"></a><a name="value_compare"></a>Multimap:: value_compare (STL/CLR)

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
// cliext_multimap_value_compare.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    Mymultimap::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Mymultimap::make_value(L'a', 1),
            Mymultimap::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Mymultimap::make_value(L'a', 1),
            Mymultimap::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Mymultimap::make_value(L'b', 2),
            Mymultimap::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = False
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="multimapvalue_type-stlclr"></a><a name="value_type"></a>Multimap:: value_type (STL/CLR)

El tipo de un elemento.

### <a name="syntax"></a>Sintaxis

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de `generic_value`.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_value_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using value_type
    for (Mymultimap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Mymultimap::value_type val = *it;
        System::Console::Write("[{0} {1}] ", val->first, val->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="operator-multimap-stlclr"></a><a name="op_neq"></a>Operator! = (Multimap) (STL/CLR)

La comparación de la lista no es igual.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Key,
    typename Mapped>
    bool operator!=(multimap<Key, Mapped>% left,
        multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función de operador devuelve `!(left == right)`. Se usa para probar si la *izquierda* no está ordenada de la misma forma que la *derecha* cuando se comparan las dos múltiples asignaciones elemento a elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_operator_ne.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'a', 1));
    c2.insert(Mymultimap::make_value(L'b', 2));
    c2.insert(Mymultimap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] != [a b c] is {0}",
        c1 != c1);
    System::Console::WriteLine("[a b c] != [a b d] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] != [a b c] is False
[a b c] != [a b d] is True
```

## <a name="operatorlt-multimap-stlclr"></a><a name="op_lt"></a>operador&lt; (Multimap) (STL/CLR)

Lista de comparación inferior a.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Key,
    typename Mapped>
    bool operator<(multimap<Key, Mapped>% left,
        multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función de operador devuelve true si, para la posición más baja `i` para la que `!(right[i] < left[i])` también es true que `left[i] < right[i]`. De lo contrario, devuelve `left->size() < right->size()` se usa para probar si la *izquierda* se ordena antes que a la *derecha* cuando se comparan los dos mapas de elementos por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_operator_lt.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'a', 1));
    c2.insert(Mymultimap::make_value(L'b', 2));
    c2.insert(Mymultimap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] < [a b c] is {0}",
        c1 < c1);
    System::Console::WriteLine("[a b c] < [a b d] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] < [a b c] is False
[a b c] < [a b d] is True
```

## <a name="operatorlt-multimap-stlclr"></a><a name="op_lteq"></a>operador&lt;= (Multimap) (STL/CLR)

Lista de comparación menor o igual que.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Key,
    typename Mapped>
    bool operator<=(multimap<Key, Mapped>% left,
        multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función de operador devuelve `!(right < left)`. Se usa para comprobar si la *izquierda* no se ordena después de la *derecha* cuando se comparan los dos multimaps elemento a elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_operator_le.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'a', 1));
    c2.insert(Mymultimap::make_value(L'b', 2));
    c2.insert(Mymultimap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] <= [a b c] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] <= [a b c] is True
[a b d] <= [a b c] is False
```

## <a name="operator-multimap-stlclr"></a><a name="op_eq"></a>Operator = = (Multimap) (STL/CLR)

Enumera la comparación de igualdad.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Key,
    typename Mapped>
    bool operator==(multimap<Key, Mapped>% left,
        multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función de operador devuelve true solo si las secuencias controladas por *left* y *right* tienen la misma longitud y, para cada posición `i`, `left[i] ==` `right[i]`. Se usa para probar si la *izquierda* se ordena igual que la *derecha* cuando se comparan los dos multimaps elemento a elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_operator_eq.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'a', 1));
    c2.insert(Mymultimap::make_value(L'b', 2));
    c2.insert(Mymultimap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] == [a b c] is {0}",
        c1 == c1);
    System::Console::WriteLine("[a b c] == [a b d] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] == [a b c] is True
[a b c] == [a b d] is False
```

## <a name="operatorgt-multimap-stlclr"></a><a name="op_gt"></a>operador&gt; (Multimap) (STL/CLR)

Lista de comparación mayor que.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Key,
    typename Mapped>
    bool operator>(multimap<Key, Mapped>% left,
        multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función de operador devuelve `right` `left`de `<`. Se usa para probar si la *izquierda* se ordena después de la *derecha* cuando se comparan los dos mapas de elementos por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_operator_gt.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'a', 1));
    c2.insert(Mymultimap::make_value(L'b', 2));
    c2.insert(Mymultimap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] > [a b c] is {0}",
        c1 > c1);
    System::Console::WriteLine("[a b d] > [a b c] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] > [a b c] is False
[a b d] > [a b c] is True
```

## <a name="operatorgt-multimap-stlclr"></a><a name="op_gteq"></a>operador&gt;= (Multimap) (STL/CLR)

Lista de comparación mayor o igual que.

### <a name="syntax"></a>Sintaxis

```cpp
template<typename Key,
    typename Mapped>
    bool operator>=(multimap<Key, Mapped>% left,
        multimap<Key, Mapped>% right);
```

#### <a name="parameters"></a>Parámetros

*left*<br/>
Contenedor izquierdo que se va a comparar.

*right*<br/>
Contenedor derecho que se va a comparar.

### <a name="remarks"></a>Observaciones

La función de operador devuelve `!(left` `right)`de `<`. Se usa para probar si la *izquierda* no está ordenada antes de la *derecha* cuando se comparan los dos mapas de elementos por elemento.

### <a name="example"></a>Ejemplo

```cpp
// cliext_multimap_operator_ge.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::multimap<wchar_t, int> Mymultimap;
int main()
    {
    Mymultimap c1;
    c1.insert(Mymultimap::make_value(L'a', 1));
    c1.insert(Mymultimap::make_value(L'b', 2));
    c1.insert(Mymultimap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymultimap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymultimap c2;
    c2.insert(Mymultimap::make_value(L'a', 1));
    c2.insert(Mymultimap::make_value(L'b', 2));
    c2.insert(Mymultimap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymultimap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] >= [a b c] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] >= [a b c] is True
[a b c] >= [a b d] is False
```
