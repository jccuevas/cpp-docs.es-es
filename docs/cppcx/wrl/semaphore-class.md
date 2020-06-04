---
title: Semaphore (Clase)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Semaphore
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Semaphore class
- Microsoft::WRL::Wrappers::Semaphore::Lock method
- Microsoft::WRL::Wrappers::Semaphore::operator= operator
- Microsoft::WRL::Wrappers::Semaphore::Semaphore, constructor
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
ms.openlocfilehash: e017b1b6316c4b6d49563d9a543950ab28961d90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359356"
---
# <a name="semaphore-class"></a>Semaphore (Clase)

Representa un objeto de sincronización que controla un recurso compartido que puede admitir un número limitado de usuarios.

## <a name="syntax"></a>Sintaxis

```cpp
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>;
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Nombre       | Descripción
---------- | ------------------------------------------------------
`SyncLock` | Sinónimo de una clase que admite bloqueos sincrónicos.

### <a name="public-constructors"></a>Constructores públicos

Nombre                               | Descripción
---------------------------------- | ----------------------------------------------------
[Semáforo::Semaphore](#semaphore) | Inicializa una nueva instancia de la clase `Semaphore`.

### <a name="public-methods"></a>Métodos públicos

Nombre                     | Descripción
------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------
[Semáforo::Bloqueo](#lock) | Espera hasta que el objeto actual, o el objeto asociado con el identificador especificado, esté en el estado señalado o haya transcurrido el intervalo de tiempo de espera especificado.

### <a name="public-operators"></a>Operadores públicos

Nombre                                     | Descripción
---------------------------------------- | ---------------------------------------------------------------------------------------
[Semáforo::operador](#operator-assign) | Mueve el identificador especificado `Semaphore` de un `Semaphore` objeto al objeto actual.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Semaphore`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres:** Microsoft::WRL::Wrappers

## <a name="semaphorelock"></a><a name="lock"></a>Semáforo::Bloqueo

Espera hasta que el objeto `Semaphore` actual, o el objeto asociado con el identificador especificado, esté en el estado señalado o haya transcurrido el intervalo de tiempo de espera especificado.

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
Identificador de `Semaphore` un objeto.

### <a name="return-value"></a>Valor devuelto

Un tipo de datos `Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`

## <a name="semaphoreoperator"></a><a name="operator-assign"></a>Semáforo::operador

Mueve el identificador especificado `Semaphore` de un `Semaphore` objeto al objeto actual.

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
Rvalue-reference a `Semaphore` un objeto.

### <a name="return-value"></a>Valor devuelto

Una referencia al `Semaphore` objeto actual.

## <a name="semaphoresemaphore"></a><a name="semaphore"></a>Semáforo::Semaphore

Inicializa una nueva instancia de la clase `Semaphore`.

```cpp
explicit Semaphore(
   HANDLE h
);

WRL_NOTHROW Semaphore(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
Un identificador o una referencia `Semaphore` rvalue a un objeto.
