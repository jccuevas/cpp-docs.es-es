---
title: "CAccelerateDecelerateTransition Class | Microsoft Docs"
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
  - "CAccelerateDecelerateTransition"
  - "afxanimationcontroller/CAccelerateDecelerateTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAccelerateDecelerateTransition (clase)"
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
caps.latest.revision: 16
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAccelerateDecelerateTransition Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa una transición que aumenta\/reduce la velocidad.  
  
## Sintaxis  
  
```  
class CAccelerateDecelerateTransition : public CBaseTransition;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](../Topic/CAccelerateDecelerateTransition::CAccelerateDecelerateTransition.md)|Construye un objeto de transición.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::Create](../Topic/CAccelerateDecelerateTransition::Create.md)|Llama a la biblioteca de transiciones para crear el objeto COM de transición encapsulado.  \(Invalida [CBaseTransition::Create](../Topic/CBaseTransition::Create.md).\)|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::m\_accelerationRatio](../Topic/CAccelerateDecelerateTransition::m_accelerationRatio.md)|La proporción del tiempo empleado en acelerar la duración.|  
|[CAccelerateDecelerateTransition::m\_decelerationRatio](../Topic/CAccelerateDecelerateTransition::m_decelerationRatio.md)|La proporción del tiempo empleado en decelerar la duración.|  
|[CAccelerateDecelerateTransition::m\_duration](../Topic/CAccelerateDecelerateTransition::m_duration.md)|Duración de la transición.|  
|[CAccelerateDecelerateTransition::m\_finalValue](../Topic/CAccelerateDecelerateTransition::m_finalValue.md)|El valor final de una variable de animación al final de la transición.|  
  
## Comentarios  
 Durante una transición de aceleración y disminución de velocidad, la variable de animación aumenta y, a continuación, disminuye la velocidad mientras la duración de la transición, finalizando en un valor especificado.  Puede controlar la rapidez con la que la variable acelera y desacelera de forma independiente, especificando proporciones distintas de aceleración y desaceleración.  Cuando el progreso inicial es cero, la proporción de aceleración es la fracción de la duración que pasará la variable acelerando; de la misma manera con la proporción de desaceleración.  Si el progreso inicial es distinto de cero, es la fracción del tiempo entre el progreso que llega al cero y el fin de la transición.  La proporción de aceleración y la proporción de desaceleración deberían sumar un máximo de 1.0.  Como todas las transiciones se desactivan automáticamente, se recomienda asignarlas mediante "operator new".  CAnimationController::AnimateGroup crea el objeto COM encapsulado IUIAnimationTransition que hasta entonces es NULL.  Cambiar las variables miembro después de que la creación de este objeto COM no tiene ningún efecto.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CAccelerateDecelerateTransition](../../mfc/reference/cacceleratedeceleratetransition-class1.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)