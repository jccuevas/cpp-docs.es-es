---
title: Microsoft::WRL::Wrappers::HandleTraits (Espacio de nombres)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
ms.openlocfilehash: b19cc426fc7c1b4fc6ec0638730d59998f8c108a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213738"
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Microsoft::WRL::Wrappers::HandleTraits (Espacio de nombres)

Describe las características de los tipos de recursos basados en el controlador común.

## <a name="syntax"></a>Sintaxis

```cpp
namespace Microsoft::WRL::Wrappers::HandleTraits;
```

## <a name="members"></a>Members

### <a name="structures"></a>Estructuras

|Nombre|Descripción|
|----------|-----------------|
|[CriticalSectionTraits (estructura)](criticalsectiontraits-structure.md)|Especializa un objeto `CriticalSection` para admitir una sección crítica no válida o una función para liberar una sección crítica.|
|[EventTraits (estructura)](eventtraits-structure.md)|Define las características de un identificador de clase `Event`.|
|[FileHandleTraits (estructura)](filehandletraits-structure.md)|Define las características de un identificador de archivo.|
|[HANDLENullTraits (estructura)](handlenulltraits-structure.md)|Define las características comunes de un identificador no inicializado.|
|[HANDLETraits (estructura)](handletraits-structure.md)|Define las características comunes de un identificador.|
|[MutexTraits (estructura)](mutextraits-structure.md)|Define las características comunes de la clase [Mutex](mutex-class.md) .|
|[SemaphoreTraits (estructura)](semaphoretraits-structure.md)|Define las características comunes de un objeto Semaphore.|
|[SRWLockExclusiveTraits (estructura)](srwlockexclusivetraits-structure.md)|Describe las características comunes de la clase `SRWLock` en modo de bloqueo exclusivo.|
|[SRWLockSharedTraits (estructura)](srwlocksharedtraits-structure.md)|Describe las características comunes de la clase `SRWLock` en el modo de bloqueo compartido.|

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers. h

**Espacio de nombres:** Microsoft:: WRL:: wrappers

## <a name="see-also"></a>Consulte también

[Microsoft::WRL::Wrappers (espacio de nombres)](microsoft-wrl-wrappers-namespace.md)
