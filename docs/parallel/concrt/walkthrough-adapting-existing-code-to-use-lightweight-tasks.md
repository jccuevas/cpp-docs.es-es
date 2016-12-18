---
title: "Tutorial: Adaptar el c&#243;digo existente para usar tareas ligeras | Microsoft Docs"
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
  - "usar tareas ligeras [Runtime de simultaneidad]"
  - "tareas ligeras, usar [Runtime de simultaneidad]"
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Adaptar el c&#243;digo existente para usar tareas ligeras
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este tema se muestra cómo adaptar código existente que usa la API de Windows para crear y ejecutar un subproceso para una tarea ligera.  
  
 Una *tarea ligera* es aquella que se programa directamente a partir de un objeto [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) o [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md).  Las tareas ligeras son útiles cuando se adapta código existente para usar la funcionalidad de programación del Runtime de simultaneidad.  
  
## Requisitos previos  
 Antes de empezar este tutorial, lea el tema [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
## Ejemplo  
  
### Descripción  
 En el siguiente ejemplo se muestra el uso típico de la API de Windows para crear y ejecutar un subproceso.  En este ejemplo se usa la función [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) para llamar a `MyThreadFunction` en un subproceso independiente.  
  
### Código  
 [!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]  
  
### Comentarios  
 Este ejemplo produce el siguiente resultado:  
  
  **Parámetros \= 50, 100** Los siguientes pasos muestran cómo adaptar el ejemplo de código para usar el Runtime de simultaneidad para realizar la misma tarea.  
  
### Para adaptar el ejemplo para usar una tarea ligera  
  
1.  Agregue una directiva `#include` para el archivo de encabezado concrt.h.  
  
     [!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]  
  
2.  Agregue una directiva `using` para el espacio de nombres `concurrency`.  
  
     [!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]  
  
3.  Cambie la declaración de `MyThreadFunction` pasa usar la convención de llamada `__cdecl` y devolver `void`.  
  
     [!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]  
  
4.  Modifique la estructura de `MyData` para incluir un objeto [concurrency::event](../../parallel/concrt/reference/event-class.md) que indique a la aplicación principal que la tarea ha terminado.  
  
     [!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]  
  
5.  Reemplace la llamada a `CreateThread` por una llamada al método [concurrency::CurrentScheduler::ScheduleTask](../Topic/CurrentScheduler::ScheduleTask%20Method.md).  
  
     [!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]  
  
6.  Reemplace la llamada a `WaitForSingleObject` por una llamada al método [concurrency::event::wait](../Topic/event::wait%20Method.md) para esperar a que finalice la tarea.  
  
     [!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]  
  
7.  Quite la llamada a `CloseHandle`.  
  
8.  Cambie la signatura de la definición de `MyThreadFunction` para que coincida con el paso 3.  
  
     [!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]  
  
9. Al final de la función `MyThreadFunction`, llame al método [concurrency::event::set](../Topic/event::set%20Method.md) para indicar a la aplicación principal que la tarea ha terminado.  
  
     [!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]  
  
10. Quite la instrucción `return` de `MyThreadFunction`.  
  
## Ejemplo  
  
### Descripción  
 En el siguiente ejemplo completo se muestra código que usa una tarea ligera para llamar a la función `MyThreadFunction`.  
  
### Código  
 [!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/CPP/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]  
  
### Comentarios  
  
## Vea también  
 [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Scheduler \(Clase\)](../../parallel/concrt/reference/scheduler-class.md)