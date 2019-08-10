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
ms.openlocfilehash: ccd500547bdcf65e922f7b5e5ca8d30e0423933d
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866188"
---
# <a name="cmfcrebar-class"></a>Clase CMFCReBar

Un `CMFCReBar` objeto es una barra de control que proporciona información de diseño, persistencia y estado para los controles rebar.
Para obtener más información, consulte el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\MFC** de la instalación de Visual Studio.
## <a name="syntax"></a>Sintaxis

```
class CMFCReBar : public CPane
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCReBar::AddBar](#addbar)|Agrega una banda a un rebar.|
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|(Invalida [a cbasepane:: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)).|
|[CMFCReBar::CanFloat](#canfloat)|(Invalida [a cbasepane:: CanFloat](../../mfc/reference/cbasepane-class.md#canfloat)).|
|[CMFCReBar::Create](#create)|Crea el control rebar y lo adjunta al `CMFCReBar` objeto.|
|[CMFCReBar::EnableDocking](#enabledocking)|(Invalida [a cbasepane:: EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)).|
|[CMFCReBar::GetReBarBandInfoSize](#getrebarbandinfosize)||
|[CMFCReBar::GetReBarCtrl](#getrebarctrl)|Proporciona acceso directo al control común [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) subyacente.|
|[CMFCReBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|(Invalida [CPane:: OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu)).|
|[CMFCReBar::OnToolHitTest](#ontoolhittest)|(Invalida [CWnd:: OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest)).|
|[CMFCReBar::OnUpdateCmdUI](#onupdatecmdui)|(Invalida [a cbasepane:: OnUpdateCmdUI](cbasepane-class.md)).|
|[CMFCReBar::SetPaneAlignment](#setpanealignment)|(Invalida [a cbasepane:: SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment)).|

## <a name="remarks"></a>Comentarios

Un `CMFCReBar` objeto puede contener diversas ventanas secundarias. Esto incluye cuadros de edición, barras de herramientas y cuadros de lista. Puede cambiar el tamaño del rebar mediante programación o el usuario puede cambiar manualmente el tamaño del rebar arrastrando su barra de redimensionamiento. También puede establecer el fondo de un objeto rebar en un mapa de bits de su elección.

Un objeto rebar se comporta de forma similar a un objeto Toolbar. Un control rebar puede contener una o más bandas y cada banda puede contener una barra de agarre, un mapa de bits, una etiqueta de texto y una ventana secundaria.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCReBar` . En el ejemplo se muestra cómo crear un control rebar y cómo agregarle una banda. La banda funciona como una barra de herramientas interna. Este fragmento de código forma parte del [ejemplo de prueba rebar](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[A cbasepane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CPane](../../mfc/reference/cpane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CMFCReBar](../../mfc/reference/cmfcrebar-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxRebar. h

##  <a name="addbar"></a>  CMFCReBar::AddBar

Agrega una banda a un rebar.

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
[in, out] Puntero a la ventana secundaria que se va a insertar en el rebar. El objeto al que se hace referencia debe tener el estilo de ventana **WS_CHILD** .

*pszText*<br/>
de Especifica el texto que se va a mostrar en el rebar. El texto no forma parte de la ventana secundaria. En su lugar, se muestra en el propio rebar.

*pbmp*<br/>
[in, out] Especifica el mapa de bits que se va a mostrar en el fondo de rebar.

*dwStyle*<br/>
de Contiene el estilo que se va a aplicar a la banda. Para obtener una lista completa de los estilos de banda, vea `fStyle` la descripción de en la estructura [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) en la documentación de Windows SDK.

*clrFore*<br/>
de Representa el color de primer plano del rebar.

*clrBack*<br/>
de Representa el color de fondo del rebar.

### <a name="return-value"></a>Valor devuelto

TRUE si la banda se agregó correctamente al rebar; en caso contrario, FALSE.

##  <a name="create"></a>  CMFCReBar::Create

Crea el control rebar y lo adjunta al objeto [CMFCReBar](../../mfc/reference/cmfcrebar-class.md) .

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
[in, out] Puntero a la ventana primaria de este control rebar.

*dwCtrlStyle*<br/>
de Especifica el estilo del control rebar. El valor de estilo predeterminado es **RBS_BANDBORDERS**, que muestra líneas estrechas para separar las bandas adyacentes en el control rebar. Para obtener una lista de estilos válidos, vea los [estilos de control rebar](/windows/desktop/Controls/rebar-control-styles) en la documentación de Windows SDK.

*dwStyle*<br/>
de Estilo de ventana del control rebar. Para obtener una lista de estilos válidos, vea [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*nID*<br/>
de IDENTIFICADOR de la ventana secundaria del rebar.

### <a name="return-value"></a>Valor devuelto

TRUE si el rebar se creó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="getrebarctrl"></a>  CMFCReBar::GetReBarCtrl

Proporciona acceso directo al `CReBarCtrl` control común subyacente para `CMFCReBar` los objetos.

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

Referencia al objeto subyacente `CReBarCtrl` .

### <a name="remarks"></a>Comentarios

Llame a este método para aprovechar las ventajas de la funcionalidad de control común de rebar de Windows al personalizar el rebar.

##  <a name="calcfixedlayout"></a>  CMFCReBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parámetros

de *bStretch*<br/>
de *bHorz*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="canfloat"></a>  CMFCReBar::CanFloat

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="enabledocking"></a>  CMFCReBar::EnableDocking

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parámetros

de *dwDockStyle*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="getrebarbandinfosize"></a>  CMFCReBar::GetReBarBandInfoSize

```
UINT GetReBarBandInfoSize() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="onshowcontrolbarmenu"></a>  CMFCReBar::OnShowControlBarMenu

```
virtual BOOL OnShowControlBarMenu(CPoint);
```

### <a name="parameters"></a>Parámetros

de *CPoint*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="ontoolhittest"></a>  CMFCReBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>Parámetros

de *punto* de<br/>
de *pTI*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="onupdatecmdui"></a>  CMFCReBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parámetros

de *pTarget*<br/>
de *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="setpanealignment"></a>  CMFCReBar::SetPaneAlignment

```
virtual void SetPaneAlignment(DWORD dwAlignment);
```

### <a name="parameters"></a>Parámetros

de *dwAlignment*<br/>

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CReBarCtrl (clase)](../../mfc/reference/crebarctrl-class.md)<br/>
[CPane (clase)](../../mfc/reference/cpane-class.md)
