---
title: "Grupos de programación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: schedule groups
ms.assetid: 03523572-5891-4d17-89ce-fa795605f28b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 234288be0313c8e50fde08a3cb898f498ebe4174
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="schedule-groups"></a>Grupos de programación
Este documento describe el rol de los grupos de programación del Runtime de simultaneidad. A *grupo de programación* establece la afinidad o agrupa, tareas relacionadas. Cada programador tiene uno o más grupos de programación. Use los grupos de programación si necesita aplicar un grado elevado de localidad entre las tareas (por ejemplo, si resulta positivo para un grupo de tareas relacionadas ejecutarse en el mismo nodo del procesador). Por el contrario, utilice las instancias del programador cuando la aplicación tiene requisitos de calidad específicos, por ejemplo, si desea limitar la cantidad de recursos de procesamiento que se asignan a un conjunto de tareas. Para obtener más información acerca de las instancias del programador, consulte [instancias del programador](../../parallel/concrt/scheduler-instances.md).  
  
> [!TIP]
>  Runtime de simultaneidad proporciona un programador predeterminado, por lo que no deberá crear uno en la aplicación. Dado que el programador de tareas permite ajustar el rendimiento de las aplicaciones, es recomendable que comience con la [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si está nuevo para el Runtime de simultaneidad.  
  
 Cada `Scheduler` objeto tiene un grupo de programación predeterminado para cada nodo de programación. A *programación nodo* se asigna a la topología del sistema subyacente. El runtime crea un nodo de programación para cada paquete de procesadores o nodo de la arquitectura de memoria no uniforme (NUMA), el que sea mayor. Si no se asocie explícitamente una tarea a un grupo de programación, el programador elige el grupo al que agregar a la tarea.  
  
 El `SchedulingProtocol` directiva de programador influye en el orden en el que el programador ejecuta las tareas de cada grupo de programación. Cuando `SchedulingProtocol` se establece en `EnhanceScheduleGroupLocality` (que es el valor predeterminado), el programador de tareas elige la tarea siguiente en el grupo de programación que se está trabajando en cuando la tarea actual finaliza o cede de manera cooperativa. El programador de tareas busca el grupo de programación actual para el trabajo antes de pasar al siguiente grupo de disponibilidad. Por el contrario, cuando `SchedulingProtocol` se establece en `EnhanceForwardProgress`, el programador se mueve al siguiente grupo de programación después de cada tarea finaliza o produce un resultado. Para obtener un ejemplo que compara estas directivas, consulte [Cómo: utilizar grupos de programación para influyen en orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).  
  

 El runtime usa el [Concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) clase para representar grupos de programación. Para crear un `ScheduleGroup` objeto, llame a la [concurrency::CurrentScheduler::CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup) o [concurrency::Scheduler::CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup) método. El runtime usa un mecanismo de recuento de referencias para controlar la duración de `ScheduleGroup` objetos, igual que con `Scheduler` objetos. Cuando se crea un `ScheduleGroup` de objeto, el tiempo de ejecución establece la referencia del contador en uno. El [concurrency::ScheduleGroup::Reference](reference/schedulegroup-class.md#reference) método incrementa el contador de referencias en uno. El [concurrency::ScheduleGroup::Release](reference/schedulegroup-class.md#release) método disminuye el contador de referencias en uno.  
  
 Muchos tipos en el Runtime de simultaneidad permiten asociar un objeto junto con un grupo de programación. Por ejemplo, el [Concurrency](../../parallel/concrt/reference/agent-class.md) clase y mensaje de un bloque de clases como [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md), [Concurrency:: join](../../parallel/concrt/reference/join-class.md)y la simultaneidad::[ temporizador](reference/timer-class.md), proporcionan las versiones sobrecargadas del constructor que toman un `ScheduleGroup` objeto. El runtime usa el `Scheduler` objeto que está asociado a este `ScheduleGroup` objeto para programar la tarea.  
  
 También puede usar el [concurrency::ScheduleGroup::ScheduleTask](reference/schedulegroup-class.md#scheduletask) método para programar una tarea ligera. Para obtener más información acerca de las tareas ligeras, vea [tareas ligeras](../../parallel/concrt/lightweight-tasks.md).  

  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo que usa grupos para controlar el orden de ejecución de la tarea de programación, vea [Cómo: utilizar grupos de programación para influyen en orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).  
  
## <a name="see-also"></a>Vea también  
 [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Instancias del programador](../../parallel/concrt/scheduler-instances.md)   
 [Procedimiento para usar grupos de programación para influir en el orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)

