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
ms.openlocfilehash: 9039d44d9ef36a47c11b3ecaddf232ad427727c4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507649"
---
# <a name="canimationcontroller-class"></a>Clase CAnimationController

Implementa el controlador de animación, que proporciona una interfaz central para crear y administrar las animaciones.

## <a name="syntax"></a>Sintaxis

```
class CAnimationController : public CObject;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAnimationController::CAnimationController](#canimationcontroller)|Crea un controlador de animación.|
|[CAnimationController::~CAnimationController](#_dtorcanimationcontroller)|Destructor. Se llama cuando se destruye el objeto de controlador de animación.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAnimationController::AddAnimationObject](#addanimationobject)|Agrega un objeto Animation a un grupo que pertenece al controlador de animaciones.|
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|Agrega un fotograma clave al grupo.|
|[CAnimationController::AnimateGroup](#animategroup)|Prepara un grupo para ejecutar la animación y, de forma opcional, programarlo.|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Sobrecargado. Lo llama el marco de trabajo para limpiar el grupo cuando se ha programado la animación.|
|[CAnimationController::CreateKeyframe](#createkeyframe)|Sobrecargado. Crea un fotograma clave que depende de la transición y lo agrega al grupo especificado.|
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|Establece o libera un controlador al que se llama cuando cambia el estado del administrador de animaciones.|
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|Establece o libera un controlador para los eventos de control de tiempo y el controlador para las actualizaciones de control de tiempo.|
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|Establece o libera el controlador de comparación de prioridades que se va a llamar para determinar si un guion gráfico programado se puede cancelar, concluir, recortar o comprimir.|
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|Establece o libera un controlador para los eventos de actualización y estado de guion gráfico.|
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|Sobrecargado. Busca un grupo de animaciones por su guion gráfico.|
|[CAnimationController::FindAnimationObject](#findanimationobject)|Busca un objeto de animación que contiene una variable de animación especificada.|
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|Devuelve un fotograma clave que identifica el inicio de un guion gráfico.|
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|Proporciona acceso al objeto IUIAnimationManager encapsulado.|
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|Proporciona acceso al objeto IUIAnimationTimer encapsulado.|
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|Un puntero a la interfaz IUIAnimationTransitionFactory o NULL si se produce un error en la creación de la biblioteca de transición.|
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|Proporciona acceso al objeto IUIAnimationTransitionLibrary encapsulado.|
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|Indica si al menos un grupo está reproduciendo animación.|
|[CAnimationController::IsValid](#isvalid)|Indica si el controlador de animación es válido.|
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|Lo llama el marco de trabajo cuando ha cambiado el valor entero de la variable de animación.|
|[CAnimationController::OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|Lo llama el marco de trabajo en respuesta al evento StatusChanged del administrador de animaciones.|
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|Lo llama el marco de trabajo una vez finalizada la actualización de una animación.|
|[CAnimationController::OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|Lo llama el marco de trabajo antes de que se inicie una actualización de animación.|
|[CAnimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|Lo llama el marco de trabajo cuando la velocidad de fotogramas de representación de una animación cae por debajo de una velocidad de fotogramas deseada mínima.|
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|Lo llama el marco de trabajo cuando ha cambiado el valor de la variable de animación.|
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|Lo llama el marco de trabajo antes de que se programe la animación.|
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|Lo llama el marco para resolver los conflictos de programación.|
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|Lo llama el marco para resolver los conflictos de programación.|
|[CAnimationController::OnHasPriorityConclude](#onhaspriorityconclude)|Lo llama el marco para resolver los conflictos de programación.|
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|Lo llama el marco para resolver los conflictos de programación.|
|[CAnimationController::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Lo llama el marco de trabajo cuando ha cambiado el estado del guión gráfico.|
|[CAnimationController::OnStoryboardUpdated](#onstoryboardupdated)|Lo llama el marco de trabajo cuando se ha actualizado el guión gráfico.|
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|Quita todos los grupos de animaciones del controlador de animación.|
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|Quita un grupo de animaciones con el identificador especificado de la controladora de animación.|
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|Quitar un objeto Animation del controlador de animación.|
|[CAnimationController::RemoveTransitions](#removetransitions)|Quita las transiciones de los objetos de animación que pertenecen al grupo especificado.|
|[CAnimationController::ScheduleGroup](#schedulegroup)|Programa una animación.|
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|Establece una relación entre el controlador de animación y una ventana.|
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|Indica al administrador de animaciones que actualice los valores de todas las variables de animación.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Sobrecargado. Aplicación auxiliar que limpia el grupo.|
|[CAnimationController::OnAfterSchedule](#onafterschedule)|Lo llama el marco de trabajo cuando se acaba de programar una animación para el grupo especificado.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|Fotograma clave que representa el inicio del guión gráfico.|
|[CAnimationController::m_bIsValid](#m_bisvalid)|Especifica si un controlador de animación es válido o no. Este miembro se establece en FALSE si el sistema operativo actual no admite la API de animación de Windows.|
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|Lista de grupos de animaciones que pertenecen a este controlador de animación.|
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|Almacena un puntero al objeto COM del administrador de animaciones.|
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|Almacena un puntero al objeto COM del temporizador de animación.|
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|Un puntero a un objeto CWnd relacionado, que se puede volver a dibujar automáticamente cuando el estado del administrador de animaciones ha cambiado o se ha producido un evento posterior a la actualización. Puede ser NULL.|
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|Almacena un puntero al objeto COM del generador de transición.|
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|Almacena un puntero al objeto COM de la biblioteca de transición.|

## <a name="remarks"></a>Comentarios

La clase CAnimationController es la clase clave que administra las animaciones. Puede crear una o varias instancias del controlador de animación en una aplicación y, opcionalmente, conectar una instancia de un controlador de animación a un objeto CWnd mediante CAnimationController:: SetRelatedWnd. Esta conexión es necesaria para enviar mensajes WM_PAINT a la ventana relacionada automáticamente cuando el estado del administrador de animaciones ha cambiado o se ha actualizado el temporizador de animación. Si no habilita esta relación, debe volver a dibujar una ventana que muestre una animación manualmente. Para este propósito, puede derivar una clase de CAnimationController e invalidar OnAnimationManagerStatusChanged o OnAnimationTimerPostUpdate e invalidar una o más ventanas cuando sea necesario.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxanimationcontroller.h

##  <a name="_dtorcanimationcontroller"></a>CAnimationController:: ~ CAnimationController

Destructor. Se llama cuando se destruye el objeto de controlador de animación.

```
virtual ~CAnimationController(void);
```

##  <a name="addanimationobject"></a>  CAnimationController::AddAnimationObject

Agrega un objeto Animation a un grupo que pertenece al controlador de animaciones.

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>Parámetros

*pObject*<br/>
Un puntero a un objeto Animation.

### <a name="return-value"></a>Valor devuelto

Un puntero a un grupo de animaciones nuevo o existente en el que se ha agregado pObject si la función se realiza correctamente; ES NULL si ya se ha agregado pObject a un grupo que pertenece a otro controlador de animación.

### <a name="remarks"></a>Comentarios

Llame a este método para agregar un objeto Animation al controlador de animación. Un objeto se agregará a un grupo según el GroupID del objeto (vea CAnimationBaseObject:: SetId). El controlador de animación creará un nuevo grupo si es el primer objeto que se va a agregar con el GroupID especificado. Un objeto Animation solo puede agregarse a un controlador de animación. Si necesita agregar un objeto a otro controlador, llame a RemoveAnimationObject en primer lugar. Si llama a SetId con New GroupID para un objeto que ya se ha agregado a un grupo, el objeto se quitará del grupo anterior y se agregará a otro grupo con el identificador especificado.

##  <a name="addkeyframetogroup"></a>  CAnimationController::AddKeyframeToGroup

Agrega un fotograma clave al grupo.

```
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe);
```

### <a name="parameters"></a>Parámetros

*nGroupID*<br/>
Especifica el identificador del grupo.

*pKeyframe*<br/>
Un puntero a un fotograma clave.

### <a name="return-value"></a>Valor devuelto

TRUE si la función se ejecuta correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Normalmente no es necesario llamar a este método, use CAnimationController:: CreateKeyframe en su lugar, que crea y agrega automáticamente el fotograma clave creado a un grupo.

##  <a name="animategroup"></a>  CAnimationController::AnimateGroup

Prepara un grupo para ejecutar la animación y, de forma opcional, programarlo.

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

TRUE si la animación se programó y ejecutó correctamente.

### <a name="remarks"></a>Comentarios

Este método realiza el trabajo real de creación de guiones gráficos, agrega variables de animación, aplica transiciones y establece fotogramas clave. Es posible retrasar la programación si establece bScheduleNow en FALSE. En este caso, el grupo especificado contendrá un guion gráfico que se ha configurado para la animación. En ese momento, puede configurar eventos para las variables Storyboard y Animation. Cuando realmente necesite ejecutar la llamada de animación CAnimationController:: ScheduleGroup.

##  <a name="canimationcontroller"></a>  CAnimationController::CAnimationController

Crea un controlador de animación.

```
CAnimationController(void);
```

##  <a name="cleanupgroup"></a>  CAnimationController::CleanUpGroup

Lo llama el marco de trabajo para limpiar el grupo cuando se ha programado la animación.

```
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parámetros

*nGroupID*<br/>
Especifica GroupID.

*pGroup*<br/>
Un puntero al grupo de animaciones que se va a limpiar.

### <a name="remarks"></a>Comentarios

Este método quita todas las transiciones y fotogramas clave del grupo especificado, ya que no son relevantes después de que se haya programado una animación.

##  <a name="createkeyframe"></a>  CAnimationController::CreateKeyframe

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

*pTransition*<br/>
Puntero a la transición. El fotograma clave se insertará en el guion gráfico después de esta transición.

*pKeyframe*<br/>
Puntero al fotograma clave base de este fotograma clave.

*offset*<br/>
Desplazamiento en segundos desde el fotograma clave base especificado por pKeyframe.

### <a name="return-value"></a>Valor devuelto

Puntero al fotograma clave recién creado si la función se ejecuta correctamente.

### <a name="remarks"></a>Comentarios

Puede almacenar el puntero devuelto y basar otros fotogramas clave en el fotograma clave recién creado (véase la segunda sobrecarga). Es posible iniciar las transiciones en los fotogramas clave (véase CBaseTransition::SetKeyframes). No es necesario eliminar fotogramas clave creados de esta manera, ya que los grupos de animación los eliminan automáticamente. Tenga cuidado al crear fotogramas clave basados en otros fotogramas clave y transiciones, y evite las referencias circulares.

##  <a name="enableanimationmanagerevent"></a>  CAnimationController::EnableAnimationManagerEvent

Establece o libera un controlador al que se llama cuando cambia el estado del administrador de animaciones.

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
Especifica si se debe establecer o liberar un controlador.

### <a name="return-value"></a>Valor devuelto

TRUE si el controlador se ha establecido o liberado correctamente.

### <a name="remarks"></a>Comentarios

Cuando se establece un controlador (habilitado), la animación de Windows llama a OnAnimationManagerStatusChanged cuando cambia el estado del administrador de animaciones.

##  <a name="enableanimationtimereventhandler"></a>  CAnimationController::EnableAnimationTimerEventHandler

Establece o libera un controlador para los eventos de control de tiempo y el controlador para las actualizaciones de control de tiempo.

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
Especifica si se van a establecer o liberar los controladores.

*idleBehavior*<br/>
Especifica el comportamiento de inactividad para el controlador de actualización del temporizador.

### <a name="return-value"></a>Valor devuelto

TRUE si los controladores se han establecido o liberado correctamente; FALSE si se llama a este método por segunda vez sin liberar primero los controladores o si se produce cualquier otro error.

### <a name="remarks"></a>Comentarios

Cuando los controladores se establecen (habilitadas), la API de animación de Windows llama a los métodos OnAnimationTimerPreUpdate, OnAnimationTimerPostUpdate y OnRenderingTooSlow. Debe habilitar los temporizadores de animación para permitir que la API de animación de Windows actualice guiones gráficos. En caso contrario, deberá llamar a CAnimationController:: UpdateAnimationManager para dirigir el administrador de animaciones para que actualice los valores de todas las variables de animación.

##  <a name="enableprioritycomparisonhandler"></a>  CAnimationController::EnablePriorityComparisonHandler

Establece o libera el controlador de comparación de prioridades que se va a llamar para determinar si un guion gráfico programado se puede cancelar, concluir, recortar o comprimir.

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>Parámetros

*dwHandlerType*<br/>
Una combinación de marcas UI_ANIMATION_PHT_ (vea comentarios), que especifica qué controladores se deben establecer o liberar.

### <a name="return-value"></a>Valor devuelto

TRUE si el controlador se ha establecido o liberado correctamente.

### <a name="remarks"></a>Comentarios

Cuando se establece un controlador (habilitado), la animación de Windows llama a los siguientes métodos virtuales en función de dwHandlerType: OnHasPriorityCancel, OnHasPriorityConclude, OnHasPriorityTrim, OnHasPriorityCompress. dwHandler puede ser una combinación de las marcas siguientes: UI_ANIMATION_PHT_NONE-Release todos los controladores UI_ANIMATION_PHT_CANCEL-Set CANCEL Comparison handler UI_ANIMATION_PHT_CONCLUDE-Set Terminate comparis handler UI_ANIMATION_PHT_COMPRESS-Set compress Comparison handler UI_ANIMATION_PHT_TRIM-set El controlador de comparación de recortes UI_ANIMATION_PHT_CANCEL_REMOVE-Remove cancelar el controlador de comparación UI_ANIMATION_PHT_CONCLUDE_REMOVE-Remove concluir el controlador de comparación UI_ANIMATION_PHT_COMPRESS_REMOVE-Remove compress comparador UI_ANIMATION_PHT _TRIM_REMOVE: quitar el controlador de comparación de recorte

##  <a name="enablestoryboardeventhandler"></a>  CAnimationController::EnableStoryboardEventHandler

Establece o libera un controlador para los eventos de actualización y estado de guion gráfico.

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*nGroupID*<br/>
Especifica el identificador del grupo.

*bEnable*<br/>
Especifica si se debe establecer o liberar un controlador.

### <a name="return-value"></a>Valor devuelto

TRUE si el controlador se ha establecido o liberado correctamente; FALSE si el grupo de animación especificado ya se encuentra o si la animación del grupo especificado no se ha iniciado y su guión gráfico interno es NULL.

### <a name="remarks"></a>Comentarios

Cuando se establece un controlador (habilitado), la API de animación de Windows llama a los métodos virtuales OnStoryboardStatusChanges y OnStoryboardUpdated. Un controlador debe establecerse después de que se haya llamado a CAnimationController:: Animate para el grupo de animación especificado, ya que crea un objeto IUIAnimationStoryboard encapsulado.

##  <a name="findanimationgroup"></a>  CAnimationController::FindAnimationGroup

Busca un grupo de animaciones por su identificador de grupo.

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parámetros

*nGroupID*<br/>
Especifica un GroupID.

*pStoryboard*<br/>
Un puntero a un guion gráfico.

### <a name="return-value"></a>Valor devuelto

Un puntero a un grupo de animación o NULL si no se encuentra el grupo con el identificador especificado.

### <a name="remarks"></a>Comentarios

Utilice este método para buscar un grupo de animaciones en tiempo de ejecución. Se crea un grupo y se agrega a la lista interna de grupos de animación cuando se agrega al controlador de animación un primer objeto de animación con un determinado GroupID.

##  <a name="findanimationobject"></a>  CAnimationController::FindAnimationObject

Busca un objeto de animación que contiene una variable de animación especificada.

```
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,
    CAnimationBaseObject** ppObject,
    CAnimationGroup** ppGroup);
```

### <a name="parameters"></a>Parámetros

*pVariable*<br/>
Puntero a la variable de animación.

*ppObject*<br/>
Genere. Contiene un puntero a un objeto Animation o NULL.

*ppGroup*<br/>
Genere. Contiene un puntero a un grupo de animación que contiene el objeto de animación o NULL.

### <a name="return-value"></a>Valor devuelto

TRUE si se encontró el objeto; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Se llama desde los controladores de eventos cuando es necesario buscar un objeto de animación de la variable de animación entrante.

##  <a name="g_keyframestoryboardstart"></a>  CAnimationController::gkeyframeStoryboardStart

Fotograma clave que representa el inicio del guión gráfico.

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

##  <a name="getkeyframestoryboardstart"></a>  CAnimationController::GetKeyframeStoryboardStart

Devuelve un fotograma clave que identifica el inicio de un guion gráfico.

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>Valor devuelto

Puntero al fotograma clave base, que identifica el inicio del guion gráfico.

### <a name="remarks"></a>Comentarios

Obtenga este fotograma clave para basar cualquier otro fotograma clave o transición en el momento en que se inicia un guion gráfico.

##  <a name="getuianimationmanager"></a>  CAnimationController::GetUIAnimationManager

Proporciona acceso al objeto IUIAnimationManager encapsulado.

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la interfaz IUIAnimationManager o NULL si no se pudo crear el administrador de animaciones.

### <a name="remarks"></a>Comentarios

Si el sistema operativo actual no admite la API de animación de Windows, este método devuelve NULL y después de que todas las llamadas subsiguientes en CAnimationController:: IsValid devuelvan FALSE. Puede que necesite tener acceso a IUIAnimationManager para llamar a sus métodos de interfaz, que no están encapsulados por el controlador de animación.

##  <a name="getuianimationtimer"></a>  CAnimationController::GetUIAnimationTimer

Proporciona acceso al objeto IUIAnimationTimer encapsulado.

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la interfaz IUIAnimationTimer o NULL si no se pudo crear el temporizador de animación.

### <a name="remarks"></a>Comentarios

Si el sistema operativo actual no admite la API de animación de Windows, este método devuelve NULL y después de que todas las llamadas subsiguientes en CAnimationController:: IsValid devuelvan FALSE.

##  <a name="getuitransitionfactory"></a>  CAnimationController::GetUITransitionFactory

Un puntero a la interfaz IUIAnimationTransitionFactory o NULL si se produce un error en la creación de la biblioteca de transición.

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a IUIAnimationTransitionFactory o NULL, si se produce un error en la creación del generador de transiciones.

### <a name="remarks"></a>Comentarios

Si el sistema operativo actual no admite la API de animación de Windows, este método devuelve NULL y después de que todas las llamadas subsiguientes en CAnimationController:: IsValid devuelvan FALSE.

##  <a name="getuitransitionlibrary"></a>  CAnimationController::GetUITransitionLibrary

Proporciona acceso al objeto IUIAnimationTransitionLibrary encapsulado.

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la interfaz IUIAnimationTransitionLibrary o NULL si se produce un error en la creación de la biblioteca de transición.

### <a name="remarks"></a>Comentarios

Si el sistema operativo actual no admite la API de animación de Windows, este método devuelve NULL y después de que todas las llamadas subsiguientes en CAnimationController:: IsValid devuelvan FALSE.

##  <a name="isanimationinprogress"></a>  CAnimationController::IsAnimationInProgress

Indica si al menos un grupo está reproduciendo animación.

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>Valor devuelto

TRUE si hay una animación en curso para este controlador de animación; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Comprueba el estado del administrador de animaciones y devuelve TRUE si el estado es UI_ANIMATION_MANAGER_BUSY.

##  <a name="isvalid"></a>  CAnimationController::IsValid

Indica si el controlador de animación es válido.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el controlador de animación es válido; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método devuelve FALSE solo si la API de animación de Windows no se admite en el sistema operativo actual y no se pudo crear el administrador de animaciones porque no está registrada. Debe llamar a GetUIAnimationManager al menos una vez después de la inicialización de las bibliotecas COM para producir la configuración de esta marca.

##  <a name="m_bisvalid"></a>  CAnimationController::m_bIsValid

Especifica si un controlador de animación es válido o no. Este miembro se establece en FALSE si el sistema operativo actual no admite la API de animación de Windows.

```
BOOL m_bIsValid;
```

##  <a name="m_lstanimationgroups"></a>  CAnimationController::m_lstAnimationGroups

Lista de grupos de animaciones que pertenecen a este controlador de animación.

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

##  <a name="m_panimationmanager"></a>  CAnimationController::m_pAnimationManager

Almacena un puntero al objeto COM del administrador de animaciones.

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

##  <a name="m_panimationtimer"></a>  CAnimationController::m_pAnimationTimer

Almacena un puntero al objeto COM del temporizador de animación.

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

##  <a name="m_prelatedwnd"></a>  CAnimationController::m_pRelatedWnd

Un puntero a un objeto CWnd relacionado, que se puede volver a dibujar automáticamente cuando el estado del administrador de animaciones ha cambiado o se ha producido un evento posterior a la actualización. Puede ser NULL.

```
CWnd* m_pRelatedWnd;
```

##  <a name="m_ptransitionfactory"></a>  CAnimationController::m_pTransitionFactory

Almacena un puntero al objeto COM del generador de transición.

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

##  <a name="m_ptransitionlibrary"></a>  CAnimationController::m_pTransitionLibrary

Almacena un puntero al objeto COM de la biblioteca de transición.

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

##  <a name="onafterschedule"></a>  CAnimationController::OnAfterSchedule

Lo llama el marco de trabajo cuando se acaba de programar una animación para el grupo especificado.

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parámetros

*pGroup*<br/>
Un puntero a un grupo de animaciones, que se ha programado.

### <a name="remarks"></a>Comentarios

La implementación predeterminada quita los fotogramas clave del grupo especificado y realiza las transiciones de las variables de animación que pertenecen al grupo especificado. Se puede invalidar en una clase derivada para realizar acciones adicionales en la programación de la animación.

##  <a name="onanimationintegervaluechanged"></a>  CAnimationController::OnAnimationIntegerValueChanged

Lo llama el marco de trabajo cuando ha cambiado el valor entero de la variable de animación.

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
Un puntero a un grupo de animaciones que contiene un objeto de animación cuyo valor ha cambiado.

*pObject*<br/>
Un puntero a un objeto Animation que contiene una variable de animación cuyo valor ha cambiado.

*variable*<br/>
Puntero a una variable de animación.

*newValue*<br/>
Especifica un nuevo valor.

*prevValue*<br/>
Especifica el valor anterior.

### <a name="remarks"></a>Comentarios

Se llama a este método si se habilitan eventos de variables de animación con EnableIntegerValueChangedEvent denominado para una variable de animación o un objeto de animación concretos. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación.

##  <a name="onanimationmanagerstatuschanged"></a>  CAnimationController::OnAnimationManagerStatusChanged

Lo llama el marco de trabajo en respuesta al evento StatusChanged del administrador de animaciones.

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Parámetros

*newStatus*<br/>
Nuevo estado del administrador de animaciones.

*previousStatus*<br/>
Estado anterior del administrador de animaciones.

### <a name="remarks"></a>Comentarios

Se llama a este método si se habilitan los eventos del administrador de animaciones con EnableAnimationManagerEvent. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación. La implementación predeterminada actualiza una ventana relacionada si se ha establecido con SetRelatedWnd.

##  <a name="onanimationtimerpostupdate"></a>  CAnimationController::OnAnimationTimerPostUpdate

Lo llama el marco de trabajo una vez finalizada la actualización de una animación.

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>Comentarios

Se llama a este método si se habilitan los controladores de eventos de temporizador mediante EnableAnimationTimerEventHandler. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación.

##  <a name="onanimationtimerpreupdate"></a>  CAnimationController::OnAnimationTimerPreUpdate

Lo llama el marco de trabajo antes de que se inicie una actualización de animación.

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>Comentarios

Se llama a este método si se habilitan los controladores de eventos de temporizador mediante EnableAnimationTimerEventHandler. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación.

##  <a name="onanimationtimerrenderingtooslow"></a>  CAnimationController::OnAnimationTimerRenderingTooSlow

Lo llama el marco de trabajo cuando la velocidad de fotogramas de representación de una animación cae por debajo de una velocidad de fotogramas deseada mínima.

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>Parámetros

*fps*<br/>
Velocidad de fotogramas actual en fotogramas por segundo.

### <a name="remarks"></a>Comentarios

Se llama a este método si se habilitan los controladores de eventos de temporizador mediante EnableAnimationTimerEventHandler. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación. La velocidad de fotogramas deseada mínima se especifica mediante una llamada a IUIAnimationTimer:: SetFrameRateThreshold.

##  <a name="onanimationvaluechanged"></a>  CAnimationController::OnAnimationValueChanged

Lo llama el marco de trabajo cuando ha cambiado el valor de la variable de animación.

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
Un puntero a un grupo de animaciones que contiene un objeto de animación cuyo valor ha cambiado.

*pObject*<br/>
Un puntero a un objeto Animation que contiene una variable de animación cuyo valor ha cambiado.

*variable*<br/>
Puntero a una variable de animación.

*newValue*<br/>
Especifica un nuevo valor.

*prevValue*<br/>
Especifica el valor anterior.

### <a name="remarks"></a>Comentarios

Se llama a este método si se habilitan eventos de variables de animación con EnableValueChangedEvent denominado para una variable de animación o un objeto de animación concretos. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación.

##  <a name="onbeforeanimationstart"></a>  CAnimationController::OnBeforeAnimationStart

Lo llama el marco de trabajo antes de que se programe la animación.

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parámetros

*pGroup*<br/>
Un puntero a un grupo de animaciones cuya animación está a punto de iniciarse.

### <a name="remarks"></a>Comentarios

Esta llamada se enruta a CWnd relacionado y se puede invalidar en una clase derivada para realizar acciones adicionales antes de que se inicie la animación para el grupo especificado.

##  <a name="onhasprioritycancel"></a>  CAnimationController::OnHasPriorityCancel

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

### <a name="remarks"></a>Comentarios

Se llama a este método si se habilitan eventos de comparación de prioridad mediante CAnimationController::EnablePriorityComparisonHandler y se especifica UI_ANIMATION_PHT_CANCEL. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación. Lea la documentación de la API de animación de Windows para obtener más información sobre la [Administración de conflictos](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

##  <a name="onhasprioritycompress"></a>  CAnimationController::OnHasPriorityCompress

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

### <a name="remarks"></a>Comentarios

Se llama a este método si se habilitan eventos de comparación de prioridad mediante CAnimationController::EnablePriorityComparisonHandler y se especifica UI_ANIMATION_PHT_COMPRESS. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación. Lea la documentación de la API de animación de Windows para obtener más información sobre la [Administración de conflictos](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

##  <a name="onhaspriorityconclude"></a>  CAnimationController::OnHasPriorityConclude

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

### <a name="remarks"></a>Comentarios

Se llama a este método si se habilitan eventos de comparación de prioridad mediante CAnimationController::EnablePriorityComparisonHandler y se especifica UI_ANIMATION_PHT_CONCLUDE. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación. Lea la documentación de la API de animación de Windows para obtener más información sobre la [Administración de conflictos](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

##  <a name="onhasprioritytrim"></a>  CAnimationController::OnHasPriorityTrim

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

### <a name="remarks"></a>Comentarios

Se llama a este método si se habilitan eventos de comparación de prioridad mediante CAnimationController::EnablePriorityComparisonHandler y se especifica UI_ANIMATION_PHT_TRIM. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación. Lea la documentación de la API de animación de Windows para obtener más información sobre la [Administración de conflictos](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

##  <a name="onstoryboardstatuschanged"></a>  CAnimationController::OnStoryboardStatusChanged

Lo llama el marco de trabajo cuando ha cambiado el estado del guión gráfico.

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>Parámetros

*pGroup*<br/>
Un puntero a un grupo de animación que posee el guión gráfico cuyo estado ha cambiado.

*newStatus*<br/>
Especifica el nuevo estado.

*previousStatus*<br/>
Especifica el estado anterior.

### <a name="remarks"></a>Comentarios

Se llama a este método si se habilitan eventos de guion gráfico mediante CAnimationController:: EnableStoryboardEventHandler. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación.

##  <a name="onstoryboardupdated"></a>  CAnimationController::OnStoryboardUpdated

Lo llama el marco de trabajo cuando se ha actualizado el guión gráfico.

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parámetros

*pGroup*<br/>
Un puntero a un grupo que posee el guión gráfico.

### <a name="remarks"></a>Comentarios

Se llama a este método si se habilitan eventos de guion gráfico mediante CAnimationController:: EnableStoryboardEventHandler. Se puede invalidar en una clase derivada para realizar acciones específicas de la aplicación.

##  <a name="removeallanimationgroups"></a>  CAnimationController::RemoveAllAnimationGroups

Quita todos los grupos de animaciones del controlador de animación.

```
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>Comentarios

Se eliminarán todos los grupos, su puntero, si se almacenan en el nivel de aplicación, se debe invalidar. Si CAnimationGroup:: m_bAutodestroyAnimationObjects para un grupo que se va a eliminar es TRUE, se eliminarán todos los objetos de animación que pertenezcan a ese grupo; de lo contrario, las referencias al controlador de animación primario se establecerán en NULL y se pueden agregar a otro controlador.

##  <a name="removeanimationgroup"></a>  CAnimationController::RemoveAnimationGroup

Quita un grupo de animaciones con el identificador especificado de la controladora de animación.

```
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>Parámetros

*nGroupID*<br/>
Especifica el identificador del grupo de animaciones.

### <a name="remarks"></a>Comentarios

Este método quita un grupo de animaciones de la lista interna de grupos y lo elimina; por lo tanto, si ha almacenado un puntero a ese grupo de animaciones, se debe invalidar. Si CAnimationGroup:: m_bAutodestroyAnimationObjects es TRUE, se eliminarán todos los objetos de animación que pertenezcan a ese grupo; de lo contrario, las referencias al controlador de animación primario se establecerán en NULL y se pueden agregar a otro controlador.

##  <a name="removeanimationobject"></a>  CAnimationController::RemoveAnimationObject

Quitar un objeto Animation del controlador de animación.

```
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>Parámetros

*pObject*<br/>
Un puntero a un objeto Animation.

*bNoDelete*<br/>
Si este parámetro es TRUE, el objeto no se eliminará al quitarlo.

### <a name="remarks"></a>Comentarios

Quita un objeto Animation del controlador de animación y del grupo de animaciones. Llame a esta función si un objeto determinado ya no se debe animar o si necesita trasladar el objeto a otro controlador de animación. En el último caso, bNoDelete debe ser TRUE.

##  <a name="removetransitions"></a>  CAnimationController::RemoveTransitions

Quita las transiciones de los objetos de animación que pertenecen al grupo especificado.

```
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>Parámetros

*nGroupID*<br/>
Especifica el identificador del grupo.

### <a name="remarks"></a>Comentarios

El grupo recorre en bucle los objetos de animación y llama a ClearTransitions (FALSE) para cada objeto de animación. El marco de trabajo llama a este método después de que se haya programado la animación.

##  <a name="schedulegroup"></a>  CAnimationController::ScheduleGroup

Programa una animación.

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>Parámetros

*nGroupID*<br/>
Especifica el identificador del grupo de animaciones que se va a programar.

*time*<br/>
Especifica el tiempo de programación.

### <a name="return-value"></a>Valor devuelto

TRUE si la animación se programó correctamente. FALSE si no se ha creado el guión gráfico o se produce otro error.

### <a name="remarks"></a>Comentarios

Debe llamar a AnimateGroup con el parámetro bScheduleNow establecido en FALSE anterior ScheduleGroup. Puede especificar el tiempo de animación deseado Obtenido de IUIAnimationTimer:: GetTime. Si el parámetro de hora es 0,0, la animación está programada para la hora actual.

##  <a name="setrelatedwnd"></a>  CAnimationController::SetRelatedWnd

Establece una relación entre el controlador de animación y una ventana.

```
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero al objeto de ventana que se va a establecer.

### <a name="remarks"></a>Comentarios

Si se establece un objeto CWnd relacionado, el controlador de animación puede actualizarlo automáticamente (enviar mensaje WM_PAINT) cuando el estado del administrador de animaciones ha cambiado o se ha producido un evento de temporizador posterior a la actualización.

##  <a name="updateanimationmanager"></a>  CAnimationController::UpdateAnimationManager

Indica al administrador de animaciones que actualice los valores de todas las variables de animación.

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>Comentarios

Al llamar a este método, se avanza el administrador de animaciones hasta la hora actual, se cambian los Estados de los guiones gráficos según sea necesario y se actualizan las variables de animación a los valores interpolados adecuados. Internamente, este método llama a IUIAnimationTimer:: GetTime (timeNow) y IUIAnimationManager:: Update (timeNow). Invalide este método en una clase derivada para personalizar este comportamiento.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
