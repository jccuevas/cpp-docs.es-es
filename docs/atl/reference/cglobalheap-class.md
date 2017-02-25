---
title: "CGlobalHeap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CGlobalHeap"
  - "ATL::CGlobalHeap"
  - "CGlobalHeap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CGlobalHeap class"
ms.assetid: e348d838-3aa7-4bee-a1b3-cd000c99f834
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CGlobalHeap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones globales de la pila de Win32.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CGlobalHeap : public IAtlMemMgr  
  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGlobalHeap::Allocate](../Topic/CGlobalHeap::Allocate.md)|Llame a este método para asignar un bloque de memoria.|  
|[CGlobalHeap::Free](../Topic/CGlobalHeap::Free.md)|Llame a este método para liberar un bloque de memoria asignada por este administrador de memoria.|  
|[CGlobalHeap::GetSize](../Topic/CGlobalHeap::GetSize.md)|Llame a este método para obtener el tamaño asignado de un bloque de memoria asignada por este administrador de memoria.|  
|[CGlobalHeap::Reallocate](../Topic/CGlobalHeap::Reallocate.md)|Llame a este método para reasignar la memoria asignada por este administrador de memoria.|  
  
## Comentarios  
 `CGlobalHeap` implementa funciones de asignación de memoria mediante las funciones globales de la pila de Win32.  
  
> [!NOTE]
>  Las funciones globales de pila son más lentas que otras funciones de administración de memoria y no proporcionan tantas características.  Por consiguiente, las aplicaciones nuevas deben utilizar [funciones del montón](http://msdn.microsoft.com/library/windows/desktop/aa366711).  Éstos están disponibles en la clase de [CWin32Heap](../../atl/reference/cwin32heap-class.md) .  las funciones globales todavía son utilizadas por DDE y el portapapeles funciona.  
  
## Ejemplo  
 Vea el ejemplo para [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## Jerarquía de herencia  
 `IAtlMemMgr`  
  
 `CGlobalHeap`  
  
## Requisitos  
 **encabezado:** atlmem.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComHeap Class](../../atl/reference/ccomheap-class.md)   
 [CWin32Heap Class](../../atl/reference/cwin32heap-class.md)   
 [CLocalHeap Class](../../atl/reference/clocalheap-class.md)   
 [CCRTHeap Class](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr Class](../../atl/reference/iatlmemmgr-class.md)