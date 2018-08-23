---
title: Handletraits Namespace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
dev_langs:
- C++
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 683759c3bf0b2152ee6fadbb638cd2398daecccd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42586134"
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
|[CriticalSectionTraits (estructura)](../windows/criticalsectiontraits-structure.md)|Se especializa un `CriticalSection` objeto sea compatible con una sección crítica no válida o una función para liberar una sección crítica.|
|[EventTraits (estructura)](../windows/eventtraits-structure.md)|Define las características de un `Event` identificador de clase.|
|[FileHandleTraits (estructura)](../windows/filehandletraits-structure.md)|Define las características de un identificador de archivo.|
|[HANDLENullTraits (estructura)](../windows/handlenulltraits-structure.md)|Define las características comunes de un identificador sin inicializar.|
|[HANDLETraits (estructura)](../windows/handletraits-structure.md)|Define las características comunes de un controlador.|
|[MutexTraits (estructura)](../windows/mutextraits-structure.md)|Define las características comunes de la [Mutex](../windows/mutex-class1.md) clase.|
|[SemaphoreTraits (estructura)](../windows/semaphoretraits-structure.md)|Define las características comunes de un objeto semáforo.|
|[SRWLockExclusiveTraits (estructura)](../windows/srwlockexclusivetraits-structure.md)|Describe las características comunes de la `SRWLock` clase en modo de bloqueo exclusivo.|
|[SRWLockSharedTraits (estructura)](../windows/srwlocksharedtraits-structure.md)|Describe las características comunes de la `SRWLock` clase en modo de bloqueo compartido.|

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Wrappers (espacio de nombres)](../windows/microsoft-wrl-wrappers-namespace.md)