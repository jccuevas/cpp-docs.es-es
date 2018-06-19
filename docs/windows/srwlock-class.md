---
title: SRWLock (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock
dev_langs:
- C++
helpviewer_keywords:
- SRWLock class
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ec31b1469f437ff2776ed9da52fbcd7557fca8e2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891758"
---
# <a name="srwlock-class"></a>SRWLock (clase)
Representa un bloqueo finos de lector/escritor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class SRWLock;  
```  
  
## <a name="remarks"></a>Comentarios  
 Un bloqueo finos de lector/escritor se utiliza para sincronizar el acceso a través de subprocesos a un objeto o un recurso. Para obtener más información, consulte [funciones de sincronización](http://msdn.microsoft.com/en-us/9b6359c2-0113-49b6-83d0-316ad95aba1b).  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|||  
|-|-|  
|**SyncLockExclusive**|Sinónimo de un objeto SRWLock que se adquiere en modo exclusivo.|  
|**SyncLockShared**|Sinónimo de un objeto SRWLock que se adquiere en modo compartido.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SRWLock::SRWLock (constructor)](../windows/srwlock-srwlock-constructor.md)|Inicializa una nueva instancia de la clase SRWLock.|  
|[SRWLock::~SRWLock (destructor)](../windows/srwlock-tilde-srwlock-destructor.md)|Desinicializa una instancia de la clase SRWLock.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SRWLock::LockExclusive (método)](../windows/srwlock-lockexclusive-method.md)|Adquiere un objeto SRWLock en modo exclusivo.|  
|[SRWLock::LockShared (método)](../windows/srwlock-lockshared-method.md)|Adquiere un objeto SRWLock en modo compartido.|  
|[SRWLock::TryLockExclusive (método)](../windows/srwlock-trylockexclusive-method.md)|Intenta adquirir un objeto SRWLock en modo exclusivo para el objeto de SRWLock actual o especificado.|  
|[SRWLock::TryLockShared (método)](../windows/srwlock-trylockshared-method.md)|Intenta adquirir un objeto SRWLock en modo compartido para el objeto de SRWLock actual o especificado.|  
  
### <a name="protected-data-member"></a>Miembro de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[SRWLock::SRWLock_ (miembro de datos)](../windows/srwlock-srwlock-data-member.md)|Contiene la variable subyacente de bloqueo para el objeto de SRWLock actual.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `SRWLock`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Wrappers (espacio de nombres)](../windows/microsoft-wrl-wrappers-namespace.md)