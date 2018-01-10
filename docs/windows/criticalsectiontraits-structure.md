---
title: CriticalSectionTraits (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
dev_langs: C++
helpviewer_keywords: CriticalSectionTraits structure
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c24d8dea31a87094329276af3ebfaf9f06136adc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits (estructura)
Se especializa en un objeto CriticalSection para admitir una sección crítica no válida o una función para liberar una sección crítica.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct CriticalSectionTraits;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`Type`|Un `typedef` que define un puntero a una sección crítica. `Type`se define como `typedef CRITICAL_SECTION* Type;`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CriticalSectionTraits::GetInvalidValue (método)](../windows/criticalsectiontraits-getinvalidvalue-method.md)|Una plantilla CriticalSection se especializa para que la plantilla no siempre es válida.|  
|[CriticalSectionTraits::Unlock (método)](../windows/criticalsectiontraits-unlock-method.md)|Una plantilla CriticalSection se especializa para que admita liberando propiedad del objeto de sección crítica especificado.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `CriticalSectionTraits`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** handletraits  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers::HandleTraits (espacio de nombres)](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)