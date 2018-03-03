---
title: "Semaphore:: lock (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 0eef6ede-dc7d-4f09-a6c8-2f7d39d65bfa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 11531a07f161722947d03a53392b8315b7593958
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="semaphorelock-method"></a>Semaphore::Lock (Método)
Espera a que el objeto actual o el objeto de semáforo asociado con el identificador especificado, está en el estado señalado o ha transcurrido el intervalo de tiempo de espera especificado.  
  
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
 Un identificador para un objeto de semáforo.  
  
## <a name="return-value"></a>Valor devuelto  
 Un Details::SyncLockWithStatusT\<HandleTraits::SemaphoreTraits >  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
[Semaphore (clase)](../windows/semaphore-class.md)
 