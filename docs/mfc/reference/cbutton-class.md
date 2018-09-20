---
title: CButton (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2f0f0ce6a893406fca73f25e040cbc3dbd29d08
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429947"
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
|[CButton::CButton](#cbutton)|Construye un objeto `CButton`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CButton::Create](#create)|Crea el control de botón de Windows y lo adjunta a la `CButton` objeto.|
|[CButton::DrawItem](#drawitem)|Invalidación para dibujar un dibujado `CButton` objeto.|
|[CButton::GetBitmap](#getbitmap)|Recupera el identificador del mapa de bits establecido previamente con [SetBitmap](#setbitmap).|
|[CButton::GetButtonStyle](#getbuttonstyle)|Recupera información sobre el estilo del control de botón.|
|[CButton::GetCheck](#getcheck)|Recupera el estado de activación de un control de botón.|
|[CButton::GetCursor](#getcursor)|Recupera el identificador de la imagen del cursor establecido previamente con [SetCursor](#setcursor).|
|[CButton::GetIcon](#geticon)|Recupera el identificador del icono establecido previamente con [SetIcon](#seticon).|
|[CButton::GetIdealSize](#getidealsize)|Recupera el tamaño ideal del control de botón.|
|[CButton::GetImageList](#getimagelist)|Recupera la lista de imágenes del control de botón.|
|[CButton::GetNote](#getnote)|Recupera el componente de nota del control de vínculo de comando actual.|
|[CButton::GetNoteLength](#getnotelength)|Recupera la longitud del texto de nota para el control de vínculo de comando actual.|
|[CButton::GetSplitGlyph](#getsplitglyph)|Recupera el glifo asociado al control de botón de división actual.|
|[CButton::GetSplitImageList](#getsplitimagelist)|Recupera la lista de imágenes para el control de botón de división actual.|
|[CButton::GetSplitInfo](#getsplitinfo)|Recupera la información que define el control de botón de división actual.|
|[CButton::GetSplitSize](#getsplitsize)|Recupera el rectángulo delimitador del componente de lista desplegable del control de botón de división actual.|
|[CButton::GetSplitStyle](#getsplitstyle)|Recupera los estilos de botón de división que definen el control de botón de división actual.|
|[CButton::GetState](#getstate)|Recupera el estado de comprobación, el estado de resaltado y el estado del foco de un control de botón.|
|[CButton::GetTextMargin](#gettextmargin)|Recupera el margen del texto del control de botón.|
|[CButton:: SetBitmap](#setbitmap)|Especifica un mapa de bits que se mostrará en el botón.|
|[CButton::SetButtonStyle](#setbuttonstyle)|Cambia el estilo de un botón.|
|[CButton::SetCheck](#setcheck)|Establece el estado de activación de un control de botón.|
|[CButton::SetCursor](#setcursor)|Especifica una imagen de cursor que se mostrará en el botón.|
|[CButton::SetDropDownState](#setdropdownstate)|Establece el estado de la lista desplegable del control de botón de división actual.|
|[CButton::SetIcon](#seticon)|Especifica el icono que se muestra en el botón.|
|[CButton::SetImageList](#setimagelist)|Establece la lista de imágenes del control de botón.|
|[CButton::SetNote](#setnote)|Establece la nota en el control de vínculo de comando actual.|
|[CButton::SetSplitGlyph](#setsplitglyph)|Asocia un glifo especificado con el control de botón de división actual.|
|[CButton::SetSplitImageList](#setsplitimagelist)|Asocia una lista de imágenes con el control de botón de división actual.|
|[CButton::SetSplitInfo](#setsplitinfo)|Especifica la información que define el control de botón de división actual.|
|[CButton::SetSplitSize](#setsplitsize)|Establece el rectángulo delimitador del componente de lista desplegable del control de botón de división actual.|
|[CButton::SetSplitStyle](#setsplitstyle)|Establece el estilo del control de botón de división actual.|
|[CButton::SetState](#setstate)|Establece el estado de un control de botón resaltado.|
|[CButton::SetTextMargin](#settextmargin)|Establece el margen del texto del control de botón.|

## <a name="remarks"></a>Comentarios

Un control de botón es una ventana rectangular pequeño secundarios que puede hacer clic en activar y desactivar. Botones pueden usarse por sí solo o en grupos y o bien se pueden etiquetar o aparecen sin texto. Un botón normalmente cambia de apariencia cuando el usuario hace clic en él.

Botones habituales son la casilla de verificación, botón de radio y pushbutton. Un `CButton` objeto puede convertirse en cualquiera de ellos, según la [botón estilo](../../mfc/reference/styles-used-by-mfc.md#button-styles) especificado en su inicialización, mediante la [crear](#create) función miembro.

Además, el [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) deriva de la clase `CButton` admite la creación de controles de botón con la etiqueta con imágenes de mapa de bits en lugar de texto. Un `CBitmapButton` puede tener los mapas de bits independientes para un botón de la, abajo, centrado y deshabilitado Estados.

Puede crear un control de botón de una plantilla de cuadro de diálogo o directamente en el código. En ambos casos, primero llame al constructor `CButton` para construir el `CButton` objeto; a continuación, llame a la `Create` función miembro para crear el Windows control de botón y adjuntarlo a la `CButton` objeto.

Construcción puede ser un proceso de un paso en una clase derivada de `CButton`. Escribir un constructor para la clase derivada y llame a `Create` desde dentro del constructor.

Si desea controlar los mensajes de notificación de Windows enviados por un control de botón a su elemento primario (normalmente una clase derivada de [CDialog](../../mfc/reference/cdialog-class.md)), agregue una función de miembro de entrada y el controlador de mensajes del mapa de mensajes a la clase primaria para cada mensaje.

Cada entrada de mapa de mensajes tiene el formato siguiente:

**ON_** notificación **(**`id`, `memberFxn` **)**

donde `id` especifica el identificador de ventana secundaria del control que envía la notificación y `memberFxn` es el nombre de la función de miembro primario que ha escrito para controlar la notificación.

Prototipo de función del elemento primario es el siguiente:

**afx_msg** `void` `memberFxn` **();**

Las entradas de mapa de mensajes posibles son los siguientes:

|Entrada de asignación|Se envían al elemento primario cuando...|
|---------------|----------------------------|
|ON_BN_CLICKED|El usuario hace clic en un botón.|
|ON_BN_DOUBLECLICKED|El usuario hace doble clic en un botón.|

Si creas un `CButton` objeto desde un recurso de cuadro de diálogo, el `CButton` objeto se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.

Si creas un `CButton` objeto dentro de una ventana, es posible que deba destruirlo. Si crea el `CButton` objeto en el montón mediante el uso de la **nueva** función, debe llamar a **eliminar** control de botón en el objeto que lo destruirá cuando el usuario cierra el Windows. Si crea la `CButton` objeto en la pila, o bien está incrustado en el objeto de cuadro de diálogo primario, se destruye automáticamente.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cbutton"></a>  CButton::CButton

Construye un objeto `CButton`.

```
CButton();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

##  <a name="create"></a>  CButton::Create

Crea el control de botón de Windows y lo adjunta a la `CButton` objeto.

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
Especifica el estilo del control de botón. Aplicar cualquier combinación de [estilos de botón](../../mfc/reference/styles-used-by-mfc.md#button-styles) al botón.

*Rect*<br/>
Especifica el tamaño y la posición del control de botón. Puede ser un `CRect` objeto o un `RECT` estructura.

*pParentWnd*<br/>
Especifica la ventana del elemento primario del control de botón, normalmente un `CDialog`. No debe ser NULL.

*nID*<br/>
Especifica el identificador. del control de botón

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Construir un `CButton` objeto en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a `Create`, que crea el control de botón de Windows y lo adjunta a la `CButton` objeto.

Si se especifica el estilo WS_VISIBLE, Windows envía el control de botón en todos los mensajes necesarios para activar y mostrar el botón.

Aplique el siguiente [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) a un control de botón:

- WS_CHILD siempre

- WS_VISIBLE normalmente

- WS_DISABLED rara vez

- WS_GROUP a controles de grupo

- WS_TABSTOP para incluir el botón en el orden de tabulación

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

##  <a name="drawitem"></a>  CButton::DrawItem

Lo llama el marco cuando un aspecto visual de un botón dibujado por el propietario ha cambiado.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Un puntero largo a un [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) estructura. La estructura contiene información sobre el elemento que se va a dibujar y el tipo de dibujo necesaria.

### <a name="remarks"></a>Comentarios

Un botón dibujado por el usuario tiene el estilo BS_OWNERDRAW establecido. Reemplace esta función miembro para implementar el dibujo para dibujar un `CButton` objeto. La aplicación debe restaurar todos los objetos de interfaz (GDI) de dispositivo de gráficos seleccionados para proporciona el contexto de presentación en *lpDrawItemStruct* antes del miembro de función termina.

Consulte también el [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) valores de estilo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

##  <a name="getbitmap"></a>  CButton::GetBitmap

Llame a esta función miembro para obtener el identificador de un mapa de bits establecido previamente con [SetBitmap](#setbitmap), que está asociado con un botón.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador de un mapa de bits. NULL si previamente no se especifica ningún mapa de bits.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

##  <a name="getbuttonstyle"></a>  CButton::GetButtonStyle

Recupera información sobre el estilo del control de botón.

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve los estilos de botón para este `CButton` objeto. Esta función devuelve solo el [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) valores de estilo, no en cualquiera de los demás estilos de ventana.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

##  <a name="getcheck"></a>  CButton::GetCheck

Recupera el estado de activación de un botón de radio o casilla.

```
int GetCheck() const;
```

### <a name="return-value"></a>Valor devuelto

El valor devuelto de un control de botón creado con la BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON o estilo BS_3STATE es uno de los siguientes valores:

|Valor|Significado|
|-----------|-------------|
|BST_UNCHECKED|Estado del botón está desactivada.|
|BST_CHECKED|Se comprueba el estado del botón.|
|BST_INDETERMINATE|Estado del botón es indeterminado (se aplica sólo si el botón tiene el estilo BS_3STATE o BS_AUTO3STATE).|

Si el botón tiene cualquier otro estilo, el valor devuelto es BST_UNCHECKED.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

##  <a name="getcursor"></a>  CButton::GetCursor

Llame a esta función miembro para obtener el identificador de un cursor, establecido previamente con [SetCursor](#setcursor), que está asociado con un botón.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Valor devuelto

Identificador de una imagen del cursor. NULL si previamente no se especifica ningún cursor.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

##  <a name="geticon"></a>  CButton::GetIcon

Llame a esta función miembro para obtener el identificador de un conjunto de iconos, anteriormente con [SetIcon](#seticon), que está asociado con un botón.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador de un icono. NULL si previamente no se especifica ningún icono.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

##  <a name="getidealsize"></a>  CButton::GetIdealSize

Recupera el tamaño ideal para el control de botón.

```
BOOL GetIdealSize(SIZE* psize);
```

### <a name="parameters"></a>Parámetros

*psize*<br/>
Un puntero al tamaño actual del botón.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad del mensaje BCM_GETIDEALSIZE, como se describe en el [botones](https://msdn.microsoft.com/library/windows/desktop/bb775943) sección del SDK de Windows.

##  <a name="getimagelist"></a>  CButton::GetImageList

Llame a este método para obtener la lista de imágenes desde el control de botón.

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parámetros

*pbuttonImagelist*<br/>
Un puntero a la lista de imágenes de la `CButton` objeto.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad del mensaje BCM_GETIMAGELIST, como se describe en el [botones](https://msdn.microsoft.com/library/windows/desktop/bb775943) sección del SDK de Windows.

##  <a name="getnote"></a>  CButton::GetNote

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
|*lpszNote*|[out] Puntero a un búfer que el llamador es responsable de asignar y desasignar. Si el valor devuelto es TRUE, el búfer contiene el texto de la nota que está asociado con el control de vínculo de comando actual; en caso contrario, no se modifica el búfer.|
|*cchNote*|[in, out] Un puntero a una variable de entero sin signo.<br /><br /> Cuando se llama a este método, la variable contiene el tamaño del búfer especificado por el *lpszNote* parámetro.<br /><br /> Cuando este método devuelve, si el valor devuelto es TRUE, la variable contiene el tamaño de la nota asociado al control de vínculo de comando actual. Si el valor devuelto es FALSE, la variable contiene el tamaño del búfer necesario para contener la nota.|

### <a name="return-value"></a>Valor devuelto

En la primera sobrecarga, una [CString](../../atl-mfc-shared/using-cstring.md) objeto que contiene el texto de nota asociado con el control de vínculo de comando actual.

O bien

En la segunda sobrecarga, TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use este método solo con los controles cuyo estilo de botón es BS_COMMANDLINK o BS_DEFCOMMANDLINK.

Este método envía el [BCM_GETNOTE](/windows/desktop/Controls/bcm-getnote) mensaje, que se describe en el SDK de Windows.

##  <a name="getnotelength"></a>  CButton::GetNoteLength

Recupera la longitud del texto de nota para el control de vínculo de comando actual.

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud del texto de nota, en caracteres Unicode de 16 bits, para el control de vínculo de comando actual.

### <a name="remarks"></a>Comentarios

Use este método solo con los controles cuyo estilo de botón es BS_COMMANDLINK o BS_DEFCOMMANDLINK.

Este método envía el [BCM_GETNOTELENGTH](/windows/desktop/Controls/bcm-getnotelength) mensaje, que se describe en el SDK de Windows.

##  <a name="getsplitglyph"></a>  CButton::GetSplitGlyph

Recupera el glifo asociado al control de botón de división actual.

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>Valor devuelto

El carácter de glifo asociado al control de botón de división actual.

### <a name="remarks"></a>Comentarios

Un glifo es la representación física de un carácter en una fuente concreta. Por ejemplo, un control de botón de expansión podría ser representativos con el glifo del carácter de marca de verificación de Unicode (2713).

Use este método solo con los controles cuyo estilo de botón es BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Este método inicializa la `mask` miembro de un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) estructura con la marca BCSIF_GLYPH y, a continuación, envía a los que la estructura en el [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) mensaje que se describe en el Windows SDK. La función del mensaje que devuelve este método recupera el glifo de la `himlGlyph` miembro de la estructura.

##  <a name="getsplitimagelist"></a>  CButton::GetSplitImageList

Recupera el [lista de imágenes](../../mfc/reference/cimagelist-class.md) para el control de botón de división actual.

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto.

### <a name="remarks"></a>Comentarios

Use este método solo con los controles cuyo estilo de botón es BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Este método inicializa la `mask` miembro de un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) estructura con la marca BCSIF_IMAGE y, a continuación, envía a los que la estructura en el [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) mensaje que se describe en el Windows SDK. La función del mensaje que devuelve este método recupera la lista de imágenes desde el `himlGlyph` miembro de la estructura.

##  <a name="getsplitinfo"></a>  CButton::GetSplitInfo

Recupera los parámetros que determinan cómo Windows dibuja el control de botón de división actual.

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pInfo*|[out] Puntero a un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) estructura que recibe información sobre el control de botón de división actual. El llamador es responsable de asignar la estructura.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use este método solo con los controles cuyo estilo de botón es BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Este método envía el [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) mensaje, que se describe en el SDK de Windows.

##  <a name="getsplitsize"></a>  CButton::GetSplitSize

Recupera el rectángulo delimitador del componente de lista desplegable del control de botón de división actual.

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pSize*|[out] Puntero a un [tamaño](https://msdn.microsoft.com/library/windows/desktop/dd145106) estructura que recibe la descripción de un rectángulo.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use este método solo con los controles cuyo estilo de botón es BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Cuando se expande el control de botón de expansión, puede mostrar un componente de la lista desplegable, como un control de lista o un control de paginación. Este método recupera el rectángulo delimitador que contiene el componente de la lista desplegable.

Este método inicializa la `mask` miembro de un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) estructura con la marca BCSIF_SIZE y, a continuación, envía a los que la estructura en el [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) mensaje que se describe en el Windows SDK. La función del mensaje que devuelve este método recupera el rectángulo delimitador de la `size` miembro de la estructura.

##  <a name="getsplitstyle"></a>  CButton::GetSplitStyle

Recupera los estilos de botón de división que definen el control de botón de división actual.

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>Valor devuelto

Una combinación bit a bit de los estilos de botón de división. Para obtener más información, consulte el `uSplitStyle` miembro de la [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) estructura.

### <a name="remarks"></a>Comentarios

Use este método solo con los controles cuyo estilo de botón es BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Los estilos de botón de división especifican la alineación, la relación de aspecto y el formato gráfico con el que Windows dibuja un icono de botón de división.

Este método inicializa la `mask` miembro de un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) estructura con la marca BCSIF_STYLE y, a continuación, envía a los que la estructura en el [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) mensaje que se describe en el Windows SDK. La función del mensaje que devuelve este método recupera los estilos de botón de división de la `uSplitStyle` miembro de la estructura.

##  <a name="getstate"></a>  CButton::GetState

Recupera el estado de un control de botón.

```
UINT GetState() const;
```

### <a name="return-value"></a>Valor devuelto

Un campo de bits que contiene la combinación de valores que indican el estado actual de un control de botón. En la tabla siguiente se enumera los valores posibles.

|Estado del botón|Valor|Descripción|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|El estado inicial.|
|BST_CHECKED|0 x 0001|El control de botón está activado.|
|BST_INDETERMINATE|0x0002|El estado indeterminado (sólo es posible cuando el control de botón tiene tres estados).|
|BST_PUSHED|0x0004|El control de botón está presionado.|
|BST_FOCUS|0x0008|El control de botón tiene el foco.|

### <a name="remarks"></a>Comentarios

Un control de botón con el estilo de botón BS_3STATE o BS_AUTO3STATE crea una casilla que tiene un estado terceros que se denomina el estado indeterminado. El estado indeterminado indica que la casilla de verificación está ni activada ni desactivada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

##  <a name="gettextmargin"></a>  CButton::GetTextMargin

Llame a este método para obtener el margen del texto de la `CButton` objeto.

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parámetros

*pmargin*<br/>
Un puntero en el margen del texto de la `CButton` objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve el margen de texto.

### <a name="remarks"></a>Comentarios

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad del mensaje BCM_GETTEXTMARGIN, como se describe en el [botones](https://msdn.microsoft.com/library/windows/desktop/bb775943) sección del SDK de Windows.

##  <a name="setbitmap"></a>  CButton:: SetBitmap

Llame a esta función miembro para asociar un nuevo mapa de bits con el botón.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parámetros

*hBitmap*<br/>
El identificador de un mapa de bits.

### <a name="return-value"></a>Valor devuelto

El identificador de un mapa de bits asociado anteriormente con el botón.

### <a name="remarks"></a>Comentarios

El mapa de bits se colocará automáticamente en el botón, centrado de forma predeterminada. Si el mapa de bits es demasiado grande para el botón, se recortará a ambos lados. Puede elegir otras opciones de alineación, incluidas las siguientes:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

A diferencia de [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), que usa cuatro mapas de bits por cada botón, `SetBitmap` utiliza sólo un mapa de bits por el botón. Cuando se presiona el botón, aparece el mapa de bits desplazar hacia abajo y a la derecha.

Usted es responsable de liberar el mapa de bits cuando haya terminado con él.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

##  <a name="setbuttonstyle"></a>  CButton::SetButtonStyle

Cambia el estilo de un botón.

```
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parámetros

*nStyle*<br/>
Especifica el [botón estilo](../../mfc/reference/styles-used-by-mfc.md#button-styles).

*bRedraw*<br/>
Especifica si el botón volver a dibujar. Un valor distinto de cero, se vuelve a dibujar el botón. Un valor de 0 no volver a dibujar el botón. Se vuelve a dibujar el botón de forma predeterminada.

### <a name="remarks"></a>Comentarios

Use el `GetButtonStyle` función miembro para recuperar el estilo de botón. La palabra de orden inferior del estilo de botón de finalización es el estilo de botón específico.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

##  <a name="setcheck"></a>  CButton::SetCheck

Establece o restablece el estado de activación de un botón de radio o casilla.

```
void SetCheck(int nCheck);
```

### <a name="parameters"></a>Parámetros

*nCompruebe*<br/>
Especifica el estado de activación. Este parámetro puede ser uno de los siguientes:

|Valor|Significado|
|-----------|-------------|
|BST_UNCHECKED|Establece el estado del botón en desactivada.|
|BST_CHECKED|Establecer el estado del botón que va a comprobar.|
|BST_INDETERMINATE|Establecer el estado del botón a indeterminado. Este valor puede utilizarse solo si el botón tiene el estilo BS_3STATE o BS_AUTO3STATE.|

### <a name="remarks"></a>Comentarios

Esta función miembro tiene ningún efecto en un botón de comando.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

##  <a name="setcursor"></a>  CButton::SetCursor

Llame a esta función miembro para asociar un nuevo cursor con el botón.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parámetros

*hCursor*<br/>
El identificador de un cursor.

### <a name="return-value"></a>Valor devuelto

El identificador de un cursor anteriormente asociado con el botón.

### <a name="remarks"></a>Comentarios

El cursor se colocará automáticamente en el botón, centrado de forma predeterminada. Si el cursor es demasiado grande para el botón, se recortará a ambos lados. Puede elegir otras opciones de alineación, incluidas las siguientes:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

A diferencia de [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), que usa cuatro mapas de bits por cada botón, `SetCursor` utiliza sólo un cursor por el botón. Cuando se presiona el botón, aparece el cursor de desplazamiento hacia abajo y a la derecha.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

##  <a name="setdropdownstate"></a>  CButton::SetDropDownState

Establece el estado de la lista desplegable del control de botón de división actual.

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*fDropDown*|[in] TRUE para establecer el estado BST_DROPDOWNPUSHED; en caso contrario, FALSE.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Un control de botón de expansión tiene un estilo BS_SPLITBUTTON o BS_DEFSPLITBUTTON y consta de un botón y una flecha de lista desplegable a la derecha. Para obtener más información, consulte [estilos de botón](/windows/desktop/Controls/button-styles). Por lo general, el estado de la lista desplegable se establece cuando el usuario hace clic en la flecha de lista desplegable. Utilice este método para establecer mediante programación el estado de la lista desplegable del control. La flecha de lista desplegable se dibuja sombreada para indicar el estado.

Este método envía el [BCM_SETDROPDOWNSTATE](/windows/desktop/Controls/bcm-setdropdownstate) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente define la variable, *m_splitButton*, que se usa para obtener acceso mediante programación el control de botón de expansión. Esta variable se usa en el ejemplo siguiente.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente establece el estado del control de botón de división para indicar que se inserta la flecha de lista desplegable.

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

##  <a name="setelevationrequired"></a>  CButton::SetElevationRequired

Establece el estado del control de botón actual a `elevation required`, que es necesario para el control mostrar un icono de seguridad con privilegios elevados.

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*fElevationRequired*|[in] Es True para establecer `elevation required` estado; en caso contrario, FALSE.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Si un control de vínculo de botón o comando requiere el permiso de seguridad con privilegios elevados para realizar una acción, establezca el control en `elevation required` estado. Posteriormente, Windows muestra el icono de escudo de Control de cuentas de usuario (UAC) en el control. Para obtener más información, vea "Control de cuentas de usuario" en [MSDN](http://go.microsoft.com/fwlink/p/?linkid=18507).

Este método envía el [BCM_SETSHIELD](/windows/desktop/Controls/bcm-setshield) mensaje, que se describe en el SDK de Windows.

##  <a name="seticon"></a>  CButton::SetIcon

Llame a esta función miembro para asociar un icono nuevo con el botón.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parámetros

*hIcon*<br/>
El identificador de un icono.

### <a name="return-value"></a>Valor devuelto

El identificador de un icono de estado asociado anteriormente con el botón.

### <a name="remarks"></a>Comentarios

El icono se colocará automáticamente en el botón, centrado de forma predeterminada. Si el icono es demasiado grande para el botón, se recortará a ambos lados. Puede elegir otras opciones de alineación, incluidas las siguientes:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

A diferencia de [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), que usa cuatro mapas de bits por cada botón, `SetIcon` usa un solo icono por el botón. Cuando se presiona el botón, aparece el icono de desplazamiento hacia abajo y a la derecha.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

##  <a name="setimagelist"></a>  CButton::SetImageList

Llame a este método para establecer la lista de imágenes de la `CButton` objeto.

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>Parámetros

*pbuttonImagelist*<br/>
Un puntero a la nueva lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad del mensaje BCM_SETIMAGELIST, como se describe en el [botones](https://msdn.microsoft.com/library/windows/desktop/bb775943) sección del SDK de Windows.

##  <a name="setnote"></a>  CButton::SetNote

Establece el texto de nota para el control de vínculo de comando actual.

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*lpszNote*|[in] Puntero a una cadena Unicode que se establece como el texto de nota para el control de vínculo de comando.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use este método solo con los controles cuyo estilo de botón es BS_COMMANDLINK o BS_DEFCOMMANDLINK.

Este método envía el [BCM_SETNOTE](/windows/desktop/Controls/bcm-setnote) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente define la variable, *m_cmdLink*, que se usa para obtener acceso mediante programación el control de vínculo de comando. Esta variable se usa en el ejemplo siguiente.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente establece el texto de nota para el control de vínculo de comando.

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

##  <a name="setsplitglyph"></a>  CButton::SetSplitGlyph

Asocia un glifo especificado con el control de botón de división actual.

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*chGlyph*|[in] Un carácter que especifica el glifo que se usará como la flecha de lista desplegable del botón de división.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use este método solo con los controles que tienen el estilo BS_SPLITBUTTON o BS_DEFSPLITBUTTON del botón.

Un glifo es la representación física de un carácter en una fuente concreta. El *chGlyph* parámetro no se utiliza como el glifo, pero en su lugar se utiliza para seleccionar un glifo de un conjunto de glifos definido por el sistema. El glifo de flecha de lista desplegable predeterminado especificado por un carácter '6' y parece el carácter Unicode de triángulo hacia abajo negro (25BC).

Este método inicializa la `mask` miembro de un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) estructura con la marca BCSIF_GLYPH y `himlGlyph` miembro con el *chGlyph* parámetro y, a continuación, envía que estructura en el [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) mensaje que se describe en el SDK de Windows.

##  <a name="setsplitimagelist"></a>  CButton::SetSplitImageList

Asocia un [lista de imágenes](../../mfc/reference/cimagelist-class.md) con el control de botón de división actual.

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pSplitImageList*|[in] Puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto que se va a asignar al control de botón de división actual.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use este método solo con los controles cuyo estilo de botón es BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Este método inicializa la `mask` miembro de un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) estructura con la marca BCSIF_IMAGE y `himlGlyph` miembro con el *pSplitImageList* parámetro y, a continuación, envía esa estructura en el [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) mensaje que se describe en el SDK de Windows.

##  <a name="setsplitinfo"></a>  CButton::SetSplitInfo

Especifica los parámetros que determinan cómo Windows dibuja el control de botón de división actual.

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pInfo*|[in] Puntero a un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) estructura que define el control de botón de división actual.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use este método solo con los controles cuyo estilo de botón es BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Este método envía el [BCM_SETSPLITINFO](/windows/desktop/Controls/bcm-setsplitinfo) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente define la variable, `m_splitButton`, que se usa para obtener acceso mediante programación el control de botón de expansión.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se cambia el glifo que se usa para la flecha de lista desplegable del botón de división. En el ejemplo se sustituye por un glifo de triángulo hacia arriba para el glifo de triángulo hacia abajo de forma predeterminada. El glifo que se muestra depende del carácter que se especifique en el `himlGlyph` miembro de la `BUTTON_SPLITINFO` estructura. Se especifica el glifo de triángulo hacia abajo por un carácter ' 6 'y el glifo de triángulo hacia arriba se especifica mediante un carácter ' 5'. Para la comparación, vea el método de conveniencia [CButton::SetSplitGlyph](#setsplitglyph).

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

##  <a name="setsplitsize"></a>  CButton::SetSplitSize

Establece el rectángulo delimitador del componente de lista desplegable del control de botón de división actual.

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pSize*|[in] Puntero a un [tamaño](https://msdn.microsoft.com/library/windows/desktop/dd145106) estructura que describe un rectángulo delimitador.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use este método solo con los controles cuyo estilo de botón es BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Cuando se expande el control de botón de expansión, puede mostrar un componente de la lista desplegable, como un control de lista o un control de paginación. Este método especifica el tamaño del rectángulo delimitador que contiene el componente de la lista desplegable.

Este método inicializa la `mask` miembro de un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) estructura con la marca BCSIF_SIZE y `size` miembro con el *pSize* parámetro y, a continuación, envía a los que la estructura en el [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) mensaje que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente define la variable, `m_splitButton`, que se usa para obtener acceso mediante programación el control de botón de expansión. Esta variable se usa en el ejemplo siguiente.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se duplica el tamaño de la flecha de lista desplegable del botón de división.

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

##  <a name="setsplitstyle"></a>  CButton::SetSplitStyle

Establece el estilo del control de botón de división actual.

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*uSplitStyle*|[in] Una combinación bit a bit de los estilos de botón de división. Para obtener más información, consulte el `uSplitStyle` miembro de la [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) estructura.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use este método solo con los controles cuyo estilo de botón es BS_SPLITBUTTON o BS_DEFSPLITBUTTON.

Los estilos de botón de división especifican la alineación, la relación de aspecto y el formato gráfico con el que Windows dibuja un icono de botón de división. Para obtener más información, consulte el `uSplitStyle` miembro de la [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) estructura.

Este método inicializa la `mask` miembro de un [BUTTON_SPLITINFO](/windows/desktop/api/commctrl/ns-commctrl-tagbutton_splitinfo) estructura con la marca BCSIF_STYLE y `uSplitStyle` miembro con el *uSplitStyle* parámetro y, a continuación, envía que estructura en el [BCM_GETSPLITINFO](/windows/desktop/Controls/bcm-getsplitinfo) mensaje que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente define la variable, `m_splitButton`, que se usa para obtener acceso mediante programación el control de botón de expansión.

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente establece el estilo de la flecha de lista desplegable del botón de división. El estilo BCSS_ALIGNLEFT muestra la flecha situada a la izquierda del botón y el estilo BCSS_STRETCH conserva las proporciones de la flecha de lista desplegable cuando cambia el tamaño del botón.

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

##  <a name="setstate"></a>  CButton::SetState

Establece si un control de botón está resaltado o no.

```
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>Parámetros

*bHighlight*<br/>
Especifica si el botón está resaltado. Un valor distinto de cero, resalta el botón; un valor de 0, quita cualquier resaltado.

### <a name="remarks"></a>Comentarios

Resaltado afecta a la parte exterior de un control de botón. No tiene ningún efecto en el estado de activación de un botón de radio o casilla.

Un control de botón se resalta automáticamente cuando el usuario hace clic y mantiene presionado el botón primario del mouse. El resaltado se quita cuando el usuario suelta el botón del mouse.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

##  <a name="settextmargin"></a>  CButton::SetTextMargin

Llame a este método para establecer el margen del texto de la `CButton` objeto.

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>Parámetros

*pmargin*<br/>
Un puntero al margen de texto nuevo.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad del mensaje BCM_SETTEXTMARGIN, como se describe en el [botones](https://msdn.microsoft.com/library/windows/desktop/bb775943) sección del SDK de Windows.

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CComboBox (clase)](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit (clase)](../../mfc/reference/cedit-class.md)<br/>
[CListBox (clase)](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar (clase)](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic (clase)](../../mfc/reference/cstatic-class.md)<br/>
[CBitmapButton (clase)](../../mfc/reference/cbitmapbutton-class.md)<br/>
[CDialog (clase)](../../mfc/reference/cdialog-class.md)
