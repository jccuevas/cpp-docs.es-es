---
title: unbounded_buffer (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- unbounded_buffer
- AGENTS/concurrency::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::dequeue
- AGENTS/concurrency::unbounded_buffer::enqueue
- AGENTS/concurrency::unbounded_buffer::accept_message
- AGENTS/concurrency::unbounded_buffer::consume_message
- AGENTS/concurrency::unbounded_buffer::link_target_notification
- AGENTS/concurrency::unbounded_buffer::process_input_messages
- AGENTS/concurrency::unbounded_buffer::propagate_message
- AGENTS/concurrency::unbounded_buffer::propagate_output_messages
- AGENTS/concurrency::unbounded_buffer::release_message
- AGENTS/concurrency::unbounded_buffer::reserve_message
- AGENTS/concurrency::unbounded_buffer::resume_propagation
- AGENTS/concurrency::unbounded_buffer::send_message
- AGENTS/concurrency::unbounded_buffer::supports_anonymous_source
dev_langs:
- C++
ms.assetid: 6b1a939a-1819-4385-b1d8-708f83d4ec47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ffc1ea1f512e049f3a6af15170429a3618323dc5
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163002"
---
Un bloque de mensajería `unbounded_buffer` es un bloque `propagator_block` de destino único, de varios orígenes y ordenado capaz de almacenar un número ilimitado de mensajes.

## <a name="syntax"></a>Sintaxis

```
template<
   class             _Type
>
class unbounded_buffer : public propagator_block<multi_link_registry<ITarget<            _Type>>, multi_link_registry<ISource<            _Type>>>;
```

#### <a name="parameters"></a>Parámetros

*_Tipo*<br/>
El tipo de carga de los mensajes se almacena y se propaga por el búfer.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[unbounded_buffer](#ctor)|Sobrecargado. Construye un `unbounded_buffer` bloque de mensajería.|
|[~ unbounded_buffer (destructor)](#dtor)|Destruye el `unbounded_buffer` bloque de mensajería.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[eliminación de cola](#dequeue)|Quita un elemento de la `unbounded_buffer` bloque de mensajería.|
|[poner en cola](#enqueue)|Agrega un elemento a la `unbounded_buffer` bloque de mensajería.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[accept_message](#accept_message)|Acepta un mensaje que se ha proporcionado por este `unbounded_buffer` bloque de mensajería, transferencia de la propiedad al llamador.|
|[consume_message](#consume_message)|Consume un mensaje ofrecido previamente por el `unbounded_buffer` bloque de mensajería y reservado por el destino, transfiriendo la propiedad al llamador.|
|[link_target_notification](#link_target_notification)|Una devolución de llamada que notifica que se ha vinculado un nuevo destino para esta `unbounded_buffer` bloque de mensajería.|
|[process_input_messages](#process_input_messages)|Coloca el `message` `_PMessage` en este `unbounded_buffer` bloque de mensajería e intenta ofrecer a todos los destinos vinculados.|
|[propagate_message](#propagate_message)|Pasa de forma asincrónica un mensaje desde un `ISource` bloque a este `unbounded_buffer` bloque de mensajería. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.|
|[propagate_output_messages](#propagate_output_messages)|Coloca el `message` `_PMessage` en este `unbounded_buffer` bloque de mensajería e intenta ofrecer a todos los destinos vinculados. (Invalida [source_block::propagate_output_messages](source-block-class.md#propagate_output_messages).)|
|[release_message](#release_message)|Libera una reserva de mensaje anterior. (Invalida [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Reserva un mensaje ofrecido previamente por este `unbounded_buffer` bloque de mensajería. (Invalida [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Reanuda la propagación después de que se ha liberado una reserva. (Invalida [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Un mensaje de forma sincrónica, pasa un `ISource` bloque a este `unbounded_buffer` bloque de mensajería. Se invoca con el `send` método, cuando se llama a un bloque de origen.|
|[supports_anonymous_source](#supports_anonymous_source)|Invalida el `supports_anonymous_source` método para indicar que este bloque puede aceptar mensajes ofrecidos por un origen que no está vinculado. (Invalida [ITarget](itarget-class.md#supports_anonymous_source).)|

Para obtener más información, consulte [bloques de mensajes asincrónicos](../asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block)](source-block-class.md)

[propagator_block](propagator-block-class.md)

`unbounded_buffer`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

##  <a name="accept_message"></a> accept_message

Acepta un mensaje que se ha proporcionado por este `unbounded_buffer` bloque de mensajería, transferencia de la propiedad al llamador.

```
virtual message<_Type> * accept_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
El `runtime_object_identity` de la ofrecida `message` objeto.

### <a name="return-value"></a>Valor devuelto

Un puntero a la `message` que el llamador tiene ahora la propiedad de objeto.

##  <a name="consume_message"></a> consume_message

Consume un mensaje ofrecido previamente por el `unbounded_buffer` bloque de mensajería y reservado por el destino, transfiriendo la propiedad al llamador.

```
virtual message<_Type> * consume_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
El `runtime_object_identity` de la `message` objeto consumido.

### <a name="return-value"></a>Valor devuelto

Un puntero a la `message` que el llamador tiene ahora la propiedad de objeto.

### <a name="remarks"></a>Comentarios

Similar a `accept`, pero siempre está precedido por una llamada a `reserve`.

##  <a name="dequeue"></a> eliminación de cola

Quita un elemento de la `unbounded_buffer` bloque de mensajería.

```
_Type dequeue();
```

### <a name="return-value"></a>Valor devuelto

La carga del mensaje que se quitó el `unbounded_buffer`.

##  <a name="enqueue"></a> poner en cola

Agrega un elemento a la `unbounded_buffer` bloque de mensajería.

```
bool enqueue(
   _Type const&                 _Item
);
```

### <a name="parameters"></a>Parámetros

*_Elemento*<br/>
Elemento que se va a agregar.

### <a name="return-value"></a>Valor devuelto

**True** si se aceptó el elemento, **false** en caso contrario.

##  <a name="link_target_notification"></a> link_target_notification

Una devolución de llamada que notifica que se ha vinculado un nuevo destino para esta `unbounded_buffer` bloque de mensajería.

```
virtual void link_target_notification(
   _Inout_ ITarget<_Type> *                 _PTarget
);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Un puntero al destino recién vinculado.

##  <a name="propagate_message"></a> propagate_message

Pasa de forma asincrónica un mensaje desde un `ISource` bloque a este `unbounded_buffer` bloque de mensajería. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.

```
virtual message_status propagate_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>Parámetros

*Parámetro _PMessage*<br/>
Un puntero al objeto `message`.

*_PSource*<br/>
Un puntero al bloque de origen que proporciona el mensaje.

### <a name="return-value"></a>Valor devuelto

Un [message_status](concurrency-namespace-enums.md#message_status) indicación de lo que el destino decidió hacer con el mensaje.

##  <a name="propagate_output_messages"></a> propagate_output_messages

Coloca el `message` `_PMessage` en este `unbounded_buffer` bloque de mensajería e intenta ofrecer a todos los destinos vinculados.

```
virtual void propagate_output_messages();
```

### <a name="remarks"></a>Comentarios

Si otro mensaje ya está delante de este en el `unbounded_buffer`, propagación a los destinos vinculados no se producirá hasta que se han aceptado o consumir los mensajes anteriores. El primer vinculado destino correctamente `accept` o `consume` el mensaje toma posesión y ningún otro destino, a continuación, puede obtener el mensaje.

##  <a name="process_input_messages"></a> process_input_messages

Coloca el `message` `_PMessage` en este `unbounded_buffer` bloque de mensajería e intenta ofrecer a todos los destinos vinculados.

```
virtual void process_input_messages(
   _Inout_ message<_Type> *                 _PMessage
);
```

### <a name="parameters"></a>Parámetros

*Parámetro _PMessage*<br/>
Un puntero al mensaje que debe procesarse.

##  <a name="release_message"></a> release_message

Libera una reserva de mensaje anterior.

```
virtual void release_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
El `runtime_object_identity` de la `message` objeto liberarse.

##  <a name="reserve_message"></a> reserve_message

Reserva un mensaje ofrecido previamente por este `unbounded_buffer` bloque de mensajería.

```
virtual bool reserve_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
El `runtime_object_identity` de la `message` objeto va a reservar.

### <a name="return-value"></a>Valor devuelto

**True** si el mensaje se ha reservado correctamente, **false** en caso contrario.

### <a name="remarks"></a>Comentarios

Después de `reserve` se llama, si devuelve **true**, ya sea `consume` o `release` debe llamarse para aceptar o liberar la propiedad del mensaje.

##  <a name="resume_propagation"></a> resume_propagation

Reanuda la propagación después de que se ha liberado una reserva.

```
virtual void resume_propagation();
```

##  <a name="send_message"></a> send_message

Un mensaje de forma sincrónica, pasa un `ISource` bloque a este `unbounded_buffer` bloque de mensajería. Se invoca con el `send` método, cuando se llama a un bloque de origen.

```
virtual message_status send_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>Parámetros

*Parámetro _PMessage*<br/>
Un puntero al objeto `message`.

*_PSource*<br/>
Un puntero al bloque de origen que proporciona el mensaje.

### <a name="return-value"></a>Valor devuelto

Un [message_status](concurrency-namespace-enums.md#message_status) indicación de lo que el destino decidió hacer con el mensaje.

##  <a name="supports_anonymous_source"></a> supports_anonymous_source

Invalida el `supports_anonymous_source` método para indicar que este bloque puede aceptar mensajes ofrecidos por un origen que no está vinculado.

```
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Valor devuelto

**True** porque no posponer el bloque de mensajes ofrecidos.

##  <a name="ctor"></a> unbounded_buffer

Construye un `unbounded_buffer` bloque de mensajería.

```
unbounded_buffer();

unbounded_buffer(
   filter_method const&                 _Filter
);

unbounded_buffer(
   Scheduler&                 _PScheduler
);

unbounded_buffer(
   Scheduler&                 _PScheduler,
   filter_method const&                 _Filter
);

unbounded_buffer(
   ScheduleGroup&                 _PScheduleGroup
);

unbounded_buffer(
   ScheduleGroup&                 _PScheduleGroup,
   filter_method const&                 _Filter
);
```

### <a name="parameters"></a>Parámetros

*_Filtrar*<br/>
Una función de filtro que determina si se deben aceptar mensajes ofrecidos.

*_PScheduler*<br/>
El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `unbounded_buffer` .

*_PScheduleGroup*<br/>
El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `unbounded_buffer` . El objeto `Scheduler` utilizado está implícito en el grupo de programación.

### <a name="remarks"></a>Comentarios

El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PScheduleGroup` .

El tipo `filter_method` es un functor con firma `bool (_Type const &)` que es invocado por este `unbounded_buffer` bloque de mensajería para determinar si debe aceptar un mensaje proporcionado.

##  <a name="dtor"></a> ~ unbounded_buffer

Destruye el `unbounded_buffer` bloque de mensajería.

```
~unbounded_buffer();
```

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[overwrite_buffer (clase)](overwrite-buffer-class.md)<br/>
[single_assignment (clase)](single-assignment-class.md)

