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
ms.openlocfilehash: fc0164b2d0046ca2d36291696dd6137a9fcef069
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447431"
---
# <a name="cstatic-class"></a>Clase CStatic

Proporciona la funcionalidad de un control estático de Windows.

## <a name="syntax"></a>Sintaxis

```
class CStatic : public CWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStatic::CStatic](#cstatic)|Construye un objeto `CStatic`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStatic:: Create](#create)|Crea el control estático de Windows y lo adjunta al objeto `CStatic`.|
|[CStatic::D rawItem](#drawitem)|Invalide para dibujar un control estático dibujado por el propietario.|
|[CStatic::GetBitmap](#getbitmap)|Recupera el identificador del mapa de bits previamente establecido con [SetBitmap](#setbitmap).|
|[CStatic::GetCursor](#getcursor)|Recupera el identificador de la imagen de cursor previamente establecida con [setCursor](#setcursor).|
|[CStatic::GetEnhMetaFile](#getenhmetafile)|Recupera el identificador del metarchivo mejorado previamente establecido con [SetEnhMetaFile](#setenhmetafile).|
|[CStatic:: GetIcon](#geticon)|Recupera el identificador del icono establecido previamente con [SetIcon](#seticon).|
|[CStatic::SetBitmap](#setbitmap)|Especifica un mapa de bits que se va a mostrar en el control estático.|
|[CStatic::SetCursor](#setcursor)|Especifica una imagen de cursor que se va a mostrar en el control estático.|
|[CStatic::SetEnhMetaFile](#setenhmetafile)|Especifica un metarchivo mejorado que se va a mostrar en el control estático.|
|[CStatic::SetIcon](#seticon)|Especifica un icono que se va a mostrar en el control estático.|

## <a name="remarks"></a>Observaciones

Un control estático muestra una cadena de texto, un cuadro, un rectángulo, un icono, un cursor, un mapa de bits o un metarchivo mejorado. Se puede utilizar para etiquetar, mostrar o separar otros controles. Normalmente, un control estático no toma ninguna entrada y no proporciona ningún resultado; sin embargo, puede notificar a su elemento primario de los clics del mouse si se crea con SS_NOTIFY estilo.

Cree un control estático en dos pasos. En primer lugar, llame al constructor para construir el `CStatic` objeto y, a continuación, llame a la función miembro [Create](#create) para crear el control estático y adjuntarlo al objeto `CStatic`.

Si crea un objeto de `CStatic` dentro de un cuadro de diálogo (a través de un recurso de cuadro de diálogo), el objeto de `CStatic` se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.

Si crea un objeto de `CStatic` dentro de una ventana, es posible que también tenga que destruirlo. Un objeto `CStatic` creado en la pila dentro de una ventana se destruye automáticamente. Si crea el objeto de `CStatic` en el montón mediante la **nueva** función, debe llamar a **Delete** en el objeto para destruirlo cuando haya terminado.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="create"></a>CStatic:: Create

Crea el control estático de Windows y lo adjunta al objeto `CStatic`.

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
Especifica el texto que se va a colocar en el control. Si es NULL, no habrá texto visible.

*dwStyle*<br/>
Especifica el estilo de ventana del control estático. Aplique cualquier combinación de [estilos de control estáticos](../../mfc/reference/styles-used-by-mfc.md#static-styles) al control.

*Rect*<br/>
Especifica la posición y el tamaño del control estático. Puede ser una estructura de `RECT` o un objeto `CRect`.

*pParentWnd*<br/>
Especifica la `CStatic` ventana primaria, normalmente un objeto `CDialog`. No debe ser NULL.

*nID*<br/>
Especifica el identificador de control del control estático.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Construya un objeto `CStatic` en dos pasos. En primer lugar, llame al constructor `CStatic`y, a continuación, llame a `Create`, que crea el control estático de Windows y lo adjunta al objeto `CStatic`.

Aplique los siguientes [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) a un control estático:

- WS_CHILD siempre

- WS_VISIBLE normalmente

- WS_DISABLED raramente

Si va a mostrar un mapa de bits, un cursor, un icono o un metarchivo en el control estático, deberá aplicar uno de los siguientes [estilos estáticos](../../mfc/reference/styles-used-by-mfc.md#static-styles):

- SS_BITMAP usar este estilo para los mapas de bits.

- SS_ICON usar este estilo para los cursores e iconos.

- SS_ENHMETAFILE usar este estilo para los metaarchivos mejorados.

En el caso de los cursores, mapas de bits o iconos, puede que también desee usar el siguiente estilo:

- SS_CENTERIMAGE usar para centrar la imagen en el control estático.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

##  <a name="cstatic"></a>CStatic::CStatic

Construye un objeto `CStatic`.

```
CStatic();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

##  <a name="drawitem"></a>CStatic::D rawItem

Lo llama el marco de trabajo para dibujar un control estático dibujado por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Puntero a una estructura [drawitemstruct (](/windows/win32/api/winuser/ns-winuser-drawitemstruct) . La estructura contiene información sobre el elemento que se va a dibujar y el tipo de dibujo necesario.

### <a name="remarks"></a>Observaciones

Invalide esta función para implementar el dibujo de un objeto de `CStatic` dibujado por el propietario (el control tiene el estilo SS_OWNERDRAW).

##  <a name="getbitmap"></a>CStatic::GetBitmap

Obtiene el identificador del mapa de bits, previamente establecido con [SetBitmap](#setbitmap), que está asociado a `CStatic`.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del mapa de bits actual o NULL si no se ha establecido ningún mapa de bits.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="getcursor"></a>CStatic::GetCursor

Obtiene el identificador del cursor, previamente establecido con [setCursor](#setcursor), que está asociado a `CStatic`.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Valor devuelto

Identificador del cursor actual o NULL si no se ha establecido ningún cursor.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="getenhmetafile"></a>CStatic::GetEnhMetaFile

Obtiene el identificador del metarchivo mejorado, previamente establecido con [SetEnhMetafile](#setenhmetafile), que está asociado a `CStatic`.

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del metarchivo mejorado actual o NULL si no se ha establecido ningún metarchivo mejorado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="geticon"></a>CStatic:: GetIcon

Obtiene el identificador del icono, previamente establecido con [SetIcon](#seticon), que está asociado a `CStatic`.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del icono actual o NULL si no se ha establecido ningún icono.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

##  <a name="setbitmap"></a>CStatic::SetBitmap

Asocia un nuevo mapa de bits al control estático.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parámetros

*hBitmap*<br/>
Identificador del mapa de bits que se va a dibujar en el control estático.

### <a name="return-value"></a>Valor devuelto

Identificador del mapa de bits que se asoció previamente al control estático o NULL si no se asoció ningún mapa de bits al control estático.

### <a name="remarks"></a>Observaciones

El mapa de bits se dibujará automáticamente en el control estático. De forma predeterminada, se dibujará en la esquina superior izquierda y se cambiará el tamaño del control estático al tamaño del mapa de bits.

Puede usar varios estilos de ventana y de control estáticos, entre los que se incluyen los siguientes:

- SS_BITMAP usar este estilo siempre para los mapas de bits.

- SS_CENTERIMAGE usar para centrar la imagen en el control estático. Si la imagen es mayor que el control estático, se recortará. Si es menor que el control estático, el espacio vacío alrededor de la imagen se rellenará con el color del píxel situado en la esquina superior izquierda del mapa de bits.

- MFC proporciona la clase `CBitmap`, que puede utilizar cuando tenga que hacer más con una imagen de mapa de bits que simplemente llamar a la función de Win32 `LoadBitmap`. `CBitmap`, que contiene un tipo de objeto GDI, se usa a menudo en cooperación con `CStatic`, que es una clase `CWnd` que se usa para mostrar un objeto gráfico como control estático.

`CImage` es una clase ATL/MFC que le permite trabajar más fácilmente con mapas de bits independientes del dispositivo (DIB). Para obtener más información, vea [CImage (clase](../../atl-mfc-shared/reference/cimage-class.md)).

- El uso típico es dar a `CStatic::SetBitmap` un objeto GDI devuelto por el operador HBITMAP de un objeto `CBitmap` o `CImage`. El código para hacerlo es similar al de la línea siguiente.

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```

En el ejemplo siguiente se crean dos objetos `CStatic` en el montón. A continuación, carga uno con un mapa de bits del sistema mediante `CBitmap::LoadOEMBitmap` y el otro desde un archivo mediante `CImage::Load`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="setcursor"></a>CStatic::SetCursor

Asocia una nueva imagen de cursor al control estático.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parámetros

*hCursor*<br/>
Identificador del cursor que se va a dibujar en el control estático.

### <a name="return-value"></a>Valor devuelto

Identificador del cursor previamente asociado al control estático o NULL si no hay ningún cursor asociado al control estático.

### <a name="remarks"></a>Observaciones

El cursor se dibujará automáticamente en el control estático. De forma predeterminada, se dibujará en la esquina superior izquierda y se cambiará el tamaño del control estático al tamaño del cursor.

Puede usar varios estilos de ventana y de control estático, entre los que se incluyen los siguientes:

- SS_ICON usar este estilo siempre para los cursores e iconos.

- SS_CENTERIMAGE usar para centrarse en el control estático. Si la imagen es mayor que el control estático, se recortará. Si es menor que el control estático, el espacio vacío alrededor de la imagen se rellenará con el color de fondo del control estático.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="setenhmetafile"></a>CStatic::SetEnhMetaFile

Asocia una nueva imagen de metarchivo mejorado con el control estático.

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>Parámetros

*hMetaFile*<br/>
Identificador del metarchivo mejorado que se va a dibujar en el control estático.

### <a name="return-value"></a>Valor devuelto

Identificador del metarchivo mejorado previamente asociado al control estático o NULL si no se asoció un metarchivo mejorado al control estático.

### <a name="remarks"></a>Observaciones

El metarchivo mejorado se dibujará automáticamente en el control estático. El metarchivo mejorado se escala para ajustarse al tamaño del control estático.

Puede usar varios estilos de ventana y de control estático, entre los que se incluyen los siguientes:

- SS_ENHMETAFILE usar este estilo siempre para los metaarchivos mejorados.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="seticon"></a>CStatic::SetIcon

Asocia una nueva imagen de icono al control estático.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parámetros

*hIcon*<br/>
Identificador del icono que se va a dibujar en el control estático.

### <a name="return-value"></a>Valor devuelto

Identificador del icono asociado anteriormente al control estático o NULL si no hay ningún icono asociado al control estático.

### <a name="remarks"></a>Observaciones

El icono se dibujará automáticamente en el control estático. De forma predeterminada, se dibujará en la esquina superior izquierda y se cambiará el tamaño del control estático al tamaño del icono.

Puede usar varios estilos de ventana y de control estático, entre los que se incluyen los siguientes:

- SS_ICON usar este estilo siempre para los cursores e iconos.

- SS_CENTERIMAGE usar para centrarse en el control estático. Si la imagen es mayor que el control estático, se recortará. Si es menor que el control estático, el espacio vacío alrededor de la imagen se rellenará con el color de fondo del control estático.

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
[CDialog (clase)](../../mfc/reference/cdialog-class.md)
