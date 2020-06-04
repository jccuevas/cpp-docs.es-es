---
title: transformer (clase)
ms.date: 11/04/2016
f1_keywords:
- transformer
- AGENTS/concurrency::transformer
- AGENTS/concurrency::transformer::transformer
- AGENTS/concurrency::transformer::accept_message
- AGENTS/concurrency::transformer::consume_message
- AGENTS/concurrency::transformer::link_target_notification
- AGENTS/concurrency::transformer::propagate_message
- AGENTS/concurrency::transformer::propagate_to_any_targets
- AGENTS/concurrency::transformer::release_message
- AGENTS/concurrency::transformer::reserve_message
- AGENTS/concurrency::transformer::resume_propagation
- AGENTS/concurrency::transformer::send_message
- AGENTS/concurrency::transformer::supports_anonymous_source
helpviewer_keywords:
- transformer class
ms.assetid: eea71925-7043-4a92-bfd4-dbc0ece5d081
ms.openlocfilehash: 75c7697087b8b3ad8ff15ae4d08f2b4701aaa36a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142354"
---
# <a name="transformer-class"></a>transformer (clase)

Un bloque de mensajería `transformer` es un bloque `propagator_block` de destino único, de varios orígenes y ordenado capaz de almacenar un número ilimitado de mensajes de un tipo diferente.

## <a name="syntax"></a>Sintaxis

```cpp
template<class _Input, class _Output>
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>,
    multi_link_registry<ISource<_Input>>>;
```

### <a name="parameters"></a>Parámetros

*_Input*<br/>
El tipo de carga de los mensajes aceptados por el búfer.

*_Output*<br/>
El tipo de carga de los mensajes almacenados y propagados por el búfer.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[transformador](#ctor)|Sobrecargado. Construye un bloque de mensajería `transformer` .|
|[~ Transformer (destructor)](#dtor)|Destruye el bloque de mensajería `transformer`.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[accept_message](#accept_message)|Acepta un mensaje ofrecido por este `transformer` bloque de mensajería, transfiriendo la propiedad al autor de la llamada.|
|[consume_message](#consume_message)|Consume un mensaje ofrecido anteriormente por el `transformer` y reservado por el destino, transfiriendo la propiedad al autor de la llamada.|
|[link_target_notification](#link_target_notification)|Una devolución de llamada que notifica que un nuevo destino se ha vinculado a este `transformer` bloque de mensajería.|
|[propagate_message](#propagate_message)|Pasa asincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `transformer`. Lo invoca el método `propagate`, cuando lo llama un bloque de origen.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Ejecuta la función de transformador en los mensajes de entrada.|
|[release_message](#release_message)|Libera una reserva de mensaje anterior. (Invalida [source_block:: release_message](source-block-class.md#release_message)).|
|[reserve_message](#reserve_message)|Reserva un mensaje ofrecido anteriormente por este `transformer` bloque de mensajería. (Invalida [source_block:: reserve_message](source-block-class.md#reserve_message)).|
|[resume_propagation](#resume_propagation)|Reanuda la propagación una vez que se ha liberado una reserva. (Invalida [source_block:: resume_propagation](source-block-class.md#resume_propagation)).|
|[send_message](#send_message)|Pasa sincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `transformer`. Lo invoca el método `send`, cuando lo llama un bloque de origen.|
|[supports_anonymous_source](#supports_anonymous_source)|Invalida el método `supports_anonymous_source` para indicar que este bloque puede aceptar los mensajes que le ofrece un origen que no está vinculado. (Invalida [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source)).|

## <a name="remarks"></a>Observaciones

Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`transformer`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="accept_message"></a>accept_message

Acepta un mensaje ofrecido por este `transformer` bloque de mensajería, transfiriendo la propiedad al autor de la llamada.

```cpp
virtual message<_Output>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto `message` proporcionado.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de `message` al que el llamador tiene ahora propiedad.

## <a name="consume_message"></a>consume_message

Consume un mensaje ofrecido anteriormente por el `transformer` y reservado por el destino, transfiriendo la propiedad al autor de la llamada.

```cpp
virtual message<_Output>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` que se va a consumir.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de `message` al que el llamador tiene ahora propiedad.

### <a name="remarks"></a>Observaciones

Similar a `accept`, pero siempre va precedido de una llamada a `reserve`.

## <a name="link_target_notification"></a>link_target_notification

Una devolución de llamada que notifica que un nuevo destino se ha vinculado a este `transformer` bloque de mensajería.

```cpp
virtual void link_target_notification(_Inout_ ITarget<_Output> *);
```

## <a name="propagate_message"></a>propagate_message

Pasa asincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `transformer`. Lo invoca el método `propagate`, cuando lo llama un bloque de origen.

```cpp
virtual message_status propagate_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Un puntero al objeto `message`.

*_PSource*<br/>
Puntero al bloque de origen que ofrece el mensaje.

### <a name="return-value"></a>Valor devuelto

[Message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

Ejecuta la función de transformador en los mensajes de entrada.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<_Output> *);
```

## <a name="release_message"></a>release_message

Libera una reserva de mensaje anterior.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` que se va a liberar.

## <a name="reserve_message"></a>reserve_message

Reserva un mensaje ofrecido anteriormente por este `transformer` bloque de mensajería.

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

## <a name="send_message"></a>send_message

Pasa sincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `transformer`. Lo invoca el método `send`, cuando lo llama un bloque de origen.

```cpp
virtual message_status send_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
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

## <a name="ctor"></a>transformador

Construye un bloque de mensajería `transformer` .

```cpp
transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Parámetros

*_Func*<br/>
Función que se invocará para cada mensaje aceptado.

*_PTarget*<br/>
Puntero a un bloque de destino que se va a vincular al transformador.

*_Filter*<br/>
Función de filtro que determina si se deben aceptar los mensajes ofrecidos.

*_PScheduler*<br/>
El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `transformer` .

*_PScheduleGroup*<br/>
El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `transformer` . El objeto `Scheduler` utilizado está implícito en el grupo de programación.

### <a name="remarks"></a>Observaciones

El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PScheduleGroup` .

El tipo `_Transform_method` es un functor con `_Output (_Input const &)` de firma invocado por este `transformer` bloque de mensajería para procesar un mensaje.

El tipo `filter_method` es un functor con `bool (_Input const &)` de firma invocado por este bloque de mensajería de `transformer` para determinar si debe aceptar o no un mensaje ofrecido.

## <a name="dtor"></a>~ Transformer

Destruye el bloque de mensajería `transformer`.

```cpp
~transformer();
```

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[call (clase)](call-class.md)
