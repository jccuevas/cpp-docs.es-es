---
title: CButton (clase)
ms.date: 11/04/2016
f1_keywords:
- CButton
- AFXWIN/CButton
- AFXWIN/CButton::CButton
- AFXWIN/CButton::Create
- AFXWIN/CButton::DrawItem
- AFXWIN/CButton::GetBitmap
- AFXWIN/CButton::GetButtonStyle
- AFXWIN/CButton::GetCheck
- AFXWIN/CButton::GetCursor
- AFXWIN/CButton::GetIcon
- AFXWIN/CButton::GetIdealSize
- AFXWIN/CButton::GetImageList
- AFXWIN/CButton::GetNote
- AFXWIN/CButton::GetNoteLength
- AFXWIN/CButton::GetSplitGlyph
- AFXWIN/CButton::GetSplitImageList
- AFXWIN/CButton::GetSplitInfo
- AFXWIN/CButton::GetSplitSize
- AFXWIN/CButton::GetSplitStyle
- AFXWIN/CButton::GetState
- AFXWIN/CButton::GetTextMargin
- AFXWIN/CButton::SetBitmap
- AFXWIN/CButton::SetButtonStyle
- AFXWIN/CButton::SetCheck
- AFXWIN/CButton::SetCursor
- AFXWIN/CButton::SetDropDownState
- AFXWIN/CButton::SetIcon
- AFXWIN/CButton::SetImageList
- AFXWIN/CButton::SetNote
- AFXWIN/CButton::SetSplitGlyph
- AFXWIN/CButton::SetSplitImageList
- AFXWIN/CButton::SetSplitInfo
- AFXWIN/CButton::SetSplitSize
- AFXWIN/CButton::SetSplitStyle
- AFXWIN/CButton::SetState
- AFXWIN/CButton::SetTextMargin
helpviewer_keywords:
- CButton [MFC], CButton
- CButton [MFC], Create
- CButton [MFC], DrawItem
- CButton [MFC], GetBitmap
- CButton [MFC], GetButtonStyle
- CButton [MFC], GetCheck
- CButton [MFC], GetCursor
- CButton [MFC], GetIcon
- CButton [MFC], GetIdealSize
- CButton [MFC], GetImageList
- CButton [MFC], GetNote
- CButton [MFC], GetNoteLength
- CButton [MFC], GetSplitGlyph
- CButton [MFC], GetSplitImageList
- CButton [MFC], GetSplitInfo
- CButton [MFC], GetSplitSize
- CButton [MFC], GetSplitStyle
- CButton [MFC], GetState
- CButton [MFC], GetTextMargin
- CButton [MFC], SetBitmap
- CButton [MFC], SetButtonStyle
- CButton [MFC], SetCheck
- CButton [MFC], SetCursor
- CButton [MFC], SetDropDownState
- CButton [MFC], SetIcon
- CButton [MFC], SetImageList
- CButton [MFC], SetNote
- CButton [MFC], SetSplitGlyph
- CButton [MFC], SetSplitImageList
- CButton [MFC], SetSplitInfo
- CButton [MFC], SetSplitSize
- CButton [MFC], SetSplitStyle
- CButton [MFC], SetState
- CButton [MFC], SetTextMargin
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
ms.openlocfilehash: 669bdb18e378c4dc39bdc6d51ca1ebe7f93fa839
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78870617"
---
# <a name="cbutton-class"></a>CButton (clase)

Proporciona la funcionalidad de los controles de botón de Windows.

## <a name="syntax"></a>Sintaxis

```
class CButton : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CButton:: CButton](#cbutton)|Construye un objeto `CButton`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CButton:: Create](#create)|Crea el control botón de Windows y lo adjunta al objeto `CButton`.|
|[CButton::D rawItem](#drawitem)|Invalide para dibujar un objeto de `CButton` dibujado por el propietario.|
|[CButton:: GetBitmap](#getbitmap)|Recupera el identificador del mapa de bits previamente establecido con [SetBitmap](#setbitmap).|
|[CButton:: GetButtonStyle](#getbuttonstyle)|Recupera información sobre el estilo de control Button.|
|[CButton:: GetCheck](#getcheck)|Recupera el estado de comprobación de un control de botón.|
|[CButton:: GetCursor](#getcursor)|Recupera el identificador de la imagen de cursor previamente establecida con [setCursor](#setcursor).|
|[CButton:: GetIcon](#geticon)|Recupera el identificador del icono establecido previamente con [SetIcon](#seticon).|
|[CButton:: GetIdealSize](#getidealsize)|Recupera el tamaño ideal del control de botón.|
|[CButton:: GetImageList](#getimagelist)|Recupera la lista de imágenes del control de botón.|
|[CButton:: GetNote](#getnote)|Recupera el componente de nota del control de vínculo de comando actual.|
|[CButton:: GetNoteLength](#getnotelength)|Recupera la longitud del texto de la nota para el control de vínculo de comando actual.|
|[CButton:: GetSplitGlyph](#getsplitglyph)|Recupera el glifo asociado al control de botón de expansión actual.|
|[CButton:: GetSplitImageList](#getsplitimagelist)|Recupera la lista de imágenes del control de botón de expansión actual.|
|[CButton:: GetSplitInfo](#getsplitinfo)|Recupera información que define el control de botón de expansión actual.|
|[CButton:: GetSplitSize](#getsplitsize)|Recupera el rectángulo delimitador del componente desplegable del control de botón de expansión actual.|
|[CButton:: GetSplitStyle](#getsplitstyle)|Recupera los estilos de botón de expansión que definen el control de botón de expansión actual.|
|[CButton:: GetState](#getstate)|Recupera el estado de activación, el estado de resaltado y el estado de foco de un control de botón.|
|[CButton:: GetTextMargin](#gettextmargin)|Recupera el margen del texto del control de botón.|
|[CButton:: SetBitmap](#setbitmap)|Especifica un mapa de bits que se va a mostrar en el botón.|
|[CButton:: SetButtonStyle](#setbuttonstyle)|Cambia el estilo de un botón.|
|[CButton:: SetCheck](#setcheck)|Establece el estado de comprobación de un control de botón.|
|[CButton:: SetCursor](#setcursor)|Especifica una imagen de cursor que se va a mostrar en el botón.|
|[CButton:: SetDropDownState](#setdropdownstate)|Establece el estado desplegable del control de botón de expansión actual.|
|[CButton:: SetIcon](#seticon)|Especifica el icono que se va a mostrar en el botón.|
|[CButton:: SetImageList](#setimagelist)|Establece la lista de imágenes del control de botón.|
|[CButton:: SetNote](#setnote)|Establece la nota en el control de vínculo de comando actual.|
|[CButton:: SetSplitGlyph](#setsplitglyph)|Asocia un glifo especificado al control de botón de expansión actual.|
|[CButton:: SetSplitImageList](#setsplitimagelist)|Asocia una lista de imágenes al control de botón de expansión actual.|
|[CButton:: SetSplitInfo](#setsplitinfo)|Especifica la información que define el control de botón de expansión actual.|
|[CButton:: SetSplitSize](#setsplitsize)|Establece el rectángulo delimitador del componente desplegable del control de botón de expansión actual.|
|[CButton:: SetSplitStyle](#setsplitstyle)|Establece el estilo del control de botón de expansión actual.|
|[CButton:: SetState](#setstate)|Establece el estado de resaltado de un control de botón.|
|[CButton:: SetTextMargin](#settextmargin)|Establece el margen del texto del control de botón.|

## <a name="remarks"></a>Comentarios

Un control de botón es una pequeña ventana secundaria rectangular en la que se puede hacer clic y desactivarla. Los botones se pueden usar solos o en grupos y se pueden etiquetar o mostrar sin texto. Un botón suele cambiar de apariencia cuando el usuario hace clic en él.

Los botones típicos son la casilla, el botón de radio y el botón de control. Un objeto `CButton` puede convertirse en cualquiera de ellos, según el [estilo de botón](../../mfc/reference/styles-used-by-mfc.md#button-styles) especificado en su inicialización por la función miembro [Create](#create) .

Además, la clase [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) derivada de `CButton` admite la creación de controles de botón etiquetados con imágenes de mapa de bits en lugar de texto. Un `CBitmapButton` puede tener mapas de bits independientes para los Estados activo, inactivo, centrado y deshabilitado de un botón.

Puede crear un control de botón desde una plantilla de cuadro de diálogo o directamente en el código. En ambos casos, llame primero al constructor `CButton` para construir el objeto `CButton`; a continuación, llame a la función miembro `Create` para crear el control botón de Windows y adjuntarlo al objeto `CButton`.

La construcción puede ser un proceso de un solo paso en una clase derivada de `CButton`. Escriba un constructor para la clase derivada y llame a `Create` desde dentro del constructor.

Si desea controlar los mensajes de notificación de Windows enviados por un control de botón a su elemento primario (normalmente una clase derivada de [CDialog](../../mfc/reference/cdialog-class.md)), agregue una entrada de mapa de mensajes y una función miembro de controlador de mensajes a la clase primaria para cada mensaje.

Cada entrada de mapa de mensajes tiene el siguiente formato:

**En\_** _notificación_ **(** _ID._ , _memberFxn_ **)**

donde *ID* especifica el identificador de la ventana secundaria del control que envía la notificación y *memberFxn* es el nombre de la función miembro primaria que ha escrito para controlar la notificación.

El prototipo de función del elemento primario es el siguiente:

`afx_msg void memberFxn();`

Las posibles entradas de mapa de mensajes son las siguientes:

|Entrada de asignación|Enviado a primario cuando...|
|---------------|----------------------------|
|ON_BN_CLICKED|El usuario hace clic en un botón.|
|ON_BN_DOUBLECLICKED|El usuario hace doble clic en un botón.|

Si crea un objeto de `CButton` a partir de un recurso de cuadro de diálogo, el objeto de `CButton` se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.

Si crea un objeto de `CButton` dentro de una ventana, puede que tenga que destruirlo. Si crea el objeto de `CButton` en el montón mediante la **nueva** función, debe llamar a **Delete** en el objeto para destruirlo cuando el usuario cierre el control botón de Windows. Si crea el objeto de `CButton` en la pila o se incrusta en el objeto de cuadro de diálogo primario, se destruye automáticamente.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cbutton"></a>CButton:: CButton

Construye un objeto `CButton`.

```
CButton();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

##  <a name="create"></a>CButton:: Create

Crea el control botón de Windows y lo adjunta al objeto `CButton`.

```
virtual BOOL Create(
    LPCTSTR lpszCaption,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*lpszCaption*<br/>
Especifica el texto del control de botón.

*dwStyle*<br/>
Especifica el estilo del control de botón. Aplique cualquier combinación de [estilos de botón](../../mfc/reference/styles-used-by-mfc.md#button-styles) al botón.

*Rect*<br/>
Especifica el tamaño y la posición del control de botón. Puede ser un objeto `CRect` o una estructura `RECT`.

*pParentWnd*<br/>
Especifica la ventana primaria del control de botón, normalmente una `CDialog`. No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de botón.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Cree un objeto de `CButton` en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a `Create`, que crea el control de botón de Windows y lo adjunta al objeto `CButton`.

Si se proporciona el estilo de WS_VISIBLE, Windows envía al control de botón todos los mensajes necesarios para activar y mostrar el botón.

Aplique los siguientes [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) a un control de botón:

- WS_CHILD siempre

- WS_VISIBLE normalmente

- WS_DISABLED raramente

- WS_GROUP a controles de grupo

- WS_TABSTOP para incluir el botón en el orden de tabulación

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

##  <a name="drawitem"></a>CButton::D rawItem

Lo llama el marco de trabajo cuando ha cambiado un aspecto visual de un botón dibujado por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Puntero largo a una estructura [drawitemstruct (](/windows/win32/api/winuser/ns-winuser-drawitemstruct) . La estructura contiene información sobre el elemento que se va a dibujar y el tipo de dibujo necesario.

### <a name="remarks"></a>Comentarios

Un botón dibujado por el propietario tiene el conjunto de estilos BS_OWNERDRAW. Invalide esta función miembro para implementar el dibujo de un objeto de `CButton` dibujado por el propietario. La aplicación debe restaurar todos los objetos de la interfaz de dispositivo gráfico (GDI) seleccionados para el contexto de presentación proporcionado en *lpDrawItemStruct* antes de que finalice la función miembro.

Vea también los valores de estilo [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

##  <a name="getbitmap"></a>CButton:: GetBitmap

Llame a esta función miembro para obtener el identificador de un mapa de bits, previamente establecido con [SetBitmap](#setbitmap), que está asociado a un botón.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador de un mapa de bits. Es NULL si no se ha especificado ningún mapa de bits previamente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

##  <a name="getbuttonstyle"></a>CButton:: GetButtonStyle

Recupera información sobre el estilo de control Button.

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve los estilos de botón para este objeto `CButton`. Esta función devuelve solo los valores de estilo [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) , no los de los demás estilos de ventana.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

##  <a name="getcheck"></a>CButton:: GetCheck

Recupera el estado de activación de un botón de radio o casilla.

```
int GetCheck() const;
```

### <a name="return-value"></a>Valor devuelto

El valor devuelto de un control de botón creado con el estilo BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON o BS_3STATE es uno de los valores siguientes:

|Valor|Significado|
|-----------|-------------|
|BST_UNCHECKED|El estado del botón es desactivado.|
|BST_CHECKED|El estado del botón está activado.|
|BST_INDETERMINATE|El estado del botón es indeterminado (solo se aplica si el botón tiene el estilo BS_3STATE o BS_AUTO3STATE).|

Si el botón tiene cualquier otro estilo, el valor devuelto es BST_UNCHECKED.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

##  <a name="getcursor"></a>CButton:: GetCursor

Llame a esta función miembro para obtener el identificador de un cursor, previamente establecido con [setCursor](#setcursor), que está asociado a un botón.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Valor devuelto

Identificador de una imagen de cursor. Es NULL si no se ha especificado ningún cursor previamente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

##  <a name="geticon"></a>CButton:: GetIcon

Llame a esta función miembro para obtener el identificador de un icono, previamente establecido con [SetIcon](#seticon), que está asociado a un botón.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador de un icono. Es NULL si no se ha especificado previamente ningún icono.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

##  <a name="getidealsize"></a>CButton:: GetIdealSize

Recupera el tamaño ideal para el control de botón.

```
BOOL GetIdealSize(SIZE* psize);
```

### <a name="parameters"></a>Parámetros

*psize*<br/>
Puntero al tamaño actual del botón.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad del mensaje de BCM_GETIDEALSIZE, como se describe en la sección [botones](/windows/win32/controls/buttons) del Windows SDK.

##  <a name="getimagelist"></a>CButton:: GetImageList

Llame a este método para obtener la lista de imágenes del control de botón.

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parámetros

*pbuttonImagelist*<br/>
Puntero a la lista de imágenes del objeto `CButton`.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad del mensaje de BCM_GETIMAGELIST, como se describe en la sección [botones](/windows/win32/controls/buttons) del Windows SDK.

##  <a name="getnote"></a>CButton:: GetNote

Recupera el texto de la nota asociado al control de vínculo de comando actual.

```
CString GetNote() const;

BOOL GetNote(
    LPTSTR lpszNote,
    UINT* cchNote) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*lpszNote*|enuncia Puntero a un búfer, que el llamador es responsable de la asignación y desasignación. Si el valor devuelto es TRUE, el búfer contiene el texto de la nota que está asociado al control de vínculo de comando actual. de lo contrario, el búfer no se modifica.|
|*cchNote*|[in, out] Puntero a una variable de entero sin signo.<br /><br /> Cuando se llama a este método, la variable contiene el tamaño del búfer especificado por el parámetro *lpszNote* .<br /><br /> Cuando este método devuelve un resultado, si el valor devuelto es TRUE, la variable contiene el tamaño de la nota asociada al control de vínculo de comando actual. Si el valor devuelto es FALSE, la variable contiene el tamaño de búfer necesario para contener la nota.|

### <a name="return-value"></a>Valor devuelto

En la primera sobrecarga, objeto [CString](../../atl-mfc-shared/using-cstring.md) que contiene el texto de la nota asociado al control de vínculo de comando actual.

O bien,

En la segunda sobrecarga, es TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use este método solo con controles cuyo estilo de botón sea BS_COMMANDLINK o BS_DEFCOMMANDLINK.

Este método envía el mensaje de [BCM_GETNOTE](/windows/win32/Controls/bcm-getnote) , que se describe en el Windows SDK.

##  <a name="getnotelength"></a>CButton:: GetNoteLength

Recupera la longitud del texto de la nota para el control de vínculo de comando actual.

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>Valor devuelto

Longitud del texto de la nota, en caracteres Unicode de 16 bits, para el control de vínculo de comando actual.

### <a name="remarks"></a>Comentarios

Use este método solo con controles cuyo estilo de botón sea BS_COMMANDLINK o BS_DEFCOMMANDLINK.

Este método envía el mensaje de [BCM_GETNOTELENGTH](/windows/win32/Controls/bcm-getnotelength) , que se describe en el Windows SDK.

##  <a name="getsplitglyph"></a>CButton:: GetSplitGlyph

Recupera el glifo asociado al control de botón de expansión actual.

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>Valor devuelto

Carácter de glifo asociado al control de botón de expansión actual.

### <a name="remarks"></a>Comentarios

Un glifo es la representación física de un carácter en una fuente determinada. Por ejemplo, un control de botón de expansión podría estar decorado con el glifo del carácter de marca de verificación Unicode (U + 2713).

Use este método solo con controles cuyo estilo de botón sea BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Este método inicializa el miembro de `mask` de una estructura de [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) con la marca BCSIF_GLYPH y, a continuación, envía esa estructura en el mensaje de [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) que se describe en el Windows SDK. Cuando la función de mensaje devuelve, este método recupera el glifo del miembro de `himlGlyph` de la estructura.

##  <a name="getsplitimagelist"></a>CButton:: GetSplitImageList

Recupera la [lista de imágenes](../../mfc/reference/cimagelist-class.md) del control de botón de expansión actual.

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [CImageList](../../mfc/reference/cimagelist-class.md) .

### <a name="remarks"></a>Comentarios

Use este método solo con controles cuyo estilo de botón sea BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Este método inicializa el miembro de `mask` de una estructura de [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) con la marca BCSIF_IMAGE y, a continuación, envía esa estructura en el mensaje de [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) que se describe en el Windows SDK. Cuando la función de mensaje devuelve, este método recupera la lista de imágenes del miembro de `himlGlyph` de la estructura.

##  <a name="getsplitinfo"></a>CButton:: GetSplitInfo

Recupera parámetros que determinan cómo Windows dibuja el control de botón de expansión actual.

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pInfo*|enuncia Puntero a una estructura de [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) que recibe información sobre el control de botón de expansión actual. El autor de la llamada es responsable de la asignación de la estructura.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use este método solo con controles cuyo estilo de botón sea BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Este método envía el mensaje de [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) , que se describe en el Windows SDK.

##  <a name="getsplitsize"></a>CButton:: GetSplitSize

Recupera el rectángulo delimitador del componente desplegable del control de botón de expansión actual.

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pSize*|enuncia Puntero a una estructura de [tamaño](/windows/win32/api/windef/ns-windef-size) que recibe la descripción de un rectángulo.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use este método solo con controles cuyo estilo de botón sea BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Cuando se expande el control de botón de expansión, puede mostrar un componente desplegable, como un control de lista o un control de paginación. Este método recupera el rectángulo delimitador que contiene el componente desplegable.

Este método inicializa el miembro de `mask` de una estructura de [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) con la marca BCSIF_SIZE y, a continuación, envía esa estructura en el mensaje de [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) que se describe en el Windows SDK. Cuando la función de mensaje devuelve, este método recupera el rectángulo delimitador del miembro de `size` de la estructura.

##  <a name="getsplitstyle"></a>CButton:: GetSplitStyle

Recupera los estilos de botón de expansión que definen el control de botón de expansión actual.

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>Valor devuelto

Combinación bit a bit de estilos de botón de expansión. Para obtener más información, vea el `uSplitStyle` miembro de la estructura [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) .

### <a name="remarks"></a>Comentarios

Use este método solo con controles cuyo estilo de botón sea BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Los estilos del botón de expansión especifican la alineación, la relación de aspecto y el formato gráfico con el que Windows dibuja un icono de botón de expansión.

Este método inicializa el miembro de `mask` de una estructura de [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) con la marca BCSIF_STYLE y, a continuación, envía esa estructura en el mensaje de [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) que se describe en el Windows SDK. Cuando se devuelve la función Message, este método recupera los estilos de botón de expansión del miembro `uSplitStyle` de la estructura.

##  <a name="getstate"></a>CButton:: GetState

Recupera el estado de un control de botón.

```
UINT GetState() const;
```

### <a name="return-value"></a>Valor devuelto

Campo de bits que contiene la combinación de valores que indican el estado actual de un control de botón. En la tabla siguiente se enumeran los valores posibles.

|Estado del botón|Valor|Descripción|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|Estado inicial.|
|BST_CHECKED|0x0001|El control de botón está activado.|
|BST_INDETERMINATE|0x0002|El estado es indeterminado (solo es posible cuando el control de botón tiene tres Estados).|
|BST_PUSHED|0x0004|Se presiona el control de botón.|
|BST_FOCUS|0x0008|El control de botón tiene el foco.|

### <a name="remarks"></a>Comentarios

Un control de botón con el estilo de botón BS_3STATE o BS_AUTO3STATE crea una casilla que tiene un tercer estado denominado estado indeterminado. El estado indeterminado indica que la casilla no está activada ni desactivada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

##  <a name="gettextmargin"></a>CButton:: GetTextMargin

Llame a este método para obtener el margen de texto del objeto `CButton`.

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parámetros

*pmargin*<br/>
Puntero al margen del texto del objeto de `CButton`.

### <a name="return-value"></a>Valor devuelto

Devuelve el margen del texto.

### <a name="remarks"></a>Comentarios

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad del mensaje de BCM_GETTEXTMARGIN, como se describe en la sección [botones](/windows/win32/controls/buttons) del Windows SDK.

##  <a name="setbitmap"></a>CButton:: SetBitmap

Llame a esta función miembro para asociar un nuevo mapa de bits al botón.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parámetros

*hBitmap*<br/>
Identificador de un mapa de bits.

### <a name="return-value"></a>Valor devuelto

Identificador de un mapa de bits asociado previamente al botón.

### <a name="remarks"></a>Comentarios

El mapa de bits se colocará automáticamente en la superficie del botón, centrada de forma predeterminada. Si el mapa de bits es demasiado grande para el botón, se recortará en cualquier lado. Puede elegir otras opciones de alineación, entre las que se incluyen las siguientes:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

A diferencia de [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), que usa cuatro mapas de bits por botón, `SetBitmap` solo usa un mapa de bits por cada botón. Cuando se presiona el botón, el mapa de bits parece desplazarse hacia abajo y hacia la derecha.

Usted es responsable de liberar el mapa de bits cuando termine de usarlo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

##  <a name="setbuttonstyle"></a>CButton:: SetButtonStyle

Cambia el estilo de un botón.

```
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parámetros

*nStyle*<br/>
Especifica el [estilo del botón](../../mfc/reference/styles-used-by-mfc.md#button-styles).

*bRedraw*<br/>
Especifica si se debe volver a dibujar el botón. Un valor distinto de cero vuelve A dibujar el botón. Un valor 0 no vuelve A dibujar el botón. De forma predeterminada, se vuelve a dibujar el botón.

### <a name="remarks"></a>Comentarios

Utilice la función miembro `GetButtonStyle` para recuperar el estilo del botón. La palabra de orden inferior del estilo de botón completo es el estilo específico del botón.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

##  <a name="setcheck"></a>CButton:: SetCheck

Establece o restablece el estado de activación de un botón o casilla de radio.

```
void SetCheck(int nCheck);
```

### <a name="parameters"></a>Parámetros

*nCompruebe*<br/>
Especifica el estado de comprobación. Este parámetro puede ser uno de los siguientes:

|Valor|Significado|
|-----------|-------------|
|BST_UNCHECKED|Establezca el estado del botón en desactivado.|
|BST_CHECKED|Establezca el estado del botón en activado.|
|BST_INDETERMINATE|Establezca el estado de botón en indeterminado. Este valor solo se puede usar si el botón tiene el estilo BS_3STATE o BS_AUTO3STATE.|

### <a name="remarks"></a>Comentarios

Esta función miembro no tiene ningún efecto en un pulsador.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

##  <a name="setcursor"></a>CButton:: SetCursor

Llame a esta función miembro para asociar un nuevo cursor al botón.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parámetros

*hCursor*<br/>
Identificador de un cursor.

### <a name="return-value"></a>Valor devuelto

Identificador de un cursor asociado previamente al botón.

### <a name="remarks"></a>Comentarios

El cursor se colocará automáticamente en la superficie del botón, centrada de forma predeterminada. Si el cursor es demasiado grande para el botón, se recortará en cualquier lado. Puede elegir otras opciones de alineación, entre las que se incluyen las siguientes:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

A diferencia de [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), que usa cuatro mapas de bits por botón, `SetCursor` solo usa un cursor por cada botón. Cuando se presiona el botón, el cursor parece desplazarse hacia abajo y hacia la derecha.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

##  <a name="setdropdownstate"></a>CButton:: SetDropDownState

Establece el estado desplegable del control de botón de expansión actual.

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*fDropDown*|de TRUE para establecer el estado de BST_DROPDOWNPUSHED; en caso contrario, FALSE.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Un control de botón de expansión tiene un estilo de BS_SPLITBUTTON o BS_DEFSPLITBUTTON y consta de un botón y una flecha desplegable a su derecha. Para obtener más información, consulte [estilos de botón](/windows/win32/Controls/button-styles). Normalmente, el estado desplegable se establece cuando el usuario hace clic en la flecha de lista desplegable. Use este método para establecer mediante programación el estado de la lista desplegable del control. La flecha desplegable se dibuja sombreada para indicar el estado.

Este método envía el mensaje de [BCM_SETDROPDOWNSTATE](/windows/win32/Controls/bcm-setdropdownstate) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define la variable, *m_splitButton*, que se usa para tener acceso mediante programación al control de botón de expansión. Esta variable se usa en el ejemplo siguiente.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece el estado del control de botón de expansión para indicar que se ha insertado la flecha de lista desplegable.

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

##  <a name="setelevationrequired"></a>CButton:: SetElevationRequired

Establece el estado del control de botón actual en `elevation required`, que es necesario para que el control muestre un icono de seguridad elevado.

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*fElevationRequired*|de TRUE para establecer el estado de `elevation required`; en caso contrario, FALSE.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Si un control de botón o vínculo de comando requiere permisos de seguridad elevados para realizar una acción, establezca el control en `elevation required` estado. Posteriormente, Windows muestra el icono de escudo de control de cuentas de usuario (UAC) en el control. Para obtener más información, vea "control de cuentas de usuario" en [MSDN](https://go.microsoft.com/fwlink/p/?linkid=18507).

Este método envía el mensaje de [BCM_SETSHIELD](/windows/win32/Controls/bcm-setshield) , que se describe en el Windows SDK.

##  <a name="seticon"></a>CButton:: SetIcon

Llame a esta función miembro para asociar un icono nuevo al botón.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parámetros

*hIcon*<br/>
Identificador de un icono.

### <a name="return-value"></a>Valor devuelto

Identificador de un icono asociado previamente al botón.

### <a name="remarks"></a>Comentarios

El icono se colocará automáticamente en la superficie del botón, centrada de forma predeterminada. Si el icono es demasiado grande para el botón, se recortará en cualquier lado. Puede elegir otras opciones de alineación, entre las que se incluyen las siguientes:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

A diferencia de [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), que usa cuatro mapas de bits por botón, `SetIcon` solo usa un icono por el botón. Cuando se presiona el botón, el icono parece desplazarse hacia abajo y hacia la derecha.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

##  <a name="setimagelist"></a>CButton:: SetImageList

Llame a este método para establecer la lista de imágenes del objeto `CButton`.

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parámetros

*pbuttonImagelist*<br/>
Puntero a la nueva lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad del mensaje de BCM_SETIMAGELIST, como se describe en la sección [botones](/windows/win32/controls/buttons) del Windows SDK.

##  <a name="setnote"></a>CButton:: SetNote

Establece el texto de la nota para el control de vínculo de comando actual.

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*lpszNote*|de Puntero a una cadena Unicode que se establece como texto de la nota para el control de vínculo de comando.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use este método solo con controles cuyo estilo de botón sea BS_COMMANDLINK o BS_DEFCOMMANDLINK.

Este método envía el mensaje de [BCM_SETNOTE](/windows/win32/Controls/bcm-setnote) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define la variable, *m_cmdLink*, que se usa para tener acceso mediante programación al control de vínculo de comando. Esta variable se usa en el ejemplo siguiente.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece el texto de la nota para el control de vínculo de comando.

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

##  <a name="setsplitglyph"></a>CButton:: SetSplitGlyph

Asocia un glifo especificado al control de botón de expansión actual.

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*chGlyph*|de Carácter que especifica el glifo que se va a usar como flecha de cuadro desplegable del botón de expansión.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use este método solo con controles que tengan el estilo de botón BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Un glifo es la representación física de un carácter en una fuente determinada. El parámetro *chGlyph* no se utiliza como glifo, sino que se usa para seleccionar un glifo de un conjunto de glifos definidos por el sistema. El glifo de la flecha de lista desplegable predeterminada se especifica mediante un carácter ' 6 ' y se asemeja al triángulo que apunta hacia abajo del carácter Unicode (U + 25BC).

Este método inicializa el miembro de `mask` de una estructura de [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) con la marca BCSIF_GLYPH y el miembro `himlGlyph` con el parámetro *chGlyph* y, a continuación, envía esa estructura en el mensaje [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) que se describe en el Windows SDK.

##  <a name="setsplitimagelist"></a>CButton:: SetSplitImageList

Asocia una [lista de imágenes](../../mfc/reference/cimagelist-class.md) al control de botón de expansión actual.

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pSplitImageList*|de Puntero a un objeto [CImageList](../../mfc/reference/cimagelist-class.md) que se va a asignar al control de botón de expansión actual.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use este método solo con controles cuyo estilo de botón sea BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Este método inicializa el miembro de `mask` de una estructura de [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) con la marca BCSIF_IMAGE y el miembro `himlGlyph` con el parámetro *pSplitImageList* y, a continuación, envía esa estructura en el mensaje [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) que se describe en el Windows SDK.

##  <a name="setsplitinfo"></a>CButton:: SetSplitInfo

Especifica los parámetros que determinan cómo Windows dibuja el control de botón de expansión actual.

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pInfo*|de Puntero a una estructura de [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) que define el control de botón de expansión actual.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use este método solo con controles cuyo estilo de botón sea BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Este método envía el mensaje de [BCM_SETSPLITINFO](/windows/win32/Controls/bcm-setsplitinfo) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define la variable, `m_splitButton`, que se usa para tener acceso mediante programación al control de botón de expansión.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se cambia el glifo que se usa para la flecha desplegable del botón de expansión. En el ejemplo se sustituye un glifo de triángulo hacia arriba por el glifo de triángulo que apunta hacia abajo predeterminado. El glifo que se muestra depende del carácter que se especifique en el `himlGlyph` miembro de la estructura de `BUTTON_SPLITINFO`. El glifo de triángulo que apunta hacia abajo se especifica mediante un carácter ' 6 ' y el glifo de triángulo hacia arriba se especifica mediante un carácter ' 5 '. Para realizar una comparación, vea el método conveniente, [CButton:: SetSplitGlyph](#setsplitglyph).

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

##  <a name="setsplitsize"></a>CButton:: SetSplitSize

Establece el rectángulo delimitador del componente desplegable del control de botón de expansión actual.

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pSize*|de Puntero a una estructura de [tamaño](/windows/win32/api/windef/ns-windef-size) que describe un rectángulo delimitador.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use este método solo con controles cuyo estilo de botón sea BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Cuando se expande el control de botón de expansión, puede mostrar un componente desplegable, como un control de lista o un control de paginación. Este método especifica el tamaño del rectángulo delimitador que contiene el componente desplegable.

Este método inicializa el miembro de `mask` de una estructura de [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) con la marca BCSIF_SIZE y el miembro `size` con el parámetro *pSize* y, a continuación, envía esa estructura en el mensaje [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define la variable, `m_splitButton`, que se usa para tener acceso mediante programación al control de botón de expansión. Esta variable se usa en el ejemplo siguiente.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se duplica el tamaño de la flecha desplegable del botón de expansión.

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

##  <a name="setsplitstyle"></a>CButton:: SetSplitStyle

Establece el estilo del control de botón de expansión actual.

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*uSplitStyle*|de Combinación bit a bit de estilos de botón de expansión. Para obtener más información, vea el `uSplitStyle` miembro de la estructura [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) .|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use este método solo con controles cuyo estilo de botón sea BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Los estilos del botón de expansión especifican la alineación, la relación de aspecto y el formato gráfico con el que Windows dibuja un icono de botón de expansión. Para obtener más información, vea el `uSplitStyle` miembro de la estructura [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) .

Este método inicializa el miembro de `mask` de una estructura de [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) con la marca BCSIF_STYLE y el miembro `uSplitStyle` con el parámetro *uSplitStyle* y, a continuación, envía esa estructura en el mensaje [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define la variable, `m_splitButton`, que se usa para tener acceso mediante programación al control de botón de expansión.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece el estilo de la flecha de cuadro desplegable del botón de expansión. El estilo de BCSS_ALIGNLEFT muestra la flecha en el lado izquierdo del botón y el estilo de BCSS_STRETCH conserva las proporciones de la flecha de lista desplegable al cambiar el tamaño del botón.

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

##  <a name="setstate"></a>CButton:: SetState

Establece si un control de botón está resaltado o no.

```
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>Parámetros

*bHighlight*<br/>
Especifica si el botón se va a resaltar. Un valor distinto de cero resalta el botón; un valor 0 quita cualquier resaltado.

### <a name="remarks"></a>Comentarios

El resaltado afecta al exterior de un control de botón. No tiene ningún efecto en el estado de activación de un botón de radio o casilla.

Un control de botón se resalta automáticamente cuando el usuario hace clic y mantiene presionado el botón primario del mouse. El resaltado se quita cuando el usuario suelta el botón del mouse.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

##  <a name="settextmargin"></a>CButton:: SetTextMargin

Llame a este método para establecer el margen de texto del objeto de `CButton`.

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parámetros

*pmargin*<br/>
Puntero al nuevo margen del texto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad del mensaje de BCM_SETTEXTMARGIN, como se describe en la sección [botones](/windows/win32/controls/buttons) del Windows SDK.

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CComboBox (clase)](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox (clase)](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar (clase)](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic (clase)](../../mfc/reference/cstatic-class.md)<br/>
[CBitmapButton (clase)](../../mfc/reference/cbitmapbutton-class.md)<br/>
[CDialog (clase)](../../mfc/reference/cdialog-class.md)
