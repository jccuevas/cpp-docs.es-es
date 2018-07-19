---
title: CFrameWndEx (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFrameWndEx
- AFXFRAMEWNDEX/CFrameWndEx
- AFXFRAMEWNDEX/CFrameWndEx::ActiveItemRecalcLayout
- AFXFRAMEWNDEX/CFrameWndEx::AddPane
- AFXFRAMEWNDEX/CFrameWndEx::AdjustDockingLayout
- AFXFRAMEWNDEX/CFrameWndEx::DelayUpdateFrameMenu
- AFXFRAMEWNDEX/CFrameWndEx::DockPane
- AFXFRAMEWNDEX/CFrameWndEx::DockPaneLeftOf
- AFXFRAMEWNDEX/CFrameWndEx::EnableAutoHidePanes
- AFXFRAMEWNDEX/CFrameWndEx::EnableDocking
- AFXFRAMEWNDEX/CFrameWndEx::EnableFullScreenMainMenu
- AFXFRAMEWNDEX/CFrameWndEx::EnableFullScreenMode
- AFXFRAMEWNDEX/CFrameWndEx::EnableLoadDockState
- AFXFRAMEWNDEX/CFrameWndEx::EnablePaneMenu
- AFXFRAMEWNDEX/CFrameWndEx::GetActivePopup
- AFXFRAMEWNDEX/CFrameWndEx::GetDefaultResId
- AFXFRAMEWNDEX/CFrameWndEx::GetDockingManager
- AFXFRAMEWNDEX/CFrameWndEx::GetMenuBar
- AFXFRAMEWNDEX/CFrameWndEx::GetPane
- AFXFRAMEWNDEX/CFrameWndEx::GetRibbonBar
- AFXFRAMEWNDEX/CFrameWndEx::GetTearOffBars
- AFXFRAMEWNDEX/CFrameWndEx::GetToolbarButtonToolTipText
- AFXFRAMEWNDEX/CFrameWndEx::InsertPane
- AFXFRAMEWNDEX/CFrameWndEx::IsFullScreen
- AFXFRAMEWNDEX/CFrameWndEx::IsMenuBarAvailable
- AFXFRAMEWNDEX/CFrameWndEx::IsPointNearDockSite
- AFXFRAMEWNDEX/CFrameWndEx::IsPrintPreview
- AFXFRAMEWNDEX/CFrameWndEx::LoadFrame
- AFXFRAMEWNDEX/CFrameWndEx::NegotiateBorderSpace
- AFXFRAMEWNDEX/CFrameWndEx::OnActivate
- AFXFRAMEWNDEX/CFrameWndEx::OnActivateApp
- AFXFRAMEWNDEX/CFrameWndEx::OnChangeVisualManager
- AFXFRAMEWNDEX/CFrameWndEx::OnClose
- AFXFRAMEWNDEX/CFrameWndEx::OnCloseDockingPane
- AFXFRAMEWNDEX/CFrameWndEx::OnCloseMiniFrame
- AFXFRAMEWNDEX/CFrameWndEx::OnClosePopupMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnCmdMsg
- AFXFRAMEWNDEX/CFrameWndEx::OnContextHelp
- AFXFRAMEWNDEX/CFrameWndEx::OnCreate
- AFXFRAMEWNDEX/CFrameWndEx::OnDestroy
- AFXFRAMEWNDEX/CFrameWndEx::OnDrawMenuImage
- AFXFRAMEWNDEX/CFrameWndEx::OnDrawMenuLogo
- AFXFRAMEWNDEX/CFrameWndEx::OnDWMCompositionChanged
- AFXFRAMEWNDEX/CFrameWndEx::OnExitSizeMove
- AFXFRAMEWNDEX/CFrameWndEx::OnGetMinMaxInfo
- AFXFRAMEWNDEX/CFrameWndEx::OnIdleUpdateCmdUI
- AFXFRAMEWNDEX/CFrameWndEx::OnLButtonDown
- AFXFRAMEWNDEX/CFrameWndEx::OnLButtonUp
- AFXFRAMEWNDEX/CFrameWndEx::OnMenuButtonToolHitTest
- AFXFRAMEWNDEX/CFrameWndEx::OnMenuChar
- AFXFRAMEWNDEX/CFrameWndEx::OnMouseMove
- AFXFRAMEWNDEX/CFrameWndEx::OnMoveMiniFrame
- AFXFRAMEWNDEX/CFrameWndEx::OnNcActivate
- AFXFRAMEWNDEX/CFrameWndEx::OnNcCalcSize
- AFXFRAMEWNDEX/CFrameWndEx::OnNcHitTest
- AFXFRAMEWNDEX/CFrameWndEx::OnNcMouseMove
- AFXFRAMEWNDEX/CFrameWndEx::OnNcPaint
- AFXFRAMEWNDEX/CFrameWndEx::OnPaneCheck
- AFXFRAMEWNDEX/CFrameWndEx::OnPostPreviewFrame
- AFXFRAMEWNDEX/CFrameWndEx::OnPowerBroadcast
- AFXFRAMEWNDEX/CFrameWndEx::OnSetMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnSetPreviewMode
- AFXFRAMEWNDEX/CFrameWndEx::OnSetText
- AFXFRAMEWNDEX/CFrameWndEx::OnShowCustomizePane
- AFXFRAMEWNDEX/CFrameWndEx::OnShowPanes
- AFXFRAMEWNDEX/CFrameWndEx::OnShowPopupMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnSize
- AFXFRAMEWNDEX/CFrameWndEx::OnSizing
- AFXFRAMEWNDEX/CFrameWndEx::OnSysColorChange
- AFXFRAMEWNDEX/CFrameWndEx::OnTearOffMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnToolbarContextMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnToolbarCreateNew
- AFXFRAMEWNDEX/CFrameWndEx::OnToolbarDelete
- AFXFRAMEWNDEX/CFrameWndEx::OnUpdateFrameMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnUpdateFrameTitle
- AFXFRAMEWNDEX/CFrameWndEx::OnUpdatePaneMenu
- AFXFRAMEWNDEX/CFrameWndEx::OnWindowPosChanged
- AFXFRAMEWNDEX/CFrameWndEx::PaneFromPoint
- AFXFRAMEWNDEX/CFrameWndEx::PreTranslateMessage
- AFXFRAMEWNDEX/CFrameWndEx::RecalcLayout
- AFXFRAMEWNDEX/CFrameWndEx::RemovePaneFromDockManager
- AFXFRAMEWNDEX/CFrameWndEx::SetDockState
- AFXFRAMEWNDEX/CFrameWndEx::SetPrintPreviewFrame
- AFXFRAMEWNDEX/CFrameWndEx::SetupToolbarMenu
- AFXFRAMEWNDEX/CFrameWndEx::ShowFullScreen
- AFXFRAMEWNDEX/CFrameWndEx::ShowPane
- AFXFRAMEWNDEX/CFrameWndEx::UpdateCaption
- AFXFRAMEWNDEX/CFrameWndEx::WinHelp
dev_langs:
- C++
helpviewer_keywords:
- CFrameWndEx [MFC], ActiveItemRecalcLayout
- CFrameWndEx [MFC], AddPane
- CFrameWndEx [MFC], AdjustDockingLayout
- CFrameWndEx [MFC], DelayUpdateFrameMenu
- CFrameWndEx [MFC], DockPane
- CFrameWndEx [MFC], DockPaneLeftOf
- CFrameWndEx [MFC], EnableAutoHidePanes
- CFrameWndEx [MFC], EnableDocking
- CFrameWndEx [MFC], EnableFullScreenMainMenu
- CFrameWndEx [MFC], EnableFullScreenMode
- CFrameWndEx [MFC], EnableLoadDockState
- CFrameWndEx [MFC], EnablePaneMenu
- CFrameWndEx [MFC], GetActivePopup
- CFrameWndEx [MFC], GetDefaultResId
- CFrameWndEx [MFC], GetDockingManager
- CFrameWndEx [MFC], GetMenuBar
- CFrameWndEx [MFC], GetPane
- CFrameWndEx [MFC], GetRibbonBar
- CFrameWndEx [MFC], GetTearOffBars
- CFrameWndEx [MFC], GetToolbarButtonToolTipText
- CFrameWndEx [MFC], InsertPane
- CFrameWndEx [MFC], IsFullScreen
- CFrameWndEx [MFC], IsMenuBarAvailable
- CFrameWndEx [MFC], IsPointNearDockSite
- CFrameWndEx [MFC], IsPrintPreview
- CFrameWndEx [MFC], LoadFrame
- CFrameWndEx [MFC], NegotiateBorderSpace
- CFrameWndEx [MFC], OnActivate
- CFrameWndEx [MFC], OnActivateApp
- CFrameWndEx [MFC], OnChangeVisualManager
- CFrameWndEx [MFC], OnClose
- CFrameWndEx [MFC], OnCloseDockingPane
- CFrameWndEx [MFC], OnCloseMiniFrame
- CFrameWndEx [MFC], OnClosePopupMenu
- CFrameWndEx [MFC], OnCmdMsg
- CFrameWndEx [MFC], OnContextHelp
- CFrameWndEx [MFC], OnCreate
- CFrameWndEx [MFC], OnDestroy
- CFrameWndEx [MFC], OnDrawMenuImage
- CFrameWndEx [MFC], OnDrawMenuLogo
- CFrameWndEx [MFC], OnDWMCompositionChanged
- CFrameWndEx [MFC], OnExitSizeMove
- CFrameWndEx [MFC], OnGetMinMaxInfo
- CFrameWndEx [MFC], OnIdleUpdateCmdUI
- CFrameWndEx [MFC], OnLButtonDown
- CFrameWndEx [MFC], OnLButtonUp
- CFrameWndEx [MFC], OnMenuButtonToolHitTest
- CFrameWndEx [MFC], OnMenuChar
- CFrameWndEx [MFC], OnMouseMove
- CFrameWndEx [MFC], OnMoveMiniFrame
- CFrameWndEx [MFC], OnNcActivate
- CFrameWndEx [MFC], OnNcCalcSize
- CFrameWndEx [MFC], OnNcHitTest
- CFrameWndEx [MFC], OnNcMouseMove
- CFrameWndEx [MFC], OnNcPaint
- CFrameWndEx [MFC], OnPaneCheck
- CFrameWndEx [MFC], OnPostPreviewFrame
- CFrameWndEx [MFC], OnPowerBroadcast
- CFrameWndEx [MFC], OnSetMenu
- CFrameWndEx [MFC], OnSetPreviewMode
- CFrameWndEx [MFC], OnSetText
- CFrameWndEx [MFC], OnShowCustomizePane
- CFrameWndEx [MFC], OnShowPanes
- CFrameWndEx [MFC], OnShowPopupMenu
- CFrameWndEx [MFC], OnSize
- CFrameWndEx [MFC], OnSizing
- CFrameWndEx [MFC], OnSysColorChange
- CFrameWndEx [MFC], OnTearOffMenu
- CFrameWndEx [MFC], OnToolbarContextMenu
- CFrameWndEx [MFC], OnToolbarCreateNew
- CFrameWndEx [MFC], OnToolbarDelete
- CFrameWndEx [MFC], OnUpdateFrameMenu
- CFrameWndEx [MFC], OnUpdateFrameTitle
- CFrameWndEx [MFC], OnUpdatePaneMenu
- CFrameWndEx [MFC], OnWindowPosChanged
- CFrameWndEx [MFC], PaneFromPoint
- CFrameWndEx [MFC], PreTranslateMessage
- CFrameWndEx [MFC], RecalcLayout
- CFrameWndEx [MFC], RemovePaneFromDockManager
- CFrameWndEx [MFC], SetDockState
- CFrameWndEx [MFC], SetPrintPreviewFrame
- CFrameWndEx [MFC], SetupToolbarMenu
- CFrameWndEx [MFC], ShowFullScreen
- CFrameWndEx [MFC], ShowPane
- CFrameWndEx [MFC], UpdateCaption
- CFrameWndEx [MFC], WinHelp
ms.assetid: 5830aca8-4a21-4f31-91f1-dd5477ffcc8d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97548fca6b47e8d765eb7744a86ab0d4cfa27b17
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337493"
---
# <a name="cframewndex-class"></a>CFrameWndEx (clase)
Implementa la funcionalidad de una interfaz de un único documento (SDI) de Windows superpuesta o una ventana de marco emergente y proporciona miembros para administrar la ventana. Extiende la [CFrameWnd](../../mfc/reference/cframewnd-class.md) clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CFrameWndEx : public CFrameWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFrameWndEx::ActiveItemRecalcLayout](#activeitemrecalclayout)|Ajusta el diseño del elemento de cliente OLE y el área de cliente del marco.|  
|`CFrameWndEx::AddDockSite`|No se utiliza este método.|  
|[CFrameWndEx::AddPane](#addpane)|Registra una barra de control con el Administrador de acoplamiento.|  
|[CFrameWndEx::AdjustDockingLayout](#adjustdockinglayout)|Actualiza la disposición de todos los paneles se acoplan en la ventana de marco.|  
|[CFrameWndEx::DelayUpdateFrameMenu](#delayupdateframemenu)|Establece el menú de marco y, a continuación, actualiza al procesamiento de comandos está inactivo.|  
|[CFrameWndEx::DockPane](#dockpane)|Acopla el panel especificado en la ventana de marco.|  
|[CFrameWndEx::DockPaneLeftOf](#dockpaneleftof)|Acopla un panel a la izquierda de otro panel.|  
|[CFrameWndEx::EnableAutoHidePanes](#enableautohidepanes)|Habilita el modo de ocultación automática para los paneles al que se acoplan a los lados de la ventana de marco principal especificados.|  
|[Cframewndex:: EnableDocking](#enabledocking)|Permite el acoplamiento de los paneles que pertenecen a la ventana de marco.|  
|[CFrameWndEx::EnableFullScreenMainMenu](#enablefullscreenmainmenu)|Muestra u oculta el menú principal de un modo de pantalla completa.|  
|[CFrameWndEx::EnableFullScreenMode](#enablefullscreenmode)|Habilita el modo de pantalla completa para la ventana de marco.|  
|[CFrameWndEx::EnableLoadDockState](#enableloaddockstate)|Habilita o deshabilita la carga del estado de acoplamiento.|  
|[CFrameWndEx::EnablePaneMenu](#enablepanemenu)|Habilita o deshabilita el control automático del menú panel.|  
|[CFrameWndEx::GetActivePopup](#getactivepopup)|Devuelve un puntero al menú emergente mostrado actualmente.|  
|[CFrameWndEx::GetDefaultResId](#getdefaultresid)|Devuelve el identificador de recurso que especificó cuando el marco de trabajo carga la ventana de marco.|  
|[CFrameWndEx::GetDockingManager](#getdockingmanager)|Recupera el [CDockingManager Class](../../mfc/reference/cdockingmanager-class.md) objeto para la ventana de marco.|  
|[CFrameWndEx::GetMenuBar](#getmenubar)|Devuelve un puntero al objeto de barra de menú asociado a la ventana de marco.|  
|[CFrameWndEx::GetPane](#getpane)|Devuelve un puntero al panel que tiene el identificador especificado.|  
|[CFrameWndEx::GetRibbonBar](#getribbonbar)|Recupera el control de barra de cinta de opciones para el marco.|  
|[CFrameWndEx::GetTearOffBars](#gettearoffbars)|Devuelve una lista de objetos de panel que están en un estado desplazable.|  
|[CFrameWndEx::GetToolbarButtonToolTipText](#gettoolbarbuttontooltiptext)|Lo llama el marco de trabajo cuando la aplicación muestra la información sobre herramientas para un botón de barra de herramientas.|  
|[CFrameWndEx::InsertPane](#insertpane)|Registra un panel con el Administrador de acoplamiento.|  
|[CFrameWndEx::IsFullScreen](#isfullscreen)|Determina si la ventana de marco está en modo de pantalla completa.|  
|[CFrameWndEx::IsMenuBarAvailable](#ismenubaravailable)|Determina si el puntero al objeto de barra de menú es válido.|  
|[CFrameWndEx::IsPointNearDockSite](#ispointneardocksite)|Indica si el punto se encuentra en una zona de alineación.|  
|[CFrameWndEx::IsPrintPreview](#isprintpreview)|Indica si la ventana de marco está en modo de vista previa de impresión.|  
|[CFrameWndEx::LoadFrame](#loadframe)|Este método se llama después de la construcción para crear la ventana de marco y cargar sus recursos.|  
|[CFrameWndEx::NegotiateBorderSpace](#negotiateborderspace)|Negociación de borde de cliente de implementa OLE.|  
|[CFrameWndEx::OnActivate](#onactivate)|El marco llama a este método cuando se cambia la entrada del usuario a o fuera del marco.|  
|[CFrameWndEx::OnActivateApp](#onactivateapp)|Lo llama el marco de trabajo cuando se selecciona o anula la selección de la aplicación.|  
|[CFrameWndEx::OnChangeVisualManager](#onchangevisualmanager)|Lo llama el marco cuando un cambio en el marco requiere un cambio en el administrador visual.|  
|[CFrameWndEx::OnClose](#onclose)|El marco llama a este método para cerrar el marco.|  
|[CFrameWndEx::OnCloseDockingPane](#onclosedockingpane)|Lo llama el marco cuando el usuario hace clic en el **cerrar** botón en un panel acoplable.|  
|[CFrameWndEx::OnCloseMiniFrame](#oncloseminiframe)|Lo llama el marco cuando el usuario hace clic en el **cerrar** botón en una ventana de marco mini flotante.|  
|[CFrameWndEx::OnClosePopupMenu](#onclosepopupmenu)|Lo llama el marco cuando un menú emergente activo procesa un mensaje WM_DESTROY.|  
|[CFrameWndEx::OnCmdMsg](#oncmdmsg)|Este comando envía los mensajes.|  
|[CFrameWndEx::OnContextHelp](#oncontexthelp)|Lo llama el marco de trabajo mostrar el contexto de ayuda relacionada.|  
|[CFrameWndEx::OnCreate](#oncreate)|Lo llama el marco de trabajo una vez creado el marco.|  
|[CFrameWndEx::OnDestroy](#ondestroy)|Lo llama el marco de trabajo cuando se destruye el marco.|  
|[CFrameWndEx::OnDrawMenuImage](#ondrawmenuimage)|Lo llama el marco de trabajo cuando la aplicación dibuja la imagen asociada a un elemento de menú.|  
|[CFrameWndEx::OnDrawMenuLogo](#ondrawmenulogo)|Lo llama el marco cuando un `CMFCPopupMenu` objeto procesos un [WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) mensaje.|  
|[CFrameWndEx::OnDWMCompositionChanged](#ondwmcompositionchanged)|Lo llama el marco de trabajo cuando se habilita o deshabilita composición del Administrador de ventanas de escritorio (DWM).|  
|[CFrameWndEx::OnExitSizeMove](#onexitsizemove)|Lo llama el marco de trabajo cuando detiene el marco de movimiento o cambio de tamaño.|  
|[CFrameWndEx::OnGetMinMaxInfo](#ongetminmaxinfo)|Lo llama el marco de trabajo cuando se cambia el tamaño del marco para establecer los límites de la dimensión de ventana.|  
|[CFrameWndEx::OnIdleUpdateCmdUI](#onidleupdatecmdui)|Lo llama el marco de trabajo para actualizar la pantalla de marco cuando el procesamiento de comandos está inactivo.|  
|[CFrameWndEx::OnLButtonDown](#onlbuttondown)|El marco llama a este método cuando el usuario presiona el botón primario del mouse.|  
|[CFrameWndEx::OnLButtonUp](#onlbuttonup)|El marco llama a este método cuando el usuario suelta el botón primario del mouse.|  
|[CFrameWndEx::OnMenuButtonToolHitTest](#onmenubuttontoolhittest)|Lo llama el marco cuando un `CMFCToolBarButton` objeto procesa un mensaje WM_NCHITTEST.|  
|[CFrameWndEx::OnMenuChar](#onmenuchar)|Lo llama el marco de trabajo cuando se muestra un menú y el usuario presiona una tecla que no corresponde a un comando.|  
|[CFrameWndEx::OnMouseMove](#onmousemove)|El marco llama a este método cuando el puntero se mueve.|  
|[CFrameWndEx::OnMoveMiniFrame](#onmoveminiframe)|Lo llama el marco de trabajo cuando se mueve una ventana del panel.|  
|[CFrameWndEx::OnNcActivate](#onncactivate)|Lo llama el marco de trabajo cuando debe dibujarse el área no cliente del marco para indicar un cambio en el estado activo.|  
|[CFrameWndEx::OnNcCalcSize](#onnccalcsize)|Lo llama el marco de trabajo cuando se deben calcular el tamaño y posición del área de cliente.|  
|[CFrameWndEx::OnNcHitTest](#onnchittest)|Lo llama el marco cuando el puntero se mueve o al presionar o soltar un botón del mouse.|  
|[CFrameWndEx::OnNcMouseMove](#onncmousemove)|Lo llama el marco cuando el puntero se mueve en un área no cliente.|  
|[CFrameWndEx::OnNcPaint](#onncpaint)|Lo llama el marco de trabajo cuando se debe pintar el área no cliente.|  
|[CFrameWndEx::OnPaneCheck](#onpanecheck)|Lo llama el marco de trabajo para controlar la visibilidad de un panel.|  
|[CFrameWndEx::OnPostPreviewFrame](#onpostpreviewframe)|Lo llama el marco cuando el usuario ha cambiado el modo de vista previa de impresión.|  
|[CFrameWndEx::OnPowerBroadcast](#onpowerbroadcast)|Lo llama el marco de trabajo cuando se produce un evento de administración de energía.|  
|[CFrameWndEx::OnSetMenu](#onsetmenu)|Lo llama el marco de trabajo para reemplazar el menú de la ventana de marco.|  
|[CFrameWndEx::OnSetPreviewMode](#onsetpreviewmode)|Lo llama el marco de trabajo para establecer el modo de vista previa de impresión para el marco.|  
|[CFrameWndEx::OnSetText](#onsettext)|Lo llama el marco de trabajo para establecer el texto de una ventana.|  
|[CFrameWndEx::OnShowCustomizePane](#onshowcustomizepane)|Lo llama el marco cuando personalizan una rápida panel está habilitado.|  
|[CFrameWndEx::OnShowPanes](#onshowpanes)|Lo llama el marco de trabajo para mostrar u ocultar paneles.|  
|[CFrameWndEx::OnShowPopupMenu](#onshowpopupmenu)|Lo llama el marco de trabajo cuando se activa un menú emergente.|  
|[CFrameWndEx::OnSize](#onsize)|El marco llama a este método después de realizar cambios de tamaño del marco.|  
|[CFrameWndEx::OnSizing](#onsizing)|El marco llama a este método cuando el usuario cambia el tamaño del marco.|  
|[CFrameWndEx::OnSysColorChange](#onsyscolorchange)|Lo llama el marco cuando cambian los colores del sistema.|  
|[CFrameWndEx::OnTearOffMenu](#ontearoffmenu)|Lo llama el marco de trabajo cuando se activa un menú que tiene una barra desplazable.|  
|[CFrameWndEx::OnToolbarContextMenu](#ontoolbarcontextmenu)|Lo llama el marco para crear un menú contextual de barra de herramientas.|  
|[CFrameWndEx::OnToolbarCreateNew](#ontoolbarcreatenew)|El marco llama a este método para crear una nueva barra de herramientas.|  
|[CFrameWndEx::OnToolbarDelete](#ontoolbardelete)|Lo llama el marco de trabajo cuando se elimina una barra de herramientas.|  
|[CFrameWndEx::OnUpdateFrameMenu](#onupdateframemenu)|Lo llama el marco de trabajo para establecer el menú del marco.|  
|[CFrameWndEx::OnUpdateFrameTitle](#onupdateframetitle)|El marco llama a este método para actualizar la barra de título de la ventana de marco.|  
|[CFrameWndEx::OnUpdatePaneMenu](#onupdatepanemenu)|Lo llama el marco de trabajo para actualizar el menú del panel.|  
|[CFrameWndEx::OnWindowPosChanged](#onwindowposchanged)|Lo llama el marco cuando el tamaño del marco, la posición o el orden z ha cambiado debido a una llamada a un método de administración de la ventana.|  
|[CFrameWndEx::PaneFromPoint](#panefrompoint)|Devuelve el panel de acoplamiento que contiene el punto especificado.|  
|[CFrameWndEx::PreTranslateMessage](#pretranslatemessage)|Controla los mensajes de ventana específicos antes de enviarlos.|  
|[CFrameWndEx::RecalcLayout](#recalclayout)|Ajusta el diseño del marco y sus ventanas secundarias.|  
|[CFrameWndEx::RemovePaneFromDockManager](#removepanefromdockmanager)|Anula el registro de un panel y lo quita de la lista interna en el Administrador de acoplamiento.|  
|[CFrameWndEx::SetDockState](#setdockstate)|Restaura el diseño de acoplamiento en el estado de acoplamiento almacenado en el registro.|  
|[CFrameWndEx::SetPrintPreviewFrame](#setprintpreviewframe)|Establece la ventana de marco de vista previa de impresión.|  
|[CFrameWndEx::SetupToolbarMenu](#setuptoolbarmenu)|Comandos definidos por el usuario inserta en un menú de barra de herramientas.|  
|[CFrameWndEx::ShowFullScreen](#showfullscreen)|Cambia el marco principal entre los modos normales y de la pantalla completa.|  
|[CFrameWndEx::ShowPane](#showpane)|Muestra u oculta el panel especificado.|  
|[CFrameWndEx::UpdateCaption](#updatecaption)|Lo llama el marco de trabajo para actualizar el título del marco de ventana.|  
|[CFrameWndEx::WinHelp](#winhelp)|Ya sea invoca el `WinHelp` ayuda relacionados con la aplicación o contexto.|  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo se hereda de una clase desde el `CFrameWndEx` clase. El ejemplo ilustra las firmas de método en la subclase y cómo reemplazar el `OnShowPopupMenu` método. Este fragmento de código forma parte del [ejemplo de WordPad](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#3](../../mfc/reference/codesnippet/cpp/cframewndex-class_1.h)]  
[!code-cpp[NVC_MFC_WordPad#4](../../mfc/reference/codesnippet/cpp/cframewndex-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CFrameWndEx](../../mfc/reference/cframewndex-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxframewndex.h  
  
##  <a name="activeitemrecalclayout"></a>  CFrameWndEx::ActiveItemRecalcLayout  
 Ajusta el diseño del elemento de cliente OLE y el área de cliente del marco.  
  
```  
void ActiveItemRecalcLayout();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="addpane"></a>  CFrameWndEx::AddPane  
 Registra una barra de control con el Administrador de acoplamiento.  
  
```  
BOOL AddPane(
    CBasePane* pControlBar,  
    BOOL bTail=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pControlBar*  
 Un panel de barra de control para registrar.  
  
 [in] *bTail*  
 TRUE si desea agregar el panel de barra de control al final de la lista. FALSE en caso contrario.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la barra de control se registró correctamente; FALSE en caso contrario.  
  
##  <a name="adjustdockinglayout"></a>  CFrameWndEx::AdjustDockingLayout  
 Actualiza la disposición de todos los paneles se acoplan en la ventana de marco.  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *hdwp*  
 Identificador de una estructura que contiene las posiciones de varias ventanas. .  
  
### <a name="remarks"></a>Comentarios  
 Inicializa la estructura hdwp el [BeginDeferWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms632672) método.  
  
##  <a name="delayupdateframemenu"></a>  CFrameWndEx::DelayUpdateFrameMenu  
 Establece el menú de marco y, a continuación, actualiza al procesamiento de comandos está inactivo.  
  
```  
virtual void DelayUpdateFrameMenu(HMENU hMenuAlt);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *hMenuAlt*  
 Identificador de un menú alternativo.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="dockpane"></a>  CFrameWndEx::DockPane  
 Acopla el panel especificado en la ventana de marco.  
  
```  
void DockPane(
    CBasePane* pBar,  
    UINT nDockBarID=0,  
    LPCRECT lpRect=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pBar*  
 Un puntero a la barra de control quede acoplado.  
  
 [in] *nDockBarID*  
 El identificador del lado de la ventana de marco para acoplar a.  
  
 [in] *lpRect*  
 Un puntero a una estructura Rect constante que especifica la posición de la pantalla y el tamaño de la ventana.  
  
### <a name="remarks"></a>Comentarios  
 El *nDockBarID* parámetro puede tener uno de los valores siguientes:  
  
-   AFX_IDW_DOCKBAR_TOP  
  
-   AFX_IDW_DOCKBAR_BOTTOM  
  
-   AFX_IDW_DOCKBAR_LEFT  
  
-   AFX_IDW_DOCKBAR_RIGHT  
  
##  <a name="dockpaneleftof"></a>  CFrameWndEx::DockPaneLeftOf  
 Acopla el panel especificado a la izquierda de otro panel.  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBar,  
    CPane* pLeftOf);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pBar*  
 Un puntero al objeto de panel para acoplar.  
  
 [in] *pLeftOf*  
 Un puntero en el panel a la izquierda de la que se va a acoplar el panel especificado por *pBar*.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si *pBar* se acopla correctamente. FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 El método toma la barra de herramientas especificado por el *pBar* parámetro y lo acopla en el lado izquierdo de la barra de herramientas especificado por *pLeftOf* parámetro.  
  
##  <a name="enableautohidepanes"></a>  CFrameWndEx::EnableAutoHidePanes  
 Permite oculta automáticamente el modo del panel cuando se acopla en el lado especificado de la ventana de marco principal.  
  
```  
BOOL EnableAutoHidePanes(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *dwDockStyle*  
 Especifica el lado de la ventana de marco principal que se va a acoplar el panel.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si una barra de panel se acopla correctamente en el lado de la ventana de marco especificado por *dwDockStyle*, FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 *dwDockStyle* puede tener uno de los siguientes valores:  
  
-   CBRS_ALIGN_TOP: permite que la barra de control quede acoplado a la parte superior del área de cliente de una ventana de marco.  
  
-   CBRS_ALIGN_BOTTOM: permite que la barra de control quede acoplado a la parte inferior del área de cliente de una ventana de marco.  
  
-   CBRS_ALIGN_LEFT: permite que la barra de control se acopla al lado izquierdo del área cliente de una ventana de marco.  
  
-   CBRS_ALIGN_RIGHT: permite que la barra de control se acopla a la derecha del área de cliente de una ventana de marco.  
  
##  <a name="enabledocking"></a>  Cframewndex:: EnableDocking  
 Permite el acoplamiento de los paneles de la ventana de marco.  
  
```  
BOOL EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *dwDockStyle*  
 Especifica el lado de la ventana de marco principal donde se acopla la barra del panel.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si una barra de panel se puede acoplar correctamente en el lado especificado. FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 El *dwDockStyle* parámetro puede tener uno de los valores siguientes:  
  
-   CBRS_ALIGN_TOP  
  
-   CBRS_ALIGN_BOTTOM  
  
-   CBRS_ALIGN_LEFT  
  
-   CBRS_ALIGN_RIGHT  
  
##  <a name="enablefullscreenmainmenu"></a>  CFrameWndEx::EnableFullScreenMainMenu  
 Muestra u oculta el menú principal de un modo de pantalla completa.  
  
```  
void EnableFullScreenMainMenu(BOOL bEnableMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bEnableMenu*  
 True para mostrar el menú principal de una completa de la pantalla modo, FALSE en caso contrario.  
  
##  <a name="enablefullscreenmode"></a>  CFrameWndEx::EnableFullScreenMode  
 Habilita el modo de pantalla completa para la ventana de marco.  
  
```  
void EnableFullScreenMode(UINT uiFullScreenCmd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *uiFullScreenCmd*  
 El identificador de comando que habilita y deshabilita el modo de pantalla completa.  
  
### <a name="remarks"></a>Comentarios  
 En el modo de pantalla completa, todas las barras de control de acoplamiento, barras de herramientas y menús están ocultos y se cambia el tamaño de la vista activa para ocupar la pantalla completa.  
  
 Cuando se habilita el modo de pantalla completa, debe especificar un identificador del comando que habilita o deshabilita el modo de pantalla completa. Puede llamar a `EnableFullScreenMode` desde el marco principal `OnCreate` función. Cuando una ventana de marco que se cambia a un modo de pantalla completa, el marco de trabajo crea una barra de herramientas flotante con un botón que tiene el identificador de comando especificado.  
  
 Si desea mantener el menú principal en la pantalla, llame a [CFrameWndEx::EnableFullScreenMainMenu](#enablefullscreenmainmenu).  
  
##  <a name="enableloaddockstate"></a>  CFrameWndEx::EnableLoadDockState  
 Habilita o deshabilita la carga del estado de acoplamiento.  
  
```  
void EnableLoadDockState(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bHabilitar el*  
 TRUE para habilitar la carga de estado de acoplamiento, FALSE para deshabilitar la carga del estado de acoplamiento.  
  
##  <a name="enablepanemenu"></a>  CFrameWndEx::EnablePaneMenu  
 Habilita o deshabilita el control automático del menú panel.  
  
```  
void EnablePaneMenu(
    BOOL bEnable,  
    UINT uiCustomizeCmd,  
    const CString& strCustomizeLabel,  
    UINT uiViewToolbarsMenuEntryID,  
    BOOL bContextMenuShowsToolbarsOnly=FALSE,  
    BOOL bViewMenuShowsToolbarsOnly=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bHabilitar el*  
 TRUE para habilitar el control automático del control de barra de menús emergentes; FALSE para deshabilitar el control automático del control de barra de menús emergentes.  
  
 [in] *uiCustomizeCmd*  
 El identificador del comando el **personalizar** elemento de menú.  
  
 [in] *strCustomizeLabel*  
 La etiqueta que se mostrará para el **personalizar** elemento de menú  
  
 [in] *uiViewToolbarsMenuEntryID*  
 El identificador de un elemento de menú de barra de herramientas que se abre el menú emergente en la barra de control.  
  
 [in] *bContextMenuShowsToolbarsOnly*  
 Si es TRUE, el menú contextual de barra de control muestra la lista de sólo las barras de herramientas. Si es FALSE, el menú muestra la lista de las barras de herramientas y las barras de acoplamiento.  
  
 [in] *bViewMenuShowsToolbarsOnly*  
 Si es TRUE, el menú de la barra de control muestra la lista de sólo las barras de herramientas. Si es FALSE, el menú muestra la lista de las barras de herramientas y las barras de acoplamiento.  
  
##  <a name="getactivepopup"></a>  CFrameWndEx::GetActivePopup  
 Devuelve un puntero al menú emergente mostrado actualmente.  
  
```  
CMFCPopupMenu* GetActivePopup() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al menú emergente mostrado actualmente; en caso contrario, es NULL.  
  
##  <a name="getdefaultresid"></a>  CFrameWndEx::GetDefaultResId  
 Devuelve el identificador de recurso que especificó cuando el marco de trabajo carga la ventana de marco.  
  
```  
UINT GetDefaultResId() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de identificador de recurso que el usuario especificado cuando el marco de trabajo carga la ventana de marco. Cero si la ventana de marco no tiene una barra de menús.  
  
##  <a name="getdockingmanager"></a>  CFrameWndEx::GetDockingManager  
 Recupera el [CDockingManager Class](../../mfc/reference/cdockingmanager-class.md) objeto para la ventana de marco.  
  
```  
CDockingManager* GetDockingManager();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la [CDockingManager Class](../../mfc/reference/cdockingmanager-class.md).  
  
### <a name="remarks"></a>Comentarios  
 La ventana de marco crea y utiliza un [CDockingManager Class](../../mfc/reference/cdockingmanager-class.md) objeto para administrar la ventana de acoplamiento de secundarios.  
  
##  <a name="getmenubar"></a>  CFrameWndEx::GetMenuBar  
 Devuelve un puntero al objeto de barra de menú asociado a la ventana de marco.  
  
```  
const CMFCMenuBar* GetMenuBar() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto de barra de menú asociado a la ventana de marco.  
  
##  <a name="getpane"></a>  CFrameWndEx::GetPane  
 Devuelve un puntero al panel que tiene el identificador especificado.  
  
```  
CBasePane* GetPane(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nID*  
 El identificador de control.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al panel que tiene el identificador especificado. NULL si no existe ningún panel de este tipo.  
  
##  <a name="getribbonbar"></a>  CFrameWndEx::GetRibbonBar  
 Recupera el control de barra de cinta de opciones para el marco.  
  
```  
CMFCRibbonBar* GetRibbonBar();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la [CMFCRibbonBar (clase)](../../mfc/reference/cmfcribbonbar-class.md) para el marco.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gettearoffbars"></a>  CFrameWndEx::GetTearOffBars  
 Devuelve una lista de objetos de panel que están en un estado desplazable.  
  
```  
const CObList& GetTearOffBars() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a `CObList` objeto que contiene una colección de punteros a los objetos de panel que se encuentran en un estado desplazable.  
  
##  <a name="gettoolbarbuttontooltiptext"></a>  CFrameWndEx::GetToolbarButtonToolTipText  
 Lo llama el marco de trabajo cuando la aplicación muestra la información sobre herramientas para un botón de barra de herramientas.  
  
```  
virtual BOOL GetToolbarButtonToolTipText(
    CMFCToolBarButton* pButton,  
    CString& strTTText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pButton*  
 Un puntero a un botón de barra de herramientas.  
  
 [in] *strTTText*  
 El texto de información sobre herramientas que se muestra en el botón.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se ha mostrado la información sobre herramientas. FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método no hace nada. Invalide este método si desea mostrar la información sobre herramientas para el botón de barra de herramientas.  
  
##  <a name="insertpane"></a>  CFrameWndEx::InsertPane  
 Inserta un panel en una lista de barras de control y lo registra con el administrador de acoplamiento.  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *pControlBar*  
 Puntero a una barra de controles que se va a insertar en la lista de barras de control y a registrar con el administrador de acoplamiento.  
  
 *pTarget*  
 Puntero a una barra de control antes o después de la que se va a insertar el panel.  
  
 *Después*  
 TRUE si desea insertar *pControlBar* después *pTarget*, FALSE en caso contrario.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la barra de control se ha insertado correctamente y se registrado, FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Se debe registrar cada barra de control mediante la [CDockingManager Class](../../mfc/reference/cdockingmanager-class.md) para formar parte del diseño de acoplamiento.  
  
##  <a name="isfullscreen"></a>  CFrameWndEx::IsFullScreen  
 Determina si la ventana de marco está en modo de pantalla completa.  
  
```  
BOOL IsFullScreen() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la ventana de marco está en modo de pantalla completa; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Puede establecer el modo de pantalla completa mediante una llamada a la [CFrameWndEx::EnableFullScreenMode](#enablefullscreenmode) método.  
  
##  <a name="ismenubaravailable"></a>  CFrameWndEx::IsMenuBarAvailable  
 Determina si el puntero al objeto de barra de menú es válido.  
  
```  
BOOL IsMenuBarAvailable() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la ventana de marco tiene una barra de menús; en caso contrario, FALSE.  
  
##  <a name="ispointneardocksite"></a>  CFrameWndEx::IsPointNearDockSite  
 Determina si el punto se encuentra en una zona de alineación.  
  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *punto*  
 La posición del punto.  
  
 [out] *dwBarAlignment*  
 Donde el punto está alineado. Consulte la tabla en la sección Comentarios para los valores posibles.  
  
 [out] *bOuterEdge*  
 TRUE si el punto se encuentra cerca del borde de marco; FALSE si el punto se encuentra en un área de cliente.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el punto se encuentra en una zona de alineación; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 La tabla siguiente enumeran los valores posibles para el *dwBarAlignment* parámetro.  
  
 CBRS_ALIGN_TOP  
 Alinea a la parte superior.  
  
 CBRS_ALIGN_RIGHT  
 Alinea a la derecha.  
  
 CBRS_ALIGN_BOTTOM  
 Alinea a la parte inferior.  
  
 CBRS_ALIGN_LEFT  
 Alinea a la izquierda.  
  
##  <a name="isprintpreview"></a>  CFrameWndEx::IsPrintPreview  
 Determina si la ventana de marco está en modo de vista previa de impresión.  
  
```  
BOOL IsPrintPreview();
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la ventana de marco está en modo de vista previa de impresión; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="loadframe"></a>  CFrameWndEx::LoadFrame  
 Este método se llama después de la construcción para crear la ventana de marco y cargar sus recursos.  
  
```  
virtual BOOL LoadFrame(
    UINT nIDResource,  
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,  
    CWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nIDResource*  
 El identificador de recurso que se usa para cargar todos los recursos de marco.  
  
 [in] *dwDefaultStyle*  
 El estilo de ventana de marco de forma predeterminada.  
  
 [in] *pParentWnd*  
 Puntero a la ventana primaria del marco.  
  
 [in] *pContext*  
 Puntero a un [CCreateContext (estructura)](../../mfc/reference/ccreatecontext-structure.md) clase que se usa el marco de trabajo durante la creación de aplicaciones.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el método se realizó correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="negotiateborderspace"></a>  CFrameWndEx::NegotiateBorderSpace  
 Negociación de borde de cliente de implementa OLE.  
  
```  
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,  
    LPRECT lpRectBorder);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nBorderCmd*  
 El comando de negociación de borde. Consulte la sección Comentarios para los valores posibles.  
  
 [in, out] *lpRectBorder*  
 Dimensiones del borde.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se debe volver a calcular el diseño; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 La tabla siguiente enumeran los valores posibles para el *nBorderCmd* parámetro.  
  
 *borderGet*  
 Obtiene el espacio disponible de cliente OLE.  
  
 *borderRequest*  
 Espacio de cliente OLE de solicitud.  
  
 *borderSet*  
 Establecer el espacio de cliente OLE.  
  
##  <a name="onactivate"></a>  CFrameWndEx::OnActivate  
 El marco llama a este método cuando se cambia la entrada del usuario a o fuera del marco.  
  
```  
afx_msg void OnActivate(
    UINT nState,  
    CWnd* pWndOther,  
    BOOL bMinimized);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nState*  
 Si el marco está activo o inactivo. Consulte la tabla en la sección Comentarios para los valores posibles.  
  
 [in] *pWndOther*  
 Puntero a otra ventana que está cambiando la entrada del usuario con la actual.  
  
 [in] *bMinimized*  
 El estado minimizado del marco. TRUE si el marco está minimizado; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 La tabla siguiente enumeran los valores posibles para el *nState* parámetro.  
  
 WA_ACTIVE  
 El marco se selecciona un método distinto de un clic del mouse.  
  
 WA_CLICKACTIVE  
 El marco se selecciona mediante un clic del mouse.  
  
 WA_INACTIVE  
 El marco no está seleccionado.  
  
##  <a name="onactivateapp"></a>  CFrameWndEx::OnActivateApp  
 Lo llama el marco de trabajo cuando se selecciona o anula la selección de la aplicación.  
  
```  
afx_msg void OnActivateApp(
    BOOL bActive,  
    DWORD dwThreadID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bSecuencias de ActiveX*  
 TRUE si se selecciona la aplicación; FALSE si no se selecciona la aplicación.  
  
 [in] *dwThreadID*  
 Este parámetro no se utiliza.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onchangevisualmanager"></a>  CFrameWndEx::OnChangeVisualManager  
 Lo llama el marco cuando un cambio en el marco requiere un cambio en el administrador visual.  
  
```  
afx_msg LRESULT OnChangeVisualManager(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *wParam*  
 Este parámetro no se utiliza.  
  
 [in] *lParam*  
 Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onclose"></a>  CFrameWndEx::OnClose  
 El marco llama a este método para cerrar el marco.  
  
```  
afx_msg void OnClose();
```  
  
### <a name="remarks"></a>Comentarios  
 Si el marco está en modo de vista previa de impresión, envía un mensaje de Windows para cerrar la vista previa de impresión; en caso contrario, si el marco hospeda a un cliente OLE, se desactiva el cliente.  
  
##  <a name="onclosedockingpane"></a>  CFrameWndEx::OnCloseDockingPane  
 Lo llama el marco cuando el usuario hace clic en el **cerrar** botón en un panel acoplable.  
  
```  
virtual BOOL OnCloseDockingPane(CDockablePane* pPane);
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se puede cerrar la barra de acoplamiento. FALSE en caso contrario  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no hace nada. Invalide este método si desea controlar la ocultación de la barra de acoplamiento.  
  
##  <a name="oncloseminiframe"></a>  CFrameWndEx::OnCloseMiniFrame  
 Lo llama el marco cuando el usuario hace clic en el **cerrar** botón en una ventana de marco mini flotante.  
  
```  
virtual BOOL OnCloseMiniFrame(CPaneFrameWnd* pWnd);
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se puede cerrar una ventana de marco mini flotante. FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no hace nada. Invalide este método si desea procesar la ocultación de una ventana de marco mini flotante.  
  
##  <a name="onclosepopupmenu"></a>  CFrameWndEx::OnClosePopupMenu  
 Lo llama el marco cuando un menú emergente activo procesa un mensaje WM_DESTROY.  
  
```  
virtual void OnClosePopupMenu(CMFCPopupMenu* pMenuPopup);
```  
  
### <a name="parameters"></a>Parámetros  
 *pMenuPopup*  
 Un puntero a un menú emergente.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo envía un mensaje WM_DESTROY cuando está a punto de cerrar la ventana. Invalide este método si desea controlar las notificaciones de `CMFCPopupMenu` objetos que pertenecen a la ventana de marco cuando un `CMFCPopupMenu` objeto está procesando un mensaje WM_DESTROY enviado por el marco de trabajo cuando se cierra la ventana.  
  
##  <a name="oncmdmsg"></a>  CFrameWndEx::OnCmdMsg  
 Este comando envía los mensajes.  
  
```  
virtual BOOL OnCmdMsg(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nID*  
 Identificador del comando.  
  
 [in] *nCode*  
 Categoría del mensaje de comando.  
  
 [in, out] *pExtra*  
 Puntero a un objeto de comando.  
  
 [in, out] *pHandlerInfo*  
 Puntero a una estructura de controlador de comandos.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se ha controlado el mensaje de comando; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="oncontexthelp"></a>  CFrameWndEx::OnContextHelp  
 Lo llama el marco de trabajo para mostrar la ayuda relacionada con el contexto.  
  
```  
afx_msg void OnContextHelp();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="oncreate"></a>  CFrameWndEx::OnCreate  
 Lo llama el marco de trabajo una vez creado el marco.  
  
```  
afx_msg int OnCreate(LPCREATESTRUCT lpCreateStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *lpCreateStruct*  
 Un puntero a la [CREATESTRUCT (estructura)](../../mfc/reference/createstruct-structure.md) para el nuevo marco.  
  
### <a name="return-value"></a>Valor devuelto  
 0 para continuar con la creación de marco; -1 para destruir el marco.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondestroy"></a>  CFrameWndEx::OnDestroy  
 Lo llama el marco de trabajo cuando se destruye el marco.  
  
```  
afx_msg void OnDestroy();
```  
  
### <a name="remarks"></a>Comentarios  
 La tabla de aceleradores y todas las ventanas se destruyen.  
  
##  <a name="ondrawmenuimage"></a>  CFrameWndEx::OnDrawMenuImage  
 Lo llama el marco de trabajo cuando la aplicación dibuja la imagen asociada a un elemento de menú.  
  
```  
virtual BOOL OnDrawMenuImage(
    CDC* pDC,  
    const CMFCToolBarMenuButton* pMenuButton,  
    const CRect& rectImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a un contexto de dispositivo.  
  
 [in] *pMenuButton*  
 Un puntero a un botón de menú cuya imagen que se va a representar.  
  
 [in] *rectImage*  
 Un puntero a un `Rect` estructura que especifica la posición de la pantalla y el tamaño de la imagen.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el marco de trabajo representa correctamente la imagen. FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método si desea personalizar la representación de imagen para los elementos de menú que pertenecen a la barra de menús que pertenecen a la `CFrameWndEx` objeto derivado.  
  
##  <a name="ondrawmenulogo"></a>  CFrameWndEx::OnDrawMenuLogo  
 Lo llama el marco cuando un `CMFCPopupMenu` objeto procesa un mensaje WM_PAINT.  
  
```  
virtual void OnDrawMenuLogo(
    CDC* pDC,  
    CMFCPopupMenu* pMenu,  
    const CRect& rectLogo);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a un contexto de dispositivo.  
  
 [in] *pMenu*  
 Un puntero al elemento de menú.  
  
 [in] *rectLogo*  
 Una referencia a una constante `CRect` estructura que especifica la posición de la pantalla y el tamaño del logotipo de menú.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si desea mostrar un logotipo en el menú emergente que pertenece a la barra de menús que pertenecen a la `CFrameWndEx` objeto derivado.  
  
##  <a name="ondwmcompositionchanged"></a>  CFrameWndEx::OnDWMCompositionChanged  
 Lo llama el marco de trabajo cuando se habilita o deshabilita composición del Administrador de ventanas de escritorio (DWM).  
  
```  
afx_msg LRESULT OnDWMCompositionChanged(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *wp*  
 Este parámetro no se utiliza.  
  
 [in] *lp*  
 Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onexitsizemove"></a>  CFrameWndEx::OnExitSizeMove  
 Lo llama el marco de trabajo cuando detiene el marco de movimiento o cambio de tamaño.  
  
```  
LRESULT OnExitSizeMove(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *wp*  
 Este parámetro no se utiliza.  
  
 [in] *lp*  
 Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ongetminmaxinfo"></a>  CFrameWndEx::OnGetMinMaxInfo  
 Lo llama el marco de trabajo cuando se cambia el tamaño del marco para establecer los límites de la dimensión de ventana.  
  
```  
afx_msg void OnGetMinMaxInfo(MINMAXINFO FAR* lpMMI);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *lpMMI*  
 Puntero a un [MINMAXINFO](http://msdn.microsoft.com/library/windows/desktop/ms632605) estructura.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onidleupdatecmdui"></a>  CFrameWndEx::OnIdleUpdateCmdUI  
 Lo llama el marco de trabajo para actualizar la pantalla de marco cuando el procesamiento de comandos está inactivo.  
  
```  
afx_msg LRESULT OnIdleUpdateCmdUI(
    WPARAM wParam = 0,  
    LPARAM lParam = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *wParam*  
 Este parámetro no se utiliza.  
  
 [in] *lParam*  
 Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onlbuttondown"></a>  CFrameWndEx::OnLButtonDown  
 El marco llama a este método cuando el usuario presiona el botón primario del mouse.  
  
```  
afx_msg void OnLButtonDown(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nFlags*  
 Indica si el usuario presiona las teclas modificadoras. Para los valores posibles, vea el parámetro *wParam* en [WM_LBUTTONDOWN notificación](http://msdn.microsoft.com/library/windows/desktop/ms645607).  
  
 [in] *punto*  
 Especifica las coordenadas x e y del puntero, relativa a la esquina superior izquierda de la ventana.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onlbuttonup"></a>  CFrameWndEx::OnLButtonUp  
 El marco llama a este método cuando el usuario suelta el botón primario del mouse.  
  
```  
afx_msg void OnLButtonUp(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nFlags*  
 Indica si el usuario presiona las teclas modificadoras. Para los valores posibles, vea el parámetro *wParam* en [WM_LBUTTONUP notificación](http://msdn.microsoft.com/library/windows/desktop/ms645608).  
  
 [in] *punto*  
 Especifica las coordenadas x e y del puntero, relativa a la esquina superior izquierda de la ventana.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onmenubuttontoolhittest"></a>  CFrameWndEx::OnMenuButtonToolHitTest  
 Lo llama el marco cuando un `CMFCToolBarButton` objeto procesa un mensaje WM_NCHITTEST.  
  
```  
virtual BOOL OnMenuButtonToolHitTest(
    CMFCToolBarButton* pButton,  
    TOOLINFO* pTI);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pButton*  
 Un puntero en el botón de barra de herramientas.  
  
 [out] *pTI*  
 Un puntero a una estructura de información de la herramienta.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la aplicación rellena el *pTI* parámetro. FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método si desea proporcionar una información sobre herramientas acerca de un elemento de menú concreto.  
  
##  <a name="onmenuchar"></a>  CFrameWndEx::OnMenuChar  
 Lo llama el marco de trabajo cuando se muestra un menú y el usuario presiona una tecla que no corresponde a un comando.  
  
```  
afx_msg LRESULT OnMenuChar(
    UINT nChar,  
    UINT nFlags,  
    CMenu* pMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nChar*  
 Código de carácter de la tecla presionada.  
  
 [in] *nFlags*  
 Contiene la marca MF_POPUP si el menú que aparece es un submenú. contiene la marca MF_SYSMENU si la muestra es un menú de control.  
  
 [in] *pMenu*  
 Puntero a un menú.  
  
### <a name="return-value"></a>Valor devuelto  
 La palabra de orden superior debe ser uno de los siguientes valores.  
  
 `0`  
 El marco de trabajo debe pasar por alto la pulsación de tecla.  
  
 `1`  
 El marco de trabajo debería cerrar el menú.  
  
 `2`  
 El marco de trabajo debe seleccionar uno de los elementos mostrados en el menú. La palabra de orden inferior contiene el identificador del comando para seleccionar.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onmousemove"></a>  CFrameWndEx::OnMouseMove  
 El marco llama a este método cuando el puntero se mueve.  
  
```  
afx_msg void OnMouseMove(
    UINT nFlags,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nFlags*  
 Indica si un usuario presiona las teclas modificadoras. Para los valores posibles, vea el parámetro *wParam* en [WM_MOUSEMOVE notificación](http://msdn.microsoft.com/library/windows/desktop/ms645616).  
  
 [in] *punto*  
 Especifica la x e y las coordenadas del puntero en relación con la esquina superior izquierda de la ventana.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onmoveminiframe"></a>  CFrameWndEx::OnMoveMiniFrame  
 Lo llama el marco de trabajo cuando se mueve una ventana del panel.  
  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pFrame*  
 Puntero a la [CPaneFrameWnd (clase)](../../mfc/reference/cpaneframewnd-class.md) ventana del panel.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la ventana de panel no se acopla; FALSE si la ventana de panel se acopla.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onncactivate"></a>  CFrameWndEx::OnNcActivate  
 Lo llama el marco de trabajo cuando debe dibujarse el área no cliente del marco para indicar un cambio en el estado activo.  
  
```  
afx_msg BOOL OnNcActivate(BOOL bActive);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bSecuencias de ActiveX*  
 True para dibujar el fotograma activo; FALSE para dibujar el marco inactivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero para continuar con el procesamiento de forma predeterminada; 0 para evitar que el área no cliente se desactiva.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onnccalcsize"></a>  CFrameWndEx::OnNcCalcSize  
 Lo llama el marco de trabajo cuando se deben calcular el tamaño y posición del área de cliente.  
  
```  
afx_msg void OnNcCalcSize(
    BOOL bCalcValidRects,  
    NCCALCSIZE_PARAMS FAR* lpncsp);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bCalcValidRects*  
 Es TRUE cuando la aplicación debe especificar un área de cliente válido; en caso contrario, FALSE.  
  
 [in] *lpncsp*  
 Puntero a un `NCCALCSIZE_PARAMS` estructura que contiene los cambios de dimensión de fotograma.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onnchittest"></a>  CFrameWndEx::OnNcHitTest  
 Lo llama el marco cuando el puntero se mueve o al presionar o soltar un botón del mouse.  
  
```  
afx_msg LRESULT OnNcHitTest(CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *punto*  
 La ubicación del puntero en coordenadas de pantalla.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor enumerado de posicionamiento de un puntero. Para obtener una lista de valores posibles, vea [WM_NCHITTEST notificación](http://msdn.microsoft.com/library/windows/desktop/ms645618).  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onncmousemove"></a>  CFrameWndEx::OnNcMouseMove  
 Lo llama el marco cuando el puntero se mueve en un área no cliente.  
  
```  
afx_msg void OnNcMouseMove(
    UINT nHitTest,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nHitTest*  
 Valor enumerado de posicionamiento de un puntero. Para obtener una lista de valores posibles, vea [WM_NCHITTEST notificación](http://msdn.microsoft.com/library/windows/desktop/ms645618).  
  
 [in] *punto*  
 La ubicación del puntero en coordenadas de pantalla.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onncpaint"></a>  CFrameWndEx::OnNcPaint  
 Lo llama el marco de trabajo cuando se debe pintar el área no cliente.  
  
```  
afx_msg void OnNcPaint();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onpanecheck"></a>  CFrameWndEx::OnPaneCheck  
 Lo llama el marco de trabajo para controlar la visibilidad de un panel.  
  
```  
afx_msg BOOL OnPaneCheck(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nID*  
 Id. de un panel de control.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se controló el comando; FALSE para continuar con el procesamiento de comandos.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onpostpreviewframe"></a>  CFrameWndEx::OnPostPreviewFrame  
 Lo llama el marco cuando el usuario cambia el modo de vista previa de impresión.  
  
```  
afx_msg LRESULT OnPostPreviewFrame(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *wParam*  
 Este parámetro no se utiliza.  
  
 [in] *lParam*  
 Es TRUE cuando el marco está en modo de vista previa de impresión; FALSE cuando el modo de vista previa de impresión está desactivado.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onpowerbroadcast"></a>  CFrameWndEx::OnPowerBroadcast  
 Lo llama el marco de trabajo cuando se produce un evento de administración de energía.  
  
```  
afx_msg LRESULT OnPowerBroadcast(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *wp*  
 El evento de administración de energía. Para obtener una lista de valores posibles, vea [mensaje WM_POWERBROADCAST](http://msdn.microsoft.com/library/windows/desktop/aa373247).  
  
 [in] *lp*  
 Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 El resultado de llamar al procedimiento de ventana predeterminado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onsetmenu"></a>  CFrameWndEx::OnSetMenu  
 Lo llama el marco de trabajo para reemplazar el menú de la ventana de marco.  
  
```  
afx_msg LRESULT OnSetMenu(
    WPARAM wp,  
    LPARAM lp);  
  
BOOL OnSetMenu(HMENU hmenu);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *wp*  
 Identificador del nuevo menú de ventana de marco.  
  
 [in] *lp*  
 Identificador del menú Ventana nueva.  
  
 [in] *hmenu*  
 Identificador del nuevo menú de ventana de marco.  
  
### <a name="return-value"></a>Valor devuelto  
 LRESULT es el resultado de la llamada a procedimiento de ventana predeterminado.  
  
 BOOL es TRUE si se controló el evento; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onsetpreviewmode"></a>  CFrameWndEx::OnSetPreviewMode  
 Lo llama el marco de trabajo para establecer el modo de vista previa de impresión para el marco.  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bPreview*  
 TRUE para habilitar la vista previa de impresión; FALSO para deshabilitar la vista previa de impresión.  
  
 [in] *pState*  
 Puntero a un `CPrintPreviewState` enmarcar la estructura de estado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onsettext"></a>  CFrameWndEx::OnSetText  
 Lo llama el marco de trabajo para establecer el texto de una ventana.  
  
```  
afx_msg LRESULT OnSetText(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *wParam*  
 Este parámetro no se utiliza.  
  
 [in] *lParam*  
 Puntero al texto de la ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de una llamada a [DefWindowProc](http://msdn.microsoft.com/library/windows/desktop/ms633572).  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onshowcustomizepane"></a>  CFrameWndEx::OnShowCustomizePane  
 Lo llama el marco de trabajo cuando se muestre un `QuickCustomizePane`.  
  
```  
virtual BOOL OnShowCustomizePane(
    CMFCPopupMenu* pMenuPane,  
    UINT uiToolbarID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pMenuPane*  
 Un puntero a la rápida personalizar el panel.  
  
 [in] *uiToolbarID*  
 El identificador de control de la barra de herramientas para personalizar.  
  
### <a name="return-value"></a>Valor devuelto  
 Este método siempre devuelve TRUE.  
  
### <a name="remarks"></a>Comentarios  
 Personalizar la rápida es un menú emergente que aparece al hacer clic en el botón de personalizar la barra de herramientas  
  
##  <a name="onshowpanes"></a>  CFrameWndEx::OnShowPanes  
 Lo llama el marco de trabajo para mostrar u ocultar paneles.  
  
```  
virtual BOOL OnShowPanes(BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bMostrar*  
 TRUE si la aplicación muestra los paneles; FALSE en caso contrario.  
  
### <a name="return-value"></a>Valor devuelto  
 Este método siempre devuelve FALSE.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada muestra los paneles si *bMostrar* es TRUE y se ocultan los paneles o cuando *bMostrar* es FALSE y los paneles son visibles.  
  
 La implementación predeterminada oculta los paneles si *bMostrar* es TRUE y los paneles son visibles o cuando *bMostrar* es FALSE y los paneles están ocultas.  
  
 Invalide este método en una clase derivada para ejecutar código personalizado cuando el marco de trabajo muestra u oculta los paneles.  
  
##  <a name="onshowpopupmenu"></a>  CFrameWndEx::OnShowPopupMenu  
 Lo llama el marco de trabajo cuando se muestre un menú emergente.  
  
```  
virtual BOOL OnShowPopupMenu(CMFCPopupMenu* pMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pMenu*  
 Un puntero a un menú emergente.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el menú emergente es visible; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para ejecutar código personalizado cuando el marco de trabajo muestra un menú emergente. Por ejemplo, invalide este método para cambiar el color de fondo de los comandos en un menú emergente.  
  
##  <a name="onsize"></a>  CFrameWndEx::OnSize  
 Lo llama el marco de trabajo después de realizar cambios de tamaño del marco.  
  
```  
afx_msg void OnSize(
    UINT nType,  
    int cx,  
    int cy);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nLas*  
 El tipo de cambio de tamaño. Para los valores posibles, vea el parámetro *wParam* en [WM_SIZE notificación](http://msdn.microsoft.com/library/windows/desktop/ms632646).  
  
 [in] *cx*  
 Nuevo ancho del fotograma de píxeles.  
  
 [in] *cy*  
 Nuevo alto del fotograma de píxeles.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onsizing"></a>  CFrameWndEx::OnSizing  
 Lo llama el marco cuando el usuario cambia el tamaño del marco.  
  
```  
afx_msg void OnSizing(
    UINT fwSide,  
    LPRECT pRect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *fwSide*  
 El borde del marco que se mueve. Vea el parámetro *wParam* en [WM_SIZING notificación](http://msdn.microsoft.com/library/windows/desktop/ms632647).  
  
 [in, out] *pRect*  
 Puntero a un [CRect](../../atl-mfc-shared/reference/crect-class.md) o [RECT](../../mfc/reference/rect-structure1.md) estructura que contiene las coordenadas del marco.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onsyscolorchange"></a>  CFrameWndEx::OnSysColorChange  
 Lo llama el marco cuando cambian los colores del sistema.  
  
```  
void OnSysColorChange();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ontearoffmenu"></a>  CFrameWndEx::OnTearOffMenu  
 Lo llama el marco de trabajo cuando la aplicación muestra un menú que tiene una barra desplazable.  
  
```  
virtual BOOL OnTearOffMenu(
    CMFCPopupMenu* pMenuPopup,  
    CPane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pMenuPopup*  
 Un puntero a un menú emergente.  
  
 [in] *pBar*  
 Un puntero a una barra desplazable.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si está habilitado el menú emergente con la barra desplazable; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para ejecutar código personalizado cuando el marco de trabajo muestra una barra de control.  
  
 La implementación predeterminada no hace nada y devuelve TRUE.  
  
##  <a name="ontoolbarcontextmenu"></a>  CFrameWndEx::OnToolbarContextMenu  
 Lo llama el marco para crear un menú emergente de la barra de herramientas.  
  
```  
afx_msg LRESULT OnToolbarContextMenu(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *wp*  
 Este parámetro no se utiliza.  
  
 [in] *lp*  
 Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve 1.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ontoolbarcreatenew"></a>  CFrameWndEx::OnToolbarCreateNew  
 El marco llama a este método para crear una nueva barra de herramientas.  
  
```  
afx_msg LRESULT OnToolbarCreateNew(
    WPARAM wp,  
    LPARAM lp);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *wp*  
 Este parámetro no se utiliza.  
  
 [in] *lp*  
 Puntero al texto de la barra de título de la barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la nueva barra de herramientas; o NULL si no se ha creado una barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ontoolbardelete"></a>  CFrameWndEx::OnToolbarDelete  
 Lo llama el marco de trabajo cuando se elimina una barra de herramientas.  
  
```  
afx_msg LRESULT OnToolbarDelete(
    WPARAM, 
    LPARAM lp);
```  
  
### <a name="parameters"></a>Parámetros  
 [in]  
 Este parámetro no se utiliza.  
  
 [in] *lp*  
 Puntero a una barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se ha eliminado la barra de herramientas; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onupdateframemenu"></a>  CFrameWndEx::OnUpdateFrameMenu  
 Lo llama el marco de trabajo para establecer el menú del marco.  
  
```  
virtual void OnUpdateFrameMenu(HMENU hMenuAlt);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *hMenuAlt*  
 Identificador del menú alternativo.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onupdateframetitle"></a>  CFrameWndEx::OnUpdateFrameTitle  
 El marco llama a este método para actualizar la barra de título de la ventana de marco.  
  
```  
virtual void OnUpdateFrameTitle(BOOL bAddToTitle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bAddToTitle*  
 TRUE para agregar el título del documento activo en la barra de título de ventana de marco; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onupdatepanemenu"></a>  CFrameWndEx::OnUpdatePaneMenu  
 Lo llama el marco de trabajo para actualizar el menú del panel.  
  
```  
afx_msg void OnUpdatePaneMenu(CCmdUI* pCmdUI);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pCmdUI*  
 Puntero al objeto de interfaz de usuario de panel.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onwindowposchanged"></a>  CFrameWndEx::OnWindowPosChanged  
 Lo llama el marco cuando el tamaño del marco, la posición o el orden z ha cambiado debido a una llamada a un método de administración de la ventana.  
  
```  
afx_msg void OnWindowPosChanged(WINDOWPOS FAR* lpwndpos);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *lpwndpos*  
 Puntero a un [WINDOWPOS](../../mfc/reference/windowpos-structure1.md) estructura que contiene el nuevo tamaño y posición.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="panefrompoint"></a>  CFrameWndEx::PaneFromPoint  
 Busca en cada panel en el momento dado.  
  
```  
CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    bool bExactBar,  
    CRuntimeClass* pRTCBarType) const;  
  
CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    DWORD& dwAlignment,  
    CRuntimeClass* pRTCBarType) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *punto*  
 Las coordenadas de pantalla del punto para comprobar.  
  
 [in] *nSensitivity*  
 Cuando se busca el punto de, expanda el rectángulo delimitador de cada barra de control por esta cantidad.  
  
 [in] *bExactBar*  
 TRUE para omitir el *nSensitivity* parámetro; en caso contrario, FALSE.  
  
 [in] *pRTCBarType*  
 Si no es NULL, el método busca sólo las barras de control del tipo especificado.  
  
 [out] *dwAlignment*  
 Si se realiza correctamente, este parámetro contiene el lado de la barra de control que esté más próximo al punto especificado. En caso contrario, este parámetro no se ha inicializado.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a una barra de controles que contiene el *punto*; NULL si no se encuentra ningún control.  
  
### <a name="remarks"></a>Comentarios  
 Este método busca en todas las barras de control en la aplicación para un *punto*.  
  
 Use *nSensitivity* para aumentar el tamaño del área de búsqueda. Use *pRTCBarType* para restringir los tipos de barras de control que busca el método.  
  
##  <a name="pretranslatemessage"></a>  CFrameWndEx::PreTranslateMessage  
 Controla los mensajes de ventana específicos antes de enviarlos.  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pMsg*  
 Un puntero a un [MSG](../../mfc/reference/msg-structure1.md) estructura que contiene el mensaje que se va a procesar.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el mensaje se controló y no se debería enviar; 0 si el mensaje no se controló y debería enviarse.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="recalclayout"></a>  CFrameWndEx::RecalcLayout  
 Ajusta el diseño del marco y sus ventanas secundarias.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bNotify*  
 Especifica si se debe notificar el elemento de cliente OLE sobre el cambio de diseño.  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama cuando ha cambiado el tamaño de la ventana de marco o cuando se muestren u ocultas los barras de control.  
  
##  <a name="removepanefromdockmanager"></a>  CFrameWndEx::RemovePaneFromDockManager  
 Anula el registro de un panel y se quita el Administrador de acoplamiento.  
  
```  
void RemovePaneFromDockManager(
    CBasePane* pControlBar,  
    BOOL bDestroy,  
    BOOL bAdjustLayout,  
    BOOL bAutoHide,  
    CBasePane* pBarReplacement);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pControlBar*  
 Un puntero en el panel de barra de control para quitar.  
  
 [in] *bDestroy*  
 TRUE para destruir la barra de control después de quitarla; FALSE en caso contrario.  
  
 [in] *bAdjustLayout*  
 TRUE para ajustar el diseño de acoplamiento FALSE en caso contrario.  
  
 [in] *bAutoHide*  
 TRUE si la barra de control está en modo de ocultación automática; FALSE en caso contrario.  
  
 [in] *pBarReplacement*  
 Un puntero a un panel que reemplaza el panel quitado.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para quitar una barra de controles de diseño de acoplamiento de la ventana de marco.  
  
 El [CDockingManager Class](../../mfc/reference/cdockingmanager-class.md) controla el diseño de las barras de control. Debe registrar cada barra de control con el Administrador de acoplamiento con el [CFrameWndEx::AddPane](#addpane) método o la [CFrameWndEx::InsertPane](#insertpane) método.  
  
##  <a name="setdockstate"></a>  CFrameWndEx::SetDockState  
 Restaura el diseño de acoplamiento en el estado de acoplamiento almacenado en el registro.  
  
```  
void SetDockState(const CDockState& state);
```  
  
### <a name="parameters"></a>Parámetros  
 *state*  
 El estado de acoplamiento. Este parámetro se ignora.  
  
##  <a name="setprintpreviewframe"></a>  CFrameWndEx::SetPrintPreviewFrame  
 Establece la ventana de marco de vista previa de impresión.  
  
```  
void SetPrintPreviewFrame(CFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *conquistado*  
 Puntero a una ventana de marco de vista previa de impresión.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setuptoolbarmenu"></a>  CFrameWndEx::SetupToolbarMenu  
 Comandos definidos por el usuario inserta en un menú de barra de herramientas.  
  
```  
void SetupToolbarMenu(
    CMenu& menu,  
    const UINT uiViewUserToolbarCmdFirst,  
    const UINT uiViewUserToolbarCmdLast);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *menú*  
 Un `CMenu` objeto va a modificar.  
  
 [in] *uiViewUserToolbarCmdFirst*  
 El primer comando definido por el usuario.  
  
 [in] *uiViewUserToolbarCmdLast*  
 El último comando definido por el usuario.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo almacena los comandos definidos por el usuario en una lista. Use *uiViewUserToolbarCmdFirst* y *uiViewUserToolbarCmdList* para especificar los índices de los comandos que se va a insertar.  
  
##  <a name="showfullscreen"></a>  CFrameWndEx::ShowFullScreen  
 Cambia el marco principal entre el modo normal y el modo de pantalla completa.  
  
```  
void ShowFullScreen();
```  
  
##  <a name="showpane"></a>  CFrameWndEx::ShowPane  
 Muestra u oculta el panel especificado.  
  
```  
void ShowPane(
    CBasePane* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pBar*  
 Un puntero a la barra de control para mostrar u ocultar.  
  
 [in] *bMostrar*  
 Si es TRUE, la aplicación muestra la barra de control. En caso contrario, la aplicación oculta la barra de control.  
  
 [in] *bDelay*  
 Si es TRUE, retrasar el ajuste del diseño de acoplamiento hasta que llama el marco [CFrameWndEx::AdjustDockingLayout](#adjustdockinglayout). En caso contrario, vuelve a calcular el diseño de acoplamiento inmediatamente.  
  
 [in] *bActivate*  
 Si es TRUE, activar la barra de control. En caso contrario, se muestra la barra de control en un estado inactivo.  
  
##  <a name="updatecaption"></a>  CFrameWndEx::UpdateCaption  
 Lo llama el marco de trabajo para actualizar el título del marco de ventana.  
  
```  
void UpdateCaption();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="winhelp"></a>  CFrameWndEx::WinHelp  
 Invoca la aplicación WinHelp o el contexto de ayuda relacionada.  
  
```  
virtual void WinHelp(
    DWORD dwData,  
    UINT nCmd = HELP_CONTEXT);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwData*  
 Datos que dependen del *nCmd* parámetro. Para obtener una lista de valores posibles, vea [WinHelp](http://msdn.microsoft.com/library/windows/desktop/bb762267).  
  
 *nCmd*  
 El comando help. Para obtener una lista de valores posibles, vea [WinHelp](http://msdn.microsoft.com/library/windows/desktop/bb762267).  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)
