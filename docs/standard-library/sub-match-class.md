---
title: "sub_match (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sub_match"
  - "std::tr1::sub_match"
  - "std.tr1.sub_match"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sub_match (clase) [TR1]"
ms.assetid: 804e2b9e-d16a-4c4c-ac60-024e0b2dd0e8
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# sub_match (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe a una subcoincidencia.  
  
## Sintaxis  
  
```  
template<class BidIt>  
    class sub_match  
        : public std::pair<BidIt, BidIt> {  
public:  
    bool matched;  
    int compare(const sub_match& right) const;  
    int compare(const basic_string<value_type>& right) const;  
    int compare(const value_type *right) const;  
    difference_type length() const;  
    operator basic_string<value_type>() const;  
    basic_string<value_type> str() const;  
    typedef typename iterator_traits<BidIt>::value_type value_type;  
    typedef typename iterator_traits<BidIt>::difference_type difference_type;  
    typedef BidIt iterator;  
    };  
```  
  
#### Parámetros  
 `BidIt`  
 El tipo de iterador para subcoincidencias.  
  
## Comentarios  
 La clase de plantilla describe un objeto que designa una secuencia de caracteres que coinciden con un grupo de capturas en una llamada a [regex\_match \(Función\)](../Topic/regex_match%20Function.md) o [regex\_search \(Función\)](../Topic/regex_search%20Function.md). Los objetos del tipo [match\_results \(Clase\)](../standard-library/match-results-class.md) contienen una matriz de estos objetos, uno para cada grupo de capturas en la expresión regular usada en la búsqueda.  
  
 Si no hay coincidencia con el grupo de capturas, el miembro de datos `matched` del objeto se considera false y los dos iteradores `first` y `second` \(heredados de la base `std::pair`\) son iguales. Si hay coincidencia con el grupo de capturas, `matched` es true, el iterador `first` apunta al primer carácter de la secuencia de destino que coincide con el grupo de capturas y el iterador `second` apunta a una posición más allá del último carácter de la secuencia de destino que coincide con el grupo de capturas. Observe que para una coincidencia de longitud cero, el miembro `matched` es true, los dos iteradores son iguales y ambos apuntan a la posición de la coincidencia.  
  
 Una coincidencia de longitud cero puede aparecer cuando un grupo de capturas solo se compone de una aserción o de una repetición que permite que se repita cero. Por ejemplo:  
  
 "^" coincide con la secuencia "a" de destino; el objeto `sub_match` correspondiente al grupo de capturas 0 contiene iteradores que apuntan al primer carácter de la secuencia.  
  
 "b\(a\*\)b" coincide con la secuencia "bb" de destino; el objeto `sub_match` correspondiente al grupo de capturas 1 contiene iteradores que apuntan al segundo carácter de la secuencia.  
  
## Requisitos  
 **Encabezado:** \<regex\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<regex\>](../standard-library/regex.md)   
 [sub\_match](../standard-library/sub-match-class.md)   
 [regex\_match \(Función\)](../Topic/regex_match%20Function.md)   
 [regex\_search \(Función\)](../Topic/regex_search%20Function.md)