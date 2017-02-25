---
title: "propagator_block (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::propagator_block"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "propagator_block (clase)"
ms.assetid: 86aa75fd-eda5-42aa-aadf-25c0c1c9742d
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# propagator_block (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `propagator_block` es una clase base abstracta para los bloques de mensaje que son un bloque de origen y de destino.  Combina la funcionalidad de las clases `source_block` y `target_block`.  
  
## Sintaxis  
  
```  
template<  
   class _TargetLinkRegistry,  
   class _SourceLinkRegistry,  
   class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>  
>  
class propagator_block : public source_block<_TargetLinkRegistry, _MessageProcessorType>, public ITarget<typename _SourceLinkRegistry::type::source_type>;  
```  
  
#### Parámetros  
 `_TargetLinkRegistry`  
 El Registro del vínculo que se va a usar para retener los vínculos de destino.  
  
 `_SourceLinkRegistry`  
 El Registro del vínculo que se va a usar para retener los vínculos de origen.  
  
 `_MessageProcessorType`  
 El tipo de procesador para el procesamiento de mensajes.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`source_iterator`|El tipo de iterador para `source_link_manager`, para este `propagator_block`.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[propagator\_block::propagator\_block \(Constructor\)](../Topic/propagator_block::propagator_block%20Constructor.md)|Construye un objeto `propagator_block`.|  
|[propagator\_block::~propagator\_block \(Destructor\)](../Topic/propagator_block::~propagator_block%20Destructor.md)|Destruye un objeto `propagator_block`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[propagator\_block::propagate \(Método\)](../Topic/propagator_block::propagate%20Method.md)|De forma asincrónica, pasa un mensaje de un bloque de orígenes a este bloque de destino.|  
|[propagator\_block::send \(Método\)](../Topic/propagator_block::send%20Method.md)|De forma sincrónica, inicia un mensaje a este bloque.  Lo llama un bloque `ISource`.  Cuando esta función se completa, el mensaje ya se habrá propagado en el bloque.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[propagator\_block::decline\_incoming\_messages \(Método\)](../Topic/propagator_block::decline_incoming_messages%20Method.md)|Indica al bloque que se deben rechazar los mensajes nuevos.|  
|[propagator\_block::initialize\_source\_and\_target \(Método\)](../Topic/propagator_block::initialize_source_and_target%20Method.md)|Inicializa el objeto base.  Específicamente, el objeto `message_processor` debe inicializarse.|  
|[propagator\_block::link\_source \(Método\)](../Topic/propagator_block::link_source%20Method.md)|Vincula un bloque de orígenes especificado con este objeto `propagator_block`.|  
|[propagator\_block::process\_input\_messages \(Método\)](../Topic/propagator_block::process_input_messages%20Method.md)|Mensajes de entrada de proceso.  Esto sólo es útil para los bloques propagador, que derivan de source\_block \(reemplaza [source\_block::process\_input\_messages](../Topic/source_block::process_input_messages%20Method.md).\)|  
|[propagator\_block::propagate\_message \(Método\)](../Topic/propagator_block::propagate_message%20Method.md)|Cuando se invalida en una clase derivada, este método pasa de forma asincrónica un mensaje de un bloque `ISource` a este objeto `propagator_block`.  Lo invoca el método `propagate`, cuando lo llama un bloque de origen.|  
|[propagator\_block::register\_filter \(Método\)](../Topic/propagator_block::register_filter%20Method.md)|Registra un método de filtro que se invocará en cada mensaje recibido.|  
|[propagator\_block::remove\_network\_links \(Método\)](../Topic/propagator_block::remove_network_links%20Method.md)|Quita todos los vínculos de red de origen y de destino de este objeto `propagator_block`.|  
|[propagator\_block::send\_message \(Método\)](../Topic/propagator_block::send_message%20Method.md)|Cuando se invalida en una clase derivada, este método pasa de forma sincrónica un mensaje de un bloque `ISource` a este objeto `propagator_block`.  Lo invoca el método `send`, cuando lo llama un bloque de origen.|  
|[propagator\_block::unlink\_source \(Método\)](../Topic/propagator_block::unlink_source%20Method.md)|Desvincula un bloque de orígenes especificado desde este objeto `propagator_block`.|  
|[propagator\_block::unlink\_sources \(Método\)](../Topic/propagator_block::unlink_sources%20Method.md)|Desvincula todos los bloques de origen desde este objeto `propagator_block`. \(Invalida [ITarget::unlink\_sources](../Topic/ITarget::unlink_sources%20Method.md).\)|  
  
## Comentarios  
 Para evitar la herencia múltiple, la clase `propagator_block` hereda de la clase `source_block` y de la clase abstracta `ITarget`.  La mayor parte de la funcionalidad de la clase `target_block` se replica aquí.  
  
## Jerarquía de herencia  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 [source\_block](../../../parallel/concrt/reference/source-block-class.md)  
  
 `propagator_block`  
  
## Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [source\_block \(Clase\)](../../../parallel/concrt/reference/source-block-class.md)   
 [ITarget \(Clase\)](../../../parallel/concrt/reference/itarget-class.md)