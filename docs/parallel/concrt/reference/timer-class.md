---
title: "Clase timer | Microsoft Docs"
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
  - "agents/concurrency::timer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "timer (clase)"
ms.assetid: 4f4dea51-de9f-40f9-93f5-dd724c567b49
caps.latest.revision: 21
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clase timer
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Un bloque de mensajería `timer` es un bloque `source_block` con destino único, capaz de enviar un mensaje a su destino cuando un período de tiempo especificado ha transcurrido o en intervalos concretos.  
  
## Sintaxis  
  
```  
template<  
   class _Type  
>  
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<_Type>>>;  
```  
  
#### Parámetros  
 `_Type`  
 El tipo de carga de los mensajes de resultados propagados de este bloque.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[timer::timer \(Constructor\)](../Topic/timer::timer%20Constructor.md)|Sobrecargado.  Construye un bloque de mensajería `timer` que desencadenará un mensaje determinado después de un intervalo especificado.|  
|[timer::~timer \(Destructor\)](../Topic/timer::~timer%20Destructor.md)|Destruye un bloque de mensajería `timer`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[timer::pause \(Método\)](../Topic/timer::pause%20Method.md)|Detiene el bloque de mensajería `timer`.  Si es un bloque de mensajería `timer` que se repite, se puede reiniciar con una llamada `start()` subsiguiente.  Para los temporizadores no repetitivos, esto tiene el mismo efecto que una llamada `stop`.|  
|[timer::start \(Método\)](../Topic/timer::start%20Method.md)|Inicia el bloque de mensajería `timer`.  Se llama al número especificado de milisegundos después de este, el valor especificado se propagará por el canal de bajada como un `message`.|  
|[timer::stop \(Método\)](../Topic/timer::stop%20Method.md)|Detiene el bloque de mensajería `timer`.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[timer::accept\_message \(Método\)](../Topic/timer::accept_message%20Method.md)|Acepta un mensaje que fue proporcionado por este bloque de mensajería `timer`, transfiriendo la propiedad al llamador.|  
|[timer::consume\_message \(Método\)](../Topic/timer::consume_message%20Method.md)|Consume un mensaje que fue proporcionado anteriormente por `timer` y reservado por el destino, transfiriendo la propiedad al llamador.|  
|[timer::link\_target\_notification \(Método\)](../Topic/timer::link_target_notification%20Method.md)|Una devolución de llamada que notifica que se ha vinculado un nuevo destino a este bloque de mensajería `timer`.|  
|[timer::propagate\_to\_any\_targets \(Método\)](../Topic/timer::propagate_to_any_targets%20Method.md)|Intenta proporcionar el mensaje generado por el bloque `timer` a todos los destinos vinculados.|  
|[timer::release\_message \(Método\)](../Topic/timer::release_message%20Method.md)|Libera una reserva de mensaje anterior. \(Invalida [source\_block::release\_message](../Topic/source_block::release_message%20Method.md).\)|  
|[timer::reserve\_message \(Método\)](../Topic/timer::reserve_message%20Method.md)|Reserva un mensaje ofrecido previamente por este bloque de mensajería `timer`. \(Invalida [source\_block::reserve\_message](../Topic/source_block::reserve_message%20Method.md).\)|  
|[timer::resume\_propagation \(Método\)](../Topic/timer::resume_propagation%20Method.md)|Reanuda la propagación una vez liberada una reserva. \(Invalida [source\_block::resume\_propagation](../Topic/source_block::resume_propagation%20Method.md).\)|  
  
## Comentarios  
 Para obtener más información, vea [Bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## Jerarquía de herencia  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 [source\_block](../../../parallel/concrt/reference/source-block-class.md)  
  
 `timer`  
  
## Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)