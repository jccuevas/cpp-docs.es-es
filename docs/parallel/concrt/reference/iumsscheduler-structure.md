---
title: "IUMSScheduler (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::IUMSScheduler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IUMSScheduler (estructura)"
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# IUMSScheduler (Estructura)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Una interfaz a una abstracción de un programador de trabajo que desea que el Administrador de recursos del runtime de simultaneidad controle los subprocesos programables de modo de usuario \(UMS\).  El Administrador de recursos usa esta interfaz para comunicarse con los programadores de subprocesos UMS.  La interfaz `IUMSScheduler` hereda de la interfaz `IScheduler`.  
  
## Sintaxis  
  
```  
struct IUMSScheduler : public IScheduler;  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IUMSScheduler::SetCompletionList \(Método\)](../Topic/IUMSScheduler::SetCompletionList%20Method.md)|Asigna una interfaz `IUMSCompletionList` a un programador de subproceso de UMS.|  
  
## Comentarios  
 Si está implementando un programador personalizado que comunica con el administrador de recursos, y desea que su programador controle los subprocesos programables en modo usuario \(UMS\) en lugar de subprocesos de Win32 ordinarios, debería proporcionar una implementación de la interfaz `IUMSScheduler`.  Además, debería establecer el valor de directiva de la clave de la directiva del programador `SchedulerKind` para que sea `UmsThreadDefault`.  Si la directiva especifica el subproceso de UMS, la interfaz `IScheduler` que se pasa como un parámetro al método [IResourceManager::RegisterScheduler](../Topic/IResourceManager::RegisterScheduler%20Method.md) debe ser una interfaz `IUMSScheduler`.  
  
 El administrador de recursos puede pasar subprocesos UMS sólo en los sistemas operativos que tienen la característica UMS. Los sistemas operativos de 64 bits con versión de Windows 7 y superior son compatibles con subprocesos UMS.  Si crea una directiva del programador con la clave `SchedulerKind` establecida en el valor `UmsThreadDefault` y la plataforma subyacente no admite UMS, el valor de la clave `SchedulerKind` de esa directiva se cambiará al valor `ThreadScheduler`.  Debería volver leer siempre este valor de directiva antes de esperar recibir subprocesos UMS.  
  
 La interfaz `IUMSScheduler` es uno de los extremos de un canal bidireccional de comunicación entre un programador y el administrador de recursos.  Las interfaces `ISchedulerProxy` e `IResourceManager`, implementadas por el administrador de recursos, representan el otro extremo.  
  
## Jerarquía de herencia  
 [IScheduler](../../../parallel/concrt/reference/ischeduler-structure.md)  
  
 `IUMSScheduler`  
  
## Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [PolicyElementKey \(Enumeración\)](../Topic/PolicyElementKey%20Enumeration.md)   
 [IScheduler \(Estructura\)](../../../parallel/concrt/reference/ischeduler-structure.md)   
 [IUMSCompletionList \(Estructura\)](../../../parallel/concrt/reference/iumscompletionlist-structure.md)   
 [IResourceManager \(Estructura\)](../../../parallel/concrt/reference/iresourcemanager-structure.md)