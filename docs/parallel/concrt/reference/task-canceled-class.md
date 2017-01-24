---
title: "task_canceled (Clase) | Microsoft Docs"
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
  - "concrt/concurrency::task_canceled"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "task_canceled (clase)"
ms.assetid: c3f0b234-2cc1-435f-a48e-995f45b190be
caps.latest.revision: 11
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# task_canceled (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción producida por la capa de tareas de PPL para obligar a que se cancele la tarea actual.  También la produce el método `get()` de [task](../Topic/Task%20Class%20-%20Internal%20Members.md) en una tarea cancelada.  
  
## Sintaxis  
  
```  
class task_canceled : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[task\_canceled::task\_canceled \(Constructor\)](../Topic/task_canceled::task_canceled%20Constructor.md)|Sobrecargado.  Construye un objeto `task_canceled`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `task_canceled`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task::get \(Método\)](../Topic/task::get%20Method.md)   
 [cancel\_current\_task \(Función\)](../Topic/cancel_current_task%20Function.md)