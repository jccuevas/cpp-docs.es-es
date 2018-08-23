---
title: SRWLockSharedTraits (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
dev_langs:
- C++
helpviewer_keywords:
- SRWLockSharedTraits structure
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 50bcfc728a2f228e4fa8444fe41cc25c3ff449a2
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602251"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits (estructura)

Describe las características comunes de la `SRWLock` clase en modo de bloqueo compartido.

## <a name="syntax"></a>Sintaxis

```cpp
struct SRWLockSharedTraits;
```

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`Type`|Sinónimo de un puntero a la [SRWLOCK](../windows/srwlock-class.md) clase.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[SRWLockSharedTraits::GetInvalidValue (método)](../windows/srwlocksharedtraits-getinvalidvalue-method.md)|Recupera un **SRWLockSharedTraits** objeto que no siempre es válido.|
|[SRWLockSharedTraits::Unlock (método)](../windows/srwlocksharedtraits-unlock-method.md)|Devuelve el control exclusivo del elemento especificado `SRWLock` objeto.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SRWLockSharedTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** handletraits

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Wrappers::HandleTraits (espacio de nombres)](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)