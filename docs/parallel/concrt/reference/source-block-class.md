---
title: source_block (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- source_block
- AGENTS/concurrency::source_block
- AGENTS/concurrency::source_block::source_block
- AGENTS/concurrency::source_block::accept
- AGENTS/concurrency::source_block::acquire_ref
- AGENTS/concurrency::source_block::consume
- AGENTS/concurrency::source_block::link_target
- AGENTS/concurrency::source_block::release
- AGENTS/concurrency::source_block::release_ref
- AGENTS/concurrency::source_block::reserve
- AGENTS/concurrency::source_block::unlink_target
- AGENTS/concurrency::source_block::unlink_targets
- AGENTS/concurrency::source_block::accept_message
- AGENTS/concurrency::source_block::async_send
- AGENTS/concurrency::source_block::consume_message
- AGENTS/concurrency::source_block::enable_batched_processing
- AGENTS/concurrency::source_block::initialize_source
- AGENTS/concurrency::source_block::link_target_notification
- AGENTS/concurrency::source_block::process_input_messages
- AGENTS/concurrency::source_block::propagate_output_messages
- AGENTS/concurrency::source_block::propagate_to_any_targets
- AGENTS/concurrency::source_block::release_message
- AGENTS/concurrency::source_block::remove_targets
- AGENTS/concurrency::source_block::reserve_message
- AGENTS/concurrency::source_block::resume_propagation
- AGENTS/concurrency::source_block::sync_send
- AGENTS/concurrency::source_block::unlink_target_notification
- AGENTS/concurrency::source_block::wait_for_outstanding_async_sends
dev_langs: C++
helpviewer_keywords: source_block class
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1709ebf0a831fa7c1bba79b338a2978d6c6dae86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="sourceblock-class"></a>source_block (Clase)
La clase `source_block` es una clase base abstracta solo para bloques de origen. La clase proporciona funcionalidad de administración de vínculo básico, así como comprobaciones de errores frecuentes.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class _TargetLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;
```  
  
#### <a name="parameters"></a>Parámetros  
 `_TargetLinkRegistry`  
 Registro del vínculo que se usará para retener los vínculos de destino.  
  
 `_MessageProcessorType`  
 Tipo de procesador para procesar el mensaje.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`target_iterator`|El iterador para recorrer los destinos conectados.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[source_block)](#ctor)|Construye un objeto `source_block`.|  
|[~ source_block (destructor)](#dtor)|Destruye el objeto `source_block`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Aceptar](#accept)|Acepta un mensaje que fue proporcionado por este `source_block` objeto, transferir la propiedad al llamador.|  
|[acquire_ref](#acquire_ref)|Adquiere un recuento de referencias en el objeto `source_block` objeto, para evitar la eliminación.|  
|[consumir](#consume)|Consume un mensaje ofrecido previamente por este `source_block` objeto y correctamente reservado por el destino, transfiriendo la propiedad al llamador.|  
|[link_target](#link_target)|Vincula un bloque de destino a esta `source_block` objeto.|  
|[release](#release)|Libera una reserva de mensaje correcto anterior.|  
|[release_ref](#release_ref)|Libera un recuento de referencias en el objeto `source_block` objeto.|  
|[reserve](#reserve)|Reserva un mensaje ofrecido previamente por este `source_block` objeto.|  
|[unlink_target](#unlink_target)|Desvincula un bloque de destino de este `source_block` objeto.|  
|[unlink_targets](#unlink_targets)|Desvincula todos los bloques de destino desde este `source_block` objeto. (Invalida [ISource:: Unlink_targets](isource-class.md#unlink_targets).)|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[accept_message](#accept_message)|Cuando se invalida en una clase derivada, acepta un mensaje proporcionado por el origen. Los bloques de mensaje deberían invalidar este método para validar la `_MsgId` y devolver un mensaje.|  
|[async_send](#async_send)|Pone en cola los mensajes de forma asincrónica y se inicia una tarea de propagación, si esto no se ha hecho ya|  
|[consume_message](#consume_message)|Cuando se invalida en una clase derivada, consume un mensaje que se ha reservado previamente.|  
|[enable_batched_processing](#enable_batched_processing)|Permite procesar por lotes de procesamiento para este bloque.|  
|[initialize_source](#initialize_source)|Inicializa el `message_propagator` dentro de este `source_block`.|  
|[link_target_notification](#link_target_notification)|Una devolución de llamada que notifica que se ha vinculado un nuevo destino a este `source_block` objeto.|  
|[process_input_messages](#process_input_messages)|Procesar mensajes de entrada. Esto solo es útil para los bloques propagadores, que derivan de source_block|  
|[propagate_output_messages](#propagate_output_messages)|Propagar los mensajes a los destinos.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Cuando se invalida en una clase derivada, propaga el mensaje especificado a cualquiera de los destinos vinculados. Se trata de la rutina de propagación principal para los bloques de mensajes.|  
|[release_message](#release_message)|Cuando se invalida en una clase derivada, libera una reserva de mensaje anterior.|  
|[remove_targets](#remove_targets)|Quita todos los vínculos de destino para este bloque de origen. Esto se debe llamar desde el destructor.|  
|[reserve_message](#reserve_message)|Cuando se invalida en una clase derivada, reserva un mensaje ofrecido previamente por este `source_block` objeto.|  
|[resume_propagation](#resume_propagation)|Cuando se invalida en una clase derivada, reanuda la propagación después de que se ha liberado una reserva.|  
|[sync_send](#sync_send)|Sincrónicamente pone en cola los mensajes e inicia una tarea de propagación, si esto no se ha hecho ya.|  
|[unlink_target_notification](#unlink_target_notification)|Una devolución de llamada que notifica que un destino se ha desvinculado desde este `source_block` objeto.|  
|[wait_for_outstanding_async_sends](#wait_for_outstanding_async_sends)|Espera a que todas las propagaciones asincrónicas que se complete. Esta espera de vuelta específica del propagador se usa en destructores de bloques de mensajes para asegurarse de que todas las propagaciones asincrónicas tienen tiempo para finalizar antes de destruir el bloque.|  
  
## <a name="remarks"></a>Comentarios  
 Bloques de mensajes deben derivar de este bloque para aprovechar las ventajas de administración de vínculos y sincronización proporcionados por esta clase.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [ISource](isource-class.md)  
  
 `source_block`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="accept"></a>Aceptar 

 Acepta un mensaje que fue proporcionado por este `source_block` objeto, transferir la propiedad al llamador.  
  
```
virtual message<_Target_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la que se ofrecen `message` objeto.  
  
 `_PTarget`  
 Un puntero al bloque de destino que llama a la `accept` método.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `message` que el llamador tiene ahora la propiedad del objeto.  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción si el parámetro `_PTarget` es `NULL`.  
  
 El `accept` método se llama mediante un destino mientras se ofrece un mensaje por este `ISource` bloque. El puntero de mensaje devuelto puede ser diferente de la que se pasa a la `propagate` método de la `ITarget` bloquear, si este origen decide realizar una copia del mensaje.  
  
##  <a name="accept_message"></a>accept_message 

 Cuando se invalida en una clase derivada, acepta un mensaje proporcionado por el origen. Los bloques de mensaje deberían invalidar este método para validar la `_MsgId` y devolver un mensaje.  
  
```
virtual message<_Target_type>* accept_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 La identidad del objeto en tiempo de ejecución de la `message` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al mensaje que el llamador tiene ahora la propiedad.  
  
### <a name="remarks"></a>Comentarios  
 Para transferir la propiedad, se debería devolver el puntero de mensaje original. Para mantener la propiedad, debe se realiza y se devuelve una copia de la carga del mensaje.  
  
##  <a name="acquire_ref"></a>acquire_ref 

 Adquiere un recuento de referencias en el objeto `source_block` objeto, para evitar la eliminación.  
  
```
virtual void acquire_ref(_Inout_ ITarget<_Target_type> *);
```  
  
### <a name="remarks"></a>Comentarios  
 Este método es invocado por un `ITarget` objeto que se está vinculando a este origen durante el `link_target` método.  
  
##  <a name="async_send"></a>async_send 

 Pone en cola los mensajes de forma asincrónica y se inicia una tarea de propagación, si esto no se ha hecho ya  
  
```
virtual void async_send(_Inout_opt_ message<_Target_type>* _Msg);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Msg`  
 Un puntero a un `message` objeto que se va a devolver de forma asincrónica.  
  
##  <a name="consume"></a>consumir 

 Consume un mensaje ofrecido previamente por este `source_block` objeto y correctamente reservado por el destino, transfiriendo la propiedad al llamador.  
  
```
virtual message<_Target_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de reservado `message` objeto.  
  
 `_PTarget`  
 Un puntero al bloque de destino que llama a la `consume` método.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `message` que el llamador tiene ahora la propiedad del objeto.  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción si el parámetro `_PTarget` es `NULL`.  
  
 El método produce una [bad_target](bad-target-class.md) excepción si el parámetro `_PTarget` no representa el destino que llama `reserve`.  
  
 El `consume` método es similar a `accept`, pero siempre debe ir precedido por una llamada a `reserve` que devuelve `true`.  
  
##  <a name="consume_message"></a>consume_message 

 Cuando se invalida en una clase derivada, consume un mensaje que se ha reservado previamente.  
  
```
virtual message<_Target_type>* consume_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la `message` objeto consumido.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al mensaje que el llamador tiene ahora la propiedad.  
  
### <a name="remarks"></a>Comentarios  
 Similar a `accept`, pero siempre va precedido por una llamada a `reserve`.  
  
##  <a name="enable_batched_processing"></a>enable_batched_processing 

 Permite procesar por lotes de procesamiento para este bloque.  
  
```
void enable_batched_processing();
```  
  
##  <a name="initialize_source"></a>initialize_source 

 Inicializa el `message_propagator` dentro de este `source_block`.  
  
```
void initialize_source(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PScheduler`  
 El programador que se usará para programar tareas.  
  
 `_PScheduleGroup`  
 El grupo de programación que se usará para programar tareas.  
  
##  <a name="link_target"></a>link_target 

 Vincula un bloque de destino a esta `source_block` objeto.  
  
```
virtual void link_target(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero a un `ITarget` bloque para vincularlo a este `source_block` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción si el parámetro `_PTarget` es `NULL`.  
  
##  <a name="link_target_notification"></a>link_target_notification 

 Una devolución de llamada que notifica que se ha vinculado un nuevo destino a este `source_block` objeto.  
  
```
virtual void link_target_notification(_Inout_ ITarget<_Target_type> *);
```  
  
##  <a name="process_input_messages"></a>process_input_messages 

 Procesar mensajes de entrada. Esto solo es útil para los bloques propagadores, que derivan de source_block  
  
```
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
  
##  <a name="propagate_output_messages"></a>propagate_output_messages 

 Propagar los mensajes a los destinos.  
  
```
virtual void propagate_output_messages();
```  
  
##  <a name="propagate_to_any_targets"></a>propagate_to_any_targets 

 Cuando se invalida en una clase derivada, propaga el mensaje especificado a cualquiera de los destinos vinculados. Se trata de la rutina de propagación principal para los bloques de mensajes.  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Target_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
 Un puntero al mensaje que se propaguen.  
  
##  <a name="release"></a>la versión 

 Libera una reserva de mensaje correcto anterior.  
  
```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de reservado `message` objeto.  
  
 `_PTarget`  
 Un puntero al bloque de destino que llama a la `release` método.  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción si el parámetro `_PTarget` es `NULL`.  
  
 El método produce una [bad_target](bad-target-class.md) excepción si el parámetro `_PTarget` no representa el destino que llama `reserve`.  
  
##  <a name="release_message"></a>release_message 

 Cuando se invalida en una clase derivada, libera una reserva de mensaje anterior.  
  
```
virtual void release_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la `message` del objeto que se libera.  
  
##  <a name="release_ref"></a>release_ref 

 Libera un recuento de referencias en el objeto `source_block` objeto.  
  
```
virtual void release_ref(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero al bloque de destino que llama a este método.  
  
### <a name="remarks"></a>Comentarios  
 Este método es invocado por un `ITarget` objeto que se desvincula de este origen. El bloque de origen puede liberar cualquier recurso reservado para el bloque de destino.  
  
##  <a name="remove_targets"></a>remove_targets 

 Quita todos los vínculos de destino para este bloque de origen. Esto se debe llamar desde el destructor.  
  
```
void remove_targets();
```  
  
##  <a name="reserve"></a>reservar 

 Reserva un mensaje ofrecido previamente por este `source_block` objeto.  
  
```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la que se ofrecen `message` objeto.  
  
 `_PTarget`  
 Un puntero al bloque de destino que llama a la `reserve` método.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el mensaje se reservó correctamente, `false` en caso contrario. Las reservas pueden tener errores por diversos motivos, incluidos: el mensaje ya se ha reservado o aceptó por otro destino, el origen podría denegar reservas y así sucesivamente.  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción si el parámetro `_PTarget` es `NULL`.  
  
 Después de llamar a `reserve`, si se realiza correctamente, debe llamar a `consume` o `release` para aceptar o ceder la posesión del mensaje, respectivamente.  
  
##  <a name="reserve_message"></a>reserve_message 

 Cuando se invalida en una clase derivada, reserva un mensaje ofrecido previamente por este `source_block` objeto.  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId) = 0;
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la `message` objeto va a reservar.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el mensaje se reservó correctamente, `false` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Después de `reserve` se llama, si devuelve `true`, ya sea `consume` o `release` debe llamarse para aceptar o liberar la propiedad del mensaje.  
  
##  <a name="resume_propagation"></a>resume_propagation 

 Cuando se invalida en una clase derivada, reanuda la propagación después de que se ha liberado una reserva.  
  
```
virtual void resume_propagation() = 0;
```  
  
##  <a name="ctor"></a>source_block) 

 Construye un objeto `source_block`.  
  
```
source_block();
```  
  
##  <a name="dtor"></a>~ source_block) 

 Destruye el objeto `source_block`.  
  
```
virtual ~source_block();
```  
  
##  <a name="sync_send"></a>sync_send 

 Sincrónicamente pone en cola los mensajes e inicia una tarea de propagación, si esto no se ha hecho ya.  
  
```
virtual void sync_send(_Inout_opt_ message<_Target_type>* _Msg);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Msg`  
 Un puntero a un `message` objeto que se va a enviar de forma sincrónica.  
  
##  <a name="unlink_target"></a>unlink_target 

 Desvincula un bloque de destino de este `source_block` objeto.  
  
```
virtual void unlink_target(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero a un `ITarget` bloque desvinculación de esto `source_block` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción si el parámetro `_PTarget` es `NULL`.  
  
##  <a name="unlink_target_notification"></a>unlink_target_notification 

 Una devolución de llamada que notifica que un destino se ha desvinculado desde este `source_block` objeto.  
  
```
virtual void unlink_target_notification(_Inout_ ITarget<_Target_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 El `ITarget` bloque que se desvinculó.  
  
##  <a name="unlink_targets"></a>unlink_targets 

 Desvincula todos los bloques de destino desde este `source_block` objeto.  
  
```
virtual void unlink_targets();
```  
  
##  <a name="wait_for_outstanding_async_sends"></a>wait_for_outstanding_async_sends 

 Espera a que todas las propagaciones asincrónicas que se complete. Esta espera de vuelta específica del propagador se usa en destructores de bloques de mensajes para asegurarse de que todas las propagaciones asincrónicas tienen tiempo para finalizar antes de destruir el bloque.  
  
```
void wait_for_outstanding_async_sends();
```  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [ISource (clase)](isource-class.md)
