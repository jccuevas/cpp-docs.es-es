---
title: CMFCPropertyGridToolTipCtrl (clase)
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
ms.openlocfilehash: a7262416fa3555993ea237dd2f6b82b73ed9949c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429099"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>CMFCPropertyGridToolTipCtrl (clase)

Implementa una información sobre herramientas que controlan el [CMFCPropertyGridCtrl (clase)](../../mfc/reference/cmfcpropertygridctrl-class.md) usa para mostrar información sobre herramientas.

## <a name="syntax"></a>Sintaxis

```
class CMFCPropertyGridToolTipCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Name|Descripción|
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|Construye un objeto `CMFCPropertyGridToolTipCtrl`.|
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Name|Descripción|
|[CMFCPropertyGridToolTipCtrl::Create](#create)|Crea una ventana para el control tooltip.|
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|Desactiva y oculta el control tooltip.|
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Devuelve las coordenadas de la última posición del control tooltip.|
|[CMFCPropertyGridToolTipCtrl::Hide](#hide)|Oculta el control tooltip.|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|La clase [CWinApp](../../mfc/reference/cwinapp-class.md) lo usa para traducir los mensajes de ventana antes de que se envíen a las funciones de Windows [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) . (Invalida [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)).|
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|Establece el espaciado entre el texto de información sobre herramientas y el borde de la ventana de información sobre herramientas.|
|[CMFCPropertyGridToolTipCtrl::Track](#track)|Muestra el control de información sobre herramientas.|

## <a name="remarks"></a>Comentarios

Información sobre herramientas se muestra cuando el puntero se sitúa sobre un nombre de propiedad. El [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) clase muestra una información sobre herramientas para que resulte fácil de leer el usuario. Normalmente, la posición de una información sobre herramientas viene determinada por la posición del puntero. Mediante el uso de esta clase, la información sobre herramientas aparece sobre el nombre de propiedad y es similar a la extensión natural de propiedad, por lo que el nombre de propiedad está totalmente visible.

MFC automáticamente crea este control y se utiliza en el [CMFCPropertyGridCtrl (clase)](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCPropertyGridToolTipCtrl` clase y cómo mostrar el control tooltip.

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxpropertygridtooltipctrl.h

##  <a name="cmfcpropertygridtooltipctrl"></a>  CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl

Construye un objeto `CMFCPropertyGridToolTipCtrl`.

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

##  <a name="create"></a>  CMFCPropertyGridToolTipCtrl::Create

Crea una ventana para el control tooltip.

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[in] Un puntero a la ventana primaria.

### <a name="return-value"></a>Valor devuelto

TRUE si la ventana se ha creado correctamente; en caso contrario, FALSE.

##  <a name="deactivate"></a>  CMFCPropertyGridToolTipCtrl::Deactivate

Desactiva y oculta el control tooltip.

```
void Deactivate();
```

### <a name="remarks"></a>Comentarios

Este método establece la última posición y texto a los valores vacíos, para que las llamadas futuras a [CMFCPropertyGridToolTipCtrl::Track](#track) mostrar la información sobre herramientas.

##  <a name="getlastrect"></a>  CMFCPropertyGridToolTipCtrl::GetLastRect

Devuelve las coordenadas de la última posición del control tooltip.

```
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
[out] Contiene la última posición del control tooltip.

##  <a name="hide"></a>  CMFCPropertyGridToolTipCtrl::Hide

Oculta el control tooltip.

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
[in] Especifica el espaciado entre el texto del control de información sobre herramientas y el borde de la ventana de información sobre herramientas. El valor predeterminado es 10 píxeles.

##  <a name="track"></a>  CMFCPropertyGridToolTipCtrl::Track

Muestra el control de información sobre herramientas.

```
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
[in] Especifica la posición y el tamaño del control tooltip.

*strText*<br/>
[in] Especifica el texto que se mostrará en la información sobre herramientas.

### <a name="remarks"></a>Comentarios

Este método muestra el control de información sobre herramientas en la posición y el tamaño especificado por *rect*. Si la posición, el tamaño y el texto no han cambiado desde la última vez que se llamó a este método, este método tiene ningún efecto.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
