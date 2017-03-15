---
title: "Mutex::Lock (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Lock (método)"
ms.assetid: 61d95072-b690-441e-a080-0bf94a733141
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Mutex::Lock (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

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
  
 **Espacio de nombres:** Wrappers
 
 ## <a name="see-also"></a>Vea también
 [Mutex (clase)](Mutex%20Class1.md)