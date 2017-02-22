---
title: "CWin32Heap Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CWin32Heap"
  - "ATL.CWin32Heap"
  - "CWin32Heap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWin32Heap class"
ms.assetid: 69176022-ed98-4e3b-96d8-116b0c58ac95
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CWin32Heap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones de asignación del montón de Win32.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CWin32Heap : public IAtlMemMgr  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWin32Heap::CWin32Heap](../Topic/CWin32Heap::CWin32Heap.md)|el constructor.|  
|[CWin32Heap::~CWin32Heap](../Topic/CWin32Heap::~CWin32Heap.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWin32Heap::Allocate](../Topic/CWin32Heap::Allocate.md)|Asigna un bloque de memoria del objeto de pila.|  
|[CWin32Heap::Attach](../Topic/CWin32Heap::Attach.md)|Asocia el objeto de pila una pila existente.|  
|[CWin32Heap::Detach](../Topic/CWin32Heap::Detach.md)|Desasocia el objeto de pila de una pila existente.|  
|[CWin32Heap::Free](../Topic/CWin32Heap::Free.md)|Libera memoria asignada previamente de la pila.|  
|[CWin32Heap::GetSize](../Topic/CWin32Heap::GetSize.md)|Devuelve el tamaño de un bloque de memoria asignado de objeto de la pila.|  
|[CWin32Heap::Reallocate](../Topic/CWin32Heap::Reallocate.md)|Reasigna un bloque de memoria del objeto de pila.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWin32Heap::m\_bOwnHeap](../Topic/CWin32Heap::m_bOwnHeap.md)|Un indicador utilizado para determinar la propiedad actual del identificador de la pila.|  
|[CWin32Heap::m\_hHeap](../Topic/CWin32Heap::m_hHeap.md)|Identificador del objeto de pila.|  
  
## Comentarios  
 `CWin32Heap` implementa métodos de asignación de memoria mediante las funciones de asignación del montón de Win32, incluidas [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597) y [HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701).  A diferencia de otras clases de pila, `CWin32Heap` requiere un identificador válido de pila proporcionarse antes de que se asigna la memoria: el otro valor predeterminado de las clases usar la pila de proceso.  El identificador se puede proporcionar un constructor o método de [CWin32Heap:: Asociar](../Topic/CWin32Heap::Attach.md) .  Vea el método de [CWin32Heap:: CWin32Heap](../Topic/CWin32Heap::CWin32Heap.md) para más detalles.  
  
## Ejemplo  
 Vea el ejemplo para [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## Jerarquía de herencia  
 `IAtlMemMgr`  
  
 `CWin32Heap`  
  
## Requisitos  
 **encabezado:** atlmem.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)   
 [IAtlMemMgr Class](../../atl/reference/iatlmemmgr-class.md)   
 [CLocalHeap Class](../../atl/reference/clocalheap-class.md)   
 [CGlobalHeap Class](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap Class](../../atl/reference/ccrtheap-class.md)   
 [CComHeap Class](../../atl/reference/ccomheap-class.md)