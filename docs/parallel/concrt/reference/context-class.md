---
title: Context (clase)
ms.date: 11/04/2016
f1_keywords:
- Context
- CONCRT/concurrency::Context
- CONCRT/concurrency::Context::Block
- CONCRT/concurrency::Context::CurrentContext
- CONCRT/concurrency::Context::GetId
- CONCRT/concurrency::Context::GetScheduleGroupId
- CONCRT/concurrency::Context::GetVirtualProcessorId
- CONCRT/concurrency::Context::Id
- CONCRT/concurrency::Context::IsCurrentTaskCollectionCanceling
- CONCRT/concurrency::Context::IsSynchronouslyBlocked
- CONCRT/concurrency::Context::Oversubscribe
- CONCRT/concurrency::Context::ScheduleGroupId
- CONCRT/concurrency::Context::Unblock
- CONCRT/concurrency::Context::VirtualProcessorId
- CONCRT/concurrency::Context::Yield
helpviewer_keywords:
- Context class
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
ms.openlocfilehash: 7c47d9db64b0af7d5413abed3f85e9d41a591fa2
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427408"
---
# <a name="context-class"></a>Context (clase)

Representa una abstracción para un contexto de ejecución.

## <a name="syntax"></a>Sintaxis

```cpp
class Context;
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[~ (Destructor de contexto)](#dtor)||

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Bloque](#block)|Bloquea el contexto actual.|
|[CurrentContext](#currentcontext)|Devuelve un puntero al contexto actual.|
|[GetId](#getid)|Devuelve un identificador para el contexto que es único dentro del programador al que pertenece el contexto.|
|[Getschedulegroupid (](#getschedulegroupid)|Devuelve un identificador para el grupo de programación en el que el contexto está trabajando actualmente.|
|[Getvirtualprocessorid (](#getvirtualprocessorid)|Devuelve un identificador para el procesador virtual en el que el contexto se está ejecutando actualmente.|
|[Id](#id)|Devuelve un identificador para el contexto actual que es único dentro del programador al que pertenece el contexto actual.|
|[Iscurrenttaskcollectioncanceling (](#iscurrenttaskcollectioncanceling)|Devuelve una indicación de si la colección de tareas que actualmente se ejecuta alineada en el contexto actual, está en medio de una cancelación activa (o lo estará pronto).|
|[Issynchronouslyblocked (](#issynchronouslyblocked)|Determina si el contexto está o no bloqueado de forma sincrónica. Se considera que un contexto está bloqueado de forma sincrónica si realizó una acción que condujo al bloqueo explícitamente.|
|[Saturar](#oversubscribe)|Inserta un procesador virtual adicional en un programador para la duración de un bloque de código cuando se invoca en un contexto que se ejecuta en uno de los procesadores virtuales de ese programador.|
|[ScheduleGroupId (](#schedulegroupid)|Devuelve un identificador para el grupo de programación en el que el contexto actual está trabajando.|
|[Desbloquear](#unblock)|Desbloquea el contexto y hace que se convierta en ejecutable.|
|[Virtualprocessorid (](#virtualprocessorid)|Devuelve un identificador para el procesador virtual en el que el contexto actual se está ejecutando.|
|[Yield](#yield)|Genera la ejecución para que otro contexto se pueda ejecutar. Si no hay ningún otro contexto disponible para dar prioridad, el programador puede dar prioridad a otro subproceso del sistema operativo.|

## <a name="remarks"></a>Observaciones

El programador de Runtime de simultaneidad (consulte [Scheduler](scheduler-class.md)) utiliza contextos de ejecución para ejecutar el trabajo en la cola de la aplicación. Un subproceso de Win32 es un ejemplo de un contexto de ejecución en un sistema operativo Windows.

En cualquier momento, el nivel de simultaneidad de un programador es igual al número de procesadores virtuales que le ha concedido el Administrador de recursos. Un procesador virtual es una abstracción para un recurso de procesamiento y se asigna a un subproceso del hardware en el sistema subyacente. Solo se puede ejecutar un único contexto del programador en un procesador virtual a una hora determinada.

El programador es cooperativo por su naturaleza y un contexto de ejecución puede producir su procesador virtual en un contexto diferente en cualquier momento si desea escribir un estado de espera. Cuando la espera se cumple, no se puede volver a reanudar hasta que un procesador virtual disponible del programador comienza su ejecución.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Context`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

**Espacio de nombres:** simultaneidad

## <a name="block"></a>Sin

Bloquea el contexto actual.

```cpp
static void __cdecl Block();
```

### <a name="remarks"></a>Observaciones

Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada.

Si el contexto de llamada se ejecuta en un procesador virtual, el procesador virtual encontrará otro contexto ejecutable para ejecutarse o podría crear uno nuevo.

Una vez que se ha llamado al método `Block` o se le va a llamar, debe emparejarlo con una llamada al método [unblock](#unblock) desde otro contexto de ejecución para que se ejecute de nuevo. Tenga en cuenta que hay un período crítico entre el punto en el que el código publica su contexto para que otro subproceso pueda llamar al método `Unblock` y el punto en el que se realiza la llamada de método real a `Block`. Durante este período, no debe llamar a ningún método que, a su vez, se bloquee y desbloquee por sus propias razones (por ejemplo, la adquisición de un bloqueo). Las llamadas al método `Block` y `Unblock` no realizan un seguimiento de la razón del bloqueo y desbloqueo. Solo un objeto debe tener la propiedad de una `Block`- par de `Unblock`.

Este método puede producir varias excepciones, incluidas [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md).

## <a name="dtor"></a>~ Contexto

```cpp
virtual ~Context();
```

## <a name="currentcontext"></a>CurrentContext

Devuelve un puntero al contexto actual.

```cpp
static Context* __cdecl CurrentContext();
```

### <a name="return-value"></a>Valor devuelto

Puntero al contexto actual.

### <a name="remarks"></a>Observaciones

Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada.

## <a name="getid"></a>GetId

Devuelve un identificador para el contexto que es único dentro del programador al que pertenece el contexto.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador del contexto que es único dentro del programador al que pertenece el contexto.

## <a name="getschedulegroupid"></a>Getschedulegroupid (

Devuelve un identificador para el grupo de programación en el que el contexto está trabajando actualmente.

```cpp
virtual unsigned int GetScheduleGroupId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador del grupo de programación en el que está trabajando actualmente el contexto.

### <a name="remarks"></a>Observaciones

El valor devuelto de este método es un muestreo instantáneo del grupo de programación en el que se está ejecutando el contexto. Si se llama a este método en un contexto distinto del contexto actual, el valor puede quedar obsoleto en el momento en que se devuelva y no se pueda confiar en él. Normalmente, este método se usa solo con fines de depuración o seguimiento.

## <a name="getvirtualprocessorid"></a>Getvirtualprocessorid (

Devuelve un identificador para el procesador virtual en el que el contexto se está ejecutando actualmente.

```cpp
virtual unsigned int GetVirtualProcessorId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Si el contexto se está ejecutando actualmente en un procesador virtual, identificador del procesador virtual en el que se está ejecutando actualmente el contexto; de lo contrario, el valor `-1`.

### <a name="remarks"></a>Observaciones

El valor devuelto de este método es un muestreo instantáneo del procesador virtual en el que se está ejecutando el contexto. Este valor puede estar obsoleto en el momento en que se devuelva y no se pueda confiar en él. Normalmente, este método se usa solo con fines de depuración o seguimiento.

## <a name="id"></a>Sesión

Devuelve un identificador para el contexto actual que es único dentro del programador al que pertenece el contexto actual.

```cpp
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>Valor devuelto

Si el contexto actual está asociado a un programador, identificador del contexto actual que es único dentro del programador al que pertenece el contexto actual; de lo contrario, el valor `-1`.

## <a name="iscurrenttaskcollectioncanceling"></a>Iscurrenttaskcollectioncanceling (

Devuelve una indicación de si la colección de tareas que actualmente se ejecuta alineada en el contexto actual, está en medio de una cancelación activa (o lo estará pronto).

```cpp
static bool __cdecl IsCurrentTaskCollectionCanceling();
```

### <a name="return-value"></a>Valor devuelto

Si un programador está asociado al contexto de llamada y un grupo de tareas está ejecutando una tarea insertada en ese contexto, una indicación de si ese grupo de tareas está en medio de una cancelación activa (o será breve); de lo contrario, el valor `false`.

## <a name="issynchronouslyblocked"></a>Issynchronouslyblocked (

Determina si el contexto está o no bloqueado de forma sincrónica. Se considera que un contexto está bloqueado de forma sincrónica si realizó una acción que condujo al bloqueo explícitamente.

```cpp
virtual bool IsSynchronouslyBlocked() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Indica si el contexto está bloqueado de forma sincrónica.

### <a name="remarks"></a>Observaciones

Se considera que un contexto está bloqueado de forma sincrónica si realizó una acción que condujo al bloqueo explícitamente. En el programador de subprocesos, esto indicaría una llamada directa al método `Context::Block` o un objeto de sincronización que se compiló mediante el método `Context::Block`.

El valor devuelto de este método es un ejemplo instantáneo de si el contexto está bloqueado de forma sincrónica. Este valor puede estar obsoleto en el momento en que se devuelve y solo se puede usar en circunstancias muy específicas.

## <a name="operator_delete"></a>operador Delete

El tiempo de ejecución destruye internamente un objeto `Context`. No se puede eliminar explícitamente.

```cpp
void operator delete(void* _PObject);
```

### <a name="parameters"></a>Parámetros

*_PObject*<br/>
Puntero al objeto que se va a eliminar.

## <a name="oversubscribe"></a>Saturar

Inserta un procesador virtual adicional en un programador para la duración de un bloque de código cuando se invoca en un contexto que se ejecuta en uno de los procesadores virtuales de ese programador.

```cpp
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```

### <a name="parameters"></a>Parámetros

*_BeginOversubscription*<br/>
Si **es true**, indica que se debe agregar un procesador virtual adicional para la duración de la suscripción excesiva. Si **es false**, indica que la suscripción excesiva debe finalizar y se debe quitar el procesador virtual agregado previamente.

## <a name="schedulegroupid"></a>ScheduleGroupId (

Devuelve un identificador para el grupo de programación en el que el contexto actual está trabajando.

```cpp
static unsigned int __cdecl ScheduleGroupId();
```

### <a name="return-value"></a>Valor devuelto

Si el contexto actual se adjunta a un programador y está trabajando en un grupo de programación, un identificador para el grupo de Scheduler en el que está trabajando el contexto actual; de lo contrario, el valor `-1`.

## <a name="unblock"></a>Desbloquear

Desbloquea el contexto y hace que se convierta en ejecutable.

```cpp
virtual void Unblock() = 0;
```

### <a name="remarks"></a>Observaciones

Es absolutamente válido que una llamada al método `Unblock` precede a una llamada correspondiente al método [Block](#block) . Siempre que las llamadas a los métodos `Block` y `Unblock` se emparejan correctamente, el tiempo de ejecución controla correctamente la carrera natural de cualquier orden. Una llamada `Unblock` que va antes de una llamada a `Block` simplemente niega el efecto de la llamada a `Block`.

Hay varias excepciones que se pueden producir desde este método. Si un contexto intenta llamar al método `Unblock` en sí mismo, se producirá una excepción [context_self_unblock](context-self-unblock-class.md) . Si las llamadas a `Block` y `Unblock` no se emparejan correctamente (por ejemplo, se realizan dos llamadas a `Unblock` para un contexto que se está ejecutando actualmente), se iniciará una excepción de [context_unblock_unbalanced](context-unblock-unbalanced-class.md) .

Tenga en cuenta que hay un período crítico entre el punto en el que el código publica su contexto para que otro subproceso pueda llamar al método `Unblock` y el punto en el que se realiza la llamada de método real a `Block`. Durante este período, no debe llamar a ningún método que, a su vez, se bloquee y desbloquee por sus propias razones (por ejemplo, la adquisición de un bloqueo). Las llamadas al método `Block` y `Unblock` no realizan un seguimiento de la razón del bloqueo y desbloqueo. Solo un objeto debe tener la propiedad de un par de `Block` y `Unblock`.

## <a name="virtualprocessorid"></a>Virtualprocessorid (

Devuelve un identificador para el procesador virtual en el que el contexto actual se está ejecutando.

```cpp
static unsigned int __cdecl VirtualProcessorId();
```

### <a name="return-value"></a>Valor devuelto

Si el contexto actual está asociado a un programador, identificador del procesador virtual en el que se está ejecutando el contexto actual; de lo contrario, el valor `-1`.

### <a name="remarks"></a>Observaciones

El valor devuelto de este método es un muestreo instantáneo del procesador virtual en el que se está ejecutando el contexto actual. Este valor puede estar obsoleto en el momento en que se devuelva y no se pueda confiar en él. Normalmente, este método se usa solo con fines de depuración o seguimiento.

## <a name="yield"></a>Yield

Genera la ejecución para que otro contexto se pueda ejecutar. Si no hay ningún otro contexto disponible para dar prioridad, el programador puede dar prioridad a otro subproceso del sistema operativo.

```cpp
static void __cdecl Yield();
```

### <a name="remarks"></a>Observaciones

Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada.

## <a name="yieldexecution"></a>YieldExecution

Genera la ejecución para que otro contexto se pueda ejecutar. Si no hay ningún otro contexto disponible para dar prioridad, el programador puede dar prioridad a otro subproceso del sistema operativo.

```cpp
static void __cdecl YieldExecution();
```

### <a name="remarks"></a>Observaciones

Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada.

Esta función es nueva en Visual Studio 2015 y es idéntica a la función [yield](#yield) , pero no entra en conflicto con la macro yield de Windows. h.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Scheduler (clase)](scheduler-class.md)<br/>
[Programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
