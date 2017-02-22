---
title: "Clase overwrite_buffer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::overwrite_buffer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "overwrite_buffer (clase)"
ms.assetid: 5cc428fe-3697-419c-9fb2-78f6181c9293
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# Clase overwrite_buffer
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Un bloque de mensajería `overwrite_buffer` es un bloque `propagator_block` de destino único, de varios orígenes y ordenado que es capaz de almacenar un único mensaje cada vez.  Los nuevos mensajes sobrescriben a los retenidos previamente.  
  
## Sintaxis  
  
```  
template<  
   class _Type  
>  
class overwrite_buffer : public propagator_block<multi_link_registry<ITarget<_Type>>, multi_link_registry<ISource<_Type>>>;  
```  
  
#### Parámetros  
 `_Type`  
 El tipo de carga de los mensajes almacenados y propagados por el búfer.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[overwrite\_buffer::overwrite\_buffer \(Constructor\)](../Topic/overwrite_buffer::overwrite_buffer%20Constructor.md)|Sobrecargado.  Construye un bloque de mensajería `overwrite_buffer`.|  
|[overwrite\_buffer::~overwrite\_buffer \(Destructor\)](../Topic/overwrite_buffer::~overwrite_buffer%20Destructor.md)|Destruye el bloque de mensajería `overwrite_buffer`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[overwrite\_buffer::has\_value \(Método\)](../Topic/overwrite_buffer::has_value%20Method.md)|Comprueba si este bloque de mensajería `overwrite_buffer` tiene un valor.|  
|[overwrite\_buffer::value \(Método\)](../Topic/overwrite_buffer::value%20Method.md)|Obtiene una referencia a la carga útil actual del mensaje que se está almacenado en el bloque de mensajería `overwrite_buffer`.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[overwrite\_buffer::accept\_message \(Método\)](../Topic/overwrite_buffer::accept_message%20Method.md)|Acepta un mensaje que fue proporcionado por este bloque de mensajería `overwrite_buffer`, devolviendo una copia del mensaje al llamador.|  
|[overwrite\_buffer::consume\_message \(Método\)](../Topic/overwrite_buffer::consume_message%20Method.md)|Consume un mensaje que fue proporcionado anteriormente por el bloque de mensajería `overwrite_buffer` y reservado por el destino, devolviendo una copia del mensaje al llamador.|  
|[overwrite\_buffer::link\_target\_notification \(Método\)](../Topic/overwrite_buffer::link_target_notification%20Method.md)|Una devolución de llamada que notifica que se ha vinculado un nuevo destino a este bloque de mensajería `overwrite_buffer`.|  
|[overwrite\_buffer::propagate\_message \(Método\)](../Topic/overwrite_buffer::propagate_message%20Method.md)|De forma asincrónica, pasa un mensaje de un bloque `ISource` a este bloque de mensajería `overwrite_buffer`.  Lo invoca el método `propagate`, cuando lo llama un bloque de origen.|  
|[overwrite\_buffer::propagate\_to\_any\_targets \(Método\)](../Topic/overwrite_buffer::propagate_to_any_targets%20Method.md)|Coloca `message``_PMessage` en este bloque de mensajería `overwrite_buffer` y lo ofrece a todos los destinos vinculados.|  
|[overwrite\_buffer::release\_message \(Método\)](../Topic/overwrite_buffer::release_message%20Method.md)|Libera una reserva de mensaje anterior. \(Invalida [source\_block::release\_message](../Topic/source_block::release_message%20Method.md).\)|  
|[overwrite\_buffer::reserve\_message \(Método\)](../Topic/overwrite_buffer::reserve_message%20Method.md)|Reserva un mensaje ofrecido previamente por este bloque de mensajería `overwrite_buffer`. \(Invalida [source\_block::reserve\_message](../Topic/source_block::reserve_message%20Method.md).\)|  
|[overwrite\_buffer::resume\_propagation \(Método\)](../Topic/overwrite_buffer::resume_propagation%20Method.md)|Reanuda la propagación una vez liberada una reserva. \(Invalida [source\_block::resume\_propagation](../Topic/source_block::resume_propagation%20Method.md).\)|  
|[overwrite\_buffer::send\_message \(Método\)](../Topic/overwrite_buffer::send_message%20Method.md)|De forma sincrónica, pasa un mensaje de un bloque `ISource` a este bloque de mensajería `overwrite_buffer`.  Lo invoca el método `send`, cuando lo llama un bloque de origen.|  
|[overwrite\_buffer::supports\_anonymous\_source \(Método\)](../Topic/overwrite_buffer::supports_anonymous_source%20Method.md)|Invalida el método de `supports_anonymous_source` para indicar que este bloque puede aceptar mensajes proporcionados al por un origen que no están vinculados. \(Reemplaza [ITarget::supports\_anonymous\_source](../Topic/ITarget::supports_anonymous_source%20Method.md).\)|  
  
## Comentarios  
 Un bloque de mensajería `overwrite_buffer` propaga las copias de su mensaje almacenado a cada uno de sus destinos.  
  
 Para obtener más información, vea [Bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## Jerarquía de herencia  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 [source\_block](../../../parallel/concrt/reference/source-block-class.md)  
  
 [propagator\_block](../../../parallel/concrt/reference/propagator-block-class.md)  
  
 `overwrite_buffer`  
  
## Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Clase unbounded\_buffer](../Topic/unbounded_buffer%20Class.md)   
 [Clase single\_assignment](../../../parallel/concrt/reference/single-assignment-class.md)