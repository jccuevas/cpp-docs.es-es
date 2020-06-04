---
title: Scheduler (clase)
ms.date: 11/04/2016
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
helpviewer_keywords:
- Scheduler class
ms.assetid: 34cf7961-048d-4852-8a5c-a32f823e3506
ms.openlocfilehash: 77ad876b8352ab1ae86fde622b05712ec5f2cea9
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427354"
---
# <a name="scheduler-class"></a>Scheduler (clase)

Representa una abstracción para un programador del runtime de simultaneidad.

## <a name="syntax"></a>Sintaxis

```cpp
class Scheduler;
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[Scheduler](#ctor)|Un objeto de la clase `Scheduler` solo se puede crear mediante métodos de generador o implícitamente.|
|[~ (Destructor)](#dtor)|Un objeto de la clase `Scheduler` se destruye implícitamente cuando deja de existir todas las referencias externas a él.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Adjuntar](#attach)|Asocia el programador al contexto de la llamada. Una vez que este método devuelve, el programador administra el contexto de la llamada y el programador se convierte en el programador actual.|
|[Creación](#create)|Crea un nuevo programador cuyo comportamiento se describe en el `_Policy` parámetro, coloca una referencia inicial en el programador y devuelve un puntero a él.|
|[Createschedulegroup (](#createschedulegroup)|Sobrecargado. Crea un nuevo grupo de programación dentro del programador. La versión que toma el parámetro `_Placement` hace que las tareas del grupo de programación recién creado se desvíen hacia la ejecución en la ubicación especificada por ese parámetro.|
|[GetNumberOfVirtualProcessors (](#getnumberofvirtualprocessors)|Devuelve el número actual de procesadores virtuales para el programador.|
|[Getpolicy (](#getpolicy)|Devuelve una copia de la Directiva con la que se creó el programador.|
|[Id](#id)|Devuelve un identificador único para el programador.|
|[Isavailablelocation (](#isavailablelocation)|Determina si una ubicación determinada está disponible en el programador.|
|[Referencia](#reference)|Incrementa el recuento de referencias del programador.|
|[RegisterShutdownEvent (](#registershutdownevent)|Hace que el identificador de eventos de Windows pasado en el parámetro `_Event` se señalice cuando el programador se cierra y se destruye. En el momento en que se señala el evento, se completa todo el trabajo que se ha programado para el programador. Se pueden registrar varios eventos de cierre mediante este método.|
|[Versión](#release)|Disminuye el recuento de referencias del programador.|
|[Resetdefaultschedulerpolicy (](#resetdefaultschedulerpolicy)|Restablece la directiva predeterminada del programador en el tiempo de ejecución predeterminado. La próxima vez que se cree un programador predeterminado, utilizará la configuración de directiva predeterminada en tiempo de ejecución.|
|[ScheduleTask (](#scheduletask)|Sobrecargado. Programa una tarea ligera dentro del programador. La tarea ligera se colocará en un grupo de programación determinado por el tiempo de ejecución. La versión que toma el parámetro `_Placement` hace que la tarea se desvíe hacia la ejecución en la ubicación especificada.|
|[SetDefaultSchedulerPolicy (](#setdefaultschedulerpolicy)|Permite usar una directiva definida por el usuario para crear el programador predeterminado. Solo se puede llamar a este método cuando no existe ningún programador predeterminado en el proceso. Una vez establecida una directiva predeterminada, permanece en vigor hasta la siguiente llamada válida al método `SetDefaultSchedulerPolicy` o [resetdefaultschedulerpolicy (](#resetdefaultschedulerpolicy) .|

## <a name="remarks"></a>Observaciones

El programador de Runtime de simultaneidad utiliza contextos de ejecución, que se asignan a los contextos de ejecución del sistema operativo, como un subproceso, para ejecutar el trabajo en la cola de la aplicación. En cualquier momento, el nivel de simultaneidad de un programador es igual al número de procesadores virtuales concedidos por el Administrador de recursos. Un procesador virtual es una abstracción para un recurso de procesamiento y se asigna a un subproceso del hardware en el sistema subyacente. Solo se puede ejecutar un único contexto del programador en un procesador virtual a una hora determinada.

El Runtime de simultaneidad creará un programador predeterminado por proceso para ejecutar el trabajo paralelo. Además, puede crear sus propias instancias de Scheduler y manipularlas con esta clase.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Scheduler`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="attach"></a>Incluir

Asocia el programador al contexto de la llamada. Una vez que este método devuelve, el programador administra el contexto de la llamada y el programador se convierte en el programador actual.

```cpp
virtual void Attach() = 0;
```

### <a name="remarks"></a>Observaciones

Al adjuntar un programador, se coloca implícitamente una referencia en el programador.

En algún momento en el futuro, debe llamar al método [CurrentScheduler::D Etach](currentscheduler-class.md#detach) para permitir que el programador se cierre.

Si se llama a este método desde un contexto que ya está asociado a un programador diferente, el programador existente se recuerda como el programador anterior y el programador recién creado se convierte en el programador actual. Cuando se llama al método `CurrentScheduler::Detach` en un punto posterior, el programador anterior se restaura como el programador actual.

Este método producirá una excepción [improper_scheduler_attach](improper-scheduler-attach-class.md) si este programador es el programador actual del contexto de llamada.

## <a name="create"></a> Crear

Crea un nuevo programador cuyo comportamiento se describe en el `_Policy` parámetro, coloca una referencia inicial en el programador y devuelve un puntero a él.

```cpp
static Scheduler* __cdecl Create(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Parámetros

*_Policy*<br/>
Directiva del programador que describe el comportamiento del programador recién creado.

### <a name="return-value"></a>Valor devuelto

Un puntero a un programador recién creado. Este objeto `Scheduler` tiene un recuento de referencias inicial colocado en él.

### <a name="remarks"></a>Observaciones

Después de crear un programador con el método `Create`, debe llamar al método `Release` en algún momento en el futuro para quitar el recuento de referencias inicial y permitir que el programador se cierre.

Un programador creado con este método no está asociado al contexto de llamada. Se puede adjuntar a un contexto mediante el método [Attach](#attach) .

Este método puede producir varias excepciones, incluidas [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md) y [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md).

## <a name="createschedulegroup"></a>Createschedulegroup (

Crea un nuevo grupo de programación dentro del programador. La versión que toma el parámetro `_Placement` hace que las tareas del grupo de programación recién creado se desvíen hacia la ejecución en la ubicación especificada por ese parámetro.

```cpp
virtual ScheduleGroup* CreateScheduleGroup() = 0;

virtual ScheduleGroup* CreateScheduleGroup(location& _Placement) = 0;
```

### <a name="parameters"></a>Parámetros

*_Placement*<br/>
Referencia a una ubicación en la que las tareas dentro del grupo de programación se sesgarán en la ejecución en.

### <a name="return-value"></a>Valor devuelto

Puntero al grupo de programación recién creado. Este objeto `ScheduleGroup` tiene un recuento de referencias inicial colocado en él.

### <a name="remarks"></a>Observaciones

Debe invocar el método [Release](schedulegroup-class.md#release) en un grupo de programación cuando haya terminado de programar el trabajo. El programador destruirá el grupo de programación cuando se haya completado todo el trabajo en cola.

Tenga en cuenta que si ha creado explícitamente este programador, debe liberar todas las referencias a los grupos de programación que contiene, antes de liberar las referencias en el programador.

## <a name="getnumberofvirtualprocessors"></a>GetNumberOfVirtualProcessors (

Devuelve el número actual de procesadores virtuales para el programador.

```cpp
virtual unsigned int GetNumberOfVirtualProcessors() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Número actual de procesadores virtuales para el programador.

## <a name="getpolicy"></a>Getpolicy (

Devuelve una copia de la Directiva con la que se creó el programador.

```cpp
virtual SchedulerPolicy GetPolicy() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Una copia de la Directiva con la que se creó el programador.

## <a name="id"></a>Sesión

Devuelve un identificador único para el programador.

```cpp
virtual unsigned int Id() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador único para el programador.

## <a name="isavailablelocation"></a>Isavailablelocation (

Determina si una ubicación determinada está disponible en el programador.

```cpp
virtual bool IsAvailableLocation(const location& _Placement) const = 0;
```

### <a name="parameters"></a>Parámetros

*_Placement*<br/>
Referencia a la ubicación sobre la que se va a consultar el programador.

### <a name="return-value"></a>Valor devuelto

Indicación de si la ubicación especificada por el argumento `_Placement` está disponible en el programador.

### <a name="remarks"></a>Observaciones

Tenga en cuenta que el valor devuelto es un muestreo instantáneo que indica si la ubicación especificada está disponible. En presencia de varios programadores, la administración dinámica de recursos puede Agregar o quitar recursos de programadores en cualquier momento. Si esto ocurre, la ubicación especificada puede cambiar la disponibilidad.

## <a name="reference"></a>Referencia

Incrementa el recuento de referencias del programador.

```cpp
virtual unsigned int Reference() = 0 ;
```

### <a name="return-value"></a>Valor devuelto

Recuento de referencias incrementado recientemente.

### <a name="remarks"></a>Observaciones

Normalmente se utiliza para administrar la duración del programador para la composición. Cuando el recuento de referencias de un programador cae a cero, el programador se apagará y se desestructurará por sí mismo una vez completado todo el trabajo en el programador.

El método producirá una excepción [improper_scheduler_reference](improper-scheduler-reference-class.md) si el recuento de referencias antes de llamar al método `Reference` era cero y la llamada se realiza desde un contexto que no es propiedad del programador.

## <a name="registershutdownevent"></a>RegisterShutdownEvent (

Hace que el identificador de eventos de Windows pasado en el parámetro `_Event` se señalice cuando el programador se cierra y se destruye. En el momento en que se señala el evento, se completa todo el trabajo que se ha programado para el programador. Se pueden registrar varios eventos de cierre mediante este método.

```cpp
virtual void RegisterShutdownEvent(HANDLE _Event) = 0;
```

### <a name="parameters"></a>Parámetros

*_Event*<br/>
Identificador de un objeto de evento de Windows que será señalizado por el tiempo de ejecución cuando el programador se cierre y se destruya.

## <a name="release"></a>Emisión

Disminuye el recuento de referencias del programador.

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>Valor devuelto

Recuento de referencias disminuido recientemente.

### <a name="remarks"></a>Observaciones

Normalmente se utiliza para administrar la duración del programador para la composición. Cuando el recuento de referencias de un programador cae a cero, el programador se apagará y se desestructurará por sí mismo una vez completado todo el trabajo en el programador.

## <a name="resetdefaultschedulerpolicy"></a>Resetdefaultschedulerpolicy (

Restablece la directiva predeterminada del programador en el tiempo de ejecución predeterminado. La próxima vez que se cree un programador predeterminado, utilizará la configuración de directiva predeterminada en tiempo de ejecución.

```cpp
static void __cdecl ResetDefaultSchedulerPolicy();
```

### <a name="remarks"></a>Observaciones

Se puede llamar a este método mientras exista un programador predeterminado dentro del proceso. No afectará a la Directiva del programador predeterminado existente. Sin embargo, si el programador predeterminado se cerrara y se creara un nuevo valor predeterminado en un momento posterior, el nuevo programador utilizaría la configuración de directiva predeterminada en tiempo de ejecución.

## <a name="ctor"></a>Aquél

Un objeto de la clase `Scheduler` solo se puede crear mediante métodos de generador o implícitamente.

```cpp
Scheduler();
```

### <a name="remarks"></a>Observaciones

El programador predeterminado del proceso se crea implícitamente cuando se usan muchas de las funciones en tiempo de ejecución que requieren que se adjunte un programador al contexto de llamada. Los métodos dentro de la clase `CurrentScheduler` y las características de la biblioteca PPL y los niveles de agentes suelen realizar datos adjuntos implícitos.

También puede crear un programador explícitamente mediante el método `CurrentScheduler::Create` o el método `Scheduler::Create`.

## <a name="dtor"></a>~ Scheduler

Un objeto de la clase `Scheduler` se destruye implícitamente cuando deja de existir todas las referencias externas a él.

```cpp
virtual ~Scheduler();
```

## <a name="scheduletask"></a>ScheduleTask (

Programa una tarea ligera dentro del programador. La tarea ligera se colocará en un grupo de programación determinado por el tiempo de ejecución. La versión que toma el parámetro `_Placement` hace que la tarea se desvíe hacia la ejecución en la ubicación especificada.

```cpp
virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data) = 0;

virtual void ScheduleTask(
    TaskProc _Proc,
    _Inout_opt_ void* _Data,
    location& _Placement) = 0;
```

### <a name="parameters"></a>Parámetros

*_Proc*<br/>
Puntero a la función que se va a ejecutar para realizar el cuerpo de la tarea ligera.

*_Data*<br/>
Un puntero void a los datos que se pasarán como parámetro al cuerpo de la tarea.

*_Placement*<br/>
Referencia a una ubicación en la que la tarea ligera se sesgará hacia la ejecución en.

## <a name="setdefaultschedulerpolicy"></a>SetDefaultSchedulerPolicy (

Permite usar una directiva definida por el usuario para crear el programador predeterminado. Solo se puede llamar a este método cuando no existe ningún programador predeterminado en el proceso. Una vez establecida una directiva predeterminada, permanece en vigor hasta la siguiente llamada válida al método `SetDefaultSchedulerPolicy` o [resetdefaultschedulerpolicy (](#resetdefaultschedulerpolicy) .

```cpp
static void __cdecl SetDefaultSchedulerPolicy(const SchedulerPolicy& _Policy);
```

### <a name="parameters"></a>Parámetros

*_Policy*<br/>
Directiva que se va a establecer como la directiva predeterminada del programador.

### <a name="remarks"></a>Observaciones

Si se llama al método `SetDefaultSchedulerPolicy` cuando ya existe un programador predeterminado en el proceso, el tiempo de ejecución producirá una excepción [default_scheduler_exists](default-scheduler-exists-class.md) .

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Scheduler (clase)](scheduler-class.md)<br/>
[Policyelementkey (](concurrency-namespace-enums.md)<br/>
[Programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
