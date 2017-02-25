---
title: "CComAllocator Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComAllocator"
  - "ATL::CComAllocator"
  - "CComAllocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComAllocator class"
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComAllocator Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para administrar la memoria usando las rutinas COM de memoria.  
  
## Sintaxis  
  
```  
  
class CComAllocator  
  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComAllocator::Allocate](../Topic/CComAllocator::Allocate.md)|Llame a este método estático para asignar memoria.|  
|[CComAllocator::Free](../Topic/CComAllocator::Free.md)|Llame a este método estático para liberar la memoria asignada.|  
|[CComAllocator::Reallocate](../Topic/CComAllocator::Reallocate.md)|Llame a este método estático para reasignar memoria.|  
  
## Comentarios  
 Esta clase es utilizada por [CComHeapPtr](../../atl/reference/ccomheapptr-class.md) para proporcionar rutinas COM de asignación de memoria.  La clase de equivalente, [CCRTAllocator](../../atl/reference/ccrtallocator-class.md), proporciona los mismos métodos usando las rutinas de CRT.  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [CComHeapPtr Class](../../atl/reference/ccomheapptr-class.md)   
 [CCRTAllocator Class](../../atl/reference/ccrtallocator-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)