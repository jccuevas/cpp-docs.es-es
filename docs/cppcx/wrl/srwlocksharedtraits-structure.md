---
title: SRWLockSharedTraits (estructura)
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock method
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
ms.openlocfilehash: 0dc43d4b9c16145ed7a5abe03cddb598c59b1e94
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374297"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits (estructura)

Describe las características `SRWLock` comunes de la clase en modo de bloqueo compartido.

## <a name="syntax"></a>Sintaxis

```cpp
struct SRWLockSharedTraits;
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Nombre   | Descripción
------ | --------------------------------------------------------------------------
`Type` | Sinónimo de puntero a la clase [SRWLOCK.](srwlock-class.md)

### <a name="public-methods"></a>Métodos públicos

Nombre                                                     | Descripción
-------------------------------------------------------- | -----------------------------------------------------------------
[SRWLockSharedTraits::GetInvalidValue](#getinvalidvalue) | Recupera un `SRWLockSharedTraits` objeto que siempre no es válido.
[SRWLockSharedTraits::Unlock](#unlock)                   | Libera el control exclusivo `SRWLock` del objeto especificado.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SRWLockSharedTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="srwlocksharedtraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>SRWLockSharedTraits::GetInvalidValue

Recupera un `SRWLockSharedTraits` objeto que siempre no es válido.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valor devuelto

Identificador de `SRWLockSharedTraits` un objeto.

## <a name="srwlocksharedtraitsunlock"></a><a name="unlock"></a>SRWLockSharedTraits::Unlock

Libera el control exclusivo `SRWLock` del objeto especificado.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Parámetros

*srwlock*<br/>
Identificador de `SRWLock` un objeto.
