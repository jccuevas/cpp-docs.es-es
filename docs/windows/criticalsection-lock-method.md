---
title: Método CriticalSection | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 37cb184c-e13c-49ef-b6a0-13908a956414
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4fedde29441c9c14b68dec5cff998be57d216e29
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607665"
---
# <a name="criticalsectionlock-method"></a>CriticalSection::Lock (Método)

Espera a que la propiedad del objeto especificado de sección crítica. La función devuelve cuando el subproceso de llamada se concede la propiedad.

## <a name="syntax"></a>Sintaxis

```cpp
SyncLock Lock();

   static SyncLock Lock(
   _In_ CRITICAL_SECTION* cs
);
```

### <a name="parameters"></a>Parámetros

*CS*  
Un objeto de sección crítica especificado por el usuario.

## <a name="return-value"></a>Valor devuelto

Un objeto de bloqueo que puede usarse para desbloquear la sección crítica actual.

## <a name="remarks"></a>Comentarios

La primera **bloqueo** el objeto de sección crítica actual afecta a la función. El segundo **bloqueo** función afecta a una sección crítica especificado por el usuario.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[CriticalSection (clase)](../windows/criticalsection-class.md)