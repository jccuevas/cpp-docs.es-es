---
title: "CCRTHeap Class | Microsoft Docs"
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
  - "ATL::CCRTHeap"
  - "ATL.CCRTHeap"
  - "CCRTHeap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCRTHeap class"
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCRTHeap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones del montón de CRT.  
  
## Sintaxis  
  
```  
  
class CCRTHeap : public IAtlMemMgr  
  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCRTHeap::Allocate](../Topic/CCRTHeap::Allocate.md)|Llame a este método para asignar un bloque de memoria.|  
|[CCRTHeap::Free](../Topic/CCRTHeap::Free.md)|Llame a este método para liberar un bloque de memoria asignada por este administrador de memoria.|  
|[CCRTHeap::GetSize](../Topic/CCRTHeap::GetSize.md)|Llame a este método para obtener el tamaño asignado de un bloque de memoria asignada por este administrador de memoria.|  
|[CCRTHeap::Reallocate](../Topic/CCRTHeap::Reallocate.md)|Llame a este método para reasignar la memoria asignada por este administrador de memoria.|  
  
## Comentarios  
 Las funciones de asignación de memoria de ayudas de`CCRTHeap` mediante el montón de CRT funcionan, incluidos [malloc](../../c-runtime-library/reference/malloc.md), [libre](../../c-runtime-library/reference/free.md), [realloc](../../c-runtime-library/reference/realloc.md), y [\_msize](../../c-runtime-library/reference/msize.md).  
  
## Ejemplo  
 Vea el ejemplo para [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## Jerarquía de herencia  
 `IAtlMemMgr`  
  
 `CCRTHeap`  
  
## Requisitos  
 **encabezado:** atlmem.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComHeap Class](../../atl/reference/ccomheap-class.md)   
 [CWin32Heap Class](../../atl/reference/cwin32heap-class.md)   
 [CLocalHeap Class](../../atl/reference/clocalheap-class.md)   
 [CGlobalHeap Class](../../atl/reference/cglobalheap-class.md)   
 [IAtlMemMgr Class](../../atl/reference/iatlmemmgr-class.md)