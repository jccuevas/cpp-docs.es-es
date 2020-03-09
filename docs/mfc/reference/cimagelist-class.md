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
ms.openlocfilehash: 1555209ce0f1c2caacbfb4b01107775db948d230
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890712"
---
# <a name="cimagelist-class"></a>CImageList (clase)

Proporciona la funcionalidad del control de lista de imágenes común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CImageList : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CImageList:: CImageList](#cimagelist)|Construye un objeto `CImageList`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CImageList:: Add](#add)|Agrega una imagen o imágenes a una lista de imágenes.|
|[CImageList:: Attach](#attach)|Asocia una lista de imágenes a un objeto `CImageList`.|
|[CImageList:: BeginDrag](#begindrag)|Comienza a arrastrar una imagen.|
|[CImageList:: Copy](#copy)|Copia una imagen dentro de un objeto `CImageList`.|
|[CImageList:: Create](#create)|Inicializa una lista de imágenes y la adjunta a un objeto `CImageList`.|
|[CImageList::D eleteImageList](#deleteimagelist)|Elimina una lista de imágenes.|
|[CImageList::D eleteTempMap](#deletetempmap)|Lo llama el controlador de tiempo de inactividad de [CWinApp](../../mfc/reference/cwinapp-class.md) para eliminar cualquier objeto `CImageList` temporal creado por `FromHandle`.|
|[CImageList::D Etach](#detach)|Desasocia un objeto de lista de imágenes de un objeto `CImageList` y devuelve un identificador a una lista de imágenes.|
|[CImageList::D ragEnter](#dragenter)|Bloquea las actualizaciones durante una operación de arrastre y muestra la imagen de arrastre en una posición especificada.|
|[CImageList::D ragLeave](#dragleave)|Desbloquea la ventana y oculta la imagen de arrastre para que la ventana se pueda actualizar.|
|[CImageList::D ragMove](#dragmove)|Mueve la imagen que se está arrastrando durante una operación de arrastrar y colocar.|
|[CImageList::D ragShowNolock](#dragshownolock)|Muestra u oculta la imagen de arrastre durante una operación de arrastre, sin bloquear la ventana.|
|[CImageList::D RAW](#draw)|Dibuja la imagen que se está arrastrando durante una operación de arrastrar y colocar.|
|[CImageList::D rawEx](#drawex)|Dibuja un elemento de lista de imágenes en el contexto de dispositivo especificado. La función usa el estilo de dibujo especificado y combina la imagen con el color especificado.|
|[CImageList::D rawIndirect](#drawindirect)|Dibuja una imagen a partir de una lista de imágenes.|
|[CImageList:: EndDrag](#enddrag)|Finaliza una operación de arrastre.|
|[CImageList:: ExtractIcon](#extracticon)|Crea un icono basado en una imagen y una máscara en una lista de imágenes.|
|[CImageList:: FromHandle](#fromhandle)|Devuelve un puntero a un objeto `CImageList` cuando se proporciona un identificador a una lista de imágenes. Si no hay un objeto `CImageList` asociado al identificador, se crea y asocia un objeto `CImageList` temporal.|
|[CImageList:: FromHandlePermanent](#fromhandlepermanent)|Devuelve un puntero a un objeto `CImageList` cuando se proporciona un identificador a una lista de imágenes. Si un objeto de `CImageList` no está asociado al identificador, se devuelve NULL.|
|[CImageList:: GetBkColor](#getbkcolor)|Recupera el color de fondo actual para una lista de imágenes.|
|[CImageList:: GetDragImage](#getdragimage)|Obtiene la lista de imágenes temporales que se usa para arrastrar.|
|[CImageList:: GetImageCount](#getimagecount)|Recupera el número de imágenes de una lista de imágenes.|
|[CImageList:: GetImageInfo](#getimageinfo)|Recupera información acerca de una imagen.|
|[CImageList:: GetSafeHandle](#getsafehandle)|Recupera `m_hImageList`.|
|[CImageList:: Read](#read)|Lee una lista de imágenes de un archivo.|
|[CImageList:: Remove](#remove)|Quita una imagen de una lista de imágenes.|
|[CImageList:: Replace](#replace)|Reemplaza una imagen de una lista de imágenes por una nueva.|
|[CImageList:: SetBkColor](#setbkcolor)|Establece el color de fondo de una lista de imágenes.|
|[CImageList:: SetDragCursorImage](#setdragcursorimage)|Crea una nueva imagen de arrastre.|
|[CImageList:: SetImageCount](#setimagecount)|Restablece el recuento de imágenes de una lista de imágenes.|
|[CImageList:: SetOverlayImage](#setoverlayimage)|Agrega el índice de base cero de una imagen a la lista de imágenes que se van a usar como máscaras superpuestas.|
|[CImageList:: Write](#write)|Escribe una lista de imágenes en un archivo.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CImageList:: Operator HIMAGELIST](#operator_himagelist)|Devuelve el HIMAGELIST asociado a la `CImageList`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CImageList:: m_hImageList](#m_himagelist)|Identificador que contiene la lista de imágenes asociada a este objeto.|

## <a name="remarks"></a>Observaciones

Una "lista de imágenes" es una colección de imágenes del mismo tamaño, a las que se puede hacer referencia a través de su índice basado en cero. Las listas de imágenes se utilizan para administrar de forma eficaz grandes conjuntos de iconos o mapas de bits. Todas las imágenes de una lista de imágenes están contenidas en un único mapa de bits ancho en formato de dispositivo de pantalla. Una lista de imágenes también puede incluir un mapa de bits monocromo que contenga máscaras utilizadas para dibujar imágenes de forma transparente (estilo de icono). La interfaz de programación de aplicaciones (API) de Microsoft Win32 proporciona funciones de lista de imágenes que permiten dibujar imágenes, crear y destruir listas de imágenes, agregar y quitar imágenes, reemplazar imágenes, combinar imágenes y arrastrar imágenes.

Este control (y, por tanto, la clase `CImageList`) solo está disponible para programas que se ejecutan en Windows 95/98 y Windows NT versión 3,51 y versiones posteriores.

Para obtener más información sobre el uso de `CImageList`, vea [controles](../../mfc/controls-mfc.md) y [uso de CImageList](../../mfc/using-cimagelist.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="add"></a>CImageList:: Add

Llame a esta función para agregar una o varias imágenes o un icono a una lista de imágenes.

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
Puntero al mapa de bits que contiene la imagen o imágenes. El número de imágenes se deduce del ancho del mapa de bits.

*pbmMask*<br/>
Puntero al mapa de bits que contiene la máscara. Si no se usa ninguna máscara con la lista de imágenes, se omite este parámetro.

*crMask*<br/>
Color usado para generar la máscara. Cada píxel de este color en el mapa de bits dado se cambia a negro y el bit correspondiente de la máscara se establece en uno.

*hIcon*<br/>
Identificador del icono que contiene el mapa de bits y la máscara de la nueva imagen.

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la primera imagen nueva si se realiza correctamente; de lo contrario,-1.

### <a name="remarks"></a>Observaciones

Usted es responsable de liberar el identificador del icono cuando haya terminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

##  <a name="attach"></a>CImageList:: Attach

Llame a esta función para asociar una lista de imágenes a un objeto `CImageList`.

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parámetros

*hImageList*<br/>
Identificador de un objeto de lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los datos adjuntos se han realizado correctamente; de lo contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

##  <a name="begindrag"></a>CImageList:: BeginDrag

Llame a esta función para empezar a arrastrar una imagen.

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parámetros

*nImage*<br/>
Índice de base cero de la imagen que se va a arrastrar.

*ptHotSpot*<br/>
Coordenadas de la posición de arrastre inicial (normalmente, la posición del cursor). Las coordenadas son relativas a la esquina superior izquierda de la imagen.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función crea una lista de imágenes temporales que se usa para arrastrar. La imagen combina la imagen especificada y su máscara con el cursor actual. En respuesta a los mensajes de WM_MOUSEMOVE subsiguientes, puede trasladar la imagen de arrastre mediante la función miembro `DragMove`. Para finalizar la operación de arrastre, puede usar la función miembro `EndDrag`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

##  <a name="cimagelist"></a>CImageList:: CImageList

Construye un objeto `CImageList`.

```
CImageList();
```

##  <a name="copy"></a>CImageList:: Copy

Esta función miembro implementa el comportamiento de la función de Win32 [ImageList_Copy](/windows/win32/api/commctrl/nf-commctrl-imagelist_copy), como se describe en el Windows SDK.

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
Índice de base cero de la imagen que se va a usar como destino de la operación de copia.

*iSrc*<br/>
Índice de base cero de la imagen que se va a usar como origen de la operación de copia.

*uFlags*<br/>
Valor de marca de bits que especifica el tipo de operación de copia que se va a realizar. Este parámetro puede ser uno de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|ILCF_MOVE|La imagen de origen se copia en el índice de la imagen de destino. Esta operación da como resultado varias instancias de una imagen determinada. ILCF_MOVE es el valor predeterminado.|
|ILCF_SWAP|Las imágenes de origen y de destino intercambian posiciones dentro de la lista de imágenes.|

*pSrc*<br/>
Un puntero a un objeto `CImageList` que es el destino de la operación de copia.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

##  <a name="create"></a>CImageList:: Create

Inicializa una lista de imágenes y la adjunta a un objeto [CImageList](../../mfc/reference/cimagelist-class.md) .

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

*serie*<br/>
Dimensiones de cada imagen, en píxeles.

*CY*<br/>
Dimensiones de cada imagen, en píxeles.

*nFlags*<br/>
Especifica el tipo de lista de imágenes que se va a crear. Este parámetro puede ser una combinación de los valores siguientes, pero solo puede incluir uno de los valores de `ILC_COLOR`.

|Value|Significado|
|-----------|-------------|
|ILC_COLOR|Use el comportamiento predeterminado si no se especifica ninguna de las otras marcas ILC_COLOR *. Normalmente, el valor predeterminado es ILC_COLOR4; pero para los controladores de pantalla anteriores, el valor predeterminado es ILC_COLORDDB.|
|ILC_COLOR4|Use una sección de mapa de bits independiente del dispositivo (DIB) de 4 bits (16 colores) como mapa de bits para la lista de imágenes.|
|ILC_COLOR8|Use una sección DIB de 8 bits. Los colores usados para la tabla de colores son los mismos que los colores de la paleta de semitonos.|
|ILC_COLOR16|Use una sección DIB de 16 bits (color de 32/64k).|
|ILC_COLOR24|Use una sección DIB de 24 bits.|
|ILC_COLOR32|Use una sección DIB de 32 bits.|
|ILC_COLORDDB|Use un mapa de bits dependiente del dispositivo.|
|ILC_MASK|Usa una máscara. La lista de imágenes contiene dos mapas de bits, uno de los cuales es un mapa de bits monocromo que se usa como máscara. Si no se incluye este valor, la lista de imágenes solo contiene un mapa de bits. Vea [dibujar imágenes de una lista](../../mfc/drawing-images-from-an-image-list.md) de imágenes para obtener información adicional sobre las imágenes enmascaradas.|

*nInitial*<br/>
Número de imágenes que la lista de imágenes contiene inicialmente.

*nGrow*<br/>
Número de imágenes que pueden alcanzar la lista de imágenes cuando el sistema necesita cambiar el tamaño de la lista para dejar espacio para las nuevas imágenes. Este parámetro representa el número de imágenes nuevas que puede contener la lista de imágenes cuyo tamaño se ha cambiado.

*nBitmapID*<br/>
Los identificadores de recursos del mapa de bits que se van a asociar a la lista de imágenes.

*crMask*<br/>
Color usado para generar una máscara. Cada píxel de este color en el mapa de bits especificado cambia a negro y el bit correspondiente de la máscara se establece en uno.

*lpszBitmapID*<br/>
Cadena que contiene los identificadores de recursos de las imágenes.

*imagelist1*<br/>
Referencia a un objeto `CImageList`.

*nImage1*<br/>
Índice de la primera imagen existente.

*imagelist2*<br/>
Referencia a un objeto `CImageList`.

*nImage2*<br/>
Índice de la segunda imagen existente.

*DX*<br/>
Desplazamiento del eje x de la segunda imagen en relación con la primera imagen, en píxeles.

*DY*<br/>
Desplazamiento del eje y de la segunda imagen en relación con la primera imagen, en píxeles.

*pImageList*<br/>
Puntero a un objeto `CImageList` .

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Una `CImageList` se crea en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a `Create`, que crea la lista de imágenes y la adjunta al objeto `CImageList`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

##  <a name="deleteimagelist"></a>CImageList::D eleteImageList

Llame a esta función para eliminar una lista de imágenes.

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

##  <a name="deletetempmap"></a>CImageList::D eleteTempMap

Llamado automáticamente por el controlador de tiempo de inactividad de `CWinApp`, `DeleteTempMap` elimina los objetos `CImageList` temporales creados por [FromHandle](#fromhandle), pero no destruye ningún manipulador (`hImageList`) que esté asociado temporalmente a los objetos `ImageList`.

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

##  <a name="detach"></a>CImageList::D Etach

Llame a esta función para desasociar un objeto de lista de imágenes de un objeto `CImageList`.

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>Valor devuelto

Identificador de un objeto de lista de imágenes.

### <a name="remarks"></a>Observaciones

Esta función devuelve un identificador al objeto de lista de imágenes.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CImageList:: Attach](#attach).

##  <a name="dragenter"></a>CImageList::D ragEnter

Durante una operación de arrastre, bloquea las actualizaciones de la ventana especificada por *pWndLock* y muestra la imagen de arrastre en la posición especificada por *Point*.

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*pWndLock*<br/>
Puntero a la ventana que posee la imagen de arrastre.

*Elija*<br/>
Posición en la que se va a mostrar la imagen de arrastre. Las coordenadas son relativas a la esquina superior izquierda de la ventana (no al área cliente).

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Las coordenadas son relativas a la esquina superior izquierda de la ventana, por lo que debe compensar los anchos de los elementos de ventana, como el borde, la barra de título y la barra de menús, al especificar las coordenadas.

Si *pWndLock* es null, esta función dibuja la imagen en el contexto de presentación asociado a la ventana del escritorio y las coordenadas son relativas a la esquina superior izquierda de la pantalla.

Esta función bloquea todas las demás actualizaciones en la ventana especificada durante la operación de arrastre. Si necesita realizar algún dibujo durante una operación de arrastre, como resaltar el destino de una operación de arrastrar y colocar, puede ocultar temporalmente la imagen arrastrada mediante la función [CImageList::D ragleave](#dragleave) .

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CImageList:: BeginDrag](#begindrag).

##  <a name="dragleave"></a>CImageList::D ragLeave

Desbloquea la ventana especificada por *pWndLock* y oculta la imagen de arrastre, lo que permite que la ventana se actualice.

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>Parámetros

*pWndLock*<br/>
Puntero a la ventana que posee la imagen de arrastre.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CImageList:: EndDrag](#enddrag).

##  <a name="dragmove"></a>CImageList::D ragMove

Llame a esta función para mover la imagen que se está arrastrando durante una operación de arrastrar y colocar.

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>Parámetros

*pt*<br/>
Nueva posición de arrastre.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Normalmente, se llama a esta función en respuesta a un mensaje WM_MOUSEMOVE. Para comenzar una operación de arrastre, utilice la función miembro `BeginDrag`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

##  <a name="dragshownolock"></a>CImageList::D ragShowNolock

Muestra u oculta la imagen de arrastre durante una operación de arrastre, sin bloquear la ventana.

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bShow*<br/>
Especifica si se va a mostrar la imagen de arrastre.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

La función [CImageList::D ragenter](#dragenter) bloquea todas las actualizaciones de la ventana durante una operación de arrastre. Sin embargo, esta función no bloquea la ventana.

##  <a name="draw"></a>CImageList::D RAW

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
Puntero al contexto de dispositivo de destino.

*nImage*<br/>
Índice de base cero de la imagen que se va a dibujar.

*pt*<br/>
Ubicación en la que se va a dibujar dentro del contexto de dispositivo especificado.

*nStyle*<br/>
Marca que especifica el estilo de dibujo. Puede ser uno o varios de estos valores:

|Value|Significado|
|-----------|-------------|
|ILD_BLEND25, ILD_FOCUS|Dibuja la imagen y combina el 25 por ciento con el color de resaltado del sistema. Este valor no tiene ningún efecto si la lista de imágenes no contiene una máscara.|
|ILD_BLEND50, ILD_SELECTED, ILD_BLEND|Dibuja la imagen y combina el 50 por ciento con el color de resaltado del sistema. Este valor no tiene ningún efecto si la lista de imágenes no contiene una máscara.|
|ILD_MASK|Dibuja la máscara.|
|ILD_NORMAL|Dibuja la imagen con el color de fondo de la lista de imágenes. Si el color de fondo es el valor de CLR_NONE, la imagen se dibuja de forma transparente con la máscara.|
|ILD_TRANSPARENT|Dibuja la imagen de forma transparente con la máscara, independientemente del color de fondo.|

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CImageList:: SetOverlayImage](#setoverlayimage).

##  <a name="drawex"></a>CImageList::D rawEx

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
Puntero al contexto de dispositivo de destino.

*nImage*<br/>
Índice de base cero de la imagen que se va a dibujar.

*pt*<br/>
Ubicación en la que se va a dibujar dentro del contexto de dispositivo especificado.

*SZ*<br/>
Tamaño de la parte de la imagen que se va a dibujar con respecto a la esquina superior izquierda de la imagen. Consulte *DX* y *DY* en [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) en el Windows SDK.

*clrBk*<br/>
Color de fondo de la imagen. Vea *rgbBk* en [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) en el Windows SDK.

*clrFg*<br/>
Color de primer plano de la imagen. Vea *rgbFg* en [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) en el Windows SDK.

*nStyle*<br/>
Marca que especifica el estilo de dibujo. Vea *fStyle* en [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

La función usa el estilo de dibujo especificado y combina la imagen con el color especificado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

##  <a name="drawindirect"></a>CImageList::D rawIndirect

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
Puntero a una estructura [IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) que contiene información sobre la operación de dibujo.

*pDC*<br/>
Un puntero al contexto de dispositivo de destino. Debe eliminar este objeto [CDC](../../mfc/reference/cdc-class.md) cuando haya terminado.

*nImage*<br/>
Índice de base cero de la imagen que se va a dibujar.

*pt*<br/>
Estructura de [punto](/previous-versions/dd162805\(v=vs.85\)) que contiene las coordenadas x e y donde se dibujará la imagen.

*SZ*<br/>
Estructura de [tamaño](/windows/win32/api/windef/ns-windef-size) que indica el tamaño de la imagen que se va a dibujar.

*ptOrigin*<br/>
Estructura de [punto](/previous-versions/dd162805\(v=vs.85\)) que contiene las coordenadas x e y que especifican la esquina superior izquierda de la operación de dibujo con respecto a la propia imagen. Los píxeles de la imagen que están a la izquierda de la coordenada x y sobre la coordenada y no se dibujan.

*fStyle*<br/>
Marca que especifica el estilo de dibujo y, opcionalmente, la imagen de superposición. Vea la sección Comentarios para obtener información sobre la imagen de superposición. La implementación predeterminada de MFC, ILD_NORMAL, dibuja la imagen con el color de fondo de la lista de imágenes. Si el color de fondo es el valor de CLR_NONE, la imagen se dibuja de forma transparente con una máscara.

Otros estilos posibles se describen en el miembro *fStyle* de la estructura [IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) .

*dwRop*<br/>
Valor que especifica un código de operación de trama. Estos códigos definen el modo en que los datos de color del rectángulo de origen se combinarán con los datos de color del rectángulo de destino para lograr el color final. La implementación predeterminada de MFC, SRCCOPY, copia el rectángulo de origen directamente en el rectángulo de destino. Este parámetro se omite si el parámetro *fStyle* no incluye la marca ILD_ROP.

Otros valores posibles se describen en el miembro *dwRop* de la estructura [IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) .

*rgbBack*<br/>
Color de fondo de la imagen, de forma predeterminada CLR_DEFAULT. Este parámetro puede ser un valor RGB definido por la aplicación o uno de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|CLR_DEFAULT|Color de fondo predeterminado. La imagen se dibuja con el color de fondo de la lista de imágenes.|
|CLR_NONE|Ningún color de fondo. La imagen se dibuja de forma transparente.|

*rgbFore*<br/>
Color de primer plano de la imagen, de forma predeterminada CLR_DEFAULT. Este parámetro puede ser un valor RGB definido por la aplicación o uno de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|CLR_DEFAULT|Color de primer plano predeterminado. La imagen se dibuja con el color de resaltado del sistema como el color de primer plano.|
|CLR_NONE|Ningún color de fusión. La imagen se combina con el color del contexto del dispositivo de destino.|

Este parámetro solo se usa si *fStyle* incluye la marca ILD_BLEND25 o ILD_BLEND50.

*fState*<br/>
Marca que especifica el estado del dibujo. Este miembro puede contener una o varias marcas de estado de la lista de imágenes.

*Frame*<br/>
Afecta al comportamiento de los efectos saturados y de mezcla alfa.

Cuando se usa con ILS_SATURATE, este miembro contiene el valor que se agrega a cada componente de color del tripledo RGB para cada píxel del icono.

Cuando se usa con ILS_APLHA, este miembro contiene el valor del canal alfa. Este valor puede estar comprendido entre 0 y 255, donde 0 es completamente transparente y 255 es totalmente opaco.

*crEffect*<br/>
Valor de [COLORREF](/windows/win32/gdi/colorref) que se usa para los efectos de resplandor y sombra.

### <a name="return-value"></a>Valor devuelto

TRUE si la imagen se dibuja correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Use la primera versión si desea rellenar la estructura de Win32. Use la segunda versión si desea sacar partido de uno o más de los argumentos predeterminados de MFC o evitar administrar la estructura.

Una imagen de superposición es una imagen que se dibuja sobre la imagen principal, especificada en esta función miembro, mediante el parámetro *nImage* . Dibuje una máscara de superposición mediante la función miembro [Draw](#draw) con el índice basado en uno de la máscara de superposición especificada mediante la macro [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

##  <a name="enddrag"></a>CImageList:: EndDrag

Llame a esta función para finalizar una operación de arrastre.

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>Observaciones

Para comenzar una operación de arrastre, utilice la función miembro `BeginDrag`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

##  <a name="extracticon"></a>CImageList:: ExtractIcon

Llame a esta función para crear un icono basado en una imagen y su máscara relacionada en una lista de imágenes.

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>Parámetros

*nImage*<br/>
Índice de base cero de la imagen.

### <a name="return-value"></a>Valor devuelto

Identificador del icono si se realiza correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Este método se basa en el comportamiento de la macro [ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) para crear el icono. Consulte la macro [ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) para obtener más información sobre la creación y limpieza de iconos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

##  <a name="fromhandle"></a>CImageList:: FromHandle

Devuelve un puntero a un objeto `CImageList` cuando se proporciona un identificador a una lista de imágenes.

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parámetros

*hImageList*<br/>
Especifica la lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto de `CImageList` si se realiza correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Si aún no se ha adjuntado un `CImageList` al identificador, se crea y se adjunta un objeto de `CImageList` temporal. Este objeto de `CImageList` temporal solo es válido hasta la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos, momento en el que se eliminarán todos los objetos temporales.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

##  <a name="fromhandlepermanent"></a>CImageList:: FromHandlePermanent

Devuelve un puntero a un objeto `CImageList` cuando se proporciona un identificador a una lista de imágenes.

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parámetros

*hImageList*<br/>
Especifica la lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto de `CImageList` si se realiza correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Si un objeto de `CImageList` no está asociado al identificador, se devuelve NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

##  <a name="getbkcolor"></a>CImageList:: GetBkColor

Llame a esta función para recuperar el color de fondo actual para una lista de imágenes.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de color RGB del color de fondo del objeto `CImageList`.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CImageList:: SetBkColor](#setbkcolor).

##  <a name="getdragimage"></a>CImageList:: GetDragImage

Obtiene la lista de imágenes temporales que se usa para arrastrar.

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>Parámetros

*lpPoint*<br/>
Dirección de una estructura de [punto](/previous-versions/dd162805\(v=vs.85\)) que recibe la posición de arrastre actual.

*lpPointHotSpot*<br/>
Dirección de una estructura de `POINT` que recibe el desplazamiento de la imagen de arrastre con respecto a la posición de arrastre.

### <a name="return-value"></a>Valor devuelto

Si es correcto, puntero a la lista de imágenes temporales que se usa para arrastrar; de lo contrario, es NULL.

##  <a name="getimagecount"></a>CImageList:: GetImageCount

Llame a esta función para recuperar el número de imágenes de una lista de imágenes.

```
int GetImageCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de imágenes.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CImageList:: ExtractIcon](#extracticon).

##  <a name="getimageinfo"></a>CImageList:: GetImageInfo

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
Puntero a una estructura [IMAGEINFO](/windows/win32/api/commctrl/ns-commctrl-imageinfo) que recibe información sobre la imagen. La información de esta estructura se puede usar para manipular directamente los mapas de bits de la imagen.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

La estructura `IMAGEINFO` contiene información sobre una imagen de una lista de imágenes.

##  <a name="getsafehandle"></a>CImageList:: GetSafeHandle

Llame a esta función para recuperar el `m_hImageList` miembro de datos.

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador de la lista de imágenes adjunta; de lo contrario, es NULL si no hay ningún objeto asociado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

##  <a name="m_himagelist"></a>CImageList:: m_hImageList

Identificador de la lista de imágenes asociada a este objeto.

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>Observaciones

El miembro de datos `m_hImageList` es una variable pública de tipo HIMAGELIST.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

##  <a name="operator_himagelist"></a>CImageList:: Operator HIMAGELIST

Utilice este operador para obtener el identificador adjunto del objeto de `CImageList`.

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcto, identificador de la lista de imágenes representada por el objeto `CImageList`; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Este operador es un operador de conversión, que admite el uso directo de un objeto HIMAGELIST.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

##  <a name="read"></a>CImageList:: Read

Llame a esta función para leer una lista de imágenes de un archivo.

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>Parámetros

*pArchive*<br/>
Puntero a un objeto `CArchive` del que se va a leer la lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

##  <a name="remove"></a>CImageList:: Remove

Llame a esta función para quitar una imagen de un objeto de lista de imágenes.

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>Parámetros

*nImage*<br/>
Índice de base cero de la imagen que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Ahora, todos los elementos que siguen a *nImage* bajan una posición. Por ejemplo, si una lista de imágenes contiene dos elementos, al eliminar el primer elemento, el elemento restante quedará ahora en la primera posición. *nImage*= 0 para el elemento en la primera posición.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

##  <a name="replace"></a>CImageList:: Replace

Llame a esta función para reemplazar una imagen de una lista de imágenes por una imagen nueva.

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
Índice de base cero de la imagen que se va a reemplazar.

*pbmImage*<br/>
Puntero al mapa de bits que contiene la imagen.

*pbmMask*<br/>
Puntero al mapa de bits que contiene la máscara. Si no se usa ninguna máscara con la lista de imágenes, se omite este parámetro.

*hIcon*<br/>
Identificador del icono que contiene el mapa de bits y la máscara de la nueva imagen.

### <a name="return-value"></a>Valor devuelto

La versión que devuelve BOOL devuelve un valor distinto de cero si es correcto; de lo contrario, es 0.

La versión que devuelve **int** devuelve el índice de base cero de la imagen si se realiza correctamente; de lo contrario,-1.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro después de llamar a [SetImageCount](#setimagecount) para asignar las nuevas imágenes válidas a los números de índice de la imagen de marcador de posición.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CImageList:: SetImageCount](#setimagecount).

##  <a name="setbkcolor"></a>CImageList:: SetBkColor

Llame a esta función para establecer el color de fondo de una lista de imágenes.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parámetros

*compra*<br/>
Color de fondo que se va a establecer. Se puede CLR_NONE. En ese caso, las imágenes se dibujan de forma transparente mediante la máscara.

### <a name="return-value"></a>Valor devuelto

El color de fondo anterior si se realiza correctamente; de lo contrario CLR_NONE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

##  <a name="setdragcursorimage"></a>CImageList:: SetDragCursorImage

Crea una nueva imagen de arrastre combinando la imagen especificada (normalmente una imagen de cursor del mouse) con la imagen de arrastre actual.

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parámetros

*nDrag*<br/>
Índice de la nueva imagen que se va a combinar con la imagen de arrastre.

*ptHotSpot*<br/>
Posición de la zona activa dentro de la nueva imagen.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Dado que las funciones de arrastre usan la nueva imagen durante una operación de arrastre, debe usar la función [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor) de Windows para ocultar el cursor del mouse real después de llamar a `CImageList::SetDragCursorImage`. De lo contrario, puede parecer que el sistema tiene dos cursores del mouse mientras dure la operación de arrastre.

##  <a name="setimagecount"></a>CImageList:: SetImageCount

Llame a esta función miembro para restablecer el número de imágenes de un objeto `CImageList`.

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>Parámetros

*uNewCount*<br/>
Valor que especifica el nuevo número total de imágenes de la lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Si llama a esta función miembro para aumentar el número de imágenes de la lista de imágenes, llame a [Replace](#replace) por cada imagen adicional para asignar los nuevos índices a imágenes válidas. Si no puede asignar los índices a imágenes válidas, las operaciones de dibujo que crean las imágenes nuevas serán impredecibles.

Si reduce el tamaño de una lista de imágenes mediante esta función, se liberan las imágenes truncadas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

##  <a name="setoverlayimage"></a>CImageList:: SetOverlayImage

Llame a esta función para agregar el índice de base cero de una imagen a la lista de imágenes que se van a usar como máscaras superpuestas.

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>Parámetros

*nImage*<br/>
Índice de base cero de la imagen que se va a usar como máscara de superposición.

*nOverlay*<br/>
Índice de base uno de la máscara de superposición.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Se pueden agregar hasta cuatro índices a la lista.

Una máscara superpuesta es una imagen dibujada de forma transparente sobre otra imagen. Dibuje una máscara de superposición sobre una imagen mediante la función de miembro [CImageList::D RAW](#draw) con el índice basado en uno de la máscara de superposición especificada mediante la macro INDEXTOOVERLAYMASK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

##  <a name="write"></a>CImageList:: Write

Llame a esta función para escribir un objeto de lista de imágenes en un archivo.

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>Parámetros

*pArchive*<br/>
Puntero a un objeto `CArchive` en el que se va a almacenar la lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>Consulte también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CListCtrl (clase)](../../mfc/reference/clistctrl-class.md)<br/>
[CTabCtrl (clase)](../../mfc/reference/ctabctrl-class.md)
