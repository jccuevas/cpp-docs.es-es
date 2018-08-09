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
ms.openlocfilehash: 5bfbd3418af731edf826debd9d6663095be706b8
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641524"
---
# <a name="synclocktislocked-method"></a>SyncLockT::IsLocked (Método)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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