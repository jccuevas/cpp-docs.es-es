---
title: call (clase)
ms.date: 11/04/2016
f1_keywords:
- call
- AGENTS/concurrency::call
- AGENTS/concurrency::call::call
- AGENTS/concurrency::call::process_input_messages
- AGENTS/concurrency::call::process_message
- AGENTS/concurrency::call::propagate_message
- AGENTS/concurrency::call::send_message
- AGENTS/concurrency::call::supports_anonymous_source
helpviewer_keywords:
- call class
ms.assetid: 1521970a-1e9c-4b0c-a681-d18e40976f49
ms.openlocfilehash: 445e368ced9d9c8faf30351ecaeecc4e1b8a59f2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142836"
---
# <a name="call-class"></a>call (clase)

Un bloque de mensajería `call` es un `target_block` con varios orígenes y ordenado, que invoca una función especificada al recibir un mensaje.

## <a name="syntax"></a>Sintaxis

```cpp
template<class T, class _FunctorType = std::function<void(T const&)>>
class call : public target_block<multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de carga de los mensajes propagados a este bloque.

*_FunctorType*<br/>
Firma de las funciones que este bloque puede aceptar.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[llama](#ctor)|Sobrecargado. Construye un bloque de mensajería `call` .|
|[~ Call (destructor)](#dtor)|Destruye el bloque de mensajería `call`.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[process_input_messages](#process_input_messages)|Ejecuta la función de llamada en los mensajes de entrada.|
|[process_message](#process_message)|Procesa un mensaje aceptado por este `call` bloque de mensajería.|
|[propagate_message](#propagate_message)|Pasa asincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `call`. Lo invoca el método `propagate`, cuando lo llama un bloque de origen.|
|[send_message](#send_message)|Pasa sincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `call`. Lo invoca el método `send`, cuando lo llama un bloque de origen.|
|[supports_anonymous_source](#supports_anonymous_source)|Invalida el método `supports_anonymous_source` para indicar que este bloque puede aceptar los mensajes que le ofrece un origen que no está vinculado. (Invalida [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source)).|

## <a name="remarks"></a>Observaciones

Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[ITarget](itarget-class.md)

[target_block](target-block-class.md)

`call`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="ctor"></a>llama

Construye un bloque de mensajería `call` .

```cpp
call(
    _Call_method const& _Func);

call(
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Parámetros

*_Func*<br/>
Función que se invocará para cada mensaje aceptado.

*_Filter*<br/>
Función de filtro que determina si se deben aceptar los mensajes ofrecidos.

*_PScheduler*<br/>
El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `call` .

*_PScheduleGroup*<br/>
El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `call` . El objeto `Scheduler` utilizado está implícito en el grupo de programación.

### <a name="remarks"></a>Observaciones

El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PScheduleGroup` .

El tipo `_Call_method` es un functor con `void (T const &)` de firma invocado por este `call` bloque de mensajería para procesar un mensaje.

El tipo `filter_method` es un functor con `bool (T const &)` de firma invocado por este bloque de mensajería de `call` para determinar si debe aceptar o no un mensaje ofrecido.

## <a name="dtor"></a>~ Call

Destruye el bloque de mensajería `call`.

```cpp
~call();
```

## <a name="process_input_messages"></a>process_input_messages

Ejecuta la función de llamada en los mensajes de entrada.

```cpp
virtual void process_input_messages(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Puntero al mensaje que se va a controlar.

## <a name="process_message"></a>process_message

Procesa un mensaje aceptado por este `call` bloque de mensajería.

```cpp
virtual void process_message(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Puntero al mensaje que se va a controlar.

## <a name="propagate_message"></a>propagate_message

Pasa asincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `call`. Lo invoca el método `propagate`, cuando lo llama un bloque de origen.

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

## <a name="send_message"></a>send_message

Pasa sincrónicamente un mensaje de un bloque `ISource` a este bloque de mensajería `call`. Lo invoca el método `send`, cuando lo llama un bloque de origen.

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

## <a name="supports_anonymous_source"></a>supports_anonymous_source

Invalida el método `supports_anonymous_source` para indicar que este bloque puede aceptar los mensajes que le ofrece un origen que no está vinculado.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Valor devuelto

**true** porque el bloque no pospone los mensajes ofrecidos.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[transformer (clase)](transformer-class.md)
