---
title: Método Synclockwithstatust | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
dev_langs:
- C++
helpviewer_keywords:
- IsLocked method
ms.assetid: e1b75b7b-c145-471a-aa5d-71abf31f5990
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d70a2c316f9e7994292f3dc29cef5bce993778ad
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595068"
---
# <a name="synclockwithstatustislocked-method"></a>SyncLockWithStatusT::IsLocked (Método)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
bool IsLocked() const;
```

## <a name="remarks"></a>Comentarios

Indica si el actual **SyncLockWithStatusT** objeto posee un recurso; es decir, el **SyncLockWithStatusT** objeto es *bloqueado*.

## <a name="return-value"></a>Valor devuelto

**True** si el **SyncLockWithStatusT** objeto está bloqueado; en caso contrario, **false**.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[SyncLockWithStatusT (clase)](../windows/synclockwithstatust-class.md)