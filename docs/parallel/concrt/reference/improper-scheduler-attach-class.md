---
title: "improper_scheduler_attach (Clase) | Microsoft Docs"
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
  - "concrt/concurrency::improper_scheduler_attach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "improper_scheduler_attach (clase)"
ms.assetid: 5a76da0a-091b-4748-8f62-b3a28f674f9e
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# improper_scheduler_attach (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando se llama al método `Attach` en un objeto `Scheduler` que ya se ha adjuntado al contexto actual.  
  
## Sintaxis  
  
```  
class improper_scheduler_attach : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[improper\_scheduler\_attach::improper\_scheduler\_attach \(Constructor\)](../Topic/improper_scheduler_attach::improper_scheduler_attach%20Constructor.md)|Sobrecargado.  Construye un objeto `improper_scheduler_attach`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `improper_scheduler_attach`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler \(Clase\)](../../../parallel/concrt/reference/scheduler-class.md)   
 [Scheduler::Attach \(Método\)](../Topic/Scheduler::Attach%20Method.md)