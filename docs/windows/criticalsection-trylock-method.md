---
title: TryLock (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
dev_langs:
- C++
helpviewer_keywords:
- TryLock method
ms.assetid: 504bb87c-2cd0-4f54-b458-b3efb9789053
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 382dbdd2d0816d6ab0846acd0f8c164cd542114f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42575846"
---
# <a name="criticalsectiontrylock-method"></a>CriticalSection::TryLock (Método)

Intenta entrar en una sección crítica sin bloquear. Si la llamada se realiza correctamente, el subproceso de llamada toma posesión de la sección crítica.

## <a name="syntax"></a>Sintaxis

```cpp
SyncLock TryLock();

static SyncLock TryLock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parámetros

*CS*  
Un objeto de sección crítica especificado por el usuario.

## <a name="return-value"></a>Valor devuelto

Un valor distinto de cero si la sección crítica está escrita correctamente o el subproceso actual ya posee la sección crítica. Cero si otro subproceso ya posee la sección crítica.

## <a name="remarks"></a>Comentarios

La primera **TryLock** el objeto de sección crítica actual afecta a la función. El segundo **TryLock** función afecta a una sección crítica especificado por el usuario.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[CriticalSection (clase)](../windows/criticalsection-class.md)