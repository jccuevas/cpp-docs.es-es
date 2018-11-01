---
title: Clase CSinusoidalTransitionFromRange
ms.date: 11/04/2016
f1_keywords:
- CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::Create
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMaximumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMinimumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_duration
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_period
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_slope
helpviewer_keywords:
- CSinusoidalTransitionFromRange [MFC], CSinusoidalTransitionFromRange
- CSinusoidalTransitionFromRange [MFC], Create
- CSinusoidalTransitionFromRange [MFC], m_dblMaximumValue
- CSinusoidalTransitionFromRange [MFC], m_dblMinimumValue
- CSinusoidalTransitionFromRange [MFC], m_duration
- CSinusoidalTransitionFromRange [MFC], m_period
- CSinusoidalTransitionFromRange [MFC], m_slope
ms.assetid: 8b66a729-5f10-431a-b055-e3600d0065da
ms.openlocfilehash: 20e910dfa34e90af2c8a2765947ad85a2465c596
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477589"
---
# <a name="csinusoidaltransitionfromrange-class"></a>Clase CSinusoidalTransitionFromRange

Encapsula una transición de intervalo sinusoidal que tiene un intervalo determinado de oscilación.

## <a name="syntax"></a>Sintaxis

```
class CSinusoidalTransitionFromRange : public CBaseTransition;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange](#csinusoidaltransitionfromrange)|Construye un objeto de transición.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSinusoidalTransitionFromRange::Create](#create)|Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado. (Invalida [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CSinusoidalTransitionFromRange::m_dblMaximumValue](#m_dblmaximumvalue)|El valor de la variable de animación en un pico de la onda sinusoidal.|
|[CSinusoidalTransitionFromRange::m_dblMinimumValue](#m_dblminimumvalue)|El valor de la variable de animación en un Valle de la onda sinusoidal.|
|[CSinusoidalTransitionFromRange::m_duration](#m_duration)|La duración de la transición.|
|[CSinusoidalTransitionFromRange::m_period](#m_period)|El período de oscilación de la onda sinusoidal en segundos.|
|[CSinusoidalTransitionFromRange::m_slope](#m_slope)|La pendiente del principio de la transición.|

## <a name="remarks"></a>Comentarios

El valor de la variable de animación fluctúa entre los valores mínimos y máximo especificados en toda la duración de una transición de intervalo sinusoidal. El parámetro "pendiente" se usa para eliminar la ambigüedad entre las dos ondas de seno posible especificadas por los otros parámetros. Dado que todas las transiciones se borran automáticamente, se recomienda asignada a ellos mediante el operador nuevo. El objeto COM IUIAnimationTransition encapsulado se crea por CAnimationController::AnimateGroup, hasta que es NULL. Cambiar las variables de miembro después de la creación de este objeto COM no tiene ningún efecto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CSinusoidalTransitionFromRange](../../mfc/reference/csinusoidaltransitionfromrange-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="create"></a>  CSinusoidalTransitionFromRange::Create

Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parámetros

*pLibrary*<br/>
Un puntero a la biblioteca de transición, que es responsable de la creación de transiciones estándares.

### <a name="return-value"></a>Valor devuelto

TRUE si la transición se crea correctamente; en caso contrario, FALSE.

##  <a name="csinusoidaltransitionfromrange"></a>  CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange

Construye un objeto de transición.

```
CSinusoidalTransitionFromRange(
    UI_ANIMATION_SECONDS duration,
    DOUBLE dblMinimumValue,
    DOUBLE dblMaximumValue,
    UI_ANIMATION_SECONDS period,
    UI_ANIMATION_SLOPE slope);
```

### <a name="parameters"></a>Parámetros

*Duración*<br/>
La duración de la transición.

*dblMinimumValue*<br/>
El valor de la variable de animación en un Valle de la onda sinusoidal.

*dblMaximumValue*<br/>
El valor de la variable de animación en un pico de la onda sinusoidal.

*Período*<br/>
El período de oscilación de la onda sinusoidal en segundos.

*pendiente*<br/>
La pendiente del principio de la transición.

##  <a name="m_dblmaximumvalue"></a>  CSinusoidalTransitionFromRange::m_dblMaximumValue

El valor de la variable de animación en un pico de la onda sinusoidal.

```
DOUBLE m_dblMaximumValue;
```

##  <a name="m_dblminimumvalue"></a>  CSinusoidalTransitionFromRange::m_dblMinimumValue

El valor de la variable de animación en un Valle de la onda sinusoidal.

```
DOUBLE m_dblMinimumValue;
```

##  <a name="m_duration"></a>  CSinusoidalTransitionFromRange::m_duration

La duración de la transición.

```
UI_ANIMATION_SECONDS m_duration;
```

##  <a name="m_period"></a>  CSinusoidalTransitionFromRange::m_period

El período de oscilación de la onda sinusoidal en segundos.

```
UI_ANIMATION_SECONDS m_period;
```

##  <a name="m_slope"></a>  CSinusoidalTransitionFromRange::m_slope

La pendiente del principio de la transición.

```
UI_ANIMATION_SLOPE m_slope;
```

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
