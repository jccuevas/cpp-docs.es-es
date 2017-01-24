---
title: "C&#243;mo: Administrar una instancia del programador | Microsoft Docs"
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
  - "administrar una instancia del programador [Runtime de simultaneidad]"
  - "instancias del programador, administrar [Runtime de simultaneidad]"
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
caps.latest.revision: 15
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Administrar una instancia del programador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las instancias del Programador permiten asociar directivas de programación concretas con varios tipos de cargas de trabajo.  Este tema contiene dos ejemplos básicos que muestran cómo crear y administrar una instancia del programador.  
  
 En los ejemplos se crean programadores que usan las directivas del programador predeterminado.  Para obtener un ejemplo donde se crea un programador que usa una directiva personalizada, vea [Cómo: Especificar directivas de programador concretas](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).  
  
### Para administrar una instancia del programador en su aplicación  
  
1.  Cree un objeto [concurrency::SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) que contenga los valores de directiva que debe usar el programador.  
  
2.  Llame al método [concurrency::CurrentScheduler::Create](../Topic/CurrentScheduler::Create%20Method.md) o al método [concurrency::Scheduler::Create](../Topic/Scheduler::Create%20Method.md) para crear una instancia del programador.  
  
     Si usa el método `Scheduler::Create`, llame al método [concurrency::Scheduler::Attach](../Topic/Scheduler::Attach%20Method.md) cuando necesite asociar el programador al contexto actual.  
  
3.  Llame a la función [CreateEvent](http://msdn.microsoft.com/library/windows/desktop/ms682396) para crear un controlador para un objeto de evento de restablecimiento automático no señalado.  
  
4.  Pase el identificador del objeto de evento recién creado al método [concurrency::CurrentScheduler::RegisterShutdownEvent](../Topic/CurrentScheduler::RegisterShutdownEvent%20Method.md) o al método [concurrency::Scheduler::RegisterShutdownEvent](../Topic/Scheduler::RegisterShutdownEvent%20Method.md).  De esta forma se registra el evento que se debe establecer cuando se destruya el programador.  
  
5.  Realice las tareas que desea que programe el programador actual.  
  
6.  Llame al método [concurrency::CurrentScheduler::Detach](../Topic/CurrentScheduler::Detach%20Method.md) para desasociar el programador actual y restaurar el programador anterior.  
  
     Si usa el método `Scheduler::Create`, llame al método [concurrency::Scheduler::Release](../Topic/Scheduler::Release%20Method.md) para reducir el recuento de referencias del objeto `Scheduler`.  
  
7.  Pase el controlador del evento a la función [WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032) para esperar a que el programador se cierre.  
  
8.  Llame a la función [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211) para cerrar el controlador del objeto de evento.  
  
## Ejemplo  
 En el siguiente código se muestran dos maneras de administrar una instancia del programador.  En cada ejemplo se usa primero el programador predeterminado para realizar una tarea que imprima el identificador único del programador actual.  A continuación, se usa una instancia del programador para realizar la misma tarea de nuevo.  Finalmente, en cada ejemplo se restaura el programador predeterminado como el actual y se realiza la tarea una vez más.  
  
 En el primer ejemplo, se usa la clase [concurrency::CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) para crear una instancia del programador y asociarla al contexto actual.  En el segundo ejemplo, se usa la clase [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) para realizar la misma tarea.  Normalmente, la clase `CurrentScheduler` se usa con el programador actual.  El segundo ejemplo, que usa la clase `Scheduler`, es útil si se desea controlar cuándo está asociado el programador al contexto actual o si se desea asociar programadores concretos a tareas concretas.  
  
 [!code-cpp[concrt-scheduler-instance#1](../../parallel/concrt/codesnippet/CPP/how-to-manage-a-scheduler-instance_1.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **Using CurrentScheduler class...**  
**Current scheduler id: 0**  
**Creating and attaching scheduler...**  
**Current scheduler id: 1**  
**Detaching scheduler...**  
**Current scheduler id: 0**  
**Using Scheduler class...**  
**Current scheduler id: 0**  
**Creating scheduler...**  
**Attaching scheduler...**  
**Current scheduler id: 2**  
**Detaching scheduler...**  
**Current scheduler id: 0**   
## Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o en un archivo denominado `scheduler-instance.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc scheduler\-instance.cpp**  
  
## Vea también  
 [Instancias del programador](../../parallel/concrt/scheduler-instances.md)   
 [Cómo: Especificar directivas de programador concretas](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)