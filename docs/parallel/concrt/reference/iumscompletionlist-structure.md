---
title: "IUMSCompletionList (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::IUMSCompletionList"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IUMSCompletionList (estructura)"
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# IUMSCompletionList (Estructura)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Representa una lista de finalización UMS.  Cuando se bloquea un subproceso UMS, el contexto de programación designado del programador se envía de forma que se puede tomar una decisión sobre qué programar en la raíz del procesador virtual subyacente mientras se bloquea el subproceso original.  Cuando el subproceso original se desbloquea, el sistema operativo lo pone en cola de la lista de finalización, que es accesible a través de esta interfaz.  El programador puede consultar la lista de finalización en el contexto de programación designado o en cualquier otro lugar que busca trabajo.  
  
## Sintaxis  
  
```  
struct IUMSCompletionList;  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IUMSCompletionList::GetUnblockNotifications \(Método\)](../Topic/IUMSCompletionList::GetUnblockNotifications%20Method.md)|Recupera una cadena de interfaces `IUMSUnblockNotification` que representan contextos de ejecución cuyos proxy de subprocesos asociados se han desbloqueado desde la última vez que se invocó este método.|  
  
## Comentarios  
 Un programador debe ser extraordinariamente cuidadoso sobre qué acciones se realizan después de usar esta interfaz para quitar elementos de la cola en la lista de finalización.  Los elementos se deberían colocar en la lista del programador de contextos ejecutables y estar generalmente accesibles tan pronto como sea posible.  Es completamente posible que a uno de los elementos quitados de la cola se le haya proporcionado la propiedad de un bloqueo arbitrario.  El programador no puede realizar llamadas de función arbitraria que se pueden bloquear entre la llamada a los elementos que se quitan de la cola y la posición de esos elementos en una lista a la que generalmente se puede tener acceso desde dentro del programador.  
  
## Jerarquía de herencia  
 `IUMSCompletionList`  
  
## Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IUMSScheduler \(Estructura\)](../../../parallel/concrt/reference/iumsscheduler-structure.md)   
 [IUMSUnblockNotification \(Estructura\)](../../../parallel/concrt/reference/iumsunblocknotification-structure.md)