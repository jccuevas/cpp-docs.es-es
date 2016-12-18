---
title: "Tareas ligeras | Microsoft Docs"
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
  - "tareas ligeras"
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
caps.latest.revision: 7
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tareas ligeras
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este documento se describe el rol de las tareas ligeras en el runtime de simultaneidad.  Una *tarea ligera* es una tarea que programa directamente a partir del objeto `concurrency::ScheduleGroup` o `concurrency::Scheduler`.  Una tarea ligera recuerda a la función que se proporciona a la función de la API de Windows [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453).  Por consiguiente, las tareas ligeras son útiles cuando se adapta código existente para usar la funcionalidad de programación del Runtime de simultaneidad.  El propio Runtime de simultaneidad utiliza las tareas ligeras para programar los agentes asincrónicos y enviar mensajes entre los bloques de mensajes asincrónicos.  
  
> [!TIP]
>  El runtime de simultaneidad proporciona un programador predeterminado y, por tanto, no es necesario crear uno en la aplicación.  Dado que el programador de tareas ayuda a ajustar el rendimiento de las aplicaciones, se recomienda que comience con [Parallel Patterns Library \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md) o [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si no ha usado antes el runtime de simultaneidad.  
  
 Las tareas ligeras llevan menos sobrecarga que los agentes asincrónicos y los grupos de tareas.  Por ejemplo, el runtime no informa cuando finaliza una tarea ligera.  Además, el runtime no detecta ni administra las excepciones que se producen desde una tarea ligera.  Para obtener más información sobre control de excepciones y tareas ligeras, vea [Control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
 Para la mayoría de las tareas, recomendamos utilizar funcionalidad más robusta, como grupos de tareas y algoritmos paralelos, porque permiten descomponer más fácilmente tareas complejas en tareas más básicas.  Para obtener más información acerca de los grupos de tareas, vea [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  Para obtener más información acerca de los algoritmos paralelos, vea [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).  
  
 Para crear una tarea ligera, llame a [concurrency::ScheduleGroup::ScheduleTask](../Topic/ScheduleGroup::ScheduleTask%20Method.md), [concurrency::CurrentScheduler::ScheduleTask](../Topic/CurrentScheduler::ScheduleTask%20Method.md), o un método de [concurrency::Scheduler::ScheduleTask](../Topic/Scheduler::ScheduleTask%20Method.md) .  Para esperar a que una tarea ligera finalice, espere a que el programador primario para cerrar o use un mecanismo de sincronización como un objeto de [concurrency::event](../../parallel/concrt/reference/event-class.md) .  
  
## Ejemplo  
 Para obtener un ejemplo que muestra cómo adaptar el código existente para utilizar una tarea ligera, vea [Tutorial: Adaptar el código existente para usar tareas ligeras](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md).  
  
## Vea también  
 [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Tutorial: Adaptar el código existente para usar tareas ligeras](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)