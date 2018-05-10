---
title: Namespace handletraits | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
dev_langs:
- C++
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b114d067249e78d7fb935e473cc3cc952c76fe02
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Microsoft::WRL::Wrappers::HandleTraits (Espacio de nombres)
Describe las características de tipos comunes de recurso basado en el identificador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
namespace Microsoft::WRL::Wrappers::HandleTraits;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="structures"></a>Estructuras  
  
|Name|Descripción|  
|----------|-----------------|  
|[CriticalSectionTraits (estructura)](../windows/criticalsectiontraits-structure.md)|Especializa un `CriticalSection` objeto para admitir una sección crítica no válida o una función para liberar una sección crítica.|  
|[EventTraits (estructura)](../windows/eventtraits-structure.md)|Define las características de un `Event` identificador de clase.|  
|[FileHandleTraits (estructura)](../windows/filehandletraits-structure.md)|Define las características de un identificador de archivo.|  
|[HANDLENullTraits (estructura)](../windows/handlenulltraits-structure.md)|Define las características comunes de un identificador sin inicializar.|  
|[HANDLETraits (estructura)](../windows/handletraits-structure.md)|Define las características comunes de un identificador.|  
|[MutexTraits (estructura)](../windows/mutextraits-structure.md)|Define las características comunes de la [exclusión mutua](../windows/mutex-class1.md) clase.|  
|[SemaphoreTraits (estructura)](../windows/semaphoretraits-structure.md)|Define las características comunes de un objeto de semáforo.|  
|[SRWLockExclusiveTraits (estructura)](../windows/srwlockexclusivetraits-structure.md)|Describe las características comunes de la `SRWLock` clase en modo de bloqueo exclusivo.|  
|[SRWLockSharedTraits (estructura)](../windows/srwlocksharedtraits-structure.md)|Describe las características comunes de la `SRWLock` clase en modo de bloqueo compartido.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers (espacio de nombres)](../windows/microsoft-wrl-wrappers-namespace.md)