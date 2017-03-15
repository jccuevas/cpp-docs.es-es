---
title: "Procedimientos recomendados en la biblioteca de agentes asincr&#243;nicos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "procedimientos recomendados, Biblioteca de agentes asincrónicos"
  - "Biblioteca de agentes asincrónicos, procedimientos recomendados"
  - "Biblioteca de agentes asincrónicos, procedimientos que deben evitarse"
  - "procedimientos que deben evitarse, Biblioteca de agentes asincrónicos"
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# Procedimientos recomendados en la biblioteca de agentes asincr&#243;nicos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este documento se describe cómo hacer un uso eficaz de la biblioteca de agentes asincrónicos.  La biblioteca de agentes promueve un modelo de programación basado en actores y en el paso de mensajes en proceso para el flujo de datos general y las tareas de canalización.  
  
 Para obtener más información sobre la Biblioteca de agentes, vea [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md).  
  
##  <a name="top"></a> Secciones  
 Este documento contiene las siguientes secciones:  
  
-   [Usar agentes para aislar el estado](#isolation)  
  
-   [Usar un mecanismo de limitación para limitar el número de mensajes en una canalización de datos](#throttling)  
  
-   [No realizar trabajo específico en una canalización de datos](#fine-grained)  
  
-   [No pasar cargas grandes de mensaje por valor](#large-payloads)  
  
-   [Usar shared\_ptr en una red de datos cuando la propiedad no está definida](#ownership)  
  
##  <a name="isolation"></a> Usar agentes para aislar el estado  
 La biblioteca de agentes proporciona alternativas al estado compartido al permitir conectar componentes aislados a través de un mecanismo de paso de mensajes asincrónico.  Los agentes asincrónicos son más eficaces cuando aíslan su estado interno de otros componentes.  Al aislar el estado, varios componentes no actúan normalmente en los datos compartidos.  El aislamiento del estado puede permitir escalar la aplicación porque reduce la contención en la memoria compartida.  El aislamiento del estado también reduce la posibilidad de condiciones de carrera e interbloqueo porque los componentes no tienen que sincronizar el acceso a los datos compartidos.  
  
 Normalmente, para aislar el estado en un agente, se conservan los miembros de datos en las secciones `private` o `protected` de la clase de agente y se usan los búferes de mensajes para comunicar los cambios de estado.  En el ejemplo siguiente se muestra la clase `basic_agent`, que se deriva de [concurrency::agent](../../parallel/concrt/reference/agent-class.md).  La clase `basic_agent` usa dos búferes de mensajes para comunicarse con los componentes externos.  Un búfer de mensajes contiene los mensajes entrantes; el otro búfer de mensajes contiene los mensajes de salida.  
  
 [!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-asynchronous-agents-library_1.cpp)]  
  
 Para obtener ejemplos completos sobre cómo definir y usar los agentes, vea [Tutorial: Crear una aplicación basada en agente](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md) y [Tutorial: Crear un agente de flujo de datos](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md).  
  
 \[[Arriba](#top)\]  
  
##  <a name="throttling"></a> Usar un mecanismo de limitación para limitar el número de mensajes en una canalización de datos  
 Muchos tipos de búferes de mensajes, como [concurrency::unbounded\_buffer](../Topic/unbounded_buffer%20Class.md), pueden contener un número ilimitado de mensajes.  Cuando un productor de mensajes envía mensajes a una canalización de datos más rápidamente de lo que el consumidor puede procesarlos, la aplicación puede entrar en un estado de memoria insuficiente.  Puede usar un mecanismo de limitación, por ejemplo, un semáforo, para limitar el número de mensajes que están activos en paralelo en una canalización de datos.  
  
 En el siguiente ejemplo básico se muestra cómo usar un semáforo para limitar el número de mensajes en una canalización de datos.  La canalización de datos usa la función [concurrency::wait](../Topic/wait%20Function.md) para simular una operación que tarda al menos 100 milisegundos.  Dado que el remitente muestra los mensajes más rápidamente de lo que el consumidor puede procesarlos, en este ejemplo se define la clase `semaphore` para que la aplicación pueda limitar el número de mensajes activos.  
  
 [!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-asynchronous-agents-library_2.cpp)]  
  
 El objeto `semaphore` limita la canalización para procesar a lo sumo dos mensajes al mismo tiempo.  
  
 El productor de este ejemplo envía relativamente pocos mensajes al consumidor.  Por consiguiente, en este ejemplo no se muestra una condición potencial de memoria insuficiente.  Sin embargo, este mecanismo es útil cuando una canalización de datos contiene un número de mensajes relativamente elevado.  
  
 Para obtener más información sobre cómo crear la clase de semáforo que se usa en este ejemplo, vea [Cómo: Usar la clase Context para implementar un semáforo cooperativo](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).  
  
 \[[Arriba](#top)\]  
  
##  <a name="fine-grained"></a> No realizar trabajo específico en una canalización de datos  
 La biblioteca de agentes es muy útil cuando el trabajo que realiza una canalización de datos es bastante general.  Por ejemplo, un componente de la aplicación podría leer los datos de un archivo o una conexión de red y enviar ocasionalmente esos datos a otro componente.  El protocolo que la biblioteca de agentes usa para propagar los mensajes hace que el mecanismo de paso de mensajes tenga más sobrecarga que las construcciones paralelas de tareas proporcionadas por la [biblioteca de modelos de procesamiento paralelo](../../parallel/concrt/parallel-patterns-library-ppl.md) \(PPL\).  Por consiguiente, asegúrese de que el trabajo que realiza una canalización de datos es suficientemente larga para desplazar esta sobrecarga.  
  
 Aunque una canalización de datos es más eficaz cuando sus tareas son generales, cada fase de la canalización de datos puede usar las construcciones de PPL como grupos de tareas y algoritmos paralelos para realizar un trabajo más específico.  Para obtener un ejemplo de una red de datos de generales que usa el paralelismo específico en cada fase de procesamiento, vea [Tutorial: Crear una red de procesamiento de imagen](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).  
  
 \[[Arriba](#top)\]  
  
##  <a name="large-payloads"></a> No pasar cargas grandes de mensaje por valor  
 En algunos casos, el runtime crea una copia de cada mensaje que pasa de un búfer de mensajes a otro búfer de mensajes.  Por ejemplo, la clase [concurrency::overwrite\_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) proporciona una copia de cada mensaje que recibe a cada uno de sus destinos.  El runtime también crea una copia de los datos del mensaje cuando se usan funciones de paso de mensajes como [concurrency::send](../Topic/send%20Function.md) y [concurrency::receive](../Topic/receive%20Function.md) para escribir y leer los mensajes de un búfer de mensajes.  Aunque este mecanismo ayuda a eliminar el riesgo de escribir simultáneamente en los datos compartidos, podría dar lugar a un rendimiento deficiente de memoria cuando la carga del mensaje es relativamente grande.  
  
 Puede utilizar los punteros o referencias para mejorar el rendimiento de la memoria al pasar los mensajes que tienen una carga grande.  En el siguiente ejemplo se compara el paso de mensajes grandes por valor con el paso de punteros al mismo tipo de mensaje.  En el ejemplo se definen dos tipos de agentes, `producer` y `consumer`, que actúan sobre los objetos `message_data`.  En el ejemplo se compara el tiempo necesario para que el productor envíe varios objetos `message_data` al consumidor con el tiempo necesario para que el agente del productor envíe varios punteros a objetos `message_data` al consumidor.  
  
 [!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-asynchronous-agents-library_3.cpp)]  
  
 Este ejemplo genera la siguiente salida de ejemplo:  
  
  **Using message\_data...**  
**took 437ms.**  
**Using message\_data\*...**  
**took 47ms.** La versión que usa punteros funciona mejor porque elimina la necesidad de que el runtime cree una copia completa de cada objeto `message_data` que pasa del productor al consumidor.  
  
 \[[Arriba](#top)\]  
  
##  <a name="ownership"></a> Usar shared\_ptr en una red de datos cuando la propiedad no está definida  
 Cuando se envían mensajes mediante un puntero a través de una canalización o una red de paso de mensajes, normalmente se asigna la memoria para cada mensaje al principio de la red y se libera esa memoria en el extremo de la red.  Aunque este mecanismo funciona bien con frecuencia, hay casos en los que resulta difícil o imposible utilizarlo.  Por ejemplo, considere el caso en el que la red de datos contiene varios nodos finales.  En este caso, no hay ninguna ubicación clara para liberar la memoria para los mensajes.  
  
 Para solucionar este problema, puede usar un mecanismo, por ejemplo, [std::shared\_ptr](../../standard-library/shared-ptr-class.md), que habilita un puntero que va a ser propiedad de varios componentes.  Cuando se destruye el objeto final `shared_ptr` que posee un recurso, se libera el recurso también.  
  
 En el ejemplo siguiente se muestra cómo usar `shared_ptr` para compartir valores de puntero entre búferes de mensajes.  En el ejemplo se conecta un objeto [concurrency::overwrite\_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) con tres objetos [concurrency::call](../../parallel/concrt/reference/call-class.md).  La clase `overwrite_buffer` proporciona mensajes a cada uno de los destinos.  Dado que hay varios propietarios de los datos en el extremo de la red de datos, en este ejemplo se usa `shared_ptr` para permitir que cada objeto `call` comparta la propiedad de los mensajes.  
  
 [!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-asynchronous-agents-library_4.cpp)]  
  
 Este ejemplo genera la siguiente salida de ejemplo:  
  
  **Creating resource 42...**  
**receiver1: received resource 42**  
**Creating resource 64...**  
**receiver2: received resource 42**  
**receiver1: received resource 64**  
**Destroying resource 42...**  
**receiver2: received resource 64**  
**Destroying resource 64...**   
## Vea también  
 [Procedimientos recomendados del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)   
 [Tutorial: Crear una aplicación basada en agente](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)   
 [Tutorial: Crear un agente de flujo de datos](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)   
 [Tutorial: Crear una red de procesamiento de imagen](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)   
 [Procedimientos recomendados en la biblioteca de modelos paralelos](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)   
 [Procedimientos recomendados generales con el Runtime de simultaneidad](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)