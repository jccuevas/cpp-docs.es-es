---
title: "invalid_scheduler_policy_key (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::invalid_scheduler_policy_key"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_scheduler_policy_key (clase)"
ms.assetid: 6a7c42fe-9bc4-4a02-bebb-99fe9ef9817d
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# invalid_scheduler_policy_key (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando una clave no válida o desconocida se pasa a un constructor de objeto `SchedulerPolicy`, o el método `SetPolicyValue` de un objeto `SchedulerPolicy` se pasa a una clave que se debe cambiar mediante otros medios como el método `SetConcurrencyLimits`.  
  
## Sintaxis  
  
```  
class invalid_scheduler_policy_key : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[invalid\_scheduler\_policy\_key::invalid\_scheduler\_policy\_key \(Constructor\)](../Topic/invalid_scheduler_policy_key::invalid_scheduler_policy_key%20Constructor.md)|Sobrecargado.  Construye un objeto `invalid_scheduler_policy_key`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `invalid_scheduler_policy_key`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [SchedulerPolicy \(Clase\)](../../../parallel/concrt/reference/schedulerpolicy-class.md)   
 [PolicyElementKey \(Enumeración\)](../Topic/PolicyElementKey%20Enumeration.md)   
 [SchedulerPolicy::SetPolicyValue \(Método\)](../Topic/SchedulerPolicy::SetPolicyValue%20Method.md)   
 [SchedulerPolicy::SetConcurrencyLimits \(Método\)](../Topic/SchedulerPolicy::SetConcurrencyLimits%20Method.md)