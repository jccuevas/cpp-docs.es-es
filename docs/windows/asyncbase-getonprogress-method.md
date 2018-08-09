---
title: Getonprogress (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::GetOnProgress
dev_langs:
- C++
helpviewer_keywords:
- GetOnProgress method
ms.assetid: 286ddc9c-3e30-41a2-8e8b-e53d3fb0649d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9446c94039db0ff81826e77d71a2a9539be4b276
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643152"
---
# <a name="asyncbasegetonprogress-method"></a>AsyncBase::GetOnProgress (Método)
Copia la dirección del controlador de eventos de progreso actual en la variable especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
STDMETHOD(  
   GetOnProgress  
)(TProgress** progressHandler);  
```  
  
### <a name="parameters"></a>Parámetros  
 *progressHandler*  
 La ubicación donde se almacena la dirección del controlador de eventos de progreso actual.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [AsyncBase (clase)](../windows/asyncbase-class.md)