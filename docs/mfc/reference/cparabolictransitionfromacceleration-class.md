---
title: "CParabolicTransitionFromAcceleration Class | Microsoft Docs"
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
  - "afxanimationcontroller/CParabolicTransitionFromAcceleration"
  - "CParabolicTransitionFromAcceleration"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CParabolicTransitionFromAcceleration (clase)"
ms.assetid: 1e59b86f-358b-4da0-a4fd-8eaf5e85e00f
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CParabolicTransitionFromAcceleration Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula una transición de aceleración parabólica.  
  
## Sintaxis  
  
```  
class CParabolicTransitionFromAcceleration : public CBaseTransition;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration](../Topic/CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration.md)|Construye una transición de la aceleración parabólica y lo inicializa con parámetros especificados.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CParabolicTransitionFromAcceleration::Create](../Topic/CParabolicTransitionFromAcceleration::Create.md)|Llama a la biblioteca de transiciones para crear el objeto COM de transición encapsulado.  \(Invalida [CBaseTransition::Create](../Topic/CBaseTransition::Create.md).\)|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CParabolicTransitionFromAcceleration::m\_dblAcceleration](../Topic/CParabolicTransitionFromAcceleration::m_dblAcceleration.md)|La aceleración de la variable de animación durante la transición.|  
|[CParabolicTransitionFromAcceleration::m\_dblFinalValue](../Topic/CParabolicTransitionFromAcceleration::m_dblFinalValue.md)|El valor final de una variable de animación al final de la transición.|  
|[CParabolicTransitionFromAcceleration::m\_dblFinalVelocity](../Topic/CParabolicTransitionFromAcceleration::m_dblFinalVelocity.md)|El progreso de una variable de animación al final de la transición.|  
  
## Comentarios  
 Durante una transición de aceleración parabólica, el valor de la variable de animación cambia del valor inicial al valor final determinado finalizando en un progreso especificado.  Puede controlar la velocidad con la que la variable alcanza el valor final especificando la tasa de aceleración.  Como todas las transiciones se desactivan automáticamente, se recomienda asignarlas mediante "operator new".  CAnimationController::AnimateGroup crea el objeto COM encapsulado IUIAnimationTransition que hasta entonces es NULL.  Cambiar las variables miembro después de que la creación de este objeto COM no tiene ningún efecto.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CParabolicTransitionFromAcceleration](../../mfc/reference/cparabolictransitionfromacceleration-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)