---
title: Clase CD2DLayer
ms.date: 11/04/2016
f1_keywords:
- CD2DLayer
- AFXRENDERTARGET/CD2DLayer
- AFXRENDERTARGET/CD2DLayer::CD2DLayer
- AFXRENDERTARGET/CD2DLayer::Attach
- AFXRENDERTARGET/CD2DLayer::Create
- AFXRENDERTARGET/CD2DLayer::Destroy
- AFXRENDERTARGET/CD2DLayer::Detach
- AFXRENDERTARGET/CD2DLayer::Get
- AFXRENDERTARGET/CD2DLayer::GetSize
- AFXRENDERTARGET/CD2DLayer::IsValid
- AFXRENDERTARGET/CD2DLayer::m_pLayer
helpviewer_keywords:
- CD2DLayer [MFC], CD2DLayer
- CD2DLayer [MFC], Attach
- CD2DLayer [MFC], Create
- CD2DLayer [MFC], Destroy
- CD2DLayer [MFC], Detach
- CD2DLayer [MFC], Get
- CD2DLayer [MFC], GetSize
- CD2DLayer [MFC], IsValid
- CD2DLayer [MFC], m_pLayer
ms.assetid: 2f96378e-66bb-40d1-9661-6afe324de3c1
ms.openlocfilehash: 28ebe19b0f28692116a0b95721ff2e5490ad7e68
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270883"
---
# <a name="cd2dlayer-class"></a>Clase CD2DLayer

Un contenedor para ID2D1Layer.

## <a name="syntax"></a>Sintaxis

```
class CD2DLayer : public CD2DResource;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DLayer::CD2DLayer](#cd2dlayer)|Construye un objeto CD2DLayer.|
|[CD2DLayer::~CD2DLayer](#_dtorcd2dlayer)|Destructor. Se llama cuando se destruye un objeto de capa de D2D.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DLayer::Attach](#attach)|Adjunta existente de la interfaz de recurso para el objeto|
|[CD2DLayer::Create](#create)|Crea un CD2DLayer. (Invalida [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DLayer::Destroy](#destroy)|Destruye un objeto CD2DLayer. (Invalida [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DLayer::Detach](#detach)|Separa la interfaz de recursos desde el objeto|
|[CD2DLayer::Get](#get)|Interfaz de ID2D1Layer devuelve|
|[CD2DLayer::GetSize](#getsize)|Devuelve el tamaño del destino de representación en píxeles independientes del dispositivo|
|[CD2DLayer::IsValid](#isvalid)|Comprueba la validez de los recursos (invalidaciones [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CD2DLayer::operator ID2D1Layer *](#operator_id2d1layer_star)|Interfaz de ID2D1Layer devuelve|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|nombre|Descripción|
|----------|-----------------|
|[CD2DLayer::m_pLayer](#m_player)|Almacena un puntero a un objeto ID2D1Layer.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DLayer`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

##  <a name="_dtorcd2dlayer"></a>  CD2DLayer::~CD2DLayer

Destructor. Se llama cuando se destruye un objeto de capa de D2D.

```
virtual ~CD2DLayer();
```

##  <a name="attach"></a>  CD2DLayer::Attach

Adjunta existente de la interfaz de recurso para el objeto

```
void Attach(ID2D1Layer* pResource);
```

### <a name="parameters"></a>Parámetros

*pResource*<br/>
Interfaz de recursos existente. No puede ser NULL

##  <a name="cd2dlayer"></a>  CD2DLayer::CD2DLayer

Construye un objeto CD2DLayer.

```
CD2DLayer(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

*pParentTarget*<br/>
Un puntero para el destino de representación.

*bAutoDestroy*<br/>
Indica que se va a destruir el objeto propietario (pParentTarget).

##  <a name="create"></a>  CD2DLayer::Create

Crea un CD2DLayer.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parámetros

*pRenderTarget*<br/>
Un puntero para el destino de representación.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. En caso contrario, devuelve un código de error HRESULT.

##  <a name="destroy"></a>  CD2DLayer::Destroy

Destruye un objeto CD2DLayer.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DLayer::Detach

Separa la interfaz de recursos desde el objeto

```
ID2D1Layer* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a interfaz separada del recurso.

##  <a name="get"></a>  CD2DLayer::Get

Interfaz de ID2D1Layer devuelve

```
ID2D1Layer* Get();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1Layer o NULL si el objeto no se ha inicializado todavía.

##  <a name="getsize"></a>  CD2DLayer::GetSize

Devuelve el tamaño del destino de representación en píxeles independientes del dispositivo

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño actual del destino de representación en píxeles independientes del dispositivo

##  <a name="isvalid"></a>  CD2DLayer::IsValid

Comprobaciones de validez de los recursos

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el recurso es válida; en caso contrario, FALSE.

##  <a name="m_player"></a>  CD2DLayer::m_pLayer

Almacena un puntero a un objeto ID2D1Layer.

```
ID2D1Layer* m_pLayer;
```

##  <a name="operator_id2d1layer_star"></a>  CD2DLayer::operator ID2D1Layer *

Interfaz de ID2D1Layer devuelve

```
operator ID2D1Layer* ();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1Layer o NULL si el objeto no se ha inicializado todavía.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
