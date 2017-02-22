---
title: "CComMultiThreadModelNoCS Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CComMultiThreadModelNoCS"
  - "CComMultiThreadModelNoCS"
  - "ATL.CComMultiThreadModelNoCS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, multithreading"
  - "CComMultiThreadModelNoCS class"
  - "subprocesamiento [ATL]"
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CComMultiThreadModelNoCS Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CComMultiThreadModelNoCS` proporciona métodos seguros para subprocesos para aumentar y disminuir el valor de una variable, sin el bloqueo de la sección crítica funcionalidad o el desbloquear.  
  
## Sintaxis  
  
```  
  
class CComMultiThreadModelNoCS  
  
```  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComMultiThreadModelNoCS::AutoCriticalSection](../Topic/CComMultiThreadModelNoCS::AutoCriticalSection.md)|Hace referencia a la clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|  
|[CComMultiThreadModelNoCS::CriticalSection](../Topic/CComMultiThreadModelNoCS::CriticalSection.md)|Hace referencia a la clase `CComFakeCriticalSection`.|  
|[CComMultiThreadModelNoCS::ThreadModelNoCS](../Topic/CComMultiThreadModelNoCS::ThreadModelNoCS.md)|Hace referencia a la clase `CComMultiThreadModelNoCS`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComMultiThreadModelNoCS::Decrement](../Topic/CComMultiThreadModelNoCS::Decrement.md)|\(Estático\) disminuye el valor de la variable especificada de una manera segura para subprocesos.|  
|[CComMultiThreadModelNoCS::Increment](../Topic/CComMultiThreadModelNoCS::Increment.md)|\(Estático\) incrementa el valor de la variable especificada de una manera segura para subprocesos.|  
  
## Comentarios  
 `CComMultiThreadModelNoCS` es similar a [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) en que proporciona métodos seguros para subprocesos para aumentar y disminuir una variable.  Sin embargo, cuando se hace referencia a una clase de sección crítica con `CComMultiThreadModelNoCS`, métodos como `Lock` y `Unlock` no harán nada.  
  
 Normalmente, se utiliza `CComMultiThreadModelNoCS` con el nombre de `ThreadModelNoCS``typedef` .  Este `typedef` se define en `CComMultiThreadModelNoCS`, `CComMultiThreadModel`, y [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md).  
  
> [!NOTE]
>  Los nombres globales [CComObjectThreadModel](../Topic/CComObjectThreadModel.md) y [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md) de `typedef` no hacen referencia a `CComMultiThreadModelNoCS`.  
  
 Además de `ThreadModelNoCS`, `CComMultiThreadModelNoCS` define `AutoCriticalSection` y `CriticalSection`.  Referencia de estos la última dos nombres de `typedef`[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), que proporciona métodos vacíos asociado a obtener y liberar una sección crítica.  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)