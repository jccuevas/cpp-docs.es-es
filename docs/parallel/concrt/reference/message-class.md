---
title: message (Clase)
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
ms.openlocfilehash: 83cfdb5807581f7092709691a1839052abdd657c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263083"
---
# <a name="message-class"></a>message (Clase)

El sobre del mensaje básico que contiene la carga de datos que se pasa entre bloques de mensajería.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class message : public ::Concurrency::details::_Runtime_object;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos de la carga dentro del mensaje.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`type`|Un alias de tipo para `T`.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[message](#ctor)|Sobrecargado. Construye un objeto `message`.|
|[~ message (destructor)](#dtor)|Destruye el objeto `message`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[add_ref](#add_ref)|Agrega el recuento de referencias para el `message` objeto. Se usa para los bloques de mensajes que necesitan el recuento de referencias para determinar la duración del mensaje.|
|[msg_id](#msg_id)|Devuelve el identificador de la `message` objeto.|
|[remove_ref](#remove_ref)|Resta el recuento de referencias para el `message` objeto. Se usa para los bloques de mensajes que necesitan el recuento de referencias para determinar la duración del mensaje.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[payload](#payload)|La carga de la `message` objeto.|

## <a name="remarks"></a>Comentarios

Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`message`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

##  <a name="add_ref"></a> add_ref

Agrega el recuento de referencias para el `message` objeto. Se usa para los bloques de mensajes que necesitan el recuento de referencias para determinar la duración del mensaje.

```
long add_ref();
```

### <a name="return-value"></a>Valor devuelto

El nuevo valor del recuento de referencia.

##  <a name="ctor"></a> Mensaje

Construye un objeto `message`.

```
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
El identificador único de este mensaje.

*_Msg*<br/>
Una referencia o puntero a un `message` objeto.

### <a name="remarks"></a>Comentarios

El constructor que toma un puntero a un `message` objeto como un argumento, se produce un [invalid_argument](../../../standard-library/invalid-argument-class.md) excepción si el parámetro `_Msg` es `NULL`.

##  <a name="dtor"></a> ~message

Destruye el objeto `message`.

```
virtual ~message();
```

##  <a name="msg_id"></a> msg_id

Devuelve el identificador de la `message` objeto.

```
runtime_object_identity msg_id() const;
```

### <a name="return-value"></a>Valor devuelto

El `runtime_object_identity` de la `message` objeto.

##  <a name="payload"></a> carga

La carga de la `message` objeto.

```
T const payload;
```

##  <a name="remove_ref"></a> remove_ref

Resta el recuento de referencias para el `message` objeto. Se usa para los bloques de mensajes que necesitan el recuento de referencias para determinar la duración del mensaje.

```
long remove_ref();
```

### <a name="return-value"></a>Valor devuelto

El nuevo valor del recuento de referencia.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
