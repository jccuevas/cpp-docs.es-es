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
ms.openlocfilehash: 450314fdbf8441b0cc345430518d083573659add
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750304"
---
# <a name="cd2dradialgradientbrush-class"></a>Clase CD2DRadialGradientBrush

Un contenedor para ID2D1RadialGradientBrush.

## <a name="syntax"></a>Sintaxis

```
class CD2DRadialGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DRadialGradientBrush::CD2DRadialGradientBrush](#cd2dradialgradientbrush)|Construye un CD2DLinearGradientBrush objeto.|
|[CD2DRadialGradientBrush::-CD2DRadialGradientBrush](#_dtorcd2dradialgradientbrush)|Destructor. Se llama cuando se destruye un objeto de pincel de degradado radial D2D.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DRadialGradientBrush::Attach](#attach)|Adjunta la interfaz de recursos existente al objeto|
|[CD2DRadialGradientBrush::Create](#create)|Crea un CD2DRadialGradientBrush. (Reemplaza [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DRadialGradientBrush::Destroy](#destroy)|Destruye un CD2DRadialGradientBrush objeto. (Reemplaza [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[CD2DRadialGradientBrush::Detach](#detach)|Separa la interfaz de recursos del objeto|
|[CD2DRadialGradientBrush::Get](#get)|Devuelve ID2D1RadialGradientBrush interfaz|
|[CD2DRadialGradientBrush::GetCenter](#getcenter)|Recupera el centro de la elipse de degradado|
|[CD2DRadialGradientBrush::GetGradientOriginOffset](#getgradientoriginoffset)|Recupera el desplazamiento del origen del degradado en relación con el centro de la elipse de degradado|
|[CD2DRadialGradientBrush::GetRadiusX](#getradiusx)|Recupera el radio x de la elipse de degradado|
|[CD2DRadialGradientBrush::GetRadiusY](#getradiusy)|Recupera el radio Y de la elipse de degradado|
|[CD2DRadialGradientBrush::SetCenter](#setcenter)|Especifica el centro de la elipse de degradado en el espacio de coordenadas del pincel|
|[CD2DRadialGradientBrush::SetGradientOriginOffset](#setgradientoriginoffset)|Especifica el desfase del origen del degradado en relación con el centro de la elipse de degradado|
|[CD2DRadialGradientBrush::SetRadiusX](#setradiusx)|Especifica el radio x de la elipse de degradado, en el espacio de coordenadas del pincel|
|[CD2DRadialGradientBrush::SetRadiusY](#setradiusy)|Especifica el radio Y de la elipse de degradado, en el espacio de coordenadas del pincel|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush*](#operator_id2d1radialgradientbrush_star)|Devuelve ID2D1RadialGradientBrush interfaz|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DRadialGradientBrush::m_pRadialGradientBrush](#m_pradialgradientbrush)|Un puntero a un ID2D1RadialGradientBrush.|
|[CD2DRadialGradientBrush::m_RadialGradientBrushProperties](#m_radialgradientbrushproperties)|El centro, el desfase de origen de degradado y el radio X y el radio Y del degradado del pincel.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DRadialGradientBrush`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="_dtorcd2dradialgradientbrush"></a>CD2DRadialGradientBrush::-CD2DRadialGradientBrush

Destructor. Se llama cuando se destruye un objeto de pincel de degradado radial D2D.

```
virtual ~CD2DRadialGradientBrush();
```

## <a name="cd2dradialgradientbrushattach"></a><a name="attach"></a>CD2DRadialGradientBrush::Attach

Adjunta la interfaz de recursos existente al objeto

```cpp
void Attach(ID2D1RadialGradientBrush* pResource);
```

### <a name="parameters"></a>Parámetros

*pResource*<br/>
Interfaz de recursos existente. No puede ser NULL

## <a name="cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="cd2dradialgradientbrush"></a>CD2DRadialGradientBrush::CD2DRadialGradientBrush

Construye un CD2DLinearGradientBrush objeto.

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
Un puntero al destino de representación.

*gradientStops*<br/>
Puntero a una matriz de estructuras D2D1_GRADIENT_STOP.

*gradientStopsCount*<br/>
Valor mayor o igual que 1 que especifica el número de paradas de degradado en la matriz gradientStops.

*RadialGradientBrushProperties*<br/>
El centro, el desfase de origen de degradado y el radio X y el radio Y del degradado del pincel.

*colorInterpolationGamma*<br/>
El espacio en el que se realiza la interpolación de color entre el degradado se detiene.

*extendMode*<br/>
El comportamiento del degradado fuera del rango normalizado [0,1].

*pBrushProperties*<br/>
Un puntero a la opacidad y transformación de un pincel.

*bAutoDestroy*<br/>
Indica que el propietario destruirá el objeto (pParentTarget).

## <a name="cd2dradialgradientbrushcreate"></a><a name="create"></a>CD2DRadialGradientBrush::Create

Crea un CD2DRadialGradientBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parámetros

*pRenderTarget*<br/>
Un puntero al destino de representación.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

## <a name="cd2dradialgradientbrushdestroy"></a><a name="destroy"></a>CD2DRadialGradientBrush::Destroy

Destruye un CD2DRadialGradientBrush objeto.

```
virtual void Destroy();
```

## <a name="cd2dradialgradientbrushdetach"></a><a name="detach"></a>CD2DRadialGradientBrush::Detach

Separa la interfaz de recursos del objeto

```
ID2D1RadialGradientBrush* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a interfaz de recursos separada.

## <a name="cd2dradialgradientbrushget"></a><a name="get"></a>CD2DRadialGradientBrush::Get

Devuelve ID2D1RadialGradientBrush interfaz

```
ID2D1RadialGradientBrush* Get();
```

### <a name="return-value"></a>Valor devuelto

Puntero a un ID2D1RadialGradientBrush interfaz o NULL si el objeto no se ha inicializado todavía.

## <a name="cd2dradialgradientbrushgetcenter"></a><a name="getcenter"></a>CD2DRadialGradientBrush::GetCenter

Recupera el centro de la elipse de degradado

```
CD2DPointF GetCenter() const;
```

### <a name="return-value"></a>Valor devuelto

El centro de la elipse de degradado. Este valor se expresa en el espacio de coordenadas del pincel

## <a name="cd2dradialgradientbrushgetgradientoriginoffset"></a><a name="getgradientoriginoffset"></a>CD2DRadialGradientBrush::GetGradientOriginOffset

Recupera el desplazamiento del origen del degradado en relación con el centro de la elipse de degradado

```
CD2DPointF GetGradientOriginOffset() const;
```

### <a name="return-value"></a>Valor devuelto

Desplazamiento del origen del degradado desde el centro de la elipse de degradado. Este valor se expresa en el espacio de coordenadas del pincel

## <a name="cd2dradialgradientbrushgetradiusx"></a><a name="getradiusx"></a>CD2DRadialGradientBrush::GetRadiusX

Recupera el radio x de la elipse de degradado

```
FLOAT GetRadiusX() const;
```

### <a name="return-value"></a>Valor devuelto

El radio x de la elipse de degradado. Este valor se expresa en el espacio de coordenadas del pincel

## <a name="cd2dradialgradientbrushgetradiusy"></a><a name="getradiusy"></a>CD2DRadialGradientBrush::GetRadiusY

Recupera el radio Y de la elipse de degradado

```
FLOAT GetRadiusY() const;
```

### <a name="return-value"></a>Valor devuelto

El radio Y de la elipse degradada. Este valor se expresa en el espacio de coordenadas del pincel

## <a name="cd2dradialgradientbrushm_pradialgradientbrush"></a><a name="m_pradialgradientbrush"></a>CD2DRadialGradientBrush::m_pRadialGradientBrush

Un puntero a un ID2D1RadialGradientBrush.

```
ID2D1RadialGradientBrush* m_pRadialGradientBrush;
```

## <a name="cd2dradialgradientbrushm_radialgradientbrushproperties"></a><a name="m_radialgradientbrushproperties"></a>CD2DRadialGradientBrush::m_RadialGradientBrushProperties

El centro, el desfase de origen de degradado y el radio X y el radio Y del degradado del pincel.

```
D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES m_RadialGradientBrushProperties;
```

## <a name="cd2dradialgradientbrushoperator-id2d1radialgradientbrush"></a><a name="operator_id2d1radialgradientbrush_star"></a>CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush*

Devuelve ID2D1RadialGradientBrush interfaz

```
operator ID2D1RadialGradientBrush*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a un ID2D1RadialGradientBrush interfaz o NULL si el objeto no se ha inicializado todavía.

## <a name="cd2dradialgradientbrushsetcenter"></a><a name="setcenter"></a>CD2DRadialGradientBrush::SetCenter

Especifica el centro de la elipse de degradado en el espacio de coordenadas del pincel

```cpp
void SetCenter(CD2DPointF point);
```

### <a name="parameters"></a>Parámetros

*Punto*<br/>
El centro de la elipse de degradado, en el espacio de coordenadas del pincel

## <a name="cd2dradialgradientbrushsetgradientoriginoffset"></a><a name="setgradientoriginoffset"></a>CD2DRadialGradientBrush::SetGradientOriginOffset

Especifica el desfase del origen del degradado en relación con el centro de la elipse de degradado

```cpp
void SetGradientOriginOffset(CD2DPointF gradientOriginOffset);
```

### <a name="parameters"></a>Parámetros

*gradientOriginOffset*<br/>
El desplazamiento del origen del degradado desde el centro de la elipse de degradado

## <a name="cd2dradialgradientbrushsetradiusx"></a><a name="setradiusx"></a>CD2DRadialGradientBrush::SetRadiusX

Especifica el radio x de la elipse de degradado, en el espacio de coordenadas del pincel

```cpp
void SetRadiusX(FLOAT radiusX);
```

### <a name="parameters"></a>Parámetros

*radiusX*<br/>
El radio x de la elipse de degradado. Este valor está en el espacio de coordenadas del pincel

## <a name="cd2dradialgradientbrushsetradiusy"></a><a name="setradiusy"></a>CD2DRadialGradientBrush::SetRadiusY

Especifica el radio Y de la elipse de degradado, en el espacio de coordenadas del pincel

```cpp
void SetRadiusY(FLOAT radiusY);
```

### <a name="parameters"></a>Parámetros

*radiusY*<br/>
El radio Y de la elipse degradada. Este valor está en el espacio de coordenadas del pincel

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
