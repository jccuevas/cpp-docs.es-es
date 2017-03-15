---
title: "Tutoriales del Runtime de simultaneidad | Microsoft Docs"
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
  - "Runtime de simultaneidad, tutoriales"
  - "tutoriales [Runtime de simultaneidad]"
ms.assetid: 7374c5e9-54eb-44bf-9ed9-5e190cfd290b
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Tutoriales del Runtime de simultaneidad
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En los temas basados en escenarios de esta sección se muestra cómo se usan muchas de las características del Runtime de simultaneidad.  
  
## En esta sección  
 [Tutorial: Conectar usando tareas y solicitudes HTTP XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)  
 Muestra cómo utilizar las interfaces [IXMLHTTPRequest2](http://msdn.microsoft.com/es-es/bbc11c4a-aecf-4d6d-8275-3e852e309908) e [IXMLHTTPRequest2Callback](http://msdn.microsoft.com/es-es/aa4b3f4c-6e28-458b-be25-6cce8865fc71) junto con otras tareas para enviar solicitudes HTTP GET y POST a un servicio web en una aplicación de la [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  
  
 [Tutorial: Crear una aplicación basada en agente](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)  
 Describe cómo se crea una aplicación básica basada en un agente.  
  
 [Tutorial: Crear un agente de flujo de datos](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)  
 Muestra cómo crear aplicaciones basadas en agentes que recurren al flujo de datos, no al flujo de control.  
  
 [Tutorial: Crear una red de procesamiento de imagen](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)  
 Muestra cómo crear una red de bloques de mensajes asincrónicos que realizan el procesamiento de imágenes.  
  
 [Tutorial: Implementar futuros](../../parallel/concrt/walkthrough-implementing-futures.md)  
 Muestra cómo se calculan asincrónicamente valores para su uso posterior.  
  
 [Tutorial: Usar la clase join para evitar un interbloqueo](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)  
 Usa el problema de la cena de los filósofos para mostrar cómo utilizar la clase de [concurrency::join](../../parallel/concrt/reference/join-class.md) para evitar el interbloqueo en la aplicación.  
  
 [Tutorial: Quitar trabajo de un subproceso de la interfaz de usuario](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)  
 Muestra cómo puede mejorarse el rendimiento de una aplicación MFC que dibuja el fractal de Mandelbrot.  
  
 [Tutorial: Usar el Runtime de simultaneidad en una aplicación habilitada para COM](../../parallel/concrt/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application.md)  
 Muestra cómo se usa el Runtime de simultaneidad en una aplicación que emplea el Modelo de objetos componentes \(COM\).  
  
 [Tutorial: Adaptar el código existente para usar tareas ligeras](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)  
 Muestra cómo adaptar código existente que utiliza la API de Windows para crear y ejecutar un subproceso para una tarea ligera.  
  
 [Tutorial: Crear un bloque de mensajes personalizado](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)  
 Describe cómo crear un tipo de bloque de mensajes personalizado que ordena los mensajes entrantes por prioridad.  
  
## Secciones relacionadas  
 [Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime.md)  
 Presenta el marco de programación simultáneo de Visual C\+\+.