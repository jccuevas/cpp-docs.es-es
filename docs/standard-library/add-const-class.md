---
title: "add_const (Clase) | Microsoft Docs"
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
  - "std::tr1::add_const"
  - "add_const"
  - "std.tr1.add_const"
  - "std.add_const"
  - "std::add_const"
  - "type_traits/std::add_const"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "add_const (clase) [TR1]"
  - "add_const"
ms.assetid: 1262a1eb-8c9c-4dd6-9f43-88ba280182f1
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# add_const (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea un tipo const a partir de un tipo.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct add_const;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a modificar.  
  
## Comentarios  
 Una instancia del modificador de tipo contiene un tipo modificado que es `Ty` si `Ty` es una referencia, una función o un tipo calificado como const; si no, es `const Ty`.  
  
## Ejemplo  
  
```  
// std_tr1__type_traits__add_const.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::add_const<int>::type *p = (const int *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "add_const<int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **add\_const\<int\> \=\= int**   
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [remove\_const \(Clase\)](../standard-library/remove-const-class.md)