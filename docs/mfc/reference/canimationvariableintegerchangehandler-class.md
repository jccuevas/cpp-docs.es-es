---
title: Clase CAnimationVariableIntegerChangeHandler
ms.date: 11/04/2016
f1_keywords:
- CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::SetAnimationController
helpviewer_keywords:
- CAnimationVariableIntegerChangeHandler [MFC], CAnimationVariableIntegerChangeHandler
- CAnimationVariableIntegerChangeHandler [MFC], CreateInstance
- CAnimationVariableIntegerChangeHandler [MFC], OnIntegerValueChanged
- CAnimationVariableIntegerChangeHandler [MFC], SetAnimationController
ms.assetid: 6ac8e91b-e514-4ff6-babd-33f77c4b2b61
ms.openlocfilehash: e1c3dc080c23ba4ac05539674047a66059ce52d0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296584"
---
# <a name="canimationvariableintegerchangehandler-class"></a>Clase CAnimationVariableIntegerChangeHandler

Implementa una devolución de llamada, a la que llama la API de animación cuando cambia el valor de una animación.

## <a name="syntax"></a>Sintaxis

```
class CAnimationVariableIntegerChangeHandler : public CUIAnimationVariableIntegerChangeHandlerBase<CAnimationVariableIntegerChangeHandler>;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler](#canimationvariableintegerchangehandler)|Construye un objeto `CAnimationVariableIntegerChangeHandler`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationVariableIntegerChangeHandler::CreateInstance](#createinstance)|Crea una instancia de `CAnimationVariableIntegerChangeHandler` devolución de llamada.|
|[CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged](#onintegervaluechanged)|Se llama cuando ha cambiado un valor de una variable de animación. (Invalida `CUIAnimationVariableIntegerChangeHandlerBase::OnIntegerValueChanged`).|
|[CAnimationVariableIntegerChangeHandler::SetAnimationController](#setanimationcontroller)|Almacena un puntero al controlador de animación para el enrutamiento de eventos.|

## <a name="remarks"></a>Comentarios

Se crea y se pasa al método de IUIAnimationVariable::SetVariableIntegerChangeHandler al CAnimationVariable::EnableIntegerValueChangedEvent o CAnimationBaseObject::EnableIntegerValueChangedEvent (lo que permite llamar a este controlador de eventos Este evento para todas las variables de animación encapsulado en un objeto de animación).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[Clases de MFC](../../mfc/reference/mfc-classes.md)

`CUIAnimationCallbackBase`

`CUIAnimationVariableIntegerChangeHandlerBase`

`CAnimationVariableIntegerChangeHandler`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="canimationvariableintegerchangehandler"></a>  CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler

Construye un objeto CAnimationVariableIntegerChangeHandler.

```
CAnimationVariableIntegerChangeHandler ();
```

##  <a name="createinstance"></a>  CAnimationVariableIntegerChangeHandler::CreateInstance

Crea una instancia de devolución de llamada CAnimationVariableIntegerChangeHandler.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationVariableIntegerChangeHandler** ppHandler);
```

### <a name="parameters"></a>Parámetros

*pAnimationController*<br/>
Un puntero al controlador de animación, que se va a recibir eventos.

*ppHandler*

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. En caso contrario, devuelve un código de error HRESULT.

##  <a name="onintegervaluechanged"></a>  CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged

Se llama cuando ha cambiado un valor de una variable de animación.

```
IFACEMETHOD(OnIntegerValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in INT32 newValue,
    __in INT32 previousValue);
```

### <a name="parameters"></a>Parámetros

*storyboard*<br/>
El guión gráfico que se anima la variable.

*variable*<br/>
La variable de animación que se ha actualizado.

*newValue*<br/>
El nuevo valor redondeado.

*previousValue*<br/>
El valor redondeado anterior.

### <a name="return-value"></a>Valor devuelto

S_OK si el método se realiza correctamente; en caso contrario, E_FAIL.

##  <a name="setanimationcontroller"></a>  CAnimationVariableIntegerChangeHandler::SetAnimationController

Almacena un puntero al controlador de animación para el enrutamiento de eventos.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parámetros

*pAnimationController*<br/>
Un puntero al controlador de animación, que se va a recibir eventos.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
