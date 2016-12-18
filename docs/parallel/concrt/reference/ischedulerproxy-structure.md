---
title: "ISchedulerProxy (Estructura) | Microsoft Docs"
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
  - "concrtrm/concurrency::ISchedulerProxy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ISchedulerProxy (estructura)"
ms.assetid: af416973-7a1c-4c30-aa3b-4161c2aaea54
caps.latest.revision: 18
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ISchedulerProxy (Estructura)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La interfaz por la que los programadores se comunican con el Administrador de recursos del runtime de simultaneidad para negociar la asignación de recursos.  
  
## Sintaxis  
  
```  
struct ISchedulerProxy;  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ISchedulerProxy::BindContext \(Método\)](../Topic/ISchedulerProxy::BindContext%20Method.md)|Asocia un contexto de ejecución a un proxy del subproceso, si aún no está asociado a uno.|  
|[ISchedulerProxy::CreateOversubscriber \(Método\)](../Topic/ISchedulerProxy::CreateOversubscriber%20Method.md)|Crea una nueva raíz del procesador virtual en el subproceso del hardware asociado a un recurso de ejecución existente.|  
|[ISchedulerProxy::RequestInitialVirtualProcessors \(Método\)](../Topic/ISchedulerProxy::RequestInitialVirtualProcessors%20Method.md)|Solicita una asignación inicial de raíces del procesador virtual.  Cada raíz del procesador virtual representa la capacidad de ejecutar un subproceso que puede realizar el trabajo para el programador.|  
|[ISchedulerProxy::Shutdown \(Método\)](../Topic/ISchedulerProxy::Shutdown%20Method.md)|Notifica al administrador de recursos que el programador va a cerrarse.  Esto provocará que el administrador de recursos reclame inmediatamente todos los recursos concedidos al programador.|  
|[ISchedulerProxy::SubscribeCurrentThread \(Método\)](../Topic/ISchedulerProxy::SubscribeCurrentThread%20Method.md)|Registra el subproceso actual con el administrador de recursos, asociándolo a este programador.|  
|[ISchedulerProxy::UnbindContext \(Método\)](../Topic/ISchedulerProxy::UnbindContext%20Method.md)|Desasocia un proxy del subproceso del contexto de ejecución especificado por el parámetro `pContext` y lo devuelve al grupo libre del generador de proxy de subproceso.  Se puede llamar a este método sólo en un contexto de ejecución que se enlazó a través del método [ISchedulerProxy::BindContext](../Topic/ISchedulerProxy::BindContext%20Method.md) y no se ha iniciado todavía a través de ser el parámetro `pContext` de una llamada al método [de IThreadProxy::SwitchTo](../Topic/IThreadProxy::SwitchTo%20Method.md).|  
  
## Comentarios  
 El administrador de recursos pasa una interfaz `ISchedulerProxy` a cada programador que se registra con él mediante el método [IResourceManager::RegisterScheduler](../Topic/IResourceManager::RegisterScheduler%20Method.md).  
  
## Jerarquía de herencia  
 `ISchedulerProxy`  
  
## Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IScheduler \(Estructura\)](../../../parallel/concrt/reference/ischeduler-structure.md)   
 [IThreadProxy \(Estructura\)](../../../parallel/concrt/reference/ithreadproxy-structure.md)   
 [IVirtualProcessorRoot \(Estructura\)](../../../parallel/concrt/reference/ivirtualprocessorroot-structure.md)   
 [IResourceManager \(Estructura\)](../../../parallel/concrt/reference/iresourcemanager-structure.md)