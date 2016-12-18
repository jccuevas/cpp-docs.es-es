---
title: "CComHeap Class | Microsoft Docs"
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
  - "CComHeap"
  - "ATL.CComHeap"
  - "ATL::CComHeap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComHeap class"
ms.assetid: c74183ce-98ae-46fb-b186-93ea4cf0222b
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComHeap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones de asignación de memoria COM.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CComHeap : public IAtlMemMgr  
  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComHeap::Allocate](../Topic/CComHeap::Allocate.md)|Llame a este método para asignar un bloque de memoria.|  
|[CComHeap::Free](../Topic/CComHeap::Free.md)|Llame a este método para liberar un bloque de memoria asignada por este administrador de memoria.|  
|[CComHeap::GetSize](../Topic/CComHeap::GetSize.md)|Llame a este método para obtener el tamaño asignado de un bloque de memoria asignada por este administrador de memoria.|  
|[CComHeap::Reallocate](../Topic/CComHeap::Reallocate.md)|Llame a este método para reasignar la memoria asignada por este administrador de memoria.|  
  
## Comentarios  
 `CComHeap` implementa funciones de asignación de memoria mediante las funciones de asignación COM, incluidas [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727), [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722), [IMalloc:: GetSize](http://msdn.microsoft.com/library/windows/desktop/ms691226), y [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280).  La cantidad de memoria máxima que puede ser asignada es igual a 2147483647\) bytes de **INT\_MAX** \(.  
  
## Ejemplo  
 Vea el ejemplo para [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## Jerarquía de herencia  
 `IAtlMemMgr`  
  
 `CComHeap`  
  
## Requisitos  
 **encabezado:** ATLComMem.h  
  
## Vea también  
 [Ejemplo DynamicConsumer](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CWin32Heap Class](../../atl/reference/cwin32heap-class.md)   
 [CLocalHeap Class](../../atl/reference/clocalheap-class.md)   
 [CGlobalHeap Class](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap Class](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr Class](../../atl/reference/iatlmemmgr-class.md)