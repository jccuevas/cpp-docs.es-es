---
title: CPagerCtrl (clase)
ms.date: 11/04/2016
f1_keywords:
- CPagerCtrl
- AFXCMN/CPagerCtrl
- AFXCMN/CPagerCtrl::CPagerCtrl
- AFXCMN/CPagerCtrl::Create
- AFXCMN/CPagerCtrl::CreateEx
- AFXCMN/CPagerCtrl::ForwardMouse
- AFXCMN/CPagerCtrl::GetBkColor
- AFXCMN/CPagerCtrl::GetBorder
- AFXCMN/CPagerCtrl::GetButtonSize
- AFXCMN/CPagerCtrl::GetButtonState
- AFXCMN/CPagerCtrl::GetDropTarget
- AFXCMN/CPagerCtrl::GetScrollPos
- AFXCMN/CPagerCtrl::IsButtonDepressed
- AFXCMN/CPagerCtrl::IsButtonGrayed
- AFXCMN/CPagerCtrl::IsButtonHot
- AFXCMN/CPagerCtrl::IsButtonInvisible
- AFXCMN/CPagerCtrl::IsButtonNormal
- AFXCMN/CPagerCtrl::RecalcSize
- AFXCMN/CPagerCtrl::SetBkColor
- AFXCMN/CPagerCtrl::SetBorder
- AFXCMN/CPagerCtrl::SetButtonSize
- AFXCMN/CPagerCtrl::SetChild
- AFXCMN/CPagerCtrl::SetScrollPos
helpviewer_keywords:
- CPagerCtrl [MFC], CPagerCtrl
- CPagerCtrl [MFC], Create
- CPagerCtrl [MFC], CreateEx
- CPagerCtrl [MFC], ForwardMouse
- CPagerCtrl [MFC], GetBkColor
- CPagerCtrl [MFC], GetBorder
- CPagerCtrl [MFC], GetButtonSize
- CPagerCtrl [MFC], GetButtonState
- CPagerCtrl [MFC], GetDropTarget
- CPagerCtrl [MFC], GetScrollPos
- CPagerCtrl [MFC], IsButtonDepressed
- CPagerCtrl [MFC], IsButtonGrayed
- CPagerCtrl [MFC], IsButtonHot
- CPagerCtrl [MFC], IsButtonInvisible
- CPagerCtrl [MFC], IsButtonNormal
- CPagerCtrl [MFC], RecalcSize
- CPagerCtrl [MFC], SetBkColor
- CPagerCtrl [MFC], SetBorder
- CPagerCtrl [MFC], SetButtonSize
- CPagerCtrl [MFC], SetChild
- CPagerCtrl [MFC], SetScrollPos
ms.assetid: 65ac58dd-4f5e-4b7e-b15c-e0d435a7e884
ms.openlocfilehash: c782d5761323129eccf7ee129d877128c400d93a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270727"
---
# <a name="cpagerctrl-class"></a>CPagerCtrl (clase)

La clase `CPagerCtrl` ajusta el control de paginación de Windows, que puede desplazar en la vista una ventana contenida que no cabe en la ventana contenedora.

## <a name="syntax"></a>Sintaxis

```
class CPagerCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CPagerCtrl::CPagerCtrl](#cpagerctrl)|Construye un objeto `CPagerCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CPagerCtrl::Create](#create)|Crea un control de paginación con los estilos especificados y lo asocia a la actual `CPagerCtrl` objeto.|
|[CPagerCtrl::CreateEx](#createex)|Crea un control de paginación con los estilos extendidos especificados y lo asocia a la actual `CPagerCtrl` objeto.|
|[CPagerCtrl::ForwardMouse](#forwardmouse)|Habilita o deshabilita el reenvío [WM_MOUSEMOVE](/windows/desktop/inputdev/wm-mousemove) mensajes a la ventana que se encuentra en el control de paginación actual.|
|[CPagerCtrl::GetBkColor](#getbkcolor)|Recupera el color de fondo del control de paginación actual.|
|[CPagerCtrl::GetBorder](#getborder)|Recupera el tamaño del borde del control de paginación actual.|
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|Recupera el tamaño de los botones de control de paginación actual.|
|[CPagerCtrl::GetButtonState](#getbuttonstate)|Recupera el estado del botón especificado en el control de paginación actual.|
|[CPagerCtrl::GetDropTarget](#getdroptarget)|Recupera el [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget) interfaz para el control de paginación actual.|
|[CPagerCtrl::GetScrollPos](#getscrollpos)|Recupera la posición de desplazamiento del control de paginación actual.|
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|Indica si el botón de control de paginación actual especificado está en `pressed` estado.|
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|Indica si el botón de control de paginación actual especificado está en `grayed` estado.|
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|Indica si el botón de control de paginación actual especificado está en `hot` estado.|
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|Indica si el botón de control de paginación actual especificado está en `invisible` estado.|
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|Indica si el botón de control de paginación actual especificado está en `normal` estado.|
|[CPagerCtrl::RecalcSize](#recalcsize)|Hace que el control de paginación actual volver a calcular el tamaño de la ventana contenida.|
|[CPagerCtrl::SetBkColor](#setbkcolor)|Establece el color de fondo del control de paginación actual.|
|[CPagerCtrl::SetBorder](#setborder)|Establece el tamaño del borde del control de paginación actual.|
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|Establece el tamaño de los botones de control de paginación actual.|
|[CPagerCtrl::SetChild](#setchild)|Establece la ventana de contenido para el control de paginación actual.|
|[CPagerCtrl::SetScrollPos](#setscrollpos)|Establece la posición de desplazamiento del control de paginación actual.|

## <a name="remarks"></a>Comentarios

Un control de paginación es una ventana que contiene otra ventana que es mayor que la ventana contenedora y lineal y permite desplazar la ventana contenida en la vista. El control de paginación muestra dos botones de desplazamiento que desaparecen automáticamente cuando se desplaza la ventana contenida en su alcance más alejada y vuelva a aparecer en caso contrario. Puede crear un control de paginación que se desplaza horizontalmente o verticalmente.

Por ejemplo, si la aplicación tiene una barra de herramientas que no es lo suficientemente ancha para mostrar todos sus elementos, puede asignar la barra de herramientas a un control de paginación y los usuarios podrán desplazarse la barra de herramientas a la izquierda o derecha para acceder a todos los elementos. Microsoft Internet Explorer versión 4.0 (versión commctrl.dll 4.71) introduce el control de paginación.

El `CPagerCtrl` clase se deriva el [CWnd](../../mfc/reference/cwnd-class.md) clase. Para obtener más información y ver una ilustración de un control de paginación, vea [controles de paginación](/windows/desktop/Controls/pager-controls).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPagerCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="cpagerctrl"></a>  CPagerCtrl::CPagerCtrl

Construye un objeto `CPagerCtrl`.

```
CPagerCtrl();
```

### <a name="remarks"></a>Comentarios

Use la [CPagerCtrl::Create](#create) o [CPagerCtrl::CreateEx](#createex) método para crear un control de paginación y adjuntarlo a la `CPagerCtrl` objeto.

##  <a name="create"></a>  CPagerCtrl::Create

Crea un control de paginación con los estilos especificados y lo asocia a la actual `CPagerCtrl` objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*dwStyle*|[in] Una combinación bit a bit (OR) de [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) y [estilos de control de paginación](/windows/desktop/Controls/pager-control-styles) aplicarse al control.|
|*rect*|[in] Una referencia a un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que contiene la posición y el tamaño del control, en coordenadas de cliente.|
|*pParentWnd*|[in] Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que es la ventana primaria del control. Este parámetro no puede ser NULL.|
|*nID*|[in] El identificador del control.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Para crear un control de paginación, declare un `CPagerCtrl` variable, a continuación, llame a la [CPagerCtrl::Create](#create) o [CPagerCtrl::CreateEx](#createex) método en esa variable.

### <a name="example"></a>Ejemplo

El ejemplo siguiente se crea un control de paginación, a continuación, usa el [CPagerCtrl::SetChild](#setchild) método para asociar un control de botón mucho con el control de paginación. El ejemplo se utiliza el [CPagerCtrl::SetButtonSize](#setbuttonsize) método para establecer el alto del control de paginación a 20 píxeles y el [CPagerCtrl::SetBorder](#setborder) método para establecer el grosor del borde en 1 píxel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="createex"></a>  CPagerCtrl::CreateEx

Crea un control de paginación con los estilos extendidos especificados y lo asocia a la actual `CPagerCtrl` objeto.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*dwExStyle*|[in] Una combinación bit a bit de los estilos extendidos para aplicarse al control. Para obtener más información, consulte el *dwExStyle* parámetro de la [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) función.|
|*dwStyle*|[in] Una combinación bit a bit (OR) de [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) y [estilos de control de paginación](/windows/desktop/Controls/pager-control-styles) aplicarse al control.|
|*rect*|[in] Una referencia a un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que contiene la posición y el tamaño del control, en coordenadas de cliente.|
|*pParentWnd*|[in] Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que es la ventana primaria del control. Este parámetro no puede ser NULL.|
|*nID*|[in] El identificador del control.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Para crear un control de paginación, declare un `CPagerCtrl` variable, a continuación, llame a la [CPagerCtrl::Create](#create) o [CPagerCtrl::CreateEx](#createex) método en esa variable.

##  <a name="forwardmouse"></a>  CPagerCtrl::ForwardMouse

Habilita o deshabilita el reenvío [WM_MOUSEMOVE](/windows/desktop/inputdev/wm-mousemove) mensajes a la ventana que se encuentra en el control de paginación actual.

```
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*bForward*|[in] True para los mensajes del mouse hacia delante o falso para que no reenvíen mensajes del mouse.|

### <a name="remarks"></a>Comentarios

Este método envía el [PGM_FORWARDMOUSE](/windows/desktop/Controls/pgm-forwardmouse) mensaje, que se describe en el SDK de Windows.

##  <a name="getborder"></a>  CPagerCtrl::GetBorder

Recupera el tamaño del borde del control de paginación actual.

```
int GetBorder() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño actual del borde, medido en píxeles.

### <a name="remarks"></a>Comentarios

Este método envía el [PGM_GETBORDER](/windows/desktop/Controls/pgm-getborder) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa el [CPagerCtrl::GetBorder](#getborder) método para recuperar el grosor del borde del control de paginación.

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

##  <a name="getbkcolor"></a>  CPagerCtrl::GetBkColor

Recupera el color de fondo del control de paginación actual.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valor devuelto

Un [COLORREF](/windows/desktop/gdi/colorref) valor que contiene el color de fondo actual del control de paginación.

### <a name="remarks"></a>Comentarios

Este método envía el [PGM_GETBKCOLOR](/windows/desktop/Controls/pgm-getbkcolor) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa el [CPagerCtrl::SetBkColor](#setbkcolor) método para establecer el color de fondo del control de paginación a rojo y el [CPagerCtrl::GetBkColor](#getbkcolor) método para confirmar que se realizó el cambio.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="getbuttonsize"></a>  CPagerCtrl::GetButtonSize

Recupera el tamaño de los botones de control de paginación actual.

```
int GetButtonSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño actual del botón, medido en píxeles.

### <a name="remarks"></a>Comentarios

Este método envía el [PGM_GETBUTTONSIZE](/windows/desktop/Controls/pgm-getbuttonsize) mensaje, que se describe en el SDK de Windows.

Si el control de paginación tiene el estilo PGS_HORZ, el tamaño del botón determina el ancho de los botones de paginación, y si el control de paginación tiene el estilo PGS_VERT, el tamaño del botón determina el alto de los botones de paginación. Para obtener más información, consulte [estilos de Control de paginación](/windows/desktop/Controls/pager-control-styles).

##  <a name="getbuttonstate"></a>  CPagerCtrl::GetButtonState

Recupera el estado del botón de desplazamiento especificada en el control de paginación actual.

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*iButton*|[in] Indica el botón que se recupera el estado. Si el estilo de control de paginación es PGS_HORZ, especifique PGB_TOPORLEFT para el botón primario y PGB_BOTTOMORRIGHT para el botón derecho. Si el estilo de control de paginación es PGS_VERT, especifique PGB_TOPORLEFT para el botón superior y PGB_BOTTOMORRIGHT para el botón de la parte inferior. Para obtener más información, consulte [estilos de Control de paginación](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Valor devuelto

El estado del botón especificado por el *iButton* parámetro. El estado es PGF_INVISIBLE, PGF_NORMAL, PGF_GRAYED, PGF_DEPRESSED o PGF_HOT. Para obtener más información, vea la sección de valor devuelto de la [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) mensaje.

### <a name="remarks"></a>Comentarios

Este método envía el [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) mensaje, que se describe en el SDK de Windows.

##  <a name="getdroptarget"></a>  CPagerCtrl::GetDropTarget

Recupera el [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget) interfaz para el control de paginación actual.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la `IDropTarget` interfaz para el control de paginación actual.

### <a name="remarks"></a>Comentarios

`IDropTarget` es una de las interfaces que implementar para admitir operaciones de arrastrar y colocar en la aplicación.

Este método envía el [PGM_GETDROPTARGET](/windows/desktop/Controls/pgm-getdroptarget) mensaje, que se describe en el SDK de Windows. El llamador de este método es responsable de llamar a la `Release` miembro de la [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget) cuando ya no se necesita la interfaz de la interfaz.

##  <a name="getscrollpos"></a>  CPagerCtrl::GetScrollPos

Recupera la posición de desplazamiento del control de paginación actual.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Valor devuelto

La posición de desplazamiento actual, medido en píxeles.

### <a name="remarks"></a>Comentarios

Este método envía el [PGM_GETPOS](/windows/desktop/Controls/pgm-getpos) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa el [CPagerCtrl::GetScrollPos](#getscrollpos) método para recuperar la posición de desplazamiento actual del control de paginación. Si el control de paginación no está ya se ha desplazado a cero, la posición de la izquierda, en el ejemplo se usa el [CPagerCtrl::SetScrollPos](#setscrollpos) método para establecer la posición de desplazamiento en cero.

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

##  <a name="isbuttondepressed"></a>  CPagerCtrl::IsButtonDepressed

Indica si el botón de desplazamiento especificada del control de paginación actual está en estado presionado.

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*iButton*|[in] Indica el botón que se recupera el estado. Si el estilo de control de paginación es PGS_HORZ, especifique PGB_TOPORLEFT para el botón primario y PGB_BOTTOMORRIGHT para el botón derecho. Si el estilo de control de paginación es PGS_VERT, especifique PGB_TOPORLEFT para el botón superior y PGB_BOTTOMORRIGHT para el botón de la parte inferior. Para obtener más información, consulte [estilos de Control de paginación](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Valor devuelto

TRUE si el botón especificado está en estado presionado; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) mensaje, que se describe en el SDK de Windows. A continuación, comprueba si el estado que se devuelve es PGF_DEPRESSED. Para obtener más información, vea la sección de valor devuelto de la [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) mensaje.

##  <a name="isbuttongrayed"></a>  CPagerCtrl::IsButtonGrayed

Indica si el botón de desplazamiento especificada del control de paginación actual está en estado atenuado.

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*iButton*|[in] Indica el botón que se recupera el estado. Si el estilo de control de paginación es PGS_HORZ, especifique PGB_TOPORLEFT para el botón primario y PGB_BOTTOMORRIGHT para el botón derecho. Si el estilo de control de paginación es PGS_VERT, especifique PGB_TOPORLEFT para el botón superior y PGB_BOTTOMORRIGHT para el botón de la parte inferior. Para obtener más información, consulte [estilos de Control de paginación](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Valor devuelto

TRUE si el botón especificado está en estado atenuado; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) mensaje, que se describe en el SDK de Windows. A continuación, comprueba si el estado que se devuelve es PGF_GRAYED. Para obtener más información, vea la sección de valor devuelto de la [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) mensaje.

##  <a name="isbuttonhot"></a>  CPagerCtrl::IsButtonHot

Indica si el botón de desplazamiento especificada del control de paginación actual está en estado activo.

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*iButton*|[in] Indica el botón que se recupera el estado. Si el estilo de control de paginación es PGS_HORZ, especifique PGB_TOPORLEFT para el botón primario y PGB_BOTTOMORRIGHT para el botón derecho. Si el estilo de control de paginación es PGS_VERT, especifique PGB_TOPORLEFT para el botón superior y PGB_BOTTOMORRIGHT para el botón de la parte inferior. Para obtener más información, consulte [estilos de Control de paginación](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Valor devuelto

TRUE si el botón especificado está en estado activo; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) mensaje, que se describe en el SDK de Windows. A continuación, comprueba si el estado que se devuelve es PGF_HOT. Para obtener más información, vea la sección de valor devuelto de la [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) mensaje.

##  <a name="isbuttoninvisible"></a>  CPagerCtrl::IsButtonInvisible

Indica si el botón de desplazamiento especificada del control de paginación actual está en estado invisible.

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*iButton*|[in] Indica el botón que se recupera el estado. Si el estilo de control de paginación es PGS_HORZ, especifique PGB_TOPORLEFT para el botón primario y PGB_BOTTOMORRIGHT para el botón derecho. Si el estilo de control de paginación es PGS_VERT, especifique PGB_TOPORLEFT para el botón superior y PGB_BOTTOMORRIGHT para el botón de la parte inferior. Para obtener más información, consulte [estilos de Control de paginación](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Valor devuelto

TRUE si el botón especificado está en estado invisible; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Windows hace que el botón de desplazamiento en una dirección determinada sea invisible cuando se desplaza la ventana contenida en su alcance más alejada porque al hacer clic en el botón más no puede poner más de la ventana contenida en la vista.

Este método envía el [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) mensaje, que se describe en el SDK de Windows. A continuación, comprueba si el estado que se devuelve es PGF_INVISIBLE. Para obtener más información, vea la sección de valor devuelto de la [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) mensaje.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa el [CPagerCtrl::IsButtonInvisible](#isbuttoninvisible) método para determinar si el control de paginación de la izquierda y los botones de desplazamiento a la derecha están visibles.

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

##  <a name="isbuttonnormal"></a>  CPagerCtrl::IsButtonNormal

Indica si el botón de desplazamiento especificada del control de paginación actual está en estado normal.

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*iButton*|[in] Indica el botón que se recupera el estado. Si el estilo de control de paginación es PGS_HORZ, especifique PGB_TOPORLEFT para el botón primario y PGB_BOTTOMORRIGHT para el botón derecho. Si el estilo de control de paginación es PGS_VERT, especifique PGB_TOPORLEFT para el botón superior y PGB_BOTTOMORRIGHT para el botón de la parte inferior. Para obtener más información, consulte [estilos de Control de paginación](/windows/desktop/Controls/pager-control-styles).|

### <a name="return-value"></a>Valor devuelto

TRUE si el botón especificado está en estado normal; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) mensaje, que se describe en el SDK de Windows. A continuación, comprueba si el estado que se devuelve es PGF_NORMAL. Para obtener más información, vea la sección de valor devuelto de la [PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate) mensaje.

##  <a name="recalcsize"></a>  CPagerCtrl::RecalcSize

Hace que el control de paginación actual volver a calcular el tamaño de la ventana contenida.

```
void RecalcSize();
```

### <a name="remarks"></a>Comentarios

Este método envía el [PGM_RECALCSIZE](/windows/desktop/Controls/pgm-recalcsize) mensaje, que se describe en el SDK de Windows. Por lo tanto, se envía el control de paginación la [PGN_CALCSIZE](/windows/desktop/Controls/pgn-calcsize) notificación para obtener las dimensiones de la ventana de contenido desplazables.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa el [CPagerCtrl::RecalcSize](#recalcsize) método para solicitar el control de paginación actual para volver a calcular su tamaño.

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa [reflexión de mensajes](../../mfc/tn062-message-reflection-for-windows-controls.md) para habilitar el control de paginación volver a calcular su propio tamaño en lugar de requerir el cuadro de diálogo del control primario para realizar el cálculo. El ejemplo se deriva el `MyPagerCtrl` clase desde el [CPagerCtrl (clase)](../../mfc/reference/cpagerctrl-class.md), a continuación, usa un mapa de mensajes para asociar el [PGN_CALCSIZE](/windows/desktop/Controls/pgn-calcsize) notificación con el `OnCalcsize` controlador de notificación. En este ejemplo, el controlador de notificación establece el ancho y alto del control de paginación en valores fijos.

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

##  <a name="setbkcolor"></a>  CPagerCtrl::SetBkColor

Establece el color de fondo del control de paginación actual.

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*clrBk*|[in] Un [COLORREF](/windows/desktop/gdi/colorref) valor que contiene el nuevo color de fondo del control de paginación.|

### <a name="return-value"></a>Valor devuelto

Un [COLORREF](/windows/desktop/gdi/colorref) valor que contiene el color de fondo anterior del control de paginación.

### <a name="remarks"></a>Comentarios

Este método envía el [PGM_SETBKCOLOR](/windows/desktop/Controls/pgm-setbkcolor) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa el [CPagerCtrl::SetBkColor](#setbkcolor) método para establecer el color de fondo del control de paginación a rojo y el [CPagerCtrl::GetBkColor](#getbkcolor) método para confirmar que se realizó el cambio.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="setborder"></a>  CPagerCtrl::SetBorder

Establece el tamaño del borde del control de paginación actual.

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*iBorder*|[in] El nuevo tamaño del borde, medido en píxeles. Si el *iBorder* parámetro es negativo, el tamaño del borde se establece en cero.|

### <a name="return-value"></a>Valor devuelto

El tamaño del borde anterior, medido en píxeles.

### <a name="remarks"></a>Comentarios

Este método envía el [PGM_SETBORDER](/windows/desktop/Controls/pgm-setborder) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El ejemplo siguiente se crea un control de paginación, a continuación, usa el [CPagerCtrl::SetChild](#setchild) método para asociar un control de botón mucho con el control de paginación. El ejemplo se utiliza el [CPagerCtrl::SetButtonSize](#setbuttonsize) método para establecer el alto del control de paginación a 20 píxeles y el [CPagerCtrl::SetBorder](#setborder) método para establecer el grosor del borde en 1 píxel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setbuttonsize"></a>  CPagerCtrl::SetButtonSize

Establece el tamaño de los botones de control de paginación actual.

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*iButtonSize*|[in] El nuevo tamaño de botón, medido en píxeles.|

### <a name="return-value"></a>Valor devuelto

El tamaño del botón anterior, medido en píxeles.

### <a name="remarks"></a>Comentarios

Este método envía el [PGM_SETBUTTONSIZE](/windows/desktop/Controls/pgm-setpos) mensaje, que se describe en el SDK de Windows.

Si el control de paginación tiene el estilo PGS_HORZ, el tamaño del botón determina el ancho de los botones de paginación, y si el control de paginación tiene el estilo PGS_VERT, el tamaño del botón determina el alto de los botones de paginación. El tamaño del botón predeterminado es tres cuartas partes del ancho de la barra de desplazamiento y el tamaño de botón mínimo es de 12 píxeles. Para obtener más información, consulte [estilos de Control de paginación](/windows/desktop/Controls/pager-control-styles).

### <a name="example"></a>Ejemplo

El ejemplo siguiente se crea un control de paginación, a continuación, usa el [CPagerCtrl::SetChild](#setchild) método para asociar un control de botón mucho con el control de paginación. El ejemplo se utiliza el [CPagerCtrl::SetButtonSize](#setbuttonsize) método para establecer el alto del control de paginación a 20 píxeles y el [CPagerCtrl::SetBorder](#setborder) método para establecer el grosor del borde en 1 píxel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setchild"></a>  CPagerCtrl::SetChild

Establece la ventana de contenido para el control de paginación actual.

```
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*hwndChild*|[in] Identificador de la ventana que se debe incluir.|

### <a name="remarks"></a>Comentarios

Este método envía el [PGM_SETCHILD](/windows/desktop/Controls/pgm-setchild) mensaje, que se describe en el SDK de Windows.

Este método no cambia al elemento primario de la ventana independiente; solo se asigna un identificador de ventana para el control de paginación para el desplazamiento. En la mayoría de los casos, la ventana contenida será una ventana secundaria de control de paginación.

### <a name="example"></a>Ejemplo

El ejemplo siguiente se crea un control de paginación, a continuación, usa el [CPagerCtrl::SetChild](#setchild) método para asociar un control de botón mucho con el control de paginación. El ejemplo se utiliza el [CPagerCtrl::SetButtonSize](#setbuttonsize) método para establecer el alto del control de paginación a 20 píxeles y el [CPagerCtrl::SetBorder](#setborder) método para establecer el grosor del borde en 1 píxel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setscrollpos"></a>  CPagerCtrl::SetScrollPos

Establece la posición de desplazamiento del control de paginación actual.

```
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*iPos*|[in] La nueva posición de desplazamiento, medido en píxeles.|

### <a name="remarks"></a>Comentarios

Este método envía el [PGM_SETPOS](/windows/desktop/Controls/pgm-setpos) mensaje, que se describe en el SDK de Windows.

## <a name="see-also"></a>Vea también

[CPagerCtrl (clase)](../../mfc/reference/cpagerctrl-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Controles de paginación](/windows/desktop/Controls/pager-controls)
