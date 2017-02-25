---
title: "improper_lock (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::improper_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "improper_lock (clase)"
ms.assetid: 8f494942-7748-4a2a-8de2-23414bfe6346
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# improper_lock (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando se realiza un bloqueo de forma incorrecta.  
  
## Sintaxis  
  
```  
class improper_lock : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[improper\_lock::improper\_lock \(Constructor\)](../Topic/improper_lock::improper_lock%20Constructor.md)|Sobrecargado.  Construye un `improper_lock exception`.|  
  
## Comentarios  
 Normalmente, se produce esta excepción cuando se intenta adquirir un bloqueo no reentrante en el mismo contexto de forma recursiva.  
  
## Jerarquía de herencia  
 `exception`  
  
 `improper_lock`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [critical\_section \(Clase\)](../../../parallel/concrt/reference/critical-section-class.md)   
 [reader\_writer\_lock \(Clase\)](../../../parallel/concrt/reference/reader-writer-lock-class.md)