---
title: CAnimationSize (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 974bf49b4315095a2103c50bfb81cc5e164273d6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433181"
---
# <a name="canimationsize-class"></a>Clase CAnimationSize

Implementa la funcionalidad de un objeto cuyas dimensiones se pueden animar.

## <a name="syntax"></a>Sintaxis

```
class CAnimationSize : public CAnimationBaseObject;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationSize::CAnimationSize](#canimationsize)|Sobrecargado. Construye un objeto de tamaño de la animación.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationSize::AddTransition](#addtransition)|Agrega las transiciones de ancho y alto.|
|[CAnimationSize::GetCX](#getcx)|Proporciona acceso a CAnimationVariable que representa el ancho.|
|[CAnimationSize::GetCY](#getcy)|Proporciona acceso a CAnimationVariable que representa el alto.|
|[CAnimationSize::GetDefaultValue](#getdefaultvalue)|Devuelve los valores predeterminados para Width y Height.|
|[CAnimationSize::GetValue](#getvalue)|Devuelve el valor actual.|
|[CAnimationSize::SetDefaultValue](#setdefaultvalue)|Establece el valor predeterminado.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CAnimationSize::GetAnimationVariableList](#getanimationvariablelist)|Coloca las variables de animación encapsulado en una lista. (Invalida [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CSize CAnimationSize::operator](#operator_csize)|Convierte un CAnimationSize un CSize.|
|[CAnimationSize::operator =](#operator_eq)|Asigna szSrc a CAnimationSize.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|nombre|Descripción|
|----------|-----------------|
|[CAnimationSize::m_cxValue](#m_cxvalue)|La variable de animación encapsulado que representa el ancho del tamaño de la animación.|
|[CAnimationSize::m_cyValue](#m_cyvalue)|La variable de animación encapsulado que representa el alto del tamaño de la animación.|

## <a name="remarks"></a>Comentarios

La clase CAnimationSize encapsula los dos objetos CAnimationVariable y puede representar en aplicaciones de un tamaño. Por ejemplo, puede usar esta clase para animar un tamaño de dos dimensiones objeto en la pantalla (como en el rectángulo, controlar etcetera). Para usar esta clase en la aplicación, simplemente cree una instancia de un objeto de esta clase, agréguelo al controlador de animación mediante CAnimationController::AddAnimationObject y llamar a AddTransition para cada transición que se aplicará al ancho o alto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationSize`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationSize::AddTransition

Agrega las transiciones de ancho y alto.

```
void AddTransition(
    CBaseTransition* pCXTransition,
    CBaseTransition* pCYTransition);
```

### <a name="parameters"></a>Parámetros

*pCXTransition*<br/>
Puntero a la transición para el ancho.

*pCYTransition*<br/>
Puntero a la transición para el alto.

### <a name="remarks"></a>Comentarios

Llame a esta función para agregar las transiciones especificadas a la lista interna de las transiciones que se aplicará a las variables de animación de ancho y alto. Al agregar transiciones, no se aplican inmediatamente y almacenan en una lista interna. Las transiciones se aplican (agregado a un guión gráfico para un determinado valor) cuando se llama a CAnimationController::AnimateGroup. Si no tiene que aplicar una transición a una de las dimensiones, puede pasar NULL.

##  <a name="canimationsize"></a>  CAnimationSize::CAnimationSize

Construye un objeto de tamaño de la animación.

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

### <a name="remarks"></a>Comentarios

Se construye el objeto con valores predeterminados para el ancho, alto, objeto de identificador y el identificador de grupo, que se establecerá en 0. Puede cambiar posteriormente en tiempo de ejecución mediante SetDefaultValue y SetID.

##  <a name="getanimationvariablelist"></a>  CAnimationSize::GetAnimationVariableList

Coloca las variables de animación encapsulado en una lista.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parámetros

*lst*<br/>
Cuando la función devuelve, contiene punteros a dos objetos CAnimationVariable que representa el ancho y alto.

##  <a name="getcx"></a>  CAnimationSize::GetCX

Proporciona acceso a CAnimationVariable que representa el ancho.

```
CAnimationVariable& GetCX();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a CAnimationVariable encapsulado que representa el ancho.

### <a name="remarks"></a>Comentarios

Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa el ancho.

##  <a name="getcy"></a>  CAnimationSize::GetCY

Proporciona acceso a CAnimationVariable que representa el alto.

```
CAnimationVariable& GetCY();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a CAnimationVariable encapsulado que representa el alto.

### <a name="remarks"></a>Comentarios

Puede llamar a este método para obtener acceso directo a CAnimationVariable subyacente que representa el alto.

##  <a name="getdefaultvalue"></a>  CAnimationSize::GetDefaultValue

Devuelve los valores predeterminados para Width y Height.

```
CSize GetDefaultValue();
```

### <a name="return-value"></a>Valor devuelto

Un objeto CSize que contiene los valores predeterminados.

### <a name="remarks"></a>Comentarios

Llame a esta función para recuperar el valor predeterminado, que anteriormente se ha establecido mediante el constructor o SetDefaultValue.

##  <a name="getvalue"></a>  CAnimationSize::GetValue

Devuelve el valor actual.

```
BOOL GetValue(CSize& szValue);
```

### <a name="parameters"></a>Parámetros

*szValue*<br/>
Salida. Cuando este método vuelve, contiene el valor actual.

### <a name="return-value"></a>Valor devuelto

Es TRUE si el valor actual se ha recuperado correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Llame a esta función para recuperar el valor actual de tamaño de la animación. Si este método produce un error o no se han inicializado los objetos COM subyacentes para el ancho y el tamaño, szValue contiene el valor predeterminado, que anteriormente se estableció en el constructor o por SetDefaultValue.

##  <a name="m_cxvalue"></a>  CAnimationSize::m_cxValue

La variable de animación encapsulado que representa el ancho del tamaño de la animación.

```
CAnimationVariable m_cxValue;
```

##  <a name="m_cyvalue"></a>  CAnimationSize::m_cyValue

La variable de animación encapsulado que representa el alto del tamaño de la animación.

```
CAnimationVariable m_cyValue;
```

##  <a name="operator_csize"></a>  CSize CAnimationSize::operator

Convierte un CAnimationSize un CSize.

```
operator CSize();
```

### <a name="return-value"></a>Valor devuelto

Valor actual de tamaño de la animación como CSize.

### <a name="remarks"></a>Comentarios

Esta función llama internamente a GetValue. Si se produce un error en GetValue por algún motivo, el tamaño devuelto contendrá los valores predeterminados de ancho y alto.

##  <a name="operator_eq"></a>  CAnimationSize::operator =

Asigna szSrc a CAnimationSize.

```
void operator=(const CSize& szSrc);
```

### <a name="parameters"></a>Parámetros

*szSrc*<br/>
Hace referencia a CSize o tamaño.

### <a name="remarks"></a>Comentarios

Asigna szSrc a CAnimationSize. Se recomienda hacerlo antes del inicio de la animación, dado que este operador llama a SetDefaultValue, que vuelve a crear los objetos COM subyacentes de Width y Height si se han creado. Si se ha suscrito a este objeto de animación a eventos (ValueChanged o IntegerValueChanged), deberá volver a habilitar estos eventos.

##  <a name="setdefaultvalue"></a>  CAnimationSize::SetDefaultValue

Establece el valor predeterminado.

```
void SetDefaultValue(const CSize& szDefault);
```

### <a name="parameters"></a>Parámetros

*szDefault*<br/>
Especifica el nuevo tamaño de forma predeterminada.

### <a name="remarks"></a>Comentarios

Utilice esta función para establecer un valor predeterminado para el objeto de animación. Este método asigna valores predeterminados para el ancho y alto del tamaño de la animación. También se vuelve a crear objetos COM subyacentes si se han creado. Si se ha suscrito a este objeto de animación a eventos (ValueChanged o IntegerValueChanged), deberá volver a habilitar estos eventos.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
