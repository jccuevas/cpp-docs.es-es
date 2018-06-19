---
title: Tareas ligeras | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- lightweight tasks
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d602f83cfe2da6bc1506e07720d3ef021ebce04a
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687418"
---
# <a name="lightweight-tasks"></a>Tareas ligeras
Este documento describe el rol de las tareas ligeras en el Runtime de simultaneidad. A *tarea ligera* es una tarea que se programa directamente desde un `concurrency::Scheduler` o `concurrency::ScheduleGroup` objeto. Una tarea ligera es similar a la función que se proporciona a la API de Windows [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) función. Por lo tanto, las tareas ligeras son útiles cuando se adapta código existente para usar la funcionalidad de programación del Runtime de simultaneidad. El propio Runtime de simultaneidad usa tareas ligeras para programar los agentes asincrónicos y enviar mensajes entre los bloques de mensajes asincrónicos.  
  
> [!TIP]
>  Runtime de simultaneidad proporciona un programador predeterminado, por lo que no deberá crear uno en la aplicación. Dado que el programador de tareas permite ajustar el rendimiento de las aplicaciones, es recomendable que comience con la [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si está nuevo para el Runtime de simultaneidad.  
  
 Las tareas ligeras implican una menor sobrecarga que agentes asincrónicos y grupos de tareas. Por ejemplo, el tiempo de ejecución no le informan cuando finaliza una tarea ligera. Además, el tiempo de ejecución no detectar o controlar las excepciones que se producen en una tarea ligera. Para obtener más información sobre el control de excepciones y las tareas ligeras, vea [Exception Handling](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
 Para la mayoría de las tareas, se recomienda que utilice la funcionalidad más sólida como grupos de tareas y algoritmos paralelos ya que permiten más fácilmente dividir tareas complejas en las más básicas. Para obtener más información acerca de los grupos de tareas, consulte [paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Para obtener más información acerca de los algoritmos paralelos, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).  
  
 Para crear una tarea ligera, llame a la [concurrency::ScheduleGroup::ScheduleTask](reference/schedulegroup-class.md#scheduletask), [concurrency::CurrentScheduler::ScheduleTask](reference/currentscheduler-class.md#scheduletask), o [concurrency::Scheduler::ScheduleTask ](reference/scheduler-class.md#scheduletask) (método). Para esperar a que finalice una tarea ligera, espere a que el programador primario apagar o usar un mecanismo de sincronización como un [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) objeto.  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo que muestra cómo adaptar código existente para usar una tarea ligera, vea [Tutorial: adaptar el código existente para usar tareas ligeras](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md).  
  
## <a name="see-also"></a>Vea también  
 [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Tutorial: Adaptar el código existente para usar tareas ligeras](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)

