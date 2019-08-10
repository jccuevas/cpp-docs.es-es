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
ms.openlocfilehash: bd13ba4d0dd60f65372b2c1f51d70d338566301e
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916259"
---
# <a name="canimationmanagereventhandler-class"></a>Clase CAnimationManagerEventHandler

Implementa una devolución de llamada, a la que llama la API de animación cuando se cambia el estado de un administrador de animación.

## <a name="syntax"></a>Sintaxis

```
class CAnimationManagerEventHandler : public CUIAnimationManagerEventHandlerBase<CAnimationManagerEventHandler>;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAnimationManagerEventHandler::CAnimationManagerEventHandler](#canimationmanagereventhandler)|Construye un objeto `CAnimationManagerEventHandler`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAnimationManagerEventHandler::CreateInstance](#createinstance)|Crea una instancia del `CAnimationManagerEventHandler` objeto.|
|[CAnimationManagerEventHandler::OnManagerStatusChanged](#onmanagerstatuschanged)|Se llama cuando cambia el estado del administrador de animaciones. (Invalida `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`).|
|[CAnimationManagerEventHandler::SetAnimationController](#setanimationcontroller)|Almacena un puntero a un controlador de animación para enrutar los eventos.|

## <a name="remarks"></a>Comentarios

Este controlador de eventos se crea y se pasa al método IUIAnimationManager:: SetManagerEventHandler, cuando se llama a CAnimationController:: EnableAnimationManagerEvent.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CUIAnimationCallbackBase`

`CUIAnimationManagerEventHandlerBase`

`CAnimationManagerEventHandler`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="canimationmanagereventhandler"></a>  CAnimationManagerEventHandler::CAnimationManagerEventHandler

Se requiere Visual Studio 2010 SP1.

Construye un objeto CAnimationManagerEventHandler.

```
CAnimationManagerEventHandler();
```

##  <a name="createinstance"></a>  CAnimationManagerEventHandler::CreateInstance

Se requiere Visual Studio 2010 SP1.

Crea una instancia del objeto CAnimationManagerEventHandler.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationManagerEventHandler** ppManagerEventHandler);
```

### <a name="parameters"></a>Parámetros

*pAnimationController*<br/>
Un puntero a un controlador de animación, que recibirá eventos.

*ppManagerEventHandler*<br/>
Genere. Si el método se ejecuta correctamente, contiene un puntero a un objeto COM que controlará las actualizaciones de estado de un administrador de animaciones.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, Devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

##  <a name="onmanagerstatuschanged"></a>  CAnimationManagerEventHandler::OnManagerStatusChanged

Se requiere Visual Studio 2010 SP1.

Se llama cuando cambia el estado del administrador de animaciones.

```
IFACEMETHOD(OnManagerStatusChanged)(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Parámetros

*newStatus*<br/>
Nuevo estado.

*previousStatus*<br/>
Estado anterior.

### <a name="return-value"></a>Valor devuelto

La implementación actual siempre Devuelve S_OK;

##  <a name="setanimationcontroller"></a>  CAnimationManagerEventHandler::SetAnimationController

Se requiere Visual Studio 2010 SP1.

Almacena un puntero a un controlador de animación para enrutar los eventos.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parámetros

*pAnimationController*<br/>
Un puntero a un controlador de animación, que recibirá eventos.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
