---
title: Método Asyncbase | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Start
dev_langs:
- C++
helpviewer_keywords:
- Start method
ms.assetid: 67405c9d-0d1a-4c1e-8ea4-6ba01c1f90d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 32c59c00180b26a2856b1fc210302ffff0e72f0c
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641309"
---
# <a name="asyncbasestart-method"></a>AsyncBase::Start (Método)
Inicia la operación asincrónica.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
STDMETHOD(  
   Start  
)(void);  
```  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si la operación se inicia o ya está iniciado; en caso contrario, E_ILLEGAL_STATE_CHANGE.  
  
## <a name="remarks"></a>Comentarios  
 **Start()** es una implementación predeterminada de `IAsyncInfo::Start`, y no se realiza ningún trabajo real. Para iniciar una operación asincrónica, invalidar el `OnStart()` método virtual puro.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [AsyncBase (clase)](../windows/asyncbase-class.md)