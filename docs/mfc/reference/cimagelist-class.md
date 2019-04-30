---
title: CImageList (clase)
ms.date: 11/04/2016
f1_keywords:
- CImageList
- AFXCMN/CImageList
- AFXCMN/CImageList::CImageList
- AFXCMN/CImageList::Add
- AFXCMN/CImageList::Attach
- AFXCMN/CImageList::BeginDrag
- AFXCMN/CImageList::Copy
- AFXCMN/CImageList::Create
- AFXCMN/CImageList::DeleteImageList
- AFXCMN/CImageList::DeleteTempMap
- AFXCMN/CImageList::Detach
- AFXCMN/CImageList::DragEnter
- AFXCMN/CImageList::DragLeave
- AFXCMN/CImageList::DragMove
- AFXCMN/CImageList::DragShowNolock
- AFXCMN/CImageList::Draw
- AFXCMN/CImageList::DrawEx
- AFXCMN/CImageList::DrawIndirect
- AFXCMN/CImageList::EndDrag
- AFXCMN/CImageList::ExtractIcon
- AFXCMN/CImageList::FromHandle
- AFXCMN/CImageList::FromHandlePermanent
- AFXCMN/CImageList::GetBkColor
- AFXCMN/CImageList::GetDragImage
- AFXCMN/CImageList::GetImageCount
- AFXCMN/CImageList::GetImageInfo
- AFXCMN/CImageList::GetSafeHandle
- AFXCMN/CImageList::Read
- AFXCMN/CImageList::Remove
- AFXCMN/CImageList::Replace
- AFXCMN/CImageList::SetBkColor
- AFXCMN/CImageList::SetDragCursorImage
- AFXCMN/CImageList::SetImageCount
- AFXCMN/CImageList::SetOverlayImage
- AFXCMN/CImageList::Write
- AFXCMN/CImageList::m_hImageList
helpviewer_keywords:
- CImageList [MFC], CImageList
- CImageList [MFC], Add
- CImageList [MFC], Attach
- CImageList [MFC], BeginDrag
- CImageList [MFC], Copy
- CImageList [MFC], Create
- CImageList [MFC], DeleteImageList
- CImageList [MFC], DeleteTempMap
- CImageList [MFC], Detach
- CImageList [MFC], DragEnter
- CImageList [MFC], DragLeave
- CImageList [MFC], DragMove
- CImageList [MFC], DragShowNolock
- CImageList [MFC], Draw
- CImageList [MFC], DrawEx
- CImageList [MFC], DrawIndirect
- CImageList [MFC], EndDrag
- CImageList [MFC], ExtractIcon
- CImageList [MFC], FromHandle
- CImageList [MFC], FromHandlePermanent
- CImageList [MFC], GetBkColor
- CImageList [MFC], GetDragImage
- CImageList [MFC], GetImageCount
- CImageList [MFC], GetImageInfo
- CImageList [MFC], GetSafeHandle
- CImageList [MFC], Read
- CImageList [MFC], Remove
- CImageList [MFC], Replace
- CImageList [MFC], SetBkColor
- CImageList [MFC], SetDragCursorImage
- CImageList [MFC], SetImageCount
- CImageList [MFC], SetOverlayImage
- CImageList [MFC], Write
- CImageList [MFC], m_hImageList
ms.assetid: b6d1a704-1c82-4548-8a8f-77972adc98a5
ms.openlocfilehash: 2fc92858f84826e2b953fcbc9de020741e97b007
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346371"
---
# <a name="cimagelist-class"></a>CImageList (clase)

Proporciona la funcionalidad del control de lista de imágenes común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CImageList : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CImageList::CImageList](#cimagelist)|Construye un objeto `CImageList`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CImageList::Add](#add)|Agrega una imagen o imágenes a una lista de imágenes.|
|[CImageList::Attach](#attach)|Asocia una lista de imágenes a un `CImageList` objeto.|
|[CImageList::BeginDrag](#begindrag)|Comienza a arrastrar una imagen.|
|[CImageList::Copy](#copy)|Copia una imagen dentro de un `CImageList` objeto.|
|[CImageList::Create](#create)|Inicializa una lista de imágenes y lo adjunta a un `CImageList` objeto.|
|[CImageList::DeleteImageList](#deleteimagelist)|Elimina una lista de imágenes.|
|[CImageList::DeleteTempMap](#deletetempmap)|Lo llama el [CWinApp](../../mfc/reference/cwinapp-class.md) controlador de tiempo de inactividad para eliminar de temporales `CImageList` objeto creado por `FromHandle`.|
|[CImageList::Detach](#detach)|Desasocia un objeto de lista de la imagen desde un `CImageList` de objetos y devuelve un identificador a una lista de imágenes.|
|[CImageList::DragEnter](#dragenter)|Bloquea las actualizaciones durante una operación de arrastrar y muestra la imagen de arrastre en la posición especificada.|
|[CImageList::DragLeave](#dragleave)|Desbloquea la ventana y oculta la imagen de arrastre para que se puede actualizar la ventana.|
|[CImageList::DragMove](#dragmove)|Mueve la imagen que se está arrastrando durante una operación de arrastrar y colocar.|
|[CImageList::DragShowNolock](#dragshownolock)|Muestra u oculta la imagen de arrastre durante una operación de arrastre, sin bloquear la ventana.|
|[CImageList::Draw](#draw)|Dibuja la imagen que se está arrastrando durante una operación de arrastrar y colocar.|
|[CImageList::DrawEx](#drawex)|Dibuja un elemento de lista de imágenes en el contexto de dispositivo especificado. La función usa el estilo de dibujo especificado y combina la imagen con el color especificado.|
|[CImageList::DrawIndirect](#drawindirect)|Dibuja una imagen de una lista de imágenes.|
|[CImageList::EndDrag](#enddrag)|Finaliza una operación de arrastre.|
|[CImageList::ExtractIcon](#extracticon)|Crea un icono basado en una imagen y una máscara en una lista de imágenes.|
|[CImageList::FromHandle](#fromhandle)|Devuelve un puntero a un `CImageList` objeto cuando se especifica un identificador para una lista de imágenes. Si no hay un objeto `CImageList` asociado al identificador, se crea y asocia un objeto `CImageList` temporal.|
|[CImageList::FromHandlePermanent](#fromhandlepermanent)|Devuelve un puntero a un `CImageList` objeto cuando se especifica un identificador para una lista de imágenes. Si un `CImageList` objeto no está asociado al identificador, se devuelve NULL.|
|[CImageList::GetBkColor](#getbkcolor)|Recupera el color de fondo actual para una lista de imágenes.|
|[CImageList::GetDragImage](#getdragimage)|Obtiene la lista de imágenes temporal que se usa para la operación de arrastre.|
|[CImageList::GetImageCount](#getimagecount)|Recupera el número de imágenes en una lista de imágenes.|
|[CImageList::GetImageInfo](#getimageinfo)|Recupera información sobre una imagen.|
|[CImageList::GetSafeHandle](#getsafehandle)|Recupera `m_hImageList`.|
|[CImageList::Read](#read)|Lee una lista de imágenes de un archivo.|
|[CImageList::Remove](#remove)|Quita una imagen de una lista de imágenes.|
|[CImageList::Replace](#replace)|Reemplaza una imagen en una lista de imágenes con una imagen nueva.|
|[CImageList::SetBkColor](#setbkcolor)|Establece el color de fondo de una lista de imágenes.|
|[CImageList::SetDragCursorImage](#setdragcursorimage)|Crea una nueva imagen de arrastre.|
|[CImageList::SetImageCount](#setimagecount)|Restablece el recuento de imágenes en una lista de imágenes.|
|[CImageList::SetOverlayImage](#setoverlayimage)|Agrega el índice de base cero de una imagen a la lista de imágenes que se usará como máscaras de superposición.|
|[CImageList::Write](#write)|Escribe una lista de imágenes en un archivo.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CImageList::operator HIMAGELIST](#operator_himagelist)|Devuelve el HIMAGELIST conectados a la `CImageList`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CImageList::m_hImageList](#m_himagelist)|Un identificador que contiene la lista de imágenes asociada a este objeto.|

## <a name="remarks"></a>Comentarios

Una "lista de imágenes" es una colección de imágenes de un mismo tamaño, cada uno de los cuales se puede hacer referencia a por su índice basado en cero. Listas de imágenes se usan para administrar eficazmente grandes conjuntos de iconos o mapas de bits. Todas las imágenes en una lista de imágenes se encuentran en un mapa de bits única y amplia en formato de dispositivo de pantalla. Una lista de imágenes también puede incluir un mapa de bits monocromo que contiene las máscaras utilizadas para dibujar imágenes de forma transparente (estilo de icono). La aplicación de Microsoft Win32 (API) de la interfaz de programación proporciona funciones de la lista de imágenes que permiten dibujar imágenes, crear y destruir listas de imágenes, agregar y quitar imágenes, reemplazar imágenes, combinar imágenes y arrastrar imágenes.

Este control (y, por tanto, la `CImageList` clase) está disponible solo para programas que se ejecutan en Windows 95/98 y Windows NT versión 3.51 y versiones posteriores.

Para obtener más información sobre el uso de `CImageList`, consulte [controles](../../mfc/controls-mfc.md) y [utilizar CImageList](../../mfc/using-cimagelist.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="add"></a>  CImageList::Add

Llame a esta función para agregar una o más imágenes o en un icono a una lista de imágenes.

```
int Add(
    CBitmap* pbmImage,
    CBitmap* pbmMask);

int Add(
    CBitmap* pbmImage,
    COLORREF crMask);

int Add(HICON hIcon);
```

### <a name="parameters"></a>Parámetros

*pbmImage*<br/>
Puntero al mapa de bits que contiene la imagen o imágenes. El número de imágenes se deduce el ancho del mapa de bits.

*pbmMask*<br/>
Puntero al mapa de bits que contiene la máscara. Si no se usa ninguna máscara con la lista de imágenes, se omite este parámetro.

*crMask*<br/>
Color utilizado para generar la máscara. Cada píxel de este color del mapa de bits especificado se ha cambiado a negro y el bit correspondiente de la máscara se establece en uno.

*hIcon*<br/>
Identificador del icono que contiene el mapa de bits y una máscara para la nueva imagen.

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la nueva imagen si se realiza correctamente; en caso contrario, - 1.

### <a name="remarks"></a>Comentarios

Usted es responsable de liberar el identificador del icono cuando haya terminado con él.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

##  <a name="attach"></a>  CImageList::Attach

Llame a esta función para asociar una lista de imágenes a un `CImageList` objeto.

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parámetros

*hImageList*<br/>
Identificador de un objeto de lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los datos adjuntos se realizó correctamente; en caso contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

##  <a name="begindrag"></a>  CImageList::BeginDrag

Llame a esta función para comenzar a arrastrar una imagen.

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parámetros

*nImage*<br/>
Índice de base cero de la imagen de arrastre.

*ptHotSpot*<br/>
Coordenadas de la posición inicial de arrastre (normalmente, la posición del cursor). Las coordenadas son en relación con la esquina superior izquierda de la imagen.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función crea una lista de imagen temporales que se usa para la operación de arrastre. La imagen combina la imagen especificada y su máscara con el cursor actual. En respuesta a los mensajes subsiguientes WM_MOUSEMOVE, puede mover la imagen de arrastre mediante el `DragMove` función miembro. Para finalizar la operación de arrastre, puede usar el `EndDrag` función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

##  <a name="cimagelist"></a>  CImageList::CImageList

Construye un objeto `CImageList`.

```
CImageList();
```

##  <a name="copy"></a>  CImageList::Copy

Esta función miembro implementa el comportamiento de la función de Win32 [ImageList_Copy](/windows/desktop/api/commctrl/nf-commctrl-imagelist_copy), tal y como se describe en el SDK de Windows.

```
BOOL Copy(
    int iDst,
    int iSrc,
    UINT uFlags = ILCF_MOVE);

BOOL Copy(
    int iDst,
    CImageList* pSrc,
    int iSrc,
    UINT uFlags = ILCF_MOVE);
```

### <a name="parameters"></a>Parámetros

*iDst*<br/>
Índice de base cero de la imagen que se usará como el destino de la operación de copia.

*iSrc*<br/>
Índice de base cero de la imagen que se usará como el origen de la operación de copia.

*uFlags*<br/>
El valor de marca de bits que especifica el tipo de operación de copia se realiza. Este parámetro puede ser uno de los siguientes valores:

|Valor|Significado|
|-----------|-------------|
|ILCF_MOVE|La imagen de origen se copia en el índice de la imagen de destino. Esta operación da como resultado varias instancias de una imagen determinada. ILCF_MOVE es el valor predeterminado.|
|ILCF_SWAP|Las imágenes de origen y destino intercambian posiciones dentro de la lista de imágenes.|

*pSrc*<br/>
Un puntero a un `CImageList` objeto que es el destino de la operación de copia.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

##  <a name="create"></a>  CImageList::Create

Inicializa una lista de imágenes y lo adjunta a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto.

```
BOOL Create(
    int cx,
    int cy,
    UINT nFlags,
    int nInitial,
    int nGrow);

BOOL Create(
    UINT nBitmapID,
    int cx,
    int nGrow,
    COLORREF crMask);

BOOL Create(
    LPCTSTR lpszBitmapID,
    int cx,
    int nGrow,
    COLORREF crMask);

BOOL Create(
    CImageList& imagelist1,
    int nImage1,
    CImageList& imagelist2,
    int nImage2,
    int dx,
    int dy);

BOOL Create(CImageList* pImageList);
```

### <a name="parameters"></a>Parámetros

*cx*<br/>
Dimensiones de cada imagen, en píxeles.

*cy*<br/>
Dimensiones de cada imagen, en píxeles.

*nFlags*<br/>
Especifica el tipo de lista de imágenes para crear. Este parámetro puede ser una combinación de los siguientes valores, pero puede incluir solo uno de los `ILC_COLOR` valores.

|Valor|Significado|
|-----------|-------------|
|ILC_COLOR|Use el comportamiento predeterminado si no se especifica ninguno de los demás ILC_COLOR * marcadores. Normalmente, el valor predeterminado es ILC_COLOR4; pero para los controladores de pantalla anterior, el valor predeterminado es ILC_COLORDDB.|
|ILC_COLOR4|Usar una sección de mapa de bits independientes del dispositivo (DIB) de 4 bits (16 colores) como el mapa de bits de la lista de imágenes.|
|ILC_COLOR8|Utilice una sección DIB de 8 bits. Los colores usados para la tabla de colores son los mismos colores como la paleta de semitonos.|
|ILC_COLOR16|Usar 16 bits (32 / 64k color) sección DIB.|
|ILC_COLOR24|Usar una sección DIB de 24 bits.|
|ILC_COLOR32|Usar una sección DIB de 32 bits.|
|ILC_COLORDDB|Usar un mapa de bits dependiente del dispositivo.|
|ILC_MASK|Utiliza una máscara. La lista de imágenes contiene dos mapas de bits, uno de los cuales es un mapa de bits monocromático utilizado como máscara. Si no se incluye este valor, la lista de imágenes contiene sólo un mapa de bits. Consulte [dibujar imágenes de una lista de imágenes](../../mfc/drawing-images-from-an-image-list.md) para obtener más información sobre imágenes enmascaradas.|

*nInitial*<br/>
Número de imágenes que inicialmente contiene la lista de imágenes.

*nGrow*<br/>
Número de imágenes que puede alcanzar la lista de imágenes cuando el sistema debe cambiar el tamaño de la lista para dejar espacio para incluir nuevas imágenes. Este parámetro representa el número de nuevas imágenes que puede contener la lista de imágenes cuyo tamaño ha cambiado.

*nBitmapID*<br/>
Identificadores de recursos del mapa de bits que se asociará con la lista de imágenes.

*crMask*<br/>
Color utilizado para generar una máscara. Cada píxel de este color del mapa de bits especificado se ha cambiado a negro y el bit correspondiente de la máscara se establece en uno.

*lpszBitmapID*<br/>
Una cadena que contiene los identificadores de las imágenes de recursos.

*imagelist1*<br/>
Referencia a un objeto `CImageList`.

*nImage1*<br/>
Índice de la primera imagen existente.

*imagelist2*<br/>
Referencia a un objeto `CImageList`.

*nImage2*<br/>
Índice de la segunda imagen existente.

*dx*<br/>
Desplazamiento del eje x de la segunda imagen en relación con la primera imagen, en píxeles.

*dy*<br/>
Desplazamiento del eje y de la segunda imagen en relación con la primera imagen, en píxeles.

*pImageList*<br/>
Puntero a un objeto `CImageList` .

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Construir un `CImageList` en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a `Create`, que crea la lista de imágenes y la conecta a la `CImageList` objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

##  <a name="deleteimagelist"></a>  CImageList::DeleteImageList

Llame a esta función para eliminar una lista de imágenes.

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

##  <a name="deletetempmap"></a>  CImageList::DeleteTempMap

Llama de forma automática el `CWinApp` controlador de tiempo de inactividad, `DeleteTempMap` elimina temporales `CImageList` los objetos creados por [FromHandle](#fromhandle), pero no destruirá los identificadores ( `hImageList`) asociados temporalmente con el `ImageList` objetos.

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

##  <a name="detach"></a>  CImageList::Detach

Llame a esta función para desasociar un objeto de lista de la imagen desde un `CImageList` objeto.

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>Valor devuelto

Identificador de un objeto de lista de imágenes.

### <a name="remarks"></a>Comentarios

Esta función devuelve un identificador para el objeto de lista de imágenes.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CImageList::Attach](#attach).

##  <a name="dragenter"></a>  CImageList::DragEnter

Durante una operación de arrastre, bloquea las actualizaciones de la ventana especificada por *pWndLock* y muestra la imagen de arrastre en la posición especificada por *punto*.

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*pWndLock*<br/>
Puntero a la ventana propietaria de la imagen de arrastre.

*point*<br/>
Posición en la que se va a mostrar la imagen de arrastre. Las coordenadas son en relación con la esquina superior izquierda de la ventana (no en el área de cliente).

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Las coordenadas son en relación con esquina superior izquierda la ventana en la, por lo que debe compensar los anchos de los elementos de ventana, como el borde, la barra de título y la barra de menús, al especificar las coordenadas.

Si *pWndLock* es NULL, esta función dibuja la imagen en el contexto de presentación asociado con la ventana de escritorio y coordenadas son relativas a la esquina superior izquierda de la pantalla.

Esta función bloquea todas las demás actualizaciones a la ventana especificada durante la operación de arrastre. Si tiene que hacer ningún dibujo durante una operación de arrastre, como resaltar el destino de una operación de arrastrar y colocar, puede ocultar temporalmente la imagen arrastrada utilizando la [CImageList::DragLeave](#dragleave) función.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CImageList::BeginDrag](#begindrag).

##  <a name="dragleave"></a>  CImageList::DragLeave

Desbloquea la ventana especificada por *pWndLock* y oculta la imagen de arrastre, lo que permite la ventana para actualizarse.

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>Parámetros

*pWndLock*<br/>
Puntero a la ventana propietaria de la imagen de arrastre.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CImageList::EndDrag](#enddrag).

##  <a name="dragmove"></a>  CImageList::DragMove

Llame a esta función para mover la imagen que se está arrastrando durante una operación de arrastrar y colocar.

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>Parámetros

*pt*<br/>
Nueva posición de arrastre.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función normalmente se llama en respuesta a un mensaje WM_MOUSEMOVE. Para comenzar una operación de arrastre, use el `BeginDrag` función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

##  <a name="dragshownolock"></a>  CImageList::DragShowNolock

Muestra u oculta la imagen de arrastre durante una operación de arrastre, sin bloquear la ventana.

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bShow*<br/>
Especifica si la imagen de arrastre es que se mostrará.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El [CImageList::DragEnter](#dragenter) función bloquea todas las actualizaciones de la ventana durante una operación de arrastre. Sin embargo, esta función, no bloquea la ventana.

##  <a name="draw"></a>  CImageList::Draw

Llame a esta función para dibujar la imagen que se está arrastrando durante una operación de arrastrar y colocar.

```
BOOL Draw(
    CDC* pDC,
    int nImage,
    POINT pt,
    UINT nStyle);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero al contexto del dispositivo de destino.

*nImage*<br/>
Índice de base cero de la imagen para dibujar.

*pt*<br/>
Ubicación en la que se va a dibujar dentro del contexto de dispositivo especificado.

*nStyle*<br/>
Marca que especifica el estilo de dibujo. Puede ser uno o varios de estos valores:

|Valor|Significado|
|-----------|-------------|
|ILD_BLEND25, ILD_FOCUS|Dibuja la imagen, un 25 por ciento con el color de resaltado del sistema de fusión. Este valor no tiene ningún efecto si la lista de imágenes no contiene una máscara.|
|ILD_BLEND50, ILD_SELECTED, ILD_BLEND|Dibuja la imagen, fusión 50 por ciento con el color de resaltado del sistema. Este valor no tiene ningún efecto si la lista de imágenes no contiene una máscara.|
|ILD_MASK|Dibuja la máscara.|
|ILD_NORMAL|Dibuja la imagen con el color de fondo de la lista de imágenes. Si el color de fondo es el valor como CLR_NONE, la imagen se dibuja de forma transparente utilizando la máscara.|
|ILD_TRANSPARENT|Dibuja la imagen con la máscara, independientemente del color de fondo de forma transparente.|

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [función CImageList:: SetOverlayImage](#setoverlayimage).

##  <a name="drawex"></a>  CImageList::DrawEx

Dibuja un elemento de lista de imágenes en el contexto de dispositivo especificado.

```
BOOL DrawEx(
    CDC* pDC,
    int nImage,
    POINT pt,
    SIZE sz,
    COLORREF clrBk,
    COLORREF clrFg,
    UINT nStyle);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero al contexto del dispositivo de destino.

*nImage*<br/>
Índice de base cero de la imagen para dibujar.

*pt*<br/>
Ubicación en la que se va a dibujar dentro del contexto de dispositivo especificado.

*sz*<br/>
Tamaño de la parte de la imagen para dibujar, relativa a la esquina superior izquierda de la imagen. Consulte *dx* y *dy* en [ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) en el SDK de Windows.

*clrBk*<br/>
Color de fondo de la imagen. Consulte *rgbBk* en [ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) en el SDK de Windows.

*clrFg*<br/>
Color de primer plano de la imagen. Consulte *rgbFg* en [ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) en el SDK de Windows.

*nStyle*<br/>
Marca que especifica el estilo de dibujo. Consulte *fStyle* en [ImageList_DrawEx](/windows/desktop/api/commctrl/nf-commctrl-imagelist_drawex) en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

La función usa el estilo de dibujo especificado y combina la imagen con el color especificado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

##  <a name="drawindirect"></a>  CImageList::DrawIndirect

Llame a esta función miembro para dibujar una imagen de una lista de imágenes.

```
BOOL DrawIndirect(IMAGELISTDRAWPARAMS* pimldp);

BOOL DrawIndirect(
    CDC* pDC,
    int nImage,
    POINT pt,
    SIZE sz,
    POINT ptOrigin,
    UINT fStyle = ILD_NORMAL,
    DWORD dwRop = SRCCOPY,
    COLORREF rgbBack = CLR_DEFAULT,
    COLORREF rgbFore = CLR_DEFAULT,
    DWORD fState = ILS_NORMAL,
    DWORD Frame = 0,
    COLORREF crEffect = CLR_DEFAULT);
```

### <a name="parameters"></a>Parámetros

*pimldp*<br/>
Un puntero a un [estructura IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams) estructura que contiene información sobre la operación de dibujo.

*pDC*<br/>
Un puntero al contexto del dispositivo de destino. Debe eliminar este [CDC](../../mfc/reference/cdc-class.md) objeto cuando haya terminado con él.

*nImage*<br/>
Índice de base cero de la imagen que se va a dibujar.

*pt*<br/>
Un [punto](/previous-versions/dd162805\(v=vs.85\)) estructura que contiene las coordenadas x e y donde se dibujará la imagen.

*sz*<br/>
Un [tamaño](/windows/desktop/api/windef/ns-windef-tagsize) estructura que indica el tamaño de la imagen que se va a dibujar.

*ptOrigin*<br/>
Un [punto](/previous-versions/dd162805\(v=vs.85\)) estructura que contiene las coordenadas x e y especificación de la esquina superior izquierda de la operación de dibujo con respecto a la imagen en Sí. No se dibujan los píxeles de la imagen que están a la izquierda de la coordenada x y versiones posteriores de la coordenada y.

*fStyle*<br/>
Marca que especifica el estilo de dibujo y, opcionalmente, la imagen de superposición. Vea la sección Comentarios para obtener información sobre la imagen de superposición. La implementación predeterminada MFC, ILD_NORMAL, dibuja la imagen con el color de fondo de la lista de imágenes. Si el color de fondo es el valor como CLR_NONE, la imagen se dibuja utilizando una máscara de forma transparente.

Otros estilos posibles se describen en la *fStyle* miembro de la [estructura IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams) estructura.

*dwRop*<br/>
Valor que especifica un código de operación de trama. Estos códigos definen cómo los datos de color del rectángulo de origen se combinarán con los datos de color del rectángulo de destino lograr el color final. La implementación predeterminada de MFC, SRCCOPY, copia el rectángulo de origen directamente en el rectángulo de destino. Este parámetro se omite si el *fStyle* parámetro no incluye la marca ILD_ROP.

Otros valores posibles se describen en la *dwRop* miembro de la [estructura IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams) estructura.

*rgbBack*<br/>
El color de fondo de imagen, de forma predeterminada CLR_DEFAULT. Este parámetro puede ser un valor definido por la aplicación de RGB o uno de los valores siguientes:

|Valor|Significado|
|-----------|-------------|
|CLR_DEFAULT|Color de fondo predeterminado. La imagen se dibuja utilizando el color de fondo de la lista de imágenes.|
|CLR_NONE|Ningún color de fondo. La imagen se dibuja de forma transparente.|

*rgbFore*<br/>
Color de primer plano de imagen, de forma predeterminada CLR_DEFAULT. Este parámetro puede ser un valor definido por la aplicación de RGB o uno de los valores siguientes:

|Valor|Significado|
|-----------|-------------|
|CLR_DEFAULT|Color de primer plano predeterminado. La imagen se dibuja utilizando el color de resaltado del sistema como el color de primer plano.|
|CLR_NONE|Ningún color de blend. La imagen se mezcla con el color del contexto del dispositivo de destino.|

Este parámetro se usa únicamente si *fStyle* incluye la marca ILD_BLEND25 o ILD_BLEND50.

*fState*<br/>
Marca que especifica el estado de dibujo. Este miembro puede contener uno o más indicadores de estado de lista de imágenes.

*Frame*<br/>
Afecta al comportamiento de efectos saturados y combinación alfa.

Cuando se usa con ILS_SATURATE, este miembro contiene el valor que se agrega a cada componente de color de la terna RGB para cada píxel en el icono.

Cuando se usa con ILS_APLHA, este miembro contiene el valor para el canal alfa. Este valor puede ser entre 0 y 255, donde 0 es completamente transparente y 255 es completamente opaco.

*crEffect*<br/>
Un [COLORREF](/windows/desktop/gdi/colorref) valor utilizado para los efectos de sombra e iluminado.

### <a name="return-value"></a>Valor devuelto

TRUE si la imagen se dibuja correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Utilice la primera versión, si desea rellenar manualmente la estructura de Win32. Use la segunda versión si desea aprovechar las ventajas de uno o varios de los argumentos predeterminados de MFC o evitar tener que administrar la estructura.

Una imagen de superposición es una imagen que se dibuja encima de la imagen principal, especificada en esta función miembro por el *nImage* parámetro. Dibujar una máscara de superposición con el [dibujar](#draw) función miembro con el índice basado en uno de la máscara de superposición especificada utilizando el [macro INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask) macro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

##  <a name="enddrag"></a>  CImageList::EndDrag

Llame a esta función para finalizar una operación de arrastre.

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>Comentarios

Para comenzar una operación de arrastre, use el `BeginDrag` función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

##  <a name="extracticon"></a>  CImageList::ExtractIcon

Llame a esta función para crear un icono que se basa en una imagen y su máscara relacionado en una lista de imágenes.

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>Parámetros

*nImage*<br/>
Índice de base cero de la imagen.

### <a name="return-value"></a>Valor devuelto

Identificador del icono si es correcto; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

Este método se basa en el comportamiento de la [ImageList_ExtractIcon](/windows/desktop/api/commctrl/nf-commctrl-imagelist_extracticon) macro para crear el icono. Hacer referencia a la [ImageList_ExtractIcon](/windows/desktop/api/commctrl/nf-commctrl-imagelist_extracticon) macro para obtener más información sobre la creación de icono y limpieza.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

##  <a name="fromhandle"></a>  CImageList::FromHandle

Devuelve un puntero a un `CImageList` objeto cuando se especifica un identificador para una lista de imágenes.

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parámetros

*hImageList*<br/>
Especifica la lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Un puntero a un `CImageList` objeto si es correcto; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Si un `CImageList` ya no está asociado al identificador, un archivo temporal `CImageList` objeto creado y conectado. Este temporal `CImageList` objeto es válido solo hasta que la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos, momento en el que se eliminan todos los objetos temporales.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

##  <a name="fromhandlepermanent"></a>  CImageList::FromHandlePermanent

Devuelve un puntero a un `CImageList` objeto cuando se especifica un identificador para una lista de imágenes.

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parámetros

*hImageList*<br/>
Especifica la lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Un puntero a un `CImageList` objeto si es correcto; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Si un `CImageList` objeto no está asociado al identificador, se devuelve NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

##  <a name="getbkcolor"></a>  CImageList::GetBkColor

Llame a esta función para recuperar el color de fondo actual para una lista de imágenes.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valor devuelto

El valor de color RGB de la `CImageList` color de fondo de objeto.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CImageList::SetBkColor](#setbkcolor).

##  <a name="getdragimage"></a>  CImageList::GetDragImage

Obtiene la lista de imágenes temporal que se usa para la operación de arrastre.

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>Parámetros

*lpPoint*<br/>
Dirección de un [punto](/previous-versions/dd162805\(v=vs.85\)) estructura que recibe la actual posición de arrastre.

*lpPointHotSpot*<br/>
Dirección de un `POINT` estructura que recibe el desplazamiento de la imagen de arrastre en relación con la posición de arrastre.

### <a name="return-value"></a>Valor devuelto

Si es correcto, un puntero a la imagen temporal una lista que se usa para operaciones de arrastre; en caso contrario, es NULL.

##  <a name="getimagecount"></a>  CImageList::GetImageCount

Llame a esta función para recuperar el número de imágenes en una lista de imágenes.

```
int GetImageCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de imágenes.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CImageList::ExtractIcon](#extracticon).

##  <a name="getimageinfo"></a>  CImageList::GetImageInfo

Llame a esta función para recuperar información acerca de una imagen.

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>Parámetros

*nImage*<br/>
Índice de base cero de la imagen.

*pImageInfo*<br/>
Puntero a un [IMAGEINFO](/windows/desktop/api/commctrl/ns-commctrl-_imageinfo) estructura que recibe información acerca de la imagen. La información de esta estructura puede usarse para manipular directamente los mapas de bits para la imagen.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El `IMAGEINFO` estructura contiene información sobre una imagen en una lista de imágenes.

##  <a name="getsafehandle"></a>  CImageList::GetSafeHandle

Llame a esta función para recuperar el `m_hImageList` miembro de datos.

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>Valor devuelto

Un identificador de la lista de la imagen adjunta; en caso contrario, es NULL si no hay ningún objeto está asociado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

##  <a name="m_himagelist"></a>  CImageList::m_hImageList

Identificador de la lista de imágenes asociado a este objeto.

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>Comentarios

El `m_hImageList` miembro de datos es una variable pública de tipo HIMAGELIST.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

##  <a name="operator_himagelist"></a>  CImageList::operator HIMAGELIST

Utilice este operador para obtener el identificador de adjunta el `CImageList` objeto.

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcto, un identificador de la lista de imágenes representado por la `CImageList` objeto; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Este es un operador de conversión, que admite el uso directo de un objeto HIMAGELIST.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

##  <a name="read"></a>  CImageList::Read

Llame a esta función para leer una lista de imágenes de un archivo.

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>Parámetros

*pArchive*<br/>
Un puntero a un `CArchive` objeto desde el que se puede leer la lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

##  <a name="remove"></a>  CImageList::Remove

Llame a esta función para quitar una imagen de un objeto de lista de imágenes.

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>Parámetros

*nImage*<br/>
Índice de base cero de la imagen para quitar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Todos los elementos que siguen a *nImage* ahora Bajar una posición. Por ejemplo, si una lista de imágenes contiene dos elementos, eliminar el primer elemento hará que el elemento restante esté ahora en la primera posición. *nImage*= 0 para el elemento en la primera posición.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

##  <a name="replace"></a>  CImageList::Replace

Llame a esta función para reemplazar una imagen en una lista de imágenes con una imagen nueva.

```
BOOL Replace(
    int nImage,
    CBitmap* pbmImage,
    CBitmap* pbmMask);

int Replace(
    int nImage,
    HICON hIcon);
```

### <a name="parameters"></a>Parámetros

*nImage*<br/>
Índice de base cero de la imagen para reemplazar.

*pbmImage*<br/>
Un puntero al mapa de bits que contiene la imagen.

*pbmMask*<br/>
Un puntero al mapa de bits que contiene la máscara. Si no se usa ninguna máscara con la lista de imágenes, se omite este parámetro.

*hIcon*<br/>
Identificador del icono que contiene el mapa de bits y una máscara para la nueva imagen.

### <a name="return-value"></a>Valor devuelto

La versión devolver BOOL devuelve distinto de cero si se realiza correctamente; en caso contrario, es 0.

La versión devolver **int** devuelve el índice de base cero de la imagen si es correcto; en caso contrario, - 1.

### <a name="remarks"></a>Comentarios

Llame a esta función miembro después de llamar a [función SetImageCount](#setimagecount) para asignar el nuevo, las imágenes válidas para el marcador de posición de imagen números de índice.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CImageList::SetImageCount](#setimagecount).

##  <a name="setbkcolor"></a>  CImageList::SetBkColor

Llame a esta función para establecer el color de fondo de una lista de imágenes.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parámetros

*cr*<br/>
Color de fondo para establecer. Puede ser como CLR_NONE. En ese caso, las imágenes se dibujan utilizando la máscara de forma transparente.

### <a name="return-value"></a>Valor devuelto

El color de fondo anterior si es correcto; como en caso contrario CLR_NONE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

##  <a name="setdragcursorimage"></a>  CImageList::SetDragCursorImage

Crea una nueva imagen de arrastre combinando la imagen especificada (normalmente una imagen del cursor del mouse) con la imagen de arrastre actual.

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parámetros

*nDrag*<br/>
Índice de la nueva imagen que va a combinarse con la imagen de arrastre.

*ptHotSpot*<br/>
Posición de la zona activa dentro de la nueva imagen.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Dado que las funciones de arrastre usan la nueva imagen durante una operación de arrastre, debe usar el Windows [ShowCursor](/windows/desktop/api/winuser/nf-winuser-showcursor) función para ocultar el cursor del mouse real después de llamar a `CImageList::SetDragCursorImage`. En caso contrario, el sistema puede parecer que tiene dos cursores del mouse para la duración de la operación de arrastre.

##  <a name="setimagecount"></a>  CImageList::SetImageCount

Llame a esta función miembro para restablecer el número de imágenes en un `CImageList` objeto.

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>Parámetros

*uNewCount*<br/>
Valor que especifica el nuevo número total de imágenes en la lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Si se llama a esta función miembro para aumentar el número de imágenes en la lista de imágenes, a continuación, llame a [reemplazar](#replace) para cada imagen adicional asignar los nuevos índices a las imágenes válidas. Si no puede asignar los índices a las imágenes válidas, las operaciones de dibujo que crean las nuevas imágenes serán impredecibles.

Si disminuye el tamaño de una lista de imágenes mediante el uso de esta función, se liberan las imágenes truncadas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

##  <a name="setoverlayimage"></a>  CImageList::SetOverlayImage

Llame a esta función para agregar el índice de base cero de una imagen a la lista de imágenes que se usará como máscaras de superposición.

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>Parámetros

*nImage*<br/>
Índice de base cero de la imagen que se usará como máscara de superposición.

*nOverlay*<br/>
Índice basado en uno de la máscara de superposición.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Hasta cuatro índices se pueden agregar a la lista.

Una máscara de superposición es una imagen dibujada de forma transparente sobre otra imagen. Dibujar una máscara superpuesta a través de una imagen mediante la [CImageList::Draw](#draw) función miembro con el índice basado en uno de la máscara de superposición especificada mediante el uso de la macro INDEXTOOVERLAYMASK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

##  <a name="write"></a>  CImageList::Write

Llame a esta función para escribir un objeto de lista de imágenes en un archivo.

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>Parámetros

*pArchive*<br/>
Un puntero a un `CArchive` objeto en el que se almacenará la lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>Vea también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CListCtrl (clase)](../../mfc/reference/clistctrl-class.md)<br/>
[CTabCtrl (clase)](../../mfc/reference/ctabctrl-class.md)
