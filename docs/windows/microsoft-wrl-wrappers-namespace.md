---
title: Microsoft::WRL::Wrappers (Espacio de nombres)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
ms.openlocfilehash: eac85d10351a141ce561da4272d033644128608f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535491"
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers (Espacio de nombres)

Define los tipos de contenedor de recursos adquisición es inicialización (RAII) que simplifican la administración de la duración de objetos, cadenas e identificadores.

## <a name="syntax"></a>Sintaxis

```cpp
namespace Microsoft::WRL::Wrappers;
```

## <a name="members"></a>Miembros

### <a name="typedefs"></a>Typedefs

|Name|Descripción|
|----------|-----------------|
|`FileHandle`|`HandleT<HandleTraits::FileHandleTraits>`|

### <a name="classes"></a>Clases

|Name|Descripción|
|----------|-----------------|
|[CriticalSection (clase)](../windows/criticalsection-class.md)|Representa un objeto de sección crítica.|
|[Event (clase) (WRL)](../windows/event-class-wrl.md)|Representa un evento.|
|[HandleT (clase)](../windows/handlet-class.md)|Representa un identificador a un objeto.|
|[HString (clase)](../windows/hstring-class.md)|Proporciona compatibilidad para manipular los identificadores HSTRING.|
|[HStringReference (clase)](../windows/hstringreference-class.md)|Representa un objeto HSTRING que se crea a partir de una cadena existente.|
|[Mutex (clase)](../windows/mutex-class.md)|Representa un objeto de sincronización que controla de forma exclusiva un recurso compartido.|
|[RoInitializeWrapper (clase)](../windows/roinitializewrapper-class.md)|Inicializa el tiempo de ejecución de Windows.|
|[Semaphore (clase)](../windows/semaphore-class.md)|Representa un objeto de sincronización que controla un recurso compartido que puede admitir un número limitado de usuarios.|
|[SRWLock (clase)](../windows/srwlock-class.md)|Representa un bloqueo fino de lector/escritor.|

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)