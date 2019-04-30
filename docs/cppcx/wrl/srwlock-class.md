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
ms.openlocfilehash: 6d4a504d9465c858af59a88cf0ef611bf88c3fde
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403098"
---
# <a name="srwlock-class"></a>SRWLock (clase)

Representa un bloqueo fino de lector/escritor.

## <a name="syntax"></a>Sintaxis

```cpp
class SRWLock;
```

## <a name="remarks"></a>Comentarios

Un bloqueo fino de lector/escritor se utiliza para sincronizar el acceso a través de subprocesos a un objeto o un recurso. Para obtener más información, consulte [funciones de sincronización](/windows/desktop/Sync/synchronization-functions).

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Name                | Descripción
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | Sinónimo de un `SRWLock` objeto que se adquiere en modo exclusivo.
`SyncLockShared`    | Sinónimo de un `SRWLock` objeto que se adquiere en modo compartido.

### <a name="public-constructors"></a>Constructores públicos

Name                                     | Descripción
---------------------------------------- | --------------------------------------------------
[SRWLock::SRWLock](#srwlock-constructor) | Inicializa una nueva instancia de la clase `SRWLock`.
[SRWLock::~SRWLock](#tilde-srwlock)      | Desinicializa una instancia de la `SRWLock` clase.

### <a name="public-methods"></a>Métodos públicos

Name                                           | Descripción
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock::LockExclusive](#lockexclusive)       | Adquiere un `SRWLock` objeto en modo exclusivo.
[SRWLock::LockShared](#lockshared)             | Adquiere un `SRWLock` objeto en modo compartido.
[SRWLock::TryLockExclusive](#trylockexclusive) | Intenta adquirir un `SRWLock` objeto en modo exclusivo para el actual o especificada `SRWLock` objeto.
[SRWLock::TryLockShared](#trylockshared)       | Intenta adquirir un `SRWLock` objeto en modo compartido para el actual o especificada `SRWLock` objeto.

### <a name="protected-data-member"></a>Miembro de datos protegidos

Name                                      | Descripción
----------------------------------------- | -----------------------------------------------------------------------
[SRWLock::SRWLock_](#srwlock-data-member) | Contiene la variable subyacente de bloqueo actual `SRWLock` objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SRWLock`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres**: Microsoft::WRL::Wrappers

## <a name="tilde-srwlock"></a>SRWLock::~SRWLock

Desinicializa una instancia de la `SRWLock` clase.

```cpp
~SRWLock();
```

## <a name="lockexclusive"></a>SRWLock::LockExclusive

Adquiere un `SRWLock` objeto en modo exclusivo.

```cpp
SyncLockExclusive LockExclusive();

static SyncLockExclusive LockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parámetros

*lock*<br/>
Puntero a un `SRWLock` objeto.

### <a name="return-value"></a>Valor devuelto

Un `SRWLock` objeto en modo exclusivo.

## <a name="lockshared"></a>SRWLock::LockShared

Adquiere un `SRWLock` objeto en modo compartido.

```cpp
SyncLockShared LockShared();

static SyncLockShared LockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parámetros

*lock*<br/>
Puntero a un `SRWLock` objeto.

### <a name="return-value"></a>Valor devuelto

Un `SRWLock` objeto en modo compartido.

## <a name="srwlock-constructor"></a>SRWLock::SRWLock

Inicializa una nueva instancia de la clase `SRWLock`.

```cpp
SRWLock();
```

## <a name="srwlock-data-member"></a>SRWLock::SRWLock_

Contiene la variable subyacente de bloqueo actual `SRWLock` objeto.

```cpp
SRWLOCK SRWLock_;
```

## <a name="trylockexclusive"></a>SRWLock::TryLockExclusive

Intenta adquirir un `SRWLock` objeto en modo exclusivo para el actual o especificada `SRWLock` objeto. Si la llamada se realiza correctamente, el subproceso de llamada toma posesión del bloqueo.

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parámetros

*lock*<br/>
Puntero a un `SRWLock` objeto.

### <a name="return-value"></a>Valor devuelto

Si es correcto, un `SRWLock` objeto en modo exclusivo y el subproceso de llamada toma posesión del bloqueo. En caso contrario, un `SRWLock` objeto cuyo estado no es válido.

## <a name="trylockshared"></a>SRWLock::TryLockShared

Intenta adquirir un `SRWLock` objeto en modo compartido para el actual o especificada `SRWLock` objeto.

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parámetros

*lock*<br/>
Puntero a un `SRWLock` objeto.

### <a name="return-value"></a>Valor devuelto

Si es correcto, un `SRWLock` objeto en modo compartido y el subproceso de llamada toma posesión del bloqueo. En caso contrario, un `SRWLock` objeto cuyo estado no es válido.
