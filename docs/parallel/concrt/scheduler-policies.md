---
title: Directivas de Scheduler
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
ms.openlocfilehash: e2acfc199e7ad9edf3965dc8ccb4103eb615a66b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408009"
---
# <a name="scheduler-policies"></a>Directivas de Scheduler

Este documento describe el rol de las directivas del programador del Runtime de simultaneidad. Un *directiva de programador* controla la estrategia que el programador utiliza cuando administra tareas. Por ejemplo, considere una aplicación que requiere algunas tareas que se ejecutan en `THREAD_PRIORITY_NORMAL` y otras tareas que se ejecutan en `THREAD_PRIORITY_HIGHEST`.  Puede crear dos instancias del programador: uno que especifica el `ContextPriority` directiva sea `THREAD_PRIORITY_NORMAL` y otro que especifica la misma directiva para que sea `THREAD_PRIORITY_HIGHEST`.

Mediante el uso de directivas del programador, puede dividir los recursos de procesamiento disponibles y asignar un conjunto fijo de recursos a cada programador. Por ejemplo, considere un algoritmo paralelo que no se escala más allá de cuatro procesadores. Puede crear una directiva de programador que limite las tareas para utilizar no más de cuatro procesadores simultáneamente.

> [!TIP]
>  El Runtime de simultaneidad proporciona a un programador predeterminado. Por lo tanto, no tienes que crear una cuenta en la aplicación. Dado que el programador de tareas le ayuda a ajustar el rendimiento de las aplicaciones, es recomendable que comience con la [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si es nuevo en el Runtime de simultaneidad.

Cuando se usa el [concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create), [concurrency::Scheduler::Create](reference/scheduler-class.md#create), o [concurrency::Scheduler::SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) método para crear una instancia del programador, proporciona un [Concurrency:: SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) objeto que contiene una colección de pares clave-valor que especifican el comportamiento del programador. El `SchedulerPolicy` constructor toma un número variable de argumentos. El primer argumento es el número de elementos de directiva que se va a especificar. Los argumentos restantes son pares de clave y valor para cada elemento de directiva. En el ejemplo siguiente se crea un `SchedulerPolicy` objeto que especifica tres elementos de directiva. El tiempo de ejecución usa valores predeterminados para las claves de directiva que no se especifican.

[!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]

El [concurrency::PolicyElementKey](reference/concurrency-namespace-enums.md#policyelementkey) enumeración define las claves de directiva que están asociadas con el programador de tareas. En la tabla siguiente se describe las claves de directiva y el valor predeterminado que usa el tiempo de ejecución para cada uno de ellos.

|Clave de la directiva|Descripción|Valor predeterminado|
|----------------|-----------------|-------------------|
|`SchedulerKind`|Un [concurrency::SchedulerType](reference/concurrency-namespace-enums.md#schedulertype) valor que especifica el tipo de subprocesos que se utilizarán para programar tareas.|`ThreadScheduler` (use subprocesos normales). Este es el único valor válido para esta clave.|
|`MaxConcurrency`|Un `unsigned int` valor que especifica el número máximo de recursos de simultaneidad que usa el programador.|[concurrency::MaxExecutionResources](reference/concurrency-namespace-constants1.md#maxexecutionresources)|
|`MinConcurrency`|Un `unsigned int` valor que especifica el número mínimo de recursos de simultaneidad que usa el programador.|`1`|
|`TargetOversubscriptionFactor`|Un `unsigned int` valor que especifica cuántos subprocesos se asignan a cada recurso de procesamiento.|`1`|
|`LocalContextCacheSize`|Un `unsigned int` valor que especifica el número máximo de contextos que pueden almacenarse en caché en la cola local de cada procesador virtual.|`8`|
|`ContextStackSize`|Un `unsigned int` valor que especifica el tamaño de la pila, en kilobytes, que se reserva para cada contexto.|`0` (use el tamaño de pila predeterminado)|
|`ContextPriority`|Un `int` valor que especifica la prioridad del subproceso de cada contexto. Esto puede ser cualquier valor que se puede pasar a [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) o `INHERIT_THREAD_PRIORITY`.|`THREAD_PRIORITY_NORMAL`|

|`SchedulingProtocol`| Un [concurrency::SchedulingProtocolType](reference/concurrency-namespace-enums.md#schedulingprotocoltype) valor que especifica el algoritmo de programación para usar. | `EnhanceScheduleGroupLocality`| | `DynamicProgressFeedback`| Un [concurrency::DynamicProgressFeedbackType](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype) valor que especifica si se va a equilibrar los recursos según la información de progreso basada en las estadísticas.<br /><br /> **Tenga en cuenta** no establezca esta directiva en `ProgressFeedbackDisabled` porque está reservado para su uso por el tiempo de ejecución. |`ProgressFeedbackEnabled`|

Cada programador utiliza su propia directiva al programar tareas. Las directivas que están asociadas a un programador no afectan el comportamiento de cualquier otro programador. Además, no se puede cambiar la directiva del programador después de crear el `Scheduler` objeto.

> [!IMPORTANT]
>  Usar solo las directivas de programador para controlar los atributos para los subprocesos que crea el tiempo de ejecución. No cambie la afinidad de subprocesos o la prioridad de subprocesos creados por el tiempo de ejecución ya que podría provocar un comportamiento indefinido.

El runtime crea a un programador predeterminado si no crea explícitamente una. Si desea usar el programador predeterminado en la aplicación, pero desea especificar una directiva de programador usar, llame a la [concurrency::Scheduler::SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) método antes de programar el trabajo paralelo. Si no se llama el `Scheduler::SetDefaultSchedulerPolicy` método, el tiempo de ejecución utiliza la directiva predeterminada de los valores de la tabla.

Use la [concurrency::CurrentScheduler::GetPolicy](reference/currentscheduler-class.md#getpolicy) y [concurrency::Scheduler::GetPolicy](reference/scheduler-class.md#getpolicy) métodos para recuperar una copia de la directiva del programador. Los valores de directiva que reciben de estos métodos pueden diferir de los valores de directiva que especifique cuando se crea el programador.

## <a name="example"></a>Ejemplo

Para examinar ejemplos que usan directivas de programador específicas para controlar el comportamiento del programador, vea [Cómo: Especificar directivas de programador específicas](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md) y [Cómo: Crear agentes que usen directivas de programador específicas](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).

## <a name="see-also"></a>Vea también

[Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Cómo: Especificar directivas de Scheduler concretas](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br/>
[Cómo: Crear agentes que usen directivas de programador específicas](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
