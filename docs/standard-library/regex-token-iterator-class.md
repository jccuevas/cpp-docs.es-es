---
title: regex_token_iterator (Clase)
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_token_iterator
- regex/std::regex_token_iterator::regex_type
- regex/std::regex_token_iterator::value_type
- regex/std::regex_token_iterator::iterator_category
- regex/std::regex_token_iterator::difference_type
- regex/std::regex_token_iterator::pointer
- regex/std::regex_token_iterator::reference
- regex/std::regex_token_iterator::operator==
- regex/std::regex_token_iterator::operator!=
- regex/std::regex_token_iterator::operator*
- regex/std::regex_token_iterator::operator->
- regex/std::regex_token_iterator::operator++
helpviewer_keywords:
- std::regex_token_iterator [C++]
- std::regex_token_iterator [C++], regex_type
- std::regex_token_iterator [C++], value_type
- std::regex_token_iterator [C++], iterator_category
- std::regex_token_iterator [C++], difference_type
- std::regex_token_iterator [C++], pointer
- std::regex_token_iterator [C++], reference
ms.assetid: a213ba48-8e4e-4b6b-871a-2637acf05f15
ms.openlocfilehash: 5ada2ad69cbcac15e09968045e54095dfb2623d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366399"
---
# <a name="regex_token_iterator-class"></a>regex_token_iterator (Clase)

Clase de iterador para subcoincidencias.

## <a name="syntax"></a>Sintaxis

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_token_iterator
```

## <a name="parameters"></a>Parámetros

*BidIt*\
El tipo de iterador para subcoincidencias.

*Elem*\
Tipo de los elementos que debe coincidir.

*RXtraits*\
Clase Traits para los elementos.

## <a name="remarks"></a>Observaciones

La plantilla de clase describe un objeto de iterador de avance constante. Conceptualmente, contiene un objeto `regex_iterator` que usa para buscar coincidencias de expresiones regulares en una secuencia de caracteres. Extrae objetos del tipo `sub_match<BidIt>` que representan las subcoincidencias identificadas por los valores de índice en el vector almacenado `subs` para cada coincidencia de expresión regular.

Un valor de índice de -1 señala la secuencia de caracteres que empieza inmediatamente después del final de la coincidencia de expresión regular anterior (o comienza al principio de la secuencia de caracteres si no había ninguna coincidencia de expresión regular anterior) y que se extiende, aunque sin incluirlo, al primer carácter de la coincidencia de expresión regular actual o hasta el final de la secuencia de caracteres si no hay una coincidencia actual. Cualquier otro valor de índice `idx` señala el contenido del grupo de capturas incluido en `it.match[idx]`.

### <a name="members"></a>Miembros

|Member|Valor predeterminado|
|-|-|
|`private regex_iterator<BidIt, Elem, RXtraits> it`||
|`private vector<int> subs`||
|`private int pos`||

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[regex_token_iterator](#regex_token_iterator)|Construye el iterador.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[difference_type](#difference_type)|El tipo de diferencia de un iterador.|
|[iterator_category](#iterator_category)|Tipo de la categoría del iterador.|
|[puntero](#pointer)|El tipo de un puntero a una coincidencia.|
|[Referencia](#reference)|El tipo de una referencia a una subcoincidencia.|
|[regex_type](#regex_type)|El tipo de expresión regular que debe coincidir.|
|[value_type](#value_type)|El tipo de una subcoincidencia.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[¡Operador!](#op_neq)|Compara iteradores para buscar desigualdad.|
|[operador*](#op_star)|Tiene acceso a la subcoincidencia designada.|
|[operador++](#op_add_add)|Incrementa el iterador almacenado.|
|[operadora](#op_eq_eq)|Compara iteradores para buscar igualdad.|
|[>operador](#op_arrow)|Tiene acceso a la subcoincidencia designada.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<regex>

**Espacio de nombres:** std

## <a name="example"></a>Ejemplo

```cpp
#include <regex>
#include <iostream>

typedef std::regex_token_iterator<const char *> Myiter;
int main()
    {
    const char *pat = "aaxaayaaz";
    Myiter::regex_type rx("(a)a");
    Myiter next(pat, pat + strlen(pat), rx);
    Myiter end;

// show whole match
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefix before match
    next = Myiter(pat, pat + strlen(pat), rx, -1);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show (a) submatch only
    next = Myiter(pat, pat + strlen(pat), rx, 1);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefixes and submatches
    std::vector<int> vec;
    vec.push_back(-1);
    vec.push_back(1);
    next = Myiter(pat, pat + strlen(pat), rx, vec);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefixes and whole matches
    int arr[] = {-1, 0};
    next = Myiter(pat, pat + strlen(pat), rx, arr);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

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
match == aa
match == aa
match == aa

match ==
match == x
match == y
match == z

match == a
match == a
match == a

match ==
match == a
match == x
match == a
match == y
match == a
match == z

match ==
match == aa
match == x
match == aa
match == y
match == aa
match == z
```

## <a name="regex_token_iteratordifference_type"></a><a name="difference_type"></a>regex_token_iterator::difference_type

El tipo de diferencia de un iterador.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de `std::ptrdiff_t`.

## <a name="regex_token_iteratoriterator_category"></a><a name="iterator_category"></a>regex_token_iterator::iterator_category

Tipo de la categoría del iterador.

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de `std::forward_iterator_tag`.

## <a name="regex_token_iteratoroperator"></a><a name="op_neq"></a>regex_token_iterator::operador!

Compara iteradores para buscar desigualdad.

```cpp
bool operator!=(const regex_token_iterator& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Iterador con el que se compara.

### <a name="remarks"></a>Observaciones

La función miembro devuelve `!(*this == right)`.

## <a name="regex_token_iteratoroperator"></a><a name="op_star"></a>regex_token_iterator::operador*

Tiene acceso a la subcoincidencia designada.

```cpp
const sub_match<BidIt>& operator*();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un objeto `sub_match<BidIt>` que representa el grupo de capturas identificado por el valor de índice `subs[pos]`.

## <a name="regex_token_iteratoroperator"></a><a name="op_add_add"></a>regex_token_iterator::operador++

Incrementa el iterador almacenado.

```cpp
regex_token_iterator& operator++();

regex_token_iterator& operator++(int);
```

### <a name="remarks"></a>Observaciones

Si el iterador almacenado `it` es un iterador de final de secuencia, el primer operador establece el valor almacenado `pos` en el valor de `subs.size()` (lo que lo convierte en un iterador de fin de secuencia). En caso contrario, el operador incrementa el valor almacenado `pos`; si el resultado es igual al valor `subs.size()`, establece el valor almacenado `pos` en cero e incrementa el iterador almacenado `it`. Si al incrementar el iterador almacenado no queda igual que un iterador de final de secuencia, el operador no hace nada más. De lo contrario, si el final de la coincidencia precedente no estaba al final de la secuencia de caracteres, el operador establece el valor almacenado de `pos` en `subs.size()`. De lo contrario, el operador incrementa repetidamente el valor almacenado `pos` hasta `pos == subs.size()` o `subs[pos] == -1` (lo que garantiza que la siguiente desreferencia del iterador devolverá el final de la secuencia de caracteres si uno de los valores de índice es -1). En todos los casos, el operador devuelve el objeto.

El segundo operador realiza una copia del objeto, incrementa el objeto y devuelve la copia.

## <a name="regex_token_iteratoroperator"></a><a name="op_eq_eq"></a>regex_token_iterator::operador

Compara iteradores para buscar igualdad.

```cpp
bool operator==(const regex_token_iterator& right);
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Iterador con el que se compara.

### <a name="remarks"></a>Observaciones

La función miembro devuelve `it == right.it && subs == right.subs && pos == right.pos`.

## <a name="regex_token_iteratoroperator-gt"></a><a name="op_arrow"></a>regex_token_iterator::operador-&gt;

Tiene acceso a la subcoincidencia designada.

```cpp
const sub_match<BidIt> * operator->();
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve un puntero al objeto `sub_match<BidIt>` que representa el grupo de capturas identificado por el valor de índice `subs[pos]`.

## <a name="regex_token_iteratorpointer"></a><a name="pointer"></a>regex_token_iterator::pointer

El tipo de un puntero a una coincidencia.

```cpp
typedef sub_match<BidIt> *pointer;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de `sub_match<BidIt>*`, donde `BidIt` es el parámetro de plantilla.

## <a name="regex_token_iteratorreference"></a><a name="reference"></a>regex_token_iterator::referencia

El tipo de una referencia a una subcoincidencia.

```cpp
typedef sub_match<BidIt>& reference;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de `sub_match<BidIt>&`, donde `BidIt` es el parámetro de plantilla.

## <a name="regex_token_iteratorregex_token_iterator"></a><a name="regex_token_iterator"></a>regex_token_iterator::regex_token_iterator

Construye el iterador.

```cpp
regex_token_iterator();

regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, int submatch = 0,
    regex_constants::match_flag_type f = regex_constants::match_default);

regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, const vector<int> submatches,
    regex_constants::match_flag_type f = regex_constants::match_default);

template <std::size_t N>
regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, const int (&submatches)[N],
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

El primer constructor crea un iterador de final de secuencia.

El segundo constructor crea un objeto cuyo iterador almacenado `it` se inicializa en `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, cuyo vector almacenado `subs` contiene exactamente un número entero, con el valor `submatch`, y cuyo valor almacenado `pos` es cero. Nota: el objeto resultante extrae la subcoincidencia identificada por el valor de índice `submatch` por cada coincidencia de expresión regular correcta.

El tercer constructor crea un objeto cuyo iterador almacenado `it` se inicializa en `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, cuyo vector almacenado `subs` contiene una copia del argumento `submatches`de constructor y cuyo valor almacenado `pos` es cero.

El cuarto constructor crea un objeto cuyo iterador almacenado `it` se inicializa en `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, cuyo vector almacenado `subs` contiene los valores de `N` señalados por el argumento `submatches`de constructor y cuyo valor almacenado `pos` es cero.

## <a name="regex_token_iteratorregex_type"></a><a name="regex_type"></a>regex_token_iterator::regex_type

El tipo de expresión regular que debe coincidir.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>Observaciones

La definición de tipo es un sinónimo de `basic_regex<Elem, RXtraits>`.

## <a name="regex_token_iteratorvalue_type"></a><a name="value_type"></a>regex_token_iterator::value_type

El tipo de una subcoincidencia.

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de `sub_match<BidIt>`, donde `BidIt` es el parámetro de plantilla.

## <a name="see-also"></a>Consulte también

[\<regex>](../standard-library/regex.md)\
[Clase regex_constants](../standard-library/regex-constants-class.md)\
[Clase regex_error](../standard-library/regex-error-class.md)\
[\<funciones de> regex](../standard-library/regex-functions.md)\
[Clase regex_iterator](../standard-library/regex-iterator-class.md)\
[\<operadores de> regex](../standard-library/regex-operators.md)\
[Clase regex_traits](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)
