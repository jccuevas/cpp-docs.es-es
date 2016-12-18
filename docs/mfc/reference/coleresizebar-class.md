---
title: "COleResizeBar Class | Microsoft Docs"
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
  - "COleResizeBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleResizeBar class"
  - "control bars, cambiar el tamaño"
  - "in-place items"
  - "in-place items, cambiar el tamaño"
  - "OLE items, cambiar el tamaño"
  - "resizing in-place OLE items"
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleResizeBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un tipo de barra de control que admite el cambio de tamaño de elementos de OLE en contexto.  
  
## Sintaxis  
  
```  
class COleResizeBar : public CControlBar  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleResizeBar::COleResizeBar](../Topic/COleResizeBar::COleResizeBar.md)|Crea un objeto `COleResizeBar`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleResizeBar::Create](../Topic/COleResizeBar::Create.md)|Crea e inicializa una ventana secundaria de Windows y la asocia el objeto de `COleResizeBar` .|  
  
## Comentarios  
 Los objetos de`COleResizeBar` aparecen como [CRectTracker](../../mfc/reference/crecttracker-class.md) con un borde tramado y controladores de cambio de tamaño externos.  
  
 Los objetos de`COleResizeBar` suelen ser miembros insertados de los objetos de la cuadro\- ventana derivados de la clase de [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md) .  
  
 Para obtener más información, vea el artículo [activación](../../mfc/activation-cpp.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `COleResizeBar`  
  
## Requisitos  
 **encabezado:** afxole.h  
  
## Vea también  
 [ejemplo SUPERPAD de MFC](../../top/visual-cpp-samples.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleServerDoc Class](../../mfc/reference/coleserverdoc-class.md)