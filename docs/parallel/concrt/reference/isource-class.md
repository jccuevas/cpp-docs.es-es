---
title: ISource (clase)
ms.date: 11/04/2016
f1_keywords:
- ISource
- AGENTS/concurrency::ISource
- AGENTS/concurrency::ISource::accept
- AGENTS/concurrency::ISource::acquire_ref
- AGENTS/concurrency::ISource::consume
- AGENTS/concurrency::ISource::link_target
- AGENTS/concurrency::ISource::release
- AGENTS/concurrency::ISource::release_ref
- AGENTS/concurrency::ISource::reserve
- AGENTS/concurrency::ISource::unlink_target
- AGENTS/concurrency::ISource::unlink_targets
helpviewer_keywords:
- ISource class
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
ms.openlocfilehash: a9ef9990db6376536f2f2a15c053b3b1d4ed12cf
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139318"
---
# <a name="isource-class"></a>ISource (clase)

La clase `ISource` es la interfaz para todos los bloques de origen. Los bloques de origen propagan mensajes a los bloques `ITarget`.

## <a name="syntax"></a>Sintaxis

```cpp
template<class T>
class ISource;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos de la carga dentro de los mensajes generados por el bloque de origen.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`source_type`|Un alias de tipo para `T`.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[~ ISource (destructor)](#dtor)|Destruye el objeto `ISource`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[acept](#accept)|Cuando se invalida en una clase derivada, acepta un mensaje ofrecido por este `ISource` bloque, transfiriendo la propiedad al autor de la llamada.|
|[acquire_ref](#acquire_ref)|Cuando se reemplaza en una clase derivada, adquiere un recuento de referencias en este bloque `ISource` para evitar la eliminación.|
|[consumo](#consume)|Cuando se reemplaza en una clase derivada, consume un mensaje ofrecido anteriormente por este `ISource` bloque y reservado correctamente por el destino, transfiriendo la propiedad al autor de la llamada.|
|[link_target](#link_target)|Cuando se invalida en una clase derivada, vincula un bloque de destino a este bloque de `ISource`.|
|[release](#release)|Cuando se reemplaza en una clase derivada, libera una reserva de mensajes correcta anterior.|
|[release_ref](#release_ref)|Cuando se reemplaza en una clase derivada, libera un recuento de referencias en este bloque de `ISource`.|
|[reserve](#reserve)|Cuando se reemplaza en una clase derivada, reserva un mensaje ofrecido anteriormente por este `ISource` bloque.|
|[unlink_target](#unlink_target)|Cuando se reemplaza en una clase derivada, desvincula un bloque de destino de este bloque `ISource`, si se encuentra vinculado previamente.|
|[unlink_targets](#unlink_targets)|Cuando se reemplaza en una clase derivada, desvincula todos los bloques de destino de este bloque `ISource`.|

## <a name="remarks"></a>Observaciones

Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ISource`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

## <a name="accept"></a>acept

Cuando se invalida en una clase derivada, acepta un mensaje ofrecido por este `ISource` bloque, transfiriendo la propiedad al autor de la llamada.

```cpp
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto `message` proporcionado.

*_PTarget*<br/>
Puntero al bloque de destino que llama al método de `accept`.

### <a name="return-value"></a>Valor devuelto

Un puntero al mensaje del que el llamador tiene ahora propiedad.

### <a name="remarks"></a>Observaciones

Un destino llama al método `accept` mientras este bloque `ISource` ofrece un mensaje. El puntero de mensaje devuelto puede ser diferente del que se pasa al método `propagate` del bloque de `ITarget`, si este origen decide realizar una copia del mensaje.

## <a name="acquire_ref"></a>acquire_ref

Cuando se reemplaza en una clase derivada, adquiere un recuento de referencias en este bloque `ISource` para evitar la eliminación.

```cpp
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Puntero al bloque de destino que llama a este método.

### <a name="remarks"></a>Observaciones

Un objeto `ITarget` que se vincula a este origen llama a este método durante el método `link_target`.

## <a name="consume"></a>emplear

Cuando se reemplaza en una clase derivada, consume un mensaje ofrecido anteriormente por este `ISource` bloque y reservado correctamente por el destino, transfiriendo la propiedad al autor de la llamada.

```cpp
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` reservado.

*_PTarget*<br/>
Puntero al bloque de destino que llama al método de `consume`.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de `message` al que el llamador tiene ahora propiedad.

### <a name="remarks"></a>Observaciones

El método `consume` es similar a `accept`, pero siempre debe ir precedido de una llamada a `reserve` que devolvió **true**.

## <a name="dtor"></a>~ ISource

Destruye el objeto `ISource`.

```cpp
virtual ~ISource();
```

## <a name="link_target"></a>link_target

Cuando se invalida en una clase derivada, vincula un bloque de destino a este bloque de `ISource`.

```cpp
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Puntero al bloque de destino que se está vinculando a este `ISource` bloque.

## <a name="release"></a>emisión

Cuando se reemplaza en una clase derivada, libera una reserva de mensajes correcta anterior.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto de `message` reservado.

*_PTarget*<br/>
Puntero al bloque de destino que llama al método de `release`.

## <a name="release_ref"></a>release_ref

Cuando se reemplaza en una clase derivada, libera un recuento de referencias en este bloque de `ISource`.

```cpp
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Puntero al bloque de destino que llama a este método.

### <a name="remarks"></a>Observaciones

Un objeto `ITarget` al que se va a desvincular de este origen llama a este método. El bloque de origen puede liberar los recursos reservados para el bloque de destino.

## <a name="reserve"></a>realizan

Cuando se reemplaza en una clase derivada, reserva un mensaje ofrecido anteriormente por este `ISource` bloque.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
`runtime_object_identity` del objeto `message` proporcionado.

*_PTarget*<br/>
Puntero al bloque de destino que llama al método de `reserve`.

### <a name="return-value"></a>Valor devuelto

**true** si el mensaje se ha reservado correctamente; de lo contrario, **false** . Se puede producir un error en las reservas por muchas razones, como: el mensaje ya estaba reservado o lo aceptó otro destino, el origen podría denegar reservas, etc.

### <a name="remarks"></a>Observaciones

Después de llamar a `reserve`, si se realiza correctamente, debe llamar a `consume` o `release` para poder llevar a cabo o renunciar al mensaje, respectivamente.

## <a name="unlink_target"></a>unlink_target

Cuando se reemplaza en una clase derivada, desvincula un bloque de destino de este bloque `ISource`, si se encuentra vinculado previamente.

```cpp
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Puntero al bloque de destino que se va a desvincular de este bloque de `ISource`.

## <a name="unlink_targets"></a>unlink_targets

Cuando se reemplaza en una clase derivada, desvincula todos los bloques de destino de este bloque `ISource`.

```cpp
virtual void unlink_targets() = 0;
```

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[ITarget (clase)](itarget-class.md)
