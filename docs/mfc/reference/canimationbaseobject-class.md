---
title: Clase CAnimationBaseObject
ms.date: 03/27/2019
f1_keywords:
- CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ContainsVariable
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::DetachFromController
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetParentAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_dwUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_pParentController
helpviewer_keywords:
- CAnimationBaseObject [MFC], CAnimationBaseObject
- CAnimationBaseObject [MFC], ApplyTransitions
- CAnimationBaseObject [MFC], ClearTransitions
- CAnimationBaseObject [MFC], ContainsVariable
- CAnimationBaseObject [MFC], CreateTransitions
- CAnimationBaseObject [MFC], DetachFromController
- CAnimationBaseObject [MFC], EnableIntegerValueChangedEvent
- CAnimationBaseObject [MFC], EnableValueChangedEvent
- CAnimationBaseObject [MFC], GetAutodestroyTransitions
- CAnimationBaseObject [MFC], GetGroupID
- CAnimationBaseObject [MFC], GetObjectID
- CAnimationBaseObject [MFC], GetUserData
- CAnimationBaseObject [MFC], SetAutodestroyTransitions
- CAnimationBaseObject [MFC], SetID
- CAnimationBaseObject [MFC], SetUserData
- CAnimationBaseObject [MFC], GetAnimationVariableList
- CAnimationBaseObject [MFC], SetParentAnimationObjects
- CAnimationBaseObject [MFC], m_bAutodestroyTransitions
- CAnimationBaseObject [MFC], m_dwUserData
- CAnimationBaseObject [MFC], m_nGroupID
- CAnimationBaseObject [MFC], m_nObjectID
- CAnimationBaseObject [MFC], m_pParentController
ms.assetid: 76b25917-940e-4eba-940f-31d270702603
ms.openlocfilehash: 1874ddfdd26b8dd371e32f7e68ea8f668c47d8e1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750222"
---
# <a name="canimationbaseobject-class"></a>Clase CAnimationBaseObject

La clase base para todos los objetos de animación.

## <a name="syntax"></a>Sintaxis

```
class CAnimationBaseObject : public CObject;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationBaseObject::CAnimationBaseObject](#canimationbaseobject)|Sobrecargado. Construye un objeto de animación.|
|[CAnimationBaseObject::CAnimationBaseObject](#_dtorcanimationbaseobject)|Destructor. Se llama cuando se destruye un objeto de animación.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationBaseObject::ApplyTransitions](#applytransitions)|Agrega transiciones al guión gráfico con la variable de animación encapsulada.|
|[CAnimationBaseObject::ClearTransitions](#cleartransitions)|Elimina todas las transiciones relacionadas.|
|[CAnimationBaseObject::ContainsVariable](#containsvariable)|Determina si un objeto de animación contiene una variable de animación determinada.|
|[CAnimationBaseObject::CreateTransitions](#createtransitions)|Crea transiciones asociadas a un objeto de animación.|
|[CAnimationBaseObject::DetachFromController](#detachfromcontroller)|Separa un objeto de animación del controlador de animación primario.|
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Configura el controlador de eventos Integer Value Changed.|
|[CAnimationBaseObject::EnableValueChangedEvent](#enablevaluechangedevent)|Configura el controlador de eventos Value Changed.|
|[CAnimationBaseObject::GetAutodestroyTransitions](#getautodestroytransitions)|Indica si la transición relacionada se destruye automáticamente.|
|[CAnimationBaseObject::GetGroupID](#getgroupid)|Devuelve el identificador de grupo actual.|
|[CAnimationBaseObject::GetObjectID](#getobjectid)|Devuelve el identificador de objeto actual.|
|[CAnimationBaseObject::GetUserData](#getuserdata)|Devuelve datos definidos por el usuario.|
|[CAnimationBaseObject::SetAutodestroyTransitions](#setautodestroytransitions)|Establece una marca para destruir automáticamente las transiciones.|
|[CAnimationBaseObject::SetID](#setid)|Establece nuevos iDs.|
|[CAnimationBaseObject::SetUserData](#setuserdata)|Establece los datos definidos por el usuario.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationBaseObject::GetAnimationVariableList](#getanimationvariablelist)|Recopila punteros a variables de animación contenidas.|
|[CAnimationBaseObject::SetParentAnimationObjects](#setparentanimationobjects)|Establece la relación entre las variables de animación, contenidas en un objeto de animación, y su contenedor.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationBaseObject::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Especifica si las transiciones relacionadas se deben destruir automáticamente.|
|[CAnimationBaseObject::m_dwUserData](#m_dwuserdata)|Almacena los datos definidos por el usuario.|
|[CAnimationBaseObject::m_nGroupID](#m_ngroupid)|Especifica el identificador de grupo del objeto de animación.|
|[CAnimationBaseObject::m_nObjectID](#m_nobjectid)|Especifica el identificador de objeto del objeto de animación.|
|[CAnimationBaseObject::m_pParentController](#m_pparentcontroller)|Un puntero al controlador de animación primario.|

## <a name="remarks"></a>Observaciones

Esta clase implementa métodos básicos para todos los objetos de animación. Un objeto de animación puede representar un valor, punto, tamaño, rectángulo o color en una aplicación, así como cualquier entidad personalizada. Los objetos de animación se almacenan en grupos de animación (consulte CAnimationGroup). Cada grupo se puede animar por separado y se puede tratar como un análogo del guión gráfico. Un objeto de animación encapsula una o varias variables de animación (consulte CAnimationVariable), en función de su representación lógica. Por ejemplo, CAnimationRect contiene cuatro variables de animación: una variable para cada lado del rectángulo. Cada clase de objeto de animación expone sobrecargado AddTransition método, que se debe usar para aplicar transiciones a las variables de animación encapsuladas. Un objeto de animación se puede identificar mediante el identificador de objeto (opcionalmente) y el identificador de grupo. Un ID de grupo es necesario para colocar un objeto de animación para corregir el grupo, pero si no se especifica un ID de grupo, se coloca un objeto en el grupo predeterminado con el ID 0. Si llama a SetID con GroupID diferente, un objeto de animación se moverá a otro grupo (se crea un nuevo grupo si es necesario).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationBaseObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="canimationbaseobjectcanimationbaseobject"></a><a name="_dtorcanimationbaseobject"></a>CAnimationBaseObject::CAnimationBaseObject

Destructor. Se llama cuando se destruye un objeto de animación.

```
virtual ~CAnimationBaseObject();
```

## <a name="canimationbaseobjectapplytransitions"></a><a name="applytransitions"></a>CAnimationBaseObject::ApplyTransitions

Agrega transiciones al guión gráfico con la variable de animación encapsulada.

```
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parámetros

*pStoryboard*<br/>
Un puntero a un guión gráfico.

*bDependOnKeyframes*<br/>
Cuando FALSE, este método agrega solo aquellas transiciones que no dependen de fotogramas clave.

### <a name="return-value"></a>Valor devuelto

TRUESi las transiciones se agregaron correctamente.

### <a name="remarks"></a>Observaciones

Agrega transiciones relacionadas, que se han agregado con AddTransition (métodos sobrecargados en clases derivadas), al guión gráfico.

## <a name="canimationbaseobjectcanimationbaseobject"></a><a name="canimationbaseobject"></a>CAnimationBaseObject::CAnimationBaseObject

Construye un objeto de animación.

```
CAnimationBaseObject();

CAnimationBaseObject(
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parámetros

*nGroupID*<br/>
Especifica el identificador de grupo.

*nObjectID*<br/>
Especifica el identificador de objeto.

*dwUserData*<br/>
Datos definidos por el usuario, que se pueden asociar con el objeto de animación y recuperarse más adelante en tiempo de ejecución.

### <a name="remarks"></a>Observaciones

Construye un objeto de animación y asigna el ID de objeto (0) y el ID de grupo (0) predeterminados.

## <a name="canimationbaseobjectcleartransitions"></a><a name="cleartransitions"></a>CAnimationBaseObject::ClearTransitions

Elimina todas las transiciones relacionadas.

```
virtual void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>Parámetros

*bAutodestroy*<br/>
Especifica si se destruirán objetos de transición automáticamente o simplemente eliminarlos de la lista relacionada.

### <a name="remarks"></a>Observaciones

Quita todas las transiciones relacionadas y las destruye si bAutodestroy o m_bAutodestroyTransitions marca es TRUE. Las transiciones deben destruirse automáticamente solo si no se asignan en la pila. Si los indicadores anteriores son FALSE, las transiciones se eliminan de la lista interna de transiciones relacionadas.

## <a name="canimationbaseobjectcontainsvariable"></a><a name="containsvariable"></a>CAnimationBaseObject::ContainsVariable

Determina si un objeto de animación contiene una variable de animación determinada.

```
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parámetros

*pVariable*<br/>
Un puntero a la variable de animación.

### <a name="return-value"></a>Valor devuelto

TRUESi la variable de animación está contenida en el objeto de animación; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Este método se puede utilizar para determinar si una variable de animación especificada por pVariable está contenida dentro de un objeto de animación. Un objeto de animación, dependiendo de su tipo, puede contener varias variables de animación. Por ejemplo, CAnimationColor contiene tres variables, una para cada componente de color (rojo, verde y azul). Cuando un valor de la variable de animación ha cambiado, la API de animación de Windows envía eventos ValueChanged o IntegerValueChanged (si está habilitado) y el parámetro de este evento es un puntero a la interfaz IUIAnimationVariable de la variable de animación. Este método ayuda a obtener un puntero a la animación de un puntero a objeto COM contenido.

## <a name="canimationbaseobjectcreatetransitions"></a><a name="createtransitions"></a>CAnimationBaseObject::CreateTransitions

Crea transiciones asociadas a un objeto de animación.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>Valor devuelto

TRUESi las transiciones se crearon correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Recorre la lista de variables de animación encapsuladas en un objeto de animación derivado y crea transiciones asociadas a cada variable de animación.

## <a name="canimationbaseobjectdetachfromcontroller"></a><a name="detachfromcontroller"></a>CAnimationBaseObject::DetachFromController

Separa un objeto de animación del controlador de animación primario.

```cpp
void DetachFromController();
```

### <a name="remarks"></a>Observaciones

Este método se utiliza internamente.

## <a name="canimationbaseobjectenableintegervaluechangedevent"></a><a name="enableintegervaluechangedevent"></a>CAnimationBaseObject::EnableIntegerValueChangedEvent

Configura el controlador de eventos Integer Value Changed.

```
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parámetros

*pController*<br/>
Un puntero a un controlador primario.

*bHabilitar*<br/>
Especifica si se debe habilitar o deshabilitar el evento Integer Value Changed.

### <a name="remarks"></a>Observaciones

Si el valor entero changed controlador de eventos está habilitado, puede controlar este evento en CAnimationController::OnAnimationIntegerValueChanged método, que se debe invalidar en un CAnimationController-clase derivada. Se llama a este método cada vez que el valor entero de la animación ha cambiado.

## <a name="canimationbaseobjectenablevaluechangedevent"></a><a name="enablevaluechangedevent"></a>CAnimationBaseObject::EnableValueChangedEvent

Configura el controlador de eventos Value Changed.

```
virtual void EnableValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parámetros

*pController*<br/>
Un puntero a un controlador primario.

*bHabilitar*<br/>
Especifica si se debe habilitar o deshabilitar el evento Value Changed.

### <a name="remarks"></a>Observaciones

Si el Value Changed controlador de eventos está habilitado, puede controlar este evento en CAnimationController::OnAnimationValueChanged método, que se debe invalidar en un CAnimationController-clase derivada. Se llama a este método cada vez que el valor de la animación ha cambiado.

## <a name="canimationbaseobjectgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationBaseObject::GetAnimationVariableList

Recopila punteros a variables de animación contenidas.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& list) = 0;
```

### <a name="parameters"></a>Parámetros

*list*<br/>
Una lista que debe rellenarse con variables de animación contenidas en un objeto de animación.

### <a name="remarks"></a>Observaciones

Este método virtual puro debe reemplazarse en una clase derivada. Un objeto de animación, según su tipo, contiene una o varias variables de animación. Por ejemplo, CAnimationPoint contiene dos variables, para las coordenadas X e Y respectivamente. La clase base CAnimationBaseObject implementa algunos métodos genéricos, que actúan en una lista de variables de animación: ApplyTransitions, ClearTransitions, EnableValueChangedEvent, EnableIntegerValueChangedEvent. Estos métodos llaman a GetAnimationVariableList, que se rellena en una clase derivada con variables de animación reales contenidas en un objeto de animación determinado, a continuación, bucle sobre la lista y realizar las acciones necesarias. Si crea un objeto de animación personalizado, debe agregar para *enumerar* todas las variables de animación contenidas en ese objeto.

## <a name="canimationbaseobjectgetautodestroytransitions"></a><a name="getautodestroytransitions"></a>CAnimationBaseObject::GetAutodestroyTransitions

Indica si la transición relacionada se destruye automáticamente.

```
BOOL GetAutodestroyTransitions() const;
```

### <a name="return-value"></a>Valor devuelto

Si ES TRUE, las transiciones relacionadas se destruyen automáticamente; si FALSE, los objetos de transición deben desasignarse llamando a la aplicación.

### <a name="remarks"></a>Observaciones

De forma predeterminada, esta marca es TRUE. Establezca esta marca solo si la aplicación que realiza la llamada debe desasignar la transición en la pila o las transiciones.

## <a name="canimationbaseobjectgetgroupid"></a><a name="getgroupid"></a>CAnimationBaseObject::GetGroupID

Devuelve el identificador de grupo actual.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>Valor devuelto

ID de grupo actual.

### <a name="remarks"></a>Observaciones

Utilice este método para recuperar el identificador de grupo. Es 0 si el identificador de grupo no se ha establecido explícitamente en el constructor o con SetID.

## <a name="canimationbaseobjectgetobjectid"></a><a name="getobjectid"></a>CAnimationBaseObject::GetObjectID

Devuelve el identificador de objeto actual.

```
UINT32 GetObjectID() const;
```

### <a name="return-value"></a>Valor devuelto

ID de objeto actual.

### <a name="remarks"></a>Observaciones

Utilice este método para recuperar el identificador de objeto. Es 0 si el identificador de objeto no se ha establecido explícitamente en el constructor o con SetID.

## <a name="canimationbaseobjectgetuserdata"></a><a name="getuserdata"></a>CAnimationBaseObject::GetUserData

Devuelve datos definidos por el usuario.

```
DWORD GetUserData() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de datos personalizados.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar los datos personalizados en tiempo de ejecución. El valor devuelto será 0 si no se inicializó explícitamente en el constructor o con SetUserData.

## <a name="canimationbaseobjectm_bautodestroytransitions"></a><a name="m_bautodestroytransitions"></a>CAnimationBaseObject::m_bAutodestroyTransitions

Especifica si las transiciones relacionadas se deben destruir automáticamente.

```
BOOL m_bAutodestroyTransitions;
```

## <a name="canimationbaseobjectm_dwuserdata"></a><a name="m_dwuserdata"></a>CAnimationBaseObject::m_dwUserData

Almacena los datos definidos por el usuario.

```
DWORD m_dwUserData;
```

## <a name="canimationbaseobjectm_ngroupid"></a><a name="m_ngroupid"></a>CAnimationBaseObject::m_nGroupID

Especifica el identificador de grupo del objeto de animación.

```
UINT32 m_nGroupID;
```

## <a name="canimationbaseobjectm_nobjectid"></a><a name="m_nobjectid"></a>CAnimationBaseObject::m_nObjectID

Especifica el identificador de objeto del objeto de animación.

```
UINT32 m_nObjectID;
```

## <a name="canimationbaseobjectm_pparentcontroller"></a><a name="m_pparentcontroller"></a>CAnimationBaseObject::m_pParentController

Un puntero al controlador de animación primario.

```
CAnimationController* m_pParentController;
```

## <a name="canimationbaseobjectsetautodestroytransitions"></a><a name="setautodestroytransitions"></a>CAnimationBaseObject::SetAutodestroyTransitions

Establece una marca para destruir automáticamente las transiciones.

```cpp
void SetAutodestroyTransitions(BOOL bValue);
```

### <a name="parameters"></a>Parámetros

*bValor*<br/>
Especifica la marca de destrucción automática.

### <a name="remarks"></a>Observaciones

Establezca esta marca solo si ha asignado objetos de transición mediante el operador new. Si por alguna razón se asignan objetos de transición en la pila, la marca de destrucción automática debe ser FALSE. De forma predeterminada, esta marca es TRUE.

## <a name="canimationbaseobjectsetid"></a><a name="setid"></a>CAnimationBaseObject::SetID

Establece nuevos iDs.

```cpp
void SetID(
    UINT32 nObjectID,
    UINT32 nGroupID = 0);
```

### <a name="parameters"></a>Parámetros

*nObjectID*<br/>
Especifica el nuevo ID de objeto.

*nGroupID*<br/>
Especifica el nuevo ID de grupo.

### <a name="remarks"></a>Observaciones

Le permite cambiar el ID de objeto y el ID de grupo. Si el nuevo ID de grupo difiere del identificador actual, se mueve un objeto de animación a otro grupo (se creará un nuevo grupo, si es necesario).

## <a name="canimationbaseobjectsetparentanimationobjects"></a><a name="setparentanimationobjects"></a>CAnimationBaseObject::SetParentAnimationObjects

Establece la relación entre las variables de animación, contenidas en un objeto de animación, y su contenedor.

```
virtual void SetParentAnimationObjects();
```

### <a name="remarks"></a>Observaciones

Esta aplicación auxiliar se puede utilizar para establecer una relación entre las variables de animación contenidas en un objeto de animación y su contenedor. Recorre las variables de animación y establece un puntero de retroceso a un objeto de animación primario en cada variable de animación. En la implementación actual, la relación real se establece en CAnimationBaseObject::ApplyTransitions, por lo tanto, los punteros de retroceso no se establecen hasta que se llama a CAnimationGroup::Animate. Conocer la relación puede ser útil al procesar eventos y necesita obtener un objeto de animación primario de CAnimationVariable. Utilice CAnimationVariable::GetParentAnimationObject.

## <a name="canimationbaseobjectsetuserdata"></a><a name="setuserdata"></a>CAnimationBaseObject::SetUserData

Establece los datos definidos por el usuario.

```cpp
void SetUserData (DWORD dwUserData);
```

### <a name="parameters"></a>Parámetros

*dwUserData*<br/>
Especifica los datos personalizados.

### <a name="remarks"></a>Observaciones

Utilice este método para asociar datos personalizados con un objeto de animación. GetUserData puede recuperar estos datos más adelante en tiempo de ejecución.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
