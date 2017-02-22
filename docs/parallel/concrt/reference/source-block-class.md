---
title: "source_block (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::source_block"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "source_block (clase)"
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# source_block (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `source_block` es una clase base abstracta solo para bloques de origen.  La clase proporciona funcionalidad de administración de vínculo básico, así como comprobaciones de errores frecuentes.  
  
## Sintaxis  
  
```  
template<  
   class _TargetLinkRegistry,  
   class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>  
>  
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;  
```  
  
#### Parámetros  
 `_TargetLinkRegistry`  
 El Registro del vínculo que se va a usar para retener los vínculos de destino.  
  
 `_MessageProcessorType`  
 Tipo de procesador para el procesamiento de mensajes.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`target_iterator`|El iterador para recorrer los destinos conectados.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[source\_block::source\_block \(Constructor\)](../Topic/source_block::source_block%20Constructor.md)|Construye un objeto `source_block`.|  
|[source\_block::~source\_block \(Destructor\)](../Topic/source_block::~source_block%20Destructor.md)|Destruye el objeto `source_block`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[source\_block::accept \(Método\)](../Topic/source_block::accept%20Method.md)|Acepta un mensaje que fue proporcionado por este objeto `source_block`, transfiriendo la propiedad al llamador.|  
|[source\_block::acquire\_ref \(Método\)](../Topic/source_block::acquire_ref%20Method.md)|Adquiere un recuento de referencias en este objeto `source_block`, para evitar la eliminación.|  
|[source\_block::consume \(Método\)](../Topic/source_block::consume%20Method.md)|Consume un mensaje que fue proporcionado anteriormente por este objeto `source_block` y correctamente reservado por el destino, transfiriendo la propiedad al llamador.|  
|[source\_block::link\_target \(Método\)](../Topic/source_block::link_target%20Method.md)|Vincula un bloque de destino con este objeto `source_block`.|  
|[source\_block::release \(Método\)](../Topic/source_block::release%20Method.md)|Libera una reserva de mensaje anterior correcta.|  
|[source\_block::release\_ref \(Método\)](../Topic/source_block::release_ref%20Method.md)|Libera un recuento de referencias en este objeto `source_block`.|  
|[source\_block::reserve \(Método\)](../Topic/source_block::reserve%20Method.md)|Reserva un mensaje ofrecido previamente por este objeto `source_block`.|  
|[source\_block::unlink\_target \(Método\)](../Topic/source_block::unlink_target%20Method.md)|Desvincula un bloque de destino de este objeto `source_block`.|  
|[source\_block::unlink\_targets \(Método\)](../Topic/source_block::unlink_targets%20Method.md)|Desvincula todos los bloques de destino desde este objeto `source_block`. \(Invalida [ISource::unlink\_targets](../Topic/ISource::unlink_targets%20Method.md).\)|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[source\_block::accept\_message \(Método\)](../Topic/source_block::accept_message%20Method.md)|Cuando se invalida en una clase derivada, acepta un mensaje proporcionado por el origen.  Los bloques de mensaje deberían invalidar este método para validar `_MsgId` y devolver un mensaje.|  
|[source\_block::async\_send \(Método\)](../Topic/source_block::async_send%20Method.md)|De forma asincrónica, pone en la cola a los mensajes e inicia una tarea de propagación, si esto no se ha hecho ya.|  
|[source\_block::consume\_message \(Método\)](../Topic/source_block::consume_message%20Method.md)|Cuando se invalida en una clase derivada, consume un mensaje reservado previamente.|  
|[source\_block::enable\_batched\_processing \(Método\)](../Topic/source_block::enable_batched_processing%20Method.md)|Habilita el procesamiento por lotes para este bloque.|  
|[source\_block::initialize\_source \(Método\)](../Topic/source_block::initialize_source%20Method.md)|Inicializa `message_propagator` dentro de este `source_block`.|  
|[source\_block::link\_target\_notification \(Método\)](../Topic/source_block::link_target_notification%20Method.md)|Una devolución de llamada que notifica que se ha vinculado un nuevo destino a este objeto `source_block`.|  
|[source\_block::process\_input\_messages \(Método\)](../Topic/source_block::process_input_messages%20Method.md)|Mensajes de entrada de proceso.  Esto sólo es útil para los bloques propagador, que derivan de source\_block|  
|[source\_block::propagate\_output\_messages \(Método\)](../Topic/source_block::propagate_output_messages%20Method.md)|Mensajes de la propagación de los destinos.|  
|[source\_block::propagate\_to\_any\_targets \(Método\)](../Topic/source_block::propagate_to_any_targets%20Method.md)|Cuando se invalida en una clase derivada, propaga el mensaje dado a cualquiera o a todos los destinos vinculados.  Esta es la rutina de propagación principal para los bloques de mensaje.|  
|[source\_block::release\_message \(Método\)](../Topic/source_block::release_message%20Method.md)|Cuando se invalida en una clase derivada, libera una reserva de mensaje anterior.|  
|[source\_block::remove\_targets \(Método\)](../Topic/source_block::remove_targets%20Method.md)|Quita todos los vínculos de destino para este bloque de orígenes.  Se debería llamar a esto desde el destructor.|  
|[source\_block::reserve\_message \(Método\)](../Topic/source_block::reserve_message%20Method.md)|Cuando se invalida en una clase derivada, reserva un mensaje ofrecido previamente por este objeto `source_block`.|  
|[source\_block::resume\_propagation \(Método\)](../Topic/source_block::resume_propagation%20Method.md)|Cuando se invalida en una clase derivada, reanuda la propagación después de liberar una reserva.|  
|[source\_block::sync\_send \(Método\)](../Topic/source_block::sync_send%20Method.md)|De forma sincrónica, pone en la cola a los mensajes e inicia una tarea de propagación, si esto no se ha hecho ya.|  
|[source\_block::unlink\_target\_notification \(Método\)](../Topic/source_block::unlink_target_notification%20Method.md)|Una devolución de llamada que notifica que se ha desvinculado un destino de este objeto `source_block`.|  
|[source\_block::wait\_for\_outstanding\_async\_sends \(Método\)](../Topic/source_block::wait_for_outstanding_async_sends%20Method.md)|Espera a que todas las propagaciones asincrónicas se completen.  Esta espera de vuelta específica del propagador se usa en destructores de bloques de mensaje para asegurarse de que todas las propagaciones asincrónicas tienen tiempo para finalizar antes de destruir el bloque.|  
  
## Comentarios  
 Los bloques de mensaje deberían derivar de este bloque para aprovechar la administración de vínculos y la sincronización que proporciona esta clase.  
  
## Jerarquía de herencia  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 `source_block`  
  
## Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [ISource \(Clase\)](../../../parallel/concrt/reference/isource-class.md)