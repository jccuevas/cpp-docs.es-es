---
title: "regex_token_iterator (Clase) | Microsoft Docs"
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
  - "regex_token_iterator"
  - "std.tr1.regex_token_iterator"
  - "std::tr1::regex_token_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "regex_token_iterator (clase) [TR1]"
ms.assetid: a213ba48-8e4e-4b6b-871a-2637acf05f15
caps.latest.revision: 15
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# regex_token_iterator (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase de iterador para subcoincidencias.  
  
## Sintaxis  
  
```  
template<class BidIt, class Elem = iterator_traits<BidIt>::value_type,  
    class RXtraits = regex_traits<Elem> >  
        class regex_token_iterator {  
public:  
    typedef basic_regex<Elem, RXtraits> regex_type;  
    typedef sub_match<BidIt> value_type;  
    typedef std::forward_iterator_tag iterator_category;  
    typedef std::ptrdiff_t difference_type;  
    typedef const sub_match<BidIt> *pointer;  
    typedef const sub_match<BidIt>& reference;  
  
    regex_token_iterator();  
    regex_token_iterator(BidIt first, BidIt last,  
        const regex_type& re, int submatch = 0,  
        regex_constants::match_flag_type f = regex_constants::match_default);  
    regex_token_iterator(BidIt first, BidIt last,  
        const regex_type& re, const std::vector<int> submatches,  
        regex_constants::match_flag_type f = regex_constants::match_default);  
    template<std::size_t N>  
    regex_token_iterator(BidIt first, BidIt last,  
        const regex_type& re, const int (&submatches)[N],  
        regex_constants::match_flag_type f = regex_constants::match_default);  
  
    bool operator==(const regex_token_iterator& right);  
    bool operator!=(const regex_token_iterator& right);  
    const basic_string<Elem>& operator*();  
    const basic_string<Elem> *operator->();  
    regex_token_iterator& operator++();  
    regex_token_iterator& operator++(int);  
private:  
    regex_iterator<BidIt, Elem, RXtraits> it; // exposition only  
    vector<int> subs;                         // exposition only  
    int pos;                                  // exposition only  
    };  
```  
  
#### Parámetros  
 `BidIt`  
 El tipo de iterador para subcoincidencias.  
  
 `Elem`  
 Tipo de los elementos que debe coincidir.  
  
 `RXtraits`  
 Clase Traits para los elementos.  
  
## Comentarios  
 La clase de plantilla describe un objeto constante de iterador hacia delante. Conceptualmente, contiene un objeto `regex_iterator` que usa para buscar coincidencias de expresiones regulares en una secuencia de caracteres. Extrae objetos del tipo `sub_match<BidIt>` que representan las subcoincidencias identificadas por los valores de índice en el vector almacenado `subs` para cada coincidencia de expresión regular.  
  
 Un valor de índice de \-1 señala la secuencia de caracteres que empieza inmediatamente después del final de la coincidencia de expresión regular anterior \(o comienza al principio de la secuencia de caracteres si no había ninguna coincidencia de expresión regular anterior\) y que se extiende, aunque sin incluirlo, al primer carácter de la coincidencia de expresión regular actual o hasta el final de la secuencia de caracteres si no hay una coincidencia actual. Cualquier otro valor de índice `idx` señala el contenido del grupo de capturas incluido en `it.match[idx]`.  
  
## Requisitos  
 **Encabezado:** \<regex\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<regex\>](../standard-library/regex.md)   
 [regex\_token\_iterator](../standard-library/regex-token-iterator-class.md)   
 [regex\_iterator \(Clase\)](../standard-library/regex-iterator-class.md)