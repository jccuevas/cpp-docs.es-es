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
- agents/concurrency::message_processor
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
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 98f1c1072916c4cf3670e40ce0c6ddd1a17f1b63
ms.lasthandoff: 02/24/2017

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
|[async_send (método)](#async_send)|Cuando se invalida en una clase derivada, coloca mensajes en el bloque de forma asincrónica.|  
|[sync_send (método)](#sync_send)|Cuando se invalida en una clase derivada, coloca mensajes en el bloque de forma sincrónica.|  
|[Wait (método)](#wait)|Cuando se invalida en una clase derivada, espera a completar todas las operaciones asincrónicas.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[process_incoming_message (método)](#process_incoming_message)|Cuando se invalida en una clase derivada, realiza el procesamiento de enrutamiento de mensajes en el bloque. Se llama una vez cada vez que se agrega un nuevo mensaje y se encuentra la cola esté vacío.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `message_processor`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-nameasyncsenda-asyncsend"></a><a name="async_send"></a>async_send 

 Cuando se invalida en una clase derivada, coloca mensajes en el bloque de forma asincrónica.  
  
```
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Msg`  
 Un `message` objeto para enviar de forma asincrónica.  
  
### <a name="remarks"></a>Comentarios  
 Las implementaciones del procesador deberían invalidar este método.  
  
##  <a name="a-nameprocessincomingmessagea-processincomingmessage"></a><a name="process_incoming_message"></a>process_incoming_message 

 Cuando se invalida en una clase derivada, realiza el procesamiento de enrutamiento de mensajes en el bloque. Se llama una vez cada vez que se agrega un nuevo mensaje y se encuentra la cola esté vacío.  
  
```
virtual void process_incoming_message() = 0;
```  
  
### <a name="remarks"></a>Comentarios  
 Las implementaciones de bloque de mensajes deben invalidar este método.  
  
##  <a name="a-namesyncsenda-syncsend"></a><a name="sync_send"></a>sync_send 

 Cuando se invalida en una clase derivada, coloca mensajes en el bloque de forma sincrónica.  
  
```
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Msg`  
 Un `message` objeto para enviar de forma sincrónica.  
  
### <a name="remarks"></a>Comentarios  
 Las implementaciones del procesador deberían invalidar este método.  
  
##  <a name="a-namewaita-wait"></a><a name="wait"></a>esperar 

 Cuando se invalida en una clase derivada, espera a completar todas las operaciones asincrónicas.  
  
```
virtual void wait() = 0;
```  
  
### <a name="remarks"></a>Comentarios  
 Las implementaciones del procesador deberían invalidar este método.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [ordered_message_processor (clase)](ordered-message-processor-class.md)

