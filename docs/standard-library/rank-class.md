---
title: "rank (Clase) | Microsoft Docs"
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
  - "std::tr1::rank"
  - "std.tr1.rank"
  - "rank"
  - "std.rank"
  - "std::rank"
  - "type_traits/std::rank"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rank (clase) [TR1]"
  - "rank"
ms.assetid: bc9f1b8f-800f-46ca-b6f4-d8579ed5406a
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# rank (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene el número de dimensiones de matriz.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct rank;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## Comentarios  
 La consulta de tipo contiene el valor del número de dimensiones del tipo de matriz `Ty`, o 0 si `Ty` no es un tipo de matriz.  
  
## Ejemplo  
  
```  
// std_tr1__type_traits__rank.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    std::cout << "rank<int> == "   
        << std::rank<int>::value << std::endl;   
    std::cout << "rank<int[5]> == "   
        << std::rank<int[5]>::value << std::endl;   
    std::cout << "rank<int[5][10]> == "   
        << std::rank<int[5][10]>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
rango < int > == 0 rango < int [5] > == 1 rango < int [5] [10] > == 2  
```  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [extent \(Clase\)](../standard-library/extent-class.md)