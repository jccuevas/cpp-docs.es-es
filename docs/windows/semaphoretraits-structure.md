---
title: SemaphoreTraits (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock method
ms.assetid: eddb8576-d063-409b-9201-cc87ca5d111e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 553d0cbb69bcf3167974cb42abb26f4aae04bfb3
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234143"
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits (estructura)

Define las características comunes de un `Semaphore` objeto.

## <a name="syntax"></a>Sintaxis

```cpp
struct SemaphoreTraits : HANDLENullTraits;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

Name                               | Descripción
---------------------------------- | --------------------------------------
[Semaphoretraits](#unlock) | Control de versiones de un recurso compartido.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HANDLENullTraits`

`SemaphoreTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** handletraits

## <a name="unlock"></a>Semaphoretraits

Control de versiones de un recurso compartido.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Parámetros

*h*<br/>
Identificador de un `Semaphore` objeto.

### <a name="remarks"></a>Comentarios

Si la operación de desbloqueo se realiza correctamente, `Unlock()` emite un error que indica la causa del error.
