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
ms.openlocfilehash: fe328cb0d857ff9154624d218b1b56362890ce81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369654"
---
# <a name="cmfcoutlookbar-class"></a>CMFCOutlookBar (clase)

Un panel con pestañas con el aspecto visual del **Panel de navegación** en Microsoft Outlook 2000 u Outlook 2003. El `CMFCOutlookBar` objeto contiene un [CMFCOutlookBarTabCtrl clase](../../mfc/reference/cmfcoutlookbartabctrl-class.md) objeto y una serie de fichas. Las fichas pueden ser [CMFCOutlookBarPane (clase)](../../mfc/reference/cmfcoutlookbarpane-class.md) objetos u `CWnd`objetos derivados. Para el usuario, la barra de Outlook aparece como una serie de botones y un área de presentación. Cuando el usuario hace clic en un botón, se muestra el panel de control o botón correspondiente .

## <a name="syntax"></a>Sintaxis

```cpp
class CMFCOutlookBar : public CBaseTabbedPane
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCOutlookBar::CMFCOutlookBar`|Constructor predeterminado.|
|`CMFCOutlookBar::~CMFCOutlookBar`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Especifica si se puede destruir un panel con pestañas vacío. (Reemplaza [CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane).)|
|[CMFCOutlookBar::CanAcceptPane](#canacceptpane)|Determina si se puede acoplar otro panel al panel de la barra de Outlook. (Reemplaza CDockablePane::CanAcceptPane.)|
|[CMFCOutlookBar::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Determina si el título del panel con fichas muestra el mismo texto que la ficha activa (Reemplaza [CBaseTabbedPane::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname).)|
|[CMFCOutlookBar::Crear](#create)|Crea el control de barra de Outlook.|
|[CMFCOutlookBar::CreateCustomPage](#createcustompage)|Crea una pestaña de barra de Outlook personalizada.|
|`CMFCOutlookBar::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|[CMFCOutlookBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Determina si un usuario puede acoplar una barra de control en el borde exterior de la barra de Outlook.|
|[CMFCOutlookBar::FloatTab](#floattab)|Flota un panel, pero solo si el panel reside actualmente en una ficha desmontable.(Overrides [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|
|[CMFCOutlookBar::GetButtonsFont](#getbuttonsfont)|Devuelve la fuente del texto en los botones de la barra de Outlook.|
|[CMFCOutlookBar::GetTabArea](#gettabarea)|Devuelve el tamaño y la posición de las áreas de pestaña en la barra de Outlook. (Reemplaza [CBaseTabbedPane::GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea).)|
|`CMFCOutlookBar::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|[CMFCOutlookBar::IsMode2003](#ismode2003)|Determina si el comportamiento de la barra de Outlook imita el de Microsoft Office Outlook 2003 (consulte Comentarios).|
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|Llamado por [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) después de que la pestaña activa se ha establecido mediante animación.|
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|Llamado por [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) antes de que una página de ficha se establece como la pestaña activa mediante animación.|
|[CMFCOutlookBar::OnScroll](#onscroll)|Llamado por el marco de trabajo si la barra de Outlook se desplaza hacia arriba o hacia abajo.|
|[CMFCOutlookBar::RemoveCustomPage](#removecustompage)|Quita una pestaña de barra de Outlook personalizada.|
|[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)|Establece la fuente del texto en los botones de la barra de Outlook.|
|[CMFCOutlookBar::SetMode2003](#setmode2003)|Especifica si el comportamiento de la barra de Outlook imita el de Outlook 2003 (consulte Comentarios).|

## <a name="remarks"></a>Observaciones

Para obtener un ejemplo de una barra de Outlook, vea el [ejemplo de OutlookDemo: MFC OutlookDemo Application](../../overview/visual-cpp-samples.md).

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

1. Al procesar el mensaje WM_CREATE en el marco principal, llame a la [CMFCOutlookBar::Create](#create) método para crear el control de ficha de barra de Outlook.

    ```cpp
    m_wndOutlookBar.Create (_T("Shortcuts"),
        this,
        CRect (0, 0, 100, 100),
        ID_VIEW_OUTLOOKBAR,
        WS_CHILD | WS_VISIBLE | CBRS_LEFT);
    ```

1. Obtener un puntero al `CMFCOutlookBarTabCtrl` subyacente mediante [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow).

    ```cpp
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();
    ```

1. Cree un [CMFCOutlookBarPane clase](../../mfc/reference/cmfcoutlookbarpane-class.md) objeto para cada ficha que contiene botones.

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

1. Llame a [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) para agregar cada nueva pestaña. Establezca el *bDetachable* parámetro FALSE para que una página no desmontable. O bien, utilice [CMFCOutlookBarTabCtrl::AddControl](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol) para agregar páginas desmontables.

    ```cpp
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1, TRUE);
    ```

1. Para agregar `CWnd`un control derivado (por ejemplo, [CMFCShellTreeCtrl (Clase)](../../mfc/reference/cmfcshelltreectrl-class.md)como ficha, cree el control y llame a [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) para agregarlo a la barra de Outlook.

> [!NOTE]
> Debe usar identificadores de control únicos para cada [CMFCOutlookBarPane clase](../../mfc/reference/cmfcoutlookbarpane-class.md) objeto y para cada `CWnd`-objeto derivado.

Para agregar o eliminar dinámicamente nuevas páginas en tiempo de ejecución, utilice [CMFCOutlookBar::CreateCustomPage](#createcustompage) y [CMFCOutlookBar::RemoveCustomPage](#removecustompage).

## <a name="outlook-2003-mode"></a>Modo Outlook 2003

En el modo de Outlook 2003, los botones de pestaña se colocan en la parte inferior del panel de la barra de Outlook. Cuando no hay suficiente espacio para mostrar los botones, se muestran como iconos en un área similar a una barra de herramientas a lo largo de la parte inferior del panel.

Utilice [CMFCOutlookBar::SetMode2003](#setmode2003) para habilitar el modo de Outlook 2003. Utilice [CMFCOutlookBarTabCtrl::SetToolbarImageList](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist) para establecer el mapa de bits que contiene los iconos que se muestran en la parte inferior de la barra de Outlook. Los iconos del mapa de bits deben ordenarse por índice de tabulación.

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

## <a name="cmfcoutlookbarallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a>CMFCOutlookBar::AllowDestroyEmptyTabbedPane

Especifica si se puede destruir un panel con pestañas vacío.

```cpp
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi se puede destruir un panel con pestañas vacío; de lo contrario, FALSE. La implementación predeterminada siempre devuelve TRUE.

### <a name="remarks"></a>Observaciones

Si no se puede destruir un panel con pestañas vacío, el marco de trabajo lo oculta en su lugar.

## <a name="cmfcoutlookbarcanacceptpane"></a><a name="canacceptpane"></a>CMFCOutlookBar::CanAcceptPane

Determina si se puede acoplar otro panel al panel de la barra de Outlook.

```cpp
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
[en] Puntero a otro panel que se está acoplando a este panel.

### <a name="return-value"></a>Valor devuelto

TRUESi se puede acoplar otro panel al panel de la barra de Outlook; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Si la barra de Outlook está en modo Outlook 2003, no se admite el acoplamiento, por lo que el valor devuelto es FALSE.

Si el *pBar* parámetro es NULL, este método devuelve FALSE.

De lo contrario, este método se comporta como el método base [CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane), excepto que incluso si el acoplamiento no está habilitado, una barra de Outlook todavía puede habilitar otra barra de Outlook para acoplarse sobre ella.

## <a name="cmfcoutlookbarcansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a>CMFCOutlookBar::CanSetCaptionTextToTabName

Determina si el título del panel con fichas muestra el mismo texto que la pestaña activa.

```cpp
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el título de la ventana de la barra de Outlook se establece automáticamente en el texto de la pestaña activa; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Use [CBaseTabbedPane::EnableSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname) para habilitar o deshabilitar esta funcionalidad.

En el modo de Outlook 2003, esta configuración siempre está habilitada.

## <a name="cmfcoutlookbarcreate"></a><a name="create"></a>CMFCOutlookBar::Crear

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
[en] Especifica el título de la ventana.

*pParentWnd*<br/>
[en] Especifica un puntero a una ventana primaria. No debe ser NULL.

*Rect*<br/>
[en] Especifica el tamaño y la posición de la barra de perspectiva en píxeles.

*nID*<br/>
[en] Especifica el identificador de control. Debe ser distinto de otros identificadores de control utilizados en la aplicación.

*dwStyle*<br/>
[en] Especifica el estilo de barra de control deseado. Para ver los valores posibles, consulte [Estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles)de ventana .

*dwControlBarStyle*<br/>
[en] Especifica los estilos especiales definidos por la biblioteca.

*pContext*<br/>
[en] Crear contexto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método es correcto; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Construir un `CMFCOutlookBar` objeto en dos pasos. En primer lugar, llame `Create`al constructor y, a continuación, `CMFCOutlookBar` llame a , que crea el control de barra de outlook y lo adjunta al objeto.

Vea [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) para obtener la lista de los estilos definidos por la biblioteca disponibles que especificará *dwControlBarStyle*.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `Create` muestra `CMFCOutlookBar` cómo utilizar el método de la clase. Este fragmento de código forma parte del [ejemplo de Outlook Multi Views.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]

## <a name="cmfcoutlookbarcreatecustompage"></a><a name="createcustompage"></a>CMFCOutlookBar::CreateCustomPage

Crea una pestaña de barra de Outlook personalizada.

```cpp
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,
    BOOL bActivatePage=TRUE,
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,
    BOOL bEnableTextLabels=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszPageName*<br/>
[en] La etiqueta de página.

*bActivatePage*<br/>
[en] Si es TRUE, la página se activa al crearse.

*dwEnabledDocking*<br/>
[en] Una combinación de indicadores CBRS_ALIGN_ que especifica los lados de acoplamiento habilitados cuando se separa la página.

*bEnableTextLabels*<br/>
[en] Si es TRUE, las etiquetas de texto están habilitadas para los botones que residen en la página.

### <a name="return-value"></a>Valor devuelto

Un puntero a la página recién creada, o NULL si se produjo un error en la creación.

### <a name="remarks"></a>Observaciones

Utilice este método para permitir a los usuarios crear páginas de barra de Outlook personalizadas. Puede crear hasta 100 páginas por aplicación. Los iDs de control de página comienzan a partir de 0xF000. Se produce un error en la creación si el número total de páginas de barra de Outlook personalizadas supera 100.

Utilice [CMFCOutlookBar::RemoveCustomPage](#removecustompage) para eliminar páginas personalizadas.

## <a name="cmfcoutlookbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFCOutlookBar::DoesAllowDynInsertBefore

Especifica si un usuario puede acoplar un panel en el borde exterior de la barra de Outlook.

```
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve FALSE.

### <a name="remarks"></a>Observaciones

El marco `DoesAllowDynInsertBefore` de trabajo llama al método cuando busca una ubicación para acoplar un panel dinámico. Si la función devuelve FALSE, el marco de trabajo no permite el acoplamiento de ningún panel dinámico en los bordes exteriores del panel.

Normalmente, se crea una barra de Outlook como un control estático no flotante. Puede invalidar esta función en una clase derivada y devolver TRUE para cambiar este comportamiento.

> [!NOTE]
> Dado que los paneles dinámicos comprueban el estado de los paneles estáticos acoplados al acoplar, debe acoplar paneles dinámicos después de paneles estáticos siempre que sea posible.

## <a name="cmfcoutlookbarfloattab"></a><a name="floattab"></a>CMFCOutlookBar::FloatTab

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
[en] Puntero al panel para flotar.

*nTabID*<br/>
[en] El índice de base cero de la pestaña para flotar.

*dockMethod*<br/>
[en] Especifica el método que se usará para que el panel sea flotante.  Para obtener más información, vea [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).

*bOcultar*<br/>
[en] TRUE para ocultar el panel antes de flotar; de lo contrario, FALSE. A diferencia de la versión de clase base de este método, este parámetro no tiene un valor predeterminado.

### <a name="return-value"></a>Valor devuelto

TRUESi el panel flotaba; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método es como [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab) excepto que no habilita la última pestaña restante en un control de barra de Outlook para flotar.

## <a name="cmfcoutlookbargetbuttonsfont"></a><a name="getbuttonsfont"></a>CMFCOutlookBar::GetButtonsFont

Devuelve la fuente del texto en las pestañas de los botones de página de la barra de Outlook.

```cpp
CFont* GetButtonsFont() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de fuente que se utiliza para mostrar texto en las pestañas de botón de la página de la barra de Outlook.

### <a name="remarks"></a>Observaciones

Utilice esta función para recuperar la fuente que se utiliza para mostrar el texto en las pestañas de botón de página de Outlook. Puede establecer la fuente llamando a [CMFCOutlookBar::SetButtonsFont](#setbuttonsfont).

## <a name="cmfcoutlookbargettabarea"></a><a name="gettabarea"></a>CMFCOutlookBar::GetTabArea

Determina el tamaño y la posición de las áreas de pestaña en la barra de Outlook.

```cpp
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Parámetros

*rectTabAreaTop*<br/>
[fuera] Contiene el tamaño y la posición (en las coordenadas de cliente) del área de ficha superior cuando se devuelve la función.

*rectTabAreaBottom*<br/>
[fuera] Contiene el tamaño y la posición (en las coordenadas de cliente) del área de ficha inferior cuando se devuelve la función.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método para determinar el tipo de acoplamiento al panel de destino. Cuando el marco de trabajo determina que el usuario arrastra el panel que se va a acoplar sobre el área de ficha del panel de destino, intenta agregar el primer panel como una nueva pestaña del panel de destino. De lo contrario, intenta acoplar el primer panel en un lado adecuado del panel de destino. El marco de trabajo crea un nuevo contenedor con un control deslizante para dar cabida al panel acoplado adicional.

La implementación `GetTabArea` predeterminada de devuelve todo el área de cliente de la barra de Outlook si la barra de Outlook es estática; es decir, si la barra de Outlook no puede flotar. De lo contrario, devuelve el área que los botones de página toman en la parte superior e inferior del control de barra de Outlook.

Invalide este método en `CMFCOutlookBar` la clase derivada de para cambiar este comportamiento.

## <a name="cmfcoutlookbarismode2003"></a><a name="ismode2003"></a>CMFCOutlookBar::IsMode2003

Especifica si el comportamiento de la barra de Outlook imita el de Microsoft Office Outlook 2003.

```cpp
BOOL IsMode2003() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la barra de Outlook se ejecuta en modo Microsoft Office 2003; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Puede habilitar este modo mediante [CMFCOutlookBar::SetMode2003](#setmode2003).

## <a name="cmfcoutlookbaronafteranimation"></a><a name="onafteranimation"></a>CMFCOutlookBar::OnAfterAnimation

Llamado por [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) después de que la pestaña activa se ha establecido mediante animación.

```cpp
virtual void OnAfterAnimation(int nPage);
```

### <a name="parameters"></a>Parámetros

*nPage*<br/>
[en] El índice de base cero de la página de fichas que se ha activo.

### <a name="remarks"></a>Observaciones

El efecto visual de establecer la pestaña activa depende de si ha habilitado la animación. Para obtener más información, vea [CMFCOutlookBarTabCtrl::EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation).

## <a name="cmfcoutlookbaronbeforeanimation"></a><a name="onbeforeanimation"></a>CMFCOutlookBar::OnBeforeAnimation

Llamado por [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) antes de que una página de ficha se establece como la pestaña activa mediante animación.

```cpp
virtual BOOL OnBeforeAnimation(int nPage);
```

### <a name="parameters"></a>Parámetros

*nPage*<br/>
[en] El índice de base cero de la página de pestañas que está a punto de establecerse activa.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se debe usar la animación para establecer la nueva pestaña activa, o FALSE si se debe deshabilitar la animación.

### <a name="remarks"></a>Observaciones

## <a name="cmfcoutlookbaronscroll"></a><a name="onscroll"></a>CMFCOutlookBar::OnScroll

Llamado por el marco de trabajo si la barra de Outlook se desplaza hacia arriba o hacia abajo.

```cpp
virtual void OnScroll(BOOL bDown);
```

### <a name="parameters"></a>Parámetros

*bDown*<br/>
[en] TRUESi la barra de Outlook se desplaza hacia abajo o FALSE si se desplaza hacia arriba.

### <a name="remarks"></a>Observaciones

## <a name="cmfcoutlookbarremovecustompage"></a><a name="removecustompage"></a>CMFCOutlookBar::RemoveCustomPage

Quita una página de pestaña de barra de Outlook personalizada.

```cpp
BOOL RemoveCustomPage(
    UINT uiPage,
    CMFCOutlookBarTabCtrl* pTargetWnd);
```

### <a name="parameters"></a>Parámetros

*uiPage*<br/>
[en] El índice de base cero de la página en la ventana principal de Outlook.

*pTargetWnd*<br/>
[en] Puntero a la ventana principal de Outlook.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la página personalizada se ha quitado correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Llame a esta función para eliminar páginas personalizadas. Cuando se quita la página, su identificador de control se devuelve al grupo de identificadores disponibles.

Debe proporcionar un puntero a [CMFCOutlookBarTabCtrl clase](../../mfc/reference/cmfcoutlookbartabctrl-class.md) objeto en el que reside actualmente la página que se va a quitar. Tenga en cuenta que un usuario puede mover páginas desmontables entre diferentes barras de Outlook, pero la información sobre una página personalizada reside en el objeto de barra de Outlook para el que ha llamado [CMFCOutlookBar::CreateCustomPage](#createcustompage).

Use [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow) para obtener un puntero a la ventana de Outlook.

## <a name="cmfcoutlookbarsetbuttonsfont"></a><a name="setbuttonsfont"></a>CMFCOutlookBar::SetButtonsFont

Establece la fuente del texto en los botones de la barra de Outlook.

```cpp
void SetButtonsFont(
    CFont* pFont,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parámetros

*pFont*<br/>
[en] Especifica la nueva fuente.

*bRedraw*<br/>
[en] Si es TRUE, se volverá a dibujar la barra de Outlook.

### <a name="remarks"></a>Observaciones

Utilice este método para establecer una fuente para el texto que se muestra en los botones de página de la pestaña de Outlook.

## <a name="cmfcoutlookbarsetmode2003"></a><a name="setmode2003"></a>CMFCOutlookBar::SetMode2003

Especifica si el comportamiento de la barra de Outlook imita el de Outlook 2003.

```cpp
void SetMode2003(BOOL bMode2003=TRUE);
```

### <a name="parameters"></a>Parámetros

*bMode2003*<br/>
[en] Si es TRUE, el modo de Office 2003 está habilitado.

### <a name="remarks"></a>Observaciones

Utilice esta función para habilitar o deshabilitar el modo de Office 2003. En este modo, la barra de Outlook tiene una barra de herramientas adicional con un botón de personalización. El comportamiento de la barra de Outlook se ajusta al comportamiento de la barra de Outlook en Microsoft Office 2003.

De forma predeterminada, este modo está deshabilitado.

> [!NOTE]
> Esta función debe llamarse antes de [CMFCOutlookBar::Create](#create).

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CBaseTabbedPane (clase)](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md)<br/>
[CMFCOutlookBarPane Clase](../../mfc/reference/cmfcoutlookbarpane-class.md)
