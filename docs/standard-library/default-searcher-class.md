---
title: clase default_searcher
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: 2c8b93b83b271f787c993f789e1a68f84a60f016
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368927"
---
# <a name="default_searcher-class"></a>Clase default_searcher

A `default_searcher` es un tipo de objeto de función para las operaciones que buscan una secuencia especificada en el constructor del objeto. La búsqueda se realiza dentro de otra secuencia proporcionada al operador de llamada de función del objeto. El `default_searcher` invoca [std::search](algorithm-functions.md#search) para realizar la búsqueda.

## <a name="syntax"></a>Sintaxis

```cpp
template <class ForwardIterator, class BinaryPredicate = equal_to<>>
class default_searcher
{
    default_searcher(
        ForwardIterator pat_first,
        ForwardIterator pat_last,
        BinaryPredicate pred = BinaryPredicate());

    template <class ForwardIterator2>
    pair<ForwardIterator2, ForwardIterator2> operator()(
        ForwardIterator2 first,
        ForwardIterator2 last) const;
};
```

## <a name="members"></a>Miembros

| | |
| - | - |
| **Constructor** | |
| [default_searcher](#default-searcher-constructor) | |
| **Operadores** | |
| [operador()](#operator-call) | |

## <a name="default_searcher-constructor"></a><a name="default-searcher-constructor"></a>constructor default_searcher

Construye un `default_searcher` objeto de función mediante la secuencia que se va a buscar y un predicado de igualdad.

```cpp
default_searcher(                   // C++17
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());

constexpr default_searcher(         // C++20
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>Parámetros

*pat_first*\
El elemento inicial de la secuencia que se va a buscar.

*pat_last*\
El final de la secuencia que se va a buscar.

*Pred*\
El predicado de comparación de igualdad opcional para los elementos de secuencia. Si no se especifica un tipo de comparación de igualdad, el valor predeterminado es `std::equal_to`.

### <a name="remarks"></a>Observaciones

Produce cualquier excepción producida por el constructor de copia de la *BinaryPredicate* o *ForwardIterator* tipos.

Esta clase es nueva en C++17. C++20 hizo `constexpr`el constructor .

## <a name="operator"></a><a name="operator-call"></a>operador()

El operador de llamada del operador de función. Busca dentro de `[first, last)` la secuencia de argumentos la secuencia especificada en el constructor.

```cpp
template <class ForwardIterator2>   // C++17
pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;

template <class ForwardIterator2>   // C++20
constexpr pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
El elemento inicial de la secuencia en la que se va a buscar.

*Última*\
El final de la secuencia en la que buscar.

### <a name="remarks"></a>Observaciones

Devuelve un par de iteradores. El iterador inicial *i* es el resultado efectivo de:

`std::search( first, last, pat_first, pat_last, pred )`.

El segundo iterador del par es *last* if *i** is *last*. De lo contrario, es el resultado efectivo de:

`std::next( i, std::distance( pat_first, pat_last ))`.

Esta clase es nueva en C++17. C++20 hizo el `constexpr`operador de llamada .

## <a name="see-also"></a>Consulte también

[\<>funcional](functional.md)\
[funciones de algoritmo](algorithm-functions.md)\
[std::search](algorithm-functions.md#search)
