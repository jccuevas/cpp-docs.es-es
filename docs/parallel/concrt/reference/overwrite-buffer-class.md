---
title: overwrite_buffer (clase)
ms.date: 11/04/2016
f1_keywords:
- overwrite_buffer
- AGENTS/concurrency::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::has_value
- AGENTS/concurrency::overwrite_buffer::value
- AGENTS/concurrency::overwrite_buffer::accept_message
- AGENTS/concurrency::overwrite_buffer::consume_message
- AGENTS/concurrency::overwrite_buffer::link_target_notification
- AGENTS/concurrency::overwrite_buffer::propagate_message
- AGENTS/concurrency::overwrite_buffer::propagate_to_any_targets
- AGENTS/concurrency::overwrite_buffer::release_message
- AGENTS/concurrency::overwrite_buffer::reserve_message
- AGENTS/concurrency::overwrite_buffer::resume_propagation
- AGENTS/concurrency::overwrite_buffer::send_message
- AGENTS/concurrency::overwrite_buffer::supports_anonymous_source
helpviewer_keywords:
- overwrite_buffer class
ms.assetid: 5cc428fe-3697-419c-9fb2-78f6181c9293
ms.openlocfilehash: 5b222170112f43ae9700054f42e1368545612d00
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138801"
---
# <a name="overwrite_buffer-class"></a>overwrite_buffer (clase)

Un bloque de mensajería `overwrite_buffer` es un bloque `propagator_block` de destino único, de varios orígenes y ordenado que es capaz de almacenar un único mensaje cada vez. Los nuevos mensajes sobrescriben a los retenidos previamente.

## <a name="syntax"></a>Sintaxis

```cpp
template<class T>
class overwrite_buffer : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de carga de los mensajes almacenados y propagados por el búfer.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[overwrite_buffer](#ctor)|Sobrecargado. Construye un bloque de mensajería `overwrite_buffer`.|
|[~ overwrite_buffer destructor](#dtor)|Destruye el bloque de mensajería `overwrite_buffer`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[has_value](#has_value)|Comprueba si esta `overwrite_buffer` bloque de mensajería tiene un valor todavía.|
|[value](#value)|Obtiene una referencia a la carga actual del mensaje que se almacena en el `overwrite_buffer` bloque de mensajería.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[accept_message](#accept_message)|Acepta un mensaje ofrecido por este `overwrite_buffer` bloque de mensajería y devuelve una copia del mensaje al autor de la llamada.|
|[consume_message](#consume_message)|Consume un mensaje ofrecido anteriormente por el `overwrite_buffer` bloque de mensajería y reservado por el destino, y devuelve una copia del mensaje al autor de la llamada.|
|[link_target_notification](#link_target_notification)|Una devolución de llamada que notifica que un nuevo destino se ha vinculado a este `overwrite_buffer` bloque de mensajería.|
|[propagate_message](#propagate_message)|Pasa asincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `overwrite_buffer`. Lo invoca el método `propagate`, cuando lo llama un bloque de origen.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Coloca el `message _PMessage` en este `overwrite_buffer` bloque de mensajería y lo ofrece a todos los destinos vinculados.|
|[release_message](#release_message)|Libera una reserva de mensaje anterior. (Invalida [source_block:: release_message](source-block-class.md#release_message)).|
|[reserve_message](#reserve_message)|Reserva un mensaje ofrecido anteriormente por este `overwrite_buffer` bloque de mensajería. (Invalida [source_block:: reserve_message](source-block-class.md#reserve_message)).|
|[resume_propagation](#resume_propagation)|Reanuda la propagación una vez que se ha liberado una reserva. (Invalida [source_block:: resume_propagation](source-block-class.md#resume_propagation)).|
|[send_message](#send_message)|Pasa sincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `overwrite_buffer`. Lo invoca el método `send`, cuando lo llama un bloque de origen.|
|[supports_anonymous_source](#supports_anonymous_source)|Invalida el método `supports_anonymous_source` para indicar que este bloque puede aceptar los mensajes que le ofrece un origen que no está vinculado. (Invalida [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source)).|

## <a name="remarks"></a>Observaciones

Un bloque de mensajería de `overwrite_buffer` propaga las copias de su mensaje almacenado a cada uno de sus destinos.

Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`overwrite_buffer`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="accept_message"></a>accept_message

Acepta un mensaje ofrecido por este `overwrite_buffer` bloque de mensajería y devuelve una copia del mensaje al autor de la llamada.

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto `message` proporcionado.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de `message` al que el llamador tiene ahora propiedad.

### <a name="remarks"></a>Observaciones

El bloque de mensajería de `overwrite_buffer` devuelve copias del mensaje a sus destinos, en lugar de transferir la propiedad del mensaje que se encuentra actualmente.

## <a name="consume_message"></a>consume_message

Consume un mensaje ofrecido anteriormente por el `overwrite_buffer` bloque de mensajería y reservado por el destino, y devuelve una copia del mensaje al autor de la llamada.

```cpp
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` que se va a consumir.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de `message` al que el llamador tiene ahora propiedad.

### <a name="remarks"></a>Observaciones

Similar a `accept`, pero siempre va precedido de una llamada a `reserve`.

## <a name="has_value"></a>has_value

Comprueba si esta `overwrite_buffer` bloque de mensajería tiene un valor todavía.

```cpp
bool has_value() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si el bloque ha recibido un valor; de lo contrario, **false** .

## <a name="link_target_notification"></a>link_target_notification

Una devolución de llamada que notifica que un nuevo destino se ha vinculado a este `overwrite_buffer` bloque de mensajería.

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Puntero al destino recién vinculado.

## <a name="dtor"></a>~ overwrite_buffer

Destruye el bloque de mensajería `overwrite_buffer`.

```cpp
~overwrite_buffer();
```

## <a name="ctor"></a>overwrite_buffer

Construye un bloque de mensajería `overwrite_buffer`.

```cpp
overwrite_buffer();

overwrite_buffer(
    filter_method const& _Filter);

overwrite_buffer(
    Scheduler& _PScheduler);

overwrite_buffer(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Parámetros

*_Filter*<br/>
Función de filtro que determina si se deben aceptar los mensajes ofrecidos.

*_PScheduler*<br/>
El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `overwrite_buffer` .

*_PScheduleGroup*<br/>
El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `overwrite_buffer` . El objeto `Scheduler` utilizado está implícito en el grupo de programación.

### <a name="remarks"></a>Observaciones

El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PScheduleGroup` .

El tipo `filter_method` es un functor con `bool (T const &)` de firma invocado por este bloque de mensajería de `overwrite_buffer` para determinar si debe aceptar o no un mensaje ofrecido.

## <a name="propagate_message"></a>propagate_message

Pasa asincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `overwrite_buffer`. Lo invoca el método `propagate`, cuando lo llama un bloque de origen.

```cpp
virtual message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Un puntero al objeto `message`.

*_PSource*<br/>
Puntero al bloque de origen que ofrece el mensaje.

### <a name="return-value"></a>Valor devuelto

[Message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

Coloca el `message _PMessage` en este `overwrite_buffer` bloque de mensajería y lo ofrece a todos los destinos vinculados.

```cpp
virtual void propagate_to_any_targets(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Un puntero a un objeto `message` que este `overwrite_buffer` ha tomado posesión de.

### <a name="remarks"></a>Observaciones

Este método sobrescribe el mensaje actual en el `overwrite_buffer` con el `_PMessage`de mensajes recién aceptado.

## <a name="send_message"></a>send_message

Pasa sincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `overwrite_buffer`. Lo invoca el método `send`, cuando lo llama un bloque de origen.

```cpp
virtual message_status send_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Un puntero al objeto `message`.

*_PSource*<br/>
Puntero al bloque de origen que ofrece el mensaje.

### <a name="return-value"></a>Valor devuelto

[Message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.

## <a name="supports_anonymous_source"></a>supports_anonymous_source

Invalida el método `supports_anonymous_source` para indicar que este bloque puede aceptar los mensajes que le ofrece un origen que no está vinculado.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Valor devuelto

**true** porque el bloque no pospone los mensajes ofrecidos.

## <a name="release_message"></a>release_message

Libera una reserva de mensaje anterior.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` que se va a liberar.

## <a name="reserve_message"></a>reserve_message

Reserva un mensaje ofrecido anteriormente por este `overwrite_buffer` bloque de mensajería.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
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

## <a name="value"></a>valor

Obtiene una referencia a la carga actual del mensaje que se almacena en el `overwrite_buffer` bloque de mensajería.

```cpp
T value();
```

### <a name="return-value"></a>Valor devuelto

La carga del mensaje almacenado actualmente.

### <a name="remarks"></a>Observaciones

El valor almacenado en el `overwrite_buffer` podría cambiar inmediatamente después de que se devuelva este método. Este método esperará hasta que llegue un mensaje si no hay ningún mensaje almacenado actualmente en el `overwrite_buffer`.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[unbounded_buffer (clase)](unbounded-buffer-class.md)<br/>
[single_assignment (clase)](single-assignment-class.md)
