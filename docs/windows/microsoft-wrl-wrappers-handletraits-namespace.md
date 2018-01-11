---
title: Namespace handletraits | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits
dev_langs: C++
helpviewer_keywords: HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aec9ff1b4294257f692d76a96960820379116b0f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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