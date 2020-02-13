---
title: multitype_join (clase)
ms.date: 11/04/2016
f1_keywords:
- multitype_join
- AGENTS/concurrency::multitype_join
- AGENTS/concurrency::multitype_join::multitype_join
- AGENTS/concurrency::multitype_join::accept
- AGENTS/concurrency::multitype_join::acquire_ref
- AGENTS/concurrency::multitype_join::consume
- AGENTS/concurrency::multitype_join::link_target
- AGENTS/concurrency::multitype_join::release
- AGENTS/concurrency::multitype_join::release_ref
- AGENTS/concurrency::multitype_join::reserve
- AGENTS/concurrency::multitype_join::unlink_target
- AGENTS/concurrency::multitype_join::unlink_targets
helpviewer_keywords:
- multitype_join class
ms.assetid: 236e87a0-4867-49fd-869a-bef4010e49a7
ms.openlocfilehash: 4214c43fa0d0ab8fdd29ed54738c19f72a07267a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138953"
---
# <a name="multitype_join-class"></a>multitype_join (clase)

Un bloque de mensajería `multitype_join` es un bloque de mensajería de destino único, de varios orígenes, que combina los mensajes de diferentes tipos de cada uno de sus orígenes y ofrece una tupla de los mensajes combinados con sus destinos.

## <a name="syntax"></a>Sintaxis

```cpp
template<
    typename T,
    join_type _Jtype = non_greedy
>
class multitype_join: public ISource<typename _Unwrap<T>::type>;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
`tuple` tipo de carga de los mensajes combinados y propagados por el bloque.

*_Jtype*<br/>
El tipo de `join` bloque es, ya sea `greedy` o `non_greedy`

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`type`|Un alias de tipo para `T`.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[multitype_join](#ctor)|Sobrecargado. Construye un bloque de mensajería `multitype_join` .|
|[~ multitype_join destructor](#dtor)|Destruye el bloque de mensajería `multitype_join`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[acept](#accept)|Acepta un mensaje ofrecido por este `multitype_join` bloque, transfiriendo la propiedad al autor de la llamada.|
|[acquire_ref](#acquire_ref)|Adquiere un recuento de referencias en este `multitype_join` bloque de mensajería para evitar la eliminación.|
|[consumo](#consume)|Consume un mensaje ofrecido anteriormente por el bloque de mensajería `multitype_join` y que el destino ha reservado correctamente, transfiriendo la propiedad al autor de la llamada.|
|[link_target](#link_target)|Vincula un bloque de destino a este bloque de mensajería `multitype_join`.|
|[release](#release)|Libera una reserva de mensajes correcta anterior.|
|[release_ref](#release_ref)|Libera un recuento de referencias en este `multiple_join` bloque de mensajería.|
|[reserve](#reserve)|Reserva un mensaje ofrecido anteriormente por este `multitype_join` bloque de mensajería.|
|[unlink_target](#unlink_target)|Desvincula un bloque de destino de este bloque de mensajería `multitype_join`.|
|[unlink_targets](#unlink_targets)|Desvincula todos los destinos de este bloque de mensajería de `multitype_join`. (Invalida [ISource:: unlink_targets](isource-class.md#unlink_targets)).|

## <a name="remarks"></a>Observaciones

Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[ISource](isource-class.md)

`multitype_join`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="accept"></a>acept

Acepta un mensaje ofrecido por este `multitype_join` bloque, transfiriendo la propiedad al autor de la llamada.

```cpp
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto `message` proporcionado.

*_PTarget*<br/>
Puntero al bloque de destino que llama al método de `accept`.

### <a name="return-value"></a>Valor devuelto

Un puntero al mensaje del que el llamador tiene ahora propiedad.

## <a name="acquire_ref"></a>acquire_ref

Adquiere un recuento de referencias en este `multitype_join` bloque de mensajería para evitar la eliminación.

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Puntero al bloque de destino que llama a este método.

### <a name="remarks"></a>Observaciones

Un objeto `ITarget` que se vincula a este origen llama a este método durante el método `link_target`.

## <a name="consume"></a>emplear

Consume un mensaje ofrecido anteriormente por el bloque de mensajería `multitype_join` y que el destino ha reservado correctamente, transfiriendo la propiedad al autor de la llamada.

```cpp
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
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

## <a name="link_target"></a>link_target

Vincula un bloque de destino a este bloque de mensajería `multitype_join`.

```cpp
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Puntero a un bloque de `ITarget` que se va a vincular a este bloque de mensajería `multitype_join`.

## <a name="ctor"></a>multitype_join

Construye un bloque de mensajería `multitype_join` .

```cpp
explicit multitype_join(
    T _Tuple);

multitype_join(
    Scheduler& _PScheduler,
    T _Tuple);

multitype_join(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

multitype_join(
    multitype_join&& _Join);
```

### <a name="parameters"></a>Parámetros

*_Tuple*<br/>
`tuple` de orígenes para este bloque de mensajería `multitype_join` .

*_PScheduler*<br/>
El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `multitype_join` .

*_PScheduleGroup*<br/>
El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `multitype_join` . El objeto `Scheduler` utilizado está implícito en el grupo de programación.

*_Join*<br/>
Bloque de mensajería `multitype_join` desde el que se realizará la copia. Tenga en cuenta que el objeto original es huérfano, por lo que este constructor pasa a ser de movimiento.

### <a name="remarks"></a>Observaciones

El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PScheduleGroup` .

La construcción de movimiento no se lleva acabo con un bloqueo, lo que significa que el usuario debe asegurarse de que no hay ninguna tarea ligera en marcha en el momento del movimiento. De lo contrario, se pueden producir numerosas carreras, que darán lugar a excepciones o a un estado incoherente.

## <a name="dtor"></a>~ multitype_join

Destruye el bloque de mensajería `multitype_join`.

```cpp
~multitype_join();
```

## <a name="release"></a>emisión

Libera una reserva de mensajes correcta anterior.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` que se va a liberar.

*_PTarget*<br/>
Puntero al bloque de destino que llama al método de `release`.

## <a name="release_ref"></a>release_ref

Libera un recuento de referencias en este `multiple_join` bloque de mensajería.

```cpp
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Puntero al bloque de destino que llama a este método.

### <a name="remarks"></a>Observaciones

Un objeto `ITarget` al que se va a desvincular de este origen llama a este método. El bloque de origen puede liberar los recursos reservados para el bloque de destino.

## <a name="reserve"></a>realizan

Reserva un mensaje ofrecido anteriormente por este `multitype_join` bloque de mensajería.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` que se va a reservar.

*_PTarget*<br/>
Puntero al bloque de destino que llama al método de `reserve`.

### <a name="return-value"></a>Valor devuelto

`true` si el mensaje se ha reservado correctamente, `false` de lo contrario. Se puede producir un error en las reservas por muchas razones, como: el mensaje ya estaba reservado o lo aceptó otro destino, el origen podría denegar reservas, etc.

### <a name="remarks"></a>Observaciones

Después de llamar a `reserve`, si se realiza correctamente, debe llamar a `consume` o `release` para poder llevar a cabo o renunciar al mensaje, respectivamente.

## <a name="unlink_target"></a>unlink_target

Desvincula un bloque de destino de este bloque de mensajería `multitype_join`.

```cpp
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Un puntero a un bloque `ITarget` para desvincular de este bloque de mensajería `multitype_join`.

## <a name="unlink_targets"></a>unlink_targets

Desvincula todos los destinos de este bloque de mensajería de `multitype_join`.

```cpp
virtual void unlink_targets();
```

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[choice (clase)](choice-class.md)<br/>
[join (clase)](join-class.md)
