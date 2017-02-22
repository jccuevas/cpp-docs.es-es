---
title: "Grupos de programaci&#243;n | Microsoft Docs"
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
  - "grupos de programación"
ms.assetid: 03523572-5891-4d17-89ce-fa795605f28b
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Grupos de programaci&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este documento describe la función de los grupos de programación del Runtime de simultaneidad. Un *grupo de programación* affinitizes o agrupa, tareas relacionadas. Cada programador tiene uno o más grupos de programación. Use los grupos de programación si necesita aplicar un grado elevado de localidad entre las tareas (por ejemplo, si resulta positivo para un grupo de tareas relacionadas ejecutarse en el mismo nodo del procesador). Por el contrario, utilice las instancias del programador cuando la aplicación tiene requisitos de calidad específicos, por ejemplo, si desea limitar la cantidad de recursos de procesamiento que se asignan a un conjunto de tareas. Para obtener más información acerca de las instancias del programador, consulte [instancias del programador](../../parallel/concrt/scheduler-instances.md).  
  
> [!TIP]
>  Runtime de simultaneidad proporciona un programador predeterminado, por lo que no deberá crear uno en la aplicación. Dado que el programador de tareas le ayuda a ajustar el rendimiento de las aplicaciones, se recomienda que empiece con el [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) Si está familiarizado con el Runtime de simultaneidad.  
  
 Cada `Scheduler` objeto tiene un grupo de programación predeterminado para cada nodo de programación. Un *nodo planificación* se asigna a la topología del sistema subyacente. El runtime crea un nodo de programación para cada paquete de procesador o el nodo de la arquitectura de memoria no uniforme (NUMA), el que sea mayor. Si no asocia explícitamente una tarea a un grupo de programación, el programador elige qué grupo para agregar la tarea.  
  
 El `SchedulingProtocol` Directiva de programador influye en el orden en el que el programador ejecuta las tareas de cada grupo de programación. Cuando `SchedulingProtocol` se establece en `EnhanceScheduleGroupLocality` (que es el valor predeterminado), el programador de tareas elige la tarea siguiente desde el grupo de programación que está trabajando cuando la tarea finaliza o cede de manera cooperativa. El programador de tareas busca el grupo de programación actual para el trabajo antes de pasar al grupo disponible siguiente. Por el contrario, cuando `SchedulingProtocol` se establece en `EnhanceForwardProgress`, el programador se mueve al siguiente grupo de programación después de cada tarea finaliza o produce un resultado. Para obtener un ejemplo que compara estas directivas, consulte [Cómo: usar grupos de programación que influyen en la orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).  
  
 El runtime usa el [Concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) clase para representar grupos de programación. Para crear un `ScheduleGroup` de objeto, llame a la [concurrency::CurrentScheduler::CreateScheduleGroup](../Topic/CurrentScheduler::CreateScheduleGroup%20Method.md) o [concurrency::Scheduler::CreateScheduleGroup](../Topic/Scheduler::CreateScheduleGroup%20Method.md) método. El runtime usa un mecanismo de recuento de referencias para controlar la duración de `ScheduleGroup` objetos, al igual que con `Scheduler` objetos. Cuando se crea un `ScheduleGroup` de objeto, el tiempo de ejecución establece la referencia de contador en uno. El [concurrency::ScheduleGroup::Reference](../Topic/ScheduleGroup::Reference%20Method.md) método incrementa el contador de referencias en uno. El [concurrency::ScheduleGroup::Release](../Topic/ScheduleGroup::Release%20Method.md) método disminuye el contador de referencias en uno.  
  
 Muchos tipos del Runtime de simultaneidad permiten asociar un objeto junto con un grupo de programación. Por ejemplo, el [Concurrency](../../parallel/concrt/reference/agent-class.md) clases de bloque de mensaje y de clase como [Concurrency:: unbounded_buffer](../Topic/unbounded_buffer%20Class.md), [Concurrency:: join](../../parallel/concrt/reference/join-class.md), y concurrencia::[temporizador](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/d5d4c847-5ad6-4c7f-b35b-d0b6f446d8b4/locales/en-US), proporcionar versiones sobrecargadas del constructor que toman un `ScheduleGroup` objeto. El runtime usa el `Scheduler` objeto asociado con este `ScheduleGroup` objeto para programar la tarea.  
  
 También puede utilizar el [concurrency::ScheduleGroup::ScheduleTask](../Topic/ScheduleGroup::ScheduleTask%20Method.md) método para programar una tarea ligera. Para obtener más información sobre las tareas ligeras, vea [tareas ligeras](../../parallel/concrt/lightweight-tasks.md).  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo que utiliza grupos para controlar el orden de ejecución de la tarea de programación, vea [Cómo: usar grupos de programación que influyen en la orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).  
  
## <a name="see-also"></a>Vea también  
 [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Instancias del programador](../../parallel/concrt/scheduler-instances.md)   
 [Cómo: usar grupos de programación para influir en el orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)

