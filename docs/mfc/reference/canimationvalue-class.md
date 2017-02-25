---
title: "CAnimationValue (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CAnimationValue"
  - "CAnimationValue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationValue (clase)"
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CAnimationValue (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa la funcionalidad del objeto de animación que tiene un valor.  
  
## Sintaxis  
  
```  
class CAnimationValue : public CAnimationBaseObject;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationValue::CAnimationValue](../Topic/CAnimationValue::CAnimationValue.md)|Sobrecargado.  Construye un objeto CAnimationValue.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationValue::AddTransition](../Topic/CAnimationValue::AddTransition.md)|Agrega una transición que se va a aplicar a un valor.|  
|[CAnimationValue::GetValue](../Topic/CAnimationValue::GetValue.md)|Sobrecargado.  Recupera el valor actual.|  
|[CAnimationValue::GetVariable](../Topic/CAnimationValue::GetVariable.md)|Proporciona acceso a la variable de animación encapsulada.|  
|[CAnimationValue::SetDefaultValue](../Topic/CAnimationValue::SetDefaultValue.md)|Establece el valor predeterminado.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationValue::GetAnimationVariableList](../Topic/CAnimationValue::GetAnimationVariableList.md)|Coloca la variable de animación encapsulada en una lista.  \(Invalida [CAnimationBaseObject::GetAnimationVariableList](../Topic/CAnimationBaseObject::GetAnimationVariableList.md).\)|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationValue::operator DOUBLE](../Topic/CAnimationValue::operator%20DOUBLE.md)|Proporciona la conversión entre CAnimationValue y DOUBLE.|  
|[CAnimationValue::operator INT32](../Topic/CAnimationValue::operator%20INT32.md)|Proporciona la conversión entre CAnimationValue e INT32.|  
|[CAnimationValue::operator\=](../Topic/CAnimationValue::operator=.md)|Sobrecargado.  Asigna un valor INT32 a CAnimationValue.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationValue::m\_value](../Topic/CAnimationValue::m_value.md)|La variable de animación encapsulada que representa el valor de animación.|  
  
## Comentarios  
 La clase CAnimationValue encapsula un objeto CAnimationVariable único y puede representar un valor único animado en las aplicaciones.  Por ejemplo, puede utilizar esta clase para transparencia animada \(efecto de atenuación\), ángulo \(para girar objetos\) o para cualquier otro caso, cuando se necesite crear una animación en función de un único valor animado único.  Para utilizar esta clase en la aplicación, simplemente cree instancias de un objeto de esta clase, agréguelo al controlador de animación con CAnimationController::AddAnimationObject y llame a AddTransition para cada transición que se va a aplicar al valor.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 [CAnimationValue](../../mfc/reference/canimationvalue-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)