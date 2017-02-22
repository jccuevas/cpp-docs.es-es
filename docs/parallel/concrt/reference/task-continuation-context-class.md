---
title: "task_continuation_context (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ppltasks/concurrency::task_continuation_context"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "task_continuation_context (clase)"
ms.assetid: 1fb5a76a-3682-45c2-a615-8b6b527741f0
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# task_continuation_context (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `task_continuation_context` permite especificar dónde se desea que se ejecute una continuación.  Solo es de utilidad utilizar esta clase desde una aplicación de la Tienda Windows.  Para las aplicaciones que no sean de la Tienda Windows, el contexto de ejecución de la continuación de la tarea determina el runtime y no se puede configurar.  
  
## Sintaxis  
  
```  
class task_continuation_context : public details::_ContextCallback;  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[task\_continuation\_context::use\_arbitrary \(Método\)](../Topic/task_continuation_context::use_arbitrary%20Method.md)|Crea un contexto de continuación de tarea que permite que el Runtime elija el contexto de ejecución para una continuación.|  
|[task\_continuation\_context::use\_current \(Método\)](../Topic/task_continuation_context::use_current%20Method.md)|Devuelve un objeto de contexto de continuación de tarea que representa el contexto de ejecución actual.|  
|[task\_continuation\_context::use\_default \(Método\)](../Topic/task_continuation_context::use_default%20Method.md)|Crea el contexto de continuación de tarea predeterminado.|  
  
## Jerarquía de herencia  
 `_ContextCallback`  
  
 `task_continuation_context`  
  
## Requisitos  
 **Encabezado:** ppltasks.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [task Class](http://msdn.microsoft.com/es-es/5389e8a5-5038-40b6-844a-55e9b58ad35f)