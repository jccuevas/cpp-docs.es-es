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
ms.openlocfilehash: 316dfea16aa129dcaff42424bef46305d2dd56b4
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461434"
---
# <a name="asyncbasecurrentstatus-method"></a>AsyncBase::CurrentStatus (Método)
Recupera el estado de la operación asincrónica actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
inline void CurrentStatus(  
   Details::AsyncStatusInternal *status  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
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