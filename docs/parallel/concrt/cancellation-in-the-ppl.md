---
title: Cancelación en la biblioteca PPL
ms.date: 11/19/2018
helpviewer_keywords:
- parallel algorithms, canceling [Concurrency Runtime]
- canceling parallel algorithms [Concurrency Runtime]
- parallel tasks, canceling [Concurrency Runtime]
- cancellation in the PPL
- parallel work trees [Concurrency Runtime]
- canceling parallel tasks [Concurrency Runtime]
ms.assetid: baaef417-b2f9-470e-b8bd-9ed890725b35
ms.openlocfilehash: 27c0ea3cfcf62060800c1c0b034dde7de6357250
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368494"
---
# <a name="cancellation-in-the-ppl"></a>Cancelación en la biblioteca PPL

En este documento se explica el rol de cancelación de la biblioteca de patrones de procesamiento paralelo (PPL), cómo se cancela el trabajo paralelo y cómo se determina cuándo se cancela un trabajo paralelo.

> [!NOTE]
> El runtime usa el control de excepciones para implementar la cancelación. No debe detectar ni administrar estas excepciones en su código. Además, le recomendamos que escriba código seguro ante excepciones en los cuerpos de las funciones de las tareas. Por ejemplo, puede usar el patrón *Resource Acquisition Is Initialization* (RAII) para asegurarse de que los recursos se controlan correctamente cuando se produce una excepción en el cuerpo de una tarea. Para obtener un ejemplo completo que utiliza el patrón RAII para limpiar un recurso en una tarea cancelable, vea [Tutorial: eliminación de trabajo de un](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)subproceso de interfaz de usuario .

## <a name="key-points"></a>Puntos clave

- La cancelación es cooperativa e implica la coordinación entre el código que solicita la cancelación y la tarea que responde a la cancelación.

- Siempre que sea posible, use tokens de cancelación para cancelar el trabajo. La clase [concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) define un token de cancelación.

- Cuando utilice tokens de cancelación, use el método [concurrency::cancellation_token_source::cancel](reference/cancellation-token-source-class.md#cancel) para iniciar la cancelación y la función [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) para responder a la cancelación. Utilice el método [concurrency::cancellation_token::is_canceled](reference/cancellation-token-class.md#is_canceled) para comprobar si alguna otra tarea ha solicitado la cancelación.

- La cancelación no se produce de inmediato. Aunque no se inicia el nuevo trabajo si se cancela una tarea o un grupo de tareas, el trabajo activo debe buscar y responder a la cancelación.

- Una continuación basada en valores hereda el token de cancelación de la tarea anterior. Una continuación basada en tareas nunca hereda el token de la tarea anterior.

- Utilice el método [concurrency::cancellation_token::none](reference/cancellation-token-class.md#none) cuando llame a `cancellation_token` un constructor o función que toma un objeto, pero no desea que la operación se pueda cancelar. Además, si no pasa un token de cancelación al constructor [concurrency::task](../../parallel/concrt/reference/task-class.md) o a la función [concurrency::create_task,](reference/concurrency-namespace-functions.md#create_task) esa tarea no se puede cancelar.

## <a name="in-this-document"></a><a name="top"></a>En este documento

- [Árboles de trabajo paralelo](#trees)

- [Cancelar tareas paralelas](#tasks)

  - [Usar un token de cancelación para cancelar trabajo paralelo](#tokens)

  - [Usar el método cancel para cancelar el trabajo paralelo](#cancel)

  - [Usar excepciones para cancelar el trabajo paralelo](#exceptions)

- [Cancelar algoritmos paralelos](#algorithms)

- [Cuándo no conviene usar la cancelación](#when)

## <a name="parallel-work-trees"></a><a name="trees"></a>Arboles de trabajo paralelos

PPL usa tareas y grupos de tareas para administrar tareas y cálculos específicos. Puede anidar grupos de tareas para formar *árboles* de trabajo paralelo. En la ilustración siguiente se muestra un árbol de trabajo paralelo. En esta ilustración, `tg1` y `tg2` representan grupos de tareas; `t1`, `t2`, `t3`, `t4` y `t5` representan el trabajo que realizan los grupos de tareas.

![Árbol de trabajo paralelo](../../parallel/concrt/media/parallelwork_trees.png "Árbol de trabajo paralelo")

En el ejemplo siguiente se muestra el código necesario para crear el árbol de la ilustración. En este `tg1` ejemplo, y `tg2` son [objetos concurrency::structured_task_group;](../../parallel/concrt/reference/structured-task-group-class.md) `t1`, `t2` `t3`, `t4`, `t5` , y son objetos [concurrency::task_handle.](../../parallel/concrt/reference/task-handle-class.md)

[!code-cpp[concrt-task-tree#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_1.cpp)]

También puede usar la clase [concurrency::task_group](reference/task-group-class.md) para crear un árbol de trabajo similar. La clase [concurrency::task](../../parallel/concrt/reference/task-class.md) también admite la noción de un árbol de trabajo. Sin embargo, un árbol `task` es un árbol de dependencia. En un árbol `task`, los trabajos futuros se completan después del trabajo actual. En un árbol de grupo de tareas, el trabajo interno se completa antes que el trabajo externo. Para obtener más información sobre las diferencias entre tareas y grupos de tareas, vea [Paralelismo](../../parallel/concrt/task-parallelism-concurrency-runtime.md)de tareas .

[[Superior](#top)]

## <a name="canceling-parallel-tasks"></a><a name="tasks"></a>Cancelación de tareas paralelas

Existen varias maneras de cancelar el trabajo paralelo. La forma preferida es utilizar un token de cancelación. Los grupos de tareas también admiten el método [concurrency::task_group::cancel](reference/task-group-class.md#cancel) y el método [concurrency::structured_task_group::cancel.](reference/structured-task-group-class.md#cancel) La otra manera consiste en iniciar una excepción en el cuerpo de una función de trabajo de una tarea. Independientemente del método que elija, debe saber que la cancelación no se produce de inmediato. Aunque no se inicia el nuevo trabajo si se cancela una tarea o un grupo de tareas, el trabajo activo debe buscar y responder a la cancelación.

Para obtener más ejemplos que cancelan tareas paralelas, vea Tutorial: Conexión mediante [tareas y solicitudes HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md), [Cómo: Usar la cancelación para interrumpir un bucle paralelo](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)y Cómo: Usar el control de [excepciones para interrumpir un bucle paralelo](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

### <a name="using-a-cancellation-token-to-cancel-parallel-work"></a><a name="tokens"></a>Uso de un token de cancelación para cancelar el trabajo paralelo

Las clases `task`, `task_group` y `structured_task_group` admiten la cancelación mediante tokens de cancelación. La PPL define las clases [concurrency::cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md) y [concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) para este propósito. Cuando usa un token de cancelación para cancelar el trabajo, el runtime no inicia el nuevo trabajo suscrito a dicho token. El trabajo que ya está activo puede usar la [is_canceled](../../parallel/concrt/reference/cancellation-token-class.md#is_canceled) función miembro para supervisar el token de cancelación y detenerse cuando puede.

Para iniciar la cancelación, llame al método [concurrency::cancellation_token_source::cancel.](reference/cancellation-token-source-class.md#cancel) A la cancelación se responde de las siguientes maneras:

- Para `task` los objetos, utilice la función [concurrency::cancel_current_task.](reference/concurrency-namespace-functions.md#cancel_current_task) `cancel_current_task` cancela la tarea actual y cualquiera de sus continuaciones basadas en valores. (No cancela el *token* de cancelación asociado a la tarea o sus continuaciones.)

- Para grupos de tareas y algoritmos paralelos, utilice la función [concurrency::is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) para detectar la cancelación y la devolución lo antes posible desde el cuerpo de la tarea cuando esta función devuelve **true**. (No llame a `cancel_current_task` desde un grupo de tareas).

En el ejemplo siguiente se muestra el primer patrón básico para la cancelación de la tarea. En algunas ocasiones, el cuerpo de la tarea comprueba la cancelación dentro de un bucle.

[!code-cpp[concrt-task-basic-cancellation#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_2.cpp)]

La función `cancel_current_task` se inicia; por consiguiente, no necesita regresar de manera explícita de la función o bucle actual.

> [!TIP]
> Como alternativa, puede llamar a la función `cancel_current_task` [concurrency::interruption_point](reference/concurrency-namespace-functions.md#interruption_point) en lugar de .

Es importante llamar a `cancel_current_task` cuando responda a la cancelación porque pasa la tarea al estado cancelado. Si regresa prematuramente de la función en lugar de llamar a `cancel_current_task`, la operación pasa al estado completado y se ejecuta cualquier continuación basada en valores.

> [!CAUTION]
> Nunca inicie `task_canceled` desde su código. En su lugar, llame a `cancel_current_task`.

Cuando una tarea finaliza en el estado cancelado, el método [concurrency::task::get](reference/task-class.md#get) produce [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md). (Por el contrario, [concurrency::task::wait](reference/task-class.md#wait) devuelve [task_status::canceled](reference/concurrency-namespace-enums.md#task_group_status) y no produce.) En el ejemplo siguiente se muestra este comportamiento para una continuación basada en tareas. Siempre se llama a una continuación basada en tareas, incluso cuando se cancela la tarea anterior.

[!code-cpp[concrt-task-canceled#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_3.cpp)]

Dado que las continuaciones basadas en valores heredan el token de su tarea anterior a menos que se crearan con un token explícito, las continuaciones entran inmediatamente en estado cancelado incluso si la tarea anterior todavía se está ejecutando. Por tanto, cualquier excepción que produzca la tarea anterior tras la cancelación no se propaga a las tareas de continuación. La cancelación siempre invalida el estado de la tarea anterior. El ejemplo siguiente es similar al anterior, pero muestra el comportamiento de una continuación basada en valores.

[!code-cpp[concrt-task-canceled#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_4.cpp)]

> [!CAUTION]
> Si no pasa un token `task` de cancelación al constructor o a la función [concurrency::create_task,](reference/concurrency-namespace-functions.md#create_task) esa tarea no se puede cancelar. Además, debe pasar el mismo token de cancelación al constructor de cualquier tarea anidada (es decir, las tareas que se crean en el cuerpo de otra tarea) para cancelar todas las tareas a la vez.

Puede que desee ejecutar código arbitrario cuando se cancele un token de cancelación. Por ejemplo, si el usuario elige un botón **Cancelar** en la interfaz de usuario para cancelar la operación, puede deshabilitar ese botón hasta que el usuario inicie otra operación. En el ejemplo siguiente se muestra cómo utilizar el método [concurrency:cancellation_token::register_callback](reference/cancellation-token-class.md#register_callback) para registrar una función de devolución de llamada que se ejecuta cuando se cancela un token de cancelación.

[!code-cpp[concrt-task-cancellation-callback#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_5.cpp)]

El [paralelismo](../../parallel/concrt/task-parallelism-concurrency-runtime.md) de tareas del documento explica la diferencia entre las continuaciones basadas en valores y las continuaciones basadas en tareas. Si no proporciona un objeto `cancellation_token` a una tarea de continuación, la continuación hereda el token de cancelación de la tarea anterior de las siguientes maneras:

- Una continuación basada en valores siempre hereda el token de cancelación de la tarea anterior.

- Una continuación basada en tareas nunca hereda el token de cancelación de la tarea anterior. La única manera de hacer que una continuación basada en tareas sea cancelable es pasar de manera explícita un token de cancelación.

Estos comportamientos no se ven afectados por una tarea con errores (es decir, una que produce una excepción). En este caso, se cancela una continuación basada en valores; una continuación basada en tareas no se cancela.

> [!CAUTION]
> Una tarea que se crea en otra tarea (es decir, una tarea anidada) no hereda el token de cancelación de la tarea principal. Solo una continuación basada en valores hereda el token de cancelación de la tarea anterior.

> [!TIP]
> Utilice el método [concurrency::cancellation_token::none](reference/cancellation-token-class.md#none) cuando llame a `cancellation_token` un constructor o función que toma un objeto y no desea que la operación se pueda cancelar.

También puede proporcionar un token de cancelación al constructor de un objeto `task_group` o `structured_task_group`. Un aspecto importante que debe tener en cuenta es que los grupos de tareas secundarios heredan este token de cancelación. Para obtener un ejemplo que muestra este concepto mediante la función [concurrency::run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) que se va a ejecutar para llamar `parallel_for`, vea Cancelar [algoritmos paralelos](#algorithms) más adelante en este documento.

[[Superior](#top)]

#### <a name="cancellation-tokens-and-task-composition"></a>Tokens de cancelación y composición de tareas

Las funciones [concurrency::when_all](reference/concurrency-namespace-functions.md#when_all) y [concurrency::when_any](reference/concurrency-namespace-functions.md#when_all) pueden ayudarle a componer varias tareas para implementar patrones comunes. En esta sección se describe cómo operan estas funciones con tokens de cancelación.

Cuando se proporciona un token `when_all` `when_any` de cancelación a la función y, esa función se cancela solo cuando se cancela ese token de cancelación o cuando una de las tareas participantes finaliza en un estado cancelado o produce una excepción.

La función `when_all` hereda el token de cancelación de cada tarea que constituye la operación global cuando no se proporciona un token de cancelación. La tarea desde `when_all` la que se devuelve se cancela cuando se cancela cualquiera de estos tokens y al menos una de las tareas participantes aún no se ha iniciado o se está ejecutando. Un comportamiento similar se produce cuando una de las tareas `when_all` produce una excepción: la tarea desde la que se devuelve se cancela inmediatamente con esa excepción.

El runtime elige el token de cancelación para la tarea que se devuelve de la función `when_any` cuando se completa dicha tarea. Si ninguna de las tareas participantes finaliza en un estado completado y una o más tareas producen una excepción, se elige una de las tareas que se inician para completar `when_any` y su token se elige como token para la tarea final. Si más de una tarea finaliza con el estado completado, la tarea que se devuelve de la tarea `when_any` finaliza con un estado completado. El runtime intenta elegir una tarea completa cuyo token no se cancele en el momento de la finalización de manera que la tarea que se devuelve de `when_any` no se cancele de inmediato aunque otras tareas en ejecución puedan completarse posteriormente.

[[Superior](#top)]

### <a name="using-the-cancel-method-to-cancel-parallel-work"></a><a name="cancel"></a>Uso del método cancel para cancelar el trabajo paralelo

Los métodos [concurrency:task_group::cancel](reference/task-group-class.md#cancel) y [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) establecen un grupo de tareas en el estado cancelado. Después de llamar a `cancel`, el grupo de tareas no iniciará ninguna otra tarea posterior. Los métodos `cancel` pueden invocarse a través de varias tareas secundarias. Una tarea cancelada hace que los métodos [concurrency::task_group::wait](reference/task-group-class.md#wait) y [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait) devuelvan [concurrency::canceled](reference/concurrency-namespace-enums.md#task_group_status).

Si se cancela un grupo de tareas, las llamadas de cada tarea secundaria al tiempo de ejecución pueden desencadenar un punto de *interrupción,* lo que hace que el tiempo de ejecución inicie y detecte un tipo de excepción interno para cancelar las tareas activas. El Runtime de simultaneidad no define puntos de interrupción concretos; estos pueden producirse en cualquier llamada al runtime. El runtime debe controlar las excepciones que se producen para poder llevar a cabo la cancelación. Por tanto, no deben controlarse excepciones desconocidas en el cuerpo de una tarea.

Si una tarea secundaria realiza una operación que exige mucho tiempo y no llama al runtime, debe comprobarse periódicamente si se he cancelado y si ha salido de forma puntual. En el ejemplo siguiente se muestra un mecanismo para determinar cuándo un trabajo está cancelado. La tarea `t4` cancela el grupo de tareas primario cuando encuentra un error. La tarea `t5` llama de tanto en tanto al método `structured_task_group::is_canceling` para comprobar si se ha cancelado. Si el grupo de tareas primario está cancelado, la tarea `t5` imprime un mensaje y sale.

[!code-cpp[concrt-task-tree#6](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_6.cpp)]

En este ejemplo se comprueba la<sup>th</sup> cancelación en cada iteración de 100 del bucle de tareas. La frecuencia con la que se comprueba la cancelación depende de la cantidad de trabajo que realiza la tarea y la rapidez necesaria con la que las tareas deben responder a la cancelación.

Si no tiene acceso al objeto de grupo de tareas primario, llame a la función [concurrency::is_current_task_group_canceling](reference/concurrency-namespace-functions.md#is_current_task_group_canceling) para determinar si se cancela el grupo de tareas primario.

El método `cancel` solo afecta a las tareas secundarias. Por ejemplo, si se cancela el grupo de tareas `tg1` de la ilustración del árbol de trabajo paralelo, todas las tareas del árbol (`t1`, `t2`, `t3`, `t4` y `t5`) se verán afectadas. Si se cancela el grupo de tareas anidado `tg2`, solo las tareas `t4` y `t5` se verán afectadas.

Al llamar al método `cancel`, todos los grupos de tareas secundarios también se cancelan. Sin embargo, la cancelación no afecta a ningún elemento primario del grupo de tareas de un árbol de trabajo paralelo. En los ejemplos siguientes se usa el árbol de trabajo paralelo de la ilustración para mostrar este comportamiento.

En el primero de estos ejemplos se crea una función de trabajo para la tarea `t4`, que es un elemento secundario del grupo de tareas `tg2`. La función de trabajo llama a la función `work` en un bucle. Si las llamadas a `work` no se realizan correctamente, la tarea cancela su grupo de tareas primario. Esto hace que el grupo de tareas `tg2` adopte el estado cancelado, pero no cancela el grupo de tareas `tg1`.

[!code-cpp[concrt-task-tree#2](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_7.cpp)]

Este segundo ejemplo se parece el primero, salvo por el hecho de que la tarea cancela el grupo de tareas `tg1`. Esto afecta a todas las tareas del árbol (`t1`, `t2`, `t3`, `t4`y `t5`).

[!code-cpp[concrt-task-tree#3](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_8.cpp)]

La clase `structured_task_group` no es segura para la ejecución de subprocesos. Por tanto, si una tarea secundaria llama a un método de su objeto `structured_task_group` primario, se produce un comportamiento no especificado. Las excepciones a esta `structured_task_group::cancel` regla son los métodos y [concurrency::structured_task_group::is_canceling.](reference/structured-task-group-class.md#is_canceling) Una tarea secundaria puede llamar a estos métodos para cancelar el grupo de tareas primario y comprobar la cancelación.

> [!CAUTION]
> Aunque puede utilizar un token de cancelación para cancelar el trabajo realizado por un grupo de tareas que se ejecuta como elemento secundario de un objeto `task`, no puede usar los métodos `task_group::cancel` ni `structured_task_group::cancel` para cancelar los objetos `task` que se ejecutan en un grupo de tareas.

[[Superior](#top)]

### <a name="using-exceptions-to-cancel-parallel-work"></a><a name="exceptions"></a>Uso de excepciones para cancelar el trabajo paralelo

El uso de tokens de cancelación y el método `cancel` son más eficaces que el control de excepciones en la cancelación de un árbol de trabajo paralelo. Los tokens de cancelación y el método `cancel` cancelan una tarea y todas las tareas secundarias de forma descendente. Por el contrario, el control de excepciones funciona de manera ascendente y debe cancelar cada grupo de tareas secundario por separado a medida que la excepción se propaga hacia arriba. En el tema Control de [excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md) se explica cómo el Runtime de simultaneidad usa excepciones para comunicar errores. Sin embargo, no todas las excepciones indican un error. Por ejemplo, un algoritmo de búsqueda puede cancelar su tarea asociada cuando encuentra el resultado. Sin embargo, tal y como se mencionó anteriormente, el control de excepciones resulta menos eficaz que el método `cancel` para cancelar el trabajo paralelo.

> [!CAUTION]
> Se recomienda usar excepciones para cancelar el trabajo paralelo solo cuando sea necesario. Los tokens de cancelación y los métodos `cancel` del grupo de tareas son más eficaces y menos propensos a errores.

Cuando se produce una excepción en el cuerpo de una función de trabajo que se pasa a un grupo de tareas, el runtime almacena esa excepción y serializa las referencias de la excepción en el contexto en el que se espera a que el grupo de tareas finalice. Como sucede con el método `cancel`, el runtime descarta cualquier tarea que no se haya iniciado todavía y no acepta nuevas tareas.

Este tercer ejemplo se parece al segundo, salvo en que la tarea `t4` produce una excepción para cancelar el grupo de tareas `tg2`. En este `try` - `catch` ejemplo se usa un bloque `tg2` para comprobar la cancelación cuando el grupo de tareas espera a que finalicen sus tareas secundarias. Al igual que en el primer ejemplo, esto hace que el grupo de tareas `tg2` pase a tener el estado cancelado, pero no cancela el grupo de tareas `tg1`.

[!code-cpp[concrt-task-tree#4](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_9.cpp)]

En este cuarto ejemplo se usa el control de excepciones para cancelar todo el árbol de trabajo. En el ejemplo, la excepción se detecta cuando el grupo de tareas `tg1` espera a que sus tareas secundarias finalicen y no cuando el grupo de tareas `tg2` espera a sus tareas secundarias. Al igual que en el segundo ejemplo, esto hace que los dos grupos de tareas del árbol, `tg1` y `tg2`, pasen a tener el estado cancelado.

[!code-cpp[concrt-task-tree#5](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_10.cpp)]

Como los métodos `task_group::wait` y `structured_task_group::wait` se inician cuando una tarea secundaria produce una excepción, no devuelven ningún valor.

[[Superior](#top)]

## <a name="canceling-parallel-algorithms"></a><a name="algorithms"></a>Cancelación de algoritmos paralelos

Los algoritmos paralelos de PPL, por ejemplo, `parallel_for`, se basan en grupos de tareas. Por tanto, pueden usarse muchas técnicas similares para cancelar un algoritmo paralelo.

En los ejemplos siguientes se muestran varios mecanismos para cancelar un algoritmo paralelo.

En el ejemplo siguiente se utiliza la función `run_with_cancellation_token` para llamar al algoritmo `parallel_for`. La función `run_with_cancellation_token` utiliza un token de cancelación como argumento y llama a la función de trabajo proporcionada sincrónicamente. Como los algoritmos paralelos se basan en tareas, heredan el token de cancelación de la tarea principal. Por tanto, `parallel_for` puede responder a la cancelación.

[!code-cpp[concrt-cancel-parallel-for#1](../../parallel/concrt/codesnippet/cpp/cancellation-in-the-ppl_11.cpp)]

En el ejemplo siguiente se utiliza el método [concurrency::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait) para llamar al `parallel_for` algoritmo. El método `structured_task_group::run_and_wait` espera a que la tarea proporcionada finalice. El objeto `structured_task_group` permite que la función de trabajo cancele la tarea.

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

[[Superior](#top)]

## <a name="when-not-to-use-cancellation"></a><a name="when"></a>Cuándo no usar la cancelación

El uso de la cancelación es adecuado cuando cada miembro de un grupo de tareas relacionadas puede salir de forma puntual. Sin embargo, hay algunos escenarios en los que la cancelación podría no resultar adecuada para su aplicación. Por ejemplo, dado que la cancelación de tareas es cooperativa, el conjunto completo de tareas no se cancelará si alguna tarea individual está bloqueada. Por ejemplo, si una tarea no se ha iniciado todavía pero desbloquea otra tarea activa, no se iniciará si el grupo de tareas está cancelado. Esto puede generar una situación de interbloqueo en la aplicación. Un segundo ejemplo donde el uso de la cancelación puede no ser adecuado es cuando se cancela una tarea, pero su tarea secundaria realiza una operación importante, como liberar un recurso. Dado que el conjunto completo de tareas se cancela a la vez que la tarea primaria, esa operación no se ejecutará. Para obtener un ejemplo que ilustra este punto, vea la sección Comprender cómo la cancelación y el control de [excepciones afectan a](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) la destrucción de objetos en el tema Prácticas recomendadas de la biblioteca de patrones paralelos.

[[Superior](#top)]

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Cómo: Usar la cancelación para interrumpir un bucle Parallel](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)|Muestra cómo se usa la cancelación para implementar un algoritmo de búsqueda paralelo.|
|[Cómo: Usar el control de excepciones para interrumpir un bucle Parallel](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Muestra cómo usar la clase `task_group` para escribir un algoritmo de búsqueda en una estructura de árbol básica.|
|[Control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Describe cómo el runtime controla las excepciones generadas por grupos de tareas, tareas ligeras y agentes asincrónicos y cómo se responde a las excepciones en las aplicaciones.|
|[Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|Describe cómo se relacionan las tareas con los grupos de tareas y cómo se pueden usar tareas estructuradas y no estructuradas en las aplicaciones.|
|[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)|Describe los algoritmos paralelos, que realizan el trabajo de forma simultánea en colecciones de datos.|
|[Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Proporciona información general sobre la Biblioteca de modelos de procesamiento paralelo.|

## <a name="reference"></a>Referencia

[Clase de tarea (Runtime de simultaneidad)](../../parallel/concrt/reference/task-class.md)

[Clase cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md)

[Clase cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md)

[Clase task_group](reference/task-group-class.md)

[Clase structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)

[parallel_for (función)](reference/concurrency-namespace-functions.md#parallel_for)
