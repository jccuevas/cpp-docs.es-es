---
title: "IExecutionContext (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::IExecutionContext"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IExecutionContext (estructura)"
ms.assetid: f3108089-ecda-4b07-86db-3efae60c31e0
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# IExecutionContext (Estructura)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Una interfaz a un contexto de ejecución que se puede ejecutar en un procesador virtual determinado y que puede cambiar de contexto de forma cooperativa.  
  
## Sintaxis  
  
```  
struct IExecutionContext;  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IExecutionContext::Dispatch \(Método\)](../Topic/IExecutionContext::Dispatch%20Method.md)|El método al que se llama cuando un proxy del subproceso comienza a ejecutar un contexto de ejecución determinado.  Ésta debería ser la rutina del trabajador principal para su programador.|  
|[IExecutionContext::GetId \(Método\)](../Topic/IExecutionContext::GetId%20Method.md)|Devuelve un identificador único para el contexto de ejecución.|  
|[IExecutionContext::GetProxy \(Método\)](../Topic/IExecutionContext::GetProxy%20Method.md)|Devuelve una interfaz al proxy del subproceso que está ejecutando este contexto.|  
|[IExecutionContext::GetScheduler \(Método\)](../Topic/IExecutionContext::GetScheduler%20Method.md)|Devuelve una interfaz al programador al que pertenece esta ejecución.|  
|[IExecutionContext::SetProxy \(Método\)](../Topic/IExecutionContext::SetProxy%20Method.md)|Asocia un proxy del subproceso a este contexto de ejecución.  El proxy del subproceso asociado invoca este método justo antes de que comience a ejecutar el método `Dispatch` del contexto.|  
  
## Comentarios  
 Si está implementando un programador personalizado que interactúa con el administrador de recursos del runtime de simultaneidad, tendrá que implementar la interfaz `IExecutionContext`.  Los subprocesos creados por el administrador de recursos realizan el trabajo en nombre de su programador ejecutando el método `IExecutionContext::Dispatch`.  
  
## Jerarquía de herencia  
 `IExecutionContext`  
  
## Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IScheduler \(Estructura\)](../../../parallel/concrt/reference/ischeduler-structure.md)   
 [IThreadProxy \(Estructura\)](../../../parallel/concrt/reference/ithreadproxy-structure.md)