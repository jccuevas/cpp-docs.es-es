---
title: "cache_freelist (Clase) | Microsoft Docs"
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
  - "stdext.cache_freelist"
  - "allocators/stdext::cache_freelist"
  - "stdext::cache_freelist"
  - "cache_freelist"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cache_freelist (clase)"
ms.assetid: 840694de-36ba-470f-8dae-2b723d5a8cd9
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# cache_freelist (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define un [Bloquear asignador](../standard-library/allocators-header.md) que asigna y desasigna bloques de memoria de un tamaño único.  
  
## Sintaxis  
  
```  
template <std::size_t Sz, class Max> class cache_freelist  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Sz`|El número de elementos de la matriz que se va a asignar.|  
|`Max`|La clase máxima que representa el tamaño máximo de la lista libre. Esto puede ser [max\_fixed\_size](../standard-library/max-fixed-size-class.md), [max\_none](../standard-library/max-none-class.md), [max\_unbounded](../standard-library/max-unbounded-class.md), o [max\_variable\_size](../standard-library/max-variable-size-class.md).|  
  
## Comentarios  
 La clase de plantilla cache\_freelist mantiene una lista de bloques de memoria de tamaño `Sz`. Una vez completa la lista libre usa `operator delete` desasignar memoria bloquea. Cuando la lista está vacía utiliza `operator new` para asignar nuevos bloques de memoria. El tamaño máximo de la lista libre viene determinado por la clase clase max pasa el `Max` parámetro.  
  
 Cada bloque de memoria contiene `Sz` bytes de memoria utilizable y los datos que `operator new` y `operator delete` requieren.  
  
### Constructores  
  
|||  
|-|-|  
|[cache\_freelist](../Topic/cache_freelist::cache_freelist.md)|Construye un objeto de tipo `cache_freelist`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[allocate](../Topic/cache_freelist::allocate.md)|Asigna un bloque de memoria.|  
|[deallocate](../Topic/cache_freelist::deallocate.md)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|  
  
## Requisitos  
 **Encabezado:** \<allocators\>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<allocators\>](../standard-library/allocators-header.md)