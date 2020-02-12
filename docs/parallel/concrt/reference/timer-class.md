---
title: timer (clase)
ms.date: 11/04/2016
f1_keywords:
- timer
- AGENTS/concurrency::timer
- AGENTS/concurrency::timer::timer
- AGENTS/concurrency::timer::pause
- AGENTS/concurrency::timer::start
- AGENTS/concurrency::timer::stop
- AGENTS/concurrency::timer::accept_message
- AGENTS/concurrency::timer::consume_message
- AGENTS/concurrency::timer::link_target_notification
- AGENTS/concurrency::timer::propagate_to_any_targets
- AGENTS/concurrency::timer::release_message
- AGENTS/concurrency::timer::reserve_message
- AGENTS/concurrency::timer::resume_propagation
helpviewer_keywords:
- timer class
ms.assetid: 4f4dea51-de9f-40f9-93f5-dd724c567b49
ms.openlocfilehash: c39afc565a7ec775600b9c9fb6f15a89acdef57b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142526"
---
# <a name="timer-class"></a>timer (clase)

Un bloque de mensajería `timer` es un bloque `source_block` con destino único, capaz de enviar un mensaje a su destino cuando un período de tiempo especificado ha transcurrido o en intervalos concretos.

## <a name="syntax"></a>Sintaxis

```cpp
template<class T>
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<T>>>;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de carga de los mensajes de salida de este bloque.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[temporizador](#ctor)|Sobrecargado. Construye un bloque de mensajería `timer` que activará un mensaje determinado después de un intervalo especificado.|
|[~ Timer (destructor)](#dtor)|Destruye un bloque de mensajería `timer`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[temporalmente](#pause)|Detiene el `timer` bloque de mensajería. Si se trata de un bloque de mensajería de `timer` repetido, puede reiniciarse con una llamada a `start()` posterior. En el caso de los temporizadores que no son de repetición, esto tiene el mismo efecto que una llamada `stop`.|
|[start](#start)|Inicia el bloque de mensajería `timer`. El número especificado de milisegundos después de que se llame a este método, el valor especificado se propagará hacia abajo como `message`.|
|[stop](#stop)|Detiene el `timer` bloque de mensajería.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[accept_message](#accept_message)|Acepta un mensaje ofrecido por este `timer` bloque de mensajería, transfiriendo la propiedad al autor de la llamada.|
|[consume_message](#consume_message)|Consume un mensaje ofrecido anteriormente por el `timer` y reservado por el destino, transfiriendo la propiedad al autor de la llamada.|
|[link_target_notification](#link_target_notification)|Una devolución de llamada que notifica que un nuevo destino se ha vinculado a este `timer` bloque de mensajería.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Intenta ofrecer el mensaje generado por el bloque `timer` a todos los destinos vinculados.|
|[release_message](#release_message)|Libera una reserva de mensaje anterior. (Invalida [source_block:: release_message](source-block-class.md#release_message)).|
|[reserve_message](#reserve_message)|Reserva un mensaje ofrecido anteriormente por este `timer` bloque de mensajería. (Invalida [source_block:: reserve_message](source-block-class.md#reserve_message)).|
|[resume_propagation](#resume_propagation)|Reanuda la propagación una vez que se ha liberado una reserva. (Invalida [source_block:: resume_propagation](source-block-class.md#resume_propagation)).|

## <a name="remarks"></a>Observaciones

Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[ISource](isource-class.md)

[source_block](source-block-class.md)

`timer`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="accept_message"></a>accept_message

Acepta un mensaje ofrecido por este `timer` bloque de mensajería, transfiriendo la propiedad al autor de la llamada.

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto `message` proporcionado.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de `message` al que el llamador tiene ahora propiedad.

## <a name="consume_message"></a>consume_message

Consume un mensaje ofrecido anteriormente por el `timer` y reservado por el destino, transfiriendo la propiedad al autor de la llamada.

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

## <a name="link_target_notification"></a>link_target_notification

Una devolución de llamada que notifica que un nuevo destino se ha vinculado a este `timer` bloque de mensajería.

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Puntero al destino recién vinculado.

## <a name="pause"></a>temporalmente

Detiene el `timer` bloque de mensajería. Si se trata de un bloque de mensajería de `timer` repetido, puede reiniciarse con una llamada a `start()` posterior. En el caso de los temporizadores que no son de repetición, esto tiene el mismo efecto que una llamada `stop`.

```cpp
void pause();
```

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

Intenta ofrecer el mensaje generado por el bloque `timer` a todos los destinos vinculados.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
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

Reserva un mensaje ofrecido anteriormente por este `timer` bloque de mensajería.

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

## <a name="start"></a>iniciales

Inicia el bloque de mensajería `timer`. El número especificado de milisegundos después de que se llame a este método, el valor especificado se propagará hacia abajo como `message`.

```cpp
void start();
```

## <a name="stop"></a>detener

Detiene el `timer` bloque de mensajería.

```cpp
void stop();
```

## <a name="ctor"></a>temporizador

Construye un bloque de mensajería `timer` que activará un mensaje determinado después de un intervalo especificado.

```cpp
timer(
    unsigned int _Ms,
    T const& value,
    ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    Scheduler& _Scheduler,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    ScheduleGroup& _ScheduleGroup,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);
```

### <a name="parameters"></a>Parámetros

*_Ms*<br/>
Número de milisegundos que deben transcurrir después de la llamada a Start para que el mensaje especificado se propague hacia abajo.

*value*<br/>
Valor que se propagará hacia abajo cuando transcurra el temporizador.

*_PTarget*<br/>
Destino en el que el temporizador propagará su mensaje.

*_Repeating*<br/>
Si es true, indica que el temporizador se activará periódicamente cada `_Ms` milisegundos.

*_Scheduler*<br/>
Está programado el objeto de `Scheduler` en el que está programada la tarea de propagación para el bloque de mensajería `timer`.

*_ScheduleGroup*<br/>
El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `timer` . El objeto `Scheduler` utilizado está implícito en el grupo de programación.

### <a name="remarks"></a>Observaciones

El runtime usa el programador predeterminado si no se especifican los parámetros `_Scheduler` o `_ScheduleGroup` .

## <a name="dtor"></a>~ temporizador

Destruye un bloque de mensajería `timer`.

```cpp
~timer();
```

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
