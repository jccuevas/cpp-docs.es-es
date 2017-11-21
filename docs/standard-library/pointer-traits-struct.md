---
title: pointer_traits (Struct) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::pointer_traits::element_type
- memory/std::pointer_traits::pointer
- memory/std::pointer_traits
- memory/std::pointer_traits::difference_type
- memory/std::pointer_traits::rebind
- xmemory0/std::pointer_traits::element_type
- xmemory0/std::pointer_traits::pointer
- xmemory0/std::pointer_traits
- xmemory0/std::pointer_traits::difference_type
- xmemory0/std::pointer_traits::rebind
- memory/std::pointer_traits::pointer_to
dev_langs: C++
ms.assetid: 545aecf1-3561-4859-8b34-603c079fe1b3
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6d40f9149a9a03e4de40713ba9c7c0ce65f0edad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="pointertraits-struct"></a>pointer_traits (Struct)
Proporciona información que necesita un objeto de clase de plantilla `allocator_traits` para describir un asignador con el tipo de puntero `Ptr`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template <class Ptr>
struct pointer_traits;
```  
  
## <a name="remarks"></a>Comentarios  
 Ptr puede ser un puntero sin formato de tipo `Ty *` o una clase con las siguientes propiedades.  
```  
struct Ptr
   { // describes a pointer type usable by allocators
   typedef Ptr pointer;
   typedef T1 element_type; // optional
   typedef T2 difference_type; // optional
   template <class Other>
   using rebind = typename Ptr<Other, Rest...>; // optional
   static pointer pointer_to(element_type& obj);
   // optional
   };  
```
### <a name="typedefs"></a>Definiciones de tipo  
  
|Name|Descripción|  
|----------|-----------------|  
|`typedef T2 difference_type`|El tipo `T2` es `Ptr::difference_type` si ese tipo existe, de otro modo, `ptrdiff_t`. Si `Ptr` es un puntero sin formato, el tipo es `ptrdiff_t`.|  
|`typedef T1 element_type`|El tipo `T1` es `Ptr::element_type` si ese tipo existe, de otro modo, `Ty`. Si `Ptr` es un puntero sin formato, el tipo es `Ty`.|  
|`typedef Ptr pointer`|El tipo es `Ptr`.|  
  
### <a name="structs"></a>Structs  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`pointer_traits::rebind`|Intenta convertir el tipo de puntero subyacente en un tipo especificado.|  
  
### <a name="methods"></a>Métodos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[pointer_to](#pointer_to)|Convierte una referencia arbitraria en un objeto de clase `Ptr`.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<memory>  
  
 **Espacio de nombres:** std  
  
##  <a name="pointer_to"></a> pointer_to  
 El método estático que devuelve `Ptr::pointer_to(obj)`, si esa función existe. De otro modo, no es posible convertir una referencia arbitraria en un objeto de clase `Ptr`. Si `Ptr` es un puntero sin formato, este método devuelve `addressof(obj)`.  
  
```cpp  
static pointer pointer_to(element_type& obj);
```  
  
## <a name="see-also"></a>Vea también  
 [\<memory>](../standard-library/memory.md)   
 [allocator_traits (Clase)](../standard-library/allocator-traits-class.md)

