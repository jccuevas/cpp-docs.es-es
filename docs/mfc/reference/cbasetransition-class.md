---
title: Clase CBaseTransition
ms.date: 03/27/2019
f1_keywords:
- CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboardAtKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::Clear
- AFXANIMATIONCONTROLLER/CBaseTransition::Create
- AFXANIMATIONCONTROLLER/CBaseTransition::GetEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::GetStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::GetType
- AFXANIMATIONCONTROLLER/CBaseTransition::IsAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::SetKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::SetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_transition
- AFXANIMATIONCONTROLLER/CBaseTransition::m_type
helpviewer_keywords:
- CBaseTransition [MFC], CBaseTransition
- CBaseTransition [MFC], AddToStoryboard
- CBaseTransition [MFC], AddToStoryboardAtKeyframes
- CBaseTransition [MFC], Clear
- CBaseTransition [MFC], Create
- CBaseTransition [MFC], GetEndKeyframe
- CBaseTransition [MFC], GetRelatedVariable
- CBaseTransition [MFC], GetStartKeyframe
- CBaseTransition [MFC], GetTransition
- CBaseTransition [MFC], GetType
- CBaseTransition [MFC], IsAdded
- CBaseTransition [MFC], SetKeyframes
- CBaseTransition [MFC], SetRelatedVariable
- CBaseTransition [MFC], m_bAdded
- CBaseTransition [MFC], m_pEndKeyframe
- CBaseTransition [MFC], m_pRelatedVariable
- CBaseTransition [MFC], m_pStartKeyframe
- CBaseTransition [MFC], m_transition
- CBaseTransition [MFC], m_type
ms.assetid: dfe84007-bbc5-43b7-b5b8-fae9145573bf
ms.openlocfilehash: 8339785fd10fa3dcef1c0fb573310762dc2d2405
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352829"
---
# <a name="cbasetransition-class"></a>Clase CBaseTransition

Representa una transición básica.

## <a name="syntax"></a>Sintaxis

```
class CBaseTransition : public CObject;
```

## <a name="members"></a>Miembros

### <a name="public-enumerations"></a>Enumeraciones públicas

|Nombre|Descripción|
|----------|-----------------|
|[CBaseTransition::TRANSITION_TYPE (enumeración)](#transition_type_enumeration)|Define los tipos de transición admitidos actualmente por la implementación MFC de Windows Animation API.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBaseTransition::CBaseTransition](#cbasetransition)|Construye un objeto de transición base.|
|[CBaseTransition::-CBaseTransition](#_dtorcbasetransition)|Destructor. Se llama cuando se destruye un objeto de transición.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CBaseTransition::AddToStoryboard](#addtostoryboard)|Agrega una transición a un guión gráfico.|
|[CBaseTransition::AddToStoryboardAtKeyframes](#addtostoryboardatkeyframes)|Agrega una transición a un guión gráfico.|
|[CBaseTransition::Clear](#clear)|Libera el objeto COM IUIAnimationTransition encapsulado.|
|[CBaseTransition::Create](#create)|Crea una transición COM.|
|[CBaseTransition::GetEndKeyframe](#getendkeyframe)|Devuelve el fotograma clave de inicio.|
|[CBaseTransition::GetRelatedVariable](#getrelatedvariable)|Devuelve un puntero a la variable relacionada.|
|[CBaseTransition::GetStartKeyframe](#getstartkeyframe)|Devuelve el fotograma clave de inicio.|
|[CBaseTransition::GetTransition](#gettransition)|Sobrecargado. Devuelve un puntero al objeto de transición COM subyacente.|
|[CBaseTransition::GetType](#gettype)|Devuelve el tipo de transición.|
|[CBaseTransition::IsAdded](#isadded)|Indica si se ha agregado una transición a un guión gráfico.|
|[CBaseTransition::SetKeyframes](#setkeyframes)|Establece fotogramas clave para una transición.|
|[CBaseTransition::SetRelatedVariable](#setrelatedvariable)|Establece una relación entre la variable de animación y la transición.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CBaseTransition::m_bAdded](#m_badded)|Especifica si se ha agregado una transición a un guión gráfico.|
|[CBaseTransition::m_pEndKeyframe](#m_pendkeyframe)|Almacena un puntero al fotograma clave que especifica el final de la transición.|
|[CBaseTransition::m_pRelatedVariable](#m_prelatedvariable)|Un puntero a una variable de animación, que se anima con la transición almacenada en m_transition.|
|[CBaseTransition::m_pStartKeyframe](#m_pstartkeyframe)|Almacena un puntero al fotograma clave que especifica el principio de la transición.|
|[CBaseTransition::m_transition](#m_transition)|Almacena un puntero a IUIAnimationTransition. NULL si no se ha creado un objeto de transición COM.|
|[CBaseTransition::m_type](#m_type)|Almacena el tipo de transición.|

## <a name="remarks"></a>Observaciones

Esta clase encapsula la interfaz IUIAnimationTransition y sirve como clase base para todas las transiciones.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CBaseTransition`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="cbasetransitioncbasetransition"></a><a name="_dtorcbasetransition"></a>CBaseTransition::-CBaseTransition

Destructor. Se llama cuando se destruye un objeto de transición.

```
virtual ~CBaseTransition();
```

## <a name="cbasetransitionaddtostoryboard"></a><a name="addtostoryboard"></a>CBaseTransition::AddToStoryboard

Agrega una transición a un guión gráfico.

```
BOOL AddToStoryboard(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parámetros

*pStoryboard*<br/>
Un puntero al guión gráfico, que animará la variable relacionada.

### <a name="return-value"></a>Valor devuelto

TRUE, si la transición se agregó correctamente a un guión gráfico.

### <a name="remarks"></a>Observaciones

Aplica la transición a la variable relacionada en el guión gráfico. Si esta es la primera transición aplicada a esta variable en este guión gráfico, la transición comienza al principio del guión gráfico. De lo contrario, la transición se anexa a la transición agregada más recientemente a la variable.

## <a name="cbasetransitionaddtostoryboardatkeyframes"></a><a name="addtostoryboardatkeyframes"></a>CBaseTransition::AddToStoryboardAtKeyframes

Agrega una transición a un guión gráfico.

```
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parámetros

*pStoryboard*<br/>
Un puntero al guión gráfico, que animará la variable relacionada.

### <a name="return-value"></a>Valor devuelto

TRUE, si la transición se agregó correctamente a un guión gráfico.

### <a name="remarks"></a>Observaciones

Aplica la transición a la variable relacionada en el guión gráfico. Si se especificó el fotograma clave de inicio, la transición comienza en ese fotograma clave. Si se especificó el fotograma clave final, la transición comienza en el fotograma clave inicial y se detiene en el fotograma clave final. Si la transición se creó con un parámetro duration especificado, esa duración se sobrescribe con la duración del tiempo entre los fotogramas clave inicial y final. Si no se especificó ningún fotograma clave, la transición se anexa a la transición agregada más recientemente a la variable.

## <a name="cbasetransitioncbasetransition"></a><a name="cbasetransition"></a>CBaseTransition::CBaseTransition

Construye un objeto de transición base.

```
CBaseTransition();
```

## <a name="cbasetransitionclear"></a><a name="clear"></a>CBaseTransition::Clear

Libera el objeto COM IUIAnimationTransition encapsulado.

```
void Clear();
```

### <a name="remarks"></a>Observaciones

Este método debe llamarse desde un método Create de una clase derivada para evitar la fuga de la interfaz IUITransition.

## <a name="cbasetransitioncreate"></a><a name="create"></a>CBaseTransition::Create

Crea una transición COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory) = 0;
```

### <a name="parameters"></a>Parámetros

*pLibrary*<br/>
Puntero a la biblioteca de transición, que crea transiciones estándar. Puede ser NULL para transiciones personalizadas.

*pFactory*<br/>
Puntero a fábrica de transición, que crea transiciones personalizadas. Puede ser NULL para transiciones estándar.

### <a name="return-value"></a>Valor devuelto

TRUESi se creó correctamente un objeto COM de transición; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Se trata de una función virtual pura que se debe invalidar en una clase derivada. El marco de trabajo lo llama para crear instancias del objeto de transición COM subyacente.

## <a name="cbasetransitiongetendkeyframe"></a><a name="getendkeyframe"></a>CBaseTransition::GetEndKeyframe

Devuelve el fotograma clave de inicio.

```
CBaseKeyFrame* GetEndKeyframe();
```

### <a name="return-value"></a>Valor devuelto

Un puntero válido a un fotograma clave, o NULL si no se debe insertar una transición entre fotogramas clave.

### <a name="remarks"></a>Observaciones

Este método se puede utilizar para acceder a un objeto de fotograma clave establecido previamente por SetKeyframes. Se llama mediante código de nivel superior cuando se agregan transiciones al guión gráfico.

## <a name="cbasetransitiongetrelatedvariable"></a><a name="getrelatedvariable"></a>CBaseTransition::GetRelatedVariable

Devuelve un puntero a la variable relacionada.

```
CAnimationVariable* GetRelatedVariable();
```

### <a name="return-value"></a>Valor devuelto

Un puntero válido a la variable de animación, o NULL si SetRelatedVariable no ha establecido una variable de animación.

### <a name="remarks"></a>Observaciones

Se trata de un descriptor de acceso a la variable de animación relacionada.

## <a name="cbasetransitiongetstartkeyframe"></a><a name="getstartkeyframe"></a>CBaseTransition::GetStartKeyframe

Devuelve el fotograma clave de inicio.

```
CBaseKeyFrame* GetStartKeyframe();
```

### <a name="return-value"></a>Valor devuelto

Un puntero válido a un fotograma clave, o NULL si una transición no debe iniciarse después de un fotograma clave.

### <a name="remarks"></a>Observaciones

Este método se puede utilizar para acceder a un objeto de fotograma clave establecido previamente por SetKeyframes. Se llama mediante código de nivel superior cuando se agregan transiciones al guión gráfico.

## <a name="cbasetransitiongettransition"></a><a name="gettransition"></a>CBaseTransition::GetTransition

Devuelve un puntero al objeto de transición COM subyacente.

```
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory);

IUIAnimationTransition* GetTransition();
```

### <a name="parameters"></a>Parámetros

*pLibrary*<br/>
Puntero a la biblioteca de transición, que crea transiciones estándar. Puede ser NULL para transiciones personalizadas.

*pFactory*<br/>
Puntero a fábrica de transición, que crea transiciones personalizadas. Puede ser NULL para transiciones estándar.

### <a name="return-value"></a>Valor devuelto

Un puntero válido a IUIAnimationTransition o NULL si no se puede crear la transición subyacente.

### <a name="remarks"></a>Observaciones

Este método devuelve un puntero al objeto de transición COM subyacente y lo crea si es necesario.

## <a name="cbasetransitiongettype"></a><a name="gettype"></a>CBaseTransition::GetType

Devuelve el tipo de transición.

```
TRANSITION_TYPE GetType() const;
```

### <a name="return-value"></a>Valor devuelto

Uno de TRANSITION_TYPE valores enumerados.

### <a name="remarks"></a>Observaciones

Este método se puede utilizar para identificar un objeto de transición por su tipo. El tipo se establece en un constructor en una clase derivada.

## <a name="cbasetransitionisadded"></a><a name="isadded"></a>CBaseTransition::IsAdded

Indica si se ha agregado una transición a un guión gráfico.

```
BOOL IsAdded();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ha agregado una transición a un guión gráfico, de lo contrario FALSE.

### <a name="remarks"></a>Observaciones

Esta marca se establece internamente cuando el código de nivel superior agrega transiciones al guión gráfico.

## <a name="cbasetransitionm_badded"></a><a name="m_badded"></a>CBaseTransition::m_bAdded

Especifica si se ha agregado una transición a un guión gráfico.

```
BOOL m_bAdded;
```

## <a name="cbasetransitionm_pendkeyframe"></a><a name="m_pendkeyframe"></a>CBaseTransition::m_pEndKeyframe

Almacena un puntero al fotograma clave que especifica el final de la transición.

```
CBaseKeyFrame* m_pEndKeyframe;
```

## <a name="cbasetransitionm_prelatedvariable"></a><a name="m_prelatedvariable"></a>CBaseTransition::m_pRelatedVariable

Un puntero a una variable de animación, que se anima con la transición almacenada en m_transition.

```
CAnimationVariable* m_pRelatedVariable;
```

## <a name="cbasetransitionm_pstartkeyframe"></a><a name="m_pstartkeyframe"></a>CBaseTransition::m_pStartKeyframe

Almacena un puntero al fotograma clave que especifica el principio de la transición.

```
CBaseKeyFrame* m_pStartKeyframe;
```

## <a name="cbasetransitionm_transition"></a><a name="m_transition"></a>CBaseTransition::m_transition

Almacena un puntero a IUIAnimationTransition. NULL si no se ha creado un objeto de transición COM.

```
ATL::CComPtr<IUIAnimationTransition> m_transition;
```

## <a name="cbasetransitionm_type"></a><a name="m_type"></a>CBaseTransition::m_type

Almacena el tipo de transición.

```
TRANSITION_TYPE m_type;
```

## <a name="cbasetransitionsetkeyframes"></a><a name="setkeyframes"></a>CBaseTransition::SetKeyframes

Establece fotogramas clave para una transición.

```
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,
    CBaseKeyFrame* pEnd = NULL);
```

### <a name="parameters"></a>Parámetros

*Pstart*<br/>
Un fotograma clave que especifica el principio de la transición.

*Pend*<br/>
Un fotograma clave que especifica el final de la transición.

### <a name="remarks"></a>Observaciones

Este método indica a la transición que se inicie después del fotograma clave especificado y, opcionalmente, si pEnd no es NULL, termine antes que el fotograma clave especificado. Si la transición se creó con un parámetro duration especificado, esa duración se sobrescribe con la duración del tiempo entre los fotogramas clave inicial y final.

## <a name="cbasetransitionsetrelatedvariable"></a><a name="setrelatedvariable"></a>CBaseTransition::SetRelatedVariable

Establece una relación entre la variable de animación y la transición.

```
void SetRelatedVariable(CAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parámetros

*pVariable*<br/>
Un puntero a la variable de animación relacionada.

### <a name="remarks"></a>Observaciones

Establece una relación entre la variable de animación y la transición. Una transición solo se puede aplicar a una variable.

## <a name="cbasetransitiontransition_type-enumeration"></a><a name="transition_type_enumeration"></a>CBaseTransition::TRANSITION_TYPE (enumeración)

Define los tipos de transición admitidos actualmente por la implementación MFC de Windows Animation API.

```
enum TRANSITION_TYPE;
```

### <a name="remarks"></a>Observaciones

Un tipo de transición se establece en el constructor de transición específica. Por ejemplo, CSinusoidalTransitionFromRange establece su tipo en SINUSOIDAL_FROM_RANGE.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
