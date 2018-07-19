---
title: 'SRWLOCK:: Trylockshared (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared
dev_langs:
- C++
helpviewer_keywords:
- TryLockShared method
ms.assetid: 10cc198d-39a0-4d18-aa78-706744948668
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19ff9324f946f48f201678f9c9e7403ba774b2c0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892288"
---
# <a name="srwlocktrylockshared-method"></a>SRWLock::TryLockShared (Método)
Intenta adquirir un objeto SRWLock en modo compartido para el objeto de SRWLock actual o especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
WRL_NOTHROW SyncLockShared TryLockShared();  
WRL_NOTHROW static SyncLockShared TryLockShared(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `lock`  
 Puntero a un objeto SRWLock.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, un objeto SRWLock en modo compartido y el subproceso que realiza la llamada toma posesión del bloqueo. En caso contrario, un SRWLock objeto cuyo estado no es válido.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [SRWLock (clase)](../windows/srwlock-class.md)