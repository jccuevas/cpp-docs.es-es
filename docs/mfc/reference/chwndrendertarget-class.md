---
title: Clase CHwndRenderTarget
ms.date: 11/04/2016
f1_keywords:
- CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::Attach
- AFXRENDERTARGET/CHwndRenderTarget::CheckWindowState
- AFXRENDERTARGET/CHwndRenderTarget::Create
- AFXRENDERTARGET/CHwndRenderTarget::Detach
- AFXRENDERTARGET/CHwndRenderTarget::GetHwnd
- AFXRENDERTARGET/CHwndRenderTarget::GetHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::ReCreate
- AFXRENDERTARGET/CHwndRenderTarget::Resize
- AFXRENDERTARGET/CHwndRenderTarget::m_pHwndRenderTarget
helpviewer_keywords:
- CHwndRenderTarget [MFC], CHwndRenderTarget
- CHwndRenderTarget [MFC], Attach
- CHwndRenderTarget [MFC], CheckWindowState
- CHwndRenderTarget [MFC], Create
- CHwndRenderTarget [MFC], Detach
- CHwndRenderTarget [MFC], GetHwnd
- CHwndRenderTarget [MFC], GetHwndRenderTarget
- CHwndRenderTarget [MFC], ReCreate
- CHwndRenderTarget [MFC], Resize
- CHwndRenderTarget [MFC], m_pHwndRenderTarget
ms.assetid: aa65b69f-7202-46ea-af81-ef325da0b840
ms.openlocfilehash: 24cf4127c2f429f66143af3a0f49625f23a4e6ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372464"
---
# <a name="chwndrendertarget-class"></a>Clase CHwndRenderTarget

Un contenedor para ID2D1HwndRenderTarget.

## <a name="syntax"></a>Sintaxis

```
class CHwndRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHwndRenderTarget::CHwndRenderTarget](#chwndrendertarget)|Construye un CHwndRenderTarget objeto de HWND.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHwndRenderTarget::Attach](#attach)|Adjunta la interfaz de destino de representación existente al objeto|
|[CHwndRenderTarget::CheckWindowState](#checkwindowstate)|Indica si el HWND asociado a este destino de representación está ocluido.|
|[CHwndRenderTarget::Create](#create)|Crea un destino de representación asociado a la ventana|
|[CHwndRenderTarget::Detach](#detach)|Separa la interfaz de destino de renderización del objeto|
|[CHwndRenderTarget::GetHwnd](#gethwnd)|Devuelve el HWND asociado a este destino de representación.|
|[CHwndRenderTarget::GetHwndRenderTarget](#gethwndrendertarget)|Devuelve ID2D1HwndRenderTarget interfaz.|
|[CHwndRenderTarget::ReCreate](#recreate)|Vuelve a crear un destino de representación asociado a la ventana|
|[CHwndRenderTarget::Resize](#resize)|Cambia el tamaño del destino de representación al tamaño de píxel especificado|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHwndRenderTarget::operator ID2D1HwndRenderTarget*](#operator_id2d1hwndrendertarget_star)|Devuelve ID2D1HwndRenderTarget interfaz.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CHwndRenderTarget::m_pHwndRenderTarget](#m_phwndrendertarget)|Un puntero a un ID2D1HwndRenderTarget objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

## <a name="chwndrendertargetattach"></a><a name="attach"></a>CHwndRenderTarget::Attach

Adjunta la interfaz de destino de representación existente al objeto

```
void Attach(ID2D1HwndRenderTarget* pTarget);
```

### <a name="parameters"></a>Parámetros

*pTarget*<br/>
Interfaz de destino de representación existente. No puede ser NULL

## <a name="chwndrendertargetcheckwindowstate"></a><a name="checkwindowstate"></a>CHwndRenderTarget::CheckWindowState

Indica si el HWND asociado a este destino de representación está ocluido.

```
D2D1_WINDOW_STATE CheckWindowState() const;
```

### <a name="return-value"></a>Valor devuelto

Valor que indica si el HWND asociado a este destino de representación está ocluido.

## <a name="chwndrendertargetchwndrendertarget"></a><a name="chwndrendertarget"></a>CHwndRenderTarget::CHwndRenderTarget

Construye un CHwndRenderTarget objeto de HWND.

```
CHwndRenderTarget(HWND hwnd = NULL);
```

### <a name="parameters"></a>Parámetros

*Hwnd*<br/>
El HWND asociado a este destino de representación

## <a name="chwndrendertargetcreate"></a><a name="create"></a>CHwndRenderTarget::Create

Crea un destino de representación asociado a la ventana

```
BOOL Create(HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
El HWND asociado a este destino de representación

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE

## <a name="chwndrendertargetdetach"></a><a name="detach"></a>CHwndRenderTarget::Detach

Separa la interfaz de destino de renderización del objeto

```
ID2D1HwndRenderTarget* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a interfaz de destino de representación separada.

## <a name="chwndrendertargetgethwnd"></a><a name="gethwnd"></a>CHwndRenderTarget::GetHwnd

Devuelve el HWND asociado a este destino de representación.

```
HWND GetHwnd() const;
```

### <a name="return-value"></a>Valor devuelto

El HWND asociado a este destino de representación.

## <a name="chwndrendertargetgethwndrendertarget"></a><a name="gethwndrendertarget"></a>CHwndRenderTarget::GetHwndRenderTarget

Devuelve ID2D1HwndRenderTarget interfaz.

```
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```

### <a name="return-value"></a>Valor devuelto

Puntero a un ID2D1HwndRenderTarget interfaz o NULL si el objeto aún no se ha inicializado.

## <a name="chwndrendertargetm_phwndrendertarget"></a><a name="m_phwndrendertarget"></a>CHwndRenderTarget::m_pHwndRenderTarget

Un puntero a un ID2D1HwndRenderTarget objeto.

```
ID2D1HwndRenderTarget* m_pHwndRenderTarget;
```

## <a name="chwndrendertargetoperator-id2d1hwndrendertarget"></a><a name="operator_id2d1hwndrendertarget_star"></a>CHwndRenderTarget::operator ID2D1HwndRenderTarget*

Devuelve ID2D1HwndRenderTarget interfaz.

```
operator ID2D1HwndRenderTarget*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a un ID2D1HwndRenderTarget interfaz o NULL si el objeto aún no se ha inicializado.

## <a name="chwndrendertargetrecreate"></a><a name="recreate"></a>CHwndRenderTarget::ReCreate

Vuelve a crear un destino de representación asociado a la ventana

```
BOOL ReCreate(HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
El HWND asociado a este destino de representación

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.

## <a name="chwndrendertargetresize"></a><a name="resize"></a>CHwndRenderTarget::Resize

Cambia el tamaño del destino de representación al tamaño de píxel especificado

```
BOOL Resize(const CD2DSizeU& size);
```

### <a name="parameters"></a>Parámetros

*Tamaño*<br/>
El nuevo tamaño del destino de representación en píxeles de dispositivo

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
