---
title: "operation_timed_out (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::operation_timed_out"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operation_timed_out (clase)"
ms.assetid: 963efe1d-a6e0-477c-9a70-d93d8412c897
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# operation_timed_out (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando una operación ha agotado su tiempo de espera.  
  
## Sintaxis  
  
```  
class operation_timed_out : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[operation\_timed\_out::operation\_timed\_out \(Constructor\)](../Topic/operation_timed_out::operation_timed_out%20Constructor.md)|Sobrecargado.  Construye un objeto `operation_timed_out`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `operation_timed_out`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)