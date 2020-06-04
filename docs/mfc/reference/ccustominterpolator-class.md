---
title: Clase CCustomInterpolator
ms.date: 11/04/2016
f1_keywords:
- CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDependencies
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetFinalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::Init
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetInitialValueAndVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_duration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_finalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialVelocity
helpviewer_keywords:
- CCustomInterpolator [MFC], CCustomInterpolator
- CCustomInterpolator [MFC], GetDependencies
- CCustomInterpolator [MFC], GetDuration
- CCustomInterpolator [MFC], GetFinalValue
- CCustomInterpolator [MFC], Init
- CCustomInterpolator [MFC], InterpolateValue
- CCustomInterpolator [MFC], InterpolateVelocity
- CCustomInterpolator [MFC], SetDuration
- CCustomInterpolator [MFC], SetInitialValueAndVelocity
- CCustomInterpolator [MFC], m_currentValue
- CCustomInterpolator [MFC], m_currentVelocity
- CCustomInterpolator [MFC], m_duration
- CCustomInterpolator [MFC], m_finalValue
- CCustomInterpolator [MFC], m_initialValue
- CCustomInterpolator [MFC], m_initialVelocity
ms.assetid: 28d85595-989a-40a3-b003-e0e38437a94d
ms.openlocfilehash: 00ce0661fa3fbde714a7299ecbbd54df7c9bcc36
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749160"
---
# <a name="ccustominterpolator-class"></a>Clase CCustomInterpolator

Implementa un interpolador básico.

## <a name="syntax"></a>Sintaxis

```
class CCustomInterpolator;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCustomInterpolator::CCustomInterpolator](#ccustominterpolator)|Sobrecargado. Construye un objeto interpolador personalizado e inicializa la duración y la velocidad de los valores especificados.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCustomInterpolator::GetDependencies](#getdependencies)|Obtiene las dependencias del interpolador.|
|[CCustomInterpolator::GetDuration](#getduration)|Obtiene la duración del interpolador.|
|[CCustomInterpolator::GetFinalValue](#getfinalvalue)|Obtiene el valor final al que conduce el interpolador.|
|[CCustomInterpolator::Init](#init)|Inicializa la duración y el valor final.|
|[CCustomInterpolator::InterpolateValue](#interpolatevalue)|Interpola el valor en un desplazamiento determinado.|
|[CCustomInterpolator::InterpolateVelocity](#interpolatevelocity)|Interpola la velocidad a un desplazamiento determinado|
|[CCustomInterpolator::SetDuration](#setduration)|Establece la duración del interpolador.|
|[CCustomInterpolator::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Establece el valor inicial y la velocidad del interpolador.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CCustomInterpolator::m_currentValue](#m_currentvalue)|El valor interpolado.|
|[CCustomInterpolator::m_currentVelocity](#m_currentvelocity)|La velocidad interpolada.|
|[CCustomInterpolator::m_duration](#m_duration)|La duración de la transición.|
|[CCustomInterpolator::m_finalValue](#m_finalvalue)|El valor final de una variable al final de la transición.|
|[CCustomInterpolator::m_initialValue](#m_initialvalue)|El valor de la variable al inicio de la transición.|
|[CCustomInterpolator::m_initialVelocity](#m_initialvelocity)|La velocidad de la variable al inicio de la transición.|

## <a name="remarks"></a>Observaciones

Derive una clase de CCustomInterpolator e invalide todos los métodos necesarios para implementar un algoritmo de interpolación personalizado. Un puntero a esta clase debe pasarse como parámetro a CCustomTransition.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CCustomInterpolator`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="ccustominterpolatorccustominterpolator"></a><a name="ccustominterpolator"></a>CCustomInterpolator::CCustomInterpolator

Construye un objeto interpolador personalizado y establece todos los valores en el valor predeterminado 0.

```
CCustomInterpolator();

CCustomInterpolator(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>Parámetros

*duration*<br/>
La duración de la transición.

*finalValue*

### <a name="remarks"></a>Observaciones

Utilice CCustomInterpolator::Init para inicializar la duración y el valor final más adelante en el código.

## <a name="ccustominterpolatorgetdependencies"></a><a name="getdependencies"></a>CCustomInterpolator::GetDependencies

Obtiene las dependencias del interpolador.

```
virtual BOOL GetDependencies(
    UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Parámetros

*initialValueDependencies*<br/>
Salida. Aspectos del interpolador que dependen del valor inicial pasado a SetInitialValueAndVelocity.

*initialVelocityDependencies*<br/>
Salida. Aspectos del interpolador que dependen de la velocidad inicial pasada a SetInitialValueAndVelocity.

*durationDependencies*<br/>
Salida. Aspectos del interpolador que dependen de la duración pasada a SetDuration.

### <a name="return-value"></a>Valor devuelto

La implementación básica siempre devuelve TRUE. Devuelve FALSE de la implementación invalidada si desea producir un error en el evento.

## <a name="ccustominterpolatorgetduration"></a><a name="getduration"></a>CCustomInterpolator::GetDuration

Obtiene la duración del interpolador.

```
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Parámetros

*duration*<br/>
Salida. La duración de la transición, en segundos.

### <a name="return-value"></a>Valor devuelto

La implementación básica siempre devuelve TRUE. Devuelve FALSE de la implementación invalidada si desea producir un error en el evento.

## <a name="ccustominterpolatorgetfinalvalue"></a><a name="getfinalvalue"></a>CCustomInterpolator::GetFinalValue

Obtiene el valor final al que conduce el interpolador.

```
virtual BOOL GetFinalValue(DOUBLE* value);
```

### <a name="parameters"></a>Parámetros

*value*<br/>
Salida. El valor final de una variable al final de la transición.

### <a name="return-value"></a>Valor devuelto

La implementación básica siempre devuelve TRUE. Devuelve FALSE de la implementación invalidada si desea producir un error en el evento.

## <a name="ccustominterpolatorinit"></a><a name="init"></a>CCustomInterpolator::Init

Inicializa la duración y el valor final.

```cpp
void Init(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>Parámetros

*duration*<br/>
La duración de la transición.

*finalValue*<br/>
El valor final de una variable al final de la transición.

## <a name="ccustominterpolatorinterpolatevalue"></a><a name="interpolatevalue"></a>CCustomInterpolator::InterpolateValue

Interpola el valor en un desplazamiento determinado.

```
virtual BOOL InterpolateValue(
    UI_ANIMATION_SECONDS */,
    DOUBLE* value);
```

### <a name="parameters"></a>Parámetros

*value*<br/>
Salida. El valor interpolado.

### <a name="return-value"></a>Valor devuelto

La implementación básica siempre devuelve TRUE. Devuelve FALSE de la implementación invalidada si desea producir un error en el evento.

## <a name="ccustominterpolatorinterpolatevelocity"></a><a name="interpolatevelocity"></a>CCustomInterpolator::InterpolateVelocity

Interpola la velocidad a un desplazamiento determinado

```
virtual BOOL InterpolateVelocity(
    UI_ANIMATION_SECONDS */,
    DOUBLE* velocity);
```

### <a name="parameters"></a>Parámetros

*velocity*<br/>
Salida. La velocidad de la variable en el desplazamiento.

### <a name="return-value"></a>Valor devuelto

La implementación básica siempre devuelve TRUE. Devuelve FALSE de la implementación invalidada si desea producir un error en el evento.

## <a name="ccustominterpolatorm_currentvalue"></a><a name="m_currentvalue"></a>CCustomInterpolator::m_currentValue

El valor interpolado.

```
DOUBLE m_currentValue;
```

## <a name="ccustominterpolatorm_currentvelocity"></a><a name="m_currentvelocity"></a>CCustomInterpolator::m_currentVelocity

La velocidad interpolada.

```
DOUBLE m_currentVelocity;
```

## <a name="ccustominterpolatorm_duration"></a><a name="m_duration"></a>CCustomInterpolator::m_duration

La duración de la transición.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="ccustominterpolatorm_finalvalue"></a><a name="m_finalvalue"></a>CCustomInterpolator::m_finalValue

El valor final de una variable al final de la transición.

```
DOUBLE m_finalValue;
```

## <a name="ccustominterpolatorm_initialvalue"></a><a name="m_initialvalue"></a>CCustomInterpolator::m_initialValue

El valor de la variable al inicio de la transición.

```
DOUBLE m_initialValue;
```

## <a name="ccustominterpolatorm_initialvelocity"></a><a name="m_initialvelocity"></a>CCustomInterpolator::m_initialVelocity

La velocidad de la variable al inicio de la transición.

```
DOUBLE m_initialVelocity;
```

## <a name="ccustominterpolatorsetduration"></a><a name="setduration"></a>CCustomInterpolator::SetDuration

Establece la duración del interpolador.

```
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parámetros

*duration*<br/>
La duración de la transición.

### <a name="return-value"></a>Valor devuelto

La implementación básica siempre devuelve TRUE. Devuelve FALSE de la implementación invalidada si desea producir un error en el evento.

## <a name="ccustominterpolatorsetinitialvalueandvelocity"></a><a name="setinitialvalueandvelocity"></a>CCustomInterpolator::SetInitialValueAndVelocity

Establece el valor inicial y la velocidad del interpolador.

```
virtual BOOL SetInitialValueAndVelocity(
    DOUBLE initialValue,
    DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parámetros

*initialValue*<br/>
El valor de la variable al inicio de la transición.

*initialVelocity*<br/>
La velocidad de la variable al inicio de la transición.

### <a name="return-value"></a>Valor devuelto

La implementación básica siempre devuelve TRUE. Devuelve FALSE de la implementación invalidada si desea producir un error en el evento.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
