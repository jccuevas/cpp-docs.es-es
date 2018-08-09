---
title: Método Asyncbase | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Cancel
dev_langs:
- C++
helpviewer_keywords:
- Cancel method
ms.assetid: 8bfebc63-3848-4629-bc89-aa538ed7e7ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 439a118bbea5adce4c306298e573bed85da26291
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641909"
---
# <a name="asyncbasecancel-method"></a>AsyncBase::Cancel (Método)
Cancela una operación asincrónica.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
STDMETHOD(  
   Cancel  
)(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 De forma predeterminada, siempre devuelve S_OK.  
  
## <a name="remarks"></a>Comentarios  
 **Cancel()** es una implementación predeterminada de `IAsyncInfo::Cancel`, y no se realiza ningún trabajo real. Para cancelar realmente una operación asincrónica, invalidar el `OnCancel()` método virtual puro.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [AsyncBase (clase)](../windows/asyncbase-class.md)