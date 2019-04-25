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
ms.openlocfilehash: 6055926e05f8a7f9fbecec113e859d08e6b6e636
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323679"
---
# <a name="ctooltipctrl-class"></a>CToolTipCtrl Class

Encapsula la funcionalidad de un "control de información sobre herramientas", una pequeña ventana emergente que muestra una única línea de texto que describe el propósito de una herramienta de una aplicación.

## <a name="syntax"></a>Sintaxis

```
class CToolTipCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CToolTipCtrl::CToolTipCtrl](#ctooltipctrl)|Construye un objeto `CToolTipCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CToolTipCtrl::Activate](#activate)|Activa y desactiva el control de información sobre herramientas.|
|[CToolTipCtrl::AddTool](#addtool)|Registra una herramienta con el control de información sobre herramientas.|
|[CToolTipCtrl::AdjustRect](#adjustrect)|Convierte entre el texto del control de información sobre herramientas muestra el rectángulo y su rectángulo de la ventana.|
|[CToolTipCtrl::Create](#create)|Crea un control y lo adjunta a un `CToolTipCtrl` objeto.|
|[CToolTipCtrl::CreateEx](#createex)|Crea un control con los estilos extendidos de Windows especificados y lo adjunta a un `CToolTipCtrl` objeto.|
|[CToolTipCtrl::DelTool](#deltool)|Quita una herramienta desde el control de información sobre herramientas.|
|[CToolTipCtrl::GetBubbleSize](#getbubblesize)|Recupera el tamaño de la información sobre herramientas.|
|[CToolTipCtrl::GetCurrentTool](#getcurrenttool)|Recupera información, como el tamaño, posición y texto de la ventana de información sobre herramientas que muestra el control de información sobre herramientas actual.|
|[CToolTipCtrl::GetDelayTime](#getdelaytime)|Recupera el inicial, la ventana emergente y reshow control de información sobre las duraciones que están establecidas actualmente para una herramienta.|
|[CToolTipCtrl::GetMargin](#getmargin)|Recupera la parte superior, izquierdo, inferior y los márgenes derechos que se establecen para una ventana de sugerencia de la herramienta.|
|[CToolTipCtrl::GetMaxTipWidth](#getmaxtipwidth)|Recupera el ancho máximo de una ventana de información sobre herramientas.|
|[CToolTipCtrl::GetText](#gettext)|Recupera el texto que se mantiene un control para una herramienta.|
|[CToolTipCtrl::GetTipBkColor](#gettipbkcolor)|Recupera el color de fondo en una ventana de información sobre herramientas.|
|[CToolTipCtrl::GetTipTextColor](#gettiptextcolor)|Recupera el color del texto en una ventana de información sobre herramientas.|
|[CToolTipCtrl::GetTitle](#gettitle)|Recupera el título del control de información sobre herramientas actual.|
|[CToolTipCtrl::GetToolCount](#gettoolcount)|Recupera un recuento de las herramientas mantenida por un control de información sobre herramientas.|
|[CToolTipCtrl::GetToolInfo](#gettoolinfo)|Recupera la información que mantiene un control sobre una herramienta.|
|[CToolTipCtrl::HitTest](#hittest)|Prueba en un punto para determinar si está dentro del rectángulo delimitador de la herramienta especificada. Si es así, recupera información acerca de la herramienta.|
|[CToolTipCtrl::Pop](#pop)|Quita una ventana de sugerencia de la herramienta muestra la vista.|
|[CToolTipCtrl::Popup](#popup)|Hace que el control de información sobre herramientas actual que se muestra en las coordenadas del último mensaje de mouse.|
|[CToolTipCtrl::RelayEvent](#relayevent)|Pasa un mensaje del mouse a un control de información sobre herramientas para el procesamiento.|
|[CToolTipCtrl::SetDelayTime](#setdelaytime)|Establece la inicial, emergente y reshow las duraciones de un control de información sobre herramientas.|
|[CToolTipCtrl::SetMargin](#setmargin)|Establece la parte superior, izquierda, inferior y los márgenes derechos de una ventana de sugerencia de la herramienta.|
|[CToolTipCtrl::SetMaxTipWidth](#setmaxtipwidth)|Establece el ancho máximo de una ventana de información sobre herramientas.|
|[CToolTipCtrl::SetTipBkColor](#settipbkcolor)|Establece el color de fondo en una ventana de información sobre herramientas.|
|[CToolTipCtrl::SetTipTextColor](#settiptextcolor)|Establece el color del texto en una ventana de información sobre herramientas.|
|[CToolTipCtrl::SetTitle](#settitle)|Agrega una cadena de título y el icono estándar para una información sobre herramientas.|
|[CToolTipCtrl::SetToolInfo](#settoolinfo)|Establece la información que mantiene una información sobre herramientas para una herramienta.|
|[CToolTipCtrl::SetToolRect](#settoolrect)|Establece un nuevo rectángulo delimitador para una herramienta.|
|[CToolTipCtrl::SetWindowTheme](#setwindowtheme)|Establece el estilo visual de la ventana de información sobre herramientas.|
|[CToolTipCtrl::Update](#update)|Fuerza la herramienta actual se vuelva a dibujar.|
|[CToolTipCtrl::UpdateTipText](#updatetiptext)|Establece el texto de sugerencia para una herramienta.|

## <a name="remarks"></a>Comentarios

Una "herramienta" es cualquier ventana, como una ventana secundaria de control o un área rectangular definida por la aplicación dentro del área cliente de una ventana. Una información sobre herramientas está oculta la mayoría de las veces, que aparecen solo cuando el usuario coloca el cursor sobre una herramienta y deja allí durante aproximadamente medio segundo. La información sobre herramientas aparece cerca del cursor y desaparece cuando el usuario hace clic en un botón del mouse o mueve el cursor de la herramienta.

`CToolTipCtrl` proporciona la funcionalidad al control de la hora inicial y la duración de la información sobre herramientas, el ancho de los márgenes que rodean el texto de sugerencia, el ancho de la propia ventana de sugerencia de herramienta y el color de fondo y de texto de la información sobre herramientas. Control de información sobre una sola herramienta puede proporcionar información de más de una herramienta.

La `CToolTipCtrl` clase proporciona la funcionalidad del control de sugerencia de herramienta común de Windows. Este control (y, por tanto, la `CToolTipCtrl` clase) está disponible solo para programas que se ejecutan en versiones de Windows 95/98 y Windows NT 3.51 y versiones posteriores.

Para obtener más información acerca de cómo habilitar información sobre herramientas, consulte [información sobre herramientas en Windows no derivadas de CFrameWnd](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).

Para obtener más información sobre el uso de `CToolTipCtrl`, consulte [controles](../../mfc/controls-mfc.md) y [uso de CToolTipCtrl](../../mfc/using-ctooltipctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CToolTipCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="activate"></a>  CToolTipCtrl::Activate

Llame a esta función para activar o desactivar un control.

```
void Activate(BOOL bActivate);
```

### <a name="parameters"></a>Parámetros

*bActivate*<br/>
Especifica si el control está activado o desactivado.

### <a name="remarks"></a>Comentarios

Si *bActivate* es TRUE, se activa el control; si es FALSE, se está desactivado.

Cuando un control de información sobre herramientas está activo, la información de información sobre herramientas aparece cuando el cursor esté sobre una herramienta que se registra con el control; Cuando está inactivo, la información de sugerencia de la herramienta no aparece, incluso cuando el cursor esté sobre una herramienta.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="addtool"></a>  CToolTipCtrl::AddTool

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
Id. del recurso de cadena que contiene el texto de la herramienta.

*lpRectTool*<br/>
Puntero a un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura que contiene las coordenadas de la herramienta rectángulo delimitador. Las coordenadas son relativas a la esquina superior izquierda del área cliente de la ventana identificado por *conquistado*.

*nIDTool*<br/>
Id. de la herramienta.

*lpszText*<br/>
Puntero al texto de la herramienta. Si este parámetro contiene el valor LPSTR_TEXTCALLBACK, mensajes de notificación TTN_NEEDTEXT ir al elemento primario de la ventana que *conquistado* apunta a.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El *lpRectTool* y *nIDTool* parámetros deben ser válidos, o si *lpRectTool* es NULL, *nIDTool* debe ser 0.

Un control puede asociarse con más de una herramienta. Llame a esta función para registrar una herramienta con el control de información sobre herramientas, para que se muestre la información almacenada en la información sobre herramientas cuando el cursor está en la herramienta.

> [!NOTE]
>  No se puede establecer una información sobre herramientas para un control estático mediante `AddTool`.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="adjustrect"></a>  CToolTipCtrl::AdjustRect

Convierte entre el texto de un control de información sobre herramientas muestra el rectángulo y su rectángulo de la ventana.

```
BOOL AdjustRect(
    LPRECT lprc,
    BOOL bLarger = TRUE);
```

### <a name="parameters"></a>Parámetros

*lprc*<br/>
Puntero a un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura que contiene un rectángulo de ventana de sugerencia de herramienta o un rectángulo de presentación de texto.

*bLarger*<br/>
Si es TRUE, *lprc* se usa para especificar un rectángulo de presentación del texto, y recibe el rectángulo de la ventana correspondiente. Si es FALSE, *lprc* se usa para especificar un rectángulo de la ventana, y recibe el rectángulo de presentación de texto correspondientes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el rectángulo se ajustó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función miembro calcula el rectángulo de presentación de texto del control de información sobre herramientas de su rectángulo de la ventana o el rectángulo de ventana de sugerencia herramienta necesaria para mostrar un rectángulo de presentación de texto especificado.

Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_ADJUSTRECT](/windows/desktop/Controls/ttm-adjustrect), tal y como se describe en el SDK de Windows.

##  <a name="create"></a>  CToolTipCtrl::Create

Crea un control y lo adjunta a un `CToolTipCtrl` objeto.

```
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Especifica la herramienta sugerencia ventana del control primario, normalmente un `CDialog`. No debe ser NULL.

*dwStyle*<br/>
Especifica el estilo del control de información sobre herramientas. Consulte la **comentarios** sección para obtener más información.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el `CToolTipCtrl` objeto se creó correctamente; en caso contrario, 0.

### <a name="remarks"></a>Comentarios

Construir un `CToolTipCtrl` en dos pasos. En primer lugar, llame al constructor para construir el `CToolTipCtrl` objeto y, a continuación, llame a `Create` para crear el control y adjuntarlo a la `CToolTipCtrl` objeto.

El *dwStyle* parámetro puede ser cualquier combinación de [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles). Además, un control de información sobre herramientas tiene dos estilos de clase específico: TTS_ALWAYSTIP y TTS_NOPREFIX.

|Estilo|Significado|
|-----------|-------------|
|TTS_ALWAYSTIP|Especifica que la información sobre herramientas aparecerá cuando el cursor esté sobre una herramienta, independientemente de si la ventana propietaria del control de información sobre herramientas está activa o inactiva. Sin este estilo, el control de información sobre herramientas aparece cuando está activa la ventana propietaria de la herramienta, pero no cuando está inactivo.|
|TTS_NOPREFIX|Este estilo impide que el sistema de eliminación de los caracteres de una cadena de "y" comercial (&). Si un control no tiene el estilo TTS_NOPREFIX, el sistema quita automáticamente los caracteres "y" comercial, lo que permite una aplicación para usar la misma cadena como un elemento de menú de ambos y como texto en un control de información sobre herramientas.|

Un control de información sobre herramientas tiene los estilos de ventana WS_POPUP y WS_EX_TOOLWINDOW, aunque no se especifique al crear el control.

Para crear un control con los estilos extendidos de windows, llame a [CToolTipCtrl::CreateEx](#createex) en lugar de `Create`.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="createex"></a>  CToolTipCtrl::CreateEx

Crea un control (una ventana secundaria) y asócielo con el `CToolTipCtrl` objeto.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwStyle = 0,
    DWORD dwStyleEx = 0);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Un puntero a la ventana que es primario del control.

*dwStyle*<br/>
Especifica el estilo del control de información sobre herramientas. Consulte la **comentarios** sección de [crear](#create) para obtener más información.

*dwStyleEx*<br/>
Especifica el estilo extendido del control que se está creando. Para obtener una lista de los estilos extendidos de Windows, consulte el *dwExStyle* parámetro [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

0 en caso contrario, es distinto de cero si se realiza correctamente.

### <a name="remarks"></a>Comentarios

Use `CreateEx` en lugar de `Create` para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.

##  <a name="ctooltipctrl"></a>  CToolTipCtrl::CToolTipCtrl

Construye un objeto `CToolTipCtrl`.

```
CToolTipCtrl();
```

### <a name="remarks"></a>Comentarios

Debe llamar a `Create` después de construir el objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]

##  <a name="deltool"></a>  CToolTipCtrl::DelTool

Quita la herramienta especificada por *conquistado* y *nIDTool* de la colección de herramientas compatibles con un control de información sobre herramientas.

```
void DelTool(
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero a la ventana que contiene la herramienta.

*nIDTool*<br/>
Id. de la herramienta.

##  <a name="getbubblesize"></a>  CToolTipCtrl::GetBubbleSize

Recupera el tamaño de la información sobre herramientas.

```
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parámetros

*lpToolInfo*<br/>
Un puntero a la punta de la herramienta [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) estructura.

### <a name="return-value"></a>Valor devuelto

El tamaño de la información sobre herramientas.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_GETBUBBLESIZE](/windows/desktop/Controls/ttm-getbubblesize), tal y como se describe en el SDK de Windows.

##  <a name="getcurrenttool"></a>  CToolTipCtrl::GetCurrentTool

Recupera información, como el tamaño, posición y texto de la ventana de información sobre herramientas muestra el control de información sobre herramientas actual.

```
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*lpToolInfo*|[out] Puntero a un [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) estructura que recibe información acerca de la ventana de información sobre herramientas actual.|

### <a name="return-value"></a>Valor devuelto

TRUE si la información se recupera correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el [TTM_GETCURRENTTOOL](/windows/desktop/Controls/ttm-getcurrenttool) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente recupera información acerca de la ventana de información sobre herramientas actual.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]

##  <a name="getdelaytime"></a>  CToolTipCtrl::GetDelayTime

Recupera la inicial, emergente y reshow duraciones establecidas para un control de información sobre herramientas.

```
int GetDelayTime(DWORD dwDuration) const;
```

### <a name="parameters"></a>Parámetros

*dwDuration*<br/>
Marca que especifica qué valor de duración se recuperarán. Este parámetro puede ser uno de los siguientes valores:

- Recuperar TTDT_AUTOPOP el período de tiempo de ventana de información sobre la herramienta permanece visible si el puntero se detiene dentro del rectángulo delimitador de la herramienta.

- Recuperar TTDT_INITIAL el período de tiempo que debe permanecer el puntero dentro del rectángulo de la herramienta antes de la ventana de información sobre herramientas aparece.

- TTDT_RESHOW recuperar la longitud de tiempo que tarda posteriores ventanas de sugerencia que aparezca cuando el puntero se mueve desde una herramienta a otra.

### <a name="return-value"></a>Valor devuelto

El tiempo de retraso especificado, en milisegundos

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_GETDELAYTIME](/windows/desktop/Controls/ttm-getdelaytime), tal y como se describe en el SDK de Windows.

##  <a name="getmargin"></a>  CToolTipCtrl::GetMargin

Recupera la parte superior, izquierdo, inferior y derechos márgenes establecidos para una ventana de información sobre herramientas.

```
void GetMargin(LPRECT lprc) const;
```

### <a name="parameters"></a>Parámetros

*lprc*<br/>
Dirección de un `RECT` estructura que recibirá la información del margen. Los miembros de la [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura no define un rectángulo delimitador. Con el fin de este mensaje, los miembros de estructura se interpretan como sigue:

|Miembro|Representación|
|------------|--------------------|
|`top`|Distancia entre el borde superior y la parte superior del texto de sugerencia, en píxeles.|
|`left`|Distancia entre el borde izquierdo y el extremo izquierdo del texto de sugerencia, en píxeles.|
|`bottom`|Distancia entre el borde inferior y la parte inferior del texto de sugerencia, en píxeles.|
|`right`|Distancia entre el borde derecho y el extremo derecho del texto de sugerencia, en píxeles.|

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_GETMARGIN](/windows/desktop/Controls/ttm-getmargin), tal y como se describe en el SDK de Windows.

##  <a name="getmaxtipwidth"></a>  CToolTipCtrl::GetMaxTipWidth

Recupera el ancho máximo de una ventana de información sobre herramientas.

```
int GetMaxTipWidth() const;
```

### <a name="return-value"></a>Valor devuelto

El ancho máximo de una ventana de información sobre herramientas.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_GETMAXTIPWIDTH](/windows/desktop/Controls/ttm-getmaxtipwidth), tal y como se describe en el SDK de Windows.

##  <a name="gettext"></a>  CToolTipCtrl::GetText

Recupera el texto que se mantiene un control para una herramienta.

```
void GetText(
    CString& str,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Parámetros

*str*<br/>
Hacer referencia a un `CString` objeto que recibe el texto de la herramienta.

*pWnd*<br/>
Puntero a la ventana que contiene la herramienta.

*nIDTool*<br/>
Id. de la herramienta.

### <a name="remarks"></a>Comentarios

El *conquistado* y *nIDTool* parámetros identifican la herramienta. Si esa herramienta se ha registrado anteriormente con el control de información sobre herramientas a través de una llamada anterior a `CToolTipCtrl::AddTool`, el objeto al que hace referencia el *str* parámetro se asigna el texto de la herramienta.

##  <a name="gettipbkcolor"></a>  CToolTipCtrl::GetTipBkColor

Recupera el color de fondo en una ventana de información sobre herramientas.

```
COLORREF GetTipBkColor() const;
```

### <a name="return-value"></a>Valor devuelto

Un [COLORREF](/windows/desktop/gdi/colorref) valor que representa el color de fondo.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_GETTIPBKCOLOR](/windows/desktop/Controls/ttm-gettipbkcolor), tal y como se describe en el SDK de Windows.

##  <a name="gettiptextcolor"></a>  CToolTipCtrl::GetTipTextColor

Recupera el color del texto en una ventana de información sobre herramientas.

```
COLORREF GetTipTextColor() const;
```

### <a name="return-value"></a>Valor devuelto

Un [COLORREF](/windows/desktop/gdi/colorref) valor que representa el color del texto.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_GETTIPTEXTCOLOR](/windows/desktop/Controls/ttm-gettiptextcolor), tal y como se describe en el SDK de Windows.

##  <a name="gettitle"></a>  CToolTipCtrl::GetTitle

Recupera el título del control de información sobre herramientas actual.

```
void GetTitle(PTTGETTITLE pttgt) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pttgt*|[out] Puntero a un [TTGETTITLE](/windows/desktop/api/commctrl/ns-commctrl-_ttgettitle) estructura que contiene información sobre el control ToolTip. Cuando este método finaliza, el *pszTitle* miembro de la [TTGETTITLE](/windows/desktop/api/commctrl/ns-commctrl-_ttgettitle) estructura señala el texto del título.|

### <a name="remarks"></a>Comentarios

Este método envía el [TTM_GETTITLE](/windows/desktop/Controls/ttm-gettitle) mensaje, que se describe en el SDK de Windows.

##  <a name="gettoolcount"></a>  CToolTipCtrl::GetToolCount

Recupera un recuento de las herramientas que se registra con el control de información sobre herramientas.

```
int GetToolCount() const;
```

### <a name="return-value"></a>Valor devuelto

Un recuento de herramientas registrado con el control de información sobre herramientas.

##  <a name="gettoolinfo"></a>  CToolTipCtrl::GetToolInfo

Recupera la información que mantiene un control sobre una herramienta.

```
BOOL GetToolInfo(
    CToolInfo& ToolInfo,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Parámetros

*ToolInfo*<br/>
Hacer referencia a un `TOOLINFO` objeto que recibe el texto de la herramienta.

*pWnd*<br/>
Puntero a la ventana que contiene la herramienta.

*nIDTool*<br/>
Id. de la herramienta.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El `hwnd` y `uId` los miembros de la [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) estructura al que hace referencia *CToolInfo* identificar la herramienta. Si esa herramienta se ha registrado con el control de información sobre herramientas a través de una llamada anterior a `AddTool`, el `TOOLINFO` estructura se rellena con información sobre la herramienta.

##  <a name="hittest"></a>  CToolTipCtrl::HitTest

Prueba en un punto para determinar si está dentro del rectángulo delimitador de la herramienta especificada y, si es así, recuperar información acerca de la herramienta.

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
Puntero a un `CPoint` objeto que contiene las coordenadas del punto que va a probarse.

*lpToolInfo*<br/>
Puntero a [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) estructura que contiene información acerca de la herramienta.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el punto especificado por la información de la prueba de posicionamiento está dentro del rectángulo delimitador de la herramienta; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Si esta función devuelve un valor distinto de cero, la estructura que apunta *lpToolInfo* se rellena con información sobre la herramienta dentro cuyo rectángulo se encuentra el punto.

El `TTHITTESTINFO` estructura se define como sigue:

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

   Especifica las coordenadas de un punto, si el punto está en la herramienta rectángulo delimitador.

- `ti`

   Información acerca de la herramienta. Para obtener más información sobre la `TOOLINFO` estructura, vea [CToolTipCtrl::GetToolInfo](#gettoolinfo).

##  <a name="pop"></a>  CToolTipCtrl::Pop

Quita una ventana de sugerencia de la herramienta muestra la vista.

```
void Pop();
```

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_POP](/windows/desktop/Controls/ttm-pop), tal y como se describe en el SDK de Windows.

##  <a name="popup"></a>  CToolTipCtrl::Popup

Hace que el control de información sobre herramientas actual que se muestra en las coordenadas del último mensaje de mouse.

```
void Popup();
```

### <a name="remarks"></a>Comentarios

Este método envía el [TTM_POPUP](/windows/desktop/Controls/ttm-popup) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra una ventana de información sobre herramientas.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]

##  <a name="relayevent"></a>  CToolTipCtrl::RelayEvent

Pasa un mensaje del mouse a un control de información sobre herramientas para el procesamiento.

```
void RelayEvent(LPMSG lpMsg);
```

### <a name="parameters"></a>Parámetros

*lpMsg*<br/>
Puntero a un [MSG](/windows/desktop/api/winuser/ns-winuser-msg) estructura que contiene el mensaje de retransmisión.

### <a name="remarks"></a>Comentarios

Un control procesa sólo los mensajes siguientes, que se envían a él por `RelayEvent`:

|WM_LBUTTONDOWN|WM_MOUSEMOVE|
|---------------------|-------------------|
|WM_LBUTTONUP|WM_RBUTTONDOWN|
|WM_MBUTTONDOWN|WM_RBUTTONUP|
|WM_MBUTTONUP||

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="setdelaytime"></a>  CToolTipCtrl::SetDelayTime

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
Marca que especifica qué valor de duración se recuperarán. Consulte [CToolTipCtrl::GetDelayTime](#getdelaytime) para obtener una descripción de los valores válidos.

*iTime*<br/>
El tiempo de retraso especificado, en milisegundos.

### <a name="remarks"></a>Comentarios

El tiempo de retraso es el período de tiempo que debe permanecer el cursor sobre una herramienta antes de que aparezca la ventana de información sobre herramientas. El tiempo de retraso predeterminado es 500 milisegundos.

##  <a name="setmargin"></a>  CToolTipCtrl::SetMargin

Establece la parte superior, izquierda, inferior y los márgenes derechos de una ventana de sugerencia de la herramienta.

```
void SetMargin(LPRECT lprc);
```

### <a name="parameters"></a>Parámetros

*lprc*<br/>
Dirección de un `RECT` estructura que contiene la información del margen debe establecerse. Los miembros de la `RECT` estructura no define un rectángulo delimitador. Consulte [CToolTipCtrl::GetMargin](#getmargin) para obtener una descripción de la información del margen.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_SETMARGIN](/windows/desktop/Controls/ttm-setmargin), tal y como se describe en el SDK de Windows.

##  <a name="setmaxtipwidth"></a>  CToolTipCtrl::SetMaxTipWidth

Establece el ancho máximo de una ventana de información sobre herramientas.

```
int SetMaxTipWidth(int iWidth);
```

### <a name="parameters"></a>Parámetros

*iWidth*<br/>
El ancho de ventana de sugerencia herramienta máximo debe establecerse.

### <a name="return-value"></a>Valor devuelto

El ancho máximo sugerencia anterior.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_SETMAXTIPWIDTH](/windows/desktop/Controls/ttm-setmaxtipwidth), tal y como se describe en el SDK de Windows.

##  <a name="settipbkcolor"></a>  CToolTipCtrl::SetTipBkColor

Establece el color de fondo en una ventana de información sobre herramientas.

```
void SetTipBkColor(COLORREF clr);
```

### <a name="parameters"></a>Parámetros

*clr*<br/>
El nuevo color de fondo.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_SETTIPBKCOLOR](/windows/desktop/Controls/ttm-settipbkcolor), tal y como se describe en el SDK de Windows.

##  <a name="settiptextcolor"></a>  CToolTipCtrl::SetTipTextColor

Establece el color del texto en una ventana de información sobre herramientas.

```
void SetTipTextColor(COLORREF clr);
```

### <a name="parameters"></a>Parámetros

*clr*<br/>
Color del texto nuevo.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_SETTIPTEXTCOLOR](/windows/desktop/Controls/ttm-settiptextcolor), tal y como se describe en el SDK de Windows.

##  <a name="settitle"></a>  CToolTipCtrl::SetTitle

Agrega una cadena de título y el icono estándar para una información sobre herramientas.

```
BOOL SetTitle(
    UINT uIcon,
    LPCTSTR lpstrTitle);
```

### <a name="parameters"></a>Parámetros

*uIcon*<br/>
Consulte *icono* en [TTM_SETTITLE](/windows/desktop/Controls/ttm-settitle) en el SDK de Windows.

*lpstrTitle*<br/>
Puntero a la cadena de título.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_SETTITLE](/windows/desktop/Controls/ttm-settitle), tal y como se describe en el SDK de Windows.

##  <a name="settoolinfo"></a>  CToolTipCtrl::SetToolInfo

Establece la información que mantiene una información sobre herramientas para una herramienta.

```
void SetToolInfo(LPTOOLINFO lpToolInfo);
```

### <a name="parameters"></a>Parámetros

*lpToolInfo*<br/>
Un puntero a un [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) estructura que especifica la información para establecer.

##  <a name="settoolrect"></a>  CToolTipCtrl::SetToolRect

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
Id. de la herramienta.

*lpRect*<br/>
Puntero a un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura que especifica el nuevo rectángulo delimitador.

##  <a name="setwindowtheme"></a>  CToolTipCtrl::SetWindowTheme

Establece el estilo visual de la ventana de información sobre herramientas.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parámetros

*pszSubAppName*<br/>
Un puntero a una cadena Unicode que contiene el estilo visual que establezca.

### <a name="return-value"></a>Valor devuelto

No se utiliza el valor devuelto.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad de la [TTM_SETWINDOWTHEME](/windows/desktop/Controls/ttm-setwindowtheme) del mensaje, como se describe en el SDK de Windows.

##  <a name="update"></a>  CToolTipCtrl::Update

Fuerza la herramienta actual se vuelva a dibujar.

```
void Update();
```

##  <a name="updatetiptext"></a>  CToolTipCtrl::UpdateTipText

Actualiza el texto de sugerencia para las herramientas de este control.

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
Id. de la herramienta.

*nIDText*<br/>
Id. del recurso de cadena que contiene el texto de la herramienta.

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CToolBar (clase)](../../mfc/reference/ctoolbar-class.md)
