---
title: "Semaphore::Lock (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Lock (método)"
ms.assetid: 0eef6ede-dc7d-4f09-a6c8-2f7d39d65bfa
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Semaphore::Lock (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

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
 Identificador de un objeto de semáforo.  
  
## <a name="return-value"></a>Valor devuelto  
 Un Details::SyncLockWithStatusT \< HandleTraits::SemaphoreTraits >  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Wrappers  
  
## <a name="see-also"></a>Vea también  
[Semaphore (clase)](../windows/semaphore-class.md)
 