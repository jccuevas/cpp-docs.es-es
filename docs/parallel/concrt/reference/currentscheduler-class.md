---
title: CurrentScheduler (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71ca69f645e548b1913904f692eb1c5fae167a9a
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693762"
---
# <a name="currentscheduler-class"></a>CurrentScheduler (Clase)
Representa una abstracción para el programador actual asociado al contexto de la llamada.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CurrentScheduler;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Crear](#create)|Crea un nuevo programador cuyo comportamiento se describe en el `_Policy` parámetro y lo adjunta al contexto de la llamada. El programador creado recientemente se convertirá en el programador actual para el contexto de llamada.|  
|[CreateScheduleGroup](#createschedulegroup)|Sobrecargado. Crea un nuevo grupo de programación dentro del programador asociado al contexto llamado. La versión que toma el parámetro `_Placement` hace que las tareas dentro del grupo de programación recién creado para ser inclinación hacia la ejecución en la ubicación especificada por ese parámetro.|  
|[Desasociar](#detach)|Desasocia al programador actual desde el contexto de llamada y restaura al programador asociado anteriormente como programador actual, si existe alguno. Después de que devuelve este método, el contexto de llamada es administrado por el programador que se ha adjuntado previamente en el contexto utilizando la `CurrentScheduler::Create` o `Scheduler::Attach` método.|  
|[Get](#get)|Devuelve un puntero al programador asociado con el contexto de la llamada, que también se denomina el programador actual.|  
|[GetNumberOfVirtualProcessors](#getnumberofvirtualprocessors)|Devuelve el número actual de procesadores virtuales para el programador asociado con el contexto de llamada.|  
|[GetPolicy](#getpolicy)|Devuelve una copia de la directiva que se creó el programador actual con.|  
|[Id.](#id)|Devuelve un identificador único para el programador actual.|  
|[IsAvailableLocation](#isavailablelocation)|Determina si una ubicación especificada está disponible en el programador actual.|  
|[RegisterShutdownEvent](#registershutdownevent)|Hace que el controlador de eventos de Windows pasa el `_ShutdownEvent` parámetro hasta que se señaliza cuando el programador asociado al contexto actual se cierra y se destruye. En el momento en que se señala el evento, todo el trabajo que está programado para el programador está completando. Se pueden registrar varios eventos de apagado a través de este método.|  
|[ScheduleTask](#scheduletask)|Sobrecargado. Programa una tarea ligera dentro del programador asociado al contexto llamado. La tarea ligera se colocarán en un grupo de programación determinado por el tiempo de ejecución. La versión que toma el parámetro `_Placement` hace que la tarea se inclina a ejecutar en la ubicación especificada.|  
  
## <a name="remarks"></a>Comentarios  
 Si no hay ningún programador (vea [programador](scheduler-class.md)) asociado al contexto de la llamada, muchos métodos dentro de la `CurrentScheduler` clase producirá datos adjuntos de programador de forma predeterminada el proceso. Esto también puede implicar que el programador del proceso de forma predeterminada se crea durante una llamada de este tipo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CurrentScheduler`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="create"></a> Crear 

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
  
 Si se llama a este método desde un contexto que ya está conectado a un programador diferente, el programador existente se recuerda como el programador anterior y el programador creado recientemente se convierte en el programador actual. Cuando se llama a la `CurrentScheduler::Detach` método en un momento posterior, el programador anterior se restaura como el programador actual.  
  
 Este método puede producir una variedad de excepciones, incluida la [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md) y [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md).  
  
##  <a name="createschedulegroup"></a> CreateScheduleGroup 

 Crea un nuevo grupo de programación dentro del programador asociado al contexto llamado. La versión que toma el parámetro `_Placement` hace que las tareas dentro del grupo de programación recién creado para ser inclinación hacia la ejecución en la ubicación especificada por ese parámetro.  
  
```
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Placement`  
 Una referencia a una ubicación donde las tareas dentro del grupo de programación se se inclina hacia ejecutarse en.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al grupo de programación recién creado. Esto `ScheduleGroup` objeto tiene un recuento de referencia inicial colocado en él.  
  
### <a name="remarks"></a>Comentarios  
 Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada.  
  
 Se debe invocar el [versión](schedulegroup-class.md#release) método en un grupo de programación cuando haya terminado de programación de trabajo en él. El programador destruirá la programación de grupo cuando todo el trabajo de cola se ha completado.  
  
 Tenga en cuenta que si creó a este programador explícitamente, debe liberar todas las referencias para programar grupos dentro de él, antes de liberar su referencia en el programador, separando el contexto actual de ella.  
  
##  <a name="detach"></a> Desconectar 

 Desasocia al programador actual desde el contexto de llamada y restaura al programador asociado anteriormente como programador actual, si existe alguno. Después de que devuelve este método, el contexto de llamada es administrado por el programador que se ha adjuntado previamente en el contexto utilizando la `CurrentScheduler::Create` o `Scheduler::Attach` método.  
  
```
static void __cdecl Detach();
```  
  
### <a name="remarks"></a>Comentarios  
 El `Detach` método quita implícitamente un recuento de referencias del programador.  
  
 Si no hay ningún programador adjuntado al contexto de la llamada, llamar a este método dará como resultado un [scheduler_not_attached](scheduler-not-attached-class.md) excepción producida.  
  
 Llamar a este método desde un contexto que es interno y administrados por un programador, o en un contexto que estaba conectado con un método distinto de la [Scheduler:: Attach](scheduler-class.md#attach) o [CurrentScheduler:: Create](#create) métodos, dará como resultado un [improper_scheduler_detach](improper-scheduler-detach-class.md) excepción producida.  
  
##  <a name="get"></a> Obtener 

 Devuelve un puntero al programador asociado con el contexto de la llamada, que también se denomina el programador actual.  
  
```
static Scheduler* __cdecl Get();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al programador asociado con el contexto de llamada (el programador actual).  
  
### <a name="remarks"></a>Comentarios  
 Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada. Ninguna referencia adicional se coloca en el `Scheduler` objeto devuelto por este método.  
  
##  <a name="getnumberofvirtualprocessors"></a> GetNumberOfVirtualProcessors 

 Devuelve el número actual de procesadores virtuales para el programador asociado con el contexto de llamada.  
  
```
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si un programador está asociado al contexto de la llamada, el número actual de procesadores virtuales de ese programador; en caso contrario, el valor `-1`.  
  
### <a name="remarks"></a>Comentarios  
 Este método no producirá datos adjuntos de programador si el contexto de llamada ya no está asociado a un programador.  
  
 El valor devuelto de este método es un muestreo instantáneo del número de procesadores virtuales para el programador asociado con el contexto de llamada. Este valor puede ser obsoleto en el momento en que se devuelve.  
  
##  <a name="getpolicy"></a> GetPolicy 

 Devuelve una copia de la directiva que se creó el programador actual con.  
  
```
static SchedulerPolicy __cdecl GetPolicy();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una copia de la directiva que se creó el programador actual con.  
  
### <a name="remarks"></a>Comentarios  
 Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada.  
  
##  <a name="id"></a> Id. 

 Devuelve un identificador único para el programador actual.  
  
```
static unsigned int __cdecl Id();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si un programador está asociado con el contexto de llamada, un identificador único para ese programador; en caso contrario, el valor `-1`.  
  
### <a name="remarks"></a>Comentarios  
 Este método no producirá datos adjuntos de programador si el contexto de llamada ya no está asociado a un programador.  
  
##  <a name="isavailablelocation"></a> IsAvailableLocation 

 Determina si una ubicación especificada está disponible en el programador actual.  
  
```
static bool __cdecl IsAvailableLocation(const location& _Placement);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Placement`  
 Una referencia a la ubicación para consultar al programador actual sobre.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que indica si la ubicación especificada por el `_Placement` argumento está disponible en el programador actual.  
  
### <a name="remarks"></a>Comentarios  
 Este método no producirá datos adjuntos de programador si el contexto de llamada ya no está asociado a un programador.  
  
 Tenga en cuenta que el valor devuelto es un muestreo instantáneo de si está disponible la ubicación dada. En presencia de varios programadores, administración dinámica de recursos puede agregar o quitar recursos de programadores en cualquier momento. Esto sucederá, la ubicación dada puede cambiar la disponibilidad.  
  
##  <a name="registershutdownevent"></a> RegisterShutdownEvent 

 Hace que el controlador de eventos de Windows pasa el `_ShutdownEvent` parámetro hasta que se señaliza cuando el programador asociado al contexto actual se cierra y se destruye. En el momento en que se señala el evento, todo el trabajo que está programado para el programador está completando. Se pueden registrar varios eventos de apagado a través de este método.  
  
```
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```  
  
### <a name="parameters"></a>Parámetros  
 `_ShutdownEvent`  
 Un identificador para un objeto de evento de Windows que se señalará en tiempo de ejecución cuando el programador asociado al contexto actual se cierra y se destruye.  
  
### <a name="remarks"></a>Comentarios  
 Si no hay ningún programador adjuntado al contexto de la llamada, llamar a este método dará como resultado un [scheduler_not_attached](scheduler-not-attached-class.md) excepción producida.  
  
##  <a name="scheduletask"></a> ScheduleTask 

 Programa una tarea ligera dentro del programador asociado al contexto llamado. La tarea ligera se colocarán en un grupo de programación determinado por el tiempo de ejecución. La versión que toma el parámetro `_Placement` hace que la tarea se inclina a ejecutar en la ubicación especificada.  
  
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
 Un puntero a función que se ejecuta para llevar a cabo el cuerpo de la tarea ligera.  
  
 `_Data`  
 Un puntero void para los datos que se pasarán como un parámetro en el cuerpo de la tarea.  
  
 `_Placement`  
 Una referencia a una ubicación donde se se inclina la tarea ligera para ejecutarse en.  
  
### <a name="remarks"></a>Comentarios  
 Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [Scheduler (clase)](scheduler-class.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [Programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



