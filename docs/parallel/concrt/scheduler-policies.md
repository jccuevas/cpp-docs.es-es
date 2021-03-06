---
title: Directivas del programador
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
ms.openlocfilehash: 0f90b461ecba702501c2f6919572dc828c80907f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142283"
---
# <a name="scheduler-policies"></a>Directivas del programador

En este documento se describe el rol de las directivas de programador en el Runtime de simultaneidad. Una *Directiva de Scheduler* controla la estrategia que el programador utiliza cuando administra tareas. Por ejemplo, considere una aplicación que requiere que algunas tareas se ejecuten en `THREAD_PRIORITY_NORMAL` y otras tareas que se ejecutarán en `THREAD_PRIORITY_HIGHEST`.  Puede crear dos instancias de Scheduler: una que especifique el `ContextPriority` Directiva que se va a `THREAD_PRIORITY_NORMAL` y otra que especifique la misma directiva que se va a `THREAD_PRIORITY_HIGHEST`.

Mediante el uso de directivas de Scheduler, puede dividir los recursos de procesamiento disponibles y asignar un conjunto fijo de recursos a cada programador. Por ejemplo, considere un algoritmo paralelo que no se escala más allá de cuatro procesadores. Puede crear una directiva de programador que limite sus tareas para que no use más de cuatro procesadores simultáneamente.

> [!TIP]
> El Runtime de simultaneidad proporciona un programador predeterminado. Por lo tanto, no tiene que crear una en la aplicación. Dado que el Programador de tareas le ayuda a ajustar el rendimiento de las aplicaciones, se recomienda empezar con la biblioteca de [patrones de procesamiento paralelo (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o la [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si no está familiarizado con la Runtime de simultaneidad.

Cuando se usa el método [Concurrency:: CurrentScheduler:: Create](reference/currentscheduler-class.md#create), [Concurrency:: Scheduler:: Create](reference/scheduler-class.md#create)o [Concurrency:: Scheduler:: SetDefaultSchedulerPolicy (](reference/scheduler-class.md#setdefaultschedulerpolicy) para crear una instancia de Scheduler, se proporciona un objeto [Concurrency:: SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) que contiene una colección de pares clave-valor que especifican el comportamiento del programador. El constructor `SchedulerPolicy` toma un número variable de argumentos. El primer argumento es el número de elementos de directiva que va a especificar. Los argumentos restantes son pares de clave y valor para cada elemento de directiva. En el ejemplo siguiente se crea un objeto `SchedulerPolicy` que especifica tres elementos de directiva. El Runtime usa valores predeterminados para las claves de directiva que no se especifican.

[!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]

La enumeración [Concurrency::P olicyelementkey](reference/concurrency-namespace-enums.md#policyelementkey) define las claves de directiva que están asociadas a la programador de tareas. En la tabla siguiente se describen las claves de directiva y el valor predeterminado que el Runtime usa para cada una de ellas.

|Clave de Directiva|Descripción|Valor predeterminado|
|----------------|-----------------|-------------------|
|`SchedulerKind`|Un valor [Concurrency:: schedulertype (](reference/concurrency-namespace-enums.md#schedulertype) que especifica el tipo de subprocesos que se va a usar para programar tareas.|`ThreadScheduler` (usar subprocesos normales). Este es el único valor válido para esta clave.|
|`MaxConcurrency`|`unsigned int` valor que especifica el número máximo de recursos de simultaneidad que usa el programador.|[Concurrency:: Maxexecutionresources (](reference/concurrency-namespace-constants1.md#maxexecutionresources)|
|`MinConcurrency`|`unsigned int` valor que especifica el número mínimo de recursos de simultaneidad que usa el programador.|`1`|
|`TargetOversubscriptionFactor`|`unsigned int` valor que especifica el número de subprocesos que se van a asignar a cada recurso de procesamiento.|`1`|
|`LocalContextCacheSize`|`unsigned int` valor que especifica el número máximo de contextos que se pueden almacenar en caché en la cola local de cada procesador virtual.|`8`|
|`ContextStackSize`|`unsigned int` valor que especifica el tamaño de la pila, en kilobytes, que se va a reservar para cada contexto.|`0` (usar el tamaño de pila predeterminado)|
|`ContextPriority`|Un valor `int` que especifica la prioridad del subproceso de cada contexto. Puede ser cualquier valor que se puede pasar a [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) o `INHERIT_THREAD_PRIORITY`.|`THREAD_PRIORITY_NORMAL`|

|`SchedulingProtocol`| Un valor [Concurrency:: schedulingprotocoltype (](reference/concurrency-namespace-enums.md#schedulingprotocoltype) que especifica el algoritmo de programación que se va a usar. |`EnhanceScheduleGroupLocality`| |`DynamicProgressFeedback`| Un valor de [Concurrency::D ynamicprogressfeedbacktype](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype) que especifica si se deben reequilibrar los recursos según la información de progreso basada en estadísticas.<br /><br /> **Nota:** No establezca esta directiva en `ProgressFeedbackDisabled` porque está reservada para su uso en tiempo de ejecución. |`ProgressFeedbackEnabled`|

Cada programador utiliza su propia Directiva al programar tareas. Las directivas que están asociadas a un programador no afectan al comportamiento de ningún otro programador. Además, no se puede cambiar la Directiva de Scheduler después de crear el objeto de `Scheduler`.

> [!IMPORTANT]
> Use solo las directivas de programador para controlar los atributos de los subprocesos que crea el motor en tiempo de ejecución. No cambie la afinidad de subprocesos o la prioridad de los subprocesos creados por el tiempo de ejecución, ya que esto podría provocar un comportamiento indefinido.

El tiempo de ejecución crea un programador predeterminado si no se crea uno explícitamente. Si desea usar el programador predeterminado en la aplicación, pero desea especificar una directiva para que la use ese programador, llame al método [Concurrency:: Scheduler:: SetDefaultSchedulerPolicy (](reference/scheduler-class.md#setdefaultschedulerpolicy) antes de programar el trabajo paralelo. Si no llama al método `Scheduler::SetDefaultSchedulerPolicy`, el motor en tiempo de ejecución utiliza los valores de directiva predeterminados de la tabla.

Use los métodos [Concurrency:: CurrentScheduler:: getpolicy](reference/currentscheduler-class.md#getpolicy) y [Concurrency:: Scheduler:: GetPolicy](reference/scheduler-class.md#getpolicy) para recuperar una copia de la Directiva del programador. Los valores de directiva que se reciben de estos métodos pueden diferir de los valores de directiva que se especifican al crear el programador.

## <a name="example"></a>Ejemplo

Para examinar ejemplos que usan directivas de programador específicas para controlar el comportamiento del programador, consulte [Cómo: especificar directivas de programador específicas](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md) y [Cómo: crear agentes que usen directivas de programador específicas](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).

## <a name="see-also"></a>Consulte también

[Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Procedimiento para especificar directivas de Scheduler concretas](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br/>
[Procedimiento para crear agentes que usen directivas de Scheduler concretas](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
