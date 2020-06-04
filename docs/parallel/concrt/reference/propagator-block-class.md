---
title: propagator_block (clase)
ms.date: 11/04/2016
f1_keywords:
- propagator_block
- AGENTS/concurrency::propagator_block
- AGENTS/concurrency::propagator_block::propagator_block
- AGENTS/concurrency::propagator_block::propagate
- AGENTS/concurrency::propagator_block::send
- AGENTS/concurrency::propagator_block::decline_incoming_messages
- AGENTS/concurrency::propagator_block::initialize_source_and_target
- AGENTS/concurrency::propagator_block::link_source
- AGENTS/concurrency::propagator_block::process_input_messages
- AGENTS/concurrency::propagator_block::propagate_message
- AGENTS/concurrency::propagator_block::register_filter
- AGENTS/concurrency::propagator_block::remove_network_links
- AGENTS/concurrency::propagator_block::send_message
- AGENTS/concurrency::propagator_block::unlink_source
- AGENTS/concurrency::propagator_block::unlink_sources
helpviewer_keywords:
- propagator_block class
ms.assetid: 86aa75fd-eda5-42aa-aadf-25c0c1c9742d
ms.openlocfilehash: 340af181669cbbf4c5ba910aa3ee862bd40ba27f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138741"
---
# <a name="propagator_block-class"></a>propagator_block (clase)

La clase `propagator_block` es una clase base abstracta para los bloques de mensaje que son un bloque de origen y de destino. Combina la funcionalidad de las clases `source_block` y `target_block`.

## <a name="syntax"></a>Sintaxis

```cpp
template<class _TargetLinkRegistry, class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class propagator_block : public source_block<_TargetLinkRegistry,
    _MessageProcessorType>,
public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

### <a name="parameters"></a>Parámetros

*_TargetLinkRegistry*<br/>
El registro del vínculo que se va a usar para contener los vínculos de destino.

*_SourceLinkRegistry*<br/>
El registro del vínculo que se va a usar para contener los vínculos de origen.

*_MessageProcessorType*<br/>
El tipo de procesador para el procesamiento de mensajes.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`source_iterator`|Tipo del iterador para el `source_link_manager` de este `propagator_block`.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[propagator_block](#ctor)|Construye un objeto `propagator_block`.|
|[~ propagator_block destructor](#dtor)|Destruye un objeto `propagator_block`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[propagar](#propagate)|Pasa asincrónicamente un mensaje de un bloque de origen a este bloque de destino.|
|[send](#send)|Inicia sincrónicamente un mensaje en este bloque. Lo llama un bloque `ISource`. Cuando se complete esta función, el mensaje ya se habrá propagado en el bloque.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[decline_incoming_messages](#decline_incoming_messages)|Indica al bloque que se deben rechazar los mensajes nuevos.|
|[initialize_source_and_target](#initialize_source_and_target)|Inicializa el objeto base. En concreto, es necesario inicializar el objeto de `message_processor`.|
|[link_source](#link_source)|Vincula un bloque de origen especificado a este objeto `propagator_block`.|
|[process_input_messages](#process_input_messages)|Procesar los mensajes de entrada. Esto solo es útil para los bloques de propagación, que derivan de source_block (invalida [source_block::p rocess_input_messages](source-block-class.md#process_input_messages)).|
|[propagate_message](#propagate_message)|Cuando se reemplaza en una clase derivada, este método pasa de forma asincrónica un mensaje de un bloque `ISource` a este objeto `propagator_block`. Lo invoca el método `propagate`, cuando lo llama un bloque de origen.|
|[register_filter](#register_filter)|Registra un método de filtro que se invocará en todos los mensajes recibidos.|
|[remove_network_links](#remove_network_links)|Quita todos los vínculos de red de origen y de destino de este objeto `propagator_block`.|
|[send_message](#send_message)|Cuando se reemplaza en una clase derivada, este método pasa sincrónicamente un mensaje de un bloque `ISource` a este objeto `propagator_block`. Lo invoca el método `send`, cuando lo llama un bloque de origen.|
|[unlink_source](#unlink_source)|Desvincula un bloque de origen especificado de este objeto `propagator_block`.|
|[unlink_sources](#unlink_sources)|Desvincula todos los bloques de origen de este objeto `propagator_block`. (Invalida [ITarget:: unlink_sources](itarget-class.md#unlink_sources)).|

## <a name="remarks"></a>Observaciones

Para evitar la herencia múltiple, la clase `propagator_block` hereda de la clase `source_block` y `ITarget` clase abstracta. La mayor parte de la funcionalidad de la clase `target_block` se replica aquí.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

`propagator_block`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="decline_incoming_messages"></a>decline_incoming_messages

Indica al bloque que se deben rechazar los mensajes nuevos.

```cpp
void decline_incoming_messages();
```

### <a name="remarks"></a>Observaciones

El destructor llama a este método para asegurarse de que se rechazan los nuevos mensajes mientras la destrucción está en curso.

## <a name="initialize_source_and_target"></a>initialize_source_and_target

Inicializa el objeto base. En concreto, es necesario inicializar el objeto de `message_processor`.

```cpp
void initialize_source_and_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Parámetros

*_PScheduler*<br/>
Programador que se va a usar para programar tareas.

*_PScheduleGroup*<br/>
Grupo de programación que se va a usar para programar tareas.

## <a name="link_source"></a>link_source

Vincula un bloque de origen especificado a este objeto `propagator_block`.

```cpp
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parámetros

*_PSource*<br/>
Puntero al bloque de `ISource` que se va a vincular.

## <a name="process_input_messages"></a>process_input_messages

Procesar los mensajes de entrada. Esto solo es útil para los bloques de propagación, que derivan de source_block

```cpp
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Puntero al mensaje que se va a procesar.

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

Un bloque de origen vinculado invoca el método `propagate` en un bloque de destino. Pone en cola una tarea asincrónica para controlar el mensaje, si todavía no hay ninguna en la cola o en ejecución.

El método produce una excepción de [invalid_argument](../../../standard-library/invalid-argument-class.md) si se `NULL`el parámetro `_PMessage` o `_PSource`.

## <a name="propagate_message"></a>propagate_message

Cuando se reemplaza en una clase derivada, este método pasa de forma asincrónica un mensaje de un bloque `ISource` a este objeto `propagator_block`. Lo invoca el método `propagate`, cuando lo llama un bloque de origen.

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

## <a name="ctor"></a>propagator_block

Construye un objeto `propagator_block`.

```cpp
propagator_block();
```

## <a name="dtor"></a>~ propagator_block

Destruye un objeto `propagator_block`.

```cpp
virtual ~propagator_block();
```

## <a name="register_filter"></a>register_filter

Registra un método de filtro que se invocará en todos los mensajes recibidos.

```cpp
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>Parámetros

*_Filter*<br/>
Método de filtro.

## <a name="remove_network_links"></a>remove_network_links

Quita todos los vínculos de red de origen y de destino de este objeto `propagator_block`.

```cpp
void remove_network_links();
```

## <a name="send"></a>Enviar

Inicia sincrónicamente un mensaje en este bloque. Lo llama un bloque `ISource`. Cuando se complete esta función, el mensaje ya se habrá propagado en el bloque.

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

Este método produce una excepción de [invalid_argument](../../../standard-library/invalid-argument-class.md) si se `NULL`el parámetro `_PMessage` o `_PSource`.

## <a name="send_message"></a>send_message

Cuando se reemplaza en una clase derivada, este método pasa sincrónicamente un mensaje de un bloque `ISource` a este objeto `propagator_block`. Lo invoca el método `send`, cuando lo llama un bloque de origen.

```cpp
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>Valor devuelto

[Message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.

### <a name="remarks"></a>Observaciones

De forma predeterminada, este bloque devuelve `declined` a menos que se invalide por una clase derivada.

## <a name="unlink_source"></a>unlink_source

Desvincula un bloque de origen especificado de este objeto `propagator_block`.

```cpp
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parámetros

*_PSource*<br/>
Puntero al bloque de `ISource` que se va a desvincular.

## <a name="unlink_sources"></a>unlink_sources

Desvincula todos los bloques de origen de este objeto `propagator_block`.

```cpp
virtual void unlink_sources();
```

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[source_block (clase)](source-block-class.md)<br/>
[ITarget (clase)](itarget-class.md)
