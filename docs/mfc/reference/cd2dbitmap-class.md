---
title: Clase CD2DBitmap
ms.date: 11/04/2016
f1_keywords:
- CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::Attach
- AFXRENDERTARGET/CD2DBitmap::CopyFromBitmap
- AFXRENDERTARGET/CD2DBitmap::CopyFromMemory
- AFXRENDERTARGET/CD2DBitmap::CopyFromRenderTarget
- AFXRENDERTARGET/CD2DBitmap::Create
- AFXRENDERTARGET/CD2DBitmap::Destroy
- AFXRENDERTARGET/CD2DBitmap::Detach
- AFXRENDERTARGET/CD2DBitmap::Get
- AFXRENDERTARGET/CD2DBitmap::GetDPI
- AFXRENDERTARGET/CD2DBitmap::GetPixelFormat
- AFXRENDERTARGET/CD2DBitmap::GetPixelSize
- AFXRENDERTARGET/CD2DBitmap::GetSize
- AFXRENDERTARGET/CD2DBitmap::IsValid
- AFXRENDERTARGET/CD2DBitmap::CommonInit
- AFXRENDERTARGET/CD2DBitmap::m_bAutoDestroyHBMP
- AFXRENDERTARGET/CD2DBitmap::m_hBmpSrc
- AFXRENDERTARGET/CD2DBitmap::m_lpszType
- AFXRENDERTARGET/CD2DBitmap::m_pBitmap
- AFXRENDERTARGET/CD2DBitmap::m_sizeDest
- AFXRENDERTARGET/CD2DBitmap::m_strPath
- AFXRENDERTARGET/CD2DBitmap::m_uiResID
helpviewer_keywords:
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], Attach
- CD2DBitmap [MFC], CopyFromBitmap
- CD2DBitmap [MFC], CopyFromMemory
- CD2DBitmap [MFC], CopyFromRenderTarget
- CD2DBitmap [MFC], Create
- CD2DBitmap [MFC], Destroy
- CD2DBitmap [MFC], Detach
- CD2DBitmap [MFC], Get
- CD2DBitmap [MFC], GetDPI
- CD2DBitmap [MFC], GetPixelFormat
- CD2DBitmap [MFC], GetPixelSize
- CD2DBitmap [MFC], GetSize
- CD2DBitmap [MFC], IsValid
- CD2DBitmap [MFC], CommonInit
- CD2DBitmap [MFC], m_bAutoDestroyHBMP
- CD2DBitmap [MFC], m_hBmpSrc
- CD2DBitmap [MFC], m_lpszType
- CD2DBitmap [MFC], m_pBitmap
- CD2DBitmap [MFC], m_sizeDest
- CD2DBitmap [MFC], m_strPath
- CD2DBitmap [MFC], m_uiResID
ms.assetid: 2b3686f1-812c-462b-b449-9f0cb6949bf6
ms.openlocfilehash: ce4fe49e8af85c4b63be31bf10e9f196f85c019f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369315"
---
# <a name="cd2dbitmap-class"></a>Clase CD2DBitmap

Un contenedor para ID2D1Bitmap.

## <a name="syntax"></a>Sintaxis

```
class CD2DBitmap : public CD2DResource;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Sobrecargado. Construye un CD2DBitmap objeto a partir de HBITMAP.|
|[CD2DBitmap::-CD2DBitmap](#_dtorcd2dbitmap)|Destructor. Se llama cuando se destruye un objeto de mapa de bits D2D.|

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Sobrecargado. Construye un CD2DBitmap objeto.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DBitmap::Attach](#attach)|Adjunta la interfaz de recursos existente al objeto|
|[CD2DBitmap::CopyFromBitmap](#copyfrombitmap)|Copia la región especificada del mapa de bits especificado en el mapa de bits actual|
|[CD2DBitmap::CopyFromMemory](#copyfrommemory)|Copia la región especificada de la memoria en el mapa de bits actual|
|[CD2DBitmap::CopyFromRenderTarget](#copyfromrendertarget)|Copia la región especificada del destino de representación especificado en el mapa de bits actual|
|[CD2DBitmap::Create](#create)|Crea un CD2DBitmap. (Reemplaza [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DBitmap::Destroy](#destroy)|Destruye un objeto CD2DBitmap. (Reemplaza [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DBitmap::Detach](#detach)|Separa la interfaz de recursos del objeto|
|[CD2DBitmap::Get](#get)|Devuelve la interfaz ID2D1Bitmap|
|[CD2DBitmap::GetDPI](#getdpi)|Devolver los puntos por pulgada (DPI) del mapa de bits|
|[CD2DBitmap::GetPixelFormat](#getpixelformat)|Recupera el formato de píxel y el modo alfa del mapa de bits|
|[CD2DBitmap::GetPixelSize](#getpixelsize)|Devuelve el tamaño, en unidades dependientes del dispositivo (píxeles), del mapa de bits|
|[CD2DBitmap::GetSize](#getsize)|Devuelve el tamaño, en píxeles independientes del dispositivo (DIP), del mapa de bits|
|[CD2DBitmap::IsValid](#isvalid)|Comprueba la validez de los recursos (reemplaza [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DBitmap::CommonInit](#commoninit)|Inicializa el objeto|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DBitmap::operator ID2D1Bitmap*](#operator_id2d1bitmap_star)|Devuelve la interfaz ID2D1Bitmap|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DBitmap::m_bAutoDestroyHBMP](#m_bautodestroyhbmp)|TRUESi se debe destruir m_hBmpSrc; de lo contrario FALSO.|
|[CD2DBitmap::m_hBmpSrc](#m_hbmpsrc)|Identificador de mapa de bits de origen.|
|[CD2DBitmap::m_lpszType](#m_lpsztype)|Tipo de recurso.|
|[CD2DBitmap::m_pBitmap](#m_pbitmap)|Almacena un puntero a un ID2D1Bitmap objeto.|
|[CD2DBitmap::m_sizeDest](#m_sizedest)|Tamaño de destino del mapa de bits.|
|[CD2DBitmap::m_strPath](#m_strpath)|Ruta del archivo de mapa de bots.|
|[CD2DBitmap::m_uiResID](#m_uiresid)|ID de recurso de mapa de bits.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DBitmap`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2dbitmapcd2dbitmap"></a><a name="_dtorcd2dbitmap"></a>CD2DBitmap::-CD2DBitmap

Destructor. Se llama cuando se destruye un objeto de mapa de bits D2D.

```
virtual ~CD2DBitmap();
```

## <a name="cd2dbitmapattach"></a><a name="attach"></a>CD2DBitmap::Attach

Asocia la interfaz de recursos existente al objeto.

```
void Attach(ID2D1Bitmap* pResource);
```

### <a name="parameters"></a>Parámetros

*pResource*<br/>
Interfaz de recursos existente. No puede ser NULL.

## <a name="cd2dbitmapcd2dbitmap"></a><a name="cd2dbitmap"></a>CD2DBitmap::CD2DBitmap

Construye un objeto CD2DBitmap a partir de un recurso.

```
CD2DBitmap(
    CRenderTarget* pParentTarget,
    UINT uiResID,
    LPCTSTR lpszType = NULL,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    LPCTSTR lpszPath,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    HBITMAP hbmpSrc,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

*pParentTarget*<br/>
Un puntero al destino de representación.

*uiResID*<br/>
El número de ID de recurso del recurso.

*lpszType*<br/>
Puntero a una cadena terminada en null que contiene el tipo de recurso.

*sizeDest*<br/>
Tamaño de destino del mapa de bits.

*bAutoDestroy*<br/>
Indica que el propietario destruirá el objeto (pParentTarget).

*lpszPath*<br/>
Puntero a una cadena terminada en null que contiene el nombre del archivo.

*hbmpSrc*<br/>
Controle el mapa de bits.

## <a name="cd2dbitmapcommoninit"></a><a name="commoninit"></a>CD2DBitmap::CommonInit

Inicializa el objeto.

```
void CommonInit();
```

## <a name="cd2dbitmapcopyfrombitmap"></a><a name="copyfrombitmap"></a>CD2DBitmap::CopyFromBitmap

Copia la región especificada del mapa de bits especificado en el mapa de bits actual.

```
HRESULT CopyFromBitmap(
    const CD2DBitmap* pBitmap,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>Parámetros

*pBitmap*<br/>
El mapa de bits desde el que se debe copiar.

*destPoint*<br/>
En el mapa de bits actual, se copia la esquina superior izquierda del área en la que se copia la región especificada por srcRect.

*srcRect*<br/>
El área de mapa de bits que se van a copiar.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

## <a name="cd2dbitmapcopyfrommemory"></a><a name="copyfrommemory"></a>CD2DBitmap::CopyFromMemory

Copia la región especificada de la memoria en el mapa de bits actual.

```
HRESULT CopyFromMemory(
    const void* srcData,
    UINT32 pitch,
    const CD2DRectU* destRect = NULL);
```

### <a name="parameters"></a>Parámetros

*srcData*<br/>
Los datos que se copiarán.

*alquitrán*<br/>
La zancada, o tono, del mapa de bits de origen almacenado en srcData. El paso es el recuento de bytes de una línea de exploración (una fila de píxeles en la memoria). La zancada se puede calcular a partir \* de la siguiente fórmula: bytes de ancho de píxel por píxel + relleno de memoria.

*destRect*<br/>
En el mapa de bits actual, se copia la esquina superior izquierda del área en la que se copia la región especificada por srcRect.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

## <a name="cd2dbitmapcopyfromrendertarget"></a><a name="copyfromrendertarget"></a>CD2DBitmap::CopyFromRenderTarget

Copia la región especificada del destino de representación especificado en el mapa de bits actual.

```
HRESULT CopyFromRenderTarget(
    const CRenderTarget* pRenderTarget,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>Parámetros

*pRenderTarget*<br/>
El destino de representación que contiene la región que se va a copiar.

*destPoint*<br/>
En el mapa de bits actual, se copia la esquina superior izquierda del área en la que se copia la región especificada por srcRect.

*srcRect*<br/>
El área de renderTarget que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

## <a name="cd2dbitmapcreate"></a><a name="create"></a>CD2DBitmap::Create

Crea un CD2DBitmap.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parámetros

*pRenderTarget*<br/>
Un puntero al destino de representación.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

## <a name="cd2dbitmapdestroy"></a><a name="destroy"></a>CD2DBitmap::Destroy

Destruye un objeto CD2DBitmap.

```
virtual void Destroy();
```

## <a name="cd2dbitmapdetach"></a><a name="detach"></a>CD2DBitmap::Detach

Separa la interfaz de recursos del objeto.

```
ID2D1Bitmap* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a interfaz de recursos separada.

## <a name="cd2dbitmapget"></a><a name="get"></a>CD2DBitmap::Get

Devuelve ID2D1Bitmap interfaz.

```
ID2D1Bitmap* Get();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1Bitmap o NULL si el objeto aún no se ha inicializado.

## <a name="cd2dbitmapgetdpi"></a><a name="getdpi"></a>CD2DBitmap::GetDPI

Devuelve los puntos por pulgada (DPI) del mapa de bits.

```
CD2DSizeF GetDPI() const;
```

### <a name="return-value"></a>Valor devuelto

El PPP horizontal y vertical del mapa de bits.

## <a name="cd2dbitmapgetpixelformat"></a><a name="getpixelformat"></a>CD2DBitmap::GetPixelFormat

Recupera el formato de píxel y el modo alfa del mapa de bits

```
D2D1_PIXEL_FORMAT GetPixelFormat() const;
```

### <a name="return-value"></a>Valor devuelto

El formato de píxel y el modo alfa del mapa de bits.

## <a name="cd2dbitmapgetpixelsize"></a><a name="getpixelsize"></a>CD2DBitmap::GetPixelSize

Devuelve el tamaño, en unidades dependientes del dispositivo (píxeles), del mapa de bits.

```
CD2DSizeU GetPixelSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño, en píxeles, del mapa de bits..

## <a name="cd2dbitmapgetsize"></a><a name="getsize"></a>CD2DBitmap::GetSize

Devuelve el tamaño, en píxeles independientes del dispositivo (DIP), del mapa de bits.

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño, en DIP, del mapa de bits.

## <a name="cd2dbitmapisvalid"></a><a name="isvalid"></a>CD2DBitmap::IsValid

Comprueba la validez de los recursos.

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el recurso es válido; de lo contrario FALSO.

## <a name="cd2dbitmapm_bautodestroyhbmp"></a><a name="m_bautodestroyhbmp"></a>CD2DBitmap::m_bAutoDestroyHBMP

TRUESi se debe destruir m_hBmpSrc; de lo contrario FALSO.

```
BOOL m_bAutoDestroyHBMP;
```

## <a name="cd2dbitmapm_hbmpsrc"></a><a name="m_hbmpsrc"></a>CD2DBitmap::m_hBmpSrc

Identificador de mapa de bits de origen.

```
HBITMAP m_hBmpSrc;
```

## <a name="cd2dbitmapm_lpsztype"></a><a name="m_lpsztype"></a>CD2DBitmap::m_lpszType

Tipo de recurso.

```
LPCTSTR m_lpszType;
```

## <a name="cd2dbitmapm_pbitmap"></a><a name="m_pbitmap"></a>CD2DBitmap::m_pBitmap

Almacena un puntero a un ID2D1Bitmap objeto.

```
ID2D1Bitmap* m_pBitmap;
```

## <a name="cd2dbitmapm_sizedest"></a><a name="m_sizedest"></a>CD2DBitmap::m_sizeDest

Tamaño de destino del mapa de bits.

```
CD2DSizeU m_sizeDest;
```

## <a name="cd2dbitmapm_strpath"></a><a name="m_strpath"></a>CD2DBitmap::m_strPath

Ruta del archivo de mapa de bots.

```
CString m_strPath;
```

## <a name="cd2dbitmapm_uiresid"></a><a name="m_uiresid"></a>CD2DBitmap::m_uiResID

ID de recurso de mapa de bits.

```
UINT m_uiResID;
```

## <a name="cd2dbitmapoperator-id2d1bitmap"></a><a name="operator_id2d1bitmap_star"></a>CD2DBitmap::operator ID2D1Bitmap*

Devuelve la interfaz ID2D1Bitmap

```
operator ID2D1Bitmap*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1Bitmap o NULL si el objeto aún no se ha inicializado.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
