---
title: Mutex (Clase)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Mutex class
- Microsoft::WRL::Wrappers::Mutex::Lock method
- Microsoft::WRL::Wrappers::Mutex::Mutex, constructor
- Microsoft::WRL::Wrappers::Mutex::operator= operator
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
ms.openlocfilehash: 36466bd00c5b100f20ee87173e68fdef4131ec23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371243"
---
# <a name="mutex-class"></a>Mutex (Clase)

Representa un objeto de sincronización que controla exclusivamente un recurso compartido.

## <a name="syntax"></a>Sintaxis

```cpp
class Mutex : public HandleT<HandleTraits::MutexTraits>;
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Nombre       | Descripción
---------- | ------------------------------------------------------
`SyncLock` | Sinónimo de una clase que admite bloqueos sincrónicos.

### <a name="public-constructor"></a>Constructor público

Nombre                   | Descripción
---------------------- | ------------------------------------------------
[Mutex::Mutex](#mutex) | Inicializa una nueva instancia de la clase `Mutex`.

### <a name="public-members"></a>Miembros públicos

Nombre                 | Descripción
-------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------
[Mutex::Bloqueo](#lock) | Espera hasta que el objeto `Mutex` actual, o el objeto asociado con el identificador especificado, libere la exclusión mutua o el intervalo de tiempo de espera especificado haya transcurrido.

### <a name="public-operator"></a>Operador Público

Nombre                                 | Descripción
------------------------------------ | ---------------------------------------------------------------------------
[Mutex::operador ?](#operator-assign) | Asigna (mueve) el `Mutex` objeto especificado `Mutex` al objeto actual.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Mutex`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres:** Microsoft::WRL::Wrappers

## <a name="mutexlock"></a><a name="lock"></a>Mutex::Bloqueo

Espera hasta que el objeto `Mutex` actual, o el objeto asociado con el identificador especificado, libere la exclusión mutua o el intervalo de tiempo de espera especificado haya transcurrido.

```cpp
SyncLock Lock(
   DWORD milliseconds = INFINITE
);

static SyncLock Lock(
   HANDLE h,
   DWORD milliseconds = INFINITE
);
```

### <a name="parameters"></a>Parámetros

*Milisegundos*<br/>
El intervalo de tiempo de espera, en milisegundos. El valor predeterminado es INFINITE, que espera indefinidamente.

*H*<br/>
El identificador `Mutex` de un objeto.

### <a name="return-value"></a>Valor devuelto

## <a name="mutexmutex"></a><a name="mutex"></a>Mutex::Mutex

Inicializa una nueva instancia de la clase `Mutex`.

```cpp
explicit Mutex(
   HANDLE h
);

Mutex(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
Un identificador, o una referencia rvalue a `Mutex` un identificador, a un objeto.

### <a name="remarks"></a>Observaciones

El primer constructor `Mutex` inicializa un objeto desde el identificador especificado. El segundo constructor `Mutex` inicializa un objeto desde el identificador especificado y, a `Mutex` continuación, mueve la propiedad de la exclusión mutua al objeto actual.

## <a name="mutexoperator"></a><a name="operator-assign"></a>Mutex::operador ?

Asigna (mueve) el `Mutex` objeto especificado `Mutex` al objeto actual.

```cpp
Mutex& operator=(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
Una referencia rvalue `Mutex` a un objeto.

### <a name="return-value"></a>Valor devuelto

Una referencia al `Mutex` objeto actual.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea la sección **Mover semántica** de Declarator de referencia de [valor R: &&](../../cpp/rvalue-reference-declarator-amp-amp.md).
