---
title: CReBarCtrl (clase)
ms.date: 11/19/2018
f1_keywords:
- CReBarCtrl
- AFXCMN/CReBarCtrl
- AFXCMN/CReBarCtrl::CReBarCtrl
- AFXCMN/CReBarCtrl::BeginDrag
- AFXCMN/CReBarCtrl::Create
- AFXCMN/CReBarCtrl::CreateEx
- AFXCMN/CReBarCtrl::DeleteBand
- AFXCMN/CReBarCtrl::DragMove
- AFXCMN/CReBarCtrl::EndDrag
- AFXCMN/CReBarCtrl::GetBandBorders
- AFXCMN/CReBarCtrl::GetBandCount
- AFXCMN/CReBarCtrl::GetBandInfo
- AFXCMN/CReBarCtrl::GetBandMargins
- AFXCMN/CReBarCtrl::GetBarHeight
- AFXCMN/CReBarCtrl::GetBarInfo
- AFXCMN/CReBarCtrl::GetBkColor
- AFXCMN/CReBarCtrl::GetColorScheme
- AFXCMN/CReBarCtrl::GetDropTarget
- AFXCMN/CReBarCtrl::GetExtendedStyle
- AFXCMN/CReBarCtrl::GetImageList
- AFXCMN/CReBarCtrl::GetPalette
- AFXCMN/CReBarCtrl::GetRect
- AFXCMN/CReBarCtrl::GetRowCount
- AFXCMN/CReBarCtrl::GetRowHeight
- AFXCMN/CReBarCtrl::GetTextColor
- AFXCMN/CReBarCtrl::GetToolTips
- AFXCMN/CReBarCtrl::HitTest
- AFXCMN/CReBarCtrl::IDToIndex
- AFXCMN/CReBarCtrl::InsertBand
- AFXCMN/CReBarCtrl::MaximizeBand
- AFXCMN/CReBarCtrl::MinimizeBand
- AFXCMN/CReBarCtrl::MoveBand
- AFXCMN/CReBarCtrl::PushChevron
- AFXCMN/CReBarCtrl::RestoreBand
- AFXCMN/CReBarCtrl::SetBandInfo
- AFXCMN/CReBarCtrl::SetBandWidth
- AFXCMN/CReBarCtrl::SetBarInfo
- AFXCMN/CReBarCtrl::SetBkColor
- AFXCMN/CReBarCtrl::SetColorScheme
- AFXCMN/CReBarCtrl::SetExtendedStyle
- AFXCMN/CReBarCtrl::SetImageList
- AFXCMN/CReBarCtrl::SetOwner
- AFXCMN/CReBarCtrl::SetPalette
- AFXCMN/CReBarCtrl::SetTextColor
- AFXCMN/CReBarCtrl::SetToolTips
- AFXCMN/CReBarCtrl::SetWindowTheme
- AFXCMN/CReBarCtrl::ShowBand
- AFXCMN/CReBarCtrl::SizeToRect
helpviewer_keywords:
- CReBarCtrl [MFC], CReBarCtrl
- CReBarCtrl [MFC], BeginDrag
- CReBarCtrl [MFC], Create
- CReBarCtrl [MFC], CreateEx
- CReBarCtrl [MFC], DeleteBand
- CReBarCtrl [MFC], DragMove
- CReBarCtrl [MFC], EndDrag
- CReBarCtrl [MFC], GetBandBorders
- CReBarCtrl [MFC], GetBandCount
- CReBarCtrl [MFC], GetBandInfo
- CReBarCtrl [MFC], GetBandMargins
- CReBarCtrl [MFC], GetBarHeight
- CReBarCtrl [MFC], GetBarInfo
- CReBarCtrl [MFC], GetBkColor
- CReBarCtrl [MFC], GetColorScheme
- CReBarCtrl [MFC], GetDropTarget
- CReBarCtrl [MFC], GetExtendedStyle
- CReBarCtrl [MFC], GetImageList
- CReBarCtrl [MFC], GetPalette
- CReBarCtrl [MFC], GetRect
- CReBarCtrl [MFC], GetRowCount
- CReBarCtrl [MFC], GetRowHeight
- CReBarCtrl [MFC], GetTextColor
- CReBarCtrl [MFC], GetToolTips
- CReBarCtrl [MFC], HitTest
- CReBarCtrl [MFC], IDToIndex
- CReBarCtrl [MFC], InsertBand
- CReBarCtrl [MFC], MaximizeBand
- CReBarCtrl [MFC], MinimizeBand
- CReBarCtrl [MFC], MoveBand
- CReBarCtrl [MFC], PushChevron
- CReBarCtrl [MFC], RestoreBand
- CReBarCtrl [MFC], SetBandInfo
- CReBarCtrl [MFC], SetBandWidth
- CReBarCtrl [MFC], SetBarInfo
- CReBarCtrl [MFC], SetBkColor
- CReBarCtrl [MFC], SetColorScheme
- CReBarCtrl [MFC], SetExtendedStyle
- CReBarCtrl [MFC], SetImageList
- CReBarCtrl [MFC], SetOwner
- CReBarCtrl [MFC], SetPalette
- CReBarCtrl [MFC], SetTextColor
- CReBarCtrl [MFC], SetToolTips
- CReBarCtrl [MFC], SetWindowTheme
- CReBarCtrl [MFC], ShowBand
- CReBarCtrl [MFC], SizeToRect
ms.assetid: 154570d7-e48c-425d-8c7e-c64542bcb4cc
ms.openlocfilehash: 102c06879ffaedb91f20a4b5085a10015d7a4c8b
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916867"
---
# <a name="crebarctrl-class"></a>CReBarCtrl (clase)

Encapsula la funcionalidad de un control rebar, que es un contenedor para una ventana secundaria.

## <a name="syntax"></a>Sintaxis

```
class CReBarCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CReBarCtrl::CReBarCtrl](#crebarctrl)|Construye un objeto `CReBarCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CReBarCtrl::BeginDrag](#begindrag)|Coloca el control rebar en el modo de arrastrar y colocar.|
|[CReBarCtrl::Create](#create)|Crea el control rebar y lo adjunta al `CReBarCtrl` objeto.|
|[CReBarCtrl::CreateEx](#createex)|Crea un control rebar con los estilos extendidos de Windows especificados y lo adjunta `CReBarCtrl` a un objeto.|
|[CReBarCtrl::DeleteBand](#deleteband)|Elimina una banda de un control rebar.|
|[CReBarCtrl::DragMove](#dragmove)|Actualiza la posición de arrastre en el control rebar después de una `BeginDrag`llamada a.|
|[CReBarCtrl::EndDrag](#enddrag)|Finaliza la operación de arrastrar y colocar del control rebar.|
|[CReBarCtrl::GetBandBorders](#getbandborders)|Recupera los bordes de una banda.|
|[CReBarCtrl::GetBandCount](#getbandcount)|Recupera el recuento de bandas actualmente en el control rebar.|
|[CReBarCtrl::GetBandInfo](#getbandinfo)|Recupera información sobre una banda especificada en un control rebar.|
|[CReBarCtrl::GetBandMargins](#getbandmargins)|Recupera los márgenes de una banda.|
|[CReBarCtrl::GetBarHeight](#getbarheight)|Recupera el alto del control rebar.|
|[CReBarCtrl::GetBarInfo](#getbarinfo)|Recupera información sobre el control rebar y la lista de imágenes que utiliza.|
|[CReBarCtrl::GetBkColor](#getbkcolor)|Recupera el color de fondo predeterminado de un control rebar.|
|[CReBarCtrl::GetColorScheme](#getcolorscheme)|Recupera la estructura [COLORSCHEME](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme) asociada al control rebar.|
|[CReBarCtrl::GetDropTarget](#getdroptarget)|Recupera el puntero de interfaz del `IDropTarget` control rebar.|
|[CReBarCtrl::GetExtendedStyle](#getextendedstyle)|Obtiene el estilo extendido del control rebar actual.|
|[CReBarCtrl::GetImageList](#getimagelist)|Recupera la lista de imágenes asociada a un control rebar.|
|[CReBarCtrl::GetPalette](#getpalette)|Recupera la paleta actual del control rebar.|
|[CReBarCtrl::GetRect](#getrect)|Recupera el rectángulo delimitador de una banda determinada en un control rebar.|
|[CReBarCtrl::GetRowCount](#getrowcount)|Recupera el número de filas de banda en un control rebar.|
|[CReBarCtrl::GetRowHeight](#getrowheight)|Recupera el alto de una fila especificada en un control rebar.|
|[CReBarCtrl::GetTextColor](#gettextcolor)|Recupera el color de texto predeterminado del control rebar.|
|[CReBarCtrl::GetToolTips](#gettooltips)|Recupera el identificador de cualquier control de información sobre herramientas asociado al control rebar.|
|[CReBarCtrl::HitTest](#hittest)|Determina qué parte de una banda rebar se encuentra en un punto determinado de la pantalla, si existe una banda rebar en ese punto.|
|[CReBarCtrl::IDToIndex](#idtoindex)|Convierte un identificador de banda (ID) en un índice de banda en un control rebar.|
|[CReBarCtrl::InsertBand](#insertband)|Inserta una nueva banda en un control rebar.|
|[CReBarCtrl::MaximizeBand](#maximizeband)|Cambia el tamaño de una banda de un control rebar a su tamaño más grande.|
|[CReBarCtrl::MinimizeBand](#minimizeband)|Cambia el tamaño de una banda de un control rebar a su tamaño más pequeño.|
|[CReBarCtrl::MoveBand](#moveband)|Mueve una banda de un índice a otro.|
|[CReBarCtrl::PushChevron](#pushchevron)|Envía mediante programación un botón de contenido adicional.|
|[CReBarCtrl::RestoreBand](#restoreband)|Cambia el tamaño de una banda de un control rebar a su tamaño ideal.|
|[CReBarCtrl::SetBandInfo](#setbandinfo)|Establece las características de una banda existente en un control rebar.|
|[CReBarCtrl::SetBandWidth](#setbandwidth)|Establece el ancho de la banda acoplada especificada en el control rebar actual.|
|[CReBarCtrl::SetBarInfo](#setbarinfo)|Establece las características de un control rebar.|
|[CReBarCtrl::SetBkColor](#setbkcolor)|Establece el color de fondo predeterminado del control rebar.|
|[CReBarCtrl::SetColorScheme](#setcolorscheme)|Establece la combinación de colores de los botones en un control rebar.|
|[CReBarCtrl::SetExtendedStyle](#setextendedstyle)|Establece los estilos extendidos para el control rebar actual.|
|[CReBarCtrl::SetImageList](#setimagelist)|Establece una lista de imágenes del control rebar.|
|[CReBarCtrl::SetOwner](#setowner)|Establece la ventana propietaria del control rebar.|
|[CReBarCtrl::SetPalette](#setpalette)|Establece la paleta actual del control rebar.|
|[CReBarCtrl::SetTextColor](#settextcolor)|Establece el color de texto predeterminado del control rebar.|
|[CReBarCtrl::SetToolTips](#settooltips)|Asocia un control de información sobre herramientas al control rebar.|
|[CReBarCtrl::SetWindowTheme](#setwindowtheme)|Establece el estilo visual del control rebar.|
|[CReBarCtrl::ShowBand](#showband)|Muestra u oculta una banda determinada en un control rebar.|
|[CReBarCtrl::SizeToRect](#sizetorect)|Ajusta un control rebar a un rectángulo especificado.|

## <a name="remarks"></a>Comentarios

La aplicación en la que reside el control rebar asigna la ventana secundaria que contiene el control rebar a la banda rebar. La ventana secundaria suele ser otro control común.

Los controles rebar contienen una o más bandas. Cada banda puede contener una combinación de una barra de agarre, un mapa de bits, una etiqueta de texto y una ventana secundaria. La banda solo puede contener uno de cada uno de estos elementos.

El control rebar puede mostrar la ventana secundaria sobre un mapa de bits de fondo especificado. Se puede cambiar el tamaño de todas las bandas de control rebar, excepto las que usan el estilo RBBS_FIXEDSIZE. A medida que cambia la posición o el tamaño de una banda de control rebar, el control rebar administra el tamaño y la posición de la ventana secundaria asignada a esa banda. Para cambiar el tamaño o el orden de las bandas dentro del control, haga clic y arrastre la barra de redimensionamiento de una banda.

En la ilustración siguiente se muestra un control rebar con tres bandas:

- La banda 0 contiene un control de barra de herramientas plana y transparente.

- La banda 1 contiene botones desplegables estándar transparente y transparente.

- La banda 2 contiene un cuadro combinado y cuatro botones estándar.

   ![Ejemplo de un menú rebar] (../../mfc/reference/media/vc4scc1.gif "Ejemplo de un menú rebar")

## <a name="rebar-control"></a>Rebar (control)

Compatibilidad con controles rebar:

- Listas de imágenes.

- Control de mensajes.

- Funcionalidad de dibujo personalizado.

- Diversos estilos de control además de los estilos de ventana estándar. Para obtener una lista de estos estilos, vea los [estilos de control rebar](/windows/desktop/Controls/rebar-control-styles) en el Windows SDK.

Para obtener más información, vea [usar CReBarCtrl](../../mfc/using-crebarctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CReBarCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="begindrag"></a>  CReBarCtrl::BeginDrag

Implementa el comportamiento del mensaje de Win32 [RB_BEGINDRAG](/windows/desktop/Controls/rb-begindrag), tal y como se describe en el Windows SDK.

```
void BeginDrag(
    UINT uBand,
    DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
Índice de base cero de la banda a la que afectará la operación de arrastrar y colocar.

*dwPos*<br/>
Valor DWORD que contiene las coordenadas del mouse de inicio. La coordenada horizontal está contenida en el LOWORD y la coordenada vertical está contenida en el HIWORD. Si pasa (DWORD)-1, el control rebar usará la posición del mouse la última vez que el subproceso del control llamó a `GetMessage` o `PeekMessage`.

##  <a name="create"></a>  CReBarCtrl::Create

Crea el control rebar y lo adjunta al `CReBarCtrl` objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica la combinación de estilos de control rebar aplicada al control. Vea los [estilos de control rebar](/windows/desktop/Controls/rebar-control-styles) en el Windows SDK para obtener una lista de los estilos admitidos.

*rect*<br/>
Referencia a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) o una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) , que es la posición y el tamaño del control rebar.

*pParentWnd*<br/>
Un puntero a un objeto [CWnd](../../mfc/reference/cwnd-class.md) que es la ventana primaria del control rebar. No debe ser NULL.

*nID*<br/>
Especifica el identificador de control del control rebar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto se creó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Cree un control rebar en dos pasos:

1. Llame a [CReBarCtrl](#crebarctrl) para construir `CReBarCtrl` un objeto.

1. Llame a esta función miembro, que crea el control rebar de Windows y lo adjunta al `CReBarCtrl` objeto.

Cuando se llama `Create`a, se inicializan los controles comunes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]

##  <a name="createex"></a>CReBarCtrl:: CreateEx

Crea un control (una ventana secundaria) y lo asocia al `CReBarCtrl` objeto.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwExStyle*<br/>
Especifica el estilo extendido del control que se va a crear. Para obtener una lista de los estilos extendidos de Windows, consulte el parámetro *dwExStyle* para [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) en el Windows SDK.

*dwStyle*<br/>
Especifica la combinación de estilos de control rebar aplicada al control. Para obtener una lista de los estilos admitidos, vea los [estilos de control rebar](/windows/desktop/Controls/rebar-control-styles) en el Windows SDK.

*rect*<br/>
Referencia a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que describe el tamaño y la posición de la ventana que se va a crear, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*nID*<br/>
IDENTIFICADOR de la ventana de elemento secundario del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Use `CreateEx` en lugar de [crear](#create) para aplicar los estilos extendidos de Windows, que especifica el **WS_EX_** de estilo extendido de Windows.

##  <a name="crebarctrl"></a>  CReBarCtrl::CReBarCtrl

Crea un objeto `CReBarCtrl`.

```
CReBarCtrl();
```

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CReBarCtrl:: Create](#create).

##  <a name="deleteband"></a>  CReBarCtrl::DeleteBand

Implementa el comportamiento del mensaje de Win32 [RB_DELETEBAND](/windows/desktop/Controls/rb-deleteband), tal y como se describe en el Windows SDK.

```
BOOL DeleteBand(UINT uBand);
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
Índice de base cero de la banda que se va a eliminar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la banda se ha eliminado correctamente; de lo contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]

##  <a name="dragmove"></a>  CReBarCtrl::DragMove

Implementa el comportamiento del mensaje de Win32 [RB_DRAGMOVE](/windows/desktop/Controls/rb-dragmove), tal y como se describe en el Windows SDK.

```
void DragMove(DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>Parámetros

*dwPos*<br/>
Valor DWORD que contiene las nuevas coordenadas del mouse. La coordenada horizontal está contenida en el LOWORD y la coordenada vertical está contenida en el HIWORD. Si pasa (DWORD)-1, el control rebar usará la posición del mouse la última vez que el subproceso del control llamó a `GetMessage` o `PeekMessage`.

##  <a name="enddrag"></a>  CReBarCtrl::EndDrag

Implementa el comportamiento del mensaje de Win32 [RB_ENDDRAG](/windows/desktop/Controls/rb-enddrag), tal y como se describe en el Windows SDK.

```
void EndDrag();
```

##  <a name="getbandborders"></a>  CReBarCtrl::GetBandBorders

Implementa el comportamiento del mensaje de Win32 [RB_GETBANDBORDERS](/windows/desktop/Controls/rb-getbandborders), tal y como se describe en el Windows SDK.

```
void GetBandBorders(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
Índice de base cero de la banda para la que se van a recuperar los bordes.

*prc*<br/>
Puntero a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que recibirá los bordes de la banda. Si el control rebar tiene el estilo RBS_BANDBORDERS, cada miembro de esta estructura recibirá el número de píxeles, en el lado correspondiente de la banda, que conforman el borde. Si el control rebar no tiene el estilo RBS_BANDBORDERS, solo el miembro izquierdo de esta estructura recibe información válida. Para obtener una descripción de los estilos de control rebar, vea [estilos de control rebar](/windows/desktop/Controls/rebar-control-styles) en el Windows SDK.

##  <a name="getbandcount"></a>  CReBarCtrl::GetBandCount

Implementa el comportamiento del mensaje de Win32 [RB_GETBANDCOUNT](/windows/desktop/Controls/rb-getbandcount), tal y como se describe en el Windows SDK.

```
UINT GetBandCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de bandas asignados al control.

##  <a name="getbandinfo"></a>  CReBarCtrl::GetBandInfo

Implementa el comportamiento del mensaje de Win32 [RB_GETBANDINFO](/windows/desktop/Controls/rb-getbandinfo) tal como se describe en el Windows SDK.

```
BOOL GetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi) const;
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
Índice de base cero de la banda para la que se recuperará la información.

*prbbi*<br/>
Puntero a una estructura [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) para recibir la información de la banda. Debe establecer el `cbSize` miembro de esta estructura en `sizeof(REBARBANDINFO)` y establecer el `fMask` miembro en los elementos que desea recuperar antes de enviar este mensaje.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

##  <a name="getbandmargins"></a>  CReBarCtrl::GetBandMargins

Recupera los márgenes de la banda.

```
void GetBandMargins(PMARGINS pMargins);
```

### <a name="parameters"></a>Parámetros

*pMargins*<br/>
Un puntero a una estructura de [márgenes](/windows/desktop/api/uxtheme/ns-uxtheme-margins) que recibirá la información.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad del mensaje [RB_GETBANDMARGINS](/windows/desktop/Controls/rb-getbandmargins) , tal y como se describe en el Windows SDK.

##  <a name="getbarheight"></a>  CReBarCtrl::GetBarHeight

Recupera el alto de la barra rebar.

```
UINT GetBarHeight() const;
```

### <a name="return-value"></a>Valor devuelto

Valor que representa el alto, en píxeles, del control.

##  <a name="getbarinfo"></a>  CReBarCtrl::GetBarInfo

Implementa el comportamiento del mensaje de Win32 [RB_GETBARINFO](/windows/desktop/Controls/rb-getbarinfo), tal y como se describe en el Windows SDK.

```
BOOL GetBarInfo(REBARINFO* prbi) const;
```

### <a name="parameters"></a>Parámetros

*prbi*<br/>
Puntero a una estructura [REBARINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarinfo) que recibirá la información del control rebar. Debe establecer el miembro *cbSize* de esta estructura en antes `sizeof(REBARINFO)` de enviar este mensaje.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

##  <a name="getbkcolor"></a>  CReBarCtrl::GetBkColor

Implementa el comportamiento del mensaje de Win32 [RB_GETBKCOLOR](/windows/desktop/Controls/rb-getbkcolor), tal y como se describe en el Windows SDK.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de COLORREF que representa el color de fondo predeterminado actual.

##  <a name="getcolorscheme"></a>  CReBarCtrl::GetColorScheme

Recupera la estructura [COLORSCHEME](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme) del control rebar.

```
BOOL GetColorScheme(COLORSCHEME* lpcs);
```

### <a name="parameters"></a>Parámetros

*lpcs*<br/>
Puntero a una estructura [COLORSCHEME](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme) , como se describe en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

La `COLORSCHEME` estructura incluye el color de resaltado del botón y el color de la sombra del botón.

##  <a name="getdroptarget"></a>  CReBarCtrl::GetDropTarget

Implementa el comportamiento del mensaje de Win32 [RB_GETDROPTARGET](/windows/desktop/Controls/rb-getdroptarget), tal y como se describe en el Windows SDK.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget) .

##  <a name="getextendedstyle"></a>  CReBarCtrl::GetExtendedStyle

Obtiene los estilos extendidos del control rebar actual.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Valor devuelto

Combinación bit a bit (o) de marcas que indican los estilos extendidos. Las marcas posibles son RBS_EX_SPLITTER y RBS_EX_TRANSPARENT. Para obtener más información, vea el parámetro *dwMask* del método [CReBarCtrl:: SetExtendedStyle](#setextendedstyle) .

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [RB_GETEXTENDEDSTYLE](/windows/desktop/Controls/rb-dragmove) , que se describe en el Windows SDK.

##  <a name="getimagelist"></a>  CReBarCtrl::GetImageList

Obtiene el `CImageList` objeto asociado a un control rebar.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [CImageList](../../mfc/reference/cimagelist-class.md) . Devuelve NULL si no hay ninguna lista de imágenes establecida para el control.

### <a name="remarks"></a>Comentarios

Esta función miembro usa la información de tamaño y máscara almacenada en la estructura [REBARINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarinfo) , como se describe en el Windows SDK.

##  <a name="getpalette"></a>  CReBarCtrl::GetPalette

Recupera la paleta actual del control rebar.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [CPalette](../../mfc/reference/cpalette-class.md) que especifica la paleta actual del control rebar.

### <a name="remarks"></a>Comentarios

Tenga en cuenta que esta función miembro `CPalette` usa un objeto como valor devuelto, en lugar de HPALETTE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]

##  <a name="getrect"></a>  CReBarCtrl::GetRect

Implementa el comportamiento del mensaje de Win32 [RB_GETRECT](/windows/desktop/Controls/rb-getrect), tal y como se describe en el Windows SDK.

```
BOOL GetRect(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
Índice de base cero de una banda del control rebar.

*prc*<br/>
Puntero a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que recibirá los límites de la banda rebar.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]

##  <a name="getrowcount"></a>  CReBarCtrl::GetRowCount

Implementa el comportamiento del mensaje de Win32 [RB_GETROWCOUNT](/windows/desktop/Controls/rb-getrowcount), tal y como se describe en el Windows SDK.

```
UINT GetRowCount() const;
```

### <a name="return-value"></a>Valor devuelto

Valor UINT que representa el número de filas de banda del control.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]

##  <a name="getrowheight"></a>  CReBarCtrl::GetRowHeight

Implementa el comportamiento del mensaje de Win32 [RB_GETROWHEIGHT](/windows/desktop/Controls/rb-getrowheight), tal y como se describe en el Windows SDK.

```
UINT GetRowHeight(UINT uRow) const;
```

### <a name="parameters"></a>Parámetros

*uRow*<br/>
Índice de base cero de la banda cuyo alto se va a recuperar.

### <a name="return-value"></a>Valor devuelto

Valor UINT que representa el alto de la fila, en píxeles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]

##  <a name="gettextcolor"></a>  CReBarCtrl::GetTextColor

Implementa el comportamiento del mensaje de Win32 [RB_GETTEXTCOLOR](/windows/desktop/Controls/rb-gettextcolor), tal y como se describe en el Windows SDK.

```
COLORREF GetTextColor() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de COLORREF que representa el color de texto predeterminado actual.

##  <a name="gettooltips"></a>  CReBarCtrl::GetToolTips

Implementa el comportamiento del mensaje de Win32 [RB_GETTOOLTIPS](/windows/desktop/Controls/rb-gettooltips), tal y como se describe en el Windows SDK.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) .

### <a name="remarks"></a>Comentarios

Tenga en cuenta que la implementación `GetToolTips` de MFC de devuelve un `CToolTipCtrl`puntero a, en lugar de un HWND.

##  <a name="hittest"></a>  CReBarCtrl::HitTest

Implementa el comportamiento del mensaje de Win32 [RB_HITTEST](/windows/desktop/Controls/rb-hittest), tal y como se describe en el Windows SDK.

```
int HitTest(RBHITTESTINFO* prbht);
```

### <a name="parameters"></a>Parámetros

*prbht*<br/>
Puntero a una estructura [RBHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-_rb_hittestinfo) . Antes de enviar el mensaje, `pt` el miembro de esta estructura se debe inicializar en el punto que se va a probar, en coordenadas de cliente.

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la banda en el punto especificado, o-1 si no hay ninguna banda rebar en el punto.

##  <a name="idtoindex"></a>  CReBarCtrl::IDToIndex

Implementa el comportamiento del mensaje de Win32 [RB_IDTOINDEX](/windows/desktop/controls/rb-idtoindex), tal y como se describe en el Windows SDK.

```
int IDToIndex(UINT uBandID) const;
```

### <a name="parameters"></a>Parámetros

*uBandID*<br/>
Identificador definido por la aplicación de la banda especificada, pasado en el `wID` miembro de la estructura [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) cuando se inserta la banda.

### <a name="return-value"></a>Valor devuelto

Índice de banda de base cero si es correcto, o-1 en caso contrario. Si existen índices de banda duplicados, se devuelve el primero.

##  <a name="insertband"></a>  CReBarCtrl::InsertBand

Implementa el comportamiento del mensaje de Win32 [RB_INSERTBAND](/windows/desktop/Controls/rb-insertband), tal y como se describe en el Windows SDK.

```
BOOL InsertBand(
    UINT uIndex,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>Parámetros

*uIndex*<br/>
Índice de base cero de la ubicación donde se insertará la banda. Si establece este parámetro en-1, el control agregará la nueva banda en la última ubicación.

*prbbi*<br/>
Puntero a una estructura [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) que define la banda que se va a insertar. Debe establecer el miembro *cbSize* de esta estructura en antes `sizeof(REBARBANDINFO)` de llamar a esta función.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]

##  <a name="maximizeband"></a>CReBarCtrl:: MaximizeBand

Cambia el tamaño de una banda de un control rebar a su tamaño más grande.

```
void MaximizeBand(UINT uBand);
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
Índice de base cero de la banda que se va a maximizar.

### <a name="remarks"></a>Comentarios

Implementa el comportamiento del mensaje de Win32 [RB_MAXIMIZEBAND](/windows/desktop/Controls/rb-maximizeband) con `fIdeal` establecido en 0, tal y como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]

##  <a name="minimizeband"></a>CReBarCtrl:: MinimizeBand

Cambia el tamaño de una banda de un control rebar a su tamaño más pequeño.

```
void MinimizeBand(UINT uBand);
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
Índice de base cero de la banda que se va a minimizar.

### <a name="remarks"></a>Comentarios

Implementa el comportamiento del mensaje de Win32 [RB_MINIMIZEBAND](/windows/desktop/Controls/rb-minimizeband), tal y como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]

##  <a name="moveband"></a>  CReBarCtrl::MoveBand

Implementa el comportamiento del mensaje de Win32 [RB_MOVEBAND](/windows/desktop/Controls/rb-moveband), tal y como se describe en el Windows SDK.

```
BOOL MoveBand(
    UINT uFrom,
    UINT uTo);
```

### <a name="parameters"></a>Parámetros

*uFrom*<br/>
Índice de base cero de la banda que se va a desplace.

*uTo*<br/>
Índice de base cero de la nueva posición de banda. Este valor de parámetro nunca debe ser mayor que el número de bandas menos uno. Para obtener el número de bandas, llame a [GetBandCount](#getbandcount).

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

##  <a name="pushchevron"></a>CReBarCtrl::P ushChevron

Implementa el comportamiento del mensaje de Win32 [RB_PUSHCHEVRON](/windows/desktop/Controls/rb-pushchevron), tal y como se describe en el Windows SDK.

```
void PushChevron(
    UINT uBand,
    LPARAM lAppValue);
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
Índice de base cero de la banda cuyo cheurón se va a insertar.

*lAppValue*<br/>
Un valor de 32 bits definido por la aplicación. Consulte *lAppValue* en [RB_PUSHCHEVRON](/windows/desktop/Controls/rb-pushchevron) en el Windows SDK.

##  <a name="restoreband"></a>  CReBarCtrl::RestoreBand

Cambia el tamaño de una banda de un control rebar a su tamaño ideal.

```
void RestoreBand(UINT uBand);
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
Índice de base cero de la banda que se va a maximizar.

### <a name="remarks"></a>Comentarios

Implementa el comportamiento del mensaje de Win32 [RB_MAXIMIZEBAND](/windows/desktop/Controls/rb-maximizeband) con `fIdeal` establecido en 1, como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]

##  <a name="setbandinfo"></a>  CReBarCtrl::SetBandInfo

Implementa el comportamiento del mensaje de Win32 [RB_SETBANDINFO](/windows/desktop/Controls/rb-setbandinfo), tal y como se describe en el Windows SDK.

```
BOOL SetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
Índice de base cero de la banda que va a recibir la nueva configuración.

*prbbi*<br/>
Puntero a una estructura [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) que define la banda que se va a insertar. Debe establecer el `cbSize` miembro de esta estructura en antes `sizeof(REBARBANDINFO)` de enviar este mensaje.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]

##  <a name="setbandwidth"></a>  CReBarCtrl::SetBandWidth

Establece el ancho de la banda acoplada especificada en el control rebar actual.

```
BOOL SetBandWidth(
    UINT uBand,
    int cxWidth);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*uBand*|de Índice de base cero de una banda rebar.|
|*cxWidth*|de Nuevo ancho de la banda Rebar, en píxeles.|

### <a name="return-value"></a>Valor devuelto

TRUE si el método es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [RB_SETBANDWIDTH](/windows/desktop/Controls/rb-setbandwidth) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define `m_rebar`la variable,, que se utiliza para tener acceso al control rebar actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece que cada banda rebar tenga el mismo ancho.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]

##  <a name="setbarinfo"></a>  CReBarCtrl::SetBarInfo

Implementa el comportamiento del mensaje de Win32 [RB_SETBARINFO](/windows/desktop/Controls/rb-setbarinfo), tal y como se describe en el Windows SDK.

```
BOOL SetBarInfo(REBARINFO* prbi);
```

### <a name="parameters"></a>Parámetros

*prbi*<br/>
Puntero a una estructura [REBARINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarinfo) que contiene la información que se va a establecer. Debe establecer el `cbSize` miembro de esta estructura en antes `sizeof(REBARINFO)` de enviar este mensaje.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]

##  <a name="setbkcolor"></a>  CReBarCtrl::SetBkColor

Implementa el comportamiento del mensaje de Win32 [RB_SETBKCOLOR](/windows/desktop/Controls/rb-setbkcolor), tal y como se describe en el Windows SDK.

```
COLORREF SetBkColor(COLORREF clr);
```

### <a name="parameters"></a>Parámetros

*clr*<br/>
Valor de COLORREF que representa el nuevo color de fondo predeterminado.

### <a name="return-value"></a>Valor devuelto

Valor de [COLORREF](/windows/desktop/gdi/colorref) que representa el color de fondo predeterminado anterior.

### <a name="remarks"></a>Comentarios

Vea este tema para obtener más información sobre cuándo establecer el color de fondo y cómo establecer el valor predeterminado.

##  <a name="setcolorscheme"></a>  CReBarCtrl::SetColorScheme

Establece la combinación de colores de los botones en un control rebar.

```
void SetColorScheme(const COLORSCHEME* lpcs);
```

### <a name="parameters"></a>Parámetros

*lpcs*<br/>
Puntero a una estructura [COLORSCHEME](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme) , como se describe en el Windows SDK.

### <a name="remarks"></a>Comentarios

La `COLORSCHEME` estructura incluye el color de resaltado del botón y el color de la sombra del botón.

##  <a name="setextendedstyle"></a>  CReBarCtrl::SetExtendedStyle

Establece los estilos extendidos para el control rebar actual.

```
DWORD SetExtendedStyle(
    DWORD dwMask,
    DWORD dwStyleEx);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*dwMask*|de Combinación bit a bit (o) de marcas que especifican las marcas que se aplican en el parámetro *dwStyleEx* . Utilice uno o varios de los valores siguientes:<br /><br /> RBS_EX_SPLITTER: De forma predeterminada, muestre el divisor en la parte inferior en modo horizontal y a la derecha en modo vertical.<br /><br /> RBS_EX_TRANSPARENT: Reenvíe el mensaje [WM_ERASEBKGND](/windows/desktop/winmsg/wm-erasebkgnd) a la ventana primaria.|
|*dwStyleEx*|de Combinación bit a bit (o) de marcas que especifican los estilos que se van a aplicar. Para establecer un estilo, especifique la misma marca que se usa en el parámetro *dwMask* . Para restablecer un estilo, especifique cero binario.|

### <a name="return-value"></a>Valor devuelto

Estilo extendido anterior.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [RB_SETEXTENDEDSTYLE](/windows/desktop/Controls/rb-setextendedstyle) , que se describe en el Windows SDK.

##  <a name="setimagelist"></a>  CReBarCtrl::SetImageList

Asigna una lista de imágenes a un control rebar.

```
BOOL SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parámetros

*pImageList*<br/>
Un puntero a un objeto [CImageList](../../mfc/reference/cimagelist-class.md) que contiene la lista de imágenes que se va a asignar al control rebar.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

##  <a name="setowner"></a>  CReBarCtrl::SetOwner

Implementa el comportamiento del mensaje de Win32 [RB_SETPARENT](/windows/desktop/Controls/rb-setparent), tal y como se describe en el Windows SDK.

```
CWnd* SetOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Un puntero a un `CWnd` objeto que se va a establecer como propietario del control rebar.

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [CWnd](../../mfc/reference/cwnd-class.md) que es el propietario actual del control rebar.

### <a name="remarks"></a>Comentarios

Tenga en cuenta que esta función miembro utiliza punteros a `CWnd` objetos para el propietario actual y seleccionado del control rebar, en lugar de los controladores de Windows.

> [!NOTE]
>  Esta función miembro no cambia el elemento primario real que se estableció cuando se creó el control. en su lugar, envía mensajes de notificación a la ventana que especifique.

##  <a name="setpalette"></a>  CReBarCtrl::SetPalette

Implementa el comportamiento del mensaje de Win32 [RB_SETPALETTE](/windows/desktop/Controls/rb-setpalette), tal y como se describe en el Windows SDK.

```
CPalette* SetPalette(HPALETTE hPal);
```

### <a name="parameters"></a>Parámetros

*hPal*<br/>
HPALETTE que especifica la nueva paleta que usará el control rebar.

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [CPalette](../../mfc/reference/cpalette-class.md) que especifica la paleta anterior del control rebar.

### <a name="remarks"></a>Comentarios

Tenga en cuenta que esta función miembro `CPalette` usa un objeto como valor devuelto, en lugar de HPALETTE.

##  <a name="settextcolor"></a>  CReBarCtrl::SetTextColor

Implementa el comportamiento del mensaje de Win32 [RB_SETTEXTCOLOR](/windows/desktop/Controls/rb-settextcolor), tal y como se describe en el Windows SDK.

```
COLORREF SetTextColor(COLORREF clr);
```

### <a name="parameters"></a>Parámetros

*clr*<br/>
Valor de COLORREF que representa el nuevo color del texto en `CReBarCtrl` el objeto.

### <a name="return-value"></a>Valor devuelto

Valor de [COLORREF](/windows/desktop/gdi/colorref) que representa el color de texto anterior asociado `CReBarCtrl` al objeto.

### <a name="remarks"></a>Comentarios

Se proporciona para admitir la flexibilidad del color del texto en un control rebar.

##  <a name="settooltips"></a>  CReBarCtrl::SetToolTips

Asocia un control de información sobre herramientas a un control rebar.

```
void SetToolTips(CToolTipCtrl* pToolTip);
```

### <a name="parameters"></a>Parámetros

*pToolTip*<br/>
Un puntero a un objeto [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)

### <a name="remarks"></a>Comentarios

Cuando haya terminado, `CToolTipCtrl` debe destruir el objeto.

##  <a name="setwindowtheme"></a>  CReBarCtrl::SetWindowTheme

Establece el estilo visual del control rebar.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parámetros

*pszSubAppName*<br/>
Puntero a una cadena Unicode que contiene el estilo visual de Rebar que se va a establecer.

### <a name="return-value"></a>Valor devuelto

No se utiliza el valor devuelto.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad del mensaje [RB_SETWINDOWTHEME](/windows/desktop/Controls/rb-setwindowtheme) , tal y como se describe en el Windows SDK.

##  <a name="showband"></a>  CReBarCtrl::ShowBand

Implementa el comportamiento del mensaje de Win32 [RB_SHOWBAND](/windows/desktop/Controls/rb-showband), tal y como se describe en el Windows SDK.

```
BOOL ShowBand(
    UINT uBand,
    BOOL fShow = TRUE);
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
Índice de base cero de una banda del control rebar.

*fShow*<br/>
Indica si la banda se debe mostrar u ocultar. Si este valor es TRUE, se mostrará la banda. De lo contrario, se ocultará la banda.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

##  <a name="sizetorect"></a>  CReBarCtrl::SizeToRect

Implementa el comportamiento del mensaje de Win32 [RB_SIZETORECT](/windows/desktop/Controls/rb-sizetorect), tal y como se describe en el Windows SDK.

```
BOOL SizeToRect(CRect& rect);
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
Referencia a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) que especifica el rectángulo al que se debe ajustar el tamaño del control rebar.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Tenga en cuenta que esta función miembro `CRect` usa un objeto como parámetro, en lugar `RECT` de una estructura.

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
