---
title: "IUMSUnblockNotification (Estructura) | Microsoft Docs"
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
  - "concrtrm/concurrency::IUMSUnblockNotification"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IUMSUnblockNotification (estructura)"
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IUMSUnblockNotification (Estructura)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Representa una notificación del Administrador de recursos indicando que un proxy del subproceso que había bloqueado y desencadenado un valor devuelto al contexto de programación designado del programador, se ha desbloqueado y está listo para su programación.  Esta interfaz no es válida una vez que el contexto de ejecución asociado del proxy del subproceso, devuelto desde el método `GetContext`, se vuelve a programar.  
  
## Sintaxis  
  
```  
struct IUMSUnblockNotification;  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IUMSUnblockNotification::GetContext \(Método\)](../Topic/IUMSUnblockNotification::GetContext%20Method.md)|Devuelve la interfaz `IExecutionContext` para el contexto de ejecución asociado al proxy del subproceso que se ha desbloqueado.  Cuando este método se devuelve y el contexto de ejecución subyacente se ha reprogramado a través de una llamada al método `IThreadProxy::SwitchTo`, esta interfaz ya no es válida.|  
|[IUMSUnblockNotification::GetNextUnblockNotification \(Método\)](../Topic/IUMSUnblockNotification::GetNextUnblockNotification%20Method.md)|Devuelve la próxima interfaz `IUMSUnblockNotification` de la cadena devuelta por el método `IUMSCompletionList::GetUnblockNotifications`.|  
  
## Jerarquía de herencia  
 `IUMSUnblockNotification`  
  
## Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IUMSScheduler \(Estructura\)](../../../parallel/concrt/reference/iumsscheduler-structure.md)   
 [IUMSCompletionList \(Estructura\)](../../../parallel/concrt/reference/iumscompletionlist-structure.md)