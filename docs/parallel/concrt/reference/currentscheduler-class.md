---
title: CurrentScheduler (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CurrentScheduler
- CONCRT/concurrency::CurrentScheduler
- CONCRT/concurrency::CurrentScheduler::Create
- CONCRT/concurrency::CurrentScheduler::CreateScheduleGroup
- CONCRT/concurrency::CurrentScheduler::Detach
- CONCRT/concurrency::CurrentScheduler::Get
- CONCRT/concurrency::CurrentScheduler::GetNumberOfVirtualProcessors
- CONCRT/concurrency::CurrentScheduler::GetPolicy
- CONCRT/concurrency::CurrentScheduler::Id
- CONCRT/concurrency::CurrentScheduler::IsAvailableLocation
- CONCRT/concurrency::CurrentScheduler::RegisterShutdownEvent
- CONCRT/concurrency::CurrentScheduler::ScheduleTask
dev_langs:
- C++
helpviewer_keywords:
- CurrentScheduler class
ms.assetid: 31c20e0e-4cdf-49b4-8220-d726130aad2b
caps.latest.revision: 20
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
ms.openlocfilehash: 9536dd28eeb375f3b9e018539cefb338812e340b
ms.lasthandoff: 03/17/2017

---
# <a name="currentscheduler-class"></a>CurrentScheduler (Clase)
Representa una abstracción para el programador actual asociado al contexto de la llamada.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CurrentScheduler;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Crear](#create)|Crea un nuevo programador cuyo comportamiento se describe en el `_Policy` parámetro y lo adjunta al contexto de la llamada. El programador creado recientemente se convertirá en el programador actual para el contexto de llamada.|  
|[CreateScheduleGroup](#createschedulegroup)|Sobrecargado. Crea un nuevo grupo de programación dentro del programador asociado al contexto llamado. La versión que toma el parámetro `_Placement` hace que las tareas dentro del grupo de programación recién creado para estar orientadas a ejecutar en la ubicación especificada por ese parámetro.|  
|[Desasociar](#detach)|Desasocia al programador del contexto de la llamada y restaura al programador asociado anteriormente como programador actual, si existe alguno. Cuando vuelve este método, el contexto de llamada es administrado por el programador que previamente se ha adjuntado al contexto utilizando la `CurrentScheduler::Create` o `Scheduler::Attach` (método).|  
|[Obtener](#get)|Devuelve un puntero al programador asociado con el contexto de llamada, que también se denomina el programador actual.|  
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|Devuelve el número actual de procesadores virtuales para el programador asociado al contexto de la llamada.|  
|[GetPolicy](#getpolicy)|Devuelve una copia de la directiva que creó el programador actual.|  
|[Id.](#id)|Devuelve un identificador único para el programador actual.|  
|[IsAvailableLocation](#isavailablelocation)|Determina si una determinada ubicación está disponible en el programador actual.|  
|[RegisterShutdownEvent](#registershutdownevent)|Hace que el controlador de eventos de Windows pasado en el `_ShutdownEvent` parámetro se señalice cuando el programador asociado al contexto actual se cierra y se destruye. En el momento en que se señala el evento, todo el trabajo que está programado para el programador está completando. Mediante este método, se pueden registrar varios eventos de apagado.|  
|[ScheduleTask](#scheduletask)|Sobrecargado. Programa una tarea ligera dentro del programador asociado al contexto llamado. La tarea ligera se situará en un grupo de programación determinada por el tiempo de ejecución. La versión que toma el parámetro `_Placement` hace que la tarea se inclina hacia la ejecución en la ubicación especificada.|  
  
## <a name="remarks"></a>Comentarios  
 Si no hay ningún programador (vea [programador](scheduler-class.md)) asociado al contexto de la llamada, muchos métodos dentro de la `CurrentScheduler` clase producirán datos adjuntos del programador de forma predeterminada el proceso. Esto también puede implicar que el programador del proceso de forma predeterminada se crea durante esta llamada.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CurrentScheduler`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="create"></a>Crear 

 Crea un nuevo programador cuyo comportamiento se describe en el `_Policy` parámetro y lo adjunta al contexto de la llamada. El programador creado recientemente se convertirá en el programador actual para el contexto de llamada.  
  
```
static void __cdecl Create(const SchedulerPolicy& _Policy);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Policy`  
 La directiva del programador que describe el comportamiento del programador recién creado.  
  
### <a name="remarks"></a>Comentarios  
 Los datos adjuntos del programador al contexto de la llamada colocan implícitamente un recuento de referencias en el programador.  
  
 Una vez creado un programador con el `Create` método, debe llamar a la [CurrentScheduler:: Detach](#detach) método en algún momento en el futuro para permitir que el programador se cierre.  
  
 Si se llama a este método desde un contexto que ya está adjuntado a un programador diferente, el programador existente se recuerda como el programador anterior y el programador creado recientemente se convierte en el programador actual. Cuando se llama a la `CurrentScheduler::Detach` método en un momento posterior, el programador anterior se restaura como el programador actual.  
  
 Este método puede producir una variedad de excepciones, incluida la [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md) y [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md).  
  
##  <a name="createschedulegroup"></a>CreateScheduleGroup 

 Crea un nuevo grupo de programación dentro del programador asociado al contexto llamado. La versión que toma el parámetro `_Placement` hace que las tareas dentro del grupo de programación recién creado para estar orientadas a ejecutar en la ubicación especificada por ese parámetro.  
  
```
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Placement`  
 Una referencia a una ubicación donde las tareas dentro del grupo de programación se se decanta hacia el hardware ejecutando en.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al grupo de programación recién creado. Esto `ScheduleGroup` objeto tiene un recuento de referencia inicial colocado en él.  
  
### <a name="remarks"></a>Comentarios  
 Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada.  
  
 Se debe invocar el [versión](schedulegroup-class.md#release) método en un grupo de programación cuando haya terminado el trabajo de programación en él. El programador destruirá la programación de grupo cuando todo el trabajo en la cola se ha completado.  
  
 Tenga en cuenta que si creó a este programador explícitamente, debe liberar todas las referencias, grupos de programación antes de liberar su referencia en el programador, separando el contexto actual.  
  
##  <a name="detach"></a>Desconectar 

 Desasocia al programador del contexto de la llamada y restaura al programador asociado anteriormente como programador actual, si existe alguno. Cuando vuelve este método, el contexto de llamada es administrado por el programador que previamente se ha adjuntado al contexto utilizando la `CurrentScheduler::Create` o `Scheduler::Attach` (método).  
  
```
static void __cdecl Detach();
```  
  
### <a name="remarks"></a>Comentarios  
 El `Detach` método quita implícitamente un recuento de referencias del programador.  
  
 Si no hay ningún programador adjuntado al contexto de la llamada, llamar a este método producirá una [scheduler_not_attached](scheduler-not-attached-class.md) excepción producida.  
  
 Llamar a este método desde un contexto que es interno y administrados por un programador o en un contexto que estaba conectado con un método distinto de la [Scheduler:: Attach](scheduler-class.md#attach) o [CurrentScheduler:: Create](#create) métodos, se producirá un [improper_scheduler_detach](improper-scheduler-detach-class.md) excepción producida.  
  
##  <a name="get"></a>Obtener 

 Devuelve un puntero al programador asociado con el contexto de llamada, que también se denomina el programador actual.  
  
```
static Scheduler* __cdecl Get();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al programador asociado con el contexto de llamada (el programador actual).  
  
### <a name="remarks"></a>Comentarios  
 Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada. Ninguna referencia adicional se coloca en el `Scheduler` objeto devuelto por este método.  
  
##  <a name="getnumberofvirtualprocessors"></a>GetNumberOfVirtualProcessors 

 Devuelve el número actual de procesadores virtuales para el programador asociado al contexto de la llamada.  
  
```
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si un programador está asociado al contexto de la llamada, el número actual de procesadores virtuales para ese programador; de lo contrario, el valor `-1`.  
  
### <a name="remarks"></a>Comentarios  
 Este método no producirá datos adjuntos de programador si el contexto de llamada ya no está asociado a un programador.  
  
 El valor devuelto de este método es un muestreo instantáneo del número de procesadores virtuales para el programador asociado al contexto de la llamada. Este valor puede ser obsoleto en el momento en que se devuelve.  
  
##  <a name="getpolicy"></a>GetPolicy 

 Devuelve una copia de la directiva que creó el programador actual.  
  
```
static SchedulerPolicy __cdecl GetPolicy();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una copia de la directiva que se creó el programador actual con.  
  
### <a name="remarks"></a>Comentarios  
 Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada.  
  
##  <a name="id"></a>Id. 

 Devuelve un identificador único para el programador actual.  
  
```
static unsigned int __cdecl Id();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si un programador está asociado al contexto de la llamada, un identificador único para ese programador; de lo contrario, el valor `-1`.  
  
### <a name="remarks"></a>Comentarios  
 Este método no producirá datos adjuntos de programador si el contexto de llamada ya no está asociado a un programador.  
  
##  <a name="isavailablelocation"></a>IsAvailableLocation 

 Determina si una determinada ubicación está disponible en el programador actual.  
  
```
static bool __cdecl IsAvailableLocation(const location& _Placement);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Placement`  
 Una referencia a la ubicación para el programador actual acerca de la consulta.  
  
### <a name="return-value"></a>Valor devuelto  
 Una indicación de si la ubicación especificada por el `_Placement` argumento está disponible en el programador actual.  
  
### <a name="remarks"></a>Comentarios  
 Este método no producirá datos adjuntos de programador si el contexto de llamada ya no está asociado a un programador.  
  
 Tenga en cuenta que el valor devuelto es un muestreo instantáneo de si está disponible la ubicación dada. En presencia de varios programadores, administración de recursos dinámicos puede agrega o quita los recursos de programadores en cualquier momento. Esto sucedería, la ubicación dada puede cambiar la disponibilidad.  
  
##  <a name="registershutdownevent"></a>RegisterShutdownEvent 

 Hace que el controlador de eventos de Windows pasado en el `_ShutdownEvent` parámetro se señalice cuando el programador asociado al contexto actual se cierra y se destruye. En el momento en que se señala el evento, todo el trabajo que está programado para el programador está completando. Mediante este método, se pueden registrar varios eventos de apagado.  
  
```
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```  
  
### <a name="parameters"></a>Parámetros  
 `_ShutdownEvent`  
 Identificador de un objeto de evento de Windows que señalará el tiempo de ejecución cuando el programador asociado al contexto actual se cierra y se destruye.  
  
### <a name="remarks"></a>Comentarios  
 Si no hay ningún programador adjuntado al contexto de la llamada, llamar a este método producirá una [scheduler_not_attached](scheduler-not-attached-class.md) excepción producida.  
  
##  <a name="scheduletask"></a>ScheduleTask 

 Programa una tarea ligera dentro del programador asociado al contexto llamado. La tarea ligera se situará en un grupo de programación determinada por el tiempo de ejecución. La versión que toma el parámetro `_Placement` hace que la tarea se inclina hacia la ejecución en la ubicación especificada.  
  
```
static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data);

static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Proc`  
 Un puntero a función que se ejecuta para realizar el cuerpo de la tarea ligera.  
  
 `_Data`  
 Un puntero void a los datos que se pasará como un parámetro en el cuerpo de la tarea.  
  
 `_Placement`  
 Una referencia a una ubicación donde la tarea ligera se se decanta hacia el hardware ejecutando en.  
  
### <a name="remarks"></a>Comentarios  
 Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [Scheduler (clase)](scheduler-class.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [Programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)




