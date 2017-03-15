---
title: "allocator_fixed_size (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "allocators/stdext::allocators::allocator_fixed_size"
  - "allocators::allocator_fixed_size"
  - "allocators/stdext::allocator_fixed_size"
  - "allocator_fixed_size"
  - "stdext::allocators::allocator_fixed_size"
  - "allocators.allocator_fixed_size"
  - "stdext.allocators.allocator_fixed_size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator_fixed_size (clase)"
ms.assetid: 138f3ef8-b0b3-49c3-9486-58f2213c172f
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# allocator_fixed_size (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que administra la asignación de almacenamiento y liberar para los objetos de `Type` escribe utilizando la memoria caché de [cache\_freelist](../standard-library/cache-freelist-class.md) escrito con una longitud administrada por [max\_fixed\_size](../standard-library/max-fixed-size-class.md).  
  
## Sintaxis  
  
```  
template <class Type>  
    class allocator_fixed_size;  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Type`|El tipo de elementos asignado por el asignador.|  
  
## Comentarios  
 La macro de [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md) pasa esta clase como parámetro de `name` en la instrucción siguiente: `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_fixed_size<10>), SYNC_DEFAULT, allocator_fixed_size);`  
  
## Requisitos  
 asignadores \<de**Encabezado:** \>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<allocators\>](../standard-library/allocators-header.md)