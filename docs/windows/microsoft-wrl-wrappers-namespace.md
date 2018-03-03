---
title: Wrappers Namespace | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
dev_langs:
- C++
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f7633bcd784fa7b9b5f7255e25e8ddc52c5b93db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers (Espacio de nombres)
Define los tipos de contenedor de inicialización de es de adquisición de recursos (RAII) que simplifican la administración de la duración de objetos, cadenas e identificadores.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
|[HString (clase)](../windows/hstring-class.md)|Proporciona compatibilidad para la manipulación de identificadores HSTRING.|  
|[HStringReference (clase)](../windows/hstringreference-class.md)|Representa un HSTRING que se crea a partir de una cadena existente.|  
|[Mutex (clase)](../windows/mutex-class1.md)|Representa un objeto de sincronización que controla de forma exclusiva un recurso compartido.|  
|[RoInitializeWrapper (clase)](../windows/roinitializewrapper-class.md)|Inicializa el tiempo de ejecución de Windows.|  
|[Semaphore (clase)](../windows/semaphore-class.md)|Representa un objeto de sincronización que controla un recurso compartido que puede admitir un número limitado de usuarios.|  
|[SRWLock (clase)](../windows/srwlock-class.md)|Representa un bloqueo finos de lector/escritor.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)