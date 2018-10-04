---
title: SRWLockExclusiveTraits (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock method
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7737c802634b618b9ea363c231a44d9381ad30ae
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235170"
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
`Type` | Sinónimo de un puntero a la [SRWLOCK](../windows/srwlock-class.md) clase.

### <a name="public-methods"></a>Métodos públicos

Name                                                        | Descripción
----------------------------------------------------------- | --------------------------------------------------------------------
[Srwlockexclusivetraits](#getinvalidvalue) | Recupera un `SRWLockExclusiveTraits` objeto que no siempre es válido.
[Srwlockexclusivetraits](#unlock)                   | Devuelve el control exclusivo del elemento especificado `SRWLock` objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SRWLockExclusiveTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** handletraits

## <a name="getinvalidvalue"></a>Srwlockexclusivetraits

Recupera un `SRWLockExclusiveTraits` objeto que no siempre es válido.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valor devuelto

Objeto `SRWLockExclusiveTraits` vacío.

## <a name="unlock"></a>Srwlockexclusivetraits

Devuelve el control exclusivo del elemento especificado `SRWLock` objeto.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Parámetros

*SRWLOCK*<br/>
Identificador de un `SRWLock` objeto.
