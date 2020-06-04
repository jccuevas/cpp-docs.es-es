---
title: Clase CAnimationVariableChangeHandler
ms.date: 11/04/2016
f1_keywords:
- CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::OnValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::SetAnimationController
helpviewer_keywords:
- CAnimationVariableChangeHandler [MFC], OnValueChanged
- CAnimationVariableChangeHandler [MFC], SetAnimationController
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
ms.openlocfilehash: 2dc8f2c03f9df34012fb9db1ed5e5b0bb448b17f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755042"
---
# <a name="canimationvariablechangehandler-class"></a>Clase CAnimationVariableChangeHandler

Implementa una devolución de llamada, a la que llama la API de animación cuando cambia el valor de una animación.

## <a name="syntax"></a>Sintaxis

```
class CAnimationVariableChangeHandler : public CUIAnimationVariableChangeHandlerBase<CAnimationVariableChangeHandler>;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CAnimationVariableChangeHandler`|Construye un objeto `CAnimationVariableChangeHandler`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CreateInstance`|Crea una `CAnimationVariableChangeHandler` instancia de object.|
|[CAnimationVariableChangeHandler::OnValueChanged](#onvaluechanged)|Se llama cuando un valor de una variable de animación ha cambiado. (Invalida `CUIAnimationVariableChangeHandlerBase::OnValueChanged`).|
|[CAnimationVariableChangeHandler::SetAnimationController](#setanimationcontroller)|Almacena un puntero al controlador de animación para enrutar eventos.|

## <a name="remarks"></a>Observaciones

Este controlador de eventos `IUIAnimationVariable::SetVariableChangeHandler` se crea y `CAnimationVariable::EnableValueChangedEvent` `CAnimationBaseObject::EnableValueChangedEvent` se pasa al método, cuando se llama o (que habilita este evento para todas las variables de animación encapsuladas en un objeto de animación).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CUIAnimationCallbackBase`

`CUIAnimationVariableChangeHandlerBase`

`CAnimationVariableChangeHandler`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="canimationvariablechangehandleronvaluechanged"></a><a name="onvaluechanged"></a>CAnimationVariableChangeHandler::OnValueChanged

Se llama cuando un valor de una variable de animación ha cambiado.

```
IFACEMETHOD(OnValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in DOUBLE newValue,
    __in DOUBLE previousValue);
```

### <a name="parameters"></a>Parámetros

*Guión gráfico*<br/>
El guión gráfico que está animando la variable.

*Variable*<br/>
La variable de animación que se actualizó.

*newValue*<br/>
Nuevo valor.

*previousValue*<br/>
El valor anterior.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

## <a name="canimationvariablechangehandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationVariableChangeHandler::SetAnimationController

Almacena un puntero al controlador de animación para enrutar eventos.

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parámetros

*pAnimationController*<br/>
Un puntero al controlador de animación, que recibirá eventos.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
