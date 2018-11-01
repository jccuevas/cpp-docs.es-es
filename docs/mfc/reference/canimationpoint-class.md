---
title: Clase CAnimationPoint
ms.date: 11/04/2016
f1_keywords:
- CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetX
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetY
- AFXANIMATIONCONTROLLER/CAnimationPoint::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_xValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_yValue
helpviewer_keywords:
- CAnimationPoint [MFC], CAnimationPoint
- CAnimationPoint [MFC], AddTransition
- CAnimationPoint [MFC], GetDefaultValue
- CAnimationPoint [MFC], GetValue
- CAnimationPoint [MFC], GetX
- CAnimationPoint [MFC], GetY
- CAnimationPoint [MFC], SetDefaultValue
- CAnimationPoint [MFC], GetAnimationVariableList
- CAnimationPoint [MFC], m_xValue
- CAnimationPoint [MFC], m_yValue
ms.assetid: 5dc4d46f-e695-4681-b15c-544b78b3e317
ms.openlocfilehash: 15f18a43fcda76bb5531434de84d97a349cb7f39
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497207"
---
# <a name="canimationpoint-class"></a>Clase CAnimationPoint

Implementa la funcionalidad de un punto cuyas coordenadas se pueden animar.

## <a name="syntax"></a>Sintaxis

```
class CAnimationPoint : public CAnimationBaseObject;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationPoint::CAnimationPoint](#canimationpoint)|Sobrecargado. Construye el objeto CAnimationPoint.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationPoint::AddTransition](#addtransition)|Agrega las transiciones de X y coordenadas.|
|[CAnimationPoint::GetDefaultValue](#getdefaultvalue)|Devuelve los valores predeterminados para X y coordenadas.|
|[CAnimationPoint::GetValue](#getvalue)|Devuelve el valor actual.|
|[CAnimationPoint::GetX](#getx)|Proporciona acceso a CAnimationVariable para la coordenada X.|
|[CAnimationPoint::GetY](#gety)|Proporciona acceso a CAnimationVariable para la coordenada Y.|
|[CAnimationPoint::SetDefaultValue](#setdefaultvalue)|Establece el valor predeterminado.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CAnimationPoint::GetAnimationVariableList](#getanimationvariablelist)|Coloca las variables de animación encapsulado en una lista. (Invalida [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CPoint CAnimationPoint::operator](#operator_cpoint)|Convierte un CAnimationPoint CPoint.|
|[CAnimationPoint::operator =](#operator_eq)|Asigna ptSrc a CAnimationPoint.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|nombre|Descripción|
|----------|-----------------|
|[CAnimationPoint::m_xValue](#m_xvalue)|La variable de animación encapsulado que representa la X coordenadas del punto de la animación.|
|[CAnimationPoint::m_yValue](#m_yvalue)|La variable de animación encapsulado que representa la coordenada Y del punto de la animación.|

## <a name="remarks"></a>Comentarios

La clase CAnimationPoint encapsula los dos objetos CAnimationVariable y las aplicaciones puede representar un punto. Por ejemplo, puede usar esta clase para animar la posición de cualquier objeto en la pantalla (por ejemplo, la cadena de texto, círculo, etcetera punto). Para usar esta clase en la aplicación, simplemente crear una instancia de un objeto de esta clase, agréguelo al controlador de animación mediante CAnimationController::AddAnimationObject y llamar a AddTransition para cada transición que se aplicará a las coordenadas X o Y.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationPoint`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationPoint::AddTransition

Agrega las transiciones de X y coordenadas.

```
void AddTransition(
    CBaseTransition* pXTransition,
    CBaseTransition* pYTransition);
```

### <a name="parameters"></a>Parámetros

*pXTransition*<br/>
Puntero a la transición de las coordenadas X.

*pYTransition*<br/>
Puntero a la transición y coordinar.

### <a name="remarks"></a>Comentarios

Llame a esta función para agregar las transiciones especificadas a la lista interna de las transiciones que se aplicará a las variables de animación para X y coordenadas. Al agregar transiciones, no se aplican inmediatamente y almacenan en una lista interna. Las transiciones se aplican (agregado a un guión gráfico para un determinado valor) cuando se llama a CAnimationController::AnimateGroup. Si no tiene que aplicar una transición a una de las coordenadas, puede pasar NULL.

##  <a name="canimationpoint"></a>  CAnimationPoint::CAnimationPoint

Construye el objeto CAnimationPoint.

```
CAnimationPoint();

CAnimationPoint(
    const CPoint& ptDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parámetros

*ptDefault*<br/>
Especifica las coordenadas del punto de forma predeterminada.

*nGroupID*<br/>
Especifica el identificador de grupo.

*nObjectID*<br/>
Especifica el identificador de objeto.

*dwUserData*<br/>
Especifica los datos definidos por el usuario.

### <a name="remarks"></a>Comentarios

Construye el objeto CAnimationPoint con propiedades predeterminadas: las coordenadas del punto de predeterminado, Id. de grupo y el Id. de objeto se establecen en 0.

##  <a name="getanimationvariablelist"></a>  CAnimationPoint::GetAnimationVariableList

Coloca las variables de animación encapsulado en una lista.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parámetros

*lst*<br/>
Cuando la función devuelve, contiene punteros a dos objetos CAnimationVariable que representa las coordenadas X e Y.

##  <a name="getdefaultvalue"></a>  CAnimationPoint::GetDefaultValue

Devuelve los valores predeterminados para X y coordenadas.

```
CPoint GetDefaultValue();
```

### <a name="return-value"></a>Valor devuelto

Un valor de punto de contenedor predeterminado.

### <a name="remarks"></a>Comentarios

Llame a esta función para recuperar el valor predeterminado, que anteriormente se ha establecido mediante el constructor o SetDefaultValue.

##  <a name="getvalue"></a>  CAnimationPoint::GetValue

Devuelve el valor actual.

```
BOOL GetValue(CPoint& ptValue);
```

### <a name="parameters"></a>Parámetros

*ptValue*<br/>
Salida. Cuando este método vuelve, contiene el valor actual.

### <a name="return-value"></a>Valor devuelto

Es TRUE si el valor actual se ha recuperado correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Llame a esta función para recuperar el valor actual del punto de la animación. Si este método produce un error o COM subyacente de objetos para X y coordenadas Y no se hayan inicializado, ptValue contiene el valor predeterminado, que anteriormente se estableció en el constructor o por SetDefaultValue.

##  <a name="getx"></a>  CAnimationPoint::GetX

Proporciona acceso a CAnimationVariable para la coordenada X.

```
CAnimationVariable& GetX();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a CAnimationVariable encapsulado que representa la X de coordenadas.

### <a name="remarks"></a>Comentarios

Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa la X de coordenadas.

##  <a name="gety"></a>  CAnimationPoint::GetY

Proporciona acceso a CAnimationVariable para la coordenada Y.

```
CAnimationVariable& GetY();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a CAnimationVariable encapsulado que representa la coordenada Y.

### <a name="remarks"></a>Comentarios

Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa la coordenada Y.

##  <a name="m_xvalue"></a>  CAnimationPoint::m_xValue

La variable de animación encapsulado que representa la X coordenadas del punto de la animación.

```
CAnimationVariable m_xValue;
```

##  <a name="m_yvalue"></a>  CAnimationPoint::m_yValue

La variable de animación encapsulado que representa la coordenada Y del punto de la animación.

```
CAnimationVariable m_yValue;
```

##  <a name="operator_cpoint"></a>  CPoint CAnimationPoint::operator

Convierte un CAnimationPoint CPoint.

```
operator CPoint();
```

### <a name="return-value"></a>Valor devuelto

Valor actual de CAnimationPoint como CPoint.

### <a name="remarks"></a>Comentarios

Esta función llama internamente a GetValue. Si se produce un error en GetValue por algún motivo, el punto devuelto contendrá los valores predeterminados para X y coordenadas.

##  <a name="operator_eq"></a>  CAnimationPoint::operator =

Asigna ptSrc a CAnimationPoint.

```
void operator=(const CPoint& ptSrc);
```

### <a name="parameters"></a>Parámetros

*ptSrc*<br/>
Hace referencia a CPoint o punto.

### <a name="remarks"></a>Comentarios

Asigna ptSrc a CAnimationPoint. Se recomienda hacer que antes del inicio de la animación, dado que este operador llama a SetDefaultValue, que vuelve a crear el COM subyacente objetos para coordenadas X e Y si se han creado. Si se ha suscrito a este objeto de animación a eventos (ValueChanged o IntegerValueChanged), deberá volver a habilitar estos eventos.

##  <a name="setdefaultvalue"></a>  CAnimationPoint::SetDefaultValue

Establece el valor predeterminado.

```
void SetDefaultValue(const POINT& ptDefault);
```

### <a name="parameters"></a>Parámetros

*ptDefault*<br/>
Especifica el valor del punto de forma predeterminada.

### <a name="remarks"></a>Comentarios

Utilice esta función para establecer un valor predeterminado para el objeto de animación. Este predeterminada de los métodos asigna valores a las coordenadas X e Y del punto de la animación. También se vuelve a crear objetos COM subyacentes si se han creado. Si se ha suscrito a este objeto de animación a eventos (ValueChanged o IntegerValueChanged), deberá volver a habilitar estos eventos.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
