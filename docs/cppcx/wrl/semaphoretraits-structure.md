---
title: SemaphoreTraits (estructura)
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock method
ms.assetid: eddb8576-d063-409b-9201-cc87ca5d111e
ms.openlocfilehash: 11719576c9fc7b23f4cd318ee1b3ed9ca3f5edaa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360739"
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits (estructura)

Define las características `Semaphore` comunes de un objeto.

## <a name="syntax"></a>Sintaxis

```cpp
struct SemaphoreTraits : HANDLENullTraits;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

Nombre                               | Descripción
---------------------------------- | --------------------------------------
[SemaphoreTraits::Desbloquear](#unlock) | Libera el control de un recurso compartido.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HANDLENullTraits`

`SemaphoreTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="semaphoretraitsunlock"></a><a name="unlock"></a>SemaphoreTraits::Desbloquear

Libera el control de un recurso compartido.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Parámetros

*H*<br/>
Controlar a `Semaphore` un objeto.

### <a name="remarks"></a>Observaciones

Si la operación de `Unlock()` desbloqueo no se realiza correctamente, emite un error que indica la causa del error.
