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
ms.openlocfilehash: 80c744431fe7df32be705fcf91eef0a8691b8fa4
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015803"
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