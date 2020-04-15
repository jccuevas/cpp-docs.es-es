---
title: Clase CAnimationColor
ms.date: 11/04/2016
f1_keywords:
- CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationColor::GetB
- AFXANIMATIONCONTROLLER/CAnimationColor::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetG
- AFXANIMATIONCONTROLLER/CAnimationColor::GetR
- AFXANIMATIONCONTROLLER/CAnimationColor::GetValue
- AFXANIMATIONCONTROLLER/CAnimationColor::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationColor::m_bValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_gValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_rValue
helpviewer_keywords:
- CAnimationColor [MFC], CAnimationColor
- CAnimationColor [MFC], AddTransition
- CAnimationColor [MFC], GetB
- CAnimationColor [MFC], GetDefaultValue
- CAnimationColor [MFC], GetG
- CAnimationColor [MFC], GetR
- CAnimationColor [MFC], GetValue
- CAnimationColor [MFC], SetDefaultValue
- CAnimationColor [MFC], GetAnimationVariableList
- CAnimationColor [MFC], m_bValue
- CAnimationColor [MFC], m_gValue
- CAnimationColor [MFC], m_rValue
ms.assetid: 88bfabd4-efeb-4652-87e8-304253d8e48c
ms.openlocfilehash: 5940cce6d55b95d8e1bac103cacc0bc828c213de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371105"
---
# <a name="canimationcolor-class"></a>Clase CAnimationColor

Implementa la funcionalidad de un color cuyos componentes rojo, verde y azul se pueden animar.

## <a name="syntax"></a>Sintaxis

```
class CAnimationColor : public CAnimationBaseObject;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationColor::CAnimationColor](#canimationcolor)|Sobrecargado. Construye un objeto de color de animación.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationColor::AddTransition](#addtransition)|Añade transiciones para componentes rojos, verdes y azules.|
|[CAnimationColor::GetB](#getb)|Proporciona acceso a CAnimationVariable que representa Blue componente.|
|[CAnimationColor::GetDefaultValue](#getdefaultvalue)|Devuelve los valores predeterminados para los componentes de color.|
|[CAnimationColor::GetG](#getg)|Proporciona acceso a CAnimationVariable que representa el componente Verde.|
|[CAnimationColor::GetR](#getr)|Proporciona acceso a CAnimationVariable que representa el componente Red.|
|[CAnimationColor::GetValue](#getvalue)|Devuelve el valor actual.|
|[CAnimationColor::SetDefaultValue](#setdefaultvalue)|Establece el valor predeterminado.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationColor::GetAnimationVariableList](#getanimationvariablelist)|Coloca las variables de animación encapsuladas en una lista. (Reemplaza [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationColor::operador COLORREF](#operator_colorref)||
|[CAnimationColor::operator ?](#operator_eq)|Asigna color a CAnimationColor.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationColor::m_bValue](#m_bvalue)|Variable de animación encapsulada que representa el componente Azul del color de animación.|
|[CAnimationColor::m_gValue](#m_gvalue)|Variable de animación encapsulada que representa el componente verde del color de animación.|
|[CAnimationColor::m_rValue](#m_rvalue)|Variable de animación encapsulada que representa el componente rojo del color de animación.|

## <a name="remarks"></a>Observaciones

La Clase CAnimationColor encapsula tres objetos CAnimationVariable y puede representar en aplicaciones un color. Por ejemplo, puede utilizar esta clase para animar los colores de cualquier objeto de la pantalla (como el color del texto, el color de fondo, etc.). Para usar esta clase en la aplicación, simplemente cree una instancia de un objeto de esta clase, agréguelo al controlador de animación mediante CAnimationController::AddAnimationObject y llame a AddTransition para cada transición que se aplicará a los componentes rojo, verde y azul.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationColor`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="canimationcoloraddtransition"></a><a name="addtransition"></a>CAnimationColor::AddTransition

Añade transiciones para componentes rojos, verdes y azules.

```
void AddTransition(
    CBaseTransition* pRTransition,
    CBaseTransition* pGTransition,
    CBaseTransition* pBTransition);
```

### <a name="parameters"></a>Parámetros

*pRTransition*<br/>
Transición para el componente Rojo.

*pGTransition*<br/>
Componente Transición para verde.

*pBTransition*<br/>
Componente Transición para azul.

### <a name="remarks"></a>Observaciones

Llame a esta función para agregar las transiciones especificadas a la lista interna de transiciones que se aplicarán a las variables de animación que representan componentes de color. Cuando se agregan transiciones, no se aplican inmediatamente y se almacenan en una lista interna. Las transiciones se aplican (se agregan a un guión gráfico para un valor determinado) cuando se llama a CAnimationController::AnimateGroup. Si no necesita aplicar una transición a uno de los componentes de color, puede pasar NULL.

## <a name="canimationcolorcanimationcolor"></a><a name="canimationcolor"></a>CAnimationColor::CAnimationColor

Construye un CAnimationColor objeto.

```
CAnimationColor();

CAnimationColor(
    COLORREF color,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
Especifica el color predeterminado.

*nGroupID*<br/>
Especifica el identificador de grupo.

*nObjectID*<br/>
Especifica el identificador de objeto.

*dwUserData*<br/>
Especifica los datos definidos por el usuario.

### <a name="remarks"></a>Observaciones

El objeto se construye con valores predeterminados para rojo, verde, azul, ID de objeto e ID de grupo, que se establecerán en 0. Se pueden cambiar más adelante en tiempo de ejecución mediante SetDefaultValue y SetID.

## <a name="canimationcolorgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationColor::GetAnimationVariableList

Coloca las variables de animación encapsuladas en una lista.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parámetros

*Lst*<br/>
Cuando se devuelve la función, contiene punteros a tres CAnimationVariable objetos que representan componentes rojos, verdes y azules.

## <a name="canimationcolorgetb"></a><a name="getb"></a>CAnimationColor::GetB

Proporciona acceso a CAnimationVariable que representa Blue componente.

```
CAnimationVariable& GetB();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a encapsulado CAnimationVariable que representa Blue componente.

### <a name="remarks"></a>Observaciones

Puede llamar a este método para obtener acceso directo al subyacente CAnimationVariable que representa Blue componente.

## <a name="canimationcolorgetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationColor::GetDefaultValue

Devuelve los valores predeterminados para los componentes de color.

```
COLORREF GetDefaultValue();
```

### <a name="return-value"></a>Valor devuelto

Valor COLORREF que contiene valores predeterminados para componentes RGB.

### <a name="remarks"></a>Observaciones

Llame a esta función para recuperar el valor predeterminado, que se estableció previamente por constructor o SetDefaultValue.

## <a name="canimationcolorgetg"></a><a name="getg"></a>CAnimationColor::GetG

Proporciona acceso a CAnimationVariable que representa el componente Verde.

```
CAnimationVariable& GetG();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a encapsulado CAnimationVariable que representa el componente Verde.

### <a name="remarks"></a>Observaciones

Puede llamar a este método para obtener acceso directo al subyacente CAnimationVariable que representa el componente verde.

## <a name="canimationcolorgetr"></a><a name="getr"></a>CAnimationColor::GetR

Proporciona acceso a CAnimationVariable que representa el componente Red.

```
CAnimationVariable& GetR();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a encapsulado CAnimationVariable que representa red componente.

### <a name="remarks"></a>Observaciones

Puede llamar a este método para obtener acceso directo al subyacente CAnimationVariable que representa Red componente.

## <a name="canimationcolorgetvalue"></a><a name="getvalue"></a>CAnimationColor::GetValue

Devuelve el valor actual.

```
BOOL GetValue(COLORREF& color);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
Salida. Contiene el valor actual cuando se devuelve este método.

### <a name="return-value"></a>Valor devuelto

TRUE, si el valor actual se recuperó correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Llame a esta función para recuperar el valor actual del color de animación. Si se produce un error en este método o no se han inicializado los objetos COM subyacentes para los componentes de color, color contiene el valor predeterminado, que se estableció anteriormente en el constructor o por SetDefaultValue.

## <a name="canimationcolorm_bvalue"></a><a name="m_bvalue"></a>CAnimationColor::m_bValue

Variable de animación encapsulada que representa el componente Azul del color de animación.

```
CAnimationVariable m_bValue;
```

## <a name="canimationcolorm_gvalue"></a><a name="m_gvalue"></a>CAnimationColor::m_gValue

Variable de animación encapsulada que representa el componente verde del color de animación.

```
CAnimationVariable m_gValue;
```

## <a name="canimationcolorm_rvalue"></a><a name="m_rvalue"></a>CAnimationColor::m_rValue

Variable de animación encapsulada que representa el componente rojo del color de animación.

```
CAnimationVariable m_rValue;
```

## <a name="canimationcoloroperator-colorref"></a><a name="operator_colorref"></a>CAnimationColor::operador COLORREF

```
operator COLORREF();
```

### <a name="return-value"></a>Valor devuelto

## <a name="canimationcoloroperator"></a><a name="operator_eq"></a>CAnimationColor::operator ?

Asigna color a CAnimationColor.

```
void operator=(COLORREF color);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
Especifica el nuevo valor Color de animación.

### <a name="remarks"></a>Observaciones

Se recomienda hacerlo antes del inicio de la animación, porque este operador llama a SetDefaultValue, que vuelve a crear los objetos COM subyacentes para los componentes de color si se han creado. Si suscribió este objeto de animación a eventos (ValueChanged o IntegerValueChanged), debe volver a habilitar estos eventos.

## <a name="canimationcolorsetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationColor::SetDefaultValue

Establece el valor predeterminado.

```
void SetDefaultValue(COLORREF color);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
Especifica nuevos valores predeterminados para los componentes rojo, verde y azul.

### <a name="remarks"></a>Observaciones

Utilice esta función para establecer un valor predeterminado en el objeto de animación. Este método asigna valores predeterminados a los componentes de color del color de animación. También vuelve a crear objetos COM subyacentes si se han creado. Si suscribió este objeto de animación a eventos (ValueChanged o IntegerValueChanged), debe volver a habilitar estos eventos.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
