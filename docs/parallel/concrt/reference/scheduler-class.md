---
title: "Scheduler (Clase) | Microsoft Docs"
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
  - "concrt/concurrency::Scheduler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Scheduler (clase)"
ms.assetid: 34cf7961-048d-4852-8a5c-a32f823e3506
caps.latest.revision: 19
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Scheduler (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Representa una abstracción para un programador del runtime de simultaneidad.  
  
## Sintaxis  
  
```  
class Scheduler;  
```  
  
## Miembros  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Scheduler::Scheduler \(Constructor\)](../Topic/Scheduler::Scheduler%20Constructor.md)|Un objeto de la clase `Scheduler` solo se puede crear usando los métodos de generador o implícitamente.|  
|[Scheduler::~Scheduler \(Destructor\)](../Topic/Scheduler::~Scheduler%20Destructor.md)|Un objeto de la clase `Scheduler` se destruye implícitamente cuando todas las referencias externas al mismo dejan de existir.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Scheduler::Attach \(Método\)](../Topic/Scheduler::Attach%20Method.md)|Adjunta el programador al contexto de la llamada.  Una vez que vuelva este método, el programador administra el contexto de la llamada y el programador se convierte en el programador actual.|  
|[Scheduler::Create \(Método\)](../Topic/Scheduler::Create%20Method.md)|Crea un nuevo programador cuyo comportamiento se describe en el parámetro `_Policy`, coloca una referencia inicial en el programador y le devuelve un puntero.|  
|[Scheduler::CreateScheduleGroup \(Método\)](../Topic/Scheduler::CreateScheduleGroup%20Method.md)|Sobrecargado.  Crea un nuevo grupo de programación dentro del programador.  La versión que toma el parámetro `_Placement` produce tareas dentro del grupo recién creado de programación de ser perjudicado para ejecutarse en la ubicación especificada por ese parámetro.|  
|[Scheduler::GetNumberOfVirtualProcessors \(Método\)](../Topic/Scheduler::GetNumberOfVirtualProcessors%20Method.md)|Devuelve el número actual de procesadores virtuales para el programador.|  
|[Scheduler::GetPolicy \(Método\)](../Topic/Scheduler::GetPolicy%20Method.md)|Devuelve una copia de la directiva con la que se creó el programador.|  
|[Scheduler::Id \(Método\)](../Topic/Scheduler::Id%20Method.md)|Devuelve un identificador único para el programador.|  
|[Scheduler::IsAvailableLocation \(Método\)](../Topic/Scheduler::IsAvailableLocation%20Method.md)|Determina si una ubicación determinada está disponible en el programador.|  
|[Scheduler::Reference \(Método\)](../Topic/Scheduler::Reference%20Method.md)|Incrementa el recuento de referencias del programador.|  
|[Scheduler::RegisterShutdownEvent \(Método\)](../Topic/Scheduler::RegisterShutdownEvent%20Method.md)|Hace que el controlador de eventos de Windows pasado en el parámetro `_Event` se señalice cuando el planificador se cierra y se destruye.  En el momento en que se señala el evento, todo el trabajo que está programado para el programador ha finalizado.  Los eventos de cierre varios se pueden registrar con este método.|  
|[Scheduler::Release \(Método\)](../Topic/Scheduler::Release%20Method.md)|Disminuye el recuento de referencias del programador.|  
|[Scheduler::ResetDefaultSchedulerPolicy \(Método\)](../Topic/Scheduler::ResetDefaultSchedulerPolicy%20Method.md)|Restablece la directiva predeterminada del programador al valor predeterminado de tiempo de ejecución.  La próxima vez crean un programador predeterminado, se utiliza la configuración de la directiva del valor predeterminado del tiempo de ejecución.|  
|[Scheduler::ScheduleTask \(Método\)](../Topic/Scheduler::ScheduleTask%20Method.md)|Sobrecargado.  Programa una tarea ligera dentro del programador.  La tarea ligera se escribirá en un grupo de programación determinado por el tiempo de ejecución.  La versión que toma el parámetro `_Placement` hace que la tarea se perjudicado para ejecutarse en la ubicación especificada.|  
|[Scheduler::SetDefaultSchedulerPolicy \(Método\)](../Topic/Scheduler::SetDefaultSchedulerPolicy%20Method.md)|Permite usar una directiva definida por el usuario para crear el programador predeterminado.  Puede llamar a este método cuando ningún programador predeterminado existe dentro del proceso.  Después de que se haya establecido una directiva predeterminada, permanece en vigor hasta la llamada válida siguiente a `SetDefaultSchedulerPolicy` o al método de [ResetDefaultSchedulerPolicy](../Topic/Scheduler::ResetDefaultSchedulerPolicy%20Method.md) .|  
  
## Comentarios  
 El programador del runtime de simultaneidad usa los contextos de ejecución, que se asignan a los contextos de ejecución del sistema operativo, como un subproceso, para ejecutar el trabajo en cola al por la aplicación.  En cualquier momento, el nivel de simultaneidad de un programador es igual al número de procesador virtual que le ha concedido el administrador de recursos.  Un procesador virtual es una abstracción para un recurso de procesamiento y se asigna a un subproceso del hardware en el sistema subyacente.  Solo se puede ejecutar un único contexto del programador en un procesador virtual a una hora determinada.  
  
 El runtime de simultaneidad creará un programador predeterminado por proceso para ejecutar trabajo paralelo.  Además puede crear dispone de las instancias de programador y para se manipulan mediante esta clase.  
  
## Jerarquía de herencia  
 `Scheduler`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler Class](../../../parallel/concrt/reference/scheduler-class.md)   
 [PolicyElementKey \(Enumeración\)](../Topic/PolicyElementKey%20Enumeration.md)   
 [Programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)