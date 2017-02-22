---
title: "basic_regex (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::tr1::basic_regex"
  - "basic_regex"
  - "std.tr1.basic_regex"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_regex (clase) [TR1]"
ms.assetid: 8a18c6b4-f22a-4cfd-bc16-b4267867ebc3
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# basic_regex (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Contiene una expresión regular.  
  
## Sintaxis  
  
```  
template<class Elem,  
    class RXtraits = regex_traits<Elem>,  
    class basic_regex {  
public:  
    basic_regex();  
    explicit basic_regex(const Elem *ptr,  
        flag_type flags = ECMAScript);  
    basic_regex(const Elem *ptr, size_type len,  
        flag_type flags = ECMAScript);  
    basic_regex(const basic_regex& right);  
    template<class STtraits, class STalloc>  
        explicit basic_regex(const basic_string<Elem, STtraits, STalloc>& str,  
            flag_type flags = ECMAScript);  
    template<class InIt>  
        explicit basic_regex(InIt first, InIt last,  
            flag_type flags = ECMAScript);  
  
    basic_regex& operator=(const basic_regex& right);  
    basic_regex& operator=(const Elem *ptr);  
    template<class STtraits, class STalloc>  
        basic_regex& operator=(const basic_string<Elem, STtraits, STalloc>& str);  
    basic_regex& assign(const basic_regex& right);  
    basic_regex& assign(const Elem *ptr,  
        flag_type flags = ECMAScript);  
    basic_regex& assign(const Elem *ptr, size_type len,  
        flag_type flags = ECMAScript);  
    template<class STtraits, class STalloc>  
    basic_regex& assign(const basic_string<Elem, STtraits, STalloc>& str,  
        flag_type flags = ECMAScript);  
    template<class InIt>  
        basic_regex& assign(InIt first, InIt last,  
            flag_type flags = ECMAScript);  
  
    locale_type imbue(locale_type loc);  
    locale_type getloc() const;  
    void swap(basic_regex& other) throw();  
    unsigned mark_count() const;  
    flag_type flags() const;  
  
    typedef Elem value_type;  
    typedef regex_constants::syntax_option_type flag_type;  
    typedef typename RXtraits::locale_type locale_type;  
    static const flag_type icase = regex_constants::icase;  
    static const flag_type nosubs = regex_constants::nosubs;  
    static const flag_type optimize = regex_constants::optimize;  
    static const flag_type collate = regex_constants::collate;  
    static const flag_type ECMAScript = regex_constants::ECMAScript;  
    static const flag_type basic = regex_constants::basic;  
    static const flag_type extended = regex_constants::extended;  
    static const flag_type awk = regex_constants::awk;  
    static const flag_type grep = regex_constants::grep;  
    static const flag_type egrep = regex_constants::egrep;  
private:  
    RXtraits traits;    // exposition only  
    };  
```  
  
#### Parámetros  
 `Elem`  
 Tipo de los elementos que debe coincidir.  
  
 `RXtraits`  
 Clase Traits para los elementos.  
  
## Comentarios  
 La clase de plantilla describe un objeto que contiene una expresión regular.  Los objetos de esta clase de plantilla se pueden pasar a las funciones de plantilla [regex\_match \(Función\)](../Topic/regex_match%20Function.md), [regex\_search \(Función\)](../Topic/regex_search%20Function.md) y [regex\_replace \(Función\)](../Topic/regex_replace%20Function.md), junto con los argumentos adecuados de la cadena de texto, para buscar texto que coincida con la expresión regular.  Hay dos especializaciones de esta clase de plantilla, con las definiciones de tipo [regex \(Typedef\)](../Topic/regex%20Typedef.md) para los elementos de tipo `char` y [wregex \(Typedef\)](../Topic/wregex%20Typedef.md) para los elementos de tipo `wchar_t`.  
  
 El argumento de plantilla `RXtraits` describe las distintas propiedades importantes de la sintaxis de las expresiones regulares que la clase de plantilla admite.  Una clase que especifica estos rasgos de expresiones regulares debe tener la misma interfaz externa que un objeto de la clase de plantilla [regex\_traits \(Clase\)](../standard-library/regex-traits-class.md).  
  
 Algunas funciones toman una secuencia de operandos que define una expresión regular.  Puede especificar dicha secuencia de operandos de varias maneras:  
  
 `ptr` \-\- secuencia terminada en null, \(como una cadena de C, para `Elem` de tipo `char`\) que comience en `ptr` \(que no puede ser un puntero null\), donde el elemento que finaliza es el valor `value_type()` y no forma parte de la secuencia de operandos.  
  
 `ptr`, `count` \-\- una secuencia de elementos `count` que comienza en `ptr` \(que no puede ser un puntero null\)  
  
 `str` \-\- la secuencia especificada por el objeto `basic_string` `str`  
  
 `first`, `last` \-\- una secuencia de elementos delimitada por los iteradores `first` y `last`, en el intervalo `[first, last)`  
  
 `right` \-\- el objeto `basic_regex` `right`  
  
 Estas funciones miembro también toman un argumento `flags` que especifica las distintas opciones para la interpretación de la expresión regular además de las descritas por el tipo `RXtraits`.  
  
## Requisitos  
 **Encabezado:** \<regex\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<regex\>](../standard-library/regex.md)   
 [regex\_match \(Función\)](../Topic/regex_match%20Function.md)   
 [regex\_search \(Función\)](../Topic/regex_search%20Function.md)   
 [regex\_replace \(Función\)](../Topic/regex_replace%20Function.md)   
 [regex \(Typedef\)](../Topic/regex%20Typedef.md)   
 [wregex \(Typedef\)](../Topic/wregex%20Typedef.md)   
 [regex\_traits \(Clase\)](../standard-library/regex-traits-class.md)