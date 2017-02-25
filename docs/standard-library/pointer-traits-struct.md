---
title: "pointer_traits (Struct) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "memory/std::pointer_traits::element_type"
  - "memory/std::pointer_traits::pointer"
  - "memory/std::pointer_traits"
  - "memory/std::pointer_traits::difference_type"
  - "memory/std::pointer_traits::rebind"
  - "xmemory0/std::pointer_traits::element_type"
  - "xmemory0/std::pointer_traits::pointer"
  - "xmemory0/std::pointer_traits"
  - "xmemory0/std::pointer_traits::difference_type"
  - "xmemory0/std::pointer_traits::rebind"
dev_langs: 
  - "C++"
ms.assetid: 545aecf1-3561-4859-8b34-603c079fe1b3
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# pointer_traits (Struct)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Proporciona información que necesita un objeto de clase de plantilla `allocator_traits` para describir un asignador con el tipo de puntero `Ptr`.  
  
## Sintaxis  
  
```cpp  
template<class Ptr>  
    struct pointer_traits;  
```  
  
## Comentarios  
 La PTR puede ser un puntero sin formato de `Ty *` tipo o una clase con propiedades siguientes.  
  
```  
template<class Ty, class... Rest>  
    struct Ptr  
    { // describes a pointer type usable by allocators  
    typedef Ptr pointer;  
    typedef T1 element_type; // optional  
    typedef T2 difference_type; // optional  
    template<class Other>  
        using rebind = typename Ptr<Other, Rest...>; // optional  
  
    static pointer pointer_to(element_type& obj); // optional  
    };  
```  
  
> [!WARNING]
>  Mientras el estándar de C\+\+ especifica el miembro de `rebind` como plantilla de alias, Visual C\+\+ implementa vuelve a enlazar como `struct`.  
  
### Typedefs  
  
|Name|Descripción|  
|----------|-----------------|  
|`typedef T2 difference_type`|El tipo `T2` es `Ptr::difference_type` si existe el tipo, si no `ptrdiff_t`.  Si `Ptr` es puntero sin formato, el tipo es `ptrdiff_t`.|  
|`typedef T1 element_type`|El tipo `T1` es `Ptr::element_type` si existe el tipo, si no `Ty`.  Si `Ptr` es puntero sin formato, el tipo es `Ty`.|  
|`typedef Ptr pointer`|El tipo es `Ptr`.|  
  
### Structs  
  
|Name|Descripción|  
|----------|-----------------|  
|`pointer_traits::rebind`|Intenta convertir el tipo de puntero subyacente a un tipo especificado.|  
  
### Métodos  
  
|Name|Descripción|  
|----------|-----------------|  
|[pointer\_traits::pointer\_to \(método\)](../Topic/pointer_traits::pointer_to%20Method.md)|Convierte una referencia arbitraria a un objeto de clase `Ptr`.|  
  
## Requisitos  
 **Encabezado:** \<memory\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<memory\>](../standard-library/memory.md)   
 [allocator\_traits \(clase\)](../standard-library/allocator-traits-class.md)