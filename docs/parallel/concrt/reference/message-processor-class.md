---
title: "message_processor (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::message_processor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "message_processor (clase)"
ms.assetid: 23afb052-daa7-44ed-bf24-d2513db748da
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# message_processor (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `message_processor` es la clase base abstracta del procesamiento de objetos `message`.  No hay ninguna garantía en la clasificación de los mensajes.  
  
## Sintaxis  
  
```  
template<  
   class _Type  
>  
class message_processor;  
```  
  
#### Parámetros  
 `_Type`  
 El tipo de datos de la carga dentro de los mensajes administrados por este objeto `message_processor`.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`type`|Un alias de tipo para `_Type`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[message\_processor::async\_send \(Método\)](../Topic/message_processor::async_send%20Method.md)|Cuando se invalida en una clase derivada, coloca mensajes en el bloque de forma asincrónica.|  
|[message\_processor::sync\_send \(Método\)](../Topic/message_processor::sync_send%20Method.md)|Cuando se invalida en una clase derivada, coloca mensajes en el bloque de forma sincrónica.|  
|[message\_processor::wait \(Método\)](../Topic/message_processor::wait%20Method.md)|Cuando se invalida en una clase derivada, espera a que todas las operaciones asincrónicas se completen.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[message\_processor::process\_incoming\_message \(Método\)](../Topic/message_processor::process_incoming_message%20Method.md)|Cuando se invalida en una clase derivada, realiza el procesamiento de desvío de mensajes en el bloque.  Se llama una vez cada vez que se agrega un nuevo mensaje y la cola esta vacía.|  
  
## Jerarquía de herencia  
 `message_processor`  
  
## Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [ordered\_message\_processor \(Clase\)](../../../parallel/concrt/reference/ordered-message-processor-class.md)