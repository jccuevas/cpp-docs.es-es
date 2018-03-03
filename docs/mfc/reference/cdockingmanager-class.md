---
title: Clase CDockingManager | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDockingManager
- AFXDOCKINGMANAGER/CDockingManager
- AFXDOCKINGMANAGER/CDockingManager::AddDockSite
- AFXDOCKINGMANAGER/CDockingManager::AddHiddenMDITabbedBar
- AFXDOCKINGMANAGER/CDockingManager::AddMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::AddPane
- AFXDOCKINGMANAGER/CDockingManager::AdjustDockingLayout
- AFXDOCKINGMANAGER/CDockingManager::AdjustPaneFrames
- AFXDOCKINGMANAGER/CDockingManager::AdjustRectToClientArea
- AFXDOCKINGMANAGER/CDockingManager::AlignAutoHidePane
- AFXDOCKINGMANAGER/CDockingManager::AutoHidePane
- AFXDOCKINGMANAGER/CDockingManager::BringBarsToTop
- AFXDOCKINGMANAGER/CDockingManager::BuildPanesMenu
- AFXDOCKINGMANAGER/CDockingManager::CalcExpectedDockedRect
- AFXDOCKINGMANAGER/CDockingManager::Create
- AFXDOCKINGMANAGER/CDockingManager::DeterminePaneAndStatus
- AFXDOCKINGMANAGER/CDockingManager::DisableRestoreDockState
- AFXDOCKINGMANAGER/CDockingManager::DockPane
- AFXDOCKINGMANAGER/CDockingManager::DockPaneLeftOf
- AFXDOCKINGMANAGER/CDockingManager::EnableAutoHidePanes
- AFXDOCKINGMANAGER/CDockingManager::EnableDocking
- AFXDOCKINGMANAGER/CDockingManager::EnableDockSiteMenu
- AFXDOCKINGMANAGER/CDockingManager::EnablePaneContextMenu
- AFXDOCKINGMANAGER/CDockingManager::FindDockSite
- AFXDOCKINGMANAGER/CDockingManager::FindDockSiteByPane
- AFXDOCKINGMANAGER/CDockingManager::FindPaneByID
- AFXDOCKINGMANAGER/CDockingManager::FixupVirtualRects
- AFXDOCKINGMANAGER/CDockingManager::FrameFromPoint
- AFXDOCKINGMANAGER/CDockingManager::GetClientAreaBounds
- AFXDOCKINGMANAGER/CDockingManager::GetDockingMode
- AFXDOCKINGMANAGER/CDockingManager::GetDockSiteFrameWnd
- AFXDOCKINGMANAGER/CDockingManager::GetEnabledAutoHideAlignment
- AFXDOCKINGMANAGER/CDockingManager::GetMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::GetOuterEdgeBounds
- AFXDOCKINGMANAGER/CDockingManager::GetPaneList
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingManager
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingManagerPermanent
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingParams
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingTheme
- AFXDOCKINGMANAGER/CDockingManager::HideAutoHidePanes
- AFXDOCKINGMANAGER/CDockingManager::InsertDockSite
- AFXDOCKINGMANAGER/CDockingManager::InsertPane
- AFXDOCKINGMANAGER/CDockingManager::IsDockSiteMenu
- AFXDOCKINGMANAGER/CDockingManager::IsInAdjustLayout
- AFXDOCKINGMANAGER/CDockingManager::IsOLEContainerMode
- AFXDOCKINGMANAGER/CDockingManager::IsPointNearDockSite
- AFXDOCKINGMANAGER/CDockingManager::IsPrintPreviewValid
- AFXDOCKINGMANAGER/CDockingManager::LoadState
- AFXDOCKINGMANAGER/CDockingManager::LockUpdate
- AFXDOCKINGMANAGER/CDockingManager::OnActivateFrame
- AFXDOCKINGMANAGER/CDockingManager::OnClosePopupMenu
- AFXDOCKINGMANAGER/CDockingManager::OnMoveMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::OnPaneContextMenu
- AFXDOCKINGMANAGER/CDockingManager::PaneFromPoint
- AFXDOCKINGMANAGER/CDockingManager::ProcessPaneContextMenuCommand
- AFXDOCKINGMANAGER/CDockingManager::RecalcLayout
- AFXDOCKINGMANAGER/CDockingManager::ReleaseEmptyPaneContainers
- AFXDOCKINGMANAGER/CDockingManager::RemoveHiddenMDITabbedBar
- AFXDOCKINGMANAGER/CDockingManager::RemoveMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::RemovePaneFromDockManager
- AFXDOCKINGMANAGER/CDockingManager::ReplacePane
- AFXDOCKINGMANAGER/CDockingManager::ResortMiniFramesForZOrder
- AFXDOCKINGMANAGER/CDockingManager::SaveState
- AFXDOCKINGMANAGER/CDockingManager::SendMessageToMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::Serialize
- AFXDOCKINGMANAGER/CDockingManager::SetAutohideZOrder
- AFXDOCKINGMANAGER/CDockingManager::SetDockingMode
- AFXDOCKINGMANAGER/CDockingManager::SetDockState
- AFXDOCKINGMANAGER/CDockingManager::SetPrintPreviewMode
- AFXDOCKINGMANAGER/CDockingManager::SetSmartDockingParams
- AFXDOCKINGMANAGER/CDockingManager::ShowDelayShowMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::ShowPanes
- AFXDOCKINGMANAGER/CDockingManager::StartSDocking
- AFXDOCKINGMANAGER/CDockingManager::StopSDocking
- AFXDOCKINGMANAGER/CDockingManager::m_bHideDockingBarsInContainerMode
- AFXDOCKINGMANAGER/CDockingManager::m_dockModeGlobal
- AFXDOCKINGMANAGER/CDockingManager::m_nDockSensitivity
- AFXDOCKINGMANAGER/CDockingManager::m_nTimeOutBeforeDockingBarDock
- AFXDOCKINGMANAGER/CDockingManager::m_nTimeOutBeforeToolBarDock
dev_langs:
- C++
helpviewer_keywords:
- CDockingManager [MFC], AddDockSite
- CDockingManager [MFC], AddHiddenMDITabbedBar
- CDockingManager [MFC], AddMiniFrame
- CDockingManager [MFC], AddPane
- CDockingManager [MFC], AdjustDockingLayout
- CDockingManager [MFC], AdjustPaneFrames
- CDockingManager [MFC], AdjustRectToClientArea
- CDockingManager [MFC], AlignAutoHidePane
- CDockingManager [MFC], AutoHidePane
- CDockingManager [MFC], BringBarsToTop
- CDockingManager [MFC], BuildPanesMenu
- CDockingManager [MFC], CalcExpectedDockedRect
- CDockingManager [MFC], Create
- CDockingManager [MFC], DeterminePaneAndStatus
- CDockingManager [MFC], DisableRestoreDockState
- CDockingManager [MFC], DockPane
- CDockingManager [MFC], DockPaneLeftOf
- CDockingManager [MFC], EnableAutoHidePanes
- CDockingManager [MFC], EnableDocking
- CDockingManager [MFC], EnableDockSiteMenu
- CDockingManager [MFC], EnablePaneContextMenu
- CDockingManager [MFC], FindDockSite
- CDockingManager [MFC], FindDockSiteByPane
- CDockingManager [MFC], FindPaneByID
- CDockingManager [MFC], FixupVirtualRects
- CDockingManager [MFC], FrameFromPoint
- CDockingManager [MFC], GetClientAreaBounds
- CDockingManager [MFC], GetDockingMode
- CDockingManager [MFC], GetDockSiteFrameWnd
- CDockingManager [MFC], GetEnabledAutoHideAlignment
- CDockingManager [MFC], GetMiniFrames
- CDockingManager [MFC], GetOuterEdgeBounds
- CDockingManager [MFC], GetPaneList
- CDockingManager [MFC], GetSmartDockingManager
- CDockingManager [MFC], GetSmartDockingManagerPermanent
- CDockingManager [MFC], GetSmartDockingParams
- CDockingManager [MFC], GetSmartDockingTheme
- CDockingManager [MFC], HideAutoHidePanes
- CDockingManager [MFC], InsertDockSite
- CDockingManager [MFC], InsertPane
- CDockingManager [MFC], IsDockSiteMenu
- CDockingManager [MFC], IsInAdjustLayout
- CDockingManager [MFC], IsOLEContainerMode
- CDockingManager [MFC], IsPointNearDockSite
- CDockingManager [MFC], IsPrintPreviewValid
- CDockingManager [MFC], LoadState
- CDockingManager [MFC], LockUpdate
- CDockingManager [MFC], OnActivateFrame
- CDockingManager [MFC], OnClosePopupMenu
- CDockingManager [MFC], OnMoveMiniFrame
- CDockingManager [MFC], OnPaneContextMenu
- CDockingManager [MFC], PaneFromPoint
- CDockingManager [MFC], ProcessPaneContextMenuCommand
- CDockingManager [MFC], RecalcLayout
- CDockingManager [MFC], ReleaseEmptyPaneContainers
- CDockingManager [MFC], RemoveHiddenMDITabbedBar
- CDockingManager [MFC], RemoveMiniFrame
- CDockingManager [MFC], RemovePaneFromDockManager
- CDockingManager [MFC], ReplacePane
- CDockingManager [MFC], ResortMiniFramesForZOrder
- CDockingManager [MFC], SaveState
- CDockingManager [MFC], SendMessageToMiniFrames
- CDockingManager [MFC], Serialize
- CDockingManager [MFC], SetAutohideZOrder
- CDockingManager [MFC], SetDockingMode
- CDockingManager [MFC], SetDockState
- CDockingManager [MFC], SetPrintPreviewMode
- CDockingManager [MFC], SetSmartDockingParams
- CDockingManager [MFC], ShowDelayShowMiniFrames
- CDockingManager [MFC], ShowPanes
- CDockingManager [MFC], StartSDocking
- CDockingManager [MFC], StopSDocking
- CDockingManager [MFC], m_bHideDockingBarsInContainerMode
- CDockingManager [MFC], m_dockModeGlobal
- CDockingManager [MFC], m_nDockSensitivity
- CDockingManager [MFC], m_nTimeOutBeforeDockingBarDock
- CDockingManager [MFC], m_nTimeOutBeforeToolBarDock
ms.assetid: 98e69c43-55d8-4f43-b861-4fda80ec1e32
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2f1a436ab6bfbc5e21e43267d3992310ed6f6a20
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cdockingmanager-class"></a>Clase CDockingManager
Implementa la funcionalidad básica que controla el diseño de acoplamiento en una ventana de marco principal.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDockingManager : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDockingManager::AddDockSite](#adddocksite)|Crea un panel de acoplamiento y lo agrega a la lista de barras de control.|  
|[CDockingManager::AddHiddenMDITabbedBar](#addhiddenmditabbedbar)|Agrega un identificador a una barra de panel a la lista de MDI oculto por pestañas paneles de barra.|  
|[CDockingManager::AddMiniFrame](#addminiframe)|Agrega un marco a la lista de fotogramas minivolcados.|  
|[CDockingManager::AddPane](#addpane)|Registra un panel con el Administrador de acoplamiento.|  
|[CDockingManager::AdjustDockingLayout](#adjustdockinglayout)|Vuelve a calcular y ajusta el diseño de todos los paneles en una ventana de marco.|  
|[CDockingManager::AdjustPaneFrames](#adjustpaneframes)|Hace que la `WM_NCCALCSIZE` mensaje que se enviará a todos los paneles y `CPaneFrameWnd` windows.|  
|[CDockingManager::AdjustRectToClientArea](#adjustrecttoclientarea)|Ajusta la alineación de un rectángulo.|  
|[CDockingManager::AlignAutoHidePane](#alignautohidepane)|Cambia el tamaño de un panel acoplable en modo de ocultación automática para que toma todo el ancho o alto del área de cliente del marco rodeado por acoplar sitios.|  
|[CDockingManager::AutoHidePane](#autohidepane)|Crea una barra de herramientas Ocultar automáticamente.|  
|[CDockingManager::BringBarsToTop](#bringbarstotop)|Hace que las barras acopladas que tienen la alineación especificada en la parte superior.|  
|[CDockingManager::BuildPanesMenu](#buildpanesmenu)|Agrega nombres de paneles de acoplamiento y barras de herramientas a un menú.|  
|[CDockingManager::CalcExpectedDockedRect](#calcexpecteddockedrect)|Calcula el rectángulo esperado de una ventana acoplada.|  
|[CDockingManager::Create](#create)|Crea un administrador de acoplamiento.|  
|[CDockingManager::DeterminePaneAndStatus](#determinepaneandstatus)|Determina el panel que contiene un punto determinado y su estado de acoplamiento.|  
|[CDockingManager::DisableRestoreDockState](#disablerestoredockstate)|Habilita o deshabilita la carga de diseño de acoplamiento del registro.|  
|[CDockingManager::DockPane](#dockpane)|Acopla un panel a otro panel o una ventana de marco.|  
|[CDockingManager::DockPaneLeftOf](#dockpaneleftof)|Acopla un panel a la izquierda de otro panel.|  
|[CDockingManager::EnableAutoHidePanes](#enableautohidepanes)|Permite al marco principal de acoplamiento del panel, crea un panel de acoplamiento y lo agrega a la lista de barras de control.|  
|[CDockingManager::EnableDocking](#enabledocking)|Crea un panel de acoplamiento y permite al marco principal de acoplamiento del panel.|  
|[CDockingManager::EnableDockSiteMenu](#enabledocksitemenu)|Muestra un botón que abre un menú emergente en los títulos de todos los paneles de acoplamiento.|  
|[CDockingManager::EnablePaneContextMenu](#enablepanecontextmenu)|Indica la biblioteca que se va a mostrar un menú contextual especial que tiene una lista de paneles de acoplamiento y barras de herramientas de aplicación cuando el usuario hace clic en el botón secundario del mouse y la biblioteca está procesando el mensaje WM_CONTEXTMENU.|  
|[CDockingManager::FindDockSite](#finddocksite)|Recupera la barra de panel que está en la posición especificada y que tiene la alineación especificadas.|  
|[CDockingManager::FindDockSiteByPane](#finddocksitebypane)|Devuelve la barra de panel que tiene el identificador del panel de barra de destino.|  
|[CDockingManager::FindPaneByID](#findpanebyid)|Busca un panel con el identificador del control especificado.|  
|[CDockingManager::FixupVirtualRects](#fixupvirtualrects)|Confirma todas las posiciones de la barra de herramientas actual a los rectángulos virtuales.|  
|[CDockingManager::FrameFromPoint](#framefrompoint)|Devuelve el marco que contiene el punto especificado.|  
|[CDockingManager::GetClientAreaBounds](#getclientareabounds)|Obtiene el rectángulo que contiene los límites del área de cliente.|  
|[CDockingManager::GetDockingMode](#getdockingmode)|Devuelve el modo de acoplamiento actual.|  
|[CDockingManager::GetDockSiteFrameWnd](#getdocksiteframewnd)|Obtiene un puntero al marco de ventana primaria.|  
|[CDockingManager::GetEnabledAutoHideAlignment](#getenabledautohidealignment)|Devuelve la alineación de los paneles habilitada.|  
|[CDockingManager::GetMiniFrames](#getminiframes)|Obtiene una lista de miniframes.|  
|[CDockingManager::GetOuterEdgeBounds](#getouteredgebounds)|Obtiene un rectángulo que contiene los bordes exteriores del marco.|  
|[CDockingManager::GetPaneList](#getpanelist)|Devuelve una lista de paneles que pertenecen al administrador de acoplamiento. Esto incluye todos los paneles flotantes.|  
|[CDockingManager::GetSmartDockingManager](#getsmartdockingmanager)|Recupera un puntero al administrador de acoplamiento inteligente.|  
|[CDockingManager::GetSmartDockingManagerPermanent](#getsmartdockingmanagerpermanent)|Recupera un puntero al administrador de acoplamiento inteligente.|  
|[CDockingManager::GetSmartDockingParams](#getsmartdockingparams)|Devuelve los parámetros de acoplamiento inteligentes para el Administrador de acoplamiento.|  
|[CDockingManager::GetSmartDockingTheme](#getsmartdockingtheme)|Un método estático que devuelve un tema que se usa para mostrar marcadores de acoplamiento inteligente.|  
|[CDockingManager::HideAutoHidePanes](#hideautohidepanes)|Oculta un panel que se encuentra en modo de ocultación automática.|  
|[CDockingManager::InsertDockSite](#insertdocksite)|Crea un panel de acoplamiento y lo inserta en la lista de barras de control.|  
|[CDockingManager::InsertPane](#insertpane)|Inserta un panel de control en la lista de barras de control.|  
|[CDockingManager::IsDockSiteMenu](#isdocksitemenu)|Especifica si se muestra un menú emergente en los títulos de todos los paneles.|  
|[CDockingManager::IsInAdjustLayout](#isinadjustlayout)|Determina si se ajustan los diseños de todos los paneles.|  
|[CDockingManager::IsOLEContainerMode](#isolecontainermode)|Especifica si el Administrador de acoplamiento está en modo de contenedor OLE.|  
|[CDockingManager::IsPointNearDockSite](#ispointneardocksite)|Determina si un punto especificado se encuentra cerca del sitio de vinculación.|  
|[CDockingManager::IsPrintPreviewValid](#isprintpreviewvalid)|Determina si se establece el modo de vista previa de impresión.|  
|[CDockingManager::LoadState](#loadstate)|Carga el estado del Administrador de acoplamiento desde el registro.|  
|[CDockingManager::LockUpdate](#lockupdate)|Bloquea la ventana especificada.|  
|[CDockingManager::OnActivateFrame](#onactivateframe)|Lo llama el marco de trabajo cuando la ventana de marco estará activa o se desactiva.|  
|[CDockingManager::OnClosePopupMenu](#onclosepopupmenu)|Lo llama el marco cuando un menú emergente activo procesa un mensaje WM_DESTROY.|  
|[CDockingManager::OnMoveMiniFrame](#onmoveminiframe)|Lo llama el marco para mover una ventana de marco reducido.|  
|[CDockingManager::OnPaneContextMenu](#onpanecontextmenu)|Lo llama el marco cuando compila un menú con una lista de paneles.|  
|[CDockingManager::PaneFromPoint](#panefrompoint)|Devuelve el panel que contiene el punto especificado.|  
|[CDockingManager::ProcessPaneContextMenuCommand](#processpanecontextmenucommand)|Lo llama el marco de trabajo para seleccionar o para desactivar una casilla de verificación para el comando especificado y vuelva a calcular el diseño de un panel se muestra.|  
|[CDockingManager::RecalcLayout](#recalclayout)|Vuelve a calcular el diseño interno de los controles que se encuentra en la lista de controles.|  
|[CDockingManager::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)|Libera los contenedores de panel vacía.|  
|[CDockingManager::RemoveHiddenMDITabbedBar](#removehiddenmditabbedbar)|Quita oculta la barra panel especificado.|  
|[CDockingManager::RemoveMiniFrame](#removeminiframe)|Quita un período especificado de la lista de fotogramas minivolcados.|  
|[CDockingManager::RemovePaneFromDockManager](#removepanefromdockmanager)|Anula el registro de un panel y lo quita de la lista en el Administrador de acoplamiento.|  
|[CDockingManager::ReplacePane](#replacepane)|Reemplaza un panel con otro.|  
|[CDockingManager::ResortMiniFramesForZOrder](#resortminiframesforzorder)|Vuelve a ordenar los marcos en la lista de fotogramas minivolcados.|  
|[CDockingManager::SaveState](#savestate)|Guarda el estado del Administrador de acoplamiento en el registro.|  
|[CDockingManager::SendMessageToMiniFrames](#sendmessagetominiframes)|Envía el mensaje especificado a todos los marcos minivolcados.|  
|[CDockingManager::Serialize](#serialize)|Escribe el Administrador de acoplamiento en un archivo. (Invalida [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)).|  
|[CDockingManager::SetAutohideZOrder](#setautohidezorder)|Establece el tamaño, ancho y alto de las barras de control y el panel especificado.|  
|[CDockingManager::SetDockingMode](#setdockingmode)|Establece el modo de acoplamiento.|  
|[CDockingManager::SetDockState](#setdockstate)|Establece el estado de acoplamiento de las barras de control, los marcos minivolcados y las barras Ocultar automáticamente.|  
|[CDockingManager::SetPrintPreviewMode](#setprintpreviewmode)|Establece el modo de vista previa de impresión de las barras que se muestran en la vista previa de impresión.|  
|[CDockingManager::SetSmartDockingParams](#setsmartdockingparams)|Establece los parámetros que definen el comportamiento de acoplamiento inteligente.|  
|[CDockingManager::ShowDelayShowMiniFrames](#showdelayshowminiframes)|Muestra u oculta las ventanas de los marcos minivolcados.|  
|[CDockingManager::ShowPanes](#showpanes)|Muestra u oculta los paneles de las barras de control y ocultar automáticamente.|  
|[CDockingManager::StartSDocking](#startsdocking)|Inicia el acoplamiento inteligente de la ventana especificada según la alineación del Administrador de acoplamiento inteligente.|  
|[CDockingManager::StopSDocking](#stopsdocking)|Se detiene inteligentes de acoplamiento.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)|Especifica si el Administrador de acoplamiento oculta paneles en modo de contenedor OLE.|  
|[CDockingManager::m_dockModeGlobal](#m_dockmodeglobal)|Especifica el modo de acoplamiento global.|  
|[CDockingManager::m_nDockSensitivity](#m_ndocksensitivity)|Especifica la distinción de acoplamiento.|  
|[CDockingManager::m_nTimeOutBeforeDockingBarDock](#m_ntimeoutbeforedockingbardock)|Especifica el tiempo, en milisegundos, antes de que se acopla un panel acoplable en el modo de acoplamiento inmediato.|  
|[CDockingManager::m_nTimeOutBeforeToolBarDock](#m_ntimeoutbeforetoolbardock)|Especifica el tiempo, en milisegundos, antes de una barra de herramientas está acoplada a la ventana de marco principal.|  
  
## <a name="remarks"></a>Comentarios  
 La ventana de marco principal se crea e inicializa automáticamente esta clase.  
  
 El objeto de administrador de acoplamiento contiene una lista de todos los paneles que se encuentran en el diseño de acoplamiento y también una lista de todos los [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) windows que pertenecen a la ventana de marco principal.  
  
 El `CDockingManager` clase implementa algunos servicios que puede usar para buscar un panel o un `CPaneFrameWnd` ventana. Normalmente no llamar a estos servicios directamente ya se ajustan en el objeto de ventana de marco principal. Para obtener más información, consulte [CPaneFrameWnd clase](../../mfc/reference/cpaneframewnd-class.md).  
  
## <a name="customization-tips"></a>Sugerencias de personalización  
 Las siguientes sugerencias se aplican a `CDockingManager` objetos:  
  
- [Clase CDockingManager](../../mfc/reference/cdockingmanager-class.md) admite estos modos de acoplamiento:  
  
    - `AFX_DOCK_TYPE::DT_IMMEDIATE`  
  
    - `AFX_DOCK_TYPE::DT_STANDARD`  
  
    - `AFX_DOCK_TYPE::DT_SMART`  
  
     Estos modos de acoplamiento se definen mediante [CDockingManager::m_dockModeGlobal](#m_dockmodeglobal) y se establecen mediante una llamada a [CDockingManager::SetDockingMode](#setdockingmode).  
  
-   Si desea crear un panel flotante no, no se puede cambiar, llame a la [CDockingManager::AddPane](#addpane) método. Este método registra el panel con el Administrador de acoplamiento, que es responsable del diseño del panel.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar distintos métodos en el `CDockingManager` clase para configurar un `CDockingManager` objeto. En el ejemplo se muestra cómo mostrar un botón que abre un menú emergente en los títulos de todos los paneles de acoplamiento y cómo establecer el modo de acoplamiento del objeto. Este fragmento de código forma parte de la [ejemplo de demostración de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#24](../../mfc/codesnippet/cpp/cdockingmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDockingManager](../../mfc/reference/cdockingmanager-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxDockingManager.h  
  
##  <a name="adddocksite"></a>CDockingManager::AddDockSite  
 Crea un panel de acoplamiento y lo agrega a la lista de barras de control.  
  
```  
BOOL AddDockSite(
    const AFX_DOCKSITE_INFO& info,  
    CDockSite** ppDockBar = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `info`  
 Una referencia a una estructura de información que contiene se acopla alineación del panel.  
  
 [out] `ppDockBar`  
 Un puntero a un puntero a la nueva acoplar el panel.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel de acoplamiento se creó correctamente; `FALSE` en caso contrario.  
  
##  <a name="addhiddenmditabbedbar"></a>CDockingManager::AddHiddenMDITabbedBar  
 Agrega un identificador a una barra de panel a la lista de MDI oculto por pestañas paneles de barra.  
  
```  
void AddHiddenMDITabbedBar(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Un puntero a una barra de panel  
  
##  <a name="addpane"></a>CDockingManager::AddPane  
 Registra un panel con el Administrador de acoplamiento.  
  
```  
BOOL AddPane(
    CBasePane* pWnd,  
    BOOL bTail = TRUE,  
    BOOL bAutoHide = FALSE,  
    BOOL bInsertForOuterEdge = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in, out] `pWnd`  
 Especifica el panel para agregar al administrador de acoplamiento.  
  
 [in] `bTail`  
 `TRUE`Para agregar el panel al final de la lista de paneles para el Administrador de acoplamiento; en caso contrario, `FALSE`.  
  
 [in] `bAutoHide`  
 Sólo para uso interno. Utilice siempre el valor predeterminado `FALSE`.  
  
 [in] `bInsertForOuterEdge`  
 Sólo para uso interno. Utilice siempre el valor predeterminado `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se registró correctamente con el Administrador de acoplamiento; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para registrar los paneles no flotante, no se puede cambiar con el Administrador de acoplamiento. Si no registra los paneles, no se mostrarán correctamente cuando se diseña el Administrador de acoplamiento.  
  
##  <a name="adjustdockinglayout"></a>CDockingManager::AdjustDockingLayout  
 Vuelve a calcular y ajusta el diseño de todos los paneles en una ventana de marco.  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hdwp`  
 Especifica la estructura de posición de la ventana diferida. Para obtener más información, vea [Tipos de datos de Windows](http://msdn.microsoft.com/library/windows/desktop/aa383751).  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="addminiframe"></a>CDockingManager::AddMiniFrame  
 Agrega un marco a la lista de fotogramas minivolcados.  
  
```  
virtual BOOL AddMiniFrame(CPaneFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Un puntero a un marco.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el marco no está en la lista de fotogramas minivolcados y se ha agregado correctamente; `FALSE` en caso contrario.  
  
##  <a name="adjustpaneframes"></a>CDockingManager::AdjustPaneFrames  
 Hace que la `WM_NCCALCSIZE` mensaje que se enviará a todos los paneles y `CPaneFrameWnd` windows.  
  
```  
virtual void AdjustPaneFrames();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="adjustrecttoclientarea"></a>CDockingManager::AdjustRectToClientArea  
 Ajusta la alineación de un rectángulo.  
  
```  
virtual BOOL AdjustRectToClientArea(
    CRect& rectResult,  
    DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectResult`  
 Una referencia a un `CRect` objeto  
  
 [in] `dwAlignment`  
 La alineación de la `CRect` objeto  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la alineación de la `CRect` se ha ajustado el objeto; `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 El `dwAlignment` parámetro puede tener uno de los siguientes valores:  
  
-   CBRS_ALIGN_TOP  
  
-   CBRS_ALIGN_BOTTOM  
  
-   CBRS_ALIGN_LEFT  
  
-   CBRS_ALIGN_RIGHT  
  
##  <a name="alignautohidepane"></a>CDockingManager::AlignAutoHidePane  
 Cambia el tamaño de un panel acoplable en modo de ocultación automática para que toma todo el ancho o alto del área de cliente del marco rodeado por acoplar sitios.  
  
```  
void AlignAutoHidePane(
    CPaneDivider* pDefaultSlider,  
    BOOL bIsVisible = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDefaultSlider`  
 El panel de control deslizante de acoplamiento.  
  
 [in] `bIsVisible`  
 `TRUE`Si el panel de acoplamiento está visible; `FALSE` en caso contrario.  
  
##  <a name="autohidepane"></a>CDockingManager::AutoHidePane  
 Crea una barra de herramientas Ocultar automáticamente.  
  
```  
CMFCAutoHideToolBar* AutoHidePane(
    CDockablePane* pBar,  
    CMFCAutoHideToolBar* pCurrAutoHideToolBar = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Un puntero a la barra de panel.  
  
 [in] `pCurrAutoHideToolBar`  
 Un puntero a una barra de herramientas de ocultación automática.  
  
### <a name="return-value"></a>Valor devuelto  
 `NULL`Si el auto oculta la barra de herramientas no se ha creado; en caso contrario, un puntero a la nueva barra de herramientas.  
  
##  <a name="bringbarstotop"></a>CDockingManager::BringBarsToTop  
 Hace que las barras acopladas que tienen la alineación especificada en la parte superior.  
  
```  
void BringBarsToTop(
    DWORD dwAlignment = 0,  
    BOOL bExcludeDockedBars = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwAlignment`  
 La alineación de las barras de acoplamiento que se ponen a la parte superior de otras ventanas.  
  
 [in] `bExcludeDockedBars`  
 `TRUE`Para excluir las barras acopladas ante hacia arriba. en caso contrario, `FALSE`.  
  
##  <a name="buildpanesmenu"></a>CDockingManager::BuildPanesMenu  
 Agrega nombres de paneles de acoplamiento y barras de herramientas a un menú.  
  
```  
void BuildPanesMenu(
    CMenu& menu,  
    BOOL bToolbarsOnly);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `menu`  
 Un menú para agregar los nombres de los paneles de acoplamiento y barras de herramientas.  
  
 [in] `bToolbarsOnly`  
 `TRUE`Para agregar solo los nombres de barra de herramientas en el menú; `FALSE` en caso contrario.  
  
##  <a name="calcexpecteddockedrect"></a>CDockingManager::CalcExpectedDockedRect  
 Calcula el rectángulo esperado de una ventana acoplada.  
  
```  
void CalcExpectedDockedRect(
    CWnd* pWnd,  
    CPoint ptMouse,  
    CRect& rectResult,  
    BOOL& bDrawTab,  
    CDockablePane** ppTargetBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Un puntero a la ventana se acoplará.  
  
 [in] `ptMouse`  
 La ubicación del mouse.  
  
 [out] `rectResult`  
 El rectángulo calculado.  
  
 [in] `bDrawTab`  
 `TRUE`para dibujar una ficha; en caso contrario, `FALSE`.  
  
 [out] `ppTargetBar`  
 Un puntero a un puntero al panel de destino.  
  
### <a name="remarks"></a>Comentarios  
 Este método calcula el rectángulo que podría ocupar una ventana si un usuario arrastra la ventana para el punto especificado por `ptMouse` y se acoplan de no existe.  
  
##  <a name="create"></a>CDockingManager::Create  
 Crea un administrador de acoplamiento.  
  
```  
BOOL Create(CFrameWnd* pParentWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pParentWnd`  
 Un puntero al marco principal del Administrador de acoplamiento. Este valor no debe ser `NULL`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`siempre.  
  
##  <a name="determinepaneandstatus"></a>CDockingManager::DeterminePaneAndStatus  
 Determina el panel que contiene un punto determinado y su estado de acoplamiento.  
  
```  
virtual AFX_CS_STATUS DeterminePaneAndStatus(
    CPoint pt,  
    int nSensitivity,  
    DWORD dwEnabledAlignment,  
    CBasePane** ppTargetBar,  
    const CBasePane* pBarToIgnore,  
    const CBasePane* pBarToDock);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pt`  
 La ubicación del panel para comprobar.  
  
 [in] `nSensitivity`  
 El valor para aumentar el rectángulo de la ventana de cada panel comprobado. Un panel satisface los criterios de búsqueda si el punto especificado está en esta región mayor.  
  
 [in] `dwEnabledAlignment`  
 La alineación del panel de acoplamiento.  
  
 [out] `ppTargetBar`  
 Un puntero a un puntero al panel de destino.  
  
 [in] `pBarToIgnore`  
 El panel que omite el método.  
  
 [in] `pBarToDock`  
 El panel que está acoplado.  
  
### <a name="return-value"></a>Valor devuelto  
 El estado de acoplamiento.  
  
### <a name="remarks"></a>Comentarios  
 El estado de acoplamiento puede ser uno de los valores siguientes:  
  
|Valor AFX_CS_STATUS|Significado|  
|---------------------------|-------------|  
|CS_NOTHING|El puntero no es de un sitio de vinculación. Por tanto, mantenga el panel flotante.|  
|CS_DOCK_IMMEDIATELY|El puntero está sobre el sitio de vinculación en el modo inmediato (estilo DT_IMMEDIATE está habilitada), por lo que el panel se debe acoplar inmediatamente.|  
|CS_DELAY_DOCK|El puntero está sobre un sitio de vinculación que es otro panel acoplable o un borde del marco principal.|  
|CS_DELAY_DOCK_TO_TAB|El puntero está sobre un sitio de vinculación que hace que el panel acoplada en una ventana con pestañas. Esto se produce cuando el mouse está sobre un título de otro panel acoplable o sobre un área de la pestaña de un panel con fichas.|  
  
##  <a name="disablerestoredockstate"></a>CDockingManager::DisableRestoreDockState  
 Habilita o deshabilita la carga de diseño de acoplamiento del registro.  
  
```  
void DisableRestoreDockState(BOOL bDisable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bDisable`  
 `TRUE`Para deshabilitar la carga de diseño de acoplamiento del registro; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método cuando se debe conservar el diseño actual de las barras de herramientas y los paneles de acoplamiento cuando se carga el estado de la aplicación.  
  
##  <a name="dockpane"></a>CDockingManager::DockPane  
 Acopla un panel a otro panel o una ventana de marco.  
  
```  
void DockPane(
    CBasePane* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Un puntero a una barra de panel para acoplar a.  
  
 [in] `nDockBarID`  
 El identificador de la barra para acoplar.  
  
 [in] `lpRect`  
 El rectángulo de destino.  
  
##  <a name="dockpaneleftof"></a>CDockingManager::DockPaneLeftOf  
 Acopla un panel a la izquierda de otro panel.  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBarToDock,  
    CPane* pTargetBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBarToDock`  
 Un puntero al panel quede acoplado a la izquierda del `pTargetBar`.  
  
 [in] `pTargetBar`  
 Un puntero al panel de destino.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se acopla correctamente; en caso contrario, `FALSE`.  
  
##  <a name="enableautohidepanes"></a>CDockingManager::EnableAutoHidePanes  
 Permite al marco principal de acoplamiento del panel, crea un panel de acoplamiento y lo agrega a la lista de barras de control.  
  
```  
BOOL EnableAutoHidePanes(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwStyle`  
 La alineación de acoplamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel de acoplamiento se creó correctamente; `FALSE` en caso contrario.  
  
##  <a name="enabledocking"></a>CDockingManager::EnableDocking  
 Crea un panel de acoplamiento y permite al marco principal de acoplamiento del panel.  
  
```  
BOOL EnableDocking(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwStyle`  
 La alineación de acoplamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel de acoplamiento se creó correctamente; `FALSE` en caso contrario.  
  
##  <a name="enabledocksitemenu"></a>CDockingManager::EnableDockSiteMenu  
 Muestra un botón que abre un menú emergente en los títulos de todos los paneles de acoplamiento.  
  
```  
static void EnableDockSiteMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para habilitar el menú de sitio acoplar; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El menú de sitio acoplar muestra las siguientes opciones para cambiar el estado de acoplamiento del panel:  
  
- `Floating`-Desplaza un panel  
  
- `Docking`-Acopla un panel en el marco principal en la ubicación donde última se acopla el panel  
  
- `AutoHide`-Activa el panel en modo de ocultación automática  
  
- `Hide`-Oculta un panel  
  
 De forma predeterminada, no se muestra este menú.  
  
##  <a name="enablepanecontextmenu"></a>CDockingManager::EnablePaneContextMenu  
 Indica la biblioteca que se va a mostrar un menú contextual especial que tiene una lista de paneles de acoplamiento y barras de herramientas de aplicación cuando el usuario hace clic en el botón secundario del mouse y la biblioteca está procesando el mensaje WM_CONTEXTMENU.  
  
```  
void EnablePaneContextMenu(
    BOOL bEnable,  
    UINT uiCustomizeCmd,  
    const CString& strCustomizeText,  
    BOOL bToolbarsOnly = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 Si `TRUE`, activa la compatibilidad con menú contextual automática; la biblioteca si `FALSE` la biblioteca desactiva la compatibilidad con menú contextual automática.  
  
 [in] `uiCustomizeCmd`  
 Un identificador de comando para la **personalizar** elemento en el menú.  
  
 [in] `strCustomizeText`  
 El texto de la **personalizar** elemento.  
  
 [in] `bToolbarsOnly`  
 Si `TRUE`, el menú muestra solo una lista de las barras de herramientas de aplicación; si `FALSE`, la biblioteca agrega paneles de acoplamiento de la aplicación a esta lista.  
  
##  <a name="finddocksite"></a>CDockingManager::FindDockSite  
 Recupera la barra de panel que está en la posición especificada y que tiene la alineación especificadas.  
  
```  
virtual CDockSite* FindDockSite(
    DWORD dwAlignment,  
    BOOL bOuter);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwAlignment`  
 La alineación de la barra de panel.  
  
 [in] `bOuter`  
 Si `TRUE`, recuperar la barra en la posición principal en la lista de barras de control. Recuperar en caso contrario, la barra en la posición final de la lista de barras de control.  
  
### <a name="return-value"></a>Valor devuelto  
 El panel acoplable que tiene la alineación especificada; `NULL` en caso contrario.  
  
##  <a name="findpanebyid"></a>CDockingManager::FindPaneByID  
 Busca un panel con el identificador del control especificado.  
  
```  
virtual CBasePane* FindPaneByID(
    UINT uBarID,  
    BOOL bSearchMiniFrames = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uBarID`  
 Especifica el identificador de control del panel para buscar.  
  
 [in] `bSearchMiniFrames`  
 `TRUE`para incluir todos los paneles flotantes en la búsqueda. `FALSE`para incluir solo los paneles acoplados.  
  
### <a name="return-value"></a>Valor devuelto  
 El [CBasePane](../../mfc/reference/cbasepane-class.md) objeto que tiene el identificador del control especificado, o `NULL` si no se encuentra el panel especificado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="finddocksitebypane"></a>CDockingManager::FindDockSiteByPane  
 Devuelve la barra de panel que tiene el identificador del panel de barra de destino.  
  
```  
virtual CDockSite* FindDockSiteByPane(CPane* pTargetBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pTargetBar`  
 Un puntero al panel de barra de destino.  
  
### <a name="return-value"></a>Valor devuelto  
 La barra de panel que tiene el identificador del panel de barra de destino; `NULL` si no existe ningún como barra panel.  
  
##  <a name="fixupvirtualrects"></a>CDockingManager::FixupVirtualRects  
 Confirma todas las posiciones de la barra de herramientas actual a los rectángulos virtuales.  
  
```  
virtual void FixupVirtualRects();
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando el usuario comienza a arrastrar una barra de herramientas, la aplicación le recuerda a su posición original en el *rectángulo virtual*. Cuando el usuario mueve una barra de herramientas a través de su sitio de vinculación, la barra de herramientas puede cambiar otras barras de herramientas. Las posiciones originales de las barras de herramientas se almacenan en los rectángulos virtuales correspondientes.  
  
##  <a name="framefrompoint"></a>CDockingManager::FrameFromPoint  
 Devuelve el marco que contiene el punto especificado.  
  
```  
virtual CPaneFrameWnd* FrameFromPoint(
    CPoint pt,  
    CPaneFrameWnd* pFrameToExclude,  
    BOOL bFloatMultiOnly) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pt`  
 Especifica el punto, en coordenadas de pantalla, para comprobar.  
  
 [in] `pFrameToExclude`  
 Un puntero a un marco para excluir.  
  
 [in] `bFloatMultiOnly`  
 `TRUE`Para excluir las tramas que no sean instancias de `CMultiPaneFrameWnd`; `FALSE` en caso contrario.  
  
### <a name="return-value"></a>Valor devuelto  
 El marco que contiene el punto especificado; `NULL` en caso contrario.  
  
##  <a name="getclientareabounds"></a>CDockingManager::GetClientAreaBounds  
 Obtiene el rectángulo que contiene los límites del área de cliente.  
  
```  
CRect GetClientAreaBounds() const;

void GetClientAreaBounds(CRect& rcClient);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `rcClient`  
 Una referencia al rectángulo que contiene los límites del área de cliente.  
  
### <a name="return-value"></a>Valor devuelto  
 El rectángulo que contiene los límites del área de cliente.  
  
##  <a name="getdockingmode"></a>CDockingManager::GetDockingMode  
 Devuelve el modo de acoplamiento actual.  
  
```  
static AFX_DOCK_TYPE GetDockingMode();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de enumerador que representa el modo de acoplamiento actual. Puede ser uno de los siguientes valores:  
  
- `DT_STANDARD`  
  
- `DT_IMMEDIATE`  
  
- `DT_SMART`  
  
### <a name="remarks"></a>Comentarios  
 Para establecer el modo de acoplamiento, llame a [CDockingManager::SetDockingMode](#setdockingmode).  
  
##  <a name="getdocksiteframewnd"></a>CDockingManager::GetDockSiteFrameWnd  
 Obtiene un puntero al marco de ventana primaria.  
  
```  
CFrameWnd* GetDockSiteFrameWnd() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al marco de ventana primaria.  
  
##  <a name="getenabledautohidealignment"></a>CDockingManager::GetEnabledAutoHideAlignment  
 Devuelve la alineación de los paneles habilitada.  
  
```  
DWORD GetEnabledAutoHideAlignment() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una combinación bit a bit de `CBRS_ALIGN_` marcas, o 0 si no están habilitados los paneles de ocultación automática. Para obtener más información, consulte [CFrameWnd:: EnableDocking](../../mfc/reference/cframewnd-class.md#enabledocking).  
  
### <a name="remarks"></a>Comentarios  
 El método devuelve la alineación habilitada para ocultar automáticamente las barras de control. Para habilitar las barras Ocultar automáticamente, llame a [CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes).  
  
##  <a name="getminiframes"></a>CDockingManager::GetMiniFrames  
 Obtiene una lista de miniframes.  
  
```  
const CObList& GetMiniFrames() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una lista de miniframes que contienen las barras de control que pertenecen al administrador de acoplamiento.  
  
##  <a name="getouteredgebounds"></a>CDockingManager::GetOuterEdgeBounds  
 Obtiene un rectángulo que contiene los bordes exteriores del marco.  
  
```  
CRect GetOuterEdgeBounds() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un rectángulo que contiene los bordes exteriores del marco.  
  
##  <a name="getpanelist"></a>CDockingManager::GetPaneList  
 Devuelve una lista de paneles que pertenecen al administrador de acoplamiento. Esto incluye todos los paneles flotantes.  
  
```  
void GetPaneList(
    CObList& lstBars,  
    BOOL bIncludeAutohide = FALSE,  
    CRuntimeClass* pRTCFilter = NULL,  
    BOOL bIncludeTabs = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in, out] `lstBars`  
 Contiene todos los paneles del Administrador de acoplamiento actual.  
  
 [in] `bIncludeAutohide`  
 `TRUE`para incluir los paneles que se encuentran en modo de ocultación automática; en caso contrario, `FALSE`.  
  
 [in] `pRTCFilter`  
 Si no `NULL`, la lista devuelta contiene paneles sólo de la clase en tiempo de ejecución especificado.  
  
 [in] `bIncludeTabs`  
 `TRUE`para incluir pestañas; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si hay cualquier paneles con pestañas en el Administrador de acoplamiento, el método devuelve punteros a [CBaseTabbedPane (clase)](../../mfc/reference/cbasetabbedpane-class.md) objetos y se deben enumerar explícitamente las pestañas.  
  
 Use `pRTCFilter` para obtener una clase determinada de paneles. Por ejemplo, puede obtener solo las barras de herramientas al establecer este valor correctamente.  
  
##  <a name="getsmartdockingmanager"></a>CDockingManager::GetSmartDockingManager  
 Recupera un puntero al administrador de acoplamiento inteligente.  
  
```  
CSmartDockingManager* GetSmartDockingManager();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la [Administrador de acoplamiento inteligente](http://msdn.microsoft.com/en-us/f537a1a6-fb9e-41d7-952f-0f25d5ee7534).  
  
##  <a name="getsmartdockingmanagerpermanent"></a>CDockingManager::GetSmartDockingManagerPermanent  
 Recupera un puntero al administrador de acoplamiento inteligente.  
  
```  
CSmartDockingManager* GetSmartDockingManagerPermanent() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al administrador de acoplamiento inteligente.  
  
##  <a name="getsmartdockingparams"></a>CDockingManager::GetSmartDockingParams  
 Devuelve los parámetros de acoplamiento inteligentes para el Administrador de acoplamiento.  
  
```  
static CSmartDockingInfo& GetSmartDockingParams();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La clase que contiene los parámetros de acoplamiento inteligentes para el Administrador de acoplamiento actual. Para obtener más información, consulte [CSmartDockingInfo clase](../../mfc/reference/csmartdockinginfo-class.md).  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="hideautohidepanes"></a>CDockingManager::HideAutoHidePanes  
 Oculta un panel que se encuentra en modo de ocultación automática.  
  
```  
void HideAutoHidePanes(
    CDockablePane* pBarToExclude = NULL,  
    BOOL bImmediately = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBarToExclude`  
 Un puntero a una barra que se excluirán ocultar.  
  
 [in] `bImmediately`  
 `TRUE`Para ocultar el panel inmediatamente; `FALSE` para ocultar el panel con el efecto de ocultar automáticamente.  
  
##  <a name="insertdocksite"></a>CDockingManager::InsertDockSite  
 Crea un panel de acoplamiento y lo inserta en la lista de barras de control.  
  
```  
BOOL InsertDockSite(
    const AFX_DOCKSITE_INFO& info,  
    DWORD dwAlignToInsertAfter,  
    CDockSite** ppDockBar = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `info`  
 Una estructura que contiene la información de alineación acerca del panel de acoplamiento.  
  
 [in] `dwAlignToInsertAfter`  
 Alineación del panel de acoplamiento.  
  
 [out] `ppDockBar`  
 Un puntero a un puntero a un panel de acoplamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel de acoplamiento se creó correctamente; `FALSE` en caso contrario.  
  
##  <a name="insertpane"></a>CDockingManager::InsertPane  
 Inserta un panel de control en la lista de barras de control.  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pControlBar`  
 Un puntero a un panel de control.  
  
 [in] `pTarget`  
 Un puntero a un panel de destino.  
  
 [in] `bAfter`  
 `TRUE`Para insertar el panel después de la posición del panel de destino; `FALSE` en caso contrario.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel de control se agregó correctamente a la lista de barras de control; `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve false si el panel de control ya está en la lista de barras de control o si el panel de destino no existe en la lista de barras de control.  
  
##  <a name="isdocksitemenu"></a>CDockingManager::IsDockSiteMenu  
 Especifica si se muestra un menú emergente en los títulos de todos los paneles.  
  
```  
static BOOL IsDockSiteMenu();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se muestra un menú de sitio de acoplamiento en los títulos de todos los paneles de acoplamiento; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Puede habilitar el menú de sitio acoplar mediante una llamada a [CDockingManager::EnableDockSiteMenu](#enabledocksitemenu).  
  
##  <a name="isinadjustlayout"></a>CDockingManager::IsInAdjustLayout  
 Determina si se ajustan los diseños de todos los paneles.  
  
```  
BOOL IsInAdjustLayout() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se ajustan los diseños de todos los paneles; `FALSE` en caso contrario.  
  
##  <a name="isolecontainermode"></a>CDockingManager::IsOLEContainerMode  
 Especifica si el Administrador de acoplamiento está en modo de contenedor OLE.  
  
```  
BOOL IsOLEContainerMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el Administrador de acoplamiento está en modo de contenedor OLE; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 En el modo de contenedor OLE, se ocultan todos los paneles de acoplamiento y barras de herramientas de aplicación. Los paneles se ocultan también en este modo si ha configurado [CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode) a `TRUE`.  
  
##  <a name="ispointneardocksite"></a>CDockingManager::IsPointNearDockSite  
 Determina si un punto especificado se encuentra cerca del sitio de vinculación.  
  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 El punto especificado.  
  
 [out] `dwBarAlignment`  
 Especifica cuál es el punto de cerca de los bordes. Los valores posibles son `CBRS_ALIGN_LEFT`, `CBRS_ALIGN_RIGHT`, `CBRS_ALIGN_TOP` y `CBRS_ALIGN_BOTTOM`.  
  
 [out] `bOuterEdge`  
 `TRUE`Si el punto está cerca del borde exterior del sitio de vinculación; `FALSE` en caso contrario.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el punto está cerca del sitio de vinculación; en caso contrario, `FALSE`.  
  
##  <a name="isprintpreviewvalid"></a>CDockingManager::IsPrintPreviewValid  
 Determina si se establece el modo de vista previa de impresión.  
  
```  
BOOL IsPrintPreviewValid() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se establece el modo de vista previa de impresión; `FALSE` en caso contrario.  
  
##  <a name="loadstate"></a>CDockingManager::LoadState  
 Carga el estado del Administrador de acoplamiento desde el registro.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Nombre del perfil.  
  
 [in] `uiID`  
 El identificador del Administrador de acoplamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el estado del Administrador de acoplamiento se cargó correctamente; en caso contrario, `FALSE`.  
  
##  <a name="lockupdate"></a>CDockingManager::LockUpdate  
 Bloquea la ventana especificada.  
  
```  
void LockUpdate(BOOL bLock);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bLock`  
 `TRUE`Si la ventana está bloqueada; `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Cuando una ventana está bloqueada, no se puede mover y no se vuelve a dibujarse.  
  
##  <a name="m_bhidedockingbarsincontainermode"></a>CDockingManager::m_bHideDockingBarsInContainerMode  
 Especifica si el Administrador de acoplamiento oculta paneles en modo de contenedor OLE.  
  
```  
AFX_IMPORT_DATA static BOOL m_bHideDockingBarsInContainerMode;  
```  
  
### <a name="remarks"></a>Comentarios  
 Establezca este valor en `FALSE` si desea mantener todos los paneles acoplados al marco principal visible cuando la aplicación está en modo de contenedor OLE. De forma predeterminada, este valor es `TRUE`.  
  
##  <a name="m_dockmodeglobal"></a>CDockingManager::m_dockModeGlobal  
 Especifica el modo de acoplamiento global.  
  
```  
AFX_IMPORT_DATA static AFX_DOCK_TYPE m_dockModeGlobal;  
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, cada panel acoplable utiliza este modo de acoplamiento. Para obtener más información acerca de los valores que este campo se puede establecer en, consulte [cbasepane:: Getdockingmode](../../mfc/reference/cbasepane-class.md#getdockingmode).  
  
##  <a name="m_ndocksensitivity"></a>CDockingManager::m_nDockSensitivity  
 Especifica la distinción de acoplamiento.  
  
```  
AFX_IMPORT_DATA static int m_nDockSensitivity;  
```  
  
### <a name="remarks"></a>Comentarios  
 La confidencialidad de acoplamiento define la distancia flotante panel puede tratar un panel acoplable, sitio de acoplamiento u otro panel antes de que el marco de trabajo cambia su estado acoplado.  
  
##  <a name="m_ntimeoutbeforedockingbardock"></a>CDockingManager::m_nTimeOutBeforeDockingBarDock  
 Especifica el tiempo, en milisegundos, antes de que se acopla un panel acoplable en el modo de acoplamiento inmediato.  
  
```  
static UINT m_nTimeOutBeforeDockingBarDock;  
```  
  
### <a name="remarks"></a>Comentarios  
 Antes de que se acopla un panel, el marco de trabajo espera a que el período de tiempo especificado. Esto impide que el panel se acopla accidentalmente a una ubicación mientras el usuario todavía está arrastrando.  
  
##  <a name="m_ntimeoutbeforetoolbardock"></a>CDockingManager::m_nTimeOutBeforeToolBarDock  
 Especifica el tiempo, en milisegundos, antes de una barra de herramientas está acoplada a la ventana de marco principal.  
  
```  
static UINT m_nTimeOutBeforeToolBarDock;  
```  
  
### <a name="remarks"></a>Comentarios  
 Antes de una barra de herramientas está acoplado, el marco de trabajo espera a que el período de tiempo especificado. Esto impide que accidentalmente se acopla a una ubicación mientras el usuario todavía está arrastrando la barra de herramientas.  
  
##  <a name="onactivateframe"></a>CDockingManager::OnActivateFrame  
 Lo llama el marco de trabajo cuando la ventana de marco estará activa o se desactiva.  
  
```  
virtual void OnActivateFrame(BOOL bActivate);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bActivate`  
 Si `TRUE`, estará activa la ventana de marco; si `FALSE`, se desactiva la ventana de marco.  
  
##  <a name="onclosepopupmenu"></a>CDockingManager::OnClosePopupMenu  
 Lo llama el marco cuando un menú emergente activo procesa un mensaje WM_DESTROY.  
  
```  
void OnClosePopupMenu();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo envía un mensaje WM_DESTROY cuando está a punto de cerrar la ventana principal actual. Invalide este método para controlar las notificaciones de `CMFCPopupMenu` objetos que pertenecen a la ventana de marco cuando un `CMFCPopupMenu` objeto procesos un `WM_DESTROY` mensaje.  
  
##  <a name="onmoveminiframe"></a>CDockingManager::OnMoveMiniFrame  
 Lo llama el marco para mover una ventana de marco reducido.  
  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pFrame`  
 Un puntero a una ventana de marco reducido.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método tiene éxito; en caso contrario, `FALSE`.  
  
##  <a name="onpanecontextmenu"></a>CDockingManager::OnPaneContextMenu  
 Lo llama el marco cuando compila un menú con una lista de paneles.  
  
```  
void OnPaneContextMenu(CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 Especifica la ubicación del menú.  
  
##  <a name="panefrompoint"></a>CDockingManager::PaneFromPoint  
 Devuelve el panel que contiene el punto especificado.  
  
```  
virtual CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    bool bExactBar = false,  
    CRuntimeClass* pRTCBarType = NULL,  
    BOOL bCheckVisibility = FALSE,  
    const CBasePane* pBarToIgnore = NULL) const;  
  
virtual CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    DWORD& dwAlignment,  
    CRuntimeClass* pRTCBarType = NULL,  
    const CBasePane* pBarToIgnore = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 Especifica el punto, en coordenadas de pantalla, para comprobar.  
  
 [in] `nSensitivity`  
 El valor para aumentar el rectángulo de la ventana de cada panel comprobado. Un panel satisface los criterios de búsqueda si el punto especificado está en esta región aumentada.  
  
 [in] `bExactBar`  
 `TRUE`para pasar por alto la `nSensitivity` parámetro; en caso contrario, `FALSE`.  
  
 [in] `pRTCBarType`  
 Si no `NULL`, el método busca únicamente los paneles del tipo especificado.  
  
 [in] `bCheckVisibility`  
 `TRUE`Para comprobar solo paneles visibles; en caso contrario, `FALSE`.  
  
 [out] `dwAlignment`  
 Si un panel se encuentra en el punto especificado, este parámetro contiene el lado del panel que era más cercano al punto especificado. Para obtener más información, vea la sección Comentarios.  
  
 [in] `pBarToIgnore`  
 Si no `NULL`, el método omite paneles especificados por este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 El [CBasePane](../../mfc/reference/cbasepane-class.md)-objeto derivado que contiene el punto especificado, o `NULL` si no se encontró ningún panel.  
  
### <a name="remarks"></a>Comentarios  
 Cuando la función devuelve y se ha encontrado un panel, `dwAlignment` contiene la alineación del punto especificado. Por ejemplo, si el punto es más cercano a la parte superior del panel, `dwAlignment` está establecido en `CBRS_ALIGN_TOP`.  
  
##  <a name="processpanecontextmenucommand"></a>CDockingManager::ProcessPaneContextMenuCommand  
 Lo llama el marco de trabajo para seleccionar o para desactivar una casilla de verificación para el comando especificado y vuelva a calcular el diseño de un panel se muestra.  
  
```  
BOOL ProcessPaneContextMenuCommand(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 El identificador de una barra de controles en el menú.  
  
 [in] `nCode`  
 El código de notificación de comando.  
  
 [in] `pExtra`  
 Un puntero a void que es convertir en un puntero a `CCmdUI` si `nCode` es CN_UPDATE_COMMAND_UI.  
  
 [in] `pHandlerInfo`  
 Un puntero a una estructura de información. Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si `pEXtra` no es NULL y `nCode` es igual a CN_UPDATE_COMMAND_UI, o si hay una barra de controles con los valores especificados `nID`.  
  
##  <a name="recalclayout"></a>CDockingManager::RecalcLayout  
 Vuelve a calcular el diseño interno de los controles que se encuentra en la lista de controles.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bNotify`  
 Este parámetro no se utiliza.  
  
##  <a name="releaseemptypanecontainers"></a>CDockingManager::ReleaseEmptyPaneContainers  
 Libera los contenedores de panel vacía.  
  
```  
void ReleaseEmptyPaneContainers();
```  
  
##  <a name="removehiddenmditabbedbar"></a>CDockingManager::RemoveHiddenMDITabbedBar  
 Quita oculta la barra panel especificado.  
  
```  
void RemoveHiddenMDITabbedBar(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Un puntero a una barra de panel para quitar.  
  
##  <a name="removeminiframe"></a>CDockingManager::RemoveMiniFrame  
 Quita un período especificado de la lista de fotogramas minivolcados.  
  
```  
virtual BOOL RemoveMiniFrame(CPaneFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Un puntero a un marco para quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se quita el período especificado; `FALSE` en caso contrario.  
  
##  <a name="removepanefromdockmanager"></a>CDockingManager::RemovePaneFromDockManager  
 Anula el registro de un panel y lo quita de la lista en el Administrador de acoplamiento.  
  
```  
void RemovePaneFromDockManager(
    CBasePane* pWnd,  
    BOOL bDestroy,  
    BOOL bAdjustLayout,  
    BOOL bAutoHide = FALSE,  
    CBasePane* pBarReplacement = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Un puntero a un panel que se va a quitar.  
  
 [in] `bDestroy`  
 Si `TRUE`, se destruye el panel quitado.  
  
 [in] `bAdjustLayout`  
 Si `TRUE`, ajustar el diseño de acoplamiento inmediatamente.  
  
 [in] `bAutoHide`  
 Si `TRUE`, el panel se quita de la lista de barras de ocultación automática. Si `FALSE`, el panel se quita de la lista de paneles regulares.  
  
 [in] `pBarReplacement`  
 Un puntero a un panel que reemplaza el panel quitado.  
  
##  <a name="replacepane"></a>CDockingManager::ReplacePane  
 Reemplaza un panel con otro.  
  
```  
BOOL ReplacePane(
    CDockablePane* pOriginalBar,  
    CDockablePane* pNewBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pOriginalBar`  
 Un puntero al panel original.  
  
 [in] `pNewBar`  
 Un puntero al panel que reemplaza el panel original.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se ha reemplazado correctamente; `FALSE` en caso contrario.  
  
##  <a name="resortminiframesforzorder"></a>CDockingManager::ResortMiniFramesForZOrder  
 Vuelve a ordenar los marcos en la lista de fotogramas minivolcados.  
  
```  
void ResortMiniFramesForZOrder();
```  
  
##  <a name="savestate"></a>CDockingManager::SaveState  
 Guarda el estado del Administrador de acoplamiento en el registro.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Una ruta de acceso a una clave del registro.  
  
 [in] `uiID`  
 En el identificador de jefe acoplamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el estado se guardó correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Guardar el estado del Administrador de acoplamiento en el registro implica guardar los Estados de las barras de control, los Estados de las barras Ocultar automáticamente y los Estados de los marcos minivolcados presentes en el Administrador de acoplamiento.  
  
##  <a name="sendmessagetominiframes"></a>CDockingManager::SendMessageToMiniFrames  
 Envía el mensaje especificado a todos los marcos minivolcados.  
  
```  
BOOL SendMessageToMiniFrames(
    UINT uMessage,  
    WPARAM wParam = 0,  
    LPARAM lParam = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uMessage`  
 Que se envíe el mensaje.  
  
 [in] `wParam`  
 Información dependiente del mensaje adicional.  
  
 [in] `lParam`  
 Información dependiente del mensaje adicional.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`siempre.  
  
##  <a name="serialize"></a>CDockingManager::Serialize  
 Escribe el Administrador de acoplamiento en un archivo.  
  
```  
void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `ar`  
 Una referencia a un objeto de almacenamiento.  
  
### <a name="remarks"></a>Comentarios  
 Escribir el Administrador de acoplamiento en un archivo consiste en determinar el número de barras de controles y controles deslizantes de acoplamiento y escribir las barras de control, los marcos minivolcados, las barras Ocultar automáticamente y las barras MDI con fichas en el archivo.  
  
##  <a name="setautohidezorder"></a>CDockingManager::SetAutohideZOrder  
 Establece el tamaño, ancho y alto de las barras de control y el panel especificado.  
  
```  
void SetAutohideZOrder(CDockablePane* pAHDockingBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pAHDockingBar`  
 Un puntero a un panel acoplable.  
  
##  <a name="setdockingmode"></a>CDockingManager::SetDockingMode  
 Establece el modo de acoplamiento.  
  
```  
static void SetDockingMode(
    AFX_DOCK_TYPE dockMode,  
    AFX_SMARTDOCK_THEME theme = AFX_SDT_DEFAULT);
```  
  
### <a name="parameters"></a>Parámetros  
 `dockMode`  
 Especifica el nuevo modo de acoplamiento. Para obtener más información, vea la sección Comentarios.  
  
 `theme`  
 Especifica el tema que se usará para los marcadores de acoplamiento inteligente. Puede ser uno de los valores enumerados siguientes: AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método estático para establecer el modo de acoplamiento.  
  
 `dockMode`puede ser uno de los siguientes valores:  
  
- `DT_STANDARD`-Estándar de acoplamiento de modo tal como se implementa en Visual Studio .NET 2003. Los paneles se arrastran sin un contexto de arrastrar.  
  
- `DT_IMMEDIATE`-Modo de acoplamiento inmediato como se implementa en Microsoft Visio. Los paneles se arrastran con un contexto de arrastrar, pero no se muestran marcadores.  
  
- `DT_SMART`-Modo de acoplamiento de smart tal como se implementa en Visual Studio 2005. Los paneles se arrastran con un contexto de arrastrar y se muestran los marcadores inteligentes que muestran dónde se puede acoplar el panel.  
  
##  <a name="setdockstate"></a>CDockingManager::SetDockState  
 Establece el estado de acoplamiento de las barras de control, los marcos minivolcados y las barras Ocultar automáticamente.  
  
```  
virtual void SetDockState();
```  
  
##  <a name="setprintpreviewmode"></a>CDockingManager::SetPrintPreviewMode  
 Establece el modo de vista previa de impresión de las barras que se muestran en la vista previa de impresión.  
  
```  
void SetPrintPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bPreview`  
 `TRUE`Si se establece el modo de vista previa de impresión; `FALSE` en caso contrario.  
  
 [in] `pState`  
 Un puntero a un estado de vista previa. Este parámetro no se utiliza.  
  
##  <a name="setsmartdockingparams"></a>CDockingManager::SetSmartDockingParams  
 Establece los parámetros que definen el comportamiento de acoplamiento inteligente.  
  
```  
static void SetSmartDockingParams(CSmartDockingInfo& params);
```  
  
### <a name="parameters"></a>Parámetros  
 [in, out] `params`  
 Define los parámetros de acoplamiento inteligente.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método si desea personalizar el aspecto, el color o la forma de los marcadores de acoplamiento inteligentes.  
  
 Para usar la apariencia predeterminada de marcadores de acoplamiento inteligente, pase una instancia no inicializada de [CSmartDockingInfo clase](../../mfc/reference/csmartdockinginfo-class.md) a `params`.  
  
##  <a name="showdelayshowminiframes"></a>CDockingManager::ShowDelayShowMiniFrames  
 Muestra u oculta las ventanas de los marcos minivolcados.  
  
```  
void ShowDelayShowMiniFrames(BOOL bshow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bShow`  
 `TRUE`Para activar la ventana del marco se muestra; `FALSE to` ocultar la ventana del marco.  
  
##  <a name="showpanes"></a>CDockingManager::ShowPanes  
 Muestra u oculta los paneles de las barras de control y ocultar automáticamente.  
  
```  
virtual BOOL ShowPanes(BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bShow`  
 `TRUE`para mostrar los paneles; `FALSE to` ocultar los paneles.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre es `FALSE`.  
  
##  <a name="startsdocking"></a>CDockingManager::StartSDocking  
 Inicia el acoplamiento inteligente de la ventana especificada según la alineación del Administrador de acoplamiento inteligente.  
  
```  
void StartSDocking(CWnd* pDockingWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDockingWnd`  
 Un puntero a una ventana se acoplará.  
  
##  <a name="stopsdocking"></a>CDockingManager::StopSDocking  
 Se detiene inteligentes de acoplamiento.  
  
```  
void StopSDocking();
```  
  
##  <a name="getsmartdockingtheme"></a>CDockingManager::GetSmartDockingTheme  
 Un método estático que devuelve un tema que se usa para mostrar marcadores de acoplamiento inteligente.  
  
```  
static AFX_SMARTDOCK_THEME __stdcall GetSmartDockingTheme();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores enumerados siguientes: AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Clase CFrameWndEx](../../mfc/reference/cframewndex-class.md)   
 [Clase CDockablePane](../../mfc/reference/cdockablepane-class.md)   
 [CPaneFrameWnd (clase)](../../mfc/reference/cpaneframewnd-class.md)
