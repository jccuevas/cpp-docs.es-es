---
title: "CAnimationPoint (Clase) | Microsoft Docs"
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
  - "CAnimationPoint"
  - "afxanimationcontroller/CAnimationPoint"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationPoint (clase)"
ms.assetid: 5dc4d46f-e695-4681-b15c-544b78b3e317
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAnimationPoint (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa la funcionalidad de un punto cuyas coordenadas se pueden animar.  
  
## Sintaxis  
  
```  
class CAnimationPoint : public CAnimationBaseObject;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationPoint::CAnimationPoint](../Topic/CAnimationPoint::CAnimationPoint.md)|Sobrecargado.  Construye el objeto CAnimationPoint.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationPoint::AddTransition](../Topic/CAnimationPoint::AddTransition.md)|Agrega transiciones para las coordenadas X e Y.|  
|[CAnimationPoint::GetDefaultValue](../Topic/CAnimationPoint::GetDefaultValue.md)|Devuelve los valores predeterminados para las coordenadas X e Y.|  
|[CAnimationPoint::GetValue](../Topic/CAnimationPoint::GetValue.md)|Devuelve el valor actual.|  
|[CAnimationPoint::GetX](../Topic/CAnimationPoint::GetX.md)|Proporciona acceso a CAnimationVariable para la coordenada X.|  
|[CAnimationPoint::GetY](../Topic/CAnimationPoint::GetY.md)|Proporciona acceso a CAnimationVariable para la coordenada Y.|  
|[CAnimationPoint::SetDefaultValue](../Topic/CAnimationPoint::SetDefaultValue.md)|Establece el valor predeterminado.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationPoint::GetAnimationVariableList](../Topic/CAnimationPoint::GetAnimationVariableList.md)|Coloca las variables de animación encapsuladas en una lista.  \(Invalida [CAnimationBaseObject::GetAnimationVariableList](../Topic/CAnimationBaseObject::GetAnimationVariableList.md).\)|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationPoint::operator CPoint](../Topic/CAnimationPoint::operator%20CPoint.md)|Convierte un CAnimationPoint en un CPoint.|  
|[CAnimationPoint::operator\=](../Topic/CAnimationPoint::operator=.md)|Asigna ptSrc a CAnimationPoint.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationPoint::m\_xValue](../Topic/CAnimationPoint::m_xValue.md)|La variable de animación encapsulada que representa la coordenada X del punto de animación.|  
|[CAnimationPoint::m\_yValue](../Topic/CAnimationPoint::m_yValue.md)|La variable de animación encapsulada que representa la coordenada Y del punto de animación.|  
  
## Comentarios  
 La clase CAnimationPoint encapsula dos objetos CAnimationVariable y puede representar un punto en las aplicaciones.  Por ejemplo, puede utilizar esta clase para animar una posición de cualquier objeto en la pantalla \(como cadena de texto, círculo, punto, etc.\).  Para utilizar esta clase en la aplicación, simplemente cree instancias de un objeto de esta clase, agréguelo al controlador de animación con CAnimationController::AddAnimationObject y llame a AddTransition para cada transición que se va a aplicar en las coordenadas X e Y.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 [CAnimationPoint](../../mfc/reference/canimationpoint-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)