---
title: Clase CD2DBitmapBrush
ms.date: 11/04/2016
f1_keywords:
- CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::Attach
- AFXRENDERTARGET/CD2DBitmapBrush::Create
- AFXRENDERTARGET/CD2DBitmapBrush::Destroy
- AFXRENDERTARGET/CD2DBitmapBrush::Detach
- AFXRENDERTARGET/CD2DBitmapBrush::Get
- AFXRENDERTARGET/CD2DBitmapBrush::GetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::GetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::SetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::SetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::CommonInit
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrushProperties
helpviewer_keywords:
- CD2DBitmapBrush [MFC], CD2DBitmapBrush
- CD2DBitmapBrush [MFC], Attach
- CD2DBitmapBrush [MFC], Create
- CD2DBitmapBrush [MFC], Destroy
- CD2DBitmapBrush [MFC], Detach
- CD2DBitmapBrush [MFC], Get
- CD2DBitmapBrush [MFC], GetBitmap
- CD2DBitmapBrush [MFC], GetExtendModeX
- CD2DBitmapBrush [MFC], GetExtendModeY
- CD2DBitmapBrush [MFC], GetInterpolationMode
- CD2DBitmapBrush [MFC], SetBitmap
- CD2DBitmapBrush [MFC], SetExtendModeX
- CD2DBitmapBrush [MFC], SetExtendModeY
- CD2DBitmapBrush [MFC], SetInterpolationMode
- CD2DBitmapBrush [MFC], CommonInit
- CD2DBitmapBrush [MFC], m_pBitmap
- CD2DBitmapBrush [MFC], m_pBitmapBrush
- CD2DBitmapBrush [MFC], m_pBitmapBrushProperties
ms.assetid: 46ebbe34-66e0-44c8-af1d-d129e851de5e
ms.openlocfilehash: 8d0804c094204bc0e8ab420e20c8b6a6a35dc70a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754292"
---
# <a name="cd2dbitmapbrush-class"></a>Clase CD2DBitmapBrush

Un contenedor para ID2D1BitmapBrush.

## <a name="syntax"></a>Sintaxis

```
class CD2DBitmapBrush : public CD2DBrush;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DBitmapBrush::CD2DBitmapBrush](#cd2dbitmapbrush)|Sobrecargado. Construye un CD2DBitmapBrush objeto a partir de archivo.|
|[CD2DBitmapBrush::-CD2DBitmapBrush](#dtor)|Destructor. Se llama cuando se destruye un objeto de pincel de mapa de bits D2D.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DBitmapBrush::Attach](#attach)|Adjunta la interfaz de recursos existente al objeto|
|[CD2DBitmapBrush::Create](#create)|Crea un CD2DBitmapBrush. (Reemplaza [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DBitmapBrush::Destroy](#destroy)|Destruye un CD2DBitmapBrush objeto. (Reemplaza [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[CD2DBitmapBrush::Detach](#detach)|Separa la interfaz de recursos del objeto|
|[CD2DBitmapBrush::Get](#get)|Devuelve ID2D1BitmapBrush interfaz|
|[CD2DBitmapBrush::GetBitmap](#getbitmap)|Obtiene el origen de mapa de bits que este pincel utiliza para pintar|
|[CD2DBitmapBrush::GetExtendModeX](#getextendmodex)|Obtiene el método por el que el pincel enmosaico horizontalmente aquellas áreas que se extienden más allá de su mapa de bits|
|[CD2DBitmapBrush::GetExtendModeY](#getextendmodey)|Obtiene el método por el que el pincel enmosaico verticalmente aquellas áreas que se extienden más allá de su mapa de bits|
|[CD2DBitmapBrush::GetInterpolationMode](#getinterpolationmode)|Obtiene el método de interpolación utilizado cuando se escala o gira el mapa de bits del pincel|
|[CD2DBitmapBrush::SetBitmap](#setbitmap)|Especifica el origen de mapa de bits que este pincel utiliza para pintar|
|[CD2DBitmapBrush::SetExtendModeX](#setextendmodex)|Especifica cómo el pincel teselas horizontalmente las áreas que se extienden más allá de su mapa de bits|
|[CD2DBitmapBrush::SetExtendModeY](#setextendmodey)|Especifica cómo el pincel teselas verticalmente las áreas que se extienden más allá de su mapa de bits|
|[CD2DBitmapBrush::SetInterpolationMode](#setinterpolationmode)|Especifica el modo de interpolación utilizado cuando se escala o gira el mapa de bits del pincel|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DBitmapBrush::CommonInit](#commoninit)|Inicializa el objeto|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DBitmapBrush::operator ID2D1BitmapBrush*](#operator_id2d1bitmapbrush_star)|Devuelve ID2D1BitmapBrush interfaz|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DBitmapBrush::m_pBitmap](#m_pbitmap)|Almacena un puntero a un CD2DBitmap objeto.|
|[CD2DBitmapBrush::m_pBitmapBrush](#m_pbitmapbrush)|Almacena un puntero a un ID2D1BitmapBrush objeto.|
|[CD2DBitmapBrush::m_pBitmapBrushProperties](#m_pbitmapbrushproperties)|Propiedades del pincel de mapa de bits.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

`CD2DBitmapBrush`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2dbitmapbrushcd2dbitmapbrush"></a><a name="dtor"></a>CD2DBitmapBrush::-CD2DBitmapBrush

Destructor. Se llama cuando se destruye un objeto de pincel de mapa de bits D2D.

```
virtual ~CD2DBitmapBrush();
```

## <a name="cd2dbitmapbrushattach"></a><a name="attach"></a>CD2DBitmapBrush::Attach

Adjunta la interfaz de recursos existente al objeto

```cpp
void Attach(ID2D1BitmapBrush* pResource);
```

### <a name="parameters"></a>Parámetros

*pResource*<br/>
Interfaz de recursos existente. No puede ser NULL

## <a name="cd2dbitmapbrushcd2dbitmapbrush"></a><a name="cd2dbitmapbrush"></a>CD2DBitmapBrush::CD2DBitmapBrush

Construye un CD2DBitmapBrush objeto.

```
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    UINT uiResID,
    LPCTSTR lpszType = NULL,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    LPCTSTR lpszImagePath,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

*pParentTarget*<br/>
Un puntero al destino de representación.

*pBitmapBrushProperties*<br/>
Un puntero a los modos de extensión y el modo de interpolación de un pincel de mapa de bits.

*pBrushProperties*<br/>
Un puntero a la opacidad y transformación de un pincel.

*bAutoDestroy*<br/>
Indica que el propietario destruirá el objeto (pParentTarget).

*uiResID*<br/>
El número de ID de recurso del recurso.

*lpszType*<br/>
Puntero a una cadena terminada en null que contiene el tipo de recurso.

*sizeDest*<br/>
Tamaño de destino del mapa de bits.

*lpszImagePath*<br/>
Puntero a una cadena terminada en null que contiene el nombre del archivo.

## <a name="cd2dbitmapbrushcommoninit"></a><a name="commoninit"></a>CD2DBitmapBrush::CommonInit

Inicializa el objeto

```cpp
void CommonInit(D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties);
```

### <a name="parameters"></a>Parámetros

*pBitmapBrushProperties*<br/>
Un puntero a las propiedades del pincel de mapa de bits.

## <a name="cd2dbitmapbrushcreate"></a><a name="create"></a>CD2DBitmapBrush::Create

Crea un CD2DBitmapBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parámetros

*pRenderTarget*<br/>
Un puntero al destino de representación.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

## <a name="cd2dbitmapbrushdestroy"></a><a name="destroy"></a>CD2DBitmapBrush::Destroy

Destruye un CD2DBitmapBrush objeto.

```
virtual void Destroy();
```

## <a name="cd2dbitmapbrushdetach"></a><a name="detach"></a>CD2DBitmapBrush::Detach

Separa la interfaz de recursos del objeto

```
ID2D1BitmapBrush* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a interfaz de recursos separada.

## <a name="cd2dbitmapbrushget"></a><a name="get"></a>CD2DBitmapBrush::Get

Devuelve ID2D1BitmapBrush interfaz

```
ID2D1BitmapBrush* Get();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1BitmapBrush o NULL si el objeto aún no se ha inicializado.

## <a name="cd2dbitmapbrushgetbitmap"></a><a name="getbitmap"></a>CD2DBitmapBrush::GetBitmap

Obtiene el origen de mapa de bits que este pincel utiliza para pintar

```
CD2DBitmap* GetBitmap();
```

### <a name="return-value"></a>Valor devuelto

Puntero a un CD2DBitmap objeto o NULL si el objeto no se ha inicializado todavía.

## <a name="cd2dbitmapbrushgetextendmodex"></a><a name="getextendmodex"></a>CD2DBitmapBrush::GetExtendModeX

Obtiene el método por el que el pincel enmosaico horizontalmente aquellas áreas que se extienden más allá de su mapa de bits

```
D2D1_EXTEND_MODE GetExtendModeX() const;
```

### <a name="return-value"></a>Valor devuelto

Valor que especifica cómo el pincel teselas horizontalmente las áreas que se extienden más allá de su mapa de bits

## <a name="cd2dbitmapbrushgetextendmodey"></a><a name="getextendmodey"></a>CD2DBitmapBrush::GetExtendModeY

Obtiene el método por el que el pincel enmosaico verticalmente aquellas áreas que se extienden más allá de su mapa de bits

```
D2D1_EXTEND_MODE GetExtendModeY() const;
```

### <a name="return-value"></a>Valor devuelto

Valor que especifica cómo el pincel teselas verticalmente aquellas áreas que se extienden más allá de su mapa de bits

## <a name="cd2dbitmapbrushgetinterpolationmode"></a><a name="getinterpolationmode"></a>CD2DBitmapBrush::GetInterpolationMode

Obtiene el método de interpolación utilizado cuando se escala o gira el mapa de bits del pincel

```
D2D1_BITMAP_INTERPOLATION_MODE GetInterpolationMode() const;
```

### <a name="return-value"></a>Valor devuelto

El método de interpolación utilizado cuando se escala o gira el mapa de bits del pincel

## <a name="cd2dbitmapbrushm_pbitmap"></a><a name="m_pbitmap"></a>CD2DBitmapBrush::m_pBitmap

Almacena un puntero a un CD2DBitmap objeto.

```
CD2DBitmap* m_pBitmap;
```

## <a name="cd2dbitmapbrushm_pbitmapbrush"></a><a name="m_pbitmapbrush"></a>CD2DBitmapBrush::m_pBitmapBrush

Almacena un puntero a un ID2D1BitmapBrush objeto.

```
ID2D1BitmapBrush* m_pBitmapBrush;
```

## <a name="cd2dbitmapbrushm_pbitmapbrushproperties"></a><a name="m_pbitmapbrushproperties"></a>CD2DBitmapBrush::m_pBitmapBrushProperties

Propiedades del pincel de mapa de bits.

```
D2D1_BITMAP_BRUSH_PROPERTIES* m_pBitmapBrushProperties;
```

## <a name="cd2dbitmapbrushoperator-id2d1bitmapbrush"></a><a name="operator_id2d1bitmapbrush_star"></a>CD2DBitmapBrush::operator ID2D1BitmapBrush*

Devuelve ID2D1BitmapBrush interfaz

```
operator ID2D1BitmapBrush*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1BitmapBrush o NULL si el objeto aún no se ha inicializado.

## <a name="cd2dbitmapbrushsetbitmap"></a><a name="setbitmap"></a>CD2DBitmapBrush::SetBitmap

Especifica el origen de mapa de bits que este pincel utiliza para pintar

```cpp
void SetBitmap(CD2DBitmap* pBitmap);
```

### <a name="parameters"></a>Parámetros

*pBitmap*<br/>
El origen de mapa de bits utilizado por el pincel

## <a name="cd2dbitmapbrushsetextendmodex"></a><a name="setextendmodex"></a>CD2DBitmapBrush::SetExtendModeX

Especifica cómo el pincel teselas horizontalmente las áreas que se extienden más allá de su mapa de bits

```cpp
void SetExtendModeX(D2D1_EXTEND_MODE extendModeX);
```

### <a name="parameters"></a>Parámetros

*extendModeX*<br/>
Valor que especifica cómo el pincel teselas horizontalmente las áreas que se extienden más allá de su mapa de bits

## <a name="cd2dbitmapbrushsetextendmodey"></a><a name="setextendmodey"></a>CD2DBitmapBrush::SetExtendModeY

Especifica cómo el pincel teselas verticalmente las áreas que se extienden más allá de su mapa de bits

```cpp
void SetExtendModeY(D2D1_EXTEND_MODE extendModeY);
```

### <a name="parameters"></a>Parámetros

*extendModeY*<br/>
Valor que especifica cómo el pincel teselas verticalmente aquellas áreas que se extienden más allá de su mapa de bits

## <a name="cd2dbitmapbrushsetinterpolationmode"></a><a name="setinterpolationmode"></a>CD2DBitmapBrush::SetInterpolationMode

Especifica el modo de interpolación utilizado cuando se escala o gira el mapa de bits del pincel

```cpp
void SetInterpolationMode(D2D1_BITMAP_INTERPOLATION_MODE interpolationMode);
```

### <a name="parameters"></a>Parámetros

*interpolaciónMode*<br/>
El modo de interpolación utilizado cuando se escala o gira el mapa de bits del pincel

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
