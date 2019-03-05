---
title: message_processor (Clase)
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
ms.openlocfilehash: be6cb1c614a41919663a4cc063da66679556e498
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295245"
---
# <a name="messageprocessor-class"></a>message_processor (Clase)

La clase `message_processor` es la clase base abstracta del procesamiento de objetos `message`. No hay ninguna garantía en la clasificación de los mensajes.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class message_processor;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos de la carga en los mensajes de administra este `message_processor` objeto.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`type`|Un alias de tipo para `T`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[async_send](#async_send)|Cuando se invalida en una clase derivada, coloca los mensajes en el bloque de forma asincrónica.|
|[sync_send](#sync_send)|Cuando se invalida en una clase derivada, coloca los mensajes en el bloque de forma sincrónica.|
|[wait](#wait)|Cuando se invalida en una clase derivada, espera a que todas las operaciones asincrónicas en completarse.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|Cuando se invalida en una clase derivada, realiza el procesamiento reenvío de mensajes en el bloque. Se llama una vez cada vez que se agrega un nuevo mensaje y se encuentra la cola esté vacío.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`message_processor`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

##  <a name="async_send"></a> async_send

Cuando se invalida en una clase derivada, coloca los mensajes en el bloque de forma asincrónica.

```
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>Parámetros

*_Msg*<br/>
Un `message` objeto va a enviar de forma asincrónica.

### <a name="remarks"></a>Comentarios

Las implementaciones del procesador deben invalidar este método.

##  <a name="process_incoming_message"></a> process_incoming_message

Cuando se invalida en una clase derivada, realiza el procesamiento reenvío de mensajes en el bloque. Se llama una vez cada vez que se agrega un nuevo mensaje y se encuentra la cola esté vacío.

```
virtual void process_incoming_message() = 0;
```

### <a name="remarks"></a>Comentarios

Las implementaciones de bloque de mensajes deben invalidar este método.

##  <a name="sync_send"></a> sync_send

Cuando se invalida en una clase derivada, coloca los mensajes en el bloque de forma sincrónica.

```
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>Parámetros

*_Msg*<br/>
Un `message` objeto va a enviar de forma sincrónica.

### <a name="remarks"></a>Comentarios

Las implementaciones del procesador deben invalidar este método.

##  <a name="wait"></a> Espere

Cuando se invalida en una clase derivada, espera a que todas las operaciones asincrónicas en completarse.

```
virtual void wait() = 0;
```

### <a name="remarks"></a>Comentarios

Las implementaciones del procesador deben invalidar este método.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[ordered_message_processor (clase)](ordered-message-processor-class.md)
