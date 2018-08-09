---
title: Clase de semáforo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
dev_langs:
- C++
helpviewer_keywords:
- Semaphore class
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5101aba24cd8a0ed4f44587ffc4ad9e973099b8a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652641"
---
# <a name="semaphore-class"></a>Semaphore (clase)
Representa un objeto de sincronización que controla un recurso compartido que puede admitir un número limitado de usuarios.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`SyncLock`|Un sinónimo de una clase que admita bloqueos sincrónicos.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Semaphore::Semaphore (constructor)](../windows/semaphore-semaphore-constructor.md)|Inicializa una nueva instancia de la **semáforo** clase.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[InvokeHelper::Invoke (método)](../windows/invokehelper-invoke-method.md)|Llama al controlador de eventos cuya firma contiene el número especificado de argumentos.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Semaphore::Lock (método)](../windows/semaphore-lock-method.md)|Espera a que el objeto actual o el objeto asociado con el identificador especificado, está en el estado señalado o ha transcurrido el intervalo de tiempo de espera especificado.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Semaphore::operator= (operador)](../windows/semaphore-operator-assign-operator.md)|Mueve el identificador especificado de un **semáforo** el objeto actual **semáforo** objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `Semaphore`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers (espacio de nombres)](../windows/microsoft-wrl-wrappers-namespace.md)