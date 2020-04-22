---
title: Clase CAnimationGroup
ms.date: 03/27/2019
f1_keywords:
- CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::Animate
- AFXANIMATIONCONTROLLER/CAnimationGroup::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationGroup::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::Schedule
- AFXANIMATIONCONTROLLER/CAnimationGroup::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutoclearTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstKeyFrames
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pStoryboard
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pParentController
helpviewer_keywords:
- CAnimationGroup [MFC], CAnimationGroup
- CAnimationGroup [MFC], Animate
- CAnimationGroup [MFC], ApplyTransitions
- CAnimationGroup [MFC], FindAnimationObject
- CAnimationGroup [MFC], GetGroupID
- CAnimationGroup [MFC], RemoveKeyframes
- CAnimationGroup [MFC], RemoveTransitions
- CAnimationGroup [MFC], Schedule
- CAnimationGroup [MFC], SetAutodestroyTransitions
- CAnimationGroup [MFC], AddKeyframes
- CAnimationGroup [MFC], AddTransitions
- CAnimationGroup [MFC], CreateTransitions
- CAnimationGroup [MFC], m_bAutoclearTransitions
- CAnimationGroup [MFC], m_bAutodestroyAnimationObjects
- CAnimationGroup [MFC], m_bAutodestroyKeyframes
- CAnimationGroup [MFC], m_lstAnimationObjects
- CAnimationGroup [MFC], m_lstKeyFrames
- CAnimationGroup [MFC], m_pStoryboard
- CAnimationGroup [MFC], m_nGroupID
- CAnimationGroup [MFC], m_pParentController
ms.assetid: 8bc18ceb-33a2-41d0-9731-71811adacab7
ms.openlocfilehash: 14ac32524436ff46449171ad90599e60f63dff2a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750149"
---
# <a name="canimationgroup-class"></a>Clase CAnimationGroup

Implementa un grupo de animación, que combina un guión gráfico de animación, objetos de animación y transiciones para definir una animación.

## <a name="syntax"></a>Sintaxis

```
class CAnimationGroup;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationGroup::CAnimationGroup](#canimationgroup)|Construye un grupo de animación.|
|[CAnimationGroup::-CAnimationGroup](#_dtorcanimationgroup)|Destructor. Se llama cuando se destruye un grupo de animación.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationGroup::Animate](#animate)|Anima un grupo.|
|[CAnimationGroup::ApplyTransitions](#applytransitions)|Aplica transiciones a objetos de animación.|
|[CAnimationGroup::FindAnimationObject](#findanimationobject)|Busca un objeto de animación que contiene la variable de animación especificada.|
|[CAnimationGroup::GetGroupID](#getgroupid)|Devuelve GroupID.|
|[CAnimationGroup::RemoveKeyframes](#removekeyframes)|Quita y, opcionalmente, destruye todos los fotogramas clave que pertenecen a un grupo de animación.|
|[CAnimationGroup::RemoveTransitions](#removetransitions)|Quita las transiciones de los objetos de animación que pertenecen a un grupo de animación.|
|[CAnimationGroup::Schedule](#schedule)|Programa una animación a la hora especificada.|
|[CAnimationGroup::SetAutodestroyTransitions](#setautodestroytransitions)|Dirige que todos los objetos de animación que pertenecen al grupo destruyen automáticamente las transiciones.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationGroup::AddKeyframes](#addkeyframes)|Un ayudante que agrega fotogramas clave a un guión gráfico.|
|[CAnimationGroup::AddTransitions](#addtransitions)|Una aplicación auxiliar que agrega transiciones a un guión gráfico.|
|[CAnimationGroup::CreateTransitions](#createtransitions)|Una aplicación auxiliar que crea objetos de transición COM.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationGroup::m_bAutoclearTransitions](#m_bautocleartransitions)|Especifica cómo borrar las transiciones de los objetos de animación que pertenecen al grupo. Si este miembro es TRUE, las transiciones se quitan automáticamente cuando se ha programado una animación. De lo contrario, debe eliminar las transiciones manualmente.|
|[CAnimationGroup::m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|Especifica cómo destruir objetos de animación. Si este parámetro es TRUE, los objetos de animación se destruirán automáticamente cuando se destruya el grupo. De lo contrario, los objetos de animación deben destruirse manualmente. El valor predeterminado es FALSE. Establezca este valor en TRUE solo si todos los objetos de animación que pertenecen al grupo se asignan dinámicamente con el operador new.|
|[CAnimationGroup::m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|Especifica cómo destruir fotogramas clave. Si este valor es TRUE, se quitan y destruyen todos los fotogramas clave; de lo contrario, se eliminarán de la lista únicamente. El valor predeterminado es TRUE.|
|[CAnimationGroup::m_lstAnimationObjects](#m_lstanimationobjects)|Contiene una lista de objetos de animación.|
|[CAnimationGroup::m_lstKeyFrames](#m_lstkeyframes)|Contiene una lista de fotogramas clave.|
|[CAnimationGroup::m_pStoryboard](#m_pstoryboard)|Apunta al guión gráfico de animación. Este puntero solo es válido después de llamar a Animate.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationGroup::m_nGroupID](#m_ngroupid)|Identificador único del grupo de animación.|
|[CAnimationGroup::m_pParentController](#m_pparentcontroller)|Un puntero al controlador de animación al que pertenece este grupo.|

## <a name="remarks"></a>Observaciones

Los grupos de animación se crean automáticamente mediante el controlador de animación (CAnimationController) al agregar objetos de animación mediante CAnimationController::AddAnimationObject. Un grupo de animación se identifica mediante GroupID, que normalmente se toma como parámetro para manipular grupos de animación. El GroupID se toma del primer objeto de animación que se agrega a un nuevo grupo de animación. Se crea un guión gráfico de animación encapsulado después de llamar a CAnimationController::AnimateGroup y se puede tener acceso a través de m_pStoryboard de miembros públicos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CAnimationGroup`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="canimationgroupcanimationgroup"></a><a name="_dtorcanimationgroup"></a>CAnimationGroup::-CAnimationGroup

Destructor. Se llama cuando se destruye un grupo de animación.

```
~CAnimationGroup();
```

## <a name="canimationgroupaddkeyframes"></a><a name="addkeyframes"></a>CAnimationGroup::AddKeyframes

Un ayudante que agrega fotogramas clave a un guión gráfico.

```cpp
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```

### <a name="parameters"></a>Parámetros

*pStoryboard*<br/>
Puntero a un objeto COM de guión gráfico.

*bAddDeep*<br/>
Especifica si este método debe agregarse a los fotogramas clave del guión gráfico que dependen de otros fotogramas clave.

## <a name="canimationgroupaddtransitions"></a><a name="addtransitions"></a>CAnimationGroup::AddTransitions

Una aplicación auxiliar que agrega transiciones a un guión gráfico.

```cpp
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parámetros

*pStoryboard*<br/>
Puntero a un objeto COM de guión gráfico.

*bDependOnKeyframes*

## <a name="canimationgroupanimate"></a><a name="animate"></a>CAnimationGroup::Animate

Anima un grupo.

```
BOOL Animate(
    IUIAnimationManager* pManager,
    IUIAnimationTimer* pTimer,
    BOOL bScheduleNow);
```

### <a name="parameters"></a>Parámetros

*pManager*<br/>
*pTimer*
*bScheduleNow*

### <a name="return-value"></a>Valor devuelto

TRUESi el método se realiza correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Este método crea un guión gráfico interno, crea y aplica transiciones y programa una animación si bScheduleNow es TRUE. Si bScheduleNow es FALSE, debe llamar a Schedule para iniciar la animación a la hora especificada.

## <a name="canimationgroupapplytransitions"></a><a name="applytransitions"></a>CAnimationGroup::ApplyTransitions

Aplica transiciones a objetos de animación.

```cpp
void ApplyTransitions();
```

### <a name="remarks"></a>Observaciones

Este método ASSERTS en modo de depuración si no se ha creado guión gráfico. Crea primero todas las transiciones, luego agrega fotogramas clave "estáticos" (fotogramas clave que dependen de desplazamientos), agrega transiciones que no dependen de fotogramas clave, agrega fotogramas clave en función de las transiciones y otros fotogramas clave y, por último, añade transiciones que dependen de fotogramas clave.

## <a name="canimationgroupcanimationgroup"></a><a name="canimationgroup"></a>CAnimationGroup::CAnimationGroup

Construye un grupo de animación.

```
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```

### <a name="parameters"></a>Parámetros

*pParentController*<br/>
Puntero al controlador de animación que crea un grupo.

*nGroupID*<br/>
Especifica GroupID.

## <a name="canimationgroupcreatetransitions"></a><a name="createtransitions"></a>CAnimationGroup::CreateTransitions

Una aplicación auxiliar que crea objetos de transición COM.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>Valor devuelto

TRUE es el método se realiza correctamente, de lo contrario FALSE.

## <a name="canimationgroupfindanimationobject"></a><a name="findanimationobject"></a>CAnimationGroup::FindAnimationObject

Busca un objeto de animación que contiene la variable de animación especificada.

```
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parámetros

*pVariable*<br/>
Un puntero a la variable de animación.

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto de animación, o NULL si no se encuentra el objeto de animación.

## <a name="canimationgroupgetgroupid"></a><a name="getgroupid"></a>CAnimationGroup::GetGroupID

Devuelve GroupID.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>Valor devuelto

Un identificador de grupo.

## <a name="canimationgroupm_bautocleartransitions"></a><a name="m_bautocleartransitions"></a>CAnimationGroup::m_bAutoclearTransitions

Especifica cómo borrar las transiciones de los objetos de animación que pertenecen al grupo. Si este miembro es TRUE, las transiciones se quitan automáticamente cuando se ha programado una animación. De lo contrario, debe eliminar las transiciones manualmente.

```
BOOL m_bAutoclearTransitions;
```

## <a name="canimationgroupm_bautodestroyanimationobjects"></a><a name="m_bautodestroyanimationobjects"></a>CAnimationGroup::m_bAutodestroyAnimationObjects

Especifica cómo destruir objetos de animación. Si este parámetro es TRUE, los objetos de animación se destruirán automáticamente cuando se destruya el grupo. De lo contrario, los objetos de animación deben destruirse manualmente. El valor predeterminado es FALSE. Establezca este valor en TRUE solo si todos los objetos de animación que pertenecen al grupo se asignan dinámicamente con el operador new.

```
BOOL m_bAutodestroyAnimationObjects;
```

## <a name="canimationgroupm_bautodestroykeyframes"></a><a name="m_bautodestroykeyframes"></a>CAnimationGroup::m_bAutodestroyKeyframes

Especifica cómo destruir fotogramas clave. Si este valor es TRUE, se quitan y destruyen todos los fotogramas clave; de lo contrario, se eliminarán de la lista únicamente. El valor predeterminado es TRUE.

```
BOOL m_bAutodestroyKeyframes;
```

## <a name="canimationgroupm_lstanimationobjects"></a><a name="m_lstanimationobjects"></a>CAnimationGroup::m_lstAnimationObjects

Contiene una lista de objetos de animación.

```
CObList m_lstAnimationObjects;
```

## <a name="canimationgroupm_lstkeyframes"></a><a name="m_lstkeyframes"></a>CAnimationGroup::m_lstKeyFrames

Contiene una lista de fotogramas clave.

```
CObList m_lstKeyFrames;
```

## <a name="canimationgroupm_ngroupid"></a><a name="m_ngroupid"></a>CAnimationGroup::m_nGroupID

Identificador único del grupo de animación.

```
UINT32 m_nGroupID;
```

## <a name="canimationgroupm_pparentcontroller"></a><a name="m_pparentcontroller"></a>CAnimationGroup::m_pParentController

Un puntero al controlador de animación al que pertenece este grupo.

```
CAnimationController* m_pParentController;
```

## <a name="canimationgroupm_pstoryboard"></a><a name="m_pstoryboard"></a>CAnimationGroup::m_pStoryboard

Apunta al guión gráfico de animación. Este puntero solo es válido después de llamar a Animate.

```
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;
```

## <a name="canimationgroupremovekeyframes"></a><a name="removekeyframes"></a>CAnimationGroup::RemoveKeyframes

Quita y, opcionalmente, destruye todos los fotogramas clave que pertenecen a un grupo de animación.

```cpp
void RemoveKeyframes();
```

### <a name="remarks"></a>Observaciones

Si m_bAutodestroyKeyframes miembro es TRUE, los fotogramas clave se eliminan y destruyen, de lo contrario los fotogramas clave se eliminan de la lista interna de fotogramas clave.

## <a name="canimationgroupremovetransitions"></a><a name="removetransitions"></a>CAnimationGroup::RemoveTransitions

Quita las transiciones de los objetos de animación que pertenecen a un grupo de animación.

```cpp
void RemoveTransitions();
```

### <a name="remarks"></a>Observaciones

Si m_bAutoclearTransitions marca se establece en TRUE, este método recorre en bucle todos los objetos de animación que pertenecen al grupo y llama a CAnimationObject::ClearTransitions(FALSE).

## <a name="canimationgroupschedule"></a><a name="schedule"></a>CAnimationGroup::Schedule

Programa una animación a la hora especificada.

```
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```

### <a name="parameters"></a>Parámetros

*pTimer*<br/>
Un puntero al temporizador de animación.

*time*<br/>
Especifica el tiempo para programar la animación.

### <a name="return-value"></a>Valor devuelto

TRUESi el método se realiza correctamente; FALSE si se produce un error en el método o si no se ha llamado a Animate con bScheduleNow establecido en FALSE.

### <a name="remarks"></a>Observaciones

Llame a esta función para programar una animación a la hora especificada. Debe llamar primero a Animate con bScheduleNow establecido en FALSE.

## <a name="canimationgroupsetautodestroytransitions"></a><a name="setautodestroytransitions"></a>CAnimationGroup::SetAutodestroyTransitions

Dirige que todos los objetos de animación que pertenecen al grupo destruyen automáticamente las transiciones.

```cpp
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

*bAutoDestroy*<br/>
Especifica cómo destruir transiciones.

### <a name="remarks"></a>Observaciones

Establezca este valor en FALSE solo si asigna transiciones en la pila. El valor predeterminado es TRUE, por lo que es muy recomendable asignar objetos de transición mediante el operador new.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
