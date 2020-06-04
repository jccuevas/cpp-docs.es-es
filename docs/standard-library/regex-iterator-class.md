---
title: regex_iterator (Clase)
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_iterator
- regex/std::regex_iterator::operator==
- regex/std::regex_iterator::operator!=
- regex/std::regex_iterator::operator*
- regex/std::regex_iterator::operator->
- regex/std::regex_iterator::operator++
helpviewer_keywords:
- std::regex_iterator
- std::regex_iterator::operator==
- std::regex_iterator::operator!=
- std::regex_iterator::operator*
- std::regex_iterator::operator->
- std::regex_iterator::operator++
ms.assetid: 0cfd8fd0-5a95-4f3c-bf8e-6ef028c423d3
ms.openlocfilehash: 6bc57d6815fa6f30e26b22e9b7ab758a1ac20e16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374552"
---
# <a name="regex_iterator-class"></a>regex_iterator (Clase)

Clase de iterador para las coincidencias.

## <a name="syntax"></a>Sintaxis

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_iterator
```

## <a name="parameters"></a>Parámetros

*BidIt*\
El tipo de iterador para subcoincidencias.

*Elem*\
Tipo de los elementos que debe coincidir.

*RXtraits*\
Clase Traits para los elementos.

## <a name="remarks"></a>Observaciones

La plantilla de clase describe un objeto de iterador de avance constante. Extrae objetos de tipo `match_results<BidIt>` aplicando varias veces su propio objeto de expresión regular `*pregex` a la secuencia de caracteres definida por el rango de iterador `[begin, end)`.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[regex_iterator](#regex_iterator)|Construye el iterador.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[difference_type](#difference_type)|El tipo de diferencia de un iterador.|
|[iterator_category](#iterator_category)|Tipo de la categoría del iterador.|
|[puntero](#pointer)|El tipo de un puntero a una coincidencia.|
|[Referencia](#reference)|El tipo de una referencia a una coincidencia.|
|[regex_type](#regex_type)|El tipo de expresión regular que debe coincidir.|
|[value_type](#value_type)|Tipo de una coincidencia.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[¡Operador!](#op_neq)|Compara iteradores para buscar desigualdad.|
|[operador*](#op_star)|Tiene acceso a la coincidencia designada.|
|[operador++](#op_add_add)|Incrementa el iterador almacenado.|
|[operador](#op_eq)|Compara iteradores para buscar igualdad.|
|[>operador](#op_arrow)|Tiene acceso a la coincidencia designada.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<regex>

**Espacio de nombres:** std

## <a name="examples"></a>Ejemplos

Para obtener ejemplos de expresiones regulares, vea los temas siguientes:

- [regex_match](../standard-library/regex-functions.md#regex_match)

- [regex_replace](../standard-library/regex-functions.md#regex_replace)

- [regex_search](../standard-library/regex-functions.md#regex_search)

- [swap](../standard-library/regex-functions.md#swap)

```cpp
// std__regex__regex_iterator.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::regex_iterator<const char *> Myiter;
int main()
    {
    const char *pat = "axayaz";
    Myiter::regex_type rx("a");
    Myiter next(pat, pat + strlen(pat), rx);
    Myiter end;

    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;

// other members
    Myiter it1(pat, pat + strlen(pat), rx);
    Myiter it2(it1);
    next = it1;

    Myiter::iterator_category cat = std::forward_iterator_tag();
    Myiter::difference_type dif = -3;
    Myiter::value_type mr = *it1;
    Myiter::reference ref = mr;
    Myiter::pointer ptr = &ref;

    dif = dif; // to quiet "unused" warnings
    ptr = ptr;

    return (0);
    }
```

```Output
match == a
match == a
match == a
```

## <a name="regex_iteratordifference_type"></a><a name="difference_type"></a>regex_iterator::difference_type

El tipo de diferencia de un iterador.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de `std::ptrdiff_t`.

## <a name="regex_iteratoriterator_category"></a><a name="iterator_category"></a>regex_iterator::iterator_category

Tipo de la categoría del iterador.

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de `std::forward_iterator_tag`.

## <a name="regex_iteratoroperator"></a><a name="op_neq"></a>regex_iterator::operador!

Compara iteradores para buscar desigualdad.

```cpp
bool operator!=(const regex_iterator& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Iterador con el que se compara.

### <a name="remarks"></a>Observaciones

La función miembro devuelve `!(*this == right)`.

## <a name="regex_iteratoroperator"></a><a name="op_star"></a>regex_iterator::operador*

Tiene acceso a la coincidencia designada.

```cpp
const match_results<BidIt>& operator*();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve el valor almacenado `match`.

## <a name="regex_iteratoroperator"></a><a name="op_add_add"></a>regex_iterator::operador++

Incrementa el iterador almacenado.

```cpp
regex_iterator& operator++();
regex_iterator& operator++(int);
```

### <a name="remarks"></a>Observaciones

Si la coincidencia actual no tiene ningún carácter, el primer operador llama a `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail | regex_constants::match_not_null)`; de lo contrario, pasa el valor almacenado `begin` para señalar el primer carácter después de la coincidencia actual y luego llama a `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail)`. En cualquiera de los casos, si se produce un error en la búsqueda, el operador establece el objeto en un iterador de final de la secuencia. El operador devuelve el objeto.

El segundo operador realiza una copia del objeto, incrementa el objeto y devuelve la copia.

## <a name="regex_iteratoroperator"></a><a name="op_eq"></a>regex_iterator::operador ?

Compara iteradores para buscar igualdad.

```cpp
bool operator==(const regex_iterator& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Iterador con el que se compara.

### <a name="remarks"></a>Observaciones

La función miembro `*this` devuelve true si y *right* son iteradores de fin de `begin == right.begin`secuencia `end == right.end` `pregex == right.pregex`o `flags == right.flags`si ninguno es un iterador de fin de secuencia y , , , y . De lo contrario, devuelve false.

## <a name="regex_iteratoroperator-gt"></a><a name="op_arrow"></a>regex_iterator::operador-&gt;

Tiene acceso a la coincidencia designada.

```cpp
const match_results<BidIt> * operator->();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve la dirección del valor almacenado `match`.

## <a name="regex_iteratorpointer"></a><a name="pointer"></a>regex_iterator::pointer

El tipo de un puntero a una coincidencia.

```cpp
typedef match_results<BidIt> *pointer;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de `match_results<BidIt>*`, donde `BidIt` es el parámetro de plantilla.

## <a name="regex_iteratorreference"></a><a name="reference"></a>regex_iterator::referencia

El tipo de una referencia a una coincidencia.

```cpp
typedef match_results<BidIt>& reference;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de `match_results<BidIt>&`, donde `BidIt` es el parámetro de plantilla.

## <a name="regex_iteratorregex_iterator"></a><a name="regex_iterator"></a>regex_iterator::regex_iterator

Construye el iterador.

```cpp
regex_iterator();

regex_iterator(BidIt first,
    BidIt last,
    const regex_type& re,
    regex_constants::match_flag_type f = regex_constants::match_default);
```

### <a name="parameters"></a>Parámetros

*Primero*\
Principio de la secuencia que debe coincidir.

*Última*\
Final de la secuencia que debe coincidir.

*re*\
Expresión regular para las coincidencias.

*F*\
Marcadores para coincidencias.

### <a name="remarks"></a>Observaciones

El primer constructor crea un iterador de final de secuencia. El segundo constructor inicializa `begin` el valor almacenado `end` con *first*, el valor almacenado `flags` con *last*, el valor `pregex` almacenado con `&re`, y el valor almacenado con *f*. A continuación, llama a `regex_search(begin, end, match, *pregex, flags)`. Si se produce un error en la búsqueda, el constructor establece el objeto en un iterador de final de secuencia.

## <a name="regex_iteratorregex_type"></a><a name="regex_type"></a>regex_iterator::regex_type

El tipo de expresión regular que debe coincidir.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>Observaciones

La definición de tipo es un sinónimo de `basic_regex<Elem, RXtraits>`.

## <a name="regex_iteratorvalue_type"></a><a name="value_type"></a>regex_iterator::value_type

Tipo de una coincidencia.

```cpp
typedef match_results<BidIt> value_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de `match_results<BidIt>`, donde `BidIt` es el parámetro de plantilla.

## <a name="see-also"></a>Consulte también

[\<regex>](../standard-library/regex.md)\
[Clase regex_constants](../standard-library/regex-constants-class.md)\
[Clase regex_error](../standard-library/regex-error-class.md)\
[\<funciones de> regex](../standard-library/regex-functions.md)\
[Clase regex_iterator](../standard-library/regex-iterator-class.md)\
[\<operadores de> regex](../standard-library/regex-operators.md)\
[Clase regex_token_iterator](../standard-library/regex-token-iterator-class.md)\
[Clase regex_traits](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)
