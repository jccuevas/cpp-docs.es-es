---
title: Método Semaphoretraits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 4e0ea808-b70d-43f7-81ef-998c3b34e3a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e993c58ea6fc84e0b4001b488632858e5251d67b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42583976"
---
# <a name="semaphoretraitsunlock-method"></a>SemaphoreTraits::Unlock (Método)

Control de versiones de un recurso compartido.

## <a name="syntax"></a>Sintaxis

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>Parámetros

*h*  
Identificador de un **semáforo** objeto.

## <a name="remarks"></a>Comentarios

Si la operación de desbloqueo se realiza correctamente, **Unlock()** emite un error que indica la causa del error.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** handletraits

## <a name="see-also"></a>Vea también

[SemaphoreTraits (estructura)](../windows/semaphoretraits-structure.md)