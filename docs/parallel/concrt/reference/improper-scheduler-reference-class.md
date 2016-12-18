---
title: "improper_scheduler_reference (Clase) | Microsoft Docs"
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
  - "concrt/concurrency::improper_scheduler_reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "improper_scheduler_reference (clase)"
ms.assetid: 434a7512-7796-4255-92a7-f3bf71c6a7a7
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# improper_scheduler_reference (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando se llama al método `Reference` en un objeto `Scheduler` que se está cerrando, desde un contexto que no forma parte de ese programador.  
  
## Sintaxis  
  
```  
class improper_scheduler_reference : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[improper\_scheduler\_reference::improper\_scheduler\_reference \(Constructor\)](../Topic/improper_scheduler_reference::improper_scheduler_reference%20Constructor.md)|Sobrecargado.  Construye un objeto `improper_scheduler_reference`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `improper_scheduler_reference`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler \(Clase\)](../../../parallel/concrt/reference/scheduler-class.md)   
 [Scheduler::Reference \(Método\)](../Topic/Scheduler::Reference%20Method.md)