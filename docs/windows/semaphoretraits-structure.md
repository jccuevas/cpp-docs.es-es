---
title: SemaphoreTraits (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits
dev_langs:
- C++
helpviewer_keywords:
- SemaphoreTraits structure
ms.assetid: eddb8576-d063-409b-9201-cc87ca5d111e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5919b84a8b7b0b24588958198da89271d2a20119
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601825"
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits (estructura)

Define las características comunes de un **semáforo** objeto.

## <a name="syntax"></a>Sintaxis

```cpp
struct SemaphoreTraits : HANDLENullTraits;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[SemaphoreTraits::Unlock (método)](../windows/semaphoretraits-unlock-method.md)|Control de versiones de un recurso compartido.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`HANDLENullTraits`

`SemaphoreTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** handletraits

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Wrappers::HandleTraits (espacio de nombres)](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)