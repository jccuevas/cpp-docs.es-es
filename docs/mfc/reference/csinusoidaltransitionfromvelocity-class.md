---
title: "CSinusoidalTransitionFromVelocity (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSinusoidalTransitionFromVelocity"
  - "afxanimationcontroller/CSinusoidalTransitionFromVelocity"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSinusoidalTransitionFromVelocity (clase)"
ms.assetid: cc885f17-b84b-45ee-8f1f-36a8bbb7adad
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CSinusoidalTransitionFromVelocity (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula una transición de progreso sinusoidal cuya amplitud determina el progreso inicial de la variable de animación.  
  
## Sintaxis  
  
```  
class CSinusoidalTransitionFromVelocity : public CBaseTransition;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSinusoidalTransitionFromVelocity::CSinusoidalTransitionFromVelocity](../Topic/CSinusoidalTransitionFromVelocity::CSinusoidalTransitionFromVelocity.md)|Construye un objeto de transición.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSinusoidalTransitionFromVelocity::Create](../Topic/CSinusoidalTransitionFromVelocity::Create.md)|Llama a la biblioteca de transiciones para crear el objeto COM de transición encapsulado.  \(Invalida [CBaseTransition::Create](../Topic/CBaseTransition::Create.md).\)|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSinusoidalTransitionFromVelocity::m\_duration](../Topic/CSinusoidalTransitionFromVelocity::m_duration.md)|Duración de la transición.|  
|[CSinusoidalTransitionFromVelocity::m\_period](../Topic/CSinusoidalTransitionFromVelocity::m_period.md)|El período de oscilación de la onda sinusoidal en segundos.|  
  
## Comentarios  
 El valor de la variable de animación oscila alrededor del valor inicial sobre la duración completa de una transición de rango sinusoidal.  El progreso de la variable de animación determina la amplitud de la oscilación cuando la transición comienza.  Como todas las transiciones se desactivan automáticamente, se recomienda asignarlas mediante "operator new".  CAnimationController::AnimateGroup crea el objeto COM encapsulado IUIAnimationTransition que hasta entonces es NULL.  Cambiar las variables miembro después de que la creación de este objeto COM no tiene ningún efecto.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CSinusoidalTransitionFromVelocity](../../mfc/reference/csinusoidaltransitionfromvelocity-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)