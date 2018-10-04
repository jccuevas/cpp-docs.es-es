---
title: SRWLockSharedTraits (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock method
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5cfebfd1a6ccb1f243b534c9693a4402de574f17
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48233685"
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
`Type` | Sinónimo de un puntero a la [SRWLOCK](../windows/srwlock-class.md) clase.

### <a name="public-methods"></a>Métodos públicos

Name                                                     | Descripción
-------------------------------------------------------- | -----------------------------------------------------------------
[Srwlocksharedtraits](#getinvalidvalue) | Recupera un `SRWLockSharedTraits` objeto que no siempre es válido.
[Srwlocksharedtraits](#unlock)                   | Devuelve el control exclusivo del elemento especificado `SRWLock` objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SRWLockSharedTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** handletraits

## <a name="getinvalidvalue"></a>Srwlocksharedtraits

Recupera un `SRWLockSharedTraits` objeto que no siempre es válido.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valor devuelto

Un identificador para un `SRWLockSharedTraits` objeto.

## <a name="unlock"></a>Srwlocksharedtraits

Devuelve el control exclusivo del elemento especificado `SRWLock` objeto.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Parámetros

*SRWLOCK*<br/>
Un identificador para un `SRWLock` objeto.
