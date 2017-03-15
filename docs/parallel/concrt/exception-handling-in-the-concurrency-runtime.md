---
title: "Control de excepciones en el runtime de simultaneidad | Microsoft Docs"
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
  - "tareas ligeras, control de excepciones [Runtime de simultaneidad]"
  - "control de excepciones [Runtime de simultaneidad]"
  - "grupos de tareas estructurados, control de excepciones [Runtime de simultaneidad]"
  - "agentes, control de excepciones [Runtime de simultaneidad]"
  - "grupos de tareas, control de excepciones [Runtime de simultaneidad]"
ms.assetid: 4d1494fb-3089-4f4b-8cfb-712aa67d7a7a
caps.latest.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# Control de excepciones en el runtime de simultaneidad
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El Runtime de simultaneidad usa el control de excepciones de C\+\+ para comunicar muchas modalidades de errores.  Entre estos errores, se incluyen el uso no válido del runtime, errores de runtime, como el que se produce al no poder adquirir un recurso, y errores que afectan a funciones de trabajo que el usuario proporciona a las tareas y los grupos de tareas.  Cuando una tarea o un grupo de tareas produce una excepción, el runtime mantiene esa excepción y calcula las referencias en el contexto que espera a que finalice la tarea o el grupo de tareas.  En el caso de componentes tales como tareas ligeras y agentes, el runtime no administra las excepciones en nombre del usuario.  En estos casos, debe implementar su propio mecanismo del control de excepciones.  En este tema se describe cómo controla el runtime las excepciones que producen las tareas, los grupos de tareas, las tareas ligeras y los agentes asincrónicos, y cómo se responde a las excepciones en las aplicaciones.  
  
## Puntos clave  
  
-   Cuando una tarea o un grupo de tareas produce una excepción, el runtime mantiene esa excepción y calcula las referencias en el contexto que espera a que finalice la tarea o el grupo de tareas.  
  
-   Si es posible, delimite cada llamada a [concurrency::task::get](../Topic/task::get%20Method.md) y a [concurrency::task::wait](../Topic/task::wait%20Method.md) con un bloque de `try`\/`catch` para controlar los errores de los que es posible recuperarse.  El runtime finaliza la aplicación si una tarea produce una excepción y la tarea, una de sus continuaciones o la aplicación principal no detecta la excepción.  
  
-   Siempre se ejecuta una continuación basada en tareas, independientemente de si la tarea anterior se completó correctamente, produjo una excepción o se canceló.  No se ejecuta una continuación basada en valores si se inicia la tarea anterior o se cancela.  
  
-   Dado que las continuaciones basadas en tareas siempre se ejecutan, tal vez le interese agregar una continuación basada en tareas al final de la cadena de continuación.  Puede contribuir a garantizar que el código tenga en cuenta todas las excepciones.  
  
-   El runtime produce [concurrency::task\_canceled](../../parallel/concrt/reference/task-canceled-class.md) cuando llama a [concurrency::task::get](../Topic/task::get%20Method.md) y se cancela esa tarea.  
  
-   El runtime no administra excepciones para los agentes y las tareas ligeras.  
  
##  <a name="top"></a> En este documento  
  
-   [Tareas y continuaciones](#tasks)  
  
-   [Grupos de tareas y algoritmos paralelos](#task_groups)  
  
-   [Excepciones que produce el runtime](#runtime)  
  
-   [Varias excepciones](#multiple)  
  
-   [Cancelación](#cancellation)  
  
-   [Tareas ligeras](#lwts)  
  
-   [Agentes asincrónicos](#agents)  
  
##  <a name="tasks"></a> Tareas y continuaciones  
 En esta sección se describe la manera en que el runtime controla las excepciones que producen los objetos [concurrency::task](../../parallel/concrt/reference/task-class-concurrency-runtime.md) y sus continuaciones.  Para obtener más información acerca de la tarea y el modelo de continuación, vea [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 Cuando se produce una excepción en el cuerpo de una función de trabajo que se pasa a un objeto `task`, el runtime almacena esa excepción y calcula sus referencias en el contexto en el que se llama a [concurrency::task::get](../Topic/task::get%20Method.md) o [concurrency::task::wait](../Topic/task::wait%20Method.md).  En el documento [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md) se describen las continuaciones basadas en tareas frente a las continuaciones basadas en valores pero, en resumen, una continuación basada en valores toma un parámetro de tipo `T` y una continuación basada en tareas toma un parámetro de tipo `task<T>`.  Si una tarea que se inicia tiene una o varias continuaciones basadas en valores, dichas continuaciones no se programan para su ejecución.  En el siguiente ejemplo, se muestra este comportamiento:  
  
 [!code-cpp[concrt-eh-task#1](../../parallel/concrt/codesnippet/CPP/exception-handling-in-the-concurrency-runtime_1.cpp)]  
  
 Una continuación basada en tareas le permite administrar cualquier excepción producida por la tarea anterior.  Una ejecución basada en tareas siempre se ejecuta, independientemente de si la tarea se completó correctamente, produjo una excepción o se canceló.  Cuando una tarea produce una excepción, sus continuaciones basadas en tareas se programan para su ejecución.  En el ejemplo siguiente se muestra una tarea que se inicia siempre.  La tarea tiene dos continuaciones; una está basada en valores y la otra, en tareas.  La excepción basada en tareas se ejecuta siempre y, por tanto, puede capturar la excepción que genera la tarea anterior.  Cuando el ejemplo espera que terminen ambas continuaciones, la excepción se produce de nuevo porque la excepción de la tarea se produce siempre cuando se llama a `task::get` o `task::wait`.  
  
 [!code-cpp[concrt-eh-continuations#1](../../parallel/concrt/codesnippet/CPP/exception-handling-in-the-concurrency-runtime_2.cpp)]  
  
 Se recomienda usar continuaciones basadas en tareas para capturar excepciones que pueda controlar.  Dado que las continuaciones basadas en tareas siempre se ejecutan, tal vez le interese agregar una continuación basada en tareas al final de la cadena de continuación.  Puede contribuir a garantizar que el código tenga en cuenta todas las excepciones.  En el ejemplo siguiente se muestra una cadena de continuación básica basada en valores.  Se inicia la tercera tarea de la cadena y, por tanto, no se ejecuta ninguna continuación basada en valores que la siga.  Sin embargo, la continuación final está basada en tareas y, por tanto, siempre se ejecuta.  Esta continuación final controla la excepción que produce la tercera tarea.  
  
 Se recomienda capturar las excepciones más específicas que pueda.  Puede omitir esta continuación basada en tareas final si no tiene excepciones específicas que capturar.  Cualquier excepción seguirá siendo no controlada y puede finalizar la aplicación.  
  
 [!code-cpp[concrt-eh-task-chain#1](../../parallel/concrt/codesnippet/CPP/exception-handling-in-the-concurrency-runtime_3.cpp)]  
  
> [!TIP]
>  Puede utilizar el método [concurrency::task\_completion\_event::set\_exception](../../parallel/concrt/reference/task-completion-event-class.md) para asociar una excepción a un evento de finalización de la tarea.  En el documento [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md) se describe la clase [concurrency::task\_completion\_event](../../parallel/concrt/reference/task-completion-event-class.md) con mayor detalle.  
  
 [concurrency::task\_canceled](../../parallel/concrt/reference/task-canceled-class.md) es un tipo de excepción de runtime importante que está relacionado con `task`.  El runtime produce `task_canceled` cuando llama a `task::get` y se cancela esa tarea. \(Al contrario, `task::wait` devuelve [task\_status::canceled](../Topic/task_group_status%20Enumeration.md) y no se inicia\). Puede detectar y controlar esta excepción desde una continuación basada en tareas o cuando llama a `task::get`.  Para obtener más información sobre la cancelación de tareas, vea [Cancelación](../../parallel/concrt/cancellation-in-the-ppl.md).  
  
> [!CAUTION]
>  Nunca inicie `task_canceled` desde su código.  Llame a [concurrency::cancel\_current\_task](../Topic/cancel_current_task%20Function.md) en su lugar.  
  
 El runtime finaliza la aplicación si una tarea produce una excepción y la tarea, una de sus continuaciones o la aplicación principal no detecta la excepción.  Si se bloquea la aplicación, puede configurar Visual Studio para que se interrumpa cuando se produzcan excepciones de C\+\+.  Tras diagnosticar la ubicación de la excepción no controlada, utilice una continuación basada en tareas para controlarla.  
  
 En la sección [Excepciones que produce el runtime](#runtime) de este documento se describe con mayor detalle cómo trabajar con excepciones de runtime.  
  
 \[[Arriba](#top)\]  
  
##  <a name="task_groups"></a> Grupos de tareas y algoritmos paralelos  
 En esta sección se describe cómo controla el runtime las excepciones que producen los grupos de tareas.  Esta sección también se aplica a algoritmos paralelos como [concurrency::parallel\_for](../Topic/parallel_for%20Function.md), puesto que estos algoritmos se basan en grupos de tareas.  
  
> [!CAUTION]
>  Asegúrese de que entiende los efectos que tienen las excepciones sobre las tareas dependientes.  Para obtener información sobre prácticas recomendadas acerca del uso de control de excepciones con tareas o algoritmos paralelos, vea la sección [Entienda cómo afectan a la destrucción de objetos la cancelación y el control de excepciones](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) del tema sobre procedimientos recomendados en la biblioteca de patrones de procesamiento paralelo \(PPL\).  
  
 Para obtener más información acerca de los grupos de tareas, vea [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  Para obtener más información acerca de los algoritmos paralelos, vea [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).  
  
 Cuando se produce una excepción en el cuerpo de una función de trabajo que se pasa a un objeto [concurrency::task\_group](../Topic/task_group%20Class.md) o [concurrency::structured\_task\_group](../../parallel/concrt/reference/structured-task-group-class.md), el runtime almacena esa excepción y calcula las referencias en el contexto que llama a [concurrency::task\_group::wait](../Topic/task_group::wait%20Method.md), [concurrency::structured\_task\_group::wait](../Topic/structured_task_group::wait%20Method.md), [concurrency::task\_group::run\_and\_wait](../Topic/task_group::run_and_wait%20Method.md) o [concurrency::structured\_task\_group::run\_and\_wait](../Topic/structured_task_group::run_and_wait%20Method.md).  El runtime también detiene todas las tareas activas que están en el grupo de tareas \(incluidas las que se encuentran en grupos de tareas secundarios\) y descarta cualquier tarea que no se haya iniciado todavía.  
  
 En el siguiente ejemplo se muestra la estructura básica de una función de trabajo que produce una excepción.  En el ejemplo se usa un objeto `task_group` para imprimir los valores de dos objetos `point` en paralelo.  La función de trabajo `print_point` imprime los valores de un objeto `point` en la consola.  La función de trabajo produce una excepción si el valor de entrada es `NULL`.  El runtime almacena esta excepción y calcula las referencias en el contexto que llama a `task_group::wait`.  
  
 [!code-cpp[concrt-eh-task-group#1](../../parallel/concrt/codesnippet/CPP/exception-handling-in-the-concurrency-runtime_4.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **X \= 15, Y \= 30**  
**Caught exception: point is NULL.** Para obtener un ejemplo completo donde se usa el control de excepciones en un grupo de tareas, vea [Cómo: Usar el control de excepciones para interrumpir un bucle Parallel](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).  
  
 \[[Arriba](#top)\]  
  
##  <a name="runtime"></a> Excepciones que produce el runtime  
 Una excepción puede ser el resultado de una llamada al runtime.  La mayoría de los tipos de excepción, salvo [concurrency::task\_canceled](../../parallel/concrt/reference/task-canceled-class.md) y [concurrency::operation\_timed\_out](../../parallel/concrt/reference/operation-timed-out-class.md), indican un error de programación.  Normalmente, estos errores son irrecuperables y, por consiguiente, no se deben detectar ni administrar en el código de aplicación.  Sugerimos sólo detectar o controlar los errores irrecuperables en el código de aplicación si es necesario diagnosticar errores de programación.  Sin embargo, conocer los tipos de excepciones que define el runtime puede ayudar a diagnosticar los errores de programación.  
  
 El mecanismo de control de excepciones es el mismo para las excepciones que produce el runtime y las excepciones que producen las funciones de trabajo.  Por ejemplo, la función [concurrency::receive](../Topic/receive%20Function.md) produce la excepción `operation_timed_out` cuando no recibe un mensaje en el período de tiempo especificado.  Si `receive` produce una excepción en una función de trabajo que se pasa a un grupo de tareas, el runtime almacena esa excepción y calcula las referencias en el contexto que llama a `task_group::wait`, `structured_task_group::wait`, `task_group::run_and_wait` o `structured_task_group::run_and_wait`.  
  
 En el ejemplo siguiente se usa el algoritmo [concurrency::parallel\_invoke](../Topic/parallel_invoke%20Function.md) para ejecutar dos tareas en paralelo.  La primera tarea espera cinco segundos y, a continuación, envía un mensaje a un búfer de mensajes.  La segunda tarea usa la función `receive` para esperar tres segundos a recibir un mensaje desde el mismo búfer de mensajes.  La función `receive` produce la excepción `operation_timed_out` si no recibe el mensaje en dicho período de tiempo.  
  
 [!code-cpp[concrt-eh-time-out#1](../../parallel/concrt/codesnippet/CPP/exception-handling-in-the-concurrency-runtime_5.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **La operación agotó el tiempo de espera.** Para evitar la terminación anómala de la aplicación, asegúrese de que el código controla las excepciones cuando llama al runtime.  Controle también las excepciones al llamar a código externo que use el Runtime de simultaneidad, por ejemplo, una biblioteca de otro fabricante.  
  
 \[[Arriba](#top)\]  
  
##  <a name="multiple"></a> Varias excepciones  
 Si una tarea o algoritmo paralelo recibe varias excepciones, el runtime calcula las referencias sólo de una de esas excepciones en el contexto de la llamada.  El runtime no garantiza para qué excepción se calculan las referencias.  
  
 En el ejemplo siguiente se usa el algoritmo `parallel_for` para imprimir números en la consola.  Produce una excepción si el valor de entrada es menor que un determinado valor mínimo o mayor que un determinado valor máximo.  En este ejemplo, varias funciones de trabajo pueden producir una excepción.  
  
 [!code-cpp[concrt-eh-multiple#1](../../parallel/concrt/codesnippet/CPP/exception-handling-in-the-concurrency-runtime_6.cpp)]  
  
 A continuación, se muestra la salida de este ejemplo.  
  
  **8**  
**2**  
**9**  
**3**  
**10**  
**4**  
**5**  
**6**  
**7**  
**Caught exception: \-5: the value is less than the minimum.** \[[Arriba](#top)\]  
  
##  <a name="cancellation"></a> Cancelación  
 No todas las excepciones indican un error.  Por ejemplo, un algoritmo de búsqueda podría utilizar el control de excepciones para detener su tarea asociada cuando encuentra el resultado.  Para obtener más información sobre cómo usar los mecanismos de cancelación en el código, vea [Cancelación](../../parallel/concrt/cancellation-in-the-ppl.md).  
  
 \[[Arriba](#top)\]  
  
##  <a name="lwts"></a> Tareas ligeras  
 Una tarea ligera es aquella que se programa directamente desde un objeto [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md).  Las tareas ligeras implican una menor sobrecarga que las tareas ordinarias.  Sin embargo, el runtime no detecta las excepciones producidas por las tareas ligeras.  En su lugar, el controlador de excepciones no controladas, que de forma predeterminada finaliza el proceso, detecta la excepción.  Por consiguiente, use un mecanismo de control de errores adecuado en su aplicación.  Para obtener más información sobre las tareas ligeras, vea [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
 \[[Arriba](#top)\]  
  
##  <a name="agents"></a> Agentes asincrónicos  
 Como sucede con las tareas ligeras, el runtime no controla las excepciones producidas por agentes asincrónicos.  
  
 En el ejemplo siguiente se muestra una manera de controlar excepciones en una clase que se deriva de [concurrency::agent](../../parallel/concrt/reference/agent-class.md).  En este ejemplo se define la clase `points_agent`.  El método `points_agent::run` lee los objetos `point` del búfer de mensajes y los imprime en la consola.  El método `run` produce una excepción si recibe un puntero `NULL`.  
  
 El método `run` rodea todo el trabajo en un bloque `try`\-`catch`.  El bloque `catch` almacena la excepción en un búfer de mensajes.  La aplicación comprueba si el agente encontró un error leyendo el búfer cuando el agente finaliza.  
  
 [!code-cpp[concrt-eh-agents#1](../../parallel/concrt/codesnippet/CPP/exception-handling-in-the-concurrency-runtime_7.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **X: 10 Y: 20**  
**X: 20 Y: 30**  
**error occurred in agent: point must not be NULL**  
**the status of the agent is: done** Dado que el bloque `try`\-`catch` existe fuera del bucle `while`, el agente finaliza el procesamiento cuando encuentra el primer error.  Si el bloque `try`\-`catch` estuviese dentro del bucle `while`, el agente continuaría después de producirse el error.  
  
 En este ejemplo se almacenan las excepciones en un búfer de mensajes para que otro componente pueda supervisar los errores del agente mientras se ejecuta.  En este ejemplo se usa un objeto [concurrency::single\_assignment](../../parallel/concrt/reference/single-assignment-class.md) para almacenar el error.  Cuando un agente controla varias excepciones, la clase `single_assignment` almacena únicamente el primer mensaje que se le pasa.  Para almacenar solo la última excepción, use la clase [concurrency::overwrite\_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md).  Para almacenar todas las excepciones, use la clase [concurrency::unbounded\_buffer](../Topic/unbounded_buffer%20Class.md).  Para obtener más información acerca de estos bloques de mensajes, vea [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md).  
  
 Para obtener más información sobre los agentes asincrónicos, vea [Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md).  
  
 \[[Arriba](#top)\]  
  
##  <a name="summary"></a> Resumen  
 \[[Arriba](#top)\]  
  
## Vea también  
 [Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime.md)   
 [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)   
 [Cancelación](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)