---
title: Clase CDockablePane | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDockablePane
- AFXDOCKABLEPANE/CDockablePane
- AFXDOCKABLEPANE/CDockablePane::CDockablePane
- AFXDOCKABLEPANE/CDockablePane::AttachToTabWnd
- AFXDOCKABLEPANE/CDockablePane::CalcFixedLayout
- AFXDOCKABLEPANE/CDockablePane::CanAcceptMiniFrame
- AFXDOCKABLEPANE/CDockablePane::CanAcceptPane
- AFXDOCKABLEPANE/CDockablePane::CanAutoHide
- AFXDOCKABLEPANE/CDockablePane::CanBeAttached
- AFXDOCKABLEPANE/CDockablePane::ConvertToTabbedDocument
- AFXDOCKABLEPANE/CDockablePane::CopyState
- AFXDOCKABLEPANE/CDockablePane::Create
- AFXDOCKABLEPANE/CDockablePane::CreateDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::CreateEx
- AFXDOCKABLEPANE/CDockablePane::CreateTabbedPane
- AFXDOCKABLEPANE/CDockablePane::DockPaneContainer
- AFXDOCKABLEPANE/CDockablePane::DockPaneStandard
- AFXDOCKABLEPANE/CDockablePane::DockToRecentPos
- AFXDOCKABLEPANE/CDockablePane::DockToWindow
- AFXDOCKABLEPANE/CDockablePane::EnableAutohideAll
- AFXDOCKABLEPANE/CDockablePane::EnableGripper
- AFXDOCKABLEPANE/CDockablePane::GetAHRestoredRect
- AFXDOCKABLEPANE/CDockablePane::GetAHSlideMode
- AFXDOCKABLEPANE/CDockablePane::GetCaptionHeight
- AFXDOCKABLEPANE/CDockablePane::GetDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::GetDockingStatus
- AFXDOCKABLEPANE/CDockablePane::GetDragSensitivity
- AFXDOCKABLEPANE/CDockablePane::GetLastPercentInPaneContainer
- AFXDOCKABLEPANE/CDockablePane::GetTabArea
- AFXDOCKABLEPANE/CDockablePane::GetTabbedPaneRTC
- AFXDOCKABLEPANE/CDockablePane::HasAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::HitTest
- AFXDOCKABLEPANE/CDockablePane::IsAutohideAllEnabled
- AFXDOCKABLEPANE/CDockablePane::IsAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::IsDocked
- AFXDOCKABLEPANE/CDockablePane::IsHideInAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::IsInFloatingMultiPaneFrameWnd
- AFXDOCKABLEPANE/CDockablePane::IsResizable
- AFXDOCKABLEPANE/CDockablePane::IsTabLocationBottom
- AFXDOCKABLEPANE/CDockablePane::IsTracked
- AFXDOCKABLEPANE/CDockablePane::IsVisible
- AFXDOCKABLEPANE/CDockablePane::OnAfterChangeParent
- AFXDOCKABLEPANE/CDockablePane::OnAfterDockFromMiniFrame
- AFXDOCKABLEPANE/CDockablePane::OnBeforeChangeParent
- AFXDOCKABLEPANE/CDockablePane::OnBeforeFloat
- AFXDOCKABLEPANE/CDockablePane::RemoveFromDefaultPaneDividier
- AFXDOCKABLEPANE/CDockablePane::ReplacePane
- AFXDOCKABLEPANE/CDockablePane::RestoreDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::SetAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::SetAutoHideParents
- AFXDOCKABLEPANE/CDockablePane::SetLastPercentInPaneContainer
- AFXDOCKABLEPANE/CDockablePane::SetRestoredDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::SetTabbedPaneRTC
- AFXDOCKABLEPANE/CDockablePane::ShowPane
- AFXDOCKABLEPANE/CDockablePane::Slide
- AFXDOCKABLEPANE/CDockablePane::ToggleAutoHide
- AFXDOCKABLEPANE/CDockablePane::UndockPane
- AFXDOCKABLEPANE/CDockablePane::CheckAutoHideCondition
- AFXDOCKABLEPANE/CDockablePane::CheckStopSlideCondition
- AFXDOCKABLEPANE/CDockablePane::DrawCaption
- AFXDOCKABLEPANE/CDockablePane::OnPressButtons
- AFXDOCKABLEPANE/CDockablePane::OnSlide
- AFXDOCKABLEPANE/CDockablePane::m_bDisableAnimation
- AFXDOCKABLEPANE/CDockablePane::m_bHideInAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::m_nSlideSteps
dev_langs:
- C++
helpviewer_keywords:
- CDockablePane class
ms.assetid: e2495f4c-765f-48f9-a2e2-e45e47608d91
caps.latest.revision: 34
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: dea1f1ce66c0e9bedbe83109ab62055a4af2ebce
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cdockablepane-class"></a>CDockablePane Class
Implementa un panel que se puede acoplar en un sitio de vinculación o incluir en un panel con fichas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDockablePane : public CPane  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDockablePane::CDockablePane](#cdockablepane)|Construye e inicializa un objeto `CDockablePane`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDockablePane::AttachToTabWnd](#attachtotabwnd)|Asocia un panel a otro panel. Esto crea un panel con fichas.|  
|[CDockablePane::CalcFixedLayout](#calcfixedlayout)|Devuelve el tamaño del rectángulo de panel.|  
|[CDockablePane::CanAcceptMiniFrame](#canacceptminiframe)|Determina si se puede acoplar el marco mini especificado al panel.|  
|[CDockablePane::CanAcceptPane](#canacceptpane)|Determina si el otro panel se puede acoplar el panel actual.|  
|[CDockablePane::CanAutoHide](#canautohide)|Determina si el panel admite el modo de ocultación automática. (Invalida [CBasePane::CanAutoHide](../../mfc/reference/cbasepane-class.md#canautohide).)|  
|[CDockablePane::CanBeAttached](#canbeattached)|Determina si se puede acoplar el panel actual a otro panel.|  
|[CDockablePane::ConvertToTabbedDocument](#converttotabbeddocument)|Convierte uno o más paneles acoplables en documentos con fichas de MDI.|  
|[CDockablePane::CopyState](#copystate)|Copia el estado de un panel acoplable.|  
|[CDockablePane::Create](#create)|Crea el control de Windows y lo adjunta a la `CDockablePane` objeto.|  
|[CDockablePane::CreateDefaultPaneDivider](#createdefaultpanedivider)|Crea un divisor predeterminado para el panel como fijarla en una ventana de marco.|  
|[CDockablePane::CreateEx](#createex)|Crea el control de Windows y lo adjunta a la `CDockablePane` objeto.|  
|[CDockablePane::CreateTabbedPane](#createtabbedpane)|Crea un panel con fichas en el panel actual.|  
|[CDockablePane::DockPaneContainer](#dockpanecontainer)|En el panel se acopla un contenedor.|  
|[CDockablePane::DockPaneStandard](#dockpanestandard)|Un panel se acopla utilizando el esquema de acoplamiento (estándar).|  
|`CDockablePane::DockToFrameWindow`|Se utiliza internamente. Para acoplar un panel, use [CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane) o [CDockablePane::DockToWindow](#docktowindow).|  
|[CDockablePane::DockToRecentPos](#docktorecentpos)|Un panel se acopla a su posición de acoplamiento reciente almacenado.|  
|[CDockablePane::DockToWindow](#docktowindow)|Un panel acoplable se acoplará a otro panel de acoplamiento.|  
|[CDockablePane::EnableAutohideAll](#enableautohideall)|Habilita o deshabilita el modo de ocultación automática para este panel junto con otros paneles en el contenedor.|  
|[CDockablePane::EnableGripper](#enablegripper)|Muestra u oculta la leyenda (agarrador).|  
|[CDockablePane::GetAHRestoredRect](#getahrestoredrect)|Especifica la posición del panel cuando está visible en modo de ocultación automática.|  
|[CDockablePane::GetAHSlideMode](#getahslidemode)|Recupera el modo de diapositiva Ocultar automáticamente del panel.|  
|`CDockablePane::GetAutoHideButton`|Se utiliza internamente.|  
|`CDockablePane::GetAutoHideToolBar`|Se utiliza internamente.|  
|[CDockablePane::GetCaptionHeight](#getcaptionheight)|Devuelve el alto del título actual.|  
|[CDockablePane::GetDefaultPaneDivider](#getdefaultpanedivider)|Devuelve el divisor de paneles predeterminada para el contenedor del panel.|  
|[CDockablePane::GetDockingStatus](#getdockingstatus)|Determina la capacidad de un panel acoplado en función de la ubicación del puntero proporcionado.|  
|[CDockablePane::GetDragSensitivity](#getdragsensitivity)|Devuelve la sensibilidad de arrastre de un panel acoplable.|  
|[CDockablePane::GetLastPercentInPaneContainer](#getlastpercentinpanecontainer)|Recupera el porcentaje de espacio que ocupa un panel dentro de su contenedor.|  
|[CDockablePane::GetTabArea](#gettabarea)|Recupera el área de la ficha del panel.|  
|[CDockablePane::GetTabbedPaneRTC](#gettabbedpanertc)|Devuelve la información de clase en tiempo de ejecución acerca de una ventana con fichas que se crea cuando otro panel se acopla al panel actual.|  
|[CDockablePane::HasAutoHideMode](#hasautohidemode)|Especifica si un panel acoplable se puede cambiar a modo de ocultación automática.|  
|[CDockablePane::HitTest](#hittest)|Especifica la ubicación específica en un panel donde el usuario hace clic en un mouse.|  
|`CDockablePane::IsAccessibilityCompatible`|Se utiliza internamente.|  
|[CDockablePane::IsAutohideAllEnabled](#isautohideallenabled)|Indica si el panel de acoplamiento y todos los demás paneles en el contenedor pueden colocarse en modo de ocultación automática.|  
|[CDockablePane::IsAutoHideMode](#isautohidemode)|Determina si un panel está en modo de ocultación automática.|  
|`CDockablePane::IsChangeState`|Se utiliza internamente.|  
|[CDockablePane::IsDocked](#isdocked)|Determina si se acopla el panel actual.|  
|[CDockablePane::IsHideInAutoHideMode](#ishideinautohidemode)|Determina el comportamiento de un panel que está en modo de ocultación automática si se muestra (u oculto) llamando a `ShowPane`.|  
|[CDockablePane::IsInFloatingMultiPaneFrameWnd](#isinfloatingmultipaneframewnd)|Especifica si el panel está en una ventana de marco de varios paneles.|  
|[CDockablePane::IsResizable](#isresizable)|Especifica si se puede cambiar el tamaño del panel.|  
|[CDockablePane::IsTabLocationBottom](#istablocationbottom)|Especifica si se encuentra en la parte superior o inferior del panel de pestañas.|  
|[CDockablePane::IsTracked](#istracked)|Especifica si el usuario arrastra un panel.|  
|[CDockablePane::IsVisible](#isvisible)|Determina si está visible el panel actual.|  
|[CDockablePane::LoadState](http://msdn.microsoft.com/en-us/96110136-4f46-4764-8a76-3b4abaf77917)|Se utiliza internamente.|  
|[CDockablePane::OnAfterChangeParent](#onafterchangeparent)|Llamado por el marco de trabajo cuando ha cambiado el elemento primario de un panel. (Invalida [CPane::OnAfterChangeParent](../../mfc/reference/cpane-class.md#onafterchangeparent).)|  
|[CDockablePane::OnAfterDockFromMiniFrame](#onafterdockfromminiframe)|Llamado por el marco de trabajo cuando se acopla una barra de acoplamiento flotante en una ventana de marco.|  
|[CDockablePane::OnBeforeChangeParent](#onbeforechangeparent)|Llamado por el marco cuando el elemento primario del panel que se va a cambiar. (Invalida [CPane::OnBeforeChangeParent](../../mfc/reference/cpane-class.md#onbeforechangeparent).)|  
|[CDockablePane::OnBeforeFloat](#onbeforefloat)|Lo llama el marco de trabajo cuando se trata de un panel a float. (Invalida [CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|  
|[CDockablePane::RemoveFromDefaultPaneDividier](#removefromdefaultpanedividier)|El marco de trabajo llama a este método cuando un panel se está desacoplado.|  
|[CDockablePane::ReplacePane](#replacepane)|Reemplaza el panel con un panel especificado.|  
|[CDockablePane::RestoreDefaultPaneDivider](#restoredefaultpanedivider)|El marco de trabajo llama a este método cuando se deserializa un panel para restaurar el divisor de paneles predeterminada.|  
|`CDockablePane::SaveState`|Se utiliza internamente.|  
|`CDockablePane::Serialize`|Serializa el panel. (Invalida `CBasePane::Serialize`).|  
|[CDockablePane::SetAutoHideMode](#setautohidemode)|Alterna entre visible el panel de acoplamiento y modo de ocultación automática.|  
|[CDockablePane::SetAutoHideParents](#setautohideparents)|Establece el botón de ocultación automática y el panel en la barra de herramientas Ocultar automáticamente.|  
|`CDockablePane::SetDefaultPaneDivider`|Se utiliza internamente.|  
|[CDockablePane::SetLastPercentInPaneContainer](#setlastpercentinpanecontainer)|Establece el porcentaje de espacio que ocupa un panel dentro de su contenedor.|  
|`CDockablePane::SetResizeMode`|Se utiliza internamente.|  
|[CDockablePane::SetRestoredDefaultPaneDivider](#setrestoreddefaultpanedivider)|Establece el divisor de paneles predeterminada restaurada.|  
|[CDockablePane::SetTabbedPaneRTC](#settabbedpanertc)|Establece la información de clase en tiempo de ejecución para una ventana con fichas que se crea cuando dos paneles acoplar juntos.|  
|[CDockablePane::ShowPane](#showpane)|Muestra u oculta un panel.|  
|[CDockablePane::Slide](#slide)|Muestra u oculta un panel con una animación deslizante que muestra solo cuando el panel está en modo de ocultación automática.|  
|[CDockablePane::ToggleAutoHide](#toggleautohide)|Modo de ocultación automática de conmutadores. (Invalida [CPane::ToggleAutoHide](../../mfc/reference/cpane-class.md#toggleautohide) .)|  
|[CDockablePane::UndockPane](#undockpane)|Desacopla un panel de la ventana de marco principal o un contenedor de ventana de marco reducido.|  
|`CDockablePane::UnSetAutoHideMode`|Se utiliza internamente. Para establecer el modo de ocultación automática, utilice [CDockablePane::SetAutoHideMode](#setautohidemode)|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDockablePane::CheckAutoHideCondition](#checkautohidecondition)|Determina si se oculta el panel de acoplamiento (en modo de ocultación automática).|  
|[CDockablePane::CheckStopSlideCondition](#checkstopslidecondition)|Determina cuándo un panel acoplable de ocultación automática debe detenerse deslizante.|  
|[CDockablePane::DrawCaption](#drawcaption)|Dibuja el título del panel acoplable (agarrador).|  
|[CDockablePane::OnPressButtons](#onpressbuttons)|Se llama cuando el usuario presiona un botón de título distinto de la `AFX_HTCLOSE` y `AFX_HTMAXBUTTON` botones.|  
|[CDockablePane::OnSlide](#onslide)|Llamado por el marco para representar el efecto de diapositiva de ocultación automática cuando el panel se muestra o se oculta.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDockablePane::m_bDisableAnimation](#m_bdisableanimation)|Especifica si se deshabilita la animación de ocultación automática del panel acoplable.|  
|[CDockablePane::m_bHideInAutoHideMode](#m_bhideinautohidemode)|Determina el comportamiento del panel cuando el panel está en modo de ocultación automática.|  
|[CDockablePane::m_nSlideSteps](#m_nslidesteps)|Especifica la velocidad de animación del panel cuando se muestran u ocultan cuando está en modo de ocultación automática.|  
  
## <a name="remarks"></a>Comentarios  
 `CDockablePane`implementa la funcionalidad siguiente:  
  
-   Acoplar un panel a una ventana de marco principal.  
  
-   Cambiar un panel a modo de ocultación automática.  
  
-   Adjuntar un panel a una ventana con fichas.  
  
-   Flotante un panel en una ventana de marco reducido.  
  
-   Acoplar un panel a otro panel es flotante en una ventana de marco reducido.  
  
-   Cambiar el tamaño de un panel.  
  
-   Cargar y guardar el estado de un panel acoplable.  
  
    > [!NOTE]
    >  La información de estado se guarda en el registro de Windows.  
  
-   Creación de un panel con o sin título. El título puede tener una etiqueta de texto y se puede rellenar con un degradado de color.  
  
-   Arrastrar un panel mientras se muestra el contenido del panel  
  
-   Arrastrar un panel al mostrar un rectángulo de arrastre.  
  
 Para usar un panel acoplable en la aplicación, derive la clase de panel de la `CDockablePane` clase. O bien incrustar el objeto derivado en el objeto de ventana de marco principal o en un objeto de ventana que controla la instancia del panel. A continuación, llame el [CDockablePane::Create](#create) método o el [CDockablePane::CreateEx](#createex) método al procesar el `WM_CREATE` mensaje en la ventana de marco principal. Por último, configure el objeto de panel mediante una llamada a [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking), [CBasePane::DockPane](../../mfc/reference/cbasepane-class.md#dockpane), o [CDockablePane::AttachToTabWnd](#attachtotabwnd).  
  
## <a name="customization-tips"></a>Sugerencias de personalización  
 Las sugerencias siguientes se aplican a `CDockablePane` objetos:  
  
-   Si se llama a [CDockablePane::AttachToTabWnd](#attachtotabwnd) para dos paneles acoplables, sin fichas, se devuelve un puntero a una ventana con fichas en la `ppTabbedControlBar` parámetro. Aún puede agregar pestañas a la ventana con fichas mediante el uso de este parámetro.  
  
-   El tipo de panel con fichas creado por [CDockablePane::AttachToTabWnd](#attachtotabwnd) viene determinado por la `CDockablePane` objeto en el `pTabControlBarAttachTo` parámetro. Puede llamar a [CDockablePane::SetTabbedPaneRTC](#settabbedpanertc) para establecer el tipo de panel con fichas que el `CDockablePane` va a crear. El tipo predeterminado es determinado por la `dwTabbedStyle` de [CDockablePane::Create](#create) al crear la `CDockablePane`. Si `dwTabbedStyle` es el tipo predeterminado es de AFX_CBRS_OUTLOOK_TABS [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md); si `dwTabbedStyle` es el tipo predeterminado es de AFX_CBRS_REGULAR_TABS [CTabbedPane clase](../../mfc/reference/ctabbedpane-class.md).  
  
-   Si desea acoplar un panel acoplable a otro, llame a la [CDockablePane::DockToWindow](#docktowindow) método. El panel original debe acoplarse en algún lugar antes de llamar a este método.  
  
-   La variable miembro [CDockablePane::m_bHideInAutoHideMode](#m_bhideinautohidemode) controles cómo se comportan los paneles acoplables Auto Ocultar modo cuando se llama a [CDockablePane::ShowPane](#showpane). Si se establece esta variable miembro en `TRUE`, se ocultarán los paneles acoplables y sus botones de ocultar automáticamente. En caso contrario, la entrada y salida se diapositiva.  
  
-   Animación de ocultación automática se puede deshabilitar estableciendo la [CDockablePane::m_bDisableAnimation](#m_bdisableanimation) la variable miembro que `TRUE`.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo configurar un `CDockablePane` objeto utilizando varios métodos en la `CDockablePane` clase. En el ejemplo se muestra cómo habilitar la opción Ocultar automáticamente todas las características del panel acoplable, habilitar el título o la barra de redimensionamiento, habilitar el modo de ocultación automática, mostrar el panel y animar un panel que se encuentra en modo de ocultación automática. Este fragmento de código forma parte de la [ejemplo de demostración de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo Nº&27;](../../mfc/codesnippet/cpp/cdockablepane-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo&#28;](../../mfc/codesnippet/cpp/cdockablepane-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxDockablePane.h  
  
##  <a name="attachtotabwnd"></a>CDockablePane::AttachToTabWnd  
 Adjunta el panel actual a un panel de destino, la creación de un panel con fichas.  
  
```  
virtual CDockablePane* AttachToTabWnd(
    CDockablePane* pTabControlBarAttachTo,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bSetActive= TRUE,  
    CDockablePane** ppTabbedControlBar = NULL);  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`pTabControlBarAttachTo`  
 Especifica el panel de destino que asocia el panel actual a. El panel de destino debe ser un panel acoplable.  
  
 [in] `dockMethod`  
 Especifica el método de acoplamiento.  
  
 [in] `bSetActive`  
 `TRUE`Para activar el panel con fichas después de la operación de adjuntar; de lo contrario, `FALSE`.  
  
 [out] `ppTabbedControlBar`  
 Contiene el panel con fichas que es el resultado de la operación de adjuntar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al panel actual, si no es un panel con fichas; de lo contrario, un puntero al panel con fichas que es el resultado de la operación de adjuntar. El valor devuelto es `NULL` si no se puede adjuntar el panel actual, o si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se asocia un panel acoplable a otro panel con este método, ocurre lo siguiente:  
  
1.  Las comprobaciones de marco de trabajo si el panel destino `pTabControlBarAttachTo` normal de acoplamiento panel o si se deriva de [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md).  
  
2.  Si el panel de destino es un panel con fichas, el marco de trabajo se le agrega el panel actual como una pestaña.  
  
3.  Si el panel de destino es un panel acoplable regular, el marco de trabajo crea un panel con fichas.  
  
    -   El marco llama `pTabControlBarAttachTo->CreateTabbedPane`. El estilo del nuevo panel con fichas depende del `m_pTabbedControlBarRTC` miembro. De forma predeterminada, este miembro se establece en la clase en tiempo de ejecución de [CTabbedPane](../../mfc/reference/ctabbedpane-class.md). Si se pasa el `AFX_CBRS_OUTLOOK_TABS` de estilo como el `dwTabbedStyle` parámetro para la [CDockablePane::Create](#create) método, el objeto de clase en tiempo de ejecución se establece en la clase en tiempo de ejecución de [CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md). Este miembro puede cambiar en cualquier momento para cambiar el estilo del nuevo panel.  
  
    -   Cuando este método crea un panel con fichas, el marco de trabajo reemplaza el puntero a `pTabControlBarAttachTo` (si el panel está acoplado o flotante en una ventana de marco de varias) con un puntero al nuevo panel con fichas.  
  
    -   El marco de trabajo agrega la `pTabControlBarAttachTo` panel al panel con fichas como la primera pestaña. El marco de trabajo, a continuación, agrega el panel actual como una segunda pestaña.  
  
4.  Si el panel actual se deriva `CBaseTabbedPane`, todas sus fichas se mueven a `pTabControlBarAttachTo` y se destruye el panel actual. Por lo tanto, tenga cuidado al llamar a este método, porque un puntero al panel actual puede ser válido cuando el método devuelve.  
  
 Si asocia un panel a otro al crear un diseño de acoplamiento, establezca `dockMethod` a `DM_SHOW`.  
  
 Debe acoplar el primer panel antes de adjuntar otro panel a él.  
  
##  <a name="calcfixedlayout"></a>CDockablePane::CalcFixedLayout  
 Devuelve el tamaño del rectángulo de panel.  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bStretch`  
 No usado.  
  
 [in] `bHorz`  
 No usado.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CSize` objeto que contiene el tamaño del rectángulo de panel.  
  
##  <a name="canacceptminiframe"></a>CDockablePane::CanAcceptMiniFrame  
 Determina si se puede acoplar el marco mínima especificado en el panel.  
  
```  
virtual BOOL CanAcceptMiniFrame(CPaneFrameWnd* pMiniFrame) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMiniFrame`  
 Puntero a un `CPaneFrameWnd` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si `pMiniFrame` puede ser acoplado al panel; de lo contrario, `FALSE`.  
  
##  <a name="canacceptpane"></a>CDockablePane::CanAcceptPane  
 Determina si el otro panel se puede acoplar el panel actual.  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Especifica el panel para acoplar el panel actual.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se puede acoplar el panel especificado a este panel; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método antes de un panel se acopla al panel actual.  
  
 Reemplace esta función en una clase derivada para habilitar o deshabilitar el acoplamiento a un panel específico.  
  
 De forma predeterminada, este método devuelve `TRUE` si `pBar` o su elemento primario es de tipo `CDockablePane`.  
  
##  <a name="canautohide"></a>CDockablePane::CanAutoHide  
 Determina si el panel puede ocultar automáticamente.  
  
```  
virtual BOOL CanAutoHide() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel puede ocultar automáticamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 `CDockablePane::CanAutoHide`Devuelve `FALSE` en cualquiera de las siguientes situaciones:  
  
-   El panel tiene ningún primario.  
  
-   El Administrador de acoplamiento no admite paneles de ocultación automática.  
  
-   El panel no está acoplado.  
  
##  <a name="canbeattached"></a>CDockablePane::CanBeAttached  
 Determina si se puede acoplar el panel actual a otro panel.  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se puede acoplar el panel acoplable a otro panel o la ventana de marco principal; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método devuelve siempre `TRUE`. Invalide este método en una clase derivada para habilitar o deshabilitar el acoplamiento sin llamar a [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).  
  
##  <a name="cdockablepane"></a>CDockablePane::CDockablePane  
 Construye e inicializa un [CDockablePane](../../mfc/reference/cdockablepane-class.md) objeto.  
  
```  
CDockablePane();
```  
  
### <a name="remarks"></a>Comentarios  
 Después de crear un objeto de panel acoplable, llame a [CDockablePane::Create](#create) o [CDockablePane::CreateEx](#createex) para crearlo.  
  
##  <a name="converttotabbeddocument"></a>CDockablePane::ConvertToTabbedDocument  
 Convierte uno o más paneles acoplables en documentos con fichas de MDI.  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bActiveTabOnly`  
 Al convertir un `CTabbedPane`, especifique `TRUE` para convertir sólo la pestaña activa. Especificar `FALSE` para convertir todas las fichas en el panel.  
  
##  <a name="checkautohidecondition"></a>CDockablePane::CheckAutoHideCondition  
 Determina si el panel de acoplamiento está oculto (también conocido como modo de ocultación automática).  
  
```  
virtual BOOL CheckAutoHideCondition();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se cumple la condición de ocultar; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo usa un temporizador para comprobar periódicamente si desea ocultar un panel acoplable de ocultación automática. El método devuelve `TRUE` cuando no está activo en el panel, el panel no cambia de tamaño y no es el puntero del mouse sobre el panel.  
  
 Si se cumplen todas las condiciones anteriores, el marco llama a [CDockablePane::Slide](#slide) para ocultar el panel.  
  
##  <a name="checkstopslidecondition"></a>CDockablePane::CheckStopSlideCondition  
 Determina cuándo un panel acoplable de ocultación automática debe detenerse deslizante.  
  
```  
virtual BOOL CheckStopSlideCondition(BOOL bDirection);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bDirection`  
 `TRUE`Si el panel está visible; `FALSE` si el panel está oculto.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se cumple la condición de detención; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un panel acoplable se establece en modo de ocultación automática, el marco de trabajo usa efectos deslizantes para mostrar u ocultar el panel. El marco de trabajo llama a esta función cuando se esté desplazando el panel. `CheckStopSlideCondition`Devuelve `TRUE` cuando el panel está totalmente visible o cuando se oculta completamente.  
  
 Invalide este método en una clase derivada para implementar los efectos de ocultación automática personalizado.  
  
##  <a name="copystate"></a>CDockablePane::CopyState  
 Copia el estado de un panel acoplable.  
  
```  
virtual void CopyState(CDockablePane* pOrgBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pOrgBar`  
 Un puntero a un panel acoplable.  
  
### <a name="remarks"></a>Comentarios  
 `CDockablePane::CopyState`copia el estado de `pOrgBar` al panel actual llamando a los métodos siguientes:  
  
- [CPane::CopyState](../../mfc/reference/cpane-class.md#copystate)  
  
- [CDockablePane::GetAHRestoredRect](#getahrestoredrect)  
  
- [CDockablePane::GetAHSlideMode](#getahslidemode)  
  
- [CDockablePane::GetLastPercentInPaneContainer](#getlastpercentinpanecontainer)  
  
- [CDockablePane::IsAutohideAllEnabled](#isautohideallenabled)  
  
##  <a name="create"></a>CDockablePane::Create  
 Crea el control de Windows y lo adjunta a la [CDockablePane](../../mfc/reference/cdockablepane-class.md) objeto.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszCaption,  
    CWnd* pParentWnd,  
    const RECT& rect,  
    BOOL bHasGripper,  
    UINT nID,  
    DWORD dwStyle,  
    DWORD dwTabbedStyle = AFX_CBRS_REGULAR_TABS,  
    DWORD dwControlBarStyle = AFX_DEFAULT_DOCKING_PANE_STYLE,  
    CCreateContext* pContext = NULL);

 
virtual BOOL Create(
    LPCTSTR lpszWindowName,  
    CWnd* pParentWnd,  
    CSize sizeDefault,  
    BOOL bHasGripper,  
    UINT nID,  
    DWORD dwStyle = WS_CHILD|WS_VISIBLE|CBRS_TOP|CBRS_HIDE_INPLACE,  
    DWORD dwTabbedStyle = AFX_CBRS_REGULAR_TABS,  
    DWORD dwControlBarStyle = AFX_DEFAULT_DOCKING_PANE_STYLE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszCaption`  
 Especifica el nombre de la ventana.  
  
 [in] [out]`pParentWnd`  
 Especifica la ventana primaria.  
  
 [in] `rect`  
 Especifica el tamaño y la posición de la ventana, en coordenadas de cliente `pParentWnd`.  
  
 [in] `bHasGripper`  
 `TRUE`Para crear el panel con un título; de lo contrario, `FALSE`.  
  
 [in] `nID`  
 Especifica el identificador de la ventana secundaria. Este valor debe ser único si desea guardar el estado de acoplamiento para este panel acoplable.  
  
 [in] `dwStyle`  
 Especifica los atributos de estilo de ventana.  
  
 [in] `dwTabbedStyle`  
 Especifica el estilo de una ventana con fichas que se crea cuando el usuario arrastra un panel en el título de este panel con fichas.  
  
 [in] `dwControlBarStyle`  
 Especifica los atributos de estilo adicionales.  
  
 [in] [out]`pContext`  
 Especifica el contexto de creación de la ventana.  
  
 [in] `lpszWindowName`  
 Especifica el nombre de la ventana.  
  
 [in] `sizeDefault`  
 Especifica el tamaño de la ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel acoplable se creó correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Crea un panel de Windows y lo adjunta a la `CDockablePane` objeto.  
  
 Si el `dwStyle` el estilo de ventana tiene la `CBRS_FLOAT_MULTI` marca, la ventana de marco reducido puede flotar con otros paneles de la ventana de marco reducido. De forma predeterminada, acoplar paneles sólo flotante individualmente.  
  
 Si el `dwTabbedStyle` parámetro tiene el `AFX_CBRS_OUTLOOK_TABS` especifica la marca, el panel crea paneles con pestañas de estilo Outlook cuando otro panel se adjunta a este panel mediante el [CDockablePane::AttachToTabWnd](#attachtotabwnd) método. De forma predeterminada, paneles acoplables crean fichas regulares del tipo [CTabbedPane](../../mfc/reference/ctabbedpane-class.md).  
  
##  <a name="createdefaultpanedivider"></a>CDockablePane::CreateDefaultPaneDivider  
 Crea un divisor predeterminado para el panel como fijarla en una ventana de marco.  
  
```  
static CPaneDivider* __stdcall CreateDefaultPaneDivider(
    DWORD dwAlignment,  
    CWnd* pParent,  
    CRuntimeClass* pSliderRTC = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwAlignment`  
 Especifica el lado del marco principal a la que el panel que se está acoplado. Si `dwAlignment` contiene el `CBRS_ALIGN_LEFT` o `CBRS_ALIGN_RIGHT` marca, este método crea una vertical ( `CPaneDivider::SS_VERT`) separador; en caso contrario, este método crea una horizontal ( `CPaneDivider::SS_HORZ`) divisor.  
  
 [in] `pParent`  
 Puntero al marco primario.  
  
 [in] `pSliderRTC`  
 No usado.  
  
### <a name="return-value"></a>Valor devuelto  
 Este método devuelve un puntero divisor recién creada, o `NULL` si se produce un error en la creación del divisor.  
  
### <a name="remarks"></a>Comentarios  
 `dwAlignment`puede ser cualquiera de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`CBRS_ALIGN_TOP`|El panel que se está acoplado a la parte superior del área cliente de una ventana de marco.|  
|`CBRS_ALIGN_BOTTOM`|El panel que se está acoplado a la parte inferior del área de cliente de una ventana de marco.|  
|`CBRS_ALIGN_LEFT`|El panel que se está acoplado en el lado izquierdo del área cliente de una ventana de marco.|  
|`CBRS_ALIGN_RIGHT`|El panel que se está acoplado a la derecha del área de cliente de una ventana de marco.|  
  
##  <a name="createex"></a>CDockablePane::CreateEx  
 Crea el control de Windows y lo adjunta a la [CDockablePane](../../mfc/reference/cdockablepane-class.md) objeto.  
  
```  
virtual BOOL CreateEx(
    DWORD dwStyleEx,  
    LPCTSTR lpszCaption,  
    CWnd* pParentWnd,  
    const RECT& rect,  
    BOOL bHasGripper,  
    UINT nID,  
    DWORD dwStyle,  
    DWORD dwTabbedStyle = AFX_CBRS_REGULAR_TABS,  
    DWORD dwControlBarStyle = AFX_DEFAULT_DOCKING_PANE_STYLE,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwStyleEx`  
 Especifica los atributos de estilo extendido de la nueva ventana.  
  
 [in] `lpszCaption`  
 Especifica el nombre de la ventana.  
  
 [in] [out]`pParentWnd`  
 Especifica la ventana primaria.  
  
 [in] `rect`  
 Especifica el tamaño y la posición de la ventana, en coordenadas de cliente `pParentWnd`.  
  
 [in] `bHasGripper`  
 `TRUE`Para crear el panel con un título; de lo contrario, `FALSE`.  
  
 [in] `nID`  
 Especifica el identificador de la ventana secundaria. Este valor debe ser único si desea guardar el estado de acoplamiento para este panel acoplable.  
  
 [in] `dwStyle`  
 Especifica los atributos de estilo de ventana.  
  
 [in] `dwTabbedStyle`  
 Especifica el estilo de una ventana con fichas que se crea cuando el usuario arrastra un panel en el título de este panel con fichas.  
  
 [in] `dwControlBarStyle`  
 Especifica los atributos de estilo adicionales.  
  
 [in] [out]`pContext`  
 Especifica el contexto de creación de la ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel acoplable se creó correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Crea un panel de Windows y lo adjunta a la `CDockablePane` objeto.  
  
 Si el `dwStyle` el estilo de ventana tiene la `CBRS_FLOAT_MULTI` marca, la ventana de marco reducido puede flotar con otros paneles de la ventana de marco reducido. De forma predeterminada, acoplar paneles sólo flotante individualmente.  
  
 Si el `dwTabbedStyle` parámetro tiene el `AFX_CBRS_OUTLOOK_TABS` especifica la marca, el panel crea paneles con pestañas de estilo Outlook cuando otro panel se adjunta a este panel mediante el [CDockablePane::AttachToTabWnd](#attachtotabwnd) método. De forma predeterminada, paneles acoplables crean fichas regulares del tipo [CTabbedPane](../../mfc/reference/ctabbedpane-class.md).  
  
##  <a name="createtabbedpane"></a>CDockablePane::CreateTabbedPane  
 Crea un panel con fichas en el panel actual.  
  
```  
virtual CTabbedPane* CreateTabbedPane();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El nuevo panel con fichas, o `NULL` si falla la operación de creación.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando se crea un panel con fichas para reemplazar este panel. Para obtener más información, consulte [CDockablePane::AttachToTabWnd](#attachtotabwnd).  
  
 Invalidación de este método en una clase derivada para personalizar cómo fichas se crean e inicializan.  
  
 El panel con fichas se crea según la información de clase en tiempo de ejecución almacenada en el `m_pTabbedControlBarRTC` miembro, que inicializa el [CDockablePane::CreateEx](#createex) método.  
  
##  <a name="dockpanecontainer"></a>CDockablePane::DockPaneContainer  
 En el panel se acopla un contenedor.  
  
```  
virtual BOOL DockPaneContainer(
    CPaneContainerManager& barContainerManager,  
    DWORD dwAlignment,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `barContainerManager`  
 Una referencia al administrador de contenedor del contenedor al que está acoplado.  
  
 [in] `dwAlignment`  
 `DWORD`que especifica el lado del panel al que se está acoplado el contenedor.  
  
 [in] `dockMethod`  
 No usado.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el contenedor se acopla correctamente al panel; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 `dwAlignment`puede ser cualquiera de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`CBRS_ALIGN_TOP`|El contenedor que se está acoplado a la parte superior del panel.|  
|`CBRS_ALIGN_BOTTOM`|El contenedor que se está acoplado a la parte inferior del panel.|  
|`CBRS_ALIGN_LEFT`|El contenedor que se está acoplado a la izquierda del panel.|  
|`CBRS_ALIGN_RIGHT`|El contenedor que se está acoplado a la derecha del panel.|  
  
##  <a name="dockpanestandard"></a>CDockablePane::DockPaneStandard  
 Un panel se acopla utilizando el esquema de acoplamiento (estándar).  
  
```  
virtual CPane* DockPaneStandard(BOOL& bWasDocked);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bWasDocked`  
 Cuando el método vuelve, este valor contiene `TRUE` si el panel se ha acoplado correctamente; de lo contrario, contiene `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el panel se acopla a una ventana con fichas, o si se ha creado una ventana con fichas como resultado de acoplamiento, este método devuelve un puntero a la ventana con fichas. Si el panel era correctamente acoplada, este método devuelve el `this` puntero. Si acoplamiento defectuosa, este método devuelve `NULL`.  
  
##  <a name="docktorecentpos"></a>CDockablePane::DockToRecentPos  
 Un panel se acopla a su posición de acoplamiento almacenado.  
  
```  
BOOL CDockablePane::DockToRecentPos();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel está acoplado correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Paneles acoplables almacenan información reciente de acoplamiento en una [CRecentDockSiteInfo](../../mfc/reference/crecentdocksiteinfo-class.md) objeto.  
  
##  <a name="docktowindow"></a>CDockablePane::DockToWindow  
 Un panel acoplable se acoplará a otro panel de acoplamiento.  
  
```  
virtual BOOL DockToWindow(
    CDockablePane* pTargetWindow,  
    DWORD dwAlignment,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`pTargetWindow`  
 Especifica el panel acoplable para acoplar este panel.  
  
 [in] `dwAlignment`  
 Especifica la alineación del panel de acoplamiento. Puede ser uno de los CBRS_ALIGN_LEFT, CBRS_ALIGN_TOP, CBRS_ALIGN_RIGHT, CBRS_ALIGN_BOTTOM o CBRS_ALIGN_ANY. (Definidos en afxres.h).  
  
 [in] `lpRect`  
 Especifica el rectángulo para el panel de acoplamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se acopla correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para acoplar un panel a otro panel con la alineación especificada por `dwAlignment`.  
  
##  <a name="drawcaption"></a>CDockablePane::DrawCaption  
 Dibuja el título (también denominado a agarrador) de un panel acoplable.  
  
```  
virtual void DrawCaption(
    CDC* pDC,  
    CRect rectCaption);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Representa el contexto de dispositivo usado para dibujar.  
  
 [in] `rectCaption`  
 Especifica el rectángulo delimitador del título del panel.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para dibujar el título de un panel acoplable.  
  
 Invalide este método en una clase derivada para personalizar la apariencia del título.  
  
##  <a name="enableautohideall"></a>CDockablePane::EnableAutohideAll  
 Habilita o deshabilita el modo de ocultación automática para este panel y para otros paneles en el contenedor.  
  
```  
void EnableAutohideAll(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para habilitar el ocultar automáticamente todas las características del panel acoplable; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un usuario mantiene el `Ctrl` clave y hace clic en el botón de anclaje para cambiar un panel a modo de ocultación automática, todos los demás paneles en el mismo contenedor también se cambió al modo de ocultación automática.  
  
 Llamar a este método con `bEnable` establecido en `FALSE` para deshabilitar esta característica para un determinado panel.  
  
##  <a name="enablegripper"></a>CDockablePane::EnableGripper  
 Muestra u oculta la leyenda (también denominada a agarrador).  
  
```  
virtual void EnableGripper(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para habilitar el título; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el marco de trabajo crea paneles acoplables, no tienen la **WS_STYLE** estilo de ventana, incluso si se especifica. Esto significa que el título del panel es un área no cliente controlada por el marco de trabajo, pero difiere de esta área de título de ventana estándar.  
  
 Puede mostrar u ocultar el título en cualquier momento. El marco de trabajo oculta la leyenda cuando se agrega un panel como una ficha en una ventana con fichas o flota un panel en una ventana de marco reducido.  
  
##  <a name="getahrestoredrect"></a>CDockablePane::GetAHRestoredRect  
 Especifica la posición del panel en modo de ocultación automática.  
  
```  
CRect GetAHRestoredRect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CRect` objeto que contiene la posición del panel cuando está en modo de ocultación automática.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getahslidemode"></a>CDockablePane::GetAHSlideMode  
 Recupera el modo de diapositiva de ocultación automática para el panel.  
  
```  
virtual UINT GetAHSlideMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `UINT` que especifica el modo de diapositiva de ocultación automática para el panel. El valor devuelto puede ser `AFX_AHSM_MOVE` o `AFX_AHSM_STRETCH`, pero sólo utiliza la implementación `AFX_AHSM_MOVE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getcaptionheight"></a>CDockablePane::GetCaptionHeight  
 Devuelve el alto, en píxeles, del título actual.  
  
```  
virtual int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El alto del título, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Alto del título es 0 si el título se ha ocultado mediante el [CDockablePane::EnableGripper](#enablegripper) método, o si el panel no tiene un título.  
  
##  <a name="getdefaultpanedivider"></a>CDockablePane::GetDefaultPaneDivider  
 Devuelve el divisor de paneles predeterminada para el contenedor del panel.  
  
```  
CPaneDivider* GetDefaultPaneDivider() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Válido [CPaneDivider](../../mfc/reference/cpanedivider-class.md) objeto si el panel acoplable está acoplado a la ventana de marco principal, o `NULL` si no se acopla el panel acoplable o si está flotando.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre los divisores de los paneles, consulte [CPaneDivider clase](../../mfc/reference/cpanedivider-class.md).  
  
##  <a name="getdockingstatus"></a>CDockablePane::GetDockingStatus  
 Determina la capacidad de un panel acoplado en función de la ubicación del puntero proporcionado.  
  
```  
virtual AFX_CS_STATUS GetDockingStatus(
    CPoint pt,  
    int nSensitivity);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pt`  
 La ubicación del puntero en coordenadas de pantalla.  
  
 [in] `nSensitivity`  
 La distancia, en píxeles, lejos del borde de un rectángulo el puntero debe habilitar el acoplamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores de estado siguientes:  
  
|Valor de `AFX_CS_STATUS`|Significado|  
|---------------------------|-------------|  
|`CS_NOTHING`|El puntero no está sobre un sitio de vinculación. El marco no acoplar el panel.|  
|`CS_DOCK_IMMEDIATELY`|El puntero se encuentra sobre el sitio de vinculación en el modo inmediato (el panel utiliza el `DT_IMMEDIATE` modo de acoplamiento). El marco de trabajo acopla el panel inmediatamente.|  
|`CS_DELAY_DOCK`|El puntero está sobre un sitio de vinculación que otro panel de acoplamiento o un borde del marco principal. El marco de trabajo acopla el panel después de un retraso. Vea la sección Comentarios para obtener más información acerca de este retraso.|  
|`CS_DELAY_DOCK_TO_TAB`|El puntero se encuentra sobre un sitio de vinculación que hace que el panel se acopla en una ventana con fichas. Esto se produce cuando el puntero se encuentra sobre el título de otro panel de acoplamiento o sobre el área de la ficha de un panel con fichas.|  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para controlar el acoplamiento de un panel flotante.  
  
 Barras de herramientas flotantes o acoplar paneles que usan la `DT_IMMEDIATE` acoplamiento modo, el marco de trabajo retrasa el comando acoplar para permitir al usuario mover la ventana fuera del área de cliente del marco primario antes de acoplamiento. La duración del retraso se mide en milisegundos y se controla mediante la [CDockingManager::m_nTimeOutBeforeToolBarDock](../../mfc/reference/cdockingmanager-class.md#m_ntimeoutbeforetoolbardock) miembro de datos... El valor predeterminado de [CDockingManager::m_nTimeOutBeforeToolBarDock](../../mfc/reference/cdockingmanager-class.md#m_ntimeoutbeforetoolbardock) es 200. Este comportamiento emula el comportamiento de acoplamiento [!INCLUDE[ofprword](../../mfc/reference/includes/ofprword_md.md)] 2007.  
  
 Para retrasar el acoplamiento de los Estados ( `CS_DELAY_DOCK` y `CS_DELAY_DOCK_TO_TAB`), el marco de trabajo no lleva a cabo acoplamiento hasta que el usuario suelta el botón del mouse. Si usa un panel de la `DT_STANDARD` acoplamiento modo, el marco de trabajo muestra un rectángulo en la ubicación de acoplamiento proyectada. Si usa un panel de la `DT_SMART` acoplamiento modo, el marco de trabajo muestra marcadores de acoplamiento inteligente y semitransparentes rectángulos en la ubicación de acoplamiento proyectada. Para especificar el modo de acoplamiento para el panel, llame a la [CBasePane::SetDockingMode](../../mfc/reference/cbasepane-class.md#setdockingmode) método. Para obtener más información acerca de acoplamiento inteligente, consulte [CDockingManager::GetSmartDockingParams](../../mfc/reference/cdockingmanager-class.md#getsmartdockingparams).  
  
##  <a name="getdragsensitivity"></a>CDockablePane::GetDragSensitivity  
 Devuelve la sensibilidad de arrastre de un panel acoplable.  
  
```  
static const CSize& GetDragSensitivity();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que contiene el ancho y el alto, en píxeles, de un rectángulo centrado en un punto de arrastre. La operación de arrastre no comienza hasta que el puntero del mouse se mueve fuera de este rectángulo.  
  
##  <a name="getlastpercentinpanecontainer"></a>CDockablePane::GetLastPercentInPaneContainer  
 Recupera el porcentaje de espacio que ocupa un panel en su contenedor ( [CPaneContainer clase](../../mfc/reference/cpanecontainer-class.md)).  
  
```  
int GetLastPercentInPaneContainer() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `int` que especifica el porcentaje de espacio que ocupa el panel en su contenedor.  
  
### <a name="remarks"></a>Comentarios  
 Este método se utiliza cuando el contenedor ajusta su diseño.  
  
##  <a name="gettabarea"></a>CDockablePane::GetTabArea  
 Recupera el área de la ficha del panel.  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectTabAreaTop`  
 `GetTabArea`rellena esta variable con el área de la ficha si se encuentran en la parte superior del panel de pestañas. Si las fichas se encuentran en la parte inferior del panel, esta variable se rellena con un rectángulo vacío.  
  
 [in] `rectTabAreaBottom`  
 `GetTabArea`rellena esta variable con el área de la ficha si se encuentran en la parte inferior del panel de pestañas. Si las fichas se encuentran en la parte superior del panel, esta variable se rellena con un rectángulo vacío.  
  
### <a name="remarks"></a>Comentarios  
 Este método sólo se utiliza en las clases derivadas de `CDockablePane` y tiene fichas. Para obtener más información, consulte [CTabbedPane::GetTabArea](../../mfc/reference/ctabbedpane-class.md#gettabarea) y [CMFCOutlookBar::GetTabArea](../../mfc/reference/cmfcoutlookbar-class.md#gettabarea).  
  
##  <a name="gettabbedpanertc"></a>CDockablePane::GetTabbedPaneRTC  
 Devuelve la información de clase en tiempo de ejecución acerca de una ventana con fichas que se crea cuando otro panel se acopla al panel actual.  
  
```  
CRuntimeClass* GetTabbedPaneRTC() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La información de clase en tiempo de ejecución para el panel acoplable.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para recuperar la información de clase en tiempo de ejecución para los paneles con fichas que se crean dinámicamente. Esto puede ocurrir cuando un usuario arrastra un panel con el título de otro panel, o si se llama a la [CDockablePane::AttachToTabWnd](#attachtotabwnd) método para crear mediante programación un panel con fichas de dos paneles acoplables.  
  
 Puede establecer la información de clase en tiempo de ejecución llamando a la [CDockablePane::SetTabbedPaneRTC](#settabbedpanertc) método.  
  
##  <a name="hasautohidemode"></a>CDockablePane::HasAutoHideMode  
 Especifica si un panel acoplable se puede cambiar a modo de ocultación automática.  
  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel acoplable se puede cambiar a modo de ocultación automática; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para deshabilitar el modo de ocultación automática para un panel acoplable específico.  
  
##  <a name="hittest"></a>CDockablePane::HitTest  
 Especifica la ubicación en un panel donde el usuario hace clic en un mouse.  
  
```  
virtual int HitTest(
    CPoint point,  
    BOOL bDetectCaption = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 Especifica el punto de prueba.  
  
 [in] `bDetectCaption`  
 `TRUE`Si `HTCAPTION` se debe devolver si el punto está en el título del panel; de lo contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los siguientes valores:  
  
- `HTNOWHERE`Si `point` no está en el panel acoplable.  
  
- `HTCLIENT`Si `point` está en el área de cliente del panel acoplable.  
  
- `HTCAPTION`Si `point` está en el área de título del panel acoplable.  
  
- `AFX_HTCLOSE`Si `point` está en el botón Cerrar.  
  
- `HTMAXBUTTON`Si `point` está en el botón de anclaje.  
  
##  <a name="isautohideallenabled"></a>CDockablePane::IsAutohideAllEnabled  
 Indica si el panel de acoplamiento y todos los demás paneles en el contenedor se pueden cambiar a modo de ocultación automática.  
  
```  
virtual BOOL IsAutohideAllEnabled() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel acoplable y todos los demás paneles en el contenedor, se pueden cambiar al modo de ocultación automática; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Un usuario habilita el modo de ocultación automática haciendo clic en el botón de anclaje acoplamiento mientras mantiene la **Ctrl** clave  
  
 Para habilitar o deshabilitar este comportamiento, llame a la [CDockablePane::EnableAutohideAll](#enableautohideall) método.  
  
##  <a name="isautohidemode"></a>CDockablePane::IsAutoHideMode  
 Determina si un panel está en modo de ocultación automática.  
  
```  
virtual BOOL IsAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel acoplable está en modo de ocultación automática; de lo contrario, `FALSE`.  
  
##  <a name="isdocked"></a>CDockablePane::IsDocked  
 Determina si se acopla el panel actual.  
  
```  
virtual BOOL IsDocked() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel acoplable no pertenece a una ventana de marco reducido o si está flotando en una ventana de marco reducido con otro panel. `FALSE`Si el panel es un elemento secundario de una ventana de marco reducido y no hay ningún otros paneles que pertenecen a la ventana de marco reducido.  
  
### <a name="remarks"></a>Comentarios  
 Para determinar si el panel está acoplado a la ventana de marco principal, llame a [CDockablePane::GetDefaultPaneDivider](#getdefaultpanedivider). Si el método devuelve un puntero no NULL, el panel está acoplado en la ventana de marco principal.  
  
##  <a name="ishideinautohidemode"></a>CDockablePane::IsHideInAutoHideMode  
 Determina el comportamiento de un panel que está en modo de ocultación automática si se muestra (u oculto) llamando a [CDockablePane::ShowPane](#showpane).  
  
```  
virtual BOOL IsHideInAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se debe ocultar el panel acoplable en modo de ocultación automática; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un panel acoplable está en modo de ocultación automática, comportamiento es diferente al llamar a `ShowPane` para ocultar o mostrar el panel. Este comportamiento se controla mediante el miembro estático [CDockablePane::m_bHideInAutoHideMode](#m_bhideinautohidemode). Si este miembro es `TRUE`, el panel acoplable y su barra de herramientas Ocultar automáticamente relacionados o el botón Ocultar automáticamente está oculta o se muestra cuando se llama a `ShowPane`. De lo contrario, se activa o desactiva el panel acoplable y siempre está visible su barra de herramientas Ocultar automáticamente relacionados o el botón Ocultar automáticamente.  
  
 Invalide este método en una clase derivada para cambiar el comportamiento predeterminado para los paneles individuales.  
  
 El valor predeterminado de `m_bHideInAutoHideMode` es `FALSE`.  
  
##  <a name="isinfloatingmultipaneframewnd"></a>CDockablePane::IsInFloatingMultiPaneFrameWnd  
 Especifica si el panel está en una ventana de marco de varios paneles ( [CMultiPaneFrameWnd clase](../../mfc/reference/cmultipaneframewnd-class.md)).  
  
```  
virtual BOOL IsInFloatingMultiPaneFrameWnd() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel está en una ventana de marco de varios paneles; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isresizable"></a>CDockablePane::IsResizable  
 Especifica si se puede cambiar el tamaño del panel.  
  
```  
virtual BOOL IsResizable() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se puede cambiar de tamaño; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, los paneles acoplables son redimensionables. Para evitar el cambio de tamaño, invalide este método en una clase derivada y devolver `FALSE`. Tenga en cuenta que un `FALSE` valor genera un error `ASSERT` en [CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane). Utilice [CDockingManager::AddPane](../../mfc/reference/cdockingmanager-class.md#addpane) en su lugar para acoplar un panel dentro de un marco primario.  
  
 Los paneles que no puede cambiarse ni pueden flotar ni entrar en modo de ocultación automática y siempre se encuentran en el borde exterior del marco primario.  
  
##  <a name="istablocationbottom"></a>CDockablePane::IsTabLocationBottom  
 Especifica si se encuentra en la parte superior o inferior del panel de pestañas.  
  
```  
virtual BOOL IsTabLocationBottom() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si las fichas se encuentran en la parte inferior del panel; `FALSE` si se encuentran en la parte superior del panel de pestañas.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [CTabbedPane::IsTabLocationBottom](../../mfc/reference/ctabbedpane-class.md#istablocationbottom).  
  
##  <a name="istracked"></a>CDockablePane::IsTracked  
 Especifica si el usuario mueve un panel.  
  
```  
BOOL IsTracked() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se mueve el panel; de lo contrario, `FALSE`.  
  
##  <a name="isvisible"></a>CDockablePane::IsVisible  
 Determina si está visible el panel actual.  
  
```  
virtual BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel acoplable está visible; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para determinar si un panel acoplable está visible. Puede utilizar este método en lugar de llamar [CWnd::IsWindowVisible](../../mfc/reference/cwnd-class.md#iswindowvisible) o pruebas para los `WS_VISIBLE` estilo. El estado de visibilidad devuelto depende de si el modo de ocultación automática está habilitado o deshabilitado y el valor de la [CDockablePane::IsHideInAutoHideMode](#ishideinautohidemode) propiedad.  
  
 Si el panel acoplable está en modo de ocultación automática y `IsHideInAutoHideMode` devuelve `FALSE` el estado de visibilidad es siempre `FALSE`.  
  
 Si el panel acoplable está en modo de ocultación automática y `IsHideInAutoHideMode` devuelve `TRUE` el estado de visibilidad depende del estado de visibilidad de la barra de herramientas Ocultar automáticamente relacionados.  
  
 Si el panel acoplable no está en modo de ocultación automática, el estado de visibilidad viene determinado por la [CBasePane::IsVisible](../../mfc/reference/cbasepane-class.md#isvisible) método.  
  
##  <a name="m_bdisableanimation"></a>CDockablePane::m_bDisableAnimation  
 Especifica si se deshabilita la animación de ocultación automática del panel acoplable.  
  
```  
AFX_IMPORT_DATA static BOOL m_bDisableAnimation;  
```  
  
##  <a name="m_bhideinautohidemode"></a>CDockablePane::m_bHideInAutoHideMode  
 Determina el comportamiento del panel cuando el panel está en modo de ocultación automática.  
  
```  
AFX_IMPORT_DATA static BOOL m_bHideInAutoHideMode;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este valor afecta a todos los paneles de acoplamiento en la aplicación.  
  
 Si establece este miembro en `TRUE`, paneles acoplables se ocultan o se muestran con sus botones y barras de herramientas Ocultar automáticamente relacionados cuando se llama a [CDockablePane::ShowPane](#showpane).  
  
 Si establece este miembro en `FALSE`, se activa o se desactiva cuando se llama a paneles acoplables [CDockablePane::ShowPane](#showpane).  
  
##  <a name="m_nslidesteps"></a>CDockablePane::m_nSlideSteps  
 Especifica la velocidad de animación del panel cuando está en modo de ocultación automática.  
  
```  
AFX_IMPORT_DATA static int m_nSlideSteps;  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener un efecto de animación más rápido, disminuir este valor. Para obtener un efecto de animación más lento, aumente este valor.  
  
##  <a name="onafterchangeparent"></a>CDockablePane::OnAfterChangeParent  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndOldParent`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onafterdockfromminiframe"></a>CDockablePane::OnAfterDockFromMiniFrame  
 Llamado por el marco de trabajo cuando se acopla una barra de acoplamiento flotante en una ventana de marco.  
  
```  
virtual void OnAfterDockFromMiniFrame();
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método no hace nada.  
  
##  <a name="onbeforechangeparent"></a>CDockablePane::OnBeforeChangeParent  
 El marco de trabajo llama a este método antes de que cambie al elemento primario del panel.  
  
```  
virtual void OnBeforeChangeParent(
    CWnd* pWndNewParent,  
    BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndNewParent`  
 Puntero a la nueva ventana primaria.  
  
 [in] `bDelay`  
 `BOOL`que especifica si se va a retrasar el recálculo del diseño de acoplamiento si el panel está desacoplado. Para obtener más información, consulte [CDockablePane::UndockPane](#undockpane).  
  
### <a name="remarks"></a>Comentarios  
 Si el panel está acoplado y el nuevo elemento primario no permitir el acoplamiento, este método desacopla el panel.  
  
 Si el panel se convierte en un documento con pestañas, este método almacena su posición de acoplamiento recientes. El marco de trabajo utiliza la posición de acoplamiento recientes para restaurar la posición del panel cuando se convierte a un estado acoplado.  
  
##  <a name="onbeforefloat"></a>CDockablePane::OnBeforeFloat  
 El marco de trabajo llama a este método antes de un panel transiciones a un estado flotante.  
  
```  
virtual BOOL OnBeforeFloat(
    CRect& rectFloat,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectFloat`  
 Especifica la posición y el tamaño del panel cuando se encuentra en un estado flotante.  
  
 [in] `dockMethod`  
 Especifica el método de acoplamiento. Consulte [CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane) para obtener una lista de valores posibles.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel puede flotar; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando se trata de un panel a float. Puede invalidar este método en una clase derivada si desea realizar cualquier procesamiento antes de que el panel de la flota.  
  
##  <a name="onpressbuttons"></a>CDockablePane::OnPressButtons  
 Se llama cuando el usuario presiona un botón de título distinto de la `AFX_HTCLOSE` y `AFX_HTMAXBUTTON` botones.  
  
```  
virtual void OnPressButtons(UINT nHit);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nHit`  
 Este parámetro no se utiliza.  
  
### <a name="remarks"></a>Comentarios  
 Si agrega un botón personalizado con el título de un panel acoplable, invalide este método para recibir notificaciones cuando el usuario presiona el botón.  
  
##  <a name="onslide"></a>CDockablePane::OnSlide  
 Llamado por el marco para animar el panel cuando está en modo de ocultación automática.  
  
```  
virtual void OnSlide(BOOL bSlideOut);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSlideOut`  
 `TRUE`para mostrar el panel; `FALSE` para ocultar el panel.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para implementar los efectos de ocultación automática personalizado.  
  
##  <a name="removefromdefaultpanedividier"></a>CDockablePane::RemoveFromDefaultPaneDividier  
 El marco de trabajo llama a este método cuando un panel se está desacoplado.  
  
```  
void RemoveFromDefaultPaneDividier();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método establece el divisor de forma predeterminada en `NULL` y quita el panel de su contenedor.  
  
##  <a name="replacepane"></a>CDockablePane::ReplacePane  
 Reemplaza el panel con un panel especificado.  
  
```  
BOOL ReplacePane(
    CDockablePane* pBarToReplaceWith,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bRegisterWithFrame = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBarToReplaceWith`  
 Un puntero a un panel acoplable.  
  
 [in] `dockMethod`  
 No usado.  
  
 [in] `bRegisterWithFrame`  
 Si `TRUE`, el nuevo panel está registrado con el administrador del elemento primario del antiguo panel de acoplamiento. El nuevo panel se inserta en el índice de la sección anterior en la lista de paneles que es mantenida por el Administrador de acoplamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el reemplazo se realiza correctamente; de lo contrario, `FALSE`.  
  
##  <a name="restoredefaultpanedivider"></a>CDockablePane::RestoreDefaultPaneDivider  
 Cuando se deserializa un panel, el marco de trabajo llama a este método para restaurar el divisor de paneles predeterminada.  
  
```  
void RestoreDefaultPaneDivider();
```  
  
### <a name="remarks"></a>Comentarios  
 El divisor de paneles predeterminada restaurada reemplaza el divisor de paneles predeterminada actual, si existe.  
  
##  <a name="setautohidemode"></a>CDockablePane::SetAutoHideMode  
 Alterna entre visible el panel de acoplamiento y el modo de ocultación automática.  
  
```  
virtual CMFCAutoHideBar* SetAutoHideMode(
    BOOL bMode,  
    DWORD dwAlignment,  
    CMFCAutoHideBar* pCurrAutoHideBar = NULL,  
    BOOL bUseTimer = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bMode`  
 `TRUE`Para habilitar el modo de ocultación automática; `FALSE` para habilitar el modo de acoplamiento regular.  
  
 [in] `dwAlignment`  
 Especifica la alineación del panel Crear Ocultar automáticamente.  
  
 [in] [out]`pCurrAutoHideBar`  
 Puntero a la barra de herramientas Ocultar automáticamente actual. Puede ser `NULL`.  
  
 [in] `bUseTimer`  
 Especifica si utilizar el efecto de ocultar automáticamente cuando el usuario cambia el panel a modo de ocultación automática o para ocultar el panel inmediatamente.  
  
### <a name="return-value"></a>Valor devuelto  
 La barra de herramientas Ocultar automáticamente como resultado de cambiar al modo de ocultación automática, o `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando un usuario hace clic en el botón de anclaje para cambiar el panel acoplable a modo de ocultación automática o al modo normal de acoplamiento.  
  
 Llamar a este método para pasar un panel acoplable al modo de ocultación automática mediante programación. El panel debe acoplarse a la ventana de marco principal ( [CDockablePane::GetDefaultPaneDivider](#getdefaultpanedivider) debe devolver un puntero válido a la [CPaneDivider](../../mfc/reference/cpanedivider-class.md)).  
  
##  <a name="setautohideparents"></a>CDockablePane::SetAutoHideParents  
 Establece el botón de ocultación automática y el panel en la barra de herramientas Ocultar automáticamente.  
  
```  
void SetAutoHideParents(
    CMFCAutoHideBar* pToolBar,  
    CMFCAutoHideButton* pBtn);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pToolBar`  
 Puntero a una barra de herramientas Ocultar automáticamente.  
  
 [in] `pBtn`  
 Puntero a un botón de ocultación automática.  
  
##  <a name="setlastpercentinpanecontainer"></a>CDockablePane::SetLastPercentInPaneContainer  
 Establece el porcentaje de espacio que ocupa un panel en su contenedor.  
  
```  
void SetLastPercentInPaneContainer(int n);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `n`  
 Un `int` que especifica el porcentaje de espacio que ocupa el panel en su contenedor.  
  
### <a name="remarks"></a>Comentarios  
 El marco ajusta el panel para utilizar el nuevo valor cuando se vuelve a calcular el diseño.  
  
##  <a name="setrestoreddefaultpanedivider"></a>CDockablePane::SetRestoredDefaultPaneDivider  
 Establece el divisor de paneles predeterminada restaurada.  
  
```  
void SetRestoredDefaultPaneDivider(HWND hRestoredSlider);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hRestoredSlider`  
 Identificador de un divisor del panel (control).  
  
### <a name="remarks"></a>Comentarios  
 Cuando se deserializa un panel, se obtiene un divisor de paneles predeterminada restaurada. Para obtener más información, consulte [CDockablePane::RestoreDefaultPaneDivider](#restoredefaultpanedivider).  
  
##  <a name="settabbedpanertc"></a>CDockablePane::SetTabbedPaneRTC  
 Establece la información de clase en tiempo de ejecución para una ventana con fichas que se crea cuando dos paneles acoplar juntos.  
  
```  
void SetTabbedPaneRTC(CRuntimeClass* pRTC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pRTC`  
 La información de clase en tiempo de ejecución para el panel con fichas.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para establecer la información de clase en tiempo de ejecución para los paneles con fichas que se crean dinámicamente. Esto puede ocurrir cuando un usuario arrastra un panel con el título de otro panel, o si se llama a la [CDockablePane::AttachToTabWnd](#attachtotabwnd) método para crear mediante programación un panel con fichas de dos paneles acoplables.  
  
 La clase en tiempo de ejecución de forma predeterminada se establece según el `dwTabbedStyle` parámetro de [CDockablePane::Create](#create) y [CDockablePane::CreateEx](#createex). Para personalizar los paneles con fichas nuevas, derive su clase de una de las clases siguientes:  
  
- [Clase CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
- [Clase CTabbedPane](../../mfc/reference/ctabbedpane-class.md)  
  
- [Clase CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md).  
  
 A continuación, llamar a este método con el puntero a su información de clase en tiempo de ejecución.  
  
##  <a name="showpane"></a>CDockablePane::ShowPane  
 Muestra u oculta un panel.  
  
```  
virtual void ShowPane(
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bShow`  
 `TRUE`para mostrar el panel; `FALSE` para ocultar el panel.  
  
 [in] `bDelay`  
 `TRUE`retraso de ajustar el diseño de acoplamiento; `FALSE` para ajustar el diseño de acoplamiento inmediatamente.  
  
 [in] `bActivate`  
 `TRUE`Para activar el panel cuando se muestra; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método en lugar de la [CWnd:: ShowWindow](../../mfc/reference/cwnd-class.md#showwindow) al mostrar u ocultar paneles acoplables.  
  
##  <a name="slide"></a>CDockablePane::Slide  
 Se anima un panel que está en modo de ocultación automática.  
  
```  
virtual void Slide(
    BOOL bSlideOut,  
    BOOL bUseTimer = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSlideOut`  
 `TRUE`para mostrar el panel; `FALSE` para ocultar el panel.  
  
 [in] `bUseTimer`  
 `TRUE`para mostrar u ocultar el panel con el efecto de ocultar automáticamente; `FALSE` para mostrar u ocultar el panel inmediatamente.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para animar un panel que está en modo de ocultación automática.  
  
 Este método usa la `CDockablePane::m_nSlideDefaultTimeOut` valor para determinar el tiempo de espera para el efecto de diapositiva. El valor predeterminado para el tiempo de espera es 1. Si personaliza el algoritmo de ocultación automática, modifique este miembro para cambiar el tiempo de espera.  
  
##  <a name="toggleautohide"></a>CDockablePane::ToggleAutoHide  
 Alterna el modo de ocultación automática y entre panel siempre visible.  
  
```  
virtual void ToggleAutoHide();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método alterna el modo de ocultación automática para el panel mediante una llamada a [CDockablePane::SetAutoHideMode](#setautohidemode).  
  
##  <a name="undockpane"></a>CDockablePane::UndockPane  
 Desacopla un panel de la ventana de marco principal o un contenedor de ventana de marco reducido.  
  
```  
virtual void UndockPane(BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bDelay`  
 `TRUE`retraso de calcular el diseño de acoplamiento; `FALSE` para volver a calcular el diseño de acoplamiento inmediatamente.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para desacoplar un panel de la ventana de marco principal o de un contenedor de ventana de marco múltiple (es decir, un panel que está flotando en una ventana de marco reducido único con otros paneles).  
  
 Debe desacoplar un panel antes de realizar cualquier operación externo que no sea realizada por el [CDockingManager](../../mfc/reference/cdockingmanager-class.md). Por ejemplo, debe desacoplar un panel para mover mediante programación desde una ubicación a otra.  
  
 El marco de trabajo desacoplará automáticamente paneles antes de que se destruyen.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CPane](../../mfc/reference/cpane-class.md)

