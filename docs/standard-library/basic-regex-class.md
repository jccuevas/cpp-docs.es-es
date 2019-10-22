---
title: basic_regex (Clase)
ms.date: 03/27/2019
f1_keywords:
- regex/std::basic_regex
helpviewer_keywords:
- basic_regex class
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
ms.openlocfilehash: 45776754bd0854aeb85382eda95891a6832ca09e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689964"
---
# <a name="basic_regex-class"></a>basic_regex (Clase)

Contiene una expresión regular.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Elem, class RXtraits>
class basic_regex
```

## <a name="parameters"></a>Parámetros

@No__t_1 *Elem*
Tipo de los elementos que debe coincidir.

@No__t_1 *RXtraits*
Clase Traits para los elementos.

## <a name="remarks"></a>Comentarios

La plantilla de clase describe un objeto que contiene una expresión regular. Los objetos de esta plantilla de clase se pueden pasar a las funciones de plantilla [regex_match](../standard-library/regex-functions.md#regex_match), [regex_search](../standard-library/regex-functions.md#regex_search)y [regex_replace](../standard-library/regex-functions.md#regex_replace), junto con los argumentos de cadena de texto adecuados, para buscar texto que coincida con la expresión regular. Hay dos especializaciones de esta plantilla de clase, con las definiciones de tipo [Regex](../standard-library/regex-typedefs.md#regex) para los elementos de tipo **Char**y [wregex](../standard-library/regex-typedefs.md#wregex) para los elementos de tipo **wchar_t**.

El argumento de plantilla *RXtraits* describe diversas propiedades importantes de la sintaxis de las expresiones regulares que admite la plantilla de clase. Una clase que especifica estos rasgos de expresiones regulares debe tener la misma interfaz externa que un objeto de tipo [clase regex_traits](../standard-library/regex-traits-class.md).

Algunas funciones toman una secuencia de operandos que define una expresión regular. Puede especificar dicha secuencia de operandos de varias maneras:

`ptr`: una secuencia terminada en null (como una cadena de C, para *Elem* de tipo **Char**) que empieza en `ptr` (que no debe ser un puntero NULL), donde el elemento de terminación es el valor `value_type()` y no forma parte de la secuencia de operandos.

`ptr`, `count` -- una secuencia de elementos `count` que comienza en `ptr` (que no puede ser un puntero null)

`str` -- la secuencia especificada por el objeto `basic_string` `str`

`first`, `last` -- una secuencia de elementos delimitada por los iteradores `first` y `last`, en el intervalo `[first, last)`

`right` -- el objeto `basic_regex` `right`

Estas funciones miembro también toman un argumento `flags` que especifica varias opciones para la interpretación de la expresión regular además de las descritas por el tipo *RXtraits* .

### <a name="members"></a>Miembros

|Miembro|Default Value|
|-|-|
|public static const flag_type ICAse|regex_constants::icase|
|public static const flag_type nosubs|regex_constants:: nosubs|
|public static const flag_type Optimize|regex_constants:: Optimize|
|intercalación de flag_type estática const|regex_constants:: COLLATE|
|public static const flag_type ECMAScript|regex_constants:: ECMAScript|
|public static const flag_type Basic|regex_constants:: Basic|
|public static const flag_type Extended|regex_constants:: Extended|
|public static const flag_type awk|regex_constants:: awk|
|grep public static const flag_type|regex_constants:: grep|
|public static const flag_type egrep|regex_constants:: egrep|
|rasgos de RXtraits privados||

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_regex](#basic_regex)|Construye el objeto de expresión regular.|

### <a name="typedefs"></a>Definiciones de tipo

|Nombre de tipo|Descripción|
|-|-|
|[flag_type](#flag_type)|El tipo de marcas de opción de sintaxis.|
|[locale_type](#locale_type)|El tipo de objeto de configuración regional almacenado.|
|[value_type](#value_type)|El tipo de elemento.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[assign](#assign)|Asigna un valor al objeto de expresión regular.|
|[flags](#flags)|Devuelve marcas de opción de sintaxis.|
|[getloc](#getloc)|Devuelve el objeto de configuración regional almacenado.|
|[imbue](#imbue)|Modifica el objeto de configuración regional almacenado.|
|[mark_count](#mark_count)|Devuelve el número de subexpresiones coincidentes.|
|[swap](#swap)|Intercambia dos objetos de expresión regular.|

### <a name="operators"></a>Operadores

|"??"|Descripción|
|-|-|
|[operator=](#op_eq)|Asigna un valor al objeto de expresión regular.|

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

## <a name="assign"></a>  basic_regex::assign

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

@No__t_1 *STtraits*
Clase traits para un origen de cadena.

@No__t_1 *STalloc*
Clase de asignador para un origen de cadena.

@No__t_1 *InIt*
Tipo de iterador de entrada para un origen de intervalo.

\ *derecha*
Origen regex que se va a copiar.

\ *ptr*
Puntero al inicio de la secuencia que se va a copiar.

*marcas* \
Marcas de opción de sintaxis que se van a agregar al copiar.

*Len/TD >* \
Longitud de la secuencia que se va a copiar.

\ *Str*
Cadena que se va a copiar.

*primer* \
Principio de la secuencia que se va a copiar.

*última* \
Final de la secuencia que se va a copiar.

*IList* \
initializer_list que se va a copiar.

### <a name="remarks"></a>Comentarios

Cada una de las funciones miembro reemplaza la expresión regular que contiene `*this` con la expresión regular descrita por la secuencia de operandos y después devuelve `*this`.

## <a name="basic_regex"></a>  basic_regex::basic_regex

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

@No__t_1 *STtraits*
Clase traits para un origen de cadena.

@No__t_1 *STalloc*
Clase de asignador para un origen de cadena.

@No__t_1 *InIt*
Tipo de iterador de entrada para un origen de intervalo.

\ *derecha*
Origen regex que se va a copiar.

\ *ptr*
Puntero al inicio de la secuencia que se va a copiar.

*marcas* \
Marcas de opción de sintaxis que se van a agregar al copiar.

*Len/TD >* \
Longitud de la secuencia que se va a copiar.

\ *Str*
Cadena que se va a copiar.

*primer* \
Principio de la secuencia que se va a copiar.

*última* \
Final de la secuencia que se va a copiar.

*IList* \
initializer_list que se va a copiar.

### <a name="remarks"></a>Comentarios

Todos los constructores almacenan un objeto construido de forma predeterminada de tipo `RXtraits`.

El primer constructor crea un objeto `basic_regex` vacío. Los otros constructores crean un objeto `basic_regex` que contiene la expresión regular descrita por la secuencia de operandos.

Un objeto de `basic_regex` vacío no coincide con ninguna secuencia de caracteres cuando se pasa a [regex_match](../standard-library/regex-functions.md#regex_match), [regex_search](../standard-library/regex-functions.md#regex_search)o [regex_replace](../standard-library/regex-functions.md#regex_replace).

## <a name="flag_type"></a>  basic_regex::flag_type

El tipo de marcas de opción de sintaxis.

```cpp
typedef regex_constants::syntax_option_type flag_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#syntax_option_type).

## <a name="flags"></a>  basic_regex::flags

Devuelve marcas de opción de sintaxis.

```cpp
flag_type flags() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve el valor del argumento `flag_type` pasado a la llamada más reciente a una de las funciones miembro [basic_regex::assign](#assign) o, si no se hizo dicha llamada, el valor pasado al constructor.

## <a name="getloc"></a>  basic_regex::getloc

Devuelve el objeto de configuración regional almacenado.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve `traits.`[regex_traits::getloc](../standard-library/regex-traits-class.md#getloc)`()`.

## <a name="imbue"></a>  basic_regex::imbue

Modifica el objeto de configuración regional almacenado.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Parámetros

\ *Loc*
El objeto de configuración regional que se va a almacenar.

### <a name="remarks"></a>Comentarios

La función miembro vacía `*this` y devuelve `traits.`[regex_traits::imbue](../standard-library/regex-traits-class.md#imbue)`(loc)`.

## <a name="locale_type"></a>  basic_regex::locale_type

El tipo de objeto de configuración regional almacenado.

```cpp
typedef typename RXtraits::locale_type locale_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de [regex_traits::locale_type](../standard-library/regex-traits-class.md#locale_type).

## <a name="mark_count"></a>  basic_regex::mark_count

Devuelve el número de subexpresiones coincidentes.

```cpp
unsigned mark_count() const;
```

### <a name="remarks"></a>Comentarios

La función miembro devuelve el número de grupos de capturas de la expresión regular.

## <a name="op_eq"></a>  basic_regex::operator=

Asigna un valor al objeto de expresión regular.

```cpp
basic_regex& operator=(const basic_regex& right);

basic_regex& operator=(const Elem *str);

template <class STtraits, class STalloc>
basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);
```

### <a name="parameters"></a>Parámetros

@No__t_1 *STtraits*
Clase traits para un origen de cadena.

@No__t_1 *STalloc*
Clase de asignador para un origen de cadena.

\ *derecha*
Origen regex que se va a copiar.

\ *Str*
Cadena que se va a copiar.

### <a name="remarks"></a>Comentarios

Cada uno de los operandos reemplaza la expresión regular incluida en `*this` con la expresión regular descrita por la secuencia de operandos y después devuelve `*this`.

## <a name="swap"></a>  basic_regex::swap

Intercambia dos objetos de expresión regular.

```cpp
void swap(basic_regex& right) throw();
```

### <a name="parameters"></a>Parámetros

\ *derecha*
El objeto de expresión regular con el que se intercambia.

### <a name="remarks"></a>Comentarios

La función miembro intercambia las expresiones regulares entre `*this` y *right*. Lo hace en tiempo constante y no inicia ninguna excepción.

## <a name="value_type"></a>  basic_regex::value_type

El tipo de elemento.

```cpp
typedef Elem value_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla *Elem*.

## <a name="see-also"></a>Vea también

[\<regex>](../standard-library/regex.md)\
\ [regex_match](../standard-library/regex-functions.md#regex_match)
\ [regex_search](../standard-library/regex-functions.md#regex_search)
\ [regex_replace](../standard-library/regex-functions.md#regex_replace)
[regex](../standard-library/regex-typedefs.md#regex)\
[wregex](../standard-library/regex-typedefs.md#wregex)\
[regex_traits (Clase)](../standard-library/regex-traits-class.md)
