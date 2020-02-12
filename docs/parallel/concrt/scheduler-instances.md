---
title: Instancias del programador
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler instances
ms.assetid: 4819365f-ef99-49cc-963e-50a2a35a8d6b
ms.openlocfilehash: e9e9b8124254084ac30191d37d49f2ef72bd677e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142294"
---
# <a name="scheduler-instances"></a>Instancias del programador

En este documento se describe el rol de las instancias de Scheduler en el Runtime de simultaneidad y cómo usar las clases [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) y [Concurrency:: CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) para crear y administrar instancias de Scheduler. Las instancias de Scheduler son útiles cuando se desea asociar directivas de programación explícitas a tipos específicos de cargas de trabajo. Por ejemplo, puede crear una instancia de programador para ejecutar algunas tareas con una prioridad elevada de subproceso y usar el programador predeterminado para ejecutar con otras tareas con la prioridad normal de subproceso.

> [!TIP]
> Runtime de simultaneidad proporciona un programador predeterminado, por lo que no deberá crear uno en la aplicación. Dado que el Programador de tareas le ayuda a ajustar el rendimiento de las aplicaciones, se recomienda empezar con la biblioteca de [patrones de procesamiento paralelo (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o la [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si no está familiarizado con la Runtime de simultaneidad.

## <a name="top"></a> Secciones

- [Clases Scheduler y CurrentScheduler](#classes)

- [Creación de una instancia de Scheduler](#creating)

- [Administrar la duración de una instancia de Scheduler](#managing)

- [Métodos y características](#features)

- [Ejemplo](#example)

## <a name="classes"></a>Clases Scheduler y CurrentScheduler

El Programador de tareas permite a las aplicaciones usar una o más *instancias de Scheduler* para programar el trabajo. La clase [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) representa una instancia de Scheduler y encapsula la funcionalidad relacionada con las tareas de programación.

Un subproceso que se adjunta a un programador se conoce como *contexto de ejecución*o simplemente *contexto*. Un programador puede estar activo en el contexto actual en cualquier momento. El programador activo también se conoce como *programador actual*. En el Runtime de simultaneidad se usa la clase [Concurrency:: CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) para proporcionar acceso al programador actual. El programador actual para un contexto puede diferir del programador actual para otro contexto. El runtime no proporciona una representación de nivel de proceso del programador actual.

Normalmente, la clase `CurrentScheduler` se utiliza para tener acceso al programador actual. La clase `Scheduler` es útil cuando necesita administrar un programador que no es el actual.

En las secciones siguientes se describe cómo crear y administrar una instancia del programador. Para obtener un ejemplo completo que muestra estas tareas, vea [Cómo: administrar una instancia del programador](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).

[[Arriba](#top)]

## <a name="creating"></a>Creación de una instancia de Scheduler

Existen tres formas de crear un objeto de `Scheduler`:

- Si no existe ningún programador, el tiempo de ejecución crea un programador predeterminado automáticamente cuando se utiliza la funcionalidad en tiempo de ejecución, por ejemplo, un algoritmo paralelo, para realizar el trabajo. El programador predeterminado se convierte en el programador actual para el contexto que inicia el trabajo paralelo.

- El método [Concurrency:: CurrentScheduler:: Create](reference/currentscheduler-class.md#create) crea un objeto `Scheduler` que utiliza una directiva específica y asocia ese programador con el contexto actual.

- El método [Concurrency:: Scheduler:: Create](reference/scheduler-class.md#create) crea un objeto `Scheduler` que utiliza una directiva específica, pero no lo asocia al contexto actual.

Permitir al tiempo de ejecución crear un programador predeterminado permite que todas las tareas simultáneas compartan el mismo programador. Normalmente, la funcionalidad proporcionada por la biblioteca de [patrones de procesamiento paralelo](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) o la [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) se usa para realizar el trabajo paralelo. Por lo tanto, no tiene que trabajar directamente con el programador para controlar su Directiva o duración. Al usar PPL o la biblioteca de agentes, el tiempo de ejecución crea el programador predeterminado si no existe y lo convierte en el programador actual para cada contexto. Cuando se crea un programador y se establece como el programador actual, el Runtime usa ese programador para programar tareas. Cree instancias de programador adicionales solo cuando necesite una directiva de programación específica. Para obtener más información sobre las directivas que están asociadas a un programador, consulte [directivas del programador](../../parallel/concrt/scheduler-policies.md).

[[Arriba](#top)]

## <a name="managing"></a>Administrar la duración de una instancia de Scheduler

El motor en tiempo de ejecución usa un mecanismo de recuento de referencias para controlar la duración de los objetos `Scheduler`.

Cuando se usa el método `CurrentScheduler::Create` o el método `Scheduler::Create` para crear un objeto `Scheduler`, el tiempo de ejecución establece el recuento de referencias inicial de ese programador en uno. El tiempo de ejecución incrementa el recuento de referencias cuando se llama al método [Concurrency:: Scheduler:: Attach](reference/scheduler-class.md#attach) . El método `Scheduler::Attach` asocia el objeto `Scheduler` junto con el contexto actual. Esto lo convierte en el programador actual. Cuando se llama al método `CurrentScheduler::Create`, el tiempo de ejecución crea un objeto `Scheduler` y lo adjunta al contexto actual (y establece el recuento de referencias en uno). También puede utilizar el método [Concurrency:: Scheduler:: Reference](reference/scheduler-class.md#reference) para incrementar el recuento de referencias de un objeto `Scheduler`.

El Runtime reduce el recuento de referencias cuando se llama al método [Concurrency:: CurrentScheduler::D Etach](reference/currentscheduler-class.md#detach) para desasociar el programador actual o llamar al método [Concurrency:: Scheduler:: Release](reference/scheduler-class.md#release) . Cuando el recuento de referencias llega a cero, el tiempo de ejecución destruye el objeto de `Scheduler` una vez finalizadas todas las tareas programadas. Una tarea en ejecución puede incrementar el recuento de referencias del programador actual. Por lo tanto, si el recuento de referencias llega a cero y una tarea incrementa el recuento de referencias, el tiempo de ejecución no destruye el objeto de `Scheduler` hasta que el recuento de referencias no llegue a cero y finalicen todas las tareas.

El tiempo de ejecución mantiene una pila interna de objetos de `Scheduler` para cada contexto. Cuando se llama al método `Scheduler::Attach` o `CurrentScheduler::Create`, el motor en tiempo de ejecución envía ese objeto `Scheduler` en la pila para el contexto actual. Esto lo convierte en el programador actual. Cuando se llama a `CurrentScheduler::Detach`, el tiempo de ejecución extrae el programador actual de la pila para el contexto actual y establece el anterior como el programador actual.

El tiempo de ejecución proporciona varias maneras de administrar la duración de una instancia del programador. En la tabla siguiente se muestra el método adecuado que libera o Desasocia el programador del contexto actual para cada método que crea o adjunta un programador al contexto actual.

|Create o Attach (método)|Release o Detach (método)|
|-----------------------------|------------------------------|
|`CurrentScheduler::Create`|`CurrentScheduler::Detach`|
|`Scheduler::Create`|`Scheduler::Release`|
|`Scheduler::Attach`|`CurrentScheduler::Detach`|
|`Scheduler::Reference`|`Scheduler::Release`|

La llamada al método Release o detach inadecuados produce un comportamiento no especificado en el tiempo de ejecución.

Cuando se usa la funcionalidad, por ejemplo, la biblioteca PPL, que hace que el tiempo de ejecución cree el programador predeterminado automáticamente, no se libera ni se desasocia este programador. El Runtime administra la duración de cualquier programador que cree.

Dado que el runtime no destruye un objeto `Scheduler` antes de que finalicen todas las tareas, puede usar el método [Concurrency:: Scheduler:: RegisterShutdownEvent (](reference/scheduler-class.md#registershutdownevent) o el método [Concurrency:: CurrentScheduler:: RegisterShutdownEvent (](reference/currentscheduler-class.md#registershutdownevent) para recibir una notificación cuando se destruye un objeto `Scheduler`. Esto resulta útil cuando debe esperar a que finalicen todas las tareas programadas por un objeto `Scheduler`.

[[Arriba](#top)]

## <a name="features"></a>Métodos y características

En esta sección se resumen los métodos importantes de las clases `CurrentScheduler` y `Scheduler`.

Piense en la clase `CurrentScheduler` como una aplicación auxiliar para crear un programador para su uso en el contexto actual. La clase `Scheduler` permite controlar un programador que pertenece a otro contexto.

En la tabla siguiente se muestran los métodos importantes definidos por la clase `CurrentScheduler`.

|Método|Descripción|
|------------|-----------------|
|[Creación](reference/currentscheduler-class.md#create)|Crea un objeto `Scheduler` que utiliza la Directiva especificada y lo asocia al contexto actual.|
|[Get](reference/currentscheduler-class.md#get)|Recupera un puntero al objeto `Scheduler` asociado al contexto actual. Este método no incrementa el recuento de referencias del objeto `Scheduler`.|
|[Separar](reference/currentscheduler-class.md#detach)|Desasocia el programador actual del contexto actual y establece el anterior como el programador actual.|
|[RegisterShutdownEvent (](reference/currentscheduler-class.md#registershutdownevent)|Registra un evento que establece el tiempo de ejecución cuando se destruye el programador actual.|
|[Createschedulegroup (](reference/currentscheduler-class.md#createschedulegroup)|Crea un objeto [Concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) en el programador actual.|
|[ScheduleTask (](reference/currentscheduler-class.md#scheduletask)|Agrega una tarea ligera a la cola de programación del programador actual.|
|[Getpolicy (](reference/currentscheduler-class.md#getpolicy)|Recupera una copia de la directiva asociada al programador actual.|

En la tabla siguiente se muestran los métodos importantes definidos por la clase `Scheduler`.

|Método|Descripción|
|------------|-----------------|
|[Creación](reference/scheduler-class.md#create)|Crea un objeto `Scheduler` que utiliza la Directiva especificada.|
|[Adjuntar](reference/scheduler-class.md#attach)|Asocia el objeto `Scheduler` junto con el contexto actual.|
|[Referencia](reference/scheduler-class.md#reference)|Incrementa el contador de referencias del objeto `Scheduler`.|
|[Versión](reference/scheduler-class.md#release)|Disminuye el contador de referencias del objeto `Scheduler`.|
|[RegisterShutdownEvent (](reference/scheduler-class.md#registershutdownevent)|Registra un evento que establece el tiempo de ejecución cuando se destruye el objeto de `Scheduler`.|
|[Createschedulegroup (](reference/scheduler-class.md#createschedulegroup)|Crea un objeto [Concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) en el objeto `Scheduler`.|
|[ScheduleTask (](reference/scheduler-class.md#scheduletask)|Programa una tarea ligera desde el objeto de `Scheduler`.|
|[Getpolicy (](reference/scheduler-class.md#getpolicy)|Recupera una copia de la directiva asociada al objeto de `Scheduler`.|
|[SetDefaultSchedulerPolicy (](reference/scheduler-class.md#setdefaultschedulerpolicy)|Establece la Directiva para el tiempo de ejecución que se va a usar al crear el programador predeterminado.|
|[Resetdefaultschedulerpolicy (](reference/scheduler-class.md#resetdefaultschedulerpolicy)|Restaura la directiva predeterminada a la que estaba activa antes de la llamada a `SetDefaultSchedulerPolicy`. Si se crea el programador predeterminado después de esta llamada, el tiempo de ejecución usa la configuración de directiva predeterminada para crear el programador.|

[[Arriba](#top)]

## <a name="example"></a> Ejemplo

Para obtener ejemplos básicos de cómo crear y administrar una instancia de Scheduler, vea [Cómo: administrar una instancia del programador](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).

## <a name="see-also"></a>Consulte también

[Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Procedimiento para administrar una instancia de Scheduler](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br/>
[Directivas de Scheduler](../../parallel/concrt/scheduler-policies.md)<br/>
[Grupos de programación](../../parallel/concrt/schedule-groups.md)
