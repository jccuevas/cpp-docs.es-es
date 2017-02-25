---
title: "CTreeView Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CTreeView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTreeView class"
  - "CTreeView class, controles comunes"
  - "directory lists"
  - "file lists [C++]"
  - "tree view controls"
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CTreeView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Simplifica el uso del control de árbol y de [CTreeCtrl](../../mfc/reference/ctreectrl-class.md), la clase que encapsula la funcionalidad de control de árbol, con la arquitectura de la vista del documento de MFC.  
  
## Sintaxis  
  
```  
class CTreeView : public CCtrlView  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTreeView::CTreeView](../Topic/CTreeView::CTreeView.md)|Crea un objeto `CTreeView`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTreeView::GetTreeCtrl](../Topic/CTreeView::GetTreeCtrl.md)|Devuelve el control de árbol asociado a la vista.|  
  
## Comentarios  
 Para obtener más información sobre esta arquitectura, vea información general de la clase de [CView](../../mfc/reference/cview-class.md) y referencias cruzadas delimitadas allí.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CTreeView`  
  
## Requisitos  
 **encabezado:** afxcview.h  
  
## Vea también  
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)   
 [CTreeCtrl Class](../../mfc/reference/ctreectrl-class.md)