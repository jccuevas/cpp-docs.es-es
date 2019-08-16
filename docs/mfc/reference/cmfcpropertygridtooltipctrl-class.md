---
title: Clase CMFCPropertyGridToolTipCtrl
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
ms.openlocfilehash: f1b6f626b5f9844c73cd2225a7d6311f5b2f7d4f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505094"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>Clase CMFCPropertyGridToolTipCtrl

Implementa un control de información sobre herramientas que la [clase cmfcpropertygridctrl (](../../mfc/reference/cmfcpropertygridctrl-class.md) utiliza para mostrar la información sobre herramientas.

## <a name="syntax"></a>Sintaxis

```
class CMFCPropertyGridToolTipCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|NOMBRE|DESCRIPCIÓN|
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|Construye un objeto `CMFCPropertyGridToolTipCtrl`.|
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|NOMBRE|DESCRIPCIÓN|
|[CMFCPropertyGridToolTipCtrl::Create](#create)|Crea una ventana para el control ToolTip.|
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|Desactiva y oculta el control de información sobre herramientas.|
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Devuelve las coordenadas de la última posición del control ToolTip.|
|[CMFCPropertyGridToolTipCtrl::Hide](#hide)|Oculta el control ToolTip.|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|La clase [CWinApp](../../mfc/reference/cwinapp-class.md) lo usa para traducir los mensajes de ventana antes de que se envíen a las funciones de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Invalida [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)).|
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|Establece el espaciado entre el texto de información sobre herramientas y el borde de la ventana de información sobre herramientas.|
|[CMFCPropertyGridToolTipCtrl::Track](#track)|Muestra el control ToolTip.|

## <a name="remarks"></a>Comentarios

La información sobre herramientas se muestra cuando el puntero se coloca sobre un nombre de propiedad. La clase [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) muestra una información sobre herramientas para que el usuario pueda leerla fácilmente. Normalmente, la posición de una información sobre herramientas viene determinada por la posición del puntero. Mediante el uso de esta clase, la información sobre herramientas aparece sobre el nombre de la propiedad y se parece a la extensión de propiedad natural, de modo que el nombre de la propiedad es totalmente visible.

MFC crea automáticamente este control y lo usa en la [clase cmfcpropertygridctrl (](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto de `CMFCPropertyGridToolTipCtrl` la clase y cómo mostrar el control ToolTip.

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpropertygridtooltipctrl. h

##  <a name="cmfcpropertygridtooltipctrl"></a>  CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl

Construye un objeto `CMFCPropertyGridToolTipCtrl`.

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

##  <a name="create"></a>  CMFCPropertyGridToolTipCtrl::Create

Crea una ventana para el control ToolTip.

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
de Puntero a la ventana primaria.

### <a name="return-value"></a>Valor devuelto

TRUE si la ventana se creó correctamente; en caso contrario, FALSE.

##  <a name="deactivate"></a>  CMFCPropertyGridToolTipCtrl::Deactivate

Desactiva y oculta el control de información sobre herramientas.

```
void Deactivate();
```

### <a name="remarks"></a>Comentarios

Este método establece la última posición y el texto en valores vacíos, de modo que las llamadas futuras a [CMFCPropertyGridToolTipCtrl:: Track](#track) muestren la información sobre herramientas.

##  <a name="getlastrect"></a>  CMFCPropertyGridToolTipCtrl::GetLastRect

Devuelve las coordenadas de la última posición del control ToolTip.

```
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
enuncia Contiene la última posición del control ToolTip.

##  <a name="hide"></a>  CMFCPropertyGridToolTipCtrl::Hide

Oculta el control ToolTip.

```
void Hide();
```

##  <a name="settextmargin"></a>  CMFCPropertyGridToolTipCtrl::SetTextMargin

Establece el espaciado entre el texto de información sobre herramientas y el borde de la ventana de información sobre herramientas.

```
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>Parámetros

*nTextMargin*<br/>
de Especifica el espaciado entre el texto del control de información sobre herramientas y el borde de la ventana de información sobre herramientas. El valor predeterminado es 10 píxeles.

##  <a name="track"></a>  CMFCPropertyGridToolTipCtrl::Track

Muestra el control ToolTip.

```
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
de Especifica la posición y el tamaño del control ToolTip.

*strText*<br/>
de Especifica el texto que se va a mostrar en la información sobre herramientas.

### <a name="remarks"></a>Comentarios

Este método muestra el control de información sobre herramientas en la posición y el tamaño especificados por *Rect*. Si la posición, el tamaño y el texto no han cambiado desde la última vez que se llamó a este método, este método no tiene ningún efecto.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
