---
title: Tareas ligeras
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
ms.openlocfilehash: 7b798312c9660e51338d51a97a052ad4e5bdca6b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512180"
---
# <a name="lightweight-tasks"></a>Tareas ligeras

En este documento se describe el rol de las tareas ligeras en el Runtime de simultaneidad. Una *tarea ligera* es una tarea que se programa directamente desde un `concurrency::Scheduler` objeto `concurrency::ScheduleGroup` o. Una tarea ligera es similar a la función que se proporciona a la función [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) de la API de Windows. Por lo tanto, las tareas ligeras son útiles cuando se adapta el código existente para usar la funcionalidad de programación del Runtime de simultaneidad. El propio Runtime de simultaneidad utiliza tareas ligeras para programar agentes asincrónicos y enviar mensajes entre bloques de mensajes asincrónicos.

> [!TIP]
>  Runtime de simultaneidad proporciona un programador predeterminado, por lo que no deberá crear uno en la aplicación. Dado que el Programador de tareas le ayuda a ajustar el rendimiento de las aplicaciones, se recomienda empezar con la biblioteca de [patrones de procesamiento paralelo (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o la [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si no está familiarizado con la Runtime de simultaneidad.

Las tareas ligeras transportan menos sobrecarga que los agentes asincrónicos y los grupos de tareas. Por ejemplo, el tiempo de ejecución no le informará cuando una tarea ligera finalice. Además, el runtime no detecta ni controla las excepciones que se producen desde una tarea ligera. Para obtener más información sobre el control de excepciones y las tareas ligeras, vea [control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Para la mayoría de las tareas, se recomienda usar una funcionalidad más sólida, como grupos de tareas y algoritmos paralelos, ya que permiten dividir más fácilmente las tareas complejas en otras más básicas. Para obtener más información acerca de los grupos de tareas, consulte [paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Para obtener más información sobre los algoritmos paralelos, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).

Para crear una tarea ligera, llame a los métodos [Concurrency:: ScheduleGroup:: ScheduleTask](reference/schedulegroup-class.md#scheduletask), Concurrency [:: CurrentScheduler:: ScheduleTask](reference/currentscheduler-class.md#scheduletask)o Concurrency [:: Scheduler:: ScheduleTask](reference/scheduler-class.md#scheduletask) . Para esperar a que finalice una tarea ligera, espere a que el programador primario se cierre o use un mecanismo de sincronización, como un objeto [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) .

## <a name="example"></a>Ejemplo

Para obtener un ejemplo en el que se muestra cómo adaptar el código existente para usar una [tarea ligera, vea Tutorial: Adaptación del código existente para usar tareas](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)ligeras.

## <a name="see-also"></a>Vea también

[Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Tutorial: Adaptación del código existente para usar tareas ligeras](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)
