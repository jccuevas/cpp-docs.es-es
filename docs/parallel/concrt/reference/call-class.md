---
title: "Clase call | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::call"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "call (clase)"
ms.assetid: 1521970a-1e9c-4b0c-a681-d18e40976f49
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# Clase call
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Un bloque de mensajería `call` es un `target_block` con varios orígenes y ordenado, que invoca una función especificada al recibir un mensaje.  
  
## Sintaxis  
  
```  
template<  
   class _Type,  
   class _FunctorType = std::tr1::function<void(_Type const&)>  
>  
class call : public target_block<multi_link_registry<ISource<_Type>>>;  
```  
  
#### Parámetros  
 `_Type`  
 El tipo de carga de los mensajes propagados a este búfer.  
  
 `_FunctorType`  
 La firma de funciones que este bloque puede aceptar.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[call::call \(Constructor\)](../Topic/call::call%20Constructor.md)|Sobrecargado.  Construye un bloque de mensajería `call`.|  
|[call::~call \(Destructor\)](../Topic/call::~call%20Destructor.md)|Destruye el bloque de mensajería `call`.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[call::process\_input\_messages \(Método\)](../Topic/call::process_input_messages%20Method.md)|Ejecuta la función de llamada en los mensajes entrantes.|  
|[call::process\_message \(Método\)](../Topic/call::process_message%20Method.md)|Procesa un mensaje que fue aceptado por este bloque de mensajería `call`.|  
|[call::propagate\_message \(Método\)](../Topic/call::propagate_message%20Method.md)|De forma asincrónica, pasa un mensaje de un bloque `ISource` a este bloque de mensajería `call`.  Lo invoca el método `propagate`, cuando lo llama un bloque de origen.|  
|[call::send\_message \(Método\)](../Topic/call::send_message%20Method.md)|De forma sincrónica, pasa un mensaje de un bloque `ISource` a este bloque de mensajería `call`.  Lo invoca el método `send`, cuando lo llama un bloque de origen.|  
|[call::supports\_anonymous\_source \(Método\)](../Topic/call::supports_anonymous_source%20Method.md)|Invalida el método de `supports_anonymous_source` para indicar que este bloque puede aceptar mensajes proporcionados al por un origen que no están vinculados. \(Reemplaza [ITarget::supports\_anonymous\_source](../Topic/ITarget::supports_anonymous_source%20Method.md).\)|  
  
## Comentarios  
 Para obtener más información, vea [Bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## Jerarquía de herencia  
 [ITarget](../../../parallel/concrt/reference/itarget-class.md)  
  
 [target\_block](../../../parallel/concrt/reference/target-block-class.md)  
  
 `call`  
  
## Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Clase transformer](../../../parallel/concrt/reference/transformer-class.md)