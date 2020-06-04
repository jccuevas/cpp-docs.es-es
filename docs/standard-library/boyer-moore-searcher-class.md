---
title: clase boyer_moore_searcher
ms.date: 08/03/2019
f1_keywords:
- functional/std::boyer_moore_searcher
helpviewer_keywords:
- std::boyer_moore_searcher [C++]
ms.openlocfilehash: 54e5c4b7c9fe27d6df32f56d57eb1207fa09332c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366765"
---
# <a name="boyer_moore_searcher-class"></a>clase boyer_moore_searcher

La `boyer_moore_searcher` clase es un tipo de objeto de función que utiliza el algoritmo Boyer-Moore para buscar una secuencia especificada en el constructor del objeto. La búsqueda se realiza dentro de otra secuencia proporcionada al operador de llamada de función del objeto. Esta clase se pasa como parámetro a una de las sobrecargas de [std::search](algorithm-functions.md#search).

## <a name="syntax"></a>Sintaxis

```cpp
template <
    class RandomAccessIterator1,
    class Hash = hash<typename iterator_traits<RandomAccessIterator1>::value_type>,
    class BinaryPredicate = equal_to<>>
class boyer_moore_searcher
{
    boyer_moore_searcher(
        RandomAccessIterator1 pat_first,
        RandomAccessIterator1 pat_last,
        Hash hf = Hash(),
        BinaryPredicate pred = BinaryPredicate());

    template <class RandomAccessIterator2>
    pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
        RandomAccessIterator2 first,
        RandomAccessIterator2 last) const;
};
```

## <a name="members"></a>Miembros

| | |
| - | - |
| **Constructor** | |
|[boyer_moore_searcher](#boyer-moore-searcher-constructor)||
| **Operadores** | |
| [operador()](#operator-call) | |

## <a name="boyer_moore_searcher-constructor"></a><a name="boyer-moore-searcher-constructor"></a>constructor boyer_moore_searcher

Construye un `boyer_moore_searcher` objeto de función mediante la secuencia que se va a buscar, un objeto de función hash y un predicado de igualdad.

```cpp
boyer_moore_searcher(
    RandomAccessIterator pat_first,
    RandomAccessIterator pat_last,
    Hash hf = Hash(),
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>Parámetros

*pat_first*\
El elemento inicial de la secuencia que se va a buscar.

*pat_last*\
El final de la secuencia que se va a buscar.

*Hf*\
Objeto invocable, que se utiliza para aplicar hash a los elementos de secuencia.

*Pred*\
El predicado de comparación de igualdad opcional para los elementos de secuencia. Si no se especifica un tipo de comparación de igualdad, el valor predeterminado es `std::equal_to`.

### <a name="remarks"></a>Observaciones

Produce cualquier excepción iniciada por el constructor de copias de los tipos *BinaryPredicate*, *Hash*o *RandomAccessIterator* o el operador de llamada de *BinaryPredicate* o *Hash*.

Esta clase es nueva en C++17.

## <a name="operator"></a><a name="operator-call"></a>operador()

El operador de llamada del objeto de función. Busca dentro de `[first, last)` la secuencia de argumentos la secuencia especificada en el constructor.

```cpp
template <class ForwardIterator2>
pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
    RandomAccessIterator2 first,
    RandomAccessIterator2 last) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
El elemento inicial de la secuencia en la que se va a buscar.

*Última*\
El final de la secuencia en la que buscar.

### <a name="remarks"></a>Observaciones

Si el `[pat_first, pat_last)` patrón de `make_pair(first, first)`búsqueda está vacío, devuelve . Si no se encuentra el `make_pair(last, last)`patrón de búsqueda, devuelve . De lo contrario, devuelve un par de iteradores al principio y al final de una secuencia que `[first, last)` es igual a `[pat_first, pat_last)` según el *pred*de predicado .

Esta clase es nueva en C++17.

## <a name="see-also"></a>Consulte también

[\<>funcional](functional.md)\
[funciones de algoritmo](algorithm-functions.md)\
[clase boyer_moore_horspool_searcher](boyer-moore-horspool-searcher-class.md)\
[std::search](algorithm-functions.md#search)
