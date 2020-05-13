---
title: Clase CConstantTransition
ms.date: 11/04/2016
f1_keywords:
- CConstantTransition
- AFXANIMATIONCONTROLLER/CConstantTransition
- AFXANIMATIONCONTROLLER/CConstantTransition::CConstantTransition
- AFXANIMATIONCONTROLLER/CConstantTransition::Create
- AFXANIMATIONCONTROLLER/CConstantTransition::m_duration
helpviewer_keywords:
- CConstantTransition [MFC], CConstantTransition
- CConstantTransition [MFC], Create
- CConstantTransition [MFC], m_duration
ms.assetid: f6fa4780-a71b-4cd6-80aa-d4792ace36c2
ms.openlocfilehash: 0d5d92f02cc3b56268966f1cd79451578a5cc390
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369408"
---
# <a name="cconstanttransition-class"></a>Clase CConstantTransition

Encapsula una transición constante.

## <a name="syntax"></a>Sintaxis

```
class CConstantTransition : public CBaseTransition;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CConstantTransition::CConstantTransition](#cconstanttransition)|Construye un objeto de transición e inicializa su duración.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CConstantTransition::Create](#create)|Llama a la biblioteca de transición para crear un objeto COM de transición encapsulado. (Reemplaza [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CConstantTransition::m_duration](#m_duration)|La duración de la transición.|

## <a name="remarks"></a>Observaciones

Durante una transición constante, el valor de una variable de animación permanece en el valor inicial durante la duración de la transición. Dado que todas las transiciones se borran automáticamente, se recomienda asignarlas mediante el operador new. CAnimationController::AnimateGroup crea el objeto COM IUIAnimationTransition encapsulado, hasta que es NULL. Cambiar las variables miembro después de la creación de este objeto COM no tiene ningún efecto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CConstantTransition`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="cconstanttransitioncconstanttransition"></a><a name="cconstanttransition"></a>CConstantTransition::CConstantTransition

Construye un objeto de transición e inicializa su duración.

```
CConstantTransition (UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parámetros

*duration*<br/>
La duración de la transición.

## <a name="cconstanttransitioncreate"></a><a name="create"></a>CConstantTransition::Create

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

## <a name="cconstanttransitionm_duration"></a><a name="m_duration"></a>CConstantTransition::m_duration

La duración de la transición.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
