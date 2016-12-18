---
title: "CMDIFrameWndEx (Clase) | Microsoft Docs"
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
  - "CMDIFrameWndEx.AddDockSite"
  - "CMDIFrameWndEx"
  - "CMDIFrameWndEx::AddDockSite"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMDIFrameWndEx (clase)"
ms.assetid: dbcafcb3-9a7a-4f11-9dfe-ba57565c81d0
caps.latest.revision: 42
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMDIFrameWndEx (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Extiende la funcionalidad de [CMDIFrameWnd](../../mfc/reference/cframewnd-class.md), una ventana de cuadro de \(MDI\) de interfaz de múltiples documentos de Windows.  
  
## Sintaxis  
  
```  
class CMDIFrameWndEx : public CMDIFrameWnd  
```  
  
## Members  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMDIFrameWndEx::ActiveItemRecalcLayout](../Topic/CMDIFrameWndEx::ActiveItemRecalcLayout.md)|Actualiza el diseño del elemento activo.|  
|`CMDIFrameWndEx::AddDockSite`|Este método no se utiliza.|  
|[CMDIFrameWndEx::AddPane](../Topic/CMDIFrameWndEx::AddPane.md)|Registra un panel con el administrador de acoplamiento.|  
|[CMDIFrameWndEx::AdjustClientArea](../Topic/CMDIFrameWndEx::AdjustClientArea.md)|Reduce el área cliente para tener en cuenta un borde.|  
|[CMDIFrameWndEx::AdjustDockingLayout](../Topic/CMDIFrameWndEx::AdjustDockingLayout.md)|Actualiza el diseño de todos los paneles acoplados.|  
|[CMDIFrameWndEx::AreMDITabs](../Topic/CMDIFrameWndEx::AreMDITabs.md)|Determina si la característica de pestañas MDI o características de los grupos de MDI organización por fichas está habilitada.|  
|[CMDIFrameWndEx::CanCovertControlBarToMDIChild](../Topic/CMDIFrameWndEx::CanCovertControlBarToMDIChild.md)|Llamado por el marco para determinar si la ventana de marco puede convertir los paneles de acoplamiento a documentos con fichas.|  
|[CMDIFrameWndEx::ControlBarToTabbedDocument](../Topic/CMDIFrameWndEx::ControlBarToTabbedDocument.md)|Convierte el panel de acoplamiento especificado a un documento con fichas.|  
|[CMDIFrameWndEx::CreateDocumentWindow](../Topic/CMDIFrameWndEx::CreateDocumentWindow.md)|Crea una ventana de documento secundaria.|  
|[CMDIFrameWndEx::CreateNewWindow](../Topic/CMDIFrameWndEx::CreateNewWindow.md)|Llamado por el marco para crear una nueva ventana.|  
|`CMDIFrameWndEx::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMDIFrameWndEx::DockPane](../Topic/CMDIFrameWndEx::DockPane.md)|Acoplar el panel especificado a la ventana de marco.|  
|[CMDIFrameWndEx::DockPaneLeftOf](../Topic/CMDIFrameWndEx::DockPaneLeftOf.md)|Lo acopla un panel a la izquierda de otro panel.|  
|[CMDIFrameWndEx::EnableAutoHidePanes](../Topic/CMDIFrameWndEx::EnableAutoHidePanes.md)|Enables oculta automáticamente el modo para los paneles cuando se acoplan en los lados especificados de la ventana de marco principal.|  
|[CMDIFrameWndEx::EnableDocking](../Topic/CMDIFrameWndEx::EnableDocking.md)|Habilita el acoplamiento de los paneles que pertenecen a la ventana de marco MDI.|  
|[CMDIFrameWndEx::EnableFullScreenMainMenu](../Topic/CMDIFrameWndEx::EnableFullScreenMainMenu.md)|Muestra u oculta el menú principal en modo de pantalla completa.|  
|[CMDIFrameWndEx::EnableFullScreenMode](../Topic/CMDIFrameWndEx::EnableFullScreenMode.md)|Habilita el modo de pantalla completa para la ventana de marco.|  
|[CMDIFrameWndEx::EnableLoadDockState](../Topic/CMDIFrameWndEx::EnableLoadDockState.md)|Habilita o deshabilita la carga del estado de vinculación.|  
|[CMDIFrameWndEx::EnableMDITabbedGroups](../Topic/CMDIFrameWndEx::EnableMDITabbedGroups.md)|Habilita o deshabilita la característica de los grupos de MDI organización por fichas.|  
|[CMDIFrameWndEx::EnableMDITabs](../Topic/CMDIFrameWndEx::EnableMDITabs.md)|Habilita o deshabilita la característica de fichas de MDI.  Cuando está habilitada, la ventana cuadro muestra una ficha para cada ventana MDI secundaria.|  
|[CMDIFrameWndEx::EnableMDITabsLastActiveActivation](../Topic/CMDIFrameWndEx::EnableMDITabsLastActiveActivation.md)|Especifica si la pestaña activa última debe activarse cuando el usuario cierra la ficha actual.|  
|[CMDIFrameWndEx::EnablePaneMenu](../Topic/CMDIFrameWndEx::EnablePaneMenu.md)|Habilita o deshabilita la creación automática y administración del menú emergente del panel, que muestra una lista de paneles de la aplicación.  .|  
|[CMDIFrameWndEx::EnableWindowsDialog](../Topic/CMDIFrameWndEx::EnableWindowsDialog.md)|Inserta un elemento de menú cuyo identificador de comando llama a un cuadro de diálogo de [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md).|  
|[CMDIFrameWndEx::GetActivePopup](../Topic/CMDIFrameWndEx::GetActivePopup.md)|Devuelve un puntero al menú emergente mostrado actualmente.|  
|[CMDIFrameWndEx::GetPane](../Topic/CMDIFrameWndEx::GetPane.md)|Devuelve un puntero al panel que tiene el identificador especificado del control|  
|[CMDIFrameWndEx::GetDefaultResId](../Topic/CMDIFrameWndEx::GetDefaultResId.md)|Devuelve el identificador de recursos compartidos de la ventana de marco MDI.|  
|[CMDIFrameWndEx::GetMDITabGroups](../Topic/CMDIFrameWndEx::GetMDITabGroups.md)|Devuelve una lista de MDI con las ventanas.|  
|[CMDIFrameWndEx::GetMDITabs](../Topic/CMDIFrameWndEx::GetMDITabs.md)|Devuelve una referencia a la ventana con fichas subrayada.|  
|[CMDIFrameWndEx::GetMDITabsContextMenuAllowedItems](../Topic/CMDIFrameWndEx::GetMDITabsContextMenuAllowedItems.md)|Devuelve una combinación de marcadores que determina qué elementos de menú contextual son válidos cuando se habilita la característica de los grupos de MDI organización por fichas.|  
|[CMDIFrameWndEx::GetMenuBar](../Topic/CMDIFrameWndEx::GetMenuBar.md)|Devuelve un puntero a un objeto de la barra de menús asociado a la ventana de marco.|  
|[CMDIFrameWndEx::GetRibbonBar](../Topic/CMDIFrameWndEx::GetRibbonBar.md)|Recupera el control de barra de la cinta de opciones del cuadro.|  
|[CMDIFrameWndEx::GetTearOffBars](../Topic/CMDIFrameWndEx::GetTearOffBars.md)|Devuelve una lista de [CPane](../../mfc/reference/cpane-class.md)\- objetos derivados que están en estado de rasgón.|  
|`CMDIFrameWndEx::GetThisClass`|Llamado por el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|  
|[CMDIFrameWndEx::GetToolbarButtonToolTipText](../Topic/CMDIFrameWndEx::GetToolbarButtonToolTipText.md)|Llamado por el marco cuando la aplicación muestra información sobre herramientas de un botón de la barra de herramientas.|  
|[CMDIFrameWndEx::InsertPane](../Topic/CMDIFrameWndEx::InsertPane.md)|Registra el panel especificado con el administrador de acoplamiento.|  
|[CMDIFrameWndEx::IsFullScreen](../Topic/CMDIFrameWndEx::IsFullScreen.md)|Determina si la ventana de marco está en modo de pantalla completa.|  
|[CMDIFrameWndEx::IsMDITabbedGroup](../Topic/CMDIFrameWndEx::IsMDITabbedGroup.md)|Determina si la característica de los grupos de MDI organización por fichas está habilitada.|  
|[CMDIFrameWndEx::IsMemberOfMDITabGroup](../Topic/CMDIFrameWndEx::IsMemberOfMDITabGroup.md)|Determina si la ventana con fichas especificada está en la lista de ventanas que están en grupos de MDI organización por fichas.|  
|[CMDIFrameWndEx::IsMenuBarAvailable](../Topic/CMDIFrameWndEx::IsMenuBarAvailable.md)|Determina si la ventana cuadro tiene una barra de menús.|  
|[CMDIFrameWndEx::IsPointNearDockSite](../Topic/CMDIFrameWndEx::IsPointNearDockSite.md)|Determina si un punto especificado está cerca del sitio de vinculación.|  
|[CMDIFrameWndEx::IsPrintPreview](../Topic/CMDIFrameWndEx::IsPrintPreview.md)|Determina si la ventana de marco está en modo de vista previa de impresión.|  
|[CMDIFrameWndEx::LoadFrame](../Topic/CMDIFrameWndEx::LoadFrame.md)|Crea una ventana de marco de información de recursos.  \(Reemplaza `CMDIFrameWnd::LoadFrame`.\)|  
|[CMDIFrameWndEx::LoadMDIState](../Topic/CMDIFrameWndEx::LoadMDIState.md)|Carga el diseño especificado de grupos de MDI organización por fichas y la lista de documentos abiertos previamente.|  
|[CMDIFrameWndEx::MDITabMoveToNextGroup](../Topic/CMDIFrameWndEx::MDITabMoveToNextGroup.md)|Mueve la pestaña activa actual de la ventana con fichas activo el grupo con siguiente o anterior.|  
|[CMDIFrameWndEx::MDITabNewGroup](../Topic/CMDIFrameWndEx::MDITabNewGroup.md)|Crea un nuevo grupo con fichas que tiene una sola ventana.|  
|[CMDIFrameWndEx::NegotiateBorderSpace](../Topic/CMDIFrameWndEx::NegotiateBorderSpace.md)|Negocia el espacio del borde en una ventana de marco durante la activación en contexto OLE.|  
|[CMDIFrameWndEx::OnCloseDockingPane](../Topic/CMDIFrameWndEx::OnCloseDockingPane.md)|Llamado por el marco cuando el usuario hace clic en el botón **Cerrar** en un panel acoplable.|  
|[CMDIFrameWndEx::OnCloseMiniFrame](../Topic/CMDIFrameWndEx::OnCloseMiniFrame.md)|Llamado por el marco cuando el usuario hace clic en el botón **Cerrar** en una mini ventana flotante del cuadro.|  
|[CMDIFrameWndEx::OnClosePopupMenu](../Topic/CMDIFrameWndEx::OnClosePopupMenu.md)|Llamado por el marco cuando un menú emergente activo procesa un mensaje de `WM_DESTROY`.|  
|[CMDIFrameWndEx::OnCmdMsg](../Topic/CMDIFrameWndEx::OnCmdMsg.md)|Llamado por el marco para distribuir y enviar mensajes de comando y actualizar los objetos de la interfaz de usuario del comando.|  
|[CMDIFrameWndEx::OnDrawMenuImage](../Topic/CMDIFrameWndEx::OnDrawMenuImage.md)|Llamado por el marco cuando la imagen asociada a un elemento de menú se dibuja.|  
|[CMDIFrameWndEx::OnDrawMenuLogo](../Topic/CMDIFrameWndEx::OnDrawMenuLogo.md)|Llamado por el marco cuando [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) procesa un mensaje de `WM_PAINT`.|  
|[CMDIFrameWndEx::OnEraseMDIClientBackground](../Topic/CMDIFrameWndEx::OnEraseMDIClientBackground.md)|Llamado por el marco cuando la ventana de marco MDI procesa un mensaje de `WM_ERASEBKGND`.|  
|[CMDIFrameWndEx::OnMenuButtonToolHitTest](../Topic/CMDIFrameWndEx::OnMenuButtonToolHitTest.md)|Llamado por el marco cuando un objeto de [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) procesa un mensaje de `WM_NCHITTEST`.|  
|[CMDIFrameWndEx::OnMoveMiniFrame](../Topic/CMDIFrameWndEx::OnMoveMiniFrame.md)|Llamado por el marco para mover una ventana de mini\- cuadro.|  
|[CMDIFrameWndEx::OnSetPreviewMode](../Topic/CMDIFrameWndEx::OnSetPreviewMode.md)|Establece el modo de vista previa de impresión de la ventana de marco principal de la aplicación.  \(Reemplaza [CFrameWnd::OnSetPreviewMode](../Topic/CFrameWnd::OnSetPreviewMode.md).\)|  
|[CMDIFrameWndEx::OnShowCustomizePane](../Topic/CMDIFrameWndEx::OnShowCustomizePane.md)|Llamado por el marco cuando un Quick personaliza se produce el panel.|  
|[CMDIFrameWndEx::OnShowMDITabContextMenu](../Topic/CMDIFrameWndEx::OnShowMDITabContextMenu.md)|Llamado por el marco cuando un menú contextual se debería mostrar en una de las pestañas.  \(Válido para grupos de MDI organización por fichas sólo.\)|  
|[CMDIFrameWndEx::OnShowPanes](../Topic/CMDIFrameWndEx::OnShowPanes.md)|Llamado por el marco para mostrar u ocultar paneles.|  
|[CMDIFrameWndEx::OnShowPopupMenu](../Topic/CMDIFrameWndEx::OnShowPopupMenu.md)|Llamado por el marco cuando se activa un menú emergente.|  
|[CMDIFrameWndEx::OnSizeMDIClient](../Topic/CMDIFrameWndEx::OnSizeMDIClient.md)|Llamado por el marco cuando el tamaño de la ventana MDI de cliente está cambiando.|  
|[CMDIFrameWndEx::OnTearOffMenu](../Topic/CMDIFrameWndEx::OnTearOffMenu.md)|Llamado por el marco cuando se activa un menú que tiene una barra de rasgón.|  
|[CMDIFrameWndEx::OnUpdateFrameMenu](../Topic/CMDIFrameWndEx::OnUpdateFrameMenu.md)|Llamado por el marco para actualizar el menú del cuadro.  \(Reemplaza `CMDIFrameWnd::OnUpdateFrameMenu`.\)|  
|[CMDIFrameWndEx::PaneFromPoint](../Topic/CMDIFrameWndEx::PaneFromPoint.md)|Devuelve el panel acoplable que contiene el punto especificado.|  
|`CMDIFrameWndEx::PreTranslateMessage`|Utiliza la clase [CWinApp](../../mfc/reference/cwinapp-class.md) para traducir mensajes de ventana antes de que se envíen a las funciones de [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y de [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows.  \(Reemplaza `CMDIFrameWnd::PreTranslateMessage`.\)|  
|[CMDIFrameWndEx::RecalcLayout](../Topic/CMDIFrameWndEx::RecalcLayout.md)|Llamado por el marco para actualizar el diseño de la ventana de marco.  \(Reemplaza [CFrameWnd::RecalcLayout](../Topic/CFrameWnd::RecalcLayout.md).\)|  
|[CMDIFrameWndEx::RemovePaneFromDockManager](../Topic/CMDIFrameWndEx::RemovePaneFromDockManager.md)|Anula un panel y colóquelo de administrador de acoplamiento.|  
|[CMDIFrameWndEx::SaveMDIState](../Topic/CMDIFrameWndEx::SaveMDIState.md)|Guarda el diseño actual de grupos de MDI organización por fichas y la lista de documentos abiertos previamente.|  
|[CMDIFrameWndEx::SetPrintPreviewFrame](../Topic/CMDIFrameWndEx::SetPrintPreviewFrame.md)|Establece la ventana cuadro de vista previa de impresión.|  
|[CMDIFrameWndEx::SetupToolbarMenu](../Topic/CMDIFrameWndEx::SetupToolbarMenu.md)|Modifica un objeto de la barra de herramientas buscando los elementos ficticios y reemplazandolos con los elementos definidos por el usuario especificados.|  
|[CMDIFrameWndEx::ShowFullScreen](../Topic/CMDIFrameWndEx::ShowFullScreen.md)|Cambia el marco principal de modo normal al modo de pantalla completa.|  
|[CMDIFrameWndEx::ShowPane](../Topic/CMDIFrameWndEx::ShowPane.md)|Muestra u oculta el panel especificado.|  
|[CMDIFrameWndEx::ShowWindowsDialog](../Topic/CMDIFrameWndEx::ShowWindowsDialog.md)|Crea un cuadro de [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) y lo abre.|  
|[CMDIFrameWndEx::TabbedDocumentToControlBar](../Topic/CMDIFrameWndEx::TabbedDocumentToControlBar.md)|Convierte el documento con fichas especificado a un panel acoplable.|  
|[CMDIFrameWndEx::UpdateCaption](../Topic/CMDIFrameWndEx::UpdateCaption.md)|Llamado por el marco para actualizar la leyenda de la ventana.|  
|[CMDIFrameWndEx::UpdateMDITabbedBarsIcons](../Topic/CMDIFrameWndEx::UpdateMDITabbedBarsIcons.md)|Establece el icono para cada panel con MDI.|  
|[CMDIFrameWndEx::WinHelp](../Topic/CMDIFrameWndEx::WinHelp.md)|Llamado por el marco para iniciar la aplicación o la ayuda contextual de WinHelp.  \(Reemplaza [CWnd::WinHelp](../Topic/CWnd::WinHelp.md).\)|  
  
### Miembros de datos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMDIFrameWndEx::m\_bCanCovertControlBarToMDIChild](../Topic/CMDIFrameWndEx::m_bCanCovertControlBarToMDIChild.md)|Determina si acoplar paneles se puede convertir a las ventanas secundarias MDI.|  
|[CMDIFrameWndEx::m\_bDisableSetRedraw](../Topic/CMDIFrameWndEx::m_bDisableSetRedraw.md)|Habilita o deshabilita la optimización actualizar para las ventanas MDI secundarias.|  
  
## Comentarios  
 Para aprovechar características extendidas de personalización de la aplicación MDI, derive la clase de ventana de marco MDI de la aplicación de `CMDIFrameWndEx` en lugar de `CMDIFrameWnd`.  
  
## Ejemplo  
 El ejemplo siguiente crea una clase derivada de `CMDIFrameWndEx`.  Este fragmento de código procede de [Ejemplo de DrawClient: MFC Cinta de opciones\- en la aplicación de dibujo de objetos OLE](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#1](../../mfc/reference/codesnippet/CPP/cmdiframewndex-class_1.h)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)  
  
 [CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)  
  
## Requisitos  
 **Encabezado:** afxMDIFrameWndEx.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMDIFrameWnd](../../mfc/reference/cframewnd-class.md)   
 [Clase CMDIChildWndEx](../../mfc/reference/cmdichildwndex-class.md)