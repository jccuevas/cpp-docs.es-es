---
title: "sync_per_thread (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext::sync_per_thread"
  - "sync_per_thread"
  - "allocators/stdext::sync_per_thread"
  - "stdext.sync_per_thread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sync_per_thread (clase)"
ms.assetid: 47bf75f8-5b02-4760-b1d3-3099d08fe14c
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# sync_per_thread (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe [filtro de sincronización](../standard-library/allocators-header.md) que proporciona un objeto de caché independiente para cada subproceso.  
  
## Sintaxis  
  
```  
template <class Cache> class sync_per_thread  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Cache`|El tipo de caché asociado al filtro de sincronización.  Puede ser [cache\_chunklist](../standard-library/cache-chunklist-class.md), [cache\_freelist](../standard-library/cache-freelist-class.md), o [cache\_suballoc](../standard-library/cache-suballoc-class.md).|  
  
## Comentarios  
 Los asignadores que utilizan `sync_per_thread` pueden comparar el igual aunque los bloques asignados en un subproceso no se pueden desasignar de otro subproceso.  Al utilizar uno de estos bloques de memoria de los asignadores asignados en un subproceso no se debe hacer visible a otros subprocesos.  Esto significa en la práctica que un contenedor que usa uno de estos asignadores debe realizarse únicamente por un único subproceso.  
  
### Funciones miembro  
  
|||  
|-|-|  
|[asigna](../Topic/sync_per_thread::allocate.md)|Asigna un bloque de memoria.|  
|[desasignar cualquier espacio](../Topic/sync_per_thread::deallocate.md)|Libera un número especificado de objetos inicial de almacenamiento en una posición especificada.|  
|[equals](../Topic/sync_per_thread::equals.md)|Compara dos memorias caché de igualdad.|  
  
## Requisitos  
 asignadores \<de**Encabezado:** \>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<allocators\>](../standard-library/allocators-header.md)