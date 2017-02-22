---
title: "max_none (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "max_none"
  - "stdext::max_none"
  - "stdext.max_none"
  - "allocators/stdext::max_none"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "max_none (clase)"
ms.assetid: 12ab5376-412e-479c-86dc-2c3d6a3559b6
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# max_none (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe una [máximo de la clase](../standard-library/allocators-header.md) objeto que limita una [freelist](../standard-library/freelist-class.md) objeto a una longitud máxima de cero.  
  
## Sintaxis  
  
```  
template <std::size_t Max> class max_none  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Max`|La clase máxima que determina el número máximo de elementos que se van a almacenar en el `freelist`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[asignado](../Topic/max_none::allocated.md)|Incrementa el número de bloques de memoria asignada.|  
|[Cancelar la asignación](../Topic/max_none::deallocated.md)|Disminuye el recuento de asigna bloques de memoria.|  
|[completa](../Topic/max_none::full.md)|Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.|  
|[publicado](../Topic/max_none::released.md)|Disminuye el recuento de memoria se bloquea en la lista libre.|  
|[guardado](../Topic/max_none::saved.md)|Incrementa el número de bloques de memoria en la lista libre.|  
  
## Requisitos  
 **Encabezado:** \<allocators\>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<allocators\>](../standard-library/allocators-header.md)