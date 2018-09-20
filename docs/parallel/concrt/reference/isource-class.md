---
title: ISource (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- ISource class
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 26f39b9fff9d5fad930123fc930afe1600cd259e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396485"
---
# <a name="isource-class"></a>ISource (Clase)

La clase `ISource` es la interfaz para todos los bloques de origen. Los bloques de origen propagan mensajes a los bloques `ITarget`.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class ISource;
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos de la carga dentro de los mensajes generados por el bloque de origen.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`source_type`|Un alias de tipo para `T`.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[~ ISource (destructor)](#dtor)|Destruye el objeto `ISource`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[Aceptar](#accept)|Cuando se invalida en una clase derivada, acepta un mensaje que se ha proporcionado por este `ISource` bloque, transfiriendo la propiedad al llamador.|
|[acquire_ref](#acquire_ref)|Cuando se invalida en una clase derivada, adquiere un recuento de referencias en este `ISource` bloquear para impedir la eliminación.|
|[consumir](#consume)|Cuando se invalida en una clase derivada, consume un mensaje ofrecido previamente por este `ISource` bloquear y correctamente reservado por el destino, transfiriendo la propiedad al llamador.|
|[link_target](#link_target)|Cuando se invalida en una clase derivada, vincula un bloque de destino a esta `ISource` bloque.|
|[release](#release)|Cuando se invalida en una clase derivada, libera una reserva de mensaje correcto anterior.|
|[release_ref](#release_ref)|Cuando se reemplaza en una clase derivada, libera un recuento de referencias en este `ISource` bloque.|
|[reserve](#reserve)|Cuando se invalida en una clase derivada, se reserva un mensaje ofrecido previamente por este `ISource` bloque.|
|[unlink_target](#unlink_target)|Cuando se invalida en una clase derivada, desvincula un bloque de destino de este `ISource` bloquear si se encuentra vinculado previamente.|
|[unlink_targets](#unlink_targets)|Cuando se invalida en una clase derivada, desvincula todos los bloques de destino de este `ISource` bloque.|

## <a name="remarks"></a>Comentarios

Para obtener más información, consulte [bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ISource`

## <a name="requirements"></a>Requisitos

**Encabezado:** agents.h

**Espacio de nombres:** simultaneidad

##  <a name="accept"></a> Aceptar

Cuando se invalida en una clase derivada, acepta un mensaje que se ha proporcionado por este `ISource` bloque, transfiriendo la propiedad al llamador.

```
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
El `runtime_object_identity` de la ofrecida `message` objeto.

*_PTarget*<br/>
Un puntero al bloque de destino que llama a la `accept` método.

### <a name="return-value"></a>Valor devuelto

Un puntero al mensaje que el llamador tiene ahora la propiedad.

### <a name="remarks"></a>Comentarios

El `accept` llama al método un destino mientras se ofrece un mensaje por este `ISource` bloque. El puntero de mensaje devuelto puede ser diferente del que se pasó el `propagate` método de la `ITarget` block, si decide realizar una copia del mensaje de este origen.

##  <a name="acquire_ref"></a> acquire_ref

Cuando se invalida en una clase derivada, adquiere un recuento de referencias en este `ISource` bloquear para impedir la eliminación.

```
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Un puntero al bloque de destino que llama a este método.

### <a name="remarks"></a>Comentarios

Este método es invocado por un `ITarget` objeto vinculado a este origen durante la `link_target` método.

##  <a name="consume"></a> consumir

Cuando se invalida en una clase derivada, consume un mensaje ofrecido previamente por este `ISource` bloquear y correctamente reservado por el destino, transfiriendo la propiedad al llamador.

```
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
El `runtime_object_identity` de reservado `message` objeto.

*_PTarget*<br/>
Un puntero al bloque de destino que llama a la `consume` método.

### <a name="return-value"></a>Valor devuelto

Un puntero a la `message` que el llamador tiene ahora la propiedad de objeto.

### <a name="remarks"></a>Comentarios

El `consume` es similar al método `accept`, pero siempre debe ir precedido por una llamada a `reserve` que devuelve `true`.

##  <a name="dtor"></a> ~ ISource

Destruye el objeto `ISource`.

```
virtual ~ISource();
```

##  <a name="link_target"></a> link_target

Cuando se invalida en una clase derivada, vincula un bloque de destino a esta `ISource` bloque.

```
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Un puntero al bloque de destino que se vincula a esta `ISource` bloque.

##  <a name="release"></a> Versión

Cuando se invalida en una clase derivada, libera una reserva de mensaje correcto anterior.

```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
El `runtime_object_identity` de reservado `message` objeto.

*_PTarget*<br/>
Un puntero al bloque de destino que llama a la `release` método.

##  <a name="release_ref"></a> release_ref

Cuando se reemplaza en una clase derivada, libera un recuento de referencias en este `ISource` bloque.

```
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Un puntero al bloque de destino que llama a este método.

### <a name="remarks"></a>Comentarios

Este método es invocado por un `ITarget` objeto que se desvincula de este origen. El bloque de origen se permite para liberar los recursos reservados para el bloque de destino.

##  <a name="reserve"></a> reservar

Cuando se invalida en una clase derivada, se reserva un mensaje ofrecido previamente por este `ISource` bloque.

```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parámetros

*_MsgId*<br/>
El `runtime_object_identity` de la ofrecida `message` objeto.

*_PTarget*<br/>
Un puntero al bloque de destino que llama a la `reserve` método.

### <a name="return-value"></a>Valor devuelto

`true` Si el mensaje se ha reservado correctamente, `false` en caso contrario. Las reservas de direcciones pueden producir un error por diversos motivos, incluidos: el mensaje ya se ha reservado o aceptados por otro destino, el origen podría denegar reservas y así sucesivamente.

### <a name="remarks"></a>Comentarios

Después de llamar a `reserve`, si se realiza correctamente, debe llamar a `consume` o `release` con el fin de Aceptar o ceder la posesión del mensaje, respectivamente.

##  <a name="unlink_target"></a> unlink_target

Cuando se invalida en una clase derivada, desvincula un bloque de destino de este `ISource` bloquear si se encuentra vinculado previamente.

```
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parámetros

*_PTarget*<br/>
Un puntero al bloque de destino que se desvincula de esto `ISource` bloque.

##  <a name="unlink_targets"></a> unlink_targets

Cuando se invalida en una clase derivada, desvincula todos los bloques de destino de este `ISource` bloque.

```
virtual void unlink_targets() = 0;
```

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[ITarget (clase)](itarget-class.md)
