---
title: SemaphoreTraits (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits
dev_langs:
- C++
helpviewer_keywords:
- SemaphoreTraits structure
ms.assetid: eddb8576-d063-409b-9201-cc87ca5d111e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1c5bdb20a765b56fd90a46389eba2a869890e4fd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892610"
---
# <a name="semaphoretraits-structure"></a>SemaphoreTraits (estructura)
Define las características comunes de un objeto de semáforo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct SemaphoreTraits : HANDLENullTraits;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SemaphoreTraits::Unlock (método)](../windows/semaphoretraits-unlock-method.md)|Control de versiones de un recurso compartido.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `HANDLENullTraits`  
  
 `SemaphoreTraits`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** handletraits  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers::HandleTraits (espacio de nombres)](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)