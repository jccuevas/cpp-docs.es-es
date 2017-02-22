---
title: "CAnimationColor (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAnimationColor"
  - "afxanimationcontroller/CAnimationColor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationColor (clase)"
ms.assetid: 88bfabd4-efeb-4652-87e8-304253d8e48c
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CAnimationColor (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa la funcionalidad de un color cuyos componentes rojo, verde y azul se pueden animar.  
  
## Sintaxis  
  
```  
class CAnimationColor : public CAnimationBaseObject;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationColor::CAnimationColor](../Topic/CAnimationColor::CAnimationColor.md)|Sobrecargado.  Construye un objeto de color de animación.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationColor::AddTransition](../Topic/CAnimationColor::AddTransition.md)|Agrega transiciones para los componentes Rojo, Azul y Verde.|  
|[CAnimationColor::GetB](../Topic/CAnimationColor::GetB.md)|Proporciona acceso a CAnimationVariable que representa el componente Azul.|  
|[CAnimationColor::GetDefaultValue](../Topic/CAnimationColor::GetDefaultValue.md)|Devuelve los valores predeterminados para los componentes en color.|  
|[CAnimationColor::GetG](../Topic/CAnimationColor::GetG.md)|Proporciona acceso a CAnimationVariable que representa el componente Verde.|  
|[CAnimationColor::GetR](../Topic/CAnimationColor::GetR.md)|Proporciona acceso a CAnimationVariable que representa el componente Rojo.|  
|[CAnimationColor::GetValue](../Topic/CAnimationColor::GetValue.md)|Devuelve el valor actual.|  
|[CAnimationColor::SetDefaultValue](../Topic/CAnimationColor::SetDefaultValue.md)|Establece el valor predeterminado.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationColor::GetAnimationVariableList](../Topic/CAnimationColor::GetAnimationVariableList.md)|Coloca las variables de animación encapsuladas en una lista.  \(Invalida [CAnimationBaseObject::GetAnimationVariableList](../Topic/CAnimationBaseObject::GetAnimationVariableList.md).\)|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationColor::operator COLORREF](../Topic/CAnimationColor::operator%20COLORREF.md)||  
|[CAnimationColor::operator\=](../Topic/CAnimationColor::operator=.md)|Asigna color a CAnimationColor.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationColor::m\_bValue](../Topic/CAnimationColor::m_bValue.md)|La variable de animación encapsulada que representa el componente azul del color de animación.|  
|[CAnimationColor::m\_gValue](../Topic/CAnimationColor::m_gValue.md)|La variable de animación encapsulada que representa el componente verde del color de animación.|  
|[CAnimationColor::m\_rValue](../Topic/CAnimationColor::m_rValue.md)|La variable de animación encapsulada que representa el componente rojo del color de animación.|  
  
## Comentarios  
 La clase CAnimationColor encapsula tres objetos CAnimationVariable y puede representar un color en las aplicaciones.  Por ejemplo, puede utilizar esta clase para animar los colores de cualquier objeto en la pantalla \(como color del texto, color de fondo, etc.\).  Para utilizar esta clase en la aplicación, simplemente cree instancias de un objeto de esta clase, agréguelo al controlador de animación con CAnimationController::AddAnimationObject y llame a AddTransition para cada transición que se va a aplicar en los componentes Rojo, Verde y Azul.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 [CAnimationColor](../../mfc/reference/canimationcolor-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)