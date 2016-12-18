---
title: "CBaseKeyFrame (Clase) | Microsoft Docs"
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
  - "CBaseKeyFrame"
  - "afxanimationcontroller/CBaseKeyFrame"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBaseKeyFrame (clase)"
ms.assetid: 285a2eff-e7c4-43be-b5aa-737727e6866d
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBaseKeyFrame (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa la funcionalidad básica de un fotograma clave.  
  
## Sintaxis  
  
```  
class CBaseKeyFrame : public CObject;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBaseKeyFrame::CBaseKeyFrame](../Topic/CBaseKeyFrame::CBaseKeyFrame.md)|Construye un objeto fotograma clave.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBaseKeyFrame::AddToStoryboard](../Topic/CBaseKeyFrame::AddToStoryboard.md)|Agrega un fotograma clave a un guión gráfico.|  
|[CBaseKeyFrame::GetAnimationKeyframe](../Topic/CBaseKeyFrame::GetAnimationKeyframe.md)|Devuelve el valor del fotograma clave subyacente.|  
|[CBaseKeyFrame::IsAdded](../Topic/CBaseKeyFrame::IsAdded.md)|Indica si un fotograma clave se ha agregado al guión gráfico.|  
|[CBaseKeyFrame::IsKeyframeAtOffset](../Topic/CBaseKeyFrame::IsKeyframeAtOffset.md)|Especifica si el fotograma clave se debe agregar al guión gráfico en el desplazamiento, o después de la transición.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBaseKeyFrame::m\_bAdded](../Topic/CBaseKeyFrame::m_bAdded.md)|Especifica si este fotograma clave se ha agregado a un guión gráfico.|  
|[CBaseKeyFrame::m\_bIsKeyframeAtOffset](../Topic/CBaseKeyFrame::m_bIsKeyframeAtOffset.md)|Especifica si este fotograma clave se debería agregar al guión gráfico en un desplazamiento desde otro fotograma clave existente, o al final de alguna transición.|  
|[CBaseKeyFrame::m\_keyframe](../Topic/CBaseKeyFrame::m_keyframe.md)|Representa un fotograma clave de la API de Windows Animation.  Cuando no se ha inicializado un fotograma clave se establece en el valor UI\_ANIMATION\_KEYFRAME\_STORYBOARD\_START predefinido.|  
  
## Comentarios  
 Encapsula la variable UI\_ANIMATION\_KEYFRAME.  Actúa como una clase base para cualquier implementación del fotograma clave.  Un fotograma clave representa un momento en el tiempo dentro de un guión gráfico y se puede utilizar para especificar la hora de inicio y final de las transiciones.  Hay dos tipos de fotogramas clave: los fotogramas clave agregados al guión gráfico en el desplazamiento especificado \(en el tiempo\) o los fotogramas clave agregados después de la transición especificada.  Debido a que no se pueden conocer las duraciones de algunas transiciones antes del comienzo de la animación, se determinan los valores reales de algunos fotogramas clave solo en el runtime.  Dado que los fotogramas clave pueden depender de las transiciones, que, a su vez, dependen de los fotogramas clave, es importante evitar recursividades infinitas al compilar cadenas de fotograma clave.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)