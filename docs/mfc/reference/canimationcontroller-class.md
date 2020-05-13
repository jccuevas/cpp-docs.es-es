---
title: Clase CAnimationController
ms.date: 03/27/2019
f1_keywords:
- CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::AddAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::AddKeyframeToGroup
- AFXANIMATIONCONTROLLER/CAnimationController::AnimateGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CleanUpGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CreateKeyframe
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationManagerEvent
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnablePriorityComparisonHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnableStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::GetKeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionLibrary
- AFXANIMATIONCONTROLLER/CAnimationController::IsAnimationInProgress
- AFXANIMATIONCONTROLLER/CAnimationController::IsValid
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnBeforeAnimationStart
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCancel
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCompress
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityConclude
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityTrim
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAllAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationController::ScheduleGroup
- AFXANIMATIONCONTROLLER/CAnimationController::SetRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::UpdateAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::OnAfterSchedule
- AFXANIMATIONCONTROLLER/CAnimationController::gkeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::m_bIsValid
- AFXANIMATIONCONTROLLER/CAnimationController::m_lstAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::m_pRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionLibrary
helpviewer_keywords:
- CAnimationController [MFC], CAnimationController
- CAnimationController [MFC], AddAnimationObject
- CAnimationController [MFC], AddKeyframeToGroup
- CAnimationController [MFC], AnimateGroup
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], CreateKeyframe
- CAnimationController [MFC], EnableAnimationManagerEvent
- CAnimationController [MFC], EnableAnimationTimerEventHandler
- CAnimationController [MFC], EnablePriorityComparisonHandler
- CAnimationController [MFC], EnableStoryboardEventHandler
- CAnimationController [MFC], FindAnimationGroup
- CAnimationController [MFC], FindAnimationObject
- CAnimationController [MFC], GetKeyframeStoryboardStart
- CAnimationController [MFC], GetUIAnimationManager
- CAnimationController [MFC], GetUIAnimationTimer
- CAnimationController [MFC], GetUITransitionFactory
- CAnimationController [MFC], GetUITransitionLibrary
- CAnimationController [MFC], IsAnimationInProgress
- CAnimationController [MFC], IsValid
- CAnimationController [MFC], OnAnimationIntegerValueChanged
- CAnimationController [MFC], OnAnimationManagerStatusChanged
- CAnimationController [MFC], OnAnimationTimerPostUpdate
- CAnimationController [MFC], OnAnimationTimerPreUpdate
- CAnimationController [MFC], OnAnimationTimerRenderingTooSlow
- CAnimationController [MFC], OnAnimationValueChanged
- CAnimationController [MFC], OnBeforeAnimationStart
- CAnimationController [MFC], OnHasPriorityCancel
- CAnimationController [MFC], OnHasPriorityCompress
- CAnimationController [MFC], OnHasPriorityConclude
- CAnimationController [MFC], OnHasPriorityTrim
- CAnimationController [MFC], OnStoryboardStatusChanged
- CAnimationController [MFC], OnStoryboardUpdated
- CAnimationController [MFC], RemoveAllAnimationGroups
- CAnimationController [MFC], RemoveAnimationGroup
- CAnimationController [MFC], RemoveAnimationObject
- CAnimationController [MFC], RemoveTransitions
- CAnimationController [MFC], ScheduleGroup
- CAnimationController [MFC], SetRelatedWnd
- CAnimationController [MFC], UpdateAnimationManager
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], OnAfterSchedule
- CAnimationController [MFC], gkeyframeStoryboardStart
- CAnimationController [MFC], m_bIsValid
- CAnimationController [MFC], m_lstAnimationGroups
- CAnimationController [MFC], m_pAnimationManager
- CAnimationController [MFC], m_pAnimationTimer
- CAnimationController [MFC], m_pRelatedWnd
- CAnimationController [MFC], m_pTransitionFactory
- CAnimationController [MFC], m_pTransitionLibrary
ms.assetid: ed294c98-695e-40a6-b940-33ef1d40aa6b
ms.openlocfilehash: 489e931c4063e7bf06ace1cb130b9891253c94d4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750181"
---
# <a name="canimationcontroller-class"></a>Clase CAnimationController

Implementa el controlador de animación, que proporciona una interfaz central para crear y administrar las animaciones.

## <a name="syntax"></a>Sintaxis

```
class CAnimationController : public CObject;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationController::CAnimationController](#canimationcontroller)|Construye un controlador de animación.|
|[CAnimationController::-CAnimationController](#_dtorcanimationcontroller)|Destructor. Se llama cuando se destruye el objeto del controlador de animación.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationController::AddAnimationObject](#addanimationobject)|Agrega un objeto de animación a un grupo que pertenece al controlador de animación.|
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|Agrega un fotograma clave al grupo.|
|[CAnimationController::AnimateGroup](#animategroup)|Prepara un grupo para ejecutar la animación y, opcionalmente, la programa.|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Sobrecargado. Llamado por el marco de trabajo para limpiar el grupo cuando se ha programado la animación.|
|[CAnimationController::CreateKeyframe](#createkeyframe)|Sobrecargado. Crea un fotograma clave que depende de la transición y lo agrega al grupo especificado.|
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|Establece o libera un controlador para llamar cuando cambia el estado del administrador de animaciones.|
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|Establece o libera un controlador para los eventos de temporización y el controlador para las actualizaciones de tiempo.|
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|Establece o libera el controlador de comparación de prioridad para llamar para determinar si un guión gráfico programado se puede cancelar, concluir, recortar o comprimir.|
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|Establece o libera un controlador para el estado del guión gráfico y los eventos de actualización.|
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|Sobrecargado. Busca un grupo de animación por su guión gráfico.|
|[CAnimationController::FindAnimationObject](#findanimationobject)|Busca el objeto de animación que contiene una variable de animación especificada.|
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|Devuelve un fotograma clave que identifica el inicio del guión gráfico.|
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|Proporciona acceso al objeto IUIAnimationManager encapsulado.|
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|Proporciona acceso al objeto Encapsulado IUIAnimationTimer.|
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|Un puntero a IUIAnimationTransitionFactory interfaz o NULL, si se produjo un error en la creación de la biblioteca de transición.|
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|Proporciona acceso al objeto Encapsulado IUIAnimationTransitionLibrary.|
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|Indica si al menos un grupo está reproduciendo animación.|
|[CAnimationController::IsValid](#isvalid)|Indica si el controlador de animación es válido.|
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|Llamado por el marco de trabajo cuando el valor entero de la variable de animación ha cambiado.|
|[CAnimationController::OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|Llamado por el marco de trabajo en respuesta al evento StatusChanged desde el administrador de animación.|
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|Llamado por el marco de trabajo después de que se haya terminado una actualización de animación.|
|[CAnimationController::OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|Llamado por el marco de trabajo antes de que comience una actualización de animación.|
|[CAnimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|Llamado por el marco de trabajo cuando la velocidad de fotogramas de representación para una animación cae por debajo de una velocidad de fotogramas mínima deseable.|
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|Llamado por el marco de trabajo cuando el valor de la variable de animación ha cambiado.|
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|Llamado por el marco de trabajo justo antes de que se programe la animación.|
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|Lo llama el marco para resolver los conflictos de programación.|
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|Lo llama el marco para resolver los conflictos de programación.|
|[CAnimationController::OnHasPriorityConclude](#onhaspriorityconclude)|Lo llama el marco para resolver los conflictos de programación.|
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|Lo llama el marco para resolver los conflictos de programación.|
|[CAnimationController::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Llamado por el marco de trabajo cuando el estado del guión gráfico ha cambiado.|
|[CAnimationController::OnStoryboardUpdated](#onstoryboardupdated)|Llamado por el marco de trabajo cuando se ha actualizado el guión gráfico.|
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|Quita todos los grupos de animación del controlador de animación.|
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|Quita un grupo de animación con el identificador especificado del controlador de animación.|
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|Quitar un objeto de animación del controlador de animación.|
|[CAnimationController::RemoveTransitions](#removetransitions)|Quita las transiciones de los objetos de animación que pertenecen al grupo especificado.|
|[CAnimationController::ScheduleGroup](#schedulegroup)|Programa una animación.|
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|Establece una relación entre el controlador de animación y una ventana.|
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|Dirige al administrador de animaciones que actualice los valores de todas las variables de animación.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Sobrecargado. Un ayudante que limpia el grupo.|
|[CAnimationController::OnAfterSchedule](#onafterschedule)|Llamado por el marco de trabajo cuando se acaba de programar una animación para el grupo especificado.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|Un fotograma clave que representa el inicio del guión gráfico.|
|[CAnimationController::m_bIsValid](#m_bisvalid)|Especifica si un controlador de animación es válido o no. Este miembro se establece en FALSE si el sistema operativo actual no admite la API de animación de Windows.|
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|Una lista de grupos de animación que pertenecen a este controlador de animación.|
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|Almacena un puntero al objeto COM del Administrador de animaciones.|
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|Almacena un puntero al objeto COM del temporizador de animación.|
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|Un puntero a un objeto CWnd relacionado, que se puede volver a dibujar automáticamente cuando el estado del administrador de animaciones ha cambiado o se ha producido un evento posterior a la actualización. Puede ser NULL.|
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|Almacena un puntero al objeto COM de fábrica de transición.|
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|Almacena un puntero al objeto COM de la biblioteca de transición.|

## <a name="remarks"></a>Observaciones

La clase CAnimationController es la clase clave que administra las animaciones. Puede crear una o varias instancias del controlador de animación en una aplicación y, opcionalmente, conectar una instancia de controlador de animación a un CWnd objeto mediante CAnimationController::SetRelatedWnd. Esta conexión es necesaria para enviar mensajes WM_PAINT a la ventana relacionada automáticamente cuando el estado del administrador de animaciones ha cambiado o se ha actualizado el temporizador de animación. Si no habilita esta relación, debe volver a dibujar una ventana que muestre una animación manualmente. Para ello, puede derivar una clase de CAnimationController e invalidar OnAnimationManagerStatusChanged y/o OnAnimationTimerPostUpdate e invalidar una o varias ventanas cuando sea necesario.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

## <a name="canimationcontrollercanimationcontroller"></a><a name="_dtorcanimationcontroller"></a>CAnimationController::-CAnimationController

Destructor. Se llama cuando se destruye el objeto del controlador de animación.

```
virtual ~CAnimationController(void);
```

## <a name="canimationcontrolleraddanimationobject"></a><a name="addanimationobject"></a>CAnimationController::AddAnimationObject

Agrega un objeto de animación a un grupo que pertenece al controlador de animación.

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>Parámetros

*pObject*<br/>
Puntero a un objeto de animación.

### <a name="return-value"></a>Valor devuelto

Un puntero al grupo de animación existente o nuevo donde pObject se ha agregado si la función se realiza correctamente; NULL si pObject ya se ha agregado a un grupo que pertenece a otro controlador de animación.

### <a name="remarks"></a>Observaciones

Llame a este método para agregar un objeto de animación al controlador de animación. Un objeto se agregará a un grupo según GroupID del objeto (consulte CAnimationBaseObject::SetID). El controlador de animación creará un nuevo grupo si es el primer objeto que se agrega con el GroupID especificado. Un objeto de animación solo se puede agregar a un controlador de animación. Si necesita agregar un objeto a otro controlador, llame primero a RemoveAnimationObject. Si llama a SetID con un nuevo GroupID para un objeto que ya se ha agregado a un grupo, el objeto se quitará del grupo anterior y se agregará a otro grupo con el identificador especificado.

## <a name="canimationcontrolleraddkeyframetogroup"></a><a name="addkeyframetogroup"></a>CAnimationController::AddKeyframeToGroup

Agrega un fotograma clave al grupo.

```
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe);
```

### <a name="parameters"></a>Parámetros

*nGroupID*<br/>
Especifica el identificador de grupo.

*pKeyframe*<br/>
Un puntero a un fotograma clave.

### <a name="return-value"></a>Valor devuelto

TRUESi la función se realiza correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Normalmente no es necesario llamar a este método, utilice CAnimationController::CreateKeyframe en su lugar, que crea y agrega el fotograma clave creado a un grupo automáticamente.

## <a name="canimationcontrolleranimategroup"></a><a name="animategroup"></a>CAnimationController::AnimateGroup

Prepara un grupo para ejecutar la animación y, opcionalmente, la programa.

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>Parámetros

*nGroupID*<br/>
Especifica GroupID.

*bScheduleNow*<br/>
Especifica si se va a ejecutar la animación de inmediato.

### <a name="return-value"></a>Valor devuelto

TRUESi la animación se programó y ejecutó correctamente.

### <a name="remarks"></a>Observaciones

Este método realiza el trabajo real creando guión gráfico, agregando variables de animación, aplicando transiciones y estableciendo fotogramas clave. Es posible retrasar la programación si establece bScheduleNow en FALSE. En este caso, el grupo especificado contendrá un guión gráfico que se ha configurado para la animación. En ese momento puede configurar eventos para el guión gráfico y las variables de animación. Cuando realmente necesita ejecutar la llamada de animación CAnimationController::ScheduleGroup.

## <a name="canimationcontrollercanimationcontroller"></a><a name="canimationcontroller"></a>CAnimationController::CAnimationController

Construye un controlador de animación.

```
CAnimationController(void);
```

## <a name="canimationcontrollercleanupgroup"></a><a name="cleanupgroup"></a>CAnimationController::CleanUpGroup

Llamado por el marco de trabajo para limpiar el grupo cuando se ha programado la animación.

```cpp
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parámetros

*nGroupID*<br/>
Especifica GroupID.

*pGroup*<br/>
Un puntero al grupo de animación para limpiar.

### <a name="remarks"></a>Observaciones

Este método quita todas las transiciones y fotogramas clave del grupo especificado, porque no son relevantes después de que se haya programado una animación.

## <a name="canimationcontrollercreatekeyframe"></a><a name="createkeyframe"></a>CAnimationController::CreateKeyframe

Crea un fotograma clave que depende de la transición y lo agrega al grupo especificado.

```
CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,
    CBaseTransition* pTransition);

CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>Parámetros

*nGroupID*<br/>
Especifica el identificador de grupo para el que se crea el fotograma clave.

*pTransición*<br/>
Puntero a la transición. El fotograma clave se insertará en el guion gráfico después de esta transición.

*pKeyframe*<br/>
Puntero al fotograma clave base de este fotograma clave.

*offset*<br/>
Desplazamiento en segundos desde el fotograma clave base especificado por pKeyframe.

### <a name="return-value"></a>Valor devuelto

Puntero al fotograma clave recién creado si la función se ejecuta correctamente.

### <a name="remarks"></a>Observaciones

Puede almacenar el puntero devuelto y basar otros fotogramas clave en el fotograma clave recién creado (véase la segunda sobrecarga). Es posible iniciar las transiciones en los fotogramas clave (véase CBaseTransition::SetKeyframes). No es necesario eliminar fotogramas clave creados de esta manera, ya que los grupos de animación los eliminan automáticamente. Tenga cuidado al crear fotogramas clave basados en otros fotogramas clave y transiciones, y evite las referencias circulares.

## <a name="canimationcontrollerenableanimationmanagerevent"></a><a name="enableanimationmanagerevent"></a>CAnimationController::EnableAnimationManagerEvent

Establece o libera un controlador para llamar cuando cambia el estado del administrador de animaciones.

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
Especifica si se debe establecer o liberar un controlador.

### <a name="return-value"></a>Valor devuelto

TRUESi el controlador se estableció o liberó correctamente.

### <a name="remarks"></a>Observaciones

Cuando se establece un controlador (habilitado) Animación de Windows llama a OnAnimationManagerStatusChanged cuando cambia el estado del administrador de animaciones.

## <a name="canimationcontrollerenableanimationtimereventhandler"></a><a name="enableanimationtimereventhandler"></a>CAnimationController::EnableAnimationTimerEventHandler

Establece o libera un controlador para los eventos de temporización y el controlador para las actualizaciones de tiempo.

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
Especifica si se deben establecer o liberar los controladores.

*idleBehavior*<br/>
Especifica el comportamiento inactivo para el controlador de actualización del temporizador.

### <a name="return-value"></a>Valor devuelto

TRUESi los controladores se establecieron o liberaron correctamente; FALSE si se llama a este método por segunda vez sin liberar primero los controladores, o si se produce cualquier otro error.

### <a name="remarks"></a>Observaciones

Cuando se establecen los controladores (habilitados) Windows Animation API llama a OnAnimationTimerPreUpdate, OnAnimationTimerPostUpdate, OnRenderingTooSlow métodos. Debe habilitar los temporizadores de animación para permitir guiones gráficos de actualización de la API de animación de Windows. De lo contrario, tendrá que llamar a CAnimationController::UpdateAnimationManager para dirigir al administrador de animación que actualice los valores de todas las variables de animación.

## <a name="canimationcontrollerenableprioritycomparisonhandler"></a><a name="enableprioritycomparisonhandler"></a>CAnimationController::EnablePriorityComparisonHandler

Establece o libera el controlador de comparación de prioridad para llamar para determinar si un guión gráfico programado se puede cancelar, concluir, recortar o comprimir.

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>Parámetros

*dwHandlerType*<br/>
Una combinación de UI_ANIMATION_PHT_ marcas (consulte comentarios), que especifica qué controladores establecer o liberar.

### <a name="return-value"></a>Valor devuelto

TRUESi el controlador se estableció o liberó correctamente.

### <a name="remarks"></a>Observaciones

Cuando se establece un controlador (habilitado) Windows Animation llama a los siguientes métodos virtuales en función de dwHandlerType: OnHasPriorityCancel, OnHasPriorityConclude, OnHasPriorityTrim, OnHasPriorityCompress. dwHandler puede ser una combinación de las siguientes marcas: UI_ANIMATION_PHT_NONE - liberar todos los controladores UI_ANIMATION_PHT_CANCEL - establecer Cancel comparison handler UI_ANIMATION_PHT_CONCLUDE - set Conclude comparison handler UI_ANIMATION_PHT_COMPRESS - set Compress comparison handler UI_ANIMATION_PHT_TRIM - set Trim comparison handler UI_ANIMATION_PHT_CANCEL_REMOVE - remove Cancel comparison handler UI_ANIMATION_PHT_CONCLUDE_REMOVE - remove Conclude comparison handler UI_ANIMATION_PHT_COMPRESS_REMOVE - remove Compress comparison handler UI_ANIMATION_PHT_TRIM_REMOVE - eliminar el controlador de comparación Trim

## <a name="canimationcontrollerenablestoryboardeventhandler"></a><a name="enablestoryboardeventhandler"></a>CAnimationController::EnableStoryboardEventHandler

Establece o libera un controlador para el estado del guión gráfico y los eventos de actualización.

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*nGroupID*<br/>
Especifica el identificador de grupo.

*bHabilitar*<br/>
Especifica si se debe establecer o liberar un controlador.

### <a name="return-value"></a>Valor devuelto

TRUESi el controlador se estableció o liberó correctamente; FALSE si ahora se encuentra el grupo de animación especificado o no se ha iniciado la animación para el grupo especificado y su guión gráfico interno es NULL.

### <a name="remarks"></a>Observaciones

Cuando se establece un controlador (habilitado) API de animación de Windows llama a OnStoryboardStatusChanges y OnStoryboardUpdated métodos virtuales. Se debe establecer un controlador después de CAnimationController::Animate se ha llamado para el grupo de animación especificado, porque crea encapsulado IUIAnimationStoryboard objeto.

## <a name="canimationcontrollerfindanimationgroup"></a><a name="findanimationgroup"></a>CAnimationController::FindAnimationGroup

Busca un grupo de animación por su ID de grupo.

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parámetros

*nGroupID*<br/>
Especifica un GroupID.

*pStoryboard*<br/>
Un puntero a un guión gráfico.

### <a name="return-value"></a>Valor devuelto

Un puntero al grupo de animación o NULL si no se encuentra el grupo con el identificador especificado.

### <a name="remarks"></a>Observaciones

Utilice este método para buscar un grupo de animación en tiempo de ejecución. Se crea un grupo y se agrega a la lista interna de grupos de animación cuando se agrega un primer objeto de animación con GroupID determinado al controlador de animación.

## <a name="canimationcontrollerfindanimationobject"></a><a name="findanimationobject"></a>CAnimationController::FindAnimationObject

Busca el objeto de animación que contiene una variable de animación especificada.

```
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,
    CAnimationBaseObject** ppObject,
    CAnimationGroup** ppGroup);
```

### <a name="parameters"></a>Parámetros

*pVariable*<br/>
Un puntero a la variable de animación.

*ppObject*<br/>
Salida. Contiene un puntero al objeto de animación o NULL.

*ppGroup*<br/>
Salida. Contiene un puntero al grupo de animación que contiene el objeto de animación o NULL.

### <a name="return-value"></a>Valor devuelto

TRUESi se ha encontrado el objeto; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Se llama desde controladores de eventos cuando es necesario encontrar un objeto de animación de la variable de animación entrante.

## <a name="canimationcontrollergkeyframestoryboardstart"></a><a name="g_keyframestoryboardstart"></a>CAnimationController::gkeyframeStoryboardStart

Un fotograma clave que representa el inicio del guión gráfico.

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

## <a name="canimationcontrollergetkeyframestoryboardstart"></a><a name="getkeyframestoryboardstart"></a>CAnimationController::GetKeyframeStoryboardStart

Devuelve un fotograma clave que identifica el inicio del guión gráfico.

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>Valor devuelto

Puntero al fotograma clave base, que identifica el inicio del guión gráfico.

### <a name="remarks"></a>Observaciones

Obtenga este fotograma clave para basar cualquier otro fotograma clave o transición en el momento en que se inicia un guión gráfico.

## <a name="canimationcontrollergetuianimationmanager"></a><a name="getuianimationmanager"></a>CAnimationController::GetUIAnimationManager

Proporciona acceso al objeto IUIAnimationManager encapsulado.

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a IUIAnimationManager interfaz o NULL, si se produce un error en la creación del administrador de animaciones.

### <a name="remarks"></a>Observaciones

Si el sistema operativo actual no admite la API de animación de Windows, este método devuelve NULL y después de eso todas las llamadas posteriores en CAnimationController::IsValid devuelven FALSE. Es posible que necesite tener acceso a IUIAnimationManager para llamar a sus métodos de interfaz, que no se ajustan mediante el controlador de animación.

## <a name="canimationcontrollergetuianimationtimer"></a><a name="getuianimationtimer"></a>CAnimationController::GetUIAnimationTimer

Proporciona acceso al objeto Encapsulado IUIAnimationTimer.

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a IUIAnimationTimer interfaz o NULL, si se produjo un error en la creación del temporizador de animación.

### <a name="remarks"></a>Observaciones

Si el sistema operativo actual no admite la API de animación de Windows, este método devuelve NULL y después de eso todas las llamadas posteriores en CAnimationController::IsValid devuelven FALSE.

## <a name="canimationcontrollergetuitransitionfactory"></a><a name="getuitransitionfactory"></a>CAnimationController::GetUITransitionFactory

Un puntero a IUIAnimationTransitionFactory interfaz o NULL, si se produjo un error en la creación de la biblioteca de transición.

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a IUIAnimationTransitionFactory o NULL, si se produjo un error en la creación de la fábrica de transición.

### <a name="remarks"></a>Observaciones

Si el sistema operativo actual no admite la API de animación de Windows, este método devuelve NULL y después de eso todas las llamadas posteriores en CAnimationController::IsValid devuelven FALSE.

## <a name="canimationcontrollergetuitransitionlibrary"></a><a name="getuitransitionlibrary"></a>CAnimationController::GetUITransitionLibrary

Proporciona acceso al objeto Encapsulado IUIAnimationTransitionLibrary.

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a IUIAnimationTransitionLibrary interfaz o NULL, si se produce un error en la creación de la biblioteca de transición.

### <a name="remarks"></a>Observaciones

Si el sistema operativo actual no admite la API de animación de Windows, este método devuelve NULL y después de eso todas las llamadas posteriores en CAnimationController::IsValid devuelven FALSE.

## <a name="canimationcontrollerisanimationinprogress"></a><a name="isanimationinprogress"></a>CAnimationController::IsAnimationInProgress

Indica si al menos un grupo está reproduciendo animación.

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>Valor devuelto

TRUESi hay una animación en curso para este controlador de animación; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Comprueba el estado del administrador de animaciones y devuelve TRUE si el estado es UI_ANIMATION_MANAGER_BUSY.

## <a name="canimationcontrollerisvalid"></a><a name="isvalid"></a>CAnimationController::IsValid

Indica si el controlador de animación es válido.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el controlador de animación es válido; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Este método devuelve FALSE solo si la API de animación de Windows no se admite en el sistema operativo actual y se produjo un error en la creación del administrador de animaciones porque no está registrado. Debe llamar a GetUIAnimationManager al menos una vez después de la inicialización de bibliotecas COM para provocar la configuración de esta marca.

## <a name="canimationcontrollerm_bisvalid"></a><a name="m_bisvalid"></a>CAnimationController::m_bIsValid

Especifica si un controlador de animación es válido o no. Este miembro se establece en FALSE si el sistema operativo actual no admite la API de animación de Windows.

```
BOOL m_bIsValid;
```

## <a name="canimationcontrollerm_lstanimationgroups"></a><a name="m_lstanimationgroups"></a>CAnimationController::m_lstAnimationGroups

Una lista de grupos de animación que pertenecen a este controlador de animación.

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

## <a name="canimationcontrollerm_panimationmanager"></a><a name="m_panimationmanager"></a>CAnimationController::m_pAnimationManager

Almacena un puntero al objeto COM del Administrador de animaciones.

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

## <a name="canimationcontrollerm_panimationtimer"></a><a name="m_panimationtimer"></a>CAnimationController::m_pAnimationTimer

Almacena un puntero al objeto COM del temporizador de animación.

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

## <a name="canimationcontrollerm_prelatedwnd"></a><a name="m_prelatedwnd"></a>CAnimationController::m_pRelatedWnd

Un puntero a un objeto CWnd relacionado, que se puede volver a dibujar automáticamente cuando el estado del administrador de animaciones ha cambiado o se ha producido un evento posterior a la actualización. Puede ser NULL.

```
CWnd* m_pRelatedWnd;
```

## <a name="canimationcontrollerm_ptransitionfactory"></a><a name="m_ptransitionfactory"></a>CAnimationController::m_pTransitionFactory

Almacena un puntero al objeto COM de fábrica de transición.

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

## <a name="canimationcontrollerm_ptransitionlibrary"></a><a name="m_ptransitionlibrary"></a>CAnimationController::m_pTransitionLibrary

Almacena un puntero al objeto COM de la biblioteca de transición.

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

## <a name="canimationcontrolleronafterschedule"></a><a name="onafterschedule"></a>CAnimationController::OnAfterSchedule

Llamado por el marco de trabajo cuando se acaba de programar una animación para el grupo especificado.

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parámetros

*pGroup*<br/>
Un puntero a un grupo de animación, que se ha programado.

### <a name="remarks"></a>Observaciones

La implementación predeterminada quita los fotogramas clave del grupo especificado y las transiciones de las variables de animación que pertenecen al grupo especificado. Se puede invalidar en una clase derivada para realizar cualquier acción adicional según la programación de animación.

## <a name="canimationcontrolleronanimationintegervaluechanged"></a><a name="onanimationintegervaluechanged"></a>CAnimationController::OnAnimationIntegerValueChanged

Llamado por el marco de trabajo cuando el valor entero de la variable de animación ha cambiado.

```
virtual void OnAnimationIntegerValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    INT32 newValue,
    INT32 prevValue);
```

### <a name="parameters"></a>Parámetros

*pGroup*<br/>
Puntero a un grupo de animación que contiene un objeto de animación cuyo valor ha cambiado.

*pObject*<br/>
Puntero a un objeto de animación que contiene una variable de animación cuyo valor ha cambiado.

*Variable*<br/>
Un puntero a una variable de animación.

*newValue*<br/>
Especifica un nuevo valor.

*prevValue*<br/>
Especifica el valor anterior.

### <a name="remarks"></a>Observaciones

Se llama a este método si habilita eventos de variables de animación con EnableIntegerValueChangedEvent llamado para una variable de animación específica o un objeto de animación. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación.

## <a name="canimationcontrolleronanimationmanagerstatuschanged"></a><a name="onanimationmanagerstatuschanged"></a>CAnimationController::OnAnimationManagerStatusChanged

Llamado por el marco de trabajo en respuesta al evento StatusChanged desde el administrador de animación.

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Parámetros

*newStatus*<br/>
Nuevo estado del administrador de animaciones.

*previousEstado*<br/>
Estado anterior del administrador de animaciones.

### <a name="remarks"></a>Observaciones

Se llama a este método si habilita eventos del administrador de animaciones con EnableAnimationManagerEvent. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación. La implementación predeterminada actualiza una ventana relacionada si se ha establecido con SetRelatedWnd.

## <a name="canimationcontrolleronanimationtimerpostupdate"></a><a name="onanimationtimerpostupdate"></a>CAnimationController::OnAnimationTimerPostUpdate

Llamado por el marco de trabajo después de que se haya terminado una actualización de animación.

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>Observaciones

Se llama a este método si habilita controladores de eventos del temporizador mediante EnableAnimationTimerEventHandler. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación.

## <a name="canimationcontrolleronanimationtimerpreupdate"></a><a name="onanimationtimerpreupdate"></a>CAnimationController::OnAnimationTimerPreUpdate

Llamado por el marco de trabajo antes de que comience una actualización de animación.

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>Observaciones

Se llama a este método si habilita controladores de eventos del temporizador mediante EnableAnimationTimerEventHandler. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación.

## <a name="canimationcontrolleronanimationtimerrenderingtooslow"></a><a name="onanimationtimerrenderingtooslow"></a>CAnimationController::OnAnimationTimerRenderingTooSlow

Llamado por el marco de trabajo cuando la velocidad de fotogramas de representación para una animación cae por debajo de una velocidad de fotogramas mínima deseable.

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>Parámetros

*Fps*<br/>
La velocidad de fotogramas actual en fotogramas por segundo.

### <a name="remarks"></a>Observaciones

Se llama a este método si habilita controladores de eventos del temporizador mediante EnableAnimationTimerEventHandler. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación. La velocidad de fotogramas mínima deseable se especifica mediante una llamada a IUIAnimationTimer::SetFrameRateThreshold.

## <a name="canimationcontrolleronanimationvaluechanged"></a><a name="onanimationvaluechanged"></a>CAnimationController::OnAnimationValueChanged

Llamado por el marco de trabajo cuando el valor de la variable de animación ha cambiado.

```
virtual void OnAnimationValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    DOUBLE newValue,
    DOUBLE prevValue);
```

### <a name="parameters"></a>Parámetros

*pGroup*<br/>
Puntero a un grupo de animación que contiene un objeto de animación cuyo valor ha cambiado.

*pObject*<br/>
Puntero a un objeto de animación que contiene una variable de animación cuyo valor ha cambiado.

*Variable*<br/>
Un puntero a una variable de animación.

*newValue*<br/>
Especifica un nuevo valor.

*prevValue*<br/>
Especifica el valor anterior.

### <a name="remarks"></a>Observaciones

Se llama a este método si habilita eventos de variables de animación con EnableValueChangedEvent llamado para una variable de animación específica o un objeto de animación. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación.

## <a name="canimationcontrolleronbeforeanimationstart"></a><a name="onbeforeanimationstart"></a>CAnimationController::OnBeforeAnimationStart

Llamado por el marco de trabajo justo antes de que se programe la animación.

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parámetros

*pGroup*<br/>
Puntero a un grupo de animación cuya animación está a punto de iniciarse.

### <a name="remarks"></a>Observaciones

Esta llamada se enruta a CWnd relacionado y se puede invalidar en una clase derivada para realizar cualquier acción adicional antes de que se inicie la animación para el grupo especificado.

## <a name="canimationcontrolleronhasprioritycancel"></a><a name="onhasprioritycancel"></a>CAnimationController::OnHasPriorityCancel

Lo llama el marco para resolver los conflictos de programación.

```
virtual BOOL OnHasPriorityCancel(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parámetros

*pGroupScheduled*<br/>
El grupo que posee el guion gráfico actualmente programado.

*pGroupNew*<br/>
El grupo que posee el nuevo guion gráfico que está en conflicto de programación con el guion gráfico programado que pertenece a pGroupScheduled.

*priorityEffect*<br/>
Efecto potencial en pGroupNew si pGroupScheduled tiene una prioridad más alta.

### <a name="return-value"></a>Valor devuelto

Debe devolver TRUE si el guion gráfico propiedad de pGroupNew tiene prioridad. Debe devolver FALSE si el guion gráfico propiedad de pGroupNew tiene prioridad.

### <a name="remarks"></a>Observaciones

Se llama a este método si se habilitan eventos de comparación de prioridad mediante CAnimationController::EnablePriorityComparisonHandler y se especifica UI_ANIMATION_PHT_CANCEL. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación. Lea la documentación de la API de animación de Windows para obtener más información sobre [la administración](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)de conflictos.

## <a name="canimationcontrolleronhasprioritycompress"></a><a name="onhasprioritycompress"></a>CAnimationController::OnHasPriorityCompress

Lo llama el marco para resolver los conflictos de programación.

```
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parámetros

*pGroupScheduled*<br/>
El grupo que posee el guion gráfico actualmente programado.

*pGroupNew*<br/>
El grupo que posee el nuevo guion gráfico que está en conflicto de programación con el guion gráfico programado que pertenece a pGroupScheduled.

*priorityEffect*<br/>
Efecto potencial en pGroupNew si pGroupScheduled tiene una prioridad más alta.

### <a name="return-value"></a>Valor devuelto

Debe devolver TRUE si el guion gráfico propiedad de pGroupNew tiene prioridad. Debe devolver FALSE si el guion gráfico propiedad de pGroupNew tiene prioridad.

### <a name="remarks"></a>Observaciones

Se llama a este método si se habilitan eventos de comparación de prioridad mediante CAnimationController::EnablePriorityComparisonHandler y se especifica UI_ANIMATION_PHT_COMPRESS. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación. Lea la documentación de la API de animación de Windows para obtener más información sobre [la administración](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)de conflictos.

## <a name="canimationcontrolleronhaspriorityconclude"></a><a name="onhaspriorityconclude"></a>CAnimationController::OnHasPriorityConclude

Lo llama el marco para resolver los conflictos de programación.

```
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parámetros

*pGroupScheduled*<br/>
El grupo que posee el guion gráfico actualmente programado.

*pGroupNew*<br/>
El grupo que posee el nuevo guion gráfico que está en conflicto de programación con el guion gráfico programado que pertenece a pGroupScheduled.

*priorityEffect*<br/>
Efecto potencial en pGroupNew si pGroupScheduled tiene una prioridad más alta.

### <a name="return-value"></a>Valor devuelto

Debe devolver TRUE si el guion gráfico propiedad de pGroupNew tiene prioridad. Debe devolver FALSE si el guion gráfico propiedad de pGroupNew tiene prioridad.

### <a name="remarks"></a>Observaciones

Se llama a este método si se habilitan eventos de comparación de prioridad mediante CAnimationController::EnablePriorityComparisonHandler y se especifica UI_ANIMATION_PHT_CONCLUDE. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación. Lea la documentación de la API de animación de Windows para obtener más información sobre [la administración](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)de conflictos.

## <a name="canimationcontrolleronhasprioritytrim"></a><a name="onhasprioritytrim"></a>CAnimationController::OnHasPriorityTrim

Lo llama el marco para resolver los conflictos de programación.

```
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parámetros

*pGroupScheduled*<br/>
El grupo que posee el guion gráfico actualmente programado.

*pGroupNew*<br/>
El grupo que posee el nuevo guion gráfico que está en conflicto de programación con el guion gráfico programado que pertenece a pGroupScheduled.

*priorityEffect*<br/>
Efecto potencial en pGroupNew si pGroupScheduled tiene una prioridad más alta.

### <a name="return-value"></a>Valor devuelto

Debe devolver TRUE si el guion gráfico propiedad de pGroupNew tiene prioridad. Debe devolver FALSE si el guion gráfico propiedad de pGroupNew tiene prioridad.

### <a name="remarks"></a>Observaciones

Se llama a este método si se habilitan eventos de comparación de prioridad mediante CAnimationController::EnablePriorityComparisonHandler y se especifica UI_ANIMATION_PHT_TRIM. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación. Lea la documentación de la API de animación de Windows para obtener más información sobre [la administración](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)de conflictos.

## <a name="canimationcontrolleronstoryboardstatuschanged"></a><a name="onstoryboardstatuschanged"></a>CAnimationController::OnStoryboardStatusChanged

Llamado por el marco de trabajo cuando el estado del guión gráfico ha cambiado.

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>Parámetros

*pGroup*<br/>
Puntero a un grupo de animación que posee el guión gráfico cuyo estado ha cambiado.

*newStatus*<br/>
Especifica el nuevo estado.

*previousEstado*<br/>
Especifica el estado anterior.

### <a name="remarks"></a>Observaciones

Se llama a este método si habilita eventos de guión gráfico mediante CAnimationController::EnableStoryboardEventHandler. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación.

## <a name="canimationcontrolleronstoryboardupdated"></a><a name="onstoryboardupdated"></a>CAnimationController::OnStoryboardUpdated

Llamado por el marco de trabajo cuando se ha actualizado el guión gráfico.

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parámetros

*pGroup*<br/>
Puntero a un grupo que posee el guión gráfico.

### <a name="remarks"></a>Observaciones

Se llama a este método si habilita eventos de guión gráfico mediante CAnimationController::EnableStoryboardEventHandler. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación.

## <a name="canimationcontrollerremoveallanimationgroups"></a><a name="removeallanimationgroups"></a>CAnimationController::RemoveAllAnimationGroups

Quita todos los grupos de animación del controlador de animación.

```cpp
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>Observaciones

Se eliminarán todos los grupos, su puntero, si se almacena en el nivel de aplicación, debe invalidarse. Si CAnimationGroup::m_bAutodestroyAnimationObjects para un grupo que se va a eliminar es TRUE, se eliminarán todos los objetos de animación que pertenezcan a ese grupo; de lo contrario, sus referencias al controlador de animación primario se establecerán en NULL y se pueden agregar a otro controlador.

## <a name="canimationcontrollerremoveanimationgroup"></a><a name="removeanimationgroup"></a>CAnimationController::RemoveAnimationGroup

Quita un grupo de animación con el identificador especificado del controlador de animación.

```cpp
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>Parámetros

*nGroupID*<br/>
Especifica el identificador del grupo de animación.

### <a name="remarks"></a>Observaciones

Este método quita un grupo de animación de la lista interna de grupos y lo elimina, por lo tanto, si almacenó un puntero a ese grupo de animación, debe invalidarse. Si CAnimationGroup::m_bAutodestroyAnimationObjects es TRUE, se eliminarán todos los objetos de animación que pertenezcan a ese grupo; de lo contrario, sus referencias al controlador de animación primario se establecerán en NULL y se pueden agregar a otro controlador.

## <a name="canimationcontrollerremoveanimationobject"></a><a name="removeanimationobject"></a>CAnimationController::RemoveAnimationObject

Quitar un objeto de animación del controlador de animación.

```cpp
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>Parámetros

*pObject*<br/>
Puntero a un objeto de animación.

*bNoDelete*<br/>
Si este parámetro es TRUE, el objeto no se eliminará al quitar.

### <a name="remarks"></a>Observaciones

Quita un objeto de animación del controlador de animación y del grupo de animación. Llame a esta función si un objeto determinado ya no se debe animar, o si necesita mover el objeto a otro controlador de animación. En el último caso bNoDelete debe ser TRUE.

## <a name="canimationcontrollerremovetransitions"></a><a name="removetransitions"></a>CAnimationController::RemoveTransitions

Quita las transiciones de los objetos de animación que pertenecen al grupo especificado.

```cpp
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>Parámetros

*nGroupID*<br/>
Especifica el identificador de grupo.

### <a name="remarks"></a>Observaciones

El grupo recorre en bucle sus objetos de animación y llama a ClearTransitions(FALSE) para cada objeto de animación. El marco de trabajo llama a este método después de que se haya programado la animación.

## <a name="canimationcontrollerschedulegroup"></a><a name="schedulegroup"></a>CAnimationController::ScheduleGroup

Programa una animación.

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>Parámetros

*nGroupID*<br/>
Especifica el IDENTIFICADOR de grupo de animación que se va a programar.

*time*<br/>
Especifica el tiempo de programación.

### <a name="return-value"></a>Valor devuelto

TRUESi la animación se programó correctamente. FALSE si no se ha creado el guión gráfico o se produce otro error.

### <a name="remarks"></a>Observaciones

Debe llamar a AnimateGroup con el parámetro bScheduleNow establecido en FALSE anterior ScheduleGroup. Puede especificar el tiempo de animación deseado obtenido de IUIAnimationTimer::GetTime. Si el parámetro time es 0.0, la animación se programa para la hora actual.

## <a name="canimationcontrollersetrelatedwnd"></a><a name="setrelatedwnd"></a>CAnimationController::SetRelatedWnd

Establece una relación entre el controlador de animación y una ventana.

```cpp
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero al objeto de ventana que se va a establecer.

### <a name="remarks"></a>Observaciones

Si se establece un objeto CWnd relacionado, el controlador de animación puede actualizarlo automáticamente (enviar WM_PAINT mensaje) cuando el estado del administrador de animación ha cambiado o se ha producido el evento de actualización posterior del temporizador.

## <a name="canimationcontrollerupdateanimationmanager"></a><a name="updateanimationmanager"></a>CAnimationController::UpdateAnimationManager

Dirige al administrador de animaciones que actualice los valores de todas las variables de animación.

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>Observaciones

Llamar a este método avanza el administrador de animaciones a la hora actual, cambiando los estados de los guiones gráficos según sea necesario y actualizando las variables de animación a los valores interpolados adecuados. Internamente este método llama a IUIAnimationTimer::GetTime(timeNow) y IUIAnimationManager::Update(timeNow). Invalide este método en una clase derivada para personalizar este comportamiento.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
