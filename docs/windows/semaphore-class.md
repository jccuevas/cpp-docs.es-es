---
title: Clase de semáforo | Microsoft Docs
ms.custom: ''
ms.date: 09/25/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Semaphore
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Semaphore class
- Microsoft::WRL::Wrappers::Semaphore::Lock method
- Microsoft::WRL::Wrappers::Semaphore::operator= operator
- Microsoft::WRL::Wrappers::Semaphore::Semaphore, constructor
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 269b3229a0755e88d55fc4fa5d14b843345ccc44
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234459"
---
# <a name="semaphore-class"></a>Semaphore (clase)

Representa un objeto de sincronización que controla un recurso compartido que puede admitir un número limitado de usuarios.

## <a name="syntax"></a>Sintaxis

```cpp
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Name       | Descripción
---------- | ------------------------------------------------------
`SyncLock` | Un sinónimo de una clase que admita bloqueos sincrónicos.

### <a name="public-constructors"></a>Constructores públicos

Name                               | Descripción
---------------------------------- | ----------------------------------------------------
[Semaphore](#semaphore) | Inicializa una nueva instancia de la clase `Semaphore`.

### <a name="public-methods"></a>Métodos públicos

Name                     | Descripción
------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------
[Semaphore](#lock) | Espera a que el objeto actual o el objeto asociado con el identificador especificado, está en el estado señalado o ha transcurrido el intervalo de tiempo de espera especificado.

### <a name="public-operators"></a>Operadores públicos

Name                                     | Descripción
---------------------------------------- | ---------------------------------------------------------------------------------------
[Semaphore:: operator =](#operator-assign) | Mueve el identificador especificado de un `Semaphore` el objeto actual `Semaphore` objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Semaphore`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="lock"></a>Semaphore

Espera hasta que el objeto actual, o la `Semaphore` objeto asociado con el identificador especificado, está en el estado señalado o ha transcurrido el intervalo de tiempo de espera especificado.

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

*milisegundos*<br/>
El intervalo de tiempo de espera, en milisegundos. El valor predeterminado es infinito, que espera indefinidamente.

*h*<br/>
Un identificador para un `Semaphore` objeto.

### <a name="return-value"></a>Valor devuelto

`Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`.

## <a name="operator-assign"></a>Semaphore:: operator =

Mueve el identificador especificado de un `Semaphore` el objeto actual `Semaphore` objeto.

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Parámetros

*h*<br/>
Referencia de valor r a un `Semaphore` objeto.

### <a name="return-value"></a>Valor devuelto

Una referencia a la actual `Semaphore` objeto.

## <a name="semaphore"></a>Semaphore

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

*h*<br/>
Un identificador o una referencia rvalue para un `Semaphore` objeto.
