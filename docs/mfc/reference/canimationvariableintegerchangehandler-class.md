---
title: "CAnimationVariableIntegerChangeHandler Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CAnimationVariableIntegerChangeHandler"
  - "CAnimationVariableIntegerChangeHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationVariableIntegerChangeHandler (clase)"
ms.assetid: 6ac8e91b-e514-4ff6-babd-33f77c4b2b61
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CAnimationVariableIntegerChangeHandler Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa una devolución de llamada, a la que llama la API de animación cuando cambia el valor de una animación.  
  
## Sintaxis  
  
```  
class CAnimationVariableIntegerChangeHandler : public CUIAnimationVariableIntegerChangeHandlerBase<CAnimationVariableIntegerChangeHandler>;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler](../Topic/CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler.md)|Crea un objeto `CAnimationVariableIntegerChangeHandler`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationVariableIntegerChangeHandler::CreateInstance](../Topic/CAnimationVariableIntegerChangeHandler::CreateInstance.md)|Crea una instancia de devolución de `CAnimationVariableIntegerChangeHandler` .|  
|[CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged](../Topic/CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged.md)|Llamado cuando un valor de una variable de animación ha cambiado.  \(Reemplaza `CUIAnimationVariableIntegerChangeHandlerBase::OnIntegerValueChanged`.\)|  
|[CAnimationVariableIntegerChangeHandler::SetAnimationController](../Topic/CAnimationVariableIntegerChangeHandler::SetAnimationController.md)|Almacena un puntero al controlador de animación para enrutar eventos.|  
  
## Comentarios  
 Este controlador de eventos se crea y pasa al método IUIAnimationVariable::SetVariableIntegerChangeHandler, al llamar a CAnimationVariable::EnableIntegerValueChangedEvent o CAnimationBaseObject::EnableIntegerValueChangedEvent \(qué habilita este evento para todas las variables de animación encapsuladas en un objeto de animación\).  
  
## Jerarquía de herencia  
 [Clases MFC](../../mfc/reference/mfc-classes.md)  
  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationVariableIntegerChangeHandlerBase`  
  
 `CAnimationVariableIntegerChangeHandler`  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)