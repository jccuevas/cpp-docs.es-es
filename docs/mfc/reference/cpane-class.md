---
title: Clase CPane | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPane
- AFXPANE/CPane
- AFXPANE/CPane::AdjustSizeImmediate
- AFXPANE/CPane::AllocElements
- AFXPANE/CPane::AllowShowOnPaneMenu
- AFXPANE/CPane::CalcAvailableSize
- AFXPANE/CPane::CalcInsideRect
- AFXPANE/CPane::CalcRecentDockedRect
- AFXPANE/CPane::CalcSize
- AFXPANE/CPane::CanBeDocked
- AFXPANE/CPane::CanBeTabbedDocument
- AFXPANE/CPane::ConvertToTabbedDocument
- AFXPANE/CPane::CopyState
- AFXPANE/CPane::Create
- AFXPANE/CPane::CreateDefaultMiniframe
- AFXPANE/CPane::CreateEx
- AFXPANE/CPane::DockByMouse
- AFXPANE/CPane::DockPane
- AFXPANE/CPane::DockPaneStandard
- AFXPANE/CPane::DockToFrameWindow
- AFXPANE/CPane::DoesAllowSiblingBars
- AFXPANE/CPane::FloatPane
- AFXPANE/CPane::GetAvailableExpandSize
- AFXPANE/CPane::GetAvailableStretchSize
- AFXPANE/CPane::GetBorders
- AFXPANE/CPane::GetClientHotSpot
- AFXPANE/CPane::GetDockSiteRow
- AFXPANE/CPane::GetExclusiveRowMode
- AFXPANE/CPane::GetHotSpot
- AFXPANE/CPane::GetMinSize
- AFXPANE/CPane::GetPaneName
- AFXPANE/CPane::GetVirtualRect
- AFXPANE/CPane::IsChangeState
- AFXPANE/CPane::IsDragMode
- AFXPANE/CPane::IsInFloatingMultiPaneFrameWnd
- AFXPANE/CPane::IsLeftOf
- AFXPANE/CPane::IsResizable
- AFXPANE/CPane::IsTabbed
- AFXPANE/CPane::LoadState
- AFXPANE/CPane::MoveByAlignment
- AFXPANE/CPane::MovePane
- AFXPANE/CPane::OnAfterChangeParent
- AFXPANE/CPane::OnBeforeChangeParent
- AFXPANE/CPane::OnPressCloseButton
- AFXPANE/CPane::OnShowControlBarMenu
- AFXPANE/CPane::RecalcLayout
- AFXPANE/CPane::SaveState
- AFXPANE/CPane::SetActiveInGroup
- AFXPANE/CPane::SetBorders
- AFXPANE/CPane::SetClientHotSpot
- AFXPANE/CPane::SetDockState
- AFXPANE/CPane::SetExclusiveRowMode
- AFXPANE/CPane::SetMiniFrameRTC
- AFXPANE/CPane::SetMinSize
- AFXPANE/CPane::SetVirtualRect
- AFXPANE/CPane::StretchPaneDeferWndPos
- AFXPANE/CPane::ToggleAutoHide
- AFXPANE/CPane::UndockPane
- AFXPANE/CPane::UpdateVirtualRect
- AFXPANE/CPane::OnAfterDock
- AFXPANE/CPane::OnAfterFloat
- AFXPANE/CPane::OnBeforeDock
- AFXPANE/CPane::OnBeforeFloat
- AFXPANE/CPane::m_bHandleMinSize
- AFXPANE/CPane::m_recentDockInfo
dev_langs: C++
helpviewer_keywords:
- CPane [MFC], AdjustSizeImmediate
- CPane [MFC], AllocElements
- CPane [MFC], AllowShowOnPaneMenu
- CPane [MFC], CalcAvailableSize
- CPane [MFC], CalcInsideRect
- CPane [MFC], CalcRecentDockedRect
- CPane [MFC], CalcSize
- CPane [MFC], CanBeDocked
- CPane [MFC], CanBeTabbedDocument
- CPane [MFC], ConvertToTabbedDocument
- CPane [MFC], CopyState
- CPane [MFC], Create
- CPane [MFC], CreateDefaultMiniframe
- CPane [MFC], CreateEx
- CPane [MFC], DockByMouse
- CPane [MFC], DockPane
- CPane [MFC], DockPaneStandard
- CPane [MFC], DockToFrameWindow
- CPane [MFC], DoesAllowSiblingBars
- CPane [MFC], FloatPane
- CPane [MFC], GetAvailableExpandSize
- CPane [MFC], GetAvailableStretchSize
- CPane [MFC], GetBorders
- CPane [MFC], GetClientHotSpot
- CPane [MFC], GetDockSiteRow
- CPane [MFC], GetExclusiveRowMode
- CPane [MFC], GetHotSpot
- CPane [MFC], GetMinSize
- CPane [MFC], GetPaneName
- CPane [MFC], GetVirtualRect
- CPane [MFC], IsChangeState
- CPane [MFC], IsDragMode
- CPane [MFC], IsInFloatingMultiPaneFrameWnd
- CPane [MFC], IsLeftOf
- CPane [MFC], IsResizable
- CPane [MFC], IsTabbed
- CPane [MFC], LoadState
- CPane [MFC], MoveByAlignment
- CPane [MFC], MovePane
- CPane [MFC], OnAfterChangeParent
- CPane [MFC], OnBeforeChangeParent
- CPane [MFC], OnPressCloseButton
- CPane [MFC], OnShowControlBarMenu
- CPane [MFC], OnShowControlBarMenu
- CPane [MFC], RecalcLayout
- CPane [MFC], SaveState
- CPane [MFC], SetActiveInGroup
- CPane [MFC], SetBorders
- CPane [MFC], SetClientHotSpot
- CPane [MFC], SetDockState
- CPane [MFC], SetExclusiveRowMode
- CPane [MFC], SetMiniFrameRTC
- CPane [MFC], SetMinSize
- CPane [MFC], SetVirtualRect
- CPane [MFC], StretchPaneDeferWndPos
- CPane [MFC], ToggleAutoHide
- CPane [MFC], UndockPane
- CPane [MFC], UpdateVirtualRect
- CPane [MFC], OnAfterDock
- CPane [MFC], OnAfterFloat
- CPane [MFC], OnBeforeDock
- CPane [MFC], OnBeforeFloat
- CPane [MFC], m_bHandleMinSize
- CPane [MFC], m_recentDockInfo
ms.assetid: 5c651a64-3c79-4d94-9676-45f6402a6bc5
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e078f094e51b022bc697ba44eec47de1bf452c96
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cpane-class"></a>CPane Class
El `CPane` clase es una mejora de la [CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md). Si va a actualizar un proyecto MFC existente, reemplace todas las apariciones de `CControlBar` con `CPane`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CPane : public CBasePane  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CPane::~CPane`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPane::AdjustSizeImmediate](#adjustsizeimmediate)|Inmediatamente, vuelve a calcular el diseño de un panel.|  
|[CPane::AllocElements](#allocelements)|Asigna almacenamiento para uso interno.|  
|[CPane::AllowShowOnPaneMenu](#allowshowonpanemenu)|Especifica si el panel se muestra en la lista generada en tiempo de ejecución de los paneles de la aplicación.|  
|[CPane::CalcAvailableSize](#calcavailablesize)|Calcula la diferencia de tamaño entre un rectángulo especificado y el rectángulo de la ventana actual.|  
|[CPane::CalcInsideRect](#calcinsiderect)|Calcula el interior del rectángulo de un panel, teniendo en cuenta los bordes y las barras de redimensionamiento.|  
|[CPane::CalcRecentDockedRect](#calcrecentdockedrect)|Calcula el rectángulo recientemente acoplado.|  
|[CPane::CalcSize](#calcsize)|Calcula el tamaño del panel.|  
|[CPane::CanBeDocked](#canbedocked)|Determina si se puede acoplar el panel en el panel de base especificado.|  
|[CPane::CanBeTabbedDocument](#canbetabbeddocument)|Determina si el panel se puede convertir a un documento con pestañas.|  
|[CPane::ConvertToTabbedDocument](#converttotabbeddocument)|Convierte un panel acoplable en un documento con pestañas.|  
|[CPane::CopyState](#copystate)|Copia el estado de un panel. (Invalida [CBasePane::CopyState](../../mfc/reference/cbasepane-class.md#copystate).)|  
|[CPANE:: Create](#create)|Crea una barra de control y lo adjunta a la `CPane` objeto.|  
|[Createdefaultminiframe](#createdefaultminiframe)|Crea una ventana de marco reducido para un panel flotante.|  
|[CPANE:: CreateEx](#createex)|Crea una barra de control y lo adjunta a la `CPane` objeto.|  
|`CPane::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|[CPane::DockByMouse](#dockbymouse)|Acopla un panel con el mouse acoplamiento método.|  
|[CPane::DockPane](#dockpane)|Acopla el panel flotante a un panel de base.|  
|[CPane::DockPaneStandard](#dockpanestandard)|Acopla un panel mediante el uso de esquema de acoplamiento (estándar).|  
|[CPane::DockToFrameWindow](#docktoframewindow)|Acopla un panel acoplable a un marco. (Invalida `CBasePane::DockToFrameWindow`).|  
|[CPane::DoesAllowSiblingBars](#doesallowsiblingbars)|Indica si se puede acoplar el panel de otro en la misma fila en el panel actual está acoplado.|  
|[CPane::FloatPane](#floatpane)|Desplaza el panel.|  
|[CPane::GetAvailableExpandSize](#getavailableexpandsize)|Devuelve la cantidad, en píxeles, que se pueda expandir el panel.|  
|[CPane::GetAvailableStretchSize](#getavailablestretchsize)|Devuelve la cantidad, en píxeles, que puede reducir el panel.|  
|[CPane::GetBorders](#getborders)|Devuelve el ancho de los bordes del panel.|  
|[CPane::GetClientHotSpot](#getclienthotspot)|Devuelve el *zona activa* para el panel.|  
|[CPane::GetDockSiteRow](#getdocksiterow)|Devuelve la fila de acoplamiento en la que el panel está acoplado.|  
|[CPane::GetExclusiveRowMode](#getexclusiverowmode)|Determina si el panel está en modo de fila exclusivos.|  
|[CPane::GetHotSpot](#gethotspot)|Devuelve la zona activa que se almacena en una subyacente `CMFCDragFrameImpl` objeto.|  
|[CPane::GetMinSize](#getminsize)|Recupera el mínimo tamaño permitido para el panel.|  
|[CPane::GetPaneName](#getpanename)|Recupera el título para el panel.|  
|`CPane::GetResizeStep`|Se utiliza internamente.|  
|`CPane::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CPane::GetVirtualRect](#getvirtualrect)|Recupera el *rectángulo virtual* del panel.|  
|[CPane::IsChangeState](#ischangestate)|Tal y como se mueve el panel, este método analiza la posición del panel en relación con otros paneles, acoplar filas y ventanas de marco reducido y devuelve el apropiado `AFX_CS_STATUS` valor.|  
|[CPane::IsDragMode](#isdragmode)|Especifica si se arrastra el panel.|  
|[CPane::IsInFloatingMultiPaneFrameWnd](#isinfloatingmultipaneframewnd)|Especifica si el panel está en una ventana de marco de varios paneles. (Invalida `CBasePane::IsInFloatingMultiPaneFrameWnd`).|  
|[CPane::IsLeftOf](#isleftof)|Determina si se deja el panel de (o superior) del rectángulo especificado.|  
|[CPane::IsResizable](#isresizable)|Determina si el panel puede cambiarse. (Invalida [cbasepane:: isResizable](../../mfc/reference/cbasepane-class.md#isresizable).)|  
|[CPane::IsTabbed](#istabbed)|Determina si el panel se ha insertado en el control de pestaña de una ventana con pestañas. (Invalida [CBasePane::IsTabbed](../../mfc/reference/cbasepane-class.md#istabbed).)|  
|[CPane::LoadState](#loadstate)|Carga el estado del panel desde el registro. (Invalida [CBasePane::LoadState](../../mfc/reference/cbasepane-class.md#loadstate).)|  
|[CPane::MoveByAlignment](#movebyalignment)|Mueve el panel y el rectángulo virtual en la cantidad especificada.|  
|[CPane::MovePane](#movepane)|Mueve el panel en el rectángulo especificado.|  
|[CPane::OnAfterChangeParent](#onafterchangeparent)|Lo llama el marco de trabajo cuando ha cambiado el elemento primario de un panel.|  
|[CPane::OnBeforeChangeParent](#onbeforechangeparent)|Lo llama el marco cuando el elemento primario del panel se va a cambiar.|  
|[CPane::OnPressCloseButton](#onpressclosebutton)|Lo llama el marco cuando el usuario elige el botón de cierre en el título del panel.|  
|`CPane::OnProcessDblClk`|Se utiliza internamente.|  
|[CPANE:: Onshowcontrolbarmenu](#onshowcontrolbarmenu)|Lo llama el marco de trabajo cuando está a punto de mostrarse un menú de panel especial.|  
|[CPANE:: Onshowcontrolbarmenu](#onshowcontrolbarmenu)|Lo llama el marco de trabajo cuando está a punto de mostrarse un menú de panel especial.|  
|`CPane::PrepareToDock`|Se utiliza internamente.|  
|[CPANE:: RecalcLayout](#recalclayout)|Recalcula la información de diseño para el panel. (Invalida [CBasePane::RecalcLayout](../../mfc/reference/cbasepane-class.md#recalclayout).)|  
|[CPane::SaveState](#savestate)|Guarda el estado del panel en el registro. (Invalida [CBasePane::SaveState](../../mfc/reference/cbasepane-class.md#savestate).)|  
|[CPANE:: Setactiveingroup](#setactiveingroup)|Marca un panel como activa.|  
|[CPane::SetBorders](#setborders)|Establece los valores de borde del panel.|  
|[CPane::SetClientHotSpot](#setclienthotspot)|Establece la zona activa para el panel.|  
|[CPane::SetDockState](#setdockstate)|Restauraciones de información de estado para el panel de acoplamiento.|  
|[CPane::SetExclusiveRowMode](#setexclusiverowmode)|Habilita o deshabilita el modo de fila exclusivos.|  
|[CPane::SetMiniFrameRTC](#setminiframertc)|Establece la información de clase en tiempo de ejecución de la ventana de marco reducido predeterminada.|  
|[CPane::SetMinSize](#setminsize)|Establece el mínimo tamaño permitido para el panel.|  
|[CPane::SetVirtualRect](#setvirtualrect)|Establece el *rectángulo virtual* del panel.|  
|[CPane::StretchPaneDeferWndPos](#stretchpanedeferwndpos)|Expande el panel vertical u horizontalmente en función de estilo de acoplamiento.|  
|[CPane::ToggleAutoHide](#toggleautohide)|Alternar modo de ocultación automática.|  
|[CPane::UndockPane](#undockpane)|Quita el panel desde el sitio de vinculación, control deslizante de manera predeterminada o ventana de marco reducido que actualmente está acoplada. (Invalida [CBasePane::UndockPane](../../mfc/reference/cbasepane-class.md#undockpane).)|  
|[CPane::UpdateVirtualRect](#updatevirtualrect)|Actualiza el rectángulo virtual.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPane::OnAfterDock](#onafterdock)|Llamado por el marco de trabajo cuando se han acoplado un panel.|  
|[CPane::OnAfterFloat](#onafterfloat)|Lo llama el marco cuando queda flotando un panel.|  
|[CPane::OnBeforeDock](#onbeforedock)|Lo llama el marco cuando el panel está a punto de acoplarse.|  
|[CPane::OnBeforeFloat](#onbeforefloat)|Lo llama el marco cuando un panel se va a flotar.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPane::m_bHandleMinSize](#m_bhandleminsize)|Habilita el control coherente del tamaño mínimo de los paneles.|  
|[CPANE:: M_recentdockinfo](#m_recentdockinfo)|Contiene información de acoplamiento reciente.|  
  
## <a name="remarks"></a>Comentarios  
 Por lo general, `CPane` objetos no crear instancias directamente. Si necesita un panel que dispone de funcionalidad de acoplamiento, derive su objeto de [CDockablePane](../../mfc/reference/cdockablepane-class.md). Si necesita funcionalidad de la barra de herramientas, derive su objeto de [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md).  
  
 Al derivar una clase de `CPane`, se puede acoplar en un [CDockSite](../../mfc/reference/cdocksite-class.md) y lo puede flotar en un [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxPane.h  
  
##  <a name="adjustsizeimmediate"></a>CPane::AdjustSizeImmediate  
 Inmediatamente, vuelve a calcular el diseño de un panel.  
  
```  
virtual void AdjustSizeImmediate(BOOL bRecalcLayout = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bRecalcLayout`  
 `TRUE`Para volver a calcular automáticamente el diseño del panel; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método cuando se cambia dinámicamente el diseño de un panel. Por ejemplo, puede llamar a este método cuando ocultar o mostrar botones de barra de herramientas.  
  
##  <a name="allocelements"></a>CPane::AllocElements  
 Asigna almacenamiento para uso interno.  
  
```  
BOOL AllocElements(
    int nElements,  
    int cbElement);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nElements`  
 El número de elementos para los que se va a asignar el almacenamiento.  
  
 [in] `cbElement`  
 El tamaño, en bytes, de un elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 `FALSE`Si se produce un error en la asignación de memoria; en caso contrario, `TRUE`.  
  
##  <a name="allowshowonpanemenu"></a>CPane::AllowShowOnPaneMenu  
 Especifica si el panel se muestra en la lista generada en tiempo de ejecución de los paneles de la aplicación.  
  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se muestra en la lista; en caso contrario, `FALSE`. La implementación base siempre devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 La aplicación generada por el Asistente contiene una opción de menú que aparecen los paneles que lo contiene. Este método determina si el panel se muestra en la lista.  
  
##  <a name="calcavailablesize"></a>CPane::CalcAvailableSize  
 Calcula la diferencia de tamaño entre un rectángulo especificado y el rectángulo de la ventana actual.  
  
```  
virtual CSize CalcAvailableSize(CRect rectRequired);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectRequired`  
 El rectángulo necesario.  
  
### <a name="return-value"></a>Valor devuelto  
 La diferencia de ancho y alto entre `rectRequired` y el rectángulo de la ventana actual.  
  
##  <a name="calcinsiderect"></a>CPane::CalcInsideRect  
 Calcula el interior del rectángulo de un panel, incluidos los bordes y las barras de redimensionamiento.  
  
```  
void CalcInsideRect(
    CRect& rect,  
    BOOL bHorz) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `rect`  
 Contiene el tamaño y el desplazamiento del área cliente del panel.  
  
 [in] `bHorz`  
 `TRUE`Si el panel se orienta horizontalmente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando tiene que volver a calcular el diseño de un panel. El `rect` parámetro se rellena con el tamaño y el desplazamiento del área cliente del panel. Esto incluye sus bordes y las barras de redimensionamiento.  
  
##  <a name="calcrecentdockedrect"></a>CPane::CalcRecentDockedRect  
 Calcula el rectángulo recientemente acoplado.  
  
```  
void CalcRecentDockedRect();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método actualiza [CPANE:: M_recentdockinfo](#m_recentdockinfo).  
  
##  <a name="calcsize"></a>CPane::CalcSize  
 Calcula el tamaño del panel.  
  
```  
virtual CSize CalcSize(BOOL bVertDock);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bVertDock`  
 `TRUE`Si el panel que se está acoplado verticalmente, `FALSE` en caso contrario.  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada de este método devuelve un tamaño de (0, 0).  
  
### <a name="remarks"></a>Comentarios  
 Las clases derivadas deben invalidar este método.  
  
##  <a name="canbedocked"></a>CPane::CanBeDocked  
 Determina si se puede acoplar el panel en el panel de base especificado.  
  
```  
virtual BOOL CanBeDocked(CBasePane* pDockBar) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDockBar`  
 Especifica el panel que este panel está acoplada.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este panel se puede acoplar en el panel de acoplamiento especificado; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente se llama a este método por el marco de trabajo para determinar si se puede acoplar un panel en el panel de acoplamiento especificado. Para determinar si se puede acoplar el panel, el método se evalúa como el panel actualmente habilitado alineación de acoplamiento.  
  
 Habilitar a los distintos lados de la ventana de marco de acoplamiento mediante una llamada a [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).  
  
##  <a name="canbetabbeddocument"></a>CPane::CanBeTabbedDocument  
 Determina si el panel se puede convertir a un documento con pestañas.  
  
```  
virtual BOOL CanBeTabbedDocument() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se puede convertir en un documento con pestañas; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada y devolver `FALSE` si desea impedir que un panel que se va a convertir en un documento con pestañas. No se incluirá un documento con pestañas en el menú de la posición de la ventana.  
  
##  <a name="converttotabbeddocument"></a>CPane::ConvertToTabbedDocument  
 Convierte un panel acoplable en un documento con pestañas.  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bActiveTabOnly`  
 No se usa en `CPane::ConvertToTabbedDocument`.  
  
### <a name="remarks"></a>Comentarios  
 Paneles acoplables solo se pueden convertir en documentos con fichas. Para obtener información, consulte [CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).  
  
##  <a name="copystate"></a>CPane::CopyState  
 Copia el estado de un panel.  
  
```  
virtual void CopyState(CPane* pOrgBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pOrgBar`  
 Un puntero a un panel.  
  
### <a name="remarks"></a>Comentarios  
 Este método copia el estado de `pOrgBar` al panel actual.  
  
##  <a name="create"></a>CPANE:: Create  
 Crea una barra de control y lo adjunta a la [CPane](../../mfc/reference/cpane-class.md) objeto.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    DWORD dwControlBarStyle = AFX_DEFAULT_PANE_STYLE,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszClassName`  
 Especifica el nombre de la clase de Windows.  
  
 [in] `dwStyle`  
 Especifica los atributos de estilo de ventana. Para obtener más información, consulte [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in] `rect`  
 Especifica el tamaño inicial y la posición de la `pParentWnd` ventana, en coordenadas de cliente.  
  
 [in] [out]`pParentWnd`  
 Especifica la ventana primaria de este panel.  
  
 [in] `nID`  
 Especifica el identificador del panel.  
  
 [in] `dwControlBarStyle`  
 Especifica el estilo para el panel. Para obtener más información, consulte [cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
 [in] [out]`pContext`  
 Especifica el contexto de creación del panel.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se creó correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método crea un panel de Windows y lo adjunta a la `CPane` objeto.  
  
 Si no ha inicializado explícitamente [CPANE:: M_recentdockinfo](#m_recentdockinfo) antes de llamar a `Create`, el parámetro `rect` se usará como el rectángulo cuando flotante o acoplar el panel.  
  
##  <a name="createdefaultminiframe"></a>Createdefaultminiframe  
 Crea una ventana de marco reducido para un panel flotante.  
  
```  
virtual CPaneFrameWnd* CreateDefaultMiniframe(CRect rectInitial);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectInitial`  
 Especifica el tamaño inicial y la posición, en coordenadas de pantalla de la ventana de marco reducido a crear.  
  
### <a name="return-value"></a>Valor devuelto  
 La ventana de marco reducido recién creado.  
  
### <a name="remarks"></a>Comentarios  
 Se llama a este método por el marco de trabajo para crear una ventana de marco reducido cuando un panel está flotando. La ventana de marco reducido puede ser de tipo [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) o de tipo [CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md). Se crea una ventana de marco reducido de múltiples si el panel tiene la `AFX_CBRS_FLOAT_MULTI` estilo.  
  
 La información de clase en tiempo de ejecución de la ventana de marco reducido se almacena en la `CPane::m_pMiniFrameRTC` miembro. Puede usar una clase derivada para establecer a este miembro si decide crear ventanas de marco reducido personalizada.  
  
##  <a name="createex"></a>CPANE:: CreateEx  
 Crea una barra de control y lo adjunta a la [CPane](../../mfc/reference/cpane-class.md) objeto.  
  
```  
virtual BOOL CreateEx(
    DWORD dwStyleEx,  
    LPCTSTR lpszClassName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    DWORD dwControlBarStyle = AFX_DEFAULT_PANE_STYLE,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwStyleEx`  
 Especifica los atributos de estilo de ventana extendidos. Para obtener más información, consulte [estilos de ventana extendidos](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).  
  
 [in] `lpszClassName`  
 Especifica el nombre de la clase de Windows.  
  
 [in] `dwStyle`  
 Especifica los atributos de estilo de ventana. Para obtener más información, consulte [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in] `rect`  
 Especifica el tamaño inicial y la posición de la `pParentWnd` ventana, en coordenadas de cliente.  
  
 [in] [out]`pParentWnd`  
 Especifica la ventana primaria de este panel.  
  
 [in] `nID`  
 Especifica el identificador del panel.  
  
 [in] `dwControlBarStyle`  
 Especifica el estilo para el panel. Para obtener más información, consulte [cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
 [in] [out]`pContext`  
 Especifica el contexto de creación para el panel.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se creó correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método crea un panel de Windows y lo adjunta a la `CPane` objeto.  
  
 Si no ha inicializado explícitamente [CPANE:: M_recentdockinfo](#m_recentdockinfo) antes de llamar a `CreateEx`, el parámetro `rect` se usará como el rectángulo cuando flotante o acoplar el panel.  
  
##  <a name="dockbymouse"></a>CPane::DockByMouse  
 Acopla un panel con el mouse.  
  
```  
virtual BOOL DockByMouse(CBasePane* pDockBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDockBar`  
 Especifica el panel de base que se va a acoplar este panel.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se acopla correctamente; en caso contrario, `FALSE`.  
  
##  <a name="dockpane"></a>CPane::DockPane  
 Acopla el panel flotante a un panel de base.  
  
```  
virtual BOOL DockPane(
    CBasePane* pDockBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`pDockBar`  
 Especifica el panel para acoplar este panel para base.  
  
 [in] `lpRect`  
 Especifica el rectángulo en el panel base donde este panel está acoplada.  
  
 [in] `dockMethod`  
 Especifica el método de acoplamiento para usar. Opciones disponibles son los siguientes:  
  
|Opción|Descripción|  
|------------|-----------------|  
|`DM_UNKNOWN`|El marco de trabajo usa esta opción cuando el método de acoplamiento es desconocido. El panel no almacena su posición flotante más reciente. También puede usar esta opción para acoplar mediante programación un panel cuando no tiene que almacenar la posición de punto flotante recientes.|  
|`DM_MOUSE`|Se utiliza internamente.|  
|`DM_DBL_CLICK`|Esta opción se utiliza cuando se hace doble clic en la barra de redimensionamiento. El panel se vuelve a colocar en su posición de acoplamiento más reciente. Si el panel está desacoplado haciendo doble clic en, el panel se vuelve a colocar en su posición flotante más reciente.|  
|`DM_SHOW`|Esta opción puede utilizarse para acoplar el panel de mediante programación. El panel almacena su posición flotante más reciente.|  
|`DM_RECT`|El panel está acoplado en la región que se especifica mediante `lpRect`.|  
|`DM_STANDARD`|Cuando se usa esta opción, el marco de trabajo dibuja el panel como un marco de esquema mientras se esté moviendo.|  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se acopla correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método acopla el panel en el panel base especificado por el `pDockBar` parámetro. Primero debe habilitar acoplamiento mediante una llamada a [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).  
  
##  <a name="dockpanestandard"></a>CPane::DockPaneStandard  
 Acopla un panel mediante el uso de esquema de acoplamiento (estándar).  
  
```  
virtual CPane* DockPaneStandard(BOOL& bWasDocked);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bWasDocked`  
 `TRUE`Si el panel se acopla correctamente; en caso contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 Este método devuelve siempre el `this` puntero.  
  
### <a name="remarks"></a>Comentarios  
 Este método se usa solo para los paneles que se derivan de la [clase CDockablePane](../../mfc/reference/cdockablepane-class.md). Para obtener más información, consulte [CDockablePane::DockPaneStandard](../../mfc/reference/cdockablepane-class.md#dockpanestandard).  
  
##  <a name="docktoframewindow"></a>CPane::DockToFrameWindow  
 Acopla un panel acoplable a un marco.  
  
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
 El lado del marco principal que desea acoplar el panel a.  
  
 [in] `lpRect`  
 El tamaño especificado.  
  
 [in] `dwDockFlags`  
 ignorado.  
  
 [in] `pRelativeBar`  
 ignorado.  
  
 [in] `nRelativeIndex`  
 ignorado.  
  
 [in] `bOuterEdge`  
 Si `TRUE` y hay otros paneles acoplables en el lado que se especifican mediante `dwAlignment`, el panel está acoplado fuera de los otros paneles, cuanto más se acerque al borde del marco primario. Si `FALSE`, el panel está acoplado cuando se acerque al centro del área de cliente.  
  
### <a name="return-value"></a>Valor devuelto  
 `FALSE`Si un panel divisor ( [CPaneDivider clase](../../mfc/reference/cpanedivider-class.md)) no se puede crear; en caso contrario, `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="doesallowsiblingbars"></a>CPane::DoesAllowSiblingBars  
 Indica si se puede acoplar el panel de otro en la misma fila en el panel actual está acoplado.  
  
```  
virtual BOOL DoesAllowSiblingBars() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este panel se puede acoplar a otro panel en la misma fila por sí misma; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Puede habilitar o deshabilitar este comportamiento mediante una llamada a [CPane::SetExclusiveRowMode](#setexclusiverowmode).  
  
 De forma predeterminada, las barras de herramientas tienen deshabilitado el modo exclusivos de fila y la barra de menús tiene habilitado el modo de fila exclusivos.  
  
##  <a name="floatpane"></a>CPane::FloatPane  
 Desplaza el panel.  
  
```  
virtual BOOL FloatPane(
    CRect rectFloat,  
    AFX_DOCK_METHOD dockMethod = DM_UNKNOWN,  
    bool bShow = true);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectFloat`  
 Especifica la ubicación, en coordenadas de pantalla, para colocar el panel cuando se está flotando.  
  
 [in] `dockMethod`  
 Especifica el método de acoplamiento que se usará cuando el panel está flotando. Para obtener una lista de valores posibles, consulte [CPane::DockPane](#dockpane).  
  
 [in] `bShow`  
 `TRUE`para mostrar el panel cuando flota; en caso contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se flota correctamente o si el panel no puede flotar porque [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat) devuelve `FALSE`; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para hacer flotar el panel en la posición especificada por el `rectFloat` parámetro. Este método crea automáticamente una ventana de marco reducido primaria para el panel.  
  
##  <a name="getavailableexpandsize"></a>CPane::GetAvailableExpandSize  
 Devuelve la cantidad, en píxeles, que se pueda expandir el panel.  
  
```  
virtual int GetAvailableExpandSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si el panel está acoplado horizontalmente, el valor devuelto es el ancho disponible; en caso contrario, el valor devuelto es el alto disponible.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getavailablestretchsize"></a>CPane::GetAvailableStretchSize  
 Devuelve la cantidad, en píxeles, que puede reducir el panel.  
  
```  
virtual int GetAvailableStretchSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La cantidad, en píxeles, que puede reducir el panel. Si el panel está acoplado horizontalmente, esta cantidad es el ancho disponible; en caso contrario, es el alto disponible.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de stretch disponible se calcula restando el mínimo tamaño permitido para el panel ( [CPane::GetMinSize](#getminsize)) desde el tamaño actual ( [CWnd::GetWindowRect](../../mfc/reference/cwnd-class.md#getwindowrect)).  
  
##  <a name="getborders"></a>CPane::GetBorders  
 Devuelve el ancho de los bordes del panel.  
  
```  
CRect GetBorders() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que contiene el ancho actual, en píxeles, de cada lado del panel. Por ejemplo, el valor de la `left` miembro de la `CRect` objeto es el ancho del borde izquierdo.  
  
### <a name="remarks"></a>Comentarios  
 Para establecer el tamaño de los bordes, llame a [CPane::SetBorders](#setborders).  
  
##  <a name="getclienthotspot"></a>CPane::GetClientHotSpot  
 Devuelve el *zona activa* para el panel.  
  
```  
CPoint GetClientHotSpot() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 El *zona activa* es el punto en el panel de que el usuario selecciona y mantiene para mover el panel. Una zona activa se usa para animación suave cuando se mueve el panel de una posición acoplada.  
  
##  <a name="getdocksiterow"></a>CPane::GetDockSiteRow  
 Devuelve la fila de acoplamiento ( [CDockingPanesRow clase](../../mfc/reference/cdockingpanesrow-class.md)) en que el panel está acoplado.  
  
```  
CDockingPanesRow* GetDockSiteRow() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 A `CDockingPanesRow`* que apunta a la fila de acoplamiento en la que el panel está acoplado, o `NULL` si el panel no está acoplado.  
  
##  <a name="getexclusiverowmode"></a>CPane::GetExclusiveRowMode  
 Determina si el panel está en modo de fila exclusivos.  
  
```  
virtual BOOL GetExclusiveRowMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel está en modo de fila exclusivos; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca del modo de exclusivos de fila, vea [CPane::SetExclusiveRowMode](#setexclusiverowmode).  
  
##  <a name="gethotspot"></a>CPane::GetHotSpot  
 Devuelve la zona activa que se almacena en una subyacente `CMFCDragFrameImpl` objeto.  
  
```  
CPoint GetHotSpot() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 El `CPane` clase contiene un `CMFCDragFrameImpl` objeto, `m_dragFrameImpl`, que es responsable de dibujar el rectángulo que aparece cuando el usuario mueve un panel en el modo de acoplamiento estándar. La zona activa se usa para dibujar el rectángulo en relación con la actual posición del mouse cuando el usuario mueve el panel.  
  
##  <a name="getminsize"></a>CPane::GetMinSize  
 Recupera el mínimo tamaño permitido para el panel.  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `size`  
 Un `CSize` objeto que se rellena con el mínimo tamaño permitido.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getpanename"></a>CPane::GetPaneName  
 Recupera el título para el panel.  
  
```  
virtual void GetPaneName(CString& strName) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `strName`  
 Un `CString` objeto que se rellena con el nombre del título.  
  
### <a name="remarks"></a>Comentarios  
 El título del panel se muestra en el área de título cuando el panel está acoplado o flotante. Si el panel forma parte de un grupo con pestañas, el título se muestra en el área de pestañas. Si el panel está en modo de ocultación automática, el título se muestra en un `CMFCAutoHideButton`.  
  
##  <a name="getvirtualrect"></a>CPane::GetVirtualRect  
 Recupera el *rectángulo virtual* del panel.  
  
```  
void GetVirtualRect(CRect& rectVirtual) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `rectVirtual`  
 Un `CRect` objeto que se rellena con el rectángulo virtual.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se mueve un panel, el marco de trabajo almacena la posición original del panel en un rectángulo virtual. El marco de trabajo puede usar el rectángulo virtual para restaurar la posición original del panel.  
  
 No llame a métodos que están relacionados con rectángulos virtuales a menos que se va a mover paneles mediante programación.  
  
##  <a name="ischangestate"></a>CPane::IsChangeState  
 Tal y como se mueve el panel, este método analiza su posición en relación con otros paneles, acoplar filas y ventanas de marco reducido y devuelve el apropiado `AFX_CS_STATUS` valor.  
  
```  
virtual AFX_CS_STATUS IsChangeState(
    int nOffset,  
    CBasePane** ppTargetBar) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nOffset`  
 Especifica la distinción de acoplamiento. Por ejemplo, un panel que se mueve dentro de `nOffset` se acoplará píxeles desde una fila de acoplamiento.  
  
 [in] `ppTargetBar`  
 Cuando el método vuelve, `ppTargetBar` contiene ya sea un puntero al objeto al que se debe acoplar el panel actual, o `NULL` si no se debería ejecutar ningún proceso de acoplamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los siguientes valores de `AFX_CS_STATUS`:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`CS_NOTHING`|El panel no está cerca de un sitio de vinculación. El marco de trabajo no acoplar el panel.|  
|`CS_DOCK_IMMEDIATELY`|El panel está en un sitio de vinculación y `DT_IMMEDIATE` estilo está habilitado. El marco de trabajo acopla el panel inmediatamente.|  
|`CS_DELAY_DOCK`|El panel está en un sitio de vinculación que es otro panel acoplable o un borde del marco principal. El marco de trabajo acopla el panel cuando el usuario suelta el movimiento.|  
|`CS_DELAY_DOCK_TO_TAB`|El panel está en un sitio de vinculación que hace que el panel acoplada en una ventana con pestañas. Esto se produce cuando el panel está en el título de otro panel acoplable o sobre el área de la ficha de un panel con fichas. El marco de trabajo acopla el panel cuando el usuario suelta el movimiento.|  
  
##  <a name="isdragmode"></a>CPane::IsDragMode  
 Especifica si se va a mover el panel.  
  
```  
virtual BOOL IsDragMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se mueve el panel; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isinfloatingmultipaneframewnd"></a>CPane::IsInFloatingMultiPaneFrameWnd  
 Especifica si el panel está en una ventana de marco de varios paneles ( [CMultiPaneFrameWnd clase](../../mfc/reference/cmultipaneframewnd-class.md)).  
  
```  
virtual BOOL IsInFloatingMultiPaneFrameWnd() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel está en una ventana de marco de varios paneles; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Solo los paneles acoplables pueden flotar en una ventana de marco de varios paneles. Por lo tanto, `CPane::IsInFloatingMultiPaneFrameWnd` siempre devuelve `FALSE`.  
  
##  <a name="isleftof"></a>CPane::IsLeftOf  
 Determina si se deja el panel de (o superior) del rectángulo especificado.  
  
```  
bool IsLeftOf(
    CRect rect,  
    bool bWindowRect = true) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rect`  
 Un `CRect` objeto que se usa para la comparación.  
  
 [in] `bWindowRect`  
 Si `TRUE`, `rect` se supone que contienen las coordenadas de pantalla; si `FALSE`, `rect` se supone que contienen las coordenadas de cliente.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 Si el panel está acoplado horizontalmente, este método comprueba si su ubicación se deja de `rect`. En caso contrario, este método comprueba si la ubicación está por encima `rect`.  
  
##  <a name="isresizable"></a>CPane::IsResizable  
 Especifica si se puede cambiar el tamaño del panel.  
  
```  
virtual BOOL IsResizable() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se puede cambiar el tamaño; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Base `CPane` objetos no son de tamaño variable.  
  
 El Administrador de acoplamiento usa la marca puede cambiar el tamaño para determinar el diseño del panel. Paneles de tamaño variable no siempre se encuentran en los bordes exteriores de un marco primario.  
  
 Puede cambiar el tamaño no paneles no pueden residir en contenedores de acoplamiento.  
  
##  <a name="istabbed"></a>CPane::IsTabbed  
 Determina si el panel se ha insertado en el control de pestaña de una ventana con pestañas.  
  
```  
virtual BOOL IsTabbed() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se por pestañas; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El estado con pestañas se trata por separado de flotante, acopla y Estados de ocultación automática.  
  
##  <a name="loadstate"></a>CPane::LoadState  
 Carga el estado del panel desde el registro.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Nombre del perfil.  
  
 [in] `nIndex`  
 Índice de perfil.  
  
 [in] `uiID`  
 Id. de panel.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el estado del panel se cargó correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para cargar el estado del panel desde el registro. Invalidar en una clase derivada para cargar información adicional que se guarda de forma [CPane::SaveState](#savestate).  
  
 Cuando se reemplaza este método, también llama al método base y devolver `FALSE` si el método base devuelve `FALSE`.  
  
##  <a name="m_bhandleminsize"></a>CPane::m_bHandleMinSize  
 Habilita el control coherente de tamaños mínimo del panel.  
  
```  
AFX_IMPORT_DATA static BOOL m_bHandleMinSize;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si uno o más paneles de acoplamiento en la aplicación invalidación `GetMinSize`, o si la aplicación llama a `SetMinSize`, puede que desee establecer este miembro estático en `TRUE` para permitir que el marco de forma coherente controlar cómo se cambia el tamaño de los paneles.  
  
 Si este valor se establece en `TRUE`, cuyo tamaño se debería reducir por debajo de su tamaño mínimo de todos los paneles se recortan, no ajusta. Dado que el marco de trabajo utiliza regiones de ventana para fines de ajuste de tamaño del panel, no cambie el tamaño de la región de ventana para acoplar paneles si este valor se establece en `TRUE`.  
  
##  <a name="m_recentdockinfo"></a>CPANE:: M_recentdockinfo  
 Contiene información de acoplamiento reciente.  
  
```  
CRecentDockSiteInfo m_recentDockInfo;  
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo almacena la información de estado más reciente de acoplamiento para el panel en este miembro.  
  
##  <a name="movebyalignment"></a>CPane::MoveByAlignment  
 Mueve el panel y el rectángulo virtual en la cantidad especificada.  
  
```  
BOOL MoveByAlignment(
    DWORD dwAlignment,  
    int nOffset);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwAlignment`  
 Especifica la alineación del panel.  
  
 [in] `nOffset`  
 La cantidad, en píxeles, por el que se va a mover el panel y el rectángulo virtual.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 `dwAlignment`puede ser cualquiera de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`CBRS_ALIGN_TOP`|Permite que el panel se acopla a la parte superior del área cliente de una ventana de marco.|  
|`CBRS_ALIGN_BOTTOM`|Permite que el panel se acopla a la parte inferior del área de cliente de una ventana de marco.|  
|`CBRS_ALIGN_LEFT`|Permite que el panel se acopla a la izquierda del área cliente de una ventana de marco.|  
|`CBRS_ALIGN_RIGHT`|Permite que el panel se acopla a la derecha del área de cliente de una ventana de marco.|  
|`CBRS_ALIGN_ANY`|Permite que el panel para que se puede acoplar a cualquier lado del área cliente de una ventana de marco.|  
  
 Si `dwAlignment` contiene el `CBRS_ALIGN_LEFT` o `CBRS_ALIGN_RIGHT` marca, el panel y el rectángulo virtual se mueven horizontalmente; de lo contrario, si `dwAlignment` contiene el `CBRS_ALIGN_TOP` o `CBRS_ALIGN_BOTTOM` se mueven marca, el panel y el rectángulo virtual verticalmente.  
  
##  <a name="movepane"></a>CPane::MovePane  
 Mueve el panel en el rectángulo especificado.  
  
```  
virtual CSize MovePane(
    CRect rectNew,  
    BOOL bForceMove,  
    HDWP& hdwp);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectNew`  
 Especifica el nuevo rectángulo para el panel.  
  
 [in] `bForceMove`  
 Si `TRUE`, este método pasa por alto el tamaño mínimo permitido del panel ( [CPane::GetMinSize](#getminsize)); en caso contrario, se ajusta el panel, si es necesario, para asegurarse de que al menos el mínimo tamaño permitido.  
  
 [in] `hdwp`  
 No usado.  
  
### <a name="return-value"></a>Valor devuelto  
 A `CSize` objeto que contiene las diferencias de ancho y alto entre los rectángulos nuevos y antiguos (rectángulo anterior - `rectNew`).  
  
### <a name="remarks"></a>Comentarios  
 Este método se usa solo para paneles acoplables.  
  
##  <a name="onafterchangeparent"></a>CPane::OnAfterChangeParent  
 Lo llama el marco de trabajo cuando ha cambiado el elemento primario de un panel.  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`pWndOldParent`  
 Ventana principal de la anterior del panel.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando el elemento primario de un panel ha cambiado debido a una operación de acoplamiento o de punto flotante.  
  
##  <a name="onafterdock"></a>CPane::OnAfterDock  
 Llamado por el marco de trabajo cuando se han acoplado un panel.  
  
```  
virtual void OnAfterDock(
    CBasePane* pBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Este parámetro no se utiliza.  
  
 [in] `lpRect`  
 Este parámetro no se utiliza.  
  
 [in] `dockMethod`  
 Este parámetro no se utiliza.  
  
##  <a name="onafterfloat"></a>CPane::OnAfterFloat  
 Llamado por el marco de trabajo cuando se desplaza de un panel.  
  
```  
virtual void OnAfterFloat();
```  
  
### <a name="remarks"></a>Comentarios  
 Puede invalidar este método en una clase derivada si desea realizar cualquier procesamiento después de un panel flota.  
  
##  <a name="onbeforechangeparent"></a>CPane::OnBeforeChangeParent  
 Lo llama el marco cuando el elemento primario del panel se va a cambiar.  
  
```  
virtual void OnBeforeChangeParent(
    CWnd* pWndNewParent,  
    BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`pWndNewParent`  
 Especifica la nueva ventana primaria.  
  
 [in] `bDelay`  
 `TRUE`Para retrasar el ajuste del diseño de acoplamiento global; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando el elemento primario del panel se va a cambiar porque se está el panel acoplado o flota.  
  
 De forma predeterminada, el panel está registrado con el panel de acoplamiento mediante una llamada a `CDockSite::RemovePane`.  
  
##  <a name="onbeforedock"></a>CPane::OnBeforeDock  
 Lo llama el marco cuando el panel se va a acoplar.  
  
```  
virtual BOOL OnBeforeDock(
    CBasePane** ppDockBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`ppDockBar`  
 Especifica el panel de acoplamiento a este panel.  
  
 [in] `lpRect`  
 Especifica el rectángulo de acoplamiento.  
  
 [in] `dockMethod`  
 Especifica el método de acoplamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se puede acoplar el panel. Si la función devuelve `FALSE`, se anulará la operación de acoplamiento.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando un panel está a punto de acoplarse. Puede invalidar este método en una clase derivada si desea realizar cualquier procesamiento antes de que finalmente se acopla un panel.  
  
##  <a name="onbeforefloat"></a>CPane::OnBeforeFloat  
 Lo llama el marco cuando un panel se acerca a float.  
  
```  
virtual BOOL OnBeforeFloat(
    CRect& rectFloat,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectFloat`  
 Especifica la posición y el tamaño del panel cuando se encuentra en un estado flotante.  
  
 [in] `dockMethod`  
 Especifica el método de acoplamiento del panel.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel puede flotar; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando un panel se acerca a float. Puede invalidar este método en una clase derivada si desea realizar cualquier procesamiento antes de que el panel finalmente flota.  
  
##  <a name="onpressclosebutton"></a>CPane::OnPressCloseButton  
 Lo llama el marco cuando el usuario presiona el botón de cierre en el título del panel.  
  
```  
virtual void OnPressCloseButton();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando el usuario presiona el **cerrar** botón de título del panel. Para recibir notificaciones sobre el **cerrar** eventos, puede invalidar este método en una clase derivada.  
  
##  <a name="onshowcontrolbarmenu"></a>CPANE:: Onshowcontrolbarmenu  
 Lo llama el marco de trabajo cuando está a punto de mostrarse un menú de panel especial.  
  
```  
virtual BOOL OnShowControlBarMenu(CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 Especifica la ubicación del menú.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se puede mostrar el menú; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El menú contiene varios elementos que le permiten especificar el comportamiento del panel, a saber: **flotante**, **acoplamiento**, **Ocultar automáticamente**, y **ocultar**. Puede habilitar este menú para todos los paneles mediante una llamada a [CDockingManager::EnableDockSiteMenu](../../mfc/reference/cdockingmanager-class.md#enabledocksitemenu).  
  
##  <a name="recalclayout"></a>CPANE:: RecalcLayout  
 Recalcula la información de diseño para el panel.  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>Comentarios  
 Si el panel está acoplado, este método actualiza el rectángulo virtual para el panel estableciendo su tamaño en el tamaño actual del panel.  
  
 Si el panel está flotando, este método notifica el marco primario a mínima para ajustar el tamaño del panel para el tamaño de marco reducido. El marco de trabajo se asegura de que el marco reducido es al menos el mínimo tamaño permitido para el panel ( [CPane::GetMinSize](#getminsize)) y cambia el tamaño de marco reducido si es necesario.  
  
##  <a name="savestate"></a>CPane::SaveState  
 Guarda el estado del panel en el registro.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Nombre del perfil.  
  
 [in] `nIndex`  
 Índice de perfil.  
  
 [in] `uiID`  
 Id. de panel.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el estado se guardó correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando guarda el estado del panel en el registro. Invalidar `SaveState` en una clase derivada para almacenar información adicional.  
  
 Cuando se reemplaza este método, también llama al método base y devolver `FALSE` si el método base devuelve `FALSE`.  
  
##  <a name="setactiveingroup"></a>CPANE:: Setactiveingroup  
 Marca un panel como activa.  
  
```  
virtual void SetActiveInGroup(BOOL bActive);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bActive`  
 Un `BOOL` que especifica si el panel se marca como activa.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se muestra un panel acoplable o se elige un botón de ocultación automática, el panel de ocultación automática correspondiente se marca como activo.  
  
 La apariencia de un botón de ocultación automática que está asociado con el panel se basa en dos factores. Si el panel está activo y la `static BOOL CMFCAutoHideButton::m_bOverlappingTabs` es `TRUE`, el marco de trabajo muestra el botón de ocultación automática como un icono y una etiqueta. Para un panel inactivo, el marco de trabajo muestra sólo el icono de ocultación automática.  
  
 Si `CMFCAutoHideButton::m_bOverlappingTabs` es `FALSE`, o si el panel no se encuentra en un grupo, el marco de trabajo muestra el botón de ocultación automática asociado como un icono y una etiqueta.  
  
##  <a name="setborders"></a>CPane::SetBorders  
 Establece los valores de borde del panel.  
  
```  
void SetBorders(
    int cxLeft = 0,  
    int cyTop = 0,  
    int cxRight = 0,  
    int cyBottom = 0);  
  
void SetBorders(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `cxLeft`  
 Especifica el ancho, en píxeles, del borde izquierdo del panel.  
  
 [in] `cyTop`  
 Especifica el ancho, en píxeles, del borde superior del panel.  
  
 [in] `cxRight`  
 Especifica el ancho, en píxeles, del borde derecho del panel.  
  
 [in] `cyBottom`  
 Especifica el ancho, en píxeles, del borde inferior del panel.  
  
 [in] `lpRect`  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que contiene el ancho, en píxeles, de cada borde del panel.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para establecer los tamaños de los bordes del panel.  
  
##  <a name="setclienthotspot"></a>CPane::SetClientHotSpot  
 Establece el *zona activa* para el panel.  
  
```  
void SetClientHotSpot(const CPoint& ptNew);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `ptNew`  
 Un `CPoint` objeto que especifica la nueva zona activa.  
  
### <a name="remarks"></a>Comentarios  
 El *zona activa* es el punto en el panel de que el usuario selecciona y mantiene para mover el panel. Una zona activa se usa para animación suave cuando se arrastra el panel de una posición acoplada.  
  
##  <a name="setdockstate"></a>CPane::SetDockState  
 Restauraciones de información de estado para el panel de acoplamiento.  
  
```  
virtual void SetDockState(CDockingManager* pDockManager);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDockManager`  
 Puntero para el Administrador de acoplamiento para la ventana de marco principal.  
  
### <a name="remarks"></a>Comentarios  
 Se llama a este método por el marco de trabajo para restaurar la información de estado de acoplamiento reciente para el panel. Un panel almacena la información de estado de acoplamiento reciente en [CPANE:: M_recentdockinfo](#m_recentdockinfo). Para obtener más información, consulte el [CRecentDockSiteInfo clase](../../mfc/reference/crecentdocksiteinfo-class.md).  
  
 También puede llamar a este método para establecer el estado de acoplamiento cuando se carga la información del panel desde un origen externo.  
  
##  <a name="setexclusiverowmode"></a>CPane::SetExclusiveRowMode  
 Habilita o deshabilita el modo de fila exclusivos.  
  
```  
virtual void SetExclusiveRowMode(BOOL bExclusive = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bExclusive`  
 `TRUE`Para habilitar el modo de fila exclusivos; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para habilitar o deshabilitar el modo de fila exclusivos. Cuando un panel está en modo de fila exclusivos, lo no puede compartir la misma fila con otras barras de herramientas.  
  
 De forma predeterminada, todas las barras de herramientas tienen deshabilitado el modo exclusivos de fila y la barra de menús tiene habilitado el modo de fila exclusivos.  
  
##  <a name="setminsize"></a>CPane::SetMinSize  
 Establece el mínimo tamaño permitido para el panel.  
  
```  
void SetMinSize(const CSize& size);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `size`  
 Un `CSize` objeto que contiene el mínimo tamaño permitido para el panel.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setvirtualrect"></a>CPane::SetVirtualRect  
 Establece el *rectángulo virtual* del panel.  
  
```  
void SetVirtualRect(
    const CRect& rect,  
    BOOL bMapToParent = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rect`  
 Un `CRect` objeto que especifica el rectángulo virtual establecerse.  
  
 [in] `bMapToParent`  
 Especifique `TRUE` si `rect` contiene puntos con relación a la ventana primaria.  
  
### <a name="remarks"></a>Comentarios  
 A *rectángulo virtual* almacena la posición original de un panel cuando se mueven. El marco de trabajo puede usar el rectángulo virtual para restaurar la posición original.  
  
 No llame a métodos que están relacionados con rectángulos virtuales a menos que se va a mover paneles mediante programación.  
  
##  <a name="setminiframertc"></a>CPane::SetMiniFrameRTC  
 Establece la información de clase en tiempo de ejecución de la ventana de marco reducido predeterminada.  
  
```  
void SetMiniFrameRTC(CRuntimeClass* pClass);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`pClass`  
 Especifica la información de clase en tiempo de ejecución de la ventana de marco reducido.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un panel está flotando, se coloca en un [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) ventana (minimarco). Puede proporcionar un personalizado `CPaneFrameWnd`-clase derivada que será utilizado al [Createdefaultminiframe](#createdefaultminiframe) se llama.  
  
##  <a name="stretchpanedeferwndpos"></a>CPane::StretchPaneDeferWndPos  
 Expande el panel vertical u horizontalmente en función de estilo de acoplamiento.  
  
```  
virtual int StretchPaneDeferWndPos(
    int nStretchSize,  
    HDWP& hdwp);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nStretchSize`  
 La cantidad, en píxeles, para expandir el panel. Use un valor negativo para reducir el panel.  
  
 [in] `hdwp`  
 No usado.  
  
### <a name="return-value"></a>Valor devuelto  
 La cantidad real, en píxeles, que se ajusta el panel.  
  
### <a name="remarks"></a>Comentarios  
 Si es necesario, este método modifica `nStretchSize` para asegurarse de que el panel no supera los límites de tamaño. Estos límites se obtienen mediante una llamada a [CPane::GetAvailableStretchSize](#getavailablestretchsize) y [CPane::GetAvailableExpandSize](#getavailableexpandsize).  
  
##  <a name="toggleautohide"></a>CPane::ToggleAutoHide  
 Alternar modo de ocultación automática.  
  
```  
virtual void ToggleAutoHide();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para alternar el modo de ocultación automática. Un panel debe acoplarse a una ventana de marco principal para ser conforme a cambiar a modo de ocultación automática.  
  
##  <a name="undockpane"></a>CPane::UndockPane  
 Quita el panel desde el sitio de vinculación, control deslizante de manera predeterminada o ventana de marco reducido que actualmente está acoplada.  
  
```  
virtual void UndockPane(BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bDelay`  
 Si `FALSE`, las llamadas de framework [cbasepane:: Adjustdockinglayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout) para ajustar el diseño de acoplamiento.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para desacoplar mediante programación un panel.  
  
##  <a name="updatevirtualrect"></a>CPane::UpdateVirtualRect  
 Actualiza el rectángulo virtual.  
  
```  
void UpdateVirtualRect();  
void UpdateVirtualRect(CPoint ptOffset);  
  void UpdateVirtualRect(CSize sizeNew);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `ptOffset`  
 Un `CPoint` objeto que especifica un desplazamiento de la que se va a desplazar el panel.  
  
 [in] `sizeNew`  
 Un `CSize` objeto que especifica un nuevo tamaño para el panel.  
  
### <a name="remarks"></a>Comentarios  
 La primera sobrecarga establece el rectángulo virtual mediante el uso de la posición actual y el tamaño del panel.  
  
 La segunda sobrecarga desplaza el rectángulo virtual en la cantidad especificada por `ptOffset`.  
  
 La tercera sobrecarga establece el rectángulo virtual mediante el uso de la posición actual del panel y el tamaño especificado por `sizeNew`.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CBasePane (clase)](../../mfc/reference/cbasepane-class.md)
