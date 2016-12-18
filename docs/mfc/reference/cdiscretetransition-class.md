---
title: "CDiscreteTransition (Clase) | Microsoft Docs"
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
  - "CDiscreteTransition"
  - "afxanimationcontroller/CDiscreteTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDiscreteTransition (clase)"
ms.assetid: b4d84fb3-ccaa-451c-a69b-6b50dcb9b9c8
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDiscreteTransition (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula una transición discreta.  
  
## Sintaxis  
  
```  
class CDiscreteTransition : public CBaseTransition;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDiscreteTransition::CDiscreteTransition](../Topic/CDiscreteTransition::CDiscreteTransition.md)|Construye un objeto de transición discreto e inicializa sus parámetros.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDiscreteTransition::Create](../Topic/CDiscreteTransition::Create.md)|Llama a la biblioteca de transiciones para crear el objeto COM de transición encapsulado.  \(Invalida [CBaseTransition::Create](../Topic/CBaseTransition::Create.md).\)|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDiscreteTransition::m\_dblFinalValue](../Topic/CDiscreteTransition::m_dblFinalValue.md)|El valor final de una variable de animación al final de la transición.|  
|[CDiscreteTransition::m\_delay](../Topic/CDiscreteTransition::m_delay.md)|La cantidad de tiempo por el que retrasar el modificador instantáneo al valor final.|  
|[CDiscreteTransition::m\_hold](../Topic/CDiscreteTransition::m_hold.md)|La cantidad de tiempo por el que retener la variable en su valor final.|  
  
## Comentarios  
 Durante una transición discreta, la variable de animación se mantiene en el valor inicial durante un tiempo de retraso especificado y, a continuación, cambia de forma instantánea a un valor final especificado y se mantiene en ese valor para un determinado tiempo de retención.  Como todas las transiciones se desactivan automáticamente, se recomienda asignarlas mediante "operator new".  CAnimationController::AnimateGroup crea el objeto COM encapsulado IUIAnimationTransition que hasta entonces es NULL.  Cambiar las variables miembro después de que la creación de este objeto COM no tiene ningún efecto.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CDiscreteTransition](../../mfc/reference/cdiscretetransition-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)