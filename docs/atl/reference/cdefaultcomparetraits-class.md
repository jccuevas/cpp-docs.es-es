---
title: "CDefaultCompareTraits Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CDefaultCompareTraits<T>"
  - "ATL::CDefaultCompareTraits"
  - "ATL.CDefaultCompareTraits"
  - "ATL::CDefaultCompareTraits<T>"
  - "CDefaultCompareTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDefaultCompareTraits class"
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CDefaultCompareTraits Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona funciones de comparación predeterminadas del elemento.  
  
## Sintaxis  
  
```  
  
      template<  
   typename T  
>  
class CDefaultCompareTraits  
```  
  
#### Parámetros  
 `T`  
 El tipo de datos que se almacenan en la colección.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDefaultCompareTraits::CompareElements](../Topic/CDefaultCompareTraits::CompareElements.md)|\(Estático\) llame a esta función para comparar dos elementos de igualdad.|  
|[CDefaultCompareTraits::CompareElementsOrdered](../Topic/CDefaultCompareTraits::CompareElementsOrdered.md)|\(Estático\) llame a esta función para determinar el mayor y poco elemento.|  
  
## Comentarios  
 Esta clase contiene dos funciones estáticas para comparar los elementos almacenados en un objeto de clase de colección.  esta clase es utilizada por [clase de CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md).  
  
 Para obtener más información, vea [clases de colección de ATL](../../atl/atl-collection-classes.md).  
  
## Requisitos  
 **encabezado:** atlcoll.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)