---
title: Clase CInterpolatorBase
ms.date: 11/04/2016
f1_keywords:
- CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CreateInstance
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDependencies
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetFinalValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetCustomInterpolator
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetInitialValueAndVelocity
helpviewer_keywords:
- CInterpolatorBase [MFC], CInterpolatorBase
- CInterpolatorBase [MFC], CreateInstance
- CInterpolatorBase [MFC], GetDependencies
- CInterpolatorBase [MFC], GetDuration
- CInterpolatorBase [MFC], GetFinalValue
- CInterpolatorBase [MFC], InterpolateValue
- CInterpolatorBase [MFC], InterpolateVelocity
- CInterpolatorBase [MFC], SetCustomInterpolator
- CInterpolatorBase [MFC], SetDuration
- CInterpolatorBase [MFC], SetInitialValueAndVelocity
ms.assetid: bbc3dce7-8398-47f9-b97e-e4fd2d737232
ms.openlocfilehash: efa08aa5dd556d7e136323c31451a9f33bd72ec6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754946"
---
# <a name="cinterpolatorbase-class"></a>Clase CInterpolatorBase

Implementa una devolución de llamada, a la que llama la API de animación cuando tiene que calcular un nuevo valor de una variable de animación.

## <a name="syntax"></a>Sintaxis

```
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|Construye el `CInterpolatorBase` objeto.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CInterpolatorBase::CreateInstance](#createinstance)|Crea una `CInterpolatorBase` instancia de un interpolador personalizado y lo almacena, que controlará los eventos.|
|[CInterpolatorBase::GetDependencies](#getdependencies)|Obtiene las dependencias del interpolador. (Invalida `CUIAnimationInterpolatorBase::GetDependencies`).|
|[CInterpolatorBase::GetDuration](#getduration)|Obtiene la duración del interpolador. (Invalida `CUIAnimationInterpolatorBase::GetDuration`).|
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|Obtiene el valor final al que conduce el interpolador. (Invalida `CUIAnimationInterpolatorBase::GetFinalValue`).|
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|Interpola el valor en un desplazamiento `CUIAnimationInterpolatorBase::InterpolateValue`determinado (Reemplaza .)|
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|Interpola la velocidad en un desplazamiento `CUIAnimationInterpolatorBase::InterpolateVelocity`determinado (Reemplaza .)|
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|Almacena un puntero al interpolador personalizado, que controlará los eventos.|
|[CInterpolatorBase::SetDuration](#setduration)|Establece la duración del interpolador `CUIAnimationInterpolatorBase::SetDuration`(Reemplaza .)|
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Establece el valor inicial y la velocidad del interpolador. (Invalida `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`).|

## <a name="remarks"></a>Observaciones

Este controlador se crea `IUIAnimationTransitionFactory::CreateTransition` y `CCustomTransition` se pasa a cuando se crea un `CAnimationController::AnimateGroup`objeto como parte del proceso de inicialización de animación (iniciado por ). Normalmente no es necesario usar esta clase directamente, simplemente `CCustomInterpolator`renuncia a todos los eventos a `CCustomTransition`una clase derivada, cuyo puntero se pasa al constructor de .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CUIAnimationCallbackBase`

`CUIAnimationInterpolatorBase`

`CInterpolatorBase`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="cinterpolatorbasecinterpolatorbase"></a><a name="cinterpolatorbase"></a>CInterpolatorBase::CInterpolatorBase

Construye el cInterpolatorBase objeto.

```
CInterpolatorBase();
```

## <a name="cinterpolatorbasecreateinstance"></a><a name="createinstance"></a>CInterpolatorBase::CreateInstance

Crea una instancia de CInterpolatorBase y almacena un puntero al interpolador personalizado, que controlará los eventos.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>Parámetros

*pInterpolator*<br/>
Un puntero al interpolador personalizado.

*ppHandler*<br/>
Salida. Contiene un puntero a la instancia de CInterpolatorBase cuando se devuelve la función.

### <a name="return-value"></a>Valor devuelto

## <a name="cinterpolatorbasegetdependencies"></a><a name="getdependencies"></a>CInterpolatorBase::GetDependencies

Obtiene las dependencias del interpolador.

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Parámetros

*initialValueDependencies*<br/>
Salida. Aspectos del interpolador que dependen del valor inicial pasado a SetInitialValueAndVelocity.

*initialVelocityDependencies*<br/>
Salida. Aspectos del interpolador que dependen de la velocidad inicial pasada a SetInitialValueAndVelocity.

*durationDependencies*<br/>
Salida. Aspectos del interpolador que dependen de la duración pasada a SetDuration.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. Devuelve E_FAIL si CCustomInterpolator no está establecido o la implementación personalizada devuelve FALSE desde el GetDependencies método.

## <a name="cinterpolatorbasegetduration"></a><a name="getduration"></a>CInterpolatorBase::GetDuration

Obtiene la duración del interpolador.

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Parámetros

*duration*<br/>
Salida. La duración de la transición, en segundos.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. Devuelve E_FAIL si CCustomInterpolator no está establecido o la implementación personalizada devuelve FALSE desde el GetDuration método.

## <a name="cinterpolatorbasegetfinalvalue"></a><a name="getfinalvalue"></a>CInterpolatorBase::GetFinalValue

Obtiene el valor final al que conduce el interpolador.

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>Parámetros

*value*<br/>
Salida. El valor final de una variable al final de la transición.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. Devuelve E_FAIL si CCustomInterpolator no está establecido o la implementación personalizada devuelve FALSE desde el GetFinalValue método.

## <a name="cinterpolatorbaseinterpolatevalue"></a><a name="interpolatevalue"></a>CInterpolatorBase::InterpolateValue

Interpola el valor en un desplazamiento determinado

```
IFACEMETHOD(InterpolateValue)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* value);
```

### <a name="parameters"></a>Parámetros

*offset*<br/>
El desplazamiento desde el inicio de la transición. El desplazamiento siempre es mayor o igual que cero y menor que la duración de la transición. No se llama a este método si la duración de la transición es cero.

*value*<br/>
Salida. El valor interpolado.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. Devuelve E_FAIL si CCustomInterpolator no está establecido o la implementación personalizada devuelve FALSE desde el InterpolateValue método.

## <a name="cinterpolatorbaseinterpolatevelocity"></a><a name="interpolatevelocity"></a>CInterpolatorBase::InterpolateVelocity

Interpola la velocidad a un desplazamiento determinado

```
IFACEMETHOD(InterpolateVelocity)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* velocity);
```

### <a name="parameters"></a>Parámetros

*offset*<br/>
El desplazamiento desde el inicio de la transición. El desplazamiento siempre es mayor o igual que cero y menor o igual que la duración de la transición. No se llama a este método si la duración de la transición es cero.

*velocity*<br/>
Salida. La velocidad de la variable en el desplazamiento.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. Devuelve E_FAIL si CCustomInterpolator no está establecido o la implementación personalizada devuelve FALSE desde el Método InterpolateVelocity.

## <a name="cinterpolatorbasesetcustominterpolator"></a><a name="setcustominterpolator"></a>CInterpolatorBase::SetCustomInterpolator

Almacena un puntero al interpolador personalizado, que controlará los eventos.

```cpp
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Parámetros

*pInterpolator*<br/>
Un puntero al interpolador personalizado.

## <a name="cinterpolatorbasesetduration"></a><a name="setduration"></a>CInterpolatorBase::SetDuration

Establece la duración del interpolador

```
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parámetros

*duration*<br/>
La duración de la transición.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. Devuelve E_FAIL si CCustomInterpolator no está establecido o la implementación personalizada devuelve FALSE desde el SetDuration método.

## <a name="cinterpolatorbasesetinitialvalueandvelocity"></a><a name="setinitialvalueandvelocity"></a>CInterpolatorBase::SetInitialValueAndVelocity

Establece el valor inicial y la velocidad del interpolador.

```
IFACEMETHOD(SetInitialValueAndVelocity)(
    __in DOUBLE initialValue,
    __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parámetros

*initialValue*<br/>
El valor de la variable al inicio de la transición.

*initialVelocity*<br/>
La velocidad de la variable al inicio de la transición.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. Devuelve E_FAIL si CCustomInterpolator no está establecido o la implementación personalizada devuelve FALSE desde el SetInitialValueAndVelocity método.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
