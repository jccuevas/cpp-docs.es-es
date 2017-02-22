---
title: "CHtmlEditView Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CHtmlEditView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHtmlEditView class"
ms.assetid: 166c8ba8-3fb5-4dd7-a9ea-5bca662d00f6
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CHtmlEditView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad de la plataforma de edición WebBrowser en el contexto del documento de MFC o de la arquitectura de la vista.  
  
## Sintaxis  
  
```  
  
class CHtmlEditView : public CHtmlView, public CHtmlEditCtrlBase< CHtmlEditView >  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHtmlEditView::CHtmlEditView](../Topic/CHtmlEditView::CHtmlEditView.md)|Crea un objeto `CHtmlEditView`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHtmlEditView::Create](../Topic/CHtmlEditView::Create.md)|crea un objeto de la nueva ventana.|  
|[CHtmlEditView::GetDHtmlDocument](../Topic/CHtmlEditView::GetDHtmlDocument.md)|devuelve la interfaz de **IHTMLDocument2** en el documento actual.|  
|[CHtmlEditView::GetStartDocument](../Topic/CHtmlEditView::GetStartDocument.md)|Recupera el nombre del documento predeterminado para esta vista.|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CScrollView](../../mfc/reference/cscrollview-class.md)  
  
 [CFormView](../../mfc/reference/cformview-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CHtmlView](../../mfc/reference/chtmlview-class.md)  
  
 `CHtmlEditView`  
  
## Requisitos  
 **encabezado:** afxhtml.h  
  
## Vea también  
 [Ejemplo HTMLEdit](../../top/visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)