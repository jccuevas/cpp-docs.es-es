---
title: "CMFCDropDownFrame Class | Microsoft Docs"
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
  - "CMFCDropDownFrame"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDropDownFrame class"
ms.assetid: 09ff81a9-de00-43ec-9df9-b626f7728c4b
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCDropDownFrame Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona funcionalidad desplegable de la ventana de marco a las barras de herramientas desplegables y los botones de la barra de herramientas desplegables.  
  
## Sintaxis  
  
```  
class CMFCDropDownFrame : public CMiniFrameWnd  
```  
  
## Members  
  
### Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CMFCDropDownFrame::CMFCDropDownFrame`|Constructor predeterminado.|  
|`CMFCDropDownFrame::~CMFCDropDownFrame`|Un destructor.|  
  
### Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCDropDownFrame::Create](../Topic/CMFCDropDownFrame::Create.md)|Crea un objeto `CMFCDropDownFrame`.|  
|`CMFCDropDownFrame::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCDropDownFrame::GetParentMenuBar](../Topic/CMFCDropDownFrame::GetParentMenuBar.md)|Recupera la barra de menú primario del marco desplegable.|  
|[CMFCDropDownFrame::GetParentPopupMenu](../Topic/CMFCDropDownFrame::GetParentPopupMenu.md)|Recupera el elemento emergente primario del marco desplegable.|  
|`CMFCDropDownFrame::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CMFCDropDownFrame::RecalcLayout](../Topic/CMFCDropDownFrame::RecalcLayout.md)|Coloca el cuadro de nuevo desplegable.|  
|[CMFCDropDownFrame::SetAutoDestroy](../Topic/CMFCDropDownFrame::SetAutoDestroy.md)|establece si la ventana desplegable secundaria de la barra de herramientas está destruida automáticamente.|  
  
### Comentarios  
 Esta clase no está pensada para utilizarla directamente desde el código.  
  
 El marco de trabajo usa esta clase para proporcionar el comportamiento de cuadro a las clases de `CMFCDropDownToolbar` y de `CMFCDropDownToolbarButton` .  Para obtener más información sobre estas clases, vea [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md) y [CMFCDropDownToolbarButton Class](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md).  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo recuperar un puntero a un objeto de `CMFCDropDownFrame` de una clase de `CFrameWnd` , y cómo establecer la ventana desplegable secundaria de la barra de herramientas que se destruirá automáticamente.  
  
 [!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/CPP/cmfcdropdownframe-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)  
  
## Requisitos  
 **encabezado:** afxdropdowntoolbar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCDropDownToolBar Class](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [CMFCDropDownToolbarButton Class](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)