---
title: Grupos de programación
ms.date: 11/04/2016
helpviewer_keywords:
- schedule groups
ms.assetid: 03523572-5891-4d17-89ce-fa795605f28b
ms.openlocfilehash: 1765c10f4cf8fe499aed1a140d2bba1ecaaf2300
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142312"
---
# <a name="schedule-groups"></a>Grupos de programación

En este documento se describe el rol de los grupos de programación en el Runtime de simultaneidad. Un *grupo de programación* establece, o grupos, tareas relacionadas. Cada programador tiene uno o más grupos de programación. Use los grupos de programación si necesita aplicar un grado elevado de localidad entre las tareas (por ejemplo, si resulta positivo para un grupo de tareas relacionadas ejecutarse en el mismo nodo del procesador). Por el contrario, use instancias de Scheduler cuando la aplicación tenga requisitos de calidad específicos, por ejemplo, cuando desee limitar la cantidad de recursos de procesamiento que se asignan a un conjunto de tareas. Para obtener más información sobre las instancias de Scheduler, consulte [instancias de Scheduler](../../parallel/concrt/scheduler-instances.md).

> [!TIP]
> Runtime de simultaneidad proporciona un programador predeterminado, por lo que no deberá crear uno en la aplicación. Dado que el Programador de tareas le ayuda a ajustar el rendimiento de las aplicaciones, se recomienda empezar con la biblioteca de [patrones de procesamiento paralelo (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o la [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si no está familiarizado con la Runtime de simultaneidad.

Cada `Scheduler` objeto tiene un grupo de programación predeterminado para cada nodo de programación. Un *nodo de programación* se asigna a la topología del sistema subyacente. El tiempo de ejecución crea un nodo de programación para cada paquete de procesador o nodo de arquitectura de memoria no uniforme (NUMA), lo que sea mayor. Si no asocia explícitamente una tarea a un grupo de programación, el programador elige a qué grupo desea agregar la tarea.

La Directiva del programador de `SchedulingProtocol` influye en el orden en que el programador ejecuta las tareas en cada grupo de programación. Cuando `SchedulingProtocol` se establece en `EnhanceScheduleGroupLocality` (que es el valor predeterminado), el Programador de tareas elige la siguiente tarea del grupo de programación en el que está trabajando cuando la tarea actual finaliza o cede de forma cooperativa. El Programador de tareas busca el trabajo en el grupo de programación actual antes de que se mueva al siguiente grupo disponible. Por el contrario, cuando `SchedulingProtocol` está establecido en `EnhanceForwardProgress`, el programador se desplaza al siguiente grupo de programación después de que finalice cada tarea o se produzca. Para obtener un ejemplo en el que se comparan estas directivas, consulte [Cómo: usar grupos de programación para influir en el orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

El Runtime usa la clase [Concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) para representar grupos de programación. Para crear un objeto de `ScheduleGroup`, llame al método [Concurrency:: CurrentScheduler:: createschedulegroup (](reference/currentscheduler-class.md#createschedulegroup) o [Concurrency:: Scheduler:: createschedulegroup (](reference/scheduler-class.md#createschedulegroup) . El motor en tiempo de ejecución usa un mecanismo de recuento de referencias para controlar la duración de los objetos `ScheduleGroup`, tal como hace con los objetos `Scheduler`. Cuando se crea un objeto de `ScheduleGroup`, el tiempo de ejecución establece el contador de referencias en uno. El método [Concurrency:: ScheduleGroup:: Reference](reference/schedulegroup-class.md#reference) incrementa el contador de referencias en uno. El método [Concurrency:: ScheduleGroup:: Release](reference/schedulegroup-class.md#release) reduce el contador de referencias en uno.

Muchos tipos en el Runtime de simultaneidad permiten asociar un objeto junto con un grupo de programación. Por ejemplo, la clase [Concurrency:: Agent](../../parallel/concrt/reference/agent-class.md) y las clases de bloque de mensajes como [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md), [Concurrency:: join](../../parallel/concrt/reference/join-class.md)y Concurrency::[Timer](reference/timer-class.md), proporcionan versiones sobrecargadas del constructor que toman un objeto `ScheduleGroup`. El motor en tiempo de ejecución utiliza el objeto `Scheduler` asociado a este objeto `ScheduleGroup` para programar la tarea.

También puede utilizar el método [Concurrency:: ScheduleGroup:: ScheduleTask](reference/schedulegroup-class.md#scheduletask) para programar una tarea ligera. Para obtener más información sobre las tareas ligeras, vea [tareas ligeras](../../parallel/concrt/lightweight-tasks.md).

## <a name="example"></a>Ejemplo

Para obtener un ejemplo en el que se usan grupos de programación para controlar el orden de ejecución de la tarea, vea [Cómo: usar grupos de programación para influir en el orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

## <a name="see-also"></a>Consulte también

[Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Instancias de Scheduler](../../parallel/concrt/scheduler-instances.md)<br/>
[Procedimiento para usar grupos de programación para influir en el orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)
