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
ms.openlocfilehash: 93de43ac7e5314501d0391e2cde862ba32be0b4b
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785930"
---
# <a name="mutex-class"></a>Mutex (Clase)

Representa un objeto de sincronización que controla de forma exclusiva un recurso compartido.

## <a name="syntax"></a>Sintaxis

```cpp
class Mutex : public HandleT<HandleTraits::MutexTraits>;
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Name       | Descripción
---------- | ------------------------------------------------------
`SyncLock` | Un sinónimo de una clase que admita bloqueos sincrónicos.

### <a name="public-constructor"></a>Constructor público

Name                   | Descripción
---------------------- | ------------------------------------------------
[Mutex::Mutex](#mutex) | Inicializa una nueva instancia de la clase `Mutex`.

### <a name="public-members"></a>Miembros públicos

Name                 | Descripción
-------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------
[Mutex::Lock](#lock) | Espera hasta que el objeto actual, o la `Mutex` objeto asociado con el identificador especificado, las versiones que ha transcurrido el intervalo de tiempo de espera especificado o de la exclusión mutua.

### <a name="public-operator"></a>Operador público

Name                                 | Descripción
------------------------------------ | ---------------------------------------------------------------------------
[Mutex::operator=](#operator-assign) | Asigna (mueve) especificado `Mutex` el objeto actual `Mutex` objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Mutex`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres**: Microsoft::WRL::Wrappers

## <a name="lock"></a>Mutex::Lock

Espera hasta que el objeto actual, o la `Mutex` objeto asociado con el identificador especificado, las versiones que ha transcurrido el intervalo de tiempo de espera especificado o de la exclusión mutua.

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

*milliseconds*<br/>
El intervalo de tiempo de espera, en milisegundos. El valor predeterminado es infinito, que espera indefinidamente.

*h*<br/>
El identificador de un `Mutex` objeto.

### <a name="return-value"></a>Valor devuelto

## <a name="mutex"></a>Mutex::Mutex

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

*h*<br/>
Un identificador o una referencia rvalue a un identificador, para un `Mutex` objeto.

### <a name="remarks"></a>Comentarios

El primer constructor inicializa un `Mutex` objeto a partir del identificador especificado. El segundo constructor inicializa un `Mutex` el objeto en el identificador especificado y, a continuación, mueve la propiedad del mutex actual `Mutex` objeto.

## <a name="operator-assign"></a>Mutex::operator=

Asigna (mueve) especificado `Mutex` el objeto actual `Mutex` objeto.

```cpp
Mutex& operator=(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Parámetros

*h*<br/>
Una referencia rvalue para un `Mutex` objeto.

### <a name="return-value"></a>Valor devuelto

Una referencia a la actual `Mutex` objeto.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte el **mover semántica** sección de [declarador de referencia Rvalue: & &](../../cpp/rvalue-reference-declarator-amp-amp.md).
