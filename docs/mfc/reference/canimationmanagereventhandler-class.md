---
title: "CAnimationManagerEventHandler (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CAnimationManagerEventHandler"
  - "CAnimationManagerEventHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationManagerEventHandler (clase)"
ms.assetid: 6089ec07-e661-4805-b227-823b4652aade
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CAnimationManagerEventHandler (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa una devolución de llamada, a la que llama la API de animación cuando se cambia el estado de un administrador de animación.  
  
## Sintaxis  
  
```  
class CAnimationManagerEventHandler : public CUIAnimationManagerEventHandlerBase<CAnimationManagerEventHandler>;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationManagerEventHandler::CAnimationManagerEventHandler](../Topic/CAnimationManagerEventHandler::CAnimationManagerEventHandler.md)|Crea un objeto `CAnimationManagerEventHandler`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationManagerEventHandler::CreateInstance](../Topic/CAnimationManagerEventHandler::CreateInstance.md)|Crea una instancia del objeto de `CAnimationManagerEventHandler` .|  
|[CAnimationManagerEventHandler::OnManagerStatusChanged](../Topic/CAnimationManagerEventHandler::OnManagerStatusChanged.md)|Se llama cuando un estado de administrador de animaciones ha cambiado.  \(Reemplaza `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`.\)|  
|[CAnimationManagerEventHandler::SetAnimationController](../Topic/CAnimationManagerEventHandler::SetAnimationController.md)|Almacena un puntero al controlador de animación para enrutar eventos.|  
  
## Comentarios  
 Este controlador de eventos se crea y se pasa al método IUIAnimationManager::SetManagerEventHandler, al llamar a CAnimationController::EnableAnimationManagerEvent.  
  
## Jerarquía de herencia  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationManagerEventHandlerBase`  
  
 `CAnimationManagerEventHandler`  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)