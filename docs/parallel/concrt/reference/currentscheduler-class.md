---
title: CurrentScheduler (clase)
ms.date: 11/04/2016
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
helpviewer_keywords:
- CurrentScheduler class
ms.assetid: 31c20e0e-4cdf-49b4-8220-d726130aad2b
ms.openlocfilehash: 6bf61af9ff55722553353a045c87501dbd27fad9
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427414"
---
# <a name="currentscheduler-class"></a>CurrentScheduler (clase)

Representa una abstracción para el programador actual asociado al contexto de la llamada.

## <a name="syntax"></a>Sintaxis

```cpp
class CurrentScheduler;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Creación](#create)|Crea un nuevo programador cuyo comportamiento se describe en el `_Policy` parámetro y lo adjunta al contexto de llamada. El programador recién creado se convertirá en el programador actual para el contexto de llamada.|
|[Createschedulegroup (](#createschedulegroup)|Sobrecargado. Crea un nuevo grupo de programación dentro del programador asociado al contexto de llamada. La versión que toma el parámetro `_Placement` hace que las tareas del grupo de programación recién creado se desvíen hacia la ejecución en la ubicación especificada por ese parámetro.|
|[Separar](#detach)|Desasocia el programador actual del contexto de llamada y restaura el programador previamente asociado como el programador actual, si existe uno. Una vez que este método devuelve, el programador administra el contexto de la llamada que se adjuntó previamente al contexto mediante el método `CurrentScheduler::Create` o `Scheduler::Attach`.|
|[Get](#get)|Devuelve un puntero al programador asociado al contexto de la llamada, que también se conoce como programador actual.|
|[GetNumberOfVirtualProcessors (](#getnumberofvirtualprocessors)|Devuelve el número actual de procesadores virtuales para el programador asociado al contexto de llamada.|
|[Getpolicy (](#getpolicy)|Devuelve una copia de la Directiva con la que se creó el programador actual.|
|[Id](#id)|Devuelve un identificador único para el programador actual.|
|[Isavailablelocation (](#isavailablelocation)|Determina si una ubicación determinada está disponible en el programador actual.|
|[RegisterShutdownEvent (](#registershutdownevent)|Hace que el identificador de eventos de Windows pasado en el parámetro `_ShutdownEvent` se señalice cuando el programador asociado al contexto actual se cierra y se destruye. En el momento en que se señala el evento, se completa todo el trabajo que se ha programado para el programador. Se pueden registrar varios eventos de cierre mediante este método.|
|[ScheduleTask (](#scheduletask)|Sobrecargado. Programa una tarea ligera dentro del programador asociado al contexto de llamada. La tarea ligera se colocará en un grupo de programación determinado por el tiempo de ejecución. La versión que toma el parámetro `_Placement` hace que la tarea se desvíe hacia la ejecución en la ubicación especificada.|

## <a name="remarks"></a>Observaciones

Si no hay ningún programador (vea [Scheduler](scheduler-class.md)) asociado al contexto de llamada, muchos métodos dentro de la clase `CurrentScheduler` producirán datos adjuntos del programador predeterminado del proceso. Esto también puede implicar que el programador predeterminado del proceso se crea durante una llamada de este tipo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CurrentScheduler`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="create"></a> Crear

Crea un nuevo programador cuyo comportamiento se describe en el `_Policy` parámetro y lo adjunta al contexto de llamada. El programador recién creado se convertirá en el programador actual para el contexto de llamada.

```cpp
static void __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Parámetros

*_Policy*<br/>
La Directiva del programador que describe el comportamiento del programador recién creado.

### <a name="remarks"></a>Observaciones

Los datos adjuntos del programador al contexto de llamada colocan implícitamente un recuento de referencias en el programador.

Después de crear un programador con el método `Create`, debe llamar al método [CurrentScheduler::D Etach](#detach) en algún momento en el futuro para permitir que se cierre el programador.

Si se llama a este método desde un contexto que ya está asociado a un programador diferente, el programador existente se recuerda como el programador anterior y el programador recién creado se convierte en el programador actual. Cuando se llama al método `CurrentScheduler::Detach` en un punto posterior, el programador anterior se restaura como el programador actual.

Este método puede producir varias excepciones, incluidas [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md) y [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md).

## <a name="createschedulegroup"></a>Createschedulegroup (

Crea un nuevo grupo de programación dentro del programador asociado al contexto de llamada. La versión que toma el parámetro `_Placement` hace que las tareas del grupo de programación recién creado se desvíen hacia la ejecución en la ubicación especificada por ese parámetro.

```cpp
static ScheduleGroup* __cdecl CreateScheduleGroup();

static ScheduleGroup* __cdecl CreateScheduleGroup(location& _Placement);
```

### <a name="parameters"></a>Parámetros

*_Placement*<br/>
Referencia a una ubicación en la que las tareas dentro del grupo de programación se destinarán a su ejecución en.

### <a name="return-value"></a>Valor devuelto

Puntero al grupo de programación recién creado. Este objeto `ScheduleGroup` tiene un recuento de referencias inicial colocado en él.

### <a name="remarks"></a>Observaciones

Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada.

Debe invocar el método [Release](schedulegroup-class.md#release) en un grupo de programación cuando haya terminado de programar el trabajo. El programador destruirá el grupo de programación cuando se haya completado todo el trabajo en cola.

Tenga en cuenta que si ha creado explícitamente este programador, debe liberar todas las referencias a los grupos de programación que contiene, antes de liberar la referencia en el programador, desasociando el contexto actual de ella.

## <a name="detach"></a>Conecta

Desasocia el programador actual del contexto de llamada y restaura el programador previamente asociado como el programador actual, si existe uno. Una vez que este método devuelve, el programador administra el contexto de la llamada que se adjuntó previamente al contexto mediante el método `CurrentScheduler::Create` o `Scheduler::Attach`.

```cpp
static void __cdecl Detach();
```

### <a name="remarks"></a>Observaciones

El método `Detach` quita implícitamente un recuento de referencias del programador.

Si no hay ningún programador asociado al contexto de la llamada, al llamar a este método se producirá una excepción [scheduler_not_attached](scheduler-not-attached-class.md) .

La llamada a este método desde un contexto interno a y administrado por un programador, o un contexto que se adjuntó mediante un método distinto de los métodos [Scheduler:: Attach](scheduler-class.md#attach) o [CurrentScheduler:: Create](#create) , producirá una excepción [improper_scheduler_detach](improper-scheduler-detach-class.md) que se va a producir.

## <a name="get"></a>Obtener

Devuelve un puntero al programador asociado al contexto de la llamada, que también se conoce como programador actual.

```cpp
static Scheduler* __cdecl Get();
```

### <a name="return-value"></a>Valor devuelto

Puntero al programador asociado al contexto de la llamada (programador actual).

### <a name="remarks"></a>Observaciones

Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada. No se coloca ninguna referencia adicional en el objeto `Scheduler` devuelto por este método.

## <a name="getnumberofvirtualprocessors"></a>GetNumberOfVirtualProcessors (

Devuelve el número actual de procesadores virtuales para el programador asociado al contexto de llamada.

```cpp
static unsigned int __cdecl GetNumberOfVirtualProcessors();
```

### <a name="return-value"></a>Valor devuelto

Si un programador está asociado al contexto de la llamada, el número actual de procesadores virtuales para ese programador; de lo contrario, el valor `-1`.

### <a name="remarks"></a>Observaciones

Este método no producirá datos adjuntos del programador si el contexto de la llamada aún no está asociado a un programador.

El valor devuelto de este método es un muestreo instantáneo del número de procesadores virtuales para el programador asociado al contexto de llamada. Este valor puede estar obsoleto en el momento en que se devuelve.

## <a name="getpolicy"></a>Getpolicy (

Devuelve una copia de la Directiva con la que se creó el programador actual.

```cpp
static SchedulerPolicy __cdecl GetPolicy();
```

### <a name="return-value"></a>Valor devuelto

Una copia de la Directiva con la que se creó el programador actual.

### <a name="remarks"></a>Observaciones

Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada.

## <a name="id"></a>Sesión

Devuelve un identificador único para el programador actual.

```cpp
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>Valor devuelto

Si un programador está asociado al contexto de la llamada, un identificador único para ese programador; de lo contrario, el valor `-1`.

### <a name="remarks"></a>Observaciones

Este método no producirá datos adjuntos del programador si el contexto de la llamada aún no está asociado a un programador.

## <a name="isavailablelocation"></a>Isavailablelocation (

Determina si una ubicación determinada está disponible en el programador actual.

```cpp
static bool __cdecl IsAvailableLocation(const location& _Placement);
```

### <a name="parameters"></a>Parámetros

*_Placement*<br/>
Referencia a la ubicación sobre la que se va a consultar el programador actual.

### <a name="return-value"></a>Valor devuelto

Indicación de si la ubicación especificada por el argumento `_Placement` está disponible en el programador actual.

### <a name="remarks"></a>Observaciones

Este método no producirá datos adjuntos del programador si el contexto de la llamada aún no está asociado a un programador.

Tenga en cuenta que el valor devuelto es un muestreo instantáneo que indica si la ubicación especificada está disponible. En presencia de varios programadores, la administración dinámica de recursos puede Agregar o quitar recursos de programadores en cualquier momento. Si esto ocurre, la ubicación especificada puede cambiar la disponibilidad.

## <a name="registershutdownevent"></a>RegisterShutdownEvent (

Hace que el identificador de eventos de Windows pasado en el parámetro `_ShutdownEvent` se señalice cuando el programador asociado al contexto actual se cierra y se destruye. En el momento en que se señala el evento, se completa todo el trabajo que se ha programado para el programador. Se pueden registrar varios eventos de cierre mediante este método.

```cpp
static void __cdecl RegisterShutdownEvent(HANDLE _ShutdownEvent);
```

### <a name="parameters"></a>Parámetros

*_ShutdownEvent*<br/>
Identificador de un objeto de evento de Windows que será señalizado por el tiempo de ejecución cuando el programador asociado al contexto actual se cierra y se destruye.

### <a name="remarks"></a>Observaciones

Si no hay ningún programador asociado al contexto de la llamada, al llamar a este método se producirá una excepción [scheduler_not_attached](scheduler-not-attached-class.md) .

## <a name="scheduletask"></a>ScheduleTask (

Programa una tarea ligera dentro del programador asociado al contexto de llamada. La tarea ligera se colocará en un grupo de programación determinado por el tiempo de ejecución. La versión que toma el parámetro `_Placement` hace que la tarea se desvíe hacia la ejecución en la ubicación especificada.

```cpp
static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data);

static void __cdecl ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement);
```

### <a name="parameters"></a>Parámetros

*_Proc*<br/>
Puntero a la función que se va a ejecutar para realizar el cuerpo de la tarea ligera.

*_Data*<br/>
Un puntero void a los datos que se pasarán como parámetro al cuerpo de la tarea.

*_Placement*<br/>
Referencia a una ubicación en la que la tarea ligera se sesgará hacia la ejecución en.

### <a name="remarks"></a>Observaciones

Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Scheduler (clase)](scheduler-class.md)<br/>
[Policyelementkey (](concurrency-namespace-enums.md)<br/>
[Programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
