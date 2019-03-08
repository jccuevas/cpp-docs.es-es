---
title: Clase CAccelerateDecelerateTransition
ms.date: 11/04/2016
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
ms.openlocfilehash: dbebe794ba76ae4abd3d1e3ea6bc8ee31bc3007f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278865"
---
# <a name="cacceleratedeceleratetransition-class"></a>Clase CAccelerateDecelerateTransition

Implementa una transición que aumenta/reduce la velocidad.

## <a name="syntax"></a>Sintaxis

```
class CAccelerateDecelerateTransition : public CBaseTransition;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|Construye un objeto de transición.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAccelerateDecelerateTransition::Create](#create)|Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado. (Invalida [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CAccelerateDecelerateTransition::m_accelerationRatio](#m_accelerationratio)|La proporción del tiempo transcurrido acelerando la duración.|
|[CAccelerateDecelerateTransition::m_decelerationRatio](#m_decelerationratio)|La proporción del tiempo empleado en decelerar a la duración.|
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|La duración de la transición.|
|[CAccelerateDecelerateTransition::m_finalValue](#m_finalvalue)|El valor de la variable de animación al final de la transición.|

## <a name="remarks"></a>Comentarios

Durante una-reducir la velocidad de transición, la variable de animación acelera y, a continuación, se ralentiza a través de la duración de la transición, finalizando en un valor especificado. Puede controlar la rapidez con la variable acelera y disminuye la velocidad de forma independiente, mediante la especificación de aceleración diferentes y proporciones de desaceleración. Cuando la velocidad inicial es cero, la proporción de aceleración es la fracción de la duración de la variable pasará la aceleración; lo mismo con la proporción de desaceleración. Si la velocidad inicial es distinto de cero, es la fracción del tiempo entre la velocidad llegue a cero y el final de la transición. La proporción de aceleración y la desaceleración deberían sumar un máximo de 1.0. Dado que todas las transiciones se borran automáticamente, se recomienda asignada a ellos mediante el operador nuevo. El objeto COM IUIAnimationTransition encapsulado se crea por CAnimationController::AnimateGroup, hasta que es NULL. Cambiar las variables de miembro después de la creación de este objeto COM no tiene ningún efecto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CAccelerateDecelerateTransition`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="cacceleratedeceleratetransition"></a>  CAccelerateDecelerateTransition::CAccelerateDecelerateTransition

Construye un objeto de transición.

```
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE accelerationRatio = 0.3,
    DOUBLE decelerationRatio = 0.3);
```

### <a name="parameters"></a>Parámetros

*Duración*<br/>
La duración de la transición.

*finalValue*<br/>
El valor de la variable de animación al final de la transición.

*accelerationRatio*<br/>
La proporción del tiempo transcurrido acelerando la duración.

*decelerationRatio*<br/>
La proporción del tiempo empleado en decelerar a la duración.

##  <a name="create"></a>  CAccelerateDecelerateTransition::Create

Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* *\not used*\);
```

### <a name="parameters"></a>Parámetros

*pLibrary*<br/>
Un puntero a un [IUIAnimationTransitionLibrary interfaz](/windows/desktop/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), que define una biblioteca de transiciones estándares.

### <a name="return-value"></a>Valor devuelto

TRUE si la transición se crea correctamente; en caso contrario, FALSE.

##  <a name="m_accelerationratio"></a>  CAccelerateDecelerateTransition::m_accelerationRatio

La proporción del tiempo transcurrido acelerando la duración.

```
DOUBLE m_accelerationRatio;
```

##  <a name="m_decelerationratio"></a>  CAccelerateDecelerateTransition::m_decelerationRatio

La proporción del tiempo empleado en decelerar a la duración.

```
DOUBLE m_decelerationRatio;
```

##  <a name="m_duration"></a>  CAccelerateDecelerateTransition::m_duration

La duración de la transición.

```
UI_ANIMATION_SECONDS m_duration;
```

##  <a name="m_finalvalue"></a>  CAccelerateDecelerateTransition::m_finalValue

El valor de la variable de animación al final de la transición.

```
DOUBLE m_finalValue;
```

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
