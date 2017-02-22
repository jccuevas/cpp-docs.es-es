---
title: "CurrentScheduler (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::CurrentScheduler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CurrentScheduler (clase)"
ms.assetid: 31c20e0e-4cdf-49b4-8220-d726130aad2b
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# CurrentScheduler (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Representa una abstracción para el programador actual asociado al contexto de la llamada.  
  
## Sintaxis  
  
```  
class CurrentScheduler;  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CurrentScheduler::Create \(Método\)](../Topic/CurrentScheduler::Create%20Method.md)|Crea un nuevo programador cuyo comportamiento se describe en el parámetro `_Policy` y lo asocia al contexto de la llamada.  El programador creado recientemente se volverá el programador actual para el contexto de la llamada.|  
|[CurrentScheduler::CreateScheduleGroup \(Método\)](../Topic/CurrentScheduler::CreateScheduleGroup%20Method.md)|Sobrecargado.  Crea un nuevo grupo de programación dentro del programador asociado al contexto de la llamada.  La versión que toma el parámetro `_Placement` produce tareas dentro del grupo recién creado de programación de ser perjudicado para ejecutarse en la ubicación especificada por ese parámetro.|  
|[CurrentScheduler::Detach \(Método\)](../Topic/CurrentScheduler::Detach%20Method.md)|Desasocia el programador del contexto de la llamada y restaura el programador asociado anteriormente como programador actual, si existe.  Cuando este método vuelve, el contexto de la llamada a continuación es administrado por el programador que se adjuntó previamente al contexto mediante `CurrentScheduler::Create` o el método de `Scheduler::Attach` .|  
|[CurrentScheduler::Get \(Método\)](../Topic/CurrentScheduler::Get%20Method.md)|Devuelve un puntero al programador asociado con el contexto de la llamada, que también se conoce como el programador actual.|  
|[CurrentScheduler::GetNumberOfVirtualProcessors \(Método\)](../Topic/CurrentScheduler::GetNumberOfVirtualProcessors%20Method.md)|Devuelve el número actual de procesadores virtuales para el programador asociado al contexto de la llamada.|  
|[CurrentScheduler::GetPolicy \(Método\)](../Topic/CurrentScheduler::GetPolicy%20Method.md)|Devuelve una copia de la directiva con la que se creó el programador actual.|  
|[CurrentScheduler::Id \(Método\)](../Topic/CurrentScheduler::Id%20Method.md)|Devuelve un identificador único para el programador actual.|  
|[CurrentScheduler::IsAvailableLocation \(Método\)](../Topic/CurrentScheduler::IsAvailableLocation%20Method.md)|Determina si una ubicación determinada está disponible en el programador actual.|  
|[CurrentScheduler::RegisterShutdownEvent \(Método\)](../Topic/CurrentScheduler::RegisterShutdownEvent%20Method.md)|Hace que el controlador de eventos de Windows pasado en el parámetro `_ShutdownEvent` se señalice cuando el planificador asociado con el contexto actual se cierra y se destruye.  En el momento en que se señala el evento, todo el trabajo que está programado para el programador ha finalizado.  Los eventos de cierre varios se pueden registrar con este método.|  
|[CurrentScheduler::ScheduleTask \(Método\)](../Topic/CurrentScheduler::ScheduleTask%20Method.md)|Sobrecargado.  Programa una tarea ligera dentro del programador asociado al contexto de la llamada.  La tarea ligera se escribirá en un grupo de programación determinado por el tiempo de ejecución.  La versión que toma el parámetro `_Placement` hace que la tarea se perjudicado para ejecutarse en la ubicación especificada.|  
  
## Comentarios  
 Si no hay ningún programador \(vea [Programador](../../../parallel/concrt/reference/scheduler-class.md)\) asociado al contexto de la llamada, muchos métodos dentro de la clase `CurrentScheduler` producirán datos adjuntos del programador predeterminado del proceso.  Esto también puede implicar que el programador predeterminado del proceso se cree durante este tipo de llamada.  
  
## Jerarquía de herencia  
 `CurrentScheduler`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler \(Clase\)](../../../parallel/concrt/reference/scheduler-class.md)   
 [PolicyElementKey \(Enumeración\)](../Topic/PolicyElementKey%20Enumeration.md)   
 [Programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)