---
title: Scheduler (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Scheduler
- CONCRT/concurrency::Scheduler
- CONCRT/concurrency::Scheduler::Scheduler
- CONCRT/concurrency::Scheduler::Attach
- CONCRT/concurrency::Scheduler::Create
- CONCRT/concurrency::Scheduler::CreateScheduleGroup
- CONCRT/concurrency::Scheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::Scheduler::GetPolicy
- CONCRT/concurrency::Scheduler::Id
- CONCRT/concurrency::Scheduler::IsAvailableLocation
- CONCRT/concurrency::Scheduler::Reference
- CONCRT/concurrency::Scheduler::RegisterShutdownEvent
- CONCRT/concurrency::Scheduler::Release
- CONCRT/concurrency::Scheduler::ResetDefaultSchedulerPolicy
- CONCRT/concurrency::Scheduler::ScheduleTask
- CONCRT/concurrency::Scheduler::SetDefaultSchedulerPolicy
dev_langs:
- C++
helpviewer_keywords:
- Scheduler class
ms.assetid: 34cf7961-048d-4852-8a5c-a32f823e3506
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: cc39a524e9a65aeab0c84fb43f5b38ddd892923e
ms.lasthandoff: 03/17/2017

---
# <a name="scheduler-class"></a>Scheduler (Clase)
Representa una abstracción para un programador del runtime de simultaneidad.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class Scheduler;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Programador](#ctor)|Un objeto de la `Scheduler` clase solo se puede crear utilizando métodos de generador o implícitamente.|  
|[~ Scheduler (destructor)](#dtor)|Un objeto de la `Scheduler` clase se destruye implícitamente cuando todas las referencias externas al mismo dejan de existir.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Asociar](#attach)|Adjunta al programador al contexto de la llamada. Cuando vuelve este método, el programador administra el contexto de llamada y el programador se convierte en el programador actual.|  
|[Crear](#create)|Crea un nuevo programador cuyo comportamiento se describe en el `_Policy` parámetro, coloca una referencia inicial en el programador y devuelve un puntero a ella.|  
|[CreateScheduleGroup](#createschedulegroup)|Sobrecargado. Crea un nuevo grupo de programación dentro del programador. La versión que toma el parámetro `_Placement` hace que las tareas dentro del grupo de programación recién creado para estar orientadas a ejecutar en la ubicación especificada por ese parámetro.|  
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|Devuelve el número actual de procesadores virtuales para el programador.|  
|[GetPolicy](#getpolicy)|Devuelve una copia de la directiva que creó el programador.|  
|[Id.](#id)|Devuelve un identificador único para el programador.|  
|[IsAvailableLocation](#isavailablelocation)|Determina si una determinada ubicación está disponible en el programador.|  
|[Referencia](#reference)|Incrementa el recuento de referencias del programador.|  
|[RegisterShutdownEvent](#registershutdownevent)|Hace que el controlador de eventos de Windows pasado en el `_Event` parámetro se señalice cuando el planificador se cierra y se destruye. En el momento en que se señala el evento, todo el trabajo que está programado para el programador está completando. Mediante este método, se pueden registrar varios eventos de apagado.|  
|[Release](#release)|Reduce el recuento de la referencia del programador.|  
|[ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy)|Restablece la directiva del programador predeterminado con el valor predeterminado de tiempo de ejecución. La próxima vez que se crea un programador predeterminado, utilizará la configuración de directiva en tiempo de ejecución predeterminado.|  
|[ScheduleTask](#scheduletask)|Sobrecargado. Programa una tarea ligera dentro del programador. La tarea ligera se situará en un grupo de programación determinada por el tiempo de ejecución. La versión que toma el parámetro `_Placement` hace que la tarea se inclina hacia la ejecución en la ubicación especificada.|  
|[SetDefaultSchedulerPolicy](#setdefaultschedulerpolicy)|Permite una directiva definida por el usuario que se utilizará para crear al programador predeterminado. Puede llamar a este método sólo cuando no existe ningún programador predeterminado dentro del proceso. Una vez establecida una directiva predeterminada, permanece en vigor hasta la siguiente llamada válida a la `SetDefaultSchedulerPolicy` o [ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy) (método).|  
  
## <a name="remarks"></a>Comentarios  
 El programador del Runtime de simultaneidad usa contextos de ejecución, que se asignan a los contextos de ejecución del sistema operativo, por ejemplo, un subproceso, para ejecutar el trabajo de cola para su aplicación. En cualquier momento, el nivel de simultaneidad de un programador es igual al número de procesador virtual concedido por el Administrador de recursos. Un procesador virtual es una abstracción para un recurso de procesamiento y se asigna a un subproceso del hardware en el sistema subyacente. Solo se puede ejecutar un único contexto del programador en un procesador virtual a una hora determinada.  
  
 El Runtime de simultaneidad creará un programador predeterminado por proceso para ejecutar trabajo paralelo. Además puede crear instancias de su propio programador y manipularlo usando esta clase.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `Scheduler`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="attach"></a>Adjuntar 

 Adjunta al programador al contexto de la llamada. Cuando vuelve este método, el programador administra el contexto de llamada y el programador se convierte en el programador actual.  
  
```
virtual void Attach() = 0;
```  
  
### <a name="remarks"></a>Comentarios  
 Adjuntar a un programador implícitamente coloca una referencia en el programador.  
  
 En algún momento en el futuro, debe llamar a la [CurrentScheduler:: Detach](currentscheduler-class.md#detach) método para permitir que el programador se cierre.  
  
 Si se llama a este método desde un contexto que ya está adjuntado a un programador diferente, el programador existente se recuerda como el programador anterior y el programador creado recientemente se convierte en el programador actual. Cuando se llama a la `CurrentScheduler::Detach` método en un momento posterior, el programador anterior se restaura como el programador actual.  
  
 Este método producirá una [improper_scheduler_attach](improper-scheduler-attach-class.md) excepción si este programador es el programador actual del contexto de la llamada.  
  
##  <a name="create"></a>Crear 

 Crea un nuevo programador cuyo comportamiento se describe en el `_Policy` parámetro, coloca una referencia inicial en el programador y devuelve un puntero a ella.  
  
```
static Scheduler* __cdecl Create(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Policy`  
 La directiva del programador que describe el comportamiento del programador recién creado.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un programador recién creado. Esto `Scheduler` objeto tiene un recuento de referencia inicial colocado en él.  
  
### <a name="remarks"></a>Comentarios  
 Una vez creado un programador con el `Create` método, debe llamar a la `Release` método en algún momento en el futuro con el fin de quitar el recuento de referencias inicial y permitir que el programador se cierre.  
  
 Un programador creado con este método no está asociado al contexto de la llamada. Se puede adjuntar a un contexto mediante la [adjuntar](#attach) método.  
  
 Este método puede producir una variedad de excepciones, incluida la [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md) y [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md).  
  
##  <a name="createschedulegroup"></a>CreateScheduleGroup 

 Crea un nuevo grupo de programación dentro del programador. La versión que toma el parámetro `_Placement` hace que las tareas dentro del grupo de programación recién creado para estar orientadas a ejecutar en la ubicación especificada por ese parámetro.  
  
```
virtual ScheduleGroup* CreateScheduleGroup() = 0;

virtual ScheduleGroup* CreateScheduleGroup(location& _Placement) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Placement`  
 Una referencia a una ubicación donde las tareas dentro del grupo de programación se inclina hacia ejecutando en.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al grupo de programación recién creado. Esto `ScheduleGroup` objeto tiene un recuento de referencia inicial colocado en él.  
  
### <a name="remarks"></a>Comentarios  
 Se debe invocar el [versión](schedulegroup-class.md#release) método en un grupo de programación cuando haya terminado el trabajo de programación en él. El programador destruirá la programación de grupo cuando todo el trabajo en la cola se ha completado.  
  
 Tenga en cuenta que si creó a este programador explícitamente, debe liberar todas las referencias, grupos de programación antes de liberar sus referencias en el programador.  
  
##  <a name="getnumberofvirtualprocessors"></a>GetNumberOfVirtualProcessors 

 Devuelve el número actual de procesadores virtuales para el programador.  
  
```
virtual unsigned int GetNumberOfVirtualProcessors() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número actual de procesadores virtuales para el programador.  
  
##  <a name="getpolicy"></a>GetPolicy 

 Devuelve una copia de la directiva que creó el programador.  
  
```
virtual SchedulerPolicy GetPolicy() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una copia de la directiva que creó el programador.  
  
##  <a name="id"></a>Id. 

 Devuelve un identificador único para el programador.  
  
```
virtual unsigned int Id() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador único para el programador.  
  
##  <a name="isavailablelocation"></a>IsAvailableLocation 

 Determina si una determinada ubicación está disponible en el programador.  
  
```
virtual bool IsAvailableLocation(const location& _Placement) const = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Placement`  
 Una referencia a la ubicación para el programador de consultas sobre.  
  
### <a name="return-value"></a>Valor devuelto  
 Una indicación de si la ubicación especificada por el `_Placement` argumento está disponible en el programador.  
  
### <a name="remarks"></a>Comentarios  
 Tenga en cuenta que el valor devuelto es un muestreo instantáneo de si está disponible la ubicación dada. En presencia de varios programadores, administración de recursos dinámicos puede agrega o quita los recursos de programadores en cualquier momento. Esto sucedería, la ubicación dada puede cambiar la disponibilidad.  
  
##  <a name="reference"></a>Referencia 

 Incrementa el recuento de referencias del programador.  
  
```
virtual unsigned int Reference() = 0 ;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El recuento de referencias incrementado recientemente.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, esto se utiliza para administrar la duración del programador para la composición. Cuando el recuento de referencias de un programador cae a cero, el programador se cerrará y destruct propio después de todo trabajo en el programador ha completado.  
  
 El método producirá una [improper_scheduler_reference](improper-scheduler-reference-class.md) excepción si el recuento de referencias antes de llamar a la `Reference` método era cero y la llamada se realiza desde un contexto que no es propiedad del programador.  
  
##  <a name="registershutdownevent"></a>RegisterShutdownEvent 

 Hace que el controlador de eventos de Windows pasado en el `_Event` parámetro se señalice cuando el planificador se cierra y se destruye. En el momento en que se señala el evento, todo el trabajo que está programado para el programador está completando. Mediante este método, se pueden registrar varios eventos de apagado.  
  
```
virtual void RegisterShutdownEvent(HANDLE _Event) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Event`  
 Identificador de un objeto de evento de Windows que señalará el tiempo de ejecución cuando se cierra y se destruye el programador.  
  
##  <a name="release"></a>Versión 

 Reduce el recuento de la referencia del programador.  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El recuento de referencias disminuido recientemente.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, esto se utiliza para administrar la duración del programador para la composición. Cuando el recuento de referencias de un programador cae a cero, el programador se cerrará y destruct propio después de todo trabajo en el programador ha completado.  
  
##  <a name="resetdefaultschedulerpolicy"></a>ResetDefaultSchedulerPolicy 

 Restablece la directiva del programador predeterminado con el valor predeterminado de tiempo de ejecución. La próxima vez que se crea un programador predeterminado, utilizará la configuración de directiva en tiempo de ejecución predeterminado.  
  
```
static void __cdecl ResetDefaultSchedulerPolicy();
```  
  
### <a name="remarks"></a>Comentarios  
 Puede llamar a este método mientras exista un programador predeterminado dentro del proceso. No afectará a la directiva del programador predeterminado existente. Sin embargo, si el programador predeterminado se fuese a cerrar, y un nuevo valor predeterminado se creará en un momento posterior, el nuevo programador usaría la configuración de directiva en tiempo de ejecución predeterminado.  
  
##  <a name="ctor"></a>Programador 

 Un objeto de la `Scheduler` clase solo se puede crear utilizando métodos de generador o implícitamente.  
  
```
Scheduler();
```  
  
### <a name="remarks"></a>Comentarios  
 El programador predeterminado del proceso se crea implícitamente al utilizar muchas de las funciones en tiempo de ejecución que requieren un programador se adjunte al contexto de la llamada. Métodos dentro de la `CurrentScheduler` clase y las características de las capas PPL y los agentes normalmente realizan datos adjuntos implícitos.  
  
 También puede crear un programador explícitamente a través del `CurrentScheduler::Create` (método) o `Scheduler::Create` (método).  
  
##  <a name="dtor"></a>~ Programador 

 Un objeto de la `Scheduler` clase se destruye implícitamente cuando todas las referencias externas al mismo dejan de existir.  
  
```
virtual ~Scheduler();
```  
  
##  <a name="scheduletask"></a>ScheduleTask 

 Programa una tarea ligera dentro del programador. La tarea ligera se situará en un grupo de programación determinada por el tiempo de ejecución. La versión que toma el parámetro `_Placement` hace que la tarea se inclina hacia la ejecución en la ubicación especificada.  
  
```
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;

virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Proc`  
 Un puntero a función que se ejecuta para realizar el cuerpo de la tarea ligera.  
  
 `_Data`  
 Un puntero void a los datos que se pasará como un parámetro en el cuerpo de la tarea.  
  
 `_Placement`  
 Una referencia a una ubicación donde la tarea ligera se se decanta hacia el hardware ejecutando en.  
  
##  <a name="setdefaultschedulerpolicy"></a>SetDefaultSchedulerPolicy 

 Permite una directiva definida por el usuario que se utilizará para crear al programador predeterminado. Puede llamar a este método sólo cuando no existe ningún programador predeterminado dentro del proceso. Una vez establecida una directiva predeterminada, permanece en vigor hasta la siguiente llamada válida a la `SetDefaultSchedulerPolicy` o [ResetDefaultSchedulerPolicy](#resetdefaultschedulerpolicy) (método).  
  
```
static void __cdecl SetDefaultSchedulerPolicy(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Policy`  
 La directiva que se establecerá como la directiva del programador predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 Si el `SetDefaultSchedulerPolicy` se invoca cuando un programador predeterminado ya existe dentro del proceso, el runtime producirá una [default_scheduler_exists](default-scheduler-exists-class.md) excepción.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [Scheduler (clase)](scheduler-class.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [Programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)




