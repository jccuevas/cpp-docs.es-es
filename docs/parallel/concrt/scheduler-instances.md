---
title: "Instancias del programador | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "instancias del programador"
ms.assetid: 4819365f-ef99-49cc-963e-50a2a35a8d6b
caps.latest.revision: 7
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Instancias del programador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este documento se describe el rol de instancias del programador del runtime de simultaneidad y cómo usar las clases de [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) y de [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) para crear y administrar las instancias del programador.  Las instancias de programador son útiles cuando desea asociar directivas de programación explícitas con tipos concretos de cargas de trabajo.  Por ejemplo, puede crear una instancia de programador para ejecutar algunas tareas con una prioridad elevada de subproceso y usar el programador predeterminado para ejecutar con otras tareas con la prioridad normal de subproceso.  
  
> [!TIP]
>  El runtime de simultaneidad proporciona un programador predeterminado y, por tanto, no es necesario crear uno en la aplicación.  Dado que el programador de tareas ayuda a ajustar el rendimiento de las aplicaciones, se recomienda que comience con [Parallel Patterns Library \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md) o [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si no ha usado antes el runtime de simultaneidad.  
  
##  <a name="top"></a> Secciones  
  
-   [Las clases CurrentScheduler y Scheduler](#classes)  
  
-   [Crear una instancia del Programador](#creating)  
  
-   [Administrar la duración de una instancia de programador](#managing)  
  
-   [Métodos y características](#features)  
  
-   [Ejemplo](#example)  
  
##  <a name="classes"></a> Las clases CurrentScheduler y Scheduler  
 El Programador de tareas permite a las aplicaciones utilizar una o varias *instancias del programador* para programar el trabajo.  La clase de [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) representa una instancia de programador y encapsula la funcionalidad relacionada con la programación de tareas.  
  
 Un subproceso que se adjunta a un programador se conoce como *contexto de ejecución* o simplemente *contexto*.  Un programador puede estar activo en el contexto actual en cualquier momento.  El programador activo también es conocido como *programador actual*.  El runtime de simultaneidad utiliza la clase de [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) para proporcionar acceso al programador actual.  El programador actual de un contexto puede diferir del programador de otro contexto.  El runtime no proporciona ninguna representación de nivel de proceso del programador actual.  
  
 Normalmente, la clase `CurrentScheduler` se utiliza para tener acceso al programador actual.  La clase `Scheduler` resulta útil si necesita administrar un programador que no es el actual.  
  
 En las siguientes secciones se describe cómo crear y administrar una instancia del programador.  Para obtener un ejemplo completo que ilustre estas tareas, vea [Cómo: Administrar una instancia del programador](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).  
  
 \[[Arriba](#top)\]  
  
##  <a name="creating"></a> Crear una instancia del Programador  
 Hay tres maneras de crear un objeto `Scheduler`:  
  
-   Si no existe ningún programador, el runtime crea uno predeterminado para que pueda utilizar la funcionalidad en tiempo de ejecución, por ejemplo, un algoritmo paralelo, para llevar a cabo el trabajo.  El programador predeterminado se convierte en el programador actual para el contexto que inicia el trabajo paralelo.  
  
-   El método de [concurrency::CurrentScheduler::Create](../Topic/CurrentScheduler::Create%20Method.md) crea un objeto de `Scheduler` que usa una directiva concreta y asocia ese programador al contexto actual.  
  
-   El método de [concurrency::Scheduler::Create](../Topic/Scheduler::Create%20Method.md) crea un objeto de `Scheduler` que usa una directiva concreta, pero no lo asocia al contexto actual.  
  
 Permitir que el runtime cree un programador predeterminado posibilita que todas las tareas simultáneas compartan el mismo programador.  Normalmente, la funcionalidad que proporciona la [Biblioteca de modelos de procesamiento paralelo](../../parallel/concrt/parallel-patterns-library-ppl.md) \(PPL\) o la [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) se usa para realizar trabajo paralelo.  Por consiguiente, no tiene que trabajar directamente con el programador para controlar su directiva o duración.  Al utilizar PPL o la Biblioteca de agentes, el runtime crea el programador predeterminado si no existe y lo convierte en el programador actual para cada contexto.  Cuando se crea un programador y se establece como el programador actual, el runtime usa ese programador para programar tareas.  Cree instancias adicionales del programador solo cuando necesite una directiva de programación concreta.  Para obtener más información sobre las directivas asociadas a un programador, vea [Directivas del programador](../../parallel/concrt/scheduler-policies.md).  
  
 \[[Arriba](#top)\]  
  
##  <a name="managing"></a> Administrar la duración de una instancia de programador  
 El runtime utiliza un mecanismo de recuento de referencias para controlar la duración de los objetos `Scheduler`.  
  
 Al utilizar el método `CurrentScheduler::Create` o `Scheduler::Create` para crear un objeto `Scheduler`, el runtime establece el recuento de referencias inicial de ese programador en uno.  El runtime incrementa el recuento de referencias cuando se llama al método de [concurrency::Scheduler::Attach](../Topic/Scheduler::Attach%20Method.md) .  El método `Scheduler::Attach` asocia el objeto `Scheduler` junto con el contexto actual.  Esto lo convierte en el programador actual.  Al llamar al método `CurrentScheduler::Create`, el tiempo de ejecución crea un objeto `Scheduler` y lo adjunta al contexto actual \(y establece el recuento de referencias en uno\).  También puede utilizar el método de [concurrency::Scheduler::Reference](../Topic/Scheduler::Reference%20Method.md) para incrementar el recuento de referencias de un objeto de `Scheduler` .  
  
 El runtime disminuye el recuento de referencias cuando se llama al método de [concurrency::CurrentScheduler::Detach](../Topic/CurrentScheduler::Detach%20Method.md) para desasociar el programador actual, o llama al método de [concurrency::Scheduler::Release](../Topic/Scheduler::Release%20Method.md) .  Cuando el recuento de referencias llega a cero, el runtime destruye el objeto `Scheduler` cuando todas las tareas programadas finalizan.  Una tarea en ejecución puede incrementar el recuento de referencias del programador actual.  Por consiguiente, si el recuento de referencias llega a cero y una tarea incrementa el recuento de referencias, el runtime no destruye el objeto `Scheduler` hasta que el recuento de referencias llega a cero de nuevo y finalizan todas las tareas.  
  
 El runtime mantiene una pila interna de los objetos `Scheduler` para cada contexto.  Cuando se llama al método `CurrentScheduler::Create` o `Scheduler::Attach`, el runtime empuja el objeto `Scheduler` hacia la pila del contexto actual.  Esto lo convierte en el programador actual.  Al llamar a `CurrentScheduler::Detach`, el runtime saca el programador de la pila para el contexto actual y establece el anterior como programador actual.  
  
 El runtime proporciona varias maneras de administrar la duración de una instancia del programador.  En la siguiente tabla se muestra el método adecuado que libera o desasocia el programador del contexto actual para cada método que crea o adjunta un programador al contexto actual.  
  
|Crear o adjuntar|Liberar o desasociar|  
|----------------------|--------------------------|  
|`CurrentScheduler::Create`|`CurrentScheduler::Detach`|  
|`Scheduler::Create`|`Scheduler::Release`|  
|`Scheduler::Attach`|`CurrentScheduler::Detach`|  
|`Scheduler::Reference`|`Scheduler::Release`|  
  
 Llamar al método de liberar o asociar incorrecto genera un comportamiento no especificado en el runtime.  
  
 Cuando usa funcionalidad, por ejemplo, PPL hace que el runtime cree el programador predeterminado, no libera ni desasocia este programador.  El runtime administra la duración de cualquier programador que cree.  
  
 Como el runtime no destruye un objeto de `Scheduler` antes de que todas las tareas hayan finalizado, puede utilizar el método de [concurrency::Scheduler::RegisterShutdownEvent](../Topic/Scheduler::RegisterShutdownEvent%20Method.md) o el método de [concurrency::CurrentScheduler::RegisterShutdownEvent](../Topic/CurrentScheduler::RegisterShutdownEvent%20Method.md) para recibir una notificación cuando se destruye un objeto de `Scheduler` .  Esto es útil cuando hay que esperar a que finalice cada tarea programada por un objeto `Scheduler`.  
  
 \[[Arriba](#top)\]  
  
##  <a name="features"></a> Métodos y características  
 En esta sección se resumen los métodos importantes de las clases `Scheduler` y `CurrentScheduler`.  
  
 Piense en la clase `CurrentScheduler` como una aplicación auxiliar para crear un programador que se usará en el contexto actual.  La clase `Scheduler` permite controlar un programador que pertenece a otro contexto.  
  
 En la tabla siguiente se muestran los métodos importantes definidos por la clase `CurrentScheduler`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Create](../Topic/CurrentScheduler::Create%20Method.md)|Crea un objeto `Scheduler` que utiliza la directiva especificada y la asocia con el contexto actual.|  
|[Get](../Topic/CurrentScheduler::Get%20Method.md)|Recupera un puntero al objeto `Scheduler` asociado con los nodos del contexto actual.  Este método no incrementa el recuento de referencias del objeto `Scheduler`.|  
|[Desasociar](../Topic/CurrentScheduler::Detach%20Method.md)|Desasocia el programador del contexto actual y establece el anterior como programador actual.|  
|[RegisterShutdownEvent](../Topic/CurrentScheduler::RegisterShutdownEvent%20Method.md)|Registra un evento que el runtime establece cuando se destruye el programador actual.|  
|[CreateScheduleGroup](../Topic/CurrentScheduler::CreateScheduleGroup%20Method.md)|Crea un objeto de [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) en el programador actual.|  
|[ScheduleTask](../Topic/CurrentScheduler::ScheduleTask%20Method.md)|Agrega una tarea ligera a la cola de programación del programador actual.|  
|[GetPolicy](../Topic/CurrentScheduler::GetPolicy%20Method.md)|Recupera una copia de la directiva que está asociada al programador actual.|  
  
 En la tabla siguiente se muestran los métodos importantes definidos por la clase `Scheduler`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Create](../Topic/Scheduler::Create%20Method.md)|Crea un objeto `Scheduler` que usa la directiva especificada.|  
|[Asociar](../Topic/Scheduler::Attach%20Method.md)|Asocia el objeto `Scheduler` al contexto actual.|  
|[Reference](../Topic/Scheduler::Reference%20Method.md)|Incrementa el contador de referencia del objeto `Scheduler`.|  
|[Release](../Topic/Scheduler::Release%20Method.md)|Disminuye el contador de referencia del objeto `Scheduler`.|  
|[RegisterShutdownEvent](../Topic/Scheduler::RegisterShutdownEvent%20Method.md)|Registra un evento que el runtime establece cuando se destruye el objeto `Scheduler`.|  
|[CreateScheduleGroup](../Topic/Scheduler::CreateScheduleGroup%20Method.md)|Crea un objeto de [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) en el objeto de `Scheduler` .|  
|[ScheduleTask](../Topic/Scheduler::ScheduleTask%20Method.md)|Programa una tarea ligera del objeto `Scheduler`.|  
|[GetPolicy](../Topic/Scheduler::GetPolicy%20Method.md)|Recupera una copia de la directiva que está asociada al objeto `Scheduler`.|  
|[SetDefaultSchedulerPolicy](../Topic/Scheduler::SetDefaultSchedulerPolicy%20Method.md)|Establece la directiva que el runtime usa cuando crea el programador predeterminado.|  
|[ResetDefaultSchedulerPolicy](../Topic/Scheduler::ResetDefaultSchedulerPolicy%20Method.md)|Restaura la directiva predeterminada que estaba activa antes de la llamada a `SetDefaultSchedulerPolicy`.  Si el programador predeterminado se crea después de esta llamada, el runtime utiliza los valores de la directiva predeterminada para crear el programador.|  
  
 \[[Arriba](#top)\]  
  
##  <a name="example"></a> Ejemplo  
 Para obtener ejemplos básicos sobre cómo crear y administrar una instancia de programador, vea [Cómo: Administrar una instancia del programador](../../parallel/concrt/how-to-manage-a-scheduler-instance.md).  
  
## Vea también  
 [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Cómo: Administrar una instancia del programador](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)   
 [Directivas del programador](../../parallel/concrt/scheduler-policies.md)   
 [Grupos de programación](../../parallel/concrt/schedule-groups.md)