---
title: "allocator_chunklist (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext::allocators::allocator_chunklist"
  - "allocators::allocator_chunklist"
  - "allocators/stdext::allocator_chunklist"
  - "allocators.allocator_chunklist"
  - "allocators/stdext::allocators::allocator_chunklist"
  - "allocator_chunklist"
  - "stdext.allocators.allocator_chunklist"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator_chunklist (clase)"
ms.assetid: ea72ed0a-dfdb-4c8b-8096-e4baf567b80f
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# allocator_chunklist (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que administra la asignación de almacenamiento y liberar para los objetos en la memoria caché de [cache\_chunklist](../standard-library/cache-chunklist-class.md)escrito.  
  
## Sintaxis  
  
```  
template <class Type>  
    class allocator_chunklist;  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Type`|El tipo de elementos asignado por el asignador.|  
  
## Comentarios  
 La macro de [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md) pasa esta clase como parámetro de `name` en la instrucción siguiente: `ALLOCATOR_DECL(CACHE_CHUNKLIST, SYNC_DEFAULT, allocator_chunklist``);`  
  
## Requisitos  
 asignadores \<de**Encabezado:** \>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<allocators\>](../standard-library/allocators-header.md)