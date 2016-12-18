---
title: "Microsoft::WRL::Wrappers::HandleTraits (Espacio de nombres) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HandleTraits (espacio de nombres)"
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Microsoft::WRL::Wrappers::HandleTraits (Espacio de nombres)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe las características de tipos comunes de recurso basado en el identificador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
namespace Microsoft::WRL::Wrappers::HandleTraits;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="structures"></a>Estructuras  
  
|Name|Descripción|  
|----------|-----------------|  
|[CriticalSectionTraits (estructura)](../windows/criticalsectiontraits-structure.md)|Se especializa un `CriticalSection` objeto para admitir una sección crítica no válida o una función para liberar una sección crítica.|  
|[EventTraits (estructura)](../windows/eventtraits-structure.md)|Define las características de un `Event` identificador de clase.|  
|[FileHandleTraits (estructura)](../windows/filehandletraits-structure.md)|Define las características de un identificador de archivo.|  
|[HANDLENullTraits (estructura)](../windows/handlenulltraits-structure.md)|Define las características comunes de un identificador sin inicializar.|  
|[HANDLETraits (estructura)](../windows/handletraits-structure.md)|Define las características comunes de un identificador.|  
|[MutexTraits (estructura)](../windows/mutextraits-structure.md)|Define las características comunes de la [Mutex](Mutex%20Class1.md) clase.|  
|[SemaphoreTraits (estructura)](../Topic/SemaphoreTraits%20Structure.md)|Define las características comunes de un objeto semáforo.|  
|[SRWLockExclusiveTraits (estructura)](../windows/srwlockexclusivetraits-structure.md)|Describe las características comunes de la `SRWLock` clase en modo de bloqueo exclusivo.|  
|[SRWLockSharedTraits (estructura)](../windows/srwlocksharedtraits-structure.md)|Describe las características comunes de la `SRWLock` clase en modo de bloqueo compartido.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres Wrappers](../Topic/Microsoft::WRL::Wrappers%20Namespace.md)