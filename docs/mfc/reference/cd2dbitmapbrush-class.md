---
title: Clase CD2DBitmapBrush | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b40f7e3d4a37dbc73494444fbfcc398621b7ec4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080018"
---
# <a name="cd2dbitmapbrush-class"></a>Clase CD2DBitmapBrush

Un contenedor para ID2D1BitmapBrush.

## <a name="syntax"></a>Sintaxis

```
class CD2DBitmapBrush : public CD2DBrush;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DBitmapBrush::CD2DBitmapBrush](#cd2dbitmapbrush)|Sobrecargado. Construye un objeto CD2DBitmapBrush del archivo.|
|[CD2DBitmapBrush:: ~ CD2DBitmapBrush](#dtor)|Destructor. Se llama cuando se destruye un objeto brush de mapa de bits de D2D.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DBitmapBrush::Attach](#attach)|Adjunta existente de la interfaz de recurso para el objeto|
|[CD2DBitmapBrush::Create](#create)|Crea un CD2DBitmapBrush. (Invalida [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DBitmapBrush::Destroy](#destroy)|Destruye un objeto CD2DBitmapBrush. (Invalida [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[CD2DBitmapBrush::Detach](#detach)|Separa la interfaz de recursos desde el objeto|
|[CD2DBitmapBrush::Get](#get)|Interfaz de ID2D1BitmapBrush devuelve|
|[CD2DBitmapBrush::GetBitmap](#getbitmap)|Obtiene el origen del mapa de bits que usa este pincel para pintar|
|[CD2DBitmapBrush::GetExtendModeX](#getextendmodex)|Obtiene el método por el que el pincel en mosaico horizontalmente las áreas que se extienden más allá de su mapa de bits|
|[CD2DBitmapBrush::GetExtendModeY](#getextendmodey)|Obtiene el método por el que el pincel iconos verticalmente las áreas que se extienden más allá de su mapa de bits|
|[CD2DBitmapBrush::GetInterpolationMode](#getinterpolationmode)|Obtiene el método de interpolación que se utiliza cuando el mapa de bits del pincel se escala o girada|
|[CD2DBitmapBrush::SetBitmap](#setbitmap)|Especifica el origen del mapa de bits que usa este pincel para pintar|
|[CD2DBitmapBrush::SetExtendModeX](#setextendmodex)|Especifica cómo el pincel de mosaico horizontalmente esas áreas que se extienden más allá de su mapa de bits|
|[CD2DBitmapBrush::SetExtendModeY](#setextendmodey)|Especifica cómo el pincel iconos verticalmente las áreas que se extienden más allá de su mapa de bits|
|[CD2DBitmapBrush::SetInterpolationMode](#setinterpolationmode)|Especifica el modo de interpolación usado cuando el mapa de bits del pincel se escala o girada|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CD2DBitmapBrush::CommonInit](#commoninit)|Inicializa el objeto|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DBitmapBrush::operator ID2D1BitmapBrush *](#operator_id2d1bitmapbrush_star)|Interfaz de ID2D1BitmapBrush devuelve|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|nombre|Descripción|
|----------|-----------------|
|[CD2DBitmapBrush::m_pBitmap](#m_pbitmap)|Almacena un puntero a un objeto CD2DBitmap.|
|[CD2DBitmapBrush::m_pBitmapBrush](#m_pbitmapbrush)|Almacena un puntero a un objeto ID2D1BitmapBrush.|
|[CD2DBitmapBrush::m_pBitmapBrushProperties](#m_pbitmapbrushproperties)|Las propiedades del pincel de mapa de bits.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

`CD2DBitmapBrush`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

##  <a name="dtor"></a>  CD2DBitmapBrush:: ~ CD2DBitmapBrush

Destructor. Se llama cuando se destruye un objeto brush de mapa de bits de D2D.

```
virtual ~CD2DBitmapBrush();
```

##  <a name="attach"></a>  CD2DBitmapBrush::Attach

Adjunta existente de la interfaz de recurso para el objeto

```
void Attach(ID2D1BitmapBrush* pResource);
```

### <a name="parameters"></a>Parámetros

*pResource*<br/>
Interfaz de recursos existente. No puede ser NULL

##  <a name="cd2dbitmapbrush"></a>  CD2DBitmapBrush::CD2DBitmapBrush

Construye un objeto CD2DBitmapBrush.

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
Un puntero para el destino de representación.

*pBitmapBrushProperties*<br/>
Un puntero a los modos de extender y el modo de interpolación de un pincel de mapa de bits.

*pBrushProperties*<br/>
Un puntero a la opacidad y la transformación de un pincel.

*bAutoDestroy*<br/>
Indica que se va a destruir el objeto propietario (pParentTarget).

*uiResID*<br/>
El número de Id. de recurso del recurso.

*lpszType*<br/>
Puntero a una cadena terminada en null que contiene el tipo de recurso.

*sizeDest*<br/>
Tamaño de destino del mapa de bits.

*lpszImagePath*<br/>
Puntero a una cadena terminada en null que contiene el nombre del archivo.

##  <a name="commoninit"></a>  CD2DBitmapBrush::CommonInit

Inicializa el objeto

```
void CommonInit(D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties);
```

### <a name="parameters"></a>Parámetros

*pBitmapBrushProperties*<br/>
Un puntero a las propiedades de pincel de mapa de bits.

##  <a name="create"></a>  CD2DBitmapBrush::Create

Crea un CD2DBitmapBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parámetros

*pRenderTarget*<br/>
Un puntero para el destino de representación.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. En caso contrario, devuelve un código de error HRESULT.

##  <a name="destroy"></a>  CD2DBitmapBrush::Destroy

Destruye un objeto CD2DBitmapBrush.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DBitmapBrush::Detach

Separa la interfaz de recursos desde el objeto

```
ID2D1BitmapBrush* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a interfaz separada del recurso.

##  <a name="get"></a>  CD2DBitmapBrush::Get

Interfaz de ID2D1BitmapBrush devuelve

```
ID2D1BitmapBrush* Get();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1BitmapBrush o NULL si el objeto no se ha inicializado todavía.

##  <a name="getbitmap"></a>  CD2DBitmapBrush::GetBitmap

Obtiene el origen del mapa de bits que usa este pincel para pintar

```
CD2DBitmap* GetBitmap();
```

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto CD2DBitmap o NULL si el objeto no se ha inicializado todavía.

##  <a name="getextendmodex"></a>  CD2DBitmapBrush::GetExtendModeX

Obtiene el método por el que el pincel en mosaico horizontalmente las áreas que se extienden más allá de su mapa de bits

```
D2D1_EXTEND_MODE GetExtendModeX() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor que especifica cómo el pincel de mosaico horizontalmente esas áreas que se extienden más allá de su mapa de bits

##  <a name="getextendmodey"></a>  CD2DBitmapBrush::GetExtendModeY

Obtiene el método por el que el pincel iconos verticalmente las áreas que se extienden más allá de su mapa de bits

```
D2D1_EXTEND_MODE GetExtendModeY() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor que especifica cómo el pincel iconos verticalmente las áreas que se extienden más allá de su mapa de bits

##  <a name="getinterpolationmode"></a>  CD2DBitmapBrush::GetInterpolationMode

Obtiene el método de interpolación que se utiliza cuando el mapa de bits del pincel se escala o girada

```
D2D1_BITMAP_INTERPOLATION_MODE GetInterpolationMode() const;
```

### <a name="return-value"></a>Valor devuelto

El método de interpolación que se utiliza cuando el mapa de bits del pincel se escala o girada

##  <a name="m_pbitmap"></a>  CD2DBitmapBrush::m_pBitmap

Almacena un puntero a un objeto CD2DBitmap.

```
CD2DBitmap* m_pBitmap;
```

##  <a name="m_pbitmapbrush"></a>  CD2DBitmapBrush::m_pBitmapBrush

Almacena un puntero a un objeto ID2D1BitmapBrush.

```
ID2D1BitmapBrush* m_pBitmapBrush;
```

##  <a name="m_pbitmapbrushproperties"></a>  CD2DBitmapBrush::m_pBitmapBrushProperties

Las propiedades del pincel de mapa de bits.

```
D2D1_BITMAP_BRUSH_PROPERTIES* m_pBitmapBrushProperties;
```

##  <a name="operator_id2d1bitmapbrush_star"></a>  CD2DBitmapBrush::operator ID2D1BitmapBrush *

Interfaz de ID2D1BitmapBrush devuelve

```
operator ID2D1BitmapBrush*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1BitmapBrush o NULL si el objeto no se ha inicializado todavía.

##  <a name="setbitmap"></a>  CD2DBitmapBrush::SetBitmap

Especifica el origen del mapa de bits que usa este pincel para pintar

```
void SetBitmap(CD2DBitmap* pBitmap);
```

### <a name="parameters"></a>Parámetros

*pBitmap*<br/>
El origen de mapa de bits usado por el pincel

##  <a name="setextendmodex"></a>  CD2DBitmapBrush::SetExtendModeX

Especifica cómo el pincel de mosaico horizontalmente esas áreas que se extienden más allá de su mapa de bits

```
void SetExtendModeX(D2D1_EXTEND_MODE extendModeX);
```

### <a name="parameters"></a>Parámetros

*extendModeX*<br/>
Un valor que especifica cómo el pincel de mosaico horizontalmente esas áreas que se extienden más allá de su mapa de bits

##  <a name="setextendmodey"></a>  CD2DBitmapBrush::SetExtendModeY

Especifica cómo el pincel iconos verticalmente las áreas que se extienden más allá de su mapa de bits

```
void SetExtendModeY(D2D1_EXTEND_MODE extendModeY);
```

### <a name="parameters"></a>Parámetros

*extendModeY*<br/>
Un valor que especifica cómo el pincel iconos verticalmente las áreas que se extienden más allá de su mapa de bits

##  <a name="setinterpolationmode"></a>  CD2DBitmapBrush::SetInterpolationMode

Especifica el modo de interpolación usado cuando el mapa de bits del pincel se escala o girada

```
void SetInterpolationMode(D2D1_BITMAP_INTERPOLATION_MODE interpolationMode);
```

### <a name="parameters"></a>Parámetros

*interpolationMode*<br/>
El modo de interpolación que se utiliza cuando el mapa de bits del pincel se escala o girada

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
