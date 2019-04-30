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
ms.openlocfilehash: 379aa5607e459ad8acfd99c5899315afb84ac4a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392666"
---
# <a name="cinterpolatorbase-class"></a>Clase CInterpolatorBase

Implementa una devolución de llamada, a la que llama la API de animación cuando tiene que calcular un nuevo valor de una variable de animación.

## <a name="syntax"></a>Sintaxis

```
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|Construye el `CInterpolatorBase` objeto.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CInterpolatorBase::CreateInstance](#createinstance)|Crea una instancia de `CInterpolatorBase` y almacena un puntero a interpolador personalizado, que se maneje los eventos.|
|[CInterpolatorBase::GetDependencies](#getdependencies)|Obtiene las dependencias del interpolador. (Invalida `CUIAnimationInterpolatorBase::GetDependencies`).|
|[CInterpolatorBase::GetDuration](#getduration)|Obtiene la duración del interpolador. (Invalida `CUIAnimationInterpolatorBase::GetDuration`).|
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|Obtiene el valor final al que lleva el interpolador. (Invalida `CUIAnimationInterpolatorBase::GetFinalValue`).|
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|Interpola el valor en un desplazamiento dado (invalidaciones `CUIAnimationInterpolatorBase::InterpolateValue`.)|
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|La velocidad en un desplazamiento dado se interpola (invalidaciones `CUIAnimationInterpolatorBase::InterpolateVelocity`.)|
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|Almacena un puntero a interpolador personalizado, que se maneje los eventos.|
|[CInterpolatorBase::SetDuration](#setduration)|Establece la duración del interpolador (invalidaciones `CUIAnimationInterpolatorBase::SetDuration`.)|
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Establece el valor inicial y la velocidad del interpolador. (Invalida `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`).|

## <a name="remarks"></a>Comentarios

Se crea y se pasa a este controlador `IUIAnimationTransitionFactory::CreateTransition` cuando un `CCustomTransition` se está creando el objeto como parte del proceso de inicialización de animación (iniciado por `CAnimationController::AnimateGroup`). Normalmente no es necesario usar esta clase directamente, solo enruta el todos los eventos en un `CCustomInterpolator`-clase derivada, cuyo puntero se pasa al constructor de `CCustomTransition`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CUIAnimationCallbackBase`

`CUIAnimationInterpolatorBase`

`CInterpolatorBase`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="cinterpolatorbase"></a>  CInterpolatorBase::CInterpolatorBase

Construye el objeto CInterpolatorBase.

```
CInterpolatorBase();
```

##  <a name="createinstance"></a>  CInterpolatorBase::CreateInstance

Crea una instancia de CInterpolatorBase y almacena un puntero a interpolador personalizado, que se maneje los eventos.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>Parámetros

*pInterpolator*<br/>
Un puntero a un interpolador personalizado.

*ppHandler*<br/>
Salida. Contiene un puntero a la instancia de CInterpolatorBase cuando la función devuelve.

### <a name="return-value"></a>Valor devuelto

##  <a name="getdependencies"></a>  CInterpolatorBase::GetDependencies

Obtiene las dependencias del interpolador.

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Parámetros

*initialValueDependencies*<br/>
Salida. Aspectos del interpolador que dependen del valor inicial que se pasan a SetInitialValueAndVelocity.

*initialVelocityDependencies*<br/>
Salida. Aspectos del interpolador que dependen de la velocidad inicial que se pasan a SetInitialValueAndVelocity.

*durationDependencies*<br/>
Salida. Aspectos del interpolador que dependen de la duración se pasan a SetDuration.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. Si no se ha establecido CCustomInterpolator o implementación personalizada, se devuelve FALSE desde el método GetDependencies devuelve E_FAIL.

##  <a name="getduration"></a>  CInterpolatorBase::GetDuration

Obtiene la duración del interpolador.

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Parámetros

*Duración*<br/>
Salida. La duración de la transición, en segundos.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. Si no se ha establecido CCustomInterpolator o implementación personalizada, se devuelve FALSE desde el método GetDuration devuelve E_FAIL.

##  <a name="getfinalvalue"></a>  CInterpolatorBase::GetFinalValue

Obtiene el valor final al que lleva el interpolador.

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>Parámetros

*value*<br/>
Salida. El valor final de una variable al final de la transición.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. Si no se ha establecido CCustomInterpolator o implementación personalizada, se devuelve FALSE desde el método GetFinalValue devuelve E_FAIL.

##  <a name="interpolatevalue"></a>  CInterpolatorBase::InterpolateValue

Interpola el valor en un desplazamiento dado

```
IFACEMETHOD(InterpolateValue)(
  __in UI_ANIMATION_SECONDS offset,
  __out DOUBLE* value);
```

### <a name="parameters"></a>Parámetros

*offset*<br/>
El desplazamiento desde el principio de la transición. El desplazamiento es siempre mayor o igual que cero y menor que la duración de la transición. No se llama a este método si la duración de la transición es cero.

*value*<br/>
Salida. El valor de interpolación.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. Si no se ha establecido CCustomInterpolator o implementación personalizada, se devuelve FALSE desde el método InterpolateValue devuelve E_FAIL.

##  <a name="interpolatevelocity"></a>  CInterpolatorBase::InterpolateVelocity

Interpola la velocidad en un desplazamiento dado

```
IFACEMETHOD(InterpolateVelocity)(
  __in UI_ANIMATION_SECONDS offset,
  __out DOUBLE* velocity);
```

### <a name="parameters"></a>Parámetros

*offset*<br/>
El desplazamiento desde el principio de la transición. El desplazamiento es siempre mayor o igual que cero y menor o igual que la duración de la transición. No se llama a este método si la duración de la transición es cero.

*velocity*<br/>
Salida. La velocidad de la variable en el desplazamiento.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. Si no se ha establecido CCustomInterpolator o implementación personalizada, se devuelve FALSE desde el método InterpolateVelocity devuelve E_FAIL.

##  <a name="setcustominterpolator"></a>  CInterpolatorBase::SetCustomInterpolator

Almacena un puntero a interpolador personalizado, que se maneje los eventos.

```
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Parámetros

*pInterpolator*<br/>
Un puntero a un interpolador personalizado.

##  <a name="setduration"></a>  CInterpolatorBase::SetDuration

Establece la duración del interpolador

```
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parámetros

*Duración*<br/>
La duración de la transición.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. Si no se ha establecido CCustomInterpolator o implementación personalizada, se devuelve FALSE desde el método SetDuration devuelve E_FAIL.

##  <a name="setinitialvalueandvelocity"></a>  CInterpolatorBase::SetInitialValueAndVelocity

Establece el valor inicial y la velocidad del interpolador.

```
IFACEMETHOD(SetInitialValueAndVelocity)(
  __in DOUBLE initialValue,
  __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parámetros

*initialValue*<br/>
El valor de la variable al principio de la transición.

*initialVelocity*<br/>
La velocidad de la variable al principio de la transición.

### <a name="return-value"></a>Valor devuelto

Si el método se realiza correctamente, devuelve S_OK. Si no se ha establecido CCustomInterpolator o implementación personalizada, se devuelve FALSE desde el método SetInitialValueAndVelocity devuelve E_FAIL.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
