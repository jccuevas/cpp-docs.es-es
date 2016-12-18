---
title: "CComFakeCriticalSection Class | Microsoft Docs"
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
  - "ATL.CComFakeCriticalSection"
  - "CComFakeCriticalSection"
  - "ATL::CComFakeCriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComFakeCriticalSection class"
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComFakeCriticalSection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase proporciona los mismos métodos que [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) pero no proporciona una sección crítica.  
  
## Sintaxis  
  
```  
  
class CComFakeCriticalSection  
  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComFakeCriticalSection::Init](../Topic/CComFakeCriticalSection::Init.md)|No hace nada dado que no hay sección crítica.|  
|[CComFakeCriticalSection::Lock](../Topic/CComFakeCriticalSection::Lock.md)|No hace nada dado que no hay sección crítica.|  
|[CComFakeCriticalSection::Term](../Topic/CComFakeCriticalSection::Term.md)|No hace nada dado que no hay sección crítica.|  
|[CComFakeCriticalSection::Unlock](../Topic/CComFakeCriticalSection::Unlock.md)|No hace nada dado que no hay sección crítica.|  
  
## Comentarios  
 `CComFakeCriticalSection` refleja los métodos incluidos en [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).  sin embargo, `CComFakeCriticalSection` no proporciona una sección crítica; por consiguiente, los métodos no hacen nada.  
  
 Normalmente, se utiliza `CComFakeCriticalSection` con un nombre de `typedef` , `AutoCriticalSection` o `CriticalSection`.  Al utilizar [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) o [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), referencia de ambos nombres de `typedef``CComFakeCriticalSection`.  Al utilizar [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md), haga referencia [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md) y `CComCriticalSection`, respectivamente.  
  
## Requisitos  
 **encabezado:** atlcore.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)