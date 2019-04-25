---
title: Clase CSmoothStopTransition
ms.date: 11/04/2016
f1_keywords:
- CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::Create
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::m_maximumDuration
helpviewer_keywords:
- CSmoothStopTransition [MFC], CSmoothStopTransition
- CSmoothStopTransition [MFC], Create
- CSmoothStopTransition [MFC], m_dblFinalValue
- CSmoothStopTransition [MFC], m_maximumDuration
ms.assetid: e1a4b476-6f96-43dd-90db-870a64406b85
ms.openlocfilehash: 89496c1b867d6fbb498f56271de7b45afef7edc3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323887"
---
# <a name="csmoothstoptransition-class"></a>Clase CSmoothStopTransition

Encapsula una transición de pausa suavizada.

## <a name="syntax"></a>Sintaxis

```
class CSmoothStopTransition : public CBaseTransition;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CSmoothStopTransition::CSmoothStopTransition](#csmoothstoptransition)|Construye una transición de pausa suavizada e inicializa su valor final y la duración máxima.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSmoothStopTransition::Create](#create)|Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado. (Invalida [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CSmoothStopTransition::m_dblFinalValue](#m_dblfinalvalue)|El valor de la variable de animación al final de la transición.|
|[CSmoothStopTransition::m_maximumDuration](#m_maximumduration)|La duración máxima de la transición.|

## <a name="remarks"></a>Comentarios

Una transición de pausa suavizada ralentiza cuando se aproxima a un determinado valor final y alcanza su con una velocidad de cero. La duración de la transición viene determinada por la velocidad inicial, la diferencia entre los valores iniciales y finales y la duración máxima especificada. Si no hay ninguna solución que consta de un único arco parabólica, este método crea una transición cúbica. Dado que todas las transiciones se borran automáticamente, se recomienda asignada a ellos mediante el operador nuevo. El objeto COM IUIAnimationTransition encapsulado se crea por CAnimationController::AnimateGroup, hasta que es NULL. Cambiar las variables de miembro después de la creación de este objeto COM no tiene ningún efecto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CSmoothStopTransition](../../mfc/reference/csmoothstoptransition-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="create"></a>  CSmoothStopTransition::Create

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

##  <a name="csmoothstoptransition"></a>  CSmoothStopTransition::CSmoothStopTransition

Construye una transición de pausa suavizada e inicializa su valor final y la duración máxima.

```
CSmoothStopTransition(
    UI_ANIMATION_SECONDS maximumDuration,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>Parámetros

*maximumDuration*<br/>
La duración máxima de la transición.

*dblFinalValue*<br/>
El valor de la variable de animación al final de la transición.

##  <a name="m_dblfinalvalue"></a>  CSmoothStopTransition::m_dblFinalValue

El valor de la variable de animación al final de la transición.

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_maximumduration"></a>  CSmoothStopTransition::m_maximumDuration

La duración máxima de la transición.

```
UI_ANIMATION_SECONDS m_maximumDuration;
```

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
