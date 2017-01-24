---
title: "rts_alloc (Clase) | Microsoft Docs"
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
  - "stdext::rts_alloc"
  - "allocators/stdext::rts_alloc"
  - "rts_alloc"
  - "stdext.rts_alloc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rts_alloc (clase)"
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# rts_alloc (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla rts\_alloc describe un [filtro](../standard-library/allocators-header.md) que contiene una matriz de instancias de caché y determina la instancia que se va a usar para la asignación y la desasignación en tiempo de ejecución, y no en tiempo de compilación.  
  
## Sintaxis  
  
```  
template <class Cache> class rts_alloc  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Cache`|El tipo de instancias de caché contenido en la matriz.  Puede ser [cache\_chunklist \(Clase\)](../standard-library/cache-chunklist-class.md), [cache\_freelist](../standard-library/cache-freelist-class.md) o [cache\_suballoc](../standard-library/cache-suballoc-class.md).|  
  
## Comentarios  
 Esta clase de plantilla contiene varias instancias del asignador de bloques y determina la instancia que se va a usar para la asignación o desasignación en tiempo de ejecución, y no en tiempo de compilación.  Se usa con los compiladores que no se pueden reenlazar mediante compilación.  
  
### Funciones miembro  
  
|||  
|-|-|  
|[allocate](../Topic/rts_alloc::allocate.md)|Asigna un bloque de memoria.|  
|[deallocate](../Topic/rts_alloc::deallocate.md)|Libera un número especificado de objetos del almacenamiento, a partir de una posición especificada.|  
|[es igual a](../Topic/rts_alloc::equals.md)|Compara dos cachés para determinar si son iguales.|  
  
## Requisitos  
 **Encabezado:** \<allocators\>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md)   
 [\<allocators\>](../standard-library/allocators-header.md)