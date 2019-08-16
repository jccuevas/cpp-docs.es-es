---
title: Clase CScrollBar
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
ms.openlocfilehash: cd0c1ed85969d50548cf6b2be1d5677ed62110bc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502575"
---
# <a name="cscrollbar-class"></a>Clase CScrollBar

Proporciona la funcionalidad de un control de barra de desplazamiento de Windows.

## <a name="syntax"></a>Sintaxis

```
class CScrollBar : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CScrollBar::CScrollBar](#cscrollbar)|Construye un objeto `CScrollBar`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CScrollBar::Create](#create)|Crea la barra de desplazamiento de Windows y la `CScrollBar` adjunta al objeto.|
|[CScrollBar::EnableScrollBar](#enablescrollbar)|Habilita o deshabilita una o ambas flechas de una barra de desplazamiento.|
|[CScrollBar::GetScrollBarInfo](#getscrollbarinfo)|Recupera información sobre la barra de desplazamiento mediante una `SCROLLBARINFO` estructura.|
|[CScrollBar::GetScrollInfo](#getscrollinfo)|Recupera información sobre la barra de desplazamiento.|
|[CScrollBar::GetScrollLimit](#getscrolllimit)|Recupera el límite de la barra de desplazamiento.|
|[CScrollBar::GetScrollPos](#getscrollpos)|Recupera la posición actual de un cuadro de desplazamiento.|
|[CScrollBar::GetScrollRange](#getscrollrange)|Recupera las posiciones de barra de desplazamiento mínima y máxima actuales para la barra de desplazamiento especificada.|
|[CScrollBar::SetScrollInfo](#setscrollinfo)|Establece la información acerca de la barra de desplazamiento.|
|[CScrollBar::SetScrollPos](#setscrollpos)|Establece la posición actual de un cuadro de desplazamiento.|
|[CScrollBar::SetScrollRange](#setscrollrange)|Establece los valores de posición mínimo y máximo de la barra de desplazamiento especificada.|
|[CScrollBar::ShowScrollBar](#showscrollbar)|Muestra u oculta una barra de desplazamiento.|

## <a name="remarks"></a>Comentarios

Puede crear un control de barra de desplazamiento en dos pasos. En primer lugar, llame `CScrollBar` al constructor para `CScrollBar` construir el objeto y, a continuación, llame a la función miembro [Create](#create) para crear el control de `CScrollBar` barra de desplazamiento de Windows y adjuntarlo al objeto.

Si crea un `CScrollBar` objeto dentro de un cuadro de diálogo (a través de un recurso de `CScrollBar` cuadro de diálogo), se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.

Si crea un `CScrollBar` objeto dentro de una ventana, es posible que también tenga que destruirlo.

Si crea el `CScrollBar` objeto en la pila, se destruye automáticamente. Si crea el `CScrollBar` objeto en el montón mediante la **nueva** función, debe llamar a **Delete** en el objeto para destruirlo cuando el usuario finaliza la barra de desplazamiento de Windows.

Si asigna memoria en el `CScrollBar` objeto, invalide el `CScrollBar` destructor para desechar las asignaciones.

Para obtener información relacionada `CScrollBar`sobre el uso de, vea [controles](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CScrollBar`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="create"></a>  CScrollBar::Create

Crea la barra de desplazamiento de Windows y la `CScrollBar` adjunta al objeto.

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

*rect*<br/>
Especifica el tamaño y la posición de la barra de desplazamiento. Puede ser una `RECT` estructura o un `CRect` objeto.

*pParentWnd*<br/>
Especifica la ventana primaria de la barra de desplazamiento, `CDialog` normalmente un objeto. No debe ser NULL.

*nID*<br/>
IDENTIFICADOR de control de la barra de desplazamiento.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Un `CScrollBar` objeto se crea en dos pasos. En primer lugar, llame al constructor, que construye `CScrollBar` el objeto; a `Create`continuación, llame a, que crea e inicializa la barra de desplazamiento de Windows asociada y `CScrollBar` la adjunta al objeto.

Aplique los siguientes [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) en una barra de desplazamiento:

- WS_CHILD siempre

- WS_VISIBLE normalmente

- WS_DISABLED raramente

- WS_GROUP a controles de grupo

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CScrollBar#1](../../mfc/reference/codesnippet/cpp/cscrollbar-class_1.cpp)]

##  <a name="cscrollbar"></a>  CScrollBar::CScrollBar

Construye un objeto `CScrollBar`.

```
CScrollBar();
```

### <a name="remarks"></a>Comentarios

Después de construir el objeto, llame a `Create` la función miembro para crear e inicializar la barra de desplazamiento de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CScrollBar#2](../../mfc/reference/codesnippet/cpp/cscrollbar-class_2.h)]

##  <a name="enablescrollbar"></a>  CScrollBar::EnableScrollBar

Habilita o deshabilita una o ambas flechas de una barra de desplazamiento.

```
BOOL EnableScrollBar(UINT nArrowFlags = ESB_ENABLE_BOTH);
```

### <a name="parameters"></a>Parámetros

*nArrowFlags*<br/>
Especifica si las flechas de desplazamiento están habilitadas o deshabilitadas y qué flechas están habilitadas o deshabilitadas. Este parámetro puede ser uno de los siguientes valores:

- ESB_ENABLE_BOTH habilita ambas flechas de una barra de desplazamiento.

- ESB_DISABLE_LTUP deshabilita la flecha izquierda de una barra de desplazamiento horizontal o la flecha hacia arriba de una barra de desplazamiento vertical.

- ESB_DISABLE_RTDN deshabilita la flecha derecha de una barra de desplazamiento horizontal o la flecha hacia abajo de una barra de desplazamiento vertical.

- ESB_DISABLE_BOTH deshabilita ambas flechas de una barra de desplazamiento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si las flechas están habilitadas o deshabilitadas según lo especificado; de lo contrario, 0, que indica que las flechas ya están en el estado solicitado o que se ha producido un error.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CScrollBar:: SetScrollRange](#setscrollrange).

##  <a name="getscrollbarinfo"></a>  CScrollBar::GetScrollBarInfo

Recupera la información que la estructura `SCROLLBARINFO` mantiene sobre una barra de desplazamiento.

```
BOOL GetScrollBarInfo(PSCROLLBARINFO pScrollInfo) const;
```

### <a name="parameters"></a>Parámetros

*pScrollInfo*<br/>
Puntero a la estructura [SCROLLBARINFO](/windows/win32/api/winuser/ns-winuser-scrollbarinfo) .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad del mensaje [SBM_SCROLLBARINFO](/windows/win32/Controls/sbm-getscrollbarinfo) , tal y como se describe en el Windows SDK.

##  <a name="getscrollinfo"></a>  CScrollBar::GetScrollInfo

Recupera la información que la estructura `SCROLLINFO` mantiene sobre una barra de desplazamiento.

```
BOOL GetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    UINT nMask = SIF_ALL);
```

### <a name="parameters"></a>Parámetros

*lpScrollInfo*<br/>
Puntero a una estructura [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) . Vea el Windows SDK para obtener más información sobre esta estructura.

*nMask*<br/>
Especifica los parámetros de la barra de desplazamiento que se van a recuperar. Uso típico, SIF_ALL, especifica una combinación de SIF_PAGE, SIF_POS, SIF_TRACKPOS y SIF_RANGE. Vea `SCROLLINFO` para obtener más información sobre los valores de nMask.

### <a name="return-value"></a>Valor devuelto

Si el mensaje recupera algún valor, el valor devuelto es TRUE. De lo contrario, es FALSE.

### <a name="remarks"></a>Comentarios

`GetScrollInfo`permite a las aplicaciones usar las posiciones de desplazamiento de 32 bits.

La estructura [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) contiene información acerca de una barra de desplazamiento, incluidas las posiciones de desplazamiento mínima y máxima, el tamaño de página y la posición del cuadro de desplazamiento (el control de posición). Vea el `SCROLLINFO` tema sobre la estructura en el Windows SDK para obtener más información sobre cómo cambiar los valores predeterminados de la estructura.

Los controladores de mensajes de Windows de MFC que indican la posición de la barra de desplazamiento, [CWnd:: OnHScroll y [CWnd:: OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll), solo proporcionan 16 bits de datos de posición. `GetScrollInfo`y `SetScrollInfo` proporcionan 32 bits de datos de posición de la barra de desplazamiento. Por lo tanto, una aplicación `GetScrollInfo` puede llamar a `CWnd::OnHScroll` mientras `CWnd::OnVScroll` procesa o para obtener datos de posición de la barra de desplazamiento de 32 bits.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

##  <a name="getscrolllimit"></a>  CScrollBar::GetScrollLimit

Recupera la posición de desplazamiento máxima de la barra de desplazamiento.

```
int GetScrollLimit();
```

### <a name="return-value"></a>Valor devuelto

Especifica la posición máxima de una barra de desplazamiento si se realiza correctamente; de lo contrario, es 0.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

##  <a name="getscrollpos"></a>  CScrollBar::GetScrollPos

Recupera la posición actual de un cuadro de desplazamiento.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Valor devuelto

Especifica la posición actual del cuadro de desplazamiento si se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La posición actual es un valor relativo que depende del intervalo de desplazamiento actual. Por ejemplo, si el intervalo de desplazamiento es de 100 a 200 y el cuadro de desplazamiento está en el centro de la barra, la posición actual es 150.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

##  <a name="getscrollrange"></a>  CScrollBar::GetScrollRange

Copia las posiciones de barra de desplazamiento mínima y máxima actuales de la barra de desplazamiento dada en las ubicaciones especificadas por *lpMinPos* y *lpMaxPos*.

```
void GetScrollRange(
    LPINT lpMinPos,
    LPINT lpMaxPos) const;
```

### <a name="parameters"></a>Parámetros

*lpMinPos*<br/>
Apunta a la variable de entero que va a recibir la posición mínima.

*lpMaxPos*<br/>
Apunta a la variable de entero que va a recibir la posición máxima.

### <a name="remarks"></a>Comentarios

El intervalo predeterminado para un control de barra de desplazamiento está vacío (ambos valores son 0).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll).

##  <a name="setscrollinfo"></a>  CScrollBar::SetScrollInfo

Establece la información que mantiene `SCROLLINFO` la estructura sobre una barra de desplazamiento.

```
BOOL SetScrollInfo(
    LPSCROLLINFO lpScrollInfo,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpScrollInfo*<br/>
Puntero a una estructura [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) .

*bRedraw*<br/>
Especifica si la barra de desplazamiento debe volver a dibujarse para reflejar la nueva información. Si *bRedraw* es true, se vuelve a dibujar la barra de desplazamiento. Si es FALSE, no se vuelve a dibujar. De forma predeterminada, se vuelve a dibujar la barra de desplazamiento.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el valor devuelto es TRUE. De lo contrario, es FALSE.

### <a name="remarks"></a>Comentarios

Debe proporcionar los valores requeridos por los parámetros `SCROLLINFO` de la estructura, incluidos los valores de la marca.

La `SCROLLINFO` estructura contiene información acerca de una barra de desplazamiento, incluidas las posiciones de desplazamiento mínima y máxima, el tamaño de página y la posición del cuadro de desplazamiento (el control de posición). Vea el tema estructura de [SCROLLINFO](/windows/win32/api/winuser/ns-winuser-scrollinfo) en el Windows SDK para obtener más información sobre cómo cambiar los valores predeterminados de la estructura.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CScrollBar#3](../../mfc/reference/codesnippet/cpp/cscrollbar-class_3.cpp)]

##  <a name="setscrollpos"></a>  CScrollBar::SetScrollPos

Establece la posición actual de un cuadro de desplazamiento en el especificado por *NPOs* y, si se especifica, vuelve a dibujar la barra de desplazamiento para reflejar la nueva posición.

```
int SetScrollPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Especifica la nueva posición del cuadro de desplazamiento. Debe encontrarse dentro del intervalo de desplazamiento.

*bRedraw*<br/>
Especifica si la barra de desplazamiento debe volver a dibujarse para reflejar la nueva posición. Si *bRedraw* es true, se vuelve a dibujar la barra de desplazamiento. Si es FALSE, no se vuelve a dibujar. De forma predeterminada, se vuelve a dibujar la barra de desplazamiento.

### <a name="return-value"></a>Valor devuelto

Especifica la posición anterior del cuadro de desplazamiento si se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Establezca *bRedraw* en false siempre que la barra de desplazamiento se vuelva a dibujar mediante una llamada subsiguiente a otra función para evitar que la barra de desplazamiento se vuelva a dibujar dos veces dentro de un breve intervalo.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CScrollBar:: SetScrollRange](#setscrollrange).

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
Especifica la posición de desplazamiento mínima.

*nMaxPos*<br/>
Especifica la posición de desplazamiento máxima.

*bRedraw*<br/>
Especifica si la barra de desplazamiento debe volver a dibujarse para reflejar el cambio. Si *bRedraw* es true, se vuelve a dibujar la barra de desplazamiento. Si es FALSE, no se vuelve a dibujar. De forma predeterminada, se vuelve a dibujar.

### <a name="remarks"></a>Comentarios

Establezca *nMinPos* y *nMaxPos* en 0 para ocultar las barras de desplazamiento estándar.

No llame a esta función para ocultar una barra de desplazamiento mientras procesa un mensaje de notificación de la barra de desplazamiento.

Si una llamada a `SetScrollRange` sigue inmediatamente a una llamada a `SetScrollPos` la función miembro, establezca bRedraw `SetScrollPos` en en 0 para evitar que la barra de desplazamiento se vuelva a dibujar dos veces.

La diferencia entre los valores especificados por *nMinPos* y *nMaxPos* no debe ser mayor que 32.767. El intervalo predeterminado para un control de barra de desplazamiento está vacío ( *nMinPos* y *nMaxPos* son 0).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CScrollBar#4](../../mfc/reference/codesnippet/cpp/cscrollbar-class_4.cpp)]

##  <a name="showscrollbar"></a>  CScrollBar::ShowScrollBar

Muestra u oculta una barra de desplazamiento.

```
void ShowScrollBar(BOOL bShow = TRUE);
```

### <a name="parameters"></a>Parámetros

*bShow*<br/>
Especifica si se muestra u oculta la barra de desplazamiento. Si este parámetro es TRUE, se muestra la barra de desplazamiento. en caso contrario, está oculto.

### <a name="remarks"></a>Comentarios

Una aplicación no debe llamar a esta función para ocultar una barra de desplazamiento mientras se procesa un mensaje de notificación de la barra de desplazamiento.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CScrollBar:: Create](#create).

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
