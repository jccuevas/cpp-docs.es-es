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
ms.openlocfilehash: eff2d0c1de88ebd9d949ebe197563c87c17e5b05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372448"
---
# <a name="cimagelist-class"></a>CImageList (clase)

Proporciona la funcionalidad del control de lista de imágenes común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CImageList : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CImageList::CImageList](#cimagelist)|Construye un objeto `CImageList`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CImageList::Add](#add)|Agrega una imagen o imágenes a una lista de imágenes.|
|[CImageList::Attach](#attach)|Asocia una lista de `CImageList` imágenes a un objeto.|
|[CImageList::BeginDrag](#begindrag)|Comienza a arrastrar una imagen.|
|[CImageList::Copy](#copy)|Copia una imagen `CImageList` dentro de un objeto.|
|[CImageList::Create](#create)|Inicializa una lista de imágenes `CImageList` y la adjunta a un objeto.|
|[CImageList::DeleteImageList](#deleteimagelist)|Elimina una lista de imágenes.|
|[CImageList::DeleteTempMap](#deletetempmap)|Llamado por el controlador de tiempo de `CImageList` inactividad `FromHandle` [CWinApp](../../mfc/reference/cwinapp-class.md) para eliminar cualquier objeto temporal creado por .|
|[CImageList::Detach](#detach)|Separa un objeto de `CImageList` lista de imágenes de un objeto y devuelve un identificador a una lista de imágenes.|
|[CImageList::DragEnter](#dragenter)|Bloquea las actualizaciones durante una operación de arrastre y muestra la imagen de arrastre en una posición especificada.|
|[CImageList::DragLeave](#dragleave)|Desbloquea la ventana y oculta la imagen de arrastre para que la ventana se pueda actualizar.|
|[CImageList::DragMove](#dragmove)|Mueve la imagen que se está arrastrando durante una operación de arrastrar y colocar.|
|[CImageList::DragShowNolock](#dragshownolock)|Muestra u oculta la imagen de arrastre durante una operación de arrastre, sin bloquear la ventana.|
|[CImageList::Draw](#draw)|Dibuja la imagen que se arrastra durante una operación de arrastrar y colocar.|
|[CImageList::DrawEx](#drawex)|Dibuja un elemento de lista de imágenes en el contexto de dispositivo especificado. La función utiliza el estilo de dibujo especificado y combina la imagen con el color especificado.|
|[CImageList::DrawIndirect](#drawindirect)|Dibuja una imagen de una lista de imágenes.|
|[CImageList::EndDrag](#enddrag)|Finaliza una operación de arrastre.|
|[CImageList::ExtractIcon](#extracticon)|Crea un icono basado en una imagen y una máscara en una lista de imágenes.|
|[CImageList::FromHandle](#fromhandle)|Devuelve un puntero `CImageList` a un objeto cuando se le da un identificador a una lista de imágenes. Si no hay un objeto `CImageList` asociado al identificador, se crea y asocia un objeto `CImageList` temporal.|
|[CImageList::FromHandlePermanent](#fromhandlepermanent)|Devuelve un puntero `CImageList` a un objeto cuando se le da un identificador a una lista de imágenes. Si `CImageList` un objeto no está asociado al identificador, se devuelve NULL.|
|[CImageList::GetBkColor](#getbkcolor)|Recupera el color de fondo actual de una lista de imágenes.|
|[CImageList::GetDragImage](#getdragimage)|Obtiene la lista de imágenes temporales que se utiliza para arrastrar.|
|[CImageList::GetImageCount](#getimagecount)|Recupera el número de imágenes de una lista de imágenes.|
|[CImageList::GetImageInfo](#getimageinfo)|Recupera información sobre una imagen.|
|[CImageList::GetSafeHandle](#getsafehandle)|Recupera `m_hImageList`.|
|[CImageList::Read](#read)|Lee una lista de imágenes de un archivo.|
|[CImageList::Remove](#remove)|Elimina una imagen de una lista de imágenes.|
|[CImageList::Reemplazar](#replace)|Reemplaza una imagen de una lista de imágenes por una nueva imagen.|
|[CImageList::SetBkColor](#setbkcolor)|Establece el color de fondo de una lista de imágenes.|
|[CImageList::SetDragCursorImage](#setdragcursorimage)|Crea una nueva imagen de arrastre.|
|[CImageList::SetImageCount](#setimagecount)|Restablece el recuento de imágenes en una lista de imágenes.|
|[CImageList::SetOverlayImage](#setoverlayimage)|Agrega el índice de base cero de una imagen a la lista de imágenes que se utilizarán como máscaras de superposición.|
|[CImageList::Write](#write)|Escribe una lista de imágenes en un archivo.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CImageList::operator HIMAGELIST](#operator_himagelist)|Devuelve el HIMAGELIST `CImageList`asociado al archivo .|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CImageList::m_hImageList](#m_himagelist)|Identificador que contiene la lista de imágenes adjunta a este objeto.|

## <a name="remarks"></a>Observaciones

Una "lista de imágenes" es una colección de imágenes del mismo tamaño, cada una de las cuales puede ser referida por su índice de base cero. Las listas de imágenes se utilizan para administrar de forma eficaz grandes conjuntos de iconos o mapas de bits. Todas las imágenes de una lista de imágenes están contenidas en un único mapa de bits amplio en formato de dispositivo de pantalla. Una lista de imágenes también puede incluir un mapa de bits monocromo que contiene máscaras utilizadas para dibujar imágenes de forma transparente (estilo de icono). La interfaz de programación de aplicaciones (API) de Microsoft Win32 proporciona funciones de lista de imágenes que le permiten dibujar imágenes, crear y destruir listas de imágenes, agregar y eliminar imágenes, reemplazar imágenes, combinar imágenes y arrastrar imágenes.

Este control (y, por lo tanto, la `CImageList` clase) solo está disponible para programas que se ejecutan en Windows 95/98 y Windows NT versión 3.51 y versiones posteriores.

Para obtener más `CImageList`información sobre el uso de , vea [Controles](../../mfc/controls-mfc.md) y [uso de CImageList](../../mfc/using-cimagelist.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

## <a name="cimagelistadd"></a><a name="add"></a>CImageList::Add

Llame a esta función para agregar una o más imágenes o un icono a una lista de imágenes.

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
Puntero al mapa de bits que contiene la máscara. Si no se utiliza ninguna máscara con la lista de imágenes, se omite este parámetro.

*crMask*<br/>
Color utilizado para generar la máscara. Cada píxel de este color en el mapa de bits dado se cambia a negro y el bit correspondiente en la máscara se establece en uno.

*hIcon*<br/>
Control del icono que contiene el mapa de bits y la máscara de la nueva imagen.

### <a name="return-value"></a>Valor devuelto

El índice de base cero de la primera imagen nueva si se realiza correctamente; de lo contrario - 1.

### <a name="remarks"></a>Observaciones

Usted es responsable de liberar el identificador de icono cuando haya terminado con él.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

## <a name="cimagelistattach"></a><a name="attach"></a>CImageList::Attach

Llame a esta función para `CImageList` adjuntar una lista de imágenes a un objeto.

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parámetros

*hImageList*<br/>
Identificador de un objeto de lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el archivo adjunto se realizó correctamente; de lo contrario 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

## <a name="cimagelistbegindrag"></a><a name="begindrag"></a>CImageList::BeginDrag

Llame a esta función para comenzar a arrastrar una imagen.

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parámetros

*nImage*<br/>
El índice de base cero de la imagen que se va a arrastrar.

*ptHotSpot*<br/>
Coordenadas de la posición de arrastre inicial (normalmente, la posición del cursor). Las coordenadas son relativas a la esquina superior izquierda de la imagen.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función crea una lista de imágenes temporal que se utiliza para arrastrar. La imagen combina la imagen especificada y su máscara con el cursor actual. En respuesta a los mensajes de WM_MOUSEMOVE posteriores, puede mover la imagen de arrastre mediante la `DragMove` función miembro. Para finalizar la operación de `EndDrag` arrastre, puede utilizar la función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

## <a name="cimagelistcimagelist"></a><a name="cimagelist"></a>CImageList::CImageList

Construye un objeto `CImageList`.

```
CImageList();
```

## <a name="cimagelistcopy"></a><a name="copy"></a>CImageList::Copy

Esta función miembro implementa el comportamiento de la [función](/windows/win32/api/commctrl/nf-commctrl-imagelist_copy)Win32 ImageList_Copy , como se describe en el Windows SDK.

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
El índice de base cero de la imagen que se utilizará como destino de la operación de copia.

*Isrc*<br/>
El índice de base cero de la imagen que se utilizará como origen de la operación de copia.

*uFlags*<br/>
El valor de marca de bits que especifica el tipo de operación de copia que se va a realizar. Este parámetro puede ser uno de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|ILCF_MOVE|La imagen de origen se copia en el índice de la imagen de destino. Esta operación da como resultado varias instancias de una imagen determinada. ILCF_MOVE es el valor predeterminado.|
|ILCF_SWAP|Las imágenes de origen y destino intercambian posiciones dentro de la lista de imágenes.|

*pSrc*<br/>
Puntero a `CImageList` un objeto que es el destino de la operación de copia.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

## <a name="cimagelistcreate"></a><a name="create"></a>CImageList::Create

Inicializa una lista de imágenes y la adjunta a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto.

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

*Cx*<br/>
Dimensiones de cada imagen, en píxeles.

*Cy*<br/>
Dimensiones de cada imagen, en píxeles.

*nFlags*<br/>
Especifica el tipo de lista de imágenes que se va a crear. Este parámetro puede ser una combinación de los siguientes `ILC_COLOR` valores, pero solo puede incluir uno de los valores.

|Value|Significado|
|-----------|-------------|
|ILC_COLOR|Utilice el comportamiento predeterminado si no se especifica ninguno de los otros indicadores ILC_COLOR*. Normalmente, el valor predeterminado es ILC_COLOR4; pero para los controladores de pantalla más antiguos, el valor predeterminado es ILC_COLORDDB.|
|ILC_COLOR4|Utilice una sección de mapa de bits independiente del dispositivo (DIB) de 4 bits (16 colores) como mapa de bits para la lista de imágenes.|
|ILC_COLOR8|Utilice una sección DIB de 8 bits. Los colores utilizados para la tabla de colores son los mismos colores que la paleta de medios tonos.|
|ILC_COLOR16|Utilice una sección DIB de 16 bits (32/64k color).|
|ILC_COLOR24|Utilice una sección DIB de 24 bits.|
|ILC_COLOR32|Utilice una sección DIB de 32 bits.|
|ILC_COLORDDB|Utilice un mapa de bits dependiente del dispositivo.|
|ILC_MASK|Utiliza una máscara. La lista de imágenes contiene dos mapas de bits, uno de los cuales es un mapa de bits monocromo utilizado como máscara. Si no se incluye este valor, la lista de imágenes contiene solo un mapa de bits. Consulte [Dibujo de imágenes de una lista](../../mfc/drawing-images-from-an-image-list.md) de imágenes para obtener información adicional sobre las imágenes enmascaradas.|

*nInicial*<br/>
Número de imágenes que la lista de imágenes contiene inicialmente.

*nGrow*<br/>
Número de imágenes por las que la lista de imágenes puede crecer cuando el sistema necesita cambiar el tamaño de la lista para dejar espacio para nuevas imágenes. Este parámetro representa el número de imágenes nuevas que puede contener la lista de imágenes redimensionadas.

*nBitmapID*<br/>
Identificadores de recursos del mapa de bits que se asociarán a la lista de imágenes.

*crMask*<br/>
Color utilizado para generar una máscara. Cada píxel de este color en el mapa de bits especificado se cambia a negro y el bit correspondiente en la máscara se establece en uno.

*lpszBitmapID*<br/>
Cadena que contiene los identificadores de recursos de las imágenes.

*imagelist1*<br/>
Referencia a un objeto `CImageList`.

*nImage1*<br/>
Indice de la primera imagen existente.

*imagelist2*<br/>
Referencia a un objeto `CImageList`.

*nImage2*<br/>
Indice de la segunda imagen existente.

*Dx*<br/>
Desplazamiento del eje X de la segunda imagen en relación con la primera imagen, en píxeles.

*Dy*<br/>
Desplazamiento del eje Y de la segunda imagen en relación con la primera imagen, en píxeles.

*pImageList*<br/>
Puntero a un objeto `CImageList` .

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Se construye `CImageList` un en dos pasos. En primer lugar, llame `Create`al constructor y, a continuación, `CImageList` llame a , que crea la lista de imágenes y la adjunta al objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

## <a name="cimagelistdeleteimagelist"></a><a name="deleteimagelist"></a>CImageList::DeleteImageList

Llame a esta función para eliminar una lista de imágenes.

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

## <a name="cimagelistdeletetempmap"></a><a name="deletetempmap"></a>CImageList::DeleteTempMap

Llamado automáticamente `CWinApp` por el controlador `DeleteTempMap` de tiempo `CImageList` de inactividad, elimina los objetos `hImageList`temporales creados `ImageList` por [FromHandle](#fromhandle), pero no destruye ningún identificador ( ) asociado temporalmente con los objetos.

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

## <a name="cimagelistdetach"></a><a name="detach"></a>CImageList::Detach

Llame a esta función para separar `CImageList` un objeto de lista de imágenes de un objeto.

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>Valor devuelto

Identificador de un objeto de lista de imágenes.

### <a name="remarks"></a>Observaciones

Esta función devuelve un identificador al objeto de lista de imágenes.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CImageList::Attach](#attach).

## <a name="cimagelistdragenter"></a><a name="dragenter"></a>CImageList::DragEnter

Durante una operación de arrastre, bloquea las actualizaciones de la ventana especificada por *pWndLock* y muestra la imagen de arrastre en la posición especificada por *el punto*.

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*pWndLock*<br/>
Puntero a la ventana propietaria de la imagen de arrastre.

*Punto*<br/>
Posición en la que se mostrará la imagen de arrastre. Las coordenadas son relativas a la esquina superior izquierda de la ventana (no al área de cliente).

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Las coordenadas son relativas a la esquina superior izquierda de la ventana, por lo que debe compensar los anchos de los elementos de la ventana, como el borde, la barra de título y la barra de menús, al especificar las coordenadas.

Si *pWndLock* es NULL, esta función dibuja la imagen en el contexto de visualización asociado a la ventana de escritorio y las coordenadas son relativas a la esquina superior izquierda de la pantalla.

Esta función bloquea todas las demás actualizaciones de la ventana dada durante la operación de arrastre. Si necesita realizar cualquier dibujo durante una operación de arrastre, como resaltar el destino de una operación de arrastrar y colocar, puede ocultar temporalmente la imagen arrastrada mediante la función [CImageList::DragLeave.](#dragleave)

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CImageList::BeginDrag](#begindrag).

## <a name="cimagelistdragleave"></a><a name="dragleave"></a>CImageList::DragLeave

Desbloquea la ventana especificada por *pWndLock* y oculta la imagen de arrastre, lo que permite actualizar la ventana.

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

## <a name="cimagelistdragmove"></a><a name="dragmove"></a>CImageList::DragMove

Llame a esta función para mover la imagen que se está arrastrando durante una operación de arrastrar y colocar.

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>Parámetros

*Pt*<br/>
Nueva posición de arrastre.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Normalmente se llama a esta función en respuesta a un mensaje WM_MOUSEMOVE. Para iniciar una operación `BeginDrag` de arrastre, utilice la función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

## <a name="cimagelistdragshownolock"></a><a name="dragshownolock"></a>CImageList::DragShowNolock

Muestra u oculta la imagen de arrastre durante una operación de arrastre, sin bloquear la ventana.

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bMostrar*<br/>
Especifica si se va a mostrar la imagen de arrastre.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

La función [CImageList::DragEnter](#dragenter) bloquea todas las actualizaciones de la ventana durante una operación de arrastre. Esta función, sin embargo, no bloquea la ventana.

## <a name="cimagelistdraw"></a><a name="draw"></a>CImageList::Draw

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
El índice de base cero de la imagen que se va a dibujar.

*Pt*<br/>
Ubicación en la que se dibujará dentro del contexto de dispositivo especificado.

*nStyle*<br/>
Marcar especificando el estilo de dibujo. Puede ser uno o más de estos valores:

|Value|Significado|
|-----------|-------------|
|ILD_BLEND25, ILD_FOCUS|Dibuja la imagen, mezclando el 25 por ciento con el color de resaltado del sistema. Este valor no tiene ningún efecto si la lista de imágenes no contiene una máscara.|
|ILD_BLEND50, ILD_SELECTED, ILD_BLEND|Dibuja la imagen, mezclando el 50 por ciento con el color de resaltado del sistema. Este valor no tiene ningún efecto si la lista de imágenes no contiene una máscara.|
|ILD_MASK|Dibuja la máscara.|
|ILD_NORMAL|Dibuja la imagen utilizando el color de fondo de la lista de imágenes. Si el color de fondo es el valor CLR_NONE, la imagen se dibuja de forma transparente utilizando la máscara.|
|ILD_TRANSPARENT|Dibuja la imagen de forma transparente utilizando la máscara, independientemente del color de fondo.|

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CImageList::SetOverlayImage](#setoverlayimage).

## <a name="cimagelistdrawex"></a><a name="drawex"></a>CImageList::DrawEx

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
El índice de base cero de la imagen que se va a dibujar.

*Pt*<br/>
Ubicación en la que se dibujará dentro del contexto de dispositivo especificado.

*Sz*<br/>
Tamaño de la parte de la imagen que se va a dibujar en relación con la esquina superior izquierda de la imagen. Consulte *dx* y *dy* en [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) en el Windows SDK.

*clrBk*<br/>
Color de fondo de la imagen. Consulte *rgbBk* en [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) en el Windows SDK.

*clrFg*<br/>
Color de primer plano de la imagen. Consulte *rgbFg* en [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) en el Windows SDK.

*nStyle*<br/>
Marcar especificando el estilo de dibujo. Consulte *fStyle* en [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

La función utiliza el estilo de dibujo especificado y combina la imagen con el color especificado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

## <a name="cimagelistdrawindirect"></a><a name="drawindirect"></a>CImageList::DrawIndirect

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
Un puntero al contexto del dispositivo de destino. Debe eliminar este objeto [CDC](../../mfc/reference/cdc-class.md) cuando haya terminado con él.

*nImage*<br/>
El índice de base cero de la imagen que se va a dibujar.

*Pt*<br/>
Estructura [POINT](/previous-versions/dd162805\(v=vs.85\)) que contiene las coordenadas x e y donde se dibujará la imagen.

*Sz*<br/>
Estructura [SIZE](/windows/win32/api/windef/ns-windef-size) que indica el tamaño de la imagen que se va a dibujar.

*ptOrigin*<br/>
Estructura [POINT](/previous-versions/dd162805\(v=vs.85\)) que contiene las coordenadas X e Y que especifican la esquina superior izquierda de la operación de dibujo con respecto a la propia imagen. Los píxeles de la imagen que se encuentran a la izquierda de la coordenada x y por encima de la coordenada y no se dibujan.

*fStyle*<br/>
Marcar especificando el estilo de dibujo y, opcionalmente, la imagen de superposición. Consulte la sección Comentarios para obtener información sobre la imagen superpuesta. La implementación predeterminada de MFC, ILD_NORMAL, dibuja la imagen con el color de fondo de la lista de imágenes. Si el color de fondo es el valor CLR_NONE, la imagen se dibuja de forma transparente utilizando una máscara.

Otros estilos posibles se describen en el *fStyle* miembro de la [IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) estructura.

*dwRop*<br/>
Valor que especifica un código de operación ráster. Estos códigos definen cómo se combinarán los datos de color para el rectángulo de origen con los datos de color del rectángulo de destino para lograr el color final. La implementación predeterminada de MFC, SRCCOPY, copia el rectángulo de origen directamente en el rectángulo de destino. Este parámetro se omite si el *parámetro fStyle* no incluye el ILD_ROP marca.

Otros valores posibles se describen en el miembro *dwRop* de la estructura [IMAGELISTDRAWPARAMS.](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams)

*rgbBack*<br/>
El color de fondo de la imagen, de forma predeterminada CLR_DEFAULT. Este parámetro puede ser un valor RGB definido por la aplicación o uno de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|CLR_DEFAULT|Color de fondo predeterminado. La imagen se dibuja utilizando el color de fondo de la lista de imágenes.|
|CLR_NONE|Sin color de fondo. La imagen se dibuja de forma transparente.|

*rgbFore*<br/>
Color de primer plano de la imagen, de forma predeterminada CLR_DEFAULT. Este parámetro puede ser un valor RGB definido por la aplicación o uno de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|CLR_DEFAULT|Color de primer plano predeterminado. La imagen se dibuja utilizando el color de resaltado del sistema como color de primer plano.|
|CLR_NONE|Sin color de mezcla. La imagen se mezcla con el color del contexto del dispositivo de destino.|

Este parámetro solo se utiliza si *fStyle* incluye la marca ILD_BLEND25 o ILD_BLEND50.

*fState*<br/>
Marcar especificando el estado del dibujo. Este miembro puede contener uno o más indicadores de estado de lista de imágenes.

*Marco*<br/>
Afecta el comportamiento de los efectos de saturación y fusión alfa.

Cuando se utiliza con ILS_SATURATE, este miembro contiene el valor que se agrega a cada componente de color del triplete RGB para cada píxel del icono.

Cuando se utiliza con ILS_APLHA, este miembro contiene el valor para el canal alfa. Este valor puede ser de 0 a 255, siendo 0 completamente transparente y 255 completamente opaco.

*crEffect*<br/>
Valor [COLORREF](/windows/win32/gdi/colorref) utilizado para efectos de resplandor y sombra.

### <a name="return-value"></a>Valor devuelto

TRUESi la imagen se dibuja correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Utilice la primera versión si desea rellenar la estructura Win32 usted mismo. Use la segunda versión si desea aprovechar uno o varios de los argumentos predeterminados de MFC o evitar la administración de la estructura.

Una imagen de superposición es una imagen que se dibuja encima de la imagen principal, especificada en esta función miembro por el *nImage* parámetro. Dibuje una máscara de superposición mediante el [Draw](#draw) función miembro con el índice basado en uno de la máscara de superposición especificado mediante el [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask) macro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

## <a name="cimagelistenddrag"></a><a name="enddrag"></a>CImageList::EndDrag

Llame a esta función para finalizar una operación de arrastre.

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>Observaciones

Para iniciar una operación `BeginDrag` de arrastre, utilice la función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

## <a name="cimagelistextracticon"></a><a name="extracticon"></a>CImageList::ExtractIcon

Llame a esta función para crear un icono basado en una imagen y su máscara relacionada en una lista de imágenes.

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>Parámetros

*nImage*<br/>
Indice de base cero de la imagen.

### <a name="return-value"></a>Valor devuelto

Control del icono si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Este método se basa en el comportamiento de la [macro ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) para crear el icono. Consulte la macro [ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) para obtener más información sobre la creación y limpieza de iconos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

## <a name="cimagelistfromhandle"></a><a name="fromhandle"></a>CImageList::FromHandle

Devuelve un puntero `CImageList` a un objeto cuando se le da un identificador a una lista de imágenes.

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parámetros

*hImageList*<br/>
Especifica la lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Un puntero `CImageList` a un objeto si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Si `CImageList` a aún no está asociado `CImageList` al identificador, se crea y adjunta un objeto temporal. Este `CImageList` objeto temporal solo es válido hasta la próxima vez que la aplicación tenga tiempo de inactividad en su bucle de eventos, momento en el que se eliminan todos los objetos temporales.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

## <a name="cimagelistfromhandlepermanent"></a><a name="fromhandlepermanent"></a>CImageList::FromHandlePermanent

Devuelve un puntero `CImageList` a un objeto cuando se le da un identificador a una lista de imágenes.

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parámetros

*hImageList*<br/>
Especifica la lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Un puntero `CImageList` a un objeto si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Si `CImageList` un objeto no está asociado al identificador, se devuelve NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

## <a name="cimagelistgetbkcolor"></a><a name="getbkcolor"></a>CImageList::GetBkColor

Llame a esta función para recuperar el color de fondo actual de una lista de imágenes.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Valor devuelto

El valor de `CImageList` color RGB del color de fondo del objeto.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CImageList::SetBkColor](#setbkcolor).

## <a name="cimagelistgetdragimage"></a><a name="getdragimage"></a>CImageList::GetDragImage

Obtiene la lista de imágenes temporales que se utiliza para arrastrar.

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>Parámetros

*lpPoint*<br/>
Dirección de una estructura [POINT](/previous-versions/dd162805\(v=vs.85\)) que recibe la posición de arrastre actual.

*lpPointHotSpot*<br/>
Dirección de `POINT` una estructura que recibe el desplazamiento de la imagen de arrastre en relación con la posición de arrastre.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, un puntero a la lista de imágenes temporales que se utiliza para arrastrar; de lo contrario, NULL.

## <a name="cimagelistgetimagecount"></a><a name="getimagecount"></a>CImageList::GetImageCount

Llame a esta función para recuperar el número de imágenes de una lista de imágenes.

```
int GetImageCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de imágenes.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CImageList::ExtractIcon](#extracticon).

## <a name="cimagelistgetimageinfo"></a><a name="getimageinfo"></a>CImageList::GetImageInfo

Llame a esta función para recuperar información sobre una imagen.

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>Parámetros

*nImage*<br/>
Indice de base cero de la imagen.

*pImageInfo*<br/>
Puntero a una estructura [IMAGEINFO](/windows/win32/api/commctrl/ns-commctrl-imageinfo) que recibe información sobre la imagen. La información de esta estructura se puede utilizar para manipular directamente los mapas de bits de la imagen.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

La `IMAGEINFO` estructura contiene información sobre una imagen en una lista de imágenes.

## <a name="cimagelistgetsafehandle"></a><a name="getsafehandle"></a>CImageList::GetSafeHandle

Llame a esta `m_hImageList` función para recuperar el miembro de datos.

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>Valor devuelto

Un identificador de la lista de imágenes adjuntas; de lo contrario NULL si no se adjunta ningún objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

## <a name="cimagelistm_himagelist"></a><a name="m_himagelist"></a>CImageList::m_hImageList

Identificador de la lista de imágenes adjunta a este objeto.

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>Observaciones

El `m_hImageList` miembro de datos es una variable pública de tipo HIMAGELIST.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

## <a name="cimagelistoperator-himagelist"></a><a name="operator_himagelist"></a>CImageList::operator HIMAGELIST

Utilice este operador para obtener `CImageList` el identificador adjunto del objeto.

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, un identificador `CImageList` de la lista de imágenes representada por el objeto; NULL.

### <a name="remarks"></a>Observaciones

Este operador es un operador de conversión, que admite el uso directo de un objeto HIMAGELIST.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

## <a name="cimagelistread"></a><a name="read"></a>CImageList::Read

Llame a esta función para leer una lista de imágenes de un archivo.

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>Parámetros

*pArchive*<br/>
Puntero a `CArchive` un objeto desde el que se va a leer la lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

## <a name="cimagelistremove"></a><a name="remove"></a>CImageList::Remove

Llame a esta función para eliminar una imagen de un objeto de lista de imágenes.

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>Parámetros

*nImage*<br/>
El índice de base cero de la imagen que se va a eliminar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Todos los elementos que siguen *a nImage* ahora se mueven hacia abajo una posición. Por ejemplo, si una lista de imágenes contiene dos elementos, eliminar el primer elemento hará que el elemento restante esté ahora en la primera posición. *nImagen*n.o 0 para el elemento en la primera posición.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

## <a name="cimagelistreplace"></a><a name="replace"></a>CImageList::Reemplazar

Llame a esta función para reemplazar una imagen de una lista de imágenes con una nueva imagen.

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
El índice de base cero de la imagen que se va a reemplazar.

*pbmImage*<br/>
Un puntero al mapa de bits que contiene la imagen.

*pbmMask*<br/>
Un puntero al mapa de bits que contiene la máscara. Si no se utiliza ninguna máscara con la lista de imágenes, se omite este parámetro.

*hIcon*<br/>
Identificador del icono que contiene el mapa de bits y la máscara de la nueva imagen.

### <a name="return-value"></a>Valor devuelto

La versión que devuelve BOOL devuelve distinto de cero si se realiza correctamente; de lo contrario 0.

La versión que devuelve **int** devuelve el índice de base cero de la imagen si se realiza correctamente; de lo contrario - 1.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro después de llamar a [SetImageCount](#setimagecount) para asignar las nuevas imágenes válidas a los números de índice de imagen de marcador de posición.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CImageList::SetImageCount](#setimagecount).

## <a name="cimagelistsetbkcolor"></a><a name="setbkcolor"></a>CImageList::SetBkColor

Llame a esta función para establecer el color de fondo de una lista de imágenes.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parámetros

*Cr*<br/>
Color de fondo para establecer. Puede ser CLR_NONE. En ese caso, las imágenes se dibujan de forma transparente utilizando la máscara.

### <a name="return-value"></a>Valor devuelto

El color de fondo anterior si se realiza correctamente; de lo contrario CLR_NONE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

## <a name="cimagelistsetdragcursorimage"></a><a name="setdragcursorimage"></a>CImageList::SetDragCursorImage

Crea una nueva imagen de arrastre combinando la imagen dada (normalmente una imagen de cursor del ratón) con la imagen de arrastre actual.

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parámetros

*nDrag*<br/>
Index de la nueva imagen que se va a combinar con la imagen de arrastre.

*ptHotSpot*<br/>
Posición del punto caliente dentro de la nueva imagen.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Dado que las funciones de arrastre utilizan la nueva imagen durante una operación de `CImageList::SetDragCursorImage`arrastre, debe utilizar la función [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor) de Windows para ocultar el cursor del mouse real después de llamar. De lo contrario, el sistema puede parecer tener dos cursores del ratón durante la operación de arrastre.

## <a name="cimagelistsetimagecount"></a><a name="setimagecount"></a>CImageList::SetImageCount

Llame a esta función miembro para `CImageList` restablecer el número de imágenes en un objeto.

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>Parámetros

*uNewCount*<br/>
Valor que especifica el nuevo número total de imágenes en la lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Si llama a esta función miembro para aumentar el número de imágenes en la lista de imágenes, a continuación, llame a [reemplazar](#replace) para cada imagen adicional para asignar los nuevos índices a imágenes válidas. Si no asigna los índices a imágenes válidas, las operaciones de dibujo que creen las nuevas imágenes serán impredecibles.

Si reduce el tamaño de una lista de imágenes mediante esta función, las imágenes truncadas se liberan.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

## <a name="cimagelistsetoverlayimage"></a><a name="setoverlayimage"></a>CImageList::SetOverlayImage

Llame a esta función para agregar el índice de base cero de una imagen a la lista de imágenes que se utilizarán como máscaras de superposición.

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>Parámetros

*nImage*<br/>
El índice de base cero de la imagen se utilizará como máscara de superposición.

*nOverlay*<br/>
El índice basado en uno de la máscara de superposición.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Se pueden añadir hasta cuatro índices a la lista.

Una máscara de superposición es una imagen dibujada de forma transparente sobre otra imagen. Dibuje una máscara de superposición sobre una imagen mediante la función miembro [CImageList::Draw](#draw) con el índice basado en uno de la máscara de superposición especificado mediante la macro INDEXTOOVERLAYMASK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

## <a name="cimagelistwrite"></a><a name="write"></a>CImageList::Write

Llame a esta función para escribir un objeto de lista de imágenes en un archivo.

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>Parámetros

*pArchive*<br/>
Puntero a `CArchive` un objeto en el que se va a almacenar la lista de imágenes.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>Consulte también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CListCtrl (clase)](../../mfc/reference/clistctrl-class.md)<br/>
[CTabCtrl (clase)](../../mfc/reference/ctabctrl-class.md)
