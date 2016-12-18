---
title: "Context (Clase) | Microsoft Docs"
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
  - "concrt/concurrency::Context"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Context (clase)"
ms.assetid: c0d553f3-961d-4ecd-9a29-4fa4351673b8
caps.latest.revision: 20
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Context (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Representa una abstracción para un contexto de ejecución.  
  
## Sintaxis  
  
```  
class Context;  
```  
  
## Miembros  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Context::~Context \(Destructor\)](../Topic/Context::~Context%20Destructor.md)||  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Context::Block \(Método\)](../Topic/Context::Block%20Method.md)|Bloquea el contexto actual.|  
|[Context::CurrentContext \(Método\)](../Topic/Context::CurrentContext%20Method.md)|Devuelve un puntero al contexto actual.|  
|[Context::GetId \(Método\)](../Topic/Context::GetId%20Method.md)|Devuelve un identificador para el contexto que es único dentro del programador al que pertenece el contexto.|  
|[Context::GetScheduleGroupId \(Método\)](../Topic/Context::GetScheduleGroupId%20Method.md)|Devuelve un identificador para el grupo de programación en el que el contexto está trabajando actualmente.|  
|[Context::GetVirtualProcessorId \(Método\)](../Topic/Context::GetVirtualProcessorId%20Method.md)|Devuelve un identificador para el procesador virtual en el que el contexto se está ejecutando actualmente.|  
|[Context::Id \(Método\)](../Topic/Context::Id%20Method.md)|Devuelve un identificador para el contexto actual que es único dentro del programador al que pertenece el contexto actual.|  
|[Context::IsCurrentTaskCollectionCanceling \(Método\)](../Topic/Context::IsCurrentTaskCollectionCanceling%20Method.md)|Devuelve una indicación de si la colección de tareas que actualmente se ejecuta alineada en el contexto actual, está en medio de una cancelación activa \(o lo estará pronto\).|  
|[Context::IsSynchronouslyBlocked \(Método\)](../Topic/Context::IsSynchronouslyBlocked%20Method.md)|Determina si el contexto está o no bloqueado de forma sincrónica.  Se considera que un contexto está bloqueado de forma sincrónica si realizó una acción que condujo al bloqueo explícitamente.|  
|[Context::Oversubscribe \(Método\)](../Topic/Context::Oversubscribe%20Method.md)|Inserta un procesador virtual adicional en un programador para la duración de un bloque de código cuando se invoca en un contexto que se ejecuta en uno de los procesadores virtuales de ese programador.|  
|[Context::ScheduleGroupId \(Método\)](../Topic/Context::ScheduleGroupId%20Method.md)|Devuelve un identificador para el grupo de programación en el que el contexto actual está trabajando.|  
|[Context::Unblock \(Método\)](../Topic/Context::Unblock%20Method.md)|Desbloquea el contexto y hace que se convierta en ejecutable.|  
|[Context::VirtualProcessorId \(Método\)](../Topic/Context::VirtualProcessorId%20Method.md)|Devuelve un identificador para el procesador virtual en el que el contexto actual se está ejecutando.|  
|[Context::Yield \(Método\)](../Topic/Context::Yield%20Method.md)|Genera la ejecución para que otro contexto se pueda ejecutar.  Si no hay ningún otro contexto disponible para dar prioridad, el programador puede dar prioridad a otro subproceso del sistema operativo.|  
  
## Comentarios  
 El programador del runtime de simultaneidad \(vea [Programador](../../../parallel/concrt/reference/scheduler-class.md)\) usa contextos de ejecución para ejecutar el trabajo de cola para su aplicación.  Un subproceso de Win32 es un ejemplo de un contexto de ejecución en un sistema operativo Windows.  
  
 En cualquier momento, el nivel de simultaneidad de un programador es igual al número de procesadores virtuales que le ha concedido el Administrador de recursos.  Un procesador virtual es una abstracción para un recurso de procesamiento y se asigna a un subproceso del hardware en el sistema subyacente.  Solo se puede ejecutar un único contexto del programador en un procesador virtual a una hora determinada.  
  
 El programador es cooperativo por su naturaleza y un contexto de ejecución puede producir su procesador virtual en un contexto diferente en cualquier momento si desea escribir un estado de espera.  Cuando la espera se cumple, no se puede volver a reanudar hasta que un procesador virtual disponible del programador comienza su ejecución.  
  
## Jerarquía de herencia  
 `Context`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler \(Clase\)](../../../parallel/concrt/reference/scheduler-class.md)   
 [Programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)