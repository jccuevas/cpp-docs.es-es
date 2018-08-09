---
title: TryLock (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock
dev_langs:
- C++
helpviewer_keywords:
- TryLock method
ms.assetid: 504bb87c-2cd0-4f54-b458-b3efb9789053
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 12d823cdefa90cad1e454996be274135d9e68fa9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647633"
---
# <a name="criticalsectiontrylock-method"></a>CriticalSection::TryLock (Método)
Intenta entrar en una sección crítica sin bloquear. Si la llamada se realiza correctamente, el subproceso de llamada toma posesión de la sección crítica.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SyncLock TryLock();  
  
static SyncLock TryLock(  
   _In_ CRITICAL_SECTION* cs  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *CS*  
 Un objeto de sección crítica especificado por el usuario.  
  
## <a name="return-value"></a>Valor devuelto  
 Un valor distinto de cero si la sección crítica está escrita correctamente o el subproceso actual ya posee la sección crítica. Cero si otro subproceso ya posee la sección crítica.  
  
## <a name="remarks"></a>Comentarios  
 La primera **TryLock** el objeto de sección crítica actual afecta a la función. El segundo **TryLock** función afecta a una sección crítica especificado por el usuario.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [CriticalSection (clase)](../windows/criticalsection-class.md)