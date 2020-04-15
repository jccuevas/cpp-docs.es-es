---
title: CTabbedPane (clase)
ms.date: 11/04/2016
f1_keywords:
- CTabbedPane
- AFXTABBEDPANE/CTabbedPane
- AFXTABBEDPANE/CTabbedPane::DetachPane
- AFXTABBEDPANE/CTabbedPane::EnableTabAutoColor
- AFXTABBEDPANE/CTabbedPane::FloatTab
- AFXTABBEDPANE/CTabbedPane::GetTabArea
- AFXTABBEDPANE/CTabbedPane::GetTabWnd
- AFXTABBEDPANE/CTabbedPane::HasAutoHideMode
- AFXTABBEDPANE/CTabbedPane::IsTabLocationBottom
- AFXTABBEDPANE/CTabbedPane::ResetTabs
- AFXTABBEDPANE/CTabbedPane::SetTabAutoColors
- AFXTABBEDPANE/CTabbedPane::m_bTabsAlwaysTop
- AFXTABBEDPANE/CTabbedPane::m_pTabWndRTC
helpviewer_keywords:
- CTabbedPane [MFC], DetachPane
- CTabbedPane [MFC], EnableTabAutoColor
- CTabbedPane [MFC], FloatTab
- CTabbedPane [MFC], GetTabArea
- CTabbedPane [MFC], GetTabWnd
- CTabbedPane [MFC], HasAutoHideMode
- CTabbedPane [MFC], IsTabLocationBottom
- CTabbedPane [MFC], ResetTabs
- CTabbedPane [MFC], SetTabAutoColors
- CTabbedPane [MFC], m_bTabsAlwaysTop
- CTabbedPane [MFC], m_pTabWndRTC
ms.assetid: f4dc5215-b789-4f2d-8c62-477aceda3578
ms.openlocfilehash: 17351eaed585ec34117a2ef825964fd51bd0d86b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365946"
---
# <a name="ctabbedpane-class"></a>CTabbedPane (clase)

Implementa la funcionalidad de un panel con pestañas separables.

o más detalles vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

## <a name="syntax"></a>Sintaxis

```
class CTabbedPane : public CBaseTabbedPane
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|`CTabbedPane::CTabbedPane`|Constructor predeterminado.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTabbedPane::DetachPane](#detachpane)|(Reemplaza [CBaseTabbedPane::DetachPane](../../mfc/reference/cbasetabbedpane-class.md#detachpane).)|
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|Habilita o deshabilita el coloreado automático de pestañas.|
|[CTabbedPane::FloatTab](#floattab)|Flota un panel, pero solo si el panel reside actualmente en una ficha desmontable.(Overrides [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|
|[CTabbedPane::GetTabArea](#gettabarea)|Devuelve el tamaño y la posición del área de pestañas de la ventana con pestañas.|
|[CTabbedPane::GetTabWnd](#gettabwnd)||
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|Determina si el panel con pestañas se puede cambiar a modo de ocultación automática. (Reemplaza [CBaseTabbedPane::HasAutoHideMode](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode).)|
|[CTabbedPane::IsTabLocationBottom](#istablocationbottom)|Determina si las pestañas se sitúan en la parte inferior de la ventana.|
|[CTabbedPane::ResetTabs](#resettabs)|Restablece todos los paneles con pestañas al estado predeterminado.|
|[CTabbedPane::SetTabAutoColors](#settabautocolors)|Establece una lista de colores personalizados que se pueden usar cuando se habilita la característica de color automático.|

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|[CTabbedPane::m_bTabsAlwaysTop](#m_btabsalwaystop)|La ubicación predeterminada de las pestañas en la aplicación.|
|[CTabbedPane::m_pTabWndRTC](#m_ptabwndrtc)|Información de clase en tiempo de ejecución para un derivado de `CMFCTabCtrl` personalizado.|

## <a name="remarks"></a>Observaciones

El marco de trabajo crea automáticamente una instancia de esta clase cuando un usuario adjunta un panel a otro apuntando al título del segundo panel. Todos los paneles con pestañas que se crean mediante el marco de trabajo tienen un identificador de -1.

Para especificar pestañas regulares en lugar de pestañas de estilo de Outlook, pase el estilo de AFX_CBRS_REGULAR_TABS al método [CDockablePane::CreateEx.](../../mfc/reference/cdockablepane-class.md#createex)

Si crea un panel con pestañas separables, el marco de trabajo puede destruir automáticamente el panel, por lo que no debe almacenar el puntero. Para obtener un puntero al panel con pestañas, llame al método `CBasePane::GetParentTabbedPane`.

## <a name="example"></a>Ejemplo

En este ejemplo, crearemos un objeto `CTabbedPane`. A continuación, usamos [CBaseTabbedPane::AddTab](../../mfc/reference/cbasetabbedpane-class.md#addtab) para adjuntar pestañas adicionales.

```cpp
CTabbedPane* pTabbededBar = new CTabbedPane (TRUE);

if (!pTabbededBar->Create (_T(""),
    this,
    CRect (0,
    0,
    200,
    200),
    TRUE,
    (UINT) -1,
    WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS |
    WS_CLIPCHILDREN | CBRS_LEFT |
    CBRS_FLOAT_MULTI))
{
    TRACE0("Failed to create Solution Explorer bar\n");

    return FALSE;      // fail to create
}

pTabbededBar->AddTab (&m_wndClassView);
pTabbededBar->AddTab (&m_wndResourceView);

pTabbededBar->AddTab (&m_wndFileView);
pTabbededBar->EnableDocking(CBRS_ALIGN_ANY);

DockPane(pTabbededBar);
```

## <a name="example"></a>Ejemplo

Otra forma de crear un objeto de barra de control con fichas es utilizar [CDockablePane::AttachToTabWnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd). El `AttachToTabWnd` método crea dinámicamente un objeto de panel con fichas mediante la información de clase en tiempo de ejecución establecida por [CDockablePane::SetTabbedPaneRTC](../../mfc/reference/cdockablepane-class.md#settabbedpanertc).

En este ejemplo se crea dinámicamente un panel con pestañas, se asocian dos pestañas y se convierte la segunda pestaña en no separable.

```cpp
DockPane(&m_wndClassView);

CTabbedPane* pTabbedBar = NULL;
m_wndResourceView.AttachToTabWnd (&m_wndClassView,
    DM_SHOW,
    TRUE,
    (CDockablePane**) &pTabbedBar);

m_wndFileView.AttachToTabWnd (pTabbedBar,
    DM_SHOW,
    TRUE,
    (CDockablePane**) &pTabbedBar);

pTabbedBar->GetUnderlyingWindow ()->EnableTabDetach (1,
    FALSE);
```

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CTabbedPane](../../mfc/reference/ctabbedpane-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxTabbedPane.h

## <a name="ctabbedpanedetachpane"></a><a name="detachpane"></a>CTabbedPane::DetachPane

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parámetros

[en] *pBar*<br/>

[en] *bOcultar*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="ctabbedpaneenabletabautocolor"></a><a name="enabletabautocolor"></a>CTabbedPane::EnableTabAutoColor

Habilita o deshabilita el coloreado automático de pestañas.

```
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
[en] TRUE para habilitar el color automático de las pestañas; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Utilice este método estático para habilitar o deshabilitar el color automático de las pestañas en todos los paneles con fichas de la aplicación. Cuando esta función está habilitada, cada pestaña se rellena con su propio color. Puede encontrar la lista de colores que se usan para colorear las fichas mediante una llamada a la [CMFCBaseTabCtrl::GetAutoColors](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors) método.

Puede especificar la lista de colores que se usarán para las fichas llamando a [CTabbedPane::SetTabAutoColors](#settabautocolors).

Esta opción está deshabilitada de forma predeterminada.

## <a name="ctabbedpanefloattab"></a><a name="floattab"></a>CTabbedPane::FloatTab

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parámetros

[en] *pBar*<br/>
[en] *nTabID*<br/>
[en] *dockMethod*<br/>
[en] *bOcultar*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="ctabbedpanegettabarea"></a><a name="gettabarea"></a>CTabbedPane::GetTabArea

Devuelve el tamaño y la posición del área de ficha en la ventana con fichas.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>Parámetros

*rectTabAreaTop*<br/>
[fuera] Contiene el tamaño y la posición, en coordenadas de pantalla, del área de la ficha superior.

*rectTabAreaBottom*<br/>
[fuera] Contiene el tamaño y la posición, en coordenadas de pantalla, del área de la ficha inferior.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método para determinar cómo acoplar un panel que un usuario está arrastrando. Cuando el usuario arrastra un panel sobre el área de ficha del panel de destino, el marco de trabajo intenta agregarlo como una nueva pestaña del panel de destino. De lo contrario, intenta acoplar el panel al lado del panel de destino, lo que implica la creación de un nuevo contenedor de paneles con un divisor de paneles que separa los dos paneles.

Invalide este `CTabbedPane`método en una clase derivada para cambiar este comportamiento.

## <a name="ctabbedpanegettabwnd"></a><a name="gettabwnd"></a>CTabbedPane::GetTabWnd

```
CMFCTabCtrl* GetTabWnd() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="ctabbedpanehasautohidemode"></a><a name="hasautohidemode"></a>CTabbedPane::HasAutoHideMode

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="ctabbedpaneistablocationbottom"></a><a name="istablocationbottom"></a>CTabbedPane::IstabLocationBottom

Determina si las pestañas se sitúan en la parte inferior de la ventana.

```
virtual BOOL IsTabLocationBottom() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el área de ficha se encuentra en la parte inferior de la ventana con pestañas; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

## <a name="ctabbedpanem_btabsalwaystop"></a><a name="m_btabsalwaystop"></a>CTabbedPane::m_bTabsAlwaysTop

La ubicación predeterminada de las pestañas en la aplicación.

```
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;
```

### <a name="remarks"></a>Observaciones

Establezca este miembro estático en TRUE para forzar que todas las fichas de la aplicación se muestren en la parte superior del panel con fichas.

Debe establecer este valor antes de crear un panel con fichas.

El valor predeterminado es FALSE.

## <a name="ctabbedpanem_ptabwndrtc"></a><a name="m_ptabwndrtc"></a>CTabbedPane::m_pTabWndRTC

Información de clase en tiempo de ejecución para un derivado de `CMFCTabCtrl` personalizado.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;
```

### <a name="remarks"></a>Observaciones

Establezca esta variable miembro estática en un puntero `CMFCTabCtrl`a la información de clase en tiempo de ejecución de un objeto derivado si utiliza una ventana con fichas personalizada dentro de un panel con fichas.

## <a name="ctabbedpaneresettabs"></a><a name="resettabs"></a>CTabbedPane::ResetTabs

Restablece todos los paneles con pestañas al estado predeterminado.

```
static void ResetTabs();
```

### <a name="remarks"></a>Observaciones

Llame a este método para revertir todos los paneles con pestañas a su estado predeterminado. Cuando se llama, este método restablece los tamaños de borde y el estado de color automático de todos los paneles con pestañas.

## <a name="ctabbedpanesettabautocolors"></a><a name="settabautocolors"></a>CTabbedPane::SetTabAutoColors

Establece una lista de colores personalizados que se utilizan cuando la función de color automático está habilitada.

```
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Parámetros

*arColors*<br/>
[en] Contiene la matriz de colores que se han de establecer.

### <a name="remarks"></a>Observaciones

Utilice este método para personalizar la lista de colores que se utilizan cuando la característica de color automático está habilitada. Se trata de una función estática y afecta a todos los paneles con pestañas de la aplicación.

Utilice [CTabbedPane::EnableTabAutoColor](#enabletabautocolor) para habilitar o deshabilitar la característica de color automático.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)<br/>
[CBaseTabbedPane (clase)](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBar Clase](../../mfc/reference/cmfcoutlookbar-class.md)
