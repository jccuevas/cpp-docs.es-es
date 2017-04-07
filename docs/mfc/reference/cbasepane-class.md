---
title: Clase CBasePane | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBasePane
- AFXBASEPANE/CBasePane
- AFXBASEPANE/CBasePane::AccNotifyObjectFocusEvent
- AFXBASEPANE/CBasePane::AddPane
- AFXBASEPANE/CBasePane::AdjustDockingLayout
- AFXBASEPANE/CBasePane::AdjustLayout
- AFXBASEPANE/CBasePane::CalcFixedLayout
- AFXBASEPANE/CBasePane::CanAcceptPane
- AFXBASEPANE/CBasePane::CanAutoHide
- AFXBASEPANE/CBasePane::CanBeAttached
- AFXBASEPANE/CBasePane::CanBeClosed
- AFXBASEPANE/CBasePane::CanBeDocked
- AFXBASEPANE/CBasePane::CanBeResized
- AFXBASEPANE/CBasePane::CanBeTabbedDocument
- AFXBASEPANE/CBasePane::CanFloat
- AFXBASEPANE/CBasePane::CanFocus
- AFXBASEPANE/CBasePane::CopyState
- AFXBASEPANE/CBasePane::CreateDefaultMiniframe
- AFXBASEPANE/CBasePane::CreateEx
- AFXBASEPANE/CBasePane::DockPane
- AFXBASEPANE/CBasePane::DockPaneUsingRTTI
- AFXBASEPANE/CBasePane::DockToFrameWindow
- AFXBASEPANE/CBasePane::DoesAllowDynInsertBefore
- AFXBASEPANE/CBasePane::EnableDocking
- AFXBASEPANE/CBasePane::EnableGripper
- AFXBASEPANE/CBasePane::FloatPane
- AFXBASEPANE/CBasePane::get_accHelpTopic
- AFXBASEPANE/CBasePane::get_accSelection
- AFXBASEPANE/CBasePane::GetCaptionHeight
- AFXBASEPANE/CBasePane::GetControlBarStyle
- AFXBASEPANE/CBasePane::GetCurrentAlignment
- AFXBASEPANE/CBasePane::GetDockingMode
- AFXBASEPANE/CBasePane::GetDockSiteFrameWnd
- AFXBASEPANE/CBasePane::GetEnabledAlignment
- AFXBASEPANE/CBasePane::GetMFCStyle
- AFXBASEPANE/CBasePane::GetPaneIcon
- AFXBASEPANE/CBasePane::GetPaneRow
- AFXBASEPANE/CBasePane::GetPaneStyle
- AFXBASEPANE/CBasePane::GetParentDockSite
- AFXBASEPANE/CBasePane::GetParentMiniFrame
- AFXBASEPANE/CBasePane::GetParentTabbedPane
- AFXBASEPANE/CBasePane::GetParentTabWnd
- AFXBASEPANE/CBasePane::GetRecentVisibleState
- AFXBASEPANE/CBasePane::HideInPrintPreviewMode
- AFXBASEPANE/CBasePane::InsertPane
- AFXBASEPANE/CBasePane::IsAccessibilityCompatible
- AFXBASEPANE/CBasePane::IsAutoHideMode
- AFXBASEPANE/CBasePane::IsDialogControl
- AFXBASEPANE/CBasePane::IsDocked
- AFXBASEPANE/CBasePane::IsFloating
- AFXBASEPANE/CBasePane::IsHorizontal
- AFXBASEPANE/CBasePane::IsInFloatingMultiPaneFrameWnd
- AFXBASEPANE/CBasePane::IsMDITabbed
- AFXBASEPANE/CBasePane::IsPaneVisible
- AFXBASEPANE/CBasePane::IsPointNearDockSite
- AFXBASEPANE/CBasePane::IsResizable
- AFXBASEPANE/CBasePane::IsRestoredFromRegistry
- AFXBASEPANE/CBasePane::IsTabbed
- AFXBASEPANE/CBasePane::IsVisible
- AFXBASEPANE/CBasePane::LoadState
- AFXBASEPANE/CBasePane::MoveWindow
- AFXBASEPANE/CBasePane::OnAfterChangeParent
- AFXBASEPANE/CBasePane::OnBeforeChangeParent
- AFXBASEPANE/CBasePane::OnDrawCaption
- AFXBASEPANE/CBasePane::OnMovePaneDivider
- AFXBASEPANE/CBasePane::OnPaneContextMenu
- AFXBASEPANE/CBasePane::OnRemoveFromMiniFrame
- AFXBASEPANE/CBasePane::OnSetAccData
- AFXBASEPANE/CBasePane::PaneFromPoint
- AFXBASEPANE/CBasePane::RecalcLayout
- AFXBASEPANE/CBasePane::RemovePaneFromDockManager
- AFXBASEPANE/CBasePane::SaveState
- AFXBASEPANE/CBasePane::SelectDefaultFont
- AFXBASEPANE/CBasePane::SetControlBarStyle
- AFXBASEPANE/CBasePane::SetDockingMode
- AFXBASEPANE/CBasePane::SetPaneAlignment
- AFXBASEPANE/CBasePane::SetPaneStyle
- AFXBASEPANE/CBasePane::SetWindowPos
- AFXBASEPANE/CBasePane::ShowPane
- AFXBASEPANE/CBasePane::StretchPane
- AFXBASEPANE/CBasePane::UndockPane
- AFXBASEPANE/CBasePane::DoPaint
dev_langs:
- C++
helpviewer_keywords:
- get_accState method
- get_accHelp method
- CBasePane class
- accLocation method
- accHitTest method
- get_accDescription method
- get_accDefaultAction method
- get_accName method
- get_accFocus method
- get_accRole method
- get_accValue method
- get_accChild method
- accSelect method
- get_accKeyboardShortcut method
- get_accChildCount method
- Serialize method
- PreTranslateMessage method
- get_accParent method
ms.assetid: 8163dd51-d7c7-4def-9c74-61f8ecdfad82
caps.latest.revision: 43
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
ms.openlocfilehash: 0444c0647d83a1e9b431dd0c5bdb369da213b91b
ms.lasthandoff: 02/24/2017

---
# <a name="cbasepane-class"></a>Clase CBasePane
Clase base para todos los paneles de MFC.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CBasePane : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CBasePane::CBasePane`|Constructor predeterminado.|  
|`CBasePane::~CBasePane`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CBasePane::accHitTest`|El marco llama a este método para recuperar el elemento u objeto secundario situado en un punto dado de la pantalla. (Invalida [CWnd::accHitTest](../../mfc/reference/cwnd-class.md#acchittest).)|  
|`CBasePane::accLocation`|Llamado por el marco de trabajo para recuperar la ubicación de pantalla actual para el objeto especificado. (Invalida [CWnd::accLocation](../../mfc/reference/cwnd-class.md#acclocation).)|  
|[CBasePane::AccNotifyObjectFocusEvent](#accnotifyobjectfocusevent)|`CBasePane`no se utiliza este método.|  
|`CBasePane::accSelect`|El marco llama a este método para modificar la selección o desplazar el foco de teclado del objeto especificado. (Invalida [CWnd::accSelect](../../mfc/reference/cwnd-class.md#accselect).)|  
|[CBasePane::AddPane](#addpane)|Agrega un panel al administrador de acoplamiento.|  
|[CBasePane::AdjustDockingLayout](#adjustdockinglayout)|Redirige una llamada al administrador de acoplamiento para ajustar el diseño de acoplamiento.|  
|[CBasePane::AdjustLayout](#adjustlayout)|Llamado por el marco de trabajo cuando el panel debe ajustar su diseño interno.|  
|[CBasePane::CalcFixedLayout](#calcfixedlayout)|Calcula el tamaño horizontal de una barra de controles.|  
|[CBasePane::CanAcceptPane](#canacceptpane)|Determina si el otro panel se puede acoplar el panel.|  
|[CBasePane::CanAutoHide](#canautohide)|Determina si el panel admite el modo de ocultación automática.|  
|[CBasePane::CanBeAttached](#canbeattached)|Determina si el panel se puede acoplar a otro panel.|  
|[CBasePane::CanBeClosed](#canbeclosed)|Determina si se puede cerrar el panel.|  
|[CBasePane::CanBeDocked](#canbedocked)|Determina si el panel se puede acoplar a otro panel.|  
|[CBasePane::CanBeResized](#canberesized)|Determina si el panel puede cambiarse.|  
|[CBasePane::CanBeTabbedDocument](#canbetabbeddocument)|Especifica si el panel se puede convertir en un documento con fichas de MDI.|  
|[CBasePane::CanFloat](#canfloat)|Determina si el panel puede flotar.|  
|[CBasePane::CanFocus](#canfocus)|Especifica si el panel puede recibir el foco.|  
|[CBasePane::CopyState](#copystate)|Copia el estado de un determinado panel.|  
|[CBasePane::CreateDefaultMiniframe](#createdefaultminiframe)|Si el panel puede flotar, crea una ventana de marco reducido.|  
|[CBasePane::CreateEx](#createex)|Crea el control de panel.|  
|[CBasePane::DockPane](#dockpane)|Un panel se acopla a otro panel, o a una ventana de marco.|  
|[CBasePane::DockPaneUsingRTTI](#dockpaneusingrtti)|El panel se acopla con información de tipo en tiempo de ejecución.|  
|[CBasePane::DockToFrameWindow](#docktoframewindow)|Un panel acoplable se acopla a un marco.|  
|[CBasePane::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Determina si se puede insertar otro panel dinámicamente entre este panel y el marco primario.|  
|[CBasePane::EnableDocking](#enabledocking)|Habilita el acoplamiento del panel al marco principal.|  
|[CBasePane::EnableGripper](#enablegripper)|Habilita o deshabilita el punto de sujeción. Si está habilitado el redimensionamiento, el usuario puede arrastrar para ajustar la posición del panel.|  
|`CBasePane::FillWindowRect`|Se utiliza internamente.|  
|[CBasePane::FloatPane](#floatpane)|Desplaza el panel.|  
|`CBasePane::get_accChild`|El marco llama a este método para recuperar la dirección de una interfaz `IDispatch` del elemento secundario especificado. (Invalida [CWnd::get_accChild](../../mfc/reference/cwnd-class.md#get_accchild).)|  
|`CBasePane::get_accChildCount`|Llamado por el marco de trabajo para recuperar el número de elementos secundarios que pertenecen a este objeto. (Invalida [CWnd::get_accChildCount](../../mfc/reference/cwnd-class.md#get_accchildcount).)|  
|`CBasePane::get_accDefaultAction`|Llamado por el marco de trabajo para recuperar una cadena que describe la acción predeterminada para el objeto. (Invalida [CWnd::get_accDefaultAction](../../mfc/reference/cwnd-class.md#get_accdefaultaction).)|  
|`CBasePane::get_accDescription`|El marco llama a este método para recuperar una cadena que describe la apariencia visual del objeto especificado. (Invalida [CWnd::get_accDescription](../../mfc/reference/cwnd-class.md#get_accdescription).)|  
|`CBasePane::get_accFocus`|El marco llama a este método para recuperar el objeto que tiene el foco de teclado. (Invalida [CWnd::get_accFocus](../../mfc/reference/cwnd-class.md#get_accfocus).)|  
|`CBasePane::get_accHelp`|Llamado por el marco de trabajo para recuperar una cadena de propiedad de ayuda para el objeto. (Invalida [CWnd::get_accHelp](../../mfc/reference/cwnd-class.md#get_acchelp).)|  
|[CBasePane::get_accHelpTopic](#get_acchelptopic)|Llamado por el marco de trabajo para recuperar la ruta de acceso completa del archivo WinHelp asociado con el objeto especificado y el identificador del tema correspondiente en el archivo. (Invalida [CWnd::get_accHelpTopic](../../mfc/reference/cwnd-class.md#get_acchelptopic).)|  
|`CBasePane::get_accKeyboardShortcut`|Llamado por el marco de trabajo para recuperar la clave de acceso directo especificado para el objeto. (Invalida [CWnd::get_accKeyboardShortcut](../../mfc/reference/cwnd-class.md#get_acckeyboardshortcut).)|  
|`CBasePane::get_accName`|El marco llama a este método para recuperar el nombre del objeto especificado. (Invalida [CWnd::get_accName](../../mfc/reference/cwnd-class.md#get_accname).)|  
|`CBasePane::get_accParent`|Llamado por el marco para recuperar la `IDispatch` interfaz para el elemento primario del objeto. (Invalida [CWnd::get_accParent](../../mfc/reference/cwnd-class.md#get_accparent).)|  
|`CBasePane::get_accRole`|El marco llama a este método para recuperar información que describe el rol del objeto especificado. (Invalida [CWnd::get_accRole](../../mfc/reference/cwnd-class.md#get_accrole).)|  
|[CBasePane::get_accSelection](#get_accselection)|El marco llama a este método para recuperar el elemento secundario seleccionado de este objeto. (Invalida [CWnd::get_accSelection](../../mfc/reference/cwnd-class.md#get_accselection).)|  
|`CBasePane::get_accState`|El marco llama a este método para recuperar el estado actual del objeto especificado. (Invalida [CWnd::get_accState](../../mfc/reference/cwnd-class.md#get_accstate).)|  
|`CBasePane::get_accValue`|El marco llama a este método para recuperar el valor del objeto especificado. (Invalida [CWnd::get_accValue](../../mfc/reference/cwnd-class.md#get_accvalue).)|  
|[CBasePane::GetCaptionHeight](#getcaptionheight)|Devuelve la altura del título.|  
|[CBasePane::GetControlBarStyle](#getcontrolbarstyle)|Devuelve el estilo de barra de control.|  
|[CBasePane::GetCurrentAlignment](#getcurrentalignment)|Devuelve la alineación actual del panel.|  
|[CBasePane::GetDockingMode](#getdockingmode)|Devuelve el modo de acoplamiento actual para el panel.|  
|[CBasePane::GetDockSiteFrameWnd](#getdocksiteframewnd)|Devuelve un puntero a la ventana que es el sitio de vinculación para el panel.|  
|[CBasePane::GetEnabledAlignment](#getenabledalignment)|Devuelve los estilos CBRS_ALIGN_ que se aplican al panel.|  
|[CBasePane::GetMFCStyle](#getmfcstyle)|Devuelve los estilos del panel específico a MFC.|  
|[CBasePane::GetPaneIcon](#getpaneicon)|Devuelve un identificador para el icono del panel.|  
|`CBasePane::GetPaneRect`|Se utiliza internamente.|  
|[CBasePane::GetPaneRow](#getpanerow)|Devuelve un puntero a la [CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)objeto en el panel está acoplado.|  
|[CBasePane::GetPaneStyle](#getpanestyle)|Devuelve el estilo del panel.|  
|[CBasePane::GetParentDockSite](#getparentdocksite)|Devuelve un puntero al sitio de acoplamiento principal.|  
|[CBasePane::GetParentMiniFrame](#getparentminiframe)|Devuelve un puntero a la ventana de marco reducido primaria.|  
|[CBasePane::GetParentTabbedPane](#getparenttabbedpane)|Devuelve un puntero al panel con fichas primario.|  
|[CBasePane::GetParentTabWnd](#getparenttabwnd)|Devuelve un puntero a la ventana primaria que está dentro de una pestaña.|  
|[CBasePane::GetRecentVisibleState](#getrecentvisiblestate)|El marco de trabajo llama a este método cuando se restaura un panel desde un archivo.|  
|[CBasePane::HideInPrintPreviewMode](#hideinprintpreviewmode)|Especifica si el panel está oculto en la vista preliminar.|  
|[CBasePane::InsertPane](#insertpane)|El panel especificado se registra con el Administrador de acoplamiento.|  
|[CBasePane::IsAccessibilityCompatible](#isaccessibilitycompatible)|Especifica si el panel admite Active Accessibility.|  
|[CBasePane::IsAutoHideMode](#isautohidemode)|Determina si un panel está en modo de ocultación automática.|  
|[CBasePane::IsDialogControl](#isdialogcontrol)|Especifica si el panel es un control de cuadro de diálogo.|  
|[CBasePane::IsDocked](#isdocked)|Determina si el panel está acoplado.|  
|[CBasePane::IsFloating](#isfloating)|Determina si el panel está flotando.|  
|[CBasePane::IsHorizontal](#ishorizontal)|Determina si el panel se acopla horizontalmente.|  
|[CBasePane::IsInFloatingMultiPaneFrameWnd](#isinfloatingmultipaneframewnd)|Especifica si el panel está en una ventana de marco de varios paneles.|  
|[CBasePane::IsMDITabbed](#ismditabbed)|Determina si el panel se ha agregado a una ventana secundaria MDI como un documento con fichas.|  
|[CBasePane::IsPaneVisible](#ispanevisible)|Especifica si el `WS_VISIBLE` marca está establecida para el panel.|  
|[CBasePane::IsPointNearDockSite](#ispointneardocksite)|Determina si un punto especificado está cerca del sitio de vinculación.|  
|[CBasePane::IsResizable](#isresizable)|Determina si el panel puede cambiarse.|  
|[CBasePane::IsRestoredFromRegistry](#isrestoredfromregistry)|Determina si el panel está restaurado desde el registro.|  
|[CBasePane::IsTabbed](#istabbed)|Determina si el panel se ha insertado en el control de ficha de una ventana con fichas.|  
|`CBasePane::IsTooltipTopmost`|Se utiliza internamente.|  
|[CBasePane::IsVisible](#isvisible)|Determina si el panel está visible.|  
|[CBasePane::LoadState](#loadstate)|Carga el estado del panel desde el registro.|  
|[CBasePane::MoveWindow](#movewindow)|Mueve el panel.|  
|[CBasePane::OnAfterChangeParent](#onafterchangeparent)|Lo llama el marco de trabajo cuando se ha cambiado el elemento primario del panel.|  
|[CBasePane::OnBeforeChangeParent](#onbeforechangeparent)|Llamado por el marco justo antes de que el panel cambia su ventana primaria.|  
|[CBasePane::OnDrawCaption](#ondrawcaption)|El marco de trabajo llama a este método cuando se dibuja la leyenda.|  
|[CBasePane::OnMovePaneDivider](#onmovepanedivider)|Este método no se utiliza actualmente.|  
|[CBasePane::OnPaneContextMenu](#onpanecontextmenu)|Llamado por el marco cuando compila un menú con una lista de paneles.|  
|[CBasePane::OnRemoveFromMiniFrame](#onremovefromminiframe)|Lo llama el marco de trabajo cuando se quita un panel de la ventana de marco flotante primaria.|  
|[CBasePane::OnSetAccData](#onsetaccdata)|`CBasePane`no se utiliza este método.|  
|`CBasePane::OnUpdateCmdUI`|Se utiliza internamente.|  
|[CBasePane::PaneFromPoint](#panefrompoint)|Devuelve el panel que contiene el punto especificado.|  
|`CBasePane::PreTranslateMessage`|Utilizado por la clase [CWinApp](../../mfc/reference/cwinapp-class.md) para traducir los mensajes de ventana antes de que se envíen a la [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funciones de Windows. (Invalida [CWnd:: PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CBasePane::RecalcLayout](#recalclayout)|`CBasePane`no se utiliza este método.|  
|[CBasePane::RemovePaneFromDockManager](#removepanefromdockmanager)|Anula el registro de un panel y lo quita de la lista en el Administrador de acoplamiento.|  
|[CBasePane::SaveState](#savestate)|Guarda el estado del panel en el registro.|  
|[CBasePane::SelectDefaultFont](#selectdefaultfont)|Selecciona la fuente predeterminada para un contexto de dispositivo especificado.|  
|`CBasePane::Serialize`|Lee o escribe este objeto de o en un archivo. (Invalida [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize).)|  
|[CBasePane::SetControlBarStyle](#setcontrolbarstyle)|Establece el estilo de barra de control.|  
|[CBasePane::SetDockingMode](#setdockingmode)|Establece el modo de acoplamiento del panel.|  
|`CBasePane::SetMDITabbed`|Se utiliza internamente.|  
|[CBasePane::SetPaneAlignment](#setpanealignment)|Establece la alineación del panel.|  
|`CBasePane::SetPaneRect`|Se utiliza internamente.|  
|[CBasePane::SetPaneStyle](#setpanestyle)|Establece el estilo del panel.|  
|`CBasePane::SetRestoredFromRegistry`|Se utiliza internamente.|  
|[CBasePane::SetWindowPos](#setwindowpos)|Cambia el tamaño, la posición y el orden Z de un panel.|  
|[CBasePane::ShowPane](#showpane)|Muestra u oculta el panel.|  
|[CBasePane::StretchPane](#stretchpane)|Expande un panel vertical u horizontalmente.|  
|[CBasePane::UndockPane](#undockpane)|Quita el panel desde el sitio de vinculación, slider predeterminado o ventana de marco reducido que actualmente está acoplada.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CBasePane::DoPaint](#dopaint)|Rellena el fondo del panel.|  
  
## <a name="remarks"></a>Comentarios  
 Si desea crear una clase de panel que admite las características de acoplamiento extendidas disponibles en MFC, debe derivar de `CBasePane` o de [CPane clase](../../mfc/reference/cpane-class.md).  
  
## <a name="customization-tips"></a>Sugerencias de personalización  
 Las siguientes sugerencias de personalización que pertenecen a la `CBasePane Class` y todas las clases que heredan de él:  
  
-   Cuando se crea un panel, puede aplicar varios estilos de nuevo:  
  
    - `AFX_CBRS_FLOAT`hace que el tipo float de panel.  
  
    - `AFX_CBRS_AUTOHIDE`permite oculta automáticamente el modo.  
  
    - `AFX_CBRS_CLOSE`permite que el panel de cierre (oculto).  
  
     Estos son marcas que se pueden combinar con una operación OR bit a bit.  
  
 `CBasePane`implementa los siguientes métodos booleanos virtuales para reflejar estos indicadores: [CBasePane::CanBeClosed](#canbeclosed), [CBasePane::CanAutoHide](#canautohide), [CBasePane::CanFloat](#canfloat). Se puede reemplazar en clases derivadas para personalizar su comportamiento.  
  
-   Puede personalizar el comportamiento de acoplamiento invalidando [CBasePane::CanAcceptPane](#canacceptpane). Que su panel devuelva `FALSE` desde este método para evitar que otro panel de acoplamiento a él.  
  
-   Si desea crear un panel estático que no se puede desplazar y que evita que cualquier otro panel de acoplamiento antes (similar a la barra de Outlook en el ejemplo de OutlookDemo), créela como no flotante y reemplace [CBasePane::DoesAllowDynInsertBefore](#doesallowdyninsertbefore) para devolver `FALSE`. La implementación predeterminada devuelve `FALSE` si se crea el panel sin el `AFX_CBRS_FLOAT` estilo.  
  
-   Crear todos los paneles con identificadores que no sea -1.  
  
-   Para determinar la visibilidad del panel, utilice [CBasePane::IsVisible](#isvisible). Administra correctamente el estado de visibilidad en fichas y modos de ocultación automática.  
  
-   Si desea crear un panel de tamaño variable no flotante, sin crear el `AFX_CBRS_FLOAT` estilo y llame a [CFrameWnd:: DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).  
  
-   Para excluir un panel de diseño de acoplamiento o para quitar una barra de herramientas de la barra de acoplamiento, llame a [CBasePane::UndockPane](#undockpane). No llame a este método para los paneles en modo de ocultación automática o de los paneles que residen en las fichas de las ventanas con fichas.  
  
-   Si desea float o desacoplar un panel que se encuentra en modo de ocultación automática, se debe llamar a [CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode) con `FALSE` como el primer argumento antes de llamar a [CBasePane::FloatPane](#floatpane) o [CBasePane::UndockPane](#undockpane).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios métodos en la `CBasePane` clase. En el ejemplo se muestra cómo recuperar un panel desde el `CFrameWndEx` clase y cómo establecer el modo de acoplamiento, la alineación del panel y el estilo del panel. El código es de la [ejemplo de panel de palabras](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad&#2;](../../mfc/reference/codesnippet/cpp/cbasepane-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxbasepane.h  
  
##  <a name="accnotifyobjectfocusevent"></a>CBasePane::AccNotifyObjectFocusEvent  
 `CBasePane`no se utiliza este método.  
  
```  
virtual void AccNotifyObjectFocusEvent(int);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `int`  
 No usado.  
  
##  <a name="addpane"></a>CBasePane::AddPane  
 Agrega un panel al administrador de acoplamiento.  
  
```  
void AddPane(CBasePane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Puntero a un panel para agregar.  
  
### <a name="remarks"></a>Comentarios  
 Se trata de un método de conveniencia que agrega un panel a un administrador de acoplamiento. Mediante este método, no es necesario escribir código que analiza el tipo del marco primario.  
  
 Para obtener más información, consulte [CDockingManager clase](../../mfc/reference/cdockingmanager-class.md) y [CMDIFrameWndEx::AddPane](../../mfc/reference/cmdiframewndex-class.md#addpane).  
  
##  <a name="adjustdockinglayout"></a>CBasePane::AdjustDockingLayout  
 Redirige una llamada al administrador de acoplamiento para ajustar el diseño de acoplamiento.  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `hdwp`  
 Identificador de una estructura que contiene múltiples posiciones de ventana.  
  
### <a name="remarks"></a>Comentarios  
 Se trata de un método de conveniencia que ajusta el diseño de acoplamiento. Mediante este método, no es necesario escribir código que analiza el tipo del marco primario.  
  
 Para obtener más información, consulte [CDockingManager::AdjustDockingLayout](../../mfc/reference/cdockingmanager-class.md#adjustdockinglayout)  
  
##  <a name="adjustlayout"></a>CBasePane::AdjustLayout  
 Llamado por el marco para ajustar el diseño interno de un panel.  
  
```  
virtual void AdjustLayout();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando tiene un panel ajustar su diseño interno. La implementación base no hace nada.  
  
##  <a name="calcfixedlayout"></a>CBasePane::CalcFixedLayout  
 Calcula el tamaño horizontal de una barra de controles.  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bStretch`  
 Indica si la barra debe ajustarse al tamaño del marco. El `bStretch` parámetro es distinto de cero cuando la barra no es una barra de acoplamiento (no disponible para acoplar) y es 0 si es acoplada o flotante (disponible para acoplar).  
  
 [in] `bHorz`  
 Indica que la barra está orientada horizontal o verticalmente. El `bHorz` parámetro es distinto de cero si la barra se orienta horizontalmente y es 0 si es una orientación vertical.  
  
### <a name="return-value"></a>Valor devuelto  
 La barra de control de tamaño, en píxeles, de un `CSize` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Consulte la sección de la sección comentarios en [CControlBar::CalcFixedLayout](../../mfc/reference/ccontrolbar-class.md#calcfixedlayout)  
  
##  <a name="canacceptpane"></a>CBasePane::CanAcceptPane  
 Determina si el otro panel se puede acoplar el panel.  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Un puntero al panel para acoplar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se puede aceptar otro panel; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método antes de que acopla el panel especificado por `pBar` al panel actual.  
  
 Utilice este método y el [CBasePane::CanBeDocked](#canbedocked) método para controlar cómo acoplar paneles a otros paneles de la aplicación.  
  
 La implementación predeterminada devuelve `FALSE`.  
  
##  <a name="canautohide"></a>CBasePane::CanAutoHide  
 Determina si el panel admite el modo de ocultación automática.  
  
```  
virtual BOOL CanAutoHide() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este panel admite el modo de ocultación automática; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función para determinar si el panel admite el modo de ocultación automática.  
  
 Durante la construcción, puede establecer esta capacidad pasando el `AFX_CBRS_AUTOHIDE` marca [CBasePane::CreateEx](#createex).  
  
 La implementación predeterminada busca la `AFX_CBRS_AUTOHIDE` marca. Invalide este método en una clase derivada para personalizar este comportamiento.  
  
##  <a name="canbeattached"></a>CBasePane::CanBeAttached  
 Determina si el panel se puede acoplar a otra ventana de panel o marco.  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se puede acoplar a otro panel o ventana de marco; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada devuelve `FALSE`. Invalide este método en una clase derivada para habilitar o deshabilitar la capacidad de acoplar sin llamar a [CBasePane::EnableDocking](#enabledocking).  
  
##  <a name="canbeclosed"></a>CBasePane::CanBeClosed  
 Determina si se puede cerrar el panel.  
  
```  
virtual BOOL CanBeClosed() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se puede cerrar; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para determinar si se puede cerrar el panel. Si el método devuelve `TRUE`, **cerrar** botón se agrega a la barra de título del panel o, si el panel está flotando, en la barra de título de ventana de marco reducido del panel.  
  
 Durante la construcción, puede establecer esta capacidad pasando el `AFX_CBRS_CLOSE` marca [CBasePane::CreateEx](#createex).  
  
 La implementación predeterminada busca la `AFX_CBRS_CLOSE` marca.  
  
##  <a name="canbedocked"></a>CBasePane::CanBeDocked  
 Determina si el panel se puede acoplar a otro panel.  
  
```  
virtual BOOL CanBeDocked(CBasePane* pDockBar) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDockBar`  
 Un puntero a otro panel.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este panel se puede acoplar a otro panel; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método antes de que acopla el panel especificado por `pDockBar` al panel actual.  
  
 Utilice este método y el [CBasePane::CanAcceptPane](#canacceptpane) método para controlar cómo acoplar paneles a otros paneles de la aplicación.  
  
 La implementación predeterminada devuelve `FALSE`.  
  
##  <a name="canberesized"></a>CBasePane::CanBeResized  
 Determina si el panel puede cambiarse.  
  
```  
virtual BOOL CanBeResized() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel puede cambiarse de tamaño; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método comprueba el `AFX_CBRS_RESIZE` marca, que se especifica de forma predeterminada en `CBasePane::OnCreate`. Si no se especifica este marcador, el Administrador de acoplamiento indicadores del panel internamente como inamovible en lugar de acoplarla.  
  
##  <a name="canbetabbeddocument"></a>CBasePane::CanBeTabbedDocument  
 Especifica si el panel se puede convertir en un documento con fichas de MDI.  
  
```  
virtual BOOL CanBeTabbedDocument() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se puede convertir en un documento con fichas; de lo contrario, `FALSE`. `CBasePane::CanBeTabbedDocument` siempre devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Sólo los objetos de determinados `CBasePane`-tipos derivados, como el [CDockablePane Class](../../mfc/reference/cdockablepane-class.md), se puede convertir en documentos con fichas.  
  
##  <a name="canfloat"></a>CBasePane::CanFloat  
 Determina si el panel puede flotar.  
  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel puede flotar; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para determinar si puede flotar el panel.  
  
 Durante la construcción, puede establecer esta capacidad pasando el `AFX_CBRS_FLOAT` marca [CBasePane::CreateEx](#createex).  
  
> [!NOTE]
>  El marco de trabajo supone que no flotante paneles son estáticas y que no se puede cambiar su estado de acoplamiento. Por lo tanto, el marco de trabajo no guarda el estado de acoplamiento de paneles no flotante.  
  
 La implementación predeterminada busca la `AFX_CBRS_FLOAT` estilo.  
  
##  <a name="canfocus"></a>CBasePane::CanFocus  
 Especifica si el panel puede recibir el foco.  
  
```  
virtual BOOL CanFocus() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel puede recibir el foco; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para controlar el foco. Por ejemplo, dado que las barras de herramientas no pueden recibir el foco, este método devuelve `FALSE` cuando se llama en los objetos de la barra de herramientas.  
  
 El marco de trabajo intenta establecer el foco de entrada cuando un panel está acoplado o flotante.  
  
##  <a name="copystate"></a>CBasePane::CopyState  
 Copia el estado de un determinado panel.  
  
```  
virtual void CopyState(CBasePane* pOrgBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pOrgBar`  
 Un puntero a otro panel.  
  
### <a name="remarks"></a>Comentarios  
 Este método copia el estado de `pOrgBar` a este panel.  
  
##  <a name="createdefaultminiframe"></a>CBasePane::CreateDefaultMiniframe  
 Si el panel puede flotar, este método crea una ventana de marco reducido para él.  
  
```  
virtual CPaneFrameWnd* CreateDefaultMiniframe(CRect rectInitial);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectInitial`  
 Especifica las coordenadas iniciales de la ventana de marco reducido.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la nueva ventana de marco reducido o `NULL` si falló la creación.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando cambia de un panel a un estado flotante. El método crea una ventana de marco reducido y adjunta el panel a esta ventana.  
  
 La implementación predeterminada devuelve `NULL`.  
  
##  <a name="createex"></a>CBasePane::CreateEx  
 Crea el control de panel.  
  
```  
virtual BOOL CreateEx(
    DWORD dwStyleEx,  
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    DWORD dwControlBarStyle=0,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwStyleEx`  
 Los estilos extendidos (consulte [CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex) para obtener más información).  
  
 [in] `lpszClassName`  
 El nombre de clase de ventana.  
  
 [in] `lpszWindowName`  
 Nombre de la ventana.  
  
 [in] `dwStyle`  
 El estilo de ventana (consulte [CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex)).  
  
 [in] `rect`  
 El rectángulo inicial.  
  
 [in] `pParentWnd`  
 Puntero a la ventana primaria.  
  
 [in] `nID`  
 Especifica el identificador del panel. Debe ser único.  
  
 [in] `dwControlBarStyle`  
 Indicadores de estilo para los paneles.  
  
 [in] `pContext`  
 Un puntero a`CcreateContext`  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se ha creado correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Crea una ventana de la clase `lpszClassName`. Si especifica `WS_CAPTION`, este método borra la `WS_CAPTION` bit de estilo y establece `CBasePane::m_bHasCaption` a `TRUE`, ya que la biblioteca no admite paneles con subtítulos.  
  
 Puede utilizar cualquier combinación de los estilos de ventana secundaria y control MFC barra estilos (CBRS_).  
  
 La biblioteca agrega varios nuevos estilos para los paneles. En la tabla siguiente se describe los nuevos estilos:  
  
|Estilo|Descripción|  
|-----------|-----------------|  
|`AFX_CBRS_FLOAT`|El panel flotante.|  
|`AFX_CBRS_AUTOHIDE`|El panel admite el modo de ocultación automática|  
|`AFX_CBRS_RESIZE`|El panel puede cambiarse. **Importante:** este estilo no está implementada.|  
|`AFX_CBRS_CLOSE`|Se puede cerrar el panel.|  
|`AFX_CBRS_AUTO_ROLLUP`|El panel se puede acumular cuando flota.|  
|`AFX_CBRS_REGULAR_TABS`|Cuando se acopla un panel a otro panel que tenga este estilo, se crea una ventana con fichas regular. (Para obtener más información, consulte [CTabbedPane clase](../../mfc/reference/ctabbedpane-class.md).)|  
|`AFX_CBRS_OUTLOOK_TABS`|Cuando se acopla un panel a otro panel que tenga este estilo, se crea una ventana con pestañas de estilo de Outlook. (Para obtener más información, consulte [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).)|  
  
 Para usar los nuevos estilos, especifíquelos en `dwControlBarStyle`.  
  
##  <a name="dockpane"></a>CBasePane::DockPane  
 Un panel se acopla a otro panel, o a una ventana de marco.  
  
```  
virtual BOOL DockPane(
    CBasePane* pDockBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDockBar`  
 Un puntero a otro panel.  
  
 [in] `lpRect`  
 Especifica el rectángulo de destino.  
  
 [in] `dockMethod`  
 Especifica el método de acoplamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la barra de control se acopla correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para acoplar un panel a otro panel o una barra de acoplamiento ( [CDockSite clase](../../mfc/reference/cdocksite-class.md)) especificado por `pDockBar`, o a un marco principal si `pDockBar` es `NULL`.  
  
 `dockMethod`Especifica cómo el panel está acoplado. Consulte [CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane) para obtener una lista de valores posibles.  
  
##  <a name="dockpaneusingrtti"></a>CBasePane::DockPaneUsingRTTI  
 El panel se acopla con información de tipo en tiempo de ejecución.  
  
```  
void DockPaneUsingRTTI(BOOL bUseDockSite);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bUseDockSite`  
 Si `TRUE`, acoplar al sitio de acoplamiento. Si `FALSE`, acoplar al marco primario.  
  
##  <a name="docktoframewindow"></a>CBasePane::DockToFrameWindow  
 Un panel acoplable se acopla a un marco.  
  
```  
virtual BOOL DockToFrameWindow(
    DWORD dwAlignment,  
    LPCRECT lpRect = NULL,  
    DWORD dwDockFlags = DT_DOCK_LAST,  
    CBasePane* pRelativeBar = NULL,  
    int nRelativeIndex = -1,  
    BOOL bOuterEdge = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwAlignment`  
 El lado del marco primario que desea acoplar el panel.  
  
 [in] `lpRect`  
 El tamaño deseado.  
  
 [in] `dwDockFlags`  
 ignorado.  
  
 [in] `pRelativeBar`  
 ignorado.  
  
 [in] `nRelativeIndex`  
 ignorado.  
  
 [in] `bOuterEdge`  
 Si `TRUE` y hay otros paneles acoplables en el lado especificado por `dwAlignment`, el panel se acopla fuera de los otros paneles, más cerca del borde del marco primario. Si `FALSE`, el panel se acopla más cercano al centro del área de cliente.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método se realizó correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método produce un error si un divisor ( [CPaneDivider clase](../../mfc/reference/cpanedivider-class.md)) no se puede crear. De lo contrario, siempre devuelve `TRUE`.  
  
##  <a name="doesallowdyninsertbefore"></a>CBasePane::DoesAllowDynInsertBefore  
 Determina si se puede insertar otro panel dinámicamente entre este panel y el marco primario.  
  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si un usuario puede insertar otro panel; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para determinar si un usuario puede insertar dinámicamente un panel antes de este panel.  
  
 Por ejemplo, suponga que la aplicación crea un panel acoplado en el lado izquierdo del marco (por ejemplo, la barra de Outlook). Para evitar que el usuario otro panel de acoplamiento a la izquierda de la primera sección, invalide este método y devolver `FALSE`.  
  
 Se recomienda reemplazar este método y devolver `FALSE` de paneles flotante no derivan de [CDockablePane Class](../../mfc/reference/cdockablepane-class.md).  
  
 La implementación predeterminada devuelve `TRUE`.  
  
##  <a name="dopaint"></a>CBasePane::DoPaint  
 Rellena el fondo del panel.  
  
```  
virtual void DoPaint(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada llama el administrador visual actual para rellenar el fondo ( [CMFCVisualManager::OnFillBarBackground](../../mfc/reference/cmfcvisualmanager-class.md#onfillbarbackground)).  
  
##  <a name="enabledocking"></a>CBasePane::EnableDocking  
 Habilita el acoplamiento del panel al marco principal.  
  
```  
virtual void EnableDocking(DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwAlignment`  
 Especifica la alineación de acoplamiento para habilitar.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para activar la alineación de acoplamiento en el marco principal. Puede pasar una combinación de `CBRS_ALIGN_` marcas (para obtener más información, consulte [CControlBar:: EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking)).  
  
 `EnableDocking`Establezca el indicador interno `CBasePane::m_dwEnabledAlignment` y el marco de trabajo comprueba este indicador cuando se acopla a un panel.  
  
 Llame a [CBasePane::GetEnabledAlignment](#getenabledalignment) para determinar la alineación de un panel de acoplamiento.  
  
##  <a name="enablegripper"></a>CBasePane::EnableGripper  
 Habilita o deshabilita el punto de sujeción. Si está habilitado el redimensionamiento, el usuario puede arrastrar para ajustar la posición del panel.  
  
```  
virtual void EnableGripper(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para habilitar al redimensionamiento; `FALSE` para deshabilitarlo.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo usa este método para habilitar un agarrador en lugar de utilizar el `WS_CAPTION` estilo.  
  
##  <a name="floatpane"></a>CBasePane::FloatPane  
 Desplaza el panel.  
  
```  
virtual BOOL FloatPane(
    CRect rectFloat,  
    AFX_DOCK_METHOD dockMethod=DM_UNKNOWN,  
    bool bShow=true);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectFloat`  
 Especifica las coordenadas de la pantalla donde aparece el panel flotante.  
  
 [in] `dockMethod`  
 Especifica el método acoplar a usar para el panel flotante.  
  
 [in] `bShow`  
 Especifica si está visible el panel flotante ( `TRUE`) u oculto ( `FALSE`).  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se flota correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para convertir en flotante un panel situado en la posición de pantalla especificada por `rectFloat`.  
  
##  <a name="get_acchelptopic"></a>CBasePane::get_accHelpTopic  
 El marco de trabajo llama a este método para recuperar la ruta de acceso completa de la `WinHelp` archivo que está asociado con el objeto especificado y el identificador del tema correspondiente en el archivo.  
  
```  
virtual HRESULT get_accHelpTopic(
    BSTR* pszHelpFile,  
    VARIANT varChild,  
    long* pidTopic);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pszHelpFile`  
 Dirección de un `BSTR` que recibe la ruta de acceso completa de la `WinHelp` archivo que está asociado con el objeto especificado, si existe.  
  
 [in] `varChild`  
 Especifica si va a recuperar el tema de ayuda es que el objeto o uno de los elementos secundarios del objeto. Este parámetro puede ser `CHILDID_SELF` (para obtener un tema de ayuda para el objeto) o un identificador secundario (para obtener un tema de ayuda para uno de los secundarios de elementos del objeto).  
  
 [in] `pidTopic`  
 Identifica el `Help` tema de archivo que está asociado con el objeto especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 `CBasePane`Implemente este método. Por lo tanto, `CBasePane::get_accHelpTopic` siempre devuelve `S_FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función forma parte de la compatibilidad de Active Accessibility en MFC. Reemplace esta función en una clase derivada para proporcionar información de ayuda sobre el objeto.  
  
##  <a name="get_accselection"></a>CBasePane::get_accSelection  
 El marco de trabajo llama a este método para recuperar al elemento secundario seleccionado de este objeto.  
  
```  
virtual HRESULT get_accSelection(VARIANT* pvarChildren);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pvarChildren`  
 Recibe la información que identifica al elemento secundario seleccionado.  
  
### <a name="return-value"></a>Valor devuelto  
 `CBasePane`Implemente este método. Si `pvarChildren` es `NULL` este método devuelve `E_INVALIDARG`. De lo contrario, este método devuelve `DISP_E_MEMBERNOTFOUND`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función forma parte de la compatibilidad de Active Accessibility en MFC. Reemplace esta función en una clase derivada si tiene elementos de la interfaz de usuario no son ventanas que no sea de controles ActiveX sin ventana.  
  
##  <a name="getcaptionheight"></a>CBasePane::GetCaptionHeight  
 Devuelve la altura del título.  
  
```  
virtual int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Alto del título.  
  
##  <a name="getcontrolbarstyle"></a>CBasePane::GetControlBarStyle  
 Devuelve el estilo de barra de control.  
  
```  
virtual DWORD GetControlBarStyle() const 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una combinación OR bit a bit de los indicadores AFX_CBRS_.  
  
### <a name="remarks"></a>Comentarios  
 El valor devuelto es una combinación de los siguientes valores posibles.  
  
|Estilo|Descripción|  
|-----------|-----------------|  
|`AFX_CBRS_FLOAT`|Hace que el tipo float de barra de control.|  
|`AFX_CBRS_AUTOHIDE`|Permite oculta automáticamente el modo.|  
|`AFX_CBRS_RESIZE`|Permite cambiar el tamaño de la barra de control. Cuando se establece este marcador, se puede colocar la barra de controles en un panel acoplable.|  
|`AFX_CBRS_CLOSE`|Permite ocultar la barra de control.|  
  
##  <a name="getcurrentalignment"></a>CBasePane::GetCurrentAlignment  
 Devuelve la alineación actual del panel.  
  
```  
virtual DWORD GetCurrentAlignment() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La alineación actual de la barra de control. La siguiente tabla muestra los valores posibles:  
  
|Valor|Alineación|  
|-----------|---------------|  
|`CBRS_ALIGN_LEFT`|Alineación a la izquierda.|  
|`CBRS_ALIGN_RIGHT`|Alineación a la derecha.|  
|`CBRS_ALIGN_TOP`|Alineación superior.|  
|`CBRS_ALIGN_BOTTOM`|Alineación de la parte inferior.|  
  
##  <a name="getdockingmode"></a>CBasePane::GetDockingMode  
 Devuelve el modo de acoplamiento actual para el panel.  
  
```  
virtual AFX_DOCK_TYPE GetDockingMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 DT_STANDARD si arrastra el panel se indica en la pantalla mediante un rectángulo de arrastre. DT_IMMEDIATE si se arrastra el contenido del panel.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para determinar el modo de acoplamiento actual del panel.  
  
 Si `CBasePane::m_dockMode` es undefined (DT_UNDEFINED), el modo de acoplamiento se toma desde el modo de acoplamiento global ( `AFX_GLOBAL_DATA::m_dockModeGlobal`).  
  
 Estableciendo `m_dockMode` o reemplazar `GetDockingMode` puede controlar el modo de acoplamiento para cada panel.  
  
##  <a name="getdocksiteframewnd"></a>CBasePane::GetDockSiteFrameWnd  
 Devuelve un puntero a la [CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)objeto en el panel está acoplado.  
  
```  
virtual CWnd* GetDockSiteFrameWnd() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al sitio de acoplamiento del panel.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para recuperar un puntero al sitio de acoplamiento del panel. Si el panel está flotando, el sitio de vinculación puede ser una ventana de marco principal si el panel se acopla al marco principal o una ventana de marco reducido.  
  
##  <a name="getenabledalignment"></a>CBasePane::GetEnabledAlignment  
 Devuelve los estilos CBRS_ALIGN_ que se aplican al panel.  
  
```  
virtual DWORD GetEnabledAlignment() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una combinación de estilos CBRS_ALIGN_. La siguiente tabla muestra los estilos posibles:  
  
|Marcar|Alineación habilitado|  
|----------|-----------------------|  
|`CBRS_ALIGN_LEFT`|A la izquierda.|  
|`CBRS_ALIGN_RIGHT`|Correcto.|  
|`CBRS_ALIGN_TOP`|Arriba.|  
|`CBRS_ALIGN_BOTTOM`|Parte inferior.|  
|`CBRS_ALIGN_ANY`|Combinación de todas las marcas.|  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para determinar la alineación habilitada para el panel. Alineación habilitado significa los lados de la ventana de marco principal que se puede acoplar un panel en.  
  
 Habilitar el acoplamiento alineación mediante [CBasePane::EnableDocking](#enabledocking).  
  
##  <a name="getmfcstyle"></a>CBasePane::GetMFCStyle  
 Devuelve los estilos de panel que son específicos de MFC.  
  
```  
virtual DWORD GetMFCStyle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una combinación de estilos de panel (AFX_CBRS_) específicas de la biblioteca.  
  
##  <a name="getpaneicon"></a>CBasePane::GetPaneIcon  
 Devuelve un identificador para el icono del panel.  
  
```  
virtual HICON GetPaneIcon(BOOL bBigIcon);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bBigIcon`  
 Especifica que un píxel 32 por icono 32 píxeles si `TRUE`; especifica que un píxel de 16 por icono 16 píxeles si `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador del icono de panel. Si se produce un error, devuelve `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada llama [CWnd::GetIcon](../../mfc/reference/cwnd-class.md#geticon).  
  
##  <a name="getpanerow"></a>CBasePane::GetPaneRow  
 Devuelve un puntero a la [CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)objeto en el panel está acoplado.  
  
```  
CDockingPanesRow* GetPaneRow();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a `CDockingPanesRow` si el panel está acoplado, o `NULL` si está flotando.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para tener acceso a la fila donde un panel está acoplado. Por ejemplo, para organizar los paneles en una fila determinada, llame a `GetPaneRow` y, a continuación, llame a [CDockingPanesRow::ArrangePanes](../../mfc/reference/cdockingpanesrow-class.md#arrangepanes).  
  
##  <a name="getpanestyle"></a>CBasePane::GetPaneStyle  
 Devuelve el estilo del panel.  
  
```  
virtual DWORD GetPaneStyle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una combinación de estilos de barra de control (incluidos los estilos CBRS_) definido por el [CBasePane::SetPaneStyle](#setpanestyle) método en tiempo de creación.  
  
##  <a name="getparentdocksite"></a>CBasePane::GetParentDockSite  
 Devuelve un puntero al sitio de acoplamiento principal.  
  
```  
virtual CDockSite* GetParentDockSite() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El sitio de acoplamiento principal.  
  
##  <a name="getparentminiframe"></a>CBasePane::GetParentMiniFrame  
 Devuelve un puntero a la ventana de marco reducido primaria.  
  
```  
virtual CPaneFrameWnd* GetParentMiniFrame(BOOL bNoAssert=FALSE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bNoAssert`  
 Si `TRUE`, este método no se busca punteros no válidos. Si se llama a este método cuando se cierra la aplicación, establezca este parámetro en `TRUE`.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero válido a la ventana de marco reducido primario si el panel es flotante; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para recuperar un puntero a la ventana de marco reducido primaria. Este método recorre en iteración todos los elementos primarios y comprueba si un objeto derivado de [CPaneFrameWnd clase](../../mfc/reference/cpaneframewnd-class.md).  
  
 Utilice `GetParentMiniFrame` para determinar si el panel está flotando.  
  
##  <a name="getparenttabbedpane"></a>CBasePane::GetParentTabbedPane  
 Devuelve un puntero al panel con fichas primario.  
  
```  
CBaseTabbedPane* GetParentTabbedPane() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al panel con fichas primario si existe; de lo contrario, `NULL`.  
  
##  <a name="getparenttabwnd"></a>CBasePane::GetParentTabWnd  
 Devuelve un puntero a la ventana primaria que está dentro de una pestaña.  
  
```  
CMFCBaseTabCtrl* GetParentTabWnd(HWND& hWndTab) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `hWndTab`  
 Si el valor devuelto no es `NULL`, este parámetro contiene el identificador de la ventana con fichas primaria.  
  
### <a name="return-value"></a>Valor devuelto  
 Ventana de fichas de un puntero válido para el elemento primario o `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para recuperar un puntero a la ventana con fichas primaria. A veces no es suficiente llamar a `GetParent`, ya que puede ser un panel dentro de un contenedor de acoplamiento ( [CDockablePaneAdapter clase](../../mfc/reference/cdockablepaneadapter-class.md)) o dentro de un adaptador de panel ( [CDockablePaneAdapter clase](../../mfc/reference/cdockablepaneadapter-class.md)). Mediante el uso de `GetParentTabWnd` , podrá recuperar un puntero válido en esos casos (suponiendo que el elemento primario es una ventana con fichas).  
  
##  <a name="getrecentvisiblestate"></a>CBasePane::GetRecentVisibleState  
 El marco de trabajo llama a este método cuando se restaura un panel desde un archivo.  
  
```  
virtual BOOL GetRecentVisibleState() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `BOOL` que especifica el estado de visibilidad recientes. Si `TRUE`, el panel era visible cuando serializa y debe estar visible cuando restaura. Si `FALSE`, se oculta el panel cuando serializa y debe estar oculto cuando restaura.  
  
##  <a name="hideinprintpreviewmode"></a>CBasePane::HideInPrintPreviewMode  
 Especifica si el panel está oculto en la vista preliminar.  
  
```  
virtual BOOL HideInPrintPreviewMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si no se muestra el panel de vista previa de impresión; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Paneles de base no se muestran en la vista previa de impresión. Por lo tanto, este método devuelve siempre `TRUE`.  
  
##  <a name="insertpane"></a>CBasePane::InsertPane  
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
  
##  <a name="isaccessibilitycompatible"></a>CBasePane::IsAccessibilityCompatible  
 Especifica si el panel admite Active Accessibility.  
  
```  
virtual BOOL IsAccessibilityCompatible();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel admite Active Accessibility; de lo contrario, `FALSE`.  
  
##  <a name="isautohidemode"></a>CBasePane::IsAutoHideMode  
 Determina si un panel está en modo de ocultación automática.  
  
```  
virtual BOOL IsAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel está en modo de ocultación automática; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Paneles de base no se pueden ocultar automáticamente. Este método devuelve siempre `FALSE`.  
  
##  <a name="isdialogcontrol"></a>CBasePane::IsDialogControl  
 Especifica si el panel es un control de cuadro de diálogo.  
  
```  
BOOL IsDialogControl() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel es un control de cuadro de diálogo; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo usa este método para garantizar la coherencia del diseño para todos los paneles.  
  
##  <a name="isdocked"></a>CBasePane::IsDocked  
 Determina si el panel está acoplado.  
  
```  
virtual BOOL IsDocked() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento primario del panel no es un marco mínima o si el panel está flotando en un marco reducido con otro panel; de lo contrario, `FALSE`.  
  
##  <a name="isfloating"></a>CBasePane::IsFloating  
 Determina si el panel está flotando.  
  
```  
virtual BOOL IsFloating() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel es flotante; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve el valor contrario de [CBasePane::IsDocked](#isdocked).  
  
##  <a name="ishorizontal"></a>CBasePane::IsHorizontal  
 Determina si el panel se acopla horizontalmente.  
  
```  
virtual BOOL IsHorizontal() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se acopla horizontalmente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada comprueba la alineación de acoplamiento actual para `CBRS_ORIENT_HORZ`.  
  
##  <a name="isinfloatingmultipaneframewnd"></a>CBasePane::IsInFloatingMultiPaneFrameWnd  
 Especifica si el panel está en una ventana de marco de varios paneles ( [CMultiPaneFrameWnd clase](../../mfc/reference/cmultipaneframewnd-class.md)).  
  
```  
virtual BOOL IsInFloatingMultiPaneFrameWnd() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel está en una ventana de marco de varios paneles; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Pueden flotar paneles acoplables solo en una ventana de marco de varios paneles. Por lo tanto, `CBasePane::IsInFloatingMultiPaneFrameWnd` siempre devuelve `FALSE`.  
  
##  <a name="ismditabbed"></a>CBasePane::IsMDITabbed  
 Determina si el panel se ha agregado a una ventana secundaria MDI como un documento con fichas.  
  
```  
virtual BOOL IsMDITabbed() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se agregó a una ventana secundaria MDI como un documento con fichas; de lo contrario, `FALSE`.  
  
##  <a name="ispanevisible"></a>CBasePane::IsPaneVisible  
 Especifica si el `WS_VISIBLE` marca está establecida para el panel.  
  
```  
BOOL IsPaneVisible() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si `WS_VISIBLE` se ha establecido; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice [CBasePane::IsVisible](#isvisible) para determinar la visibilidad del panel.  
  
##  <a name="ispointneardocksite"></a>CBasePane::IsPointNearDockSite  
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
 Especifica qué borde es el punto de cerca. Los valores posibles son `CBRS_ALIGN_LEFT`, `CBRS_ALIGN_RIGHT`, `CBRS_ALIGN_TOP`, y`CBRS_ALIGN_BOTTOM`  
  
 [out] `bOuterEdge`  
 `TRUE`Si el punto está cerca del borde exterior del sitio de vinculación; `FALSE` en caso contrario.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el punto está cerca del sitio de vinculación; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El punto está cerca del sitio de vinculación cuando se encuentra dentro de la sensibilidad establecida en el Administrador de acoplamiento. La sensibilidad predeterminado es 15 píxeles.  
  
##  <a name="isresizable"></a>CBasePane::IsResizable  
 Determina si el panel puede cambiarse.  
  
```  
virtual BOOL IsResizable() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel puede cambiarse por el usuario; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Paneles de [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) puede cambiarse.  
  
 La barra de estado ( [CMFCStatusBar clase](../../mfc/reference/cmfcstatusbar-class.md)) y la barra de acoplamiento ( [CDockSite clase](../../mfc/reference/cdocksite-class.md)) no puede cambiarse.  
  
##  <a name="isrestoredfromregistry"></a>CBasePane::IsRestoredFromRegistry  
 Determina si el panel está restaurado desde el registro.  
  
```  
virtual BOOL IsRestoredFromRegistry() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se restaura en el registro; de lo contrario, `FALSE`.  
  
##  <a name="istabbed"></a>CBasePane::IsTabbed  
 Determina si el panel se ha insertado en el control de ficha de una ventana con fichas.  
  
```  
virtual BOOL IsTabbed() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la barra de control se inserta en una ficha de una ventana con fichas; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método recupera un puntero para el objeto primario inmediato y determina si la clase de tiempo de ejecución del elemento primario es [CMFCBaseTabCtrl clase](../../mfc/reference/cmfcbasetabctrl-class.md).  
  
##  <a name="isvisible"></a>CBasePane::IsVisible  
 Determina si el panel está visible.  
  
```  
virtual BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel está visible; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para determinar la visibilidad de un panel. No utilice `::IsWindowVisible`.  
  
 Si el panel no es por fichas (consulte [CBasePane::IsTabbed](#istabbed)), este método comprueba el `WS_VISIBLE` estilo. Si el panel se fichas, este método comprueba la visibilidad de la ventana con fichas primaria. Si está visible la ventana primaria, la función comprueba la visibilidad de la ficha de panel utilizando [CMFCBaseTabCtrl::IsTabVisible](../../mfc/reference/cmfcbasetabctrl-class.md#istabvisible).  
  
##  <a name="loadstate"></a>CBasePane::LoadState  
 Carga el estado del panel desde el registro.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName=NULL,  
    int nIndex=-1,  
    UINT uiID=(UINT)-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Nombre del perfil.  
  
 [in] `nIndex`  
 Índice de perfil.  
  
 [in] `uiID`  
 Id. de panel.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el estado del panel se ha cargado correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para cargar el estado del panel desde el registro. Reemplazar en una clase derivada para cargar información adicional que se guardan de forma [CBasePane::SaveState](#savestate).  
  
##  <a name="movewindow"></a>CBasePane::MoveWindow  
 Mueve el panel.  
  
```  
virtual HDWP MoveWindow(
    CRect& rect,  
    BOOL bRepaint = TRUE,  
    HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rect`  
 Un rectángulo que especifica la nueva ubicación y el tamaño del panel.  
  
 [in] `bRepaint`  
 Si `TRUE`, se vuelve a dibujar el panel. Si `FALSE`, no se vuelve a dibujar el panel.  
  
 [in] `hdwp`  
 Identificador de una estructura de posición de la ventana aplazada.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de una estructura de posición de ventana diferida o `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Si se pasa `NULL` como el `hdwp` parámetro, este método mueve la ventana normalmente. Si pasa un identificador, este método realiza un movimiento de ventana aplazada. Puede obtener un identificador llamando a [BeginDeferWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms632672) o almacenar el valor devuelto de una llamada anterior a este método.  
  
##  <a name="onafterchangeparent"></a>CBasePane::OnAfterChangeParent  
 Llamado por el marco después de realizar cambios del panel primario.  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndOldParent`  
 Un puntero al elemento primario anterior.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método después de primaria del panel cambia, normalmente debido a una operación de acoplamiento o de punto flotante.  
  
 La implementación predeterminada no hace nada.  
  
##  <a name="onbeforechangeparent"></a>CBasePane::OnBeforeChangeParent  
 Llamado por el marco justo antes de que el panel cambia su ventana primaria.  
  
```  
virtual void OnBeforeChangeParent(
    CWnd* pWndNewParent,  
    BOOL bDelay=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndNewParent`  
 Un puntero a una nueva ventana principal.  
  
 [in] `bDelay`  
 Especifica si se deben retrasar los ajustes de diseño.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método justo antes cambia en primario del panel, normalmente debido a un acoplamiento, flotante o de operación de ocultar automáticamente.  
  
 La implementación predeterminada no hace nada.  
  
##  <a name="ondrawcaption"></a>CBasePane::OnDrawCaption  
 El marco de trabajo llama a este método cuando se dibuja la leyenda.  
  
```  
virtual void OnDrawCaption();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método no tiene ninguna funcionalidad para la `CBasePane` clase.  
  
##  <a name="onmovepanedivider"></a>CBasePane::OnMovePaneDivider  
 Este método no se utiliza actualmente.  
  
```  
virtual void OnMovePaneDivider(CPaneDivider*);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `CPaneDivider*`  
 No usado.  
  
##  <a name="onpanecontextmenu"></a>CBasePane::OnPaneContextMenu  
 Llamado por el marco cuando compila un menú con una lista de paneles.  
  
```  
virtual void OnPaneContextMenu(
    CWnd* pParentFrame,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pParentFrame`  
 Un puntero al marco primario.  
  
 [in] `point`  
 Especifica la ubicación del menú contextual.  
  
### <a name="remarks"></a>Comentarios  
 `OnPaneContextMenu`llama al administrador de acoplamiento, que mantiene la lista de paneles de la ventana de marco actual. Este método agrega los nombres de los paneles a un menú contextual y lo muestra. Los comandos en el menú Mostrar u oculten los paneles individuales.  
  
 Invalide este método para personalizar este comportamiento.  
  
##  <a name="onremovefromminiframe"></a>CBasePane::OnRemoveFromMiniFrame  
 Lo llama el marco de trabajo cuando se quita un panel de la ventana de marco flotante primaria.  
  
```  
virtual void OnRemoveFromMiniFrame(CPaneFrameWnd* pMiniFrame);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMiniFrame`  
 Puntero a una ventana de marco reducido del que se va a quitar el panel.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando se quita un panel de la ventana de marco reducido primaria (como resultado de acoplamiento, por ejemplo).  
  
 La implementación predeterminada no hace nada.  
  
##  <a name="onsetaccdata"></a>CBasePane::OnSetAccData  
 `CBasePane`no se utiliza este método.  
  
```  
virtual BOOL OnSetAccData(long lVal);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lVal`  
 No usado.  
  
### <a name="return-value"></a>Valor devuelto  
 Este método devuelve siempre `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="panefrompoint"></a>CBasePane::PaneFromPoint  
 Devuelve el panel que contiene el punto especificado.  
  
```  
CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    bool bExactBar = false,  
    CRuntimeClass* pRTCBarType = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 Especifica el punto, en coordenadas de pantalla para comprobar.  
  
 [in] `nSensitivity`  
 Aumentar el área de búsqueda en esta cantidad. Un panel cumple los criterios de búsqueda si el punto especificado se encuentra en el área de mayor.  
  
 [in] `bExactBar`  
 `TRUE`para omitir la `nSensitivity` parámetro; en caso contrario, `FALSE`.  
  
 [in] `pRTCBarType`  
 Si no `NULL`, el método busca solo los paneles del tipo especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 El `CBasePane`-objeto derivado que contiene el punto especificado, o `NULL` si no se encontró ningún panel.  
  
##  <a name="recalclayout"></a>CBasePane::RecalcLayout  
 `CBasePane`no se utiliza este método.  
  
```  
virtual void RecalcLayout();
```  
  
##  <a name="removepanefromdockmanager"></a>CBasePane::RemovePaneFromDockManager  
 Anula el registro de un panel y lo quita de la lista en el Administrador de acoplamiento.  
  
```  
void RemovePaneFromDockManager(
    CBasePane* pBar,  
    BOOL bDestroy = TRUE,  
    BOOL bAdjustLayout = FALSE,  
    BOOL bAutoHide = FALSE,  
    CBasePane* pBarReplacement = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Un puntero a un panel que se va a quitar.  
  
 [in] `bDestroy`  
 Si `TRUE`, se destruye el panel quitado.  
  
 [in] `bAdjustLayout`  
 Si `TRUE`, ajustar el diseño de acoplamiento inmediatamente.  
  
 [in] `bAutoHide`  
 Si `TRUE`, la lista de barras Ocultar automáticamente está relacionado con el diseño de acoplamiento. Si `FALSE`, está relacionado con el diseño de acoplamiento a la lista de paneles regulares.  
  
 [in] `pBarReplacement`  
 Puntero a un panel que reemplazará al panel quitado.  
  
##  <a name="savestate"></a>CBasePane::SaveState  
 Guarda el estado del panel en el registro.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName=NULL,  
    int nIndex=-1,  
    UINT uiID=(UINT)-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Nombre del perfil.  
  
 [in] `nIndex`  
 Índice de perfil.  
  
 [in] `uiID`  
 Id. de panel.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el estado se guardó correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando guarda el estado del panel en el registro. Invalidar `SaveState` en una clase derivada para almacenar información adicional.  
  
##  <a name="selectdefaultfont"></a>CBasePane::SelectDefaultFont  
 Selecciona la fuente predeterminada para un contexto de dispositivo especificado.  
  
```  
CFont* SelectDefaultFont(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Un contexto de dispositivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al valor predeterminado [CFont (clase)](../../mfc/reference/cfont-class.md) objeto.  
  
##  <a name="setcontrolbarstyle"></a>CBasePane::SetControlBarStyle  
 Establece el estilo de barra de control.  
  
```  
virtual void SetControlBarStyle(DWORD dwNewStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwNewStyle`  
 Una combinación OR bit a bit de los siguientes valores posibles.  
  
|Estilo|Descripción|  
|-----------|-----------------|  
|`AFX_CBRS_FLOAT`|Hace que el tipo float de barra de control.|  
|`AFX_CBRS_AUTOHIDE`|Permite oculta automáticamente el modo.|  
|`AFX_CBRS_RESIZE`|Permite cambiar el tamaño de la barra de control. Cuando se establece este marcador, se puede colocar la barra de controles en un panel acoplable.|  
|`AFX_CBRS_CLOSE`|Permite ocultar la barra de control.|  
  
##  <a name="setdockingmode"></a>CBasePane::SetDockingMode  
 Establece el modo de acoplamiento del panel.  
  
```  
void SetDockingMode(AFX_DOCK_TYPE dockModeNew);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dockModeNew`  
 Especifica el nuevo modo de acoplamiento del panel.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo admite dos modos de acoplamiento: estándar y de forma inmediata.  
  
 En el modo de acoplamiento estándar, paneles y ventanas de marco reducido se mueven alrededor de un rectángulo de arrastre. En el modo inmediato de acoplamiento, barras de controles y ventanas de marco reducido se mueven inmediatamente con su contexto.  
  
 Inicialmente, el modo de acoplamiento está definido globalmente mediante [CDockingManager::m_dockModeGlobal](../../mfc/reference/cdockingmanager-class.md#m_dockmodeglobal). Puede establecer el modo de acoplamiento para cada panel individualmente mediante el `SetDockingMode` método.  
  
##  <a name="setpanealignment"></a>CBasePane::SetPaneAlignment  
 Establece la alineación del panel.  
  
```  
virtual void SetPaneAlignment(DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwAlignment`  
 Especifica la alineación nuevo.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, el marco de trabajo llama a este método cuando un panel se acopla en un lado del marco principal a otro.  
  
 La siguiente tabla muestra los valores posibles para `dwAlignment`:  
  
|Valor|Alineación|  
|-----------|---------------|  
|`CBRS_ALIGN_LEFT`|Alineación a la izquierda.|  
|`CBRS_ALIGN_RIGHT`|Alineación a la derecha.|  
|`CBRS_ALIGN_TOP`|Alineación superior.|  
|`CBRS_ALIGN_BOTTOM`|Alineación de la parte inferior.|  
  
##  <a name="setpanestyle"></a>CBasePane::SetPaneStyle  
 Establece el estilo del panel.  
  
```  
virtual void SetPaneStyle(DWORD dwNewStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwNewStyle`  
 Especifica el nuevo estilo a establecer.  
  
### <a name="remarks"></a>Comentarios  
 Este método puede utilizarse para establecer cualquiera de los estilos CBRS_ que están definidos en afxres.h. Como estilo de panel y alineación de panel se almacenan juntos, establezca el nuevo estilo al combinarla con la alineación actual.  
  
 `pPane->SetPaneStyle (pPane->GetCurrentAlignment() | CBRS_TOOLTIPS);`  
  
##  <a name="setwindowpos"></a>CBasePane::SetWindowPos  
 Cambia el tamaño, la posición y el orden Z de un panel.  
  
```  
virtual HDWP SetWindowPos(
    const CWnd* pWndInsertAfter,  
    int x,  
    int y,  
    int cx,  
    int cy,  
    UINT nFlags,  
    HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndInsertAfter`  
 Identifica la `CWnd` objeto que precede a este `CWnd` objeto en el orden Z. Para obtener más información, consulte [CWnd:: SetWindowPos](../../mfc/reference/cwnd-class.md#setwindowpos).  
  
 [in] `x`  
 Especifica la posición del lado izquierdo de la ventana.  
  
 [in] `y`  
 Especifica la posición de la parte superior de la ventana.  
  
 [in] `cx`  
 Especifica el ancho de la ventana.  
  
 [in] `cy`  
 Especifica el alto de la ventana.  
  
 [in] `nFlags`  
 Especifica las opciones de tamaño y posición. Para obtener más información, consulte [CWnd:: SetWindowPos](../../mfc/reference/cwnd-class.md#setwindowpos).  
  
 [in] `hdwp`  
 Identificador de una estructura que contiene información de tamaño y posición de una o varias ventanas.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de una estructura de posición de ventana aplazada actualizada o `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Si `pWndInsertAfter` es `NULL`, este método llama a [CWnd:: SetWindowPos](../../mfc/reference/cwnd-class.md#setwindowpos). Si `pWndInsertAfter` no es `NULL`, este método llama a `DeferWindowPos`.  
  
##  <a name="showpane"></a>CBasePane::ShowPane  
 Muestra u oculta el panel.  
  
```  
virtual void ShowPane(
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bShow`  
 Especifica si se debe mostrar ( `TRUE`) u ocultar ( `FALSE`) un panel.  
  
 [in] `bDelay`  
 Si `TRUE`, volver a calcular el diseño de acoplamiento se retrasa.  
  
 [in] `bActivate`  
 Si `TRUE`, está activo cuando se muestra el panel.  
  
### <a name="remarks"></a>Comentarios  
 Este método muestra u oculta un panel. Utilice este método en lugar de `ShowWindow` porque este método notifica a los administradores de acoplamiento relevantes acerca de los cambios en la visibilidad del panel.  
  
 Utilice [CBasePane::IsVisible](#isvisible) para determinar la visibilidad actual de un panel.  
  
##  <a name="stretchpane"></a>CBasePane::StretchPane  
 Expande un panel vertical u horizontalmente.  
  
```  
virtual CSize StretchPane(
    int nLength,  
    BOOL bVert);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nLength`  
 La longitud por el que se va a expandir el panel.  
  
 [in] `bVert`  
 Si `TRUE`, expandir el panel verticalmente. Si `FALSE`, expandir el panel horizontalmente.  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño del panel estirado.  
  
##  <a name="undockpane"></a>CBasePane::UndockPane  
 Quita el panel desde el sitio de vinculación, slider predeterminado o ventana de marco reducido que actualmente está acoplada.  
  
```  
virtual void UndockPane(BOOL bDelay=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bDelay`  
 Si es TRUE, el diseño de acoplamiento no se actualiza inmediatamente.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para manipular el estado del panel o excluir el panel de diseño de acoplamiento.  
  
 Si desea seguir usando este panel, llamar a [CBasePane::DockPane](#dockpane) o [CBasePane::FloatPane](#floatpane) antes de llamar a este método.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CPane](../../mfc/reference/cbasepane-class.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)

