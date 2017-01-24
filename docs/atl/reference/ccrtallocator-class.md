---
title: "CCRTAllocator Class | Microsoft Docs"
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
  - "CCRTAllocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCRTAllocator class"
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCRTAllocator Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para administrar la memoria usando las rutinas de memoria CRT.  
  
## Sintaxis  
  
```  
  
class ATL::CCRTAllocator  
  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCRTAllocator::Allocate](../Topic/CCRTAllocator::Allocate.md)|\(Estático\) llame a este método para asignar memoria.|  
|[CCRTAllocator::Free](../Topic/CCRTAllocator::Free.md)|\(Estático\) llame a este método para liberar memoria.|  
|[CCRTAllocator::Reallocate](../Topic/CCRTAllocator::Reallocate.md)|\(Estático\) llame a este método para reasignar memoria.|  
  
## Comentarios  
 Esta clase es utilizada por [CHeapPtr](../../atl/reference/cheapptr-class.md) para proporcionar rutinas de asignación de memoria CRT.  La clase de equivalente, [CComAllocator](../../atl/reference/ccomallocator-class.md), proporciona los mismos métodos usando las rutinas COM.  
  
## Requisitos  
 **encabezado:** atlcore.h  
  
## Vea también  
 [CHeapPtr Class](../../atl/reference/cheapptr-class.md)   
 [CComAllocator Class](../../atl/reference/ccomallocator-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)