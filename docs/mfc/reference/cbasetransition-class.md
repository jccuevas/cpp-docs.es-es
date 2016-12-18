---
title: "CBaseTransition (Clase) | Microsoft Docs"
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
  - "CBaseTransition"
  - "afxanimationcontroller/CBaseTransition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBaseTransition (clase)"
ms.assetid: dfe84007-bbc5-43b7-b5b8-fae9145573bf
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBaseTransition (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una transición básica.  
  
## Sintaxis  
  
```  
class CBaseTransition : public CObject;  
```  
  
## Members  
  
### Enumeraciones públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBaseTransition::TRANSITION\_TYPE \(Enumeración\)](../Topic/CBaseTransition::TRANSITION_TYPE%20Enumeration.md)|Define los tipos de transición que admite actualmente la implementación MFC de la API de Windows Animation.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBaseTransition::CBaseTransition](../Topic/CBaseTransition::CBaseTransition.md)|Construye un objeto base de transición.|  
|[CBaseTransition::~CBaseTransition](../Topic/CBaseTransition::~CBaseTransition.md)|El destructor.  Se llama cuando se destruye un objeto de transición.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBaseTransition::AddToStoryboard](../Topic/CBaseTransition::AddToStoryboard.md)|Agrega una transición a un guión gráfico.|  
|[CBaseTransition::AddToStoryboardAtKeyframes](../Topic/CBaseTransition::AddToStoryboardAtKeyframes.md)|Agrega una transición a un guión gráfico.|  
|[CBaseTransition::Clear](../Topic/CBaseTransition::Clear.md)|Suelta el objeto COM encapsulado de IUIAnimationTransition.|  
|[CBaseTransition::Create](../Topic/CBaseTransition::Create.md)|Crea una transición COM.|  
|[CBaseTransition::GetEndKeyframe](../Topic/CBaseTransition::GetEndKeyframe.md)|Devuelve el inicio del fotograma clave.|  
|[CBaseTransition::GetRelatedVariable](../Topic/CBaseTransition::GetRelatedVariable.md)|Devuelve un puntero a la variable relacionada.|  
|[CBaseTransition::GetStartKeyframe](../Topic/CBaseTransition::GetStartKeyframe.md)|Devuelve el inicio del fotograma clave.|  
|[CBaseTransition::GetTransition](../Topic/CBaseTransition::GetTransition.md)|Sobrecargado.  Devuelve un puntero al objeto de transición COM subyacente.|  
|[CBaseTransition::GetType](../Topic/CBaseTransition::GetType.md)|Devuelve el tipo de transición.|  
|[CBaseTransition::IsAdded](../Topic/CBaseTransition::IsAdded.md)|Indica si una transición se ha agregado a un guión gráfico.|  
|[CBaseTransition::SetKeyframes](../Topic/CBaseTransition::SetKeyframes.md)|Establece los fotogramas clave para una transición.|  
|[CBaseTransition::SetRelatedVariable](../Topic/CBaseTransition::SetRelatedVariable.md)|Establece una relación entre la variable de animación y la transición.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBaseTransition::m\_bAdded](../Topic/CBaseTransition::m_bAdded.md)|Especifica si una transición se ha agregado a un guión gráfico.|  
|[CBaseTransition::m\_pEndKeyframe](../Topic/CBaseTransition::m_pEndKeyframe.md)|Almacena un puntero al fotograma clave que especifica el final de la transición.|  
|[CBaseTransition::m\_pRelatedVariable](../Topic/CBaseTransition::m_pRelatedVariable.md)|Un puntero a una variable de animación, que se anima con la transición almacenada en m\_transition.|  
|[CBaseTransition::m\_pStartKeyframe](../Topic/CBaseTransition::m_pStartKeyframe.md)|Almacena un puntero al fotograma clave que especifica el principio de la transición.|  
|[CBaseTransition::m\_transition](../Topic/CBaseTransition::m_transition.md)|Almacena un puntero a IUIAnimationTransition.  NULL si no se ha creado un objeto de transición COM.|  
|[CBaseTransition::m\_type](../Topic/CBaseTransition::m_type.md)|Almacena el tipo de transición.|  
  
## Comentarios  
 Esta clase encapsula la interfaz IUIAnimationTransition y sirve como una clase base para todas las transiciones.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)