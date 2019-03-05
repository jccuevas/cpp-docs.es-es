---
title: Procedimientos recomendados en la biblioteca de agentes asincrónicos
ms.date: 11/04/2016
helpviewer_keywords:
- best practices, Asynchronous Agents Library
- Asynchronous Agents Library, best practices
- Asynchronous Agents Library, practices to avoid
- practices to avoid, Asynchronous Agents Library
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
ms.openlocfilehash: c61393957a63895a9ecbdaaae8d83a5fbd710de3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266424"
---
# <a name="best-practices-in-the-asynchronous-agents-library"></a>Procedimientos recomendados en la biblioteca de agentes asincrónicos

En este documento se describe cómo hacer un uso eficaz de la biblioteca de agentes asincrónicos. La biblioteca de agentes promueve un modelo de programación basado en actores y en el paso de mensajes en proceso para el flujo de datos general y las tareas de canalización.

Para obtener más información acerca de la biblioteca de agentes, vea [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md).

##  <a name="top"></a> Secciones

Este documento contiene las siguientes secciones:

- [Usar a agentes para aislar el estado](#isolation)

- [Usar un mecanismo de limitación para limitar el número de mensajes en una canalización de datos](#throttling)

- [No realizar trabajo específico en una canalización de datos](#fine-grained)

- [No pasar cargas grandes de mensaje por valor](#large-payloads)

- [Usar shared_ptr en una datos red cuando la propiedad no está definida](#ownership)

##  <a name="isolation"></a> Usar a agentes para aislar el estado

La biblioteca de agentes proporciona alternativas al estado compartido al permitir conectar componentes aislados a través de un mecanismo de paso de mensajes asincrónico. Los agentes asincrónicos son más eficaces cuando aíslan su estado interno de otros componentes. Al aislar el estado, varios componentes no actúan normalmente en los datos compartidos. El aislamiento del estado puede permitir escalar la aplicación porque reduce la contención en la memoria compartida. El aislamiento del estado también reduce la posibilidad de condiciones de carrera e interbloqueo porque los componentes no tienen que sincronizar el acceso a los datos compartidos.

Normalmente, para aislar el estado en un agente, se conservan los miembros de datos en las secciones `private` o `protected` de la clase de agente y se usan los búferes de mensajes para comunicar los cambios de estado. El ejemplo siguiente se muestra el `basic_agent` (clase), que se deriva de [Concurrency:: Agent](../../parallel/concrt/reference/agent-class.md). La clase `basic_agent` usa dos búferes de mensajes para comunicarse con los componentes externos. Un búfer de mensajes contiene los mensajes entrantes; el otro búfer de mensajes contiene los mensajes de salida.

[!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_1.cpp)]

Para obtener ejemplos completos acerca de cómo definir y usar los agentes, vea [Tutorial: Crear una aplicación basada en agente](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md) y [Tutorial: Creación de un agente de flujo de datos](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md).

[[Arriba](#top)]

##  <a name="throttling"></a> Usar un mecanismo de limitación para limitar el número de mensajes en una canalización de datos

Muchos tipos de búfer de mensajes, como [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md), puede contener un número ilimitado de mensajes. Cuando un productor de mensajes envía mensajes a una canalización de datos más rápidamente de lo que el consumidor puede procesarlos, la aplicación puede entrar en un estado de memoria insuficiente. Puede usar un mecanismo de limitación, por ejemplo, un semáforo, para limitar el número de mensajes que están activos en paralelo en una canalización de datos.

En el siguiente ejemplo básico se muestra cómo usar un semáforo para limitar el número de mensajes en una canalización de datos. La canalización de datos usa el [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait) función para simular una operación que tarda al menos 100 milisegundos. Dado que el remitente muestra los mensajes más rápidamente de lo que el consumidor puede procesarlos, en este ejemplo se define la clase `semaphore` para que la aplicación pueda limitar el número de mensajes activos.

[!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_2.cpp)]

El objeto `semaphore` limita la canalización para procesar a lo sumo dos mensajes al mismo tiempo.

El productor de este ejemplo envía relativamente pocos mensajes al consumidor. Por consiguiente, en este ejemplo no se muestra una condición potencial de memoria insuficiente. Sin embargo, este mecanismo es útil cuando una canalización de datos contiene un número de mensajes relativamente elevado.

Para obtener más información sobre cómo crear la clase de semáforo que se usa en este ejemplo, vea [Cómo: Usar la clase Context para implementar un semáforo cooperativo](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).

[[Arriba](#top)]

##  <a name="fine-grained"></a> No realizar trabajo específico en una canalización de datos

La biblioteca de agentes es muy útil cuando el trabajo que realiza una canalización de datos es bastante general. Por ejemplo, un componente de la aplicación podría leer los datos de un archivo o una conexión de red y enviar ocasionalmente esos datos a otro componente. El protocolo que usa la biblioteca de agentes para propagar los mensajes hace que el mecanismo de paso de mensajes que tienen más sobrecarga que las construcciones paralelas de tareas proporcionadas por el [Parallel Patterns Library](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL). Por consiguiente, asegúrese de que el trabajo que realiza una canalización de datos es suficientemente larga para desplazar esta sobrecarga.

Aunque una canalización de datos es más eficaz cuando sus tareas son generales, cada fase de la canalización de datos puede usar las construcciones de PPL como grupos de tareas y algoritmos paralelos para realizar un trabajo más específico. Para obtener un ejemplo de una red de datos de generales que usa el paralelismo específico en cada fase de procesamiento, vea [Tutorial: Creación de una red de procesamiento de imágenes](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[[Arriba](#top)]

##  <a name="large-payloads"></a> No pasar cargas grandes de mensaje por valor

En algunos casos, el runtime crea una copia de cada mensaje que pasa de un búfer de mensajes a otro búfer de mensajes. Por ejemplo, el [Concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) clase ofrece una copia de todos los mensajes que recibe a cada uno de sus destinos. El tiempo de ejecución crea también una copia de los datos del mensaje al usar funciones de paso de mensajes, como [Concurrency:: Send](reference/concurrency-namespace-functions.md#send) y [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) para escribir y leer los mensajes de un mensaje búfer. Aunque este mecanismo ayuda a eliminar el riesgo de escribir simultáneamente en los datos compartidos, podría dar lugar a un rendimiento deficiente de memoria cuando la carga del mensaje es relativamente grande.

Puede utilizar los punteros o referencias para mejorar el rendimiento de la memoria al pasar los mensajes que tienen una carga grande. En el siguiente ejemplo se compara el paso de mensajes grandes por valor con el paso de punteros al mismo tipo de mensaje. En el ejemplo se definen dos tipos de agentes, `producer` y `consumer`, que actúan sobre los objetos `message_data`. En el ejemplo se compara el tiempo necesario para que el productor envíe varios objetos `message_data` al consumidor con el tiempo necesario para que el agente del productor envíe varios punteros a objetos `message_data` al consumidor.

[!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_3.cpp)]

Este ejemplo genera la siguiente salida de ejemplo:

```Output
Using message_data...
took 437ms.
Using message_data*...
took 47ms.
```

La versión que usa punteros funciona mejor porque elimina la necesidad de que el runtime cree una copia completa de cada objeto `message_data` que pasa del productor al consumidor.

[[Arriba](#top)]

##  <a name="ownership"></a> Usar shared_ptr en una datos red cuando la propiedad no está definida

Cuando se envían mensajes mediante un puntero a través de una canalización o una red de paso de mensajes, normalmente se asigna la memoria para cada mensaje al principio de la red y se libera esa memoria en el extremo de la red. Aunque este mecanismo funciona bien con frecuencia, hay casos en los que resulta difícil o imposible utilizarlo. Por ejemplo, considere el caso en el que la red de datos contiene varios nodos finales. En este caso, no hay ninguna ubicación clara para liberar la memoria para los mensajes.

Para solucionar este problema, puede usar un mecanismo, por ejemplo, [std:: shared_ptr](../../standard-library/shared-ptr-class.md), que permite un puntero a pertenecer a varios componentes. Cuando se destruye el objeto final `shared_ptr` que posee un recurso, se libera el recurso también.

En el ejemplo siguiente se muestra cómo usar `shared_ptr` para compartir valores de puntero entre búferes de mensajes. El ejemplo se conecta un [Concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) objeto a tres [Concurrency:: call](../../parallel/concrt/reference/call-class.md) objetos. La clase `overwrite_buffer` proporciona mensajes a cada uno de los destinos. Dado que hay varios propietarios de los datos en el extremo de la red de datos, en este ejemplo se usa `shared_ptr` para permitir que cada objeto `call` comparta la propiedad de los mensajes.

[!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_4.cpp)]

Este ejemplo genera la siguiente salida de ejemplo:

```Output
Creating resource 42...
receiver1: received resource 42
Creating resource 64...
receiver2: received resource 42
receiver1: received resource 64
Destroying resource 42...
receiver2: received resource 64
Destroying resource 64...
```

## <a name="see-also"></a>Vea también

[Procedimientos recomendados del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Tutorial: Creación de una aplicación basada en agente](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br/>
[Tutorial: Creación de un agente de flujo de datos](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[Tutorial: Creación de una red de procesamiento de imagen](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[Procedimientos recomendados en la biblioteca de modelos paralelos](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[Procedimientos recomendados generales en el Runtime de simultaneidad](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)
