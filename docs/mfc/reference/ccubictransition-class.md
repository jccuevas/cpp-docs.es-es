---
title: "CCubicTransition (Clase) | Microsoft Docs"
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
  - "CCubicTransition"
  - "afxanimationcontroller/CCubicTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCubicTransition (clase)"
ms.assetid: 4fc30e9c-160c-45e1-bdbe-51adf8fee9c5
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCubicTransition (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula una transición cúbica.  
  
## Sintaxis  
  
```  
class CCubicTransition : public CBaseTransition;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCubicTransition::CCubicTransition](../Topic/CCubicTransition::CCubicTransition.md)|Construye un objeto de transición e inicializa sus parámetros.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCubicTransition::Create](../Topic/CCubicTransition::Create.md)|Llama a la biblioteca de transiciones para crear el objeto COM de transición encapsulado.  \(Invalida [CBaseTransition::Create](../Topic/CBaseTransition::Create.md).\)|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCubicTransition::m\_dblFinalValue](../Topic/CCubicTransition::m_dblFinalValue.md)|El valor final de una variable de animación al final de la transición.|  
|[CCubicTransition::m\_dblFinalVelocity](../Topic/CCubicTransition::m_dblFinalVelocity.md)|El progreso de una variable al final de la transición.|  
|[CCubicTransition::m\_duration](../Topic/CCubicTransition::m_duration.md)|Duración de la transición.|  
  
## Comentarios  
 Durante una transición cúbica, el valor de la variable de animación cambia de su valor inicial a un valor final determinado durante la duración de la transición, finalizando en un progreso especificado.  Como todas las transiciones se desactivan automáticamente, se recomienda asignarlas mediante "operator new".  CAnimationController::AnimateGroup crea el objeto COM encapsulado IUIAnimationTransition que hasta entonces es NULL.  Cambiar las variables miembro después de que la creación de este objeto COM no tiene ningún efecto.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CCubicTransition](../../mfc/reference/ccubictransition-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)