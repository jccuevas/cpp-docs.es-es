---
title: "CCustomInterpolator (Clase) | Microsoft Docs"
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
  - "afxanimationcontroller/CCustomInterpolator"
  - "CCustomInterpolator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCustomInterpolator (clase)"
ms.assetid: 28d85595-989a-40a3-b003-e0e38437a94d
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCustomInterpolator (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa un interpolador básico.  
  
## Sintaxis  
  
```  
class CCustomInterpolator;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCustomInterpolator::CCustomInterpolator](../Topic/CCustomInterpolator::CCustomInterpolator.md)|Sobrecargado.  Construye un objeto de interpolador personalizado e inicializa la duración y el progreso para los valores especificados.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCustomInterpolator::GetDependencies](../Topic/CCustomInterpolator::GetDependencies.md)|Obtiene las dependencias del interpolador.|  
|[CCustomInterpolator::GetDuration](../Topic/CCustomInterpolator::GetDuration.md)|Obtiene la duración del interpolador.|  
|[CCustomInterpolator::GetFinalValue](../Topic/CCustomInterpolator::GetFinalValue.md)|Obtiene el valor final al que conduce el interpolador.|  
|[CCustomInterpolator::Init](../Topic/CCustomInterpolator::Init.md)|Inicializa el valor de duración y final.|  
|[CCustomInterpolator::InterpolateValue](../Topic/CCustomInterpolator::InterpolateValue.md)|Interpola el valor en un desplazamiento determinado.|  
|[CCustomInterpolator::InterpolateVelocity](../Topic/CCustomInterpolator::InterpolateVelocity.md)|Interpola el progreso en un desplazamiento determinado|  
|[CCustomInterpolator::SetDuration](../Topic/CCustomInterpolator::SetDuration.md)|Establece la duración del interpolador.|  
|[CCustomInterpolator::SetInitialValueAndVelocity](../Topic/CCustomInterpolator::SetInitialValueAndVelocity.md)|Establece el valor inicial y el progreso del interpolador.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCustomInterpolator::m\_currentValue](../Topic/CCustomInterpolator::m_currentValue.md)|El valor interpolado.|  
|[CCustomInterpolator::m\_currentVelocity](../Topic/CCustomInterpolator::m_currentVelocity.md)|El progreso interpolado.|  
|[CCustomInterpolator::m\_duration](../Topic/CCustomInterpolator::m_duration.md)|Duración de la transición.|  
|[CCustomInterpolator::m\_finalValue](../Topic/CCustomInterpolator::m_finalValue.md)|El valor final de una variable al final de la transición.|  
|[CCustomInterpolator::m\_initialValue](../Topic/CCustomInterpolator::m_initialValue.md)|El valor de la variable al principio de la transición .|  
|[CCustomInterpolator::m\_initialVelocity](../Topic/CCustomInterpolator::m_initialVelocity.md)|El progreso de la variable al principio de la transición .|  
  
## Comentarios  
 Derive una clase de CCustomInterpolator e invalide todos los métodos necesarios para implementar un algoritmo de interpolación personalizado.  Un puntero a esta clase se debería pasar como un parámetro a CCustomTransition.  
  
## Jerarquía de herencia  
 [CCustomInterpolator](../../mfc/reference/ccustominterpolator-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)