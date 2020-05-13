---
title: Clase CAnimationVariable
ms.date: 03/27/2019
f1_keywords:
- CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationVariable::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::Create
- AFXANIMATIONCONTROLLER/CAnimationVariable::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_dblDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_lstTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_pParentObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_variable
helpviewer_keywords:
- CAnimationVariable [MFC], CAnimationVariable
- CAnimationVariable [MFC], AddTransition
- CAnimationVariable [MFC], ApplyTransitions
- CAnimationVariable [MFC], ClearTransitions
- CAnimationVariable [MFC], Create
- CAnimationVariable [MFC], CreateTransitions
- CAnimationVariable [MFC], EnableIntegerValueChangedEvent
- CAnimationVariable [MFC], EnableValueChangedEvent
- CAnimationVariable [MFC], GetDefaultValue
- CAnimationVariable [MFC], GetParentAnimationObject
- CAnimationVariable [MFC], GetValue
- CAnimationVariable [MFC], GetVariable
- CAnimationVariable [MFC], SetDefaultValue
- CAnimationVariable [MFC], SetParentAnimationObject
- CAnimationVariable [MFC], m_bAutodestroyTransitions
- CAnimationVariable [MFC], m_dblDefaultValue
- CAnimationVariable [MFC], m_lstTransitions
- CAnimationVariable [MFC], m_pParentObject
- CAnimationVariable [MFC], m_variable
ms.assetid: 506e697e-31a8-4033-a27e-292f4d7b42d9
ms.openlocfilehash: b53a1338566a329fbdf5b91c41d0411a529afe8d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755071"
---
# <a name="canimationvariable-class"></a>Clase CAnimationVariable

Representa una variable de animación.

## <a name="syntax"></a>Sintaxis

```
class CAnimationVariable;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationVariable::CAnimationVariable](#canimationvariable)|Construye un objeto de variable de animación.|
|[CAnimationVariable::-CAnimationVariable](#_dtorcanimationvariable)|Destructor. Se llama cuando un CAnimationVariable objeto se está destruyendo.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationVariable::AddTransition](#addtransition)|Agrega una transición.|
|[CAnimationVariable::ApplyTransitions](#applytransitions)|Agrega transiciones de la lista interna al guión gráfico.|
|[CAnimationVariable::ClearTransitions](#cleartransitions)|Borra las transiciones.|
|[CAnimationVariable::Create](#create)|Crea el objeto COM de la variable de animación subyacente.|
|[CAnimationVariable::CreateTransitions](#createtransitions)|Crea todas las transiciones que se aplicarán a esta variable de animación.|
|[CAnimationVariable::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Habilita o deshabilita el evento IntegerValueChanged.|
|[CAnimationVariable::EnableValueChangedEvent](#enablevaluechangedevent)|Habilita o deshabilita el ValueChanged eventos.|
|[CAnimationVariable::GetDefaultValue](#getdefaultvalue)|Devuelve el valor predeterminado.|
|[CAnimationVariable::GetParentAnimationObject](#getparentanimationobject)|Devuelve el objeto de animación primario.|
|[CAnimationVariable::GetValue](#getvalue)|Sobrecargado. Devuelve el valor actual de la variable de animación.|
|[CAnimationVariable::GetVariable](#getvariable)|Devuelve un puntero a IUIAnimationVariable objeto COM.|
|[CAnimationVariable::SetDefaultValue](#setdefaultvalue)|Establece el valor predeterminado y libera IUIAnimationVariable objeto COM.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationVariable::SetParentAnimationObject](#setparentanimationobject)|Establece la relación entre una variable de animación y un objeto de animación.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationVariable::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Especifica si se deben eliminar los objetos de transición relacionados.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationVariable::m_dblDefaultValue](#m_dbldefaultvalue)|Especifica el valor predeterminado, que se propaga a IUIAnimationVariable.|
|[CAnimationVariable::m_lstTransitions](#m_lsttransitions)|Contiene una lista de transiciones que animan esta variable de animación.|
|[CAnimationVariable::m_pParentObject](#m_pparentobject)|Puntero a un objeto de animación que encapsula esta variable de animación.|
|[CAnimationVariable::m_variable](#m_variable)|Almacena un puntero a IUIAnimationVariable objeto COM. NULL si el objeto COM aún no se ha creado o si se ha producido un error en la creación.|

## <a name="remarks"></a>Observaciones

La clase CAnimationVariable encapsula el objeto COM IUIAnimationVariable. También contiene una lista de transiciones que se aplicarán a la variable de animación en un guión gráfico. CAnimationVariable objetos se incrustan en objetos de animación, que pueden representar en una aplicación un valor animado, punto, tamaño, color y rectángulo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CAnimationVariable`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="canimationvariablecanimationvariable"></a><a name="_dtorcanimationvariable"></a>CAnimationVariable::-CAnimationVariable

Destructor. Se llama cuando un CAnimationVariable objeto se está destruyendo.

```
virtual ~CAnimationVariable();
```

## <a name="canimationvariableaddtransition"></a><a name="addtransition"></a>CAnimationVariable::AddTransition

Agrega una transición.

```cpp
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>Parámetros

*pTransición*<br/>
Puntero a una transición que se va a agregar.

### <a name="remarks"></a>Observaciones

Se llama a este método para agregar una transición a la lista interna de transiciones que se aplicarán a la variable de animación. Esta lista debe borrarse cuando se haya programado una animación.

## <a name="canimationvariableapplytransitions"></a><a name="applytransitions"></a>CAnimationVariable::ApplyTransitions

Agrega transiciones de la lista interna al guión gráfico.

```cpp
void ApplyTransitions(
    CAnimationController* pController,
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parámetros

*pController*<br/>
Un puntero al controlador de animación primario.

*pStoryboard*<br/>
Un puntero al guión gráfico.

*bDependOnKeyframes*<br/>
TRUE, si este método debe agregar transiciones que dependen de fotogramas clave.

### <a name="remarks"></a>Observaciones

Este método agrega transiciones de la lista interna al guión gráfico. Se llama desde el código de nivel superior varias veces para agregar transiciones que no dependen de fotogramas clave y agregar transiciones que dependen de fotogramas clave. Si no se ha creado el objeto COM de la variable de animación subyacente, este método lo crea en esta etapa.

## <a name="canimationvariablecanimationvariable"></a><a name="canimationvariable"></a>CAnimationVariable::CAnimationVariable

Construye un objeto de variable de animación.

```
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```

### <a name="parameters"></a>Parámetros

*dblDefaultValue*<br/>
Especifica el valor predeterminado.

### <a name="remarks"></a>Observaciones

Construye un objeto de variable de animación y establece su valor predeterminado. Un valor predeterminado se utiliza cuando una variable no está animada o no se puede animar.

## <a name="canimationvariablecleartransitions"></a><a name="cleartransitions"></a>CAnimationVariable::ClearTransitions

Borra las transiciones.

```cpp
void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>Parámetros

*bAutodestroy*<br/>
Especifica si este método debe eliminar objetos de transición.

### <a name="remarks"></a>Observaciones

Este método quita todas las transiciones de la lista interna de transiciones. Si bAutodestroy es TRUE o m_bAutodestroyTransitions es TRUE, se eliminan las transiciones. De lo contrario, el autor de la llamada debe desasignar los objetos de transición.

## <a name="canimationvariablecreate"></a><a name="create"></a>CAnimationVariable::Create

Crea el objeto COM de la variable de animación subyacente.

```
virtual BOOL Create(IUIAnimationManager* pManager);
```

### <a name="parameters"></a>Parámetros

*pManager*<br/>
Un puntero al administrador de animaciones.

### <a name="return-value"></a>Valor devuelto

TRUESi la variable de animación se creó correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Este método crea el objeto COM de la variable de animación subyacente y establece su valor predeterminado.

## <a name="canimationvariablecreatetransitions"></a><a name="createtransitions"></a>CAnimationVariable::CreateTransitions

Crea todas las transiciones que se aplicarán a esta variable de animación.

```
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parámetros

*pLibrary*<br/>
Puntero a una [interfaz IUIAnimationTransitionLibrary](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), que define una biblioteca de transiciones estándar.

### <a name="return-value"></a>Valor devuelto

TRUESi las transiciones se crearon correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método cuando necesita crear transiciones que se han agregado a la lista interna de transiciones de la variable.

## <a name="canimationvariableenableintegervaluechangedevent"></a><a name="enableintegervaluechangedevent"></a>CAnimationVariable::EnableIntegerValueChangedEvent

Habilita o deshabilita el evento IntegerValueChanged.

```cpp
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parámetros

*pController*<br/>
Un puntero al controlador primario.

*bHabilitar*<br/>
TRUE - habilitar evento, FALSE - deshabilitar evento.

### <a name="remarks"></a>Observaciones

Cuando ValueChanged evento está habilitado, el marco de trabajo llama al método virtual CAnimationController::OnAnimationIntegerValueChanged. Debe reemplazarlo en una clase derivada de CAnimationController para procesar este evento. Se llama a este método cada vez que se cambia el valor entero de la variable de animación.

## <a name="canimationvariableenablevaluechangedevent"></a><a name="enablevaluechangedevent"></a>CAnimationVariable::EnableValueChangedEvent

Habilita o deshabilita el ValueChanged eventos.

```cpp
void EnableValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parámetros

*pController*<br/>
Un puntero al controlador primario.

*bHabilitar*<br/>
TRUE - habilitar evento, FALSE - deshabilitar evento.

### <a name="remarks"></a>Observaciones

Cuando ValueChanged evento está habilitado, el marco de trabajo llama al método virtual CAnimationController::OnAnimationValueChanged. Debe reemplazarlo en una clase derivada de CAnimationController para procesar este evento. Se llama a este método cada vez que se cambia el valor de la variable de animación.

## <a name="canimationvariablegetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationVariable::GetDefaultValue

Devuelve el valor predeterminado.

```
DOUBLE GetDefaultValue() const;
```

### <a name="return-value"></a>Valor devuelto

El valor predeterminado.

### <a name="remarks"></a>Observaciones

Utilice esta función para obtener el valor predeterminado de la variable de animación. El valor predeterminado se puede establecer en el constructor o por SetDefaultValue método.

## <a name="canimationvariablegetparentanimationobject"></a><a name="getparentanimationobject"></a>CAnimationVariable::GetParentAnimationObject

Devuelve el objeto de animación primario.

```
CAnimationBaseObject* GetParentAnimationObject();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto de animación primario, si se estableció la relación, en caso contrario NULL.

### <a name="remarks"></a>Observaciones

Se puede llamar a este método para recuperar un puntero a un objeto de animación primario (un contenedor).

## <a name="canimationvariablegetvalue"></a><a name="getvalue"></a>CAnimationVariable::GetValue

Devuelve el valor actual de la variable de animación.

```
HRESULT GetValue(DOUBLE& dblValue);
HRESULT GetValue(INT32& nValue);
```

### <a name="parameters"></a>Parámetros

*dblValue*<br/>
El valor actual de la variable de animación.

*nValor*<br/>
El valor actual de la variable de animación.

### <a name="return-value"></a>Valor devuelto

S_OK si el valor se obtuvo correctamente o no se ha creado la variable de animación subyacente. De lo contrario, el código de error HRESULT.

### <a name="remarks"></a>Observaciones

Se puede llamar a este método para recuperar el valor actual de la variable de animación. Si no se ha creado el objeto COM subyacente, dblValue contendrá un valor predeterminado, cuando se devuelva la función.

## <a name="canimationvariablegetvariable"></a><a name="getvariable"></a>CAnimationVariable::GetVariable

Devuelve un puntero a IUIAnimationVariable objeto COM.

```
IUIAnimationVariable* GetVariable();
```

### <a name="return-value"></a>Valor devuelto

Un puntero válido a IUIAnimationVariable objeto COM, o NULL si no se creó la variable de animación o no se puede crear.

### <a name="remarks"></a>Observaciones

Utilice esta función para tener acceso al objeto COM IUIAnimationVariable subyacente y llamar a sus métodos directamente si es necesario.

## <a name="canimationvariablem_bautodestroytransitions"></a><a name="m_bautodestroytransitions"></a>CAnimationVariable::m_bAutodestroyTransitions

Especifica si se deben eliminar los objetos de transición relacionados.

```
BOOL m_bAutodestroyTransitions;
```

### <a name="remarks"></a>Observaciones

Establezca este valor en TRUE para forzar la eliminación de objetos de transición cuando se quitan de la lista interna de transiciones. Si este valor es FALSE, las transiciones se deben eliminar llamando a la aplicación. La lista de transiciones siempre se borra después de que se haya programado una animación. El valor predeterminado es FALSE.

## <a name="canimationvariablem_dbldefaultvalue"></a><a name="m_dbldefaultvalue"></a>CAnimationVariable::m_dblDefaultValue

Especifica el valor predeterminado, que se propaga a IUIAnimationVariable.

```
DOUBLE m_dblDefaultValue;
```

## <a name="canimationvariablem_lsttransitions"></a><a name="m_lsttransitions"></a>CAnimationVariable::m_lstTransitions

Contiene una lista de transiciones que animan esta variable de animación.

```
CObList m_lstTransitions;
```

## <a name="canimationvariablem_pparentobject"></a><a name="m_pparentobject"></a>CAnimationVariable::m_pParentObject

Puntero a un objeto de animación que encapsula esta variable de animación.

```
CAnimationBaseObject* m_pParentObject;
```

## <a name="canimationvariablem_variable"></a><a name="m_variable"></a>CAnimationVariable::m_variable

Almacena un puntero a IUIAnimationVariable objeto COM. NULL si el objeto COM aún no se ha creado o si se ha producido un error en la creación.

```
ATL::CComPtr<IUIAnimationVariable> m_variable;
```

## <a name="canimationvariablesetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationVariable::SetDefaultValue

Establece el valor predeterminado y libera IUIAnimationVariable objeto COM.

```cpp
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>Parámetros

*dblDefaultValue*<br/>
Especifica el nuevo valor predeterminado.

### <a name="remarks"></a>Observaciones

Utilice este método para restablecer el valor predeterminado. Este método libera el objeto COM IUIAnimationVariable interno, por lo tanto, cuando se vuelve a crear la variable de animación, el objeto COM subyacente obtiene el nuevo valor predeterminado. GetValue devuelve el valor predeterminado si no se crea el objeto COM que representa la variable de animación o si la variable no se ha animado.

## <a name="canimationvariablesetparentanimationobject"></a><a name="setparentanimationobject"></a>CAnimationVariable::SetParentAnimationObject

Establece la relación entre una variable de animación y un objeto de animación.

```cpp
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```

### <a name="parameters"></a>Parámetros

*pParentObject*<br/>
Puntero a un objeto de animación que contiene esta variable.

### <a name="remarks"></a>Observaciones

Este método se llama internamente para establecer una relación uno a uno entre una variable de animación y un objeto de animación que lo encapsula.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
