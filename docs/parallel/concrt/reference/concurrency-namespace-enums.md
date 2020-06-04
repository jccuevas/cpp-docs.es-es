---
title: concurrency (Enumeraciones del espacio de nombres)
ms.date: 11/04/2016
f1_keywords:
- CONCRT/concurrency::Agents_EventType
- CONCRT/concurrency::Concrt_TraceFlags
- CONCRT/concurrency::CriticalRegionType
- CONCRT/concurrency::PolicyElementKey
- CONCRT/concurrency::SchedulerType
- CONCRT/concurrency::SwitchingProxyState
- CONCRT/concurrency::WinRTInitializationType
- CONCRT/concurrency::join_type
- CONCRT/concurrency::message_status Enumeration
ms.assetid: a40e3b2d-ad21-4229-9880-2cfa84f7ab8f
ms.openlocfilehash: e3a943ed52ce9653086203713bb98331f809314d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372717"
---
# <a name="concurrency-namespace-enums"></a>concurrency (Enumeraciones del espacio de nombres)

||||
|-|-|-|
|[Agents_EventType](#agents_eventtype)|[ConcRT_EventType](#concrt_eventtype)|[Concrt_TraceFlags](#concrt_traceflags)|
|[CriticalRegionType](#criticalregiontype)|[DynamicProgressFeedbackType](#dynamicprogressfeedbacktype)|[PolicyElementKey](#policyelementkey)|
|[SchedulerType](#schedulertype)|[SchedulingProtocolType](#schedulingprotocoltype)|[SwitchingProxyState](#switchingproxystate)|
|[WinRTInitializationType](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|
|[message_status](#message_status)|[task_group_status](#task_group_status)|

## <a name="agent_status-enumeration"></a><a name="agent_status"></a>agent_status (enumeración)

Los estados válidos para un `agent`.

```cpp
enum agent_status;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`agent_canceled`|`agent` se canceló.|
|`agent_created`|Se `agent` ha creado pero no se ha iniciado.|
|`agent_done`|El `agent` terminado sin ser cancelado.|
|`agent_runnable`|Se `agent` ha iniciado, pero `run` no ha entrado en su método.|
|`agent_started`|El `agent` ha empezado.|

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [Agentes asincrónicos](../../../parallel/concrt/asynchronous-agents.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

## <a name="agents_eventtype-enumeration"></a><a name="agents_eventtype"></a>Agents_EventType (enumeración)

Los tipos de eventos a los que se puede realiza un seguimiento utilizando la funcionalidad de seguimiento proporcionada por la Biblioteca de agentes.

```cpp
enum Agents_EventType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`AGENTS_EVENT_CREATE`|Un tipo de evento que representa la creación de un objeto|
|`AGENTS_EVENT_DESTROY`|Un tipo de evento que representa la eliminación de un objeto|
|`AGENTS_EVENT_END`|Un tipo de evento que representa la conclusión de algún procesamiento|
|`AGENTS_EVENT_LINK`|Un tipo de evento que representa la vinculación de bloques de mensajes|
|`AGENTS_EVENT_NAME`|Un tipo de evento que representa el nombre de un objeto|
|`AGENTS_EVENT_SCHEDULE`|Un tipo de evento que representa la programación de un proceso|
|`AGENTS_EVENT_START`|Un tipo de evento que representa el inicio de algún procesamiento|
|`AGENTS_EVENT_UNLINK`|Un tipo de evento que representa la desvinculación de bloques de mensajes|

### <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

## <a name="concrt_eventtype-enumeration"></a><a name="concrt_eventtype"></a>ConcRT_EventType (enumeración)

Los tipos de eventos a los que se puede realizar un seguimiento utilizando la funcionalidad de seguimiento proporcionada por el runtime de simultaneidad.

```cpp
enum ConcRT_EventType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|Un tipo de evento que representa el acto de un adjuntar a un programador.|
|`CONCRT_EVENT_BLOCK`|Tipo de evento que representa el acto de un bloqueo de contexto.|
|`CONCRT_EVENT_DETACH`|Un tipo de evento que representa el acto de una separación de un programador.|
|`CONCRT_EVENT_END`|Un tipo de evento que marca el principio de un par de eventos de inicio y fin.|
|`CONCRT_EVENT_GENERIC`|Tipo de evento utilizado para eventos varios.|
|`CONCRT_EVENT_IDLE`|Tipo de evento que representa el acto de que un contexto se vuelva inactivo.|
|`CONCRT_EVENT_START`|Un tipo de evento que marca el principio de un par de eventos de inicio y fin.|
|`CONCRT_EVENT_UNBLOCK`|Un tipo de evento que representa el acto de desbloquear un contexto.|
|`CONCRT_EVENT_YIELD`|Un tipo de evento que representa el acto de un contexto que produce.|

### <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h **Espacio de nombres:** simultaneidad

## <a name="concrt_traceflags-enumeration"></a><a name="concrt_traceflags"></a>Concrt_TraceFlags (enumeración)

Marcas de seguimiento para los tipos de evento

```cpp
enum Concrt_TraceFlags;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`AgentEventFlag`||
|`AllEventsFlag`||
|`ContextEventFlag`||
|`PPLEventFlag`||
|`ResourceManagerEventFlag`||
|`SchedulerEventFlag`||
|`VirtualProcessorEventFlag`||

### <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

## <a name="criticalregiontype-enumeration"></a><a name="criticalregiontype"></a>CriticalRegionType (enumeración)

El tipo de región crítica dentro del que se encuentra un contexto.

```cpp
enum CriticalRegionType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`InsideCriticalRegion`|Indica que el contexto está dentro de una región crítica. Cuando se encuentra dentro de una región crítica, las suspensiones asincrónicas se ocultan del programador. Si se produce una suspensión de este tipo, Resource Manager esperará a que el subproceso se pueda ejecutar y simplemente lo reanudará en lugar de volver a invocar el programador. Las cerraduras tomadas dentro de una región de este tipo deben ser tomadas con extremo cuidado.|
|`InsideHyperCriticalRegion`|Indica que el contexto está dentro de una región hipercrítica. Cuando se encuentra dentro de una región hipercrítica, las suspensiones sincrónicas y asincrónicas se ocultan del programador. Si se produce una suspensión o un bloqueo de este tipo, el administrador de recursos esperará a que el subproceso se pueda ejecutar y simplemente lo reanudará en lugar de invocar al programador de nuevo. Los bloqueos tomados dentro de una región de este tipo nunca deben compartirse con código que se ejecute fuera de una región de este tipo. Si lo hace, se producirá un interbloqueo impredecible.|
|`OutsideCriticalRegion`|Indica que el contexto está fuera de cualquier región crítica.|

### <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

## <a name="dynamicprogressfeedbacktype-enumeration"></a><a name="dynamicprogressfeedbacktype"></a>DinámicaProgressFeedbackType (enumeración)

La usa la directiva `DynamicProgressFeedback` para describir si los recursos para el programador se volverán a equilibrar según la información estadística recopilada desde el programador, o únicamente se basarán en procesadores virtuales que entran y salen del estado de inactividad a través de llamadas a los métodos `Activate` y `Deactivate` en la interfaz `IVirtualProcessorRoot`. Para obtener más información sobre las directivas de programador disponibles, vea [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`ProgressFeedbackDisabled`|El programador no recopila información de progreso. El reequilibrio se realiza basándose únicamente en el nivel de suscripción del subproceso de hardware subyacente. Para obtener más información sobre los niveles de suscripción, vea [IExecutionResource::CurrentSubscriptionLevel](IExecutionResource-structure.md).<br /><br /> Este valor está reservado para su uso por el tiempo de ejecución.|
|`ProgressFeedbackEnabled`|El programador recopila información de progreso y la pasa al administrador de recursos. El administrador de recursos utilizará esta información estadística para reequilibrar los recursos en nombre del programador, además del nivel de suscripción del subproceso de hardware subyacente. Para obtener más información sobre los niveles de suscripción, vea [IExecutionResource::CurrentSubscriptionLevel](IExecutionResource-structure.md).|

## <a name="join_type-enumeration"></a><a name="join_type"></a>join_type (enumeración)

El tipo de un bloque de mensajería `join`.

```cpp
enum join_type;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`greedy`|Los `join` bloques de mensajería codiciosos aceptan inmediatamente un mensaje tras la propagación. Esto es más eficiente, pero tiene la posibilidad de live-lock, dependiendo de la configuración de red.|
|`non_greedy`|Los bloques `join` de mensajes no expansivos posponen los mensajes e intentan consumirlos después de que todos hayan llegado. Se garantiza que funcionan, pero más lentos.|

### <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

## <a name="message_status-enumeration"></a><a name="message_status"></a>message_status Enumeración

Las respuestas válidas para una oferta de un objeto `message` a un bloque.

```cpp
enum message_status;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`accepted`|El destino aceptó el mensaje.|
|`declined`|El destino no aceptó el mensaje.|
|`missed`|El destino intentó aceptar el mensaje, pero ya no estaba disponible.|
|`postponed`|El objetivo pospuso el mensaje.|

### <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

## <a name="policyelementkey-enumeration"></a><a name="policyelementkey"></a>PolicyElementKey (enumeración)

Claves de directiva que describen aspectos de comportamiento del programador. Cada elemento de directiva se describe mediante un par clave-valor. Para obtener más información acerca de las directivas del programador y su impacto en los programadores, vea [Programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

```cpp
enum PolicyElementKey;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`ContextPriority`|La prioridad de subproceso del sistema operativo de cada contexto en el programador. Si esta clave se `INHERIT_THREAD_PRIORITY` establece en el valor, los contextos del programador heredarán la prioridad del subproceso que creó el programador.<br /><br /> Valores válidos : Cualquiera de `SetThreadPriority` los valores válidos para la función de Windows y el valor especial`INHERIT_THREAD_PRIORITY`<br /><br /> Valor predeterminado :`THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|El tamaño de pila reservado de cada contexto en el programador en kilobytes.<br /><br /> Valores válidos : Enteros positivos<br /><br /> Valor predeterminado `0`: , que indica que se utilizará el valor predeterminado del proceso para el tamaño de pila.|
|`DynamicProgressFeedback`|Determina si los recursos del programador se reequilibrarán según la información estadística recopilada del programador o solo en función del nivel de suscripción de los subprocesos de hardware subyacentes. Para obtener más información, vea [DynamicProgressFeedbackType](#dynamicprogressfeedbacktype).<br /><br /> Valores válidos : `DynamicProgressFeedbackType` Un miembro `ProgressFeedbackEnabled` de la enumeración, o o`ProgressFeedbackDisabled`<br /><br /> Valor predeterminado :`ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|Cuando `SchedulingProtocol` la clave de directiva `EnhanceScheduleGroupLocality`se establece en el valor, se especifica el número máximo de contextos que se pueden ejecutar en las que se puede almacenar en caché por las colas locales del procesador virtual. Estos contextos normalmente se ejecutarán en orden de último en entrar primero en salir (LIFO) en el procesador virtual que hizo que se ejecutaran. Tenga en cuenta que esta `SchedulingProtocol` clave de directiva `EnhanceForwardProgress`no tiene ningún significado cuando la clave se establece en el valor .<br /><br /> Valores válidos : Enteros no negativos<br /><br /> Valor predeterminado :`8`|
|`MaxConcurrency`|El nivel máximo de simultaneidad deseado por el programador. El administrador de recursos intentará asignar inicialmente tantos procesadores virtuales. El valor especial [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) indica que el nivel de simultaneidad deseado es el mismo que el número de subprocesos de hardware en el equipo. Si el valor `MinConcurrency` especificado para es mayor que el `MaxConcurrency` número de `MaxExecutionResources`subprocesos de `MaxConcurrency` hardware en el equipo `MinConcurrency`y se especifica como , el valor para se genera para que coincida con lo establecido para .<br /><br /> Valores válidos : Enteros positivos y el valor especial`MaxExecutionResources`<br /><br /> Valor predeterminado :`MaxExecutionResources`|
|`MaxPolicyElementKey`|La clave de elemento de política máxima. No es una clave de elemento válida.|
|`MinConcurrency`|El nivel de simultaneidad mínimo que debe proporcionar el administrador de recursos debe proporcionar al programador. El número de procesadores virtuales asignados a un programador nunca será inferior al mínimo. El valor especial [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) indica que el nivel de simultaneidad mínimo es el mismo que el número de subprocesos de hardware en el equipo. Si el valor `MaxConcurrency` especificado para es menor que el `MinConcurrency` número de `MaxExecutionResources`subprocesos de `MinConcurrency` hardware en el equipo `MaxConcurrency`y se especifica como , el valor para se reduce para que coincida con lo establecido para .<br /><br /> Valores válidos : Enteros no negativos y el valor `MaxExecutionResources`especial . Tenga en cuenta que para las directivas de programador `0` utilizadas para la construcción de programadores de Tiempo de ejecución de simultaneidad, el valor no es válido.<br /><br /> Valor predeterminado :`1`|
|`SchedulerKind`|El tipo de subprocesos que el programador utilizará para los contextos de ejecución subyacentes. Para obtener más información, vea [SchedulerType](#schedulertype).<br /><br /> Valores válidos : `SchedulerType` Un miembro de la enumeración, por ejemplo,`ThreadScheduler`<br /><br /> Valor predeterminado `ThreadScheduler`: . Esto se traduce en subprocesos Win32 en todos los sistemas operativos.|
|`SchedulingProtocol`|Describe qué algoritmo de programación utilizará el programador. Para obtener más información, vea [SchedulingProtocolType](#schedulingprotocoltype).<br /><br /> Valores válidos : `SchedulingProtocolType` Un miembro `EnhanceScheduleGroupLocality` de la enumeración, o o`EnhanceForwardProgress`<br /><br /> Valor predeterminado :`EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|Número provisional de procesadores virtuales por subproceso de hardware. El Factor de sobresuscripción de destino puede aumentarlo `MaxConcurrency` el Administrador de recursos, si es necesario, para satisfacerlos con los subprocesos de hardware del equipo.<br /><br /> Valores válidos : Enteros positivos<br /><br /> Valor predeterminado :`1`|
|`WinRTInitialization`||

### <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

## <a name="schedulertype-enumeration"></a><a name="schedulertype"></a>SchedulerType (enumeración)

Utilizado por la directiva `SchedulerKind` para describir el tipo de subprocesos que el programador debería usar para contextos de ejecución subyacentes. Para obtener más información sobre las directivas de programador disponibles, vea [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum SchedulerType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`ThreadScheduler`|Indica una solicitud explícita de subprocesos Win32 normales.|
|`UmsThreadDefault`|Los subprocesos programables en modo de usuario (UMS) no se admiten en el Runtime de simultaneidad en Visual Studio 2013. Usando `UmsThreadDefault` como valor de la directiva `SchedulerType` no se producirá un error. Sin embargo, un programador creado con esa directiva establecerá el uso de subprocesos Win32 como valor predeterminado.|

### <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

## <a name="schedulingprotocoltype-enumeration"></a><a name="schedulingprotocoltype"></a>SchedulingProtocolType (enumeración)

La usa la directiva `SchedulingProtocol` para describir el algoritmo de programación que utilizará el programador. Para obtener más información sobre las directivas de programador disponibles, vea [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum SchedulingProtocolType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`EnhanceForwardProgress`|El programador prefiere repasar a través de grupos de programación después de ejecutar cada tarea. Los contextos desbloqueados normalmente se programan de forma primero en entrar primero en salir (FIFO). Los procesadores virtuales no almacenan en caché contextos desbloqueados.|
|`EnhanceScheduleGroupLocality`|El programador prefiere seguir trabajando en tareas dentro del grupo de programación actual antes de pasar a otro grupo de programación. Los contextos desbloqueados se almacenan en caché por procesador virtual y normalmente se programan de forma de última entrada y salida (LIFO) por el procesador virtual que los desbloquea.|

### <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

## <a name="switchingproxystate-enumeration"></a><a name="switchingproxystate"></a>SwitchingProxyState (enumeración)

Se usa para denotar el estado en el que se encuentra un proxy del subproceso, cuando se ejecuta un cambio de contexto cooperativo en un proxy del subproceso diferente.

```cpp
enum SwitchingProxyState;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`Blocking`|Indica que el subproceso de llamada se bloquea de forma cooperativa y debe ser propiedad exclusiva del autor de la llamada hasta que se vuelva a ejecutar posteriormente y realice otra acción.|
|`Idle`|Indica que el programador ya no necesita el subproceso que realiza la llamada y se devuelve al Administrador de recursos. El contexto que se estaba distribuyendo ya no puede ser utilizado por el Administrador de recursos.|
|`Nesting`|Indica que el subproceso de llamada está anidando un programador secundario y es necesario por el autor de la llamada, para adjuntar a un programador diferente.|

### <a name="remarks"></a>Observaciones

Un parámetro `SwitchingProxyState` de tipo se `IThreadProxy::SwitchTo` pasa al método para indicar al Administrador de recursos cómo tratar el proxy de subproceso que realiza la llamada.

Para obtener más información sobre cómo se usa este tipo, vea [IThreadProxy::SwitchTo](ithreadproxy-structure.md#switchto).

## <a name="task_group_status-enumeration"></a><a name="task_group_status"></a>task_group_status (enumeración)

Describe el estado de ejecución de un objeto `task_group` o `structured_task_group`. Numeroso métodos que esperan tareas programadas para que se complete un grupo de tareas, devuelven un valor de este tipo.

```cpp
enum task_group_status;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`canceled`|El objeto `task_group` o `structured_task_group` se canceló. Puede que una o varias tareas no se hayan ejecutado.|
|`completed`|Las tareas puestas en cola en el objeto `task_group` o `structured_task_group` se han completado correctamente.|
|`not_complete`|Las tareas puestas en cola en el objeto `task_group` no se han completado. Observe que el runtime de simultaneidad no devuelve actualmente este valor.|

### <a name="requirements"></a>Requisitos

**Encabezado:** pplinterface.h

## <a name="winrtinitializationtype-enumeration"></a><a name="winrtinitializationtype"></a>Enumeración WinRTInitializationType

La utiliza la directiva `WinRTInitialization` para describir si se iniciará y cómo se iniciará Windows Runtime en subprocesos del programador para una aplicación que se ejecuta en sistemas operativos con Windows 8 o una versión posterior. Para obtener más información sobre las directivas de programador disponibles, vea [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum WinRTInitializationType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`DoNotInitializeWinRT`|Cuando la aplicación se ejecuta en los sistemas operativos con Windows 8 o una versión posterior, los subprocesos dentro del programador no se inicializarán en Windows Runtime.|
|`InitializeWinRTAsMTA`|Cuando la aplicación se ejecuta en los sistemas operativos con Windows 8 o una versión posterior, cada subproceso del programador se inicializará en Windows en tiempo de ejecución y declarará que forma parte del apartamento multiproceso.|

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)
