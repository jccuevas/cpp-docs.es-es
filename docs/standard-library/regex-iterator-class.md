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
ms.openlocfilehash: fb609df2bf52873dac3cddaa6b12f82ea1b53237
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689084"
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

@No__t_1 *BidIt*
El tipo de iterador para subcoincidencias.

@No__t_1 *Elem*
Tipo de los elementos que debe coincidir.

@No__t_1 *RXtraits*
Clase Traits para los elementos.

## <a name="remarks"></a>Comentarios

La plantilla de clase describe un objeto de iterador hacia delante constante. Extrae objetos de tipo `match_results<BidIt>` aplicando varias veces su propio objeto de expresión regular `*pregex` a la secuencia de caracteres definida por el rango de iterador `[begin, end)`.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[regex_iterator](#regex_iterator)|Construye el iterador.|

### <a name="typedefs"></a>Definiciones de tipo

|Nombre de tipo|Descripción|
|-|-|
|[difference_type](#difference_type)|El tipo de diferencia de un iterador.|
|[iterator_category](#iterator_category)|Tipo de la categoría del iterador.|
|[pointer](#pointer)|El tipo de un puntero a una coincidencia.|
|[reference](#reference)|El tipo de una referencia a una coincidencia.|
|[regex_type](#regex_type)|El tipo de expresión regular que debe coincidir.|
|[value_type](#value_type)|Tipo de una coincidencia.|

### <a name="operators"></a>Operadores

|"??"|Descripción|
|-|-|
|[operator!=](#op_neq)|Compara iteradores para buscar desigualdad.|
|[operator*](#op_star)|Tiene acceso a la coincidencia designada.|
|[operator++](#op_add_add)|Incrementa el iterador almacenado.|
|[operator=](#op_eq)|Compara iteradores para buscar igualdad.|
|[operator->](#op_arrow)|Tiene acceso a la coincidencia designada.|

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

## <a name="difference_type"></a>  regex_iterator::difference_type

El tipo de diferencia de un iterador.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de `std::ptrdiff_t`.

## <a name="iterator_category"></a>  regex_iterator::iterator_category

Tipo de la categoría del iterador.

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de `std::forward_iterator_tag`.

## <a name="op_neq"></a>  regex_iterator::operator!=

Compara iteradores para buscar desigualdad.

```cpp
bool operator!=(const regex_iterator& right);
```

### <a name="parameters"></a>Parámetros

\ *derecha*
Iterador con el que se compara.

### <a name="remarks"></a>Comentarios

La función miembro devuelve `!(*this == right)`.

## <a name="op_star"></a>  regex_iterator::operator*

Tiene acceso a la coincidencia designada.

```cpp
const match_results<BidIt>& operator*();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve el valor almacenado `match`.

## <a name="op_add_add"></a>  regex_iterator::operator++

Incrementa el iterador almacenado.

```cpp
regex_iterator& operator++();
regex_iterator& operator++(int);
```

### <a name="remarks"></a>Comentarios

Si la coincidencia actual no tiene ningún carácter, el primer operador llama a `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail | regex_constants::match_not_null)`; de lo contrario, pasa el valor almacenado `begin` para señalar el primer carácter después de la coincidencia actual y luego llama a `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail)`. En cualquiera de los casos, si se produce un error en la búsqueda, el operador establece el objeto en un iterador de final de la secuencia. El operador devuelve el objeto.

El segundo operador realiza una copia del objeto, incrementa el objeto y devuelve la copia.

## <a name="op_eq"></a>  regex_iterator::operator=

Compara iteradores para buscar igualdad.

```cpp
bool operator==(const regex_iterator& right);
```

### <a name="parameters"></a>Parámetros

\ *derecha*
Iterador con el que se compara.

### <a name="remarks"></a>Comentarios

La función miembro devuelve true si `*this` y *right* son iteradores de final de secuencia o si ninguno es un iterador de final de secuencia y `begin == right.begin`, `end == right.end`, `pregex == right.pregex` y `flags == right.flags`. De lo contrario, devuelve false.

## <a name="op_arrow"></a>  regex_iterator::operator-&gt;

Tiene acceso a la coincidencia designada.

```cpp
const match_results<BidIt> * operator->();
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve la dirección del valor almacenado `match`.

## <a name="pointer"></a>  regex_iterator::pointer

El tipo de un puntero a una coincidencia.

```cpp
typedef match_results<BidIt> *pointer;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de `match_results<BidIt>*`, donde `BidIt` es el parámetro de plantilla.

## <a name="reference"></a>  regex_iterator::reference

El tipo de una referencia a una coincidencia.

```cpp
typedef match_results<BidIt>& reference;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de `match_results<BidIt>&`, donde `BidIt` es el parámetro de plantilla.

## <a name="regex_iterator"></a>  regex_iterator::regex_iterator

Construye el iterador.

```cpp
regex_iterator();

regex_iterator(BidIt first,
    BidIt last,
    const regex_type& re,
    regex_constants::match_flag_type f = regex_constants::match_default);
```

### <a name="parameters"></a>Parámetros

*primer* \
Principio de la secuencia que debe coincidir.

*última* \
Final de la secuencia que debe coincidir.

*\*
Expresión regular para las coincidencias.

\ *f*
Marcadores para coincidencias.

### <a name="remarks"></a>Comentarios

El primer constructor crea un iterador de final de secuencia. El segundo constructor inicializa el valor almacenado `begin` con *First*, el valor almacenado `end` con *Last*, el valor almacenado `pregex` con `&re` y el valor almacenado `flags` con *f*. A continuación, llama a `regex_search(begin, end, match, *pregex, flags)`. Si se produce un error en la búsqueda, el constructor establece el objeto en un iterador de final de secuencia.

## <a name="regex_type"></a>  regex_iterator::regex_type

El tipo de expresión regular que debe coincidir.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>Comentarios

La definición de tipo es un sinónimo de `basic_regex<Elem, RXtraits>`.

## <a name="value_type"></a>  regex_iterator::value_type

Tipo de una coincidencia.

```cpp
typedef match_results<BidIt> value_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de `match_results<BidIt>`, donde `BidIt` es el parámetro de plantilla.

## <a name="see-also"></a>Vea también

[\<regex>](../standard-library/regex.md)\
\ de la [clase regex_constants](../standard-library/regex-constants-class.md)
\ de la [clase regex_error](../standard-library/regex-error-class.md)
[\<regex > funciones](../standard-library/regex-functions.md) \
\ de la [clase regex_iterator](../standard-library/regex-iterator-class.md)
[operadores de > de \<regex](../standard-library/regex-operators.md) \
\ de la [clase regex_token_iterator](../standard-library/regex-token-iterator-class.md)
\ de la [clase regex_traits](../standard-library/regex-traits-class.md)
[Definiciones de tipo \<regex>](../standard-library/regex-typedefs.md)
