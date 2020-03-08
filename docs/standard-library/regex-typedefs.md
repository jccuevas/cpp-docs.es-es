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
ms.openlocfilehash: 4321d9ea6fd9ba57074b25e084553fe1f0846213
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876153"
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

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de clase de [match_results](../standard-library/match-results-class.md) de plantilla de clase para iteradores de tipo `const char*`.

## <a name="cregex_iterator"></a>  cregex_iterator (Definición de tipo)

Definición de tipo para regex_iterator de char.

```cpp
typedef regex_iterator<const char*> cregex_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de clase de [regex_iterator](../standard-library/regex-iterator-class.md) de plantilla de clase para iteradores de tipo `const char*`.

## <a name="cregex_token_iterator"></a>  cregex_token_iterator (Definición de tipo)

Definición de tipo para regex_token_iterator de char

```cpp
typedef regex_token_iterator<const char*> cregex_token_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de clase de [regex_token_iterator](../standard-library/regex-token-iterator-class.md) de plantilla de clase para iteradores de tipo `const char*`.

## <a name="csub_match"></a>  csub_match (Definición de tipo)

Definición de tipo para sub_match de char.

```cpp
typedef sub_match<const char*> csub_match;
```

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de clase de [sub_match](../standard-library/sub-match-class.md) de plantilla de clase para iteradores de tipo `const char*`.

## <a name="regex"></a>  regex (Definición de tipo)

Definición de tipo para basic_regex de char.

```cpp
typedef basic_regex<char> regex;
```

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de la clase de [basic_regex](../standard-library/basic-regex-class.md) de plantilla de clase para los elementos de tipo **Char**.

> [!NOTE]
> Los caracteres ASCII de 8 bits tendrán resultados imprevisibles con `regex`. Los valores fuera del intervalo de 0 a 127 pueden producir un comportamiento indefinido.

## <a name="smatch"></a>  smatch (Definición de tipo)

Definición de tipo de regex_iterator de string.

```cpp
typedef match_results<string::const_iterator> smatch;
```

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de clase de [match_results](../standard-library/match-results-class.md) de plantilla de clase para iteradores de tipo `string::const_iterator`.

## <a name="sregex_iterator"></a>  sregex_iterator (Definición de tipo)

Definición de tipo de string regex_iterator.

```cpp
typedef regex_iterator<string::const_iterator> sregex_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de clase de [regex_iterator](../standard-library/regex-iterator-class.md) de plantilla de clase para iteradores de tipo `string::const_iterator`.

## <a name="sregex_token_iterator"></a>  sregex_token_iterator (Definición de tipo)

Definición de tipo para regex_token_iterator de string.

```cpp
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de clase de [regex_token_iterator](../standard-library/regex-token-iterator-class.md) de plantilla de clase para iteradores de tipo `string::const_iterator`.

## <a name="ssub_match"></a>  ssub_match (Definición de tipo)

Definición de tipo para sub_match de string.

```cpp
typedef sub_match<string::const_iterator> ssub_match;
```

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de clase de [sub_match](../standard-library/sub-match-class.md) de plantilla de clase para iteradores de tipo `string::const_iterator`.

## <a name="wcmatch"></a>  wcmatch (Definición de tipo)

Definición de tipo para match_results de wchar_t.

```cpp
typedef match_results<const wchar_t *> wcmatch;
```

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de clase de [match_results](../standard-library/match-results-class.md) de plantilla de clase para iteradores de tipo `const wchar_t*`.

## <a name="wcregex_iterator"></a>  wcregex_iterator (Definición de tipo)

Definición de tipo para wchar_t regex_iterator.

```cpp
typedef regex_iterator<const wchar_t*> wcregex_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de clase de [regex_iterator](../standard-library/regex-iterator-class.md) de plantilla de clase para iteradores de tipo `const wchar_t*`.

## <a name="wcregex_token_iterator"></a>  wcregex_token_iterator (Definición de tipo)

Definición de tipo para regex_token_iterator de wchar_t.

```cpp
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de clase de [regex_token_iterator](../standard-library/regex-token-iterator-class.md) de plantilla de clase para iteradores de tipo `const wchar_t*`.

## <a name="wcsub_match"></a>  wcsub_match (Definición de tipo)

Definición de tipo para sub_match de wchar_t.

```cpp
typedef sub_match<const wchar_t*> wcsub_match;
```

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de clase de [sub_match](../standard-library/sub-match-class.md) de plantilla de clase para iteradores de tipo `const wchar_t*`.

## <a name="wregex"></a>  wregex (Definición de tipo)

Definición de tipo para basic_regex de wchar_t.

```cpp
typedef basic_regex<wchar_t> wregex;
```

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de clase de [basic_regex](../standard-library/basic-regex-class.md) de plantilla de clase para los elementos de tipo **wchar_t**.

## <a name="wsmatch"></a>  wsmatch (Definición de tipo)

Definición de tipo para match_results de wstring.

```cpp
typedef match_results<wstring::const_iterator> wsmatch;
```

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de clase de [match_results](../standard-library/match-results-class.md) de plantilla de clase para iteradores de tipo `wstring::const_iterator`.

## <a name="wsregex_iterator"></a>  wsregex_iterator (Definición de tipo)

Definición de tipo para regex_iterator de wstring.

```cpp
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de clase de [regex_iterator](../standard-library/regex-iterator-class.md) de plantilla de clase para iteradores de tipo `wstring::const_iterator`.

## <a name="wsregex_token_iterator"></a>  wsregex_token_iterator (Definición de tipo)

Definición de tipo para regex_token_iterator de wstring.

```cpp
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;
```

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de clase de [regex_token_iterator](../standard-library/regex-token-iterator-class.md) de plantilla de clase para iteradores de tipo `wstring::const_iterator`.

## <a name="wssub_match"></a>  wssub_match (Definición de tipo)

Definición de tipo de wstring sub_match.

```cpp
typedef sub_match<wstring::const_iterator> wssub_match;
```

### <a name="remarks"></a>Observaciones

El tipo describe una especialización de clase de [sub_match](../standard-library/sub-match-class.md) de plantilla de clase para iteradores de tipo `wstring::const_iterator`.

## <a name="see-also"></a>Consulte también

[\<regex>](../standard-library/regex.md)\
[Regex_constants clase](../standard-library/regex-constants-class.md)\
[Regex_error clase](../standard-library/regex-error-class.md)\
[\<las funciones > regex](../standard-library/regex-functions.md)\
[Regex_iterator clase](../standard-library/regex-iterator-class.md)\
[\<operadores > regex](../standard-library/regex-operators.md)\
[Regex_token_iterator clase](../standard-library/regex-token-iterator-class.md)\
[regex_traits (Clase)](../standard-library/regex-traits-class.md)
