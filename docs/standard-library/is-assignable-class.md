---
title: "is_assignable (clase) | Microsoft Docs"
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
  - "is_assignable"
  - "std.is_assignable"
  - "std::is_assignable"
  - "type_traits/std::is_assignable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_assignable"
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
caps.latest.revision: 14
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_assignable (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Prueba si un valor de `From` tipo puede asignarse a un `To` tipo.  
  
## Sintaxis  
  
```  
template <class To, class From>  
    struct is_assignable;  
```  
  
#### Parámetros  
 Para  
 El tipo del objeto que recibe la asignación.  
  
 De  
 El tipo del objeto que proporciona el valor.  
  
## Comentarios  
 La expresión no evaluada `declval<To>() = declval<From>()` debe ser correcto. Ambos `From` y `To` deben ser tipos completos, `void`, o matrices de límite desconocido.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)