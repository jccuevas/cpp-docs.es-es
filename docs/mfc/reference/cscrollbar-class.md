---
title: CScrollBar (clase)
ms.date: 11/04/2016
f1_keywords:
- CScrollBar
- AFXWIN/CScrollBar
- AFXWIN/CScrollBar::CScrollBar
- AFXWIN/CScrollBar::Create
- AFXWIN/CScrollBar::EnableScrollBar
- AFXWIN/CScrollBar::GetScrollBarInfo
- AFXWIN/CScrollBar::GetScrollInfo
- AFXWIN/CScrollBar::GetScrollLimit
- AFXWIN/CScrollBar::GetScrollPos
- AFXWIN/CScrollBar::GetScrollRange
- AFXWIN/CScrollBar::SetScrollInfo
- AFXWIN/CScrollBar::SetScrollPos
- AFXWIN/CScrollBar::SetScrollRange
- AFXWIN/CScrollBar::ShowScrollBar
helpviewer_keywords:
- CScrollBar [MFC], CScrollBar
- CScrollBar [MFC], Create
- CScrollBar [MFC], EnableScrollBar
- CScrollBar [MFC], GetScrollBarInfo
- CScrollBar [MFC], GetScrollInfo
- CScrollBar [MFC], GetScrollLimit
- CScrollBar [MFC], GetScrollPos
- CScrollBar [MFC], GetScrollRange
- CScrollBar [MFC], SetScrollInfo
- CScrollBar [MFC], SetScrollPos
- CScrollBar [MFC], SetScrollRange
- CScrollBar [MFC], ShowScrollBar
ms.assetid: f3735ca5-73ea-46dc-918b-4d824c9fe47f
ms.openlocfilehash: 761d7e9db650c6d95e916c85bd7456d9b1c647c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318533"
---
# <a name="cscrollbar-class"></a>CScrollBar (clase)

Proporciona la funcionalidad de un control de barra de desplazamiento de Windows.

## <a name="syntax"></a>Sintaxis

```
class CScrollBar : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CScrollBar::CScrollBar](#cscrollbar)|Construye un objeto `CScrollBar`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CScrollBar::Crear](#create)|Crea la barra de desplazamiento de `CScrollBar` Windows y la adjunta al objeto.|
|[CScrollBar::EnableScrollBar](#enablescrollbar)|Habilita o deshabilita una o ambas flechas de una barra de desplazamiento.|
|[CScrollBar::GetScrollBarInfo](#getscrollbarinfo)|Recupera información sobre la barra `SCROLLBARINFO` de desplazamiento mediante una estructura.|
|[CScrollBar::GetScrollInfo](#getscrollinfo)|Recupera información sobre la barra de desplazamiento.|
|[CScrollBar::GetScrollLimit](#getscrolllimit)|Recupera el límite de la barra de desplazamiento|
|[CScrollBar::GetScrollPos](#getscrollpos)|Recupera la posición actual de un cuadro de desplazamiento.|
|[CScrollBar::GetScrollRange](#getscrollrange)|Recupera las posiciones actuales de la barra de desplazamiento mínima y máxima para la barra de desplazamiento determinada.|
|[CScrollBar::SetScrollInfo](#setscrollinfo)|Establece la información acerca de la barra de desplazamiento.|
|[CScrollBar::SetScrollPos](#setscrollpos)|Establece la posición actual de un cuadro de desplazamiento.|
|[CScrollBar::SetScrollRange](#setscrollrange)|Establece los valores de posición mínimo y máximo de la barra de desplazamiento especificada.|
|[CScrollBar::ShowScrollBar](#showscrollbar)|Muestra u oculta una barra de desplazamiento.|

## <a name="remarks"></a>Observaciones

Crear un control de barra de desplazamiento en dos pasos. En primer lugar, `CScrollBar` llame `CScrollBar` al constructor para construir el objeto y, a continuación, `CScrollBar` llame a la [create](#create) función miembro para crear el control de barra de desplazamiento de Windows y adjuntarlo al objeto.

Si crea `CScrollBar` un objeto dentro de un cuadro `CScrollBar` de diálogo (a través de un recurso de cuadro de diálogo), se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.

Si crea `CScrollBar` un objeto dentro de una ventana, es posible que también deba destruirlo.

Si crea `CScrollBar` el objeto en la pila, se destruye automáticamente. Si crea `CScrollBar` el objeto en el montón mediante la **nueva** función, debe llamar a **delete** en el objeto para destruirlo cuando el usuario termine la barra de desplazamiento de Windows.

Si asigna memoria en `CScrollBar` el objeto, reemplace el `CScrollBar` destructor para eliminar las asignaciones.

Para obtener información `CScrollBar`relacionada sobre el uso de , vea [Controles](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CScrollBar`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cscrollbarcreate"></a><a name="create"></a>CScrollBar::Crear

Crea la barra de desplazamiento de `CScrollBar` Windows y la adjunta al objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo de la barra de desplazamiento. Aplique cualquier combinación de [estilos de barra de desplazamiento](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles) a la barra de desplazamiento.

*Rect*<br/>
Especifica el tamaño y la posición de la barra de desplazamiento. Puede ser `RECT` una estructura `CRect` o un objeto.

*pParentWnd*<br/>
Especifica la ventana primaria de la `CDialog` barra de desplazamiento, normalmente un objeto. No debe ser NULL.

*nID*<br/>
Identificador de control de la barra de desplazamiento.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Construir un `CScrollBar` objeto en dos pasos. En primer lugar, llame al `CScrollBar` constructor, que construye el objeto; a `Create`continuación, llame a , que crea e inicializa `CScrollBar` la barra de desplazamiento de Windows asociada y la adjunta al objeto.

Aplique los siguientes [estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles) de ventana a una barra de desplazamiento:

- WS_CHILD Siempre

- WS_VISIBLE Por lo general

- WS_DISABLED Rara vez

- WS_GROUP Para agrupar controles

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]

## <a name="cscrollbarcscrollbar"></a><a name="cscrollbar"></a>CScrollBar::CScrollBar

Construye un objeto `CScrollBar`.

```
CScrollBar();
```

### <a name="remarks"></a>Observaciones

Después de construir el `Create` objeto, llame a la función miembro para crear e inicializar la barra de desplazamiento de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]

## <a name="cscrollbarenablescrollbar"></a><a name="enablescrollbar"></a>CScrollBar::EnableScrollBar

Habilita o deshabilita una o ambas flechas de una barra de desplazamiento.

```
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```

### <a name="parameters"></a>Parámetros

*nArrowFlags*<br/>
Especifica si las flechas de desplazamiento están habilitadas o deshabilitadas y qué flechas están habilitadas o deshabilitadas. Este parámetro puede ser uno de los siguientes valores:

- ESB_ENABLE_BOTH Habilita ambas flechas de una barra de desplazamiento.

- ESB_DISABLE_LTUP Deshabilita la flecha izquierda de una barra de desplazamiento horizontal o la flecha hacia arriba de una barra de desplazamiento vertical.

- ESB_DISABLE_RTDN Deshabilita la flecha derecha de una barra de desplazamiento horizontal o la flecha hacia abajo de una barra de desplazamiento vertical.

- ESB_DISABLE_BOTH Deshabilita ambas flechas de una barra de desplazamiento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si las flechas están habilitadas o deshabilitadas según lo especificado; de lo contrario 0, lo que indica que las flechas ya están en el estado solicitado o que se ha producido un error.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CScrollBar::SetScrollRange](#setscrollrange).

## <a name="cscrollbargetscrollbarinfo"></a><a name="getscrollbarinfo"></a>CScrollBar::GetScrollBarInfo

Recupera la información que la estructura `SCROLLBARINFO` mantiene sobre una barra de desplazamiento.

```
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;
```

### <a name="parameters"></a>Parámetros

*pScrollInfo*<br/>
Un puntero a la [SCROLLBARINFO](/windows/win32/api/winuser/ns-winuser-scrollbarinfo) estructura.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Esta función miembro emula la funcionalidad del [mensaje de SBM_SCROLLBARINFO,](/windows/win32/Controls/sbm-getscrollbarinfo) como se describe en el Windows SDK.

## <a name="cscrollbargetscrollinfo"></a><a name="getscrollinfo"></a>CScrollBar::GetScrollInfo

Recupera la información que la estructura `SCROLLINFO` mantiene sobre una barra de desplazamiento.

```
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    UINT nMask = SIF_ALL);
```

### <a name="parameters"></a>Parámetros

*lpScrollInfo*<br/>
Un puntero a una estructura [SCROLLINFO.](/windows/win32/api/winuser/ns-winuser-scrollinfo) Consulte el Windows SDK para obtener más información acerca de esta estructura.

*nMask*<br/>
Especifica los parámetros de la barra de desplazamiento que se van a recuperar. El uso típico, SIF_ALL, especifica una combinación de SIF_PAGE, SIF_POS, SIF_TRACKPOS y SIF_RANGE. Consulte `SCROLLINFO` para obtener más información sobre los valores nMask.

### <a name="return-value"></a>Valor devuelto

Si el mensaje recuperó algún valor, el valor devuelto es TRUE. De lo contrario, es FALSE.

### <a name="remarks"></a>Observaciones

`GetScrollInfo`permite a las aplicaciones utilizar posiciones de desplazamiento de 32 bits.

La estructura [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) contiene información sobre una barra de desplazamiento, incluidas las posiciones de desplazamiento mínima y máxima, el tamaño de página y la posición del cuadro de desplazamiento (el pulgar). Consulte `SCROLLINFO` el tema de estructura en el Windows SDK para obtener más información acerca de cómo cambiar los valores predeterminados de la estructura.

Los controladores de mensajes de Windows MFC que indican la posición de la barra de desplazamiento, [CWnd::OnHScroll, y [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll), proporcionan solo 16 bits de datos de posición. `GetScrollInfo`y `SetScrollInfo` proporcionar 32 bits de datos de posición de la barra de desplazamiento. Por lo tanto, `GetScrollInfo` una `CWnd::OnHScroll` aplicación `CWnd::OnVScroll` puede llamar mientras se procesa o para obtener datos de posición de la barra de desplazamiento de 32 bits.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrolllimit"></a><a name="getscrolllimit"></a>CScrollBar::GetScrollLimit

Recupera la posición de desplazamiento máxima de la barra de desplazamiento.

```
int GetScrollLimit();
```

### <a name="return-value"></a>Valor devuelto

Especifica la posición máxima de una barra de desplazamiento si se realiza correctamente; de lo contrario 0.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrollpos"></a><a name="getscrollpos"></a>CScrollBar::GetScrollPos

Recupera la posición actual de un cuadro de desplazamiento.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Valor devuelto

Especifica la posición actual del cuadro de desplazamiento si se realiza correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La posición actual es un valor relativo que depende del rango de desplazamiento actual. Por ejemplo, si el rango de desplazamiento es de 100 a 200 y el cuadro de desplazamiento está en el centro de la barra, la posición actual es 150.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbargetscrollrange"></a><a name="getscrollrange"></a>CScrollBar::GetScrollRange

Copia las posiciones actuales de la barra de desplazamiento mínima y máxima para la barra de desplazamiento especificada en las ubicaciones especificadas por *lpMinPos* y *lpMaxPos*.

```
void GetScrollRange(
    LPINT lpMinPos,
    LPINT lpMaxPos) const;
```

### <a name="parameters"></a>Parámetros

*lpMinPos*<br/>
Apunta a la variable entera que va a recibir la posición mínima.

*lpMaxPos*<br/>
Apunta a la variable entera que va a recibir la posición máxima.

### <a name="remarks"></a>Observaciones

El intervalo predeterminado para un control de barra de desplazamiento está vacío (ambos valores son 0).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

## <a name="cscrollbarsetscrollinfo"></a><a name="setscrollinfo"></a>CScrollBar::SetScrollInfo

Establece la información `SCROLLINFO` que la estructura mantiene sobre una barra de desplazamiento.

```
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpScrollInfo*<br/>
Un puntero a una estructura [SCROLLINFO.](/windows/win32/api/winuser/ns-winuser-scrollinfo)

*bRedraw*<br/>
Especifica si se debe volver a dibujar la barra de desplazamiento para reflejar la nueva información. Si *bRedraw* es TRUE, se vuelve a dibujar la barra de desplazamiento. Si es FALSE, no se vuelve a dibujar. La barra de desplazamiento se vuelve a dibujar de forma predeterminada.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, la devolución es TRUE. De lo contrario, es FALSE.

### <a name="remarks"></a>Observaciones

Debe proporcionar los valores `SCROLLINFO` requeridos por los parámetros de estructura, incluidos los valores de marca.

La `SCROLLINFO` estructura contiene información sobre una barra de desplazamiento, incluidas las posiciones de desplazamiento mínima y máxima, el tamaño de página y la posición del cuadro de desplazamiento (el pulgar). Consulte el tema de estructura [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) en el Windows SDK para obtener más información acerca de cómo cambiar los valores predeterminados de la estructura.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]

## <a name="cscrollbarsetscrollpos"></a><a name="setscrollpos"></a>CScrollBar::SetScrollPos

Establece la posición actual de un cuadro de desplazamiento en la especificada por *nPos* y, si se especifica, vuelve a dibujar la barra de desplazamiento para reflejar la nueva posición.

```
int SetScrollPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parámetros

*Fnco*<br/>
Especifica la nueva posición del cuadro de desplazamiento. Debe estar dentro del rango de desplazamiento.

*bRedraw*<br/>
Especifica si se debe volver a dibujar la barra de desplazamiento para reflejar la nueva posición. Si *bRedraw* es TRUE, se vuelve a dibujar la barra de desplazamiento. Si es FALSE, no se vuelve a dibujar. La barra de desplazamiento se vuelve a dibujar de forma predeterminada.

### <a name="return-value"></a>Valor devuelto

Especifica la posición anterior del cuadro de desplazamiento si se realiza correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Establezca *bRedraw en* FALSE siempre que la barra de desplazamiento se vuelva a dibujar mediante una llamada posterior a otra función para evitar que la barra de desplazamiento se vuelva a dibujar dos veces en un intervalo corto.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CScrollBar::SetScrollRange](#setscrollrange).

## <a name="cscrollbarsetscrollrange"></a><a name="setscrollrange"></a>CScrollBar::SetScrollRange

Establece los valores de posición mínimo y máximo de la barra de desplazamiento especificada.

```
void SetScrollRange(
    int nMinPos,
    int nMaxPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parámetros

*nMinPos*<br/>
Especifica la posición de desplazamiento mínima.

*nMaxPos*<br/>
Especifica la posición máxima de desplazamiento.

*bRedraw*<br/>
Especifica si se debe volver a dibujar la barra de desplazamiento para reflejar el cambio. Si *bRedraw* es TRUE, se vuelve a dibujar la barra de desplazamiento; si FALSE, no se vuelve a dibujar. Se vuelve a dibujar de forma predeterminada.

### <a name="remarks"></a>Observaciones

Establezca *nMinPos* y *nMaxPos* en 0 para ocultar las barras de desplazamiento estándar.

No llame a esta función para ocultar una barra de desplazamiento mientras procesa un mensaje de notificación de barra de desplazamiento.

Si una `SetScrollRange` llamada a inmediatamente sigue `SetScrollPos` una llamada a la `SetScrollPos` función miembro, establezca *bRedraw* en 0 para evitar que la barra de desplazamiento se vuelva a dibujar dos veces.

La diferencia entre los valores especificados por *nMinPos* y *nMaxPos* no debe ser mayor que 32.767. El intervalo predeterminado para un control de barra de desplazamiento está vacío *(nMinPos* y *nMaxPos* son 0).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]

## <a name="cscrollbarshowscrollbar"></a><a name="showscrollbar"></a>CScrollBar::ShowScrollBar

Muestra u oculta una barra de desplazamiento.

```
void ShowScrollBar(BOOL bShow = TRUE);
```

### <a name="parameters"></a>Parámetros

*bMostrar*<br/>
Especifica si la barra de desplazamiento se muestra u oculta. Si este parámetro es TRUE, se muestra la barra de desplazamiento; de lo contrario, está oculto.

### <a name="remarks"></a>Observaciones

Una aplicación no debe llamar a esta función para ocultar una barra de desplazamiento mientras se procesa un mensaje de notificación de barra de desplazamiento.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CScrollBar::Create](#create).

## <a name="see-also"></a>Consulte también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CButton (clase)](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox (clase)](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox (clase)](../../mfc/reference/clistbox-class.md)<br/>
[Clase CStatic](../../mfc/reference/cstatic-class.md)<br/>
[Clase CDialog](../../mfc/reference/cdialog-class.md)
