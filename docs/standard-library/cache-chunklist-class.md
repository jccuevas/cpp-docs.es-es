---
title: "cache_chunklist (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "allocators/stdext::cache_chunklist"
  - "stdext.cache_chunklist"
  - "stdext::cache_chunklist"
  - "cache_chunklist"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cache_chunklist (clase)"
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# cache_chunklist (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define [asignador de bloque](../standard-library/allocators-header.md) que asigna y libere los bloques de memoria de un solo tamaño.  
  
## Sintaxis  
  
```  
template <std::size_t Sz, std::size_t Nelts = 20> class cache_chunklist  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Sz`|El número de elementos de la matriz que se asignará.|  
  
## Comentarios  
 Esta clase de plantilla utiliza `operator new` para asignar los elementos de la memoria sin formato, suballocating bloques para asignar el almacenamiento de un bloque de memoria cuando es necesario; almacena los bloques de memoria desasignados en una lista disponible independiente para cada fragmento, y utiliza `operator delete` para desasignar un fragmento cuando ninguno de los bloques de memoria está en uso.  
  
 Cada bloque de memoria contiene los bytes de `Sz` de memoria utilizable y un puntero a la que pertenece.  Cada fragmento contiene los bloques de memoria de `Nelts` , tres punteros, int y los datos que `operator new` y `operator delete` requieren.  
  
### Constructores  
  
|||  
|-|-|  
|[cache\_chunklist](../Topic/cache_chunklist::cache_chunklist.md)|Construye un objeto de tipo `cache_chunklist`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[asigna](../Topic/cache_chunklist::allocate.md)|Asigna un bloque de memoria.|  
|[desasignar cualquier espacio](../Topic/cache_chunklist::deallocate.md)|Libera un número especificado de objetos inicial de almacenamiento en una posición especificada.|  
  
## Requisitos  
 asignadores \<de**Encabezado:** \>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<allocators\>](../standard-library/allocators-header.md)