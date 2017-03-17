---
title: Clase CMDIChildWndEx | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMDIChildWndEx
- AFXMDICHILDWNDEX/CMDIChildWndEx
- AFXMDICHILDWNDEX/CMDIChildWndEx::ActivateTopLevelFrame
- AFXMDICHILDWNDEX/CMDIChildWndEx::AddPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::AddTabbedPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::AdjustDockingLayout
- AFXMDICHILDWNDEX/CMDIChildWndEx::CanShowOnMDITabs
- AFXMDICHILDWNDEX/CMDIChildWndEx::CanShowOnTaskBarTabs
- AFXMDICHILDWNDEX/CMDIChildWndEx::CanShowOnWindowsList
- AFXMDICHILDWNDEX/CMDIChildWndEx::DockPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::DockPaneLeftOf
- AFXMDICHILDWNDEX/CMDIChildWndEx::EnableAutoHidePanes
- AFXMDICHILDWNDEX/CMDIChildWndEx::EnableDocking
- AFXMDICHILDWNDEX/CMDIChildWndEx::EnableTaskbarThumbnailClipRect
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetDockingManager
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetDocumentName
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetFrameIcon
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetFrameText
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetRelatedTabGroup
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTabbedPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTabProxyWnd
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTaskbarPreviewWnd
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTaskbarThumbnailClipRect
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetToolbarButtonToolTipText
- AFXMDICHILDWNDEX/CMDIChildWndEx::InsertPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::InvalidateIconicBitmaps
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsPointNearDockSite
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsReadOnly
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsRegisteredWithTaskbarTabs
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsTabbedPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsTaskbarTabsSupportEnabled
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled
- AFXMDICHILDWNDEX/CMDIChildWndEx::m_dwDefaultTaskbarTabPropertyFlags
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnGetIconicLivePreviewBitmap
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnGetIconicThumbnail
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnMoveMiniFrame
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnSetPreviewMode
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnTaskbarTabThumbnailActivate
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnTaskbarTabThumbnailStretch
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnUpdateFrameTitle
- AFXMDICHILDWNDEX/CMDIChildWndEx::PaneFromPoint
- AFXMDICHILDWNDEX/CMDIChildWndEx::RecalcLayout
- AFXMDICHILDWNDEX/CMDIChildWndEx::RegisterTaskbarTab
- AFXMDICHILDWNDEX/CMDIChildWndEx::RemovePaneFromDockManager
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetRelatedTabGroup
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarTabActive
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarTabOrder
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarTabProperties
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarThumbnailClipRect
- AFXMDICHILDWNDEX/CMDIChildWndEx::ShowPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::UnregisterTaskbarTab
- AFXMDICHILDWNDEX/CMDIChildWndEx::UpdateTaskbarTabIcon
dev_langs:
- C++
helpviewer_keywords:
- CMDIChildWndEx class
- ActivateFrame method
- PreTranslateMessage method
- GetThisClass method
- CreateObject method
ms.assetid: d39fec06-0bd6-4271-917d-35aae3b24d8e
caps.latest.revision: 35
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
ms.openlocfilehash: 016de8fdade75376f9f081539c0f160a6502bc37
ms.lasthandoff: 02/24/2017

---
# <a name="cmdichildwndex-class"></a>Clase CMDIChildWndEx
La `CMDIChildWndEx` clase proporciona la funcionalidad de Windows ventana secundaria MDI (interfaz) de varios documentos. Amplía la funcionalidad de [CMDIChildWnd (clase)](../../mfc/reference/cmdichildwnd-class.md). El marco requiere esta clase cuando una aplicación MDI utiliza determinadas clases MFC.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMDIChildWndEx : public CMDIChildWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMDIChildWndEx::ActivateTopLevelFrame](#activatetoplevelframe)|Se llama internamente el marco de trabajo para activar marco de nivel superior cuando la aplicación debe activarse desde una ficha de la barra de tareas.|  
|`CMDIChildWndEx::AddDockSite`|Este método no se utiliza o implementado.|  
|[CMDIChildWndEx::AddPane](#addpane)|Agrega un panel.|  
|[CMDIChildWndEx::AddTabbedPane](#addtabbedpane)|Agrega un panel con fichas.|  
|[CMDIChildWndEx::AdjustDockingLayout](#adjustdockinglayout)|Ajusta el diseño de acoplamiento.|  
|[CMDIChildWndEx::CanShowOnMDITabs](#canshowonmditabs)||  
|[CMDIChildWndEx::CanShowOnTaskBarTabs](#canshowontaskbartabs)|Indica que el marco de trabajo si se puede mostrar este elemento secundario MDI en fichas de la barra de tareas de Windows 7.|  
|[CMDIChildWndEx::CanShowOnWindowsList](#canshowonwindowslist)|Devuelve `TRUE` si el nombre de ventana secundaria MDI puede mostrarse en el [CMFCWindowsManagerDialog clase](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) cuadro de diálogo. De lo contrario, devuelve `FALSE`.|  
|`CMDIChildWndEx::CreateObject`|Llamado por el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMDIChildWndEx::DockPane](#dockpane)|Un panel se acopla.|  
|[CMDIChildWndEx::DockPaneLeftOf](#dockpaneleftof)|Acopla un panel a la izquierda de otro panel.|  
|[CMDIChildWndEx::EnableAutoHidePanes](#enableautohidepanes)|Permite oculta automáticamente el modo de paneles cuando se acoplan a los lados de la ventana especificados.|  
|[CMDIChildWndEx::EnableDocking](#enabledocking)|Permite acoplar de la ventana secundaria en el marco principal.|  
|[CMDIChildWndEx::EnableTaskbarThumbnailClipRect](#enabletaskbarthumbnailcliprect)|Habilita o deshabilita la selección automática de una parte del área de cliente de una ventana para mostrar como miniatura de la ventana en la barra de tareas.|  
|[CMDIChildWndEx::GetDockingManager](#getdockingmanager)||  
|[CMDIChildWndEx::GetDocumentName](#getdocumentname)|Devuelve el nombre del documento que se muestra en la ventana secundaria MDI.|  
|[CMDIChildWndEx::GetFrameIcon](#getframeicon)|Llamado por el marco de trabajo para recuperar el icono de ventana secundaria MDI.|  
|[CMDIChildWndEx::GetFrameText](#getframetext)|Llamado por el marco de trabajo para recuperar el texto de la ventana secundaria MDI.|  
|[CMDIChildWndEx::GetPane](#getpane)|Busca un panel mediante el identificador de control especificado.|  
|[CMDIChildWndEx::GetRelatedTabGroup](#getrelatedtabgroup)||  
|[CMDIChildWndEx::GetTabbedPane](#gettabbedpane)|Devuelve un puntero a un panel acoplable incrustado que se convirtió en un documento con fichas.|  
|[CMDIChildWndEx::GetTabProxyWnd](#gettabproxywnd)|Devuelve la pestaña ventana proxy registrada con fichas de la barra de tareas de Windows 7.|  
|[CMDIChildWndEx::GetTaskbarPreviewWnd](#gettaskbarpreviewwnd)|Llamado por el marco de trabajo cuando se necesita obtener una ventana secundaria (normalmente una ventana de vista o divisor) que se mostrará en la miniatura de ficha barra de tareas de Windows 7.|  
|[CMDIChildWndEx::GetTaskbarThumbnailClipRect](#gettaskbarthumbnailcliprect)|Llamado por el marco cuando sea necesario seleccionar una parte del área de cliente de una ventana para mostrar como miniatura de la ventana en la barra de tareas.|  
|`CMDIChildWndEx::GetThisClass`|Llamado por el marco para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMDIChildWndEx::GetToolbarButtonToolTipText](#gettoolbarbuttontooltiptext)|Llamado por el marco de trabajo para recuperar información sobre herramientas para un botón de barra de herramientas.|  
|[CMDIChildWndEx::InsertPane](#insertpane)|El panel especificado se registra con el Administrador de acoplamiento.|  
|[CMDIChildWndEx::InvalidateIconicBitmaps](#invalidateiconicbitmaps)|Invalida la representación del mapa de iconos de formulario secundario MDI.|  
|[CMDIChildWndEx::IsPointNearDockSite](#ispointneardocksite)|Determina si un punto especificado está cerca del sitio de vinculación.|  
|[CMDIChildWndEx::IsReadOnly](#isreadonly)|Devuelve `TRUE` si el documento que se muestra en la ventana secundaria es de sólo lectura. De lo contrario, devuelve `FALSE`.|  
|[CMDIChildWndEx::IsRegisteredWithTaskbarTabs](#isregisteredwithtaskbartabs)|Devuelve TRUE si el formulario secundario MDI con fichas de la barra de tareas de Windows 7 se ha registrado correctamente.|  
|[CMDIChildWndEx::IsTabbedPane](#istabbedpane)|Devuelve `TRUE` si la ventana secundaria MDI contiene un panel acoplable. De lo contrario, devuelve `FALSE`.|  
|[CMDIChildWndEx::IsTaskbarTabsSupportEnabled](#istaskbartabssupportenabled)|Indica si el formulario MDI secundario puede aparecer en las fichas de la barra de tareas de Windows 7.|  
|[CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled](#istaskbarthumbnailcliprectenabled)|Indica si la selección automática de una parte del área de cliente de una ventana para mostrar como miniatura de la ventana en la barra de tareas está habilitada o deshabilitada.|  
|[CMDIChildWndEx::m_dwDefaultTaskbarTabPropertyFlags](#m_dwdefaulttaskbartabpropertyflags)|Una combinación de indicadores, que se pasa por el marco de trabajo para el método SetTaskbarTabProperties, cuando se está registrando una pestaña (elemento secundario MDI) con fichas de la barra de tareas de Windows 7. La combinación predeterminada es STPF_USEAPPTHUMBNAILWHENACTIVE | STPF_USEAPPPEEKWHENACTIVE.|  
|[CMDIChildWndEx::OnGetIconicLivePreviewBitmap](#ongeticoniclivepreviewbitmap)|Llamado por el marco cuando sea necesario obtener un mapa de bits para la vista previa activa de formulario secundario MDI.|  
|[CMDIChildWndEx::OnGetIconicThumbnail](#ongeticonicthumbnail)|Llamado por el marco cuando sea necesario obtener un mapa de bits para icónica miniatura del elemento secundario MDI.|  
|[CMDIChildWndEx::OnMoveMiniFrame](#onmoveminiframe)|Llamado por el marco para mover una ventana de marco reducido.|  
|[CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton](#onpresstaskbarthmbnailclosebutton)|Llamado por el marco de trabajo cuando el usuario presiona el botón Cerrar en la miniatura de la ficha de barra de tareas...|  
|[CMDIChildWndEx::OnSetPreviewMode](#onsetpreviewmode)|Llamado por el marco para entrar o salir del modo de vista previa de impresión.|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailActivate](#ontaskbartabthumbnailactivate)|Llamado por el marco de trabajo cuando la miniatura de la ficha barra de tareas debe procesar el mensaje WM_ACTIVATE.|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate](#ontaskbartabthumbnailmouseactivate)|Llamado por el marco de trabajo cuando la miniatura de la ficha barra de tareas debe procesar el mensaje WM_MOUSEACTIVATE.|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailStretch](#ontaskbartabthumbnailstretch)|Llamado por el marco cuando sea necesario ajustar un mapa de bits de Windows 7 barra de tareas ficha Vista previa en miniatura del elemento secundario MDI.|  
|[CMDIChildWndEx::OnUpdateFrameTitle](#onupdateframetitle)|Llamado por el marco de trabajo para actualizar el título de marco. (Invalida `CMDIChildWnd::OnUpdateFrameTitle`).|  
|[CMDIChildWndEx::PaneFromPoint](#panefrompoint)|Devuelve el panel que contiene el punto especificado.|  
|`CMDIChildWndEx::PreTranslateMessage`|Utilizado por la clase [CWinApp](../../mfc/reference/cwinapp-class.md) para traducir los mensajes de ventana antes de que se envíen a la [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funciones de Windows. (Invalida [CWnd:: PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMDIChildWndEx::RecalcLayout](#recalclayout)|Vuelve a calcular el diseño de la ventana.|  
|[CMDIChildWndEx::RegisterTaskbarTab](#registertaskbartab)|Registra el formulario secundario MDI con fichas de la barra de tareas de Windows 7.|  
|[CMDIChildWndEx::RemovePaneFromDockManager](#removepanefromdockmanager)|Quita un panel desde el Administrador de acoplamiento.|  
|[CMDIChildWndEx::SetRelatedTabGroup](#setrelatedtabgroup)||  
|[CMDIChildWndEx::SetTaskbarTabActive](#settaskbartabactive)|Activa la pestaña correspondiente de barra de tareas de Windows 7.|  
|[CMDIChildWndEx::SetTaskbarTabOrder](#settaskbartaborder)|Inserta el elemento secundario MDI antes de la ventana especificada en las fichas de la barra de tareas de Windows 7.|  
|[CMDIChildWndEx::SetTaskbarTabProperties](#settaskbartabproperties)|Establece las propiedades de una pestaña de la barra de tareas de Windows 7.|  
|[CMDIChildWndEx::SetTaskbarThumbnailClipRect](#settaskbarthumbnailcliprect)|Se llama internamente por el marco de trabajo para establecer el rectángulo de recorte para seleccionar una parte del área de cliente de una ventana para mostrar como miniatura de la ventana en la barra de tareas.|  
|[CMDIChildWndEx::ShowPane](#showpane)||  
|[CMDIChildWndEx::UnregisterTaskbarTab](#unregistertaskbartab)|Quita el formulario secundario MDI de fichas de la barra de tareas de Windows 7.|  
|[CMDIChildWndEx::UpdateTaskbarTabIcon](#updatetaskbartabicon)|Actualiza el icono de tabulación de barra de tareas de Windows 7.|  
  
## <a name="remarks"></a>Comentarios  
 Para sacar partido de las características extendidas de acoplamiento en aplicaciones MDI, derive la clase de ventana secundaria MDI de la aplicación de `CMDIChildWndEx` en lugar de [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se deriva una clase de `CMDIChildWndEx`. Este fragmento de código procede de la [ejemplo VisualStudioDemo: aplicación MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&3;](../../mfc/codesnippet/cpp/cmdichildwndex-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)  
  
 [CMDIChildWndEx](../../mfc/reference/cmdichildwndex-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxMDIChildWndEx.h  
  
##  <a name="addpane"></a>CMDIChildWndEx::AddPane  
 Agrega un panel.  
  
```  
BOOL AddPane(
    CBasePane* pControlBar,  
    BOOL bTail = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pControlBar`  
 Un puntero al panel.  
  
 [in] `bTail`  
 `TRUE`Para agregar el panel al final de la lista de paneles para el Administrador de acoplamiento; de lo contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se registró correctamente con el Administrador de acoplamiento; de lo contrario, `FALSE`.  
  
##  <a name="addtabbedpane"></a>CMDIChildWndEx::AddTabbedPane  
 Agrega un panel con fichas.  
  
```  
void AddTabbedPane(CDockablePane* pControlBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pControlBar`  
 Un puntero al panel.  
  
##  <a name="adjustdockinglayout"></a>CMDIChildWndEx::AdjustDockingLayout  
 Ajusta el diseño de acoplamiento.  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hdwp`  
 Identificador de una estructura de posición de la ventana aplazada.  
  
##  <a name="canshowonmditabs"></a>CMDIChildWndEx::CanShowOnMDITabs  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanShowOnMDITabs();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="canshowonwindowslist"></a>CMDIChildWndEx::CanShowOnWindowsList  
 Especifica si se puede mostrar el nombre de ventana secundaria MDI en la [CMFCWindowsManagerDialog clase](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) cuadro de diálogo.  
  
```  
virtual BOOL CanShowOnWindowsList();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la ventana se puede mostrar en el **Windows** cuadro de diálogo; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada y devolver `FALSE` si no se debe mostrar la ventana en la **Windows** cuadro de diálogo. Esta función se llama desde `CMFCWindowsManagerDialog`.  
  
##  <a name="dockpane"></a>CMDIChildWndEx::DockPane  
 Un panel se acopla.  
  
```  
void DockPane(
    CBasePane* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Un puntero al panel.  
  
 [in] `nDockBarID`  
 El identificador del panel.  
  
 [in] `lpRect`  
 Un puntero a un rectángulo.  
  
### <a name="remarks"></a>Comentarios  
 El `lpRect` no se utiliza el parámetro.  
  
##  <a name="dockpaneleftof"></a>CMDIChildWndEx::DockPaneLeftOf  
 Acopla un panel a la izquierda de otro panel.  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBar,  
    CPane* pLeftOf);
```  
  
### <a name="parameters"></a>Parámetros  
 `pBar`  
 Un puntero en el panel que está acoplada.  
  
 `pLeftOf`  
 Un puntero al panel que sirve como punto de referencia.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`en caso de éxito, `FALSE` en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método toma el panel especificado por `pBar` y lo acopla en el lado izquierdo del panel especificado por `pLeftOf`.  
  
 Llamar a este método cuando desee acoplar varios paneles en un orden predefinido.  
  
##  <a name="enableautohidepanes"></a>CMDIChildWndEx::EnableAutoHidePanes  
 Permite oculta automáticamente el modo de paneles cuando se acoplan a los lados de la ventana especificados.  
  
```  
BOOL EnableAutoHidePanes(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwDockStyle`  
 Especifica los lados de la ventana de marco principal está habilitado. Utilice uno o varios de los siguientes indicadores.  
  
- `CBRS_ALIGN_LEFT`  
  
- `CBRS_ALIGN_RIGHT`  
  
- `CBRS_ALIGN_TOP`  
  
- `CBRS_ALIGN_BOTTOM`  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método tiene éxito; de lo contrario, `FALSE`.  
  
##  <a name="enabledocking"></a>CMDIChildWndEx::EnableDocking  
 Permite acoplar de la ventana secundaria en el marco principal.  
  
```  
BOOL EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwDockStyle`  
 Especifica la alineación de acoplamiento para habilitar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método tiene éxito; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para activar la alineación de acoplamiento en el marco principal. Puede pasar una combinación de indicadores CBRS_ALIGN_ (para obtener más información, consulte [CControlBar:: EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking)).  
  
##  <a name="getdockingmanager"></a>CMDIChildWndEx::GetDockingManager  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CDockingManager* GetDockingManager();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getdocumentname"></a>CMDIChildWndEx::GetDocumentName  
 Devuelve el nombre del documento que se muestra en la ventana secundaria MDI.  
  
```  
virtual LPCTSTR GetDocumentName(CObject** pObj);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a una cadena que contiene el nombre de un documento.  
  
### <a name="remarks"></a>Comentarios  
 Un documento es lo que muestra la ventana secundaria MDI. Por lo general, la ventana muestra los datos que están cargados o guardados en un archivo. Por lo tanto, el nombre del documento es el nombre del archivo. La implementación predeterminada de `GetDocumentName` devuelve una cadena obtenida de `CDocument::GetPathName`.  
  
 Si la ventana muestra un documento que no se carga desde un archivo, invalide este método en una clase derivada y devuelven un identificador de documento único.  
  
 `GetDocumentName`se llama el marco de trabajo cuando guarda el estado de todos los documentos abiertos. La cadena devuelta se escribe en el registro.  
  
 Cuando el marco de trabajo es restaurar el estado más adelante, el nombre del documento es leer desde el registro y se pasa al [CMDIFrameWndEx::CreateDocumentWindow](../../mfc/reference/cmdiframewndex-class.md#createdocumentwindow). Invalide este método en un [CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)-clase derivada y crear o abrir un documento que tiene este nombre y leer el archivo con este nombre. Si el documento no se basa en un archivo, crear del documento basándose en el identificador del documento. Debe realizar las acciones anteriores sólo si desea guardar y restaurar los documentos.  
  
### <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso del método `GetDocumentName`. Este fragmento de código procede de la [ejemplo VisualStudioDemo: aplicación MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#17;](../../mfc/codesnippet/cpp/cmdichildwndex-class_2.cpp)]  
  
##  <a name="getframeicon"></a>CMDIChildWndEx::GetFrameIcon  
 Llamado por el marco de trabajo para recuperar el icono de la ventana secundaria MDI.  
  
```  
virtual HICON GetFrameIcon() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador de un icono de la ventana.  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama el marco de trabajo para determinar qué icono se mostrará en la ficha MDI que contiene la ventana de marco secundaria MDI.  
  
 De forma predeterminada, este método devuelve el icono de la ventana. Invalidar `GetFrameIcon` en un `CMDIChildWndEx`-clase derivada para personalizar este comportamiento.  
  
##  <a name="getframetext"></a>CMDIChildWndEx::GetFrameText  
 Llamado por el marco de trabajo para recuperar el texto de la ventana secundaria MDI.  
  
```  
virtual CString GetFrameText() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Cadena que contiene el texto de la ventana de marco.  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama el marco de trabajo para determinar el texto que aparecerá en la ficha MDI que contiene la ventana de marco secundaria MDI.  
  
 De forma predeterminada, este método devuelve el texto de la ventana. Invalidar `GetFrameText` en un `CMDIChildWndEx`-clase derivada para personalizar este comportamiento.  
  
##  <a name="getpane"></a>CMDIChildWndEx::GetPane  
 Busca un panel mediante el identificador de control especificado.  
  
```  
CBasePane* GetPane(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 El identificador de control del panel a buscar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al panel si se encuentra, de lo contrario, `NULL`.  
  
##  <a name="getrelatedtabgroup"></a>CMDIChildWndEx::GetRelatedTabGroup  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCTabCtrl* GetRelatedTabGroup();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gettabbedpane"></a>CMDIChildWndEx::GetTabbedPane  
 Devuelve un puntero a un panel acoplable que forma parte de un grupo de MDI con fichas de documentos.  
  
```  
CDockablePane* GetTabbedPane() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un panel acoplable que forma parte de un grupo de MDI con fichas de documentos.  
  
##  <a name="gettoolbarbuttontooltiptext"></a>CMDIChildWndEx::GetToolbarButtonToolTipText  
 Llamado por el marco de trabajo para recuperar información sobre herramientas para un botón de barra de herramientas.  
  
```  
virtual BOOL GetToolbarButtonToolTipText(
    CMFCToolBarButton*, 
    CString&);
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se ha mostrado la información sobre herramientas. La implementación predeterminada devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método si desea mostrar información sobre herramientas personalizado para los botones de barra de herramientas.  
  
##  <a name="insertpane"></a>CMDIChildWndEx::InsertPane  
 El panel especificado se registra con el Administrador de acoplamiento.  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pControlBar`  
 Un puntero al panel para insertar.  
  
 [in] `pTarget`  
 Un puntero en el panel adyacente.  
  
 [in] `bAfter`  
 Si `TRUE`, `pControlBar` se inserta después `pTarget`. Si `FALSE`, `pControlBar` se insertará antes de `pTarget`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método tiene éxito, `FALSE` en caso contrario.  
  
##  <a name="ispointneardocksite"></a>CMDIChildWndEx::IsPointNearDockSite  
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
  
 [in] `dwBarAlignment`  
 Especifica qué borde es el punto de cerca. Los valores posibles son `CBRS_ALIGN_LEFT`, `CBRS_ALIGN_RIGHT`, `CBRS_ALIGN_TOP`, y`CBRS_ALIGN_BOTTOM`  
  
 [in] `bOuterEdge`  
 `TRUE`Si el punto está cerca del borde exterior del sitio de vinculación; `FALSE` en caso contrario.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el punto está cerca del sitio de vinculación; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El punto está cerca del sitio de vinculación cuando se encuentra dentro de la sensibilidad establecida en el Administrador de acoplamiento. La sensibilidad predeterminado es 15 píxeles.  
  
##  <a name="isreadonly"></a>CMDIChildWndEx::IsReadOnly  
 Especifica si el documento que se muestra en la ventana secundaria es de solo lectura.  
  
```  
virtual BOOL IsReadOnly();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el documento es de sólo lectura; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se utiliza para evitar que se guarden de documentos de sólo lectura.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo reemplazar el `IsReadOnly` método. Este fragmento de código procede de la [ejemplo VisualStudioDemo: aplicación MFC de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#2;](../../mfc/codesnippet/cpp/cmdichildwndex-class_3.cpp)]  
  
##  <a name="istabbedpane"></a>CMDIChildWndEx::IsTabbedPane  
 Especifica si la ventana secundaria MDI contiene un panel acoplable.  
  
```  
BOOL IsTabbedPane() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la ventana secundaria MDI contiene un panel acoplable que se convirtió en un documento con fichas; de lo contrario, `FALSE`.  
  
##  <a name="onmoveminiframe"></a>CMDIChildWndEx::OnMoveMiniFrame  
 Llamado por el marco para mover una ventana de marco reducido.  
  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pFrame`  
 Puntero a una ventana de marco reducido.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método tiene éxito, de lo contrario, `FALSE`.  
  
##  <a name="onsetpreviewmode"></a>CMDIChildWndEx::OnSetPreviewMode  
 Llamado por el marco para entrar o salir del modo de vista previa de impresión.  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bPreview`  
 Si `TRUE`, entrar en modo de vista previa de impresión. Si `FALSE`, salir del modo de vista previa de impresión.  
  
 [in] `pState`  
 Puntero a la estructura de estado de vista previa de impresión.  
  
##  <a name="onupdateframetitle"></a>CMDIChildWndEx::OnUpdateFrameTitle  
 Llamado por el marco de trabajo para actualizar el título de marco.  
  
```  
virtual void OnUpdateFrameTitle(BOOL bAddToTitle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bAddToTitle`  
 Si `TRUE`, agregue el nombre del documento al título.  
  
##  <a name="panefrompoint"></a>CMDIChildWndEx::PaneFromPoint  
 Devuelve el panel que contiene el punto especificado.  
  
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
 Especifica el punto, en coordenadas de pantalla para comprobar.  
  
 [in] `nSensitivity`  
 Aumentar el área de búsqueda en esta cantidad. Un panel satisface los criterios de búsqueda si el punto especificado se encuentra en el área de aumento.  
  
 [in] `bExactBar`  
 `TRUE`para omitir la `nSensitivity` parámetro; en caso contrario, `FALSE`.  
  
 [in] `pRTCBarType`  
 Si no `NULL`, el método busca solo los paneles del tipo especificado.  
  
 [in] `dwAlignment`  
 Si un panel se encuentra en el punto especificado, este parámetro contiene el lado del panel que era más cercano al punto especificado. Para obtener más información, vea la sección Comentarios.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `CBasePane`-objeto derivado que contiene el punto especificado, o `NULL` si no se encontró ningún panel.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para determinar si un panel contiene el punto especificado según las condiciones especificadas como clase en tiempo de ejecución y visibilidad.  
  
 Cuando se devuelve la función y se encontró un panel, `dwAlignment` contiene la alineación del punto especificado. Por ejemplo, si el punto era más cercano a la parte superior del panel, `dwAlignment` está establecido en `CBRS_ALIGN_TOP`.  
  
##  <a name="recalclayout"></a>CMDIChildWndEx::RecalcLayout  
 Vuelve a calcular el diseño de la ventana.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bNotify`  
 Si `TRUE`, el elemento en el contexto activo de la ventana recibe la notificación de cambio de diseño.  
  
##  <a name="removepanefromdockmanager"></a>CMDIChildWndEx::RemovePaneFromDockManager  
 Quita un panel desde el Administrador de acoplamiento.  
  
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
 Un puntero al panel para quitar.  
  
 [in] `bDestroy`  
 Si `TRUE`, se destruye el panel quitado.  
  
 [in] `bAdjustLayout`  
 Si `TRUE`, ajustar el diseño de acoplamiento inmediatamente.  
  
 [in] `bAutoHide`  
 Si `TRUE`, la lista de barras Ocultar automáticamente está relacionado con el diseño de acoplamiento. Si `FALSE`, está relacionado con el diseño de acoplamiento a la lista de paneles regulares.  
  
 [in] `pBarReplacement`  
 Puntero a un panel que reemplazará al panel quitado.  
  
##  <a name="setrelatedtabgroup"></a>CMDIChildWndEx::SetRelatedTabGroup  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetRelatedTabGroup(CMFCTabCtrl* p);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `p`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="showpane"></a>CMDIChildWndEx::ShowPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
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
  
##  <a name="updatetaskbartabicon"></a>CMDIChildWndEx::UpdateTaskbarTabIcon  
 Actualiza el icono de tabulación de la barra de tareas de Windows 7.  
  
```  
virtual void UpdateTaskbarTabIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>Parámetros  
 `hIcon`  
 Identificador de un icono para mostrar en la ficha de la barra de tareas de Windows 7.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="unregistertaskbartab"></a>CMDIChildWndEx::UnregisterTaskbarTab  
 Quita al elemento secundario MDI de fichas de la barra de tareas de Windows 7.  
  
```  
void UnregisterTaskbarTab(BOOL bCheckRegisteredMDIChildCount = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bCheckRegisteredMDIChildCount`  
 Especifica si esta función se debe comprobar el número de elementos secundarios MDI registrado con fichas MDI. Si este número es 0, esta función quita el rectángulo de recorte de la miniatura de la barra de tareas de la aplicación.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="settaskbarthumbnailcliprect"></a>CMDIChildWndEx::SetTaskbarThumbnailClipRect  
 Llamado por el marco para establecer el rectángulo de recorte para seleccionar una parte del área de cliente de una ventana para mostrar como miniatura de la ventana en la barra de tareas.  
  
```  
virtual BOOL SetTaskbarThumbnailClipRect(CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 `rect`  
 Especifica el nuevo rectángulo de recorte. Si el rectángulo está vacío o nulo, se quitará el recorte.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si es correcto; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="settaskbartabproperties"></a>CMDIChildWndEx::SetTaskbarTabProperties  
 Establece las propiedades de una pestaña de la barra de tareas de Windows 7.  
  
```  
void SetTaskbarTabProperties(DWORD dwFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwFlags`  
 Combinación de valores STPFLAG. Para obtener más información, consulte [itaskbarlist4:: Settabproperties](http://msdn.microsoft.com/library/dd562049\(vs.85\).aspx).  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="settaskbartaborder"></a>CMDIChildWndEx::SetTaskbarTabOrder  
 Inserta al elemento secundario MDI antes de la ventana especificada en las fichas de la barra de tareas de Windows 7.  
  
```  
void SetTaskbarTabOrder(CMDIChildWndEx* pWndBefore = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWndBefore`  
 Puntero a la ventana secundaria MDI cuya vista en miniatura se inserta a la izquierda. Esta ventana ya debe registrarse mediante `RegisterTaskbarTab`. Si este valor es `NULL`, la miniatura nueva se agrega al final de la lista.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="settaskbartabactive"></a>CMDIChildWndEx::SetTaskbarTabActive  
 Activa la pestaña correspondiente de barra de tareas de Windows 7.  
  
```  
void SetTaskbarTabActive();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="registertaskbartab"></a>CMDIChildWndEx::RegisterTaskbarTab  
 Registra al formulario secundario MDI con fichas de la barra de tareas de Windows 7.  
  
```  
virtual void RegisterTaskbarTab(CMDIChildWndEx* pWndBefore = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWndBefore`  
 Puntero a la ventana secundaria MDI cuya vista en miniatura se inserta a la izquierda. Esta ventana ya debe registrarse mediante `RegisterTaskbarTab`. Si este valor es `NULL`, la miniatura nueva se agrega al final de la lista.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ontaskbartabthumbnailstretch"></a>CMDIChildWndEx::OnTaskbarTabThumbnailStretch  
 Llamado por el marco cuando sea necesario ajustar un mapa de bits para una Windows 7 barra de tareas ficha Vista previa en miniatura de la ventana secundaria MDI.  
  
```  
virtual BOOL OnTaskbarTabThumbnailStretch(
    HBITMAP hBmpDst,  
    const CRect& rectDst,  
    HBITMAP hBmpSrc,  
    const CRect& rectSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `hBmpDst`  
 Identificador de un mapa de bits de destino.  
  
 `rectDst`  
 Especifica el rectángulo de destino.  
  
 `hBmpSrc`  
 Identificador de un mapa de bits de origen.  
  
 `rectSrc`  
 Especifica el rectángulo de origen.  
  
### <a name="remarks"></a>Comentarios  
 Requirementher o él le él le él le le **:** afxmdichildwndex.h  
  
##  <a name="ontaskbartabthumbnailmouseactivate"></a>CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate  
 Llamado por el marco de trabajo cuando la miniatura de la ficha barra de tareas debe procesar el mensaje WM_MOUSEACTIVATE.  
  
```  
virtual int OnTaskbarTabThumbnailMouseActivate(
    CWnd* pDesktopWnd,  
    UINT nHitTest,  
    UINT message);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDesktopWnd`  
 Especifica un puntero a la ventana principal de nivel superior de la ventana activa. El puntero puede ser temporal y no debe almacenarse.  
  
 `nHitTest`  
 Especifica el código de área de prueba de posicionamiento. Una prueba de posicionamiento es una prueba que determina la ubicación del cursor.  
  
 `message`  
 Especifica el número de mensajes del mouse.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada activa del marco MDI secundario relacionado.  
  
##  <a name="ontaskbartabthumbnailactivate"></a>CMDIChildWndEx::OnTaskbarTabThumbnailActivate  
 Llamado por el marco de trabajo cuando la miniatura de la ficha barra de tareas debe procesar el mensaje WM_ACTIVATE.  
  
```  
virtual void OnTaskbarTabThumbnailActivate(
    UINT nState,  
    CWnd* pWndOther,  
    BOOL bMinimized);
```  
  
### <a name="parameters"></a>Parámetros  
 `nState`  
 Especifica si la `CWnd` es está activado o desactivado.  
  
 `pWndOther`  
 Puntero a la `CWnd` está activado o desactivado. El puntero puede ser `NULL`, y puede ser temporal.  
  
 `bMinimized`  
 Especifica el estado minimizado de la `CWnd` está activado o desactivado. Un valor de `TRUE` indica que la ventana está minimizada.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada activa del marco MDI secundario relacionado.  
  
##  <a name="onpresstaskbarthmbnailclosebutton"></a>CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton  
 Lo llama el marco de trabajo cuando el usuario presiona el botón de cierre en la miniatura de la ficha barra de tareas.  
  
```  
virtual void OnPressTaskbarThmbnailCloseButton();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ongeticonicthumbnail"></a>CMDIChildWndEx::OnGetIconicThumbnail  
 Llamado por el marco cuando sea necesario obtener un mapa de bits para la miniatura de iconos de la ventana secundaria MDI.  
  
```  
virtual HBITMAP OnGetIconicThumbnail(
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 `nWidth`  
 Especifica el ancho del mapa de bits necesario.  
  
 `nHeight`  
 Especifica el alto del mapa de bits necesario.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ongeticoniclivepreviewbitmap"></a>CMDIChildWndEx::OnGetIconicLivePreviewBitmap  
 Llamado por el marco de trabajo cuando se necesita obtener un mapa de bits para la vista previa activa de la ventana secundaria MDI.  
  
```  
virtual HBITMAP OnGetIconicLivePreviewBitmap(
    BOOL bIsMDIChildActive,  
    CPoint& ptLocation);
```  
  
### <a name="parameters"></a>Parámetros  
 `bIsMDIChildActive`  
 Este parámetro es `TRUE` si se solicita el mapa de bits para el formulario secundario MDI, que está actualmente activo y la ventana principal no se minimiza. El procesamiento en este caso predeterminado toma una instantánea de la ventana principal.  
  
 `ptLocation`  
 Especifica la ubicación del mapa de bits en los principales (nivel superior) coordenadas de cliente de la ventana. El destinatario debe proporcionar este punto.  
  
### <a name="return-value"></a>Valor devuelto  
 Si ha procesado, devuelve un identificador para un mapa de bits de 32 bpp válida, en caso contrario `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada y devolver un mapa de bits de 32 bpp válido para la vista previa activa de formulario secundario MDI. Este método se llama sólo cuando se muestra el formulario secundario MDI en fichas de la barra de tareas de Windows 7. Si devuelve `NULL`, MFC llama a los controladores predeterminados y obtenga con mapas de bits `PrintClient` o `PrintWindow`.  
  
##  <a name="m_dwdefaulttaskbartabpropertyflags"></a>CMDIChildWndEx::m_dwDefaultTaskbarTabPropertyFlags  
 Una combinación de indicadores, que se pasa por el marco de trabajo para el `SetTaskbarTabProperties` método, cuando se está registrando una pestaña (elemento secundario MDI) con fichas de la barra de tareas de Windows 7.  
  
```  
AFX_IMPORT_DATA static DWORD m_dwDefaultTaskbarTabPropertyFlags;  
```  
  
### <a name="remarks"></a>Comentarios  
 La combinación predeterminada es STPF_USEAPPTHUMBNAILWHENACTIVE | STPF_USEAPPPEEKWHENACTIVE.  
  
##  <a name="istaskbarthumbnailcliprectenabled"></a>CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled  
 Indica si la selección automática de una parte del área de cliente de una ventana para mostrar como miniatura de la ventana en la barra de tareas está habilitada o deshabilitada.  
  
```  
BOOL IsTaskbarThumbnailClipRectEnabled() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si la selección automática de una parte del área de cliente de una ventana para mostrar está habilitado; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="istaskbartabssupportenabled"></a>CMDIChildWndEx::IsTaskbarTabsSupportEnabled  
 Indica si el formulario MDI secundario puede aparecer en las fichas de la barra de tareas de Windows 7.  
  
```  
BOOL IsTaskbarTabsSupportEnabled();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el formulario MDI secundario puede aparecer en las fichas de la barra de tareas de Windows 7; `FALSE` si el formulario MDI secundario no puede aparecer en las fichas de la barra de tareas de Windows 7.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isregisteredwithtaskbartabs"></a>CMDIChildWndEx::IsRegisteredWithTaskbarTabs  
 Devuelve `TRUE` si se ha registrado correctamente el formulario secundario MDI con fichas de la barra de tareas de Windows 7.  
  
```  
BOOL IsRegisteredWithTaskbarTabs();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si está registrado el formulario secundario MDI con fichas de la barra de tareas de Windows 7; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="invalidateiconicbitmaps"></a>CMDIChildWndEx::InvalidateIconicBitmaps  
 Invalida una representación de mapa de bits icónica de un elemento secundario MDI.  
  
```  
BOOL InvalidateIconicBitmaps();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `FALSE` si se deshabilita la compatibilidad de la barra de tareas de Windows 7 o el formulario MDI secundario no está registrado con fichas de la barra de tareas de Windows 7; de lo contrario devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Debe llamarse cuando ha cambiado el contenido en directo o el tamaño de un elemento secundario MDI.  
  
##  <a name="gettaskbarthumbnailcliprect"></a>CMDIChildWndEx::GetTaskbarThumbnailClipRect  
 Llamado por el marco cuando sea necesario seleccionar una parte del área de cliente de una ventana para mostrar como miniatura de la ventana en la barra de tareas.  
  
```  
virtual CRect GetTaskbarThumbnailClipRect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un rectángulo en las coordenadas de windows. Este rectángulo se asigna al área de cliente del marco de nivel superior. El rectángulo debe estar vacío para borrar el rectángulo de recorte.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gettaskbarpreviewwnd"></a>CMDIChildWndEx::GetTaskbarPreviewWnd  
 Llamado por el marco de trabajo cuando se necesita obtener una ventana secundaria (normalmente una ventana de vista o divisor) que se mostrará en la miniatura de ficha de la barra de tareas de Windows 7.  
  
```  
virtual CWnd* GetTaskbarPreviewWnd();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Debe devolver un puntero válido a una `CWnd` relacionados con el objeto cuya vista previa debe mostrarse en una ficha de la barra de tareas de Windows 7 este formulario secundario MDI. La implementación predeterminada devuelve una ventana secundaria de este elemento secundario MDI con el Id. de control AFX_IDW_PANE_FIRST (que suele ser un `CView`-clase derivada).  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gettabproxywnd"></a>CMDIChildWndEx::GetTabProxyWnd  
 Devuelve la ventana de proxy de la ficha registrada con fichas de la barra de tareas de Windows 7.  
  
```  
CMDITabProxyWnd* GetTabProxyWnd();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CMDITabProxyWnd` objeto, que se registra con fichas de la barra de tareas de Windows 7.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="enabletaskbarthumbnailcliprect"></a>CMDIChildWndEx::EnableTaskbarThumbnailClipRect  
 Habilita o deshabilita la selección automática de una parte del área de cliente de una ventana para mostrar como miniatura de la ventana en la barra de tareas.  
  
```  
void EnableTaskbarThumbnailClipRect(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bEnable`  
 Especifica si se habilita ( `TRUE`), o deshabilitar ( `FALSE`) la selección automática de una parte del área de cliente de una ventana para mostrar.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="canshowontaskbartabs"></a>CMDIChildWndEx::CanShowOnTaskBarTabs  
 Indica que el marco de trabajo si se puede mostrar este elemento secundario MDI en fichas de la barra de tareas de Windows 7.  
  
```  
virtual BOOL CanShowOnTaskBarTabs();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el contenido de la ventana secundaria MDI se puede mostrar en vistas en miniatura de la barra de tareas de Windows 7.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada y devolver `FALSE` para deshabilitar el aspecto de este elemento secundario MDI en fichas de la barra de tareas de Windows 7.  
  
##  <a name="activatetoplevelframe"></a>CMDIChildWndEx::ActivateTopLevelFrame  
 Llamado por el marco de trabajo para activar el marco de nivel superior cuando se activa la aplicación desde una ficha de la barra de tareas.  
  
```  
virtual void ActivateTopLevelFrame();
```  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMDIChildWnd (clase)](../../mfc/reference/cmdichildwnd-class.md)   
 [Clase CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)   
 [CMDIFrameWndEx Class](../../mfc/reference/cmdiframewndex-class.md)

