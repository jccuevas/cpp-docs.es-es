---
title: "allocator_base (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "allocators.allocator_base"
  - "stdext.allocators.allocator_base"
  - "allocator_base"
  - "allocators/stdext::allocator_base"
  - "stdext::allocator_base"
  - "stdext::allocators::allocator_base"
  - "allocators/stdext::allocators::allocator_base"
  - "allocators::allocator_base"
  - "stdext.allocator_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator_base (clase)"
ms.assetid: f920b45f-2a88-4bb0-8ead-b6126b426ed4
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# allocator_base (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define la clase base y las funciones comunes necesarias para crear un asignador definido por el usuario a partir de un filtro de sincronización.  
  
## Sintaxis  
  
```  
template <class Type, class Sync> class allocator_base  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Type`|Tipo de elementos que asigna el asignador.|  
|`Sync`|Directiva de sincronización del asignador, que es [sync\_none \(Clase\)](../standard-library/sync-none-class.md), [sync\_per\_container \(Clase\)](../standard-library/sync-per-container-class.md), [sync\_per\_thread \(Clase\)](../standard-library/sync-per-thread-class.md) o [sync\_shared \(Clase\)](../standard-library/sync-shared-class.md).|  
  
### Constructores  
  
|||  
|-|-|  
|[allocator\_base](../Topic/allocator_base::allocator_base.md)|Construye un objeto de tipo `allocator_base`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[const\_pointer](../Topic/allocator_base::const_pointer.md)|Tipo que proporciona un puntero constante al tipo de objeto administrado por el asignador.|  
|[const\_reference](../Topic/allocator_base::const_reference.md)|Tipo que proporciona una referencia constante al tipo de objeto administrado por el asignador.|  
|[difference\_type](../Topic/allocator_base::difference_type.md)|Tipo entero con signo que puede representar la diferencia entre valores de punteros que señalan al tipo de objeto administrado por el asignador.|  
|[puntero](../Topic/allocator_base::pointer.md)|Tipo que proporciona un puntero al tipo de objeto administrado por el asignador.|  
|[referencia](../Topic/allocator_base::reference.md)|Tipo que proporciona una referencia al tipo de objeto administrado por el asignador.|  
|[size\_type](../Topic/allocator_base::size_type.md)|Tipo entero sin signo que puede representar la longitud de cualquier secuencia que un objeto de clase de plantilla `allocator_base` puede asignar.|  
|[value\_type](../Topic/allocator_base::value_type.md)|Tipo administrado por el asignador.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[\_Charalloc](../Topic/allocator_base::_Charalloc.md)|Asigna almacenamiento para una matriz de tipo `char`.|  
|[\_Chardealloc](../Topic/allocator_base::_Chardealloc.md)|Libera almacenamiento para la matriz que contiene elementos de tipo `char`.|  
|[dirección](../Topic/allocator_base::address.md)|Encuentra la dirección de un objeto cuyo valor se especifica.|  
|[allocate](../Topic/allocator_base::allocate.md)|Asigna un bloque de memoria lo suficientemente grande como para almacenar al menos un número especificado de elementos.|  
|[construct](../Topic/allocator_base::construct.md)|Crea un tipo concreto de objeto en una dirección especificada que se inicializa con un valor especificado.|  
|[deallocate](../Topic/allocator_base::deallocate.md)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|  
|[destroy](../Topic/allocator_base::destroy.md)|Llama a un destructor de objetos sin desasignar la memoria donde el objeto se almacena.|  
|[max\_size](../Topic/allocator_base::max_size.md)|Devuelve el número de elementos de tipo `Type` que podría asignar un objeto de clase allocator antes de que la memoria libre se agote.|  
  
## Requisitos  
 **Encabezado:** \<allocators\>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [\<allocators\>](../standard-library/allocators-header.md)