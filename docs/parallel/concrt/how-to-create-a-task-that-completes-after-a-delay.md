---
title: "Cómo: crear una tarea que finaliza después de un retraso | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- task_completion_event class, example
- create a task that completes after a delay, example [C++]
ms.assetid: 3fc0a194-3fdb-4eba-8b8a-b890981a985d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f9547bb5e586c20a22ce79d1227fa5f15b3ea305
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-a-task-that-completes-after-a-delay"></a>Cómo: Crear una tarea que se complete después de un retardo
Este ejemplo muestra cómo utilizar el [Concurrency:: Task](../../parallel/concrt/reference/task-class.md), [Concurrency:: cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md), [cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md), [ Concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), [Concurrency:: Timer](../../parallel/concrt/reference/timer-class.md), y [Concurrency:: call](../../parallel/concrt/reference/call-class.md) clases para crear una tarea que finaliza después de un retraso. Puede usar este método para crear bucles que ocasionalmente sondean en busca de datos, introducen los tiempos de espera, retrasar el control de entrada de usuario durante un tiempo predeterminado y así sucesivamente.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestran las funciones `complete_after` y `cancel_after_timeout`. El `complete_after` función crea un `task` objeto que se completa después del retraso especificado. Usa un `timer` objeto y un `call` objeto para establecer un `task_completion_event` objeto después del retraso especificado. Mediante el uso de la `task_completion_event` (clase), puede definir una tarea que finaliza después de que un subproceso o de otra tarea indica que un valor está disponible. Cuando se establece el evento, completen las tareas de agente de escucha y sus continuaciones se programan para ejecutarse.  
  
> [!TIP]
>  Para obtener más información sobre la `timer` y `call` clases, que forman parte de la biblioteca de agentes asincrónicos, vea el artículo [los bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md).  
  
 El `cancel_after_timeout` función se basa en el `complete_after` función para cancelar una tarea si dicha tarea no se completa antes de un tiempo de espera especificado. El `cancel_after_timeout` función crea dos tareas. La primera tarea indica una ejecución correcta y completa una vez completada la tarea proporcionada; la segunda tarea indica un error y se completa después del tiempo de espera especificado. El `cancel_after_timeout` función crea una tarea de continuación que se ejecuta cuando se completa la tarea finalizó correctamente o no. Si la tarea de error ocurra primero, la continuación cancela el origen del token para cancelar la tarea global.  
  
 [!code-cpp[concrt-task-delay#1](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_1.cpp)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se calcula el recuento de números primos en el intervalo [0, 100000] varias veces. La operación se produce un error si no se completa en un límite de tiempo determinado. El `count_primes` función muestra cómo utilizar el `cancel_after_timeout` función. Cuenta el número de números primos del intervalo especificado y se produce un error si la tarea no se completa en el tiempo proporcionado. El `wmain` llamadas a funciones el `count_primes` función varias veces. Cada vez, divide por dos el límite de tiempo. El programa finaliza después de la operación no se completa en el límite de tiempo actual.  
  
 [!code-cpp[concrt-task-delay#2](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_2.cpp)]  
  
 Cuando se utiliza esta técnica para cancelar las tareas después de un retraso, las tareas no iniciadas no se inician después de cancela la tarea global. Sin embargo, es importante para las tareas de larga duración responder a la cancelación de una manera oportuna. Para obtener más información sobre la cancelación de tareas, consulte [cancelación en la biblioteca PPL](cancellation-in-the-ppl.md).  
  
## <a name="example"></a>Ejemplo  
 Este es el código completo de este ejemplo:  
  
 [!code-cpp[concrt-task-delay#3](../../parallel/concrt/codesnippet/cpp/how-to-create-a-task-that-completes-after-a-delay_3.cpp)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo que se denomina `task-delay.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe/EHsc tarea-delay.cpp**  
  
## <a name="see-also"></a>Vea también  
 [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [tarea (clase) (Runtime de simultaneidad)](../../parallel/concrt/reference/task-class.md)   
 [cancellation_token_source (clase)](../../parallel/concrt/reference/cancellation-token-source-class.md)   
 [cancellation_token (clase)](../../parallel/concrt/reference/cancellation-token-class.md)   
 [task_completion_event (clase)](../../parallel/concrt/reference/task-completion-event-class.md)   
 [Clase Timer](../../parallel/concrt/reference/timer-class.md)   
 [Call (clase)](../../parallel/concrt/reference/call-class.md)   
 [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)

