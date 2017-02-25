---
title: "improper_scheduler_detach (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::improper_scheduler_detach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "improper_scheduler_detach (clase)"
ms.assetid: 30132102-c900-4951-a470-b63b4e3aa2d2
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# improper_scheduler_detach (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando se llama al método `CurrentScheduler::Detach` en un contexto que no se ha adjuntado a ningún programador mediante el método `Attach` de un objeto `Scheduler`.  
  
## Sintaxis  
  
```  
class improper_scheduler_detach : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[improper\_scheduler\_detach::improper\_scheduler\_detach \(Constructor\)](../Topic/improper_scheduler_detach::improper_scheduler_detach%20Constructor.md)|Sobrecargado.  Construye un objeto `improper_scheduler_detach`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `improper_scheduler_detach`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler \(Clase\)](../../../parallel/concrt/reference/scheduler-class.md)   
 [CurrentScheduler::Detach \(Método\)](../Topic/CurrentScheduler::Detach%20Method.md)   
 [Scheduler::Attach \(Método\)](../Topic/Scheduler::Attach%20Method.md)