---
title: Clase single_assignment
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
ms.openlocfilehash: 5a27fb6cdc13fbbd3ceb8a85adacf5491ddc3ce1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593484"
---
# <a name="singleassignment-class"></a>Clase single_assignment

Un bloque de mensajería `single_assignment` es un bloque `propagator_block` de destino único, de varios orígenes y ordenado capaz de almacenar un único `message` de una sola escritura.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class single_assignment : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de carga del mensaje se almacena y se propaga por el búfer.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[single_assignment](#ctor)|Sobrecargado. Construye un bloque de mensajería `single_assignment` .|
|[~ single_assignment (destructor)](#dtor)|Destruye el `single_assignment` bloque de mensajería.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[has_value](#has_value)|Comprueba si este `single_assignment` bloque de mensajería se ha inicializado con un valor aún.|
|[valor](#value)|Obtiene una referencia a la carga actual del mensaje que se almacenan en el `single_assignment` bloque de mensajería.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[accept_message](#accept_message)|Acepta un mensaje que se ha proporcionado por este `single_assignment` bloque de mensajería, devolviendo una copia del mensaje al llamador.|
|[consume_message](#consume_message)|Consume un mensaje ofrecido previamente por el `single_assignment` y reservado por el destino, devolviendo una copia del mensaje al llamador.|
|[link_target_notification](#link_target_notification)|Una devolución de llamada que notifica que se ha vinculado un nuevo destino para esta `single_assignment` bloque de mensajería.|
|[propagate_message](#propagate_message)|Pasa de forma asincrónica un mensaje desde un `ISource` bloque a este `single_assignment` bloque de mensajería. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Coloca el `message _PMessage` en este `single_assignment` bloque de mensajería y ofrece a todos los destinos vinculados.|
|[release_message](#release_message)|Libera una reserva de mensaje anterior. (Invalida [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Reserva un mensaje ofrecido previamente por este `single_assignment` bloque de mensajería. (Invalida [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Reanuda la propagación después de que se ha liberado una reserva. (Invalida [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Un mensaje de forma sincrónica, pasa un `ISource` bloque a este `single_assignment` bloque de mensajería. Se invoca con el `send` método, cuando se llama a un bloque de origen.|

## <a name="remarks"></a>Comentarios

Un `single_assignment` bloque de mensajería propaga las copias de su mensaje a cada destino.

Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block)](source-block-class.md)

[propagator_block](propagator-block-class.md)

`single_assignment`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

##  <a name="accept_message"></a> accept_message

Acepta un mensaje que se ha proporcionado por este `single_assignment` bloque de mensajería, devolviendo una copia del mensaje al llamador.

```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
El `runtime_object_identity` de la ofrecida `message` objeto.

### <a name="return-value"></a>Valor devuelto

Un puntero a la `message` que el llamador tiene ahora la propiedad de objeto.

### <a name="remarks"></a>Comentarios

El `single_assignment` mensajería bloque devuelve copias del mensaje a sus destinos, en lugar de transferir la propiedad del mensaje mantiene actualmente.

##  <a name="consume_message"></a> consume_message

Consume un mensaje ofrecido previamente por el `single_assignment` y reservado por el destino, devolviendo una copia del mensaje al llamador.

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

Comprueba si este `single_assignment` bloque de mensajería se ha inicializado con un valor aún.

```
bool has_value() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si el bloque ha recibido un valor, **false** en caso contrario.

##  <a name="link_target_notification"></a> link_target_notification

Una devolución de llamada que notifica que se ha vinculado un nuevo destino para esta `single_assignment` bloque de mensajería.

```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Un puntero al destino recién vinculado.

##  <a name="propagate_message"></a> propagate_message

Pasa de forma asincrónica un mensaje desde un `ISource` bloque a este `single_assignment` bloque de mensajería. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.

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

Coloca el `message` `_PMessage` en este `single_assignment` bloque de mensajería y ofrece a todos los destinos vinculados.

```
virtual void propagate_to_any_targets(_Inout_opt_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parámetros

*Parámetro _PMessage*<br/>
Un puntero a un `message` que este `single_assignment` ha tomado la posesión de bloque de mensajería.

##  <a name="release_message"></a> release_message

Libera una reserva de mensaje anterior.

```
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
El `runtime_object_identity` de la `message` objeto liberarse.

##  <a name="reserve_message"></a> reserve_message

Reserva un mensaje ofrecido previamente por este `single_assignment` bloque de mensajería.

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

##  <a name="send_message"></a> send_message

Un mensaje de forma sincrónica, pasa un `ISource` bloque a este `single_assignment` bloque de mensajería. Se invoca con el `send` método, cuando se llama a un bloque de origen.

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

##  <a name="ctor"></a> single_assignment

Construye un bloque de mensajería `single_assignment` .

```
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

*_Filtrar*<br/>
Una función de filtro que determina si se deben aceptar mensajes ofrecidos.

*_PScheduler*<br/>
El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `single_assignment` .

*_PScheduleGroup*<br/>
El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `single_assignment` . El objeto `Scheduler` utilizado está implícito en el grupo de programación.

### <a name="remarks"></a>Comentarios

El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PScheduleGroup` .

El tipo `filter_method` es un functor con firma `bool (T const &)` que es invocado por este `single_assignment` bloque de mensajería para determinar si debe aceptar un mensaje proporcionado.

##  <a name="dtor"></a> ~ single_assignment

Destruye el `single_assignment` bloque de mensajería.

```
~single_assignment();
```

##  <a name="value"></a> Valor

Obtiene una referencia a la carga actual del mensaje que se almacenan en el `single_assignment` bloque de mensajería.

```
T const& value();
```

### <a name="return-value"></a>Valor devuelto

La carga del mensaje almacenado.

### <a name="remarks"></a>Comentarios

Este método esperará hasta que llegue un mensaje si ningún mensaje actualmente se almacena en el `single_assignment` bloque de mensajería.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[overwrite_buffer (clase)](overwrite-buffer-class.md)<br/>
[unbounded_buffer (clase)](unbounded-buffer-class.md)

