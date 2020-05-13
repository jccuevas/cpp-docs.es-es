---
title: Clase CLinearTransition
ms.date: 11/04/2016
f1_keywords:
- CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::Create
- AFXANIMATIONCONTROLLER/CLinearTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransition::m_duration
helpviewer_keywords:
- CLinearTransition [MFC], CLinearTransition
- CLinearTransition [MFC], Create
- CLinearTransition [MFC], m_dblFinalValue
- CLinearTransition [MFC], m_duration
ms.assetid: 7fcb2dba-beb8-4933-9f5d-3b7fb1585ef0
ms.openlocfilehash: 1d3bc50255dae93bfa80e8212c2349db66db4eb6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372275"
---
# <a name="clineartransition-class"></a>Clase CLinearTransition

Encapsula una transición lineal.

## <a name="syntax"></a>Sintaxis

```
class CLinearTransition : public CBaseTransition;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CLinearTransition::CLinearTransition](#clineartransition)|Construye un objeto de transición lineal y lo inicializa con duración y valor final.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CLinearTransition::Create](#create)|Llama a la biblioteca de transición para crear un objeto COM de transición encapsulado. (Reemplaza [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CLinearTransition::m_dblFinalValue](#m_dblfinalvalue)|El valor de la variable de animación al final de la transición.|
|[CLinearTransition::m_duration](#m_duration)|La duración de la transición.|

## <a name="remarks"></a>Observaciones

Durante una transición lineal, el valor de la variable de animación pasa linealmente de su valor inicial a un valor final especificado. Dado que todas las transiciones se borran automáticamente, se recomienda asignarlas mediante el operador new. CAnimationController::AnimateGroup crea el objeto COM IUIAnimationTransition encapsulado, hasta que es NULL. Cambiar las variables miembro después de la creación de este objeto COM no tiene ningún efecto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CLinearTransition](../../mfc/reference/clineartransition-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="clineartransitionclineartransition"></a><a name="clineartransition"></a>CLinearTransition::CLinearTransition

Construye un objeto de transición lineal y lo inicializa con duración y valor final.

```
CLinearTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>Parámetros

*duration*<br/>
La duración de la transición.

*dblFinalValue*<br/>
El valor de la variable de animación al final de la transición.

## <a name="clineartransitioncreate"></a><a name="create"></a>CLinearTransition::Create

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

## <a name="clineartransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>CLinearTransition::m_dblFinalValue

El valor de la variable de animación al final de la transición.

```
DOUBLE m_dblFinalValue;
```

## <a name="clineartransitionm_duration"></a><a name="m_duration"></a>CLinearTransition::m_duration

La duración de la transición.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
