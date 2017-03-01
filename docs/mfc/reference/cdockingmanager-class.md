---
title: Clase CDockingManager | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDockingManager
dev_langs:
- C++
helpviewer_keywords:
- CDockingManager class
ms.assetid: 98e69c43-55d8-4f43-b861-4fda80ec1e32
caps.latest.revision: 37
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 106046dc9dc671b5baea7c6df78b91ba37098978
ms.lasthandoff: 02/24/2017

---
# <a name="cdockingmanager-class"></a>Clase CDockingManager
Implementa la funcionalidad básica que controla el diseño de acoplamiento en una ventana de marco principal.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDockingManager : public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDockingManager::AddDockSite](#adddocksite)|Crea un panel de acoplamiento y lo agrega a la lista de barras de control.|  
|[CDockingManager::AddHiddenMDITabbedBar](#addhiddenmditabbedbar)|Agrega un identificador a una barra de panel a la lista de fichas de paneles de barra de MDI oculto.|  
|[CDockingManager::AddMiniFrame](#addminiframe)|Agrega un marco a la lista de fotogramas minivolcados.|  
|[CDockingManager::AddPane](#addpane)|Registra un panel con el Administrador de acoplamiento.|  
|[CDockingManager::AdjustDockingLayout](#adjustdockinglayout)|Vuelve a calcular y ajusta el diseño de todos los paneles en una ventana de marco.|  
|[CDockingManager::AdjustPaneFrames](#adjustpaneframes)|Hace que la `WM_NCCALCSIZE` mensaje que se enviará a todos los paneles y `CPaneFrameWnd` windows.|  
|[CDockingManager::AdjustRectToClientArea](#adjustrecttoclientarea)|Ajusta la alineación de un rectángulo.|  
|[CDockingManager::AlignAutoHidePane](#alignautohidepane)|Cambia el tamaño de un panel acoplable en modo de ocultación automática para que se necesita todo el ancho o alto del área de cliente del marco rodeado de acoplar sitios.|  
|[CDockingManager::AutoHidePane](#autohidepane)|Crea una barra de herramientas Ocultar automáticamente.|  
|[CDockingManager::BringBarsToTop](#bringbarstotop)|Aporta las barras acopladas con la alineación especificadas en la parte superior.|  
|[CDockingManager::BuildPanesMenu](#buildpanesmenu)|Agrega nombres de paneles de acoplamiento y barras de herramientas a un menú.|  
|[CDockingManager::CalcExpectedDockedRect](#calcexpecteddockedrect)|Calcula el rectángulo esperado de una ventana acoplada.|  
|[CDockingManager::Create](#create)|Crea un administrador de acoplamiento.|  
|[CDockingManager::DeterminePaneAndStatus](#determinepaneandstatus)|Determina el panel que contiene un punto determinado y su estado de acoplamiento.|  
|[CDockingManager::DisableRestoreDockState](#disablerestoredockstate)|Habilita o deshabilita la carga de diseño de acoplamiento desde el registro.|  
|[CDockingManager::DockPane](#dockpane)|Un panel se acopla a otro panel, o a una ventana de marco.|  
|[CDockingManager::DockPaneLeftOf](#dockpaneleftof)|Acopla un panel a la izquierda de otro panel.|  
|[CDockingManager::EnableAutoHidePanes](#enableautohidepanes)|Permite el acoplamiento del panel al marco principal, crea un panel de acoplamiento y lo agrega a la lista de barras de control.|  
|[CDockingManager::EnableDocking](#enabledocking)|Crea un panel de acoplamiento y permite el acoplamiento del panel en el marco principal.|  
|[CDockingManager::EnableDockSiteMenu](#enabledocksitemenu)|Muestra un botón que abre un menú emergente en los títulos de todos los paneles de acoplamiento.|  
|[CDockingManager::EnablePaneContextMenu](#enablepanecontextmenu)|Indica la biblioteca para mostrar un menú de contexto especial que tiene una lista de las barras de herramientas de la aplicación y paneles de acoplamiento cuando el usuario hace clic en el botón secundario del mouse y la biblioteca está procesando el mensaje WM_CONTEXTMENU.|  
|[CDockingManager::FindDockSite](#finddocksite)|Recupera la barra de panel que está en la posición especificada y que tiene la alineación especificadas.|  
|[CDockingManager::FindDockSiteByPane](#finddocksitebypane)|Devuelve la barra de panel que tiene el identificador del panel de barra de destino.|  
|[CDockingManager::FindPaneByID](#findpanebyid)|Busca un panel mediante el identificador de control especificado.|  
|[CDockingManager::FixupVirtualRects](#fixupvirtualrects)|Confirma todas las posiciones de la barra de herramientas actual a rectángulos virtuales.|  
|[CDockingManager::FrameFromPoint](#framefrompoint)|Devuelve el marco que contiene el punto especificado.|  
|[CDockingManager::GetClientAreaBounds](#getclientareabounds)|Obtiene el rectángulo que contiene los límites del área de cliente.|  
|[CDockingManager::GetDockingMode](#getdockingmode)|Devuelve el modo de acoplamiento actual.|  
|[CDockingManager::GetDockSiteFrameWnd](#getdocksiteframewnd)|Obtiene un puntero al marco de ventana principal.|  
|[CDockingManager::GetEnabledAutoHideAlignment](#getenabledautohidealignment)|Devuelve la alineación de los paneles habilitada.|  
|[CDockingManager::GetMiniFrames](#getminiframes)|Obtiene una lista de miniframes.|  
|[CDockingManager::GetOuterEdgeBounds](#getouteredgebounds)|Obtiene un rectángulo que contiene los bordes exteriores del marco.|  
|[CDockingManager::GetPaneList](#getpanelist)|Devuelve una lista de paneles que pertenecen al administrador de acoplamiento. Esto incluye todos los paneles flotantes.|  
|[CDockingManager::GetSmartDockingManager](#getsmartdockingmanager)|Recupera un puntero al administrador de acoplamiento inteligente.|  
|[CDockingManager::GetSmartDockingManagerPermanent](#getsmartdockingmanagerpermanent)|Recupera un puntero al administrador de acoplamiento inteligente.|  
|[CDockingManager::GetSmartDockingParams](#getsmartdockingparams)|Devuelve los parámetros de acoplamiento inteligentes para el Administrador de acoplamiento.|  
|[CDockingManager::GetSmartDockingTheme](#getsmartdockingtheme)|Un método estático que devuelve un tema que se usa para mostrar marcadores de acoplamiento inteligente.|  
|[CDockingManager::HideAutoHidePanes](#hideautohidepanes)|Oculta un panel que está en modo de ocultación automática.|  
|[CDockingManager::InsertDockSite](#insertdocksite)|Crea un panel de acoplamiento y lo inserta en la lista de barras de control.|  
|[CDockingManager::InsertPane](#insertpane)|Inserta un panel de control en la lista de barras de control.|  
|[CDockingManager::IsDockSiteMenu](#isdocksitemenu)|Especifica si se muestra un menú emergente en los títulos de todos los paneles.|  
|[CDockingManager::IsInAdjustLayout](#isinadjustlayout)|Determina si se ajustan los diseños de todos los paneles.|  
|[CDockingManager::IsOLEContainerMode](#isolecontainermode)|Especifica si el Administrador de acoplamiento está en modo de contenedor OLE.|  
|[CDockingManager::IsPointNearDockSite](#ispointneardocksite)|Determina si un punto especificado está cerca del sitio de vinculación.|  
|[CDockingManager::IsPrintPreviewValid](#isprintpreviewvalid)|Determina si se establece el modo de vista previa de impresión.|  
|[CDockingManager::LoadState](#loadstate)|Carga el estado de acoplamiento del administrador del registro.|  
|[CDockingManager::LockUpdate](#lockupdate)|Bloquea la ventana dada.|  
|[CDockingManager::OnActivateFrame](#onactivateframe)|Llamado por el marco de trabajo cuando la ventana de marco se realiza activa o se desactiva.|  
|[CDockingManager::OnClosePopupMenu](#onclosepopupmenu)|Lo llama el marco cuando un menú emergente activo procesa un mensaje WM_DESTROY.|  
|[CDockingManager::OnMoveMiniFrame](#onmoveminiframe)|Llamado por el marco para mover una ventana de marco reducido.|  
|[CDockingManager::OnPaneContextMenu](#onpanecontextmenu)|Llamado por el marco cuando compila un menú con una lista de paneles.|  
|[CDockingManager::PaneFromPoint](#panefrompoint)|Devuelve el panel que contiene el punto especificado.|  
|[CDockingManager::ProcessPaneContextMenuCommand](#processpanecontextmenucommand)|Llamado por el marco de trabajo para seleccionar o para desactivar una casilla de verificación para el comando especificado y vuelve a calcular el diseño de un panel que se muestra.|  
|[CDockingManager::RecalcLayout](#recalclayout)|Vuelve a calcular el diseño interno de los controles que se presente en la lista de controles.|  
|[CDockingManager::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)|Libera los contenedores de panel vacío.|  
|[CDockingManager::RemoveHiddenMDITabbedBar](#removehiddenmditabbedbar)|Quita oculta barra panel especificado.|  
|[CDockingManager::RemoveMiniFrame](#removeminiframe)|Quita un intervalo especificado de la lista de fotogramas minivolcados.|  
|[CDockingManager::RemovePaneFromDockManager](#removepanefromdockmanager)|Anula el registro de un panel y lo quita de la lista en el Administrador de acoplamiento.|  
|[CDockingManager::ReplacePane](#replacepane)|Reemplaza un panel con otro.|  
|[CDockingManager::ResortMiniFramesForZOrder](#resortminiframesforzorder)|Vuelve a ordenar los marcos en la lista de fotogramas minivolcados.|  
|[CDockingManager::SaveState](#savestate)|Guarda el estado del Administrador de acoplamiento en el registro.|  
|[CDockingManager::SendMessageToMiniFrames](#sendmessagetominiframes)|Envía el mensaje especificado a todos los marcos minivolcados.|  
|[CDockingManager::Serialize](#serialize)|El Administrador de acoplamiento se escribe en un archivo. (Invalida [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize).)|  
|[CDockingManager::SetAutohideZOrder](#setautohidezorder)|Establece el tamaño, ancho y alto de las barras de control y el panel especificado.|  
|[CDockingManager::SetDockingMode](#setdockingmode)|Establece el modo de acoplamiento.|  
|[CDockingManager::SetDockState](#setdockstate)|Establece el estado de acoplamiento de las barras de controles, los marcos minivolcados y las barras Ocultar automáticamente.|  
|[CDockingManager::SetPrintPreviewMode](#setprintpreviewmode)|Establece el modo de vista previa de impresión de las barras que se muestran en la vista previa de impresión.|  
|[CDockingManager::SetSmartDockingParams](#setsmartdockingparams)|Establece los parámetros que definen el comportamiento de acoplamiento inteligente.|  
|[CDockingManager::ShowDelayShowMiniFrames](#showdelayshowminiframes)|Muestra u oculta las ventanas de los marcos minivolcados.|  
|[CDockingManager::ShowPanes](#showpanes)|Muestra u oculta los paneles de las barras de control y ocultar automáticamente.|  
|[CDockingManager::StartSDocking](#startsdocking)|Inicia el acoplamiento inteligente de la ventana especificada según la alineación del Administrador de acoplamiento inteligente.|  
|[CDockingManager::StopSDocking](#stopsdocking)|Se detiene inteligente de acoplamiento.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)|Especifica si el Administrador de acoplamiento oculta paneles en modo de contenedor OLE.|  
|[CDockingManager::m_dockModeGlobal](#m_dockmodeglobal)|Especifica el modo de acoplamiento global.|  
|[CDockingManager::m_nDockSensitivity](#m_ndocksensitivity)|Especifica la distinción de acoplamiento.|  
|[CDockingManager::m_nTimeOutBeforeDockingBarDock](#m_ntimeoutbeforedockingbardock)|Especifica el tiempo, en milisegundos, antes de que un panel acoplable está acoplado en el modo inmediato de acoplamiento.|  
|[CDockingManager::m_nTimeOutBeforeToolBarDock](#m_ntimeoutbeforetoolbardock)|Especifica el tiempo, en milisegundos, antes de que una barra de herramientas está acoplada a la ventana de marco principal.|  
  
## <a name="remarks"></a>Comentarios  
 La ventana de marco principal se crea e inicializa automáticamente de esta clase.  
  
 El objeto de administrador de acoplamiento contiene una lista de todos los paneles que están en el diseño de acoplamiento y también una lista de todos los [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) windows que pertenecen a la ventana de marco principal.  
  
 El `CDockingManager` clase implementa algunos servicios que puede usar para buscar un panel o una `CPaneFrameWnd` ventana. Normalmente no se llama estos servicios directamente porque se ajustan en el objeto de ventana de marco principal. Para obtener más información, consulte [CPaneFrameWnd clase](../../mfc/reference/cpaneframewnd-class.md).  
  
## <a name="customization-tips"></a>Sugerencias de personalización  
 Las sugerencias siguientes se aplican a `CDockingManager` objetos:  
  
- [Clase CDockingManager](../../mfc/reference/cdockingmanager-class.md) admite estos modos de acoplamiento:  
  
    - `AFX_DOCK_TYPE::DT_IMMEDIATE`  
  
    - `AFX_DOCK_TYPE::DT_STANDARD`  
  
    - `AFX_DOCK_TYPE::DT_SMART`  
  
     Estos modos de acoplamiento se definen mediante [CDockingManager::m_dockModeGlobal](#m_dockmodeglobal) y se establecen mediante una llamada a [CDockingManager::SetDockingMode](#setdockingmode).  
  
-   Si desea crear un panel flotante no, invariable, llame a la [CDockingManager::AddPane](#addpane) método. Este método registra el panel con el Administrador de acoplamiento, que es responsable del diseño del panel.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios métodos en la `CDockingManager` clase para configurar un `CDockingManager` objeto. El ejemplo muestra cómo mostrar un botón que abre un menú emergente en los títulos de todos los paneles de acoplamiento y cómo establecer el modo de acoplamiento del objeto. Este fragmento de código forma parte de la [ejemplo de demostración de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#24;](../../mfc/codesnippet/cpp/cdockingmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDockingManager](../../mfc/reference/cdockingmanager-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxDockingManager.h  
  
##  <a name="a-nameadddocksitea--cdockingmanageradddocksite"></a><a name="adddocksite"></a>CDockingManager::AddDockSite  
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
 Un puntero a un puntero al nuevo panel de acoplamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel de acoplamiento se creó correctamente; `FALSE` en caso contrario.  
  
##  <a name="a-nameaddhiddenmditabbedbara--cdockingmanageraddhiddenmditabbedbar"></a><a name="addhiddenmditabbedbar"></a>CDockingManager::AddHiddenMDITabbedBar  
 Agrega un identificador a una barra de panel a la lista de fichas de paneles de barra de MDI oculto.  
  
```  
void AddHiddenMDITabbedBar(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Un puntero a una barra de panel  
  
##  <a name="a-nameaddpanea--cdockingmanageraddpane"></a><a name="addpane"></a>CDockingManager::AddPane  
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
 `TRUE`Para agregar el panel al final de la lista de paneles para el Administrador de acoplamiento; de lo contrario, `FALSE`.  
  
 [in] `bAutoHide`  
 Sólo para uso interno. Utilice siempre el valor predeterminado `FALSE`.  
  
 [in] `bInsertForOuterEdge`  
 Sólo para uso interno. Utilice siempre el valor predeterminado `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se registró correctamente con el Administrador de acoplamiento; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para registrar los paneles invariable, no flotante con el Administrador de acoplamiento. Si no registra los paneles, no se mostrarán correctamente cuando se presenta el Administrador de acoplamiento.  
  
##  <a name="a-nameadjustdockinglayouta--cdockingmanageradjustdockinglayout"></a><a name="adjustdockinglayout"></a>CDockingManager::AdjustDockingLayout  
 Vuelve a calcular y ajusta el diseño de todos los paneles en una ventana de marco.  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hdwp`  
 Especifica la estructura de posición de la ventana aplazada. Para obtener más información, consulte [tipos de datos de Windows](http://msdn.microsoft.com/library/windows/desktop/aa383751).  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameaddminiframea--cdockingmanageraddminiframe"></a><a name="addminiframe"></a>CDockingManager::AddMiniFrame  
 Agrega un marco a la lista de fotogramas minivolcados.  
  
```  
virtual BOOL AddMiniFrame(CPaneFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Un puntero a un marco.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el marco no está en la lista de fotogramas minivolcados y se ha agregado correctamente; `FALSE` en caso contrario.  
  
##  <a name="a-nameadjustpaneframesa--cdockingmanageradjustpaneframes"></a><a name="adjustpaneframes"></a>CDockingManager::AdjustPaneFrames  
 Hace que la `WM_NCCALCSIZE` mensaje que se enviará a todos los paneles y `CPaneFrameWnd` windows.  
  
```  
virtual void AdjustPaneFrames();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameadjustrecttoclientareaa--cdockingmanageradjustrecttoclientarea"></a><a name="adjustrecttoclientarea"></a>CDockingManager::AdjustRectToClientArea  
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
 `TRUE`Si la alineación de la `CRect` se ajustó el objeto; `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 El `dwAlignment` parámetro puede tener uno de los siguientes valores:  
  
-   CBRS_ALIGN_TOP  
  
-   CBRS_ALIGN_BOTTOM  
  
-   CBRS_ALIGN_LEFT  
  
-   CBRS_ALIGN_RIGHT  
  
##  <a name="a-namealignautohidepanea--cdockingmanageralignautohidepane"></a><a name="alignautohidepane"></a>CDockingManager::AlignAutoHidePane  
 Cambia el tamaño de un panel acoplable en modo de ocultación automática para que se necesita todo el ancho o alto del área de cliente del marco rodeado de acoplar sitios.  
  
```  
void AlignAutoHidePane(
    CPaneDivider* pDefaultSlider,  
    BOOL bIsVisible = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDefaultSlider`  
 El panel de control deslizante de acoplamiento.  
  
 [in] `bIsVisible`  
 `TRUE`Si el panel de acoplamiento es visible; `FALSE` en caso contrario.  
  
##  <a name="a-nameautohidepanea--cdockingmanagerautohidepane"></a><a name="autohidepane"></a>CDockingManager::AutoHidePane  
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
 `NULL`Si el auto oculta barra de herramientas no se creó; de lo contrario, un puntero a la nueva barra de herramientas.  
  
##  <a name="a-namebringbarstotopa--cdockingmanagerbringbarstotop"></a><a name="bringbarstotop"></a>CDockingManager::BringBarsToTop  
 Aporta las barras acopladas con la alineación especificadas en la parte superior.  
  
```  
void BringBarsToTop(
    DWORD dwAlignment = 0,  
    BOOL bExcludeDockedBars = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwAlignment`  
 La alineación de las barras de acoplamiento que se incluyan en la parte superior de otras ventanas.  
  
 [in] `bExcludeDockedBars`  
 `TRUE`Para impedir que las barras acopladas en la parte superior; de lo contrario, `FALSE`.  
  
##  <a name="a-namebuildpanesmenua--cdockingmanagerbuildpanesmenu"></a><a name="buildpanesmenu"></a>CDockingManager::BuildPanesMenu  
 Agrega nombres de paneles de acoplamiento y barras de herramientas a un menú.  
  
```  
void BuildPanesMenu(
    CMenu& menu,  
    BOOL bToolbarsOnly);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `menu`  
 Menú para agregar los nombres de los paneles de acoplamiento y barras de herramientas.  
  
 [in] `bToolbarsOnly`  
 `TRUE`Para agregar sólo los nombres de barra de herramientas en el menú. `FALSE` en caso contrario.  
  
##  <a name="a-namecalcexpecteddockedrecta--cdockingmanagercalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CDockingManager::CalcExpectedDockedRect  
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
 Puntero a la ventana para acoplar.  
  
 [in] `ptMouse`  
 La ubicación del mouse.  
  
 [out] `rectResult`  
 Rectángulo calculado.  
  
 [in] `bDrawTab`  
 `TRUE`para dibujar una ficha; de lo contrario, `FALSE`.  
  
 [out] `ppTargetBar`  
 Un puntero a un puntero al panel de destino.  
  
### <a name="remarks"></a>Comentarios  
 Este método calcula el rectángulo que ocuparía una ventana si un usuario arrastra la ventana para el punto especificado por `ptMouse` y acoplado no existe.  
  
##  <a name="a-namecreatea--cdockingmanagercreate"></a><a name="create"></a>CDockingManager::Create  
 Crea un administrador de acoplamiento.  
  
```  
BOOL Create(CFrameWnd* pParentWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pParentWnd`  
 Un puntero al marco primario del Administrador de acoplamiento. Este valor no debe ser `NULL`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`siempre.  
  
##  <a name="a-namedeterminepaneandstatusa--cdockingmanagerdeterminepaneandstatus"></a><a name="determinepaneandstatus"></a>CDockingManager::DeterminePaneAndStatus  
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
 El panel está acoplado.  
  
### <a name="return-value"></a>Valor devuelto  
 El estado de acoplamiento.  
  
### <a name="remarks"></a>Comentarios  
 El estado de acoplamiento puede ser uno de los siguientes valores:  
  
|Valor AFX_CS_STATUS|Significado|  
|---------------------------|-------------|  
|CS_NOTHING|El puntero no está sobre un sitio de vinculación. Por lo tanto, mantener el panel flotante.|  
|CS_DOCK_IMMEDIATELY|El puntero está sobre el sitio de vinculación en el modo inmediato (estilo DT_IMMEDIATE está habilitada), por lo que debe acoplar el panel inmediatamente.|  
|CS_DELAY_DOCK|El puntero está sobre un sitio de vinculación que otro panel de acoplamiento o un borde del marco principal.|  
|CS_DELAY_DOCK_TO_TAB|El puntero está sobre un sitio de vinculación que hace que el panel se acopla en una ventana con fichas. Esto se produce cuando el mouse está sobre un título de otro panel de acoplamiento o sobre un área de la ficha de un panel con fichas.|  
  
##  <a name="a-namedisablerestoredockstatea--cdockingmanagerdisablerestoredockstate"></a><a name="disablerestoredockstate"></a>CDockingManager::DisableRestoreDockState  
 Habilita o deshabilita la carga de diseño de acoplamiento desde el registro.  
  
```  
void DisableRestoreDockState(BOOL bDisable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bDisable`  
 `TRUE`Para deshabilitar la carga del diseño de acoplamiento del registro; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método cuando hay que conservar el diseño actual de las barras de herramientas y paneles de acoplamiento cuando se carga el estado de la aplicación.  
  
##  <a name="a-namedockpanea--cdockingmanagerdockpane"></a><a name="dockpane"></a>CDockingManager::DockPane  
 Un panel se acopla a otro panel, o a una ventana de marco.  
  
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
 El identificador de la barra de acoplar.  
  
 [in] `lpRect`  
 El rectángulo de destino.  
  
##  <a name="a-namedockpaneleftofa--cdockingmanagerdockpaneleftof"></a><a name="dockpaneleftof"></a>CDockingManager::DockPaneLeftOf  
 Acopla un panel a la izquierda de otro panel.  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBarToDock,  
    CPane* pTargetBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBarToDock`  
 Un puntero al panel para acoplar a la izquierda del `pTargetBar`.  
  
 [in] `pTargetBar`  
 Un puntero al panel de destino.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se acopla correctamente; de lo contrario, `FALSE`.  
  
##  <a name="a-nameenableautohidepanesa--cdockingmanagerenableautohidepanes"></a><a name="enableautohidepanes"></a>CDockingManager::EnableAutoHidePanes  
 Permite el acoplamiento del panel al marco principal, crea un panel de acoplamiento y lo agrega a la lista de barras de control.  
  
```  
BOOL EnableAutoHidePanes(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwStyle`  
 La alineación de acoplamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel de acoplamiento se creó correctamente; `FALSE` en caso contrario.  
  
##  <a name="a-nameenabledockinga--cdockingmanagerenabledocking"></a><a name="enabledocking"></a>CDockingManager::EnableDocking  
 Crea un panel de acoplamiento y permite el acoplamiento del panel en el marco principal.  
  
```  
BOOL EnableDocking(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwStyle`  
 La alineación de acoplamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel de acoplamiento se creó correctamente; `FALSE` en caso contrario.  
  
##  <a name="a-nameenabledocksitemenua--cdockingmanagerenabledocksitemenu"></a><a name="enabledocksitemenu"></a>CDockingManager::EnableDockSiteMenu  
 Muestra un botón que abre un menú emergente en los títulos de todos los paneles de acoplamiento.  
  
```  
static void EnableDockSiteMenu(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para habilitar el menú de sitio acoplar; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El menú de sitio acoplar muestra las siguientes opciones para cambiar el estado de acoplamiento del panel:  
  
- `Floating`-Flota de un panel  
  
- `Docking`-Se acopla un panel en el marco principal en la ubicación donde el panel se acopla última  
  
- `AutoHide`-Activa el panel en modo de ocultación automática  
  
- `Hide`-Oculta un panel  
  
 De forma predeterminada, no se muestra este menú.  
  
##  <a name="a-nameenablepanecontextmenua--cdockingmanagerenablepanecontextmenu"></a><a name="enablepanecontextmenu"></a>CDockingManager::EnablePaneContextMenu  
 Indica la biblioteca para mostrar un menú de contexto especial que tiene una lista de las barras de herramientas de la aplicación y paneles de acoplamiento cuando el usuario hace clic en el botón secundario del mouse y la biblioteca está procesando el mensaje WM_CONTEXTMENU.  
  
```  
void EnablePaneContextMenu(
    BOOL bEnable,  
    UINT uiCustomizeCmd,  
    const CString& strCustomizeText,  
    BOOL bToolbarsOnly = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 Si `TRUE`, vuelve a la biblioteca en el menú contextual automático; la compatibilidad con si `FALSE` la biblioteca desactiva la compatibilidad con menú contextual automático.  
  
 [in] `uiCustomizeCmd`  
 Un identificador de comando para la **personalizar** elemento en el menú.  
  
 [in] `strCustomizeText`  
 El texto de la **personalizar** elemento.  
  
 [in] `bToolbarsOnly`  
 Si `TRUE`, el menú muestra sólo una lista de barras de herramientas de la aplicación; si `FALSE`, la biblioteca de paneles de acoplamiento de la aplicación agrega a esta lista.  
  
##  <a name="a-namefinddocksitea--cdockingmanagerfinddocksite"></a><a name="finddocksite"></a>CDockingManager::FindDockSite  
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
 El panel de acoplamiento que tiene la alineación especificadas; `NULL` en caso contrario.  
  
##  <a name="a-namefindpanebyida--cdockingmanagerfindpanebyid"></a><a name="findpanebyid"></a>CDockingManager::FindPaneByID  
 Busca un panel mediante el identificador de control especificado.  
  
```  
virtual CBasePane* FindPaneByID(
    UINT uBarID,  
    BOOL bSearchMiniFrames = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uBarID`  
 Especifica el identificador del control del panel para buscar.  
  
 [in] `bSearchMiniFrames`  
 `TRUE`para incluir todos los paneles flotantes en la búsqueda. `FALSE`para incluir solo los paneles acoplados.  
  
### <a name="return-value"></a>Valor devuelto  
 El [CBasePane](../../mfc/reference/cbasepane-class.md) objeto que tiene el identificador del control especificado, o `NULL` si no se encuentra el panel especificado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namefinddocksitebypanea--cdockingmanagerfinddocksitebypane"></a><a name="finddocksitebypane"></a>CDockingManager::FindDockSiteByPane  
 Devuelve la barra de panel que tiene el identificador del panel de barra de destino.  
  
```  
virtual CDockSite* FindDockSiteByPane(CPane* pTargetBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pTargetBar`  
 Un puntero en el panel de barra de destino.  
  
### <a name="return-value"></a>Valor devuelto  
 La barra de panel que tiene el identificador del panel de barra de destino; `NULL` si no existe ningún como panel de barra.  
  
##  <a name="a-namefixupvirtualrectsa--cdockingmanagerfixupvirtualrects"></a><a name="fixupvirtualrects"></a>CDockingManager::FixupVirtualRects  
 Confirma todas las posiciones de la barra de herramientas actual a rectángulos virtuales.  
  
```  
virtual void FixupVirtualRects();
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando el usuario comienza a arrastrar una barra de herramientas, la aplicación recuerda su posición original en el *rectángulo virtual*. Cuando el usuario mueve una barra de herramientas a través de su sitio de vinculación, la barra de herramientas puede cambiar otras barras de herramientas. La posición original de las barras de herramientas se almacena en los rectángulos virtuales correspondientes.  
  
##  <a name="a-nameframefrompointa--cdockingmanagerframefrompoint"></a><a name="framefrompoint"></a>CDockingManager::FrameFromPoint  
 Devuelve el marco que contiene el punto especificado.  
  
```  
virtual CPaneFrameWnd* FrameFromPoint(
    CPoint pt,  
    CPaneFrameWnd* pFrameToExclude,  
    BOOL bFloatMultiOnly) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pt`  
 Especifica el punto, en coordenadas de pantalla para comprobar.  
  
 [in] `pFrameToExclude`  
 Un puntero a un marco para excluir.  
  
 [in] `bFloatMultiOnly`  
 `TRUE`Para excluir las tramas que no sean instancias de `CMultiPaneFrameWnd`; `FALSE` en caso contrario.  
  
### <a name="return-value"></a>Valor devuelto  
 El marco que contiene el punto especificado; `NULL` en caso contrario.  
  
##  <a name="a-namegetclientareaboundsa--cdockingmanagergetclientareabounds"></a><a name="getclientareabounds"></a>CDockingManager::GetClientAreaBounds  
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
  
##  <a name="a-namegetdockingmodea--cdockingmanagergetdockingmode"></a><a name="getdockingmode"></a>CDockingManager::GetDockingMode  
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
  
##  <a name="a-namegetdocksiteframewnda--cdockingmanagergetdocksiteframewnd"></a><a name="getdocksiteframewnd"></a>CDockingManager::GetDockSiteFrameWnd  
 Obtiene un puntero al marco de ventana principal.  
  
```  
CFrameWnd* GetDockSiteFrameWnd() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al marco de ventana principal.  
  
##  <a name="a-namegetenabledautohidealignmenta--cdockingmanagergetenabledautohidealignment"></a><a name="getenabledautohidealignment"></a>CDockingManager::GetEnabledAutoHideAlignment  
 Devuelve la alineación de los paneles habilitada.  
  
```  
DWORD GetEnabledAutoHideAlignment() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una combinación bit a bit de `CBRS_ALIGN_` marcas o 0 si no están habilitados los paneles de ocultación automática. Para obtener más información, consulte [CFrameWnd:: EnableDocking](../../mfc/reference/cframewnd-class.md#enabledocking).  
  
### <a name="remarks"></a>Comentarios  
 El método devuelve la alineación habilitada para ocultar automáticamente las barras de control. Para habilitar las barras Ocultar automáticamente, llame a [CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes).  
  
##  <a name="a-namegetminiframesa--cdockingmanagergetminiframes"></a><a name="getminiframes"></a>CDockingManager::GetMiniFrames  
 Obtiene una lista de miniframes.  
  
```  
const CObList& GetMiniFrames() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una lista de miniframes que contienen las barras de controles que pertenecen al administrador de acoplamiento.  
  
##  <a name="a-namegetouteredgeboundsa--cdockingmanagergetouteredgebounds"></a><a name="getouteredgebounds"></a>CDockingManager::GetOuterEdgeBounds  
 Obtiene un rectángulo que contiene los bordes exteriores del marco.  
  
```  
CRect GetOuterEdgeBounds() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un rectángulo que contiene los bordes exteriores del marco.  
  
##  <a name="a-namegetpanelista--cdockingmanagergetpanelist"></a><a name="getpanelist"></a>CDockingManager::GetPaneList  
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
 `TRUE`para incluir los paneles que están en modo de ocultación automática; de lo contrario, `FALSE`.  
  
 [in] `pRTCFilter`  
 Si no `NULL`, la lista devuelta contiene paneles sólo de la clase en tiempo de ejecución.  
  
 [in] `bIncludeTabs`  
 `TRUE`para incluir las fichas; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si hay cualquier paneles con fichas en el Administrador de acoplamiento, el método devuelve punteros a [CBaseTabbedPane clase](../../mfc/reference/cbasetabbedpane-class.md) objetos y se deben enumerar explícitamente las fichas.  
  
 Use `pRTCFilter` para obtener una clase determinada de paneles. Por ejemplo, puede obtener sólo las barras de herramientas al establecer este valor correctamente.  
  
##  <a name="a-namegetsmartdockingmanagera--cdockingmanagergetsmartdockingmanager"></a><a name="getsmartdockingmanager"></a>CDockingManager::GetSmartDockingManager  
 Recupera un puntero al administrador de acoplamiento inteligente.  
  
```  
CSmartDockingManager* GetSmartDockingManager();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la [manager de acoplamiento inteligente](http://msdn.microsoft.com/en-us/f537a1a6-fb9e-41d7-952f-0f25d5ee7534).  
  
##  <a name="a-namegetsmartdockingmanagerpermanenta--cdockingmanagergetsmartdockingmanagerpermanent"></a><a name="getsmartdockingmanagerpermanent"></a>CDockingManager::GetSmartDockingManagerPermanent  
 Recupera un puntero al administrador de acoplamiento inteligente.  
  
```  
CSmartDockingManager* GetSmartDockingManagerPermanent() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al administrador de acoplamiento inteligente.  
  
##  <a name="a-namegetsmartdockingparamsa--cdockingmanagergetsmartdockingparams"></a><a name="getsmartdockingparams"></a>CDockingManager::GetSmartDockingParams  
 Devuelve los parámetros de acoplamiento inteligentes para el Administrador de acoplamiento.  
  
```  
static CSmartDockingInfo& GetSmartDockingParams();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La clase que contiene los parámetros de acoplamiento inteligentes para el Administrador de acoplamiento actual. Para obtener más información, consulte [CSmartDockingInfo clase](../../mfc/reference/csmartdockinginfo-class.md).  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namehideautohidepanesa--cdockingmanagerhideautohidepanes"></a><a name="hideautohidepanes"></a>CDockingManager::HideAutoHidePanes  
 Oculta un panel que está en modo de ocultación automática.  
  
```  
void HideAutoHidePanes(
    CDockablePane* pBarToExclude = NULL,  
    BOOL bImmediately = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBarToExclude`  
 Un puntero a una barra de excluir de ocultación.  
  
 [in] `bImmediately`  
 `TRUE`Para ocultar el panel inmediatamente; `FALSE` para ocultar el panel con el efecto de ocultar automáticamente.  
  
##  <a name="a-nameinsertdocksitea--cdockingmanagerinsertdocksite"></a><a name="insertdocksite"></a>CDockingManager::InsertDockSite  
 Crea un panel de acoplamiento y lo inserta en la lista de barras de control.  
  
```  
BOOL InsertDockSite(
    const AFX_DOCKSITE_INFO& info,  
    DWORD dwAlignToInsertAfter,  
    CDockSite** ppDockBar = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `info`  
 Estructura que contiene la información de alineación acerca del panel de acoplamiento.  
  
 [in] `dwAlignToInsertAfter`  
 Alineación del panel de acoplamiento.  
  
 [out] `ppDockBar`  
 Un puntero a un puntero a un panel de acoplamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel de acoplamiento se creó correctamente; `FALSE` en caso contrario.  
  
##  <a name="a-nameinsertpanea--cdockingmanagerinsertpane"></a><a name="insertpane"></a>CDockingManager::InsertPane  
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
 Puntero a un panel de destino.  
  
 [in] `bAfter`  
 `TRUE`Para insertar el panel después de la posición del panel de destino; `FALSE` en caso contrario.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel de control se agrega correctamente a la lista de barras de control; `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve false si ya está en la lista de barras de control en el panel de control o si el panel de destino no existe en la lista de barras de control.  
  
##  <a name="a-nameisdocksitemenua--cdockingmanagerisdocksitemenu"></a><a name="isdocksitemenu"></a>CDockingManager::IsDockSiteMenu  
 Especifica si se muestra un menú emergente en los títulos de todos los paneles.  
  
```  
static BOOL IsDockSiteMenu();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se muestra un menú de sitio de acoplamiento en los títulos de todos los paneles de acoplamiento; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Puede habilitar el menú de sitio acoplar llamando [CDockingManager::EnableDockSiteMenu](#enabledocksitemenu).  
  
##  <a name="a-nameisinadjustlayouta--cdockingmanagerisinadjustlayout"></a><a name="isinadjustlayout"></a>CDockingManager::IsInAdjustLayout  
 Determina si se ajustan los diseños de todos los paneles.  
  
```  
BOOL IsInAdjustLayout() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se ajustan los diseños de todos los paneles; `FALSE` en caso contrario.  
  
##  <a name="a-nameisolecontainermodea--cdockingmanagerisolecontainermode"></a><a name="isolecontainermode"></a>CDockingManager::IsOLEContainerMode  
 Especifica si el Administrador de acoplamiento está en modo de contenedor OLE.  
  
```  
BOOL IsOLEContainerMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el Administrador de acoplamiento está en modo de contenedor OLE; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 En el modo de contenedor OLE, se ocultan todos los paneles de acoplamiento y barras de herramientas de aplicación. Los paneles también se ocultan en este modo, si ha configurado [CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode) a `TRUE`.  
  
##  <a name="a-nameispointneardocksitea--cdockingmanagerispointneardocksite"></a><a name="ispointneardocksite"></a>CDockingManager::IsPointNearDockSite  
 Determina si un punto especificado está cerca del sitio de vinculación.  
  
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
 Especifica qué borde es el punto de cerca. Los valores posibles son `CBRS_ALIGN_LEFT`, `CBRS_ALIGN_RIGHT`, `CBRS_ALIGN_TOP` y `CBRS_ALIGN_BOTTOM`.  
  
 [out] `bOuterEdge`  
 `TRUE`Si el punto está cerca del borde exterior del sitio de vinculación; `FALSE` en caso contrario.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el punto está cerca del sitio de vinculación; de lo contrario, `FALSE`.  
  
##  <a name="a-nameisprintpreviewvalida--cdockingmanagerisprintpreviewvalid"></a><a name="isprintpreviewvalid"></a>CDockingManager::IsPrintPreviewValid  
 Determina si se establece el modo de vista previa de impresión.  
  
```  
BOOL IsPrintPreviewValid() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se establece el modo de vista previa de impresión; `FALSE` en caso contrario.  
  
##  <a name="a-nameloadstatea--cdockingmanagerloadstate"></a><a name="loadstate"></a>CDockingManager::LoadState  
 Carga el estado de acoplamiento del administrador del registro.  
  
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
 `TRUE`Si el estado de acoplamiento manager se ha cargado correctamente; de lo contrario, `FALSE`.  
  
##  <a name="a-namelockupdatea--cdockingmanagerlockupdate"></a><a name="lockupdate"></a>CDockingManager::LockUpdate  
 Bloquea la ventana dada.  
  
```  
void LockUpdate(BOOL bLock);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bLock`  
 `TRUE`Si la ventana está bloqueada; `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se bloquea una ventana, no se puede mover y no se vuelve a dibujar.  
  
##  <a name="a-namembhidedockingbarsincontainermodea--cdockingmanagermbhidedockingbarsincontainermode"></a><a name="m_bhidedockingbarsincontainermode"></a>CDockingManager::m_bHideDockingBarsInContainerMode  
 Especifica si el Administrador de acoplamiento oculta paneles en modo de contenedor OLE.  
  
```  
AFX_IMPORT_DATA static BOOL m_bHideDockingBarsInContainerMode;  
```  
  
### <a name="remarks"></a>Comentarios  
 Establezca este valor en `FALSE` si desea mantener todos los paneles acoplados al marco principal visible cuando la aplicación está en modo de contenedor OLE. De forma predeterminada, este valor es `TRUE`.  
  
##  <a name="a-namemdockmodeglobala--cdockingmanagermdockmodeglobal"></a><a name="m_dockmodeglobal"></a>CDockingManager::m_dockModeGlobal  
 Especifica el modo de acoplamiento global.  
  
```  
AFX_IMPORT_DATA static AFX_DOCK_TYPE m_dockModeGlobal;  
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, cada panel acoplable utiliza este modo de acoplamiento. Para obtener más información acerca de los valores que se puede establecer para este campo, consulte [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).  
  
##  <a name="a-namemndocksensitivitya--cdockingmanagermndocksensitivity"></a><a name="m_ndocksensitivity"></a>CDockingManager::m_nDockSensitivity  
 Especifica la distinción de acoplamiento.  
  
```  
AFX_IMPORT_DATA static int m_nDockSensitivity;  
```  
  
### <a name="remarks"></a>Comentarios  
 La sensibilidad de acoplamiento define cómo cerrar flotante panel puede llevar un panel acoplable, sitio de acoplamiento u otro panel antes de que el marco de trabajo cambia su estado acoplado.  
  
##  <a name="a-namemntimeoutbeforedockingbardocka--cdockingmanagermntimeoutbeforedockingbardock"></a><a name="m_ntimeoutbeforedockingbardock"></a>CDockingManager::m_nTimeOutBeforeDockingBarDock  
 Especifica el tiempo, en milisegundos, antes de que un panel acoplable está acoplado en el modo inmediato de acoplamiento.  
  
```  
static UINT m_nTimeOutBeforeDockingBarDock;  
```  
  
### <a name="remarks"></a>Comentarios  
 Antes de un panel se acopla, el marco de trabajo espera el período de tiempo especificado. Esto impide que el panel se acopla accidentalmente a una ubicación mientras el usuario todavía está arrastrando.  
  
##  <a name="a-namemntimeoutbeforetoolbardocka--cdockingmanagermntimeoutbeforetoolbardock"></a><a name="m_ntimeoutbeforetoolbardock"></a>CDockingManager::m_nTimeOutBeforeToolBarDock  
 Especifica el tiempo, en milisegundos, antes de que una barra de herramientas está acoplada a la ventana de marco principal.  
  
```  
static UINT m_nTimeOutBeforeToolBarDock;  
```  
  
### <a name="remarks"></a>Comentarios  
 Antes de que se acopla una barra de herramientas, el marco de trabajo espera el período de tiempo especificado. Esto impide que accidentalmente se acopla en una ubicación mientras el usuario todavía está arrastrando la barra de herramientas.  
  
##  <a name="a-nameonactivateframea--cdockingmanageronactivateframe"></a><a name="onactivateframe"></a>CDockingManager::OnActivateFrame  
 Llamado por el marco de trabajo cuando la ventana de marco se realiza activa o se desactiva.  
  
```  
virtual void OnActivateFrame(BOOL bActivate);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bActivate`  
 Si `TRUE`, se convierte en la ventana de marco activa; si `FALSE`, se desactiva la ventana de marco.  
  
##  <a name="a-nameonclosepopupmenua--cdockingmanageronclosepopupmenu"></a><a name="onclosepopupmenu"></a>CDockingManager::OnClosePopupMenu  
 Lo llama el marco cuando un menú emergente activo procesa un mensaje WM_DESTROY.  
  
```  
void OnClosePopupMenu();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo envía un mensaje WM_DESTROY cuando está a punto de cerrar la ventana principal actual. Invalide este método para controlar las notificaciones de `CMFCPopupMenu` objetos que pertenecen a la ventana de marco cuando una `CMFCPopupMenu` objeto procesos un `WM_DESTROY` mensaje.  
  
##  <a name="a-nameonmoveminiframea--cdockingmanageronmoveminiframe"></a><a name="onmoveminiframe"></a>CDockingManager::OnMoveMiniFrame  
 Llamado por el marco para mover una ventana de marco reducido.  
  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pFrame`  
 Puntero a una ventana de marco reducido.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método tiene éxito; de lo contrario, `FALSE`.  
  
##  <a name="a-nameonpanecontextmenua--cdockingmanageronpanecontextmenu"></a><a name="onpanecontextmenu"></a>CDockingManager::OnPaneContextMenu  
 Llamado por el marco cuando compila un menú con una lista de paneles.  
  
```  
void OnPaneContextMenu(CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 Especifica la ubicación del menú.  
  
##  <a name="a-namepanefrompointa--cdockingmanagerpanefrompoint"></a><a name="panefrompoint"></a>CDockingManager::PaneFromPoint  
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
 Especifica el punto, en coordenadas de pantalla para comprobar.  
  
 [in] `nSensitivity`  
 El valor para aumentar el rectángulo de la ventana de cada panel comprobado. Un panel satisface los criterios de búsqueda si el punto especificado está en esta región aumentada.  
  
 [in] `bExactBar`  
 `TRUE`para omitir la `nSensitivity` parámetro; en caso contrario, `FALSE`.  
  
 [in] `pRTCBarType`  
 Si no `NULL`, el método busca solo en los paneles del tipo especificado.  
  
 [in] `bCheckVisibility`  
 `TRUE`Para comprobar sólo los paneles visibles; de lo contrario, `FALSE`.  
  
 [out] `dwAlignment`  
 Si un panel se encuentra en el punto especificado, este parámetro contiene el lado del panel que era más cercano al punto especificado. Para obtener más información, vea la sección Comentarios.  
  
 [in] `pBarToIgnore`  
 Si no `NULL`, el método omite paneles especificados por este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 El [CBasePane](../../mfc/reference/cbasepane-class.md)-objeto derivado que contiene el punto especificado, o `NULL` si no se encontró ningún panel.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se devuelve la función y se encontró un panel, `dwAlignment` contiene la alineación del punto especificado. Por ejemplo, si el punto era más cercano a la parte superior del panel, `dwAlignment` está establecido en `CBRS_ALIGN_TOP`.  
  
##  <a name="a-nameprocesspanecontextmenucommanda--cdockingmanagerprocesspanecontextmenucommand"></a><a name="processpanecontextmenucommand"></a>CDockingManager::ProcessPaneContextMenuCommand  
 Llamado por el marco de trabajo para seleccionar o para desactivar una casilla de verificación para el comando especificado y vuelve a calcular el diseño de un panel que se muestra.  
  
```  
BOOL ProcessPaneContextMenuCommand(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 El identificador de una barra de control en el menú.  
  
 [in] `nCode`  
 El código de notificación de comando.  
  
 [in] `pExtra`  
 Un puntero a void que es convertir un puntero a `CCmdUI` si `nCode` es CN_UPDATE_COMMAND_UI.  
  
 [in] `pHandlerInfo`  
 Un puntero a una estructura de información. Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si `pEXtra` no es NULL y `nCode` es igual a CN_UPDATE_COMMAND_UI, o si hay una barra de controles con el parámetro `nID`.  
  
##  <a name="a-namerecalclayouta--cdockingmanagerrecalclayout"></a><a name="recalclayout"></a>CDockingManager::RecalcLayout  
 Vuelve a calcular el diseño interno de los controles que se presente en la lista de controles.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bNotify`  
 Este parámetro no se utiliza.  
  
##  <a name="a-namereleaseemptypanecontainersa--cdockingmanagerreleaseemptypanecontainers"></a><a name="releaseemptypanecontainers"></a>CDockingManager::ReleaseEmptyPaneContainers  
 Libera los contenedores de panel vacío.  
  
```  
void ReleaseEmptyPaneContainers();
```  
  
##  <a name="a-nameremovehiddenmditabbedbara--cdockingmanagerremovehiddenmditabbedbar"></a><a name="removehiddenmditabbedbar"></a>CDockingManager::RemoveHiddenMDITabbedBar  
 Quita oculta barra panel especificado.  
  
```  
void RemoveHiddenMDITabbedBar(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Un puntero a una barra de panel para quitar.  
  
##  <a name="a-nameremoveminiframea--cdockingmanagerremoveminiframe"></a><a name="removeminiframe"></a>CDockingManager::RemoveMiniFrame  
 Quita un intervalo especificado de la lista de fotogramas minivolcados.  
  
```  
virtual BOOL RemoveMiniFrame(CPaneFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Un puntero a un marco para quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se quita el marco especificado; `FALSE` en caso contrario.  
  
##  <a name="a-nameremovepanefromdockmanagera--cdockingmanagerremovepanefromdockmanager"></a><a name="removepanefromdockmanager"></a>CDockingManager::RemovePaneFromDockManager  
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
 Si `TRUE`, el panel se quita de la lista de barras Ocultar automáticamente. Si `FALSE`, el panel se quita de la lista de paneles regulares.  
  
 [in] `pBarReplacement`  
 Puntero a un panel que reemplazará al panel quitado.  
  
##  <a name="a-namereplacepanea--cdockingmanagerreplacepane"></a><a name="replacepane"></a>CDockingManager::ReplacePane  
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
  
##  <a name="a-nameresortminiframesforzordera--cdockingmanagerresortminiframesforzorder"></a><a name="resortminiframesforzorder"></a>CDockingManager::ResortMiniFramesForZOrder  
 Vuelve a ordenar los marcos en la lista de fotogramas minivolcados.  
  
```  
void ResortMiniFramesForZOrder();
```  
  
##  <a name="a-namesavestatea--cdockingmanagersavestate"></a><a name="savestate"></a>CDockingManager::SaveState  
 Guarda el estado del Administrador de acoplamiento en el registro.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Ruta de acceso a una clave del registro.  
  
 [in] `uiID`  
 En el identificador de jefe acoplamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el estado se guardó correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Guardar el estado del Administrador de acoplamiento en el registro implica guardar los Estados de las barras de controles, los Estados de las barras Ocultar automáticamente y los Estados de los marcos minivolcados presentes en el Administrador de acoplamiento.  
  
##  <a name="a-namesendmessagetominiframesa--cdockingmanagersendmessagetominiframes"></a><a name="sendmessagetominiframes"></a>CDockingManager::SendMessageToMiniFrames  
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
  
##  <a name="a-nameserializea--cdockingmanagerserialize"></a><a name="serialize"></a>CDockingManager::Serialize  
 El Administrador de acoplamiento se escribe en un archivo.  
  
```  
void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `ar`  
 Una referencia a un objeto de almacenamiento.  
  
### <a name="remarks"></a>Comentarios  
 Escribir el Administrador de acoplamiento en un archivo consiste en determinar el número de barras de controles y controles deslizantes de acoplamiento y escribir las barras de controles, los marcos minivolcados, las barras Ocultar automáticamente y las barras MDI con fichas en el archivo.  
  
##  <a name="a-namesetautohidezordera--cdockingmanagersetautohidezorder"></a><a name="setautohidezorder"></a>CDockingManager::SetAutohideZOrder  
 Establece el tamaño, ancho y alto de las barras de control y el panel especificado.  
  
```  
void SetAutohideZOrder(CDockablePane* pAHDockingBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pAHDockingBar`  
 Un puntero a un panel acoplable.  
  
##  <a name="a-namesetdockingmodea--cdockingmanagersetdockingmode"></a><a name="setdockingmode"></a>CDockingManager::SetDockingMode  
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
  
- `DT_STANDARD`-Estándar de acoplamiento modo como se implementa en Visual Studio .NET 2003. Se arrastran paneles sin un contexto de arrastre.  
  
- `DT_IMMEDIATE`-Modo de acoplamiento inmediato como se implementa en Microsoft Visio. Se arrastran paneles con un contexto de arrastre, pero no se muestran marcadores.  
  
- `DT_SMART`-Modo de acoplamiento de smart tal como se implementa en Visual Studio 2005. Se arrastran paneles con un contexto de arrastre y se muestran los marcadores inteligentes que muestran dónde se puede acoplar el panel.  
  
##  <a name="a-namesetdockstatea--cdockingmanagersetdockstate"></a><a name="setdockstate"></a>CDockingManager::SetDockState  
 Establece el estado de acoplamiento de las barras de controles, los marcos minivolcados y las barras Ocultar automáticamente.  
  
```  
virtual void SetDockState();
```  
  
##  <a name="a-namesetprintpreviewmodea--cdockingmanagersetprintpreviewmode"></a><a name="setprintpreviewmode"></a>CDockingManager::SetPrintPreviewMode  
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
  
##  <a name="a-namesetsmartdockingparamsa--cdockingmanagersetsmartdockingparams"></a><a name="setsmartdockingparams"></a>CDockingManager::SetSmartDockingParams  
 Establece los parámetros que definen el comportamiento de acoplamiento inteligente.  
  
```  
static void SetSmartDockingParams(CSmartDockingInfo& params);
```  
  
### <a name="parameters"></a>Parámetros  
 [in, out] `params`  
 Define los parámetros de acoplamiento inteligente.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método si desea personalizar la apariencia, el color o la forma de los marcadores de acoplamiento inteligentes.  
  
 Para utilizar la apariencia predeterminada de los marcadores de acoplamiento inteligente, pase una instancia no inicializada de [CSmartDockingInfo clase](../../mfc/reference/csmartdockinginfo-class.md) a `params`.  
  
##  <a name="a-nameshowdelayshowminiframesa--cdockingmanagershowdelayshowminiframes"></a><a name="showdelayshowminiframes"></a>CDockingManager::ShowDelayShowMiniFrames  
 Muestra u oculta las ventanas de los marcos minivolcados.  
  
```  
void ShowDelayShowMiniFrames(BOOL bshow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bShow`  
 `TRUE`Para activar la ventana del marco se muestra; `FALSE to` ocultar la ventana de marco.  
  
##  <a name="a-nameshowpanesa--cdockingmanagershowpanes"></a><a name="showpanes"></a>CDockingManager::ShowPanes  
 Muestra u oculta los paneles de las barras de control y ocultar automáticamente.  
  
```  
virtual BOOL ShowPanes(BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bShow`  
 `TRUE`para mostrar los paneles; `FALSE to` ocultar los paneles.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre es `FALSE`.  
  
##  <a name="a-namestartsdockinga--cdockingmanagerstartsdocking"></a><a name="startsdocking"></a>CDockingManager::StartSDocking  
 Inicia el acoplamiento inteligente de la ventana especificada según la alineación del Administrador de acoplamiento inteligente.  
  
```  
void StartSDocking(CWnd* pDockingWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDockingWnd`  
 Puntero a una ventana para acoplar.  
  
##  <a name="a-namestopsdockinga--cdockingmanagerstopsdocking"></a><a name="stopsdocking"></a>CDockingManager::StopSDocking  
 Se detiene inteligente de acoplamiento.  
  
```  
void StopSDocking();
```  
  
##  <a name="a-namegetsmartdockingthemea--cdockingmanagergetsmartdockingtheme"></a><a name="getsmartdockingtheme"></a>CDockingManager::GetSmartDockingTheme  
 Un método estático que devuelve un tema que se usa para mostrar marcadores de acoplamiento inteligente.  
  
```  
static AFX_SMARTDOCK_THEME __stdcall GetSmartDockingTheme();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores enumerados siguientes: AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Clase CFrameWndEx](../../mfc/reference/cframewndex-class.md)   
 [Clase CDockablePane](../../mfc/reference/cdockablepane-class.md)   
 [Clase CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)

