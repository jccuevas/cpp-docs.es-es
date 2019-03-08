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
ms.openlocfilehash: 25249b8823b8c182133e85aa4cd07d38f5874cf2
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337674"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits (estructura)

Describe las características comunes de la `SRWLock` clase en modo de bloqueo exclusivo.

## <a name="syntax"></a>Sintaxis

```cpp
struct SRWLockExclusiveTraits;
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

Name   | Descripción
------ | --------------------------------------------------------------------------
`Type` | Sinónimo de un puntero a la [SRWLOCK](srwlock-class.md) clase.

### <a name="public-methods"></a>Métodos públicos

Name                                                        | Descripción
----------------------------------------------------------- | --------------------------------------------------------------------
[SRWLockExclusiveTraits::GetInvalidValue](#getinvalidvalue) | Recupera un `SRWLockExclusiveTraits` objeto que no siempre es válido.
[SRWLockExclusiveTraits::Unlock](#unlock)                   | Devuelve el control exclusivo del elemento especificado `SRWLock` objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SRWLockExclusiveTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres**: Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>SRWLockExclusiveTraits::GetInvalidValue

Recupera un `SRWLockExclusiveTraits` objeto que no siempre es válido.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valor devuelto

Objeto `SRWLockExclusiveTraits` vacío.

## <a name="unlock"></a>SRWLockExclusiveTraits::Unlock

Devuelve el control exclusivo del elemento especificado `SRWLock` objeto.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Parámetros

*srwlock*<br/>
Identificador de un `SRWLock` objeto.
