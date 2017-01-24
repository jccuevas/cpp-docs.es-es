---
title: "Clase single_assignment | Microsoft Docs"
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
  - "agents/concurrency::single_assignment"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "single_assignment (clase)"
ms.assetid: ccc34728-8de9-4e07-b83d-a36a58d9d2b9
caps.latest.revision: 21
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clase single_assignment
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Un bloque de mensajería `single_assignment` es un bloque `propagator_block` de destino único, de varios orígenes y ordenado capaz de almacenar un único `message` de una sola escritura.  
  
## Sintaxis  
  
```  
template<  
   class _Type  
>  
class single_assignment : public propagator_block<multi_link_registry<ITarget<_Type>>, multi_link_registry<ISource<_Type>>>;  
```  
  
#### Parámetros  
 `_Type`  
 El tipo de carga del mensaje almacenado y propagado por el búfer.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[single\_assignment::single\_assignment \(Constructor\)](../Topic/single_assignment::single_assignment%20Constructor.md)|Sobrecargado.  Construye un bloque de mensajería `single_assignment`.|  
|[single\_assignment::~single\_assignment \(Destructor\)](../Topic/single_assignment::~single_assignment%20Destructor.md)|Destruye el bloque de mensajería `single_assignment`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[single\_assignment::has\_value \(Método\)](../Topic/single_assignment::has_value%20Method.md)|Comprueba si este bloque de mensajería `single_assignment` se ha inicializado con un valor.|  
|[single\_assignment::value \(Método\)](../Topic/single_assignment::value%20Method.md)|Obtiene una referencia a la carga útil actual del mensaje que se está almacenado en el bloque de mensajería `single_assignment`.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[single\_assignment::accept\_message \(Método\)](../Topic/single_assignment::accept_message%20Method.md)|Acepta un mensaje que fue proporcionado por este bloque de mensajería `single_assignment`, devolviendo una copia del mensaje al llamador.|  
|[single\_assignment::consume\_message \(Método\)](../Topic/single_assignment::consume_message%20Method.md)|Consume un mensaje que fue proporcionado anteriormente por `single_assignment` y reservado por el destino, devolviendo una copia del mensaje al llamador.|  
|[single\_assignment::link\_target\_notification \(Método\)](../Topic/single_assignment::link_target_notification%20Method.md)|Una devolución de llamada que notifica que se ha vinculado un nuevo destino a este bloque de mensajería `single_assignment`.|  
|[single\_assignment::propagate\_message \(Método\)](../Topic/single_assignment::propagate_message%20Method.md)|De forma asincrónica, pasa un mensaje de un bloque `ISource` a este bloque de mensajería `single_assignment`.  Lo invoca el método `propagate`, cuando lo llama un bloque de origen.|  
|[single\_assignment::propagate\_to\_any\_targets \(Método\)](../Topic/single_assignment::propagate_to_any_targets%20Method.md)|Coloca `message``_PMessage` en este bloque de mensajería `single_assignment` y lo ofrece a todos los destinos vinculados.|  
|[single\_assignment::release\_message \(Método\)](../Topic/single_assignment::release_message%20Method.md)|Libera una reserva de mensaje anterior. \(Invalida [source\_block::release\_message](../Topic/source_block::release_message%20Method.md).\)|  
|[single\_assignment::reserve\_message \(Método\)](../Topic/single_assignment::reserve_message%20Method.md)|Reserva un mensaje ofrecido previamente por este bloque de mensajería `single_assignment`. \(Invalida [source\_block::reserve\_message](../Topic/source_block::reserve_message%20Method.md).\)|  
|[single\_assignment::resume\_propagation \(Método\)](../Topic/single_assignment::resume_propagation%20Method.md)|Reanuda la propagación una vez liberada una reserva. \(Invalida [source\_block::resume\_propagation](../Topic/source_block::resume_propagation%20Method.md).\)|  
|[single\_assignment::send\_message \(Método\)](../Topic/single_assignment::send_message%20Method.md)|De forma sincrónica, pasa un mensaje de un bloque `ISource` a este bloque de mensajería `single_assignment`.  Lo invoca el método `send`, cuando lo llama un bloque de origen.|  
  
## Comentarios  
 Un bloque de mensajería `single_assignment` propaga las copias de su mensaje a cada destino.  
  
 Para obtener más información, vea [Bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## Jerarquía de herencia  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 [source\_block](../../../parallel/concrt/reference/source-block-class.md)  
  
 [propagator\_block](../../../parallel/concrt/reference/propagator-block-class.md)  
  
 `single_assignment`  
  
## Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Clase overwrite\_buffer](../../../parallel/concrt/reference/overwrite-buffer-class.md)   
 [Clase unbounded\_buffer](../Topic/unbounded_buffer%20Class.md)