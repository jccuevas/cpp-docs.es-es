---
title: "sync_none (Clase) | Microsoft Docs"
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
  - "stdext.sync_none"
  - "sync_none"
  - "allocators/stdext::sync_none"
  - "stdext::sync_none"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sync_none (clase)"
ms.assetid: f7473cee-14f3-4fe1-88bc-68cd085e59e1
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# sync_none (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe [filtro de sincronización](../standard-library/allocators-header.md) que no proporciona ninguna sincronización.  
  
## Sintaxis  
  
```  
template <class Cache> class sync_none  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Cache`|El tipo de caché asociado al filtro de sincronización.  Puede ser [cache\_chunklist](../standard-library/cache-chunklist-class.md), [cache\_freelist](../standard-library/cache-freelist-class.md), o [cache\_suballoc](../standard-library/cache-suballoc-class.md).|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[asigna](../Topic/sync_none::allocate.md)|Asigna un bloque de memoria.|  
|[desasignar cualquier espacio](../Topic/sync_none::deallocate.md)|Libera un número especificado de objetos inicial de almacenamiento en una posición especificada.|  
|[equals](../Topic/sync_none::equals.md)|Compara dos memorias caché de igualdad.|  
  
## Requisitos  
 asignadores \<de**Encabezado:** \>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<allocators\>](../standard-library/allocators-header.md)