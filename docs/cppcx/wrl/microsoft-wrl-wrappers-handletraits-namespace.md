---
title: Microsoft::WRL::Wrappers::HandleTraits (Espacio de nombres)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
ms.openlocfilehash: 55e1dfea2d4075a5a37b9654a70e9ce74383ea53
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785982"
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Microsoft::WRL::Wrappers::HandleTraits (Espacio de nombres)

Describe las características de los tipos de recursos basado en identificador común.

## <a name="syntax"></a>Sintaxis

```cpp
namespace Microsoft::WRL::Wrappers::HandleTraits;
```

## <a name="members"></a>Miembros

### <a name="structures"></a>Estructuras

|Name|Descripción|
|----------|-----------------|
|[CriticalSectionTraits (estructura)](criticalsectiontraits-structure.md)|Se especializa un `CriticalSection` objeto sea compatible con una sección crítica no válida o una función para liberar una sección crítica.|
|[EventTraits (estructura)](eventtraits-structure.md)|Define las características de un `Event` identificador de clase.|
|[FileHandleTraits (estructura)](filehandletraits-structure.md)|Define las características de un identificador de archivo.|
|[HANDLENullTraits (estructura)](handlenulltraits-structure.md)|Define las características comunes de un identificador sin inicializar.|
|[HANDLETraits (estructura)](handletraits-structure.md)|Define las características comunes de un controlador.|
|[MutexTraits (estructura)](mutextraits-structure.md)|Define las características comunes de la [Mutex](mutex-class.md) clase.|
|[SemaphoreTraits (estructura)](semaphoretraits-structure.md)|Define las características comunes de un objeto semáforo.|
|[SRWLockExclusiveTraits (estructura)](srwlockexclusivetraits-structure.md)|Describe las características comunes de la `SRWLock` clase en modo de bloqueo exclusivo.|
|[SRWLockSharedTraits (estructura)](srwlocksharedtraits-structure.md)|Describe las características comunes de la `SRWLock` clase en modo de bloqueo compartido.|

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres**: Microsoft::WRL::Wrappers

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Wrappers (espacio de nombres)](microsoft-wrl-wrappers-namespace.md)