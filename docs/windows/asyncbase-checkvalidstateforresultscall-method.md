---
title: Checkvalidstateforresultscall (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall
dev_langs:
- C++
helpviewer_keywords:
- CheckValidStateForResultsCall method
ms.assetid: 87ca6805-bff1-4063-b855-6dd26132deff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dfa3b7222a25ed56d014cc90dbffa5f57a2c9436
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651913"
---
# <a name="asyncbasecheckvalidstateforresultscall-method"></a>AsyncBase::CheckValidStateForResultsCall (Método)
Comprueba si se pueden recopilar los resultados de una operación asincrónica en el estado asincrónico actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
inline HRESULT CheckValidStateForResultsCall();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se pueden recopilar los resultados; en caso contrario, E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [AsyncBase (clase)](../windows/asyncbase-class.md)