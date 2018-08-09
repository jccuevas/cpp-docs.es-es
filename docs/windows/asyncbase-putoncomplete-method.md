---
title: Putoncomplete (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::PutOnComplete
dev_langs:
- C++
helpviewer_keywords:
- PutOnComplete method
ms.assetid: 1c469ff9-b2df-4637-bf05-01a617043149
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e982e6f053b207b1d57ed5c0df483a9d9ab778eb
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646977"
---
# <a name="asyncbaseputoncomplete-method"></a>AsyncBase::PutOnComplete (Método)
Establece la dirección del controlador de eventos de finalización en el valor especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
STDMETHOD(  
   PutOnComplete  
)(TComplete* completeHandler);  
```  
  
### <a name="parameters"></a>Parámetros  
 *completeHandler*  
 La dirección a la que se establece el controlador de eventos de finalización.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [AsyncBase (clase)](../windows/asyncbase-class.md)