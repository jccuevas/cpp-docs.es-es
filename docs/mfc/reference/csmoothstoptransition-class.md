---
title: "CSmoothStopTransition (Clase) | Microsoft Docs"
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
  - "CSmoothStopTransition"
  - "afxanimationcontroller/CSmoothStopTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSmoothStopTransition (clase)"
ms.assetid: e1a4b476-6f96-43dd-90db-870a64406b85
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSmoothStopTransition (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula una transición de pausa suavizada.  
  
## Sintaxis  
  
```  
class CSmoothStopTransition : public CBaseTransition;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSmoothStopTransition::CSmoothStopTransition](../Topic/CSmoothStopTransition::CSmoothStopTransition.md)|Construye una transición de pausa sin problemas e inicializa su duración máxima y valor final.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSmoothStopTransition::Create](../Topic/CSmoothStopTransition::Create.md)|Llama a la biblioteca de transiciones para crear el objeto COM de transición encapsulado.  \(Invalida [CBaseTransition::Create](../Topic/CBaseTransition::Create.md).\)|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSmoothStopTransition::m\_dblFinalValue](../Topic/CSmoothStopTransition::m_dblFinalValue.md)|El valor final de una variable de animación al final de la transición.|  
|[CSmoothStopTransition::m\_maximumDuration](../Topic/CSmoothStopTransition::m_maximumDuration.md)|La duración máxima de la transición.|  
  
## Comentarios  
 Una transición de detención suave reduce la velocidad cuando se acerca a un determinado valor final y lo alcanza con un progreso de cero.  El progreso inicial, la diferencia entre los valores finales e inicial, determina la duración de la transición y la duración máxima especificada.  Si no hay ninguna solución que consista en un único arco parabólico, este método crea una transición cúbica.  Como todas las transiciones se desactivan automáticamente, se recomienda asignarlas mediante "operator new".  CAnimationController::AnimateGroup crea el objeto COM encapsulado IUIAnimationTransition que hasta entonces es NULL.  Cambiar las variables miembro después de que la creación de este objeto COM no tiene ningún efecto.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CSmoothStopTransition](../../mfc/reference/csmoothstoptransition-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)