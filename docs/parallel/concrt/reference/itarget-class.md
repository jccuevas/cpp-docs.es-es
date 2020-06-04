---
title: ITarget (clase)
ms.date: 11/04/2016
f1_keywords:
- ITarget
- AGENTS/concurrency::ITarget
- AGENTS/concurrency::ITarget::propagate
- AGENTS/concurrency::ITarget::send
- AGENTS/concurrency::ITarget::supports_anonymous_source
- AGENTS/concurrency::ITarget::link_source
- AGENTS/concurrency::ITarget::unlink_source
- AGENTS/concurrency::ITarget::unlink_sources
helpviewer_keywords:
- ITarget class
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
ms.openlocfilehash: dc9eacad744536e640417a4ebf51b975bd05bcc7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142030"
---
# <a name="itarget-class"></a>ITarget (clase)

La clase `ITarget` es la interfaz para todos los bloques de destino. Los bloques de destinos consumen mensajes ofrecidos por los bloques `ISource`.

## <a name="syntax"></a>Sintaxis

```cpp
template<class T>
class ITarget;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos de la carga dentro de los mensajes aceptados por el bloque de destino.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`filter_method`|Firma de cualquier método utilizado por el bloque que devuelve un valor `bool` para determinar si se debe aceptar un mensaje ofrecido.|
|`type`|Un alias de tipo para `T`.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[~ ITarget (destructor)](#dtor)|Destruye el objeto `ITarget`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[propagar](#propagate)|Cuando se reemplaza en una clase derivada, pasa de forma asincrónica un mensaje de un bloque de origen a este bloque de destino.|
|[send](#send)|Cuando se reemplaza en una clase derivada, pasa un mensaje de forma sincrónica al bloque de destino.|
|[supports_anonymous_source](#supports_anonymous_source)|Cuando se reemplaza en una clase derivada, devuelve true o false, en función de si el bloque de mensajes acepta mensajes ofrecidos por un origen que no está vinculado a él. Si el método invalidado devuelve **true**, el destino no puede posponer un mensaje ofrecido, ya que el uso de un mensaje pospuesto en un momento posterior requiere la identificación del origen en su registro de vínculo de origen.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[link_source](#link_source)|Cuando se reemplaza en una clase derivada, vincula un bloque de origen especificado a este bloque de `ITarget`.|
|[unlink_source](#unlink_source)|Cuando se reemplaza en una clase derivada, desvincula un bloque de origen especificado de este bloque `ITarget`.|
|[unlink_sources](#unlink_sources)|Cuando se reemplaza en una clase derivada, desvincula todos los bloques de origen de este bloque `ITarget`.|

## <a name="remarks"></a>Observaciones

Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ITarget`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="dtor"></a>~ ITarget

Destruye el objeto `ITarget`.

```cpp
virtual ~ITarget();
```

## <a name="link_source"></a>link_source

Cuando se reemplaza en una clase derivada, vincula un bloque de origen especificado a este bloque de `ITarget`.

```cpp
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parámetros

*_PSource*<br/>
`ISource` bloque que se está vinculando a este bloque de `ITarget`.

### <a name="remarks"></a>Observaciones

No se debe llamar a esta función directamente en un bloque `ITarget`. Los bloques se deben conectar entre sí mediante el método `link_target` en `ISource` bloques, lo que invocará el método `link_source` en el destino correspondiente.

## <a name="propagate"></a>propagar

Cuando se reemplaza en una clase derivada, pasa de forma asincrónica un mensaje de un bloque de origen a este bloque de destino.

```cpp
virtual message_status propagate(
    _Inout_opt_ message<T>* _PMessage,
    _Inout_opt_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Un puntero al objeto `message`.

*_PSource*<br/>
Puntero al bloque de origen que ofrece el mensaje.

### <a name="return-value"></a>Valor devuelto

[Message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.

### <a name="remarks"></a>Observaciones

El método produce una excepción de [invalid_argument](../../../standard-library/invalid-argument-class.md) si se `NULL`el parámetro `_PMessage` o `_PSource`.

## <a name="send"></a>Enviar

Cuando se reemplaza en una clase derivada, pasa un mensaje de forma sincrónica al bloque de destino.

```cpp
virtual message_status send(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parámetros

*_PMessage*<br/>
Un puntero al objeto `message`.

*_PSource*<br/>
Puntero al bloque de origen que ofrece el mensaje.

### <a name="return-value"></a>Valor devuelto

[Message_status](concurrency-namespace-enums.md) indicación de lo que el destino decidió hacer con el mensaje.

### <a name="remarks"></a>Observaciones

El método produce una excepción de [invalid_argument](../../../standard-library/invalid-argument-class.md) si se `NULL`el parámetro `_PMessage` o `_PSource`.

Usar el método `send` fuera del inicio del mensaje y propagar los mensajes dentro de una red es peligroso y puede provocar un interbloqueo.

Cuando `send` devuelve, el mensaje ya se aceptó y se transfirió al bloque de destino, o bien el destino lo rechazó.

## <a name="supports_anonymous_source"></a>supports_anonymous_source

Cuando se reemplaza en una clase derivada, devuelve true o false, en función de si el bloque de mensajes acepta mensajes ofrecidos por un origen que no está vinculado a él. Si el método invalidado devuelve **true**, el destino no puede posponer un mensaje ofrecido, ya que el uso de un mensaje pospuesto en un momento posterior requiere que el origen se identifique en su registro de vínculo de sistema.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Valor devuelto

**true** si el bloque puede aceptar mensajes de un origen que no está vinculado a él **false** en caso contrario.

## <a name="unlink_source"></a>unlink_source

Cuando se reemplaza en una clase derivada, desvincula un bloque de origen especificado de este bloque `ITarget`.

```cpp
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parámetros

*_PSource*<br/>
Bloque de `ISource` que se va a desvincular de este bloque de `ITarget`.

### <a name="remarks"></a>Observaciones

No se debe llamar a esta función directamente en un bloque `ITarget`. Los bloques se deben desconectar mediante los métodos `unlink_target` o `unlink_targets` en los bloques `ISource`, lo que invocará el método `unlink_source` en el destino correspondiente.

## <a name="unlink_sources"></a>unlink_sources

Cuando se reemplaza en una clase derivada, desvincula todos los bloques de origen de este bloque `ITarget`.

```cpp
virtual void unlink_sources() = 0;
```

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[ISource (clase)](isource-class.md)
