---
title: "CElementTraitsBase Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CElementTraitsBase"
  - "ATL::CElementTraitsBase"
  - "ATL.CElementTraitsBase<T>"
  - "ATL::CElementTraitsBase<T>"
  - "ATL.CElementTraitsBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CElementTraitsBase class"
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CElementTraitsBase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona los métodos predeterminados de copia y move para una clase de colección.  
  
## Sintaxis  
  
```  
  
      template<  
   typename T  
>  
class CElementTraitsBase  
```  
  
#### Parámetros  
 `T`  
 El tipo de datos que se almacenan en la colección.  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CElementTraitsBase::INARGTYPE](../Topic/CElementTraitsBase::INARGTYPE.md)|El tipo de datos que desea usar para agregar elementos al objeto de clase de colección.|  
|[CElementTraitsBase::OUTARGTYPE](../Topic/CElementTraitsBase::OUTARGTYPE.md)|El tipo de datos para recuperar elementos de objeto de la clase de colección.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CElementTraitsBase::CopyElements](../Topic/CElementTraitsBase::CopyElements.md)|Llame a este método para copiar los elementos almacenados en un objeto de clase de colección.|  
|[CElementTraitsBase::RelocateElements](../Topic/CElementTraitsBase::RelocateElements.md)|Llame a este método para reubicar los elementos almacenados en un objeto de clase de colección.|  
  
## Comentarios  
 Esta clase base define métodos para copiar y reubicar elementos en una clase de colección.  Lo utilizan las clases [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md), [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md), y [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).  
  
 Para obtener más información, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)