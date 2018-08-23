---
title: Trylockshared (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared
dev_langs:
- C++
helpviewer_keywords:
- TryLockShared method
ms.assetid: 10cc198d-39a0-4d18-aa78-706744948668
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bcad153145432997841753828b3b01b728ff365d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42608178"
---
# <a name="srwlocktrylockshared-method"></a>SRWLock::TryLockShared (Método)

Intenta adquirir un **SRWLock** objeto en modo compartido para el actual o especificada **SRWLock** objeto.

## <a name="syntax"></a>Sintaxis

```cpp
WRL_NOTHROW SyncLockShared TryLockShared();
WRL_NOTHROW static SyncLockShared TryLockShared(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parámetros

*lock*  
Puntero a un **SRWLock** objeto.

## <a name="return-value"></a>Valor devuelto

Si es correcto, un **SRWLock** objeto en modo compartido y el subproceso de llamada toma posesión del bloqueo. En caso contrario, un **SRWLock** objeto cuyo estado no es válido.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[SRWLock (clase)](../windows/srwlock-class.md)