---
title: Las directivas del programador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d9c855260df34290d01f1eeeee89e8bfe8988de
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="scheduler-policies"></a>Directivas de Scheduler
Este documento describe el rol de las directivas del programador en el Runtime de simultaneidad. A *directiva de programador* controla la estrategia que el programador utiliza cuando administra tareas. Por ejemplo, considere una aplicación que requiere algunas tareas que se ejecutan en `THREAD_PRIORITY_NORMAL` y otras tareas que se ejecutan en `THREAD_PRIORITY_HIGHEST`.  Puede crear dos instancias del programador: uno que especifica la `ContextPriority` directiva sea `THREAD_PRIORITY_NORMAL` y otro que especifica la misma directiva para que sea `THREAD_PRIORITY_HIGHEST`.  
  
 Mediante el uso de las directivas del programador, puede dividir los recursos de procesamiento disponibles y asignar un conjunto fijo de recursos a cada programador. Por ejemplo, considere un algoritmo paralelo que no se escala más allá de cuatro procesadores. Puede crear una directiva de programador que limite las tareas para utilizar no más de cuatro procesadores simultáneamente.  
  
> [!TIP]
>  El Runtime de simultaneidad proporciona a un programador predeterminado. Por lo tanto, no tienes que crear uno en la aplicación. Dado que el programador de tareas permite ajustar el rendimiento de las aplicaciones, es recomendable que comience con la [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si está nuevo para el Runtime de simultaneidad.  
  
 Cuando se usa el [concurrency::CurrentScheduler::Create](reference/currentscheduler-class.md#create), [concurrency::Scheduler::Create](reference/scheduler-class.md#create), o [concurrency::Scheduler::SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) método para crear una instancia del programador, proporcione un [Concurrency:: SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) objeto que contiene una colección de pares clave-valor que especifican el comportamiento del programador. El `SchedulerPolicy` constructor toma un número variable de argumentos. El primer argumento es el número de elementos de directiva que va a especificar. Los argumentos restantes son pares clave / valor para cada elemento de directiva. En el ejemplo siguiente se crea un `SchedulerPolicy` objeto que especifica tres elementos de directiva. El runtime usa valores predeterminados para las claves de directiva que no se especifican.  

  
 [!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]  
  

 El [concurrency::PolicyElementKey](reference/concurrency-namespace-enums.md#policyelementkey) enumeración define las claves de directiva que están asociadas con el programador de tareas. La tabla siguiente describen las claves de directiva y el valor predeterminado que el runtime usa para cada uno de ellos.  
  
|Clave de directiva|Descripción|Valor predeterminado|  
|----------------|-----------------|-------------------|  
|`SchedulerKind`|A [concurrency::SchedulerType](reference/concurrency-namespace-enums.md#schedulertype) valor que especifica el tipo de subprocesos que se utilizarán para programar tareas.|`ThreadScheduler` (usa subprocesos normales). Este es el único valor válido para esta clave.|  
|`MaxConcurrency`|Un `unsigned int` valor que especifica el número máximo de recursos de simultaneidad que el programador utiliza.|[Concurrency::MaxExecutionResources](reference/concurrency-namespace-constants1.md#maxexecutionresources)|  
|`MinConcurrency`|Un `unsigned int` valor que especifica el número mínimo de recursos de simultaneidad que el programador utiliza.|`1`|  
|`TargetOversubscriptionFactor`|Un `unsigned int` valor que especifica cuántos subprocesos se asignan a cada recurso de procesamiento.|`1`|  
|`LocalContextCacheSize`|Un `unsigned int` valor que especifica el número máximo de contextos que pueden almacenarse en caché en la cola local de cada procesador virtual.|`8`|  
|`ContextStackSize`|Un `unsigned int` valor que especifica el tamaño de la pila, en kilobytes, que se reserva para cada contexto.|`0` (use el tamaño de pila predeterminado)|  
|`ContextPriority`|Un `int` valor que especifica la prioridad del subproceso de cada contexto. Esto puede ser cualquier valor que se puede pasar a [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) o `INHERIT_THREAD_PRIORITY`.|`THREAD_PRIORITY_NORMAL`|  

|`SchedulingProtocol`| A [concurrency::SchedulingProtocolType](reference/concurrency-namespace-enums.md#schedulingprotocoltype) valor que especifica el algoritmo de programación para usar. |`EnhanceScheduleGroupLocality`|  
|`DynamicProgressFeedback`| A [concurrency::DynamicProgressFeedbackType](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype) valor que especifica si se va a equilibrar los recursos según la información de progreso basada en estadísticas.<br /><br /> **Tenga en cuenta** no establezca esta directiva en `ProgressFeedbackDisabled` porque está reservada para su uso en tiempo de ejecución. |`ProgressFeedbackEnabled`|  

  
 Cada programador utiliza su propia directiva al programar tareas. Las directivas que están asociadas a un programador no afectan al comportamiento de cualquier otro programador. Además, no se puede cambiar la directiva del programador después de crear el `Scheduler` objeto.  
  
> [!IMPORTANT]
>  Usar solo las directivas del programador para controlar los atributos para los subprocesos creados por el tiempo de ejecución. No cambie la afinidad de subprocesos o la prioridad de subprocesos que se crean en tiempo de ejecución, ya que podría provocar un comportamiento indefinido.  
  
 El runtime crea a un programador predeterminado si no crea explícitamente una. Si desea usar el programador predeterminado en la aplicación, pero desea especificar una directiva de programador a la utilice, llame a la [concurrency::Scheduler::SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) método para programar el trabajo paralelo. Si no se llama a la  `Scheduler::SetDefaultSchedulerPolicy` /método siguiente, el tiempo de ejecución utiliza la directiva predeterminada de los valores de la tabla.  
  
 Use la [concurrency::CurrentScheduler::GetPolicy](reference/currentscheduler-class.md#getpolicy) y [concurrency::Scheduler::GetPolicy](reference/scheduler-class.md#getpolicy) métodos para recuperar una copia de la directiva del programador. Los valores de directiva que reciben de estos métodos pueden diferir de los valores de directiva que especifican cuando se crea el programador.  
  
## <a name="example"></a>Ejemplo  
 Para examinar ejemplos que utilizan directivas de programador concretas para controlar el comportamiento del programador, consulte [Cómo: especificar directivas de programador específicas](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md) y [Cómo: crear agentes que Use Specific Scheduler Policies](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).  
  
## <a name="see-also"></a>Vea también  
 [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Cómo: especificar directivas de programador específicas](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)   
 [Procedimiento para crear agentes que usen directivas de Scheduler concretas](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)

