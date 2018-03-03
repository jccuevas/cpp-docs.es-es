---
title: "SRWLOCK:: Lockexclusive (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockExclusive
dev_langs:
- C++
helpviewer_keywords:
- LockExclusive method
ms.assetid: f361b672-fca6-45cc-a9b4-310cc0d23fdc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 345a2a4b52e0bb0811709c71e9e0b1d4a9b4d494
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="srwlocklockexclusive-method"></a>SRWLock::LockExclusive (Método)
Adquiere un objeto SRWLock en modo exclusivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
SyncLockExclusive LockExclusive();  
  
static SyncLockExclusive LockExclusive(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `lock`  
 Puntero a un objeto SRWLock.  
  
## <a name="return-value"></a>Valor devuelto  
 Un objeto SRWLock en modo exclusivo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [SRWLock (clase)](../windows/srwlock-class.md)