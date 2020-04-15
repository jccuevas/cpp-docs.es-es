---
title: Clase CStatic
ms.date: 11/04/2016
f1_keywords:
- CStatic
- AFXWIN/CStatic
- AFXWIN/CStatic::CStatic
- AFXWIN/CStatic::Create
- AFXWIN/CStatic::DrawItem
- AFXWIN/CStatic::GetBitmap
- AFXWIN/CStatic::GetCursor
- AFXWIN/CStatic::GetEnhMetaFile
- AFXWIN/CStatic::GetIcon
- AFXWIN/CStatic::SetBitmap
- AFXWIN/CStatic::SetCursor
- AFXWIN/CStatic::SetEnhMetaFile
- AFXWIN/CStatic::SetIcon
helpviewer_keywords:
- CStatic [MFC], CStatic
- CStatic [MFC], Create
- CStatic [MFC], DrawItem
- CStatic [MFC], GetBitmap
- CStatic [MFC], GetCursor
- CStatic [MFC], GetEnhMetaFile
- CStatic [MFC], GetIcon
- CStatic [MFC], SetBitmap
- CStatic [MFC], SetCursor
- CStatic [MFC], SetEnhMetaFile
- CStatic [MFC], SetIcon
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
ms.openlocfilehash: e5c3705c0aa2fd90e73cb54ba5a97c252ed2cf83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371640"
---
# <a name="cstatic-class"></a>Clase CStatic

Proporciona la funcionalidad de un control estático de Windows.

## <a name="syntax"></a>Sintaxis

```
class CStatic : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStatic::CStatic](#cstatic)|Construye un objeto `CStatic`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStatic::Crear](#create)|Crea el control estático de Windows `CStatic` y lo adjunta al objeto.|
|[CStatic::DrawItem](#drawitem)|Reemplazar para dibujar un control estático dibujado por el propietario.|
|[CStatic::GetBitmap](#getbitmap)|Recupera el identificador del mapa de bits establecido anteriormente con [SetBitmap](#setbitmap).|
|[CStatic::GetCursor](#getcursor)|Recupera el identificador de la imagen del cursor previamente establecida con [SetCursor](#setcursor).|
|[CStatic::GetEnhMetaFile](#getenhmetafile)|Recupera el identificador del metarchivo mejorado establecido anteriormente con [SetEnhMetaFile](#setenhmetafile).|
|[CStatic::GetIcon](#geticon)|Recupera el identificador del icono establecido previamente con [SetIcon](#seticon).|
|[CStatic::SetBitmap](#setbitmap)|Especifica un mapa de bits que se mostrará en el control estático.|
|[CStatic::SetCursor](#setcursor)|Especifica una imagen de cursor que se mostrará en el control estático.|
|[CStatic::SetEnhMetaFile](#setenhmetafile)|Especifica un metarchivo mejorado que se mostrará en el control estático.|
|[CStatic::SetIcon](#seticon)|Especifica un icono que se mostrará en el control estático.|

## <a name="remarks"></a>Observaciones

Un control estático muestra una cadena de texto, cuadro, rectángulo, icono, cursor, mapa de bits o metarchivo mejorado. Se puede utilizar para etiquetar, encajonar o separar otros controles. Un control estático normalmente no toma ninguna entrada y no proporciona ninguna salida; sin embargo, puede notificar a su elemento primario de los clics del ratón si se crea con SS_NOTIFY estilo.

Cree un control estático en dos pasos. En primer lugar, llame `CStatic` al constructor para construir el objeto y, a `CStatic` continuación, llame a la [Create](#create) función miembro para crear el control estático y adjuntarlo al objeto.

Si crea `CStatic` un objeto dentro de un cuadro `CStatic` de diálogo (a través de un recurso de cuadro de diálogo), el objeto se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.

Si crea `CStatic` un objeto dentro de una ventana, es posible que también deba destruirlo. Un `CStatic` objeto creado en la pila dentro de una ventana se destruye automáticamente. Si crea `CStatic` el objeto en el montón mediante la **nueva** función, debe llamar a **delete** en el objeto para destruirlo cuando haya terminado con él.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cstaticcreate"></a><a name="create"></a>CStatic::Crear

Crea el control estático de Windows `CStatic` y lo adjunta al objeto.

```
virtual BOOL Create(
    LPCTSTR lpszText,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID = 0xffff);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
Especifica el texto que se va a colocar en el control. Si NULL, no habrá texto visible.

*dwStyle*<br/>
Especifica el estilo de ventana del control estático. Aplique cualquier combinación de estilos de [control estáticos](../../mfc/reference/styles-used-by-mfc.md#static-styles) al control.

*Rect*<br/>
Especifica la posición y el tamaño del control estático. Puede ser una `RECT` estructura `CRect` o un objeto.

*pParentWnd*<br/>
Especifica la `CStatic` ventana primaria, `CDialog` normalmente un objeto. No debe ser NULL.

*nID*<br/>
Especifica el identificador de control del control estático.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Construir `CStatic` un objeto en dos pasos. En primer lugar, llame al constructor `CStatic`y, a continuación, llame a `Create`, que crea el control estático de Windows y lo adjunta al `CStatic` objeto.

Aplique los siguientes [estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles) de ventana a un control estático:

- WS_CHILD Siempre

- WS_VISIBLE Por lo general

- WS_DISABLED Rara vez

Si va a mostrar un mapa de bits, cursor, icono o metarchivo en el control estático, deberá aplicar uno de los siguientes [estilos estáticos:](../../mfc/reference/styles-used-by-mfc.md#static-styles)

- SS_BITMAP Usar este estilo para mapas de bits.

- SS_ICON Utilice este estilo para cursores e iconos.

- SS_ENHMETAFILE Utilice este estilo para obtener metarchivos mejorados.

Para cursores, mapas de bits o iconos, es posible que también desee utilizar el siguiente estilo:

- SS_CENTERIMAGE Se utiliza para centrar la imagen en el control estático.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

## <a name="cstaticcstatic"></a><a name="cstatic"></a>CStatic::CStatic

Construye un objeto `CStatic`.

```
CStatic();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

## <a name="cstaticdrawitem"></a><a name="drawitem"></a>CStatic::DrawItem

Llamado por el marco de trabajo para dibujar un control estático dibujado por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Un puntero a un [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) estructura. La estructura contiene información sobre el elemento que se va a dibujar y el tipo de dibujo necesario.

### <a name="remarks"></a>Observaciones

Reemplace esta función para implementar `CStatic` el dibujo de un objeto dibujado por el propietario (el control tiene el estilo SS_OWNERDRAW).

## <a name="cstaticgetbitmap"></a><a name="getbitmap"></a>CStatic::GetBitmap

Obtiene el identificador del mapa de bits, establecido previamente con [SetBitmap](#setbitmap), que está asociado a `CStatic`.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Valor devuelto

Un identificador para el mapa de bits actual, o NULL si no se ha establecido ningún mapa de bits.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

## <a name="cstaticgetcursor"></a><a name="getcursor"></a>CStatic::GetCursor

Obtiene el identificador del cursor, establecido previamente con `CStatic` [SetCursor](#setcursor), que está asociado con .

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Valor devuelto

Un identificador del cursor actual, o NULL si no se ha establecido ningún cursor.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

## <a name="cstaticgetenhmetafile"></a><a name="getenhmetafile"></a>CStatic::GetEnhMetaFile

Obtiene el identificador del metarchivo mejorado, establecido anteriormente con [SetEnhMetafile](#setenhmetafile), que está asociado a `CStatic`.

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>Valor devuelto

Un identificador del metarchivo mejorado actual, o NULL si no se ha establecido ningún metarchivo mejorado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

## <a name="cstaticgeticon"></a><a name="geticon"></a>CStatic::GetIcon

Obtiene el identificador del icono, establecido previamente con [SetIcon](#seticon), que está asociado con `CStatic`.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del icono actual o NULL si no se ha establecido ningún icono.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="cstaticsetbitmap"></a><a name="setbitmap"></a>CStatic::SetBitmap

Asocia un nuevo mapa de bits con el control estático.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parámetros

*hBitmap*<br/>
Control del mapa de bits que se va a dibujar en el control estático.

### <a name="return-value"></a>Valor devuelto

El identificador del mapa de bits que se asoció anteriormente con el control estático, o NULL si no se asoció ningún mapa de bits con el control estático.

### <a name="remarks"></a>Observaciones

El mapa de bits se dibujará automáticamente en el control estático. De forma predeterminada, se dibujará en la esquina superior izquierda y el control estático cambiará de tamaño al tamaño del mapa de bits.

Puede utilizar varios estilos de control estático y de ventana, incluidos los siguientes:

- SS_BITMAP Utilice este estilo siempre para mapas de bits.

- SS_CENTERIMAGE Se utiliza para centrar la imagen en el control estático. Si la imagen es mayor que el control estático, se recortará. Si es menor que el control estático, el espacio vacío alrededor de la imagen se rellenará con el color del píxel en la esquina superior izquierda del mapa de bits.

- MFC proporciona `CBitmap`la clase , que puede usar cuando tiene que hacer más con `LoadBitmap`una imagen de mapa de bits que simplemente llamar a la función Win32 . `CBitmap`, que contiene un tipo de objeto GDI, se utiliza a menudo en cooperación con `CStatic`, que es una `CWnd` clase que se utiliza para mostrar un objeto gráfico como un control estático.

`CImage`es una clase ATL/MFC que le permite trabajar más fácilmente con mapas de bits independientes del dispositivo (DIB). Para obtener más información, vea [CImage (Clase)](../../atl-mfc-shared/reference/cimage-class.md).

- El uso típico `CStatic::SetBitmap` es proporcionar un objeto GDI devuelto `CBitmap` por `CImage` el operador HBITMAP de un objeto o. El código para hacerlo se asemeja a la siguiente línea.

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```

En el ejemplo `CStatic` siguiente se crean dos objetos en el montón. A continuación, carga uno `CBitmap::LoadOEMBitmap` con un mapa de `CImage::Load`bits del sistema utilizando y el otro de un archivo utilizando .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

## <a name="cstaticsetcursor"></a><a name="setcursor"></a>CStatic::SetCursor

Asocia una nueva imagen de cursor con el control estático.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parámetros

*hCursor*<br/>
Control del cursor que se va a dibujar en el control estático.

### <a name="return-value"></a>Valor devuelto

El identificador del cursor asociado anteriormente con el control estático, o NULL si no se asoció ningún cursor con el control estático.

### <a name="remarks"></a>Observaciones

El cursor se dibujará automáticamente en el control estático. De forma predeterminada, se dibujará en la esquina superior izquierda y el control estático cambiará de tamaño al tamaño del cursor.

Puede utilizar varios estilos de control estático y de ventana, incluidos los siguientes:

- SS_ICON Utilice este estilo siempre para cursores e iconos.

- SS_CENTERIMAGE Se utiliza para centrar en el control estático. Si la imagen es mayor que el control estático, se recortará. Si es menor que el control estático, el espacio vacío alrededor de la imagen se rellenará con el color de fondo del control estático.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

## <a name="cstaticsetenhmetafile"></a><a name="setenhmetafile"></a>CStatic::SetEnhMetaFile

Asocia una nueva imagen de metarchivo mejorada con el control estático.

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>Parámetros

*hMetaFile*<br/>
Control del metarchivo mejorado que se va a dibujar en el control estático.

### <a name="return-value"></a>Valor devuelto

El identificador del metarchivo mejorado asociado anteriormente con el control estático, o NULL si no se asoció ningún metarchivo mejorado con el control estático.

### <a name="remarks"></a>Observaciones

El metarchivo mejorado se dibujará automáticamente en el control estático. El metarchivo mejorado se escala para ajustarse al tamaño del control estático.

Puede utilizar varios estilos de control estático y de ventana, incluidos los siguientes:

- SS_ENHMETAFILE Utilice este estilo siempre para metarchivos mejorados.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

## <a name="cstaticseticon"></a><a name="seticon"></a>CStatic::SetIcon

Asocia una nueva imagen de icono con el control estático.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parámetros

*hIcon*<br/>
Control del icono que se va a dibujar en el control estático.

### <a name="return-value"></a>Valor devuelto

El identificador del icono asociado anteriormente con el control estático, o NULL si no se asoció ningún icono con el control estático.

### <a name="remarks"></a>Observaciones

El icono se dibujará automáticamente en el control estático. De forma predeterminada, se dibujará en la esquina superior izquierda y el control estático cambiará de tamaño al tamaño del icono.

Puede utilizar varios estilos de control estático y de ventana, incluidos los siguientes:

- SS_ICON Utilice este estilo siempre para cursores e iconos.

- SS_CENTERIMAGE Se utiliza para centrar en el control estático. Si la imagen es mayor que el control estático, se recortará. Si es menor que el control estático, el espacio vacío alrededor de la imagen se rellenará con el color de fondo del control estático.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="see-also"></a>Consulte también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CButton (clase)](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox (clase)](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox (clase)](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar (clase)](../../mfc/reference/cscrollbar-class.md)<br/>
[Clase CDialog](../../mfc/reference/cdialog-class.md)
