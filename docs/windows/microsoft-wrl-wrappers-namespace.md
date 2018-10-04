---
title: Wrappers Namespace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
dev_langs:
- C++
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2b1a63494e06ce3117e7e8fccd1d0cbca8cdb4d0
ms.sourcegitcommit: d1527eb2d50156bf923f2a32ec3af9efc7fc4304
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48250346"
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
|[Clase de eventos (WRL)](../windows/event-class-wrl.md)|Representa un evento.|
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