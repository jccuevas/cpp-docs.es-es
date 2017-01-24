---
title: "sync_shared (Clase) | Microsoft Docs"
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
  - "sync_shared"
  - "allocators/stdext::sync_shared"
  - "stdext.sync_shared"
  - "stdext::sync_shared"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sync_shared (clase)"
ms.assetid: cab3af9e-3d1a-4f2c-8580-0f89e5687d8e
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# sync_shared (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un [filtro de sincronización](../standard-library/allocators-header.md) que usa una exclusión mutua para controlar el acceso a un objeto de caché compartido por todos los asignadores.  
  
## Sintaxis  
  
```  
template <class Cache> class sync_shared  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Cache`|El tipo de caché asociado al filtro de sincronización. Puede ser [cache\_chunklist](../standard-library/cache-chunklist-class.md), [cache\_freelist](../standard-library/cache-freelist-class.md) o [cache\_suballoc](../standard-library/cache-suballoc-class.md).|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[allocate](../Topic/sync_shared::allocate.md)|Asigna un bloque de memoria.|  
|[deallocate](../Topic/sync_shared::deallocate.md)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|  
|[es igual a](../Topic/sync_shared::equals.md)|Compara dos cachés para determinar si son iguales.|  
  
## Requisitos  
 **Encabezado:** \<allocators\>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<allocators\>](../standard-library/allocators-header.md)