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
ms.openlocfilehash: 079f1abe652d8c1610a084f5e1158cc5798d61c4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498290"
---
# <a name="srwlock-class"></a>SRWLock (clase)

Representa un bloqueo delgado de lector/escritor.

## <a name="syntax"></a>Sintaxis

```cpp
class SRWLock;
```

## <a name="remarks"></a>Comentarios

Un bloqueo delgado de lector/escritor se utiliza para sincronizar el acceso entre subprocesos a un objeto o recurso. Para obtener más información, vea [funciones de sincronización](/windows/win32/Sync/synchronization-functions).

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

NOMBRE                | DESCRIPCIÓN
------------------- | -------------------------------------------------------------------
`SyncLockExclusive` | Sinónimo de un `SRWLock` objeto que se adquiere en modo exclusivo.
`SyncLockShared`    | Sinónimo de un `SRWLock` objeto que se adquiere en modo compartido.

### <a name="public-constructors"></a>Constructores públicos

NOMBRE                                     | DESCRIPCIÓN
---------------------------------------- | --------------------------------------------------
[SRWLock::SRWLock](#srwlock-constructor) | Inicializa una nueva instancia de la clase `SRWLock`.
[SRWLock::~SRWLock](#tilde-srwlock)      | Desinicializa una instancia de la `SRWLock` clase.

### <a name="public-methods"></a>Métodos públicos

NOMBRE                                           | DESCRIPCIÓN
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[SRWLock::LockExclusive](#lockexclusive)       | Adquiere un `SRWLock` objeto en modo exclusivo.
[SRWLock::LockShared](#lockshared)             | Adquiere un `SRWLock` objeto en modo compartido.
[SRWLock::TryLockExclusive](#trylockexclusive) | Intenta adquirir un `SRWLock` objeto en modo exclusivo para el objeto actual o el `SRWLock` objeto especificado.
[SRWLock::TryLockShared](#trylockshared)       | Intenta adquirir un `SRWLock` objeto en modo compartido para el objeto actual o especificado `SRWLock` .

### <a name="protected-data-member"></a>Miembro de datos protegidos

NOMBRE                                      | DESCRIPCIÓN
----------------------------------------- | -----------------------------------------------------------------------
[SRWLock::SRWLock_](#srwlock-data-member) | Contiene la variable de bloqueo subyacente para el `SRWLock` objeto actual.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SRWLock`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers. h

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

`SRWLock` Objeto en modo exclusivo.

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

`SRWLock` Objeto en modo compartido.

## <a name="srwlock-constructor"></a>SRWLock::SRWLock

Inicializa una nueva instancia de la clase `SRWLock`.

```cpp
SRWLock();
```

## <a name="srwlock-data-member"></a>SRWLock::SRWLock_

Contiene la variable de bloqueo subyacente para el `SRWLock` objeto actual.

```cpp
SRWLOCK SRWLock_;
```

## <a name="trylockexclusive"></a>SRWLock::TryLockExclusive

Intenta adquirir un `SRWLock` objeto en modo exclusivo para el objeto actual o el `SRWLock` objeto especificado. Si la llamada se realiza correctamente, el subproceso que realiza la llamada toma la propiedad del bloqueo.

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

Si es correcto, `SRWLock` un objeto en modo exclusivo y el subproceso que realiza la llamada toma la propiedad del bloqueo. De lo contrario `SRWLock` , un objeto cuyo estado no sea válido.

## <a name="trylockshared"></a>SRWLock::TryLockShared

Intenta adquirir un `SRWLock` objeto en modo compartido para el objeto actual o especificado `SRWLock` .

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

Si es correcto, `SRWLock` un objeto en modo compartido y el subproceso que realiza la llamada toma la propiedad del bloqueo. De lo contrario `SRWLock` , un objeto cuyo estado no sea válido.
