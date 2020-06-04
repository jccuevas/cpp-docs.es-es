---
title: Funciones &lt;regex&gt;
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_match
- regex/std::regex_replace
- regex/std::regex_search
- regex/std::swap
ms.assetid: 91a8314b-6f7c-4e33-b7d6-d8583dd75585
helpviewer_keywords:
- std::regex_match [C++]
- std::regex_replace [C++]
- std::regex_search [C++]
- std::swap [C++]
- std::swap [C++]
ms.openlocfilehash: ff6ea37208aef19431bf7aefe612dccd589c638b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374543"
---
# <a name="ltregexgt-functions"></a>Funciones &lt;regex&gt;

|||
|-|-|
|[regex_match](#regex_match)|Comprueba si una expresión regular coincide con toda la cadena de destino.|
|[regex_replace](#regex_replace)|Reemplaza las expresiones regulares que coincidan.|
|[regex_search](#regex_search)|Busca una coincidencia con la expresión regular.|
|[swap](#swap)|Intercambia `basic_regex` dos `match_results` u objetos.|

## <a name="regex_match"></a><a name="regex_match"></a>regex_match

Comprueba si una expresión regular coincide con toda la cadena de destino.

```cpp
// (1)
template <class BidIt, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    BidIt first,
    Bidit last,
    match_results<BidIt, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (2)
template <class BidIt, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    BidIt first,
    Bidit last,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (3)
template <class Elem, class Alloc, class RXtraits, class Alloc2>
bool regex_match(
    const Elem *ptr,
    match_results<const Elem*, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (4)
template <class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const Elem *ptr,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (5)
template <class IOtraits, class IOalloc, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    match_results<typename basic_string<Elem, IOtraits, IOalloc>::const_iterator, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (6)
template <class IOtraits, class IOalloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>Parámetros

*BidIt*\
El tipo de iterador para subcoincidencias. Para casos comunes `string::const_iterator`este `wstring::const_iterator` `const char*` de `const wchar_t*`, , o .

*Alloc*\
La clase de asignador de resultados de coincidencia.

*Elem*\
Tipo de los elementos que debe coincidir. Para casos comunes `string` `wstring`esto `char*` `wchar_t*`es , , o .

*RXtraits*\
Clase Traits para los elementos.

*Alloc2*\
La clase de asignador de expresión regular.

*IOtraits*\
La clase de características de cadena.

*IOalloc*\
La clase de asignador de cadena.

*Banderas*\
Marcadores para coincidencias.

*Primero*\
Principio de la secuencia que debe coincidir.

*Última*\
Final de la secuencia que debe coincidir.

*Partido*\
Los resultados de la coincidencia. Corresponde al tipo Elem: `string` [smatch](../standard-library/regex-typedefs.md#smatch) for `wstring`, [wsmatch](../standard-library/regex-typedefs.md#wsmatch) for `wchar_t*`, [cmatch](../standard-library/regex-typedefs.md#cmatch) for `char*` o [wcmatch](../standard-library/regex-typedefs.md#wcmatch) for .

*Ptr*\
Puntero al inicio de la secuencia que debe coincidir. Si *ptr* ptr `char*`es `cmatch` , `regex`a continuación, utilice y . Si *ptr* ptr `wchar_t*` es `wcmatch` `wregex`entonces use y .

*re*\
La expresión regular con la que debe coincidir. Escriba `regex` `string` for `char*`y `wregex` `wstring` , `wchar_t*`o for y .

*Str*\
Cadena que debe coincidir. Corresponde al tipo de *Elem*.

### <a name="remarks"></a>Observaciones

Cada función de plantilla devuelve true solo si toda la secuencia *de operandos str* coincide exactamente con el argumento de expresión regular *re*. Utilice [regex_search](../standard-library/regex-functions.md#regex_search) para hacer coincidir una `regex_iterator` subcadena dentro de una secuencia de destino y para buscar varias coincidencias. Las funciones que toman un objeto `match_results` establecen que sus miembros reflejen si la coincidencia ha tenido lugar y, de ser así, qué han capturado los varios grupos de captura de la expresión regular.

Las funciones que toman un objeto `match_results` establecen que sus miembros reflejen si la coincidencia ha tenido lugar y, de ser así, qué han capturado los varios grupos de captura de la expresión regular.

### <a name="example"></a>Ejemplo

```cpp
// std__regex__regex_match.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

using namespace std;

int main()
{
    // (1) with char*
    // Note how const char* requires cmatch and regex
    const char *first = "abc";
    const char *last = first + strlen(first);
    cmatch narrowMatch;
    regex rx("a(b)c");

    bool found = regex_match(first, last, narrowMatch, rx);
    if (found)
        wcout << L"Regex found in abc" << endl;

    // (2) with std::wstring
    // Note how wstring requires wsmatch and wregex.
    // Note use of const iterators cbegin() and cend().
    wstring target(L"Hello");
    wsmatch wideMatch;
    wregex wrx(L"He(l+)o");

    if (regex_match(target.cbegin(), target.cend(), wideMatch, wrx))
        wcout << L"The matching text is:" << wideMatch.str() << endl;

    // (3) with std::string
    string target2("Drizzle");
    regex rx2(R"(D\w+e)"); // no double backslashes with raw string literal

    found = regex_match(target2.cbegin(), target2.cend(), rx2);
    if (found)
        wcout << L"Regex found in Drizzle" << endl;

    // (4) with wchar_t*
    const wchar_t* target3 = L"2014-04-02";
    wcmatch wideMatch2;

    // LR"(...)" is a  raw wide-string literal. Open and close parens
    // are delimiters, not string elements.
    wregex wrx2(LR"(\d{4}(-|/)\d{2}(-|/)\d{2})");
    if (regex_match(target3, wideMatch2, wrx2))
    {
        wcout << L"Matching text: " << wideMatch2.str() << endl;
    }

     return 0;
}
```

```Output
Regex found in abc
The matching text is: Hello
Regex found in Drizzle
The matching text is: 2014-04-02
```

## <a name="regex_replace"></a><a name="regex_replace"></a>regex_replace

Reemplaza las expresiones regulares que coincidan.

```cpp
template <class OutIt, class BidIt, class RXtraits, class Alloc, class Elem>
OutIt regex_replace(
    OutIt out,
    BidIt first,
    BidIt last,
    const basic_regex<Elem, RXtraits, Alloc>& re,
    const basic_string<Elem>& fmt,
    match_flag_type flags = match_default);

template <class RXtraits, class Alloc, class Elem>
basic_string<Elem> regex_replace(
    const basic_string<Elem>& str,
    const basic_regex<Elem, RXtraits, Alloc>& re,
    const basic_string<Elem>& fmt,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>Parámetros

*OutIt*\
El tipo de iterador para reemplazos.

*BidIt*\
El tipo de iterador para subcoincidencias.

*RXtraits*\
Clase Traits para los elementos.

*Alloc*\
La clase de asignador de expresión regular.

*Elem*\
Tipo de los elementos que debe coincidir.

*Banderas*\
Marcadores para coincidencias.

*Primero*\
Principio de la secuencia que debe coincidir.

*Fmt*\
El formato para reemplazos.

*Última*\
Final de la secuencia que debe coincidir.

*hacia fuera*\
El tipo de iterador de salida.

*re*\
La expresión regular con la que debe coincidir.

*Str*\
Cadena que debe coincidir.

### <a name="remarks"></a>Observaciones

La primera función [regex_iterator Class](../standard-library/regex-iterator-class.md) construye `iter(first, last, re, flags)` un objeto regex_iterator Class `[first, last)` y lo utiliza para `T0 M0 T1 M1...TN-1 MN-1 TN`dividir `Mn` su rango de entrada en una serie de subsecuencias, donde está la enésima coincidencia detectada por el iterador. Si no se detecta ninguna coincidencia, `T0` es el intervalo de entrada completo y `N` es cero. Si `(flags & format_first_only) != 0` solo se usa la primera coincidencia, `T1` es todo el texto de entrada que sigue a la coincidencia y `N` es 1. Para `i` cada uno `[0, N)`en `(flags & format_no_copy) == 0` el intervalo , `Ti` si copia el texto del intervalo en el *iterador*. A continuación, llama a `m.format(out, fmt, flags)`, donde `m` está el `match_results` objeto devuelto por el objeto `iter` de iterador para la subsecuencia `Mi`. Por último, si `(flags & format_no_copy) == 0` copia el `TN` texto del intervalo en el *iterador*. La función devuelve *.*

La segunda función construye una variable local `result` de tipo `basic_string<charT>` y llama a `regex_replace(back_inserter(result), str.begin(), str.end(), re, fmt, flags)`. Devuelve `result`.

### <a name="example"></a>Ejemplo

```cpp
// std__regex__regex_replace.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    char buf[20];
    const char *first = "axayaz";
    const char *last = first + strlen(first);
    std::regex rx("a");
    std::string fmt("A");
    std::regex_constants::match_flag_type fonly =
        std::regex_constants::format_first_only;

    *std::regex_replace(&buf[0], first, last, rx, fmt) = '\0';
    std::cout << "replacement == " << &buf[0] << std::endl;

    *std::regex_replace(&buf[0], first, last, rx, fmt, fonly) = '\0';
    std::cout << "replacement == " << &buf[0] << std::endl;

    std::string str("adaeaf");
    std::cout << "replacement == "
        << std::regex_replace(str, rx, fmt) << std::endl;

    std::cout << "replacement == "
        << std::regex_replace(str, rx, fmt, fonly) << std::endl;

    return (0);
}
```

```Output
replacement == AxAyAz
replacement == Axayaz
replacement == AdAeAf
replacement == Adaeaf
```

## <a name="regex_search"></a><a name="regex_search"></a>regex_search

Busca una coincidencia con la expresión regular.

```cpp
template <class BidIt, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    BidIt first,
    Bidit last,
    match_results<BidIt, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class BidIt, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    BidIt first,
    Bidit last,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class Elem, class Alloc, class RXtraits, class Alloc2>
bool regex_search(
    const Elem* ptr,
    match_results<const Elem*, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const Elem* ptr,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class IOtraits, class IOalloc, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    match_results<typename basic_string<Elem, IOtraits, IOalloc>::const_iterator, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class IOtraits, class IOalloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>Parámetros

*BidIt*\
El tipo de iterador para subcoincidencias.

*Alloc*\
La clase de asignador de resultados de coincidencia.

*Elem*\
Tipo de los elementos que debe coincidir.

*RXtraits*\
Clase Traits para los elementos.

*Alloc2*\
La clase de asignador de expresión regular.

*IOtraits*\
La clase de características de cadena.

*IOalloc*\
La clase de asignador de cadena.

*Banderas*\
Marcadores para coincidencias.

*Primero*\
Principio de la secuencia que debe coincidir.

*Última*\
Final de la secuencia que debe coincidir.

*Partido*\
Los resultados de la coincidencia.

*Ptr*\
Puntero al inicio de la secuencia que debe coincidir.

*re*\
La expresión regular con la que debe coincidir.

*Str*\
Cadena que debe coincidir.

### <a name="remarks"></a>Observaciones

Cada función de plantilla devuelve true solo si se realiza correctamente una búsqueda de su argumento *de* expresión regular en su secuencia de operandos. Las funciones que toman un objeto `match_results` establecen que sus miembros reflejen si la búsqueda se ha realizado correctamente y, de ser así, que han capturado los diversos grupos de captura de la expresión regular.

### <a name="example"></a>Ejemplo

```cpp
// std__regex__regex_search.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    const char *first = "abcd";
    const char *last = first + strlen(first);
    std::cmatch mr;
    std::regex rx("abc");
    std::regex_constants::match_flag_type fl =
        std::regex_constants::match_default;

    std::cout << "search(f, f+1, \"abc\") == " << std::boolalpha
        << regex_search(first, first + 1, rx, fl) << std::endl;

    std::cout << "search(f, l, \"abc\") == " << std::boolalpha
        << regex_search(first, last, mr, rx) << std::endl;
    std::cout << "  matched: \"" << mr.str() << "\"" << std::endl;

    std::cout << "search(\"a\", \"abc\") == " << std::boolalpha
        << regex_search("a", rx) << std::endl;

    std::cout << "search(\"xabcd\", \"abc\") == " << std::boolalpha
        << regex_search("xabcd", mr, rx) << std::endl;
    std::cout << "  matched: \"" << mr.str() << "\"" << std::endl;

    std::cout << "search(string, \"abc\") == " << std::boolalpha
        << regex_search(std::string("a"), rx) << std::endl;

    std::string str("abcabc");
    std::match_results<std::string::const_iterator> mr2;
    std::cout << "search(string, \"abc\") == " << std::boolalpha
        << regex_search(str, mr2, rx) << std::endl;
    std::cout << "  matched: \"" << mr2.str() << "\"" << std::endl;

    return (0);
}
```

```Output
search(f, f+1, "abc") == false
search(f, l, "abc") == true
  matched: "abc"
search("a", "abc") == false
search("xabcd", "abc") == true
  matched: "abc"
search(string, "abc") == false
search(string, "abc") == true
  matched: "abc"
```

## <a name="swap"></a><a name="swap"></a>Intercambio

Intercambia `basic_regex` dos `match_results` u objetos.

```cpp
template <class Elem, class RXtraits>
void swap(
    basic_regex<Elem, RXtraits, Alloc>& left,
    basic_regex<Elem, RXtraits>& right) noexcept;

template <class Elem, class IOtraits, class BidIt, class Alloc>
void swap(
    match_results<BidIt, Alloc>& left,
    match_results<BidIt, Alloc>& right) noexcept;
```

### <a name="parameters"></a>Parámetros

*Elem*\
Tipo de los elementos que debe coincidir.

*RXtraits*\
Clase Traits para los elementos.

### <a name="remarks"></a>Observaciones

Las funciones de plantilla intercambian el contenido de sus argumentos respectivos en tiempo constante y no producen excepciones.

### <a name="example"></a>Ejemplo

```cpp
// std__regex__swap.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    std::regex rx0("c(a*)|(b)");
    std::regex rx1;
    std::cmatch mr0;
    std::cmatch mr1;

    swap(rx0, rx1);
    std::regex_search("xcaaay", mr1, rx1);
    swap(mr0, mr1);

    std::csub_match sub = mr0[1];
    std::cout << "matched == " << std::boolalpha
        << sub.matched << std::endl;
    std::cout << "length == " << sub.length() << std::endl;
    std::cout << "string == " << sub << std::endl;

    return (0);
}
```

```Output
matched == true
length == 3
string == aaa
```

## <a name="see-also"></a>Consulte también

[\<regex>](../standard-library/regex.md)\
[Clase regex_constants](../standard-library/regex-constants-class.md)\
[Clase regex_error](../standard-library/regex-error-class.md)\
[Clase regex_iterator](../standard-library/regex-iterator-class.md)\
[\<operadores de> regex](../standard-library/regex-operators.md)\
[Clase regex_token_iterator](../standard-library/regex-token-iterator-class.md)\
[Clase regex_traits](../standard-library/regex-traits-class.md)\
[\<regex> typedefs](../standard-library/regex-typedefs.md)
