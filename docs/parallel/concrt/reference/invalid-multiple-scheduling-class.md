---
title: "invalid_multiple_scheduling (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::invalid_multiple_scheduling"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_multiple_scheduling (clase)"
ms.assetid: e9a47cb7-a778-4df7-92b0-3752119fd4c7
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# invalid_multiple_scheduling (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando un objeto `task_handle` se programa varias veces mediante el método `run` de un objeto `task_group` o `structured_task_group` sin una llamada que se interponga a los métodos `wait` o `run_and_wait`.  
  
## Sintaxis  
  
```  
class invalid_multiple_scheduling : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[invalid\_multiple\_scheduling::invalid\_multiple\_scheduling \(Constructor\)](../Topic/invalid_multiple_scheduling::invalid_multiple_scheduling%20Constructor.md)|Sobrecargado.  Construye un objeto `invalid_multiple_scheduling`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `invalid_multiple_scheduling`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task\_handle \(Clase\)](../../../parallel/concrt/reference/task-handle-class.md)   
 [task\_group \(Clase\)](../Topic/task_group%20Class.md)   
 [task\_group::run \(Método\)](../Topic/task_group::run%20Method.md)   
 [task\_group::wait \(Método\)](../Topic/task_group::wait%20Method.md)   
 [task\_group::run\_and\_wait \(Método\)](../Topic/task_group::run_and_wait%20Method.md)   
 [structured\_task\_group \(Clase\)](../../../parallel/concrt/reference/structured-task-group-class.md)   
 [structured\_task\_group::run \(Método\)](../Topic/structured_task_group::run%20Method.md)   
 [structured\_task\_group::wait \(Método\)](../Topic/structured_task_group::wait%20Method.md)   
 [structured\_task\_group::run\_and\_wait \(Método\)](../Topic/structured_task_group::run_and_wait%20Method.md)