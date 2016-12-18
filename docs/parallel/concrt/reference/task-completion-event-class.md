---
title: "task_completion_event (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ppltasks/concurrency::task_completion_event"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "task_completion_event (clase)"
ms.assetid: fb19ed98-f245-48dc-9ba5-487ba879b28a
caps.latest.revision: 11
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# task_completion_event (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `task_completion_event` permite retrasar la ejecución de una tarea hasta que se satisfaga una condición, o iniciar una tarea en respuesta a un evento externo.  
  
## Sintaxis  
  
```  
template<  
   typename _ResultType  
>  
class task_completion_event;  
  
template<>  
class task_completion_event<void>;  
```  
  
#### Parámetros  
 `_ResultType`  
 El tipo de resultado de esta clase `task_completion_event`.  
  
 `T`  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[task\_completion\_event::task\_completion\_event \(Constructor\)](../Topic/task_completion_event::task_completion_event%20Constructor.md)|Construye un objeto `task_completion_event`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[task\_completion\_event::set \(Método\)](../Topic/task_completion_event::set%20Method.md)|Sobrecargado.  Establece el evento de finalización de la tarea.|  
|[task\_completion\_event::set\_exception \(Método\)](../Topic/task_completion_event::set_exception%20Method.md)|Sobrecargado.  Propaga una excepción a todas las tareas asociadas con este evento.|  
  
## Comentarios  
 Use una tarea creada a partir de un evento de finalización de la tarea cuando su escenario requiere la creación de una tarea que completar, y así tendrá las continuaciones programadas para su ejecución en el futuro.  `task_completion_event` debe tener el mismo tipo que la tarea que se crea, así como poder llamar al método set en el evento de finalización de la tarea con un valor de ese tipo, lo que provocará que se complete la tarea asociada y proporcionará ese valor como resultado de sus continuaciones.  
  
 Si el evento de finalización de la tarea nunca se señala, cualquier tarea creada a partir de ese evento se cancelará cuando se destruye.  
  
 El objeto `task_completion_event` se comporta como un puntero inteligente y debe pasar por valor.  
  
## Jerarquía de herencia  
 `task_completion_event`  
  
## Requisitos  
 **Encabezado:** ppltasks.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task Class](http://msdn.microsoft.com/es-es/5389e8a5-5038-40b6-844a-55e9b58ad35f)