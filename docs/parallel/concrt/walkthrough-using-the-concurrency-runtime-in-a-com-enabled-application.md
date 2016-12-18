---
title: "Tutorial: Usar el Runtime de simultaneidad en una aplicaci&#243;n habilitada para COM | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Runtime de simultaneidad, usar con COM"
  - "COM, usar con el Runtime de simultaneidad"
ms.assetid: a7c798b8-0fc8-4bee-972f-22ef158f7f48
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Usar el Runtime de simultaneidad en una aplicaci&#243;n habilitada para COM
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este documento se muestra cómo se usa el Runtime de simultaneidad en una aplicación que emplea el Modelo de objetos componentes \(COM\).  
  
## Requisitos previos  
 Lea los documentos siguientes antes de iniciar este tutorial:  
  
-   [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
-   [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)  
  
-   [Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)  
  
-   [Control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)  
  
 Para obtener más información sobre COM, vea [Component Object Model \(COM\)](http://msdn.microsoft.com/library/windows/desktop/ms680573).  
  
## Administrar la duración de la biblioteca COM  
 Aunque el uso de COM con el Runtime de simultaneidad sigue los mismos principios que cualquier otro mecanismo de simultaneidad, las siguientes instrucciones pueden ayudarle a usar conjuntamente estas bibliotecas de forma eficaz.  
  
-   Un subproceso debe llamar a [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) antes de usar la biblioteca COM.  
  
-   Un subproceso puede llamar varias veces a `CoInitializeEx` siempre que proporcione los mismos argumentos en cada llamada.  
  
-   En cada llamada a `CoInitializeEx`, debe haber un subproceso que llame también a [CoUninitialize](http://msdn.microsoft.com/library/windows/desktop/ms688715).  En otras palabras, las llamadas a `CoInitializeEx` y `CoUninitialize` deben estar equilibradas.  
  
-   Para pasar de un apartamento de subproceso a otro, un subproceso debe liberar completamente la biblioteca COM antes de llamar a `CoInitializeEx` con la nueva especificación de subprocesamiento.  
  
 Cuando se usa COM con el runtime de simultaneidad, se aplican otros principios de COM.  Por ejemplo, una aplicación que crea un objeto en un contenedor uniproceso \(STA\) y calcula las referencias de ese objeto en otro contenedor también debe proporcionar un bucle de mensajes para procesar los mensajes entrantes.  Recuerde también que el cálculo de referencias de objetos entre apartamentos puede reducir el rendimiento.  
  
### Usar COM con la Biblioteca de modelos paralelos  
 Cuando usa COM con un componente de la Biblioteca de modelos paralelos \(PPL\), por ejemplo, un algoritmo paralelo o un grupo de tareas llama a `CoInitializeEx` antes de usar la biblioteca COM durante cada tarea o iteración y llama a `CoUninitialize` antes de que finalice cada tarea o iteración.  En el ejemplo siguiente se muestra cómo administrar la duración de la biblioteca COM con un objeto [concurrency::structured\_task\_group](../../parallel/concrt/reference/structured-task-group-class.md).  
  
 [!code-cpp[concrt-parallel-scripts#1](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_1.cpp)]  
  
 Debe asegurarse de que la biblioteca COM se libera correctamente cuando se cancela una tarea o algoritmo paralelo, o cuando el cuerpo de la tarea produce una excepción.  Para garantizar que la tarea llama a `CoUninitialize` antes de salir, use un bloque `try-finally` o el modelo *Resource Acquisition Is Initialization* \(RAII\).  En el ejemplo siguiente se usa un bloque `try-finally` para liberar la biblioteca COM cuando la tarea se completa o se cancela, o cuando se produce una excepción.  
  
 [!code-cpp[concrt-parallel-scripts#2](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_2.cpp)]  
  
 En el ejemplo siguiente se usa un modelo RAII para definir la clase `CCoInitializer`, que administra la duración de la biblioteca COM en un ámbito determinado.  
  
 [!code-cpp[concrt-parallel-scripts#3](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_3.cpp)]  
  
 Puede usar la clase `CCoInitializer` para liberar la biblioteca COM automáticamente cuando la tarea finaliza, tal y como se muestra a continuación.  
  
 [!code-cpp[concrt-parallel-scripts#4](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_4.cpp)]  
  
 Para obtener más información sobre la cancelación del Runtime de simultaneidad, vea [Cancelación](../../parallel/concrt/cancellation-in-the-ppl.md).  
  
### Usar COM con agentes asincrónicos  
 Cuando use COM con agentes asincrónicos, llame a `CoInitializeEx` antes de usar la biblioteca COM en el método [concurrency::agent::run](../Topic/agent::run%20Method.md) para el agente.  A continuación, llame a `CoUninitialize` antes de que el método `run` devuelva un resultado.  No use las rutinas de administración COM en el constructor o destructor del agente y no reemplace los métodos [concurrency::agent::start](../Topic/agent::start%20Method.md) ni [concurrency::agent::done](../Topic/agent::done%20Method.md), ya que estos métodos se invocan desde un subproceso distinto al del método `run`.  
  
 En el siguiente ejemplo se muestra una clase de agente básica, denominada `CCoAgent`, que administra la biblioteca COM en el método `run`.  
  
 [!code-cpp[concrt-parallel-scripts#5](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_5.cpp)]  
  
 Más adelante en este tutorial se proporciona un ejemplo completo.  
  
### Usar COM con tareas ligeras  
 En el documento [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md) se describe el rol de las tareas ligeras en el Runtime de simultaneidad.  Puede usar COM con una tarea ligera del mismo modo que lo haría con cualquier rutina de subprocesamiento que pase a la función `CreateThread` de la API de Windows.  Esta implementación se muestra en el ejemplo siguiente.  
  
 [!code-cpp[concrt-parallel-scripts#6](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_6.cpp)]  
  
## Ejemplo de una aplicación habilitada para COM  
 En esta sección se muestra una aplicación completa habilitada para COM que usa la interfaz `IScriptControl` para ejecutar un script que calcula el enésimo número de Fibonacci.  En este ejemplo se llama primero al script desde el subproceso principal y, a continuación, se usa la biblioteca PPL y los agentes para llamar al script simultáneamente.  
  
 Considere la siguiente función auxiliar, `RunScriptProcedure`, que llama a un procedimiento en un objeto `IScriptControl`.  
  
 [!code-cpp[concrt-parallel-scripts#7](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_7.cpp)]  
  
 La función `wmain` crea un objeto `IScriptControl`, le agrega el código del script que calcula el enésimo número de Fibonacci y, a continuación, llama a la función `RunScriptProcedure` para ejecutar ese script.  
  
 [!code-cpp[concrt-parallel-scripts#8](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_8.cpp)]  
  
### Llamar al script desde la biblioteca PPL  
 La siguiente función, `ParallelFibonacci`, usa el algoritmo [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) para llamar al script en paralelo.  Esta función usa la clase `CCoInitializer` para administrar la duración de la biblioteca COM durante cada iteración de la tarea.  
  
 [!code-cpp[concrt-parallel-scripts#9](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_9.cpp)]  
  
 Para usar la función `ParallelFibonacci` con el ejemplo, agregue el código siguiente antes de que la función `wmain` devuelva un resultado.  
  
 [!code-cpp[concrt-parallel-scripts#10](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_10.cpp)]  
  
### Llamar al script desde un agente  
 En el ejemplo siguiente se muestra la clase `FibonacciScriptAgent`, que llama a un procedimiento de script para calcular el enésimo número de Fibonacci.  La clase `FibonacciScriptAgent` usa el paso de mensajes para recibir del programa principal los valores de entrada para la función del script.  El método `run` administra la duración de la biblioteca COM a lo largo de la tarea.  
  
 [!code-cpp[concrt-parallel-scripts#11](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_11.cpp)]  
  
 La siguiente función, `AgentFibonacci`, crea varios objetos `FibonacciScriptAgent` y usa el paso de mensajes para enviar varios valores de entrada a esos objetos.  
  
 [!code-cpp[concrt-parallel-scripts#12](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_12.cpp)]  
  
 Para usar la función `AgentFibonacci` con el ejemplo, agregue el código siguiente antes de que la función `wmain` devuelva un resultado.  
  
 [!code-cpp[concrt-parallel-scripts#13](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_13.cpp)]  
  
### Ejemplo completo  
 En el código siguiente se muestra el ejemplo completo, en el que se usan algoritmos paralelos y agentes asincrónicos para llamar a un procedimiento de script que calcula los números de Fibonacci.  
  
 [!code-cpp[concrt-parallel-scripts#14](../../parallel/concrt/codesnippet/CPP/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_14.cpp)]  
  
 El ejemplo genera la siguiente salida de ejemplo:  
  
  **Main Thread:**  
**fib\(15\) \= 610**  
**Parallel Fibonacci:**  
**fib\(15\) \= 610**  
**fib\(10\) \= 55**  
**fib\(16\) \= 987**  
**fib\(18\) \= 2584**  
**fib\(11\) \= 89**  
**fib\(17\) \= 1597**  
**fib\(19\) \= 4181**  
**fib\(12\) \= 144**  
**fib\(13\) \= 233**  
**fib\(14\) \= 377**  
**Agent Fibonacci:**  
**fib\(30\) \= 832040**  
**fib\(22\) \= 17711**  
**fib\(10\) \= 55**  
**fib\(12\) \= 144**   
## Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o en un archivo denominado `parallel-scripts.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc parallel\-scripts.cpp \/link ole32.lib**  
  
## Vea también  
 [Tutoriales del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)   
 [Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)   
 [Control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [Cancelación](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)