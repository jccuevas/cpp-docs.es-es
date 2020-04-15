---
title: CMFCPropertyGridToolTipCtrl Clase
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Create
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Deactivate
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::GetLastRect
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Hide
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::SetTextMargin
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Track
helpviewer_keywords:
- CMFCPropertyGridToolTipCtrl [MFC], CMFCPropertyGridToolTipCtrl
- CMFCPropertyGridToolTipCtrl [MFC], Create
- CMFCPropertyGridToolTipCtrl [MFC], Deactivate
- CMFCPropertyGridToolTipCtrl [MFC], GetLastRect
- CMFCPropertyGridToolTipCtrl [MFC], Hide
- CMFCPropertyGridToolTipCtrl [MFC], SetTextMargin
- CMFCPropertyGridToolTipCtrl [MFC], Track
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
ms.openlocfilehash: 94d75f914e5f7928d08dd2a87997ab02c4f16832
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361787"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>CMFCPropertyGridToolTipCtrl Clase

Implementa un control de información sobre herramientas que la [CMFCPropertyGridCtrl clase](../../mfc/reference/cmfcpropertygridctrl-class.md) utiliza para mostrar información sobre herramientas.

## <a name="syntax"></a>Sintaxis

```
class CMFCPropertyGridToolTipCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Nombre|Descripción|
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|Construye un objeto `CMFCPropertyGridToolTipCtrl`.|
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Nombre|Descripción|
|[CMFCPropertyGridToolTipCtrl::Create](#create)|Crea una ventana para el control de información sobre herramientas.|
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|Desactiva y oculta el control de información sobre herramientas.|
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Devuelve las coordenadas de la última posición del control de información sobre herramientas.|
|[CMFCPropertyGridToolTipCtrl::Ocultar](#hide)|Oculta el control de información sobre herramientas.|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|Utilizado por la clase [CWinApp](../../mfc/reference/cwinapp-class.md) para traducir mensajes de ventana antes de que se distribuyen a la [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) funciones de Windows. (Invalida [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)).|
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|Establece el espaciado entre el texto de información sobre herramientas y el borde de la ventana de información sobre herramientas.|
|[CMFCPropertyGridToolTipCtrl::Track](#track)|Muestra el control de información sobre herramientas.|

## <a name="remarks"></a>Observaciones

La información sobre herramientas se muestra cuando el puntero descansa sobre un nombre de propiedad. El [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) clase muestra una información sobre herramientas para que sea fácilmente legible por el usuario. Normalmente, la posición de una información sobre herramientas viene determinada por la posición del puntero. Mediante el uso de esta clase, la información sobre herramientas aparece sobre el nombre de la propiedad y se asemeja a la extensión de propiedad natural, por lo que el nombre de propiedad es totalmente visible.

MFC crea automáticamente este control y lo utiliza en la [clase CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCPropertyGridToolTipCtrl` cómo construir un objeto de la clase y cómo mostrar el control de información sobre herramientas.

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpropertygridtooltipctrl.h

## <a name="cmfcpropertygridtooltipctrlcmfcpropertygridtooltipctrl"></a><a name="cmfcpropertygridtooltipctrl"></a>CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl

Construye un objeto `CMFCPropertyGridToolTipCtrl`.

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

## <a name="cmfcpropertygridtooltipctrlcreate"></a><a name="create"></a>CMFCPropertyGridToolTipCtrl::Create

Crea una ventana para el control de información sobre herramientas.

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[en] Un puntero a la ventana primaria.

### <a name="return-value"></a>Valor devuelto

TRUESi la ventana se creó correctamente; de lo contrario, FALSE.

## <a name="cmfcpropertygridtooltipctrldeactivate"></a><a name="deactivate"></a>CMFCPropertyGridToolTipCtrl::Deactivate

Desactiva y oculta el control de información sobre herramientas.

```
void Deactivate();
```

### <a name="remarks"></a>Observaciones

Este método establece la última posición y el texto en valores vacíos, por lo que futuras llamadas a [CMFCPropertyGridToolTipCtrl::Track](#track) muestran la información sobre herramientas.

## <a name="cmfcpropertygridtooltipctrlgetlastrect"></a><a name="getlastrect"></a>CMFCPropertyGridToolTipCtrl::GetLastRect

Devuelve las coordenadas de la última posición del control de información sobre herramientas.

```
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
[fuera] Contiene la última posición del control de información sobre herramientas.

## <a name="cmfcpropertygridtooltipctrlhide"></a><a name="hide"></a>CMFCPropertyGridToolTipCtrl::Ocultar

Oculta el control de información sobre herramientas.

```
void Hide();
```

## <a name="cmfcpropertygridtooltipctrlsettextmargin"></a><a name="settextmargin"></a>CMFCPropertyGridToolTipCtrl::SetTextMargin

Establece el espaciado entre el texto de información sobre herramientas y el borde de la ventana de información sobre herramientas.

```
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>Parámetros

*nTextMargin*<br/>
[en] Especifica el espaciado entre el texto del control de información sobre herramientas y el borde de la ventana de información sobre herramientas. El valor predeterminado es 10 píxeles.

## <a name="cmfcpropertygridtooltipctrltrack"></a><a name="track"></a>CMFCPropertyGridToolTipCtrl::Track

Muestra el control de información sobre herramientas.

```
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
[en] Especifica la posición y el tamaño del control de información sobre herramientas.

*strText*<br/>
[en] Especifica el texto que se mostrará en la información sobre herramientas.

### <a name="remarks"></a>Observaciones

Este método muestra el control de información sobre herramientas en la posición y el tamaño especificados por *rect*. Si la posición, el tamaño y el texto no han cambiado desde la última vez que se llamó a este método, este método no tiene ningún efecto.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
