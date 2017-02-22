---
title: "multitype_join (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::multitype_join"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "multitype_join (clase)"
ms.assetid: 236e87a0-4867-49fd-869a-bef4010e49a7
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# multitype_join (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

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
  
|Nombre|Descripción|  
|----------|-----------------|  
|`type`|Un alias de tipo para `T`.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Constructor multitype_join:: multitype_join](#multitype_join__multitype_join_constructor)|Sobrecargado. Construye un bloque de mensajería `multitype_join` .|  
|[multitype_join:: ~ multitype_join (destructor)](#multitype_join___dtormultitype_join_destructor)|Destruye el `multitype_join` bloque de mensajería.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[multitype_join:: Accept (método)](#multitype_join__accept_method)|Acepta un mensaje que fue proporcionado por este `multitype_join` bloque, transfiriendo la propiedad al llamador.|  
|[multitype_join:: acquire_ref (método)](#multitype_join__acquire_ref_method)|Adquiere un recuento de referencias en este `multitype_join` bloque de mensajería, para evitar la eliminación.|  
|[multitype_join:: consume (método)](#multitype_join__consume_method)|Consume un mensaje proporcionado anteriormente por el `multitype_join` bloque de mensajería y correctamente reservado por el destino, transfiriendo la propiedad al llamador.|  
|[multitype_join:: link_target (método)](#multitype_join__link_target_method)|Vincula un bloque de destino a esta `multitype_join` bloque de mensajería.|  
|[multitype_join:: Release (método)](#multitype_join__release_method)|Libera una reserva de mensaje correcto anterior.|  
|[multitype_join:: release_ref (método)](#multitype_join__release_ref_method)|Libera un recuento de referencias en este `multiple_join` bloque de mensajería.|  
|[multitype_join:: reserve (método)](#multitype_join__reserve_method)|Reserva un mensaje ofrecido previamente por este `multitype_join` bloque de mensajería.|  
|[multitype_join:: unlink_target (método)](#multitype_join__unlink_target_method)|Desvincula un bloque de destino de este `multitype_join` bloque de mensajería.|  
|[multitype_join:: unlink_targets (método)](#multitype_join__unlink_targets_method)|Desvincula todos los destinos de este `multitype_join` bloque de mensajería. (Invalida [ISource:: Unlink_targets](../../../parallel/concrt/reference/isource-class.md#isource__unlink_targets_method).)|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 `multitype_join`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-namemultitypejoinacceptmethoda-multitypejoinaccept-method"></a><a name="multitype_join__accept_method"></a>  multitype_join:: Accept (método)  
 Acepta un mensaje que fue proporcionado por este `multitype_join` bloque, transfiriendo la propiedad al llamador.  
  
```  
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,  
    _Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MsgId`  
 El `runtime_object_identity` de la ofrecida `message` objeto.  
  
 `_PTarget`  
 Un puntero al bloque de destino que llama a la `accept` (método).  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al mensaje que el llamador tiene ahora la propiedad.  
  
##  <a name="a-namemultitypejoinacquirerefmethoda-multitypejoinacquireref-method"></a><a name="multitype_join__acquire_ref_method"></a>  multitype_join:: acquire_ref (método)  
 Adquiere un recuento de referencias en este `multitype_join` bloque de mensajería, para evitar la eliminación.  
  
```  
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero al bloque de destino que llama a este método.  
  
### <a name="remarks"></a>Comentarios  
 Este método es invocado por un `ITarget` objeto vinculado a este origen durante el `link_target` método.  
  
##  <a name="a-namemultitypejoinconsumemethoda-multitypejoinconsume-method"></a><a name="multitype_join__consume_method"></a>  multitype_join:: consume (método)  
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
 Un puntero al bloque de destino que llama a la `consume` (método).  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `message` que el llamador tiene ahora la propiedad de objeto.  
  
### <a name="remarks"></a>Comentarios  
 El `consume` es similar al método `accept`, pero siempre debe ir precedido por una llamada a `reserve` que devuelve `true`.  
  
##  <a name="a-namemultitypejoinlinktargetmethoda-multitypejoinlinktarget-method"></a><a name="multitype_join__link_target_method"></a>  multitype_join:: link_target (método)  
 Vincula un bloque de destino a esta `multitype_join` bloque de mensajería.  
  
```  
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero a un `ITarget` bloque para vincular a esta `multitype_join` bloque de mensajería.  
  
##  <a name="a-namemultitypejoinmultitypejoinconstructora-multitypejoinmultitypejoin-constructor"></a><a name="multitype_join__multitype_join_constructor"></a>  Constructor multitype_join:: multitype_join  
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
  
##  <a name="a-namemultitypejoindtormultitypejoindestructora-multitypejoinmultitypejoin-destructor"></a><a name="multitype_join___dtormultitype_join_destructor"></a>  multitype_join:: ~ multitype_join (destructor)  
 Destruye el `multitype_join` bloque de mensajería.  
  
```  
~multitype_join();
```  
  
##  <a name="a-namemultitypejoinreleasemethoda-multitypejoinrelease-method"></a><a name="multitype_join__release_method"></a>  multitype_join:: Release (método)  
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
 Un puntero al bloque de destino que llama a la `release` (método).  
  
##  <a name="a-namemultitypejoinreleaserefmethoda-multitypejoinreleaseref-method"></a><a name="multitype_join__release_ref_method"></a>  multitype_join:: release_ref (método)  
 Libera un recuento de referencias en este `multiple_join` bloque de mensajería.  
  
```  
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero al bloque de destino que llama a este método.  
  
### <a name="remarks"></a>Comentarios  
 Este método es invocado por un `ITarget` objeto que se desvincula de este origen. El bloque de origen puede liberar cualquier recurso reservado para el bloque de destino.  
  
##  <a name="a-namemultitypejoinreservemethoda-multitypejoinreserve-method"></a><a name="multitype_join__reserve_method"></a>  multitype_join:: reserve (método)  
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
 Un puntero al bloque de destino que llama a la `reserve` (método).  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el mensaje se ha reservado correctamente, `false` en caso contrario. Las reservas pueden fallar por diversos motivos, incluidos: el mensaje ya se ha reservado o aceptó por otro destino, el origen podría denegar reservas etc..  
  
### <a name="remarks"></a>Comentarios  
 Después de llamar a `reserve`, si se realiza correctamente, debe llamar `consume` o `release` para aceptar o ceder la posesión del mensaje, respectivamente.  
  
##  <a name="a-namemultitypejoinunlinktargetmethoda-multitypejoinunlinktarget-method"></a><a name="multitype_join__unlink_target_method"></a>  multitype_join:: unlink_target (método)  
 Desvincula un bloque de destino de este `multitype_join` bloque de mensajería.  
  
```  
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero a un `ITarget` bloque desvincular desde este `multitype_join` bloque de mensajería.  
  
##  <a name="a-namemultitypejoinunlinktargetsmethoda-multitypejoinunlinktargets-method"></a><a name="multitype_join__unlink_targets_method"></a>  multitype_join:: unlink_targets (método)  
 Desvincula todos los destinos de este `multitype_join` bloque de mensajería.  
  
```  
virtual void unlink_targets();
```  
  
## <a name="see-also"></a>Vea también  
 [espacio de nombres de simultaneidad](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Clase Choice](../../../parallel/concrt/reference/choice-class.md)   
 [Join (clase)](../../../parallel/concrt/reference/join-class.md)
