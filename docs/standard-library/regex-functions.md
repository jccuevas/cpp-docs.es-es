---
title: Funciones &lt;regex&gt; | Microsoft Docs
ms.custom: ''
ms.date: 09/10/2018
ms.topic: reference
f1_keywords:
- regex/std::regex_match
- regex/std::regex_replace
- regex/std::regex_search
- regex/std::swap
dev_langs:
- C++
ms.assetid: 91a8314b-6f7c-4e33-b7d6-d8583dd75585
helpviewer_keywords:
- std::regex_match [C++]
- std::regex_replace [C++]
- std::regex_search [C++]
- std::swap [C++]
- std::swap [C++]
ms.openlocfilehash: 3b78ce35b20c3049c168ab23c512ae7ae23b9886
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691555"
---
# <a name="ltregexgt-functions"></a>Funciones &lt;regex&gt;

|||
|-|-|
|[regex_match](#regex_match)|Comprueba si una expresión regular coincide con toda la cadena de destino.|
|[regex_replace](#regex_replace)|Reemplaza las expresiones regulares que coincidan.|
|[regex_search](#regex_search)|Busca una coincidencia con la expresión regular.|
|[swap](#swap)|Intercambia dos `basic_regex` o `match_results` objetos.|

## <a name="regex_match"></a>  regex_match)

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

*BidIt*<br/> El tipo de iterador para subcoincidencias. Para casos comunes de `string::const_iterator`, `wstring::const_iterator`, `const char*` o `const wchar_t*`.

*Alloc*<br/>
La clase de asignador de resultados de coincidencia.

*Elem*<br/>
Tipo de los elementos que debe coincidir. Para casos comunes, esto es `string`, `wstring`, `char*` o `wchar_t*`.

*RXtraits*<br/>
Clase Traits para los elementos.

*Alloc2*<br/>
La clase de asignador de expresión regular.

*IOtraits*<br/>
La clase de características de cadena.

*IOalloc*<br/>
La clase de asignador de cadena.

*flags*<br/>
Marcadores para coincidencias.

*first*<br/>
Principio de la secuencia que debe coincidir.

*Último*<br/>
Final de la secuencia que debe coincidir.

*Match*<br/>
Los resultados de la coincidencia. Corresponde al tipo Elem: [smatch](../standard-library/regex-typedefs.md#smatch) para `string`, [wsmatch](../standard-library/regex-typedefs.md#wsmatch) para `wstring`, [cmatch](../standard-library/regex-typedefs.md#cmatch) para `char*` o [wcmatch](../standard-library/regex-typedefs.md#wcmatch) para `wchar_t*`.

*ptr*<br/>
Puntero al inicio de la secuencia que debe coincidir. Si *ptr* es `char*`, a continuación, usar `cmatch` y `regex`. Si *ptr* es `wchar_t*` , a continuación, usar `wcmatch` y `wregex`.

*Re*<br/>
La expresión regular que debe coincidir. Tipo `regex` para `string` y `char*`, o `wregex` para `wstring` y `wchar_t*`.

*str*<br/>
Cadena que debe coincidir. Corresponde al tipo de *Elem*.

### <a name="remarks"></a>Comentarios

Cada función de plantilla devuelve true solo si la secuencia de operandos todo *str* coincide exactamente con el argumento de expresión regular *re*. Use [regex_search](../standard-library/regex-functions.md#regex_search) para hacer coincidir una subcadena dentro de una secuencia de destino y `regex_iterator` para encontrar coincidencias múltiples. Las funciones que toman un objeto `match_results` establecen que sus miembros reflejen si la coincidencia ha tenido lugar y, de ser así, qué han capturado los varios grupos de captura de la expresión regular.

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

## <a name="regex_replace"></a>  regex_replace)

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

*OutIt*<br/>
El tipo de iterador para reemplazos.

*BidIt*<br/>
El tipo de iterador para subcoincidencias.

*RXtraits*<br/>
Clase Traits para los elementos.

*Alloc*<br/>
La clase de asignador de expresión regular.

*Elem*<br/>
Tipo de los elementos que debe coincidir.

*flags*<br/>
Marcadores para coincidencias.

*first*<br/>
Principio de la secuencia que debe coincidir.

*FMT*<br/>
El formato para reemplazos.

*Último*<br/>
Final de la secuencia que debe coincidir.

*out*<br/>
El tipo de iterador de salida.

*Re*<br/>
La expresión regular que debe coincidir.

*str*<br/>
Cadena que debe coincidir.

### <a name="remarks"></a>Comentarios

La primera función construye un [regex_iterator (clase)](../standard-library/regex-iterator-class.md) objeto `iter(first, last, re, flags)` y lo usa para dividir su intervalo de entrada `[first, last)` en una serie de subsecuencias `T0 M0 T1 M1...TN-1 MN-1 TN`, donde `Mn` es la coincidencia enésima detectada por el iterador. Si no se detecta ninguna coincidencia, `T0` es el intervalo de entrada completo y `N` es cero. Si `(flags & format_first_only) != 0` solo se usa la primera coincidencia, `T1` es todo el texto de entrada que sigue a la coincidencia y `N` es 1. Para cada `i` en el intervalo `[0, N)`si `(flags & format_no_copy) == 0` copia el texto en el intervalo `Ti` al iterador *out*. Después, llama a `m.format(out, fmt, flags)`, donde `m` es el objeto `match_results` que ha devuelto el objeto de iterador `iter` para la subsecuencia `Mi`. Por último, si `(flags & format_no_copy) == 0` copia el texto en el intervalo `TN` al iterador *out*. La función devuelve *out*.

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

## <a name="regex_search"></a>  regex_search)

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

*BidIt*<br/>
El tipo de iterador para subcoincidencias.

*Alloc*<br/>
La clase de asignador de resultados de coincidencia.

*Elem*<br/>
Tipo de los elementos que debe coincidir.

*RXtraits*<br/>
Clase Traits para los elementos.

*Alloc2*<br/>
La clase de asignador de expresión regular.

*IOtraits*<br/>
La clase de características de cadena.

*IOalloc*<br/>
La clase de asignador de cadena.

*flags*<br/>
Marcadores para coincidencias.

*first*<br/>
Principio de la secuencia que debe coincidir.

*Último*<br/>
Final de la secuencia que debe coincidir.

*Match*<br/>
Los resultados de la coincidencia.

*ptr*<br/>
Puntero al inicio de la secuencia que debe coincidir.

*Re*<br/>
La expresión regular que debe coincidir.

*str*<br/>
Cadena que debe coincidir.

### <a name="remarks"></a>Comentarios

Cada función de plantilla devuelve true solo si una búsqueda de su argumento de expresión regular *re* en su operando de la secuencia se realiza correctamente. Las funciones que toman un objeto `match_results` establecen que sus miembros reflejen si la búsqueda se ha realizado correctamente y, de ser así, que han capturado los diversos grupos de captura de la expresión regular.

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

## <a name="swap"></a>  swap

Intercambia dos `basic_regex` o `match_results` objetos.

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

*Elem*<br/>
Tipo de los elementos que debe coincidir.

*RXtraits*<br/>
Clase Traits para los elementos.

### <a name="remarks"></a>Comentarios

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

## <a name="see-also"></a>Vea también

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants (Clase)](../standard-library/regex-constants-class.md)<br/>
[regex_error (Clase)](../standard-library/regex-error-class.md)<br/>
[regex_iterator (Clase)](../standard-library/regex-iterator-class.md)<br/>
[Operadores de \<regex>](../standard-library/regex-operators.md)<br/>
[regex_token_iterator (Clase)](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits (Clase)](../standard-library/regex-traits-class.md)<br/>
[Definiciones de tipo \<regex>](../standard-library/regex-typedefs.md)<br/>
