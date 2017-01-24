---
title: "IThreadProxy (Estructura) | Microsoft Docs"
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
  - "concrtrm/concurrency::IThreadProxy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IThreadProxy (estructura)"
ms.assetid: feb89241-a555-4e61-ad48-40add54daeca
caps.latest.revision: 21
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IThreadProxy (Estructura)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Una abstracción para un subproceso de ejecución.  Dependiendo de la clave de directiva `SchedulerType` del programador que se crea, el Administrador de recursos concederá al usuario un proxy del subproceso que está respaldado por un subproceso de Win32 normal o por un subproceso programable de modo de usuario \(UMS\).  Los subprocesos UMS se admiten en sistemas operativos de 64 bits con Windows 7 o una versión posterior.  
  
## Sintaxis  
  
```  
struct IThreadProxy;  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IThreadProxy::GetId \(Método\)](../Topic/IThreadProxy::GetId%20Method.md)|Devuelve un identificador único para el proxy del subproceso.|  
|[IThreadProxy::SwitchOut \(Método\)](../Topic/IThreadProxy::SwitchOut%20Method.md)|Desasocia el contexto de la raíz del procesador virtual subyacente.|  
|[IThreadProxy::SwitchTo \(Método\)](../Topic/IThreadProxy::SwitchTo%20Method.md)|Realiza un cambio de contexto cooperativo del contexto actualmente en ejecución a uno diferente.|  
|[IThreadProxy::YieldToSystem \(Método\)](../Topic/IThreadProxy::YieldToSystem%20Method.md)|Hace que el subproceso que realiza la llamada proporcione la ejecución a otro subproceso que está listo para ejecutarse en el procesador actual.  El sistema operativo selecciona el siguiente subproceso que se va a ejecutar.|  
  
## Comentarios  
 Los proxy del subproceso se acoplan en los contextos de ejecución representados por la interfaz `IExecutionContext` como un medio de envío de trabajo.  
  
## Jerarquía de herencia  
 `IThreadProxy`  
  
## Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IExecutionContext \(Estructura\)](../../../parallel/concrt/reference/iexecutioncontext-structure.md)   
 [IScheduler \(Estructura\)](../../../parallel/concrt/reference/ischeduler-structure.md)   
 [IVirtualProcessorRoot \(Estructura\)](../../../parallel/concrt/reference/ivirtualprocessorroot-structure.md)