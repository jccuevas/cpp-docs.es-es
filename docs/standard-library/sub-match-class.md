---
title: sub_match (Clase)
ms.date: 09/10/2018
f1_keywords:
- regex/std::sub_match
- regex/std::sub_match::matched
- regex/std::sub_match::compare
- regex/std::sub_match::length
- regex/std::sub_match::str
- regex/std::sub_match::difference_type
- regex/std::sub_match::iterator
- regex/std::sub_match::value_type
helpviewer_keywords:
- std::sub_match [C++]
- std::sub_match [C++], matched
- std::sub_match [C++], compare
- std::sub_match [C++], length
- std::sub_match [C++], str
- std::sub_match [C++], difference_type
- std::sub_match [C++], iterator
- std::sub_match [C++], value_type
ms.assetid: 804e2b9e-d16a-4c4c-ac60-024e0b2dd0e8
ms.openlocfilehash: 460f79fe0f23643fafcebb64aecf2988bdb0debe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376581"
---
# <a name="sub_match-class"></a>sub_match (Clase)

Describe a una subcoincidencia.

## <a name="syntax"></a>Sintaxis

```cpp
template <class BidIt>
class sub_match
    : public std::pair<BidIt, BidIt>
```

## <a name="parameters"></a>Parámetros

*BidIt*\
El tipo de iterador para subcoincidencias.

## <a name="remarks"></a>Observaciones

La plantilla de clase describe un objeto que designa una secuencia de caracteres que coincide con un grupo de captura en una llamada a [regex_match](../standard-library/regex-functions.md#regex_match) o para [regex_search](../standard-library/regex-functions.md#regex_search). Los objetos del tipo [match_results (clase)](../standard-library/match-results-class.md) contienen una matriz de estos objetos, uno para cada grupo de capturas en la expresión regular usada en la búsqueda.

Si no hay coincidencia con el grupo de capturas, el miembro de datos `matched` del objeto se considera false y los dos iteradores `first` y `second` (heredados de la base `std::pair`) son iguales. Si hay coincidencia con el grupo de capturas, `matched` es true, el iterador `first` apunta al primer carácter de la secuencia de destino que coincide con el grupo de capturas y el iterador `second` apunta a una posición más allá del último carácter de la secuencia de destino que coincide con el grupo de capturas. Observe que para una coincidencia de longitud cero, el miembro `matched` es true, los dos iteradores son iguales y ambos apuntan a la posición de la coincidencia.

Una coincidencia de longitud cero puede aparecer cuando un grupo de capturas solo se compone de una aserción o de una repetición que permite que se repita cero. Por ejemplo:

"^" coincide con la secuencia "a" de destino; el objeto `sub_match` correspondiente al grupo de capturas 0 contiene iteradores que apuntan al primer carácter de la secuencia.

"b(a*)b" coincide con la secuencia "bb" de destino; el objeto `sub_match` correspondiente al grupo de capturas 1 contiene iteradores que apuntan al segundo carácter de la secuencia.

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[difference_type](#difference_type)|El tipo de diferencia de un iterador.|
|[Iterador](#iterator)|Tipo de un iterador.|
|[value_type](#value_type)|El tipo de un elemento.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Comparar](#compare)|Comparar la subcoincidencia con una secuencia.|
|[length](#length)|Devuelve la longitud de una subcoincidencia.|
|[Emparejado](#matched)|Indica si la coincidencia se realizó correctamente.|
|[Str](#str)|Convierte la subcoincidencia a una cadena.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[value_type><value_type basic_string operador](#op_basic_string_lt_value_type_gt)|Convierte la subcoincidencia en una cadena.|

## <a name="example"></a>Ejemplo

```cpp
// std__regex__sub_match.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "matched == " << std::boolalpha
        << sub.matched << std::endl;
    std::cout << "length == " << sub.length() << std::endl;

    std::csub_match::difference_type dif = std::distance(sub.first, sub.second);
    std::cout << "difference == " << dif << std::endl;

    std::csub_match::iterator first = sub.first;
    std::csub_match::iterator last = sub.second;
    std::cout << "range == " << std::string(first, last)
        << std::endl;
    std::cout << "string == " << sub << std::endl;

    std::csub_match::value_type const *ptr = "aab";
    std::cout << "compare(\"aab\") == "
        << sub.compare(ptr) << std::endl;
    std::cout << "compare(string) == "
        << sub.compare(std::string("AAA")) << std::endl;
    std::cout << "compare(sub) == "
        << sub.compare(sub) << std::endl;

    return (0);
    }
```

```Output
matched == true
length == 3
difference == 3
range == aaa
string == aaa
compare("aab") == -1
compare(string) == 1
compare(sub) == 0
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<regex>

**Espacio de nombres:** std

## <a name="sub_matchcompare"></a><a name="compare"></a>sub_match::comparar

Comparar la subcoincidencia con una secuencia.

```cpp
int compare(const sub_match& right) const;
int compare(const basic_string<value_type>& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Subcoincidencia con la que se va comparar.

*Str*\
Cadena con la que se va a comparar.

*Ptr*\
La secuencia terminada en un valor nulo con la que se va a comparar.

### <a name="remarks"></a>Observaciones

La primera función miembro compara la secuencia coincidente `[first, second)` con la secuencia coincidente `[right.first, right.second)`. La segunda función miembro compara la secuencia coincidente `[first, second)` con la secuencia de caracteres `[right.begin(), right.end())`. La tercera función miembro compara la secuencia coincidente `[first, second)` con la secuencia de caracteres `[right, right + std::char_traits<value_type>::length(right))`.

Cada función devuelve lo siguiente:

un valor negativo si el primer valor diferente de la secuencia coincidente se es menor que el elemento correspondiente de la secuencia de operandos (según lo determinado por `std::char_traits<value_type>::compare`), o si los dos tienen un prefijo común pero la secuencia de destino es más larga

cero si los dos son iguales elemento a elemento y tienen la misma longitud

un valor positivo en caso contrario

## <a name="sub_matchdifference_type"></a><a name="difference_type"></a>sub_match::difference_type

El tipo de diferencia de un iterador.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Observaciones

La definición de tipo es un sinónimo de `iterator_traits<BidIt>::difference_type`.

## <a name="sub_matchiterator"></a><a name="iterator"></a>sub_match::iterator

Tipo de un iterador.

```cpp
typedef BidIt iterator;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del argumento de tipo de plantilla `Bidit`.

## <a name="sub_matchlength"></a><a name="length"></a>sub_match::longitud

Devuelve la longitud de una subcoincidencia.

```cpp
difference_type length() const;
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve la longitud de la secuencia coincidente, o cero si no se ha producido ninguna secuencia coincidente.

## <a name="sub_matchmatched"></a><a name="matched"></a>sub_match::matched

Indica si la coincidencia se realizó correctamente.

```cpp
bool matched;
```

### <a name="remarks"></a>Observaciones

El miembro solo es **true** si `*this` el grupo de captura asociado formaba parte de la coincidencia de expresiones regulares.

## <a name="sub_matchoperator-basic_stringltvalue_typegt"></a><a name="op_basic_string_lt_value_type_gt"></a>sub_match::operador&lt;basic_string value_type&gt;

Convierte la subcoincidencia en una cadena.

```cpp
operator basic_string<value_type>() const;
```

### <a name="remarks"></a>Observaciones

El operador miembro devuelve `str()`.

## <a name="sub_matchstr"></a><a name="str"></a>sub_match::str

Convierte la subcoincidencia a una cadena.

```cpp
basic_string<value_type> str() const;
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve `basic_string<value_type>(first, second)`.

## <a name="sub_matchvalue_type"></a><a name="value_type"></a>sub_match::value_type

El tipo de un elemento.

```cpp
typedef typename iterator_traits<BidIt>::value_type value_type;
```

### <a name="remarks"></a>Observaciones

La definición de tipo es un sinónimo de `iterator_traits<BidIt>::value_type`.

## <a name="see-also"></a>Consulte también

[\<regex>](../standard-library/regex.md)\
[sub_match](../standard-library/sub-match-class.md)
