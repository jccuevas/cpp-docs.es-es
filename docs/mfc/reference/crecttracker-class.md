---
title: "CRectTracker Class | Microsoft Docs"
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
  - "CRectTracker"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRectTracker class"
  - "displaying items"
  - "resizing items"
ms.assetid: 99caa7f2-3c0d-4a42-bbee-e5d1d342d4ee
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRectTracker Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Permite que se desplazan, y cambiar el tamaño de un elemento se muestra, en distintos modos.  
  
## Sintaxis  
  
```  
  
class CRectTracker  
  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRectTracker::CRectTracker](../Topic/CRectTracker::CRectTracker.md)|Crea un objeto `CRectTracker`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRectTracker::AdjustRect](../Topic/CRectTracker::AdjustRect.md)|Se invoca cuando se cambia el tamaño del rectángulo.|  
|[CRectTracker::Draw](../Topic/CRectTracker::Draw.md)|genera el rectángulo.|  
|[CRectTracker::DrawTrackerRect](../Topic/CRectTracker::DrawTrackerRect.md)|Denominado al dibujar el borde de un objeto de `CRectTracker` .|  
|[CRectTracker::GetHandleMask](../Topic/CRectTracker::GetHandleMask.md)|denominado para obtener la máscara de los controladores de cambio de tamaño de un elemento de `CRectTracker`.|  
|[CRectTracker::GetTrueRect](../Topic/CRectTracker::GetTrueRect.md)|Devuelve el ancho y el alto del rectángulo, incluidos los cuadros de tamaño.|  
|[CRectTracker::HitTest](../Topic/CRectTracker::HitTest.md)|Devuelve la posición actual del cursor relacionado con el objeto de `CRectTracker` .|  
|[CRectTracker::NormalizeHit](../Topic/CRectTracker::NormalizeHit.md)|normaliza un código de prueba de posicionamiento.|  
|[CRectTracker::OnChangedRect](../Topic/CRectTracker::OnChangedRect.md)|Se invoca cuando se cambia el tamaño o se ha movido el rectángulo.|  
|[CRectTracker::SetCursor](../Topic/CRectTracker::SetCursor.md)|Establece el cursor, dependiendo de su posición sobre el rectángulo.|  
|[CRectTracker::Track](../Topic/CRectTracker::Track.md)|Permite al usuario manipular el rectángulo.|  
|[CRectTracker::TrackRubberBand](../Topic/CRectTracker::TrackRubberBand.md)|Ofrece al usuario “caucho\-banda” la selección.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRectTracker::m\_nHandleSize](../Topic/CRectTracker::m_nHandleSize.md)|Determina el tamaño de controladores de tamaño.|  
|[CRectTracker::m\_nStyle](../Topic/CRectTracker::m_nStyle.md)|Estilos actuales del seguimiento.|  
|[CRectTracker::m\_rect](../Topic/CRectTracker::m_rect.md)|Posición actual \(en píxeles\) del rectángulo.|  
|[CRectTracker::m\_sizeMin](../Topic/CRectTracker::m_sizeMin.md)|Determina el ancho y el alto mínimos del rectángulo.|  
  
## Comentarios  
 `CRectTracker` no tiene una clase base.  
  
 Aunque la clase de `CRectTracker` está diseñado para permitir al usuario interactuar con los elementos de OLE mediante una interfaz gráfica, su uso no se limita a las aplicaciones OLE\-habilitadas.  Puede utilizar cualquier parte como interfaz de usuario es necesario.  
  
 los bordes de`CRectTracker` pueden ser sólidos o líneas de puntos.  El elemento se puede asignar un borde tramado o superponer con un modelo tramado para indicar diversos estados del elemento.  Puede colocar ocho controladores de tamaño fuera o el borde interior del elemento.  \(Para obtener una explicación de los controladores de tamaño, vea [GetHandleMask](../Topic/CRectTracker::GetHandleMask.md).\) Finalmente, `CRectTracker` permite cambiar la orientación de un elemento durante el tamaño.  
  
 Para utilizar `CRectTracker`, cree un objeto de `CRectTracker` y especifíquelo se inicializan que muestran estados.  Puede utilizar esta interfaz para proporcionar al usuario comentarios visuales sobre el estado actual del elemento OLE asociado con el objeto de `CRectTracker` .  
  
 Para obtener más información sobre cómo utilizar `CRectTracker`, vea el artículo [rastreadores](../../mfc/trackers.md).  
  
## Jerarquía de herencia  
 `CRectTracker`  
  
## Requisitos  
 **encabezado:** afxext.h  
  
## Vea también  
 [RASTREADOR de ejemplo de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo DRAWCLI de MFC](../../top/visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleResizeBar Class](../../mfc/reference/coleresizebar-class.md)   
 [CRect Class](../../atl-mfc-shared/reference/crect-class.md)   
 [CRectTracker::GetHandleMask](../Topic/CRectTracker::GetHandleMask.md)