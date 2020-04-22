---
title: Clase CMFCReBar
ms.date: 11/04/2016
f1_keywords:
- CMFCReBar
- AFXREBAR/CMFCReBar
- AFXREBAR/CMFCReBar::AddBar
- AFXREBAR/CMFCReBar::CalcFixedLayout
- AFXREBAR/CMFCReBar::CanFloat
- AFXREBAR/CMFCReBar::Create
- AFXREBAR/CMFCReBar::EnableDocking
- AFXREBAR/CMFCReBar::GetReBarBandInfoSize
- AFXREBAR/CMFCReBar::GetReBarCtrl
- AFXREBAR/CMFCReBar::OnShowControlBarMenu
- AFXREBAR/CMFCReBar::OnToolHitTest
- AFXREBAR/CMFCReBar::OnUpdateCmdUI
- AFXREBAR/CMFCReBar::SetPaneAlignment
helpviewer_keywords:
- CMFCReBar [MFC], AddBar
- CMFCReBar [MFC], CalcFixedLayout
- CMFCReBar [MFC], CanFloat
- CMFCReBar [MFC], Create
- CMFCReBar [MFC], EnableDocking
- CMFCReBar [MFC], GetReBarBandInfoSize
- CMFCReBar [MFC], GetReBarCtrl
- CMFCReBar [MFC], OnShowControlBarMenu
- CMFCReBar [MFC], OnToolHitTest
- CMFCReBar [MFC], OnUpdateCmdUI
- CMFCReBar [MFC], SetPaneAlignment
ms.assetid: 02a60e29-6224-49c1-9e74-e0a7d9f8d023
ms.openlocfilehash: 409c97aba64c97ecf0443d14a70848cc298a44ba
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750002"
---
# <a name="cmfcrebar-class"></a>Clase CMFCReBar

Un `CMFCReBar` objeto es una barra de control que proporciona información de diseño, persistencia y estado para los controles de armadura.
Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

## <a name="syntax"></a>Sintaxis

```
class CMFCReBar : public CPane
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCReBar::AddBar](#addbar)|Agrega una banda a una armadura.|
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|(Reemplaza [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCReBar::CanFloat](#canfloat)|(Reemplaza [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|
|[CMFCReBar::Crear](#create)|Crea el control de armadura y `CMFCReBar` lo adjunta al objeto.|
|[CMFCReBar::EnableDocking](#enabledocking)|(Reemplaza [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).)|
|[CMFCReBar::GetReBarBandInfoSize](#getrebarbandinfosize)||
|[CMFCReBar::GetReBarCtrl](#getrebarctrl)|Proporciona acceso directo al control común [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) subyacente.|
|[CMFCReBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|(Reemplaza [CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|
|[CMFCReBar::OnToolHitTest](#ontoolhittest)|(Reemplaza [CWnd::OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest).)|
|[CMFCReBar::OnUpdateCmdUI](#onupdatecmdui)|(Reemplaza [CBasePane::OnUpdateCmdUI](cbasepane-class.md).)|
|[CMFCReBar::SetPaneAlignment](#setpanealignment)|(Reemplaza [CBasePane::SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment).)|

## <a name="remarks"></a>Observaciones

Un `CMFCReBar` objeto puede contener una variedad de ventanas secundarias. Esto incluye cuadros de edición, barras de herramientas y cuadros de lista. Puede cambiar el tamaño de la armadura mediante programación o el usuario puede cambiar manualmente el tamaño de la armadura arrastrando su barra de pinzamiento. También puede establecer el fondo de un objeto de armadura en un mapa de bits de su elección.

Un objeto de armadura se comporta de forma similar a un objeto de barra de herramientas. Un control de armadura puede contener una o más bandas y cada banda puede contener una barra de pinzamiento, un mapa de bits, una etiqueta de texto y una ventana secundaria.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCReBar` . En el ejemplo se muestra cómo crear un control de armadura y agregarle una banda. La banda funciona como una barra de herramientas interna. Este fragmento de código forma parte del ejemplo Prueba de [armadura.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[Cobject](../../mfc/reference/cobject-class.md)\
.&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CBasepane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CMFCReBar](../../mfc/reference/cmfcrebar-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxRebar.h

## <a name="cmfcrebaraddbar"></a><a name="addbar"></a>CMFCReBar::AddBar

Agrega una banda a una armadura.

```
BOOL AddBar(
    CWnd* pBar,
    LPCTSTR pszText = NULL,
    CBitmap* pbmp = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

BOOL AddBar(
    CWnd* pBar,
    COLORREF clrFore,
    COLORREF clrBack,
    LPCTSTR pszText = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
[adentro, fuera] Puntero a la ventana secundaria que se va a insertar en la armadura. El objeto al que se hace referencia debe tener el estilo de ventana **WS_CHILD.**

*pszText*<br/>
[en] Especifica el texto que aparecerá en la armadura. El texto no forma parte de la ventana secundaria. Más bien, se muestra en la propia armadura.

*pbmp*<br/>
[adentro, fuera] Especifica el mapa de bits que se mostrará en el fondo de armadura.

*dwStyle*<br/>
[en] Contiene el estilo que se aplicará a la banda. Para obtener una lista completa de `fStyle` estilos de banda, consulte la descripción de la estructura [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) en la documentación de Windows SDK.

*clrFore*<br/>
[en] Representa el color de primer plano de la armadura.

*clrBack*<br/>
[en] Representa el color de fondo de la armadura.

### <a name="return-value"></a>Valor devuelto

TRUESi la banda se agregó correctamente a la armadura; de lo contrario, FALSE.

## <a name="cmfcrebarcreate"></a><a name="create"></a>CMFCReBar::Crear

Crea el control de armadura y lo adjunta a la [CMFCReBar](../../mfc/reference/cmfcrebar-class.md) objeto.

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
[adentro, fuera] Un puntero a la ventana primaria de este control de armadura.

*dwCtrlStyle*<br/>
[en] Especifica el estilo del control de armadura. El valor de estilo predeterminado es **RBS_BANDBORDERS**, que muestra líneas estrechas para separar las bandas adyacentes en el control de armadura. Para obtener una lista de estilos válidos, consulte [Estilos](/windows/win32/Controls/rebar-control-styles) de control de armadura en la documentación de Windows SDK.

*dwStyle*<br/>
[en] El estilo de ventana del control de armadura. Para obtener una lista de estilos válidos, vea [Estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles)de ventana .

*nID*<br/>
[en] Identificación de la ventana secundaria de la armadura.

### <a name="return-value"></a>Valor devuelto

TRUESi la armadura se creó correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cmfcrebargetrebarctrl"></a><a name="getrebarctrl"></a>CMFCReBar::GetReBarCtrl

Proporciona acceso `CReBarCtrl` directo al control `CMFCReBar` común subyacente para los objetos.

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

Una referencia al `CReBarCtrl` objeto subyacente.

### <a name="remarks"></a>Observaciones

Llame a este método para aprovechar la funcionalidad de control común de armadura de Windows al personalizar la armadura.

## <a name="cmfcrebarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCReBar::CalcFixedLayout

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

## <a name="cmfcrebarcanfloat"></a><a name="canfloat"></a>CMFCReBar::CanFloat

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcrebarenabledocking"></a><a name="enabledocking"></a>CMFCReBar::EnableDocking

```cpp
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parámetros

[en] *dwDockStyle*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcrebargetrebarbandinfosize"></a><a name="getrebarbandinfosize"></a>CMFCReBar::GetReBarBandInfoSize

```
UINT GetReBarBandInfoSize() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcrebaronshowcontrolbarmenu"></a><a name="onshowcontrolbarmenu"></a>CMFCReBar::OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>Parámetros

[en] *CPoint*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcrebarontoolhittest"></a><a name="ontoolhittest"></a>CMFCReBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>Parámetros

[en] *punto*<br/>
[en] *pTI*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcrebaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCReBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parámetros

[en] *pTarget*<br/>
[en] *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcrebarsetpanealignment"></a><a name="setpanealignment"></a>CMFCReBar::SetPaneAlignment

```
virtual void SetPaneAlignment(DWORD dwAlignment);
```

### <a name="parameters"></a>Parámetros

[en] *dwAlignment*<br/>

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Clase CReBarCtrl](../../mfc/reference/crebarctrl-class.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)
