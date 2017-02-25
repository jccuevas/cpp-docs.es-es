---
title: "ordered_message_processor (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::ordered_message_processor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ordered_message_processor (clase)"
ms.assetid: 787adfb7-7f79-4a70-864a-80e3b64088cd
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# ordered_message_processor (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Un `ordered_message_processor` es un `message_processor` que permite a los bloques de mensaje procesar los mensajes en el orden que se recibieron.  
  
## Sintaxis  
  
```  
template<  
   class _Type  
>  
class ordered_message_processor : public message_processor<_Type>;  
```  
  
#### Parámetros  
 `_Type`  
 El tipo de carga de mensajes administrados por el procesador.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`type`|Un alias de tipo para `_Type`.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ordered\_message\_processor::ordered\_message\_processor \(Constructor\)](../Topic/ordered_message_processor::ordered_message_processor%20Constructor.md)|Construye un objeto `ordered_message_processor`.|  
|[ordered\_message\_processor::~ordered\_message\_processor \(Destructor\)](../Topic/ordered_message_processor::~ordered_message_processor%20Destructor.md)|Destruye el objeto `ordered_message_processor`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ordered\_message\_processor::async\_send \(Método\)](../Topic/ordered_message_processor::async_send%20Method.md)|De forma asincrónica, pone en la cola a los mensajes e inicia una tarea de procesamiento, si esto no se ha hecho ya. \(Invalida [message\_processor::async\_send](../Topic/message_processor::async_send%20Method.md).\)|  
|[ordered\_message\_processor::initialize \(Método\)](../Topic/ordered_message_processor::initialize%20Method.md)|Inicializa el objeto `ordered_message_processor` con la función de devolución de llamada, el programador y el grupo de programación adecuados.|  
|[ordered\_message\_processor::initialize\_batched\_processing \(Método\)](../Topic/ordered_message_processor::initialize_batched_processing%20Method.md)|Procesamiento de mensajes por lotes Initialize|  
|[ordered\_message\_processor::sync\_send \(Método\)](../Topic/ordered_message_processor::sync_send%20Method.md)|De forma sincrónica, pone en la cola a los mensajes e inicia una tarea de procesamiento, si esto no se ha hecho ya. \(Invalida [message\_processor::sync\_send](../Topic/message_processor::sync_send%20Method.md).\)|  
|[ordered\_message\_processor::wait \(Método\)](../Topic/ordered_message_processor::wait%20Method.md)|Una espera de vuelta específica del procesador usada en destructores de bloques de mensaje para asegurarse de que todas las tareas de procesamiento asincrónico tienen tiempo para finalizar antes de destruir el bloque. \(Invalida [message\_processor::wait](../Topic/message_processor::wait%20Method.md).\)|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ordered\_message\_processor::process\_incoming\_message \(Método\)](../Topic/ordered_message_processor::process_incoming_message%20Method.md)|La función de procesamiento a la que se llama de forma asincrónica.  Elimina mensajes de la cola y empieza a procesarlos. \(Invalida [message\_processor::process\_incoming\_message](../Topic/message_processor::process_incoming_message%20Method.md).\)|  
  
## Jerarquía de herencia  
 [message\_processor](../../../parallel/concrt/reference/message-processor-class.md)  
  
 `ordered_message_processor`  
  
## Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)