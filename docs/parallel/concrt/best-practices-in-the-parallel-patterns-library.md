---
title: "Procedimientos recomendados en la biblioteca de modelos paralelos | Microsoft Docs"
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
  - "Parallel Patterns Library, prácticas recomendadas para evitar"
  - "procedimientos recomendados para evitar Parallel Patterns Library"
  - "procedimientos recomendados, Parallel Patterns Library"
  - "Parallel Patterns Library, prácticas recomendadas"
ms.assetid: e43e0304-4d54-4bd8-a3b3-b8673559a9d7
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedimientos recomendados en la biblioteca de modelos paralelos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este documento se describe la mejor forma de usar eficazmente la biblioteca de patrones de procesamiento paralelos (PPL). PPL proporciona algoritmos, objetos y contenedores de propósito general para realizar paralelismos específicos.  
  
 Para obtener más información acerca de la biblioteca PPL, consulte [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md).  
  
##  <a name="a-nametopa-sections"></a><a name="top"></a> Secciones  
 Este documento contiene las siguientes secciones:  
  
- [No establecer paralelismos en cuerpos de bucle pequeños](#small-loops)  
  
- [Expresar el paralelismo en el nivel más alto posible](#highest)  
  
- [Usar parallel_invoke para resolver problemas de Divide y vencerás](#divide-and-conquer)  
  
- [Usar la cancelación o el control de excepciones para interrumpir desde un bucle paralelo](#breaking-loops)  
  
- [Comprender cómo afectan cancelación y control de excepciones a la destrucción de objetos](#object-destruction)  
  
- [No se bloquean varias veces en un bucle paralelo](#repeated-blocking)  
  
- [Realizar operaciones de bloqueo al cancelar el trabajo paralelo](#blocking)  
  
- [No escriba a los datos compartidos en un bucle paralelo](#shared-writes)  
  
- [Cuando sea posible, evite compartir False](#false-sharing)  
  
- [Asegúrese de que las Variables son válidas durante toda la duración de una tarea](#lifetime)  
  
##  <a name="a-namesmall-loopsa-do-not-parallelize-small-loop-bodies"></a><a name="small-loops"></a> No establecer paralelismos en cuerpos de bucle pequeños  
 La ejecución en paralelo de cuerpos de bucle relativamente pequeños puede hacer que la sobrecarga de programación asociada supere a las ventajas del procesamiento en paralelo. Considere el ejemplo siguiente, que agrega cada par de elementos en dos matrices.  
  
 [!code-cpp[concrt-small-loops#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_1.cpp)]  
  
 La carga de trabajo de cada iteración del bucle paralelo es demasiado pequeña para poder obtener beneficios de la sobrecarga de procesamiento en paralelo. Puede mejorar el rendimiento de este bucle realizando más trabajo en el cuerpo del bucle o realizando el bucle en serie.  
  
 [[Arriba](#top)]  
  
##  <a name="a-namehighesta-express-parallelism-at-the-highest-possible-level"></a><a name="highest"></a> Expresar el paralelismo en el nivel más alto posible  
 Cuando se paraleliza código solamente en el nivel inferior, se puede introducir una construcción del tipo bifurcar-combinar que no crece cuando aumenta el número de procesadores. Un *Bifurcar-recombinar* construcción es una construcción donde una tarea divide su trabajo en subtareas paralelas más pequeñas y espera a que esas subtareas Finalizar. Cada subtarea puede dividirse de forma recursiva en subtareas adicionales.  
  
 Aunque el modelo del tipo bifurcar-recombinar puede ser útil para resolver diversos problemas, hay situaciones en las que la sobrecarga de la sincronización puede disminuir la escalabilidad. Por ejemplo, considere el siguiente código en serie que procesa datos de imagen.  
  
 [!code-cpp[concrt-image-processing-filter#20](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_2.cpp)]  
  
 Dado que cada iteración del bucle es independiente, puede paralelizar buena parte del trabajo, como se muestra en el ejemplo siguiente. Este ejemplo se utiliza la [Concurrency:: parallel_for](../Topic/parallel_for%20Function.md) algoritmo para paralelizar el bucle exterior.  
  
 [!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_3.cpp)]  
  
 El ejemplo siguiente muestra una construcción del tipo bifurcar-recombinar llamando a la función `ProcessImage` en un bucle. Cada llamada a `ProcessImage` no se resuelve hasta que finaliza cada subtarea.  
  
 [!code-cpp[concrt-image-processing-filter#21](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_4.cpp)]  
  
 Si el trabajo que realiza cada iteración del bucle paralelo es casi inexistente o el trabajo que realiza el bucle paralelo no está equilibrado (es decir, algunas iteraciones del bucle tardan más que otras), la sobrecarga de programación que se necesita para bifurcar y recombinar el trabajo con tanta frecuencia puede sobrepasar el beneficio obtenido con la ejecución en paralelo. Esta sobrecarga aumenta cuando aumenta el número de procesadores.  
  
 Para reducir la cantidad de sobrecarga de programación en este ejemplo, puede paralelizar los bucles externos antes de paralelizar los bucles internos, o bien utilizar otra construcción paralela, como una canalización. En el ejemplo siguiente se modifica el `ProcessImages` función para que use la [Concurrency:: parallel_for_each](../Topic/parallel_for_each%20Function.md) algoritmo para paralelizar el bucle exterior.  
  
 [!code-cpp[concrt-image-processing-filter#22](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_5.cpp)]  
  
 Para obtener un ejemplo similar que usa una canalización para realizar el procesamiento de imágenes en paralelo, vea [Tutorial: creación de una red de procesamiento de imágenes](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).  
  
 [[Arriba](#top)]  
  
##  <a name="a-namedivide-and-conquera-use-parallelinvoke-to-solve-divide-and-conquer-problems"></a><a name="divide-and-conquer"></a> Usar parallel_invoke para resolver problemas de Divide y vencerás  
 Un *divide y vencerás* es un problema de la construcción del tipo bifurcar-recombinar que usa la recursividad para dividir una tarea en subtareas. Además el [Concurrency:: task_group](../Topic/task_group%20Class.md) y [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) clases, también puede utilizar el [Concurrency:: parallel_invoke](../Topic/parallel_invoke%20Function.md) algoritmo para resolver problemas de dividir y vencer. El algoritmo `parallel_invoke` tiene una sintaxis más concisa que los objetos de grupo de tareas y es útil cuando se tiene un número fijo de tareas paralelas.  
  
 En el ejemplo siguiente se muestra el uso del algoritmo `parallel_invoke` para implementar el algoritmo de ordenación bitónica.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#12](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_6.cpp)]  
  
 Para reducir la sobrecarga, el algoritmo `parallel_invoke` realiza la última serie de tareas en el contexto de la llamada.  
  
 Para obtener la versión completa de este ejemplo, vea [Cómo: usar Parallel.Invoke para escribir una rutina de ordenación en paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md). Para obtener más información acerca de la `parallel_invoke` algoritmo, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).  
  
 [[Arriba](#top)]  
  
##  <a name="a-namebreaking-loopsa-use-cancellation-or-exception-handling-to-break-from-a-parallel-loop"></a><a name="breaking-loops"></a> Usar la cancelación o el control de excepciones para interrumpir desde un bucle paralelo  
 PPL proporciona dos mecanismos para cancelar el trabajo paralelo que realiza un algoritmo paralelo o un grupo de tareas. Es una manera de usar el mecanismo de cancelación proporcionado por el [Concurrency:: task_group](../Topic/task_group%20Class.md) y [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) clases. El otro mecanismo consiste en producir una excepción en el cuerpo de la función de trabajo de una tarea. El mecanismo de cancelación es más eficaz que el control de excepciones para cancelar un árbol de trabajo paralelo. Un *árbol de trabajo paralelo* es un grupo de grupos de tareas relacionadas en la que algunos grupos de tareas contienen otros grupos de tareas. El mecanismo de cancelación cancela un grupo de tareas y sus grupos de tareas secundarios de forma descendente. Por el contrario, el control de excepciones funciona de manera ascendente y debe cancelar cada grupo de tareas secundario por separado a medida que la excepción se propaga hacia arriba.  
  
 Cuando se trabaja directamente con un objeto de grupo de tareas, utilice la [concurrency::task_group::cancel](../Topic/task_group::cancel%20Method.md) o [concurrency::structured_task_group::cancel](../Topic/structured_task_group::cancel%20Method.md) métodos para cancelar el trabajo que pertenece a ese grupo de tareas. Para cancelar un algoritmo paralelo, por ejemplo, `parallel_for`, cree un grupo de tareas primario y cancele ese grupo de tareas. Por ejemplo, considere la siguiente función, `parallel_find_any`, que busca un valor en una matriz en paralelo.  
  
 [!code-cpp[concrt-parallel-array-search#2](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_7.cpp)]  
  
 Dado que los algoritmos paralelos usan grupos de tareas, cuando una de las iteraciones paralelas cancela el grupo de tareas primario, se cancela la tarea global. Para obtener la versión completa de este ejemplo, vea [Cómo: uso de cancelación para interrumpir un bucle paralelo](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md).  
  
 Aunque el control de excepciones es una forma menos eficaz de cancelar el trabajo paralelo que el mecanismo de cancelación, hay casos en los que el control de excepciones es adecuado. Por ejemplo, el siguiente método, `for_all`, realiza de forma recursiva una función de trabajo en cada nodo de una estructura `tree`. En este ejemplo, el `_children` miembro de datos es un [std::list](../../standard-library/list-class.md) que contiene `tree` objetos.  
  
 [!code-cpp[concrt-task-tree-search#6](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_8.cpp)]  
  
 El llamador del método `tree::for_all` puede producir una excepción si no requiere que se llame a la función de trabajo en cada elemento del árbol. El ejemplo siguiente se muestra la función `search_for_value`, que busca un valor en el objeto `tree` proporcionado. La función `search_for_value` usa una función de trabajo que produce una excepción cuando el elemento actual del árbol coincide con el valor proporcionado. La función `search_for_value` usa un bloque `try-catch` para capturar la excepción e imprimir el resultado en la consola.  
  
 [!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_9.cpp)]  
  
 Para obtener la versión completa de este ejemplo, vea [Cómo: utilizar el control de excepciones para interrumpir un bucle paralelo](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).  
  
 Para obtener información general acerca de los mecanismos de control de excepciones que proporcionan la biblioteca PPL y cancelación, consulte [cancelación](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation_in_the_ppl) y [Exception Handling](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
 [[Arriba](#top)]  
  
##  <a name="a-nameobject-destructiona-understand-how-cancellation-and-exception-handling-affect-object-destruction"></a><a name="object-destruction"></a> Comprender cómo afectan cancelación y control de excepciones a la destrucción de objetos  
 En un árbol de trabajo paralelo, una tarea que se cancela impide que se ejecuten las tareas secundarias. Esto puede causar problemas si una de las tareas secundarias realiza una operación que tiene importancia para la aplicación, como liberar un recurso. Además, la cancelación de tareas puede hacer que una excepción se propague a través de un destructor de objeto y provoque un comportamiento no definido en la aplicación.  
  
 En el ejemplo siguiente, la clase `Resource` describe un recurso y la clase `Container` describe un contenedor que contiene los recursos. En su destructor, la clase `Container` llama al `cleanup` método en dos de sus miembros `Resource` en paralelo y, a continuación, llama al método `cleanup` en su tercer miembro `Resource`.  
  
 [!code-cpp[concrt-parallel-resource-destruction#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_10.h)]  
  
 Aunque este patrón no tiene ningún problema por sí mismo, considere el siguiente código, que ejecuta dos tareas en paralelo. La primera tarea crea un objeto `Container` y la segunda tarea cancela la tarea global. Con fines ilustrativos, el ejemplo utiliza dos [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) objetos para asegurarse de que la cancelación se produce después de la `Container` se crea el objeto y que la `Container` objeto se destruye después de que se produzca la operación de cancelación.  
  
 [!code-cpp[concrt-parallel-resource-destruction#2](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_11.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
```Output  
Container 1: Freeing resources...Exiting program...  
```  
  
 Este ejemplo de código presenta los siguientes problemas que pueden hacer que no se comporte de la forma esperada:  
  
-   La cancelación de la tarea principal hace que la tarea secundaria, la llamada a [Concurrency:: parallel_invoke](../Topic/parallel_invoke%20Function.md), que también se puede cancelar. Por lo tanto, estos dos recursos no se liberan.  
  
-   La cancelación de la tarea principal hace que la tarea secundaria produzca una excepción interna. Dado que el destructor `Container` no controla esta excepción, la excepción se propaga hacia arriba y no se libera el tercer recurso.  
  
-   La excepción producida por la tarea secundaria se propaga a través del destructor `Container`. Al propagarse desde un destructor, pone a la aplicación en un estado indefinido.  
  
 Se recomienda que no se realicen operaciones críticas, como liberar recursos, en las tareas, a menos que pueda garantizar que esas tareas no se cancelarán. También se recomienda no utilizar funcionalidad de tiempo de ejecución que pueda introducir el destructor de los tipos.  
  
 [[Arriba](#top)]  
  
##  <a name="a-namerepeated-blockinga-do-not-block-repeatedly-in-a-parallel-loop"></a><a name="repeated-blocking"></a> No se bloquean varias veces en un bucle paralelo  
 Un bucle paralelo como [Concurrency:: parallel_for](../Topic/parallel_for%20Function.md) o [Concurrency:: parallel_for_each](../Topic/parallel_for_each%20Function.md) que está dominado por bloqueo de operaciones pueden hacer que el runtime cree muchos subprocesos en un tiempo breve.  
  
 El Runtime de simultaneidad realiza un trabajo adicional cuando una tarea finaliza, o cuando bloquea o produce un resultado de forma cooperativa. Cuando una iteración de un bucle paralelo se bloquea, el runtime podría iniciar otra iteración. Si no hay ningún subproceso inactivo disponible, el runtime crea un subproceso nuevo.  
  
 Cuando el cuerpo de un bucle paralelo se bloquea puntualmente, este mecanismo ayuda a maximizar el rendimiento de la tarea global. Sin embargo, cuando se bloquean muchas iteraciones, el runtime puede crear muchos subprocesos para ejecutar el trabajo adicional. Esto podría provocar un estado de memoria insuficiente o una mala utilización de los recursos de hardware.  
  
 Considere el ejemplo siguiente que llama el [Concurrency:: Send](../Topic/send%20Function.md) función en cada iteración de un `parallel_for` bucle. Dado que `send` bloquea de forma cooperativa, el runtime crea un nuevo subproceso para ejecutar el trabajo adicional cada vez que se llama a `send`.  
  
 [!code-cpp[concrt-repeated-blocking#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_12.cpp)]  
  
 Se recomienda refactorizar el código para evitar este patrón. En este ejemplo, puede evitar la creación de subprocesos adicionales mediante una llamada a `send` en un bucle `for` en serie.  
  
 [[Arriba](#top)]  
  
##  <a name="a-nameblockinga-do-not-perform-blocking-operations-when-you-cancel-parallel-work"></a><a name="blocking"></a> Realizar operaciones de bloqueo al cancelar el trabajo paralelo  
 Cuando sea posible, no realice operaciones de bloqueo antes de llamar a la [concurrency::task_group::cancel](../Topic/task_group::cancel%20Method.md) o [concurrency::structured_task_group::cancel](../Topic/structured_task_group::cancel%20Method.md) método para cancelar el trabajo paralelo.  
  
 Cuando una tarea realiza una operación de bloqueo cooperativa, el runtime puede realizar otro trabajo mientras la primera tarea espera los datos. El runtime reprograma la tarea en espera cuando se desbloquea. Normalmente, el runtime reprograma las tareas que se han desbloqueado más recientemente antes de reprogramar las tareas que se han desbloqueado menos recientemente. El runtime, por tanto, podría programar trabajo innecesario durante la operación de bloqueo, lo que provocaría una disminución del rendimiento. En consecuencia, si se realiza una operación de bloqueo antes de cancelar el trabajo paralelo, la operación de bloqueo puede retrasar la llamada a `cancel`. Esto hace que otras tareas realicen trabajo innecesario.  
  
 Considere el siguiente ejemplo en el que se define la función `parallel_find_answer`, que busca un elemento de la matriz proporcionada que cumpla la función de predicado proporcionada. Cuando la función de predicado devuelve `true`, la función de trabajo paralela crea un objeto `Answer` y cancela la tarea general.  
  
 [!code-cpp[concrt-blocking-cancel#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_13.cpp)]  
  
 El operador `new` realiza una asignación en el montón, lo que podría producir un bloqueo. El tiempo de ejecución realiza otro trabajo solo cuando la tarea realiza una cooperativa de bloqueo de llamada, como una llamada a [concurrency::critical_section::lock](../Topic/critical_section::lock%20Method.md).  
  
 En el ejemplo siguiente se muestra cómo evitar el trabajo innecesario y mejorar así el rendimiento. Este ejemplo cancela el grupo de tareas antes de asignar el almacenamiento para el objeto `Answer`.  
  
 [!code-cpp[concrt-blocking-cancel#2](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_14.cpp)]  
  
 [[Arriba](#top)]  
  
##  <a name="a-nameshared-writesa-do-not-write-to-shared-data-in-a-parallel-loop"></a><a name="shared-writes"></a> No escriba a los datos compartidos en un bucle paralelo  
 El Runtime de simultaneidad proporciona varias estructuras de datos, por ejemplo, [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md), sincronizar el acceso simultáneo a los datos compartidos. Estas estructuras de datos son útiles en muchos casos; por ejemplo, cuando varias tareas requieren con poca frecuencia acceso compartido a un recurso.  
  
 Considere el siguiente ejemplo que utiliza el [Concurrency:: parallel_for_each](../Topic/parallel_for_each%20Function.md) algoritmo y un `critical_section` objeto que se va a calcular el recuento de números primos en un [std:: Array](../../standard-library/array-class-stl.md) objeto. Este ejemplo no se escala porque cada subproceso debe esperar para obtener acceso a la variable compartida `prime_sum`.  
  
 [!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_15.cpp)]  
  
 Este ejemplo también puede provocar un rendimiento bajo porque la operación de bloqueo frecuente serializa eficazmente el bucle. Además, cuando un objeto del Runtime de simultaneidad realiza una operación de bloqueo, el programador puede crear un subproceso adicional que realice otro trabajo mientras el primer subproceso espera los datos. Si el runtime crea muchos subprocesos porque hay muchas tareas esperando los datos compartidos, la aplicación puede tener un rendimiento bajo o entrar en un estado de escasez de recursos.  
  
 PPL define la [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) (clase), lo que ayuda a eliminar el estado compartido al proporcionar acceso a los recursos compartidos de forma libre de bloqueo. La clase `combinable` proporciona un almacenamiento local para los subprocesos que permite realizar cálculos específicos y, a continuación, combinar estos cálculos en un resultado final. Puede pensar en un objeto `combinable` como una variable de reducción.  
  
 El ejemplo siguiente modifica el ejemplo anterior mediante el uso de un objeto `combinable` en lugar de un objeto `critical_section` para calcular la suma. Este ejemplo sí se escala, porque cada subproceso tiene su propia copia local de la suma. Este ejemplo se utiliza la [concurrency::combinable::combine](../Topic/combinable::combine%20Method.md) método para combinar los cálculos locales en el resultado final.  
  
 [!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_16.cpp)]  
  
 Para obtener la versión completa de este ejemplo, vea [Cómo: usar la clase combinable para mejorar el rendimiento](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md). Para obtener más información acerca de la `combinable` de clases, consulte [objetos y contenedores paralelos](../../parallel/concrt/parallel-containers-and-objects.md).  
  
 [[Arriba](#top)]  
  
##  <a name="a-namefalse-sharinga-when-possible-avoid-false-sharing"></a><a name="false-sharing"></a> Cuando sea posible, evite compartir False  
 *Compartir false* se produce cuando varias tareas simultáneas que se ejecutan en procesadores separados escritura a las variables que se encuentran en la misma línea de caché. Cuando una tarea escribe en una de las variables, se invalida la línea de caché de las dos variables. Cada procesador debe volver a cargar la línea de caché cada vez que esta se invalida. Por lo tanto, el uso compartido falso puede causar una disminución del rendimiento de la aplicación.  
  
 El siguiente ejemplo básico se muestra dos tareas simultáneas, cada una de las cuales incrementa una variable de contador compartida.  
  
 [!code-cpp[concrt-false-sharing#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_17.cpp)]  
  
 Para eliminar el uso compartido de datos entre las dos tareas, se puede modificar el ejemplo de forma que use dos variables de contador. Este ejemplo calcula el valor final del contador después de finalizar las tareas. Sin embargo, este es un ejemplo de uso compartido falso, porque es muy probable que las variables `count1` y `count2` se encuentren en la misma línea de caché.  
  
 [!code-cpp[concrt-false-sharing#2](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_18.cpp)]  
  
 Una manera de eliminar el uso compartido falso consiste en asegurarse de que las variables de contador estén en líneas de caché distintas. El ejemplo siguiente alinea las variables `count1` y `count2` en límites de 64 bytes.  
  
 [!code-cpp[concrt-false-sharing#3](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_19.cpp)]  
  
 En este ejemplo se supone que el tamaño de la memoria caché es de 64 bytes o inferior.  
  
 Se recomienda que utilice la [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) clase deben compartir datos entre tareas. La clase `combinable` crea variables locales para los subprocesos de tal manera que es menos probable que se dé un uso compartido falso. Para obtener más información acerca de la `combinable` de clases, consulte [objetos y contenedores paralelos](../../parallel/concrt/parallel-containers-and-objects.md).  
  
 [[Arriba](#top)]  
  
##  <a name="a-namelifetimea-make-sure-that-variables-are-valid-throughout-the-lifetime-of-a-task"></a><a name="lifetime"></a> Asegúrese de que las Variables son válidas durante toda la duración de una tarea  
 Al proporcionar una expresión lambda a un grupo de tareas o algoritmo paralelo, la cláusula de captura especifica si el cuerpo de la expresión lambda tiene acceso a las variables del ámbito de inclusión por valor o por referencia. Si pasa variables por referencia a una expresión lambda, debe garantizar que esas variables se conserven hasta que finalice la tarea.  
  
 Considere el ejemplo siguiente que define la clase `object` y la función `perform_action`. La función `perform_action` crea una variable `object` y realiza alguna acción en esa variable de forma asincrónica. Dado que no se garantiza que la tarea finalice antes de que la función `perform_action` se resuelva, el programa se bloqueará o mostrará un comportamiento no especificado si la variable `object` se destruye mientras se ejecuta la tarea.  
  
 [!code-cpp[concrt-lambda-lifetime#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_20.cpp)]  
  
 Según los requisitos de la aplicación, puede utilizar una de las siguientes técnicas para asegurarse de que las variables sigan siendo válidas mientras dure cualquiera de las tareas.  
  
 En el ejemplo siguiente se pasa la variable `object` por valor a la tarea. Por lo tanto, la tarea opera sobre su propia copia de la variable.  
  
 [!code-cpp[concrt-lambda-lifetime#2](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_21.cpp)]  
  
 Dado que la variable `object` se pasa por valor, cualquier cambio de estado que se produzca en esta variable no aparecerá en la copia original.  
  
 En el ejemplo siguiente se utiliza la [concurrency::task_group::wait](../Topic/task_group::wait%20Method.md) método para asegurarse de que la tarea finalice antes de la `perform_action` función devuelve.  
  
 [!code-cpp[concrt-lambda-lifetime#3](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_22.cpp)]  
  
 Dado que ahora finaliza la tarea antes de que se resuelva la función, la función `perform_action` ya no se comporta de forma asincrónica.  
  
 En el ejemplo siguiente se modifica la función `perform_action` para que tome una referencia a la variable `object`. El llamador debe garantizar que la duración de la variable `object` sea válida hasta que finalice la tarea.  
  
 [!code-cpp[concrt-lambda-lifetime#4](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_23.cpp)]  
  
 También puede utilizar un puntero para controlar la duración del objeto que va a pasar a un algoritmo paralelo o un grupo de tareas.  
  
 Para obtener más información sobre las expresiones lambda, vea [expresiones Lambda](../../cpp/lambda-expressions-in-cpp.md).  
  
 [[Arriba](#top)]  
  
## <a name="see-also"></a>Vea también  
 [Procedimientos recomendados del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [Biblioteca de modelos paralelos (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)   
 [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)   
 [Cancelación](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation_in_the_ppl)   
 [Control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [Tutorial: Crear una red de procesamiento de imágenes](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)   
 [Cómo: usar Parallel.Invoke para escribir una rutina de ordenación en paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)   
 [Cómo: usar la cancelación para interrumpir un bucle paralelo](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)   
 [Cómo: usar la clase combinable para mejorar el rendimiento](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)   
 [Procedimientos recomendados en la biblioteca de agentes asincrónicos](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)   
 [Recomendaciones generales en el Runtime de simultaneidad](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)

