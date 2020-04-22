---
title: Clase CCustomTransition
ms.date: 11/04/2016
f1_keywords:
- CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::Create
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialValueSpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialVelocitySpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_pInterpolator
helpviewer_keywords:
- CCustomTransition [MFC], CCustomTransition
- CCustomTransition [MFC], Create
- CCustomTransition [MFC], SetInitialValue
- CCustomTransition [MFC], SetInitialVelocity
- CCustomTransition [MFC], m_bInitialValueSpecified
- CCustomTransition [MFC], m_bInitialVelocitySpecified
- CCustomTransition [MFC], m_initialValue
- CCustomTransition [MFC], m_initialVelocity
- CCustomTransition [MFC], m_pInterpolator
ms.assetid: 5bd3f492-940f-4290-a38b-fa68eb8f8401
ms.openlocfilehash: 76e0d12308ad579e4bdf9866dfcf1cde231a2d0c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749155"
---
# <a name="ccustomtransition-class"></a>Clase CCustomTransition

Implementa una transición personalizada.

## <a name="syntax"></a>Sintaxis

```
class CCustomTransition : public CBaseTransition;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCustomTransition::CCustomTransition](#ccustomtransition)|Construye un objeto de transición personalizado.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCustomTransition::Create](#create)|Llama a la biblioteca de transición para crear un objeto COM de transición encapsulado. (Reemplaza [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|
|[CCustomTransition::SetInitialValue](#setinitialvalue)|Establece un valor inicial, que se aplicará a una variable de animación asociada a esta transición.|
|[CCustomTransition::SetInitialVelocity](#setinitialvelocity)|Establece una velocidad inicial, que se aplicará a una variable de animación asociada a esta transición.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CCustomTransition::m_bInitialValueSpecified](#m_binitialvaluespecified)|Especifica si el valor inicial se especificó con SetInitialValue.|
|[CCustomTransition::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|Especifica si la velocidad inicial se especificó con SetInitialVelocity.|
|[CCustomTransition::m_initialValue](#m_initialvalue)|Almacena el valor inicial.|
|[CCustomTransition::m_initialVelocity](#m_initialvelocity)|Almacena la velocidad inicial.|
|[CCustomTransition::m_pInterpolator](#m_pinterpolator)|Almacena un puntero a un interpolador personalizado.|

## <a name="remarks"></a>Observaciones

La clase CCustomTransitions permite a los desarrolladores implementar transiciones personalizadas. Se crea y se usa como una transición estándar, pero su constructor acepta como parámetro un puntero a un interpolador personalizado. Realice los pasos siguientes para utilizar transiciones personalizadas: 1. Derive una clase de CCustomInterpolator e implemente al menos el método InterpolateValue. 2. Asegúrese de que la duración del objeto interpolador personalizado debe ser mayor que la duración de la animación donde se usa. 3. Crear una instancia (mediante el operador new) un CCustomTransition objeto y pasar un puntero al interpolador personalizado en el constructor. 4. Llame a CCustomTransition::SetInitialValue y CCustomTransition::SetInitialVelocity si estos parámetros son necesarios para la interpolación personalizada. 5. Pase el puntero a la transición personalizada al método AddTransition del objeto de animación, cuyo valor debe animarse con el algoritmo personalizado. 6. Cuando el valor del objeto de animación debe cambiar la API de animación de Windows llamará a InterpolateValue (y otros métodos relevantes) en CCustomInterpolator.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CCustomTransition`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="ccustomtransitionccustomtransition"></a><a name="ccustomtransition"></a>CCustomTransition::CCustomTransition

Construye un objeto de transición personalizado.

```
CCustomTransition(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Parámetros

*pInterpolator*<br/>
Un puntero al interpolador personalizado.

## <a name="ccustomtransitioncreate"></a><a name="create"></a>CCustomTransition::Create

Llama a la biblioteca de transición para crear un objeto COM de transición encapsulado.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,
    IUIAnimationTransitionFactory* pFactory);
```

### <a name="parameters"></a>Parámetros

*pFactory*<br/>
Un puntero a la fábrica de transición, que es responsable de la creación de transiciones personalizadas.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

Este método también puede establecer el valor inicial y la velocidad inicial que se aplicará a una variable de animación, que está asociada a esta transición. Para ello, debe llamar a SetInitialValue y SetInitialVelocity antes de que el marco de trabajo cree el objeto COM de transición encapsulado (sucede cuando se llama a CAnimationController::AnimateGroup).

## <a name="ccustomtransitionm_binitialvaluespecified"></a><a name="m_binitialvaluespecified"></a>CCustomTransition::m_bInitialValueSpecified

Especifica si el valor inicial se especificó con SetInitialValue.

```
BOOL m_bInitialValueSpecified;
```

## <a name="ccustomtransitionm_binitialvelocityspecified"></a><a name="m_binitialvelocityspecified"></a>CCustomTransition::m_bInitialVelocitySpecified

Especifica si la velocidad inicial se especificó con SetInitialVelocity.

```
BOOL m_bInitialVelocitySpecified;
```

## <a name="ccustomtransitionm_initialvalue"></a><a name="m_initialvalue"></a>CCustomTransition::m_initialValue

Almacena el valor inicial.

```
DOUBLE m_initialValue;
```

## <a name="ccustomtransitionm_initialvelocity"></a><a name="m_initialvelocity"></a>CCustomTransition::m_initialVelocity

Almacena la velocidad inicial.

```
DOUBLE m_initialVelocity;
```

## <a name="ccustomtransitionm_pinterpolator"></a><a name="m_pinterpolator"></a>CCustomTransition::m_pInterpolator

Almacena un puntero a un interpolador personalizado.

```
CCustomInterpolator* m_pInterpolator;
```

## <a name="ccustomtransitionsetinitialvalue"></a><a name="setinitialvalue"></a>CCustomTransition::SetInitialValue

Establece un valor inicial, que se aplicará a una variable de animación asociada a esta transición.

```cpp
void SetInitialValue(DOUBLE initialValue);
```

### <a name="parameters"></a>Parámetros

*initialValue*

## <a name="ccustomtransitionsetinitialvelocity"></a><a name="setinitialvelocity"></a>CCustomTransition::SetInitialVelocity

Establece una velocidad inicial, que se aplicará a una variable de animación asociada a esta transición.

```cpp
void SetInitialVelocity(DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parámetros

*initialVelocity*

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
