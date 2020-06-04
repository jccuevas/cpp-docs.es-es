---
title: Paralelismo de tareas (Runtime de simultaneidad)
ms.date: 11/04/2016
helpviewer_keywords:
- structured task groups [Concurrency Runtime]
- structured tasks [Concurrency Runtime]
- task groups [Concurrency Runtime]
- task parallelism
- tasks [Concurrency Runtime]
ms.assetid: 42f05ac3-2098-494a-ba84-737fcdcad077
ms.openlocfilehash: f65521771db3eb0fe19dc863b1b49e9627fc60e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368586"
---
# <a name="task-parallelism-concurrency-runtime"></a>Paralelismo de tareas (Runtime de simultaneidad)

En el Runtime de simultaneidad, una *tarea* es una unidad de trabajo que realiza un trabajo específico y normalmente se ejecuta en paralelo con otras tareas. Una tarea se puede descomponer en tareas adicionales más detalladas que se organizan en un grupo de *tareas.*

Las tareas se usan al escribir código asincrónico y cuando se quiere que alguna operación se produzca después de que finalice la operación asincrónica. Por ejemplo, podría usar una tarea para leer de forma asincrónica desde un archivo y, a continuación, usar otra tarea (una tarea de *continuación,* que se explica más adelante en este documento) para procesar los datos después de que estén disponibles. A la inversa, se pueden usar grupos de tareas para descomponer el trabajo paralelo en partes más pequeñas. Supongamos, por ejemplo, que tiene un algoritmo recursivo que divide el trabajo restante en dos partes. Puede usar grupos de tareas para ejecutar estas partes simultáneamente y esperar a que el trabajo dividido se complete.

> [!TIP]
> Cuando desee aplicar la misma rutina a cada elemento de una colección en paralelo, utilice un algoritmo paralelo, como [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for), en lugar de una tarea o grupo de tareas. Para obtener más información acerca de los algoritmos paralelos, vea [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).

## <a name="key-points"></a>Puntos clave

- Cuando se pasan variables por referencia a una expresión lambda, es necesario garantizar que esas variables van a persistir hasta que la tarea finalice.

- Use tareas (la clase [concurrency::task)](../../parallel/concrt/reference/task-class.md) al escribir código asincrónico. La clase task usa como programador el grupo de subprocesos de Windows, no el Runtime de simultaneidad.

- Use grupos de tareas (la clase [concurrency::task_group](reference/task-group-class.md) o el algoritmo [concurrency::parallel_invoke)](reference/concurrency-namespace-functions.md#parallel_invoke) cuando desee descomponer el trabajo paralelo en partes más pequeñas y, a continuación, espere a que se completen esas piezas más pequeñas.

- Utilice el método [concurrency::task::then](reference/task-class.md#then) para crear continuaciones. Una *continuación* es una tarea que se ejecuta de forma asincrónica una vez completada otra tarea. Puede conectar un número indeterminado de continuaciones para formar una cadena de trabajo asincrónico.

- Una continuación basada en tareas está programada siempre para ejecutarse cuando finaliza la tarea antecedente, aun cuando esta se cancele o genere una excepción.

- Use [concurrency::when_all](reference/concurrency-namespace-functions.md#when_all) para crear una tarea que se complete después de que se complete cada miembro de un conjunto de tareas. Use [concurrency::when_any](reference/concurrency-namespace-functions.md#when_any) para crear una tarea que se complete después de que se complete un miembro de un conjunto de tareas.

- Las tareas y los grupos de tareas pueden participar en el mecanismo de cancelación de la Biblioteca de patrones de procesamiento paralelo (PPL). Para obtener más información, consulte [Cancelación en la PPL](cancellation-in-the-ppl.md).

- Para obtener información sobre cómo el tiempo de ejecución controla las excepciones que producen las tareas y los grupos de tareas, vea Control de [excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="in-this-document"></a>En este documento

- [Uso de expresiones lambda](#lambdas)

- [La clase task](#task-class)

- [Tareas de continuación](#continuations)

- [Continuaciones basadas en valores frente a continuaciones basadas en tareas](#value-versus-task)

- [Tareas de composición](#composing-tasks)

  - [La función when_all](#when-all)

  - [La función when_any](#when-any)

- [Ejecución retrasada de una tarea](#delayed-tasks)

- [Grupos de tareas](#task-groups)

- [Comparación de task_group y structured_task_group](#comparing-groups)

- [Ejemplo](#example)

- [Programación sólida](#robust)

## <a name="using-lambda-expressions"></a><a name="lambdas"></a>Uso de expresiones Lambda

Dada su sintaxis concisa, las expresiones lambda son una forma habitual de definir el trabajo que las tareas y los grupos de tareas llevan a cabo. Estas son algunas sugerencias de uso:

- Como las tareas normalmente se ejecutan en subprocesos en segundo plano, tenga en cuenta la duración del objeto cuando capture variables en expresiones lambda. Cuando se captura una variable por valor, se hace una copia de esa variable en el cuerpo de la lambda. Esta copia no se realiza cuando se captura por referencia. Por lo tanto, asegúrese de que la duración de la variable que capture por referencia es mayor que la tarea que la usa.

- Cuando pase una expresión lambda a una tarea, no capture las variables que se asignan en la pila por referencia.

- Sea explícito sobre las variables que captura en expresiones lambda para que pueda identificar lo que está capturando por valor frente a por referencia. Por este motivo, recomendamos no usar las opciones `[=]` o `[&]` en expresiones lambda.

Un patrón común tiene lugar cuando una tarea en una cadena de continuación se asigna a una variable y otra tarea lee esa variable. No se puede capturar por valor porque cada tarea de continuación contendría una copia diferente de la variable. Para las variables asignadas a la pila, tampoco se puede capturar por referencia porque la variable puede ya no ser válida.

Para resolver este problema, utilice un puntero inteligente, como [std::shared_ptr](../../standard-library/shared-ptr-class.md), para ajustar la variable y pasar el puntero inteligente por valor. De este modo, el objeto subyacente se puede asignar y leer, y su duración será mayor que la de las tareas que lo usan. Use esta técnica incluso cuando la variable sea un puntero o un identificador de recuento de referencia (`^`) a un objeto de Windows Runtime. Este es un ejemplo básico:

[!code-cpp[concrt-lambda-task-lifetime#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_1.cpp)]

Para obtener más información acerca de las expresiones lambda, consulte [Expresiones](../../cpp/lambda-expressions-in-cpp.md)de Lambda .

## <a name="the-task-class"></a><a name="task-class"></a>La tarea Clase

Puede usar la clase [concurrency::task](../../parallel/concrt/reference/task-class.md) para componer tareas en un conjunto de operaciones dependientes. Este modelo de composición está respaldado por la noción de *continuaciones.* Una continuación permite que el código se ejecute cuando se complete la tarea anterior, o *anterior*. El resultado de la tarea antecedente se pasa como entrada para una o varias tareas de continuación. Cuando una tarea antecedente se completa, las tareas de continuación en espera están programadas para ejecutarse. Cada tarea de continuación recibe una copia del resultado de la tarea anterior. Las tareas de continuación también pueden ser, a su vez, tareas antecedentes de otras continuaciones, lo que hace que se vaya creando una cadena de tareas. Las continuaciones sirven para crear cadenas de tareas de longitud arbitraria que tienen dependencias específicas entre ellas. Asimismo, una tarea puede participar en la cancelación antes de que una tarea se inicie o bien de manera cooperativa, mientras se está ejecutando. Para obtener más información sobre este modelo de cancelación, consulte [Cancelación en la PPL](cancellation-in-the-ppl.md).

`task` es una clase de plantilla. El parámetro de tipo `T` es el tipo del resultado generado por la tarea. Este tipo puede ser `void` si la tarea no devuelve un valor. `T` no puede usar el modificador `const`.

Cuando se crea una tarea, se proporciona una *función* de trabajo que realiza el cuerpo de la tarea. Esta función de trabajo tiene la forma de una función lambda, un puntero de función o un objeto de función. Para esperar a que finalice una tarea sin obtener el resultado, llame al método [concurrency::task::wait.](reference/task-class.md#wait) El `task::wait` método devuelve un valor [concurrency::task_status](reference/concurrency-namespace-enums.md#task_group_status) que describe si la tarea se ha completado o cancelado. Para obtener el resultado de la tarea, llame al método [concurrency::task::get.](reference/task-class.md#get) Este método llama a `task::wait` para esperar a que la tarea finalice y, por lo tanto, bloquea la ejecución del subproceso actual hasta que el resultado esté disponible.

En el siguiente ejemplo se muestra cómo crear una tarea, esperar su resultado y mostrar el valor correspondiente. En los ejemplos de esta documentación se usan funciones lambda porque proporcionan una sintaxis más concisa. Sin embargo, también se pueden usar objetos de función y punteros de función al trabajar con tareas.

[!code-cpp[concrt-basic-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_2.cpp)]

Cuando se usa la función [concurrency::create_task,](reference/concurrency-namespace-functions.md#create_task) puede usar la `auto` palabra clave en lugar de declarar el tipo. Veamos, por ejemplo, este código con el que se crea e imprime la matriz de identidad:

[!code-cpp[concrt-create-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_3.cpp)]

Puede usar la función `create_task` para crear la operación equivalente.

[!code-cpp[concrt-create-task#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_4.cpp)]

Si se produce una excepción mientras una tarea se ejecuta, el Runtime calcula las referencias a esa excepción en la siguiente llamada a `task::get` o `task::wait`, o bien a una continuación basada en tareas. Para obtener más información sobre el mecanismo de control de excepciones de tarea, vea [Control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Para obtener un `task`ejemplo que usa , [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md), cancelación, vea [Tutorial: Conexión mediante tareas y solicitudes HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md). (La clase `task_completion_event` se describe más adelante en este documento).

> [!TIP]
> Para obtener información detallada sobre las tareas específicas de las aplicaciones para UWP, consulta [Programación asincrónica en C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) y Creación de [operaciones asincrónicas en C++ para aplicaciones para UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).

## <a name="continuation-tasks"></a><a name="continuations"></a>Tareas de continuación

En la programación asincrónica, es muy común que una operación asincrónica, al finalizar, invoque una segunda operación y le pase los datos. Tradicionalmente, esto se realiza mediante métodos de devolución de llamada. En el Runtime de simultaneidad, las tareas de *continuación*proporcionan la misma funcionalidad. Una tarea de continuación (también conocida como continuación) es una tarea asincrónica invocada por otra tarea, que se conoce como *el antecedente,* cuando se completa el antecedente. El uso de continuaciones permite hacer lo siguiente:

- Pasar datos del antecedente a la continuación.

- Especificar las condiciones exactas en las que se invoca o no se invoca la continuación.

- Cancelar una continuación antes de que se inicie o de forma cooperativa mientras se ejecuta.

- Proporcionar sugerencias sobre cómo debería programarse la continuación. (Esto solo se aplica a las aplicaciones de la Plataforma universal de Windows (UWP). Para obtener más información, consulta [Crear operaciones asincrónicas en C++ para aplicaciones para UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).)

- Invocar varias continuaciones desde el mismo antecedente.

- Invocar una continuación cuando todas o una de las tareas antecedentes finalicen.

- Encadenar continuaciones una tras otra de cualquier longitud.

- Usar una continuación para controlar las excepciones producidas por el antecedente.

Estas características permiten ejecutar una o más tareas cuando la primera tarea se completa. Por ejemplo, puede crear una continuación que comprenda un archivo después de que la primera tarea lo lea desde el disco.

En el ejemplo siguiente se modifica el anterior para usar el método [concurrency::task::then](reference/task-class.md#then) para programar una continuación que imprime el valor de la tarea anterior cuando está disponible.

[!code-cpp[concrt-basic-continuation#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_5.cpp)]

Puede encadenar y anidar tareas de cualquier longitud. Una tarea también puede tener varias continuaciones. En el siguiente ejemplo se muestra una cadena de continuación básica que triplica el valor de la tarea anterior.

[!code-cpp[concrt-continuation-chain#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_6.cpp)]

Una continuación también puede devolver otra tarea. Si no hay ninguna cancelación, esta tarea se ejecuta antes de la continuación siguiente. Esta técnica se conoce como *desencapsulado asincrónico.* La desencapsulación asincrónica resulta útil cuando se quiere realizar un trabajo adicional en segundo plano sin que la tarea actual bloquee el subproceso actual. (Esto es común en las aplicaciones para UWP, donde las continuaciones se pueden ejecutar en el subproceso de interfaz de usuario). En el siguiente ejemplo se muestran tres tareas. La primera tarea devuelve otra tarea que se ejecuta antes de una tarea de continuación.

[!code-cpp[concrt-async-unwrapping#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_7.cpp)]

> [!IMPORTANT]
> Cuando una continuación de una tarea devuelve una tarea anidada de tipo `N`, la tarea resultante tiene el tipo `N` (no `task<N>`) y se completa cuando lo haga la tarea anidada. En otras palabras, la continuación realiza la desencapsulación de la tarea anidada.

## <a name="value-based-versus-task-based-continuations"></a><a name="value-versus-task"></a>Continuacións basadas en el valor frente a las basadas en tareas

Si tenemos un objeto `task` cuyo tipo de valor devuelto es `T`, se puede proporcionar un valor de tipo `T` o `task<T>` a las tareas de continuación. Una continuación que `T` toma el tipo se conoce como *continuación basada en valores*. Una continuación basada en valores está programada para ejecutarse cuando la tarea antecedente se completa sin errores y no se ha cancelado. Una continuación que `task<T>` toma el tipo como parámetro se conoce como *continuación basada en tareas.* Una continuación basada en tareas está programada siempre para ejecutarse cuando finaliza la tarea antecedente, aun cuando esta se cancele o genere una excepción. Tras ello, puede llamar a `task::get` para obtener el resultado de la tarea antecedente. Si se canceló la tarea `task::get` anterior, se produce [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md). Si la tarea antecedente produjo una excepción, `task::get` vuelve a producir esta excepción. Una continuación basada en tareas no se marca como cancelada cuando su tarea antecedente se cancela.

## <a name="composing-tasks"></a><a name="composing-tasks"></a>Tareas de composición

En esta sección se describen las funciones [concurrency::when_all](reference/concurrency-namespace-functions.md#when_all) y [concurrency::when_any,](reference/concurrency-namespace-functions.md#when_all) que pueden ayudarle a componer varias tareas para implementar patrones comunes.

### <a name="the-when_all-function"></a><a name="when-all"></a>La función when_all

La función `when_all` genera una tarea que finaliza después de que se complete un conjunto de tareas. Esta función devuelve un objeto[vectorial](../../standard-library/vector-class.md) std:: que contiene el resultado de cada tarea del conjunto. En el siguiente ejemplo básico se usa `when_all` para crear una tarea que representa la finalización de otras tres tareas.

[!code-cpp[concrt-join-tasks#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_8.cpp)]

> [!NOTE]
> Las tareas que se pasan a `when_all` tienen que ser uniformes. En otras palabras, todas tienen que devolver el mismo tipo.

También puede usar la sintaxis `&&` para crear una tarea que finalice cuando lo haga un conjunto de tareas, como se aprecia en el siguiente ejemplo.

`auto t = t1 && t2; // same as when_all`

Es habitual usar una continuación junto con `when_all` para realizar una acción después de que un conjunto de tareas finalice. En el siguiente ejemplo se modifica el ejemplo anterior con el propósito de imprimir la suma de tres tareas que generan un resultado `int` cada una.

[!code-cpp[concrt-join-tasks#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_9.cpp)]

En este ejemplo, también puede especificar `task<vector<int>>` para generar una continuación basada en tareas.

Si una tarea de un conjunto de tareas se cancela o genera una excepción, `when_all` se completa inmediatamente y no se espera a que las tareas restantes terminen. Si se produce una excepción, el Runtime volverá a producirla cuando se llame a `task::get` o a `task::wait` en el objeto de tarea que `when_all` devuelve. Si se produce una excepción en más de una tarea, el Runtime elige una de ellas. Por lo tanto, procure observar todas las excepciones después de que todas las tareas se hayan completado; una excepción de tarea no controlada hará que la aplicación finalice.

Esta es una función de utilidad que puede usar para asegurarse de que el programa observa todas las excepciones. Por cada tarea en el intervalo proporcionado, `observe_all_exceptions` desencadena cualquier excepción que se haya vuelto a producir y, luego, la pasa.

[!code-cpp[concrt-eh-when_all#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_10.cpp)]

Considera una aplicación para UWP que use C++ y XAML y escriba un conjunto de archivos en el disco. En el siguiente ejemplo se muestra cómo usar `when_all` y `observe_all_exceptions` para asegurarse de que el programa tiene presentes todas las excepciones.

[!code-cpp[concrt-eh-when_all#2](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_11.cpp)]

##### <a name="to-run-this-example"></a>Para ejecutar este ejemplo

1. En MainPage.xaml, agregue un control `Button`.

[!code-xml[concrt-eh-when_all#3](../../parallel/concrt/codesnippet/xaml/task-parallelism-concurrency-runtime_12.xaml)]

1. En MainPage.xaml.h, agregue estas declaraciones adelantadas a la sección `private` de la declaración de clase `MainPage`.

[!code-cpp[concrt-eh-when_all#4](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_13.h)]

1. En MainPage.xaml.cpp, implemente el controlador de eventos `Button_Click`.

[!code-cpp[concrt-eh-when_all#5](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_14.cpp)]

1. En MainPage.xaml.cpp, implemente `WriteFilesAsync` tal y como se muestra en el ejemplo.

> [!TIP]
> `when_all` es una función sin bloqueo que genera `task` como resultado. A diferencia de [task::wait](reference/task-class.md#wait), es seguro llamar a esta función en una aplicación para UWP en el subproceso ASTA (Application STA).

### <a name="the-when_any-function"></a><a name="when-any"></a>La función when_any

La función `when_any` genera una tarea que finaliza después de que lo haga la primera tarea de un conjunto de tareas. Esta función devuelve un objeto [std::pair](../../standard-library/pair-structure.md) que contiene el resultado de la tarea completada y el índice de esa tarea en el conjunto.

La función `when_any` es especialmente útil en los siguientes escenarios:

- Operaciones redundantes. Considere un algoritmo o una operación que pueda realizarse de muchas maneras. Puede usar la función `when_any` para seleccionar la operación que finaliza primero y, luego, cancelar las operaciones restantes.

- Operaciones intercaladas. Puede iniciar varias operaciones que tienen que finalizar en su totalidad y usar la función `when_any` para procesar los resultados cuando cada operación finalice. Finalizada una operación, puede iniciar una o más tareas adicionales.

- Operaciones limitadas. Puede usar la función `when_any` para ampliar el escenario anterior limitando el número de operaciones simultáneas.

- Operaciones que han expirado. Puede usar la función `when_any` para seleccionar entre una o más tareas y una tarea que finaliza después de una hora específica.

Al igual que `when_all`, es habitual usar una continuación que tiene `when_any` para realizar una acción al finalizar la primera tarea de un conjunto de tareas. En el siguiente ejemplo básico se usa `when_any` para crear una tarea que se completa cuando lo hace la primera de otras tres tareas.

[!code-cpp[concrt-select-task#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_15.cpp)]

En este ejemplo, también puede especificar `task<pair<int, size_t>>` para generar una continuación basada en tareas.

> [!NOTE]
> Al igual que `when_all`, todas las tareas que se pasan a `when_any` tienen que devolver el mismo tipo.

También puede usar la sintaxis `||` para crear una tarea que finalice cuando lo haga la primera tarea de un conjunto de tareas, como se aprecia en el siguiente ejemplo.

`auto t = t1 || t2; // same as when_any`

> [!TIP]
> Al `when_all`igual `when_any` que con , no es bloqueo y es seguro llamar a una aplicación para UWP en el subproceso ASTA.

## <a name="delayed-task-execution"></a><a name="delayed-tasks"></a>Ejecución de tareas retrasadas

Hay veces que es necesario retrasar la ejecución de una tarea hasta que se satisfaga una condición, o iniciar una tarea en respuesta a un evento externo. Por ejemplo, en una programación asincrónica, puede que tenga que iniciar una tarea en respuesta a un evento de finalización de E/S.

Dos maneras de lograr esto son usar una continuación o iniciar una tarea y esperar un evento dentro de la función de trabajo de la tarea. Sin embargo, hay casos en los que no es posible recurrir a una de estas técnicas. Por ejemplo, para crear una continuación, hay que tener la tarea antecedente. Sin embargo, si no tiene la tarea anterior, puede crear un evento de *finalización* de tarea y, posteriormente, encadenar ese evento de finalización a la tarea anterior cuando esté disponible. Además, como una tarea en espera también bloquea un subproceso, puede usar eventos de finalización de tarea para realizar el trabajo cuando una operación asincrónica se complete y, de este modo, liberar un subproceso.

La clase [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) ayuda a simplificar dicha composición de tareas. Al igual que la clase `task`, el parámetro de tipo `T` es el tipo del resultado que la tarea genera. Este tipo puede ser `void` si la tarea no devuelve un valor. `T` no puede usar el modificador `const`. Normalmente, se proporciona un objeto `task_completion_event` a un subproceso o una tarea que indicará el momento en el que el valor esté disponible. Al mismo tiempo, se establecen una o varias tareas como agentes de escucha de ese evento. Cuando se establece el evento, las tareas de agente de escucha finalizan y sus continuaciones se programan para ejecutarse.

Para obtener un `task_completion_event` ejemplo que se usa para implementar una tarea que se completa después de un retraso, vea [Cómo: crear una tarea que se complete después](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)de un retraso .

## <a name="task-groups"></a><a name="task-groups"></a>Grupos de tareas

Un grupo de *tareas* organiza una colección de tareas. Los grupos de tareas envían tareas a una cola de robo de trabajo. El programador quita las tareas de esta cola y las ejecuta en los recursos informáticos disponibles. Después de agregar tareas a un grupo de tareas, puede esperar a que todas las tareas finalicen o cancelar las tareas que aún no se han iniciado.

La PPL usa las clases [concurrency::task_group](reference/task-group-class.md) y [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) para representar grupos de tareas y la clase [concurrency::task_handle](../../parallel/concrt/reference/task-handle-class.md) para representar las tareas que se ejecutan en estos grupos. La clase `task_handle` encapsula el código que realiza el trabajo. Al igual que la clase `task`, la función de trabajo tiene la forma de una función lambda, un puntero de función o un objeto de función. Normalmente no es necesario trabajar con objetos `task_handle` directamente. En su lugar, se pasan funciones de trabajo a un grupo de tareas y el grupo de tareas crea y administra los objetos `task_handle`.

La PPL divide los grupos de tareas en estas dos categorías: grupos de *tareas no estructurados* y grupos de *tareas estructurados.* La biblioteca PPL usa la clase `task_group` para representar grupos de tareas sin estructura y la clase `structured_task_group` para representar grupos de tareas con estructura.

> [!IMPORTANT]
> La PPL también define el algoritmo [concurrency::parallel_invoke,](reference/concurrency-namespace-functions.md#parallel_invoke) que utiliza la `structured_task_group` clase para ejecutar un conjunto de tareas en paralelo. Como el algoritmo `parallel_invoke` tiene una sintaxis más concisa, recomendamos usarlo en lugar de la clase `structured_task_group` siempre que sea posible. El tema [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md) `parallel_invoke` describe con más detalle.

Use `parallel_invoke` cuando tenga varias tareas independientes que quiere ejecutar al mismo tiempo y tenga que esperar a que todas las tareas finalicen antes de continuar. Esta técnica se conoce a menudo como *horquilla y unión* de paralelismo. Use `task_group` cuando tenga varias tareas independientes que quiere ejecutar al mismo tiempo, pero quiera esperar a que las tareas finalicen más adelante. Por ejemplo, puede agregar tareas a un objeto `task_group` y esperar a que las tareas finalicen en otra función o desde otro subproceso.

Los grupos de tareas admiten el concepto de cancelación. Con la cancelación puede indicar a todas las tareas activas que quiere cancelar la operación global. De igual modo, las cancelaciones evitan que se inicien las tareas que aún no han empezado. Para obtener más información acerca de la cancelación, consulte [Cancelación en la PPL](cancellation-in-the-ppl.md).

El Runtime también proporciona un modelo de control de excepciones que permite generar una excepción desde una tarea y controlar esa excepción mientras espera a que el grupo de tareas asociado finalice. Para obtener más información acerca de este modelo de control de excepciones, vea Control de [excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="comparing-task_group-to-structured_task_group"></a><a name="comparing-groups"></a>Comparación de task_group con structured_task_group

Aunque recomendamos usar `task_group` o `parallel_invoke` en lugar de la clase `structured_task_group`, hay casos donde probablemente prefiera usar `structured_task_group`, por ejemplo, al escribir un algoritmo paralelo que realiza un número variable de tareas o que requiere compatibilidad con la cancelación. En esta sección se explican las diferencias entre las clases `task_group` y `structured_task_group`.

La clase `task_group` es segura para la ejecución de subprocesos. Por lo tanto, puede agregar tareas a un objeto `task_group` desde varios subprocesos y esperar o cancelar un objeto `task_group` desde varios subprocesos. Es necesario que la construcción y destrucción de un objeto `structured_task_group` ocurran en el mismo ámbito léxico. Además, todas las operaciones en un objeto `structured_task_group` tienen que producirse en el mismo subproceso. La excepción a esta regla es los métodos [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) y [concurrency::structured_task_group::is_canceling.](reference/structured-task-group-class.md#is_canceling) Una tarea secundaria puede llamar a estos métodos para cancelar el grupo de tareas primario y buscar la cancelación en cualquier momento.

Puede ejecutar tareas adicionales `task_group` en un objeto después de llamar al método [concurrency::task_group::wait](reference/task-group-class.md#wait) o [concurrency::task_group::run_and_wait.](reference/task-group-class.md#run_and_wait) Por el contrario, si ejecuta `structured_task_group` tareas adicionales en un objeto después de llamar a los métodos [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait) o [concurrency::structured_task_group:run_and_wait,](reference/structured-task-group-class.md#run_and_wait) el comportamiento es indefinido.

La clase `structured_task_group` no se sincroniza entre subprocesos, de modo que tiene menos sobrecarga de ejecución que la clase `task_group`. Por lo tanto, si su problema no requiere programar el trabajo desde varios subprocesos y no puede usar el algoritmo `parallel_invoke`, la clase `structured_task_group` le ayudará a escribir código con mejor rendimiento.

Si usa un objeto `structured_task_group` dentro de otro objeto `structured_task_group`, el objeto interno debe finalizar y destruirse antes de que el objeto externo finalice. La clase `task_group` no requiere que los grupos de tareas anidadas finalicen antes de que finalice el grupo externo.

Los grupos de tareas con y sin estructura funcionan con identificadores de tareas de distinta forma. Se pueden pasar funciones de trabajo directamente a un objeto `task_group`; el objeto `task_group` creará y administrará el identificador de tarea automáticamente. La clase `structured_task_group` requiere que se administre un objeto `task_handle` por cada tarea. Cada objeto `task_handle` tiene que ser válido a lo largo de toda la duración del objeto `structured_task_group` asociado. Utilice la función [concurrency::make_task](reference/concurrency-namespace-functions.md#make_task) para crear un `task_handle` objeto, como se muestra en el siguiente ejemplo básico:

[!code-cpp[concrt-make-task-structure#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_16.cpp)]

Para administrar identificadores de tareas para casos en los que tiene un número variable de tareas, utilice una rutina de asignación de pila como [_malloca](../../c-runtime-library/reference/malloca.md) o una clase contenedora, como std::[vector](../../standard-library/vector-class.md).

Tanto `task_group` como `structured_task_group` admiten la cancelación. Para obtener más información acerca de la cancelación, consulte [Cancelación en la PPL](cancellation-in-the-ppl.md).

## <a name="example"></a><a name="example"></a>Ejemplo

En el siguiente ejemplo básico se indica cómo trabajar con grupos de tareas. En él se usa el algoritmo `parallel_invoke` para realizar dos tareas simultáneamente. Cada tarea agrega subtareas a un objeto `task_group`. Tenga en cuenta que la clase `task_group` permite que varias tareas agreguen tareas al objeto al mismo tiempo.

[!code-cpp[concrt-using-task-groups#1](../../parallel/concrt/codesnippet/cpp/task-parallelism-concurrency-runtime_17.cpp)]

Aquí mostramos la salida de muestra de este ejemplo:

```Output
Message from task: Hello
Message from task: 3.14
Message from task: 42
```

El algoritmo `parallel_invoke` ejecuta tareas de forma simultánea, por lo que el orden de los mensajes de salida podría variar.

Para obtener ejemplos completos `parallel_invoke` que muestran cómo utilizar el algoritmo, vea [Cómo: Usar parallel_invoke para escribir una rutina](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) de ordenación paralela y [Cómo: usar parallel_invoke para ejecutar operaciones paralelas](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md). Para obtener un ejemplo `task_group` completo que usa la clase para implementar futuros asincrónicos, vea [Tutorial: Implementación](../../parallel/concrt/walkthrough-implementing-futures.md)de futuros .

## <a name="robust-programming"></a><a name="robust"></a>Programación robusta

Asegúrese de que comprende el rol de cancelación y control de excepciones cuando use tareas, grupos de tareas y algoritmos paralelos. Por ejemplo, en un árbol de trabajo paralelo, una tarea que se cancela impide que se ejecuten las tareas secundarias. Esto puede causar problemas si una de las tareas secundarias realiza una operación que tiene importancia para la aplicación, como liberar un recurso. Además, si una tarea secundaria genera una excepción, esta podría propagarse a través de un destructor de objetos y provocar un comportamiento no definido en la aplicación. Para obtener un ejemplo que ilustra estos puntos, vea la sección Comprender cómo la cancelación y el control de [excepciones afectan a](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) la destrucción de objetos en el documento Prácticas recomendadas de la biblioteca de patrones paralelos. Para obtener más información acerca de los modelos de cancelación y control de excepciones en la PPL, vea [Anulación](../../parallel/concrt/cancellation-in-the-ppl.md) y control de [excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Cómo: Usar parallel.invoke para escribir una rutina de ordenación en paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Muestra cómo usar el algoritmo `parallel_invoke` para mejorar el rendimiento del algoritmo de ordenación bitónica.|
|[Cómo: Usar parallel_invoke para ejecutar operaciones paralelas](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Muestra cómo usar el algoritmo `parallel_invoke` para mejorar el rendimiento de un programa que realiza varias operaciones en un origen de datos compartido.|
|[Cómo: Crear una tarea que se complete después de un retardo](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Muestra cómo utilizar `task` `cancellation_token_source`las `cancellation_token`clases , , , y `task_completion_event` para crear una tarea que se completa después de un retraso.|
|[Tutorial: Implementar futuros](../../parallel/concrt/walkthrough-implementing-futures.md)|Muestra cómo combinar la funcionalidad existente en el Runtime de simultaneidad para ampliar capacidades.|
|[Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Describe la biblioteca PPL, que proporciona un modelo de programación imperativo para desarrollar aplicaciones simultáneas.|

## <a name="reference"></a>Referencia

[Clase de tarea (Runtime de simultaneidad)](../../parallel/concrt/reference/task-class.md)

[Clase task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md)

[when_all (Función)](reference/concurrency-namespace-functions.md#when_all)

[when_any (función)](reference/concurrency-namespace-functions.md#when_any)

[Clase task_group](reference/task-group-class.md)

[parallel_invoke (Función)](reference/concurrency-namespace-functions.md#parallel_invoke)

[Clase structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md)
