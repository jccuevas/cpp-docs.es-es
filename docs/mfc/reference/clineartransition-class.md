---
title: "CLinearTransition (Clase) | Microsoft Docs"
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
  - "CLinearTransition"
  - "afxanimationcontroller/CLinearTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLinearTransition (clase)"
ms.assetid: 7fcb2dba-beb8-4933-9f5d-3b7fb1585ef0
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CLinearTransition (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula una transición lineal.  
  
## Sintaxis  
  
```  
class CLinearTransition : public CBaseTransition;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLinearTransition::CLinearTransition](../Topic/CLinearTransition::CLinearTransition.md)|Construye un objeto de transición lineal y lo inicializa con duración y valor final.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLinearTransition::Create](../Topic/CLinearTransition::Create.md)|Llama a la biblioteca de transiciones para crear el objeto COM de transición encapsulado.  \(Invalida [CBaseTransition::Create](../Topic/CBaseTransition::Create.md).\)|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLinearTransition::m\_dblFinalValue](../Topic/CLinearTransition::m_dblFinalValue.md)|El valor final de una variable de animación al final de la transición.|  
|[CLinearTransition::m\_duration](../Topic/CLinearTransition::m_duration.md)|Duración de la transición.|  
  
## Comentarios  
 Durante una transición lineal, el valor de la variable de animación realiza transiciones linealmente desde su valor inicial a un valor final especificado.  Como todas las transiciones se desactivan automáticamente, se recomienda asignarlas mediante "operator new".  CAnimationController::AnimateGroup crea el objeto COM encapsulado IUIAnimationTransition que hasta entonces es NULL.  Cambiar las variables miembro después de que la creación de este objeto COM no tiene ningún efecto.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CLinearTransition](../../mfc/reference/clineartransition-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)