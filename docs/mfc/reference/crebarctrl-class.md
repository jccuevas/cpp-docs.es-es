---
title: Clase CReBarCtrl
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
ms.openlocfilehash: 776892d71e2cb0f5d57512754cd7fa12730eb044
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367442"
---
# <a name="crebarctrl-class"></a>Clase CReBarCtrl

Encapsula la funcionalidad de un control rebar, que es un contenedor para una ventana secundaria.

## <a name="syntax"></a>Sintaxis

```
class CReBarCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CReBarCtrl::CReBarCtrl](#crebarctrl)|Construye un objeto `CReBarCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CReBarCtrl::BeginDrag](#begindrag)|Coloca el control de armadura en modo de arrastrar y colocar.|
|[CReBarCtrl::Crear](#create)|Crea el control de armadura y `CReBarCtrl` lo adjunta al objeto.|
|[CReBarCtrl::CreateEx](#createex)|Crea un control de armadura con los estilos extendidos de Windows especificados y lo asocia a un `CReBarCtrl` objeto.|
|[CReBarCtrl::DeleteBand](#deleteband)|Elimina una banda de un control de armadura.|
|[CReBarCtrl::DragMove](#dragmove)|Actualiza la posición de arrastre en el `BeginDrag`control de armadura después de una llamada a .|
|[CReBarCtrl::EndDrag](#enddrag)|Termina la operación de arrastrar y colocar del control de armadura.|
|[CReBarCtrl::GetBandBorders](#getbandborders)|Recupera los bordes de una banda.|
|[CReBarCtrl::GetBandCount](#getbandcount)|Recupera el recuento de bandas actualmente en el control de armadura.|
|[CReBarCtrl::GetBandInfo](#getbandinfo)|Recupera información sobre una banda especificada en un control de armadura.|
|[CReBarCtrl::GetBandMargins](#getbandmargins)|Recupera los márgenes de una banda.|
|[CReBarCtrl::GetBarHeight](#getbarheight)|Recupera el alto del control de armadura.|
|[CReBarCtrl::GetBarInfo](#getbarinfo)|Recupera información sobre el control de armadura y la lista de imágenes que utiliza.|
|[CReBarCtrl::GetBkColor](#getbkcolor)|Recupera el color de fondo predeterminado de un control de armadura.|
|[CReBarCtrl::GetColorScheme](#getcolorscheme)|Recupera la estructura [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) asociada al control de armadura.|
|[CReBarCtrl::GetDropTarget](#getdroptarget)|Recupera el puntero de `IDropTarget` interfaz de un control de armadura.|
|[CReBarCtrl::GetExtendedStyle](#getextendedstyle)|Obtiene el estilo extendido del control de armadura actual.|
|[CReBarCtrl::GetImageList](#getimagelist)|Recupera la lista de imágenes asociada a un control de armadura.|
|[CReBarCtrl::GetPalette](#getpalette)|Recupera la paleta actual del control de armadura.|
|[CReBarCtrl::GetRect](#getrect)|Recupera el rectángulo delimitador de una banda determinada en un control de armadura.|
|[CReBarCtrl::GetRowCount](#getrowcount)|Recupera el número de filas de banda en un control de armadura.|
|[CReBarCtrl::GetRowHeight](#getrowheight)|Recupera el alto de una fila especificada en un control de armadura.|
|[CReBarCtrl::GetTextColor](#gettextcolor)|Recupera el color de texto predeterminado de un control de armadura.|
|[CReBarCtrl::GetToolTips](#gettooltips)|Recupera el identificador de cualquier control de información sobre herramientas asociado con el control de armadura.|
|[CReBarCtrl::HitTest](#hittest)|Determina qué parte de una banda de armadura se encuentra en un punto determinado de la pantalla, si existe una banda de armadura en ese punto.|
|[CReBarCtrl::IDToIndex](#idtoindex)|Convierte un identificador de banda (ID) en un índice de banda en un control de armadura.|
|[CReBarCtrl::InsertBand](#insertband)|Inserta una nueva banda en un control de armadura.|
|[CReBarCtrl::MaximizeBand](#maximizeband)|Cambia el tamaño de una banda en un control de armadura a su tamaño más grande.|
|[CReBarCtrl::MinimizeBand](#minimizeband)|Cambia el tamaño de una banda en un control de armadura a su tamaño más pequeño.|
|[CReBarCtrl::MoveBand](#moveband)|Mueve una banda de un índice a otro.|
|[CReBarCtrl::PushChevron](#pushchevron)|Empuja mediante programación un chevron.|
|[CReBarCtrl::RestoreBand](#restoreband)|Cambia el tamaño de una banda en un control de armadura a su tamaño ideal.|
|[CReBarCtrl::SetBandInfo](#setbandinfo)|Establece las características de una banda existente en un control de armadura.|
|[CReBarCtrl::SetBandWidth](#setbandwidth)|Establece el ancho de la banda acoplada especificada en el control de armadura actual.|
|[CReBarCtrl::SetBarInfo](#setbarinfo)|Establece las características de un control de armadura.|
|[CReBarCtrl::SetBkColor](#setbkcolor)|Establece el color de fondo predeterminado de un control de armadura.|
|[CReBarCtrl::SetColorScheme](#setcolorscheme)|Establece el esquema de color para los botones de un control de armadura.|
|[CReBarCtrl::SetExtendedStyle](#setextendedstyle)|Establece los estilos extendidos para el control de armadura actual.|
|[CReBarCtrl::SetImageList](#setimagelist)|Establece la lista de imágenes de un control de armadura.|
|[CReBarCtrl::SetOwner](#setowner)|Establece la ventana propietaria de un control de armadura.|
|[CReBarCtrl::SetPalette](#setpalette)|Establece la paleta actual del control de armadura.|
|[CReBarCtrl::SetTextColor](#settextcolor)|Establece el color de texto predeterminado de un control de armadura.|
|[CReBarCtrl::SetToolTips](#settooltips)|Asocia un control de información sobre herramientas con el control de armadura.|
|[CReBarCtrl::SetWindowTheme](#setwindowtheme)|Establece el estilo visual del control de armadura.|
|[CReBarCtrl::ShowBand](#showband)|Muestra u oculta una banda determinada en un control de armadura.|
|[CReBarCtrl::SizeToRect](#sizetorect)|Ajusta un control de armadura a un rectángulo especificado.|

## <a name="remarks"></a>Observaciones

La aplicación en la que reside el control de armadura asigna la ventana secundaria contenida por el control de armadura a la banda de armadura. La ventana secundaria suele ser otro control común.

Los controles de armadura contienen una o más bandas. Cada banda puede contener una combinación de una barra de pinzamiento, un mapa de bits, una etiqueta de texto y una ventana secundaria. La banda puede contener solo uno de estos elementos.

El control de armadura puede mostrar la ventana secundaria sobre un mapa de bits de fondo especificado. Se puede cambiar el tamaño de todas las bandas de control de armadura, excepto las que utilizan el estilo RBBS_FIXEDSIZE. Al cambiar la posición o el tamaño de una banda de control de armadura, el control de armadura administra el tamaño y la posición de la ventana secundaria asignada a esa banda. Para cambiar el tamaño o el cambio del orden de las bandas dentro del control, haga clic y arrastre la barra de agarre de una banda.

La siguiente ilustración muestra un control de armadura que tiene tres bandas:

- La banda 0 contiene un control de barra de herramientas transparente y plano.

- La banda 1 contiene botones desplegables estándar y transparentes transparentes.

- La banda 2 contiene una caja combinación y cuatro botones estándar.

   ![Ejemplo de un menú Rebar](../../mfc/reference/media/vc4scc1.gif "Ejemplo de un menú Rebar")

## <a name="rebar-control"></a>Control de armadura

Los controles de armadura admiten:

- Listas de imágenes.

- Manejo de mensajes.

- Funcionalidad de dibujo personalizado.

- Una variedad de estilos de control además de los estilos de ventana estándar. Para obtener una lista de estos estilos, vea [Estilos](/windows/win32/Controls/rebar-control-styles) de control de armadura en el Windows SDK.

Para obtener más información, consulte Uso de [CReBarCtrl](../../mfc/using-crebarctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CReBarCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

## <a name="crebarctrlbegindrag"></a><a name="begindrag"></a>CReBarCtrl::BeginDrag

Implementa el comportamiento del mensaje De32 [RB_BEGINDRAG](/windows/win32/Controls/rb-begindrag), como se describe en el Windows SDK.

```
void BeginDrag(
    UINT uBand,
    DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
El índice de base cero de la banda a la que afectará la operación de arrastrar y colocar.

*dwPos*<br/>
Un valor DWORD que contiene las coordenadas iniciales del mouse. La coordenada horizontal está contenida en lo WORD y la coordenada vertical está contenida en HIWORD. Si pasa (DWORD)-1, el control de armadura usará la posición del mouse `GetMessage` la `PeekMessage`última vez que el subproceso del control llamó o .

## <a name="crebarctrlcreate"></a><a name="create"></a>CReBarCtrl::Crear

Crea el control de armadura y `CReBarCtrl` lo adjunta al objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica la combinación de estilos de control de armadura aplicados al control. Consulte [Estilos](/windows/win32/Controls/rebar-control-styles) de control de armadura en el Windows SDK para obtener una lista de estilos admitidos.

*Rect*<br/>
Una referencia a un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura, que es la posición y el tamaño del control de armadura.

*pParentWnd*<br/>
Puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que es la ventana primaria del control de armadura. No debe ser NULL.

*nID*<br/>
Especifica el identificador de control del control de armadura.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto se creó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Cree un control de armadura en dos pasos:

1. Llame a [CReBarCtrl](#crebarctrl) para construir un `CReBarCtrl` objeto.

1. Llame a esta función miembro, que crea el `CReBarCtrl` control de armadura de Windows y lo adjunta al objeto.

Cuando se `Create`llama a , se inicializan los controles comunes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]

## <a name="crebarctrlcreateex"></a><a name="createex"></a>CReBarCtrl::CreateEx

Crea un control (una ventana secundaria) `CReBarCtrl` y lo asocia con el objeto.

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
Especifica el estilo extendido del control que se está creando. Para obtener una lista de estilos de Windows extendidos, vea el *dwExStyle* parámetro para [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*dwStyle*<br/>
Especifica la combinación de estilos de control de armadura aplicados al control. Para obtener una lista de estilos admitidos, vea [Estilos](/windows/win32/Controls/rebar-control-styles) de control de armadura en el Windows SDK.

*Rect*<br/>
Una referencia a una estructura [RECT](/previous-versions/dd162897\(v=vs.85\)) que describe el tamaño y la posición de la ventana que se va a crear, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*nID*<br/>
Identificador de ventana secundaria del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Se `CreateEx` usa en lugar de [Crear](#create) para aplicar estilos de Windows extendidos, especificados por el **prefacio**de estilo extendido de Windows WS_EX_ .

## <a name="crebarctrlcrebarctrl"></a><a name="crebarctrl"></a>CReBarCtrl::CReBarCtrl

Crea un objeto `CReBarCtrl` .

```
CReBarCtrl();
```

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CReBarCtrl::Create](#create).

## <a name="crebarctrldeleteband"></a><a name="deleteband"></a>CReBarCtrl::DeleteBand

Implementa el comportamiento del mensaje de Win32 [RB_DELETEBAND](/windows/win32/Controls/rb-deleteband), como se describe en el Windows SDK.

```
BOOL DeleteBand(UINT uBand);
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
El índice de base cero de la banda que se va a eliminar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la banda se eliminó correctamente; de lo contrario cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]

## <a name="crebarctrldragmove"></a><a name="dragmove"></a>CReBarCtrl::DragMove

Implementa el comportamiento del mensaje Win32 [RB_DRAGMOVE](/windows/win32/Controls/rb-dragmove), como se describe en el Windows SDK.

```
void DragMove(DWORD dwPos = (DWORD)-1);
```

### <a name="parameters"></a>Parámetros

*dwPos*<br/>
Un valor DWORD que contiene las nuevas coordenadas del mouse. La coordenada horizontal está contenida en lo WORD y la coordenada vertical está contenida en HIWORD. Si pasa (DWORD)-1, el control de armadura usará la posición del mouse `GetMessage` la `PeekMessage`última vez que el subproceso del control llamó o .

## <a name="crebarctrlenddrag"></a><a name="enddrag"></a>CReBarCtrl::EndDrag

Implementa el comportamiento del [RB_ENDDRAG](/windows/win32/Controls/rb-enddrag)de mensajes de Win32, como se describe en el Windows SDK.

```
void EndDrag();
```

## <a name="crebarctrlgetbandborders"></a><a name="getbandborders"></a>CReBarCtrl::GetBandBorders

Implementa el comportamiento del mensaje de Win32 [RB_GETBANDBORDERS](/windows/win32/Controls/rb-getbandborders), como se describe en el Windows SDK.

```
void GetBandBorders(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
El índice de base cero de la banda para la que se recuperarán los bordes.

*Prc*<br/>
Puntero a una estructura [RECT](/previous-versions/dd162897\(v=vs.85\)) que recibirá los bordes de la banda. Si el control de armadura tiene el estilo RBS_BANDBORDERS, cada miembro de esta estructura recibirá el número de píxeles, en el lado correspondiente de la banda, que constituyen el borde. Si el control de armadura no tiene el estilo RBS_BANDBORDERS, solo el miembro izquierdo de esta estructura recibe información válida. Para obtener una descripción de los estilos de control de armadura, vea [Estilos](/windows/win32/Controls/rebar-control-styles) de control de armadura en el Windows SDK.

## <a name="crebarctrlgetbandcount"></a><a name="getbandcount"></a>CReBarCtrl::GetBandCount

Implementa el comportamiento del mensaje de Win32 [RB_GETBANDCOUNT](/windows/win32/Controls/rb-getbandcount), como se describe en el Windows SDK.

```
UINT GetBandCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de bandas asignadas al control.

## <a name="crebarctrlgetbandinfo"></a><a name="getbandinfo"></a>CReBarCtrl::GetBandInfo

Implementa el comportamiento del mensaje de Win32 [RB_GETBANDINFO](/windows/win32/Controls/rb-getbandinfo) como se describe en el Windows SDK.

```
BOOL GetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi) const;
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
El índice de base cero de la banda para la que se recuperará la información.

*prbbi*<br/>
Puntero a una estructura [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) para recibir la información de banda. Debe establecer `cbSize` el miembro de `sizeof(REBARBANDINFO)` esta `fMask` estructura y establecer el miembro en los elementos que desea recuperar antes de enviar este mensaje.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

## <a name="crebarctrlgetbandmargins"></a><a name="getbandmargins"></a>CReBarCtrl::GetBandMargins

Recupera los márgenes de la banda.

```
void GetBandMargins(PMARGINS pMargins);
```

### <a name="parameters"></a>Parámetros

*pMargins*<br/>
Puntero a una estructura [MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins)que recibirá la información.

### <a name="remarks"></a>Observaciones

Esta función miembro emula la funcionalidad del [mensaje de RB_GETBANDMARGINS,](/windows/win32/Controls/rb-getbandmargins) como se describe en el Windows SDK.

## <a name="crebarctrlgetbarheight"></a><a name="getbarheight"></a>CReBarCtrl::GetBarHeight

Recupera la altura de la barra de armadura.

```
UINT GetBarHeight() const;
```

### <a name="return-value"></a>Valor devuelto

Valor que representa la altura, en píxeles, del control.

## <a name="crebarctrlgetbarinfo"></a><a name="getbarinfo"></a>CReBarCtrl::GetBarInfo

Implementa el comportamiento del mensaje Win32 [RB_GETBARINFO](/windows/win32/Controls/rb-getbarinfo), como se describe en el Windows SDK.

```
BOOL GetBarInfo(REBARINFO* prbi) const;
```

### <a name="parameters"></a>Parámetros

*prbi*<br/>
Puntero a una estructura [REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) que recibirá la información de control de armadura. Debe establecer el miembro *cbSize* `sizeof(REBARINFO)` de esta estructura antes de enviar este mensaje.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

## <a name="crebarctrlgetbkcolor"></a><a name="getbkcolor"></a>CReBarCtrl::GetBkColor

Implementa el comportamiento del mensaje [Win32 RB_GETBKCOLOR](/windows/win32/Controls/rb-getbkcolor), como se describe en el Windows SDK.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valor devuelto

Valor COLORREF que representa el color de fondo predeterminado actual.

## <a name="crebarctrlgetcolorscheme"></a><a name="getcolorscheme"></a>CReBarCtrl::GetColorScheme

Recupera la estructura [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) para el control de armadura.

```
BOOL GetColorScheme(COLORSCHEME* lpcs);
```

### <a name="parameters"></a>Parámetros

*lpcs*<br/>
Un puntero a un [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) estructura, como se describe en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

La `COLORSCHEME` estructura incluye el color de resaltado del botón y el color de sombra del botón.

## <a name="crebarctrlgetdroptarget"></a><a name="getdroptarget"></a>CReBarCtrl::GetDropTarget

Implementa el comportamiento del mensaje de Win32 [RB_GETDROPTARGET](/windows/win32/Controls/rb-getdroptarget), como se describe en el Windows SDK.

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget) interfaz.

## <a name="crebarctrlgetextendedstyle"></a><a name="getextendedstyle"></a>CReBarCtrl::GetExtendedStyle

Obtiene los estilos extendidos del control de armadura actual.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Valor devuelto

Una combinación bit a bit (OR) de indicadores que indican los estilos extendidos. Las banderas posibles están RBS_EX_SPLITTER y RBS_EX_TRANSPARENT. Para obtener más información, vea el *dwMask* parámetro de la [CReBarCtrl::SetExtendedStyle](#setextendedstyle) método.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje RB_GETEXTENDEDSTYLE,](/windows/win32/Controls/rb-dragmove) que se describe en el Windows SDK.

## <a name="crebarctrlgetimagelist"></a><a name="getimagelist"></a>CReBarCtrl::GetImageList

Obtiene el `CImageList` objeto asociado a un control de armadura.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto. Devuelve NULL si no se establece ninguna lista de imágenes para el control.

### <a name="remarks"></a>Observaciones

Esta función miembro utiliza información de tamaño y máscara almacenada en la estructura [REBARINFO,](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) como se describe en el Windows SDK.

## <a name="crebarctrlgetpalette"></a><a name="getpalette"></a>CReBarCtrl::GetPalette

Recupera la paleta actual del control de armadura.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto [CPalette](../../mfc/reference/cpalette-class.md) que especifica la paleta actual del control de armadura.

### <a name="remarks"></a>Observaciones

Tenga en cuenta que `CPalette` esta función miembro utiliza un objeto como su valor devuelto, en lugar de un HPALETTE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]

## <a name="crebarctrlgetrect"></a><a name="getrect"></a>CReBarCtrl::GetRect

Implementa el comportamiento del mensaje [de](/windows/win32/Controls/rb-getrect)Win32 RB_GETRECT , como se describe en el Windows SDK.

```
BOOL GetRect(
    UINT uBand,
    LPRECT prc) const;
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
El índice de base cero de una banda en el control de armadura.

*Prc*<br/>
Puntero a una estructura [RECT](/previous-versions/dd162897\(v=vs.85\)) que recibirá los límites de la banda de armadura.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]

## <a name="crebarctrlgetrowcount"></a><a name="getrowcount"></a>CReBarCtrl::GetRowCount

Implementa el comportamiento del mensaje Win32 [RB_GETROWCOUNT](/windows/win32/Controls/rb-getrowcount), como se describe en el Windows SDK.

```
UINT GetRowCount() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor UINT que representa el número de filas de banda en el control.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]

## <a name="crebarctrlgetrowheight"></a><a name="getrowheight"></a>CReBarCtrl::GetRowHeight

Implementa el comportamiento del mensaje De32 [RB_GETROWHEIGHT](/windows/win32/Controls/rb-getrowheight), como se describe en el Windows SDK.

```
UINT GetRowHeight(UINT uRow) const;
```

### <a name="parameters"></a>Parámetros

*uRow*<br/>
El índice de base cero de la banda que tendrá su altura recuperada.

### <a name="return-value"></a>Valor devuelto

Un valor UINT que representa el alto de la fila, en píxeles.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]

## <a name="crebarctrlgettextcolor"></a><a name="gettextcolor"></a>CReBarCtrl::GetTextColor

Implementa el comportamiento del mensaje Win32 [RB_GETTEXTCOLOR](/windows/win32/Controls/rb-gettextcolor), como se describe en el Windows SDK.

```
COLORREF GetTextColor() const;
```

### <a name="return-value"></a>Valor devuelto

Valor COLORREF que representa el color de texto predeterminado actual.

## <a name="crebarctrlgettooltips"></a><a name="gettooltips"></a>CReBarCtrl::GetToolTips

Implementa el comportamiento del mensaje de Win32 [RB_GETTOOLTIPS](/windows/win32/Controls/rb-gettooltips), como se describe en el Windows SDK.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objeto.

### <a name="remarks"></a>Observaciones

Tenga en cuenta `GetToolTips` que la implementación MFC de devuelve un puntero a un `CToolTipCtrl`, en lugar de un HWND.

## <a name="crebarctrlhittest"></a><a name="hittest"></a>CReBarCtrl::HitTest

Implementa el comportamiento del mensaje de Win32 [RB_HITTEST](/windows/win32/Controls/rb-hittest), como se describe en el Windows SDK.

```
int HitTest(RBHITTESTINFO* prbht);
```

### <a name="parameters"></a>Parámetros

*prbht*<br/>
Un puntero a un [RBHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-rbhittestinfo) estructura. Antes de enviar `pt` el mensaje, el miembro de esta estructura debe inicializarse hasta el punto que se probará, en coordenadas de cliente.

### <a name="return-value"></a>Valor devuelto

El índice de base cero de la banda en el punto dado, o -1 si no había ninguna banda de armadura en el punto.

## <a name="crebarctrlidtoindex"></a><a name="idtoindex"></a>CReBarCtrl::IDToIndex

Implementa el comportamiento del mensaje Win32 [RB_IDTOINDEX](/windows/win32/controls/rb-idtoindex), como se describe en el Windows SDK.

```
int IDToIndex(UINT uBandID) const;
```

### <a name="parameters"></a>Parámetros

*uBandID*<br/>
Identificador definido por la aplicación de la `wID` banda especificada, pasado en el miembro de la estructura [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) cuando se inserta la banda.

### <a name="return-value"></a>Valor devuelto

El índice de banda de base cero si se realiza correctamente, o -1 en caso contrario. Si existen índices de banda duplicados, se devuelve el primero.

## <a name="crebarctrlinsertband"></a><a name="insertband"></a>CReBarCtrl::InsertBand

Implementa el comportamiento del [RB_INSERTBAND](/windows/win32/Controls/rb-insertband)de mensajes de Win32, como se describe en el Windows SDK.

```
BOOL InsertBand(
    UINT uIndex,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>Parámetros

*uIndex*<br/>
Indice de base cero de la ubicación donde se insertará la banda. Si establece este parámetro en -1, el control agregará la nueva banda en la última ubicación.

*prbbi*<br/>
Puntero a una estructura [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) que define la banda que se va a insertar. Debe establecer el *cbSize* miembro `sizeof(REBARBANDINFO)` de esta estructura a antes de llamar a esta función.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]

## <a name="crebarctrlmaximizeband"></a><a name="maximizeband"></a>CReBarCtrl::MaximizeBand

Cambia el tamaño de una banda en un control de armadura a su tamaño más grande.

```
void MaximizeBand(UINT uBand);
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
El índice de base cero de la banda que se va a maximizar.

### <a name="remarks"></a>Observaciones

Implementa el comportamiento del [RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband) de `fIdeal` mensaje de Win32 con establecido en 0, como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]

## <a name="crebarctrlminimizeband"></a><a name="minimizeband"></a>CReBarCtrl::MinimizeBand

Cambia el tamaño de una banda en un control de armadura a su tamaño más pequeño.

```
void MinimizeBand(UINT uBand);
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
El índice de base cero de la banda que se va a minimizar.

### <a name="remarks"></a>Observaciones

Implementa el comportamiento del mensaje Win32 [RB_MINIMIZEBAND](/windows/win32/Controls/rb-minimizeband), como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]

## <a name="crebarctrlmoveband"></a><a name="moveband"></a>CReBarCtrl::MoveBand

Implementa el comportamiento del mensaje de Win32 [RB_MOVEBAND](/windows/win32/Controls/rb-moveband), como se describe en el Windows SDK.

```
BOOL MoveBand(
    UINT uFrom,
    UINT uTo);
```

### <a name="parameters"></a>Parámetros

*uFrom*<br/>
El índice de base cero de la banda que se va a mover.

*Uto*<br/>
Indice de base cero de la nueva posición de banda. Este valor de parámetro nunca debe ser mayor que el número de bandas menos una. Para obtener el número de bandas, llame a [GetBandCount](#getbandcount).

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

## <a name="crebarctrlpushchevron"></a><a name="pushchevron"></a>CReBarCtrl::PushChevron

Implementa el comportamiento del mensaje [Win32 RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron), como se describe en el Windows SDK.

```
void PushChevron(
    UINT uBand,
    LPARAM lAppValue);
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
El índice de base cero de la banda cuyo chevron se va a empujar.

*lAppValue*<br/>
Una aplicación definió el valor de 32 bits. Consulte *lAppValue* en [RB_PUSHCHEVRON](/windows/win32/Controls/rb-pushchevron) en el Windows SDK.

## <a name="crebarctrlrestoreband"></a><a name="restoreband"></a>CReBarCtrl::RestoreBand

Cambia el tamaño de una banda en un control de armadura a su tamaño ideal.

```
void RestoreBand(UINT uBand);
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
El índice de base cero de la banda que se va a maximizar.

### <a name="remarks"></a>Observaciones

Implementa el comportamiento del [RB_MAXIMIZEBAND](/windows/win32/Controls/rb-maximizeband) de `fIdeal` mensaje de Win32 con establecido en 1, como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]

## <a name="crebarctrlsetbandinfo"></a><a name="setbandinfo"></a>CReBarCtrl::SetBandInfo

Implementa el comportamiento del mensaje [Win32 RB_SETBANDINFO](/windows/win32/Controls/rb-setbandinfo), como se describe en el Windows SDK.

```
BOOL SetBandInfo(
    UINT uBand,
    REBARBANDINFO* prbbi);
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
El índice de base cero de la banda para recibir la nueva configuración.

*prbbi*<br/>
Puntero a una estructura [REBARBANDINFO](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow) que define la banda que se va a insertar. Debe establecer `cbSize` el miembro de `sizeof(REBARBANDINFO)` esta estructura en antes de enviar este mensaje.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]

## <a name="crebarctrlsetbandwidth"></a><a name="setbandwidth"></a>CReBarCtrl::SetBandWidth

Establece el ancho de la banda acoplada especificada en el control de armadura actual.

```
BOOL SetBandWidth(
    UINT uBand,
    int cxWidth);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*uBand*|[en] El índice de base cero de una banda de armadura.|
|*cxWidth*|[en] Nuevo ancho de la banda de armadura, en píxeles.|

### <a name="return-value"></a>Valor devuelto

TRUESi el método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje RB_SETBANDWIDTH,](/windows/win32/Controls/rb-setbandwidth) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de `m_rebar`código siguiente se define la variable, , que se utiliza para tener acceso al control de armadura actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece cada banda de armadura para que sea el mismo ancho.

[!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]

## <a name="crebarctrlsetbarinfo"></a><a name="setbarinfo"></a>CReBarCtrl::SetBarInfo

Implementa el comportamiento del mensaje Win32 [RB_SETBARINFO](/windows/win32/Controls/rb-setbarinfo), como se describe en el Windows SDK.

```
BOOL SetBarInfo(REBARINFO* prbi);
```

### <a name="parameters"></a>Parámetros

*prbi*<br/>
Puntero a una estructura [REBARINFO](/windows/win32/api/commctrl/ns-commctrl-rebarinfo) que contiene la información que se va a establecer. Debe establecer `cbSize` el miembro de `sizeof(REBARINFO)` esta estructura en antes de enviar este mensaje

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]

## <a name="crebarctrlsetbkcolor"></a><a name="setbkcolor"></a>CReBarCtrl::SetBkColor

Implementa el comportamiento del [RB_SETBKCOLOR](/windows/win32/Controls/rb-setbkcolor)de mensaje de Win32, como se describe en el Windows SDK.

```
COLORREF SetBkColor(COLORREF clr);
```

### <a name="parameters"></a>Parámetros

*Clr*<br/>
El valor COLORREF que representa el nuevo color de fondo predeterminado.

### <a name="return-value"></a>Valor devuelto

Un valor [COLORREF](/windows/win32/gdi/colorref) que representa el color de fondo predeterminado anterior.

### <a name="remarks"></a>Observaciones

Consulte este tema para obtener más información sobre cuándo establecer el color de fondo y cómo establecer el valor predeterminado.

## <a name="crebarctrlsetcolorscheme"></a><a name="setcolorscheme"></a>CReBarCtrl::SetColorScheme

Establece el esquema de color para los botones de un control de armadura.

```
void SetColorScheme(const COLORSCHEME* lpcs);
```

### <a name="parameters"></a>Parámetros

*lpcs*<br/>
Un puntero a un [COLORSCHEME](/windows/win32/api/commctrl/ns-commctrl-colorscheme) estructura, como se describe en el Windows SDK.

### <a name="remarks"></a>Observaciones

La `COLORSCHEME` estructura incluye tanto el color de resaltado del botón como el color de sombra del botón.

## <a name="crebarctrlsetextendedstyle"></a><a name="setextendedstyle"></a>CReBarCtrl::SetExtendedStyle

Establece los estilos extendidos para el control de armadura actual.

```
DWORD SetExtendedStyle(
    DWORD dwMask,
    DWORD dwStyleEx);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*dwMask*|[en] Una combinación bit a bit (OR) de indicadores que especifican qué indicadores en el *dwStyleEx* parámetro se aplican. Utilice uno o varios de los siguientes valores:<br /><br /> RBS_EX_SPLITTER: Por defecto, muestre el divisor en la parte inferior en modo horizontal y a la derecha en modo vertical.<br /><br /> RBS_EX_TRANSPARENT: Reenvíe el mensaje [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd) a la ventana primaria.|
|*dwStyleEx*|[en] Una combinación bit a bit (OR) de indicadores que especifican los estilos que se aplicarán. Para establecer un estilo, especifique la misma marca que se utiliza en el parámetro *dwMask.* Para restablecer un estilo, especifique cero binario.|

### <a name="return-value"></a>Valor devuelto

El estilo extendido anterior.

### <a name="remarks"></a>Observaciones

Este método envía el [RB_SETEXTENDEDSTYLE](/windows/win32/Controls/rb-setextendedstyle) mensaje, que se describe en el Windows SDK.

## <a name="crebarctrlsetimagelist"></a><a name="setimagelist"></a>CReBarCtrl::SetImageList

Asigna una lista de imágenes a un control de armadura.

```
BOOL SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parámetros

*pImageList*<br/>
Un puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto que contiene la lista de imágenes que se va a asignar al control de armadura.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

## <a name="crebarctrlsetowner"></a><a name="setowner"></a>CReBarCtrl::SetOwner

Implementa el comportamiento del mensaje [de](/windows/win32/Controls/rb-setparent)Win32 RB_SETPARENT , como se describe en el Windows SDK.

```
CWnd* SetOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero a `CWnd` un objeto que se va a establecer como propietario del control de armadura.

### <a name="return-value"></a>Valor devuelto

Puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que es el propietario actual del control de armadura.

### <a name="remarks"></a>Observaciones

Tenga en cuenta que esta `CWnd` función miembro utiliza punteros a objetos para el propietario actual y seleccionado del control de armadura, en lugar de identificadores a ventanas.

> [!NOTE]
> Esta función miembro no cambia el elemento primario real que se estableció cuando se creó el control; más bien envía mensajes de notificación a la ventana que especifique.

## <a name="crebarctrlsetpalette"></a><a name="setpalette"></a>CReBarCtrl::SetPalette

Implementa el comportamiento del mensaje [Win32 RB_SETPALETTE](/windows/win32/Controls/rb-setpalette), como se describe en el Windows SDK.

```
CPalette* SetPalette(HPALETTE hPal);
```

### <a name="parameters"></a>Parámetros

*hPal*<br/>
Un HPALETTE que especifica la nueva paleta que utilizará el control de armadura.

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto [CPalette](../../mfc/reference/cpalette-class.md) que especifica la paleta anterior del control de armadura.

### <a name="remarks"></a>Observaciones

Tenga en cuenta que `CPalette` esta función miembro utiliza un objeto como su valor devuelto, en lugar de un HPALETTE.

## <a name="crebarctrlsettextcolor"></a><a name="settextcolor"></a>CReBarCtrl::SetTextColor

Implementa el comportamiento del mensaje de Win32 [RB_SETTEXTCOLOR](/windows/win32/Controls/rb-settextcolor), como se describe en el Windows SDK.

```
COLORREF SetTextColor(COLORREF clr);
```

### <a name="parameters"></a>Parámetros

*Clr*<br/>
Un valor COLORREF que representa el `CReBarCtrl` nuevo color de texto en el objeto.

### <a name="return-value"></a>Valor devuelto

El valor [COLORREF](/windows/win32/gdi/colorref) que representa el `CReBarCtrl` color de texto anterior asociado al objeto.

### <a name="remarks"></a>Observaciones

Se proporciona para admitir la flexibilidad de color de texto en un control de armadura.

## <a name="crebarctrlsettooltips"></a><a name="settooltips"></a>CReBarCtrl::SetToolTips

Asocia un control de información sobre herramientas con un control de armadura.

```
void SetToolTips(CToolTipCtrl* pToolTip);
```

### <a name="parameters"></a>Parámetros

*pToolTip*<br/>
Un puntero a un [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objeto

### <a name="remarks"></a>Observaciones

Debe destruir `CToolTipCtrl` el objeto cuando haya terminado con él.

## <a name="crebarctrlsetwindowtheme"></a><a name="setwindowtheme"></a>CReBarCtrl::SetWindowTheme

Establece el estilo visual del control de armadura.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parámetros

*pszSubAppName*<br/>
Puntero a una cadena Unicode que contiene el estilo visual de armadura que se va a establecer.

### <a name="return-value"></a>Valor devuelto

No se utiliza el valor devuelto.

### <a name="remarks"></a>Observaciones

Esta función miembro emula la funcionalidad del [mensaje de RB_SETWINDOWTHEME,](/windows/win32/Controls/rb-setwindowtheme) como se describe en el Windows SDK.

## <a name="crebarctrlshowband"></a><a name="showband"></a>CReBarCtrl::ShowBand

Implementa el comportamiento del mensaje de Win32 [RB_SHOWBAND](/windows/win32/Controls/rb-showband), como se describe en el Windows SDK.

```
BOOL ShowBand(
    UINT uBand,
    BOOL fShow = TRUE);
```

### <a name="parameters"></a>Parámetros

*uBand*<br/>
El índice de base cero de una banda en el control de armadura.

*fMostrar*<br/>
Indica si la banda debe mostrarse u ocultarse. Si este valor es TRUE, se mostrará la banda. De lo contrario, la banda estará oculta.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

## <a name="crebarctrlsizetorect"></a><a name="sizetorect"></a>CReBarCtrl::SizeToRect

Implementa el comportamiento del mensaje de Win32 [RB_SIZETORECT](/windows/win32/Controls/rb-sizetorect), como se describe en el Windows SDK.

```
BOOL SizeToRect(CRect& rect);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
Una referencia a un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que especifica el rectángulo que el control de armadura debe tener el tamaño de.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Tenga en cuenta que `CRect` esta función miembro `RECT` utiliza un objeto como un parámetro, en lugar de una estructura.

## <a name="see-also"></a>Consulte también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
