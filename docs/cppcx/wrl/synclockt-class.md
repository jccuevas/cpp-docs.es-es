---
title: SyncLockT (clase)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::sync_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockT class
- Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockT::sync_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT, constructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT, destructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock method
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
ms.openlocfilehash: 52c4404fa28f680a9a7a4592d03f535e8406d1a4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374281"
---
# <a name="synclockt-class"></a>SyncLockT (clase)

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename SyncTraits>
class SyncLockT;
```

### <a name="parameters"></a>Parámetros

*SyncTraits*<br/>
El tipo que puede tomar posesión de un recurso.

## <a name="remarks"></a>Observaciones

Representa un tipo que puede tomar la propiedad exclusiva o compartida de un recurso.

La `SyncLockT` clase se utiliza, por ejemplo, para ayudar a implementar la clase [SRWLock.](srwlock-class.md)

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Nombre                                      | Descripción
----------------------------------------- | ----------------------------------------------------
[SyncLockT::SyncLockT](#synclockt)        | Inicializa una nueva instancia de la clase `SyncLockT`.
[SyncLockT::-SyncLockT](#tilde-synclockt) | Desinicializa una instancia `SyncLockT` de la clase.

### <a name="protected-constructors"></a>Constructores protegidos

Nombre                               | Descripción
---------------------------------- | ----------------------------------------------------
[SyncLockT::SyncLockT](#synclockt) | Inicializa una nueva instancia de la clase `SyncLockT`.

### <a name="public-methods"></a>Métodos públicos

Nombre                             | Descripción
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[SyncLockT::IsLocked](#islocked) | Indica si el `SyncLockT` objeto actual posee un recurso; es decir, `SyncLockT` el objeto está *bloqueado.*
[SyncLockT::Desbloquear](#unlock)     | Libera el control del recurso `SyncLockT` mantenido por el objeto actual, si existe.

### <a name="protected-data-members"></a>Miembros de datos protegidos

Nombre                      | Descripción
------------------------- | -------------------------------------------------------------------
[SyncLockT::sync_](#sync) | Contiene el recurso subyacente representado `SyncLockT` por la clase.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SyncLockT`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres:** Microsoft::WRL::Wrappers::Details

## <a name="synclocktsynclockt"></a><a name="tilde-synclockt"></a>SyncLockT::-SyncLockT

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
~SyncLockT();
```

### <a name="remarks"></a>Observaciones

Desinicializa una instancia `SyncLockT` de la clase.

Este destructor también desbloquea `SyncLockT` la instancia actual.

## <a name="synclocktislocked"></a><a name="islocked"></a>SyncLockT::IsLocked

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>Valor devuelto

**true** si `SyncLockT` el objeto está bloqueado; de lo contrario, **false**.

### <a name="remarks"></a>Observaciones

Indica si el `SyncLockT` objeto actual posee un recurso; es decir, `SyncLockT` el objeto está *bloqueado.*

## <a name="synclocktsync_"></a><a name="sync"></a>SyncLockT::sync_

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>Observaciones

Contiene el recurso subyacente representado `SyncLockT` por la clase.

## <a name="synclocktsynclockt"></a><a name="synclockt"></a>SyncLockT::SyncLockT

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
SyncLockT(
   _Inout_ SyncLockT&& other
);

explicit SyncLockT(
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()
);
```

### <a name="parameters"></a>Parámetros

*Otro*<br/>
Una referencia rvalue `SyncLockT` a otro objeto.

*Sincronizar*<br/>
Una referencia `SyncLockWithStatusT` a otro objeto.

### <a name="remarks"></a>Observaciones

Inicializa una nueva instancia de la clase `SyncLockT`.

El primer constructor inicializa `SyncLockT` el `SyncLockT` objeto actual desde otro objeto especificado por `SyncLockT` el parámetro *other*y, a continuación, invalida el otro objeto. El segundo `protected`constructor es , `SyncLockT` e inicializa el objeto actual en un estado no válido.

## <a name="synclocktunlock"></a><a name="unlock"></a>SyncLockT::Desbloquear

Admite la infraestructura WRL y no está diseñado para usarse directamente desde el código.

```cpp
void Unlock();
```

### <a name="remarks"></a>Observaciones

Libera el control del recurso `SyncLockT` mantenido por el objeto actual, si existe.
