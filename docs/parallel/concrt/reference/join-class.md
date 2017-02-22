---
title: "join (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::join"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "join (clase)"
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# join (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Un bloque de mensajería `join` es un bloque `propagator_block` de destino único y de varios orígenes ordenado, que combina los mensajes de tipo `_Type` de cada uno de sus orígenes.  
  
## Sintaxis  
  
```  
template<  
   class _Type,  
   join_type _Jtype = non_greedy  
>  
class join : public propagator_block<single_link_registry<ITarget<std::vector<_Type>>>, multi_link_registry<ISource<_Type>>>;  
```  
  
#### Parámetros  
 `_Type`  
 El tipo de carga de los mensajes combinados y propagados por el bloque.  
  
 `_Jtype`  
 El tipo de bloque `join` es `greedy` o `non_greedy`  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[join::join \(Constructor\)](../Topic/join::join%20Constructor.md)|Sobrecargado.  Construye un bloque de mensajería `join`.|  
|[join::~join \(Destructor\)](../Topic/join::~join%20Destructor.md)|Destruye el bloque `join`.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[join::accept\_message \(Método\)](../Topic/join::accept_message%20Method.md)|Acepta un mensaje que fue proporcionado por este bloque de mensajería `join`, transfiriendo la propiedad al llamador.|  
|[join::consume\_message \(Método\)](../Topic/join::consume_message%20Method.md)|Consume un mensaje que fue proporcionado anteriormente por el bloque de mensajería `join` y reservado por el destino, transfiriendo la propiedad al llamador.|  
|[join::link\_target\_notification \(Método\)](../Topic/join::link_target_notification%20Method.md)|Una devolución de llamada que notifica que se ha vinculado un nuevo destino a este bloque de mensajería `join`.|  
|[join::propagate\_message \(Método\)](../Topic/join::propagate_message%20Method.md)|De forma asincrónica, pasa un mensaje de un bloque `ISource` a este bloque de mensajería `join`.  Lo invoca el método `propagate`, cuando lo llama un bloque de origen.|  
|[join::propagate\_to\_any\_targets \(Método\)](../Topic/join::propagate_to_any_targets%20Method.md)|Construye un mensaje de salida que contiene un mensaje de entrada de cada origen cuando todos ellos han propagado un mensaje.  Envía este mensaje de resultados a cada uno de sus objetivos.|  
|[join::release\_message \(Método\)](../Topic/join::release_message%20Method.md)|Libera una reserva de mensaje anterior. \(Invalida [source\_block::release\_message](../Topic/source_block::release_message%20Method.md).\)|  
|[join::reserve\_message \(Método\)](../Topic/join::reserve_message%20Method.md)|Reserva un mensaje ofrecido previamente por este bloque de mensajería `join`. \(Invalida [source\_block::reserve\_message](../Topic/source_block::reserve_message%20Method.md).\)|  
|[join::resume\_propagation \(Método\)](../Topic/join::resume_propagation%20Method.md)|Reanuda la propagación una vez liberada una reserva. \(Invalida [source\_block::resume\_propagation](../Topic/source_block::resume_propagation%20Method.md).\)|  
  
## Comentarios  
 Para obtener más información, vea [Bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## Jerarquía de herencia  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 [source\_block](../../../parallel/concrt/reference/source-block-class.md)  
  
 [propagator\_block](../../../parallel/concrt/reference/propagator-block-class.md)  
  
 `join`  
  
## Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Clase choice](../../../parallel/concrt/reference/choice-class.md)   
 [multitype\_join \(Clase\)](../../../parallel/concrt/reference/multitype-join-class.md)   
 [join\_type \(Enumeración\)](../Topic/join_type%20Enumeration.md)