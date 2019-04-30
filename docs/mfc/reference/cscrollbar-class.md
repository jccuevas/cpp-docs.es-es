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
ms.openlocfilehash: d677d72b7e758fcdaa7df0e2918e9bbec3e18ee9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324238"
---
# <a name="cscrollbar-class"></a>CScrollBar (clase)

Proporciona la funcionalidad de un control de barra de desplazamiento de Windows.

## <a name="syntax"></a>Sintaxis

```
class CScrollBar : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CScrollBar::CScrollBar](#cscrollbar)|Construye un objeto `CScrollBar`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CScrollBar::Create](#create)|Crea la barra de desplazamiento de Windows y lo adjunta a la `CScrollBar` objeto.|
|[CScrollBar::EnableScrollBar](#enablescrollbar)|Habilita o deshabilita una o ambas flechas de una barra de desplazamiento.|
|[CScrollBar::GetScrollBarInfo](#getscrollbarinfo)|Recupera información sobre el uso de la barra de desplazamiento un `SCROLLBARINFO` estructura.|
|[CScrollBar::GetScrollInfo](#getscrollinfo)|Recupera información acerca de la barra de desplazamiento.|
|[CScrollBar::GetScrollLimit](#getscrolllimit)|Recupera el límite de la barra de desplazamiento|
|[CScrollBar::GetScrollPos](#getscrollpos)|Recupera la posición actual de un cuadro de desplazamiento.|
|[CScrollBar::GetScrollRange](#getscrollrange)|Recupera las posiciones actuales de barra de desplazamiento mínimo y máximo de la barra de desplazamiento especificada.|
|[CScrollBar::SetScrollInfo](#setscrollinfo)|Establece la información acerca de la barra de desplazamiento.|
|[CScrollBar::SetScrollPos](#setscrollpos)|Establece la posición actual de un cuadro de desplazamiento.|
|[CScrollBar::SetScrollRange](#setscrollrange)|Establece los valores de posición mínimo y máximo de la barra de desplazamiento especificada.|
|[CScrollBar::ShowScrollBar](#showscrollbar)|Muestra u oculta una barra de desplazamiento.|

## <a name="remarks"></a>Comentarios

Crear un control de barra de desplazamiento en dos pasos. En primer lugar, llame al constructor `CScrollBar` para construir el `CScrollBar` objeto y, después, llame a la [crear](#create) función miembro para crear el control de barra de desplazamiento de Windows y adjuntarlo a la `CScrollBar` objeto.

Si creas un `CScrollBar` objeto dentro de un cuadro de diálogo (a través de un recurso de cuadro de diálogo), el `CScrollBar` se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.

Si creas un `CScrollBar` objeto dentro de una ventana, es posible que también deba destruirlo.

Si crea la `CScrollBar` objeto en la pila, se destruye automáticamente. Si crea el `CScrollBar` objeto en el montón mediante el uso de la **nueva** función, debe llamar a **eliminar** en el objeto que lo destruirá cuando el usuario finaliza la barra de desplazamiento de Windows.

Si asigna memoria en el `CScrollBar` objeto, invalide el `CScrollBar` destructor para deshacerse de las asignaciones.

Para obtener información relacionada sobre el uso de `CScrollBar`, consulte [controles](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CScrollBar`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="create"></a>  CScrollBar::Create

Crea la barra de desplazamiento de Windows y lo adjunta a la `CScrollBar` objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el desplazamiento del estilo de la barra. Aplicar cualquier combinación de [estilos de barra de desplazamiento](../../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles) a la barra de desplazamiento.

*rect*<br/>
Especifica el tamaño de la barra de desplazamiento y la posición. Puede ser un `RECT` estructura o un `CRect` objeto.

*pParentWnd*<br/>
Especifica el desplazamiento principal ventana de barra, normalmente un `CDialog` objeto. No debe ser NULL.

*nID*<br/>
Id. de control de la barra de desplazamiento.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Construir un `CScrollBar` objeto en dos pasos. En primer lugar, llame al constructor, que construye la `CScrollBar` objeto; a continuación, llamar a `Create`, que crea e inicializa la barra de desplazamiento de Windows asociada y lo adjunta a la `CScrollBar` objeto.

Aplique el siguiente [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) a una barra de desplazamiento:

- WS_CHILD siempre

- WS_VISIBLE normalmente

- WS_DISABLED rara vez

- WS_GROUP a controles de grupo

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]

##  <a name="cscrollbar"></a>  CScrollBar::CScrollBar

Construye un objeto `CScrollBar`.

```
CScrollBar();
```

### <a name="remarks"></a>Comentarios

Después de crear el objeto, llame a la `Create` la función miembro para crear e inicializar la barra de desplazamiento de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]

##  <a name="enablescrollbar"></a>  CScrollBar::EnableScrollBar

Habilita o deshabilita una o ambas flechas de una barra de desplazamiento.

```
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```

### <a name="parameters"></a>Parámetros

*nArrowFlags*<br/>
Especifica si se habilitan o deshabilitan las flechas de desplazamiento y qué flechas están habilitadas o deshabilitadas. Este parámetro puede ser uno de los siguientes valores:

- ESB_ENABLE_BOTH permite ambas flechas de una barra de desplazamiento.

- ESB_DISABLE_LTUP deshabilita la flecha izquierda de una barra de desplazamiento horizontal o la flecha arriba de una barra de desplazamiento vertical.

- ESB_DISABLE_RTDN deshabilita la flecha derecha de una barra de desplazamiento horizontal o la flecha abajo de una barra de desplazamiento vertical.

- ESB_DISABLE_BOTH deshabilita ambas flechas de una barra de desplazamiento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se habilitan o deshabilitan según lo especificado; las flechas en caso contrario, 0, lo que indica que las flechas ya están en el estado solicitado o que se ha producido un error.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CScrollBar::SetScrollRange](#setscrollrange).

##  <a name="getscrollbarinfo"></a>  CScrollBar::GetScrollBarInfo

Recupera la información que la estructura `SCROLLBARINFO` mantiene sobre una barra de desplazamiento.

```
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;
```

### <a name="parameters"></a>Parámetros

*pScrollInfo*<br/>
Un puntero a la [SCROLLBARINFO](/windows/desktop/api/winuser/ns-winuser-tagscrollbarinfo) estructura.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad de la [SBM_SCROLLBARINFO](/windows/desktop/Controls/sbm-getscrollbarinfo) del mensaje, como se describe en el SDK de Windows.

##  <a name="getscrollinfo"></a>  CScrollBar::GetScrollInfo

Recupera la información que la estructura `SCROLLINFO` mantiene sobre una barra de desplazamiento.

```
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    UINT nMask = SIF_ALL);
```

### <a name="parameters"></a>Parámetros

*lpScrollInfo*<br/>
Un puntero a un [SCROLLINFO](/windows/desktop/api/winuser/ns-winuser-tagscrollinfo) estructura. Consulte el SDK de Windows para obtener más información acerca de esta estructura.

*nMask*<br/>
Especifica los parámetros de la barra de desplazamiento para recuperar. Un uso típico, SIF_ALL, especifica una combinación de SIF_PAGE, SIF_POS, SIF_TRACKPOS y SIF_RANGE. Consulte `SCROLLINFO` para obtener más información sobre los valores de nMask.

### <a name="return-value"></a>Valor devuelto

Si el mensaje puede recuperar los valores, el valor devuelto es TRUE. En caso contrario, es FALSE.

### <a name="remarks"></a>Comentarios

`GetScrollInfo` permite a las aplicaciones usar posiciones de desplazamiento de 32 bits.

El [SCROLLINFO](/windows/desktop/api/winuser/ns-winuser-tagscrollinfo) estructura contiene información sobre una barra de desplazamiento, incluidos los valores mínimo y máximo de la posición del cuadro de desplazamiento (control), el tamaño de página y las posiciones de desplazamiento. Vea el `SCROLLINFO` tema de la estructura en el SDK de Windows para obtener más información acerca de cómo cambiar los valores predeterminados de la estructura.

Controladores que indican la posición de la barra de desplazamiento, de mensaje de la Windows MFC [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) y [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll), proporcione solo de 16 bits de datos de posición. `GetScrollInfo` y `SetScrollInfo` proporcionar 32 bits de datos de la posición de la barra de desplazamiento. Por lo tanto, una aplicación puede llamar a `GetScrollInfo` al procesar cualquiera `CWnd::OnHScroll` o `CWnd::OnVScroll` para obtener datos de posición de barra de desplazamiento de 32 bits.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

##  <a name="getscrolllimit"></a>  CScrollBar::GetScrollLimit

Recupera el número máximo de la barra de desplazamiento de la posición de desplazamiento.

```
int GetScrollLimit();
```

### <a name="return-value"></a>Valor devuelto

Especifica la posición máxima de una barra de desplazamiento si se realiza correctamente; en caso contrario, es 0.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

##  <a name="getscrollpos"></a>  CScrollBar::GetScrollPos

Recupera la posición actual de un cuadro de desplazamiento.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Valor devuelto

Especifica la posición actual del cuadro de desplazamiento si se realiza correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

La posición actual es un valor relativo a los que depende del intervalo de desplazamiento actual. Por ejemplo, si el intervalo de desplazamiento es de 100 a 200 y el cuadro de desplazamiento está en medio de la barra, la posición actual es 150.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

##  <a name="getscrollrange"></a>  CScrollBar::GetScrollRange

Copia las posiciones actuales de barra de desplazamiento mínimo y máximo de la barra de desplazamiento especificada en las ubicaciones especificadas por *lpMinPos* y *lpMaxPos*.

```
void GetScrollRange(
    LPINT lpMinPos,
    LPINT lpMaxPos) const;
```

### <a name="parameters"></a>Parámetros

*lpMinPos*<br/>
Apunta a la variable de entero que se va a recibir la posición mínima.

*lpMaxPos*<br/>
Apunta a la variable de entero que se va a recibir la posición máxima.

### <a name="remarks"></a>Comentarios

El intervalo predeterminado para un control de barra de desplazamiento está vacío (ambos valores son 0).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

##  <a name="setscrollinfo"></a>  CScrollBar::SetScrollInfo

Establece la información que el `SCROLLINFO` estructura se mantiene sobre una barra de desplazamiento.

```
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpScrollInfo*<br/>
Un puntero a un [SCROLLINFO](/windows/desktop/api/winuser/ns-winuser-tagscrollinfo) estructura.

*bRedraw*<br/>
Especifica si se debe volver a dibujar la barra de desplazamiento para reflejar la nueva información. Si *bRedraw* es TRUE, se vuelve a dibujar la barra de desplazamiento. Si es FALSE, no se actualiza. Se vuelve a dibujar la barra de desplazamiento de forma predeterminada.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el valor devuelto es TRUE. En caso contrario, es FALSE.

### <a name="remarks"></a>Comentarios

Debe proporcionar los valores requeridos por la `SCROLLINFO` estructura parámetros, incluidos los valores de indicador.

El `SCROLLINFO` estructura contiene información sobre una barra de desplazamiento, incluidos los valores mínimo y máximo de la posición del cuadro de desplazamiento (control), el tamaño de página y las posiciones de desplazamiento. Consulte la [SCROLLINFO](/windows/desktop/api/winuser/ns-winuser-tagscrollinfo) tema de la estructura en el SDK de Windows para obtener más información acerca de cómo cambiar los valores predeterminados de la estructura.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]

##  <a name="setscrollpos"></a>  CScrollBar::SetScrollPos

Establece la posición actual de un cuadro de desplazamiento al especificado por *nPos* y, si se especifica, vuelve a dibujar la barra de desplazamiento para reflejar la nueva posición.

```
int SetScrollPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Especifica la nueva posición para el cuadro de desplazamiento. Debe estar dentro del intervalo de desplazamiento.

*bRedraw*<br/>
Especifica si se debe volver a dibujar la barra de desplazamiento para reflejar la nueva posición. Si *bRedraw* es TRUE, se vuelve a dibujar la barra de desplazamiento. Si es FALSE, no se actualiza. Se vuelve a dibujar la barra de desplazamiento de forma predeterminada.

### <a name="return-value"></a>Valor devuelto

Especifica la posición anterior del cuadro de desplazamiento si se realiza correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Establecer *bRedraw* en FALSE siempre que la barra de desplazamiento se volverá a dibujar una llamada posterior a otra función para evitar que vuelva a dibujar dos veces en un breve intervalo de la barra de desplazamiento.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CScrollBar::SetScrollRange](#setscrollrange).

##  <a name="setscrollrange"></a>  CScrollBar::SetScrollRange

Establece los valores de posición mínimo y máximo de la barra de desplazamiento especificada.

```
void SetScrollRange(
    int nMinPos,
    int nMaxPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parámetros

*nMinPos*<br/>
Especifica la posición de desplazamiento mínimo.

*nMaxPos*<br/>
Especifica el máximo de la posición de desplazamiento.

*bRedraw*<br/>
Especifica si se debe volver a dibujar la barra de desplazamiento para reflejar el cambio. Si *bRedraw* es TRUE, se vuelve a dibujar la barra de desplazamiento; si es FALSE, no se actualiza. Se vuelve a dibujar de forma predeterminada.

### <a name="remarks"></a>Comentarios

Establecer *nMinPos* y *nMaxPos* en 0 para ocultar las barras de desplazamiento estándar.

No llame a esta función para ocultar una barra de desplazamiento al procesar un mensaje de notificación de la barra de desplazamiento.

Si una llamada a `SetScrollRange` sigue inmediatamente a una llamada a la `SetScrollPos` función miembro, establezca *bRedraw* en `SetScrollPos` en 0 para evitar que la barra de desplazamiento que se va a dibujar dos veces.

La diferencia entre los valores especificados por *nMinPos* y *nMaxPos* no debe ser mayor que 32.767. El intervalo predeterminado para un control de barra de desplazamiento está vacío (ambos *nMinPos* y *nMaxPos* son 0).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]

##  <a name="showscrollbar"></a>  CScrollBar::ShowScrollBar

Muestra u oculta una barra de desplazamiento.

```
void ShowScrollBar(BOOL bShow = TRUE);
```

### <a name="parameters"></a>Parámetros

*bShow*<br/>
Especifica si se muestra o se oculta la barra de desplazamiento. Si este parámetro es TRUE, se muestra la barra de desplazamiento; en caso contrario, se oculta.

### <a name="remarks"></a>Comentarios

Una aplicación no debe llamar a esta función para ocultar una barra de desplazamiento al procesar un mensaje de notificación de la barra de desplazamiento.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CScrollBar::Create](#create).

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CButton (clase)](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox (clase)](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit (clase)](../../mfc/reference/cedit-class.md)<br/>
[CListBox (clase)](../../mfc/reference/clistbox-class.md)<br/>
[CStatic (clase)](../../mfc/reference/cstatic-class.md)<br/>
[CDialog (clase)](../../mfc/reference/cdialog-class.md)
