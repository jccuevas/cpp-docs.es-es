---
title: "IAtlMemMgr Class | Microsoft Docs"
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
  - "IAtlMemMgr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IAtlMemMgr class"
  - "memoria, administrar"
  - "memoria, memory manager"
ms.assetid: 18b2c569-25fe-4464-bdb6-3b1abef7154a
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IAtlMemMgr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase representa la interfaz a un administrador de memoria.  
  
## Sintaxis  
  
```  
  
__interface __declspec( uuid( "654F7EF5-CFDF-4df9-A450-6C6A13C622C0" )) IAtlMemMgr  
  
```  
  
## Members  
  
### Métodos  
  
|||  
|-|-|  
|[Asigna](../Topic/IAtlMemMgr::Allocate.md)|Llame a este método para asignar un bloque de memoria.|  
|[Libre](../Topic/IAtlMemMgr::Free.md)|Llame a este método para liberar un bloque de memoria.|  
|[GetSize](../Topic/IAtlMemMgr::GetSize.md)|Llame a este método para recuperar el tamaño de un bloque de memoria asignado.|  
|[reasigne](../Topic/IAtlMemMgr::Reallocate.md)|Llame a este método para reasignar un bloque de memoria.|  
  
## Comentarios  
 Esta interfaz se implementa por [CComHeap](../../atl/reference/ccomheap-class.md), [CCRTHeap](../../atl/reference/ccrtheap-class.md), [CLocalHeap](../../atl/reference/clocalheap-class.md), [CGlobalHeap](../../atl/reference/cglobalheap-class.md), o [CWin32Heap](../../atl/reference/cwin32heap-class.md).  
  
> [!NOTE]
>  El valor local y funciones globales de pila son más lentos que otras funciones de administración de memoria, y no proporcionan tantas características.  Por consiguiente, las aplicaciones nuevas deben utilizar [funciones del montón](http://msdn.microsoft.com/library/windows/desktop/aa366711).  Éstos están disponibles en la clase de [CWin32Heap](../../atl/reference/cwin32heap-class.md) .  
  
## Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#94](../../atl/codesnippet/CPP/iatlmemmgr-class_1.cpp)]  
  
## Requisitos  
 **encabezado:** atlmem.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)