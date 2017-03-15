---
title: Clase Choice | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::choice
dev_langs:
- C++
helpviewer_keywords:
- choice class
ms.assetid: 4157a539-d5c2-4161-b1ab-536ce2888397
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
ms.openlocfilehash: 1ee8fe2197a41ad2abc14e24c372f808bdbc16d0
ms.lasthandoff: 02/24/2017

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
  
|Nombre|Descripción|  
|----------|-----------------|  
|`type`|Un alias de tipo para `T`.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[elección del Constructor](#ctor)|Sobrecargado. Construye un bloque de mensajería `choice` .|  
|[~ choice (destructor)](#dtor)|Destruye el `choice` bloque de mensajería.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Accept (método)](#accept)|Acepta un mensaje que fue proporcionado por este `choice` bloque, transfiriendo la propiedad al llamador.|  
|[acquire_ref (método)](#acquire_ref)|Adquiere un recuento de referencias en este `choice` bloque de mensajería, para evitar la eliminación.|  
|[consume (método)](#consume)|Consume un mensaje ofrecido previamente por este `choice` bloque de mensajería y correctamente reservado por el destino, transfiriendo la propiedad al llamador.|  
|[has_value (método)](#has_value)|Comprueba si este `choice` bloque de mensajería se ha inicializado con un valor aún.|  
|[índice (método)](#index)|Devuelve un índice en la `tuple` que representa el elemento seleccionado por el `choice` bloque de mensajería.|  
|[link_target (método)](#link_target)|Vincula un bloque de destino a esta `choice` bloque de mensajería.|  
|[Release (método)](#release)|Libera una reserva de mensaje correcto anterior.|  
|[release_ref (método)](#release_ref)|Libera un recuento de referencias en este `choice` bloque de mensajería.|  
|[Reserve (método)](#reserve)|Reserva un mensaje ofrecido previamente por este `choice` bloque de mensajería.|  
|[unlink_target (método)](#unlink_target)|Desvincula un bloque de destino de este `choice` bloque de mensajería.|  
|[unlink_targets (método)](#unlink_targets)|Desvincula todos los destinos de este `choice` bloque de mensajería. (Invalida [ISource:: Unlink_targets](isource-class.md#unlink_targets).)|  
|[valor (método)](#value)|Obtiene el mensaje cuyo índice seleccionó el `choice` bloque de mensajería.|  
  
## <a name="remarks"></a>Comentarios  
 El bloque de elección asegura que sólo uno de los mensajes entrantes se consume.  
  
 Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [ISource](isource-class.md)  
  
 `choice`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-nameaccepta-accept"></a><a name="accept"></a>Aceptar 

 Acepta un mensaje que fue proporcionado por este `choice` bloque, transfiriendo la propiedad al llamador.  
  
```  
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la ofrecida `message` objeto.  
  
 `_PTarget`  
 Un puntero al bloque de destino que llama a la `accept` (método).  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al mensaje que el llamador tiene ahora la propiedad.  
  
##  <a name="a-nameacquirerefa-acquireref"></a><a name="acquire_ref"></a>acquire_ref 

 Adquiere un recuento de referencias en este `choice` bloque de mensajería, para evitar la eliminación.  
  
```  
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero al bloque de destino que llama a este método.  
  
### <a name="remarks"></a>Comentarios  
 Este método es invocado por un `ITarget` objeto vinculado a este origen durante el `link_target` método.  
  
##  <a name="a-namectora-choice"></a><a name="ctor"></a>opción 

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
  
##  <a name="a-namedtora-choice"></a><a name="dtor"></a>~ choice 

 Destruye el `choice` bloque de mensajería.  
  
```  
~choice();
```  
  
##  <a name="a-nameconsumea-consume"></a><a name="consume"></a>consumir 

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
 Un puntero al bloque de destino que llama a la `consume` (método).  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `message` que el llamador tiene ahora la propiedad de objeto.  
  
### <a name="remarks"></a>Comentarios  
 El `consume` método es similar a `accept`, pero siempre debe ir precedido por una llamada a `reserve` que devuelve `true`.  
  
##  <a name="a-namehasvaluea-hasvalue"></a><a name="has_value"></a>has_value 

 Comprueba si este `choice` bloque de mensajería se ha inicializado con un valor aún.  
  
```  
bool has_value() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el bloque ha recibido un valor `false` en caso contrario.  
  
##  <a name="a-nameindexa-index"></a><a name="index"></a>índice 

 Devuelve un índice en la `tuple` que representa el elemento seleccionado por el `choice` bloque de mensajería.  
  
```  
size_t index();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del mensaje.  
  
### <a name="remarks"></a>Comentarios  
 Se puede extraer la carga del mensaje utilizando el `get` método.  
  
##  <a name="a-namelinktargeta-linktarget"></a><a name="link_target"></a>link_target 

 Vincula un bloque de destino a esta `choice` bloque de mensajería.  
  
```  
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero a un `ITarget` bloque para vincular a esta `choice` bloque de mensajería.  
  
##  <a name="a-namereleasea-release"></a><a name="release"></a>la versión 

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
 Un puntero al bloque de destino que llama a la `release` (método).  
  
##  <a name="a-namereleaserefa-releaseref"></a><a name="release_ref"></a>release_ref 

 Libera un recuento de referencias en este `choice` bloque de mensajería.  
  
```  
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero al bloque de destino que llama a este método.  
  
### <a name="remarks"></a>Comentarios  
 Este método es invocado por un `ITarget` objeto que se desvincula de este origen. El bloque de origen puede liberar cualquier recurso reservado para el bloque de destino.  
  
##  <a name="a-namereservea-reserve"></a><a name="reserve"></a>reservar 

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
 Un puntero al bloque de destino que llama a la `reserve` (método).  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el mensaje se ha reservado correctamente, `false` en caso contrario. Las reservas pueden fallar por diversos motivos, incluidos: el mensaje ya se ha reservado o aceptó por otro destino, el origen podría denegar reservas etc..  
  
### <a name="remarks"></a>Comentarios  
 Después de llamar a `reserve`, si se realiza correctamente, debe llamar `consume` o `release` para aceptar o ceder la posesión del mensaje, respectivamente.  
  
##  <a name="a-nameunlinktargeta-unlinktarget"></a><a name="unlink_target"></a>unlink_target 

 Desvincula un bloque de destino de este `choice` bloque de mensajería.  
  
```  
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero a un `ITarget` bloque desvincular desde este `choice` bloque de mensajería.  
  
##  <a name="a-nameunlinktargetsa-unlinktargets"></a><a name="unlink_targets"></a>unlink_targets 

 Desvincula todos los destinos de este `choice` bloque de mensajería.  
  
```  
virtual void unlink_targets();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método no necesita que se llame desde el destructor porque el destructor para interno `single_assignment` bloque desvinculará correctamente.  
  
##  <a name="a-namevaluea-value"></a><a name="value"></a>valor 

 Obtiene el mensaje cuyo índice seleccionó el `choice` bloque de mensajería.  
  
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
 Dado que un `choice` bloque de mensajería puede tomar entradas con tipos de carga diferentes, debe especificar el tipo de la carga en el punto de recuperación. Puede determinar el tipo basado en el resultado de la `index` (método).  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [Join (clase)](join-class.md)   
 [Clase single_assignment](single-assignment-class.md)

