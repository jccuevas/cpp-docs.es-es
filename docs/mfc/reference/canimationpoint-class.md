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
ms.openlocfilehash: 19f02010b6b73573a4800152e40c592fd1736ad5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369733"
---
# <a name="canimationpoint-class"></a>Clase CAnimationPoint

Implementa la funcionalidad de un punto cuyas coordenadas se pueden animar.

## <a name="syntax"></a>Sintaxis

```
class CAnimationPoint : public CAnimationBaseObject;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationPoint::CAnimationPoint](#canimationpoint)|Sobrecargado. Construye CAnimationPoint objeto.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationPoint::AddTransition](#addtransition)|Añade transiciones para las coordenadas X e Y.|
|[CAnimationPoint::GetDefaultValue](#getdefaultvalue)|Devuelve los valores predeterminados para las coordenadas X e Y.|
|[CAnimationPoint::GetValue](#getvalue)|Devuelve el valor actual.|
|[CAnimationPoint::GetX](#getx)|Proporciona acceso a CAnimationVariable para la coordenada X.|
|[CAnimationPoint::GetY](#gety)|Proporciona acceso a CAnimationVariable para la coordenada Y.|
|[CAnimationPoint::SetDefaultValue](#setdefaultvalue)|Establece el valor predeterminado.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationPoint::GetAnimationVariableList](#getanimationvariablelist)|Coloca las variables de animación encapsuladas en una lista. (Reemplaza [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationPoint::operator CPoint](#operator_cpoint)|Convierte un CAnimationPoint en un CPoint.|
|[CAnimationPoint::operador ?](#operator_eq)|Asigna ptSrc a CAnimationPoint.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationPoint::m_xValue](#m_xvalue)|Variable de animación encapsulada que representa la coordenada X del punto de animación.|
|[CAnimationPoint::m_yValue](#m_yvalue)|La variable de animación encapsulada que representa la coordenada Y del punto de animación.|

## <a name="remarks"></a>Observaciones

La clase CAnimationPoint encapsula dos objetos CAnimationVariable y puede representar en aplicaciones un punto. Por ejemplo, puede utilizar esta clase para animar una posición de cualquier objeto en la pantalla (como cadena de texto, círculo, punto, etc.). Para usar esta clase en la aplicación, simplemente cree una instancia de un objeto de esta clase, agréguelo al controlador de animación mediante CAnimationController::AddAnimationObject y llame a AddTransition para cada transición que se aplicará a las coordenadas X o Y.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationPoint`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="canimationpointaddtransition"></a><a name="addtransition"></a>CAnimationPoint::AddTransition

Añade transiciones para las coordenadas X e Y.

```
void AddTransition(
    CBaseTransition* pXTransition,
    CBaseTransition* pYTransition);
```

### <a name="parameters"></a>Parámetros

*pXTransition*<br/>
Puntero a transición para coordenadas X.

*pYTransition*<br/>
Un puntero a la transición para la coordenada Y.

### <a name="remarks"></a>Observaciones

Llame a esta función para agregar las transiciones especificadas a la lista interna de transiciones que se aplicarán a las variables de animación para las coordenadas X e Y. Cuando se agregan transiciones, no se aplican inmediatamente y se almacenan en una lista interna. Las transiciones se aplican (se agregan a un guión gráfico para un valor determinado) cuando se llama a CAnimationController::AnimateGroup. Si no necesita aplicar una transición a una de las coordenadas, puede pasar NULL.

## <a name="canimationpointcanimationpoint"></a><a name="canimationpoint"></a>CAnimationPoint::CAnimationPoint

Construye CAnimationPoint objeto.

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
Especifica las coordenadas de punto predeterminadas.

*nGroupID*<br/>
Especifica el identificador de grupo.

*nObjectID*<br/>
Especifica el identificador de objeto.

*dwUserData*<br/>
Especifica los datos definidos por el usuario.

### <a name="remarks"></a>Observaciones

Construye CAnimationPoint objeto con propiedades predeterminadas: coordenadas de punto predeterminadas, ID de grupo e ID de objeto se establecen en 0.

## <a name="canimationpointgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationPoint::GetAnimationVariableList

Coloca las variables de animación encapsuladas en una lista.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parámetros

*Lst*<br/>
Cuando se devuelve la función, contiene punteros a dos CAnimationVariable objetos que representan las coordenadas X e Y.

## <a name="canimationpointgetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationPoint::GetDefaultValue

Devuelve los valores predeterminados para las coordenadas X e Y.

```
CPoint GetDefaultValue();
```

### <a name="return-value"></a>Valor devuelto

Un punto que contiene el valor predeterminado.

### <a name="remarks"></a>Observaciones

Llame a esta función para recuperar el valor predeterminado, que se estableció previamente por constructor o SetDefaultValue.

## <a name="canimationpointgetvalue"></a><a name="getvalue"></a>CAnimationPoint::GetValue

Devuelve el valor actual.

```
BOOL GetValue(CPoint& ptValue);
```

### <a name="parameters"></a>Parámetros

*ptValue*<br/>
Salida. Contiene el valor actual cuando se devuelve este método.

### <a name="return-value"></a>Valor devuelto

TRUE, si el valor actual se recuperó correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Llame a esta función para recuperar el valor actual del punto de animación. Si se produce un error en este método o no se han inicializado los objetos COM subyacentes para las coordenadas X e Y, ptValue contiene el valor predeterminado, que se estableció anteriormente en el constructor o por SetDefaultValue.

## <a name="canimationpointgetx"></a><a name="getx"></a>CAnimationPoint::GetX

Proporciona acceso a CAnimationVariable para la coordenada X.

```
CAnimationVariable& GetX();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a encapsulado CAnimationVariable que representa X coordenada.

### <a name="remarks"></a>Observaciones

Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa X coordenada.

## <a name="canimationpointgety"></a><a name="gety"></a>CAnimationPoint::GetY

Proporciona acceso a CAnimationVariable para la coordenada Y.

```
CAnimationVariable& GetY();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a encapsulado CAnimationVariable que representa y coordenadas.

### <a name="remarks"></a>Observaciones

Puede llamar a este método para obtener acceso directo a subyacente CAnimationVariable que representa y coordenadas.

## <a name="canimationpointm_xvalue"></a><a name="m_xvalue"></a>CAnimationPoint::m_xValue

Variable de animación encapsulada que representa la coordenada X del punto de animación.

```
CAnimationVariable m_xValue;
```

## <a name="canimationpointm_yvalue"></a><a name="m_yvalue"></a>CAnimationPoint::m_yValue

La variable de animación encapsulada que representa la coordenada Y del punto de animación.

```
CAnimationVariable m_yValue;
```

## <a name="canimationpointoperator-cpoint"></a><a name="operator_cpoint"></a>CAnimationPoint::operator CPoint

Convierte un CAnimationPoint en un CPoint.

```
operator CPoint();
```

### <a name="return-value"></a>Valor devuelto

Valor actual de CAnimationPoint como CPoint.

### <a name="remarks"></a>Observaciones

Esta función llama internamente a GetValue. Si se produce un error en GetValue por algún motivo, el punto devuelto contendrá valores predeterminados para las coordenadas X e Y.

## <a name="canimationpointoperator"></a><a name="operator_eq"></a>CAnimationPoint::operador ?

Asigna ptSrc a CAnimationPoint.

```
void operator=(const CPoint& ptSrc);
```

### <a name="parameters"></a>Parámetros

*ptSrc*<br/>
Se refiere a CPoint o POINT.

### <a name="remarks"></a>Observaciones

Asigna ptSrc a CAnimationPoint. Se recomienda hacerlo antes del inicio de la animación, porque este operador llama a SetDefaultValue, que vuelve a crear los objetos COM subyacentes para las coordenadas X e Y si se han creado. Si suscribió este objeto de animación a eventos (ValueChanged o IntegerValueChanged), debe volver a habilitar estos eventos.

## <a name="canimationpointsetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationPoint::SetDefaultValue

Establece el valor predeterminado.

```
void SetDefaultValue(const POINT& ptDefault);
```

### <a name="parameters"></a>Parámetros

*ptDefault*<br/>
Especifica el valor de punto predeterminado.

### <a name="remarks"></a>Observaciones

Utilice esta función para establecer un valor predeterminado en el objeto de animación. Este método asigna valores predeterminados a las coordenadas X e Y del punto de animación. También vuelve a crear objetos COM subyacentes si se han creado. Si suscribió este objeto de animación a eventos (ValueChanged o IntegerValueChanged), debe volver a habilitar estos eventos.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
