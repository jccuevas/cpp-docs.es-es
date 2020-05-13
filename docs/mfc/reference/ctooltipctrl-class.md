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
ms.openlocfilehash: 53a5a5b6871680f9758d140174dcceae6c53f568
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752199"
---
# <a name="ctooltipctrl-class"></a>CToolTipCtrl Class

Encapsula la funcionalidad de un "control de información sobre herramientas", una pequeña ventana emergente que muestra una única línea de texto que describe el propósito de una herramienta de una aplicación.

## <a name="syntax"></a>Sintaxis

```
class CToolTipCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CToolTipCtrl::CToolTipCtrl](#ctooltipctrl)|Construye un objeto `CToolTipCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CToolTipCtrl::Activar](#activate)|Activa y desactiva el control de información sobre herramientas.|
|[CToolTipCtrl::AddTool](#addtool)|Registra una herramienta con el control de información sobre herramientas.|
|[CToolTipCtrl::AdjustRect](#adjustrect)|Convierte entre el rectángulo de visualización de texto de un control de información sobre herramientas y su rectángulo de ventana.|
|[CToolTipCtrl::Create](#create)|Crea un control de información sobre `CToolTipCtrl` herramientas y lo adjunta a un objeto.|
|[CToolTipCtrl::CreateEx](#createex)|Crea un control de información sobre herramientas con los `CToolTipCtrl` estilos extendidos de Windows especificados y lo asocia a un objeto.|
|[CToolTipCtrl::DelTool](#deltool)|Elimina una herramienta del control de información sobre herramientas.|
|[CToolTipCtrl::GetBubbleSize](#getbubblesize)|Recupera el tamaño de la información sobre herramientas.|
|[CToolTipCtrl::GetCurrentTool](#getcurrenttool)|Recupera información, como el tamaño, la posición y el texto, de la ventana de información sobre herramientas que muestra el control de información sobre herramientas actual.|
|[CToolTipCtrl::GetDelayTime](#getdelaytime)|Recupera las duraciones iniciales, emergentes y de reprogramación que se establecen actualmente para un control de información sobre herramientas.|
|[CToolTipCtrl::GetMargin](#getmargin)|Recupera los márgenes superior, izquierdo, inferior y derecho que se establecen para una ventana de información sobre herramientas.|
|[CToolTipCtrl::GetMaxTipWidth](#getmaxtipwidth)|Recupera el ancho máximo de una ventana de información sobre herramientas.|
|[CToolTipCtrl::GetText](#gettext)|Recupera el texto que mantiene un control de información sobre herramientas para una herramienta.|
|[CToolTipCtrl::GetTipBkColor](#gettipbkcolor)|Recupera el color de fondo en una ventana de información sobre herramientas.|
|[CToolTipCtrl::GetTipTextColor](#gettiptextcolor)|Recupera el color del texto en una ventana de información sobre herramientas.|
|[CToolTipCtrl::GetTitle](#gettitle)|Recupera el título del control de información sobre herramientas actual.|
|[CToolTipCtrl::GetToolCount](#gettoolcount)|Recupera un recuento de las herramientas mantenidas por un control de información sobre herramientas.|
|[CToolTipCtrl::GetToolInfo](#gettoolinfo)|Recupera la información que un control de información sobre herramientas mantiene sobre una herramienta.|
|[CToolTipCtrl::HitTest](#hittest)|Comprueba un punto para determinar si está dentro del rectángulo delimitador de la herramienta dada. Si es así, recupera información sobre la herramienta.|
|[CToolTipCtrl::Pop](#pop)|Elimina una ventana de información sobre herramientas mostrada de la vista.|
|[CToolTipCtrl::Popup](#popup)|Hace que el control ToolTip actual se muestre en las coordenadas del último mensaje del mouse.|
|[CToolTipCtrl::RelayEvent](#relayevent)|Pasa un mensaje del mouse a un control de información sobre herramientas para su procesamiento.|
|[CToolTipCtrl::SetDelayTime](#setdelaytime)|Establece las duraciones iniciales, emergentes y remostrar para un control de información sobre herramientas.|
|[CToolTipCtrl::SetMargin](#setmargin)|Establece los márgenes superior, izquierdo, inferior y derecho de una ventana de información sobre herramientas.|
|[CToolTipCtrl::SetMaxTipWidth](#setmaxtipwidth)|Establece el ancho máximo de una ventana de información sobre herramientas.|
|[CToolTipCtrl::SetTipBkColor](#settipbkcolor)|Establece el color de fondo en una ventana de información sobre herramientas.|
|[CToolTipCtrl::SetTipTextColor](#settiptextcolor)|Establece el color del texto en una ventana de información sobre herramientas.|
|[CToolTipCtrl::SetTitle](#settitle)|Agrega un icono estándar y una cadena de título a una información sobre herramientas.|
|[CToolTipCtrl::SetToolInfo](#settoolinfo)|Establece la información que mantiene una información sobre herramientas para una herramienta.|
|[CToolTipCtrl::SetToolRect](#settoolrect)|Establece un nuevo rectángulo delimitador para una herramienta.|
|[CToolTipCtrl::SetWindowTheme](#setwindowtheme)|Establece el estilo visual de la ventana de información sobre herramientas.|
|[CToolTipCtrl::Update](#update)|Fuerza la redibujo de la herramienta actual.|
|[CToolTipCtrl::UpdateTipText](#updatetiptext)|Establece el texto de la información sobre herramientas de una herramienta.|

## <a name="remarks"></a>Observaciones

Una "herramienta" es una ventana, como una ventana o control secundario, o un área rectangular definida por la aplicación dentro del área de cliente de una ventana. Una información sobre herramientas se oculta la mayor parte del tiempo, apareciendo solo cuando el usuario coloca el cursor en una herramienta y lo deja allí durante aproximadamente medio segundo. La información sobre herramientas aparece cerca del cursor y desaparece cuando el usuario hace clic en un botón del ratón o mueve el cursor fuera de la herramienta.

`CToolTipCtrl`proporciona la funcionalidad para controlar el tiempo inicial y la duración de la información sobre herramientas, los anchos de margen que rodean el texto de la información sobre herramientas, el ancho de la propia ventana de información sobre herramientas y el color de fondo y texto de la información sobre herramientas. Un solo control de información sobre herramientas puede proporcionar información para más de una herramienta.

La `CToolTipCtrl` clase proporciona la funcionalidad del control de información sobre herramientas común de Windows. Este control (y, por lo tanto, la `CToolTipCtrl` clase) solo está disponible para programas que se ejecutan en Windows 95/98 y Windows NT versiones 3.51 y posteriores.

Para obtener más información sobre cómo habilitar sugerencias de herramientas, vea Sugerencias de herramientas [en Windows no derivadas de CFrameWnd](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).

Para obtener más `CToolTipCtrl`información sobre el uso de , vea [Controles](../../mfc/controls-mfc.md) y [uso de CToolTipCtrl](../../mfc/using-ctooltipctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CToolTipCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

## <a name="ctooltipctrlactivate"></a><a name="activate"></a>CToolTipCtrl::Activar

Llame a esta función para activar o desactivar un control de información sobre herramientas.

```cpp
void Activate(BOOL bActivate);
```

### <a name="parameters"></a>Parámetros

*bActivar*<br/>
Especifica si el control de información sobre herramientas se va a activar o desactivar.

### <a name="remarks"></a>Observaciones

Si *bActivate* es TRUE, se activa el control; si FALSE, se desactiva.

Cuando un control de información sobre herramientas está activo, la información de información sobre herramientas aparece cuando el cursor está en una herramienta registrada con el control; cuando está inactivo, la información de la información de la información de la información de la información de la herramienta no aparece, incluso cuando el cursor está en una herramienta.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrladdtool"></a><a name="addtool"></a>CToolTipCtrl::AddTool

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
ID del recurso de cadena que contiene el texto de la herramienta.

*lpRectTool*<br/>
Puntero a una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) que contiene coordenadas del rectángulo delimitador de la herramienta. Las coordenadas son relativas a la esquina superior izquierda del área cliente de la ventana identificada por *pWnd*.

*nIDTool*<br/>
ID de la herramienta.

*lpszText*<br/>
Puntero al texto de la herramienta. Si este parámetro contiene el valor LPSTR_TEXTCALLBACK, TTN_NEEDTEXT mensajes de notificación van al elemento primario de la ventana a la que *apunta pWnd.*

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Los *parámetros lpRectTool* y *nIDTool* deben ser válidos, o si *lpRectTool* es NULL, *nIDTool* debe ser 0.

Un control de información sobre herramientas se puede asociar a más de una herramienta. Llame a esta función para registrar una herramienta con el control de información sobre herramientas, de modo que la información almacenada en la información sobre herramientas se muestre cuando el cursor está en la herramienta.

> [!NOTE]
> No se puede establecer una información `AddTool`sobre herramientas en un control estático mediante .

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrladjustrect"></a><a name="adjustrect"></a>CToolTipCtrl::AdjustRect

Convierte entre el rectángulo de visualización de texto de un control de información sobre herramientas y su rectángulo de ventana.

```
BOOL AdjustRect(
    LPRECT lprc,
    BOOL bLarger = TRUE);
```

### <a name="parameters"></a>Parámetros

*lprc*<br/>
Puntero a una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) que contiene un rectángulo de ventana de información sobre herramientas o un rectángulo de visualización de texto.

*bLarger*<br/>
Si ES TRUE, *lprc* se utiliza para especificar un rectángulo de visualización de texto y recibe el rectángulo de ventana correspondiente. Si FALSE, *lprc* se utiliza para especificar un rectángulo de ventana y recibe el rectángulo de visualización de texto correspondiente.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el rectángulo se ajusta correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función miembro calcula el rectángulo de visualización de texto de un control de información sobre herramientas desde su rectángulo de ventana o el rectángulo de ventana de información sobre herramientas necesario para mostrar un rectángulo de visualización de texto especificado.

Esta función miembro implementa el comportamiento del mensaje Win32 [TTM_ADJUSTRECT](/windows/win32/Controls/ttm-adjustrect), como se describe en el Windows SDK.

## <a name="ctooltipctrlcreate"></a><a name="create"></a>CToolTipCtrl::Create

Crea un control de información sobre `CToolTipCtrl` herramientas y lo adjunta a un objeto.

```
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Especifica la ventana primaria del control de `CDialog`información sobre herramientas, normalmente un archivo . No debe ser NULL.

*dwStyle*<br/>
Especifica el estilo del control de información sobre herramientas. Consulte la sección **Comentarios** para obtener más información.

### <a name="return-value"></a>Valor devuelto

Distinto de `CToolTipCtrl` cero si el objeto se crea correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Se construye `CToolTipCtrl` un en dos pasos. En primer lugar, llame `CToolTipCtrl` al constructor `Create` para construir el objeto y, `CToolTipCtrl` a continuación, llame para crear el control de información sobre herramientas y adjuntarlo al objeto.

El parámetro *dwStyle* puede ser cualquier combinación de [estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles)de ventana . Además, un control de información sobre herramientas tiene dos estilos específicos de clase: TTS_ALWAYSTIP y TTS_NOPREFIX.

|Estilo|Significado|
|-----------|-------------|
|TTS_ALWAYSTIP|Especifica que la información sobre herramientas aparecerá cuando el cursor esté en una herramienta, independientemente de si la ventana propietaria del control de información sobre herramientas está activa o inactiva. Sin este estilo, el control de información sobre herramientas aparece cuando la ventana propietaria de la herramienta está activa, pero no cuando está inactiva.|
|TTS_NOPREFIX|Este estilo impide que el sistema desmonte el carácter de y comercial (&) de una cadena. Si un control de información sobre herramientas no tiene el estilo TTS_NOPREFIX, el sistema elimina automáticamente los caracteres de y comercial, lo que permite a una aplicación utilizar la misma cadena que un elemento de menú y como texto en un control de información sobre herramientas.|

Un control de información sobre herramientas tiene los estilos de ventana WS_POPUP y WS_EX_TOOLWINDOW, independientemente de si se especifican al crear el control.

Para crear un control de información sobre herramientas con estilos de `Create`ventanas extendidas, llame a [CToolTipCtrl::CreateEx](#createex) en lugar de .

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrlcreateex"></a><a name="createex"></a>CToolTipCtrl::CreateEx

Crea un control (una ventana secundaria) `CToolTipCtrl` y lo asocia con el objeto.

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
Especifica el estilo del control de información sobre herramientas. Consulte la sección **Comentarios** de [Crear](#create) para obtener más información.

*dwStyleEx*<br/>
Especifica el estilo extendido del control que se está creando. Para obtener una lista de estilos de Windows extendidos, vea el *dwExStyle* parámetro para [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente 0.

### <a name="remarks"></a>Observaciones

Se `CreateEx` usa `Create` en lugar de aplicar estilos de Windows extendidos, especificados por el **prefacio**de estilo extendido de Windows WS_EX_ .

## <a name="ctooltipctrlctooltipctrl"></a><a name="ctooltipctrl"></a>CToolTipCtrl::CToolTipCtrl

Construye un objeto `CToolTipCtrl`.

```
CToolTipCtrl();
```

### <a name="remarks"></a>Observaciones

Debe llamar `Create` después de construir el objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]

## <a name="ctooltipctrldeltool"></a><a name="deltool"></a>CToolTipCtrl::DelTool

Quita la herramienta especificada por *pWnd* y *nIDTool* de la colección de herramientas admitidas por un control de información sobre herramientas.

```cpp
void DelTool(
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero a la ventana que contiene la herramienta.

*nIDTool*<br/>
ID de la herramienta.

## <a name="ctooltipctrlgetbubblesize"></a><a name="getbubblesize"></a>CToolTipCtrl::GetBubbleSize

Recupera el tamaño de la información sobre herramientas.

```
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parámetros

*lpToolInfo*<br/>
Puntero a la estructura [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) de la información sobre herramientas.

### <a name="return-value"></a>Valor devuelto

El tamaño de la información sobre herramientas.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_GETBUBBLESIZE](/windows/win32/Controls/ttm-getbubblesize), como se describe en el Windows SDK.

## <a name="ctooltipctrlgetcurrenttool"></a><a name="getcurrenttool"></a>CToolTipCtrl::GetCurrentTool

Recupera información, como el tamaño, la posición y el texto, de la ventana de información sobre herramientas que muestra el control de información sobre herramientas actual.

```
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*lpToolInfo*|[fuera] Puntero a una estructura [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) que recibe información sobre la ventana de información sobre herramientas actual.|

### <a name="return-value"></a>Valor devuelto

TRUESi la información se recupera correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje TTM_GETCURRENTTOOL,](/windows/win32/Controls/ttm-getcurrenttool) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se recupera información sobre la ventana de información sobre herramientas actual.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]

## <a name="ctooltipctrlgetdelaytime"></a><a name="getdelaytime"></a>CToolTipCtrl::GetDelayTime

Recupera las duraciones iniciales, emergentes y de reprograma establecidas actualmente para un control de información sobre herramientas.

```
int GetDelayTime(DWORD dwDuration) const;
```

### <a name="parameters"></a>Parámetros

*dwDuración*<br/>
Marcador que especifica qué valor de duración se recuperará. Este parámetro puede ser uno de los siguientes valores:

- TTDT_AUTOPOP Recuperar el tiempo que la ventana de información sobre herramientas permanece visible si el puntero está inmóvil dentro del rectángulo delimitador de una herramienta.

- TTDT_INITIAL Recuperar el tiempo que el puntero debe permanecer inmóvil dentro del rectángulo delimitador de una herramienta antes de que aparezca la ventana de información sobre herramientas.

- TTDT_RESHOW Recuperar el tiempo que tardan las ventanas de información sobre herramientas posteriores en aparecer a medida que el puntero se mueve de una herramienta a otra.

### <a name="return-value"></a>Valor devuelto

El tiempo de retardo especificado, en milisegundos

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/ttm-getdelaytime)Win32 TTM_GETDELAYTIME , como se describe en el Windows SDK.

## <a name="ctooltipctrlgetmargin"></a><a name="getmargin"></a>CToolTipCtrl::GetMargin

Recupera los márgenes superior, izquierdo, inferior y derecho establecidos para una ventana de información sobre herramientas.

```cpp
void GetMargin(LPRECT lprc) const;
```

### <a name="parameters"></a>Parámetros

*lprc*<br/>
Dirección de `RECT` una estructura que recibirá la información de margen. Los miembros de la estructura [RECT](/windows/win32/api/windef/ns-windef-rect) no definen un rectángulo delimitador. A los efectos de este mensaje, los miembros de la estructura se interpretan de la siguiente manera:

|Member|Representación|
|------------|--------------------|
|`top`|Distancia entre el borde superior y la parte superior del texto de la información sobre herramientas, en píxeles.|
|`left`|Distancia entre el borde izquierdo y el extremo izquierdo del texto de la punta, en píxeles.|
|`bottom`|Distancia entre el borde inferior y la parte inferior del texto de la punta, en píxeles.|
|`right`|Distancia entre el borde derecho y el extremo derecho del texto de la punta, en píxeles.|

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje Win32 [TTM_GETMARGIN](/windows/win32/Controls/ttm-getmargin), como se describe en el Windows SDK.

## <a name="ctooltipctrlgetmaxtipwidth"></a><a name="getmaxtipwidth"></a>CToolTipCtrl::GetMaxTipWidth

Recupera el ancho máximo de una ventana de información sobre herramientas.

```
int GetMaxTipWidth() const;
```

### <a name="return-value"></a>Valor devuelto

El ancho máximo de una ventana de información sobre herramientas.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje Win32 [TTM_GETMAXTIPWIDTH](/windows/win32/Controls/ttm-getmaxtipwidth), como se describe en el Windows SDK.

## <a name="ctooltipctrlgettext"></a><a name="gettext"></a>CToolTipCtrl::GetText

Recupera el texto que mantiene un control de información sobre herramientas para una herramienta.

```cpp
void GetText(
    CString& str,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Parámetros

*Str*<br/>
Referencia a `CString` un objeto que recibe el texto de la herramienta.

*pWnd*<br/>
Puntero a la ventana que contiene la herramienta.

*nIDTool*<br/>
ID de la herramienta.

### <a name="remarks"></a>Observaciones

Los *parámetros pWnd* y *nIDTool* identifican la herramienta. Si esa herramienta se ha registrado previamente con `CToolTipCtrl::AddTool`el control de información sobre herramientas mediante una llamada anterior a , al objeto al que hace referencia el parámetro *str* se le asigna el texto de la herramienta.

## <a name="ctooltipctrlgettipbkcolor"></a><a name="gettipbkcolor"></a>CToolTipCtrl::GetTipBkColor

Recupera el color de fondo en una ventana de información sobre herramientas.

```
COLORREF GetTipBkColor() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor [COLORREF](/windows/win32/gdi/colorref) que representa el color de fondo.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_GETTIPBKCOLOR](/windows/win32/Controls/ttm-gettipbkcolor), como se describe en el Windows SDK.

## <a name="ctooltipctrlgettiptextcolor"></a><a name="gettiptextcolor"></a>CToolTipCtrl::GetTipTextColor

Recupera el color del texto en una ventana de información sobre herramientas.

```
COLORREF GetTipTextColor() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor [COLORREF](/windows/win32/gdi/colorref) que representa el color del texto.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/ttm-gettiptextcolor)Win32 TTM_GETTIPTEXTCOLOR , como se describe en el Windows SDK.

## <a name="ctooltipctrlgettitle"></a><a name="gettitle"></a>CToolTipCtrl::GetTitle

Recupera el título del control de información sobre herramientas actual.

```cpp
void GetTitle(PTTGETTITLE pttgt) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pttgt*|[fuera] Puntero a una estructura [TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) que contiene información sobre el ToolTip control. Cuando se devuelve este método, el *pszTitle* miembro de la [TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) estructura apunta al texto del título.|

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje TTM_GETTITLE,](/windows/win32/Controls/ttm-gettitle) que se describe en el Windows SDK.

## <a name="ctooltipctrlgettoolcount"></a><a name="gettoolcount"></a>CToolTipCtrl::GetToolCount

Recupera un recuento de las herramientas registradas con el control de información sobre herramientas.

```
int GetToolCount() const;
```

### <a name="return-value"></a>Valor devuelto

Un recuento de herramientas registradas con el control de información sobre herramientas.

## <a name="ctooltipctrlgettoolinfo"></a><a name="gettoolinfo"></a>CToolTipCtrl::GetToolInfo

Recupera la información que un control de información sobre herramientas mantiene sobre una herramienta.

```
BOOL GetToolInfo(
    CToolInfo& ToolInfo,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Parámetros

*ToolInfo*<br/>
Referencia a `TOOLINFO` un objeto que recibe el texto de la herramienta.

*pWnd*<br/>
Puntero a la ventana que contiene la herramienta.

*nIDTool*<br/>
ID de la herramienta.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Los `hwnd` `uId` miembros de la estructura [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) a los que hace referencia *CToolInfo* identifican la herramienta. Si esa herramienta se ha registrado con el `AddTool`control `TOOLINFO` de información sobre herramientas a través de una llamada anterior a , la estructura se rellena con información sobre la herramienta.

## <a name="ctooltipctrlhittest"></a><a name="hittest"></a>CToolTipCtrl::HitTest

Comprueba un punto para determinar si está dentro del rectángulo delimitador de la herramienta dada y, si es así, recupera información sobre la herramienta.

```
BOOL HitTest(
    CWnd* pWnd,
    CPoint pt,
    LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero a la ventana que contiene la herramienta.

*Pt*<br/>
Puntero a `CPoint` un objeto que contiene las coordenadas del punto que se va a probar.

*lpToolInfo*<br/>
Puntero a la estructura [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) que contiene información sobre la herramienta.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el punto especificado por la información de prueba de posicionamiento está dentro del rectángulo delimitador de la herramienta; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si esta función devuelve un valor distinto de cero, la estructura señalada por *lpToolInfo* se rellena con información sobre la herramienta dentro de cuyo rectángulo se encuentra el punto.

La `TTHITTESTINFO` estructura se define de la siguiente manera:

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

   Información sobre la herramienta. Para obtener más `TOOLINFO` información acerca de la estructura, vea [CToolTipCtrl::GetToolInfo](#gettoolinfo).

## <a name="ctooltipctrlpop"></a><a name="pop"></a>CToolTipCtrl::Pop

Elimina una ventana de información sobre herramientas mostrada de la vista.

```cpp
void Pop();
```

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento de la [TTM_POP](/windows/win32/Controls/ttm-pop)de mensaje de Win32 , como se describe en el Windows SDK.

## <a name="ctooltipctrlpopup"></a><a name="popup"></a>CToolTipCtrl::Popup

Hace que el control de información sobre herramientas actual se muestre en las coordenadas del último mensaje del mouse.

```cpp
void Popup();
```

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje TTM_POPUP,](/windows/win32/Controls/ttm-popup) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra una ventana de información sobre herramientas.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]

## <a name="ctooltipctrlrelayevent"></a><a name="relayevent"></a>CToolTipCtrl::RelayEvent

Pasa un mensaje del mouse a un control de información sobre herramientas para su procesamiento.

```cpp
void RelayEvent(LPMSG lpMsg);
```

### <a name="parameters"></a>Parámetros

*lpMsg*<br/>
Puntero a una estructura [MSG](/windows/win32/api/winuser/ns-winuser-msg) que contiene el mensaje que se retransmite.

### <a name="remarks"></a>Observaciones

Un control de información sobre herramientas procesa sólo `RelayEvent`los siguientes mensajes, que se le envían por:

|WM_LBUTTONDOWN|WM_MOUSEMOVE|
|---------------------|-------------------|
|WM_LBUTTONUP|WM_RBUTTONDOWN|
|WM_MBUTTONDOWN|WM_RBUTTONUP|
|WM_MBUTTONUP||

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrlsetdelaytime"></a><a name="setdelaytime"></a>CToolTipCtrl::SetDelayTime

Establece el tiempo de retardo para un control de información sobre herramientas.

```cpp
void SetDelayTime(UINT nDelay);

void SetDelayTime(
    DWORD dwDuration,
    int iTime);
```

### <a name="parameters"></a>Parámetros

*nDelay*<br/>
Especifica el nuevo tiempo de retardo, en milisegundos.

*dwDuración*<br/>
Marcador que especifica qué valor de duración se recuperará. Vea [CToolTipCtrl::GetDelayTime](#getdelaytime) para obtener una descripción de los valores válidos.

*iTime*<br/>
El tiempo de retardo especificado, en milisegundos.

### <a name="remarks"></a>Observaciones

El tiempo de retardo es el tiempo que el cursor debe permanecer en una herramienta antes de que aparezca la ventana de información sobre herramientas. El tiempo de retardo predeterminado es de 500 milisegundos.

## <a name="ctooltipctrlsetmargin"></a><a name="setmargin"></a>CToolTipCtrl::SetMargin

Establece los márgenes superior, izquierdo, inferior y derecho de una ventana de información sobre herramientas.

```cpp
void SetMargin(LPRECT lprc);
```

### <a name="parameters"></a>Parámetros

*lprc*<br/>
Dirección de `RECT` una estructura que contiene la información de margen que se va a establecer. Los miembros `RECT` de la estructura no definen un rectángulo delimitador. Consulte [CToolTipCtrl::GetMargin](#getmargin) para obtener una descripción de la información del margen.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/ttm-setmargin)Win32 TTM_SETMARGIN , como se describe en el Windows SDK.

## <a name="ctooltipctrlsetmaxtipwidth"></a><a name="setmaxtipwidth"></a>CToolTipCtrl::SetMaxTipWidth

Establece el ancho máximo de una ventana de información sobre herramientas.

```
int SetMaxTipWidth(int iWidth);
```

### <a name="parameters"></a>Parámetros

*iWidth*<br/>
El ancho máximo de la ventana de información sobre herramientas que se va a establecer.

### <a name="return-value"></a>Valor devuelto

El ancho máximo de la punta anterior.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje win32 TTM_SETMAXTIPWIDTH](/windows/win32/Controls/ttm-setmaxtipwidth), como se describe en el Windows SDK.

## <a name="ctooltipctrlsettipbkcolor"></a><a name="settipbkcolor"></a>CToolTipCtrl::SetTipBkColor

Establece el color de fondo en una ventana de información sobre herramientas.

```cpp
void SetTipBkColor(COLORREF clr);
```

### <a name="parameters"></a>Parámetros

*Clr*<br/>
Nuevo color de fondo.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_SETTIPBKCOLOR](/windows/win32/Controls/ttm-settipbkcolor), como se describe en el Windows SDK.

## <a name="ctooltipctrlsettiptextcolor"></a><a name="settiptextcolor"></a>CToolTipCtrl::SetTipTextColor

Establece el color del texto en una ventana de información sobre herramientas.

```cpp
void SetTipTextColor(COLORREF clr);
```

### <a name="parameters"></a>Parámetros

*Clr*<br/>
El nuevo color del texto.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_SETTIPTEXTCOLOR](/windows/win32/Controls/ttm-settiptextcolor), como se describe en el Windows SDK.

## <a name="ctooltipctrlsettitle"></a><a name="settitle"></a>CToolTipCtrl::SetTitle

Agrega un icono estándar y una cadena de título a una información sobre herramientas.

```
BOOL SetTitle(
    UINT uIcon,
    LPCTSTR lpstrTitle);
```

### <a name="parameters"></a>Parámetros

*uIcon*<br/>
Consulte *el icono* en [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle) en el Windows SDK.

*lpstrTitle*<br/>
Puntero a la cadena de título.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle), como se describe en el Windows SDK.

## <a name="ctooltipctrlsettoolinfo"></a><a name="settoolinfo"></a>CToolTipCtrl::SetToolInfo

Establece la información que mantiene una información sobre herramientas para una herramienta.

```cpp
void SetToolInfo(LPTOOLINFO lpToolInfo);
```

### <a name="parameters"></a>Parámetros

*lpToolInfo*<br/>
Puntero a una estructura [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) que especifica la información que se va a establecer.

## <a name="ctooltipctrlsettoolrect"></a><a name="settoolrect"></a>CToolTipCtrl::SetToolRect

Establece un nuevo rectángulo delimitador para una herramienta.

```cpp
void SetToolRect(
    CWnd* pWnd,
    UINT_PTR nIDTool,
    LPCRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero a la ventana que contiene la herramienta.

*nIDTool*<br/>
ID de la herramienta.

*lpRect*<br/>
Puntero a una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) que especifica el nuevo rectángulo delimitador.

## <a name="ctooltipctrlsetwindowtheme"></a><a name="setwindowtheme"></a>CToolTipCtrl::SetWindowTheme

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

Esta función miembro emula la funcionalidad del [mensaje de TTM_SETWINDOWTHEME,](/windows/win32/Controls/ttm-setwindowtheme) como se describe en el Windows SDK.

## <a name="ctooltipctrlupdate"></a><a name="update"></a>CToolTipCtrl::Update

Fuerza la redibujo de la herramienta actual.

```cpp
void Update();
```

## <a name="ctooltipctrlupdatetiptext"></a><a name="updatetiptext"></a>CToolTipCtrl::UpdateTipText

Actualiza el texto de información sobre herramientas para las herramientas de este control.

```cpp
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
ID de la herramienta.

*nIDText*<br/>
ID del recurso de cadena que contiene el texto de la herramienta.

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CToolBar (clase)](../../mfc/reference/ctoolbar-class.md)
