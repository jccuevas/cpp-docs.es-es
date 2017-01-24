---
title: "Clase transformer | Microsoft Docs"
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
  - "agents/concurrency::transformer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "transformer (clase)"
ms.assetid: eea71925-7043-4a92-bfd4-dbc0ece5d081
caps.latest.revision: 22
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clase transformer
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Un bloque de mensajería `transformer` es un bloque `propagator_block` de destino único, de varios orígenes y ordenado capaz de almacenar un número ilimitado de mensajes de un tipo diferente.  
  
## Sintaxis  
  
```  
template<  
   class _Input,  
   class _Output  
>  
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>, multi_link_registry<ISource<_Input>>>;  
```  
  
#### Parámetros  
 `_Input`  
 El tipo de carga de los mensajes aceptados por el procesador.  
  
 `_Output`  
 El tipo de carga de los mensajes almacenados y propagados fuera por el búfer.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[transformer::transformer \(Constructor\)](../Topic/transformer::transformer%20Constructor.md)|Sobrecargado.  Construye un bloque de mensajería `transformer`.|  
|[transformer::~transformer \(Destructor\)](../Topic/transformer::~transformer%20Destructor.md)|Destruye el bloque de mensajería `transformer`.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[transformer::accept\_message \(Método\)](../Topic/transformer::accept_message%20Method.md)|Acepta un mensaje que fue proporcionado por este bloque de mensajería `transformer`, transfiriendo la propiedad al llamador.|  
|[transformer::consume\_message \(Método\)](../Topic/transformer::consume_message%20Method.md)|Consume un mensaje que fue proporcionado anteriormente por `transformer` y reservado por el destino, transfiriendo la propiedad al llamador.|  
|[transformer::link\_target\_notification \(Método\)](../Topic/transformer::link_target_notification%20Method.md)|Una devolución de llamada que notifica que se ha vinculado un nuevo destino a este bloque de mensajería `transformer`.|  
|[transformer::propagate\_message \(Método\)](../Topic/transformer::propagate_message%20Method.md)|De forma asincrónica, pasa un mensaje de un bloque `ISource` a este bloque de mensajería `transformer`.  Lo invoca el método `propagate`, cuando lo llama un bloque de origen.|  
|[transformer::propagate\_to\_any\_targets \(Método\)](../Topic/transformer::propagate_to_any_targets%20Method.md)|Ejecuta la función transformer en los mensajes entrantes.|  
|[transformer::release\_message \(Método\)](../Topic/transformer::release_message%20Method.md)|Libera una reserva de mensaje anterior. \(Invalida [source\_block::release\_message](../Topic/source_block::release_message%20Method.md).\)|  
|[transformer::reserve\_message \(Método\)](../Topic/transformer::reserve_message%20Method.md)|Reserva un mensaje ofrecido previamente por este bloque de mensajería `transformer`. \(Invalida [source\_block::reserve\_message](../Topic/source_block::reserve_message%20Method.md).\)|  
|[transformer::resume\_propagation \(Método\)](../Topic/transformer::resume_propagation%20Method.md)|Reanuda la propagación una vez liberada una reserva. \(Invalida [source\_block::resume\_propagation](../Topic/source_block::resume_propagation%20Method.md).\)|  
|[transformer::send\_message \(Método\)](../Topic/transformer::send_message%20Method.md)|De forma sincrónica, pasa un mensaje de un bloque `ISource` a este bloque de mensajería `transformer`.  Lo invoca el método `send`, cuando lo llama un bloque de origen.|  
|[transformer::supports\_anonymous\_source \(Método\)](../Topic/transformer::supports_anonymous_source%20Method.md)|Invalida el método de `supports_anonymous_source` para indicar que este bloque puede aceptar mensajes proporcionados al por un origen que no están vinculados. \(Reemplaza [ITarget::supports\_anonymous\_source](../Topic/ITarget::supports_anonymous_source%20Method.md).\)|  
  
## Comentarios  
 Para obtener más información, vea [Bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## Jerarquía de herencia  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 [source\_block](../../../parallel/concrt/reference/source-block-class.md)  
  
 [propagator\_block](../../../parallel/concrt/reference/propagator-block-class.md)  
  
 `transformer`  
  
## Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Clase call](../../../parallel/concrt/reference/call-class.md)