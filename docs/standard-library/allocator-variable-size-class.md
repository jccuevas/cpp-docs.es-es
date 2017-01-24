---
title: "allocator_variable_size (Clase) | Microsoft Docs"
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
  - "allocators.allocator_variable_size"
  - "allocators::allocator_variable_size"
  - "allocators/stdext::allocator_variable_size"
  - "stdext.allocators.allocator_variable_size"
  - "allocator_variable_size"
  - "allocators/stdext::allocators::allocator_variable_size"
  - "stdext::allocators::allocator_variable_size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator_variable_size (clase)"
ms.assetid: c3aa4105-ae45-4385-bbbe-9f23060478cb
caps.latest.revision: 16
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# allocator_variable_size (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que administra la asignación de almacenamiento y liberar para los objetos de `Type` escribe utilizando la memoria caché de [cache\_freelist](../standard-library/cache-freelist-class.md) escrito con una longitud administrada por [max\_variable\_size](../standard-library/max-variable-size-class.md).  
  
## Sintaxis  
  
```  
template <class Type>  
    class allocator_variable_size;  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Type`|El tipo de elementos asignado por el asignador.|  
  
## Comentarios  
 La macro de [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md) pasa esta clase como parámetro de `name` en la instrucción siguiente: `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_variable_size), SYNC_DEFAULT, allocator_variable_size);`  
  
## Requisitos  
 asignadores \<de**Encabezado:** \>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<allocators\>](../standard-library/allocators-header.md)