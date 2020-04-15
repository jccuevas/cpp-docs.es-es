---
title: Clase CD2DLinearGradientBrush
ms.date: 11/04/2016
f1_keywords:
- CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::Attach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Create
- AFXRENDERTARGET/CD2DLinearGradientBrush::Destroy
- AFXRENDERTARGET/CD2DLinearGradientBrush::Detach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Get
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_LinearGradientBrushProperties
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_pLinearGradientBrush
helpviewer_keywords:
- CD2DLinearGradientBrush [MFC], CD2DLinearGradientBrush
- CD2DLinearGradientBrush [MFC], Attach
- CD2DLinearGradientBrush [MFC], Create
- CD2DLinearGradientBrush [MFC], Destroy
- CD2DLinearGradientBrush [MFC], Detach
- CD2DLinearGradientBrush [MFC], Get
- CD2DLinearGradientBrush [MFC], GetEndPoint
- CD2DLinearGradientBrush [MFC], GetStartPoint
- CD2DLinearGradientBrush [MFC], SetEndPoint
- CD2DLinearGradientBrush [MFC], SetStartPoint
- CD2DLinearGradientBrush [MFC], m_LinearGradientBrushProperties
- CD2DLinearGradientBrush [MFC], m_pLinearGradientBrush
ms.assetid: d4be9ff9-0ea8-45e6-9b8d-f3bc5673cbac
ms.openlocfilehash: 6c488d66962f26b6ca9b8c63cb387fc75191085a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369197"
---
# <a name="cd2dlineargradientbrush-class"></a>Clase CD2DLinearGradientBrush

Un contenedor para ID2D1LinearGradientBrush.

## <a name="syntax"></a>Sintaxis

```
class CD2DLinearGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DLinearGradientBrush::CD2DLinearGradientBrush](#cd2dlineargradientbrush)|Construye un CD2DLinearGradientBrush objeto.|
|[CD2DLinearGradientBrush::-CD2DLinearGradientBrush](#_dtorcd2dlineargradientbrush)|Destructor. Se llama cuando se destruye un objeto de pincel de degradado lineal D2D.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DLinearGradientBrush::Attach](#attach)|Adjunta la interfaz de recursos existente al objeto|
|[CD2DLinearGradientBrush::Create](#create)|Crea un CD2DLinearGradientBrush. (Reemplaza [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DLinearGradientBrush::Destroy](#destroy)|Destruye un CD2DLinearGradientBrush objeto. (Reemplaza [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[CD2DLinearGradientBrush::Detach](#detach)|Separa la interfaz de recursos del objeto|
|[CD2DLinearGradientBrush::Get](#get)|Devuelve ID2D1LinearGradientBrush interfaz|
|[CD2DLinearGradientBrush::GetEndPoint](#getendpoint)|Recupera las coordenadas finales del degradado lineal|
|[CD2DLinearGradientBrush::GetStartPoint](#getstartpoint)|Recupera las coordenadas iniciales del degradado lineal|
|[CD2DLinearGradientBrush::SetEndPoint](#setendpoint)|Establece las coordenadas finales del degradado lineal en el espacio de coordenadas del pincel|
|[CD2DLinearGradientBrush::SetStartPoint](#setstartpoint)|Establece las coordenadas iniciales del degradado lineal en el espacio de coordenadas del pincel|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush*](#operator_id2d1lineargradientbrush_star)|Devuelve ID2D1LinearGradientBrush interfaz|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DLinearGradientBrush::m_LinearGradientBrushProperties](#m_lineargradientbrushproperties)|Los puntos inicial y final del degradado.|
|[CD2DLinearGradientBrush::m_pLinearGradientBrush](#m_plineargradientbrush)|Un puntero a un ID2D1LinearGradientBrush.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DLinearGradientBrush`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="_dtorcd2dlineargradientbrush"></a>CD2DLinearGradientBrush::-CD2DLinearGradientBrush

Destructor. Se llama cuando se destruye un objeto de pincel de degradado lineal D2D.

```
virtual ~CD2DLinearGradientBrush();
```

## <a name="cd2dlineargradientbrushattach"></a><a name="attach"></a>CD2DLinearGradientBrush::Attach

Adjunta la interfaz de recursos existente al objeto

```
void Attach(ID2D1LinearGradientBrush* pResource);
```

### <a name="parameters"></a>Parámetros

*pResource*<br/>
Interfaz de recursos existente. No puede ser NULL

## <a name="cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="cd2dlineargradientbrush"></a>CD2DLinearGradientBrush::CD2DLinearGradientBrush

Construye un CD2DLinearGradientBrush objeto.

```
CD2DLinearGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES LinearGradientBrushProperties,
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

*LinearGradientBrushProperties*<br/>
Los puntos inicial y final del degradado.

*colorInterpolationGamma*<br/>
El espacio en el que se realiza la interpolación de color entre el degradado se detiene.

*extendMode*<br/>
El comportamiento del degradado fuera del rango normalizado [0,1].

*pBrushProperties*<br/>
Un puntero a la opacidad y transformación de un pincel.

*bAutoDestroy*<br/>
Indica que el propietario destruirá el objeto (pParentTarget).

## <a name="cd2dlineargradientbrushcreate"></a><a name="create"></a>CD2DLinearGradientBrush::Create

Crea un CD2DLinearGradientBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parámetros

*pRenderTarget*<br/>
Un puntero al destino de representación.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

## <a name="cd2dlineargradientbrushdestroy"></a><a name="destroy"></a>CD2DLinearGradientBrush::Destroy

Destruye un CD2DLinearGradientBrush objeto.

```
virtual void Destroy();
```

## <a name="cd2dlineargradientbrushdetach"></a><a name="detach"></a>CD2DLinearGradientBrush::Detach

Separa la interfaz de recursos del objeto

```
ID2D1LinearGradientBrush* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a interfaz de recursos separada.

## <a name="cd2dlineargradientbrushget"></a><a name="get"></a>CD2DLinearGradientBrush::Get

Devuelve ID2D1LinearGradientBrush interfaz

```
ID2D1LinearGradientBrush* Get();
```

### <a name="return-value"></a>Valor devuelto

Puntero a un ID2D1LinearGradientBrush interfaz o NULL si el objeto no se ha inicializado todavía.

## <a name="cd2dlineargradientbrushgetendpoint"></a><a name="getendpoint"></a>CD2DLinearGradientBrush::GetEndPoint

Recupera las coordenadas finales del degradado lineal

```
CD2DPointF GetEndPoint() const;
```

### <a name="return-value"></a>Valor devuelto

Las coordenadas bidimensionales finales del degradado lineal, en el espacio de coordenadas del pincel

## <a name="cd2dlineargradientbrushgetstartpoint"></a><a name="getstartpoint"></a>CD2DLinearGradientBrush::GetStartPoint

Recupera las coordenadas iniciales del degradado lineal

```
CD2DPointF GetStartPoint() const;
```

### <a name="return-value"></a>Valor devuelto

Las coordenadas bidimensionales iniciales del degradado lineal, en el espacio de coordenadas del pincel

## <a name="cd2dlineargradientbrushm_lineargradientbrushproperties"></a><a name="m_lineargradientbrushproperties"></a>CD2DLinearGradientBrush::m_LinearGradientBrushProperties

Los puntos inicial y final del degradado.

```
D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES m_LinearGradientBrushProperties;
```

## <a name="cd2dlineargradientbrushm_plineargradientbrush"></a><a name="m_plineargradientbrush"></a>CD2DLinearGradientBrush::m_pLinearGradientBrush

Un puntero a un ID2D1LinearGradientBrush.

```
ID2D1LinearGradientBrush* m_pLinearGradientBrush;
```

## <a name="cd2dlineargradientbrushoperator-id2d1lineargradientbrush"></a><a name="operator_id2d1lineargradientbrush_star"></a>CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush*

Devuelve ID2D1LinearGradientBrush interfaz

```
operator ID2D1LinearGradientBrush*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a un ID2D1LinearGradientBrush interfaz o NULL si el objeto no se ha inicializado todavía.

## <a name="cd2dlineargradientbrushsetendpoint"></a><a name="setendpoint"></a>CD2DLinearGradientBrush::SetEndPoint

Establece las coordenadas finales del degradado lineal en el espacio de coordenadas del pincel

```
void SetEndPoint(CD2DPointF point);
```

### <a name="parameters"></a>Parámetros

*Punto*<br/>
Las coordenadas bidimensionales finales del degradado lineal, en el espacio de coordenadas del pincel

## <a name="cd2dlineargradientbrushsetstartpoint"></a><a name="setstartpoint"></a>CD2DLinearGradientBrush::SetStartPoint

Establece las coordenadas iniciales del degradado lineal en el espacio de coordenadas del pincel

```
void SetStartPoint(CD2DPointF point);
```

### <a name="parameters"></a>Parámetros

*Punto*<br/>
Las coordenadas bidimensionales iniciales del degradado lineal, en el espacio de coordenadas del pincel

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
