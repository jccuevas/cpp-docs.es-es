---
title: "max_fixed_size (Clase) | Microsoft Docs"
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
  - "allocators/stdext::max_fixed_size"
  - "max_fixed_size"
  - "stdext::max_fixed_size"
  - "stdext.max_fixed_size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "max_fixed_size (clase)"
ms.assetid: 8c8f4588-37e9-4579-8168-ba3553800914
caps.latest.revision: 18
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# max_fixed_size (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto de [clase máxima](../standard-library/allocators-header.md) limitar un objeto de [freelist](../standard-library/freelist-class.md) a una longitud máxima fija.  
  
## Sintaxis  
  
```  
template <std::size_t Max> class max_fixed_size  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Max`|La clase máxima que determina el número máximo de elementos para almacenar en `freelist`.|  
  
### Constructores  
  
|||  
|-|-|  
|[max\_fixed\_size](../Topic/max_fixed_size::max_fixed_size.md)|Construye un objeto de tipo `max_fixed_size`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[asignado](../Topic/max_fixed_size::allocated.md)|Incrementa el recuento de bloques de memoria asignados.|  
|[desasignado](../Topic/max_fixed_size::deallocated.md)|Disminuye el recuento de bloques de memoria asignados.|  
|[completa](../Topic/max_fixed_size::full.md)|Devuelve un valor que especifica si varios bloques de memoria se deben agregar a la lista disponible.|  
|[liberado](../Topic/max_fixed_size::released.md)|Disminuye el recuento de bloques de memoria de la lista disponible.|  
|[guardado](../Topic/max_fixed_size::saved.md)|Incrementa el recuento de bloques de memoria de la lista disponible.|  
  
## Requisitos  
 asignadores \<de**Encabezado:** \>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<allocators\>](../standard-library/allocators-header.md)