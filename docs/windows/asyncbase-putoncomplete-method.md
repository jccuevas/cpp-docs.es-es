---
title: "Asyncbase:: Putoncomplete (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::PutOnComplete
dev_langs:
- C++
helpviewer_keywords:
- PutOnComplete method
ms.assetid: 1c469ff9-b2df-4637-bf05-01a617043149
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5ceda6a67053fb3d90dff1796c47c753b51f72e6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbaseputoncomplete-method"></a>AsyncBase::PutOnComplete (Método)
Establece la dirección del controlador de eventos de finalización en el valor especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDMETHOD(  
   PutOnComplete  
)(TComplete* completeHandler);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `completeHandler`  
 La dirección a la que se establece el controlador de eventos de finalización.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [AsyncBase (clase)](../windows/asyncbase-class.md)