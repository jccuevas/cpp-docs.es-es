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
ms.openlocfilehash: d1fc675b1014ab9a099e8310b52b7458f2bff65f
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916196"
---
# <a name="cinterpolatorbase-class"></a>Clase CInterpolatorBase

Implementa una devolución de llamada, a la que llama la API de animación cuando tiene que calcular un nuevo valor de una variable de animación.

## <a name="syntax"></a>Sintaxis

```
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|Construye el `CInterpolatorBase` objeto.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CInterpolatorBase::CreateInstance](#createinstance)|Crea una instancia de `CInterpolatorBase` y almacena un puntero a un interpolador personalizado, que controlará los eventos.|
|[CInterpolatorBase::GetDependencies](#getdependencies)|Obtiene las dependencias del interpolador. (Invalida `CUIAnimationInterpolatorBase::GetDependencies`).|
|[CInterpolatorBase::GetDuration](#getduration)|Obtiene la duración del interpolador. (Invalida `CUIAnimationInterpolatorBase::GetDuration`).|
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|Obtiene el valor final al que el interpolador conduce. (Invalida `CUIAnimationInterpolatorBase::GetFinalValue`).|
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|Interpola el valor en un desplazamiento determinado (invalida `CUIAnimationInterpolatorBase::InterpolateValue`).|
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|Interpola la velocidad en un desplazamiento determinado (invalida `CUIAnimationInterpolatorBase::InterpolateVelocity`).|
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|Almacena un puntero a un interpolador personalizado, que controlará los eventos.|
|[CInterpolatorBase::SetDuration](#setduration)|Establece la duración del interpolador (invalida `CUIAnimationInterpolatorBase::SetDuration`).|
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Establece el valor inicial y la velocidad del interpolador. (Invalida `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`).|

## <a name="remarks"></a>Comentarios

Este controlador se crea y se pasa `IUIAnimationTransitionFactory::CreateTransition` a cuando `CCustomTransition` se crea un objeto como parte del proceso de inicialización de animación ( `CAnimationController::AnimateGroup`Iniciado por). Normalmente no es necesario usar esta clase directamente, sino que solo enrutará todos los eventos `CCustomInterpolator`a una clase derivada de, cuyo puntero se pasa al `CCustomTransition`constructor de.

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

Crea una instancia de CInterpolatorBase y almacena un puntero a un interpolador personalizado, que controlará los eventos.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>Parámetros

*pInterpolator*<br/>
Un puntero a un interpolador personalizado.

*ppHandler*<br/>
Genere. Contiene un puntero a una instancia de CInterpolatorBase cuando la función devuelve.

### <a name="return-value"></a>Valor devuelto

##  <a name="getdependencies"></a>CInterpolatorBase::GetDependencies

Obtiene las dependencias del interpolador.

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Parámetros

*initialValueDependencies*<br/>
Genere. Aspectos del interpolador que dependen del valor inicial pasado a SetInitialValueAndVelocity.

*initialVelocityDependencies*<br/>
Genere. Aspectos del interpolador que dependen de la velocidad inicial pasada a SetInitialValueAndVelocity.

*durationDependencies*<br/>
Genere. Aspectos del interpolador que dependen de la duración pasada a SetDuration.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, Devuelve S_OK. Devuelve E_FAIL si CCustomInterpolator no está establecido o la implementación personalizada devuelve FALSE desde el método GetDependencies.

##  <a name="getduration"></a>  CInterpolatorBase::GetDuration

Obtiene la duración del interpolador.

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Parámetros

*Duration*<br/>
Genere. La duración de la transición, en segundos.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, Devuelve S_OK. Devuelve E_FAIL si CCustomInterpolator no está establecido o la implementación personalizada devuelve FALSE desde el método GetDuration.

##  <a name="getfinalvalue"></a>  CInterpolatorBase::GetFinalValue

Obtiene el valor final al que el interpolador conduce.

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>Parámetros

*value*<br/>
Genere. Valor final de una variable al final de la transición.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, Devuelve S_OK. Devuelve E_FAIL si CCustomInterpolator no está establecido o la implementación personalizada devuelve FALSE desde el método GetFinalValue.

##  <a name="interpolatevalue"></a>  CInterpolatorBase::InterpolateValue

Interpola el valor en un desplazamiento determinado.

```
IFACEMETHOD(InterpolateValue)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* value);
```

### <a name="parameters"></a>Parámetros

*offset*<br/>
Desplazamiento desde el inicio de la transición. El desplazamiento siempre es mayor o igual que cero y menor que la duración de la transición. No se llama a este método si la duración de la transición es cero.

*value*<br/>
Genere. Valor interpolado.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, Devuelve S_OK. Devuelve E_FAIL si CCustomInterpolator no está establecido o la implementación personalizada devuelve FALSE desde el método InterpolateValue.

##  <a name="interpolatevelocity"></a>  CInterpolatorBase::InterpolateVelocity

Interpola la velocidad en un desplazamiento determinado.

```
IFACEMETHOD(InterpolateVelocity)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* velocity);
```

### <a name="parameters"></a>Parámetros

*offset*<br/>
Desplazamiento desde el inicio de la transición. El desplazamiento siempre es mayor o igual que cero y menor o igual que la duración de la transición. No se llama a este método si la duración de la transición es cero.

*velocity*<br/>
Genere. Velocidad de la variable en el desplazamiento.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, Devuelve S_OK. Devuelve E_FAIL si CCustomInterpolator no está establecido o la implementación personalizada devuelve FALSE desde el método InterpolateVelocity.

##  <a name="setcustominterpolator"></a>  CInterpolatorBase::SetCustomInterpolator

Almacena un puntero a un interpolador personalizado, que controlará los eventos.

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

*Duration*<br/>
La duración de la transición.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, Devuelve S_OK. Devuelve E_FAIL si CCustomInterpolator no está establecido o la implementación personalizada devuelve FALSE desde el método SetDuration.

##  <a name="setinitialvalueandvelocity"></a>  CInterpolatorBase::SetInitialValueAndVelocity

Establece el valor inicial y la velocidad del interpolador.

```
IFACEMETHOD(SetInitialValueAndVelocity)(
    __in DOUBLE initialValue,
    __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parámetros

*initialValue*<br/>
Valor de la variable al principio de la transición.

*initialVelocity*<br/>
Velocidad de la variable al principio de la transición.

### <a name="return-value"></a>Valor devuelto

Si el método se ejecuta correctamente, Devuelve S_OK. Devuelve E_FAIL si CCustomInterpolator no está establecido o la implementación personalizada devuelve FALSE desde el método SetInitialValueAndVelocity.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
