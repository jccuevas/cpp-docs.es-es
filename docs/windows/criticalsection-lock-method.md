---
title: "CriticalSection:: lock (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 37cb184c-e13c-49ef-b6a0-13908a956414
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: af996faeebd0fcddb85993badd71ceecd32d494e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="criticalsectionlock-method"></a>CriticalSection::Lock (Método)
Esperas de propiedad del objeto de sección crítica especificado. La función devuelve cuando el subproceso que realiza la llamada se concede la propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
SyncLock Lock();  
  
   static SyncLock Lock(  
   _In_ CRITICAL_SECTION* cs  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cs`  
 Un objeto de sección crítica especificado por el usuario.  
  
## <a name="return-value"></a>Valor devuelto  
 Un objeto de bloqueo que puede usarse para desbloquear la sección crítica actual.  
  
## <a name="remarks"></a>Comentarios  
 La primera **bloqueo** el objeto de sección crítica actual afecta a la función. El segundo **bloqueo** function afecta a una sección crítica especificado por el usuario.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [CriticalSection (clase)](../windows/criticalsection-class.md)