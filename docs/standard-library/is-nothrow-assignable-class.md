---
title: "is_nothrow_assignable (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "is_nothrow_assignable"
  - "std.is_nothrow_assignable"
  - "std::is_nothrow_assignable"
  - "type_traits/std::is_nothrow_assignable"
dev_langs: 
  - "C++"
  - "c++"
helpviewer_keywords: 
  - "is_nothrow_assignable"
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_nothrow_assignable (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Prueba si un valor de `From` tipo puede asignarse a `To` se conoce el tipo y la asignación no se iniciará.  
  
## Sintaxis  
  
```  
template <class To, class From>   
    struct is_nothrow_assignable;  
```  
  
#### Parámetros  
 Para  
 El tipo del objeto que recibe la asignación.  
  
 De  
 El tipo del objeto que proporciona el valor.  
  
## Comentarios  
 La expresión `declval<To>() = declval<From>()` debe ser correcto y debe conocerse en el compilador no se iniciará. Ambos `From` y `To` deben ser tipos completos, `void`, o matrices de límite desconocido.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)