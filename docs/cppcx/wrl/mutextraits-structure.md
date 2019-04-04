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
ms.openlocfilehash: 9bc4071e5699610a664cbf01ca3e7d36d7effc5e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785843"
---
# <a name="mutextraits-structure"></a>MutexTraits (estructura)

Define las características comunes de la [Mutex](mutex-class.md) clase.

## <a name="syntax"></a>Sintaxis

```cpp
struct MutexTraits : HANDLENullTraits;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

Name                           | Descripción
------------------------------ | ------------------------------------------------
[MutexTraits::Unlock](#unlock) | Devuelve el control exclusivo de un recurso compartido.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HANDLENullTraits`

`MutexTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres**: Microsoft::WRL::Wrappers::HandleTraits

## <a name="unlock"></a>Mutextraits (método)

Devuelve el control exclusivo de un recurso compartido.

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Parámetros

*h*<br/>
Identificador de un objeto de exclusión mutua.
