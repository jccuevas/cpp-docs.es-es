---
title: "is_empty (Clase) | Microsoft Docs"
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
  - "std::tr1::is_empty"
  - "std.tr1.is_empty"
  - "is_empty"
  - "std.is_empty"
  - "std::is_empty"
  - "type_traits/std::is_empty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_empty (clase) [TR1]"
  - "is_empty"
ms.assetid: 44a6fc92-7e55-4fbe-9a24-2a0ce2dccba0
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_empty (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo es una clase vacía.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct is_empty;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo es true si el tipo `Ty` es una clase vacía; en caso contrario, es false.  
  
## Ejemplo  
  
```  
// std_tr1__type_traits__is_empty.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct empty   
    {   
    };   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_empty<trivial> == " << std::boolalpha   
        << std::is_empty<trivial>::value << std::endl;   
    std::cout << "is_empty<empty> == " << std::boolalpha   
        << std::is_empty<empty>::value << std::endl;   
    std::cout << "is_empty<int> == " << std::boolalpha   
        << std::is_empty<int>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
is_empty < trivial > == false is_empty < vacío > == true is_empty < int > == false  
```  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)