---
title: CToolTipCtrl Class
ms.date: 11/04/2016
f1_keywords:
- CToolTipCtrl
- AFXCMN/CToolTipCtrl
- AFXCMN/CToolTipCtrl::CToolTipCtrl
- AFXCMN/CToolTipCtrl::Activate
- AFXCMN/CToolTipCtrl::AddTool
- AFXCMN/CToolTipCtrl::AdjustRect
- AFXCMN/CToolTipCtrl::Create
- AFXCMN/CToolTipCtrl::CreateEx
- AFXCMN/CToolTipCtrl::DelTool
- AFXCMN/CToolTipCtrl::GetBubbleSize
- AFXCMN/CToolTipCtrl::GetCurrentTool
- AFXCMN/CToolTipCtrl::GetDelayTime
- AFXCMN/CToolTipCtrl::GetMargin
- AFXCMN/CToolTipCtrl::GetMaxTipWidth
- AFXCMN/CToolTipCtrl::GetText
- AFXCMN/CToolTipCtrl::GetTipBkColor
- AFXCMN/CToolTipCtrl::GetTipTextColor
- AFXCMN/CToolTipCtrl::GetTitle
- AFXCMN/CToolTipCtrl::GetToolCount
- AFXCMN/CToolTipCtrl::GetToolInfo
- AFXCMN/CToolTipCtrl::HitTest
- AFXCMN/CToolTipCtrl::Pop
- AFXCMN/CToolTipCtrl::Popup
- AFXCMN/CToolTipCtrl::RelayEvent
- AFXCMN/CToolTipCtrl::SetDelayTime
- AFXCMN/CToolTipCtrl::SetMargin
- AFXCMN/CToolTipCtrl::SetMaxTipWidth
- AFXCMN/CToolTipCtrl::SetTipBkColor
- AFXCMN/CToolTipCtrl::SetTipTextColor
- AFXCMN/CToolTipCtrl::SetTitle
- AFXCMN/CToolTipCtrl::SetToolInfo
- AFXCMN/CToolTipCtrl::SetToolRect
- AFXCMN/CToolTipCtrl::SetWindowTheme
- AFXCMN/CToolTipCtrl::Update
- AFXCMN/CToolTipCtrl::UpdateTipText
helpviewer_keywords:
- CToolTipCtrl [MFC], CToolTipCtrl
- CToolTipCtrl [MFC], Activate
- CToolTipCtrl [MFC], AddTool
- CToolTipCtrl [MFC], AdjustRect
- CToolTipCtrl [MFC], Create
- CToolTipCtrl [MFC], CreateEx
- CToolTipCtrl [MFC], DelTool
- CToolTipCtrl [MFC], GetBubbleSize
- CToolTipCtrl [MFC], GetCurrentTool
- CToolTipCtrl [MFC], GetDelayTime
- CToolTipCtrl [MFC], GetMargin
- CToolTipCtrl [MFC], GetMaxTipWidth
- CToolTipCtrl [MFC], GetText
- CToolTipCtrl [MFC], GetTipBkColor
- CToolTipCtrl [MFC], GetTipTextColor
- CToolTipCtrl [MFC], GetTitle
- CToolTipCtrl [MFC], GetToolCount
- CToolTipCtrl [MFC], GetToolInfo
- CToolTipCtrl [MFC], HitTest
- CToolTipCtrl [MFC], Pop
- CToolTipCtrl [MFC], Popup
- CToolTipCtrl [MFC], RelayEvent
- CToolTipCtrl [MFC], SetDelayTime
- CToolTipCtrl [MFC], SetMargin
- CToolTipCtrl [MFC], SetMaxTipWidth
- CToolTipCtrl [MFC], SetTipBkColor
- CToolTipCtrl [MFC], SetTipTextColor
- CToolTipCtrl [MFC], SetTitle
- CToolTipCtrl [MFC], SetToolInfo
- CToolTipCtrl [MFC], SetToolRect
- CToolTipCtrl [MFC], SetWindowTheme
- CToolTipCtrl [MFC], Update
- CToolTipCtrl [MFC], UpdateTipText
ms.assetid: 8973f70c-b73a-46c7-908d-758f364b9a97
ms.openlocfilehash: bf32671eb3535de1bf072e24bc642145e87c84ee
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865460"
---
# <a name="ctooltipctrl-class"></a>CToolTipCtrl Class

Encapsula la funcionalidad de un "control de información sobre herramientas", una pequeña ventana emergente que muestra una única línea de texto que describe el propósito de una herramienta de una aplicación.

## <a name="syntax"></a>Sintaxis

```
class CToolTipCtrl : public CWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CToolTipCtrl:: CToolTipCtrl](#ctooltipctrl)|Construye un objeto `CToolTipCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CToolTipCtrl:: Activate](#activate)|Activa y desactiva el control de información sobre herramientas.|
|[CToolTipCtrl:: AddTool](#addtool)|Registra una herramienta con el control de información sobre herramientas.|
|[CToolTipCtrl:: AdjustRect](#adjustrect)|Convierte entre el rectángulo de presentación del texto de un control de información sobre herramientas y su rectángulo de ventana.|
|[CToolTipCtrl:: Create](#create)|Crea un control de información sobre herramientas y lo adjunta a un objeto `CToolTipCtrl`.|
|[CToolTipCtrl:: CreateEx](#createex)|Crea un control de información sobre herramientas con los estilos extendidos de Windows especificados y lo adjunta a un objeto `CToolTipCtrl`.|
|[CToolTipCtrl::D elTool](#deltool)|Quita una herramienta del control de información sobre herramientas.|
|[CToolTipCtrl:: GetBubbleSize](#getbubblesize)|Recupera el tamaño de la información sobre herramientas.|
|[CToolTipCtrl:: GetCurrentTool](#getcurrenttool)|Recupera información, como el tamaño, la posición y el texto, de la ventana de información sobre herramientas que muestra el control ToolTip actual.|
|[CToolTipCtrl:: GetDelayTime](#getdelaytime)|Recupera las duraciones inicial, emergente y de representación que están establecidas actualmente para un control de información sobre herramientas.|
|[CToolTipCtrl:: GetMargin](#getmargin)|Recupera los márgenes superior, izquierdo, inferior y derecho que se establecen para una ventana de información sobre herramientas.|
|[CToolTipCtrl:: GetMaxTipWidth](#getmaxtipwidth)|Recupera el ancho máximo de una ventana de información sobre herramientas.|
|[CToolTipCtrl:: GetText](#gettext)|Recupera el texto que mantiene un control de información sobre herramientas para una herramienta.|
|[CToolTipCtrl:: GetTipBkColor](#gettipbkcolor)|Recupera el color de fondo de una ventana de información sobre herramientas.|
|[CToolTipCtrl:: GetTipTextColor](#gettiptextcolor)|Recupera el color del texto en una ventana de información sobre herramientas.|
|[CToolTipCtrl:: GetTitle](#gettitle)|Recupera el título del control de información sobre herramientas actual.|
|[CToolTipCtrl:: GetToolCount](#gettoolcount)|Recupera un recuento de las herramientas que mantiene un control de información sobre herramientas.|
|[CToolTipCtrl:: GetToolInfo](#gettoolinfo)|Recupera la información que mantiene un control de información sobre herramientas sobre una herramienta.|
|[CToolTipCtrl:: HitTest](#hittest)|Comprueba un punto para determinar si está dentro del rectángulo delimitador de la herramienta especificada. Si es así, recupera información sobre la herramienta.|
|[CToolTipCtrl::P op](#pop)|Quita de la vista una ventana de información sobre herramientas mostrada.|
|[CToolTipCtrl::P opup](#popup)|Hace que el control ToolTip actual se muestre en las coordenadas del último mensaje del mouse.|
|[CToolTipCtrl:: RelayEvent](#relayevent)|Pasa un mensaje del mouse a un control de información sobre herramientas para su procesamiento.|
|[CToolTipCtrl:: SetDelayTime](#setdelaytime)|Establece las duraciones inicial, emergente y de presentación de un control de información sobre herramientas.|
|[CToolTipCtrl:: SetMargin](#setmargin)|Establece los márgenes superior, izquierdo, inferior y derecho de una ventana de información sobre herramientas.|
|[CToolTipCtrl:: SetMaxTipWidth](#setmaxtipwidth)|Establece el ancho máximo de una ventana de información sobre herramientas.|
|[CToolTipCtrl:: SetTipBkColor](#settipbkcolor)|Establece el color de fondo en una ventana de información sobre herramientas.|
|[CToolTipCtrl:: SetTipTextColor](#settiptextcolor)|Establece el color del texto en una ventana de información sobre herramientas.|
|[CToolTipCtrl:: SetTitle](#settitle)|Agrega un icono estándar y una cadena de título a una información sobre herramientas.|
|[CToolTipCtrl:: SetToolInfo](#settoolinfo)|Establece la información que mantiene una información sobre herramientas para una herramienta.|
|[CToolTipCtrl:: SetToolRect](#settoolrect)|Establece un nuevo rectángulo delimitador para una herramienta.|
|[CToolTipCtrl:: SetWindowTheme](#setwindowtheme)|Establece el estilo visual de la ventana de información sobre herramientas.|
|[CToolTipCtrl:: Update](#update)|Obliga a que se vuelva a dibujar la herramienta actual.|
|[CToolTipCtrl:: UpdateTipText](#updatetiptext)|Establece el texto de información sobre herramientas de una herramienta.|

## <a name="remarks"></a>Observaciones

Una "herramienta" es una ventana, como un control o una ventana secundaria, o un área rectangular definida por la aplicación en el área de cliente de una ventana. La información sobre herramientas está oculta en la mayoría de los casos, solo aparece cuando el usuario coloca el cursor en una herramienta y la deja allí durante aproximadamente un segundo medio. La información sobre herramientas aparece cerca del cursor y desaparece cuando el usuario hace clic en un botón del mouse o mueve el cursor fuera de la herramienta.

`CToolTipCtrl` proporciona la funcionalidad para controlar el tiempo y la duración iniciales de la información sobre herramientas, el ancho del margen alrededor del texto de información sobre herramientas, el ancho de la ventana de información sobre herramientas y el color del fondo y del texto de la información sobre herramientas. Un único control de información sobre herramientas puede proporcionar información a más de una herramienta.

La clase `CToolTipCtrl` proporciona la funcionalidad del control de información común de herramientas de Windows. Este control (y, por tanto, la clase `CToolTipCtrl`) solo está disponible para los programas que se ejecutan en Windows 95/98 y en las versiones 3,51 y posteriores de Windows NT.

Para obtener más información acerca de la habilitación de la información sobre herramientas, vea [información sobre herramientas en ventanas no derivadas de CFrameWnd](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).

Para obtener más información sobre el uso de `CToolTipCtrl`, vea [controles](../../mfc/controls-mfc.md) y [uso de CToolTipCtrl](../../mfc/using-ctooltipctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CToolTipCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="activate"></a>CToolTipCtrl:: Activate

Llame a esta función para activar o desactivar un control de información sobre herramientas.

```
void Activate(BOOL bActivate);
```

### <a name="parameters"></a>Parámetros

*bActivate*<br/>
Especifica si el control de información sobre herramientas se va a activar o desactivar.

### <a name="remarks"></a>Observaciones

Si *bActivate* es true, el control se activa; Si es FALSE, se desactiva.

Cuando hay un control de información sobre herramientas activo, la información sobre herramientas aparece cuando el cursor está en una herramienta que está registrada con el control. cuando está inactivo, la información sobre herramientas no aparece, incluso cuando el cursor está en una herramienta.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="addtool"></a>CToolTipCtrl:: AddTool

Registra una herramienta con el control de información sobre herramientas.

```
BOOL AddTool(
    CWnd* pWnd,
    UINT nIDText,
    LPCRECT lpRectTool = NULL,
    UINT_PTR nIDTool = 0);

BOOL AddTool(
    CWnd* pWnd,
    LPCTSTR lpszText = LPSTR_TEXTCALLBACK,
    LPCRECT lpRectTool = NULL,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero a la ventana que contiene la herramienta.

*nIDText*<br/>
IDENTIFICADOR del recurso de cadena que contiene el texto de la herramienta.

*lpRectTool*<br/>
Puntero a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que contiene coordenadas del rectángulo delimitador de la herramienta. Las coordenadas son relativas a la esquina superior izquierda del área cliente de la ventana identificada por *PWND*.

*nIDTool*<br/>
IDENTIFICADOR de la herramienta.

*lpszText*<br/>
Puntero al texto de la herramienta. Si este parámetro contiene el valor LPSTR_TEXTCALLBACK, TTN_NEEDTEXT mensajes de notificación van al elemento primario de la ventana a la que apunta *PWND* .

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Los parámetros *lpRectTool* y *nIDTool* deben ser válidos, o si *lpRectTool* es null, *nIDTool* debe ser 0.

Un control de información sobre herramientas puede asociarse a más de una herramienta. Llame a esta función para registrar una herramienta con el control de información sobre herramientas, de modo que la información almacenada en la información sobre herramientas se muestre cuando el cursor esté en la herramienta.

> [!NOTE]
>  No se puede establecer una información sobre herramientas en un control estático mediante `AddTool`.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="adjustrect"></a>CToolTipCtrl:: AdjustRect

Convierte entre el rectángulo de presentación del texto de un control ToolTip y su rectángulo de ventana.

```
BOOL AdjustRect(
    LPRECT lprc,
    BOOL bLarger = TRUE);
```

### <a name="parameters"></a>Parámetros

*lprc*<br/>
Puntero a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que contiene un rectángulo de la ventana de información sobre herramientas o un rectángulo de presentación de texto.

*bLarger*<br/>
Si es TRUE, *LPRC* se usa para especificar un rectángulo de presentación de texto y recibe el rectángulo de ventana correspondiente. Si es FALSE, *LPRC* se usa para especificar un rectángulo de ventana y recibe el rectángulo de presentación de texto correspondiente.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el rectángulo se ajusta correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Esta función miembro calcula el rectángulo de presentación de texto del control de información sobre herramientas desde el rectángulo de la ventana o el rectángulo de la ventana de información sobre herramientas necesario para mostrar un rectángulo de presentación de texto especificado.

Esta función miembro implementa el comportamiento del [TTM_ADJUSTRECT](/windows/win32/Controls/ttm-adjustrect)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="create"></a>CToolTipCtrl:: Create

Crea un control de información sobre herramientas y lo adjunta a un objeto `CToolTipCtrl`.

```
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Especifica la ventana primaria del control de información sobre herramientas, normalmente una `CDialog`. No debe ser NULL.

*dwStyle*<br/>
Especifica el estilo del control de información sobre herramientas. Vea la sección **comentarios** para obtener más información.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto de `CToolTipCtrl` se ha creado correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Una `CToolTipCtrl` se crea en dos pasos. En primer lugar, llame al constructor para construir el objeto `CToolTipCtrl` y, a continuación, llame a `Create` para crear el control de información sobre herramientas y adjuntarlo al objeto `CToolTipCtrl`.

El parámetro *dwStyle* puede ser cualquier combinación de [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles). Además, un control de información sobre herramientas tiene dos estilos específicos de clase: TTS_ALWAYSTIP y TTS_NOPREFIX.

|Estilo|Significado|
|-----------|-------------|
|TTS_ALWAYSTIP|Especifica que la información sobre herramientas aparecerá cuando el cursor esté en una herramienta, independientemente de si la ventana propietaria del control de información sobre herramientas está activa o inactiva. Sin este estilo, el control de información sobre herramientas aparece cuando la ventana propietaria de la herramienta está activa, pero no cuando está inactiva.|
|TTS_NOPREFIX|Este estilo evita que el sistema elimine el carácter de y comercial (&) de una cadena. Si un control de información sobre herramientas no tiene el estilo de TTS_NOPREFIX, el sistema quita automáticamente los caracteres de y comercial, lo que permite que una aplicación utilice la misma cadena como un elemento de menú y como texto en un control de información sobre herramientas.|

Un control de información sobre herramientas tiene los estilos de ventana WS_POPUP y WS_EX_TOOLWINDOW, independientemente de si se especifican al crear el control.

Para crear un control de información sobre herramientas con estilos extendidos de Windows, llame a [CToolTipCtrl:: CreateEx](#createex) en lugar de a `Create`.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="createex"></a>CToolTipCtrl:: CreateEx

Crea un control (una ventana secundaria) y lo asocia al objeto `CToolTipCtrl`.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwStyle = 0,
    DWORD dwStyleEx = 0);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*dwStyle*<br/>
Especifica el estilo del control de información sobre herramientas. Vea la sección **comentarios** de [Create](#create) para obtener más información.

*dwStyleEx*<br/>
Especifica el estilo extendido del control que se va a crear. Para obtener una lista de los estilos extendidos de Windows, consulte el parámetro *dwExStyle* para [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si es correcto; de lo contrario, 0.

### <a name="remarks"></a>Observaciones

Utilice `CreateEx` en lugar de `Create` para aplicar los estilos extendidos de Windows, especificados por el **WS_EX_** de prefacio de estilo extendido de Windows.

##  <a name="ctooltipctrl"></a>CToolTipCtrl:: CToolTipCtrl

Construye un objeto `CToolTipCtrl`.

```
CToolTipCtrl();
```

### <a name="remarks"></a>Observaciones

Debe llamar a `Create` después de construir el objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]

##  <a name="deltool"></a>CToolTipCtrl::D elTool

Quita la herramienta especificada por *PWND* y *nIDTool* de la colección de herramientas admitida por un control de información sobre herramientas.

```
void DelTool(
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero a la ventana que contiene la herramienta.

*nIDTool*<br/>
IDENTIFICADOR de la herramienta.

##  <a name="getbubblesize"></a>CToolTipCtrl:: GetBubbleSize

Recupera el tamaño de la información sobre herramientas.

```
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parámetros

*lpToolInfo*<br/>
Puntero a la estructura [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) de la información sobre herramientas.

### <a name="return-value"></a>Valor devuelto

Tamaño de la información sobre herramientas.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [TTM_GETBUBBLESIZE](/windows/win32/Controls/ttm-getbubblesize)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="getcurrenttool"></a>CToolTipCtrl:: GetCurrentTool

Recupera información, como el tamaño, la posición y el texto, de la ventana de información sobre herramientas que muestra el control ToolTip actual.

```
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*lpToolInfo*|enuncia Puntero a una estructura [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) que recibe información sobre la ventana de información sobre herramientas actual.|

### <a name="return-value"></a>Valor devuelto

TRUE si la información se recupera correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método envía el mensaje de [TTM_GETCURRENTTOOL](/windows/win32/Controls/ttm-getcurrenttool) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se recupera información sobre la ventana de información sobre herramientas actual.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]

##  <a name="getdelaytime"></a>CToolTipCtrl:: GetDelayTime

Recupera las duraciones iniciales, emergentes y de visualización que se establecen actualmente para un control de información sobre herramientas.

```
int GetDelayTime(DWORD dwDuration) const;
```

### <a name="parameters"></a>Parámetros

*dwDuration*<br/>
Marca que especifica el valor de duración que se recuperará. Este parámetro puede ser uno de los siguientes valores:

- TTDT_AUTOPOP recuperar el tiempo durante el que la ventana de información sobre herramientas permanece visible si el puntero es estacionario dentro del rectángulo delimitador de una herramienta.

- TTDT_INITIAL recuperar la cantidad de tiempo que el puntero debe permanecer estacionario dentro del rectángulo delimitador de una herramienta antes de que aparezca la ventana de información sobre herramientas.

- TTDT_RESHOW recuperar la cantidad de tiempo que tardan las ventanas de información de herramientas posteriores en aparecer cuando el puntero se mueve de una herramienta a otra.

### <a name="return-value"></a>Valor devuelto

Tiempo de retraso especificado, en milisegundos

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [TTM_GETDELAYTIME](/windows/win32/Controls/ttm-getdelaytime)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="getmargin"></a>CToolTipCtrl:: GetMargin

Recupera los márgenes superior, izquierdo, inferior y derecho establecidos para una ventana de información sobre herramientas.

```
void GetMargin(LPRECT lprc) const;
```

### <a name="parameters"></a>Parámetros

*lprc*<br/>
Dirección de una estructura de `RECT` que recibirá la información del margen. Los miembros de la estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) no definen un rectángulo delimitador. Para este mensaje, los miembros de la estructura se interpretan de la siguiente manera:

|Member|Representación|
|------------|--------------------|
|`top`|Distancia entre el borde superior y la parte superior del texto de información sobre herramientas, en píxeles.|
|`left`|Distancia entre el borde izquierdo y el final izquierdo del texto de la sugerencia, en píxeles.|
|`bottom`|Distancia entre el borde inferior y la parte inferior del texto de la sugerencia, en píxeles.|
|`right`|Distancia entre el borde derecho y el extremo derecho del texto de la sugerencia, en píxeles.|

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [TTM_GETMARGIN](/windows/win32/Controls/ttm-getmargin)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="getmaxtipwidth"></a>CToolTipCtrl:: GetMaxTipWidth

Recupera el ancho máximo de una ventana de información sobre herramientas.

```
int GetMaxTipWidth() const;
```

### <a name="return-value"></a>Valor devuelto

El ancho máximo de una ventana de información sobre herramientas.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [TTM_GETMAXTIPWIDTH](/windows/win32/Controls/ttm-getmaxtipwidth)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="gettext"></a>CToolTipCtrl:: GetText

Recupera el texto que mantiene un control de información sobre herramientas para una herramienta.

```
void GetText(
    CString& str,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Parámetros

*str*<br/>
Referencia a un objeto `CString` que recibe el texto de la herramienta.

*pWnd*<br/>
Puntero a la ventana que contiene la herramienta.

*nIDTool*<br/>
IDENTIFICADOR de la herramienta.

### <a name="remarks"></a>Observaciones

Los parámetros *PWND* y *nIDTool* identifican la herramienta. Si la herramienta se registró previamente con el control de información sobre herramientas a través de una llamada anterior a `CToolTipCtrl::AddTool`, se asigna el texto de la herramienta al objeto al que hace referencia el parámetro *Str* .

##  <a name="gettipbkcolor"></a>CToolTipCtrl:: GetTipBkColor

Recupera el color de fondo de una ventana de información sobre herramientas.

```
COLORREF GetTipBkColor() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de [COLORREF](/windows/win32/gdi/colorref) que representa el color de fondo.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [TTM_GETTIPBKCOLOR](/windows/win32/Controls/ttm-gettipbkcolor)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="gettiptextcolor"></a>CToolTipCtrl:: GetTipTextColor

Recupera el color del texto en una ventana de información sobre herramientas.

```
COLORREF GetTipTextColor() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de [COLORREF](/windows/win32/gdi/colorref) que representa el color del texto.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [TTM_GETTIPTEXTCOLOR](/windows/win32/Controls/ttm-gettiptextcolor)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="gettitle"></a>CToolTipCtrl:: GetTitle

Recupera el título del control de información sobre herramientas actual.

```
void GetTitle(PTTGETTITLE pttgt) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pttgt*|enuncia Puntero a una estructura [TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) que contiene información sobre el control ToolTip. Cuando este método devuelve, el miembro *pszTitle* de la estructura [TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) apunta al texto del título.|

### <a name="remarks"></a>Observaciones

Este método envía el mensaje de [TTM_GETTITLE](/windows/win32/Controls/ttm-gettitle) , que se describe en el Windows SDK.

##  <a name="gettoolcount"></a>CToolTipCtrl:: GetToolCount

Recupera un recuento de las herramientas registradas con el control de información sobre herramientas.

```
int GetToolCount() const;
```

### <a name="return-value"></a>Valor devuelto

Recuento de herramientas registradas con el control de información sobre herramientas.

##  <a name="gettoolinfo"></a>CToolTipCtrl:: GetToolInfo

Recupera la información que mantiene un control de información sobre herramientas sobre una herramienta.

```
BOOL GetToolInfo(
    CToolInfo& ToolInfo,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Parámetros

*ToolInfo*<br/>
Referencia a un objeto `TOOLINFO` que recibe el texto de la herramienta.

*pWnd*<br/>
Puntero a la ventana que contiene la herramienta.

*nIDTool*<br/>
IDENTIFICADOR de la herramienta.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Los miembros `hwnd` y `uId` de la estructura [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) a la que hace referencia *CToolInfo* identifican la herramienta. Si la herramienta se ha registrado con el control de información sobre herramientas a través de una llamada anterior a `AddTool`, la estructura de `TOOLINFO` se rellena con información sobre la herramienta.

##  <a name="hittest"></a>CToolTipCtrl:: HitTest

Comprueba un punto para determinar si está dentro del rectángulo delimitador de la herramienta especificada y, en caso afirmativo, recupera información sobre la herramienta.

```
BOOL HitTest(
    CWnd* pWnd,
    CPoint pt,
    LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero a la ventana que contiene la herramienta.

*pt*<br/>
Puntero a un objeto `CPoint` que contiene las coordenadas del punto que se va a probar.

*lpToolInfo*<br/>
Puntero a la estructura [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) que contiene información sobre la herramienta.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el punto especificado por la información de la prueba de posicionamiento está dentro del rectángulo delimitador de la herramienta. de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Si esta función devuelve un valor distinto de cero, la estructura a la que apunta *lpToolInfo* se rellena con información sobre la herramienta en cuyo rectángulo se encuentra el punto.

La estructura de `TTHITTESTINFO` se define de la siguiente manera:

```cpp
typedef struct _TT_HITTESTINFO { // tthti
    HWND hwnd;   // handle of tool or window with tool
    POINT pt;    // client coordinates of point to test
    TOOLINFO ti; // receives information about the tool
} TTHITTESTINFO, FAR * LPHITTESTINFO;
```

- `hwnd`

   Especifica el identificador de la herramienta.

- `pt`

   Especifica las coordenadas de un punto si el punto está en el rectángulo delimitador de la herramienta.

- `ti`

   Información sobre la herramienta. Para obtener más información sobre la estructura de `TOOLINFO`, vea [CToolTipCtrl:: GetToolInfo](#gettoolinfo).

##  <a name="pop"></a>CToolTipCtrl::P op

Quita de la vista una ventana de información sobre herramientas mostrada.

```
void Pop();
```

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [TTM_POP](/windows/win32/Controls/ttm-pop)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="popup"></a>CToolTipCtrl::P opup

Hace que el control ToolTip actual se muestre en las coordenadas del último mensaje del mouse.

```
void Popup();
```

### <a name="remarks"></a>Observaciones

Este método envía el mensaje de [TTM_POPUP](/windows/win32/Controls/ttm-popup) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra una ventana de información sobre herramientas.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]

##  <a name="relayevent"></a>CToolTipCtrl:: RelayEvent

Pasa un mensaje del mouse a un control de información sobre herramientas para su procesamiento.

```
void RelayEvent(LPMSG lpMsg);
```

### <a name="parameters"></a>Parámetros

*lpMsg*<br/>
Puntero a una estructura [MSG](/windows/win32/api/winuser/ns-winuser-msg) que contiene el mensaje que se va a retransmitir.

### <a name="remarks"></a>Observaciones

Un control de información sobre herramientas solo procesa los mensajes siguientes, que se le envían por `RelayEvent`:

|WM_LBUTTONDOWN|WM_MOUSEMOVE|
|---------------------|-------------------|
|WM_LBUTTONUP|WM_RBUTTONDOWN|
|WM_MBUTTONDOWN|WM_RBUTTONUP|
|WM_MBUTTONUP||

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="setdelaytime"></a>CToolTipCtrl:: SetDelayTime

Establece el tiempo de retraso para un control de información sobre herramientas.

```
void SetDelayTime(UINT nDelay);

void SetDelayTime(
    DWORD dwDuration,
    int iTime);
```

### <a name="parameters"></a>Parámetros

*nDelay*<br/>
Especifica el nuevo tiempo de retardo, en milisegundos.

*dwDuration*<br/>
Marca que especifica el valor de duración que se recuperará. Vea [CToolTipCtrl:: GetDelayTime](#getdelaytime) para obtener una descripción de los valores válidos.

*iTime*<br/>
Tiempo de retraso especificado, en milisegundos.

### <a name="remarks"></a>Observaciones

El tiempo de retardo es la cantidad de tiempo que el cursor debe permanecer en una herramienta antes de que aparezca la ventana de información sobre herramientas. El tiempo de retraso predeterminado es de 500 milisegundos.

##  <a name="setmargin"></a>CToolTipCtrl:: SetMargin

Establece los márgenes superior, izquierdo, inferior y derecho de una ventana de información sobre herramientas.

```
void SetMargin(LPRECT lprc);
```

### <a name="parameters"></a>Parámetros

*lprc*<br/>
Dirección de una estructura de `RECT` que contiene la información de margen que se va a establecer. Los miembros de la estructura `RECT` no definen un rectángulo delimitador. Vea [CToolTipCtrl:: GetMargin](#getmargin) para obtener una descripción de la información del margen.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [TTM_SETMARGIN](/windows/win32/Controls/ttm-setmargin)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="setmaxtipwidth"></a>CToolTipCtrl:: SetMaxTipWidth

Establece el ancho máximo de una ventana de información sobre herramientas.

```
int SetMaxTipWidth(int iWidth);
```

### <a name="parameters"></a>Parámetros

*iWidth*<br/>
Ancho máximo de la ventana de información sobre herramientas que se va a establecer.

### <a name="return-value"></a>Valor devuelto

El ancho máximo de la sugerencia anterior.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [TTM_SETMAXTIPWIDTH](/windows/win32/Controls/ttm-setmaxtipwidth)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="settipbkcolor"></a>CToolTipCtrl:: SetTipBkColor

Establece el color de fondo en una ventana de información sobre herramientas.

```
void SetTipBkColor(COLORREF clr);
```

### <a name="parameters"></a>Parámetros

*CLR*<br/>
Nuevo color de fondo.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [TTM_SETTIPBKCOLOR](/windows/win32/Controls/ttm-settipbkcolor)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="settiptextcolor"></a>CToolTipCtrl:: SetTipTextColor

Establece el color del texto en una ventana de información sobre herramientas.

```
void SetTipTextColor(COLORREF clr);
```

### <a name="parameters"></a>Parámetros

*CLR*<br/>
Nuevo color del texto.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [TTM_SETTIPTEXTCOLOR](/windows/win32/Controls/ttm-settiptextcolor)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="settitle"></a>CToolTipCtrl:: SetTitle

Agrega un icono estándar y una cadena de título a una información sobre herramientas.

```
BOOL SetTitle(
    UINT uIcon,
    LPCTSTR lpstrTitle);
```

### <a name="parameters"></a>Parámetros

*uIcon*<br/>
Vea el *icono* en [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle) en el Windows SDK.

*lpstrTitle*<br/>
Puntero a la cadena de título.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="settoolinfo"></a>CToolTipCtrl:: SetToolInfo

Establece la información que mantiene una información sobre herramientas para una herramienta.

```
void SetToolInfo(LPTOOLINFO lpToolInfo);
```

### <a name="parameters"></a>Parámetros

*lpToolInfo*<br/>
Puntero a una estructura [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) que especifica la información que se va a establecer.

##  <a name="settoolrect"></a>CToolTipCtrl:: SetToolRect

Establece un nuevo rectángulo delimitador para una herramienta.

```
void SetToolRect(
    CWnd* pWnd,
    UINT_PTR nIDTool,
    LPCRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero a la ventana que contiene la herramienta.

*nIDTool*<br/>
IDENTIFICADOR de la herramienta.

*lpRect*<br/>
Puntero a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que especifica el nuevo rectángulo delimitador.

##  <a name="setwindowtheme"></a>CToolTipCtrl:: SetWindowTheme

Establece el estilo visual de la ventana de información sobre herramientas.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parámetros

*pszSubAppName*<br/>
Puntero a una cadena Unicode que contiene el estilo visual que se va a establecer.

### <a name="return-value"></a>Valor devuelto

No se utiliza el valor devuelto.

### <a name="remarks"></a>Observaciones

Esta función miembro emula la funcionalidad del mensaje de [TTM_SETWINDOWTHEME](/windows/win32/Controls/ttm-setwindowtheme) , como se describe en el Windows SDK.

##  <a name="update"></a>CToolTipCtrl:: Update

Obliga a que se vuelva a dibujar la herramienta actual.

```
void Update();
```

##  <a name="updatetiptext"></a>CToolTipCtrl:: UpdateTipText

Actualiza el texto de información sobre herramientas para las herramientas de este control.

```
void UpdateTipText(
    LPCTSTR lpszText,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);

void UpdateTipText(
    UINT nIDText,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
Puntero al texto de la herramienta.

*pWnd*<br/>
Puntero a la ventana que contiene la herramienta.

*nIDTool*<br/>
IDENTIFICADOR de la herramienta.

*nIDText*<br/>
IDENTIFICADOR del recurso de cadena que contiene el texto de la herramienta.

## <a name="see-also"></a>Consulte también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CToolBar (clase)](../../mfc/reference/ctoolbar-class.md)
