---
title: Clase CDCRenderTarget
ms.date: 11/04/2016
f1_keywords:
- CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::Attach
- AFXRENDERTARGET/CDCRenderTarget::BindDC
- AFXRENDERTARGET/CDCRenderTarget::Create
- AFXRENDERTARGET/CDCRenderTarget::Detach
- AFXRENDERTARGET/CDCRenderTarget::GetDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::m_pDCRenderTarget
helpviewer_keywords:
- CDCRenderTarget [MFC], CDCRenderTarget
- CDCRenderTarget [MFC], Attach
- CDCRenderTarget [MFC], BindDC
- CDCRenderTarget [MFC], Create
- CDCRenderTarget [MFC], Detach
- CDCRenderTarget [MFC], GetDCRenderTarget
- CDCRenderTarget [MFC], m_pDCRenderTarget
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
ms.openlocfilehash: 70169d2b89d9ea657898f7a96dea27556023d4e2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268283"
---
# <a name="cdcrendertarget-class"></a>Clase CDCRenderTarget

Un contenedor para ID2D1DCRenderTarget.

## <a name="syntax"></a>Sintaxis

```
class CDCRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CDCRenderTarget::CDCRenderTarget](#cdcrendertarget)|Construye un objeto CDCRenderTarget.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDCRenderTarget::Attach](#attach)|Adjunta existente representar la interfaz de destino para el objeto|
|[CDCRenderTarget::BindDC](#binddc)|El destino de representación se enlaza al contexto de dispositivo a la que emite comandos de dibujo|
|[CDCRenderTarget::Create](#create)|Crea un CDCRenderTarget.|
|[CDCRenderTarget::Detach](#detach)|Separa la interfaz de destino de representación del objeto|
|[CDCRenderTarget::GetDCRenderTarget](#getdcrendertarget)|Interfaz de ID2D1DCRenderTarget devuelve|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CDCRenderTarget::operator ID2D1DCRenderTarget *](#operator_id2d1dcrendertarget_star)|Interfaz de ID2D1DCRenderTarget devuelve|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|nombre|Descripción|
|----------|-----------------|
|[CDCRenderTarget::m_pDCRenderTarget](#m_pdcrendertarget)|Un puntero a un objeto ID2D1DCRenderTarget.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

##  <a name="attach"></a>  CDCRenderTarget::Attach

Adjunta existente representar la interfaz de destino para el objeto

```
void Attach(ID2D1DCRenderTarget* pTarget);
```

### <a name="parameters"></a>Parámetros

*pTarget*<br/>
Interfaz de destino de representación existente. No puede ser NULL

##  <a name="binddc"></a>  CDCRenderTarget::BindDC

El destino de representación se enlaza al contexto de dispositivo a la que emite comandos de dibujo

```
BOOL BindDC(
    const CDC& dc,
    const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*dc*<br/>
El contexto de dispositivo a la que el destino de representación emite comandos de dibujo

*rect*<br/>
Las dimensiones del identificador de un contexto de dispositivo (HDC) al que está enlazado el destino de representación

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.

##  <a name="cdcrendertarget"></a>  CDCRenderTarget::CDCRenderTarget

Construye un objeto CDCRenderTarget.

```
CDCRenderTarget();
```

##  <a name="create"></a>  CDCRenderTarget::Create

Crea un CDCRenderTarget.

```
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```

### <a name="parameters"></a>Parámetros

*props*<br/>
El modo de representación, formato de píxel, opciones de comunicación remota, información de PPP y la compatibilidad de DirectX mínima necesario para la representación de hardware.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.

##  <a name="detach"></a>  CDCRenderTarget::Detach

Separa la interfaz de destino de representación del objeto

```
ID2D1DCRenderTarget* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a desasociado representar la interfaz de destino.

##  <a name="getdcrendertarget"></a>  CDCRenderTarget::GetDCRenderTarget

Interfaz de ID2D1DCRenderTarget devuelve

```
ID2D1DCRenderTarget* GetDCRenderTarget();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1DCRenderTarget o NULL si el objeto no se ha inicializado todavía.

##  <a name="m_pdcrendertarget"></a>  CDCRenderTarget::m_pDCRenderTarget

Un puntero a un objeto ID2D1DCRenderTarget.

```
ID2D1DCRenderTarget* m_pDCRenderTarget;
```

##  <a name="operator_id2d1dcrendertarget_star"></a>  CDCRenderTarget::operator ID2D1DCRenderTarget *

Interfaz de ID2D1DCRenderTarget devuelve

```
operator ID2D1DCRenderTarget*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1DCRenderTarget o NULL si el objeto no se ha inicializado todavía.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
