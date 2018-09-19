---
title: Trylockexclusive (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
dev_langs:
- C++
helpviewer_keywords:
- TryLockExclusive method
ms.assetid: 661e8b19-3058-4511-8742-c9fbb90412c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2ec8275b1db692410677276e762f79ccf23548cc
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606236"
---
# <a name="srwlocktrylockexclusive-method"></a>SRWLock::TryLockExclusive (Método)

Intenta adquirir un **SRWLock** objeto en modo exclusivo para el actual o especificada **SRWLock** objeto. Si la llamada se realiza correctamente, el subproceso de llamada toma posesión del bloqueo.

## <a name="syntax"></a>Sintaxis

```cpp
SyncLockExclusive TryLockExclusive();

static SyncLockExclusive TryLockExclusive(
   _In_ SRWLOCK* lock
);
```

### <a name="parameters"></a>Parámetros

*lock*  
Puntero a un **SRWLock** objeto.

## <a name="return-value"></a>Valor devuelto

Si es correcto, un **SRWLock** objeto en modo exclusivo y el subproceso de llamada toma posesión del bloqueo. En caso contrario, un **SRWLock** objeto cuyo estado no es válido.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[SRWLock (clase)](../windows/srwlock-class.md)