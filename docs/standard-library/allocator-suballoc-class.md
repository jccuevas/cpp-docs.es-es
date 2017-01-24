---
title: "allocator_suballoc (Clase) | Microsoft Docs"
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
  - "allocators::allocator_suballoc"
  - "allocator_suballoc"
  - "stdext.allocators.allocator_suballoc"
  - "allocators/stdext::allocators::allocator_suballoc"
  - "stdext::allocators::allocator_suballoc"
  - "allocators/stdext::allocator_suballoc"
  - "allocators.allocator_suballoc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator_suballoc (clase)"
ms.assetid: 50c6a5c0-d00d-4276-9285-d908fd4f6483
caps.latest.revision: 16
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# allocator_suballoc (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que administra la asignación de almacenamiento y la liberación de objetos de tipo `Type` con una memoria caché de tipo [cache\_suballoc](../standard-library/cache-suballoc-class.md).  
  
## Sintaxis  
  
```  
template <class Type>  
    class allocator_suballoc;  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Type`|Tipo de elementos que asigna el asignador.|  
  
## Comentarios  
 El [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md) macro pasa esta clase como el `name` parámetro en la instrucción siguiente: `ALLOCATOR_DECL(CACHE_SUBALLOC, SYNC_DEFAULT, allocator_suballoc);`  
  
## Requisitos  
 **Encabezado:** \<allocators\>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<allocators\>](../standard-library/allocators-header.md)