---
title: "max_unbounded (Clase) | Microsoft Docs"
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
  - "allocators/stdext::max_unbounded"
  - "stdext::max_unbounded"
  - "stdext.max_unbounded"
  - "max_unbounded"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "max_unbounded (clase)"
ms.assetid: e34627a9-c231-4031-a483-cbb0514fff46
caps.latest.revision: 18
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# max_unbounded (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe una [máximo de la clase](../standard-library/allocators-header.md) objeto que no limita la longitud máxima de un [freelist](../standard-library/freelist-class.md) objeto.  
  
## Sintaxis  
  
```  
class max_unbounded  
```  
  
### Funciones miembro  
  
|||  
|-|-|  
|[asignado](../Topic/max_unbounded::allocated.md)|Incrementa el número de bloques de memoria asignada.|  
|[Cancelar la asignación](../Topic/max_unbounded::deallocated.md)|Disminuye el recuento de asigna bloques de memoria.|  
|[completa](../Topic/max_unbounded::full.md)|Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.|  
|[publicado](../Topic/max_unbounded::released.md)|Disminuye el recuento de memoria se bloquea en la lista libre.|  
|[guardado](../Topic/max_unbounded::saved.md)|Incrementa el número de bloques de memoria en la lista libre.|  
  
## Requisitos  
 **Encabezado:** \<allocators\>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<allocators\>](../standard-library/allocators-header.md)