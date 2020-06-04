---
title: basic_regex (Clase)
ms.date: 03/27/2019
f1_keywords:
- regex/std::basic_regex
helpviewer_keywords:
- basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
ms.openlocfilehash: 74a8684c619e2cfbd5417950aa6108ad93511bf7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376747"
---
# <a name="basic_regex-class"></a>basic_regex (Clase)

Contiene una expresión regular.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Elem, class RXtraits>
class basic_regex
```

## <a name="parameters"></a>Parámetros

*Elem*\
Tipo de los elementos que debe coincidir.

*RXtraits*\
Clase Traits para los elementos.

## <a name="remarks"></a>Observaciones

La plantilla de clase describe un objeto que contiene una expresión regular. Los objetos de esta plantilla de clase se pueden pasar a las funciones de plantilla [regex_match](../standard-library/regex-functions.md#regex_match), [regex_search](../standard-library/regex-functions.md#regex_search)y [regex_replace](../standard-library/regex-functions.md#regex_replace), junto con argumentos de cadena de texto adecuados, para buscar texto que coincida con la expresión regular. Hay dos especializaciones de esta plantilla de clase, con las definiciones de tipo [regex](../standard-library/regex-typedefs.md#regex) para los elementos de tipo **char**y [wregex](../standard-library/regex-typedefs.md#wregex) para elementos de tipo **wchar_t**.

El argumento de plantilla *RXtraits* describe varias propiedades importantes de la sintaxis de las expresiones regulares que admite la plantilla de clase. Una clase que especifica estos rasgos de expresión regular debe tener la misma interfaz externa que un objeto de tipo [regex_traits Class](../standard-library/regex-traits-class.md).

Algunas funciones toman una secuencia de operandos que define una expresión regular. Puede especificar dicha secuencia de operandos de varias maneras:

`ptr`-- una secuencia terminada en null (como una cadena **char**C, para `ptr` *Elem* de tipo char ) que comienza en `value_type()` (que no debe ser un puntero nulo), donde el elemento de terminación es el valor y no forma parte de la secuencia de operandos

`ptr`, `count` -- una secuencia de elementos `count` que comienza en `ptr` (que no puede ser un puntero null)

`str` -- la secuencia especificada por el objeto `basic_string``str`

`first`, `last` -- una secuencia de elementos delimitada por los iteradores `first` y `last`, en el intervalo `[first, last)`

`right` -- el objeto `basic_regex``right`

Estas funciones miembro `flags` también toman un argumento que especifica varias opciones para la interpretación de la expresión regular además de las descritas por el *tipo RXtraits.*

### <a name="members"></a>Miembros

|Member|Valor predeterminado|
|-|-|
|const estático público flag_type icase|regex_constants::icase|
|const estático público flag_type nosubs|regex_constants::nosubs|
|const estático público flag_type optimizar|regex_constants::optimizar|
|const estático público flag_type cotejar|regex_constants::collate|
|const estático público flag_type ECMAScript|regex_constants::ECMAScript|
|const estático público flag_type básico|regex_constants::básico|
|const estático público flag_type extendido|regex_constants::extendido|
|const estático público flag_type awk|regex_constants::awk|
|const estático público flag_type grep|regex_constants::grep|
|público static const flag_type egrep|regex_constants::egrep|
|rasgos privados de RXtraits||

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_regex](#basic_regex)|Construye el objeto de expresión regular.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[flag_type](#flag_type)|El tipo de marcas de opción de sintaxis.|
|[locale_type](#locale_type)|El tipo de objeto de configuración regional almacenado.|
|[value_type](#value_type)|El tipo de elemento.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Asignar](#assign)|Asigna un valor al objeto de expresión regular.|
|[Banderas](#flags)|Devuelve marcas de opción de sintaxis.|
|[getloc](#getloc)|Devuelve el objeto de configuración regional almacenado.|
|[imbue](#imbue)|Modifica el objeto de configuración regional almacenado.|
|[mark_count](#mark_count)|Devuelve el número de subexpresiones coincidentes.|
|[swap](#swap)|Intercambia dos objetos de expresión regular.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[operador](#op_eq)|Asigna un valor al objeto de expresión regular.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<regex>

**Espacio de nombres:** std

## <a name="example"></a>Ejemplo

```cpp
// std__regex__basic_regex.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

using namespace std;

int main()
{
    regex::value_type elem = 'x';
    regex::flag_type flag = regex::grep;

    elem = elem;  // to quiet "unused" warnings
    flag = flag;

    // constructors
    regex rx0;
    cout << "match(\"abc\", \"\") == " << boolalpha
        << regex_match("abc", rx0) << endl;

    regex rx1("abcd", regex::ECMAScript);
    cout << "match(\"abc\", \"abcd\") == " << boolalpha
        << regex_match("abc", rx1) << endl;

    regex rx2("abcd", 3);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx2) << endl;

    regex rx3(rx2);
    cout << "match(\"abc\", \"abc\") == " << boolalpha
        << regex_match("abc", rx3) << endl;

    string str("abcd");
    regex rx4(str);
    cout << "match(string(\"abcd\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx4) << endl;

    regex rx5(str.begin(), str.end() - 1);
    cout << "match(string(\"abc\"), \"abc\") == " << boolalpha
        << regex_match("abc", rx5) << endl;
    cout << endl;

    // assignments
    rx0 = "abc";
    rx0 = rx1;
    rx0 = str;

    rx0.assign("abcd", regex::ECMAScript);
    rx0.assign("abcd", 3);
    rx0.assign(rx1);
    rx0.assign(str);
    rx0.assign(str.begin(), str.end() - 1);

    rx0.swap(rx1);

    // mark_count
    cout << "\"abc\" mark_count == "
        << regex("abc").mark_count() << endl;
    cout << "\"(abc)\" mark_count == "
        << regex("(abc)").mark_count() << endl;

    // locales
    regex::locale_type loc = rx0.imbue(locale());
    cout << "getloc == imbued == " << boolalpha
        << (loc == rx0.getloc()) << endl;

    // initializer_list
    regex rx6({ 'a', 'b', 'c' }, regex::ECMAScript);
    cout << "match(\"abc\") == " << boolalpha
        << regex_match("abc", rx6);
    cout << endl;
}
```

```Output
match("abc", "") == false
match("abc", "abcd") == false
match("abc", "abc") == true
match("abc", "abc") == true
match(string("abcd"), "abc") == false
match(string("abc"), "abc") == true

"abc" mark_count == 0
"(abc)" mark_count == 1
getloc == imbued == true
match("abc") == true
```

## <a name="basic_regexassign"></a><a name="assign"></a>basic_regex::asignar

Asigna un valor al objeto de expresión regular.

```cpp
basic_regex& assign(
    const basic_regex& right);

basic_regex& assign(
    const Elem* ptr,
    flag_type flags = ECMAScript);

basic_regex& assign(
    const Elem* ptr,
    size_type len,
    flag_type flags = ECMAScript);

basic_regex& assign(
    initializer_list<_Elem> IList,
    flag_type flags = regex_constants::ECMAScript);

template <class STtraits, class STalloc>
basic_regex& assign(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags = ECMAScript);

template <class InIt>
basic_regex& assign(
    InIt first, InIt last,
    flag_type flags = ECMAScript);
```

### <a name="parameters"></a>Parámetros

*Estrechos*\
Clase traits para un origen de cadena.

*STalloc*\
Clase de asignador para un origen de cadena.

*Init*\
Tipo de iterador de entrada para un origen de intervalo.

*Correcto*\
Origen regex que se va a copiar.

*Ptr*\
Puntero al inicio de la secuencia que se va a copiar.

*Banderas*\
Marcas de opción de sintaxis que se van a agregar al copiar.

*>len/TD*\
Longitud de la secuencia que se va a copiar.

*Str*\
Cadena que se va a copiar.

*Primero*\
Principio de la secuencia que se va a copiar.

*Última*\
Final de la secuencia que se va a copiar.

*Ilist*\
initializer_list que se va a copiar.

### <a name="remarks"></a>Observaciones

Cada una de las funciones miembro reemplaza la expresión regular que contiene `*this` con la expresión regular descrita por la secuencia de operandos y después devuelve `*this`.

## <a name="basic_regexbasic_regex"></a><a name="basic_regex"></a>basic_regex::basic_regex

Construye el objeto de expresión regular.

```cpp
basic_regex();

explicit basic_regex(
    const Elem* ptr,
    flag_type flags);

explicit basic_regex(
    const Elem* ptr,
    size_type len,
    flag_type flags);

basic_regex(
    const basic_regex& right);

basic_regex(
    initializer_list<Type> IList,
    flag_type flags);

template <class STtraits, class STalloc>
explicit basic_regex(
    const basic_string<Elem, STtraits, STalloc>& str,
    flag_type flags);

template <class InIt>
explicit basic_regex(
    InIt first,
    InIt last,
    flag_type flags);
```

### <a name="parameters"></a>Parámetros

*Estrechos*\
Clase traits para un origen de cadena.

*STalloc*\
Clase de asignador para un origen de cadena.

*Init*\
Tipo de iterador de entrada para un origen de intervalo.

*Correcto*\
Origen regex que se va a copiar.

*Ptr*\
Puntero al inicio de la secuencia que se va a copiar.

*Banderas*\
Marcas de opción de sintaxis que se van a agregar al copiar.

*>len/TD*\
Longitud de la secuencia que se va a copiar.

*Str*\
Cadena que se va a copiar.

*Primero*\
Principio de la secuencia que se va a copiar.

*Última*\
Final de la secuencia que se va a copiar.

*Ilist*\
initializer_list que se va a copiar.

### <a name="remarks"></a>Observaciones

Todos los constructores almacenan un objeto construido de forma predeterminada de tipo `RXtraits`.

El primer constructor crea un objeto `basic_regex` vacío. Los otros constructores crean un objeto `basic_regex` que contiene la expresión regular descrita por la secuencia de operandos.

Un `basic_regex` objeto vacío no coincide con ninguna secuencia de caracteres cuando se pasa a [regex_match](../standard-library/regex-functions.md#regex_match), [regex_search](../standard-library/regex-functions.md#regex_search)o [regex_replace](../standard-library/regex-functions.md#regex_replace).

## <a name="basic_regexflag_type"></a><a name="flag_type"></a>basic_regex::flag_type

El tipo de marcas de opción de sintaxis.

```cpp
typedef regex_constants::syntax_option_type flag_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

## <a name="basic_regexflags"></a><a name="flags"></a>basic_regex::flags

Devuelve marcas de opción de sintaxis.

```cpp
flag_type flags() const;
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve el valor del argumento `flag_type` pasado a la llamada más reciente a una de las funciones miembro [basic_regex::assign](#assign) o, si no se hizo dicha llamada, el valor pasado al constructor.

## <a name="basic_regexgetloc"></a><a name="getloc"></a>basic_regex::getloc

Devuelve el objeto de configuración regional almacenado.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Observaciones

La función `traits.`miembro devuelve [regex_traits::getloc](../standard-library/regex-traits-class.md#getloc)`()`.

## <a name="basic_regeximbue"></a><a name="imbue"></a>basic_regex::imbue

Modifica el objeto de configuración regional almacenado.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Parámetros

*Loc*\
El objeto de configuración regional que se va a almacenar.

### <a name="remarks"></a>Observaciones

La función `*this` miembro `traits.`vacía y devuelve [regex_traits::imbue](../standard-library/regex-traits-class.md#imbue)`(loc)`.

## <a name="basic_regexlocale_type"></a><a name="locale_type"></a>basic_regex::locale_type

El tipo de objeto de configuración regional almacenado.

```cpp
typedef typename RXtraits::locale_type locale_type;
```

### <a name="remarks"></a>Observaciones

El tipo es sinónimo de [regex_traits::locale_type](../standard-library/regex-traits-class.md#locale_type).

## <a name="basic_regexmark_count"></a><a name="mark_count"></a>basic_regex::mark_count

Devuelve el número de subexpresiones coincidentes.

```cpp
unsigned mark_count() const;
```

### <a name="remarks"></a>Observaciones

La función miembro devuelve el número de grupos de capturas de la expresión regular.

## <a name="basic_regexoperator"></a><a name="op_eq"></a>basic_regex::operador ?

Asigna un valor al objeto de expresión regular.

```cpp
basic_regex& operator=(const basic_regex& right);

basic_regex& operator=(const Elem *str);

template <class STtraits, class STalloc>
basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
```

### <a name="parameters"></a>Parámetros

*Estrechos*\
Clase traits para un origen de cadena.

*STalloc*\
Clase de asignador para un origen de cadena.

*Correcto*\
Origen regex que se va a copiar.

*Str*\
Cadena que se va a copiar.

### <a name="remarks"></a>Observaciones

Cada uno de los operandos reemplaza la expresión regular incluida en `*this` con la expresión regular descrita por la secuencia de operandos y después devuelve `*this`.

## <a name="basic_regexswap"></a><a name="swap"></a>basic_regex::swap

Intercambia dos objetos de expresión regular.

```cpp
void swap(basic_regex& right) throw();
```

### <a name="parameters"></a>Parámetros

*Correcto*\
El objeto de expresión regular con el que se intercambia.

### <a name="remarks"></a>Observaciones

La función miembro intercambia `*this` las expresiones regulares entre y *right*. Lo hace en tiempo constante y no inicia ninguna excepción.

## <a name="basic_regexvalue_type"></a><a name="value_type"></a>basic_regex::value_type

El tipo de elemento.

```cpp
typedef Elem value_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla *Elem*.

## <a name="see-also"></a>Consulte también

[\<regex>](../standard-library/regex.md)\
[regex_match](../standard-library/regex-functions.md#regex_match)\
[regex_search](../standard-library/regex-functions.md#regex_search)\
[regex_replace](../standard-library/regex-functions.md#regex_replace)\
[Regex](../standard-library/regex-typedefs.md#regex)\
[wregex](../standard-library/regex-typedefs.md#wregex)\
[regex_traits (Clase)](../standard-library/regex-traits-class.md)
