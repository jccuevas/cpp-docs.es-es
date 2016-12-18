---
title: "CCtrlView Class | Microsoft Docs"
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
  - "CCtrlView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCtrlView class"
  - "controles [MFC], common"
  - "vistas, and common controls"
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCtrlView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Adapta la arquitectura de la vista del documento a los controles comunes admitidos por las versiones 3,51 de Windows 98 y Windows NT y posterior.  
  
## Sintaxis  
  
```  
class CCtrlView : public CView  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCtrlView::CCtrlView](../Topic/CCtrlView::CCtrlView.md)|Crea un objeto `CCtrlView`.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCtrlView::OnDraw](../Topic/CCtrlView::OnDraw.md)|Llamado por el marco para dibujar utilizando el contexto especificado del dispositivo.|  
|[CCtrlView::PreCreateWindow](../Topic/CCtrlView::PreCreateWindow.md)|Se llama antes de la creación de la ventana de Windows asociada a este objeto de `CCtrlView` .|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCtrlView::m\_dwDefaultStyle](../Topic/CCtrlView::m_dwDefaultStyle.md)|Contiene el estilo predeterminado de la clase de vista.|  
|[CCtrlView::m\_strClass](../Topic/CCtrlView::m_strClass.md)|Contiene el nombre de clase de Windows para la clase de vista.|  
  
## Comentarios  
 La clase `CCtrlView` y sus derivados, [CEditView](../../mfc/reference/ceditview-class.md), [CListView](../../mfc/reference/clistview-class.md), [CTreeView](../../mfc/reference/ctreeview-class.md), y [CRichEditView](../../mfc/reference/cricheditview-class.md), admiten la arquitectura de la vista del documento a los nuevos controles comunes admitidos por las versiones de Windows 3,51 95 \/98 y Windows NT y posterior.  Para obtener más información sobre la arquitectura de la vista del documento, vea [Arquitectura documento\/vista](../../mfc/document-view-architecture.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 `CCtrlView`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [CView Class](../../mfc/reference/cview-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CTreeView Class](../../mfc/reference/ctreeview-class.md)   
 [CListView Class](../../mfc/reference/clistview-class.md)   
 [CRichEditView Class](../../mfc/reference/cricheditview-class.md)