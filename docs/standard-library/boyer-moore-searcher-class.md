---
title: clase boyer_moore_searcher
ms.date: 08/03/2019
f1_keywords:
- functional/std::boyer_moore_searcher
helpviewer_keywords:
- std::boyer_moore_searcher [C++]
ms.openlocfilehash: 3a6741a8ee9988a9842dea691a4ef01254872ed1
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957143"
---
# <a name="boyer_moore_searcher-class"></a>clase boyer_moore_searcher

La `boyer_moore_searcher` clase es un tipo de objeto de función que usa el algoritmo Boyer-Moore para buscar una secuencia especificada en el constructor del objeto. La búsqueda se realiza dentro de otra secuencia proporcionada al operador de llamada de función del objeto. Esta clase se pasa como parámetro a una de las sobrecargas de [STD:: Search](algorithm-functions.md#search).

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
| [operator()](#operator-call) | |

## <a name="boyer-moore-searcher-constructor"></a>constructor de boyer_moore_searcher

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
Elemento inicial de la secuencia que se va a buscar.

*pat_last*\
Final de la secuencia que se va a buscar.

*HF*\
Objeto al que se puede llamar, que se usa para aplicar un algoritmo hash a los elementos de secuencia

*pronostica*\
Predicado de comparación de igualdad opcional para los elementos de la secuencia. Si no se especifica un tipo de comparación de igualdad, `std::equal_to`el valor predeterminado es.

### <a name="remarks"></a>Comentarios

Produce cualquier excepción producida por el constructor de copias de los tipos *BinaryPredicate*, *hash*o *RandomAccessIterator* , o el operador de llamada de *BinaryPredicate* o *hash*.

Esta clase es nueva en C++ 17.

## <a name="operator-call"></a> operator()

El operador de llamada del objeto de función. Busca en la secuencia `[first, last)` de argumentos la secuencia especificada en el constructor.

```cpp
template <class ForwardIterator2>
pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
    RandomAccessIterator2 first,
    RandomAccessIterator2 last) const;
```

### <a name="parameters"></a>Parámetros

*lugar*\
Elemento inicial de la secuencia en la que se va a buscar.

*guardado*\
Final de la secuencia en la que se va a buscar.

### <a name="remarks"></a>Comentarios

Si el patrón `[pat_first, pat_last)` de búsqueda está vacío, `make_pair(first, first)`devuelve. Si no se encuentra el patrón de búsqueda `make_pair(last, last)`, devuelve. De lo contrario, devuelve un par de iteradores al principio y al final de una `[first, last)` secuencia en que es `[pat_first, pat_last)` igual a según el predicado *Pred*.

Esta clase es nueva en C++ 17.

## <a name="see-also"></a>Vea también

[\<functional>](functional.md)\
[funciones de algoritmo](algorithm-functions.md)\
[clase boyer_moore_horspool_searcher](boyer-moore-horspool-searcher-class.md)\
[STD:: Search](algorithm-functions.md#search)
