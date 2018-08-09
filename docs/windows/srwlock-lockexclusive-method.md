---
title: Lockexclusive (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockExclusive
dev_langs:
- C++
helpviewer_keywords:
- LockExclusive method
ms.assetid: f361b672-fca6-45cc-a9b4-310cc0d23fdc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a32fe0e66a8f61bc17e4512f63705635cd8b5263
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643681"
---
# <a name="srwlocklockexclusive-method"></a>SRWLock::LockExclusive (Método)
Adquiere un **SRWLock** objeto en modo exclusivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
SyncLockExclusive LockExclusive();  
  
static SyncLockExclusive LockExclusive(  
   _In_ SRWLOCK* lock  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *lock*  
 Puntero a un **SRWLock** objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Un **SRWLock** objeto en modo exclusivo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [SRWLock (clase)](../windows/srwlock-class.md)