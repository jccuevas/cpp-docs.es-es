---
title: message_processor (clase)
ms.date: 11/04/2016
f1_keywords:
- message_processor
- AGENTS/concurrency::message_processor
- AGENTS/concurrency::message_processor::async_send
- AGENTS/concurrency::message_processor::sync_send
- AGENTS/concurrency::message_processor::wait
- AGENTS/concurrency::message_processor::process_incoming_message
helpviewer_keywords:
- message_processor class
ms.assetid: 23afb052-daa7-44ed-bf24-d2513db748da
ms.openlocfilehash: 88944b2d935eebd0e031be1431c2a0f4efa3d760
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139470"
---
# <a name="message_processor-class"></a>message_processor (clase)

La clase `message_processor` es la clase base abstracta del procesamiento de objetos `message`. No hay ninguna garantía en la clasificación de los mensajes.

## <a name="syntax"></a>Sintaxis

```cpp
template<class T>
class message_processor;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos de la carga en los mensajes administrados por este objeto `message_processor`.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`type`|Un alias de tipo para `T`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[async_send](#async_send)|Cuando se reemplaza en una clase derivada, coloca los mensajes en el bloque de forma asincrónica.|
|[sync_send](#sync_send)|Cuando se reemplaza en una clase derivada, coloca los mensajes en el bloque de forma sincrónica.|
|[currir](#wait)|Cuando se reemplaza en una clase derivada, espera a que se completen todas las operaciones asincrónicas.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|Cuando se reemplaza en una clase derivada, realiza el procesamiento hacia delante de los mensajes en el bloque. Se le llama una vez cada vez que se agrega un nuevo mensaje y se detecta que la cola está vacía.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`message_processor`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="async_send"></a>async_send

Cuando se reemplaza en una clase derivada, coloca los mensajes en el bloque de forma asincrónica.

```cpp
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>Parámetros

*_Msg*<br/>
Objeto `message` que se va a enviar de forma asincrónica.

### <a name="remarks"></a>Observaciones

Las implementaciones del procesador deben invalidar este método.

## <a name="process_incoming_message"></a>process_incoming_message

Cuando se reemplaza en una clase derivada, realiza el procesamiento hacia delante de los mensajes en el bloque. Se le llama una vez cada vez que se agrega un nuevo mensaje y se detecta que la cola está vacía.

```cpp
virtual void process_incoming_message() = 0;
```

### <a name="remarks"></a>Observaciones

Las implementaciones de bloque de mensajes deben invalidar este método.

## <a name="sync_send"></a>sync_send

Cuando se reemplaza en una clase derivada, coloca los mensajes en el bloque de forma sincrónica.

```cpp
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>Parámetros

*_Msg*<br/>
Objeto `message` que se va a enviar sincrónicamente.

### <a name="remarks"></a>Observaciones

Las implementaciones del procesador deben invalidar este método.

## <a name="wait"></a>currir

Cuando se reemplaza en una clase derivada, espera a que se completen todas las operaciones asincrónicas.

```cpp
virtual void wait() = 0;
```

### <a name="remarks"></a>Observaciones

Las implementaciones del procesador deben invalidar este método.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[ordered_message_processor (clase)](ordered-message-processor-class.md)
