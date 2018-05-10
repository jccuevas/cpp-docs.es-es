---
title: Clase Choice | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- choice
- AGENTS/concurrency::choice
- AGENTS/concurrency::choice::choice
- AGENTS/concurrency::choice::accept
- AGENTS/concurrency::choice::acquire_ref
- AGENTS/concurrency::choice::consume
- AGENTS/concurrency::choice::has_value
- AGENTS/concurrency::choice::index
- AGENTS/concurrency::choice::link_target
- AGENTS/concurrency::choice::release
- AGENTS/concurrency::choice::release_ref
- AGENTS/concurrency::choice::reserve
- AGENTS/concurrency::choice::unlink_target
- AGENTS/concurrency::choice::unlink_targets
- AGENTS/concurrency::choice::value
dev_langs:
- C++
helpviewer_keywords:
- choice class
ms.assetid: 4157a539-d5c2-4161-b1ab-536ce2888397
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 56b936e1ecb3864b7a7bb95f3e552c16d2ce81d0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="choice-class"></a>Clase choice
Un bloque de mensajería `choice` es un bloque de varios orígenes y de destino único que representa una interacción del flujo de control con un conjunto de orígenes. El bloque de elección esperará a cualquiera de los orígenes para generar un mensaje y propagará el índice del origen que generó el mensaje.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<
    class T  
>  
class choice: public ISource<size_t>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Un `tuple`-según el tipo que representa las cargas de los orígenes de entrada.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`type`|Un alias de tipo para `T`.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Elección](#ctor)|Sobrecargado. Construye un bloque de mensajería `choice` .|  
|[~ choice (destructor)](#dtor)|Destruye el `choice` bloque de mensajería.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Aceptar](#accept)|Acepta un mensaje que fue proporcionado por este `choice` bloque, transferir la propiedad al llamador.|  
|[acquire_ref](#acquire_ref)|Adquiere un recuento de referencias en el objeto `choice` bloque de mensajería, para evitar la eliminación.|  
|[Consumir](#consume)|Consume un mensaje ofrecido previamente por este `choice` bloque de mensajería y correctamente reservado por el destino, transfiriendo la propiedad al llamador.|  
|[has_value](#has_value)|Comprueba si este `choice` bloque de mensajería se ha inicializado con un valor aún.|  
|[index](#index)|Devuelve un índice en la `tuple` que representa el elemento seleccionado por el `choice` bloque de mensajería.|  
|[link_target](#link_target)|Vincula un bloque de destino a esta `choice` bloque de mensajería.|  
|[release](#release)|Libera una reserva de mensaje correcto anterior.|  
|[release_ref](#release_ref)|Libera un recuento de referencias en el objeto `choice` bloque de mensajería.|  
|[reserve](#reserve)|Reserva un mensaje ofrecido previamente por este `choice` bloque de mensajería.|  
|[unlink_target](#unlink_target)|Desvincula un bloque de destino de este `choice` bloque de mensajería.|  
|[unlink_targets](#unlink_targets)|Desvincula todos los destinos de este `choice` bloque de mensajería. (Invalida [ISource:: Unlink_targets](isource-class.md#unlink_targets).)|  
|[value](#value)|Obtiene el mensaje cuyo índice seleccionado por el `choice` bloque de mensajería.|  
  
## <a name="remarks"></a>Comentarios  
 El bloque de elección se asegura de que se utilicen solo uno de los mensajes entrantes.  
  
 Para obtener más información, consulte [los bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [ISource](isource-class.md)  
  
 `choice`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="accept"></a> Aceptar 

 Acepta un mensaje que fue proporcionado por este `choice` bloque, transferir la propiedad al llamador.  
  
```  
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la que se ofrecen `message` objeto.  
  
 `_PTarget`  
 Un puntero al bloque de destino que llama a la `accept` método.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al mensaje que el llamador tiene ahora la propiedad.  
  
##  <a name="acquire_ref"></a> acquire_ref 

 Adquiere un recuento de referencias en el objeto `choice` bloque de mensajería, para evitar la eliminación.  
  
```  
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero al bloque de destino que llama a este método.  
  
### <a name="remarks"></a>Comentarios  
 Este método es invocado por un `ITarget` objeto que se está vinculando a este origen durante el `link_target` método.  
  
##  <a name="ctor"></a> Elección 

 Construye un bloque de mensajería `choice` .  
  
```  
explicit choice(
    T _Tuple);

 
choice(
    Scheduler& _PScheduler,  
    T _Tuple);

 
choice(
    ScheduleGroup& _PScheduleGroup,  
    T _Tuple);

 
choice(
    choice&& _Choice);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Tuple`  
 `tuple` de orígenes para choice.  
  
 `_PScheduler`  
 El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `choice` .  
  
 `_PScheduleGroup`  
 El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `choice` . El objeto `Scheduler` utilizado está implícito en el grupo de programación.  
  
 `_Choice`  
 Bloque de mensajería `choice` desde el que se realizará la copia. Tenga en cuenta que el objeto original es huérfano, por lo que este constructor pasa a ser de movimiento.  
  
### <a name="remarks"></a>Comentarios  
 El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PScheduleGroup` .  
  
 La construcción de movimiento no se lleva acabo con un bloqueo, lo que significa que el usuario debe asegurarse de que no hay ninguna tarea ligera en marcha en el momento del movimiento. De lo contrario, se pueden producir numerosas carreras, que darán lugar a excepciones o a un estado incoherente.  
  
##  <a name="dtor"></a> ~ choice 

 Destruye el `choice` bloque de mensajería.  
  
```  
~choice();
```  
  
##  <a name="consume"></a> Consumir 

 Consume un mensaje ofrecido previamente por este `choice` bloque de mensajería y correctamente reservado por el destino, transfiriendo la propiedad al llamador.  
  
```  
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
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
  
##  <a name="has_value"></a> has_value 

 Comprueba si este `choice` bloque de mensajería se ha inicializado con un valor aún.  
  
```  
bool has_value() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el bloque ha recibido un valor `false` en caso contrario.  
  
##  <a name="index"></a> Índice 

 Devuelve un índice en la `tuple` que representa el elemento seleccionado por el `choice` bloque de mensajería.  
  
```  
size_t index();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del mensaje.  
  
### <a name="remarks"></a>Comentarios  
 Se puede extraer la carga del mensaje utilizando el `get` método.  
  
##  <a name="link_target"></a> link_target 

 Vincula un bloque de destino a esta `choice` bloque de mensajería.  
  
```  
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero a un `ITarget` bloque para vincularlo a este `choice` bloque de mensajería.  
  
##  <a name="release"></a> la versión 

 Libera una reserva de mensaje correcto anterior.  
  
```  
virtual void release(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la `message` del objeto que se libera.  
  
 `_PTarget`  
 Un puntero al bloque de destino que llama a la `release` método.  
  
##  <a name="release_ref"></a> release_ref 

 Libera un recuento de referencias en el objeto `choice` bloque de mensajería.  
  
```  
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero al bloque de destino que llama a este método.  
  
### <a name="remarks"></a>Comentarios  
 Este método es invocado por un `ITarget` objeto que se desvincula de este origen. El bloque de origen puede liberar cualquier recurso reservado para el bloque de destino.  
  
##  <a name="reserve"></a> reservar 

 Reserva un mensaje ofrecido previamente por este `choice` bloque de mensajería.  
  
```  
virtual bool reserve(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
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

 Desvincula un bloque de destino de este `choice` bloque de mensajería.  
  
```  
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero a un `ITarget` bloque desvinculación de esto `choice` bloque de mensajería.  
  
##  <a name="unlink_targets"></a> unlink_targets 

 Desvincula todos los destinos de este `choice` bloque de mensajería.  
  
```  
virtual void unlink_targets();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método no es necesario que se llame desde el destructor porque el destructor para la propia `single_assignment` bloque éste desvinculará correctamente.  
  
##  <a name="value"></a> Valor 

 Obtiene el mensaje cuyo índice seleccionado por el `choice` bloque de mensajería.  
  
```  
template <
    typename _Payload_type  
>  
_Payload_type const& value();
```  
  
### <a name="parameters"></a>Parámetros  
 `_Payload_type`  
 El tipo de la carga del mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 La carga del mensaje.  
  
### <a name="remarks"></a>Comentarios  
 Dado que un `choice` bloque de mensajería puede tomar entradas con tipos de carga diferentes, debe especificar el tipo de la carga en el punto de recuperación. Puede determinar el tipo según el resultado de la `index` método.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [Join (clase)](join-class.md)   
 [single_assignment (clase)](single-assignment-class.md)
