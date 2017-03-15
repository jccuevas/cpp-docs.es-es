---
title: "C&#243;mo: Crear una tarea que se complete despu&#233;s de un retardo | Microsoft Docs"
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
  - "task_completion_event (clase), ejemplo"
  - "crear una tarea que finaliza después de un retraso, ejemplo [C++]"
ms.assetid: 3fc0a194-3fdb-4eba-8b8a-b890981a985d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# C&#243;mo: Crear una tarea que se complete despu&#233;s de un retardo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este ejemplo muestra cómo utilizar el [Concurrency:: Task](../../parallel/concrt/reference/task-class-concurrency-runtime.md), [Concurrency:: cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md), [cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md), [Concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), "Concurrency:: Timer" y [Concurrency:: call](../../parallel/concrt/reference/call-class.md) clases para crear una tarea que finaliza después de un retraso. Puede utilizar este método para crear bucles que ocasionalmente sondean en busca de datos, introducen los tiempos de espera, retrasen el control de entrada de usuario durante un tiempo predeterminado y así sucesivamente.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestran las funciones `complete_after` y `cancel_after_timeout`. El `complete_after` función crea un `task` objeto que finalice después del retraso especificado. Utiliza un `timer` objeto y un `call` objeto para establecer un `task_completion_event` objeto después del retraso especificado. Mediante el uso de la `task_completion_event` (clase), puede definir una tarea que finaliza después de que un subproceso u otra tarea indica que un valor está disponible. Cuando se establece el evento, completen las tareas de agente de escucha y sus continuaciones se programan para ejecutarse.  
  
> [!TIP]
>  Para obtener más información acerca de la `timer` y `call` clases que forman parte de la biblioteca de agentes asincrónicos, vea [bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md).  
  
 El `cancel_after_timeout` función se basa en el `complete_after` función para cancelar una tarea si dicha tarea no se completa antes de un tiempo de espera. El `cancel_after_timeout` función crea dos tareas. La primera tarea indica éxito y finaliza después de que se complete la tarea proporcionada; la segunda tarea indica un error y finaliza tras el tiempo de espera especificado. El `cancel_after_timeout` función crea una tarea de continuación que se ejecuta cuando se completa la tarea de éxito o error. Si la tarea de error finaliza primero, la continuación cancela el origen del token para cancelar la tarea.  
  
 [!code-cpp[concrt-task-delay#1](../../parallel/concrt/codesnippet/CPP/how-to-create-a-task-that-completes-after-a-delay_1.cpp)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se calcula el recuento de números primos en el intervalo [0, 100000] varias veces. Se produce un error en la operación si no se completa en un límite de tiempo determinado. El `count_primes` función muestra cómo utilizar el `cancel_after_timeout` (función). Cuenta el número de números primos del intervalo especificado y se produce un error si no se completa la tarea en el tiempo proporcionado. El `wmain` llamadas a funciones del `count_primes` función varias veces. Cada vez, lo divide por dos el límite de tiempo. El programa termina después de la operación no se completa en el límite de tiempo actual.  
  
 [!code-cpp[concrt-task-delay#2](../../parallel/concrt/codesnippet/CPP/how-to-create-a-task-that-completes-after-a-delay_2.cpp)]  
  
 Cuando se utiliza esta técnica para cancelar tareas después de un retraso, no se iniciará cualquier tarea que no han comenzado después de cancela la tarea. Sin embargo, es importante para las tareas de ejecución prolongada responder a la cancelación de manera oportuna. En este ejemplo, el `count_primes` llamadas al método el [Concurrency:: is_task_cancellation_requested](../../misc/is-task-cancellation-requested-function.md) y `cancel_current_task` funciones para responder a la cancelación. (Como alternativa, puede llamar a la [Concurrency:: interruption_point](../Topic/interruption_point%20Function.md) función). Para obtener más información sobre la cancelación de tareas, consulte [cancelación](../../parallel/concrt/cancellation-in-the-ppl.md).  
  
## <a name="example"></a>Ejemplo  
 Este es el código completo de este ejemplo:  
  
 [!code-cpp[concrt-task-delay#3](../../parallel/concrt/codesnippet/CPP/how-to-create-a-task-that-completes-after-a-delay_3.cpp)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `task-delay.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe/EHsc tarea-delay.cpp**  
  
## <a name="see-also"></a>Vea también  
 [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [tarea (clase) (Runtime de simultaneidad)](../../parallel/concrt/reference/task-class-concurrency-runtime.md)   
 [cancellation_token_source (clase)](../../parallel/concrt/reference/cancellation-token-source-class.md)   
 [cancellation_token (clase)](../../parallel/concrt/reference/cancellation-token-class.md)   
 [task_completion_event (clase)](../../parallel/concrt/reference/task-completion-event-class.md)   
 [is_task_cancellation_requested (función)](../../misc/is-task-cancellation-requested-function.md)   
 [cancel_current_task (función)](../Topic/cancel_current_task%20Function.md)   
 [interruption_point (función)](../Topic/interruption_point%20Function.md)   
 [Call (clase)](../../parallel/concrt/reference/call-class.md)   
 [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Cancelación](../../parallel/concrt/cancellation-in-the-ppl.md)