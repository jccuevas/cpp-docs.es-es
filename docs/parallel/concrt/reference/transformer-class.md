---
title: Clase transformer | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- transformer
- AGENTS/concurrency::transformer
- AGENTS/concurrency::transformer::transformer
- AGENTS/concurrency::transformer::accept_message
- AGENTS/concurrency::transformer::consume_message
- AGENTS/concurrency::transformer::link_target_notification
- AGENTS/concurrency::transformer::propagate_message
- AGENTS/concurrency::transformer::propagate_to_any_targets
- AGENTS/concurrency::transformer::release_message
- AGENTS/concurrency::transformer::reserve_message
- AGENTS/concurrency::transformer::resume_propagation
- AGENTS/concurrency::transformer::send_message
- AGENTS/concurrency::transformer::supports_anonymous_source
dev_langs: C++
helpviewer_keywords: transformer class
ms.assetid: eea71925-7043-4a92-bfd4-dbc0ece5d081
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 87f4dd90328a647502c50f973d402f7964eaf5f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="transformer-class"></a>Clase transformer
Un bloque de mensajería `transformer` es un bloque `propagator_block` de destino único, de varios orígenes y ordenado capaz de almacenar un número ilimitado de mensajes de un tipo diferente.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class _Input, class _Output>
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>,
    multi_link_registry<ISource<_Input>>>;
```   
  
#### <a name="parameters"></a>Parámetros  
 `_Input`  
 El tipo de carga de los mensajes aceptados por el procesador.  
  
 `_Output`  
 El tipo de carga de los mensajes almacenados y propagado por el búfer.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[clase transformer](#ctor)|Sobrecargado. Construye un `transformer` bloque de mensajería.|  
|[~ transformer (destructor)](#dtor)|Destruye el `transformer` bloque de mensajería.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[accept_message](#accept_message)|Acepta un mensaje que fue proporcionado por este `transformer` bloque de mensajería, transferir la propiedad al llamador.|  
|[consume_message](#consume_message)|Consume un mensaje proporcionado anteriormente por el `transformer` y reservado por el destino, transfiriendo la propiedad al llamador.|  
|[link_target_notification](#link_target_notification)|Una devolución de llamada que notifica que se ha vinculado un nuevo destino a este `transformer` bloque de mensajería.|  
|[propagate_message](#propagate_message)|Un mensaje de forma asincrónica, pasa un `ISource` bloque a este `transformer` bloque de mensajería. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Ejecuta la función de la clase transformer en los mensajes de entrada.|  
|[release_message](#release_message)|Libera una reserva de mensaje anterior. (Invalida [source_block:: release_message](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Reserva un mensaje ofrecido previamente por este `transformer` bloque de mensajería. (Invalida [source_block:: reserve_message](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Reanuda la propagación después de que se ha liberado una reserva. (Invalida [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|  
|[send_message](#send_message)|Un mensaje de forma sincrónica, pasa un `ISource` bloque a este `transformer` bloque de mensajería. Se invoca con el `send` método, cuando se llama a un bloque de origen.|  
|[supports_anonymous_source](#supports_anonymous_source)|Invalida el `supports_anonymous_source` método para indicar que este bloque puede aceptar mensajes ofrecidos por un origen que no está vinculado. (Invalida [ITarget:: Supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [los bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block)](source-block-class.md)  
  
 [propagator_block)](propagator-block-class.md)  
  
 `transformer`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="accept_message"></a>accept_message 

 Acepta un mensaje que fue proporcionado por este `transformer` bloque de mensajería, transferir la propiedad al llamador.  
  
```
virtual message<_Output>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la que se ofrecen `message` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `message` que el llamador tiene ahora la propiedad del objeto.  
  
##  <a name="consume_message"></a>consume_message 

 Consume un mensaje proporcionado anteriormente por el `transformer` y reservado por el destino, transfiriendo la propiedad al llamador.  
  
```
virtual message<_Output>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la `message` objeto consumido.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `message` que el llamador tiene ahora la propiedad del objeto.  
  
### <a name="remarks"></a>Comentarios  
 Similar a `accept`, pero siempre va precedido por una llamada a `reserve`.  
  
##  <a name="link_target_notification"></a>link_target_notification 

 Una devolución de llamada que notifica que se ha vinculado un nuevo destino a este `transformer` bloque de mensajería.  
  
```
virtual void link_target_notification(_Inout_ ITarget<_Output> *);
```  
  
##  <a name="propagate_message"></a>propagate_message 

 Un mensaje de forma asincrónica, pasa un `ISource` bloque a este `transformer` bloque de mensajería. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.  
  
```
virtual message_status propagate_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
 Un puntero al objeto `message`.  
  
 `_PSource`  
 Un puntero al bloque de origen que proporciona el mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 A [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
##  <a name="propagate_to_any_targets"></a>propagate_to_any_targets 

 Ejecuta la función de la clase transformer en los mensajes de entrada.  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Output> *);
```  
  
##  <a name="release_message"></a>release_message 

 Libera una reserva de mensaje anterior.  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la `message` del objeto que se libera.  
  
##  <a name="reserve_message"></a>reserve_message 

 Reserva un mensaje ofrecido previamente por este `transformer` bloque de mensajería.  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la `message` objeto va a reservar.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el mensaje se reservó correctamente, `false` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Después de `reserve` se llama, si devuelve `true`, ya sea `consume` o `release` debe llamarse para aceptar o liberar la propiedad del mensaje.  
  
##  <a name="resume_propagation"></a>resume_propagation 

 Reanuda la propagación después de que se ha liberado una reserva.  
  
```
virtual void resume_propagation();
```  
  
##  <a name="send_message"></a>send_message 

 Un mensaje de forma sincrónica, pasa un `ISource` bloque a este `transformer` bloque de mensajería. Se invoca con el `send` método, cuando se llama a un bloque de origen.  
  
```
virtual message_status send_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
 Un puntero al objeto `message`.  
  
 `_PSource`  
 Un puntero al bloque de origen que proporciona el mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 A [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
##  <a name="supports_anonymous_source"></a>supports_anonymous_source 

 Invalida el `supports_anonymous_source` método para indicar que este bloque puede aceptar mensajes ofrecidos por un origen que no está vinculado.  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Dado que el bloque no posponer mensajes que se ofrecen.  
  
##  <a name="ctor"></a>clase transformer 

 Construye un `transformer` bloque de mensajería.  
  
```
transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Func`  
 Una función que se invocará para cada mensaje aceptado.  
  
 `_PTarget`  
 Un puntero a un bloque de destino para vincular con el convertidor.  
  
 `_Filter`  
 Una función de filtro que determina si se deben aceptar los mensajes que se ofrecen.  
  
 `_PScheduler`  
 El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `transformer`.  
  
 `_PScheduleGroup`  
 El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `transformer`. El objeto `Scheduler` utilizado está implícito en el grupo de programación.  
  
### <a name="remarks"></a>Comentarios  
 El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PScheduleGroup` .  
  
 El tipo `_Transform_method` es un functor con firma `_Output (_Input const &)` que es invocado por este `transformer` bloque de mensajería para procesar un mensaje.  
  
 El tipo `filter_method` es un functor con firma `bool (_Input const &)` que es invocado por este `transformer` bloque de mensajería para determinar si debe aceptar un mensaje proporcionado.  
  
##  <a name="dtor"></a>~ transformer 

 Destruye el `transformer` bloque de mensajería.  
  
```
~transformer();
```  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [call (clase)](call-class.md)
