---
title: CMFCOutlookBarTabCtrl Class
ms.date: 10/18/2018
f1_keywords:
- CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::AddControl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::Create
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableInPlaceEdit
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableScrollButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetVisiblePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsMode2003
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowOptions
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetActiveTab
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetPageButtonTextAlign
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetToolbarImageList
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetVisiblePageButtons
helpviewer_keywords:
- CMFCOutlookBarTabCtrl [MFC], AddControl
- CMFCOutlookBarTabCtrl [MFC], CanShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], CanShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], Create
- CMFCOutlookBarTabCtrl [MFC], EnableAnimation
- CMFCOutlookBarTabCtrl [MFC], EnableInPlaceEdit
- CMFCOutlookBarTabCtrl [MFC], EnableScrollButtons
- CMFCOutlookBarTabCtrl [MFC], GetBorderSize
- CMFCOutlookBarTabCtrl [MFC], GetVisiblePageButtons
- CMFCOutlookBarTabCtrl [MFC], IsAnimation
- CMFCOutlookBarTabCtrl [MFC], IsMode2003
- CMFCOutlookBarTabCtrl [MFC], OnShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowOptions
- CMFCOutlookBarTabCtrl [MFC], SetActiveTab
- CMFCOutlookBarTabCtrl [MFC], SetBorderSize
- CMFCOutlookBarTabCtrl [MFC], SetPageButtonTextAlign
- CMFCOutlookBarTabCtrl [MFC], SetToolbarImageList
- CMFCOutlookBarTabCtrl [MFC], SetVisiblePageButtons
ms.assetid: b1f2b3f7-cc59-49a3-99d8-7ff9b37c044b
ms.openlocfilehash: 309b74126f57e76aa6399f57382d88fee4400700
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369660"
---
# <a name="cmfcoutlookbartabctrl-class"></a>CMFCOutlookBarTabCtrl Class

Un control de pestaña que tiene el aspecto visual del **Panel de navegación** de Microsoft Outlook.
Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

## <a name="syntax"></a>Sintaxis

```
class CMFCOutlookBarTabCtrl : public CMFCBaseTabCtrl
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCOutlookBarTabCtrl::CMFCOutlookBarTabCtrl`|Constructor predeterminado.|
|`CMFCOutlookBarTabCtrl::~CMFCOutlookBarTabCtrl`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCOutlookBarTabCtrl::AddControl](#addcontrol)|Agrega un control de Windows como una nueva pestaña en la barra de Outlook.|
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|Llamado por el marco de trabajo para determinar las dimensiones del cuadro `CMFCBaseTabCtrl::CalcRectEdit`de edición que aparece cuando un usuario cambia el nombre de una ficha. (Reemplaza .)|
|[CMFCOutlookBarTabCtrl::CanShowFewerPageButtons](#canshowfewerpagebuttons)|Llamado por el marco de trabajo durante las operaciones de cambio de tamaño para determinar si se pueden mostrar menos botones de página de la pestaña de la barra de Outlook que están visibles actualmente.|
|[CMFCOutlookBarTabCtrl::CanShowMorePageButtons](#canshowmorepagebuttons)|Llamado por el marco de trabajo durante las operaciones de cambio de tamaño para determinar si se pueden mostrar más botones de página de la barra de Outlook que están visibles actualmente.|
|[CMFCOutlookBarTabCtrl::Crear](#create)|Crea el control de pestaña de la barra de Outlook.|
|`CMFCOutlookBarTabCtrl::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|[CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)|Especifica si la animación que se produce durante el cambio entre fichas activas está habilitada.|
|[CMFCOutlookBarTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|Especifica si un usuario puede modificar las etiquetas de texto en los botones de ficha de la barra de Outlook. (Reemplaza [CMFCBaseTabCtrl::EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit).)|
|[CMFCOutlookBarTabCtrl::EnableScrollButtons](#enablescrollbuttons)|Llamado por el marco de trabajo para habilitar botones que permiten al usuario desplazarse por los botones en el panel de la barra de Outlook.|
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|Identifica el panel que contiene un punto especificado. (Reemplaza [CMFCBaseTabCtrl::FindTargetWnd](../../mfc/reference/cmfcbasetabctrl-class.md#findtargetwnd).)|
|[CMFCOutlookBarTabCtrl::GetBorderSize](#getbordersize)|Devuelve el tamaño de borde del control de ficha Outlook.|
|`CMFCOutlookBarTabCtrl::GetTabArea`|Recupera el tamaño y la posición del área de ficha del control de ficha. (Reemplaza [CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea).)|
|`CMFCOutlookBarTabCtrl::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|[CMFCOutlookBarTabCtrl::GetVisiblePageButtons](#getvisiblepagebuttons)||
|[CMFCOutlookBarTabCtrl::IsAnimation](#isanimation)|Determina si la animación que se produce durante el cambio entre pestañas activas está habilitada.|
|[CMFCOutlookBarTabCtrl::IsMode2003](#ismode2003)|Determina si el control de pestaña de barra de Outlook está en un modo que emula Microsoft Outlook 2003.|
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|Determina si un punto está dentro del área de tabulación. (Reemplaza [CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea).)|
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|Determina si una ficha es desmontable. (Reemplaza [CMFCBaseTabCtrl::IsTabDetachable](../../mfc/reference/cmfcbasetabctrl-class.md#istabdetachable).)|
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|Llamado por el marco de trabajo cuando se inserta o quita una pestaña. (Invalida `CMFCBaseTabCtrl::OnChangeTabs`).|
|[CMFCOutlookBarTabCtrl::OnShowFewerPageButtons](#onshowfewerpagebuttons)|Llamado por el marco de trabajo para disminuir el número de botones de página de pestañas que están visibles.|
|[CMFCOutlookBarTabCtrl::OnShowMorePageButtons](#onshowmorepagebuttons)|Llamado por el marco de trabajo para aumentar el número de botones de página de pestañas que están visibles.|
|[CMFCOutlookBarTabCtrl::OnShowOptions](#onshowoptions)|Muestra el cuadro de diálogo **Opciones del panel de navegación.**|
|`CMFCOutlookBarTabCtrl::RecalcLayout`|Vuelve a calcular el diseño interno del control de ficha. (Reemplaza [CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout).)|
|[CMFCOutlookBarTabCtrl::SetActiveTab](#setactivetab)|Establece la ficha activa (Reemplaza [CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab).)|
|[CMFCOutlookBarTabCtrl::SetBorderSize](#setbordersize)|Establece el tamaño del borde del control de ficha Outlook.|
|[CMFCOutlookBarTabCtrl::SetPageButtonTextAlign](#setpagebuttontextalign)|Establece la alineación de las etiquetas de texto en los botones de tabulación de la barra de Outlook.|
|[CMFCOutlookBarTabCtrl::SetToolbarImageList](#settoolbarimagelist)|Establece el mapa de bits que contiene los iconos que se muestran en la parte inferior de la barra de Outlook en modo Outlook 2003 (consulte [CMFCOutlookBar (Clase)](../../mfc/reference/cmfcoutlookbar-class.md)).|
|[CMFCOutlookBarTabCtrl::SetVisiblePageButtons](#setvisiblepagebuttons)||

## <a name="remarks"></a>Observaciones

Para crear una barra de Outlook que `CMFCOutlookBar` tenga compatibilidad con el acoplamiento, use un objeto para hospedar el control de ficha de la barra de Outlook. Para obtener más información, vea [CMFCOutlookBar (Clase)](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se `CMFCOutlookBarTabCtrl` muestra cómo inicializar `CMFCOutlookBarTabCtrl` un objeto y utilizar varios métodos en la clase. En el ejemplo se muestra cómo habilitar la edición in situ de la etiqueta de texto en los botones de página de pestañades la barra de Outlook, habilitar la animación, habilitar los controles de desplazamiento que permiten al usuario desplazarse por los botones del panel de la barra de Outlook, establecer el tamaño del borde del control de ficha de Outlook y establecer la alineación de las etiquetas de texto en los botones de tabulación de la barra de Outlook. Este fragmento de código forma parte del [ejemplo de demostración](../../overview/visual-cpp-samples.md)de Outlook.

[!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_1.cpp)]
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)

[CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxoutlookbartabctrl.h

## <a name="cmfcoutlookbartabctrladdcontrol"></a><a name="addcontrol"></a>CMFCOutlookBarTabCtrl::AddControl

Agrega un control de Windows como una nueva pestaña en la barra de Outlook.

```
void AddControl(
    CWnd* pWndCtrl,
    LPCTSTR lpszName,
    int nImageID=-1,
    BOOL bDetachable=TRUE,
    DWORD dwControlBarStyle=AFX_CBRS_FLOAT |  AFX_CBRS_CLOSE | AFX_CBRS_RESIZE |  CBRS_AFX_AUTOHIDE);
```

### <a name="parameters"></a>Parámetros

*pWndCtrl*<br/>
[en] Puntero a un control que se va a agregar.

*lpszName*<br/>
[en] Especifica el nombre de la pestaña.

*bDesmontable*<br/>
[en] Si es TRUE, la página se creará como desmontable.

*nImageID*<br/>
[en] El índice de imagen en la lista de imágenes internas de la imagen que se mostrará en la nueva pestaña.

*dwControlBarStyle*<br/>
[en] Especifica el estilo AFX_ CBRS_* para los paneles de acoplamiento ajustados.

### <a name="remarks"></a>Observaciones

Utilice esta función para agregar un control como una nueva página de una barra de perspectiva.

Esta función llama internamente [a CMFCBaseTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab).

Si establece *bDetachable* en `AddControl` TRUE, `CDockablePaneAdapter` crea internamente un objeto y ajusta el control agregado. Establece automáticamente la clase en tiempo de ejecución `CMFCOutlookBar` de la ventana con fichas `CMultiPaneFrameWnd`en la clase en tiempo de ejecución y la clase en tiempo de ejecución del fotograma flotante en .

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `AddControl` muestra `CMFCOutlookBarTabCtrl` cómo utilizar el método en la clase. Este fragmento de código forma parte del [ejemplo de demostración](../../overview/visual-cpp-samples.md)de Outlook.

[!code-cpp[NVC_MFC_OutlookDemo#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_3.cpp)]

## <a name="cmfcoutlookbartabctrlcanshowfewerpagebuttons"></a><a name="canshowfewerpagebuttons"></a>CMFCOutlookBarTabCtrl::CanShowFewerPageButtons

Llamado por el marco de trabajo durante las operaciones de cambio de tamaño para determinar si se pueden mostrar menos botones de página de pestaña de barra de Outlook que están visibles actualmente.

```
virtual BOOL CanShowFewerPageButtons() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi hay más de un botón; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

El control de pestaña de barra de Outlook agrega o quita dinámicamente pestañas de la pantalla en función de la cantidad de espacio disponible. El marco de trabajo utiliza este método para ayudar en ese proceso.

## <a name="cmfcoutlookbartabctrlcanshowmorepagebuttons"></a><a name="canshowmorepagebuttons"></a>CMFCOutlookBarTabCtrl::CanShowMorePageButtons

Llamado por el marco de trabajo durante las operaciones de cambio de tamaño para determinar si se pueden mostrar más botones de página de la barra de Outlook que están visibles actualmente.

```
virtual BOOL CanShowMorePageButtons() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi hay botones que no están visibles actualmente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

El control de pestaña de barra de Outlook agrega o quita dinámicamente pestañas de la pantalla, dependiendo de la cantidad de espacio disponible. El marco de trabajo utiliza este método para ayudar en ese proceso.

## <a name="cmfcoutlookbartabctrlcreate"></a><a name="create"></a>CMFCOutlookBarTabCtrl::Crear

Crea el control de pestaña de la barra de Outlook.

```
virtual BOOL Create(
    const CRect& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
[en] Especifica el tamaño y la posición iniciales, en píxeles.

*pParentWnd*<br/>
[en] Apunta a la ventana padre. No debe ser NULL.

*nID*<br/>
[en] El identificador de control.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el control se ha creado correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Normalmente, los controles de pestaña de barra de outlook se crean cuando [CMFCOutlookBar clase](../../mfc/reference/cmfcoutlookbar-class.md) controla el WM_CREATE mensaje del proceso.

## <a name="cmfcoutlookbartabctrlenableanimation"></a><a name="enableanimation"></a>CMFCOutlookBarTabCtrl::EnableAnimation

Especifica si la animación que se produce durante el cambio entre fichas activas está habilitada.

```
static void EnableAnimation(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
[en] Especifica si la animación debe estar habilitada o deshabilitada.

### <a name="remarks"></a>Observaciones

Llame a esta función para habilitar y deshabilitar la animación. Cuando el usuario abre una página de pestañas, el título de la página se desliza hacia arriba o hacia abajo si la animación está habilitada. Si la animación está deshabilitada, la página se activa inmediatamente.

De forma predeterminada, la animación está habilitada.

## <a name="cmfcoutlookbartabctrlenableinplaceedit"></a><a name="enableinplaceedit"></a>CMFCOutlookBarTabCtrl::EnableInPlaceEdit

Especifica si un usuario puede modificar las etiquetas de texto en los botones de la página de pestañas de la barra de Outlook.

```
virtual void EnableInPlaceEdit(BOOL bEnable);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
Si es TRUE, habilite la edición in situ de la etiqueta de texto. Si FALSE, deshabilite la edición in situ.

### <a name="remarks"></a>Observaciones

Llame a esta función para habilitar o deshabilitar la edición in situ de etiquetas de texto en los botones de la página de pestañas. De forma predeterminada, la edición in situ está deshabilitada.

## <a name="cmfcoutlookbartabctrlenablescrollbuttons"></a><a name="enablescrollbuttons"></a>CMFCOutlookBarTabCtrl::EnableScrollButtons

Llamado por el marco de trabajo para habilitar los identificadores de desplazamiento que permiten al usuario desplazarse por los botones en el panel de la barra de Outlook.

```
void EnableScrollButtons(
    BOOL bEnable = TRUE,
    BOOL bIsUp = TRUE,
    BOOL bIsDown = TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
[en] Determina si se muestran los botones de desplazamiento.

*bIsUp*<br/>
[en] Determina si se muestra la barra de desplazamiento superior.

*bIsDown*<br/>
[en] Determina si se muestra la barra de desplazamiento inferior.

### <a name="remarks"></a>Observaciones

Habilita la visualización de los botones de desplazamiento. El marco de trabajo llama a este método cuando cambia la pestaña activa para restaurar los botones de desplazamiento.

## <a name="cmfcoutlookbartabctrlgetbordersize"></a><a name="getbordersize"></a>CMFCOutlookBarTabCtrl::GetBorderSize

Devuelve el tamaño de borde del control de ficha Outlook.

```
int GetBorderSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño del borde, en píxeles.

## <a name="cmfcoutlookbartabctrlgetvisiblepagebuttons"></a><a name="getvisiblepagebuttons"></a>CMFCOutlookBarTabCtrl::GetVisiblePageButtons

```
int GetVisiblePageButtons() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcoutlookbartabctrlisanimation"></a><a name="isanimation"></a>CMFCOutlookBarTabCtrl::IsAnimation

Especifica si la animación que se produce durante el cambio entre fichas activas está habilitada.

```
static BOOL IsAnimation();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la animación está habilitada; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Llame a la [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation) función para habilitar o deshabilitar la animación.

## <a name="cmfcoutlookbartabctrlismode2003"></a><a name="ismode2003"></a>CMFCOutlookBarTabCtrl::IsMode2003

Determina si el control de pestaña de la barra de Outlook está en un modo que emula Microsoft Outlook 2003.

```
BOOL IsMode2003() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el control de pestaña de la barra de Outlook está en modo de Outlook 2003; de lo contrario FALSE;

### <a name="remarks"></a>Observaciones

Este valor se establece mediante [CMFCOutlookBar::SetMode2003](../../mfc/reference/cmfcoutlookbar-class.md#setmode2003).

## <a name="cmfcoutlookbartabctrlonshowfewerpagebuttons"></a><a name="onshowfewerpagebuttons"></a>CMFCOutlookBarTabCtrl::OnShowFewerPageButtons

Llamado por el marco de trabajo para disminuir el número de botones de página de pestañas que están visibles.

```
virtual void OnShowFewerPageButtons();
```

### <a name="remarks"></a>Observaciones

Este método ajusta el número de botones de pestaña de página visibles cuando se cambia el tamaño del control.

## <a name="cmfcoutlookbartabctrlonshowmorepagebuttons"></a><a name="onshowmorepagebuttons"></a>CMFCOutlookBarTabCtrl::OnShowMorePageButtons

Llamado por el marco de trabajo para aumentar el número de botones de página de pestañas que están visibles.

```
virtual void OnShowMorePageButtons();
```

### <a name="remarks"></a>Observaciones

Este método ajustar el número de botones de página de pestaña que son visibles cuando se cambia el tamaño del control.

## <a name="cmfcoutlookbartabctrlonshowoptions"></a><a name="onshowoptions"></a>CMFCOutlookBarTabCtrl::OnShowOptions

Muestra el cuadro de diálogo **Opciones del panel de navegación.**

```
virtual void OnShowOptions();
```

### <a name="remarks"></a>Observaciones

El cuadro de diálogo Opciones del panel de **navegación** permite al usuario seleccionar qué botones de página de ficha se mostrarán y el orden en que se muestran.

El marco de trabajo llama a este método cuando el usuario selecciona el elemento de menú Opciones del panel de **navegación** en el menú de personalización del control.

## <a name="cmfcoutlookbartabctrlsetactivetab"></a><a name="setactivetab"></a>CMFCOutlookBarTabCtrl::SetActiveTab

Establece la pestaña activa. La pestaña activa es la que está abierta, con su contenido visible.

```
virtual BOOL SetActiveTab(int iTab);
```

### <a name="parameters"></a>Parámetros

*Itab*<br/>
[en] El índice de base cero de una pestaña que se va a abrir.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la pestaña especificada se ha abierto correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El efecto visual de establecer la pestaña activa depende de si ha habilitado la animación. Para obtener más información, vea [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation).

## <a name="cmfcoutlookbartabctrlsetbordersize"></a><a name="setbordersize"></a>CMFCOutlookBarTabCtrl::SetBorderSize

Establece el tamaño del borde del control de ficha Outlook.

```
void SetBorderSize(int nBorderSize);
```

### <a name="parameters"></a>Parámetros

*nBorderSize*<br/>
[en] Especifica el nuevo tamaño de borde en píxeles.

### <a name="remarks"></a>Observaciones

Establece el nuevo tamaño de borde y vuelve a calcular el diseño de la ventana de Outlook.

## <a name="cmfcoutlookbartabctrlsetpagebuttontextalign"></a><a name="setpagebuttontextalign"></a>CMFCOutlookBarTabCtrl::SetPageButtonTextAlign

Establece la alineación de las etiquetas de texto en los botones de tabulación de la barra de Outlook.

```
void SetPageButtonTextAlign(
    UINT uiAlign,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parámetros

*uiAlign*<br/>
[en] Especifica la alineación del texto.

*bRedraw*<br/>
[en] Si es TRUE, se volverá a dibujar la ventana de Outlook.

### <a name="remarks"></a>Observaciones

Utilice esta función para cambiar la alineación del texto de los botones de página.

*uiAlign* puede ser uno de los siguientes valores:

|Constante|Significado|
|--------------|-------------|
|TA_LEFT|Alineación izquierda|
|TA_CENTER|Alineación central|
|TA_RIGHT|Alineación derecha|

El valor predeterminado es TA_CENTER.

## <a name="cmfcoutlookbartabctrlsettoolbarimagelist"></a><a name="settoolbarimagelist"></a>CMFCOutlookBarTabCtrl::SetToolbarImageList

Establece el mapa de bits que contiene los iconos que se muestran en la parte inferior de la barra de Outlook en el modo de Outlook 2003.

```
BOOL SetToolbarImageList(
    UINT uiID,
    int cx,
    COLORREF clrTransp=RGB(255, 0, 255));
```

### <a name="parameters"></a>Parámetros

*uiID*<br/>
[en] Especifica el identificador de recurso de la imagen que se va a cargar.

*Cx*<br/>
[en] Especifica el ancho de una imagen en la lista de imágenes, en píxeles.

*clrTransp*<br/>
[en] Un valor RGB que especifica el color transparente.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se realiza correctamente; de lo contrario devuelve FALSE.

### <a name="remarks"></a>Observaciones

Utilice esta función para adjuntar una lista de imágenes cuyas imágenes se mostrarán en los botones de la barra de herramientas en el modo DeMicrosoft Office 2003. Los índices de imagen deben corresponder a los índices de página.

No se debe llamar a este método si no está en modo de Microsoft Office 2003. Para obtener más información, vea [CMFCOutlookBar (Clase)](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="cmfcoutlookbartabctrlsetvisiblepagebuttons"></a><a name="setvisiblepagebuttons"></a>CMFCOutlookBarTabCtrl::SetVisiblePageButtons

```
void SetVisiblePageButtons(int nVisiblePageButtons);
```

### <a name="parameters"></a>Parámetros

[en] *nVisiblePageButtons*<br/>

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md)<br/>
[CMFCOutlookBar Clase](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarPane Clase](../../mfc/reference/cmfcoutlookbarpane-class.md)
