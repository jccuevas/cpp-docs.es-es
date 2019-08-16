---
title: Clase CD2DRadialGradientBrush
ms.date: 11/04/2016
f1_keywords:
- CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::Attach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Create
- AFXRENDERTARGET/CD2DRadialGradientBrush::Destroy
- AFXRENDERTARGET/CD2DRadialGradientBrush::Detach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Get
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_pRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_RadialGradientBrushProperties
helpviewer_keywords:
- CD2DRadialGradientBrush [MFC], CD2DRadialGradientBrush
- CD2DRadialGradientBrush [MFC], Attach
- CD2DRadialGradientBrush [MFC], Create
- CD2DRadialGradientBrush [MFC], Destroy
- CD2DRadialGradientBrush [MFC], Detach
- CD2DRadialGradientBrush [MFC], Get
- CD2DRadialGradientBrush [MFC], GetCenter
- CD2DRadialGradientBrush [MFC], GetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], GetRadiusX
- CD2DRadialGradientBrush [MFC], GetRadiusY
- CD2DRadialGradientBrush [MFC], SetCenter
- CD2DRadialGradientBrush [MFC], SetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], SetRadiusX
- CD2DRadialGradientBrush [MFC], SetRadiusY
- CD2DRadialGradientBrush [MFC], m_pRadialGradientBrush
- CD2DRadialGradientBrush [MFC], m_RadialGradientBrushProperties
ms.assetid: 6c76d84a-d831-4ee2-96f1-82c1f5b0d6a9
ms.openlocfilehash: 22029ebcf8cf519571e81e11c84de146c9d54b26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396332"
---
# <a name="cd2dradialgradientbrush-class"></a>Clase CD2DRadialGradientBrush

Un contenedor para ID2D1RadialGradientBrush.

## <a name="syntax"></a>Sintaxis

```
class CD2DRadialGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DRadialGradientBrush::CD2DRadialGradientBrush](#cd2dradialgradientbrush)|Construye un objeto CD2DLinearGradientBrush.|
|[CD2DRadialGradientBrush::~CD2DRadialGradientBrush](#_dtorcd2dradialgradientbrush)|Destructor. Se llama cuando se destruye un objeto de pincel de degradado radial D2D.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DRadialGradientBrush::Attach](#attach)|Adjunta existente de la interfaz de recurso para el objeto|
|[CD2DRadialGradientBrush::Create](#create)|Crea un CD2DRadialGradientBrush. (Invalida [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DRadialGradientBrush::Destroy](#destroy)|Destruye un objeto CD2DRadialGradientBrush. (Invalida [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[CD2DRadialGradientBrush::Detach](#detach)|Separa la interfaz de recursos desde el objeto|
|[CD2DRadialGradientBrush::Get](#get)|Interfaz de ID2D1RadialGradientBrush devuelve|
|[CD2DRadialGradientBrush::GetCenter](#getcenter)|Recupera el centro de la elipse de degradado|
|[CD2DRadialGradientBrush::GetGradientOriginOffset](#getgradientoriginoffset)|Recupera el desplazamiento del origen de degradado en relación con el centro del degradado de la elipse|
|[CD2DRadialGradientBrush::GetRadiusX](#getradiusx)|Recupera el radio x de la elipse de degradado|
|[CD2DRadialGradientBrush::GetRadiusY](#getradiusy)|Recupera el radio y de la elipse de degradado|
|[CD2DRadialGradientBrush::SetCenter](#setcenter)|Especifica el centro de la elipse degradado en el espacio de coordenadas del pincel|
|[CD2DRadialGradientBrush::SetGradientOriginOffset](#setgradientoriginoffset)|Especifica el desplazamiento del origen de degradado en relación con el centro del degradado de la elipse|
|[CD2DRadialGradientBrush::SetRadiusX](#setradiusx)|Especifica el radio x de la elipse degradado, en el espacio de coordenadas del pincel|
|[CD2DRadialGradientBrush::SetRadiusY](#setradiusy)|Especifica el radio y de la elipse degradado, en el espacio de coordenadas del pincel|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush*](#operator_id2d1radialgradientbrush_star)|Interfaz de ID2D1RadialGradientBrush devuelve|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Name|Descripción|
|----------|-----------------|
|[CD2DRadialGradientBrush::m_pRadialGradientBrush](#m_pradialgradientbrush)|Un puntero a un ID2D1RadialGradientBrush.|
|[CD2DRadialGradientBrush::m_RadialGradientBrushProperties](#m_radialgradientbrushproperties)|El centro, el desplazamiento de origen de degradado y radio x y radio "y" del pincel de degradado del.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DRadialGradientBrush`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

##  <a name="_dtorcd2dradialgradientbrush"></a>  CD2DRadialGradientBrush::~CD2DRadialGradientBrush

Destructor. Se llama cuando se destruye un objeto de pincel de degradado radial D2D.

```
virtual ~CD2DRadialGradientBrush();
```

##  <a name="attach"></a>  CD2DRadialGradientBrush::Attach

Adjunta existente de la interfaz de recurso para el objeto

```
void Attach(ID2D1RadialGradientBrush* pResource);
```

### <a name="parameters"></a>Parámetros

*pResource*<br/>
Interfaz de recursos existente. No puede ser NULL

##  <a name="cd2dradialgradientbrush"></a>  CD2DRadialGradientBrush::CD2DRadialGradientBrush

Construye un objeto CD2DLinearGradientBrush.

```
CD2DRadialGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES RadialGradientBrushProperties,
    D2D1_GAMMA colorInterpolationGamma = D2D1_GAMMA_2_2,
    D2D1_EXTEND_MODE extendMode = D2D1_EXTEND_MODE_CLAMP,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

*pParentTarget*<br/>
Un puntero para el destino de representación.

*gradientStops*<br/>
Un puntero a una matriz de estructuras D2D1_GRADIENT_STOP.

*gradientStopsCount*<br/>
Un valor mayor o igual a 1 que especifica el número de delimitadores de degradado de la matriz gradientStops.

*RadialGradientBrushProperties*<br/>
El centro, el desplazamiento de origen de degradado y radio x y radio "y" del pincel de degradado del.

*colorInterpolationGamma*<br/>
El espacio en el color que se realiza una interpolación entre los delimitadores de degradado.

*extendMode*<br/>
El comportamiento del degradado fuera del intervalo [0,1] normalizado.

*pBrushProperties*<br/>
Un puntero a la opacidad y la transformación de un pincel.

*bAutoDestroy*<br/>
Indica que se va a destruir el objeto propietario (pParentTarget).

##  <a name="create"></a>  CD2DRadialGradientBrush::Create

Crea un CD2DRadialGradientBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parámetros

*pRenderTarget*<br/>
Un puntero para el destino de representación.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. En caso contrario, devuelve un código de error HRESULT.

##  <a name="destroy"></a>  CD2DRadialGradientBrush::Destroy

Destruye un objeto CD2DRadialGradientBrush.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DRadialGradientBrush::Detach

Separa la interfaz de recursos desde el objeto

```
ID2D1RadialGradientBrush* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a interfaz separada del recurso.

##  <a name="get"></a>  CD2DRadialGradientBrush::Get

Interfaz de ID2D1RadialGradientBrush devuelve

```
ID2D1RadialGradientBrush* Get();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1RadialGradientBrush o NULL si el objeto no se ha inicializado todavía.

##  <a name="getcenter"></a>  CD2DRadialGradientBrush::GetCenter

Recupera el centro de la elipse de degradado

```
CD2DPointF GetCenter() const;
```

### <a name="return-value"></a>Valor devuelto

El centro de la elipse de degradado. Este valor se expresa en el espacio de coordenadas del pincel

##  <a name="getgradientoriginoffset"></a>  CD2DRadialGradientBrush::GetGradientOriginOffset

Recupera el desplazamiento del origen de degradado en relación con el centro del degradado de la elipse

```
CD2DPointF GetGradientOriginOffset() const;
```

### <a name="return-value"></a>Valor devuelto

El desplazamiento del degradado origen desde el centro de la elipse de degradado. Este valor se expresa en el espacio de coordenadas del pincel

##  <a name="getradiusx"></a>  CD2DRadialGradientBrush::GetRadiusX

Recupera el radio x de la elipse de degradado

```
FLOAT GetRadiusX() const;
```

### <a name="return-value"></a>Valor devuelto

El radio x de la elipse de degradado. Este valor se expresa en el espacio de coordenadas del pincel

##  <a name="getradiusy"></a>  CD2DRadialGradientBrush::GetRadiusY

Recupera el radio y de la elipse de degradado

```
FLOAT GetRadiusY() const;
```

### <a name="return-value"></a>Valor devuelto

El radio y de la elipse de degradado. Este valor se expresa en el espacio de coordenadas del pincel

##  <a name="m_pradialgradientbrush"></a>  CD2DRadialGradientBrush::m_pRadialGradientBrush

Un puntero a un ID2D1RadialGradientBrush.

```
ID2D1RadialGradientBrush* m_pRadialGradientBrush;
```

##  <a name="m_radialgradientbrushproperties"></a>  CD2DRadialGradientBrush::m_RadialGradientBrushProperties

El centro, el desplazamiento de origen de degradado y radio x y radio "y" del pincel de degradado del.

```
D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES m_RadialGradientBrushProperties;
```

##  <a name="operator_id2d1radialgradientbrush_star"></a>  CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush *

Interfaz de ID2D1RadialGradientBrush devuelve

```
operator ID2D1RadialGradientBrush*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1RadialGradientBrush o NULL si el objeto no se ha inicializado todavía.

##  <a name="setcenter"></a>  CD2DRadialGradientBrush::SetCenter

Especifica el centro de la elipse degradado en el espacio de coordenadas del pincel

```
void SetCenter(CD2DPointF point);
```

### <a name="parameters"></a>Parámetros

*point*<br/>
El centro de la elipse degradado, en el espacio de coordenadas del pincel

##  <a name="setgradientoriginoffset"></a>  CD2DRadialGradientBrush::SetGradientOriginOffset

Especifica el desplazamiento del origen de degradado en relación con el centro del degradado de la elipse

```
void SetGradientOriginOffset(CD2DPointF gradientOriginOffset);
```

### <a name="parameters"></a>Parámetros

*gradientOriginOffset*<br/>
El desplazamiento del degradado origen desde el centro de la elipse de degradado

##  <a name="setradiusx"></a>  CD2DRadialGradientBrush::SetRadiusX

Especifica el radio x de la elipse degradado, en el espacio de coordenadas del pincel

```
void SetRadiusX(FLOAT radiusX);
```

### <a name="parameters"></a>Parámetros

*radiusX*<br/>
El radio x de la elipse de degradado. Este valor está en el espacio de coordenadas del pincel

##  <a name="setradiusy"></a>  CD2DRadialGradientBrush::SetRadiusY

Especifica el radio y de la elipse degradado, en el espacio de coordenadas del pincel

```
void SetRadiusY(FLOAT radiusY);
```

### <a name="parameters"></a>Parámetros

*radiusY*<br/>
El radio y de la elipse de degradado. Este valor está en el espacio de coordenadas del pincel

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
