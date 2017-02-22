---
title: "target_block (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::target_block"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "target_block (clase)"
ms.assetid: 3ce181b4-b94a-4894-bf7b-64fc09821f9f
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# target_block (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `target_block` es una clase base abstracta que proporciona funcionalidad de administración de vínculo básica y comprueba errores solo para bloques de destino.  
  
## Sintaxis  
  
```  
template<  
   class _SourceLinkRegistry,  
   class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>  
>  
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;  
```  
  
#### Parámetros  
 `_SourceLinkRegistry`  
 El Registro del vínculo que se va a usar para retener los vínculos de origen.  
  
 `_MessageProcessorType`  
 El tipo de procesador para el procesamiento de mensajes.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`source_iterator`|El tipo de iterador para `source_link_manager`, para este objeto `target_block`.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[target\_block::target\_block \(Constructor\)](../Topic/target_block::target_block%20Constructor.md)|Construye un objeto `target_block`.|  
|[target\_block::~target\_block \(Destructor\)](../Topic/target_block::~target_block%20Destructor.md)|Destruye el objeto `target_block`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[target\_block::propagate \(Método\)](../Topic/target_block::propagate%20Method.md)|De forma asincrónica, pasa un mensaje de un bloque de orígenes a este bloque de destino.|  
|[target\_block::send \(Método\)](../Topic/target_block::send%20Method.md)|De forma sincrónica, pasa un mensaje de un bloque de origen a este bloque de destino.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[target\_block::async\_send \(Método\)](../Topic/target_block::async_send%20Method.md)|De forma asincrónica, envía un mensaje para procesar.|  
|[target\_block::decline\_incoming\_messages \(Método\)](../Topic/target_block::decline_incoming_messages%20Method.md)|Indica al bloque que se deben rechazar los mensajes nuevos.|  
|[target\_block::enable\_batched\_processing \(Método\)](../Topic/target_block::enable_batched_processing%20Method.md)|Habilita el procesamiento por lotes para este bloque.|  
|[target\_block::initialize\_target \(Método\)](../Topic/target_block::initialize_target%20Method.md)|Inicializa el objeto base.  Específicamente, el objeto `message_processor` debe inicializarse.|  
|[target\_block::link\_source \(Método\)](../Topic/target_block::link_source%20Method.md)|Vincula un bloque de orígenes especificado con este objeto `target_block`.|  
|[target\_block::process\_input\_messages \(Método\)](../Topic/target_block::process_input_messages%20Method.md)|Procesa los mensajes que se reciben como entradas.|  
|[target\_block::process\_message \(Método\)](../Topic/target_block::process_message%20Method.md)|Cuando se reemplaza en una clase derivada, procesa un mensaje admitido por este objeto de `target_block` .|  
|[target\_block::propagate\_message \(Método\)](../Topic/target_block::propagate_message%20Method.md)|Cuando se invalida en una clase derivada, este método pasa de forma asincrónica un mensaje de un bloque `ISource` a este objeto `target_block`.  Lo invoca el método `propagate`, cuando lo llama un bloque de origen.|  
|[target\_block::register\_filter \(Método\)](../Topic/target_block::register_filter%20Method.md)|Registra un método de filtro que se invocará en cada mensaje recibido.|  
|[target\_block::remove\_sources \(Método\)](../Topic/target_block::remove_sources%20Method.md)|Desvincula todos los orígenes después de esperar que se completen las operaciones de envío asincrónico pendientes.|  
|[target\_block::send\_message \(Método\)](../Topic/target_block::send_message%20Method.md)|Cuando se invalida en una clase derivada, este método pasa de forma sincrónica un mensaje de un bloque `ISource` a este objeto `target_block`.  Lo invoca el método `send`, cuando lo llama un bloque de origen.|  
|[target\_block::sync\_send \(Método\)](../Topic/target_block::sync_send%20Method.md)|De forma sincrónica, envía un mensaje para procesar.|  
|[target\_block::unlink\_source \(Método\)](../Topic/target_block::unlink_source%20Method.md)|Desvincula un bloque de orígenes especificado desde este objeto `target_block`.|  
|[target\_block::unlink\_sources \(Método\)](../Topic/target_block::unlink_sources%20Method.md)|Desvincula todos los bloques de origen desde este objeto `target_block`. \(Invalida [ITarget::unlink\_sources](../Topic/ITarget::unlink_sources%20Method.md).\)|  
|[target\_block::wait\_for\_async\_sends \(Método\)](../Topic/target_block::wait_for_async_sends%20Method.md)|Espera a que todas las propagaciones asincrónicas se completen.|  
  
## Jerarquía de herencia  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 `target_block`  
  
## Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [ITarget \(Clase\)](../../../parallel/concrt/reference/itarget-class.md)