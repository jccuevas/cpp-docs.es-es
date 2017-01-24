---
title: "structured_task_group (Clase) | Microsoft Docs"
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
  - "ppl/concurrency::structured_task_group"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "structured_task_group (clase)"
ms.assetid: 742afa8c-c7b6-482c-b0ba-04c809927b22
caps.latest.revision: 21
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# structured_task_group (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `structured_task_group` representa una colección muy estructurada de trabajos paralelos.  Puede poner en cola tareas individuales paralelas a `structured_task_group` mediante objetos `task_handle`, y esperar a que se completen, o cancelar el grupo de tareas antes de que haya finalizado su ejecución, que anulará cualquier tarea cuya ejecución no haya comenzado.  
  
## Sintaxis  
  
```  
class structured_task_group;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[structured\_task\_group::structured\_task\_group \(Constructor\)](../Topic/structured_task_group::structured_task_group%20Constructor.md)|Sobrecargado.  Crea un nuevo objeto `structured_task_group`.|  
|[structured\_task\_group::~structured\_task\_group \(Destructor\)](../Topic/structured_task_group::~structured_task_group%20Destructor.md)|Destruye un objeto `structured_task_group`.  Se espera que llame al método `run_and_wait` o `wait` en el objeto antes de la ejecución del destructor, a menos que el destructor se esté ejecutando como un resultado del desenredo de pila debido a una excepción.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[structured\_task\_group::cancel \(Método\)](../Topic/structured_task_group::cancel%20Method.md)|Realiza un mayor esfuerzo para intentar cancelar el subárbol de trabajo con raíz en este grupo de tareas.  Cada tarea programada en el grupo de tareas se cancelará transitivamente si es posible.|  
|[structured\_task\_group::is\_canceling \(Método\)](../Topic/structured_task_group::is_canceling%20Method.md)|Informa el llamador si el grupo de tareas está o no actualmente en medio de una cancelación.  Esto no indica necesariamente que el método `cancel` fue llamado en el objeto `structured_task_group` \(aunque sin duda califica este método para devolver `true`\).  Puede darse el caso de que el objeto `structured_task_group` se está ejecutando alineado y un grupo de tareas más arriba en el árbol de trabajo se haya cancelado.  En casos como éstos donde el runtime puede determinar de antemano que la cancelación fluirá a través de este objeto `structured_task_group`, también se devolverá `true`.|  
|[structured\_task\_group::run \(Método\)](../Topic/structured_task_group::run%20Method.md)|Sobrecargado.  Programa una tarea en el objeto `structured_task_group`.  El llamador administra la duración del objeto `task_handle` pasado en el parámetro `_Task_handle`.  La versión que toma el parámetro `_Placement` hace que la tarea se perjudicado para ejecutarse en la ubicación especificada por ese parámetro.|  
|[structured\_task\_group::run\_and\_wait \(Método\)](../Topic/structured_task_group::run_and_wait%20Method.md)|Sobrecargado.  Programa una tarea que se ejecuta alineada en el contexto de la llamada con la ayuda del objeto `structured_task_group` para una compatibilidad de cancelación completa.  Si un objeto `task_handle` se pasa como un parámetro a `run_and_wait`, el llamador es responsable de administrar la duración del objeto `task_handle`.  Después, la función espera hasta que todo el trabajo en el objeto `structured_task_group` se haya completado o cancelado.|  
|[structured\_task\_group::wait \(Método\)](../Topic/structured_task_group::wait%20Method.md)|Espera hasta que todo el trabajo en `structured_task_group` se haya completado o cancelado.|  
  
## Comentarios  
 Hay varias restricciones graves sobre el uso de un objeto `structured_task_group` con el fin de obtener mejoras de rendimiento:  
  
-   Varios subprocesos no pueden usar un único objeto `structured_task_group`.  El subproceso que creó el objeto debe realizar todas las operaciones en un objeto `structured_task_group`.  Las dos excepciones a esta regla son las funciones miembro `cancel` e `is_canceling`.  El objeto no puede estar en la lista de captura de una expresión lambda y se debe usar dentro de una tarea, a menos que la tarea esté utilizando una de las operaciones de cancelación.  
  
-   Todas las tareas programadas en un objeto `structured_task_group` se programan a través del uso de objetos `task_handle` cuya duración debe administrar explícitamente.  
  
-   Varios grupos solo se pueden usar en orden completamente anidado.  Si se declaran dos objetos `structured_task_group`, el segundo que se declara \(el interno\) se debe destruir antes de cualquier método excepto `cancel` o se llama a `is_canceling` en el primero \(el exterior\).  Esta condición es válida tanto en el caso de declarar simplemente varios objetos `structured_task_group` dentro de los mismos o de ámbitos funcionalmente anidados, como en el caso de una tarea que se puso en cola de `structured_task_group` a través de los métodos `run` o `run_and_wait`.  
  
-   A diferencia de la clase `task_group` general, todos los estados en la clase `structured_task_group` son finales.  Después de haber en cola las tareas al grupo y esperadas los para completar, no puede utilizar el mismo grupo.  
  
 Para obtener más información, vea [Paralelismo de tareas](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
## Jerarquía de herencia  
 `structured_task_group`  
  
## Requisitos  
 **Encabezado:** ppl.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task\_group \(Clase\)](../Topic/task_group%20Class.md)   
 [task\_handle \(Clase\)](../../../parallel/concrt/reference/task-handle-class.md)