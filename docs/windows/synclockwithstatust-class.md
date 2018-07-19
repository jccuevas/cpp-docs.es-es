---
title: SyncLockWithStatusT (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT class
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 51e5a66358890fc20731fb5cb657616484e19db4
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890985"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT (Clase)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <  
   typename SyncTraits  
>  
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `SyncTraits`  
 Un tipo que puede llevar a cabo exclusivo o compartido posesión de un recurso.  
  
## <a name="remarks"></a>Comentarios  
 Representa un tipo que puede llevar a cabo exclusivo o compartido posesión de un recurso.  
  
 SyncLockWithStatusT (clase) se utiliza para implementar el [exclusión mutua](../windows/mutex-class1.md) y [semáforo](../windows/semaphore-class.md) clases.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SyncLockWithStatusT::SyncLockWithStatusT (constructor)](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|Inicializa una nueva instancia de la clase de SyncLockWithStatusT.|  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SyncLockWithStatusT::SyncLockWithStatusT (constructor)](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|Inicializa una nueva instancia de la clase de SyncLockWithStatusT.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SyncLockWithStatusT::GetStatus (método)](../windows/synclockwithstatust-getstatus-method.md)|Recupera el estado de espera del objeto de SyncLockWithStatusT actual.|  
|[SyncLockWithStatusT::IsLocked (método)](../windows/synclockwithstatust-islocked-method.md)|Indica si el objeto de SyncLockWithStatusT actual es propietario de un recurso; es decir, el objeto de SyncLockWithStatusT *bloqueado*.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[SyncLockWithStatusT::status_ (miembro de datos)](../windows/synclockwithstatust-status-data-member.md)|Contiene el resultado de subyacente esperar la operación después de una operación de bloqueo en un objeto basado en el objeto de SyncLockWithStatusT actual.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `SyncLockT`  
  
 `SyncLockWithStatusT`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers::Details (espacio de nombres)](../windows/microsoft-wrl-wrappers-details-namespace.md)