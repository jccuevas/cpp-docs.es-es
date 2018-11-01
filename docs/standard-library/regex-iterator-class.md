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
ms.openlocfilehash: 937c217cdef6895aaa3adb1499f1fde8f67fd513
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482633"
---
# <a name="regexiterator-class"></a>regex_iterator (Clase)

Clase de iterador para las coincidencias.

## <a name="syntax"></a>Sintaxis

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_iterator
```

## <a name="parameters"></a>Parámetros

*BidIt*<br/>
El tipo de iterador para subcoincidencias.

*Elem*<br/>
Tipo de los elementos que debe coincidir.

*RXtraits*<br/>
Clase Traits para los elementos.

## <a name="remarks"></a>Comentarios

La clase de plantilla describe un objeto constante de iterador hacia delante. Extrae objetos de tipo `match_results<BidIt>` aplicando varias veces su propio objeto de expresión regular `*pregex` a la secuencia de caracteres definida por el rango de iterador `[begin, end)`.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[regex_iterator](#regex_iterator)|Construye el iterador.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[difference_type](#difference_type)|El tipo de diferencia de un iterador.|
|[iterator_category](#iterator_category)|Tipo de la categoría del iterador.|
|[pointer](#pointer)|El tipo de un puntero a una coincidencia.|
|[reference](#reference)|El tipo de una referencia a una coincidencia.|
|[regex_type](#regex_type)|El tipo de expresión regular que debe coincidir.|
|[value_type](#value_type)|Tipo de una coincidencia.|

### <a name="operators"></a>Operadores

|Operador|Descripción|
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

*right*<br/>
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

*right*<br/>
Iterador con el que se compara.

### <a name="remarks"></a>Comentarios

La función miembro devuelve true si `*this` y *derecho* son iteradores de final de secuencia o si ninguno es un iterador de final de secuencia y `begin == right.begin`, `end == right.end`, `pregex == right.pregex`, y `flags == right.flags`. De lo contrario, devuelve false.

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

*first*<br/>
Principio de la secuencia que debe coincidir.

*Último*<br/>
Final de la secuencia que debe coincidir.

*Re*<br/>
Expresión regular para las coincidencias.

*f*<br/>
Marcadores para coincidencias.

### <a name="remarks"></a>Comentarios

El primer constructor crea un iterador de final de secuencia. El segundo constructor inicializa el valor almacenado `begin` con *primera*, el valor almacenado `end` con *última*, el valor almacenado `pregex` con `&re`y el valor almacenado `flags` con *f*. A continuación, llama a `regex_search(begin, end, match, *pregex, flags)`. Si se produce un error en la búsqueda, el constructor establece el objeto en un iterador de final de secuencia.

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

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants (Clase)](../standard-library/regex-constants-class.md)<br/>
[regex_error (Clase)](../standard-library/regex-error-class.md)<br/>
[Funciones de \<regex>](../standard-library/regex-functions.md)<br/>
[regex_iterator (Clase)](../standard-library/regex-iterator-class.md)<br/>
[Operadores de \<regex>](../standard-library/regex-operators.md)<br/>
[regex_token_iterator (Clase)](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits (Clase)](../standard-library/regex-traits-class.md)<br/>
[Definiciones de tipo \<regex>](../standard-library/regex-typedefs.md)<br/>
