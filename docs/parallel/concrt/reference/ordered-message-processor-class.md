---
title: ordered_message_processor (Clase)
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
ms.openlocfilehash: b88544f399031a5f770fa39aa1f3300306158511
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394434"
---
# <a name="orderedmessageprocessor-class"></a>ordered_message_processor (Clase)

Un `ordered_message_processor` es un `message_processor` que permite a los bloques de mensaje procesar los mensajes en el orden que se recibieron.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class ordered_message_processor : public message_processor<T>;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de carga de mensajes controlados por el procesador.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`type`|Un alias de tipo para `T`.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[ordered_message_processor](#ctor)|Construye un objeto `ordered_message_processor`.|
|[~ ordered_message_processor (destructor)](#dtor)|Destruye el objeto `ordered_message_processor`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[async_send](#async_send)|Pone en cola los mensajes de forma asincrónica y se inicia una tarea de procesamiento, si esto no se ha hecho ya. (Invalida [message_processor:: async_send](message-processor-class.md#async_send).)|
|[initialize](#initialize)|Inicializa el `ordered_message_processor` objeto con el grupo de programación, el programador y la función de devolución de llamada apropiados.|
|[initialize_batched_processing](#initialize_batched_processing)|Inicializar el procesamiento de mensajes por lotes|
|[sync_send](#sync_send)|Sincrónicamente pone en cola los mensajes e inicia una tarea de procesamiento, si esto no se ha hecho ya. (Invalida [message_processor:: sync_send](message-processor-class.md#sync_send).)|
|[wait](#wait)|Una espera de vuelta específica del procesador usada en destructores de bloques de mensajes para asegurarse de que todas las tareas de procesamiento asincrónico tienen tiempo para finalizar antes de destruir el bloque. (Invalida [message_processor:: wait](message-processor-class.md#wait).)|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|La función de procesamiento que se llama de forma asincrónica. Quita los mensajes de la cola y empieza a procesarlos. (Invalida [message_processor:: process_incoming_message](message-processor-class.md#process_incoming_message).)|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[message_processor](message-processor-class.md)

`ordered_message_processor`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

##  <a name="async_send"></a> async_send

Pone en cola los mensajes de forma asincrónica y se inicia una tarea de procesamiento, si esto no se ha hecho ya.

```
virtual void async_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>Parámetros

*_Msg*<br/>
Un puntero a un mensaje.

##  <a name="initialize"></a> inicializar

Inicializa el `ordered_message_processor` objeto con el grupo de programación, el programador y la función de devolución de llamada apropiados.

```
void initialize(
    _Inout_opt_ Scheduler* _PScheduler,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup,
    _Handler_method const& _Handler);
```

### <a name="parameters"></a>Parámetros

*_PScheduler*<br/>
Un puntero al programador que se usará para programar las tareas ligeras.

*_PScheduleGroup*<br/>
Un puntero al grupo de programación que se usará para programar las tareas ligeras.

*_Handler*<br/>
El functor de controlador que se invoca durante la devolución de llamada.

##  <a name="initialize_batched_processing"></a> initialize_batched_processing

Inicializar el procesamiento de mensajes por lotes

```
virtual void initialize_batched_processing(
    _Handler_method const& _Processor,
    _Propagator_method const& _Propagator);
```

### <a name="parameters"></a>Parámetros

*_Processor*<br/>
El functor de procesador que se invoca durante la devolución de llamada.

*_Propagator*<br/>
El functor propagador invocado durante la devolución de llamada.

##  <a name="ctor"></a> ordered_message_processor)

Construye un objeto `ordered_message_processor`.

```
ordered_message_processor();
```

### <a name="remarks"></a>Comentarios

Esto `ordered_message_processor` no programará controladores sincrónicos o asincrónicos hasta el `initialize` se llama a la función.

##  <a name="dtor"></a> ~ordered_message_processor

Destruye el objeto `ordered_message_processor`.

```
virtual ~ordered_message_processor();
```

### <a name="remarks"></a>Comentarios

Espera a que todas las operaciones asincrónicas pendientes antes de destruir el procesador.

##  <a name="process_incoming_message"></a> process_incoming_message

La función de procesamiento que se llama de forma asincrónica. Quita los mensajes de la cola y empieza a procesarlos.

```
virtual void process_incoming_message();
```

##  <a name="sync_send"></a> sync_send

Sincrónicamente pone en cola los mensajes e inicia una tarea de procesamiento, si esto no se ha hecho ya.

```
virtual void sync_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>Parámetros

*_Msg*<br/>
Un puntero a un mensaje.

##  <a name="wait"></a> Espere

Una espera de vuelta específica del procesador usada en destructores de bloques de mensajes para asegurarse de que todas las tareas de procesamiento asincrónico tienen tiempo para finalizar antes de destruir el bloque.

```
virtual void wait();
```

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
