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
ms.openlocfilehash: 790ce0f32c2325fa0ea92ca0bda64ddaa4c86c45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375704"
---
# <a name="cdcrendertarget-class"></a>Clase CDCRenderTarget

Un contenedor para ID2D1DCRenderTarget.

## <a name="syntax"></a>Sintaxis

```
class CDCRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDCRenderTarget::CDCRenderTarget](#cdcrendertarget)|Construye un CDCRenderTarget objeto.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDCRenderTarget::Adjuntar](#attach)|Adjunta la interfaz de destino de representación existente al objeto|
|[CDCRenderTarget::BindDC](#binddc)|Enlaza el destino de representación al contexto del dispositivo al que emite comandos de dibujo|
|[CDCRenderTarget::Crear](#create)|Crea un CDCRenderTarget.|
|[CDCRenderTarget::Detach](#detach)|Separa la interfaz de destino de renderización del objeto|
|[CDCRenderTarget::GetDCRenderTarget](#getdcrendertarget)|Devuelve la interfaz ID2D1DCRenderTarget|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDCRenderTarget::operador ID2D1DCRenderTarget*](#operator_id2d1dcrendertarget_star)|Devuelve la interfaz ID2D1DCRenderTarget|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CDCRenderTarget::m_pDCRenderTarget](#m_pdcrendertarget)|Puntero a un ID2D1DCRenderTarget objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="cdcrendertargetattach"></a><a name="attach"></a>CDCRenderTarget::Adjuntar

Adjunta la interfaz de destino de representación existente al objeto

```
void Attach(ID2D1DCRenderTarget* pTarget);
```

### <a name="parameters"></a>Parámetros

*pTarget*<br/>
Interfaz de destino de representación existente. No puede ser NULL

## <a name="cdcrendertargetbinddc"></a><a name="binddc"></a>CDCRenderTarget::BindDC

Enlaza el destino de representación al contexto del dispositivo al que emite comandos de dibujo

```
BOOL BindDC(
    const CDC& dc,
    const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*Dc*<br/>
El contexto del dispositivo al que el destino de representación emite comandos de dibujo

*Rect*<br/>
Las dimensiones del identificador a un contexto de dispositivo (HDC) al que está enlazado el destino de representación

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.

## <a name="cdcrendertargetcdcrendertarget"></a><a name="cdcrendertarget"></a>CDCRenderTarget::CDCRenderTarget

Construye un CDCRenderTarget objeto.

```
CDCRenderTarget();
```

## <a name="cdcrendertargetcreate"></a><a name="create"></a>CDCRenderTarget::Crear

Crea un CDCRenderTarget.

```
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```

### <a name="parameters"></a>Parámetros

*Apoyos*<br/>
El modo de representación, el formato de píxel, las opciones de comunicación remota, la información de PPP y la compatibilidad mínima con DirectX necesaria para la representación de hardware.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.

## <a name="cdcrendertargetdetach"></a><a name="detach"></a>CDCRenderTarget::Detach

Separa la interfaz de destino de renderización del objeto

```
ID2D1DCRenderTarget* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a interfaz de destino de representación separada.

## <a name="cdcrendertargetgetdcrendertarget"></a><a name="getdcrendertarget"></a>CDCRenderTarget::GetDCRenderTarget

Devuelve la interfaz ID2D1DCRenderTarget

```
ID2D1DCRenderTarget* GetDCRenderTarget();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1DCRenderTarget o NULL si el objeto aún no se ha inicializado.

## <a name="cdcrendertargetm_pdcrendertarget"></a><a name="m_pdcrendertarget"></a>CDCRenderTarget::m_pDCRenderTarget

Puntero a un ID2D1DCRenderTarget objeto.

```
ID2D1DCRenderTarget* m_pDCRenderTarget;
```

## <a name="cdcrendertargetoperator-id2d1dcrendertarget"></a><a name="operator_id2d1dcrendertarget_star"></a>CDCRenderTarget::operador ID2D1DCRenderTarget*

Devuelve la interfaz ID2D1DCRenderTarget

```
operator ID2D1DCRenderTarget*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1DCRenderTarget o NULL si el objeto aún no se ha inicializado.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
