---
title: SRWLockExclusiveTraits (estructura)
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock method
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
ms.openlocfilehash: eb7b30915d6061e8470601df33fecec310d1bbca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374307"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits (estructura)

Describe las características `SRWLock` comunes de la clase en modo de bloqueo exclusivo.

## <a name="syntax"></a>Sintaxis

```cpp
struct SRWLockExclusiveTraits;
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Nombre   | Descripción
------ | --------------------------------------------------------------------------
`Type` | Sinónimo de puntero a la clase [SRWLOCK.](srwlock-class.md)

### <a name="public-methods"></a>Métodos públicos

Nombre                                                        | Descripción
----------------------------------------------------------- | --------------------------------------------------------------------
[SRWLockExclusiveTraits::GetInvalidValue](#getinvalidvalue) | Recupera un `SRWLockExclusiveTraits` objeto que siempre no es válido.
[SRWLockExclusiveTraits::Unlock](#unlock)                   | Libera el control exclusivo `SRWLock` del objeto especificado.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SRWLockExclusiveTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="srwlockexclusivetraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>SRWLockExclusiveTraits::GetInvalidValue

Recupera un `SRWLockExclusiveTraits` objeto que siempre no es válido.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valor devuelto

Objeto `SRWLockExclusiveTraits` vacío.

## <a name="srwlockexclusivetraitsunlock"></a><a name="unlock"></a>SRWLockExclusiveTraits::Unlock

Libera el control exclusivo `SRWLock` del objeto especificado.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Parámetros

*srwlock*<br/>
Controlar un `SRWLock` objeto.
