---
title: SRWLock (clase)
ms.date: 09/25/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockExclusive
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockShared
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::SRWLock_
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::~SRWLock
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared
helpviewer_keywords:
- Microsoft::WRL::Wrappers::SRWLock class
- Microsoft::WRL::Wrappers::SRWLock::LockExclusive method
- Microsoft::WRL::Wrappers::SRWLock::LockShared method
- Microsoft::WRL::Wrappers::SRWLock::SRWLock, constructor
- Microsoft::WRL::Wrappers::SRWLock::SRWLock_ data member
- Microsoft::WRL::Wrappers::SRWLock::~SRWLock, destructor
- Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive method
- Microsoft::WRL::Wrappers::SRWLock::TryLockShared method
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
ms.openlocfilehash: e305ad54e30455ce7c25f356c454791da0783591
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377276"
---
# <a name="srwlock-class"></a>SRWLock (clase)

Representa un bloqueo de lector/escritor delgado.

## <a name="syntax"></a>Sintaxis

```cpp
class SRWLock;
```

## <a name="remarks"></a>Observaciones

Un bloqueo de lector/escritor delgado se utiliza para sincronizar el acceso entre subprocesos a un objeto o recurso. Para obtener más información, consulte Funciones de [sincronización](/windows/win32/Sync/synchronization-functions).

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Nombre                | Descripción
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | Sinónimo de `SRWLock` un objeto que se adquiere en modo exclusivo.
`SyncLockShared`    | Sinónimo de `SRWLock` un objeto que se adquiere en modo compartido.

### <a name="public-constructors"></a>Constructores públicos

Nombre                                     | Descripción
---------------------------------------- | --------------------------------------------------
[SRWLock::SRWLock](#srwlock-constructor) | Inicializa una nueva instancia de la clase `SRWLock`.
[SRWLock::-SRWLock](#tilde-srwlock)      | Desinicializa una instancia `SRWLock` de la clase.

### <a name="public-methods"></a>Métodos públicos

Nombre                                           | Descripción
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock::LockExclusive](#lockexclusive)       | Adquiere un `SRWLock` objeto en modo exclusivo.
[SRWLock::LockShared](#lockshared)             | Adquiere un `SRWLock` objeto en modo compartido.
[SRWLock::TryLockExclusive](#trylockexclusive) | Intenta adquirir `SRWLock` un objeto en modo exclusivo `SRWLock` para el objeto actual o especificado.
[SRWLock::TryLockShared](#trylockshared)       | Intenta adquirir `SRWLock` un objeto en modo compartido `SRWLock` para el objeto actual o especificado.

### <a name="protected-data-member"></a>Miembro de datos protegidos

Nombre                                      | Descripción
----------------------------------------- | -----------------------------------------------------------------------
[SRWLock::SRWLock_](#srwlock-data-member) | Contiene la variable de bloqueo `SRWLock` subyacente para el objeto actual.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SRWLock`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres:** Microsoft::WRL::Wrappers

## <a name="srwlocksrwlock"></a><a name="tilde-srwlock"></a>SRWLock::-SRWLock

Desinicializa una instancia `SRWLock` de la clase.

```cpp
~SRWLock();
```

## <a name="srwlocklockexclusive"></a><a name="lockexclusive"></a>SRWLock::LockExclusive

Adquiere un `SRWLock` objeto en modo exclusivo.

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parámetros

*Cerradura*<br/>
Puntero a `SRWLock` un objeto.

### <a name="return-value"></a>Valor devuelto

Un `SRWLock` objeto en modo exclusivo.

## <a name="srwlocklockshared"></a><a name="lockshared"></a>SRWLock::LockShared

Adquiere un `SRWLock` objeto en modo compartido.

```cpp
SyncLockShared LockShared();

static SyncLockShared LockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parámetros

*Cerradura*<br/>
Puntero a `SRWLock` un objeto.

### <a name="return-value"></a>Valor devuelto

Un `SRWLock` objeto en modo compartido.

## <a name="srwlocksrwlock"></a><a name="srwlock-constructor"></a>SRWLock::SRWLock

Inicializa una nueva instancia de la clase `SRWLock`.

```cpp
SRWLock();
```

## <a name="srwlocksrwlock_"></a><a name="srwlock-data-member"></a>SRWLock::SRWLock_

Contiene la variable de bloqueo `SRWLock` subyacente para el objeto actual.

```cpp
SRWLOCK SRWLock_;
```

## <a name="srwlocktrylockexclusive"></a><a name="trylockexclusive"></a>SRWLock::TryLockExclusive

Intenta adquirir `SRWLock` un objeto en modo exclusivo `SRWLock` para el objeto actual o especificado. Si la llamada se realiza correctamente, el subproceso que realiza la llamada toma la propiedad del bloqueo.

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parámetros

*Cerradura*<br/>
Puntero a `SRWLock` un objeto.

### <a name="return-value"></a>Valor devuelto

Si se `SRWLock` realiza correctamente, un objeto en modo exclusivo y el subproceso que realiza la llamada toma la propiedad del bloqueo. De lo `SRWLock` contrario, un objeto cuyo estado no es válido.

## <a name="srwlocktrylockshared"></a><a name="trylockshared"></a>SRWLock::TryLockShared

Intenta adquirir `SRWLock` un objeto en modo compartido `SRWLock` para el objeto actual o especificado.

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parámetros

*Cerradura*<br/>
Puntero a `SRWLock` un objeto.

### <a name="return-value"></a>Valor devuelto

Si se `SRWLock` realiza correctamente, un objeto en modo compartido y el subproceso que realiza la llamada toma la propiedad del bloqueo. De lo `SRWLock` contrario, un objeto cuyo estado no es válido.
