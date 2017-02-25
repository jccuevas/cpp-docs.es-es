---
title: "Clase choice | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::choice"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "choice (clase)"
ms.assetid: 4157a539-d5c2-4161-b1ab-536ce2888397
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# Clase choice
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

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
|[Constructor choice:: choice](#choice__choice_constructor)|Sobrecargado. Construye un bloque de mensajería `choice` .|  
|[choice:: ~ choice (destructor)](#choice___dtorchoice_destructor)|Destruye el `choice` bloque de mensajería.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[choice:: Accept (método)](#choice__accept_method)|Acepta un mensaje que fue proporcionado por este `choice` bloque, transfiriendo la propiedad al llamador.|  
|[choice:: acquire_ref (método)](#choice__acquire_ref_method)|Adquiere un recuento de referencias en este `choice` bloque de mensajería, para evitar la eliminación.|  
|[choice:: consume (método)](#choice__consume_method)|Consume un mensaje ofrecido previamente por este `choice` bloque de mensajería y correctamente reservado por el destino, transfiriendo la propiedad al llamador.|  
|[choice:: has_value (método)](#choice__has_value_method)|Comprueba si este `choice` bloque de mensajería se ha inicializado con un valor aún.|  
|[choice:: index (método)](#choice__index_method)|Devuelve el índice en el `tuple` que representa el elemento seleccionado por el `choice` bloque de mensajería.|  
|[choice:: link_target (método)](#choice__link_target_method)|Vincula un bloque de destino a esta `choice` bloque de mensajería.|  
|[choice:: Release (método)](#choice__release_method)|Libera una reserva de mensaje correcto anterior.|  
|[choice:: release_ref (método)](#choice__release_ref_method)|Libera un recuento de referencias en este `choice` bloque de mensajería.|  
|[choice:: reserve (método)](#choice__reserve_method)|Reserva un mensaje ofrecido previamente por este `choice` bloque de mensajería.|  
|[choice:: unlink_target (método)](#choice__unlink_target_method)|Desvincula un bloque de destino de este `choice` bloque de mensajería.|  
|[choice:: unlink_targets (método)](#choice__unlink_targets_method)|Desvincula todos los destinos de este `choice` bloque de mensajería. (Invalida [ISource:: Unlink_targets](../../../parallel/concrt/reference/isource-class.md#isource__unlink_targets_method).)|  
|[choice:: value (método)](#choice__value_method)|Obtiene el mensaje cuyo índice seleccionó el `choice` bloque de mensajería.|  
  
## <a name="remarks"></a>Comentarios  
 El bloque de elección asegura que sólo uno de los mensajes entrantes se consume.  
  
 Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [ISource](../../../parallel/concrt/reference/isource-class.md)  
  
 `choice`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-namechoiceacceptmethoda-choiceaccept-method"></a><a name="choice__accept_method"></a>  choice:: Accept (método)  
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
  
##  <a name="a-namechoiceacquirerefmethoda-choiceacquireref-method"></a><a name="choice__acquire_ref_method"></a>  choice:: acquire_ref (método)  
 Adquiere un recuento de referencias en este `choice` bloque de mensajería, para evitar la eliminación.  
  
```  
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero al bloque de destino que llama a este método.  
  
### <a name="remarks"></a>Comentarios  
 Este método es invocado por un `ITarget` objeto vinculado a este origen durante el `link_target` método.  
  
##  <a name="a-namechoicechoiceconstructora-choicechoice-constructor"></a><a name="choice__choice_constructor"></a>  Constructor choice:: choice  
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
  
##  <a name="a-namechoicedtorchoicedestructora-choicechoice-destructor"></a><a name="choice___dtorchoice_destructor"></a>  choice:: ~ choice (destructor)  
 Destruye el `choice` bloque de mensajería.  
  
```  
~choice();
```  
  
##  <a name="a-namechoiceconsumemethoda-choiceconsume-method"></a><a name="choice__consume_method"></a>  choice:: consume (método)  
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
 El `consume` es similar al método `accept`, pero siempre debe ir precedido por una llamada a `reserve` que devuelve `true`.  
  
##  <a name="a-namechoicehasvaluemethoda-choicehasvalue-method"></a><a name="choice__has_value_method"></a>  choice:: has_value (método)  
 Comprueba si este `choice` bloque de mensajería se ha inicializado con un valor aún.  
  
```  
bool has_value() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el bloque ha recibido un valor `false` en caso contrario.  
  
##  <a name="a-namechoiceindexmethoda-choiceindex-method"></a><a name="choice__index_method"></a>  choice:: index (método)  
 Devuelve el índice en el `tuple` que representa el elemento seleccionado por el `choice` bloque de mensajería.  
  
```  
size_t index();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del mensaje.  
  
### <a name="remarks"></a>Comentarios  
 Se puede extraer la carga del mensaje utilizando el `get` método.  
  
##  <a name="a-namechoicelinktargetmethoda-choicelinktarget-method"></a><a name="choice__link_target_method"></a>  choice:: link_target (método)  
 Vincula un bloque de destino a esta `choice` bloque de mensajería.  
  
```  
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero a un `ITarget` bloque para vincular a esta `choice` bloque de mensajería.  
  
##  <a name="a-namechoicereleasemethoda-choicerelease-method"></a><a name="choice__release_method"></a>  choice:: Release (método)  
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
  
##  <a name="a-namechoicereleaserefmethoda-choicereleaseref-method"></a><a name="choice__release_ref_method"></a>  choice:: release_ref (método)  
 Libera un recuento de referencias en este `choice` bloque de mensajería.  
  
```  
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero al bloque de destino que llama a este método.  
  
### <a name="remarks"></a>Comentarios  
 Este método es invocado por un `ITarget` objeto que se desvincula de este origen. El bloque de origen puede liberar cualquier recurso reservado para el bloque de destino.  
  
##  <a name="a-namechoicereservemethoda-choicereserve-method"></a><a name="choice__reserve_method"></a>  choice:: reserve (método)  
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
 `true` Si el mensaje se ha reservado correctamente, `false` en caso contrario. Las reservas pueden fallar por diversos motivos, incluidos: el mensaje ya se ha reservado o aceptó por otro destino, el origen podría denegar reservas etc..  
  
### <a name="remarks"></a>Comentarios  
 Después de llamar a `reserve`, si se realiza correctamente, debe llamar `consume` o `release` para aceptar o ceder la posesión del mensaje, respectivamente.  
  
##  <a name="a-namechoiceunlinktargetmethoda-choiceunlinktarget-method"></a><a name="choice__unlink_target_method"></a>  choice:: unlink_target (método)  
 Desvincula un bloque de destino de este `choice` bloque de mensajería.  
  
```  
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 Un puntero a un `ITarget` bloque desvincular desde este `choice` bloque de mensajería.  
  
##  <a name="a-namechoiceunlinktargetsmethoda-choiceunlinktargets-method"></a><a name="choice__unlink_targets_method"></a>  choice:: unlink_targets (método)  
 Desvincula todos los destinos de este `choice` bloque de mensajería.  
  
```  
virtual void unlink_targets();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método no necesita que se llame desde el destructor porque el destructor para interno `single_assignment` bloque desvinculará correctamente.  
  
##  <a name="a-namechoicevaluemethoda-choicevalue-method"></a><a name="choice__value_method"></a>  choice:: value (método)  
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
 [espacio de nombres de simultaneidad](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Join (clase)](../../../parallel/concrt/reference/join-class.md)   
 [Clase single_assignment](../../../parallel/concrt/reference/single-assignment-class.md)
