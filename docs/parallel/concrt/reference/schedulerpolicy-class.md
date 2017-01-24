---
title: "SchedulerPolicy (Clase) | Microsoft Docs"
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
  - "concrt/concurrency::SchedulerPolicy"
  - "concrtrm/concurrency::SchedulerPolicy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SchedulerPolicy (clase)"
ms.assetid: bcebf51a-65f8-45a3-809b-d1ff93527dc4
caps.latest.revision: 22
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SchedulerPolicy (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `SchedulerPolicy` contiene un conjunto de pares clave\-valor, uno para cada elemento de directiva, que controla el comportamiento de una instancia del programador.  
  
## Sintaxis  
  
```  
class SchedulerPolicy;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SchedulerPolicy::SchedulerPolicy \(Constructor\)](../Topic/SchedulerPolicy::SchedulerPolicy%20Constructor.md)|Sobrecargado.  Construye una nueva directiva del programador y la llena con valores para [claves de directiva](../Topic/PolicyElementKey%20Enumeration.md) admitidas por programadores del Runtime de simultaneidad y el Administrador de recursos.|  
|[SchedulerPolicy::~SchedulerPolicy \(Destructor\)](../Topic/SchedulerPolicy::~SchedulerPolicy%20Destructor.md)|Destruye una directiva de programador.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SchedulerPolicy::GetPolicyValue \(Método\)](../Topic/SchedulerPolicy::GetPolicyValue%20Method.md)|Recupera el valor de la clave de directiva proporcionado como el parámetro `_Key`.|  
|[SchedulerPolicy::SetConcurrencyLimits \(Método\)](../Topic/SchedulerPolicy::SetConcurrencyLimits%20Method.md)|Simultáneamente establece las directivas `MaxConcurrency` y `MinConcurrency` en el objeto `SchedulerPolicy`.|  
|[SchedulerPolicy::SetPolicyValue \(Método\)](../Topic/SchedulerPolicy::SetPolicyValue%20Method.md)|Establece el valor de la clave de directiva proporcionado como el parámetro `_Key` y devuelve el valor anterior.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SchedulerPolicy::operator\= \(Operador\)](../Topic/SchedulerPolicy::operator=%20Operator.md)|Asigna la directiva de programador a partir de otra directiva de programador.|  
  
## Comentarios  
 Para obtener más información sobre las directivas que se pueden controlar usando la clase `SchedulerPolicy`, vea [PolicyElementKey \(Enumeración\)](../Topic/PolicyElementKey%20Enumeration.md).  
  
## Jerarquía de herencia  
 `SchedulerPolicy`  
  
## Requisitos  
 **Encabezado:** concrt.h, concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [PolicyElementKey \(Enumeración\)](../Topic/PolicyElementKey%20Enumeration.md)   
 [CurrentScheduler \(Clase\)](../../../parallel/concrt/reference/currentscheduler-class.md)   
 [Scheduler \(Clase\)](../../../parallel/concrt/reference/scheduler-class.md)   
 [Programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)