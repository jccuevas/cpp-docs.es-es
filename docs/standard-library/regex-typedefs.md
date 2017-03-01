---
title: Definiciones de tipo de &lt;regex&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cmatch
- std::cmatch
- regex/std::cmatch
- cregex_iterator
- std::cregex_iterator
- regex/std::cregex_iterator
- cregex_token_iterator
- std::cregex_token_iterator
- regex/std::cregex_token_iterator
- csub_match
- std::csub_match
- regex/std::csub_match
- regex
- std::regex
- regex/std::regex
- smatch
- std::smatch
- regex/std::smatch
- sregex_iterator
- std::sregex_iterator
- regex/std::sregex_iterator
- sregex_token_iterator
- std::sregex_token_iterator
- regex/std::sregex_token_iterator
- ssub_match
- std::ssub_match
- regex/std::ssub_match
- wcmatch
- std::wcmatch
- regex/std::wcmatch
- wcregex_iterator
- std::wcregex_iterator
- regex/std::wcregex_iterator
- wcregex_token_iterator
- std::wcregex_token_iterator
- regex/std::wcregex_token_iterator
- wcsub_match
- std::wcsub_match
- regex/std::wcsub_match
- wregex
- std::wregex
- regex/std::wregex
- wsmatch
- std::wsmatch
- regex/std::wsmatch
- wsregex_iterator
- std::wsregex_iterator
- regex/std::wsregex_iterator
- wsregex_token_iterator
- std::wsregex_token_iterator
- regex/std::wsregex_token_iterator
- wssub_match
- std::wssub_match
- regex/std::wssub_match
ms.assetid: e6a69067-106c-4a24-9e08-7c867a3a2260
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 41b445ceeeb1f37ee9873cb55f62d30d480d8718
ms.openlocfilehash: 60822dd232399b27ccda3db829b636d817091a2d
ms.lasthandoff: 02/24/2017

---
# <a name="ltregexgt-typedefs"></a>Definiciones de tipo de &lt;regex&gt;
||||  
|-|-|-|  
|[cmatch (Definición de tipo)](#cmatch_typedef)|[cregex_iterator (Definición de tipo)](#cregex_iterator_typedef)|[cregex_token_iterator (Definición de tipo)](#cregex_token_iterator_typedef)|  
|[csub_match (Definición de tipo)](#csub_match_typedef)|[regex (Definición de tipo)](#regex_typedef)|[smatch (Definición de tipo)](#smatch_typedef)|  
|[sregex_iterator (Definición de tipo)](#sregex_iterator_typedef)|[sregex_token_iterator (Definición de tipo)](#sregex_token_iterator_typedef)|[ssub_match (Definición de tipo)](#ssub_match_typedef)|  
|[wcmatch (Definición de tipo)](#wcmatch_typedef)|[wcregex_iterator (Definición de tipo)](#wcregex_iterator_typedef)|[wcregex_token_iterator (Definición de tipo)](#wcregex_token_iterator_typedef)|  
|[wcsub_match (Definición de tipo)](#wcsub_match_typedef)|[wregex (Definición de tipo)](#wregex_typedef)|[wsmatch (Definición de tipo)](#wsmatch_typedef)|  
|[wsregex_iterator (Definición de tipo)](#wsregex_iterator_typedef)|[wsregex_token_iterator (Definición de tipo)](#wsregex_token_iterator_typedef)|[wssub_match (Definición de tipo)](#wssub_match_typedef)|  
  
##  <a name="a-namecmatchtypedefa--cmatch-typedef"></a><a name="cmatch_typedef"></a>  cmatch (Definición de tipo)  
 Tipo de definición de char match_results.  
  
```  
typedef match_results<const char*> cmatch;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [match_results (Clase)](../standard-library/match-results-class.md) para iteradores del tipo `const char*`.  
  
##  <a name="a-namecregexiteratortypedefa--cregexiterator-typedef"></a><a name="cregex_iterator_typedef"></a>  cregex_iterator (Definición de tipo)  
 Definición de tipo para regex_iterator de char.  
  
```  
typedef regex_iterator<const char*> cregex_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [regex_iterator (Clase)](../standard-library/regex-iterator-class.md) para iteradores del tipo `const char*`.  
  
##  <a name="a-namecregextokeniteratortypedefa--cregextokeniterator-typedef"></a><a name="cregex_token_iterator_typedef"></a>  cregex_token_iterator (Definición de tipo)  
 Definición de tipo para regex_token_iterator de char  
  
```  
typedef regex_token_iterator<const char*> cregex_token_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [regex_token_iterator (Clase)](../standard-library/regex-token-iterator-class.md) para iteradores del tipo `const char*`.  
  
##  <a name="a-namecsubmatchtypedefa--csubmatch-typedef"></a><a name="csub_match_typedef"></a>  csub_match (Definición de tipo)  
 Definición de tipo para sub_match de char.  
  
```  
typedef sub_match<const char*> csub_match;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [sub_match (Clase)](../standard-library/sub-match-class.md) para iteradores del tipo `const char*`.  
  
##  <a name="a-nameregextypedefa--regex-typedef"></a><a name="regex_typedef"></a>  regex (Definición de tipo)  
 Definición de tipo para basic_regex de char.  
  
```  
typedef basic_regex<char> regex;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [basic_regex (Clase)](../standard-library/basic-regex-class.md) para iteradores del tipo `char`.  
  
> [!NOTE]
>  Los caracteres ASCII de&8; bits tendrán resultados imprevisibles con `regex`. Los valores fuera del intervalo de 0 a 127 pueden producir un comportamiento indefinido.  
  
##  <a name="a-namesmatchtypedefa--smatch-typedef"></a><a name="smatch_typedef"></a>  smatch (Definición de tipo)  
 Definición de tipo de regex_iterator de string.  
  
```  
typedef match_results<string::const_iterator> smatch;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [match_results (Clase)](../standard-library/match-results-class.md) para iteradores del tipo `string::const_iterator`.  
  
##  <a name="a-namesregexiteratortypedefa--sregexiterator-typedef"></a><a name="sregex_iterator_typedef"></a>  sregex_iterator (Definición de tipo)  
 Definición de tipo de string regex_iterator.  
  
```  
typedef regex_iterator<string::const_iterator> sregex_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [regex_iterator (Clase)](../standard-library/regex-iterator-class.md) para iteradores del tipo `string::const_iterator`.  
  
##  <a name="a-namesregextokeniteratortypedefa--sregextokeniterator-typedef"></a><a name="sregex_token_iterator_typedef"></a>  sregex_token_iterator (Definición de tipo)  
 Definición de tipo para regex_token_iterator de string.  
  
```  
typedef regex_token_iterator<string::const_iterator> sregex_token_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [regex_token_iterator (Clase)](../standard-library/regex-token-iterator-class.md) para iteradores del tipo `string::const_iterator`.  
  
##  <a name="a-namessubmatchtypedefa--ssubmatch-typedef"></a><a name="ssub_match_typedef"></a>  ssub_match (Definición de tipo)  
 Definición de tipo para sub_match de string.  
  
```  
typedef sub_match<string::const_iterator> ssub_match;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [sub_match (Clase)](../standard-library/sub-match-class.md) para iteradores del tipo `string::const_iterator`.  
  
##  <a name="a-namewcmatchtypedefa--wcmatch-typedef"></a><a name="wcmatch_typedef"></a>  wcmatch (Definición de tipo)  
 Definición de tipo para match_results de wchar_t.  
  
```  
typedef match_results<const wchar_t *> wcmatch;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [match_results (Clase)](../standard-library/match-results-class.md) para iteradores del tipo `const wchar_t*`.  
  
##  <a name="a-namewcregexiteratortypedefa--wcregexiterator-typedef"></a><a name="wcregex_iterator_typedef"></a>  wcregex_iterator (Definición de tipo)  
 Definición de tipo para wchar_t regex_iterator.  
  
```  
typedef regex_iterator<const wchar_t*> wcregex_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [regex_iterator (Clase)](../standard-library/regex-iterator-class.md) para iteradores del tipo `const wchar_t*`.  
  
##  <a name="a-namewcregextokeniteratortypedefa--wcregextokeniterator-typedef"></a><a name="wcregex_token_iterator_typedef"></a>  wcregex_token_iterator (Definición de tipo)  
 Definición de tipo para regex_token_iterator de wchar_t.  
  
```  
typedef regex_token_iterator<const wchar_t*> wcregex_token_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [regex_token_iterator (Clase)](../standard-library/regex-token-iterator-class.md) para iteradores del tipo `const wchar_t*`.  
  
##  <a name="a-namewcsubmatchtypedefa--wcsubmatch-typedef"></a><a name="wcsub_match_typedef"></a>  wcsub_match (Definición de tipo)  
 Definición de tipo para sub_match de wchar_t.  
  
```  
typedef sub_match<const wchar_t*> wcsub_match;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [sub_match (Clase)](../standard-library/sub-match-class.md) para iteradores del tipo `const wchar_t*`.  
  
##  <a name="a-namewregextypedefa--wregex-typedef"></a><a name="wregex_typedef"></a>  wregex (Definición de tipo)  
 Definición de tipo para basic_regex de wchar_t.  
  
```  
typedef basic_regex<wchar_t> wregex;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [basic_regex (Clase)](../standard-library/basic-regex-class.md) para iteradores del tipo `wchar_t`.  
  
##  <a name="a-namewsmatchtypedefa--wsmatch-typedef"></a><a name="wsmatch_typedef"></a>  wsmatch (Definición de tipo)  
 Definición de tipo para match_results de wstring.  
  
```  
typedef match_results<wstring::const_iterator> wsmatch;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [match_results (Clase)](../standard-library/match-results-class.md) para iteradores del tipo `wstring::const_iterator`.  
  
##  <a name="a-namewsregexiteratortypedefa--wsregexiterator-typedef"></a><a name="wsregex_iterator_typedef"></a>  wsregex_iterator (Definición de tipo)  
 Definición de tipo para regex_iterator de wstring.  
  
```  
typedef regex_iterator<wstring::const_iterator> wsregex_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [regex_iterator (Clase)](../standard-library/regex-iterator-class.md) para iteradores del tipo `wstring::const_iterator`.  
  
##  <a name="a-namewsregextokeniteratortypedefa--wsregextokeniterator-typedef"></a><a name="wsregex_token_iterator_typedef"></a>  wsregex_token_iterator (Definición de tipo)  
 Definición de tipo para regex_token_iterator de wstring.  
  
```  
typedef regex_token_iterator<wstring::const_iterator> wsregex_token_iterator;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [regex_token_iterator (Clase)](../standard-library/regex-token-iterator-class.md) para iteradores del tipo `wstring::const_iterator`.  
  
##  <a name="a-namewssubmatchtypedefa--wssubmatch-typedef"></a><a name="wssub_match_typedef"></a>  wssub_match (Definición de tipo)  
 Definición de tipo de wstring sub_match.  
  
```  
typedef sub_match<wstring::const_iterator> wssub_match;  
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe una especialización de clase de plantilla [sub_match (Clase)](../standard-library/sub-match-class.md) para iteradores del tipo `wstring::const_iterator`.  
  
## <a name="see-also"></a>Vea también  
[\<regex>](../standard-library/regex.md)  
[regex_constants (Clase)](../standard-library/regex-constants-class.md)  
[regex_error (Clase)](../standard-library/regex-error-class.md)  
[Funciones de \<regex>](../standard-library/regex-functions.md)  
[regex_iterator (Clase)](../standard-library/regex-iterator-class.md)  
[Operadores de \<regex>](../standard-library/regex-operators.md)  
[regex_token_iterator (Clase)](../standard-library/regex-token-iterator-class.md)  
[regex_traits (Clase)](../standard-library/regex-traits-class.md)  

