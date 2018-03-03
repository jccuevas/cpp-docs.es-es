---
title: SRWLockExclusiveTraits (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
dev_langs:
- C++
helpviewer_keywords:
- SRWLockExclusiveTraits structure
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 05e7b2a6814cefffee258909f4bab11fcfe34f1c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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