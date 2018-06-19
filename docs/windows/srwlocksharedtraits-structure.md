---
title: SRWLockSharedTraits (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
dev_langs:
- C++
helpviewer_keywords:
- SRWLockSharedTraits structure
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6a18edef3fa658608459244143a5e48738f0c3a9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889651"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits (estructura)
Describe las características comunes de la clase SRWLock en modo de bloqueo compartido.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct SRWLockSharedTraits;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`Type`|Sinónimo de un puntero a la [SRWLOCK](../windows/srwlock-class.md) clase.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SRWLockSharedTraits::GetInvalidValue (método)](../windows/srwlocksharedtraits-getinvalidvalue-method.md)|Recupera un objeto SRWLockSharedTraits que siempre es válido.|  
|[SRWLockSharedTraits::Unlock (método)](../windows/srwlocksharedtraits-unlock-method.md)|Devuelve el control exclusivo del objeto SRWLock especificado.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `SRWLockSharedTraits`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** handletraits  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers::HandleTraits (espacio de nombres)](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)