---
title: MutexTraits (estructura)
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock method
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
ms.openlocfilehash: 6d4ba08ab1884e8584b0e98e931d2d63cdac5aec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371250"
---
# <a name="mutextraits-structure"></a>MutexTraits (estructura)

Define las características comunes de la clase [Mutex.](mutex-class.md)

## <a name="syntax"></a>Sintaxis

```cpp
struct MutexTraits : HANDLENullTraits;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

Nombre                           | Descripción
------------------------------ | ------------------------------------------------
[MutexTraits::Unlock](#unlock) | Libera el control exclusivo de un recurso compartido.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HANDLENullTraits`

`MutexTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="mutextraitsunlock-method"></a><a name="unlock"></a>MutexTraits::Método de desbloqueo

Libera el control exclusivo de un recurso compartido.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
Controlar a un objeto de exclusión mutua.
