---
title: "CListView Class | Microsoft Docs"
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
  - "CListView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CListView class"
  - "vistas, and common controls"
ms.assetid: 7626bdb2-a1b8-4eab-b631-6743710a8432
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CListView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Simplifica el uso del control de lista y de [CListCtrl](../../mfc/reference/clistctrl-class.md), la clase que encapsula la funcionalidad del control de lista, con la arquitectura de la vista del documento de MFC.  
  
## Sintaxis  
  
```  
class CListView : public CCtrlView  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CListView::CListView](../Topic/CListView::CListView.md)|Crea un objeto `CListView`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CListView::GetListCtrl](../Topic/CListView::GetListCtrl.md)|Devuelve el control de lista asociado a la vista.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CListView::RemoveImageList](../Topic/CListView::RemoveImageList.md)|Quita la imagen especificada lista de vista de lista.|  
  
## Comentarios  
 Para obtener más información sobre esta arquitectura, vea información general de la clase de [CView](../../mfc/reference/cview-class.md) y referencias cruzadas delimitadas allí.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CListView`  
  
## Requisitos  
 **encabezado:** afxcview.h  
  
## Vea también  
 [ejemplo ROWLIST de MFC](../../top/visual-cpp-samples.md)   
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)