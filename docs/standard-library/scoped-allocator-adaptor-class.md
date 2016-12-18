---
title: "scoped_allocator_adaptor (clase) | Microsoft Docs"
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
  - "std.scoped_allocator_adaptor"
  - "scoped_allocator_adaptor"
  - "scoped_allocator/std::scoped_allocator_adaptor"
  - "std::scoped_allocator_adaptor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "scoped_allocator_adaptor (clase)"
ms.assetid: 0d9b06a1-9a4a-4669-9470-8805cae48e89
caps.latest.revision: 10
caps.handback.revision: 1
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# scoped_allocator_adaptor (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa un anidado de asignadores.  
  
## Sintaxis  
  
```cpp  
template<class Outer, class... Inner>  
    class scoped_allocator_adaptor;  
```  
  
## Comentarios  
 La clase de plantilla encapsula un anidado de uno o más asignadores.  Cada una clase tiene un asignador fuera de `outer_allocator_type`escrito, un sinónimo de `Outer`, que es una base pública del objeto de `scoped_allocator_adaptor` .  `Outer` se utiliza para asignar memoria que se usará en un contenedor.  Puede obtener una referencia a este objeto del asignador llamando a `outer_allocator`.  
  
 El resto de anidar ha escrito `inner_allocator_type`.  Un asignador interno se utiliza para asignar memoria para los elementos de un contenedor.  Puede obtener una referencia al objeto almacenado de este tipo llamando a `inner_allocator`.  Si `Inner...` no está vacío, `inner_allocator_type` ha escrito `scoped_allocator_adaptor<Inner...>`, y `inner_allocator` indica un objeto miembro.  Si no, `inner_allocator_type` ha escrito `scoped_allocator_adaptor<Outer>`, y `inner_allocator` designa el objeto completo.  
  
 El nido se comporta como si tiene profundidad arbitraria, replicando el asignador encapsulado más interno según sea necesario.  
  
 Varios conceptos que no forman parte de ayuda visibles de la interfaz en la descripción del comportamiento de esta clase de plantilla.  *Un asignador fuera* media todas las llamadas a la construcción y destruye métodos.  Se define eficazmente por la función recursiva `OUTERMOST(X)`, donde uno `OUTERMOST(X)` de siguiente.  
  
-   Si `X.outer_allocator()` está bien formado, después `OUTERMOST(X)` es `OUTERMOST(X.outer_allocator())`.  
  
-   De lo contrario, `OUTERMOST(X)` es `X`.  
  
 Definen a tres tipos por la exposición:  
  
|Tipo|Descripción|  
|----------|-----------------|  
|`Outermost`|Tipo de `OUTERMOST(*this)`.|  
|`Outermost_traits`|`allocator_traits<Outermost>`|  
|`Outer_traits`|`allocator_traits<Outer>`|  
  
### Constructores  
  
|Name|Descripción|  
|----------|-----------------|  
|[scoped\_allocator\_adaptor::scoped\_allocator\_adaptor \(constructor\)](../Topic/scoped_allocator_adaptor::scoped_allocator_adaptor%20Constructor.md)|Construye un objeto `scoped_allocator_adaptor`.|  
  
### Typedefs  
  
|Name|Descripción|  
|----------|-----------------|  
|`const_pointer`|Este tipo es un sinónimo de `const_pointer` que se asocia el asignador `Outer`.|  
|`const_void_pointer`|Este tipo es un sinónimo de `const_void_pointer` que se asocia el asignador `Outer`.|  
|`difference_type`|Este tipo es un sinónimo de `difference_type` que se asocia el asignador `Outer`.|  
|`inner_allocator_type`|Este tipo es un sinónimo para el tipo de adaptador anidados `scoped_allocator_adaptor<Inner...>`.|  
|`outer_allocator_type`|Este tipo es un sinónimo para el tipo de asignador base `Outer`.|  
|`pointer`|Este tipo es un sinónimo de `pointer` asociado al asignador `Outer`.|  
|`propagate_on_container_copy_assignment`|El tipo es true solo si `Outer_traits::propagate_on_container_copy_assignment` es true o `inner_allocator_type::propagate_on_container_copy_assignment` es true.|  
|`propagate_on_container_move_assignment`|El tipo es true solo si `Outer_traits::propagate_on_container_move_assignment` es true o `inner_allocator_type::propagate_on_container_move_assignment` es true.|  
|`propagate_on_container_swap`|El tipo es true solo si `Outer_traits::propagate_on_container_swap` es true o `inner_allocator_type::propagate_on_container_swap` es true.|  
|`size_type`|Este tipo es un sinónimo de `size_type` asociado al asignador `Outer`.|  
|`value_type`|Este tipo es un sinónimo de `value_type` asociado al asignador `Outer`.|  
|`void_pointer`|Este tipo es un sinónimo de `void_pointer` asociado al asignador `Outer`.|  
  
### Structs  
  
|Name|Descripción|  
|----------|-----------------|  
|[scoped\_allocator\_adaptor::rebind \(Struct\)](../Topic/scoped_allocator_adaptor::rebind%20Struct.md)|Define el tipo `Outer::rebind<Other>::other` como sinónimo de `scoped_allocator_adaptor<Other, Inner...>`.|  
  
### Métodos  
  
|Name|Descripción|  
|----------|-----------------|  
|[scoped\_allocator\_adaptor::allocate \(método\)](../Topic/scoped_allocator_adaptor::allocate%20Method.md)|Asigna memoria mediante el asignador de `Outer` .|  
|[scoped\_allocator\_adaptor::construct \(método\)](../Topic/scoped_allocator_adaptor::construct%20Method.md)|Construye un objeto.|  
|[scoped\_allocator\_adaptor::deallocate \(método\)](../Topic/scoped_allocator_adaptor::deallocate%20Method.md)|Desasigna objetos utilizando el asignador externo.|  
|[scoped\_allocator\_adaptor::destroy \(método\)](../Topic/scoped_allocator_adaptor::destroy%20Method.md)|Destruye un objeto especificado.|  
|[scoped\_allocator\_adaptor::inner\_allocator \(método\)](../Topic/scoped_allocator_adaptor::inner_allocator%20Method.md)|Recupera una referencia al objeto almacenado de `inner_allocator_type`escrito.|  
|[scoped\_allocator\_adaptor::max\_size \(método\)](../Topic/scoped_allocator_adaptor::max_size%20Method.md)|Determina el número máximo de objetos que se pueden asignar mediante el asignador externo.|  
|[scoped\_allocator\_adaptor::outer\_allocator \(método\)](../Topic/scoped_allocator_adaptor::outer_allocator%20Method.md)|Recupera una referencia al objeto almacenado de `outer_allocator_type`escrito.|  
|[scoped\_allocator\_adaptor::select\_on\_container\_copy\_construction \(método\)](../Topic/scoped_allocator_adaptor::select_on_container_copy_construction%20Method.md)|Crea un nuevo objeto de `scoped_allocator_adaptor` con cada asignador almacenado que el objeto inicializado llamando a `select_on_container_copy_construction` para cada asignador correspondiente.|  
  
## Requisitos  
 scoped\_allocator \<de**Encabezado:** \>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)