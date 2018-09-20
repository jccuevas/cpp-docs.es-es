---
title: CCustomTransition (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94590b5f14fe8f8be072a1db751129045aaa08e2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434861"
---
# <a name="ccustomtransition-class"></a>Clase CCustomTransition

Implementa una transición personalizada.

## <a name="syntax"></a>Sintaxis

```
class CCustomTransition : public CBaseTransition;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CCustomTransition::CCustomTransition](#ccustomtransition)|Construye un objeto de transición personalizada.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CCustomTransition::Create](#create)|Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado. (Invalida [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|
|[CCustomTransition::SetInitialValue](#setinitialvalue)|Establece un valor inicial, que se aplicarán a una variable de animación asociada con esta transición.|
|[CCustomTransition::SetInitialVelocity](#setinitialvelocity)|Establece una velocidad inicial, que se aplicarán a una variable de animación asociada con esta transición.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|nombre|Descripción|
|----------|-----------------|
|[CCustomTransition::m_bInitialValueSpecified](#m_binitialvaluespecified)|Especifica si se ha especificado el valor inicial con SetInitialValue.|
|[CCustomTransition::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|Especifica si se ha especificado la velocidad inicial con SetInitialVelocity.|
|[CCustomTransition::m_initialValue](#m_initialvalue)|Almacena el valor inicial.|
|[CCustomTransition::m_initialVelocity](#m_initialvelocity)|Almacena la velocidad inicial.|
|[CCustomTransition::m_pInterpolator](#m_pinterpolator)|Almacena un puntero a un interpolador personalizado.|

## <a name="remarks"></a>Comentarios

La clase CCustomTransitions permite a los desarrolladores implementar transiciones personalizadas. Se crea y utiliza como una transición estándar, pero su constructor acepta como parámetro un puntero a un interpolador personalizado. Realice los pasos siguientes para usar transiciones personalizadas: 1. Derivar una clase CCustomInterpolator e implementar al menos InterpolateValue método. 2. Asegúrese de que la duración del objeto personalizado interpolador debe ser la duración de la animación que se utiliza. 3. Crear una instancia (mediante el operador new) un objeto CCustomTransition y pasar un puntero a un interpolador personalizado en el constructor. 4. Llamar a CCustomTransition::SetInitialValue y CCustomTransition::SetInitialVelocity si estos parámetros son necesarios para la interpolación personalizada. 5. Sitúe el puntero pase personalizado al método AddTransition del objeto de animación, cuyo valor se debe animar con el algoritmo personalizado. 6. Cuando tenga que cambiar el valor del objeto de animación de API de animación de Windows llamará a en CCustomInterpolator InterpolateValue (y otros métodos relevantes).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CCustomTransition`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="ccustomtransition"></a>  CCustomTransition::CCustomTransition

Construye un objeto de transición personalizada.

```
CCustomTransition(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Parámetros

*pInterpolator*<br/>
Un puntero a un interpolador personalizado.

##  <a name="create"></a>  CCustomTransition::Create

Llama a la biblioteca de transición para crear el objeto COM de transición encapsulado.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,
    IUIAnimationTransitionFactory* pFactory);
```

### <a name="parameters"></a>Parámetros

*pFactory*<br/>
Un puntero a la fábrica de transición, que es responsable de la creación de transiciones personalizadas.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

Este método también puede establecer un valor inicial y velocidad inicial que se aplicará a una variable de animación, que está asociada a esta transición. Para ello debe llamar a SetInitialValue y SetInitialVelocity antes de que el marco crea el objeto COM de transición encapsulado (ocurre cuando se llama a CAnimationController::AnimateGroup).

##  <a name="m_binitialvaluespecified"></a>  CCustomTransition::m_bInitialValueSpecified

Especifica si se ha especificado el valor inicial con SetInitialValue.

```
BOOL m_bInitialValueSpecified;
```

##  <a name="m_binitialvelocityspecified"></a>  CCustomTransition::m_bInitialVelocitySpecified

Especifica si se ha especificado la velocidad inicial con SetInitialVelocity.

```
BOOL m_bInitialVelocitySpecified;
```

##  <a name="m_initialvalue"></a>  CCustomTransition::m_initialValue

Almacena el valor inicial.

```
DOUBLE m_initialValue;
```

##  <a name="m_initialvelocity"></a>  CCustomTransition::m_initialVelocity

Almacena la velocidad inicial.

```
DOUBLE m_initialVelocity;
```

##  <a name="m_pinterpolator"></a>  CCustomTransition::m_pInterpolator

Almacena un puntero a un interpolador personalizado.

```
CCustomInterpolator* m_pInterpolator;
```

##  <a name="setinitialvalue"></a>  CCustomTransition::SetInitialValue

Establece un valor inicial, que se aplicarán a una variable de animación asociada con esta transición.

```
void SetInitialValue(DOUBLE initialValue);
```

### <a name="parameters"></a>Parámetros

*initialValue*

##  <a name="setinitialvelocity"></a>  CCustomTransition::SetInitialVelocity

Establece una velocidad inicial, que se aplicarán a una variable de animación asociada con esta transición.

```
void SetInitialVelocity(DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parámetros

*initialVelocity*

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
