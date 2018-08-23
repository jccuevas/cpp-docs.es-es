---
title: CurrentStatus (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::CurrentStatus
dev_langs:
- C++
helpviewer_keywords:
- CurrentStatus method
ms.assetid: 26ee4c4a-6525-4a5f-b49c-3ca40c365eb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 193f4d26f7e163707092f3d0bc8f981a02611a22
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603707"
---
# <a name="asyncbasecurrentstatus-method"></a>AsyncBase::CurrentStatus (Método)

Recupera el estado de la operación asincrónica actual.

## <a name="syntax"></a>Sintaxis

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>Parámetros

*status*  
La ubicación donde esta operación almacena el estado actual.

## <a name="remarks"></a>Comentarios

Esta operación es segura para subprocesos.

## <a name="requirements"></a>Requisitos

**Encabezado:** async.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[AsyncBase (clase)](../windows/asyncbase-class.md)  
[AsyncStatusInternal (enumeración)](../windows/asyncstatusinternal-enumeration.md)