---
title: "default_scheduler_exists (Clase) | Microsoft Docs"
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
  - "concrt/concurrency::default_scheduler_exists"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "default_scheduler_exists (clase)"
ms.assetid: f6e575e2-4e0f-455a-9e06-54f462ce0c1c
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# default_scheduler_exists (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando se llama al método `Scheduler::SetDefaultSchedulerPolicy` cuando un programador predeterminado ya existe dentro del proceso.  
  
## Sintaxis  
  
```  
class default_scheduler_exists : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[default\_scheduler\_exists::default\_scheduler\_exists \(Constructor\)](../Topic/default_scheduler_exists::default_scheduler_exists%20Constructor.md)|Sobrecargado.  Construye un objeto `default_scheduler_exists`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `default_scheduler_exists`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Scheduler::SetDefaultSchedulerPolicy \(Método\)](../Topic/Scheduler::SetDefaultSchedulerPolicy%20Method.md)