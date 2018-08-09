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
ms.openlocfilehash: d65d7e2a1087dcce8eaee2fa132ae80d14073dda
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014944"
---
# <a name="mutex-class1"></a>Mutex (Class1)
Representa un objeto de sincronización que controla de forma exclusiva un recurso compartido.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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