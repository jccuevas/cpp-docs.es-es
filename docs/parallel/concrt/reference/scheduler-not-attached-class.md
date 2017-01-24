---
title: "scheduler_not_attached (Clase) | Microsoft Docs"
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
  - "concrt/concurrency::scheduler_not_attached"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "scheduler_not_attached (clase)"
ms.assetid: 26001970-b400-463b-be3d-8623359c399a
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# scheduler_not_attached (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando se realiza una operación que requiere que un programador se adjunte al contexto actual y no hay ninguno.  
  
## Sintaxis  
  
```  
class scheduler_not_attached : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[scheduler\_not\_attached::scheduler\_not\_attached \(Constructor\)](../Topic/scheduler_not_attached::scheduler_not_attached%20Constructor.md)|Sobrecargado.  Construye un objeto `scheduler_not_attached`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `scheduler_not_attached`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler \(Clase\)](../../../parallel/concrt/reference/scheduler-class.md)   
 [Scheduler::Attach \(Método\)](../Topic/Scheduler::Attach%20Method.md)