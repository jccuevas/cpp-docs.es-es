---
title: algorithm (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/algorithm>
- cliext::adjacent_find
- cliext::binary_search
- cliext::copy
- cliext::copy_backward
- cliext::count
- cliext::count_if
- cliext::equal
- cliext::equal_range
- cliext::fill
- cliext::fill_n
- cliext::find
- cliext::find_end
- cliext::find_first_of
- cliext::find_if
- cliext::for_each
- cliext::generate
- cliext::generate_n
- cliext::includes
- cliext::inplace_merge
- cliext::iter_swap
- cliext::lexicographical_compare
- cliext::lower_bound
- cliext::make_heap
- cliext::max
- cliext::max_element
- cliext::merge
- cliext::min
- cliext::min_element
- cliext::mismatch
- cliext::next_permutation
- cliext::nth_element
- cliext::partial_sort
- cliext::partial_sort_copy
- cliext::partition
- cliext::pop_heap
- cliext::prev_permutation
- cliext::push_heap
- cliext::random_shuffle
- cliext::remove
- cliext::remove_copy
- cliext::remove_copy_if
- cliext::remove_if
- cliext::replace
- cliext::replace_copy
- cliext::replace_copy_if
- cliext::replace_if
- cliext::reverse
- cliext::reverse_copy
- cliext::rotate
- cliext::rotate_copy
- cliext::search
- cliext::search_n
- cliext::set_difference
- cliext::set_intersection
- cliext::set_symmetric_difference
- cliext::set_union
- cliext::sort
- cliext::sort_heap
- cliext::stable_partition
- cliext::stable_sort
- cliext::swap
- cliext::swap_ranges
- cliext::transform
- cliext::unique
- cliext::unique_copy
- cliext::upper_bound
helpviewer_keywords:
- algorithm functions [STL/CLR]
- <algorithm> header [STL/CLR]
- <cliext/algorithm> header [STL/CLR]
- adjacent_find function
- binary_search function [STL/CLR]
- copy function [STL/CLR]
- copy_backward function [STL/CLR]
- count function [STL/CLR]
- count_if function [STL/CLR]
- equal function [STL/CLR]
- equal_range function [STL/CLR]
- fill function
- fill_n function
- find function [STL/CLR]
- find_end function [STL/CLR]
- find_first_of function [STL/CLR]
- find_if function [STL/CLR]
- for_each function [STL/CLR]
- generate function [STL/CLR]
- generate_n function [STL/CLR]
- includes function [STL/CLR]
- inplace_merge function [STL/CLR]
- iter_swap function [STL/CLR]
- lexicographical_compare function [STL/CLR]
- lower_bound function [STL/CLR]
- make_heap function [STL/CLR]
- max function [STL/CLR]
- max_element function [STL/CLR]
- merge function [STL/CLR]
- min function [STL/CLR]
- min_element function [STL/CLR]
- mismatch function [STL/CLR]
- next_permutation function [STL/CLR]
- nth_element function [STL/CLR]
- partial_sort function [STL/CLR]
- partial_sort_copy function [STL/CLR]
- partition function [STL/CLR]
- pop_heap function [STL/CLR]
- prev_permutation function [STL/CLR]
- push_heap function [STL/CLR]
- random_shuffle function [STL/CLR]
- remove function [STL/CLR]
- remove_copy function [STL/CLR]
- remove_copy_if function [STL/CLR]
- remove_if function [STL/CLR]
- replace function [STL/CLR]
- replace_copy function [STL/CLR]
- replace_copy_if function [STL/CLR]
- replace_if function [STL/CLR]
- reverse function [STL/CLR]
- reverse_copy function [STL/CLR]
- rotate function [STL/CLR]
- rotate_copy function [STL/CLR]
- search function [STL/CLR]
- search_n function [STL/CLR]
- set_difference function [STL/CLR]
- set_intersection function [STL/CLR]
- set_symmetric_difference function [STL/CLR]
- set_union function [STL/CLR]
- sort function [STL/CLR]
- sort_heap function [STL/CLR]
- stable_partition function [STL/CLR]
- stable_sort function [STL/CLR]
- swap function [STL/CLR]
- swap_ranges function [STL/CLR]
- transform function [STL/CLR]
- unique function [STL/CLR]
- unique_copy function [STL/CLR]
- upper_bound function [STL/CLR]
ms.assetid: ee2718dc-a98d-40b8-8341-593fe7d2ac15
ms.openlocfilehash: 6011aad0ef86bc0e633687a6d8e017e9b12771c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350837"
---
# <a name="algorithm-stlclr"></a>algorithm (STL/CLR)

Define las funciones de plantilla de contenedor STL/CLR que realizan algoritmos.

## <a name="syntax"></a>Sintaxis

```cpp
#include <cliext/algorithm>
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<cliext/algorithm >

**Namespace:** cliext

## <a name="declarations"></a>Declaraciones

|Función|Descripción|
|--------------|-----------------|
|[adjacent_find (STL/CLR)](#adjacent_find)|Busca dos elementos adyacentes que son iguales.|
|[binary_search (STL/CLR)](#binary_search)|Comprueba si una secuencia ordenada contiene un valor determinado.|
|[copy (STL/CLR)](#copy)|Copia los valores de un intervalo de origen a un intervalo de destino, efectuar una iteración en la dirección de avance.|
|[copy_backward (STL/CLR)](#copy_backward)|Copia los valores de un intervalo de origen a un intervalo de destino, efectuar una iteración en la dirección hacia atrás.|
|[count (STL/CLR)](#count)|Devuelve el número de elementos de un intervalo cuyos valores coinciden con un valor especificado.|
|[count_if (STL/CLR)](#count_if)|Devuelve el número de elementos de un intervalo cuyos valores coinciden con una condición especificada.|
|[equal (STL/CLR)](#equal)|Compara dos intervalos, elemento por elemento.|
|[equal_range (STL/CLR)](#equal_range)|Busca una secuencia ordenada de valores y devuelve dos posiciones que delimitan una subsecuencia de valores que son iguales a un elemento determinado.|
|[fill (STL/CLR)](#fill)|Asigna el mismo valor nuevo a cada elemento de un intervalo especificado.|
|[fill_n (STL/CLR)](#fill_n)|Asigna un nuevo valor a un número especificado de elementos de un intervalo a partir de un elemento determinado.|
|[find (STL/CLR)](#find)|Devuelve la posición de la primera aparición de un valor especificado.|
|[find_end (STL/CLR)](#find_end)|Devuelve la última subsecuencia de un intervalo que es idéntico a una secuencia especificada.|
|[find_first_of (STL/CLR)](#find_first_of)|Busca un intervalo para la primera aparición de cualquiera de un determinado intervalo de elementos.|
|[find_if (STL/CLR)](#find_if)|Devuelve la posición del primer elemento en una secuencia de valores donde el elemento satisface una condición especificada.|
|[for_each (STL/CLR)](#for_each)|Se aplica un objeto de función especificada a cada elemento de una secuencia de valores y devuelve el objeto de función.|
|[generate (STL/CLR)](#generate)|Asigna los valores generados por un objeto de función a cada elemento de una secuencia de valores.|
|[generate_n (STL/CLR)](#generate_n)|Asigna los valores generados por un objeto de función a un número especificado de elementos.|
|[includes (STL/CLR)](#includes)|Comprueba si un intervalo ordenado contiene todos los elementos de un segundo intervalo ordenado.|
|[inplace_merge (STL/CLR)](#inplace_merge)|Combina los elementos de dos intervalos ordenados consecutivos en un solo intervalo ordenado.|
|[iter_swap (STL/CLR)](#iter_swap)|Intercambia dos valores a los que se hace referencia mediante un par de iteradores especificados.|
|[lexicographical_compare (STL/CLR)](#lexicographical_compare)|Compara dos secuencias, elemento por elemento, que identifica qué secuencia es el menor de los dos.|
|[lower_bound (STL/CLR)](#lower_bound)|Busca la posición del primer elemento en una secuencia ordenada de valores que tiene un valor mayor o igual que un valor especificado.|
|[make_heap (STL/CLR)](#make_heap)|Convierte los elementos de un intervalo especificado en un montón donde el primer elemento en el montón es la más grande.|
|[max (STL/CLR)](#max))|Compara dos objetos y devuelve el mayor de los dos.|
|[max_element (STL/CLR)](#max_element)|Busca el elemento más grande en una secuencia de valores especificada.|
|[merge (STL/CLR)](#merge))|Combina todos los elementos de dos intervalos de origen ordenados en un intervalo de destino único, ordenado.|
|[min (STL/CLR)](#min)|Compara dos objetos y devuelve el menor de los dos.|
|[min_element (STL/CLR)](#min_element)|Busca el elemento más pequeño en una secuencia de valores especificada.|
|[mismatch (STL/CLR)](#mismatch)|Compara dos intervalos elemento a elemento y devuelve la primera posición donde se produce una diferencia.|
|[next_permutation (STL/CLR)](#next_permutation)|Reorganiza los elementos de un intervalo de modo que la ordenación original se reemplaza por la mayor permutación lexicográficamente siguiente si existe.|
|[nth_element (STL/CLR)](#nth_element)|Las particiones de una secuencia de elementos, situando correctamente el `n`elemento de la secuencia para que todos los elementos que hay delante sean menor o igual a él y todos los elementos siguientes son mayores o iguales que él.|
|[partial_sort (STL/CLR)](#partial_sort)|Organiza un número especificado de los elementos más pequeños en un intervalo en orden no descendente.|
|[partial_sort_copy (STL/CLR)](#partial_sort_copy)|Copia elementos de un intervalo de origen en un intervalo de destino que se ordenan los elementos del intervalo de origen.|
|[partition (STL/CLR)](#partition)|Organiza los elementos en un intervalo de modo que los elementos que cumplen un predicado unario preceden a los que no lo satisfacen.|
|[pop_heap (STL/CLR)](#pop_heap)|Mueve el elemento más grande de la parte delantera de un montón al final y, a continuación, se forma un montón nuevo con los elementos restantes.|
|[prev_permutation (STL/CLR)](#prev_permutation)|Reorganiza una secuencia de elementos de modo que la ordenación original se reemplaza por la mayor permutación lexicográficamente anterior, si existe.|
|[push_heap (STL/CLR)](#push_heap)|Agrega un elemento que está al final de un intervalo a un montón existente que se compone de los elementos anteriores del intervalo.|
|[random_shuffle (STL/CLR)](#random_shuffle)|¡Reorganiza una secuencia de `N` elementos de un intervalo en uno de `N`! organizaciones posibles seleccionadas aleatoriamente.|
|[remove (STL/CLR)](#remove)|Elimina un valor especificado de un intervalo determinado sin alterar el orden de los elementos restantes y devuelve el final de un nuevo intervalo libre del valor especificado.|
|[remove_copy (STL/CLR)](#remove_copy)|Copia elementos de un intervalo de origen en un intervalo de destino, excepto que no se copian los elementos de un valor especificado, sin alterar el orden de los elementos restantes.|
|[remove_copy_if (STL/CLR)](#remove_copy_if)|Copia los elementos de un intervalo de origen a un intervalo de destino, excepto aquellos que satisfacen un predicado, sin alterar el orden de los elementos restantes.|
|[remove_if (STL/CLR)](#remove_if)|Elimina los elementos que satisfacen un predicado de un intervalo determinado sin alterar el orden de los elementos restantes. .|
|[replace (STL/CLR)](#replace)|Reemplaza los elementos de un intervalo que coincide con un valor especificado con un nuevo valor.|
|[replace_copy (STL/CLR)](#replace_copy)|Copia los elementos de un intervalo de origen a un intervalo de destino, reemplazando los elementos que coinciden con un valor especificado con un nuevo valor.|
|[replace_copy_if (STL/CLR)](#replace_copy_if)|Examina cada elemento de un intervalo de origen y lo reemplaza si satisface un predicado especificado y copia el resultado a un nuevo intervalo de destino.|
|[replace_if (STL/CLR)](#replace_if)|Examina cada elemento de un intervalo y lo reemplaza si satisface un predicado especificado.|
|[reverse (STL/CLR)](#reverse)|Invierte el orden de los elementos dentro de un intervalo.|
|[reverse_copy (STL/CLR)](#reverse_copy)|Invierte el orden de los elementos dentro de un intervalo de origen mientras los copia a un intervalo de destino.|
|[rotate (STL/CLR)](#rotate)|Intercambia los elementos de dos intervalos adyacentes.|
|[rotate_copy (STL/CLR)](#rotate_copy)|Intercambia los elementos de dos intervalos adyacentes dentro de un intervalo de origen y copia el resultado a un intervalo de destino.|
|[search (STL/CLR)](#search_)|Busca la primera aparición de una secuencia dentro de un intervalo de destino cuyos elementos son iguales que los de una secuencia determinada de elementos o cuyos elementos son equivalentes según lo especificado por un predicado binario a los elementos de la secuencia especificada.|
|[search_n (STL/CLR)](#search_n)|Busca la primera subsecuencia de un intervalo en la que un número especificado de elementos tienen un valor determinado o una relación con ese valor según lo especificado por un predicado binario.|
|[set_difference (STL/CLR)](#set_difference)|Agrupa todos los elementos que pertenecen a un intervalo de origen ordenado, pero no a un segundo intervalo de origen ordenado, en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|
|[set_intersection (STL/CLR)](#set_intersection)|Agrupa todos los elementos que pertenecen a ambos intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|
|[set_symmetric_difference (STL/CLR)](#set_symmetric_difference)|Agrupa todos los elementos que pertenecen a uno, pero no a ambos, de los intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|
|[set_union (STL/CLR)](#set_union))|Agrupa todos los elementos que pertenecen al menos a uno de los dos intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|
|[sort (STL/CLR)](#sort)|Organiza los elementos de un intervalo especificado en un orden no descendente o de acuerdo con un criterio de ordenación especificado por un predicado binario.|
|[sort_heap (STL/CLR)](#sort_heap)|Convierte un montón en un intervalo ordenado.|
|[stable_partition (STL/CLR)](#stable_partition)|Clasifica los elementos de un intervalo en dos conjuntos disjuntos, donde los elementos que satisfacen un predicado unario preceden a los que no lo satisfacen, conservando el orden relativo de los elementos equivalentes.|
|[stable_sort (STL/CLR)](#stable_sort)|Organiza los elementos de un intervalo especificado en un orden no descendente o de acuerdo con un criterio de ordenación especificado por un predicado binario y conserva el orden relativo de los elementos equivalentes.|
|[swap (STL/CLR)](#swap)|Intercambia los valores de los elementos entre dos tipos de objetos, asignando el contenido del primer objeto al segundo objeto y el contenido del segundo al primero.|
|[swap_ranges (STL/CLR)](#swap_ranges)|Intercambia los elementos de un intervalo con los elementos de otro intervalo del mismo tamaño.|
|[transform (STL/CLR)](#transform)|Aplica un objeto de función especificado a cada elemento de un intervalo de origen o a un par de elementos de dos intervalos de origen y copia los valores devueltos del objeto de función a un intervalo de destino.|
|[unique (STL/CLR)](#unique)|Quita los elementos duplicados adyacentes entre sí en un intervalo especificado.|
|[unique_copy (STL/CLR)](#unique_copy)|Copia los elementos de un intervalo de origen a un intervalo de destino salvo los elementos duplicados que son adyacentes entre sí.|
|[upper_bound (STL/CLR)](#upper_bound)|Busca la posición del primer elemento de un intervalo ordenado que tiene un valor mayor que un valor especificado, donde el criterio de ordenación se puede especificar mediante un predicado binario.|

## <a name="members"></a>Miembros

## <a name="adjacent_find"></a> adjacent_find (STL/CLR)

Busca dos elementos adyacentes que son iguales o cumplen una condición especificada.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt> inline
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt adjacent_find(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `adjacent_find`. Para obtener más información, consulte [adjacent_find](../standard-library/algorithm-functions.md#adjacent_find).

## <a name="binary_search"></a> binary_search (STL/CLR)

Comprueba si hay un elemento en un intervalo ordenado que sea igual a un valor especificado o equivalente a este del modo especificado por un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt, class _Ty> inline
    bool binary_search(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    bool binary_search(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `binary_search`. Para obtener más información, consulte [binary_search](../standard-library/algorithm-functions.md#binary_search).

## <a name="copy"></a> Copiar (STL/CLR)

Asigna los valores de elementos de un intervalo de origen a un intervalo de destino, recorriendo en iteración la secuencia de origen de elementos y asignándoles nuevas posiciones en una dirección hacia delante.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt copy(_InIt _First, _InIt _Last, _OutIt _Dest);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `copy`. Para obtener más información, consulte [copia](../standard-library/algorithm-functions.md#copy).

## <a name="copy_backward"></a> copy_backward (STL/CLR)

Asigna los valores de elementos de un intervalo de origen a un intervalo de destino, recorriendo en iteración la secuencia de origen de elementos y asignándoles nuevas posiciones en una dirección hacia atrás.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _BidIt1, class _BidIt2> inline
    _BidIt2 copy_backward(_BidIt1 _First, _BidIt1 _Last,
        _BidIt2 _Dest);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `copy_backward`. Para obtener más información, consulte [copy_backward](../standard-library/algorithm-functions.md#copy_backward).

## <a name="count"></a> recuento (STL/CLR)

Devuelve el número de elementos de un intervalo cuyos valores coinciden con un valor especificado.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt, class _Ty> inline
    typename iterator_traits<_InIt>::difference_type
        count(_InIt _First, _InIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `count`. Para obtener más información, consulte [recuento](../standard-library/algorithm-functions.md#count).

## <a name="count_if"></a> count_if (STL/CLR)

Devuelve el número de elementos de un intervalo cuyos valores coinciden con una condición especificada.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt, class _Pr> inline
    typename iterator_traits<_InIt>::difference_type
        count_if(_InIt _First, _InIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `count_if`. Para obtener más información, consulte [count_if](../standard-library/algorithm-functions.md#count_if).

## <a name="equal"></a> equal (STL/CLR)

Compara dos intervalos elemento a elemento para ver si son iguales o equivalentes según lo especificado por un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt1, class _InIt2> inline
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool equal(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `equal`. Para obtener más información, consulte [igual](../standard-library/algorithm-functions.md#equal).

## <a name="equal_range"></a> equal_range (STL/CLR)

Busca un par de posiciones en un intervalo ordenado; la primera es menor o equivalente a la posición de un elemento especificado y la segunda es mayor que la posición del elemento, donde el sentido de equivalencia o de ordenación empleado para establecer las posiciones en la secuencia se puede especificar con un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt, class _Ty> inline
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `equal_range`. Para obtener más información, consulte [equal_range](../standard-library/algorithm-functions.md#equal_range).

## <a name="fill"></a> relleno (STL/CLR)

Asigna el mismo valor nuevo a cada elemento de un intervalo especificado.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt, class _Ty> inline
    void fill(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `fill`. Para obtener más información, consulte [relleno](../standard-library/algorithm-functions.md#fill).

## <a name="fill_n"></a> fill_n (STL/CLR)

Asigna un nuevo valor a un número especificado de elementos de un intervalo a partir de un elemento determinado.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _OutIt, class _Diff, class _Ty> inline
    void fill_n(_OutIt _First, _Diff _Count, const _Ty% _Val);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `fill_n`. Para obtener más información, consulte [fill_n](../standard-library/algorithm-functions.md#fill_n).

## <a name="find"></a> Find (STL/CLR)

Busca la posición de la primera aparición de un elemento en un intervalo que tiene un valor especificado.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt, class _Ty> inline
    _InIt find(_InIt _First, _InIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `find`. Para obtener más información, consulte [encontrar](../standard-library/algorithm-functions.md#find).

## <a name="find_end"></a> find_end (STL/CLR)

Busca en un intervalo la última subsecuencia que es idéntica a una secuencia especificada o que es equivalente según lo especificado por un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 find_end(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `find_end`. Para obtener más información, consulte [find_end](../standard-library/algorithm-functions.md#find_end).

## <a name="find_first_of"></a> find_first_of (STL/CLR)

Busca la primera aparición de cualquiera de varios valores dentro de un intervalo de destino o la primera aparición de cualquiera de varios elementos que son equivalentes según lo especificado por un predicado binario en un conjunto especificado de los elementos.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 find_first_of(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `find_first_of`. Para obtener más información, consulte [find_first_of](../standard-library/algorithm-functions.md#find_first_of).

## <a name="find_if"></a> find_if (STL/CLR)

Busca la posición de la primera aparición de un elemento en un intervalo que cumple una condición especificada.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt, class _Pr> inline
    _InIt find_if(_InIt _First, _InIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `find_if`. Para obtener más información, consulte [find_if](../standard-library/algorithm-functions.md#find_if).

## <a name="for_each"></a> for_each (STL/CLR)

Aplica un objeto de función especificado a cada elemento en un orden hacia delante dentro de un intervalo y devuelve el objeto de función.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt, class _Fn1> inline
    _Fn1 for_each(_InIt _First, _InIt _Last, _Fn1 _Func);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `for_each`. Para obtener más información, consulte [for_each](../standard-library/algorithm-functions.md#for_each).

## <a name="generate"></a> generate (STL/CLR)

Asigna los valores generados por un objeto de función a cada elemento de un intervalo.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt, class _Fn0> inline
    void generate(_FwdIt _First, _FwdIt _Last, _Fn0 _Func);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `generate`. Para obtener más información, consulte [generar](../standard-library/algorithm-functions.md#generate).

## <a name="generate_n"></a> generate_n (STL/CLR)

Asigna los valores generados por un objeto de función a un número especificado de elemento de un intervalo y vuelve a la posición situada una más allá del último valor asignado.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _OutIt, class _Diff, class _Fn0> inline
    void generate_n(_OutIt _Dest, _Diff _Count, _Fn0 _Func);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `generate_n`. Para obtener más información, consulte [generate_n](../standard-library/algorithm-functions.md#generate_n).

## <a name="includes"></a> incluye (STL/CLR)

Prueba si un intervalo ordenado contiene todos los elementos incluidos en un segundo intervalo ordenado, donde el criterio de ordenación o equivalencia entre los elementos se pueden especificar mediante un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt1, class _InIt2> inline
    bool includes(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool includes(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `includes`. Para obtener más información, consulte [incluye](../standard-library/algorithm-functions.md#includes).

## <a name="inplace_merge"></a> inplace_merge (STL/CLR)

Combina los elementos de dos intervalos ordenados consecutivos en un único intervalo ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _BidIt> inline
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    void inplace_merge(_BidIt _First, _BidIt _Mid, _BidIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que el C++ función de la biblioteca estándar `inplace_merge` para obtener más información, consulte [inplace_merge](../standard-library/algorithm-functions.md#inplace_merge).

## <a name="iter_swap"></a> iter_swap (STL/CLR)

Intercambia dos valores a los que se hace referencia mediante un par de iteradores especificados.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    void iter_swap(_FwdIt1 _Left, _FwdIt2 _Right);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `iter_swap`. Para obtener más información, consulte [iter_swap](../standard-library/algorithm-functions.md#iter_swap).

## <a name="lexicographical_compare"></a> lexicographical_compare (STL/CLR)

Compara dos secuencias elemento a elemento para determinar cuál es menor de los dos.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt1, class _InIt2> inline
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2);
template<class _InIt1, class _InIt2, class _Pr> inline
    bool lexicographical_compare(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `lexicographical_compare`. Para obtener más información, consulte [lexicographical_compare](../standard-library/algorithm-functions.md#lexicographical_compare).

## <a name="lower_bound"></a> lower_bound (STL/CLR)

Busca la posición del primer elemento en un intervalo ordenado que tiene un valor menor o equivalente a un valor especificado, donde el criterio de ordenación se puede especificar mediante un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `lower_bound`. Para obtener más información, consulte [lower_bound](../standard-library/algorithm-functions.md#lower_bound).

## <a name="make_heap"></a> make_heap (STL/CLR)

Convierte elementos de un intervalo especificado en un montón en el que el primer elemento es el mayor y para el que se puede especificar un criterio de ordenación con un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _RanIt> inline
    void make_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void make_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `make_heap`. Para obtener más información, consulte [make_heap](../standard-library/algorithm-functions.md#make_heap).

## <a name="max"></a> Max (STL/CLR)

Compara dos objetos y devuelve el mayor de los dos, donde el criterio de ordenación se puede especificar mediante un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _Ty> inline
    const _Ty max(const _Ty% _Left, const _Ty% _Right);
template<class _Ty, class _Pr> inline
    const _Ty max(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `max`. Para obtener más información, consulte [max](../standard-library/algorithm-functions.md#max).

## <a name="max_element"></a> max_element (STL/CLR)

Busca la primera aparición del elemento mayor en un intervalo especificado donde el criterio de ordenación se puede especificar mediante un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt> inline
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `max_element`. Para obtener más información, consulte [max_element](../standard-library/algorithm-functions.md#max_element).

## <a name="merge"></a> merge (STL/CLR)

Combina todos los elementos de dos intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt merge(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `merge`. Para obtener más información, consulte [mezcla](../standard-library/algorithm-functions.md#merge).

## <a name="min"></a> min (STL/CLR)

Compara dos objetos y devuelve el menor de los dos, donde el criterio de ordenación se puede especificar mediante un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _Ty> inline
    const _Ty min(const _Ty% _Left, const _Ty% _Right);
template<class _Ty, class _Pr> inline
    const _Ty min(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `min`. Para obtener más información, consulte [min](../standard-library/algorithm-functions.md#min).

## <a name="min_element"></a> min_element (STL/CLR)

Busca la primera aparición del menor elemento en un intervalo especificado donde el criterio de ordenación se puede especificar mediante un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt> inline
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `min_element`. Para obtener más información, consulte [min_element](../standard-library/algorithm-functions.md#min_element).

## <a name="mismatch"></a> mismatch (STL/CLR)

Compara dos intervalos elemento a elemento para ver si son iguales o equivalentes según lo especificado por un predicado binario y busca la primera posición donde se produce una diferencia.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt1, class _InIt2> inline
    _PAIR_TYPE(_InIt1)
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);
template<class _InIt1, class _InIt2, class _Pr> inline
    _PAIR_TYPE(_InIt1)
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
            _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `mismatch`. Para obtener más información, consulte [discrepancia](../standard-library/algorithm-functions.md#mismatch).

## <a name="next_permutation"></a> next_permutation (STL/CLR)

Reorganiza los elementos de un intervalo de modo que la ordenación original se reemplaza con la mayor permutación lexicográficamente siguiente si existe, donde el sentido de siguiente se puede especificar con un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _BidIt> inline
    bool next_permutation(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    bool next_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `next_permutation`. Para obtener más información, consulte [next_permutation](../standard-library/algorithm-functions.md#next_permutation).

## <a name="nth_element"></a> nth_element (STL/CLR)

Divide un intervalo de elementos, situando correctamente el `n`elemento de la secuencia en el intervalo para que todos los elementos que hay delante sean menor o igual a él y todos los elementos que lo siguen en la secuencia sean mayores o iguales que él.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _RanIt> inline
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `nth_element`. Para obtener más información, consulte [nth_element](../standard-library/algorithm-functions.md#nth_element).

## <a name="partial_sort"></a> partial_sort (STL/CLR)

Organiza un número especificado de los elementos menores de un intervalo en un orden no descendente, o de acuerdo con un criterio de ordenación especificado por un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _RanIt> inline
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void partial_sort(_RanIt _First, _RanIt _Mid, _RanIt _Last,
        _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `partial_sort`. Para obtener más información, consulte [partial_sort](../standard-library/algorithm-functions.md#partial_sort).

## <a name="partial_sort_copy"></a> partial_sort_copy (STL/CLR)

Copia los elementos de un intervalo de origen a un intervalo de destino donde los elementos de origen están ordenados por menor que u otro predicado binario especificado.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt, class _RanIt> inline
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,
        _RanIt _First2, _RanIt _Last2);
template<class _InIt, class _RanIt, class _Pr> inline
    _RanIt partial_sort_copy(_InIt _First1, _InIt _Last1,
        _RanIt _First2, _RanIt _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `partial_sort_copy`. Para obtener más información, consulte [partial_sort_copy](../standard-library/algorithm-functions.md#partial_sort_copy).

## <a name="partition"></a> partición (STL/CLR)

Clasifica los elementos de un intervalo en dos conjuntos disjuntos, donde los elementos que satisfacen un predicado unario preceden a los que no lo satisfacen.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _BidIt, class _Pr> inline
    _BidIt partition(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `partition`. Para obtener más información, consulte [partición](../standard-library/algorithm-functions.md#partition).

## <a name="pop_heap"></a> pop_heap (STL/CLR)

Quita el elemento mayor del principio de un montón hasta la penúltima posición del intervalo y después forma un nuevo montón con los elementos restantes.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _RanIt> inline
    void pop_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void pop_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `pop_heap`. Para obtener más información, consulte [pop_heap](../standard-library/algorithm-functions.md#pop_heap).

## <a name="prev_permutation"></a> prev_permutation (STL/CLR)

Reorganiza los elementos de un intervalo de modo que la ordenación original se reemplaza con la mayor permutación lexicográficamente siguiente si existe, donde el sentido de siguiente se puede especificar con un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _BidIt> inline
    bool prev_permutation(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    bool prev_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `prev_permutation`. Para obtener más información, consulte [prev_permutation](../standard-library/algorithm-functions.md#prev_permutation).

## <a name="push_heap"></a> push_heap (STL/CLR)

Agrega un elemento que está al final de un intervalo a un montón existente que se compone de los elementos anteriores del intervalo.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _RanIt> inline
    void push_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void push_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `push_heap`. Para obtener más información, consulte [push_heap](../standard-library/algorithm-functions.md#push_heap).

## <a name="random_shuffle"></a> random_shuffle (STL/CLR)

¡Reorganiza una secuencia de `N` elementos de un intervalo en uno de `N`! organizaciones posibles seleccionadas aleatoriamente.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _RanIt> inline
    void random_shuffle(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Fn1> inline
    void random_shuffle(_RanIt _First, _RanIt _Last, _Fn1% _Func);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `random_shuffle`. Para obtener más información, consulte [random_shuffle](../standard-library/algorithm-functions.md#random_shuffle).

## <a name="remove"></a> Quitar (STL/CLR)

Elimina un valor especificado de un intervalo determinado sin alterar el orden de los elementos restantes y devolver el final de un nuevo intervalo libre del valor especificado.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt remove(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `remove`. Para obtener más información, consulte [quitar](../standard-library/algorithm-functions.md#remove).

## <a name="remove_copy"></a> remove_copy (STL/CLR)

Copia elementos de un intervalo de origen a un intervalo de destino, excepto que los elementos de un valor especificado no se copian, sin alterar el orden de los elementos restantes y devolver el final de un nuevo intervalo de destino.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt, class _OutIt, class _Ty> inline
    _OutIt remove_copy(_InIt _First, _InIt _Last,
        _OutIt _Dest, const _Ty% _Val);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `remove_copy`. Para obtener más información, consulte [remove_copy](../standard-library/algorithm-functions.md#remove_copy).

## <a name="remove_copy_if"></a> remove_copy_if (STL/CLR)

Copia elementos de un intervalo de origen a un intervalo de destino, excepto que los elementos que satisfacen un predicado no se copian, sin alterar el orden de los elementos restantes y devolver el final de un nuevo intervalo de destino.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt, class _OutIt, class _Pr> inline
    _OutIt remove_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `remove_copy_if`. Para obtener más información, consulte [remove_copy_if](../standard-library/algorithm-functions.md#remove_copy_if).

## <a name="remove_if"></a> remove_if (STL/CLR)

Elimina los elementos que cumplen un predicado de un intervalo determinado sin alterar el orden de los elementos restantes y devolver el final de un nuevo intervalo libre del valor especificado.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt, class _Pr> inline
    _FwdIt remove_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `remove_if`. Para obtener más información, consulte [remove_if](../standard-library/algorithm-functions.md#remove_if).

## <a name="replace"></a> Replace (STL/CLR)

Examina cada elemento de un intervalo y lo reemplaza si coincide con un valor especificado.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt, class _Ty> inline
    void replace(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Oldval, const _Ty% _Newval);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `replace`. Para obtener más información, consulte [reemplazar](../standard-library/algorithm-functions.md#replace).

## <a name="replace_copy"></a> replace_copy (STL/CLR)

Examina cada elemento de un intervalo de origen y lo reemplaza si coincide con un valor especificado y copia el resultado a un nuevo intervalo de destino.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt, class _OutIt, class _Ty> inline
    _OutIt replace_copy(_InIt _First, _InIt _Last, _OutIt _Dest,
        const _Ty% _Oldval, const _Ty% _Newval);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `replace_copy`. Para obtener más información, consulte [replace_copy](../standard-library/algorithm-functions.md#replace_copy).

## <a name="replace_copy_if"></a> replace_copy_if (STL/CLR)

Examina cada elemento de un intervalo de origen y lo reemplaza si satisface un predicado especificado y copia el resultado a un nuevo intervalo de destino.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt, class _OutIt, class _Pr, class _Ty> inline
    _OutIt replace_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred, const _Ty% _Val);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `replace_copy_if`. Para obtener más información, consulte [replace_copy_if](../standard-library/algorithm-functions.md#replace_copy_if).

## <a name="replace_if"></a> replace_if (STL/CLR)

Examina cada elemento de un intervalo y lo reemplaza si satisface un predicado especificado.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt, class _Pr, class _Ty> inline
    void replace_if(_FwdIt _First, _FwdIt _Last, _Pr _Pred,
        const _Ty% _Val);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `replace_if`. Para obtener más información, consulte [replace_if](../standard-library/algorithm-functions.md#replace_if).

## <a name="reverse"></a> Reverse (STL/CLR)

Invierte el orden de los elementos dentro de un intervalo.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _BidIt> inline
    void reverse(_BidIt _First, _BidIt _Last);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `reverse`. Para obtener más información, consulte [inverso](../standard-library/algorithm-functions.md#reverse).

## <a name="reverse_copy"></a> reverse_copy (STL/CLR)

Invierte el orden de los elementos dentro de un intervalo de origen mientras los copia a un intervalo de destino.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _BidIt, class _OutIt> inline
    _OutIt reverse_copy(_BidIt _First, _BidIt _Last, _OutIt _Dest);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `reverse_copy`. Para obtener más información, consulte [reverse_copy](../standard-library/algorithm-functions.md#reverse_copy).

## <a name="rotate"></a> Girar (STL/CLR)

Intercambia los elementos de dos intervalos adyacentes.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt> inline
    void rotate(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `rotate`. Para obtener más información, consulte [girar](../standard-library/algorithm-functions.md#rotate).

## <a name="rotate_copy"></a> rotate_copy (STL/CLR)

Intercambia los elementos de dos intervalos adyacentes dentro de un intervalo de origen y copia el resultado a un intervalo de destino.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt, class _OutIt> inline
    _OutIt rotate_copy(_FwdIt _First, _FwdIt _Mid, _FwdIt _Last,
        _OutIt _Dest);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `rotate_copy`. Para obtener más información, consulte [rotate_copy](../standard-library/algorithm-functions.md#rotate_copy).

## <a name="search_"></a> search (STL/CLR)

Busca la primera aparición de una secuencia dentro de un intervalo de destino cuyos elementos son iguales que los de una secuencia determinada de elementos o cuyos elementos son equivalentes según lo especificado por un predicado binario a los elementos de la secuencia especificada.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2);
template<class _FwdIt1, class _FwdIt2, class _Pr> inline
    _FwdIt1 search(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2, _FwdIt2 _Last2, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `search`. Para obtener más información, consulte [búsqueda](../standard-library/algorithm-functions.md#search).

## <a name="search_n"></a> search_n (STL/CLR)

Busca la primera subsecuencia de un intervalo en la que un número especificado de elementos tienen un valor determinado o una relación con ese valor según lo especificado por un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt1, class _Diff2, class _Ty> inline
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,
        _Diff2 _Count, const _Ty& _Val);
template<class _FwdIt1, class _Diff2, class _Ty, class _Pr> inline
    _FwdIt1 search_n(_FwdIt1 _First1, _FwdIt1 _Last1,
        _Diff2 _Count, const _Ty& _Val, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `search_n`. Para obtener más información, consulte [search_n](../standard-library/algorithm-functions.md#search_n).

## <a name="set_difference"></a> set_difference (STL/CLR)

Agrupa todos los elementos que pertenecen a un intervalo de origen ordenado, pero no a un segundo intervalo de origen ordenado, en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2,_OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `set_difference`. Para obtener más información, consulte [set_difference](../standard-library/algorithm-functions.md#set_difference).

## <a name="set_intersection"></a> set_intersection (STL/CLR)

Agrupa todos los elementos que pertenecen a ambos intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_intersection(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `set_intersection`. Para obtener más información, consulte [set_intersection](../standard-library/algorithm-functions.md#set_intersection).

## <a name="set_symmetric_difference"></a> set_symmetric_difference (STL/CLR)

Agrupa todos los elementos que pertenecen a uno, pero no a ambos, de los intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_symmetric_difference(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `set_symmetric_difference`. Para obtener más información, consulte [set_symmetric_difference](../standard-library/algorithm-functions.md#set_symmetric_difference).

## <a name="set_union"></a> set_union (STL/CLR)

Agrupa todos los elementos que pertenecen al menos a uno de los dos intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt1, class _InIt2, class _OutIt> inline
    _OutIt set_union(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest);
template<class _InIt1, class _InIt2, class _OutIt, class _Pr> inline
    _OutIt set_union(_InIt1 _First1, _InIt1 _Last1,
        _InIt2 _First2, _InIt2 _Last2, _OutIt _Dest, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `set_union`. Para obtener más información, consulte [set_union](../standard-library/algorithm-functions.md#set_union).

## <a name="sort"></a> sort (STL/CLR)

Organiza los elementos de un intervalo especificado en un orden no descendente o de acuerdo con un criterio de ordenación especificado por un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _RanIt> inline
    void sort(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void sort(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `sort`. Para obtener más información, consulte [ordenación](../mfc/reference/cmfclistctrl-class.md#sort).

## <a name="sort_heap"></a> sort_heap (STL/CLR)

Convierte un montón en un intervalo ordenado.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _RanIt> inline
    void sort_heap(_RanIt _First, _RanIt _Last);
template<class _RanIt, class _Pr> inline
    void sort_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `sort_heap`. Para obtener más información, consulte [sort_heap](../standard-library/algorithm-functions.md#sort_heap).

## <a name="stable_partition"></a> stable_partition (STL/CLR)

Clasifica los elementos de un intervalo en dos conjuntos disjuntos, donde los elementos que satisfacen un predicado unario preceden a los que no lo satisfacen, conservando el orden relativo de los elementos equivalentes.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _BidIt, class _Pr> inline
    _BidIt stable_partition(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `stable_partition`. Para obtener más información, consulte [stable_partition](../standard-library/algorithm-functions.md#stable_partition).

## <a name="stable_sort"></a> stable_sort (STL/CLR)

Organiza los elementos de un intervalo especificado en un orden no descendente o de acuerdo con un criterio de ordenación especificado por un predicado binario y conserva el orden relativo de los elementos equivalentes.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _BidIt> inline
    void stable_sort(_BidIt _First, _BidIt _Last);
template<class _BidIt, class _Pr> inline
    void stable_sort(_BidIt _First, _BidIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `stable_sort`. Para obtener más información, consulte [stable_sort](../standard-library/algorithm-functions.md#stable_sort).

## <a name="swap"></a> swap (STL/CLR)

Intercambia los valores de los elementos entre dos tipos de objetos, asignando el contenido del primer objeto al segundo objeto y el contenido del segundo al primero.

### <a name="syntax"></a>Sintaxis

```cpp
<class _Ty> inline
    void swap(_Ty% _Left, _Ty% _Right);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `swap`. Para obtener más información, consulte [intercambio](../standard-library/algorithm-functions.md#swap).

## <a name="swap_ranges"></a> swap_ranges (STL/CLR)

Intercambia los elementos de un intervalo con los elementos de otro intervalo del mismo tamaño.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt1, class _FwdIt2> inline
    _FwdIt2 swap_ranges(_FwdIt1 _First1, _FwdIt1 _Last1,
        _FwdIt2 _First2);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `swap_ranges`. Para obtener más información, consulte [swap_ranges](../standard-library/algorithm-functions.md#swap_ranges).

## <a name="transform"></a> transformación (STL/CLR)

Aplica un objeto de función especificado a cada elemento de un intervalo de origen o a un par de elementos de dos intervalos de origen y copia los valores devueltos del objeto de función a un intervalo de destino.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt, class _OutIt, class _Fn1> inline
    _OutIt transform(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Fn1 _Func);
template<class _InIt1, class _InIt2, class _OutIt, class _Fn2> inline
    _OutIt transform(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `transform`. Para obtener más información, consulte [transformar](../standard-library/algorithm-functions.md#transform).

## <a name="unique"></a> exclusivo (STL/CLR)

Quita los elementos duplicados adyacentes entre sí en un intervalo especificado.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt> inline
    _FwdIt unique(_FwdIt _First, _FwdIt _Last);
template<class _FwdIt, class _Pr> inline
    _FwdIt unique(_FwdIt _First, _FwdIt _Last, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `unique`. Para obtener más información, consulte [único](../standard-library/algorithm-functions.md#unique).

## <a name="unique_copy"></a> unique_copy (STL/CLR)

Copia los elementos de un intervalo de origen a un intervalo de destino salvo los elementos duplicados que son adyacentes entre sí.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest);
template<class _InIt, class _OutIt, class _Pr> inline
    _OutIt unique_copy(_InIt _First, _InIt _Last, _OutIt _Dest,
        _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `unique_copy`. Para obtener más información, consulte [unique_copy](../standard-library/algorithm-functions.md#unique_copy).

## <a name="upper_bound"></a> upper_bound (STL/CLR)

Busca la posición del primer elemento de un intervalo ordenado que tiene un valor mayor que un valor especificado, donde el criterio de ordenación se puede especificar mediante un predicado binario.

### <a name="syntax"></a>Sintaxis

```cpp
template<class _FwdIt, class _Ty> inline
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);
template<class _FwdIt, class _Ty, class _Pr> inline
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last,
        const _Ty% _Val, _Pr _Pred);
```

### <a name="remarks"></a>Comentarios

Esta función comporta igual que la función de la biblioteca estándar de C++ `upper_bound`. Para obtener más información, consulte [upper_bound](../standard-library/algorithm-functions.md#upper_bound).