---
title: Clase CAnimationTimerEventHandler
ms.date: 11/04/2016
f1_keywords:
- CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationTimerEventHandler [MFC], CreateInstance
- CAnimationTimerEventHandler [MFC], OnPostUpdate
- CAnimationTimerEventHandler [MFC], OnPreUpdate
- CAnimationTimerEventHandler [MFC], OnRenderingTooSlow
- CAnimationTimerEventHandler [MFC], SetAnimationController
ms.assetid: 188dea3b-4b5e-4f6b-8df9-09d993a21619
ms.openlocfilehash: c94cb3849d4101365d137733c08135b86db23801
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518669"
---
# <a name="canimationtimereventhandler-class"></a>Clase CAnimationTimerEventHandler

Implementa una devolución de llamada, a la que llama la API de animación cuando se producen eventos de control de tiempo.

## <a name="syntax"></a>Sintaxis

```
class CAnimationTimerEventHandler : public CUIAnimationTimerEventHandlerBase<CAnimationTimerEventHandler>;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationTimerEventHandler::CreateInstance](#createinstance)|Crea una instancia de `CAnimationTimerEventHandler` devolución de llamada.|
|[CAnimationTimerEventHandler::OnPostUpdate](#onpostupdate)|Controla los eventos que se producen una vez finalizada la actualización de una animación. (Invalida `CUIAnimationTimerEventHandlerBase::OnPostUpdate`).|
|[CAnimationTimerEventHandler::OnPreUpdate](#onpreupdate)|Controla los eventos que se producen antes de comenzar una actualización de la animación. (Invalida `CUIAnimationTimerEventHandlerBase::OnPreUpdate`).|
|[CAnimationTimerEventHandler::OnRenderingTooSlow](#onrenderingtooslow)|Controla los eventos que se producen cuando la velocidad de fotogramas de representación para una animación cae por debajo de la velocidad de fotogramas deseable mínimo. (Invalida `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`).|
|[CAnimationTimerEventHandler::SetAnimationController](#setanimationcontroller)|Almacena un puntero al controlador de animación para el enrutamiento de eventos.|

## <a name="remarks"></a>Comentarios

Este controlador de eventos se crea y se pasa a IUIAnimationTimer::SetTimerEventHandler al llamar a CAnimationController::EnableAnimationTimerEventHandler.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CUIAnimationCallbackBase`

`CUIAnimationTimerEventHandlerBase`

`CAnimationTimerEventHandler`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="createinstance"></a>  CAnimationTimerEventHandler::CreateInstance

Crea una instancia de devolución de llamada CAnimationTimerEventHandler.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationTimerEventHandler** ppTimerEventHandler);
```

### <a name="parameters"></a>Parámetros

*pAnimationController*<br/>
Un puntero al controlador de animación, que se va a recibir eventos.

*ppTimerEventHandler*

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. En caso contrario, devuelve un código de error HRESULT.

##  <a name="onpostupdate"></a>  CAnimationTimerEventHandler::OnPostUpdate

Controla los eventos que se producen una vez finalizada la actualización de una animación.

```
IFACEMETHOD(OnPostUpdate)();
```

### <a name="return-value"></a>Valor devuelto

S_OK si el método se realiza correctamente; en caso contrario, E_FAIL.

##  <a name="onpreupdate"></a>  CAnimationTimerEventHandler::OnPreUpdate

Controla los eventos que se producen antes de comenzar una actualización de la animación.

```
IFACEMETHOD(OnPreUpdate)();
```

### <a name="return-value"></a>Valor devuelto

S_OK si el método se realiza correctamente; en caso contrario, E_FAIL.

##  <a name="onrenderingtooslow"></a>  CAnimationTimerEventHandler::OnRenderingTooSlow

Controla los eventos que se producen cuando la velocidad de fotogramas de representación para una animación cae por debajo de la velocidad de fotogramas deseable mínimo.

```
IFACEMETHOD(OnRenderingTooSlow)(UINT32 fps);
```

### <a name="parameters"></a>Parámetros

*fps*

### <a name="return-value"></a>Valor devuelto

S_OK si el método se realiza correctamente; en caso contrario, E_FAIL.

##  <a name="setanimationcontroller"></a>  CAnimationTimerEventHandler::SetAnimationController

Almacena un puntero al controlador de animación para el enrutamiento de eventos.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parámetros

*pAnimationController*<br/>
Un puntero al controlador de animación, que se va a recibir eventos.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
