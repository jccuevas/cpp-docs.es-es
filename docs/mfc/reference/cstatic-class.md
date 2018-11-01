---
title: CStatic (clase)
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
ms.openlocfilehash: 622172d369818a7a503945bcd3cf064662f38266
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576714"
---
# <a name="cstatic-class"></a>CStatic (clase)

Proporciona la funcionalidad de un control estático de Windows.

## <a name="syntax"></a>Sintaxis

```
class CStatic : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CStatic::CStatic](#cstatic)|Construye un objeto `CStatic`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CStatic::Create](#create)|Crea el control estático de Windows y lo adjunta a la `CStatic` objeto.|
|[CStatic::DrawItem](#drawitem)|Invalide para dibujar un control estático dibujado por el propietario.|
|[CStatic::GetBitmap](#getbitmap)|Recupera el identificador del mapa de bits establecido previamente con [SetBitmap](#setbitmap).|
|[CStatic::GetCursor](#getcursor)|Recupera el identificador de la imagen del cursor establecido previamente con [SetCursor](#setcursor).|
|[CStatic::GetEnhMetaFile](#getenhmetafile)|Recupera el identificador del metarchivo mejorado establecido previamente con [SetEnhMetaFile](#setenhmetafile).|
|[CStatic::GetIcon](#geticon)|Recupera el identificador del icono establecido previamente con [SetIcon](#seticon).|
|[CStatic::SetBitmap](#setbitmap)|Especifica un mapa de bits que se mostrará en el control estático.|
|[CStatic::SetCursor](#setcursor)|Especifica una imagen de cursor que se mostrará en el control estático.|
|[CStatic::SetEnhMetaFile](#setenhmetafile)|Especifica un metarchivo mejorado para mostrarse en el control estático.|
|[CStatic::SetIcon](#seticon)|Especifica el icono que se muestra en el control estático.|

## <a name="remarks"></a>Comentarios

Un control estático muestra una cadena de texto, cuadro, rectángulo, icono, cursor, mapa de bits o metarchivo mejorado. Se puede usar para etiquetar, cuadro o separar otros controles. Un control estático normalmente toma ninguna entrada y no proporciona ningún resultado; Sin embargo, puede notificar a su elemento primario de clics del mouse si se ha creado con estilo SS_NOTIFY.

Crear un control estático en dos pasos. En primer lugar, llame al constructor para construir el `CStatic` objeto y, después, llame a la [crear](#create) función miembro para crear el control estático y adjuntarlo a la `CStatic` objeto.

Si creas un `CStatic` objeto dentro de un cuadro de diálogo (a través de un recurso de cuadro de diálogo), el `CStatic` objeto se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.

Si creas un `CStatic` objeto dentro de una ventana, es posible que también deba destruirlo. Un `CStatic` automáticamente se destruye el objeto creado en la pila dentro de una ventana. Si crea el `CStatic` objeto en el montón mediante el uso de la **nueva** función, debe llamar a **eliminar** en el objeto que lo destruirá cuando haya terminado con él.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="create"></a>  CStatic::Create

Crea el control estático de Windows y lo adjunta a la `CStatic` objeto.

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
Especifica el texto que se va a colocar en el control. Si es NULL, no estará visible.

*dwStyle*<br/>
Especifica el estilo de ventana del control estático. Aplicar cualquier combinación de [estilos de control estático](../../mfc/reference/styles-used-by-mfc.md#static-styles) al control.

*Rect*<br/>
Especifica la posición y el tamaño del control estático. Puede ser un `RECT` estructura o un `CRect` objeto.

*pParentWnd*<br/>
Especifica el `CStatic` ventana primaria, normalmente un `CDialog` objeto. No debe ser NULL.

*nID*<br/>
Especifica el identificador de control. del control estático

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Construir un `CStatic` objeto en dos pasos. En primer lugar, llame al constructor `CStatic`y, a continuación, llame a `Create`, que crea el control estático de Windows y lo adjunta a la `CStatic` objeto.

Aplique el siguiente [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) a un control estático:

- WS_CHILD siempre

- WS_VISIBLE normalmente

- WS_DISABLED rara vez

Si va a mostrar un mapa de bits, cursores, icono o metarchivo en el control estático, se deberá aplicar uno de los siguientes [estilos estáticos](../../mfc/reference/styles-used-by-mfc.md#static-styles):

- SS_BITMAP utilizar este estilo para los mapas de bits.

- SS_ICON utilizar este estilo para iconos y cursores.

- SS_ENHMETAFILE utilizar este estilo de metarchivos mejorados.

Para los cursores, mapas de bits o iconos, también puede usar el siguiente estilo:

- SS_CENTERIMAGE uso para centrar la imagen en el control estático.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

##  <a name="cstatic"></a>  CStatic::CStatic

Construye un objeto `CStatic`.

```
CStatic();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

##  <a name="drawitem"></a>  CStatic::DrawItem

Lo llama el marco de trabajo para dibujar un control estático dibujado por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Un puntero a un [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) estructura. La estructura contiene información sobre el elemento que se va a dibujar y el tipo de dibujo necesaria.

### <a name="remarks"></a>Comentarios

Reemplace esta función para implementar el dibujo para dibujar un `CStatic` objeto (el control tiene el estilo SS_OWNERDRAW).

##  <a name="getbitmap"></a>  CStatic::GetBitmap

Obtiene el identificador del mapa de bits, establecido previamente con [SetBitmap](#setbitmap), que está asociado con `CStatic`.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Valor devuelto

Un identificador para el mapa de bits actual, o NULL si no se ha establecido ningún mapa de bits.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="getcursor"></a>  CStatic::GetCursor

Obtiene el identificador del cursor establecido previamente con [SetCursor](#setcursor), que está asociado con `CStatic`.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Valor devuelto

Identificador de cursor actual, o NULL si no se ha establecido ningún cursor.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="getenhmetafile"></a>  CStatic::GetEnhMetaFile

Obtiene el identificador del metarchivo mejorado, establecido previamente con [SetEnhMetafile](#setenhmetafile), que está asociado con `CStatic`.

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del metarchivo mejorado actual, o NULL si no se ha establecido ningún metarchivo mejorado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="geticon"></a>  CStatic::GetIcon

Obtiene el identificador del icono, establecido previamente con [SetIcon](#seticon), que está asociado con `CStatic`.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del icono actual, o NULL si no se ha establecido ningún icono.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

##  <a name="setbitmap"></a>  CStatic::SetBitmap

Asocia un nuevo mapa de bits con el control estático.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parámetros

*hBitmap*<br/>
Identificador del mapa de bits para dibujar en el control estático.

### <a name="return-value"></a>Valor devuelto

El identificador del mapa de bits que se asoció anteriormente con el control estático, o NULL si se ha asociado con el control estático ningún mapa de bits.

### <a name="remarks"></a>Comentarios

El mapa de bits se dibujarán automáticamente en el control estático. De forma predeterminada, se dibujará en la esquina superior izquierda y el control estático se ajustará al tamaño del mapa de bits.

Puede usar distintos de ventana y estilos de control estático, incluidos los siguientes:

- SS_BITMAP usan este estilo siempre para los mapas de bits.

- SS_CENTERIMAGE uso para centrar la imagen en el control estático. Si la imagen es mayor que el control estático, se recortará. Si es menor que el control estático, se rellenará el espacio vacío alrededor de la imagen mediante el color del píxel en la esquina superior izquierda del mapa de bits.

- MFC proporciona la clase `CBitmap`, que se puede usar una vez más con una imagen de mapa de bits que llamaremos Win32 funcionando `LoadBitmap`. `CBitmap`, que contiene un tipo de objeto GDI, se usa a menudo en cooperación con `CStatic`, que es un `CWnd` clase que se utiliza para mostrar un objeto gráfico como un control estático.

`CImage` es una clase ATL/MFC que le permite trabajar fácilmente con los mapas de bits independientes del dispositivo (DIB). Para obtener más información, consulte [CImage (clase)](../../atl-mfc-shared/reference/cimage-class.md).

- Uso habitual consiste en dar `CStatic::SetBitmap` un objeto GDI devuelto por el operador de un HBITMAP un `CBitmap` o `CImage` objeto. El código para hacer esto es similar a la siguiente línea.

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```
En el ejemplo siguiente se crean dos `CStatic` objetos del montón. A continuación, carga uno con un mapa de bits del sistema con `CBitmap::LoadOEMBitmap` y otra de un archivo mediante `CImage::Load`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="setcursor"></a>  CStatic::SetCursor

Asocia una nueva imagen de cursor con el control estático.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parámetros

*hCursor*<br/>
Identificador del cursor para dibujar en el control estático.

### <a name="return-value"></a>Valor devuelto

El identificador del cursor asociado anteriormente con el control estático, o NULL si el cursor no se asoció con el control estático.

### <a name="remarks"></a>Comentarios

El cursor se dibujarán automáticamente en el control estático. De forma predeterminada, se dibujará en la esquina superior izquierda y el control estático se ajustará al tamaño del cursor.

Puede usar distintos ventana y estilos de control estático, incluidas las siguientes:

- SS_ICON usan este estilo siempre para iconos y cursores.

- SS_CENTERIMAGE uso para centrar en el control estático. Si la imagen es mayor que el control estático, se recortará. Si es menor que el control estático, el espacio vacío alrededor de la imagen se rellenará con el color de fondo del control estático.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="setenhmetafile"></a>  CStatic::SetEnhMetaFile

Asocia una nueva imagen de metarchivo mejorado el control estático.

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>Parámetros

*hMetaFile*<br/>
Identificador del metarchivo mejorado para dibujar en el control estático.

### <a name="return-value"></a>Valor devuelto

El identificador del metarchivo mejorado asociado anteriormente con el control estático, o NULL si se ha asociado con el control estático no metarchivo mejorado.

### <a name="remarks"></a>Comentarios

Metarchivo mejorado se dibujarán automáticamente en el control estático. Metarchivo mejorado se escala para ajustarse al tamaño del control estático.

Puede usar distintos ventana y estilos de control estático, incluidas las siguientes:

- SS_ENHMETAFILE Use siempre este estilo de metarchivos mejorados.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="seticon"></a>  CStatic::SetIcon

Asocia una nueva imagen de icono del control estático.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parámetros

*hIcon*<br/>
Identificador del icono que debe dibujarse en el control estático.

### <a name="return-value"></a>Valor devuelto

El identificador del icono asociado anteriormente con el control estático, o NULL si se ha asociado con el control estático ningún icono.

### <a name="remarks"></a>Comentarios

El icono se dibujarán automáticamente en el control estático. De forma predeterminada, se dibujará en la esquina superior izquierda y el control estático se ajustará al tamaño del icono.

Puede usar distintos ventana y estilos de control estático, incluidas las siguientes:

- SS_ICON usan este estilo siempre para iconos y cursores.

- SS_CENTERIMAGE uso para centrar en el control estático. Si la imagen es mayor que el control estático, se recortará. Si es menor que el control estático, el espacio vacío alrededor de la imagen se rellenará con el color de fondo del control estático.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CButton (clase)](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox (clase)](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit (clase)](../../mfc/reference/cedit-class.md)<br/>
[CListBox (clase)](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar (clase)](../../mfc/reference/cscrollbar-class.md)<br/>
[CDialog (clase)](../../mfc/reference/cdialog-class.md)
