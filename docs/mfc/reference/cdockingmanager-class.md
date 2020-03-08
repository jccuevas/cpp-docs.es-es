---
title: Clase CDockingManager
ms.date: 11/04/2016
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
ms.openlocfilehash: 8709b3a4eb3f57a3d2700ad7aaed16df994245c5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883944"
---
# <a name="cdockingmanager-class"></a>Clase CDockingManager

Implementa la funcionalidad básica que controla el diseño de acoplamiento en una ventana de marco principal.

## <a name="syntax"></a>Sintaxis

```
class CDockingManager : public CObject
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDockingManager::AddDockSite](#adddocksite)|Crea un panel de acoplamiento y lo agrega a la lista de barras de control.|
|[CDockingManager::AddHiddenMDITabbedBar](#addhiddenmditabbedbar)|Agrega un identificador a un panel de barras a la lista de paneles de barra de pestañas MDI ocultos.|
|[CDockingManager::AddMiniFrame](#addminiframe)|Agrega un marco a la lista de fotogramas.|
|[CDockingManager::AddPane](#addpane)|Registra un panel con el administrador de acoplamiento.|
|[CDockingManager::AdjustDockingLayout](#adjustdockinglayout)|Vuelve a calcular y ajusta el diseño de todos los paneles en una ventana de marco.|
|[CDockingManager::AdjustPaneFrames](#adjustpaneframes)|Hace que el mensaje de WM_NCCALCSIZE se envíe a todos los paneles y `CPaneFrameWnd` ventanas.|
|[CDockingManager::AdjustRectToClientArea](#adjustrecttoclientarea)|Ajusta la alineación de un rectángulo.|
|[CDockingManager::AlignAutoHidePane](#alignautohidepane)|Cambia el tamaño de un panel acoplable en modo Ocultar automáticamente para que tome el ancho o el alto completo del área cliente del marco entre los sitios acoplados.|
|[CDockingManager::AutoHidePane](#autohidepane)|Crea una barra de herramientas ocultar automáticamente.|
|[CDockingManager::BringBarsToTop](#bringbarstotop)|Coloca en la parte superior las barras acopladas que tienen la alineación especificada.|
|[CDockingManager::BuildPanesMenu](#buildpanesmenu)|Agrega nombres de paneles y barras de herramientas de acoplamiento a un menú.|
|[CDockingManager::CalcExpectedDockedRect](#calcexpecteddockedrect)|Calcula el rectángulo esperado de una ventana acoplada.|
|[CDockingManager:: Create](#create)|Crea un administrador de acoplamiento.|
|[CDockingManager::D eterminePaneAndStatus](#determinepaneandstatus)|Determina el panel que contiene un punto determinado y su estado de acoplamiento.|
|[CDockingManager::D isableRestoreDockState](#disablerestoredockstate)|Habilita o deshabilita la carga del diseño de acoplamiento del registro.|
|[CDockingManager::D ockPane](#dockpane)|Acopla un panel a otro panel o a una ventana de marco.|
|[CDockingManager::D ockPaneLeftOf](#dockpaneleftof)|Acopla un panel a la izquierda de otro panel.|
|[CDockingManager::EnableAutoHidePanes](#enableautohidepanes)|Habilita el acoplamiento del panel al marco principal, crea un panel de acoplamiento y lo agrega a la lista de barras de control.|
|[CDockingManager:: EnableDocking](#enabledocking)|Crea un panel de acoplamiento y permite acoplar el panel en el marco principal.|
|[CDockingManager::EnableDockSiteMenu](#enabledocksitemenu)|Muestra un botón adicional que abre un menú emergente en los títulos de todos los paneles de acoplamiento.|
|[CDockingManager::EnablePaneContextMenu](#enablepanecontextmenu)|Indica a la biblioteca que muestre un menú contextual especial que tenga una lista de barras de herramientas de la aplicación y paneles de acoplamiento cuando el usuario haga clic con el botón secundario del mouse y la biblioteca esté procesando el mensaje de WM_CONTEXTMENU.|
|[CDockingManager::FindDockSite](#finddocksite)|Recupera el panel de barra que se encuentra en la posición especificada y que tiene la alineación especificada.|
|[CDockingManager::FindDockSiteByPane](#finddocksitebypane)|Devuelve el panel de barra que tiene el identificador del panel de la barra de destino.|
|[CDockingManager::FindPaneByID](#findpanebyid)|Busca un panel por el ID. de control especificado.|
|[CDockingManager::FixupVirtualRects](#fixupvirtualrects)|Confirma todas las posiciones de la barra de herramientas actual en rectángulos virtuales.|
|[CDockingManager::FrameFromPoint](#framefrompoint)|Devuelve el marco que contiene el punto especificado.|
|[CDockingManager::GetClientAreaBounds](#getclientareabounds)|Obtiene el rectángulo que contiene los límites del área cliente.|
|[CDockingManager::GetDockingMode](#getdockingmode)|Devuelve el modo de acoplamiento actual.|
|[CDockingManager::GetDockSiteFrameWnd](#getdocksiteframewnd)|Obtiene un puntero al marco de la ventana primaria.|
|[CDockingManager::GetEnabledAutoHideAlignment](#getenabledautohidealignment)|Devuelve la alineación habilitada de los paneles.|
|[CDockingManager::GetMiniFrames](#getminiframes)|Obtiene una lista de miniframes.|
|[CDockingManager::GetOuterEdgeBounds](#getouteredgebounds)|Obtiene un rectángulo que contiene los bordes exteriores del marco.|
|[CDockingManager::GetPaneList](#getpanelist)|Devuelve una lista de los paneles que pertenecen al administrador de acoplamiento. Esto incluye todos los paneles flotantes.|
|[CDockingManager::GetSmartDockingManager](#getsmartdockingmanager)|Recupera un puntero al administrador de acoplamiento inteligente.|
|[CDockingManager::GetSmartDockingManagerPermanent](#getsmartdockingmanagerpermanent)|Recupera un puntero al administrador de acoplamiento inteligente.|
|[CDockingManager::GetSmartDockingParams](#getsmartdockingparams)|Devuelve los parámetros de acoplamiento inteligente para el administrador de acoplamiento.|
|[CDockingManager::GetSmartDockingTheme](#getsmartdockingtheme)|Un método estático que devuelve un tema que se usa para mostrar los marcadores de acoplamiento inteligente.|
|[CDockingManager::HideAutoHidePanes](#hideautohidepanes)|Oculta un panel que está en modo de ocultación automáticamente.|
|[CDockingManager::InsertDockSite](#insertdocksite)|Crea un panel de acoplamiento y lo inserta en la lista de barras de control.|
|[CDockingManager::InsertPane](#insertpane)|Inserta un panel de control en la lista de barras de control.|
|[CDockingManager::IsDockSiteMenu](#isdocksitemenu)|Especifica si se muestra un menú emergente en los títulos de todos los paneles.|
|[CDockingManager::IsInAdjustLayout](#isinadjustlayout)|Determina si se ajustan los diseños de todos los paneles.|
|[CDockingManager::IsOLEContainerMode](#isolecontainermode)|Especifica si el administrador de acoplamiento está en modo de contenedor OLE.|
|[CDockingManager::IsPointNearDockSite](#ispointneardocksite)|Determina si un punto especificado está cerca del sitio de acoplamiento.|
|[CDockingManager::IsPrintPreviewValid](#isprintpreviewvalid)|Determina si el modo de vista previa de impresión está establecido.|
|[CDockingManager:: LoadState](#loadstate)|Carga el estado del administrador de acoplamiento desde el registro.|
|[CDockingManager::LockUpdate](#lockupdate)|Bloquea la ventana especificada.|
|[CDockingManager::OnActivateFrame](#onactivateframe)|Lo llama el marco de trabajo cuando la ventana de marco se activa o se desactiva.|
|[CDockingManager::OnClosePopupMenu](#onclosepopupmenu)|Lo llama el marco cuando un menú emergente activo procesa un mensaje WM_DESTROY.|
|[CDockingManager::OnMoveMiniFrame](#onmoveminiframe)|Lo llama el marco de trabajo para desplace una ventana de marco reducido.|
|[CDockingManager::OnPaneContextMenu](#onpanecontextmenu)|Lo llama el marco de trabajo cuando crea un menú que tiene una lista de paneles.|
|[CDockingManager::P aneFromPoint](#panefrompoint)|Devuelve el panel que contiene el punto especificado.|
|[CDockingManager::P rocessPaneContextMenuCommand](#processpanecontextmenucommand)|Lo llama el marco de trabajo para activar o desactivar una casilla para el comando especificado y volver a calcular el diseño de un panel mostrado.|
|[CDockingManager::RecalcLayout](#recalclayout)|Vuelve a calcular el diseño interno de los controles presentes en la lista de controles.|
|[CDockingManager::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)|Libera los contenedores de paneles vacíos.|
|[CDockingManager::RemoveHiddenMDITabbedBar](#removehiddenmditabbedbar)|Quita el panel de la barra oculta especificado.|
|[CDockingManager::RemoveMiniFrame](#removeminiframe)|Quita un marco especificado de la lista de fotogramas minis.|
|[CDockingManager::RemovePaneFromDockManager](#removepanefromdockmanager)|Anula el registro de un panel y lo quita de la lista en el administrador de acoplamiento.|
|[CDockingManager::ReplacePane](#replacepane)|Reemplaza un panel con otro.|
|[CDockingManager::ResortMiniFramesForZOrder](#resortminiframesforzorder)|Reordena los fotogramas de la lista de fotogramas.|
|[CDockingManager:: SaveState](#savestate)|Guarda el estado del administrador de acoplamiento en el registro.|
|[CDockingManager::SendMessageToMiniFrames](#sendmessagetominiframes)|Envía el mensaje especificado a todos los fotogramas.|
|[CDockingManager:: Serialize](#serialize)|Escribe el administrador de acoplamiento en un archivo. (Invalida [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)).|
|[CDockingManager::SetAutohideZOrder](#setautohidezorder)|Establece el tamaño, el ancho y el alto de las barras de control y el panel especificado.|
|[CDockingManager::SetDockingMode](#setdockingmode)|Establece el modo de acoplamiento.|
|[CDockingManager::SetDockState](#setdockstate)|Establece el estado de acoplamiento de las barras de control, los fotogramas y las barras de ocultación automáticamente.|
|[CDockingManager::SetPrintPreviewMode](#setprintpreviewmode)|Establece el modo de vista previa de impresión de las barras que se muestran en la vista previa de impresión.|
|[CDockingManager::SetSmartDockingParams](#setsmartdockingparams)|Establece los parámetros que definen el comportamiento de la función de acoplamiento inteligente.|
|[CDockingManager::ShowDelayShowMiniFrames](#showdelayshowminiframes)|Muestra u oculta las ventanas de los fotogramas.|
|[CDockingManager::ShowPanes](#showpanes)|Muestra u oculta los paneles del control y las barras de ocultación automáticamente.|
|[CDockingManager::StartSDocking](#startsdocking)|Inicia el acoplamiento inteligente de la ventana especificada según la alineación del administrador de acoplamiento inteligente.|
|[CDockingManager::StopSDocking](#stopsdocking)|Detiene el acoplamiento inteligente.|

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|[CDockingManager:: m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)|Especifica si el administrador de acoplamiento oculta los paneles en el modo de contenedor OLE.|
|[CDockingManager:: m_dockModeGlobal](#m_dockmodeglobal)|Especifica el modo de acoplamiento global.|
|[CDockingManager:: m_nDockSensitivity](#m_ndocksensitivity)|Especifica la sensibilidad de acoplamiento.|
|[CDockingManager:: m_nTimeOutBeforeDockingBarDock](#m_ntimeoutbeforedockingbardock)|Especifica el tiempo, en milisegundos, antes de que un panel acoplable se acople en el modo de acoplamiento inmediato.|
|[CDockingManager:: m_nTimeOutBeforeToolBarDock](#m_ntimeoutbeforetoolbardock)|Especifica el tiempo, en milisegundos, antes de que una barra de herramientas esté acoplada a la ventana de marco principal.|

## <a name="remarks"></a>Observaciones

La ventana de marco principal crea e inicializa esta clase automáticamente.

El objeto de administrador de acoplamiento contiene una lista de todos los paneles que se encuentran en el diseño de acoplamiento y también una lista de todas las ventanas de [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) que pertenecen a la ventana de marco principal.

La clase `CDockingManager` implementa algunos servicios que puede usar para buscar un panel o una ventana de `CPaneFrameWnd`. Normalmente no se llaman directamente a estos servicios porque se incluyen en el objeto de la ventana de marco principal. Para obtener más información, consulte [clase CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md).

## <a name="customization-tips"></a>Sugerencias de personalización

Las siguientes sugerencias se aplican a los objetos de `CDockingManager`:

- La [clase CDockingManager](../../mfc/reference/cdockingmanager-class.md) admite estos modos de acoplamiento:

  - `AFX_DOCK_TYPE::DT_IMMEDIATE`

  - `AFX_DOCK_TYPE::DT_STANDARD`

  - `AFX_DOCK_TYPE::DT_SMART`

  Estos modos de acoplamiento se definen mediante [CDockingManager:: m_dockModeGlobal](#m_dockmodeglobal) y se establecen mediante una llamada a [CDockingManager:: SetDockingMode](#setdockingmode).

- Si desea crear un panel que no sea flotante y que no se pueda cambiar de tamaño, llame al método [CDockingManager:: AddPane](#addpane) . Este método registra el panel con el administrador de acoplamiento, que es responsable del diseño del panel.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar varios métodos en la clase `CDockingManager` para configurar un objeto `CDockingManager`. En el ejemplo se muestra cómo mostrar un botón adicional que abre un menú emergente en los títulos de todos los paneles de acoplamiento y cómo establecer el modo de acoplamiento del objeto. Este fragmento de código forma parte del [ejemplo de demostración de Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#24](../../mfc/codesnippet/cpp/cdockingmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CDockingManager](../../mfc/reference/cdockingmanager-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxDockingManager. h

##  <a name="adddocksite"></a>CDockingManager::AddDockSite

Crea un panel de acoplamiento y lo agrega a la lista de barras de control.

```
BOOL AddDockSite(
    const AFX_DOCKSITE_INFO& info,
    CDockSite** ppDockBar = NULL);
```

### <a name="parameters"></a>Parámetros

*info*<br/>
de Referencia a una estructura de información que contiene la alineación del panel de acoplamiento.

*ppDockBar*<br/>
enuncia Un puntero a un puntero al nuevo panel de acoplamiento.

### <a name="return-value"></a>Valor devuelto

TRUE si el panel de acoplamiento se creó correctamente; De lo contrario, FALSE.

##  <a name="addhiddenmditabbedbar"></a>CDockingManager::AddHiddenMDITabbedBar

Agrega un identificador a un panel de barras a la lista de paneles de barra de pestañas MDI ocultos.

```
void AddHiddenMDITabbedBar(CDockablePane* pBar);
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
de Un puntero a un panel de barra

##  <a name="addpane"></a>CDockingManager::AddPane

Registra un panel con el administrador de acoplamiento.

```
BOOL AddPane(
    CBasePane* pWnd,
    BOOL bTail = TRUE,
    BOOL bAutoHide = FALSE,
    BOOL bInsertForOuterEdge = FALSE);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
[in, out] Especifica el panel que se va a agregar al administrador de acoplamiento.

*bTail*<br/>
de TRUE para agregar el panel al final de la lista de paneles para el administrador de acoplamiento; en caso contrario, FALSE.

*bAutoHide*<br/>
de Solo para uso interno. Use siempre el valor predeterminado FALSE.

*bInsertForOuterEdge*<br/>
de Solo para uso interno. Use siempre el valor predeterminado FALSE.

### <a name="return-value"></a>Valor devuelto

TRUE si el panel se registró correctamente con el administrador de acoplamiento; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Llame a este método para registrar paneles no flotantes y sin tamaño con el administrador de acoplamiento. Si no registra los paneles, no aparecerán correctamente cuando se disponga del administrador de acoplamiento.

##  <a name="adjustdockinglayout"></a>CDockingManager::AdjustDockingLayout

Vuelve a calcular y ajusta el diseño de todos los paneles en una ventana de marco.

```
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```

### <a name="parameters"></a>Parámetros

*hdwp*<br/>
de Especifica la estructura de posición de la ventana diferida. Para obtener más información, vea [Tipos de datos de Windows](/windows/win32/WinProg/windows-data-types).

### <a name="remarks"></a>Observaciones

##  <a name="addminiframe"></a>CDockingManager::AddMiniFrame

Agrega un marco a la lista de fotogramas.

```
virtual BOOL AddMiniFrame(CPaneFrameWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
de Un puntero a un marco.

### <a name="return-value"></a>Valor devuelto

TRUE si el marco no está en la lista de Marcos reducidos y se ha agregado correctamente; De lo contrario, FALSE.

##  <a name="adjustpaneframes"></a>CDockingManager::AdjustPaneFrames

Hace que el mensaje de WM_NCCALCSIZE se envíe a todos los paneles y `CPaneFrameWnd` ventanas.

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>Observaciones

##  <a name="adjustrecttoclientarea"></a>CDockingManager::AdjustRectToClientArea

Ajusta la alineación de un rectángulo.

```
virtual BOOL AdjustRectToClientArea(
    CRect& rectResult,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Parámetros

*rectResult*<br/>
de Referencia a un objeto `CRect`

*dwAlignment*<br/>
de Alineación del objeto `CRect`

### <a name="return-value"></a>Valor devuelto

TRUE si se ajustó la alineación del objeto `CRect`; De lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

El parámetro *dwAlignment* puede tener uno de los valores siguientes:

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

##  <a name="alignautohidepane"></a>CDockingManager::AlignAutoHidePane

Cambia el tamaño de un panel acoplable en modo Ocultar automáticamente para que tome el ancho o el alto completo del área cliente del marco entre los sitios acoplados.

```
void AlignAutoHidePane(
    CPaneDivider* pDefaultSlider,
    BOOL bIsVisible = TRUE);
```

### <a name="parameters"></a>Parámetros

*pDefaultSlider*<br/>
de Panel de control deslizante de acoplamiento.

*bIsVisible*<br/>
de TRUE si está visible el panel de acoplamiento; De lo contrario, FALSE.

##  <a name="autohidepane"></a>CDockingManager::AutoHidePane

Crea una barra de herramientas ocultar automáticamente.

```
CMFCAutoHideToolBar* AutoHidePane(
    CDockablePane* pBar,
    CMFCAutoHideToolBar* pCurrAutoHideToolBar = NULL);
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
de Puntero al panel de barra.

*pCurrAutoHideToolBar*<br/>
de Puntero a una barra de herramientas ocultar automáticamente.

### <a name="return-value"></a>Valor devuelto

NULL si no se creó la barra de herramientas ocultar automáticamente; de lo contrario, un puntero a la nueva barra de herramientas.

##  <a name="bringbarstotop"></a>CDockingManager::BringBarsToTop

Coloca en la parte superior las barras acopladas que tienen la alineación especificada.

```
void BringBarsToTop(
    DWORD dwAlignment = 0,
    BOOL bExcludeDockedBars = TRUE);
```

### <a name="parameters"></a>Parámetros

*dwAlignment*<br/>
de Alineación de las barras de acoplamiento que se llevan a la parte superior de otras ventanas.

*bExcludeDockedBars*<br/>
de TRUE para excluir la posición de las barras acopladas en la parte superior; en caso contrario, FALSE.

##  <a name="buildpanesmenu"></a>CDockingManager::BuildPanesMenu

Agrega nombres de paneles y barras de herramientas de acoplamiento a un menú.

```
void BuildPanesMenu(
    CMenu& menu,
    BOOL bToolbarsOnly);
```

### <a name="parameters"></a>Parámetros

*MENU*<br/>
de Un menú para agregar los nombres de los paneles y barras de herramientas de acoplamiento.

*bToolbarsOnly*<br/>
de TRUE para agregar solo nombres de barras de herramientas al menú; De lo contrario, FALSE.

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

*pWnd*<br/>
de Puntero a la ventana que se va a acoplar.

*ptMouse*<br/>
de La ubicación del mouse.

*rectResult*<br/>
enuncia Rectángulo calculado.

*bDrawTab*<br/>
de TRUE para dibujar una pestaña; en caso contrario, FALSE.

*ppTargetBar*<br/>
enuncia Un puntero a un puntero al panel de destino.

### <a name="remarks"></a>Observaciones

Este método calcula el rectángulo que ocuparía una ventana si un usuario arrastrase la ventana hasta el punto especificado por *ptMouse* y lo acoplaba allí.

##  <a name="create"></a>CDockingManager:: Create

Crea un administrador de acoplamiento.

```
BOOL Create(CFrameWnd* pParentWnd);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
de Puntero al marco primario del administrador de acoplamiento. Este valor no debe ser NULL.

### <a name="return-value"></a>Valor devuelto

TRUE siempre.

##  <a name="determinepaneandstatus"></a>CDockingManager::D eterminePaneAndStatus

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

*pt*<br/>
de Ubicación del panel que se va a comprobar.

*nSensitivity*<br/>
de Valor para aumentar el rectángulo de la ventana de cada panel activado. Un panel cumple los criterios de búsqueda si el punto especificado se encuentra en esta mayor región.

*dwEnabledAlignment*<br/>
de Alineación del panel de acoplamiento.

*ppTargetBar*<br/>
enuncia Un puntero a un puntero al panel de destino.

*pBarToIgnore*<br/>
de Panel que omite el método.

*pBarToDock*<br/>
de Panel que está acoplado.

### <a name="return-value"></a>Valor devuelto

El estado de acoplamiento.

### <a name="remarks"></a>Observaciones

El estado de acoplamiento puede ser uno de los siguientes valores:

|AFX_CS_STATUS valor|Significado|
|---------------------------|-------------|
|CS_NOTHING|El puntero no está sobre un sitio de acoplamiento. Por lo tanto, mantenga el panel flotante.|
|CS_DOCK_IMMEDIATELY|El puntero está sobre el sitio de acoplamiento en el modo inmediato (el estilo de DT_IMMEDIATE está habilitado), por lo que el panel debe acoplarse inmediatamente.|
|CS_DELAY_DOCK|El puntero está sobre un sitio de acoplamiento que es otro panel acoplable o es un borde del marco principal.|
|CS_DELAY_DOCK_TO_TAB|El puntero se encuentra sobre un sitio de acoplamiento que hace que el panel se acople en una ventana con pestañas. Esto se produce cuando el mouse está encima de un título de otro panel de acoplamiento o de un área de ficha de un panel con pestañas.|

##  <a name="disablerestoredockstate"></a>CDockingManager::D isableRestoreDockState

Habilita o deshabilita la carga del diseño de acoplamiento del registro.

```
void DisableRestoreDockState(BOOL bDisable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bDeshabilite*<br/>
de TRUE para deshabilitar la carga del diseño de acoplamiento del registro; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Llame a este método cuando deba conservar el diseño actual de paneles de acoplamiento y barras de herramientas cuando se cargue el estado de la aplicación.

##  <a name="dockpane"></a>CDockingManager::D ockPane

Acopla un panel a otro panel o a una ventana de marco.

```
void DockPane(
    CBasePane* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
de Un puntero a un panel de barra para acoplarlo.

*nDockBarID*<br/>
de Identificador de la barra que se va a acoplar.

*lpRect*<br/>
de Rectángulo de destino.

##  <a name="dockpaneleftof"></a>CDockingManager::D ockPaneLeftOf

Acopla un panel a la izquierda de otro panel.

```
BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>Parámetros

*pBarToDock*<br/>
de Puntero al panel que se va a acoplar a la izquierda de *pTargetBar*.

*pTargetBar*<br/>
de Puntero al panel de destino.

### <a name="return-value"></a>Valor devuelto

TRUE si el panel se ha acoplado correctamente; en caso contrario, FALSE.

##  <a name="enableautohidepanes"></a>CDockingManager::EnableAutoHidePanes

Habilita el acoplamiento del panel al marco principal, crea un panel de acoplamiento y lo agrega a la lista de barras de control.

```
BOOL EnableAutoHidePanes(DWORD dwStyle);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
de Alineación de acoplamiento.

### <a name="return-value"></a>Valor devuelto

TRUE si el panel de acoplamiento se creó correctamente; De lo contrario, FALSE.

##  <a name="enabledocking"></a>CDockingManager:: EnableDocking

Crea un panel de acoplamiento y permite acoplar el panel en el marco principal.

```
BOOL EnableDocking(DWORD dwStyle);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
de Alineación de acoplamiento.

### <a name="return-value"></a>Valor devuelto

TRUE si el panel de acoplamiento se creó correctamente; De lo contrario, FALSE.

##  <a name="enabledocksitemenu"></a>CDockingManager::EnableDockSiteMenu

Muestra un botón adicional que abre un menú emergente en los títulos de todos los paneles de acoplamiento.

```
static void EnableDockSiteMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
de TRUE para habilitar el menú de sitio de Dock; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

En el menú sitio de acoplamiento se muestran las siguientes opciones para cambiar el estado de acoplamiento del panel:

- `Floating`: flota un panel

- `Docking`: acopla un panel en el marco principal en la ubicación en la que se ha acoplado el panel por última vez.

- `AutoHide`: cambia el panel al modo de ocultar automáticamente

- `Hide`: oculta un panel

De forma predeterminada, este menú no se muestra.

##  <a name="enablepanecontextmenu"></a>CDockingManager::EnablePaneContextMenu

Indica a la biblioteca que muestre un menú contextual especial que tenga una lista de barras de herramientas de la aplicación y paneles de acoplamiento cuando el usuario haga clic con el botón secundario del mouse y la biblioteca esté procesando el mensaje de WM_CONTEXTMENU.

```
void EnablePaneContextMenu(
    BOOL bEnable,
    UINT uiCustomizeCmd,
    const CString& strCustomizeText,
    BOOL bToolbarsOnly = FALSE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
de Si es TRUE, la biblioteca activa la compatibilidad con el menú contextual automático; Si es FALSE, la biblioteca desactiva la compatibilidad con el menú contextual automático.

*uiCustomizeCmd*<br/>
de Identificador de comando para el elemento **personalizar** en el menú.

*strCustomizeText*<br/>
de Texto del elemento que se va a **personalizar** .

*bToolbarsOnly*<br/>
de Si es TRUE, el menú muestra solo una lista de barras de herramientas de la aplicación; Si es FALSE, la biblioteca agrega paneles de acoplamiento de aplicaciones a esta lista.

##  <a name="finddocksite"></a>CDockingManager::FindDockSite

Recupera el panel de barra que se encuentra en la posición especificada y que tiene la alineación especificada.

```
virtual CDockSite* FindDockSite(
    DWORD dwAlignment,
    BOOL bOuter);
```

### <a name="parameters"></a>Parámetros

*dwAlignment*<br/>
de Alineación del panel de barras.

*más cercado*<br/>
de Si es TRUE, recupere la barra en la posición del encabezado en la lista de barras de control. De lo contrario, recupere la barra en la posición de la cola en la lista de barras de control.

### <a name="return-value"></a>Valor devuelto

Panel acoplable que tiene la alineación especificada; De lo contrario, NULL.

##  <a name="findpanebyid"></a>CDockingManager::FindPaneByID

Busca un panel por el ID. de control especificado.

```
virtual CBasePane* FindPaneByID(
    UINT uBarID,
    BOOL bSearchMiniFrames = FALSE);
```

### <a name="parameters"></a>Parámetros

*uBarID*<br/>
de Especifica el identificador de control del panel que se va a buscar.

*bSearchMiniFrames*<br/>
de TRUE para incluir todos los paneles flotantes en la búsqueda. FALSE para incluir solo los paneles acoplados.

### <a name="return-value"></a>Valor devuelto

El objeto [a cbasepane](../../mfc/reference/cbasepane-class.md) que tiene el identificador de control especificado, o null si no se encuentra el panel especificado.

### <a name="remarks"></a>Observaciones

##  <a name="finddocksitebypane"></a>CDockingManager::FindDockSiteByPane

Devuelve el panel de barra que tiene el identificador del panel de la barra de destino.

```
virtual CDockSite* FindDockSiteByPane(CPane* pTargetBar);
```

### <a name="parameters"></a>Parámetros

*pTargetBar*<br/>
de Puntero al panel de la barra de destino.

### <a name="return-value"></a>Valor devuelto

El panel de barra que tiene el identificador del panel de la barra de destino; ES NULL si no existe tal panel de barra.

##  <a name="fixupvirtualrects"></a>CDockingManager::FixupVirtualRects

Confirma todas las posiciones de la barra de herramientas actual en rectángulos virtuales.

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>Observaciones

Cuando el usuario empieza a arrastrar una barra de herramientas, la aplicación recuerda su posición original en el *rectángulo virtual*. Cuando el usuario mueve una barra de herramientas por su sitio de acoplamiento, la barra de herramientas puede desplazarse por otras barras de herramientas. Las posiciones originales de las otras barras de herramientas se almacenan en los rectángulos virtuales correspondientes.

##  <a name="framefrompoint"></a>CDockingManager::FrameFromPoint

Devuelve el marco que contiene el punto especificado.

```
virtual CPaneFrameWnd* FrameFromPoint(
    CPoint pt,
    CPaneFrameWnd* pFrameToExclude,
    BOOL bFloatMultiOnly) const;
```

### <a name="parameters"></a>Parámetros

*pt*<br/>
de Especifica el punto, en coordenadas de la pantalla, que se va a comprobar.

*pFrameToExclude*<br/>
de Puntero a un marco que se va a excluir.

*bFloatMultiOnly*<br/>
de TRUE para excluir fotogramas que no sean instancias de `CMultiPaneFrameWnd`; De lo contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

Marco que contiene el punto especificado; De lo contrario, NULL.

##  <a name="getclientareabounds"></a>CDockingManager::GetClientAreaBounds

Obtiene el rectángulo que contiene los límites del área cliente.

```
CRect GetClientAreaBounds() const;

void GetClientAreaBounds(CRect& rcClient);
```

### <a name="parameters"></a>Parámetros

*rcClient*<br/>
enuncia Referencia al rectángulo que contiene los límites del área cliente.

### <a name="return-value"></a>Valor devuelto

Rectángulo que contiene los límites del área cliente.

##  <a name="getdockingmode"></a>CDockingManager::GetDockingMode

Devuelve el modo de acoplamiento actual.

```
static AFX_DOCK_TYPE GetDockingMode();
```

### <a name="return-value"></a>Valor devuelto

Un valor de enumerador que representa el modo de acoplamiento actual. Puede ser uno de los siguientes valores:

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

### <a name="remarks"></a>Observaciones

Para establecer el modo de acoplamiento, llame a [CDockingManager:: SetDockingMode](#setdockingmode).

##  <a name="getdocksiteframewnd"></a>CDockingManager::GetDockSiteFrameWnd

Obtiene un puntero al marco de la ventana primaria.

```
CFrameWnd* GetDockSiteFrameWnd() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al marco de la ventana primaria.

##  <a name="getenabledautohidealignment"></a>CDockingManager::GetEnabledAutoHideAlignment

Devuelve la alineación habilitada de los paneles.

```
DWORD GetEnabledAutoHideAlignment() const;
```

### <a name="return-value"></a>Valor devuelto

Combinación bit a bit de marcas de CBRS_ALIGN_, o 0 si los paneles de ocultar automáticamente no están habilitados. Para obtener más información, vea [CFrameWnd:: EnableDocking](../../mfc/reference/cframewnd-class.md#enabledocking).

### <a name="remarks"></a>Observaciones

El método devuelve la alineación habilitada para ocultar automáticamente las barras de control. Para habilitar las barras ocultas automáticamente, llame a [CFrameWndEx:: EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes).

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

Rectángulo que contiene los bordes exteriores del marco.

##  <a name="getpanelist"></a>CDockingManager::GetPaneList

Devuelve una lista de los paneles que pertenecen al administrador de acoplamiento. Esto incluye todos los paneles flotantes.

```
void GetPaneList(
    CObList& lstBars,
    BOOL bIncludeAutohide = FALSE,
    CRuntimeClass* pRTCFilter = NULL,
    BOOL bIncludeTabs = FALSE);
```

### <a name="parameters"></a>Parámetros

*lstBars*<br/>
[in, out] Contiene todos los paneles del administrador de acoplamiento actual.

*bIncludeAutohide*<br/>
de TRUE para incluir los paneles que se encuentran en modo de ocultación automáticamente; en caso contrario, FALSE.

*pRTCFilter*<br/>
de Si no es NULL, la lista devuelta contiene paneles solo de la clase en tiempo de ejecución especificada.

*bIncludeTabs*<br/>
de TRUE para incluir pestañas; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Si hay paneles con pestañas en el administrador de acoplamiento, el método devuelve punteros a objetos de la [clase CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md) y debe enumerar las fichas explícitamente.

Use *pRTCFilter* para obtener una clase determinada de paneles. Por ejemplo, puede obtener únicamente barras de herramientas estableciendo este valor de manera adecuada.

##  <a name="getsmartdockingmanager"></a>CDockingManager::GetSmartDockingManager

Recupera un puntero al administrador de acoplamiento inteligente.

```
CSmartDockingManager* GetSmartDockingManager();
```

### <a name="return-value"></a>Valor devuelto

Puntero al administrador de acoplamiento inteligente.

##  <a name="getsmartdockingmanagerpermanent"></a>CDockingManager::GetSmartDockingManagerPermanent

Recupera un puntero al administrador de acoplamiento inteligente.

```
CSmartDockingManager* GetSmartDockingManagerPermanent() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al administrador de acoplamiento inteligente.

##  <a name="getsmartdockingparams"></a>CDockingManager::GetSmartDockingParams

Devuelve los parámetros de acoplamiento inteligente para el administrador de acoplamiento.

```
static CSmartDockingInfo& GetSmartDockingParams();
```

### <a name="return-value"></a>Valor devuelto

La clase que contiene los parámetros de acoplamiento inteligente para el administrador de acoplamiento actual. Para obtener más información, consulte [clase CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md).

### <a name="remarks"></a>Observaciones

##  <a name="hideautohidepanes"></a>CDockingManager::HideAutoHidePanes

Oculta un panel que está en modo de ocultación automáticamente.

```
void HideAutoHidePanes(
    CDockablePane* pBarToExclude = NULL,
    BOOL bImmediately = FALSE);
```

### <a name="parameters"></a>Parámetros

*pBarToExclude*<br/>
de Puntero a una barra que se va a excluir de la ocultación.

*bImmediately*<br/>
de TRUE para ocultar el panel inmediatamente; FALSE para ocultar el panel con el efecto de ocultar automáticamente.

##  <a name="insertdocksite"></a>CDockingManager::InsertDockSite

Crea un panel de acoplamiento y lo inserta en la lista de barras de control.

```
BOOL InsertDockSite(
    const AFX_DOCKSITE_INFO& info,
    DWORD dwAlignToInsertAfter,
    CDockSite** ppDockBar = NULL);
```

### <a name="parameters"></a>Parámetros

*info*<br/>
de Estructura que contiene la información de alineación sobre el panel de acoplamiento.

*dwAlignToInsertAfter*<br/>
de Alineación del panel de acoplamiento.

*ppDockBar*<br/>
enuncia Un puntero a un puntero a un panel de acoplamiento.

### <a name="return-value"></a>Valor devuelto

TRUE si el panel de acoplamiento se creó correctamente; De lo contrario, FALSE.

##  <a name="insertpane"></a>CDockingManager::InsertPane

Inserta un panel de control en la lista de barras de control.

```
BOOL InsertPane(
    CBasePane* pControlBar,
    CBasePane* pTarget,
    BOOL bAfter = TRUE);
```

### <a name="parameters"></a>Parámetros

*pControlBar*<br/>
de Un puntero a un panel de control.

*pTarget*<br/>
de Un puntero a un panel de destino.

*bAfter*<br/>
de TRUE para insertar el panel después de la posición del panel de destino; De lo contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

TRUE si el panel de control se ha agregado correctamente a la lista de barras de control; De lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método devuelve false si el panel de control ya está en la lista de barras de control o si el panel de destino no existe en la lista de barras de control.

##  <a name="isdocksitemenu"></a>CDockingManager::IsDockSiteMenu

Especifica si se muestra un menú emergente en los títulos de todos los paneles.

```
static BOOL IsDockSiteMenu();
```

### <a name="return-value"></a>Valor devuelto

TRUE si se muestra un menú de sitio de acoplamiento en los títulos de todos los paneles de acoplamiento; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Puede habilitar el menú sitio de Dock llamando a [CDockingManager:: EnableDockSiteMenu](#enabledocksitemenu).

##  <a name="isinadjustlayout"></a>CDockingManager::IsInAdjustLayout

Determina si se ajustan los diseños de todos los paneles.

```
BOOL IsInAdjustLayout() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si se ajustan los diseños de todos los paneles; De lo contrario, FALSE.

##  <a name="isolecontainermode"></a>CDockingManager::IsOLEContainerMode

Especifica si el administrador de acoplamiento está en modo de contenedor OLE.

```
BOOL IsOLEContainerMode() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el administrador de acoplamiento está en modo de contenedor OLE; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

En el modo de contenedor OLE, se ocultan todos los paneles de acoplamiento y las barras de herramientas de la aplicación. Los paneles también se ocultan en este modo si ha establecido [CDockingManager:: m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode) en true.

##  <a name="ispointneardocksite"></a>CDockingManager::IsPointNearDockSite

Determina si un punto especificado está cerca del sitio de acoplamiento.

```
BOOL IsPointNearDockSite(
    CPoint point,
    DWORD& dwBarAlignment,
    BOOL& bOuterEdge) const;
```

### <a name="parameters"></a>Parámetros

*Elija*<br/>
de El punto especificado.

*dwBarAlignment*<br/>
enuncia Especifica a qué borde está cerca el punto. Los valores posibles son CBRS_ALIGN_LEFT, CBRS_ALIGN_RIGHT, CBRS_ALIGN_TOP y CBRS_ALIGN_BOTTOM.

*bOuterEdge*<br/>
enuncia TRUE si el punto está cerca del borde exterior del sitio de acoplamiento; De lo contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

TRUE si el punto está cerca del sitio de acoplamiento; en caso contrario, FALSE.

##  <a name="isprintpreviewvalid"></a>CDockingManager::IsPrintPreviewValid

Determina si el modo de vista previa de impresión está establecido.

```
BOOL IsPrintPreviewValid() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si está establecido el modo de vista previa de impresión; De lo contrario, FALSE.

##  <a name="loadstate"></a>CDockingManager:: LoadState

Carga el estado del administrador de acoplamiento desde el registro.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
de Nombre del perfil.

*uiID*<br/>
de Identificador del administrador de acoplamiento.

### <a name="return-value"></a>Valor devuelto

TRUE si el estado del administrador de acoplamiento se cargó correctamente; en caso contrario, FALSE.

##  <a name="lockupdate"></a>CDockingManager::LockUpdate

Bloquea la ventana especificada.

```
void LockUpdate(BOOL bLock);
```

### <a name="parameters"></a>Parámetros

*Sin*<br/>
de TRUE si la ventana está bloqueada; De lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Cuando una ventana está bloqueada, no se puede desplace y no se puede volver a dibujar.

##  <a name="m_bhidedockingbarsincontainermode"></a>CDockingManager:: m_bHideDockingBarsInContainerMode

Especifica si el administrador de acoplamiento oculta los paneles en el modo de contenedor OLE.

```
AFX_IMPORT_DATA static BOOL m_bHideDockingBarsInContainerMode;
```

### <a name="remarks"></a>Observaciones

Establezca este valor en FALSE si desea mantener visibles todos los paneles acoplados al marco principal cuando la aplicación está en modo de contenedor OLE. De forma predeterminada, este valor es TRUE.

##  <a name="m_dockmodeglobal"></a>CDockingManager:: m_dockModeGlobal

Especifica el modo de acoplamiento global.

```
AFX_IMPORT_DATA static AFX_DOCK_TYPE m_dockModeGlobal;
```

### <a name="remarks"></a>Observaciones

De forma predeterminada, cada panel de acoplamiento utiliza este modo de acoplamiento. Para obtener más información sobre los valores en los que se puede establecer este campo, vea [a cbasepane:: GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).

##  <a name="m_ndocksensitivity"></a>CDockingManager:: m_nDockSensitivity

Especifica la sensibilidad de acoplamiento.

```
AFX_IMPORT_DATA static int m_nDockSensitivity;
```

### <a name="remarks"></a>Observaciones

La sensibilidad de acoplamiento define cómo cerrar un panel flotante puede enfocarse en un panel acoplable, un sitio de acoplamiento u otro panel antes de que el marco cambie su estado a acoplado.

##  <a name="m_ntimeoutbeforedockingbardock"></a>CDockingManager:: m_nTimeOutBeforeDockingBarDock

Especifica el tiempo, en milisegundos, antes de que un panel acoplable se acople en el modo de acoplamiento inmediato.

```
static UINT m_nTimeOutBeforeDockingBarDock;
```

### <a name="remarks"></a>Observaciones

Antes de acoplar un panel, el marco de trabajo espera la cantidad de tiempo especificada. Esto evita que el panel se acople accidentalmente a una ubicación mientras el usuario todavía lo está arrastrando.

##  <a name="m_ntimeoutbeforetoolbardock"></a>CDockingManager:: m_nTimeOutBeforeToolBarDock

Especifica el tiempo, en milisegundos, antes de que una barra de herramientas esté acoplada a la ventana de marco principal.

```
static UINT m_nTimeOutBeforeToolBarDock;
```

### <a name="remarks"></a>Observaciones

Antes de que una barra de herramientas esté acoplada, el marco de trabajo espera la cantidad de tiempo especificada. Esto evita que la barra de herramientas se acople accidentalmente a una ubicación mientras el usuario todavía lo está arrastrando.

##  <a name="onactivateframe"></a>CDockingManager::OnActivateFrame

Lo llama el marco de trabajo cuando la ventana de marco se activa o se desactiva.

```
virtual void OnActivateFrame(BOOL bActivate);
```

### <a name="parameters"></a>Parámetros

*bActivate*<br/>
de Si es TRUE, la ventana de marco se activa; Si es FALSE, la ventana de marco está desactivada.

##  <a name="onclosepopupmenu"></a>CDockingManager::OnClosePopupMenu

Lo llama el marco cuando un menú emergente activo procesa un mensaje WM_DESTROY.

```
void OnClosePopupMenu();
```

### <a name="remarks"></a>Observaciones

El marco de trabajo envía un mensaje de WM_DESTROY cuando está a punto de cerrar la ventana principal actual. Invalide este método para controlar las notificaciones de `CMFCPopupMenu` objetos que pertenecen a la ventana de marco cuando un objeto `CMFCPopupMenu` procesa un mensaje de WM_DESTROY.

##  <a name="onmoveminiframe"></a>CDockingManager::OnMoveMiniFrame

Lo llama el marco de trabajo para desplace una ventana de marco reducido.

```
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```

### <a name="parameters"></a>Parámetros

*pFrame*<br/>
de Puntero a una ventana de marco reducido.

### <a name="return-value"></a>Valor devuelto

TRUE si el método se ejecuta correctamente; en caso contrario, FALSE.

##  <a name="onpanecontextmenu"></a>CDockingManager::OnPaneContextMenu

Lo llama el marco de trabajo cuando crea un menú que tiene una lista de paneles.

```
void OnPaneContextMenu(CPoint point);
```

### <a name="parameters"></a>Parámetros

*Elija*<br/>
de Especifica la ubicación del menú.

##  <a name="panefrompoint"></a>CDockingManager::P aneFromPoint

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

*Elija*<br/>
de Especifica el punto, en coordenadas de la pantalla, que se va a comprobar.

*nSensitivity*<br/>
de Valor para aumentar el rectángulo de la ventana de cada panel activado. Un panel cumple los criterios de búsqueda si el punto especificado se encuentra en esta región no plana.

*bExactBar*<br/>
de TRUE para omitir el parámetro *nSensitivity* ; en caso contrario, FALSE.

*pRTCBarType*<br/>
de Si no es NULL, el método busca solo los paneles del tipo especificado.

*bCheckVisibility*<br/>
de TRUE para comprobar solo los paneles visibles; en caso contrario, FALSE.

*dwAlignment*<br/>
enuncia Si un panel se encuentra en el punto especificado, este parámetro contiene el lado del panel más cercano al punto especificado. Para obtener más información, vea la sección Comentarios.

*pBarToIgnore*<br/>
de Si no es NULL, el método omite los paneles especificados por este parámetro.

### <a name="return-value"></a>Valor devuelto

Objeto derivado de [a cbasepane](../../mfc/reference/cbasepane-class.md)que contiene el punto especificado, o null si no se encuentra ningún panel.

### <a name="remarks"></a>Observaciones

Cuando se devuelve la función y se encuentra un panel, *dwAlignment* contiene la alineación del punto especificado. Por ejemplo, si el punto estaba más cerca de la parte superior del panel, *dwAlignment* se establece en CBRS_ALIGN_TOP.

##  <a name="processpanecontextmenucommand"></a>CDockingManager::P rocessPaneContextMenuCommand

Lo llama el marco de trabajo para activar o desactivar una casilla para el comando especificado y volver a calcular el diseño de un panel mostrado.

```
BOOL ProcessPaneContextMenuCommand(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
de Identificador de una barra de controles del menú.

*nCode*<br/>
de Código de notificación de comandos.

*pExtra*<br/>
de Puntero a void que se convierte en un puntero a `CCmdUI` si *nCode* es CN_UPDATE_COMMAND_UI.

*pHandlerInfo*<br/>
de Puntero a una estructura de información. Este parámetro no se utiliza.

### <a name="return-value"></a>Valor devuelto

TRUE si *pEXtra* no es NULL y *nCode* es igual a CN_UPDATE_COMMAND_UI, o bien, si hay una barra de control con el *nID*especificado.

##  <a name="recalclayout"></a>CDockingManager::RecalcLayout

Vuelve a calcular el diseño interno de los controles presentes en la lista de controles.

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>Parámetros

*bNotify*<br/>
de Este parámetro no se utiliza.

##  <a name="releaseemptypanecontainers"></a>CDockingManager::ReleaseEmptyPaneContainers

Libera los contenedores de paneles vacíos.

```
void ReleaseEmptyPaneContainers();
```

##  <a name="removehiddenmditabbedbar"></a>CDockingManager::RemoveHiddenMDITabbedBar

Quita el panel de la barra oculta especificado.

```
void RemoveHiddenMDITabbedBar(CDockablePane* pBar);
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
de Un puntero a un panel de barra que se va a quitar.

##  <a name="removeminiframe"></a>CDockingManager::RemoveMiniFrame

Quita un marco especificado de la lista de fotogramas minis.

```
virtual BOOL RemoveMiniFrame(CPaneFrameWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
de Puntero a un marco que se va a quitar.

### <a name="return-value"></a>Valor devuelto

TRUE si se quita el marco especificado; De lo contrario, FALSE.

##  <a name="removepanefromdockmanager"></a>CDockingManager::RemovePaneFromDockManager

Anula el registro de un panel y lo quita de la lista en el administrador de acoplamiento.

```
void RemovePaneFromDockManager(
    CBasePane* pWnd,
    BOOL bDestroy,
    BOOL bAdjustLayout,
    BOOL bAutoHide = FALSE,
    CBasePane* pBarReplacement = NULL);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
de Un puntero a un panel que se va a quitar.

*bDestroy*<br/>
de Si es TRUE, se destruye el panel que se ha quitado.

*bAdjustLayout*<br/>
de Si es TRUE, ajuste el diseño de acoplamiento inmediatamente.

*bAutoHide*<br/>
de Si es TRUE, el panel se quita de la lista de barras de ocultación automáticamente. Si es FALSE, el panel se quita de la lista de paneles normales.

*pBarReplacement*<br/>
de Un puntero a un panel que reemplaza al panel que se ha quitado.

##  <a name="replacepane"></a>CDockingManager::ReplacePane

Reemplaza un panel con otro.

```
BOOL ReplacePane(
    CDockablePane* pOriginalBar,
    CDockablePane* pNewBar);
```

### <a name="parameters"></a>Parámetros

*pOriginalBar*<br/>
de Puntero al panel original.

*pNewBar*<br/>
de Un puntero al panel que reemplaza al panel original.

### <a name="return-value"></a>Valor devuelto

TRUE si el panel se ha reemplazado correctamente; De lo contrario, FALSE.

##  <a name="resortminiframesforzorder"></a>CDockingManager::ResortMiniFramesForZOrder

Reordena los fotogramas de la lista de fotogramas.

```
void ResortMiniFramesForZOrder();
```

##  <a name="savestate"></a>CDockingManager:: SaveState

Guarda el estado del administrador de acoplamiento en el registro.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
de Ruta de acceso a una clave del registro.

*uiID*<br/>
de IDENTIFICADOR del administrador de acoplamiento.

### <a name="return-value"></a>Valor devuelto

TRUE si el estado se ha guardado correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Guardar el estado del administrador de acoplamiento en el registro implica guardar los Estados de las barras de control, los Estados de las barras de ocultación y los Estados de los fotogramas que se encuentran en el administrador de acoplamiento.

##  <a name="sendmessagetominiframes"></a>CDockingManager::SendMessageToMiniFrames

Envía el mensaje especificado a todos los fotogramas.

```
BOOL SendMessageToMiniFrames(
    UINT uMessage,
    WPARAM wParam = 0,
    LPARAM lParam = 0);
```

### <a name="parameters"></a>Parámetros

*uMessage*<br/>
de Mensaje que se va a enviar.

*wParam*<br/>
de Información adicional dependiente del mensaje.

*lParam*<br/>
de Información adicional dependiente del mensaje.

### <a name="return-value"></a>Valor devuelto

TRUE siempre.

##  <a name="serialize"></a>CDockingManager:: Serialize

Escribe el administrador de acoplamiento en un archivo.

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

*analítico*<br/>
de Referencia a un objeto de almacenamiento.

### <a name="remarks"></a>Observaciones

Escribir el administrador de acoplamiento en un archivo implica determinar el número de barras de control de acoplamiento y controles deslizantes, y escribir las barras de control, los fotogramas, las barras de ocultación y las barras de pestañas MDI en el archivo.

##  <a name="setautohidezorder"></a>CDockingManager::SetAutohideZOrder

Establece el tamaño, el ancho y el alto de las barras de control y el panel especificado.

```
void SetAutohideZOrder(CDockablePane* pAHDockingBar);
```

### <a name="parameters"></a>Parámetros

*pAHDockingBar*<br/>
de Un puntero a un panel acoplable.

##  <a name="setdockingmode"></a>CDockingManager::SetDockingMode

Establece el modo de acoplamiento.

```
static void SetDockingMode(
    AFX_DOCK_TYPE dockMode,
    AFX_SMARTDOCK_THEME theme = AFX_SDT_DEFAULT);
```

### <a name="parameters"></a>Parámetros

*dockMode*<br/>
Especifica el nuevo modo de acoplamiento. Para obtener más información, vea la sección Comentarios.

*diccionarios*<br/>
Especifica el tema que se va a usar para los marcadores de acoplamiento inteligente. Puede ser uno de los valores enumerados siguientes: AFX_SDT_DEFAULT, AFX_SDT_VS2005 AFX_SDT_VS2008.

### <a name="remarks"></a>Observaciones

Llame a este método estático para establecer el modo de acoplamiento.

*dockMode* puede tener uno de los siguientes valores:

- DT_STANDARD modo de acoplamiento estándar tal como se implementa en Visual Studio .NET 2003. Los paneles se arrastran sin un contexto de arrastre.

- DT_IMMEDIATE: modo de acoplamiento inmediato tal como se implementa en Microsoft Visio. Los paneles se arrastran con un contexto de arrastre, pero no se muestran marcadores.

- DT_SMART: modo de acoplamiento inteligente tal y como se implementa en Visual Studio 2005. Los paneles se arrastran con un contexto de arrastre y se muestran marcadores inteligentes que muestran dónde se puede acoplar el panel.

##  <a name="setdockstate"></a>CDockingManager::SetDockState

Establece el estado de acoplamiento de las barras de control, los fotogramas y las barras de ocultación automáticamente.

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

*bPreview*<br/>
de TRUE si está establecido el modo de vista previa de impresión; De lo contrario, FALSE.

*pState*<br/>
de Un puntero a un estado de vista previa. Este parámetro no se utiliza.

##  <a name="setsmartdockingparams"></a>CDockingManager::SetSmartDockingParams

Establece los parámetros que definen el comportamiento de la función de acoplamiento inteligente.

```
static void SetSmartDockingParams(CSmartDockingInfo& params);
```

### <a name="parameters"></a>Parámetros

*params*<br/>
[in, out] Define los parámetros para el acoplamiento inteligente.

### <a name="remarks"></a>Observaciones

Llame a este método si desea personalizar el aspecto, el color o la forma de los marcadores de acoplamiento inteligente.

Para usar el aspecto predeterminado de los marcadores de acoplamiento inteligente, pase una instancia no inicializada de la [clase CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md) a los *parámetros*.

##  <a name="showdelayshowminiframes"></a>CDockingManager::ShowDelayShowMiniFrames

Muestra u oculta las ventanas de los fotogramas.

```
void ShowDelayShowMiniFrames(BOOL bshow);
```

### <a name="parameters"></a>Parámetros

*bShow*<br/>
de TRUE para activar la ventana del marco mostrado; FALSE para ocultar la ventana del marco.

##  <a name="showpanes"></a>CDockingManager::ShowPanes

Muestra u oculta los paneles del control y las barras de ocultación automáticamente.

```
virtual BOOL ShowPanes(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bShow*<br/>
de TRUE para mostrar los paneles; FALSE para ocultar los paneles.

### <a name="return-value"></a>Valor devuelto

Siempre FALSE.

##  <a name="startsdocking"></a>CDockingManager::StartSDocking

Inicia el acoplamiento inteligente de la ventana especificada según la alineación del administrador de acoplamiento inteligente.

```
void StartSDocking(CWnd* pDockingWnd);
```

### <a name="parameters"></a>Parámetros

*pDockingWnd*<br/>
de Puntero a una ventana que se va a acoplar.

##  <a name="stopsdocking"></a>CDockingManager::StopSDocking

Detiene el acoplamiento inteligente.

```
void StopSDocking();
```

##  <a name="getsmartdockingtheme"></a>CDockingManager::GetSmartDockingTheme

Un método estático que devuelve un tema que se usa para mostrar los marcadores de acoplamiento inteligente.

```
static AFX_SMARTDOCK_THEME __stdcall GetSmartDockingTheme();
```

### <a name="return-value"></a>Valor devuelto

Devuelve uno de los valores enumerados siguientes: AFX_SDT_DEFAULT, AFX_SDT_VS2005 AFX_SDT_VS2008.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[CFrameWndEx (clase)](../../mfc/reference/cframewndex-class.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)<br/>
[CPaneFrameWnd (clase)](../../mfc/reference/cpaneframewnd-class.md)
