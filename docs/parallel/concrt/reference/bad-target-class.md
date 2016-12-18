---
title: "bad_target (Clase) | Microsoft Docs"
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
  - "concrt/concurrency::bad_target"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_target (clase)"
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# bad_target (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando un bloque de mensajería recibe un puntero a un destino que no es válido para la operación que se realiza.  
  
## Sintaxis  
  
```  
class bad_target : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[bad\_target::bad\_target \(Constructor\)](../Topic/bad_target::bad_target%20Constructor.md)|Sobrecargado.  Construye un objeto `bad_target`.|  
  
## Comentarios  
 Esta excepción se produce normalmente por razones tales como un intento de destino para utilizar un mensaje que se reserva para un destino diferente o liberando una reserva que no contiene.  
  
## Jerarquía de herencia  
 `exception`  
  
 `bad_target`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md)