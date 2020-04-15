---
title: Clase CAnimationSize
ms.date: 11/04/2016
f1_keywords:
- CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCX
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCY
- AFXANIMATIONCONTROLLER/CAnimationSize::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetValue
- AFXANIMATIONCONTROLLER/CAnimationSize::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cxValue
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cyValue
helpviewer_keywords:
- CAnimationSize [MFC], CAnimationSize
- CAnimationSize [MFC], AddTransition
- CAnimationSize [MFC], GetCX
- CAnimationSize [MFC], GetCY
- CAnimationSize [MFC], GetDefaultValue
- CAnimationSize [MFC], GetValue
- CAnimationSize [MFC], SetDefaultValue
- CAnimationSize [MFC], GetAnimationVariableList
- CAnimationSize [MFC], m_cxValue
- CAnimationSize [MFC], m_cyValue
ms.assetid: ea06d1b5-502c-44a3-82ca-8bd6ba6a9364
ms.openlocfilehash: 80a90dfa37bc1d2c3c84e6451ae23af7ded767c2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369699"
---
# <a name="canimationsize-class"></a>Clase CAnimationSize

Implementa la funcionalidad de un objeto cuyas dimensiones se pueden animar.

## <a name="syntax"></a>Sintaxis

```
class CAnimationSize : public CAnimationBaseObject;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationSize::CAnimationSize](#canimationsize)|Sobrecargado. Construye un objeto de tamaño de animación.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationSize::AddTransition](#addtransition)|Agrega transiciones para Anchura y Altura.|
|[CAnimationSize::GetCX](#getcx)|Proporciona acceso a CAnimationVariable que representa Width.|
|[CAnimationSize::GetCY](#getcy)|Proporciona acceso a CAnimationVariable que representa Height.|
|[CAnimationSize::GetDefaultValue](#getdefaultvalue)|Devuelve los valores predeterminados de Width y Height.|
|[CAnimationSize::GetValue](#getvalue)|Devuelve el valor actual.|
|[CAnimationSize::SetDefaultValue](#setdefaultvalue)|Establece el valor predeterminado.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationSize::GetAnimationVariableList](#getanimationvariablelist)|Coloca las variables de animación encapsuladas en una lista. (Reemplaza [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationSize::operator CSize](#operator_csize)|Convierte un CAnimationSize en un CSize.|
|[CAnimationSize::operator ?](#operator_eq)|Asigna szSrc a CAnimationSize.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationSize::m_cxValue](#m_cxvalue)|Variable de animación encapsulada que representa el ancho del tamaño de la animación.|
|[CAnimationSize::m_cyValue](#m_cyvalue)|Variable de animación encapsulada que representa el alto del tamaño de la animación.|

## <a name="remarks"></a>Observaciones

La clase CAnimationSize encapsula dos objetos CAnimationVariable y puede representar en aplicaciones un tamaño. Por ejemplo, puede utilizar esta clase para animar un tamaño de cualquier objeto bidimensional en la pantalla (como rectángulo, control, etc.). Para usar esta clase en la aplicación, simplemente cree una instancia de un objeto de esta clase, agréguelo al controlador de animación mediante CAnimationController::AddAnimationObject y llame a AddTransition para cada transición que se aplicará a Width y/o Height.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationSize`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="canimationsizeaddtransition"></a><a name="addtransition"></a>CAnimationSize::AddTransition

Agrega transiciones para Anchura y Altura.

```
void AddTransition(
    CBaseTransition* pCXTransition,
    CBaseTransition* pCYTransition);
```

### <a name="parameters"></a>Parámetros

*pCXTransición*<br/>
Puntero a transición para Ancho.

*pCYTransition*<br/>
Puntero a transición para Altura.

### <a name="remarks"></a>Observaciones

Llame a esta función para agregar las transiciones especificadas a la lista interna de transiciones que se aplicarán a las variables de animación para Width y Height. Cuando se agregan transiciones, no se aplican inmediatamente y se almacenan en una lista interna. Las transiciones se aplican (se agregan a un guión gráfico para un valor determinado) cuando se llama a CAnimationController::AnimateGroup. Si no necesita aplicar una transición a una de las dimensiones, puede pasar NULL.

## <a name="canimationsizecanimationsize"></a><a name="canimationsize"></a>CAnimationSize::CAnimationSize

Construye un objeto de tamaño de animación.

```
CAnimationSize();

CAnimationSize(
    const CSize& szDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parámetros

*szDefault*<br/>
Especifica el tamaño predeterminado.

*nGroupID*<br/>
Especifica el identificador de grupo.

*nObjectID*<br/>
Especifica el identificador de objeto.

*dwUserData*<br/>
Especifica los datos definidos por el usuario.

### <a name="remarks"></a>Observaciones

El objeto se construye con valores predeterminados para width, height, Object ID y Group ID, que se establecerán en 0. Se pueden cambiar más adelante en tiempo de ejecución mediante SetDefaultValue y SetID.

## <a name="canimationsizegetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationSize::GetAnimationVariableList

Coloca las variables de animación encapsuladas en una lista.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parámetros

*Lst*<br/>
Cuando se devuelve la función, contiene punteros a dos CAnimationVariable objetos que representan el ancho y alto.

## <a name="canimationsizegetcx"></a><a name="getcx"></a>CAnimationSize::GetCX

Proporciona acceso a CAnimationVariable que representa Width.

```
CAnimationVariable& GetCX();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a encapsulado CAnimationVariable que representa Width.

### <a name="remarks"></a>Observaciones

Puede llamar a este método para obtener acceso directo a subyacente CAnimationVariable que representa Width.

## <a name="canimationsizegetcy"></a><a name="getcy"></a>CAnimationSize::GetCY

Proporciona acceso a CAnimationVariable que representa Height.

```
CAnimationVariable& GetCY();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a encapsulado CAnimationVariable que representa Height.

### <a name="remarks"></a>Observaciones

Puede llamar a este método para obtener acceso directo a subyacente CAnimationVariable que representa Height.

## <a name="canimationsizegetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationSize::GetDefaultValue

Devuelve los valores predeterminados de Width y Height.

```
CSize GetDefaultValue();
```

### <a name="return-value"></a>Valor devuelto

Un CSize objeto que contiene valores predeterminados.

### <a name="remarks"></a>Observaciones

Llame a esta función para recuperar el valor predeterminado, que se estableció previamente por constructor o SetDefaultValue.

## <a name="canimationsizegetvalue"></a><a name="getvalue"></a>CAnimationSize::GetValue

Devuelve el valor actual.

```
BOOL GetValue(CSize& szValue);
```

### <a name="parameters"></a>Parámetros

*szValue*<br/>
Salida. Contiene el valor actual cuando se devuelve este método.

### <a name="return-value"></a>Valor devuelto

TRUE, si el valor actual se recuperó correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Llame a esta función para recuperar el valor actual del tamaño de la animación. Si se produce un error en este método o no se han inicializado los objetos COM subyacentes para Width y Size, szValue contiene el valor predeterminado, que se estableció anteriormente en el constructor o por SetDefaultValue.

## <a name="canimationsizem_cxvalue"></a><a name="m_cxvalue"></a>CAnimationSize::m_cxValue

Variable de animación encapsulada que representa el ancho del tamaño de la animación.

```
CAnimationVariable m_cxValue;
```

## <a name="canimationsizem_cyvalue"></a><a name="m_cyvalue"></a>CAnimationSize::m_cyValue

Variable de animación encapsulada que representa el alto del tamaño de la animación.

```
CAnimationVariable m_cyValue;
```

## <a name="canimationsizeoperator-csize"></a><a name="operator_csize"></a>CAnimationSize::operator CSize

Convierte un CAnimationSize en un CSize.

```
operator CSize();
```

### <a name="return-value"></a>Valor devuelto

Valor actual del tamaño de la animación como CSize.

### <a name="remarks"></a>Observaciones

Esta función llama internamente a GetValue. Si se produce un error en GetValue por algún motivo, el tamaño devuelto contendrá los valores predeterminados de Width y Height.

## <a name="canimationsizeoperator"></a><a name="operator_eq"></a>CAnimationSize::operator ?

Asigna szSrc a CAnimationSize.

```
void operator=(const CSize& szSrc);
```

### <a name="parameters"></a>Parámetros

*szSrc*<br/>
Hace referencia a CSize o SIZE.

### <a name="remarks"></a>Observaciones

Asigna szSrc a CAnimationSize. Se recomienda hacerlo antes del inicio de la animación, porque este operador llama a SetDefaultValue, que vuelve a crear los objetos COM subyacentes para Width y Height si se han creado. Si suscribió este objeto de animación a eventos (ValueChanged o IntegerValueChanged), debe volver a habilitar estos eventos.

## <a name="canimationsizesetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationSize::SetDefaultValue

Establece el valor predeterminado.

```
void SetDefaultValue(const CSize& szDefault);
```

### <a name="parameters"></a>Parámetros

*szDefault*<br/>
Especifica el nuevo tamaño predeterminado.

### <a name="remarks"></a>Observaciones

Utilice esta función para establecer un valor predeterminado en el objeto de animación. Este método asigna valores predeterminados a Width y Height de tamaño de animación. También vuelve a crear objetos COM subyacentes si se han creado. Si suscribió este objeto de animación a eventos (ValueChanged o IntegerValueChanged), debe volver a habilitar estos eventos.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
