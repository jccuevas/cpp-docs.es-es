---
title: "hash (Clase) | Microsoft Docs"
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
  - "std.hash"
  - "xfunctional/std::hash"
  - "hash"
  - "typeindex/std::hash"
  - "std::hash"
  - "std.tr1.hash"
  - "std::tr1::hash"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash (clase)"
  - "hash (clase) [TR1]"
ms.assetid: e1b500c6-a5c8-4f6f-ad33-7ec52eb8e2e4
caps.latest.revision: 21
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# hash (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Calcula el código hash para un valor.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct hash  
        : public unary_function<Ty, size_t> {  
    size_t operator()(Ty _Val) const;  
    };  
```  
  
## Comentarios  
 La función miembro define una función hash, conviene asignar valores de `Ty` tipo a una distribución de valores de índice.  El operador de miembro devuelve un código hash para `_Val`, adecuado para el uso con clases de plantilla `unordered_map`, `unordered_multimap`, `unordered_set`, y `unordered_multiset`.  `Ty` puede ser cualquier tipo escalar, `string`, `wstring`, `error_code`, `error_condition`, `u16string`, o `u32string`.  
  
## Ejemplo  
  
```  
// std_tr1__functional__hash.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
#include <unordered_set>   
  
int main()   
    {   
    std::unordered_set<int, std::hash<int> > c0;   
    c0.insert(3);   
    std::cout << *c0.find(3) << std::endl;   
  
    return (0);   
    }  
  
```  
  
 **3**   
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<unordered\_map\>](../standard-library/unordered-map.md)   
 [unordered\_multimap \(Clase\)](../standard-library/unordered-multimap-class.md)   
 [unordered\_multiset \(Clase\)](../standard-library/unordered-multiset-class.md)   
 [\<unordered\_set\>](../standard-library/unordered-set.md)