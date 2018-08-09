---
title: Get_status (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_Status
dev_langs:
- C++
helpviewer_keywords:
- get_Status method
ms.assetid: 9823ecb9-212e-471d-b76f-7b8f21208905
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b49e7cbd30445250bdf0710973ba65e47823b36c
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652258"
---
# <a name="asyncbasegetstatus-method"></a>AsyncBase::get_Status (Método)
Recupera un valor que indica el estado de la operación asincrónica.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
STDMETHOD(  
   get_Status  
)(AsyncStatus *status) override;  
```  
  
### <a name="parameters"></a>Parámetros  
 *status*  
 La ubicación donde se almacenará el estado. Para obtener más información, consulte `Windows::Foundation::AsyncStatus` enumeración.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, E_ILLEGAL_METHOD_CALL.  
  
## <a name="remarks"></a>Comentarios  
 Este método implementa `IAsyncInfo::get_Status`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [AsyncBase (clase)](../windows/asyncbase-class.md)