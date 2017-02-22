---
title: "CKeyFrame (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxanimationcontroller/CKeyFrame"
  - "CKeyFrame"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CKeyFrame (clase)"
ms.assetid: d050a562-20f6-4c65-8ce5-ccb3aef1a20e
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CKeyFrame (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa un fotograma clave de la animación.  
  
## Sintaxis  
  
```  
class CKeyFrame : public CBaseKeyFrame;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CKeyFrame::CKeyFrame](../Topic/CKeyFrame::CKeyFrame.md)|Sobrecargado.  Construye un fotograma clave que depende de otro fotograma clave.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CKeyFrame::AddToStoryboard](../Topic/CKeyFrame::AddToStoryboard.md)|Agrega un fotograma clave a un guión gráfico.  \(Invalida [CBaseKeyFrame::AddToStoryboard](../Topic/CBaseKeyFrame::AddToStoryboard.md).\)|  
|[CKeyFrame::AddToStoryboardAfterTransition](../Topic/CKeyFrame::AddToStoryboardAfterTransition.md)|Agrega un fotograma clave al guión gráfico después de la transición.|  
|[CKeyFrame::AddToStoryboardAtOffset](../Topic/CKeyFrame::AddToStoryboardAtOffset.md)|Agrega un fotograma clave al guión gráfico en el desplazamiento.|  
|[CKeyFrame::GetExistingKeyframe](../Topic/CKeyFrame::GetExistingKeyframe.md)|Devuelve un puntero a un fotograma clave del que depende este fotograma clave.|  
|[CKeyFrame::GetOffset](../Topic/CKeyFrame::GetOffset.md)|Devuelve un desplazamiento de otro fotograma clave.|  
|[CKeyFrame::GetTransition](../Topic/CKeyFrame::GetTransition.md)|Devuelve un puntero a una transición de la que depende este fotograma clave.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CKeyFrame::m\_offset](../Topic/CKeyFrame::m_offset.md)|Especifica el desplazamiento de este fotograma clave de un fotograma clave almacenado en m\_pExistingKeyFrame.|  
|[CKeyFrame::m\_pExistingKeyFrame](../Topic/CKeyFrame::m_pExistingKeyFrame.md)|Almacena un puntero a un fotograma clave existente.  Este fotograma clave se agrega al guión gráfico con m\_offset al fotograma clave existente.|  
|[CKeyFrame::m\_pTransition](../Topic/CKeyFrame::m_pTransition.md)|Almacena un puntero a la transición que comienza en este fotograma clave.|  
  
## Comentarios  
 Esta clase implementa un fotograma clave de animación.  Un fotograma clave representa un momento en el tiempo dentro de un guión gráfico y se puede utilizar para especificar la hora de inicio y final de las transiciones.  Un fotograma clave puede basarse en otro fotograma clave y tener un desplazamiento \(en segundos\) de él, o puede estar basado en una transición y representa un momento en la hora de finalización de esta transición.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)  
  
 [CKeyFrame](../../mfc/reference/ckeyframe-class.md)  
  
## Requisitos  
 **Encabezado:** afxanimationcontroller.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)