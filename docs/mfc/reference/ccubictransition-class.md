---
title: Clase CCubicTransition
ms.date: 11/04/2016
f1_keywords:
- CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::Create
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalVelocity
- AFXANIMATIONCONTROLLER/CCubicTransition::m_duration
helpviewer_keywords:
- CCubicTransition [MFC], CCubicTransition
- CCubicTransition [MFC], Create
- CCubicTransition [MFC], m_dblFinalValue
- CCubicTransition [MFC], m_dblFinalVelocity
- CCubicTransition [MFC], m_duration
ms.assetid: 4fc30e9c-160c-45e1-bdbe-51adf8fee9c5
ms.openlocfilehash: de376503111dab157ca34744863fb1d35a58785e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369347"
---
# <a name="ccubictransition-class"></a>Clase CCubicTransition

Encapsula una transición cúbica.

## <a name="syntax"></a>Sintaxis

```
class CCubicTransition : public CBaseTransition;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCubicTransition::CCubicTransition](#ccubictransition)|Construye un objeto de transición e inicializa sus parámetros.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCubicTransition::Create](#create)|Llama a la biblioteca de transición para crear un objeto COM de transición encapsulado. (Reemplaza [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCubicTransition::m_dblFinalValue](#m_dblfinalvalue)|El valor de la variable de animación al final de la transición.|
|[CCubicTransition::m_dblFinalVelocity](#m_dblfinalvelocity)|La velocidad de la variable al final de la transición.|
|[CCubicTransition::m_duration](#m_duration)|La duración de la transición.|

## <a name="remarks"></a>Observaciones

Durante una transición cúbica, el valor de la variable de animación cambia de su valor inicial a un valor final especificado durante la duración de la transición, terminando a una velocidad especificada. Dado que todas las transiciones se borran automáticamente, se recomienda asignarlas mediante el operador new. CAnimationController::AnimateGroup crea el objeto COM IUIAnimationTransition encapsulado, hasta que es NULL. Cambiar las variables miembro después de la creación de este objeto COM no tiene ningún efecto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CCubicTransition`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="ccubictransitionccubictransition"></a><a name="ccubictransition"></a>CCubicTransition::CCubicTransition

Construye un objeto de transición e inicializa sus parámetros.

```
CCubicTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE finalVelocity);
```

### <a name="parameters"></a>Parámetros

*duration*<br/>
La duración de la transición.

*finalValue*<br/>
El valor de la variable de animación al final de la transición.

*finalVelocity*<br/>
La velocidad de la variable al final de la transición.

## <a name="ccubictransitioncreate"></a><a name="create"></a>CCubicTransition::Create

Llama a la biblioteca de transición para crear un objeto COM de transición encapsulado.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parámetros

*pLibrary*<br/>
Puntero a una [interfaz IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), que define una biblioteca de transiciones estándar.

### <a name="return-value"></a>Valor devuelto

TRUESi la transición se crea correctamente; de lo contrario FALSO.

## <a name="ccubictransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>CCubicTransition::m_dblFinalValue

El valor de la variable de animación al final de la transición.

```
DOUBLE m_dblFinalValue;
```

## <a name="ccubictransitionm_dblfinalvelocity"></a><a name="m_dblfinalvelocity"></a>CCubicTransition::m_dblFinalVelocity

La velocidad de la variable al final de la transición.

```
DOUBLE m_dblFinalVelocity;
```

## <a name="ccubictransitionm_duration"></a><a name="m_duration"></a>CCubicTransition::m_duration

La duración de la transición.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
