---
title: "CReversalTransition (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CReversalTransition"
  - "CReversalTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CReversalTransition (clase)"
ms.assetid: e89516be-2d07-4885-95a8-fc278f46e3ad
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CReversalTransition (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula una transición de inversión.  
  
## Sintaxis  
  
```  
class CReversalTransition : public CBaseTransition;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CReversalTransition::CReversalTransition](../Topic/CReversalTransition::CReversalTransition.md)|Construye un objeto de transición de inversión e inicializa su duración.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CReversalTransition::Create](../Topic/CReversalTransition::Create.md)|Llama a la biblioteca de transiciones para crear el objeto COM de transición encapsulado.  \(Invalida [CBaseTransition::Create](../Topic/CBaseTransition::Create.md).\)|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CReversalTransition::m\_duration](../Topic/CReversalTransition::m_duration.md)|Duración de la transición.|  
  
## Comentarios  
 Una transición de inversión cambia sin problemas de dirección durante un período de tiempo determinado.  El valor final será igual que el valor inicial y el último progreso será el negativo del progreso inicial.  Como todas las transiciones se desactivan automáticamente, se recomienda asignarlas mediante "operator new".  CAnimationController::AnimateGroup crea el objeto COM encapsulado IUIAnimationTransition que hasta entonces es NULL.  Cambiar las variables miembro después de que la creación de este objeto COM no tiene ningún efecto.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CReversalTransition](../../mfc/reference/creversaltransition-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)