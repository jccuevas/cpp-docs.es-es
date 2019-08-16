---
title: Clase CPagerCtrl
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
ms.openlocfilehash: 519a376bdecc488a94eab65973e33d960ca50c8d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503028"
---
# <a name="cpagerctrl-class"></a>Clase CPagerCtrl

La clase `CPagerCtrl` ajusta el control de paginación de Windows, que puede desplazar en la vista una ventana contenida que no cabe en la ventana contenedora.

## <a name="syntax"></a>Sintaxis

```
class CPagerCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPagerCtrl::CPagerCtrl](#cpagerctrl)|Construye un objeto `CPagerCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPagerCtrl::Create](#create)|Crea un control de paginación con los estilos especificados y lo adjunta al `CPagerCtrl` objeto actual.|
|[CPagerCtrl::CreateEx](#createex)|Crea un control de paginación con los estilos extendidos especificados y lo adjunta `CPagerCtrl` al objeto actual.|
|[CPagerCtrl::ForwardMouse](#forwardmouse)|Habilita o deshabilita el reenvío de mensajes [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) a la ventana contenida en el control de paginación actual.|
|[CPagerCtrl::GetBkColor](#getbkcolor)|Recupera el color de fondo del control de paginación actual.|
|[CPagerCtrl::GetBorder](#getborder)|Recupera el tamaño del borde del control de paginación actual.|
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|Recupera el tamaño del botón del control de paginación actual.|
|[CPagerCtrl::GetButtonState](#getbuttonstate)|Recupera el estado del botón especificado en el control de paginación actual.|
|[CPagerCtrl::GetDropTarget](#getdroptarget)|Recupera la interfaz [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) para el control de paginación actual.|
|[CPagerCtrl::GetScrollPos](#getscrollpos)|Recupera la posición de desplazamiento del control de paginación actual.|
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|Indica si el botón especificado del control de paginación actual está en `pressed` estado.|
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|Indica si el botón especificado del control de paginación actual está en `grayed` estado.|
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|Indica si el botón especificado del control de paginación actual está en `hot` estado.|
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|Indica si el botón especificado del control de paginación actual está en `invisible` estado.|
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|Indica si el botón especificado del control de paginación actual está en `normal` estado.|
|[CPagerCtrl::RecalcSize](#recalcsize)|Hace que el control de paginación actual recalcule el tamaño de la ventana contenida.|
|[CPagerCtrl::SetBkColor](#setbkcolor)|Establece el color de fondo del control de paginación actual.|
|[CPagerCtrl::SetBorder](#setborder)|Establece el tamaño del borde del control de paginación actual.|
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|Establece el tamaño del botón del control de paginación actual.|
|[CPagerCtrl::SetChild](#setchild)|Establece la ventana contenida para el control de paginación actual.|
|[CPagerCtrl::SetScrollPos](#setscrollpos)|Establece la posición de desplazamiento del control de paginación actual.|

## <a name="remarks"></a>Comentarios

Un control de paginación es una ventana que contiene otra ventana que es lineal y más grande que la ventana contenedora y permite desplazar la ventana contenida en la vista. El control de paginación muestra dos botones de desplazamiento que desaparecen automáticamente cuando la ventana contenida se desplaza a su extensión más lejana y vuelven a aparecer. Puede crear un control de paginación que se desplace horizontal o verticalmente.

Por ejemplo, si la aplicación tiene una barra de herramientas que no es lo suficientemente ancha para mostrar todos sus elementos, puede asignar la barra de herramientas a un control de paginación y los usuarios podrán desplazarse por la barra de herramientas a la izquierda o a la derecha para tener acceso a todos los elementos. Microsoft Internet Explorer versión 4,0 (commctrl. dll versión 4,71) presenta el control de paginación.

La `CPagerCtrl` clase se deriva de la clase [CWnd](../../mfc/reference/cwnd-class.md) . Para obtener más información y una ilustración de un control de paginación, vea [controles](/windows/win32/Controls/pager-controls)de paginación.

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

Use el método [CPagerCtrl:: Create](#create) o [CPagerCtrl:: CreateEx](#createex) para crear un control de paginación y adjuntarlo `CPagerCtrl` al objeto.

##  <a name="create"></a>  CPagerCtrl::Create

Crea un control de paginación con los estilos especificados y lo adjunta al `CPagerCtrl` objeto actual.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*dwStyle*|de Combinación bit a bit (o) de estilos de [ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) y [estilos de control](/windows/win32/Controls/pager-control-styles) de paginación que se van a aplicar al control.|
|*rect*|de Referencia a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que contiene la posición y el tamaño del control en coordenadas de cliente.|
|*pParentWnd*|de Un puntero a un objeto [CWnd](../../mfc/reference/cwnd-class.md) que es la ventana primaria del control. Este parámetro no puede ser NULL.|
|*nID*|de IDENTIFICADOR del control.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Para crear un control de paginación, declare una `CPagerCtrl` variable y, a continuación, llame al método [CPagerCtrl:: Create](#create) o [CPagerCtrl:: CreateEx](#createex) en esa variable.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea un control de paginación y, a continuación, se usa el método [CPagerCtrl:: SetChild](#setchild) para asociar un control de botón muy largo con el control de paginación. A continuación, en el ejemplo se usa el método [CPagerCtrl:: SetButtonSize](#setbuttonsize) para establecer el alto del control de paginación en 20 píxeles y el método [CPagerCtrl:: SetBorder](#setborder) para establecer el grosor del borde en 1 píxel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="createex"></a>  CPagerCtrl::CreateEx

Crea un control de paginación con los estilos extendidos especificados y lo adjunta `CPagerCtrl` al objeto actual.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*dwExStyle*|de Combinación bit a bit de los estilos extendidos que se van a aplicar al control. Para obtener más información, vea el parámetro *dwExStyle* de la función [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) .|
|*dwStyle*|de Combinación bit a bit (o) de estilos de [ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) y [estilos de control](/windows/win32/Controls/pager-control-styles) de paginación que se van a aplicar al control.|
|*rect*|de Referencia a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que contiene la posición y el tamaño del control en coordenadas de cliente.|
|*pParentWnd*|de Un puntero a un objeto [CWnd](../../mfc/reference/cwnd-class.md) que es la ventana primaria del control. Este parámetro no puede ser NULL.|
|*nID*|de IDENTIFICADOR del control.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Para crear un control de paginación, declare una `CPagerCtrl` variable y, a continuación, llame al método [CPagerCtrl:: Create](#create) o [CPagerCtrl:: CreateEx](#createex) en esa variable.

##  <a name="forwardmouse"></a>  CPagerCtrl::ForwardMouse

Habilita o deshabilita el reenvío de mensajes [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) a la ventana contenida en el control de paginación actual.

```
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*bForward*|de TRUE para reenviar los mensajes del mouse o FALSE para no reenviar los mensajes del mouse.|

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PGM_FORWARDMOUSE](/windows/win32/Controls/pgm-forwardmouse) , que se describe en el Windows SDK.

##  <a name="getborder"></a>  CPagerCtrl::GetBorder

Recupera el tamaño del borde del control de paginación actual.

```
int GetBorder() const;
```

### <a name="return-value"></a>Valor devuelto

Tamaño actual del borde, medido en píxeles.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PGM_GETBORDER](/windows/win32/Controls/pgm-getborder) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa el método [CPagerCtrl:: GetBorder](#getborder) para recuperar el grosor del borde del control de paginación.

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

##  <a name="getbkcolor"></a>  CPagerCtrl::GetBkColor

Recupera el color de fondo del control de paginación actual.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de [COLORREF](/windows/win32/gdi/colorref) que contiene el color de fondo actual del control de paginación.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PGM_GETBKCOLOR](/windows/win32/Controls/pgm-getbkcolor) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa el método [CPagerCtrl:: SetBkColor](#setbkcolor) para establecer el color de fondo del control de paginación en rojo y el método [CPagerCtrl:: GetBkColor](#getbkcolor) para confirmar que se ha realizado el cambio.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="getbuttonsize"></a>  CPagerCtrl::GetButtonSize

Recupera el tamaño del botón del control de paginación actual.

```
int GetButtonSize() const;
```

### <a name="return-value"></a>Valor devuelto

Tamaño del botón actual, medido en píxeles.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PGM_GETBUTTONSIZE](/windows/win32/Controls/pgm-getbuttonsize) , que se describe en el Windows SDK.

Si el control de paginación tiene el estilo PGS_HORZ, el tamaño del botón determina el ancho de los botones de paginación y, si el control de paginación tiene el estilo PGS_VERT, el tamaño del botón determina el alto de los botones de paginación. Para obtener más información, vea [estilos de control](/windows/win32/Controls/pager-control-styles)de buscapersonas.

##  <a name="getbuttonstate"></a>  CPagerCtrl::GetButtonState

Recupera el estado del botón de desplazamiento especificado en el control de paginación actual.

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*iButton*|de Indica el botón para el que se recupera el estado. Si el estilo de control de paginación es PGS_HORZ, especifique PGB_TOPORLEFT para el botón primario y PGB_BOTTOMORRIGHT para el botón derecho. Si el estilo de control de paginación es PGS_VERT, especifique PGB_TOPORLEFT para el botón superior y PGB_BOTTOMORRIGHT para el botón inferior. Para obtener más información, vea [estilos de control](/windows/win32/Controls/pager-control-styles)de buscapersonas.|

### <a name="return-value"></a>Valor devuelto

Estado del botón especificado por el parámetro *iButton* . El estado es PGF_INVISIBLE, PGF_NORMAL, PGF_GRAYED, PGF_DEPRESSED o PGF_HOT. Para obtener más información, vea la sección valor devuelto del mensaje [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , que se describe en el Windows SDK.

##  <a name="getdroptarget"></a>  CPagerCtrl::GetDropTarget

Recupera la interfaz [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) para el control de paginación actual.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a la `IDropTarget` interfaz para el control de paginación actual.

### <a name="remarks"></a>Comentarios

`IDropTarget`es una de las interfaces que se implementan para admitir las operaciones de arrastrar y colocar en la aplicación.

Este método envía el mensaje [PGM_GETDROPTARGET](/windows/win32/Controls/pgm-getdroptarget) , que se describe en el Windows SDK. El autor de la llamada de este método es responsable de `Release` llamar al miembro de la interfaz [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) cuando ya no se necesita la interfaz.

##  <a name="getscrollpos"></a>  CPagerCtrl::GetScrollPos

Recupera la posición de desplazamiento del control de paginación actual.

```
int GetScrollPos() const;
```

### <a name="return-value"></a>Valor devuelto

Posición de desplazamiento actual, medida en píxeles.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PGM_GETPOS](/windows/win32/Controls/pgm-getpos) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa el método [CPagerCtrl:: GetScrollPos](#getscrollpos) para recuperar la posición de desplazamiento actual del control de paginación. Si el control de paginación todavía no se ha desplazado a cero, la posición más a la izquierda, en el ejemplo se usa el método [CPagerCtrl:: SetScrollPos](#setscrollpos) para establecer la posición de desplazamiento en cero.

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

##  <a name="isbuttondepressed"></a>  CPagerCtrl::IsButtonDepressed

Indica si el botón de desplazamiento especificado del control de paginación actual está en estado presionado.

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*iButton*|de Indica el botón para el que se recupera el estado. Si el estilo de control de paginación es PGS_HORZ, especifique PGB_TOPORLEFT para el botón primario y PGB_BOTTOMORRIGHT para el botón derecho. Si el estilo de control de paginación es PGS_VERT, especifique PGB_TOPORLEFT para el botón superior y PGB_BOTTOMORRIGHT para el botón inferior. Para obtener más información, vea [estilos de control](/windows/win32/Controls/pager-control-styles)de buscapersonas.|

### <a name="return-value"></a>Valor devuelto

TRUE si el botón especificado está en estado presionado; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , que se describe en el Windows SDK. A continuación, comprueba si el estado que se devuelve es PGF_DEPRESSED. Para obtener más información, vea la sección valor devuelto del mensaje [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

##  <a name="isbuttongrayed"></a>  CPagerCtrl::IsButtonGrayed

Indica si el botón de desplazamiento especificado del control de paginación actual está en estado atenuado.

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*iButton*|de Indica el botón para el que se recupera el estado. Si el estilo de control de paginación es PGS_HORZ, especifique PGB_TOPORLEFT para el botón primario y PGB_BOTTOMORRIGHT para el botón derecho. Si el estilo de control de paginación es PGS_VERT, especifique PGB_TOPORLEFT para el botón superior y PGB_BOTTOMORRIGHT para el botón inferior. Para obtener más información, vea [estilos de control](/windows/win32/Controls/pager-control-styles)de buscapersonas.|

### <a name="return-value"></a>Valor devuelto

TRUE si el botón especificado está atenuado; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , que se describe en el Windows SDK. A continuación, comprueba si el estado que se devuelve es PGF_GRAYED. Para obtener más información, vea la sección valor devuelto del mensaje [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

##  <a name="isbuttonhot"></a>  CPagerCtrl::IsButtonHot

Indica si el botón de desplazamiento especificado del control de paginación actual está en estado activo.

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*iButton*|de Indica el botón para el que se recupera el estado. Si el estilo de control de paginación es PGS_HORZ, especifique PGB_TOPORLEFT para el botón primario y PGB_BOTTOMORRIGHT para el botón derecho. Si el estilo de control de paginación es PGS_VERT, especifique PGB_TOPORLEFT para el botón superior y PGB_BOTTOMORRIGHT para el botón inferior. Para obtener más información, vea [estilos de control](/windows/win32/Controls/pager-control-styles)de buscapersonas.|

### <a name="return-value"></a>Valor devuelto

TRUE si el botón especificado está en estado activo; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , que se describe en el Windows SDK. A continuación, comprueba si el estado que se devuelve es PGF_HOT. Para obtener más información, vea la sección valor devuelto del mensaje [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

##  <a name="isbuttoninvisible"></a>  CPagerCtrl::IsButtonInvisible

Indica si el botón de desplazamiento especificado del control de paginación actual está en estado invisible.

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*iButton*|de Indica el botón para el que se recupera el estado. Si el estilo de control de paginación es PGS_HORZ, especifique PGB_TOPORLEFT para el botón primario y PGB_BOTTOMORRIGHT para el botón derecho. Si el estilo de control de paginación es PGS_VERT, especifique PGB_TOPORLEFT para el botón superior y PGB_BOTTOMORRIGHT para el botón inferior. Para obtener más información, vea [estilos de control](/windows/win32/Controls/pager-control-styles)de buscapersonas.|

### <a name="return-value"></a>Valor devuelto

TRUE si el botón especificado se encuentra en estado invisible; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Windows hace que el botón de desplazamiento en una dirección determinada sea invisible cuando la ventana contenida se desplaza hasta su extensión más lejana, ya que al hacer clic en el botón no se puede ver más la ventana contenida.

Este método envía el mensaje [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , que se describe en el Windows SDK. A continuación, comprueba si el estado que se devuelve es PGF_INVISIBLE. Para obtener más información, vea la sección valor devuelto del mensaje [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa el método [CPagerCtrl:: IsButtonInvisible](#isbuttoninvisible) para determinar si los botones de desplazamiento izquierdo y derecho del control de paginación están visibles.

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

##  <a name="isbuttonnormal"></a>  CPagerCtrl::IsButtonNormal

Indica si el botón de desplazamiento especificado del control de paginación actual está en estado normal.

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*iButton*|de Indica el botón para el que se recupera el estado. Si el estilo de control de paginación es PGS_HORZ, especifique PGB_TOPORLEFT para el botón primario y PGB_BOTTOMORRIGHT para el botón derecho. Si el estilo de control de paginación es PGS_VERT, especifique PGB_TOPORLEFT para el botón superior y PGB_BOTTOMORRIGHT para el botón inferior. Para obtener más información, vea [estilos de control](/windows/win32/Controls/pager-control-styles)de buscapersonas.|

### <a name="return-value"></a>Valor devuelto

TRUE si el botón especificado está en estado normal; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) , que se describe en el Windows SDK. A continuación, comprueba si el estado que se devuelve es PGF_NORMAL. Para obtener más información, vea la sección valor devuelto del mensaje [PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate) .

##  <a name="recalcsize"></a>  CPagerCtrl::RecalcSize

Hace que el control de paginación actual recalcule el tamaño de la ventana contenida.

```
void RecalcSize();
```

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PGM_RECALCSIZE](/windows/win32/Controls/pgm-recalcsize) , que se describe en el Windows SDK. Por consiguiente, el control de paginación envía la notificación [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) para obtener las dimensiones desplazables de la ventana contenida.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa el método [CPagerCtrl:: RecalcSize](#recalcsize) para solicitar al control de paginación actual que vuelva a calcular su tamaño.

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa la [reflexión de mensajes](../../mfc/tn062-message-reflection-for-windows-controls.md) para permitir que el control de paginación recalcule su propio tamaño en lugar de requerir el cuadro de diálogo primario del control para realizar el cálculo. En el ejemplo se deriva `MyPagerCtrl` la clase de la [clase CPagerCtrl](../../mfc/reference/cpagerctrl-class.md)y, a continuación, se usa un mapa de mensajes para `OnCalcsize` asociar la notificación [PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize) al controlador de notificación. En este ejemplo, el controlador de notificación establece el ancho y el alto del control de paginación en valores fijos.

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

##  <a name="setbkcolor"></a>  CPagerCtrl::SetBkColor

Establece el color de fondo del control de paginación actual.

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*clrBk*|de Valor de [COLORREF](/windows/win32/gdi/colorref) que contiene el nuevo color de fondo del control de paginación.|

### <a name="return-value"></a>Valor devuelto

Valor de [COLORREF](/windows/win32/gdi/colorref) que contiene el color de fondo anterior del control de paginación.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PGM_SETBKCOLOR](/windows/win32/Controls/pgm-setbkcolor) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa el método [CPagerCtrl:: SetBkColor](#setbkcolor) para establecer el color de fondo del control de paginación en rojo y el método [CPagerCtrl:: GetBkColor](#getbkcolor) para confirmar que se ha realizado el cambio.

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="setborder"></a>  CPagerCtrl::SetBorder

Establece el tamaño del borde del control de paginación actual.

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*iBorder*|de Nuevo tamaño del borde, medido en píxeles. Si el parámetro *iBorder* es negativo, el tamaño del borde se establece en cero.|

### <a name="return-value"></a>Valor devuelto

Tamaño del borde anterior, medido en píxeles.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PGM_SETBORDER](/windows/win32/Controls/pgm-setborder) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea un control de paginación y, a continuación, se usa el método [CPagerCtrl:: SetChild](#setchild) para asociar un control de botón muy largo con el control de paginación. A continuación, en el ejemplo se usa el método [CPagerCtrl:: SetButtonSize](#setbuttonsize) para establecer el alto del control de paginación en 20 píxeles y el método [CPagerCtrl:: SetBorder](#setborder) para establecer el grosor del borde en 1 píxel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setbuttonsize"></a>  CPagerCtrl::SetButtonSize

Establece el tamaño del botón del control de paginación actual.

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*iButtonSize*|de Nuevo tamaño del botón, medido en píxeles.|

### <a name="return-value"></a>Valor devuelto

Tamaño del botón anterior, medido en píxeles.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PGM_SETBUTTONSIZE](/windows/win32/Controls/pgm-setpos) , que se describe en el Windows SDK.

Si el control de paginación tiene el estilo PGS_HORZ, el tamaño del botón determina el ancho de los botones de paginación y, si el control de paginación tiene el estilo PGS_VERT, el tamaño del botón determina el alto de los botones de paginación. El tamaño predeterminado del botón es tres cuartos del ancho de la barra de desplazamiento y el tamaño mínimo del botón es de 12 píxeles. Para obtener más información, vea [estilos de control](/windows/win32/Controls/pager-control-styles)de buscapersonas.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea un control de paginación y, a continuación, se usa el método [CPagerCtrl:: SetChild](#setchild) para asociar un control de botón muy largo con el control de paginación. A continuación, en el ejemplo se usa el método [CPagerCtrl:: SetButtonSize](#setbuttonsize) para establecer el alto del control de paginación en 20 píxeles y el método [CPagerCtrl:: SetBorder](#setborder) para establecer el grosor del borde en 1 píxel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setchild"></a>  CPagerCtrl::SetChild

Establece la ventana contenida para el control de paginación actual.

```
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*hwndChild*|de Identificador de la ventana que se va a incluir.|

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PGM_SETCHILD](/windows/win32/Controls/pgm-setchild) , que se describe en el Windows SDK.

Este método no cambia el elemento primario de la ventana contenida; solo asigna un identificador de ventana al control de paginación para el desplazamiento. En la mayoría de los casos, la ventana contenida será una ventana secundaria del control de paginación.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea un control de paginación y, a continuación, se usa el método [CPagerCtrl:: SetChild](#setchild) para asociar un control de botón muy largo con el control de paginación. A continuación, en el ejemplo se usa el método [CPagerCtrl:: SetButtonSize](#setbuttonsize) para establecer el alto del control de paginación en 20 píxeles y el método [CPagerCtrl:: SetBorder](#setborder) para establecer el grosor del borde en 1 píxel.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setscrollpos"></a>  CPagerCtrl::SetScrollPos

Establece la posición de desplazamiento del control de paginación actual.

```
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*iPos*|de Nueva posición de desplazamiento, medida en píxeles.|

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [PGM_SETPOS](/windows/win32/Controls/pgm-setpos) , que se describe en el Windows SDK.

## <a name="see-also"></a>Vea también

[CPagerCtrl (clase)](../../mfc/reference/cpagerctrl-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Controles de paginación](/windows/win32/Controls/pager-controls)
