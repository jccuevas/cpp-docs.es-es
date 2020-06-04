---
title: regex_traits (Clase)
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_traits
- regex/std::regex_traits::char_type
- regex/std::regex_traits::size_type
- regex/std::regex_traits::string_type
- regex/std::regex_traits::locale_type
- regex/std::regex_traits::char_class_type
- regex/std::regex_traits::length
- regex/std::regex_traits::translate
- regex/std::regex_traits::translate_nocase
- regex/std::regex_traits::transform
- regex/std::regex_traits::transform_primary
- regex/std::regex_traits::lookup_classname
- regex/std::regex_traits::lookup_collatename
- regex/std::regex_traits::isctype
- regex/std::regex_traits::value
- regex/std::regex_traits::imbue
- regex/std::regex_traits::getloc
helpviewer_keywords:
- std::regex_traits [C++]
- std::regex_traits [C++], char_type
- std::regex_traits [C++], size_type
- std::regex_traits [C++], string_type
- std::regex_traits [C++], locale_type
- std::regex_traits [C++], char_class_type
- std::regex_traits [C++], length
- std::regex_traits [C++], translate
- std::regex_traits [C++], translate_nocase
- std::regex_traits [C++], transform
- std::regex_traits [C++], transform_primary
- std::regex_traits [C++], lookup_classname
- std::regex_traits [C++], lookup_collatename
- std::regex_traits [C++], isctype
- std::regex_traits [C++], value
- std::regex_traits [C++], imbue
- std::regex_traits [C++], getloc
ms.assetid: bc5a5eed-32fc-4eb7-913d-71c42e729e81
ms.openlocfilehash: 8879336c48d0fec8a20411abf1c07d570a1575e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366388"
---
# <a name="regex_traits-class"></a>regex_traits (Clase)

Describe las características de los elementos para buscar coincidencias.

## <a name="syntax"></a>Sintaxis

```cpp
template<class Elem>
class regex_traits
```

## <a name="parameters"></a>Parámetros

*Elem*\
El tipo de elemento de carácter que se va describir.

## <a name="remarks"></a>Observaciones

La plantilla de clase describe varios rasgos de expresión regular para el tipo *Elem*. La plantilla de clase [basic_regex Class](../standard-library/basic-regex-class.md) utiliza esta información para manipular elementos de tipo *Elem*.

Cada objeto `regex_traits` contiene un objeto de tipo `regex_traits::locale` que usan algunas de sus funciones miembro. La configuración regional predeterminada es una copia de `regex_traits::locale()`. La función miembro `imbue` reemplaza el objeto de configuración regional, y la función miembro `getloc` devuelve una copia del objeto de configuración regional.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[regex_traits](#regex_traits)|Construye el objeto.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[char_class_type](#char_class_type)|El tipo de designador de clases de caracteres.|
|[char_type](#char_type)|El tipo de un elemento.|
|[locale_type](#locale_type)|El tipo de objeto de configuración regional almacenado.|
|[size_type](#size_type)|Tipo de una longitud de secuencia.|
|[string_type](#string_type)|Tipo de una cadena de elementos.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[getloc](#getloc)|Devuelve el objeto de configuración regional almacenado.|
|[imbue](#imbue)|Modifica el objeto de configuración regional almacenado.|
|[isctype](#isctype)|Realiza pruebas de pertenencia a una clase.|
|[length](#length)|Devuelve la longitud de una secuencia terminada en null.|
|[lookup_classname](#lookup_classname)|Asigna una secuencia a una clase de caracteres.|
|[lookup_collatename](#lookup_collatename)|Asigna una secuencia a un elemento de intercalación.|
|[Transformar](#transform)|Convierte a la secuencia ordenada equivalente.|
|[transform_primary](#transform_primary)|Convierte a la secuencia ordenada caseless equivalente.|
|[Traducir](#translate)|Convierte a un elemento coincidente equivalente.|
|[translate_nocase](#translate_nocase)|Convierte al elemento equivalente que coincide sin distinción entre mayúsculas y minúsculas.|
|[value](#value)|Convierte un elemento en un valor de dígito.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<regex>

**Espacio de nombres:** std

## <a name="example"></a>Ejemplo

```cpp
// std__regex__regex_traits.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::regex_traits<char> Mytr;
int main()
    {
    Mytr tr;

    Mytr::char_type ch = tr.translate('a');
    std::cout << "translate('a') == 'a' == " << std::boolalpha
        << (ch == 'a') << std::endl;

    std::cout << "nocase 'a' == 'A' == " << std::boolalpha
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))
        << std::endl;

    const char *lbegin = "abc";
    const char *lend = lbegin + strlen(lbegin);
    Mytr::size_type size = tr.length(lbegin);
    std::cout << "length(\"abc\") == " << size <<std::endl;

    Mytr::string_type str = tr.transform(lbegin, lend);
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha
        << (str < "abc") << std::endl;

    const char *ubegin = "ABC";
    const char *uend = ubegin + strlen(ubegin);
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha
        << (tr.transform_primary(ubegin, uend) <
            tr.transform_primary(lbegin, lend))
        << std::endl;

    const char *dig = "digit";
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);
    std::cout << "class digit == d == " << std::boolalpha
        << (cl == tr.lookup_classname(dig, dig + 1))
        << std::endl;

    std::cout << "'3' is digit == " <<std::boolalpha
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))
        << std::endl;

    std::cout << "hex C == " << tr.value('C', 16) << std::endl;

// other members
    str = tr.lookup_collatename(dig, dig + 5);

    Mytr::locale_type loc = tr.getloc();
    tr.imbue(loc);

    return (0);
    }
```

```Output
translate('a') == 'a' == true
nocase 'a' == 'A' == true
length("abc") == 3
transform("abc") < "abc" == false
primary "ABC" < "abc" == false
class digit == d == true
'3' is digit == true
hex C == 12
```

## <a name="regex_traitschar_class_type"></a><a name="char_class_type"></a>regex_traits::char_class_type

El tipo de designador de clases de caracteres.

```cpp
typedef T8 char_class_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de un tipo no especificado que designa clases de caracteres. Se pueden combinar los valores de este tipo mediante el operador `|` para designar clases de caracteres que constituyen la unión de las clases designadas por los operandos.

## <a name="regex_traitschar_type"></a><a name="char_type"></a>regex_traits::char_type

El tipo de un elemento.

```cpp
typedef Elem char_type;
```

### <a name="remarks"></a>Observaciones

La definición de tipo es un sinónimo del argumento de plantilla `Elem`.

## <a name="regex_traitsgetloc"></a><a name="getloc"></a>regex_traits::getloc

Devuelve el objeto de configuración regional almacenado.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve el objeto `locale` almacenado.

## <a name="regex_traitsimbue"></a><a name="imbue"></a>regex_traits::imbue

Modifica el objeto de configuración regional almacenado.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Parámetros

*Loc*\
El objeto de configuración regional que se va a almacenar.

### <a name="remarks"></a>Observaciones

La función miembro copia `locale` *loc* en el objeto almacenado y `locale` devuelve una copia del valor anterior del objeto almacenado.

## <a name="regex_traitsisctype"></a><a name="isctype"></a>regex_traits::isctype

Realiza pruebas de pertenencia a una clase.

```cpp
bool isctype(char_type ch, char_class_type cls) const;
```

### <a name="parameters"></a>Parámetros

*Ch*\
Elemento que se va a comprobar.

*Cls*\
Las clases que se van a probar.

### <a name="remarks"></a>Observaciones

La función miembro devuelve true solo si el carácter *ch* está en la clase de caracteres designada por *cls*.

## <a name="regex_traitslength"></a><a name="length"></a>regex_traits::longitud

Devuelve la longitud de una secuencia terminada en null.

```cpp
static size_type length(const char_type *str);
```

### <a name="parameters"></a>Parámetros

*Str*\
La secuencia terminada en null.

### <a name="remarks"></a>Observaciones

La función miembro estática devuelve `std::char_traits<char_type>::length(str)`.

## <a name="regex_traitslocale_type"></a><a name="locale_type"></a>regex_traits::locale_type

El tipo de objeto de configuración regional almacenado.

```cpp
typedef T7 locale_type;
```

### <a name="remarks"></a>Observaciones

La definición de tipo es un sinónimo de un tipo que encapsula las configuraciones regionales. En las especializaciones `regex_traits<char>` y `regex_traits<wchar_t>` es un sinónimo de `std::locale`.

## <a name="regex_traitslookup_classname"></a><a name="lookup_classname"></a>regex_traits::lookup_classname

Asigna una secuencia a una clase de caracteres.

```cpp
template <class FwdIt>
char_class_type lookup_classname(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Principio de la secuencia que se va a buscar.

*Última*\
Final de la secuencia que se va a buscar.

### <a name="remarks"></a>Observaciones

La función miembro devuelve un valor que designa la clase de caracteres denominada por la secuencia de caracteres a la que señalan sus argumentos. El valor es independiente de mayúsculas o minúsculas en los caracteres de la secuencia.

La especialización `regex_traits<char>` reconoce los nombres `"d"`, `"s"`, `"w"`, `"alnum"`, `"alpha"`, `"blank"`, `"cntrl"`, `"digit"`, `"graph"`, `"lower"`, `"print"`, `"punct"`, `"space"`, `"upper"` y `"xdigit"` sin tener en cuenta mayúsculas o minúsculas.

La especialización `regex_traits<wchar_t>` reconoce los nombres `L"d"`, `L"s"`, `L"w"`, `L"alnum"`, `L"alpha"`, `L"blank"`, `L"cntrl"`, `L"digit"`, `L"graph"`, `L"lower"`, `L"print"`, `L"punct"`, `L"space"`, `L"upper"` y `L"xdigit"` sin tener en cuenta mayúsculas o minúsculas.

## <a name="regex_traitslookup_collatename"></a><a name="lookup_collatename"></a>regex_traits::lookup_collatename

Asigna una secuencia a un elemento de intercalación.

```cpp
template <class FwdIt>
string_type lookup_collatename(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Principio de la secuencia que se va a buscar.

*Última*\
Final de la secuencia que se va a buscar.

### <a name="remarks"></a>Observaciones

La función miembro devuelve un objeto de cadena que contiene el elemento de intercalación correspondiente a la secuencia de `[first, last)`o una cadena vacía si la secuencia no es un elemento de intercalación válido.

## <a name="regex_traitsregex_traits"></a><a name="regex_traits"></a>regex_traits::regex_traits

Construye el objeto.

```cpp
regex_traits();
```

### <a name="remarks"></a>Observaciones

El constructor crea un objeto cuyo objeto `locale` almacenado se inicializa en la configuración regional predeterminada.

## <a name="regex_traitssize_type"></a><a name="size_type"></a>regex_traits::size_type

Tipo de una longitud de secuencia.

```cpp
typedef T6 size_type;
```

### <a name="remarks"></a>Observaciones

La definición de tipo es un sinónimo para un tipo entero sin signo. En las especializaciones `regex_traits<char>` y `regex_traits<wchar_t>` es un sinónimo de `std::size_t`.

La definición de tipo es un sinónimo de `std::size_t`.

## <a name="regex_traitsstring_type"></a><a name="string_type"></a>regex_traits::string_type

Tipo de una cadena de elementos.

```cpp
typedef basic_string<Elem> string_type;
```

### <a name="remarks"></a>Observaciones

La definición de tipo es un sinónimo de `basic_string<Elem>`.

## <a name="regex_traitstransform"></a><a name="transform"></a>regex_traits::transformar

Convierte a la secuencia ordenada equivalente.

```cpp
template <class FwdIt>
string_type transform(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Principio de la secuencia que se va a transformar.

*Última*\
Final de la secuencia que se va a transformar.

### <a name="remarks"></a>Observaciones

La función miembro devuelve una cadena que dicha función genera mediante una regla de transformación que depende del objeto `locale` almacenado. En el caso de dos secuencias de caracteres designadas por los rangos de iterador `[first1, last1)` y `[first2, last2)`, `transform(first1, last1) < transform(first2, last2)` si la secuencia de caracteres designada por el rango de iterador `[first1, last1)` se ordena antes que la secuencia de caracteres designada por el rango de iterador `[first2, last2)`.

## <a name="regex_traitstransform_primary"></a><a name="transform_primary"></a>regex_traits::transform_primary

Convierte a la secuencia ordenada caseless equivalente.

```cpp
template <class FwdIt>
string_type transform_primary(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parámetros

*Primero*\
Principio de la secuencia que se va a transformar.

*Última*\
Final de la secuencia que se va a transformar.

### <a name="remarks"></a>Observaciones

La función miembro devuelve una cadena que dicha función genera mediante una regla de transformación que depende del objeto `locale` almacenado. En el caso de dos secuencias de caracteres designadas por los rangos de iterador `[first1, last1)` y `[first2, last2)`, `transform_primary(first1, last1) < transform_primary(first2, last2)` si la secuencia de caracteres designada por el rango de iterador `[first1, last1)` se ordena antes que la secuencia de caracteres designada por el rango de iterador `[first2, last2)` sin tener en cuenta mayúsculas y minúsculas o acentos.

## <a name="regex_traitstranslate"></a><a name="translate"></a>regex_traits::traducir

Convierte a un elemento coincidente equivalente.

```cpp
char_type translate(char_type ch) const;
```

### <a name="parameters"></a>Parámetros

*Ch*\
El elemento que se va a convertir.

### <a name="remarks"></a>Observaciones

La función miembro devuelve un carácter que dicha función genera mediante una regla de transformación que depende del objeto `locale` almacenado. Para dos objetos `char_type` y `ch1` de `ch2`, `translate(ch1) == translate(ch2)` solo si `ch1` y `ch2` deben coincidir cuando uno aparece en la definición de la expresión regular y el otro en la posición correspondiente de la secuencia de destino para una coincidencia que depende de la configuración regional.

## <a name="regex_traitstranslate_nocase"></a><a name="translate_nocase"></a>regex_traits::translate_nocase

Convierte al elemento equivalente que coincide sin distinción entre mayúsculas y minúsculas.

```cpp
char_type translate_nocase(char_type ch) const;
```

### <a name="parameters"></a>Parámetros

*Ch*\
El elemento que se va a convertir.

### <a name="remarks"></a>Observaciones

La función miembro devuelve un carácter que dicha función genera mediante una regla de transformación que depende del objeto `locale` almacenado. Para dos objetos `char_type` y `ch1` de `ch2`, `translate_nocase(ch1) == translate_nocase(ch2)` solo si `ch1` y `ch2` deben coincidir cuando uno aparece en la definición de la expresión regular y el otro en la posición correspondiente de la secuencia de destino para una coincidencia que no distingue entre mayúsculas y minúsculas.

## <a name="regex_traitsvalue"></a><a name="value"></a>regex_traits::valor

Convierte un elemento en un valor de dígito.

```cpp
int value(Elem ch, int radix) const;
```

### <a name="parameters"></a>Parámetros

*Ch*\
El elemento que se va a convertir.

*Radix*\
Las operaciones aritméticas base que se van a usar.

### <a name="remarks"></a>Observaciones

La función miembro devuelve el valor representado por el carácter *ch* en el *radio*base , o -1 si *ch* no es un dígito válido en el *radio*base . La función solo se llamará con un argumento *radix* de 8, 10 o 16.

## <a name="see-also"></a>Consulte también

[\<regex>](../standard-library/regex.md)\
[Clase regex_constants](../standard-library/regex-constants-class.md)\
[Clase regex_error](../standard-library/regex-error-class.md)\
[\<funciones de> regex](../standard-library/regex-functions.md)\
[Clase regex_iterator](../standard-library/regex-iterator-class.md)\
[\<operadores de> regex](../standard-library/regex-operators.md)\
[Clase regex_token_iterator](../standard-library/regex-token-iterator-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)\
[regex_traits\<char> Clase](../standard-library/regex-traits-char-class.md)\
[regex_traits\<wchar_t> (Clase)](../standard-library/regex-traits-wchar-t-class.md)
