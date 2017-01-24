---
title: "task_options (Clase) (Runtime de simultaneidad) | Microsoft Docs"
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
  - "ppltasks/concurrency::task_options"
dev_langs: 
  - "C++"
ms.assetid: f93d146b-70f7-46ec-8c2f-c33b8bb0af69
caps.latest.revision: 7
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# task_options (Clase) (Runtime de simultaneidad)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Representa las opciones permitidas para crear una tarea  
  
## Sintaxis  
  
```  
class task_options;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[task\_options::task\_options \(Constructor\) \(Runtime de simultaneidad\)](../Topic/task_options::task_options%20Constructor%20\(Concurrency%20Runtime\).md)|Sobrecargado.  Lista predeterminado de opciones de creación de tareas|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[task\_options::get\_cancellation\_token \(Método\) \(Runtime de simultaneidad\)](../Topic/task_options::get_cancellation_token%20Method%20\(Concurrency%20Runtime\).md)|Devuelve el token de cancelación|  
|[task\_options::get\_continuation\_context \(Método\) \(Runtime de simultaneidad\)](../Topic/task_options::get_continuation_context%20Method%20\(Concurrency%20Runtime\).md)|Devuelve el contexto de continuación|  
|[task\_options::get\_scheduler \(Método\) \(Runtime de simultaneidad\)](../Topic/task_options::get_scheduler%20Method%20\(Concurrency%20Runtime\).md)|Devuelve el programador|  
|[task\_options::has\_cancellation\_token \(Método\) \(Runtime de simultaneidad\)](../Topic/task_options::has_cancellation_token%20Method%20\(Concurrency%20Runtime\).md)|Indica si el usuario especificó un token de cancelación|  
|[task\_options::has\_scheduler \(Método\) \(Runtime de simultaneidad\)](../Topic/task_options::has_scheduler%20Method%20\(Concurrency%20Runtime\).md)|Indica si se especificó un programador por el usuario|  
|[task\_options::set\_cancellation\_token \(Método\) \(Runtime de simultaneidad\)](../Topic/task_options::set_cancellation_token%20Method%20\(Concurrency%20Runtime\).md)|Establece el token determinado en las opciones|  
|[task\_options::set\_continuation\_context \(Método\) \(Runtime de simultaneidad\)](../Topic/task_options::set_continuation_context%20Method%20\(Concurrency%20Runtime\).md)|Establece el contexto de continuación determinado en las opciones|  
  
## Jerarquía de herencia  
 `task_options`  
  
## Requisitos  
 **Encabezado:** ppltasks.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)