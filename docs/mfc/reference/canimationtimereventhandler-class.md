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
ms.openlocfilehash: 72b6e5d8d9d4823795a1fb053c5f2374cb80fba4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320010"
---
# <a name="canimationtimereventhandler-class"></a>Clase CAnimationTimerEventHandler

Implementa una devolución de llamada, a la que llama la API de animación cuando se producen eventos de control de tiempo.

## <a name="syntax"></a>Sintaxis

```
class CAnimationTimerEventHandler : public CUIAnimationTimerEventHandlerBase<CAnimationTimerEventHandler>;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationTimerEventHandler::CreateInstance](#createinstance)|Crea una `CAnimationTimerEventHandler` instancia de devolución de llamada.|
|[CAnimationTimerEventHandler::OnPostUpdate](#onpostupdate)|Controla los eventos que se producen una vez finalizada una actualización de animación. (Invalida `CUIAnimationTimerEventHandlerBase::OnPostUpdate`).|
|[CAnimationTimerEventHandler::OnPreUpdate](#onpreupdate)|Controla los eventos que se producen antes de que comience una actualización de animación. (Invalida `CUIAnimationTimerEventHandlerBase::OnPreUpdate`).|
|[CAnimationTimerEventHandler::OnRenderingTooSlow](#onrenderingtooslow)|Controla los eventos que se producen cuando la velocidad de fotogramas de representación de una animación cae por debajo de la velocidad de fotogramas mínima deseable. (Invalida `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`).|
|[CAnimationTimerEventHandler::SetAnimationController](#setanimationcontroller)|Almacena un puntero al controlador de animación para enrutar eventos.|

## <a name="remarks"></a>Observaciones

Este controlador de eventos se crea y se pasa a IUIAnimationTimer::SetTimerEventHandler cuando se llama a CAnimationController::EnableAnimationTimerEventHandler.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CUIAnimationCallbackBase`

`CUIAnimationTimerEventHandlerBase`

`CAnimationTimerEventHandler`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="canimationtimereventhandlercreateinstance"></a><a name="createinstance"></a>CAnimationTimerEventHandler::CreateInstance

Crea una instancia de CAnimationTimerEventHandler devolución de llamada.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationTimerEventHandler** ppTimerEventHandler);
```

### <a name="parameters"></a>Parámetros

*pAnimationController*<br/>
Un puntero al controlador de animación, que recibirá eventos.

*ppTimerEventHandler*

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

## <a name="canimationtimereventhandleronpostupdate"></a><a name="onpostupdate"></a>CAnimationTimerEventHandler::OnPostUpdate

Controla los eventos que se producen una vez finalizada una actualización de animación.

```
IFACEMETHOD(OnPostUpdate)();
```

### <a name="return-value"></a>Valor devuelto

S_OK si el método se realiza correctamente; E_FAIL de lo contrario.

## <a name="canimationtimereventhandleronpreupdate"></a><a name="onpreupdate"></a>CAnimationTimerEventHandler::OnPreUpdate

Controla los eventos que se producen antes de que comience una actualización de animación.

```
IFACEMETHOD(OnPreUpdate)();
```

### <a name="return-value"></a>Valor devuelto

S_OK si el método se realiza correctamente; E_FAIL de lo contrario.

## <a name="canimationtimereventhandleronrenderingtooslow"></a><a name="onrenderingtooslow"></a>CAnimationTimerEventHandler::OnRenderingTooSlow

Controla los eventos que se producen cuando la velocidad de fotogramas de representación de una animación cae por debajo de la velocidad de fotogramas mínima deseable.

```
IFACEMETHOD(OnRenderingTooSlow)(UINT32 fps);
```

### <a name="parameters"></a>Parámetros

*Fps*

### <a name="return-value"></a>Valor devuelto

S_OK si el método se realiza correctamente; E_FAIL de lo contrario.

## <a name="canimationtimereventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationTimerEventHandler::SetAnimationController

Almacena un puntero al controlador de animación para enrutar eventos.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parámetros

*pAnimationController*<br/>
Un puntero al controlador de animación, que recibirá eventos.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
