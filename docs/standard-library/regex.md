---
title: '&lt;regex&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <regex>
dev_langs:
- C++
helpviewer_keywords:
- regex header
ms.assetid: 5dd4ef74-6063-4dbc-b692-1960bb736f0b
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 248e9ba676b906af62f6804f4939e04158a8e2ef
ms.openlocfilehash: 4e172f8bf72fd528027c333cf411a307aa97d786
ms.lasthandoff: 02/24/2017

---
# <a name="ltregexgt"></a>&lt;regex&gt;
Define una clase de plantilla para analizar [Expresiones regulares (C++)](../standard-library/regular-expressions-cpp.md) y varias clases de plantilla y funciones para buscar texto que coincida con un objeto de expresión regular.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#include <regex>  
```  
  
## <a name="remarks"></a>Comentarios  
 Para crear un objeto de expresión regular, use la clase de plantilla [basic_regex](../standard-library/basic-regex-class.md) o una de sus especializaciones, [regex](../standard-library/regex-typedefs.md#regex_typedef) y [wregex](../standard-library/regex-typedefs.md#wregex_typedef), junto con las marcas de sintaxis de tipo [regex_constants::syntax_option_type](../standard-library/regex-constants-class.md#regex_constants__syntax_option_type).  
  
 Para buscar texto que coincida con un objeto de expresión regular, use las funciones de plantilla [regex_match (función)](../standard-library/regex-functions.md#regex_match_function) y [regex_search (función)](../standard-library/regex-functions.md#regex_search_function), junto con las marcas de coincidencia de tipo [regex_constants::match_flag_type](../standard-library/regex-constants-class.md#regex_constants__match_flag_type). Estas funciones devuelven resultados mediante el uso de la clase de plantilla [match_results (Clase)](../standard-library/match-results-class.md) y sus especializaciones, [cmatch](../standard-library/regex-typedefs.md#cmatch_typedef), [wcmatch](../standard-library/regex-typedefs.md#wcmatch_typedef), [smatch](../standard-library/regex-typedefs.md#smatch_typedef) y [wsmatch](../standard-library/regex-typedefs.md#wsmatch_typedef), junto con la clase de plantilla [sub_match (Clase)](../standard-library/sub-match-class.md) y sus especializaciones, [csub_match](../standard-library/regex-typedefs.md#csub_match_typedef), [wcsub_match](../standard-library/regex-typedefs.md#wcsub_match_typedef), [ssub_match](../standard-library/regex-typedefs.md#ssub_match_typedef) y [wssub_match](../standard-library/regex-typedefs.md#wssub_match_typedef).  
  
 Para reemplazar texto que coincida con un objeto de expresión regular, use la función de plantilla [regex_replace (Función)](../standard-library/regex-functions.md#regex_replace_function), junto con las marcas de coincidencia de tipo [regex_constants::match_flag_type](../standard-library/regex-constants-class.md#regex_constants__match_flag_type).  
  
 Para procesar una iteración en varias coincidencias de un objeto de expresión regular, use las clases de plantilla [regex_iterator (Clase)](../standard-library/regex-iterator-class.md) y [regex_token_iterator (Clase)](../standard-library/regex-token-iterator-class.md) o una de sus especializaciones, [cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator_typedef), [sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator_typedef), [wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator_typedef), [wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator_typedef), [cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator_typedef), [sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator_typedef), [wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator_typedef) o [wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator_typedef), junto con las marcas de coincidencia de tipo [regex_constants::match_flag_type](../standard-library/regex-constants-class.md#regex_constants__match_flag_type).  
  
 Para modificar los detalles de la gramática de expresiones regulares, escriba una clase que implemente los rasgos de expresiones regulares.  
  
### <a name="classes"></a>Clases  
  
|||  
|-|-|  
|[basic_regex](../standard-library/basic-regex-class.md)|Contiene una expresión regular.|  
|[match_results](../standard-library/match-results-class.md)|Contiene una secuencia de subcoincidencias.|  
|[regex_constants](../standard-library/regex-constants-class.md)|Contiene constantes ordenadas.|  
|[regex_error](../standard-library/regex-error-class.md)|Notifica la existencia de una expresión regular no válida.|  
|[regex_iterator](../standard-library/regex-iterator-class.md)|Procesa una iteración por los resultados de la coincidencia.|  
|[regex_traits](../standard-library/regex-traits-class.md)|Describe las características de los elementos para buscar coincidencias.|  
|[regex_traits\<char>](../standard-library/regex-traits-char-class.md)|Describe las características de `char` para buscar coincidencias.|  
|[regex_traits<wchar_t>](../standard-library/regex-traits-wchar-t-class.md)|Describe las características de `wchar_t` para buscar coincidencias.|  
|[regex_token_iterator](../standard-library/regex-token-iterator-class.md)|Procesa una iteración en las subcoincidencias.|  
|[sub_match](../standard-library/sub-match-class.md)|Describe a una subcoincidencia.|  
  
### <a name="type-definitions"></a>Definiciones de tipos  
  
|||  
|-|-|  
|[cmatch](../standard-library/regex-typedefs.md#cmatch_typedef)|Definición de tipo de `char``match_results`.|  
|[cregex_iterator](../standard-library/regex-typedefs.md#cregex_iterator_typedef)|Definición de tipo de `char``regex_iterator`.|  
|[cregex_token_iterator](../standard-library/regex-typedefs.md#cregex_token_iterator_typedef)|Definición de tipo de `char``regex_token_iterator`.|  
|[csub_match](../standard-library/regex-typedefs.md#csub_match_typedef)|Definición de tipo de `char``sub_match`.|  
|[regex](../standard-library/regex-typedefs.md#regex_typedef)|Definición de tipo de `char``basic_regex`.|  
|[smatch](../standard-library/regex-typedefs.md#smatch_typedef)|Definición de tipo de `string``match_results`.|  
|[sregex_iterator](../standard-library/regex-typedefs.md#sregex_iterator_typedef)|Definición de tipo de `string``regex_iterator`.|  
|[sregex_token_iterator](../standard-library/regex-typedefs.md#sregex_token_iterator_typedef)|Definición de tipo de `string``regex_token_iterator`.|  
|[ssub_match](../standard-library/regex-typedefs.md#ssub_match_typedef)|Definición de tipo de `string``sub_match`.|  
|[wcmatch](../standard-library/regex-typedefs.md#wcmatch_typedef)|Definición de tipo de `wchar_t``match_results`.|  
|[wcregex_iterator](../standard-library/regex-typedefs.md#wcregex_iterator_typedef)|Definición de tipo de `wchar_t``regex_iterator`.|  
|[wcregex_token_iterator](../standard-library/regex-typedefs.md#wcregex_token_iterator_typedef)|Definición de tipo de `wchar_t``regex_token_iterator`.|  
|[wcsub_match](../standard-library/regex-typedefs.md#wcsub_match_typedef)|Definición de tipo de `wchar_t``sub_match`.|  
|[wregex](../standard-library/regex-typedefs.md#wregex_typedef)|Definición de tipo de `wchar_t``basic_regex`.|  
|[wsmatch](../standard-library/regex-typedefs.md#wsmatch_typedef)|Definición de tipo de `wstring``match_results`.|  
|[wsregex_iterator](../standard-library/regex-typedefs.md#wsregex_iterator_typedef)|Definición de tipo de `wstring``regex_iterator`.|  
|[wsregex_token_iterator](../standard-library/regex-typedefs.md#wsregex_token_iterator_typedef)|Definición de tipo de `wstring``regex_token_iterator`.|  
|[wssub_match](../standard-library/regex-typedefs.md#wssub_match_typedef)|Definición de tipo de `wstring``sub_match`.|  
  
### <a name="functions"></a>Funciones  
  
|||  
|-|-|  
|[regex_match](../standard-library/regex-functions.md#regex_match_function)|Coincide por completo con una expresión regular.|  
|[regex_replace](../standard-library/regex-functions.md#regex_replace_function)|Reemplaza las expresiones regulares que coincidan.|  
|[regex_search](../standard-library/regex-functions.md#regex_search_function)|Busca una coincidencia con la expresión regular.|  
|[swap](../standard-library/regex-functions.md#swap_function)|Intercambia los objetos `basic_regex` o `match_results`.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator==](../standard-library/regex-operators.md#operator_eq_eq)|Comparación de varios objetos, igual.|  
|[operator!=](../standard-library/regex-operators.md#operator_neq)|Comparación de desigualdad de varios objetos.|  
|[operator<](../standard-library/regex-operators.md#operator_lt_)|Comparación de varios objetos, no igual.|  
|[operator\<=](../standard-library/regex-operators.md#operator_lt__eq)|Comparación de varios objetos, menor o igual que.|  
|[operator>](../standard-library/regex-operators.md#operator_gt_)|Comparación de varios objetos, mayor que.|  
|[operator>=](../standard-library/regex-operators.md#operator_gt__eq)|Comparación de varios objetos, mayor o igual que.|  
|[operator<<](../standard-library/regex-operators.md#operator_lt__lt_)|Inserta un `sub_match` en una secuencia.|  
  
## <a name="see-also"></a>Vea también  
[Expresiones regulares (C++)](../standard-library/regular-expressions-cpp.md)  
[regex_constants (Clase)](../standard-library/regex-constants-class.md)  
[regex_error (Clase)](../standard-library/regex-error-class.md)  
[Funciones de \<regex>](../standard-library/regex-functions.md)  
[regex_iterator (Clase)](../standard-library/regex-iterator-class.md)  
[Operadores de \<regex>](../standard-library/regex-operators.md)  
[regex_token_iterator (Clase)](../standard-library/regex-token-iterator-class.md)  
[regex_traits (Clase)](../standard-library/regex-traits-class.md)  
[Definiciones de tipo \<regex>](../standard-library/regex-typedefs.md)  




