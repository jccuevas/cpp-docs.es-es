---
title: Mutex (Class1) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex class
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cd9c3dbbcbffff32f7c1611b6b49ee19ada7e52c
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606779"
---
# <a name="mutex-class1"></a>Mutex (Class1)
Representa un objeto de sincronización que controla de forma exclusiva un recurso compartido.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class Mutex : public HandleT<HandleTraits::MutexTraits>  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`SyncLock`|Un sinónimo de una clase que admita bloqueos sincrónicos.|  
  
### <a name="public-constructor"></a>Constructor público  
  
|nombre|Descripción|  
|----------|-----------------|  
|[Mutex::Mutex (constructor)](../windows/mutex-mutex-constructor.md)|Inicializa una nueva instancia de la **Mutex** clase.|  
  
### <a name="public-members"></a>Miembros públicos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[Mutex::Lock (método)](../windows/mutex-lock-method.md)|Espera hasta que el objeto actual, o la **Mutex** objeto asociado con el identificador especificado, las versiones que ha transcurrido el intervalo de tiempo de espera especificado o de la exclusión mutua.|  
  
### <a name="public-operator"></a>Operador público  
  
|nombre|Descripción|  
|----------|-----------------|  
|[Mutex::operator= (operador)](../windows/mutex-operator-assign-operator.md)|Asigna (mueve) especificado **Mutex** el objeto actual **Mutex** objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `Mutex`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers (espacio de nombres)](../windows/microsoft-wrl-wrappers-namespace.md)