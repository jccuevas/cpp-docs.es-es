---
title: Clase CPane | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
dev_langs:
- C++
helpviewer_keywords:
- CPane class
ms.assetid: 5c651a64-3c79-4d94-9676-45f6402a6bc5
caps.latest.revision: 30
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
ms.openlocfilehash: 586133277aa4a9d89ca15cdd496a1ca7e4232632
ms.lasthandoff: 02/24/2017

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
|[CPane::AdjustSizeImmediate](#adjustsizeimmediate)|El diseño de un panel se actualiza inmediatamente.|  
|[CPane::AllocElements](#allocelements)|Asigna almacenamiento para uso interno.|  
|[CPane::AllowShowOnPaneMenu](#allowshowonpanemenu)|Especifica si el panel se muestra en la lista generada en tiempo de ejecución de los paneles de la aplicación.|  
|[CPane::CalcAvailableSize](#calcavailablesize)|Calcula la diferencia de tamaño entre un rectángulo especificado y el rectángulo de la ventana actual.|  
|[CPane::CalcInsideRect](#calcinsiderect)|Calcula el interior del rectángulo de un panel, teniendo en cuenta los bordes y las barras de redimensionamiento.|  
|[CPane::CalcRecentDockedRect](#calcrecentdockedrect)|Calcula el rectángulo recientemente acoplado.|  
|[CPane::CalcSize](#calcsize)|Calcula el tamaño del panel.|  
|[CPane::CanBeDocked](#canbedocked)|Determina si el panel se puede acoplar el panel de base especificado.|  
|[CPane::CanBeTabbedDocument](#canbetabbeddocument)|Determina si el panel puede convertirse en un documento con fichas.|  
|[CPane::ConvertToTabbedDocument](#converttotabbeddocument)|Convierte un panel acoplable en un documento con fichas.|  
|[CPane::CopyState](#copystate)|Copia el estado de un panel. (Invalida [CBasePane::CopyState](../../mfc/reference/cbasepane-class.md#copystate).)|  
|[CPane::Create](#create)|Crea una barra de control y lo adjunta a la `CPane` objeto.|  
|[CPane::CreateDefaultMiniframe](#createdefaultminiframe)|Crea una ventana de marco reducido para un panel flotante.|  
|[CPane::CreateEx](#createex)|Crea una barra de control y lo adjunta a la `CPane` objeto.|  
|`CPane::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|[CPane::DockByMouse](#dockbymouse)|Un panel se acopla con el mouse acoplamiento (método).|  
|[CPane::DockPane](#dockpane)|Acopla el panel flotante a un panel de base.|  
|[CPane::DockPaneStandard](#dockpanestandard)|Un panel se acopla utilizando el esquema de acoplamiento (estándar).|  
|[CPane::DockToFrameWindow](#docktoframewindow)|Un panel acoplable se acopla a un marco. (Invalida `CBasePane::DockToFrameWindow`).|  
|[CPane::DoesAllowSiblingBars](#doesallowsiblingbars)|Indica si se puede acoplar el panel de otro en la misma fila en el panel actual está acoplado.|  
|[CPane::FloatPane](#floatpane)|Desplaza el panel.|  
|[CPane::GetAvailableExpandSize](#getavailableexpandsize)|Devuelve la cantidad, en píxeles, que se puede expandir el panel.|  
|[CPane::GetAvailableStretchSize](#getavailablestretchsize)|Devuelve la cantidad, en píxeles, que puede reducir el tamaño del panel.|  
|[CPane::GetBorders](#getborders)|Devuelve el ancho de los bordes del panel.|  
|[CPane::GetClientHotSpot](#getclienthotspot)|Devuelve el *zona activa* para el panel.|  
|[CPane::GetDockSiteRow](#getdocksiterow)|Devuelve la fila de acoplamiento en la que el panel está acoplado.|  
|[CPane::GetExclusiveRowMode](#getexclusiverowmode)|Determina si el panel está en modo exclusivo de la fila.|  
|[CPane::GetHotSpot](#gethotspot)|Devuelve la zona activa que se almacena en una base de `CMFCDragFrameImpl` objeto.|  
|[CPane::GetMinSize](#getminsize)|Recupera el mínimo tamaño permitido para el panel.|  
|[CPane::GetPaneName](#getpanename)|Recupera el título del panel.|  
|`CPane::GetResizeStep`|Se utiliza internamente.|  
|`CPane::GetThisClass`|Usar el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CPane::GetVirtualRect](#getvirtualrect)|Recupera el *rectángulo virtual* del panel.|  
|[CPane::IsChangeState](#ischangestate)|Se mueve el panel, este método analiza la posición del panel en relación con otros paneles, acoplar filas y ventanas de marco mínima y devuelve el correspondiente `AFX_CS_STATUS` valor.|  
|[CPane::IsDragMode](#isdragmode)|Especifica si se arrastra el panel.|  
|[CPane::IsInFloatingMultiPaneFrameWnd](#isinfloatingmultipaneframewnd)|Especifica si el panel está en una ventana de marco de varios paneles. (Invalida `CBasePane::IsInFloatingMultiPaneFrameWnd`).|  
|[CPane::IsLeftOf](#isleftof)|Determina si se deja el panel de (o superior) del rectángulo especificado.|  
|[CPane::IsResizable](#isresizable)|Determina si el panel puede cambiarse. (Invalida [CBasePane::IsResizable](../../mfc/reference/cbasepane-class.md#isresizable).)|  
|[CPane::IsTabbed](#istabbed)|Determina si el panel se ha insertado en el control de ficha de una ventana con fichas. (Invalida [CBasePane::IsTabbed](../../mfc/reference/cbasepane-class.md#istabbed).)|  
|[CPane::LoadState](#loadstate)|Carga el estado del panel desde el registro. (Invalida [CBasePane::LoadState](../../mfc/reference/cbasepane-class.md#loadstate).)|  
|[CPane::MoveByAlignment](#movebyalignment)|Mueve el panel y el rectángulo virtual en la cantidad especificada.|  
|[CPane::MovePane](#movepane)|Mueve el panel para el rectángulo especificado.|  
|[CPane::OnAfterChangeParent](#onafterchangeparent)|Llamado por el marco de trabajo cuando ha cambiado el elemento primario de un panel.|  
|[CPane::OnBeforeChangeParent](#onbeforechangeparent)|Llamado por el marco cuando el elemento primario del panel que se va a cambiar.|  
|[CPane::OnPressCloseButton](#onpressclosebutton)|Llamado por el marco cuando el usuario elige el botón de cierre en el título del panel.|  
|`CPane::OnProcessDblClk`|Se utiliza internamente.|  
|[CPane::OnShowControlBarMenu](#onshowcontrolbarmenu)|Lo llama el marco de trabajo cuando está a punto de mostrarse un menú de panel especial.|  
|[CPane::OnShowControlBarMenu](#onshowcontrolbarmenu)|Lo llama el marco de trabajo cuando está a punto de mostrarse un menú de panel especial.|  
|`CPane::PrepareToDock`|Se utiliza internamente.|  
|[CPane::RecalcLayout](#recalclayout)|Vuelve a calcular la información de diseño para el panel. (Invalida [CBasePane::RecalcLayout](../../mfc/reference/cbasepane-class.md#recalclayout).)|  
|[CPane::SaveState](#savestate)|Guarda el estado del panel en el registro. (Invalida [CBasePane::SaveState](../../mfc/reference/cbasepane-class.md#savestate).)|  
|[CPane::SetActiveInGroup](#setactiveingroup)|Marca un panel como activa.|  
|[CPane::SetBorders](#setborders)|Establece los valores de borde del panel.|  
|[CPane::SetClientHotSpot](#setclienthotspot)|Establece la zona activa para el panel.|  
|[CPane::SetDockState](#setdockstate)|Restaura la información de estado para el panel de acoplamiento.|  
|[CPane::SetExclusiveRowMode](#setexclusiverowmode)|Habilita o deshabilita el modo de fila exclusivos.|  
|[CPane::SetMiniFrameRTC](#setminiframertc)|Establece la información de clase en tiempo de ejecución de la ventana de marco reducido de forma predeterminada.|  
|[CPane::SetMinSize](#setminsize)|Establece el mínimo tamaño permitido para el panel.|  
|[CPane::SetVirtualRect](#setvirtualrect)|Establece la *rectángulo virtual* del panel.|  
|[CPane::StretchPaneDeferWndPos](#stretchpanedeferwndpos)|Expande el panel vertical u horizontalmente en función de estilo de acoplamiento.|  
|[CPane::ToggleAutoHide](#toggleautohide)|Modo de ocultación automática de conmutadores.|  
|[CPane::UndockPane](#undockpane)|Quita el panel desde el sitio de vinculación, slider predeterminado o ventana de marco reducido que actualmente está acoplada. (Invalida [CBasePane::UndockPane](../../mfc/reference/cbasepane-class.md#undockpane).)|  
|[CPane::UpdateVirtualRect](#updatevirtualrect)|Actualiza el rectángulo virtual.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPane::OnAfterDock](#onafterdock)|Llamado por el marco de trabajo cuando se han acoplado un panel.|  
|[CPane::OnAfterFloat](#onafterfloat)|Llamado por el marco cuando un panel es flotante.|  
|[CPane::OnBeforeDock](#onbeforedock)|Llamado por el marco de trabajo cuando es acoplar el panel.|  
|[CPane::OnBeforeFloat](#onbeforefloat)|Llamado por el marco cuando un panel va a flotar.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPane::m_bHandleMinSize](#m_bhandleminsize)|Permite una manipulación coherente del tamaño mínimo de los paneles.|  
|[CPane::m_recentDockInfo](#m_recentdockinfo)|Contiene información reciente de acoplamiento.|  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, `CPane` objetos no crear instancias directamente. Si necesita un panel con funcionalidad de acoplamiento, derive su objeto de [CDockablePane](../../mfc/reference/cdockablepane-class.md). Si necesita funcionalidad de la barra de herramientas, derive su objeto de [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md).  
  
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
 El diseño de un panel se actualiza inmediatamente.  
  
```  
virtual void AdjustSizeImmediate(BOOL bRecalcLayout = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bRecalcLayout`  
 `TRUE`Para actualizar automáticamente el diseño del panel; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método cuando se cambia dinámicamente el diseño de un panel. Por ejemplo, puede llamar a este método cuando ocultar o mostrar los botones de barra de herramientas.  
  
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
 `FALSE`Si se produce un error en la asignación de memoria; de lo contrario, `TRUE`.  
  
##  <a name="allowshowonpanemenu"></a>CPane::AllowShowOnPaneMenu  
 Especifica si el panel se muestra en la lista generada en tiempo de ejecución de los paneles de la aplicación.  
  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se muestra en la lista; de lo contrario, `FALSE`. La implementación base siempre devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 La aplicación generada por el Asistente contiene una opción de menú que aparecen los paneles que contiene. Este método determina si el panel se muestra en la lista.  
  
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
 `TRUE`Si el panel está orientado horizontalmente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando se tiene que volver a calcular el diseño de un panel. El `rect` parámetro se rellena con el tamaño y el desplazamiento del área cliente del panel. Esto incluye sus bordes y las barras de redimensionamiento.  
  
##  <a name="calcrecentdockedrect"></a>CPane::CalcRecentDockedRect  
 Calcula el rectángulo recientemente acoplado.  
  
```  
void CalcRecentDockedRect();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método actualiza [CPane::m_recentDockInfo](#m_recentdockinfo).  
  
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
 Determina si el panel se puede acoplar el panel de base especificado.  
  
```  
virtual BOOL CanBeDocked(CBasePane* pDockBar) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDockBar`  
 Especifica el panel donde este panel está acoplada.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este panel se puede acoplar el panel de acoplamiento especificado; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método normalmente se llama el marco de trabajo para determinar si se puede acoplar un panel en el panel de acoplamiento especificado. Para determinar si se puede acoplar el panel, el método se evalúa como el panel actualmente habilitado alineación de acoplamiento.  
  
 Habilitar acoplamiento a los distintos lados de la ventana de marco llamando a [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).  
  
##  <a name="canbetabbeddocument"></a>CPane::CanBeTabbedDocument  
 Determina si el panel se puede convertir en un documento con fichas.  
  
```  
virtual BOOL CanBeTabbedDocument() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se puede convertir en un documento con fichas; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada y devolver `FALSE` si desea evitar que un panel que se va a convertir en un documento con fichas. Un documento con fichas no aparecerán en el menú de la posición de la ventana.  
  
##  <a name="converttotabbeddocument"></a>CPane::ConvertToTabbedDocument  
 Convierte un panel acoplable en un documento con fichas.  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bActiveTabOnly`  
 No se usa en `CPane::ConvertToTabbedDocument`.  
  
### <a name="remarks"></a>Comentarios  
 Paneles acoplables sólo se pueden convertir en documentos con fichas. Para obtener información, consulte [CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).  
  
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
  
##  <a name="create"></a>CPane::Create  
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
 Especifica los atributos de estilo de ventana. Para obtener más información, consulte [estilos de ventana](../../mfc/reference/window-styles.md).  
  
 [in] `rect`  
 Especifica el tamaño inicial y la posición de la `pParentWnd` ventana, en coordenadas de cliente.  
  
 [in] [out]`pParentWnd`  
 Especifica la ventana principal de este panel.  
  
 [in] `nID`  
 Especifica el identificador del panel.  
  
 [in] `dwControlBarStyle`  
 Especifica el estilo del panel. Para obtener más información, consulte [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
 [in] [out]`pContext`  
 Especifica el contexto de creación del panel.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se creó correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método crea un panel de Windows y lo adjunta a la `CPane` objeto.  
  
 Si no ha inicializado explícitamente [CPane::m_recentDockInfo](#m_recentdockinfo) antes de llamar a `Create`, el parámetro `rect` se usará como el rectángulo cuando flotante o acoplar el panel.  
  
##  <a name="createdefaultminiframe"></a>CPane::CreateDefaultMiniframe  
 Crea una ventana de marco reducido para un panel flotante.  
  
```  
virtual CPaneFrameWnd* CreateDefaultMiniframe(CRect rectInitial);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectInitial`  
 Especifica el tamaño inicial y la posición, en coordenadas de pantalla de la ventana de marco reducido para crear.  
  
### <a name="return-value"></a>Valor devuelto  
 La ventana de marco reducido recién creado.  
  
### <a name="remarks"></a>Comentarios  
 Este método es llamado por el marco para crear una ventana de marco reducido cuando flota un panel. La ventana de marco reducido puede ser de tipo [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) o de tipo [CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md). Se crea una ventana de marco reducido de múltiples si el panel tiene la `AFX_CBRS_FLOAT_MULTI` estilo.  
  
 Se almacena la información de clase en tiempo de ejecución de la ventana de marco reducido en el `CPane::m_pMiniFrameRTC` miembro. Puede utilizar una clase derivada para establecer a este miembro si decide crear ventanas de marco reducido personalizada.  
  
##  <a name="createex"></a>CPane::CreateEx  
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
 Especifica los atributos de estilo de ventana extendidos. Para obtener más información, consulte [estilos de ventana extendidos](../../mfc/reference/extended-window-styles.md).  
  
 [in] `lpszClassName`  
 Especifica el nombre de la clase de Windows.  
  
 [in] `dwStyle`  
 Especifica los atributos de estilo de ventana. Para obtener más información, consulte [estilos de ventana](../../mfc/reference/window-styles.md).  
  
 [in] `rect`  
 Especifica el tamaño inicial y la posición de la `pParentWnd` ventana, en coordenadas de cliente.  
  
 [in] [out]`pParentWnd`  
 Especifica la ventana principal de este panel.  
  
 [in] `nID`  
 Especifica el identificador del panel.  
  
 [in] `dwControlBarStyle`  
 Especifica el estilo del panel. Para obtener más información, consulte [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
 [in] [out]`pContext`  
 Especifica el contexto de creación para el panel.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se creó correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método crea un panel de Windows y lo adjunta a la `CPane` objeto.  
  
 Si no ha inicializado explícitamente [CPane::m_recentDockInfo](#m_recentdockinfo) antes de llamar a `CreateEx`, el parámetro `rect` se usará como el rectángulo cuando flotante o acoplar el panel.  
  
##  <a name="dockbymouse"></a>CPane::DockByMouse  
 Un panel se acopla con el mouse.  
  
```  
virtual BOOL DockByMouse(CBasePane* pDockBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDockBar`  
 Especifica el panel de base a la que se acopla este panel.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se acopla correctamente; de lo contrario, `FALSE`.  
  
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
 Especifica el método de acoplamiento que utilice. Las opciones disponibles son:  
  
|Opción|Descripción|  
|------------|-----------------|  
|`DM_UNKNOWN`|El marco de trabajo usa esta opción cuando el método acoplamiento es desconocido. El panel no almacena la última posición flotante. También puede utilizar esta opción para acoplar mediante programación un panel cuando no es necesario que almacenar la posición flotante recientes.|  
|`DM_MOUSE`|Se utiliza internamente.|  
|`DM_DBL_CLICK`|Esta opción se utiliza cuando se hace doble clic en el punto de sujeción. El panel se vuelve a colocar en su posición de acoplamiento más reciente. Si el panel está desacoplado haciendo doble clic en, el panel se vuelve a colocar en su posición flotante más reciente.|  
|`DM_SHOW`|Esta opción se puede utilizar para acoplar el panel de mediante programación. El panel almacena su posición flotante más reciente.|  
|`DM_RECT`|El panel está acoplado en la región especificada por `lpRect`.|  
|`DM_STANDARD`|Si utiliza esta opción, el marco de trabajo dibuja el panel como un marco de esquema mientras se mueve.|  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se acopla correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método acopla el panel en el panel de base especificada por el `pDockBar` parámetro. Primero debe habilitar acoplamiento llamando a [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).  
  
##  <a name="dockpanestandard"></a>CPane::DockPaneStandard  
 Un panel se acopla utilizando el esquema de acoplamiento (estándar).  
  
```  
virtual CPane* DockPaneStandard(BOOL& bWasDocked);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bWasDocked`  
 `TRUE`Si el panel se acopla correctamente; de lo contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 Este método devuelve siempre el `this` puntero.  
  
### <a name="remarks"></a>Comentarios  
 Este método se usa solo para paneles derivados de la [CDockablePane Class](../../mfc/reference/cdockablepane-class.md). Para obtener más información, consulte [CDockablePane::DockPaneStandard](../../mfc/reference/cdockablepane-class.md#dockpanestandard).  
  
##  <a name="docktoframewindow"></a>CPane::DockToFrameWindow  
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
 El tamaño especificado.  
  
 [in] `dwDockFlags`  
 ignorado.  
  
 [in] `pRelativeBar`  
 ignorado.  
  
 [in] `nRelativeIndex`  
 ignorado.  
  
 [in] `bOuterEdge`  
 Si `TRUE` y hay otros paneles acoplables en el lado que se especifican mediante `dwAlignment`, el panel se acopla fuera de los otros paneles, más cerca del borde del marco primario. Si `FALSE`, el panel se acopla más cercano al centro del área de cliente.  
  
### <a name="return-value"></a>Valor devuelto  
 `FALSE`Si un divisor ( [CPaneDivider clase](../../mfc/reference/cpanedivider-class.md)) no puede ser creado; en caso contrario, `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="doesallowsiblingbars"></a>CPane::DoesAllowSiblingBars  
 Indica si se puede acoplar el panel de otro en la misma fila en el panel actual está acoplado.  
  
```  
virtual BOOL DoesAllowSiblingBars() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este panel se puede acoplar a otro panel en la misma fila por sí misma; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Puede habilitar o deshabilitar este comportamiento mediante una llamada a [CPane::SetExclusiveRowMode](#setexclusiverowmode).  
  
 De forma predeterminada, las barras de herramientas tienen deshabilitado el modo exclusivo de fila y la barra de menús tiene habilitado el modo de fila exclusivos.  
  
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
 Especifica la ubicación, en coordenadas de pantalla para colocar el panel al que flota.  
  
 [in] `dockMethod`  
 Especifica el método que se usará cuando flota el panel de acoplamiento. Para obtener una lista de valores posibles, consulte [CPane::DockPane](#dockpane).  
  
 [in] `bShow`  
 `TRUE`para mostrar el panel cuando flota; de lo contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se flota correctamente o si el panel no puede flotar porque [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat) devuelve `FALSE`; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para hacer flotar el panel situado en la posición especificada por el `rectFloat` parámetro. Este método crea automáticamente una ventana de marco reducido primaria para el panel.  
  
##  <a name="getavailableexpandsize"></a>CPane::GetAvailableExpandSize  
 Devuelve la cantidad, en píxeles, que se puede expandir el panel.  
  
```  
virtual int GetAvailableExpandSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si el panel se acopla horizontalmente, el valor devuelto es el ancho disponible; de lo contrario, el valor devuelto es el alto disponible.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getavailablestretchsize"></a>CPane::GetAvailableStretchSize  
 Devuelve la cantidad, en píxeles, que puede reducir el tamaño del panel.  
  
```  
virtual int GetAvailableStretchSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La cantidad, en píxeles, que puede reducir el tamaño del panel. Si el panel se acopla horizontalmente, esta cantidad es el ancho disponible; de lo contrario, es el alto disponible.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de ajuste disponible se calcula restando el mínimo tamaño permitido para el panel ( [CPane::GetMinSize](#getminsize)) desde el tamaño actual ( [CWnd::GetWindowRect](../../mfc/reference/cwnd-class.md#getwindowrect)).  
  
##  <a name="getborders"></a>CPane::GetBorders  
 Devuelve el ancho de los bordes del panel.  
  
```  
CRect GetBorders() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que contiene el ancho actual, en píxeles, de cada lado del panel. Por ejemplo, el valor de la `left` miembro de la `CRect` objeto es el ancho del borde izquierdo.  
  
### <a name="remarks"></a>Comentarios  
 Para establecer el tamaño de los bordes, llame a [CPane::SetBorders](#setborders).  
  
##  <a name="getclienthotspot"></a>CPane::GetClientHotSpot  
 Devuelve el *zona activa* para el panel.  
  
```  
CPoint GetClientHotSpot() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 El *zona activa* es el punto en el panel de que el usuario selecciona y se mantiene para mover el panel. Una zona activa se usa para una animación fluida cuando el panel se mueve de una posición anclada.  
  
##  <a name="getdocksiterow"></a>CPane::GetDockSiteRow  
 Devuelve la fila dock ( [CDockingPanesRow clase](../../mfc/reference/cdockingpanesrow-class.md)) en la que el panel está acoplado.  
  
```  
CDockingPanesRow* GetDockSiteRow() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CDockingPanesRow`* que apunta a la fila de acoplamiento en la que el panel está acoplado, o `NULL` si el panel no está acoplado.  
  
##  <a name="getexclusiverowmode"></a>CPane::GetExclusiveRowMode  
 Determina si el panel está en modo exclusivo de fila.  
  
```  
virtual BOOL GetExclusiveRowMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel está en modo de fila exclusivos; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca del modo de fila exclusivos, consulte [CPane::SetExclusiveRowMode](#setexclusiverowmode).  
  
##  <a name="gethotspot"></a>CPane::GetHotSpot  
 Devuelve la zona activa que se almacena en una base de `CMFCDragFrameImpl` objeto.  
  
```  
CPoint GetHotSpot() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 El `CPane` clase contiene un `CMFCDragFrameImpl` objeto, `m_dragFrameImpl`, que es responsable de dibujar el rectángulo que aparece cuando el usuario mueve un panel en el modo de acoplamiento estándar. La zona activa se usa para dibujar el rectángulo con respecto a la posición actual del mouse cuando el usuario mueve el panel.  
  
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
 Recupera el título del panel.  
  
```  
virtual void GetPaneName(CString& strName) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `strName`  
 Un `CString` objeto que se rellena con el nombre del título.  
  
### <a name="remarks"></a>Comentarios  
 Título del panel se muestra en el área de título cuando el panel está acoplado o flotante. Si el panel forma parte de un grupo, el título se muestra en el área de fichas. Si el panel está en modo de ocultación automática, el título se muestra en un `CMFCAutoHideButton`.  
  
##  <a name="getvirtualrect"></a>CPane::GetVirtualRect  
 Recupera el *rectángulo virtual* del panel.  
  
```  
void GetVirtualRect(CRect& rectVirtual) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `rectVirtual`  
 Un `CRect` objeto que se rellena con el rectángulo virtual.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se mueve un panel, el marco de trabajo almacena la posición original del panel en un rectángulo virtual. El marco de trabajo puede utilizar el rectángulo virtual para restaurar la posición original del panel.  
  
 No llame a los métodos que están relacionados con rectángulos virtuales a menos que se va a mover paneles mediante programación.  
  
##  <a name="ischangestate"></a>CPane::IsChangeState  
 Se mueve el panel, este método analiza su posición en relación con otros paneles, acoplar filas y ventanas de marco mínima y devuelve el correspondiente `AFX_CS_STATUS` valor.  
  
```  
virtual AFX_CS_STATUS IsChangeState(
    int nOffset,  
    CBasePane** ppTargetBar) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nOffset`  
 Especifica la distinción de acoplamiento. Por ejemplo, un panel que se mueve `nOffset` se acoplará píxeles desde una fila de acoplamiento.  
  
 [in] `ppTargetBar`  
 Cuando el método vuelve, `ppTargetBar` contiene el puntero al objeto al que se debe acoplar el panel actual, o `NULL` si no debe producirse acoplar.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los siguientes valores de `AFX_CS_STATUS`:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`CS_NOTHING`|El panel no está cerca de un sitio de vinculación. El marco no acoplar el panel.|  
|`CS_DOCK_IMMEDIATELY`|El panel está por encima de un sitio de vinculación y el `DT_IMMEDIATE` estilo está habilitado. El marco de trabajo acopla el panel inmediatamente.|  
|`CS_DELAY_DOCK`|El panel está por encima de un sitio de vinculación es otro panel acoplable o un borde del marco principal. El marco de trabajo acopla el panel cuando el usuario suelta el movimiento.|  
|`CS_DELAY_DOCK_TO_TAB`|El panel está por encima de un sitio de vinculación que hace que el panel se acopla en una ventana con fichas. Esto se produce cuando el panel está sobre el título de otro panel de acoplamiento o sobre el área de ficha de un panel con fichas. El marco de trabajo acopla el panel cuando el usuario suelta el movimiento.|  
  
##  <a name="isdragmode"></a>CPane::IsDragMode  
 Especifica si se va a mover el panel.  
  
```  
virtual BOOL IsDragMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se mueve el panel; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isinfloatingmultipaneframewnd"></a>CPane::IsInFloatingMultiPaneFrameWnd  
 Especifica si el panel está en una ventana de marco de varios paneles ( [CMultiPaneFrameWnd clase](../../mfc/reference/cmultipaneframewnd-class.md)).  
  
```  
virtual BOOL IsInFloatingMultiPaneFrameWnd() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel está en una ventana de marco de varios paneles; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Pueden flotar paneles acoplables solo en una ventana de marco de varios paneles. Por lo tanto, `CPane::IsInFloatingMultiPaneFrameWnd` siempre devuelve `FALSE`.  
  
##  <a name="isleftof"></a>CPane::IsLeftOf  
 Determina si se deja el panel de (o superior) del rectángulo especificado.  
  
```  
bool IsLeftOf(
    CRect rect,  
    bool bWindowRect = true) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rect`  
 Un `CRect` objeto que se utiliza para la comparación.  
  
 [in] `bWindowRect`  
 Si `TRUE`, `rect` se supone que contienen las coordenadas de pantalla; si `FALSE`, `rect` se supone que contiene las coordenadas de cliente.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 Si el panel se acopla horizontalmente, este método comprueba si se deja su ubicación de `rect`. De lo contrario, este método comprueba si la ubicación está encima de `rect`.  
  
##  <a name="isresizable"></a>CPane::IsResizable  
 Especifica si se puede cambiar el tamaño del panel.  
  
```  
virtual BOOL IsResizable() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se puede cambiar de tamaño; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Base `CPane` los objetos no son de tamaño variable.  
  
 El Administrador de acoplamiento usa el indicador de tamaño variable para determinar el diseño del panel. Paneles de tamaño variable no siempre se encuentran en los bordes exteriores de un marco primario.  
  
 Paneles de tamaño variable no pueden residir en contenedores de acoplamiento.  
  
##  <a name="istabbed"></a>CPane::IsTabbed  
 Determina si el panel se ha insertado en el control de ficha de una ventana con fichas.  
  
```  
virtual BOOL IsTabbed() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se fichas; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El estado con fichas se trata por separado de flotante, acopla y Estados de ocultación automática.  
  
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
 `TRUE`Si el estado del panel se ha cargado correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para cargar el estado del panel desde el registro. Reemplazar en una clase derivada para cargar información adicional almacenada [CPane::SaveState](#savestate).  
  
 Cuando se reemplaza este método, también llama al método base y devolver `FALSE` si el método base devuelve `FALSE`.  
  
##  <a name="m_bhandleminsize"></a>CPane::m_bHandleMinSize  
 Permite el tratamiento coherente de tamaño mínimo del panel.  
  
```  
AFX_IMPORT_DATA static BOOL m_bHandleMinSize;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si uno o más paneles de acoplamiento en la aplicación reemplaza `GetMinSize`, o si la aplicación llama `SetMinSize`, puede establecer este miembro estático en `TRUE` para permitir que el marco de trabajo coherente controlar cómo se cambia el tamaño de paneles.  
  
 Si este valor se establece en `TRUE`, cuyo tamaño se debe reducir por debajo de su tamaño mínimo de todos los paneles se recortan, no ajusta. Dado que el marco de trabajo utiliza regiones de ventana para fines de ajuste de tamaño del panel, no cambie el tamaño de la región de ventana para acoplar paneles si este valor se establece en `TRUE`.  
  
##  <a name="m_recentdockinfo"></a>CPane::m_recentDockInfo  
 Contiene información reciente de acoplamiento.  
  
```  
CRecentDockSiteInfo m_recentDockInfo;  
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo almacena la información de estado más reciente de acoplamiento del panel en este miembro.  
  
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
|`CBRS_ALIGN_TOP`|Habilita el panel acoplada en la parte superior del área cliente de una ventana de marco.|  
|`CBRS_ALIGN_BOTTOM`|Permite que el panel se acopla a la parte inferior del área de cliente de una ventana de marco.|  
|`CBRS_ALIGN_LEFT`|Permite que el panel se acopla al lado izquierdo del área cliente de una ventana de marco.|  
|`CBRS_ALIGN_RIGHT`|Permite que el panel se acopla a la derecha del área de cliente de una ventana de marco.|  
|`CBRS_ALIGN_ANY`|Permite que el panel se acopla a cualquier lado del área de cliente de una ventana de marco.|  
  
 Si `dwAlignment` contiene el `CBRS_ALIGN_LEFT` o `CBRS_ALIGN_RIGHT` marca, el panel y el rectángulo virtual se mueven horizontal; en caso contrario, si `dwAlignment` contiene el `CBRS_ALIGN_TOP` o `CBRS_ALIGN_BOTTOM` marca, el panel y el rectángulo virtual se mueven verticalmente.  
  
##  <a name="movepane"></a>CPane::MovePane  
 Mueve el panel para el rectángulo especificado.  
  
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
 Si `TRUE`, este método omite el tamaño mínimo permitido del panel ( [CPane::GetMinSize](#getminsize)); en caso contrario, el panel se ajusta, si es necesario, para asegurarse de que al menos el mínimo tamaño permitido.  
  
 [in] `hdwp`  
 No usado.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CSize` objeto que contiene las diferencias de ancho y alto entre los rectángulos nuevos y antiguos (rectángulo antiguo: `rectNew`).  
  
### <a name="remarks"></a>Comentarios  
 Este método se usa solo para los paneles acoplables.  
  
##  <a name="onafterchangeparent"></a>CPane::OnAfterChangeParent  
 Llamado por el marco de trabajo cuando ha cambiado el elemento primario de un panel.  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`pWndOldParent`  
 Ventana principal de la anterior del panel.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando el elemento primario de un panel ha cambiado debido a una operación de acoplamiento o flotante.  
  
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
 Llamado por el marco de trabajo cuando flota de un panel.  
  
```  
virtual void OnAfterFloat();
```  
  
### <a name="remarks"></a>Comentarios  
 Puede invalidar este método en una clase derivada si desea realizar cualquier procesamiento después de la flota de un panel.  
  
##  <a name="onbeforechangeparent"></a>CPane::OnBeforeChangeParent  
 Llamado por el marco cuando el elemento primario del panel que se va a cambiar.  
  
```  
virtual void OnBeforeChangeParent(
    CWnd* pWndNewParent,  
    BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`pWndNewParent`  
 Especifica la nueva ventana primaria.  
  
 [in] `bDelay`  
 `TRUE`Para retrasar el ajuste del diseño de acoplamiento global; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Por el marco de trabajo llama a este método cuando el elemento primario del panel está a punto de cambiar porque el panel está acoplado o flotante.  
  
 De forma predeterminada, el panel está registrado con el panel acoplable mediante una llamada a `CDockSite::RemovePane`.  
  
##  <a name="onbeforedock"></a>CPane::OnBeforeDock  
 Llamado por el marco de trabajo cuando es acoplar el panel.  
  
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
 El marco de trabajo llama a este método cuando se puede acoplar un panel. Puede invalidar este método en una clase derivada si desea realizar cualquier procesamiento antes de que finalmente se acopla un panel.  
  
##  <a name="onbeforefloat"></a>CPane::OnBeforeFloat  
 Lo llama el marco de trabajo cuando se trata de un panel a float.  
  
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
 `TRUE`Si el panel puede flotar; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando se trata de un panel a float. Puede invalidar este método en una clase derivada si desea realizar cualquier procesamiento antes de que el panel finalmente flota.  
  
##  <a name="onpressclosebutton"></a>CPane::OnPressCloseButton  
 Llamado por el marco cuando el usuario presiona el botón de cierre en el título del panel.  
  
```  
virtual void OnPressCloseButton();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando el usuario presiona el **cerrar** botón de título del panel. Para recibir notificaciones acerca de la **cerrar** eventos, puede invalidar este método en una clase derivada.  
  
##  <a name="onshowcontrolbarmenu"></a>CPane::OnShowControlBarMenu  
 Lo llama el marco de trabajo cuando está a punto de mostrarse un menú de panel especial.  
  
```  
virtual BOOL OnShowControlBarMenu(CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 Especifica la ubicación del menú.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se puede mostrar el menú; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El menú contiene varios elementos que le permiten especificar el comportamiento del panel, a saber: **flotante**, **acoplamiento**, **AutoHide**, y **ocultar**. Puede habilitar este menú para todos los paneles mediante una llamada a [CDockingManager::EnableDockSiteMenu](../../mfc/reference/cdockingmanager-class.md#enabledocksitemenu).  
  
##  <a name="recalclayout"></a>CPane::RecalcLayout  
 Vuelve a calcular la información de diseño para el panel.  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>Comentarios  
 Si el panel está acoplado, este método actualiza el rectángulo virtual para el panel estableciendo su tamaño al tamaño actual del panel.  
  
 Si el panel está flotando, este método notifica el marco primario a mínima para ajustar el tamaño del panel para el tamaño del marco mínima. El marco de trabajo garantiza que el marco mínima es al menos el mínimo tamaño permitido para el panel ( [CPane::GetMinSize](#getminsize)) y cambia el tamaño del marco reducido si es necesario.  
  
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
 `TRUE`Si el estado se guardó correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando guarda el estado del panel en el registro. Invalidar `SaveState` en una clase derivada para almacenar información adicional.  
  
 Cuando se reemplaza este método, también llama al método base y devolver `FALSE` si el método base devuelve `FALSE`.  
  
##  <a name="setactiveingroup"></a>CPane::SetActiveInGroup  
 Marca un panel como activa.  
  
```  
virtual void SetActiveInGroup(BOOL bActive);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bActive`  
 Un `BOOL` que especifica si el panel está marcado como activa.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se muestra un panel acoplable o se elige un botón de ocultación automática, el panel de ocultación automática correspondiente se marca como activo.  
  
 La apariencia de un botón de ocultación automática está asociado con el panel se basa en dos factores. Si el panel está activo y la `static``BOOL``CMFCAutoHideButton::m_bOverlappingTabs` es `TRUE`, el marco de trabajo muestra el botón Ocultar automáticamente como un icono y una etiqueta. Para un panel inactivo, el marco de trabajo muestra sólo el icono de ocultar automáticamente.  
  
 Si `CMFCAutoHideButton::m_bOverlappingTabs` es `FALSE`, o si no está situado en un grupo, el marco de trabajo muestra el botón Ocultar automáticamente asociado como un icono y una etiqueta.  
  
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
 Un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que contiene el ancho, en píxeles, de cada borde del panel.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para establecer los tamaños de los bordes del panel.  
  
##  <a name="setclienthotspot"></a>CPane::SetClientHotSpot  
 Establece la *zona activa* para el panel.  
  
```  
void SetClientHotSpot(const CPoint& ptNew);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `ptNew`  
 Un `CPoint` objeto que especifica la nueva zona activa.  
  
### <a name="remarks"></a>Comentarios  
 El *zona activa* es el punto en el panel de que el usuario selecciona y se mantiene para mover el panel. Una zona activa se usa para una animación fluida cuando el panel se arrastra desde una posición anclada.  
  
##  <a name="setdockstate"></a>CPane::SetDockState  
 Restaura la información de estado para el panel de acoplamiento.  
  
```  
virtual void SetDockState(CDockingManager* pDockManager);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDockManager`  
 Puntero al administrador de acoplamiento para la ventana de marco principal.  
  
### <a name="remarks"></a>Comentarios  
 Este método es llamado por el marco para restaurar la información de estado de acoplamiento recientes para el panel. Un panel almacena información de estado de acoplamiento reciente en [CPane::m_recentDockInfo](#m_recentdockinfo). Para obtener más información, consulte el [CRecentDockSiteInfo clase](../../mfc/reference/crecentdocksiteinfo-class.md).  
  
 También puede llamar a este método para establecer el estado de acoplamiento cuando se carga la información del panel desde un origen externo.  
  
##  <a name="setexclusiverowmode"></a>CPane::SetExclusiveRowMode  
 Habilita o deshabilita el modo de fila exclusivos.  
  
```  
virtual void SetExclusiveRowMode(BOOL bExclusive = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bExclusive`  
 `TRUE`Para habilitar el modo de fila exclusivos; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para habilitar o deshabilitar el modo de fila exclusivos. Cuando un panel está en modo de fila exclusivos, no puede compartir la misma fila con otras barras de herramientas.  
  
 De forma predeterminada, todas las barras de herramientas tienen deshabilitado el modo exclusivo de fila y la barra de menús tiene habilitado el modo de fila exclusivos.  
  
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
 Establece la *rectángulo virtual* del panel.  
  
```  
void SetVirtualRect(
    const CRect& rect,  
    BOOL bMapToParent = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rect`  
 Un `CRect` objeto que especifica el rectángulo virtual a establecerse.  
  
 [in] `bMapToParent`  
 Especifique `TRUE` si `rect` contiene puntos con relación a la ventana primaria.  
  
### <a name="remarks"></a>Comentarios  
 Un *rectángulo virtual* almacena la posición original de un panel cuando se mueve. El marco de trabajo puede utilizar el rectángulo virtual para restaurar la posición original.  
  
 No llame a los métodos que están relacionados con rectángulos virtuales a menos que se va a mover paneles mediante programación.  
  
##  <a name="setminiframertc"></a>CPane::SetMiniFrameRTC  
 Establece la información de clase en tiempo de ejecución de la ventana de marco reducido de forma predeterminada.  
  
```  
void SetMiniFrameRTC(CRuntimeClass* pClass);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`pClass`  
 Especifica la información de clase en tiempo de ejecución de la ventana de marco reducido.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un panel flotando, se coloca un [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) ventana (minimarco). Puede proporcionar un personalizado `CPaneFrameWnd`-clase derivada que será utilizado al [CPane::CreateDefaultMiniframe](#createdefaultminiframe) se llama.  
  
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
 La cantidad real, en píxeles, que se ajustó el panel.  
  
### <a name="remarks"></a>Comentarios  
 Si es necesario, este método modifica `nStretchSize` para asegurarse de que el panel no supere los límites de tamaño. Estos límites se obtienen llamando a [CPane::GetAvailableStretchSize](#getavailablestretchsize) y [CPane::GetAvailableExpandSize](#getavailableexpandsize).  
  
##  <a name="toggleautohide"></a>CPane::ToggleAutoHide  
 Modo de ocultación automática de conmutadores.  
  
```  
virtual void ToggleAutoHide();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para alternar el modo de ocultación automática. Debe acoplar un panel a una ventana de marco principal para poder cambiar a modo de ocultación automática.  
  
##  <a name="undockpane"></a>CPane::UndockPane  
 Quita el panel desde el sitio de vinculación, slider predeterminado o ventana de marco reducido que actualmente está acoplada.  
  
```  
virtual void UndockPane(BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bDelay`  
 Si `FALSE`, el marco llama [CBasePane::AdjustDockingLayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout) para ajustar el diseño de acoplamiento.  
  
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
 Un `CPoint` objeto que especifica un desplazamiento de la que hay que desplazar el panel.  
  
 [in] `sizeNew`  
 Un `CSize` objeto que especifica un nuevo tamaño para el panel.  
  
### <a name="remarks"></a>Comentarios  
 La primera sobrecarga establece el rectángulo virtual mediante la posición actual y el tamaño del panel.  
  
 La segunda sobrecarga desplaza la cantidad especificada por el rectángulo virtual `ptOffset`.  
  
 La tercera sobrecarga establece el rectángulo virtual mediante la posición actual del panel y el tamaño especificado por `sizeNew`.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CBasePane](../../mfc/reference/cbasepane-class.md)

