---
title: "CComCriticalSection Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComCriticalSection"
  - "CComCriticalSection"
  - "ATL::CComCriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComCriticalSection class"
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CComCriticalSection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.  
  
## Sintaxis  
  
```  
  
class CComCriticalSection  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCriticalSection::CComCriticalSection](../Topic/CComCriticalSection::CComCriticalSection.md)|el constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCriticalSection::Init](../Topic/CComCriticalSection::Init.md)|Crea e inicializa un objeto de sección crítica.|  
|[CComCriticalSection::Lock](../Topic/CComCriticalSection::Lock.md)|Obtiene la propiedad del objeto de sección crítica.|  
|[CComCriticalSection::Term](../Topic/CComCriticalSection::Term.md)|Los recursos del sistema de las versiones utilizados por la sección crítica se oponen.|  
|[CComCriticalSection::Unlock](../Topic/CComCriticalSection::Unlock.md)|Libera la propiedad del objeto de sección crítica.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCriticalSection::m\_sec](../Topic/CComCriticalSection::m_sec.md)|un objeto de **CRITICAL\_SECTION** .|  
  
## Comentarios  
 `CComCriticalSection` es similar ordenar [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md), excepto que debe explícitamente inicializar y liberar la sección crítica.  
  
 Normalmente, se utiliza `CComCriticalSection` con el nombre [CriticalSection](../Topic/CComMultiThreadModel::CriticalSection.md)de `typedef` .  Referencias de este nombre `CComCriticalSection` cuando se utiliza [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) .  
  
 Vea [clase de CComCritSecLock](../../atl/reference/ccomcritseclock-class.md) para que una forma más segura utilice esta clase que llamando a `Lock` y `Unlock` directamente.  
  
## Requisitos  
 **Header:** atlcore.h  
  
## Vea también  
 [CComFakeCriticalSection Class](../../atl/reference/ccomfakecriticalsection-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComCritSecLock Class](../../atl/reference/ccomcritseclock-class.md)