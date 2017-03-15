---
title: Join (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::join
dev_langs:
- C++
helpviewer_keywords:
- join class
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
caps.latest.revision: 20
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
ms.openlocfilehash: b9671e6c9d29fb5f93977fe080e90dd087429460
ms.lasthandoff: 02/24/2017

---
# <a name="join-class"></a>join (Clase)
Un bloque de mensajería `join` es un bloque `propagator_block` de destino único y de varios orígenes ordenado, que combina los mensajes de tipo `T` de cada uno de sus orígenes.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T,
    join_type _Jtype = non_greedy>
class join : public propagator_block<single_link_registry<ITarget<std::vector<T>>>,
    multi_link_registry<ISource<T>>>;
```   
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de carga de los mensajes combinados y propagados por el bloque.  
  
 `_Jtype`  
 El tipo de `join` bloque es, ya sea `greedy` o`non_greedy`  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[unir el Constructor](#ctor)|Sobrecargado. Construye un `join` bloque de mensajería.|  
|[~ join (destructor)](#dtor)|Destruye el `join` bloque.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[accept_message (método)](#accept_message)|Acepta un mensaje que fue proporcionado por este `join` bloque de mensajería, transfiriendo la propiedad al llamador.|  
|[consume_message (método)](#consume_message)|Consume un mensaje proporcionado anteriormente por el `join` bloque de mensajería y reservado por el destino, transfiriendo la propiedad al llamador.|  
|[link_target_notification (método)](#link_target_notification)|Una devolución de llamada que notifica que se ha vinculado un nuevo destino a este `join` bloque de mensajería.|  
|[propagate_message (método)](#propagate_message)|Un mensaje de forma asincrónica, pasa un `ISource` este bloque `join` bloque de mensajería. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.|  
|[propagate_to_any_targets (método)](#propagate_to_any_targets)|Construye un mensaje de salida que contiene un mensaje de entrada de cada origen cuando todos han propagado un mensaje. Envía este mensaje de salida para cada uno de sus destinos.|  
|[release_message (método)](#release_message)|Libera una reserva de mensaje anterior. (Invalida [source_block:: release_message](source-block-class.md#release_message).)|  
|[reserve_message (método)](#reserve_message)|Reserva un mensaje ofrecido previamente por este `join` bloque de mensajería. (Invalida [source_block:: reserve_message](source-block-class.md#reserve_message).)|  
|[resume_propagation (método)](#resume_propagation)|Reanuda la propagación una vez liberada una reserva. (Invalida [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `join`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-nameacceptmessagea-acceptmessage"></a><a name="accept_message"></a>accept_message 

 Acepta un mensaje que fue proporcionado por este `join` bloque de mensajería, transfiriendo la propiedad al llamador.  
  
```
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la ofrecida `message` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `message` que el llamador tiene ahora la propiedad de objeto.  
  
##  <a name="a-nameconsumemessagea-consumemessage"></a><a name="consume_message"></a>consume_message 

 Consume un mensaje proporcionado anteriormente por el `join` bloque de mensajería y reservado por el destino, transfiriendo la propiedad al llamador.  
  
```
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la `message` objeto consumido.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `message` que el llamador tiene ahora la propiedad de objeto.  
  
### <a name="remarks"></a>Comentarios  
 Similar a `accept`, pero siempre va precedido por una llamada a `reserve`.  
  
##  <a name="a-namectora-join"></a><a name="ctor"></a>combinación 

 Construye un `join` bloque de mensajería.  
  
```
join(
    size_t _NumInputs);

join(
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parámetros  
 `_NumInputs`  
 El número de entradas esto `join` se permitirá el bloque.  
  
 `_Filter`  
 Una función de filtro que determina si se deben aceptar los mensajes que se ofrecen.  
  
 `_PScheduler`  
 El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `join`.  
  
 `_PScheduleGroup`  
 El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `join`. El objeto `Scheduler` utilizado está implícito en el grupo de programación.  
  
### <a name="remarks"></a>Comentarios  
 El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PScheduleGroup` .  
  
 El tipo `filter_method` es un functor con firma `bool (T const &)` que es invocado por este `join` el bloque de mensajería para determinar si debe aceptar un mensaje proporcionado.  
  
##  <a name="a-namedtora-join"></a><a name="dtor"></a>~ join 

 Destruye el `join` bloque.  
  
```
~join();
```  
  
##  <a name="a-namelinktargetnotificationa-linktargetnotification"></a><a name="link_target_notification"></a>link_target_notification 

 Una devolución de llamada que notifica que se ha vinculado un nuevo destino a este `join` bloque de mensajería.  
  
```
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```  
  
##  <a name="a-namepropagatemessagea-propagatemessage"></a><a name="propagate_message"></a>propagate_message 

 Un mensaje de forma asincrónica, pasa un `ISource` este bloque `join` bloque de mensajería. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.  
  
```
message_status propagate_message(
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

 Construye un mensaje de salida que contiene un mensaje de entrada de cada origen cuando todos han propagado un mensaje. Envía este mensaje de salida para cada uno de sus destinos.  
  
```
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
```  
  
##  <a name="a-namereleasemessagea-releasemessage"></a><a name="release_message"></a>release_message 

 Libera una reserva de mensaje anterior.  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la `message` del objeto que se libera.  
  
##  <a name="a-namereservemessagea-reservemessage"></a><a name="reserve_message"></a>reserve_message 

 Reserva un mensaje ofrecido previamente por este `join` bloque de mensajería.  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la ofrecida `message` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el mensaje se ha reservado correctamente, `false` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Después de `reserve` se llama, si devuelve `true`, `consume` o `release` se debe llamar para aceptar o liberar la propiedad del mensaje.  
  
##  <a name="a-nameresumepropagationa-resumepropagation"></a><a name="resume_propagation"></a>resume_propagation 

 Reanuda la propagación una vez liberada una reserva.  
  
```
virtual void resume_propagation();
```  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [Clase Choice](choice-class.md)   
 [multitype_join (clase)](multitype-join-class.md)

