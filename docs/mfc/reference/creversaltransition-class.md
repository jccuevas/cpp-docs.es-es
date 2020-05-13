---
title: Clase CReversalTransition
ms.date: 11/04/2016
f1_keywords:
- CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::Create
- AFXANIMATIONCONTROLLER/CReversalTransition::m_duration
helpviewer_keywords:
- CReversalTransition [MFC], CReversalTransition
- CReversalTransition [MFC], Create
- CReversalTransition [MFC], m_duration
ms.assetid: e89516be-2d07-4885-95a8-fc278f46e3ad
ms.openlocfilehash: 73d12fb6bbaefcfac1437248ebe11f3a5c24c45b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368311"
---
# <a name="creversaltransition-class"></a>Clase CReversalTransition

Encapsula una transición de inversión.

## <a name="syntax"></a>Sintaxis

```
class CReversalTransition : public CBaseTransition;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CReversalTransition::CReversalTransition](#creversaltransition)|Construye un objeto de transición de inversión e inicializa su duración.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CReversalTransition::Create](#create)|Llama a la biblioteca de transición para crear un objeto COM de transición encapsulado. (Reemplaza [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CReversalTransition::m_duration](#m_duration)|La duración de la transición.|

## <a name="remarks"></a>Observaciones

Una transición de inversión cambia suavemente la dirección durante una duración determinada. El valor final será el mismo que el valor inicial y la velocidad final será el negativo de la velocidad inicial. Dado que todas las transiciones se borran automáticamente, se recomienda asignarlas mediante el operador new. CAnimationController::AnimateGroup crea el objeto COM IUIAnimationTransition encapsulado, hasta que es NULL. Cambiar las variables miembro después de la creación de este objeto COM no tiene ningún efecto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CReversalTransition](../../mfc/reference/creversaltransition-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="creversaltransitioncreate"></a><a name="create"></a>CReversalTransition::Create

Llama a la biblioteca de transición para crear un objeto COM de transición encapsulado.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parámetros

*pLibrary*<br/>
Un puntero a la biblioteca de transición, que es responsable de la creación de transiciones estándar.

### <a name="return-value"></a>Valor devuelto

TRUESi la transición se crea correctamente; de lo contrario FALSO.

## <a name="creversaltransitioncreversaltransition"></a><a name="creversaltransition"></a>CReversalTransition::CReversalTransition

Construye un objeto de transición de inversión e inicializa su duración.

```
CReversalTransition(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parámetros

*duration*<br/>
La duración de la transición.

## <a name="creversaltransitionm_duration"></a><a name="m_duration"></a>CReversalTransition::m_duration

La duración de la transición.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
