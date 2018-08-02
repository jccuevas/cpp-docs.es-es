---
title: Método CriticalSection | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock
dev_langs:
- C++
helpviewer_keywords:
- Lock method
ms.assetid: 37cb184c-e13c-49ef-b6a0-13908a956414
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1a4fee4991459ddbab0ac370f025776529a6bd1e
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464553"
---
# <a name="criticalsectionlock-method"></a>CriticalSection::Lock (Método)
Espera a que la propiedad del objeto especificado de sección crítica. La función devuelve cuando el subproceso de llamada se concede la propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
SyncLock Lock();  
  
   static SyncLock Lock(  
   _In_ CRITICAL_SECTION* cs  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *CS*  
 Un objeto de sección crítica especificado por el usuario.  
  
## <a name="return-value"></a>Valor devuelto  
 Un objeto de bloqueo que puede usarse para desbloquear la sección crítica actual.  
  
## <a name="remarks"></a>Comentarios  
 La primera **bloqueo** el objeto de sección crítica actual afecta a la función. El segundo **bloqueo** función afecta a una sección crítica especificado por el usuario.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [CriticalSection (clase)](../windows/criticalsection-class.md)