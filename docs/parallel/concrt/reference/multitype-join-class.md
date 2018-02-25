---
title: multitype_join (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- multitype_join
- AGENTS/concurrency::multitype_join
- AGENTS/concurrency::multitype_join::multitype_join
- AGENTS/concurrency::multitype_join::accept
- AGENTS/concurrency::multitype_join::acquire_ref
- AGENTS/concurrency::multitype_join::consume
- AGENTS/concurrency::multitype_join::link_target
- AGENTS/concurrency::multitype_join::release
- AGENTS/concurrency::multitype_join::release_ref
- AGENTS/concurrency::multitype_join::reserve
- AGENTS/concurrency::multitype_join::unlink_target
- AGENTS/concurrency::multitype_join::unlink_targets
dev_langs:
- C++
helpviewer_keywords:
- multitype_join class
ms.assetid: 236e87a0-4867-49fd-869a-bef4010e49a7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 62d91f878a8330b6e4fe60f7e24ad25c779b868d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="multitypejoin-class"></a>multitype_join (Clase)
Un bloque de mensajería `multitype_join` es un bloque de mensajería de destino único, de varios orígenes, que combina los mensajes de diferentes tipos de cada uno de sus orígenes y ofrece una tupla de los mensajes combinados con sus destinos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<
    typename T,  
    join_type _Jtype = non_greedy  
>  
class multitype_join: public ISource<typename _Unwrap<T>::type>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El `tuple` tipo de carga de los mensajes combinados y propagados por el bloque.  
  
 `_Jtype`  
 El tipo de `join` bloque es, ya sea `greedy` o `non_greedy`  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`type`|Un alias de tipo para `T`.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[multitype_join](#ctor)|Sobrecargado. Construye un bloque de mensajería `multitype_join` .|  
|[~multitype_join Destructor](#dtor)|Destruye el `multitype_join` bloque de mensajería.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[accept](#accept)|Acepta un mensaje que fue proporcionado por este `multitype_join` bloque, transferir la propiedad al llamador.|  
|[acquire_ref](#acquire_ref)|Adquiere un recuento de referencias en el objeto `multitype_join` bloque de mensajería, para evitar la eliminación.|  
|[consume](#consume)|Consume un mensaje proporcionado anteriormente por el `multitype_join` bloque de mensajería y correctamente reservado por el destino, transfiriendo la propiedad al llamador.|  
|[link_target](#link_target)|Vincula un bloque de destino a esta `multitype_join` bloque de mensajería.|  
|[release](#release)|Libera una reserva de mensaje correcto anterior.|  
|[release_ref](#release_ref)|Libera un recuento de referencias en el objeto `multiple_join` bloque de mensajería.|  
|[reserve](#reserve)|Reserva un mensaje ofrecido previamente por este `multitype_join` bloque de mensajería.|  
|[unlink_target](#unlink_target)|Desvincula un bloque de destino de este `multitype_join` bloque de mensajería.|  
|[unlink_targets](#unlink_targets)|Desvincula todos los destinos de este `multitype_join` bloque de mensajería. (Invalida [ISource:: Unlink_targets](isource-class.md#unlink_targets).)|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [los bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [ISource](isource-class.md)  
  
 `multitype_join`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="accept"></a> Aceptar 

 Acepta un mensaje que fue proporcionado por este `multitype_join` bloque, transferir la propiedad al llamador.  
  
```  
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la que se ofrecen `message` objeto.  
  
 `_PTarget`  
 Un puntero al bloque de destino que llama a la `accept` método.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al mensaje que el llamador tiene ahora la propiedad.  
  
##  <a name="acquire_ref"></a> acquire_ref 

 Adquiere un recuento de referencias en el objeto `multitype_join` bloque de mensajería, para evitar la eliminación.  
  
```  
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero al bloque de destino que llama a este método.  
  
### <a name="remarks"></a>Comentarios  
 Este método es invocado por un `ITarget` objeto que se está vinculando a este origen durante el `link_target` método.  
  
##  <a name="consume"></a> Consumir 

 Consume un mensaje proporcionado anteriormente por el `multitype_join` bloque de mensajería y correctamente reservado por el destino, transfiriendo la propiedad al llamador.  
  
```  
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de reservado `message` objeto.  
  
 `_PTarget`  
 Un puntero al bloque de destino que llama a la `consume` método.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `message` que el llamador tiene ahora la propiedad del objeto.  
  
### <a name="remarks"></a>Comentarios  
 El `consume` método es similar a `accept`, pero siempre debe ir precedido por una llamada a `reserve` que devuelve `true`.  
  
##  <a name="link_target"></a> link_target 

 Vincula un bloque de destino a esta `multitype_join` bloque de mensajería.  
  
```  
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero a un `ITarget` bloque para vincularlo a este `multitype_join` bloque de mensajería.  
  
##  <a name="ctor"></a> multitype_join 

 Construye un bloque de mensajería `multitype_join` .  
  
```  
explicit multitype_join(
    T _Tuple);

 
multitype_join(
    Scheduler& _PScheduler,  
    T _Tuple);

 
multitype_join(
    ScheduleGroup& _PScheduleGroup,  
    T _Tuple);

 
multitype_join(
    multitype_join&& _Join);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Tuple`  
 `tuple` de orígenes para este bloque de mensajería `multitype_join` .  
  
 `_PScheduler`  
 El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `multitype_join` .  
  
 `_PScheduleGroup`  
 El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `multitype_join` . El objeto `Scheduler` utilizado está implícito en el grupo de programación.  
  
 `_Join`  
 Bloque de mensajería `multitype_join` desde el que se realizará la copia. Tenga en cuenta que el objeto original es huérfano, por lo que este constructor pasa a ser de movimiento.  
  
### <a name="remarks"></a>Comentarios  
 El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PScheduleGroup` .  
  
 La construcción de movimiento no se lleva acabo con un bloqueo, lo que significa que el usuario debe asegurarse de que no hay ninguna tarea ligera en marcha en el momento del movimiento. De lo contrario, se pueden producir numerosas carreras, que darán lugar a excepciones o a un estado incoherente.  
  
##  <a name="dtor"></a> ~multitype_join 

 Destruye el `multitype_join` bloque de mensajería.  
  
```  
~multitype_join();
```  
  
##  <a name="release"></a> la versión 

 Libera una reserva de mensaje correcto anterior.  
  
```  
virtual void release(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la `message` del objeto que se libera.  
  
 `_PTarget`  
 Un puntero al bloque de destino que llama a la `release` método.  
  
##  <a name="release_ref"></a> release_ref 

 Libera un recuento de referencias en el objeto `multiple_join` bloque de mensajería.  
  
```  
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero al bloque de destino que llama a este método.  
  
### <a name="remarks"></a>Comentarios  
 Este método es invocado por un `ITarget` objeto que se desvincula de este origen. El bloque de origen puede liberar cualquier recurso reservado para el bloque de destino.  
  
##  <a name="reserve"></a> reservar 

 Reserva un mensaje ofrecido previamente por este `multitype_join` bloque de mensajería.  
  
```  
virtual bool reserve(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la `message` objeto va a reservar.  
  
 `_PTarget`  
 Un puntero al bloque de destino que llama a la `reserve` método.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el mensaje se reservó correctamente, `false` en caso contrario. Las reservas pueden tener errores por diversos motivos, incluidos: el mensaje ya se ha reservado o aceptó por otro destino, el origen podría denegar reservas y así sucesivamente.  
  
### <a name="remarks"></a>Comentarios  
 Después de llamar a `reserve`, si se realiza correctamente, debe llamar a `consume` o `release` para aceptar o ceder la posesión del mensaje, respectivamente.  
  
##  <a name="unlink_target"></a> unlink_target 

 Desvincula un bloque de destino de este `multitype_join` bloque de mensajería.  
  
```  
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero a un `ITarget` bloque desvinculación de esto `multitype_join` bloque de mensajería.  
  
##  <a name="unlink_targets"></a> unlink_targets 

 Desvincula todos los destinos de este `multitype_join` bloque de mensajería.  
  
```  
virtual void unlink_targets();
```  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [Clase Choice](choice-class.md)   
 [join (clase)](join-class.md)
