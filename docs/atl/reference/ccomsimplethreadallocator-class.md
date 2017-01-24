---
title: "CComSimpleThreadAllocator Class | Microsoft Docs"
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
  - "CComSimpleThreadAllocator"
  - "ATL::CComSimpleThreadAllocator"
  - "ATL.CComSimpleThreadAllocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL threads"
  - "ATL threads, asignar"
  - "CComSimpleThreadAllocator class"
  - "subprocesamiento [ATL], selecting threads"
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComSimpleThreadAllocator Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase administra la selección de subprocesos para la clase `CComAutoThreadModule`.  
  
## Sintaxis  
  
```  
  
class CComSimpleThreadAllocator  
  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComSimpleThreadAllocator::GetThread](../Topic/CComSimpleThreadAllocator::GetThread.md)|selecciona un subproceso.|  
  
## Comentarios  
 `CComSimpleThreadAllocator` administra la selección de subprocesos para [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  de`CComSimpleThreadAllocator::GetThread` los ciclos simplemente a través de cada subproceso y devuelven el siguiente de la secuencia.  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [CComApartment Class](../../atl/reference/ccomapartment-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)