---
title: SRWLock (clase) | Microsoft Docs
ms.custom: ''
ms.date: 09/25/2018
ms.technology:
- cpp-windows
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 771a375d46177bb3b9d263f0a5221039bb963bc2
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48233975"
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
[SRWLOCK](#srwlock-constructor) | Inicializa una nueva instancia de la clase `SRWLock`.
[SRWLock:: ~ SRWLock](#tilde-srwlock)      | Desinicializa una instancia de la `SRWLock` clase.

### <a name="public-methods"></a>Métodos públicos

Name                                           | Descripción
---------------------------------------------- | -------------------------------------------------------------------------------------------------------
[Lockexclusive](#lockexclusive)       | Adquiere un `SRWLock` objeto en modo exclusivo.
[Lockshared](#lockshared)             | Adquiere un `SRWLock` objeto en modo compartido.
[Trylockexclusive](#trylockexclusive) | Intenta adquirir un `SRWLock` objeto en modo exclusivo para el actual o especificada `SRWLock` objeto.
[Trylockshared](#trylockshared)       | Intenta adquirir un `SRWLock` objeto en modo compartido para el actual o especificada `SRWLock` objeto.

### <a name="protected-data-member"></a>Miembro de datos protegidos

nombre                                      | Descripción
----------------------------------------- | -----------------------------------------------------------------------
[Srwlock_](#srwlock-data-member) | Contiene la variable subyacente de bloqueo actual `SRWLock` objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SRWLock`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="tilde-srwlock"></a>SRWLock:: ~ SRWLock

Desinicializa una instancia de la `SRWLock` clase.

```cpp
~SRWLock();
```

## <a name="lockexclusive"></a>Lockexclusive

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

## <a name="lockshared"></a>Lockshared

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

## <a name="srwlock-constructor"></a>SRWLOCK

Inicializa una nueva instancia de la clase `SRWLock`.

```cpp
SRWLock();
```

## <a name="srwlock-data-member"></a>Srwlock_

Contiene la variable subyacente de bloqueo actual `SRWLock` objeto.

```cpp
SRWLOCK SRWLock_;
```

## <a name="trylockexclusive"></a>Trylockexclusive

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

## <a name="trylockshared"></a>Trylockshared

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
