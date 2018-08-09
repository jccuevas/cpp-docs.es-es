---
title: Wrappers Namespace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
dev_langs:
- C++
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9667a3660f46db0a61991545108d66bf0cac9f38
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017801"
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers (Espacio de nombres)
Define los tipos de contenedor de recursos adquisición es inicialización (RAII) que simplifican la administración de la duración de objetos, cadenas e identificadores.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
namespace Microsoft::WRL::Wrappers;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="typedefs"></a>Typedefs  
  
|Name|Descripción|  
|----------|-----------------|  
|`FileHandle`|`HandleT<HandleTraits::FileHandleTraits>`|  
  
### <a name="classes"></a>Clases  
  
|Name|Descripción|  
|----------|-----------------|  
|[CriticalSection (clase)](../windows/criticalsection-class.md)|Representa un objeto de sección crítica.|  
|[Event (clase) (Biblioteca de plantillas C++ de Windows en tiempo de ejecución)](../windows/event-class-windows-runtime-cpp-template-library.md)|Representa un evento.|  
|[HandleT (clase)](../windows/handlet-class.md)|Representa un identificador a un objeto.|  
|[HString (clase)](../windows/hstring-class.md)|Proporciona compatibilidad para manipular los identificadores HSTRING.|  
|[HStringReference (clase)](../windows/hstringreference-class.md)|Representa un objeto HSTRING que se crea a partir de una cadena existente.|  
|[Mutex (clase)](../windows/mutex-class1.md)|Representa un objeto de sincronización que controla de forma exclusiva un recurso compartido.|  
|[RoInitializeWrapper (clase)](../windows/roinitializewrapper-class.md)|Inicializa el tiempo de ejecución de Windows.|  
|[Semaphore (clase)](../windows/semaphore-class.md)|Representa un objeto de sincronización que controla un recurso compartido que puede admitir un número limitado de usuarios.|  
|[SRWLock (clase)](../windows/srwlock-class.md)|Representa un bloqueo fino de lector/escritor.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)