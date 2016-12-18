---
title: "CAnimationStoryboardEventHandler Class | Microsoft Docs"
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
  - "afxanimationcontroller/CAnimationStoryboardEventHandler"
  - "CAnimationStoryboardEventHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationStoryboardEventHandler (clase)"
ms.assetid: 10a7e86b-c02d-4124-9a2e-61ecf8ac62fc
caps.latest.revision: 18
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAnimationStoryboardEventHandler Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa una devolución de llamada, a la que llama la API de animación cuando se cambia el estado de un guión gráfico o se actualiza.  
  
## Sintaxis  
  
```  
class CAnimationStoryboardEventHandler : public CUIAnimationStoryboardEventHandlerBase<CAnimationStoryboardEventHandler>;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler](../Topic/CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler.md)|Crea un objeto `CAnimationStoryboardEventHandler`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationStoryboardEventHandler::CreateInstance](../Topic/CAnimationStoryboardEventHandler::CreateInstance.md)|Crea una instancia de devolución de `CAnimationStoryboardEventHandler` .|  
|[CAnimationStoryboardEventHandler::OnStoryboardStatusChanged](../Topic/CAnimationStoryboardEventHandler::OnStoryboardStatusChanged.md)|Administra los eventos de `OnStoryboardStatusChanged` , que aparecen cuando cambia el estado de un guión gráfico \(reemplaza `CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged`.\)|  
|[CAnimationStoryboardEventHandler::OnStoryboardUpdated](../Topic/CAnimationStoryboardEventHandler::OnStoryboardUpdated.md)|Administra los eventos de `OnStoryboardUpdated` , que aparecen cuando se actualiza un guión gráfico \(reemplaza `CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated`.\)|  
|[CAnimationStoryboardEventHandler::SetAnimationController](../Topic/CAnimationStoryboardEventHandler::SetAnimationController.md)|Almacena un puntero al controlador de animación para enrutar eventos.|  
  
## Comentarios  
 Crean y se pasan a este controlador de eventos a `IUIAnimationStoryboard::SetStoryboardEventHandler` método, cuando se llama a `CAnimationController::EnableStoryboardEventHandler`.  
  
## Jerarquía de herencia  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationStoryboardEventHandlerBase`  
  
 `CAnimationStoryboardEventHandler`  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)