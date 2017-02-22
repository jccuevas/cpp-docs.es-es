---
title: "CAnimationBaseObject (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CAnimationBaseObject"
  - "CAnimationBaseObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationBaseObject (clase)"
ms.assetid: 76b25917-940e-4eba-940f-31d270702603
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CAnimationBaseObject (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase base para todos los objetos de animación.  
  
## Sintaxis  
  
```  
class CAnimationBaseObject : public CObject;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationBaseObject::CAnimationBaseObject](../Topic/CAnimationBaseObject::CAnimationBaseObject.md)|Sobrecargado.  Construye un objeto de animación.|  
|[CAnimationBaseObject::~CAnimationBaseObject](../Topic/CAnimationBaseObject::~CAnimationBaseObject.md)|El destructor.  Se llama cuando se destruye un objeto de animación.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationBaseObject::ApplyTransitions](../Topic/CAnimationBaseObject::ApplyTransitions.md)|Agrega transiciones al guión gráfico con variable de animación encapsulada.|  
|[CAnimationBaseObject::ClearTransitions](../Topic/CAnimationBaseObject::ClearTransitions.md)|Quita todas las transiciones relacionadas.|  
|[CAnimationBaseObject::ContainsVariable](../Topic/CAnimationBaseObject::ContainsVariable.md)|Determina si un objeto de animación contiene una variable de animación determinada.|  
|[CAnimationBaseObject::CreateTransitions](../Topic/CAnimationBaseObject::CreateTransitions.md)|Crea transiciones asociadas a un objeto de animación.|  
|[CAnimationBaseObject::DetachFromController](../Topic/CAnimationBaseObject::DetachFromController.md)|Desasocia un objeto de animación del controlador de animación primario.|  
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](../Topic/CAnimationBaseObject::EnableIntegerValueChangedEvent.md)|Configura el controlador de eventos IntegerValueChanged.|  
|[CAnimationBaseObject::EnableValueChangedEvent](../Topic/CAnimationBaseObject::EnableValueChangedEvent.md)|Configura el controlador de evento ValueChanged.|  
|[CAnimationBaseObject::GetAutodestroyTransitions](../Topic/CAnimationBaseObject::GetAutodestroyTransitions.md)|Indica si se destruye automáticamente la transición relacionada.|  
|[CAnimationBaseObject::GetGroupID](../Topic/CAnimationBaseObject::GetGroupID.md)|Devuelve el Id. de grupo actual.|  
|[CAnimationBaseObject::GetObjectID](../Topic/CAnimationBaseObject::GetObjectID.md)|Devuelve el Id. de objeto actual.|  
|[CAnimationBaseObject::GetUserData](../Topic/CAnimationBaseObject::GetUserData.md)|Devuelve datos definido por el usuario.|  
|[CAnimationBaseObject::SetAutodestroyTransitions](../Topic/CAnimationBaseObject::SetAutodestroyTransitions.md)|Establece una marca que ordena destruir las transiciones automáticamente.|  
|[CAnimationBaseObject::SetID](../Topic/CAnimationBaseObject::SetID.md)|Establece nuevos identificadores.|  
|[CAnimationBaseObject::SetUserData](../Topic/CAnimationBaseObject::SetUserData.md)|Establece los datos definidos por el usuario.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationBaseObject::GetAnimationVariableList](../Topic/CAnimationBaseObject::GetAnimationVariableList.md)|Recopila punteros para variables de animación contenidas.|  
|[CAnimationBaseObject::SetParentAnimationObjects](../Topic/CAnimationBaseObject::SetParentAnimationObjects.md)|Establece la relación entre las variables de animación, contenidas en un objeto de animación, y su contenedor.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAnimationBaseObject::m\_bAutodestroyTransitions](../Topic/CAnimationBaseObject::m_bAutodestroyTransitions.md)|Especifica si se deberían destruir automáticamente las transiciones relacionadas.|  
|[CAnimationBaseObject::m\_dwUserData](../Topic/CAnimationBaseObject::m_dwUserData.md)|Almacena los datos definidos por el usuario.|  
|[CAnimationBaseObject::m\_nGroupID](../Topic/CAnimationBaseObject::m_nGroupID.md)|Especifica el Id. de grupo del objeto de animación.|  
|[CAnimationBaseObject::m\_nObjectID](../Topic/CAnimationBaseObject::m_nObjectID.md)|Especifica el Id. de objeto del objeto de animación.|  
|[CAnimationBaseObject::m\_pParentController](../Topic/CAnimationBaseObject::m_pParentController.md)|Puntero al controlador de animación primario.|  
  
## Comentarios  
 Esta clase implementa métodos básicos para todos los objetos de animación.  Un objeto de animación puede representar un valor, punto, tamaño, rectángulo o color en una aplicación, así como cualquier entidad personalizada.  Los objetos de animación se almacenan en grupos de animación \(vea CAnimationGroup\).  Cada grupo se puede animar separadamente y se puede tratar como un análogo de guión gráfico.  Un objeto de animación encapsula una o más variables de animación \(vea CAnimationVariable\), dependiendo de su representación lógica.  Por ejemplo, CAnimationRect contiene cuatro variables de animación: una variable para cada lado del rectángulo.  Cada clase de objeto de animación expone el método sobrecargado AddTransition, que se debería utilizar para aplicar transiciones a las variables de animación encapsuladas.  Un objeto de animación se puede identificar a través del Id. de objeto \(opcionalmente\) y a través del Id. de grupo.  Un Id. de grupo es necesario para colocar un objeto de animación y corregir el grupo, pero si no se especifica un Id. de grupo, se coloca un objeto en el grupo predeterminado con id. 0.  Si llama a SetID con GroupID diferente, se moverá un objeto de animación a otro grupo \(se crea un nuevo grupo, si es necesario\).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)