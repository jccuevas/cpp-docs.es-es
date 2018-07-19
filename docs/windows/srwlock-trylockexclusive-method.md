---
title: 'SRWLOCK:: Trylockexclusive (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive
dev_langs:
- C++
helpviewer_keywords:
- TryLockExclusive method
ms.assetid: 661e8b19-3058-4511-8742-c9fbb90412c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1cc9ee8a63d7403c3de408c924eeab07f1d0efa1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892662"
---
# <a name="srwlocktrylockexclusive-method"></a>SRWLock::TryLockExclusive (Método)
Intenta adquirir un objeto SRWLock en modo exclusivo para el objeto de SRWLock actual o especificado. Si la llamada se realiza correctamente, el subproceso de llamada toma posesión del bloqueo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
SyncLockExclusive TryLockExclusive();  
  
static SyncLockExclusive TryLockExclusive(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `lock`  
 Puntero a un objeto SRWLock.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, un objeto SRWLock en modo exclusivo y el subproceso que realiza la llamada toma posesión del bloqueo. En caso contrario, un SRWLock objeto cuyo estado no es válido.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [SRWLock (clase)](../windows/srwlock-class.md)