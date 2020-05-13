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
ms.openlocfilehash: 30025d6097e439c07202d144a6e549845b78ffa6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754761"
---
# <a name="cd2dlayer-class"></a>Clase CD2DLayer

Un contenedor para ID2D1Layer.

## <a name="syntax"></a>Sintaxis

```
class CD2DLayer : public CD2DResource;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DLayer::CD2DLayer](#cd2dlayer)|Construye un objeto CD2DLayer.|
|[CD2DLayer::-CD2DLayer](#_dtorcd2dlayer)|Destructor. Se llama cuando se destruye un objeto de capa D2D.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DLayer::Attach](#attach)|Adjunta la interfaz de recursos existente al objeto|
|[CD2DLayer::Crear](#create)|Crea un CD2DLayer. (Reemplaza [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DLayer::Destroy](#destroy)|Destruye un objeto CD2DLayer. (Reemplaza [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DLayer::Detach](#detach)|Separa la interfaz de recursos del objeto|
|[CD2DLayer::Get](#get)|Devuelve la interfaz ID2D1Layer|
|[CD2DLayer::GetSize](#getsize)|Devuelve el tamaño del destino de representación en píxeles independientes del dispositivo|
|[CD2DLayer::IsValid](#isvalid)|Comprueba la validez de los recursos (reemplaza [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DLayer::operator ID2D1Layer*](#operator_id2d1layer_star)|Devuelve la interfaz ID2D1Layer|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CD2DLayer::m_pLayer](#m_player)|Almacena un puntero a un ID2D1Layer objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DLayer`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cd2dlayercd2dlayer"></a><a name="_dtorcd2dlayer"></a>CD2DLayer::-CD2DLayer

Destructor. Se llama cuando se destruye un objeto de capa D2D.

```
virtual ~CD2DLayer();
```

## <a name="cd2dlayerattach"></a><a name="attach"></a>CD2DLayer::Attach

Adjunta la interfaz de recursos existente al objeto

```cpp
void Attach(ID2D1Layer* pResource);
```

### <a name="parameters"></a>Parámetros

*pResource*<br/>
Interfaz de recursos existente. No puede ser NULL

## <a name="cd2dlayercd2dlayer"></a><a name="cd2dlayer"></a>CD2DLayer::CD2DLayer

Construye un objeto CD2DLayer.

```
CD2DLayer(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

*pParentTarget*<br/>
Un puntero al destino de representación.

*bAutoDestroy*<br/>
Indica que el propietario destruirá el objeto (pParentTarget).

## <a name="cd2dlayercreate"></a><a name="create"></a>CD2DLayer::Crear

Crea un CD2DLayer.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parámetros

*pRenderTarget*<br/>
Un puntero al destino de representación.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

## <a name="cd2dlayerdestroy"></a><a name="destroy"></a>CD2DLayer::Destroy

Destruye un objeto CD2DLayer.

```
virtual void Destroy();
```

## <a name="cd2dlayerdetach"></a><a name="detach"></a>CD2DLayer::Detach

Separa la interfaz de recursos del objeto

```
ID2D1Layer* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a interfaz de recursos separada.

## <a name="cd2dlayerget"></a><a name="get"></a>CD2DLayer::Get

Devuelve la interfaz ID2D1Layer

```
ID2D1Layer* Get();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1Layer o NULL si el objeto aún no se ha inicializado.

## <a name="cd2dlayergetsize"></a><a name="getsize"></a>CD2DLayer::GetSize

Devuelve el tamaño del destino de representación en píxeles independientes del dispositivo

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño actual del destino de representación en píxeles independientes del dispositivo

## <a name="cd2dlayerisvalid"></a><a name="isvalid"></a>CD2DLayer::IsValid

Comprueba la validez de los recursos

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el recurso es válido; de lo contrario FALSO.

## <a name="cd2dlayerm_player"></a><a name="m_player"></a>CD2DLayer::m_pLayer

Almacena un puntero a un ID2D1Layer objeto.

```
ID2D1Layer* m_pLayer;
```

## <a name="cd2dlayeroperator-id2d1layer"></a><a name="operator_id2d1layer_star"></a>CD2DLayer::operator ID2D1Layer*

Devuelve la interfaz ID2D1Layer

```
operator ID2D1Layer* ();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1Layer o NULL si el objeto aún no se ha inicializado.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
