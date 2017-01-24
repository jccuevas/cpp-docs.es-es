---
title: "CSinusoidalTransitionFromRange (Clase) | Microsoft Docs"
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
  - "afxanimationcontroller/CSinusoidalTransitionFromRange"
  - "CSinusoidalTransitionFromRange"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSinusoidalTransitionFromRange (clase)"
ms.assetid: 8b66a729-5f10-431a-b055-e3600d0065da
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSinusoidalTransitionFromRange (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula una transición de intervalo sinusoidal que tiene un intervalo determinado de oscilación.  
  
## Sintaxis  
  
```  
class CSinusoidalTransitionFromRange : public CBaseTransition;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange](../Topic/CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange.md)|Construye un objeto de transición.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSinusoidalTransitionFromRange::Create](../Topic/CSinusoidalTransitionFromRange::Create.md)|Llama a la biblioteca de transiciones para crear el objeto COM de transición encapsulado.  \(Invalida [CBaseTransition::Create](../Topic/CBaseTransition::Create.md).\)|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSinusoidalTransitionFromRange::m\_dblMaximumValue](../Topic/CSinusoidalTransitionFromRange::m_dblMaximumValue.md)|El valor de la variable de animación en el valor máximo de la onda sinusoidal.|  
|[CSinusoidalTransitionFromRange::m\_dblMinimumValue](../Topic/CSinusoidalTransitionFromRange::m_dblMinimumValue.md)|El valor de la variable de animación en el valor mínimo de la onda sinusoidal.|  
|[CSinusoidalTransitionFromRange::m\_duration](../Topic/CSinusoidalTransitionFromRange::m_duration.md)|Duración de la transición.|  
|[CSinusoidalTransitionFromRange::m\_period](../Topic/CSinusoidalTransitionFromRange::m_period.md)|El período de oscilación de la onda sinusoidal en segundos.|  
|[CSinusoidalTransitionFromRange::m\_slope](../Topic/CSinusoidalTransitionFromRange::m_slope.md)|La inclinación al principio de la transición.|  
  
## Comentarios  
 El valor de la variable de animación fluctúa entre los valores mínimos y máximos especificados sobre la duración completa de una transición de rango sinusoidal.  El parámetro de pendiente se utiliza para eliminar la ambigüedad entre las dos posibles ondas del seno especificada por los otros parámetros.  Como todas las transiciones se desactivan automáticamente, se recomienda asignarlas mediante "operator new".  CAnimationController::AnimateGroup crea el objeto COM encapsulado IUIAnimationTransition que hasta entonces es NULL.  Cambiar las variables miembro después de que la creación de este objeto COM no tiene ningún efecto.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CSinusoidalTransitionFromRange](../../mfc/reference/csinusoidaltransitionfromrange-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)