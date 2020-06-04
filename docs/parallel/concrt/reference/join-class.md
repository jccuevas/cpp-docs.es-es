---
title: join (clase)
ms.date: 11/04/2016
f1_keywords:
- join
- AGENTS/concurrency::join
- AGENTS/concurrency::join::join
- AGENTS/concurrency::join::accept_message
- AGENTS/concurrency::join::consume_message
- AGENTS/concurrency::join::link_target_notification
- AGENTS/concurrency::join::propagate_message
- AGENTS/concurrency::join::propagate_to_any_targets
- AGENTS/concurrency::join::release_message
- AGENTS/concurrency::join::reserve_message
- AGENTS/concurrency::join::resume_propagation
helpviewer_keywords:
- join class
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
ms.openlocfilehash: f75cf8483e7d6d65d118cc8f0ea756302d1b1d7c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139846"
---
# <a name="join-class"></a>join (clase)

Un bloque de mensajería `join` es un bloque `propagator_block` de destino único y de varios orígenes ordenado, que combina los mensajes de tipo `T` de cada uno de sus orígenes.

## <a name="syntax"></a>Sintaxis

```cpp
template<class T,
    join_type _Jtype = non_greedy>
class join : public propagator_block<single_link_registry<ITarget<std::vector<T>>>,
    multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de carga de los mensajes combinados y propagados por el bloque.

*_Jtype*<br/>
El tipo de `join` bloque es, ya sea `greedy` o `non_greedy`

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[join](#ctor)|Sobrecargado. Construye un bloque de mensajería `join` .|
|[~ join (destructor)](#dtor)|Destruye el bloque de `join`.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[accept_message](#accept_message)|Acepta un mensaje ofrecido por este `join` bloque de mensajería, transfiriendo la propiedad al autor de la llamada.|
|[consume_message](#consume_message)|Consume un mensaje ofrecido anteriormente por el `join` bloque de mensajería y reservado por el destino, transfiriendo la propiedad al autor de la llamada.|
|[link_target_notification](#link_target_notification)|Una devolución de llamada que notifica que un nuevo destino se ha vinculado a este `join` bloque de mensajería.|
|[propagate_message](#propagate_message)|Pasa asincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `join`. Lo invoca el método `propagate`, cuando lo llama un bloque de origen.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Construye un mensaje de salida que contiene un mensaje de entrada de cada origen cuando todos han propagado un mensaje. Envía el mensaje de salida a cada uno de sus destinos.|
|[release_message](#release_message)|Libera una reserva de mensaje anterior. (Invalida [source_block:: release_message](source-block-class.md#release_message)).|
|[reserve_message](#reserve_message)|Reserva un mensaje ofrecido anteriormente por este `join` bloque de mensajería. (Invalida [source_block:: reserve_message](source-block-class.md#reserve_message)).|
|[resume_propagation](#resume_propagation)|Reanuda la propagación una vez que se ha liberado una reserva. (Invalida [source_block:: resume_propagation](source-block-class.md#resume_propagation)).|

## <a name="remarks"></a>Observaciones

Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`join`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="accept_message"></a>accept_message

Acepta un mensaje ofrecido por este `join` bloque de mensajería, transfiriendo la propiedad al autor de la llamada.

```cpp
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto `message` proporcionado.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de `message` al que el llamador tiene ahora propiedad.

## <a name="consume_message"></a>consume_message

Consume un mensaje ofrecido anteriormente por el `join` bloque de mensajería y reservado por el destino, transfiriendo la propiedad al autor de la llamada.

```cpp
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` que se va a consumir.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de `message` al que el llamador tiene ahora propiedad.

### <a name="remarks"></a>Observaciones

Similar a `accept`, pero siempre va precedido de una llamada a `reserve`.

## <a name="ctor"></a>vuelve

Construye un bloque de mensajería `join` .

```cpp
join(
    size_t _NumInputs);

join(
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Parámetros

*_NumInputs*<br/>
El número de entradas que se permitirá este bloque `join`.

*_Filter*<br/>
Función de filtro que determina si se deben aceptar los mensajes ofrecidos.

*_PScheduler*<br/>
El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `join` .

*_PScheduleGroup*<br/>
El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `join` . El objeto `Scheduler` utilizado está implícito en el grupo de programación.

### <a name="remarks"></a>Observaciones

El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PScheduleGroup` .

El tipo `filter_method` es un functor con `bool (T const &)` de firma invocado por este bloque de mensajería de `join` para determinar si debe aceptar o no un mensaje ofrecido.

## <a name="dtor"></a>~ join

Destruye el bloque de `join`.

```cpp
~join();
```

## <a name="link_target_notification"></a>link_target_notification

Una devolución de llamada que notifica que un nuevo destino se ha vinculado a este `join` bloque de mensajería.

```cpp
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```

## <a name="propagate_message"></a>propagate_message

Pasa asincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `join`. Lo invoca el método `propagate`, cuando lo llama un bloque de origen.

```cpp
message_status propagate_message(
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

Construye un mensaje de salida que contiene un mensaje de entrada de cada origen cuando todos han propagado un mensaje. Envía el mensaje de salida a cada uno de sus destinos.

```cpp
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
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

Reserva un mensaje ofrecido anteriormente por este `join` bloque de mensajería.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto `message` proporcionado.

### <a name="return-value"></a>Valor devuelto

**true** si el mensaje se ha reservado correctamente; de lo contrario, **false** .

### <a name="remarks"></a>Observaciones

Una vez que se llama a `reserve`, si devuelve **true**, se debe llamar a `consume` o `release` para tomar o liberar la propiedad del mensaje.

## <a name="resume_propagation"></a>resume_propagation

Reanuda la propagación una vez que se ha liberado una reserva.

```cpp
virtual void resume_propagation();
```

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[choice (clase)](choice-class.md)<br/>
[multitype_join (clase)](multitype-join-class.md)
