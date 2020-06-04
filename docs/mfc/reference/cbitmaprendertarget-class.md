---
title: Clase CBitmapRenderTarget
ms.date: 11/04/2016
f1_keywords:
- CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::Attach
- AFXRENDERTARGET/CBitmapRenderTarget::Detach
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmap
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::m_pBitmapRenderTarget
helpviewer_keywords:
- CBitmapRenderTarget [MFC], CBitmapRenderTarget
- CBitmapRenderTarget [MFC], Attach
- CBitmapRenderTarget [MFC], Detach
- CBitmapRenderTarget [MFC], GetBitmap
- CBitmapRenderTarget [MFC], GetBitmapRenderTarget
- CBitmapRenderTarget [MFC], m_pBitmapRenderTarget
ms.assetid: c89a4437-812e-4943-acb2-b429a04cc4d2
ms.openlocfilehash: 8ba8c8819b47185315d67d732fc90ab2ffc0ad0a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752932"
---
# <a name="cbitmaprendertarget-class"></a>Clase CBitmapRenderTarget

Un contenedor para ID2D1BitmapRenderTarget.

## <a name="syntax"></a>Sintaxis

```
class CBitmapRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBitmapRenderTarget::CBitmapRenderTarget](#cbitmaprendertarget)|Construye un CBitmapRenderTarget objeto.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBitmapRenderTarget::Attach](#attach)|Adjunta la interfaz de destino de representación existente al objeto|
|[CBitmapRenderTarget::Detach](#detach)|Separa la interfaz de destino de renderización del objeto|
|[CBitmapRenderTarget::GetBitmap](#getbitmap)|Recupera el mapa de bits para este destino de representación. El mapa de bits devuelto se puede utilizar para las operaciones de dibujo.|
|[CBitmapRenderTarget::GetBitmapRenderTarget](#getbitmaprendertarget)|Devuelve id2D1BitmapRenderTarget interfaz|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBitmapRenderTarget::operator ID2D1BitmapRenderTarget*](#operator_id2d1bitmaprendertarget_star)|Devuelve id2D1BitmapRenderTarget interfaz|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CBitmapRenderTarget::m_pBitmapRenderTarget](#m_pbitmaprendertarget)|Puntero a un ID2D1BitmapRenderTarget objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

`CBitmapRenderTarget`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cbitmaprendertargetattach"></a><a name="attach"></a>CBitmapRenderTarget::Attach

Adjunta la interfaz de destino de representación existente al objeto

```cpp
void Attach(ID2D1BitmapRenderTarget* pTarget);
```

### <a name="parameters"></a>Parámetros

*pTarget*<br/>
Interfaz de destino de representación existente. No puede ser NULL

## <a name="cbitmaprendertargetcbitmaprendertarget"></a><a name="cbitmaprendertarget"></a>CBitmapRenderTarget::CBitmapRenderTarget

Construye un CBitmapRenderTarget objeto.

```
CBitmapRenderTarget();
```

## <a name="cbitmaprendertargetdetach"></a><a name="detach"></a>CBitmapRenderTarget::Detach

Separa la interfaz de destino de renderización del objeto

```
ID2D1BitmapRenderTarget* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a interfaz de destino de representación separada.

## <a name="cbitmaprendertargetgetbitmap"></a><a name="getbitmap"></a>CBitmapRenderTarget::GetBitmap

Recupera el mapa de bits para este destino de representación. El mapa de bits devuelto se puede utilizar para las operaciones de dibujo.

```
BOOL GetBitmap(CD2DBitmap& bitmap);
```

### <a name="parameters"></a>Parámetros

*Bits*<br/>
Cuando se devuelve este método, contiene el mapa de bits válido para este destino de representación. Este mapa de bits se puede utilizar para operaciones de dibujo.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.

## <a name="cbitmaprendertargetgetbitmaprendertarget"></a><a name="getbitmaprendertarget"></a>CBitmapRenderTarget::GetBitmapRenderTarget

Devuelve id2D1BitmapRenderTarget interfaz

```
ID2D1BitmapRenderTarget* GetBitmapRenderTarget();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1BitmapRenderTarget o NULL si el objeto aún no se ha inicializado.

## <a name="cbitmaprendertargetm_pbitmaprendertarget"></a><a name="m_pbitmaprendertarget"></a>CBitmapRenderTarget::m_pBitmapRenderTarget

Puntero a un ID2D1BitmapRenderTarget objeto.

```
ID2D1BitmapRenderTarget* m_pBitmapRenderTarget;
```

## <a name="cbitmaprendertargetoperator-id2d1bitmaprendertarget"></a><a name="operator_id2d1bitmaprendertarget_star"></a>CBitmapRenderTarget::operator ID2D1BitmapRenderTarget*

Devuelve id2D1BitmapRenderTarget interfaz

```
operator ID2D1BitmapRenderTarget*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1BitmapRenderTarget o NULL si el objeto aún no se ha inicializado.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
