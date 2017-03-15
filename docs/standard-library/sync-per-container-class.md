---
title: "sync_per_container (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext.sync_per_container"
  - "sync_per_container"
  - "stdext::sync_per_container"
  - "allocators/stdext::sync_per_container"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sync_per_container (clase)"
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# sync_per_container (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe [filtro de sincronización](../standard-library/allocators-header.md) que proporciona un objeto de caché independiente para cada objeto de asignador.  
  
## Sintaxis  
  
```  
template <class Cache> class sync_per_container  
    : public Cache  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Cache`|El tipo de caché asociado al filtro de sincronización.  Puede ser [cache\_chunklist](../standard-library/cache-chunklist-class.md), [cache\_freelist](../standard-library/cache-freelist-class.md), o [cache\_suballoc](../standard-library/cache-suballoc-class.md).|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[equals](../Topic/sync_per_container::equals.md)|Compara dos memorias caché de igualdad.|  
  
## Requisitos  
 asignadores \<de**Encabezado:** \>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<allocators\>](../standard-library/allocators-header.md)