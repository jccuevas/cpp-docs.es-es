---
title: CMFCOutlookBar (clase)
ms.date: 06/25/2018
f1_keywords:
- CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar::AllowDestroyEmptyTabbedPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanAcceptPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanSetCaptionTextToTabName
- AFXOUTLOOKBAR/CMFCOutlookBar::Create
- AFXOUTLOOKBAR/CMFCOutlookBar::CreateCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::DoesAllowDynInsertBefore
- AFXOUTLOOKBAR/CMFCOutlookBar::FloatTab
- AFXOUTLOOKBAR/CMFCOutlookBar::GetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::GetTabArea
- AFXOUTLOOKBAR/CMFCOutlookBar::IsMode2003
- AFXOUTLOOKBAR/CMFCOutlookBar::OnAfterAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnBeforeAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnScroll
- AFXOUTLOOKBAR/CMFCOutlookBar::RemoveCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::SetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::SetMode2003
helpviewer_keywords:
- CMFCOutlookBar [MFC], AllowDestroyEmptyTabbedPane
- CMFCOutlookBar [MFC], CanAcceptPane
- CMFCOutlookBar [MFC], CanSetCaptionTextToTabName
- CMFCOutlookBar [MFC], Create
- CMFCOutlookBar [MFC], CreateCustomPage
- CMFCOutlookBar [MFC], DoesAllowDynInsertBefore
- CMFCOutlookBar [MFC], FloatTab
- CMFCOutlookBar [MFC], GetButtonsFont
- CMFCOutlookBar [MFC], GetTabArea
- CMFCOutlookBar [MFC], IsMode2003
- CMFCOutlookBar [MFC], OnAfterAnimation
- CMFCOutlookBar [MFC], OnBeforeAnimation
- CMFCOutlookBar [MFC], OnScroll
- CMFCOutlookBar [MFC], RemoveCustomPage
- CMFCOutlookBar [MFC], SetButtonsFont
- CMFCOutlookBar [MFC], SetMode2003
ms.assetid: 2b335f71-ce99-4efd-b103-e65ba43ffc36
ms.openlocfilehash: fc1281db0271393ec0538e26c2a2d2af09c99f7a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58775262"
---
# <a name="cmfcoutlookbar-class"></a>CMFCOutlookBar (clase)

Un panel con pestañas con el aspecto visual del **Panel de navegación** en Microsoft Outlook 2000 u Outlook 2003. El `CMFCOutlookBar` objeto contiene un [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md) objeto y una serie de pestañas. Las pestañas pueden ser [clase CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md) objetos o `CWnd`-objetos derivados. Para el usuario, la barra de Outlook aparece como una serie de botones y un área de presentación. Cuando el usuario hace clic en un botón, se muestra el panel de control o botón correspondiente .

## <a name="syntax"></a>Sintaxis

```cpp
class CMFCOutlookBar : public CBaseTabbedPane
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|`CMFCOutlookBar::CMFCOutlookBar`|Constructor predeterminado.|
|`CMFCOutlookBar::~CMFCOutlookBar`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Especifica si se puede destruir un panel con pestañas vacío. (Invalida [CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane).)|
|[CMFCOutlookBar::CanAcceptPane](#canacceptpane)|Determina si se puede acoplar a otro panel al panel de barra de Outlook. (Invalida CDockablePane::CanAcceptPane).|
|[CMFCOutlookBar::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Determina si el título para el panel con pestañas muestra el mismo texto como la pestaña activa. (Invalida [CBaseTabbedPane::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname).)|
|[CMFCOutlookBar::Create](#create)|Crea el control de barra de Outlook.|
|[CMFCOutlookBar::CreateCustomPage](#createcustompage)|Crea una pestaña personalizada de barra de Outlook.|
|`CMFCOutlookBar::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|[CMFCOutlookBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Determina si un usuario puede acoplar una barra de controles en el borde exterior de la barra de Outlook.|
|[CMFCOutlookBar::FloatTab](#floattab)|Convierte un panel en flotante, pero solo si el panel se encuentra actualmente en una pestaña desmontable. (Invalida [cbasetabbedpane:: Floattab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|
|[CMFCOutlookBar::GetButtonsFont](#getbuttonsfont)|Devuelve la fuente del texto en los botones de la barra de Outlook.|
|[CMFCOutlookBar::GetTabArea](#gettabarea)|Devuelve el tamaño y posición de las áreas de ficha en la barra de Outlook. (Invalida [CBaseTabbedPane::GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea).)|
|`CMFCOutlookBar::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|
|[CMFCOutlookBar::IsMode2003](#ismode2003)|Determina si el comportamiento de la barra de Outlook imita de Microsoft Office Outlook 2003 (vea la sección Comentarios).|
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|Lo llama [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) después de haber establecido la pestaña activa con la animación.|
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|Lo llama [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) antes de una pestaña de página se establece como la pestaña activa con la animación.|
|[CMFCOutlookBar::OnScroll](#onscroll)|Lo llama el marco de trabajo si la barra de Outlook se desplaza hacia arriba o hacia abajo.|
|[CMFCOutlookBar::RemoveCustomPage](#removecustompage)|Quita una pestaña personalizada de barra de Outlook.|
|[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)|Establece la fuente del texto de los botones de la barra de Outlook.|
|[CMFCOutlookBar::SetMode2003](#setmode2003)|Especifica si el comportamiento de la barra de Outlook imita de Outlook 2003 (vea la sección Comentarios).|

## <a name="remarks"></a>Comentarios

Para obtener un ejemplo de una barra de Outlook, consulte el [OutlookDemo ejemplo: Aplicación de MFC OutlookDemo](../../overview/visual-cpp-samples.md).

## <a name="implementing-the-outlook-bar"></a>Implementación de la barra de Outlook

Para usar el control `CMFCOutlookBar` de la aplicación, siga estos pasos:

1. Incruste un objeto `CMFCOutlookBar` en la clase de ventana de marco principal.

    ```cpp
    class CMainFrame : public CMDIFrameWnd
    {
        // ...
        CMFCOutlookBar m_wndOutlookBar;
        CMFCOutlookBarPane m_wndOutlookPane;
        // ...
    };
    ```

1. Al procesar el mensaje WM_CREATE en el marco principal, llame a la [CMFCOutlookBar::Create](#create) método para crear el control de ficha de la barra de Outlook.

    ```cpp
    m_wndOutlookBar.Create (_T("Shortcuts"),
        this,
        CRect (0, 0, 100, 100),
        ID_VIEW_OUTLOOKBAR,
        WS_CHILD | WS_VISIBLE | CBRS_LEFT);
    ```

1. Obtener un puntero subyacente `CMFCOutlookBarTabCtrl` utilizando [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow).

    ```cpp
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();
    ```

1. Crear un [clase CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md) objeto para cada pestaña que contiene los botones.

    ```cpp
    m_wndOutlookPane.Create(&m_wndOutlookBar,
        AFX_DEFAULT_TOOLBAR_STYLE,
        ID_OUTLOOK_PANE_GENERAL,
        AFX_CBRS_FLOAT | AFX_CBRS_RESIZE);

    // make the Outlook pane detachable (enable docking)
    m_wndOutlookPane.EnableDocking(CBRS_ALIGN_ANY);

    // add buttons
    m_wndOutlookPane.AddButton(theApp.LoadIcon (IDR_MAINFRAME),
        "About",
        ID_APP_ABOUT);

    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_CUSTOM_OPEN_ICON),
        "Open",
        ID_FILE_OPEN);
    ```

1. Llame a [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) para agregar cada nueva pestaña. Establecer el *bDetachable* parámetro en FALSE para que una página no separable. O bien, use [CMFCOutlookBarTabCtrl::AddControl](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol) para agregar páginas desmontables.

    ```cpp
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1, TRUE);
    ```

1. Para agregar un `CWnd`-control derivado (por ejemplo, [CMFCShellTreeCtrl (clase)](../../mfc/reference/cmfcshelltreectrl-class.md)) como una pestaña, crear el control y la llamada [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) para agregarlo a la barra de Outlook.

> [!NOTE]
>  Debe usar identificadores de control único para cada [clase CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md) objeto y para cada `CWnd`-objeto derivado.

Para dinámicamente, agregar o eliminar páginas nuevas en tiempo de ejecución, utilice [CMFCOutlookBar::CreateCustomPage](#createcustompage) y [CMFCOutlookBar::RemoveCustomPage](#removecustompage).

## <a name="outlook-2003-mode"></a>Modo de Outlook 2003

En el modo de Outlook 2003, los botones de ficha se colocan en la parte inferior del panel de barra de Outlook. Cuando no hay espacio suficiente para mostrar los botones, se muestran como iconos en un área de barra de herramientas similares a lo largo de la parte inferior del panel.

Use [CMFCOutlookBar::SetMode2003](#setmode2003) para habilitar el modo de Outlook 2003. Use [CMFCOutlookBarTabCtrl::SetToolbarImageList](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist) para establecer el mapa de bits que contiene los iconos que se muestran en la parte inferior de la barra de Outlook. Los iconos en el mapa de bits deben estar ordenados por índice de tabulación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxoutlookbar.h

##  <a name="allowdestroyemptytabbedpane"></a>  CMFCOutlookBar::AllowDestroyEmptyTabbedPane

Especifica si se puede destruir un panel con pestañas vacío.

```cpp
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si se puede destruir un panel con pestañas vacío; en caso contrario, FALSE. La implementación predeterminada siempre devuelve TRUE.

### <a name="remarks"></a>Comentarios

Si no se puede destruir un panel con pestañas vacío, el marco de trabajo lo oculta en su lugar.

##  <a name="canacceptpane"></a>  CMFCOutlookBar::CanAcceptPane

Determina si se puede acoplar a otro panel al panel de barra de Outlook.

```cpp
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
[in] Un puntero a otro panel que se está acoplando hasta este panel.

### <a name="return-value"></a>Valor devuelto

TRUE si otro panel se puede acoplar en el panel de barra de Outlook; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Si no se admite la barra está en modo de Outlook 2003, el acoplamiento de Outlook, por lo que el valor devuelto es FALSE.

Si el *pBar* parámetro es NULL, este método devuelve FALSE.

En caso contrario, este método se comporta como el método base [cbasepane:: Canacceptpane](../../mfc/reference/cbasepane-class.md#canacceptpane), salvo que incluso si no está habilitado el acoplamiento, una barra de Outlook puede habilitar otra barra de Outlook para acoplar encima de él.

##  <a name="cansetcaptiontexttotabname"></a>  CMFCOutlookBar::CanSetCaptionTextToTabName

Determina si el título para el panel con pestañas muestra el mismo texto como la pestaña activa.

```cpp
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si la barra de título de la ventana de Outlook se establece automáticamente en el texto de la pestaña activa; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use [CBaseTabbedPane::EnableSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname) para habilitar o deshabilitar esta funcionalidad.

En el modo de Outlook 2003, esta opción siempre está habilitada.

##  <a name="create"></a>  CMFCOutlookBar::Create

Crea el control de barra de Outlook.

```cpp
virtual BOOL Create(
    LPCTSTR lpszCaption,
    CWnd* pParentWnd,
    const RECT& rect,
    UINT nID,
    DWORD dwStyle,
    DWORD dwControlBarStyle=AFX_CBRS_RESIZE,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>Parámetros

*lpszCaption*<br/>
[in] Especifica el título de ventana.

*pParentWnd*<br/>
[in] Especifica un puntero a una ventana primaria. No debe ser NULL.

*rect*<br/>
[in] Especifica el tamaño y posición de píxeles de la barra de outlook.

*nID*<br/>
[in] Especifica el identificador de control. Debe ser distinto de otro identificadores utilizados en la aplicación de control.

*dwStyle*<br/>
[in] Especifica el estilo de barra de control deseada. Para los valores posibles, vea [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwControlBarStyle*<br/>
[in] Especifica los estilos definidos en la biblioteca especiales.

*pContext*<br/>
[in] Crear el contexto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método es correcto; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Construir un `CMFCOutlookBar` objeto en dos pasos. Llamar primero al constructor y, a continuación, llame a `Create`, que crea el control de barra de outlook y lo adjunta a la `CMFCOutlookBar` objeto.

Consulte [cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex) para obtener la lista de los estilos definidos en la biblioteca disponibles que especificarse mediante *dwControlBarStyle*.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar el `Create` método de la `CMFCOutlookBar` clase. Este fragmento de código forma parte de la [ejemplo Outlook con varias vistas](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]

##  <a name="createcustompage"></a>  CMFCOutlookBar::CreateCustomPage

Crea una pestaña personalizada de barra de Outlook.

```cpp
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,
    BOOL bActivatePage=TRUE,
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,
    BOOL bEnableTextLabels=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszPageName*<br/>
[in] La etiqueta de página.

*bActivatePage*<br/>
[in] Si es TRUE, la página se convierte en activa tras su creación.

*dwEnabledDocking*<br/>
[in] Una combinación de marcas CBRS_ALIGN_ que especifica los lados de acoplamiento habilitados cuando se desasocia la página.

*bEnableTextLabels*<br/>
[in] Si es TRUE, se habilitan las etiquetas de texto para los botones que residen en la página.

### <a name="return-value"></a>Valor devuelto

Un puntero a la página recién creada, o NULL si no se pudo crear.

### <a name="remarks"></a>Comentarios

Utilice este método para que los usuarios puedan crear páginas personalizadas de la barra de Outlook. Puede crear hasta 100 páginas por aplicación. El control de la página identificadores inicie desde 0xF000. La creación se produce un error si el número total de páginas personalizadas de la barra de Outlook es superior a 100.

Use [CMFCOutlookBar::RemoveCustomPage](#removecustompage) eliminar páginas personalizadas.

##  <a name="doesallowdyninsertbefore"></a>  CMFCOutlookBar::DoesAllowDynInsertBefore

Especifica si un usuario puede acoplar un panel en el borde exterior de la barra de Outlook.

```
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve FALSE.

### <a name="remarks"></a>Comentarios

Las llamadas de framework la `DoesAllowDynInsertBefore` método cuando busca una ubicación acoplar un panel dinámico. Si la función devuelve FALSE, el marco de trabajo no admite el acoplamiento de cualquier panel dinámico en los bordes externos del panel.

Normalmente, se crea una barra de Outlook como un control estático no flotante. Puede invalidar esta función en una clase derivada y devolver TRUE para cambiar este comportamiento.

> [!NOTE]
>  Porque paneles dinámicos comprobación el estado de acopladas paneles estáticos al acoplamiento, debe acoplar paneles dinámicos después paneles estáticos siempre que sea posible.

##  <a name="floattab"></a>  CMFCOutlookBar::FloatTab

Flota un panel.

```cpp
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide);
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
[in] Un puntero al panel en flotante.

*nTabID*<br/>
[in] Índice de base cero de la pestaña a float.

*dockMethod*<br/>
[in] Especifica el método se usa para hacer flotar el panel.  Para obtener más información, consulte [cbasetabbedpane:: Floattab](../../mfc/reference/cbasetabbedpane-class.md#floattab).

*bHide*<br/>
[in] TRUE para ocultar el panel antes flotante; en caso contrario, FALSE. A diferencia de la versión de la clase base de este método, este parámetro no tiene un valor predeterminado.

### <a name="return-value"></a>Valor devuelto

TRUE si el panel de flota; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método es similar a [cbasetabbedpane:: Floattab](../../mfc/reference/cbasetabbedpane-class.md#floattab) , salvo que no permite la última pestaña restante en un control de barra de Outlook a float.

##  <a name="getbuttonsfont"></a>  CMFCOutlookBar::GetButtonsFont

Devuelve a la fuente del texto en la página de fichas de botón de la barra de Outlook.

```cpp
CFont* GetButtonsFont() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto de fuente que se utiliza para mostrar texto en Outlook barra de pestañas de botón de página.

### <a name="remarks"></a>Comentarios

Utilice esta función para recuperar la fuente que se usa para mostrar el texto en las fichas de botón de página de Outlook. Puede establecer la fuente mediante una llamada en [CMFCOutlookBar::SetButtonsFont](#setbuttonsfont).

##  <a name="gettabarea"></a>  CMFCOutlookBar::GetTabArea

Determina el tamaño y posición de las áreas de ficha en la barra de Outlook.

```cpp
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Parámetros

*rectTabAreaTop*<br/>
[out] Cuando la función devuelve, contiene el tamaño y posición (en coordenadas de cliente) del área superior de ficha.

*rectTabAreaBottom*<br/>
[out] Cuando la función devuelve, contiene el tamaño y posición (en coordenadas de cliente) del área inferior de ficha.

### <a name="remarks"></a>Comentarios

El marco llama a este método para determinar el tipo de acoplamiento en el panel de destino. Cuando el marco de trabajo determina que el usuario arrastra el panel para acoplar en el área de pestañas del panel de destino, intenta agregar el primer panel como una nueva pestaña del panel de destino. En caso contrario, intenta acoplar el primer panel en un lado correspondiente del panel de destino. El marco de trabajo crea un nuevo contenedor con un control deslizante para acomodar el panel acoplado adicional.

La implementación predeterminada de `GetTabArea` devuelve todo el área cliente de la barra de Outlook si la barra de Outlook es estática; que es, si no se puede desplazar la barra de Outlook. En caso contrario, devuelve el área que toman los botones de página en la parte superior e inferior del control de barra de Outlook.

Invalide este método en la clase derivada de `CMFCOutlookBar` para cambiar este comportamiento.

##  <a name="ismode2003"></a>  CMFCOutlookBar::IsMode2003

Especifica si el comportamiento de la barra de Outlook imita de Microsoft Office Outlook 2003.

```cpp
BOOL IsMode2003() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la barra de Outlook se ejecuta en modo de Microsoft Office 2003; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Puede habilitar este modo mediante [CMFCOutlookBar::SetMode2003](#setmode2003).

##  <a name="onafteranimation"></a>  CMFCOutlookBar::OnAfterAnimation

Lo llama [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) después de haber establecido la pestaña activa con la animación.

```cpp
virtual void OnAfterAnimation(int nPage);
```

### <a name="parameters"></a>Parámetros

*nPage*<br/>
[in] Índice de base cero de la página de ficha que se ha realizado activo.

### <a name="remarks"></a>Comentarios

El efecto visual de la configuración de la pestaña activa depende de si ha habilitado la animación. Para obtener más información, consulte [CMFCOutlookBarTabCtrl::EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation).

##  <a name="onbeforeanimation"></a>  CMFCOutlookBar::OnBeforeAnimation

Lo llama [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) antes de una pestaña de página se establece como la pestaña activa con la animación.

```cpp
virtual BOOL OnBeforeAnimation(int nPage);
```

### <a name="parameters"></a>Parámetros

*nPage*<br/>
[in] Índice de base cero de la página de ficha que se va a establecerse en activo.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si debe utilizarse la animación en la configuración de la pestaña activa de nuevo, o FALSE si se debe deshabilitar la animación.

### <a name="remarks"></a>Comentarios

##  <a name="onscroll"></a>  CMFCOutlookBar::OnScroll

Lo llama el marco de trabajo si la barra de Outlook se desplaza hacia arriba o hacia abajo.

```cpp
virtual void OnScroll(BOOL bDown);
```

### <a name="parameters"></a>Parámetros

*bDown*<br/>
[in] TRUE si la barra de Outlook está al desplazarse hacia abajo, o FALSE si se desplaza hacia arriba.

### <a name="remarks"></a>Comentarios

##  <a name="removecustompage"></a>  CMFCOutlookBar::RemoveCustomPage

Quita una página personalizada de pestaña de barra de Outlook.

```cpp
BOOL RemoveCustomPage(
    UINT uiPage,
    CMFCOutlookBarTabCtrl* pTargetWnd);
```

### <a name="parameters"></a>Parámetros

*uiPage*<br/>
[in] Índice de base cero de la página en la ventana de Outlook primaria.

*pTargetWnd*<br/>
[in] Pointerto la ventana de Outlook primaria.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha quitado correctamente; la página personalizada en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Llame a esta función para eliminar las páginas personalizadas. Cuando se quita la página de su Id. de control se devuelve al grupo de identificadores disponibles.

Debe proporcionar un puntero a [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md) objeto en el que reside la página que se va a quitar actualmente. Tenga en cuenta que un usuario puede mover las páginas separables entre las distintas barras de Outlook, pero la información sobre una página personalizada reside en el objeto de la barra de Outlook para el que ha llamado [CMFCOutlookBar::CreateCustomPage](#createcustompage).

Use [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow) para obtener un puntero a la ventana de Outlook.

##  <a name="setbuttonsfont"></a>  CMFCOutlookBar::SetButtonsFont

Establece la fuente del texto de los botones de la barra de Outlook.

```cpp
void SetButtonsFont(
    CFont* pFont,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parámetros

*pFont*<br/>
[in] Especifica la nueva fuente.

*bRedraw*<br/>
[in] Si es TRUE, se volverá a dibujar la barra de Outlook.

### <a name="remarks"></a>Comentarios

Utilice este método para establecer una fuente para el texto mostrado en los botones de página de ficha de outlook.

##  <a name="setmode2003"></a>  CMFCOutlookBar::SetMode2003

Especifica si el comportamiento de la barra de Outlook imita de Outlook 2003.

```cpp
void SetMode2003(BOOL bMode2003=TRUE);
```

### <a name="parameters"></a>Parámetros

*bMode2003*<br/>
[in] Si es TRUE, el modo de Office 2003 está habilitado.

### <a name="remarks"></a>Comentarios

Utilice esta función para habilitar o deshabilitar el modo de Office 2003. En este modo, la barra de Outlook tiene una barra de herramientas adicional con un botón de personalización. El comportamiento de la barra de Outlook se ajusta al comportamiento de la barra de Outlook de Microsoft Office 2003.

De forma predeterminada, este modo está deshabilitado.

> [!NOTE]
>  Esta función debe llamarse antes [CMFCOutlookBar::Create](#create).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CBaseTabbedPane (clase)](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBarTabCtrl (clase)](../../mfc/reference/cmfcoutlookbartabctrl-class.md)<br/>
[CMFCOutlookBarPane (clase)](../../mfc/reference/cmfcoutlookbarpane-class.md)
