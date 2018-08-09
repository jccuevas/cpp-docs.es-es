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
ms.openlocfilehash: 36c3f76e3fc137458acddacd834563d845057a24
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646580"
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