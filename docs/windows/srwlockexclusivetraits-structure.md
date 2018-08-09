---
title: SRWLockExclusiveTraits (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
dev_langs:
- C++
helpviewer_keywords:
- SRWLockExclusiveTraits structure
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 49f1f50b3fa9e34da8831c1cec138b6aefec27a5
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649278"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits (estructura)
Describe las características comunes de la `SRWLock` clase en modo de bloqueo exclusivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct SRWLockExclusiveTraits;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`Type`|Sinónimo de un puntero a la [SRWLOCK](../windows/srwlock-class.md) clase.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SRWLockExclusiveTraits::GetInvalidValue (método)](../windows/srwlockexclusivetraits-getinvalidvalue-method.md)|Recupera un **SRWLockExclusiveTraits** objeto que no siempre es válido.|  
|[SRWLockExclusiveTraits::Unlock (método)](../windows/srwlockexclusivetraits-unlock-method.md)|Devuelve el control exclusivo del elemento especificado `SRWLock` objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `SRWLockExclusiveTraits`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** handletraits  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers::HandleTraits (espacio de nombres)](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)