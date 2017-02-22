---
title: "CAnimationTimerEventHandler (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CAnimationTimerEventHandler"
  - "CAnimationTimerEventHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationTimerEventHandler (clase)"
ms.assetid: 188dea3b-4b5e-4f6b-8df9-09d993a21619
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CAnimationTimerEventHandler (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa una devolución de llamada, a la que llama la API de animación cuando se producen eventos de control de tiempo.  
  
## Sintaxis  
  
```  
class CAnimationTimerEventHandler : public CUIAnimationTimerEventHandlerBase<CAnimationTimerEventHandler>;  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationTimerEventHandler::CreateInstance](../Topic/CAnimationTimerEventHandler::CreateInstance.md)|Crea una instancia de devolución de `CAnimationTimerEventHandler` .|  
|[CAnimationTimerEventHandler::OnPostUpdate](../Topic/CAnimationTimerEventHandler::OnPostUpdate.md)|Administra eventos que se producen una vez finalizada una actualización de animación.  \(Reemplaza `CUIAnimationTimerEventHandlerBase::OnPostUpdate`.\)|  
|[CAnimationTimerEventHandler::OnPreUpdate](../Topic/CAnimationTimerEventHandler::OnPreUpdate.md)|Administra eventos que se producen antes del comienzo de una actualización de animación.  \(Reemplaza `CUIAnimationTimerEventHandlerBase::OnPreUpdate`.\)|  
|[CAnimationTimerEventHandler::OnRenderingTooSlow](../Topic/CAnimationTimerEventHandler::OnRenderingTooSlow.md)|Controla los eventos que se producen cuando la velocidad de fotogramas de representación para una animación se sitúa por debajo de la velocidad de fotogramas mínima deseable.  \(Reemplaza `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`.\)|  
|[CAnimationTimerEventHandler::SetAnimationController](../Topic/CAnimationTimerEventHandler::SetAnimationController.md)|Almacena un puntero al controlador de animación para enrutar eventos.|  
  
## Comentarios  
 Este controlador de eventos se crea y se pasa a IUIAnimationTimer::SetTimerEventHandler al llamar a CAnimationController::EnableAnimationTimerEventHandler.  
  
## Jerarquía de herencia  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationTimerEventHandlerBase`  
  
 `CAnimationTimerEventHandler`  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)