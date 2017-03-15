---
title: "allocator_traits (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "memory/std::allocator_traits"
  - "memory/std::allocator_traits::propagate_on_container_move_assignment"
  - "memory/std::allocator_traits::const_pointer"
  - "memory/std::allocator_traits::propagate_on_container_swap"
  - "memory/std::allocator_traits::propagate_on_container_copy_assignment"
  - "memory/std::allocator_traits::difference_type"
  - "memory/std::allocator_traits::allocator_type"
  - "memory/std::allocator_traits::value_type"
  - "memory/std::allocator_traits::pointer"
  - "memory/std::allocator_traits::size_type"
  - "memory/std::allocator_traits::const_void_pointer"
  - "memory/std::allocator_traits::void_pointer"
dev_langs: 
  - "C++"
ms.assetid: 612974b8-b5d4-4668-82fb-824bff6821d6
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# allocator_traits (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que complemente *un tipo de asignador*.  Un tipo de asignador es cualquier tipo que describa un objeto de asignador que se utiliza para administrar almacenamiento asignado.  , Porque cualquier asignador escribe `Alloc`, puede utilizar específicamente `allocator_traits<Alloc>` para determinar toda la información que necesita un contenedor asignador\- habilitado.  Para obtener más información, vea [allocator \(Clase\)](../standard-library/allocator-class.md)predeterminado.  
  
## Sintaxis  
  
```cpp  
template<class Alloc>  
    class allocator_traits;  
```  
  
### Typedefs  
  
|Name|Descripción|  
|----------|-----------------|  
|`allocator_traits::allocator_type`|Este tipo es un sinónimo para el parámetro `Alloc`de la plantilla.|  
|`allocator_traits::const_pointer`|Este tipo es `Alloc::const_pointer`, si el tipo es correcto; si no, este tipo es `pointer_traits<pointer>::rebind<const value_type>`.|  
|`allocator_traits::const_void_pointer`|Este tipo es `Alloc::const_void_pointer`, si el tipo es correcto; si no, este tipo es `pointer_traits<pointer>::rebind<const void>`.|  
|`allocator_traits::difference_type`|Este tipo es `Alloc::difference_type`, si el tipo es correcto; si no, este tipo es `pointer_traits<pointer>::difference_type`.|  
|`allocator_traits::pointer`|Este tipo es `Alloc::pointer`, si el tipo es correcto; si no, este tipo es `value_type *`.|  
|`allocator_traits::propagate_on_container_copy_assignment`|Este tipo es `Alloc::propagate_on_container_copy_assignment`, si el tipo es correcto; si no, este tipo es `false_type`.|  
|`allocator_traits::propagate_on_container_move_assignment`|Este tipo es `Alloc::propagate_on_container_move_assignment`, si el tipo es correcto; si no, este tipo es `false_type`.  Si el tipo es true, un contenedor asignador\- habilitado copia el asignador almacenado en una asignación de movimiento.|  
|`allocator_traits::propagate_on_container_swap`|Este tipo es `Alloc::propagate_on_container_swap`, si el tipo es correcto; si no, este tipo es `false_type`.  Si el tipo es true, un contenedor asignador\- habilitado cambia el asignador almacenado en un intercambio.|  
|`allocator_traits::size_type`|Este tipo es `Alloc::size_type`, si el tipo es correcto; si no, este tipo es `make_unsigned<difference_type>::type`.|  
|`allocator_traits::value_type`|Este tipo es un sinónimo de `Alloc::value_type`.|  
|`allocator_traits::void_pointer`|Este tipo es `Alloc::void_pointer`, si el tipo es correcto; si no, este tipo es `pointer_traits<pointer>::rebind<void>`.|  
  
### Métodos estáticos  
 Los métodos estáticos siguientes llaman al método correspondiente en un parámetro determinado del asignador.  
  
|Name|Descripción|  
|----------|-----------------|  
|[allocator\_traits::allocate \(método\)](../Topic/allocator_traits::allocate%20Method.md)|Método estático que asigna memoria mediante el parámetro determinado del asignador.|  
|[allocator\_traits::construct \(método\)](../Topic/allocator_traits::construct%20Method.md)|Método estático que utiliza un asignador especificado para construir un objeto.|  
|[allocator\_traits::deallocate \(método\)](../Topic/allocator_traits::deallocate%20Method.md)|Método estático que utiliza un asignador especificado para desasignar un número especificado de objetos.|  
|[allocator\_traits::destruir \(método\)](../Topic/allocator_traits::destroy%20Method.md)|Método estático que utiliza un asignador especificado para llamar al destructor en un objeto sin desasignar su memoria.|  
|[allocator\_traits::max\_size \(método\)](../Topic/allocator_traits::max_size%20Method.md)|Método estático que utiliza un asignador especificado para determinar el número máximo de objetos que pueden asignarse.|  
|[allocator\_traits::select\_on\_container\_copy\_construction \(método\)](../Topic/allocator_traits::select_on_container_copy_construction%20Method.md)|Método estático que llama a `select_on_container_copy_construction` en el asignador especificado.|  
  
## Requisitos  
 **Encabezado:** \<memory\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<memory\>](../standard-library/memory.md)   
 [pointer\_traits \(Struct\)](../standard-library/pointer-traits-struct.md)   
 [scoped\_allocator\_adaptor \(clase\)](../standard-library/scoped-allocator-adaptor-class.md)