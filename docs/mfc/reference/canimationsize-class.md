---
title: "CAnimationSize (Clase) | Microsoft Docs"
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
  - "afxanimationcontroller/CAnimationSize"
  - "CAnimationSize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationSize (clase)"
ms.assetid: ea06d1b5-502c-44a3-82ca-8bd6ba6a9364
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAnimationSize (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa la funcionalidad de un objeto cuyas dimensiones se pueden animar.  
  
## Sintaxis  
  
```  
class CAnimationSize : public CAnimationBaseObject;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationSize::CAnimationSize](../Topic/CAnimationSize::CAnimationSize.md)|Sobrecargado.  Construye un objeto de tamaño de animación.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationSize::AddTransition](../Topic/CAnimationSize::AddTransition.md)|Agrega transiciones para Ancho y Alto.|  
|[CAnimationSize::GetCX](../Topic/CAnimationSize::GetCX.md)|Proporciona acceso a CAnimationVariable que representa Ancho.|  
|[CAnimationSize::GetCY](../Topic/CAnimationSize::GetCY.md)|Proporciona acceso a CAnimationVariable que representa Alto.|  
|[CAnimationSize::GetDefaultValue](../Topic/CAnimationSize::GetDefaultValue.md)|Devuelve los valores predeterminados para Ancho y Alto.|  
|[CAnimationSize::GetValue](../Topic/CAnimationSize::GetValue.md)|Devuelve el valor actual.|  
|[CAnimationSize::SetDefaultValue](../Topic/CAnimationSize::SetDefaultValue.md)|Establece el valor predeterminado.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationSize::GetAnimationVariableList](../Topic/CAnimationSize::GetAnimationVariableList.md)|Coloca las variables de animación encapsuladas en una lista.  \(Invalida [CAnimationBaseObject::GetAnimationVariableList](../Topic/CAnimationBaseObject::GetAnimationVariableList.md).\)|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationSize::operator CSize](../Topic/CAnimationSize::operator%20CSize.md)|Convierte un CAnimationSize en un CSize.|  
|[CAnimationSize::operator\=](../Topic/CAnimationSize::operator=.md)|Asigna szSrc a CAnimationSize.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationSize::m\_cxValue](../Topic/CAnimationSize::m_cxValue.md)|La variable de animación encapsulada que representa ancho del tamaño de animación.|  
|[CAnimationSize::m\_cyValue](../Topic/CAnimationSize::m_cyValue.md)|La variable de animación encapsulada que representa alto del tamaño de animación.|  
  
## Comentarios  
 La clase CAnimationSize encapsula dos objetos CAnimationVariable y puede representar un tamaño en las aplicaciones.  Por ejemplo, puede utilizar esta clase para animar el tamaño de cualquier objeto bidimensional en la pantalla \(como rectángulo, control, etc.\).  Para utilizar esta clase en la aplicación, simplemente cree instancias de un objeto de esta clase, agréguelo al controlador de animación con CAnimationController::AddAnimationObject y llame a AddTransition para cada transición que se va a aplicar a Ancho o Alto.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 [CAnimationSize](../../mfc/reference/canimationsize-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)