---
title: "allocator_unbounded (Clase) | Microsoft Docs"
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
  - "stdext::allocators::allocator_unbounded"
  - "allocator_unbounded"
  - "allocators/stdext::allocator_unbounded"
  - "allocators::allocator_unbounded"
  - "allocators/stdext::allocators::allocator_unbounded"
  - "allocators.allocator_unbounded"
  - "stdext.allocators.allocator_unbounded"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator_unbounded (clase)"
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
caps.latest.revision: 17
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# allocator_unbounded (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que administra la asignación de almacenamiento y liberar para los objetos de `Type` escribe utilizando la memoria caché de [cache\_freelist](../standard-library/cache-freelist-class.md) escrito con una longitud administrada por [max\_unbounded](../standard-library/max-unbounded-class.md).  
  
## Sintaxis  
  
```  
template <class Type>  
    class allocator_unbounded;  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Type`|El tipo de elementos asignado por el asignador.|  
  
## Comentarios  
 La macro de [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md) pasa esta clase como parámetro de `name` en la instrucción siguiente: `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`  
  
## Requisitos  
 asignadores \<de**Encabezado:** \>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<allocators\>](../standard-library/allocators-header.md)