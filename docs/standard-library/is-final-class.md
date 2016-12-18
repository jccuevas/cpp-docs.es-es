---
title: "is_final (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_final"
  - "std.is_final"
  - "std::is_final"
  - "type_traits/std::is_final"
dev_langs: 
  - "C++"
  - "c++"
helpviewer_keywords: 
  - "is_final"
ms.assetid: 9dbad82f-6685-4909-94e8-98e4a93994b9
caps.latest.revision: 12
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_final (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo es un tipo de clase marcado `final`.  
  
## Sintaxis  
  
```  
template<class T>  
    struct is_final;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo de `T` se marca un tipo de clase `final`, de lo contrario, contiene false. Si `T` es un tipo de clase, debe ser un tipo completo.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [final \(especificador\)](../cpp/final-specifier.md)