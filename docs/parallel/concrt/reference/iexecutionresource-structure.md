---
title: "IExecutionResource (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::IExecutionResource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IExecutionResource (estructura)"
ms.assetid: 6b27042b-b98c-4f7f-b831-566950af84cd
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# IExecutionResource (Estructura)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Una abstracción para un subproceso del hardware.  
  
## Sintaxis  
  
```  
struct IExecutionResource;  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IExecutionResource::CurrentSubscriptionLevel \(Método\)](../Topic/IExecutionResource::CurrentSubscriptionLevel%20Method.md)|Devuelve el número de raíces del procesador virtual activadas y los subprocesos externos actualmente subscritos asociados al subproceso de hardware subyacente que representa este recurso de ejecución.|  
|[IExecutionResource::GetExecutionResourceId \(Método\)](../Topic/IExecutionResource::GetExecutionResourceId%20Method.md)|Devuelve un identificador único para el subproceso del hardware que representa este recurso de ejecución.|  
|[IExecutionResource::GetNodeId \(Método\)](../Topic/IExecutionResource::GetNodeId%20Method.md)|Devuelve un identificador único para el nodo de procesador la que pertenece este recurso de ejecución.|  
|[IExecutionResource::Remove \(Método\)](../Topic/IExecutionResource::Remove%20Method.md)|Devuelve este recurso de ejecución al administrador de recursos.|  
  
## Comentarios  
 Los recursos de ejecución pueden ser independientes o asociados a raíces del procesador virtuales.  Se crea un recurso de ejecución independiente cuando un subproceso en su aplicación crea una suscripción del subproceso.  Los métodos [ISchedulerProxy::SubscribeThread](../Topic/ISchedulerProxy::SubscribeCurrentThread%20Method.md) e [ISchedulerProxy::RequestInitialVirtualProcessors](../Topic/ISchedulerProxy::RequestInitialVirtualProcessors%20Method.md) crean suscripciones del subproceso y devuelven una interfaz `IExecutionResource` que representa la suscripción.  Crear una suscripción del subproceso es una manera de informar al administrador de recursos que un subproceso determinado participará en el trabajo de la cola de un programador, junto al administrador de recursos de raíces del procesador virtual asignado al programador.  El administrador de recursos usa la información para evitar suscripciones excesivas de subprocesos de hardware donde es posible.  
  
## Jerarquía de herencia  
 `IExecutionResource`  
  
## Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IVirtualProcessorRoot \(Estructura\)](../../../parallel/concrt/reference/ivirtualprocessorroot-structure.md)   
 [ISchedulerProxy::SubscribeCurrentThread \(Método\)](../Topic/ISchedulerProxy::SubscribeCurrentThread%20Method.md)   
 [ISchedulerProxy::RequestInitialVirtualProcessors \(Método\)](../Topic/ISchedulerProxy::RequestInitialVirtualProcessors%20Method.md)