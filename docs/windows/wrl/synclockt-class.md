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
ms.openlocfilehash: d27e6ba8601d0e822113bf3a4a65269c89437271
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337518"
---
# <a name="synclockt-class"></a>SyncLockT (clase)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename SyncTraits>
class SyncLockT;
```

### <a name="parameters"></a>Parámetros

*SyncTraits*<br/>
El tipo que puede tomar posesión de un recurso.

## <a name="remarks"></a>Comentarios

Representa un tipo que puede tardar exclusivo o propiedad compartida de un recurso.

El `SyncLockT` clase se utiliza, por ejemplo, para ayudar a implementar el [SRWLock](srwlock-class.md) clase.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

Name                                      | Descripción
----------------------------------------- | ----------------------------------------------------
[SyncLockT::SyncLockT](#synclockt)        | Inicializa una nueva instancia de la clase `SyncLockT`.
[SyncLockT::~SyncLockT](#tilde-synclockt) | Desinicializa una instancia de la `SyncLockT` clase.

### <a name="protected-constructors"></a>Constructores protegidos

Name                               | Descripción
---------------------------------- | ----------------------------------------------------
[SyncLockT::SyncLockT](#synclockt) | Inicializa una nueva instancia de la clase `SyncLockT`.

### <a name="public-methods"></a>Métodos públicos

Name                             | Descripción
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[SyncLockT::IsLocked](#islocked) | Indica si el actual `SyncLockT` objeto posee un recurso; es decir, el `SyncLockT` objeto es *bloqueado*.
[SyncLockT::Unlock](#unlock)     | Devuelve el control de los recursos mantenidos por el actual `SyncLockT` objeto, si existe.

### <a name="protected-data-members"></a>Miembros de datos protegidos

nombre                      | Descripción
------------------------- | -------------------------------------------------------------------
[SyncLockT::sync_](#sync) | Contiene el recurso subyacente representado por la `SyncLockT` clase.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SyncLockT`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres**: Microsoft::WRL::Wrappers::Details

## <a name="tilde-synclockt"></a>SyncLockT::~SyncLockT

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
~SyncLockT();
```

### <a name="remarks"></a>Comentarios

Desinicializa una instancia de la `SyncLockT` clase.

Este destructor también desbloquea actual `SyncLockT` instancia.

## <a name="islocked"></a>SyncLockT::IsLocked

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si el `SyncLockT` objeto está bloqueado; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Indica si el actual `SyncLockT` objeto posee un recurso; es decir, el `SyncLockT` objeto es *bloqueado*.

## <a name="sync"></a>SyncLockT::sync_

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>Comentarios

Contiene el recurso subyacente representado por la `SyncLockT` clase.

## <a name="synclockt"></a>SyncLockT::SyncLockT

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
SyncLockT(
   _Inout_ SyncLockT&& other
);

explicit SyncLockT(
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()
);
```

### <a name="parameters"></a>Parámetros

*other*<br/>
Una referencia rvalue a otro `SyncLockT` objeto.

*sync*<br/>
Una referencia a otro `SyncLockWithStatusT` objeto.

### <a name="remarks"></a>Comentarios

Inicializa una nueva instancia de la clase `SyncLockT`.

El primer constructor inicializa actual `SyncLockT` objeto desde otro `SyncLockT` objeto especificado por el parámetro *otros*y, a continuación, se invalidan otro `SyncLockT` objeto. Es el segundo constructor `protected`e inicializa actual `SyncLockT` objeto a un estado no válido.

## <a name="unlock"></a>SyncLockT::Unlock

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

```cpp
void Unlock();
```

### <a name="remarks"></a>Comentarios

Devuelve el control de los recursos mantenidos por el actual `SyncLockT` objeto, si existe.
