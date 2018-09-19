---
title: Miembro de datos Status_ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::status_
dev_langs:
- C++
helpviewer_keywords:
- status_ data member
ms.assetid: 466fa336-b5ff-4d43-8efd-1e87e5fddf88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d4a9a65e7ba45d38084d1695932c3897de583f49
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42610032"
---
# <a name="synclockwithstatuststatus-data-member"></a>SyncLockWithStatusT::status_ (Miembro de datos)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
DWORD status_;
```

## <a name="remarks"></a>Comentarios

Contiene el resultado de la operación de espera subyacente después de una operación de bloqueo en un objeto basado en la actual **SyncLockWithStatusT** objeto.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[SyncLockWithStatusT (clase)](../windows/synclockwithstatust-class.md)