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
ms.openlocfilehash: 5ad8784f3bff999eec046aa91f52b1cd164764e5
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425884"
---
# <a name="cedit-class"></a>CEdit Class

Proporciona la funcionalidad de un control de edición de Windows.

## <a name="syntax"></a>Sintaxis

```
class CEdit : public CWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CEdit:: CEdit](#cedit)|Construye un objeto de control de `CEdit`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CEdit:: CanUndo](#canundo)|Determina si se puede deshacer una operación de control de edición.|
|[CEdit:: CharFromPos](#charfrompos)|Recupera los índices de línea y de carácter del carácter más próximo a una posición especificada.|
|[CEdit:: Clear](#clear)|Elimina (borra) la selección actual (si existe) en el control de edición.|
|[CEdit:: Copy](#copy)|Copia la selección actual (si existe) en el control de edición en el portapapeles en CF_TEXT formato.|
|[CEdit:: Create](#create)|Crea el control de edición de Windows y lo adjunta al objeto `CEdit`.|
|[CEdit:: Cut](#cut)|Elimina (corta) la selección actual (si existe) en el control de edición y copia el texto eliminado en el portapapeles en CF_TEXT formato.|
|[CEdit:: EmptyUndoBuffer](#emptyundobuffer)|Restablece (borra) la marca de deshacer de un control de edición.|
|[CEdit:: FmtLines](#fmtlines)|Establece la inclusión de caracteres de salto de línea automáticos en un control de edición de varias líneas.|
|[CEdit:: GetCueBanner](#getcuebanner)|Recupera el texto que se muestra como la indicación de texto o la sugerencia en un control de edición cuando el control está vacío y no tiene el foco.|
|[CEdit:: GetFirstVisibleLine](#getfirstvisibleline)|Determina la línea visible de nivel superior en un control de edición.|
|[CEdit:: GetHandle](#gethandle)|Recupera un identificador de la memoria que está asignada actualmente para un control de edición de varias líneas.|
|[CEdit:: GetHighlight](#gethighlight)|Obtiene los índices de los caracteres inicial y final de un intervalo de texto que está resaltado en el control de edición actual.|
|[CEdit:: GetLimitText](#getlimittext)|Obtiene la cantidad máxima de texto que puede contener este `CEdit`.|
|[CEdit:: GetLine](#getline)|Recupera una línea de texto de un control de edición.|
|[CEdit:: GetLineCount](#getlinecount)|Recupera el número de líneas de un control de edición de varias líneas.|
|[CEdit:: GetMargins](#getmargins)|Obtiene los márgenes izquierdo y derecho de esta `CEdit`.|
|[CEdit:: GetModify](#getmodify)|Determina si se ha modificado el contenido de un control de edición.|
|[CEdit:: GetPasswordChar](#getpasswordchar)|Recupera el carácter de contraseña que se muestra en un control de edición cuando el usuario escribe texto.|
|[CEdit:: GetRect](#getrect)|Obtiene el rectángulo de formato de un control de edición.|
|[CEdit:: GetSel](#getsel)|Obtiene la primera y la última posición de carácter de la selección actual en un control de edición.|
|[CEdit:: HideBalloonTip](#hideballoontip)|Oculta los globos de sugerencias asociados al control de edición actual.|
|[CEdit:: LimitText](#limittext)|Limita la longitud del texto que el usuario puede escribir en un control de edición.|
|[CEdit:: LineFromChar](#linefromchar)|Recupera el número de línea de la línea que contiene el índice de carácter especificado.|
|[CEdit:: LineIndex](#lineindex)|Recupera el índice de carácter de una línea dentro de un control de edición de varias líneas.|
|[CEdit:: LineLength](#linelength)|Recupera la longitud de una línea en un control de edición.|
|[CEdit:: LineScroll](#linescroll)|Desplaza el texto de un control de edición de varias líneas.|
|[CEdit::P pegar](#paste)|Inserta los datos del portapapeles en el control de edición en la posición actual del cursor. Los datos se insertan solo si el Portapapeles contiene datos en formato CF_TEXT.|
|[CEdit::P osFromChar](#posfromchar)|Recupera las coordenadas de la esquina superior izquierda de un índice de carácter especificado.|
|[CEdit:: ReplaceSel](#replacesel)|Reemplaza la selección actual en un control de edición con el texto especificado.|
|[CEdit:: SetCueBanner](#setcuebanner)|Establece el texto que se muestra como la indicación de texto o la sugerencia en un control de edición cuando el control está vacío y no tiene el foco.|
|[CEdit:: SetHandle](#sethandle)|Establece el identificador de la memoria local que va a usar un control de edición de varias líneas.|
|[CEdit:: SetHighlight](#sethighlight)|Resalta un intervalo de texto que se muestra en el control de edición actual.|
|[CEdit:: SetLimitText](#setlimittext)|Establece la cantidad máxima de texto que puede contener este `CEdit`.|
|[CEdit:: SetMargins](#setmargins)|Establece los márgenes izquierdo y derecho de esta `CEdit`.|
|[CEdit:: SetModify](#setmodify)|Establece o borra la marca de modificación de un control de edición.|
|[CEdit:: SetPasswordChar](#setpasswordchar)|Establece o quita un carácter de contraseña que se muestra en un control de edición cuando el usuario escribe texto.|
|[CEdit:: SetReadOnly](#setreadonly)|Establece el estado de solo lectura de un control de edición.|
|[CEdit:: SetRect](#setrect)|Establece el rectángulo de formato de un control de edición de varias líneas y actualiza el control.|
|[CEdit:: SetRectNP](#setrectnp)|Establece el rectángulo de formato de un control de edición de varias líneas sin volver a dibujar la ventana de control.|
|[CEdit:: SetSel](#setsel)|Selecciona un intervalo de caracteres en un control de edición.|
|[CEdit:: SetTabStops](#settabstops)|Establece las tabulaciones en un control de edición de varias líneas.|
|[CEdit:: ShowBalloonTip](#showballoontip)|Muestra un globo de sugerencias que está asociado al control de edición actual.|
|[CEdit:: Undo](#undo)|Invierte la última operación de edición del control.|

## <a name="remarks"></a>Observaciones

Un control de edición es una ventana secundaria rectangular en la que el usuario puede escribir texto.

Puede crear un control de edición desde una plantilla de cuadro de diálogo o directamente en el código. En ambos casos, llame primero al constructor `CEdit` para construir el `CEdit` objeto y, a continuación, llame a la función miembro [Create](#create) para crear el control de edición de Windows y adjuntarlo al objeto `CEdit`.

La construcción puede ser un proceso de un solo paso en una clase derivada de `CEdit`. Escriba un constructor para la clase derivada y llame a `Create` desde dentro del constructor.

`CEdit` hereda la funcionalidad significativa de `CWnd`. Para establecer y recuperar texto de un objeto `CEdit`, utilice las funciones miembro de `CWnd` [SetWindowText](cwnd-class.md#setwindowtext) y [GetWindowText](cwnd-class.md#getwindowtext), que establecen u obtienen todo el contenido de un control de edición, incluso si es un control multilínea. Las líneas de texto de un control multilínea se separan mediante secuencias de caracteres ' \r\n '. Además, si un control de edición es multilínea, obtenga y establezca parte del texto del control llamando a las funciones miembro de `CEdit` [GetLine](#getline), [SetSel](#setsel), [GetSel](#getsel)y [ReplaceSel](#replacesel).

Si desea controlar los mensajes de notificación de Windows enviados por un control de edición a su elemento primario (normalmente una clase derivada de `CDialog`), agregue una entrada de mapa de mensajes y una función miembro de controlador de mensajes a la clase primaria para cada mensaje.

Cada entrada de mapa de mensajes tiene el siguiente formato:

  **ON_** _Notificación_de ON_ **(** _ID._ **,** _memberFxn_ **)**

donde `id` especifica el identificador de la ventana secundaria del control de edición que envía la notificación y `memberFxn` es el nombre de la función miembro primaria que ha escrito para controlar la notificación.

El prototipo de función del elemento primario es el siguiente:

**afx_msg** void memberFxn **();**

A continuación se muestra una lista de posibles entradas de mapa de mensajes y una descripción de los casos en los que se enviarían a la primaria:

- ON_EN_CHANGE el usuario ha realizado una acción que puede haber alterado el texto en un control de edición. A diferencia del mensaje de notificación de EN_UPDATE, este mensaje de notificación se envía después de que Windows actualice la pantalla.

- ON_EN_ERRSPACE el control de edición no puede asignar suficiente memoria para satisfacer una solicitud concreta.

- ON_EN_HSCROLL el usuario hace clic en la barra de desplazamiento horizontal de un control de edición. Se notifica a la ventana primaria antes de que se actualice la pantalla.

- ON_EN_KILLFOCUS el control de edición pierde el foco de entrada.

- ON_EN_MAXTEXT la inserción actual ha superado el número de caracteres especificado para el control de edición y se ha truncado. También se envía cuando un control de edición no tiene el estilo de ES_AUTOHSCROLL y el número de caracteres que se va a insertar superará el ancho del control de edición. También se envía cuando un control de edición no tiene el estilo de ES_AUTOVSCROLL y el número total de líneas resultante de una inserción de texto superaría el alto del control de edición.

- ON_EN_SETFOCUS envía cuando un control de edición recibe el foco de entrada.

- ON_EN_UPDATE el control de edición está a punto de mostrar el texto modificado. Se envía una vez que el control ha dado formato al texto, pero antes de que el texto se contenga en pantalla para que se pueda modificar el tamaño de la ventana, si es necesario.

- ON_EN_VSCROLL el usuario hace clic en la barra de desplazamiento vertical de un control de edición. Se notifica a la ventana primaria antes de que se actualice la pantalla.

Si crea un objeto de `CEdit` dentro de un cuadro de diálogo, el objeto de `CEdit` se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.

Si crea un objeto de `CEdit` a partir de un recurso de cuadro de diálogo mediante el editor de cuadros de diálogo, el objeto de `CEdit` se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.

Si crea un objeto de `CEdit` dentro de una ventana, es posible que también tenga que destruirlo. Si crea el objeto de `CEdit` en la pila, se destruye automáticamente. Si crea el objeto de `CEdit` en el montón mediante la **nueva** función, debe llamar a **Delete** en el objeto para destruirlo cuando el usuario finaliza el control de edición de Windows. Si asigna memoria en el objeto `CEdit`, invalide el destructor `CEdit` para desechar las asignaciones.

Para modificar ciertos estilos en un control de edición (como ES_READONLY), debe enviar mensajes específicos al control en lugar de usar [ModifyStyle](cwnd-class.md#modifystyle). Vea [Editar estilos de control](/windows/win32/Controls/edit-control-styles) en el Windows SDK.

Para obtener más información sobre `CEdit`, consulte [controles](../../mfc/controls-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="canundo"></a>CEdit:: CanUndo

Llame a esta función para determinar si se puede deshacer la última operación de edición.

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la última operación de edición se puede deshacer mediante una llamada a la función miembro `Undo`; 0 si no se puede deshacer.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [EM_CANUNDO](/windows/win32/Controls/em-canundo) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEDIT:: Undo](#undo).

##  <a name="cedit"></a>CEdit:: CEdit

Construye un objeto `CEdit`.

```
CEdit();
```

### <a name="remarks"></a>Observaciones

Use [crear](#create) para construir el control de edición de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

##  <a name="charfrompos"></a>CEdit:: CharFromPos

Llame a esta función para recuperar los índices de línea y carácter de base cero del carácter más próximo al punto especificado en este control `CEdit`

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>Parámetros

*pt*<br/>
Coordenadas de un punto en el área cliente de este `CEdit` objeto.

### <a name="return-value"></a>Valor devuelto

Índice de carácter de la palabra de orden inferior y el índice de línea en la palabra de orden superior.

### <a name="remarks"></a>Observaciones

> [!NOTE]
>  Esta función miembro está disponible a partir de Windows 95 y Windows NT 4,0.

Para obtener más información, vea [EM_CHARFROMPOS](/windows/win32/Controls/em-charfrompos) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

##  <a name="clear"></a>CEdit:: Clear

Llame a esta función para eliminar (borrar) la selección actual (si existe) en el control de edición.

```
void Clear();
```

### <a name="remarks"></a>Observaciones

La eliminación realizada por `Clear` se puede deshacer llamando a la función miembro [Undo](#undo) .

Para eliminar la selección actual y colocar el contenido eliminado en el portapapeles, llame a la función miembro [CUT](#cut) .

Para obtener más información, vea [WM_CLEAR](/windows/win32/dataxchg/wm-clear) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

##  <a name="copy"></a>CEdit:: Copy

Llame a esta función para copiar la selección actual (si existe) en el control de edición del portapapeles en formato de CF_TEXT.

```
void Copy();
```

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [WM_COPY](/windows/win32/dataxchg/wm-copy) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

##  <a name="create"></a>CEdit:: Create

Crea el control de edición de Windows y lo adjunta al objeto `CEdit`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de edición. Aplique cualquier combinación de [estilos de edición](styles-used-by-mfc.md#edit-styles) al control.

*Rect*<br/>
Especifica el tamaño y la posición del control de edición. Puede ser un objeto `CRect` o `RECT` estructura.

*pParentWnd*<br/>
Especifica la ventana primaria del control de edición (normalmente una `CDialog`). No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de edición.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización es correcta; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Cree un objeto de `CEdit` en dos pasos. En primer lugar, llame al constructor `CEdit` y, a continuación, llame a `Create`, que crea el control de edición de Windows y lo adjunta al objeto `CEdit`.

Cuando se ejecuta `Create`, Windows envía los mensajes [WM_NCCREATE](/windows/win32/winmsg/wm-nccreate), [WM_NCCALCSIZE](/windows/win32/winmsg/wm-nccalcsize), [WM_CREATE](/windows/win32/winmsg/wm-create)y [WM_GETMINMAXINFO](/windows/win32/winmsg/wm-getminmaxinfo) al control de edición.

Estos mensajes se controlan de forma predeterminada mediante las funciones de miembro [OnNcCreate](cwnd-class.md#onnccreate), [OnNcCalcSize](cwnd-class.md#onnccalcsize), [alcrear](cwnd-class.md#oncreate)y [OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo) en la clase base `CWnd`. Para extender el control de mensajes predeterminado, derive una clase de `CEdit`, agregue un mapa de mensajes a la nueva clase e invalide las funciones miembro de controlador de mensajes anteriores. Invalide `OnCreate`, por ejemplo, para realizar la inicialización necesaria para la nueva clase.

Aplique los siguientes [estilos de ventana](styles-used-by-mfc.md#window-styles) a un control de edición.

- WS_CHILD siempre

- WS_VISIBLE normalmente

- WS_DISABLED raramente

- WS_GROUP a controles de grupo

- WS_TABSTOP incluir el control de edición en el orden de tabulación

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

##  <a name="cut"></a>CEdit:: Cut

Llame a esta función para eliminar (cortar) la selección actual (si existe) en el control de edición y copiar el texto eliminado en el portapapeles en CF_TEXT formato.

```
void Cut();
```

### <a name="remarks"></a>Observaciones

La eliminación realizada por `Cut` se puede deshacer llamando a la función miembro [Undo](#undo) .

Para eliminar la selección actual sin colocar el texto eliminado en el portapapeles, llame a la función miembro [Clear](#clear) .

Para obtener más información, vea [WM_CUT](/windows/win32/dataxchg/wm-cut) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

##  <a name="emptyundobuffer"></a>CEdit:: EmptyUndoBuffer

Llame a esta función para restablecer (borrar) la marca de deshacer de un control de edición.

```
void EmptyUndoBuffer();
```

### <a name="remarks"></a>Observaciones

Ahora, el control de edición no podrá deshacer la última operación. La marca de deshacer se establece siempre que se puede deshacer una operación dentro del control de edición.

La marca de deshacer se borra automáticamente siempre que se llama a las funciones miembro de [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) o [SetHandle](#sethandle)`CWnd`.

Para obtener más información, vea [EM_EMPTYUNDOBUFFER](/windows/win32/Controls/em-emptyundobuffer) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

##  <a name="fmtlines"></a>CEdit:: FmtLines

Llame a esta función para establecer en o desactivada la inclusión de caracteres de salto de línea automáticos en un control de edición de varias líneas.

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>Parámetros

*bAddEOL*<br/>
Especifica si se van a insertar caracteres de salto de línea. Un valor TRUE inserta los caracteres; Si el valor es FALSE, se quitan.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se produce algún formato; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Un salto de línea flexible se compone de dos retornos de carro y un avance de línea insertado al final de una línea que se rompe debido al ajuste de palabras. Un salto de línea fuerte se compone de un retorno de carro y un avance de línea. Las líneas que finalizan con un salto de línea no se ven afectadas por `FmtLines`.

Windows solo responderá si el objeto `CEdit` es un control de edición de varias líneas.

`FmtLines` solo afecta al búfer devuelto por [GetHandle](#gethandle) y el texto devuelto por [WM_GETTEXT](/windows/win32/winmsg/wm-gettext). No tiene ningún impacto en la presentación del texto en el control de edición.

Para obtener más información, vea [EM_FMTLINES](/windows/win32/Controls/em-fmtlines) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

##  <a name="getcuebanner"></a>CEdit:: GetCueBanner

Recupera el texto que se muestra como la indicación de texto o la sugerencia en un control de edición cuando el control está vacío.

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
enuncia Puntero a una cadena que contiene el texto de la indicación.

*cchText*<br/>
de Número de caracteres que se pueden recibir. Este número incluye el carácter nulo de terminación.

### <a name="return-value"></a>Valor devuelto

Para la primera sobrecarga, TRUE si el método es correcto; en caso contrario, FALSE.

Para la segunda sobrecarga, un [CString](../../atl-mfc-shared/using-cstring.md) que contiene el texto de indicación si el método se realiza correctamente; de lo contrario, la cadena vacía ("").

### <a name="remarks"></a>Observaciones

Este método envía el mensaje de [EM_GETCUEBANNER](/windows/win32/Controls/em-getcuebanner) , que se describe en el Windows SDK. Para obtener más información, vea la macro [Edit_GetCueBannerText](/windows/win32/api/commctrl/nf-commctrl-edit_getcuebannertext) .

##  <a name="getfirstvisibleline"></a>CEdit:: GetFirstVisibleLine

Llame a esta función para determinar la línea visible de nivel superior en un control de edición.

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la línea visible superior. En el caso de los controles de edición de una sola línea, el valor devuelto es 0.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [EM_GETFIRSTVISIBLELINE](/windows/win32/Controls/em-getfirstvisibleline) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

##  <a name="gethandle"></a>CEdit:: GetHandle

Llame a esta función para recuperar un identificador de la memoria asignada actualmente para un control de edición de varias líneas.

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador de memoria local que identifica el búfer que contiene el contenido del control de edición. Si se produce un error, como el envío del mensaje a un control de edición de una sola línea, el valor devuelto es 0.

### <a name="remarks"></a>Observaciones

El identificador es un identificador de memoria local y puede ser utilizado por cualquiera de las funciones de memoria **local** de Windows que toman un identificador de memoria local como parámetro.

`GetHandle` solo lo procesan los controles de edición de varias líneas.

Llame a `GetHandle` para un control de edición de varias líneas en un cuadro de diálogo solo si el cuadro de diálogo se creó con la marca de estilo DS_LOCALEDIT establecida. Si no se establece el estilo de DS_LOCALEDIT, seguirá teniendo un valor devuelto distinto de cero, pero no podrá usar el valor devuelto.

> [!NOTE]
> `GetHandle` no funcionará con Windows 95/98. Si llama a `GetHandle` en Windows 95/98, devolverá NULL. `GetHandle` funcionará como se documenta en Windows NT, versiones 3,51 y posteriores.

Para obtener más información, vea [EM_GETHANDLE](/windows/win32/Controls/em-gethandle) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

##  <a name="gethighlight"></a>CEdit:: GetHighlight

Obtiene los índices del primer y último carácter de un intervalo de texto que está resaltado en el control de edición actual.

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pichStart*|enuncia Índice de base cero del primer carácter del intervalo de texto que se resalta.|
|*pichEnd*|enuncia Índice de base cero del último carácter del intervalo de texto que se resalta.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método envía el mensaje de [EM_GETHILITE](/windows/win32/Controls/em-gethilite) , que se describe en el Windows SDK. Tanto `SetHighlight` como `GetHighlight` están habilitadas actualmente solo para compilaciones Unicode.

##  <a name="getlimittext"></a>CEdit:: GetLimitText

Llame a esta función miembro para obtener el límite de texto de este objeto `CEdit`.

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>Valor devuelto

Límite de texto actual, en TCHARs, para este objeto `CEdit`.

### <a name="remarks"></a>Observaciones

El límite de texto es la cantidad máxima de texto, en TCHARs, que el control de edición puede aceptar.

> [!NOTE]
>  Esta función miembro está disponible a partir de Windows 95 y Windows NT 4,0.

Para obtener más información, vea [EM_GETLIMITTEXT](/windows/win32/Controls/em-getlimittext) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

##  <a name="getline"></a>CEdit:: GetLine

Llame a esta función para recuperar una línea de texto de un control de edición y colocarla en *lpszbuffer se*.

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
Especifica el número de línea que se va a recuperar de un control de edición de varias líneas. Los números de línea son de base cero; un valor de 0 especifica la primera línea. Este parámetro se omite en un control de edición de una sola línea.

*Lpszbuffer se*<br/>
Apunta al búfer que recibe una copia de la línea. La primera palabra del búfer debe especificar el número máximo de TCHARs que se pueden copiar en el búfer.

*nMaxLength*<br/>
Especifica el número máximo de caracteres TCHAR que se pueden copiar en el búfer. `GetLine` coloca este valor en la primera palabra de *lpszbuffer se* antes de hacer la llamada a Windows.

### <a name="return-value"></a>Valor devuelto

Número de caracteres que realmente se va a copiar. El valor devuelto es 0 si el número de línea especificado por *NINDEX* es mayor que el número de líneas del control de edición.

### <a name="remarks"></a>Observaciones

La línea copiada no contiene un carácter de terminación null.

Para obtener más información, vea [EM_GETLINE](/windows/win32/Controls/em-getline) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEDIT:: GetLineCount](#getlinecount).

##  <a name="getlinecount"></a>CEdit:: GetLineCount

Llame a esta función para recuperar el número de líneas de un control de edición de varias líneas.

```
int GetLineCount() const;
```

### <a name="return-value"></a>Valor devuelto

Entero que contiene el número de líneas del control de edición de varias líneas. Si no se ha escrito ningún texto en el control de edición, el valor devuelto es 1.

### <a name="remarks"></a>Observaciones

`GetLineCount` solo lo procesan los controles de edición de varias líneas.

Para obtener más información, vea [EM_GETLINECOUNT](/windows/win32/Controls/em-getlinecount) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

##  <a name="getmargins"></a>CEdit:: GetMargins

Llame a esta función miembro para recuperar los márgenes izquierdo y derecho de este control de edición.

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>Valor devuelto

Ancho del margen izquierdo en la palabra de orden inferior y el ancho del margen derecho en la palabra de orden superior.

### <a name="remarks"></a>Observaciones

Los márgenes se miden en píxeles.

> [!NOTE]
>  Esta función miembro está disponible a partir de Windows 95 y Windows NT 4,0.

Para obtener más información, vea [EM_GETMARGINS](/windows/win32/Controls/em-getmargins) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEditView:: GetEditCtrl](ceditview-class.md#geteditctrl).

##  <a name="getmodify"></a>CEdit:: GetModify

Llame a esta función para determinar si se ha modificado el contenido de un control de edición.

```
BOOL GetModify() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha modificado el contenido del control de edición; 0 si se han mantenido sin cambios.

### <a name="remarks"></a>Observaciones

Windows mantiene una marca interna que indica si se ha cambiado el contenido del control de edición. Esta marca se borra cuando se crea por primera vez el control de edición y también puede borrarse llamando a la función miembro [SetModify](#setmodify) .

Para obtener más información, vea [EM_GETMODIFY](/windows/win32/Controls/em-getmodify) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

##  <a name="getpasswordchar"></a>CEdit:: GetPasswordChar

Llame a esta función para recuperar el carácter de la contraseña que se muestra en un control de edición cuando el usuario escribe texto.

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>Valor devuelto

Especifica el carácter que se va a mostrar en lugar del carácter que el usuario ha escrito. El valor devuelto es NULL si no existe ningún carácter de contraseña.

### <a name="remarks"></a>Observaciones

Si crea el control de edición con el estilo ES_PASSWORD, el archivo DLL que admite el control determina el carácter de contraseña predeterminado. El manifiesto o el método [InitCommonControlsEx](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex) determina qué dll es compatible con el control de edición. Si user32. dll admite el control de edición, el carácter de contraseña predeterminado es asterisco (' * ', U + 002A). Si la versión 6 de COMCTL32. dll es compatible con el control de edición, el carácter predeterminado es el círculo negro (' ● ', U + 25CF). Para obtener más información sobre qué DLL y versión es compatible con los controles comunes, vea [Shell y versiones de controles comunes](/previous-versions/windows/desktop/legacy/bb776779\(v=vs.85\)).

Este método envía el mensaje de [EM_GETPASSWORDCHAR](/windows/win32/Controls/em-getpasswordchar) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

##  <a name="getrect"></a>CEdit:: GetRect

Llame a esta función para obtener el rectángulo de formato de un control de edición.

```
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a la estructura `RECT` que recibe el rectángulo de formato.

### <a name="remarks"></a>Observaciones

El rectángulo de formato es el rectángulo de limitación del texto, que es independiente del tamaño de la ventana de control de edición.

Las funciones miembro [SetRect](#setrect) y [SetRectNP](#setrectnp) pueden modificar el rectángulo de formato de un control de edición de varias líneas.

Para obtener más información, vea [EM_GETRECT](/windows/win32/Controls/em-getrect) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEDIT:: LimitText](#limittext).

##  <a name="getsel"></a>CEdit:: GetSel

Llame a esta función para obtener las posiciones de caracteres inicial y final de la selección actual (si existe) en un control de edición, mediante el valor devuelto o los parámetros.

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

La versión que devuelve DWORD devuelve un valor que contiene la posición inicial en la palabra de orden inferior y la posición del primer carácter no seleccionado después del final de la selección en la palabra de orden superior.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [EM_GETSEL](/windows/win32/Controls/em-getsel) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

##  <a name="hideballoontip"></a>CEdit:: HideBalloonTip

Oculta los globos de sugerencias asociados al control de edición actual.

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Esta función envía el mensaje de [EM_HIDEBALLOONTIP](/windows/win32/Controls/em-hideballoontip) , que se describe en el Windows SDK.

##  <a name="limittext"></a>CEdit:: LimitText

Llame a esta función para limitar la longitud del texto que el usuario puede escribir en un control de edición.

```
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>Parámetros

*nChars*<br/>
Especifica la longitud (en TCHARs) del texto que el usuario puede escribir. Si este parámetro es 0, la longitud del texto se establece en UINT_MAX bytes. Este es el comportamiento predeterminado.

### <a name="remarks"></a>Observaciones

Al cambiar el límite de texto, solo se restringe el texto que el usuario puede escribir. No tiene ningún efecto en ningún texto que ya esté en el control de edición, ni afecta a la longitud del texto copiado en el control de edición por parte de la función miembro [SetWindowText](cwnd-class.md#setwindowtext) en `CWnd`. Si una aplicación utiliza la función `SetWindowText` para colocar más texto en un control de edición que se especifica en la llamada a `LimitText`, el usuario puede eliminar cualquier texto del control de edición. Sin embargo, el límite de texto impedirá que el usuario Reemplace el texto existente por un nuevo texto, a menos que la eliminación de la selección actual haga que el texto quede por debajo del límite de texto.

> [!NOTE]
>  En Win32 (Windows NT y Windows 95/98), [SetLimitText](#setlimittext) reemplaza esta función.

Para obtener más información, vea [EM_LIMITTEXT](/windows/win32/Controls/em-limittext) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

##  <a name="linefromchar"></a>CEdit:: LineFromChar

Llame a esta función para recuperar el número de línea de la línea que contiene el índice de carácter especificado.

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Contiene el valor de índice de base cero para el carácter deseado en el texto del control de edición o contiene-1. Si *NINDEX* es-1, especifica la línea actual, es decir, la línea que contiene el símbolo de intercalación.

### <a name="return-value"></a>Valor devuelto

Número de línea de base cero de la línea que contiene el índice de caracteres especificado por *NINDEX*. Si *NINDEX* es-1, se devuelve el número de la línea que contiene el primer carácter de la selección. Si no hay ninguna selección, se devuelve el número de línea actual.

### <a name="remarks"></a>Observaciones

Un índice de caracteres es el número de caracteres desde el principio del control de edición.

Esta función miembro solo la usan los controles de edición de varias líneas.

Para obtener más información, vea [EM_LINEFROMCHAR](/windows/win32/Controls/em-linefromchar) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

##  <a name="lineindex"></a>CEdit:: LineIndex

Llame a esta función para recuperar el índice de carácter de una línea dentro de un control de edición de varias líneas.

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>Parámetros

*nlínea*<br/>
Contiene el valor de índice de la línea deseada en el texto del control de edición o contiene-1. Si *nlínea* es-1, especifica la línea actual, es decir, la línea que contiene el símbolo de intercalación.

### <a name="return-value"></a>Valor devuelto

Índice de carácter de la línea especificada en *nlínea* o-1 si el número de línea especificado es mayor que el número de líneas del control de edición.

### <a name="remarks"></a>Observaciones

El índice de carácter es el número de caracteres desde el principio del control de edición hasta la línea especificada.

Esta función miembro solo la procesan los controles de edición de varias líneas.

Para obtener más información, vea [EM_LINEINDEX](/windows/win32/controls/em-lineindex) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

##  <a name="linelength"></a>CEdit:: LineLength

Recupera la longitud de una línea en un control de edición.

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>Parámetros

*nlínea*<br/>
Índice de base cero de un carácter de la línea cuya longitud se va a recuperar. El valor predeterminado es -1.

### <a name="return-value"></a>Valor devuelto

En el caso de los controles de edición de una sola línea, el valor devuelto es la longitud, en TCHARs, del texto del control de edición.

En el caso de los controles de edición multilínea, el valor devuelto es la longitud, en TCHARs, de la línea especificada por el parámetro *nlínea* . En el caso de texto ANSI, la longitud es el número de bytes de la línea; en el caso de texto Unicode, la longitud es el número de caracteres de la línea. La longitud no incluye el carácter de retorno de carro al final de la línea.

Si el parámetro *nlínea* es mayor que el número de caracteres del control, el valor devuelto es cero.

Si el parámetro *nlínea* es-1, el valor devuelto es el número de caracteres no seleccionados en las líneas que contienen los caracteres seleccionados. Por ejemplo, si la selección se extiende desde el cuarto carácter de una línea hasta el octavo carácter desde el final de la línea siguiente, el valor devuelto es 10. Es decir, tres caracteres en la primera línea y siete en el siguiente.

Para obtener más información sobre el tipo TCHAR, vea la fila TCHAR en la tabla de [tipos de datos de Windows](/windows/win32/WinProg/windows-data-types).

### <a name="remarks"></a>Observaciones

Este método es compatible con el mensaje de [EM_LINELENGTH](/windows/win32/Controls/em-linelength) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEDIT:: LineIndex](#lineindex).

##  <a name="linescroll"></a>CEdit:: LineScroll

Llame a esta función para desplazar el texto de un control de edición de varias líneas.

```
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>Parámetros

*nLines*<br/>
Especifica el número de líneas que se va a desplazar verticalmente.

*nChars*<br/>
Especifica el número de posiciones de caracteres que se va a desplazar horizontalmente. Este valor se omite si el control de edición tiene el estilo ES_RIGHT o ES_CENTER.

### <a name="remarks"></a>Observaciones

Esta función miembro solo se procesa mediante controles de edición de varias líneas.

El control de edición no se desplaza verticalmente más allá de la última línea de texto del control de edición. Si la línea actual más el número de líneas especificado por *nLines* supera el número total de líneas en el control de edición, el valor se ajusta de modo que la última línea del control de edición se desplaza a la parte superior de la ventana de edición del control.

`LineScroll` se puede utilizar para desplazarse horizontalmente más allá del último carácter de cualquier línea.

Para obtener más información, vea [EM_LINESCROLL](/windows/win32/Controls/em-linescroll) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEDIT:: GetFirstVisibleLine](#getfirstvisibleline).

##  <a name="paste"></a>CEdit::P pegar

Llame a esta función para insertar los datos del portapapeles en el `CEdit` en el punto de inserción.

```
void Paste();
```

### <a name="remarks"></a>Observaciones

Los datos se insertan solo si el Portapapeles contiene datos en formato CF_TEXT.

Para obtener más información, vea [WM_PASTE](/windows/win32/dataxchg/wm-paste) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

##  <a name="posfromchar"></a>CEdit::P osFromChar

Llame a esta función para obtener la posición (esquina superior izquierda) de un carácter determinado dentro de este objeto `CEdit`.

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>Parámetros

*nChar*<br/>
Índice de base cero del carácter especificado.

### <a name="return-value"></a>Valor devuelto

Coordenadas de la esquina superior izquierda del carácter especificado por *nChar*.

### <a name="remarks"></a>Observaciones

El carácter se especifica proporcionando su valor de índice basado en cero. Si *nChar* es mayor que el índice del último carácter de este `CEdit` objeto, el valor devuelto especifica las coordenadas de la posición de carácter justo después del último carácter de este objeto `CEdit`.

> [!NOTE]
>  Esta función miembro está disponible a partir de Windows 95 y Windows NT 4,0.

Para obtener más información, vea [EM_POSFROMCHAR](/windows/win32/Controls/em-posfromchar) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEDIT:: LineFromChar](#linefromchar).

##  <a name="replacesel"></a>CEdit:: ReplaceSel

Llame a esta función para reemplazar la selección actual en un control de edición con el texto especificado por *lpszNewText*.

```
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>Parámetros

*lpszNewText*<br/>
Apunta a una cadena terminada en null que contiene el texto de reemplazo.

*bCanUndo*<br/>
Para especificar que esta función se puede deshacer, establezca el valor de este parámetro en TRUE. El valor predeterminado es FALSE.

### <a name="remarks"></a>Observaciones

Reemplaza solo una parte del texto en un control de edición. Si desea reemplazar todo el texto, use la función miembro [CWnd:: SetWindowText](cwnd-class.md#setwindowtext) .

Si no hay ninguna selección actual, el texto de reemplazo se inserta en la ubicación actual del cursor.

Para obtener más información, vea [EM_REPLACESEL](/windows/win32/Controls/em-replacesel) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEDIT:: LineIndex](#lineindex).

##  <a name="setcuebanner"></a>CEdit:: SetCueBanner

Establece el texto que se muestra como la indicación de texto o la sugerencia en un control de edición cuando el control está vacío.

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
de Puntero a una cadena que contiene la pila que se va a mostrar en el control de edición.

*fDrawWhenFocused*<br/>
de Si es FALSE, el banner de indicación no se dibuja cuando el usuario hace clic en el control de edición y proporciona al control el foco.

Si es TRUE, el banner de indicación se dibuja incluso cuando el control tiene el foco. El banner de indicación desaparece cuando el usuario empieza a escribir en el control.

El valor predeterminado es FALSE.

### <a name="return-value"></a>Valor devuelto

TRUE si el método es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método envía el mensaje de [EM_SETCUEBANNER](/windows/win32/Controls/em-setcuebanner) , que se describe en el Windows SDK. Para obtener más información, vea la macro [Edit_SetCueBannerTextFocused](/windows/win32/api/commctrl/nf-commctrl-edit_setcuebannertextfocused) .

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el método [CEDIT:: SetCueBanner](#setcuebanner) .

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

##  <a name="sethandle"></a>CEdit:: SetHandle

Llame a esta función para establecer el identificador de la memoria local que va a usar un control de edición de varias líneas.

```
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>Parámetros

*hBuffer*<br/>
Contiene un identificador para la memoria local. Este identificador debe haberse creado mediante una llamada anterior a la función de Windows [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) mediante la marca LMEM_MOVEABLE. Se supone que la memoria contiene una cadena terminada en NULL. Si no es así, el primer byte de la memoria asignada debe establecerse en 0.

### <a name="remarks"></a>Observaciones

Después, el control de edición usará este búfer para almacenar el texto que se muestra actualmente en lugar de asignar su propio búfer.

Esta función miembro solo se procesa mediante controles de edición de varias líneas.

Antes de que una aplicación establezca un nuevo identificador de memoria, debe usar la función miembro [GetHandle](#gethandle) para obtener el identificador del búfer de memoria actual y liberar esa memoria mediante el `LocalFree` función de Windows.

`SetHandle` borra el búfer de deshacer (la función miembro [CanUndo](#canundo) devuelve 0) y la marca de modificación interna (la función miembro [GetModify](#getmodify) devuelve 0). La ventana Editar control se vuelve a dibujar.

Puede usar esta función miembro en un control de edición de varias líneas en un cuadro de diálogo solo si ha creado el cuadro de diálogo con la marca de estilo DS_LOCALEDIT establecida.

> [!NOTE]
> `GetHandle` no funcionará con Windows 95/98. Si llama a `GetHandle` en Windows 95/98, devolverá NULL. `GetHandle` funcionará como se documenta en Windows NT, versiones 3,51 y posteriores.

Para obtener más información, vea [EM_SETHANDLE](/windows/win32/Controls/em-sethandle), [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)y [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

##  <a name="sethighlight"></a>CEdit:: SetHighlight

Resalta un intervalo de texto que se muestra en el control de edición actual.

```
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*ichStart*|de Índice de base cero del primer carácter del intervalo de texto que se va a resaltar.|
|*ichEnd*|de Índice de base cero del último carácter del intervalo de texto que se va a resaltar.|

### <a name="remarks"></a>Observaciones

Este método envía el mensaje de [EM_SETHILITE](/windows/win32/Controls/em-sethilite) , que se describe en el Windows SDK.  Este método envía el mensaje de [EM_SETHILITE](/windows/win32/Controls/em-sethilite) , que se describe en el Windows SDK. Tanto `SetHighlight` como `GetHighlight` solo están habilitadas para compilaciones Unicode.

##  <a name="setlimittext"></a>CEdit:: SetLimitText

Llame a esta función miembro para establecer el límite de texto de este objeto `CEdit`.

```
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>Parámetros

*Nmáx.*<br/>
Nuevo límite de texto, en caracteres.

### <a name="remarks"></a>Observaciones

El límite de texto es la cantidad máxima de texto, en caracteres, que el control de edición puede aceptar.

Al cambiar el límite de texto, solo se restringe el texto que el usuario puede escribir. No tiene ningún efecto en ningún texto que ya esté en el control de edición, ni afecta a la longitud del texto copiado en el control de edición por parte de la función miembro [SetWindowText](cwnd-class.md#setwindowtext) en `CWnd`. Si una aplicación utiliza la función `SetWindowText` para colocar más texto en un control de edición que se especifica en la llamada a `LimitText`, el usuario puede eliminar cualquier texto del control de edición. Sin embargo, el límite de texto impedirá que el usuario Reemplace el texto existente por un nuevo texto, a menos que la eliminación de la selección actual haga que el texto quede por debajo del límite de texto.

Esta función reemplaza [LimitText](#limittext) en Win32.

Para obtener más información, vea [EM_SETLIMITTEXT](/windows/win32/Controls/em-setlimittext) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEditView:: GetEditCtrl](ceditview-class.md#geteditctrl).

##  <a name="setmargins"></a>CEdit:: SetMargins

Llame a este método para establecer los márgenes izquierdo y derecho de este control de edición.

```
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>Parámetros

*nLeft*<br/>
Ancho del nuevo margen izquierdo, en píxeles.

*nRight*<br/>
Ancho del nuevo margen derecho, en píxeles.

### <a name="remarks"></a>Observaciones

> [!NOTE]
>  Esta función miembro está disponible a partir de Windows 95 y Windows NT 4,0.

Para obtener más información, vea [EM_SETMARGINS](/windows/win32/Controls/em-setmargins) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEditView:: GetEditCtrl](ceditview-class.md#geteditctrl).

##  <a name="setmodify"></a>CEdit:: SetModify

Llame a esta función para establecer o borrar la marca modificada de un control de edición.

```
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>Parámetros

*bModified*<br/>
Un valor de TRUE indica que el texto se ha modificado y el valor FALSE indica que no se ha modificado. De forma predeterminada, se establece la marca modificada.

### <a name="remarks"></a>Observaciones

La marca Modified indica si el texto del control de edición se ha modificado o no. Se establece automáticamente cada vez que el usuario cambia el texto. Su valor se puede recuperar con la función miembro [GetModify](#getmodify) .

Para obtener más información, vea [EM_SETMODIFY](/windows/win32/Controls/em-setmodify) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEDIT:: GetModify](#getmodify).

##  <a name="setpasswordchar"></a>CEdit:: SetPasswordChar

Llame a esta función para establecer o quitar un carácter de contraseña que se muestra en un control de edición cuando el usuario escribe texto.

```
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>Parámetros

*Cam*<br/>
Especifica el carácter que se va a mostrar en lugar del carácter escrito por el usuario. Si *CH* es 0, se muestran los caracteres reales que escribe el usuario.

### <a name="remarks"></a>Observaciones

Cuando se establece un carácter de contraseña, se muestra ese carácter para cada carácter que el usuario escribe.

Esta función miembro no tiene ningún efecto en un control de edición de varias líneas.

Cuando se llama a la función miembro `SetPasswordChar`, `CEdit` volverá a dibujar todos los caracteres visibles mediante el carácter especificado por *CH*.

Si el control de edición se crea con el estilo [ES_PASSWORD](styles-used-by-mfc.md#edit-styles) , el carácter de contraseña predeterminado se establece en un asterisco ( <strong>\*</strong>). Este estilo se quita si se llama a `SetPasswordChar` con *CH* establecido en 0.

Para obtener más información, vea [EM_SETPASSWORDCHAR](/windows/win32/Controls/em-setpasswordchar) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

##  <a name="setreadonly"></a>CEdit:: SetReadOnly

Llama a esta función para establecer el estado de solo lectura de un control de edición.

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>Parámetros

*bReadOnly*<br/>
Especifica si se debe establecer o quitar el estado de solo lectura del control de edición. Un valor de TRUE establece el estado en solo lectura; un valor de FALSE establece el estado en lectura/escritura.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realiza correctamente, o 0 si se produce un error.

### <a name="remarks"></a>Observaciones

La configuración actual se puede encontrar mediante la comprobación de la marca de [ES_READONLY](styles-used-by-mfc.md#edit-styles) en el valor devuelto de [CWnd:: getStyle](cwnd-class.md#getstyle).

Para obtener más información, vea [EM_SETREADONLY](/windows/win32/Controls/em-setreadonly) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

##  <a name="setrect"></a>CEdit:: SetRect

Llame a esta función para establecer las dimensiones de un rectángulo utilizando las coordenadas especificadas.

```
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a la estructura `RECT` o `CRect` objeto que especifica las nuevas dimensiones del rectángulo de formato.

### <a name="remarks"></a>Observaciones

Este miembro solo lo procesan los controles de edición de varias líneas.

Use `SetRect` para establecer el rectángulo de formato de un control de edición de varias líneas. El rectángulo de formato es el rectángulo de limitación del texto, que es independiente del tamaño de la ventana de control de edición. Cuando se crea por primera vez el control de edición, el rectángulo de formato es el mismo que el área cliente de la ventana de control de edición. Mediante el uso de la función miembro `SetRect`, una aplicación puede hacer que el rectángulo de formato sea más grande o más pequeño que la ventana de control de edición.

Si el control de edición no tiene ninguna barra de desplazamiento, el texto se recortará y no se ajustará si el rectángulo de formato se hace más grande que la ventana. Si el control de edición contiene un borde, el rectángulo de formato se reduce con el tamaño del borde. Si ajusta el rectángulo devuelto por la función miembro `GetRect`, debe quitar el tamaño del borde antes de pasar el rectángulo a `SetRect`.

Cuando se llama a `SetRect`, también se vuelve a formatear y volver a mostrar el texto del control de edición.

Para obtener más información, vea [EM_SETRECT](/windows/win32/Controls/em-setrect) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

##  <a name="setrectnp"></a>CEdit:: SetRectNP

Llame a esta función para establecer el rectángulo de formato de un control de edición de varias líneas.

```
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a una estructura `RECT` o a un objeto `CRect` que especifica las nuevas dimensiones del rectángulo.

### <a name="remarks"></a>Observaciones

El rectángulo de formato es el rectángulo de limitación del texto, que es independiente del tamaño de la ventana de control de edición.

`SetRectNP` es idéntica a la función miembro `SetRect`, salvo que la ventana Editar control no se vuelve a dibujar.

Cuando se crea por primera vez el control de edición, el rectángulo de formato es el mismo que el área cliente de la ventana de control de edición. Al llamar a la función miembro `SetRectNP`, una aplicación puede hacer que el rectángulo de formato sea mayor o menor que la ventana de control de edición.

Si el control de edición no tiene ninguna barra de desplazamiento, el texto se recortará y no se ajustará si el rectángulo de formato se hace más grande que la ventana.

Este miembro solo lo procesan los controles de edición de varias líneas.

Para obtener más información, vea [EM_SETRECTNP](/windows/win32/Controls/em-setrectnp) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEDIT:: SetRect](#setrect).

##  <a name="setsel"></a>CEdit:: SetSel

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
Especifica la posición inicial en la palabra de orden inferior y la posición final en la palabra de orden superior. Si la palabra de orden inferior es 0 y la palabra de orden superior es-1, se selecciona todo el texto del control de edición. Si la palabra de orden inferior es-1, se quita cualquier selección actual.

*bNoScroll*<br/>
Indica si el símbolo de intercalación se debe desplazar en la vista. Si es FALSE, el símbolo de intercalación se desplaza a la vista. Si es TRUE, el símbolo de intercalación no se desplaza en la vista.

*nStartChar*<br/>
Especifica la posición inicial. Si *nStartChar* es 0 y *nEndChar* es-1, se selecciona todo el texto del control de edición. Si *nStartChar* es-1, se quita cualquier selección actual.

*nEndChar*<br/>
Especifica la posición final.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [EM_SETSEL](/windows/win32/Controls/em-setsel) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEDIT:: GetSel](#getsel).

##  <a name="settabstops"></a>CEdit:: SetTabStops

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
Especifica que las tabulaciones se van a establecer en cada unidad de cuadro de diálogo de *cxEachStop* .

*nTabStops*<br/>
Especifica el número de tabulaciones contenidas en *rgTabStops*. Este número debe ser mayor que 1.

*rgTabStops*<br/>
Apunta a una matriz de enteros sin signo que especifican las tabulaciones en las unidades de cuadro de diálogo. Una unidad de cuadro de diálogo es una distancia horizontal o vertical. Una unidad de cuadro de diálogo horizontal es igual a una cuarta parte de la unidad de ancho base del cuadro de diálogo actual y 1 unidad de cuadro de diálogo vertical es igual a una octava parte de la unidad de alto de cuadro de diálogo actual. Las unidades base de cuadro de diálogo se calculan en función del alto y el ancho de la fuente actual del sistema. La función `GetDialogBaseUnits` Windows devuelve las unidades base de diálogo actuales en píxeles.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se han establecido las pestañas; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Cuando se copia texto en un control de edición de varias líneas, cualquier carácter de tabulación del texto hará que se genere espacio hasta la siguiente tabulación.

Para establecer las tabulaciones en el tamaño predeterminado de 32 unidades de cuadro de diálogo, llame a la versión sin parámetros de esta función miembro. Para establecer las tabulaciones en un tamaño distinto de 32, llame a la versión con el parámetro *cxEachStop* . Para establecer las tabulaciones en una matriz de tamaños, use la versión con dos parámetros.

Esta función miembro solo la procesan los controles de edición de varias líneas.

`SetTabStops` no vuelve a dibujar automáticamente la ventana de edición. Si cambia las tabulaciones del texto que ya está en el control de edición, llame a [CWnd:: InvalidateRect](cwnd-class.md#invalidaterect) para volver a dibujar la ventana de edición.

Para obtener más información, vea [EM_SETTABSTOPS](/windows/win32/Controls/em-settabstops) y [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CEditView:: SetTabStops](ceditview-class.md#settabstops).

##  <a name="showballoontip"></a>CEdit:: ShowBalloonTip

Muestra un globo de sugerencias que está asociado al control de edición actual.

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
|*pEditBalloonTip*|de Puntero a una estructura [EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip) que describe el globo de sugerencias.|
|*lpszTitle*|de Puntero a una cadena Unicode que contiene el título del globo de sugerencias.|
|*lpszText*|de Puntero a una cadena Unicode que contiene el texto de globo de sugerencias.|
|*ttiIcon*|de Valor **int** que especifica el tipo de icono que se va a asociar al globo de sugerencias. El valor predeterminado es TTI_NONE. Para obtener más información, vea el `ttiIcon` miembro de la estructura [EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip) .|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Esta función envía el mensaje de [EM_SHOWBALLOONTIP](/windows/win32/Controls/em-showballoontip) , que se describe en el Windows SDK. Para obtener más información, vea la macro [Edit_ShowBalloonTip](/windows/win32/api/commctrl/nf-commctrl-edit_showballoontip) .

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define una variable, `m_cedit`, que se utiliza para tener acceso al control de edición actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra un globo de sugerencias para un control de edición. El método [CEDIT:: ShowBalloonTip](#showballoontip) especifica un título y un texto de sugerencia.

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

##  <a name="undo"></a>CEdit:: Undo

Llame a esta función para deshacer la última operación de edición del control.

```
BOOL Undo();
```

### <a name="return-value"></a>Valor devuelto

Para un control de edición de una sola línea, el valor devuelto siempre es distinto de cero. Para un control de edición de varias líneas, el valor devuelto es distinto de cero si la operación de deshacer se realiza correctamente, o 0 si se produce un error en la operación de deshacer.

### <a name="remarks"></a>Observaciones

También se puede deshacer una operación de deshacer. Por ejemplo, puede restaurar el texto eliminado con la primera llamada a `Undo`. Siempre que no haya ninguna operación de edición que intervenga, puede volver a quitar el texto con una segunda llamada a `Undo`.

Para obtener más información, vea [EM_UNDO](/windows/win32/Controls/em-undo) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](cwnd-class.md)<br/>
[CButton (clase)](cbutton-class.md)<br/>
[CComboBox (clase)](ccombobox-class.md)<br/>
[CListBox (clase)](clistbox-class.md)<br/>
[CScrollBar (clase)](cscrollbar-class.md)<br/>
[CStatic (clase)](cstatic-class.md)<br/>
[CDialog (clase)](cdialog-class.md)
