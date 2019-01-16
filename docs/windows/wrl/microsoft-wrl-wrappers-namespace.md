---
title: Microsoft::WRL::Wrappers (Espacio de nombres)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
ms.openlocfilehash: 953318e09c4c0d00748f2b6189615dbd66677a96
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337496"
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
|[CriticalSection (clase)](criticalsection-class.md)|Representa un objeto de sección crítica.|
|[Event (clase) (WRL)](event-class-wrl.md)|Representa un evento.|
|[HandleT (clase)](handlet-class.md)|Representa un identificador a un objeto.|
|[HString (clase)](hstring-class.md)|Proporciona compatibilidad para manipular los identificadores HSTRING.|
|[HStringReference (clase)](hstringreference-class.md)|Representa un objeto HSTRING que se crea a partir de una cadena existente.|
|[Mutex (clase)](mutex-class.md)|Representa un objeto de sincronización que controla de forma exclusiva un recurso compartido.|
|[RoInitializeWrapper (clase)](roinitializewrapper-class.md)|Inicializa el tiempo de ejecución de Windows.|
|[Semaphore (clase)](semaphore-class.md)|Representa un objeto de sincronización que controla un recurso compartido que puede admitir un número limitado de usuarios.|
|[SRWLock (clase)](srwlock-class.md)|Representa un bloqueo fino de lector/escritor.|

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Espacio de nombres**: Microsoft::WRL::Wrappers

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)