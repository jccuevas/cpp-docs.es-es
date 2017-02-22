---
title: "nested_scheduler_missing_detach (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::nested_scheduler_missing_detach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nested_scheduler_missing_detach (clase)"
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# nested_scheduler_missing_detach (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando el runtime de simultaneidad detecta que se dejó de llamar al método `CurrentScheduler::Detach` en un contexto adjunto a un segundo programador mediante el método `Attach` del objeto `Scheduler`.  
  
## Sintaxis  
  
```  
class nested_scheduler_missing_detach : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[nested\_scheduler\_missing\_detach::nested\_scheduler\_missing\_detach \(Constructor\)](../Topic/nested_scheduler_missing_detach::nested_scheduler_missing_detach%20Constructor.md)|Sobrecargado.  Construye un objeto `nested_scheduler_missing_detach`.|  
  
## Comentarios  
 Esta excepción se produce cuando se anida una dentro de otra scheduler llamando al método de `Attach` de un objeto de `Scheduler` en un contexto que se ya posee por o se asocia a otro programador.  El runtime de simultaneidad produce esta excepción de forma oportuna cuando puede detectar el escenario como una ayuda para a localizar el problema.  No todas las instancias que no especifican la llamada al método `CurrentScheduler::Detach` producen esta excepción.  
  
## Jerarquía de herencia  
 `exception`  
  
 `nested_scheduler_missing_detach`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler \(Clase\)](../../../parallel/concrt/reference/scheduler-class.md)   
 [CurrentScheduler::Detach \(Método\)](../Topic/CurrentScheduler::Detach%20Method.md)   
 [Scheduler::Attach \(Método\)](../Topic/Scheduler::Attach%20Method.md)