---
title: "cache_suballoc (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext.cache_suballoc"
  - "allocators/stdext::cache_suballoc"
  - "stdext::cache_suballoc"
  - "cache_suballoc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cache_suballoc (clase)"
ms.assetid: 9ea9c5e9-1dcc-45d0-b3a7-a56a93d88898
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# cache_suballoc (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define un [Bloquear asignador](../standard-library/allocators-header.md) que asigna y desasigna bloques de memoria de un tamaño único.  
  
## Sintaxis  
  
```  
template <std::size_t Sz, size_t Nelts = 20> class cache_suballoc  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Sz`|El número de elementos de la matriz que se va a asignar.|  
  
## Comentarios  
 La clase de plantilla cache\_suballoc almacena los bloques de memoria desasignada en una lista con longitud ilimitada, mediante `freelist<sizeof(Type), max_unbounded>`, y suballocates de bloques de memoria de un fragmento mayor asignado con `operator new` cuando la lista está vacía.  
  
 Cada fragmento contiene `Sz * Nelts` bytes de memoria utilizable y los datos que `operator new` y `operator delete` requieren. Nunca se liberarán los fragmentos asignados.  
  
### Constructores  
  
|||  
|-|-|  
|[cache\_suballoc](../Topic/cache_suballoc::cache_suballoc.md)|Construye un objeto de tipo `cache_suballoc`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[allocate](../Topic/cache_suballoc::allocate.md)|Asigna un bloque de memoria.|  
|[deallocate](../Topic/cache_suballoc::deallocate.md)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|  
  
## Requisitos  
 **Encabezado:** \<allocators\>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<allocators\>](../standard-library/allocators-header.md)