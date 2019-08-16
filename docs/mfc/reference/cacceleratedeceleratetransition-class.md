---
title: Clase CAccelerateDecelerateTransition
ms.date: 11/04/2016
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
ms.openlocfilehash: 1e55e81b4d9b5c324f86bfd141b74d9faa362d94
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507736"
---
# <a name="cacceleratedeceleratetransition-class"></a>Clase CAccelerateDecelerateTransition

Implementa una transición que aumenta/reduce la velocidad.

## <a name="syntax"></a>Sintaxis

```
class CAccelerateDecelerateTransition : public CBaseTransition;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|Construye un objeto de transición.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAccelerateDecelerateTransition::Create](#create)|Llama a la biblioteca de transición para crear el objeto COM de transición encapsulada. (Invalida [CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create)).|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAccelerateDecelerateTransition::m_accelerationRatio](#m_accelerationratio)|La proporción del tiempo empleado en acelerar la duración.|
|[CAccelerateDecelerateTransition::m_decelerationRatio](#m_decelerationratio)|La proporción del tiempo empleado en disminuir la duración.|
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|La duración de la transición.|
|[CAccelerateDecelerateTransition::m_finalValue](#m_finalvalue)|Valor de la variable de animación al final de la transición.|

## <a name="remarks"></a>Comentarios

Durante una transición Celer-Decelerate, la variable de animación se acelera y después se ralentiza a lo largo de la transición, finalizando en un valor especificado. Puede controlar la rapidez con la que la variable se acelera y desacelera de forma independiente, especificando diferentes proporciones de aceleración y desaceleración. Cuando la velocidad inicial es cero, la relación de aceleración es la fracción de la duración que la variable va a acelerar. del mismo modo que la relación de desaceleración. Si la velocidad inicial es distinta de cero, es la fracción del tiempo entre la velocidad que llega a cero y el final de la transición. La relación de aceleración y la relación de desaceleración deben sumar un máximo de 1,0. Dado que todas las transiciones se borran automáticamente, se recomienda asignarlas mediante el operador new. CAnimationController:: AnimateGroup crea el objeto COM encapsulado IUIAnimationTransition, hasta que sea NULL. Cambiar las variables de miembro después de la creación de este objeto COM no tiene ningún efecto.

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

*Duration*<br/>
La duración de la transición.

*finalValue*<br/>
Valor de la variable de animación al final de la transición.

*accelerationRatio*<br/>
La proporción del tiempo empleado en acelerar la duración.

*decelerationRatio*<br/>
La proporción del tiempo empleado en disminuir la duración.

##  <a name="create"></a>  CAccelerateDecelerateTransition::Create

Llama a la biblioteca de transición para crear el objeto COM de transición encapsulada.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* *\not used*\);
```

### <a name="parameters"></a>Parámetros

*pLibrary*<br/>
Puntero a una [interfaz IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), que define una biblioteca de transiciones estándar.

### <a name="return-value"></a>Valor devuelto

TRUE si la transición se crea correctamente; en caso contrario, FALSE.

##  <a name="m_accelerationratio"></a>  CAccelerateDecelerateTransition::m_accelerationRatio

La proporción del tiempo empleado en acelerar la duración.

```
DOUBLE m_accelerationRatio;
```

##  <a name="m_decelerationratio"></a>  CAccelerateDecelerateTransition::m_decelerationRatio

La proporción del tiempo empleado en disminuir la duración.

```
DOUBLE m_decelerationRatio;
```

##  <a name="m_duration"></a>  CAccelerateDecelerateTransition::m_duration

La duración de la transición.

```
UI_ANIMATION_SECONDS m_duration;
```

##  <a name="m_finalvalue"></a>  CAccelerateDecelerateTransition::m_finalValue

Valor de la variable de animación al final de la transición.

```
DOUBLE m_finalValue;
```

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
