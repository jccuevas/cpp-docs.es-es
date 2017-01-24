---
title: "Runtime de simultaneidad | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "Runtime de simultaneidad, introducción"
  - "ConcRT (véase Runtime de simultaneidad)"
  - "Runtime de simultaneidad"
ms.assetid: 874bc58f-8dce-483e-a3a1-4dcc9e52ed2c
caps.latest.revision: 40
caps.handback.revision: 39
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Runtime de simultaneidad
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El runtime de simultaneidad de C\+\+ ayuda a escribir aplicaciones paralelas sólidas, escalables y receptivas. Eleva el nivel de abstracción para que, de esta forma, no sea necesario administrar los detalles de infraestructura relacionados con la simultaneidad. También se puede usar para especificar directivas de programación que cumplan las demandas de calidad de servicio de las aplicaciones. Use estos recursos como ayuda para empezar a trabajar con el runtime de simultaneidad.  
  
 Para obtener documentación de referencia, consulte [Referencia](../../parallel/concrt/reference/reference-concurrency-runtime.md).  
  
> [!TIP]
>  El runtime de simultaneidad se basa principalmente en las características C\+\+11 y adopta el estilo más moderno de C\+\+. Para obtener más información, lea [Aquí está otra vez C\+\+](../../cpp/welcome-back-to-cpp-modern-cpp.md).  
  
## Elegir características del runtime de simultaneidad  
  
|||  
|-|-|  
|[Información general](../../parallel/concrt/overview-of-the-concurrency-runtime.md)|Le enseña por qué el runtime de simultaneidad es importante y describe sus características clave.|  
|[Comparar con otros modelos de simultaneidad](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|Compara el runtime de simultaneidad con otros modelos de simultaneidad, como el grupo de subprocesos de Windows y OpenMP, para que pueda usar el modelo de simultaneidad que mejor se ajuste a los requisitos de la aplicación.|  
|[Migrar de OpenMP al Runtime de simultaneidad](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)|Compara OpenMP con el runtime de simultaneidad y proporciona ejemplos sobre cómo migrar el código existente de OpenMP para usar el runtime de simultaneidad.|  
|[Parallel Patterns Library \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Presenta el PPL, que proporciona bucles, tareas y contenedores paralelos.|  
|[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)|Le explica cómo usar los agentes asincrónicos y el paso de mensajes para incorporar fácilmente las tareas de flujo de datos y canalización a las aplicaciones.|  
|[Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)|Presenta el Programador de tareas, que le permite ajustar el rendimiento de las aplicaciones de escritorio que usa el runtime de simultaneidad.|  
  
## Paralelismo de tareas en PPL  
  
|||  
|-|-|  
|[Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br /><br /> [Cómo: Usar parallel.invoke para escribir una rutina de ordenación en paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br /><br /> [Cómo: Usar parallel.invoke para ejecutar operaciones paralelas](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)<br /><br /> [Cómo: Crear una tarea que se complete después de un retardo](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Describe las tareas y los grupos de tareas, que le pueden ayudar a escribir código asincrónico y a descomponer el trabajo paralelo en partes más pequeñas.|  
|[Tutorial: Implementar futuros](../../parallel/concrt/walkthrough-implementing-futures.md)|Muestra cómo combinar las características del runtime de simultaneidad para llevar a cabo más tareas.|  
|[Tutorial: Quitar trabajo de un subproceso de la interfaz de usuario](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)|Muestra cómo mover el trabajo realizado por el subproceso de interfaz de usuario en una aplicación MFC a un subproceso de trabajo.|  
|[Procedimientos recomendados en la biblioteca de modelos paralelos](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Procedimientos recomendados generales con el Runtime de simultaneidad](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Proporciona sugerencias y prácticas recomendadas para trabajar con el PPL.|  
  
## Paralelismo de datos en PPL  
  
|||  
|-|-|  
|[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)<br /><br /> [Cómo: Escribir un bucle parallel\_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)<br /><br /> [Cómo: Escribir un bucle parallel\_for\_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)<br /><br /> [Cómo: Realizar operaciones de asignación y reducción en paralelo](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Describe `parallel_for`, `parallel_for_each`, `parallel_invoke` y otros algoritmos paralelos. Use algoritmos paralelos para solucionar problemas *de datos en paralelo* que impliquen colecciones de datos.|  
|[Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)<br /><br /> [Cómo: Usar contenedores paralelos para aumentar la eficacia](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br /><br /> [Cómo: Usar la clase combinable para mejorar el rendimiento](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br /><br /> [Cómo: Usar la clase combinable para combinar conjuntos](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)|Describe la clase `combinable`, así como `concurrent_vector`, `concurrent_queue`, `concurrent_unordered_map` y otros contenedores paralelos. Use contenedores y objetos paralelos cuando necesite contenedores que proporcionen acceso seguro para subprocesos a sus elementos.|  
|[Procedimientos recomendados en la biblioteca de modelos paralelos](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Procedimientos recomendados generales con el Runtime de simultaneidad](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Proporciona sugerencias y prácticas recomendadas para trabajar con el PPL.|  
  
## Cancelar tareas y algoritmos paralelos  
  
|||  
|-|-|  
|[Cancelación](../../parallel/concrt/cancellation-in-the-ppl.md)|Describe el rol de cancelación en PPL, incluyendo cómo iniciar y responder a las solicitudes de cancelación.|  
|[Cómo: Usar la cancelación para interrumpir un bucle Parallel](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br /><br /> [Cómo: Usar el control de excepciones para interrumpir un bucle Parallel](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Muestra dos mecanismos para cancelar el trabajo de datos en paralelo.|  
  
## Aplicaciones de la Tienda Windows  
  
|||  
|-|-|  
|[Crear operaciones asincrónicas en C\+\+ para aplicaciones de la Tienda Windows](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)|Describe algunos de los puntos clave para tener en cuenta cuando se usa el runtime de simultaneidad para generar operaciones asincrónicas en una aplicación de la [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].|  
|[Tutorial: Conectar usando tareas y solicitudes HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)|Muestra cómo combinar tareas PPL con interfaces `IXMLHTTPRequest2` y `IXMLHTTPRequest2Callback` para enviar solicitudes HTTP GET y POST a un servicio web en una aplicación de la [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].|  
|[Ejemplos de aplicación de la Tienda Windows](http://code.msdn.microsoft.com/windowsapps)|Contiene ejemplos de código descargables y aplicaciones de demostración para [!INCLUDE[win8](../../build/includes/win8_md.md)]. Los ejemplos de C\+\+ usan características del runtime de simultaneidad, como tareas PPL, para procesar datos en segundo plano con objeto de que la UX siga respondiendo.|  
  
## Programación del flujo de datos en la Biblioteca de agentes asincrónicos  
  
|||  
|-|-|  
|[Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)<br /><br /> [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br /><br /> [Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)<br /><br /> [Cómo: Implementar varios modelos productor\-consumidor](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br /><br /> [Cómo: Proporcionar funciones de trabajo a las clases call y transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br /><br /> [Cómo: Usar la clase transformer en una canalización de datos](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br /><br /> [Cómo: Seleccionar tareas completadas](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br /><br /> [Cómo: Enviar un mensaje a intervalos periódicos](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br /><br /> [Cómo: Utilizar un filtro de bloque de mensaje](../../parallel/concrt/how-to-use-a-message-block-filter.md)|Describe los agentes asincrónicos, los bloques de mensajes, y las funciones de paso de mensajes, que son los bloques de creación para realizar operaciones de flujo de datos en el runtime de simultaneidad.|  
|[Tutorial: Crear una aplicación basada en agente](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br /><br /> [Tutorial: Crear un agente de flujo de datos](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)|Muestra cómo crear aplicaciones básicas basadas en un agente.|  
|[Tutorial: Crear una red de procesamiento de imagen](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)|Muestra cómo crear una red de bloques de mensajes asincrónicos que realizan el procesamiento de imágenes.|  
|[Tutorial: Usar la clase join para evitar un interbloqueo](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)|Usa el problema de la cena de los filósofos para ilustrar cómo se usa el runtime de simultaneidad para evitar el interbloqueo en la aplicación.|  
|[Tutorial: Crear un bloque de mensajes personalizado](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)|Muestra cómo crear un tipo de bloque de mensajes personalizado que ordena los mensajes entrantes por prioridad.|  
|[Procedimientos recomendados en la biblioteca de agentes asincrónicos](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br /><br /> [Procedimientos recomendados generales con el Runtime de simultaneidad](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Proporciona sugerencias y prácticas recomendadas para trabajar con agentes.|  
  
## Control de excepciones y depuración  
  
|||  
|-|-|  
|[Control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Describe cómo trabajar con excepciones en el runtime de simultaneidad.|  
|[Herramientas de diagnóstico paralelo](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Le enseña cómo ajustar las aplicaciones y hacer un uso más eficaz del runtime de simultaneidad.|  
  
## Optimizar el rendimiento  
  
|||  
|-|-|  
|[Herramientas de diagnóstico paralelo](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Le enseña cómo ajustar las aplicaciones y hacer un uso más eficaz del runtime de simultaneidad.|  
|[Instancias del programador](../../parallel/concrt/scheduler-instances.md)<br /><br /> [Cómo: Administrar una instancia del programador](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br /><br /> [Directivas del programador](../../parallel/concrt/scheduler-policies.md)<br /><br /> [Cómo: Especificar directivas de programador concretas](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br /><br /> [Cómo: Crear agentes que usen directivas de programador específicas](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)|Muestra cómo administrar las instancias y las directivas de programador. En las aplicaciones de escritorio, las directivas de programador le permiten asociar reglas específicas con tipos concretos de cargas de trabajo. Por ejemplo, puede crear una instancia de programador para ejecutar algunas tareas con una prioridad elevada de subproceso y usar el programador predeterminado para ejecutar con otras tareas con la prioridad normal de subproceso.|  
|[Grupos de programación](../../parallel/concrt/schedule-groups.md)<br /><br /> [Cómo: Usar grupos de programación para influir en el orden de ejecución](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)|Muestra cómo usar los grupos de programación para establecer afinidades entre las tareas relacionadas y agruparlas. Por ejemplo, es posible que necesite un alto grado de emplazamiento entre tareas relacionadas cuando estas tareas se benefician de ejecutarse en el mismo nodo del procesador.|  
|[Tareas ligeras](../../parallel/concrt/lightweight-tasks.md)|Explica cómo se pueden usar las tareas ligeras para crear trabajo que no requiere equilibrio de carga ni cancelación, y cómo resultan útiles para adaptar el código existente para su uso con el runtime de simultaneidad.|  
|[Contextos](../../parallel/concrt/contexts.md)<br /><br /> [Cómo: Usar la clase Context para implementar un semáforo cooperativo](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br /><br /> [Cómo: Usar la suscripción excesiva para compensar la latencia](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)|Describe cómo controlar el comportamiento de los subprocesos que administra el runtime de simultaneidad.|  
|[Funciones de administración de memoria](../../parallel/concrt/memory-management-functions.md)<br /><br /> [Cómo: Usar Alloc y Free para mejorar el rendimiento de la memoria](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)|Describe las funciones de administración de memoria que el runtime de simultaneidad proporciona para ayudarle a asignar y liberar memoria de manera simultánea.|  
  
## Recursos adicionales  
  
|||  
|-|-|  
|[Patrones y sugerencias de programación Async en Hilo \(aplicaciones de la Tienda Windows que usan C\+\+ y XAML\)](http://msdn.microsoft.com/library/windows/apps/jj160321.aspx)|Obtenga información sobre el uso del runtime de simultaneidad para implementar operaciones asincrónicas en Hilo, una aplicación de la [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] que usa C\+\+ y XAML.|  
|[Ejemplos de código para el Runtime de simultaneidad y la biblioteca de patrones de procesamiento paralelo en Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkID=183875)|Proporciona aplicaciones de ejemplo y utilidades que muestran el uso del runtime de simultaneidad.|  
|[Blog de programación en paralelo en código nativo](http://go.microsoft.com/fwlink/?LinkID=183873)|Proporciona artículos de blog detallados adicionales sobre la programación paralela en el runtime de simultaneidad.|  
|[Foro de informática en paralelo en C\+\+ y código nativo](http://go.microsoft.com/fwlink/?LinkID=183874)|Le permite participar en los debates de la comunidad sobre el runtime de simultaneidad.|  
|[Parallel Programming](../Topic/Parallel%20Programming%20in%20the%20.NET%20Framework.md)|Le enseña el modelo de programación paralelo que está disponible en [!INCLUDE[dnprdnshort](../../error-messages/tool-errors/includes/dnprdnshort_md.md)].|  
  
## Vea también  
 [Referencia](../../parallel/concrt/reference/reference-concurrency-runtime.md)