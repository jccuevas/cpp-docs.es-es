---
title: overwrite_buffer (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- overwrite_buffer class
ms.assetid: 5cc428fe-3697-419c-9fb2-78f6181c9293
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82266e387bcba3e4e7f2e377c666ce890d258e0f
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162118"
---
# <a name="overwritebuffer-class"></a>Clase overwrite_buffer

Un bloque de mensajería `overwrite_buffer` es un bloque `propagator_block` de destino único, de varios orígenes y ordenado que es capaz de almacenar un único mensaje cada vez. Los nuevos mensajes sobrescriben a los retenidos previamente.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class overwrite_buffer : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de carga de los mensajes se almacena y se propaga por el búfer.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[overwrite_buffer](#ctor)|Sobrecargado. Construye un `overwrite_buffer` bloque de mensajería.|
|[~ overwrite_buffer (destructor)](#dtor)|Destruye el `overwrite_buffer` bloque de mensajería.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[has_value](#has_value)|Comprueba si este `overwrite_buffer` bloque de mensajería aún tiene un valor.|
|[valor](#value)|Obtiene una referencia a la carga actual del mensaje que se almacenan en el `overwrite_buffer` bloque de mensajería.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[accept_message](#accept_message)|Acepta un mensaje que se ha proporcionado por este `overwrite_buffer` bloque de mensajería, devolviendo una copia del mensaje al llamador.|
|[consume_message](#consume_message)|Consume un mensaje ofrecido previamente por el `overwrite_buffer` bloque de mensajería y reservado por el destino, devolviendo una copia del mensaje al llamador.|
|[link_target_notification](#link_target_notification)|Una devolución de llamada que notifica que se ha vinculado un nuevo destino para esta `overwrite_buffer` bloque de mensajería.|
|[propagate_message](#propagate_message)|Pasa de forma asincrónica un mensaje desde un `ISource` bloque a este `overwrite_buffer` bloque de mensajería. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Coloca el `message _PMessage` en este `overwrite_buffer` bloque de mensajería y ofrece a todos los destinos vinculados.|
|[release_message](#release_message)|Libera una reserva de mensaje anterior. (Invalida [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Reserva un mensaje ofrecido previamente por este `overwrite_buffer` bloque de mensajería. (Invalida [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Reanuda la propagación después de que se ha liberado una reserva. (Invalida [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Un mensaje de forma sincrónica, pasa un `ISource` bloque a este `overwrite_buffer` bloque de mensajería. Se invoca con el `send` método, cuando se llama a un bloque de origen.|
|[supports_anonymous_source](#supports_anonymous_source)|Invalida el `supports_anonymous_source` método para indicar que este bloque puede aceptar mensajes ofrecidos por un origen que no está vinculado. (Invalida [ITarget](itarget-class.md#supports_anonymous_source).)|

## <a name="remarks"></a>Comentarios

Un `overwrite_buffer` bloque de mensajería propaga las copias de su mensaje almacenado en cada uno de sus destinos.

Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block)](source-block-class.md)

[propagator_block](propagator-block-class.md)

`overwrite_buffer`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

##  <a name="accept_message"></a> accept_message

Acepta un mensaje que se ha proporcionado por este `overwrite_buffer` bloque de mensajería, devolviendo una copia del mensaje al llamador.

```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
El `runtime_object_identity` de la ofrecida `message` objeto.

### <a name="return-value"></a>Valor devuelto

Un puntero a la `message` que el llamador tiene ahora la propiedad de objeto.

### <a name="remarks"></a>Comentarios

El `overwrite_buffer` mensajería bloque devuelve copias del mensaje a sus destinos, en lugar de transferir la propiedad del mensaje mantiene actualmente.

##  <a name="consume_message"></a> consume_message

Consume un mensaje ofrecido previamente por el `overwrite_buffer` bloque de mensajería y reservado por el destino, devolviendo una copia del mensaje al llamador.

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

##  <a name="has_value"></a> has_value

Comprueba si este `overwrite_buffer` bloque de mensajería aún tiene un valor.

```
bool has_value() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si el bloque ha recibido un valor, **false** en caso contrario.

##  <a name="link_target_notification"></a> link_target_notification

Una devolución de llamada que notifica que se ha vinculado un nuevo destino para esta `overwrite_buffer` bloque de mensajería.

```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Un puntero al destino recién vinculado.

##  <a name="dtor"></a> ~ overwrite_buffer

Destruye el `overwrite_buffer` bloque de mensajería.

```
~overwrite_buffer();
```

##  <a name="ctor"></a> overwrite_buffer

Construye un `overwrite_buffer` bloque de mensajería.

```
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

*_Filtrar*<br/>
Una función de filtro que determina si se deben aceptar mensajes ofrecidos.

*_PScheduler*<br/>
El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `overwrite_buffer` .

*_PScheduleGroup*<br/>
El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `overwrite_buffer` . El objeto `Scheduler` utilizado está implícito en el grupo de programación.

### <a name="remarks"></a>Comentarios

El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PScheduleGroup` .

El tipo `filter_method` es un functor con firma `bool (T const &)` que es invocado por este `overwrite_buffer` bloque de mensajería para determinar si debe aceptar un mensaje proporcionado.

##  <a name="propagate_message"></a> propagate_message

Pasa de forma asincrónica un mensaje desde un `ISource` bloque a este `overwrite_buffer` bloque de mensajería. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.

```
virtual message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>Parámetros

*Parámetro _PMessage*<br/>
Un puntero al objeto `message`.

*_PSource*<br/>
Un puntero al bloque de origen que proporciona el mensaje.

### <a name="return-value"></a>Valor devuelto

Un [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.

##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets

Coloca el `message _PMessage` en este `overwrite_buffer` bloque de mensajería y ofrece a todos los destinos vinculados.

```
virtual void propagate_to_any_targets(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parámetros

*Parámetro _PMessage*<br/>
Un puntero a un `message` objeto que este `overwrite_buffer` ha asumido la titularidad de.

### <a name="remarks"></a>Comentarios

Este método sobrescribe el mensaje actual de la `overwrite_buffer` con el mensaje recién aceptado `_PMessage`.

##  <a name="send_message"></a> send_message

Un mensaje de forma sincrónica, pasa un `ISource` bloque a este `overwrite_buffer` bloque de mensajería. Se invoca con el `send` método, cuando se llama a un bloque de origen.

```
virtual message_status send_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>Parámetros

*Parámetro _PMessage*<br/>
Un puntero al objeto `message`.

*_PSource*<br/>
Un puntero al bloque de origen que proporciona el mensaje.

### <a name="return-value"></a>Valor devuelto

Un [message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.

##  <a name="supports_anonymous_source"></a> supports_anonymous_source

Invalida el `supports_anonymous_source` método para indicar que este bloque puede aceptar mensajes ofrecidos por un origen que no está vinculado.

```
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Valor devuelto

**True** porque no posponer el bloque de mensajes ofrecidos.

##  <a name="release_message"></a> release_message

Libera una reserva de mensaje anterior.

```
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
El `runtime_object_identity` de la `message` objeto liberarse.

##  <a name="reserve_message"></a> reserve_message

Reserva un mensaje ofrecido previamente por este `overwrite_buffer` bloque de mensajería.

```
virtual bool reserve_message(runtime_object_identity _MsgId);
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

##  <a name="value"></a> Valor

Obtiene una referencia a la carga actual del mensaje que se almacenan en el `overwrite_buffer` bloque de mensajería.

```
T value();
```

### <a name="return-value"></a>Valor devuelto

La carga del mensaje almacenado actualmente.

### <a name="remarks"></a>Comentarios

El valor almacenado en el `overwrite_buffer` podría cambiar inmediatamente después de que este método devuelve. Este método esperará hasta que llegue un mensaje si ningún mensaje actualmente se almacena en el `overwrite_buffer`.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[unbounded_buffer (clase)](unbounded-buffer-class.md)<br/>
[single_assignment (clase)](single-assignment-class.md)
