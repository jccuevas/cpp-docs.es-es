---
title: "CComHeapPtr Class | Microsoft Docs"
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
  - "ATL::CComHeapPtr"
  - "ATL.CComHeapPtr<T>"
  - "ATL::CComHeapPtr<T>"
  - "CComHeapPtr"
  - "ATL.CComHeapPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComHeapPtr class"
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComHeapPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una clase de puntero inteligente para administrar punteros de la pila.  
  
## Sintaxis  
  
```  
  
      template<  
   typename T  
> class CComHeapPtr :  
   public CHeapPtr< T, CComAllocator >  
```  
  
#### Parámetros  
 `T`  
 El tipo de objeto que se va a almacenar en la pila.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComHeapPtr::CComHeapPtr](../Topic/CComHeapPtr::CComHeapPtr.md)|el constructor.|  
  
## Comentarios  
 `CComHeapPtr` deriva de `CHeapPtr`, pero utiliza [CComAllocator](../../atl/reference/ccomallocator-class.md) para asignar memoria usando las rutinas COM.  Vea [CHeapPtr](../../atl/reference/cheapptr-class.md) y [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) para los métodos disponibles.  
  
## Jerarquía de herencia  
 [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)  
  
 [CHeapPtr](../../atl/reference/cheapptr-class.md)  
  
 `CComHeapPtr`  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [CHeapPtr Class](../../atl/reference/cheapptr-class.md)   
 [CHeapPtrBase Class](../../atl/reference/cheapptrbase-class.md)   
 [CComAllocator Class](../../atl/reference/ccomallocator-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)