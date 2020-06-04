---
title: single_assignment (clase)
ms.date: 11/04/2016
f1_keywords:
- single_assignment
- AGENTS/concurrency::single_assignment
- AGENTS/concurrency::single_assignment::single_assignment
- AGENTS/concurrency::single_assignment::has_value
- AGENTS/concurrency::single_assignment::value
- AGENTS/concurrency::single_assignment::accept_message
- AGENTS/concurrency::single_assignment::consume_message
- AGENTS/concurrency::single_assignment::link_target_notification
- AGENTS/concurrency::single_assignment::propagate_message
- AGENTS/concurrency::single_assignment::propagate_to_any_targets
- AGENTS/concurrency::single_assignment::release_message
- AGENTS/concurrency::single_assignment::reserve_message
- AGENTS/concurrency::single_assignment::resume_propagation
- AGENTS/concurrency::single_assignment::send_message
helpviewer_keywords:
- single_assignment class
ms.assetid: ccc34728-8de9-4e07-b83d-a36a58d9d2b9
ms.openlocfilehash: 0d302f4f7f85737d9c3b2368e3ae04d88bc1a370
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142731"
---
# <a name="single_assignment-class"></a>single_assignment (clase)

Un bloque de mensajería `single_assignment` es un bloque `propagator_block` de destino único, de varios orígenes y ordenado capaz de almacenar un único `message` de una sola escritura.

## <a name="syntax"></a>Sintaxis

```cpp
template<class T>
class single_assignment : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de carga del mensaje almacenado y propagado por el búfer.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[single_assignment](#ctor)|Sobrecargado. Construye un bloque de mensajería `single_assignment` .|
|[~ single_assignment destructor](#dtor)|Destruye el bloque de mensajería `single_assignment`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[has_value](#has_value)|Comprueba si esta `single_assignment` bloque de mensajería se ha inicializado con un valor todavía.|
|[value](#value)|Obtiene una referencia a la carga actual del mensaje que se almacena en el `single_assignment` bloque de mensajería.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[accept_message](#accept_message)|Acepta un mensaje ofrecido por este `single_assignment` bloque de mensajería y devuelve una copia del mensaje al autor de la llamada.|
|[consume_message](#consume_message)|Consume un mensaje ofrecido anteriormente por el `single_assignment` y reservado por el destino, y devuelve una copia del mensaje al autor de la llamada.|
|[link_target_notification](#link_target_notification)|Una devolución de llamada que notifica que un nuevo destino se ha vinculado a este `single_assignment` bloque de mensajería.|
|[propagate_message](#propagate_message)|Pasa asincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `single_assignment`. Lo invoca el método `propagate`, cuando lo llama un bloque de origen.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Coloca el `message _PMessage` en este `single_assignment` bloque de mensajería y lo ofrece a todos los destinos vinculados.|
|[release_message](#release_message)|Libera una reserva de mensaje anterior. (Invalida [source_block:: release_message](source-block-class.md#release_message)).|
|[reserve_message](#reserve_message)|Reserva un mensaje ofrecido anteriormente por este `single_assignment` bloque de mensajería. (Invalida [source_block:: reserve_message](source-block-class.md#reserve_message)).|
|[resume_propagation](#resume_propagation)|Reanuda la propagación una vez que se ha liberado una reserva. (Invalida [source_block:: resume_propagation](source-block-class.md#resume_propagation)).|
|[send_message](#send_message)|Pasa sincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `single_assignment`. Lo invoca el método `send`, cuando lo llama un bloque de origen.|

## <a name="remarks"></a>Observaciones

Un bloque de mensajería de `single_assignment` propaga las copias de su mensaje a cada destino.

Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`single_assignment`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="accept_message"></a>accept_message

Acepta un mensaje ofrecido por este `single_assignment` bloque de mensajería y devuelve una copia del mensaje al autor de la llamada.

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto `message` proporcionado.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de `message` al que el llamador tiene ahora propiedad.

### <a name="remarks"></a>Observaciones

El bloque de mensajería de `single_assignment` devuelve copias del mensaje a sus destinos, en lugar de transferir la propiedad del mensaje que se encuentra actualmente.

## <a name="consume_message"></a>consume_message

Consume un mensaje ofrecido anteriormente por el `single_assignment` y reservado por el destino, y devuelve una copia del mensaje al autor de la llamada.

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

Comprueba si esta `single_assignment` bloque de mensajería se ha inicializado con un valor todavía.

```cpp
bool has_value() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si el bloque ha recibido un valor; de lo contrario, **false** .

## <a name="link_target_notification"></a>link_target_notification

Una devolución de llamada que notifica que un nuevo destino se ha vinculado a este `single_assignment` bloque de mensajería.

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Puntero al destino recién vinculado.

## <a name="propagate_message"></a>propagate_message

Pasa asincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `single_assignment`. Lo invoca el método `propagate`, cuando lo llama un bloque de origen.

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

Coloca el `_PMessage` de `message` en este `single_assignment` bloque de mensajería y lo ofrece a todos los destinos vinculados.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Un puntero a un `message` que este bloque de mensajería `single_assignment` ha tomado propiedad de.

## <a name="release_message"></a>release_message

Libera una reserva de mensaje anterior.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` que se va a liberar.

## <a name="reserve_message"></a>reserve_message

Reserva un mensaje ofrecido anteriormente por este `single_assignment` bloque de mensajería.

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

Pasa sincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `single_assignment`. Lo invoca el método `send`, cuando lo llama un bloque de origen.

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

## <a name="ctor"></a>single_assignment

Construye un bloque de mensajería `single_assignment` .

```cpp
single_assignment();

single_assignment(
    filter_method const& _Filter);

single_assignment(
    Scheduler& _PScheduler);

single_assignment(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

single_assignment(
    ScheduleGroup& _PScheduleGroup);

single_assignment(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Parámetros

*_Filter*<br/>
Función de filtro que determina si se deben aceptar los mensajes ofrecidos.

*_PScheduler*<br/>
El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `single_assignment` .

*_PScheduleGroup*<br/>
El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `single_assignment` . El objeto `Scheduler` utilizado está implícito en el grupo de programación.

### <a name="remarks"></a>Observaciones

El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PScheduleGroup` .

El tipo `filter_method` es un functor con `bool (T const &)` de firma invocado por este bloque de mensajería de `single_assignment` para determinar si debe aceptar o no un mensaje ofrecido.

## <a name="dtor"></a>~ single_assignment

Destruye el bloque de mensajería `single_assignment`.

```cpp
~single_assignment();
```

## <a name="value"></a>valor

Obtiene una referencia a la carga actual del mensaje que se almacena en el `single_assignment` bloque de mensajería.

```cpp
T const& value();
```

### <a name="return-value"></a>Valor devuelto

La carga del mensaje almacenado.

### <a name="remarks"></a>Observaciones

Este método esperará hasta que llegue un mensaje si no hay ningún mensaje almacenado actualmente en el bloque de mensajería `single_assignment`.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[overwrite_buffer (clase)](overwrite-buffer-class.md)<br/>
[unbounded_buffer (clase)](unbounded-buffer-class.md)
