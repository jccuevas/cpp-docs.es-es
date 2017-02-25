---
title: "Directivas del programador | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "directivas del programador"
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Directivas del programador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este documento se describe el rol de las directivas de programador en el runtime de simultaneidad.  Una *directiva de programador* controla la estrategia que el programador usa cuando administra tareas.  Por ejemplo, considere una aplicación que requiere algunas tareas de ejecutarse en `THREAD_PRIORITY_NORMAL` y otras tareas se ejecuten en `THREAD_PRIORITY_HIGHEST`.  Puede crear dos instancias del programador: una que especifica la directiva de `ContextPriority` para ser `THREAD_PRIORITY_NORMAL` y otra que especifica la misma directiva para ser `THREAD_PRIORITY_HIGHEST`.  
  
 Mediante directivas de programador, puede dividir los recursos de procesamiento disponibles y asignar un conjunto fijo de recursos a cada programador.  Por ejemplo, considere un algoritmo paralelo que no se amplía para más de cuatro procesadores.  Puede crear una directiva de programador que limite las tareas para que no usen más de cuatro procesadores simultáneamente.  
  
> [!TIP]
>  El runtime de simultaneidad proporciona un programador predeterminado.  Por consiguiente, no tiene que crear uno en la aplicación.  Dado que el programador de tareas ayuda a ajustar el rendimiento de las aplicaciones, se recomienda que comience con [Parallel Patterns Library \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md) o [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si no ha usado antes el runtime de simultaneidad.  
  
 Cuando se utiliza [concurrency::CurrentScheduler::Create](../Topic/CurrentScheduler::Create%20Method.md), [concurrency::Scheduler::Create](../Topic/Scheduler::Create%20Method.md), o un método de [concurrency::Scheduler::SetDefaultSchedulerPolicy](../Topic/Scheduler::SetDefaultSchedulerPolicy%20Method.md) para crear una instancia de programador, se proporciona un objeto de [concurrency::SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) que contiene una colección de pares clave\-valor que especifican el comportamiento del programador.  El constructor `SchedulerPolicy` toma un número variable de argumentos.  El primer argumento es el número de elementos de directiva que está a punto de especificar.  Los argumentos restantes son los pares clave\-valor para cada elemento de directiva.  En el siguiente ejemplo se crea un objeto `SchedulerPolicy` que especifica tres elementos de directiva.  El runtime utiliza los valores predeterminados para las claves de directiva que no se especifican.  
  
 [!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/CPP/scheduler-policies_1.cpp)]  
  
 La enumeración de [concurrency::PolicyElementKey](../Topic/PolicyElementKey%20Enumeration.md) define las claves de directiva asociadas al Programador de tareas.  En la siguiente tabla se describen las claves de directiva y el valor predeterminado que el runtime usa para cada uno de ellos.  
  
|Clave de directiva|Descripción|Valor predeterminado|  
|------------------------|-----------------|--------------------------|  
|`SchedulerKind`|Un valor de [concurrency::SchedulerType](../Topic/SchedulerType%20Enumeration.md) que especifica el tipo de subprocesos para utilizar para programar tareas.|`ThreadScheduler` \(subprocesos normales\).  Éste es el único valor válido para esta clave.|  
|`MaxConcurrency`|Valor `unsigned int` que especifica el número máximo de recursos de simultaneidad que el programador usa.|[concurrency::MaxExecutionResources](../Topic/MaxExecutionResources%20Constant.md)|  
|`MinConcurrency`|Un valor `unsigned int` que especifica el número mínimo de recursos de simultaneidad que el programador utiliza.|`1`|  
|`TargetOversubscriptionFactor`|Un valor `unsigned int` que especifica cuántos subprocesos se asignan a cada recurso de procesamiento.|`1`|  
|`LocalContextCacheSize`|Un valor `unsigned int` que especifica el número máximo de contextos que pueden estar almacenados en memoria caché en la cola local de cada procesador virtual.|`8`|  
|`ContextStackSize`|Un valor `unsigned int` que especifica el tamaño de la pila, en kilobytes, que se reserva para cada contexto.|`0` \(usa el tamaño de pila predeterminado\)|  
|`ContextPriority`|Un valor `int` que especifica la prioridad del subproceso de cada contexto.  Puede ser cualquier valor que se pueda pasar a [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) o `INHERIT_THREAD_PRIORITY`.|`THREAD_PRIORITY_NORMAL`|  
|`SchedulingProtocol`|Un valor de [concurrency::SchedulingProtocolType](../Topic/SchedulingProtocolType%20Enumeration.md) que especifica el algoritmo de programación para utilizar.|`EnhanceScheduleGroupLocality`|  
|`DynamicProgressFeedback`|Un valor de [concurrency::DynamicProgressFeedbackType](../Topic/DynamicProgressFeedbackType%20Enumeration.md) que especifica si se van a volver a equilibrar los recursos según la información estadística\- basada progreso.<br /><br /> **Nota** No establezca esta directiva a `ProgressFeedbackDisabled` porque se reserva para uso en tiempo de ejecución.|`ProgressFeedbackEnabled`|  
  
 Cada programador utiliza su propia directiva cuando programa tareas.  Las directivas que están asociadas a un programador no afectan al comportamiento de otros programadores.  Además, no puede cambiar la directiva de programador después de crear el objeto `Scheduler`.  
  
> [!IMPORTANT]
>  Use solo directivas de programador para controlar los atributos de los subprocesos que el runtime crea.  No cambie la afinidad de subprocesos o la prioridad de los subprocesos creados por el tiempo de ejecución porque podría producir un comportamiento indefinido.  
  
 El runtime creará un programador predeterminado si no crea uno explícitamente.  Si desea usar el programador predeterminado en la aplicación, pero desea especificar una directiva para que use el programador, llame al método de [concurrency::Scheduler::SetDefaultSchedulerPolicy](../Topic/Scheduler::SetDefaultSchedulerPolicy%20Method.md) antes de que se programe trabajo paralelo.  Si no llama al método `Scheduler::SetDefaultSchedulerPolicy`, el runtime utiliza los valores de directiva predeterminados de la tabla.  
  
 Utilice [concurrency::CurrentScheduler::GetPolicy](../Topic/CurrentScheduler::GetPolicy%20Method.md) y los métodos de [concurrency::Scheduler::GetPolicy](../Topic/Scheduler::GetPolicy%20Method.md) para recuperar una copia de la directiva de programador.  Los valores de directiva que se reciben de estos métodos pueden diferir de los valores de directiva que se especifican cuando se crea el programador.  
  
## Ejemplo  
 Para examinar los ejemplos que utilizan directivas de programador concretas para controlar el comportamiento del programador, vea [Cómo: Especificar directivas de programador concretas](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md) y [Cómo: Crear agentes que usen directivas de programador específicas](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).  
  
## Vea también  
 [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Cómo: Especificar directivas de programador concretas](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)   
 [Cómo: Crear agentes que usen directivas de programador específicas](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)