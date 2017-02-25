---
title: "CHeapPtrList Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CHeapPtrList"
  - "CHeapPtrList"
  - "ATL.CHeapPtrList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHeapPtrList class"
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CHeapPtrList Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos útiles al crear una lista de punteros de la pila.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template<  
typename E,  
class Allocator = ATL::CCRTAllocator  
>  
class CHeapPtrList : public CAtlList<  
ATL::CHeapPtr< E, Allocator>,  
CHeapPtrElementTraits< E, Allocator>  
>  
```  
  
#### Parámetros  
 `E`  
 El tipo de objeto que se va a almacenar en la clase de colección.  
  
 `Allocator`  
 La clase de asignación de memoria en uso.  El valor predeterminado es [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHeapPtrList::CHeapPtrList](../Topic/CHeapPtrList::CHeapPtrList.md)|el constructor.|  
  
## Comentarios  
 Esta clase proporciona un constructor y deriva métodos de [CAtlList](../../atl/reference/catllist-class.md) y de [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md) para facilitar la creación de un objeto de clase de colección que almacena punteros de la pila.  
  
## Jerarquía de herencia  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CHeapPtrList`  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [CAtlList Class](../../atl/reference/catllist-class.md)   
 [CHeapPtr Class](../../atl/reference/cheapptr-class.md)   
 [CHeapPtrElementTraits Class](../../atl/reference/cheapptrelementtraits-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)