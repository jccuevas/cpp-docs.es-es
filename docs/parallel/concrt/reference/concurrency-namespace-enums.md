---
title: enumeraciones del espacio de nombres de simultaneidad
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
ms.openlocfilehash: 97d2e9fd8e64475d9194bb8b2ab12fdee315e176
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677349"
---
# <a name="concurrency-namespace-enums"></a>enumeraciones del espacio de nombres de simultaneidad

||||
|-|-|-|
|[Agents_EventType](#agents_eventtype)|[ConcRT_EventType](#concrt_eventtype)|[Concrt_TraceFlags](#concrt_traceflags)|
|[CriticalRegionType](#criticalregiontype)|[DynamicProgressFeedbackType](#dynamicprogressfeedbacktype)|[PolicyElementKey](#policyelementkey)|
|[SchedulerType](#schedulertype)|[SchedulingProtocolType](#schedulingprotocoltype)|[SwitchingProxyState](#switchingproxystate)|
|[WinRTInitializationType](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|
|[message_status](#message_status)|[task_group_status](#task_group_status)|

##  <a name="agent_status"></a>  agent_status (enumeración)

Los estados válidos para un `agent`.

```
enum agent_status;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`agent_canceled`|`agent` se canceló.|
|`agent_created`|El `agent` se ha creado pero no ha iniciado.|
|`agent_done`|El `agent` ha finalizado sin que se va a cancelar.|
|`agent_runnable`|El `agent` se ha iniciado, pero no se ha introducido su `run` método.|
|`agent_started`|El `agent` se ha iniciado.|

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [agentes asincrónicos](../../../parallel/concrt/asynchronous-agents.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

##  <a name="agents_eventtype"></a>  Agents_EventType (enumeración)

Los tipos de eventos a los que se puede realiza un seguimiento utilizando la funcionalidad de seguimiento proporcionada por la Biblioteca de agentes.

```
enum Agents_EventType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`AGENTS_EVENT_CREATE`|Un tipo de evento que representa la creación de un objeto|
|`AGENTS_EVENT_DESTROY`|Un tipo de evento que representa la eliminación de un objeto|
|`AGENTS_EVENT_END`|Procesamiento de un tipo de evento que representa la conclusión de algunas|
|`AGENTS_EVENT_LINK`|Un tipo de evento que representa la vinculación de bloques de mensajes|
|`AGENTS_EVENT_NAME`|Un tipo de evento que representa el nombre de un objeto|
|`AGENTS_EVENT_SCHEDULE`|Un tipo de evento que representa la programación de un proceso|
|`AGENTS_EVENT_START`|Procesamiento de un tipo de evento que representa el inicio de algunas|
|`AGENTS_EVENT_UNLINK`|Un tipo de evento que representa la desvinculación de bloques de mensajes|

### <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

##  <a name="concrt_eventtype"></a>  ConcRT_EventType (enumeración)

Los tipos de eventos a los que se puede realizar un seguimiento utilizando la funcionalidad de seguimiento proporcionada por el runtime de simultaneidad.

```
enum ConcRT_EventType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|Un tipo de evento que representa la acción de una asociación a un programador.|
|`CONCRT_EVENT_BLOCK`|Un tipo de evento que representa la acción de un bloqueo de contexto.|
|`CONCRT_EVENT_DETACH`|Un tipo de evento que representa la acción de desasociarse de un programador.|
|`CONCRT_EVENT_END`|Un tipo de evento que marca el principio de un par de eventos de inicio y fin.|
|`CONCRT_EVENT_GENERIC`|Un tipo de evento usado para varios eventos.|
|`CONCRT_EVENT_IDLE`|Un tipo de evento que representa la acción de un contexto que se vuelvan inactivas.|
|`CONCRT_EVENT_START`|Un tipo de evento que marca el principio de un par de eventos de inicio y fin.|
|`CONCRT_EVENT_UNBLOCK`|Un tipo de evento que representa la acción de desbloquear un contexto.|
|`CONCRT_EVENT_YIELD`|Un tipo de evento que representa la acción de obtención de un contexto.|

### <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h **Namespace:** simultaneidad

##  <a name="concrt_traceflags"></a>  Concrt_TraceFlags (enumeración)

Marcas de seguimiento para los tipos de evento

```
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

##  <a name="criticalregiontype"></a>  CriticalRegionType (enumeración)

El tipo de región crítica dentro del que se encuentra un contexto.

```
enum CriticalRegionType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`InsideCriticalRegion`|Indica que el contexto está dentro de una región crítica. Dentro de una región crítica, las suspensiones asincrónicas se ocultan del programador. Debe ocurrir una suspensión, el Administrador de recursos esperará a que el subproceso se convierta en ejecutable y simplemente se reanudará en lugar de invocar el programador de nuevo. Los bloqueos tomados dentro de este tipo de región deben realizarse con extremo cuidado.|
|`InsideHyperCriticalRegion`|Indica que el contexto está dentro de una región hyper crítica. Dentro de una región crítica hyper, suspensiones sincrónicas y asincrónicas se ocultan del programador. Debe una suspensión o de bloqueo se producen, el Administrador de recursos esperará a que el subproceso se convierta en ejecutable y simplemente se reanudará en lugar de invocar al programador de nuevo. Bloqueos tomados dentro de este tipo de región nunca deben compartirse con código que se ejecuta fuera de este tipo de región. Si lo hace, provocará un interbloqueo impredecible.|
|`OutsideCriticalRegion`|Indica que el contexto está fuera de cualquier región crítica.|

### <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

##  <a name="dynamicprogressfeedbacktype"></a>  DynamicProgressFeedbackType (enumeración)

La usa la directiva `DynamicProgressFeedback` para describir si los recursos para el programador se volverán a equilibrar según la información estadística recopilada desde el programador, o únicamente se basarán en procesadores virtuales que entran y salen del estado de inactividad a través de llamadas a los métodos `Activate` y `Deactivate` en la interfaz `IVirtualProcessorRoot`. Para obtener más información sobre las directivas del programador disponibles, vea [PolicyElementKey](concurrency-namespace-enums.md).

```
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`ProgressFeedbackDisabled`|El programador no recopila información de progreso. Reequilibrio se realiza basándose únicamente en el nivel de suscripción del subproceso de hardware subyacente. Para obtener más información sobre los niveles de suscripción, consulte [IExecutionResource:: CurrentSubscriptionLevel](IExecutionResource-structure.md).<br /><br /> Este valor está reservado para su uso por el tiempo de ejecución.|
|`ProgressFeedbackEnabled`|El programador recopila información de progreso y lo pasa al administrador de recursos. El Administrador de recursos usará esta información estadística para volver a equilibrar los recursos en nombre del programador además del nivel de suscripción de subproceso de hardware subyacente. Para obtener más información sobre los niveles de suscripción, consulte [IExecutionResource:: CurrentSubscriptionLevel](IExecutionResource-structure.md).|
##  <a name="join_type"></a>  join_type (enumeración)

El tipo de un bloque de mensajería `join`.

```
enum join_type;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`greedy`|Expansiva `join` bloques de mensajería aceptan inmediatamente un mensaje en la propagación. Esto es más eficaz, pero tiene la posibilidad de un bloqueo activo, según la configuración de red.|
|`non_greedy`|No expansivo `join` bloques de mensajería posponer mensajes e intentará consumen después de haber llegado todos. Estos se garantiza que funcionen, pero más lentamente.|

### <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

##  <a name="message_status"></a>  message_status (enumeración)

Las respuestas válidas para una oferta de un objeto `message` a un bloque.

```
enum message_status;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`accepted`|El destino aceptó el mensaje.|
|`declined`|El destino no aceptó el mensaje.|
|`missed`|El destino intentó aceptar el mensaje, pero ya no estaba disponible.|
|`postponed`|El destino pospone el mensaje.|

### <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

##  <a name="policyelementkey"></a>  PolicyElementKey (enumeración)

Claves de directiva que describen aspectos de comportamiento del programador. Cada elemento de directiva se describe mediante un par clave-valor. Para obtener más información sobre las directivas del programador y su impacto en los programadores, vea [programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

```
enum PolicyElementKey;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`ContextPriority`|La prioridad del subproceso del sistema operativo de cada contexto en el programador. Si esta clave se establece en el valor `INHERIT_THREAD_PRIORITY` los contextos en el programador heredarán la prioridad del subproceso que creó el programador.<br /><br /> Los valores válidos: cualquiera de los valores válidos para el Windows `SetThreadPriority` función y el valor especial `INHERIT_THREAD_PRIORITY`<br /><br /> Valor predeterminado: `THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|El tamaño de pila reservado de cada contexto en el programador en kilobytes.<br /><br /> Los valores válidos: enteros positivos<br /><br /> Valor predeterminado: `0`, que indica que se utiliza el valor predeterminado de la variable del proceso para el tamaño de la pila.|
|`DynamicProgressFeedback`|Determina si los recursos para el programador se volverán a equilibrar según la información estadística recopilada desde el programador o solo en función del nivel de suscripción de subprocesos de hardware subyacentes. Para obtener más información, consulte [DynamicProgressFeedbackType](#dynamicprogressfeedbacktype).<br /><br /> Los valores válidos: un miembro de la `DynamicProgressFeedbackType` enumeración, ya sea `ProgressFeedbackEnabled` o `ProgressFeedbackDisabled`<br /><br /> Valor predeterminado: `ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|Cuando el `SchedulingProtocol` clave de la directiva se establece en el valor `EnhanceScheduleGroupLocality`, esta propiedad especifica el número máximo de contextos ejecutables que pueden almacenarse en caché por colas locales de procesador virtual. Estos contextos generalmente se ejecutarán en orden de último en el primero en salir (LIFO) en el procesador virtual que provocó que se convierta en ejecutable. Tenga en cuenta que esta clave de directiva no tiene ningún significado cuando la `SchedulingProtocol` clave se establece en el valor `EnhanceForwardProgress`.<br /><br /> Los valores válidos: enteros no negativos<br /><br /> Valor predeterminado: `8`|
|`MaxConcurrency`|La simultaneidad máxima nivel deseada por el programador. El Administrador de recursos intentará asignar inicialmente el siguiente número de procesadores virtuales. El valor especial [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) indica que el nivel de simultaneidad deseado es igual que el número de subprocesos de hardware en el equipo. Si el valor especificado para `MinConcurrency` es mayor que el número de subprocesos de hardware en el equipo y `MaxConcurrency` se especifica como `MaxExecutionResources`, el valor de `MaxConcurrency` se genera para que coincida con lo que se establece para `MinConcurrency`.<br /><br /> Los valores válidos: enteros positivos y el valor especial `MaxExecutionResources`<br /><br /> Valor predeterminado: `MaxExecutionResources`|
|`MaxPolicyElementKey`|La clave de elemento de directiva máxima. No es una clave de elemento válido.|
|`MinConcurrency`|El nivel de simultaneidad mínimo que debe proporcionarse al programador mediante el Administrador de recursos. El número de procesadores virtuales asignados a un programador nunca pasará por debajo del mínimo. El valor especial [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) indica que el nivel de simultaneidad mínimo es igual que el número de subprocesos de hardware en el equipo. Si el valor especificado para `MaxConcurrency` es menor que el número de subprocesos de hardware en el equipo y `MinConcurrency` se especifica como `MaxExecutionResources`, el valor de `MinConcurrency` se reduce para que coincida con lo que se establece para `MaxConcurrency`.<br /><br /> Los valores válidos: enteros no negativos y el valor especial `MaxExecutionResources`. Tenga en cuenta que las directivas de programador utilizadas para la construcción de los programadores del Runtime de simultaneidad, el valor de `0` no es válido.<br /><br /> Valor predeterminado: `1`|
|`SchedulerKind`|El tipo de subprocesos que el programador se utilizará para contextos de ejecución subyacentes. Para obtener más información, consulte [SchedulerType](#schedulertype).<br /><br /> Los valores válidos: un miembro de la `SchedulerType` enumeración, por ejemplo, `ThreadScheduler`<br /><br /> Valor predeterminado: `ThreadScheduler`. Esto se traduce en subprocesos de Win32 en todos los sistemas operativos.|
|`SchedulingProtocol`|Describe el algoritmo de programación que se usará en el programador. Para obtener más información, consulte [SchedulingProtocolType](#schedulingprotocoltype).<br /><br /> Los valores válidos: un miembro de la `SchedulingProtocolType` enumeración, ya sea `EnhanceScheduleGroupLocality` o `EnhanceForwardProgress`<br /><br /> Valor predeterminado: `EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|Número de procesadores virtuales por subproceso de hardware provisional. El factor de la suscripción excesiva puede aumentarse el Administrador de recursos, si es necesario, para satisfacer `MaxConcurrency` con los subprocesos de hardware en el equipo.<br /><br /> Los valores válidos: enteros positivos<br /><br /> Valor predeterminado: `1`|
|`WinRTInitialization`||

### <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

##  <a name="schedulertype"></a>  SchedulerType (enumeración)

Utilizado por la directiva `SchedulerKind` para describir el tipo de subprocesos que el programador debería usar para contextos de ejecución subyacentes. Para obtener más información sobre las directivas del programador disponibles, vea [PolicyElementKey](concurrency-namespace-enums.md).

```
enum SchedulerType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`ThreadScheduler`|Indica una solicitud explícita de subprocesos Win32 normales.|
|`UmsThreadDefault`|Subprocesos programables en modo usuario (UMS) no se admiten en el Runtime de simultaneidad en Visual Studio 2013. Usando `UmsThreadDefault` como valor de la directiva `SchedulerType` no se producirá un error. Sin embargo, un programador creado con esa directiva establecerá el uso de subprocesos Win32 como valor predeterminado.|

### <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

##  <a name="schedulingprotocoltype"></a>  SchedulingProtocolType (enumeración)

La usa la directiva `SchedulingProtocol` para describir el algoritmo de programación que utilizará el programador. Para obtener más información sobre las directivas del programador disponibles, vea [PolicyElementKey](concurrency-namespace-enums.md).

```
enum SchedulingProtocolType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`EnhanceForwardProgress`|El programador prefiere round-robin a través de grupos de programación después de ejecutar cada tarea. Contextos desbloqueados se programan normalmente en un modo de primero en el primero en salir (FIFO). Procesadores virtuales no almacenan en caché contextos desbloqueados.|
|`EnhanceScheduleGroupLocality`|El programador prefiere continuar trabajando en tareas dentro del grupo de programación actual antes de pasar a otro grupo de programación. Contextos desbloqueados se almacenan en caché por cada procesador virtual y se programan normalmente en forma de último en el primero en salir (LIFO) mediante el procesador virtual que se les desbloqueado.|

### <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

##  <a name="switchingproxystate"></a>  SwitchingProxyState (enumeración)

Se usa para denotar el estado en el que se encuentra un proxy del subproceso, cuando se ejecuta un cambio de contexto cooperativo en un proxy del subproceso diferente.

```
enum SwitchingProxyState;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`Blocking`|Indica que el subproceso que realiza la llamada está bloqueando de forma cooperativa y debería ser propiedad exclusiva por el llamador hasta que posteriormente, volver a ejecutar y realizar otra acción.|
|`Idle`|Indica que el subproceso de llamada ya no se necesita el componente Scheduler y se devuelven al administrador de recursos. El contexto que se enviaba es ya no puede ser utilizado por el Administrador de recursos.|
|`Nesting`|Indica que el subproceso de llamada es un programador secundario de anidamiento y es necesario por el llamador, para adjuntar a un programador diferente.|

### <a name="remarks"></a>Comentarios

Un parámetro de tipo `SwitchingProxyState` se pasa al método `IThreadProxy::SwitchTo` para indicar cómo tratar el proxy del subproceso que realiza la llamada a Resource Manager.

Para obtener más información sobre cómo se utiliza este tipo, consulte [IThreadProxy:: SwitchTo](ithreadproxy-structure.md#switchto).

##  <a name="task_group_status"></a>  task_group_status (enumeración)

Describe el estado de ejecución de un objeto `task_group` o `structured_task_group`. Numeroso métodos que esperan tareas programadas para que se complete un grupo de tareas, devuelven un valor de este tipo.

```
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

##  <a name="winrtinitializationtype"></a>  WinRTInitializationType (enumeración)

La utiliza la directiva `WinRTInitialization` para describir si se iniciará y cómo se iniciará Windows Runtime en subprocesos del programador para una aplicación que se ejecuta en sistemas operativos con Windows 8 o una versión posterior. Para obtener más información sobre las directivas del programador disponibles, vea [PolicyElementKey](concurrency-namespace-enums.md).

```
enum WinRTInitializationType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`DoNotInitializeWinRT`|Cuando la aplicación se ejecuta en los sistemas operativos con Windows 8 o una versión posterior, los subprocesos dentro del programador no se inicializarán en Windows Runtime.|
|`InitializeWinRTAsMTA`|Cuando la aplicación se ejecuta en los sistemas operativos con Windows 8 o una versión posterior, cada subproceso del programador se inicializará en Windows Runtime y declarará que forma parte del apartamento multiproceso.|

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt.h

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
