---
title: Putonprogress (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::PutOnProgress
dev_langs:
- C++
helpviewer_keywords:
- PutOnProgress method
ms.assetid: 1f5f180e-eb5a-4afe-ac16-69dbf36f0383
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1a9460664ed58cf39f7b295e1406649ad1d66ca9
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467422"
---
# <a name="asyncbaseputonprogress-method"></a>AsyncBase::PutOnProgress (Método)
Establece la dirección del controlador de eventos de progreso en el valor especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
STDMETHOD(  
   PutOnProgress  
)(TProgress* progressHandler);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *progressHandler*  
 La dirección a la que se establece el controlador de eventos de progreso.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [AsyncBase (clase)](../windows/asyncbase-class.md)