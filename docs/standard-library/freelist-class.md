---
title: "freelist (Clase) | Microsoft Docs"
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
  - "stdext::freelist"
  - "freelist"
  - "stdext.freelist"
  - "allocators/stdext::freelist"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "freelist (clase)"
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
caps.latest.revision: 17
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# freelist (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Administra una lista de bloques de memoria.  
  
## Sintaxis  
  
```  
template <std::size_t Sz, class Max> class freelist  
    : public Max  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Sz`|El número de elementos de la matriz que se asignará.|  
|`Max`|La clase máxima que representa el número máximo de elementos que se almacenan en la lista disponible.  La clase máxima posible [max\_none](../standard-library/max-none-class.md), [max\_unbounded](../standard-library/max-unbounded-class.md), [max\_fixed\_size](../standard-library/max-fixed-size-class.md), o [max\_variable\_size](../standard-library/max-variable-size-class.md).|  
  
## Comentarios  
 Esta clase de plantilla administra una lista de bloques de memoria de tamaño `Sz` con la longitud máxima de la lista determinada por la clase máxima última en `Max`.  
  
### Constructores  
  
|||  
|-|-|  
|[freelist](../Topic/freelist::freelist.md)|Construye un objeto de tipo `freelist`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[pop](../Topic/freelist::pop.md)|Quita el primer bloque de memoria de la lista disponible.|  
|[push](../Topic/freelist::push.md)|Agrega un bloque de memoria a la lista.|  
  
## Requisitos  
 asignadores \<de**Encabezado:** \>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<allocators\>](../standard-library/allocators-header.md)