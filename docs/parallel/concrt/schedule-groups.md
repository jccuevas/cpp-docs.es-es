---
title: Grupos de programación | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- schedule groups
ms.assetid: 03523572-5891-4d17-89ce-fa795605f28b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4fa61772af96ba0d2602ff42a6a43b2b3a13a4e6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385904"
---
# <a name="schedule-groups"></a>Grupos de programación

Este documento describe la función de los grupos de programación del Runtime de simultaneidad. Un *grupo de programación* affinitizes o agrupa, las tareas relacionadas. Cada programador tiene uno o varios grupos de programación. Use los grupos de programación si necesita aplicar un grado elevado de localidad entre las tareas (por ejemplo, si resulta positivo para un grupo de tareas relacionadas ejecutarse en el mismo nodo del procesador). Por el contrario, utilice las instancias del programador cuando la aplicación tiene requisitos concretos de calidad, por ejemplo, cuando desee limitar la cantidad de recursos de procesamiento que se asignan a un conjunto de tareas. Para obtener más información acerca de las instancias del programador, consulte [las instancias del programador](../../parallel/concrt/scheduler-instances.md).

> [!TIP]
>  Runtime de simultaneidad proporciona un programador predeterminado, por lo que no deberá crear uno en la aplicación. Dado que el programador de tareas le ayuda a ajustar el rendimiento de las aplicaciones, es recomendable que comience con la [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si es nuevo en el Runtime de simultaneidad.

Cada `Scheduler` objeto tiene un grupo de programación predeterminado para cada nodo de programación. Un *programación nodo* se asigna a la topología del sistema subyacente. El runtime crea un nodo de programación para cada paquete de procesadores o nodo de la arquitectura de memoria no uniforme (NUMA), el que sea mayor. Si no asocia explícitamente una tarea con un grupo de programación, el programador elige qué grupo va a agregar a la tarea.

El `SchedulingProtocol` directiva de programador influye en el orden en que el programador ejecuta las tareas de cada grupo de programación. Cuando `SchedulingProtocol` está establecido en `EnhanceScheduleGroupLocality` (que es el valor predeterminado), el programador de tareas elige la siguiente tarea en el grupo de programación que está trabajando cuando la tarea actual finaliza o cede de manera cooperativa. El programador de tareas busca el grupo de programación actual para el trabajo antes de pasar al siguiente grupo de disponibilidad. Por el contrario, cuando `SchedulingProtocol` está establecido en `EnhanceForwardProgress`, el programador se mueve al siguiente grupo de programación después de cada tarea finaliza o cede. Para obtener un ejemplo que compara estas directivas, consulte [Cómo: utilizar grupos de programación para influyen en la orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

El runtime usa el [Concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) clase para representar grupos de programación. Para crear un `ScheduleGroup` de objeto, llame a la [concurrency::CurrentScheduler::CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup) o [concurrency::Scheduler::CreateScheduleGroup](reference/scheduler-class.md#createschedulegroup) método. El tiempo de ejecución usa un mecanismo de recuento de referencias para controlar la duración de `ScheduleGroup` objetos, al igual que con `Scheduler` objetos. Cuando creas un `ScheduleGroup` de objeto, el tiempo de ejecución establece la referencia del contador en uno. El [concurrency::ScheduleGroup::Reference](reference/schedulegroup-class.md#reference) método incrementa el contador de referencias en uno. El [concurrency::ScheduleGroup::Release](reference/schedulegroup-class.md#release) método disminuye el contador de referencias en uno.

Muchos tipos en el Runtime de simultaneidad permiten asociar un objeto junto con un grupo de programación. Por ejemplo, el [Concurrency:: Agent](../../parallel/concrt/reference/agent-class.md) clases de bloque de clase y el mensaje como [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md), [Concurrency:: join](../../parallel/concrt/reference/join-class.md)y la simultaneidad::[ temporizador](reference/timer-class.md), proporcionar versiones sobrecargadas del constructor que toman un `ScheduleGroup` objeto. El runtime usa el `Scheduler` objeto que está asociado con este `ScheduleGroup` objeto para programar la tarea.

También puede usar el [concurrency::ScheduleGroup::ScheduleTask](reference/schedulegroup-class.md#scheduletask) método para programar una tarea ligera. Para obtener más información sobre las tareas ligeras, vea [tareas ligeras](../../parallel/concrt/lightweight-tasks.md).

## <a name="example"></a>Ejemplo

Para obtener un ejemplo que usa grupos para controlar el orden de ejecución de la tarea de programación, vea [Cómo: utilizar grupos de programación para influyen en la orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

## <a name="see-also"></a>Vea también

[Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Instancias de Scheduler](../../parallel/concrt/scheduler-instances.md)<br/>
[Procedimiento para usar grupos de programación para influir en el orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)

