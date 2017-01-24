---
title: "CAnimationGroup (Clase) | Microsoft Docs"
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
  - "afxanimationcontroller/CAnimationGroup"
  - "CAnimationGroup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationGroup (clase)"
ms.assetid: 8bc18ceb-33a2-41d0-9731-71811adacab7
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAnimationGroup (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa un grupo de animación, que combina un guión gráfico, objetos y transiciones de animación para definir una animación.  
  
## Sintaxis  
  
```  
class CAnimationGroup;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationGroup::CAnimationGroup](../Topic/CAnimationGroup::CAnimationGroup.md)|Construye un grupo de animación.|  
|[CAnimationGroup::~CAnimationGroup](../Topic/CAnimationGroup::~CAnimationGroup.md)|El destructor.  Se llama cuando se destruye un grupo de animación.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationGroup::Animate](../Topic/CAnimationGroup::Animate.md)|Anima un grupo.|  
|[CAnimationGroup::ApplyTransitions](../Topic/CAnimationGroup::ApplyTransitions.md)|Aplica las transiciones a los objetos de animación.|  
|[CAnimationGroup::FindAnimationObject](../Topic/CAnimationGroup::FindAnimationObject.md)|Encuentra un objeto de animación que contiene la variable de animación especificada.|  
|[CAnimationGroup::GetGroupID](../Topic/CAnimationGroup::GetGroupID.md)|Devuelve GroupID.|  
|[CAnimationGroup::RemoveKeyframes](../Topic/CAnimationGroup::RemoveKeyframes.md)|Quita y, opcionalmente, destruye todos los fotogramas clave que pertenecen a un grupo de animación.|  
|[CAnimationGroup::RemoveTransitions](../Topic/CAnimationGroup::RemoveTransitions.md)|Quita las transiciones de los objetos de animación que pertenecen a un grupo de animación.|  
|[CAnimationGroup::Schedule](../Topic/CAnimationGroup::Schedule.md)|Programa una animación en el momento especificado.|  
|[CAnimationGroup::SetAutodestroyTransitions](../Topic/CAnimationGroup::SetAutodestroyTransitions.md)|Dirige todos los objetos de animación que pertenecen al grupo que automáticamente destruye las transiciones.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationGroup::AddKeyframes](../Topic/CAnimationGroup::AddKeyframes.md)|Una aplicación auxiliar que agrega los fotogramas clave a un guión gráfico.|  
|[CAnimationGroup::AddTransitions](../Topic/CAnimationGroup::AddTransitions.md)|Una aplicación auxiliar que agrega transiciones a un guión gráfico.|  
|[CAnimationGroup::CreateTransitions](../Topic/CAnimationGroup::CreateTransitions.md)|Una aplicación auxiliar que crea objetos COM de transición.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationGroup::m\_bAutoclearTransitions](../Topic/CAnimationGroup::m_bAutoclearTransitions.md)|Especifica cómo borrar las transiciones de los objetos de animación que pertenecen al grupo.  Si este miembro es TRUE, las transiciones se quitan de forma automática cuando se ha programado una animación.  De lo contrario, necesita quitar las transiciones de forma manual.|  
|[CAnimationGroup::m\_bAutodestroyAnimationObjects](../Topic/CAnimationGroup::m_bAutodestroyAnimationObjects.md)|Especifica cómo destruir los objetos de animación.  Si este parámetro es TRUE, se destruirán de forma automática los objetos de animación cuando se destruye el grupo.  De lo contrario, se deben destruir los objetos de animación de forma manual.  El valor predeterminado es FALSE.  Establezca este valor en TRUE únicamente si todos los objetos de animación que pertenecen al grupo se asignan de forma dinámica con "operator new".|  
|[CAnimationGroup::m\_bAutodestroyKeyframes](../Topic/CAnimationGroup::m_bAutodestroyKeyframes.md)|Especifica cómo destruir los fotogramas clave.  Si este valor es TRUE, todos los fotogramas clave se quitan y destruyen; de lo contrario únicamente se quitan de la lista.  El valor predeterminado es TRUE.|  
|[CAnimationGroup::m\_lstAnimationObjects](../Topic/CAnimationGroup::m_lstAnimationObjects.md)|Contiene una lista de objetos de animación.|  
|[CAnimationGroup::m\_lstKeyFrames](../Topic/CAnimationGroup::m_lstKeyFrames.md)|Contiene una lista de fotogramas clave.|  
|[CAnimationGroup::m\_pStoryboard](../Topic/CAnimationGroup::m_pStoryboard.md)|Señala al guión gráfico de animación.  Este puntero solo es válido después de la llamada a Animate.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationGroup::m\_nGroupID](../Topic/CAnimationGroup::m_nGroupID.md)|Un identificador único de grupo de animación.|  
|[CAnimationGroup::m\_pParentController](../Topic/CAnimationGroup::m_pParentController.md)|Puntero al controlador de animación al que pertenece este grupo.|  
  
## Comentarios  
 El controlador de animación \(CAnimationController\) crea automáticamente grupos de animación al agregar objetos de animación mediante CAnimationController::AddAnimationObject.  Un grupo de animación se identifica mediante GroupID, que normalmente se toma como un parámetro para manipular los grupos de animación.  Se toma GroupID del primer objeto de animación que se ha agregado a un nuevo grupo de animación.  Un guión gráfico de animación encapsulado se crea después de llamar a CAnimationController::AnimateGroup y se puede tener acceso mediante el miembro público m\_pStoryboard.  
  
## Jerarquía de herencia  
 [CAnimationGroup](../../mfc/reference/canimationgroup-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)