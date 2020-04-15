---
title: Clase CReBar
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
ms.openlocfilehash: c1379d1ef8effea0df564da1b43769bb9a11435d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363933"
---
# <a name="crebar-class"></a>Clase CReBar

Barra de control que proporciona información de diseño, persistencia y estado para controles rebar.

## <a name="syntax"></a>Sintaxis

```
class CReBar : public CControlBar
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CReBar::AddBar](#addbar)|Agrega una banda a una armadura.|
|[CReBar::Crear](#create)|Crea el control de armadura y `CReBar` lo adjunta al objeto.|
|[CreBar::GetReBarCtrl](#getrebarctrl)|Permite el acceso directo al control común subyacente.|

## <a name="remarks"></a>Observaciones

Un objeto de armadura puede contener una variedad de ventanas secundarias, normalmente otros controles, incluidos cuadros de edición, barras de herramientas y cuadros de lista. Un objeto de armadura puede mostrar sus ventanas secundarias sobre un mapa de bits especificado. La aplicación puede cambiar automáticamente el tamaño de la armadura, o el usuario puede cambiar manualmente el tamaño de la armadura haciendo clic o arrastrando su barra de pinzamiento.

![Ejemplo de RebarMenu](../../mfc/reference/media/vc4sc61.gif "Ejemplo de RebarMenu")

## <a name="rebar-control"></a>Control de armadura

Un objeto de armadura se comporta de forma similar a un objeto de barra de herramientas. Una armadura utiliza el mecanismo de hacer clic y arrastrar para cambiar el tamaño de sus bandas. Un control de armadura puede contener una o más bandas, con cada banda que tenga cualquier combinación de una barra de pinzamiento, un mapa de bits, una etiqueta de texto y una ventana secundaria. Sin embargo, las bandas no pueden contener más de una ventana secundaria.

`CReBar`utiliza la [clase CReBarCtrl](../../mfc/reference/crebarctrl-class.md) para proporcionar su implementación. Puede tener acceso al control de armadura a través de [GetReBarCtrl](#getrebarctrl) para aprovechar las opciones de personalización del control. Para obtener más información acerca `CReBarCtrl`de los controles de armadura, consulte . Para obtener más información sobre el uso de controles de armadura, vea Uso de [CReBarCtrl](../../mfc/using-crebarctrl.md).

> [!CAUTION]
> Los objetos de control de armadura y armadura no admiten el acoplamiento de barras de control MFC. Si `CRebar::EnableDocking` se llama, la aplicación se afirmará.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CReBar`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext.h

## <a name="crebaraddbar"></a><a name="addbar"></a>CReBar::AddBar

Llame a esta función miembro para agregar una banda a la armadura.

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
Puntero a `CWnd` un objeto que es la ventana secundaria que se va a insertar en la armadura. El objeto al que se hace referencia debe tener un WS_CHILD.

*lpszText*<br/>
Puntero a una cadena que contiene el texto que aparecerá en la armadura. NULL de forma predeterminada. El texto contenido en *lpszText* no forma parte de la ventana secundaria; está en la armadura en sí.

*pbmp*<br/>
Puntero a `CBitmap` un objeto que se mostrará en el fondo de armadura. NULL de forma predeterminada.

*dwStyle*<br/>
DWORD que contiene el estilo que se aplicará a la armadura. Consulte `fStyle` la descripción de la función en la estructura [Win32 REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) para obtener una lista completa de los estilos de banda.

*clrFore*<br/>
Un valor COLORREF que representa el color de primer plano de la armadura.

*clrBack*<br/>
Un valor COLORREF que representa el color de fondo de la armadura.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]

## <a name="crebarcreate"></a><a name="create"></a>CReBar::Crear

Llame a esta función miembro para crear una armadura.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Puntero al `CWnd` objeto cuya ventana de Windows es el elemento primario de la barra de estado. Normalmente la ventana de marco.

*dwCtrlStyle*<br/>
El estilo de control de armadura. De forma predeterminada, RBS_BANDBORDERS, que muestra líneas estrechas para separar las bandas adyacentes dentro del control de armadura. Consulte [Estilos](/windows/win32/Controls/rebar-control-styles) de control de armadura en el Windows SDK para obtener una lista de estilos.

*dwStyle*<br/>
Los estilos de la ventana de armadura.

*nID*<br/>
Identificación de la ventana secundaria de la armadura.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CReBar::AddBar](#addbar).

## <a name="crebargetrebarctrl"></a><a name="getrebarctrl"></a>CreBar::GetReBarCtrl

Esta función miembro permite el acceso directo al control común subyacente.

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

Una referencia a un [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) objeto.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro para aprovechar la funcionalidad de la armadura de Windows control común en la personalización de la armadura. Cuando se `GetReBarCtrl`llama a , devuelve `CReBarCtrl` un objeto de referencia al objeto para que pueda utilizar cualquiera de los conjuntos de funciones miembro.

Para obtener más `CReBarCtrl` información sobre el uso de la armadura, consulte Uso de [CReBarCtrl](../../mfc/using-crebarctrl.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo MFCIE de MFC](../../overview/visual-cpp-samples.md)<br/>
[CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
