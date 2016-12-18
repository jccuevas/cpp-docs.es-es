---
title: "invalid_scheduler_policy_value (Clase) | Microsoft Docs"
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
  - "concrt/concurrency::invalid_scheduler_policy_value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_scheduler_policy_value (clase)"
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# invalid_scheduler_policy_value (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando una clave de directiva de un objeto `SchedulerPolicy` se establece en un valor no válido para esa clave.  
  
## Sintaxis  
  
```  
class invalid_scheduler_policy_value : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[invalid\_scheduler\_policy\_value::invalid\_scheduler\_policy\_value \(Constructor\)](../Topic/invalid_scheduler_policy_value::invalid_scheduler_policy_value%20Constructor.md)|Sobrecargado.  Construye un objeto `invalid_scheduler_policy_value`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `invalid_scheduler_policy_value`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [SchedulerPolicy \(Clase\)](../../../parallel/concrt/reference/schedulerpolicy-class.md)   
 [PolicyElementKey \(Enumeración\)](../Topic/PolicyElementKey%20Enumeration.md)   
 [SchedulerPolicy::SetPolicyValue \(Método\)](../Topic/SchedulerPolicy::SetPolicyValue%20Method.md)   
 [SchedulerPolicy::SetConcurrencyLimits \(Método\)](../Topic/SchedulerPolicy::SetConcurrencyLimits%20Method.md)