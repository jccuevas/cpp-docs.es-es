---
title: Bloques de mensajes asincrónicos
ms.date: 11/04/2016
helpviewer_keywords:
- non-greedy join [Concurrency Runtime]
- asynchronous message blocks
- greedy join [Concurrency Runtime]
ms.assetid: 79c456c0-1692-480c-bb67-98f2434c1252
ms.openlocfilehash: ef6f6f56a82cc76c2c270817ed40d15418960dc1
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141955"
---
# <a name="asynchronous-message-blocks"></a>Bloques de mensajes asincrónicos

La Biblioteca de agentes proporciona varios tipos de bloques de mensajes que permiten propagar mensajes entre los componentes de aplicación de una manera segura para subprocesos. Estos tipos de bloques de mensajes se usan a menudo con las distintas rutinas de paso de mensajes, como [Concurrency:: Send](reference/concurrency-namespace-functions.md#send), [Concurrency:: Asend](reference/concurrency-namespace-functions.md#asend), [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive)y [Concurrency:: try_receive](reference/concurrency-namespace-functions.md#try_receive). Para obtener más información sobre las rutinas de paso de mensajes definidas por la biblioteca de agentes, vea [funciones de paso de mensajes](../../parallel/concrt/message-passing-functions.md).

## <a name="top"></a> Secciones

Este tema contiene las siguientes secciones:

- [Orígenes y destinos](#sources_and_targets)

- [Propagación de mensajes](#propagation)

- [Información general de los tipos de bloques de mensajes](#overview)

- [unbounded_buffer (clase)](#unbounded_buffer)

- [overwrite_buffer (clase)](#overwrite_buffer)

- [single_assignment (clase)](#single_assignment)

- [call (clase)](#call)

- [transformer (clase)](#transformer)

- [choice (clase)](#choice)

- [Clases join y multitype_join](#join)

- [timer (clase)](#timer)

- [Filtrado de mensajes](#filtering)

- [Reserva de mensajes](#reservation)

## <a name="sources_and_targets"></a>Orígenes y destinos

Los orígenes y los destinos son dos participantes importantes en el paso de mensajes. Un *origen* hace referencia a un extremo de comunicación que envía mensajes. Un *destino* hace referencia a un extremo de comunicación que recibe los mensajes. Puede considerar el origen como un extremo del que se lee y el destino como un extremo en el que se escribe. Las aplicaciones conectan los orígenes y destinos para formar *redes de mensajería*.

La biblioteca de agentes usa dos clases abstractas para representar orígenes y destinos: [Concurrency:: ISource](../../parallel/concrt/reference/isource-class.md) y [Concurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md). Los tipos de bloques de mensajes que actúan como orígenes derivan de `ISource`; los tipos de bloques de mensajes que actúan como destinos derivan de `ITarget`. Los tipos de bloques de mensajes que actúan como orígenes y destinos derivan de `ISource` y de `ITarget`.

[[Arriba](#top)]

## <a name="propagation"></a>Propagación de mensajes

La *propagación de mensajes* es el acto de enviar un mensaje de un componente a otro. Cuando se ofrece un mensaje a un bloque de mensajes, este puede aceptar, rechazar o posponer ese mensaje. Cada tipo de bloque de mensajes almacena y transmite mensajes de maneras diferentes. Por ejemplo, la clase `unbounded_buffer` almacena un número ilimitado de mensajes, la clase `overwrite_buffer` almacena un único mensaje cada vez y la clase transformer almacena una versión modificada de cada mensaje. Estos tipos de bloques de mensajes se describen con más detalle más adelante en este documento.

Cuando un bloque de mensajes acepta un mensaje, puede realizar opcionalmente trabajo y, si el bloque de mensajes es un origen, pasar el mensaje resultante a otro miembro de la red. Un bloque de mensajes puede usar una función de filtro para rechazar los mensajes que no desea recibir. Los filtros se describen con más detalle más adelante en este tema, en la sección [filtrado de mensajes](#filtering). Un bloque de mensajes que pospone un mensaje puede reservar ese mensaje y usarlo posteriormente. La reserva de mensajes se describe con más detalle más adelante en este tema, en la sección [reserva de mensajes](#reservation).

La Biblioteca de agentes permite a los bloques de mensajes pasar mensajes de forma sincrónica o asincrónica. Cuando se pasa un mensaje a un bloque de mensajes sincrónicamente, por ejemplo mediante la función `send`, el runtime bloquea el contexto actual hasta que el bloque de destino acepta o rechaza el mensaje. Cuando se pasa un mensaje a un bloque de mensajes asincrónicamente, por ejemplo mediante la función `asend`, el runtime ofrece el mensaje al destino, y si el destino acepta el mensaje, el runtime programa una tarea asincrónica que propaga el mensaje al receptor. El runtime usa tareas ligeras para propagar mensajes de manera cooperativa. Para obtener más información sobre las tareas ligeras, vea [programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Las aplicaciones conectan los orígenes y los destinos entre sí para formar redes de mensajería. Normalmente, se enlaza la red y se llama a `send` o `asend` para pasar datos a la red. Para conectar un bloque de mensajes de origen a un destino, llame al método [Concurrency:: ISource:: link_target](reference/isource-class.md#link_target) . Para desconectar un bloque de origen de un destino, llame al método [Concurrency:: ISource:: unlink_target](reference/isource-class.md#unlink_target) . Para desconectar un bloque de origen de todos sus destinos, llame al método [Concurrency:: ISource:: unlink_targets](reference/isource-class.md#unlink_targets) . Cuando uno de los tipos de bloques de mensajes predefinido abandona el ámbito o se destruye, se desconecta automáticamente a sí mismo de cualquier bloque de destino. Algunos tipos de bloques de mensajes limitan el número máximo de destinos en los que pueden escribir. En la próxima sección se describen las restricciones que se aplican a los tipos predefinidos de bloques de mensajes.

[[Arriba](#top)]

## <a name="overview"></a>Información general de los tipos de bloques de mensajes

En la siguiente tabla se describe brevemente el rol de los tipos de bloques de mensajes.

[unbounded_buffer](#unbounded_buffer)<br/>
Almacena una cola de mensajes.

[overwrite_buffer](#overwrite_buffer)<br/>
Almacena un mensaje en el que se puede escribir y del que se puede leer varias veces.

[single_assignment](#single_assignment)<br/>
Almacena un mensaje en el que se puede escribir una vez y del que se puede leer varias veces.

[llama](#call)<br/>
Realiza trabajo cuando recibe un mensaje.

[transformador](#transformer)<br/>
Realiza trabajo cuando recibe datos y envía el resultado de ese trabajo a otro bloque de destino. La clase `transformer` puede actuar en diferentes tipos de entrada y salida.

[alternativa](#choice)<br/>
Selecciona el primer mensaje disponible en un conjunto de orígenes.

[join y combinación multitipo](#join)<br/>
Esperan por todos los mensajes que se van a recibir de un conjunto de orígenes y, a continuación, combinan los mensajes en un mensaje para otro bloque de mensajes.

[temporizador](#timer)<br/>
Envía un mensaje a un bloque de destino de manera periódica.

Estos tipos de bloques de mensajes tienen diferentes características que los hacen útiles en distintas situaciones. A continuación se indican algunas de estas características:

- *Tipo de propagación*: indica si el bloque de mensajes actúa como origen de datos, receptor de datos o ambos.

- *Ordenación de mensajes*: indica si el bloque de mensajes mantiene el orden original en el que se envían o reciben los mensajes. Cada tipo de bloque de mensajes predefinido mantiene el orden original en el que envía o recibe los mensajes.

- *Recuento*de orígenes: número máximo de orígenes de los que puede leer el bloque de mensajes.

- *Recuento de destino*: el número máximo de destinos en los que puede escribir el bloque de mensajes.

En la siguiente tabla se muestra cómo se relacionan estas características con los diferentes tipos de bloques de mensajes.

|Tipo de bloque de mensajes|Tipo de propagación (origen, destino, ambos)|Orden de mensajes (ordenado o no ordenado)|Recuento de orígenes|Recuento de destinos|
|------------------------|--------------------------------------------------|-----------------------------------------------|------------------|------------------|
|`unbounded_buffer`|Ambos|Ordered (Realizado)|Sin enlazar|Sin enlazar|
|`overwrite_buffer`|Ambos|Ordered (Realizado)|Sin enlazar|Sin enlazar|
|`single_assignment`|Ambos|Ordered (Realizado)|Sin enlazar|Sin enlazar|
|`call`|Destino|Ordered (Realizado)|Sin enlazar|No aplicable|
|`transformer`|Ambos|Ordered (Realizado)|Sin enlazar|1|
|`choice`|Ambos|Ordered (Realizado)|10|1|
|`join`|Ambos|Ordered (Realizado)|Sin enlazar|1|
|`multitype_join`|Ambos|Ordered (Realizado)|10|1|
|`timer`|Source|No aplicable|No aplicable|1|

En las secciones siguientes se describen los tipos de bloques de mensajes con más detalle.

[[Arriba](#top)]

## <a name="unbounded_buffer"></a>unbounded_buffer (clase)

La clase [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) representa una estructura de mensajería asincrónica de uso general. Esta clase almacena una cola FIFO (primero en entrar, primero en salir) de mensajes donde varios orígenes pueden escribir o de los que varios destinos pueden leer. Cuando un destino recibe un mensaje de un objeto `unbounded_buffer`, ese mensaje se quita de la cola de mensajes. Por tanto, aunque un objeto `unbounded_buffer` puede tener varios destinos, solo uno recibirá cada mensaje. La clase `unbounded_buffer` resulta útil si desea pasar varios mensajes a otro componente, y ese componente debe recibir cada mensaje.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra la estructura básica de cómo trabajar con la clase `unbounded_buffer`. En este ejemplo se envían tres valores a un objeto `unbounded_buffer` y, a continuación, se vuelven a leer esos valores del mismo objeto.

[!code-cpp[concrt-unbounded_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_1.cpp)]

En este ejemplo se produce la siguiente salida:

```Output
334455
```

Para obtener un ejemplo completo que muestra cómo usar la clase `unbounded_buffer`, consulte [Cómo: implementar varios modelos productor-consumidor](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).

[[Arriba](#top)]

## <a name="overwrite_buffer"></a>overwrite_buffer (clase)

La clase [Concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) es similar a la clase `unbounded_buffer`, salvo que un objeto `overwrite_buffer` solo almacena un mensaje. Además, cuando un destino recibe un mensaje de un objeto `overwrite_buffer`, ese mensaje no se quita del búfer. Por tanto, varios destinos reciben una copia del mensaje.

La clase `overwrite_buffer` resulta útil si desea pasar varios mensajes a otro componente, pero este componente solo necesita el valor más reciente. Esta clase también resulta útil si desea difundir un mensaje a varios componentes.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra la estructura básica de cómo trabajar con la clase `overwrite_buffer`. En este ejemplo se envían tres valores a un objeto `overwrite _buffer` y, a continuación, se lee valor actual del mismo objeto tres veces. Este ejemplo es similar al ejemplo de la clase `unbounded_buffer`. Sin embargo, la clase `overwrite_buffer` solo almacena un mensaje. Además, el runtime no quita el mensaje de un objeto `overwrite_buffer` después de leerlo.

[!code-cpp[concrt-overwrite_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_2.cpp)]

En este ejemplo se produce la siguiente salida:

```Output
555555
```

Para obtener un ejemplo completo que muestra cómo usar la clase `overwrite_buffer`, consulte [Cómo: implementar varios modelos productor-consumidor](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).

[[Arriba](#top)]

## <a name="single_assignment"></a>single_assignment (clase)

La clase [Concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) es similar a la clase `overwrite_buffer`, salvo que un objeto `single_assignment` solo se puede escribir en una vez. Al igual que la clase `overwrite_buffer`, cuando un destino recibe un mensaje de un objeto `single_assignment`, el mensaje no se quita de dicho objeto. Por tanto, varios destinos reciben una copia del mensaje. La clase `single_assignment` resulta útil si desea difundir un mensaje a varios componentes.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra la estructura básica de cómo trabajar con la clase `single_assignment`. En este ejemplo se envían tres valores a un objeto `single_assignment` y, a continuación, se lee valor actual del mismo objeto tres veces. Este ejemplo es similar al ejemplo de la clase `overwrite_buffer`. Aunque las clases `overwrite_buffer` y `single_assignment` almacenan un único mensaje, solo se puede escribir una vez en la clase `single_assignment`.

[!code-cpp[concrt-single_assignment-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_3.cpp)]

En este ejemplo se produce la siguiente salida:

```Output
333333
```

Para obtener un ejemplo completo que muestra cómo usar la clase `single_assignment`, vea [Tutorial: implementar futuros](../../parallel/concrt/walkthrough-implementing-futures.md).

[[Arriba](#top)]

## <a name="call"></a>Call (clase)

La clase [Concurrency:: Call](../../parallel/concrt/reference/call-class.md) actúa como un receptor de mensajes que realiza una función de trabajo cuando recibe datos. Esta función de trabajo puede ser una expresión lambda, un objeto de función o un puntero a una función. Un objeto `call` se comporta de manera diferente que una llamada de función ordinaria, ya que actúa en paralelo con otros componentes que le envían mensajes. Si un objeto `call` está realizando trabajo cuando recibe un mensaje, agrega ese mensaje a una cola. Cada objeto `call` procesa los mensajes en cola en el orden en el que se recibieron.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra la estructura básica de cómo trabajar con la clase `call`. En este ejemplo se crea un objeto `call` que imprime en la consola cada valor que recibe. A continuación se envían tres valores al objeto `call`. Dado que el objeto `call` procesa los mensajes en un subproceso independiente, en este ejemplo también se usa una variable de contador y un objeto de [evento](../../parallel/concrt/reference/event-class.md) para asegurarse de que el objeto `call` procesa todos los mensajes antes de que se devuelva la función `wmain`.

[!code-cpp[concrt-call-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_4.cpp)]

En este ejemplo se produce la siguiente salida:

```Output
334455
```

Para obtener un ejemplo completo que muestra cómo usar la clase `call`, vea [Cómo: proporcionar funciones de trabajo a las clases Call y Transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md).

[[Arriba](#top)]

## <a name="transformer"></a>Clase Transformer

La clase [Concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) actúa como receptor del mensaje y como remitente del mensaje. La clase `transformer` es similar a la clase `call`, ya que realiza una función de trabajo definida por el usuario cuando recibe datos. Sin embargo, la clase `transformer` también envía el resultado de la función de trabajo a objetos receptores. Al igual que un objeto `call`, el objeto `transformer` actúa en paralelo con otros componentes que le envían mensajes. Si un objeto `transformer` está realizando trabajo cuando recibe un mensaje, agrega ese mensaje a una cola. Cada objeto `transformer` procesa sus mensajes en cola en el orden en el que se recibieron.

La clase `transformer` envía su mensaje a un único destino. Si establece el parámetro `_PTarget` en el constructor en `NULL`, puede especificar posteriormente el destino llamando al método [Concurrency:: link_target](reference/source-block-class.md#link_target) .

A diferencia de los demás tipos de bloques de mensajes asincrónicos que proporciona la Biblioteca de agentes, la clase `transformer` puede actuar en tipos de entrada y salida diferentes. Esta capacidad de transformar los datos de un tipo a otro convierte a la clase `transformer` en un componente clave en muchas redes simultáneas. Además, puede agregar funcionalidad paralela más específica en la función de trabajo de un objeto `transformer`.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra la estructura básica de cómo trabajar con la clase `transformer`. En este ejemplo se crea un objeto `transformer` que multiplica cada valor `int` de entrada por 0.33 para generar un valor `double` como resultado. A continuación se recibe los valores transformados del mismo objeto `transformer` y se imprimen en la consola.

[!code-cpp[concrt-transformer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_5.cpp)]

En este ejemplo se produce la siguiente salida:

```Output
10.8914.5218.15
```

Para obtener un ejemplo completo en el que se muestra cómo usar la clase `transformer`, vea [Cómo: usar Transformer en una canalización de datos](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).

[[Arriba](#top)]

## <a name="choice"></a>Choice (clase)

La clase [Concurrency:: Choice](../../parallel/concrt/reference/choice-class.md) selecciona el primer mensaje disponible de un conjunto de orígenes. La clase `choice` representa un mecanismo de flujo de control en lugar de un mecanismo de flujo de entrada (el tema [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) describe las diferencias entre el flujo de bits y el flujo de control).

La lectura de un objeto choice es similar a la llamada a la función `WaitForMultipleObjects` de la API de Windows cuando su parámetro `bWaitAll` está establecido en `FALSE`. Sin embargo, la clase `choice` enlaza los datos al propio evento en lugar de enlazarlos a un objeto de sincronización externo.

Normalmente, se usa la clase `choice` junto con la función [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) para impulsar el flujo de control en la aplicación. Utilice la clase `choice` si debe seleccionar entre búferes de mensajes con tipos diferentes. Utilice la clase `single_assignment` si debe seleccionar entre búferes de mensajes con el mismo tipo.

El orden en el que vincula los orígenes a un objeto `choice` es importante porque puede determinar qué mensaje se selecciona. Por ejemplo, supongamos que vincula varios búferes de mensajes que ya contienen un mensaje a un objeto `choice`. El objeto `choice` selecciona el mensaje del primer origen al que está vinculado. Después de vincular todos los orígenes, el objeto `choice` conserva el orden en el que cada origen recibe un mensaje.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra la estructura básica de cómo trabajar con la clase `choice`. En este ejemplo se usa la función [Concurrency:: make_choice](reference/concurrency-namespace-functions.md#make_choice) para crear un objeto `choice` que seleccione entre tres bloques de mensajes. A continuación se calculan varios números de Fibonacci y se almacena cada resultado en un bloque de mensajes diferente. Después, se imprime en la consola un mensaje basándose en la operación que finalizó primero.

[!code-cpp[concrt-choice-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_6.cpp)]

Este ejemplo genera la siguiente salida de ejemplo:

```Output
fib35 received its value first. Result = 9227465
```

Dado que la tarea que calcula el número<sup>de Fibonacci 35</sup> no se garantiza que finalice en primer lugar, el resultado de este ejemplo puede variar.

En este ejemplo se usa el algoritmo [Concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) para calcular los números de Fibonacci en paralelo. Para obtener más información acerca de `parallel_invoke`, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).

Para obtener un ejemplo completo que muestra cómo usar la clase `choice`, consulte [Cómo: seleccionar entre tareas completadas](../../parallel/concrt/how-to-select-among-completed-tasks.md).

[[Arriba](#top)]

## <a name="join"></a>Clases join y multitype_join

Las clases [Concurrency:: join](../../parallel/concrt/reference/join-class.md) y [Concurrency:: multitype_join](../../parallel/concrt/reference/multitype-join-class.md) permiten esperar a que cada miembro de un conjunto de orígenes reciban un mensaje. La clase `join` actúa en los objetos de origen que tienen un tipo de mensaje común. La clase `multitype_join` actúa en los objetos de origen que pueden tener diferentes tipos de mensaje.

La lectura de un objeto `join` o `multitype_join` es similar a la llamada a la función `WaitForMultipleObjects` de la API de Windows cuando su parámetro `bWaitAll` está establecido en `TRUE`. Sin embargo, al igual que en el objeto `choice`, los objetos `join` y `multitype_join` usan un mecanismo de evento que enlaza los datos al propio evento en lugar de enlazarlos a un objeto de sincronización externo.

La lectura de un objeto `join` genera un objeto STD::[Vector](../../standard-library/vector-class.md) . La lectura de un objeto `multitype_join` genera un objeto STD::[Tuple](../../standard-library/tuple-class.md) . Los elementos aparecen en estos objetos en el mismo orden en que sus búferes de origen correspondientes se vinculan al objeto `join` o `multitype_join`. Como el orden en que vincula los búferes de origen a un objeto `join` o `multitype_join` está asociado con el orden de los elementos en el objeto `vector` o `tuple` resultante, se recomienda no desenlaza un búfer de origen existente de una unión. Si lo hace, puede producir un comportamiento no especificado.

### <a name="greedy-versus-non-greedy-joins"></a>Uniones expansivas y no expansivas

Las clases `join` y `multitype_join` admiten el concepto de uniones expansivas y no expansivas. Una *combinación expansiva* acepta un mensaje de cada uno de sus orígenes a medida que los mensajes están disponibles hasta que todos los mensajes están disponibles. Una *Unión no expansiva* recibe mensajes en dos fases. En primer lugar, una unión no expansiva espera hasta que cada uno de sus orígenes le ofrece un mensaje. En segundo lugar, después de que todos los mensajes de origen están disponibles, una unión no expansiva intenta reservar cada uno de esos mensajes. Si puede reservar cada mensaje, usa todos los mensajes y los propaga a su destino. De lo contrario, libera, o cancela, las reservas de mensajes y espera otra vez a que cada origen reciba un mensaje.

Las uniones expansivas funcionan mejor que las uniones no expansivas porque aceptan los mensajes de manera inmediata. Sin embargo, en raras ocasiones, las uniones expansivas pueden producir interbloqueos. Utilice una unión no expansiva si cuenta con varias uniones que contienen uno o más objetos de origen compartidos.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra la estructura básica de cómo trabajar con la clase `join`. En este ejemplo se usa la función [Concurrency:: make_join](reference/concurrency-namespace-functions.md#make_join) para crear un objeto `join` que recibe de tres objetos `single_assignment`. En este ejemplo se calculan diversos números de Fibonacci, se almacena cada resultado en un objeto `single_assignment` diferente y, a continuación, se imprime en la consola cada resultado que el objeto `join` almacena. Este ejemplo es similar al ejemplo de la clase `choice`, excepto en que la clase `join` espera a que todos los bloques de mensajes de origen reciban un mensaje.

[!code-cpp[concrt-join-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_7.cpp)]

En este ejemplo se produce la siguiente salida:

```Output
fib35 = 9227465fib37 = 24157817half_of_fib42 = 1.33957e+008
```

En este ejemplo se usa el algoritmo [Concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) para calcular los números de Fibonacci en paralelo. Para obtener más información acerca de `parallel_invoke`, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).

Para obtener ejemplos completos que muestran cómo usar la clase `join`, consulte [Cómo: seleccionar entre tareas completadas](../../parallel/concrt/how-to-select-among-completed-tasks.md) y [Tutorial: usar la combinación para evitar el interbloqueo](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).

[[Arriba](#top)]

## <a name="timer"></a>Timer (clase)

La clase Concurrency::[Timer](../../parallel/concrt/reference/timer-class.md) actúa como origen del mensaje. Un objeto `timer` envía un mensaje a un destino una vez transcurrido un período de tiempo especificado. La clase `timer` resulta útil si debe retrasar el envío de un mensaje o si desea enviar un mensaje de manera periódica.

La clase `timer` envía su mensaje a un único destino. Si establece el parámetro `_PTarget` en el constructor en `NULL`, puede especificar posteriormente el destino llamando al método [Concurrency:: ISource:: link_target](reference/source-block-class.md#link_target) .

Un objeto `timer` puede ser repetitivo o no repetitivo. Para crear un temporizador repetitivo, pase **true** para el parámetro `_Repeating` al llamar al constructor. De lo contrario, pase **false** para el parámetro `_Repeating` para crear un temporizador no repetitivo. Si el temporizador es repetitivo, envía el mismo mensaje a su destino después de cada intervalo.

La Biblioteca de agentes crea los objetos `timer` en el estado no iniciado. Para iniciar un objeto de temporizador, llame al método [Concurrency:: Timer:: Start](reference/timer-class.md#start) . Para detener un objeto `timer`, destruya el objeto o llame al método [Concurrency:: Timer:: Stop](reference/timer-class.md#stop) . Para pausar un temporizador repetitivo, llame al método [Concurrency:: Timer::p ause](reference/timer-class.md#pause) .

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra la estructura básica de cómo trabajar con la clase `timer`. En el ejemplo se usan objetos `timer` y `call` para informar sobre el progreso de una operación larga.

[!code-cpp[concrt-timer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_8.cpp)]

Este ejemplo genera la siguiente salida de ejemplo:

```Output
Computing fib(42)..................................................result is 267914296
```

Para obtener un ejemplo completo que muestra cómo usar la clase `timer`, consulte [Cómo: enviar un mensaje a intervalos regulares](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md).

[[Arriba](#top)]

## <a name="filtering"></a>Filtrado de mensajes

Cuando se crea un objeto de bloque de mensajes, se puede proporcionar una *función de filtro* que determina si el bloque de mensajes acepta o rechaza un mensaje. Una función de filtro resulta útil para garantizar que un bloque de mensajes recibe solo ciertos valores.

En el ejemplo siguiente se muestra cómo crear un objeto `unbounded_buffer` que usa una función de filtro para aceptar solo números pares. El objeto `unbounded_buffer` rechaza los números impares y, por tanto, no propaga números impares a sus bloques de destino.

[!code-cpp[concrt-filter-function#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_9.cpp)]

En este ejemplo se produce la siguiente salida:

```Output
0 2 4 6 8
```

Una función de filtro puede ser una función lambda, un puntero a función o un objeto de función. Cada función de filtro toma uno de los formatos siguientes.

```Output
bool (T)
bool (T const &)
```

Para eliminar la copia innecesaria de datos, use el segundo formato cuando tenga un tipo agregado que se propaga por valor.

El filtrado de mensajes admite el modelo de programación de *flujo* de datos, en el que los componentes realizan cálculos cuando reciben datos. Para obtener ejemplos que usan funciones de filtro para controlar el flujo de datos en una red de paso de mensajes, vea [Cómo: usar un filtro de bloque de mensajes](../../parallel/concrt/how-to-use-a-message-block-filter.md), [Tutorial: crear un agente de flujo](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)de datos y [Tutorial: crear una red de procesamiento de imágenes](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[[Arriba](#top)]

## <a name="reservation"></a>Reserva de mensajes

La *reserva de mensajes* permite a un bloque de mensajes reservar un mensaje para su uso posterior. Normalmente, la reserva de mensajes no se usa directamente. Sin embargo, entender la reserva de mensajes puede ayudarle a entender mejor el comportamiento de algunos tipos predefinidos de bloques de mensajes.

Considere las uniones no expansivas y expansivas. Ambas usan la reserva de mensajes para reservar mensajes para su uso posterior. Como se ha descrito anteriormente, una unión no expansiva recibe mensajes en dos fases. Durante la primera fase, un objeto `join` no expansivo espera que cada uno de sus orígenes reciba un mensaje. Una unión no expansiva después intenta reservar cada uno de esos mensajes. Si puede reservar cada mensaje, usa todos los mensajes y los propaga a su destino. De lo contrario, libera, o cancela, las reservas de mensajes y espera otra vez a que cada origen reciba un mensaje.

Una unión expansiva, que también lee mensajes de entrada de varios orígenes, usa la reserva de mensajes para leer mensajes adicionales mientras espera recibir un mensaje de cada origen. Por ejemplo, considere una unión expansiva que recibe mensajes de los bloques de mensajes `A` y `B`. Si la unión expansiva recibe dos mensajes de B pero aún no ha recibido un mensaje de `A`, la unión expansiva guarda el identificador de mensaje único para el segundo mensaje de `B`. Una vez que la unión expansiva recibe un mensaje de `A` y propaga out estos mensajes, usa el identificador de mensaje guardado para ver si el segundo mensaje de `B` sigue estando disponible.

Puede usar la reserva de mensajes al implementar sus propios tipos de bloques de mensajes. Para obtener un ejemplo sobre cómo crear un tipo de bloque de mensajes personalizado, vea [Tutorial: crear un bloque de mensajes personalizado](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md).

[[Arriba](#top)]

## <a name="see-also"></a>Consulte también

[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)
