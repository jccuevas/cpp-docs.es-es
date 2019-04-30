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
ms.openlocfilehash: af567fd333854519df4543ad24084e52cda4d96e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383287"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits (estructura)

Describe las características comunes de la `SRWLock` clase en modo de bloqueo compartido.

## <a name="syntax"></a>Sintaxis

```cpp
struct SRWLockSharedTraits;
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Name   | Descripción
------ | --------------------------------------------------------------------------
`Type` | Sinónimo de un puntero a la [SRWLOCK](srwlock-class.md) clase.

### <a name="public-methods"></a>Métodos públicos

Name                                                     | Descripción
-------------------------------------------------------- | -----------------------------------------------------------------
[SRWLockSharedTraits::GetInvalidValue](#getinvalidvalue) | Recupera un `SRWLockSharedTraits` objeto que no siempre es válido.
[SRWLockSharedTraits::Unlock](#unlock)                   | Devuelve el control exclusivo del elemento especificado `SRWLock` objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SRWLockSharedTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres**: Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>SRWLockSharedTraits::GetInvalidValue

Recupera un `SRWLockSharedTraits` objeto que no siempre es válido.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valor devuelto

Un identificador para un `SRWLockSharedTraits` objeto.

## <a name="unlock"></a>SRWLockSharedTraits::Unlock

Devuelve el control exclusivo del elemento especificado `SRWLock` objeto.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Parámetros

*srwlock*<br/>
Un identificador para un `SRWLock` objeto.
