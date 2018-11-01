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
ms.openlocfilehash: 4e782a9325360b69e33dfaf6a3b0649d9368b32b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540184"
---
# <a name="canimationrect-class"></a>Clase CAnimationRect

Implementa la funcionalidad de un rectángulo cuyos lados se pueden animar.

## <a name="syntax"></a>Sintaxis

```
class CAnimationRect : public CAnimationBaseObject;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationRect::CAnimationRect](#canimationrect)|Sobrecargado. Construye un objeto rect de animación.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationRect::AddTransition](#addtransition)|Agrega las transiciones de coordenadas de la izquierda, superior, derecho e inferior.|
|[CAnimationRect::GetBottom](#getbottom)|Proporciona acceso a CAnimationVariable que representa la coordenada inferior.|
|[CAnimationRect::GetDefaultValue](#getdefaultvalue)|Devuelve los valores predeterminados para los límites del rectángulo.|
|[CAnimationRect::GetLeft](#getleft)|Proporciona acceso a CAnimationVariable que representa la coordenada izquierda.|
|[CAnimationRect::GetRight](#getright)|Proporciona acceso a CAnimationVariable que representa la coordenada derecha.|
|[CAnimationRect::GetTop](#gettop)|Proporciona acceso a CAnimationVariable que representa la coordenada superior.|
|[CAnimationRect::GetValue](#getvalue)|Devuelve el valor actual.|
|[CAnimationRect::SetDefaultValue](#setdefaultvalue)|Establece el valor predeterminado.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CAnimationRect::GetAnimationVariableList](#getanimationvariablelist)|Coloca las variables de animación encapsulado en una lista. (Invalida [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationRect::operator RECT](#operator_rect)|Convierte un CAnimationRect al objeto Rect.|
|[CAnimationRect::operator =](#operator_eq)|Asigna rect a CAnimationRect.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationRect::m_bFixedSize](#m_bfixedsize)|Especifica si el rectángulo de tamaño fijo.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|nombre|Descripción|
|----------|-----------------|
|[CAnimationRect::m_bottomValue](#m_bottomvalue)|Enlaza la variable de animación encapsulado que representa la parte inferior del rectángulo de animación.|
|[CAnimationRect::m_leftValue](#m_leftvalue)|Enlaza la variable de animación encapsulado que representa la izquierda del rectángulo de animación.|
|[CAnimationRect::m_rightValue](#m_rightvalue)|Enlaza la variable de animación encapsulado que representa el derecho del rectángulo de animación.|
|[CAnimationRect::m_szInitial](#m_szinitial)|Especifica el tamaño inicial del rectángulo de animación.|
|[CAnimationRect::m_topValue](#m_topvalue)|Enlaza la variable de animación encapsulado que representa la parte superior del rectángulo de animación.|

## <a name="remarks"></a>Comentarios

La clase CAnimationRect encapsula los cuatro objetos CAnimationVariable y puede representar en aplicaciones de un rectángulo. Para usar esta clase en la aplicación, simplemente cree una instancia de un objeto de esta clase, agréguelo al controlador de animación mediante CAnimationController::AddAnimationObject y llamar a AddTransition para cada transición que se aplicará a las coordenadas de la parte superior e inferior izquierdas, derecha.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationRect`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationRect::AddTransition

Agrega las transiciones de coordenadas de la izquierda, superior, derecho e inferior.

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
Especifica la transición para el lado superior.

*pRightTransition*<br/>
Especifica la transición para el lado derecho.

*pBottomTransition*<br/>
Especifica la transición para el lado inferior.

### <a name="remarks"></a>Comentarios

Llame a esta función para agregar las transiciones especificadas a la lista interna de las transiciones que se aplicará a las variables de animación de los lados del rectángulo. Al agregar transiciones, no se aplican inmediatamente y almacenan en una lista interna. Las transiciones se aplican (agregado a un guión gráfico para un determinado valor) cuando se llama a CAnimationController::AnimateGroup. Si no tiene que aplicar una transición a uno de los lados del rectángulo, puede pasar NULL.

##  <a name="canimationrect"></a>  CAnimationRect::CAnimationRect

Construye un objeto CAnimationRect.

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
Especifica el rectángulo del predeterminado.

*nGroupID*<br/>
Especifica el identificador de grupo.

*nObjectID*<br/>
Especifica el identificador de objeto.

*dwUserData*<br/>
Especifica los datos definidos por el usuario.

*PT*<br/>
Coordenada de la esquina superior izquierda.

*sz*<br/>
Tamaño del rectángulo.

*nLeft*<br/>
Especifica la coordenada del límite izquierdo.

*nTop*<br/>
Especifica la coordenada del límite superior.

*nRight*<br/>
Especifica la coordenada del límite derecho.

*nBottom*<br/>
Especifica la coordenada del límite inferior.

### <a name="remarks"></a>Comentarios

Se construye el objeto con valores predeterminados de la izquierda, superior, derecho e inferior, Id. de objeto y el identificador de grupo, que se establecerá en 0. Puede cambiar posteriormente en tiempo de ejecución mediante SetDefaultValue y SetID.

##  <a name="getanimationvariablelist"></a>  CAnimationRect::GetAnimationVariableList

Coloca las variables de animación encapsulado en una lista.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parámetros

*lst*<br/>
Cuando la función devuelve, contiene punteros a cuatro objetos CAnimationVariable que representa las coordenadas del rectángulo.

##  <a name="getbottom"></a>  CAnimationRect::GetBottom

Proporciona acceso a CAnimationVariable que representa la coordenada inferior.

```
CAnimationVariable& GetBottom();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a CAnimationVariable encapsulado que representa la coordenada inferior.

### <a name="remarks"></a>Comentarios

Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa la coordenada de la parte inferior.

##  <a name="getdefaultvalue"></a>  CAnimationRect::GetDefaultValue

Devuelve los valores predeterminados para los límites del rectángulo.

```
CRect GetDefaultValue();
```

### <a name="return-value"></a>Valor devuelto

Un valor CRect que contiene los valores predeterminados de la izquierda, derecha, superior e inferior.

### <a name="remarks"></a>Comentarios

Llame a esta función para recuperar el valor predeterminado, que anteriormente se ha establecido mediante el constructor o SetDefaultValue.

##  <a name="getleft"></a>  CAnimationRect::GetLeft

Proporciona acceso a CAnimationVariable que representa la coordenada izquierda.

```
CAnimationVariable& GetLeft();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a CAnimationVariable encapsulado que representa la coordenada izquierda.

### <a name="remarks"></a>Comentarios

Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa la coordenada izquierda.

##  <a name="getright"></a>  CAnimationRect::GetRight

Proporciona acceso a CAnimationVariable que representa la coordenada derecha.

```
CAnimationVariable& GetRight();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a CAnimationVariable encapsulado que representa la coordenada derecha.

### <a name="remarks"></a>Comentarios

Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa la coordenada derecha.

##  <a name="gettop"></a>  CAnimationRect::GetTop

Proporciona acceso a CAnimationVariable que representa la coordenada superior.

```
CAnimationVariable& GetTop();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a CAnimationVariable encapsulado que representa la coordenada superior.

### <a name="remarks"></a>Comentarios

Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa la coordenada superior.

##  <a name="getvalue"></a>  CAnimationRect::GetValue

Devuelve el valor actual.

```
BOOL GetValue(CRect& rect);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
Salida. Cuando este método vuelve, contiene el valor actual.

### <a name="return-value"></a>Valor devuelto

Es TRUE si el valor actual se ha recuperado correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Llame a esta función para recuperar el valor actual del rectángulo de animación. Si este método produce un error o COM subyacente objetos de la izquierda, superior, derecho e inferior no se hayan inicializado, rect contiene el valor predeterminado, que anteriormente se estableció en el constructor o por SetDefaultValue.

##  <a name="m_bfixedsize"></a>  CAnimationRect::m_bFixedSize

Especifica si el rectángulo de tamaño fijo.

```
BOOL m_bFixedSize;
```

### <a name="remarks"></a>Comentarios

Si este miembro es true, el tamaño del rectángulo es fijo y derecho y los valores de la parte inferior se vuelven a calcular cada vez que se mueve la esquina superior izquierda según el tamaño fijo. Establezca este valor en TRUE para mover fácilmente el rectángulo en torno a la pantalla. En este caso se omiten las transiciones que se aplica a las coordenadas de derecho e inferior. El tamaño se almacena internamente cuando se construya el objeto o llamar a SetDefaultValue. De forma predeterminada, este miembro se establece en FALSE.

##  <a name="m_bottomvalue"></a>  CAnimationRect::m_bottomValue

Enlaza la variable de animación encapsulado que representa la parte inferior del rectángulo de animación.

```
CAnimationVariable m_bottomValue;
```

##  <a name="m_leftvalue"></a>  CAnimationRect::m_leftValue

Enlaza la variable de animación encapsulado que representa la izquierda del rectángulo de animación.

```
CAnimationVariable m_leftValue;
```

##  <a name="m_rightvalue"></a>  CAnimationRect::m_rightValue

Enlaza la variable de animación encapsulado que representa el derecho del rectángulo de animación.

```
CAnimationVariable m_rightValue;
```

##  <a name="m_szinitial"></a>  CAnimationRect::m_szInitial

Especifica el tamaño inicial del rectángulo de animación.

```
CSize m_szInitial;
```

##  <a name="m_topvalue"></a>  CAnimationRect::m_topValue

Enlaza la variable de animación encapsulado que representa la parte superior del rectángulo de animación.

```
CAnimationVariable m_topValue;
```

##  <a name="operator_rect"></a>  CAnimationRect::operator RECT

Convierte un CAnimationRect al objeto Rect.

```
operator RECT();
```

### <a name="return-value"></a>Valor devuelto

Valor actual del rectángulo de animación como objeto Rect.

### <a name="remarks"></a>Comentarios

Esta función llama internamente a GetValue. Si se produce un error en GetValue por algún motivo, el rectángulo devuelto contendrá los valores predeterminados para todas las coordenadas del rectángulo.

##  <a name="operator_eq"></a>  CAnimationRect::operator =

Asigna rect a CAnimationRect.

```
void operator=(const RECT& rect);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
El nuevo valor de rectángulo de animación.

### <a name="remarks"></a>Comentarios

Se recomienda hacerlo antes del inicio de la animación, dado que este operador llama a SetDefaultValue, que vuelve a crear los objetos COM subyacentes para los componentes de color si se han creado. Si se ha suscrito a este objeto de animación a eventos (ValueChanged o IntegerValueChanged), deberá volver a habilitar estos eventos.

##  <a name="setdefaultvalue"></a>  CAnimationRect::SetDefaultValue

Establece el valor predeterminado.

```
void SetDefaultValue(const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
Especifica los nuevos valores predeterminados de la izquierda, superior, derecho e inferior.

### <a name="remarks"></a>Comentarios

Utilice esta función para establecer un valor predeterminado para el objeto de animación. Este método asigna los valores predeterminados en los límites del rectángulo. También se vuelve a crear objetos COM subyacentes si se han creado. Si se ha suscrito a este objeto de animación a eventos (ValueChanged o IntegerValueChanged), deberá volver a habilitar estos eventos.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
