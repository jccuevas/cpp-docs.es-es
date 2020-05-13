---
title: CAccelerateDecelerateTransition (clase)
ms.date: 11/04/2016
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
ms.openlocfilehash: 356ba30e6d9a638672d2c356676735ebfaed8f3e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371145"
---
# <a name="cacceleratedeceleratetransition-class"></a>CAccelerateDecelerateTransition (clase)

Implementa una transición que aumenta/reduce la velocidad.

## <a name="syntax"></a>Sintaxis

```
class CAccelerateDecelerateTransition : public CBaseTransition;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|Construye un objeto de transición.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAccelerateDecelerateTransition::Create](#create)|Llama a la biblioteca de transición para crear un objeto COM de transición encapsulado. (Reemplaza [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAccelerateDecelerateTransition::m_accelerationRatio](#m_accelerationratio)|La relación entre el tiempo empleado acelerando a la duración.|
|[CAccelerateDecelerateTransition::m_decelerationRatio](#m_decelerationratio)|La relación entre el tiempo dedicado a la desaceleración y la duración.|
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|La duración de la transición.|
|[CAccelerateDecelerateTransition::m_finalValue](#m_finalvalue)|El valor de la variable de animación al final de la transición.|

## <a name="remarks"></a>Observaciones

Durante una transición acelerada-desacelerada, la variable de animación se acelera y, a continuación, se ralentiza durante la duración de la transición, terminando en un valor especificado. Puede controlar la rapidez con la que la variable se acelera y desacelera de forma independiente, especificando diferentes relaciones de aceleración y desaceleración. Cuando la velocidad inicial es cero, la relación de aceleración es la fracción de la duración que la variable gastará acelerando; del mismo modo con la relación de desaceleración. Si la velocidad inicial es distinta de cero, es la fracción del tiempo entre la velocidad que alcanza cero y el final de la transición. La relación de aceleración y la relación de desaceleración deben sumar un máximo de 1,0. Dado que todas las transiciones se borran automáticamente, se recomienda asignarlas mediante el operador new. CAnimationController::AnimateGroup crea el objeto COM IUIAnimationTransition encapsulado, hasta que es NULL. Cambiar las variables miembro después de la creación de este objeto COM no tiene ningún efecto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CAccelerateDecelerateTransition`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="cacceleratedeceleratetransitioncacceleratedeceleratetransition"></a><a name="cacceleratedeceleratetransition"></a>CAccelerateDecelerateTransition::CAccelerateDecelerateTransition

Construye un objeto de transición.

```
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE accelerationRatio = 0.3,
    DOUBLE decelerationRatio = 0.3);
```

### <a name="parameters"></a>Parámetros

*duration*<br/>
La duración de la transición.

*finalValue*<br/>
El valor de la variable de animación al final de la transición.

*accelerationRatio*<br/>
La relación entre el tiempo empleado acelerando a la duración.

*desaceleraationRatio*<br/>
La relación entre el tiempo dedicado a la desaceleración y la duración.

## <a name="cacceleratedeceleratetransitioncreate"></a><a name="create"></a>CAccelerateDecelerateTransition::Create

Llama a la biblioteca de transición para crear un objeto COM de transición encapsulado.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* *\not used*\);
```

### <a name="parameters"></a>Parámetros

*pLibrary*<br/>
Puntero a una [interfaz IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), que define una biblioteca de transiciones estándar.

### <a name="return-value"></a>Valor devuelto

TRUESi la transición se crea correctamente; de lo contrario FALSO.

## <a name="cacceleratedeceleratetransitionm_accelerationratio"></a><a name="m_accelerationratio"></a>CAccelerateDecelerateTransition::m_accelerationRatio

La relación entre el tiempo empleado acelerando a la duración.

```
DOUBLE m_accelerationRatio;
```

## <a name="cacceleratedeceleratetransitionm_decelerationratio"></a><a name="m_decelerationratio"></a>CAccelerateDecelerateTransition::m_decelerationRatio

La relación entre el tiempo dedicado a la desaceleración y la duración.

```
DOUBLE m_decelerationRatio;
```

## <a name="cacceleratedeceleratetransitionm_duration"></a><a name="m_duration"></a>CAccelerateDecelerateTransition::m_duration

La duración de la transición.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="cacceleratedeceleratetransitionm_finalvalue"></a><a name="m_finalvalue"></a>CAccelerateDecelerateTransition::m_finalValue

El valor de la variable de animación al final de la transición.

```
DOUBLE m_finalValue;
```

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
