---
title: 'Mutex:: lock (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 61d95072-b690-441e-a080-0bf94a733141
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 37044dbd884c4e38c70677bf9a8fa0a51fda0a88
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880877"
---
# <a name="mutexlock-method"></a>Mutex::Lock (Método)
Espera a que el objeto actual o el objeto de exclusión mutua asociado con el identificador especificado, libera la exclusión mutua o ha transcurrido el intervalo de tiempo de espera especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
SyncLock Lock(  
   DWORD milliseconds = INFINITE  
);  
  
static SyncLock Lock(  
   HANDLE h,  
   DWORD milliseconds = INFINITE  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `milliseconds`  
 El intervalo de tiempo de espera, en milisegundos. El valor predeterminado es INFINITE, que espera indefinidamente.  
  
 `h`  
 El identificador de un objeto de exclusión mutua.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers
 
 ## <a name="see-also"></a>Vea también
 [Mutex (clase)](../windows/mutex-class1.md)