---
title: Instancias del programador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scheduler instances
ms.assetid: 4819365f-ef99-49cc-963e-50a2a35a8d6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f09a5708fd9140619eea60fb8e483c2e26165d1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="scheduler-instances"></a>Instancias de Scheduler
Este documento describe el rol de instancias del programador en el Runtime de simultaneidad y cómo usar el [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) y [Concurrency:: CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) clases para crear y administrar instancias del programador. Instancias del programador son útiles cuando desea asociar directivas de programación explícitas con tipos concretos de cargas de trabajo. Por ejemplo, puede crear una instancia de programador para ejecutar algunas tareas con una prioridad elevada de subproceso y usar el programador predeterminado para ejecutar con otras tareas con la prioridad normal de subproceso.  
  
> [!TIP]
>  Runtime de simultaneidad proporciona un programador predeterminado, por lo que no deberá crear uno en la aplicación. Dado que el programador de tareas permite ajustar el rendimiento de las aplicaciones, es recomendable que comience con la [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si está nuevo para el Runtime de simultaneidad.  
  
##  <a name="top"></a> Secciones  
  
-   [Las clases CurrentScheduler y Scheduler](#classes)  
  
-   [Crear una instancia del programador](#creating)  
  
-   [Administrar la duración de una instancia del programador](#managing)  
  
-   [Métodos y características](#features)  
  
-   [Ejemplo](#example)  
  
##  <a name="classes"></a> Las clases CurrentScheduler y Scheduler  
 El programador de tareas permite a las aplicaciones usar uno o varios *instancias del programador* para programar el trabajo. El [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) clase representa una instancia del programador y encapsula la funcionalidad relacionada con la programación de tareas.  
  
 Un subproceso que se adjunta a un programador se conoce como un *contexto de ejecución*, o simplemente *contexto*. Un programador puede estar activo en el contexto actual en cualquier momento. El programador activo también es conocido como el *programador actual*. El Runtime de simultaneidad usa el [Concurrency:: CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) clase para proporcionar acceso al programador actual. El programador actual para un contexto puede ser diferente del programador actual de otro contexto. El tiempo de ejecución no proporciona una representación de nivel de proceso del programador actual.  
  
 Normalmente, la `CurrentScheduler` clase se utiliza para acceder al programador actual. La `Scheduler` clase es útil cuando se necesita para administrar un programador que no es el actual.  
  
 Las secciones siguientes describen cómo crear y administrar una instancia del programador. Para obtener un ejemplo completo que se muestra las tareas, consulte [Cómo: administrar una instancia del programador](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).  
  
 [[Arriba](#top)]  
  
##  <a name="creating"></a> Crear una instancia del programador  
 Hay tres maneras de crear un `Scheduler` objeto:  
  
-   Si no existe ningún programador, el runtime crea a un programador predeterminado automáticamente cuando se usa la funcionalidad en tiempo de ejecución, por ejemplo, un algoritmo paralelo, para realizar el trabajo. El programador predeterminado se convierte en el programador actual para el contexto que inicia el trabajo paralelo.  
  

-   El [concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create) método crea un `Scheduler` objeto que utiliza una directiva concreta y asocia ese programador con el contexto actual.  
  
-   El [concurrency::Scheduler::Create](reference/scheduler-class.md#create) método crea un `Scheduler` objeto que usa una directiva específica, pero no lo asocia con el contexto actual.  

  
 Permitir que el runtime cree a un programador predeterminado permite que todas las tareas simultáneas compartan el mismo programador. Por lo general, la funcionalidad proporcionada por el [Parallel Patterns Library](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) o la [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) se usa para realizar el trabajo paralelo. Por lo tanto, no es necesario trabajar directamente con el programador para controlar su directiva o duración. Cuando se usa la biblioteca PPL o la biblioteca de agentes, el runtime crea al programador predeterminado si no existe y hace que el programador actual para cada contexto. Al crear a un programador y lo ha configurado como el programador actual, el tiempo de ejecución usa a ese programador para programar tareas. Crear instancias adicionales del programador solo cuando necesite una directiva de programación específica. Para obtener más información acerca de las directivas que están asociadas a un programador, consulte [directivas del programador](../../parallel/concrt/scheduler-policies.md).  
  
 [[Arriba](#top)]  
  
##  <a name="managing"></a> Administrar la duración de una instancia del programador  
 El runtime usa un mecanismo de recuento de referencias para controlar la duración de `Scheduler` objetos.  
  

 Cuando se usa el `CurrentScheduler::Create` método o la `Scheduler::Create` método para crear un `Scheduler` de objeto, el tiempo de ejecución establece el recuento de referencias inicial de ese programador en uno. El tiempo de ejecución incrementa el recuento de referencias cuando se llama a la [concurrency::Scheduler::Attach](reference/scheduler-class.md#attach) método. El `Scheduler::Attach` método asocia la `Scheduler` objeto junto con el contexto actual. Esto hace que el programador actual. Cuando se llama a la `CurrentScheduler::Create` método, el runtime crea un `Scheduler` de objeto y lo adjunta al contexto actual (y establece el recuento de referencias en uno). También puede usar el [concurrency::Scheduler::Reference](reference/scheduler-class.md#reference) método para incrementar el recuento de referencias de un `Scheduler` objeto.  
  
 El runtime disminuye el recuento de referencias cuando se llama a la [concurrency::CurrentScheduler::Detach](reference/currentscheduler-class.md#detach) método para desasociar el programador actual, o llamar a la [concurrency::Scheduler::Release](reference/scheduler-class.md#release) método. Cuando el recuento de referencias llega a cero, el runtime destruye la `Scheduler` objeto después de que todos programado finalizar las tareas. Una tarea en ejecución se puede incrementar el recuento de referencias del programador actual. Por lo tanto, si el recuento de referencias llega a cero y una tarea incrementa el recuento de referencias, el runtime no destruye el `Scheduler` objeto hasta que el recuento de referencias llega a cero nuevo y finalizan todas las tareas.  

  
 El tiempo de ejecución mantiene una pila interna de `Scheduler` objetos para cada contexto. Cuando se llama a la `Scheduler::Attach` o `CurrentScheduler::Create` (método), el runtime inserciones que `Scheduler` objeto en la pila para el contexto actual. Esto hace que el programador actual. Cuando se llama a `CurrentScheduler::Detach`, el tiempo de ejecución extrae el programador actual de la pila para el contexto actual y establece el anterior como programador actual.  
  
 El runtime proporciona varias maneras de administrar la duración de una instancia del programador. En la tabla siguiente se muestra el método adecuado que libera o desasocia al programador del contexto actual para cada método que crea o adjunta a un programador al contexto actual.  
  
|Crear o attach (método)|La versión o detach (método)|  
|-----------------------------|------------------------------|  
|`CurrentScheduler::Create`|`CurrentScheduler::Detach`|  
|`Scheduler::Create`|`Scheduler::Release`|  
|`Scheduler::Attach`|`CurrentScheduler::Detach`|  
|`Scheduler::Reference`|`Scheduler::Release`|  
  
 Al llamar a la inapropiado de la versión o separar el método produce un comportamiento no especificado en el tiempo de ejecución.  
  
 Si utiliza la funcionalidad, por ejemplo, la biblioteca PPL, que hace que el runtime cree al programador predeterminado para usted, no de la versión o separar a este programador. El runtime administra la duración de cualquier programador que crea.  
  

 Dado que el runtime no destruye un `Scheduler` objeto antes de que han terminado de todas las tareas, puede usar el [concurrency::Scheduler::RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent) método o la [Concurrency:: CurrentScheduler:: RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent) método para recibir una notificación cuando un `Scheduler` se destruye el objeto. Esto es útil cuando debe esperar a que todas las tareas que se programa por un `Scheduler` objeto que se va a finalizar.  
  
 [[Arriba](#top)]  
  
##  <a name="features"></a> Métodos y características  
 En esta sección se resume los métodos importantes de la `CurrentScheduler` y `Scheduler` clases.  
  
 Piense en la `CurrentScheduler` clase como una aplicación auxiliar para crear un programador para su uso en el contexto actual. La `Scheduler` clase le permite controlar un programador que pertenece a otro contexto.  
  
 La tabla siguiente muestran los métodos importantes que se definen mediante la `CurrentScheduler` clase.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Crear](reference/currentscheduler-class.md#create)|Crea un `Scheduler` objeto que usa la directiva especificada y lo asocia con el contexto actual.|  
|[Get](reference/currentscheduler-class.md#get)|Recupera un puntero a la `Scheduler` objeto que está asociado con el contexto actual. Este método no incrementa el recuento de referencias de la `Scheduler` objeto.|  
|[Desasociar](reference/currentscheduler-class.md#detach)|Desasocia al programador actual desde el contexto actual y establece el anterior como programador actual.|  
|[RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent)|Registra un evento que el runtime establece cuando se destruya el programador actual.|  
|[CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup)|Crea un [Concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objeto en el programador actual.|  
|[ScheduleTask](reference/currentscheduler-class.md#scheduletask)|Agrega una tarea ligera a la cola de programación del programador actual.|  
|[GetPolicy](reference/currentscheduler-class.md#getpolicy)|Recupera una copia de la directiva que está asociada con el programador actual.|  
  
 La tabla siguiente muestran los métodos importantes que se definen mediante la `Scheduler` clase.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Crear](reference/scheduler-class.md#create)|Crea un `Scheduler` objeto que usa la directiva especificada.|  
|[Asociar](reference/scheduler-class.md#attach)|Asocia la `Scheduler` objeto junto con el contexto actual.|  
|[Referencia](reference/scheduler-class.md#reference)|Incrementa el contador de referencia de la `Scheduler` objeto.|  
|[Release](reference/scheduler-class.md#release)|Disminuye el contador de referencia de la `Scheduler` objeto.|  
|[RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent)|Registra un evento que el runtime establece cuando el `Scheduler` se destruye el objeto.|  
|[CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup)|Crea un [Concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objeto en el `Scheduler` objeto.|  
|[ScheduleTask](reference/scheduler-class.md#scheduletask)|Programa una tarea ligera desde el `Scheduler` objeto.|  
|[GetPolicy](reference/scheduler-class.md#getpolicy)|Recupera una copia de la directiva que está asociada el `Scheduler` objeto.|  
|[SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy)|Establece la directiva en tiempo de ejecución que se usará cuando crea el programador predeterminado.|  
|[ResetDefaultSchedulerPolicy](reference/scheduler-class.md#resetdefaultschedulerpolicy)|Restaura la directiva predeterminada a la que estaba activa antes de llamar a `SetDefaultSchedulerPolicy`. Si el programador predeterminado se crea después de esta llamada, el runtime usa la configuración de directiva predeterminada para crear al programador.|  

  
 [[Arriba](#top)]  
  
##  <a name="example"></a> Ejemplo  
 Para obtener ejemplos básicos de cómo crear y administrar una instancia del programador, consulte [Cómo: administrar una instancia del programador](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).  
  
## <a name="see-also"></a>Vea también  
 [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Cómo: administrar una instancia del programador](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)   
 [Directivas del programador](../../parallel/concrt/scheduler-policies.md)   
 [Grupos de programación](../../parallel/concrt/schedule-groups.md)

