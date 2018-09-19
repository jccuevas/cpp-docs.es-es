---
title: Método Synclockt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked
dev_langs:
- C++
helpviewer_keywords:
- IsLocked method
ms.assetid: a81fea43-f99a-4708-812a-7fd6af500d3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ca4391539e4f6987431e8b9b036053db02218007
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593060"
---
# <a name="synclocktislocked-method"></a>SyncLockT::IsLocked (Método)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
bool IsLocked() const;
```

## <a name="return-value"></a>Valor devuelto

**True** si el **SyncLockT** objeto está bloqueado; en caso contrario, **false**.

## <a name="remarks"></a>Comentarios

Indica si el actual **SyncLockT** objeto posee un recurso; es decir, el **SyncLockT** objeto es *bloqueado*.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[SyncLockT (clase)](../windows/synclockt-class.md)