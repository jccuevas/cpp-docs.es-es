---
title: "Método de synclockwithstatust:: GetStatus | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::GetStatus
dev_langs:
- C++
helpviewer_keywords:
- GetStatus method
ms.assetid: d448b51d-a63d-40d9-a9ee-4aad3204118d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 181735766e62aa1bf8c306bd425c6e6b03b2066d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="synclockwithstatustgetstatus-method"></a>SyncLockWithStatusT::GetStatus (Método)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
DWORD GetStatus() const;  
```  
  
## <a name="return-value"></a>Valor devuelto  
 El resultado de una operación de espera en el objeto que se basa en la clase de SyncLockWithStatusT, como un [exclusión mutua](../windows/mutex-class1.md) o [semáforo](../windows/semaphore-class.md). Cero (0) indica que la operación de espera devuelve el estado señalado. en caso contrario, se produjo otro estado, como el valor de tiempo de espera transcurrido.  
  
## <a name="remarks"></a>Comentarios  
 Recupera el estado de espera del objeto de SyncLockWithStatusT actual.  
  
 La función GetStatus() recupera el valor de subyacente [status_](../windows/synclockwithstatust-status-data-member.md) miembro de datos. Cuando un objeto basado en la clase de SyncLockWithStatusT realiza una operación de bloqueo, el objeto de espera en primer lugar el objeto esté disponible. El resultado de esa operación de espera se almacena en la `status_` miembro de datos. Los valores posibles de la `status_` miembro de datos son los valores devueltos de la operación de espera. Para obtener más información, vea los valores devueltos de la **WaitForSingleObjectEx()** función de la biblioteca de MSDN.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [SyncLockWithStatusT (clase)](../windows/synclockwithstatust-class.md)