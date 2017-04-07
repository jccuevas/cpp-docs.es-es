---
title: message_processor (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: dff934584179cc58d884be65fdb96cb6c646a4ac
ms.lasthandoff: 03/17/2017

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
  
|Nombre|Descripción|  
|----------|-----------------|  
|`type`|Un alias de tipo para `T`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[async_send](#async_send)|Cuando se invalida en una clase derivada, coloca mensajes en el bloque de forma asincrónica.|  
|[sync_send](#sync_send)|Cuando se invalida en una clase derivada, coloca mensajes en el bloque de forma sincrónica.|  
|[esperar](#wait)|Cuando se invalida en una clase derivada, espera a completar todas las operaciones asincrónicas.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[process_incoming_message](#process_incoming_message)|Cuando se invalida en una clase derivada, realiza el procesamiento de enrutamiento de mensajes en el bloque. Se llama una vez cada vez que se agrega un nuevo mensaje y se encuentra la cola esté vacío.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `message_processor`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="async_send"></a>async_send 

 Cuando se invalida en una clase derivada, coloca mensajes en el bloque de forma asincrónica.  
  
```
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Msg`  
 Un `message` objeto para enviar de forma asincrónica.  
  
### <a name="remarks"></a>Comentarios  
 Las implementaciones del procesador deberían invalidar este método.  
  
##  <a name="process_incoming_message"></a>process_incoming_message 

 Cuando se invalida en una clase derivada, realiza el procesamiento de enrutamiento de mensajes en el bloque. Se llama una vez cada vez que se agrega un nuevo mensaje y se encuentra la cola esté vacío.  
  
```
virtual void process_incoming_message() = 0;
```  
  
### <a name="remarks"></a>Comentarios  
 Las implementaciones de bloque de mensajes deben invalidar este método.  
  
##  <a name="sync_send"></a>sync_send 

 Cuando se invalida en una clase derivada, coloca mensajes en el bloque de forma sincrónica.  
  
```
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Msg`  
 Un `message` objeto para enviar de forma sincrónica.  
  
### <a name="remarks"></a>Comentarios  
 Las implementaciones del procesador deberían invalidar este método.  
  
##  <a name="wait"></a>esperar 

 Cuando se invalida en una clase derivada, espera a completar todas las operaciones asincrónicas.  
  
```
virtual void wait() = 0;
```  
  
### <a name="remarks"></a>Comentarios  
 Las implementaciones del procesador deberían invalidar este método.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [ordered_message_processor (clase)](ordered-message-processor-class.md)

