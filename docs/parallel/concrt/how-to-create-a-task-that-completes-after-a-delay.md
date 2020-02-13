---
title: 'Cómo: Crear una tarea que se complete después de un retardo'
ms.date: 11/04/2016
helpviewer_keywords:
- task_completion_event class, example
- create a task that completes after a delay, example [C++]
ms.assetid: 3fc0a194-3fdb-4eba-8b8a-b890981a985d
ms.openlocfilehash: 76189f45eb486e06b040155f6697bf003659b474
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141743"
---
# <a name="how-to-create-a-task-that-completes-after-a-delay"></a>Cómo: Crear una tarea que se complete después de un retardo

En este ejemplo se muestra cómo usar las clases Concurrency: [: Task](../../parallel/concrt/reference/task-class.md), [Concurrency:: cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md), [Concurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md), [Concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), [Concurrency:: Timer](../../parallel/concrt/reference/timer-class.md)y [Concurrency:: Call](../../parallel/concrt/reference/call-class.md) para crear una tarea que se completa después de un retraso. Puede usar este método para crear bucles que sondeen ocasionalmente los datos, introduzcan tiempos de espera, retrasen el control de los datos proporcionados por el usuario durante un tiempo predeterminado, etc.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran las funciones `complete_after` y `cancel_after_timeout`. La función `complete_after` crea un objeto `task` que se completa después del retraso especificado. Utiliza un objeto `timer` y un objeto `call` para establecer un objeto `task_completion_event` después del retraso especificado. Mediante el uso de la clase `task_completion_event`, puede definir una tarea que se completa después de que un subproceso u otra tarea señale que un valor está disponible. Cuando se establece el evento, las tareas del agente de escucha se completan y sus continuaciones se programan para ejecutarse.

> [!TIP]
> Para obtener más información sobre las clases `timer` y `call`, que forman parte de la biblioteca de agentes asincrónicos, vea [bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md).

La función `cancel_after_timeout` se basa en la función `complete_after` para cancelar una tarea si esa tarea no se completa antes de un tiempo de espera determinado. La función `cancel_after_timeout` crea dos tareas. La primera tarea indica que se ha realizado correctamente y se completa después de que se complete la tarea proporcionada; la segunda tarea indica un error y se completa después del tiempo de espera especificado. La función `cancel_after_timeout` crea una tarea de continuación que se ejecuta cuando se completa la tarea correcto o con errores. Si la tarea de error se completa primero, la continuación cancela el origen del token para cancelar la tarea global.

[!code-cpp[concrt-task-delay#1](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_1.cpp)]

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se calcula el recuento de números primos en el intervalo [0, 100000] varias veces. Se produce un error en la operación si no se completa en un límite de tiempo determinado. La función `count_primes` muestra cómo utilizar la función `cancel_after_timeout`. Cuenta el número de primos en el intervalo especificado y produce un error si la tarea no se completa en el tiempo proporcionado. La función `wmain` llama varias veces a la función `count_primes`. Cada vez, se divide el límite de tiempo. El programa finaliza después de que la operación no se complete en el límite de tiempo actual.

[!code-cpp[concrt-task-delay#2](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_2.cpp)]

Cuando se usa esta técnica para cancelar tareas después de un retraso, las tareas no iniciadas no se iniciarán después de que se cancele la tarea global. Sin embargo, es importante que cualquier tarea de ejecución prolongada responda a la cancelación de manera oportuna. Para obtener más información sobre la cancelación de tareas, vea [cancelación en la biblioteca PPL](cancellation-in-the-ppl.md).

## <a name="example"></a>Ejemplo

Este es el código completo de este ejemplo:

[!code-cpp[concrt-task-delay#3](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_3.cpp)]

## <a name="compiling-the-code"></a>Compilar el código

Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `task-delay.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl. exe/EHsc Task-Delay. cpp**

## <a name="see-also"></a>Consulte también

[Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[task (clase) (Runtime de simultaneidad)](../../parallel/concrt/reference/task-class.md)<br/>
[cancellation_token_source (clase)](../../parallel/concrt/reference/cancellation-token-source-class.md)<br/>
[cancellation_token (clase)](../../parallel/concrt/reference/cancellation-token-class.md)<br/>
[task_completion_event (clase)](../../parallel/concrt/reference/task-completion-event-class.md)<br/>
[timer (clase)](../../parallel/concrt/reference/timer-class.md)<br/>
[call (clase)](../../parallel/concrt/reference/call-class.md)<br/>
[Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)
