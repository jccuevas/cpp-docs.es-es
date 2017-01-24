---
title: "CComSafeDeleteCriticalSection Class | Microsoft Docs"
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
  - "CComSafeDeleteCriticalSection"
  - "ATL::CComSafeDeleteCriticalSection"
  - "ATL.CComSafeDeleteCriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComSafeDeleteCriticalSection class"
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComSafeDeleteCriticalSection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.  
  
## Sintaxis  
  
```  
  
class CComSafeDeleteCriticalSection : public CComCriticalSection  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](../Topic/CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection.md)|el constructor.|  
|[CComSafeDeleteCriticalSection::~CComSafeDeleteCriticalSection](../Topic/CComSafeDeleteCriticalSection::~CComSafeDeleteCriticalSection.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComSafeDeleteCriticalSection::Init](../Topic/CComSafeDeleteCriticalSection::Init.md)|Crea e inicializa un objeto de sección crítica.|  
|[CComSafeDeleteCriticalSection::Lock](../Topic/CComSafeDeleteCriticalSection::Lock.md)|Obtiene la propiedad del objeto de sección crítica.|  
|[CComSafeDeleteCriticalSection::Term](../Topic/CComSafeDeleteCriticalSection::Term.md)|Los recursos del sistema de las versiones utilizados por la sección crítica se oponen.|  
  
### miembros de datos  
  
|||  
|-|-|  
|[m\_bInitialized](../Topic/CComSafeDeleteCriticalSection::m_bInitialized.md)|Marca si se ha inicializado el objeto interno de **CRITICAL\_SECTION** .|  
  
## Comentarios  
 `CComSafeDeleteCriticalSection` deriva de la clase [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).  Sin embargo, `CComSafeDeleteCriticalSection` proporciona mecanismos de seguridad adicionales sobre [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).  
  
 Cuando una instancia de `CComSafeDeleteCriticalSection` sale de ámbito o explícitamente se elimina de memoria, el objeto subyacente de la sección crítica automáticamente se limpian si todavía es válido.  Además, el método de [CComSafeDeleteCriticalSection::Term](../Topic/CComSafeDeleteCriticalSection::Term.md) saldrá correctamente si el objeto subyacente de la sección crítica todavía no se ha asignado o se ha publicado una de memoria.  
  
 Vea [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) para obtener más información sobre clases auxiliares de sección crítica.  
  
## Jerarquía de herencia  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComSafeDeleteCriticalSection`  
  
## Requisitos  
 **Header:** atlcore.h  
  
## Vea también  
 [CComCriticalSection Class](../../atl/reference/ccomcriticalsection-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)