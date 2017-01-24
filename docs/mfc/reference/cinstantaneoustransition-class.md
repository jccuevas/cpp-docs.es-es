---
title: "CInstantaneousTransition (Clase) | Microsoft Docs"
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
  - "afxanimationcontroller/CInstantaneousTransition"
  - "CInstantaneousTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInstantaneousTransition (clase)"
ms.assetid: c3d5121f-2c6b-4221-9e57-10e082a31120
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CInstantaneousTransition (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula una transición instantánea.  
  
## Sintaxis  
  
```  
class CInstantaneousTransition : public CBaseTransition;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInstantaneousTransition::CInstantaneousTransition](../Topic/CInstantaneousTransition::CInstantaneousTransition.md)|Construye un objeto de transición e inicializa su valor final.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInstantaneousTransition::Create](../Topic/CInstantaneousTransition::Create.md)|Llama a la biblioteca de transiciones para crear el objeto COM de transición encapsulado.  \(Invalida [CBaseTransition::Create](../Topic/CBaseTransition::Create.md).\)|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CInstantaneousTransition::m\_dblFinalValue](../Topic/CInstantaneousTransition::m_dblFinalValue.md)|El valor final de una variable de animación al final de la transición.|  
  
## Comentarios  
 Durante una transición instantánea, el valor de la variable de animación cambia de forma instantánea de su valor actual a un valor final especificado.  La duración de esta transición siempre es cero.  Como todas las transiciones se desactivan automáticamente, se recomienda asignarlas mediante "operator new".  CAnimationController::AnimateGroup crea el objeto COM encapsulado IUIAnimationTransition que hasta entonces es NULL.  Cambiar las variables miembro después de que la creación de este objeto COM no tiene ningún efecto.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CInstantaneousTransition](../../mfc/reference/cinstantaneoustransition-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)