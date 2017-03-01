---
title: Clase CMDIFrameWndEx | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMDIFrameWndEx.AddDockSite
- CMDIFrameWndEx
- CMDIFrameWndEx::AddDockSite
dev_langs:
- C++
helpviewer_keywords:
- CMDIFrameWndEx class
ms.assetid: dbcafcb3-9a7a-4f11-9dfe-ba57565c81d0
caps.latest.revision: 42
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: b9946f59b9ed789604ac6a02d2148188831bae56
ms.lasthandoff: 02/24/2017

---
# <a name="cmdiframewndex-class"></a>CMDIFrameWndEx (Clase)
Amplía la funcionalidad de [CMDIFrameWnd](../../mfc/reference/cframewnd-class.md), una ventana de marco de interfaz de documentos múltiples (MDI).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMDIFrameWndEx : public CMDIFrameWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMDIFrameWndEx::ActiveItemRecalcLayout](#activeitemrecalclayout)|Vuelve a calcular el diseño del elemento activo.|  
|`CMDIFrameWndEx::AddDockSite`|No se utiliza este método.|  
|[CMDIFrameWndEx::AddPane](#addpane)|Registra un panel con el Administrador de acoplamiento.|  
|[CMDIFrameWndEx::AdjustClientArea](#adjustclientarea)|Reduce el área de cliente para permitir un borde.|  
|[CMDIFrameWndEx::AdjustDockingLayout](#adjustdockinglayout)|Vuelve a calcular el diseño de todos los paneles acoplados.|  
|[CMDIFrameWndEx::AreMDITabs](#aremditabs)|Determina si está habilitada la característica de las fichas de MDI o la característica grupos de fichas de MDI.|  
|[CMDIFrameWndEx::CanCovertControlBarToMDIChild](#cancovertcontrolbartomdichild)|Llamado por el marco de trabajo para determinar si la ventana de marco puede convertir paneles de acoplamiento en documentos con fichas.|  
|[CMDIFrameWndEx::ControlBarToTabbedDocument](#controlbartotabbeddocument)|Convierte el panel de acoplamiento especificado en un documento con fichas.|  
|[CMDIFrameWndEx::CreateDocumentWindow](#createdocumentwindow)|Crea una ventana de documento secundaria.|  
|[CMDIFrameWndEx::CreateNewWindow](#createnewwindow)|Llamado por el marco para crear una nueva ventana.|  
|`CMDIFrameWndEx::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMDIFrameWndEx::DockPane](#dockpane)|Acopla el panel especificado en la ventana de marco.|  
|[CMDIFrameWndEx::DockPaneLeftOf](#dockpaneleftof)|Acopla un panel a la izquierda de otro panel.|  
|[CMDIFrameWndEx::EnableAutoHidePanes](#enableautohidepanes)|Permite oculta automáticamente el modo de los paneles al que se acoplan a los costados especificados de la ventana de marco principal.|  
|[CMDIFrameWndEx::EnableDocking](#enabledocking)|Permite acoplar los paneles que pertenecen a la ventana de marco MDI.|  
|[CMDIFrameWndEx::EnableFullScreenMainMenu](#enablefullscreenmainmenu)|Muestra u oculta el menú principal en modo de pantalla completa.|  
|[CMDIFrameWndEx::EnableFullScreenMode](#enablefullscreenmode)|Habilita el modo de pantalla completa para la ventana de marco.|  
|[CMDIFrameWndEx::EnableLoadDockState](#enableloaddockstate)|Habilita o deshabilita la carga del estado de acoplamiento.|  
|[CMDIFrameWndEx::EnableMDITabbedGroups](#enablemditabbedgroups)|Habilita o deshabilita la característica grupos de fichas de MDI.|  
|[CMDIFrameWndEx::EnableMDITabs](#enablemditabs)|Habilita o deshabilita la característica de las fichas de MDI. Cuando está habilitada, la ventana de marco muestra una ficha para cada ventana secundaria MDI.|  
|[CMDIFrameWndEx::EnableMDITabsLastActiveActivation](#enablemditabslastactiveactivation)|Especifica si se debe activar la última ficha que se active cuando el usuario cierra la ficha actual.|  
|[CMDIFrameWndEx::EnablePaneMenu](#enablepanemenu)|Habilita o deshabilita la creación automática y administración del menú emergente del panel, que muestra una lista de paneles de la aplicación.  .|  
|[CMDIFrameWndEx::EnableWindowsDialog](#enablewindowsdialog)|Inserta un elemento de menú cuyo identificador de comando llama un [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) cuadro de diálogo.|  
|[CMDIFrameWndEx::GetActivePopup](#getactivepopup)|Devuelve un puntero al menú emergente mostrado actualmente.|  
|[CMDIFrameWndEx::GetPane](#getpane)|Devuelve un puntero al panel que tiene el identificador del control especificado.|  
|[CMDIFrameWndEx::GetDefaultResId](#getdefaultresid)|Devuelve el identificador de recursos compartidos de la ventana de marco MDI.|  
|[CMDIFrameWndEx::GetMDITabGroups](#getmditabgroups)|Devuelve que una lista de MDI ventanas de fichas.|  
|[CMDIFrameWndEx::GetMDITabs](#getmditabs)|Devuelve una referencia a la ventana con fichas subrayada.|  
|[CMDIFrameWndEx::GetMDITabsContextMenuAllowedItems](#getmditabscontextmenualloweditems)|Devuelve una combinación de indicadores que determina qué elementos de menú contextual son válidos cuando está habilitada la característica grupos de fichas de MDI.|  
|[CMDIFrameWndEx::GetMenuBar](#getmenubar)|Devuelve un puntero a un objeto de la barra de menú asociado a la ventana de marco.|  
|[CMDIFrameWndEx::GetRibbonBar](#getribbonbar)|Recupera el control de barra de la cinta de opciones para el marco.|  
|[CMDIFrameWndEx::GetTearOffBars](#gettearoffbars)|Devuelve una lista de [CPane](../../mfc/reference/cpane-class.md)-derivado de objetos que están en un estado.|  
|`CMDIFrameWndEx::GetThisClass`|Llamado por el marco para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMDIFrameWndEx::GetToolbarButtonToolTipText](#gettoolbarbuttontooltiptext)|Llamado por el marco de trabajo cuando la aplicación muestra la información sobre herramientas para un botón de barra de herramientas.|  
|[CMDIFrameWndEx::InsertPane](#insertpane)|El panel especificado se registra con el Administrador de acoplamiento.|  
|[CMDIFrameWndEx::IsFullScreen](#isfullscreen)|Determina si la ventana de marco está en modo de pantalla completa.|  
|[CMDIFrameWndEx::IsMDITabbedGroup](#ismditabbedgroup)|Determina si está habilitada la característica grupos de fichas de MDI.|  
|[CMDIFrameWndEx::IsMemberOfMDITabGroup](#ismemberofmditabgroup)|Determina si la ventana con fichas especificada está en la lista de windows que se encuentran en grupos con fichas de MDI.|  
|[CMDIFrameWndEx::IsMenuBarAvailable](#ismenubaravailable)|Determina si la ventana de marco tiene una barra de menús.|  
|[CMDIFrameWndEx::IsPointNearDockSite](#ispointneardocksite)|Determina si un punto especificado está cerca del sitio de vinculación.|  
|[CMDIFrameWndEx::IsPrintPreview](#isprintpreview)|Determina si la ventana de marco está en modo de vista previa de impresión.|  
|[CMDIFrameWndEx::LoadFrame](#loadframe)|Crea una ventana de marco de información de recursos. (Invalida `CMDIFrameWnd::LoadFrame`).|  
|[CMDIFrameWndEx::LoadMDIState](#loadmdistate)|Carga el diseño de los grupos de fichas de MDI especificado y la lista de documentos abiertos previamente.|  
|[CMDIFrameWndEx::MDITabMoveToNextGroup](#mditabmovetonextgroup)|Mueve la ficha activa de la ventana activa con pestañas al grupo de fichas siguiente o anterior.|  
|[CMDIFrameWndEx::MDITabNewGroup](#mditabnewgroup)|Crea un nuevo grupo con pestañas que tiene una sola ventana.|  
|[CMDIFrameWndEx::NegotiateBorderSpace](#negotiateborderspace)|Espacio del borde de una ventana de marco se negocia durante la activación en contexto OLE.|  
|[CMDIFrameWndEx::OnCloseDockingPane](#onclosedockingpane)|Llamado por el marco de trabajo cuando el usuario hace clic en el **cerrar** botón en un panel acoplable.|  
|[CMDIFrameWndEx::OnCloseMiniFrame](#oncloseminiframe)|Llamado por el marco de trabajo cuando el usuario hace clic en el **cerrar** botón en una ventana de marco flotante flotante.|  
|[CMDIFrameWndEx::OnClosePopupMenu](#onclosepopupmenu)|Llamado por el marco cuando procesa un menú emergente activo un `WM_DESTROY` mensaje.|  
|[CMDIFrameWndEx::OnCmdMsg](#oncmdmsg)|Llamado por el marco de trabajo para enrutar y enviar mensajes de comando y actualizar objetos de interfaz de usuario de comandos.|  
|[CMDIFrameWndEx::OnDrawMenuImage](#ondrawmenuimage)|Lo llama el marco de trabajo cuando se dibuja la imagen asociada a un elemento de menú.|  
|[CMDIFrameWndEx::OnDrawMenuLogo](#ondrawmenulogo)|Llamado por el marco cuando una [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)procesos un `WM_PAINT` mensaje.|  
|[CMDIFrameWndEx::OnEraseMDIClientBackground](#onerasemdiclientbackground)|Llamado por el marco cuando los procesos de ventana de marco de la MDI un `WM_ERASEBKGND` mensaje.|  
|[CMDIFrameWndEx::OnMenuButtonToolHitTest](#onmenubuttontoolhittest)|Llamado por el marco cuando una [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)objeto procesos un `WM_NCHITTEST` mensaje.|  
|[CMDIFrameWndEx::OnMoveMiniFrame](#onmoveminiframe)|Llamado por el marco para mover una ventana de marco reducido.|  
|[CMDIFrameWndEx::OnSetPreviewMode](#onsetpreviewmode)|Establece el modo de vista previa de impresión de ventana de marco principal de la aplicación. (Invalida [CFrameWnd::OnSetPreviewMode](../../mfc/reference/cframewnd-class.md#onsetpreviewmode).)|  
|[CMDIFrameWndEx::OnShowCustomizePane](#onshowcustomizepane)|Lo llama el marco de trabajo cuando se activa un panel personalizar rápida.|  
|[CMDIFrameWndEx::OnShowMDITabContextMenu](#onshowmditabcontextmenu)|Llamado por el marco de trabajo cuando un menú contextual debe mostrarse en una de las fichas. (Válido para grupos con pestañas MDI sólo).|  
|[CMDIFrameWndEx::OnShowPanes](#onshowpanes)|Llamado por el marco de trabajo para mostrar u ocultar paneles.|  
|[CMDIFrameWndEx::OnShowPopupMenu](#onshowpopupmenu)|Lo llama el marco de trabajo cuando se activa un menú emergente.|  
|[CMDIFrameWndEx::OnSizeMDIClient](#onsizemdiclient)|Llamado por el marco de trabajo cuando está cambiando el tamaño de la ventana de cliente MDI.|  
|[CMDIFrameWndEx::OnTearOffMenu](#ontearoffmenu)|Lo llama el marco de trabajo cuando se activa un menú con barra desplazable.|  
|[CMDIFrameWndEx::OnUpdateFrameMenu](#onupdateframemenu)|Llamado por el marco de trabajo para actualizar el menú de marco. (Invalida `CMDIFrameWnd::OnUpdateFrameMenu`).|  
|[CMDIFrameWndEx::PaneFromPoint](#panefrompoint)|Devuelve el panel acoplable que contiene el punto especificado.|  
|`CMDIFrameWndEx::PreTranslateMessage`|Utilizado por la clase [CWinApp](../../mfc/reference/cwinapp-class.md) para traducir los mensajes de ventana antes de que se envíen a la [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funciones de Windows.  (Invalida `CMDIFrameWnd::PreTranslateMessage`).|  
|[CMDIFrameWndEx::RecalcLayout](#recalclayout)|Llamado por el marco para volver a calcular el diseño de la ventana de marco. (Invalida [RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout).)|  
|[CMDIFrameWndEx::RemovePaneFromDockManager](#removepanefromdockmanager)|Anula el registro de un panel y quita desde el Administrador de acoplamiento.|  
|[CMDIFrameWndEx::SaveMDIState](#savemdistate)|Guarda el diseño actual de los grupos de fichas de MDI y la lista de documentos abiertos previamente.|  
|[CMDIFrameWndEx::SetPrintPreviewFrame](#setprintpreviewframe)|Establece la ventana de marco de vista previa de impresión.|  
|[CMDIFrameWndEx::SetupToolbarMenu](#setuptoolbarmenu)|Modifica un objeto de barra de herramientas al buscar elementos ficticios y reemplazarlos con los elementos definidos por el usuario especificados.|  
|[CMDIFrameWndEx::ShowFullScreen](#showfullscreen)|Cambia el marco principal de modo normal al modo de pantalla completa.|  
|[CMDIFrameWndEx::ShowPane](#showpane)|Muestra u oculta el panel especificado.|  
|[CMDIFrameWndEx::ShowWindowsDialog](#showwindowsdialog)|Crea un [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) cuadro y lo abre.|  
|[CMDIFrameWndEx::TabbedDocumentToControlBar](#tabbeddocumenttocontrolbar)|Convierte el documento con fichas especificado a un panel acoplable.|  
|[CMDIFrameWndEx::UpdateCaption](#updatecaption)|Llamado por el marco de trabajo para actualizar el título del marco de ventana.|  
|[CMDIFrameWndEx::UpdateMDITabbedBarsIcons](#updatemditabbedbarsicons)|Establece el icono de cada panel con fichas de MDI.|  
|[CMDIFrameWndEx::WinHelp](#winhelp)|Lo llama el marco para iniciar la aplicación o la ayuda contextual de WinHelp. (Invalida [CWnd::WinHelp](../../mfc/reference/cwnd-class.md#winhelp).)|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMDIFrameWndEx::m_bCanCovertControlBarToMDIChild](#m_bcancovertcontrolbartomdichild)|Determina si se pueden convertir paneles de acoplamiento para ventanas secundarias MDI.|  
|[CMDIFrameWndEx::m_bDisableSetRedraw](#m_bdisablesetredraw)|Habilita o deshabilita la optimización de la actualización de las ventanas secundarias MDI.|  
  
## <a name="remarks"></a>Comentarios  
 Para aprovechar las características de personalización extendido en una aplicación MDI, derive la clase de ventana de marco MDI de la aplicación de `CMDIFrameWndEx` en lugar de `CMDIFrameWnd`.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se deriva una clase de `CMDIFrameWndEx`. Este fragmento de código procede de la [ejemplo de DrawClient: MFC Ribbon-Based OLE objeto de aplicación de dibujo](../../visual-cpp-samples.md).  
  
 [!code-cpp[1 NVC_MFC_DrawClient](../../mfc/reference/codesnippet/cpp/cmdiframewndex-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)  
  
 [CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxMDIFrameWndEx.h  
  
##  <a name="a-nameactiveitemrecalclayouta--cmdiframewndexactiveitemrecalclayout"></a><a name="activeitemrecalclayout"></a>CMDIFrameWndEx::ActiveItemRecalcLayout  
 Vuelve a calcular el diseño del elemento activo.  
  
```  
void ActiveItemRecalcLayout();
```  
  
##  <a name="a-nameaddpanea--cmdiframewndexaddpane"></a><a name="addpane"></a>CMDIFrameWndEx::AddPane  
 Registra un panel con el Administrador de acoplamiento.  
  
```  
BOOL AddPane(
    CBasePane* pControlBar,  
    BOOL bTail=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pControlBar`  
 Puntero al panel para registrar.  
  
 [in] `bTail`  
 Especifica si se debe agregar este panel hasta el final de la lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor distinto de cero si el panel se ha registrado correctamente. Devuelve 0 si el panel ya está registrado con el Administrador de acoplamiento.  
  
### <a name="remarks"></a>Comentarios  
 Cada panel debe estar registrado en el [CDockingManager clase](../../mfc/reference/cdockingmanager-class.md) poder establecer un elemento en el diseño de acoplamiento. Utilice este método para notificar al administrador de acoplamiento que desee acoplar un panel específico. Una vez que se registra ese panel, el Administrador de acoplamiento alinea basándose en su valor de alineación y la posición en la lista de paneles mantenida por el Administrador de acoplamiento.  
  
##  <a name="a-nameadjustclientareaa--cmdiframewndexadjustclientarea"></a><a name="adjustclientarea"></a>CMDIFrameWndEx::AdjustClientArea  
 Reduce el área de cliente para permitir un borde.  
  
```  
virtual void AdjustClientArea();
```  
  
##  <a name="a-nameadjustdockinglayouta--cmdiframewndexadjustdockinglayout"></a><a name="adjustdockinglayout"></a>CMDIFrameWndEx::AdjustDockingLayout  
 Vuelve a calcular el diseño de todos los paneles acoplados.  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hdwp`  
 Identifica la estructura de la posición de la ventana de varios. Puede obtener este valor mediante una llamada a `BeginDeferWindowPos`.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para volver a calcular el diseño de todos los paneles acoplada a la ventana de marco.  
  
##  <a name="a-namearemditabsa--cmdiframewndexaremditabs"></a><a name="aremditabs"></a>CMDIFrameWndEx::AreMDITabs  
 Determina si está habilitada la característica de las fichas MDI o la característica de grupos con pestañas MDI.  
  
```  
BOOL AreMDITabs(int* pnMDITabsType=NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `pnMDITabsType`  
 Un puntero a una variable de entero que indica qué características están habilitadas:  
  
-   0: todas las características están deshabilitadas.  
  
-   1: se habilita las fichas MDI.  
  
-   2: grupos de MDI con fichas están habilitados.  
  
### <a name="return-value"></a>Valor devuelto  
 `Returns TRUE`Si las fichas MDI o MDI con grupos con pestañas está habilitado.  
  
 `Returns FALSE`Si se habilita ninguna de las características anteriores.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para determinar si las fichas MDI o MDI con grupos con pestañas está habilitada para la ventana de marco. Utilice [CMDIFrameWndEx::EnableMDITabs](#enablemditabs) para habilitar o deshabilitar la característica de las fichas MDI.  
  
 Utilice [CMDIFrameWndEx::EnableMDITabbedGroups](#enablemditabbedgroups) para habilitar o deshabilitar la característica de grupos con pestañas MDI.  
  
##  <a name="a-namecancovertcontrolbartomdichilda--cmdiframewndexcancovertcontrolbartomdichild"></a><a name="cancovertcontrolbartomdichild"></a>CMDIFrameWndEx::CanCovertControlBarToMDIChild  
 Llamado por el marco de trabajo para determinar si la ventana de marco puede convertir paneles de acoplamiento en documentos con fichas  
  
```  
virtual BOOL CanCovertControlBarToMDIChild();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si la ventana de marco puede convertir paneles de acoplamiento en documentos con fichas; en caso contrario devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada y devolver `TRUE` para permitir la conversión de acoplar paneles a documentos con fichas. Como alternativa, puede establecer [CMDIFrameWndEx::m_bCanCovertControlBarToMDIChild](#m_bcancovertcontrolbartomdichild) a `TRUE`.  
  
##  <a name="a-namecontrolbartotabbeddocumenta--cmdiframewndexcontrolbartotabbeddocument"></a><a name="controlbartotabbeddocument"></a>CMDIFrameWndEx::ControlBarToTabbedDocument  
 Convierte el panel de acoplamiento especificado en un documento con fichas.  
  
```  
virtual CMDIChildWndEx* ControlBarToTabbedDocument(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 `pBar`  
 Un puntero al panel de acoplamiento para convertir.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la nueva ventana secundaria MDI que contiene el panel de acoplamiento.  
  
### <a name="remarks"></a>Comentarios  
 Este método convierte un panel acoplable en un documento con fichas. Cuando se llama a este método, el marco de trabajo crea un [clase CMDIChildWndEx](../../mfc/reference/cmdichildwndex-class.md) objeto, quita el Administrador de acoplamiento en el panel de acoplamiento y agrega el panel de acoplamiento a la nueva ventana secundaria MDI. El panel de acoplamiento para cubrir todo el área cliente cambia el tamaño de la ventana secundaria MDI  
  
##  <a name="a-namecreatedocumentwindowa--cmdiframewndexcreatedocumentwindow"></a><a name="createdocumentwindow"></a>CMDIFrameWndEx::CreateDocumentWindow  
 Crea una ventana de documento secundaria.  
  
```  
virtual CMDIChildWndEx* CreateDocumentWindow(
    LPCTSTR lpcszDocName,  
    CObject* pObj);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpcszDocName`  
 Una cadena de texto que contiene un identificador de documento. Normalmente, es la ruta de acceso completa de un archivo de documento.  
  
 [in] `pObj`  
 Puntero a un objeto definido por el usuario. Por ejemplo, un desarrollador puede crear una estructura de datos específicos de aplicación que describe el documento y que le indica cómo se debe inicializar el documento en el inicio.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a `CMDIChildWndEx`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando se carga la lista de documentos previamente guardados en el registro.  
  
 Invalide este método para crear documentos cuando se cargan desde el registro.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo `CreateDocumentWindow` se utiliza en el [ejemplo VisualStudioDemo: aplicación MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 En este ejemplo, `g_strStartViewName` podría ser el nombre de un "documento virtual" (por ejemplo, "Página de inicio") que no se cargue realmente desde un archivo de disco. Por lo tanto, necesitamos un procesamiento especial para administrar ese caso.  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#13;](../../mfc/codesnippet/cpp/cmdiframewndex-class_2.cpp)]  
  
##  <a name="a-namecreatenewwindowa--cmdiframewndexcreatenewwindow"></a><a name="createnewwindow"></a>CMDIFrameWndEx::CreateNewWindow  
 Llamado por el marco para crear una nueva ventana.  
  
```  
virtual CMDIChildWndEx* CreateNewWindow(
    LPCTSTR lpcszDocName,  
    CObject* pObj);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpcszDocName`  
 El nombre del documento.  
  
 [in] `pObj`  
 Reservado para un uso futuro.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la nueva ventana.  
  
##  <a name="a-namedockpanea--cmdiframewndexdockpane"></a><a name="dockpane"></a>CMDIFrameWndEx::DockPane  
 Acopla el panel especificado en la ventana de marco.  
  
```  
void DockPane(
    CBasePane* pBar,  
    UINT nDockBarID=0,  
    LPCRECT lpRect=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Puntero al panel para acoplar.  
  
 [in] `nDockBarID`  
 Especifica qué lados de la ventana de marco para acoplar a.  
  
 [in] `lpRect`  
 No usado.  
  
### <a name="remarks"></a>Comentarios  
 Este método acopla especificado el panel a uno de los lados de la ventana de marco que se especificó cuando [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking) y [CMDIFrameWndEx::EnableDocking](#enabledocking) llamó.  
  
### <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso del método `DockPane`. Este fragmento de código procede de la [ejemplo VisualStudioDemo: aplicación MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo Nº&4;](../../mfc/codesnippet/cpp/cmdiframewndex-class_3.cpp)]  
  
##  <a name="a-namedockpaneleftofa--cmdiframewndexdockpaneleftof"></a><a name="dockpaneleftof"></a>CMDIFrameWndEx::DockPaneLeftOf  
 Acopla un panel a la izquierda de otro panel.  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBar,  
    CPane* pLeftOf);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Un puntero al panel de acoplamiento.  
  
 [in] `pLeftOf`  
 Un puntero al panel que actúa como el sitio de vinculación. .  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si la operación es correcta. De lo contrario, devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para acoplar varios objetos de panel en un orden predefinido. Este método acopla el panel especificado por `pBar` a la izquierda del panel especificado por `pLeftOf`.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo el `DockPaneLeftOf` método se utiliza en el [ejemplo VisualStudioDemo: aplicación MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#5;](../../mfc/codesnippet/cpp/cmdiframewndex-class_4.cpp)]  
  
##  <a name="a-nameenableautohidepanesa--cmdiframewndexenableautohidepanes"></a><a name="enableautohidepanes"></a>CMDIFrameWndEx::EnableAutoHidePanes  
 Permite oculta automáticamente paneles en el modo al que se acoplan a los lados de la ventana de marco principal especificados.  
  
```  
BOOL EnableAutoHidePanes(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwDockStyle`  
 Especifica los lados de la ventana de marco principal que se habilitará. Utilice uno o varios de los siguientes indicadores.  
  
- `CBRS_ALIGN_LEFT`  
  
- `CBRS_ALIGN_RIGHT`  
  
- `CBRS_ALIGN_TOP`  
  
- `CBRS_ALIGN_BOTTOM`  
  
### <a name="return-value"></a>Valor devuelto  
 Llame a esta función para habilitar el modo de ocultación automática para los paneles se acoplan a los lados de la ventana de marco principal especificados.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo el `EnableAutoHidePanes` método se utiliza en el [ejemplo VisualStudioDemo: aplicación MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo Nº&6;](../../mfc/codesnippet/cpp/cmdiframewndex-class_5.cpp)]  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameenabledockinga--cmdiframewndexenabledocking"></a><a name="enabledocking"></a>CMDIFrameWndEx::EnableDocking  
 Permite acoplar los paneles que pertenecen a la ventana de marco MDI.  
  
```  
BOOL EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwDockStyle`  
 Especifica el estilo de acoplamiento que desea aplicar.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para habilitar el acoplamiento de paneles que pertenecen a la `CMDIFrameWndEx` objeto.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo el `EnableDocking` método se utiliza en el [ejemplo VisualStudioDemo: aplicación MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#7;](../../mfc/codesnippet/cpp/cmdiframewndex-class_6.cpp)]  
  
##  <a name="a-nameenablefullscreenmainmenua--cmdiframewndexenablefullscreenmainmenu"></a><a name="enablefullscreenmainmenu"></a>CMDIFrameWndEx::EnableFullScreenMainMenu  
 Muestra u oculta el menú principal en modo de pantalla completa.  
  
```  
void EnableFullScreenMainMenu(BOOL bEnableMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnableMenu`  
 `TRUE`para mostrar el menú principal en modo de pantalla completa, o `FALSE` para ocultarlo.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameenablefullscreenmodea--cmdiframewndexenablefullscreenmode"></a><a name="enablefullscreenmode"></a>CMDIFrameWndEx::EnableFullScreenMode  
 Habilita el modo de pantalla completa para la ventana de marco.  
  
```  
void EnableFullScreenMode(UINT uiFullScreenCmd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiFullScreenCmd`  
 El identificador de un comando que habilita o deshabilita el modo de pantalla completa.  
  
### <a name="remarks"></a>Comentarios  
 En el modo de pantalla completa, todas las barras de control de acoplamiento, barras de herramientas y los menús están ocultos y se cambia el tamaño de la vista activa para ocupar la pantalla completa. Cuando se habilita el modo de pantalla completa, debe especificar un identificador del comando que habilita o deshabilita. Puede llamar a `EnableFullScreenMode` desde el marco principal `OnCreate` (función). Cuando una ventana de marco que se pase al modo de pantalla completa, el marco de trabajo crea una barra de herramientas flotante con un botón que tiene el identificador de comando especificado. Si desea mantener el menú principal de la pantalla, llame a [CMDIFrameWndEx::EnableFullScreenMainMenu](#enablefullscreenmainmenu).  
  
##  <a name="a-nameenableloaddockstatea--cmdiframewndexenableloaddockstate"></a><a name="enableloaddockstate"></a>CMDIFrameWndEx::EnableLoadDockState  
 Habilita o deshabilita la carga del estado de acoplamiento.  
  
```  
void EnableLoadDockState(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para habilitar la carga del estado de acoplamiento, `FALSE` para deshabilitar la carga del estado de acoplamiento.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameenablemditabbedgroupsa--cmdiframewndexenablemditabbedgroups"></a><a name="enablemditabbedgroups"></a>CMDIFrameWndEx::EnableMDITabbedGroups  
 Habilita o deshabilita la característica de grupos con pestañas MDI de la ventana de marco.  
  
```  
void EnableMDITabbedGroups(
    BOOL bEnable,  
    const CMDITabInfo& params);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 Si `TRUE`, está habilitada la característica de grupos con pestañas MDI; si `FALSE`, se deshabilita la característica de grupos con pestañas MDI.  
  
 [in] `params`  
 Especifica los parámetros que el marco de trabajo se aplica a las ventanas secundarias que se crean en el área de cliente MDI.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para habilitar o deshabilitar la característica de grupos con pestañas MDI. Esta característica permite que las aplicaciones MDI mostrar las ventanas secundarias como ventanas con fichas que se alinean verticalmente u horizontalmente en el área de cliente MDI. Grupos de ventanas con fichas se separan mediante separadores. El usuario puede cambiar el tamaño de grupos con pestañas con un separador.  
  
-   El usuario puede:  
  
-   Arrastre las fichas individuales entre grupos.  
  
-   Arrastre fichas individuales para el borde de la ventana para crear grupos nuevos.  
  
-   Fichas de mover o crear nuevos grupos mediante el menú contextual.  
  
-   La aplicación puede guardar el diseño actual de ventanas con fichas y la lista de los documentos abiertos actualmente.  
  
 Si se llama a este método con `bEnable` establecido en `FALSE`, `params` se omite.  
  
 Aunque los grupos de fichas de MDI ya está habilitado, puede llamar a este método para modificar la configuración de las ventanas secundarias. Llame al método con `bEnable` establecido en `TRUE` y modificar los miembros de la `CMDITabInfo` objeto especificados por el `params` parámetro.  
  
 Para obtener más información sobre cómo usar MDI con grupos con pestañas, consulte [grupos con fichas de MDI](../../mfc/mdi-tabbed-groups.md).  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo `EnableMDITabbedGroups` se utiliza en el [ejemplo VisualStudioDemo: aplicación MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo Nº&8;](../../mfc/codesnippet/cpp/cmdiframewndex-class_7.cpp)]  
  
##  <a name="a-nameenablemditabsa--cmdiframewndexenablemditabs"></a><a name="enablemditabs"></a>CMDIFrameWndEx::EnableMDITabs  
 Habilita o deshabilita la característica de las fichas de MDI de la ventana de marco MDI. Cuando está habilitada, la ventana de marco muestra una ficha para cada ventana secundaria MDI.  
  
```  
void EnableMDITabs(
    BOOL bEnable=TRUE,  
    BOOL bIcons=TRUE,  
    CMFCTabCtrl::Location tabLocation=CMFCTabCtrl::LOCATION_BOTTOM,  
    BOOL bTabCloseButton=FALSE,  
    CMFCTabCtrl::Style style=CMFCTabCtrl::STYLE_3D_SCROLLED,  
    BOOL bTabCustomTooltips=FALSE,  
    BOOL bActiveTabCloseButton=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bEnable`  
 Especifica si se habilitan las fichas.  
  
 `bIcons`  
 Especifica si se deben mostrar iconos de las fichas.  
  
 `tabLocation`  
 Especifica la ubicación de las etiquetas de la ficha.  
  
 `bTabCloseButton`  
 Especifica si se debe mostrar botones de cierre de pestaña.  
  
 `style`  
 Especifica el estilo de fichas. Utilice `STYLE_3D_SCROLLED` para regulares pestañas o `STYLE_3D_ONENOTE` para Microsoft OneNote pestañas.  
  
 `bTabCustomTooltips`  
 Especifica si se habilita la información sobre herramientas personalizados.  
  
 `bActiveTabCloseButton`  
 Si `TRUE`, **cerrar** botón aparecerá en la ficha activa en lugar de en la esquina derecha del área de ficha.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para habilitar o deshabilitar la característica de las fichas MDI de la ventana de marco MDI. Cuando está habilitada, todas las ventanas secundarias se muestran como fichas.  
  
 Las etiquetas de la ficha se encuentran en la parte superior o inferior del marco, dependiendo del valor del parámetro `tabLocation`. Se puede especificar `CMFCTabCtrl::LOCATION_BOTTOM` (el valor predeterminado) o `CMFCTabCtrl::LOCATION_TOP`.  
  
 Si `bTabCustomTooltips` es `TRUE`, un `AFX_WM_ON_GET_TAB_TOOLTIP` se enviará el mensaje a la ventana de marco principal. El código puede controlar este mensaje y proporcionar el marco de trabajo con información sobre herramientas personalizados para las fichas MDI.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo `EnableMDITabs` se utiliza en el [ejemplo de MDITabsDemo: aplicación MDI con fichas de MFC](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo&3;](../../mfc/reference/codesnippet/cpp/cmdiframewndex-class_8.cpp)]  
  
##  <a name="a-nameenablemditabslastactiveactivationa--cmdiframewndexenablemditabslastactiveactivation"></a><a name="enablemditabslastactiveactivation"></a>CMDIFrameWndEx::EnableMDITabsLastActiveActivation  
 Especifica si se debe abrir la última ficha que se active cuando el usuario cierra la ficha actual.  
  
```  
void EnableMDITabsLastActiveActivation(BOOL bLastActiveTab=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bLastActiveTab`  
 Si `TRUE`, habilitar la activación de la última ficha activada. Si `FALSE`, deshabilitar la activación de la última ficha activada.  
  
### <a name="remarks"></a>Comentarios  
 Hay dos formas de abrir una ficha cuando se cierra la ficha activa:  
  
-   Activar la ficha siguiente.  
  
-   Activar la ficha activa previamente.  
  
 La implementación predeterminada usa la primera de ellas.  
  
 Use `EnableMDITabsLastActiveActivation` para habilitar la segunda forma de la activación de la ficha. Emula la forma en que Windows abre ventanas secundarias MDI.  
  
##  <a name="a-nameenablepanemenua--cmdiframewndexenablepanemenu"></a><a name="enablepanemenu"></a>CMDIFrameWndEx::EnablePaneMenu  
 Habilita o deshabilita la creación automática y administración del menú emergente del panel, que muestra una lista de paneles de la aplicación.  
  
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
 [in] `bEnable`  
 Si `TRUE`, está habilitado el control automático del menú panel; si `FALSE`, control automático está deshabilitado.  
  
 [in] `uiCustomizeCmd`  
 Identificador de comando de la **personalizar** elemento de menú. Normalmente, este elemento de menú se agrega al final de la lista de paneles.  
  
 [in] `strCustomizeLabel`  
 El texto que se mostrará para el **personalizar** elemento de menú (para la localización).  
  
 [in] `uiViewToolbarsMenuEntryID`  
 Especifica el identificador de un elemento de menú de la barra de herramientas que se abre el menú del panel. Esta suele ser la **las barras de herramientas** submenú de la **vista** menú.  
  
 [in] `bContextMenuShowsToolbarsOnly`  
 Si `TRUE`, el menú de panel muestra sólo una lista de las barras de herramientas. Si `FALSE`, el menú muestra una lista de las barras de herramientas y las barras de acoplamiento.  
  
 [in] `bViewMenuShowsToolbarsOnly`  
 Si `TRUE`, el menú de panel muestra sólo una lista de las barras de herramientas. Si `FALSE`, el menú muestra una lista de las barras de herramientas y las barras de acoplamiento.  
  
### <a name="remarks"></a>Comentarios  
 El menú emergente del panel muestra la lista de paneles de la aplicación y permite al usuario mostrar u ocultar los paneles individuales.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo `EnablePaneMenu` se utiliza en el [ejemplo VisualStudioDemo: aplicación MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#9;](../../mfc/codesnippet/cpp/cmdiframewndex-class_9.cpp)]  
  
##  <a name="a-nameenablewindowsdialoga--cmdiframewndexenablewindowsdialog"></a><a name="enablewindowsdialog"></a>CMDIFrameWndEx::EnableWindowsDialog  
 Inserta un elemento de menú cuyo identificador de comando llama un [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) cuadro de diálogo.  
  
```  
void EnableWindowsDialog(
    UINT uiMenuId,  
    LPCTSTR lpszMenuText,  
    BOOL bShowAllways=FALSE,  
    BOOL bShowHelpButton=FALSE);

 
void EnableWindowsDialog(
    UINT uiMenuId,  
    UINT uiMenuTextResId,  
    BOOL bShowAllways=FALSE,  
    BOOL bShowHelpButton=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiMenuId`  
 Especifica el identificador de recurso de un menú.  
  
 [in] `lpszMenuText`  
 Especifica el texto del elemento.  
  
 [in] `bShowHelpButton`  
 Especifica si se muestra un **ayuda** botón en el cuadro de diálogo de administración de windows.  
  
 [in] `uiMenuTextResId`  
 El identificador de recurso de cadena que contiene la cadena de texto del elemento.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para insertar un elemento de menú cuyo comando llama a un cuadro de diálogo de administración de ventana MDI secundario ( [CMFCWindowsManagerDialog clase](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)). El nuevo elemento se inserta en el menú especificado mediante `uiMenuId`. Llame a `EnableWindowsDialog` al procesar el `WM_CREATE` mensaje.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo `EnableWindowsDialog` se utiliza en el [ejemplo VisualStudioDemo: aplicación MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#10;](../../mfc/codesnippet/cpp/cmdiframewndex-class_10.cpp)]  
  
##  <a name="a-namegetactivepopupa--cmdiframewndexgetactivepopup"></a><a name="getactivepopup"></a>CMDIFrameWndEx::GetActivePopup  
 Devuelve un puntero al menú emergente mostrado actualmente.  
  
```  
CMFCPopupMenu* GetActivePopup() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al menú emergente activo; `NULL` si ningún menú emergente está activo.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para obtener un puntero a la [CMFCPopupMenu clase](../../mfc/reference/cmfcpopupmenu-class.md) objeto que se muestra actualmente.  
  
##  <a name="a-namegetdefaultresida--cmdiframewndexgetdefaultresid"></a><a name="getdefaultresid"></a>CMDIFrameWndEx::GetDefaultResId  
 Devuelve el identificador de recursos compartidos de la ventana de marco MDI.  
  
```  
UINT GetDefaultResId() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de identificador de recurso. 0 si la ventana de marco no tiene ninguna barra de menús.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve el identificador de recurso que se especificó cuando se carga la ventana de marco MDI [CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe).  
  
##  <a name="a-namegetmditabgroupsa--cmdiframewndexgetmditabgroups"></a><a name="getmditabgroups"></a>CMDIFrameWndEx::GetMDITabGroups  
 Devuelve que una lista de MDI ventanas de fichas.  
  
```  
const CObList& GetMDITabGroups() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a un [clase CObList](../../mfc/reference/coblist-class.md) objeto que contiene una lista de ventanas con fichas. No almacenar ni modificar la lista.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para tener acceso a la lista de ventanas con fichas. Puede ser útil si desea cambiar o consultar algunos parámetros de ventanas con fichas individuales.  
  
##  <a name="a-namegetmditabsa--cmdiframewndexgetmditabs"></a><a name="getmditabs"></a>CMDIFrameWndEx::GetMDITabs  
 Devuelve una referencia a la ventana con fichas subrayada.  
  
```  
CMFCTabCtrl& GetMDITabs();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la ventana con fichas subrayada.  
  
##  <a name="a-namegetmditabscontextmenualloweditemsa--cmdiframewndexgetmditabscontextmenualloweditems"></a><a name="getmditabscontextmenualloweditems"></a>CMDIFrameWndEx::GetMDITabsContextMenuAllowedItems  
 Devuelve una combinación de indicadores que determina qué operaciones son válidas cuando está habilitada la característica grupos de fichas de MDI.  
  
```  
DWORD GetMDITabsContextMenuAllowedItems();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una combinación OR bit a bit de los siguientes indicadores:  
  
- `BCGP_MDI_CREATE_VERT_GROUP`-puede crear un grupo de fichas vertical.  
  
- `BCGP_MDI_CREATE_HORZ_GROUP`-puede crear un grupo de pestañas horizontal.  
  
- `BCGP_MDI_CAN_MOVE_PREV`-puede mover una ficha al grupo de ficha anterior.  
  
- `BCGP_MDI_CAN_MOVE_NEXT`-puede mover una ficha al siguiente grupo de ficha.  
  
### <a name="remarks"></a>Comentarios  
 Cuando está habilitada la característica grupos de fichas de MDI, debe saber qué operaciones se permiten en las fichas de una ventana concreta. Este método analiza el diseño actual de las ventanas con fichas y devuelve una combinación de indicadores que se pueden utiliza para crear, por ejemplo, un menú contextual.  
  
 Puede crear un nuevo grupo de fichas vertical cuando todas las ventanas con fichas se alinean verticalmente, o cuando hay sólo una ventana con fichas.  
  
 Puede crear un nuevo grupo de fichas horizontal cuando todas las ventanas con fichas estén alineadas horizontalmente, o cuando hay sólo una ventana con fichas.  
  
 Puede mover una ficha al grupo anterior sólo si hay más de una ficha en una ventana con fichas.  
  
 Puede mover una ficha al grupo siguiente sólo si hay más de una ficha en una ventana con fichas.  
  
##  <a name="a-namegetmenubara--cmdiframewndexgetmenubar"></a><a name="getmenubar"></a>CMDIFrameWndEx::GetMenuBar  
 Devuelve un puntero a un objeto de la barra de menú asociado a la ventana de marco.  
  
```  
const CMFCMenuBar* GetMenuBar() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un objeto de la barra de menú.  
  
##  <a name="a-namegetpanea--cmdiframewndexgetpane"></a><a name="getpane"></a>CMDIFrameWndEx::GetPane  
 Devuelve un puntero al panel que tiene el identificador del control especificado.  
  
```  
CBasePane* GetPane(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 El identificador del control.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al panel que tiene el identificador de control especificado, si existe. En caso contrario, es `NULL`.  
  
##  <a name="a-namegetribbonbara--cmdiframewndexgetribbonbar"></a><a name="getribbonbar"></a>CMDIFrameWndEx::GetRibbonBar  
 Recupera el control de barra de la cinta de opciones para el marco.  
  
```  
CMFCRibbonBar* GetRibbonBar();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la [CMFCRibbonBar clase](../../mfc/reference/cmfcribbonbar-class.md) para el marco.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettearoffbarsa--cmdiframewndexgettearoffbars"></a><a name="gettearoffbars"></a>CMDIFrameWndEx::GetTearOffBars  
 Devuelve una lista de menús desplazable.  
  
```  
const CObList& GetTearOffBars() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a un [clase CObList](../../mfc/reference/coblist-class.md) objeto que contiene una colección de punteros a `CPane`-derivado de objetos que están en un estado.  
  
### <a name="remarks"></a>Comentarios  
 `CMDIFrameWndEx`mantiene una colección de menús desplazable. Utilice este método para recuperar una referencia a esta lista.  
  
##  <a name="a-namegettoolbarbuttontooltiptexta--cmdiframewndexgettoolbarbuttontooltiptext"></a><a name="gettoolbarbuttontooltiptext"></a>CMDIFrameWndEx::GetToolbarButtonToolTipText  
 Llamado por el marco de trabajo cuando la aplicación muestra la información sobre herramientas para un botón de barra de herramientas.  
  
```  
virtual BOOL GetToolbarButtonToolTipText(
    CMFCToolBarButton* pButton,  
    CString& strTTText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Puntero a un botón de barra de herramientas.  
  
 [in] `strTTText`  
 El texto de información sobre herramientas para mostrar para el botón.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se ha mostrado la información sobre herramientas. En caso contrario, es `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameinsertpanea--cmdiframewndexinsertpane"></a><a name="insertpane"></a>CMDIFrameWndEx::InsertPane  
 El panel especificado se registra con el Administrador de acoplamiento.  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pControlBar`  
 Un puntero al panel que se va a insertar.  
  
 [in] `pTarget`  
 Un puntero al panel antes o después de que se va a insertar en el panel.  
  
 [in] `bAfter`  
 Si `TRUE`, `pControlBar` se inserta después `pTarget`. Si `FALSE`, `pControlBar` se insertará antes de `pTarget`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método registra correctamente el panel, `FALSE` si el panel ya se ha registrado con el Administrador de acoplamiento.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para indicar a un panel especificado por el Administrador de acoplamiento `pControlBar`. El Administrador de acoplamiento alineará este panel según el panel de la alineación y posición en la lista interna de acoplamiento del administrador.  
  
##  <a name="a-nameisfullscreena--cmdiframewndexisfullscreen"></a><a name="isfullscreen"></a>CMDIFrameWndEx::IsFullScreen  
 Determina si la ventana de marco está en modo de pantalla completa.  
  
```  
BOOL IsFullScreen() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la ventana de marco está en modo de pantalla completa; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Puede establecer el modo de pantalla completa mediante una llamada a la [CMDIFrameWndEx::EnableFullScreenMode](#enablefullscreenmode) método.  
  
##  <a name="a-nameismditabbedgroupa--cmdiframewndexismditabbedgroup"></a><a name="ismditabbedgroup"></a>CMDIFrameWndEx::IsMDITabbedGroup  
 Especifica si está habilitada la característica grupos de fichas de MDI.  
  
```  
BOOL IsMDITabbedGroup() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si está habilitada la característica grupos de fichas de MDI; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Para determinar si está habilitada fichas MDI regulares o la característica grupos de fichas de MDI, utilice [CMDIFrameWndEx::AreMDITabs](#aremditabs).  
  
##  <a name="a-nameismemberofmditabgroupa--cmdiframewndexismemberofmditabgroup"></a><a name="ismemberofmditabgroup"></a>CMDIFrameWndEx::IsMemberOfMDITabGroup  
 Determina si la ventana con fichas especificada está en la lista de windows que se encuentran en grupos con fichas de MDI.  
  
```  
BOOL IsMemberOfMDITabGroup(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Puntero a la ventana con fichas.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la ventana con fichas especificada está en la lista de ventanas con fichas que forman los grupos con fichas de MDI. De lo contrario, `FALSE`.  
  
##  <a name="a-nameismenubaravailablea--cmdiframewndexismenubaravailable"></a><a name="ismenubaravailable"></a>CMDIFrameWndEx::IsMenuBarAvailable  
 Determina si la ventana de marco tiene una barra de menús.  
  
```  
BOOL IsMenuBarAvailable() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si no es el puntero al objeto de barra de menú `NULL`; en caso contrario `FALSE`.  
  
##  <a name="a-nameispointneardocksitea--cmdiframewndexispointneardocksite"></a><a name="ispointneardocksite"></a>CMDIFrameWndEx::IsPointNearDockSite  
 Determina si un punto especificado está cerca del sitio de vinculación.  
  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 El punto especificado en coordenadas de pantalla.  
  
 [in] `dwBarAlignment`  
 Especifica qué borde es el punto de cerca. Los valores posibles son `CBRS_ALIGN_LEFT`, `CBRS_ALIGN_RIGHT`, `CBRS_ALIGN_TOP`, y`CBRS_ALIGN_BOTTOM`  
  
 [in] `bOuterEdge`  
 `TRUE`Si el punto está cerca del borde exterior del sitio de vinculación; `FALSE` en caso contrario.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el punto está cerca del sitio de vinculación; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El punto está cerca del sitio de vinculación cuando se encuentra dentro de la sensibilidad establecida en el Administrador de acoplamiento. La sensibilidad predeterminado es 15 píxeles.  
  
##  <a name="a-nameisprintpreviewa--cmdiframewndexisprintpreview"></a><a name="isprintpreview"></a>CMDIFrameWndEx::IsPrintPreview  
 Determina si la ventana de marco está en modo de vista previa de impresión.  
  
```  
BOOL IsPrintPreview();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la ventana de marco está en modo de vista previa de impresión; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameloadframea--cmdiframewndexloadframe"></a><a name="loadframe"></a>CMDIFrameWndEx::LoadFrame  
 Crea una ventana de marco de información de recursos.  
  
```  
virtual BOOL LoadFrame(
    UINT nIDResource,  
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,  
    CWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIDResource`  
 El identificador de un recurso compartido asociado a la ventana de marco.  
  
 [in] `dwDefaultStyle`  
 El estilo de la ventana de marco.  
  
 [in] `pParentWnd`  
 Un puntero al elemento primario del marco.  
  
 [in] `pContext`  
 Un puntero a un [CCreateContext estructura](../../mfc/reference/ccreatecontext-structure.md). Este parámetro puede ser `NULL`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método tiene éxito, de lo contrario, `FALSE`.  
  
##  <a name="a-nameloadmdistatea--cmdiframewndexloadmdistate"></a><a name="loadmdistate"></a>CMDIFrameWndEx::LoadMDIState  
 Carga el diseño de los grupos de fichas de MDI especificado y la lista de documentos abiertos previamente.  
  
```  
virtual BOOL LoadMDIState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Especifica el nombre del perfil.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la carga se realizó correctamente; `FALSE` si la carga no se pudo o no hay ningún dato para cargar.  
  
### <a name="remarks"></a>Comentarios  
 Para cargar o guardar el estado de las fichas MDI y grupos y la lista de los documentos abiertos, haga lo siguiente:  
  
-   Llame a [CMDIFrameWndEx::SaveMDIState](#savemdistate) cuando se cierra el marco principal  
  
-   Llame a [CMDIFrameWndEx::LoadMDIState](#loadmdistate) cuando se cree el marco principal. El lugar recomendado para esta llamada es antes de que el marco principal se muestra por primera vez. Agregar `CWinAppEx::EnableLoadWindowPlacement` `(FALSE);` antes de `pMainFrame->LoadFrame (IDR_MAINFRAME);.` agregar `CBCGPWorkspace::ReloadWindowPlacement` `(pMainFrame);` después de la llamada a `LoadMDIState` para mostrar el marco principal en la posición en la que se almacena en el registro.  
  
-   Invalidar `GetDocumentName` en el `CMDIChildWndEx`-clase derivada si la aplicación muestra los documentos que no se almacenan como archivos. La cadena devuelta se guardará en el registro como el identificador del documento. La implementación base de [CMDIChildWndEx::GetDocumentName](../../mfc/reference/cmdichildwndex-class.md#getdocumentname) devuelve un valor obtenido del [CDocument::GetPathName](../../mfc/reference/cdocument-class.md#getpathname).  
  
-   Invalidar [CMDIFrameWndEx::CreateDocumentWindow](#createdocumentwindow) crear correctamente documentos cuando se cargan desde el registro. El primer parámetro es la cadena que `GetDocumentName` devuelto.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo `LoadMDIState` se utiliza en el [ejemplo VisualStudioDemo: aplicación MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#11;](../../mfc/codesnippet/cpp/cmdiframewndex-class_11.cpp)]  
  
##  <a name="a-namemditabmovetonextgroupa--cmdiframewndexmditabmovetonextgroup"></a><a name="mditabmovetonextgroup"></a>CMDIFrameWndEx::MDITabMoveToNextGroup  
 Mueve la ficha activa de la ventana activa con pestañas al grupo de fichas siguiente o anterior.  
  
```  
void MDITabMoveToNextGroup(BOOL bNext=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bNext`  
 Si `TRUE`, mueva la etiqueta al siguiente grupo de pestañas. Si `FALSE`, muévalo al grupo de fichas anterior.  
  
##  <a name="a-namemditabnewgroupa--cmdiframewndexmditabnewgroup"></a><a name="mditabnewgroup"></a>CMDIFrameWndEx::MDITabNewGroup  
 Crea un nuevo grupo con pestañas que tiene una sola ventana.  
  
```  
void MDITabNewGroup(BOOL bVert=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bVert`  
 Especifica la alineación de grupo nuevo. Si `TRUE`, el nuevo grupo se alinea verticalmente. Si `FALSE`, el nuevo grupo se alinea horizontalmente.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para crear un nuevo (nuevo grupo con fichas) de la ventana de fichas y agregarle la primera pestaña.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo `MDITabNewGroup` se utiliza en el [ejemplo VisualStudioDemo: aplicación MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#12;](../../mfc/codesnippet/cpp/cmdiframewndex-class_12.cpp)]  
  
##  <a name="a-namembcancovertcontrolbartomdichilda--cmdiframewndexmbcancovertcontrolbartomdichild"></a><a name="m_bcancovertcontrolbartomdichild"></a>CMDIFrameWndEx::m_bCanCovertControlBarToMDIChild  
 Especifica si se pueden convertir paneles de acoplamiento para ventanas secundarias MDI.  
  
```  
BOOL m_bCanCovertControlBarToMDIChild;  
```  
  
### <a name="remarks"></a>Comentarios  
 Indica si las barras de control de acoplamiento se pueden convertir a las ventanas secundarias MDI. Si este marcador `TRUE`, el marco de trabajo realiza la conversión automáticamente cuando el usuario selecciona el **fichas** comando. El indicador está protegido y debe habilitar explícitamente esta opción estableciendo `m_bCanCovertControlBarToMDIChild` en un constructor de un `CMDIFrameWndEx`-clase derivada o reemplazar por `CanConvertControlBarToMDIChild`.  
  
 El valor predeterminado es `FALSE`.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo `m_bCanCovertControlBarToMDIChild` se utiliza en el [ejemplo VisualStudioDemo: aplicación MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#13;](../../mfc/codesnippet/cpp/cmdiframewndex-class_2.cpp)]  
  
##  <a name="a-namembdisablesetredrawa--cmdiframewndexmbdisablesetredraw"></a><a name="m_bdisablesetredraw"></a>CMDIFrameWndEx::m_bDisableSetRedraw  
 Habilita o deshabilita la optimización de la actualización de las ventanas secundarias MDI.  
  
```  
AFX_IMPORT_DATA static BOOL m_bDisableSetRedraw;  
```  
  
### <a name="remarks"></a>Comentarios  
 El valor predeterminado es `TRUE`.  
  
 Establezca esta marca en `FALSE` si desea optimizar la actualización en pantalla de elementos secundarios MDI. En este caso, el marco llamará `SetRedraw (FALSE)` del marco principal cuando la aplicación está cambiando la ficha activa.  
  
 Este indicador puede producir efectos no deseados (como las aplicaciones de segundo plano que se hacen visibles). Por lo tanto, se recomienda cambiar el valor predeterminado si se producen parpadeo notable durante la activación de la ficha MDI.  
  
##  <a name="a-namenegotiateborderspacea--cmdiframewndexnegotiateborderspace"></a><a name="negotiateborderspace"></a>CMDIFrameWndEx::NegotiateBorderSpace  
 Espacio del borde de una ventana de marco se negocia durante la activación en contexto OLE.  
  
```  
virtual BOOL NegotiateBorderSpace(
    UINT nBorderCmd,  
    LPRECT lpRectBorder);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nBorderCmd`  
 Contiene uno de los siguientes valores de la enumeración `CFrameWnd::BorderCmd`:  
  
- `borderGet` = 1  
  
- `borderRequest` = 2  
  
- `borderSet` = 3  
  
 [in, out] `lpRectBorder`  
 Puntero a un [estructura RECT](../../mfc/reference/rect-structure1.md) o un [CRect Class](../../atl-mfc-shared/reference/crect-class.md) objeto que especifica las coordenadas del borde.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el método se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método es una implementación de negociación de espacio del borde OLE.  
  
##  <a name="a-nameonclosedockingpanea--cmdiframewndexonclosedockingpane"></a><a name="onclosedockingpane"></a>CMDIFrameWndEx::OnCloseDockingPane  
 Llamado por el marco de trabajo cuando el usuario hace clic en el **cerrar** botón en un panel acoplable.  
  
```  
virtual BOOL OnCloseDockingPane(CDockablePane* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Puntero al panel se está cerrando.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se puede cerrar el panel de acoplamiento. En caso contrario, es `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para controlar la ocultación de paneles de acoplamiento. Devolver `FALSE` si desea impedir que se va a ocultar un panel acoplable.  
  
 La implementación predeterminada no hace nada y devuelve `TRUE`.  
  
##  <a name="a-nameoncloseminiframea--cmdiframewndexoncloseminiframe"></a><a name="oncloseminiframe"></a>CMDIFrameWndEx::OnCloseMiniFrame  
 Llamado por el marco de trabajo cuando el usuario hace clic en el **cerrar** botón en una ventana de marco reducido flotante.  
  
```  
virtual BOOL OnCloseMiniFrame(CPaneFrameWnd*);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Puntero a la ventana de marco reducido que se está cerrada.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se puede cerrar la ventana de marco reducido flotante. En caso contrario, es `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para controlar la ocultación de ventanas de marco reducido flotantes. Devolver `FALSE` si desea evitar que una ventana de marco reducido flotante ocultas.  
  
 La implementación predeterminada no hace nada y devuelve `TRUE`.  
  
##  <a name="a-nameonclosepopupmenua--cmdiframewndexonclosepopupmenu"></a><a name="onclosepopupmenu"></a>CMDIFrameWndEx::OnClosePopupMenu  
 Llamado por el marco cuando procesa un menú emergente activo un `WM_DESTROY` mensaje.  
  
```  
virtual void OnClosePopupMenu(CMFCPopupMenu* pMenuPopup);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMenuPopup`  
 Puntero a un menú emergente.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método si desea procesar las notificaciones de [CMFCPopupMenu clase](../../mfc/reference/cmfcpopupmenu-class.md) objetos que pertenecen a la ventana de marco MDI al procesan esos objetos `WM_DESTROY` mensajes.  
  
##  <a name="a-nameoncmdmsga--cmdiframewndexoncmdmsg"></a><a name="oncmdmsg"></a>CMDIFrameWndEx::OnCmdMsg  
 Llamado por el marco de trabajo para enrutar y enviar mensajes de comando y actualizar objetos de interfaz de usuario de comandos.  
  
```  
virtual BOOL OnCmdMsg(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 Identificador del comando.  
  
 [in] `nCode`  
 Identifica el código de notificación de comando. Consulte [CCmdTarget:: OnCmdMsg](../../mfc/reference/ccmdtarget-class.md#oncmdmsg) para obtener más información acerca de los valores para `nCode`.  
  
 [in] `pExtra`  
 Usar según el valor de `nCode`. Consulte [CCmdTarget:: OnCmdMsg](../../mfc/reference/ccmdtarget-class.md#oncmdmsg) para obtener más información acerca de `pExtra`.  
  
 [in, out] `pHandlerInfo`  
 Normalmente, este parámetro debe ser `NULL`. Si no `NULL`, `OnCmdMsg` rellena la `pTarget` y `pmf` los miembros de la `pHandlerInfo` estructura en lugar de enviar el comando.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se controló el mensaje; en caso contrario, 0.  
  
##  <a name="a-nameondrawmenuimagea--cmdiframewndexondrawmenuimage"></a><a name="ondrawmenuimage"></a>CMDIFrameWndEx::OnDrawMenuImage  
 Lo llama el marco de trabajo cuando se dibuja la imagen asociada a un elemento de menú.  
  
```  
virtual BOOL OnDrawMenuImage(
    CDC* pDC,  
    const CMFCToolBarMenuButton* pMenuButton,  
    const CRect& rectImage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pMenuButton`  
 Puntero al botón de menú.  
  
 [in] `rectImage`  
 Rectángulo delimitador de la imagen.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método dibuja la imagen. La implementación predeterminada devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método si desea personalizar la presentación de imágenes de los elementos de menú que pertenecen a la barra de menús que pertenecen a la `CMDIFrameWndEx`-objeto derivado. La implementación predeterminada no hace nada.  
  
##  <a name="a-nameondrawmenulogoa--cmdiframewndexondrawmenulogo"></a><a name="ondrawmenulogo"></a>CMDIFrameWndEx::OnDrawMenuLogo  
 Llamado por el marco cuando una [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)procesos un `WM_PAINT` mensaje.  
  
```  
virtual void OnDrawMenuLogo(
    CDC*, 
    CMFCPopupMenu*, 
    const CRect&);
```  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para mostrar un logotipo en el menú emergente que pertenece a la barra de menús que pertenecen a la `CMDIFrameWndEx`-objeto derivado. La implementación predeterminada no hace nada.  
  
##  <a name="a-nameonerasemdiclientbackgrounda--cmdiframewndexonerasemdiclientbackground"></a><a name="onerasemdiclientbackground"></a>CMDIFrameWndEx::OnEraseMDIClientBackground  
 Llamado por el marco cuando los procesos de ventana de marco de la MDI un `WM_ERASEBKGND` mensaje.  
  
```  
virtual BOOL OnEraseMDIClientBackground(CDC*);
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la aplicación procesa el mensaje y borra el fondo.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función miembro si desea procesar la `WM_ERASEBKGND` el mensaje en una `CMDIFrameWndEx`-clase derivada.  
  
##  <a name="a-nameonmenubuttontoolhittesta--cmdiframewndexonmenubuttontoolhittest"></a><a name="onmenubuttontoolhittest"></a>CMDIFrameWndEx::OnMenuButtonToolHitTest  
 Llamado por el marco cuando una [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)objeto procesos un `WM_NCHITTEST` mensaje.  
  
```  
virtual BOOL OnMenuButtonToolHitTest(
    CMFCToolBarButton* pButton,  
    TOOLINFO* pTI);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 El botón de barra de herramientas.  
  
 [out] `pTI`  
 Puntero a un [TOOLINFO](http://msdn.microsoft.com/library/windows/desktop/bb760256) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la aplicación rellena el `pTI` parámetro. La implementación predeterminada devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método si desea proporcionar información acerca de los elementos de menú a una información sobre herramientas. La implementación predeterminada no hace nada.  
  
##  <a name="a-nameonmoveminiframea--cmdiframewndexonmoveminiframe"></a><a name="onmoveminiframe"></a>CMDIFrameWndEx::OnMoveMiniFrame  
 Llamado por el marco para mover una ventana de marco reducido.  
  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pFrame`  
 Puntero a una ventana de marco reducido.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método tiene éxito, de lo contrario, `FALSE`.  
  
##  <a name="a-nameonsetpreviewmodea--cmdiframewndexonsetpreviewmode"></a><a name="onsetpreviewmode"></a>CMDIFrameWndEx::OnSetPreviewMode  
 Establece el modo de vista previa de impresión de ventana de marco principal de la aplicación.  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bPreview`  
 Si `TRUE`, Establece el modo de vista previa de impresión. Si `FALSE`, cancela el modo de vista previa.  
  
 [in] `pState`  
 Un puntero a un `CPrintPreviewState` estructura.  
  
### <a name="remarks"></a>Comentarios  
 Este método reemplaza [CFrameWnd::OnSetPreviewMode](../../mfc/reference/cframewnd-class.md#onsetpreviewmode).  
  
##  <a name="a-nameonshowcustomizepanea--cmdiframewndexonshowcustomizepane"></a><a name="onshowcustomizepane"></a>CMDIFrameWndEx::OnShowCustomizePane  
 Lo llama el marco de trabajo cuando se activa un panel personalizar rápida.  
  
```  
virtual BOOL OnShowCustomizePane(
    CMFCPopupMenu* pMenuPane,  
    UINT uiToolbarID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMenuPane`  
 Un puntero al panel personalizar rápida.  
  
 [in] `uiToolbarID`  
 Id. de control de la barra de herramientas para personalizar.  
  
### <a name="return-value"></a>Valor devuelto  
 Este método devuelve siempre `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 El panel Personalizar rápido es un menú que se abre cuando el usuario hace clic en **personalizar** en una barra de herramientas.  
  
 Invalide este método en una clase derivada para realizar cambios en el panel personalizar rápida.  
  
##  <a name="a-nameonshowmditabcontextmenua--cmdiframewndexonshowmditabcontextmenu"></a><a name="onshowmditabcontextmenu"></a>CMDIFrameWndEx::OnShowMDITabContextMenu  
 Lo llama el marco de trabajo antes de mostrar un menú contextual en una de las fichas. Válido para grupos con pestañas MDI sólo.  
  
```  
virtual BOOL OnShowMDITabContextMenu(
    CPoint point,  
    DWORD dwAllowedItems,  
    BOOL bTabDrop);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 La ubicación del menú en coordenadas de pantalla.  
  
 [in] `dwAllowedItems`  
 Una combinación de OR bit a bit de indicadores que indica qué acciones están permitidas para la ficha actual:  
  
- `BCGP_MDI_CREATE_VERT_GROUP`-puede crear un grupo de fichas vertical.  
  
- `BCGP_MDI_CREATE_HORZ_GROUP`-puede crear un grupo de pestañas horizontal.  
  
- `BCGP_MDI_CAN_MOVE_PREV`-puede mover una ficha al grupo de ficha anterior.  
  
- `BCGP_MDI_CAN_MOVE_NEXT`-puede mover una ficha al siguiente grupo de ficha.  
  
- `BCGP_MDI_CAN_BE_DOCKED`-cambie un documento con fichas a estado acoplado (relevante para los documentos con fichas sólo).  
  
 [in] `bTabDrop`  
 `TRUE`para mostrar el menú como resultado de arrastrar la ficha a otro grupo de pestañas. `FALSE`para mostrar el menú como menú contextual de la ficha activa actualmente.  
  
### <a name="return-value"></a>Valor devuelto  
 Invalide este método en un [CBCGPMDIFrameWnd](../../mfc/reference/cmdiframewndex-class.md)-clase derivada.  
  
### <a name="remarks"></a>Comentarios  
 Si no se procesan `OnShowMDITabContextMenu`, no se mostrará el menú contextual. Esta función genera la **Asistente para aplicaciones MFC** al habilitar la característica grupos de fichas de MDI.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo `OnShowMDITabContextMenu` se utiliza en el [ejemplo VisualStudioDemo: aplicación MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#14;](../../mfc/codesnippet/cpp/cmdiframewndex-class_13.cpp)]  
  
##  <a name="a-nameonshowpanesa--cmdiframewndexonshowpanes"></a><a name="onshowpanes"></a>CMDIFrameWndEx::OnShowPanes  
 Llamado por el marco de trabajo para mostrar u ocultar paneles.  
  
```  
virtual BOOL OnShowPanes(BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bShow`  
 `TRUE`para mostrar los paneles, `FALSE` para ocultar paneles.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si cambia el estado de los paneles como resultado de llamar a este método, `FALSE` si los paneles ya están en el estado especificado por `bShow`. Por ejemplo, si los paneles están ocultos y `bShow` es `FALSE`, el valor devuelto es `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada, quita la barra de herramientas de la ventana de marco de nivel superior.  
  
 Si [CDockingManager::m_bHideDockingBarsInContainerMode](../../mfc/reference/cdockingmanager-class.md#m_bhidedockingbarsincontainermode) es `TRUE` (valor predeterminado), se ocultarán todos los paneles de acoplamiento.  
  
##  <a name="a-nameonshowpopupmenua--cmdiframewndexonshowpopupmenu"></a><a name="onshowpopupmenu"></a>CMDIFrameWndEx::OnShowPopupMenu  
 Llamado por el marco de trabajo cuando se abre un menú emergente.  
  
```  
virtual BOOL OnShowPopupMenu(CMFCPopupMenu*);
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el menú emergente que se va a mostrarse. En caso contrario, es `FALSE`. La implementación predeterminada devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método si desea implementar un procesamiento especial al realizar la activación del menú emergente. Por ejemplo, si desea cambiar los elementos de menú habituales a los botones de menú de color, configurar las barras desplazable y así sucesivamente.  
  
 La implementación predeterminada no hace nada.  
  
##  <a name="a-nameonsizemdiclienta--cmdiframewndexonsizemdiclient"></a><a name="onsizemdiclient"></a>CMDIFrameWndEx::OnSizeMDIClient  
 Llamado por el marco de trabajo cuando está cambiando el tamaño de la ventana de cliente MDI.  
  
```  
virtual void OnSizeMDIClient(
    const CRect& rectOld,  
    const CRect& rectNew);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectOld`  
 El tamaño actual de la ventana de cliente MDI.  
  
 [in] `rectNew`  
 El nuevo tamaño de la ventana de cliente MDI.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameontearoffmenua--cmdiframewndexontearoffmenu"></a><a name="ontearoffmenu"></a>CMDIFrameWndEx::OnTearOffMenu  
 Lo llama el marco de trabajo cuando se activa un menú con barra desplazable.  
  
```  
virtual BOOL OnTearOffMenu(
    CMFCPopupMenu* pMenuPopup,  
    CPane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMenuPopup`  
 Un puntero al menú emergente.  
  
 [in] `pBar`  
 Puntero a la barra desplazable.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`para permitir que el menú emergente con la barra desplazable debe estar activa; de lo contrario, `FALSE`. De manera predeterminada, es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si desea implementar una configuración especial para la barra desplazable. La implementación predeterminada no hace nada.  
  
##  <a name="a-nameonupdateframemenua--cmdiframewndexonupdateframemenu"></a><a name="onupdateframemenu"></a>CMDIFrameWndEx::OnUpdateFrameMenu  
 Llamado por el marco de trabajo para actualizar el menú de marco.  
  
```  
virtual void OnUpdateFrameMenu(HMENU hMenuAlt);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hMenuAlt`  
 Identificador de un menú.  
  
##  <a name="a-namepanefrompointa--cmdiframewndexpanefrompoint"></a><a name="panefrompoint"></a>CMDIFrameWndEx::PaneFromPoint  
 Devuelve el panel acoplable que contiene el punto especificado.  
  
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
 El punto (en coordenadas de pantalla).  
  
 [in] `nSensitivity`  
 El rectángulo de la ventana de cada panel checked se aumenta en todas las direcciones en este valor.  
  
 [in] `bExactBar`  
 Si `TRUE`, el `nSensitivity` se omite el parámetro.  
  
 [in] `pRTCBarType`  
 Si no es `NULL`, el método recorre en iteración sólo los paneles del tipo especificado.  
  
 [out] `dwAlignment`  
 Si se encuentra un panel, este parámetro especificará qué lado del panel es más cercano al punto especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un panel acoplable o `NULL` si ningún control contiene el punto especificado por `point`.  
  
### <a name="remarks"></a>Comentarios  
 La llamada se redirige a la [CDockingManager clase](../../mfc/reference/cdockingmanager-class.md). Consulte [CDockingManager::ControlBarFromPoint](../../mfc/reference/cdockingmanager-class.md#panefrompoint) para obtener más información.  
  
##  <a name="a-namerecalclayouta--cmdiframewndexrecalclayout"></a><a name="recalclayout"></a>CMDIFrameWndEx::RecalcLayout  
 Llamado por el marco para volver a calcular el diseño de la ventana de marco.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bNotify`  
 Determina si el elemento en el contexto activo de la ventana de marco recibe la notificación de cambio de diseño. Si `TRUE`, el elemento es notificado; en caso contrario `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método reemplaza [RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout).  
  
##  <a name="a-nameremovepanefromdockmanagera--cmdiframewndexremovepanefromdockmanager"></a><a name="removepanefromdockmanager"></a>CMDIFrameWndEx::RemovePaneFromDockManager  
 Anula el registro de un panel y quita desde el Administrador de acoplamiento.  
  
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
 Un puntero a un panel que se va a quitar.  
  
 [in] `bDestroy`  
 `TRUE`para destruir el panel quitado. `FALSE`no destruirla.  
  
 [in] `bAdjustLayout`  
 `TRUE`Para ajustar el diseño de acoplamiento inmediatamente. Si `FALSE`, producirá el ajuste sólo cuando se produce un evento de actualización por otras razones (el usuario cambia el tamaño de la ventana, arrastra el marco principal, etcetera).  
  
 [in] `bAutoHide`  
 `TRUE`Para quitar el panel de la lista de paneles de ocultación automática. `FALSE`Para quitar el panel de la lista de paneles regulares.  
  
 [in] `pBarReplacement`  
 Puntero a un panel que reemplazará al panel quitado.  
  
### <a name="remarks"></a>Comentarios  
 Debe registrar cada panel con el Administrador de acoplamiento a participar en el diseño de acoplamiento. Utilice [CMDIFrameWndEx::AddPane](#addpane) o [CMDIFrameWndEx::InsertPane](#insertpane) para registrar los paneles.  
  
 Utilice este método cuando un panel ya no forma parte del diseño de acoplamiento de la ventana de marco.  
  
##  <a name="a-namesavemdistatea--cmdiframewndexsavemdistate"></a><a name="savemdistate"></a>CMDIFrameWndEx::SaveMDIState  
 Guarda el diseño actual de los grupos de fichas de MDI y la lista de documentos abiertos previamente.  
  
```  
virtual BOOL SaveMDIState(LPCTSTR lpszProfileName);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Especifica el nombre del perfil.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la operación de guardar se realizó correctamente; `FALSE` si no se pudo guardar.  
  
### <a name="remarks"></a>Comentarios  
 Para cargar o guardar el estado de las fichas MDI y grupos y la lista de los documentos abiertos, haga lo siguiente:  
  
-   Llame a `SaveMDIState` cuando se cierra el marco principal  
  
-   Llame a [CMDIFrameWndEx::LoadMDIState](#loadmdistate) cuando se cree el marco principal. La ubicación recomendada para esta llamada es antes de que el marco principal se muestra por primera vez.  
  
-   Llame a `CWinAppEx::EnableLoadWindowPlacement(FALSE);` antes de`pMainFrame->LoadFrame (IDR_MAINFRAME);`  
  
-   Llame a `CWinAppEx::ReloadWindowPlacement``(pMainFrame)` después `LoadMDIState` para mostrar el marco principal en la posición en la que se almacena en el registro.  
  
-   Invalidar `GetDocumentName` en el `CMDIChildWndEx`-clase derivada si la aplicación muestra los documentos que no se almacenan como archivos. La cadena devuelta se guardará en el registro como un identificador de documento. Para obtener más información, consulte [CMDIChildWndEx::GetDocumentName](../../mfc/reference/cmdichildwndex-class.md#getdocumentname).  
  
-   Invalidar [CMDIFrameWndEx::CreateDocumentWindow](#createdocumentwindow) crear correctamente documentos cuando se cargan desde el registro. El parámetro `CreateDocumentWindow` es una cadena que `GetDocumentName` anteriormente devuelto.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo `SaveMDIState` se utiliza en el [ejemplo VisualStudioDemo: aplicación MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#15;](../../mfc/codesnippet/cpp/cmdiframewndex-class_14.cpp)]  
  
##  <a name="a-namesetprintpreviewframea--cmdiframewndexsetprintpreviewframe"></a><a name="setprintpreviewframe"></a>CMDIFrameWndEx::SetPrintPreviewFrame  
 Establece la ventana de marco de vista previa de impresión.  
  
```  
void SetPrintPreviewFrame(CFrameWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Puntero a una ventana de marco de vista previa de impresión.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetuptoolbarmenua--cmdiframewndexsetuptoolbarmenu"></a><a name="setuptoolbarmenu"></a>CMDIFrameWndEx::SetupToolbarMenu  
 Modifica un objeto de barra de herramientas reemplazando elementos ficticios con elementos definidos por el usuario.  
  
```  
void SetupToolbarMenu(
    CMenu& menu,  
    const UINT uiViewUserToolbarCmdFirst,  
    const UINT uiViewUserToolbarCmdLast);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `menu`  
 Una referencia a un [CMenu (clase)](../../mfc/reference/cmenu-class.md) objeto que desee modificar.  
  
 [in] `uiViewUserToolbarCmdFirst`  
 Especifica el primer comando definido por el usuario.  
  
 [in] `uiViewUserToolbarCmdLast`  
 Especifica el último comando definido por el usuario.  
  
##  <a name="a-nameshowfullscreena--cmdiframewndexshowfullscreen"></a><a name="showfullscreen"></a>CMDIFrameWndEx::ShowFullScreen  
 Cambia el marco principal de modo normal al modo de pantalla completa.  
  
```  
void ShowFullScreen();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameshowpanea--cmdiframewndexshowpane"></a><a name="showpane"></a>CMDIFrameWndEx::ShowPane  
 Muestra u oculta el panel especificado.  
  
```  
void ShowPane(
    CBasePane* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Puntero al panel para mostrar u ocultar.  
  
 [in] `bShow`  
 `TRUE`para mostrar el panel. `FALSE`Para ocultar el panel.  
  
 [in] `bDelay`  
 `TRUE`Para retrasar la actualización del diseño de acoplamiento. `FALSE`Para volver a calcular el diseño de acoplamiento inmediatamente.  
  
 [in] `bActivate`  
 `TRUE`para mostrar el panel debe como activa. `FALSE`para mostrar el panel como inactiva.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para mostrar u ocultar el panel. No utilice `ShowWindow` para acoplar paneles.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo `ShowPane` se utiliza en el [ejemplo VisualStudioDemo: aplicación MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo Nº&16;](../../mfc/codesnippet/cpp/cmdiframewndex-class_15.cpp)]  
  
##  <a name="a-nameshowwindowsdialoga--cmdiframewndexshowwindowsdialog"></a><a name="showwindowsdialog"></a>CMDIFrameWndEx::ShowWindowsDialog  
 Crea un [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) cuadro y lo abre.  
  
```  
void ShowWindowsDialog();
```  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo `ShowWindowsDialog` se utiliza en el [ejemplo VisualStudioDemo: aplicación MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#18;](../../mfc/codesnippet/cpp/cmdiframewndex-class_16.cpp)]  
  
##  <a name="a-nametabbeddocumenttocontrolbara--cmdiframewndextabbeddocumenttocontrolbar"></a><a name="tabbeddocumenttocontrolbar"></a>CMDIFrameWndEx::TabbedDocumentToControlBar  
 Convierte el documento con fichas especificado a un panel acoplable.  
  
```  
virtual BOOL TabbedDocumentToControlBar(CMDIChildWndEx* pMDIChildWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pMDIChildWnd`  
 Puntero a la ventana secundaria MDI que contiene un panel acoplable.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método se realizó correctamente, `FALSE` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para convertir un documento con fichas en un panel acoplable. Las fichas se deben haber creado utilizando [CMDIFrameWndEx::ControlBarToTabbedDocument](#controlbartotabbeddocument).  
  
### <a name="example"></a>Ejemplo  
 El ejemplo siguiente se muestra cómo `TabbedDocumentToControlBar` se utiliza en el [ejemplo VisualStudioDemo: aplicación MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo Nº&19;](../../mfc/codesnippet/cpp/cmdiframewndex-class_17.cpp)]  
  
##  <a name="a-nameupdatecaptiona--cmdiframewndexupdatecaption"></a><a name="updatecaption"></a>CMDIFrameWndEx::UpdateCaption  
 Llamado por el marco de trabajo para actualizar el título del marco de ventana.  
  
```  
void UpdateCaption();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameupdatemditabbedbarsiconsa--cmdiframewndexupdatemditabbedbarsicons"></a><a name="updatemditabbedbarsicons"></a>CMDIFrameWndEx::UpdateMDITabbedBarsIcons  
 Establece el icono de cada panel con fichas de MDI.  
  
```  
void UpdateMDITabbedBarsIcons();
```  
  
##  <a name="a-namewinhelpa--cmdiframewndexwinhelp"></a><a name="winhelp"></a>CMDIFrameWndEx::WinHelp  
 Lo llama el marco para iniciar la aplicación o la ayuda contextual de WinHelp.  
  
```  
virtual void WinHelp(
    DWORD dwData,  
    UINT nCmd = HELP_CONTEXT);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwData`  
 Especifica datos según sea necesario para el tipo de ayuda indicado por `nCmd`.  
  
 [in] `nCmd`  
 Especifica el tipo de ayuda solicitado. Para obtener una lista de valores posibles y cómo afectan al parámetro `dwData` , consulte la [función WinHelp](http://msdn.microsoft.com/library/windows/desktop/bb762267) en Windows SDK.  
  
### <a name="remarks"></a>Comentarios  
 Este método reemplaza [CWnd::WinHelp](../../mfc/reference/cwnd-class.md#winhelp).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMDIFrameWnd](../../mfc/reference/cframewnd-class.md)   
 [Clase CMDIChildWndEx](../../mfc/reference/cmdichildwndex-class.md)

