---
title: Clase single_assignment | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::single_assignment
dev_langs:
- C++
helpviewer_keywords:
- single_assignment class
ms.assetid: ccc34728-8de9-4e07-b83d-a36a58d9d2b9
caps.latest.revision: 21
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
ms.openlocfilehash: a2a500353b06219713c5d9f3e68f82b247c1604f
ms.lasthandoff: 02/24/2017

---
# <a name="singleassignment-class"></a>Clase single_assignment
Un bloque de mensajería `single_assignment` es un bloque `propagator_block` de destino único, de varios orígenes y ordenado capaz de almacenar un único `message` de una sola escritura.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>
class single_assignment : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de carga del mensaje almacenado y propagado por el búfer.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[single_assignment Constructor](#ctor)|Sobrecargado. Construye un `single_assignment` bloque de mensajería.|  
|[~ single_assignment (destructor)](#dtor)|Destruye el `single_assignment` bloque de mensajería.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[has_value (método)](#has_value)|Comprueba si este `single_assignment` bloque de mensajería se ha inicializado con un valor aún.|  
|[valor (método)](#value)|Obtiene una referencia a la carga actual del mensaje se almacenan en la `single_assignment` bloque de mensajería.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[accept_message (método)](#accept_message)|Acepta un mensaje que fue proporcionado por este `single_assignment` bloque de mensajería, devolviendo una copia del mensaje al llamador.|  
|[consume_message (método)](#consume_message)|Consume un mensaje proporcionado anteriormente por el `single_assignment` y reservado por el destino, devolviendo una copia del mensaje al llamador.|  
|[link_target_notification (método)](#link_target_notification)|Una devolución de llamada que notifica que se ha vinculado un nuevo destino a este `single_assignment` bloque de mensajería.|  
|[propagate_message (método)](#propagate_message)|Un mensaje de forma asincrónica, pasa un `ISource` este bloque `single_assignment` bloque de mensajería. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.|  
|[propagate_to_any_targets (método)](#propagate_to_any_targets)|Sitios de la `message``_PMessage` en este `single_assignment` bloque de mensajería y ofrece a todos los destinos vinculados.|  
|[release_message (método)](#release_message)|Libera una reserva de mensaje anterior. (Invalida [source_block:: release_message](source-block-class.md#release_message).)|  
|[reserve_message (método)](#reserve_message)|Reserva un mensaje ofrecido previamente por este `single_assignment` bloque de mensajería. (Invalida [source_block:: reserve_message](source-block-class.md#reserve_message).)|  
|[resume_propagation (método)](#resume_propagation)|Reanuda la propagación una vez liberada una reserva. (Invalida [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|  
|[send_message (método)](#send_message)|Un mensaje de forma sincrónica, pasa un `ISource` este bloque `single_assignment` bloque de mensajería. Se invoca con el `send` método, cuando se llama a un bloque de origen.|  
  
## <a name="remarks"></a>Comentarios  
 Un `single_assignment` bloque de mensajería propaga las copias de su mensaje a cada destino.  
  
 Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `single_assignment`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-nameacceptmessagea-acceptmessage"></a><a name="accept_message"></a>accept_message 

 Acepta un mensaje que fue proporcionado por este `single_assignment` bloque de mensajería, devolviendo una copia del mensaje al llamador.  
  
```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la ofrecida `message` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `message` que el llamador tiene ahora la propiedad de objeto.  
  
### <a name="remarks"></a>Comentarios  
 El `single_assignment` mensajería bloque devuelve copias del mensaje a sus destinos, en lugar de transferir la propiedad del mensaje creencias.  
  
##  <a name="a-nameconsumemessagea-consumemessage"></a><a name="consume_message"></a>consume_message 

 Consume un mensaje proporcionado anteriormente por el `single_assignment` y reservado por el destino, devolviendo una copia del mensaje al llamador.  
  
```
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la `message` objeto consumido.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `message` que el llamador tiene ahora la propiedad de objeto.  
  
### <a name="remarks"></a>Comentarios  
 Similar a `accept`, pero siempre va precedido por una llamada a `reserve`.  
  
##  <a name="a-namehasvaluea-hasvalue"></a><a name="has_value"></a>has_value 

 Comprueba si este `single_assignment` bloque de mensajería se ha inicializado con un valor aún.  
  
```
bool has_value() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el bloque ha recibido un valor `false` en caso contrario.  
  
##  <a name="a-namelinktargetnotificationa-linktargetnotification"></a><a name="link_target_notification"></a>link_target_notification 

 Una devolución de llamada que notifica que se ha vinculado un nuevo destino a este `single_assignment` bloque de mensajería.  
  
```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Puntero al destino recién vinculado.  
  
##  <a name="a-namepropagatemessagea-propagatemessage"></a><a name="propagate_message"></a>propagate_message 

 Un mensaje de forma asincrónica, pasa un `ISource` este bloque `single_assignment` bloque de mensajería. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.  
  
```
virtual message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
 Un puntero al objeto `message`.  
  
 `_PSource`  
 Un puntero al bloque de origen que proporciona el mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
##  <a name="a-namepropagatetoanytargetsa-propagatetoanytargets"></a><a name="propagate_to_any_targets"></a>propagate_to_any_targets 

 Sitios de la `message``_PMessage` en este `single_assignment` bloque de mensajería y ofrece a todos los destinos vinculados.  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
 Un puntero a un `message` que `single_assignment` tome posesión de bloque de mensajería.  
  
##  <a name="a-namereleasemessagea-releasemessage"></a><a name="release_message"></a>release_message 

 Libera una reserva de mensaje anterior.  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la `message` del objeto que se libera.  
  
##  <a name="a-namereservemessagea-reservemessage"></a><a name="reserve_message"></a>reserve_message 

 Reserva un mensaje ofrecido previamente por este `single_assignment` bloque de mensajería.  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
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

 Un mensaje de forma sincrónica, pasa un `ISource` este bloque `single_assignment` bloque de mensajería. Se invoca con el `send` método, cuando se llama a un bloque de origen.  
  
```
virtual message_status send_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PMessage`  
 Un puntero al objeto `message`.  
  
 `_PSource`  
 Un puntero al bloque de origen que proporciona el mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.  
  
##  <a name="a-namectora-singleassignment"></a><a name="ctor"></a>single_assignment 

 Construye un `single_assignment` bloque de mensajería.  
  
```
single_assignment();

single_assignment(
    filter_method const& _Filter);

single_assignment(
    Scheduler& _PScheduler);

single_assignment(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

single_assignment(
    ScheduleGroup& _PScheduleGroup);

single_assignment(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Filter`  
 Una función de filtro que determina si se deben aceptar los mensajes que se ofrecen.  
  
 `_PScheduler`  
 El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `single_assignment`.  
  
 `_PScheduleGroup`  
 El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `single_assignment`. El objeto `Scheduler` utilizado está implícito en el grupo de programación.  
  
### <a name="remarks"></a>Comentarios  
 El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PScheduleGroup` .  
  
 El tipo `filter_method` es un functor con firma `bool (T const &)` que es invocado por este `single_assignment` el bloque de mensajería para determinar si debe aceptar un mensaje proporcionado.  
  
##  <a name="a-namedtora-singleassignment"></a><a name="dtor"></a>~ single_assignment 

 Destruye el `single_assignment` bloque de mensajería.  
  
```
~single_assignment();
```  
  
##  <a name="a-namevaluea-value"></a><a name="value"></a>valor 

 Obtiene una referencia a la carga actual del mensaje se almacenan en la `single_assignment` bloque de mensajería.  
  
```
T const& value();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La carga del mensaje almacenado.  
  
### <a name="remarks"></a>Comentarios  
 Este método esperará hasta que llegue un mensaje si ningún mensaje actualmente se almacena en el `single_assignment` bloque de mensajería.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [Clase overwrite_buffer](overwrite-buffer-class.md)   
 [Clase unbounded_buffer](unbounded-buffer-class.md)


