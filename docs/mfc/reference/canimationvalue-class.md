---
title: CAnimationValue (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAnimationValue [MFC], CAnimationValue
- CAnimationValue [MFC], AddTransition
- CAnimationValue [MFC], GetValue
- CAnimationValue [MFC], GetVariable
- CAnimationValue [MFC], SetDefaultValue
- CAnimationValue [MFC], GetAnimationVariableList
- CAnimationValue [MFC], m_value
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 378af608ed9f7498b00563e841521b69a10e0b05
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418286"
---
# <a name="canimationvalue-class"></a>Clase CAnimationValue

Implementa la funcionalidad del objeto de animación que tiene un valor.

## <a name="syntax"></a>Sintaxis

```
class CAnimationValue : public CAnimationBaseObject;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationValue::CAnimationValue](#canimationvalue)|Sobrecargado. Construye un objeto CAnimationValue.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationValue::AddTransition](#addtransition)|Agrega una transición que se aplicará a un valor.|
|[CAnimationValue::GetValue](#getvalue)|Sobrecargado. Recupera el valor actual.|
|[CAnimationValue::GetVariable](#getvariable)|Proporciona acceso a la variable de animación encapsulado.|
|[CAnimationValue::SetDefaultValue](#setdefaultvalue)|Establece el valor predeterminado.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CAnimationValue::GetAnimationVariableList](#getanimationvariablelist)|Coloca la variable de animación encapsulado en una lista. (Invalida [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationValue::operator doble](#operator_double)|Proporciona la conversión entre CAnimationValue y DOUBLE.|
|[CAnimationValue::operator INT32](#operator_int32)|Proporciona la conversión entre CAnimationValue e INT32.|
|[CAnimationValue::operator =](#operator_eq)|Sobrecargado. Asigna un valor INT32 a CAnimationValue.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|nombre|Descripción|
|----------|-----------------|
|[CAnimationValue::m_value](#m_value)|La variable de animación encapsulado que representa el valor de la animación.|

## <a name="remarks"></a>Comentarios

La clase CAnimationValue encapsula un único objeto CAnimationVariable y las aplicaciones puede representar un único valor animado. Por ejemplo, puede usar esta clase para transparencia animado (efecto de atenuación), ángulo (para girar objetos), o para cualquier otro caso, cuando se necesita crear una animación según un único valor animado. Para usar esta clase en la aplicación, simplemente crear una instancia de un objeto de esta clase, agréguelo al controlador de animación mediante CAnimationController::AddAnimationObject y llamar a AddTransition para cada transición que se aplica al valor.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationValue`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationValue::AddTransition

Agrega una transición que se aplicará a un valor.

```
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>Parámetros

*pTransition*<br/>
Un puntero al objeto de transición.

### <a name="remarks"></a>Comentarios

Llame a esta función para agregar una transición a la lista interna de transiciones que se aplicará a una variable de animación. Al agregar transiciones, no se aplican inmediatamente y almacenan en una lista interna. Las transiciones se aplican (agregado a un guión gráfico para un determinado valor) cuando se llama a CAnimationController::AnimateGroup.

##  <a name="canimationvalue"></a>  CAnimationValue::CAnimationValue

Construye un objeto CAnimationValue.

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
Especifica los datos definidos por el usuario.

### <a name="remarks"></a>Comentarios

Construye el objeto CAnimationValue con propiedades predeterminadas: valor predeterminado, Id. de grupo y el Id. de objeto se establecen en 0.

##  <a name="getanimationvariablelist"></a>  CAnimationValue::GetAnimationVariableList

Coloca la variable de animación encapsulado en una lista.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parámetros

*lst*<br/>
Cuando la función devuelve, contiene un puntero a CAnimationVariable que representa el valor animado.

##  <a name="getvalue"></a>  CAnimationValue::GetValue

Recupera el valor actual.

```
BOOL GetValue(DOUBLE& dblValue);
BOOL GetValue(INT32& nValue);
```

### <a name="parameters"></a>Parámetros

*dblValue*<br/>
Salida. Cuando se devuelve la función contiene un valor actual de la variable de animación.

*nvalor*<br/>
Salida. Cuando se devuelve la función contiene un valor actual de la variable de animación.

### <a name="return-value"></a>Valor devuelto

TRUE si el valor actual se recuperó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Llame a esta función para recuperar el valor actual. Esta implementación llama el objeto COM encapsulado y, si se produce un error en la llamada, este método devuelve el valor predeterminado que se configuró anteriormente en el constructor o con SetDefaultValue.

##  <a name="getvariable"></a>  CAnimationValue::GetVariable

Proporciona acceso a la variable de animación encapsulado.

```
CAnimationVariable& GetVariable();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a la variable de animación encapsulado.

### <a name="remarks"></a>Comentarios

Utilice este método para tener acceso a la variable de animación encapsulado. Desde CAnimationVariable obtener acceso al objeto subyacente de IUIAnimationVariable, cuyo puntero puede ser NULL si no se ha creado la variable de animación.

##  <a name="m_value"></a>  CAnimationValue::m_value

La variable de animación encapsulado que representa el valor de la animación.

```
CAnimationVariable m_value;
```

##  <a name="operator_double"></a>  CAnimationValue::operator doble

Proporciona la conversión entre CAnimationValue y DOUBLE.

```
operator DOUBLE();
```

### <a name="return-value"></a>Valor devuelto

Valor actual de animación.

### <a name="remarks"></a>Comentarios

Proporciona la conversión entre CAnimationValue y DOUBLE. Internamente, este método llama GetValue y no compruebe si hay errores. Si se produce un error en GetValue, el valor devuelto contendrá un valor predeterminado establecido previamente en el constructor o con SetDefaultValue.

##  <a name="operator_int32"></a>  CAnimationValue::operator INT32

Proporciona la conversión entre CAnimationValue e INT32.

```
operator INT32();
```

### <a name="return-value"></a>Valor devuelto

Valor actual de animación como entero.

### <a name="remarks"></a>Comentarios

Proporciona la conversión entre CAnimationValue e INT32. Internamente, este método llama GetValue y no compruebe si hay errores. Si se produce un error en GetValue, el valor devuelto contendrá un valor predeterminado establecido previamente en el constructor o con SetDefaultValue.

##  <a name="operator_eq"></a>  CAnimationValue::operator =

Asigna un valor doble a CAnimationValue.

```
void operator=(DOUBLE dblVal);
void operator=(INT32 nVal);
```

### <a name="parameters"></a>Parámetros

*dblVal*<br/>
Especifica el valor que se asignará al valor de la animación.

*nVal*<br/>
Especifica el valor que se asignará al valor de la animación.

### <a name="remarks"></a>Comentarios

Asigna un valor doble a CAnimationValue. Este valor se establece como valor predeterminado para la variable de animación encapsulado. Si se ha suscrito a este objeto de animación a eventos (ValueChanged o IntegerValueChanged), deberá volver a habilitar estos eventos.

##  <a name="setdefaultvalue"></a>  CAnimationValue::SetDefaultValue

Establece el valor predeterminado.

```
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>Parámetros

*dblDefaultValue*<br/>
Especifica el valor predeterminado.

### <a name="remarks"></a>Comentarios

Utilice este método para establecer un valor predeterminado. Se devuelve un valor predeterminado para la aplicación cuando no se inició la animación o no se creó el objeto COM subyacente. Si ya se ha creado el objeto COM subyacente encapsulado en CAnimationVarible, este método vuelve a crear, por lo tanto, es posible que deba llamar a métodos de EnableValueChanged/EnableIntegerValueChanged de nuevo.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
