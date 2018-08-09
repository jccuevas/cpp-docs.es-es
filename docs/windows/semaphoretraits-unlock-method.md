---
title: Método Semaphoretraits | Microsoft Docs
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
ms.openlocfilehash: 81f2214ef6a3e33b573a88ac4e23ae6aad64ea01
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015695"
---
# <a name="semaphoretraitsunlock-method"></a>SemaphoreTraits::Unlock (Método)
Control de versiones de un recurso compartido.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
inline static void Unlock(  
   _In_ Type h  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *h*  
 Identificador de un **semáforo** objeto.  
  
## <a name="remarks"></a>Comentarios  
 Si la operación de desbloqueo se realiza correctamente, **Unlock()** emite un error que indica la causa del error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** handletraits  
  
## <a name="see-also"></a>Vea también  
 [SemaphoreTraits (estructura)](../windows/semaphoretraits-structure.md)