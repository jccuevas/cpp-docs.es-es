---
title: "CLocalHeap Class | Microsoft Docs"
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
  - "ATL.CLocalHeap"
  - "ATL::CLocalHeap"
  - "CLocalHeap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLocalHeap class"
ms.assetid: 1ffa87a5-5fc8-4f8d-8809-58e87e963bd2
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CLocalHeap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante funciones locales de la pila de Win32.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CLocalHeap : public IAtlMemMgr  
  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLocalHeap::Allocate](../Topic/CLocalHeap::Allocate.md)|Llame a este método para asignar un bloque de memoria.|  
|[CLocalHeap::Free](../Topic/CLocalHeap::Free.md)|Llame a este método para liberar un bloque de memoria asignada por este administrador de memoria.|  
|[CLocalHeap::GetSize](../Topic/CLocalHeap::GetSize.md)|Llame a este método para obtener el tamaño asignado de un bloque de memoria asignada por este administrador de memoria.|  
|[CLocalHeap::Reallocate](../Topic/CLocalHeap::Reallocate.md)|Llame a este método para reasignar la memoria asignada por este administrador de memoria.|  
  
## Comentarios  
 Las funciones de asignación de memoria de ayudas de`CLocalHeap` mediante el montón local de Win32 funcionan.  
  
> [!NOTE]
>  Funciones locales de la pila son más lentas que otras funciones de administración de memoria y no proporcionan tantas características.  Por consiguiente, las aplicaciones nuevas deben utilizar [funciones del montón](http://msdn.microsoft.com/library/windows/desktop/aa366711).  Éstos están disponibles en la clase de [CWin32Heap](../../atl/reference/cwin32heap-class.md) .  
  
## Ejemplo  
 Vea el ejemplo para [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## Jerarquía de herencia  
 `IAtlMemMgr`  
  
 `CLocalHeap`  
  
## Requisitos  
 **encabezado:** atlmem.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComHeap Class](../../atl/reference/ccomheap-class.md)   
 [CWin32Heap Class](../../atl/reference/cwin32heap-class.md)   
 [CGlobalHeap Class](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap Class](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr Class](../../atl/reference/iatlmemmgr-class.md)