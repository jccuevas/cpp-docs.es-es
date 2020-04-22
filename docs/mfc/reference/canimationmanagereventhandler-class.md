---
title: Clase CAnimationManagerEventHandler
ms.date: 11/04/2016
f1_keywords:
- CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::OnManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationManagerEventHandler [MFC], CAnimationManagerEventHandler
- CAnimationManagerEventHandler [MFC], CreateInstance
- CAnimationManagerEventHandler [MFC], OnManagerStatusChanged
- CAnimationManagerEventHandler [MFC], SetAnimationController
ms.assetid: 6089ec07-e661-4805-b227-823b4652aade
ms.openlocfilehash: 58bb37e9de40f4bc711b417eab107aa55b8ff0e8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750118"
---
# <a name="canimationmanagereventhandler-class"></a>Clase CAnimationManagerEventHandler

Implementa una devolución de llamada, a la que llama la API de animación cuando se cambia el estado de un administrador de animación.

## <a name="syntax"></a>Sintaxis

```
class CAnimationManagerEventHandler : public CUIAnimationManagerEventHandlerBase<CAnimationManagerEventHandler>;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationManagerEventHandler::CAnimationManagerEventHandler](#canimationmanagereventhandler)|Construye un objeto `CAnimationManagerEventHandler`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationManagerEventHandler::CreateInstance](#createinstance)|Crea una `CAnimationManagerEventHandler` instancia de object.|
|[CAnimationManagerEventHandler::OnManagerStatusChanged](#onmanagerstatuschanged)|Se llama cuando ha cambiado el estado del administrador de animaciones. (Invalida `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`).|
|[CAnimationManagerEventHandler::SetAnimationController](#setanimationcontroller)|Almacena un puntero al controlador de animación para enrutar eventos.|

## <a name="remarks"></a>Observaciones

Este controlador de eventos se crea y se pasa a IUIAnimationManager::SetManagerEventHandler método, cuando se llama a CAnimationController::EnableAnimationManagerEvent.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CUIAnimationCallbackBase`

`CUIAnimationManagerEventHandlerBase`

`CAnimationManagerEventHandler`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="canimationmanagereventhandlercanimationmanagereventhandler"></a><a name="canimationmanagereventhandler"></a>CAnimationManagerEventHandler::CAnimationManagerEventHandler

Se requiere Visual Studio 2010 SP1.

Construye un CAnimationManagerEventHandler objeto.

```
CAnimationManagerEventHandler();
```

## <a name="canimationmanagereventhandlercreateinstance"></a><a name="createinstance"></a>CAnimationManagerEventHandler::CreateInstance

Se requiere Visual Studio 2010 SP1.

Crea una instancia de CAnimationManagerEventHandler objeto.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationManagerEventHandler** ppManagerEventHandler);
```

### <a name="parameters"></a>Parámetros

*pAnimationController*<br/>
Un puntero al controlador de animación, que recibirá eventos.

*ppManagerEventHandler*<br/>
Salida. Si el método se realiza correctamente, contiene un puntero al objeto COM que controlará las actualizaciones de estado de un administrador de animaciones.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

## <a name="canimationmanagereventhandleronmanagerstatuschanged"></a><a name="onmanagerstatuschanged"></a>CAnimationManagerEventHandler::OnManagerStatusChanged

Se requiere Visual Studio 2010 SP1.

Se llama cuando ha cambiado el estado del administrador de animaciones.

```
IFACEMETHOD(OnManagerStatusChanged)(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Parámetros

*newStatus*<br/>
Nuevo estado.

*previousEstado*<br/>
Estado anterior.

### <a name="return-value"></a>Valor devuelto

La implementación actual siempre devuelve S_OK;

## <a name="canimationmanagereventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationManagerEventHandler::SetAnimationController

Se requiere Visual Studio 2010 SP1.

Almacena un puntero al controlador de animación para enrutar eventos.

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parámetros

*pAnimationController*<br/>
Un puntero al controlador de animación, que recibirá eventos.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
