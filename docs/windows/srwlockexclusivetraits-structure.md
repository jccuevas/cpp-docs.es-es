---
title: SRWLockExclusiveTraits (estructura) | Documentos de Microsoft
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
ms.openlocfilehash: 6b5d56c4e0c31b56e5bdc92a9d209b58cd15ffb1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889282"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits (estructura)
Describe las características comunes de la clase SRWLock en modo de bloqueo exclusivo.  
  
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
|[SRWLockExclusiveTraits::GetInvalidValue (método)](../windows/srwlockexclusivetraits-getinvalidvalue-method.md)|Recupera un objeto SRWLockExclusiveTraits que siempre es válido.|  
|[SRWLockExclusiveTraits::Unlock (método)](../windows/srwlockexclusivetraits-unlock-method.md)|Devuelve el control exclusivo del objeto SRWLock especificado.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `SRWLockExclusiveTraits`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** handletraits  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers::HandleTraits (espacio de nombres)](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)