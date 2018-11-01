---
title: Tareas ligeras
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
ms.openlocfilehash: 7e155b82e963e7bf3f19fa44c66e4c22b8c602e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481437"
---
# <a name="lightweight-tasks"></a>Tareas ligeras

Este documento describe el rol de las tareas ligeras en el Runtime de simultaneidad. Un *tarea ligera* es una tarea que se programa directamente desde un `concurrency::Scheduler` o `concurrency::ScheduleGroup` objeto. Una tarea ligera es similar a la función que se proporciona a la API de Windows [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) función. Por lo tanto, las tareas ligeras son útiles cuando se adapta código existente para usar la funcionalidad de programación del Runtime de simultaneidad. El propio Runtime de simultaneidad usa las tareas ligeras para programar a los agentes asincrónicos y enviar mensajes entre los bloques de mensajes asincrónicos.

> [!TIP]
>  Runtime de simultaneidad proporciona un programador predeterminado, por lo que no deberá crear uno en la aplicación. Dado que el programador de tareas le ayuda a ajustar el rendimiento de las aplicaciones, es recomendable que comience con la [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si es nuevo en el Runtime de simultaneidad.

Las tareas ligeras implican una menor sobrecarga que los agentes asincrónicos y grupos de tareas. Por ejemplo, el tiempo de ejecución no le informan cuando finalice una tarea ligera. Además, el tiempo de ejecución no detectar ni controlar las excepciones producidas desde una tarea ligera. Para obtener más información sobre el control de excepciones y las tareas ligeras, vea [Exception Handling](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Para la mayoría de las tareas, se recomienda que utilice la funcionalidad más sólida como grupos de tareas y algoritmos paralelos porque le permiten más fácilmente interrupción las tareas complejas en otras más básicas. Para obtener más información acerca de los grupos de tareas, consulte [paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Para obtener más información acerca de los algoritmos paralelos, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).

Para crear una tarea ligera, llame a la [concurrency::ScheduleGroup::ScheduleTask](reference/schedulegroup-class.md#scheduletask), [concurrency::CurrentScheduler::ScheduleTask](reference/currentscheduler-class.md#scheduletask), o [concurrency::Scheduler::ScheduleTask ](reference/scheduler-class.md#scheduletask) método. Para esperar a que finalice una tarea ligera, espere a que el programador primario apagar o usar un mecanismo de sincronización, como un [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) objeto.

## <a name="example"></a>Ejemplo

Para obtener un ejemplo que muestra cómo adaptar código existente para usar una tarea ligera, consulte [Tutorial: adaptar código existente para usar tareas ligeras](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md).

## <a name="see-also"></a>Vea también

[Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Tutorial: Adaptar el código existente para usar tareas ligeras](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)

