---
title: "max_variable_size (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext::max_variable_size"
  - "allocators/stdext::max_variable_size"
  - "stdext.max_variable_size"
  - "max_variable_size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "max_variable_size (clase)"
ms.assetid: 9f2e9df0-4148-4b37-bc30-f8eca0ef86ae
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# max_variable_size (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe una [máximo de la clase](../standard-library/allocators-header.md) objeto que limita una [freelist](../standard-library/freelist-class.md) asignar el objeto a una longitud máxima es de aproximadamente proporcional al número de bloques de memoria.  
  
## Sintaxis  
  
```  
class max_variable_size  
```  
  
### Constructores  
  
|||  
|-|-|  
|[max\_variable\_size](../Topic/max_variable_size::max_variable_size.md)|Construye un objeto de tipo `max_variable_size`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[asignado](../Topic/max_variable_size::allocated.md)|Incrementa el número de bloques de memoria asignada.|  
|[Cancelar la asignación](../Topic/max_variable_size::deallocated.md)|Disminuye el recuento de asigna bloques de memoria.|  
|[completa](../Topic/max_variable_size::full.md)|Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.|  
|[publicado](../Topic/max_variable_size::released.md)|Disminuye el recuento de memoria se bloquea en la lista libre.|  
|[guardado](../Topic/max_variable_size::saved.md)|Incrementa el número de bloques de memoria en la lista libre.|  
  
## Requisitos  
 **Encabezado:** \<allocators\>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<allocators\>](../standard-library/allocators-header.md)