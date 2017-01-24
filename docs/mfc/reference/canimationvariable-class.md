---
title: "CAnimationVariable (Clase) | Microsoft Docs"
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
  - "CAnimationVariable"
  - "afxanimationcontroller/CAnimationVariable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationVariable (clase)"
ms.assetid: 506e697e-31a8-4033-a27e-292f4d7b42d9
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAnimationVariable (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una variable de animación.  
  
## Sintaxis  
  
```  
class CAnimationVariable;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationVariable::CAnimationVariable](../Topic/CAnimationVariable::CAnimationVariable.md)|Construye un objeto variable de animación.|  
|[CAnimationVariable::~CAnimationVariable](../Topic/CAnimationVariable::~CAnimationVariable.md)|El destructor.  Se llama cuando se destruye un objeto CAnimationVariable.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationVariable::AddTransition](../Topic/CAnimationVariable::AddTransition.md)|Agrega una transición.|  
|[CAnimationVariable::ApplyTransitions](../Topic/CAnimationVariable::ApplyTransitions.md)|Agrega transiciones de la lista interna al guión gráfico.|  
|[CAnimationVariable::ClearTransitions](../Topic/CAnimationVariable::ClearTransitions.md)|Borra transiciones.|  
|[CAnimationVariable::Create](../Topic/CAnimationVariable::Create.md)|Crea el objeto COM de variable de animación subyacente.|  
|[CAnimationVariable::CreateTransitions](../Topic/CAnimationVariable::CreateTransitions.md)|Crea todas las transiciones que se van a aplicar a esta variable de animación.|  
|[CAnimationVariable::EnableIntegerValueChangedEvent](../Topic/CAnimationVariable::EnableIntegerValueChangedEvent.md)|Se utiliza para habilitar o deshabilitar el evento IntegerValueChanged.|  
|[CAnimationVariable::EnableValueChangedEvent](../Topic/CAnimationVariable::EnableValueChangedEvent.md)|Se utiliza para habilitar o deshabilitar el evento ValueChanged.|  
|[CAnimationVariable::GetDefaultValue](../Topic/CAnimationVariable::GetDefaultValue.md)|Devuelve el valor predeterminado.|  
|[CAnimationVariable::GetParentAnimationObject](../Topic/CAnimationVariable::GetParentAnimationObject.md)|Devuelve el objeto de animación primario.|  
|[CAnimationVariable::GetValue](../Topic/CAnimationVariable::GetValue.md)|Sobrecargado.  Devuelve el valor actual de la variable de animación.|  
|[CAnimationVariable::GetVariable](../Topic/CAnimationVariable::GetVariable.md)|Devuelve un puntero al objeto COM IUIAnimationVariable.|  
|[CAnimationVariable::SetDefaultValue](../Topic/CAnimationVariable::SetDefaultValue.md)|Establece el valor predeterminado y libera el objeto COM IUIAnimationVariable.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationVariable::SetParentAnimationObject](../Topic/CAnimationVariable::SetParentAnimationObject.md)|Establece la relación entre una variable de animación y un objeto de animación.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationVariable::m\_bAutodestroyTransitions](../Topic/CAnimationVariable::m_bAutodestroyTransitions.md)|Especifica si se deberían eliminar los objetos de transición relacionados.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationVariable::m\_dblDefaultValue](../Topic/CAnimationVariable::m_dblDefaultValue.md)|Especifica el valor predeterminado, que se propaga a IUIAnimationVariable.|  
|[CAnimationVariable::m\_lstTransitions](../Topic/CAnimationVariable::m_lstTransitions.md)|Contiene una lista de transiciones que animan esta variable de animación.|  
|[CAnimationVariable::m\_pParentObject](../Topic/CAnimationVariable::m_pParentObject.md)|Un puntero a un objeto de animación que encapsula esta variable de animación.|  
|[CAnimationVariable::m\_variable](../Topic/CAnimationVariable::m_variable.md)|Almacena un puntero al objeto COM IUIAnimationVariable.  NULL si todavía no se ha creado el objeto COM o si se produce un error en la creación.|  
  
## Comentarios  
 La clase CAnimationVariable encapsula el objeto COM IUIAnimationVariable.  También mantiene una lista de transiciones que se va a aplicar a la variable de animación en un guión gráfico.  Los objetos CAnimationVariable se incrustan en objetos de animación, que pueden representar en una aplicación un valor animado, punto, tamaño, color y rectángulo.  
  
## Jerarquía de herencia  
 [CAnimationVariable](../../mfc/reference/canimationvariable-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)