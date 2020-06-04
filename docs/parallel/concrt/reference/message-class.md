---
title: message (clase)
ms.date: 11/04/2016
f1_keywords:
- message
- AGENTS/concurrency::message
- AGENTS/concurrency::message::message
- AGENTS/concurrency::message::add_ref
- AGENTS/concurrency::message::msg_id
- AGENTS/concurrency::message::remove_ref
- AGENTS/concurrency::message::payload
helpviewer_keywords:
- message class
ms.assetid: 3e1f3505-6c0c-486c-8191-666d0880ec62
ms.openlocfilehash: 700d052b6f22c970387a3ab45d299538a5b74e1b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139543"
---
# <a name="message-class"></a>message (clase)

El sobre del mensaje básico que contiene la carga de datos que se pasa entre bloques de mensajería.

## <a name="syntax"></a>Sintaxis

```cpp
template<class T>
class message : public ::Concurrency::details::_Runtime_object;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos de la carga incluida en el mensaje.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`type`|Un alias de tipo para `T`.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[message](#ctor)|Sobrecargado. Construye un objeto `message`.|
|[~ (destructor de mensaje)](#dtor)|Destruye el objeto `message`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[add_ref](#add_ref)|Agrega al recuento de referencias para el objeto `message`. Se utiliza para los bloques de mensajes que necesitan el recuento de referencias para determinar la duración de los mensajes.|
|[msg_id](#msg_id)|Devuelve el identificador del objeto `message`.|
|[remove_ref](#remove_ref)|Resta del recuento de referencias del objeto `message`. Se utiliza para los bloques de mensajes que necesitan el recuento de referencias para determinar la duración de los mensajes.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[payload](#payload)|La carga del objeto de `message`.|

## <a name="remarks"></a>Observaciones

Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`message`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="add_ref"></a>add_ref

Agrega al recuento de referencias para el objeto `message`. Se utiliza para los bloques de mensajes que necesitan el recuento de referencias para determinar la duración de los mensajes.

```cpp
long add_ref();
```

### <a name="return-value"></a>Valor devuelto

Nuevo valor del recuento de referencias.

## <a name="ctor"></a>Mensaje

Construye un objeto `message`.

```cpp
message(
    T const& _P);

message(
    T const& _P,
    runtime_object_identity _Id);

message(
    message const& _Msg);

message(
    _In_ message const* _Msg);
```

### <a name="parameters"></a>Parámetros

*_P*<br/>
La carga de este mensaje.

*_Id*<br/>
IDENTIFICADOR único de este mensaje.

*_Msg*<br/>
Referencia o puntero a un objeto `message`.

### <a name="remarks"></a>Observaciones

El constructor que toma un puntero a un objeto de `message` como argumento produce una excepción de [invalid_argument](../../../standard-library/invalid-argument-class.md) si se `NULL`el `_Msg` de parámetros.

## <a name="dtor"></a>~ Message

Destruye el objeto `message`.

```cpp
virtual ~message();
```

## <a name="msg_id"></a>msg_id

Devuelve el identificador del objeto `message`.

```cpp
runtime_object_identity msg_id() const;
```

### <a name="return-value"></a>Valor devuelto

`runtime_object_identity` del objeto `message`.

## <a name="payload"></a>útiles

La carga del objeto de `message`.

```cpp
T const payload;
```

## <a name="remove_ref"></a>remove_ref

Resta del recuento de referencias del objeto `message`. Se utiliza para los bloques de mensajes que necesitan el recuento de referencias para determinar la duración de los mensajes.

```cpp
long remove_ref();
```

### <a name="return-value"></a>Valor devuelto

Nuevo valor del recuento de referencias.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
