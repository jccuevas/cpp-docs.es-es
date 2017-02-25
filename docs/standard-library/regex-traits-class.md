---
title: "regex_traits (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "regex_traits"
  - "std::tr1::regex_traits"
  - "std.tr1.regex_traits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "regex_traits (clase) [TR1]"
ms.assetid: bc5a5eed-32fc-4eb7-913d-71c42e729e81
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# regex_traits (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe las características de los elementos para buscar coincidencias.  
  
## Sintaxis  
  
```  
template<class Elem>  
    struct regex_traits {  
    regex_traits();  
  
    static size_type length(const char_type *str);  
    char_type translate(char_type ch) const;  
    char_type translate_nocase(char_type ch) const;  
    template<class FwdIt>  
        string_type transform(FwdIt first, FwdIt last) const;  
    template<class FwdIt>  
        string_type transform_primary(FwdIt first, FwdIt last) const;  
    template<class FwdIt>  
        char_class_type lookup_classname(FwdIt first, FwdIt last) const;  
    template<class FwdIt>  
        string_type lookup_collatename(FwdIt first, FwdIt last) const;  
    bool isctype(char_type ch, char_class_type cls) const;  
    int value(Elem ch, int base) const;  
    locale_type imbue(locale_type loc);  
    locale_type getloc() const;  
  
    typedef Elem char_type;  
    typedef T6 size_type;  
    typedef basic_string<Elem> string_type;  
    typedef T7 locale_type;  
    typedef T8 char_class_type;  
    };  
```  
  
#### Parámetros  
 `Elem`  
 El tipo de elemento que se va a describir.  
  
## Comentarios  
 La clase de plantilla describe varios rasgos de expresión regular de tipo `Elem`. La clase de plantilla [basic\_regex \(Clase\)](../standard-library/basic-regex-class.md) usa esta información para manipular los elementos de tipo `Elem`.  
  
 Cada objeto `regex_traits` contiene un objeto de tipo `regex_traits::locale` que usan algunas de sus funciones miembro. La configuración regional predeterminada es una copia de `regex_traits::locale()`. La función miembro `imbue` reemplaza el objeto de configuración regional, y la función miembro `getloc` devuelve una copia del objeto de configuración regional.  
  
## Requisitos  
 **Encabezado:** \<regex\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<regex\>](../standard-library/regex.md)   
 [regex\_traits](../standard-library/regex-traits-class.md)   
 [regex\_traits \< char \> \(clase\)](../standard-library/regex-traits-char-class.md)   
 [regex\_traits\<wchar\_t\> \(Clase\)](../standard-library/regex-traits-wchar-t-class.md)