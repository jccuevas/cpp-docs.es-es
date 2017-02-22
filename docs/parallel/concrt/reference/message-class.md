---
title: "message (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::message"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "message (clase)"
ms.assetid: 3e1f3505-6c0c-486c-8191-666d0880ec62
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# message (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

El sobre del mensaje básico que contiene la carga de datos que se pasa entre bloques de mensajería.  
  
## Sintaxis  
  
```  
template<  
   class _Type  
>  
class message : public ::Concurrency::details::_Runtime_object;  
```  
  
#### Parámetros  
 `_Type`  
 El tipo de datos de la carga dentro en el mensaje.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`type`|Un alias de tipo para `_Type`.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[message::message \(Constructor\)](../Topic/message::message%20Constructor.md)|Sobrecargado.  Construye un objeto `message`.|  
|[message::~message \(Destructor\)](../Topic/message::~message%20Destructor.md)|Destruye el objeto `message`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[message::add\_ref \(Método\)](../Topic/message::add_ref%20Method.md)|Se agrega al contador de referencias para el objeto de `message`.  Se usa para bloques de mensaje que necesitan el recuento de referencias para determinar la duración del mensaje.|  
|[message::msg\_id \(Método\)](../Topic/message::msg_id%20Method.md)|Devuelve el identificador del objeto `message`.|  
|[message::remove\_ref \(Método\)](../Topic/message::remove_ref%20Method.md)|Resta del recuento de referencias para el objeto de `message`.  Se usa para bloques de mensaje que necesitan el recuento de referencias para determinar la duración del mensaje.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[message::payload \(Miembro de datos\)](../Topic/message::payload%20Data%20Member.md)|La carga del objeto `message`.|  
  
## Comentarios  
 Para obtener más información, vea [Bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## Jerarquía de herencia  
 `message`  
  
## Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)