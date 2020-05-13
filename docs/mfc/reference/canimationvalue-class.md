---
title: Clase CAnimationValue
ms.date: 11/04/2016
f1_keywords:
- CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationValue::GetValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationValue::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationValue::m_value
helpviewer_keywords:
- CAnimationValue [MFC], CAnimationValue
- CAnimationValue [MFC], AddTransition
- CAnimationValue [MFC], GetValue
- CAnimationValue [MFC], GetVariable
- CAnimationValue [MFC], SetDefaultValue
- CAnimationValue [MFC], GetAnimationVariableList
- CAnimationValue [MFC], m_value
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
ms.openlocfilehash: e020e3e123bb5dc96a623e7a41896d75c611b81e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755076"
---
# <a name="canimationvalue-class"></a>Clase CAnimationValue

Implementa la funcionalidad del objeto de animación que tiene un valor.

## <a name="syntax"></a>Sintaxis

```
class CAnimationValue : public CAnimationBaseObject;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationValue::CAnimationValue](#canimationvalue)|Sobrecargado. Construye un CAnimationValue objeto.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationValue::AddTransition](#addtransition)|Agrega una transición que se aplicará a un valor.|
|[CAnimationValue::GetValue](#getvalue)|Sobrecargado. Recupera el valor actual.|
|[CAnimationValue::GetVariable](#getvariable)|Proporciona acceso a la variable de animación encapsulada.|
|[CAnimationValue::SetDefaultValue](#setdefaultvalue)|Establece el valor predeterminado.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationValue::GetAnimationVariableList](#getanimationvariablelist)|Coloca la variable de animación encapsulada en una lista. (Reemplaza [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationValue::operator DOUBLE](#operator_double)|Proporciona la conversión entre CAnimationValue y DOUBLE.|
|[CAnimationValue::operator INT32](#operator_int32)|Proporciona la conversión entre CAnimationValue e INT32.|
|[CAnimationValue::operator ?](#operator_eq)|Sobrecargado. Asigna un valor INT32 a CAnimationValue.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationValue::m_value](#m_value)|Variable de animación encapsulada que representa el valor de animación.|

## <a name="remarks"></a>Observaciones

La clase CAnimationValue encapsula un único objeto CAnimationVariable y puede representar en aplicaciones un único valor animado. Por ejemplo, puede utilizar esta clase para la transparencia animada (efecto de fundido), el ángulo (para rotar objetos) o para cualquier otro caso cuando necesite crear una animación en función de un único valor animado. Para usar esta clase en la aplicación, simplemente cree una instancia de un objeto de esta clase, agréguelo al controlador de animación mediante CAnimationController::AddAnimationObject y llame a AddTransition para cada transición que se aplicará al valor.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationValue`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="canimationvalueaddtransition"></a><a name="addtransition"></a>CAnimationValue::AddTransition

Agrega una transición que se aplicará a un valor.

```cpp
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>Parámetros

*pTransición*<br/>
Puntero al objeto de transición.

### <a name="remarks"></a>Observaciones

Llame a esta función para agregar una transición a la lista interna de transiciones que se aplicarán a una variable de animación. Cuando se agregan transiciones, no se aplican inmediatamente y se almacenan en una lista interna. Las transiciones se aplican (se agregan a un guión gráfico para un valor determinado) cuando se llama a CAnimationController::AnimateGroup.

## <a name="canimationvaluecanimationvalue"></a><a name="canimationvalue"></a>CAnimationValue::CAnimationValue

Construye un CAnimationValue objeto.

```
CAnimationValue();

CAnimationValue(
    DOUBLE dblDefaultValue,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parámetros

*dblDefaultValue*<br/>
Especifica el valor predeterminado.

*nGroupID*<br/>
Especifica el identificador de grupo.

*nObjectID*<br/>
Especifica el identificador de objeto.

*dwUserData*<br/>
especifica los datos definidos por el usuario.

### <a name="remarks"></a>Observaciones

Construye CAnimationValue objeto con propiedades predeterminadas: valor predeterminado, ID de grupo e ID de objeto se establecen en 0.

## <a name="canimationvaluegetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationValue::GetAnimationVariableList

Coloca la variable de animación encapsulada en una lista.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parámetros

*Lst*<br/>
Cuando se devuelve la función, contiene un puntero a CAnimationVariable que representa el valor animado.

## <a name="canimationvaluegetvalue"></a><a name="getvalue"></a>CAnimationValue::GetValue

Recupera el valor actual.

```
BOOL GetValue(DOUBLE& dblValue);
BOOL GetValue(INT32& nValue);
```

### <a name="parameters"></a>Parámetros

*dblValue*<br/>
Salida. Cuando la función devuelve, contiene un valor actual de la variable de animación.

*nValor*<br/>
Salida. Cuando la función devuelve, contiene un valor actual de la variable de animación.

### <a name="return-value"></a>Valor devuelto

TRUESi el valor actual se recuperó correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Llame a esta función para recuperar el valor actual. Esta implementación llama al objeto COM encapsulado y, si se produce un error en la llamada, este método devuelve el valor predeterminado que se estableció anteriormente en el constructor o con SetDefaultValue.

## <a name="canimationvaluegetvariable"></a><a name="getvariable"></a>CAnimationValue::GetVariable

Proporciona acceso a la variable de animación encapsulada.

```
CAnimationVariable& GetVariable();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a la variable de animación encapsulada.

### <a name="remarks"></a>Observaciones

Utilice este método para tener acceso a la variable de animación encapsulada. Desde CAnimationVariable se obtiene acceso al objeto IUIAnimationVariable subyacente, cuyo puntero puede ser NULL si no se ha creado la variable de animación.

## <a name="canimationvaluem_value"></a><a name="m_value"></a>CAnimationValue::m_value

Variable de animación encapsulada que representa el valor de animación.

```
CAnimationVariable m_value;
```

## <a name="canimationvalueoperator-double"></a><a name="operator_double"></a>CAnimationValue::operator DOUBLE

Proporciona la conversión entre CAnimationValue y DOUBLE.

```
operator DOUBLE();
```

### <a name="return-value"></a>Valor devuelto

Valor actual de Valor de animación.

### <a name="remarks"></a>Observaciones

Proporciona la conversión entre CAnimationValue y DOUBLE. Este método llama internamente a GetValue y no comprueba si hay errores. Si se produce un error en GetValue, el valor devuelto contendrá un valor predeterminado establecido previamente en el constructor o con SetDefaultValue.

## <a name="canimationvalueoperator-int32"></a><a name="operator_int32"></a>CAnimationValue::operator INT32

Proporciona la conversión entre CAnimationValue e INT32.

```
operator INT32();
```

### <a name="return-value"></a>Valor devuelto

Valor actual de Valor de animación como entero.

### <a name="remarks"></a>Observaciones

Proporciona la conversión entre CAnimationValue e INT32. Este método llama internamente a GetValue y no comprueba si hay errores. Si se produce un error en GetValue, el valor devuelto contendrá un valor predeterminado establecido previamente en el constructor o con SetDefaultValue.

## <a name="canimationvalueoperator"></a><a name="operator_eq"></a>CAnimationValue::operator ?

Asigna un valor DOUBLE a CAnimationValue.

```cpp
void operator=(DOUBLE dblVal);
void operator=(INT32 nVal);
```

### <a name="parameters"></a>Parámetros

*dblVal*<br/>
Especifica el valor que se asignará al valor de animación.

*nVal*<br/>
Especifica el valor que se asignará al valor de animación.

### <a name="remarks"></a>Observaciones

Asigna un valor DOUBLE a CAnimationValue. Este valor se establece como valor predeterminado para la variable de animación encapsulada. Si suscribió este objeto de animación a eventos (ValueChanged o IntegerValueChanged), debe volver a habilitar estos eventos.

## <a name="canimationvaluesetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationValue::SetDefaultValue

Establece el valor predeterminado.

```cpp
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>Parámetros

*dblDefaultValue*<br/>
Especifica el valor predeterminado.

### <a name="remarks"></a>Observaciones

Utilice este método para establecer un valor predeterminado. Se devuelve un valor predeterminado a la aplicación cuando no se ha iniciado la animación o no se ha creado el objeto COM subyacente. Si el objeto COM subyacente encapsulado en CAnimationVarible ya se creó, este método lo vuelve a crear, por lo tanto, es posible que deba llamar a EnableValueChanged/EnableIntegerValueChanged métodos de nuevo.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
