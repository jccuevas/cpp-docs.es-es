---
title: Clase CD2DSolidColorBrush | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::Attach
- AFXRENDERTARGET/CD2DSolidColorBrush::Create
- AFXRENDERTARGET/CD2DSolidColorBrush::Destroy
- AFXRENDERTARGET/CD2DSolidColorBrush::Detach
- AFXRENDERTARGET/CD2DSolidColorBrush::Get
- AFXRENDERTARGET/CD2DSolidColorBrush::GetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::SetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::m_colorSolid
- AFXRENDERTARGET/CD2DSolidColorBrush::m_pSolidColorBrush
dev_langs:
- C++
helpviewer_keywords:
- CD2DSolidColorBrush [MFC], CD2DSolidColorBrush
- CD2DSolidColorBrush [MFC], Attach
- CD2DSolidColorBrush [MFC], Create
- CD2DSolidColorBrush [MFC], Destroy
- CD2DSolidColorBrush [MFC], Detach
- CD2DSolidColorBrush [MFC], Get
- CD2DSolidColorBrush [MFC], GetColor
- CD2DSolidColorBrush [MFC], SetColor
- CD2DSolidColorBrush [MFC], m_colorSolid
- CD2DSolidColorBrush [MFC], m_pSolidColorBrush
ms.assetid: d4506637-acce-4f74-8a9b-f0a45571a735
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb261fde28755d69e68ee7cf3bf69031ace69893
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437761"
---
# <a name="cd2dsolidcolorbrush-class"></a>Clase CD2DSolidColorBrush

Un contenedor para ID2D1SolidColorBrush.

## <a name="syntax"></a>Sintaxis

```
class CD2DSolidColorBrush : public CD2DBrush;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DSolidColorBrush::CD2DSolidColorBrush](#cd2dsolidcolorbrush)|Sobrecargado. Construye un objeto CD2DSolidColorBrush.|
|[CD2DSolidColorBrush:: ~ CD2DSolidColorBrush](#cd2dsolidcolorbrush__~cd2dsolidcolorbrush)|Destructor. Se llama cuando se destruye un objeto de pincel sólido D2D.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DSolidColorBrush::Attach](#attach)|Adjunta existente de la interfaz de recurso para el objeto|
|[CD2DSolidColorBrush::Create](#create)|Crea un CD2DSolidColorBrush. (Invalida [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DSolidColorBrush::Destroy](#destroy)|Destruye un objeto CD2DSolidColorBrush. (Invalida [CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[CD2DSolidColorBrush::Detach](#detach)|Separa la interfaz de recursos desde el objeto|
|[CD2DSolidColorBrush::Get](#get)|Interfaz de ID2D1SolidColorBrush devuelve|
|[CD2DSolidColorBrush::GetColor](#getcolor)|Recupera el color del pincel de color sólido|
|[CD2DSolidColorBrush::SetColor](#setcolor)|Especifica el color de este pincel de color sólido|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DSolidColorBrush::operator ID2D1SolidColorBrush *](#operator_id2d1solidcolorbrush_star)|Interfaz de ID2D1SolidColorBrush devuelve|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|nombre|Descripción|
|----------|-----------------|
|[CD2DSolidColorBrush::m_colorSolid](#m_colorsolid)|Pincel de color sólido.|
|[CD2DSolidColorBrush::m_pSolidColorBrush](#m_psolidcolorbrush)|Almacena un puntero a un objeto ID2D1SolidColorBrush.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DSolidColorBrush](../../mfc/reference/cd2dsolidcolorbrush-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

##  <a name="_dtorcd2dsolidcolorbrush"></a>  CD2DSolidColorBrush:: ~ CD2DSolidColorBrush

Destructor. Se llama cuando se destruye un objeto de pincel sólido D2D.

```
virtual ~CD2DSolidColorBrush();
```

##  <a name="attach"></a>  CD2DSolidColorBrush::Attach

Adjunta existente de la interfaz de recurso para el objeto

```
void Attach(ID2D1SolidColorBrush* pResource);
```

### <a name="parameters"></a>Parámetros

*pResource*<br/>
Interfaz de recursos existente. No puede ser NULL

##  <a name="cd2dsolidcolorbrush"></a>  CD2DSolidColorBrush::CD2DSolidColorBrush

Construye un objeto CD2DSolidColorBrush.

```
CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,
    D2D1_COLOR_F color,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);


CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,
    COLORREF color,
    int nAlpha = 255,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

*pParentTarget*<br/>
Un puntero para el destino de representación.

*Color*<br/>
Los valores rojos, verdes, azules y alfabéticos del color del pincel.

*pBrushProperties*<br/>
Un puntero a la opacidad y la transformación de un pincel.

*bAutoDestroy*<br/>
Indica que se va a destruir el objeto propietario (pParentTarget).

*nAlpha*<br/>
La opacidad del color del pincel.

##  <a name="create"></a>  CD2DSolidColorBrush::Create

Crea un CD2DSolidColorBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parámetros

*pRenderTarget*<br/>
Un puntero para el destino de representación.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. En caso contrario, devuelve un código de error HRESULT.

##  <a name="destroy"></a>  CD2DSolidColorBrush::Destroy

Destruye un objeto CD2DSolidColorBrush.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DSolidColorBrush::Detach

Separa la interfaz de recursos desde el objeto

```
ID2D1SolidColorBrush* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a interfaz separada del recurso.

##  <a name="get"></a>  CD2DSolidColorBrush::Get

Interfaz de ID2D1SolidColorBrush devuelve

```
ID2D1SolidColorBrush* Get();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1SolidColorBrush o NULL si el objeto no se ha inicializado todavía.

##  <a name="getcolor"></a>  CD2DSolidColorBrush::GetColor

Recupera el color del pincel de color sólido

```
D2D1_COLOR_F GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

El color de este pincel de color sólido

##  <a name="m_colorsolid"></a>  CD2DSolidColorBrush::m_colorSolid

Pincel de color sólido.

```
D2D1_COLOR_F m_colorSolid;
```

##  <a name="m_psolidcolorbrush"></a>  CD2DSolidColorBrush::m_pSolidColorBrush

Almacena un puntero a un objeto ID2D1SolidColorBrush.

```
ID2D1SolidColorBrush* m_pSolidColorBrush;
```

##  <a name="operator_id2d1solidcolorbrush_star"></a>  CD2DSolidColorBrush::operator ID2D1SolidColorBrush *

Interfaz de ID2D1SolidColorBrush devuelve

```
operator ID2D1SolidColorBrush*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1SolidColorBrush o NULL si el objeto no se ha inicializado todavía.

##  <a name="setcolor"></a>  CD2DSolidColorBrush::SetColor

Especifica el color de este pincel de color sólido

```
void SetColor(D2D1_COLOR_F color);
```

### <a name="parameters"></a>Parámetros

*Color*<br/>
El color de este pincel de color sólido

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
