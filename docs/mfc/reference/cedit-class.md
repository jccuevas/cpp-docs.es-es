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
ms.openlocfilehash: 45c03d142c34186660aa2715081ffb0f45e85ccc
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58773754"
---
# <a name="cedit-class"></a>CEdit Class

Proporciona la funcionalidad de un control de edición de Windows.

## <a name="syntax"></a>Sintaxis

```
class CEdit : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CEdit::CEdit](#cedit)|Construye un `CEdit` objeto de control.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CEdit::CanUndo](#canundo)|Determina si se puede deshacer una operación de control de edición.|
|[CEdit::CharFromPos](#charfrompos)|Recupera los índices de la línea y el carácter para el carácter más próximo a una posición especificada.|
|[CEdit::Clear](#clear)|Elimina (desactiva) la selección actual (si existe) en la edición del control.|
|[CEdit::Copy](#copy)|Copia la selección actual (si existe) en el control de edición en el Portapapeles con formato CF_TEXT.|
|[CEdit::Create](#create)|Crea el control de edición de Windows y lo adjunta a la `CEdit` objeto.|
|[CEdit::Cut](#cut)|(Cortes) elimina la selección actual (si existe) en la edición del control y copia el texto eliminado en el Portapapeles en CF_TEXT formato.|
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|Restablece el control de la marca de deshacer de la edición (borra).|
|[CEdit::FmtLines](#fmtlines)|Establece la inclusión de caracteres de salto de línea automático activado o desactivado dentro de un control de edición de varias líneas.|
|[CEdit::GetCueBanner](#getcuebanner)|Recupera el texto que se muestra como la pila de texto, o sugerencia, en un control de edición cuando el control está vacío y no tiene el foco.|
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|Determina la línea superior visible en un control de edición.|
|[CEdit::GetHandle](#gethandle)|Recupera un identificador de la memoria asignada actualmente a un control de edición de varias líneas.|
|[CEdit::GetHighlight](#gethighlight)|Obtiene los índices de iniciales y finales de caracteres en un intervalo de texto que está resaltado en el control de edición actual.|
|[CEdit::GetLimitText](#getlimittext)|Obtiene la cantidad máxima de texto esto `CEdit` puede contener.|
|[CEdit::GetLine](#getline)|Recupera una línea de texto de un control de edición.|
|[CEdit::GetLineCount](#getlinecount)|Recupera el número de líneas en un control de edición de varias líneas.|
|[CEdit::GetMargins](#getmargins)|Obtiene los márgenes izquierdos y derecho para este `CEdit`.|
|[CEdit::GetModify](#getmodify)|Determina si se ha modificado el contenido de un control de edición.|
|[CEdit::GetPasswordChar](#getpasswordchar)|Recupera el carácter de contraseña que se muestran en un control de edición cuando el usuario escribe texto.|
|[CEdit::GetRect](#getrect)|Obtiene el rectángulo de formato de un control de edición.|
|[CEdit::GetSel](#getsel)|Obtiene las posiciones de primer y último carácter de la selección actual en un control de edición.|
|[CEdit::HideBalloonTip](#hideballoontip)|Oculta un globo de sugerencias asociado al control de edición actual.|
|[CEdit::LimitText](#limittext)|Limita la longitud del texto que el usuario puede escribir en un control de edición.|
|[CEdit::LineFromChar](#linefromchar)|Recupera el número de línea de la línea que contiene el índice de carácter especificado.|
|[CEdit::LineIndex](#lineindex)|Recupera el índice de carácter de una línea dentro de un control de edición de varias líneas.|
|[CEdit::LineLength](#linelength)|Recupera la longitud de una línea en un control de edición.|
|[CEdit::LineScroll](#linescroll)|Desplaza el texto de un control de edición de varias líneas.|
|[CEdit::Paste](#paste)|Inserta los datos del Portapapeles en el control de edición en la posición actual del cursor. Datos se insertan solo si el Portapapeles contiene datos con formato CF_TEXT.|
|[CEdit::PosFromChar](#posfromchar)|Recupera las coordenadas de la esquina superior izquierda de un índice de carácter especificado.|
|[CEdit::ReplaceSel](#replacesel)|Reemplaza la selección actual en un control de edición con el texto especificado.|
|[CEdit::SetCueBanner](#setcuebanner)|Establece el texto que se muestra como la pila de texto o sugerencia, en un control de edición cuando el control está vacío y no tiene el foco.|
|[CEdit::SetHandle](#sethandle)|Establece el identificador en la memoria local que se usará en un control de edición de varias líneas.|
|[CEdit::SetHighlight](#sethighlight)|Información destacada de un intervalo de texto que se muestra en este control de edición.|
|[CEdit::SetLimitText](#setlimittext)|Establece la cantidad máxima de texto esto `CEdit` puede contener.|
|[CEdit::SetMargins](#setmargins)|Establece los márgenes izquierdos y derecho para este `CEdit`.|
|[CEdit::SetModify](#setmodify)|Establece o borra la marca de modificación de un control de edición.|
|[CEdit::SetPasswordChar](#setpasswordchar)|Establece o quita un carácter de contraseña que se muestran en un control de edición cuando el usuario escribe texto.|
|[CEdit::SetReadOnly](#setreadonly)|Establece el estado de solo lectura de un control de edición.|
|[CEdit::SetRect](#setrect)|Establece el rectángulo de formato de un control de edición de varias líneas y actualiza el control.|
|[CEdit::SetRectNP](#setrectnp)|Establece el rectángulo de formato de un control de edición de varias líneas sin volver a dibujar la ventana de control.|
|[CEdit::SetSel](#setsel)|Selecciona un intervalo de caracteres en un control de edición.|
|[CEdit::SetTabStops](#settabstops)|Control de edición de conjuntos de las posiciones de tabulación en varias líneas.|
|[CEdit::ShowBalloonTip](#showballoontip)|Muestra un globo de sugerencias asociado al control de edición actual.|
|[CEdit::Undo](#undo)|Invierte la última operación de control de edición.|

## <a name="remarks"></a>Comentarios

Un control de edición es una ventana rectangular secundarios en el que el usuario puede escribir texto.

Puede crear un control de edición de una plantilla de cuadro de diálogo o directamente en el código. En ambos casos, primero llame al constructor `CEdit` para construir el `CEdit` objeto y, después, llame a la [crear](#create) función miembro para crear el Windows control de edición y adjuntarlo a la `CEdit` objeto.

Construcción puede ser un proceso de un paso en una clase derivada de `CEdit`. Escribir un constructor para la clase derivada y llame a `Create` desde dentro del constructor.

`CEdit` hereda la funcionalidad importante de `CWnd`. Para establecer y recuperar el texto de un `CEdit` de objeto, utilice el `CWnd` funciones miembro [SetWindowText](cwnd-class.md#setwindowtext) y [GetWindowText](cwnd-class.md#getwindowtext), qué set o get controlar todo el contenido de la edición, incluso si se es un control de varias líneas. Líneas de texto en un control de varias líneas se separan mediante secuencias de caracteres '\r\n'. Además, si un control de edición es multilínea, obtener y establecer una parte del texto del control mediante una llamada a la `CEdit` funciones miembro [GetLine](#getline), [función miembro SetSel](#setsel), [función miembro GetSel](#getsel)y [ ReplaceSel](#replacesel).

Si desea controlar los mensajes de notificación de Windows enviados por un control de edición a su elemento primario (normalmente una clase derivada de `CDialog`), agregue una función de miembro de entrada y el controlador de mensajes del mapa de mensajes a la clase primaria para cada mensaje.

Cada entrada de mapa de mensajes tiene el formato siguiente:

  **ON_**_NOTIFICATION_**(** _id_**,** _memberFxn_ **)**

donde `id` especifica el identificador de ventana secundaria de enviar la notificación, el control de edición y `memberFxn` es el nombre de la función de miembro primario que ha escrito para controlar la notificación.

Prototipo de función del elemento primario es el siguiente:

**afx_msg** void memberFxn **( );**

Siguiente es una lista de posibles entradas del mapa de mensajes y una descripción de los casos en que se enviarían al elemento primario:

- Asigna ON_EN_CHANGE el usuario ha realizado una acción que puede haber modificado el texto en un control de edición. A diferencia de los mensajes de notificación EN_UPDATE, este mensaje de notificación se envía después de que Windows actualice la pantalla.

- ON_EN_ERRSPACE el control de edición no se puede asignar memoria suficiente para satisfacer una solicitud específica.

- ON_EN_HSCROLL el usuario hace clic en la barra de desplazamiento horizontal de un control de edición. Se notifica a la ventana primaria antes de actualiza la pantalla.

- ON_EN_KILLFOCUS el control de edición pierde el foco de entrada.

- ON_EN_MAXTEXT la inserción actual ha superado el número especificado de caracteres para el control de edición y se ha truncado. También se envían cuando un control de edición no tiene el estilo ES_AUTOHSCROLL y el número de caracteres que se va a insertarse superaría el ancho del control de edición. También se envían cuando un control de edición no tiene el estilo ES_AUTOVSCROLL y el número total de líneas resultante de una inserción de texto, se superará el alto del control de edición.

- ON_EN_SETFOCUS se envía cuando un control de edición recibe el foco de entrada.

- ON_EN_UPDATE el control de edición es sobre texto para mostrar que se puede modificar. Enviar después de que el control ha dado formato al texto, pero antes de que filtra el texto para que se puede modificar el tamaño de ventana, si es necesario.

- ON_EN_VSCROLL el usuario hace clic en la barra de desplazamiento vertical de un control de edición. Se notifica a la ventana primaria antes de actualiza la pantalla.

Si creas un `CEdit` objeto dentro de un cuadro de diálogo, el `CEdit` objeto se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.

Si creas un `CEdit` objeto desde un recurso de cuadro de diálogo con el editor de cuadro de diálogo, el `CEdit` objeto se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.

Si creas un `CEdit` objeto dentro de una ventana, es posible que también deba destruirlo. Si crea la `CEdit` objeto en la pila, se destruye automáticamente. Si crea el `CEdit` objeto en el montón mediante el uso de la **nueva** función, debe llamar a **eliminar** control de edición en el objeto que lo destruirá cuando el usuario finaliza la Windows. Si asigna memoria en el `CEdit` objeto, invalide el `CEdit` destructor para deshacerse de las asignaciones.

Para modificar los estilos determinados en un control de edición (por ejemplo, ES_READONLY) debe enviar mensajes específicos para el control en lugar de usar [ModifyStyle](cwnd-class.md#modifystyle). Consulte [estilos de Control de edición](/windows/desktop/Controls/edit-control-styles) en el SDK de Windows.

Para obtener más información sobre `CEdit`, consulte [controles](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="canundo"></a>  CEdit::CanUndo

Llame a esta función para determinar si se puede deshacer la última operación de edición.

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si no se puede deshacer la última operación de edición mediante una llamada a la `Undo` función miembro; 0 si no se puede deshacer.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [EM_CANUNDO](/windows/desktop/Controls/em-canundo) en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::Undo](#undo).

##  <a name="cedit"></a>  CEdit::CEdit

Construye un objeto `CEdit`.

```
CEdit();
```

### <a name="remarks"></a>Comentarios

Use [crear](#create) para construir el Windows control de edición.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

##  <a name="charfrompos"></a>  CEdit::CharFromPos

Llame a esta función para recuperar la línea de base cero y los índices de carácter del carácter más cercano al punto especificado en este `CEdit` control

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>Parámetros

*pt*<br/>
Las coordenadas de un punto en el área cliente de este `CEdit` objeto.

### <a name="return-value"></a>Valor devuelto

El índice del carácter de la palabra de orden inferior y el índice de línea de la palabra de orden superior.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Esta función miembro está disponible desde Windows 95 y Windows NT 4.0.

Para obtener más información, consulte [EM_CHARFROMPOS](/windows/desktop/Controls/em-charfrompos) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

##  <a name="clear"></a>  CEdit::Clear

Llame a esta función para eliminar (borrar) la selección actual (si existe) en el control de edición.

```
void Clear();
```

### <a name="remarks"></a>Comentarios

La eliminación realizada por `Clear` se puede deshacer mediante una llamada a la [deshacer](#undo) función miembro.

Para eliminar la selección actual y colocar el contenido eliminado en el Portapapeles, llame a la [cortar](#cut) función miembro.

Para obtener más información, consulte [WM_CLEAR](/windows/desktop/dataxchg/wm-clear) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

##  <a name="copy"></a>  CEdit::Copy

Llame a esta función para copiar la selección actual (si existe) en el control de edición en el Portapapeles con formato CF_TEXT.

```
void Copy();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [WM_COPY](/windows/desktop/dataxchg/wm-copy) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

##  <a name="create"></a>  CEdit::Create

Crea el control de edición de Windows y lo adjunta a la `CEdit` objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de edición. Aplicar cualquier combinación de [Editar estilos](styles-used-by-mfc.md#edit-styles) al control.

*rect*<br/>
Especifica el tamaño y la posición del control de edición. Puede ser un `CRect` objeto o `RECT` estructura.

*pParentWnd*<br/>
Especifica la ventana primaria del control de edición (normalmente un `CDialog`). No debe ser NULL.

*nID*<br/>
Especifica el identificador. del control de edición

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización es correcta; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Construir un `CEdit` objeto en dos pasos. En primer lugar, llame a la `CEdit` constructor y a continuación, llame `Create`, que crea el control de edición de Windows y lo adjunta a la `CEdit` objeto.

Cuando `Create` envíos de Windows que se ejecuta el [WM_NCCREATE](/windows/desktop/winmsg/wm-nccreate), [WM_NCCALCSIZE](/windows/desktop/winmsg/wm-nccalcsize), [WM_CREATE](/windows/desktop/winmsg/wm-create), y [WM_GETMINMAXINFO](/windows/desktop/winmsg/wm-getminmaxinfo) mensajes para el control de edición.

Estos mensajes se controlan de manera predeterminada el [OnNcCreate](cwnd-class.md#onnccreate), [OnNcCalcSize](cwnd-class.md#onnccalcsize), [OnCreate](cwnd-class.md#oncreate), y [OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo) funciones miembro en el `CWnd` clase base. Para extender el control de mensajes de forma predeterminada, derive una clase de `CEdit`, agregue un mapa de mensajes a la nueva clase y reemplazar las funciones de miembro anterior controlador de mensajes. Invalidar `OnCreate`, por ejemplo, para realizar la inicialización necesaria para la nueva clase.

Aplique el siguiente [estilos de ventana](styles-used-by-mfc.md#window-styles) a un control de edición.

- WS_CHILD siempre

- WS_VISIBLE normalmente

- WS_DISABLED rara vez

- WS_GROUP a controles de grupo

- WS_TABSTOP para incluir el control de edición en el orden de tabulación

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

##  <a name="cut"></a>  CEdit::Cut

Llame a esta función para eliminar (Cortar) la selección actual (si existe) en el control de edición y copie el texto eliminado en el Portapapeles con formato CF_TEXT.

```
void Cut();
```

### <a name="remarks"></a>Comentarios

La eliminación realizada por `Cut` se puede deshacer mediante una llamada a la [deshacer](#undo) función miembro.

Para eliminar la selección actual sin colocar el texto eliminado en el Portapapeles, llame a la [clara](#clear) función miembro.

Para obtener más información, consulte [WM_CUT](/windows/desktop/dataxchg/wm-cut) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

##  <a name="emptyundobuffer"></a>  CEdit::EmptyUndoBuffer

Llame a esta función para restablecer (borrar) el indicador de deshacer de un control de edición.

```
void EmptyUndoBuffer();
```

### <a name="remarks"></a>Comentarios

El control de edición ahora podrá deshacer la última operación. Se establece la marca de deshacer cada vez que se puede deshacer una operación en el control de edición.

La marca de deshacer es automáticamente cada vez que borra la [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) o [SetHandle](#sethandle) `CWnd` se llama a funciones miembro.

Para obtener más información, consulte [EM_EMPTYUNDOBUFFER](/windows/desktop/Controls/em-emptyundobuffer) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

##  <a name="fmtlines"></a>  CEdit::FmtLines

Llame a esta función para establecer la inclusión de caracteres de salto de línea automático en on u off dentro de un control de edición de varias líneas.

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>Parámetros

*bAddEOL*<br/>
Especifica si los caracteres de salto de línea automático se va a insertar. Un valor TRUE inserta los caracteres; Quita un valor FALSE.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si cualquier formato que se produzca; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Un salto de línea temporal está formado por dos retornos de carro o avance de línea insertado al final de una línea que se ha interrumpido debido a ajuste de líneas. Un salto de línea de duro está formado por un retorno de carro o avance de línea. Las líneas que terminan con un salto de línea de duro no se ven afectadas por `FmtLines`.

Windows responderá sólo si el `CEdit` objeto es un control de edición de varias líneas.

`FmtLines` solo afecta al búfer devuelto por [GetHandle](#gethandle) y el texto devuelto por [WM_GETTEXT](/windows/desktop/winmsg/wm-gettext). No tiene ningún impacto en la presentación del texto dentro del control de edición.

Para obtener más información, consulte [EM_FMTLINES](/windows/desktop/Controls/em-fmtlines) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

##  <a name="getcuebanner"></a>  CEdit::GetCueBanner

Recupera el texto que se muestra como la pila de texto, o sugerencia, en un control de edición cuando el control está vacío.

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
[out] Un puntero a una cadena que contiene el texto de indicación.

*cchText*<br/>
[in] El número de caracteres que se pueden recibir. Este número incluye el carácter nulo de terminación.

### <a name="return-value"></a>Valor devuelto

Para la primera sobrecarga, TRUE si el método se realiza correctamente; en caso contrario, FALSE.

Para la segunda sobrecarga, una [CString](../../atl-mfc-shared/using-cstring.md) que contiene el texto de indicación de si el método es correcto; en caso contrario, una cadena vacía ("").

### <a name="remarks"></a>Comentarios

Este método envía el [EM_GETCUEBANNER](/windows/desktop/Controls/em-getcuebanner) mensaje, que se describe en el SDK de Windows. Para obtener más información, consulte el [Edit_GetCueBannerText](/windows/desktop/api/commctrl/nf-commctrl-edit_getcuebannertext) macro.

##  <a name="getfirstvisibleline"></a>  CEdit::GetFirstVisibleLine

Llame a esta función para determinar la línea superior visible en un control de edición.

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la línea visible superior. Para los controles de edición de línea única, el valor devuelto es 0.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [EM_GETFIRSTVISIBLELINE](/windows/desktop/Controls/em-getfirstvisibleline) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

##  <a name="gethandle"></a>  CEdit::GetHandle

Llame a esta función para recuperar un identificador de la memoria asignada actualmente a un control de edición de varias líneas.

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>Valor devuelto

Un identificador de memoria local que identifica el búfer que contiene el contenido del control de edición. Si se produce un error, como enviar el mensaje a un control de edición de línea única, el valor devuelto es 0.

### <a name="remarks"></a>Comentarios

El identificador es un identificador de memoria local y pueden usarse en cualquiera de los **Local** las funciones de memoria de Windows que toman una memoria local se tratan como un parámetro.

`GetHandle` se procesa solo por los controles de edición de varias líneas.

Llame a `GetHandle` para un control de edición de varias líneas en un cuadro de diálogo solo si el cuadro de diálogo se creó con el marcador de estilo DS_LOCALEDIT establecido. Si no se establece el estilo DS_LOCALEDIT, seguirá teniendo el valor devuelto distinto de cero, pero no podrá usar el valor devuelto.

> [!NOTE]
> `GetHandle` no funcionará con Windows 95 ó 98. Si se llama a `GetHandle` en Windows 95/98, devolverá NULL. `GetHandle` funcionará como se documenta en Windows NT versión 3.51 y versiones posteriores.

Para obtener más información, consulte [EM_GETHANDLE](/windows/desktop/Controls/em-gethandle) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

##  <a name="gethighlight"></a>  CEdit::GetHighlight

Obtiene los índices de los caracteres primeros y últimos en un intervalo de texto que está resaltado en el control de edición actual.

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pichStart*|[out] Índice de base cero del primer carácter del intervalo de texto que aparece resaltado.|
|*pichEnd*|[out] Índice de base cero del último carácter del intervalo de texto que aparece resaltado.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el [EM_GETHILITE](/windows/desktop/Controls/em-gethilite) mensaje, que se describe en el SDK de Windows. Ambos `SetHighlight` y `GetHighlight` están habilitadas actualmente para compilaciones de UNICODE solo.

##  <a name="getlimittext"></a>  CEdit::GetLimitText

Llame a esta función miembro para obtener el límite de texto para este `CEdit` objeto.

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>Valor devuelto

El límite texto actual, en TCHARs, para este `CEdit` objeto.

### <a name="remarks"></a>Comentarios

El límite de texto es la cantidad máxima de texto, en TCHARs, que puede aceptar el control de edición.

> [!NOTE]
>  Esta función miembro está disponible desde Windows 95 y Windows NT 4.0.

Para obtener más información, consulte [EM_GETLIMITTEXT](/windows/desktop/Controls/em-getlimittext) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

##  <a name="getline"></a>  CEdit::GetLine

Llame a esta función para recuperar una línea de texto de un control de edición y lo coloca en *lpszBuffer*.

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
Especifica el número de línea para recuperar de varias líneas de control de edición. Números de línea son de base cero; un valor de 0 especifica la primera línea. Este parámetro se omite por un control de edición de línea única.

*lpszBuffer*<br/>
Apunta al búfer que recibe una copia de la línea. La primera palabra del búfer debe especificar el número máximo de TCHARs que se pueden copiar en el búfer.

*nMaxLength*<br/>
Especifica el número máximo de caracteres TCHAR que se pueden copiar en el búfer. `GetLine` coloca este valor en la primera palabra de *lpszBuffer* antes de realizar la llamada a Windows.

### <a name="return-value"></a>Valor devuelto

Número de caracteres que realmente se va a copiar. El valor devuelto es 0 si el número de línea especificado por *nIndex* es mayor que el número de líneas en el control de edición.

### <a name="remarks"></a>Comentarios

La línea copiada no contiene un carácter de terminación null.

Para obtener más información, consulte [EM_GETLINE](/windows/desktop/Controls/em-getline) en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::GetLineCount](#getlinecount).

##  <a name="getlinecount"></a>  CEdit::GetLineCount

Llame a esta función para recuperar el número de líneas en un control de edición de varias líneas.

```
int GetLineCount() const;
```

### <a name="return-value"></a>Valor devuelto

Control de edición de un entero que contiene el número de líneas en varias líneas. Si no se ha especificado ningún texto en el control de edición, el valor devuelto es 1.

### <a name="remarks"></a>Comentarios

`GetLineCount` solo se procesa por los controles de edición de varias líneas.

Para obtener más información, consulte [EM_GETLINECOUNT](/windows/desktop/Controls/em-getlinecount) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

##  <a name="getmargins"></a>  CEdit::GetMargins

Llame a esta función miembro para recuperar los márgenes izquierdos y derecho de este control de edición.

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>Valor devuelto

El ancho del margen izquierdo en la palabra de orden inferior y el ancho del margen derecho de la palabra de orden superior.

### <a name="remarks"></a>Comentarios

Los márgenes se miden en píxeles.

> [!NOTE]
>  Esta función miembro está disponible desde Windows 95 y Windows NT 4.0.

Para obtener más información, consulte [EM_GETMARGINS](/windows/desktop/Controls/em-getmargins) en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

##  <a name="getmodify"></a>  CEdit::GetModify

Llame a esta función para determinar si se ha modificado el contenido de un control de edición.

```
BOOL GetModify() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha modificado el contenido de control de edición; 0 si permanecen sin cambios.

### <a name="remarks"></a>Comentarios

Windows mantiene un marcador interno que indica si el contenido del control de edición ha cambiado. Esta marca se borra cuando el control de edición se crea por primera vez y es posible que también se puede borrar mediante una llamada a la [SetModify](#setmodify) función miembro.

Para obtener más información, consulte [EM_GETMODIFY](/windows/desktop/Controls/em-getmodify) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

##  <a name="getpasswordchar"></a>  CEdit::GetPasswordChar

Llame a esta función para recuperar el carácter de contraseña que se muestra en un control de edición cuando el usuario escribe texto.

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>Valor devuelto

Especifica el carácter que se mostrará en lugar del carácter escrito por el usuario. El valor devuelto es NULL si no existe ningún carácter de contraseña.

### <a name="remarks"></a>Comentarios

Si crea el control de edición con el estilo ES_PASSWORD, el archivo DLL que admite el control determina el carácter de contraseña predeterminado. El manifiesto o la [InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex) método determina cuáles DLL es compatible con el control de edición. Si el archivo user32.dll es compatible con el control de edición, el carácter de contraseña predeterminada es asterisco ('* ', 002A U +). Si comctl32.dll versión 6 es compatible con el control de edición, el carácter predeterminado es negro círculo ('●', 25CF U +). Para obtener más información acerca de qué archivo DLL y versión admite los controles comunes, vea [Shell y las versiones de los controles comunes](https://msdn.microsoft.com/library/windows/desktop/bb776779).

Este método envía el [EM_GETPASSWORDCHAR](/windows/desktop/Controls/em-getpasswordchar) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

##  <a name="getrect"></a>  CEdit::GetRect

Llame a esta función para obtener el rectángulo de formato de un control de edición.

```
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a la `RECT` estructura que recibe el rectángulo de formato.

### <a name="remarks"></a>Comentarios

El rectángulo de formato es el rectángulo limitador del texto, que es independiente del tamaño de la ventana de control de edición.

El rectángulo de formato de un control de edición de varias líneas se puede modificar mediante la [SetRect](#setrect) y [SetRectNP](#setrectnp) funciones miembro.

Para obtener más información, consulte [EM_GETRECT](/windows/desktop/Controls/em-getrect) en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::LimitText](#limittext).

##  <a name="getsel"></a>  CEdit::GetSel

Llame a esta función para obtener iniciales y finales de posiciones de caracteres de la selección actual (si existe) en un control de edición, con el valor devuelto o los parámetros.

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
Referencia a un entero que recibirá la posición del primer carácter más allá del final de la selección actual.

### <a name="return-value"></a>Valor devuelto

La versión que devuelve un valor DWORD devuelve un valor que contiene la posición inicial de la palabra de orden inferior y la posición del primer carácter después del final de la selección de la palabra de orden superior.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [EM_GETSEL](/windows/desktop/Controls/em-getsel) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

##  <a name="hideballoontip"></a>  CEdit::HideBalloonTip

Oculta un globo de sugerencias asociado al control de edición actual.

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Esta función envía el [EM_HIDEBALLOONTIP](/windows/desktop/Controls/em-hideballoontip) mensaje, que se describe en el SDK de Windows.

##  <a name="limittext"></a>  CEdit::LimitText

Llame a esta función para limitar la longitud del texto que el usuario puede escribir en un control de edición.

```
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>Parámetros

*nChars*<br/>
Especifica la longitud (en TCHARs) del texto que el usuario puede escribir. Si este parámetro es 0, se establece la longitud del texto en bytes UINT_MAX. Éste es el comportamiento predeterminado.

### <a name="remarks"></a>Comentarios

Cambiar el límite de texto, restringe únicamente el texto que el usuario puede escribir. No tiene ningún efecto en ningún texto ya en el control de edición, ni afecta a la longitud del texto copiado en el control de edición mediante la [SetWindowText](cwnd-class.md#setwindowtext) función miembro en `CWnd`. Si una aplicación utiliza el `SetWindowText` función colocar más texto en un control de edición que se especifica en la llamada a `LimitText`, el usuario puede eliminar el texto dentro del control de edición. Sin embargo, el límite de texto impedirá que el usuario reemplazando el texto existente por texto nuevo, a menos que la eliminación de la actual selección hace que el texto quede por debajo del límite de texto.

> [!NOTE]
>  En Win32 (Windows NT y Windows 95/98), [SetLimitText](#setlimittext) reemplaza esta función.

Para obtener más información, consulte [EM_LIMITTEXT](/windows/desktop/Controls/em-limittext) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

##  <a name="linefromchar"></a>  CEdit::LineFromChar

Llame a esta función para recuperar el número de línea de la línea que contiene el índice de carácter especificado.

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Contiene el valor de índice de base cero del carácter deseado en el texto del control de edición, o -1. Si *nIndex* es -1, especifica la línea actual, es decir, la línea que contiene el símbolo de intercalación.

### <a name="return-value"></a>Valor devuelto

El número de línea de base cero de la línea que contiene el índice de carácter especificado por *nIndex*. Si *nIndex* es -1, se devuelve el número de la línea que contiene el primer carácter de la selección. Si no hay ninguna selección, se devuelve el número de línea actual.

### <a name="remarks"></a>Comentarios

Un índice de carácter es el número de caracteres desde el principio del control de edición.

Esta función miembro se usa solamente controles de edición de varias líneas.

Para obtener más información, consulte [EM_LINEFROMCHAR](/windows/desktop/Controls/em-linefromchar) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

##  <a name="lineindex"></a>  CEdit::LineIndex

Llame a esta función para recuperar el índice de carácter de una línea dentro de un control de edición de varias líneas.

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>Parámetros

*nLine*<br/>
Contiene el valor de índice de la línea deseada en el texto del control de edición, o -1. Si *nLínea* es -1, especifica la línea actual, es decir, la línea que contiene el símbolo de intercalación.

### <a name="return-value"></a>Valor devuelto

El índice de carácter de la línea especificada en *nLínea* o -1 si el número de línea especificado es mayor que el número de líneas en el control de edición.

### <a name="remarks"></a>Comentarios

El índice de carácter es el número de caracteres desde el principio del control de edición a la línea especificada.

Esta función miembro solo se procesa por los controles de edición de varias líneas.

Para obtener más información, consulte [EM_LINEINDEX](https://msdn.microsoft.com/library/windows/desktop/bb761611) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

##  <a name="linelength"></a>  CEdit::LineLength

Recupera la longitud de una línea en un control de edición.

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>Parámetros

*nLine*<br/>
Índice de base cero de un carácter en la línea cuya longitud se va a recuperar. El valor predeterminado es -1.

### <a name="return-value"></a>Valor devuelto

Para los controles de edición de línea única, el valor devuelto es la longitud, en TCHARs, del texto del control de edición.

Para los controles de edición multilínea, el valor devuelto es la longitud, en TCHARs, de la línea especificada por el *nLínea* parámetro. Texto ANSI, la longitud es el número de bytes en la línea; texto Unicode, la longitud es el número de caracteres de la línea. La longitud no incluye el carácter de retorno de carro al final de la línea.

Si el *nLínea* parámetro es mayor que el número de caracteres en el control, el valor devuelto es cero.

Si el *nLínea* parámetro es -1, el valor devuelto es el número de caracteres no seleccionadas de las líneas que contienen los caracteres seleccionados. Por ejemplo, si la selección se extiende desde el cuarto carácter de una línea a través de los caracteres octavo desde el final de la línea siguiente, el valor devuelto es 10. Es decir, tres caracteres en la primera línea y siete en la siguiente.

Para obtener más información sobre el tipo TCHAR, consulte la fila TCHAR en la tabla de [tipos de datos de Windows](/windows/desktop/WinProg/windows-data-types).

### <a name="remarks"></a>Comentarios

Este método es compatible con la [EM_LINELENGTH](/windows/desktop/Controls/em-linelength) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::LineIndex](#lineindex).

##  <a name="linescroll"></a>  CEdit::LineScroll

Llame a esta función para desplazarse por el texto de un control de edición de varias líneas.

```
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>Parámetros

*nLines*<br/>
Especifica el número de líneas de desplazamiento vertical.

*nChars*<br/>
Especifica el número de posiciones de caracteres a desplazarse horizontalmente. Este valor se omite si el control de edición tiene estilo ES_RIGHT o ES_CENTER.

### <a name="remarks"></a>Comentarios

Esta función miembro se procesa solo por los controles de edición de varias líneas.

El control de edición se desplaza verticalmente más allá de la última línea del texto del control de edición. Si la línea actual más el número de líneas especificado por *nLines* supera el número total de líneas en el control de edición, el valor se ajusta para que la última línea del control de edición se desplaza a la parte superior de la ventana de control de edición.

`LineScroll` puede utilizarse para desplazarse horizontalmente más allá del último carácter de cualquier línea.

Para obtener más información, consulte [EM_LINESCROLL](/windows/desktop/Controls/em-linescroll) en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::GetFirstVisibleLine](#getfirstvisibleline).

##  <a name="paste"></a>  CEdit::Paste

Llame a esta función para insertar los datos desde el Portapapeles en el `CEdit` en el punto de inserción.

```
void Paste();
```

### <a name="remarks"></a>Comentarios

Datos se insertan solo si el Portapapeles contiene datos con formato CF_TEXT.

Para obtener más información, consulte [WM_PASTE](/windows/desktop/dataxchg/wm-paste) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

##  <a name="posfromchar"></a>  CEdit::PosFromChar

Llame a esta función para obtener la posición (esquina superior izquierda) de un determinado carácter dentro de este `CEdit` objeto.

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>Parámetros

*nChar*<br/>
Índice de base cero del carácter especificado.

### <a name="return-value"></a>Valor devuelto

Las coordenadas de la esquina superior izquierda del carácter especificado por *nChar*.

### <a name="remarks"></a>Comentarios

El carácter especificado por lo que ofrece su valor de índice de base cero. Si *nChar* es mayor que el índice del último carácter en esta `CEdit` objeto, el valor devuelto especifica las coordenadas de la posición del carácter inmediatamente después del último carácter en esta `CEdit` objeto.

> [!NOTE]
>  Esta función miembro está disponible desde Windows 95 y Windows NT 4.0.

Para obtener más información, consulte [EM_POSFROMCHAR](/windows/desktop/Controls/em-posfromchar) en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::LineFromChar](#linefromchar).

##  <a name="replacesel"></a>  CEdit::ReplaceSel

Llame a esta función para reemplazar la selección actual en un control de edición con el texto especificado por *lpszNewText*.

```
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>Parámetros

*lpszNewText*<br/>
Apunta a una cadena terminada en null que contiene el texto de reemplazo.

*bCanUndo*<br/>
Para especificar que se puede deshacer esta función, establezca el valor de este parámetro en TRUE. El valor predeterminado es FALSE.

### <a name="remarks"></a>Comentarios

Reemplaza solo una parte del texto en un control de edición. Si desea reemplazar todo el texto, use la [CWnd::SetWindowText](cwnd-class.md#setwindowtext) función miembro.

Si no hay ninguna selección actual, se inserta el texto de reemplazo en la ubicación actual del cursor.

Para obtener más información, consulte [EM_REPLACESEL](/windows/desktop/Controls/em-replacesel) en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::LineIndex](#lineindex).

##  <a name="setcuebanner"></a>  CEdit::SetCueBanner

Establece el texto que se muestra como la pila de texto, o sugerencia, en una edición de control cuando el control está vacío.

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
[in] Puntero a una cadena que contiene la pila para mostrar en el control de edición.

*fDrawWhenFocused*<br/>
[in] Si es FALSE, no se dibuja el titular de indicación cuando el usuario hace clic en el control de edición y proporciona el control el foco.

Si es TRUE, se dibuja el titular de indicación, incluso cuando el control tiene el foco. El titular de indicación desaparece cuando el usuario comienza a escribir en el control.

El valor predeterminado es FALSE.

### <a name="return-value"></a>Valor devuelto

TRUE si el método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el [EM_SETCUEBANNER](/windows/desktop/Controls/em-setcuebanner) mensaje, que se describe en el SDK de Windows. Para obtener más información, consulte el [Edit_SetCueBannerTextFocused](/windows/desktop/api/commctrl/nf-commctrl-edit_setcuebannertextfocused) macro.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el [CEdit::SetCueBanner](#setcuebanner) método.

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

##  <a name="sethandle"></a>  CEdit::SetHandle

Llame a esta función para establecer el identificador de la memoria local que se usará en un control de edición de varias líneas.

```
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>Parámetros

*hBuffer*<br/>
Contiene un identificador de la memoria local. Este identificador se debe haber creado mediante una llamada anterior a la [LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc) función de Windows mediante la marca LMEM_MOVEABLE. Se supone que la memoria contienen una cadena terminada en null. Si esto no es el caso, el primer byte de la memoria asignada debe establecerse en 0.

### <a name="remarks"></a>Comentarios

El control de edición, a continuación, usará este búfer para almacenar el texto mostrado actualmente en lugar de asignar su propio búfer.

Esta función miembro se procesa solo por los controles de edición de varias líneas.

Antes de que una aplicación establece un nuevo identificador de memoria, debe usar el [GetHandle](#gethandle) función miembro para obtener el identificador para el búfer de memoria actual y liberar esa memoria con el `LocalFree` función de Windows.

`SetHandle` Borra el búfer de deshacer (el [CanUndo](#canundo) función miembro, a continuación, devuelve 0) y la marca de modificación interna (la [GetModify](#getmodify) función miembro, a continuación, devuelve 0). Se vuelve a dibujar la ventana de control de edición.

Puede usar esta función miembro en un control de edición de varias líneas en un cuadro de diálogo solo si ha creado el cuadro de diálogo con el marcador de estilo DS_LOCALEDIT establecido.

> [!NOTE]
> `GetHandle` no funcionará con Windows 95 ó 98. Si se llama a `GetHandle` en Windows 95/98, devolverá NULL. `GetHandle` funcionará como se documenta en Windows NT versión 3.51 y versiones posteriores.

Para obtener más información, consulte [EM_SETHANDLE](/windows/desktop/Controls/em-sethandle), [LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc), y [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

##  <a name="sethighlight"></a>  CEdit::SetHighlight

Información destacada de un intervalo de texto que se muestra en este control de edición.

```
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*ichStart*|[in] Índice de base cero del primer carácter del intervalo de texto que se va a resaltar.|
|*ichEnd*|[in] Índice de base cero del último carácter del intervalo de texto que se va a resaltar.|

### <a name="remarks"></a>Comentarios

Este método envía el [EM_SETHILITE](/windows/desktop/Controls/em-sethilite) mensaje, que se describe en el SDK de Windows.  Este método envía el [EM_SETHILITE](/windows/desktop/Controls/em-sethilite) mensaje, que se describe en el SDK de Windows. Ambos `SetHighlight` y `GetHighlight` están habilitadas para UNICODE solo se basa.

##  <a name="setlimittext"></a>  CEdit::SetLimitText

Llame a esta función miembro para establecer el límite de texto para este `CEdit` objeto.

```
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>Parámetros

*nMax*<br/>
El nuevo límite de texto, en caracteres.

### <a name="remarks"></a>Comentarios

El límite de texto es la cantidad máxima de texto, en caracteres, que puede aceptar el control de edición.

Cambiar el límite de texto, restringe únicamente el texto que el usuario puede escribir. No tiene ningún efecto en ningún texto ya en el control de edición, ni afecta a la longitud del texto copiado en el control de edición mediante la [SetWindowText](cwnd-class.md#setwindowtext) función miembro en `CWnd`. Si una aplicación utiliza el `SetWindowText` función colocar más texto en un control de edición que se especifica en la llamada a `LimitText`, el usuario puede eliminar el texto dentro del control de edición. Sin embargo, el límite de texto impedirá que el usuario reemplazando el texto existente por texto nuevo, a menos que la eliminación de la actual selección hace que el texto quede por debajo del límite de texto.

Esta función reemplaza [LimitText](#limittext) en Win32.

Para obtener más información, consulte [EM_SETLIMITTEXT](/windows/desktop/Controls/em-setlimittext) en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

##  <a name="setmargins"></a>  CEdit::SetMargins

Llame a este método para establecer los márgenes izquierdos y derecho de este control de edición.

```
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>Parámetros

*nLeft*<br/>
El ancho del margen izquierdo nuevo, en píxeles.

*nRight*<br/>
El ancho del margen derecho nuevo, en píxeles.

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  Esta función miembro está disponible desde Windows 95 y Windows NT 4.0.

Para obtener más información, consulte [EM_SETMARGINS](/windows/desktop/Controls/em-setmargins) en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEditView::GetEditCtrl](ceditview-class.md#geteditctrl).

##  <a name="setmodify"></a>  CEdit::SetModify

Llame a esta función para establecer o borrar la marca modificada para un control de edición.

```
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parámetros

*bModified*<br/>
Un valor TRUE indica que se ha modificado el texto y un valor de FALSE indica que no se modifica. De forma predeterminada, se establece la marca modificada.

### <a name="remarks"></a>Comentarios

La marca modificada indica si se ha modificado el texto dentro del control de edición. Se establece automáticamente cuando el usuario cambia el texto. Su valor se puede recuperar con el [GetModify](#getmodify) función miembro.

Para obtener más información, consulte [EM_SETMODIFY](/windows/desktop/Controls/em-setmodify) en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::GetModify](#getmodify).

##  <a name="setpasswordchar"></a>  CEdit::SetPasswordChar

Llame a esta función para establecer o quitar un carácter de contraseña que se muestran en un control de edición cuando el usuario escribe texto.

```
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>Parámetros

*ch*<br/>
Especifica el carácter que se mostrará en lugar del carácter escrito por el usuario. Si *ch* es 0, se muestran los caracteres reales escritos por el usuario.

### <a name="remarks"></a>Comentarios

Cuando se establece un carácter de contraseña, ese carácter se muestra para cada carácter de los tipos de usuario.

Esta función miembro no tiene ningún efecto en varias líneas de control de edición.

Cuando el `SetPasswordChar` se llama a la función miembro, `CEdit` volverá a dibujar todos los caracteres visibles mediante el carácter especificado por *ch*.

Si el control de edición se crea con el [ES_PASSWORD](styles-used-by-mfc.md#edit-styles) estilo, el carácter de contraseña predeterminado se establece en un asterisco ( <strong>\*</strong>). Este estilo se quitará si `SetPasswordChar` se llama con *ch* establecido en 0.

Para obtener más información, consulte [EM_SETPASSWORDCHAR](/windows/desktop/Controls/em-setpasswordchar) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

##  <a name="setreadonly"></a>  CEdit::SetReadOnly

Llama a esta función para establecer el estado de solo lectura de un control de edición.

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>Parámetros

*bReadOnly*<br/>
Especifica si se debe establecer o quitar el estado de solo lectura del control de edición. Un valor TRUE, Establece el estado de sólo lectura; un valor FALSE, Establece el estado a lectura/escritura.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación es correcta, o 0 si un error se produce.

### <a name="remarks"></a>Comentarios

Encontrará la configuración actual mediante la comprobación de la [ES_READONLY](styles-used-by-mfc.md#edit-styles) marca en el valor devuelto de [CWnd::GetStyle](cwnd-class.md#getstyle).

Para obtener más información, consulte [EM_SETREADONLY](/windows/desktop/Controls/em-setreadonly) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

##  <a name="setrect"></a>  CEdit::SetRect

Llame a esta función para establecer las dimensiones de un rectángulo mediante las coordenadas especificadas.

```
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a la `RECT` estructura o `CRect` objeto que especifica las nuevas dimensiones del rectángulo de formato.

### <a name="remarks"></a>Comentarios

Este miembro se procesa solo por los controles de edición de varias líneas.

Use `SetRect` para establecer el formato de control de edición rectángulo de varias líneas. El rectángulo de formato es el rectángulo limitador del texto, que es independiente del tamaño de la ventana de control de edición. Cuando se crea el control de edición, el rectángulo de formato es el mismo que el área cliente de la ventana de control de edición. Mediante el uso de la `SetRect` función miembro, una aplicación puede realizar el rectángulo de formato mayor o menor que la ventana de control de edición.

Si el control de edición no tiene ninguna barra de desplazamiento, texto se recortará, no está ajustada, si el rectángulo de formato se realiza la mayor que la ventana. Si el control de edición contiene un borde, el rectángulo de formato se reduce el tamaño del borde. Si ajusta el rectángulo devuelto por la `GetRect` función miembro, debe quitar el tamaño del borde antes de pasar el rectángulo a `SetRect`.

Cuando `SetRect` se llama, el control de edición del texto también ha cambiado y se vuelve a mostrar.

Para obtener más información, consulte [EM_SETRECT](/windows/desktop/Controls/em-setrect) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

##  <a name="setrectnp"></a>  CEdit::SetRectNP

Llame a esta función para establecer el rectángulo de formato de un control de edición de varias líneas.

```
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a un `RECT` estructura o `CRect` objeto que especifica las nuevas dimensiones del rectángulo.

### <a name="remarks"></a>Comentarios

El rectángulo de formato es el rectángulo limitador del texto, que es independiente del tamaño de la ventana de control de edición.

`SetRectNP` es idéntica a la `SetRect` función miembro, salvo que la ventana de control de edición no se vuelve a dibujar.

Cuando se crea el control de edición, el rectángulo de formato es el mismo que el área cliente de la ventana de control de edición. Mediante una llamada a la `SetRectNP` función miembro, una aplicación puede realizar el rectángulo de formato mayor o menor que la ventana de control de edición.

Si el control de edición no tiene ninguna barra de desplazamiento, texto se recortará, no está ajustada, si el rectángulo de formato se realiza la mayor que la ventana.

Este miembro se procesa solo por los controles de edición de varias líneas.

Para obtener más información, consulte [EM_SETRECTNP](/windows/desktop/Controls/em-setrectnp) en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::SetRect](#setrect).

##  <a name="setsel"></a>  CEdit::SetSel

Llame a esta función para seleccionar un intervalo de caracteres en un control de edición.

```
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
Especifica la posición inicial de la palabra de orden inferior y la posición final de la palabra de orden superior. Si la palabra de orden inferior es 0 y la palabra de orden superior es -1, se selecciona todo el texto del control de edición. Si la palabra de orden inferior es -1, se quita cualquier selección actual.

*bNoScroll*<br/>
Indica si se debe desplazar el símbolo de intercalación en la vista. Si es FALSE, se desplaza el símbolo de intercalación en la vista. Si es TRUE, el símbolo de intercalación no se desplaza en la vista.

*nStartChar*<br/>
Especifica la posición inicial. Si *nStartChar* es 0 y *nEndChar* es -1, todo el texto del control de edición está seleccionado. Si *nStartChar* es -1, se quita cualquier selección actual.

*nEndChar*<br/>
Especifica la posición final.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [EM_SETSEL](/windows/desktop/Controls/em-setsel) en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEdit::GetSel](#getsel).

##  <a name="settabstops"></a>  CEdit::SetTabStops

Llame a esta función para establecer las tabulaciones en un control de edición de varias líneas.

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parámetros

*cxEachStop*<br/>
Especifica que se puede establecer en posiciones de tabulación cada *cxEachStop* unidades de cuadro de diálogo.

*nTabStops*<br/>
Especifica el número de posiciones de tabulación contenidos en *rgTabStops*. Este número debe ser mayor que 1.

*rgTabStops*<br/>
Apunta a una matriz de enteros sin signo que especifica la pestaña se detiene en unidades de cuadro de diálogo. Una unidad de cuadro de diálogo es una distancia horizontal o vertical. Una unidad de cuadro de diálogo horizontal es igual a una cuarta parte de la unidad de base de ancho del cuadro de diálogo actual y 1 unidad de cuadro de diálogo vertical es igual a una octava parte de la unidad de alto de la base del cuadro de diálogo actual. Las unidades base del cuadro de diálogo se calculan en función del alto y ancho de la fuente del sistema actual. El `GetDialogBaseUnits` función Windows devuelve el cuadro de diálogo actual unidades base en píxeles.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se establecieron las pestañas; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Cuando se copia texto en un control de edición de varias líneas, cualquier carácter de tabulación en el texto hará que el espacio que se genere hasta la siguiente posición de tabulación.

Para establecer posiciones de tabulación en el tamaño predeterminado de 32 unidades de cuadro de diálogo, llame a la versión de esta función miembro sin parámetros. Para establecer posiciones de tabulación en un tamaño distinto de 32, llame a la versión con el *cxEachStop* parámetro. Para establecer posiciones de tabulación en una matriz de tamaños, utilice la versión con dos parámetros.

Esta función miembro solo se procesa por los controles de edición de varias líneas.

`SetTabStops` no automáticamente volver a dibujar la ventana de edición. Si cambia las tabulaciones de texto ya está en el control de edición, llame a [CWnd::InvalidateRect](cwnd-class.md#invalidaterect) para volver a dibujar la ventana de edición.

Para obtener más información, consulte [EM_SETTABSTOPS](/windows/desktop/Controls/em-settabstops) y [GetDialogBaseUnits](/windows/desktop/api/winuser/nf-winuser-getdialogbaseunits) en el SDK de Windows.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEditView::SetTabStops](ceditview-class.md#settabstops).

##  <a name="showballoontip"></a>  CEdit::ShowBalloonTip

Muestra un globo de sugerencias asociado al control de edición actual.

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
|*pEditBalloonTip*|[in] Puntero a un [EDITBALLOONTIP](/windows/desktop/api/commctrl/ns-commctrl-_tageditballoontip) estructura que describe el globo de sugerencias.|
|*lpszTitle*|[in] Puntero a una cadena Unicode que contiene el título del globo de sugerencias.|
|*lpszText*|[in] Puntero a una cadena Unicode que contiene el texto de sugerencia de globo.|
|*ttiIcon*|[in] Un **INT** que especifica el tipo de icono que se va a asociar con el globo de sugerencias. El valor predeterminado es TTI_NONE. Para obtener más información, consulte el `ttiIcon` miembro de la [EDITBALLOONTIP](/windows/desktop/api/commctrl/ns-commctrl-_tageditballoontip) estructura.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Esta función envía el [EM_SHOWBALLOONTIP](/windows/desktop/Controls/em-showballoontip) mensaje, que se describe en el SDK de Windows. Para obtener más información, consulte el [Edit_ShowBalloonTip](/windows/desktop/api/commctrl/nf-commctrl-edit_showballoontip) macro.

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente define una variable, `m_cedit`, que se usa para tener acceso al control de edición actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra un globo de sugerencias para un control de edición. El [CEdit::ShowBalloonTip](#showballoontip) método especifica un título y el globo de texto de sugerencia.

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

##  <a name="undo"></a>  CEdit::Undo

Llame a esta función para deshacer la última operación de control de edición.

```
BOOL Undo();
```

### <a name="return-value"></a>Valor devuelto

Para un control de edición de línea única, el valor devuelto siempre es distinto de cero. Para un control de edición de varias líneas, el valor devuelto es distinto de cero si la operación de deshacer se realiza correctamente, o 0 si se produce un error en la operación de deshacer.

### <a name="remarks"></a>Comentarios

También se puede deshacer una operación de deshacer. Por ejemplo, puede restaurar el texto eliminado con la primera llamada a `Undo`. Siempre y cuando no hay ninguna operación de edición que intervengan, puede quitar el texto nuevo con una segunda llamada a `Undo`.

Para obtener más información, consulte [EM_UNDO](/windows/desktop/Controls/em-undo) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo de MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[MFC Sample CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](cwnd-class.md)<br/>
[CButton (clase)](cbutton-class.md)<br/>
[CComboBox (clase)](ccombobox-class.md)<br/>
[CListBox (clase)](clistbox-class.md)<br/>
[CScrollBar (clase)](cscrollbar-class.md)<br/>
[CStatic (clase)](cstatic-class.md)<br/>
[CDialog (clase)](cdialog-class.md)
