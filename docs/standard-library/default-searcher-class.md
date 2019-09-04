---
title: clase default_searcher
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: f2b1fe83b5223bbb60e9e32149c101e6379f93c3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2019
ms.locfileid: "68268827"
---
# <a name="default_searcher-class"></a>Clase default_searcher

Un `default_searcher` es un tipo de objeto de función para las operaciones que buscan una secuencia especificada en el constructor del objeto. La búsqueda se realiza dentro de otra secuencia proporcionada al operador de llamada de función del objeto. Invoca STD [:: Search](algorithm-functions.md#search) para realizar la búsqueda. `default_searcher`

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
| [operator()](#operator-call) | |

## <a name="default-searcher-constructor"></a>constructor de default_searcher

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
Elemento inicial de la secuencia que se va a buscar.

*pat_last*\
Final de la secuencia que se va a buscar.

*pronostica*\
Predicado de comparación de igualdad opcional para los elementos de la secuencia. Si no se especifica un tipo de comparación de igualdad, `std::equal_to`el valor predeterminado es.

### <a name="remarks"></a>Comentarios

Produce cualquier excepción producida por el constructor de copias de los tipos *BinaryPredicate* o *ForwardIterator* .

Esta clase es nueva en C++ 17. C++ 20 realizó el constructor `constexpr`.

## <a name="operator-call"></a> operator()

El operador de llamada del operador de función. Busca en la secuencia `[first, last)` de argumentos la secuencia especificada en el constructor.

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

*lugar*\
Elemento inicial de la secuencia en la que se va a buscar.

*guardado*\
Final de la secuencia en la que se va a buscar.

### <a name="remarks"></a>Comentarios

Devuelve un par de iteradores. El iterador inicial *i* es el resultado efectivo de:

`std::search( first, last, pat_first, pat_last, pred )`

El segundo iterador del par es *Last* si *i** es el *último*. De lo contrario, es el resultado efectivo de:

`std::next( i, std::distance( pat_first, pat_last ))`

Esta clase es nueva en C++ 17. C++ 20 realizó el operador `constexpr`de llamada.

## <a name="see-also"></a>Vea también

[\<functional>](functional.md)\
[funciones de algoritmo](algorithm-functions.md)\
[STD:: Search](algorithm-functions.md#search)
