---
title: "is_trivially_assignable (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "is_trivially_assignable"
  - "std.is_trivially_assignable"
  - "std::is_trivially_assignable"
  - "type_traits/std::is_trivially_assignable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_trivially_assignable"
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# is_trivially_assignable (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Prueba si un valor de `From` se puede asignar tipo muy `To` tipo  
  
## Sintaxis  
  
```  
template <class To, class From>  
    struct is_trivially_assignable;  
```  
  
#### Parámetros  
 Para  
 El tipo del objeto que recibe la asignación.  
  
 De  
 El tipo del objeto que proporciona el valor.  
  
## Comentarios  
 La expresión `declval<To>() = declval<From>()` debe ser correcto y debe conocerse al compilador para no requerir ninguna operación no trivial. Ambos `From` y `To` deben ser tipos completos, `void`, o matrices de límite desconocido.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)