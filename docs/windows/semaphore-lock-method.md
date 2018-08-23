---
title: Método Semaphore | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 0eef6ede-dc7d-4f09-a6c8-2f7d39d65bfa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 47925bcc647d253775e4dd61f6a7f5d5fb586dde
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599288"
---
# <a name="semaphorelock-method"></a>Semaphore::Lock (Método)

Espera hasta que el objeto actual, o la **semáforo** objeto asociado con el identificador especificado, está en el estado señalado o ha transcurrido el intervalo de tiempo de espera especificado.

## <a name="syntax"></a>Sintaxis

```cpp
SyncLock Lock(
   DWORD milliseconds = INFINITE
);

static SyncLock Lock(
   HANDLE h,
   DWORD milliseconds = INFINITE
);
```

### <a name="parameters"></a>Parámetros

*milisegundos*  
El intervalo de tiempo de espera, en milisegundos. El valor predeterminado es infinito, que espera indefinidamente.

*h*  
Un identificador para un **semáforo** objeto.

## <a name="return-value"></a>Valor devuelto

`Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[Semaphore (clase)](../windows/semaphore-class.md)