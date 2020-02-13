---
title: ordered_message_processor (clase)
ms.date: 11/04/2016
f1_keywords:
- ordered_message_processor
- AGENTS/concurrency::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::async_send
- AGENTS/concurrency::ordered_message_processor::initialize
- AGENTS/concurrency::ordered_message_processor::initialize_batched_processing
- AGENTS/concurrency::ordered_message_processor::sync_send
- AGENTS/concurrency::ordered_message_processor::wait
- AGENTS/concurrency::ordered_message_processor::process_incoming_message
helpviewer_keywords:
- ordered_message_processor class
ms.assetid: 787adfb7-7f79-4a70-864a-80e3b64088cd
ms.openlocfilehash: ea9ca799f36cac0d843a578eb7cef9c1e9c5cda6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138783"
---
# <a name="ordered_message_processor-class"></a>ordered_message_processor (clase)

Un `ordered_message_processor` es un `message_processor` que permite a los bloques de mensaje procesar los mensajes en el orden que se recibieron.

## <a name="syntax"></a>Sintaxis

```cpp
template<class T>
class ordered_message_processor : public message_processor<T>;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de carga de los mensajes administrados por el procesador.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`type`|Un alias de tipo para `T`.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[ordered_message_processor](#ctor)|Construye un objeto `ordered_message_processor`.|
|[~ ordered_message_processor destructor](#dtor)|Destruye el objeto `ordered_message_processor`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[async_send](#async_send)|Pone en cola asincrónicamente los mensajes e inicia una tarea de procesamiento, si aún no se ha hecho. (Invalida [message_processor:: async_send](message-processor-class.md#async_send)).|
|[inicia](#initialize)|Inicializa el objeto `ordered_message_processor` con la función de devolución de llamada, el programador y el grupo de programación adecuados.|
|[initialize_batched_processing](#initialize_batched_processing)|Inicializar el procesamiento de mensajes por lotes|
|[sync_send](#sync_send)|Pone en cola los mensajes de forma sincrónica e inicia una tarea de procesamiento, si aún no se ha hecho. (Invalida [message_processor:: sync_send](message-processor-class.md#sync_send)).|
|[currir](#wait)|Una espera de giro específica del procesador utilizada en destructores de bloques de mensajes para asegurarse de que todas las tareas de procesamiento asincrónico tienen tiempo de finalización antes de destruir el bloque. (Invalida [message_processor:: wait](message-processor-class.md#wait)).|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|Función de procesamiento a la que se llama de forma asincrónica. Elimina los mensajes de la cola y comienza a procesarlos. (Invalida [message_processor: rocess_incoming_message:p](message-processor-class.md#process_incoming_message)).|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[message_processor](message-processor-class.md)

`ordered_message_processor`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="async_send"></a>async_send

Pone en cola asincrónicamente los mensajes e inicia una tarea de procesamiento, si aún no se ha hecho.

```cpp
virtual void async_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>Parámetros

*_Msg*<br/>
Un puntero a un mensaje.

## <a name="initialize"></a>inicia

Inicializa el objeto `ordered_message_processor` con la función de devolución de llamada, el programador y el grupo de programación adecuados.

```cpp
void initialize(
    _Inout_opt_ Scheduler* _PScheduler,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup,
    _Handler_method const& _Handler);
```

### <a name="parameters"></a>Parámetros

*_PScheduler*<br/>
Puntero al programador que se va a usar para programar tareas ligeras.

*_PScheduleGroup*<br/>
Un puntero al grupo de programación que se va a usar para programar tareas ligeras.

*_Handler*<br/>
Se invocó el functor del controlador durante la devolución de llamada.

## <a name="initialize_batched_processing"></a>initialize_batched_processing

Inicializar el procesamiento de mensajes por lotes

```cpp
virtual void initialize_batched_processing(
    _Handler_method const& _Processor,
    _Propagator_method const& _Propagator);
```

### <a name="parameters"></a>Parámetros

*_Processor*<br/>
El procesador funcr invocación durante la devolución de llamada.

*_Propagator*<br/>
El funcdor del propagador invocó durante la devolución de llamada.

## <a name="ctor"></a>ordered_message_processor

Construye un objeto `ordered_message_processor`.

```cpp
ordered_message_processor();
```

### <a name="remarks"></a>Observaciones

Esta `ordered_message_processor` no programará controladores asincrónicos o sincrónicos hasta que se llame a la función `initialize`.

## <a name="dtor"></a>~ ordered_message_processor

Destruye el objeto `ordered_message_processor`.

```cpp
virtual ~ordered_message_processor();
```

### <a name="remarks"></a>Observaciones

Espera todas las operaciones asincrónicas pendientes antes de destruir el procesador.

## <a name="process_incoming_message"></a>process_incoming_message

Función de procesamiento a la que se llama de forma asincrónica. Elimina los mensajes de la cola y comienza a procesarlos.

```cpp
virtual void process_incoming_message();
```

## <a name="sync_send"></a>sync_send

Pone en cola los mensajes de forma sincrónica e inicia una tarea de procesamiento, si aún no se ha hecho.

```cpp
virtual void sync_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>Parámetros

*_Msg*<br/>
Un puntero a un mensaje.

## <a name="wait"></a>currir

Una espera de giro específica del procesador utilizada en destructores de bloques de mensajes para asegurarse de que todas las tareas de procesamiento asincrónico tienen tiempo de finalización antes de destruir el bloque.

```cpp
virtual void wait();
```

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
