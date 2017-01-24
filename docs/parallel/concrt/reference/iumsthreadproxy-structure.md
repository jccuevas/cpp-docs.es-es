---
title: "IUMSThreadProxy (Estructura) | Microsoft Docs"
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
  - "concrtrm/concurrency::IUMSThreadProxy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IUMSThreadProxy (estructura)"
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IUMSThreadProxy (Estructura)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Una abstracción para un subproceso de ejecución.  Si desea conceder subprocesos programables en modo usuario \(UMS\) al programador, establezca el valor para el elemento de directiva de programador `SchedulerKind` en `UmsThreadDefault` e implemente la interfaz `IUMSScheduler`.  Los subprocesos UMS se admiten únicamente en sistemas operativos de 64 bits con Windows 7 o una versión posterior.  
  
## Sintaxis  
  
```  
struct IUMSThreadProxy : public IThreadProxy;  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IUMSThreadProxy::EnterCriticalRegion \(Método\)](../Topic/IUMSThreadProxy::EnterCriticalRegion%20Method.md)|Se llama para especificar una región crítica.  Dentro de una región crítica, el programador no observará operaciones asincrónicas de bloqueo que se producen en la región.  Esto significa que no repetirán al programador para los errores de página, suspensiones de subprocesos, llamadas a procedimiento asincrónico \(APCs\) de kernel, etc., para un subproceso UMS.|  
|[IUMSThreadProxy::EnterHyperCriticalRegion \(Método\)](../Topic/IUMSThreadProxy::EnterHyperCriticalRegion%20Method.md)|Se llama para especificar una región hipercrítica.  Dentro de una región hipercrítica, el programador no observará ninguna operación de bloqueo que se producen en la región.  Esto significa que no repetirán el programador para bloquear las llamadas de función, intenta bloquean, errores de página, suspensiones de subprocesos, llamadas a procedimiento asincrónico \(APCs\) de adquisición de bloqueo de kernel, etc., para un subproceso UMS.|  
|[IUMSThreadProxy::ExitCriticalRegion \(Método\)](../Topic/IUMSThreadProxy::ExitCriticalRegion%20Method.md)|Se llama para salir de una región crítica.|  
|[IUMSThreadProxy::ExitHyperCriticalRegion \(Método\)](../Topic/IUMSThreadProxy::ExitHyperCriticalRegion%20Method.md)|Se llama para salir de una región hipercrítica.|  
|[IUMSThreadProxy::GetCriticalRegionType \(Método\)](../Topic/IUMSThreadProxy::GetCriticalRegionType%20Method.md)|Devuelve el tipo de región crítica dentro del que se encuentra el proxy del subproceso.  Dado que las regiones híper\- críticas son un superconjunto de regiones críticas, si el código entra en un área crítica y a una región híper\- crítica, `InsideHyperCriticalRegion` se devolverá.|  
  
## Jerarquía de herencia  
 [IThreadProxy](../../../parallel/concrt/reference/ithreadproxy-structure.md)  
  
 `IUMSThreadProxy`  
  
## Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IUMSScheduler \(Estructura\)](../../../parallel/concrt/reference/iumsscheduler-structure.md)   
 [SchedulerType \(Enumeración\)](../Topic/SchedulerType%20Enumeration.md)