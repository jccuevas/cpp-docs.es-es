---
title: "CDefaultElementTraits Class | Microsoft Docs"
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
  - "ATL::CDefaultElementTraits<T>"
  - "ATL.CDefaultElementTraits"
  - "ATL::CDefaultElementTraits"
  - "ATL.CDefaultElementTraits<T>"
  - "CDefaultElementTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDefaultElementTraits class"
ms.assetid: ac5ee610-7957-4b7c-92b6-38ff72e4118e
caps.latest.revision: 17
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDefaultElementTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos predeterminados y funciones para una clase de colección.  
  
## Sintaxis  
  
```  
  
      template<  
   typename T  
>  
class CDefaultElementTraits : public CElementTraitsBase< T >,  
   public CDefaultHashTraits< T >,  
   public CDefaultCompareTraits< T >  
```  
  
#### Parámetros  
 `T`  
 El tipo de datos que se almacenan en la colección.  
  
## Comentarios  
 Esta clase proporciona funciones estáticas predeterminadas y los métodos para mover, copiar, comparar, y aplicar un algoritmo hash a los elementos almacenados en un objeto de clase de colección.  Esta clase se deriva sus funciones y métodos de [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md), de [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md), y de [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md), y es utilizada por [CElementTraits](../../atl/reference/celementtraits-class.md), [CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md), y [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md).  
  
 Para obtener más información, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)