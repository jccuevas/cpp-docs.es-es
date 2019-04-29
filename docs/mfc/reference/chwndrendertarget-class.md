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
ms.openlocfilehash: bf446cdf1ea064943ff92d66ac89b0e4177e6910
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345791"
---
# <a name="chwndrendertarget-class"></a>Clase CHwndRenderTarget

Un contenedor para ID2D1HwndRenderTarget.

## <a name="syntax"></a>Sintaxis

```
class CHwndRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CHwndRenderTarget::CHwndRenderTarget](#chwndrendertarget)|Construye un objeto CHwndRenderTarget de HWND.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CHwndRenderTarget::Attach](#attach)|Adjunta existente representar la interfaz de destino para el objeto|
|[CHwndRenderTarget::CheckWindowState](#checkwindowstate)|Indica si se ocluidos el HWND asociado a este destino de representación.|
|[CHwndRenderTarget::Create](#create)|Crea un destino de representación asociado a la ventana|
|[CHwndRenderTarget::Detach](#detach)|Separa la interfaz de destino de representación del objeto|
|[CHwndRenderTarget::GetHwnd](#gethwnd)|Devuelve el HWND asociado a este destino de representación.|
|[CHwndRenderTarget::GetHwndRenderTarget](#gethwndrendertarget)|Interfaz de ID2D1HwndRenderTarget devuelve.|
|[CHwndRenderTarget::ReCreate](#recreate)|Vuelve a crear un destino de representación asociado a la ventana|
|[CHwndRenderTarget::Resize](#resize)|Cambia el tamaño del destino de representación para el tamaño de píxel especificado|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CHwndRenderTarget::operator ID2D1HwndRenderTarget*](#operator_id2d1hwndrendertarget_star)|Interfaz de ID2D1HwndRenderTarget devuelve.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Name|Descripción|
|----------|-----------------|
|[CHwndRenderTarget::m_pHwndRenderTarget](#m_phwndrendertarget)|Un puntero a un objeto ID2D1HwndRenderTarget.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrendertarget.h

##  <a name="attach"></a>  CHwndRenderTarget::Attach

Adjunta existente representar la interfaz de destino para el objeto

```
void Attach(ID2D1HwndRenderTarget* pTarget);
```

### <a name="parameters"></a>Parámetros

*pTarget*<br/>
Interfaz de destino de representación existente. No puede ser NULL

##  <a name="checkwindowstate"></a>  CHwndRenderTarget::CheckWindowState

Indica si se ocluidos el HWND asociado a este destino de representación.

```
D2D1_WINDOW_STATE CheckWindowState() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor que indica si el HWND asociado a este destino de representación es ocluido.

##  <a name="chwndrendertarget"></a>  CHwndRenderTarget::CHwndRenderTarget

Construye un objeto CHwndRenderTarget de HWND.

```
CHwndRenderTarget(HWND hwnd = NULL);
```

### <a name="parameters"></a>Parámetros

*hwnd*<br/>
El HWND asociado a este destino de representación

##  <a name="create"></a>  CHwndRenderTarget::Create

Crea un destino de representación asociado a la ventana

```
BOOL Create(HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
El HWND asociado a este destino de representación

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. De lo contrario, devuelve FALSE

##  <a name="detach"></a>  CHwndRenderTarget::Detach

Separa la interfaz de destino de representación del objeto

```
ID2D1HwndRenderTarget* Detach();
```

### <a name="return-value"></a>Valor devuelto

Puntero a desasociado representar la interfaz de destino.

##  <a name="gethwnd"></a>  CHwndRenderTarget::GetHwnd

Devuelve el HWND asociado a este destino de representación.

```
HWND GetHwnd() const;
```

### <a name="return-value"></a>Valor devuelto

El HWND asociado a este destino de representación.

##  <a name="gethwndrendertarget"></a>  CHwndRenderTarget::GetHwndRenderTarget

Interfaz de ID2D1HwndRenderTarget devuelve.

```
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1HwndRenderTarget o NULL si el objeto no se ha inicializado todavía.

##  <a name="m_phwndrendertarget"></a>  CHwndRenderTarget::m_pHwndRenderTarget

Un puntero a un objeto ID2D1HwndRenderTarget.

```
ID2D1HwndRenderTarget* m_pHwndRenderTarget;
```

##  <a name="operator_id2d1hwndrendertarget_star"></a>  CHwndRenderTarget::operator ID2D1HwndRenderTarget*

Interfaz de ID2D1HwndRenderTarget devuelve.

```
operator ID2D1HwndRenderTarget*();
```

### <a name="return-value"></a>Valor devuelto

Puntero a una interfaz ID2D1HwndRenderTarget o NULL si el objeto no se ha inicializado todavía.

##  <a name="recreate"></a>  CHwndRenderTarget::ReCreate

Vuelve a crear un destino de representación asociado a la ventana

```
BOOL ReCreate(HWND hWnd);
```

### <a name="parameters"></a>Parámetros

*hWnd*<br/>
El HWND asociado a este destino de representación

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.

##  <a name="resize"></a>  CHwndRenderTarget::Resize

Cambia el tamaño del destino de representación para el tamaño de píxel especificado

```
BOOL Resize(const CD2DSizeU& size);
```

### <a name="parameters"></a>Parámetros

*size*<br/>
El nuevo tamaño del destino de representación en píxeles del dispositivo

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve TRUE. En caso contrario, devuelve FALSE.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
