---
title: Método Synclockwithstatust | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
dev_langs:
- C++
helpviewer_keywords:
- GetStatus method
ms.assetid: d448b51d-a63d-40d9-a9ee-4aad3204118d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a54cab831d3e3180a28f892fcf37c7351c22bc33
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014967"
---
# <a name="synclockwithstatustgetstatus-method"></a>SyncLockWithStatusT::GetStatus (Método)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
DWORD GetStatus() const;  
```  
  
## <a name="return-value"></a>Valor devuelto  
 El resultado de una operación de espera en el objeto que se basa en el **SyncLockWithStatusT** clase, como un [Mutex](../windows/mutex-class1.md) o [semáforo](../windows/semaphore-class.md). Cero (0) indica que la operación de espera devuelve el estado señalado; en caso contrario, se produjo otro estado, como el valor de tiempo de espera transcurrido.  
  
## <a name="remarks"></a>Comentarios  
 Recupera el estado de espera de la actual **SyncLockWithStatusT** objeto.  
  
 La función GetStatus() recupera el valor de subyacente [status_](../windows/synclockwithstatust-status-data-member.md) miembro de datos. Cuando un objeto basado en la **SyncLockWithStatusT** clase realiza una operación de bloqueo, el objeto de espera en primer lugar el objeto esté disponible. El resultado de esa operación de espera se almacena en el `status_` miembro de datos. Los valores posibles de la `status_` miembro de datos son los valores devueltos de la operación de espera. Para obtener más información, vea los valores devueltos de la `WaitForSingleObjectEx()` función de la biblioteca de MSDN.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [SyncLockWithStatusT (clase)](../windows/synclockwithstatust-class.md)