---
title: "CLinearTransitionFromSpeed (Clase) | Microsoft Docs"
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
  - "afxanimationcontroller/CLinearTransitionFromSpeed"
  - "CLinearTransitionFromSpeed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLinearTransitionFromSpeed (clase)"
ms.assetid: 8f159a1c-8893-4017-951e-09e5758aba7d
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CLinearTransitionFromSpeed (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula una transición de velocidad lineal.  
  
## Sintaxis  
  
```  
class CLinearTransitionFromSpeed : public CBaseTransition;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLinearTransitionFromSpeed::CLinearTransitionFromSpeed](../Topic/CLinearTransitionFromSpeed::CLinearTransitionFromSpeed.md)|Construye un objeto de transición de velocidad lineal y lo inicializa con velocidad y valor final.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLinearTransitionFromSpeed::Create](../Topic/CLinearTransitionFromSpeed::Create.md)|Llama a la biblioteca de transiciones para crear el objeto COM de transición encapsulado.  \(Invalida [CBaseTransition::Create](../Topic/CBaseTransition::Create.md).\)|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLinearTransitionFromSpeed::m\_dblFinalValue](../Topic/CLinearTransitionFromSpeed::m_dblFinalValue.md)|El valor final de una variable de animación al final de la transición.|  
|[CLinearTransitionFromSpeed::m\_dblSpeed](../Topic/CLinearTransitionFromSpeed::m_dblSpeed.md)|El valor absoluto del progreso de la variable.|  
  
## Comentarios  
 Durante una transición de velocidad lineal, el valor de la variable de animación cambia a una frecuencia especificada.  La diferencia entre el valor inicial y el valor final especificado determina la duración de la transición.  Como todas las transiciones se desactivan automáticamente, se recomienda asignarlas mediante "operator new".  CAnimationController::AnimateGroup crea el objeto COM encapsulado IUIAnimationTransition que hasta entonces es NULL.  Cambiar las variables miembro después de que la creación de este objeto COM no tiene ningún efecto.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CLinearTransitionFromSpeed](../../mfc/reference/clineartransitionfromspeed-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)