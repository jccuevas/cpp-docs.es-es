---
title: target_block (clase)
ms.date: 11/04/2016
f1_keywords:
- target_block
- AGENTS/concurrency::target_block
- AGENTS/concurrency::target_block::target_block
- AGENTS/concurrency::target_block::propagate
- AGENTS/concurrency::target_block::send
- AGENTS/concurrency::target_block::async_send
- AGENTS/concurrency::target_block::decline_incoming_messages
- AGENTS/concurrency::target_block::enable_batched_processing
- AGENTS/concurrency::target_block::initialize_target
- AGENTS/concurrency::target_block::link_source
- AGENTS/concurrency::target_block::process_input_messages
- AGENTS/concurrency::target_block::process_message
- AGENTS/concurrency::target_block::propagate_message
- AGENTS/concurrency::target_block::register_filter
- AGENTS/concurrency::target_block::remove_sources
- AGENTS/concurrency::target_block::send_message
- AGENTS/concurrency::target_block::sync_send
- AGENTS/concurrency::target_block::unlink_source
- AGENTS/concurrency::target_block::unlink_sources
- AGENTS/concurrency::target_block::wait_for_async_sends
helpviewer_keywords:
- target_block class
ms.assetid: 3ce181b4-b94a-4894-bf7b-64fc09821f9f
ms.openlocfilehash: 4009133161133a99aeb0ee040f0c82fdbabecaa0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142638"
---
# <a name="target_block-class"></a>target_block (clase)

La clase `target_block` es una clase base abstracta que proporciona funcionalidad de administración de vínculo básica y comprueba errores solo para bloques de destino.

## <a name="syntax"></a>Sintaxis

```cpp
template<class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>>
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

### <a name="parameters"></a>Parámetros

*_SourceLinkRegistry*<br/>
El registro del vínculo que se va a usar para contener los vínculos de origen.

*_MessageProcessorType*<br/>
El tipo de procesador para el procesamiento de mensajes.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`source_iterator`|Tipo del iterador para el `source_link_manager` para este objeto `target_block`.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[target_block](#ctor)|Construye un objeto `target_block`.|
|[~ target_block destructor](#dtor)|Destruye el objeto `target_block`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[propagar](#propagate)|Pasa asincrónicamente un mensaje de un bloque de origen a este bloque de destino.|
|[send](#send)|Pasa sincrónicamente un mensaje de un bloque de origen a este bloque de destino.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[async_send](#async_send)|Envía de forma asincrónica un mensaje para su procesamiento.|
|[decline_incoming_messages](#decline_incoming_messages)|Indica al bloque que se deben rechazar los mensajes nuevos.|
|[enable_batched_processing](#enable_batched_processing)|Habilita el procesamiento por lotes para este bloque.|
|[initialize_target](#initialize_target)|Inicializa el objeto base. En concreto, es necesario inicializar el objeto de `message_processor`.|
|[link_source](#link_source)|Vincula un bloque de origen especificado a este objeto `target_block`.|
|[process_input_messages](#process_input_messages)|Procesa los mensajes que se reciben como entradas.|
|[process_message](#process_message)|Cuando se reemplaza en una clase derivada, procesa un mensaje aceptado por este objeto `target_block`.|
|[propagate_message](#propagate_message)|Cuando se reemplaza en una clase derivada, este método pasa de forma asincrónica un mensaje de un bloque `ISource` a este objeto `target_block`. Lo invoca el método `propagate`, cuando lo llama un bloque de origen.|
|[register_filter](#register_filter)|Registra un método de filtro que se invocará en todos los mensajes recibidos.|
|[remove_sources](#remove_sources)|Desvincula todos los orígenes después de esperar a que se completen las operaciones de envío asincrónicas pendientes.|
|[send_message](#send_message)|Cuando se reemplaza en una clase derivada, este método pasa sincrónicamente un mensaje de un bloque `ISource` a este objeto `target_block`. Lo invoca el método `send`, cuando lo llama un bloque de origen.|
|[sync_send](#sync_send)|Envía un mensaje de forma sincrónica para su procesamiento.|
|[unlink_source](#unlink_source)|Desvincula un bloque de origen especificado de este objeto `target_block`.|
|[unlink_sources](#unlink_sources)|Desvincula todos los bloques de origen de este objeto `target_block`. (Invalida [ITarget:: unlink_sources](itarget-class.md#unlink_sources)).|
|[wait_for_async_sends](#wait_for_async_sends)|Espera a que se completen todas las propagaciones asincrónicas.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[ITarget](itarget-class.md)

`target_block`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="async_send"></a>async_send

Envía de forma asincrónica un mensaje para su procesamiento.

```cpp
void async_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Puntero al mensaje que se está enviando.

## <a name="decline_incoming_messages"></a>decline_incoming_messages

Indica al bloque que se deben rechazar los mensajes nuevos.

```cpp
void decline_incoming_messages();
```

### <a name="remarks"></a>Observaciones

El destructor llama a este método para asegurarse de que se rechazan los nuevos mensajes mientras la destrucción está en curso.

## <a name="enable_batched_processing"></a>enable_batched_processing

Habilita el procesamiento por lotes para este bloque.

```cpp
void enable_batched_processing();
```

## <a name="initialize_target"></a>initialize_target

Inicializa el objeto base. En concreto, es necesario inicializar el objeto de `message_processor`.

```cpp
void initialize_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Parámetros

*_PScheduler*<br/>
Programador que se va a usar para programar tareas.

*_PScheduleGroup*<br/>
Grupo de programación que se va a usar para programar tareas.

## <a name="link_source"></a>link_source

Vincula un bloque de origen especificado a este objeto `target_block`.

```cpp
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parámetros

*_PSource*<br/>
Puntero al bloque de `ISource` que se va a vincular.

### <a name="remarks"></a>Observaciones

No se debe llamar directamente a esta función en un objeto `target_block`. Los bloques se deben conectar entre sí mediante el método `link_target` en `ISource` bloques, lo que invocará el método `link_source` en el destino correspondiente.

## <a name="process_input_messages"></a>process_input_messages

Procesa los mensajes que se reciben como entradas.

```cpp
virtual void process_input_messages(_Inout_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Puntero al mensaje que se va a procesar.

## <a name="process_message"></a>process_message

Cuando se reemplaza en una clase derivada, procesa un mensaje aceptado por este objeto `target_block`.

```cpp
virtual void process_message(message<_Source_type> *);
```

## <a name="propagate"></a>propagar

Pasa asincrónicamente un mensaje de un bloque de origen a este bloque de destino.

```cpp
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Un puntero al objeto `message`.

*_PSource*<br/>
Puntero al bloque de origen que ofrece el mensaje.

### <a name="return-value"></a>Valor devuelto

[Message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.

### <a name="remarks"></a>Observaciones

El método produce una excepción de [invalid_argument](../../../standard-library/invalid-argument-class.md) si se `NULL`el parámetro `_PMessage` o `_PSource`.

## <a name="propagate_message"></a>propagate_message

Cuando se reemplaza en una clase derivada, este método pasa de forma asincrónica un mensaje de un bloque `ISource` a este objeto `target_block`. Lo invoca el método `propagate`, cuando lo llama un bloque de origen.

```cpp
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Un puntero al objeto `message`.

*_PSource*<br/>
Puntero al bloque de origen que ofrece el mensaje.

### <a name="return-value"></a>Valor devuelto

[Message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.

## <a name="register_filter"></a>register_filter

Registra un método de filtro que se invocará en todos los mensajes recibidos.

```cpp
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>Parámetros

*_Filter*<br/>
Método de filtro.

## <a name="remove_sources"></a>remove_sources

Desvincula todos los orígenes después de esperar a que se completen las operaciones de envío asincrónicas pendientes.

```cpp
void remove_sources();
```

### <a name="remarks"></a>Observaciones

Todos los bloques de destino deben llamar a esta rutina para quitar los orígenes de su destructor.

## <a name="send"></a>Enviar

Pasa sincrónicamente un mensaje de un bloque de origen a este bloque de destino.

```cpp
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Un puntero al objeto `message`.

*_PSource*<br/>
Puntero al bloque de origen que ofrece el mensaje.

### <a name="return-value"></a>Valor devuelto

[Message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.

### <a name="remarks"></a>Observaciones

El método produce una excepción de [invalid_argument](../../../standard-library/invalid-argument-class.md) si se `NULL`el parámetro `_PMessage` o `_PSource`.

Usar el método `send` fuera del inicio del mensaje y propagar los mensajes dentro de una red es peligroso y puede provocar un interbloqueo.

Cuando `send` devuelve, el mensaje ya se aceptó y se transfirió al bloque de destino, o bien el destino lo rechazó.

## <a name="send_message"></a>send_message

Cuando se reemplaza en una clase derivada, este método pasa sincrónicamente un mensaje de un bloque `ISource` a este objeto `target_block`. Lo invoca el método `send`, cuando lo llama un bloque de origen.

```cpp
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>Valor devuelto

[Message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.

### <a name="remarks"></a>Observaciones

De forma predeterminada, este bloque devuelve `declined` a menos que se invalide por una clase derivada.

## <a name="sync_send"></a>sync_send

Envía un mensaje de forma sincrónica para su procesamiento.

```cpp
void sync_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Puntero al mensaje que se está enviando.

## <a name="ctor"></a>target_block

Construye un objeto `target_block`.

```cpp
target_block();
```

## <a name="dtor"></a>~ target_block

Destruye el objeto `target_block`.

```cpp
virtual ~target_block();
```

## <a name="unlink_source"></a>unlink_source

Desvincula un bloque de origen especificado de este objeto `target_block`.

```cpp
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parámetros

*_PSource*<br/>
Puntero al bloque de `ISource` que se va a desvincular.

## <a name="unlink_sources"></a>unlink_sources

Desvincula todos los bloques de origen de este objeto `target_block`.

```cpp
virtual void unlink_sources();
```

## <a name="wait_for_async_sends"></a>wait_for_async_sends

Espera a que se completen todas las propagaciones asincrónicas.

```cpp
void wait_for_async_sends();
```

### <a name="remarks"></a>Observaciones

Los destructores de bloque de mensajes usan este método para asegurarse de que todas las operaciones asincrónicas han tenido tiempo de finalizar antes de destruir el bloque.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[ITarget (clase)](itarget-class.md)
