---
title: "CHeapPtrElementTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CHeapPtrElementTraits"
  - "CHeapPtrElementTraits"
  - "ATL::CHeapPtrElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHeapPtrElementTraits class"
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHeapPtrElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos, funciones estáticas, y tipos útiles al crear colecciones de punteros de la pila.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template<  
typename T,  
class Allocator= ATL::CCRTAllocator  
>  
class CHeapPtrElementTraits : public CDefaultElementTraits<  
ATL::CHeapPtr< T, Allocator>  
>  
```  
  
#### Parámetros  
 `T`  
 El tipo de objeto que se va a almacenar en la clase de colección.  
  
 `Allocator`  
 La clase de asignación de memoria en uso.  El valor predeterminado es [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHeapPtrElementTraits::INARGTYPE](../Topic/CHeapPtrElementTraits::INARGTYPE.md)|El tipo de datos que desea usar para agregar elementos al objeto de clase de colección.|  
|[CHeapPtrElementTraits::OUTARGTYPE](../Topic/CHeapPtrElementTraits::OUTARGTYPE.md)|El tipo de datos para recuperar elementos de objeto de la clase de colección.|  
  
## Comentarios  
 Esta clase proporciona métodos, funciones estáticas, y tipos para facilitar la creación de objetos de clase de colección que contienen punteros de la pila.  la clase `CHeapPtrList` deriva de `CHeapPtrElementTraits`.  
  
 Para obtener más información, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Jerarquía de herencia  
 [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)  
  
 [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)  
  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)  
  
 `CHeapPtrElementTraits`  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [CDefaultElementTraits Class](../../atl/reference/cdefaultelementtraits-class.md)   
 [CComHeapPtr Class](../../atl/reference/ccomheapptr-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)