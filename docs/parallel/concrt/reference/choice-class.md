---
title: choice (clase)
ms.date: 11/04/2016
f1_keywords:
- choice
- AGENTS/concurrency::choice
- AGENTS/concurrency::choice::choice
- AGENTS/concurrency::choice::accept
- AGENTS/concurrency::choice::acquire_ref
- AGENTS/concurrency::choice::consume
- AGENTS/concurrency::choice::has_value
- AGENTS/concurrency::choice::index
- AGENTS/concurrency::choice::link_target
- AGENTS/concurrency::choice::release
- AGENTS/concurrency::choice::release_ref
- AGENTS/concurrency::choice::reserve
- AGENTS/concurrency::choice::unlink_target
- AGENTS/concurrency::choice::unlink_targets
- AGENTS/concurrency::choice::value
helpviewer_keywords:
- choice class
ms.assetid: 4157a539-d5c2-4161-b1ab-536ce2888397
ms.openlocfilehash: 3e718d0d34580d3bf2f13937159e431134631218
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142213"
---
# <a name="choice-class"></a>choice (clase)

Un bloque de mensajería `choice` es un bloque de varios orígenes y de destino único que representa una interacción del flujo de control con un conjunto de orígenes. El bloque de elección esperará a cualquiera de los orígenes para generar un mensaje y propagará el índice del origen que generó el mensaje.

## <a name="syntax"></a>Sintaxis

```cpp
template<
    class T
>
class choice: public ISource<size_t>;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo basado en `tuple`que representa las cargas de los orígenes de entrada.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`type`|Un alias de tipo para `T`.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[alternativa](#ctor)|Sobrecargado. Construye un bloque de mensajería `choice` .|
|[~ Choice (destructor)](#dtor)|Destruye el bloque de mensajería `choice`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[acept](#accept)|Acepta un mensaje ofrecido por este `choice` bloque, transfiriendo la propiedad al autor de la llamada.|
|[acquire_ref](#acquire_ref)|Adquiere un recuento de referencias en este `choice` bloque de mensajería para evitar la eliminación.|
|[consumo](#consume)|Consume un mensaje ofrecido anteriormente por este `choice` bloque de mensajería y reservado correctamente por el destino, transfiriendo la propiedad al autor de la llamada.|
|[has_value](#has_value)|Comprueba si esta `choice` bloque de mensajería se ha inicializado con un valor todavía.|
|[índice](#index)|Devuelve un índice en el `tuple` que representa el elemento seleccionado por el bloque de mensajería `choice`.|
|[link_target](#link_target)|Vincula un bloque de destino a este bloque de mensajería `choice`.|
|[release](#release)|Libera una reserva de mensajes correcta anterior.|
|[release_ref](#release_ref)|Libera un recuento de referencias en este `choice` bloque de mensajería.|
|[reserve](#reserve)|Reserva un mensaje ofrecido anteriormente por este `choice` bloque de mensajería.|
|[unlink_target](#unlink_target)|Desvincula un bloque de destino de este bloque de mensajería `choice`.|
|[unlink_targets](#unlink_targets)|Desvincula todos los destinos de este bloque de mensajería de `choice`. (Invalida [ISource:: unlink_targets](isource-class.md#unlink_targets)).|
|[value](#value)|Obtiene el mensaje cuyo índice fue seleccionado por el bloque de mensajería `choice`.|

## <a name="remarks"></a>Observaciones

El bloque Choice garantiza que solo se consume uno de los mensajes entrantes.

Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[ISource](isource-class.md)

`choice`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="accept"></a>acept

Acepta un mensaje ofrecido por este `choice` bloque, transfiriendo la propiedad al autor de la llamada.

```cpp
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto `message` proporcionado.

*_PTarget*<br/>
Puntero al bloque de destino que llama al método de `accept`.

### <a name="return-value"></a>Valor devuelto

Un puntero al mensaje del que el llamador tiene ahora propiedad.

## <a name="acquire_ref"></a>acquire_ref

Adquiere un recuento de referencias en este `choice` bloque de mensajería para evitar la eliminación.

```cpp
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Puntero al bloque de destino que llama a este método.

### <a name="remarks"></a>Observaciones

Un objeto `ITarget` que se vincula a este origen llama a este método durante el método `link_target`.

## <a name="ctor"></a>alternativa

Construye un bloque de mensajería `choice` .

```cpp
explicit choice(
    T _Tuple);

choice(
    Scheduler& _PScheduler,
    T _Tuple);

choice(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

choice(
    choice&& _Choice);
```

### <a name="parameters"></a>Parámetros

*_Tuple*<br/>
`tuple` de orígenes para choice.

*_PScheduler*<br/>
El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `choice` .

*_PScheduleGroup*<br/>
El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `choice` . El objeto `Scheduler` utilizado está implícito en el grupo de programación.

*_Choice*<br/>
Bloque de mensajería `choice` desde el que se realizará la copia. Tenga en cuenta que el objeto original es huérfano, por lo que este constructor pasa a ser de movimiento.

### <a name="remarks"></a>Observaciones

El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PScheduleGroup` .

La construcción de movimiento no se lleva acabo con un bloqueo, lo que significa que el usuario debe asegurarse de que no hay ninguna tarea ligera en marcha en el momento del movimiento. De lo contrario, se pueden producir numerosas carreras, que darán lugar a excepciones o a un estado incoherente.

## <a name="dtor"></a>~ elección

Destruye el bloque de mensajería `choice`.

```cpp
~choice();
```

## <a name="consume"></a>emplear

Consume un mensaje ofrecido anteriormente por este `choice` bloque de mensajería y reservado correctamente por el destino, transfiriendo la propiedad al autor de la llamada.

```cpp
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` reservado.

*_PTarget*<br/>
Puntero al bloque de destino que llama al método de `consume`.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de `message` al que el llamador tiene ahora propiedad.

### <a name="remarks"></a>Observaciones

El método `consume` es similar a `accept`, pero siempre debe ir precedido de una llamada a `reserve` que devolvió **true**.

## <a name="has_value"></a>has_value

Comprueba si esta `choice` bloque de mensajería se ha inicializado con un valor todavía.

```cpp
bool has_value() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si el bloque ha recibido un valor; de lo contrario, **false** .

## <a name="index"></a>ajustar

Devuelve un índice en el `tuple` que representa el elemento seleccionado por el bloque de mensajería `choice`.

```cpp
size_t index();
```

### <a name="return-value"></a>Valor devuelto

Índice del mensaje.

### <a name="remarks"></a>Observaciones

La carga del mensaje se puede extraer con el método `get`.

## <a name="link_target"></a>link_target

Vincula un bloque de destino a este bloque de mensajería `choice`.

```cpp
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Puntero a un bloque de `ITarget` que se va a vincular a este bloque de mensajería `choice`.

## <a name="release"></a>emisión

Libera una reserva de mensajes correcta anterior.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` que se va a liberar.

*_PTarget*<br/>
Puntero al bloque de destino que llama al método de `release`.

## <a name="release_ref"></a>release_ref

Libera un recuento de referencias en este `choice` bloque de mensajería.

```cpp
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Puntero al bloque de destino que llama a este método.

### <a name="remarks"></a>Observaciones

Un objeto `ITarget` al que se va a desvincular de este origen llama a este método. El bloque de origen puede liberar los recursos reservados para el bloque de destino.

## <a name="reserve"></a>realizan

Reserva un mensaje ofrecido anteriormente por este `choice` bloque de mensajería.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` que se va a reservar.

*_PTarget*<br/>
Puntero al bloque de destino que llama al método de `reserve`.

### <a name="return-value"></a>Valor devuelto

**true** si el mensaje se ha reservado correctamente; de lo contrario, **false** . Se puede producir un error en las reservas por muchas razones, como: el mensaje ya estaba reservado o lo aceptó otro destino, el origen podría denegar reservas, etc.

### <a name="remarks"></a>Observaciones

Después de llamar a `reserve`, si se realiza correctamente, debe llamar a `consume` o `release` para poder llevar a cabo o renunciar al mensaje, respectivamente.

## <a name="unlink_target"></a>unlink_target

Desvincula un bloque de destino de este bloque de mensajería `choice`.

```cpp
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Un puntero a un bloque `ITarget` para desvincular de este bloque de mensajería `choice`.

## <a name="unlink_targets"></a>unlink_targets

Desvincula todos los destinos de este bloque de mensajería de `choice`.

```cpp
virtual void unlink_targets();
```

### <a name="remarks"></a>Observaciones

No es necesario llamar a este método desde el destructor porque el destructor del bloque `single_assignment` interno se desvinculará correctamente.

## <a name="value"></a>valor

Obtiene el mensaje cuyo índice fue seleccionado por el bloque de mensajería `choice`.

```cpp
template <
    typename _Payload_type
>
_Payload_type const& value();
```

### <a name="parameters"></a>Parámetros

*_Payload_type*<br/>
El tipo de la carga del mensaje.

### <a name="return-value"></a>Valor devuelto

La carga del mensaje.

### <a name="remarks"></a>Observaciones

Dado que un bloque de mensajería de `choice` puede tomar entradas con distintos tipos de carga, debe especificar el tipo de la carga en el punto de recuperación. Puede determinar el tipo basado en el resultado del método `index`.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[join (clase)](join-class.md)<br/>
[single_assignment (clase)](single-assignment-class.md)
