---
title: CReversalTransition (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::Create
- AFXANIMATIONCONTROLLER/CReversalTransition::m_duration
dev_langs:
- C++
helpviewer_keywords:
- CReversalTransition [MFC], CReversalTransition
- CReversalTransition [MFC], Create
- CReversalTransition [MFC], m_duration
ms.assetid: e89516be-2d07-4885-95a8-fc278f46e3ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 393c0ed7c9d1c5715528468e0c611ae399fbadf6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431507"
---
# <a name="creversaltransition-class"></a>Clase CReversalTransition

Encapsula una transición de inversión.

## <a name="syntax"></a>Sintaxis

```
class CReversalTransition : public CBaseTransition;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CReversalTransition::CReversalTransition](#creversaltransition)|Construye un objeto de la transición de inversión e inicializa su duración.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CReversalTransition::Create](#create)|Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado. (Invalida [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CReversalTransition::m_duration](#m_duration)|La duración de la transición.|

## <a name="remarks"></a>Comentarios

Una transición de inversión cambia suavemente dirección durante un período determinado. El valor final será el mismo que el valor inicial y la velocidad final será el valor negativo de la velocidad inicial. Dado que todas las transiciones se borran automáticamente, se recomienda asignada a ellos mediante el operador nuevo. El objeto COM IUIAnimationTransition encapsulado se crea por CAnimationController::AnimateGroup, hasta que es NULL. Cambiar las variables de miembro después de la creación de este objeto COM no tiene ningún efecto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CReversalTransition](../../mfc/reference/creversaltransition-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="create"></a>  CReversalTransition::Create

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

##  <a name="creversaltransition"></a>  CReversalTransition::CReversalTransition

Construye un objeto de la transición de inversión e inicializa su duración.

```
CReversalTransition(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parámetros

*Duración*<br/>
La duración de la transición.

##  <a name="m_duration"></a>  CReversalTransition::m_duration

La duración de la transición.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
