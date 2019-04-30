---
title: Control de excepciones en el runtime de simultaneidad
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks, exception handling [Concurrency Runtime]
- exception handling [Concurrency Runtime]
- structured task groups, exception handling [Concurrency Runtime]
- agents, exception handling [Concurrency Runtime]
- task groups, exception handling [Concurrency Runtime]
ms.assetid: 4d1494fb-3089-4f4b-8cfb-712aa67d7a7a
ms.openlocfilehash: 8239913c369605503134a9ea4c99789528911868
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413936"
---
# <a name="exception-handling-in-the-concurrency-runtime"></a>Control de excepciones en el runtime de simultaneidad

El Runtime de simultaneidad usa el control de excepciones de C++ para comunicar muchas modalidades de errores. Entre estos errores, se incluyen el uso no válido del runtime, errores de runtime, como el que se produce al no poder adquirir un recurso, y errores que afectan a funciones de trabajo que el usuario proporciona a las tareas y los grupos de tareas. Cuando una tarea o un grupo de tareas produce una excepción, el runtime mantiene esa excepción y serializa las referencias en el contexto que espera a que finalice la tarea o el grupo de tareas. En el caso de componentes tales como tareas ligeras y agentes, el runtime no administra las excepciones en nombre del usuario. En estos casos, debe implementar su propio mecanismo del control de excepciones. En este tema se describe cómo controla el runtime las excepciones que producen las tareas, los grupos de tareas, las tareas ligeras y los agentes asincrónicos, y cómo se responde a las excepciones en las aplicaciones.

## <a name="key-points"></a>Puntos clave

- Cuando una tarea o un grupo de tareas produce una excepción, el runtime mantiene esa excepción y serializa las referencias en el contexto que espera a que finalice la tarea o el grupo de tareas.

- Cuando sea posible, delimite cada llamada a [concurrency::task::get](reference/task-class.md#get) y [concurrency::task::wait](reference/task-class.md#wait) con un `try` / `catch` bloque para controlar los errores que puede recuperar De. El runtime finaliza la aplicación si una tarea produce una excepción y la tarea, una de sus continuaciones o la aplicación principal no detecta la excepción.

- Siempre se ejecuta una continuación basada en tareas, independientemente de si la tarea anterior se completó correctamente, produjo una excepción o se canceló. No se ejecuta una continuación basada en valores si se inicia la tarea anterior o se cancela.

- Dado que las continuaciones basadas en tareas siempre se ejecutan, tal vez le interese agregar una continuación basada en tareas al final de la cadena de continuación. Puede contribuir a garantizar que el código tenga en cuenta todas las excepciones.

- El runtime produce [Concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md) cuando se llama a [concurrency::task::get](reference/task-class.md#get) y se cancela esa tarea.

- El runtime no administra excepciones para los agentes y las tareas ligeras.

##  <a name="top"></a> En este documento

- [Tareas y continuaciones](#tasks)

- [Grupos de tareas y algoritmos paralelos](#task_groups)

- [Excepciones producidas por el tiempo de ejecución](#runtime)

- [Varias excepciones](#multiple)

- [Cancelación](#cancellation)

- [Tareas ligeras](#lwts)

- [Agentes asincrónicos](#agents)

##  <a name="tasks"></a> Tareas y continuaciones

Esta sección describe cómo el runtime controla las excepciones producidas por [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) objetos y sus continuaciones. Para obtener más información sobre el modelo de tarea y a continuación, consulte [paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Cuando se produce una excepción en el cuerpo de una función de trabajo que se pasa a un `task` de objeto, el runtime almacena esa excepción y calcula las referencias en el contexto que llama a [concurrency::task::get](reference/task-class.md#get) o [concurrency:: Task:: wait](reference/task-class.md#wait). El documento [paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md) describe basado en tareas frente a continuaciones basadas en valores, pero, en resumen, una continuación basada en valores toma un parámetro de tipo `T` y una continuación basada en tareas toma un parámetro de tipo `task<T>`. Si una tarea que se inicia tiene una o varias continuaciones basadas en valores, dichas continuaciones no se programan para su ejecución. En el siguiente ejemplo, se muestra este comportamiento:

[!code-cpp[concrt-eh-task#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_1.cpp)]

Una continuación basada en tareas le permite administrar cualquier excepción producida por la tarea anterior. Una ejecución basada en tareas siempre se ejecuta, independientemente de si la tarea se completó correctamente, produjo una excepción o se canceló. Cuando una tarea produce una excepción, sus continuaciones basadas en tareas se programan para su ejecución. En el ejemplo siguiente se muestra una tarea que se inicia siempre. La tarea tiene dos continuaciones; una está basada en valores y la otra, en tareas. La excepción basada en tareas se ejecuta siempre y, por tanto, puede capturar la excepción que genera la tarea anterior. Cuando el ejemplo espera que terminen ambas continuaciones, la excepción se produce de nuevo porque la excepción de la tarea se produce siempre cuando se llama a `task::get` o `task::wait`.

[!code-cpp[concrt-eh-continuations#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_2.cpp)]

Se recomienda usar continuaciones basadas en tareas para capturar excepciones que pueda controlar. Dado que las continuaciones basadas en tareas siempre se ejecutan, tal vez le interese agregar una continuación basada en tareas al final de la cadena de continuación. Puede contribuir a garantizar que el código tenga en cuenta todas las excepciones. En el ejemplo siguiente se muestra una cadena de continuación básica basada en valores. Se inicia la tercera tarea de la cadena y, por tanto, no se ejecuta ninguna continuación basada en valores que la siga. Sin embargo, la continuación final está basada en tareas y, por tanto, siempre se ejecuta. Esta continuación final controla la excepción que produce la tercera tarea.

Se recomienda capturar las excepciones más específicas que pueda. Puede omitir esta continuación basada en tareas final si no tiene excepciones específicas que capturar. Cualquier excepción seguirá siendo no controlada y puede finalizar la aplicación.

[!code-cpp[concrt-eh-task-chain#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_3.cpp)]

> [!TIP]
>  Puede usar el [concurrency::task_completion_event::set_exception](../../parallel/concrt/reference/task-completion-event-class.md) para asociar una excepción con un evento de finalización de tarea. El documento [paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md) describe la [Concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) clase con mayor detalle.

[Concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md) es un tipo de excepción de runtime importante que se relaciona con `task`. El runtime produce `task_canceled` cuando llama a `task::get` y se cancela esa tarea. (A la inversa, `task::wait` devuelve [task_status:: Canceled](reference/concurrency-namespace-enums.md#task_group_status) y no produce una excepción.) Puede detectar y controlar esta excepción desde una continuación basada en tareas o cuando llama a `task::get`. Para obtener más información sobre la cancelación de tareas, consulte [cancelación en PPL](cancellation-in-the-ppl.md).

> [!CAUTION]
>  Nunca inicie `task_canceled` desde su código. Llame a [Concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) en su lugar.

El runtime finaliza la aplicación si una tarea produce una excepción y la tarea, una de sus continuaciones o la aplicación principal no detecta la excepción. Si se bloquea la aplicación, puede configurar Visual Studio para que se interrumpa cuando se produzcan excepciones de C++. Tras diagnosticar la ubicación de la excepción no controlada, utilice una continuación basada en tareas para controlarla.

La sección [excepciones iniciadas por el tiempo de ejecución](#runtime) en este documento se describe cómo trabajar con excepciones en tiempo de ejecución con más detalle.

[[Arriba](#top)]

##  <a name="task_groups"></a> Grupos de tareas y algoritmos paralelos

En esta sección se describe cómo controla el runtime las excepciones que producen los grupos de tareas. En esta sección también se aplica a los algoritmos paralelos como [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for), ya que estos algoritmos se basan en grupos de tareas.

> [!CAUTION]
>  Asegúrese de que entiende los efectos que tienen las excepciones sobre las tareas dependientes. Para los procedimientos recomendados sobre cómo usar el control de excepciones con tareas o algoritmos paralelos, vea el [entender cómo la cancelación y la excepción control afectan a la destrucción de objetos](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) sección de procedimientos recomendados en el paralelo Tema de la biblioteca de patrones.

Para obtener más información acerca de los grupos de tareas, consulte [paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Para obtener más información acerca de los algoritmos paralelos, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).

Cuando se produce una excepción en el cuerpo de una función de trabajo que se pasa a un [Concurrency:: task_group](reference/task-group-class.md) o [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) de objeto, el runtime almacena esa excepción y calcula las referencias en el contexto que llama a [task_group](reference/task-group-class.md#wait), [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait), [run_and_wait](reference/task-group-class.md#run_and_wait), o [concurrency::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait). El runtime también detiene todas las tareas activas que están en el grupo de tareas (incluidas las que se encuentran en grupos de tareas secundarios) y descarta cualquier tarea que no se haya iniciado todavía.

En el siguiente ejemplo se muestra la estructura básica de una función de trabajo que produce una excepción. En el ejemplo se usa un objeto `task_group` para imprimir los valores de dos objetos `point` en paralelo. La función de trabajo `print_point` imprime los valores de un objeto `point` en la consola. La función de trabajo produce una excepción si el valor de entrada es `NULL`. El runtime almacena esta excepción y calcula las referencias en el contexto que llama a `task_group::wait`.

[!code-cpp[concrt-eh-task-group#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_4.cpp)]

Este ejemplo produce el siguiente resultado:

```Output
X = 15, Y = 30Caught exception: point is NULL.
```

Para obtener un ejemplo completo que usa el control de excepciones en un grupo de tareas, consulte [Cómo: Usar excepciones para interrumpir un bucle Parallel](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

[[Arriba](#top)]

##  <a name="runtime"></a> Excepciones producidas por el tiempo de ejecución

Una excepción puede ser el resultado de una llamada al runtime. La mayoría de los tipos de excepción, excepto para [Concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md) y [Concurrency:: operation_timed_out](../../parallel/concrt/reference/operation-timed-out-class.md), indicar un error de programación. Normalmente, estos errores son irrecuperables y, por consiguiente, no se deben detectar ni administrar en el código de aplicación. Sugerimos sólo detectar o controlar los errores irrecuperables en el código de aplicación si es necesario diagnosticar errores de programación. Sin embargo, conocer los tipos de excepciones que define el runtime puede ayudar a diagnosticar los errores de programación.

El mecanismo de control de excepciones es el mismo para las excepciones que produce el runtime y las excepciones que producen las funciones de trabajo. Por ejemplo, el [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) función produce `operation_timed_out` cuando no recibe un mensaje en el período de tiempo especificado. Si `receive` produce una excepción en una función de trabajo que se pasa a un grupo de tareas, el runtime almacena esa excepción y serializa las referencias en el contexto que llama a `task_group::wait`, `structured_task_group::wait`, `task_group::run_and_wait` o `structured_task_group::run_and_wait`.

En el ejemplo siguiente se usa el [Concurrency:: parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algoritmo para ejecutar dos tareas en paralelo. La primera tarea espera cinco segundos y, a continuación, envía un mensaje a un búfer de mensajes. La segunda tarea usa la función `receive` para esperar tres segundos a recibir un mensaje desde el mismo búfer de mensajes. La función `receive` produce la excepción `operation_timed_out` si no recibe el mensaje en dicho período de tiempo.

[!code-cpp[concrt-eh-time-out#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_5.cpp)]

Este ejemplo produce el siguiente resultado:

```Output
The operation timed out.
```

Para evitar la terminación anómala de la aplicación, asegúrese de que el código controla las excepciones cuando llama al runtime. Controle también las excepciones al llamar a código externo que use el Runtime de simultaneidad, por ejemplo, una biblioteca de otro fabricante.

[[Arriba](#top)]

##  <a name="multiple"></a> Varias excepciones

Si una tarea o algoritmo paralelo recibe varias excepciones, el runtime serializa las referencias sólo de una de esas excepciones en el contexto de la llamada. El runtime no garantiza para qué excepción se calculan las referencias.

En el ejemplo siguiente se usa el algoritmo `parallel_for` para imprimir números en la consola. Produce una excepción si el valor de entrada es menor que un determinado valor mínimo o mayor que un determinado valor máximo. En este ejemplo, varias funciones de trabajo pueden producir una excepción.

[!code-cpp[concrt-eh-multiple#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_6.cpp)]

A continuación, se muestra la salida de este ejemplo.

```Output
8293104567Caught exception: -5: the value is less than the minimum.
```

[[Arriba](#top)]

##  <a name="cancellation"></a> Cancelación

No todas las excepciones indican un error. Por ejemplo, un algoritmo de búsqueda podría utilizar el control de excepciones para detener su tarea asociada cuando encuentra el resultado. Para obtener más información sobre cómo usar los mecanismos de cancelación en el código, consulte [cancelación en PPL](../../parallel/concrt/cancellation-in-the-ppl.md).

[[Arriba](#top)]

##  <a name="lwts"></a> Tareas ligeras

Una tarea ligera es una tarea que se programa directamente desde un [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) objeto. Las tareas ligeras implican una menor sobrecarga que las tareas ordinarias. Sin embargo, el runtime no detecta las excepciones producidas por las tareas ligeras. En su lugar, el controlador de excepciones no controladas, que de forma predeterminada finaliza el proceso, detecta la excepción. Por consiguiente, use un mecanismo de control de errores adecuado en su aplicación. Para obtener más información sobre las tareas ligeras, vea [programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Arriba](#top)]

##  <a name="agents"></a> Agentes asincrónicos

Como sucede con las tareas ligeras, el runtime no controla las excepciones producidas por agentes asincrónicos.

El ejemplo siguiente muestra una manera de controlar las excepciones en una clase que derive de [Concurrency:: Agent](../../parallel/concrt/reference/agent-class.md). En este ejemplo se define la clase `points_agent`. El método `points_agent::run` lee los objetos `point` del búfer de mensajes y los imprime en la consola. El método `run` produce una excepción si recibe un puntero `NULL`.

El `run` método rodea todo el trabajo en un `try` - `catch` bloque. El bloque `catch` almacena la excepción en un búfer de mensajes. La aplicación comprueba si el agente encontró un error leyendo el búfer cuando el agente finaliza.

[!code-cpp[concrt-eh-agents#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_7.cpp)]

Este ejemplo produce el siguiente resultado:

```Output
X: 10 Y: 20
X: 20 Y: 30
error occurred in agent: point must not be NULL
the status of the agent is: done
```

Dado que el `try` - `catch` bloque existe fuera de la `while` bucle, el agente finaliza el procesamiento cuando encuentra el primer error. Si el `try` - `catch` bloque estaba dentro del `while` bucle, el agente continuaría después de que se produce un error.

En este ejemplo se almacenan las excepciones en un búfer de mensajes para que otro componente pueda supervisar los errores del agente mientras se ejecuta. Este ejemplo se usa un [Concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) objeto para almacenar el error. Cuando un agente controla varias excepciones, la clase `single_assignment` almacena únicamente el primer mensaje que se le pasa. Para almacenar solo la última excepción, use el [Concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) clase. Para almacenar todas las excepciones, use la [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) clase. Para obtener más información acerca de estos bloques de mensajes, vea [bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md).

Para obtener más información sobre los agentes asincrónicos, vea [agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md).

[[Arriba](#top)]

##  <a name="summary"></a> Resumen

[[Arriba](#top)]

## <a name="see-also"></a>Vea también

[Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime.md)<br/>
[Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)<br/>
[Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)<br/>
[Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)
