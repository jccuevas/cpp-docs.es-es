---
title: unbounded_buffer (clase)
ms.date: 11/04/2016
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
ms.assetid: 6b1a939a-1819-4385-b1d8-708f83d4ec47
ms.openlocfilehash: d0f2f81957ee88d4263c6acd879bd286c95631eb
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142335"
---
# <a name="unbounded_buffer-class"></a>unbounded_buffer (clase)

Un bloque de mensajería `unbounded_buffer` es un bloque `propagator_block` de destino único, de varios orígenes y ordenado capaz de almacenar un número ilimitado de mensajes.

## <a name="syntax"></a>Sintaxis

```cpp
template<
   class             _Type
>
class unbounded_buffer : public propagator_block<multi_link_registry<ITarget<            _Type>>, multi_link_registry<ISource<            _Type>>>;
```

### <a name="parameters"></a>Parámetros

*_Type*<br/>
El tipo de carga de los mensajes almacenados y propagados por el búfer.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[unbounded_buffer](#ctor)|Sobrecargado. Construye un bloque de mensajería `unbounded_buffer`.|
|[~ unbounded_buffer destructor](#dtor)|Destruye el bloque de mensajería `unbounded_buffer`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[eliminación](#dequeue)|Quita un elemento del bloque de mensajería `unbounded_buffer`.|
|[poner en cola](#enqueue)|Agrega un elemento al `unbounded_buffer` bloque de mensajería.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[accept_message](#accept_message)|Acepta un mensaje ofrecido por este `unbounded_buffer` bloque de mensajería, transfiriendo la propiedad al autor de la llamada.|
|[consume_message](#consume_message)|Consume un mensaje ofrecido anteriormente por el `unbounded_buffer` bloque de mensajería y reservado por el destino, transfiriendo la propiedad al autor de la llamada.|
|[link_target_notification](#link_target_notification)|Una devolución de llamada que notifica que un nuevo destino se ha vinculado a este `unbounded_buffer` bloque de mensajería.|
|[process_input_messages](#process_input_messages)|Coloca el `_PMessage` de `message` en este `unbounded_buffer` bloque de mensajería e intenta ofrecerlo a todos los destinos vinculados.|
|[propagate_message](#propagate_message)|Pasa asincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `unbounded_buffer`. Lo invoca el método `propagate`, cuando lo llama un bloque de origen.|
|[propagate_output_messages](#propagate_output_messages)|Coloca el `_PMessage` de `message` en este `unbounded_buffer` bloque de mensajería e intenta ofrecerlo a todos los destinos vinculados. (Invalida [source_block: ropagate_output_messages:p](source-block-class.md#propagate_output_messages)).|
|[release_message](#release_message)|Libera una reserva de mensaje anterior. (Invalida [source_block:: release_message](source-block-class.md#release_message)).|
|[reserve_message](#reserve_message)|Reserva un mensaje ofrecido anteriormente por este `unbounded_buffer` bloque de mensajería. (Invalida [source_block:: reserve_message](source-block-class.md#reserve_message)).|
|[resume_propagation](#resume_propagation)|Reanuda la propagación una vez que se ha liberado una reserva. (Invalida [source_block:: resume_propagation](source-block-class.md#resume_propagation)).|
|[send_message](#send_message)|Pasa sincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `unbounded_buffer`. Lo invoca el método `send`, cuando lo llama un bloque de origen.|
|[supports_anonymous_source](#supports_anonymous_source)|Invalida el método `supports_anonymous_source` para indicar que este bloque puede aceptar los mensajes que le ofrece un origen que no está vinculado. (Invalida [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source)).|

Para obtener más información, consulte [bloques de mensajes asincrónicos](../asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`unbounded_buffer`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="accept_message"></a>accept_message

Acepta un mensaje ofrecido por este `unbounded_buffer` bloque de mensajería, transfiriendo la propiedad al autor de la llamada.

```cpp
virtual message<_Type> * accept_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto `message` proporcionado.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de `message` al que el llamador tiene ahora propiedad.

## <a name="consume_message"></a>consume_message

Consume un mensaje ofrecido anteriormente por el `unbounded_buffer` bloque de mensajería y reservado por el destino, transfiriendo la propiedad al autor de la llamada.

```cpp
virtual message<_Type> * consume_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` que se va a consumir.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de `message` al que el llamador tiene ahora propiedad.

### <a name="remarks"></a>Observaciones

Similar a `accept`, pero siempre va precedido de una llamada a `reserve`.

## <a name="dequeue"></a>eliminación

Quita un elemento del bloque de mensajería `unbounded_buffer`.

```cpp
_Type dequeue();
```

### <a name="return-value"></a>Valor devuelto

La carga del mensaje que se ha quitado de la `unbounded_buffer`.

## <a name="enqueue"></a>poner en cola

Agrega un elemento al `unbounded_buffer` bloque de mensajería.

```cpp
bool enqueue(
   _Type const&                 _Item
);
```

### <a name="parameters"></a>Parámetros

*_Item*<br/>
Elemento que se va a agregar.

### <a name="return-value"></a>Valor devuelto

**true** si se aceptó el elemento; en caso contrario, **false** .

## <a name="link_target_notification"></a>link_target_notification

Una devolución de llamada que notifica que un nuevo destino se ha vinculado a este `unbounded_buffer` bloque de mensajería.

```cpp
virtual void link_target_notification(
   _Inout_ ITarget<_Type> *                 _PTarget
);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Puntero al destino recién vinculado.

## <a name="propagate_message"></a>propagate_message

Pasa asincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `unbounded_buffer`. Lo invoca el método `propagate`, cuando lo llama un bloque de origen.

```cpp
virtual message_status propagate_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Un puntero al objeto `message`.

*_PSource*<br/>
Puntero al bloque de origen que ofrece el mensaje.

### <a name="return-value"></a>Valor devuelto

[Message_status](concurrency-namespace-enums.md#message_status) indicación de lo que el destino decidió hacer con el mensaje.

## <a name="propagate_output_messages"></a>propagate_output_messages

Coloca el `_PMessage` de `message` en este `unbounded_buffer` bloque de mensajería e intenta ofrecerlo a todos los destinos vinculados.

```cpp
virtual void propagate_output_messages();
```

### <a name="remarks"></a>Observaciones

Si ya hay otro mensaje por encima de este en el `unbounded_buffer`, la propagación a los destinos vinculados no se realizará hasta que se acepten o consuman mensajes anteriores. El primer destino vinculado para `accept` o `consume` correctamente el mensaje toma la propiedad y ningún otro destino puede obtener el mensaje.

## <a name="process_input_messages"></a>process_input_messages

Coloca el `_PMessage` de `message` en este `unbounded_buffer` bloque de mensajería e intenta ofrecerlo a todos los destinos vinculados.

```cpp
virtual void process_input_messages(
   _Inout_ message<_Type> *                 _PMessage
);
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Puntero al mensaje que se va a procesar.

## <a name="release_message"></a>release_message

Libera una reserva de mensaje anterior.

```cpp
virtual void release_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` que se va a liberar.

## <a name="reserve_message"></a>reserve_message

Reserva un mensaje ofrecido anteriormente por este `unbounded_buffer` bloque de mensajería.

```cpp
virtual bool reserve_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` que se va a reservar.

### <a name="return-value"></a>Valor devuelto

**true** si el mensaje se ha reservado correctamente; de lo contrario, **false** .

### <a name="remarks"></a>Observaciones

Una vez que se llama a `reserve`, si devuelve **true**, se debe llamar a `consume` o `release` para tomar o liberar la propiedad del mensaje.

## <a name="resume_propagation"></a>resume_propagation

Reanuda la propagación una vez que se ha liberado una reserva.

```cpp
virtual void resume_propagation();
```

## <a name="send_message"></a>send_message

Pasa sincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `unbounded_buffer`. Lo invoca el método `send`, cuando lo llama un bloque de origen.

```cpp
virtual message_status send_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Un puntero al objeto `message`.

*_PSource*<br/>
Puntero al bloque de origen que ofrece el mensaje.

### <a name="return-value"></a>Valor devuelto

[Message_status](concurrency-namespace-enums.md#message_status) indicación de lo que el destino decidió hacer con el mensaje.

## <a name="supports_anonymous_source"></a>supports_anonymous_source

Invalida el método `supports_anonymous_source` para indicar que este bloque puede aceptar los mensajes que le ofrece un origen que no está vinculado.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Valor devuelto

**true** porque el bloque no pospone los mensajes ofrecidos.

## <a name="ctor"></a>unbounded_buffer

Construye un bloque de mensajería `unbounded_buffer`.

```cpp
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

*_Filter*<br/>
Función de filtro que determina si se deben aceptar los mensajes ofrecidos.

*_PScheduler*<br/>
El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `unbounded_buffer` .

*_PScheduleGroup*<br/>
El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `unbounded_buffer` . El objeto `Scheduler` utilizado está implícito en el grupo de programación.

### <a name="remarks"></a>Observaciones

El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PScheduleGroup` .

El tipo `filter_method` es un functor con `bool (_Type const &)` de firma invocado por este bloque de mensajería de `unbounded_buffer` para determinar si debe aceptar o no un mensaje ofrecido.

## <a name="dtor"></a>~ unbounded_buffer

Destruye el bloque de mensajería `unbounded_buffer`.

```cpp
~unbounded_buffer();
```

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[overwrite_buffer (clase)](overwrite-buffer-class.md)<br/>
[single_assignment (clase)](single-assignment-class.md)
