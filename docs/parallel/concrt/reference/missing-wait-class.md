---
title: "missing_wait (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::missing_wait"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "missing_wait (clase)"
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# missing_wait (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando todavía existen tareas programadas para un objeto `task_group` o `structured_task_group` en el momento que el destructor de objeto se ejecuta.  Nunca se producirá esta excepción si el destructor se alcanza debido al desenredo de pila como el resultado de una excepción.  
  
## Sintaxis  
  
```  
class missing_wait : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[missing\_wait::missing\_wait \(Constructor\)](../Topic/missing_wait::missing_wait%20Constructor.md)|Sobrecargado.  Construye un objeto `missing_wait`.|  
  
## Comentarios  
 En ausencia del flujo de excepción, debe responsabilizarse de llamar o a método `run_and_wait` o `wait` de un objeto `task_group` o `structured_task_group` antes de permitir que ese objeto se destruya.  El runtime produce esta excepción como una indicación de que se olvidó de llamar al método `run_and_wait` o `wait`.  
  
## Jerarquía de herencia  
 `exception`  
  
 `missing_wait`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task\_group \(Clase\)](../Topic/task_group%20Class.md)   
 [task\_group::wait \(Método\)](../Topic/task_group::wait%20Method.md)   
 [task\_group::run\_and\_wait \(Método\)](../Topic/task_group::run_and_wait%20Method.md)   
 [structured\_task\_group \(Clase\)](../../../parallel/concrt/reference/structured-task-group-class.md)   
 [structured\_task\_group::wait \(Método\)](../Topic/structured_task_group::wait%20Method.md)   
 [structured\_task\_group::run\_and\_wait \(Método\)](../Topic/structured_task_group::run_and_wait%20Method.md)