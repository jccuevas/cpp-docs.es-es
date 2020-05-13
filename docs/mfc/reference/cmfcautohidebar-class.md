---
title: CMFCAutoHideBar (clase)
ms.date: 10/18/2018
f1_keywords:
- CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AddAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AllowShowOnPaneMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CalcFixedLayout
- AFXAUTOHIDEBAR/CMFCAutoHideBar::Create
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetFirstAHWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetVisibleCount
- AFXAUTOHIDEBAR/CMFCAutoHideBar::OnShowControlBarMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::RemoveAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetActiveInGroup
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetRecentVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::ShowAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::StretchPane
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UnSetAutoHideMode
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UpdateVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::m_nShowAHWndDelay
helpviewer_keywords:
- CMFCAutoHideBar [MFC], CMFCAutoHideBar
- CMFCAutoHideBar [MFC], AddAutoHideWindow
- CMFCAutoHideBar [MFC], AllowShowOnPaneMenu
- CMFCAutoHideBar [MFC], CalcFixedLayout
- CMFCAutoHideBar [MFC], Create
- CMFCAutoHideBar [MFC], GetFirstAHWindow
- CMFCAutoHideBar [MFC], GetVisibleCount
- CMFCAutoHideBar [MFC], OnShowControlBarMenu
- CMFCAutoHideBar [MFC], RemoveAutoHideWindow
- CMFCAutoHideBar [MFC], SetActiveInGroup
- CMFCAutoHideBar [MFC], SetRecentVisibleState
- CMFCAutoHideBar [MFC], ShowAutoHideWindow
- CMFCAutoHideBar [MFC], StretchPane
- CMFCAutoHideBar [MFC], UnSetAutoHideMode
- CMFCAutoHideBar [MFC], UpdateVisibleState
- CMFCAutoHideBar [MFC], m_nShowAHWndDelay
ms.assetid: 54c8d84f-de64-4efd-8a47-3ea0ade40a70
ms.openlocfilehash: 05f77dfba442f1ce4a375c8f225908799ece1788
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751761"
---
# <a name="cmfcautohidebar-class"></a>CMFCAutoHideBar (clase)

La clase `CMFCAutoHideBar` es una clase especial de la barra de herramientas que implementa la característica Ocultar automáticamente.

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

## <a name="syntax"></a>Sintaxis

```
class CMFCAutoHideBar : public CPane
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCAutoHideBar::CMFCAutoHideBar](#cmfcautohidebar)||

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCAutoHideBar::AddAutoHideWindow](#addautohidewindow)||
|[CMFCAutoHideBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Invalida `CPane::AllowShowOnPaneMenu`).|
|[CMFCAutoHideBar::CalcFixedLayout](#calcfixedlayout)|(Reemplaza [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCAutoHideBar::Create](#create)|Crea una barra de control y la adjunta al objeto [CPane.](../../mfc/reference/cpane-class.md) (Reemplaza [CPane::Crear](../../mfc/reference/cpane-class.md#create).)|
|[CMFCAutoHideBar::GetFirstAHWindow](#getfirstahwindow)||
|[CMFCAutoHideBar::GetVisibleCount](#getvisiblecount)||
|[CMFCAutoHideBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|Lo llama el marco de trabajo cuando está a punto de mostrarse un menú de panel especial. (Reemplaza [CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|
|[CMFCAutoHideBar::RemoveAutoHideWindow](#removeautohidewindow)||
|[CMFCAutoHideBar::SetActiveInGroup](#setactiveingroup)|(Reemplaza [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup).)|
|[CMFCAutoHideBar::SetRecentVisibleState](#setrecentvisiblestate)||
|[CMFCAutoHideBar::ShowAutoHideWindow](#showautohidewindow)||
|[CMFCAutoHideBar::StretchPane](#stretchpane)|Expande un panel vertical u horizontalmente. (Reemplaza [CBasePane::StretchPane](../../mfc/reference/cbasepane-class.md#stretchpane).)|
|[CMFCAutoHideBar::UnSetAutoHideMode](#unsetautohidemode)||
|[CMFCAutoHideBar::UpdateVisibleState](#updatevisiblestate)||

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCAutoHideBar::m_nShowAHWndDelay](#m_nshowahwnddelay)|El retardo de tiempo entre el momento en que el usuario coloca el cursor del mouse sobre una [clase CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) y el momento en que el marco de trabajo muestra la ventana asociada.|

## <a name="remarks"></a>Observaciones

Cuando el usuario cambia un panel de acoplamiento a modo de ocultación automática, el marco crea automáticamente un objeto `CMFCAutoHideBar`. También crea los objetos [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) y [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) necesarios. Cada objeto `CAutoHideDockSite` está asociado a un `CMFCAutoHideButton` individual.

La clase `CMFCAutoHideBar` implementa la presentación de un `CAutoHideDockSite` cuando el mouse de un usuario se mantiene sobre un `CMFCAutoHideButton`. Cuando la barra de herramientas recibe un mensaje WM_MOUSEMOVE, `CMFCAutoHideBar` inicia un temporizador. Cuando el temporizador finaliza, envía a la barra de herramientas una notificación de evento WM_TIMER. Para controlar este evento, la barra de herramientas comprueba si el puntero del mouse está situado sobre el mismo botón de ocultación automática que cuando se inició el temporizador. Si es así, se muestra el objeto `CAutoHideDockSite` adjunto.

Para controlar la duración del retraso del temporizador, defina `m_nShowAHWndDelay`. El valor predeterminado es de 400 ms.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto `CMFCAutoHideBar` y usar su método `GetDockSiteRow`.

[!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cmfcautohidebar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxautohidebar.h

## <a name="cmfcautohidebaraddautohidewindow"></a><a name="addautohidewindow"></a>CMFCAutoHideBar::AddAutoHideWindow

Agrega funcionalidad a una ventana `CDockablePane` que le permite ocultarse automáticamente.

```
CMFCAutoHideButton* AddAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Parámetros

*pAutoHideWnd*<br/>
[en] La ventana que quieres ocultar.

*dwAlignment*<br/>
[en] Valor que especifica la alineación del botón de ocultación automática con la ventana de la aplicación.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

El parámetro *dwAlignment* indica dónde reside el botón de ocultación automática en la aplicación. El parámetro puede establecerse en uno de los valores siguientes:

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

## <a name="cmfcautohidebarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFCAutoHideBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcautohidebarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCAutoHideBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parámetros

[en] *bStretch*<br/>

[en] *bHorz*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcautohidebarcmfcautohidebar"></a><a name="cmfcautohidebar"></a>CMFCAutoHideBar::CMFCAutoHideBar

Construye un objeto CMFCAutoHideBar.

```
CMFCAutoHideBar();
```

### <a name="remarks"></a>Observaciones

## <a name="cmfcautohidebarcreate"></a><a name="create"></a>CMFCAutoHideBar::Crear

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

*lpszClassName*<br/>

*dwStyle*<br/>

*Rect*<br/>

*pParentWnd*<br/>

*nID*<br/>

*dwControlBarStyle*<br/>

*pContext*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcautohidebargetfirstahwindow"></a><a name="getfirstahwindow"></a>CMFCAutoHideBar::GetFirstAHWindow

Devuelve un puntero a la primera ventana de ocultación automática de la aplicación.

```
CDockablePane* GetFirstAHWindow();
```

### <a name="return-value"></a>Valor devuelto

La primera ventana de ocultación automática de la aplicación o NULL si no existe ninguna.

### <a name="remarks"></a>Observaciones

## <a name="cmfcautohidebargetvisiblecount"></a><a name="getvisiblecount"></a>CMFCAutoHideBar::GetVisibleCount

Obtiene el número de botones de ocultación automática que se muestran.

```
int GetVisibleCount();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de botones de ocultación automática que se muestran.

### <a name="remarks"></a>Observaciones

## <a name="cmfcautohidebarm_nshowahwnddelay"></a><a name="m_nshowahwnddelay"></a>CMFCAutoHideBar::m_nShowAHWndDelay

El retardo de tiempo entre el momento en que el usuario coloca el cursor del mouse sobre una [clase CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) y el momento en que el marco de trabajo muestra la ventana asociada.

```
int CMFCAutoHideBar::m_nShowAHWndDelay = 400;
```

### <a name="remarks"></a>Observaciones

Cuando el usuario coloca el `CMFCAutoHideButton`cursor del mouse sobre un , hay un ligero retraso antes de que el marco de trabajo muestra la ventana asociada. Este parámetro determina la longitud de ese retraso en milisegundos.

## <a name="cmfcautohidebaronshowcontrolbarmenu"></a><a name="onshowcontrolbarmenu"></a>CMFCAutoHideBar::OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>Parámetros

[en] *CPoint*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcautohidebarremoveautohidewindow"></a><a name="removeautohidewindow"></a>CMFCAutoHideBar::RemoveAutoHideWindow

Elimina y destruye la ventana de ocultación automática.

```
    BOOL RemoveAutoHideWindow(CDockablePane* pAutoHideWnd);
```

### <a name="parameters"></a>Parámetros

CDockablePane* *pAutoHideWnd* La ventana de ocultación automática que se va a quitar.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cmfcautohidebarsetactiveingroup"></a><a name="setactiveingroup"></a>CMFCAutoHideBar::SetActiveInGroup

Marca una barra de ocultación automáticamente como activa.

```
virtual void SetActiveInGroup(BOOL bActive);
```

### <a name="parameters"></a>Parámetros

[en] BOOL *bActive* TRUE para establecer en active; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Vea [CPane::SetActiveInGroup](../../mfc/reference/cpane-class.md#setactiveingroup).

## <a name="cmfcautohidebarsetrecentvisiblestate"></a><a name="setrecentvisiblestate"></a>CMFCAutoHideBar::SetRecentVisibleState

```cpp
void SetRecentVisibleState(BOOL bState);
```

### <a name="parameters"></a>Parámetros

*bState*<br/>
[en] Estado a establecer.

### <a name="remarks"></a>Observaciones

## <a name="cmfcautohidebarshowautohidewindow"></a><a name="showautohidewindow"></a>CMFCAutoHideBar::ShowAutoHideWindow

Muestra la ventana de ocultación automática.

```
BOOL ShowAutoHideWindow(
    CDockablePane* pAutoHideWnd,
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>Parámetros

*pAutoHideWnd*<br/>
[en] Ventana para mostrar.

*bMostrar*<br/>
[en] TRUE para mostrar la ventana.

*bDelay*<br/>
[en] Este parámetro se omite.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cmfcautohidebarstretchpane"></a><a name="stretchpane"></a>CMFCAutoHideBar::StretchPane

Cambia el tamaño de la barra de ocultación automática en estado contraído para ajustarse al objeto `CMFCAutoHideButton` .

```
virtual CSize StretchPane(
    int nLength,
    BOOL bVert);
```

### <a name="parameters"></a>Parámetros

*nLongitud*<br/>
[en] El valor no se utiliza en la implementación base. En las implementaciones derivadas, use este valor para indicar la longitud del panel cuyo tamaño ha cambiado.

*bVert*<br/>
[en] El valor no se utiliza en la implementación base. En las implementaciones derivadas, use TRUE para controlar el caso en el que la barra de ocultación automática se contrae verticalmente y FALSE para el caso en el que la barra de ocultación automática se contrae horizontalmente.

### <a name="return-value"></a>Valor devuelto

El tamaño resultante del panel cuyo tamaño ha cambiado.

### <a name="remarks"></a>Observaciones

Las clases derivadas pueden reemplazar este método para personalizar el comportamiento.

## <a name="cmfcautohidebarunsetautohidemode"></a><a name="unsetautohidemode"></a>CMFCAutoHideBar::UnSetAutoHideMode

Deshabilita el modo de ocultación automática para un grupo de barras de ocultación automática.

```cpp
void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup)
```

### <a name="parameters"></a>Parámetros

[in] pFirstBarInGroup Un puntero a la primera barra de ocultación automática del grupo.

### <a name="remarks"></a>Observaciones

## <a name="cmfcautohidebarupdatevisiblestate"></a><a name="updatevisiblestate"></a>CMFCAutoHideBar::UpdateVisibleState

El marco de trabajo la llama cuando es necesario volver a dibujar la barra de ocultación automática.

```cpp
void UpdateVisibleState();
```

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)<br/>
[Clase CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)<br/>
[CMFCAutoHideButton (clase)](../../mfc/reference/cmfcautohidebutton-class.md)
