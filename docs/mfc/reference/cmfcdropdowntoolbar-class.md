---
title: "CMFCDropDownToolBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCDropDownToolBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDropDownToolBar class"
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
caps.latest.revision: 37
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 39
---
# CMFCDropDownToolBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una barra de herramientas que aparece cuando el usuario presiona y contiene un botón de la barra de herramientas de nivel superior.  
  
## Sintaxis  
  
```  
class CMFCDropDownToolBar : public CMFCToolBar  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](../Topic/CMFCDropDownToolBar::AllowShowOnPaneMenu.md)|\(Reemplaza `CPane::AllowShowOnPaneMenu`.\)|  
|[CMFCDropDownToolBar::LoadBitmap](../Topic/CMFCDropDownToolBar::LoadBitmap.md)|\(Reemplaza [CMFCToolBar::LoadBitmap](../Topic/CMFCToolBar::LoadBitmap.md).\)|  
|[CMFCDropDownToolBar::LoadToolBar](../Topic/CMFCDropDownToolBar::LoadToolBar.md)|\(Reemplaza [CMFCToolBar::LoadToolBar](../Topic/CMFCToolBar::LoadToolBar.md).\)|  
|[CMFCDropDownToolBar::OnLButtonUp](../Topic/CMFCDropDownToolBar::OnLButtonUp.md)||  
|[CMFCDropDownToolBar::OnMouseMove](../Topic/CMFCDropDownToolBar::OnMouseMove.md)||  
|[CMFCDropDownToolBar::OnSendCommand](../Topic/CMFCDropDownToolBar::OnSendCommand.md)|\(Reemplaza `CMFCToolBar::OnSendCommand`.\)|  
|[CMFCDropDownToolBar::OnUpdateCmdUI](../Topic/CMFCDropDownToolBar::OnUpdateCmdUI.md)|\(Reemplaza [CMFCToolBar::OnUpdateCmdUI](http://msdn.microsoft.com/es-es/571a38ab-2a56-4968-9796-273516126f80).\)|  
  
### Comentarios  
 un objeto de `CMFCDropDownToolBar` combina el aspecto visual de una barra de herramientas con el comportamiento de un menú emergente.  Cuando un usuario presiona y contiene un botón de la barra de herramientas desplegable \(vea [CMFCDropDownToolbarButton Class](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)\), una barra de herramientas desplegable aparece, y el usuario puede seleccionar un botón de la barra de herramientas desplegable adoptando el y lanzar el botón del mouse.  Después de que el usuario selecciona un botón en la barra de herramientas desplegable, ese botón se muestra como el botón actual en la barra de herramientas de nivel superior.  
  
 Una barra de herramientas desplegable no puede personalizar o acoplar, y no tiene un estado de rasgón.  
  
 La ilustración siguiente se muestra un objeto de `CMFCDropDownToolBar` :  
  
 ![Ejemplo de CMFCDropDownToolbar](../../mfc/reference/media/cmfcdropdown.png "CMFCDropDown")  
  
 Crea un objeto de `CMFCDropDownToolBar` de la misma manera que crea una barra de herramientas normal \(vea [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)\).  
  
 Para insertar la barra de herramientas desplegable en una barra de herramientas principal:  
  
 1.  Reserva un Id. de recurso ficticio para el botón del recurso primario de la barra de herramientas.  
  
 2.  Cree un objeto de `CMFCDropDownToolBarButton` que contiene la barra de herramientas desplegable \(para obtener más información, vea [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../Topic/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton.md)\).  
  
 3.  Reemplace el botón ficticio con el objeto de `CMFCDropDownToolBarButton` mediante [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md).  
  
 Para obtener más información sobre los botones de la barra de herramientas, vea [Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md).  Para obtener un ejemplo de una barra de herramientas desplegable, vea proyecto VisualStudioDemo de ejemplo.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo utilizar el método de `Create` en la clase de `CMFCDropDownToolBar` .  Este fragmento de código es parte de [Ejemplo de demostración de Visual Studio](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/CPP/cmfcdropdowntoolbar-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/CPP/cmfcdropdowntoolbar-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)  
  
## Requisitos  
 **encabezado:** afxdropdowntoolbar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBar::Create](../Topic/CMFCToolBar::Create.md)   
 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)   
 [CMFCDropDownToolbarButton Class](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)   
 [Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)