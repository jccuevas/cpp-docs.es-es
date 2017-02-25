---
title: "invalid_scheduler_policy_thread_specification (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::invalid_scheduler_policy_thread_specification"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_scheduler_policy_thread_specification (clase)"
ms.assetid: 2d0fafb2-18f8-4284-8040-3db640d33303
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# invalid_scheduler_policy_thread_specification (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando se realiza un intento para establecer los límites de simultaneidad de un objeto `SchedulerPolicy`, de tal forma que el valor de la clave `MinConcurrency` es menor que el valor de la clave `MaxConcurrency`.  
  
## Sintaxis  
  
```  
class invalid_scheduler_policy_thread_specification : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[invalid\_scheduler\_policy\_thread\_specification::invalid\_scheduler\_policy\_thread\_specification \(Constructor\)](../Topic/invalid_scheduler_policy_thread_specification::invalid_scheduler_policy_thread_specification%20Constructor.md)|Sobrecargado.  Construye un objeto `invalid_scheduler_policy_value`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `invalid_scheduler_policy_thread_specification`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [SchedulerPolicy \(Clase\)](../../../parallel/concrt/reference/schedulerpolicy-class.md)   
 [PolicyElementKey \(Enumeración\)](../Topic/PolicyElementKey%20Enumeration.md)   
 [SchedulerPolicy::SetConcurrencyLimits \(Método\)](../Topic/SchedulerPolicy::SetConcurrencyLimits%20Method.md)