---
title: "CAnimationVariableChangeHandler (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CAnimationVariableChangeHandler"
  - "CAnimationVariableChangeHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationVariableChangeHandler (clase)"
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CAnimationVariableChangeHandler (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa una devolución de llamada, a la que llama la API de animación cuando cambia el valor de una animación.  
  
## Sintaxis  
  
```  
class CAnimationVariableChangeHandler : public CUIAnimationVariableChangeHandlerBase<CAnimationVariableChangeHandler>;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CAnimationVariableChangeHandler::CAnimationVariableChangeHandler`|Crea un objeto `CAnimationVariableChangeHandler`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CAnimationVariableChangeHandler::CreateInstance`|Crea una instancia del objeto de `CAnimationVariableChangeHandler` .|  
|[CAnimationVariableChangeHandler::OnValueChanged](../Topic/CAnimationVariableChangeHandler::OnValueChanged.md)|Llamado cuando un valor de una variable de animación ha cambiado.  \(Reemplaza `CUIAnimationVariableChangeHandlerBase::OnValueChanged`.\)|  
|[CAnimationVariableChangeHandler::SetAnimationController](../Topic/CAnimationVariableChangeHandler::SetAnimationController.md)|Almacena un puntero al controlador de animación para enrutar eventos.|  
  
## Comentarios  
 Crean y se pasan a este controlador de eventos a `IUIAnimationVariable::SetVariableChangeHandler` método, cuando se llama a `CAnimationVariable::EnableValueChangedEvent` o `CAnimationBaseObject::EnableValueChangedEvent` \(que habilita este evento para todas las variables de animación encapsulados en un objeto de animación\).  
  
## Jerarquía de herencia  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationVariableChangeHandlerBase`  
  
 `CAnimationVariableChangeHandler`  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)