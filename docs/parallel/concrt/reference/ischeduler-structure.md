---
title: "IScheduler (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::IScheduler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IScheduler (estructura)"
ms.assetid: 471de85a-2b1a-4b6d-ab81-2eff2737161e
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# IScheduler (Estructura)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Una interfaz a una abstracción de un programador de trabajo.  El Administrador de recursos del runtime de simultaneidad usa esta interfaz para comunicarse con programadores de trabajo.  
  
## Sintaxis  
  
```  
struct IScheduler;  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IScheduler::AddVirtualProcessors \(Método\)](../Topic/IScheduler::AddVirtualProcessors%20Method.md)|Proporciona un programador con un conjunto de raíces del procesador virtual para su uso.  Cada interfaz `IVirtualProcessorRoot` representa el derecho para ejecutar un subproceso único que puede realizar el trabajo en nombre del programador.|  
|[IScheduler::GetId \(Método\)](../Topic/IScheduler::GetId%20Method.md)|Devuelve un identificador único para el programador.|  
|[IScheduler::GetPolicy \(Método\)](../Topic/IScheduler::GetPolicy%20Method.md)|Devuelve una copia de la directiva del programador.  Para obtener más información sobre las directivas del programador, vea [SchedulerPolicy](../../../parallel/concrt/reference/schedulerpolicy-class.md).|  
|[IScheduler::NotifyResourcesExternallyBusy \(Método\)](../Topic/IScheduler::NotifyResourcesExternallyBusy%20Method.md)|Notifica a este programador que los subprocesos del hardware representados por el conjunto de raíces del procesador virtual en la matriz `ppVirtualProcessorRoots` se están usando por otros programadores.|  
|[IScheduler::NotifyResourcesExternallyIdle \(Método\)](../Topic/IScheduler::NotifyResourcesExternallyIdle%20Method.md)|Notifica a este programador que los subprocesos del hardware representados por el conjunto de raíces del procesador virtual en la matriz `ppVirtualProcessorRoots` no se están usando por otros programadores.|  
|[IScheduler::RemoveVirtualProcessors \(Método\)](../Topic/IScheduler::RemoveVirtualProcessors%20Method.md)|Inicia la eliminación de raíces del procesador virtual que se asignaron previamente a este programador.|  
|[IScheduler::Statistics \(Método\)](../Topic/IScheduler::Statistics%20Method.md)|Proporciona información relacionada con tasas de llegada y finalización de la tarea, además del cambio en la longitud de cola para un programador.|  
  
## Comentarios  
 Si está implementando un programador personalizado que comunica con el administrador de recursos, debería proporcionar una implementación de la interfaz `IScheduler`.  Esta interfaz es uno de los extremos de un canal bidireccional de comunicación entre un programador y el administrador de recursos.  Las interfaces `ISchedulerProxy` e `IResourceManager`, implementadas por el administrador de recursos, representan el otro extremo.  
  
## Jerarquía de herencia  
 `IScheduler`  
  
## Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [PolicyElementKey \(Enumeración\)](../Topic/PolicyElementKey%20Enumeration.md)   
 [SchedulerPolicy \(Clase\)](../../../parallel/concrt/reference/schedulerpolicy-class.md)   
 [IExecutionContext \(Estructura\)](../../../parallel/concrt/reference/iexecutioncontext-structure.md)   
 [IThreadProxy \(Estructura\)](../../../parallel/concrt/reference/ithreadproxy-structure.md)   
 [IVirtualProcessorRoot \(Estructura\)](../../../parallel/concrt/reference/ivirtualprocessorroot-structure.md)   
 [IResourceManager \(Estructura\)](../../../parallel/concrt/reference/iresourcemanager-structure.md)