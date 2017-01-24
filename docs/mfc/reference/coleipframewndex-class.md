---
title: "COleIPFrameWndEx Class | Microsoft Docs"
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
  - "COleIPFrameWndEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleIPFrameWndEx class"
ms.assetid: ebff1560-a1eb-4854-af00-95d4a192bd55
caps.latest.revision: 34
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleIPFrameWndEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase `COleIPFrameWndEx` implementa un contenedor OLE compatible con MFC. Es necesario derivar la clase de ventana de marco en contexto de la aplicación desde la clase `COleIPFrameWndEx` en lugar de derivarla desde la clase [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md).  
  
## Sintaxis  
  
```  
class COleIPFrameWndEx : public COleIPFrameWnd  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[COleIPFrameWndEx::AddDockSite](../Topic/COleIPFrameWndEx::AddDockSite.md)||  
|[COleIPFrameWndEx::AddPane](../Topic/COleIPFrameWndEx::AddPane.md)||  
|[COleIPFrameWndEx::AdjustDockingLayout](../Topic/COleIPFrameWndEx::AdjustDockingLayout.md)||  
|[COleIPFrameWndEx::DockPane](../Topic/COleIPFrameWndEx::DockPane.md)||  
|[COleIPFrameWndEx::DockPaneLeftOf](../Topic/COleIPFrameWndEx::DockPaneLeftOf.md)|Acopla un panel a la izquierda de otro panel.|  
|[COleIPFrameWndEx::EnableAutoHidePanes](../Topic/COleIPFrameWndEx::EnableAutoHidePanes.md)||  
|[COleIPFrameWndEx::EnableDocking](../Topic/COleIPFrameWndEx::EnableDocking.md)||  
|[COleIPFrameWndEx::EnablePaneMenu](../Topic/COleIPFrameWndEx::EnablePaneMenu.md)||  
|[COleIPFrameWndEx::GetActivePopup](../Topic/COleIPFrameWndEx::GetActivePopup.md)|Devuelve un puntero al menú emergente mostrado actualmente.|  
|[COleIPFrameWndEx::GetContainerFrameWindow](../Topic/COleIPFrameWndEx::GetContainerFrameWindow.md)||  
|[COleIPFrameWndEx::GetDefaultResId](../Topic/COleIPFrameWndEx::GetDefaultResId.md)|Devuelve el identificador de recurso de la ventana de marco se que especificó al cargar la ventana.|  
|[COleIPFrameWndEx::GetDockFrame](../Topic/COleIPFrameWndEx::GetDockFrame.md)||  
|[COleIPFrameWndEx::GetDockingManager](../Topic/COleIPFrameWndEx::GetDockingManager.md)||  
|[COleIPFrameWndEx::GetMainFrame](../Topic/COleIPFrameWndEx::GetMainFrame.md)||  
|[COleIPFrameWndEx::GetMenuBar](../Topic/COleIPFrameWndEx::GetMenuBar.md)|Devuelve un puntero al objeto de barra de menú asociado a la ventana de marco.|  
|[COleIPFrameWndEx::GetPane](../Topic/COleIPFrameWndEx::GetPane.md)||  
|[COleIPFrameWndEx::GetTearOffBars](../Topic/COleIPFrameWndEx::GetTearOffBars.md)|Devuelve una lista de objetos de panel que están en un estado desplazable.|  
|[COleIPFrameWndEx::GetToolbarButtonToolTipText](../Topic/COleIPFrameWndEx::GetToolbarButtonToolTipText.md)|Lo llama el marco de trabajo antes de que aparezca la información sobre herramientas para un botón.|  
|[COleIPFrameWndEx::InsertPane](../Topic/COleIPFrameWndEx::InsertPane.md)||  
|[COleIPFrameWndEx::IsMenuBarAvailable](../Topic/COleIPFrameWndEx::IsMenuBarAvailable.md)|Determina si el puntero al objeto de barra de menú no es `NULL`.|  
|[COleIPFrameWndEx::IsPointNearDockSite](../Topic/COleIPFrameWndEx::IsPointNearDockSite.md)||  
|[COleIPFrameWndEx::LoadFrame](../Topic/COleIPFrameWndEx::LoadFrame.md)|\(Invalida `COleIPFrameWnd::LoadFrame`\).|  
|[COleIPFrameWndEx::OnCloseDockingPane](../Topic/COleIPFrameWndEx::OnCloseDockingPane.md)||  
|[COleIPFrameWndEx::OnCloseMiniFrame](../Topic/COleIPFrameWndEx::OnCloseMiniFrame.md)||  
|[COleIPFrameWndEx::OnClosePopupMenu](../Topic/COleIPFrameWndEx::OnClosePopupMenu.md)|Lo llama el marco cuando un menú emergente activo procesa un mensaje WM\_DESTROY.|  
|[COleIPFrameWndEx::OnCmdMsg](../Topic/COleIPFrameWndEx::OnCmdMsg.md)|\(Invalida `CFrameWnd::OnCmdMsg`\).|  
|[COleIPFrameWndEx::OnDrawMenuImage](../Topic/COleIPFrameWndEx::OnDrawMenuImage.md)|Lo llama el marco de trabajo cuando se dibuja la imagen asociada a un elemento de menú.|  
|[COleIPFrameWndEx::OnDrawMenuLogo](../Topic/COleIPFrameWndEx::OnDrawMenuLogo.md)|Lo llama el marco de trabajo cuando un objeto [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) procesa un mensaje WM\_PAINT.|  
|[COleIPFrameWndEx::OnMenuButtonToolHitTest](../Topic/COleIPFrameWndEx::OnMenuButtonToolHitTest.md)|Lo llama el marco cuando un objeto [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) procesa un mensaje WM\_NCHITTEST.|  
|[COleIPFrameWndEx::OnMoveMiniFrame](../Topic/COleIPFrameWndEx::OnMoveMiniFrame.md)||  
|[COleIPFrameWndEx::OnSetPreviewMode](../Topic/COleIPFrameWndEx::OnSetPreviewMode.md)|Llame a esta función miembro para establecer la ventana de marco principal de la aplicación dentro y fuera del modo de vista previa de impresión. \(Invalida [CFrameWnd::OnSetPreviewMode](../Topic/CFrameWnd::OnSetPreviewMode.md)\).|  
|[COleIPFrameWndEx::OnShowCustomizePane](../Topic/COleIPFrameWndEx::OnShowCustomizePane.md)||  
|[COleIPFrameWndEx::OnShowPanes](../Topic/COleIPFrameWndEx::OnShowPanes.md)||  
|[COleIPFrameWndEx::OnShowPopupMenu](../Topic/COleIPFrameWndEx::OnShowPopupMenu.md)|Lo llama el marco de trabajo cuando se activa un menú emergente.|  
|[COleIPFrameWndEx::OnTearOffMenu](../Topic/COleIPFrameWndEx::OnTearOffMenu.md)|Lo llama el marco de trabajo cuando se activa un menú con barra desplazable.|  
|[COleIPFrameWndEx::PaneFromPoint](../Topic/COleIPFrameWndEx::PaneFromPoint.md)||  
|[COleIPFrameWndEx::PreTranslateMessage](../Topic/COleIPFrameWndEx::PreTranslateMessage.md)|\(Invalida `COleIPFrameWnd::PreTranslateMessage`\).|  
|[COleIPFrameWndEx::RecalcLayout](../Topic/COleIPFrameWndEx::RecalcLayout.md)|\(Invalida `COleIPFrameWnd::RecalcLayout`\).|  
|[COleIPFrameWndEx::RemovePaneFromDockManager](../Topic/COleIPFrameWndEx::RemovePaneFromDockManager.md)||  
|[COleIPFrameWndEx::SetDockState](../Topic/COleIPFrameWndEx::SetDockState.md)|Aplica el estado de acoplamiento especificado a los paneles que pertenecen a la ventana de marco.|  
|[COleIPFrameWndEx::SetupToolbarMenu](../Topic/COleIPFrameWndEx::SetupToolbarMenu.md)|Modifica un objeto de barra de herramientas al buscar elementos ficticios y reemplazarlos con los elementos definidos por el usuario especificados.|  
|[COleIPFrameWndEx::ShowPane](../Topic/COleIPFrameWndEx::ShowPane.md)||  
|[COleIPFrameWndEx::WinHelp](../Topic/COleIPFrameWndEx::WinHelp.md)|Lo llama el marco para iniciar la aplicación o la ayuda contextual de WinHelp.|  
  
### Métodos protegidos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[COleIPFrameWndEx::InitUserToobars](../Topic/COleIPFrameWndEx::InitUserToobars.md)|Indica al marco que inicialice un rango de identificadores de control que están asignados a las barras de herramientas definidas por el usuario.|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo crear subclases de una instancia de la clase `COleIPFrameWndEx` e invalidar sus métodos. En el ejemplo se muestra cómo invalidar el método `OnDestory`, el método `RepositionFrame`, el método `RecalcLayout` y el método `CalcWindowRect`. Este fragmento de código forma parte del [ejemplo de WordPad](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#1](../../mfc/reference/codesnippet/CPP/coleipframewndex-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md)  
  
 [COleIPFrameWndEx](../../mfc/reference/coleipframewndex-class.md)  
  
## Requisitos  
 **Encabezado:** afxoleipframewndex.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CFrameWndEx Class](../../mfc/reference/cframewndex-class.md)   
 [CMDIFrameWndEx \(Clase\)](../../mfc/reference/cmdiframewndex-class.md)