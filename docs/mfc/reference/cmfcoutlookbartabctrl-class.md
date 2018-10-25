---
title: Clase CMFCOutlookBarTabCtrl | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19550315f17982e019d1ba6f495dedee6d2f346d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081019"
---
# <a name="cmfcoutlookbartabctrl-class"></a>CMFCOutlookBarTabCtrl Class

Un control de pestaña que tiene el aspecto visual del **Panel de navegación** de Microsoft Outlook.
Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.
## <a name="syntax"></a>Sintaxis

```
class CMFCOutlookBarTabCtrl : public CMFCBaseTabCtrl
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|`CMFCOutlookBarTabCtrl::CMFCOutlookBarTabCtrl`|Constructor predeterminado.|
|`CMFCOutlookBarTabCtrl::~CMFCOutlookBarTabCtrl`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCOutlookBarTabCtrl::AddControl](#addcontrol)|Agrega un control de Windows como una nueva pestaña en la barra de Outlook.|
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|Lo llama el marco de trabajo determinar las dimensiones del cuadro de edición que aparece cuando un usuario cambia el nombre de una pestaña. (Invalida `CMFCBaseTabCtrl::CalcRectEdit`).|
|[CMFCOutlookBarTabCtrl::CanShowFewerPageButtons](#canshowfewerpagebuttons)|Lo llama el marco de trabajo durante las operaciones de cambio de tamaño para determinar si se pueden mostrar menos botones de página de ficha de barra de Outlook que están actualmente visibles.|
|[CMFCOutlookBarTabCtrl::CanShowMorePageButtons](#canshowmorepagebuttons)|Lo llama el marco de trabajo durante las operaciones de cambio de tamaño para determinar si se pueden mostrar más botones de página de ficha de barra de Outlook que están actualmente visibles.|
|[CMFCOutlookBarTabCtrl::Create](#create)|Crea el control de ficha de la barra de Outlook.|
|`CMFCOutlookBarTabCtrl::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|
|[CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)|Especifica si está habilitada la animación que se produce durante la conmutación entre las pestañas activas.|
|[CMFCOutlookBarTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|Especifica si un usuario puede modificar las etiquetas de texto en los botones de ficha de la barra de Outlook. (Invalida [CMFCBaseTabCtrl::EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit).)|
|[CMFCOutlookBarTabCtrl::EnableScrollButtons](#enablescrollbuttons)|Lo llama el marco de trabajo para habilitar los botones que permiten al usuario desplazarse por los botones en el panel de la barra de Outlook.|
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|Identifica el panel que contiene un punto especificado. (Invalida [CMFCBaseTabCtrl::FindTargetWnd](../../mfc/reference/cmfcbasetabctrl-class.md#findtargetwnd).)|
|[CMFCOutlookBarTabCtrl::GetBorderSize](#getbordersize)|Devuelve el tamaño del borde del control de ficha de Outlook.|
|`CMFCOutlookBarTabCtrl::GetTabArea`|Recupera el tamaño y posición del área de pestaña de control de ficha. (Invalida [CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea).)|
|`CMFCOutlookBarTabCtrl::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|
|[CMFCOutlookBarTabCtrl::GetVisiblePageButtons](#getvisiblepagebuttons)||
|[CMFCOutlookBarTabCtrl::IsAnimation](#isanimation)|Determina si está habilitada la animación que se produce durante la conmutación entre las pestañas activas.|
|[CMFCOutlookBarTabCtrl::IsMode2003](#ismode2003)|Determina si el control de ficha de la barra de Outlook está en un modo que emule Microsoft Outlook 2003.|
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|Determina si un punto está dentro del área de pestaña. (Invalida [CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea).)|
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|Determina si una pestaña es desmontable. (Invalida [CMFCBaseTabCtrl::IsTabDetachable](../../mfc/reference/cmfcbasetabctrl-class.md#istabdetachable).)|
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|Lo llama el marco de trabajo cuando se inserta o se quita una pestaña. (Invalida `CMFCBaseTabCtrl::OnChangeTabs`).|
|[CMFCOutlookBarTabCtrl::OnShowFewerPageButtons](#onshowfewerpagebuttons)|Lo llama el marco de trabajo para disminuir el número de botones de la página de ficha que están visibles.|
|[CMFCOutlookBarTabCtrl::OnShowMorePageButtons](#onshowmorepagebuttons)|Lo llama el marco para aumentar el número de botones de la página de ficha que están visibles.|
|[CMFCOutlookBarTabCtrl::OnShowOptions](#onshowoptions)|Muestra el **opciones del panel de navegación** cuadro de diálogo.|
|`CMFCOutlookBarTabCtrl::RecalcLayout`|Vuelve a calcular el diseño interno del control de ficha. (Invalida [CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout).)|
|[CMFCOutlookBarTabCtrl::SetActiveTab](#setactivetab)|Establece la pestaña activa. (Invalida [CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab).)|
|[CMFCOutlookBarTabCtrl::SetBorderSize](#setbordersize)|Establece el tamaño del borde del control de ficha de Outlook.|
|[CMFCOutlookBarTabCtrl::SetPageButtonTextAlign](#setpagebuttontextalign)|Establece la alineación de las etiquetas de texto en los botones de ficha de la barra de Outlook.|
|[CMFCOutlookBarTabCtrl::SetToolbarImageList](#settoolbarimagelist)|Establece el mapa de bits que contiene los iconos que se muestran en la parte inferior de la barra de Outlook en modo de Outlook 2003 (consulte [CMFCOutlookBar (clase)](../../mfc/reference/cmfcoutlookbar-class.md)).|
|[CMFCOutlookBarTabCtrl::SetVisiblePageButtons](#setvisiblepagebuttons)||

## <a name="remarks"></a>Comentarios

Para crear una barra de Outlook que es compatible con acoplamiento, use un `CMFCOutlookBar` objeto para hospedar el control de ficha de la barra de Outlook. Para obtener más información, consulte [CMFCOutlookBar (clase)](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo inicializar un `CMFCOutlookBarTabCtrl` de objetos y usar varios métodos en la `CMFCOutlookBarTabCtrl` clase. El ejemplo muestra cómo habilitar la edición en contexto de la etiqueta de texto en los botones de la página de ficha de la barra de Outlook, habilitar la animación, habilite los identificadores de desplazamiento que permiten al usuario desplazarse por los botones en el panel de la barra de Outlook, establezca el tamaño del borde de la continuación de la pestaña de Outlook rol y establece la alineación de las etiquetas de texto en los botones de ficha de la barra de Outlook. Este fragmento de código forma parte de la [ejemplo de demostración de Outlook](../../visual-cpp-samples.md).

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

##  <a name="addcontrol"></a>  CMFCOutlookBarTabCtrl::AddControl

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
[in] Un puntero a un control para agregar.

*lpszName*<br/>
[in] Especifica el nombre de pestaña.

*bDetachable*<br/>
[in] Si es TRUE, se creará la página como desmontable.

*nImageID*<br/>
[in] Índice de imagen en la lista de imágenes interna para la imagen que se mostrará en la nueva pestaña.

*dwControlBarStyle*<br/>
[in] Especifica el estilo AFX va CBRS_ * para los paneles de acoplamiento ajustados.

### <a name="remarks"></a>Comentarios

Utilice esta función para agregar un control como una página nueva de una barra de outlook.

Esta función llama internamente en [cmfcbasetabctrl:: addTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab).

Si establece *bDetachable* en TRUE, `AddControl` crea internamente un `CDockablePaneAdapter` de objetos y ajusta el control agregado. Establece automáticamente a la clase en tiempo de ejecución de la clase en tiempo de ejecución de la ventana con pestañas `CMFCOutlookBar` y la clase en tiempo de ejecución del marco flotante para `CMultiPaneFrameWnd`.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar el `AddControl` método en el `CMFCOutlookBarTabCtrl` clase. Este fragmento de código forma parte de la [ejemplo de demostración de Outlook](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookDemo#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_3.cpp)]

##  <a name="canshowfewerpagebuttons"></a>  CMFCOutlookBarTabCtrl::CanShowFewerPageButtons

Lo llama el marco de trabajo durante el cambio de tamaño de las operaciones para determinar si se pueden mostrar menos botones de página de ficha de barra de Outlook que están actualmente visibles.

```
virtual BOOL CanShowFewerPageButtons() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si hay más de un botón; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

El control de ficha de la barra de Outlook dinámicamente agrega o quita las pestañas de la pantalla dependiendo de cuánto espacio está disponible. Este método se usa el marco de trabajo para ayudar en ese proceso.

##  <a name="canshowmorepagebuttons"></a>  CMFCOutlookBarTabCtrl::CanShowMorePageButtons

Lo llama el marco de trabajo durante el cambio de tamaño de las operaciones para determinar si se pueden mostrar más botones de página de ficha de barra de Outlook que están actualmente visibles.

```
virtual BOOL CanShowMorePageButtons() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si hay botones que no están visibles; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

El control de ficha de la barra de Outlook dinámicamente agrega o quita las pestañas de la pantalla, dependiendo de cuánto espacio está disponible. Este método se usa el marco de trabajo para ayudar en ese proceso.

##  <a name="create"></a>  CMFCOutlookBarTabCtrl::Create

Crea el control de ficha de la barra de Outlook.

```
virtual BOOL Create(
    const CRect& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
[in] Especifica el tamaño inicial y la posición, en píxeles.

*pParentWnd*<br/>
[in] Apunta a la ventana primaria. No debe ser NULL.

*nID*<br/>
[in] El identificador de control.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el control se ha creado correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Normalmente, se crean los controles de ficha de barra de outlook cuando [CMFCOutlookBar (clase)](../../mfc/reference/cmfcoutlookbar-class.md) controla el mensaje WM_CREATE del proceso.

##  <a name="enableanimation"></a>  CMFCOutlookBarTabCtrl::EnableAnimation

Especifica si está habilitada la animación que se produce durante la conmutación entre las pestañas activas.

```
static void EnableAnimation(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar el*<br/>
[in] Especifica si la animación debe habilitarse o deshabilitarse.

### <a name="remarks"></a>Comentarios

Llame a esta función para habilitar y deshabilitar la animación. Cuando el usuario abre una página de ficha, el título de la página se desliza hacia arriba o hacia abajo si está habilitada la animación. Si se deshabilita la animación, la página está activada inmediatamente.

El valor predeterminado, la animación está habilitada.

##  <a name="enableinplaceedit"></a>  CMFCOutlookBarTabCtrl::EnableInPlaceEdit

Especifica si un usuario puede modificar las etiquetas de texto en los botones de la página de ficha de la barra de Outlook.

```
virtual void EnableInPlaceEdit(BOOL bEnable);
```

### <a name="parameters"></a>Parámetros

*bHabilitar el*<br/>
Si es TRUE, habilite la edición en contexto de la etiqueta de texto. Si es FALSE, deshabilite la edición en contexto.

### <a name="remarks"></a>Comentarios

Llame a esta función para habilitar o deshabilitar la edición en contexto de las etiquetas de texto en los botones de la página de ficha. De forma predeterminada la edición en contexto está deshabilitada.

##  <a name="enablescrollbuttons"></a>  CMFCOutlookBarTabCtrl::EnableScrollButtons

Lo llama el marco de trabajo para habilitar los identificadores de desplazamiento que permiten al usuario desplazarse por los botones en el panel de la barra de Outlook.

```
void EnableScrollButtons(
    BOOL bEnable = TRUE,
    BOOL bIsUp = TRUE,
    BOOL bIsDown = TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar el*<br/>
[in] Determina si se muestran los botones de desplazamiento.

*bIsUp*<br/>
[in] Determina si se muestra la barra de desplazamiento superior.

*bIsDown*<br/>
[in] Determina si se muestra la barra de desplazamiento de la parte inferior.

### <a name="remarks"></a>Comentarios

Permite la visualización de los botones de desplazamiento. El marco de trabajo llama a este método cuando cambia la pestaña activa para restaurar los botones de desplazamiento.

##  <a name="getbordersize"></a>  CMFCOutlookBarTabCtrl::GetBorderSize

Devuelve el tamaño del borde del control de ficha de Outlook.

```
int GetBorderSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño del borde, en píxeles.

##  <a name="getvisiblepagebuttons"></a>  CMFCOutlookBarTabCtrl::GetVisiblePageButtons

```
int GetVisiblePageButtons() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="isanimation"></a>  CMFCOutlookBarTabCtrl::IsAnimation

Especifica si está habilitada la animación que se produce durante la conmutación entre las pestañas activas.

```
static BOOL IsAnimation();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la animación está habilitada; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Llame a la [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation) función para habilitar o deshabilitar la animación.

##  <a name="ismode2003"></a>  CMFCOutlookBarTabCtrl::IsMode2003

Determina si el control de ficha de la barra de Outlook está en un modo que emule Microsoft Outlook 2003.

```
BOOL IsMode2003() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el control de ficha de la barra de Outlook está en modo de Outlook 2003; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este valor se establece [CMFCOutlookBar::SetMode2003](../../mfc/reference/cmfcoutlookbar-class.md#setmode2003).

##  <a name="onshowfewerpagebuttons"></a>  CMFCOutlookBarTabCtrl::OnShowFewerPageButtons

Lo llama el marco de trabajo para disminuir el número de botones de la página de ficha que están visibles.

```
virtual void OnShowFewerPageButtons();
```

### <a name="remarks"></a>Comentarios

Este método ajusta el número de botones de ficha de página visible cuando el control cambia de tamaño.

##  <a name="onshowmorepagebuttons"></a>  CMFCOutlookBarTabCtrl::OnShowMorePageButtons

Lo llama el marco para aumentar el número de botones de la página de ficha que están visibles.

```
virtual void OnShowMorePageButtons();
```

### <a name="remarks"></a>Comentarios

Este método ajusta el número de botones de la página de ficha que están visibles cuando el control cambia de tamaño.

##  <a name="onshowoptions"></a>  CMFCOutlookBarTabCtrl::OnShowOptions

Muestra el **opciones del panel de navegación** cuadro de diálogo.

```
virtual void OnShowOptions();
```

### <a name="remarks"></a>Comentarios

El **opciones del panel de navegación** cuadro de diálogo permite al usuario seleccionar qué son los botones de página de ficha que se mostrará y el orden en el que se muestran.

Este método se llama el marco de trabajo cuando el usuario selecciona el **opciones del panel de navegación** plato de menú de personalización del control.

##  <a name="setactivetab"></a>  CMFCOutlookBarTabCtrl::SetActiveTab

Establece la pestaña activa. La pestaña activa es aquella que está abierto, con su contenido visible.

```
virtual BOOL SetActiveTab(int iTab);
```

### <a name="parameters"></a>Parámetros

*iTab*<br/>
[in] Índice de base cero de una pestaña a abrirse.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la ficha especificada se ha abierto correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

El efecto visual de la configuración de la pestaña activa depende de si ha habilitado la animación. Para obtener más información, consulte [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation).

##  <a name="setbordersize"></a>  CMFCOutlookBarTabCtrl::SetBorderSize

Establece el tamaño del borde del control de ficha de Outlook.

```
void SetBorderSize(int nBorderSize);
```

### <a name="parameters"></a>Parámetros

*nBorderSize*<br/>
[in] Especifica el nuevo tamaño del borde en píxeles.

### <a name="remarks"></a>Comentarios

Establece el tamaño del borde nuevo y vuelve a calcular el diseño de ventana de outlook.

##  <a name="setpagebuttontextalign"></a>  CMFCOutlookBarTabCtrl::SetPageButtonTextAlign

Establece la alineación de las etiquetas de texto en los botones de ficha de la barra de Outlook.

```
void SetPageButtonTextAlign(
    UINT uiAlign,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parámetros

*uiAlign*<br/>
[in] Especifica la alineación del texto.

*bRedraw*<br/>
[in] Si es TRUE, se volverá a dibujar la ventana de outlook.

### <a name="remarks"></a>Comentarios

Utilice esta función para cambiar la alineación del texto de los botones de página.

*uiAlign* puede ser uno de los siguientes valores:

|Constante|Significado|
|--------------|-------------|
|TA_LEFT|Alineación a la izquierda|
|TA_CENTER|Alineación central|
|TA_RIGHT|Alineación a la derecha|

El valor predeterminado es TA_CENTER.

##  <a name="settoolbarimagelist"></a>  CMFCOutlookBarTabCtrl::SetToolbarImageList

Establece el mapa de bits que contiene los iconos que se muestran en la parte inferior de la barra de Outlook en modo de Outlook 2003.

```
BOOL SetToolbarImageList(
    UINT uiID,
    int cx,
    COLORREF clrTransp=RGB(255, 0, 255));
```

### <a name="parameters"></a>Parámetros

*uiID*<br/>
[in] Especifica el identificador de recurso de la imagen para cargar.

*CX*<br/>
[in] Especifica el ancho de una imagen en la lista de imágenes, en píxeles.

*clrTransp*<br/>
[in] Un valor RGB que especifica el color transparente.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se realiza correctamente; en caso contrario, devuelve FALSE.

### <a name="remarks"></a>Comentarios

Use esta función para asociar una lista de imágenes cuyos imágenes se muestran en los botones de barra de herramientas en el modo de Microsoft Office 2003. Los índices de la imagen deben corresponder a los índices de la página.

No debe llamar a este método si no se encuentra en modo de Microsoft Office 2003. Para obtener más información, consulte [CMFCOutlookBar (clase)](../../mfc/reference/cmfcoutlookbar-class.md).

##  <a name="setvisiblepagebuttons"></a>  CMFCOutlookBarTabCtrl::SetVisiblePageButtons

```
void SetVisiblePageButtons(int nVisiblePageButtons);
```

### <a name="parameters"></a>Parámetros

[in] *nVisiblePageButtons*<br/>

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCBaseTabCtrl (clase)](../../mfc/reference/cmfcbasetabctrl-class.md)<br/>
[CMFCOutlookBar (clase)](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarPane (clase)](../../mfc/reference/cmfcoutlookbarpane-class.md)
