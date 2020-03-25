---
title: Microsoft::WRL::Wrappers (Espacio de nombres)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
ms.openlocfilehash: ece26b3f9928d44a593de830cf8a25c57e4c2d89
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213751"
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers (Espacio de nombres)

Define los tipos de contenedor de adquisición de recursos (RAII) que simplifican la administración de la duración de los objetos, las cadenas y los identificadores.

## <a name="syntax"></a>Sintaxis

```cpp
namespace Microsoft::WRL::Wrappers;
```

## <a name="members"></a>Members

### <a name="typedefs"></a>Typedefs

|Nombre|Descripción|
|----------|-----------------|
|`FileHandle`|`HandleT<HandleTraits::FileHandleTraits>`|

### <a name="classes"></a>Clases

|Nombre|Descripción|
|----------|-----------------|
|[CriticalSection (clase)](criticalsection-class.md)|Representa un objeto de sección crítica.|
|[Event (clase) (WRL)](event-class-wrl.md)|Representa un evento.|
|[HandleT (clase)](handlet-class.md)|Representa un identificador de un objeto.|
|[HString (clase)](hstring-class.md)|Proporciona compatibilidad para manipular los identificadores de HSTRING.|
|[HStringReference (clase)](hstringreference-class.md)|Representa un HSTRING que se crea a partir de una cadena existente.|
|[Mutex (clase)](mutex-class.md)|Representa un objeto de sincronización que controla exclusivamente un recurso compartido.|
|[RoInitializeWrapper (clase)](roinitializewrapper-class.md)|Inicializa el Windows Runtime.|
|[Semaphore (clase)](semaphore-class.md)|Representa un objeto de sincronización que controla un recurso compartido que puede admitir un número limitado de usuarios.|
|[SRWLock (clase)](srwlock-class.md)|Representa un bloqueo delgado de lector/escritor.|

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers. h

**Espacio de nombres:** Microsoft:: WRL:: wrappers

## <a name="see-also"></a>Consulte también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)
