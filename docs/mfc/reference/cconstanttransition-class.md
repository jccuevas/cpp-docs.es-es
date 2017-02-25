---
title: "CConstantTransition (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CConstantTransition"
  - "CConstantTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CConstantTransition (clase)"
ms.assetid: f6fa4780-a71b-4cd6-80aa-d4792ace36c2
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CConstantTransition (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula una transición constante.  
  
## Sintaxis  
  
```  
class CConstantTransition : public CBaseTransition;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CConstantTransition::CConstantTransition](../Topic/CConstantTransition::CConstantTransition.md)|Construye un objeto de transición e inicializa su duración.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CConstantTransition::Create](../Topic/CConstantTransition::Create.md)|Llama a la biblioteca de transiciones para crear el objeto COM de transición encapsulado.  \(Invalida [CBaseTransition::Create](../Topic/CBaseTransition::Create.md).\)|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CConstantTransition::m\_duration](../Topic/CConstantTransition::m_duration.md)|Duración de la transición.|  
  
## Comentarios  
 Durante una transición constante, el valor de una variable de animación se mantiene en el valor inicial durante la duración de la transición.  Como todas las transiciones se desactivan automáticamente, se recomienda asignarlas mediante "operator new".  CAnimationController::AnimateGroup crea el objeto COM encapsulado IUIAnimationTransition que hasta entonces es NULL.  Cambiar las variables miembro después de que la creación de este objeto COM no tiene ningún efecto.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CConstantTransition](../../mfc/reference/cconstanttransition-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)