---
title: Timer (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- timer
- AGENTS/concurrency::timer
- AGENTS/concurrency::timer::timer
- AGENTS/concurrency::timer::pause
- AGENTS/concurrency::timer::start
- AGENTS/concurrency::timer::stop
- AGENTS/concurrency::timer::accept_message
- AGENTS/concurrency::timer::consume_message
- AGENTS/concurrency::timer::link_target_notification
- AGENTS/concurrency::timer::propagate_to_any_targets
- AGENTS/concurrency::timer::release_message
- AGENTS/concurrency::timer::reserve_message
- AGENTS/concurrency::timer::resume_propagation
dev_langs:
- C++
helpviewer_keywords:
- timer class
ms.assetid: 4f4dea51-de9f-40f9-93f5-dd724c567b49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42d77386350dab3e8714b00f8e55143b2a486e79
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091665"
---
# <a name="timer-class"></a>Clase timer
Un bloque de mensajería `timer` es un bloque `source_block` con destino único, capaz de enviar un mensaje a su destino cuando un período de tiempo especificado ha transcurrido o en intervalos concretos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class T>
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<T>>>;
```  
  
#### <a name="parameters"></a>Parámetros  
*T*<br/>
El tipo de carga de los mensajes de salida de este bloque.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Temporizador](#ctor)|Sobrecargado. Construye un `timer` bloque de mensajería que desencadenará un mensaje determinado después de un intervalo especificado.|  
|[~ timer (destructor)](#dtor)|Destruye un `timer` bloque de mensajería.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[pausar](#pause)|Se detiene el `timer` bloque de mensajería. Si es una repetición `timer` bloque de mensajería, se puede reiniciar con una posterior `start()` llamar. Para no repetitivo temporizadores, esto tiene el mismo efecto que un `stop` llamar.|  
|[start](#start)|Se inicia el `timer` bloque de mensajería. Se llama el número especificado de milisegundos después de esto, el valor especificado se propagará descendentes, como un `message`.|  
|[Detener](#stop)|Se detiene el `timer` bloque de mensajería.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[accept_message](#accept_message)|Acepta un mensaje que se ha proporcionado por este `timer` bloque de mensajería, transferencia de la propiedad al llamador.|  
|[consume_message](#consume_message)|Consume un mensaje ofrecido previamente por el `timer` y reservado por el destino, transfiriendo la propiedad al llamador.|  
|[link_target_notification](#link_target_notification)|Una devolución de llamada que notifica que se ha vinculado un nuevo destino para esta `timer` bloque de mensajería.|  
|[propagate_to_any_targets](#propagate_to_any_targets)|Intenta ofrecer el mensaje generado por el `timer` bloque a todos los destinos vinculados.|  
|[release_message](#release_message)|Libera una reserva de mensaje anterior. (Invalida [source_block:: release_message](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Reserva un mensaje ofrecido previamente por este `timer` bloque de mensajería. (Invalida [source_block:: reserve_message](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Reanuda la propagación después de que se ha liberado una reserva. (Invalida [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [ISource](isource-class.md)  
  
 [source_block)](source-block-class.md)  
  
 `timer`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="accept_message"></a> accept_message 

 Acepta un mensaje que se ha proporcionado por este `timer` bloque de mensajería, transferencia de la propiedad al llamador.  
  
```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parámetros  
*_MsgId*<br/>
El `runtime_object_identity` de la ofrecida `message` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `message` que el llamador tiene ahora la propiedad de objeto.  
  
##  <a name="consume_message"></a> consume_message 

 Consume un mensaje ofrecido previamente por el `timer` y reservado por el destino, transfiriendo la propiedad al llamador.  
  
```
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parámetros  
*_MsgId*<br/>
El `runtime_object_identity` de la `message` objeto consumido.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `message` que el llamador tiene ahora la propiedad de objeto.  
  
### <a name="remarks"></a>Comentarios  
 Similar a `accept`, pero siempre está precedido por una llamada a `reserve`.  
  
##  <a name="link_target_notification"></a> link_target_notification 

 Una devolución de llamada que notifica que se ha vinculado un nuevo destino para esta `timer` bloque de mensajería.  
  
```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
*_PTarget*<br/>
Un puntero al destino recién vinculado.  
  
##  <a name="pause"></a> pausar 

 Se detiene el `timer` bloque de mensajería. Si es una repetición `timer` bloque de mensajería, se puede reiniciar con una posterior `start()` llamar. Para no repetitivo temporizadores, esto tiene el mismo efecto que un `stop` llamar.  
  
```
void pause();
```  
  
##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets 

 Intenta ofrecer el mensaje generado por el `timer` bloque a todos los destinos vinculados.  
  
```
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
```  
  
##  <a name="release_message"></a> release_message 

 Libera una reserva de mensaje anterior.  
  
```
virtual void release_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parámetros  
*_MsgId*<br/>
El `runtime_object_identity` de la `message` objeto liberarse.  
  
##  <a name="reserve_message"></a> reserve_message 

 Reserva un mensaje ofrecido previamente por este `timer` bloque de mensajería.  
  
```
virtual bool reserve_message(runtime_object_identity _MsgId);
```  
  
### <a name="parameters"></a>Parámetros  
*_MsgId*<br/>
El `runtime_object_identity` de la `message` objeto va a reservar.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el mensaje se ha reservado correctamente, `false` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Después de `reserve` se llama, si devuelve `true`, ya sea `consume` o `release` debe llamarse para aceptar o liberar la propiedad del mensaje.  
  
##  <a name="resume_propagation"></a> resume_propagation 

 Reanuda la propagación después de que se ha liberado una reserva.  
  
```
virtual void resume_propagation();
```  
  
##  <a name="start"></a> Inicio 

 Se inicia el `timer` bloque de mensajería. Se llama el número especificado de milisegundos después de esto, el valor especificado se propagará descendentes, como un `message`.  
  
```
void start();
```  
  
##  <a name="stop"></a> Detener 

 Se detiene el `timer` bloque de mensajería.  
  
```
void stop();
```  
  
##  <a name="ctor"></a> Temporizador 

 Construye un `timer` bloque de mensajería que desencadenará un mensaje determinado después de un intervalo especificado.  
  
```
timer(
    unsigned int _Ms,
    T const& value,
    ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    Scheduler& _Scheduler,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    ScheduleGroup& _ScheduleGroup,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);
```  
  
### <a name="parameters"></a>Parámetros  
*_Ms*<br/>
El número de milisegundos que deben transcurrir después de llamar a iniciar para el mensaje especificado que se propaguen de nivel inferior.  
  
*valor*<br/>
El valor se propagará bajada cuando transcurre el temporizador.  
  
*_PTarget*<br/>
El destino al que el temporizador propagará su mensaje.  
  
*_Repeating*<br/>
Si es true, indica que el temporizador se activará periódicamente cada `_Ms` milisegundos.  
  
*_Scheduler*<br/>
El `Scheduler` objeto dentro del cual la tarea de propagación para el `timer` está programado el bloque de mensajería está programada.  
  
*_ScheduleGroup*<br/>
El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `timer`. El objeto `Scheduler` utilizado está implícito en el grupo de programación.  
  
### <a name="remarks"></a>Comentarios  
 El runtime usa el programador predeterminado si no especifica la `_Scheduler` o `_ScheduleGroup` parámetros.  
  
##  <a name="dtor"></a> ~ timer 

 Destruye un `timer` bloque de mensajería.  
  
```
~timer();
```  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)
