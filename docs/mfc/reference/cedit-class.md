---
title: CEdit Class
ms.date: 09/12/2018
f1_keywords:
- CEdit
- AFXWIN/CEdit
- AFXWIN/CEdit::CEdit
- AFXWIN/CEdit::CanUndo
- AFXWIN/CEdit::CharFromPos
- AFXWIN/CEdit::Clear
- AFXWIN/CEdit::Copy
- AFXWIN/CEdit::Create
- AFXWIN/CEdit::Cut
- AFXWIN/CEdit::EmptyUndoBuffer
- AFXWIN/CEdit::FmtLines
- AFXWIN/CEdit::GetCueBanner
- AFXWIN/CEdit::GetFirstVisibleLine
- AFXWIN/CEdit::GetHandle
- AFXWIN/CEdit::GetHighlight
- AFXWIN/CEdit::GetLimitText
- AFXWIN/CEdit::GetLine
- AFXWIN/CEdit::GetLineCount
- AFXWIN/CEdit::GetMargins
- AFXWIN/CEdit::GetModify
- AFXWIN/CEdit::GetPasswordChar
- AFXWIN/CEdit::GetRect
- AFXWIN/CEdit::GetSel
- AFXWIN/CEdit::HideBalloonTip
- AFXWIN/CEdit::LimitText
- AFXWIN/CEdit::LineFromChar
- AFXWIN/CEdit::LineIndex
- AFXWIN/CEdit::LineLength
- AFXWIN/CEdit::LineScroll
- AFXWIN/CEdit::Paste
- AFXWIN/CEdit::PosFromChar
- AFXWIN/CEdit::ReplaceSel
- AFXWIN/CEdit::SetCueBanner
- AFXWIN/CEdit::SetHandle
- AFXWIN/CEdit::SetHighlight
- AFXWIN/CEdit::SetLimitText
- AFXWIN/CEdit::SetMargins
- AFXWIN/CEdit::SetModify
- AFXWIN/CEdit::SetPasswordChar
- AFXWIN/CEdit::SetReadOnly
- AFXWIN/CEdit::SetRect
- AFXWIN/CEdit::SetRectNP
- AFXWIN/CEdit::SetSel
- AFXWIN/CEdit::SetTabStops
- AFXWIN/CEdit::ShowBalloonTip
- AFXWIN/CEdit::Undo
helpviewer_keywords:
- CEdit [MFC], CEdit
- CEdit [MFC], CanUndo
- CEdit [MFC], CharFromPos
- CEdit [MFC], Clear
- CEdit [MFC], Copy
- CEdit [MFC], Create
- CEdit [MFC], Cut
- CEdit [MFC], EmptyUndoBuffer
- CEdit [MFC], FmtLines
- CEdit [MFC], GetCueBanner
- CEdit [MFC], GetFirstVisibleLine
- CEdit [MFC], GetHandle
- CEdit [MFC], GetHighlight
- CEdit [MFC], GetLimitText
- CEdit [MFC], GetLine
- CEdit [MFC], GetLineCount
- CEdit [MFC], GetMargins
- CEdit [MFC], GetModify
- CEdit [MFC], GetPasswordChar
- CEdit [MFC], GetRect
- CEdit [MFC], GetSel
- CEdit [MFC], HideBalloonTip
- CEdit [MFC], LimitText
- CEdit [MFC], LineFromChar
- CEdit [MFC], LineIndex
- CEdit [MFC], LineLength
- CEdit [MFC], LineScroll
- CEdit [MFC], Paste
- CEdit [MFC], PosFromChar
- CEdit [MFC], ReplaceSel
- CEdit [MFC], SetCueBanner
- CEdit [MFC], SetHandle
- CEdit [MFC], SetHighlight
- CEdit [MFC], SetLimitText
- CEdit [MFC], SetMargins
- CEdit [MFC], SetModify
- CEdit [MFC], SetPasswordChar
- CEdit [MFC], SetReadOnly
- CEdit [MFC], SetRect
- CEdit [MFC], SetRectNP
- CEdit [MFC], SetSel
- CEdit [MFC], SetTabStops
- CEdit [MFC], ShowBalloonTip
- CEdit [MFC], Undo
ms.assetid: b1533c30-7f10-4663-88d3-8b7f2c9f7024
ms.openlocfilehash: 94769a6fb3c5fceefda96b54cebb35b0533a8afa
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753220"
---
# <a name="cedit-class"></a>CEdit Class

Proporciona la funcionalidad de un control de edición de Windows.

## <a name="syntax"></a>Sintaxis

```
class CEdit : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CEdit::CEditar](#cedit)|Construye un `CEdit` objeto de control.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CEdit::CanUndo](#canundo)|Determina si se puede deshacer una operación de control de edición.|
|[CEdit::CharFromPos](#charfrompos)|Recupera los índices de línea y carácter del carácter más cercano a una posición especificada.|
|[CEdit::Clear](#clear)|Elimina (borra) la selección actual (si existe) en el control de edición.|
|[CEdit::Copiar](#copy)|Copia la selección actual (si existe) en el control de edición en el Portapapeles en formato CF_TEXT.|
|[CEdit::Create](#create)|Crea el control de edición `CEdit` de Windows y lo adjunta al objeto.|
|[CEdit::Corte](#cut)|Elimina (corta) la selección actual (si existe) en el control de edición y copia el texto eliminado en el Portapapeles en formato CF_TEXT.|
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|Restablece (borra) la marca de deshacer de un control de edición.|
|[CEdit::FmtLines](#fmtlines)|Establece la inclusión de caracteres de salto de línea suave activados o desactivados en un control de edición de varias líneas.|
|[CEdit::GetCueBanner](#getcuebanner)|Recupera el texto que se muestra como la indicación de texto, o sugerencia, en un control de edición cuando el control está vacío y no tiene el foco.|
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|Determina la línea visible superior en un control de edición.|
|[CEdit::GetHandle](#gethandle)|Recupera un identificador de la memoria que está asignada actualmente para un control de edición de varias líneas.|
|[CEdit::GetHighlight](#gethighlight)|Obtiene los índices de los caracteres inicial y final en un intervalo de texto que se resalta en el control de edición actual.|
|[CEdit::GetLimitText](#getlimittext)|Obtiene la cantidad máxima `CEdit` de texto que esto puede contener.|
|[CEdit::GetLine](#getline)|Recupera una línea de texto de un control de edición.|
|[CEdit::GetLineCount](#getlinecount)|Recupera el número de líneas de un control de edición de varias líneas.|
|[CEdit::GetMargins](#getmargins)|Obtiene los márgenes izquierdo y `CEdit`derecho para esto .|
|[CEdit::GetModify](#getmodify)|Determina si se ha modificado el contenido de un control de edición.|
|[CEdit::GetPasswordChar](#getpasswordchar)|Recupera el carácter de contraseña que se muestra en un control de edición cuando el usuario escribe texto.|
|[CEdit::GetRect](#getrect)|Obtiene el rectángulo de formato de un control de edición.|
|[CEdit::GetSel](#getsel)|Obtiene la primera y la última posición de carácter de la selección actual en un control de edición.|
|[CEdit::HideBalloonTip](#hideballoontip)|Oculta cualquier sugerencia de globo asociada con el control de edición actual.|
|[CEdit::LimitText](#limittext)|Limita la longitud del texto que el usuario puede escribir en un control de edición.|
|[CEdit::LineFromChar](#linefromchar)|Recupera el número de línea de la línea que contiene el índice de caracteres especificado.|
|[CEdit::LineIndex](#lineindex)|Recupera el índice de caracteres de una línea dentro de un control de edición de varias líneas.|
|[CEdit::LineLength](#linelength)|Recupera la longitud de una línea en un control de edición.|
|[CEdit::LineScroll](#linescroll)|Desplaza el texto de un control de edición de varias líneas.|
|[CEdit::Paste](#paste)|Inserta los datos del Portapapeles en el control de edición en la posición actual del cursor. Los datos solo se insertan si el Portapapeles contiene datos en formato CF_TEXT.|
|[CEdit::PosFromChar](#posfromchar)|Recupera las coordenadas de la esquina superior izquierda de un índice de caracteres especificado.|
|[CEdit::ReplaceSel](#replacesel)|Reemplaza la selección actual en un control de edición con el texto especificado.|
|[CEdit::SetCueBanner](#setcuebanner)|Establece el texto que se muestra como la indicación de texto, o sugerencia, en un control de edición cuando el control está vacío y no tiene el foco.|
|[CEdit::SetHandle](#sethandle)|Establece el identificador en la memoria local que usará un control de edición de varias líneas.|
|[CEdit::SetHighlight](#sethighlight)|Resalta un rango de texto que se muestra en el control de edición actual.|
|[CEdit::SetLimitText](#setlimittext)|Establece la cantidad máxima `CEdit` de texto que puede contener.|
|[CEdit::SetMargins](#setmargins)|Establece los márgenes izquierdo `CEdit`y derecho para este .|
|[CEdit::SetModify](#setmodify)|Establece o desactiva el indicador de modificación de un control de edición.|
|[CEdit::SetPasswordChar](#setpasswordchar)|Establece o quita un carácter de contraseña que se muestra en un control de edición cuando el usuario escribe texto.|
|[CEdit::SetReadOnly](#setreadonly)|Establece el estado de solo lectura de un control de edición.|
|[CEdit::SetRect](#setrect)|Establece el rectángulo de formato de un control de edición de varias líneas y actualiza el control.|
|[CEdit::SetRectNP](#setrectnp)|Establece el rectángulo de formato de un control de edición de varias líneas sin volver a dibujar la ventana de control.|
|[CEdit::SetSel](#setsel)|Selecciona un intervalo de caracteres en un control de edición.|
|[CEdit::SetTabStops](#settabstops)|Establece las tabulaciones en un control de edición de varias líneas.|
|[CEdit::ShowBalloonTip](#showballoontip)|Muestra una sugerencia de globo asociada al control de edición actual.|
|[CEdit::Deshacer](#undo)|Invierte la última operación de control de edición.|

## <a name="remarks"></a>Observaciones

Un control de edición es una ventana secundaria rectangular en la que el usuario puede escribir texto.

Puede crear un control de edición desde una plantilla de cuadro de diálogo o directamente en el código. En ambos casos, primero `CEdit` llame `CEdit` al constructor para construir el objeto y, a continuación, `CEdit` llame a la [create](#create) función miembro para crear el control de edición de Windows y adjuntarlo al objeto.

La construcción puede ser un proceso de `CEdit`un solo paso en una clase derivada de . Escriba un constructor para la `Create` clase derivada y llame desde dentro del constructor.

`CEdit`hereda una funcionalidad `CWnd`significativa de . Para establecer y recuperar `CEdit` texto de `CWnd` un objeto, utilice las funciones miembro [SetWindowText](cwnd-class.md#setwindowtext) y [GetWindowText](cwnd-class.md#getwindowtext), que establecen u obtienen todo el contenido de un control de edición, incluso si se trata de un control de varias líneas. Las líneas de texto de un control de varias líneas están separadas por secuencias de caracteres de '.r'n'. Además, si un control de edición es multilínea, obtenga `CEdit` y establezca parte del texto del control llamando a las funciones miembro [GetLine](#getline), [SetSel](#setsel), [GetSel](#getsel)y [ReplaceSel](#replacesel).

Si desea controlar los mensajes de notificación de Windows enviados por `CDialog`un control de edición a su elemento primario (normalmente una clase derivada de ), agregue una entrada de mapa de mensajes y una función miembro de controlador de mensajes a la clase primaria para cada mensaje.

Cada entrada de mapa de mensajes adopta la siguiente forma:

  **ON_**_NOTIFICACION_**(** _id_**,** _memberFxn_ **)**

donde `id` especifica el identificador de ventana secundaria del `memberFxn` control de edición que envía la notificación y es el nombre de la función miembro principal que ha escrito para controlar la notificación.

El prototipo de función del padre es el siguiente:

**afx_msg** miembro voidFxn **( );**

A continuación se muestra una lista de posibles entradas de mapa de mensajes y una descripción de los casos en los que se enviarían al padre:

- ON_EN_CHANGE El usuario ha realizado una acción que puede haber modificado el texto de un control de edición. A diferencia del mensaje de notificación EN_UPDATE, este mensaje de notificación se envía después de que Windows actualiza la pantalla.

- ON_EN_ERRSPACE El control de edición no puede asignar suficiente memoria para satisfacer una solicitud específica.

- ON_EN_HSCROLL El usuario hace clic en la barra de desplazamiento horizontal de un control de edición. La ventana principal se notifica antes de actualizar la pantalla.

- ON_EN_KILLFOCUS El control de edición pierde el foco de entrada.

- ON_EN_MAXTEXT La inserción actual ha superado el número especificado de caracteres para el control de edición y se ha truncado. También se envía cuando un control de edición no tiene el estilo de ES_AUTOHSCROLL y el número de caracteres que se insertaría superaría el ancho del control de edición. También se envía cuando un control de edición no tiene el estilo de ES_AUTOVSCROLL y el número total de líneas resultantes de una inserción de texto superaría la altura del control de edición.

- ON_EN_SETFOCUS Enviado cuando un control de edición recibe el foco de entrada.

- ON_EN_UPDATE El control de edición está a punto de mostrar texto modificado. Se envía después de que el control ha formateado el texto, pero antes de que se muestra el texto para que el tamaño de la ventana se puede modificar, si es necesario.

- ON_EN_VSCROLL El usuario hace clic en la barra de desplazamiento vertical de un control de edición. La ventana principal se notifica antes de actualizar la pantalla.

Si crea `CEdit` un objeto dentro de `CEdit` un cuadro de diálogo, el objeto se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.

Si crea `CEdit` un objeto a partir de un `CEdit` recurso de cuadro de diálogo mediante el editor de cuadros de diálogo, el objeto se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.

Si crea `CEdit` un objeto dentro de una ventana, es posible que también deba destruirlo. Si crea `CEdit` el objeto en la pila, se destruye automáticamente. Si crea `CEdit` el objeto en el montón mediante la **nueva** función, debe llamar a **delete** en el objeto para destruirlo cuando el usuario termine el control de edición de Windows. Si asigna memoria en `CEdit` el objeto, reemplace el `CEdit` destructor para eliminar las asignaciones.

Para modificar determinados estilos en un control de edición (como ES_READONLY) debe enviar mensajes específicos al control en lugar de usar [ModifyStyle](cwnd-class.md#modifystyle). Consulte [Editar estilos](/windows/win32/Controls/edit-control-styles) de control en el Windows SDK.

Para obtener `CEdit`más información sobre , consulte [Controles](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="ceditcanundo"></a><a name="canundo"></a>CEdit::CanUndo

Llame a esta función para determinar si se puede deshacer la última operación de edición.

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la última operación de `Undo` edición se puede deshacer mediante una llamada a la función miembro; 0 si no se puede deshacer.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [EM_CANUNDO](/windows/win32/Controls/em-canundo) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::Undo](#undo).

## <a name="ceditcedit"></a><a name="cedit"></a>CEdit::CEditar

Construye un objeto `CEdit`.

```
CEdit();
```

### <a name="remarks"></a>Observaciones

Use [Crear](#create) para construir el control de edición de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

## <a name="ceditcharfrompos"></a><a name="charfrompos"></a>CEdit::CharFromPos

Llame a esta función para recuperar los índices de línea y carácter de base cero del carácter más cercano al punto especificado en este `CEdit` control

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>Parámetros

*Pt*<br/>
Las coordenadas de un punto en `CEdit` el área de cliente de este objeto.

### <a name="return-value"></a>Valor devuelto

El índice de caracteres en el orden bajo WORD y el índice de línea en el orden alto WORD.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Esta función miembro está disponible a partir de Windows 95 y Windows NT 4.0.

Para obtener más información, consulte [EM_CHARFROMPOS](/windows/win32/Controls/em-charfrompos) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

## <a name="ceditclear"></a><a name="clear"></a>CEdit::Clear

Llame a esta función para eliminar (borrar) la selección actual (si existe) en el control de edición.

```cpp
void Clear();
```

### <a name="remarks"></a>Observaciones

La eliminación `Clear` realizada por se puede deshacer mediante una llamada a la [Deshacer](#undo) función miembro.

Para eliminar la selección actual y colocar el contenido eliminado en el Portapapeles, llame a la [Cortar](#cut) función miembro.

Para obtener más información, consulte [WM_CLEAR](/windows/win32/dataxchg/wm-clear) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

## <a name="ceditcopy"></a><a name="copy"></a>CEdit::Copiar

Llame a esta función para coy la selección actual (si existe) en el control de edición en el Portapapeles en formato CF_TEXT.

```cpp
void Copy();
```

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [WM_COPY](/windows/win32/dataxchg/wm-copy) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

## <a name="ceditcreate"></a><a name="create"></a>CEdit::Create

Crea el control de edición `CEdit` de Windows y lo adjunta al objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de edición. Aplique cualquier combinación de estilos de [edición](styles-used-by-mfc.md#edit-styles) al control.

*Rect*<br/>
Especifica el tamaño y la posición del control de edición. Puede ser `CRect` un `RECT` objeto o estructura.

*pParentWnd*<br/>
Especifica la ventana primaria del control `CDialog`de edición (normalmente un archivo ). No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de edición.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización se realiza correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Construir un `CEdit` objeto en dos pasos. En primer `CEdit` lugar, llame `Create`al constructor y, a continuación, `CEdit` llame a , que crea el control de edición de Windows y lo adjunta al objeto.

Cuando `Create` se ejecuta, Windows envía los mensajes [WM_NCCREATE](/windows/win32/winmsg/wm-nccreate), [WM_NCCALCSIZE](/windows/win32/winmsg/wm-nccalcsize), [WM_CREATE](/windows/win32/winmsg/wm-create)y [WM_GETMINMAXINFO](/windows/win32/winmsg/wm-getminmaxinfo) al control de edición.

Estos mensajes se controlan de forma predeterminada mediante las funciones miembro [OnNcCreate](cwnd-class.md#onnccreate), [OnNcCalcSize](cwnd-class.md#onnccalcsize), [OnCreate](cwnd-class.md#oncreate)y [OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo) de la `CWnd` clase base. Para extender el control de mensajes `CEdit`predeterminado, derive una clase de , agregue un mapa de mensajes a la nueva clase e invalide las funciones miembro de controlador de mensajes anteriores. Invalidar `OnCreate`, por ejemplo, para realizar la inicialización necesaria para la nueva clase.

Aplique los siguientes [estilos](styles-used-by-mfc.md#window-styles) de ventana a un control de edición.

- WS_CHILD Siempre

- WS_VISIBLE Por lo general

- WS_DISABLED Rara vez

- WS_GROUP Para agrupar controles

- WS_TABSTOP Para incluir el control de edición en el orden de tabulación

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

## <a name="ceditcut"></a><a name="cut"></a>CEdit::Corte

Llame a esta función para eliminar (cortar) la selección actual (si existe) en el control de edición y copiar el texto eliminado en el Portapapeles en formato CF_TEXT.

```cpp
void Cut();
```

### <a name="remarks"></a>Observaciones

La eliminación `Cut` realizada por se puede deshacer mediante una llamada a la [Deshacer](#undo) función miembro.

Para eliminar la selección actual sin colocar el texto eliminado en el Portapapeles, llame a la [Clear](#clear) función miembro.

Para obtener más información, consulte [WM_CUT](/windows/win32/dataxchg/wm-cut) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

## <a name="ceditemptyundobuffer"></a><a name="emptyundobuffer"></a>CEdit::EmptyUndoBuffer

Llame a esta función para restablecer (borrar) la marca de deshacer de un control de edición.

```cpp
void EmptyUndoBuffer();
```

### <a name="remarks"></a>Observaciones

El control de edición ahora no podrá deshacer la última operación. El indicador de deshacer se establece siempre que se puede deshacer una operación dentro del control de edición.

El indicador de deshacer se borra automáticamente cada vez que el [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) o [SetHandle](#sethandle) `CWnd` se llama a las funciones miembro.

Para obtener más información, consulte [EM_EMPTYUNDOBUFFER](/windows/win32/Controls/em-emptyundobuffer) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

## <a name="ceditfmtlines"></a><a name="fmtlines"></a>CEdit::FmtLines

Llame a esta función para establecer la inclusión de caracteres de salto de línea suave activados o desactivados en un control de edición de varias líneas.

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>Parámetros

*bAddEOL*<br/>
Especifica si se van a insertar caracteres de salto de línea flexibles. Un valor de TRUE inserta los caracteres; un valor de FALSE los elimina.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se produce algún formato; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Un salto de línea suave consta de dos retornos de carro y un avance de línea insertado al final de una línea que se rompe debido al ajuste de palabras. Un salto de línea duro consta de un retorno de carro y un avance de línea. Las líneas que terminan con un `FmtLines`salto de línea dura no se ven afectadas por .

Windows solo responderá `CEdit` si el objeto es un control de edición de varias líneas.

`FmtLines`solo afecta al búfer devuelto por [GetHandle](#gethandle) y al texto devuelto por [WM_GETTEXT](/windows/win32/winmsg/wm-gettext). No tiene ningún impacto en la visualización del texto dentro del control de edición.

Para obtener más información, consulte [EM_FMTLINES](/windows/win32/Controls/em-fmtlines) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

## <a name="ceditgetcuebanner"></a><a name="getcuebanner"></a>CEdit::GetCueBanner

Recupera el texto que se muestra como la indicación de texto, o sugerencia, en un control de edición cuando el control está vacío.

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
[fuera] Puntero a una cadena que contiene el texto de referencia.

*cchText*<br/>
[en] El número de caracteres que se pueden recibir. Este número incluye el carácter NULL de terminación.

### <a name="return-value"></a>Valor devuelto

Para la primera sobrecarga, TRUE si el método es correcto; de lo contrario FALSO.

Para la segunda sobrecarga, un [CString](../../atl-mfc-shared/using-cstring.md) que contiene el texto cue si el método es correcto; de lo contrario, la cadena vacía ("").

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje EM_GETCUEBANNER,](/windows/win32/Controls/em-getcuebanner) que se describe en el Windows SDK. Para obtener más información, consulte la macro [Edit_GetCueBannerText.](/windows/win32/api/commctrl/nf-commctrl-edit_getcuebannertext)

## <a name="ceditgetfirstvisibleline"></a><a name="getfirstvisibleline"></a>CEdit::GetFirstVisibleLine

Llame a esta función para determinar la línea visible superior en un control de edición.

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>Valor devuelto

El índice de base cero de la línea visible superior. Para los controles de edición de una sola línea, el valor devuelto es 0.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [EM_GETFIRSTVISIBLELINE](/windows/win32/Controls/em-getfirstvisibleline) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

## <a name="ceditgethandle"></a><a name="gethandle"></a>CEdit::GetHandle

Llame a esta función para recuperar un identificador de la memoria asignada actualmente para un control de edición de varias líneas.

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador de memoria local que identifica el búfer que contiene el contenido del control de edición. Si se produce un error, como enviar el mensaje a un control de edición de una sola línea, el valor devuelto es 0.

### <a name="remarks"></a>Observaciones

El identificador es un identificador de memoria local y puede ser utilizado por cualquiera de las funciones de memoria **local** de Windows que toman un identificador de memoria local como parámetro.

`GetHandle`solo se procesa mediante controles de edición de varias líneas.

Llame `GetHandle` a un control de edición de varias líneas en un cuadro de diálogo solo si el cuadro de diálogo se creó con la DS_LOCALEDIT marca de estilo establecida. Si no se establece el estilo DS_LOCALEDIT, obtendrá un valor devuelto distinto de cero, pero no podrá usar el valor devuelto.

> [!NOTE]
> `GetHandle`no funcionará con Windows 95/98. Si llama `GetHandle` a Windows 95/98, devolverá NULL. `GetHandle`funcionará según lo documentado en Windows NT, versiones 3.51 y posteriores.

Para obtener más información, consulte [EM_GETHANDLE](/windows/win32/Controls/em-gethandle) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

## <a name="ceditgethighlight"></a><a name="gethighlight"></a>CEdit::GetHighlight

Obtiene los índices del primer y último carácter de un intervalo de texto que se resalta en el control de edición actual.

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pichStart*|[fuera] El índice de base cero del primer carácter del intervalo de texto que se resalta.|
|*pichEnd*|[fuera] El índice de base cero del último carácter del intervalo de texto que se resalta.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje EM_GETHILITE,](/windows/win32/Controls/em-gethilite) que se describe en el Windows SDK. Ambos `SetHighlight` `GetHighlight` y actualmente están habilitados solo para compilaciones UNICODE.

## <a name="ceditgetlimittext"></a><a name="getlimittext"></a>CEdit::GetLimitText

Llame a esta función miembro `CEdit` para obtener el límite de texto para este objeto.

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>Valor devuelto

El límite de texto actual, en `CEdit` TCANRs, para este objeto.

### <a name="remarks"></a>Observaciones

El límite de texto es la cantidad máxima de texto, en TCHARs, que el control de edición puede aceptar.

> [!NOTE]
> Esta función miembro está disponible a partir de Windows 95 y Windows NT 4.0.

Para obtener más información, consulte [EM_GETLIMITTEXT](/windows/win32/Controls/em-getlimittext) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

## <a name="ceditgetline"></a><a name="getline"></a>CEdit::GetLine

Llame a esta función para recuperar una línea de texto de un control de edición y la coloca en *lpszBuffer*.

```
int GetLine(
    int nIndex,
    LPTSTR lpszBuffer) const;

int GetLine(
    int nIndex,
    LPTSTR lpszBuffer,
    int nMaxLength) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el número de línea que se va a recuperar de un control de edición de varias líneas. Los números de línea se basan en cero; un valor de 0 especifica la primera línea. Este parámetro se omite mediante un control de edición de una sola línea.

*lpszBuffer*<br/>
Apunta al búfer que recibe una copia de la línea. La primera palabra del búfer debe especificar el número máximo de TCHAR que se pueden copiar en el búfer.

*nMaxLength*<br/>
Especifica el número máximo de caracteres TCHAR que se pueden copiar en el búfer. `GetLine`coloca este valor en la primera palabra de *lpszBuffer* antes de realizar la llamada a Windows.

### <a name="return-value"></a>Valor devuelto

Número de caracteres que realmente se va a copiar. El valor devuelto es 0 si el número de línea especificado por *nIndex* es mayor que el número de líneas en el control de edición.

### <a name="remarks"></a>Observaciones

La línea copiada no contiene un carácter de terminación nula.

Para obtener más información, consulte [EM_GETLINE](/windows/win32/Controls/em-getline) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::GetLineCount](#getlinecount).

## <a name="ceditgetlinecount"></a><a name="getlinecount"></a>CEdit::GetLineCount

Llame a esta función para recuperar el número de líneas en un control de edición de varias líneas.

```
int GetLineCount() const;
```

### <a name="return-value"></a>Valor devuelto

Entero que contiene el número de líneas en el control de edición de varias líneas. Si no se ha introducido ningún texto en el control de edición, el valor devuelto es 1.

### <a name="remarks"></a>Observaciones

`GetLineCount`solo se procesa mediante controles de edición de varias líneas.

Para obtener más información, consulte [EM_GETLINECOUNT](/windows/win32/Controls/em-getlinecount) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

## <a name="ceditgetmargins"></a><a name="getmargins"></a>CEdit::GetMargins

Llame a esta función miembro para recuperar los márgenes izquierdo y derecho de este control de edición.

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>Valor devuelto

El ancho del margen izquierdo en el orden bajo WORD y el ancho del margen derecho en el orden alto WORD.

### <a name="remarks"></a>Observaciones

Los márgenes se miden en píxeles.

> [!NOTE]
> Esta función miembro está disponible a partir de Windows 95 y Windows NT 4.0.

Para obtener más información, consulte [EM_GETMARGINS](/windows/win32/Controls/em-getmargins) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditgetmodify"></a><a name="getmodify"></a>CEdit::GetModify

Llame a esta función para determinar si se ha modificado el contenido de un control de edición.

```
BOOL GetModify() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha modificado el contenido del control de edición; 0 si han permanecido inalterados.

### <a name="remarks"></a>Observaciones

Windows mantiene una marca interna que indica si se ha cambiado el contenido del control de edición. Esta marca se borra cuando se crea por primera vez el control de edición y también se puede borrar mediante una llamada a la [SetModify](#setmodify) función miembro.

Para obtener más información, consulte [EM_GETMODIFY](/windows/win32/Controls/em-getmodify) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

## <a name="ceditgetpasswordchar"></a><a name="getpasswordchar"></a>CEdit::GetPasswordChar

Llame a esta función para recuperar el carácter de contraseña que se muestra en un control de edición cuando el usuario escribe texto.

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>Valor devuelto

Especifica el carácter que se mostrará en lugar del carácter que el usuario ha escrito. El valor devuelto es NULL si no existe ningún carácter de contraseña.

### <a name="remarks"></a>Observaciones

Si crea el control de edición con el estilo ES_PASSWORD, el archivo DLL que admite el control determina el carácter de contraseña predeterminado. El manifiesto o el método [InitCommonControlsEx](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex) determina qué ARCHIVO DLL admite el control de edición. Si user32.dll admite el control de edición, el carácter de contraseña predeterminado es ASTERISK ('*', U+002A). Si comctl32.dll versión 6 admite el control de edición, el carácter predeterminado es NEGRO CIRCULO (''', U+25CF). Para obtener más información acerca de qué DLL y versión admite los controles comunes, vea [Versiones](/previous-versions/windows/desktop/legacy/bb776779\(v=vs.85\))de shell y controles comunes .

Este método envía el [mensaje EM_GETPASSWORDCHAR,](/windows/win32/Controls/em-getpasswordchar) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

## <a name="ceditgetrect"></a><a name="getrect"></a>CEdit::GetRect

Llame a esta función para obtener el rectángulo de formato de un control de edición.

```cpp
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a `RECT` la estructura que recibe el rectángulo de formato.

### <a name="remarks"></a>Observaciones

El rectángulo de formato es el rectángulo limitante del texto, que es independiente del tamaño de la ventana de control de edición.

El rectángulo de formato de un control de edición de varias líneas se puede modificar mediante el [SetRect](#setrect) y [SetRectNP](#setrectnp) funciones miembro.

Para obtener más información, consulte [EM_GETRECT](/windows/win32/Controls/em-getrect) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::LimitText](#limittext).

## <a name="ceditgetsel"></a><a name="getsel"></a>CEdit::GetSel

Llame a esta función para obtener las posiciones de carácter inicial y final de la selección actual (si existe) en un control de edición, utilizando el valor devuelto o los parámetros.

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>Parámetros

*nStartChar*<br/>
Referencia a un entero que recibirá la posición del primer carácter de la selección actual.

*nEndChar*<br/>
Referencia a un entero que recibirá la posición del primer carácter no seleccionado más allá del final de la selección actual.

### <a name="return-value"></a>Valor devuelto

La versión que devuelve un DWORD devuelve un valor que contiene la posición inicial en la palabra de orden bajo y la posición del primer carácter no seleccionado después del final de la selección en la palabra de orden superior.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [EM_GETSEL](/windows/win32/Controls/em-getsel) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

## <a name="cedithideballoontip"></a><a name="hideballoontip"></a>CEdit::HideBalloonTip

Oculta cualquier sugerencia de globo asociada con el control de edición actual.

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Esta función envía el [mensaje EM_HIDEBALLOONTIP,](/windows/win32/Controls/em-hideballoontip) que se describe en el Windows SDK.

## <a name="ceditlimittext"></a><a name="limittext"></a>CEdit::LimitText

Llame a esta función para limitar la longitud del texto que el usuario puede escribir en un control de edición.

```cpp
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>Parámetros

*nChars*<br/>
Especifica la longitud (en TCAN) del texto que el usuario puede escribir. Si este parámetro es 0, la longitud del texto se establece en UINT_MAX bytes. Este es el comportamiento predeterminado.

### <a name="remarks"></a>Observaciones

Cambiar el límite de texto restringe solo el texto que el usuario puede introducir. No tiene ningún efecto en ningún texto que ya esté en el control de edición, ni afecta `CWnd`a la longitud del texto copiado en el control de edición por el [SetWindowText](cwnd-class.md#setwindowtext) función miembro en . Si una aplicación `SetWindowText` utiliza la función para colocar más texto en `LimitText`un control de edición que el especificado en la llamada a , el usuario puede eliminar cualquiera de los textos dentro del control de edición. Sin embargo, el límite de texto impedirá que el usuario reemplace el texto existente con texto nuevo, a menos que la eliminación de la selección actual haga que el texto caiga por debajo del límite de texto.

> [!NOTE]
> En Win32 (Windows NT y Windows 95/98), [SetLimitText](#setlimittext) reemplaza esta función.

Para obtener más información, consulte [EM_LIMITTEXT](/windows/win32/Controls/em-limittext) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

## <a name="ceditlinefromchar"></a><a name="linefromchar"></a>CEdit::LineFromChar

Llame a esta función para recuperar el número de línea de la línea que contiene el índice de caracteres especificado.

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Contiene el valor de índice de base cero para el carácter deseado en el texto del control de edición o contiene -1. Si *nIndex* es -1, especifica la línea actual, es decir, la línea que contiene el intercalador.

### <a name="return-value"></a>Valor devuelto

El número de línea de base cero de la línea que contiene el índice de caracteres especificado por *nIndex*. Si *nIndex* es -1, se devuelve el número de la línea que contiene el primer carácter de la selección. Si no hay ninguna selección, se devuelve el número de línea actual.

### <a name="remarks"></a>Observaciones

Un índice de caracteres es el número de caracteres desde el principio del control de edición.

Esta función miembro solo se utiliza en controles de edición de varias líneas.

Para obtener más información, consulte [EM_LINEFROMCHAR](/windows/win32/Controls/em-linefromchar) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

## <a name="ceditlineindex"></a><a name="lineindex"></a>CEdit::LineIndex

Llame a esta función para recuperar el índice de caracteres de una línea dentro de un control de edición de varias líneas.

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>Parámetros

*nLínea*<br/>
Contiene el valor de índice de la línea deseada en el texto del control de edición o contiene -1. Si *nLine* es -1, especifica la línea actual, es decir, la línea que contiene el intercalador.

### <a name="return-value"></a>Valor devuelto

El índice de caracteres de la línea especificada en *nLine* o -1 si el número de línea especificado es mayor que el número de líneas en el control de edición.

### <a name="remarks"></a>Observaciones

El índice de caracteres es el número de caracteres desde el principio del control de edición hasta la línea especificada.

Esta función miembro solo se procesa mediante controles de edición de varias líneas.

Para obtener más información, consulte [EM_LINEINDEX](/windows/win32/controls/em-lineindex) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

## <a name="ceditlinelength"></a><a name="linelength"></a>CEdit::LineLength

Recupera la longitud de una línea en un control de edición.

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>Parámetros

*nLínea*<br/>
El índice de base cero de un carácter de la línea cuya longitud se va a recuperar. El valor predeterminado es -1.

### <a name="return-value"></a>Valor devuelto

Para los controles de edición de una sola línea, el valor devuelto es la longitud, en TCAN, del texto en el control de edición.

Para los controles de edición multilínea, el valor devuelto es la longitud, en TCAN, de la línea especificada por el *nLine* parámetro. Para el texto ANSI, la longitud es el número de bytes de la línea; para el texto Unicode, la longitud es el número de caracteres de la línea. La longitud no incluye el carácter de retorno de carro al final de la línea.

Si el *nLine* parámetro es mayor que el número de caracteres en el control, el valor devuelto es cero.

Si el *nLine* parámetro es -1, el valor devuelto es el número de caracteres no seleccionados en las líneas que contienen caracteres seleccionados. Por ejemplo, si la selección se extiende desde el cuarto carácter de una línea hasta el octavo carácter desde el final de la siguiente línea, el valor devuelto es 10. Es decir, tres caracteres en la primera línea y siete en la siguiente.

Para obtener más información sobre el tipo TCHAR, vea la fila TCHAR de la tabla Tipos de datos de [Windows](/windows/win32/WinProg/windows-data-types).

### <a name="remarks"></a>Observaciones

Este método es compatible con el [mensaje de EM_LINELENGTH,](/windows/win32/Controls/em-linelength) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::LineIndex](#lineindex).

## <a name="ceditlinescroll"></a><a name="linescroll"></a>CEdit::LineScroll

Llame a esta función para desplazar el texto de un control de edición de varias líneas.

```cpp
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>Parámetros

*nLines*<br/>
Especifica el número de líneas que se desplazará verticalmente.

*nChars*<br/>
Especifica el número de posiciones de caracteres que se desplazará horizontalmente. Este valor se omite si el control de edición tiene el estilo ES_RIGHT o ES_CENTER.

### <a name="remarks"></a>Observaciones

Esta función miembro solo se procesa mediante controles de edición de varias líneas.

El control de edición no se desplaza verticalmente más allá de la última línea de texto en el control de edición. Si la línea actual más el número de líneas especificadas por *nLines* supera el número total de líneas en el control de edición, el valor se ajusta para que la última línea del control de edición se desplace a la parte superior de la ventana de control de edición.

`LineScroll`se puede utilizar para desplazarse horizontalmente más allá del último carácter de cualquier línea.

Para obtener más información, consulte [EM_LINESCROLL](/windows/win32/Controls/em-linescroll) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::GetFirstVisibleLine](#getfirstvisibleline).

## <a name="ceditpaste"></a><a name="paste"></a>CEdit::Paste

Llame a esta función para insertar `CEdit` los datos del Portapapeles en el punto de inserción.

```cpp
void Paste();
```

### <a name="remarks"></a>Observaciones

Los datos solo se insertan si el Portapapeles contiene datos en formato CF_TEXT.

Para obtener más información, consulte [WM_PASTE](/windows/win32/dataxchg/wm-paste) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

## <a name="ceditposfromchar"></a><a name="posfromchar"></a>CEdit::PosFromChar

Llame a esta función para obtener la posición (esquina `CEdit` superior izquierda) de un carácter determinado dentro de este objeto.

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>Parámetros

*Nchar*<br/>
El índice de base cero del carácter especificado.

### <a name="return-value"></a>Valor devuelto

Las coordenadas de la esquina superior izquierda del carácter especificado por *nChar*.

### <a name="remarks"></a>Observaciones

El carácter se especifica dando su valor de índice de base cero. Si *nChar* es mayor que el índice `CEdit` del último carácter de este objeto, el valor devuelto `CEdit` especifica las coordenadas de la posición del carácter justo después del último carácter de este objeto.

> [!NOTE]
> Esta función miembro está disponible a partir de Windows 95 y Windows NT 4.0.

Para obtener más información, consulte [EM_POSFROMCHAR](/windows/win32/Controls/em-posfromchar) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::LineFromChar](#linefromchar).

## <a name="ceditreplacesel"></a><a name="replacesel"></a>CEdit::ReplaceSel

Llame a esta función para reemplazar la selección actual en un control de edición con el texto especificado por *lpszNewText*.

```cpp
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>Parámetros

*lpszNewText*<br/>
Apunta a una cadena terminada en null que contiene el texto de reemplazo.

*bCanUndo*<br/>
Para especificar que se puede deshacer esta función, establezca el valor de este parámetro en TRUE . El valor predeterminado es FALSE.

### <a name="remarks"></a>Observaciones

Reemplaza solo una parte del texto en un control de edición. Si desea reemplazar todo el texto, utilice el [CWnd::SetWindowText](cwnd-class.md#setwindowtext) función miembro.

Si no hay ninguna selección actual, el texto de sustitución se inserta en la ubicación actual del cursor.

Para obtener más información, consulte [EM_REPLACESEL](/windows/win32/Controls/em-replacesel) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::LineIndex](#lineindex).

## <a name="ceditsetcuebanner"></a><a name="setcuebanner"></a>CEdit::SetCueBanner

Establece el texto que se muestra como la indicación de texto, o sugerencia, en un control de edición cuando el control está vacío.

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
[en] Puntero a una cadena que contiene la cue que se va a mostrar en el control de edición.

*fDrawWhenFocused*<br/>
[en] Si FALSE, el banner cue no se dibuja cuando el usuario hace clic en el control de edición y proporciona al control el foco.

Si es TRUE, el banner de referencia se dibuja incluso cuando el control tiene el foco. El banner cue desaparece cuando el usuario comienza a escribir el control.

El valor predeterminado es FALSE.

### <a name="return-value"></a>Valor devuelto

TRUESi el método se realiza correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje EM_SETCUEBANNER,](/windows/win32/Controls/em-setcuebanner) que se describe en el Windows SDK. Para obtener más información, consulte la macro [Edit_SetCueBannerTextFocused.](/windows/win32/api/commctrl/nf-commctrl-edit_setcuebannertextfocused)

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el [CEdit::SetCueBanner](#setcuebanner) método.

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

## <a name="ceditsethandle"></a><a name="sethandle"></a>CEdit::SetHandle

Llame a esta función para establecer el identificador en la memoria local que usará un control de edición de varias líneas.

```cpp
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>Parámetros

*hBuffer*<br/>
Contiene un identificador de la memoria local. Este identificador debe haber sido creado por una llamada anterior a la [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) función de Windows mediante el LMEM_MOVEABLE marca. Se supone que la memoria contiene una cadena terminada en null. Si este no es el caso, el primer byte de la memoria asignada debe establecerse en 0.

### <a name="remarks"></a>Observaciones

A continuación, el control de edición usará este búfer para almacenar el texto que se muestra actualmente en lugar de asignar su propio búfer.

Esta función miembro solo se procesa mediante controles de edición de varias líneas.

Antes de que una aplicación establece un nuevo identificador de memoria, debe usar el [GetHandle](#gethandle) `LocalFree` función miembro para obtener el identificador para el búfer de memoria actual y liberar esa memoria mediante la función de Windows.

`SetHandle`borra el búfer de deshacer (la [canUndo](#canundo) función miembro, a continuación, devuelve 0) y el indicador de modificación interna (el [GetModify](#getmodify) función miembro, a continuación, devuelve 0). Se vuelve a dibujar la ventana de control de edición.

Puede utilizar esta función miembro en un control de edición de varias líneas en un cuadro de diálogo solo si ha creado el cuadro de diálogo con la DS_LOCALEDIT marca de estilo establecida.

> [!NOTE]
> `GetHandle`no funcionará con Windows 95/98. Si llama `GetHandle` a Windows 95/98, devolverá NULL. `GetHandle`funcionará según lo documentado en Windows NT, versiones 3.51 y posteriores.

Para obtener más información, vea [EM_SETHANDLE](/windows/win32/Controls/em-sethandle), [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)y [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

## <a name="ceditsethighlight"></a><a name="sethighlight"></a>CEdit::SetHighlight

Resalta un rango de texto que se muestra en el control de edición actual.

```cpp
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*ichStart*|[en] El índice de base cero del primer carácter del intervalo de texto que se va a resaltar.|
|*ichEnd*|[en] El índice de base cero del último carácter del intervalo de texto que se va a resaltar.|

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje EM_SETHILITE,](/windows/win32/Controls/em-sethilite) que se describe en el Windows SDK.  Este método envía el [mensaje EM_SETHILITE,](/windows/win32/Controls/em-sethilite) que se describe en el Windows SDK. Ambos `SetHighlight` `GetHighlight` y están habilitados solo para compilaciones UNICODE.

## <a name="ceditsetlimittext"></a><a name="setlimittext"></a>CEdit::SetLimitText

Llame a esta función miembro `CEdit` para establecer el límite de texto para este objeto.

```cpp
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>Parámetros

*nMax*<br/>
El nuevo límite de texto, en caracteres.

### <a name="remarks"></a>Observaciones

El límite de texto es la cantidad máxima de texto, en caracteres, que el control de edición puede aceptar.

Cambiar el límite de texto restringe solo el texto que el usuario puede introducir. No tiene ningún efecto en ningún texto que ya esté en el control de edición, ni afecta `CWnd`a la longitud del texto copiado en el control de edición por el [SetWindowText](cwnd-class.md#setwindowtext) función miembro en . Si una aplicación `SetWindowText` utiliza la función para colocar más texto en `LimitText`un control de edición que el especificado en la llamada a , el usuario puede eliminar cualquiera de los textos dentro del control de edición. Sin embargo, el límite de texto impedirá que el usuario reemplace el texto existente con texto nuevo, a menos que la eliminación de la selección actual haga que el texto caiga por debajo del límite de texto.

Esta función reemplaza [LimitText](#limittext) en Win32.

Para obtener más información, consulte [EM_SETLIMITTEXT](/windows/win32/Controls/em-setlimittext) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditsetmargins"></a><a name="setmargins"></a>CEdit::SetMargins

Llame a este método para establecer los márgenes izquierdo y derecho de este control de edición.

```cpp
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>Parámetros

*nIzquierda*<br/>
El ancho del nuevo margen izquierdo, en píxeles.

*nRight*<br/>
El ancho del nuevo margen derecho, en píxeles.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Esta función miembro está disponible a partir de Windows 95 y Windows NT 4.0.

Para obtener más información, consulte [EM_SETMARGINS](/windows/win32/Controls/em-setmargins) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

## <a name="ceditsetmodify"></a><a name="setmodify"></a>CEdit::SetModify

Llame a esta función para establecer o borrar el indicador modificado para un control de edición.

```cpp
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parámetros

*bModificado*<br/>
Un valor de TRUE indica que el texto se ha modificado y un valor de FALSE indica que no se modifica. De forma predeterminada, se establece el indicador modificado.

### <a name="remarks"></a>Observaciones

El indicador modificado indica si se ha modificado o no el texto del control de edición. Se establece automáticamente cada vez que el usuario cambia el texto. Su valor se puede recuperar con el [GetModify](#getmodify) función miembro.

Para obtener más información, consulte [EM_SETMODIFY](/windows/win32/Controls/em-setmodify) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::GetModify](#getmodify).

## <a name="ceditsetpasswordchar"></a><a name="setpasswordchar"></a>CEdit::SetPasswordChar

Llame a esta función para establecer o quitar un carácter de contraseña que se muestra en un control de edición cuando el usuario escribe texto.

```cpp
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>Parámetros

*Ch*<br/>
Especifica el carácter que se mostrará en lugar del carácter escrito por el usuario. Si *ch* es 0, se muestran los caracteres reales escritos por el usuario.

### <a name="remarks"></a>Observaciones

Cuando se establece un carácter de contraseña, ese carácter se muestra para cada carácter que el usuario escribe.

Esta función miembro no tiene ningún efecto en un control de edición de varias líneas.

Cuando `SetPasswordChar` se llama a `CEdit` la función miembro, volverá a dibujar todos los caracteres visibles utilizando el carácter especificado por *ch*.

Si el control de edición se crea con el estilo <strong>\*</strong> [ES_PASSWORD,](styles-used-by-mfc.md#edit-styles) el carácter de contraseña predeterminado se establece en un asterisco ( ). Este estilo se `SetPasswordChar` elimina si se llama con *ch* establecido en 0.

Para obtener más información, consulte [EM_SETPASSWORDCHAR](/windows/win32/Controls/em-setpasswordchar) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

## <a name="ceditsetreadonly"></a><a name="setreadonly"></a>CEdit::SetReadOnly

Llama a esta función para establecer el estado de solo lectura de un control de edición.

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>Parámetros

*bReadOnly*<br/>
Especifica si se debe establecer o quitar el estado de solo lectura del control de edición. Un valor de TRUE establece el estado en de solo lectura; un valor de FALSE establece el estado en lectura/escritura.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realiza correctamente, o 0 si se produce un error.

### <a name="remarks"></a>Observaciones

La configuración actual se puede encontrar probando el [indicador ES_READONLY](styles-used-by-mfc.md#edit-styles) en el valor devuelto de [CWnd::GetStyle](cwnd-class.md#getstyle).

Para obtener más información, consulte [EM_SETREADONLY](/windows/win32/Controls/em-setreadonly) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

## <a name="ceditsetrect"></a><a name="setrect"></a>CEdit::SetRect

Llame a esta función para establecer las dimensiones de un rectángulo mediante las coordenadas especificadas.

```cpp
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a `RECT` la `CRect` estructura u objeto que especifica las nuevas dimensiones del rectángulo de formato.

### <a name="remarks"></a>Observaciones

Este miembro solo se procesa mediante controles de edición de varias líneas.

Se `SetRect` utiliza para establecer el rectángulo de formato de un control de edición de varias líneas. El rectángulo de formato es el rectángulo limitante del texto, que es independiente del tamaño de la ventana de control de edición. Cuando se crea por primera vez el control de edición, el rectángulo de formato es el mismo que el área de cliente de la ventana de control de edición. Mediante el `SetRect` uso de la función miembro, una aplicación puede hacer que el rectángulo de formato mayor o menor que la ventana de control de edición.

Si el control de edición no tiene barra de desplazamiento, el texto se recortará, no se ajustará, si el rectángulo de formato se hace más grande que la ventana. Si el control de edición contiene un borde, el rectángulo de formato se reduce por el tamaño del borde. Si ajusta el rectángulo `GetRect` devuelto por la función miembro, debe quitar el `SetRect`tamaño del borde antes de pasar el rectángulo a .

Cuando `SetRect` se llama, el texto del control de edición también se vuelve a formatear y se vuelve a mostrar.

Para obtener más información, consulte [EM_SETRECT](/windows/win32/Controls/em-setrect) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

## <a name="ceditsetrectnp"></a><a name="setrectnp"></a>CEdit::SetRectNP

Llame a esta función para establecer el rectángulo de formato de un control de edición de varias líneas.

```cpp
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a `RECT` una `CRect` estructura u objeto que especifica las nuevas dimensiones del rectángulo.

### <a name="remarks"></a>Observaciones

El rectángulo de formato es el rectángulo limitante del texto, que es independiente del tamaño de la ventana de control de edición.

`SetRectNP`es idéntica `SetRect` a la función miembro, excepto que la ventana de control de edición no se vuelve a dibujar.

Cuando se crea por primera vez el control de edición, el rectángulo de formato es el mismo que el área de cliente de la ventana de control de edición. Al llamar `SetRectNP` a la función miembro, una aplicación puede hacer que el rectángulo de formato mayor o menor que la ventana de control de edición.

Si el control de edición no tiene barra de desplazamiento, el texto se recortará, no se ajustará, si el rectángulo de formato se hace más grande que la ventana.

Este miembro solo se procesa mediante controles de edición de varias líneas.

Para obtener más información, consulte [EM_SETRECTNP](/windows/win32/Controls/em-setrectnp) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::SetRect](#setrect).

## <a name="ceditsetsel"></a><a name="setsel"></a>CEdit::SetSel

Llame a esta función para seleccionar un intervalo de caracteres en un control de edición.

```cpp
void SetSel(
    DWORD dwSelection,
    BOOL bNoScroll = FALSE);

void SetSel(
    int nStartChar,
    int nEndChar,
    BOOL bNoScroll = FALSE);
```

### <a name="parameters"></a>Parámetros

*dwSelection*<br/>
Especifica la posición inicial en la palabra de orden bajo y la posición final en la palabra de orden superior. Si la palabra de orden bajo es 0 y la palabra de orden superior es -1, se selecciona todo el texto del control de edición. Si la palabra de orden bajo es -1, se elimina cualquier selección actual.

*bNoScroll*<br/>
Indica si el intercalador debe desplazarse a la vista. Si FALSE, el intercalador se desplaza a la vista. Si es TRUE, el intercalador no se desplaza a la vista.

*nStartChar*<br/>
Especifica la posición inicial. Si *nStartChar* es 0 y *nEndChar* es -1, se selecciona todo el texto del control de edición. Si *nStartChar* es -1, se elimina cualquier selección actual.

*nEndChar*<br/>
Especifica la posición final.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [EM_SETSEL](/windows/win32/Controls/em-setsel) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::GetSel](#getsel).

## <a name="ceditsettabstops"></a><a name="settabstops"></a>CEdit::SetTabStops

Llame a esta función para establecer las tabulaciones en un control de edición de varias líneas.

```cpp
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parámetros

*cxEachStop*<br/>
Especifica que las tabulaciones se deben establecer en cada unidad de cuadro de diálogo *cxEachStop.*

*nTabStops*<br/>
Especifica el número de tabulaciones contenidas en *rgTabStops*. Este número debe ser mayor que 1.

*rgTabStops*<br/>
Apunta a una matriz de enteros sin signo que especifican las tabulaciones en unidades de diálogo. Una unidad de diálogo es una distancia horizontal o vertical. Una unidad de diálogo horizontal es igual a una cuarta parte de la unidad de anchura base del cuadro de diálogo actual, y 1 unidad de diálogo vertical es igual a una octava parte de la unidad de altura base del cuadro de diálogo actual. Las unidades base del cuadro de diálogo se calculan en función de la altura y la anchura de la fuente del sistema actual. La `GetDialogBaseUnits` función Windows devuelve las unidades base del cuadro de diálogo actual en píxeles.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se establecieron las pestañas; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Cuando el texto se copia en un control de edición de varias líneas, cualquier carácter de tabulación del texto hará que se genere espacio hasta la siguiente tabulación.

Para establecer tabulaciones al tamaño predeterminado de 32 unidades de cuadro de diálogo, llame a la versión sin parámetros de esta función miembro. Para establecer tabulaciones en un tamaño distinto de 32, llame a la versión con el *cxEachStop* parámetro. Para establecer tabulaciones en una matriz de tamaños, utilice la versión con dos parámetros.

Esta función miembro solo se procesa mediante controles de edición de varias líneas.

`SetTabStops`no vuelve a dibujar automáticamente la ventana de edición. Si cambia las tabulaciones del texto que ya está en el control de edición, llame a [CWnd::InvalidateRect](cwnd-class.md#invalidaterect) para volver a dibujar la ventana de edición.

Para obtener más información, vea [EM_SETTABSTOPS](/windows/win32/Controls/em-settabstops) y [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEditView::SetTabStops](ceditview-class.md#settabstops).

## <a name="ceditshowballoontip"></a><a name="showballoontip"></a>CEdit::ShowBalloonTip

Muestra una sugerencia de globo asociada al control de edición actual.

```
BOOL ShowBalloonTip(PEDITBALLOONTIP pEditBalloonTip);

BOOL ShowBalloonTip(
    LPCWSTR lpszTitle,
    LPCWSTR lpszText,
    INT ttiIcon = TTI_NONE);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pEditBalloonTip*|[en] Puntero a una estructura [EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip) que describe la punta del globo.|
|*lpszTitle*|[en] Puntero a una cadena Unicode que contiene el título de la sugerencia de globo.|
|*lpszText*|[en] Puntero a una cadena Unicode que contiene el texto de la sugerencia de globo.|
|*ttiIcon*|[en] **InT** que especifica el tipo de icono que se va a asociar con la punta del globo. El valor predeterminado es TTI_NONE. Para obtener más `ttiIcon` información, consulte el miembro de la [editABALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip) estructura.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Esta función envía el [mensaje EM_SHOWBALLOONTIP,](/windows/win32/Controls/em-showballoontip) que se describe en el Windows SDK. Para obtener más información, consulte la macro [Edit_ShowBalloonTip.](/windows/win32/api/commctrl/nf-commctrl-edit_showballoontip)

### <a name="example"></a>Ejemplo

En el ejemplo de `m_cedit`código siguiente se define una variable, , que se utiliza para tener acceso al control de edición actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra una sugerencia de globo para un control de edición. El [método CEdit::ShowBalloonTip](#showballoontip) especifica un título y un texto de sugerencia de globo.

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

## <a name="ceditundo"></a><a name="undo"></a>CEdit::Deshacer

Llame a esta función para deshacer la última operación de control de edición.

```
BOOL Undo();
```

### <a name="return-value"></a>Valor devuelto

Para un control de edición de una sola línea, el valor devuelto siempre es distinto de cero. Para un control de edición de varias líneas, el valor devuelto es distinto de cero si la operación de deshacer es correcta, o 0 si se produce un error en la operación de deshacer.

### <a name="remarks"></a>Observaciones

También se puede deshacer una operación de deshacer. Por ejemplo, puede restaurar el texto `Undo`eliminado con la primera llamada a . Siempre que no haya ninguna operación de edición que intervenga, puede eliminar el texto de nuevo con una segunda llamada a `Undo`.

Para obtener más información, consulte [EM_UNDO](/windows/win32/Controls/em-undo) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo cmNCTRL2 de MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](cwnd-class.md)<br/>
[CButton (clase)](cbutton-class.md)<br/>
[CComboBox (clase)](ccombobox-class.md)<br/>
[CListBox (clase)](clistbox-class.md)<br/>
[CScrollBar (clase)](cscrollbar-class.md)<br/>
[Clase CStatic](cstatic-class.md)<br/>
[Clase CDialog](cdialog-class.md)
