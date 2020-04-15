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
ms.openlocfilehash: 05ad60855cd03115cf88ab2b51e56e6a26822035
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352444"
---
# <a name="cbutton-class"></a>CButton (clase)

Proporciona la funcionalidad de los controles de botón de Windows.

## <a name="syntax"></a>Sintaxis

```
class CButton : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CButton::CButton](#cbutton)|Construye un objeto `CButton`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CButton::Crear](#create)|Crea el control de botón `CButton` de Windows y lo adjunta al objeto.|
|[CButton::DrawItem](#drawitem)|Reemplazar para dibujar un `CButton` objeto dibujado por el propietario.|
|[CButton::GetBitmap](#getbitmap)|Recupera el identificador del mapa de bits establecido anteriormente con [SetBitmap](#setbitmap).|
|[CButton::GetButtonStyle](#getbuttonstyle)|Recupera información sobre el estilo de control de botón.|
|[CButton::GetCheck](#getcheck)|Recupera el estado de comprobación de un control de botón.|
|[CButton::GetCursor](#getcursor)|Recupera el identificador de la imagen del cursor previamente establecida con [SetCursor](#setcursor).|
|[CButton::GetIcon](#geticon)|Recupera el identificador del icono establecido previamente con [SetIcon](#seticon).|
|[CButton::GetIdealSize](#getidealsize)|Recupera el tamaño ideal del control de botón.|
|[CButton::GetImageList](#getimagelist)|Recupera la lista de imágenes del control de botón.|
|[CButton::GetNote](#getnote)|Recupera el componente de nota del control de vínculo de comando actual.|
|[CButton::GetNoteLength](#getnotelength)|Recupera la longitud del texto de la nota para el control de vínculo de comando actual.|
|[CButton::GetSplitGlyph](#getsplitglyph)|Recupera el glifo asociado con el control de botón de división actual.|
|[CButton::GetSplitImageList](#getsplitimagelist)|Recupera la lista de imágenes para el control de botón de división actual.|
|[CButton::GetSplitInfo](#getsplitinfo)|Recupera información que define el control de botón de división actual.|
|[CButton::GetSplitSize](#getsplitsize)|Recupera el rectángulo delimitador del componente desplegable del control de botón de división actual.|
|[CButton::GetSplitStyle](#getsplitstyle)|Recupera los estilos de botón de división que definen el control de botón de división actual.|
|[CButton::GetState](#getstate)|Recupera el estado de comprobación, el estado de resaltado y el estado de foco de un control de botón.|
|[CButton::GetTextMargin](#gettextmargin)|Recupera el margen de texto del control de botón.|
|[CButton::SetBitmap](#setbitmap)|Especifica un mapa de bits que se mostrará en el botón.|
|[CButton::SetButtonStyle](#setbuttonstyle)|Cambia el estilo de un botón.|
|[CButton::SetCheck](#setcheck)|Establece el estado de comprobación de un control de botón.|
|[CButton::SetCursor](#setcursor)|Especifica una imagen de cursor que se mostrará en el botón.|
|[CButton::SetDropDownState](#setdropdownstate)|Establece el estado desplegable del control de botón de división actual.|
|[CButton::SetIcon](#seticon)|Especifica un icono que se mostrará en el botón.|
|[CButton::SetImageList](#setimagelist)|Establece la lista de imágenes del control de botón.|
|[CButton::SetNote](#setnote)|Establece la nota en el control de vínculo de comando actual.|
|[CButton::SetSplitGlyph](#setsplitglyph)|Asocia un glifo especificado con el control de botón de división actual.|
|[CButton::SetSplitImageList](#setsplitimagelist)|Asocia una lista de imágenes con el control de botón de división actual.|
|[CButton::SetSplitInfo](#setsplitinfo)|Especifica la información que define el control de botón de división actual.|
|[CButton::SetSplitSize](#setsplitsize)|Establece el rectángulo delimitador del componente desplegable del control de botón de división actual.|
|[CButton::SetSplitStyle](#setsplitstyle)|Establece el estilo del control de botón de división actual.|
|[CButton::SetState](#setstate)|Establece el estado de resaltado de un control de botón.|
|[CButton::SetTextMargin](#settextmargin)|Establece el margen de texto del control de botón.|

## <a name="remarks"></a>Observaciones

Un control de botón es una pequeña ventana secundaria rectangular en la que se puede hacer clic en activar y desactivar. Los botones se pueden usar solos o en grupos y pueden etiquetarse o aparecer sin texto. Normalmente, un botón cambia de apariencia cuando el usuario hace clic en él.

Los botones típicos son la casilla de verificación, el botón de opción y el pulsador. Un `CButton` objeto puede convertirse en cualquiera de estos, según el estilo de [botón](../../mfc/reference/styles-used-by-mfc.md#button-styles) especificado en su inicialización por el [Crear](#create) función miembro.

Además, la [clase CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) derivada de `CButton` admite la creación de controles de botón etiquetados con imágenes de mapa de bits en lugar de texto. A `CBitmapButton` puede tener mapas de bits independientes para los estados arriba, abajo, enfocado y deshabilitado de un botón.

Puede crear un control de botón desde una plantilla de cuadro de diálogo o directamente en el código. En ambos casos, primero `CButton` llame `CButton` al constructor para construir el objeto; a continuación, llame a la `Create` función miembro `CButton` para crear el control de botón de Windows y adjuntarlo al objeto.

La construcción puede ser un proceso de `CButton`un solo paso en una clase derivada de . Escriba un constructor para la `Create` clase derivada y llame desde dentro del constructor.

Si desea controlar los mensajes de notificación de Windows enviados por un control de botón a su elemento primario (normalmente una clase derivada de [CDialog](../../mfc/reference/cdialog-class.md)), agregue una entrada de mapa de mensajes y la función miembro de controlador de mensajes a la clase primaria para cada mensaje.

Cada entrada de mapa de mensajes adopta la siguiente forma:

**ON\_**_Notificación_ **(** _id_, _memberFxn_ **)**

donde *id* especifica el identificador de ventana secundaria del control que envía la notificación y *memberFxn* es el nombre de la función miembro principal que ha escrito para controlar la notificación.

El prototipo de función del padre es el siguiente:

`afx_msg void memberFxn();`

Las posibles entradas de mapa de mensajes son las siguientes:

|Entrada de mapa|Enviado a los padres cuando...|
|---------------|----------------------------|
|ON_BN_CLICKED|El usuario hace clic en un botón.|
|ON_BN_DOUBLECLICKED|El usuario hace doble clic en un botón.|

Si crea `CButton` un objeto a partir `CButton` de un recurso de cuadro de diálogo, el objeto se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.

Si crea `CButton` un objeto dentro de una ventana, es posible que deba destruirlo. Si crea `CButton` el objeto en el montón mediante la **nueva** función, debe llamar a **delete** en el objeto para destruirlo cuando el usuario cierre el control de botón de Windows. Si crea `CButton` el objeto en la pila o está incrustado en el objeto de cuadro de diálogo primario, se destruye automáticamente.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cbuttoncbutton"></a><a name="cbutton"></a>CButton::CButton

Construye un objeto `CButton`.

```
CButton();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

## <a name="cbuttoncreate"></a><a name="create"></a>CButton::Crear

Crea el control de botón `CButton` de Windows y lo adjunta al objeto.

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
Especifica el estilo del control de botón. Aplique cualquier combinación de estilos de [botón](../../mfc/reference/styles-used-by-mfc.md#button-styles) al botón.

*Rect*<br/>
Especifica el tamaño y la posición del control de botón. Puede ser un `CRect` objeto `RECT` o una estructura.

*pParentWnd*<br/>
Especifica la ventana primaria del control `CDialog`de botón, normalmente un archivo . No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de botón.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Construir un `CButton` objeto en dos pasos. En primer lugar, llame `Create`al constructor y, a continuación, `CButton` llame a , que crea el control de botón de Windows y lo adjunta al objeto.

Si se da el estilo WS_VISIBLE, Windows envía el control de botón todos los mensajes necesarios para activar y mostrar el botón.

Aplique los siguientes [estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles) de ventana a un control de botón:

- WS_CHILD Siempre

- WS_VISIBLE Por lo general

- WS_DISABLED Rara vez

- WS_GROUP Para agrupar controles

- WS_TABSTOP Para incluir el botón en el orden de tabulación

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

## <a name="cbuttondrawitem"></a><a name="drawitem"></a>CButton::DrawItem

Llamado por el marco de trabajo cuando un aspecto visual de un botón dibujado por el propietario ha cambiado.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Un puntero largo a una estructura [DRAWITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-drawitemstruct) La estructura contiene información sobre el elemento que se va a dibujar y el tipo de dibujo necesario.

### <a name="remarks"></a>Observaciones

Un botón dibujado por el propietario tiene el BS_OWNERDRAW estilo establecido. Invalidar esta función miembro para implementar `CButton` el dibujo para un objeto dibujado por el propietario. La aplicación debe restaurar todos los objetos de interfaz de dispositivo gráfico (GDI) seleccionados para el contexto de visualización proporcionado en *lpDrawItemStruct* antes de que finalice la función miembro.

Consulte también los valores de estilo [BS_.](../../mfc/reference/styles-used-by-mfc.md#button-styles)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

## <a name="cbuttongetbitmap"></a><a name="getbitmap"></a>CButton::GetBitmap

Llame a esta función miembro para obtener el identificador de un mapa de bits, establecido previamente con [SetBitmap](#setbitmap), que está asociado a un botón.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador de un mapa de bits. NULL si no se especifica previamente ningún mapa de bits.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttongetbuttonstyle"></a><a name="getbuttonstyle"></a>CButton::GetButtonStyle

Recupera información sobre el estilo de control de botón.

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve los estilos `CButton` de botón para este objeto. Esta función devuelve solo los valores de estilo [BS_,](../../mfc/reference/styles-used-by-mfc.md#button-styles) no cualquiera de los otros estilos de ventana.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttongetcheck"></a><a name="getcheck"></a>CButton::GetCheck

Recupera el estado de comprobación de un botón de opción o casilla de verificación.

```
int GetCheck() const;
```

### <a name="return-value"></a>Valor devuelto

El valor devuelto de un control de botón creado con el estilo BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON o BS_3STATE es uno de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|BST_UNCHECKED|El estado del botón está desactivado.|
|BST_CHECKED|Se comprueba el estado del botón.|
|BST_INDETERMINATE|El estado del botón es indeterminado (solo se aplica si el botón tiene el estilo BS_3STATE o BS_AUTO3STATE).|

Si el botón tiene cualquier otro estilo, el valor devuelto es BST_UNCHECKED.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttongetcursor"></a><a name="getcursor"></a>CButton::GetCursor

Llame a esta función miembro para obtener el identificador de un cursor, establecido previamente con [SetCursor](#setcursor), que está asociado a un botón.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Valor devuelto

Identificador de una imagen de cursor. NULL si no se especifica ningún cursor previamente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttongeticon"></a><a name="geticon"></a>CButton::GetIcon

Llame a esta función miembro para obtener el identificador de un icono, establecido previamente con [SetIcon](#seticon), que está asociado a un botón.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador de un icono. NULL si no se especifica ningún icono previamente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttongetidealsize"></a><a name="getidealsize"></a>CButton::GetIdealSize

Recupera el tamaño ideal para el control de botón.

```
BOOL GetIdealSize(SIZE* psize);
```

### <a name="parameters"></a>Parámetros

*psize*<br/>
Un puntero al tamaño actual del botón.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro emula la funcionalidad del mensaje BCM_GETIDEALSIZE, como se describe en la sección [Botones](/windows/win32/controls/buttons) del Windows SDK.

## <a name="cbuttongetimagelist"></a><a name="getimagelist"></a>CButton::GetImageList

Llame a este método para obtener la lista de imágenes desde el control de botón.

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parámetros

*pbuttonImagelist*<br/>
Un puntero a la `CButton` lista de imágenes del objeto.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro emula la funcionalidad del mensaje BCM_GETIMAGELIST, como se describe en la sección [Botones](/windows/win32/controls/buttons) del Windows SDK.

## <a name="cbuttongetnote"></a><a name="getnote"></a>CButton::GetNote

Recupera el texto de nota asociado con el control de vínculo de comando actual.

```
CString GetNote() const;

BOOL GetNote(
    LPTSTR lpszNote,
    UINT* cchNote) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*lpszNote*|[fuera] Puntero a un búfer, que el autor de la llamada es responsable de asignar y desasignar. Si el valor devuelto es TRUE, el búfer contiene el texto de la nota asociado al control de vínculo de comando actual; de lo contrario, el búfer no se modifica.|
|*cchNote*|[adentro, fuera] Puntero a una variable de entero sin signo.<br /><br /> Cuando se llama a este método, la variable contiene el tamaño del búfer especificado por el *lpszNote* parámetro.<br /><br /> Cuando se devuelve este método, si el valor devuelto es TRUE la variable contiene el tamaño de la nota asociada con el control de vínculo de comando actual. Si el valor devuelto es FALSE, la variable contiene el tamaño de búfer necesario para contener la nota.|

### <a name="return-value"></a>Valor devuelto

En la primera sobrecarga, un [CString](../../atl-mfc-shared/using-cstring.md) objeto que contiene el texto de nota asociado con el control de vínculo de comando actual.

o bien

En la segunda sobrecarga, TRUE si este método es correcto; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Utilice este método solo con controles cuyo estilo de botón se BS_COMMANDLINK o BS_DEFCOMMANDLINK.

Este método envía el [mensaje BCM_GETNOTE,](/windows/win32/Controls/bcm-getnote) que se describe en el Windows SDK.

## <a name="cbuttongetnotelength"></a><a name="getnotelength"></a>CButton::GetNoteLength

Recupera la longitud del texto de la nota para el control de vínculo de comando actual.

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud del texto de la nota, en caracteres Unicode de 16 bits, para el control de vínculo de comando actual.

### <a name="remarks"></a>Observaciones

Utilice este método solo con controles cuyo estilo de botón se BS_COMMANDLINK o BS_DEFCOMMANDLINK.

Este método envía el [mensaje BCM_GETNOTELENGTH,](/windows/win32/Controls/bcm-getnotelength) que se describe en el Windows SDK.

## <a name="cbuttongetsplitglyph"></a><a name="getsplitglyph"></a>CButton::GetSplitGlyph

Recupera el glifo asociado con el control de botón de división actual.

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>Valor devuelto

Carácter de glifo asociado con el control de botón de división actual.

### <a name="remarks"></a>Observaciones

Un glifo es la representación física de un carácter en una fuente determinada. Por ejemplo, un control de botón de división podría estar decorado con el glifo del carácter de marca de verificación Unicode (U+2713).

Utilice este método solo con controles cuyo estilo de botón está BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Este método inicializa `mask` el miembro de una estructura [de BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) con la marca BCSIF_GLYPH y, a continuación, envía esa estructura en el mensaje [de BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) que se describe en el Windows SDK. Cuando se devuelve la función message, `himlGlyph` este método recupera el glifo del miembro de la estructura.

## <a name="cbuttongetsplitimagelist"></a><a name="getsplitimagelist"></a>CButton::GetSplitImageList

Recupera la lista de [imágenes](../../mfc/reference/cimagelist-class.md) para el control de botón de división actual.

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto.

### <a name="remarks"></a>Observaciones

Utilice este método solo con controles cuyo estilo de botón está BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Este método inicializa `mask` el miembro de un [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) estructura con el BCSIF_IMAGE marca y, a continuación, envía esa estructura en el [mensaje de BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) que se describe en el Windows SDK. Cuando se devuelve la función message, este `himlGlyph` método recupera la lista de imágenes del miembro de la estructura.

## <a name="cbuttongetsplitinfo"></a><a name="getsplitinfo"></a>CButton::GetSplitInfo

Recupera parámetros que determinan cómo Windows dibuja el control de botón de división actual.

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pInfo*|[fuera] Puntero a una estructura [de BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) que recibe información sobre el control de botón de división actual. El autor de la llamada es responsable de asignar la estructura.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Utilice este método solo con controles cuyo estilo de botón está BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Este método envía el [mensaje BCM_GETSPLITINFO,](/windows/win32/Controls/bcm-getsplitinfo) que se describe en el Windows SDK.

## <a name="cbuttongetsplitsize"></a><a name="getsplitsize"></a>CButton::GetSplitSize

Recupera el rectángulo delimitador del componente desplegable del control de botón de división actual.

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pSize*|[fuera] Puntero a una estructura [SIZE](/windows/win32/api/windef/ns-windef-size) que recibe la descripción de un rectángulo.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Utilice este método solo con controles cuyo estilo de botón está BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Cuando se expande el control de botón de división, puede mostrar un componente desplegable como un control de lista o un control de paginación. Este método recupera el rectángulo delimitador que contiene el componente de lista desplegable.

Este método inicializa `mask` el miembro de una estructura [de BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) con la marca BCSIF_SIZE y, a continuación, envía esa estructura en el mensaje [de BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) que se describe en el Windows SDK. Cuando se devuelve la función message, este `size` método recupera el rectángulo delimitador del miembro de la estructura.

## <a name="cbuttongetsplitstyle"></a><a name="getsplitstyle"></a>CButton::GetSplitStyle

Recupera los estilos de botón de división que definen el control de botón de división actual.

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>Valor devuelto

Una combinación bit a bit de estilos de botón dividido. Para obtener más `uSplitStyle` información, consulte el miembro de la [estructura BUTTON_SPLITINFO.](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)

### <a name="remarks"></a>Observaciones

Utilice este método solo con controles cuyo estilo de botón está BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Los estilos de botón de división especifican la alineación, la relación de aspecto y el formato gráfico con el que Windows dibuja un icono de botón de división.

Este método inicializa `mask` el miembro de un [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) estructura con el BCSIF_STYLE marca y, a continuación, envía esa estructura en el [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) mensaje que se describe en el Windows SDK. Cuando se devuelve la función message, este `uSplitStyle` método recupera los estilos de botón de división del miembro de la estructura.

## <a name="cbuttongetstate"></a><a name="getstate"></a>CButton::GetState

Recupera el estado de un control de botón.

```
UINT GetState() const;
```

### <a name="return-value"></a>Valor devuelto

Un campo de bits que contiene la combinación de valores que indican el estado actual de un control de botón. En la tabla siguiente se enumeran los valores posibles.

|Estado del botón|Valor|Descripción|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|El estado inicial.|
|BST_CHECKED|0x0001|El control de botón está activado.|
|BST_INDETERMINATE|0x0002|El estado es indeterminado (solo es posible cuando el control de botón tiene tres estados).|
|BST_PUSHED|0x0004|Se pulsa el control de botón.|
|BST_FOCUS|0x0008|El control de botón tiene el foco.|

### <a name="remarks"></a>Observaciones

Un control de botón con el estilo de botón BS_3STATE o BS_AUTO3STATE crea una casilla de verificación que tiene un tercer estado denominado estado indeterminado. El estado indeterminado indica que la casilla de verificación no está marcada ni desactivada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttongettextmargin"></a><a name="gettextmargin"></a>CButton::GetTextMargin

Llame a este método para `CButton` obtener el margen de texto del objeto.

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parámetros

*pmargin*<br/>
Un puntero al margen `CButton` de texto del objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve el margen de texto.

### <a name="remarks"></a>Observaciones

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro emula la funcionalidad del BCM_GETTEXTMARGIN mensaje, como se describe en el [botones](/windows/win32/controls/buttons) sección del Windows SDK.

## <a name="cbuttonsetbitmap"></a><a name="setbitmap"></a>CButton::SetBitmap

Llame a esta función miembro para asociar un nuevo mapa de bits con el botón.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parámetros

*hBitmap*<br/>
El identificador de un mapa de bits.

### <a name="return-value"></a>Valor devuelto

El identificador de un mapa de bits asociado previamente con el botón.

### <a name="remarks"></a>Observaciones

El mapa de bits se colocará automáticamente en la cara del botón, centrado de forma predeterminada. Si el mapa de bits es demasiado grande para el botón, se recortará a cada lado. Puede elegir otras opciones de alineación, entre las que se incluyen las siguientes:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

A diferencia de [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), que `SetBitmap` utiliza cuatro mapas de bits por botón, utiliza solo un mapa de bits por el botón. Cuando se pulsa el botón, el mapa de bits parece desplazarse hacia abajo y hacia la derecha.

Usted es responsable de liberar el mapa de bits cuando haya terminado con él.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttonsetbuttonstyle"></a><a name="setbuttonstyle"></a>CButton::SetButtonStyle

Cambia el estilo de un botón.

```
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parámetros

*nStyle*<br/>
Especifica el estilo de [botón](../../mfc/reference/styles-used-by-mfc.md#button-styles).

*bRedraw*<br/>
Especifica si se va a volver a dibujar el botón. Un valor distinto de cero vuelve a dibujar el botón. Un valor 0 no vuelve a dibujar el botón. El botón se vuelve a dibujar de forma predeterminada.

### <a name="remarks"></a>Observaciones

Utilice `GetButtonStyle` la función miembro para recuperar el estilo de botón. La palabra de orden bajo del estilo de botón completo es el estilo específico del botón.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttonsetcheck"></a><a name="setcheck"></a>CButton::SetCheck

Establece o restablece el estado de comprobación de un botón de opción o casilla de verificación.

```
void SetCheck(int nCheck);
```

### <a name="parameters"></a>Parámetros

*nCheck*<br/>
Especifica el estado de comprobación. Este parámetro puede ser uno de los siguientes:

|Value|Significado|
|-----------|-------------|
|BST_UNCHECKED|Establezca el estado del botón en desmarcado.|
|BST_CHECKED|Establezca el estado del botón en checked.|
|BST_INDETERMINATE|Establezca el estado del botón en indeterminado. Este valor solo se puede utilizar si el botón tiene el estilo BS_3STATE o BS_AUTO3STATE.|

### <a name="remarks"></a>Observaciones

Esta función miembro no tiene ningún efecto en un pulsador.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttonsetcursor"></a><a name="setcursor"></a>CButton::SetCursor

Llame a esta función miembro para asociar un nuevo cursor con el botón.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parámetros

*hCursor*<br/>
El identificador de un cursor.

### <a name="return-value"></a>Valor devuelto

El identificador de un cursor asociado previamente con el botón.

### <a name="remarks"></a>Observaciones

El cursor se colocará automáticamente en la cara del botón, centrado por defecto. Si el cursor es demasiado grande para el botón, se recortará a cada lado. Puede elegir otras opciones de alineación, entre las que se incluyen las siguientes:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

A diferencia de [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), que `SetCursor` utiliza cuatro mapas de bits por botón, utiliza solo un cursor por el botón. Cuando se pulsa el botón, el cursor parece desplazarse hacia abajo y hacia la derecha.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttonsetdropdownstate"></a><a name="setdropdownstate"></a>CButton::SetDropDownState

Establece el estado desplegable del control de botón de división actual.

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*fDropDown*|[en] TRUE para establecer BST_DROPDOWNPUSHED estado; de lo contrario, FALSE.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Un control de botón de división tiene un estilo de BS_SPLITBUTTON o BS_DEFSPLITBUTTON y consta de un botón y una flecha desplegable a su derecha. Para obtener más información, consulte Estilos de [botón](/windows/win32/Controls/button-styles). Normalmente, el estado desplegable se establece cuando el usuario hace clic en la flecha desplegable. Utilice este método para establecer mediante programación el estado de lista desplegable del control. La flecha desplegable se dibuja sombreada para indicar el estado.

Este método envía el [mensaje BCM_SETDROPDOWNSTATE,](/windows/win32/Controls/bcm-setdropdownstate) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define la variable, *m_splitButton*, que se usa para tener acceso mediante programación al control de botón de división. Esta variable se utiliza en el ejemplo siguiente.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece el estado del control de botón de división para indicar que se inserta la flecha desplegable.

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

## <a name="cbuttonsetelevationrequired"></a><a name="setelevationrequired"></a>CButton::SetElevationRequired

Establece el estado del control `elevation required`de botón actual en , que es necesario para que el control muestre un icono de seguridad elevado.

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*fElevationRequired*|[en] TRUE para `elevation required` establecer el estado; de lo contrario, FALSE.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Si un control de vínculo de botón o comando requiere un `elevation required` permiso de seguridad elevado para realizar una acción, establezca el control en estado. Posteriormente, Windows muestra el icono de escudo de Control de cuentas de usuario (UAC) en el control. Para obtener más información, consulte "Control de cuentas de usuario" en [MSDN](https://go.microsoft.com/fwlink/p/?linkid=18507).

Este método envía el [mensaje BCM_SETSHIELD,](/windows/win32/Controls/bcm-setshield) que se describe en el Windows SDK.

## <a name="cbuttonseticon"></a><a name="seticon"></a>CButton::SetIcon

Llame a esta función miembro para asociar un nuevo icono con el botón.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parámetros

*hIcon*<br/>
El identificador de un icono.

### <a name="return-value"></a>Valor devuelto

El identificador de un icono asociado previamente con el botón.

### <a name="remarks"></a>Observaciones

El icono se colocará automáticamente en la cara del botón, centrado por defecto. Si el icono es demasiado grande para el botón, se recortará a cada lado. Puede elegir otras opciones de alineación, entre las que se incluyen las siguientes:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

A diferencia de [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), que `SetIcon` utiliza cuatro mapas de bits por botón, utiliza solo un icono por el botón. Cuando se pulsa el botón, el icono parece desplazarse hacia abajo y hacia la derecha.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttonsetimagelist"></a><a name="setimagelist"></a>CButton::SetImageList

Llame a este método para `CButton` establecer la lista de imágenes del objeto.

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parámetros

*pbuttonImagelist*<br/>
Un puntero a la nueva lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Esta función miembro emula la funcionalidad del mensaje de BCM_SETIMAGELIST, como se describe en la sección [Botones](/windows/win32/controls/buttons) del Windows SDK.

## <a name="cbuttonsetnote"></a><a name="setnote"></a>CButton::SetNote

Establece el texto de la nota para el control de vínculo de comando actual.

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*lpszNote*|[en] Puntero a una cadena Unicode que se establece como texto de nota para el control de vínculo de comando.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Utilice este método solo con controles cuyo estilo de botón se BS_COMMANDLINK o BS_DEFCOMMANDLINK.

Este método envía el [mensaje BCM_SETNOTE,](/windows/win32/Controls/bcm-setnote) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define la variable, *m_cmdLink*, que se usa para tener acceso mediante programación al control de vínculo de comando. Esta variable se utiliza en el ejemplo siguiente.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece el texto de la nota para el control de vínculo de comando.

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

## <a name="cbuttonsetsplitglyph"></a><a name="setsplitglyph"></a>CButton::SetSplitGlyph

Asocia un glifo especificado con el control de botón de división actual.

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*chGlyph*|[en] Carácter que especifica el glifo que se utilizará como flecha desplegable del botón de división.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Utilice este método solo con controles que tengan el estilo de botón BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Un glifo es la representación física de un carácter en una fuente determinada. El parámetro *chGlyph* no se utiliza como glifo, sino que se utiliza para seleccionar un glifo de un conjunto de glifos definidos por el sistema. El glifo de flecha desplegable predeterminado se especifica con un carácter '6' y se asemeja al carácter Unicode BLACK DOWN-POINTING TRIANGLE (U+25BC).

Este método inicializa `mask` el miembro de un [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) `himlGlyph` estructura con el BCSIF_GLYPH marca y el miembro con el *chGlyph* parámetro y, a continuación, envía esa estructura en el [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) mensaje que se describe en el Windows SDK.

## <a name="cbuttonsetsplitimagelist"></a><a name="setsplitimagelist"></a>CButton::SetSplitImageList

Asocia una lista de [imágenes](../../mfc/reference/cimagelist-class.md) con el control de botón de división actual.

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pSplitImageList*|[en] Puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto para asignar al control de botón de división actual.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Utilice este método solo con controles cuyo estilo de botón está BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Este método inicializa `mask` el miembro de una estructura `himlGlyph` de [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) con el BCSIF_IMAGE marca y el miembro con el *pSplitImageList* parámetro y, a continuación, envía esa estructura en el [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) mensaje que se describe en el Windows SDK.

## <a name="cbuttonsetsplitinfo"></a><a name="setsplitinfo"></a>CButton::SetSplitInfo

Especifica los parámetros que determinan cómo Windows dibuja el control de botón de división actual.

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pInfo*|[en] Puntero a una estructura [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) que define el control de botón de división actual.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Utilice este método solo con controles cuyo estilo de botón está BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Este método envía el [mensaje BCM_SETSPLITINFO,](/windows/win32/Controls/bcm-setsplitinfo) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de `m_splitButton`código siguiente se define la variable, , que se usa para tener acceso mediante programación al control de botón de división.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se cambia el glifo que se utiliza para la flecha desplegable del botón de división. En el ejemplo se sustituye un glifo de triángulo que apunta hacia arriba por el glifo de triángulo que apunta hacia abajo por defecto. El glifo que se muestra depende del carácter que especifique en el `himlGlyph` miembro de la `BUTTON_SPLITINFO` estructura. El glifo de triángulo que apunta hacia abajo se especifica mediante un carácter '6' y el glifo de triángulo hacia arriba se especifica mediante un carácter '5'. Para la comparación, vea el método de conveniencia, [CButton::SetSplitGlyph](#setsplitglyph).

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

## <a name="cbuttonsetsplitsize"></a><a name="setsplitsize"></a>CButton::SetSplitSize

Establece el rectángulo delimitador del componente desplegable del control de botón de división actual.

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pSize*|[en] Puntero a una estructura [SIZE](/windows/win32/api/windef/ns-windef-size) que describe un rectángulo delimitador.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Utilice este método solo con controles cuyo estilo de botón está BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Cuando se expande el control de botón de división, puede mostrar un componente desplegable como un control de lista o un control de paginación. Este método especifica el tamaño del rectángulo delimitador que contiene el componente de lista desplegable.

Este método inicializa `mask` el miembro de una estructura `size` de [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) con el BCSIF_SIZE marca y el miembro con el *pSize* parámetro y, a continuación, envía esa estructura en el [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) mensaje que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de `m_splitButton`código siguiente se define la variable, , que se usa para tener acceso mediante programación al control de botón de división. Esta variable se utiliza en el ejemplo siguiente.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se duplica el tamaño de la flecha desplegable del botón de división.

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

## <a name="cbuttonsetsplitstyle"></a><a name="setsplitstyle"></a>CButton::SetSplitStyle

Establece el estilo del control de botón de división actual.

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*uSplitStyle*|[en] Una combinación bit a bit de estilos de botón dividido. Para obtener más `uSplitStyle` información, consulte el miembro de la [estructura BUTTON_SPLITINFO.](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Utilice este método solo con controles cuyo estilo de botón está BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Los estilos de botón de división especifican la alineación, la relación de aspecto y el formato gráfico con el que Windows dibuja un icono de botón de división. Para obtener más `uSplitStyle` información, consulte el miembro de la [estructura BUTTON_SPLITINFO.](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)

Este método inicializa `mask` el miembro de una [estructura](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo) `uSplitStyle` BUTTON_SPLITINFO con el BCSIF_STYLE marca y el miembro con el *uSplitStyle* parámetro y, a continuación, envía esa estructura en el [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo) mensaje que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de `m_splitButton`código siguiente se define la variable, , que se usa para tener acceso mediante programación al control de botón de división.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece el estilo de la flecha desplegable del botón de división. El estilo BCSS_ALIGNLEFT muestra la flecha en el lado izquierdo del botón y el estilo BCSS_STRETCH conserva las proporciones de la flecha desplegable al cambiar el tamaño del botón.

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

## <a name="cbuttonsetstate"></a><a name="setstate"></a>CButton::SetState

Establece si un control de botón está resaltado o no.

```
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>Parámetros

*bResaltar*<br/>
Especifica si se va a resaltar el botón. Un valor distinto de cero resalta el botón; un valor 0 elimina cualquier resaltado.

### <a name="remarks"></a>Observaciones

El resaltado afecta al exterior de un control de botón. No tiene ningún efecto en el estado de verificación de un botón de opción o casilla de verificación.

Un control de botón se resalta automáticamente cuando el usuario hace clic y mantiene pulsado el botón izquierdo del ratón. El resaltado se elimina cuando el usuario suelta el botón del ratón.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttonsettextmargin"></a><a name="settextmargin"></a>CButton::SetTextMargin

Llame a este método para `CButton` establecer el margen de texto del objeto.

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parámetros

*pmargin*<br/>
Un puntero al nuevo margen de texto.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Esta función miembro emula la funcionalidad del mensaje de BCM_SETTEXTMARGIN, como se describe en la sección [Botones](/windows/win32/controls/buttons) del Windows SDK.

## <a name="see-also"></a>Consulte también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CComboBox (clase)](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox (clase)](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar (clase)](../../mfc/reference/cscrollbar-class.md)<br/>
[Clase CStatic](../../mfc/reference/cstatic-class.md)<br/>
[CBitmapButton (clase)](../../mfc/reference/cbitmapbutton-class.md)<br/>
[Clase CDialog](../../mfc/reference/cdialog-class.md)
