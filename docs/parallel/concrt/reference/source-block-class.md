---
title: source_block (clase)
ms.date: 11/04/2016
f1_keywords:
- source_block
- AGENTS/concurrency::source_block
- AGENTS/concurrency::source_block::source_block
- AGENTS/concurrency::source_block::accept
- AGENTS/concurrency::source_block::acquire_ref
- AGENTS/concurrency::source_block::consume
- AGENTS/concurrency::source_block::link_target
- AGENTS/concurrency::source_block::release
- AGENTS/concurrency::source_block::release_ref
- AGENTS/concurrency::source_block::reserve
- AGENTS/concurrency::source_block::unlink_target
- AGENTS/concurrency::source_block::unlink_targets
- AGENTS/concurrency::source_block::accept_message
- AGENTS/concurrency::source_block::async_send
- AGENTS/concurrency::source_block::consume_message
- AGENTS/concurrency::source_block::enable_batched_processing
- AGENTS/concurrency::source_block::initialize_source
- AGENTS/concurrency::source_block::link_target_notification
- AGENTS/concurrency::source_block::process_input_messages
- AGENTS/concurrency::source_block::propagate_output_messages
- AGENTS/concurrency::source_block::propagate_to_any_targets
- AGENTS/concurrency::source_block::release_message
- AGENTS/concurrency::source_block::remove_targets
- AGENTS/concurrency::source_block::reserve_message
- AGENTS/concurrency::source_block::resume_propagation
- AGENTS/concurrency::source_block::sync_send
- AGENTS/concurrency::source_block::unlink_target_notification
- AGENTS/concurrency::source_block::wait_for_outstanding_async_sends
helpviewer_keywords:
- source_block class
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
ms.openlocfilehash: 3a0d69bc2e2904b1dcf37a7e9891d95bd869a610
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424192"
---
# <a name="source_block-class"></a>source_block (clase)

La clase `source_block` es una clase base abstracta solo para bloques de origen. La clase proporciona funcionalidad de administración de vínculo básico, así como comprobaciones de errores frecuentes.

## <a name="syntax"></a>Sintaxis

```cpp
template<class _TargetLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;
```

### <a name="parameters"></a>Parámetros

*_TargetLinkRegistry*<br/>
Vincular el registro que se usará para contener los vínculos de destino.

*_MessageProcessorType*<br/>
Tipo de procesador para el procesamiento de mensajes.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`target_iterator`|Iterador para recorrer los destinos conectados.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[source_block](#ctor)|Construye un objeto `source_block`.|
|[~ source_block destructor](#dtor)|Destruye el objeto `source_block`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[acept](#accept)|Acepta un mensaje ofrecido por este objeto `source_block`, transfiriendo la propiedad al autor de la llamada.|
|[acquire_ref](#acquire_ref)|Adquiere un recuento de referencias en este objeto `source_block` para evitar la eliminación.|
|[consumo](#consume)|Consume un mensaje ofrecido anteriormente por este objeto `source_block` y reservado correctamente por el destino, transfiriendo la propiedad al autor de la llamada.|
|[link_target](#link_target)|Vincula un bloque de destino a este objeto `source_block`.|
|[release](#release)|Libera una reserva de mensajes correcta anterior.|
|[release_ref](#release_ref)|Libera un recuento de referencias en este objeto `source_block`.|
|[reserve](#reserve)|Reserva un mensaje ofrecido anteriormente por este objeto `source_block`.|
|[unlink_target](#unlink_target)|Desvincula un bloque de destino de este objeto `source_block`.|
|[unlink_targets](#unlink_targets)|Desvincula todos los bloques de destino de este objeto `source_block`. (Invalida [ISource:: unlink_targets](isource-class.md#unlink_targets)).|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[accept_message](#accept_message)|Cuando se reemplaza en una clase derivada, acepta un mensaje ofrecido por el origen. Los bloques de mensajes deben invalidar este método para validar el `_MsgId` y devolver un mensaje.|
|[async_send](#async_send)|Pone en cola asincrónicamente los mensajes e inicia una tarea de propagación, si aún no se ha hecho.|
|[consume_message](#consume_message)|Cuando se reemplaza en una clase derivada, consume un mensaje que se ha reservado previamente.|
|[enable_batched_processing](#enable_batched_processing)|Habilita el procesamiento por lotes para este bloque.|
|[initialize_source](#initialize_source)|Inicializa el `message_propagator` dentro de este `source_block`.|
|[link_target_notification](#link_target_notification)|Devolución de llamada que notifica que un nuevo destino se ha vinculado a este objeto `source_block`.|
|[process_input_messages](#process_input_messages)|Procesar los mensajes de entrada. Esto solo es útil para los bloques de propagación, que derivan de source_block|
|[propagate_output_messages](#propagate_output_messages)|Propagar los mensajes a los destinos.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Cuando se reemplaza en una clase derivada, propaga el mensaje especificado a uno o todos los destinos vinculados. Esta es la rutina de propagación principal para los bloques de mensajes.|
|[release_message](#release_message)|Cuando se reemplaza en una clase derivada, libera una reserva de mensaje anterior.|
|[remove_targets](#remove_targets)|Quita todos los vínculos de destino para este bloque de origen. Se debe llamar a este método desde el destructor.|
|[reserve_message](#reserve_message)|Cuando se reemplaza en una clase derivada, reserva un mensaje ofrecido anteriormente por este objeto `source_block`.|
|[resume_propagation](#resume_propagation)|Cuando se reemplaza en una clase derivada, reanuda la propagación una vez que se ha liberado una reserva.|
|[sync_send](#sync_send)|Pone en cola los mensajes de forma sincrónica e inicia una tarea de propagación, si aún no se ha hecho.|
|[unlink_target_notification](#unlink_target_notification)|Devolución de llamada que notifica que un destino se ha desvinculado de este objeto `source_block`.|
|[wait_for_outstanding_async_sends](#wait_for_outstanding_async_sends)|Espera a que se completen todas las propagaciones asincrónicas. Esta espera de giro específica del propagador se usa en destructores de bloques de mensajes para asegurarse de que todas las propagaciones asincrónicas tienen tiempo de finalización antes de destruir el bloque.|

## <a name="remarks"></a>Observaciones

Los bloques de mensajes deben derivar de este bloque para aprovechar las ventajas de la administración de vínculos y la sincronización proporcionada por esta clase.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[ISource](isource-class.md)

`source_block`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="accept"></a>acept

Acepta un mensaje ofrecido por este objeto `source_block`, transfiriendo la propiedad al autor de la llamada.

```cpp
virtual message<_Target_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto `message` proporcionado.

*_PTarget*<br/>
Puntero al bloque de destino que llama al método de `accept`.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de `message` al que el llamador tiene ahora propiedad.

### <a name="remarks"></a>Observaciones

El método produce una excepción [invalid_argument](../../../standard-library/invalid-argument-class.md) si el `_PTarget` del parámetro es `NULL`.

Un destino llama al método `accept` mientras este bloque `ISource` ofrece un mensaje. El puntero de mensaje devuelto puede ser diferente del que se pasa al método `propagate` del bloque de `ITarget`, si este origen decide realizar una copia del mensaje.

## <a name="accept_message"></a>accept_message

Cuando se reemplaza en una clase derivada, acepta un mensaje ofrecido por el origen. Los bloques de mensajes deben invalidar este método para validar el `_MsgId` y devolver un mensaje.

```cpp
virtual message<_Target_type>* accept_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
La identidad del objeto en tiempo de ejecución del objeto `message`.

### <a name="return-value"></a>Valor devuelto

Un puntero al mensaje del que el llamador tiene ahora propiedad.

### <a name="remarks"></a>Observaciones

Para transferir la propiedad, debe devolverse el puntero de mensaje original. Para mantener la propiedad, debe realizarse y devolverse una copia de la carga del mensaje.

## <a name="acquire_ref"></a>acquire_ref

Adquiere un recuento de referencias en este objeto `source_block` para evitar la eliminación.

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Target_type> *);
```

### <a name="remarks"></a>Observaciones

Un objeto `ITarget` que se vincula a este origen llama a este método durante el método `link_target`.

## <a name="async_send"></a>async_send

Pone en cola asincrónicamente los mensajes e inicia una tarea de propagación, si aún no se ha hecho.

```cpp
virtual void async_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>Parámetros

*_Msg*<br/>
Puntero a un objeto `message` que se va a enviar de forma asincrónica.

## <a name="consume"></a>emplear

Consume un mensaje ofrecido anteriormente por este objeto `source_block` y reservado correctamente por el destino, transfiriendo la propiedad al autor de la llamada.

```cpp
virtual message<_Target_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` reservado.

*_PTarget*<br/>
Puntero al bloque de destino que llama al método de `consume`.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de `message` al que el llamador tiene ahora propiedad.

### <a name="remarks"></a>Observaciones

El método produce una excepción [invalid_argument](../../../standard-library/invalid-argument-class.md) si el `_PTarget` del parámetro es `NULL`.

El método produce una excepción [bad_target](bad-target-class.md) si el `_PTarget` de parámetros no representa el destino que llamó a `reserve`.

El método `consume` es similar a `accept`, pero siempre debe ir precedido de una llamada a `reserve` que devolvió **true**.

## <a name="consume_message"></a>consume_message

Cuando se reemplaza en una clase derivada, consume un mensaje que se ha reservado previamente.

```cpp
virtual message<_Target_type>* consume_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` que se va a consumir.

### <a name="return-value"></a>Valor devuelto

Un puntero al mensaje del que el llamador tiene ahora propiedad.

### <a name="remarks"></a>Observaciones

Similar a `accept`, pero siempre va precedido de una llamada a `reserve`.

## <a name="enable_batched_processing"></a>enable_batched_processing

Habilita el procesamiento por lotes para este bloque.

```cpp
void enable_batched_processing();
```

## <a name="initialize_source"></a>initialize_source

Inicializa el `message_propagator` dentro de este `source_block`.

```cpp
void initialize_source(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Parámetros

*_PScheduler*<br/>
Programador que se va a usar para programar tareas.

*_PScheduleGroup*<br/>
Grupo de programación que se va a usar para programar tareas.

## <a name="link_target"></a>link_target

Vincula un bloque de destino a este objeto `source_block`.

```cpp
virtual void link_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Puntero a un bloque `ITarget` que se va a vincular a este objeto `source_block`.

### <a name="remarks"></a>Observaciones

El método produce una excepción [invalid_argument](../../../standard-library/invalid-argument-class.md) si el `_PTarget` del parámetro es `NULL`.

## <a name="link_target_notification"></a>link_target_notification

Devolución de llamada que notifica que un nuevo destino se ha vinculado a este objeto `source_block`.

```cpp
virtual void link_target_notification(_Inout_ ITarget<_Target_type> *);
```

## <a name="process_input_messages"></a>process_input_messages

Procesar los mensajes de entrada. Esto solo es útil para los bloques de propagación, que derivan de source_block

```cpp
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Puntero al mensaje que se va a procesar.

## <a name="propagate_output_messages"></a>propagate_output_messages

Propagar los mensajes a los destinos.

```cpp
virtual void propagate_output_messages();
```

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

Cuando se reemplaza en una clase derivada, propaga el mensaje especificado a uno o todos los destinos vinculados. Esta es la rutina de propagación principal para los bloques de mensajes.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Puntero al mensaje que se va a propagar.

## <a name="release"></a>emisión

Libera una reserva de mensajes correcta anterior.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` reservado.

*_PTarget*<br/>
Puntero al bloque de destino que llama al método de `release`.

### <a name="remarks"></a>Observaciones

El método produce una excepción [invalid_argument](../../../standard-library/invalid-argument-class.md) si el `_PTarget` del parámetro es `NULL`.

El método produce una excepción [bad_target](bad-target-class.md) si el `_PTarget` de parámetros no representa el destino que llamó a `reserve`.

## <a name="release_message"></a>release_message

Cuando se reemplaza en una clase derivada, libera una reserva de mensaje anterior.

```cpp
virtual void release_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` que se va a liberar.

## <a name="release_ref"></a>release_ref

Libera un recuento de referencias en este objeto `source_block`.

```cpp
virtual void release_ref(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Puntero al bloque de destino que llama a este método.

### <a name="remarks"></a>Observaciones

Un objeto `ITarget` al que se va a desvincular de este origen llama a este método. El bloque de origen puede liberar los recursos reservados para el bloque de destino.

## <a name="remove_targets"></a>remove_targets

Quita todos los vínculos de destino para este bloque de origen. Se debe llamar a este método desde el destructor.

```cpp
void remove_targets();
```

## <a name="reserve"></a>realizan

Reserva un mensaje ofrecido anteriormente por este objeto `source_block`.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto `message` proporcionado.

*_PTarget*<br/>
Puntero al bloque de destino que llama al método de `reserve`.

### <a name="return-value"></a>Valor devuelto

**true** si el mensaje se ha reservado correctamente; de lo contrario, **false** . Se puede producir un error en las reservas por muchas razones, como: el mensaje ya estaba reservado o lo aceptó otro destino, el origen podría denegar reservas, etc.

### <a name="remarks"></a>Observaciones

El método produce una excepción [invalid_argument](../../../standard-library/invalid-argument-class.md) si el `_PTarget` del parámetro es `NULL`.

Después de llamar a `reserve`, si se realiza correctamente, debe llamar a `consume` o `release` para poder llevar a cabo o renunciar al mensaje, respectivamente.

## <a name="reserve_message"></a>reserve_message

Cuando se reemplaza en una clase derivada, reserva un mensaje ofrecido anteriormente por este objeto `source_block`.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` que se va a reservar.

### <a name="return-value"></a>Valor devuelto

**true** si el mensaje se ha reservado correctamente; de lo contrario, **false** .

### <a name="remarks"></a>Observaciones

Una vez que se llama a `reserve`, si devuelve **true**, se debe llamar a `consume` o `release` para tomar o liberar la propiedad del mensaje.

## <a name="resume_propagation"></a>resume_propagation

Cuando se reemplaza en una clase derivada, reanuda la propagación una vez que se ha liberado una reserva.

```cpp
virtual void resume_propagation() = 0;
```

## <a name="ctor"></a>source_block

Construye un objeto `source_block`.

```cpp
source_block();
```

## <a name="dtor"></a>~ source_block

Destruye el objeto `source_block`.

```cpp
virtual ~source_block();
```

## <a name="sync_send"></a>sync_send

Pone en cola los mensajes de forma sincrónica e inicia una tarea de propagación, si aún no se ha hecho.

```cpp
virtual void sync_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>Parámetros

*_Msg*<br/>
Puntero a un objeto `message` que se va a enviar de forma sincrónica.

## <a name="unlink_target"></a>unlink_target

Desvincula un bloque de destino de este objeto `source_block`.

```cpp
virtual void unlink_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Un puntero a un bloque `ITarget` para desvincular de este objeto `source_block`.

### <a name="remarks"></a>Observaciones

El método produce una excepción [invalid_argument](../../../standard-library/invalid-argument-class.md) si el `_PTarget` del parámetro es `NULL`.

## <a name="unlink_target_notification"></a>unlink_target_notification

Devolución de llamada que notifica que un destino se ha desvinculado de este objeto `source_block`.

```cpp
virtual void unlink_target_notification(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
`ITarget` bloque que se ha desvinculado.

## <a name="unlink_targets"></a>unlink_targets

Desvincula todos los bloques de destino de este objeto `source_block`.

```cpp
virtual void unlink_targets();
```

## <a name="wait_for_outstanding_async_sends"></a>wait_for_outstanding_async_sends

Espera a que se completen todas las propagaciones asincrónicas. Esta espera de giro específica del propagador se usa en destructores de bloques de mensajes para asegurarse de que todas las propagaciones asincrónicas tienen tiempo de finalización antes de destruir el bloque.

```cpp
void wait_for_outstanding_async_sends();
```

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[ISource (clase)](isource-class.md)
