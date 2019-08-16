---
title: CReBar (clase)
ms.date: 11/19/2018
f1_keywords:
- CReBar
- AFXEXT/CReBar
- AFXEXT/CReBar::AddBar
- AFXEXT/CReBar::Create
- AFXEXT/CReBar::GetReBarCtrl
helpviewer_keywords:
- CReBar [MFC], AddBar
- CReBar [MFC], Create
- CReBar [MFC], GetReBarCtrl
ms.assetid: c1ad2720-1d33-4106-8e4e-80aa84f93559
ms.openlocfilehash: 434232e8f99bf914b00379db53d4b4a37d24fe36
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502794"
---
# <a name="crebar-class"></a>CReBar (clase)

Barra de control que proporciona información de diseño, persistencia y estado para controles rebar.

## <a name="syntax"></a>Sintaxis

```
class CReBar : public CControlBar
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CReBar::AddBar](#addbar)|Agrega una banda a un rebar.|
|[CReBar::Create](#create)|Crea el control rebar y lo adjunta al `CReBar` objeto.|
|[CReBar::GetReBarCtrl](#getrebarctrl)|Permite el acceso directo al control común subyacente.|

## <a name="remarks"></a>Comentarios

Un objeto rebar puede contener diversas ventanas secundarias, normalmente otros controles, como cuadros de edición, barras de herramientas y cuadros de lista. Un objeto rebar puede mostrar sus ventanas secundarias en un mapa de bits especificado. La aplicación puede cambiar automáticamente el tamaño del rebar, o bien el usuario puede cambiar manualmente el tamaño del rebar haciendo clic o arrastrando su barra de redimensionamiento.

![Ejemplo de RebarMenu](../../mfc/reference/media/vc4sc61.gif "Ejemplo de RebarMenu")

## <a name="rebar-control"></a>Rebar (control)

Un objeto rebar se comporta de forma similar a un objeto Toolbar. Un rebar utiliza el mecanismo de hacer clic y arrastrar para cambiar el tamaño de sus bandas. Un control rebar puede contener una o varias bandas, cada una de las cuales tiene cualquier combinación de una barra de agarre, un mapa de bits, una etiqueta de texto y una ventana secundaria. Sin embargo, las bandas no pueden contener más de una ventana secundaria.

`CReBar`usa la clase [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) para proporcionar su implementación. Puede tener acceso al control rebar a través de [GetReBarCtrl](#getrebarctrl) para aprovechar las ventajas de las opciones de personalización del control. Para obtener más información sobre los controles rebar `CReBarCtrl`, vea. Para obtener más información sobre el uso de controles Rebar, vea [usar CReBarCtrl](../../mfc/using-crebarctrl.md).

> [!CAUTION]
>  Los objetos de control rebar y rebar no admiten el acoplamiento de barras de control MFC. Si `CRebar::EnableDocking` se llama a, la aplicación validará.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CReBar`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext. h

##  <a name="addbar"></a>  CReBar::AddBar

Llame a esta función miembro para agregar una banda al rebar.

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
Un puntero a un `CWnd` objeto que es la ventana secundaria que se va a insertar en el rebar. El objeto al que se hace referencia debe tener un WS_CHILD.

*lpszText*<br/>
Puntero a una cadena que contiene el texto que se va a mostrar en el rebar. NULL de forma predeterminada. El texto contenido en *lpszText* no forma parte de la ventana secundaria; está en el propio rebar.

*pbmp*<br/>
Un puntero a un `CBitmap` objeto que se va a mostrar en el fondo de rebar. NULL de forma predeterminada.

*dwStyle*<br/>
DWORD que contiene el estilo que se va a aplicar al rebar. Vea la `fStyle` Descripción de la función en la estructura de Win32 [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) para obtener una lista completa de los estilos de banda.

*clrFore*<br/>
Valor de COLORREF que representa el color de primer plano del rebar.

*clrBack*<br/>
Valor de COLORREF que representa el color de fondo del rebar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]

##  <a name="create"></a>CReBar:: Create

Llame a esta función miembro para crear un rebar.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Puntero al `CWnd` objeto cuya ventana de Windows es la primaria de la barra de estado. Normalmente, la ventana de marco.

*dwCtrlStyle*<br/>
Estilo del control rebar. De forma predeterminada, RBS_BANDBORDERS, que muestra líneas estrechas para separar las bandas adyacentes dentro del control rebar. Vea los [estilos de control rebar](/windows/win32/Controls/rebar-control-styles) en el Windows SDK para obtener una lista de estilos.

*dwStyle*<br/>
Estilos de la ventana rebar.

*nID*<br/>
IDENTIFICADOR de la ventana secundaria del rebar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CReBar:: AddBar](#addbar).

##  <a name="getrebarctrl"></a>  CReBar::GetReBarCtrl

Esta función miembro permite el acceso directo al control común subyacente.

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

Referencia a un objeto [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) .

### <a name="remarks"></a>Comentarios

Llame a esta función miembro para aprovechar las ventajas de la funcionalidad del control común de rebar de Windows en la personalización de rebar. Cuando se llama `GetReBarCtrl`a, devuelve un objeto de referencia `CReBarCtrl` al objeto, por lo que puede usar cualquier conjunto de funciones miembro.

Para obtener más información sobre `CReBarCtrl` cómo usar para personalizar el rebar, vea [usar CReBarCtrl](../../mfc/using-crebarctrl.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo MFCIE de MFC](../../overview/visual-cpp-samples.md)<br/>
[CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
