---
title: "message_not_found (Clase) | Microsoft Docs"
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
  - "concrt/concurrency::message_not_found"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "message_not_found (clase)"
ms.assetid: a96b9995-5ad7-4600-83c8-c15e329ff10e
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# message_not_found (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando un bloque de mensajería no puede encontrar un mensaje solicitado.  
  
## Sintaxis  
  
```  
class message_not_found : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[message\_not\_found::message\_not\_found \(Constructor\)](../Topic/message_not_found::message_not_found%20Constructor.md)|Sobrecargado.  Construye un objeto `message_not_found`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `message_not_found`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md)