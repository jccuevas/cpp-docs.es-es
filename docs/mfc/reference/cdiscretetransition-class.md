---
title: Clase CDiscreteTransition
ms.date: 11/04/2016
f1_keywords:
- CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::Create
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_delay
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_hold
helpviewer_keywords:
- CDiscreteTransition [MFC], CDiscreteTransition
- CDiscreteTransition [MFC], Create
- CDiscreteTransition [MFC], m_dblFinalValue
- CDiscreteTransition [MFC], m_delay
- CDiscreteTransition [MFC], m_hold
ms.assetid: b4d84fb3-ccaa-451c-a69b-6b50dcb9b9c8
ms.openlocfilehash: 2a32ee7921e927e25a5196d38c8f5ae350ab2b8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375656"
---
# <a name="cdiscretetransition-class"></a>Clase CDiscreteTransition

Encapsula una transición discreta.

## <a name="syntax"></a>Sintaxis

```
class CDiscreteTransition : public CBaseTransition;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDiscreteTransition::CDiscreteTransition](#cdiscretetransition)|Construye un objeto de transición discreto e inicializa sus parámetros.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDiscreteTransition::Create](#create)|Llama a la biblioteca de transición para crear un objeto COM de transición encapsulado. (Reemplaza [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDiscreteTransition::m_dblFinalValue](#m_dblfinalvalue)|El valor de la variable de animación al final de la transición.|
|[CDiscreteTransition::m_delay](#m_delay)|La cantidad de tiempo por la cual retrasar el switch instantáneo al valor final.|
|[CDiscreteTransition::m_hold](#m_hold)|La cantidad de tiempo para mantener la variable en su valor final.|

## <a name="remarks"></a>Observaciones

Durante una transición discreta, la variable de animación permanece en el valor inicial durante un tiempo de retardo especificado y, a continuación, cambia instantáneamente a un valor final especificado y permanece en ese valor durante un tiempo de espera determinado. Dado que todas las transiciones se borran automáticamente, se recomienda asignarlas mediante el operador new. CAnimationController::AnimateGroup crea el objeto COM IUIAnimationTransition encapsulado, hasta que es NULL. Cambiar las variables miembro después de la creación de este objeto COM no tiene ningún efecto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CDiscreteTransition](../../mfc/reference/cdiscretetransition-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="cdiscretetransitioncdiscretetransition"></a><a name="cdiscretetransition"></a>CDiscreteTransition::CDiscreteTransition

Construye un objeto de transición discreto e inicializa sus parámetros.

```
CDiscreteTransition(
    UI_ANIMATION_SECONDS delay,
    DOUBLE dblFinalValue,
    UI_ANIMATION_SECONDS hold);
```

### <a name="parameters"></a>Parámetros

*Retraso*<br/>
La cantidad de tiempo por la cual retrasar el switch instantáneo al valor final.

*dblFinalValue*<br/>
El valor de la variable de animación al final de la transición.

*Mantener*<br/>
La cantidad de tiempo para mantener la variable en su valor final.

## <a name="cdiscretetransitioncreate"></a><a name="create"></a>CDiscreteTransition::Create

Llama a la biblioteca de transición para crear un objeto COM de transición encapsulado.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

*pLibrary*<br/>
Puntero a una [interfaz IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), que define una biblioteca de transiciones estándar.

### <a name="return-value"></a>Valor devuelto

TRUESi la transición se crea correctamente; de lo contrario FALSO.

## <a name="cdiscretetransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>CDiscreteTransition::m_dblFinalValue

El valor de la variable de animación al final de la transición.

```
DOUBLE m_dblFinalValue;
```

## <a name="cdiscretetransitionm_delay"></a><a name="m_delay"></a>CDiscreteTransition::m_delay

La cantidad de tiempo por la cual retrasar el switch instantáneo al valor final.

```
UI_ANIMATION_SECONDS m_delay;
```

## <a name="cdiscretetransitionm_hold"></a><a name="m_hold"></a>CDiscreteTransition::m_hold

La cantidad de tiempo para mantener la variable en su valor final.

```
UI_ANIMATION_SECONDS m_hold;
```

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
