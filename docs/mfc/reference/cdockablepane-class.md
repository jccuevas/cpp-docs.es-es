---
title: CDockablePane (clase) | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-mfc
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
- CDockablePane [MFC], CDockablePane
- CDockablePane [MFC], AttachToTabWnd
- CDockablePane [MFC], CalcFixedLayout
- CDockablePane [MFC], CanAcceptMiniFrame
- CDockablePane [MFC], CanAcceptPane
- CDockablePane [MFC], CanAutoHide
- CDockablePane [MFC], CanBeAttached
- CDockablePane [MFC], ConvertToTabbedDocument
- CDockablePane [MFC], CopyState
- CDockablePane [MFC], Create
- CDockablePane [MFC], CreateDefaultPaneDivider
- CDockablePane [MFC], CreateEx
- CDockablePane [MFC], CreateTabbedPane
- CDockablePane [MFC], DockPaneContainer
- CDockablePane [MFC], DockPaneStandard
- CDockablePane [MFC], DockToRecentPos
- CDockablePane [MFC], DockToWindow
- CDockablePane [MFC], EnableAutohideAll
- CDockablePane [MFC], EnableGripper
- CDockablePane [MFC], GetAHRestoredRect
- CDockablePane [MFC], GetAHSlideMode
- CDockablePane [MFC], GetCaptionHeight
- CDockablePane [MFC], GetDefaultPaneDivider
- CDockablePane [MFC], GetDockingStatus
- CDockablePane [MFC], GetDragSensitivity
- CDockablePane [MFC], GetLastPercentInPaneContainer
- CDockablePane [MFC], GetTabArea
- CDockablePane [MFC], GetTabbedPaneRTC
- CDockablePane [MFC], HasAutoHideMode
- CDockablePane [MFC], HitTest
- CDockablePane [MFC], IsAutohideAllEnabled
- CDockablePane [MFC], IsAutoHideMode
- CDockablePane [MFC], IsDocked
- CDockablePane [MFC], IsHideInAutoHideMode
- CDockablePane [MFC], IsInFloatingMultiPaneFrameWnd
- CDockablePane [MFC], IsResizable
- CDockablePane [MFC], IsTabLocationBottom
- CDockablePane [MFC], IsTracked
- CDockablePane [MFC], IsVisible
- CDockablePane [MFC], OnAfterChangeParent
- CDockablePane [MFC], OnAfterDockFromMiniFrame
- CDockablePane [MFC], OnBeforeChangeParent
- CDockablePane [MFC], OnBeforeFloat
- CDockablePane [MFC], RemoveFromDefaultPaneDividier
- CDockablePane [MFC], ReplacePane
- CDockablePane [MFC], RestoreDefaultPaneDivider
- CDockablePane [MFC], SetAutoHideMode
- CDockablePane [MFC], SetAutoHideParents
- CDockablePane [MFC], SetLastPercentInPaneContainer
- CDockablePane [MFC], SetRestoredDefaultPaneDivider
- CDockablePane [MFC], SetTabbedPaneRTC
- CDockablePane [MFC], ShowPane
- CDockablePane [MFC], Slide
- CDockablePane [MFC], ToggleAutoHide
- CDockablePane [MFC], UndockPane
- CDockablePane [MFC], CheckAutoHideCondition
- CDockablePane [MFC], CheckStopSlideCondition
- CDockablePane [MFC], DrawCaption
- CDockablePane [MFC], OnPressButtons
- CDockablePane [MFC], OnSlide
- CDockablePane [MFC], m_bDisableAnimation
- CDockablePane [MFC], m_bHideInAutoHideMode
- CDockablePane [MFC], m_nSlideSteps
ms.assetid: e2495f4c-765f-48f9-a2e2-e45e47608d91
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91058da47a97098826939be2248d81ba657f3cbb
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078315"
---
# <a name="cdockablepane-class"></a>CDockablePane Class

Implementa un panel que se puede acoplar en un sitio de vinculación o incluir en un panel con fichas.

## <a name="syntax"></a>Sintaxis

```
class CDockablePane : public CPane
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CDockablePane::CDockablePane](#cdockablepane)|Construye e inicializa un objeto `CDockablePane`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDockablePane:: Attachtotabwnd](#attachtotabwnd)|Adjunta un panel a otro panel. Esto crea un panel con pestañas.|
|[CDockablePane::CalcFixedLayout](#calcfixedlayout)|Devuelve el tamaño del rectángulo de panel.|
|[CDockablePane::CanAcceptMiniFrame](#canacceptminiframe)|Determina si se puede acoplar el marco mini especificado en el panel.|
|[CDockablePane::CanAcceptPane](#canacceptpane)|Determina si se puede acoplar a otro panel al panel actual.|
|[CDockablePane::CanAutoHide](#canautohide)|Determina si el panel admite el modo de ocultación automática. (Invalida [CBasePane::CanAutoHide](../../mfc/reference/cbasepane-class.md#canautohide).)|
|[CDockablePane::CanBeAttached](#canbeattached)|Determina si se puede acoplar el panel actual a otro panel.|
|[CDockablePane::ConvertToTabbedDocument](#converttotabbeddocument)|Convierte uno o más paneles acoplables en documentos con fichas de MDI.|
|[CDockablePane::CopyState](#copystate)|Copia el estado de un panel acoplable.|
|[CDockablePane::Create](#create)|Crea el control de Windows y lo adjunta a la `CDockablePane` objeto.|
|[CDockablePane::CreateDefaultPaneDivider](#createdefaultpanedivider)|Crea un divisor de forma predeterminada para el panel como fijarla en una ventana de marco.|
|[CDockablePane:: CreateEx](#createex)|Crea el control de Windows y lo adjunta a la `CDockablePane` objeto.|
|[CDockablePane::CreateTabbedPane](#createtabbedpane)|Crea un panel con pestañas en el panel actual.|
|[CDockablePane::DockPaneContainer](#dockpanecontainer)|Acopla un contenedor en el panel.|
|[CDockablePane::DockPaneStandard](#dockpanestandard)|Acopla un panel mediante el uso de esquema de acoplamiento (estándar).|
|`CDockablePane::DockToFrameWindow`|Lo utiliza internamente. Para acoplar un panel, utilice [CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane) o [CDockablePane::DockToWindow](#docktowindow).|
|[CDockablePane::DockToRecentPos](#docktorecentpos)|Acopla un panel en su posición de acoplamiento reciente almacenado.|
|[CDockablePane::DockToWindow](#docktowindow)|Acopla un panel acoplable a otro panel de acoplamiento.|
|[CDockablePane::EnableAutohideAll](#enableautohideall)|Habilita o deshabilita el modo de ocultación automática para este panel junto con otros paneles en el contenedor.|
|[CDockablePane::EnableGripper](#enablegripper)|Muestra u oculta la leyenda (controles).|
|[CDockablePane::GetAHRestoredRect](#getahrestoredrect)|Especifica la posición del panel cuando está visible en modo de ocultación automática.|
|[CDockablePane::GetAHSlideMode](#getahslidemode)|Recupera el modo de diapositiva de ocultar automáticamente para el panel.|
|`CDockablePane::GetAutoHideButton`|Lo utiliza internamente.|
|`CDockablePane::GetAutoHideToolBar`|Lo utiliza internamente.|
|[CDockablePane::GetCaptionHeight](#getcaptionheight)|Devuelve el alto del título actual.|
|[CDockablePane::GetDefaultPaneDivider](#getdefaultpanedivider)|Devuelve el divisor del panel predeterminado para el contenedor del panel.|
|[CDockablePane::GetDockingStatus](#getdockingstatus)|Determina la capacidad de un panel para acoplar basándose en la ubicación del puntero proporcionado.|
|[CDockablePane::GetDragSensitivity](#getdragsensitivity)|Devuelve la sensibilidad de arrastre de un panel acoplable.|
|[CDockablePane::GetLastPercentInPaneContainer](#getlastpercentinpanecontainer)|Recupera el porcentaje de espacio que ocupa un panel dentro de su contenedor.|
|[CDockablePane::GetTabArea](#gettabarea)|Recupera el área de pestañas para el panel.|
|[CDockablePane::GetTabbedPaneRTC](#gettabbedpanertc)|Devuelve la información de clase en tiempo de ejecución acerca de una ventana con pestañas que se crea al otro panel se acopla al panel actual.|
|[CDockablePane::HasAutoHideMode](#hasautohidemode)|Especifica si un panel acoplable se puede cambiar al modo de ocultación automática.|
|[CDockablePane::HitTest](#hittest)|Especifica la ubicación específica en un panel donde el usuario hace clic del mouse.|
|`CDockablePane::IsAccessibilityCompatible`|Lo utiliza internamente.|
|[CDockablePane::IsAutohideAllEnabled](#isautohideallenabled)|Indica si el panel de acoplamiento y todos los demás paneles en el contenedor se pueden poner en modo de ocultación automática.|
|[CDockablePane::IsAutoHideMode](#isautohidemode)|Determina si un panel está en modo de ocultación automática.|
|`CDockablePane::IsChangeState`|Lo utiliza internamente.|
|[CDockablePane::IsDocked](#isdocked)|Determina si se acopla el panel actual.|
|[CDockablePane::IsHideInAutoHideMode](#ishideinautohidemode)|Determina el comportamiento de un panel que está en modo de ocultación automática si se muestra (u oculto) mediante una llamada a `ShowPane`.|
|[CDockablePane::IsInFloatingMultiPaneFrameWnd](#isinfloatingmultipaneframewnd)|Especifica si el panel está en una ventana de marco de varios paneles.|
|[CDockablePane::IsResizable](#isresizable)|Especifica si se puede cambiar el tamaño del panel.|
|[CDockablePane::IsTabLocationBottom](#istablocationbottom)|Especifica si se encuentran en la parte superior o inferior del panel de pestañas.|
|[CDockablePane::IsTracked](#istracked)|Especifica si el usuario arrastra un panel.|
|[CDockablePane::IsVisible](#isvisible)|Determina si está visible el panel actual.|
|[CDockablePane:: Loadstate](#loadstate)|Lo utiliza internamente.|
|[CDockablePane::OnAfterChangeParent](#onafterchangeparent)|Lo llama el marco de trabajo cuando ha cambiado el elemento primario de un panel. (Invalida [CPane::OnAfterChangeParent](../../mfc/reference/cpane-class.md#onafterchangeparent).)|
|[CDockablePane::OnAfterDockFromMiniFrame](#onafterdockfromminiframe)|Lo llama el marco de trabajo cuando se acopla una barra de acoplamiento flotante en una ventana de marco.|
|[CDockablePane::OnBeforeChangeParent](#onbeforechangeparent)|Lo llama el marco cuando el elemento primario del panel que se va a cambiar. (Invalida [CPane::OnBeforeChangeParent](../../mfc/reference/cpane-class.md#onbeforechangeparent).)|
|[CDockablePane::OnBeforeFloat](#onbeforefloat)|Lo llama el marco cuando un panel se acerca a float. (Invalida [CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|
|[CDockablePane:: Removefromdefaultpanedividier](#removefromdefaultpanedividier)|El marco llama a este método cuando se se desacople un panel.|
|[CDockablePane::ReplacePane](#replacepane)|Reemplaza el panel con un panel especificado.|
|[CDockablePane::RestoreDefaultPaneDivider](#restoredefaultpanedivider)|El marco llama a este método como un panel es deserializar para restaurar el divisor del panel de forma predeterminada.|
|`CDockablePane::SaveState`|Lo utiliza internamente.|
|`CDockablePane::Serialize`|Serializa el panel. (Invalida `CBasePane::Serialize`).|
|[CDockablePane::SetAutoHideMode](#setautohidemode)|Alterna entre visible el panel de acoplamiento y el modo de ocultación automática.|
|[CDockablePane::SetAutoHideParents](#setautohideparents)|Establece el botón de ocultación automática y la barra de herramientas de ocultación automática para el panel.|
|`CDockablePane::SetDefaultPaneDivider`|Lo utiliza internamente.|
|[CDockablePane::SetLastPercentInPaneContainer](#setlastpercentinpanecontainer)|Establece el porcentaje de espacio que ocupa un panel dentro de su contenedor.|
|`CDockablePane::SetResizeMode`|Lo utiliza internamente.|
|[CDockablePane::SetRestoredDefaultPaneDivider](#setrestoreddefaultpanedivider)|Establece el divisor del panel predeterminado restablecido.|
|[CDockablePane:: Settabbedpanertc](#settabbedpanertc)|Establece la información de clase en tiempo de ejecución para una ventana con pestañas que se crea cuando dos paneles de acoplamiento entre sí.|
|[CDockablePane::ShowPane](#showpane)|Muestra u oculta un panel.|
|[CDockablePane::Slide](#slide)|Muestra u oculta un panel con una animación deslizante que muestra solo cuando el panel está en modo de ocultación automática.|
|[CDockablePane::ToggleAutoHide](#toggleautohide)|Modo de ocultación automática de conmutadores. (Invalida [CPane::ToggleAutoHide](../../mfc/reference/cpane-class.md#toggleautohide) .)|
|[CDockablePane::UndockPane](#undockpane)|Desacopla un panel desde la ventana de marco principal o un contenedor de la ventana de marco reducido.|
|`CDockablePane::UnSetAutoHideMode`|Lo utiliza internamente. Para establecer el modo de ocultación automática, use [CDockablePane::SetAutoHideMode](#setautohidemode)|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CDockablePane::CheckAutoHideCondition](#checkautohidecondition)|Determina si se oculta el panel de acoplamiento (en modo de ocultación automática).|
|[CDockablePane::CheckStopSlideCondition](#checkstopslidecondition)|Determina cuándo debe dejar de un panel de acoplamiento de ocultación automática deslizante.|
|[CDockablePane::DrawCaption](#drawcaption)|Dibuja el título de panel de acoplamiento (controles).|
|[CDockablePane::OnPressButtons](#onpressbuttons)|Se llama cuando el usuario presiona un botón de título que no sean los botones AFX_HTCLOSE y AFX_HTMAXBUTTON.|
|[CDockablePane::OnSlide](#onslide)|Lo llama el marco de trabajo para representar el efecto de diapositiva de ocultación automática cuando el panel se muestra o se oculta.|

### <a name="data-members"></a>Miembros de datos

|nombre|Descripción|
|----------|-----------------|
|[CDockablePane::m_bDisableAnimation](#m_bdisableanimation)|Especifica si se deshabilita la animación de ocultación automática del panel acoplable.|
|[CDockablePane::m_bHideInAutoHideMode](#m_bhideinautohidemode)|Determina el comportamiento del panel cuando el panel está en modo de ocultación automática.|
|[CDockablePane::m_nSlideSteps](#m_nslidesteps)|Especifica la velocidad de animación del panel al que se va a mostrar u ocultar cuando está en modo de ocultación automática.|

## <a name="remarks"></a>Comentarios

`CDockablePane` implementa la funcionalidad siguiente:

- Acoplar un panel a una ventana de marco principal.

- Cambiar un panel a modo de ocultación automática.

- Adjuntar un panel a una ventana con pestañas.

- Flotante a un panel en una ventana de marco reducido.

- Acoplar un panel a otro panel está flotando en una ventana de marco reducido.

- Cambiar el tamaño de un panel.

- Cargar y guardar el estado de un panel acoplable.

    > [!NOTE]
    >  La información de estado se guarda en el registro de Windows.

- Creación de un panel con o sin un título. El título puede tener una etiqueta de texto y se puede rellenar con un degradado de color.

- Arrastrar un panel al mostrar el contenido del panel

- Al arrastrar un panel al mostrar un rectángulo de arrastre.

Para usar un panel acoplable en la aplicación, derive la clase de panel de la `CDockablePane` clase. O bien incrustar el objeto derivado en el objeto de ventana de marco principal o en un objeto window que controla la instancia de su panel. A continuación, llame a la [CDockablePane::Create](#create) método o la [CDockablePane:: CreateEx](#createex) método al procesar el mensaje WM_CREATE en la ventana de marco principal. Por último, establezca el objeto del panel mediante una llamada a [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking), [cbasepane:: Dockpane](../../mfc/reference/cbasepane-class.md#dockpane), o [CDockablePane:: Attachtotabwnd](#attachtotabwnd).

## <a name="customization-tips"></a>Sugerencias de personalización

Las sugerencias siguientes se aplican a `CDockablePane` objetos:

- Si se llama a [CDockablePane:: Attachtotabwnd](#attachtotabwnd) para dos paneles acoplables, sin fichas, se devolverá un puntero a una ventana con pestañas en el *ppTabbedControlBar* parámetro. Aún puede agregar pestañas a la ventana con pestañas mediante el uso de este parámetro.

- El tipo de panel con pestañas que se crea mediante [CDockablePane:: Attachtotabwnd](#attachtotabwnd) viene determinada por la `CDockablePane` objeto en el *pTabControlBarAttachTo* parámetro. Puede llamar a [CDockablePane:: Settabbedpanertc](#settabbedpanertc) para establecer el tipo de panel con pestañas que el `CDockablePane` va a crear. El tipo predeterminado viene determinado por la `dwTabbedStyle` de [CDockablePane::Create](#create) cuando crea el `CDockablePane`. Si *dwTabbedStyle* es el tipo predeterminado es de AFX_CBRS_OUTLOOK_TABS [CMFCOutlookBar (clase)](../../mfc/reference/cmfcoutlookbar-class.md); si *dwTabbedStyle* es el tipo predeterminado AFX_CBRS_REGULAR_TABS es [ CTabbedPane (clase)](../../mfc/reference/ctabbedpane-class.md).

- Si desea acoplar un panel acoplable a otro, llame a la [CDockablePane::DockToWindow](#docktowindow) método. El panel original debe estar acoplado en algún lugar antes de llamar a este método.

- La variable miembro [CDockablePane::m_bHideInAutoHideMode](#m_bhideinautohidemode) controles cómo se comportan los paneles acoplables Auto Ocultar modo cuando se llama a [CDockablePane::ShowPane](#showpane). Si esta variable de miembro se establece en TRUE, se ocultarán los paneles acoplables y sus botones de ocultar automáticamente. En caso contrario, aparezca de entrada y salida.

- Animación de ocultación automática se puede deshabilitar estableciendo la [CDockablePane::m_bDisableAnimation](#m_bdisableanimation) variable miembro como TRUE.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo configurar un `CDockablePane` objeto mediante distintos métodos en el `CDockablePane` clase. El ejemplo muestra cómo habilitar la opción Ocultar automáticamente todas las características del panel acoplable, habilitar el título o la barra de redimensionamiento, habilitar el modo de ocultación automática, mostrar el panel y animar un panel que está en modo de ocultación automática. Este fragmento de código forma parte de la [ejemplo de demostración de Visual Studio](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#27](../../mfc/codesnippet/cpp/cdockablepane-class_1.cpp)]
[!code-cpp[NVC_MFC_VisualStudioDemo#28](../../mfc/codesnippet/cpp/cdockablepane-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxDockablePane.h

##  <a name="attachtotabwnd"></a>  CDockablePane:: Attachtotabwnd

El panel actual se asocia a un panel de destino, la creación de un panel con pestañas.

```
virtual CDockablePane* AttachToTabWnd(
    CDockablePane* pTabControlBarAttachTo,
    AFX_DOCK_METHOD dockMethod,
    BOOL bSetActive= TRUE,
    CDockablePane** ppTabbedControlBar = NULL);
```

### <a name="parameters"></a>Parámetros

*pTabControlBarAttachTo*<br/>
[in, out] Especifica el panel de destino que asocia el panel actual a. El panel de destino debe ser un panel acoplable.

*dockMethod*<br/>
[in] Especifica el método de acoplamiento.

*bSetActive*<br/>
[in] TRUE para activar el panel con pestañas después de la operación de adjuntar; en caso contrario, FALSE.

*ppTabbedControlBar*<br/>
[out] Contiene el panel con pestañas que da como resultado de la operación de adjuntar.

### <a name="return-value"></a>Valor devuelto

Un puntero al panel actual, si no es un panel con pestañas; en caso contrario, un puntero en el panel con pestañas que da como resultado de la operación de adjuntar. El valor devuelto es NULL si no se puede adjuntar el panel actual, o si se produce un error.

### <a name="remarks"></a>Comentarios

Cuando se adjunta un panel acoplable a otro panel con este método, ocurre lo siguiente:

1. Las comprobaciones de marco de trabajo si el panel destino *pTabControlBarAttachTo* normal de acoplamiento panel o si se deriva [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md).

1. Si el panel de destino es un panel con pestañas, el marco de trabajo le agrega el panel actual como una pestaña.

1. Si el panel de destino es un panel acoplable regular, el marco de trabajo crea un panel con pestañas.

   - Las llamadas de framework `pTabControlBarAttachTo->CreateTabbedPane`. El estilo del nuevo panel con pestañas depende el `m_pTabbedControlBarRTC` miembro. De forma predeterminada, este miembro está establecido en la clase en tiempo de ejecución de [CTabbedPane](../../mfc/reference/ctabbedpane-class.md). Si se pasa como el estilo de AFX_CBRS_OUTLOOK_TABS el *dwTabbedStyle* parámetro para el [CDockablePane::Create](#create) método, el objeto de clase en tiempo de ejecución se establece en la clase en tiempo de ejecución de [ CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md). Este miembro puede cambiar en cualquier momento para cambiar el estilo del nuevo panel.

   - Cuando este método crea un panel con pestañas, el marco de trabajo reemplaza el puntero a *pTabControlBarAttachTo* (si el panel está acoplado o flotante en una ventana de marco reducido el multi) con un puntero al nuevo panel con pestañas.

   - El marco de trabajo agrega los *pTabControlBarAttachTo* hasta el panel con pestañas, como la primera pestaña. El marco de trabajo, a continuación, agrega el panel actual como una segunda pestaña.

1. Si el panel actual se deriva `CBaseTabbedPane`, todas sus pestañas se mueven a *pTabControlBarAttachTo* y se destruye el panel actual. Por lo tanto, tenga cuidado al llamar a este método, porque un puntero al panel actual puede no ser válido cuando el método devuelve.

Si adjunta un panel a otro al crear un diseño de acoplamiento, establecer `dockMethod` a DM_SHOW.

Debe acoplar el primer panel antes de conectar otro panel a él.

##  <a name="calcfixedlayout"></a>  CDockablePane::CalcFixedLayout

Devuelve el tamaño del rectángulo de panel.

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parámetros

*bStretch*<br/>
[in] No se utiliza.

*bHorz*<br/>
[in] No se utiliza.

### <a name="return-value"></a>Valor devuelto

Un `CSize` objeto que contiene el tamaño del rectángulo de panel.

##  <a name="canacceptminiframe"></a>  CDockablePane::CanAcceptMiniFrame

Determina si se puede acoplar el marco reducido especificado en el panel.

```
virtual BOOL CanAcceptMiniFrame(CPaneFrameWnd* pMiniFrame) const;
```

### <a name="parameters"></a>Parámetros

*pMiniFrame*<br/>
[in] Puntero a un `CPaneFrameWnd` objeto.

### <a name="return-value"></a>Valor devuelto

TRUE si *pMiniFrame* se puede acoplar al panel; en caso contrario, FALSE.

##  <a name="canacceptpane"></a>  CDockablePane::CanAcceptPane

Determina si se puede acoplar a otro panel al panel actual.

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
[in] Especifica el panel para acoplar el panel actual.

### <a name="return-value"></a>Valor devuelto

TRUE si se puede acoplar el panel especificado a este panel; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

El marco llama a este método antes de un panel se ancla al panel actual.

Reemplace esta función en una clase derivada para habilitar o deshabilitar el acoplamiento a un panel específico.

De forma predeterminada, este método devuelve TRUE si *pBar* o su elemento primario es de tipo `CDockablePane`.

##  <a name="canautohide"></a>  CDockablePane::CanAutoHide

Determina si el panel puede ocultar automáticamente.

```
virtual BOOL CanAutoHide() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el panel puede ocultar automáticamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

`CDockablePane::CanAutoHide` Devuelve FALSE en cualquiera de las situaciones siguientes:

- El panel no tiene ningún elemento primario.

- El Administrador de acoplamiento no permite a los paneles de ocultación automática.

- No se acopla el panel.

##  <a name="canbeattached"></a>  CDockablePane::CanBeAttached

Determina si se puede acoplar el panel actual a otro panel.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si se puede acoplar el panel acoplable a otro panel o a la ventana de marco principal; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método siempre devuelve TRUE. Invalide este método en una clase derivada para habilitar o deshabilitar el acoplamiento sin llamar a [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).

##  <a name="cdockablepane"></a>  CDockablePane::CDockablePane

Crea e inicializa un [CDockablePane](../../mfc/reference/cdockablepane-class.md) objeto.

```
CDockablePane();
```

### <a name="remarks"></a>Comentarios

Después de construir un objeto de panel acoplable, llame a [CDockablePane::Create](#create) o [CDockablePane:: CreateEx](#createex) para crearlo.

##  <a name="converttotabbeddocument"></a>  CDockablePane::ConvertToTabbedDocument

Convierte uno o más paneles acoplables en documentos con fichas de MDI.

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>Parámetros

*bActiveTabOnly*<br/>
[in] Al convertir un `CTabbedPane`, especifique "true" para convertir sólo la pestaña activa. Especifique FALSE para convertir todas las pestañas en el panel.

##  <a name="checkautohidecondition"></a>  CDockablePane::CheckAutoHideCondition

Determina si el panel de acoplamiento está oculto (también conocido como modo de ocultación automática).

```
virtual BOOL CheckAutoHideCondition();
```

### <a name="return-value"></a>Valor devuelto

TRUE si se cumple la condición de ocultar; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

El marco de trabajo usa un temporizador para comprobar periódicamente si desea ocultar un panel acoplable de ocultar automáticamente. El método devuelve TRUE cuando el panel no está activo, el panel no cambia de tamaño y el puntero del mouse no está encima del panel.

Si se cumplen todas las condiciones anteriores, el marco llama a [CDockablePane::Slide](#slide) para ocultar el panel.

##  <a name="checkstopslidecondition"></a>  CDockablePane::CheckStopSlideCondition

Determina cuándo debe dejar de un panel de acoplamiento de ocultación automática deslizante.

```
virtual BOOL CheckStopSlideCondition(BOOL bDirection);
```

### <a name="parameters"></a>Parámetros

*bDirection*<br/>
[in] TRUE si el panel está visible; FALSE si el panel está oculto.

### <a name="return-value"></a>Valor devuelto

TRUE si se cumple la condición de detención; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Cuando un panel acoplable se establece en modo de ocultación automática, el marco usa efectos deslizantes para mostrar u ocultar el panel. El marco de trabajo llama a esta función cuando se esté desplazando el panel. `CheckStopSlideCondition` Devuelve TRUE cuando el panel está totalmente visible o cuando está completamente oculta.

Invalide este método en una clase derivada para implementar los efectos personalizados de ocultar automáticamente.

##  <a name="copystate"></a>  CDockablePane::CopyState

Copia el estado de un panel acoplable.

```
virtual void CopyState(CDockablePane* pOrgBar);
```

### <a name="parameters"></a>Parámetros

*pOrgBar*<br/>
[in] Un puntero a un panel acoplable.

### <a name="remarks"></a>Comentarios

`CDockablePane::CopyState` copia el estado de *pOrgBar* al panel actual mediante una llamada a los métodos siguientes:

- [CPane::CopyState](../../mfc/reference/cpane-class.md#copystate)

- [CDockablePane::GetAHRestoredRect](#getahrestoredrect)

- [CDockablePane::GetAHSlideMode](#getahslidemode)

- [CDockablePane::GetLastPercentInPaneContainer](#getlastpercentinpanecontainer)

- [CDockablePane::IsAutohideAllEnabled](#isautohideallenabled)

##  <a name="create"></a>  CDockablePane::Create

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

*lpszCaption*<br/>
[in] Especifica el nombre de la ventana.

*pParentWnd*<br/>
[in, out] Especifica la ventana primaria.

*Rect*<br/>
[in] Especifica el tamaño y posición de la ventana, en coordenadas de cliente de *pParentWnd*.

*bHasGripper*<br/>
[in] TRUE para crear el panel con un título; en caso contrario, FALSE.

*nID*<br/>
[in] Especifica el identificador de la ventana secundaria. Este valor debe ser único si desea guardar el estado de acoplamiento para este panel de acoplamiento.

*dwStyle*<br/>
[in] Especifica los atributos de estilo de ventana.

*dwTabbedStyle*<br/>
[in] Especifica el estilo de una ventana con pestañas que se crea cuando el usuario arrastra un panel en el título de este panel con pestañas.

*dwControlBarStyle*<br/>
[in] Especifica los atributos de estilo adicionales.

*pContext*<br/>
[in, out] Especifica el contexto de creación de la ventana.

*lpszWindowName*<br/>
[in] Especifica el nombre de la ventana.

*sizeDefault*<br/>
[in] Especifica el tamaño de la ventana.

### <a name="return-value"></a>Valor devuelto

TRUE si el panel acoplable se haya creado correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Crea un panel de Windows y lo adjunta a la `CDockablePane` objeto.

Si el *dwStyle* estilo de ventana tiene la marca CBRS_FLOAT_MULTI, la ventana de marco reducido puede flotar con otros paneles en la ventana de marco reducido. De forma predeterminada, acoplar paneles sólo flotante individualmente.

Si el *dwTabbedStyle* parámetro tiene el indicador AFX_CBRS_OUTLOOK_TABS especificado, el panel crea paneles con pestañas de estilo de Outlook cuando otro panel está asociado a este panel con el [CDockablePane:: Attachtotabwnd](#attachtotabwnd) método. De forma predeterminada, los paneles acoplables crean paneles con pestañas regulares del tipo [CTabbedPane](../../mfc/reference/ctabbedpane-class.md).

##  <a name="createdefaultpanedivider"></a>  CDockablePane::CreateDefaultPaneDivider

Crea un divisor de forma predeterminada para el panel como fijarla en una ventana de marco.

```
static CPaneDivider* __stdcall CreateDefaultPaneDivider(
    DWORD dwAlignment,
    CWnd* pParent,
    CRuntimeClass* pSliderRTC = NULL);
```

### <a name="parameters"></a>Parámetros

*dwAlignment*<br/>
[in] Especifica el lado del marco principal a la que se está acoplando el panel. Si *dwAlignment* contiene la marca CBRS_ALIGN_LEFT o CBRS_ALIGN_RIGHT, este método crea una vertical (`CPaneDivider::SS_VERT`) separador; en caso contrario, este método crea una horizontal (`CPaneDivider::SS_HORZ`) divisor.

*pParent*<br/>
[in] Puntero al marco primario.

*pSliderRTC*<br/>
[in] No se utiliza.

### <a name="return-value"></a>Valor devuelto

Este método devuelve un puntero al divisor recién creada, o NULL si se produce un error en la creación del divisor.

### <a name="remarks"></a>Comentarios

*dwAlignment* puede ser cualquiera de los siguientes valores:

|Valor|Descripción|
|-----------|-----------------|
|CBRS_ALIGN_TOP|El panel que se está acoplado a la parte superior del área de cliente de una ventana de marco.|
|CBRS_ALIGN_BOTTOM|El panel que se está acoplado a la parte inferior del área de cliente de una ventana de marco.|
|CBRS_ALIGN_LEFT|El panel que se está acoplado a la izquierda del área de cliente de una ventana de marco.|
|CBRS_ALIGN_RIGHT|El panel que se está acoplado a la derecha del área de cliente de una ventana de marco.|

##  <a name="createex"></a>  CDockablePane:: CreateEx

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

*dwStyleEx*<br/>
[in] Especifica los atributos de estilo extendido de la nueva ventana.

*lpszCaption*<br/>
[in] Especifica el nombre de la ventana.

*pParentWnd*<br/>
[in, out] Especifica la ventana primaria.

*Rect*<br/>
[in] Especifica el tamaño y posición de la ventana, en coordenadas de cliente de *pParentWnd*.

*bHasGripper*<br/>
[in] TRUE para crear el panel con un título; en caso contrario, FALSE.

*nID*<br/>
[in] Especifica el identificador de la ventana secundaria. Este valor debe ser único si desea guardar el estado de acoplamiento para este panel de acoplamiento.

*dwStyle*<br/>
[in] Especifica los atributos de estilo de ventana.

*dwTabbedStyle*<br/>
[in] Especifica el estilo de una ventana con pestañas que se crea cuando el usuario arrastra un panel en el título de este panel con pestañas.

*dwControlBarStyle*<br/>
[in] Especifica los atributos de estilo adicionales.

*pContext*<br/>
[in, out] Especifica el contexto de creación de la ventana.

### <a name="return-value"></a>Valor devuelto

TRUE si el panel acoplable se haya creado correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Crea un panel de Windows y lo adjunta a la `CDockablePane` objeto.

Si el *dwStyle* estilo de ventana tiene la marca CBRS_FLOAT_MULTI, la ventana de marco reducido puede flotar con otros paneles en la ventana de marco reducido. De forma predeterminada, acoplar paneles sólo flotante individualmente.

Si el *dwTabbedStyle* parámetro tiene el indicador AFX_CBRS_OUTLOOK_TABS especificado, el panel crea paneles con pestañas de estilo de Outlook cuando otro panel está asociado a este panel con el [CDockablePane:: Attachtotabwnd](#attachtotabwnd) método. De forma predeterminada, los paneles acoplables crean paneles con pestañas regulares del tipo [CTabbedPane](../../mfc/reference/ctabbedpane-class.md).

##  <a name="createtabbedpane"></a>  CDockablePane::CreateTabbedPane

Crea un panel con pestañas en el panel actual.

```
virtual CTabbedPane* CreateTabbedPane();
```

### <a name="return-value"></a>Valor devuelto

El nuevo panel con pestañas, o NULL si la operación de creación no se pudo.

### <a name="remarks"></a>Comentarios

El marco llama a este método cuando crea un panel con pestañas para reemplazar este panel. Para obtener más información, consulte [CDockablePane:: Attachtotabwnd](#attachtotabwnd).

Invalide este método en una clase derivada para personalizar los paneles con pestañas de cómo se crean e inicializan.

Se crea el panel con pestañas según la información de clase en tiempo de ejecución almacenada en el `m_pTabbedControlBarRTC` miembro, que inicializa el [CDockablePane:: CreateEx](#createex) método.

##  <a name="dockpanecontainer"></a>  CDockablePane::DockPaneContainer

Acopla un contenedor en el panel.

```
virtual BOOL DockPaneContainer(
    CPaneContainerManager& barContainerManager,
    DWORD dwAlignment,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Parámetros

*barContainerManager*<br/>
[in] Una referencia al administrador de contenedor del contenedor que se está acoplando.

*dwAlignment*<br/>
[in] DWORD que especifica el lado del panel al que se está acoplando el contenedor.

*dockMethod*<br/>
[in] No se utiliza.

### <a name="return-value"></a>Valor devuelto

TRUE si el contenedor correctamente se acopla al panel; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

*dwAlignment* puede ser cualquiera de los siguientes valores:

|Valor|Descripción|
|-----------|-----------------|
|CBRS_ALIGN_TOP|El contenedor que se está acoplado a la parte superior del panel.|
|CBRS_ALIGN_BOTTOM|El contenedor que se está acoplado a la parte inferior del panel.|
|CBRS_ALIGN_LEFT|El contenedor que se está acoplado a la izquierda del panel.|
|CBRS_ALIGN_RIGHT|El contenedor que se está acoplado a la derecha del panel.|

##  <a name="dockpanestandard"></a>  CDockablePane::DockPaneStandard

Acopla un panel mediante el uso de esquema de acoplamiento (estándar).

```
virtual CPane* DockPaneStandard(BOOL& bWasDocked);
```

### <a name="parameters"></a>Parámetros

*bWasDocked*<br/>
[in] Cuando el método devuelve, este valor contiene TRUE si el panel se acopla correctamente; en caso contrario, contiene FALSE.

### <a name="return-value"></a>Valor devuelto

Si el panel se acopla a una ventana con pestañas, o si una ventana con pestañas que se creó como resultado de acoplamiento, este método devuelve un puntero a la ventana con pestañas. Si el panel era en caso contrario, acoplada correctamente, este método devuelve el **esto** puntero. Si no se pudo acoplamiento, este método devuelve NULL.

##  <a name="docktorecentpos"></a>  CDockablePane::DockToRecentPos

Acopla un panel en su posición de acoplamiento almacenado.

```
BOOL CDockablePane::DockToRecentPos();
```

### <a name="return-value"></a>Valor devuelto

TRUE si el panel está acoplado correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Paneles acoplables almacenan información de acoplamiento reciente en un [CRecentDockSiteInfo](../../mfc/reference/crecentdocksiteinfo-class.md) objeto.

##  <a name="docktowindow"></a>  CDockablePane::DockToWindow

Acopla un panel acoplable a otro panel de acoplamiento.

```
virtual BOOL DockToWindow(
    CDockablePane* pTargetWindow,
    DWORD dwAlignment,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parámetros

*pTargetWindow*<br/>
[in, out] Especifica el panel acoplable para acoplar este panel a.

*dwAlignment*<br/>
[in] Especifica la alineación del panel de acoplamiento. Puede ser uno de CBRS_ALIGN_LEFT, CBRS_ALIGN_TOP, CBRS_ALIGN_RIGHT, CBRS_ALIGN_BOTTOM o CBRS_ALIGN_ANY. (Definidos en afxres.h).

*lpRect*<br/>
[in] Especifica el rectángulo para el panel de acoplamiento.

### <a name="return-value"></a>Valor devuelto

TRUE si el panel se acopla correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Llame a este método para acoplar un panel a otro panel con la alineación especificada por *dwAlignment*.

##  <a name="drawcaption"></a>  CDockablePane::DrawCaption

Dibuja la leyenda (también denominada a agarrador) de un panel acoplable.

```
virtual void DrawCaption(
    CDC* pDC,
    CRect rectCaption);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] Representa el contexto de dispositivo que se usa para dibujar.

*rectCaption*<br/>
[in] Especifica el rectángulo delimitador del título del panel.

### <a name="remarks"></a>Comentarios

El marco llama a este método para dibujar el título de un panel acoplable.

Invalide este método en una clase derivada para personalizar la apariencia de la leyenda.

##  <a name="enableautohideall"></a>  CDockablePane::EnableAutohideAll

Habilita o deshabilita el modo de ocultación automática para este panel y para otros paneles en el contenedor.

```
void EnableAutohideAll(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar el*<br/>
[in] TRUE para habilitar la opción Ocultar automáticamente todas las características del panel acoplable; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Cuando un usuario mantiene el **Ctrl** clave y hace clic en el botón de anclaje para cambiar un panel a modo de ocultación automática, todos los demás paneles en el mismo contenedor también se puede cambiar al modo de ocultación automática.

Llame a este método con *bHabilitar el* establecido en FALSE para deshabilitar esta característica para un determinado panel.

##  <a name="enablegripper"></a>  CDockablePane::EnableGripper

Muestra u oculta la leyenda (también denominada a agarrador).

```
virtual void EnableGripper(BOOL bEnable);
```

### <a name="parameters"></a>Parámetros

*bHabilitar el*<br/>
[in] TRUE para habilitar el título; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Cuando el marco de trabajo crea paneles acoplables, no tienen el estilo de ventana WS_STYLE, incluso si se especifica. Esto significa que el título del panel es un área de no cliente se controla mediante el marco de trabajo, pero difiere de esta área de título de ventana estándar.

Puede mostrar u ocultar el título en cualquier momento. El marco de trabajo oculta la leyenda cuando se agrega un panel como una pestaña a una ventana con pestañas o cuando un panel de flota en una ventana de marco reducido.

##  <a name="getahrestoredrect"></a>  CDockablePane::GetAHRestoredRect

Especifica la posición del panel en modo de ocultación automática.

```
CRect GetAHRestoredRect() const;
```

### <a name="return-value"></a>Valor devuelto

Un `CRect` objeto que contiene la posición del panel cuando se encuentra en modo de ocultación automática.

### <a name="remarks"></a>Comentarios

##  <a name="getahslidemode"></a>  CDockablePane::GetAHSlideMode

Recupera el modo de diapositiva de ocultación automática para el panel.

```
virtual UINT GetAHSlideMode() const;
```

### <a name="return-value"></a>Valor devuelto

Un tipo UINT que especifica el modo de diapositiva de ocultación automática para el panel. El valor devuelto puede ser AFX_AHSM_MOVE o AFX_AHSM_STRETCH, pero la implementación sólo usa AFX_AHSM_MOVE.

### <a name="remarks"></a>Comentarios

##  <a name="getcaptionheight"></a>  CDockablePane::GetCaptionHeight

Devuelve el alto, en píxeles, del título actual.

```
virtual int GetCaptionHeight() const;
```

### <a name="return-value"></a>Valor devuelto

El alto del título, en píxeles.

### <a name="remarks"></a>Comentarios

Alto del título es 0 si el título se ha ocultado por la [CDockablePane::EnableGripper](#enablegripper) método, o si el panel no tiene un título.

##  <a name="getdefaultpanedivider"></a>  CDockablePane::GetDefaultPaneDivider

Devuelve el divisor del panel predeterminado para el contenedor del panel.

```
CPaneDivider* GetDefaultPaneDivider() const;
```

### <a name="return-value"></a>Valor devuelto

Válido [CPaneDivider](../../mfc/reference/cpanedivider-class.md) objeto si el panel acoplable se acopla a la ventana de marco principal, o `NULL` si no se acopla el panel acoplable o si está flotando.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre los divisores de paneles, consulte [CPaneDivider (clase)](../../mfc/reference/cpanedivider-class.md).

##  <a name="getdockingstatus"></a>  CDockablePane::GetDockingStatus

Determina la capacidad de un panel para acoplar basándose en la ubicación del puntero proporcionado.

```
virtual AFX_CS_STATUS GetDockingStatus(
    CPoint pt,
    int nSensitivity);
```

### <a name="parameters"></a>Parámetros

*PT*<br/>
[in] La ubicación del puntero en coordenadas de pantalla.

*nSensitivity*<br/>
[in] La distancia, en píxeles, de lejos del borde de un rectángulo el puntero debe ser para habilitar el acoplamiento.

### <a name="return-value"></a>Valor devuelto

Uno de los valores de estado siguientes:

|Valor AFX_CS_STATUS|Significado|
|---------------------------|-------------|
|CS_NOTHING|El puntero no es a través de un sitio de vinculación. El marco de trabajo no acoplar el panel.|
|CS_DOCK_IMMEDIATELY|El puntero se encuentra sobre el sitio de vinculación en el modo inmediato (el panel utiliza el modo de acoplamiento DT_IMMEDIATE). El marco de trabajo acopla el panel inmediatamente.|
|CS_DELAY_DOCK|El puntero está sobre un sitio de vinculación que es otro panel acoplable o es un borde del marco principal. El marco de trabajo acopla el panel después de un retraso. Vea la sección Comentarios para obtener más información acerca de este retraso.|
|CS_DELAY_DOCK_TO_TAB|El puntero se encuentra sobre un sitio de vinculación que hace que el panel se acopla en una ventana con pestañas. Esto se produce cuando el puntero se encuentra sobre el título de otro panel de acoplamiento o sobre el área de pestañas de un panel con pestañas.|

### <a name="remarks"></a>Comentarios

El marco llama a este método para controlar el acoplamiento de un panel flotante.

Barras de herramientas flotantes o acoplar paneles que utilizan el modo de acoplamiento DT_IMMEDIATE, el marco de trabajo retrasa el comando de acoplamiento para permitir al usuario mover la ventana fuera del área cliente del marco primario antes de que se produce de acoplamiento. La duración del retraso se mide en milisegundos y se controla mediante el [CDockingManager::m_nTimeOutBeforeToolBarDock](../../mfc/reference/cdockingmanager-class.md#m_ntimeoutbeforetoolbardock) miembro de datos... El valor predeterminado de [CDockingManager::m_nTimeOutBeforeToolBarDock](../../mfc/reference/cdockingmanager-class.md#m_ntimeoutbeforetoolbardock) es 200. Este comportamiento emula el comportamiento de acoplamiento de Microsoft Word 2007.

Para los Estados de acoplamiento retrasados (CS_DELAY_DOCK y CS_DELAY_DOCK_TO_TAB), el marco de trabajo no realiza el acoplamiento hasta que el usuario suelta el botón del mouse. Si un panel utiliza el modo de acoplamiento DT_STANDARD, el marco de trabajo muestra un rectángulo en la ubicación de acoplamiento proyectada. Si un panel utiliza el modo de acoplamiento DT_SMART, el marco de trabajo muestra marcadores de acoplamiento inteligente y rectángulos semitransparentes en la ubicación de acoplamiento proyectada. Para especificar el modo de acoplamiento para el panel, llame a la [CBasePane::SetDockingMode](../../mfc/reference/cbasepane-class.md#setdockingmode) método. Para obtener más información acerca de acoplamiento inteligente, consulte [CDockingManager::GetSmartDockingParams](../../mfc/reference/cdockingmanager-class.md#getsmartdockingparams).

##  <a name="getdragsensitivity"></a>  CDockablePane::GetDragSensitivity

Devuelve la sensibilidad de arrastre de un panel acoplable.

```
static const CSize& GetDragSensitivity();
```

### <a name="return-value"></a>Valor devuelto

Un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que contiene el ancho y alto, en píxeles, de un rectángulo centrado en un punto de arrastre. La operación de arrastre no comienza hasta que el puntero del mouse se mueve fuera de este rectángulo.

##  <a name="getlastpercentinpanecontainer"></a>  CDockablePane::GetLastPercentInPaneContainer

Recupera el porcentaje de espacio que ocupa un panel en su contenedor ( [CPaneContainer (clase)](../../mfc/reference/cpanecontainer-class.md)).

```
int GetLastPercentInPaneContainer() const;
```

### <a name="return-value"></a>Valor devuelto

Un *int* que especifica el porcentaje de espacio que ocupa el panel en su contenedor.

### <a name="remarks"></a>Comentarios

Este método se utiliza cuando el contenedor ajusta su diseño.

##  <a name="gettabarea"></a>  CDockablePane::GetTabArea

Recupera el área de pestañas para el panel.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Parámetros

*rectTabAreaTop*<br/>
[in] `GetTabArea` rellena esta variable con el área de pestañas, si se encuentran en la parte superior del panel de pestañas. Si las pestañas se encuentran en la parte inferior del panel, esta variable se rellena con un rectángulo vacío.

*rectTabAreaBottom*<br/>
[in] `GetTabArea` rellena esta variable con el área de pestañas, si se encuentran en la parte inferior del panel de pestañas. Si se encuentra en la parte superior del panel de pestañas, esta variable se rellena con un rectángulo vacío.

### <a name="remarks"></a>Comentarios

Este método solo se usa en las clases que se derivan de `CDockablePane` y tiene pestañas. Para obtener más información, consulte [CTabbedPane::GetTabArea](../../mfc/reference/ctabbedpane-class.md#gettabarea) y [CMFCOutlookBar::GetTabArea](../../mfc/reference/cmfcoutlookbar-class.md#gettabarea).

##  <a name="gettabbedpanertc"></a>  CDockablePane::GetTabbedPaneRTC

Devuelve la información de clase en tiempo de ejecución acerca de una ventana con pestañas que se crea al otro panel se acopla al panel actual.

```
CRuntimeClass* GetTabbedPaneRTC() const;
```

### <a name="return-value"></a>Valor devuelto

La información de clase en tiempo de ejecución para el panel acoplable.

### <a name="remarks"></a>Comentarios

Llame a este método para recuperar la información de clase en tiempo de ejecución para los paneles con pestañas que se crean dinámicamente. Esto puede ocurrir cuando un usuario arrastra un panel con el título de otro panel, o si se llama a la [CDockablePane:: Attachtotabwnd](#attachtotabwnd) método para crear un panel con fichas mediante programación desde dos paneles acoplables.

Puede establecer la información de clase en tiempo de ejecución mediante una llamada a la [CDockablePane:: Settabbedpanertc](#settabbedpanertc) método.

##  <a name="hasautohidemode"></a>  CDockablePane::HasAutoHideMode

Especifica si un panel acoplable se puede cambiar a modo de ocultación automática.

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el panel acoplable se puede cambiar a modo de ocultación automática; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para deshabilitar el modo de ocultación automática para un panel acoplable específico.

##  <a name="hittest"></a>  CDockablePane::HitTest

Especifica la ubicación en un panel donde el usuario hace clic del mouse.

```
virtual int HitTest(
    CPoint point,
    BOOL bDetectCaption = FALSE);
```

### <a name="parameters"></a>Parámetros

*punto*<br/>
[in] Especifica el punto de prueba.

*bDetectCaption*<br/>
[in] TRUE si se deben devolver HTCAPTION si el punto está en el título del panel; en caso contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

Uno de los siguientes valores:

- HTNOWHERE si *punto* no está en el panel acoplable.

- HTCLIENT si *punto* está en el área cliente del panel acoplable.

- HTCAPTION si *punto* está en el área de título del panel acoplable.

- AFX_HTCLOSE si *punto* se encuentra en el botón de cierre.

- HTMAXBUTTON si *punto* se encuentra en el botón de anclaje.

##  <a name="isautohideallenabled"></a>  CDockablePane::IsAutohideAllEnabled

Indica si el panel de acoplamiento y todos los demás paneles en el contenedor se pueden cambiar a modo de ocultación automática.

```
virtual BOOL IsAutohideAllEnabled() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el panel acoplable y todos los demás paneles en el contenedor, se pueden cambiar a modo de ocultación automática; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Un usuario habilita el modo de ocultación automática, haga clic en el botón de anclaje acoplamiento mientras mantiene la **Ctrl** clave

Para habilitar o deshabilitar este comportamiento, llame a la [CDockablePane::EnableAutohideAll](#enableautohideall) método.

##  <a name="isautohidemode"></a>  CDockablePane::IsAutoHideMode

Determina si un panel está en modo de ocultación automática.

```
virtual BOOL IsAutoHideMode() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el panel acoplable está en modo de ocultación automática; en caso contrario, FALSE.

##  <a name="isdocked"></a>  CDockablePane::IsDocked

Determina si se acopla el panel actual.

```
virtual BOOL IsDocked() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el panel acoplable no pertenece a una ventana de marco reducido o si está flotando en una ventana de marco reducido con otro panel. FALSE si el panel es un elemento secundario de una ventana de marco reducido y no hay ningún otros paneles que pertenecen a la ventana de marco reducido.

### <a name="remarks"></a>Comentarios

Para determinar si el panel está acoplado a la ventana de marco principal, llame a [CDockablePane::GetDefaultPaneDivider](#getdefaultpanedivider). Si el método devuelve un puntero no NULL, el panel se acopla en la ventana de marco principal.

##  <a name="ishideinautohidemode"></a>  CDockablePane::IsHideInAutoHideMode

Determina el comportamiento de un panel que está en modo de ocultación automática si se muestra (u oculto) mediante una llamada a [CDockablePane::ShowPane](#showpane).

```
virtual BOOL IsHideInAutoHideMode() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si se debe ocultar el panel acoplable cuando está en modo de ocultación automática; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Cuando un panel acoplable está en modo de ocultación automática, tiene un comportamiento diferente cuando se llama a `ShowPane` para ocultar o mostrar el panel. Este comportamiento se controla mediante el miembro estático [CDockablePane::m_bHideInAutoHideMode](#m_bhideinautohidemode). Si este miembro es TRUE, el panel acoplable y su barra de herramientas Ocultar automáticamente relacionados o botón de ocultación automática está oculta o se muestra cuando se llama a `ShowPane`. En caso contrario, se activa o desactiva el panel acoplable y su barra de herramientas Ocultar automáticamente relacionados o botón de ocultación automática está siempre visible.

Invalide este método en una clase derivada para cambiar el comportamiento predeterminado para los paneles individuales.

El valor predeterminado de `m_bHideInAutoHideMode` es FALSE.

##  <a name="isinfloatingmultipaneframewnd"></a>  CDockablePane::IsInFloatingMultiPaneFrameWnd

Especifica si el panel está en una ventana de marco de varios paneles ( [CMultiPaneFrameWnd (clase)](../../mfc/reference/cmultipaneframewnd-class.md)).

```
virtual BOOL IsInFloatingMultiPaneFrameWnd() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el panel está en una ventana de marco de varios paneles; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="isresizable"></a>  CDockablePane::IsResizable

Especifica si se puede cambiar el tamaño del panel.

```
virtual BOOL IsResizable() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el panel es de tamaño ajustable; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

De forma predeterminada, los paneles acoplables son redimensionables. Para evitar el cambio de tamaño, invalide este método en una clase derivada y devolver FALSE. Tenga en cuenta que un valor FALSE conduce a un error **ASSERT** en [CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane). Use [CDockingManager::AddPane](../../mfc/reference/cdockingmanager-class.md#addpane) en su lugar para acoplar un panel dentro de un marco primario.

Los paneles que no se puede cambiar el tamaño ni pueden flotar ni entrar en modo de ocultación automática y siempre se encuentran en el borde exterior del marco primario.

##  <a name="istablocationbottom"></a>  CDockablePane::IsTabLocationBottom

Especifica si se encuentran en la parte superior o inferior del panel de pestañas.

```
virtual BOOL IsTabLocationBottom() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si las pestañas se encuentran en la parte inferior del panel; FALSE si se encuentran en la parte superior del panel de pestañas.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [CTabbedPane::IsTabLocationBottom](../../mfc/reference/ctabbedpane-class.md#istablocationbottom).

##  <a name="istracked"></a>  CDockablePane::IsTracked

Especifica si el usuario mueve un panel.

```
BOOL IsTracked() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si se va a mover el panel; en caso contrario, FALSE.

##  <a name="isvisible"></a>  CDockablePane::IsVisible

Determina si está visible el panel actual.

```
virtual BOOL IsVisible() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el panel acoplable está visible; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Llame a este método para determinar si un panel acoplable está visible. Puede usar este método en lugar de llamar [CWnd::IsWindowVisible](../../mfc/reference/cwnd-class.md#iswindowvisible) o las pruebas para el estilo WS_VISIBLE. El estado de visibilidad devuelto depende de si el modo de ocultación automática está habilitado o deshabilitado y el valor de la [CDockablePane::IsHideInAutoHideMode](#ishideinautohidemode) propiedad.

Si el panel acoplable está en modo de ocultación automática y `IsHideInAutoHideMode` devuelve FALSE, el estado de visibilidad es siempre FALSE.

Si el panel acoplable está en modo de ocultación automática y `IsHideInAutoHideMode` devuelve TRUE y el estado de visibilidad depende del estado de visibilidad de la barra de herramientas Ocultar automáticamente relacionados.

Si el panel acoplable no está en modo de ocultación automática, el estado de visibilidad viene determinada por la [CBasePane::IsVisible](../../mfc/reference/cbasepane-class.md#isvisible) método.

## ##  <a name="loadstate"></a>  CDockablePane:: Loadstate

Sólo para uso interno. Para obtener información más detallada, consulta el código fuente ubicado en la carpeta VC\atlmfc\src\mfc de la instalación de Visual Studio.

```
virtual BOOL LoadState(
   LPCTSTR lpszProfileName = NULL,
   int nIndex = -1,
   UINT uiID = (UINT) -1
);
```

##  <a name="m_bdisableanimation"></a>  CDockablePane::m_bDisableAnimation

Especifica si se deshabilita la animación de ocultación automática del panel acoplable.

```
AFX_IMPORT_DATA static BOOL m_bDisableAnimation;
```

##  <a name="m_bhideinautohidemode"></a>  CDockablePane::m_bHideInAutoHideMode

Determina el comportamiento del panel cuando el panel está en modo de ocultación automática.

```
AFX_IMPORT_DATA static BOOL m_bHideInAutoHideMode;
```

### <a name="remarks"></a>Comentarios

Este valor afecta a todos los paneles de acoplamiento en la aplicación.

Si establece este miembro en paneles acoplables, TRUE se oculta o se muestran con sus botones y barras de herramientas Ocultar automáticamente relacionados cuando se llama a [CDockablePane::ShowPane](#showpane).

Si establece este miembro en paneles acoplables, FALSE se activan o desactivan cuando se llama a [CDockablePane::ShowPane](#showpane).

##  <a name="m_nslidesteps"></a>  CDockablePane::m_nSlideSteps

Especifica la velocidad de animación del panel cuando se encuentra en modo de ocultación automática.

```
AFX_IMPORT_DATA static int m_nSlideSteps;
```

### <a name="remarks"></a>Comentarios

Para obtener un efecto de animación más rápido, reduzca este valor. Para obtener un efecto de animación más lento, aumente este valor.

##  <a name="onafterchangeparent"></a>  CDockablePane::OnAfterChangeParent

Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.

```
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```

### <a name="parameters"></a>Parámetros

[in] *pWndOldParent*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="onafterdockfromminiframe"></a>  CDockablePane::OnAfterDockFromMiniFrame

Lo llama el marco de trabajo cuando se acopla una barra de acoplamiento flotante en una ventana de marco.

```
virtual void OnAfterDockFromMiniFrame();
```

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método no hace nada.

##  <a name="onbeforechangeparent"></a>  CDockablePane::OnBeforeChangeParent

El marco llama a este método antes de que cambie al elemento primario del panel.

```
virtual void OnBeforeChangeParent(
    CWnd* pWndNewParent,
    BOOL bDelay = FALSE);
```

### <a name="parameters"></a>Parámetros

*pWndNewParent*<br/>
[in] Un puntero a la nueva ventana primaria.

*bDelay*<br/>
[in] Valor booleano que especifica si se debe retrasar el recálculo del diseño de acoplamiento si el panel está desacoplado. Para obtener más información, consulte [CDockablePane::UndockPane](#undockpane).

### <a name="remarks"></a>Comentarios

Si el panel está acoplado y el nuevo elemento primario no permitir el acoplamiento, este método desacopla el panel.

Si el panel se está convirtiendo en un documento con pestañas, este método almacena su posición de acoplamiento recientes. El marco de trabajo utiliza la posición de acoplamiento reciente para restaurar la posición del panel cuando se convierte en un estado acoplado.

##  <a name="onbeforefloat"></a>  CDockablePane::OnBeforeFloat

El marco llama a este método antes de un panel de las transiciones a un estado flotante.

```
virtual BOOL OnBeforeFloat(
    CRect& rectFloat,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Parámetros

*rectFloat*<br/>
[in] Especifica la posición y tamaño del panel cuando se encuentra en un estado flotante.

*dockMethod*<br/>
[in] Especifica el método de acoplamiento. Consulte [CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane) para obtener una lista de valores posibles.

### <a name="return-value"></a>Valor devuelto

TRUE si el panel puede flotar; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método cuando un panel se acerca a float. Puede invalidar este método en una clase derivada si desea realizar cualquier procesamiento antes de que el panel de flota.

##  <a name="onpressbuttons"></a>  CDockablePane::OnPressButtons

Se llama cuando el usuario presiona un botón de título que no sean los botones AFX_HTCLOSE y AFX_HTMAXBUTTON.

```
virtual void OnPressButtons(UINT nHit);
```

### <a name="parameters"></a>Parámetros

*nHit*<br/>
[in] No se utiliza este parámetro.

### <a name="remarks"></a>Comentarios

Si agrega un botón personalizado con el título de un panel acoplable, invalide este método para recibir notificaciones cuando un usuario presiona el botón.

##  <a name="onslide"></a>  CDockablePane::OnSlide

Lo llama el marco de trabajo que se va a animar el panel cuando se encuentra en modo de ocultación automática.

```
virtual void OnSlide(BOOL bSlideOut);
```

### <a name="parameters"></a>Parámetros

*bSlideOut*<br/>
[in] TRUE para mostrar el panel. FALSE para ocultar el panel.

### <a name="remarks"></a>Comentarios

Invalide este método en una clase derivada para implementar los efectos personalizados de ocultar automáticamente.

##  <a name="removefromdefaultpanedividier"></a>  CDockablePane:: Removefromdefaultpanedividier

El marco llama a este método cuando se se desacople un panel.

```
void RemoveFromDefaultPaneDividier();
```

### <a name="remarks"></a>Comentarios

Este método establece el divisor del panel predeterminado en NULL y quita el panel de su contenedor.

##  <a name="replacepane"></a>  CDockablePane::ReplacePane

Reemplaza el panel con un panel especificado.

```
BOOL ReplacePane(
    CDockablePane* pBarToReplaceWith,
    AFX_DOCK_METHOD dockMethod,
    BOOL bRegisterWithFrame = FALSE);
```

### <a name="parameters"></a>Parámetros

*pBarToReplaceWith*<br/>
[in] Un puntero a un panel acoplable.

*dockMethod*<br/>
[in] No se utiliza.

*bRegisterWithFrame*<br/>
[in] Si es TRUE, el nuevo panel está registrado con el Administrador de acoplamiento del elemento primario del panel anterior. El nuevo panel se inserta en el índice de la sección anterior en la lista de paneles que se mantiene mediante el Administrador de acoplamiento.

### <a name="return-value"></a>Valor devuelto

TRUE si el reemplazo se realiza correctamente; en caso contrario, FALSE.

##  <a name="restoredefaultpanedivider"></a>  CDockablePane::RestoreDefaultPaneDivider

Cuando se deserializa un panel, el marco llama a este método para restaurar el divisor del panel de forma predeterminada.

```
void RestoreDefaultPaneDivider();
```

### <a name="remarks"></a>Comentarios

El divisor del panel predeterminado restablecido reemplaza el divisor de paneles predeterminada actual, si existe.

##  <a name="setautohidemode"></a>  CDockablePane::SetAutoHideMode

Alterna entre visible el panel de acoplamiento y el modo de ocultación automática.

```
virtual CMFCAutoHideBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>Parámetros

*bMode*<br/>
[in] TRUE para habilitar el modo de ocultación automática; FALSE para habilitar el modo normal de acoplamiento.

*dwAlignment*<br/>
[in] Especifica la alineación del panel para crear la opción Ocultar automáticamente.

*pCurrAutoHideBar*<br/>
[in, out] Un puntero a la barra de herramientas de ocultación automática actual. Puede ser NULL.

*bUseTimer*<br/>
[in] Especifica si utilizar el efecto de ocultar automáticamente cuando el usuario activa el panel en modo de ocultación automática u ocultar el panel inmediatamente.

### <a name="return-value"></a>Valor devuelto

La barra de herramientas de ocultación automática que se creó como resultado de cambiar al modo de ocultación automática, o NULL.

### <a name="remarks"></a>Comentarios

El marco llama a este método cuando un usuario hace clic en el botón de anclaje para cambiar el panel acoplable a modo de ocultación automática o a modo normal de acoplamiento.

Llame a este método para cambiar mediante programación un panel acoplable a modo de ocultación automática. Se debe acoplar el panel a la ventana de marco principal ( [CDockablePane::GetDefaultPaneDivider](#getdefaultpanedivider) debe devolver un puntero válido a la [CPaneDivider](../../mfc/reference/cpanedivider-class.md)).

##  <a name="setautohideparents"></a>  CDockablePane::SetAutoHideParents

Establece el botón de ocultación automática y la barra de herramientas de ocultación automática para el panel.

```
void SetAutoHideParents(
    CMFCAutoHideBar* pToolBar,
    CMFCAutoHideButton* pBtn);
```

### <a name="parameters"></a>Parámetros

*pToolBar*<br/>
[in] Puntero a una barra de herramientas de ocultación automática.

*pBtn*<br/>
[in] Puntero a un botón de ocultación automática.

##  <a name="setlastpercentinpanecontainer"></a>  CDockablePane::SetLastPercentInPaneContainer

Establece el porcentaje de espacio que ocupa un panel en su contenedor.

```
void SetLastPercentInPaneContainer(int n);
```

### <a name="parameters"></a>Parámetros

*n*<br/>
[in] Un **int** que especifica el porcentaje de espacio que ocupa el panel en su contenedor.

### <a name="remarks"></a>Comentarios

El marco de trabajo ajusta el panel para utilizar el nuevo valor cuando se vuelve a calcular el diseño.

##  <a name="setrestoreddefaultpanedivider"></a>  CDockablePane::SetRestoredDefaultPaneDivider

Establece el divisor del panel predeterminado restablecido.

```
void SetRestoredDefaultPaneDivider(HWND hRestoredSlider);
```

### <a name="parameters"></a>Parámetros

*hRestoredSlider*<br/>
[in] Identificador de un divisor de panel (control deslizante).

### <a name="remarks"></a>Comentarios

Cuando se deserializa un panel, se obtiene un divisor de paneles predeterminada restaurada. Para obtener más información, consulte [CDockablePane::RestoreDefaultPaneDivider](#restoredefaultpanedivider).

##  <a name="settabbedpanertc"></a>  CDockablePane:: Settabbedpanertc

Establece la información de clase en tiempo de ejecución para una ventana con pestañas que se crea cuando dos paneles de acoplamiento entre sí.

```
void SetTabbedPaneRTC(CRuntimeClass* pRTC);
```

### <a name="parameters"></a>Parámetros

*pRTC*<br/>
[in] La información de clase en tiempo de ejecución para el panel con pestañas.

### <a name="remarks"></a>Comentarios

Llame a este método para establecer la información de clase en tiempo de ejecución para los paneles con pestañas que se crean dinámicamente. Esto puede ocurrir cuando un usuario arrastra un panel con el título de otro panel, o si se llama a la [CDockablePane:: Attachtotabwnd](#attachtotabwnd) método para crear un panel con fichas mediante programación desde dos paneles acoplables.

La clase de tiempo de ejecución predeterminada se establece según el *dwTabbedStyle* parámetro de [CDockablePane::Create](#create) y [CDockablePane:: CreateEx](#createex). Para personalizar los nuevos paneles con pestañas, derive la clase de una de las clases siguientes:

- [CBaseTabbedPane (clase)](../../mfc/reference/cbasetabbedpane-class.md)

- [CTabbedPane (clase)](../../mfc/reference/ctabbedpane-class.md)

- [CMFCOutlookBar (clase)](../../mfc/reference/cmfcoutlookbar-class.md).

A continuación, llame a este método con el puntero a su información de clase en tiempo de ejecución.

##  <a name="showpane"></a>  CDockablePane::ShowPane

Muestra u oculta un panel.

```
virtual void ShowPane(
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>Parámetros

*bMostrar*<br/>
[in] TRUE para mostrar el panel. FALSE para ocultar el panel.

*bDelay*<br/>
[in] True para retrasar ajustar el diseño de acoplamiento FALSE para ajustar el diseño de acoplamiento inmediatamente.

*bActivate*<br/>
[in] TRUE para activar el panel al que se muestra; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Llame a este método en lugar de la [CWnd:: ShowWindow](../../mfc/reference/cwnd-class.md#showwindow) al mostrar u ocultar paneles acoplables.

##  <a name="slide"></a>  CDockablePane::Slide

Se anima un panel que está en modo de ocultación automática.

```
virtual void Slide(
    BOOL bSlideOut,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>Parámetros

*bSlideOut*<br/>
[in] TRUE para mostrar el panel. FALSE para ocultar el panel.

*bUseTimer*<br/>
[in] TRUE para mostrar u ocultar el panel con el efecto de ocultar automáticamente; FALSE para mostrar u ocultar el panel de inmediato.

### <a name="remarks"></a>Comentarios

El marco llama a este método para animar un panel que está en modo de ocultación automática.

Este método usa la `CDockablePane::m_nSlideDefaultTimeOut` valor para determinar el tiempo de espera para el efecto de diapositiva. El valor predeterminado para el tiempo de espera es 1. Si personaliza el algoritmo de ocultar automáticamente, modifique este miembro para cambiar el tiempo de espera.

##  <a name="toggleautohide"></a>  CDockablePane::ToggleAutoHide

Alterna el panel entre siempre visible y el modo de ocultación automática.

```
virtual void ToggleAutoHide();
```

### <a name="remarks"></a>Comentarios

Este método alterna el modo de ocultación automática para el panel mediante una llamada a [CDockablePane::SetAutoHideMode](#setautohidemode).

##  <a name="undockpane"></a>  CDockablePane::UndockPane

Desacopla un panel desde la ventana de marco principal o un contenedor de la ventana de marco reducido.

```
virtual void UndockPane(BOOL bDelay = FALSE);
```

### <a name="parameters"></a>Parámetros

*bDelay*<br/>
[in] True para retrasar calculando el diseño de acoplamiento FALSE para volver a calcular el diseño de acoplamiento inmediatamente.

### <a name="remarks"></a>Comentarios

Llame a este método para desacoplar un panel desde la ventana de marco principal o desde un contenedor de ventana de marco reducido el multi (es decir, un panel que está flotando en una ventana de marco reducido único con otros paneles).

Debe desbloquear un panel antes de realizar cualquier operación externa que no se realiza mediante el [CDockingManager](../../mfc/reference/cdockingmanager-class.md). Por ejemplo, debe desacoplar un panel para mover mediante programación desde una ubicación a otra.

El marco de trabajo desacoplará automáticamente paneles antes de que se destruyen.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CPane (clase)](../../mfc/reference/cpane-class.md)
