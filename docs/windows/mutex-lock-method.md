---
title: Método Mutex | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 61d95072-b690-441e-a080-0bf94a733141
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 38bd11620f8d403bbd1667ab6fa4f3f827362c88
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600878"
---
# <a name="mutexlock-method"></a>Mutex::Lock (Método)

Espera hasta que el objeto actual, o la **Mutex** objeto asociado con el identificador especificado, las versiones que ha transcurrido el intervalo de tiempo de espera especificado o de la exclusión mutua.

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
El identificador de un **Mutex** objeto.

## <a name="return-value"></a>Valor devuelto

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también
[Mutex (clase)](../windows/mutex-class1.md)