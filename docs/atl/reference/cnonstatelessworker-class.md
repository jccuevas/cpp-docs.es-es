---
title: "CNonStatelessWorker Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CNonStatelessWorker<Worker>"
  - "ATL::CNonStatelessWorker"
  - "ATL.CNonStatelessWorker"
  - "CNonStatelessWorker"
  - "ATL::CNonStatelessWorker<Worker>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CNonStatelessWorker class"
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CNonStatelessWorker Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recibe solicitudes de un grupo de subprocesos y las pasa en un objeto worker que se cree y se destruya en cada solicitud.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template <  
class Worker  
>  
class CNonStatelessWorker  
```  
  
#### Parámetros  
 *Trabajo*  
 Una clase de subproceso de trabajo bajo [arquetipo worker](../../atl/reference/worker-archetype.md) adecuado para administrar las solicitudes en cola en [CThreadPool](../../atl/reference/cthreadpool-class.md).  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CNonStatelessWorker::RequestType](../Topic/CNonStatelessWorker::RequestType.md)|implementación de [WorkerArchetype:: RequestType](../Topic/WorkerArchetype::RequestType.md).|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CNonStatelessWorker::Execute](../Topic/CNonStatelessWorker::Execute.md)|implementación de [WorkerArchetype:: Ejecutar](../Topic/WorkerArchetype::Execute.md).|  
|[CNonStatelessWorker::Initialize](../Topic/CNonStatelessWorker::Initialize.md)|implementación de [WorkerArchetype:: Inicialice](../Topic/WorkerArchetype::Initialize.md).|  
|[CNonStatelessWorker::Terminate](../Topic/CNonStatelessWorker::Terminate.md)|implementación de [WorkerArchetype:: terminar](../Topic/WorkerArchetype::Terminate.md).|  
  
## Comentarios  
 esta clase es un subproceso de trabajo simple para el uso con [CThreadPool](../../atl/reference/cthreadpool-class.md).  Esta clase no proporciona ninguna capacidad petición\-que administran su propio.  En su lugar, crea una instancia *de trabajo* por solicitud y delega la implementación de los métodos en esa instancia.  
  
 La ventaja de esta clase es que proporciona una manera cómoda de cambiar el modelo de estado para las clases existentes del subproceso de trabajo.  `CThreadPool` creará un único trabajo mientras dure el subproceso, por lo que si la clase worker contiene el estado, la conservará a través de varias solicitudes.  Simplemente ajustando la clase en la plantilla de `CNonStatelessWorker` antes de utilizarla con `CThreadPool`, la duración worker y estado que contiene se limita a una sola solicitud.  
  
## Requisitos  
 **encabezado:** atlutil.h  
  
## Vea también  
 [CThreadPool Class](../../atl/reference/cthreadpool-class.md)   
 [Worker Archetype](../../atl/reference/worker-archetype.md)   
 [Clases](../../atl/reference/atl-classes.md)