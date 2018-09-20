---
title: 'Tutorial: Crear un bloque de mensajes personalizado | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9391d99f75bdb5ac2191a65e525ce989aefcd6b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421289"
---
# <a name="walkthrough-creating-a-custom-message-block"></a>Tutorial: Crear un bloque de mensajes personalizado

En este documento se describe cómo crear un tipo de bloque de mensajes personalizado que ordena los mensajes entrantes por prioridad.

Aunque los tipos integrados de bloques de mensajes proporciona una amplia gama de funcionalidad, puede crear su propio tipo de bloque de mensajes y personalizarlo para satisfacer los requisitos de la aplicación. Para obtener una descripción de los tipos de bloques de mensajes integrados proporcionados por la biblioteca de agentes asincrónicos, vea [bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="prerequisites"></a>Requisitos previos

Lea los documentos siguientes antes de iniciar este tutorial:

- [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)

##  <a name="top"></a> Secciones

Este tutorial contiene las siguientes secciones:

- [Diseñar un bloque de mensajes personalizado](#design)

- [Definir la clase priority_buffer](#class)

- [Ejemplo completo](#complete)

##  <a name="design"></a> Diseñar un bloque de mensajes personalizado

Los bloques de mensajes participan en el acto de enviar y recibir mensajes. Un bloque de mensajes que envía los mensajes se conoce como un *bloque de origen*. Un bloque de mensajes que recibe los mensajes se conoce como un *bloque de destino*. Un bloque de mensajes que envía y recibe los mensajes se conoce como un *bloque propagador*. La biblioteca de agentes usa la clase abstracta [Concurrency:: ISource](../../parallel/concrt/reference/isource-class.md) para representar bloques de origen y la clase abstracta [Concurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md) para representar bloques de destino. Los tipos de bloques de mensajes que actúan como orígenes derivan de `ISource`; los tipos de bloques de mensajes que actúan como destinos derivan de `ITarget`.

Aunque puede derivar el tipo de bloque de mensajes directamente de `ISource` y `ITarget`, la Biblioteca de agentes define tres clases base que realizan gran parte de la funcionalidad común a todos los tipos de bloques de mensajes; por ejemplo, control de errores y conexión de los bloques de mensajes de manera segura para simultaneidad. El [Concurrency:: source_block](../../parallel/concrt/reference/source-block-class.md) clase se deriva de `ISource` y envía mensajes a otros bloques. El [Concurrency:: target_block](../../parallel/concrt/reference/target-block-class.md) clase se deriva de `ITarget` y recibe mensajes desde otros bloques. El [Concurrency:: propagator_block](../../parallel/concrt/reference/propagator-block-class.md) clase se deriva de `ISource` y `ITarget` y envía mensajes a otros bloques y recibe mensajes desde otros bloques. Se recomienda usar estas tres clases base para controlar los detalles de infraestructura de modo que se pueda centrar en el comportamiento del bloque de mensajes.

Las clases `source_block`, `target_block` y `propagator_block` son plantillas que se parametrizan en un tipo que administra las conexiones, o vínculos, entre los bloques de origen y de destino y en un tipo que administra cómo se procesan los mensajes. La biblioteca de agentes define dos tipos que realizan la administración de vínculo, [Concurrency:: single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md) y [Concurrency:: multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md). La clase `single_link_registry` permite vincular un bloque de mensajes a un origen o a un destino. La clase `multi_link_registry` permite vincular un bloque de mensajes a varios orígenes o a varios destinos. La biblioteca de agentes define una clase que realiza la administración de mensajes, [Concurrency:: ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md). La clase `ordered_message_processor` permite que los bloques de mensajes procesen los mensajes en el orden en que se reciben.

Para entender mejor cómo se relacionan los bloques de mensajes con sus orígenes y destinos, considere el ejemplo siguiente. En este ejemplo se muestra la declaración de la [Concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) clase.

[!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]

La clase `transformer` se deriva de `propagator_block` y, por tanto, actúa como bloque de origen y como bloque de destino. Acepta mensajes de tipo `_Input` y envía mensajes de tipo `_Output`. La clase `transformer` especifica `single_link_registry` como administrador de vínculos para los bloques de destino y `multi_link_registry` como administrador de vínculos para los bloques de origen. Por tanto, un objeto `transformer` puede tener hasta un destino y un número ilimitado de orígenes.

Una clase que derive de `source_block` debe implementar seis métodos: [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets), [accept_message](reference/source-block-class.md#accept_message), [reserve_message](reference/source-block-class.md#reserve_message), [ consume_message](reference/source-block-class.md#consume_message), [release_message](reference/source-block-class.md#release_message), y [resume_propagation](reference/source-block-class.md#resume_propagation). Una clase que derive de `target_block` debe implementar la [propagate_message](reference/propagator-block-class.md#propagate_message) método y, opcionalmente, puede implementar la [send_message](reference/propagator-block-class.md#send_message) método. Derivar de `propagator_block` es funcionalmente equivalente a la derivación de `source_block` y `target_block`.

El runtime llama al método `propagate_to_any_targets` para procesar de forma sincrónica o asincrónica los mensajes entrantes y propagar los mensajes salientes. Los bloques de destino llaman al método `accept_message` para aceptar mensajes. Muchos tipos de bloques de mensajes, como `unbounded_buffer`, envían mensajes solo al primer destino que los recibiría. Por tanto, transfiere la propiedad del mensaje al destino. Bloque de mensajes de otros tipos, como [Concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md), ofrecen mensajes a cada uno de sus bloques de destino. Por tanto, `overwrite_buffer` crea una copia del mensaje para cada uno de sus destinos.

Los métodos `reserve_message`, `consume_message`, `release_message` y `resume_propagation` permiten a los bloques de mensajes participar en la reserva de mensajes. Los bloques de destino llaman al método `reserve_message` cuando se les ofrece un mensaje y tienen que reservar el mensaje para su uso posterior. Después de que un bloque de destino reserva un mensaje, puede llamar al método `consume_message` para usar ese mensaje o al método `release_message` para cancelar la reserva. Como sucede con el método `accept_message`, la implementación de `consume_message` puede transferir la propiedad del mensaje o devolver una copia del mensaje. Después de que un bloque de destino usa o libera un mensaje reservado, el runtime llama al método `resume_propagation`. Normalmente, este método continúa la propagación de mensajes, comenzando por el siguiente mensaje de la cola.

El runtime llama al método `propagate_message` para transferir de forma asincrónica un mensaje de otro bloque al actual. El método `send_message` es similar a `propagate_message`, excepto en que envía de forma sincrónica, en lugar de asincrónica, el mensaje a los bloques de destino. La implementación predeterminada de `send_message` rechaza todos los mensajes entrantes. El runtime no llama a ninguno de estos métodos si el mensaje no supera la función opcional de filtro asociada al bloque de destino. Para obtener más información acerca de los filtros de mensajes, vea [bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md).

[[Arriba](#top)]

##  <a name="class"></a> Definir la clase priority_buffer

La clase `priority_buffer` es un tipo de bloque de mensajes personalizado que ordena los mensajes entrantes primero por prioridad y, a continuación, en el orden en que se reciben los mensajes. El `priority_buffer` es similar a la [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) porque contiene una cola de mensajes y también porque actúa como un origen y un bloque de mensajes de destino y puede tener varios orígenes y varios destinos. Sin embargo, `unbounded_buffer` basa la propagación de mensaje solo en el orden en que recibe mensajes de sus orígenes.

El `priority_buffer` clase recibe los mensajes de tipo std::[tupla](../../standard-library/tuple-class.md) que contienen `PriorityType` y `Type` elementos. `PriorityType` se refiere al tipo que contiene la prioridad de cada mensaje; `Type` se refiere a la parte de datos del mensaje. La clase `priority_buffer` envía mensajes de tipo `Type`. El `priority_buffer` clase también administra dos colas de mensajes: un [std:: priority_queue](../../standard-library/priority-queue-class.md) objeto para los mensajes entrantes y std::[cola](../../standard-library/queue-class.md) objeto para los mensajes salientes. Ordenar los mensajes por prioridad es útil cuando un objeto `priority_buffer` recibe varios mensajes simultáneamente o cuando recibe varios mensajes antes de que los consumidores lean cualquier mensaje.

Además de los siete métodos que una clase derivada de `propagator_block` debe implementar, la clase `priority_buffer` también invalida los métodos `link_target_notification` y `send_message`. La clase `priority_buffer` también define dos métodos del asistente públicos, `enqueue` y `dequeue`, y un método del asistente privado, `propagate_priority_order`.

En el procedimiento siguiente se describe cómo implementar la clase `priority_buffer`.

#### <a name="to-define-the-prioritybuffer-class"></a>Para definir la clase priority_buffer

1. Cree un archivo de encabezado de C++ y asígnele el nombre `priority_buffer.h`. O bien, puede usar un archivo de encabezado existente que forme parte del proyecto.

1. En `priority_buffer.h`, agregue el código siguiente.

[!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]

1. En el `std` espacio de nombres, defina especializaciones de [std:: less](../../standard-library/less-struct.md) y [std:: Greater](../../standard-library/greater-struct.md) que actúan sobre simultaneidad::[mensaje](../../parallel/concrt/reference/message-class.md) objetos.

[!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]

     The `priority_buffer` class stores `message` objects in a `priority_queue` object. These type specializations enable the priority queue to sort messages according to their priority. The priority is the first element of the `tuple` object.

1. En el espacio de nombres `concurrencyex`, declare la clase `priority_buffer`.

[!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]

     The `priority_buffer` class derives from `propagator_block`. Therefore, it can both send and receive messages. The `priority_buffer` class can have multiple targets that receive messages of type `Type`. It can also have multiple sources that send messages of type `tuple<PriorityType, Type>`.

1. En la sección `private` de la clase `priority_buffer`, agregue las variables miembro siguientes.

[!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]

     The `priority_queue` object holds incoming messages; the `queue` object holds outgoing messages. A `priority_buffer` object can receive multiple messages simultaneously; the `critical_section` object synchronizes access to the queue of input messages.

1. En la sección `private`, defina el constructor de copias y el operador de asignación. Esto impide que los objetos `priority_queue` sean asignables.

[!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]

1. En la sección `public`, defina los constructores que son comunes a muchos tipos de bloques de mensajes. Defina también el destructor.

[!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]

1. En la sección `public`, defina los métodos `enqueue` y `dequeue`. Estos métodos del asistente proporcionan una manera alternativa de enviar mensajes a y recibir mensajes de un objeto `priority_buffer`.

[!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]

9. En la sección `protected`, defina el método `propagate_to_any_targets`.

[!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]

     The `propagate_to_any_targets` method transfers the message that is at the front of the input queue to the output queue and propagates out all messages in the output queue.

10. En la sección `protected`, defina el método `accept_message`.

[!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]

     When a target block calls the `accept_message` method, the `priority_buffer` class transfers ownership of the message to the first target block that accepts it. (This resembles the behavior of `unbounded_buffer`.)

11. En la sección `protected`, defina el método `reserve_message`.

[!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]

     The `priority_buffer` class permits a target block to reserve a message when the provided message identifier matches the identifier of the message that is at the front of the queue. In other words, a target can reserve the message if the `priority_buffer` object has not yet received an additional message and has not yet  propagated out the current one.

12. En la sección `protected`, defina el método `consume_message`.

[!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]

     A target block calls `consume_message` to transfer ownership of the message that it reserved.

13. En la sección `protected`, defina el método `release_message`.

[!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]

     A target block calls `release_message` to cancel its reservation to a message.

14. En la sección `protected`, defina el método `resume_propagation`.

[!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]

     The runtime calls `resume_propagation` after a target block either consumes or releases a reserved message. This method propagates out any messages that are in the output queue.

15. En la sección `protected`, defina el método `link_target_notification`.

[!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]

     The `_M_pReservedFor` member variable is defined by the base class, `source_block`. This member variable points to the target block, if any, that is holding a reservation to the message that is at the front of the output queue. The runtime calls `link_target_notification` when a new target is linked to the `priority_buffer` object. This method propagates out any messages that are in the output queue if no target is holding a reservation.

16. En la sección `private`, defina el método `propagate_priority_order`.

[!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]

     This method propagates out all messages from the output queue. Every message in the queue is offered to every target block until one of the target blocks accepts the message. The `priority_buffer` class preserves the order of the outgoing messages. Therefore, the first message in the output queue must be accepted by a target block before this method offers any other message to the target blocks.

17. En la sección `protected`, defina el método `propagate_message`.

[!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]

     The `propagate_message` method enables the `priority_buffer` class to act as a message receiver, or target. This method receives the message that is offered by the provided source block and inserts that message into the priority queue. The `propagate_message` method then asynchronously sends all output messages to the target blocks.

     The runtime calls this method when you call the [concurrency::asend](reference/concurrency-namespace-functions.md#asend) function or when the message block is connected to other message blocks.

18. En la sección `protected`, defina el método `send_message`.

[!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]

     The `send_message` method resembles `propagate_message`. However it sends the output messages synchronously instead of asynchronously.

     The runtime calls this method during a synchronous send operation, such as when you call the [concurrency::send](reference/concurrency-namespace-functions.md#send) function.

La clase `priority_buffer` contiene sobrecargas del constructor que son típicas en muchos tipos de bloques de mensajes. Algunas sobrecargas de constructor toman [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) o [Concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objetos, lo que permite el bloque de mensajes que se administrarán mediante un programador de tareas específicas. Otras sobrecargas del constructor toman una función de filtro. Las funciones de filtro permiten a los bloques de mensajes aceptar o rechazar un mensaje en función de su carga. Para obtener más información acerca de los filtros de mensajes, vea [bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md). Para obtener más información acerca de los programadores de tareas, consulte [programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Dado que el `priority_buffer` clase ordena los mensajes por prioridad y, a continuación, por el orden en que se reciben los mensajes, esta clase es muy útil cuando recibe mensajes de forma asincrónica, por ejemplo, cuando se llama a la [Concurrency:: asend](reference/concurrency-namespace-functions.md#asend)función o cuando el bloque de mensajes está conectado a otros bloques de mensajes.

[[Arriba](#top)]

##  <a name="complete"></a> El ejemplo completo

En el ejemplo siguiente se muestra la definición completa de la clase `priority_buffer`.

[!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]

El ejemplo siguiente realiza simultáneamente una serie de `asend` y [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) operaciones en un `priority_buffer` objeto.

[!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]

Este ejemplo genera la siguiente salida de ejemplo.

```Output
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12
```

La clase `priority_buffer` ordena los mensajes primero por prioridad y, a continuación, por el orden en que recibe los mensajes. En este ejemplo, los mensajes con mayor prioridad numérica se insertan al principio de la cola.

[[Arriba](#top)]

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o la definición de la `priority_buffer` clase en un archivo denominado `priority_buffer.h` y el programa de prueba en un archivo denominado `priority_buffer.cpp` y, a continuación, ejecute el siguiente comando en Visual Studio Ventana de símbolo del sistema.

**cl.exe/EHsc priority_buffer.cpp**

## <a name="see-also"></a>Vea también

[Tutoriales del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)
