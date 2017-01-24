---
title: "CMessageMap Class | Microsoft Docs"
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
  - "CMessageMap"
  - "ATL.CMessageMap"
  - "ATL::CMessageMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, controladores de mensajes"
  - "CMessageMap class"
  - "message maps, ATL"
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMessageMap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase permite que los mapas de mensajes de un objeto tengan acceso al lado de otro objeto.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class ATL_NO_VTABLE CMessageMap  
  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMessageMap::ProcessWindowMessage](../Topic/CMessageMap::ProcessWindowMessage.md)|Tiene acceso a un mensaje asignado en `CMessageMap`\- clase derivada.|  
  
## Comentarios  
 `CMessageMap` es una clase abstracta que permite que los mapas de mensajes de un objeto tengan acceso a ellos otro objeto.  Para que un objeto exponer los mapas de mensajes, la clase debe derivar de `CMessageMap`.  
  
 Aplicaciones `CMessageMap` ATL de admitir las ventanas incluidas y el encadenamiento dinámico del mapa de mensajes.  Por ejemplo, no se ordenan contener un objeto de [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) deben derivar de `CMessageMap`.  El siguiente código se toma del ejemplo de [SUBEDIT](../../top/visual-cpp-samples.md) .  Con [CComControl](../../atl/reference/ccomcontrol-class.md), la clase de `CAtlEdit` automáticamente deriva de `CMessageMap`.  
  
 [!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/CPP/cmessagemap-class_1.h)]  
  
 Dado que la ventana contenida, `m_EditCtrl`, utilizará un mensaje asignado en la clase contenedora, `CAtlEdit` deriva de `CMessageMap`.  
  
 Para obtener más información sobre asignación de mensajes, vea [Mapas de mensajes](../../atl/message-maps-atl.md) en el artículo “clases de ventana ATL.”  
  
## Requisitos  
 **encabezado:** atlwin.h  
  
## Vea también  
 [CDynamicChain Class](../../atl/reference/cdynamicchain-class.md)   
 [BEGIN\_MSG\_MAP](../Topic/BEGIN_MSG_MAP.md)   
 [ALT\_MSG\_MAP](../Topic/ALT_MSG_MAP.md)   
 [Class Overview](../../atl/atl-class-overview.md)