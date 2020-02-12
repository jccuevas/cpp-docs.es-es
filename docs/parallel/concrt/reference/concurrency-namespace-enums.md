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
ms.openlocfilehash: 716c2d03e6d1ff67566bd28e5931996ea2d400af
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141322"
---
# <a name="concurrency-namespace-enums"></a>concurrency (Enumeraciones del espacio de nombres)

||||
|-|-|-|
|[Agents_EventType](#agents_eventtype)|[ConcRT_EventType](#concrt_eventtype)|[Concrt_TraceFlags](#concrt_traceflags)|
|[Criticalregiontype (](#criticalregiontype)|[DynamicProgressFeedbackType (](#dynamicprogressfeedbacktype)|[Policyelementkey (](#policyelementkey)|
|[Schedulertype (](#schedulertype)|[Schedulingprotocoltype (](#schedulingprotocoltype)|[Switchingproxystate (](#switchingproxystate)|
|[Winrtinitializationtype (](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|
|[message_status](#message_status)|[task_group_status](#task_group_status)|

## <a name="agent_status"></a>Enumeración agent_status

Los estados válidos para un `agent`.

```cpp
enum agent_status;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`agent_canceled`|`agent` se canceló.|
|`agent_created`|El `agent` se ha creado pero no se ha iniciado.|
|`agent_done`|El `agent` ha finalizado sin ser cancelado.|
|`agent_runnable`|El `agent` se ha iniciado, pero no ha entrado en su método `run`.|
|`agent_started`|Se ha iniciado el `agent`.|

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [agentes asincrónicos](../../../parallel/concrt/asynchronous-agents.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

## <a name="agents_eventtype"></a>Enumeración Agents_EventType

Los tipos de eventos a los que se puede realiza un seguimiento utilizando la funcionalidad de seguimiento proporcionada por la Biblioteca de agentes.

```cpp
enum Agents_EventType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`AGENTS_EVENT_CREATE`|Tipo de evento que representa la creación de un objeto.|
|`AGENTS_EVENT_DESTROY`|Tipo de evento que representa la eliminación de un objeto.|
|`AGENTS_EVENT_END`|Un tipo de evento que representa la conclusión de algún procesamiento|
|`AGENTS_EVENT_LINK`|Un tipo de evento que representa la vinculación de bloques de mensajes|
|`AGENTS_EVENT_NAME`|Tipo de evento que representa el nombre de un objeto.|
|`AGENTS_EVENT_SCHEDULE`|Tipo de evento que representa la programación de un proceso.|
|`AGENTS_EVENT_START`|Un tipo de evento que representa el inicio de algún procesamiento|
|`AGENTS_EVENT_UNLINK`|Tipo de evento que representa la desvinculación de bloques de mensajes|

### <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

## <a name="concrt_eventtype"></a>Enumeración ConcRT_EventType

Los tipos de eventos a los que se puede realizar un seguimiento utilizando la funcionalidad de seguimiento proporcionada por el runtime de simultaneidad.

```cpp
enum ConcRT_EventType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|Tipo de evento que representa la acción de asociar a un programador.|
|`CONCRT_EVENT_BLOCK`|Tipo de evento que representa la acción de un bloqueo de contexto.|
|`CONCRT_EVENT_DETACH`|Tipo de evento que representa la acción de Desasociar de un programador.|
|`CONCRT_EVENT_END`|Tipo de evento que marca el inicio de un par de eventos de inicio y fin.|
|`CONCRT_EVENT_GENERIC`|Tipo de evento que se usa para eventos varios.|
|`CONCRT_EVENT_IDLE`|Tipo de evento que representa la acción de un contexto que se está inactivo.|
|`CONCRT_EVENT_START`|Tipo de evento que marca el inicio de un par de eventos de inicio y fin.|
|`CONCRT_EVENT_UNBLOCK`|Tipo de evento que representa la acción de desbloquear un contexto.|
|`CONCRT_EVENT_YIELD`|Tipo de evento que representa la acción de un contexto que produce.|

### <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h **espacio de nombres:** simultaneidad

## <a name="concrt_traceflags"></a>Enumeración Concrt_TraceFlags

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

**Encabezado:** concrt. h

## <a name="criticalregiontype"></a>Enumeración Criticalregiontype (

El tipo de región crítica dentro del que se encuentra un contexto.

```cpp
enum CriticalRegionType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`InsideCriticalRegion`|Indica que el contexto está dentro de una región crítica. Cuando se encuentra dentro de una región crítica, se ocultan las suspensiones asincrónicas del programador. En caso de que se produzca una suspensión, el Administrador de recursos esperará a que el subproceso se convierta en ejecutable y simplemente lo reanudará en lugar de invocar de nuevo el programador. Los bloqueos que se realicen dentro de dicha región se deben tomar con sumo cuidado.|
|`InsideHyperCriticalRegion`|Indica que el contexto está dentro de una región de hipercrítica. Cuando se encuentra dentro de una región de Hyper-crítico, se ocultan las suspensiones sincrónicas y asincrónicas del programador. En caso de que se produzca una suspensión o un bloqueo, el administrador de recursos esperará a que el subproceso se convierta en ejecutable y simplemente lo reanudará en lugar de invocar de nuevo el programador. Los bloqueos realizados dentro de esta región nunca deben compartirse con código que se ejecuta fuera de dicha región. Si lo hace, se producirá un interbloqueo impredecible.|
|`OutsideCriticalRegion`|Indica que el contexto está fuera de cualquier región crítica.|

### <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm. h

## <a name="dynamicprogressfeedbacktype"></a>Enumeración DynamicProgressFeedbackType (

La usa la directiva `DynamicProgressFeedback` para describir si los recursos para el programador se volverán a equilibrar según la información estadística recopilada desde el programador, o únicamente se basarán en procesadores virtuales que entran y salen del estado de inactividad a través de llamadas a los métodos `Activate` y `Deactivate` en la interfaz `IVirtualProcessorRoot`. Para obtener más información sobre las directivas de programador disponibles, vea [policyelementkey (](concurrency-namespace-enums.md).

```cpp
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`ProgressFeedbackDisabled`|Scheduler no recopila información de progreso. El reequilibrio se realiza basándose únicamente en el nivel de suscripción del subproceso de hardware subyacente. Para obtener más información sobre los niveles de suscripción, vea [IExecutionResource:: currentsubscriptionlevel (](IExecutionResource-structure.md).<br /><br /> Este valor está reservado para su uso por el tiempo de ejecución.|
|`ProgressFeedbackEnabled`|Scheduler recopila información de progreso y la pasa al administrador de recursos. El administrador de recursos utilizará esta información estadística para reequilibrar los recursos en nombre del programador, además del nivel de suscripción del subproceso de hardware subyacente. Para obtener más información sobre los niveles de suscripción, vea [IExecutionResource:: currentsubscriptionlevel (](IExecutionResource-structure.md).|

## <a name="join_type"></a>Enumeración join_type

El tipo de un bloque de mensajería `join`.

```cpp
enum join_type;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`greedy`|Los bloques de mensajería de `join` expansivos aceptan inmediatamente un mensaje al propagarse. Esto es más eficaz, pero tiene la posibilidad de que se produzca un bloqueo en vivo, en función de la configuración de la red.|
|`non_greedy`|Los bloques de mensajería `join` no expansivos posponen los mensajes y los prueban y los consumen una vez que han llegado. Se garantiza que funcionan, pero son más lentos.|

### <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

## <a name="message_status"></a>Enumeración message_status

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
|`postponed`|El destino pospuso el mensaje.|

### <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

## <a name="policyelementkey"></a>Enumeración Policyelementkey (

Claves de directiva que describen aspectos de comportamiento del programador. Cada elemento de directiva se describe mediante un par clave-valor. Para obtener más información sobre las directivas del programador y su impacto en los programadores, vea [programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

```cpp
enum PolicyElementKey;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`ContextPriority`|La prioridad de subproceso del sistema operativo de cada contexto del programador. Si esta clave se establece en el valor `INHERIT_THREAD_PRIORITY` los contextos del programador heredarán la prioridad del subproceso que creó el programador.<br /><br /> Valores válidos: cualquiera de los valores válidos para la función de `SetThreadPriority` de Windows y el valor especial `INHERIT_THREAD_PRIORITY`<br /><br /> Valor predeterminado: `THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|Tamaño de pila reservado de cada contexto en el programador en kilobytes.<br /><br /> Valores válidos: enteros positivos<br /><br /> Valor predeterminado: `0`, que indica que se debe usar el valor predeterminado del proceso para el tamaño de la pila.|
|`DynamicProgressFeedback`|Determina si los recursos para el programador se reequilibrarán según la información estadística recopilada de Scheduler o solo en función del nivel de suscripción de subprocesos de hardware subyacentes. Para obtener más información, vea [DynamicProgressFeedbackType (](#dynamicprogressfeedbacktype).<br /><br /> Valores válidos: un miembro de la enumeración `DynamicProgressFeedbackType`, ya sea `ProgressFeedbackEnabled` o `ProgressFeedbackDisabled`<br /><br /> Valor predeterminado: `ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|Cuando la clave de directiva de `SchedulingProtocol` está establecida en el valor `EnhanceScheduleGroupLocality`, especifica el número máximo de contextos ejecutables que se pueden almacenar en caché en las colas locales de cada procesador virtual. Estos contextos normalmente se ejecutarán en orden LIFO (último en salir, primero en salir) en el procesador virtual que hizo que se conviertan en ejecutables. Tenga en cuenta que esta clave de Directiva no tiene ningún significado cuando la clave de `SchedulingProtocol` está establecida en el valor `EnhanceForwardProgress`.<br /><br /> Valores válidos: enteros no negativos<br /><br /> Valor predeterminado: `8`|
|`MaxConcurrency`|El nivel de simultaneidad máximo deseado por el programador. El administrador de recursos intentará asignar inicialmente estos muchos procesadores virtuales. El valor especial [maxexecutionresources (](concurrency-namespace-constants1.md#maxexecutionresources) indica que el nivel de simultaneidad deseado es el mismo que el número de subprocesos de hardware de la máquina. Si el valor especificado para `MinConcurrency` es mayor que el número de subprocesos de hardware del equipo y `MaxConcurrency` se especifica como `MaxExecutionResources`, se genera el valor de `MaxConcurrency` para que coincida con lo que se establece para `MinConcurrency`.<br /><br /> Valores válidos: enteros positivos y el valor especial `MaxExecutionResources`<br /><br /> Valor predeterminado: `MaxExecutionResources`|
|`MaxPolicyElementKey`|La clave de elemento de directiva máxima. No es una clave de elemento válida.|
|`MinConcurrency`|El nivel de simultaneidad mínimo que el administrador de recursos debe proporcionar al programador. El número de procesadores virtuales asignados a un programador nunca va por debajo del mínimo. El valor especial [maxexecutionresources (](concurrency-namespace-constants1.md#maxexecutionresources) indica que el nivel de simultaneidad mínimo es el mismo que el número de subprocesos de hardware de la máquina. Si el valor especificado para `MaxConcurrency` es menor que el número de subprocesos de hardware del equipo y `MinConcurrency` se especifica como `MaxExecutionResources`, se reduce el valor de `MinConcurrency` para que coincida con lo que se establece para `MaxConcurrency`.<br /><br /> Valores válidos: enteros no negativos y el valor especial `MaxExecutionResources`. Tenga en cuenta que para las directivas de Scheduler usadas para la construcción de Runtime de simultaneidad programadores, el valor `0` no es válido.<br /><br /> Valor predeterminado: `1`|
|`SchedulerKind`|El tipo de subprocesos que el programador utilizará para los contextos de ejecución subyacentes. Para obtener más información, vea [schedulertype (](#schedulertype).<br /><br /> Valores válidos: un miembro de la enumeración `SchedulerType`, por ejemplo, `ThreadScheduler`<br /><br /> Valor predeterminado: `ThreadScheduler`. Esto se traduce en los subprocesos Win32 en todos los sistemas operativos.|
|`SchedulingProtocol`|Describe qué algoritmo de programación usará el programador. Para obtener más información, vea [schedulingprotocoltype (](#schedulingprotocoltype).<br /><br /> Valores válidos: un miembro de la enumeración `SchedulingProtocolType`, ya sea `EnhanceScheduleGroupLocality` o `EnhanceForwardProgress`<br /><br /> Valor predeterminado: `EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|Número provisional de procesadores virtuales por subproceso de hardware. El factor de sobresuscripción de destino puede aumentarse en el Administrador de recursos, si es necesario, para satisfacer `MaxConcurrency` con los subprocesos de hardware en la máquina.<br /><br /> Valores válidos: enteros positivos<br /><br /> Valor predeterminado: `1`|
|`WinRTInitialization`||

### <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

## <a name="schedulertype"></a>Enumeración Schedulertype (

Utilizado por la directiva `SchedulerKind` para describir el tipo de subprocesos que el programador debería usar para contextos de ejecución subyacentes. Para obtener más información sobre las directivas de programador disponibles, vea [policyelementkey (](concurrency-namespace-enums.md).

```cpp
enum SchedulerType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`ThreadScheduler`|Indica una solicitud explícita de subprocesos Win32 normales.|
|`UmsThreadDefault`|Los subprocesos programables en modo usuario (UMS) no se admiten en el Runtime de simultaneidad en Visual Studio 2013. Usando `UmsThreadDefault` como valor de la directiva `SchedulerType` no se producirá un error. Sin embargo, un programador creado con esa directiva establecerá el uso de subprocesos Win32 como valor predeterminado.|

### <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

## <a name="schedulingprotocoltype"></a>Enumeración Schedulingprotocoltype (

La usa la directiva `SchedulingProtocol` para describir el algoritmo de programación que utilizará el programador. Para obtener más información sobre las directivas de programador disponibles, vea [policyelementkey (](concurrency-namespace-enums.md).

```cpp
enum SchedulingProtocolType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`EnhanceForwardProgress`|El programador prefiere el Round Robin a través de los grupos de programación después de ejecutar cada tarea. Normalmente, los contextos desbloqueados se programan en el modo FIFO (primero en salir, primero en salir). Los procesadores virtuales no almacenan en caché contextos desbloqueados.|
|`EnhanceScheduleGroupLocality`|El programador prefiere continuar trabajando en las tareas dentro del grupo de programación actual antes de pasar a otro grupo de programación. Los contextos desbloqueados se almacenan en caché por procesador virtual y, por lo general, se programan en un modo LIFO (último en salir, primero en salir) que el procesador virtual desbloqueó.|

### <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

## <a name="switchingproxystate"></a>Enumeración Switchingproxystate (

Se usa para denotar el estado en el que se encuentra un proxy del subproceso, cuando se ejecuta un cambio de contexto cooperativo en un proxy del subproceso diferente.

```cpp
enum SwitchingProxyState;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`Blocking`|Indica que el subproceso que realiza la llamada se bloquea de forma cooperativa y debe ser propiedad exclusiva del llamador hasta que se ejecute de nuevo y realice otra acción.|
|`Idle`|Indica que el programador ya no necesita el subproceso que realiza la llamada y se devuelve al Administrador de recursos. El Administrador de recursos ya no puede usar el contexto que se estaba enviando al mismo.|
|`Nesting`|Indica que el subproceso que realiza la llamada está anidando un programador secundario y es necesario para el llamador, a fin de asociarlo a un programador diferente.|

### <a name="remarks"></a>Observaciones

Un parámetro de tipo `SwitchingProxyState` se pasa al método `IThreadProxy::SwitchTo` para indicar al Administrador de recursos cómo tratar el proxy del subproceso que está realizando la llamada.

Para obtener más información sobre cómo se usa este tipo, vea [IThreadProxy:: SwitchTo](ithreadproxy-structure.md#switchto).

## <a name="task_group_status"></a>Enumeración task_group_status

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

**Encabezado:** pplinterface. h

## <a name="winrtinitializationtype"></a>Enumeración Winrtinitializationtype (

La utiliza la directiva `WinRTInitialization` para describir si se iniciará y cómo se iniciará Windows Runtime en subprocesos del programador para una aplicación que se ejecuta en sistemas operativos con Windows 8 o una versión posterior. Para obtener más información sobre las directivas de programador disponibles, vea [policyelementkey (](concurrency-namespace-enums.md).

```cpp
enum WinRTInitializationType;
```

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`DoNotInitializeWinRT`|Cuando la aplicación se ejecuta en los sistemas operativos con Windows 8 o una versión posterior, los subprocesos dentro del programador no se inicializarán en Windows Runtime.|
|`InitializeWinRTAsMTA`|Cuando la aplicación se ejecuta en los sistemas operativos con Windows 8 o una versión posterior, cada subproceso del programador se inicializará en Windows en tiempo de ejecución y declarará que forma parte del apartamento multiproceso.|

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
