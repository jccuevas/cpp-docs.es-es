---
title: 'Tutorial: Usar el Runtime de simultaneidad en una aplicación habilitada para COM'
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, use with COM
- COM, use with the Concurrency Runtime
ms.assetid: a7c798b8-0fc8-4bee-972f-22ef158f7f48
ms.openlocfilehash: 9d306377be4a000c54fb5556b15263a15b2d4618
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278202"
---
# <a name="walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application"></a>Tutorial: Usar el Runtime de simultaneidad en una aplicación habilitada para COM

En este documento se muestra cómo se usa el Runtime de simultaneidad en una aplicación que emplea el Modelo de objetos componentes (COM).

## <a name="prerequisites"></a>Requisitos previos

Lea los documentos siguientes antes de iniciar este tutorial:

- [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)

- [Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)

- [Control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)

Para obtener más información acerca de COM, consulte [modelo de objetos componentes (COM)](/windows/desktop/com/component-object-model--com--portal).

## <a name="managing-the-lifetime-of-the-com-library"></a>Administrar la duración de la biblioteca COM

Aunque el uso de COM con el Runtime de simultaneidad sigue los mismos principios que cualquier otro mecanismo de simultaneidad, las siguientes instrucciones pueden ayudarle a usar conjuntamente estas bibliotecas de forma eficaz.

- Debe llamar un subproceso [CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex) antes de usar la biblioteca COM.

- Un subproceso puede llamar varias veces a `CoInitializeEx` siempre que proporcione los mismos argumentos en cada llamada.

- Para cada llamada a `CoInitializeEx`, también debe llamar un subproceso [CoUninitialize](/windows/desktop/api/combaseapi/nf-combaseapi-couninitialize). En otras palabras, las llamadas a `CoInitializeEx` y `CoUninitialize` deben estar equilibradas.

- Para pasar de un apartamento de subproceso a otro, un subproceso debe liberar completamente la biblioteca COM antes de llamar a `CoInitializeEx` con la nueva especificación de subprocesamiento.

Cuando se usa COM con el runtime de simultaneidad, se aplican otros principios de COM. Por ejemplo, una aplicación que crea un objeto en un contenedor uniproceso (STA) y calcula las referencias de ese objeto en otro contenedor también debe proporcionar un bucle de mensajes para procesar los mensajes entrantes. Recuerde también que la serialización de objetos entre apartamentos puede reducir el rendimiento.

### <a name="using-com-with-the-parallel-patterns-library"></a>Usar COM con la Biblioteca de modelos paralelos

Cuando usa COM con un componente de la Biblioteca de modelos paralelos (PPL), por ejemplo, un algoritmo paralelo o un grupo de tareas llama a `CoInitializeEx` antes de usar la biblioteca COM durante cada tarea o iteración y llama a `CoUninitialize` antes de que finalice cada tarea o iteración. El ejemplo siguiente muestra cómo administrar la duración de la biblioteca COM con un [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objeto.

[!code-cpp[concrt-parallel-scripts#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_1.cpp)]

Debe asegurarse de que la biblioteca COM se libera correctamente cuando se cancela una tarea o algoritmo paralelo, o cuando el cuerpo de la tarea produce una excepción. Para garantizar que la tarea llama a `CoUninitialize` antes de salir, use un `try-finally` bloque o *Resource Acquisition Is Initialization* modelo (RAII). En el ejemplo siguiente se usa un bloque `try-finally` para liberar la biblioteca COM cuando la tarea se completa o se cancela, o cuando se produce una excepción.

[!code-cpp[concrt-parallel-scripts#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_2.cpp)]

En el ejemplo siguiente se usa un modelo RAII para definir la clase `CCoInitializer`, que administra la duración de la biblioteca COM en un ámbito determinado.

[!code-cpp[concrt-parallel-scripts#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_3.cpp)]

Puede usar la clase `CCoInitializer` para liberar la biblioteca COM automáticamente cuando la tarea finaliza, tal y como se muestra a continuación.

[!code-cpp[concrt-parallel-scripts#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_4.cpp)]

Para obtener más información sobre la cancelación del Runtime de simultaneidad, consulte [cancelación en PPL](cancellation-in-the-ppl.md).

### <a name="using-com-with-asynchronous-agents"></a>Usar COM con agentes asincrónicos

Cuando usa COM con agentes asincrónicos, llame a `CoInitializeEx` antes de usar la biblioteca COM en el [concurrency::agent::run](reference/agent-class.md#run) método para el agente. A continuación, llame a `CoUninitialize` antes de que el método `run` devuelva un resultado. No use las rutinas de administración COM en el constructor o destructor del agente y no se reemplazan los [Concurrency](reference/agent-class.md#start) o [Concurrency:: Agent:: realiza](reference/agent-class.md#done) métodos porque estos métodos son se llama desde un subproceso distinto del `run` método.

En el siguiente ejemplo se muestra una clase de agente básica, denominada `CCoAgent`, que administra la biblioteca COM en el método `run`.

[!code-cpp[concrt-parallel-scripts#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_5.cpp)]

Más adelante en este tutorial se proporciona un ejemplo completo.

### <a name="using-com-with-lightweight-tasks"></a>Usar COM con tareas ligeras

El documento [programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md) describe el rol de las tareas ligeras en el Runtime de simultaneidad. Puede usar COM con una tarea ligera del mismo modo que lo haría con cualquier rutina de subprocesamiento que pase a la función `CreateThread` de la API de Windows. Esta implementación se muestra en el ejemplo siguiente.

[!code-cpp[concrt-parallel-scripts#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_6.cpp)]

## <a name="an-example-of-a-com-enabled-application"></a>Ejemplo de una aplicación habilitada para COM

Esta sección muestra una aplicación completa habilitada para COM que usa el `IScriptControl` interfaz para ejecutar un script que calcula el<sup>th</sup> número de Fibonacci. En este ejemplo se llama primero al script desde el subproceso principal y, a continuación, se usa la biblioteca PPL y los agentes para llamar al script simultáneamente.

Considere la siguiente función del asistente, `RunScriptProcedure`, que llama a un procedimiento en un objeto `IScriptControl`.

[!code-cpp[concrt-parallel-scripts#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_7.cpp)]

El `wmain` función crea un `IScriptControl` de objetos, agrega el código de script que calcula la n<sup>th</sup> número de Fibonacci y, a continuación, llama a la `RunScriptProcedure` función para ejecutar ese script.

[!code-cpp[concrt-parallel-scripts#8](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_8.cpp)]

### <a name="calling-the-script-from-the-ppl"></a>Llamar al script desde la biblioteca PPL

La siguiente función, `ParallelFibonacci`, usa el [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmo para llamar a la secuencia de comandos en paralelo. Esta función usa la clase `CCoInitializer` para administrar la duración de la biblioteca COM durante cada iteración de la tarea.

[!code-cpp[concrt-parallel-scripts#9](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_9.cpp)]

Para usar la función `ParallelFibonacci` con el ejemplo, agregue el código siguiente antes de que la función `wmain` devuelva un resultado.

[!code-cpp[concrt-parallel-scripts#10](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_10.cpp)]

### <a name="calling-the-script-from-an-agent"></a>Llamar al script desde un agente

El ejemplo siguiente se muestra el `FibonacciScriptAgent` (clase), que llama a un procedimiento de script para calcular el<sup>th</sup> número de Fibonacci. La clase `FibonacciScriptAgent` usa el paso de mensajes para recibir del programa principal los valores de entrada para la función del script. El método `run` administra la duración de la biblioteca COM a lo largo de la tarea.

[!code-cpp[concrt-parallel-scripts#11](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_11.cpp)]

La siguiente función, `AgentFibonacci`, crea varios objetos `FibonacciScriptAgent` y usa el paso de mensajes para enviar varios valores de entrada a esos objetos.

[!code-cpp[concrt-parallel-scripts#12](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_12.cpp)]

Para usar la función `AgentFibonacci` con el ejemplo, agregue el código siguiente antes de que la función `wmain` devuelva un resultado.

[!code-cpp[concrt-parallel-scripts#13](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_13.cpp)]

### <a name="the-complete-example"></a>Ejemplo completo

En el código siguiente se muestra el ejemplo completo, en el que se usan algoritmos paralelos y agentes asincrónicos para llamar a un procedimiento de script que calcula los números de Fibonacci.

[!code-cpp[concrt-parallel-scripts#14](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_14.cpp)]

El ejemplo genera la siguiente salida de ejemplo:

```Output
Main Thread:
fib(15) = 610

Parallel Fibonacci:
fib(15) = 610
fib(10) = 55
fib(16) = 987
fib(18) = 2584
fib(11) = 89
fib(17) = 1597
fib(19) = 4181
fib(12) = 144
fib(13) = 233
fib(14) = 377

Agent Fibonacci:
fib(30) = 832040
fib(22) = 17711
fib(10) = 55
fib(12) = 144
```

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `parallel-scripts.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe/EHsc /link parallel-scripts.cpp ole32.lib**

## <a name="see-also"></a>Vea también

[Tutoriales del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)<br/>
[Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)<br/>
[Control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)<br/>
[Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)
