---
title: Cancelación en la biblioteca PPL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parallel algorithms, canceling [Concurrency Runtime]
- canceling parallel algorithms [Concurrency Runtime]
- parallel tasks, canceling [Concurrency Runtime]
- cancellation in the PPL
- parallel work trees [Concurrency Runtime]
- canceling parallel tasks [Concurrency Runtime]
ms.assetid: baaef417-b2f9-470e-b8bd-9ed890725b35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a0c74ad5877a5b490414d96bf0f13b32309a21a
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694841"
---
# <a name="cancellation-in-the-ppl"></a>Cancelación en la biblioteca PPL
En este documento se explica el rol de cancelación de la biblioteca de patrones de procesamiento paralelo (PPL), cómo se cancela el trabajo paralelo y cómo se determina cuándo se cancela un trabajo paralelo.  
  
> [!NOTE]
>  El runtime usa el control de excepciones para implementar la cancelación. No debe detectar ni administrar estas excepciones en su código. Además, le recomendamos que escriba código seguro ante excepciones en los cuerpos de las funciones de las tareas. Por ejemplo, puede usar el *Resource Acquisition Is Initialization* patrón (RAII) para asegurarse de que los recursos se administran correctamente cuando se produce una excepción en el cuerpo de una tarea. Para obtener un ejemplo completo que usa el modelo RAII para limpiar un recurso en una tarea cancelable, vea [Tutorial: Quitar trabajo de un subproceso de interfaz de usuario](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md).  
  
## <a name="key-points"></a>Puntos clave  
  
-   La cancelación es cooperativa e implica la coordinación entre el código que solicita la cancelación y la tarea que responde a la cancelación.  
  
-   Siempre que sea posible, use tokens de cancelación para cancelar el trabajo. El [cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) clase define un token de cancelación.  
  

-   Cuando se usa tokens de cancelación, utilice la [concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) método para iniciar la cancelación y el [Concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) función para responder a cancelación. Use la [concurrency::cancellation_token::is_canceled](reference/cancellation-token-class.md#is_canceled) método para comprobar si cualquier otra tarea ha solicitado la cancelación.
  
-   La cancelación no se produce de forma inmediata. Aunque el nuevo trabajo no se inicia si se cancela una tarea o un grupo de tareas, el trabajo activo debe buscar y responder a la cancelación.  
  
-   Una continuación basada en valores hereda el token de cancelación de la tarea anterior. Una continuación basada en tareas nunca hereda el token de la tarea anterior.  
  
-   Use la [cancellation_token:: none](reference/cancellation-token-class.md#none) método cuando se llama a un constructor o una función que toma un `cancellation_token` objeto pero no desea que la operación se pueda cancelar. Además, si no se pasa un token de cancelación para la [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) constructor o la [Concurrency:: create_task](reference/concurrency-namespace-functions.md#create_task) función, esa tarea no es cancelable.  


  
##  <a name="top"></a> En este documento  
  
- [Árboles de trabajo paralelo](#trees)  
  
- [Cancelar tareas paralelas](#tasks)  
  
    - [Usar un Token de cancelación para cancelar el trabajo paralelo](#tokens)  
  
    - [Usar el método cancel para cancelar el trabajo paralelo](#cancel)  
  
    - [Usar excepciones para cancelar el trabajo paralelo](#exceptions)  
  
- [Cancelar algoritmos paralelos](#algorithms)  
  
- [Cuando no se usa la cancelación](#when)  
  
##  <a name="trees"></a> Árboles de trabajo paralelo  
 PPL usa tareas y grupos de tareas para administrar tareas y cálculos específicos. Puede anidar grupos de tareas al formulario *árboles* de trabajo paralelo. En la ilustración siguiente se muestra un árbol de trabajo paralelo. En esta ilustración, `tg1` y `tg2` representan grupos de tareas; `t1`, `t2`, `t3`, `t4` y `t5` representan el trabajo que realizan los grupos de tareas.  
  
 ![Un árbol de trabajo paralelo](../../parallel/concrt/media/parallelwork_trees.png "parallelwork_trees")  
  
 En el ejemplo siguiente se muestra el código necesario para crear el árbol de la ilustración. En este ejemplo, `tg1` y `tg2` son [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objetos; `t1`, `t2`, `t3`, `t4`, y `t5` son [Concurrency:: task_handle](../../parallel/concrt/reference/task-handle-class.md) objetos.  
  
 [!code-cpp[concrt-task-tree#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_1.cpp)]  
  
 También puede usar el [Concurrency:: task_group](reference/task-group-class.md) clase para crear un árbol de trabajo similar. El [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) clase también admite la noción de un árbol de trabajo. Sin embargo, un árbol `task` es un árbol de dependencia. En un árbol `task`, los trabajos futuros se completan después del trabajo actual. En un árbol de grupo de tareas, el trabajo interno se completa antes que el trabajo externo. Para obtener más información acerca de las diferencias entre las tareas y grupos de tareas, consulte [paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 [[Arriba](#top)]  
  
##  <a name="tasks"></a> Cancelar tareas paralelas  

 Existen varias maneras de cancelar el trabajo paralelo. La forma preferida es utilizar un token de cancelación. Grupos de tareas también admiten la [concurrency::task_group::cancel](reference/task-group-class.md#cancel) método y [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) método. La otra manera consiste en iniciar una excepción en el cuerpo de una función de trabajo de una tarea. Independientemente del método que elija, debe saber que la cancelación no se produce de inmediato. Aunque el nuevo trabajo no se inicia si se cancela una tarea o un grupo de tareas, el trabajo activo debe buscar y responder a la cancelación.  

  
 Para obtener más ejemplos que cancelan tareas paralelas, vea [Tutorial: conectar usando tareas y solicitudes HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md), [Cómo: usar la cancelación para interrumpir un bucle paralelo](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md), y [Cómo: usar Control de excepciones para interrumpir desde un bucle paralelo](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).  
  
###  <a name="tokens"></a> Usar un Token de cancelación para cancelar el trabajo paralelo  
 Las clases `task`, `task_group` y `structured_task_group` admiten la cancelación mediante tokens de cancelación. La biblioteca PPL define la [Concurrency:: cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md) y [cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) clases para este propósito. Cuando usa un token de cancelación para cancelar el trabajo, el runtime no inicia el nuevo trabajo suscrito a dicho token. Puede usar el trabajo que ya está activo el [is_canceled](../../parallel/concrt/reference/cancellation-token-class.md#is_canceled) función de miembro para supervisar el token de cancelación y detenerse cuando puede.  
  

 Para iniciar la cancelación, llame a la [concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) método. A la cancelación se responde de las siguientes maneras:  
  
-   Para `task` objetos, use la [Concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) función. `cancel_current_task` cancela la tarea actual y cualquiera de sus continuaciones basadas en valores. (No cancela la cancelación *token* que está asociado a la tarea o sus continuaciones.)  
  
-   Grupos de tareas y algoritmos paralelos, utilice la [Concurrency:: is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) función para detectar la cancelación y regresar tan pronto como sea posible desde el cuerpo de la tarea cuando esta función devuelve `true`. (No llame a `cancel_current_task` desde un grupo de tareas).  

  
 En el ejemplo siguiente se muestra el primer patrón básico para la cancelación de la tarea. En algunas ocasiones, el cuerpo de la tarea comprueba la cancelación dentro de un bucle.  
  
 [!code-cpp[concrt-task-basic-cancellation#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_2.cpp)]  
  
 La función `cancel_current_task` se inicia; por consiguiente, no necesita regresar de manera explícita de la función o bucle actual.  
  
> [!TIP]

>  Como alternativa, puede llamar a la [Concurrency:: interruption_point](reference/concurrency-namespace-functions.md#interruption_point) función en lugar de `cancel_current_task`.  
  
 Es importante llamar a `cancel_current_task` cuando responda a la cancelación porque pasa la tarea al estado cancelado. Si regresa prematuramente de la función en lugar de llamar a `cancel_current_task`, la operación pasa al estado completado y se ejecuta cualquier continuación basada en valores.  
  
> [!CAUTION]
>  Nunca inicie `task_canceled` desde su código. En su lugar, llame a `cancel_current_task`.  
  
 Cuando finaliza una tarea en el estado cancelado, el [concurrency::task::get](reference/task-class.md#get) método inicie una excepción [Concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md). (Por el contrario, [concurrency::task::wait](reference/task-class.md#wait) devuelve [task_status:: Canceled](reference/concurrency-namespace-enums.md#task_group_status) y no produce una excepción.) En el ejemplo siguiente se muestra este comportamiento para una continuación basada en tareas. Siempre se llama a una continuación basada en tareas, incluso cuando se cancela la tarea anterior.  

  
 [!code-cpp[concrt-task-canceled#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_3.cpp)]  
  
 Dado que las continuaciones basadas en valores heredan el token de su tarea anterior a menos que se crearan con un token explícito, las continuaciones entran inmediatamente en estado cancelado incluso si la tarea anterior todavía se está ejecutando. Por tanto, cualquier excepción que produzca la tarea anterior tras la cancelación no se propaga a las tareas de continuación. La cancelación siempre invalida el estado de la tarea anterior. El ejemplo siguiente es similar al anterior, pero muestra el comportamiento de una continuación basada en valores.  
  
 [!code-cpp[concrt-task-canceled#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_4.cpp)]  
  
> [!CAUTION]

>  Si no pasa un token de cancelación para la `task` constructor o la [Concurrency:: create_task](reference/concurrency-namespace-functions.md#create_task) función, esa tarea no es cancelable. Además, debe pasar el mismo token de cancelación al constructor de cualquier tarea anidada (es decir, las tareas que se crean en el cuerpo de otra tarea) para cancelar todas las tareas a la vez.  
  
 Puede que desee ejecutar código arbitrario cuando se cancele un token de cancelación. Por ejemplo, si el usuario elige un **cancelar** botón en la interfaz de usuario para cancelar la operación, se podía deshabilitar dicho botón hasta que el usuario inicie otra operación. En el ejemplo siguiente se muestra cómo utilizar el [concurrency::cancellation_token::register_callback](reference/cancellation-token-class.md#register_callback) método para registrar una función de devolución de llamada que se ejecuta cuando se cancela un token de cancelación.  

  
 [!code-cpp[concrt-task-cancellation-callback#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_5.cpp)]  
  
 El documento [paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md) explica la diferencia entre las continuaciones basadas en valores y basada en tareas. Si no proporciona un objeto `cancellation_token` a una tarea de continuación, la continuación hereda el token de cancelación de la tarea anterior de las siguientes maneras:  
  
-   Una continuación basada en valores siempre hereda el token de cancelación de la tarea anterior.  
  
-   Una continuación basada en tareas nunca hereda el token de cancelación de la tarea anterior. La única manera de hacer que una continuación basada en tareas sea cancelable es pasar de manera explícita un token de cancelación.  
  
 Estos comportamientos no se ven afectados por una tarea con errores (es decir, una que produce una excepción). En este caso, se cancela una continuación basada en valores; no se cancela una continuación basada en tareas.  
  
> [!CAUTION]
>  Una tarea que se crea en otra tarea (es decir, una tarea anidada) no hereda el token de cancelación de la tarea principal. Solo una continuación basada en valores hereda el token de cancelación de la tarea anterior.  
  
> [!TIP]

>  Use la [cancellation_token:: none](reference/cancellation-token-class.md#none) método cuando se llama a un constructor o una función que toma un `cancellation_token` objeto y no desea que la operación se pueda cancelar.  
  
 También puede proporcionar un token de cancelación al constructor de un objeto `task_group` o `structured_task_group`. Un aspecto importante que debe tener en cuenta es que los grupos de tareas secundarios heredan este token de cancelación. Para obtener un ejemplo que muestra este concepto mediante el uso de la [Concurrency:: run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) función que se ejecuta para llamar a `parallel_for`, consulte [Cancelar algoritmos paralelos](#algorithms) más adelante en este documento.  
  
 [[Arriba](#top)]  
  
#### <a name="cancellation-tokens-and-task-composition"></a>Tokens de cancelación y composición de tareas  

 El [simultaneidad:: HYPERLINK "http://msdn.microsoft.com/library/system.threading.tasks.task.whenall(v=VS.110).aspx" when_all](reference/concurrency-namespace-functions.md#when_all) y [when_any](reference/concurrency-namespace-functions.md#when_all) las funciones que pueden ayudarle a crear varias tareas para implementar patrones comunes. En esta sección se describe cómo operan estas funciones con tokens de cancelación.  
  
 Cuando se proporciona un token de cancelación a la función `when_all` o `when_any`, dicha función se cancela solo cuando se cancela ese token de cancelación o cuando una de las tareas participantes finaliza en un estado cancelado o produce una excepción.  
  
 La función `when_all` hereda el token de cancelación de cada tarea que constituye la operación global cuando no se proporciona un token de cancelación. La tarea que se devuelve de `when_all` se cancela cuando se cancela cualquiera de estos tokens y al menos una de las tareas participantes no se ha iniciado todavía o se está ejecutando. Un comportamiento similar se produce cuando una de las tareas produce una excepción: la tarea que se devuelve de `when_all` se cancela inmediatamente con dicha excepción.  
  
 El runtime elige el token de cancelación para la tarea que se devuelve de la función `when_any` cuando se completa dicha tarea. Si ninguna de las tareas participantes finaliza en un estado completado y una o más tareas producen una excepción, se elige una de las tareas que se inician para completar `when_any` y su token se elige como token para la tarea final. Si más de una tarea finaliza con el estado completado, la tarea que se devuelve de la tarea `when_any` finaliza con un estado completado. El runtime intenta elegir una tarea completa cuyo token no se cancele en el momento de la finalización de manera que la tarea que se devuelve de `when_any` no se cancele de inmediato aunque otras tareas en ejecución puedan completarse posteriormente.  
  
 [[Arriba](#top)]  
  
###  <a name="cancel"></a> Usar el método cancel para cancelar el trabajo paralelo  

 El [concurrency::task_group::cancel](reference/task-group-class.md#cancel) y [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) métodos establecen un grupo de tareas en el estado cancelado. Después de llamar a `cancel`, el grupo de tareas no iniciará ninguna otra tarea posterior. Los métodos `cancel` pueden invocarse a través de varias tareas secundarias. Una tarea cancelada hace el [concurrency::task_group::wait](reference/task-group-class.md#wait) y [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait) métodos para devolver [Concurrency:: Canceled](reference/concurrency-namespace-enums.md#task_group_status).  

  
 Si un grupo de tareas está cancelado, las llamadas de cada tarea secundaria en el tiempo de ejecución pueden activar un *punto de interrupción*, lo que hace que el runtime inicie y detecte un tipo de excepción interna para cancelar las tareas activas. El Runtime de simultaneidad no define puntos de interrupción concretos; estos pueden producirse en cualquier llamada al runtime. El runtime debe controlar las excepciones que se producen para poder llevar a cabo la cancelación. Por tanto, no deben controlarse excepciones desconocidas en el cuerpo de una tarea.  
  
 Si una tarea secundaria realiza una operación que exige mucho tiempo y no llama al runtime, debe comprobarse periódicamente si se he cancelado y si ha salido de forma puntual. En el ejemplo siguiente se muestra un mecanismo para determinar cuándo un trabajo está cancelado. La tarea `t4` cancela el grupo de tareas primario cuando encuentra un error. La tarea `t5` llama de tanto en tanto al método `structured_task_group::is_canceling` para comprobar si se ha cancelado. Si el grupo de tareas primario está cancelado, la tarea `t5` imprime un mensaje y sale.  
  
 [!code-cpp[concrt-task-tree#6](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_6.cpp)]  
  
 Este ejemplo comprueba la cancelación cada 100<sup>th</sup> iteración del bucle de tarea. La frecuencia con la que se comprueba la cancelación depende de la cantidad de trabajo que realiza la tarea y la rapidez necesaria con la que las tareas deben responder a la cancelación.  
  
 Si no tiene acceso al objeto del grupo de tareas primario, llame a la [Concurrency:: is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) función para determinar si el grupo de tareas primario está cancelado.  

  
 El método `cancel` solo afecta a las tareas secundarias. Por ejemplo, si se cancela el grupo de tareas `tg1` de la ilustración del árbol de trabajo paralelo, todas las tareas del árbol (`t1`, `t2`, `t3`, `t4` y `t5`) se verán afectadas. Si se cancela el grupo de tareas anidado `tg2`, solo las tareas `t4` y `t5` se verán afectadas.  
  
 Al llamar al método `cancel`, todos los grupos de tareas secundarios también se cancelan. Sin embargo, la cancelación no afecta a ningún elemento primario del grupo de tareas de un árbol de trabajo paralelo. En los ejemplos siguientes se usa el árbol de trabajo paralelo de la ilustración para mostrar este comportamiento.  
  
 En el primero de estos ejemplos se crea una función de trabajo para la tarea `t4`, que es un elemento secundario del grupo de tareas `tg2`. La función de trabajo llama a la función `work` en un bucle. Si las llamadas a `work` no se realizan correctamente, la tarea cancela su grupo de tareas primario. Esto hace que el grupo de tareas `tg2` adopte el estado cancelado, pero no cancela el grupo de tareas `tg1`.  
  
 [!code-cpp[concrt-task-tree#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_7.cpp)]  
  
 Este segundo ejemplo se parece el primero, salvo por el hecho de que la tarea cancela el grupo de tareas `tg1`. Esto afecta a todas las tareas del árbol (`t1`, `t2`, `t3`, `t4`y `t5`).  
  
 [!code-cpp[concrt-task-tree#3](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_8.cpp)]  
  
 La clase `structured_task_group` no es segura para la ejecución de subprocesos. Por tanto, si una tarea secundaria llama a un método de su objeto `structured_task_group` primario, se produce un comportamiento no especificado. Las excepciones a esta regla son las `structured_task_group::cancel` y [concurrency::structured_task_group::is_canceling](reference/structured-task-group-class.md#is_canceling) métodos. Una tarea secundaria puede llamar a estos métodos para cancelar el grupo de tareas primario y comprobar la cancelación.  

 
> [!CAUTION]
>  Aunque puede utilizar un token de cancelación para cancelar el trabajo realizado por un grupo de tareas que se ejecuta como elemento secundario de un objeto `task`, no puede usar los métodos `task_group::cancel` ni `structured_task_group::cancel` para cancelar los objetos `task` que se ejecutan en un grupo de tareas.  
  
 [[Arriba](#top)]  
  
###  <a name="exceptions"></a> Usar excepciones para cancelar el trabajo paralelo  
 El uso de tokens de cancelación y el método `cancel` son más eficaces que el control de excepciones en la cancelación de un árbol de trabajo paralelo. Los tokens de cancelación y el método `cancel` cancelan una tarea y todas las tareas secundarias de forma descendente. Por el contrario, el control de excepciones funciona de manera ascendente y debe cancelar cada grupo de tareas secundario por separado a medida que la excepción se propaga hacia arriba. El tema [Exception Handling](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md) explica cómo el Runtime de simultaneidad usa las excepciones para comunicar los errores. Sin embargo, no todas las excepciones indican un error. Por ejemplo, un algoritmo de búsqueda puede cancelar su tarea asociada cuando encuentra el resultado. Sin embargo, tal y como se mencionó anteriormente, el control de excepciones resulta menos eficaz que el método `cancel` para cancelar el trabajo paralelo.  
  
> [!CAUTION]
>  Se recomienda usar excepciones para cancelar el trabajo paralelo solo cuando sea necesario. Los tokens de cancelación y los métodos `cancel` del grupo de tareas son más eficaces y menos propensos a errores.  
  
 Cuando se produce una excepción en el cuerpo de una función de trabajo que se pasa a un grupo de tareas, el runtime almacena esa excepción y calcula las referencias de la excepción en el contexto en el que se espera a que el grupo de tareas finalice. Como sucede con el método `cancel`, el runtime descarta cualquier tarea que no se haya iniciado todavía y no acepta nuevas tareas.  
  
 Este tercer ejemplo se parece al segundo, salvo en que la tarea `t4` produce una excepción para cancelar el grupo de tareas `tg2`. Este ejemplo se utiliza un `try` - `catch` bloque para comprobar la cancelación cuando el grupo de tareas `tg2` espera a que sus tareas secundarias finalicen. Al igual que en el primer ejemplo, esto hace que el grupo de tareas `tg2` pase a tener el estado cancelado, pero no cancela el grupo de tareas `tg1`.  
  
 [!code-cpp[concrt-task-tree#4](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_9.cpp)]  
  
 En este cuarto ejemplo se usa el control de excepciones para cancelar todo el árbol de trabajo. En el ejemplo, la excepción se detecta cuando el grupo de tareas `tg1` espera a que sus tareas secundarias finalicen y no cuando el grupo de tareas `tg2` espera a sus tareas secundarias. Al igual que en el segundo ejemplo, esto hace que los dos grupos de tareas del árbol, `tg1` y `tg2`, pasen a tener el estado cancelado.  
  
 [!code-cpp[concrt-task-tree#5](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_10.cpp)]  
  
 Como los métodos `task_group::wait` y `structured_task_group::wait` se inician cuando una tarea secundaria produce una excepción, no devuelven ningún valor.  
  
 [[Arriba](#top)]  
  
##  <a name="algorithms"></a> Cancelar algoritmos paralelos  
 Los algoritmos paralelos de PPL, por ejemplo, `parallel_for`, se basan en grupos de tareas. Por tanto, pueden usarse muchas técnicas similares para cancelar un algoritmo paralelo.  
  
 En los ejemplos siguientes se muestran varios mecanismos para cancelar un algoritmo paralelo.  
  
 En el ejemplo siguiente se utiliza la función `run_with_cancellation_token` para llamar al algoritmo `parallel_for`. La función `run_with_cancellation_token` utiliza un token de cancelación como argumento y llama a la función de trabajo proporcionada sincrónicamente. Como los algoritmos paralelos se basan en tareas, heredan el token de cancelación de la tarea principal. Por tanto, `parallel_for` puede responder a la cancelación.  
  
 [!code-cpp[concrt-cancel-parallel-for#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_11.cpp)]  
  

 En el ejemplo siguiente se usa el [concurrency::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait) método para llamar a la `parallel_for` algoritmo. El método `structured_task_group::run_and_wait` espera a que la tarea proporcionada finalice. El objeto `structured_task_group` permite que la función de trabajo cancele la tarea.  
  
 [!code-cpp[concrt-task-tree#7](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_12.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
```Output  
The task group status is: canceled.  
```  
  
 En el siguiente ejemplo se usa el control de excepciones para cancelar un bucle `parallel_for`. El runtime calcula las referencias de la excepción en el contexto de la llamada.  
  
 [!code-cpp[concrt-task-tree#9](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_13.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
```Output  
Caught 50  
```  
  
 En el siguiente ejemplo se usa una marca booleana para coordinar la cancelación de un bucle `parallel_for`. En este ejemplo se ejecutan todas las tareas, ya que no se usa el método `cancel` ni el control de excepciones para cancelar el conjunto completo de tareas. Por tanto, esta técnica puede tener mayor sobrecarga computacional que un mecanismo de cancelación.  
  
 [!code-cpp[concrt-task-tree#8](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_14.cpp)]  
  
 Cada uno de los métodos de cancelación tiene ventajas sobre los otros. Elija el método que mejor se ajuste a sus necesidades concretas.  
  
 [[Arriba](#top)]  
  
##  <a name="when"></a> Cuando no se usa la cancelación  
 El uso de la cancelación es adecuado cuando cada miembro de un grupo de tareas relacionadas puede salir de forma puntual. Sin embargo, hay algunos escenarios en los que la cancelación podría no resultar adecuada para su aplicación. Por ejemplo, dado que la cancelación de tareas es cooperativa, el conjunto completo de tareas no se cancelará si alguna tarea individual está bloqueada. Por ejemplo, si una tarea no se ha iniciado todavía pero desbloquea otra tarea activa, no se iniciará si el grupo de tareas está cancelado. Esto puede generar una situación de interbloqueo en la aplicación. Un segundo ejemplo donde el uso de la cancelación puede no ser adecuado es cuando se cancela una tarea, pero su tarea secundaria realiza una operación importante, como liberar un recurso. Dado que el conjunto completo de tareas se cancela a la vez que la tarea primaria, esa operación no se ejecutará. Para obtener un ejemplo que ilustre este punto, consulte la [entender cómo cancelación y excepción control afecta a la destrucción de objetos](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) sección de procedimientos recomendados en el tema Parallel Patterns Library.  
  
 [[Arriba](#top)]  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Procedimiento para usar la cancelación para interrumpir un bucle Parallel](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)|Muestra cómo se usa la cancelación para implementar un algoritmo de búsqueda paralelo.|  
|[Procedimiento para usar el control de excepciones para interrumpir un bucle Parallel](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Muestra cómo usar la clase `task_group` para escribir un algoritmo de búsqueda en una estructura de árbol básica.|  
|[Control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Describe cómo el runtime controla las excepciones generadas por grupos de tareas, tareas ligeras y agentes asincrónicos y cómo se responde a las excepciones en las aplicaciones.|  
|[Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|Describe cómo se relacionan las tareas con los grupos de tareas y cómo se pueden usar tareas estructuradas y no estructuradas en las aplicaciones.|  
|[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)|Describe los algoritmos paralelos, que realizan el trabajo de forma simultánea en colecciones de datos.|  
|[Biblioteca de patrones de procesamiento paralelo (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Proporciona información general sobre la Biblioteca de modelos de procesamiento paralelo.|  
  
## <a name="reference"></a>Referencia  
 [task (clase) (Runtime de simultaneidad)](../../parallel/concrt/reference/task-class.md)  
  
 [cancellation_token_source (clase)](../../parallel/concrt/reference/cancellation-token-source-class.md)  
  
 [cancellation_token (clase)](../../parallel/concrt/reference/cancellation-token-class.md)  
  
 [task_group (clase)](reference/task-group-class.md)  
  
 [structured_task_group (clase)](../../parallel/concrt/reference/structured-task-group-class.md)  

 [parallel_for (función)](reference/concurrency-namespace-functions.md#parallel_for)


