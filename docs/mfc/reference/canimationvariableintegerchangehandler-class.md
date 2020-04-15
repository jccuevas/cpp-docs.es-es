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
ms.openlocfilehash: 261f8eb17953c047fcc8ec05ae48dc369de4614c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377039"
---
# <a name="canimationvariableintegerchangehandler-class"></a>Clase CAnimationVariableIntegerChangeHandler

Implementa una devolución de llamada, a la que llama la API de animación cuando cambia el valor de una animación.

## <a name="syntax"></a>Sintaxis

```
class CAnimationVariableIntegerChangeHandler : public CUIAnimationVariableIntegerChangeHandlerBase<CAnimationVariableIntegerChangeHandler>;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler](#canimationvariableintegerchangehandler)|Construye un objeto `CAnimationVariableIntegerChangeHandler`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationVariableIntegerChangeHandler::CreateInstance](#createinstance)|Crea una `CAnimationVariableIntegerChangeHandler` instancia de devolución de llamada.|
|[CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged](#onintegervaluechanged)|Se llama cuando un valor de una variable de animación ha cambiado. (Invalida `CUIAnimationVariableIntegerChangeHandlerBase::OnIntegerValueChanged`).|
|[CAnimationVariableIntegerChangeHandler::SetAnimationController](#setanimationcontroller)|Almacena un puntero al controlador de animación para enrutar eventos.|

## <a name="remarks"></a>Observaciones

Este controlador de eventos se crea y se pasa a IUIAnimationVariable::SetVariableIntegerChangeHandler método, cuando se llama a CAnimationVariable::EnableIntegerValueChangedEvent o CAnimationBaseObject::EnableIntegerValueChangedEvent (que habilita este evento para todas las variables de animación encapsuladas en un objeto de animación).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[Clases MFC](../../mfc/reference/mfc-classes.md)

`CUIAnimationCallbackBase`

`CUIAnimationVariableIntegerChangeHandlerBase`

`CAnimationVariableIntegerChangeHandler`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="canimationvariableintegerchangehandlercanimationvariableintegerchangehandler"></a><a name="canimationvariableintegerchangehandler"></a>CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler

Construye un CAnimationVariableIntegerChangeHandler objeto.

```
CAnimationVariableIntegerChangeHandler ();
```

## <a name="canimationvariableintegerchangehandlercreateinstance"></a><a name="createinstance"></a>CAnimationVariableIntegerChangeHandler::CreateInstance

Crea una instancia de CAnimationVariableIntegerChangeHandler devolución de llamada.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationVariableIntegerChangeHandler** ppHandler);
```

### <a name="parameters"></a>Parámetros

*pAnimationController*<br/>
Un puntero al controlador de animación, que recibirá eventos.

*ppHandler*

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. De lo contrario, devuelve un código de error HRESULT.

## <a name="canimationvariableintegerchangehandleronintegervaluechanged"></a><a name="onintegervaluechanged"></a>CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged

Se llama cuando un valor de una variable de animación ha cambiado.

```
IFACEMETHOD(OnIntegerValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in INT32 newValue,
    __in INT32 previousValue);
```

### <a name="parameters"></a>Parámetros

*Guión gráfico*<br/>
El guión gráfico que está animando la variable.

*Variable*<br/>
La variable de animación que se actualizó.

*newValue*<br/>
El nuevo valor redondeado.

*previousValue*<br/>
El valor redondeado anterior.

### <a name="return-value"></a>Valor devuelto

S_OK si el método se realiza correctamente; E_FAIL de lo contrario.

## <a name="canimationvariableintegerchangehandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationVariableIntegerChangeHandler::SetAnimationController

Almacena un puntero al controlador de animación para enrutar eventos.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parámetros

*pAnimationController*<br/>
Un puntero al controlador de animación, que recibirá eventos.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
