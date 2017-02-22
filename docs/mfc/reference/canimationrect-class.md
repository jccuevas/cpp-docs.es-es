---
title: "CAnimationRect (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAnimationRect"
  - "afxanimationcontroller/CAnimationRect"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationRect (clase)"
ms.assetid: 0294156d-241e-4a57-92b2-31234fe557d6
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CAnimationRect (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa la funcionalidad de un rectángulo cuyos lados se pueden animar.  
  
## Sintaxis  
  
```  
class CAnimationRect : public CAnimationBaseObject;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationRect::CAnimationRect](../Topic/CAnimationRect::CAnimationRect.md)|Sobrecargado.  Construye un objeto de animación Rect.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationRect::AddTransition](../Topic/CAnimationRect::AddTransition.md)|Agrega transiciones para las coordenadas izquierda, superior, derecha e inferior.|  
|[CAnimationRect::GetBottom](../Topic/CAnimationRect::GetBottom.md)|Proporciona acceso a CAnimationVariable que representa la coordenada inferior.|  
|[CAnimationRect::GetDefaultValue](../Topic/CAnimationRect::GetDefaultValue.md)|Devuelve los valores predeterminado para los límites del rectángulo.|  
|[CAnimationRect::GetLeft](../Topic/CAnimationRect::GetLeft.md)|Proporciona acceso a CAnimationVariable que representa la coordenada izquierda.|  
|[CAnimationRect::GetRight](../Topic/CAnimationRect::GetRight.md)|Proporciona acceso a CAnimationVariable que representa la coordenada derecha.|  
|[CAnimationRect::GetTop](../Topic/CAnimationRect::GetTop.md)|Proporciona acceso a CAnimationVariable que representa la coordenada superior.|  
|[CAnimationRect::GetValue](../Topic/CAnimationRect::GetValue.md)|Devuelve el valor actual.|  
|[CAnimationRect::SetDefaultValue](../Topic/CAnimationRect::SetDefaultValue.md)|Establece el valor predeterminado.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationRect::GetAnimationVariableList](../Topic/CAnimationRect::GetAnimationVariableList.md)|Coloca las variables de animación encapsuladas en una lista.  \(Invalida [CAnimationBaseObject::GetAnimationVariableList](../Topic/CAnimationBaseObject::GetAnimationVariableList.md).\)|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationRect::operator RECT](../Topic/CAnimationRect::operator%20RECT.md)|Convierte un CAnimationRect en RECT.|  
|[CAnimationRect::operator\=](../Topic/CAnimationRect::operator=.md)|Asigna Rect a CAnimationRect.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationRect::m\_bFixedSize](../Topic/CAnimationRect::m_bFixedSize.md)|Especifica si el rectángulo tiene un tamaño fijo.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationRect::m\_bottomValue](../Topic/CAnimationRect::m_bottomValue.md)|La variable de animación encapsulada que representa límite inferior del rectángulo de animación.|  
|[CAnimationRect::m\_leftValue](../Topic/CAnimationRect::m_leftValue.md)|La variable de animación encapsulada que representa límite izquierdo del rectángulo de animación.|  
|[CAnimationRect::m\_rightValue](../Topic/CAnimationRect::m_rightValue.md)|La variable de animación encapsulada que representa límite derecho del rectángulo de animación.|  
|[CAnimationRect::m\_szInitial](../Topic/CAnimationRect::m_szInitial.md)|Especifica tamaño inicial del rectángulo de animación.|  
|[CAnimationRect::m\_topValue](../Topic/CAnimationRect::m_topValue.md)|La variable de animación encapsulada que representa límite superior del rectángulo de animación.|  
  
## Comentarios  
 La clase CAnimationRect encapsula cuatro objetos CAnimationVariable y puede representar un rectángulo en las aplicaciones.  Para utilizar esta clase en la aplicación, simplemente cree instancias de un objeto de esta clase, agréguelo al controlador de animación con CAnimationController::AddAnimationObject y llame a AddTransition para cada transición que se va a aplicar en las coordenadas izquierda, derecha, superior e inferior.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 [CAnimationRect](../../mfc/reference/canimationrect-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)