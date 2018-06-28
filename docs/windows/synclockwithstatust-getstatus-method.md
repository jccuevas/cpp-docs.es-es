---
title: 'Método de synclockwithstatust:: GetStatus | Documentos de Microsoft'
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
ms.openlocfilehash: 03addd8d89c54eddb5deb721ab47d46e8b945edd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889767"
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