---
title: Método Srwlocksharedtraits | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 33cdead9-1900-4094-b18e-38fcf1a0bd28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e00b898fc60953896a9c0d2b7a124e195d3bcbf1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593173"
---
# <a name="srwlocksharedtraitsunlock-method"></a>SRWLockSharedTraits::Unlock (Método)

Devuelve el control exclusivo del elemento especificado `SRWLock` objeto.

## <a name="syntax"></a>Sintaxis

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Parámetros

*SRWLOCK*  
Un identificador para un `SRWLock` objeto.

## <a name="return-value"></a>Valor devuelto

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** handletraits

## <a name="see-also"></a>Vea también

[SRWLockSharedTraits (estructura)](../windows/srwlocksharedtraits-structure.md)