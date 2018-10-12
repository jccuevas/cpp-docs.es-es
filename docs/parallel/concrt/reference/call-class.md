---
title: Call (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- call
- AGENTS/concurrency::call
- AGENTS/concurrency::call::call
- AGENTS/concurrency::call::process_input_messages
- AGENTS/concurrency::call::process_message
- AGENTS/concurrency::call::propagate_message
- AGENTS/concurrency::call::send_message
- AGENTS/concurrency::call::supports_anonymous_source
dev_langs:
- C++
helpviewer_keywords:
- call class
ms.assetid: 1521970a-1e9c-4b0c-a681-d18e40976f49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0a99de307ec64c3b6d4e49f4e0a6eef532314bf9
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161871"
---
# <a name="call-class"></a>Clase call

Un bloque de mensajería `call` es un `target_block` con varios orígenes y ordenado, que invoca una función especificada al recibir un mensaje.

## <a name="syntax"></a>Sintaxis

```
template<class T, class _FunctorType = std::function<void(T const&)>>
class call : public target_block<multi_link_registry<ISource<T>>>;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de carga de los mensajes se propaga a este bloque.

*_FunctorType*<br/>
La firma de funciones que este bloque puede aceptar.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[Llamar a](#ctor)|Sobrecargado. Construye un bloque de mensajería `call` .|
|[~ Llame al Destructor](#dtor)|Destruye el `call` bloque de mensajería.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[process_input_messages](#process_input_messages)|Ejecuta la función de llamada en los mensajes de entrada.|
|[process_message](#process_message)|Procesa un mensaje que se aceptó vieron `call` bloque de mensajería.|
|[propagate_message](#propagate_message)|Pasa de forma asincrónica un mensaje desde un `ISource` bloque a este `call` bloque de mensajería. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.|
|[send_message](#send_message)|Un mensaje de forma sincrónica, pasa un `ISource` bloque a este `call` bloque de mensajería. Se invoca con el `send` método, cuando se llama a un bloque de origen.|
|[supports_anonymous_source](#supports_anonymous_source)|Invalida el `supports_anonymous_source` método para indicar que este bloque puede aceptar mensajes ofrecidos por un origen que no está vinculado. (Invalida [ITarget](itarget-class.md#supports_anonymous_source).)|

## <a name="remarks"></a>Comentarios

Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[ITarget](itarget-class.md)

[target_block](target-block-class.md)

`call`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

##  <a name="ctor"></a> Llamar a

Construye un bloque de mensajería `call` .

```
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
Una función que se invocará para cada mensaje aceptado.

*_Filtrar*<br/>
Una función de filtro que determina si se deben aceptar mensajes ofrecidos.

*_PScheduler*<br/>
El objeto `Scheduler` dentro del que se programa la tarea de propagación para el bloque de mensajería `call` .

*_PScheduleGroup*<br/>
El objeto `ScheduleGroup` dentro del que se programa la tarea de propagación para el bloque de mensajería `call` . El objeto `Scheduler` utilizado está implícito en el grupo de programación.

### <a name="remarks"></a>Comentarios

El runtime usa el programador predeterminado si no se especifican los parámetros `_PScheduler` o `_PScheduleGroup` .

El tipo `_Call_method` es un functor con firma `void (T const &)` que es invocado por este `call` bloque de mensajería para procesar un mensaje.

El tipo `filter_method` es un functor con firma `bool (T const &)` que es invocado por este `call` bloque de mensajería para determinar si debe aceptar un mensaje proporcionado.

##  <a name="dtor"></a> ~ llamar

Destruye el `call` bloque de mensajería.

```
~call();
```

##  <a name="process_input_messages"></a> process_input_messages

Ejecuta la función de llamada en los mensajes de entrada.

```
virtual void process_input_messages(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parámetros

*Parámetro _PMessage*<br/>
Un puntero para el mensaje que debe controlarse.

##  <a name="process_message"></a> process_message

Procesa un mensaje que se aceptó vieron `call` bloque de mensajería.

```
virtual void process_message(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parámetros

*Parámetro _PMessage*<br/>
Un puntero para el mensaje que debe controlarse.

##  <a name="propagate_message"></a> propagate_message

Pasa de forma asincrónica un mensaje desde un `ISource` bloque a este `call` bloque de mensajería. Se invoca con el `propagate` método, cuando se llama a un bloque de origen.

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

##  <a name="send_message"></a> send_message

Un mensaje de forma sincrónica, pasa un `ISource` bloque a este `call` bloque de mensajería. Se invoca con el `send` método, cuando se llama a un bloque de origen.

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

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[transformer (clase)](transformer-class.md)
