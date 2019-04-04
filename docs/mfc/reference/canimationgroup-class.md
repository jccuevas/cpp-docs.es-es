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
ms.openlocfilehash: 32b2adfee2a36139a11caa12fa98bd240b0732dd
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565992"
---
# <a name="canimationgroup-class"></a>Clase CAnimationGroup

Implementa un grupo de animación, que combina un guión gráfico de animación, objetos de animación y transiciones para definir una animación.

## <a name="syntax"></a>Sintaxis

```
class CAnimationGroup;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationGroup::CAnimationGroup](#canimationgroup)|Crea un grupo de animación.|
|[CAnimationGroup::~CAnimationGroup](#_dtorcanimationgroup)|Destructor. Se llama cuando se está destruyendo un grupo de animación.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationGroup::Animate](#animate)|Se anima a un grupo.|
|[CAnimationGroup::ApplyTransitions](#applytransitions)|Aplica las transiciones a objetos de animación.|
|[CAnimationGroup::FindAnimationObject](#findanimationobject)|Busca un objeto de animación que contiene la variable de animación especificados.|
|[CAnimationGroup::GetGroupID](#getgroupid)|Devuelve GroupID.|
|[CAnimationGroup::RemoveKeyframes](#removekeyframes)|Quita y, opcionalmente, destruye todos los fotogramas clave que pertenecen a un grupo de animación.|
|[CAnimationGroup::RemoveTransitions](#removetransitions)|Quita las transiciones de los objetos de animación que pertenecen a un grupo de animación.|
|[CAnimationGroup::Schedule](#schedule)|Programa una animación a la hora especificada.|
|[CAnimationGroup::SetAutodestroyTransitions](#setautodestroytransitions)|Dirige las transiciones de destrucción de todos los objetos de animación que pertenecen al grupo automáticamente.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CAnimationGroup::AddKeyframes](#addkeyframes)|Una aplicación auxiliar que agrega los fotogramas clave a un guión gráfico.|
|[CAnimationGroup::AddTransitions](#addtransitions)|Una aplicación auxiliar que agrega las transiciones a un guión gráfico.|
|[CAnimationGroup::CreateTransitions](#createtransitions)|Una aplicación auxiliar que crea los objetos COM de transición.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CAnimationGroup::m_bAutoclearTransitions](#m_bautocleartransitions)|Especifica cómo borrar las transiciones de los objetos de animación que pertenecen al grupo. Si este miembro es TRUE, las transiciones se eliminan automáticamente cuando se ha programado una animación. En caso contrario, deberá quitar manualmente las transiciones.|
|[CAnimationGroup::m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|Especifica cómo destruir objetos de animación. Si este parámetro es TRUE, los objetos de animación se destruirán automáticamente cuando se destruye el grupo. En caso contrario, los objetos de animación deben destruirse manualmente. El valor predeterminado es FALSE. Establezca este valor en TRUE solo si todos los objetos de animación que pertenecen al grupo se asignan dinámicamente con el operador new.|
|[CAnimationGroup::m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|Especifica cómo destruir los fotogramas clave. Si este valor es TRUE, se quitan todos los fotogramas clave y se destruye; en caso contrario, se quitan de la lista solo. El valor predeterminado es TRUE.|
|[CAnimationGroup::m_lstAnimationObjects](#m_lstanimationobjects)|Contiene una lista de objetos de animación.|
|[CAnimationGroup::m_lstKeyFrames](#m_lstkeyframes)|Contiene una lista de fotogramas clave.|
|[CAnimationGroup::m_pStoryboard](#m_pstoryboard)|Apunta al guión gráfico de animación. Este puntero es válido solo después de la llamada a animar.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Name|Descripción|
|----------|-----------------|
|[CAnimationGroup::m_nGroupID](#m_ngroupid)|Un identificador único del grupo de animación.|
|[CAnimationGroup::m_pParentController](#m_pparentcontroller)|Un puntero al controlador de animación que pertenece este grupo.|

## <a name="remarks"></a>Comentarios

Grupos de animación mediante el controlador de animación (CAnimationController) se crean automáticamente al agregar objetos de animación mediante CAnimationController::AddAnimationObject. Un grupo de animación se identifica mediante el elemento GroupID, que normalmente se toma como parámetro para manipular grupos de animación. GroupID se toma del primer objeto de animación que se agrega a un nuevo grupo de animación. Después de llamar a CAnimationController::AnimateGroup y se puede acceder mediante m_pStoryboard miembro público, se crea un guión gráfico de animación encapsulado.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CAnimationGroup`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="_dtorcanimationgroup"></a>  CAnimationGroup::~CAnimationGroup

Destructor. Se llama cuando se está destruyendo un grupo de animación.

```
~CAnimationGroup();
```

##  <a name="addkeyframes"></a>  CAnimationGroup::AddKeyframes

Una aplicación auxiliar que agrega los fotogramas clave a un guión gráfico.

```
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```

### <a name="parameters"></a>Parámetros

*pStoryboard*<br/>
Un puntero a un objeto COM de guión gráfico.

*bAddDeep*<br/>
Especifica si este método debe agregar a los fotogramas clave de guión gráfico que dependen de otros fotogramas clave.

##  <a name="addtransitions"></a>  CAnimationGroup::AddTransitions

Una aplicación auxiliar que agrega las transiciones a un guión gráfico.

```
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parámetros

*pStoryboard*<br/>
Un puntero a un objeto COM de guión gráfico.

*bDependOnKeyframes*

##  <a name="animate"></a>  CAnimationGroup::Animate

Se anima a un grupo.

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

TRUE si el método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método crea un guión gráfico interno, crea y aplica las transiciones y programa una animación si bScheduleNow es TRUE. Si bScheduleNow es FALSE, se debe llamar a la programación para iniciar la animación a la hora especificada.

##  <a name="applytransitions"></a>  CAnimationGroup::ApplyTransitions

Aplica las transiciones a objetos de animación.

```
void ApplyTransitions();
```

### <a name="remarks"></a>Comentarios

Este método se DECLARA en modo de depuración si no ha creado el guión gráfico. Crea en primer lugar, todas las transiciones, a continuación, agrega los fotogramas clave "static" (fotogramas clave que dependen de los desplazamientos), agrega las transiciones que no dependen de los fotogramas clave, agrega otros fotogramas clave y fotogramas clave según las transiciones y finalmente agrega transiciones que dependen de los fotogramas clave .

##  <a name="canimationgroup"></a>  CAnimationGroup::CAnimationGroup

Crea un grupo de animación.

```
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```

### <a name="parameters"></a>Parámetros

*pParentController*<br/>
Un puntero al controlador de animación que se crea un grupo.

*nGroupID*<br/>
Especifica el Id.

##  <a name="createtransitions"></a>  CAnimationGroup::CreateTransitions

Una aplicación auxiliar que crea los objetos COM de transición.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>Valor devuelto

TRUE es el método tiene éxito, en caso contrario, FALSE.

##  <a name="findanimationobject"></a>  CAnimationGroup::FindAnimationObject

Busca un objeto de animación que contiene la variable de animación especificados.

```
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parámetros

*pVariable*<br/>
Un puntero a la variable de animación.

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto de animación, o NULL si no se encuentra el objeto de animación.

##  <a name="getgroupid"></a>  CAnimationGroup::GetGroupID

Devuelve GroupID.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>Valor devuelto

Un identificador de grupo.

##  <a name="m_bautocleartransitions"></a>  CAnimationGroup::m_bAutoclearTransitions

Especifica cómo borrar las transiciones de los objetos de animación que pertenecen al grupo. Si este miembro es TRUE, las transiciones se eliminan automáticamente cuando se ha programado una animación. En caso contrario, deberá quitar manualmente las transiciones.

```
BOOL m_bAutoclearTransitions;
```

##  <a name="m_bautodestroyanimationobjects"></a>  CAnimationGroup::m_bAutodestroyAnimationObjects

Especifica cómo destruir objetos de animación. Si este parámetro es TRUE, los objetos de animación se destruirán automáticamente cuando se destruye el grupo. En caso contrario, los objetos de animación deben destruirse manualmente. El valor predeterminado es FALSE. Establezca este valor en TRUE solo si todos los objetos de animación que pertenecen al grupo se asignan dinámicamente con el operador new.

```
BOOL m_bAutodestroyAnimationObjects;
```

##  <a name="m_bautodestroykeyframes"></a>  CAnimationGroup::m_bAutodestroyKeyframes

Especifica cómo destruir los fotogramas clave. Si este valor es TRUE, se quitan todos los fotogramas clave y se destruye; en caso contrario, se quitan de la lista solo. El valor predeterminado es TRUE.

```
BOOL m_bAutodestroyKeyframes;
```

##  <a name="m_lstanimationobjects"></a>  CAnimationGroup::m_lstAnimationObjects

Contiene una lista de objetos de animación.

```
CObList m_lstAnimationObjects;
```

##  <a name="m_lstkeyframes"></a>  CAnimationGroup::m_lstKeyFrames

Contiene una lista de fotogramas clave.

```
CObList m_lstKeyFrames;
```

##  <a name="m_ngroupid"></a>  CAnimationGroup::m_nGroupID

Un identificador único del grupo de animación.

```
UINT32 m_nGroupID;
```

##  <a name="m_pparentcontroller"></a>  CAnimationGroup::m_pParentController

Un puntero al controlador de animación que pertenece este grupo.

```
CAnimationController* m_pParentController;
```

##  <a name="m_pstoryboard"></a>  CAnimationGroup::m_pStoryboard

Apunta al guión gráfico de animación. Este puntero es válido solo después de la llamada a animar.

```
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;
```

##  <a name="removekeyframes"></a>  CAnimationGroup::RemoveKeyframes

Quita y, opcionalmente, destruye todos los fotogramas clave que pertenecen a un grupo de animación.

```
void RemoveKeyframes();
```

### <a name="remarks"></a>Comentarios

Si el miembro m_bAutodestroyKeyframes es TRUE, entonces los fotogramas clave se quitan y se destruye, en caso contrario, los fotogramas clave solo se quitan de la lista interna de los fotogramas clave.

##  <a name="removetransitions"></a>  CAnimationGroup::RemoveTransitions

Quita las transiciones de los objetos de animación que pertenecen a un grupo de animación.

```
void RemoveTransitions();
```

### <a name="remarks"></a>Comentarios

Si marca m_bAutoclearTransitions se establece en TRUE, este método recorre en iteración todos los objetos de animación que pertenecen al grupo y llama a CAnimationObject::ClearTransitions(FALSE).

##  <a name="schedule"></a>  CAnimationGroup::Schedule

Programa una animación a la hora especificada.

```
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```

### <a name="parameters"></a>Parámetros

*pTimer*<br/>
Un puntero al temporizador de animación.

*time*<br/>
Especifica la hora para programar la animación.

### <a name="return-value"></a>Valor devuelto

TRUE si el método se realiza correctamente; FALSE si se produce un error en el método o animar no se ha llamado con bScheduleNow establecido en FALSE.

### <a name="remarks"></a>Comentarios

Llame a esta función para programar una animación a la hora especificada. Se debe llamar a animar con bScheduleNow establecido en FALSE en primer lugar.

##  <a name="setautodestroytransitions"></a>  CAnimationGroup::SetAutodestroyTransitions

Dirige las transiciones de destrucción de todos los objetos de animación que pertenecen al grupo automáticamente.

```
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

*bAutoDestroy*<br/>
Especifica cómo destruir las transiciones.

### <a name="remarks"></a>Comentarios

Establezca este valor en FALSE solo si asigna las transiciones en la pila. El valor predeterminado es TRUE, por lo tanto, es muy recomendable para asignar objetos de la transición con operador nuevo.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
