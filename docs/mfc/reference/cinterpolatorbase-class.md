---
title: "CInterpolatorBase (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CInterpolatorBase"
  - "CInterpolatorBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInterpolatorBase (clase)"
ms.assetid: bbc3dce7-8398-47f9-b97e-e4fd2d737232
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CInterpolatorBase (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa una devolución de llamada, a la que llama la API de animación cuando tiene que calcular un nuevo valor de una variable de animación.  
  
## Sintaxis  
  
```  
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInterpolatorBase::CInterpolatorBase](../Topic/CInterpolatorBase::CInterpolatorBase.md)|Construye el objeto de `CInterpolatorBase` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInterpolatorBase::CreateInstance](../Topic/CInterpolatorBase::CreateInstance.md)|Crea una instancia de `CInterpolatorBase` y almacena un puntero al interpolador personalizado, que administrará eventos.|  
|[CInterpolatorBase::GetDependencies](../Topic/CInterpolatorBase::GetDependencies.md)|Obtiene las dependencias del interpolador.  \(Reemplaza `CUIAnimationInterpolatorBase::GetDependencies`.\)|  
|[CInterpolatorBase::GetDuration](../Topic/CInterpolatorBase::GetDuration.md)|Obtiene la duración del interpolador.  \(Reemplaza `CUIAnimationInterpolatorBase::GetDuration`.\)|  
|[CInterpolatorBase::GetFinalValue](../Topic/CInterpolatorBase::GetFinalValue.md)|Obtiene el valor final al que conduce el interpolador.  \(Reemplaza `CUIAnimationInterpolatorBase::GetFinalValue`.\)|  
|[CInterpolatorBase::InterpolateValue](../Topic/CInterpolatorBase::InterpolateValue.md)|Interpola el valor en un desplazamiento especificado \(reemplaza `CUIAnimationInterpolatorBase::InterpolateValue`.\)|  
|[CInterpolatorBase::InterpolateVelocity](../Topic/CInterpolatorBase::InterpolateVelocity.md)|Interpola la velocidad en un desplazamiento especificado \(reemplaza `CUIAnimationInterpolatorBase::InterpolateVelocity`.\)|  
|[CInterpolatorBase::SetCustomInterpolator](../Topic/CInterpolatorBase::SetCustomInterpolator.md)|Almacena un puntero al interpolador personalizado, que administrará los eventos.|  
|[CInterpolatorBase::SetDuration](../Topic/CInterpolatorBase::SetDuration.md)|Establece la duración de interpolador \(reemplaza `CUIAnimationInterpolatorBase::SetDuration`.\)|  
|[CInterpolatorBase::SetInitialValueAndVelocity](../Topic/CInterpolatorBase::SetInitialValueAndVelocity.md)|Establece el valor inicial y el progreso del interpolador.  \(Reemplaza `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`.\)|  
  
## Comentarios  
 Crean y se pasan a este controlador a `IUIAnimationTransitionFactory::CreateTransition` cuando se crea un objeto de `CCustomTransition` como parte del proceso de inicialización de animación \(iniciado por `CAnimationController::AnimateGroup`\).  No necesita normalmente utilizar esta clase directamente, simplemente encamina todos los eventos a `CCustomInterpolator`\- la clase derivada, cuyo puntero se pasa al constructor de `CCustomTransition`.  
  
## Jerarquía de herencia  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationInterpolatorBase`  
  
 `CInterpolatorBase`  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)