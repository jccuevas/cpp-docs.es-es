---
title: "&lt;regex&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<regex>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "regex (encabezado) [TR1]"
ms.assetid: 5dd4ef74-6063-4dbc-b692-1960bb736f0b
caps.latest.revision: 23
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;regex&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define una clase de plantilla para analizar [Expresiones regulares \(C\+\+\)](../standard-library/regular-expressions-cpp.md) y varias clases de plantilla y funciones para buscar texto que coincida con un objeto de expresión regular.  
  
## Sintaxis  
  
```  
#include <regex>  
```  
  
## Comentarios  
 Para crear un objeto de expresión regular, use la clase de plantilla [basic\_regex \(Clase\)](../standard-library/basic-regex-class.md) o una de sus especializaciones, [regex \(Typedef\)](../Topic/regex%20Typedef.md) y [wregex \(Typedef\)](../Topic/wregex%20Typedef.md), junto con las marcas de la sintaxis de tipo [regex\_constants::syntax\_option\_type](../Topic/regex_constants::syntax_option_type.md).  
  
 Para buscar texto que coincida con un objeto de expresión regular, utilice las funciones de plantilla [regex\_match \(Función\)](../Topic/regex_match%20Function.md) y [regex\_search \(Función\)](../Topic/regex_search%20Function.md), junto con las marcas de coincidencia de tipo [regex\_constants::match\_flag\_type](../Topic/regex_constants::match_flag_type.md).  Estas funciones devuelven resultados mediante el uso de la clase de plantilla [match\_results \(Clase\)](../standard-library/match-results-class.md) y sus especializaciones, [cmatch \(Typedef\)](../Topic/cmatch%20Typedef.md), [wcmatch \(Typedef\)](../Topic/wcmatch%20Typedef.md), [smatch \(Typedef\)](../Topic/smatch%20Typedef.md) y [wsmatch \(Typedef\)](../Topic/wsmatch%20Typedef.md), junto con la clase de plantilla [sub\_match \(Clase\)](../standard-library/sub-match-class.md) y sus especializaciones, [csub\_match \(Typedef\)](../Topic/csub_match%20Typedef.md), [wcsub\_match \(Typedef\)](../Topic/wcsub_match%20Typedef.md), [ssub\_match \(Typedef\)](../Topic/ssub_match%20Typedef.md) y [wssub\_match \(Typedef\)](../Topic/wssub_match%20Typedef.md).  
  
 Para reemplazar texto que coincida con un objeto de expresión regular, utilice la función de plantilla [regex\_replace \(Función\)](../Topic/regex_replace%20Function.md), junto con las marcas de coincidencia de tipo [regex\_constants::match\_flag\_type](../Topic/regex_constants::match_flag_type.md).  
  
 Para procesar una iteración en varias coincidencias de un objeto de expresión regular, use las clases de plantilla [regex\_iterator \(Clase\)](../standard-library/regex-iterator-class.md) y [regex\_token\_iterator \(Clase\)](../standard-library/regex-token-iterator-class.md) o una de sus especializaciones, [cregex\_iterator \(Typedef\)](../Topic/cregex_iterator%20Typedef.md), [sregex\_iterator \(Typedef\)](../Topic/sregex_iterator%20Typedef.md), [wcregex\_iterator \(Typedef\)](../Topic/wcregex_iterator%20Typedef.md), [wsregex\_iterator \(Typedef\)](../Topic/wsregex_iterator%20Typedef.md), [cregex\_token\_iterator \(Typedef\)](../Topic/cregex_token_iterator%20Typedef.md), [sregex\_token\_iterator \(Typedef\)](../Topic/sregex_token_iterator%20Typedef.md), [wcregex\_token\_iterator \(Typedef\)](../Topic/wcregex_token_iterator%20Typedef.md) o [wsregex\_token\_iterator \(Typedef\)](../Topic/wsregex_token_iterator%20Typedef.md), junto con las marcas de coincidencia de tipo [regex\_constants::match\_flag\_type](../Topic/regex_constants::match_flag_type.md).  
  
 Para modificar los detalles de la gramática de expresiones regulares, escriba una clase que implemente los rasgos de expresiones regulares.  
  
### Clases  
  
|||  
|-|-|  
|[basic\_regex](../standard-library/basic-regex-class.md)|Contiene una expresión regular.|  
|[match\_results](../standard-library/match-results-class.md)|Contiene una secuencia de subcoincidencias.|  
|[regex\_constants](../standard-library/regex-constants-class.md)|Contiene constantes ordenadas.|  
|[regex\_error](../standard-library/regex-error-class.md)|Notifica la existencia de una expresión regular no válida.|  
|[regex\_iterator](../standard-library/regex-iterator-class.md)|Procesa una iteración por los resultados de la coincidencia.|  
|[regex\_traits](../standard-library/regex-traits-class.md)|Describe las características de los elementos para buscar coincidencias.|  
|[regex\_traits\<char\>](../standard-library/regex-traits-char-class.md)|Describe las características de `char` para buscar coincidencias.|  
|[regex\_traits\<wchar\_t\>](../standard-library/regex-traits-wchar-t-class.md)|Describe las características de `wchar_t` para buscar coincidencias.|  
|[regex\_token\_iterator](../standard-library/regex-token-iterator-class.md)|Procesa una iteración en las subcoincidencias.|  
|[sub\_match](../standard-library/sub-match-class.md)|Describe a una subcoincidencia.|  
  
### Definiciones de tipos  
  
|||  
|-|-|  
|[cmatch](../Topic/cmatch%20Typedef.md)|Definición de tipo de `char` `match_results`.|  
|[cregex\_iterator](../Topic/cregex_iterator%20Typedef.md)|Definición de tipo de `char` `regex_iterator`.|  
|[cregex\_token\_iterator](../Topic/cregex_token_iterator%20Typedef.md)|Definición de tipo de `char` `regex_token_iterator`.|  
|[csub\_match](../Topic/csub_match%20Typedef.md)|Definición de tipo de `char` `sub_match`.|  
|[regex](../Topic/regex%20Typedef.md)|Definición de tipo de `char` `basic_regex`.|  
|[smatch](../Topic/smatch%20Typedef.md)|Definición de tipo de `string` `match_results`.|  
|[sregex\_iterator](../Topic/sregex_iterator%20Typedef.md)|Definición de tipo de `string` `regex_iterator`.|  
|[sregex\_token\_iterator](../Topic/sregex_token_iterator%20Typedef.md)|Definición de tipo de `string` `regex_token_iterator`.|  
|[ssub\_match](../Topic/ssub_match%20Typedef.md)|Definición de tipo de `string` `sub_match`.|  
|[wcmatch](../Topic/wcmatch%20Typedef.md)|Definición de tipo de `wchar_t` `match_results`.|  
|[wcregex\_iterator](../Topic/wcregex_iterator%20Typedef.md)|Definición de tipo de `wchar_t` `regex_iterator`.|  
|[wcregex\_token\_iterator](../Topic/wcregex_token_iterator%20Typedef.md)|Definición de tipo de `wchar_t` `regex_token_iterator`.|  
|[wcsub\_match](../Topic/wcsub_match%20Typedef.md)|Definición de tipo de `wchar_t` `sub_match`.|  
|[wregex](../Topic/wregex%20Typedef.md)|Definición de tipo de `wchar_t` `basic_regex`.|  
|[wsmatch](../Topic/wsmatch%20Typedef.md)|Definición de tipo de `wstring` `match_results`.|  
|[wsregex\_iterator](../Topic/wsregex_iterator%20Typedef.md)|Definición de tipo de `wstring` `regex_iterator`.|  
|[wsregex\_token\_iterator](../Topic/wsregex_token_iterator%20Typedef.md)|Definición de tipo de `wstring` `regex_token_iterator`.|  
|[wssub\_match](../Topic/wssub_match%20Typedef.md)|Definición de tipo de `wstring` `sub_match`.|  
  
### Funciones  
  
|||  
|-|-|  
|[regex\_match](../Topic/regex_match%20Function.md)|Coincide por completo con una expresión regular.|  
|[regex\_replace](../Topic/regex_replace%20Function.md)|Reemplaza las expresiones regulares que coincidan.|  
|[regex\_search](../Topic/regex_search%20Function.md)|Busca una coincidencia con la expresión regular.|  
|[swap](../Topic/swap%20Function%20%3Cregex%3E.md)|Intercambia los objetos `basic_regex` o `match_results`.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\=\=](../Topic/operator==%20%3Cregex%3E.md)|Comparación de varios objetos, igual.|  
|[operator\!\=](../Topic/operator!=%20%3Cregex%3E.md)|Comparación de desigualdad de varios objetos.|  
|[operador \<](../Topic/operator%3C%20%3Cregex%3E.md)|Comparación de varios objetos, no igual.|  
|[operator\<\=](../Topic/operator%3C=%20%3Cregex%3E.md)|Comparación de varios objetos, menor o igual que.|  
|[operador \>](../Topic/operator%3E%20%3Cregex%3E.md)|Comparación de varios objetos, mayor que.|  
|[operator\>\=](../Topic/operator%3E=%20%3Cregex%3E.md)|Comparación de varios objetos, mayor o igual que.|  
|[operador \<\<](../Topic/operator%3C%3C%20%3Cregex%3E.md)|Inserta un `sub_match` en una secuencia.|  
  
## Vea también  
 [Expresiones regulares \(C\+\+\)](../standard-library/regular-expressions-cpp.md)