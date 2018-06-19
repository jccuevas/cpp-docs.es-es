---
title: simultaneidad Namespace | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- concurrent_priority_queue/concurrency
- agents/concurrency
- concurrent_vector/concurrency
- concrt/concurrency
- internal_split_ordered_list/concurrency
- concurrent_queue/concurrency
- pplcancellation_token/concurrency
- pplinterface/concurrency
- ppltasks/concurrency
- ppl/concurrency
- concurrent_unordered_map/concurrency
- concrtrm/concurrency
- concurrent_unordered_set/concurrency
- pplconcrt/concurrency
- internal_concurrent_hash/concurrency
dev_langs:
- C++
helpviewer_keywords:
- Concurrency namespace
ms.assetid: f1d33ca2-679b-4442-b140-22a9d9df61d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d5659c48b73eb8dfde4ffc7683de3c2cf721564d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695192"
---
# <a name="concurrency-namespace"></a>concurrency (Espacio de nombres)
El espacio de nombres `Concurrency` proporciona las clases y funciones que dan acceso al Runtime de simultaneidad, un marco de programación simultáneo para C++. Para obtener más información, consulte [Runtime de simultaneidad](../../../parallel/concrt/concurrency-runtime.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
namespace concurrency;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="namespaces"></a>Espacios de nombres  
  
|Name|Descripción|  
|----------|-----------------|  
|[Concurrency::Extensibility Namespace](http://msdn.microsoft.com/en-us/16a86ff2-128e-4edf-89e4-38aac79c81f9)||  
  
### <a name="typedefs"></a>Typedefs  
  
|Name|Descripción|  
|----------|-----------------|  
|`runtime_object_identity`|Cada instancia del mensaje tiene una identidad que sigue a esta definición mientras se clona y se pasa entre los componentes de mensajería. Esta no puede ser la dirección del objeto de mensaje.|  
|`task_status`|Tipo que representa el estado terminal de una tarea. Los valores válidos son `completed` y `canceled`.|  
|`TaskProc`|Una abstracción básica para una tarea, definida como `void (__cdecl * TaskProc)(void *)`. Se llama a `TaskProc` para invocar al cuerpo de una tarea.|  
|`TaskProc_t`|Una abstracción básica para una tarea, definida como `void (__cdecl * TaskProc_t)(void *)`. Se llama a `TaskProc` para invocar al cuerpo de una tarea.|  
  
### <a name="classes"></a>Clases  
  
|Name|Descripción|  
|----------|-----------------|  
|[affinity_partitioner (clase)](affinity-partitioner-class.md)|La clase `affinity_partitioner` es similar a la clase `static_partitioner`, pero mejora la afinidad de caché eligiendo la asignación de subintervalos para subprocesos de trabajo. Esta clase puede mejorar considerablemente el rendimiento cuando un bucle se vuelve a ejecutar sobre el mismo conjunto de datos, y los datos se ajustan al caché. Observe que el mismo objeto `affinity_partitioner` debe utilizarse con iteraciones posteriores de un bucle paralelo que se ejecuta sobre un conjunto de datos determinado, para beneficiarse de la situación de los datos.|  
|[agent (clase)](agent-class.md)|Una clase diseñada para usarse como una clase base para todos los agentes independientes. Se usa para ocultar el estado de otros agentes e interactuar con el paso de mensajes.|  
|[auto_partitioner (clase)](auto-partitioner-class.md)|La clase `auto_partitioner` representa a los métodos predeterminados `parallel_for`, `parallel_for_each` y usa `parallel_transform` para dividir el intervalo sobre el que iteran. Este método de particiones emplea la apropiación del intervalo para el equilibrio de carga, así como la cancelación por iterar.|  
|[bad_target (clase)](bad-target-class.md)|Esta clase describe una excepción que se produce cuando un bloque de mensajería recibe un puntero a un destino que no es válido para la operación que se realiza.|  
|[call (clase)](call-class.md)|Un bloque de mensajería `call` es un `target_block` con varios orígenes y ordenado, que invoca una función especificada al recibir un mensaje.|  
|[cancellation_token (clase)](cancellation-token-class.md)|La clase `cancellation_token` representa la capacidad para determinar si se ha solicitado la cancelación de alguna operación. Se puede asociar un determinado símbolo con un objeto `task_group`, `structured_task_group` o `task` para proporcionar una cancelación implícita. Este token también puede sondearse para la cancelación o puede hacer que se registre una devolución únicamente si se cancela el objeto `cancellation_token_source` asociado.|  
|[cancellation_token_registration (clase)](cancellation-token-registration-class.md)|La clase `cancellation_token_registration` representa una notificación de devolución de llamada de un objeto `cancellation_token`. Cuando el método `register` de un objeto `cancellation_token` se usa para recibir una notificación de cuándo se produce la cancelación, se devuelve un objeto `cancellation_token_registration` como identificador a la devolución de la llamada de modo que el llamador puede solicitar que ya no se realice una devolución de llamada específica a través del uso del método `deregister`.|  
|[cancellation_token_source (clase)](cancellation-token-source-class.md)|La clase `cancellation_token_source` representa la capacidad para cancelar una operación que se puede cancelar.|  
|[choice (clase)](choice-class.md)|Un bloque de mensajería `choice` es un bloque de varios orígenes y de destino único que representa una interacción del flujo de control con un conjunto de orígenes. El bloque de elección esperará a cualquiera de los orígenes para generar un mensaje y propagará el índice del origen que generó el mensaje.|  
|[combinable (clase)](combinable-class.md)|El objeto `combinable<T>` está diseñado para proporcionar copias de subprocesos privados de datos, para realizar subcálculos de subprocesos locales sin bloqueos durante algoritmos paralelos. Al final de la operación paralela, los subcálculos de subprocesos privados pueden combinarse en un resultado final. Esta clase se puede utilizar en lugar de una variable compartida y puede dar lugar a una mejora en el rendimiento que, de lo contrario, daría lugar a mucha contención en esa variable compartida.|  
|[concurrent_priority_queue (clase)](concurrent-priority-queue-class.md)|La clase `concurrent_priority_queue` es un contenedor que permite que varios subprocesos inserten y extraigan elementos de forma simultánea. Los elementos se extraen en orden de prioridad donde la prioridad viene determinada por un functor proporcionado como un argumento de plantilla.|  
|[concurrent_queue (clase)](concurrent-queue-class.md)|La clase `concurrent_queue` es una clase de contenedor de secuencias que permite el acceso primero en entrar, primero en salir a sus elementos. Habilita un conjunto limitado de operaciones seguras para simultaneidad, como `push` y `try_pop`.|  
|[concurrent_unordered_map (clase)](concurrent-unordered-map-class.md)|La clase `concurrent_unordered_map` es un contenedor seguro para simultaneidad que controla una secuencia de variación de longitud de elementos del tipo `std::pair<const K, _Element_type>`. La secuencia se representa de una manera que habilita la anexión segura para simultaneidad, el acceso a elementos, el acceso a iterador y las operaciones de recorrido de iterador.|  
|[concurrent_unordered_multimap (clase)](concurrent-unordered-multimap-class.md)|La clase `concurrent_unordered_multimap` es un contenedor seguro para simultaneidad que controla una secuencia de elementos de longitud variable del tipo `std::pair<const K, _Element_type>`. La secuencia se representa de una manera que habilita la anexión segura para simultaneidad, el acceso a elementos, el acceso a iterador y las operaciones de recorrido de iterador.|  
|[concurrent_unordered_multiset (clase)](concurrent-unordered-multiset-class.md)|La `concurrent_unordered_multiset` clase es un contenedor seguro para simultaneidad que controla una secuencia de longitud variable de elementos de tipo K. La secuencia se representa de una manera que habilita seguro para simultaneidad anexar, acceso de elemento, acceso de iterador y las operaciones de recorrido de iterador.|  
|[concurrent_unordered_set (clase)](concurrent-unordered-set-class.md)|La `concurrent_unordered_set` clase es un contenedor seguro para simultaneidad que controla una secuencia de longitud variable de elementos de tipo K. La secuencia se representa de una manera que habilita seguro para simultaneidad anexar, acceso de elemento, acceso de iterador y las operaciones de recorrido de iterador.|  
|[concurrent_vector (clase)](concurrent-vector-class.md)|La clase `concurrent_vector` es una clase de contenedor de secuencia que permite el acceso aleatorio a cualquier elemento. Habilita las operaciones de anexión segura para simultaneidad, acceso de elemento, acceso de iterador e iterador transversal.|  
|[context (clase)](context-class.md)|Representa una abstracción para un contexto de ejecución.|  
|[context_self_unblock (clase)](context-self-unblock-class.md)|Esta clase describe una excepción que se produce cuando se llama al método `Unblock` de un objeto `Context` desde el mismo contexto. Esto indicaría que un contexto especificado ha intentado desbloquearse a sí mismo.|  
|[context_unblock_unbalanced (clase)](context-unblock-unbalanced-class.md)|Esta clase describe una excepción que se produce cuando se llama a los métodos `Block` y `Unblock` de un objeto `Context` que no están emparejados correctamente.|  
|[critical_section (clase)](critical-section-class.md)|Una exclusión mutua no reentrante que es explícitamente consciente del runtime de simultaneidad.|  
|[CurrentScheduler (clase)](currentscheduler-class.md)|Representa una abstracción para el programador actual asociado al contexto de la llamada.|  
|[default_scheduler_exists (clase)](default-scheduler-exists-class.md)|Esta clase describe una excepción que se produce cuando se llama al método `Scheduler::SetDefaultSchedulerPolicy` cuando un programador predeterminado ya existe dentro del proceso.|  
|[event (clase)](event-class.md)|Un evento de reinicio manual que es explícitamente consciente del runtime de simultaneidad.|  
|[improper_lock (clase)](improper-lock-class.md)|Esta clase describe una excepción que se produce cuando se realiza un bloqueo de forma incorrecta.|  
|[improper_scheduler_attach (clase)](improper-scheduler-attach-class.md)|Esta clase describe una excepción que se produce cuando se llama al método `Attach` en un objeto `Scheduler` que ya se ha adjuntado al contexto actual.|  
|[improper_scheduler_detach (clase)](improper-scheduler-detach-class.md)|Esta clase describe una excepción que se produce cuando se llama al método `CurrentScheduler::Detach` en un contexto que no se ha adjuntado a ningún programador mediante el método `Attach` de un objeto `Scheduler`.|  
|[improper_scheduler_reference (clase)](improper-scheduler-reference-class.md)|Esta clase describe una excepción que se produce cuando se llama al método `Reference` en un objeto `Scheduler` que se está cerrando, desde un contexto que no forma parte de ese programador.|  
|[invalid_link_target (clase)](invalid-link-target-class.md)|Esta clase describe una excepción que se produce cuando se llama al método `link_target` de un bloque de mensajería y el bloque de mensajería no se puede vincular al destino. Este puede ser el resultado de superar el número de vínculos que se permiten en el bloque de mensajería o de intentar vincular un destino específico al mismo origen dos veces.|  
|[invalid_multiple_scheduling (clase)](invalid-multiple-scheduling-class.md)|Esta clase describe una excepción que se produce cuando un objeto `task_handle` se programa varias veces mediante el método `run` de un objeto `task_group` o `structured_task_group` sin una llamada que se interponga a los métodos `wait` o `run_and_wait`.|  
|[invalid_operation (clase)](invalid-operation-class.md)|Esta clase describe una excepción producida cuando se realiza una operación no válida que no está descrita con más precisión por otro tipo de excepción producida por el runtime de simultaneidad.|  
|[invalid_oversubscribe_operation (clase)](invalid-oversubscribe-operation-class.md)|Esta clase describe una excepción cuando se llama al método `Context::Oversubscribe` con el parámetro `_BeginOversubscription` establecido en `false` sin realizar antes una llamada al método `Context::Oversubscribe` con el parámetro `_BeginOversubscription` establecido en `true`.|  
|[invalid_scheduler_policy_key (clase)](invalid-scheduler-policy-key-class.md)|Esta clase describe una excepción que se produce cuando una clave no válida o desconocida se pasa a un constructor de objeto `SchedulerPolicy`, o el método `SetPolicyValue` de un objeto `SchedulerPolicy` se pasa a una clave que se debe cambiar mediante otros medios como el método `SetConcurrencyLimits`.|  
|[invalid_scheduler_policy_thread_specification (clase)](invalid-scheduler-policy-thread-specification-class.md)|Esta clase describe una excepción que se produce cuando se realiza un intento para establecer los límites de simultaneidad de un objeto `SchedulerPolicy`, de tal forma que el valor de la clave `MinConcurrency` es menor que el valor de la clave `MaxConcurrency`.|  
|[invalid_scheduler_policy_value (clase)](invalid-scheduler-policy-value-class.md)|Esta clase describe una excepción que se produce cuando una clave de directiva de un objeto `SchedulerPolicy` se establece en un valor no válido para esa clave.|  
|[ISource (clase)](isource-class.md)|La clase `ISource` es la interfaz para todos los bloques de origen. Los bloques de origen propagan mensajes a los bloques `ITarget`.|  
|[ITarget (clase)](itarget-class.md)|La clase `ITarget` es la interfaz para todos los bloques de destino. Los bloques de destinos consumen mensajes ofrecidos por los bloques `ISource`.|  
|[join (clase)](join-class.md)|Un bloque de mensajería `join` es un bloque `propagator_block` de destino único y de varios orígenes ordenado, que combina los mensajes de tipo `T` de cada uno de sus orígenes.|  
|[location (clase)](location-class.md)|Una abstracción de una ubicación física en el hardware.|  
|[message (clase)](message-class.md)|El sobre del mensaje básico que contiene la carga de datos que se pasa entre bloques de mensajería.|  
|[message_not_found (clase)](message-not-found-class.md)|Esta clase describe una excepción que se produce cuando un bloque de mensajería no puede encontrar un mensaje solicitado.|  
|[message_processor (clase)](message-processor-class.md)|La clase `message_processor` es la clase base abstracta del procesamiento de objetos `message`. No hay ninguna garantía en la clasificación de los mensajes.|  
|[missing_wait (clase)](missing-wait-class.md)|Esta clase describe una excepción que se produce cuando todavía existen tareas programadas para un objeto `task_group` o `structured_task_group` en el momento que el destructor de objeto se ejecuta. Nunca se producirá esta excepción si el destructor se alcanza debido al desenredo de pila como el resultado de una excepción.|  
|[multi_link_registry (clase)](multi-link-registry-class.md)|El objeto `multi_link_registry` es un `network_link_registry` que administra varios bloques de origen o varios bloques de destino.|  
|[multitype_join (clase)](multitype-join-class.md)|Un bloque de mensajería `multitype_join` es un bloque de mensajería de destino único, de varios orígenes, que combina los mensajes de diferentes tipos de cada uno de sus orígenes y ofrece una tupla de los mensajes combinados con sus destinos.|  
|[nested_scheduler_missing_detach (clase)](nested-scheduler-missing-detach-class.md)|Esta clase describe una excepción que se produce cuando el runtime de simultaneidad detecta que se dejó de llamar al método `CurrentScheduler::Detach` en un contexto adjunto a un segundo programador mediante el método `Attach` del objeto `Scheduler`.|  
|[network_link_registry (clase)](network-link-registry-class.md)|La clase base abstracta `network_link_registry` que administra los vínculos entre los bloques de origen y de destino.|  
|[operation_timed_out (clase)](operation-timed-out-class.md)|Esta clase describe una excepción que se produce cuando una operación ha agotado su tiempo de espera.|  
|[ordered_message_processor (clase)](ordered-message-processor-class.md)|Un `ordered_message_processor` es un `message_processor` que permite a los bloques de mensaje procesar los mensajes en el orden que se recibieron.|  
|[overwrite_buffer (clase)](overwrite-buffer-class.md)|Un bloque de mensajería `overwrite_buffer` es un bloque `propagator_block` de destino único, de varios orígenes y ordenado que es capaz de almacenar un único mensaje cada vez. Los nuevos mensajes sobrescriben a los retenidos previamente.|  
|[progress_reporter (clase)](progress-reporter-class.md)|La clase del informador de progreso que permite informar de notificaciones de progreso de un tipo específico. Cada objeto progress_reporter se vincula a una acción u operación asincrónica determinada.|  
|[propagator_block (clase)](propagator-block-class.md)|La clase `propagator_block` es una clase base abstracta para los bloques de mensaje que son un bloque de origen y de destino. Combina la funcionalidad de las clases `source_block` y `target_block`.|  
|[reader_writer_lock (clase)](reader-writer-lock-class.md)|Un bloqueo de lectura o escritura basado en cola, con preferencia del sistema de escritura y con giro solo local. El bloqueo permite el acceso primero en entrar, primero en salir (FIFO) a los sistemas de escritura y lectores agotados bajo una carga continua de sistemas de escritura.|  
|[ScheduleGroup (clase)](schedulegroup-class.md)|Representa una abstracción para un grupo de programación. Los grupos de programación organizan un conjunto de trabajos relacionados que se benefician de programarse juntos ya sea temporalmente, mediante la ejecución de otra tarea en el mismo grupo antes de trasladarse a otro grupo, o espacialmente, mediante la ejecución de varios elementos del mismo grupo en el mismo nodo NUMA o socket físico.|  
|[Scheduler (clase)](scheduler-class.md)|Representa una abstracción para un programador del runtime de simultaneidad.|  
|[scheduler_not_attached (clase)](scheduler-not-attached-class.md)|Esta clase describe una excepción que se produce cuando se realiza una operación que requiere que un programador se adjunte al contexto actual y no hay ninguno.|  
|[scheduler_resource_allocation_error (clase)](scheduler-resource-allocation-error-class.md)|Esta clase describe una excepción que se produce debido a un error al adquirir un recurso crítico en el runtime de simultaneidad.|  
|[scheduler_worker_creation_error (clase)](scheduler-worker-creation-error-class.md)|Esta clase describe una excepción producida debido a un error al crear un contexto de ejecución del trabajo en el runtime de simultaneidad.|  
|[SchedulerPolicy (clase)](schedulerpolicy-class.md)|La clase `SchedulerPolicy` contiene un conjunto de pares clave-valor, uno para cada elemento de directiva, que controla el comportamiento de una instancia del programador.|  
|[simple_partitioner (clase)](simple-partitioner-class.md)|La clase `simple_partitioner` representa una partición estática del intervalo sobre el que se itera mediante `parallel_for`. La clase Partitioner divide el intervalo en fragmentos de forma que cada fragmento tiene al menos el número de iteraciones especificadas por el tamaño del fragmento.|  
|[single_assignment (clase)](single-assignment-class.md)|Un bloque de mensajería `single_assignment` es un bloque `propagator_block` de destino único, de varios orígenes y ordenado capaz de almacenar un único `message` de una sola escritura.|  
|[single_link_registry (clase)](single-link-registry-class.md)|El objeto `single_link_registry` es un `network_link_registry` que administra un solo bloque de origen o bloque de destino.|  
|[source_block (clase)](source-block-class.md)|La clase `source_block` es una clase base abstracta solo para bloques de origen. La clase proporciona funcionalidad de administración de vínculo básico, así como comprobaciones de errores frecuentes.|  
|[source_link_manager (clase)](source-link-manager-class.md)|El objeto `source_link_manager` administra los vínculos de red del bloque de mensajería para los bloques `ISource`.|  
|[static_partitioner (clase)](static-partitioner-class.md)|La clase `static_partitioner` representa una partición estática del intervalo sobre el que se itera mediante `parallel_for`. La clase Partitioner divide el intervalo en tantos fragmentos como trabajadores hay disponibles para el programador subyacente.|  
|[structured_task_group (clase)](structured-task-group-class.md)|La clase `structured_task_group` representa una colección muy estructurada de trabajos paralelos. Puede poner en cola tareas individuales paralelas a `structured_task_group` mediante objetos `task_handle`, y esperar a que se completen, o cancelar el grupo de tareas antes de que haya finalizado su ejecución, que anulará cualquier tarea cuya ejecución no haya comenzado.|  
|[target_block (clase)](target-block-class.md)|La clase `target_block` es una clase base abstracta que proporciona funcionalidad de administración de vínculo básica y comprueba errores solo para bloques de destino.|  
|[task (clase) (Runtime de simultaneidad)](task-class.md)|La clase `task` de la biblioteca de patrones de procesamiento paralelo (PPL). Un objeto `task` representa el trabajo que se puede ejecutar de forma asincrónica y de forma simultánea con otras tareas y trabajos paralelos generados por los algoritmos paralelos en el runtime de simultaneidad. Genera un resultado de tipo `_ResultType` al finalizar correctamente. Las tareas de tipo `task<void>` no producen ningún resultado. Es posible esperar y cancelar una tarea de forma independiente al resto de tareas. También se puede componer con otras tareas mediante continuaciones (`then`), así como con patrones de unión (`when_all`) y elección (`when_any`).|  
|[task_canceled (clase)](task-canceled-class.md)|Esta clase describe una excepción producida por la capa de tareas de PPL para obligar a que se cancele la tarea actual. También se produce por la `get()` método [tarea](http://msdn.microsoft.com/en-us/5389e8a5-5038-40b6-844a-55e9b58ad35f), para una tarea cancelada.|  
|[task_completion_event (clase)](task-completion-event-class.md)|La clase `task_completion_event` permite retrasar la ejecución de una tarea hasta que se satisfaga una condición, o iniciar una tarea en respuesta a un evento externo.|  
|[task_continuation_context (clase)](task-continuation-context-class.md)|La clase `task_continuation_context` permite especificar dónde se desea que se ejecute una continuación. Sólo es útil utilizar esta clase desde una aplicación de UWP. Para las aplicaciones en tiempo de ejecución que no sean de Windows, el contexto de ejecución de la continuación de la tarea es determinado por el tiempo de ejecución y no es configurable.|  
|[task_group (clase)](task-group-class.md)|La clase `task_group` representa una colección de trabajo paralelo que es posible esperar o cancelar.|  
|[task_handle (clase)](task-handle-class.md)|La clase `task_handle` representa un elemento de trabajo individual paralelo. Encapsula las instrucciones y los datos necesarios para ejecutar una parte del trabajo.|  
|[task_options (clase) (Runtime de simultaneidad)](task-options-class-concurrency-runtime.md)|Representa las opciones permitidas para crear una tarea|  
|[timer (clase)](timer-class.md)|Un bloque de mensajería `timer` es un bloque `source_block` con destino único, capaz de enviar un mensaje a su destino cuando un período de tiempo especificado ha transcurrido o en intervalos concretos.|  
|[transformer (clase)](transformer-class.md)|Un bloque de mensajería `transformer` es un bloque `propagator_block` de destino único, de varios orígenes y ordenado capaz de almacenar un número ilimitado de mensajes de un tipo diferente.|  
|[Clase unbounded_buffer](unbounded-buffer-class.md)|Un bloque de mensajería `unbounded_buffer` es un bloque `propagator_block` de destino único, de varios orígenes y ordenado capaz de almacenar un número ilimitado de mensajes.|  
|[unsupported_os (clase)](unsupported-os-class.md)|Esta clase describe una excepción que se produce cuando se usa un sistema operativo no compatible.|  
  
### <a name="structures"></a>Estructuras  
  
|Name|Descripción|  
|----------|-----------------|  
|[DispatchState (estructura)](dispatchstate-structure.md)|La estructura `DispatchState` se usa para transferir el estado al método `IExecutionContext::Dispatch`. Describe las circunstancias bajo las que el método `Dispatch` se invoca en una interfaz `IExecutionContext`.|  
|[IExecutionContext (estructura)](iexecutioncontext-structure.md)|Una interfaz a un contexto de ejecución que se puede ejecutar en un procesador virtual determinado y que puede cambiar de contexto de forma cooperativa.|  
|[IExecutionResource (estructura)](iexecutionresource-structure.md)|Una abstracción para un subproceso del hardware.|  
|[IResourceManager (estructura)](iresourcemanager-structure.md)|Una interfaz al Administrador de recursos del runtime de simultaneidad. Esta es la interfaz que usan los programadores para comunicares con el Administrador de recursos.|  
|[IScheduler (estructura)](ischeduler-structure.md)|Una interfaz a una abstracción de un programador de trabajo. El Administrador de recursos del runtime de simultaneidad usa esta interfaz para comunicarse con programadores de trabajo.|  
|[ISchedulerProxy (estructura)](ischedulerproxy-structure.md)|La interfaz por la que los programadores se comunican con el Administrador de recursos del runtime de simultaneidad para negociar la asignación de recursos.|  
|[IThreadProxy (estructura)](ithreadproxy-structure.md)|Una abstracción para un subproceso de ejecución. Dependiendo de la clave de directiva `SchedulerType` del programador que se crea, el Administrador de recursos concederá al usuario un proxy del subproceso que está respaldado por un subproceso de Win32 normal o por un subproceso programable de modo de usuario (UMS). Los subprocesos UMS se admiten en sistemas operativos de 64 bits con Windows 7 o una versión posterior.|  
|[ITopologyExecutionResource (estructura)](itopologyexecutionresource-structure.md)|Una interfaz a un recurso de ejecución definido por el Administrador de recursos.|  
|[ITopologyNode (estructura)](itopologynode-structure.md)|Una interfaz a un nodo de topología definido por el Administrador de recursos. Un nodo contiene uno o varios recursos de ejecución.|  
|[IUMSCompletionList (estructura)](iumscompletionlist-structure.md)|Representa una lista de finalización UMS. Cuando se bloquea un subproceso UMS, el contexto de programación designado del programador se envía de forma que se puede tomar una decisión sobre qué programar en la raíz del procesador virtual subyacente mientras se bloquea el subproceso original. Cuando el subproceso original se desbloquea, el sistema operativo lo pone en cola de la lista de finalización, que es accesible a través de esta interfaz. El programador puede consultar la lista de finalización en el contexto de programación designado o en cualquier otro lugar que busca trabajo.|  
|[IUMSScheduler (estructura)](iumsscheduler-structure.md)|Una interfaz a una abstracción de un programador de trabajo que desea que el Administrador de recursos del runtime de simultaneidad controle los subprocesos programables de modo de usuario (UMS). El Administrador de recursos usa esta interfaz para comunicarse con los programadores de subprocesos UMS. La interfaz `IUMSScheduler` hereda de la interfaz `IScheduler`.|  
|[IUMSThreadProxy (estructura)](iumsthreadproxy-structure.md)|Una abstracción para un subproceso de ejecución. Si desea conceder subprocesos programables en modo usuario (UMS) al programador, establezca el valor para el elemento de directiva de programador `SchedulerKind` en `UmsThreadDefault` e implemente la interfaz `IUMSScheduler`. Los subprocesos UMS se admiten únicamente en sistemas operativos de 64 bits con Windows 7 o una versión posterior.|  
|[IUMSUnblockNotification (estructura)](iumsunblocknotification-structure.md)|Representa una notificación del Administrador de recursos indicando que un proxy del subproceso que había bloqueado y desencadenado un valor devuelto al contexto de programación designado del programador, se ha desbloqueado y está listo para su programación. Esta interfaz no es válida una vez que el contexto de ejecución asociado del proxy del subproceso, devuelto desde el método `GetContext`, se vuelve a programar.|  
|[IVirtualProcessorRoot (estructura)](ivirtualprocessorroot-structure.md)|Una abstracción para un subproceso de hardware en el que un proxy del subproceso puede ejecutarse.|  
|[scheduler_interface (estructura)](scheduler-interface-structure.md)|Interfaz de Scheduler|  
|[scheduler_ptr (estructura) (Runtime de simultaneidad)](scheduler-ptr-structure-concurrency-runtime.md)|Representa un puntero a un programador. Esta clase existe para permitir la especificación de una duración compartida mediante shared_ptr o simplemente permitir una referencia sin formato mediante un puntero sin formato.|  
  
### <a name="enumerations"></a>Enumeraciones  
  
|nombre|Descripción|  
|----------|-----------------|  
|[agent_status](concurrency-namespace-enums.md#agent_status)|Los estados válidos para un `agent`.|  
|[Agents_EventType](concurrency-namespace-enums.md#agents_eventtype)|Los tipos de eventos a los que se puede realiza un seguimiento utilizando la funcionalidad de seguimiento proporcionada por la Biblioteca de agentes.|  
|[ConcRT_EventType](concurrency-namespace-enums.md#concrt_eventtype)|Los tipos de eventos a los que se puede realizar un seguimiento utilizando la funcionalidad de seguimiento proporcionada por el runtime de simultaneidad.|  
|[Concrt_TraceFlags](concurrency-namespace-enums.md#concrt_traceflags)|Marcas de seguimiento para los tipos de evento|  
|[CriticalRegionType](concurrency-namespace-enums.md#criticalregiontype)|El tipo de región crítica dentro del que se encuentra un contexto.|  
|[DynamicProgressFeedbackType](concurrency-namespace-enums.md#dynamicprogressfeedbacktype)|La usa la directiva `DynamicProgressFeedback` para describir si los recursos para el programador se volverán a equilibrar según la información estadística recopilada desde el programador, o únicamente se basarán en procesadores virtuales que entran y salen del estado de inactividad a través de llamadas a los métodos `Activate` y `Deactivate` en la interfaz `IVirtualProcessorRoot`. Para obtener más información sobre las directivas del programador disponibles, vea [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey).|  
|[join_type](concurrency-namespace-enums.md#join_type)|El tipo de un bloque de mensajería `join`.|  
|[message_status](concurrency-namespace-enums.md#message_status)|Las respuestas válidas para una oferta de un objeto `message` a un bloque.|  
|[PolicyElementKey](concurrency-namespace-enums.md#policyelementkey)|Claves de directiva que describen aspectos de comportamiento del programador. Cada elemento de directiva se describe mediante un par clave-valor. Para obtener más información sobre las directivas del programador y su impacto en los programadores, vea [programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).|  
|[SchedulerType](concurrency-namespace-enums.md#schedulertype)|Utilizado por la directiva `SchedulerKind` para describir el tipo de subprocesos que el programador debería usar para contextos de ejecución subyacentes. Para obtener más información sobre las directivas del programador disponibles, vea [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey).|  
|[SchedulingProtocolType](concurrency-namespace-enums.md#schedulingprotocoltype)|La usa la directiva `SchedulingProtocol` para describir el algoritmo de programación que utilizará el programador. Para obtener más información sobre las directivas del programador disponibles, vea [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey).|  
|[SwitchingProxyState](concurrency-namespace-enums.md#switchingproxystate)|Se usa para denotar el estado en el que se encuentra un proxy del subproceso, cuando se ejecuta un cambio de contexto cooperativo en un proxy del subproceso diferente.|  
|[task_group_status](concurrency-namespace-enums.md#task_group_status)|Describe el estado de ejecución de un objeto `task_group` o `structured_task_group`. Numeroso métodos que esperan tareas programadas para que se complete un grupo de tareas, devuelven un valor de este tipo.|  
|[WinRTInitializationType](concurrency-namespace-enums.md#winrtinitializationtype)|La utiliza la directiva `WinRTInitialization` para describir si se iniciará y cómo se iniciará Windows en tiempo de ejecución en subprocesos del programador para una aplicación que se ejecuta en sistemas operativos con Windows 8 o una versión posterior. Para obtener más información sobre las directivas del programador disponibles, vea [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey).|  
  
### <a name="functions"></a>Funciones  
  
|Name|Descripción|  
|----------|-----------------|  
|[Alloc (función)](concurrency-namespace-functions.md#alloc)|Asigna un bloque de memoria del tamaño especificado del subasignador de almacenamiento en caché del runtime de simultaneidad.|  
|[asend (función)](concurrency-namespace-functions.md#asend)|Sobrecargado. Una operación de envío asincrónica, que programa una tarea para propagar los datos al bloque de destino.|  
|[cancel_current_task (función)](concurrency-namespace-functions.md#cancel_current_task)|Cancela la tarea que se está ejecutando actualmente. Se puede llamar a esta función desde el cuerpo de una tarea para anular la ejecución de la tarea y hacer que obtenga el estado `canceled`.<br /><br /> No está admitido que llame a esta función si no está dentro del cuerpo de un objeto `task`. Esto dará lugar a un comportamiento indefinido como, por ejemplo, un bloqueo en la aplicación.|  
|[create_async (función)](concurrency-namespace-functions.md#create_async)|Crea una construcción asincrónica de Windows Runtime basada en un objeto o función lambda que se ha proporcionado. El tipo devuelto de `create_async` es `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^` o `IAsyncOperationWithProgress<TResult, TProgress>^` en función de la signatura de la expresión lambda pasada al método.|  
|[create_task (función)](concurrency-namespace-functions.md#create_task)|Sobrecargado. Crea un PPL [tarea](http://msdn.microsoft.com/en-us/5389e8a5-5038-40b6-844a-55e9b58ad35f) objeto. `create_task` se puede usar en cualquier lugar en el que se ha utilizado un constructor de tarea. Se proporciona principalmente por comodidad, porque permite el uso de la palabra clave `auto` cuando se crean tareas.|  
|[CreateResourceManager (función)](concurrency-namespace-functions.md#createresourcemanager)|Devuelve una interfaz que representa la instancia singleton del Administrador de recursos del runtime de simultaneidad. El Administrador de recursos es el responsable de asignar recursos a los programadores que desean cooperar entre sí.|  
|[DisableTracing (función)](concurrency-namespace-functions.md#disabletracing)|Deshabilita la traza en el runtime de simultaneidad. Esta función está en desuso porque la traza de ETW no está registrada de forma predeterminada.|  
|[EnableTracing (función)](concurrency-namespace-functions.md#enabletracing)|Habilita la traza en el runtime de simultaneidad. Esta función está en desuso porque la traza de ETW ahora está registrada de forma predeterminada.|  
|[Free (función)](concurrency-namespace-functions.md#free)|Libera un bloque de memoria asignado previamente mediante el método `Alloc` al subasignador de almacenamiento en caché del runtime de simultaneidad.|  
|[get_ambient_scheduler () (función) (Runtime de simultaneidad)](concurrency-namespace-functions.md#get_ambient_scheduler)||  
|[GetExecutionContextId (función)](concurrency-namespace-functions.md#getexecutioncontextid)|Devuelve un identificador único que se puede asignar a un contexto de ejecución que implementa la interfaz `IExecutionContext`.|  
|[GetOSVersion (función)](concurrency-namespace-functions.md#getosversion)|Devuelve la versión del sistema operativo.|  
|[GetProcessorCount (función)](concurrency-namespace-functions.md#getprocessorcount)|Devuelve el número de subprocesos de hardware en el sistema subyacente.|  
|[GetProcessorNodeCount (función)](concurrency-namespace-functions.md#getprocessornodecount)|Devuelve el número de nodos NUMA o paquetes de procesador en el sistema subyacente.|  
|[GetSchedulerId (función)](concurrency-namespace-functions.md#getschedulerid)|Devuelve un identificador único que se puede asignar a un programador que implementa la interfaz `IScheduler`.|  
|[interruption_point (función)](concurrency-namespace-functions.md#interruption_point)|Crea un punto de interrupción para la cancelación. Si una cancelación está en curso en el contexto donde se llama a esta función, se producirá una excepción interna que anula la ejecución del trabajo paralelo que se está ejecutando actualmente. Si la cancelación no está en curso, la función no hace nada.|  
|[is_current_task_group_canceling (función)](concurrency-namespace-functions.md#is_current_task_group_canceling)|Devuelve una indicación de si el grupo de tareas que actualmente se está ejecutando alineado en el contexto actual se encuentra en medio de una cancelación activa (o lo estará pronto). Tenga en cuenta que si no hay ningún grupo de tareas que se ejecuta actualmente alineado en el contexto actual, se devolverá `false`.|  
|[make_choice (función)](concurrency-namespace-functions.md#make_choice)|Sobrecargado. Construye un bloque de mensajería `choice` de un `Scheduler` opcional o `ScheduleGroup` y dos o más orígenes de entrada.|  
|[make_greedy_join (función)](concurrency-namespace-functions.md#make_greedy_join)|Sobrecargado. Construye un bloque de mensajería `greedy multitype_join` de un `Scheduler` opcional o `ScheduleGroup` y dos o más orígenes de entrada.|  
|[make_join (función)](concurrency-namespace-functions.md#make_join)|Sobrecargado. Construye un bloque de mensajería `non_greedy multitype_join` de un `Scheduler` opcional o `ScheduleGroup` y dos o más orígenes de entrada.|  
|[make_task (función)](concurrency-namespace-functions.md#make_task)|Un método generador para crear un objeto `task_handle`.|  
|[parallel_buffered_sort (función)](concurrency-namespace-functions.md#parallel_buffered_sort)|Sobrecargado. Organiza los elementos en un intervalo especificado en un orden no descendente, o de acuerdo con un criterio de ordenación especificado por un predicado binario, en paralelo. Esta función es semánticamente similar a `std::sort` que se trata de una ordenación basada en comparación, inestable, en contexto salvo que necesita espacio adicional `O(n)` y requiere una inicialización predeterminada para los elementos que se ordenan.|  
|[parallel_for (función)](concurrency-namespace-functions.md#parallel_for)|Sobrecargado. `parallel_for` itera sobre un intervalo de índices y ejecuta una función proporcionada por el usuario en cada iteración, en paralelo.|  
|[parallel_for_each (función)](concurrency-namespace-functions.md#parallel_for_each)|Sobrecargado. `parallel_for_each` aplica una función especificada para cada elemento dentro de un intervalo, en paralelo. Es semánticamente equivalente a la función `for_each` en el espacio de nombres `std`, salvo que la iteración sobre los elementos se realiza en paralelo, y el orden de iteración no está especificado. El argumento `_Func` debe admitir un operador de llamada de función del formulario `operator()(T)` donde el parámetro `T` es el tipo de elemento del contenedor que se recorre en iteración.|  
|[parallel_invoke (función)](concurrency-namespace-functions.md#parallel_invoke)|Sobrecargado. Ejecuta los objetos de función proporcionados como parámetros en paralelo y se bloquea hasta que han terminado de ejecutarse. Cada objeto de función puede ser una expresión lambda, un puntero a una función o cualquier otro objeto que admite el operador de llamada de función con la signatura `void operator()()`.|  
|[parallel_radixsort (función)](concurrency-namespace-functions.md#parallel_radixsort)|Sobrecargado. Organiza los elementos en un intervalo especificado en un orden no descendente utilizando un algoritmo de ordenación de base. Esta es una función estable de ordenación que requiere una función de proyección que pueda proyectar elementos que se puedan ordenar en claves como enteros sin signo. Se requiere una inicialización predeterminada para que se ordenen los elementos.|  
|[parallel_reduce (función)](concurrency-namespace-functions.md#parallel_reduce)|Sobrecargado. Calcula la suma de todos los elementos en un intervalo especificado mediante el cálculo de sumas parciales sucesivas, o calcula el resultado de los resultados parciales sucesivos obtenidos de manera similar mediante el uso de una operación binaria determinada distinta de la suma, en paralelo. `parallel_reduce` es semánticamente similar a `std::accumulate`, salvo que requiere que la operación binaria sea asociativa, y requiere un valor de identidad en lugar de un valor inicial.|  
|[parallel_sort (función)](concurrency-namespace-functions.md#parallel_sort)|Sobrecargado. Organiza los elementos en un intervalo especificado en un orden no descendente, o de acuerdo con un criterio de ordenación especificado por un predicado binario, en paralelo. Esta función es semánticamente similar a `std::sort` que se trata una ordenación basada en comparación, inestable, en contexto.|  
|[parallel_transform (función)](concurrency-namespace-functions.md#parallel_transform)|Sobrecargado. Aplica un objeto especificado de función a cada elemento de un intervalo de origen, o a un par de elementos de dos intervalos de origen, y copia los valores devueltos del objeto de función en un intervalo de destino, en paralelo. Esta función es semánticamente equivalente a `std::transform`.|  
|[Receive (función)](concurrency-namespace-functions.md#receive)|Sobrecargado. Una implementación receive general, que permite a un contexto esperar datos exactamente de un origen y filtrar los valores que se aceptan.|  
|[run_with_cancellation_token (función)](concurrency-namespace-functions.md#run_with_cancellation_token)|Ejecuta un objeto de función de forma inmediata y sincrónicamente en el contexto de un token de cancelación dado.|  
|[Send (función)](concurrency-namespace-functions.md#send)|Sobrecargado. Una operación de envío sincrónica, que espera hasta que el destino acepte o rechace el mensaje.|  
|[set_ambient_scheduler () (función) (Runtime de simultaneidad)](concurrency-namespace-functions.md#set_ambient_scheduler)||  
|[set_task_execution_resources Function](concurrency-namespace-functions.md#set_task_execution_resources)|Sobrecargado. Limita los recursos de ejecución que usan los subprocesos de trabajo internos del runtime de simultaneidad para el conjunto de afinidad especificado.<br /><br /> Se puede llamar a este método solamente antes de que el Administrador de recursos se haya creado o entre dos duraciones del Administrador de recursos. Se puede invocar varias veces siempre que el Administrador de recursos no exista en el momento de la invocación. Después de que se haya establecido un límite de afinidad, permanece en vigor hasta la siguiente llamada válida al método `set_task_execution_resources`.<br /><br /> La máscara de afinidad proporcionada no necesita ser un subconjunto de la máscara de afinidad en proceso. La afinidad en proceso se actualizará en caso necesario.|  
|[swap (Función)](concurrency-namespace-functions.md#swap)|Intercambia los elementos de dos objetos `concurrent_vector`.|  
|[task_from_exception () (función) (Runtime de simultaneidad)](concurrency-namespace-functions.md#task_from_exception)||  
|[task_from_result () (función) (Runtime de simultaneidad)](concurrency-namespace-functions.md#task_from_result)||  
|[Trace_agents_register_name (función)](concurrency-namespace-functions.md#trace_agents_register_name)|Asocia el nombre dado al bloque o agente de mensajes en el seguimiento ETW.|  
|[try_receive (función)](concurrency-namespace-functions.md#try_receive)|Sobrecargado. Una implementación try-receive general, que permite a un contexto buscar datos exactamente de un origen y filtrar los valores que se aceptan. Si los datos no están listos, este método devolverá false.|  
|[Wait (función)](concurrency-namespace-functions.md#wait)|Hace una pausa en el contexto actual para un periodo de tiempo indicado.|  
|[when_all (función)](concurrency-namespace-functions.md#when_all)|Crea una tarea que se completará correctamente cuando todas las tareas proporcionadas como argumentos se completen correctamente.|  
|[when_any (función)](concurrency-namespace-functions.md#when_any)|Sobrecargado. Crea una tarea que se completará correctamente cuando cualquiera de las tareas proporcionadas como argumentos se complete correctamente.|  
  
### <a name="operators"></a>Operadores  
  
|Name|Descripción|  
|----------|-----------------| 
|[operator!=](concurrency-namespace-operators.md#operator_neq)|Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador no es igual al objeto `concurrent_vector` del lado derecho.|  
|[operator&&](concurrency-namespace-operators.md#operator_amp_amp)|Sobrecargado. Crea una tarea que se completará correctamente cuando las tareas proporcionadas como argumentos se completen correctamente.|  
|[operator&#124;&#124;](concurrency-namespace-operators.md#operator_lor)|Sobrecargado. Crea una tarea que se completará correctamente cuando una de las tareas proporcionadas como argumentos se complete correctamente.|  
|[operator<](concurrency-namespace-operators.md#operator_lt)|Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es menor que el objeto `concurrent_vector` del lado derecho.|  
|[operator<=](concurrency-namespace-operators.md#operator_lt_eq)|Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es menor o igual que el objeto `concurrent_vector` del lado derecho.|  
|[operator==](concurrency-namespace-operators.md#operator_eq_eq)|Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es igual al objeto `concurrent_vector` del lado derecho.|  
|[operator>](concurrency-namespace-operators.md#operator_gt)|Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es mayor que el objeto `concurrent_vector` del lado derecho.|  
|[operator>=](concurrency-namespace-operators.md#operator_lt_eq)|Comprueba si el objeto `concurrent_vector` en el lado izquierdo del operador es mayor o igual que el objeto `concurrent_vector` del lado derecho.|  
  
### <a name="constants"></a>Constantes  
  
|Name|Descripción|  
|----------|-----------------|  
|[AgentEventGuid](concurrency-namespace-constants1.md#agenteventguid)|Un identificador GUID de categoría ({B9B5B78C-0713-4898-A21A-C67949DCED07}) que describe los eventos ETW desencadenados por la Biblioteca de agentes en el runtime de simultaneidad.|  
|[ChoreEventGuid](concurrency-namespace-constants1.md#choreeventguid)|Un identificador GUID de categoría que describe eventos ETW desencadenados por el runtime de simultaneidad que están directamente relacionados con quehaceres o tareas.|  
|[ConcRT_ProviderGuid](concurrency-namespace-constants1.md#concrt_providerguid)|El GUID del proveedor de ETW para el runtime de simultaneidad.|  
|[CONCRT_RM_VERSION_1](concurrency-namespace-constants1.md#concrt_rm_version_1)|Indica la compatibilidad de la interfaz del Administrador de recursos definida en Visual Studio 2010.|  
|[ConcRTEventGuid](concurrency-namespace-constants1.md#concrteventguid)|Un identificador GUID de categoría que describe eventos ETW desencadenados por el runtime de simultaneidad que otra categoría ya no describe específicamente.|  
|[ContextEventGuid](concurrency-namespace-constants1.md#contexteventguid)|Un identificador GUID de categoría que describe eventos ETW desencadenados por el runtime de simultaneidad que están directamente relacionados con contextos.|  
|[COOPERATIVE_TIMEOUT_INFINITE](concurrency-namespace-constants1.md#cooperative_timeout_infinite)|Valor que indica que una espera nunca debe agotar el tiempo de espera.|  
|[COOPERATIVE_WAIT_TIMEOUT](concurrency-namespace-constants1.md#cooperative_wait_timeout)|Valor que indica que se ha agotado el tiempo de espera.|  
|[INHERIT_THREAD_PRIORITY](concurrency-namespace-constants1.md#inherit_thread_priority)|Valor especial para la clave de la directiva `ContextPriority` que indica que la prioridad del subproceso de todos los contextos en el programador debe ser la misma que la del subproceso que creó el programador.|  
|[LockEventGuid](concurrency-namespace-constants1.md#lockeventguid)|Un identificador GUID de categoría que describe eventos ETW desencadenados por el runtime de simultaneidad que están directamente relacionados con bloqueos.|  
|[MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources)|Valor especial para las claves `MinConcurrency` y `MaxConcurrency` de la directiva. Tiene como valor predeterminado el número de subprocesos de hardware en el equipo si no existen otras restricciones.|  
|[PPLParallelForeachEventGuid](concurrency-namespace-constants1.md#pplparallelforeacheventguid)|Un identificador GUID de categoría que describe eventos ETW desencadenados por el runtime de simultaneidad que están directamente relacionados con el uso de la función `parallel_for_each`.|  
|[PPLParallelForEventGuid](concurrency-namespace-constants1.md#pplparallelforeventguid)|Un identificador GUID de categoría que describe eventos ETW desencadenados por el runtime de simultaneidad que están directamente relacionados con el uso de la función `parallel_for`.|  
|[PPLParallelInvokeEventGuid](concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|Un identificador GUID de categoría que describe eventos ETW desencadenados por el runtime de simultaneidad que están directamente relacionados con el uso de la función `parallel_invoke`.|  
|[ResourceManagerEventGuid](concurrency-namespace-constants1.md#resourcemanagereventguid)|Un identificador GUID de categoría que describe eventos ETW desencadenados por el runtime de simultaneidad que están directamente relacionados con el administrador de recursos.|  
|[ScheduleGroupEventGuid](concurrency-namespace-constants1.md#schedulegroupeventguid)|Un identificador GUID de categoría que describe eventos ETW desencadenados por el runtime de simultaneidad que están directamente relacionados con grupos de programación.|  
|[SchedulerEventGuid](concurrency-namespace-constants1.md#schedulereventguid)|Un identificador GUID de categoría que describe eventos ETW desencadenados por el runtime de simultaneidad que están directamente relacionados con la actividad del programador.|  
|[VirtualProcessorEventGuid](concurrency-namespace-constants1.md#virtualprocessoreventguid)|Un identificador GUID de categoría que describe eventos ETW desencadenados por el runtime de simultaneidad que están directamente relacionados con los procesadores virtuales.|  
  
## <a name="requirements"></a>Requisitos  
 **Header:** agents.h, concrt.h, concrtrm.h, concurrent_priority_queue.h, concurrent_queue.h, concurrent_unordered_map.h, concurrent_unordered_set.h, concurrent_vector.h, internal_concurrent_hash.h, internal_split_ordered_list.h, ppl.h, pplcancellation_token.h, pplconcrt.h, pplinterface.h, ppltasks.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia](reference-concurrency-runtime.md)

