---
title: "CriticalSection:: TryLock (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
dev_langs:
- C++
helpviewer_keywords:
- TryLock method
ms.assetid: 504bb87c-2cd0-4f54-b458-b3efb9789053
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2bd717e3a91d2e0210adced36e33a89f3752fa8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="criticalsectiontrylock-method"></a>CriticalSection::TryLock (Método)
Intenta entrar en una sección crítica sin bloquear. Si la llamada se realiza correctamente, el subproceso de llamada toma posesión de la sección crítica.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
SyncLock TryLock();  
  
static SyncLock TryLock(  
   _In_ CRITICAL_SECTION* cs  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cs`  
 Un objeto de sección crítica especificado por el usuario.  
  
## <a name="return-value"></a>Valor devuelto  
 Un valor distinto de cero si la sección crítica se escribe correctamente o el subproceso actual ya posee la sección crítica. Devuelve cero si otro subproceso ya posee la sección crítica.  
  
## <a name="remarks"></a>Comentarios  
 La primera **TryLock** el objeto de sección crítica actual afecta a la función. El segundo **TryLock** function afecta a una sección crítica especificado por el usuario.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [CriticalSection (clase)](../windows/criticalsection-class.md)