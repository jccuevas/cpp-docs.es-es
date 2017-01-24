---
title: "invalid_oversubscribe_operation (Clase) | Microsoft Docs"
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
  - "concrt/concurrency::invalid_oversubscribe_operation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_oversubscribe_operation (clase)"
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
caps.latest.revision: 19
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# invalid_oversubscribe_operation (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción cuando se llama al método `Context::Oversubscribe` con el parámetro `_BeginOversubscription` establecido en `false` sin realizar antes una llamada al método `Context::Oversubscribe` con el parámetro `_BeginOversubscription` establecido en `true`.  
  
## Sintaxis  
  
```  
class invalid_oversubscribe_operation : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[invalid\_oversubscribe\_operation::invalid\_oversubscribe\_operation \(Constructor\)](../Topic/invalid_oversubscribe_operation::invalid_oversubscribe_operation%20Constructor.md)|Sobrecargado.  Construye un objeto `invalid_oversubscribe_operation`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `invalid_oversubscribe_operation`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Context::Oversubscribe \(Método\)](../Topic/Context::Oversubscribe%20Method.md)