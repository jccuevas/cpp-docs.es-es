---
title: Clase COleIPFrameWndEx | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleIPFrameWndEx
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::AddDockSite
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::AddPane
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::AdjustDockingLayout
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::DockPane
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::DockPaneLeftOf
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::EnableAutoHidePanes
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::EnableDocking
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::EnablePaneMenu
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetActivePopup
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetContainerFrameWindow
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetDefaultResId
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetDockFrame
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetDockingManager
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetMainFrame
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetMenuBar
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetPane
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetTearOffBars
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetToolbarButtonToolTipText
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::InsertPane
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::IsMenuBarAvailable
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::IsPointNearDockSite
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::LoadFrame
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnCloseDockingPane
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnCloseMiniFrame
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnClosePopupMenu
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnCmdMsg
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnDrawMenuImage
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnDrawMenuLogo
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnMenuButtonToolHitTest
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnMoveMiniFrame
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnSetPreviewMode
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnShowCustomizePane
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnShowPanes
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnShowPopupMenu
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnTearOffMenu
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::PaneFromPoint
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::PreTranslateMessage
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::RecalcLayout
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::RemovePaneFromDockManager
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::SetDockState
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::SetupToolbarMenu
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::ShowPane
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::WinHelpA
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::InitUserToobars
dev_langs:
- C++
helpviewer_keywords:
- COleIPFrameWndEx class
ms.assetid: ebff1560-a1eb-4854-af00-95d4a192bd55
caps.latest.revision: 34
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 5eec8e3a9cc4ad71a1ee3de9f6d5f25cffef1242
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="coleipframewndex-class"></a>Clase COleIPFrameWndEx
La clase `COleIPFrameWndEx` implementa un contenedor OLE compatible con MFC. Debe derivar la clase de ventana de marco en contexto de la aplicación desde el `COleIPFrameWndEx` (clase), en lugar de derivar desde la [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md)clase. 
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]   
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleIPFrameWndEx : public COleIPFrameWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleIPFrameWndEx::AddDockSite](#adddocksite)||  
|[COleIPFrameWndEx::AddPane](#addpane)||  
|[COleIPFrameWndEx::AdjustDockingLayout](#adjustdockinglayout)||  
|[COleIPFrameWndEx::DockPane](#dockpane)||  
|[COleIPFrameWndEx::DockPaneLeftOf](#dockpaneleftof)|Acopla un panel a la izquierda de otro panel.|  
|[COleIPFrameWndEx::EnableAutoHidePanes](#enableautohidepanes)||  
|[COleIPFrameWndEx::EnableDocking](#enabledocking)||  
|[COleIPFrameWndEx::EnablePaneMenu](#enablepanemenu)||  
|[COleIPFrameWndEx::GetActivePopup](#getactivepopup)|Devuelve un puntero al menú emergente mostrado actualmente.|  
|[COleIPFrameWndEx::GetContainerFrameWindow](#getcontainerframewindow)||  
|[COleIPFrameWndEx::GetDefaultResId](#getdefaultresid)|Devuelve el identificador de recurso de la ventana de marco se que especificó al cargar la ventana.|  
|[COleIPFrameWndEx::GetDockFrame](#getdockframe)||  
|[COleIPFrameWndEx::GetDockingManager](#getdockingmanager)||  
|[COleIPFrameWndEx::GetMainFrame](#getmainframe)||  
|[COleIPFrameWndEx::GetMenuBar](#getmenubar)|Devuelve un puntero al objeto de barra de menú asociado a la ventana de marco.|  
|[COleIPFrameWndEx::GetPane](#getpane)||  
|[COleIPFrameWndEx::GetTearOffBars](#gettearoffbars)|Devuelve una lista de objetos de panel que están en un estado desplazable.|  
|[COleIPFrameWndEx::GetToolbarButtonToolTipText](#gettoolbarbuttontooltiptext)|Lo llama el marco de trabajo antes de que aparezca la información sobre herramientas para un botón.|  
|[COleIPFrameWndEx::InsertPane](#insertpane)||  
|[COleIPFrameWndEx::IsMenuBarAvailable](#ismenubaravailable)|Determina si el puntero al objeto de barra de menú no es `NULL`.|  
|[COleIPFrameWndEx::IsPointNearDockSite](#ispointneardocksite)||  
|[COleIPFrameWndEx::LoadFrame](#loadframe)|(Invalida `COleIPFrameWnd::LoadFrame`).|  
|[COleIPFrameWndEx::OnCloseDockingPane](#onclosedockingpane)||  
|[COleIPFrameWndEx::OnCloseMiniFrame](#oncloseminiframe)||  
|[COleIPFrameWndEx::OnClosePopupMenu](#onclosepopupmenu)|Lo llama el marco cuando un menú emergente activo procesa un mensaje WM_DESTROY.|  
|[COleIPFrameWndEx::OnCmdMsg](#oncmdmsg)|(Invalida `CFrameWnd::OnCmdMsg`).|  
|[COleIPFrameWndEx::OnDrawMenuImage](#ondrawmenuimage)|Lo llama el marco de trabajo cuando se dibuja la imagen asociada a un elemento de menú.|  
|[COleIPFrameWndEx::OnDrawMenuLogo](#ondrawmenulogo)|Llamado por el marco cuando una [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)objeto procesa un mensaje WM_PAINT.|  
|[COleIPFrameWndEx::OnMenuButtonToolHitTest](#onmenubuttontoolhittest)|Llamado por el marco cuando una [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)mensaje WM_NCHITTEST de procesos de objeto.|  
|[COleIPFrameWndEx::OnMoveMiniFrame](#onmoveminiframe)||  
|[COleIPFrameWndEx::OnSetPreviewMode](#onsetpreviewmode)|Llame a esta función miembro para establecer la ventana de marco principal de la aplicación dentro y fuera del modo de vista previa de impresión. (Invalida [CFrameWnd::OnSetPreviewMode](../../mfc/reference/cframewnd-class.md#onsetpreviewmode).)|  
|[COleIPFrameWndEx::OnShowCustomizePane](#onshowcustomizepane)||  
|[COleIPFrameWndEx::OnShowPanes](#onshowpanes)||  
|[COleIPFrameWndEx::OnShowPopupMenu](#onshowpopupmenu)|Lo llama el marco de trabajo cuando se activa un menú emergente.|  
|[COleIPFrameWndEx::OnTearOffMenu](#ontearoffmenu)|Lo llama el marco de trabajo cuando se activa un menú con barra desplazable.|  
|[COleIPFrameWndEx::PaneFromPoint](#panefrompoint)||  
|[COleIPFrameWndEx::PreTranslateMessage](#pretranslatemessage)|(Invalida `COleIPFrameWnd::PreTranslateMessage`).|  
|[COleIPFrameWndEx::RecalcLayout](#recalclayout)|(Invalida `COleIPFrameWnd::RecalcLayout`).|  
|[COleIPFrameWndEx::RemovePaneFromDockManager](#removepanefromdockmanager)||  
|[COleIPFrameWndEx::SetDockState](#setdockstate)|Aplica el estado de acoplamiento especificado a los paneles que pertenecen a la ventana de marco.|  
|[COleIPFrameWndEx::SetupToolbarMenu](#setuptoolbarmenu)|Modifica un objeto de barra de herramientas al buscar elementos ficticios y reemplazarlos con los elementos definidos por el usuario especificados.|  
|[COleIPFrameWndEx::ShowPane](#showpane)||  
|[COleIPFrameWndEx::WinHelpA](#winhelpa)|Lo llama el marco para iniciar la aplicación o la ayuda contextual de WinHelp.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleIPFrameWndEx::InitUserToobars](#initusertoobars)|Indica al marco que inicialice un rango de identificadores de control que están asignados a las barras de herramientas definidas por el usuario.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo crear subclases de una instancia de la clase `COleIPFrameWndEx` e invalidar sus métodos. En el ejemplo se muestra cómo invalidar el método `OnDestory` , el método `RepositionFrame` , el método `RecalcLayout` y el método `CalcWindowRect` . Este fragmento de código forma parte de la [ejemplo de panel de palabras](../../visual-cpp-samples.md).  
  
 [!code-cpp[1 NVC_MFC_WordPad](../../mfc/reference/codesnippet/cpp/coleipframewndex-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md)  
  
 [COleIPFrameWndEx](../../mfc/reference/coleipframewndex-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxoleipframewndex.h  
  
##  <a name="adddocksite"></a>COleIPFrameWndEx::AddDockSite  

  
```  
void AddDockSite();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="addpane"></a>COleIPFrameWndEx::AddPane  

  
```  
BOOL AddPane(
    CBasePane* pControlBar,  
    BOOL bTail = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pControlBar`  
 [in] `bTail`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="adjustdockinglayout"></a>COleIPFrameWndEx::AdjustDockingLayout  

  
```  
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hdwp`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="dockpane"></a>COleIPFrameWndEx::DockPane  

  
```  
void DockPane(
    CBasePane* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 [in] `nDockBarID`  
 [in] `lpRect`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="dockpaneleftof"></a>COleIPFrameWndEx::DockPaneLeftOf  
 Acopla un panel a la izquierda de otro panel.  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBar,  
    CPane* pLeftOf);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Un puntero al panel para acoplar.  
  
 [in] `pLeftOf`  
 Un puntero al panel que actúa como origen.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si la operación es correcta. De lo contrario, devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para acoplar varios objetos de panel en un orden predefinido. Este método acopla el panel especificado por `pBar` a la izquierda del panel especificado por `pLeftOf`.  
  
##  <a name="enableautohidepanes"></a>COleIPFrameWndEx::EnableAutoHidePanes  

  
```  
BOOL EnableAutoHidePanes(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwDockStyle`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="enabledocking"></a>COleIPFrameWndEx::EnableDocking  

  
```  
BOOL EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwDockStyle`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="enablepanemenu"></a>COleIPFrameWndEx::EnablePaneMenu  

  
```  
void EnablePaneMenu(
    BOOL bEnable,  
    UINT uiCustomizeCmd,  
    const CString& strCustomizeLabel,  
    UINT uiViewToolbarsMenuEntryID,  
    BOOL bContextMenuShowsToolbarsOnly = FALSE,  
    BOOL bViewMenuShowsToolbarsOnly = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 [in] `uiCustomizeCmd`  
 [in] `strCustomizeLabel`  
 [in] `uiViewToolbarsMenuEntryID`  
 [in] `bContextMenuShowsToolbarsOnly`  
 [in] `bViewMenuShowsToolbarsOnly`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getactivepopup"></a>COleIPFrameWndEx::GetActivePopup  
 Devuelve un puntero al menú emergente mostrado actualmente.  
  
```  
CMFCPopupMenu* GetActivePopup() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al menú emergente activo; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para obtener un puntero a la [CMFCPopupMenu clase](../../mfc/reference/cmfcpopupmenu-class.md) objeto que se muestra actualmente.  
  
##  <a name="getcontainerframewindow"></a>COleIPFrameWndEx::GetContainerFrameWindow  

  
```  
COleCntrFrameWndEx* GetContainerFrameWindow();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getdefaultresid"></a>COleIPFrameWndEx::GetDefaultResId  
 Devuelve el identificador de recurso de menú que especifica cuando la ventana de marco carga el menú.  
  
```  
UINT GetDefaultResId() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el identificador de recurso del menú o 0 si la ventana de marco no tiene ninguna barra de menús.  
  
### <a name="remarks"></a>Comentarios  
 Llamada a esta función para recuperar el identificador de recurso que especifica cuando la ventana de marco carga el recurso de menú llamando a `COleIPFrameWndEx::LoadFrame`.  
  
##  <a name="getdockframe"></a>COleIPFrameWndEx::GetDockFrame  

  
```  
CFrameWnd* GetDockFrame();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getdockingmanager"></a>COleIPFrameWndEx::GetDockingManager  

  
```  
CDockingManager* GetDockingManager();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getmainframe"></a>COleIPFrameWndEx::GetMainFrame  

  
```  
CFrameWnd* GetMainFrame();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getmenubar"></a>COleIPFrameWndEx::GetMenuBar  
 Devuelve un puntero al objeto de barra de menú asociado a la ventana de marco.  
  
```  
const CMFCMenuBar* GetMenuBar() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto de barra de menús.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para recuperar un puntero al objeto de barra de menú que pertenece a la `COleIPFrameWndEx` objeto.  
  
##  <a name="getpane"></a>COleIPFrameWndEx::GetPane  

  
```  
CBasePane* GetPane(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gettearoffbars"></a>COleIPFrameWndEx::GetTearOffBars  
 Devuelve una lista de objetos de panel que están en un estado desplazable.  
  
```  
const CObList& GetTearOffBars() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a un `CObList` objeto que contiene una colección de punteros a la [CBasePane clase](../../mfc/reference/cbasepane-class.md)-objetos derivados.  
  
### <a name="remarks"></a>Comentarios  
 El `COleIPFrameWndEx` objeto mantiene la colección de menús desplazable como una lista de [CBasePane clase](../../mfc/reference/cbasepane-class.md)-objetos derivados. Utilice este método para recuperar una referencia a esta lista.  
  
##  <a name="gettoolbarbuttontooltiptext"></a>COleIPFrameWndEx::GetToolbarButtonToolTipText  
 Lo llama el marco de trabajo antes de que aparezca la información sobre herramientas para un botón.  
  
```  
virtual BOOL GetToolbarButtonToolTipText(
    CMFCToolBarButton* pButton,  
    CString& strTTText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Puntero al botón.  
  
 [in] `strTTText`  
 Puntero al texto de información sobre herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para personalizar la presentación de información sobre herramientas en los botones de barra de herramientas.  
  
##  <a name="initusertoobars"></a>COleIPFrameWndEx::InitUserToobars  
 Especifica un intervalo de identificadores que el marco de trabajo se asigna a las barras de herramientas definidas por el usuario de control.  
  
```  
void InitUserToolbars(
    LPCTSTR lpszRegEntry,   
    UINT uiUserToolbarFirst,   
    UINT uiUserToolbarLast)  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszRegEntry`  
 La entrada del registro donde la biblioteca almacena la configuración de la barra de herramientas de usuario.  
  
 [in] `uiUserToolbarFirst`  
 Id. de control que se asigna a la primera barra de herramientas definidas por el usuario.  
  
 [in] `uiUserToolbarLast`  
 Id. de control que se asigna a la última barra de herramientas definidas por el usuario.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para inicializar un intervalo de identificadores de control para la asignación de las barras de herramientas que los usuarios se definen dinámicamente. Los parámetros `uiUserToolbarFirst` y `uiUserToolbarLast` definir un intervalo de identificadores de control de barra de herramientas permitidas. Para deshabilitar la creación de barras de herramientas definidas por el usuario, establezca `uiUserToolbarFirst` o `uiUserToolbarLast` en -1.  
  
##  <a name="insertpane"></a>COleIPFrameWndEx::InsertPane  

  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pControlBar`  
 [in] `pTarget`  
 [in] `bAfter`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ismenubaravailable"></a>COleIPFrameWndEx::IsMenuBarAvailable  
 Determina si no es el puntero al objeto de barra de menú`NULL`  
  
```  
BOOL IsMenuBarAvailable() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Valor de devuelve distinto de cero si la ventana de marco tiene una barra de menús; de lo contrario, devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para determinar si mantiene la ventana de marco no `NULL` puntero a su objeto de barra de menús.  
  
##  <a name="ispointneardocksite"></a>COleIPFrameWndEx::IsPointNearDockSite  

  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 [in] `dwBarAlignment`  
 [in] `bOuterEdge`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="loadframe"></a>COleIPFrameWndEx::LoadFrame  

  
```  
virtual BOOL LoadFrame(
    UINT nIDResource,  
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,  
    CWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIDResource`  
 [in] `dwDefaultStyle`  
 [in] `pParentWnd`  
 [in] `pContext`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onclosedockingpane"></a>COleIPFrameWndEx::OnCloseDockingPane  

  
```  
virtual BOOL OnCloseDockingPane(CDockablePane*);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `CDockablePane*`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="oncloseminiframe"></a>COleIPFrameWndEx::OnCloseMiniFrame  

  
```  
virtual BOOL OnCloseMiniFrame(CPaneFrameWnd*);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `CPaneFrameWnd*`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onclosepopupmenu"></a>COleIPFrameWndEx::OnClosePopupMenu  
 Llamado por el marco cuando procesa un menú emergente activo un `WM_DESTROY` mensaje.  
  
```  
virtual void OnClosePopupMenu(CMFCPopupMenu* pMenuPopup);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMenuPopup`  
 Un puntero al objeto de menú emergente.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para recibir notificaciones de `CMFCPopupMenu` objetos cuando procesan `WM_DESTROY` mensajes.  
  
##  <a name="oncmdmsg"></a>COleIPFrameWndEx::OnCmdMsg  

  
```  
virtual BOOL OnCmdMsg(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 [in] `nCode`  
 [in] `pExtra`  
 [in] `pHandlerInfo`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondrawmenuimage"></a>COleIPFrameWndEx::OnDrawMenuImage  
 Llamado por el marco de trabajo cuando se dibuja la imagen que está asociada a un elemento de menú.  
  
```  
virtual BOOL OnDrawMenuImage(
    CDC* pDC,  
    const CMFCToolBarMenuButton* pMenuButton,  
    const CRect& rectImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero al contexto de dispositivo.  
  
 [in] `pMenuButton`  
 Puntero al botón de menú.  
  
 [in] `rectImage`  
 La imagen asociada al elemento de menú.  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada no hace nada y devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método si desea personalizar la imagen de dibujo para los elementos de menú que pertenecen a la barra de menús que pertenecen a la `COleIPFrameWndEx`-objeto derivado.  
  
##  <a name="ondrawmenulogo"></a>COleIPFrameWndEx::OnDrawMenuLogo  
 Llamado por el marco cuando una [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)objeto procesos un `WM_PAINT` mensaje.  
  
```  
virtual void OnDrawMenuLogo(
    CDC* pDC,  
    CMFCPopupMenu* pMenu,  
    const CRect& rectLogo);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero al contexto de dispositivo.  
  
 [in] `pMenu`  
 Puntero al objeto de menú emergente.  
  
 [in] `rectLogo`  
 Puntero para el logotipo que desea mostrar.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para mostrar un logotipo en el menú emergente asociado con la barra de menús que pertenecen a la `COleIPFrameWndEx`-objeto derivado. La implementación predeterminada no hace nada.  
  
##  <a name="onmenubuttontoolhittest"></a>COleIPFrameWndEx::OnMenuButtonToolHitTest  
 Llamado por el marco cuando una [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)objeto procesos un `WM_NCHITTEST` mensaje.  
  
```  
virtual BOOL OnMenuButtonToolHitTest(
    CMFCToolBarButton* pButton,  
    TOOLINFO* pTI);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] pButton  
 Puntero a un botón de menú.  
  
 [out] pTI  
 Puntero a una estructura `TOOLINFO`.  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada no hace nada y devuelve 0. La implementación debe devolver un valor distinto de cero si se llena el `pTI` parámetro.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para proporcionar información sobre herramientas acerca de un elemento de menú específico.  
  
##  <a name="onmoveminiframe"></a>COleIPFrameWndEx::OnMoveMiniFrame  

  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pFrame`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onsetpreviewmode"></a>COleIPFrameWndEx::OnSetPreviewMode  

  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bPreview`  
 [in] `pState`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onshowcustomizepane"></a>COleIPFrameWndEx::OnShowCustomizePane  

  
```  
virtual BOOL OnShowCustomizePane(
    CMFCPopupMenu* pMenuPane,  
    UINT uiToolbarID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMenuPane`  
 [in] `uiToolbarID`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onshowpanes"></a>COleIPFrameWndEx::OnShowPanes  

  
```  
virtual BOOL OnShowPanes(BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bShow`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onshowpopupmenu"></a>COleIPFrameWndEx::OnShowPopupMenu  
 Llamado por el marco de trabajo cuando se muestra un menú emergente.  
  
```  
virtual BOOL OnShowPopupMenu(CMFCPopupMenu* pMenuPopup);
```  
  
### <a name="parameters"></a>Parámetros  
 `[in] pMenuPopup`  
 Puntero al menú emergente que se mostrará.  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada no hace nada y devuelve un valor distinto de cero. La implementación debe devolver `FALSE` si no se puede mostrar el menú emergente.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para personalizar la presentación de un menú emergente. Por ejemplo, puede cambiar los botones de menú para los botones de menú de color o inicializar barras desplazable.  
  
##  <a name="ontearoffmenu"></a>COleIPFrameWndEx::OnTearOffMenu  
 Lo llama el marco de trabajo cuando el usuario selecciona un menú que tiene una barra desplazable.  
  
```  
virtual BOOL OnTearOffMenu(
    CMFCPopupMenu* pMenuPopup,  
    CPane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMenuPopup`  
 Un puntero al menú emergente que el usuario seleccionado.  
  
 [in] `pBar`  
 Un puntero al panel que contiene el menú.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si desea que el marco de trabajo para activar el menú emergente; de lo contrario, `FALSE`. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si desea personalizar la configuración de la barra desplazable.  
  
##  <a name="panefrompoint"></a>COleIPFrameWndEx::PaneFromPoint  

  
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
 [in] `point`  
 [in] `nSensitivity`  
 [in] `bExactBar`  
 [in] `pRTCBarType`  
 [in] `dwAlignment`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="pretranslatemessage"></a>COleIPFrameWndEx::PreTranslateMessage  

  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMsg`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="recalclayout"></a>COleIPFrameWndEx::RecalcLayout  

  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bNotify`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="removepanefromdockmanager"></a>COleIPFrameWndEx::RemovePaneFromDockManager  

  
```  
void RemovePaneFromDockManager(
    CBasePane* pControlBar,  
    BOOL bDestroy,  
    BOOL bAdjustLayout,  
    BOOL bAutoHide,  
    CBasePane* pBarReplacement);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pControlBar`  
 [in] `bDestroy`  
 [in] `bAdjustLayout`  
 [in] `bAutoHide`  
 [in] `pBarReplacement`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setdockstate"></a>COleIPFrameWndEx::SetDockState  
 Se aplica el estado de acoplamiento especificado en paneles de la ventana de marco.  
  
```  
void SetDockState(const CDockState& state);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `state`  
 Especifica el estado de acoplamiento.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para especificar un nuevo estado de acoplamiento para paneles que pertenecen a la `COleIPFrameWndEx` objeto.  
  
##  <a name="setuptoolbarmenu"></a>COleIPFrameWndEx::SetupToolbarMenu  
 Modifica un objeto de barra de herramientas al buscar elementos ficticios y reemplazarlos con los elementos definidos por el usuario especificados.  
  
```  
void SetupToolbarMenu(
    CMenu& menu,  
    const UINT uiViewUserToolbarCmdFirst,  
    const UINT uiViewUserToolbarCmdLast);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `menu`  
 Una referencia a un [CMenu](../../mfc/reference/cmenu-class.md) objeto que desee modificar.  
  
 [in] `uiViewUserToolbarCmdFirst`  
 Especifica el primer comando definido por el usuario.  
  
 [in] `uiViewUserToolbarCmdLast`  
 Especifica el último comando definido por el usuario.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="showpane"></a>COleIPFrameWndEx::ShowPane  

  
```  
void ShowPane(
    CBasePane* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 [in] `bShow`  
 [in] `bDelay`  
 [in] `bActivate`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="winhelpa"></a>COleIPFrameWndEx::WinHelpA  
 Lo llama el marco para iniciar la aplicación o la ayuda contextual de WinHelp.  
  
```  
virtual void WinHelp(
    DWORD dwData,  
    UINT nCmd = HELP_CONTEXT);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] dwData  
 Especifica datos según sea necesario para el tipo de ayuda indicado por `nCmd`.  
  
 [in] `nCmd`  
 Especifica el tipo de ayuda solicitado. Para obtener una lista de valores posibles y cómo afectan al parámetro `dwData` , consulte la [función WinHelp](http://msdn.microsoft.com/library/windows/desktop/bb762267) en Windows SDK.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CFrameWndEx](../../mfc/reference/cframewndex-class.md)   
 [CMDIFrameWndEx Class](../../mfc/reference/cmdiframewndex-class.md)

