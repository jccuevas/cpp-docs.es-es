---
title: Definiciones de tipo de &lt;regex&gt;
ms.date: 11/04/2016
f1_keywords:
- regex/std::cmatch
- regex/std::cregex_iterator
- regex/std::cregex_token_iterator
- regex/std::csub_match
- regex/std::regex
- regex/std::smatch
- regex/std::sregex_iterator
- regex/std::sregex_token_iterator
- regex/std::ssub_match
- regex/std::wcmatch
- regex/std::wcregex_iterator
- regex/std::wcregex_token_iterator
- regex/std::wcsub_match
- regex/std::wregex
- regex/std::wsmatch
- regex/std::wsregex_iterator
- regex/std::wsregex_token_iterator
- regex/std::wssub_match
ms.assetid: e6a69067-106c-4a24-9e08-7c867a3a2260
ms.openlocfilehash: 33217388ff7e0826efcee413b39adaeba569399a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62369142"
---
# <a name="ltregexgt-typedefs"></a>Definiciones de tipo de &lt;regex&gt;

||||
|-|-|-|
|[cmatch](#cmatch)|[cregex_iterator](#cregex_iterator)|[cregex_token_iterator](#cregex_token_iterator)|
|[csub_match](#csub_match)|[regex](#regex)|[smatch](#smatch)|
|[sregex_iterator](#sregex_iterator)|[sregex_token_iterator](#sregex_token_iterator)|[ssub_match](#ssub_match)|
|[wcmatch](#wcmatch)|[wcregex_iterator](#wcregex_iterator)|[wcregex_token_iterator](#wcregex_token_iterator)|
|[wcsub_match](#wcsub_match)|[wregex](#wregex)|[wsmatch](#wsmatch)|
|[wsregex_iterator](#wsregex_iterator)|[wsregex_token_iterator](#wsregex_token_iterator)|[wssub_match](#wssub_match)|

## <a name="cmatch"></a>  cmatch (Definición de tipo)

Tipo de definición de char match_results.

```cpp
typedef match_results<const char*> cmatch;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [match_results (Clase)](../standard-library/match-results-class.md) para iteradores del tipo `const char*`.

## <a name="cregex_iterator"></a>  cregex_iterator (Definición de tipo)

Definición de tipo para regex_iterator de char.

```cpp
typedef regex_iterator<const char*> cregex_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [regex_iterator (Clase)](../standard-library/regex-iterator-class.md) para iteradores del tipo `const char*`.

## <a name="cregex_token_iterator"></a>  cregex_token_iterator (Definición de tipo)

Definición de tipo para regex_token_iterator de char

```cpp
typedef regex_token_iterator<const char*> cregex_token_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [regex_token_iterator (Clase)](../standard-library/regex-token-iterator-class.md) para iteradores del tipo `const char*`.

## <a name="csub_match"></a>  csub_match (Definición de tipo)

Definición de tipo para sub_match de char.

```cpp
typedef sub_match<const char*> csub_match;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [sub_match (Clase)](../standard-library/sub-match-class.md) para iteradores del tipo `const char*`.

## <a name="regex"></a>  regex (Definición de tipo)

Definición de tipo para basic_regex de char.

```cpp
typedef basic_regex<char> regex;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [basic_regex (clase)](../standard-library/basic-regex-class.md) elementos del tipo **char**.

> [!NOTE]
> Los caracteres ASCII de 8 bits tendrán resultados imprevisibles con `regex`. Los valores fuera del intervalo de 0 a 127 pueden producir un comportamiento indefinido.

## <a name="smatch"></a>  smatch (Definición de tipo)

Definición de tipo de regex_iterator de string.

```cpp
typedef match_results<string::const_iterator> smatch;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [match_results (Clase)](../standard-library/match-results-class.md) para iteradores del tipo `string::const_iterator`.

## <a name="sregex_iterator"></a>  sregex_iterator (Definición de tipo)

Definición de tipo de string regex_iterator.

```cpp
typedef regex_iterator<string::const_iterator> sregex_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [regex_iterator (Clase)](../standard-library/regex-iterator-class.md) para iteradores del tipo `string::const_iterator`.

## <a name="sregex_token_iterator"></a>  sregex_token_iterator (Definición de tipo)

Definición de tipo para regex_token_iterator de string.

```cpp
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [regex_token_iterator (Clase)](../standard-library/regex-token-iterator-class.md) para iteradores del tipo `string::const_iterator`.

## <a name="ssub_match"></a>  ssub_match (Definición de tipo)

Definición de tipo para sub_match de string.

```cpp
typedef sub_match<string::const_iterator> ssub_match;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [sub_match (Clase)](../standard-library/sub-match-class.md) para iteradores del tipo `string::const_iterator`.

## <a name="wcmatch"></a>  wcmatch (Definición de tipo)

Definición de tipo para match_results de wchar_t.

```cpp
typedef match_results<const wchar_t *> wcmatch;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [match_results (Clase)](../standard-library/match-results-class.md) para iteradores del tipo `const wchar_t*`.

## <a name="wcregex_iterator"></a>  wcregex_iterator (Definición de tipo)

Definición de tipo para wchar_t regex_iterator.

```cpp
typedef regex_iterator<const wchar_t*> wcregex_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [regex_iterator (Clase)](../standard-library/regex-iterator-class.md) para iteradores del tipo `const wchar_t*`.

## <a name="wcregex_token_iterator"></a>  wcregex_token_iterator (Definición de tipo)

Definición de tipo para regex_token_iterator de wchar_t.

```cpp
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [regex_token_iterator (Clase)](../standard-library/regex-token-iterator-class.md) para iteradores del tipo `const wchar_t*`.

## <a name="wcsub_match"></a>  wcsub_match (Definición de tipo)

Definición de tipo para sub_match de wchar_t.

```cpp
typedef sub_match<const wchar_t*> wcsub_match;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [sub_match (Clase)](../standard-library/sub-match-class.md) para iteradores del tipo `const wchar_t*`.

## <a name="wregex"></a>  wregex (Definición de tipo)

Definición de tipo para basic_regex de wchar_t.

```cpp
typedef basic_regex<wchar_t> wregex;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [basic_regex (clase)](../standard-library/basic-regex-class.md) elementos del tipo **wchar_t**.

## <a name="wsmatch"></a>  wsmatch (Definición de tipo)

Definición de tipo para match_results de wstring.

```cpp
typedef match_results<wstring::const_iterator> wsmatch;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [match_results (Clase)](../standard-library/match-results-class.md) para iteradores del tipo `wstring::const_iterator`.

## <a name="wsregex_iterator"></a>  wsregex_iterator (Definición de tipo)

Definición de tipo para regex_iterator de wstring.

```cpp
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [regex_iterator (Clase)](../standard-library/regex-iterator-class.md) para iteradores del tipo `wstring::const_iterator`.

## <a name="wsregex_token_iterator"></a>  wsregex_token_iterator (Definición de tipo)

Definición de tipo para regex_token_iterator de wstring.

```cpp
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [regex_token_iterator (Clase)](../standard-library/regex-token-iterator-class.md) para iteradores del tipo `wstring::const_iterator`.

## <a name="wssub_match"></a>  wssub_match (Definición de tipo)

Definición de tipo de wstring sub_match.

```cpp
typedef sub_match<wstring::const_iterator> wssub_match;
```

### <a name="remarks"></a>Comentarios

El tipo describe una especialización de clase de plantilla [sub_match (Clase)](../standard-library/sub-match-class.md) para iteradores del tipo `wstring::const_iterator`.

## <a name="see-also"></a>Vea también

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants (Clase)](../standard-library/regex-constants-class.md)<br/>
[regex_error (Clase)](../standard-library/regex-error-class.md)<br/>
[Funciones de \<regex>](../standard-library/regex-functions.md)<br/>
[regex_iterator (Clase)](../standard-library/regex-iterator-class.md)<br/>
[Operadores de \<regex>](../standard-library/regex-operators.md)<br/>
[regex_token_iterator (Clase)](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits (Clase)](../standard-library/regex-traits-class.md)<br/>
