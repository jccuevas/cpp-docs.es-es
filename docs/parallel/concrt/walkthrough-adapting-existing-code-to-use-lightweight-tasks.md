---
title: 'Tutorial: Adaptar código existente para usar tareas ligeras'
ms.date: 11/04/2016
helpviewer_keywords:
- using lightweight tasks [Concurrency Runtime]
- lightweight tasks, using [Concurrency Runtime]
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
ms.openlocfilehash: 43e928e7d82b41b83fde5e8a7abaeeeb8d6fefa9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261224"
---
# <a name="walkthrough-adapting-existing-code-to-use-lightweight-tasks"></a>Tutorial: Adaptar código existente para usar tareas ligeras

En este tema se muestra cómo adaptar código existente que usa la API de Windows para crear y ejecutar un subproceso para una tarea ligera.

Un *tarea ligera* es una tarea que se programa directamente desde un [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) o [Concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objeto. Las tareas ligeras son útiles cuando se adapta código existente para usar la funcionalidad de programación del Runtime de simultaneidad.

## <a name="prerequisites"></a>Requisitos previos

Antes de empezar este tutorial, lea el tema [programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

En el siguiente ejemplo se muestra el uso típico de la API de Windows para crear y ejecutar un subproceso. Este ejemplo se usa el [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) función para llamar a la `MyThreadFunction` en un subproceso independiente.

### <a name="code"></a>Código

[!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]

### <a name="comments"></a>Comentarios

Este ejemplo produce el siguiente resultado:

```Output
Parameters = 50, 100
```

Los siguientes pasos muestran cómo adaptar el ejemplo de código para usar el Runtime de simultaneidad para realizar la misma tarea.

### <a name="to-adapt-the-example-to-use-a-lightweight-task"></a>Para adaptar el ejemplo para usar una tarea ligera

1. Agregue una directiva `#include` para el archivo de encabezado concrt.h.

[!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]

1. Agregue una directiva `using` para el espacio de nombres `concurrency`.

[!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]

1. Cambie la declaración de `MyThreadFunction` pasa usar la convención de llamada `__cdecl` y devolver `void`.

[!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]

1. Modificar el `MyData` estructura para incluir un [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) objeto que señala a la aplicación principal que la tarea ha finalizado.

[!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]

1. Reemplace la llamada a `CreateThread` con una llamada a la [concurrency::CurrentScheduler::ScheduleTask](reference/currentscheduler-class.md#scheduletask) método.

[!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]

1. Reemplace la llamada a `WaitForSingleObject` con una llamada a la [concurrency::event::wait](reference/event-class.md#wait) método para esperar a que finalice la tarea.

[!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]

1. Quite la llamada a `CloseHandle`.

1. Cambie la signatura de la definición de `MyThreadFunction` para que coincida con el paso 3.

[!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]

9. Al final de la `MyThreadFunction` de función, llame a la [concurrency::event::set](reference/event-class.md#set) método para señalar a la aplicación principal que la tarea ha finalizado.

[!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]

10. Quite la instrucción `return` de `MyThreadFunction`.

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

En el siguiente ejemplo completo se muestra código que usa una tarea ligera para llamar a la función `MyThreadFunction`.

### <a name="code"></a>Código

[!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]

### <a name="comments"></a>Comentarios

## <a name="see-also"></a>Vea también

[Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Scheduler (clase)](../../parallel/concrt/reference/scheduler-class.md)
