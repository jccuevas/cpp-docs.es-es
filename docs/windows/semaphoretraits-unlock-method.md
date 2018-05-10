---
title: 'Semaphoretraits:: Unlock (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 4e0ea808-b70d-43f7-81ef-998c3b34e3a0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0914c6ff83e881f92963fc8a548ddeff587db75e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="semaphoretraitsunlock-method"></a>SemaphoreTraits::Unlock (Método)
Control de versiones de un recurso compartido.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
inline static void Unlock(  
   _In_ Type h  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `h`  
 Identificador de un objeto de semáforo.  
  
## <a name="remarks"></a>Comentarios  
 Si la operación de desbloqueo es correcta, Unlock() emite un error que indica la causa del error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** handletraits  
  
## <a name="see-also"></a>Vea también  
 [SemaphoreTraits (estructura)](../windows/semaphoretraits-structure.md)