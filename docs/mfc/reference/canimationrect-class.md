---
title: Clase CAnimationRect
ms.date: 11/04/2016
f1_keywords:
- CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationRect::GetBottom
- AFXANIMATIONCONTROLLER/CAnimationRect::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetLeft
- AFXANIMATIONCONTROLLER/CAnimationRect::GetRight
- AFXANIMATIONCONTROLLER/CAnimationRect::GetTop
- AFXANIMATIONCONTROLLER/CAnimationRect::GetValue
- AFXANIMATIONCONTROLLER/CAnimationRect::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bFixedSize
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bottomValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_leftValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_rightValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_szInitial
- AFXANIMATIONCONTROLLER/CAnimationRect::m_topValue
helpviewer_keywords:
- CAnimationRect [MFC], CAnimationRect
- CAnimationRect [MFC], AddTransition
- CAnimationRect [MFC], GetBottom
- CAnimationRect [MFC], GetDefaultValue
- CAnimationRect [MFC], GetLeft
- CAnimationRect [MFC], GetRight
- CAnimationRect [MFC], GetTop
- CAnimationRect [MFC], GetValue
- CAnimationRect [MFC], SetDefaultValue
- CAnimationRect [MFC], GetAnimationVariableList
- CAnimationRect [MFC], m_bFixedSize
- CAnimationRect [MFC], m_bottomValue
- CAnimationRect [MFC], m_leftValue
- CAnimationRect [MFC], m_rightValue
- CAnimationRect [MFC], m_szInitial
- CAnimationRect [MFC], m_topValue
ms.assetid: 0294156d-241e-4a57-92b2-31234fe557d6
ms.openlocfilehash: 4ffd1254efd3283a4c5641092aefec8eec0ac22a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373336"
---
# <a name="canimationrect-class"></a>Clase CAnimationRect

Implementa la funcionalidad de un rectángulo cuyos lados se pueden animar.

## <a name="syntax"></a>Sintaxis

```
class CAnimationRect : public CAnimationBaseObject;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationRect::CAnimationRect](#canimationrect)|Sobrecargado. Construye un objeto rect de animación.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationRect::AddTransition](#addtransition)|Añade transiciones para las coordenadas izquierda, superior, derecha e inferior.|
|[CAnimationRect::GetBottom](#getbottom)|Proporciona acceso a CAnimationVariable que representa la coordenada inferior.|
|[CAnimationRect::GetDefaultValue](#getdefaultvalue)|Devuelve los valores predeterminados para los límites del rectángulo.|
|[CAnimationRect::GetLeft](#getleft)|Proporciona acceso a CAnimationVariable que representa la coordenada izquierda.|
|[CAnimationRect::GetRight](#getright)|Proporciona acceso a CAnimationVariable que representa la coordenada derecha.|
|[CAnimationRect::GetTop](#gettop)|Proporciona acceso a CAnimationVariable que representa la coordenada superior.|
|[CAnimationRect::GetValue](#getvalue)|Devuelve el valor actual.|
|[CAnimationRect::SetDefaultValue](#setdefaultvalue)|Establece el valor predeterminado.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationRect::GetAnimationVariableList](#getanimationvariablelist)|Coloca las variables de animación encapsuladas en una lista. (Reemplaza [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationRect::operador RECT](#operator_rect)|Convierte un CAnimationRect a RECT.|
|[CAnimationRect::operator ?](#operator_eq)|Asigna rect a CAnimationRect.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationRect::m_bFixedSize](#m_bfixedsize)|Especifica si el rectángulo tiene un tamaño fijo.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationRect::m_bottomValue](#m_bottomvalue)|La variable de animación encapsulada que representa el límite inferior del rectángulo de animación.|
|[CAnimationRect::m_leftValue](#m_leftvalue)|La variable de animación encapsulada que representa el límite izquierdo del rectángulo de animación.|
|[CAnimationRect::m_rightValue](#m_rightvalue)|La variable de animación encapsulada que representa el límite derecho del rectángulo de animación.|
|[CAnimationRect::m_szInitial](#m_szinitial)|Especifica el tamaño inicial del rectángulo de animación.|
|[CAnimationRect::m_topValue](#m_topvalue)|La variable de animación encapsulada que representa el límite Superior del rectángulo de animación.|

## <a name="remarks"></a>Observaciones

El CAnimationRect clase encapsula cuatro CAnimationVariable objetos y puede representar en aplicaciones un rectángulo. Para usar esta clase en la aplicación, simplemente cree una instancia de un objeto de esta clase, agréguelo al controlador de animación mediante CAnimationController::AddAnimationObject y llame a AddTransition para cada transición que se aplicará a las coordenadas izquierda, superior derecha e inferior.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationRect`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="canimationrectaddtransition"></a><a name="addtransition"></a>CAnimationRect::AddTransition

Añade transiciones para las coordenadas izquierda, superior, derecha e inferior.

```
void AddTransition(
    CBaseTransition* pLeftTransition,
    CBaseTransition* pTopTransition,
    CBaseTransition* pRightTransition,
    CBaseTransition* pBottomTransition);
```

### <a name="parameters"></a>Parámetros

*pLeftTransition*<br/>
Especifica la transición para el lado izquierdo.

*pTopTransition*<br/>
Especifica la transición para la parte superior.

*pRightTransition*<br/>
Especifica la transición para el lado derecho.

*pBottomTransition*<br/>
Especifica la transición para la parte inferior.

### <a name="remarks"></a>Observaciones

Llame a esta función para agregar las transiciones especificadas a la lista interna de transiciones que se aplicarán a las variables de animación para cada lado del rectángulo. Cuando se agregan transiciones, no se aplican inmediatamente y se almacenan en una lista interna. Las transiciones se aplican (se agregan a un guión gráfico para un valor determinado) cuando se llama a CAnimationController::AnimateGroup. Si no necesita aplicar una transición a uno de los lados del rectángulo, puede pasar NULL.

## <a name="canimationrectcanimationrect"></a><a name="canimationrect"></a>CAnimationRect::CAnimationRect

Construye un CAnimationRect objeto.

```
CAnimationRect();

CAnimationRect(
    const CRect& rect,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);

CAnimationRect(
    const CPoint& pt,
    const CSize& sz,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);

CAnimationRect(
    int nLeft,
    int nTop,
    int nRight,
    int nBottom,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
Especifica el rectángulo predeterminado.

*nGroupID*<br/>
Especifica el identificador de grupo.

*nObjectID*<br/>
Especifica el identificador de objeto.

*dwUserData*<br/>
Especifica los datos definidos por el usuario.

*Pt*<br/>
Coordenada de la esquina superior izquierda.

*Sz*<br/>
Tamaño del rectángulo.

*nIzquierda*<br/>
Especifica la coordenada del límite izquierdo.

*Ntop*<br/>
Especifica la coordenada del límite superior.

*nRight*<br/>
Especifica la coordenada del límite a la derecha.

*nBottom*<br/>
Especifica la coordenada del límite inferior.

### <a name="remarks"></a>Observaciones

El objeto se construye con valores predeterminados para izquierda, superior, derecha e inferior, ID de objeto e ID de grupo, que se establecerán en 0. Se pueden cambiar más adelante en tiempo de ejecución mediante SetDefaultValue y SetID.

## <a name="canimationrectgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationRect::GetAnimationVariableList

Coloca las variables de animación encapsuladas en una lista.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parámetros

*Lst*<br/>
Cuando se devuelve la función, contiene punteros a cuatro CAnimationVariable objetos que representan coordenadas de rectángulo.

## <a name="canimationrectgetbottom"></a><a name="getbottom"></a>CAnimationRect::GetBottom

Proporciona acceso a CAnimationVariable que representa la coordenada inferior.

```
CAnimationVariable& GetBottom();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a encapsulado CAnimationVariable que representa la coordenada inferior.

### <a name="remarks"></a>Observaciones

Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa la coordenada inferior.

## <a name="canimationrectgetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationRect::GetDefaultValue

Devuelve los valores predeterminados para los límites del rectángulo.

```
CRect GetDefaultValue();
```

### <a name="return-value"></a>Valor devuelto

Un valor CRect que contiene valores predeterminados para izquierda, derecha, superior e inferior.

### <a name="remarks"></a>Observaciones

Llame a esta función para recuperar el valor predeterminado, que se estableció previamente por constructor o SetDefaultValue.

## <a name="canimationrectgetleft"></a><a name="getleft"></a>CAnimationRect::GetLeft

Proporciona acceso a CAnimationVariable que representa la coordenada izquierda.

```
CAnimationVariable& GetLeft();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a encapsulado CAnimationVariable que representa la coordenada izquierda.

### <a name="remarks"></a>Observaciones

Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa la coordenada izquierda.

## <a name="canimationrectgetright"></a><a name="getright"></a>CAnimationRect::GetRight

Proporciona acceso a CAnimationVariable que representa la coordenada derecha.

```
CAnimationVariable& GetRight();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a encapsulado CAnimationVariable que representa la coordenada derecha.

### <a name="remarks"></a>Observaciones

Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa la coordenada correcta.

## <a name="canimationrectgettop"></a><a name="gettop"></a>CAnimationRect::GetTop

Proporciona acceso a CAnimationVariable que representa la coordenada superior.

```
CAnimationVariable& GetTop();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a encapsulado CAnimationVariable que representa la coordenada superior.

### <a name="remarks"></a>Observaciones

Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa la coordenada superior.

## <a name="canimationrectgetvalue"></a><a name="getvalue"></a>CAnimationRect::GetValue

Devuelve el valor actual.

```
BOOL GetValue(CRect& rect);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
Salida. Contiene el valor actual cuando se devuelve este método.

### <a name="return-value"></a>Valor devuelto

TRUE, si el valor actual se recuperó correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Llame a esta función para recuperar el valor actual del rectángulo de animación. Si se produce un error en este método o no se han inicializado los objetos COM subyacentes para izquierda, superior, derecha e inferior, rect contiene el valor predeterminado, que se estableció anteriormente en el constructor o por SetDefaultValue.

## <a name="canimationrectm_bfixedsize"></a><a name="m_bfixedsize"></a>CAnimationRect::m_bFixedSize

Especifica si el rectángulo tiene un tamaño fijo.

```
BOOL m_bFixedSize;
```

### <a name="remarks"></a>Observaciones

Si este miembro es true, el tamaño del rectángulo es fijo y los valores correctos e inferiores se vuelven a calcular cada vez que la esquina superior izquierda se mueve según el tamaño fijo. Establezca este valor en TRUE para mover fácilmente el rectángulo alrededor de la pantalla. En este caso, las transiciones aplicadas a las coordenadas derecha e inferior se omiten. El tamaño se almacena internamente al construir el objeto o llamar a SetDefaultValue. De forma predeterminada, este miembro se establece en FALSE.

## <a name="canimationrectm_bottomvalue"></a><a name="m_bottomvalue"></a>CAnimationRect::m_bottomValue

La variable de animación encapsulada que representa el límite inferior del rectángulo de animación.

```
CAnimationVariable m_bottomValue;
```

## <a name="canimationrectm_leftvalue"></a><a name="m_leftvalue"></a>CAnimationRect::m_leftValue

La variable de animación encapsulada que representa el límite izquierdo del rectángulo de animación.

```
CAnimationVariable m_leftValue;
```

## <a name="canimationrectm_rightvalue"></a><a name="m_rightvalue"></a>CAnimationRect::m_rightValue

La variable de animación encapsulada que representa el límite derecho del rectángulo de animación.

```
CAnimationVariable m_rightValue;
```

## <a name="canimationrectm_szinitial"></a><a name="m_szinitial"></a>CAnimationRect::m_szInitial

Especifica el tamaño inicial del rectángulo de animación.

```
CSize m_szInitial;
```

## <a name="canimationrectm_topvalue"></a><a name="m_topvalue"></a>CAnimationRect::m_topValue

La variable de animación encapsulada que representa el límite Superior del rectángulo de animación.

```
CAnimationVariable m_topValue;
```

## <a name="canimationrectoperator-rect"></a><a name="operator_rect"></a>CAnimationRect::operador RECT

Convierte un CAnimationRect a RECT.

```
operator RECT();
```

### <a name="return-value"></a>Valor devuelto

Valor actual del rectángulo de animación como RECT.

### <a name="remarks"></a>Observaciones

Esta función llama internamente a GetValue. Si se produce un error en GetValue por algún motivo, el RECT devuelto contendrá valores predeterminados para todas las coordenadas de rectángulo.

## <a name="canimationrectoperator"></a><a name="operator_eq"></a>CAnimationRect::operator ?

Asigna rect a CAnimationRect.

```
void operator=(const RECT& rect);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
El nuevo valor del rectángulo de animación.

### <a name="remarks"></a>Observaciones

Se recomienda hacerlo antes del inicio de la animación, porque este operador llama a SetDefaultValue, que vuelve a crear los objetos COM subyacentes para los componentes de color si se han creado. Si suscribió este objeto de animación a eventos (ValueChanged o IntegerValueChanged), debe volver a habilitar estos eventos.

## <a name="canimationrectsetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationRect::SetDefaultValue

Establece el valor predeterminado.

```
void SetDefaultValue(const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
Especifica nuevos valores predeterminados para izquierda, superior, derecha e inferior.

### <a name="remarks"></a>Observaciones

Utilice esta función para establecer un valor predeterminado en el objeto de animación. Este método asigna valores predeterminados a los límites del rectángulo. También vuelve a crear objetos COM subyacentes si se han creado. Si suscribió este objeto de animación a eventos (ValueChanged o IntegerValueChanged), debe volver a habilitar estos eventos.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
