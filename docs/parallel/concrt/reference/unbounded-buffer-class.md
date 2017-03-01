---
title: Clase unbounded_buffer | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- unbounded_buffer
dev_langs:
- C++
ms.assetid: 6b1a939a-1819-4385-b1d8-708f83d4ec47
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 561f2eea7a2eb19d8cc0162df8bf659f22da1065
ms.lasthandoff: 02/24/2017

---


Un bloque de mensajería `unbounded_buffer` es un bloque `propagator_block` de destino único, de varios orígenes y ordenado capaz de almacenar un número ilimitado de mensajes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<  
   class             _Type  
>  
class unbounded_buffer : public propagator_block<multi_link_registry<ITarget<            _Type>>, multi_link_registry<ISource<            _Type>>>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `_Type`  
 El tipo de carga de los mensajes almacenados y propagados por el búfer.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[unbounded_buffer Constructor](#ctor)|Sobrecargado. Construye un `unbounded_buffer` bloque de mensajería.|  
|[~ unbounded_buffer (destructor)](#dtor)|Destruye el `unbounded_buffer` bloque de mensajería.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[dequeue (método)](#dequeue)|Quita un elemento de la `unbounded_buffer` bloque de mensajería.|  
|[enqueue (método)](#enqueue)|Agrega un elemento a la `unbounded_buffer` bloque de mensajería.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[accept_message (método)](#accept_message)|Acepta un mensaje que fue proporcionado por este `unbounded_buffer` bloque de mensajería, transfiriendo la propiedad al llamador.|  
|[consume_message (método)](#consume_message)|Consume un mensaje proporcionado anteriormente por el `unbounded_buffer` bloque de mensajería y reservado por el destino, transfiriendo la propiedad al llamador.|  
|[link_target_notification (método)](#link_target_notification)|Una devolución de llamada que notifica que se ha vinculado un nuevo destino a este `unbounded_buffer` bloque de mensajería.|  
|[process_input_messages (método)](#process_input_messages)|Sitios de la `message``_PMessage` en este `unbounded_buffer` bloque de mensajería e intenta ofrecerlo a todos los destinos vinculados.|  
|[propagate_message (método)](#propagate_message)|Un mensaje de forma asincrónica, pasa un `ISource` este bloque `unbounded_buffer` bloque de mensajería. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.|  
|[propagate_output_messages (método)](#propagate_output_messages)|Sitios de la `message``_PMessage` en este `unbounded_buffer` bloque de mensajería e intenta ofrecerlo a todos los destinos vinculados. (Invalida [source_block:: propagate_output_messages](source-block-class.md#propagate_output_messages).)|  
|[release_message (método)](#release_message)|Libera una reserva de mensaje anterior. (Invalida [source_block:: release_message](source-block-class.md#release_message).)|  
|[reserve_message (método)](#reserve_message)|Reserva un mensaje ofrecido previamente por este `unbounded_buffer` bloque de mensajería. (Invalida [source_block:: reserve_message](source-block-class.md#reserve_message).)|  
|[resume_propagation (método)](#resume_propagation)|Reanuda la propagación una vez liberada una reserva. (Invalida [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|  
|[send_message (método)](#send_message)|Un mensaje de forma sincrónica, pasa un `ISource` este bloque `unbounded_buffer` bloque de mensajería. Se invoca con el `send` método, cuando se llama a un bloque de origen.|  
|[supports_anonymous_source (método)](#supports_anonymous_source)|Reemplaza el `supports_anonymous_source` método para indicar que este bloque puede aceptar mensajes ofrecidos por un origen que no está vinculado. (Invalida [ITarget:: Supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|  

 Para obtener más información, consulte [bloques de mensajes asincrónicos](../asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `unbounded_buffer`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-nameacceptmessagea-acceptmessage"></a><a name="accept_message"></a>accept_message 

 Acepta un mensaje que fue proporcionado por este `unbounded_buffer` bloque de mensajería, transfiriendo la propiedad al llamador.  
  
```  
virtual message<_Type> * accept_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la ofrecida `message` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `message` que el llamador tiene ahora la propiedad de objeto.  
  
##  <a name="a-nameconsumemessagea-consumemessage"></a><a name="consume_message"></a>consume_message 

 Consume un mensaje proporcionado anteriormente por el `unbounded_buffer` bloque de mensajería y reservado por el destino, transfiriendo la propiedad al llamador.  
  
```  
virtual message<_Type> * consume_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la `message` objeto consumido.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `message` que el llamador tiene ahora la propiedad de objeto.  
  
### <a name="remarks"></a>Comentarios  
 Similar a `accept`, pero siempre va precedido por una llamada a `reserve`.  
  
##  <a name="a-namedequeuea-dequeue"></a><a name="dequeue"></a>eliminación de cola 

 Quita un elemento de la `unbounded_buffer` bloque de mensajería.  
  
```  
_Type dequeue();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La carga del mensaje quitado de la `unbounded_buffer`.  
  
##  <a name="a-nameenqueuea-enqueue"></a><a name="enqueue"></a>poner en cola 

 Agrega un elemento a la `unbounded_buffer` bloque de mensajería.  
  
```  
bool enqueue(  
   _Type const&                 _Item  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Item`  
 Elemento que se va a agregar.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si se aceptó el elemento, `false` en caso contrario.  
  
##  <a name="a-namelinktargetnotificationa-linktargetnotification"></a><a name="link_target_notification"></a>link_target_notification 

 Una devolución de llamada que notifica que se ha vinculado un nuevo destino a este `unbounded_buffer` bloque de mensajería.  
  
```  
virtual void link_target_notification(  
   _Inout_ ITarget<_Type> *                 _PTarget  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Puntero al destino recién vinculado.  
  
##  <a name="a-namepropagatemessagea-propagatemessage"></a><a name="propagate_message"></a>propagate_message 

 Un mensaje de forma asincrónica, pasa un `ISource` este bloque `unbounded_buffer` bloque de mensajería. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.  
  
```  
virtual message_status propagate_message(  
   _Inout_ message<_Type> *                 _PMessage,  
   _Inout_ ISource<_Type> *                 _PSource  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
 Un puntero al objeto `message`.  
  
 `_PSource`  
 Un puntero al bloque de origen que proporciona el mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [message_status](concurrency-namespace-enums.md#message_status) indicación de lo que el destino decidió hacer con el mensaje.  
  
##  <a name="a-namepropagateoutputmessagesa-propagateoutputmessages"></a><a name="propagate_output_messages"></a>propagate_output_messages 

 Sitios de la `message``_PMessage` en este `unbounded_buffer` bloque de mensajería e intenta ofrecerlo a todos los destinos vinculados.  
  
```  
virtual void propagate_output_messages();  
```  
  
### <a name="remarks"></a>Comentarios  
 Si otro mensaje ya está delante de este en el `unbounded_buffer`, propagación a los destinos vinculados no se producirá hasta que se han aceptado o consumido todos los mensajes anteriores. El primer vinculado destino correctamente `accept` o `consume` el mensaje toma posesión y ningún otro destino, a continuación, puede obtener el mensaje.  
  
##  <a name="a-nameprocessinputmessagesa-processinputmessages"></a><a name="process_input_messages"></a>process_input_messages 

 Sitios de la `message``_PMessage` en este `unbounded_buffer` bloque de mensajería e intenta ofrecerlo a todos los destinos vinculados.  
  
```  
virtual void process_input_messages(  
   _Inout_ message<_Type> *                 _PMessage  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
  
##  <a name="a-namereleasemessagea-releasemessage"></a><a name="release_message"></a>release_message 

 Libera una reserva de mensaje anterior.  
  
```  
virtual void release_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la `message` del objeto que se libera.  
  
##  <a name="a-namereservemessagea-reservemessage"></a><a name="reserve_message"></a>reserve_message 

 Reserva un mensaje ofrecido previamente por este `unbounded_buffer` bloque de mensajería.  
  
```  
virtual bool reserve_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la `message` objeto va a reservar.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el mensaje se ha reservado correctamente, `false` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Después de `reserve` se llama, si devuelve `true`, `consume` o `release` se debe llamar para aceptar o liberar la propiedad del mensaje.  
  
##  <a name="a-nameresumepropagationa-resumepropagation"></a><a name="resume_propagation"></a>resume_propagation 

 Reanuda la propagación una vez liberada una reserva.  
  
```  
virtual void resume_propagation();  
```  
  
##  <a name="a-namesendmessagea-sendmessage"></a><a name="send_message"></a>send_message 

 Un mensaje de forma sincrónica, pasa un `ISource` este bloque `unbounded_buffer` bloque de mensajería. Se invoca con el `send` método, cuando se llama a un bloque de origen.  
  
```  
virtual message_status send_message(  
   _Inout_ message<_Type> *                 _PMessage,  
   _Inout_ ISource<_Type> *                 _PSource  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
 Un puntero al objeto `message`.  
  
 `_PSource`  
 Un puntero al bloque de origen que proporciona el mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [message_status](concurrency-namespace-enums.md#message_status) indicación de lo que el destino decidió hacer con el mensaje.  
  
##  <a name="a-namesupportsanonymoussourcea-supportsanonymoussource"></a><a name="supports_anonymous_source"></a>supports_anonymous_source 

 Reemplaza el `supports_anonymous_source` método para indicar que este bloque puede aceptar mensajes ofrecidos por un origen que no está vinculado.  
  
```  
virtual bool supports_anonymous_source();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Dado que el bloque no posponer los mensajes que se ofrecen.  
  
##  <a name="a-namectora-unboundedbuffer"></a><a name="ctor"></a>unbounded_buffer 

 Construye un `unbounded_buffer` bloque de mensajería.  
  
```  
unbounded_buffer();  
  
unbounded_buffer(  
   filter_method const&                 _Filter  
);  
  
unbounded_buffer(  
   Scheduler&                 _PScheduler  
);  
  
unbounded_buffer(  
   Scheduler&                 _PScheduler,  
   filter_method const&                 _Filter  
);  
  
unbounded_buffer(  
   ScheduleGroup&                 _PScheduleGroup  
);  
  
unbounded_buffer(  
   ScheduleGroup&                 _PScheduleGroup,  
   filter_method const&                 _Filter  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Filter`  
 Una función de filtro que determina si se deben aceptar los mensajes que se ofrecen.  
  
 `_PScheduler`  
 El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `unbounded_buffer`.  
  
 `_PScheduleGroup`  
 El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `unbounded_buffer`. El objeto `Scheduler` utilizado está implícito en el grupo de programación.  
  
### <a name="remarks"></a>Comentarios  
 El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PScheduleGroup` .  
  
 El tipo `filter_method` es un functor con firma `bool (_Type const &)` que es invocado por este `unbounded_buffer` el bloque de mensajería para determinar si debe aceptar un mensaje proporcionado.  
  
##  <a name="a-namedtora-unboundedbuffer"></a><a name="dtor"></a>~ unbounded_buffer 

 Destruye el `unbounded_buffer` bloque de mensajería.  
  
```  
~unbounded_buffer();  
```  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [Clase overwrite_buffer](overwrite-buffer-class.md)   
 [Clase single_assignment](single-assignment-class.md)



