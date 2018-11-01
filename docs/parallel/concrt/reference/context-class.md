---
title: Context (Clase)
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
ms.openlocfilehash: c6b219eabd008114f40401c64465e44607c2ee9b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555082"
---
# <a name="context-class"></a>Context (Clase)

Representa una abstracción para un contexto de ejecución.

## <a name="syntax"></a>Sintaxis

```
class Context;
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Name|Descripción|
|----------|-----------------|
|[~ Context (destructor)](#dtor)||

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[Bloque](#block)|Bloquea el contexto actual.|
|[CurrentContext](#currentcontext)|Devuelve un puntero al contexto actual.|
|[GetId](#getid)|Devuelve un identificador para el contexto que es único dentro del programador al que pertenece el contexto.|
|[GetScheduleGroupId](#getschedulegroupid)|Devuelve un identificador para el grupo de programación en el que el contexto está trabajando actualmente.|
|[GetVirtualProcessorId](#getvirtualprocessorid)|Devuelve un identificador para el procesador virtual en el que el contexto se está ejecutando actualmente.|
|[Id.](#id)|Devuelve un identificador para el contexto actual que es único dentro del programador al que pertenece el contexto actual.|
|[IsCurrentTaskCollectionCanceling](#iscurrenttaskcollectioncanceling)|Devuelve una indicación de si la colección de tareas que actualmente se ejecuta alineada en el contexto actual, está en medio de una cancelación activa (o lo estará pronto).|
|[IsSynchronouslyBlocked](#issynchronouslyblocked)|Determina si el contexto está o no bloqueado de forma sincrónica. Se considera que un contexto está bloqueado de forma sincrónica si realizó una acción que condujo al bloqueo explícitamente.|
|[Saturar](#oversubscribe)|Inserta un procesador virtual adicional en un programador para la duración de un bloque de código cuando se invoca en un contexto que se ejecuta en uno de los procesadores virtuales de ese programador.|
|[ScheduleGroupId](#schedulegroupid)|Devuelve un identificador para el grupo de programación en el que el contexto actual está trabajando.|
|[Desbloquear](#unblock)|Desbloquea el contexto y hace que se convierta en ejecutable.|
|[VirtualProcessorId](#virtualprocessorid)|Devuelve un identificador para el procesador virtual en el que el contexto actual se está ejecutando.|
|[Yield](#yield)|Genera la ejecución para que otro contexto se pueda ejecutar. Si no hay ningún otro contexto disponible para dar prioridad, el programador puede dar prioridad a otro subproceso del sistema operativo.|

## <a name="remarks"></a>Comentarios

El programador del Runtime de simultaneidad (vea [programador](scheduler-class.md)) usa contextos de ejecución para ejecutar el trabajo de cola para su aplicación. Un subproceso de Win32 es un ejemplo de un contexto de ejecución en un sistema operativo Windows.

En cualquier momento, el nivel de simultaneidad de un programador es igual al número de procesadores virtuales que le ha concedido el Administrador de recursos. Un procesador virtual es una abstracción para un recurso de procesamiento y se asigna a un subproceso del hardware en el sistema subyacente. Solo se puede ejecutar un único contexto del programador en un procesador virtual a una hora determinada.

El programador es cooperativo por su naturaleza y un contexto de ejecución puede producir su procesador virtual en un contexto diferente en cualquier momento si desea escribir un estado de espera. Cuando la espera se cumple, no se puede volver a reanudar hasta que un procesador virtual disponible del programador comienza su ejecución.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Context`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

**Espacio de nombres:** simultaneidad

##  <a name="block"></a> Bloque

Bloquea el contexto actual.

```
static void __cdecl Block();
```

### <a name="remarks"></a>Comentarios

Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada.

Si el contexto de llamada se ejecuta en un procesador virtual, el procesador virtual encontrará otro contexto ejecutable para ejecutar o potencialmente puede crear uno nuevo.

Después de la `Block` método se llamará o se ha llamado a, debe emparejarlo con una llamada a la [desbloquear](#unblock) método desde otro contexto de ejecución en el fin de volver a ejecutar. Tenga en cuenta que hay un período crítico entre el punto donde el código publica su contexto para que otro subproceso poder llamar a la `Unblock` método y el punto donde el método real llamada a `Block` se realiza. Durante este período, no debe llamar a cualquier método que a su vez puede bloquear y desbloquear por sus propios motivos (por ejemplo, si se adquiere un bloqueo). Las llamadas a la `Block` y `Unblock` método no realiza el seguimiento de la razón para el bloqueo y desbloqueo. Un solo objeto debe tener la propiedad de un `Block` -  `Unblock` par.

Este método puede producir una variedad de excepciones, incluidas [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md).

##  <a name="dtor"></a> ~Context

```
virtual ~Context();
```

##  <a name="currentcontext"></a> CurrentContext

Devuelve un puntero al contexto actual.

```
static Context* __cdecl CurrentContext();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al contexto actual.

### <a name="remarks"></a>Comentarios

Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada.

##  <a name="getid"></a> GetId

Devuelve un identificador para el contexto que es único dentro del programador al que pertenece el contexto.

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Un identificador para el contexto que es único dentro del programador al que pertenece el contexto.

##  <a name="getschedulegroupid"></a> GetScheduleGroupId

Devuelve un identificador para el grupo de programación en el que el contexto está trabajando actualmente.

```
virtual unsigned int GetScheduleGroupId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Un identificador para el contexto está trabajando actualmente en el grupo de programación.

### <a name="remarks"></a>Comentarios

El valor devuelto de este método es un muestreo instantáneo del grupo de programación que se está ejecutando el contexto. Si se llama a este método en un contexto distinto del contexto actual, el valor puede ser obsoleto el momento en que se devuelve y no es confiable. Normalmente, este método se usa para depurar o solo con fines de seguimiento.

##  <a name="getvirtualprocessorid"></a> GetVirtualProcessorId

Devuelve un identificador para el procesador virtual en el que el contexto se está ejecutando actualmente.

```
virtual unsigned int GetVirtualProcessorId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Si el contexto se está ejecutando en un procesador virtual, un identificador para el procesador virtual que el contexto se está ejecutando actualmente; en caso contrario, el valor `-1`.

### <a name="remarks"></a>Comentarios

El valor devuelto de este método es un muestreo instantáneo del procesador virtual que se está ejecutando el contexto. Este valor puede ser obsoleto en el momento en que se devuelve y no es confiable. Normalmente, este método se usa para depurar o solo con fines de seguimiento.

##  <a name="id"></a> Id.

Devuelve un identificador para el contexto actual que es único dentro del programador al que pertenece el contexto actual.

```
static unsigned int __cdecl Id();
```

### <a name="return-value"></a>Valor devuelto

Si el contexto actual está asociado a un programador, un identificador para el contexto actual que es único dentro del programador al que pertenece el contexto actual; en caso contrario, el valor `-1`.

##  <a name="iscurrenttaskcollectioncanceling"></a> IsCurrentTaskCollectionCanceling

Devuelve una indicación de si la colección de tareas que actualmente se ejecuta alineada en el contexto actual, está en medio de una cancelación activa (o lo estará pronto).

```
static bool __cdecl IsCurrentTaskCollectionCanceling();
```

### <a name="return-value"></a>Valor devuelto

Si un programador se adjunta al contexto de llamada y un grupo de tareas ejecuta una tarea insertada en ese contexto, una indicación de si ese grupo de tareas está en medio de una cancelación activa (o estará pronto); en caso contrario, el valor `false`.

##  <a name="issynchronouslyblocked"></a> IsSynchronouslyBlocked

Determina si el contexto está o no bloqueado de forma sincrónica. Se considera que un contexto está bloqueado de forma sincrónica si realizó una acción que condujo al bloqueo explícitamente.

```
virtual bool IsSynchronouslyBlocked() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Si el contexto está bloqueado de forma sincrónica.

### <a name="remarks"></a>Comentarios

Se considera que un contexto está bloqueado de forma sincrónica si realizó una acción que condujo al bloqueo explícitamente. En el programador de subproceso, esto indicaría una llamada directa a la `Context::Block` método o un objeto de sincronización que se creó mediante el `Context::Block` método.

El valor devuelto de este método es un muestreo instantáneo de si el contexto está bloqueado de forma sincrónica. Este valor puede estar obsoleto en el momento en que se devuelve y sólo puede utilizarse en circunstancias muy específicas.

##  <a name="operator_delete"></a> operador delete

Un `Context` objeto sea destruido internamente por el tiempo de ejecución. Se puede no se puede eliminar explícitamente.

```
void operator delete(void* _PObject);
```

### <a name="parameters"></a>Parámetros

*_PObject*<br/>
Un puntero al objeto que se va a eliminar.

##  <a name="oversubscribe"></a> Saturar

Inserta un procesador virtual adicional en un programador para la duración de un bloque de código cuando se invoca en un contexto que se ejecuta en uno de los procesadores virtuales de ese programador.

```
static void __cdecl Oversubscribe(bool _BeginOversubscription);
```

### <a name="parameters"></a>Parámetros

*_BeginOversubscription*<br/>
Si **true**, un valor que indica que se debe agregar un procesador virtual adicional para la duración de la suscripción excesiva. Si **false**, una indicación de que debe finalizar la suscripción excesiva y se debe quitar el procesador virtual se ha agregado anteriormente.

##  <a name="schedulegroupid"></a> ScheduleGroupId

Devuelve un identificador para el grupo de programación en el que el contexto actual está trabajando.

```
static unsigned int __cdecl ScheduleGroupId();
```

### <a name="return-value"></a>Valor devuelto

Si el contexto actual se adjunta a un programador y trabaja en un grupo de programación, un identificador para el programador de grupo que el contexto actual está trabajando; en caso contrario, el valor `-1`.

##  <a name="unblock"></a> Desbloquear

Desbloquea el contexto y hace que se convierta en ejecutable.

```
virtual void Unblock() = 0;
```

### <a name="remarks"></a>Comentarios

Es perfectamente válido para una llamada a la `Unblock` método llegue antes que una llamada correspondiente a la [bloque](#block) método. Siempre que las llamadas a la `Block` y `Unblock` métodos están emparejados correctamente, el tiempo de ejecución controla correctamente la carrera natural de cualquier orden. Un `Unblock` llamada recupera antes un `Block` llamada simplemente anula el efecto de la `Block` llamar.

Hay varias excepciones que se pueden iniciar desde este método. Si un contexto intenta llamar a la `Unblock` método en sí mismo, un [context_self_unblock](context-self-unblock-class.md) se producirá la excepción. Si las llamadas a `Block` y `Unblock` no están emparejados correctamente (por ejemplo, dos llamadas a `Unblock` se llevan a cabo un contexto que se está ejecutando actualmente), un [context_unblock_unbalanced](context-unblock-unbalanced-class.md) se producirá la excepción.

Tenga en cuenta que hay un período crítico entre el punto donde el código publica su contexto para que otro subproceso poder llamar a la `Unblock` método y el punto donde el método real llamada a `Block` se realiza. Durante este período, no debe llamar a cualquier método que a su vez puede bloquear y desbloquear por sus propios motivos (por ejemplo, si se adquiere un bloqueo). Las llamadas a la `Block` y `Unblock` método no realiza el seguimiento de la razón para el bloqueo y desbloqueo. Un solo objeto debe tener la propiedad de un `Block` y `Unblock` par.

##  <a name="virtualprocessorid"></a> VirtualProcessorId

Devuelve un identificador para el procesador virtual en el que el contexto actual se está ejecutando.

```
static unsigned int __cdecl VirtualProcessorId();
```

### <a name="return-value"></a>Valor devuelto

Si el contexto actual se adjunta a un programador, un identificador para el procesador virtual que se está ejecutando el contexto actual; en caso contrario, el valor `-1`.

### <a name="remarks"></a>Comentarios

El valor devuelto de este método es un muestreo instantáneo del procesador virtual que se está ejecutando el contexto actual. Este valor puede ser obsoleto en el momento en que se devuelve y no es confiable. Normalmente, este método se usa para depurar o solo con fines de seguimiento.

##  <a name="yield"></a> yield

Genera la ejecución para que otro contexto se pueda ejecutar. Si no hay ningún otro contexto disponible para dar prioridad, el programador puede dar prioridad a otro subproceso del sistema operativo.

```
static void __cdecl Yield();
```

### <a name="remarks"></a>Comentarios

Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada.

##  <a name="yieldexecution"></a> YieldExecution

Genera la ejecución para que otro contexto se pueda ejecutar. Si no hay ningún otro contexto disponible para dar prioridad, el programador puede dar prioridad a otro subproceso del sistema operativo.

```
static void __cdecl YieldExecution();
```

### <a name="remarks"></a>Comentarios

Este método hará que se cree el programador predeterminado del proceso y se adjunte al contexto de la llamada si no hay ningún programador asociado actualmente con el contexto de la llamada.

Esta función es nueva en Visual Studio 2015 y es idéntica a la [Yield](#yield) funcionando, pero no entre en conflicto con la macro Yield en Windows.h.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Scheduler (clase)](scheduler-class.md)<br/>
[Programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)

