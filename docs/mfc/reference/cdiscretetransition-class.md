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
ms.openlocfilehash: 7087dfa13972737f0a1244d2cc9a7088b23dc184
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506861"
---
# <a name="cdiscretetransition-class"></a>Clase CDiscreteTransition

Encapsula una transición discreta.

## <a name="syntax"></a>Sintaxis

```
class CDiscreteTransition : public CBaseTransition;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDiscreteTransition::CDiscreteTransition](#cdiscretetransition)|Construye un objeto de transición discreto e inicializa sus parámetros.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDiscreteTransition::Create](#create)|Llama a la biblioteca de transición para crear el objeto COM de transición encapsulada. (Invalida [CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create)).|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDiscreteTransition::m_dblFinalValue](#m_dblfinalvalue)|Valor de la variable de animación al final de la transición.|
|[CDiscreteTransition::m_delay](#m_delay)|Cantidad de tiempo que se retrasará el cambio instantáneo hasta el valor final.|
|[CDiscreteTransition::m_hold](#m_hold)|Cantidad de tiempo que se debe contener la variable en su valor final.|

## <a name="remarks"></a>Comentarios

Durante una transición discreta, la variable de animación permanece en el valor inicial durante un tiempo de retraso especificado y, a continuación, cambia de forma instantánea a un valor final especificado y permanece en ese valor durante un tiempo de espera determinado. Dado que todas las transiciones se borran automáticamente, se recomienda asignarlas mediante el operador new. CAnimationController:: AnimateGroup crea el objeto COM encapsulado IUIAnimationTransition, hasta que sea NULL. Cambiar las variables de miembro después de la creación de este objeto COM no tiene ningún efecto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CDiscreteTransition](../../mfc/reference/cdiscretetransition-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="cdiscretetransition"></a>  CDiscreteTransition::CDiscreteTransition

Construye un objeto de transición discreto e inicializa sus parámetros.

```
CDiscreteTransition(
    UI_ANIMATION_SECONDS delay,
    DOUBLE dblFinalValue,
    UI_ANIMATION_SECONDS hold);
```

### <a name="parameters"></a>Parámetros

*delay*<br/>
Cantidad de tiempo que se retrasará el cambio instantáneo hasta el valor final.

*dblFinalValue*<br/>
Valor de la variable de animación al final de la transición.

*hold*<br/>
Cantidad de tiempo que se debe contener la variable en su valor final.

##  <a name="create"></a>  CDiscreteTransition::Create

Llama a la biblioteca de transición para crear el objeto COM de transición encapsulada.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

*pLibrary*<br/>
Puntero a una [interfaz IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), que define una biblioteca de transiciones estándar.

### <a name="return-value"></a>Valor devuelto

TRUE si la transición se crea correctamente; en caso contrario, FALSE.

##  <a name="m_dblfinalvalue"></a>  CDiscreteTransition::m_dblFinalValue

Valor de la variable de animación al final de la transición.

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_delay"></a>  CDiscreteTransition::m_delay

Cantidad de tiempo que se retrasará el cambio instantáneo hasta el valor final.

```
UI_ANIMATION_SECONDS m_delay;
```

##  <a name="m_hold"></a>  CDiscreteTransition::m_hold

Cantidad de tiempo que se debe contener la variable en su valor final.

```
UI_ANIMATION_SECONDS m_hold;
```

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
