---
title: message_processor (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- message_processor
- AGENTS/concurrency::message_processor
- AGENTS/concurrency::message_processor::async_send
- AGENTS/concurrency::message_processor::sync_send
- AGENTS/concurrency::message_processor::wait
- AGENTS/concurrency::message_processor::process_incoming_message
dev_langs:
- C++
helpviewer_keywords:
- message_processor class
ms.assetid: 23afb052-daa7-44ed-bf24-d2513db748da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95e95cc84ca999402e0d64c0699750bb92203cef
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="messageprocessor-class"></a>message_processor (Clase)
La clase `message_processor` es la clase base abstracta del procesamiento de objetos `message`. No hay ninguna garantía en la clasificación de los mensajes.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>
class message_processor;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos de la carga en los mensajes controlados por este `message_processor` objeto.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`type`|Un alias de tipo para `T`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[async_send](#async_send)|Cuando se invalida en una clase derivada, coloca mensajes en el bloque de forma asincrónica.|  
|[sync_send](#sync_send)|Cuando se invalida en una clase derivada, coloca mensajes en el bloque de forma sincrónica.|  
|[espera](#wait)|Cuando se invalida en una clase derivada, espera a que todas las operaciones asincrónicas que se complete.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[process_incoming_message](#process_incoming_message)|Cuando se invalida en una clase derivada, realiza el procesamiento de mensajes hacia delante en el bloque. Se llama una vez cada vez que se agrega un nuevo mensaje y se encuentra la cola esté vacío.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `message_processor`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="async_send"></a> async_send 

 Cuando se invalida en una clase derivada, coloca mensajes en el bloque de forma asincrónica.  
  
```
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Msg`  
 Un `message` objeto que se va a enviar de forma asincrónica.  
  
### <a name="remarks"></a>Comentarios  
 Las implementaciones del procesador deberían invalidar este método.  
  
##  <a name="process_incoming_message"></a> process_incoming_message 

 Cuando se invalida en una clase derivada, realiza el procesamiento de mensajes hacia delante en el bloque. Se llama una vez cada vez que se agrega un nuevo mensaje y se encuentra la cola esté vacío.  
  
```
virtual void process_incoming_message() = 0;
```  
  
### <a name="remarks"></a>Comentarios  
 Las implementaciones de bloque de mensajes deben invalidar este método.  
  
##  <a name="sync_send"></a> sync_send 

 Cuando se invalida en una clase derivada, coloca mensajes en el bloque de forma sincrónica.  
  
```
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Msg`  
 Un `message` objeto que se va a enviar de forma sincrónica.  
  
### <a name="remarks"></a>Comentarios  
 Las implementaciones del procesador deberían invalidar este método.  
  
##  <a name="wait"></a> espera 

 Cuando se invalida en una clase derivada, espera a que todas las operaciones asincrónicas que se complete.  
  
```
virtual void wait() = 0;
```  
  
### <a name="remarks"></a>Comentarios  
 Las implementaciones del procesador deberían invalidar este método.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [ordered_message_processor (clase)](ordered-message-processor-class.md)
